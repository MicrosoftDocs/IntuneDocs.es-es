---
title: Uso de certificados de claves públicas y privadas en Microsoft Intune (Azure) | Microsoft Docs
description: Agregue o cree certificados de Public Key Cryptography Standards (PKCS) con Microsoft Intune, incluidos los pasos para exportar un certificado raíz, configurar la plantilla de certificado, descargar e instalar Intune Certificate Connector (NDES), crear un perfil de configuración de dispositivo y crear un perfil de certificado PKCS en Azure y la entidad de certificación.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ee5ef1b5c59bbef3834d44354508b767ae99088
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722935"
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

  Intune admite hasta cien instancias de este conector por inquilino, con cada una de ellas en un servidor Windows independiente. Puede instalar una instancia de este conector en el mismo servidor que una instancia Certificate Connector PFX para Microsoft Intune. Cuando se usan varios conectores, la infraestructura del conector admite alta disponibilidad y equilibrio de carga, ya que cualquier instancia del conector disponible puede procesar las solicitudes de certificado PKCS. 

  Este conector procesa las solicitudes de certificado PKCS que se usan para la autenticación o la firma de correo electrónico S/MIME.

  Microsoft Intune Certificate Connector también admite el modo Estándar federal de procesamiento de información (FIPS). FIPS no es necesario, pero puede emitir y revocar certificados cuando está habilitado.

- **Conector de certificado PFX para Microsoft Intune**:  
  Si tiene previsto usar el cifrado de correo electrónico S/MIME, use el portal de Intune para descargar el *Conector de certificado PFX* que admite la importación de certificados PFX.  Vaya a **Configuración del dispositivo** > **Conectores de certificados** > **Agregar** y siga los *Pasos para instalar el conector para certificados PFX importados*. Use el vínculo de descarga del portal para empezar la descarga del instalador **PfxCertificateConnectorBootstrapper.exe**. 

  Cada inquilino de Intune admite una única instancia de este conector. Puede instalar este conector en el mismo servidor que una instancia de Microsoft Intune Certificate Connector.

  El conector controla las solicitudes de archivos PFX importados en Intune para el cifrado de correo electrónico S/MIME para un usuario específico.  

  Este conector pueda actualizarse automáticamente cuando estén disponibles nuevas versiones. Para usar la función de actualización, debe:
  - Instalar el Conector de certificado PFX para Microsoft Intune en el servidor.  
  - Para recibir automáticamente actualizaciones importantes, asegúrese de que los firewalls están abiertos para permitir que el conector se ponga en contacto con **autoupdate.msappproxy.net** en el puerto **443**.   

  Para más información sobre los puntos de conexión de red a los que el conector debe poder obtener acceso, consulte [Puntos de conexión de red de Microsoft Intune](../fundamentals/intune-endpoints.md).

- **Windows Server**:  
  se usa Windows Server para hospedar:

  - Microsoft Intune Certificate Connector para casos de autenticación y firma de correo electrónico S/MIME.
  - Conector de certificado PFX para Microsoft Intune para casos de cifrado de correo electrónico S/MIME.

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
3. Busque la plantilla de certificado **Usuario**, haga clic con el botón derecho en ella y elija **Duplicar plantilla**. Se abre **Propiedades de plantilla nueva**.

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
    > En el caso de plantillas de certificado de iOS, vaya a la pestaña **Extensiones**, actualice **Uso de la clave** y confirme que no está seleccionada la opción **Firma como prueba de origen**.

10. En **Seguridad**, agregue la cuenta de equipo para el servidor donde instala Microsoft Intune Certificate Connector. Permita que esta cuenta tenga los permisos **Lectura** e **Inscripción**.
11. Seleccione **Aplicar** > **Aceptar** para guardar la plantilla de certificado. Cierre la **Consola de plantillas de certificado**.
12. En la consola de la **entidad de certificación**, haga clic con el botón derecho en **Plantillas de certificado** > **Nuevo** > **Plantilla de certificado que se va a emitir**. Elija la plantilla que ha creado en los pasos anteriores. Seleccione **Aceptar**.
13. Para que el servidor administre los certificados de los dispositivos inscritos en Intune, siga estos pasos:

    1. Haga clic con el botón secundario en la entidad de certificación y elija **Propiedades**.
    2. En la pestaña Seguridad, agregue la cuenta de equipo del servidor donde se ejecutan los conectores (**Microsoft Intune Certificate Connector** o **Conector de certificado PFX para Microsoft Intune**). 
    3. Conceda los permisos **Emitir y administrar certificados** y **Solicitar certificados** a la cuenta de equipo.

