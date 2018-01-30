---
title: "Configuración y administración de certificados SCEP con Intune"
titlesuffix: Azure portal
description: Aprenda a configurar la infraestructura y, luego, crear y asignar perfiles de certificado SCEP de Intune.
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 1/18/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5aea88aa8898380c54867090650bd16d8bf60f3c
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="configure-and-manage-scep-certificates-with-intune"></a>Configuración y administración de certificados SCEP con Intune
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En este tema se muestra cómo configurar la estructura y, luego, crear y asignar perfiles de certificados de Protocolo de inscripción de certificados simple (SCEP) con Intune.

## <a name="configure-on-premises-infrastructure"></a>Configuración de la infraestructura local

-    **Dominio de Active Directory:** todos los servidores mencionados en esta sección (salvo el servidor Proxy de aplicación web) deben estar unidos al dominio de Active Directory.

-  **Entidad de certificación (CA):** también llamada CA emisora, es necesario disponer de una entidad de certificación (CA) empresarial que se ejecute en una edición Enterprise de Windows Server 2008 R2 o posterior. No se admiten CA independientes. Para detalles, consulte [Instalación de la entidad de certificación](http://technet.microsoft.com/library/jj125375.aspx).
    Si la CA ejecuta Windows Server 2008 R2, se debe [instalar la revisión de KB2483564](http://support.microsoft.com/kb/2483564/).

-  **Servidor SCEP:** en un servidor con Windows Server 2012 R2 o posterior, hay que configurar el Servicio de inscripción de dispositivos de red (SCEP). En Intune no se puede usar el Servicio de inscripción de dispositivos de red cuando se ejecuta en un servidor que también ejecuta la CA empresarial. Vea [Orientación para el Servicio de inscripción de dispositivos de red](http://technet.microsoft.com/library/hh831498.aspx) para obtener instrucciones sobre cómo configurar Windows Server 2012 R2 para hospedar el Servicio de inscripción de dispositivos de red.
El servidor SCEP debe estar unido a dominio al dominio que hospeda la entidad de certificación y no estar en el mismo servidor que ella. Puede encontrar más información sobre cómo implementar el servidor NDES en un bosque independiente, una red aislada o un dominio interno en [Uso de un módulo de directivas con el servicio de inscripción de dispositivos de red](https://technet.microsoft.com/library/dn473016.aspx).

-  **Microsoft Intune Certificate Connector**: use Azure Portal para descargar el instalador de **Certificate Connector** (**ndesconnectorssetup.exe**). Después, puede ejecutar **ndesconnectorssetup.exe** en el equipo donde desee instalar el conector de certificado. 
-  **Servidor Proxy de aplicación web** (opcional): use un servidor con Windows Server 2012 R2 o posterior como servidor Proxy de aplicación web (WAP). Esta configuración:
    -  Permite a los dispositivos recibir certificados mediante una conexión a Internet.
    -  Es una recomendación de seguridad cuando los dispositivos se conectan a través de Internet para recibir y renovar certificados.

 > [!NOTE]           
> -    El servidor que hospeda WAP [debe instalar una actualización](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que habilite la compatibilidad con las direcciones URL largas que usa el Servicio de inscripción de dispositivos de red. Esta actualización está incluida en el [paquete acumulativo de actualizaciones de diciembre de 2014](http://support.microsoft.com/kb/3013769)o está disponible por separado, en [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Además, el servidor que hospeda WAP debe tener un certificado SSL que coincida con el nombre que se publica para los clientes externos, así como confiar en el certificado SSL que se usa en el servidor NDES. Estos certificados habilitan al servidor WAP para terminar la conexión SSL entre clientes y crear una nueva conexión SSL hacia el servidor NDES.
    Para obtener más información sobre los certificados de WAP, vea la sección sobre cómo **planear certificados** de [Planeamiento de publicación de aplicaciones mediante el Proxy de aplicación web](https://technet.microsoft.com/library/dn383650.aspx). Para obtener información general sobre los servidores WAP, vea [Trabajar con el Proxy de aplicación Web](http://technet.microsoft.com/library/dn584113.aspx).|

### <a name="network-requirements"></a>Requisitos de red

Desde Internet a la red perimetral, permita el puerto 443 desde todos los hosts o direcciones IP de Internet al servidor NDES.

Desde la red perimetral a la red de confianza, permita todos los puertos y protocolos necesarios para el acceso a dominios en el servidor SCEP unido a dominio. El servidor NDES necesita acceso a los servidores de certificados, los servidores DNS, los servidores de Configuration Manager y los controladores de dominio.

Se recomienda publicar el servidor NDES a través de un proxy, como el [proxy de aplicación de Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), [el proxy de acceso web](https://technet.microsoft.com/library/dn584107.aspx) o un proxy de terceros.


### <a name="certificates-and-templates"></a>Certificados y plantillas

|Objeto|Detalles|
|----------|-----------|
|**Plantilla de certificado**|Configure esta plantilla en la CA emisora.|
|**Certificado de autenticación del cliente**|Solicitado desde la CA emisora o la CA pública; instale este certificado en el servidor NDES.|
|**Certificado de autenticación de servidor**|Solicitado desde la CA emisora o la CA pública, este certificado SSL se instala y se enlaza en IIS, en el servidor NDES.|
|**Certificado de CA raíz de confianza**|Este certificado se exporta como un archivo **.cer** desde la CA raíz o desde cualquier dispositivo que confíe en la CA raíz, y se asigna a los dispositivos mediante el perfil de certificado de CA de confianza.<br /><br />Use un único certificado de CA raíz de confianza por cada plataforma de sistema operativo y asócielo a cada perfil de certificado raíz de confianza que cree.<br /><br />Puede usar certificados de CA raíz de confianza adicionales cuando sea necesario. Por ejemplo, podría hacerlo para proporcionar una relación de confianza con una CA que firme los certificados de autenticación de servidor para los puntos de acceso Wi-Fi.|

### <a name="accounts"></a>Cuentas

|Nombre|Detalles|
|--------|-----------|
|**Cuenta de servicio NDES**|Especifique una cuenta de usuario de dominio que se vaya a usar como cuenta de servicio NDES.|

## <a name="configure-your-infrastructure"></a>Configurar la infraestructura
Para poder configurar perfiles de certificado debe completar las tareas siguientes, que requieren conocimientos de Windows Server 2012 R2 y Servicios de certificados de Active Directory (ADCS):

**Paso 1**: crear una cuenta de servicio NDES

**Paso 2**: configurar plantillas de certificado en la entidad de certificación

**Paso 3**: configurar los requisitos previos en el servidor NDES

**Paso 4**: configurar NDES para su uso con Intune

**Paso 5**: habilitar, instalar y configurar Intune Certificate Connector

#### <a name="step-1---create-an-ndes-service-account"></a>Paso 1: crear una cuenta de servicio NDES

Cree una cuenta de usuario de dominio que vaya a usar como cuenta de servicio NDES. Esta cuenta se especifica al configurar las plantillas en la CA emisora antes de instalar y configurar NDES. Asegúrese de que el usuario tenga los derechos predeterminados, los derechos **Iniciar sesión localmente**, **Iniciar sesión como un servicio** e **Iniciar sesión como trabajo por lotes**. Algunas organizaciones tienen directivas de protección que deshabilitan estos derechos.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>Paso 2: configurar plantillas de certificado en la entidad de certificación
En esta tarea tendrá que:

-   Configurar una plantilla de certificado para NDES

-   Publicar la plantilla de certificado para NDES

##### <a name="to-configure-the-certification-authority"></a>Para configurar la entidad de certificación

1.  Inicie sesión como administrador de organización.

2.  En la CA emisora, use el complemento Plantillas de certificado para crear una nueva plantilla personalizada o copiar una plantilla existente y, luego, editarla (por ejemplo, la plantilla de usuario) para su uso con NDES.

    >[!NOTE]
    > La plantilla de certificado NDES debe basarse en una plantilla de certificado v2 (con compatibilidad con Windows 2003).

    La plantilla debe tener las siguientes configuraciones:

    -   Especifique **Nombre para mostrar de plantilla** descriptivo para la plantilla.

    -   En la pestaña **Nombre del firmante** , seleccione **Proporcionado por el solicitante**. (La seguridad la aplica el módulo de directivas de Intune para NDES).

    -   En la pestaña **Extensiones** , asegúrese de que **Descripción de las directivas de aplicación** incluya **Autenticación del cliente**.

        > [!IMPORTANT]
        > En el caso de plantillas de certificado de iOS y macOS, en la pestaña **Extensiones**, edite **Uso de claves** y asegúrese de que la opción **Firma como prueba de origen** no esté seleccionada.

    -   En la pestaña **Seguridad**, agregue la cuenta de servicio NDES y otórguele permisos de **inscripción**en la plantilla. Los administradores de Intune que crean perfiles SCEP necesitan derechos de **lectura** para poder ir a la plantilla al crear los perfiles SCEP.

    > [!NOTE]
    > Para revocar certificados de la cuenta de servicio NDES, necesitará derechos para *emitir y administrar certificados* referentes a cada plantilla de certificado que use un perfil de certificado.

3.  Revise la configuración de **Período de validez** en la pestaña **General** de la plantilla. Intune usa de forma predeterminada el valor configurado en la plantilla. Pero tiene la opción de configurar la CA para permitir que el solicitante especifique otro valor, lo que se puede establecer desde la consola de administrador de Intune. Si desea usar siempre el valor de la plantilla, omita el resto de este paso.

    > [!IMPORTANT]
    > iOS y macOS siempre usa el valor establecido en la plantilla con independencia de otras configuraciones que realice.

Estas son capturas de pantalla de una configuración de plantilla de ejemplo.

![Plantilla, pestaña Administración de solicitudes](.\media\scep_ndes_request_handling.png)

![Plantilla, pestaña Nombre del sujeto](.\media\scep_ndes_subject_name.jpg)

![Plantilla, pestaña Seguridad](.\media\scep_ndes_security.jpg)

![Plantilla, pestaña Extensiones](.\media\scep_ndes_extensions.jpg)

![Plantilla, pestaña Requisitos de emisión](.\media\scep_ndes_issuance_reqs.jpg)

>   [!IMPORTANT]
    > En el caso de directivas de aplicación, agregue únicamente las directivas de aplicación necesarias. Confirme las elecciones con los administradores de seguridad.



Para configurar la CA para permitir que el solicitante especifique el período de validez:

1. En la entidad de certificación, ejecute los comandos siguientes:
    - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
    - **net stop certsvc**
    - **net start certsvc**
2. En la CA emisora, use el complemento Entidad de certificación para publicar la plantilla de certificado.
    Seleccione el nodo **Plantillas de certificado**, haga clic en **Acción**-&gt;**Nuevo** &gt; **Plantilla de certificado que se va a emitir** y seleccione la plantilla que creó en el paso 2.
3. Valide que la plantilla se publicó visualizándola en la carpeta **Plantillas de certificado** .


#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>Paso 3: configurar los requisitos previos en el servidor NDES
En esta tarea tendrá que hacer lo siguiente:

-   Agregar NDES a un servidor con Windows Server y configurar IIS para que admita NDES

-   Agregar la cuenta de servicio NDES al grupo IIS_IUSRS

-   Establecer el SPN para la cuenta de servicio NDES




   1.  En el servidor en el que se hospeda NDES, inicie sesión como **Administrador de organización** y, luego, use el [Asistente para agregar roles y características](https://technet.microsoft.com/library/hh831809.aspx) para instalar NDES:

    1.  En el asistente, seleccione **Servicios de certificados de Active Directory** para obtener acceso a los servicios de rol de AD CS. Seleccione el **Servicio de inscripción de dispositivos de red**, desactive **Entidad de certificación**y complete el asistente.

        > [!TIP]
        > En la página **Progreso de la instalación** del asistente, no haga clic en **Cerrar**. En su lugar, haga clic en el vínculo para **Configurar Servicios de certificados de Active Directory en el servidor de destino**. Se abrirá el asistente para **Configuración de AD CS** que se usa en la siguiente tarea. Una vez abierta la configuración de AD CS, puede cerrar al Asistente para agregar roles y características.

    2.  Cuando NDES se agrega al servidor, el asistente instala también IIS. Asegúrese de que IIS tenga las siguientes configuraciones:

        -   **Servidor web** &gt; **Seguridad** &gt; **Filtrado de solicitudes**

        -   **Servidor web** &gt; **Desarrollo de aplicaciones** &gt; **ASP.NET 3.5**. Al instalar ASP.NET 3.5 se instala .NET Framework 3.5. Al instalar .NET Framework 3.5, se instala tanto la característica básica **.NET Framework 3.5** como la característica **Activación HTTP**.

        -   **Servidor web** &gt; **Desarrollo de aplicaciones** &gt; **ASP.NET 4.5**. Al instalar ASP.NET 4.5 se instala .NET Framework 4.5. Al instalar .NET Framework 4.5, se instalan la característica básica **.NET Framework 4.5** y las características **ASP.NET 4.5**, **Servicios WCF** &gt; **Activación HTTP**.

        -   **Herramientas de administración** &gt; **Compatibilidad con la administración de IIS 6** &gt; **Compatibilidad con la metabase de IIS 6**

        -   **Herramientas de administración** &gt; **Compatibilidad con la administración de IIS 6** &gt; **Compatibilidad con WMI de IIS 6**

  2.  En el servidor, agregue la cuenta de servicio NDES como miembro del grupo **IIS_IUSR**.

   3.  En un símbolo del sistema con privilegios elevados, ejecute el siguiente comando para establecer el SPN de la cuenta de servicio SCEP:

`**setspn -s http/&lt;DNS name of NDES Server&gt; &lt;Domain name&gt;\&lt;NDES Service account name&gt;**`

   Por ejemplo, si el servidor NDES se denomina **Server01**, su dominio es **Contoso.com**y la cuenta de servicio es **NDESService**, use:

`**setspn –s http/Server01.contoso.com contoso\NDESService**`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>Paso 4: configurar NDES para su uso con Intune
En esta tarea tendrá que:

-   Configurar NDES para su uso con la CA emisora

-   Enlazar el certificado de autenticación (SSL) de servidor en IIS

-   Configurar el filtrado de solicitudes en IIS


1.  En el servidor NDES, abra el asistente para Configuración de AD CS y realice las configuraciones siguientes:

    > [!TIP]
    > Si hizo clic en el vínculo de la tarea anterior, este asistente ya está abierto. De lo contrario, abra el Administrador del servidor para obtener acceso a la configuración posterior a la implementación de Servicios de certificados de Active Directory.

    -   En la página **Servicios de rol** , seleccione el **Servicio de inscripción de dispositivos de red**.

    -   En la página **Cuenta de servicio para NDES** , especifique la cuenta de servicio NDES.

    -   En la página **CA para NDES** , haga clic en **Seleccionar**y seleccione la CA emisora en donde configuró la plantilla de certificado.

    -   En la página **Criptografía para NDES** , establezca la longitud de clave que satisfaga los requisitos de su empresa.

    En la página **Confirmación** , haga clic en **Configurar** para completar el asistente.

2.  Una vez finalizado el asistente, edite la siguiente clave del registro en el servidor NDES:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\**

    Para editar esta clave, identifique el **Propósito**de la plantilla de certificado disponible en la pestaña **Tratamiento de la solicitud** y, luego, modifique la entrada correspondiente del Registro reemplazando los datos existentes por el nombre de la plantilla de certificado (no el nombre para mostrar de la plantilla) que especificó en la tarea 1. La tabla siguiente asigna el propósito de la plantilla de certificado a los valores del registro:

    |Plantilla de certificado Propósito (en la pestaña Tratamiento de la solicitud)|Valor del registro que se va a editar|Valor que se ve en la consola de administración de Intune para el perfil de SCEP|
    |--------------------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------|
    |Firma|SignatureTemplate|Firma digital|
    |Cifrado|EncryptionTemplate|Cifrado de clave|
    |Firma y cifrado|GeneralPurposeTemplate|Cifrado de clave<br /><br />Firma digital|
    Por ejemplo, si el propósito de la plantilla de certificado es **Cifrado**, edite el valor **EncryptionTemplate** para que sea el nombre de la plantilla de certificado.

3. El servidor NDES recibe direcciones URL (consultas) muy largas que requieren que se agreguen dos entradas del Registro:

    |Ubicación|Valor|Tipo|Datos|
    |-------|-----|----|----|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxFieldLength|DWORD|65534 (decimal)|
    |HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters|MaxRequestBytes|DWORD|65534 (decimal)|


4. En el Administrador de IIS, seleccione **Sitio web predeterminado** -> **Filtrado de solicitudes** -> **Modificar configuración de característica** y cambie **Longitud máxima de dirección URL** y **Cadena de consulta máxima** a *65534*, como se muestra.

    ![Longitud de dirección URL y de consulta máximas de IIS](.\media\SCEP_IIS_max_URL.png)

5.  Reinicie el servidor. La ejecución de **iisreset** en el servidor no es suficiente para finalizar estos cambios.
6. Vaya a http://*FQDN*/certsrv/mscep/mscep.dll. Debería ver una página SCEP similar a esta:

    ![Probar SCEP](.\media\SCEP_NDES_URL.png)

    Si aparece **503 Servicio no disponible**, compruebe el Visor de eventos. Es probable que el grupo de aplicaciones se haya detenido debido a la falta de un derecho para el usuario SCEP. Esos derechos se describen en la tarea 1.

##### <a name="to-install-and-bind-certificates-on-the-ndes-server"></a>Para instalar y enlazar certificados en el servidor NDES

1.  En el servidor NDES, solicite e instale un certificado de **autenticación de servidor** de la CA interna o de una CA pública. Después, este certificado SSL se enlaza en IIS.

    > [!TIP]
    > Después de enlazar el certificado SSL en IIS, instale un certificado de autenticación del cliente. Este certificado puede estar emitido por una CA de confianza para el servidor NDES. Aunque no es un procedimiento recomendado, puede usar el mismo certificado para la autenticación del servidor y del cliente, siempre y cuando el certificado tenga dos usos mejorados de clave (EKU). Revise los siguientes pasos para obtener información sobre estos certificados de autenticación.

    1.  Después de obtener el certificado de autenticación de servidor, abra el **Administrador de IIS**, seleccione el **Sitio web predeterminado** en el panel **Conexiones** y haga clic en **Enlaces** en el panel **Acciones** .

    2.  Haga clic en **Agregar**, establezca **Tipo** en **https**y compruebe que el puerto sea el **443**. (Solo se admite el puerto 443 para Intune independiente).

    3.  En el caso de **Certificado SSL**, especifique el certificado de autenticación de servidor.

        > [!NOTE]
        > Si el servidor NDES usa tanto un nombre externo como interno para una única dirección de red, el certificado de autenticación de servidor debe tener un **Nombre del firmante** con un nombre de servidor público externo y un **Nombre alternativo del firmante** que incluya el nombre del servidor interno.

2.  En el servidor NDES, solicite e instale un certificado de **autenticación del cliente** de la CA interna o de una entidad de certificación pública. Este puede ser el mismo certificado que el certificado de autenticación de servidor si dicho certificado tiene ambas capacidades.

    El certificado de autenticación del cliente debe tener las siguientes propiedades:

    **Uso mejorado de clave**: debe incluir **Autenticación del cliente**.

    **Nombre del firmante:** debe ser igual al nombre DNS del servidor donde se instala el certificado (el servidor NDES).

##### <a name="to-configure-iis-request-filtering"></a>Para configurar el filtrado de solicitudes de IIS

1.  En el servidor NDES, abra el **Administrador de IIS**, seleccione el **Sitio web predeterminado** en el panel **Conexiones** y abra **Filtrado de solicitudes**.

2.  Haga clic en **Modificar configuración de característica** y después configure los valores:

    **Cadena de consulta (bytes)** = **65534**

    **Longitud máxima de dirección URL (bytes)** = **65534**

3.  Revise la siguiente clave del registro:

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    Asegúrese de que los siguientes valores se establezcan como entradas DWORD:

    Nombre: **MaxFieldLength**, con un valor decimal de **65534**

    Nombre: **MaxRequestBytes**, con un valor decimal de **65534**

4. Reinicie el servidor de NDES. El servidor está ya preparado para admitir el conector certificado.

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>Paso 5: habilitar, instalar y configurar Intune Certificate Connector
En esta tarea tendrá que:

- Habilitar la compatibilidad con SCEP en Intune.
- Descargar, instalar y configurar Certificate Connector en un servidor de su entorno. Para admitir la alta disponibilidad, puede instalar varias instancias de Certificate Connector en distintos servidores.

##### <a name="to-download-install-and-configure-the-certificate-connector"></a>Para descargar, instalar y configurar Certificate Connector
![ConnectorDownload](./media/certificates-download-connector.png)   
 
1. Inicie sesión en el portal de Azure. 
2. Seleccione **Más servicios** > **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, seleccione **Configuración del dispositivo**.
4. En la hoja **Configuración del dispositivo**, seleccione **Entidad de certificación**.
5. Haga clic en **Agregar** y seleccione **Descargue el archivo del conector**. Guarde la descarga en una ubicación a la que pueda acceder desde el servidor donde vaya a realizar la instalación. 
6.  Una vez finalizada la descarga, ejecute el instalador descargado (**ndesconnectorssetup.exe**) en un servidor de Windows Server 2012 R2. El instalador también instala el módulo de directivas para SCEP y el servicio web de CRP. (El servicio web de CRP, CertificateRegistrationSvc, se ejecuta como una aplicación en IIS).

    > [!NOTE]
    > Cuando instala NDES para Intune independiente, el servicio de CRP se instala automáticamente con Certificate Connector. Al usar Intune con Configuration Manager, instale el punto de registro de certificados como un rol de sistema de sitio independiente.

3.  Cuando se le solicite el certificado de cliente para el conector de certificado, haga clic en **Seleccionar** y seleccione el certificado de **autenticación del cliente** instalado en el servidor NDES en la tarea 3.

    Después de seleccionar el certificado de autenticación del cliente, volverá a la superficie del **Certificado de cliente para el conector de certificado para Microsoft Intune** . Aunque no se muestra el certificado seleccionado, haga clic en **Siguiente** para ver las propiedades de dicho certificado. Haga clic en **Siguiente**y, luego, en **Instalar**.

4.  Cuando se complete el asistente, pero antes de cerrarlo, haga clic en **Iniciar la UI del conector de certificado**.

    > [!TIP]
    > Si cierra al asistente antes de iniciar la IU del conector de certificado, puede volver a abrirlo ejecutando el comando siguiente:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  En la IU **Conector de certificado** :

    Haga clic en **Iniciar sesión** y escriba sus credenciales de administrador de servicio de Intune o las credenciales de un administrador de inquilinos con permiso de administración global.

    > [!IMPORTANT]
    > La cuenta de usuario debe tener una licencia válida de Intune asignada. Si la cuenta de usuario no tiene una licencia válida de Intune, NDESConnectorUI.exe produce un error.

    Si su organización usa un servidor proxy y el proxy es necesario para que el servidor NDES obtenga acceso a Internet, haga clic en **Usar servidor proxy** e indique el nombre del servidor proxy, el puerto y las credenciales de la cuenta para conectarse.

    Seleccione la pestaña **Avanzadas** , proporcione las credenciales de una cuenta que tenga el permiso **Emitir y administrar certificados** en la CA emisora y haga clic en **Aplicar**.

    Ahora puede cerrar la IU del conector de certificado.

6.  Abra un símbolo del sistema, escriba **services.msc** y haga clic en **Entrar**. Haga clic con el botón derecho en **Servicio del conector de Intune** y luego en **Reiniciar**.

Para validar que el servicio se ejecuta, abra un explorador y escriba la siguiente dirección URL, que debe devolver un error **403** :

**http:// &lt;FQDN_de_sur_servidor_NDES&gt;/certsrv/mscep/mscep.dll**

## <a name="how-to-create-a-scep-certificate-profile"></a>Creación de un perfil de certificado SCEP

1. En Azure Portal, seleccione la carga de trabajo **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, seleccione **Administrar** > **Perfiles**.
3. En la hoja de perfiles, seleccione **Crear perfil**.
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de certificado SCEP.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo para este certificado SCEP. Actualmente puede seleccionar una de las siguientes plataformas para la configuración de restricciones de dispositivos:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de los **tipos de perfil**, seleccione **Certificado SCEP**.
7. En la hoja **Certificado SCEP**, configure los siguientes valores:
    - **Período de validez del certificado**: si ha ejecutado el comando **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** en la entidad de certificación emisora, que permite un período de validez personalizado, puede especificar la cantidad de tiempo restante antes de que expire el certificado.<br>Puede especificar un valor inferior al período de validez de la plantilla de certificado especificada, pero no superior. Por ejemplo, si el período de validez del certificado en la plantilla de certificado es de dos años, puede especificar un valor de un año, pero no un valor de cinco años. El valor también debe ser menor que el período de validez restante del certificado de la CA emisora. 
    - **Proveedor de almacenamiento de claves (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10): especifique dónde se almacena la clave del certificado. Elija uno de los siguientes valores:
        - **Inscribirse en KSP Módulo de plataforma segura (TPM) si está presente, si no en KSP Software**
        - **Inscribirse en KSP del Módulo de plataforma segura (TPM) o se producirá un error**
        - **Inscribirse en Passport o se producirá un error (Windows 10 y versiones posteriores)**
        - **Inscribirse en el KSP Software**
    - **Formato de nombre del sujeto**: en la lista, seleccione cómo Intune crea automáticamente el nombre del sujeto en la solicitud de certificado. Si el certificado es para un usuario, también puede incluir la dirección de correo electrónico del usuario en el nombre del sujeto. Elija de entre las siguientes opciones:
        - **No configurado**.
        - **Nombre común**
        - **Nombre común, incluyendo la dirección de correo electrónico**
        - **Nombre común como correo electrónico**
        - **IMEI (Identidad de equipo móvil internacional)**
        - **Número de serie**
        - **Personalizado**: cuando se selecciona esta opción, se muestra otro campo de lista desplegable. Utilice este campo para escribir un formato de nombre de firmante personalizado. Las dos variables admitidas para el formato personalizado son **nombre común (CN)** y **correo electrónico (E)**. Mediante una combinación de una o varias de estas cadenas estáticas y variables, puede crear un formato de nombre de firmante personalizado, como este: **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US** En este ejemplo, ha creado un formato de nombre del firmante que, además de las variables CN y E, usa cadenas para los valores Unidad organizativa, Organización, Ubicación, Estado y País. [En este tema](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) se muestra la función **CertStrToName** y sus cadenas admitidas.
        
    - **Subject alternative name** (Nombre alternativo del sujeto): especifique cómo Intune creará automáticamente los valores del nombre alternativo del sujeto (SAN) en la solicitud de certificado. Por ejemplo, si seleccionó un tipo de certificado de usuario, puede incluir el nombre principal de usuario (UPN) en el nombre alternativo del sujeto. Si el certificado de cliente se usa para autenticar un servidor de directivas de redes, debe establecer el nombre alternativo del sujeto en el UPN. 
    - **Uso de la clave**: especifique las opciones de uso de claves para el certificado. Puede elegir entre las siguientes opciones: 
        - **Cifrado de clave**: permite el intercambio de claves solo si la clave está cifrada. 
        - **Firma digital**: permite el intercambio de claves solo cuando una firma digital ayuda a proteger la clave. 
    - **Tamaño de la clave (bits)**: seleccione el número de bits que contiene la clave. 
    - **Algoritmo hash** (Android, Windows Phone 8.1, Windows 8.1, Windows 10): seleccione uno de los tipos de algoritmos hash disponibles para usar con este certificado. Seleccione el nivel máximo de seguridad que admiten los dispositivos de conexión. 
    - **Certificado raíz**: elija un perfil de certificado de CA raíz que previamente haya configurado y asignado al usuario o dispositivo. Este certificado de CA debe ser el certificado raíz para la entidad de certificación que emite el certificado que va a configurar en este perfil de certificado. 
    - **Uso mejorado de clave**: seleccione **Agregar** para agregar valores para la finalidad prevista del certificado. En la mayoría de los casos, el certificado requiere **Autenticación de cliente** para que el usuario o dispositivo pueda autenticarse en un servidor. Sin embargo, puede agregar otros usos de clave según sea necesario. 
    - **Configuración de la inscripción**
        - **Umbral de renovación (%)**: especifique qué porcentaje de la duración del certificado tiene que quedar para que el dispositivo solicite la renovación del certificado.
        - **Direcciones URL de servidor SCEP**: especifique una o varias direcciones URL para los servidores NDES que emiten certificados mediante SCEP. 
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.

## <a name="how-to-assign-the-certificate-profile"></a>Asignación del perfil de certificado

Considere los siguiente aspectos antes de asignar perfiles de certificado a grupos:

- Cuando asigna perfiles de certificado a grupos, el archivo de certificado del perfil de certificado de CA de confianza se instala en el dispositivo. El dispositivo usa el perfil de certificado SCEP para crear una solicitud de certificado.
- Los perfiles de certificado solo se instalan en dispositivos que ejecutan la plataforma usada al crear el perfil.
- Puede asignar perfiles de certificado en recopilaciones de usuarios o en recopilaciones de dispositivos.
- Para publicar rápidamente un certificado en un dispositivo una vez inscrito el dispositivo, asigne el perfil de certificado en un grupo de usuarios (no en un grupo de dispositivos). Si lo asigna en un grupo de dispositivos, deberá efectuar un registro completo del dispositivo para que el dispositivo reciba directivas.
- Aunque asigne cada perfil por separado, también deberá asignar la CA raíz de confianza y el perfil SCEP o PKCS. De lo contrario, se produce un error en la directiva del certificado SCEP o PKCS.

Para información sobre cómo asignar perfiles, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

