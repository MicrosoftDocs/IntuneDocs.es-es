---
title: Configurar la infraestructura de certificados para PFX
description: Cree e implemente perfiles de certificado .PFX.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/17/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: vinaybha
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 819c314b2fe69077fb545afa670587c85d4fa7ef
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="configure-certificate-infrastructure"></a>Configurar la infraestructura de certificados

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

En este tema se describe qué se necesita para crear e implementar perfiles de certificado .PFX.

Para realizar cualquier autenticación basada en certificados en la organización, se necesita una entidad de certificación empresarial.

Para usar perfiles de certificado .PFX, aparte de la entidad de certificación empresarial, también se necesita lo siguiente:

-   Un equipo que pueda comunicarse con la entidad de certificación; también puede usar el propio equipo de la entidad de certificación.

-  El conector de certificado de Intune, que se ejecuta en el equipo que puede comunicarse con la entidad de certificación.

## <a name="on-premises-infrastructure-description"></a>Descripción de infraestructura local


- **Dominio de Active Directory:** todos los servidores mencionados en esta sección (salvo el servidor Proxy de aplicación web) deben estar unidos al dominio de Active Directory.

- **Entidad de certificación**: también llamada CA emisora, es necesario disponer de una entidad de certificación (CA) empresarial que se ejecute en una edición Enterprise de Windows Server 2008 R2 o versión posterior. No se admiten CA independientes. Para obtener instrucciones sobre cómo configurar una entidad de certificación, consulte [Instalar la entidad de certificación](http://technet.microsoft.com/library/jj125375.aspx).
   Si la CA ejecuta Windows Server 2008 R2, se debe [instalar la revisión de KB2483564](http://support.microsoft.com/kb/2483564/).

- **Equipo que pueda comunicarse con la entidad de certificación:** también puede usar el propio equipo de la entidad de certificación.
- **Microsoft Intune Certificate Connector:** la consola de administración de Intune se puede usar para descargar el instalador de **Certificate Connector** (**ndesconnectorssetup.exe**). Después, puede ejecutar **ndesconnectorssetup.exe** en el equipo donde desee instalar el conector de certificado. Para perfiles de certificado .PFX, instale el conector de certificado en el equipo que se comunica con la entidad de certificación.
- **Servidor Proxy de aplicación web** (opcional): puede usar un servidor con Windows Server 2012 R2 o versión posterior como servidor Proxy de aplicación web (WAP). Esta configuración:
   -  Permite a los dispositivos recibir certificados mediante una conexión a Internet.
   -  Es una recomendación de seguridad cuando los dispositivos se conectan a través de Internet para recibir y renovar certificados.

  > [!NOTE]           
  > -    El servidor que hospeda WAP [debe instalar una actualización](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que habilite la compatibilidad con las direcciones URL largas que usa el Servicio de inscripción de dispositivos de red (NDES). Esta actualización está incluida en el [paquete acumulativo de actualizaciones de diciembre de 2014](http://support.microsoft.com/kb/3013769)o está disponible por separado, en [KB3011135](http://support.microsoft.com/kb/3011135).
  >-  Además, el servidor que hospeda WAP debe tener un certificado SSL que coincida con el nombre que se publica para los clientes externos, así como confiar en el certificado SSL que se usa en el servidor NDES. Estos certificados habilitan al servidor WAP para terminar la conexión SSL entre clientes y crear una nueva conexión SSL hacia el servidor NDES.
   Para obtener más información sobre los certificados de WAP, vea la sección sobre cómo **planear certificados** de [Planeamiento de publicación de aplicaciones mediante el Proxy de aplicación web](https://technet.microsoft.com/library/dn383650.aspx). Para obtener información general sobre los servidores WAP, vea [Trabajar con el Proxy de aplicación Web](http://technet.microsoft.com/library/dn584113.aspx).|


### <a name="certificates-and-templates"></a>Certificados y plantillas

|Objeto|Detalles|
|----------|-----------|
|**Plantilla de certificado**|Esta plantilla se configura en la CA emisora.|
|**Certificado de CA raíz de confianza**|Expórtelo como archivo **.cer** desde la CA emisora o desde cualquier dispositivo que confíe en la CA emisora e impleméntelo en dispositivos con el perfil de certificado de CA de confianza.<br /><br />Use un único certificado de CA raíz de confianza por cada plataforma de sistema operativo y asócielo a cada perfil de certificado raíz de confianza que cree.<br /><br />Puede usar certificados de CA raíz de confianza adicionales cuando sea necesario. Por ejemplo, podría hacerlo para proporcionar una relación de confianza con una CA que firme los certificados de autenticación de servidor para los puntos de acceso Wi-Fi.|


## <a name="configure-your-infrastructure"></a>Configurar la infraestructura
Para poder configurar perfiles de certificado, debe llevar a cabo las siguientes tareas. Estas tareas requieren conocimientos de Windows Server 2012 R2 y Servicios de certificados de Active Directory (ADCS):

- **Tarea 1**: configurar plantillas de certificado en la entidad de certificación.
- **Tarea 2**: habilitar, instalar y configurar Intune Certificate Connector.

### <a name="task-1---configure-certificate-templates-on-the-certification-authority"></a>Tarea 1: configurar plantillas de certificado en la entidad de certificación
En esta tarea se publicará la plantilla de certificado.

##### <a name="to-configure-the-certification-authority"></a>Para configurar la entidad de certificación

1.  En la CA emisora, use el complemento Plantillas de certificado para crear una plantilla personalizada o copie una plantilla existente y edítela (por ejemplo, la plantilla de usuario) para usarla con .PFX.

    La plantilla debe incluir lo siguiente:

    -   Especifique **Nombre para mostrar de plantilla** descriptivo para la plantilla.

    -   En la pestaña **Nombre del firmante** , seleccione **Proporcionado por el solicitante**. 

    -   En la pestaña **Extensiones** , asegúrese de que **Descripción de las directivas de aplicación** incluya **Autenticación del cliente**.

        > [!IMPORTANT]
        > En el caso de plantillas de certificado de iOS y Mac OS X, en la pestaña **Extensiones**, edite **Uso de claves** y asegúrese de que la opción **Firma como prueba de origen** no esté seleccionada.

2.  Revise la configuración de **Período de validez** en la pestaña **General** de la plantilla. Intune usa de forma predeterminada el valor configurado en la plantilla. Pero tiene la opción de configurar la CA para permitir que el solicitante especifique otro valor, lo que se puede establecer desde la consola de administrador de Intune. Si desea usar siempre el valor de la plantilla, omita el resto de este paso.

    > [!IMPORTANT]
    > Las plataformas iOS y Mac OS X siempre usan el valor establecido en la plantilla, con independencia de otras configuraciones que efectúe.

    Para configurar la CA para permitir que el solicitante especifique el período de validez, ejecute los siguientes comandos en la CA:

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b.  **net stop certsvc**

    c.  **net start certsvc**

3.  En la CA emisora, use el complemento Entidad de certificación para publicar la plantilla de certificado.

    a.  Seleccione el nodo **Plantillas de certificado**, haga clic en **Acción**-&gt; **Nueva** &gt; **Plantilla de certificado que se va a emitir** y seleccione la plantilla que creó en el paso 2.

    b.  Valide que la plantilla se publicó visualizándola en la carpeta **Plantillas de certificado** .

4.  En el equipo de la entidad de certificación, asegúrese de que el equipo que hospeda Intune Certificate Connector tiene permiso de inscripción para poder tener acceso a la plantilla usada al crear el perfil .PFX. Establezca ese permiso en la pestaña **Seguridad** de las propiedades del equipo de CA.

### <a name="task-2---enable-install-and-configure-the-intune-certificate-connector"></a>Tarea 2: habilitar, instalar y configurar Intune Certificate Connector
En esta tarea tendrá que:

Descargar, instalar y configurar Certificate Connector.

##### <a name="to-enable-support-for-the-certificate-connector"></a>Para habilitar la compatibilidad del conector de certificado

1.  Abra la [consola de administración de Intune](https://manage.microsoft.com) y elija **Administración** &gt; **Certificate Connector**.

2.  Elija **Configurar On-Premises Certificate Connector**.

3.  Seleccione **Habilitar Certificate Connector** y elija **Aceptar**.

##### <a name="to-download-install-and-configure-the-certificate-connector"></a>Para descargar, instalar y configurar Certificate Connector

1. Abra la [consola de administración de Intune](https://manage.microsoft.com) y elija **Administración** &gt; **Administración de dispositivos móviles** &gt; **Certificate Connector** &gt; **Descargar Certificate Connector**.

2. Una vez finalizada la descarga, ejecute el instalador descargado (**ndesconnectorssetup.exe**).

   Ejecute el instalador en el equipo que puede conectarse con la entidad de certificación. Elija la opción de distribución .PFX y elija **Instalar**. Cuando haya finalizado la instalación, siga creando un perfil de certificado según se indica en [Configure certificate profiles (Configurar perfiles de certificado)](configure-intune-certificate-profiles.md).

   <!-- Not sure about step 3 below -->

3. Cuando se le solicite el certificado de cliente para Certificate Connector, elija **Seleccionar** y seleccione el certificado de **autenticación del cliente** instalado en la tarea 3.

   Después de seleccionar el certificado de autenticación del cliente, volverá a la superficie del **Certificado de cliente para el conector de certificado para Microsoft Intune** . Aunque no se muestre el certificado seleccionado, elija **Siguiente** para ver las propiedades de dicho certificado. Luego, elija **Siguiente** e **Instalar**.

4. Cuando se complete el asistente, pero antes de cerrarlo, haga clic en **Iniciar la UI del conector de certificado**.

   > [!TIP]
   > Si cierra al asistente antes de iniciar la IU del conector de certificado, puede volver a abrirlo ejecutando el comando siguiente:
   >
   > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5. En la interfaz de usuario **Conector de certificado**:

   a. Elija **Iniciar sesión** y escriba sus credenciales de administrador de servicio de Intune o las credenciales de un administrador de inquilinos con permiso de administración global.

   b. Seleccione la pestaña **Avanzadas**y proporcione las credenciales de una cuenta que tenga el permiso **Emitir y administrar certificados** en la entidad de certificación emisora.

   c. Elija **Aplicar**.

   Ahora puede cerrar la IU del conector de certificado.

6. Abra un símbolo del sistema y escriba **services.msc**. Después, pulse **ENTRAR**, haga clic con el botón derecho en **Servicio del conector de Intune** y elija **Reiniciar**.


### <a name="next-steps"></a>Pasos siguientes
Ya está listo para configurar los perfiles de certificado, como se describe en [Configurar perfiles de certificado de Intune](Configure-Intune-certificate-profiles.md).
