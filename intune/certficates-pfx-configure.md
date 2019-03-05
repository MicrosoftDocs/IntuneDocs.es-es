---
title: Uso de certificados de claves públicas y privadas en Microsoft Intune (Azure) | Microsoft Docs
description: Agregue o cree certificados de Public Key Cryptography Standards (PKCS) con Microsoft Intune, incluidos los pasos para exportar un certificado raíz, configurar la plantilla de certificado, descargar e instalar Microsoft Intune Certificate Connector (NDES), crear un perfil de configuración de dispositivo, crear un perfil de certificado PKCS en Azure y la entidad de certificación.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 87a7f7f77914b899b7173b8bfacb82cd0c50c6e7
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230047"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configuración y uso de certificados PKCS con Intune

Los certificados permiten autenticar y proteger el acceso a los recursos corporativos, por ejemplo, una VPN o una red Wi-Fi. Los certificados que usan un par de claves públicas y privadas, también denominados certificados PKCS, se usan en muchas organizaciones. Microsoft Intune incluye opciones de configuración integradas para usar certificados PKCS para los procesos de acceso y autenticación de los recursos de la organización. Dichas opciones de configuración se insertan (o implementan) en los dispositivos mediante los perfiles de configuración de dispositivo de Intune.

En este artículo se indican los requisitos para usar certificados PKCS, se muestra cómo exportar un certificado PKCS y cómo agregar el certificado a un perfil de configuración de dispositivo de Intune.

## <a name="requirements"></a>Requisitos

Para usar los certificados PKCS con Intune, asegúrese de que tiene la infraestructura siguiente:

