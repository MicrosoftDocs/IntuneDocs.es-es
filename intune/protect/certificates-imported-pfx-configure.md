---
title: 'Uso de certificados PFX importados en Microsoft Intune: Azure | Microsoft Docs'
description: Utilice los certificados de estándares de criptografía de clave pública (PKCS) importados con Microsoft Intune, incluida la importación de certificados, la configuración de la plantilla de certificado, la instalación del Conector de certificado PFX importado para Intune y la creación de un perfil de certificado PKCS importado.
keywords: ''
author: ralms
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: fead8b9d69f5356876c0b3a2a4ce02e9b754128e
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999342"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>Configuración y uso de certificados PKCS importados con Intune

Microsoft Intune admite el uso de certificados de pares de claves públicas (PKCS) importados, que se suelen usar para el cifrado S/MIME con perfiles de correo electrónico. Algunos perfiles de correo electrónico de Intune admiten una opción para habilitar S/MIME, donde puede definir un certificado de firma S/MIME y el certificado de cifrado S/MIME.

El cifrado S/MIME es complejo porque el correo electrónico está cifrado con un certificado específico. Debe tener la clave privada del certificado que cifró el correo electrónico en el dispositivo en el que lee el correo electrónico para que se pueda descifrar. Los certificados de cifrado se renuevan periódicamente, lo que significa que es posible que necesite el historial de cifrado en todos los dispositivos para asegurarse de que puede leer el correo electrónico anterior.  Dado que se debe usar el mismo certificado en todos los dispositivos, no es posible usar perfiles de certificado [SCEP](certificates-scep-configure.md) o [PKCS](certficates-pfx-configure.md) para este propósito, ya que los mecanismos de entrega de certificados proporcionan certificados únicos por dispositivo. 

Para más información sobre el uso de S/MIME con Intune, consulte [Uso de S/MIME para cifrar el correo electrónico](certificates-s-mime-encryption-sign.md).

## <a name="requirements"></a>Requisitos

Para usar certificados PKCS importados con Intune, debe contar con esta infraestructura:

- **Conector de certificado PFX para Microsoft Intune**:  
  Cada inquilino de Intune admite una única instancia de este conector. Puede instalar este conector en el mismo servidor que una instancia de Microsoft Intune Certificate Connector.

  El conector controla las solicitudes de archivos PFX importados en Intune para el cifrado de correo electrónico S/MIME para un usuario específico.  

  Este conector pueda actualizarse automáticamente cuando estén disponibles nuevas versiones. Para utilizar la funcionalidad de actualización, asegúrese de que los firewalls están abiertos para permitir que el conector se ponga en contacto con **autoupdate.msappproxy.net** en el puerto **443**.  

  Para más información sobre todos los puntos de conexión de red a los que accede el conector, consulte [Ancho de banda y requisitos de configuración de red de Intune](../fundamentals/network-bandwidth-use.md).


- **Windows Server**:  
  Utilice una instancia de Windows Server para hospedar el conector de certificado PFX para Microsoft Intune.  El conector se usa para procesar solicitudes de los certificados importados a Intune.

  Intune admite la instalación de *Microsoft Intune Certificate Connector* en el mismo servidor que el *conector de certificado PFX para Microsoft Intune*.

  Para admitir el conector, el servidor debe ejecutar .NET Framework 4.6, o una versión posterior. Si .NET Framework 4.6 no está instalado al iniciar la instalación del conector, se instalará automáticamente con el conector.

