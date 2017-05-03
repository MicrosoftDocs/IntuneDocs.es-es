---
title: "Configuración y administración de certificados PKCS con Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Azure de Intune: aprenda a configurar la infraestructura y, luego, cree y asigne certificados PKCS con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e189ebd1-6ca1-4365-9d5d-fab313b7e979
ms.reviewer: vinaybha
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: a981b0253f56d66292ce77639faf4beba8832a9e
ms.openlocfilehash: 0c378fe6ed26bafb5a78daf36b9326771fdd287b
ms.lasthandoff: 04/19/2017



---
# <a name="configure-your-microsoft-intune-certificate-infrastructure-for-pkcs"></a>Configuración de la infraestructura de certificados de Microsoft Intune para PKCS
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

En este tema se muestra cómo configurar la infraestructura y, luego, crear y asignar perfiles de certificados PKCS con Intune.

Para realizar cualquier autenticación basada en certificados en la organización, se necesita una entidad de certificación empresarial.

Para usar perfiles de certificado PKCS, aparte de la entidad de certificación empresarial, también se necesita lo siguiente:

-   Un equipo que pueda comunicarse con la entidad de certificación; también puede usar el propio equipo de la entidad de certificación.

-  El conector de certificado de Intune, que se ejecuta en el equipo que puede comunicarse con la entidad de certificación.

## <a name="important-terms"></a>Términos importantes


-    **Dominio de Active Directory:** todos los servidores mencionados en esta sección (salvo el servidor Proxy de aplicación web) deben estar unidos al dominio de Active Directory.

