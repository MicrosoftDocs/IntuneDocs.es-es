---
# required metadata

title: Configurar la infraestructura de certificados | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3a435650-3891-4754-8abc-4bbac244f33b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: kmyrup
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configurar la infraestructura de certificados
En este tema se describe qué se necesita para crear e implementar perfiles de certificado.

Para realizar cualquier autenticación basada en certificados en la organización, se necesita una entidad de certificación empresarial.

Para usar perfiles de certificado SCEP, aparte de la entidad de certificación empresarial, también se necesita lo siguiente:

-   Un servidor que ejecute el Servicio de inscripción de dispositivos de red

-   El conector de certificado de Intune, que se instala en el servidor de Windows Server 2012 R2 que ejecuta NDES

Para usar perfiles de certificado .PFX, aparte de la entidad de certificación empresarial, también se necesita lo siguiente:

-  Un equipo que puede comunicarse con la entidad de certificación o usar el mismo equipo de la entidad de certificación.

-  El conector de certificado de Intune, que se ejecuta en el equipo que puede comunicarse con la entidad de certificación.

## Infraestructura local


-    **Dominio de Active Directory:** todos los servidores mencionados en esta sección (salvo el servidor Proxy de aplicación web) deben estar unidos al dominio de Active Directory.

-  **Entidad de certificación (CA):** también llamada CA emisora, es necesario disponer de una entidad de certificación (CA) empresarial que se ejecute en una edición Enterprise de Windows Server 2008 R2 o posterior. No se admiten CA independientes. Para obtener instrucciones sobre cómo configurar una entidad de certificación, consulte [Instalar la entidad de certificación](http://technet.microsoft.com/library/jj125375.aspx).
    Si la CA ejecuta Windows Server 2008 R2, se debe [instalar la revisión de KB2483564](http://support.microsoft.com/kb/2483564/).

-  **Servidor NDES (solo SCEP):** en un servidor que ejecute Windows Server 2012 R2 o posterior, debe configurar el Servicio de inscripción de dispositivos de red. En Intune no se puede usar el Servicio de inscripción de dispositivos de red cuando se ejecuta en un servidor que también ejecuta la CA empresarial. Vea la [Orientación para el Servicio de inscripción de dispositivos de red](http://technet.microsoft.com/library/hh831498.aspx) si quiere obtener instrucciones sobre cómo configurar Windows Server 2012 R2 para hospedar el Servicio de inscripción de dispositivos de red.
-  **Equipo que puede comunicarse con la entidad de certificación (.PFX solo):** puede usar el mismo equipo de la entidad de certificación.
-  **Microsoft Intune Certificate Connector:** la consola de administración de Intune se puede usar para descargar el instalador de **Certificate Connector** (**ndesconnectorssetup.exe**). Después, puede ejecutar **ndesconnectorssetup.exe** en el equipo donde desee instalar el conector de certificado. Para perfiles de certificado .PFX, instale el conector de certificado en el equipo que se comunica con la entidad de certificación.
-  **Servidor Proxy de aplicación web (opcional):** puede usar un servidor que ejecute Windows Server 2012 R2 o posterior como servidor Proxy de aplicación web (WAP). Esta configuración:
    -  Permite a los dispositivos recibir certificados mediante una conexión a Internet.
    -  Es una recomendación de seguridad cuando los dispositivos se conectan a través de Internet para recibir y renovar certificados.

> [!NOTE]           
> -    El servidor que hospeda WAP [debe instalar una actualización](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que habilite la compatibilidad con las direcciones URL largas que usa el Servicio de inscripción de dispositivos de red. Esta actualización está incluida en el [paquete acumulativo de actualizaciones de diciembre de 2014](http://support.microsoft.com/kb/3013769)o está disponible por separado, en [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Además, el servidor que hospeda WAP debe tener un certificado SSL que encaje con el nombre que se publica para los clientes externos, así como confiar en el certificado SSL que se usa en el servidor NDES. Estos certificados habilitan al servidor WAP para terminar la conexión SSL entre clientes y crear una nueva conexión SSL hacia el servidor NDES.
Para obtener más información sobre los certificados de WAP, vea la sección sobre cómo **planear certificados** de [Planeamiento de publicación de aplicaciones mediante el Proxy de aplicación web](https://technet.microsoft.com/library/dn383650.aspx). Para obtener información general sobre los servidores WAP, vea [Trabajar con el Proxy de aplicación Web](http://technet.microsoft.com/library/dn584113.aspx).|


### Certificados y plantillas

|Objeto|Detalles|
|----------|-----------|
|**Plantilla de certificado**|Esta plantilla se configura en la CA emisora.|
|**Certificado de autenticación del cliente**|Solicitado desde la CA emisora o la CA pública, instale este certificado en el servidor NDES.|
|**Certificado de autenticación de servidor**|Solicitado desde la CA emisora o la CA pública, este certificado SSL se instala y se enlaza en IIS, en el servidor NDES.|
|**Certificado de CA raíz de confianza**|Expórtelo como archivo **.cer** desde la CA emisora o desde cualquier dispositivo que confíe en la CA emisora e impleméntelo en dispositivos con el perfil de certificado de CA de confianza.<br /><br />Use un único certificado de CA raíz de confianza por cada plataforma de sistema operativo y asócielo a cada perfil de certificado raíz de confianza que cree.<br /><br />Puede usar certificados de CA raíz de confianza adicionales cuando sea necesario. Por ejemplo, podría hacerlo para proporcionar una relación de confianza con una CA que firme los certificados de autenticación de servidor para los puntos de acceso Wi-Fi.|

### Cuentas

|Nombre|Detalles|
|--------|-----------|
|**Cuenta de servicio NDES**|Especifique una cuenta de usuario de dominio que se vaya a usar como cuenta de servicio NDES.|

## Configurar la infraestructura
Para poder configurar perfiles de certificado debe completar las tareas siguientes, que requieren conocimientos de Windows Server 2012 R2 y Servicios de certificados de Active Directory (ADCS):

**Tarea 1:** configurar plantillas de certificado en la entidad de certificación

**Tarea 2 (para el perfil SCEP únicamente):** configurar los requisitos previos en el servidor NDES

**Tarea 3 (para el perfil SCEP únicamente):** configurar NDES para su uso con Intune

**Tarea 4:** habilitar, instalar y configurar Intune Certificate Connector

## Tarea 1: configurar plantillas de certificado en la entidad de certificación
En esta tarea tendrá que:

-   Crear una cuenta de servicio NDES

    > [!NOTE] Para revocar certificados, la cuenta de servicio SCEP necesita derechos para *emitir y administrar certificados* para cada plantilla de certificado usada por un perfil de certificado.

-   Configurar una plantilla de certificado para NDES

-   Publicar la plantilla de certificado para NDES

##### Para configurar la entidad de certificación

1.  Cree una cuenta de usuario de dominio que vaya a usar como cuenta de servicio NDES. Deberá especificar esta cuenta al configurar las plantillas en la CA emisora antes de instalar y configurar NDES.

2.  En la CA emisora, use el complemento Plantillas de certificado para crear una nueva plantilla personalizada o copiar una plantilla existente y, luego, editarla (por ejemplo, la plantilla de usuario) para su uso con NDES.

    La plantilla debe tener las siguientes configuraciones:

    -   Especifique **Nombre para mostrar de plantilla** descriptivo para la plantilla.

    -   En la pestaña **Nombre del firmante** , seleccione **Proporcionado por el solicitante**. (La seguridad la aplica el módulo de directivas de Intune para NDES).

    -   En la pestaña **Extensiones** , asegúrese de que **Descripción de las directivas de aplicación** incluya **Autenticación del cliente**.

        > [!IMPORTANT] En el caso de plantillas de certificado de iOS y Mac OS X, en la pestaña **Extensiones**, edite **Uso de la clave** y asegúrese de que **Firma como prueba de origen** no esté seleccionado.

    -   En la pestaña **Seguridad**, agregue la cuenta de servicio NDES y otórguele permisos de **inscripción**en la plantilla.

3.  Revise la configuración de **Período de validez** en la pestaña **General** de la plantilla. Intune usa de forma predeterminada el valor configurado en la plantilla. Pero tiene la opción de configurar la CA para permitir que el solicitante especifique otro valor, lo que se puede establecer desde la consola de administrador de Intune. Si desea usar siempre el valor de la plantilla, omita el resto de este paso.

    > [!IMPORTANT] Las plataformas iOS y Mac OS X siempre usan el valor establecido en la plantilla independientemente de otras configuraciones que realice.

    Para configurar la CA para permitir que el solicitante especifique el período de validez, en la CA, ejecute los siguientes comandos:

    1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    2.  **net stop certsvc**

    3.  **net start certsvc**

4.  En la CA emisora, use el complemento Entidad de certificación para publicar la plantilla de certificado.

    1.  Seleccione el nodo **Plantillas de certificado**, haga clic en **Acción**-&gt; **Nuevo** &gt; **Plantilla de certificado que se va a emitir** y seleccione la plantilla que creó en el paso 2.

    2.  Valide que la plantilla se publicó visualizándola en la carpeta **Plantillas de certificado** .

5.  Para perfiles .PFX: en el equipo de CA asegúrese de que el equipo que hospeda el conector de certificado de Intune haya inscrito el permiso, para que pueda tener acceso a la plantilla utilizada en la creación del perfil .PFX. Establezca ese permiso en la pestaña **Seguridad** de las propiedades del equipo de CA.

## Tarea 2 (para el perfil SCEP únicamente): configurar los requisitos previos en el servidor NDES
En esta tarea tendrá que:

-   Agregar NDES a un servidor con Windows Server y configurar IIS para que admita NDES

-   Agregar la cuenta de servicio NDES al grupo IIS_IUSRS

-   Establecer el SPN para la cuenta de servicio NDES

##### Para configurar los requisitos previos para el servidor NDES

1.  En el servidor que hospedará NDES, debe iniciar sesión como **Administrador de la empresa**y, luego, usar el [Asistente para agregar roles y características](https://technet.microsoft.com/library/hh831809.aspx) para instalar NDES:

    1.  En el asistente, seleccione **Servicios de certificados de Active Directory** para obtener acceso a los servicios de rol de AD CS. Seleccione el **Servicio de inscripción de dispositivos de red**, desactive **Entidad de certificación**y complete el asistente.

        > [!TIP]
        > En la página **Progreso de la instalación** del asistente, no haga clic en **Cerrar**. En su lugar, haga clic en el vínculo para **Configurar Servicios de certificados de Active Directory en el servidor de destino**. Se abrirá el asistente para **Configuración de AD CS** que se usa en la siguiente tarea. Una vez abierta la configuración de AD CS, puede cerrar al Asistente para agregar roles y características.

    2.  Cuando NDES se agrega al servidor, el asistente instala también IIS. Asegúrese de que IIS tenga las siguientes configuraciones:

        -   **Servidor web** &gt; **Seguridad** &gt; **Filtrado de solicitudes**

        -   **Servidor web** &gt; **Desarrollo de aplicaciones** &gt; **ASP.NET 3.5**. Al instalar ASP.NET 3.5, se instalará .NET Framework 3.5. Al instalar .NET Framework 3.5, se instala tanto la característica básica **.NET Framework 3.5** como la característica **Activación HTTP**.

        -   **Servidor web** &gt; **Desarrollo de aplicaciones** &gt; **ASP.NET 4.5**. Al instalar ASP.NET 4,5 se instalará .NET Framework 4,5. Al instalar .NET Framework 4.5, se instalan la característica básica **.NET Framework 4.5** y las características **ASP.NET 4.5**, **Servicios WCF** &gt; **Activación HTTP**.

        -   **Herramientas de administración** &gt; **Compatibilidad con la administración de IIS 6** &gt; **Compatibilidad con la metabase de IIS 6**

        -   **Herramientas de administración** &gt; **Compatibilidad con la administración de IIS 6** &gt; **Compatibilidad con WMI de IIS 6**

2.  En el servidor, agregue la cuenta de servicio NDES como miembro del grupo **IIS_IUSR**.

3.  Ejecute el siguiente comando para establecer el SPN de la cuenta de servicio NDES:

    -   **setspn -s http/&lt;nombre DNS del servidor NDES&gt; &lt;nombre de dominio&gt;\&lt;nombre de la cuenta de servicio NDES&gt;**

    Por ejemplo, si el servidor NDES se denomina **Server01**, su dominio es **Contoso.com**y la cuenta de servicio es **NDESService**, use:

    -   **setspn –s http/Server01.contoso.com contoso\NDESService**

## Tarea 3 (para el perfil SCEP únicamente): configurar NDES para su uso con Microsoft Intune 
En esta tarea tendrá que:

-   Configurar NDES para su uso con la CA emisora

-   Enlazar el certificado de autenticación (SSL) de servidor en IIS

-   Configurar el filtrado de solicitudes en IIS

##### Para configurar NDES para su uso con Intune

1.  En el servidor NDES, abra el asistente para Configuración de AD CS y realice las siguientes configuraciones.

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

3.  Después de editar el registro, ejecute **iisreset** en el servidor para forzar al servidor a recoger los cambios recientes de configuración.

##### Para instalar y enlazar certificados en el servidor NDES

1.  En el servidor NDES, solicite e instale un certificado de **autenticación de servidor** de la CA interna o de una CA pública. Este certificado SSL se enlazará luego en IIS.

    > [!TIP]
    > Después de enlazar el certificado SSL en IIS, también debe instalar un certificado de autenticación del cliente. Este certificado puede estar emitido por una CA de confianza para el servidor NDES. Aunque no es un procedimiento recomendado, puede usar el mismo certificado para la autenticación de servidor y del cliente, siempre y cuando el certificado tenga dos usos mejorados de clave (EKU). Revise los siguientes pasos para obtener información sobre estos certificados de autenticación.

    1.  Después de obtener el certificado de autenticación de servidor, abra el **Administrador de IIS**, seleccione el **Sitio web predeterminado** en el panel **Conexiones** y haga clic en **Enlaces** en el panel **Acciones** .

    2.  Haga clic en **Agregar**, establezca **Tipo** en **https**y compruebe que el puerto sea el **443**. (Solo se admite el puerto 443 para Intune independiente).

    3.  En el caso de **Certificado SSL**, especifique el certificado de autenticación de servidor.

        > [!NOTE] Si el servidor SCEP usa tanto un nombre externo como uno interno para una única dirección de red, el certificado de autenticación del servidor debe tener un **Nombre del sujeto** con un nombre de servidor público externo y un **Nombre alternativo del sujeto** que incluya el nombre del servidor interno.

2.  En el servidor NDES, solicite e instale un certificado de **autenticación del cliente** de la CA interna o de una entidad de certificación pública. Este puede ser el mismo certificado que el certificado de autenticación de servidor si dicho certificado tiene ambas capacidades.

    El certificado de autenticación del cliente debe tener las siguientes propiedades:

    **Uso mejorado de clave**: debe incluir **Autenticación del cliente**.

    **Nombre del firmante:** debe ser igual al nombre DNS del servidor donde se instala el certificado (el servidor NDES).

##### Para configurar el filtrado de solicitudes de IIS

1.  En el servidor NDES, abra el **Administrador de IIS**, seleccione el **Sitio web predeterminado** en el panel **Conexiones** y abra **Filtrado de solicitudes**.

2.  Haga clic en **Modificar configuración de característica**y configure lo siguiente:

    **Cadena de consulta (bytes)** = **65534**

    **Longitud máxima de dirección URL (bytes)** = **65534**

3.  Revise la siguiente clave del registro:

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    Asegúrese de que los siguientes valores se establezcan como entradas DWORD:

    Nombre: **MaxFieldLength**, con un valor decimal de **65534**

    Nombre: **MaxRequestBytes**, con un valor decimal de **65534**

4.  Reinicie el servidor de NDES. El servidor está ya preparado para admitir el conector certificado.

## Tarea 4: habilitar, instalar y configurar el conector de certificado de Intune (para certificados SCEP y .PFX)
En esta tarea tendrá que:

Habilitar la compatibilidad de NDES en Intune

Descargar, instalar y configurar el conector de certificado en el servidor NDES

##### Para habilitar la compatibilidad del conector de certificado

1.  Abra la [consola de administración de Intune](https://manage.microsoft.com), haga clic en **Administración** &gt; **Certificate Connector**.

2.  Haga clic en **Configurar On-Premises Certificate Connector**.

3.  Seleccione **Habilitar conector de certificado**y, a continuación, haga clic en **Aceptar**.

##### Para descargar, instalar y configurar el conector de certificado

1.  Abra la [consola de administración de Intune](https://manage.microsoft.com) y haga clic en **Administración** &gt; **Administración de dispositivos móviles** &gt; **Certificate Connector** &gt; **Descargar Certificate Connector**.

2.  Una vez finalizada la descarga, ejecute el instalador descargado (**ndesconnectorssetup.exe**):

    -   Para los certificados .PFX, ejecute el instalador en el equipo que puede conectarse con la entidad de certificación. Elija la opción de distribución .PFX y haga clic en Instalar. Cuando haya finalizado la instalación, siga creando un perfil de certificado según se indica en [Configure certificate profiles (Configurar perfiles de certificado)](configure-intune-certificate-profiles.md).

    -   Para los certificados SCEP, ejecute el instalador en un servidor de Windows Server 2012 R2

    Para la opción de SCEP, el instalador también instala el módulo de directivas para NDES y el servicio web de CRP. (El servicio web de CRP, CertificateRegistrationSvc, se ejecuta como una aplicación en IIS).

    > [!NOTE]
    > Cuando instala NDES para Intune independiente, el servicio de CRP se instala automáticamente con Certificate Connector. Al usar Intune con Configuration Manager, instale el punto de registro de certificados como un rol de sistema de sitio independiente.

3.  Cuando se le solicite el certificado de cliente para el conector de certificado, haga clic en **Seleccionar**y seleccione el certificado de **autenticación del cliente** instalado en el servidor NDES en la tarea 3.

    Después de seleccionar el certificado de autenticación del cliente, volverá a la superficie del **Certificado de cliente para el conector de certificado para Microsoft Intune** . Aunque no se muestra el certificado seleccionado, haga clic en **Siguiente** para ver las propiedades de dicho certificado. Haga clic en **Siguiente**y, luego, en **Instalar**.

4.  Cuando se complete el asistente, pero antes de cerrarlo, haga clic en **Iniciar la UI del conector de certificado**.

    > [!TIP] Si cierra al asistente antes de iniciar la IU de Certificate Connector, puede volver a abrirlo si ejecuta el comando siguiente:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  En la IU **Conector de certificado** :

    Haga clic en **Iniciar sesión** y escriba sus credenciales de administrador de servicio de Intune o las credenciales de un administrador de inquilinos con permiso de administración global.

    Si su organización usa un servidor proxy y el proxy es necesario para que el servidor NDES obtenga acceso a Internet, haga clic en **Usar servidor proxy** e indique el nombre del servidor proxy, el puerto y las credenciales de la cuenta para conectarse.

    Seleccione la pestaña **Avanzadas** , proporcione las credenciales de una cuenta que tenga el permiso **Emitir y administrar certificados** en la CA emisora y haga clic en **Aplicar**.

    Ahora puede cerrar la IU del conector de certificado.

6.  Abra un símbolo del sistema, escriba **services.msc** y haga clic en **Entrar**. Haga clic con el botón derecho en **Servicio del conector de Intune** y luego en **Reiniciar**.

Para validar que el servicio se ejecuta, abra un explorador y escriba la siguiente dirección URL, que debe devolver un error **403** :

**http:// &lt;FQDN_del_servidor_NDES&gt;/certsrv/mscep/mscep.dll**

### Pasos siguientes
Ya está listo para configurar perfiles de certificado, como se describe en [Configure certificate profiles](configure-intune-certificate-profiles.md) (Configurar perfiles de certificado).


<!--HONumber=Jun16_HO1-->