- **Visual Studio 2015 o posterior** (opcional): Use Visual Studio para compilar el módulo asistente de PowerShell con cmdlets para la importación de certificados PFX en Microsoft Intune. Para obtener los cmdlets de PowerShell del asistente, consulte [PFXImport PowerShell Project en GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="how-it-works"></a>Cómo funciona

Al utilizar Intune para implementar un **certificado PFX importado** para un usuario, hay dos componentes en juego además del dispositivo: 

- **Servicio Intune**: Almacena los certificados PFX en un estado cifrado y controla la implementación del certificado en el dispositivo del usuario.  Las contraseñas que protegen las claves privadas de los certificados se cifran antes de que se carguen mediante un módulo de seguridad de hardware (HSM) o la criptografía de Windows, asegurándose de que Intune no pueda acceder a la clave privada en ningún momento.
- **Conector de certificado PFX para Microsoft Intune**: Cuando un dispositivo solicita un certificado PFX que se importó en Intune, la contraseña cifrada, el certificado y la clave pública del dispositivo se envían al conector.  El conector descifra la contraseña mediante la clave privada local y, a continuación, vuelve a cifrar la contraseña (y cualquier perfil de archivo plist si usa iOS) con la clave del dispositivo antes de volver a enviar el certificado a Intune.  Intune envía entonces el certificado al dispositivo y este puede descifrarlo con la clave privada del dispositivo e instalar el certificado.

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>Descarga, instalación y configuración del conector de certificado PFX para Microsoft Intune

1. En el portal [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), seleccione **Configuración de dispositivos** > **Certification Connectors** > **Agregar** (Conectores de certificación > Agregar).

   ![Descarga del conector de certificado PFX para Microsoft Intune](./media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

2. Siga las instrucciones para descargar el *conector de certificado PFX para Microsoft Intune* a una ubicación a la que se pueda acceder desde el servidor donde va a instalar el conector.
3. Una vez finalizada la descarga, inicie sesión en el servidor y ejecute el instalador (PfxCertificateConnectorBootstrapper.exe).  
   - Cuando acepta la ubicación de instalación predeterminada, el conector se instala en `Program Files\Microsoft Intune\PFXCertificateConnector`.
   - El servicio de conector se ejecuta en la cuenta de sistema local. Si se requiere un servidor proxy para el acceso a Internet, confirme que la cuenta de servicio local puede acceder a la configuración de proxy en el servidor.

4. El Conector de certificado PFX para Microsoft Intune se abre en la pestaña **Inscripción** después de la instalación. Para habilitar la conexión con Intune, **inicie sesión**, y escriba una cuenta con permisos de administrador global de Azure o de Intune.

   > [!WARNING]
   > De forma predeterminada, en Windows Server, la opción **Configuración de seguridad mejorada de Internet Explorer** está establecida en **Activada**, lo que puede causar problemas con el inicio de sesión en Office 365.

5. Cierre la ventana.
6. En el portal de Intune, vaya a **Configuración del dispositivo** > **Certification Connectors** (Conectores de certificación). En unos minutos, se muestra una marca de verificación verde y el **estado de la conexión** es **Activo**. El servidor del conector puede comunicarse ahora con Intune.

## <a name="import-pfx-certificates-to-intune"></a>Importación de certificados PFX en Intune

Use [Microsoft Graph](https://docs.microsoft.com/graph) para importar los certificados PFX de los usuarios en Intune. El asistente [PFXImport PowerShell Project en GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) proporciona cmdlets para realizar las operaciones con facilidad.

Si prefiere usar su propia solución personalizada con Graph, use el [tipo de recurso userPFXCertificate](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta).

### <a name="build-pfximport-powershell-project-cmdlets"></a>Compilación de cmdlets de "PFXImport PowerShell Project"

Para usar los cmdlets de PowerShell, puede compilar el proyecto con Visual Studio. El proceso es sencillo y, mientras puede ejecutarse en el servidor, se recomienda ejecutarlo en la estación de trabajo.  

1. Vaya a la raíz del repositorio [Intune-Resource-Access](https://github.com/microsoft/Intune-Resource-Access) en GitHub y, a continuación, descargue o clone el repositorio con Git en la máquina.

   ![Botón de descarga de GitHub](./media/certificates-imported-pfx-configure/github-download.png)

2. Vaya a `.\Intune-Resource-Access-develop\src\PFXImportPowershell\` y abra el proyecto con Visual Studio mediante el archivo **PFXImportPS.sln**.
3. En la parte superior, cambie de **Depurar** a **Liberar**.
4. Vaya a **Compilar** y seleccione **Build PFXImportPS**. Transcurridos unos instantes, verá que aparece un mensaje de confirmación de **compilación correcta** en la parte inferior izquierda de Visual Studio.

   ![Opción de compilación de Visual Studio](./media/certificates-imported-pfx-configure/vs-build-release.png)

5. En el proceso de compilación se crea una nueva carpeta con el módulo de PowerShell en `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release`.

   Usará la carpeta **Release** para los pasos siguientes.

### <a name="create-the-encryption-public-key"></a>Creación de la clave pública de cifrado

Importe los certificados PFX y sus claves privadas a Intune. La contraseña que protege la clave privada se cifra con una clave pública, que se almacena de forma local. Puede usar la criptografía de Windows, un módulo de seguridad de hardware u otro tipo de criptografía para generar y almacenar los pares de claves pública y privada.  Según el tipo de cifrado utilizado, el par de claves pública y privada se puede exportar en un formato de archivo para realizar copias de seguridad.

El módulo de PowerShell proporciona métodos para crear una clave mediante la criptografía de Windows. También puede usar otras herramientas para crear una clave.  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>Para crear la clave de cifrado mediante la criptografía de Windows

1. Copie la carpeta *Release* creada por Visual Studio en el servidor donde instaló el **conector de certificado PFX para Microsoft Intune**. Este carpeta contiene el módulo de PowerShell.  
2. En el servidor, abra *PowerShell* como administrador y vaya a la carpeta *Release* que contiene el módulo de PowerShell.
3. Para importar el módulo, ejecute `Import-Module .\IntunePfxImport.psd1`.
4. A continuación, ejecute `Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`.

   > [!TIP]  
   > El proveedor que usa debe volver a seleccionarse al importar los certificados PFX. Puede utilizar el **proveedor de almacenamiento de claves de software de Microsoft**, aunque también puede usar otro proveedor. Como ejemplo, también se proporciona el nombre de clave y puede usar el nombre de clave diferente de su elección.  

   Si tiene previsto importar el certificado desde la estación de trabajo, puede exportar esta clave a un archivo con el comando `Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path to write to>"`.

   Se debe importar la clave privada en el servidor que hospeda el conector de certificado PFX para Microsoft Intune para que los certificados PFX importados se puedan procesar correctamente.  

#### <a name="to-use-a-hardware-security-module-hsm"></a>Para usar un módulo de seguridad de hardware (HSM)  

Puede usar un módulo de seguridad de hardware (HSM) para generar y almacenar el par de claves pública y privada. Para más información, consulte la documentación del proveedor de HSM.

### <a name="import-pfx-certificates"></a>Importación de certificados PFX 

En el proceso siguiente se usan los cmdlets de PowerShell como ejemplo de cómo importar los certificados PFX. Puede elegir distintas opciones en función de sus necesidades.

Las opciones son:  
- Propósito planteado (agrupa los certificados basados en una etiqueta):  
  - unassigned
  - smimeEncryption
  - smimeSigning


- Esquema de relleno:  
  - pkcs1
  - oaepSha1
  - oaepSha256
  - oaepSha384
  - oaepSha512

Seleccione el proveedor de almacenamiento de claves que coincida con el proveedor que utilizó para crear la clave.

#### <a name="to-import-the-pfx-certificate"></a>Para importar el certificado PFX  

1. Exporte los certificados desde cualquier entidad de certificación siguiendo la documentación del proveedor.  Para los Servicios de certificados de Microsoft Active Directory, puede usar [este script de ejemplo](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b).   
2. En el servidor, abra *PowerShell* como administrador y vaya a la carpeta *Release* que contiene el módulo de PowerShell.
3. Para importar el módulo, ejecute `Import-Module .\IntunePfxImport.psd1`.  
4. Para autenticarse en Graph de Intune, ejecute `$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"`.

   > [!NOTE]
   > Como la autenticación se ejecuta en Graph, debe proporcionar permisos a AppID. Si es la primera vez que usa esta utilidad, se requiere un *administrador global*. Los cmdlets de PowerShell usan el mismo AppID que el que se usa con los [ejemplos de Intune de PowerShell](https://github.com/microsoftgraph/powershell-intune-samples).   
5. Convierta la contraseña de cada archivo PFX que se va a importar en una cadena segura mediante la ejecución de `$SecureFilePassword = ConvertTo-SecureString -String "<PFXPassword>" -AsPlainText -Force`.  
6. Para crear un objeto **UserPFXCertificate**, ejecute `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>"`.

   Por ejemplo: `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "C:\temp\userA.pfx" $SecureFilePassword "userA@contoso.com" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption" "pkcs1"`

   > [!NOTE]  
   > Cuando importe el certificado desde un sistema que no sea el servidor en el que está instalado el conector, tiene que usar el comando siguiente, que incluye la ruta de acceso del archivo de claves `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>" "<File path to public key file>"`.

7. Importe el objeto **UserPFXCertificate** a Intune mediante la ejecución de `Import-IntuneUserPfxCertificate -AuthenticationResult $authResult -CertificateList $userPFXObject`.

8. Para validar que el certificado se ha importado, ejecute `Get-IntuneUserPfxCertificate -AuthenticationResult $authResult -UserList "<UserUPN>"`.

Para más información sobre otros comandos disponibles, consulte el archivo Léame en [PFXImport PowerShell Project en GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Creación de un perfil de certificado PKCS importado

Después de importar los certificados en Intune, cree un perfil de **certificado PKCS importado** y asígnelo a los grupos de Azure Active Directory.

1. En el portal de [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), vaya a **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
2. Escriba las propiedades siguientes:

   - **Nombre** del perfil
   - Si lo desea, establezca una descripción
   - **Plataforma** en la cual implementar el perfil
   - Establezca **Tipo del perfil** en **Certificado PKCS importado**.

3. Vaya a **Configuración** y escriba las siguientes propiedades:

   - **Propósito planteado**: Especifique el propósito planteado de los certificados que se importan para este perfil. Los administradores pueden importar los certificados con otros propósitos planteados (como firma S/MIME o cifrado S/MIME). El propósito planteado seleccionado en el perfil de certificado coincide con el perfil de certificado con los certificados importados adecuados. El propósito planteado es una etiqueta para agrupar los certificados importados y no garantiza que los certificados importados con esa etiqueta cumplan dicho propósito.  
   - **Período de validez del certificado**: A menos que se haya cambiado el período de validez en la plantilla de certificado, esta opción tiene como valor predeterminado un año.  
   - **Proveedor de almacenamiento de claves (KSP)** : en el caso de Windows, seleccione la ubicación del dispositivo en la que quiera almacenar las claves.  

4. Seleccione **Aceptar** > **Crear** para guardar el perfil.
5. Para asignar el perfil nuevo a uno o varios dispositivos, consulte [Asignación de perfiles de dispositivo en Microsoft Intune](../configuration/device-profile-assign.md).