-  **Entidad de certificación**: también llamada CA emisora, es necesario disponer de una entidad de certificación (CA) empresarial que se ejecute en una edición Enterprise de Windows Server 2008 R2 o versión posterior. No se admiten CA independientes. Para obtener instrucciones sobre cómo configurar una entidad de certificación, consulte [Instalar la entidad de certificación](http://technet.microsoft.com/library/jj125375.aspx).
    Si la CA ejecuta Windows Server 2008 R2, se debe [instalar la revisión de KB2483564](http://support.microsoft.com/kb/2483564/).

-  **Equipo que pueda comunicarse con la entidad de certificación:** también puede usar el propio equipo de la entidad de certificación.
-  **Microsoft Intune Certificate Connector**: en el Portal de Azure, descargue el instalador de **Certificate Connector** (**ndesconnectorssetup.exe**). Después, puede ejecutar **ndesconnectorssetup.exe** en el equipo donde desee instalar el conector de certificado. Para perfiles de certificado PKCS, instale el conector de certificado en el equipo que se comunica con la entidad de certificación.
-  **Servidor Proxy de aplicación web** (opcional): puede usar un servidor con Windows Server 2012 R2 o versión posterior como servidor Proxy de aplicación web (WAP). Esta configuración:
    -  Permite a los dispositivos recibir certificados mediante una conexión a Internet.
    -  Es una recomendación de seguridad cuando los dispositivos se conectan a través de Internet para recibir y renovar certificados.

 > [!NOTE]           
> -    El servidor que hospeda WAP [debe instalar una actualización](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que habilite la compatibilidad con las direcciones URL largas que usa el Servicio de inscripción de dispositivos de red (NDES). Esta actualización está incluida en el [paquete acumulativo de actualizaciones de diciembre de 2014](http://support.microsoft.com/kb/3013769)o está disponible por separado, en [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Además, el servidor que hospeda WAP debe tener un certificado SSL que coincida con el nombre que se publica para los clientes externos, así como confiar en el certificado SSL que se usa en el servidor NDES. Estos certificados habilitan al servidor WAP para terminar la conexión SSL entre clientes y crear una nueva conexión SSL hacia el servidor NDES.
    Para obtener más información sobre los certificados de WAP, vea la sección sobre cómo **planear certificados** de [Planeamiento de publicación de aplicaciones mediante el Proxy de aplicación web](https://technet.microsoft.com/library/dn383650.aspx). Para obtener información general sobre los servidores WAP, vea [Trabajar con el Proxy de aplicación Web](http://technet.microsoft.com/library/dn584113.aspx).|


## <a name="certificates-and-templates"></a>Certificados y plantillas

|Objeto|Detalles|
|----------|-----------|
|**Plantilla de certificado**|Esta plantilla se configura en la CA emisora.|
|**Certificado de CA raíz de confianza**|Expórtelo como archivo **.cer** desde la CA emisora o desde cualquier dispositivo que confíe en la CA emisora y asígnelo en dispositivos con el perfil de certificado de CA de confianza.<br /><br />Use un único certificado de CA raíz de confianza por cada plataforma de sistema operativo y asócielo a cada perfil de certificado raíz de confianza que cree.<br /><br />Puede usar certificados de CA raíz de confianza adicionales cuando sea necesario. Por ejemplo, podría hacerlo para proporcionar una relación de confianza con una CA que firme los certificados de autenticación de servidor para los puntos de acceso Wi-Fi.|


## <a name="configure-your-infrastructure"></a>Configurar la infraestructura
Para poder configurar perfiles de certificado, debe llevar a cabo los pasos siguientes. Estos pasos requieren conocimientos de Windows Server 2012 R2 y Servicios de certificados de Active Directory (ADCS):

- **Paso 1:** configurar plantillas de certificado en la entidad de certificación.
- **Paso 2:** habilitar, instalar y configurar Intune Certificate Connector.

## <a name="step-1---configure-certificate-templates-on-the-certification-authority"></a>Paso 1: configurar plantillas de certificado en la entidad de certificación

### <a name="to-configure-the-certification-authority"></a>Para configurar la entidad de certificación

1.  En la entidad de certificación emisora, use el complemento Plantillas de certificado para crear una plantilla personalizada o copie una plantilla existente y edítela (por ejemplo, la plantilla de usuario) para usarla con PKCS.

    La plantilla debe incluir lo siguiente:

    -   Especifique **Nombre para mostrar de plantilla** descriptivo para la plantilla.

    -   En la pestaña **Nombre del firmante** , seleccione **Proporcionado por el solicitante**. (La seguridad la aplica el módulo de directivas de Intune para NDES).

    -   En la pestaña **Extensiones** , asegúrese de que **Descripción de las directivas de aplicación** incluya **Autenticación del cliente**.

        > [!IMPORTANT]
        > En el caso de plantillas de certificado de iOS y macOS, en la pestaña **Extensiones**, edite **Uso de claves** y asegúrese de que la opción **Firma como prueba de origen** no esté seleccionada.

2.  Revise la configuración de **Período de validez** en la pestaña **General** de la plantilla. Intune usa de forma predeterminada el valor configurado en la plantilla. Pero tiene la opción de configurar la CA para permitir que el solicitante especifique otro valor, lo que se puede establecer desde la consola de administrador de Intune. Si desea usar siempre el valor de la plantilla, omita el resto de este paso.

    > [!IMPORTANT]
    > iOS y macOS siempre usa el valor establecido en la plantilla con independencia de otras configuraciones que realice.

    Para configurar la CA para permitir que el solicitante especifique el período de validez, ejecute los siguientes comandos en la CA:

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b.  **net stop certsvc**

    c.  **net start certsvc**

3.  En la CA emisora, use el complemento Entidad de certificación para publicar la plantilla de certificado.

    a.  Seleccione el nodo **Plantillas de certificado**, haga clic en **Acción**-&gt;**Nuevo** &gt; **Plantilla de certificado que se va a emitir** y seleccione la plantilla que creó en el paso 2.

    b.  Valide que la plantilla se publicó visualizándola en la carpeta **Plantillas de certificado** .

4.  En el equipo de la entidad de certificación, asegúrese de que el equipo que hospeda Intune Certificate Connector tenga permiso de inscripción, de modo que pueda acceder a la plantilla usada al crear el perfil de certificado PKCS. Establezca ese permiso en la pestaña **Seguridad** de las propiedades del equipo de CA.

## <a name="step-2---enable-install-and-configure-the-intune-certificate-connector"></a>Paso 2: habilitar, instalar y configurar Intune Certificate Connector
En este paso:

- Habilitar la compatibilidad de Certificate Connector
- Descargar, instalar y configurar Certificate Connector.

### <a name="to-enable-support-for-the-certificate-connector"></a>Para habilitar la compatibilidad de Certificate Connector

1.  Inicie sesión en el portal de Azure.
2.  Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3.  En la hoja **Intune**, elija **Configurar dispositivos**.
2.  En la hoja **Configuración del dispositivo**, elija **Configuración** > **Entidad de certificación**.
2.  En **Paso 1**, elija **Habilitar**.

### <a name="to-download-install-and-configure-the-certificate-connector"></a>Para descargar, instalar y configurar Certificate Connector

1.  En la hoja **Configurar dispositivos**, elija **Configuración** > **Entidad de certificación**.
2.  Elija **Descargar Certificate Connector**.
2.  Una vez finalizada la descarga, ejecute el instalador descargado (**ndesconnectorssetup.exe**).
  Ejecute el instalador en el equipo que puede conectarse con la entidad de certificación. Elija la opción de distribución PKCS (PFX) y seleccione **Instalar**. Cuando haya finalizado la instalación, siga creando un perfil de certificado según se indica en [Configurar perfiles de certificado](how-to-configure-certificates.md).

3.  Cuando se le solicite el certificado de cliente para Certificate Connector, elija **Seleccionar** y seleccione el certificado de **autenticación del cliente** instalado.

    Después de seleccionar el certificado de autenticación del cliente, volverá a la superficie del **Certificado de cliente para el conector de certificado para Microsoft Intune** . Aunque no se muestre el certificado seleccionado, elija **Siguiente** para ver las propiedades de dicho certificado. Luego, elija **Siguiente** e **Instalar**.

4.  Cuando se complete el asistente, pero antes de cerrarlo, haga clic en **Iniciar la UI del conector de certificado**.

    > [!TIP]
    > Si cierra al asistente antes de iniciar la IU del conector de certificado, puede volver a abrirlo ejecutando el comando siguiente:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  En la IU **Conector de certificado** :

    a. Elija **Iniciar sesión** y escriba sus credenciales de administrador de servicio de Intune o las credenciales de un administrador de inquilinos con permiso de administración global.

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    b. Seleccione la pestaña **Avanzadas**y proporcione las credenciales de una cuenta que tenga el permiso **Emitir y administrar certificados** en la entidad de certificación emisora.

    c. Elija **Aplicar**.

    Ahora puede cerrar la IU del conector de certificado.

6.  Abra un símbolo del sistema y escriba **services.msc**. Después, pulse **ENTRAR**, haga clic con el botón derecho en **Servicio del conector de Intune** y elija **Reiniciar**.

Para validar que el servicio se ejecuta, abra un explorador y escriba la siguiente dirección URL, que debe devolver un error **403** :

**http:// &lt;FQDN_de_sur_servidor_NDES&gt;/certsrv/mscep/mscep.dll**


### <a name="how-to-create-a-pkcs-certificate-profile"></a>Creación de un perfil de certificado PKCS

En Azure Portal, seleccione la carga de trabajo **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, haga clic en **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de certificado PKCS.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo para este certificado PKCS:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **tipos de perfil**, elija **Certificado PKCS**.
7. En la hoja **Certificado PKCS**, configure los siguientes valores:
    - **Umbral de renovación (%)**: especifique qué porcentaje de la duración del certificado tiene que quedar para que el dispositivo solicite la renovación del certificado.
    - **Período de validez del certificado**: si ha ejecutado el comando **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** en la entidad de certificación emisora, que permite un período de validez personalizado, puede especificar la cantidad de tiempo restante antes de que expire el certificado.<br>Puede especificar un valor inferior al período de validez de la plantilla de certificado especificada, pero no superior. Por ejemplo, si el período de validez del certificado en la plantilla de certificado es de dos años, puede especificar un valor de un año, pero no un valor de cinco años. El valor también debe ser menor que el período de validez restante del certificado de la CA emisora.
    - **Proveedor de almacenamiento de claves (KSP)** (Windows 10): especifique donde se almacenará la clave del certificado. Elija uno de los siguientes valores:
        - **Inscribirse en KSP Módulo de plataforma segura (TPM) si está presente, si no en KSP Software**
        - **Inscribirse en KSP del Módulo de plataforma segura (TPM) o se producirá un error**
        - **Inscribirse en Passport o se producirá un error (Windows 10 y versiones posteriores)**
        - **Inscribirse en el KSP Software**
    - **Entidad de certificación**: entidad de certificación (CA) empresarial que se ejecuta en una edición Enterprise de Windows Server 2008 R2 o versión posterior. No se admiten CA independientes. Para obtener instrucciones sobre cómo configurar una entidad de certificación, consulte [Instalar la entidad de certificación](http://technet.microsoft.com/library/jj125375.aspx). Si la CA ejecuta Windows Server 2008 R2, se debe [instalar la revisión de KB2483564](http://support.microsoft.com/kb/2483564/).
    - **Nombre de la entidad de certificación**: escriba el nombre de la entidad de certificación.
    - **Nombre de plantilla de certificado**: escriba el nombre de una plantilla de certificado cuya utilización está configurada en el Servicio de inscripción de dispositivos de red y que se haya agregado a una CA emisora.
    Asegúrese de que el nombre coincida exactamente con una de las plantillas de certificado que se muestran en el Registro del servidor que ejecuta el Servicio de inscripción de dispositivos de red. Asegúrese de que especifica el nombre de la plantilla de certificado y no el nombre para mostrar de la plantilla de certificado. 
    Para buscar los nombres de las plantillas de certificado, vaya a la siguiente clave: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. Verá las plantillas de certificado como los valores de **EncryptionTemplate**, **GeneralPurposeTemplate**y **SignatureTemplate**. De forma predeterminada, el valor de las tres plantillas de certificado es IPSECIntermediateOffline, que se asigna al nombre de plantilla para mostrar **IPSEC (solicitud sin conexión)**. 
    - **Formato de nombre del sujeto**: en la lista, seleccione cómo Intune crea automáticamente el nombre del sujeto en la solicitud de certificado. Si el certificado es para un usuario, también puede incluir la dirección de correo electrónico del usuario en el nombre del sujeto. Elija de entre las siguientes opciones:
        - **No configurado**.
        - **Nombre común**
        - **Nombre común, incluyendo la dirección de correo electrónico**
        - **Nombre común como correo electrónico**
    - **Subject alternative name** (Nombre alternativo del sujeto): especifique cómo Intune creará automáticamente los valores del nombre alternativo del sujeto (SAN) en la solicitud de certificado. Por ejemplo, si seleccionó un tipo de certificado de usuario, puede incluir el nombre principal de usuario (UPN) en el nombre alternativo del sujeto. Si el certificado de cliente se utilizará para autenticar un servidor de directivas de redes, debe establecer el nombre alternativo del sujeto en el UPN.
    - **Uso mejorado de clave** (Android): elija **Agregar** para agregar valores para la finalidad prevista del certificado. En la mayoría de los casos, el certificado requerirá **Autenticación de cliente** para que el usuario o dispositivo pueda autenticarse en un servidor. Sin embargo, puede agregar otros usos de clave según sea necesario. 
    - **Certificado raíz** (Android): elija un perfil de certificado de CA raíz que previamente haya configurado y asignado al usuario o dispositivo. Este certificado de CA debe ser el certificado raíz para la entidad de certificación que emitirá el certificado que va a configurar en este perfil de certificado. Este es el perfil de certificado de confianza que creó anteriormente.
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.

## <a name="how-to-assign-the-certificate-profile"></a>Asignación del perfil de certificado

Considere los siguiente aspectos antes de asignar perfiles de certificado a grupos:

- Cuando asigna perfiles de certificado a grupos, el archivo de certificado del perfil de certificado de CA de confianza se instala en el dispositivo. El dispositivo usa el perfil de certificado PKCS para crear una solicitud de certificado.
- Los perfiles de certificado solo se instalan en dispositivos que ejecutan la plataforma usada al crear el perfil.
- Puede asignar perfiles de certificado en recopilaciones de usuarios o en recopilaciones de dispositivos.
- Para publicar rápidamente un certificado en un dispositivo una vez inscrito el dispositivo, asigne el perfil de certificado en un grupo de usuarios (no en un grupo de dispositivos). Si lo asigna en un grupo de dispositivos, deberá efectuar un registro completo del dispositivo para que el dispositivo reciba directivas.
- Aunque asigne cada perfil por separado, también deberá asignar la CA raíz de confianza y el perfil PKCS. De lo contrario, se producirá un error en la directiva del certificado PKCS.

Para información sobre cómo asignar perfiles, consulte [Asignación de perfiles de dispositivo](how-to-assign-device-profiles.md).