14. Cierre la sesión de la entidad de certificación empresarial.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Descarga, instalación y configuración de Microsoft Intune Certificate Connector

> [!IMPORTANT]  
> Microsoft Intune Certificate Connector no puede instalarse en la entidad emisora de certificados (CA) y debe instalarse en una instancia independiente de Windows Server.  

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Configuración del dispositivo** > **Conectores de certificación** > **Agregar**.
3. Descargue el archivo del conector y guárdelo en una ubicación a la que pueda acceder desde el servidor donde vaya a instalar el conector.

    ![Descarga de Microsoft Intune Certificate Connector](./media/certficates-pfx-configure/download-ndes-connector.png)
 

4. Una vez finalizada la descarga, inicie sesión en el servidor. Después:

    1. Asegúrese de que .NET Framework 4.5 o una versión posterior esté instalado, tal como requiere el conector de certificado NDES. .NET Framework 4.5 se incluye automáticamente con Windows Server 2012 R2 y las versiones más recientes.
    2. Ejecute el instalador (NDESConnectorSetup.exe) y acepte la ubicación predeterminada. Se instala el conector en `\Program Files\Microsoft Intune\NDESConnectorUI`. En Opciones del instalador, seleccione **Distribución PFX**. Continúe y complete la instalación.
    3. De manera predeterminada, el servicio de conector inicia sesión con la cuenta de sistema local. Si se requiere un servidor proxy para el acceso a Internet, confirme que la cuenta de servicio local puede acceder a la configuración de proxy en el servidor.

5. Microsoft Intune Certificate Connector abre la pestaña **Inscripción**. Para habilitar la conexión con Intune, **inicie sesión** y escriba una cuenta con permisos administrativos globales.
6. En la pestaña **Avanzadas**, se recomienda dejar seleccionado **Usar la cuenta SYSTEM de este equipo (predeterminado)** .
7. **Aplicar** > **Cerrar**
8. Vuelva al portal de Intune [**Intune** > **Configuración del dispositivo** > **Certification Connectors** (Conectores de certificación)]. Tras unos minutos, se mostrará una marca de verificación verde y el **Estado de la conexión** figurará como **Activo**. Ahora, el servidor del conector puede comunicarse con Intune.
9. Si tiene un proxy web en el entorno de red, es posible que necesite configuraciones adicionales para que el conector funcione. Para obtener más información, consulte [Trabajo con servidores proxy locales existentes](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) en la documentación de Azure Active Directory.

> [!NOTE]  
> Microsoft Intune Certificate Connector admite TLS 1.2. Si TLS 1.2 está instalado en el servidor que hospeda el conector, el conector usará TLS 1.2. En caso contrario, se usa TLS 1.1. Actualmente, se usa TLS 1.1 para la autenticación entre los dispositivos y el servidor.

## <a name="create-a-trusted-certificate-profile"></a>Creación de un perfil de certificado de confianza

