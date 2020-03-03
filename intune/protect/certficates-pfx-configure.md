---
title: Uso de certificados de claves públicas y privadas en Microsoft Intune (Azure) | Microsoft Docs
description: Use los certificados de estándares de criptografía de clave pública (PKCS) con Microsoft Intune, trabaje con certificados raíz y plantillas de certificado, instale Intune Certificate Connector (NDES) y use perfiles de configuración de dispositivo para un certificado PKCS.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/25/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99983b2d2776e72232c65fcfb12d8075061d804b
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609347"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configuración y uso de certificados PKCS con Intune

Intune admite el uso de certificados de par de claves privadas y públicas (PKCS). Este artículo le será útil para configurar la infraestructura necesaria, como conectores de certificados locales, exportar un certificado PKCS y luego agregarlo a un perfil de configuración de dispositivo de Intune.

Microsoft Intune incluye opciones de configuración integradas para usar certificados PKCS para los procesos de acceso y autenticación de los recursos de la organización. Los certificados permiten autenticar y proteger el acceso a los recursos corporativos, como por ejemplo, una VPN o una red Wi-Fi. Para implementar esta configuración en los dispositivos, se usan perfiles de configuración de dispositivo de Intune.

Para más información sobre el uso de certificados PKCS, consulte [Certificados PFX importados](certificates-imported-pfx-configure.md).


## <a name="requirements"></a>Requisitos

Para usar certificados PKCS con Intune, debe contar con esta infraestructura:

- **Dominio de Active Directory**:  
  todos los servidores mencionados en esta sección deben estar unidos al dominio de Active Directory.

  Para más información sobre cómo instalar y configurar Active Directory Domain Services (AD DS), vea [Planeación y diseño de AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Entidad de certificación**:  
   entidad de certificación empresarial (CA).

  Para más información sobre cómo instalar y configurar los Servicios de certificados de Active Directory (AD CS), vea [Active Directory Certificate Services Step-by-Step Guide](https://technet.microsoft.com/library/cc772393) (Guía detallada de los Servicios de certificados de Active Directory).

  > [!WARNING]  
  > Intune requiere ejecutar AD CS con una entidad de certificación (CA) empresarial, no una CA independiente.

- **Cliente**:  
  se usa para conectarse a la CA empresarial.

- **Certificado raíz**:  
  Una copia exportada del certificado raíz desde la CA empresarial.

- **Microsoft Intune Certificate Connector** (también denominado *Certificate Connector NDES*):  
  En el portal de Intune, vaya a **Configuración del dispositivo** > **Conectores de certificados** > **Agregar** y siga los *Pasos de instalación del conector para PKCS #12*. Use el vínculo de descarga del portal para empezar la descarga del instalador del conector de certificado **NDESConnectorSetup.exe**.  

  Intune admite hasta 100 instancias de este conector por inquilino. Cada instancia del conector debe estar en un servidor de Windows independiente. Puede instalar una instancia de este conector en el mismo servidor que una instancia Certificate Connector PFX para Microsoft Intune. Cuando se usan varios conectores, la infraestructura del conector admite alta disponibilidad y equilibrio de carga, ya que cualquier instancia del conector disponible puede procesar las solicitudes de certificado PKCS. 

  Este conector procesa las solicitudes de certificado PKCS que se usan para la autenticación o la firma de correo electrónico S/MIME.

  Microsoft Intune Certificate Connector también admite el modo Estándar federal de procesamiento de información (FIPS). FIPS no es necesario, pero puede emitir y revocar certificados cuando está habilitado.

- **Conector de certificado PFX para Microsoft Intune**:  
  Si tiene previsto usar el cifrado de correo electrónico S/MIME, use el portal de Intune para descargar el *Conector de certificado PFX* que admite la importación de certificados PFX.  Vaya a **Configuración del dispositivo** > **Conectores de certificados** > **Agregar** y siga los *Pasos para instalar el conector para certificados PFX importados*. Use el vínculo de descarga del portal para empezar la descarga del instalador **PfxCertificateConnectorBootstrapper.exe**.

  Cada inquilino de Intune admite una única instancia de este conector. Puede instalar este conector en el mismo servidor que una instancia de Microsoft Intune Certificate Connector.

  El conector controla las solicitudes de archivos PFX importados en Intune para el cifrado de correo electrónico S/MIME para un usuario específico.  

  Este conector pueda actualizarse automáticamente cuando estén disponibles nuevas versiones. Para usar la función de actualización, debe:
  - Instalar el Conector de certificado PFX para Microsoft Intune en el servidor.  
  - Para recibir automáticamente actualizaciones importantes, asegúrese de que los firewalls están abiertos para permitir que el conector se ponga en contacto con **autoupdate.msappproxy.net** en el puerto **443**.   

  Para más información, vea [Puntos de conexión de red de Microsoft Intune](../fundamentals/intune-endpoints.md) y [Ancho de banda y requisitos de configuración de red de Intune](../fundamentals/network-bandwidth-use.md).

- **Windows Server**:  
  Use una instancia de Windows Server para hospedar:

  - Microsoft Intune Certificate Connector para casos de autenticación y firma de correo electrónico S/MIME.
  - Conector de certificado PFX para Microsoft Intune para casos de cifrado de correo electrónico S/MIME.

  Los conectores requieren acceso a los mismos puertos que se detallan para los dispositivos administrados, como se indica en nuestro [contenido sobre los puntos de conexión de los dispositivos](https://docs.microsoft.com/intune/fundamentals/intune-endpoints#access-for-managed-devices).

  Intune admite la instalación del *Conector de certificado PFX* en el mismo servidor que *Microsoft Intune Certificate Connector*.
  
## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportación del certificado raíz desde la CA empresarial

Para autenticar un dispositivo con VPN, Wi-Fi u otros recursos, el dispositivo necesita un certificado de entidad de certificación intermedio. Los pasos siguientes explican cómo obtener el certificado requerido desde la CA empresarial.

**Usar una línea de comandos**:  
1. inicie sesión en el servidor de la entidad de certificación raíz con la cuenta de administrador.
 
2. Vaya a **Inicio** > **Ejecutar** y, después, escriba **Cmd** para abrir el símbolo del sistema. 
    
3. Especifique **certutil -ca.cert ca_name.cer** para exportar el certificado raíz como un archivo denominado *ca_name.cer*.



## <a name="configure-certificate-templates-on-the-ca"></a>Configuración de plantillas de certificado en la CA

1. Inicie sesión en la entidad de certificación empresarial con una cuenta que tenga privilegios de administración.
2. En la consola de la **entidad de certificación**, haga clic con el botón derecho en **Plantillas de certificado** y seleccione **Administrar**.
3. Busque la plantilla de certificado **Usuario**, haga clic con el botón derecho en ella y elija **Duplicar plantilla** para abrir **Propiedades de plantilla nueva**.

    > [!NOTE]
    > Para casos de cifrado y firma de correo electrónico S/MIME, muchos administradores usan certificados independientes para la firma y el cifrado. Si va a usar Servicios de certificados de Active Directory de Microsoft, puede usar la plantilla **Solo la firma de Exchange** para los certificados de firma de correo electrónico S/MIME y la plantilla **Usuario de Exchange** para los certificados de cifrado S/MIME.  Si va a usar una entidad de certificación de terceros, le recomendamos que revise las instrucciones para configurar las plantillas de firma y cifrado.

4. En la pestaña **Compatibilidad**:

    - Establezca **Entidad de certificación** en **Windows Server 2008 R2**
    - Establezca **Destinatario del certificado** en **Windows 7 / Server 2008 R2**

5. En la pestaña **General**, establezca el **nombre para mostrar de la plantilla** en un nombre significativo para usted.

    > [!WARNING]
    > El **nombre de la plantilla** predeterminado es el mismo que el **nombre para mostrar de la plantilla** *sin espacios*. Apunte el nombre de la plantilla, lo necesitará más adelante.

6. En **Tratamiento de la solicitud**, seleccione **Permitir que la clave privada se pueda exportar**.
7. En **Criptografía**, confirme que el **Tamaño mínimo de clave** esté establecido en 2048.
8. En **Nombre del firmante**, elija **Proporcionado por el solicitante**.
9. En **Extensiones**, confirme que ve Sistema de cifrado de archivos, Correo seguro y Autenticación de cliente en las **Directivas de aplicación**.

    > [!IMPORTANT]
    > En el caso de plantillas de certificado de iOS/iPadOS, vaya a la pestaña **Extensiones**, actualice **Uso de la clave** y confirme que no está seleccionada la opción **Firma como prueba de origen**.

10. En **Seguridad**, agregue la cuenta de equipo para el servidor donde instala Microsoft Intune Certificate Connector. Permita que esta cuenta tenga los permisos **Lectura** e **Inscripción**.
11. Seleccione **Aplicar** > **Aceptar** para guardar la plantilla de certificado. Cierre la **consola Plantillas de certificado**.
12. En la consola de la **entidad de certificación**, haga clic con el botón derecho en **Plantillas de certificado** > **Nuevo** > **Plantilla de certificado que se va a emitir**. Elija la plantilla que ha creado en los pasos anteriores. Seleccione **Aceptar**.
13. Para que el servidor administre los certificados de los dispositivos inscritos en Intune, siga estos pasos:

    1. Haga clic con el botón secundario en la entidad de certificación y elija **Propiedades**.
    2. En la pestaña Seguridad, agregue la cuenta de equipo del servidor donde se ejecutan los conectores (**Microsoft Intune Certificate Connector** o **Conector de certificado PFX para Microsoft Intune**). 
    3. Conceda los permisos **Emitir y administrar certificados** y **Solicitar certificados** a la cuenta de equipo.

14. Cierre la sesión de la entidad de certificación empresarial.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Descarga, instalación y configuración de Microsoft Intune Certificate Connector

> [!IMPORTANT]  
> Microsoft Intune Certificate Connector no puede instalarse en la entidad emisora de certificados (CA) y debe instalarse en una instancia independiente de Windows Server.  

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Administración de inquilinos** > **Conectores y tokens** > **Conectores de certificados** > **+ Agregar**.

3. Haga clic en *Descargar el software de Certificate Connector* para el conector de PKCS #12 y guarde el archivo en una ubicación a la que pueda acceder desde el servidor en el que va a instalar el conector.

   ![Descarga de Microsoft Intune Certificate Connector](./media/certficates-pfx-configure/download-ndes-connector.png)
 
4. Una vez finalizada la descarga, inicie sesión en el servidor. Después:

    1. Asegúrese de que .NET Framework 4.5 o una versión posterior esté instalado, tal como requiere el conector de certificado NDES. .NET Framework 4.5 se incluye automáticamente con Windows Server 2012 R2 y las versiones más recientes.
    2. Ejecute el instalador (NDESConnectorSetup.exe) y acepte la ubicación predeterminada. Se instala el conector en `\Program Files\Microsoft Intune\NDESConnectorUI`. En Opciones del instalador, seleccione **Distribución PFX**. Continúe y complete la instalación.
    3. De manera predeterminada, el servicio de conector inicia sesión con la cuenta de sistema local. Si se requiere un servidor proxy para el acceso a Internet, confirme que la cuenta de servicio local puede acceder a la configuración de proxy en el servidor.

5. Microsoft Intune Certificate Connector abre la pestaña **Inscripción**. Para habilitar la conexión con Intune, **inicie sesión** y escriba una cuenta con permisos administrativos globales.
6. En la pestaña **Avanzadas**, se recomienda dejar seleccionado **Usar la cuenta SYSTEM de este equipo (predeterminado)**.
7. **Aplicar** > **Cerrar**
8. Vuelva al portal de Intune [**Intune** > **Configuración del dispositivo** > **Certification Connectors** (Conectores de certificación)]. Tras unos minutos, se mostrará una marca de verificación verde y el **Estado de la conexión** figurará como **Activo**. Ahora, el servidor del conector puede comunicarse con Intune.
9. Si tiene un proxy web en el entorno de red, es posible que necesite configuraciones adicionales para que el conector funcione. Para obtener más información, consulte [Trabajo con servidores proxy locales existentes](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) en la documentación de Azure Active Directory.
<ul><li>Android Enterprise (*perfil de trabajo*)</li><li>iOS</li><li>macOS</li><li>Windows 10 y versiones posteriores > Microsoft Intune Certificate Connector admite TLS 1.2. Si TLS 1.2 está instalado en el servidor que hospeda el conector, el conector usará TLS 1.2. En caso contrario, se usa TLS 1.1. Actualmente, se usa TLS 1.1 para la autenticación entre los dispositivos y el servidor.

## <a name="create-a-trusted-certificate-profile"></a>Creación de un perfil de certificado de confianza

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

   ![Navegación a Intune y creación de un perfil para un certificado de confianza](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. Escriba las propiedades siguientes:

    - **Nombre** del perfil
    - Si lo desea, establezca una descripción
    - **Plataforma** en la cual implementar el perfil
    - Establezca el **tipo del perfil** en **Certificado de confianza**

4. Seleccione **Configuración** y especifique el certificado de entidad de certificación raíz del archivo .cer que ha exportado anteriormente.

   > [!NOTE]
   > En función de la plataforma que haya elegido en el **paso 2**, es posible que tenga o no la opción de seleccionar el **Almacén de destino** del certificado.

   ![Crear un perfil y cargar un certificado de confianza](./media/certficates-pfx-configure/certificates-pfx-configure-profile-fill.png)

5. Seleccione **Aceptar** > **Crear** para guardar el perfil.

6. Para asignar el perfil nuevo a uno o varios dispositivos, consulte [Asignación de perfiles de dispositivo en Microsoft Intune](../configuration/device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Creación de un perfil de certificado PKCS

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione y vaya a **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

3. Escriba las propiedades siguientes:

    - **Nombre** del perfil
    - Si lo desea, establezca una descripción
    - **Plataforma** en la cual implementar el perfil
    - Establezca **Tipo del perfil** en **Certificado PKCS**

4. Vaya a **Configuración** y configure las propiedades que se aplican a la plataforma seleccionada:
   
   |Setting     | Plataforma     | Detalles   |
   |------------|------------|------------|
   |**Umbral de renovación (%)**        |<ul><li>Todos         |El valor recomendado es del 20 %.  | 
   |**Período de validez del certificado**  |<ul><li>Todos         |si no ha cambiado la plantilla de certificado, esta opción puede estar establecida en un año. |
   |**Proveedor de almacenamiento de claves (KSP)**   |<ul><li>Windows 10  |en el caso de Windows, seleccione la ubicación del dispositivo en la que quiera almacenar las claves. |
   |**Entidad de certificación**      |<ul><li>Todos         |muestra el nombre de dominio completo (FQDN) interno de la CA empresarial.  |
   |**Nombre de la entidad de certificación** |<ul><li>Todos         |muestra el nombre de la CA empresarial, por ejemplo "Contoso Certification Authority". |
   |**Nombre de plantilla de certificado**    |<ul><li>Todos         |Enumera el nombre de la plantilla de certificado. |
   |**Tipo de certificado**             |<ul><li>Android Enterprise (*perfil de trabajo*)</li><li>iOS</li><li>macOS</li><li>Windows 10 y versiones posteriores|Seleccione un tipo: <ul><li> los certificados **Usuario** pueden contener atributos de usuario y dispositivo en el asunto y SAN del certificado. </il><li>Los certificados **Dispositivo** solo pueden contener atributos de dispositivo en el asunto y SAN del certificado. Use Dispositivo en escenarios como, por ejemplo, dispositivos sin usuario (como los quioscos multimedia) u otros dispositivos compartidos.  <br><br> Esta selección afecta al formato de nombre del firmante. |
   |**Formato de nombre del firmante**          |<ul><li>Todos         |Para obtener más información sobre cómo configurar el formato de nombre del sujeto, vea [Formato de nombre del sujeto](#subject-name-format) más adelante en este artículo.  <br><br> En la mayoría de las plataformas, use la opción **Nombre común**, a menos que se precise otra. <br><br>En las plataformas siguientes, el formato de nombre del firmante viene determinado por el tipo de certificado: <ul><li>Android Enterprise (*Perfil de trabajo*)</li><li>iOS</li><li>macOS</li><li>Windows 10 y versiones posteriores</li></ul>  <p>  |
   |**Nombre alternativo del firmante**     |<ul><li>Todos         |En *Atributo*, seleccione **Nombre principal de usuario (UPN)**, a menos que se precise otra cosa, configure un *Valor* correspondiente y, después, haga clic en **Agregar**. <br><br>Para obtener más información, vea [Formato de nombre del sujeto](#subject-name-format) más adelante en este artículo.|
   |**Uso mejorado de clave**           |<ul><li> Administrador de dispositivos Android </li><li>Android Enterprise (*Propietario del dispositivo*, *Perfil de trabajo*) </li><li>Windows 10 |Los certificados suelen requerir *Autenticación de cliente* para que el usuario o dispositivo pueda autenticarse en un servidor. |
   |**Permitir el acceso de todas las aplicaciones a la clave privada** |<ul><li>macOS  |Establezca esta opción en **Habilitar** para dar acceso a la clave privada de certificados PKCS a aquellas aplicaciones que estén configuradas para el dispositivo Mac asociado. <br><br> Para más información sobre esta configuración, vea *AllowAllAppsAccess* de la sección de carga de certificado de la [referencia de perfiles de configuración](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf) en la documentación para desarrolladores de Apple. |
   |**Certificado raíz**             |<ul><li>Administrador de dispositivos Android </li><li>Android Enterprise (*Propietario del dispositivo*, *Perfil de trabajo*) |Seleccione un perfil de certificado de CA raíz asignado previamente. |

5. Seleccione **Aceptar** > **Crear** para guardar el perfil.

6. Para asignar el perfil nuevo a uno o varios dispositivos, consulte [Asignación de perfiles de dispositivo en Microsoft Intune](../configuration/device-profile-assign.md).

   > [!NOTE]
   > En los dispositivos con un perfil de Android Enterprise, los certificados que se instalan con un perfil de certificado PKCS no son visibles en el dispositivo. Para confirmar la correcta implementación de certificados, compruebe el estado del perfil en la consola de Intune.

### <a name="subject-name-format"></a>Formato de nombre del sujeto

Al crear un perfil de certificado PKCS para las plataformas siguientes, las opciones de formato de nombre del firmante dependen del tipo de certificado que seleccione: **Usuario** o **Dispositivo**.  

Plataformas:

- Android Enterprise (*Perfil de trabajo*)
- iOS
- macOS
- Windows 10 y versiones posteriores

> [!NOTE]
> Existe un problema conocido en el uso de SCEP para obtener certificados [similar al problema que se produce con SCEP](certificates-profile-scep.md#avoid-certificate-signing-requests-with-escaped-special-characters), cuando el nombre del firmante en la solicitud de firma de certificado (CSR) resultante incluye uno de los siguientes caracteres como carácter de escape (precedido por una barra diagonal inversa \\):
> - \+
> - ;
> - ,
> - =

- **Tipo de certificado de usuario**  
  Las opciones de formato de *Formato de nombre del firmante* incluyen dos variables: **Nombre común (CN)** y **dirección de correo electrónico (E)**. **Nombre común (CN)** se puede establecer en cualquiera de las siguientes variables:

  - **CN={{UserName}}**: nombre principal de usuario, como janedoe@contoso.com.
  - **CN={{AAD_Device_ID}}**: identificador asignado al registrar un dispositivo en Azure Active Directory (AD). Este identificador normalmente se usa para autenticarse en Azure AD.
  - **CN={{SERIALNUMBER}}**: número de serie (SN) único que normalmente usa el fabricante para identificar un dispositivo.
  - **CN={{IMEINumber}}**: número exclusivo de identidad de equipo móvil internacional (IMEI) usado para identificar un teléfono móvil.
  - **CN={{OnPrem_Distinguished_Name}}**: Secuencia de nombres distintivos relativos separados por comas, como *CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com*.

    Para usar la variable *{{OnPrem_Distinguished_Name}}*, asegúrese de sincronizar el atributo de usuario *onpremisesdistinguishedname* mediante [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con la instancia de Azure AD.

  - **CN={{onPremisesSamAccountName}}**: los administradores pueden sincronizar el atributo samAccountName de Active Directory con Azure AD mediante Azure AD Connect en un atributo llamado *onPremisesSamAccountName*. Intune puede sustituir esa variable como parte de una solicitud de emisión de certificado en el asunto de un certificado. El atributo samAccountName es el nombre de inicio de sesión del usuario que se utiliza para admitir clientes y servidores de una versión anterior de Windows (anterior a Windows 2000). El formato de nombre de inicio de sesión de usuario es el siguiente: *NombreDeDominio\usuario de prueba*, o bien solo *usuario de prueba*.

    Para usar la variable *{{onPremisesSamAccountName}}*, asegúrese de sincronizar el atributo de usuario *onPremisesSamAccountName* mediante [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con la instancia de Azure AD.

  Mediante una combinación de una o muchas de estas variables y cadenas estáticas, puede crear un formato de nombre de firmante personalizado como este:  
  - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**
  
  Ese ejemplo incluye un formato de nombre de firmante en el que se usan las variables CN y E, y cadenas para los valores Unidad organizativa, Organización, Ubicación, Estado y País. [CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) describe esta función y sus cadenas admitidas.

- **Tipo de certificado de dispositivo**  
  Las opciones de formato para el formato de nombre del firmante incluyen las variables siguientes: 
  - **{{AAD_Device_ID}}**
  - **{{Device_Serial}}**
  - **{{Device_IMEI}}**
  - **{{SerialNumber}}**
  - **{{IMEINumber}}**
  - **{{AzureADDeviceId}}**
  - **{{WiFiMacAddress}}**
  - **{{IMEI}}**
  - **{{DeviceName}}**
  - **{{FullyQualifiedDomainName}}** *(Solo aplicable para dispositivos Windows y unidos a dominio)*
  - **{{MEID}}**

  Puede especificar estas variables, seguidas del texto de la variable, en el cuadro de texto. Por ejemplo, el nombre común de un dispositivo denominado *Dispositivo1* se puede agregar como **CN={{DeviceName}}Dispositivo1**.

  > [!IMPORTANT]  
  > - Al especificar una variable, incluya el nombre de la variable entre corchetes { } como se muestra en el ejemplo, para evitar un error.  
  > - Una persona con acceso al dispositivo podría suplantar las propiedades del dispositivo que se usan en el *asunto* o *SAN*, como **IMEI**, **SerialNumber** y **FullyQualifiedDomainName**.
  > - Un dispositivo debe admitir todas las variables especificadas en un perfil de certificado para que ese perfil se instale en ese dispositivo.  Por ejemplo, si se usa **{{IMEI}}** en el nombre del firmante de un perfil SCEP y se asigna a un dispositivo que no tiene un número IMEI, se producirá un error en la instalación del perfil.  
 
## <a name="whats-new-for-connectors"></a>Novedades para los conectores

Se publican actualizaciones para los dos conectores de certificados con regularidad. Cuando actualizamos un conector, informamos aquí sobre los cambios realizados.

El *conector de certificados PFX para Microsoft Intune* [admite actualizaciones automáticas](#requirements), mientras que *Intune Certificate Connector* se actualiza de forma manual.

### <a name="may-17-2019"></a>17 de mayo de 2019

- **Conector de certificados PFX para Microsoft Intune: versión 6.1905.0.404**  
  Cambios de esta versión:  
  - Se ha corregido un problema por el que los certificados PFX existentes se siguen procesando, lo que provoca que el conector deje de procesar solicitudes nuevas. 

### <a name="may-6-2019"></a>6 de mayo de 2019

- **Conector de certificados PFX para Microsoft Intune: versión 6.1905.0.402**  
  Cambios de esta versión:  
  - El intervalo de sondeo para el conector se ha reducido de 5 minutos a 30 segundos.

### <a name="april-2-2019"></a>2 de abril de 2019

- **Intune Certificate Connector: versión 6.1904.1.0**  
  Cambios de esta versión:  
  - Se ha corregido un problema que podría producir que el conector no se inscriba en Intune después de iniciar sesión en el conector con una cuenta de administrador global.  
  - Incluye correcciones de fiabilidad para la revocación de certificados.  
  - Incluye correcciones de rendimiento para aumentar la rapidez con la que se procesan las solicitudes de certificado PKCS.  

- **Conector de certificados PFX para Microsoft Intune: versión 6.1904.0.401**
  > [!NOTE]  
  > La actualización automática para esta versión del conector PFX no está disponible hasta el 11 de abril de 2019.  

  Cambios de esta versión:  
  - Se ha corregido un problema que podría producir que el conector no se inscriba en Intune después de iniciar sesión en el conector con una cuenta de administrador global.  


## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](../configuration/device-profile-assign.md) y [supervise el estado](../configuration/device-profile-monitor.md).

[Use SCEP para los certificados](certificates-scep-configure.md), o bien [emita certificados PKCS a partir de un servicio web de administración de PKI de Symantec](certificates-digicert-configure.md).
