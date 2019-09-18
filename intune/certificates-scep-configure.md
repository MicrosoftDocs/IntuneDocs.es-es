---
title: 'Configuración de la infraestructura para admitir perfiles de certificado SCEP con Microsoft Intune: Azure | Microsoft Docs'
description: Para usar SCEP en Microsoft Intune, configure el dominio de AD local, cree una entidad de certificación, configure el servidor NDES e instale Intune Certificate Connector.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/28/2019
ms.topic: article
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 909dba16e04b11989caa79112c5a89fbb7c52114
ms.sourcegitcommit: 27e63a96d15bc4062af68c2764905631bd928e7b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71061390"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>Configuración de la infraestructura para admitir SCEP con Intune  
  
Intune admite el uso del Protocolo de inscripción de certificados simple (SCEP) para [autenticar las conexiones a las aplicaciones y los recursos corporativos](certificates-configure.md). SCEP usa el certificado de la entidad de certificación (CA) para proteger el intercambio de mensajes para la solicitud de firma de certificado (CSR). Cuando la infraestructura admita SCEP, puede usar perfiles de *certificado SCEP* de Intune (un tipo de perfil de dispositivo en Intune) para implementar los certificados en los dispositivos. Se necesita Microsoft Intune Certificate Connector para usar perfiles de certificado SCEP con Intune cuando se utiliza una entidad de certificación de Servicios de certificados de Active Directory. El conector no es obligatorio cuando se usan [entidades de certificación de terceros](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration).  

La información de este artículo puede ayudarle a configurar la infraestructura para admitir SCEP cuando se usan Servicios de certificados de Active Directory. Una vez configurada la infraestructura, puede [crear e implementar perfiles de certificado SCEP](certificates-profile-scep.md) con Intune.  