1. En [Azure Portal](https://portal.azure.com), vaya a **Intune** > **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
    ![Navegar a Intune y crear un perfil nuevo de un certificado de confianza](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

2. Escriba las propiedades siguientes:

    - **Nombre** del perfil
    - Si lo desea, establezca una descripción
    - **Plataforma** en la cual implementar el perfil
    - Establezca el **tipo del perfil** en **Certificado de confianza**

3. Vaya a **Configuración** y escriba el certificado de entidad de certificación raíz del archivo .cer que ha exportado anteriormente.

   > [!NOTE]
   > En función de la plataforma que haya elegido en el **paso 2**, es posible que tenga o no la opción de seleccionar el **Almacén de destino** del certificado.

   ![Crear un perfil y cargar un certificado de confianza](./media/certficates-pfx-configure/certificates-pfx-configure-profile-fill.png) 

4. Seleccione **Aceptar** > **Crear** para guardar el perfil.
5. Para asignar el perfil nuevo a uno o varios dispositivos, consulte [Asignación de perfiles de dispositivo en Microsoft Intune](../configuration/device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Creación de un perfil de certificado PKCS

1. En [Azure Portal](https://portal.azure.com), vaya a **Intune** > **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
2. Complete las siguientes propiedades:

    - **Nombre** del perfil
    - Si lo desea, establezca una descripción
    - **Plataforma** en la cual implementar el perfil
    - Establezca **Tipo del perfil** en **Certificado PKCS**

3. Vaya a **Configuración** y escriba las siguientes propiedades:

    - **Umbral de renovación (%)** : el valor recomendado es del 20 %.
    - **Período de validez del certificado**: si no ha cambiado la plantilla de certificado, esta opción puede estar establecida en un año.
    - **Proveedor de almacenamiento de claves (KSP)** : en el caso de Windows, seleccione la ubicación del dispositivo en la que quiera almacenar las claves.
    - **Entidad de certificación**: muestra el nombre de dominio completo (FQDN) interno de la CA empresarial.
    - **Nombre de la entidad de certificación**: muestra el nombre de la CA empresarial, por ejemplo "Contoso Certification Authority".
    - **Nombre de plantilla de certificado**: corresponde al nombre de la plantilla que ha creado previamente. Recuerde que el **nombre de la plantilla** predeterminado es el mismo que el **nombre para mostrar de la plantilla** *sin espacios*.
    - **Formato de nombre del sujeto**: establezca esta opción en **Nombre común**, a menos que sea necesario hacerlo de otro modo.
    - **Nombre alternativo del firmante**: establezca esta opción en **Nombre principal de usuario (UPN)** , a menos que sea necesario hacerlo de otro modo.

4. Seleccione **Aceptar** > **Crear** para guardar el perfil.
5. Para asignar el perfil nuevo a uno o varios dispositivos, consulte [Asignación de perfiles de dispositivo en Microsoft Intune](../configuration/device-profile-assign.md).

   > [!NOTE]
   > En los dispositivos con un perfil de Android Enterprise, los certificados que se instalan con un perfil de certificado PKCS no son visibles en el dispositivo. Para confirmar la correcta implementación de certificados, compruebe el estado del perfil en la consola de Intune.

## <a name="whats-new-for-connectors"></a>Novedades para los conectores
Se publican actualizaciones para los dos conectores de certificados con regularidad. Cuando actualizamos un conector, informamos aquí sobre los cambios realizados. 

El *conector de certificados PFX para Microsoft Intune* [admite actualizaciones automáticas](#requirements), mientras que *Intune Certificate Connector* se actualiza de forma manual.

### <a name="may-17-2019"></a>17 de mayo de 2019  
- **Conector de certificados PFX para Microsoft Intune: versión 6.1905.0.404**  
  Cambios de esta versión:  
  - Se ha corregido un problema por el que los certificados PFX existentes se siguen procesando, lo que provoca que el conector deje de procesar solicitudes nuevas. 

### <a name="may-6-2019"></a>6 de mayo de 2019  
- **Conector de certificados PFX para Microsoft Intune: versión 6.1905.0.402**  
  Cambios de esta versión:  
  - El intervalo de sondeo para el conector se ha reducido de 5 minutos a 30 segundos.
 
### <a name="april-2-2019"></a>2 de abril de 2019  
- **Intune Certificate Connector: versión 6.1904.1.0**  
  Cambios de esta versión:  
  - Se ha corregido un problema que podría producir que el conector no se inscriba en Intune después de iniciar sesión en el conector con una cuenta de administrador global.  
  - Incluye correcciones de fiabilidad para la revocación de certificados.  
  - Incluye correcciones de rendimiento para aumentar la rapidez con la que se procesan las solicitudes de certificado PKCS.  

- **Conector de certificados PFX para Microsoft Intune: versión 6.1904.0.401**
  > [!NOTE]  
  > La actualización automática para esta versión del conector PFX no está disponible hasta el 11 de abril de 2019.  

  Cambios de esta versión:  
  - Se ha corregido un problema que podría producir que el conector no se inscriba en Intune después de iniciar sesión en el conector con una cuenta de administrador global.  


## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](../configuration/device-profile-assign.md) y [supervise el estado](../configuration/device-profile-monitor.md).

[Use SCEP para los certificados](certificates-scep-configure.md), o bien [emita certificados PKCS a partir de un servicio web de administración de PKI de Symantec](certificates-digicert-configure.md).
