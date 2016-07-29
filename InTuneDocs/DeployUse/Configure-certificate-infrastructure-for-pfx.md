---
title: Configurar la infraestructura de certificados para PFX | Microsoft Intune
description: Cree e implemente perfiles de certificado .PFX.
keywords: 
author: nbigman
manager: angrobe
ms.date: 05/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 2f45c54d18156469488c77600626ea359374a588



---
# Configurar la infraestructura de certificados
En este tema se describe qué se necesita para crear e implementar perfiles de certificado .PFX.

Para realizar cualquier autenticación basada en certificados en la organización, se necesita una entidad de certificación empresarial.

Para usar perfiles de certificado .PFX, aparte de la entidad de certificación empresarial, también se necesita lo siguiente:

-   Un equipo que pueda comunicarse con la entidad de certificación; también puede usar el propio equipo de la entidad de certificación.

 -  El conector de certificado de Intune, que se ejecuta en el equipo que puede comunicarse con la entidad de certificación.

## Descripción de infraestructura local


-    **Dominio de Active Directory:** todos los servidores mencionados en esta sección (salvo el servidor Proxy de aplicación web) deben estar unidos al dominio de Active Directory.

-  **Entidad de certificación (CA):** también llamada CA emisora, es necesario disponer de una entidad de certificación (CA) empresarial que se ejecute en una edición Enterprise de Windows Server 2008 R2 o posterior. No se admiten CA independientes. Para obtener instrucciones sobre cómo configurar una entidad de certificación, consulte [Instalar la entidad de certificación](http://technet.microsoft.com/library/jj125375.aspx).
    Si la CA ejecuta Windows Server 2008 R2, se debe [instalar la revisión de KB2483564](http://support.microsoft.com/kb/2483564/).

 -  **Equipo que pueda comunicarse con la entidad de certificación:** también puede usar el propio equipo de la entidad de certificación.
-  **Microsoft Intune Certificate Connector:** la consola de administración de Intune se puede usar para descargar el instalador de **Certificate Connector** (**ndesconnectorssetup.exe**). Después, puede ejecutar **ndesconnectorssetup.exe** en el equipo donde desee instalar el conector de certificado. Para perfiles de certificado .PFX, instale el conector de certificado en el equipo que se comunica con la entidad de certificación.
-  **Servidor Proxy de aplicación web** (opcional): puede usar un servidor con Windows Server 2012 R2 o posterior como servidor Proxy de aplicación web (WAP). Esta configuración:
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
|**Certificado de CA raíz de confianza**|Expórtelo como archivo **.cer** desde la CA emisora o desde cualquier dispositivo que confíe en la CA emisora e impleméntelo en dispositivos con el perfil de certificado de CA de confianza.<br /><br />Use un único certificado de CA raíz de confianza por cada plataforma de sistema operativo y asócielo a cada perfil de certificado raíz de confianza que cree.<br /><br />Puede usar certificados de CA raíz de confianza adicionales cuando sea necesario. Por ejemplo, podría hacerlo para proporcionar una relación de confianza con una CA que firme los certificados de autenticación de servidor para los puntos de acceso Wi-Fi.|


## Configurar la infraestructura
Para poder configurar perfiles de certificado debe completar las tareas siguientes, que requieren conocimientos de Windows Server 2012 R2 y Servicios de certificados de Active Directory (ADCS):

**Tarea 1:** configurar plantillas de certificado en la entidad de certificación **Tarea 2:** habilitar, instalar y configurar Intune Certificate Connector

### Tarea 1: configurar plantillas de certificado en la entidad de certificación
En esta tarea se publicará la plantilla de certificado

##### Para configurar la entidad de certificación

1.  En la entidad de certificación emisora, use el complemento Plantillas de certificado para crear una plantilla personalizada o copie una plantilla existente y, luego, edítela (por ejemplo, la plantilla de usuario) para su uso con .pFX.

    La plantilla debe tener las siguientes configuraciones:

    -   Especifique **Nombre para mostrar de plantilla** descriptivo para la plantilla.

    -   En la pestaña **Nombre del firmante** , seleccione **Proporcionado por el solicitante**. (La seguridad la aplica el módulo de directivas de Intune para NDES).

    -   En la pestaña **Extensiones** , asegúrese de que **Descripción de las directivas de aplicación** incluya **Autenticación del cliente**.

        > [!IMPORTANT]
        > En el caso de plantillas de certificado de iOS y Mac OS X, en la pestaña **Extensiones**, edite **Uso de claves** y asegúrese de que la opción **Firma como prueba de origen** no esté seleccionada.


3.  Revise la configuración de **Período de validez** en la pestaña **General** de la plantilla. Intune usa de forma predeterminada el valor configurado en la plantilla. Pero tiene la opción de configurar la CA para permitir que el solicitante especifique otro valor, lo que se puede establecer desde la consola de administrador de Intune. Si desea usar siempre el valor de la plantilla, omita el resto de este paso.

    > [!IMPORTANT]
    > Las plataformas iOS y Mac OS X siempre usan el valor establecido en la plantilla, con independencia de otras configuraciones que realice.

    Para configurar la CA para permitir que el solicitante especifique el período de validez, en la CA, ejecute los siguientes comandos:

    1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    2.  **net stop certsvc**

    3.  **net start certsvc**

4.  En la CA emisora, use el complemento Entidad de certificación para publicar la plantilla de certificado.

    1.  Seleccione el nodo **Plantillas de certificado**, haga clic en **Acción**-&gt; **Nuevo** &gt; **Plantilla de certificado que se va a emitir** y seleccione la plantilla que creó en el paso 2.

    2.  Valide que la plantilla se publicó visualizándola en la carpeta **Plantillas de certificado** .

5.  En el equipo de la entidad de certificación, asegúrese de que el equipo que hospeda Intune Certificate Connector tiene permiso de inscripción para poder acceder a la plantilla usada al crear el perfil .PFX. Establezca ese permiso en la pestaña **Seguridad** de las propiedades del equipo de CA.

### Tarea 2: habilitar, instalar y configurar Intune Certificate Connector
En esta tarea tendrá que:

Descargar, instalar y configurar Certificate Connector

##### Para habilitar la compatibilidad del conector de certificado

1.  Abra la [consola de administración de Intune](https://manage.microsoft.com), haga clic en **Administración** &gt; **Certificate Connector**.

2.  Haga clic en **Configurar On-Premises Certificate Connector**.

3.  Seleccione **Habilitar conector de certificado**y, a continuación, haga clic en **Aceptar**.

##### Para descargar, instalar y configurar el conector de certificado

1.  Abra la [consola de administración de Intune](https://manage.microsoft.com) y haga clic en **Administración** &gt; **Administración de dispositivos móviles** &gt; **Certificate Connector** &gt; **Descargar Certificate Connector**.

2.  Una vez finalizada la descarga, ejecute el instalador descargado (**ndesconnectorssetup.exe**):

  Ejecute el instalador en el equipo que puede conectarse con la entidad de certificación. Elija la opción de distribución .PFX y haga clic en Instalar. Cuando haya finalizado la instalación, siga creando un perfil de certificado según se indica en [Configure certificate profiles (Configurar perfiles de certificado)](configure-intune-certificate-profiles.md).

   <!-- Not sure about step 3 below -->

3.  Cuando se le solicite el certificado de cliente para Certificate Connector, haga clic en **Seleccionar** y seleccione el certificado de **autenticación del cliente** instalado en la tarea 3.

    Después de seleccionar el certificado de autenticación del cliente, volverá a la superficie del **Certificado de cliente para el conector de certificado para Microsoft Intune** . Aunque no se muestra el certificado seleccionado, haga clic en **Siguiente** para ver las propiedades de dicho certificado. Haga clic en **Siguiente**y, luego, en **Instalar**.

4.  Cuando se complete el asistente, pero antes de cerrarlo, haga clic en **Iniciar la UI del conector de certificado**.

    > [!TIP]
    > Si cierra al asistente antes de iniciar la IU del conector de certificado, puede volver a abrirlo ejecutando el comando siguiente:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  En la IU **Conector de certificado** :

    Haga clic en **Iniciar sesión** y escriba sus credenciales de administrador de servicio de Intune o las credenciales de un administrador de inquilinos con permiso de administración global.

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    Seleccione la pestaña **Avanzadas** , proporcione las credenciales de una cuenta que tenga el permiso **Emitir y administrar certificados** en la CA emisora y haga clic en **Aplicar**.

    Ahora puede cerrar la IU del conector de certificado.

6.  Abra un símbolo del sistema, escriba **services.msc** y haga clic en **Entrar**. Haga clic con el botón derecho en **Servicio del conector de Intune** y luego en **Reiniciar**.

Para validar que el servicio se ejecuta, abra un explorador y escriba la siguiente dirección URL, que debe devolver un error **403** :

**http:// &lt;FQDN_del_servidor_NDES&gt;/certsrv/mscep/mscep.dll**

### Pasos siguientes
Ya está listo para configurar perfiles de certificado, como se describe en [Configure certificate profiles](Configure-Intune-certificate-profiles.md) (Configurar perfiles de certificado).



<!--HONumber=Jul16_HO4-->