- **Dominio de Active Directory**: todos los servidores mencionados en esta sección deben estar unidos al dominio de Active Directory.

  Para obtener más información sobre cómo instalar y configurar AD DS, consulte [Planeación y diseño de AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Entidad de certificación** (CA): entidad de certificación empresarial (CA).

  Para obtener más información sobre cómo instalar y configurar los Servicios de certificados de Active Directory (AD CS), consulte [Active Directory Certificate Services Step-by-Step Guide](https://technet.microsoft.com/library/cc772393) (Guía detallada de los Servicios de certificados de Active Directory).

  > [!WARNING]
  > Intune requiere ejecutar AD CS con una entidad de certificación (CA) empresarial, no una CA independiente.

- **Cliente**: se utiliza para conectarse a la CA empresarial.

- **Certificado raíz**: se trata de una copia exportada del certificado raíz desde la CA empresarial.

- **Microsoft Intune Certificate Connector**: use Azure Portal para descargar el instalador del **Conector de certificado** (**NDESConnectorSetup.exe**). 

  El conector procesa las solicitudes de certificado PKCS que se usan para la autenticación o la firma de correo electrónico S/MIME.

  El conector de certificado de NDES también admite el modo Estándar federal de procesamiento de información (FIPS). FIPS no es necesario, pero puede emitir y revocar certificados cuando está habilitado.

- **Conector de certificado PFX para Microsoft Intune**: si tiene previsto usar el cifrado de correo electrónico S/MIME, use Azure Portal para descargar el instalador de **Conector de certificado PFX para Microsoft Intune** (**PfxCertificateConnectorBootstrapper.exe**). El conector controla las solicitudes de archivos PFX importados en Intune para el cifrado de correo electrónico S/MIME para un usuario específico.

- **Windows Server**: hospeda lo siguiente:

  - Microsoft Intune Certificate Connector (NDESConnectorSetup.exe) para casos de autenticación y firma de correo electrónico S/MIME.
  - Conector de certificado PFX para Microsoft Intune (PfxCertificateConnectorBootstrapper.exe) para casos de cifrado de correo electrónico S/MIME.

  Puede ejecutar los conectores (**Microsoft Intune Certificate Connector** y **Conector de certificado PFX para Microsoft Intune**) en el mismo servidor.

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportación del certificado raíz desde la CA empresarial

Para autenticarse con VPN, Wi-Fi u otros recursos, se necesita un certificado de entidad de certificación raíz o intermedio en cada dispositivo. Los pasos siguientes explican cómo obtener el certificado requerido desde la CA empresarial.

1. Inicie sesión en la entidad de certificación empresarial con una cuenta que tenga privilegios de administración.
2. Abra un símbolo del sistema como administrador.
3. Exporte el certificado de la entidad de certificación raíz (.cer) en una ubicación a la que pueda acceder más adelante.
4. Cuando se complete el asistente, pero antes de cerrarlo, haga clic en **Iniciar la UI del conector de certificado**.

   `certutil -ca.cert certnew.cer`

   Para más información, consulte las [tareas CertUtil para administrar los certificados](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

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

## <a name="download-install-and-configure-the-certificate-connectors"></a>Descargar, instalar y configurar los conectores de certificado

### <a name="microsoft-intune-certificate-connector"></a>Conector de certificado de Microsoft Intune

> [!IMPORTANT] 
> Microsoft Intune Certificate Connector **debe** instalarse en un servidor Windows independiente. No se puede instalar en la entidad de certificación (CA) emisora.

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los dispositivos**, filtre por **Intune** y seleccione **Intune**.
2. Seleccione **Configuración de dispositivos** > **Entidad de certificación** > **Agregar**.
3. Descargue y guarde el archivo del conector. Guárdelo en una ubicación accesible desde el servidor donde va a instalar el conector.

    ![ConnectorDownload][ConnectorDownload]

4. Una vez finalizada la descarga, inicie sesión en el servidor. Después:

    1. Asegúrese de que .NET Framework 4.5 o una versión posterior esté instalado, tal como requiere el conector de certificado NDES. .NET Framework 4.5 se incluye automáticamente con Windows Server 2012 R2 y las versiones más recientes.
    2. Ejecute el instalador (NDESConnectorSetup.exe) y acepte la ubicación predeterminada. Se instala el conector en `\Program Files\Microsoft Intune\NDESConnectorUI`. En Opciones del instalador, seleccione **Distribución PFX**. Continúe y complete la instalación.
    3. De manera predeterminada, el servicio de conector inicia sesión con la cuenta de sistema local. Si se requiere un servidor proxy para el acceso a Internet, confirme que la cuenta de servicio local puede acceder a la configuración de proxy en el servidor.

5. El conector NDES abre la pestaña **Inscripción**. Para habilitar la conexión con Intune, **inicie sesión** y escriba una cuenta con permisos administrativos globales.
6. En la pestaña **Avanzadas**, se recomienda dejar seleccionado **Usar la cuenta SYSTEM de este equipo (predeterminado)**.
7. **Aplicar** > **Cerrar**
8. Vuelva a Azure Portal (**Intune** > **Configuración del dispositivo** > **Entidad de certificación**). Tras unos minutos, se mostrará una marca de verificación verde y el **Estado de la conexión** figurará como **Activo**. Ahora, el servidor del conector puede comunicarse con Intune.
9. Si tiene un proxy web en el entorno de red, es posible que necesite configuraciones adicionales para que el conector funcione. Para obtener más información, consulte [Trabajo con servidores proxy locales existentes](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) en la documentación de Azure Active Directory.

> [!NOTE]
> Con Microsoft Intune Certificate Connector se incluye la compatibilidad con TLS 1.2. Por tanto, si el servidor que tiene instalado Microsoft Intune Certificate Connector es compatible con TLS 1.2, se usará TLS 1.2. Si el servidor no admite TLS 1.2, entonces se usará TLS 1.1. Actualmente, se usa TLS 1.1 para la autenticación entre los dispositivos y el servidor.

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>Conector de certificado PFX para Microsoft Intune

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración de dispositivos** > **Entidad de certificación** > **Agregar**.
3. Descargue y guarde el Conector de certificado PFX para Microsoft Intune. Guárdelo en una ubicación accesible desde el servidor donde va a instalar el conector.
4. Una vez finalizada la descarga, inicie sesión en el servidor. Después:

    1. Asegúrese de que .NET Framework 4.6 o una versión posterior esté instalado, tal como requiere el Conector de certificado PFX para Microsoft Intune. Si .NET Framework 4.6 no está instalado, el programa de instalación lo instala de forma automática.
    2. Ejecute el instalador (PfxCertificateConnectorBootstrapper.exe) y acepte la ubicación predeterminada. Se instala el conector en `Program Files\Microsoft Intune\PFXCertificateConnector`.
    3. El servicio de conector se ejecuta en la cuenta de sistema local. Si se requiere un servidor proxy para el acceso a Internet, confirme que la cuenta de servicio local puede acceder a la configuración de proxy en el servidor.

5. El Conector de certificado PFX para Microsoft Intune se abre en la pestaña **Inscripción** después de la instalación. Para habilitar la conexión con Intune, **inicie sesión**, y escriba una cuenta con permisos de administrador global de Azure o de Intune.
6. Cierre la ventana.
7. Vuelva a Azure Portal (**Intune** > **Configuración del dispositivo** > **Entidad de certificación**). Tras unos minutos, se mostrará una marca de verificación verde y el **Estado de la conexión** figurará como **Activo**. Ahora, el servidor del conector puede comunicarse con Intune.

## <a name="create-a-trusted-certificate-profile"></a>Creación de un perfil de certificado de confianza

1. En [Azure Portal](https://portal.azure.com), vaya a **Intune** > **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.

   ![NavigateIntune][NavigateIntune]

2. Complete las siguientes propiedades:

    - **Nombre** del perfil
    - Si lo desea, establezca una descripción
    - **Plataforma** en la cual implementar el perfil
    - Establezca el **tipo del perfil** en **Certificado de confianza**

3. Vaya a **Configuración** y escriba el certificado de entidad de certificación raíz del archivo .cer que ha exportado anteriormente.

   > [!NOTE]
   > En función de la plataforma que ha elegido en el **paso 3**, es posible que tenga o no la opción de seleccionar el **Almacén de destino** del certificado.

   ![ProfileSettings][ProfileSettings]

4. Seleccione **Aceptar** > **Crear** para guardar el perfil.
5. Para asignar el perfil nuevo a uno o varios dispositivos, consulte [Asignación de perfiles de dispositivo en Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Creación de un perfil de certificado PKCS

1. En [Azure Portal](https://portal.azure.com), vaya a **Intune** > **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
2. Complete las siguientes propiedades:

    - **Nombre** del perfil
    - Si lo desea, establezca una descripción
    - **Plataforma** en la cual implementar el perfil
    - Establezca **Tipo del perfil** en **Certificado PKCS**

3. Vaya a **Configuración** y escriba las siguientes propiedades:

    - **Umbral de renovación (%)**: el valor recomendado es del 20 %.
    - **Período de validez del certificado**: si no ha cambiado la plantilla de certificado, esta opción puede estar establecida en un año.
    - **Proveedor de almacenamiento de claves (KSP)**: en el caso de Windows, seleccione la ubicación del dispositivo en la que quiera almacenar las claves.
    - **Entidad de certificación**: muestra el nombre de dominio completo (FQDN) interno de la CA empresarial.
    - **Nombre de la entidad de certificación**: muestra el nombre de la CA empresarial, por ejemplo "Contoso Certification Authority".
    - **Nombre de plantilla de certificado**: corresponde al nombre de la plantilla que ha creado previamente. Recuerde que el **nombre de la plantilla** predeterminado es el mismo que el **nombre para mostrar de la plantilla** *sin espacios*.
    - **Formato de nombre del sujeto**: establezca esta opción en **Nombre común**, a menos que sea necesario hacerlo de otro modo.
    - **Nombre alternativo del firmante**: establezca esta opción en **Nombre principal de usuario (UPN)**, a menos que sea necesario hacerlo de otro modo.

4. Seleccione **Aceptar** > **Crear** para guardar el perfil.
5. Para asignar el perfil nuevo a uno o varios dispositivos, consulte [Asignación de perfiles de dispositivo en Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Creación de un perfil de certificado PKCS importado

Puede importar los certificados emitidos previamente para un usuario específico desde cualquier CA a Intune. Los certificados importados se instalan en todos los dispositivos que inscribe un usuario. El cifrado de correo electrónico S/MIME es el escenario más común para la importación de certificados PFX existentes en Intune. Un usuario puede tener varios certificados para cifrar el correo electrónico. Las claves privadas de esos certificados deben existir en todos los dispositivos del usuario para que pueda descifrar el correo electrónico cifrado previamente.

Para importar certificados en Intune, puede usar los [cmdlets de PowerShell proporcionados en GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Después de importar los certificados en Intune, cree un perfil de **certificado PKCS importado** y asígnelo a los grupos de Azure Active Directory.

1. En [Azure Portal](https://portal.azure.com), vaya a **Intune** > **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
2. Complete las siguientes propiedades:

    - **Nombre** del perfil
    - Si lo desea, establezca una descripción
    - **Plataforma** en la cual implementar el perfil
    - Establezca **Tipo del perfil** en **Certificado PKCS importado**.

3. Vaya a **Configuración** y escriba las siguientes propiedades:

    - **Propósito planteado**: corresponde al propósito planteado de los certificados que se importan para este perfil. Un administrador puede haber importado los certificados con otros propósitos planteados (por ejemplo, autenticación, firma S/MIME o cifrado S/MIME). El propósito planteado seleccionado en el perfil de certificado coincide con el perfil de certificado con los certificados importados adecuados.
    - **Período de validez del certificado**: si no ha cambiado la plantilla de certificado, esta opción puede estar establecida en un año.
    - **Proveedor de almacenamiento de claves (KSP)**: en el caso de Windows, seleccione la ubicación del dispositivo en la que quiera almacenar las claves.

4. Seleccione **Aceptar** > **Crear** para guardar el perfil.
5. Para asignar el perfil nuevo a uno o varios dispositivos, consulte [Asignación de perfiles de dispositivo en Microsoft Intune](device-profile-assign.md).

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

[Use certificados SCEP](certificates-scep-configure.md) o [emita certificados PKCS a partir de un servicio web de administración de PKI de Symantec](certificates-symantec-configure.md).

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Navegue a Intune en Azure Portal y cree un perfil nuevo de un certificado de confianza"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Cree un perfil y cargue un certificado de confianza"
[ConnectorDownload]: ./media/certificates-download-connector.png "Descargue Certificate Connector desde Azure Portal"  