> [!TIP]  
> Intune también admite el uso de [certificados de estándares de criptografía de clave pública #12](certficates-pfx-configure.md).  


## <a name="prerequisites-for-using-scep-for-certificates"></a>Requisitos previos para usar SCEP para los certificados  
Antes de continuar, asegúrese de que ha [creado e implementado un *perfil de certificado de confianza*](certificates-configure.md#export-the-trusted-root-ca-certificate) en los dispositivos que usarán los perfiles de certificado SCEP. Los perfiles de certificado SCEP hacen referencia directamente al perfil de certificado de confianza que se usa para aprovisionar dispositivos con un certificado de entidad de certificación raíz de confianza.  

### <a name="servers-and-server-roles"></a>Servidores y roles de servidor  
La siguiente infraestructura local se debe ejecutar en servidores unidos a dominio en la instancia de Active Directory, con la excepción del servidor proxy de aplicación web.  
- **Entidad de certificación**: use una entidad de certificación (CA) empresarial de Servicios de certificados de Active Directory de Microsoft que se ejecute en una edición Enterprise de Windows Server 2008 R2 con Service Pack 1 o posterior. La versión de Windows Server que use debe seguir siendo compatible con Microsoft. No se admiten CA independientes. Para más información, vea [Instalación de la entidad de certificación](http://technet.microsoft.com/library/jj125375.aspx). Si la entidad de certificación ejecuta Windows Server 2008 R2 SP1, tendrá que [instalar la revisión de KB2483564](http://support.microsoft.com/kb/2483564/).  

- **Rol de servidor NDES**: tendrá que configurar un rol de servidor Servicio de inscripción de dispositivos de red (NDES) en Windows Server 2012 R2 o posterior. En una sección posterior de este artículo, se le guiará a través de la [instalación de NDES](#set-up-ndes).  

  - El servidor en el que se hospeda NDES debe estar unido al dominio y en el mismo bosque que la entidad de certificación (CA) empresarial.  
  - No puede usar NDES instalado en el servidor en el que se hospeda la entidad de certificación empresarial.  
  - Microsoft Intune Certificate Connector se instalará en el mismo servidor en el que se hospeda NDES.  

  Para más información sobre NDES, vea [Orientación para el Servicio de inscripción de dispositivos de red](http://technet.microsoft.com/library/hh831498.aspx) y [Uso de un módulo de directivas con el Servicio de inscripción de dispositivos de red](https://technet.microsoft.com/library/dn473016.aspx).  

- **Microsoft Intune Certificate Connector**: se necesita Microsoft Intune Certificate Connector para usar perfiles de certificado SCEP con Intune. Este artículo le guiará a través de la [instalación de este conector](#install-the-intune-certificate-connector).  

  El conector admite el modo Estándar federal de procesamiento de información (FIPS). FIPS no es obligatorio, pero cuando está habilitado, permite emitir y revocar certificados.  
  - El conector se debe ejecutar en el mismo servidor que el rol de servidor NDES, un servidor que ejecute Windows Server 2012 R2 o posterior.  
  - El conector requiere .NET Framework 4.5 y se incluye automáticamente con Windows Server 2012 R2.  
  - La configuración de seguridad mejorada de Internet Explorer [debe estar deshabilitada en el servidor en el que se hospeda NDES](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) y Microsoft Intune Certificate Connector.  

La infraestructura local siguiente es opcional:  
  Para permitir que los dispositivos de Internet obtengan certificados, debe publicar la dirección URL de NDES externa a la red corporativa. Puede usar Azure AD Application Proxy, Servidor proxy de aplicación web u otro proxy inverso.
  
- **Azure AD Application Proxy** (opcional): puede usar Azure AD Application Proxy en lugar de un servidor proxy de aplicación web (WAP) dedicado para publicar la dirección URL de NDES en Internet. Esto permite que los dispositivos de la intranet y con conexión a Internet obtengan los certificados. Para más información, consulte [Provisión de acceso remoto seguro a aplicaciones locales](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy). 

- **Servidor proxy de aplicación web** (opcional): use un servidor que ejecute Windows Server 2012 R2 o posterior como servidor proxy de aplicación web (WAP) para publicar la dirección URL de NDES en Internet.  Esto permite que los dispositivos de la intranet y con conexión a Internet obtengan los certificados.

  El servidor que hospeda WAP [debe instalar una actualización](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) que habilite la compatibilidad con las direcciones URL largas que usa el Servicio de inscripción de dispositivos de red. Esta actualización está incluida en el [paquete acumulativo de actualizaciones de diciembre de 2014](http://support.microsoft.com/kb/3013769)o está disponible por separado, en [KB3011135](http://support.microsoft.com/kb/3011135).  

  El servidor WAP debe tener un certificado SSL que coincida con el nombre que se ha publicado para los clientes externos y confiar en el certificado SSL que se usa en el equipo en el que se hospeda el servicio NDES. Estos certificados habilitan al servidor WAP para terminar la conexión SSL de los clientes y crear una conexión SSL al servicio NDES.  

  Para más información, consulte [Planeamiento de certificados para WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) e [Información general sobre los servidores WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="accounts"></a>Cuentas   
- **Cuenta de servicio NDES**: antes de configurar NDES, identifique una cuenta de usuario de dominio para usarla como cuenta de servicio NDES. Tendrá que especificar esta cuenta al configurar las plantillas en la entidad de certificación emisora, antes de configurar NDES.  

  Esta cuenta debe tener los siguientes derechos en el servidor en el que se hospeda NDES:  
  - **Inicio de sesión local**  
  - **Iniciar sesión como un servicio**  
  - **Iniciar sesión como trabajo por lotes**  

  Para más información, vea [Creación de una cuenta de usuario de dominio como cuenta de servicio NDES](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account). 
- **Acceso al equipo en el que se hospeda el servicio NDES**: necesitará una cuenta de usuario de dominio con permisos para instalar y configurar roles de servidor de Windows en el servidor en el que instale NDES.  

- **Acceso a la entidad de certificación**: necesitará una cuenta de usuario de dominio que tenga derechos para administrar la entidad de certificación.  

### <a name="network-requirements"></a>Requisitos de red

Se recomienda publicar el servicio NDES a través de un proxy inverso, como el [proxy de aplicaciones de Azure AD, el proxy de acceso web](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/) o un proxy de terceros. Si no usa ningún proxy inverso, permita el tráfico TCP en el puerto 443 desde todos los hosts y direcciones IP de Internet al servicio NDES.  

Permita todos los puertos y protocolos necesarios para la comunicación entre el servicio NDES y cualquier infraestructura de soporte del entorno. Por ejemplo, el equipo en el que se hospeda el servicio NDES necesita comunicarse con la entidad de certificación, los servidores DNS, los controladores de dominio y posiblemente con otros servicios o servidores del entorno, como Configuration Manager.

### <a name="certificates-and-templates"></a>Certificados y plantillas

Al usar SCEP, se usan los siguientes certificados y plantillas.

|Objeto    |Detalles    |
|----------|-----------|
|**Plantilla de certificado SCEP**         |Plantilla que se va a configurar en la entidad de certificación emisora que se usa para satisfacer las solicitudes SCEP de los dispositivos. |
|**Certificado de autenticación del cliente** |Se solicita desde la entidad de certificación emisora o la entidad de certificación pública.<br /> Este certificado se instala en el equipo en el que se hospeda el servicio NDES y se usa en Intune Certificate Connector.<br /> Si el certificado tiene el conjunto de usos de la clave de *cliente* y *autenticación de servidor* (**Usos mejorados de clave**) en la plantilla de entidad de certificación que se usa para emitir este certificado. Después, puede usar el mismo certificado para la autenticación del servidor y el cliente. |
|**Certificado de autenticación de servidor** |Certificado de servidor web solicitado desde la entidad de certificación emisora o la entidad de certificación pública.<br /> Este certificado SSL se instala y enlaza en IIS en el equipo en el que se hospeda NDES.<br />Si el certificado tiene el conjunto de usos de la clave de *cliente* y *autenticación de servidor* (**Usos mejorados de clave**) en la plantilla de entidad de certificación que se usa para emitir este certificado. Después, puede usar el mismo certificado para la autenticación del servidor y el cliente. |
|**Certificado de CA raíz de confianza**       |Para usar un perfil de certificado SCEP, los dispositivos deben confiar en la entidad de certificación (CA) raíz de confianza. Use un *perfil de certificado de confianza* en Intune para aprovisionar usuarios y dispositivos con el certificado de entidad de certificación raíz de confianza. <br/><br/> **-**  Use un único certificado de entidad de certificación raíz de confianza por cada plataforma de sistema operativo y asócielo a cada perfil de certificado de confianza que cree. <br /><br /> **-**  Puede usar certificados de entidad de certificación raíz de confianza adicionales cuando sea necesario. Por ejemplo, es posible que use certificados adicionales para proporcionar una relación de confianza con una entidad de certificación que firme los certificados de autenticación de servidor para los puntos de acceso Wi-Fi. Cree certificados de entidad de certificación raíz de confianza adicionales para entidades de certificación emisoras.  En el perfil de certificado SCEP que cree en Intune, asegúrese de especificar el perfil de entidad de certificación raíz de confianza para la entidad de certificación emisora.<br/><br/> Para obtener información sobre el perfil de certificado de confianza, vea [Exportación del certificado de entidad de certificación raíz de confianza](certificates-configure.md#export-the-trusted-root-ca-certificate) y [Creación de perfiles de certificado de confianza](certificates-configure.md#create-trusted-certificate-profiles) en *Uso de certificados para la autenticación en Intune*. |

## <a name="configure-the-certification-authority"></a>Configurar la entidad de certificación

En las secciones siguientes, aprenderá a:
- Configurar y publicar la plantilla necesaria para NDES. 
- Establecer los permisos necesarios para la revocación de certificados. 

En las secciones siguientes se requieren conocimientos de Windows Server 2012 R2 o versiones posteriores, y de Servicios de certificados de Active Directory (AD CS).  

### <a name="access-your-issuing-ca"></a>Acceso a la entidad de certificación emisora

1. Inicie sesión en la entidad de certificación emisora con una cuenta de dominio con derechos suficientes para administrar la entidad de certificación.  
2. Abra la Consola de administración de Microsoft (MMC) de entidades de certificación. **Ejecute** "certsrv.msc" o, en **Administrador del servidor**, haga clic en **Herramientas** y después en **Entidad de certificación**.
3. Seleccione el nodo **Plantillas de certificado**  y haga clic en **Acción** > **Administrar**.

### <a name="create-the-scep-certificate-template"></a>Creación de la plantilla de certificado SCEP

1. Cree una plantilla de certificado v2 (con compatibilidad con Windows 2003) para usarla como la plantilla de certificado SCEP. Puede:  
   - Use el complemento *Plantillas de certificado* para crear una plantilla personalizada.  
   - Copie una plantilla existente (como Usuario) y luego actualice la copia para usarla como plantilla de NDES.
 
2. Configure las opciones siguientes en las pestañas especificadas de la plantilla:
   - **General**:
     - Desactive **Publicar certificado en Active Directory**.
     - Especifique un **nombre para mostrar de la plantilla** descriptivo para que pueda identificar esta plantilla más adelante.  

   - **Nombre del firmante**:  
     - Seleccione **Proporcionar en la solicitud**. La seguridad la aplica el módulo de directivas de Intune para NDES.  

     ![Plantilla, pestaña Nombre del sujeto](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)
   - **Extensiones**:  
     - Asegúrese de que **Descripción de las directivas de aplicación** incluya **Autenticación de cliente**.  
       > [!IMPORTANT]  
       > Agregue solo las directivas de aplicación que necesite. Confirme las elecciones con los administradores de seguridad.
 
     - Para las plantillas de certificado de iOS y macOS, edite también **Uso de claves** y asegúrese de que la opción **Firma como prueba de origen** no esté seleccionada.

     ![Plantilla, pestaña Extensiones](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **Seguridad**:  
     - Agregue la **Cuenta de servicio NDES**. Esta cuenta requiere los permisos **Lectura** e **Inscripción** para esta plantilla.

     - Agregue cuentas adicionales para los administradores de Intune que van a crear perfiles de SCEP. Estas cuentas requieren permisos de **Lectura** en la plantilla para que estos administradores puedan buscar esta plantilla mientras crean los perfiles SCEP.  

     ![Plantilla, pestaña Seguridad](./media/certificates-scep-configure/scep-ndes-security.jpg)  

   - **Administración de solicitudes**:  
      La imagen siguiente es un ejemplo. La configuración puede variar.  

     ![Plantilla, pestaña Administración de solicitudes](./media/certificates-scep-configure/scep-ndes-request-handling.png) 

   - **Requisitos de emisión**:  
     La imagen siguiente es un ejemplo. La configuración puede variar.  

     ![Plantilla, pestaña Requisitos de emisión](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)  

3. Guarde la plantilla de certificado.  

### <a name="create-the-client-certificate-template"></a>Creación de la plantilla de certificado de cliente

Intune Certificate Connector requiere un certificado con el uso mejorado de clave de *autenticación de cliente* y el nombre del firmante igual al FQDN del equipo en el que está instalado el conector. Se requiere una plantilla con las propiedades siguientes:

- **Extensiones** > **Directivas de aplicación** debe contener **Autenticación de cliente**
- **Nombre del firmante** > **Proporcionar en la solicitud**.

Si ya tiene una plantilla que incluye estas propiedades, puede volver a usarla; de lo contrario, cree una plantilla mediante la duplicación de una existente o la creación de una plantilla personalizada.

### <a name="create-the-server-certificate-template"></a>Creación de la plantilla de certificado de servidor

Las comunicaciones entre los dispositivos administrados e IIS en el servidor NDES usan HTTPS, que requiere el uso de un certificado. Puede usar la plantilla de certificado **Servidor web** para emitir este certificado. O bien, si prefiere tener una plantilla dedicada, las propiedades siguientes son obligatorias:

- **Extensiones** > **Directivas de aplicación** debe contener **Autenticación de servidor**
- **Nombre del firmante** > **Proporcionar en la solicitud**.

> [!NOTE]  
> Si tiene un certificado que cumple los dos requisitos de las plantillas de certificado de cliente y servidor, puede usar un solo certificado para IIS y para Intune Certificate Connector.

### <a name="grant-permissions-for-certificate-revocation"></a>Concesión de permisos para la revocación de certificados

Para que Intune pueda revocar los certificados que ya no son necesarios, debe conceder permisos en la entidad de certificación. 

En Intune Certificate Connector, puede usar la **cuenta de sistema** del servidor NDES o una cuenta específica como, por ejemplo, la **cuenta de servicio NDES**.

1. En la consola de la entidad de certificación, haga clic con el botón derecho en el nombre de la entidad de certificación y seleccione **Propiedades**.
2. En la pestaña **Seguridad**, haga clic en **Agregar**.
3. Conceda el permiso **Emitir y administrar certificados**:
   - Si opta por usar la **cuenta de sistema** del servidor NDES, proporcione los permisos al servidor NDES.
   - Si opta por usar la **cuenta de servicio NDES**, proporcione permisos para esa cuenta en su lugar.

### <a name="modify-the-validity-period-of-the-certificate-template"></a>Modificación del período de validez de la plantilla de certificado

La modificación del período de validez de la plantilla de certificado es opcional.  

Después de [crear la plantilla de certificado SCEP](#create-the-scep-certificate-template), puede editarla para revisar el **Período de validez** en la pestaña **General**.  

Intune usa de forma predeterminada el valor configurado en la plantilla. Pero puede configurar la entidad de certificación para permitir que el solicitante escriba otro valor, que se puede establecer desde la consola de Intune.  

> [!IMPORTANT]  
> Para iOS y macOS, use siempre un valor establecido en la plantilla.  

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>Para configurar un valor que se puede establecer desde la consola de Intune  
1. En la entidad de certificación, ejecute los comandos siguientes:  
   -**certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**  
   -**net stop certsvc**  
   -**net start certsvc**  

2. En la CA emisora, use el complemento Entidad de certificación para publicar la plantilla de certificado. Seleccione el nodo **Plantillas de certificado**, seleccione **Acción** > **Nueva** > **Plantilla de certificado que se va a emitir** y después la plantilla que ha creado en la sección anterior.  

3. Para comprobar que la plantilla se ha publicado, puede verla en la carpeta **Plantillas de certificado**.  

## <a name="set-up-ndes"></a>Configuración de NDES  
Los procedimientos siguientes pueden ayudarle a configurar el Servicio de inscripción de dispositivos de red (NDES) para usarlo con Intune. Para más información sobre NDES, vea [Orientación para el Servicio de inscripción de dispositivos de red](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11)).  

### <a name="install-the-ndes-service"></a>Instalación del servicio NDES  
1. En el servidor en el que se va a hospedar el servicio NDES, inicie sesión como **Administrador de la empresa** y, luego, use el [Asistente para agregar roles y características](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) para instalar NDES:

   1. En el asistente, seleccione **Servicios de certificados de Active Directory** para obtener acceso a los servicios de rol de AD CS. Seleccione **Servicio de inscripción de dispositivos de red**, desactive **Entidad de certificación** y complete el asistente.  

      > [!TIP]  
      > En **Progreso de la instalación**, no seleccione **Cerrar**. En su lugar, seleccione el vínculo **Configurar Servicios de certificados de Active Directory en el servidor de destino**. Se abre el asistente de **Configuración de AD CS**, que se usa para el siguiente procedimiento de este artículo, *Configuración del servicio NDES*. Una vez abierta la configuración de AD CS, puede cerrar al Asistente para agregar roles y características.  

   2. Cuando NDES se agrega al servidor, el asistente instala también IIS. Confirme que IIS tenga las configuraciones siguientes:  

      - **Servidor web** > **Seguridad** > **Filtrado de solicitudes**  
      - **Servidor web** > **Desarrollo de aplicaciones** > **ASP.NET 3.5**  

        Al instalar ASP.NET 3.5 se instala .NET Framework 3.5. Al instalar .NET Framework 3.5, se instala tanto la característica básica **.NET Framework 3.5** como la característica **Activación HTTP**.  
      - **Servidor web** > **Desarrollo de aplicaciones** > **ASP.NET 4.5**  

        Al instalar ASP.NET 4.5 se instala .NET Framework 4.5. Al instalar .NET Framework 4.5, se instalan la característica básica **.NET Framework 4.5**, la característica **ASP.NET 4.5** y la característica **Servicios WCF** > **Activación HTTP**.  

      - **Herramientas de administración** > **Compatibilidad con la administración de IIS 6** > **Compatibilidad con la metabase de IIS 6**  
      - **Herramientas de administración** > **Compatibilidad con la administración de IIS 6** > **Compatibilidad con WMI de IIS 6**  
      - En el servidor, agregue la cuenta de servicio NDES como miembro del grupo local **IIS_IUSR**.  

2. En el equipo en el que se hospeda el servicio NDES, ejecute el comando siguiente en un símbolo del sistema con privilegios elevados. El comando siguiente establece el SPN de la cuenta de servicio NDES:  

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`
   
   Por ejemplo, si el equipo en el que se hospeda el servicio NDES se denomina **Server01**, el dominio es **Contoso.com** y la cuenta de servicio es **NDESService**, use:  

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>Configuración del servicio NDES  

1. En el equipo en el que se hospeda el servicio NDES, abra el asistente para **Configuración de AD CS** y realice las actualizaciones siguientes:  

   > [!TIP]  
   > Si continúa desde el procedimiento anterior y ha hecho clic en el vínculo **Configurar Servicios de certificados de Active Directory en el servidor de destino**, este asistente ya debería estar abierto. De lo contrario, abra el Administrador del servidor para obtener acceso a la configuración posterior a la implementación de Servicios de certificados de Active Directory.  

   - En **Servicios de rol**, seleccione el **Servicio de inscripción de dispositivos de red**.
   - En **Cuenta de servicio para NDES**, especifique la cuenta de servicio NDES.
   - En **CA para NDES**, haga clic en **Seleccionar** y, después, seleccione la entidad de certificación emisora en la que ha configurado la plantilla de certificado.
   - En **Criptografía para NDES**, establezca la longitud de clave que satisfaga los requisitos de la empresa.
   - En **Confirmación**, seleccione **Configurar** para completar el asistente.

2. Una vez finalizado el asistente, actualice la siguiente clave del Registro en el equipo donde se hospeda el servicio NDES:  
   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`  

   Para actualizar esta clave, identifique el **Propósito** de la plantilla de certificado (se encuentra en su pestaña **Administración de solicitudes**). Después, actualice la entrada del Registro correspondiente mediante la sustitución de los datos existentes por el nombre de la plantilla de certificado (no el nombre para mostrar de la plantilla) que ha especificado al [crear la plantilla de certificado](#create-the-scep-certificate-template).  

   La tabla siguiente asigna el propósito de la plantilla de certificado a los valores del registro:
   
   |Plantilla de certificado Propósito (en la pestaña Tratamiento de la solicitud)|Valor del registro que se va a editar|Valor que se ve en la consola de administración de Intune para el perfil de SCEP|
   |------------------------|-------------------------|---|
   |Firma               |SignatureTemplate        |Firma digital |
   |Cifrado              |EncryptionTemplate       |Cifrado de clave  |
   |Firma y cifrado|GeneralPurposeTemplate   |Cifrado de clave<br/>Firma digital |  

   Por ejemplo, si el propósito de la plantilla de certificado es **Cifrado**, edite el valor **EncryptionTemplate** para que sea el nombre de la plantilla de certificado.  

3. Configure el filtrado de solicitudes de IIS para agregar compatibilidad en IIS para las direcciones URL largas (consultas) que recibe el servicio NDES.
   1. En el Administrador de IIS, seleccione **Sitio web predeterminado** > **Filtrado de solicitudes** > **Modificar configuración de característica** para abrir la página **Modificar configuración del filtrado de solicitudes**.  

   2. Configure las siguientes opciones:  
      - **Longitud máxima de dirección URL (bytes)** = 65534  
      - **Cadena de consulta máxima (bytes)** = 65534  
   3. Seleccione **Aceptar** para guardar esta configuración y cerrar el administrador de IIS.  
   4. Para validar esta configuración, puede ver la siguiente clave del Registro para confirmar que tiene los valores indicados:  

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`    

      Los valores siguientes se establecen como entradas DWORD:  
      - Nombre: **MaxFieldLength**, con un valor decimal de **65534**  
      - Nombre: **MaxRequestBytes**, con un valor decimal de **65534**  
4. Reinicie el servidor en el que se hospeda el servicio NDES. No use **iisreset**; iireset no completa los cambios necesarios.  

5. Vaya a *http://* FQDN_del_servidor */certsrv/mscep/mscep.dll*. Debería ver una página NDES similar a la de la imagen siguiente:  

   ![Probar SCEP](./media/certificates-scep-configure/scep-ndes-url.png)
  
   Si la dirección web devuelve **503 Servicio no disponible**, compruebe el visor de eventos de los equipos. Este error se suele producir cuando se detiene el grupo de aplicaciones debido a que falta el [permiso para la cuenta de servicio NDES](#accounts).  
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>Instalación y enlace de certificados en el servidor en el que se hospeda NDES  
> [!TIP]  
> En el procedimiento siguiente, puede usar un solo certificado para la *autenticación de servidor* y la *autenticación de cliente* cuando ese certificado está configurado para cumplir los criterios de ambos usos. Los criterios para cada uso se describen en los pasos 1 y 3 del procedimiento siguiente.  

1. Solicite un certificado de **autenticación de servidor** de la entidad de certificación interna o de una entidad de certificación pública, y después instálelo en el servidor.  

   Si el servidor usa un nombre externo e interno para una única dirección de red, el certificado de autenticación de servidor debe tener lo siguiente:  

   - Un **Nombre del firmante** con un nombre de servidor público externo.
   - Un **Nombre alternativo del firmante** que incluya el nombre del servidor interno.  

2. Enlace el certificado de autenticación de servidor en IIS:  
  
   1. Después de instalar el certificado de autenticación de servidor, abra el **Administrador de IIS** y seleccione el **Sitio web predeterminado**. En el panel **Acciones**, seleccione **Enlaces**.  
   1. Seleccione **Agregar**, configure **Tipo** como **https** y confirme que el puerto es **443**.  
   1. En el caso de **Certificado SSL**, especifique el certificado de autenticación de servidor.  
 
3. En el servidor NDES, solicite e instale un certificado de **autenticación del cliente** de la CA interna o de una entidad de certificación pública.  

   El certificado de autenticación del cliente debe tener las siguientes propiedades:  
   - **Uso mejorado de clave**: este valor debe incluir **Autenticación del cliente**.  
   - **Nombre del firmante**: el valor debe ser igual al nombre DNS del servidor donde se va a instalar el certificado (el servidor NDES).  

4. El servidor en el que se hospeda el servicio NDES ya está listo para admitir Intune Certificate Connector.  

## <a name="install-the-intune-certificate-connector"></a>Instalación de Intune Certificate Connector  
Microsoft Intune Certificate Connector se instala en el servidor en el que se ejecuta el servicio NDES. No se admite el uso de NDES o de Intune Certificate Connector en el mismo servidor que la entidad de certificación (CA) emisora.  

Para instalar Intune Certificate Connector:  
1. Inicie sesión en el [portal de Intune](https://aka.ms/intuneportal) con una cuenta que tenga derechos en Intune.  

2. Seleccione **Configuración de dispositivos** > **Entidad de certificación** > **Agregar**.  

3. Descargue y guarde el conector para el archivo SCEP. Guárdelo en una ubicación accesible desde el servidor donde va a instalar el conector.

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)

4. Una vez finalizada la descarga, vaya al servidor que hospeda el rol Servicio de inscripción de dispositivos de red (NDES). Después:  

   1. Confirme que .NET Framework 4.5 esté instalado, como requiere Intune Certificate Connector. .NET Framework 4.5 se incluye de forma automática con Windows Server 2012 R2 y versiones más recientes.  
   2. Ejecute el instalador (**NDESConnectorSetup.exe**). El instalador también instala el módulo de directivas para NDES y el servicio web Punto de Registro de certificado (CRP) de IIS. El servicio web CRP *CertificateRegistrationSvc*, se ejecuta como una aplicación en IIS.  

      - Cuando instala NDES para Intune independiente, el servicio de CRP se instala automáticamente con Certificate Connector. 
      - Al usar Intune con Configuration Manager, se instala el Punto de Registro de certificado como un rol de sistema de sitio de Configuration Manager.  
5. Cuando se le solicite el certificado de cliente para Certificate Connector, elija **Seleccionar** y seleccione el certificado de **autenticación del cliente** que ha instalado en el servidor NDES durante el paso 3 del procedimiento [Instalación y enlace de certificados en el servidor en el que se hospeda NDES](#install-and-bind-certificates-on-the-server-that-hosts-ndes) anteriormente en este artículo.  

   Después de seleccionar el certificado de autenticación del cliente, volverá a la superficie del **Certificado de cliente para Microsoft Intune Certificate Connector**. Aunque no se muestra el certificado seleccionado, seleccione **Siguiente** para ver las propiedades de ese certificado. Seleccione **Siguiente** y luego **Instalar**.

6. Cuando se complete el asistente, pero antes de cerrarlo, haga clic en **Iniciar la UI del conector de certificado**.  

   Si cierra al asistente antes de iniciar la interfaz de usuario de Certificate Connector, puede volver a abrirlo si ejecuta el comando siguiente: *<ruta_de_instalación>\NDESConnectorUI\NDESConnectorUI.exe*

7. En la IU **Conector de certificado** :  
   1. Seleccione **Iniciar sesión** y escriba sus credenciales de administrador de servicio de Intune o las credenciales de un administrador de inquilinos con permiso de administración global.  
   2. La cuenta que use debe tener asignada una licencia válida de Intune.  
   3. Después de iniciar sesión, Intune Certificate Connector descarga un certificado de Intune. Este certificado sirve para la autenticación entre el conector e Intune. Si la cuenta que ha usado no tiene una licencia de Intune, el conector (NDESConnectorUI.exe) no podrá obtener el certificado de Intune.  

      Si su organización usa un servidor proxy y el proxy es necesario para que el servidor NDES acceda a Internet, seleccione **Usar servidor proxy**. A continuación, escriba el nombre del servidor proxy, el puerto y las credenciales de cuenta para conectarse.  

    4. Seleccione la pestaña **Avanzadas** y especifique las credenciales de una cuenta que tenga el permiso **Emitir y administrar certificados** en la entidad de certificación emisora. **Aplique** los cambios.  

    5. Ahora puede cerrar la IU del conector de certificado.  

8. Abra un símbolo del sistema, escriba **services.msc** y presione **Entrar**. Haga clic con el botón derecho en **Servicio del conector de Intune** >  y en **Reiniciar**.


Para validar que el servicio se ejecuta, abra un explorador y escriba la siguiente dirección URL. Debe devolver un error **403**: `https://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`  

> [!NOTE]  
> Intune Certificate Connector admite TLS 1.2. Si el servidor en el que se hospeda el conector admite TLS 1.2, se usa TLS 1.2. Si el servidor no admite TLS 1.2, entonces se usará TLS 1.1. Actualmente, se usa TLS 1.1 para la autenticación entre los dispositivos y el servidor.

## <a name="next-steps"></a>Pasos siguientes

[Creación de un perfil de certificado SCEP](certificates-profile-scep.md)  
[Solución de problemas de Intune Certificate Connector](troubleshoot-certificate-connector-events.md)
