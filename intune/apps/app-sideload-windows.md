---
title: Transferencia local de aplicaciones de Windows y Windows Phone
titleSuffix: Microsoft Intune
description: Aprenda a firmar aplicaciones de línea de negocios de modo que pueda usar Intune para implementarlas.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 03b8f050dc6232b87d1149aff0a93cd7b06839cd
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755415"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Firma de aplicaciones de línea de negocio para que se puedan implementar en dispositivos Windows con Intune

Como Administrador de Intune, puede implementar aplicaciones universales de línea de negocio (LOB) en dispositivos Windows 8.1 Desktop o Windows 10 Desktop & Mobile, incluida la aplicación del Portal de empresa. Para implementar aplicaciones *.appx* en dispositivos Windows 8.1 Desktop o Windows 10 Desktop & Mobile, puede usar un certificado de firma de código de una entidad de certificación pública que ya sea de confianza para los dispositivos Windows, o bien puede usar su propia entidad de certificación.

 > [!NOTE]
 > Windows 8.1 Desktop requiere una directiva empresarial para habilitar la instalación de prueba o el uso de claves de instalación de prueba (habilitadas automáticamente para dispositivos unidos a un dominio). Para obtener más información, vea [Instalación de prueba de Windows 8](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/).

## <a name="windows-10-sideloading"></a>Instalación de prueba de Windows 10

En Windows 10, la instalación de prueba es diferente de la de versiones anteriores de Windows:

- Puede desbloquear un dispositivo para la instalación de prueba mediante una directiva empresarial. Intune proporciona una directiva de configuración de dispositivos denominada "Instalación de aplicaciones de confianza". El establecimiento de este valor en <allow> es todo lo necesario para los dispositivos que ya confían en el certificado usado para firmar la aplicación appx.

- No se necesitan certificados de Symantec Phone ni claves de licencia de instalación de prueba. Sin embargo, si una entidad de certificación local no está disponible, puede que tenga que obtener un certificado de firma de código de una entidad de certificación pública. Para obtener más información, consulte [Introducción a la firma de código](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing).

### <a name="code-sign-your-app"></a>Firma de código de la aplicación

El primer paso es firmar el código del paquete de la aplicación. Para más información, consulte [Firma de un paquete de la aplicación con SignTool](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool).

### <a name="upload-your-app"></a>Carga de la aplicación

A continuación, debe cargar el archivo appx firmado. Para más información, consulte [Adición de una aplicación de línea de negocio de Windows a Microsoft Intune](lob-apps-windows.md).

Si implementa la aplicación según sea necesario para los usuarios o dispositivos, no necesita la aplicación Portal de empresa de Intune. Sin embargo, si implementa la aplicación como disponible para los usuarios, puede usar la aplicación Portal de empresa de la instancia pública de Microsoft Store o la aplicación Portal de empresa de la instancia privada de la Microsoft Store para Empresas; o bien tendrá que firmar e implementar manualmente la aplicación Portal de empresa de Intune.

### <a name="upload-the-code-signing-certificate"></a>Carga del certificado de firma de código

Si el dispositivo de Windows 10 todavía no confía en la entidad de certificación, después de haber firmado el paquete appx y de cargarlo en el servicio de Intune, debe cargar el certificado de firma de código en el portal de Intune:

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Haga clic en **Administración de inquilinos** > **Conectores y tokens** > **Certificados de empresa de Windows**.
3. Seleccione un archivo en **Archivo de certificado de firma de código**.
4. Seleccione el archivo *.cer* y haga clic en **Abrir**.
5. Haga clic en **Cargar** para agregar el archivo de certificado a Intune.

Ahora, cualquier dispositivo móvil o de escritorio de Windows 10 con una implementación appx por parte del servicio de Intune descargará automáticamente el certificado de empresa correspondiente, y se permitirá que la aplicación se inicie después de la instalación.

Intune solo implementa el archivo. cer más reciente que se cargó. Si tiene varios archivos appx creados por distintos desarrolladores que no están asociados a su organización, tendrá que proporcionarles archivos appx sin firmar para firmar con el certificado, o bien proporcionarles el certificado de firma de código usado por su organización.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Cómo renovar el certificado de firma de código de empresa de Symantec

El certificado usado para implementar aplicaciones móviles de Windows Phone 8.1 se dejó de usar el 28 de febrero de 2019 y ya no está disponible para su renovación desde Symantec. Si va a realizar la implementación en un dispositivo móvil de Windows 10, puede seguir usando los certificados de firma de código de Symantec Desktop Enterprise siguiendo las instrucciones sobre la [instalación de prueba de Windows 10](app-sideload-windows.md#windows-10-sideloading).

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Instalación del certificado actualizado para aplicaciones de línea de negocio (LOB)

Windows Phone 8.1

El servicio Intune ya no puede implementar aplicaciones de LOB para esta plataforma una vez que expire el certificado de firma de código de Symantec Mobile Enterprise existente. Todavía será posible realizar la instalación de prueba de archivos XAP/APPX sin firmar mediante una tarjeta SD o descargando el archivo en el dispositivo. Para obtener más información consulte [Instalación de archivos XAP en Windows Phone](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280).

Windows 8.1 Desktop/Windows 10 Desktop & Mobile

Si el período del certificado ha expirado, los archivos appx pueden dejar de iniciarse. Debe obtener un nuevo archivo. cer y seguir las instrucciones para firmar el código de cada archivo appx implementado y volver a cargar todos los archivos appx y el archivo. cer actualizado en la sección Certificados de empresa de Windows del portal de Intune.

## <a name="manually-deploy-windows-10-company-portal-app"></a>Implementación manual de la aplicación del Portal de empresa para Windows 10

Si no desea ofrecer acceso a Microsoft Store, puede implementar manualmente la aplicación del Portal de empresa para Windows 10 directamente desde Intune, aunque no haya integrado Intune con la Microsoft Store para Empresas. Como alternativa, si la ha integrado, puede implementar la aplicación de Portal de empresa con la [implementación de aplicaciones mediante la Tienda Microsoft para Empresas](store-apps-windows.md).

 > [!NOTE]
 > Esta opción requiere implementar actualizaciones manuales cada vez que se publica una actualización de la aplicación.

1. Inicie sesión con su cuenta en [Microsoft Store para Empresas](https://www.microsoft.com/business-store) y adquiera la versión de **licencia sin conexión** de la aplicación del Portal de empresa.  
2. Cuando haya adquirido la aplicación, selecciónela en la página **Inventario**.  
3. Seleccione **Windows 10 all devices** (Todos los dispositivos Windows 10) como la **plataforma**, luego, la **arquitectura** correspondiente y, finalmente, haga clic en Descargar. No se necesita un archivo de licencia de la aplicación para esta aplicación.
   ![Imagen de detalles del paquete de Windows 10 X86 para su descarga](./media/app-sideload-windows/Win10CP-all-devices.png)
4. Descargue todos los paquetes en "Marcos necesarios". Debe hacerse para las arquitecturas x86, x64 y ARM, lo que produce un total de 9 paquetes, tal como se muestra a continuación.

   ![Imagen de los archivos de dependencia para descargar ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. Antes de cargar la aplicación del Portal de empresa en Intune, cree una carpeta (por ejemplo, C:&#92;Company Portal) con los paquetes estructurados de la manera siguiente:
   1. Colocar el paquete del Portal de empresa en C:\Company Portal. Cree también una subcarpeta Dependencias en esta ubicación.  
      ![Imagen de la carpeta Dependencias guardada con el archivo APPXBUN](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. Coloque los nueve paquetes de dependencias en la carpeta Dependencias.  
      Si las dependencias no se colocan con este formato, Intune no podrá reconocer y cargarlos durante la carga de los paquetes, con lo que se producirá el siguiente error.  
      <img alt="Error message - The Windows app dependency must be provided." src="./media/app-sideload-windows/Win10CP-error-message.png" width="200">
6. Vuelva a Intune y cargue la aplicación del Portal de empresa como una nueva aplicación. Impleméntela como una aplicación necesaria para el conjunto de usuarios de destino deseado.  

Consulte [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Implementación de appxbundle con dependencias a través de la MDM de Microsoft Intune) para obtener más información sobre cómo Intune controla las dependencias de aplicaciones universales.  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>¿Cómo puedo actualizar el Portal de empresa en los dispositivos de mis usuarios si ya han instalado las aplicaciones anteriores desde la Tienda?

Si los usuarios ya han instalado las aplicaciones del Portal de empresa para Windows 8.1 o Windows Phone 8.1 desde la Tienda, recibirán automáticamente la nueva versión sin que tengan que hacer nada. Si la actualización no se realiza, pida a los usuarios que comprueben que están habilitadas en sus dispositivos las actualizaciones automáticas para las aplicaciones de la Tienda.

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>¿Cómo puedo actualizar mi aplicación transferida localmente del Portal de empresa para Windows 8.1 a la versión para Windows 10?

La ruta de migración recomendada es eliminar la implementación de la aplicación del Portal de empresa para Windows 8.1 estableciendo la acción de implementación en "Desinstalar". Una vez hecho, se puede implementar la aplicación del Portal de empresa para Windows 10 con cualquiera de las opciones anteriores.  

Si necesita transferir localmente la aplicación e implementó el Portal de empresa para Windows 8.1 sin firmar con el certificado de Symantec, siga los pasos de la sección anterior Deploy directly via Intune (Implementación directa a través de Intune) para completar la actualización.

Si necesita transferir localmente la aplicación y firmó e implementó el Portal de empresa para Windows 8.1 con el certificado de firma de código de Symantec, siga los pasos descritos en la sección siguiente.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>¿Cómo puedo actualizar mi aplicación transferida localmente y firmada del Portal de empresa para Windows Phone 8.1 o del Portal de empresa para Windows 8.1 a la versión para Windows 10?

La ruta de migración recomendada es eliminar la implementación de la aplicación del Portal de empresa para Windows Phone 8.1 o del Portal de empresa para Windows 8.1 estableciendo la acción de implementación en "Desinstalar". Una vez hecho, se puede implementar con normalidad la aplicación del Portal de empresa para Windows 10.  

Si no, habrá que actualizar y firmar correctamente la aplicación del Portal de empresa para Windows 10 para garantiza que se respeta la ruta de actualización.  

Si la aplicación del Portal de empresa para Windows 10 está firmada e implementada de esta manera, debe repetir este proceso para cada nueva actualización de la aplicación cuando esté disponible en la Tienda. La aplicación no se actualizará automáticamente cuando se actualice la Tienda.  

Así es cómo tiene que firmar e implementar la aplicación:

1. Descargue el script de firma de la aplicación Portal de empresa para Windows 10 con Microsoft Intune en [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Este script requiere instalar Windows SDK para Windows 10 en el equipo host. Para descargar Windows SDK para Windows 10, visite [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Descargue la aplicación del Portal de empresa para Windows 10 desde la Tienda Microsoft para Empresas, tal como se describe anteriormente.  
3. Ejecute el script con los parámetros de entrada que se detallan en el encabezado del script para firmar la aplicación del Portal de empresa para Windows 10 (que detalla abajo). Las dependencias no tienen que pasarse al script. Solo se necesitan cuando la aplicación va a cargarse en la consola de administración de Intune.

|       Parámetro       |                                                                    Descripción                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             La ruta de acceso donde se encuentra el archivo de origen appxbundle.                                              |
| OutputWin10AppxBundle |                                                  La ruta de acceso de salida del archivo firmado appxbundle.                                                  |
|       Win81Appx       |                          La ruta de acceso a la ubicación del archivo del Portal de empresa para Windows Phone 8.1 o Windows 8.1 (.APPX).                           |
|      PfxFilePath      |                                   La ruta de acceso al archivo de certificado de firma de código móvil de empresa de Symantec (.PFX).                                    |
|      PfxPassword      |                                     La contraseña del certificado de firma de código móvil de empresa de Symantec.                                      |
|      PublisherId      |      El identificador del publicador de la empresa. Si está ausente, se usa el campo 'Asunto' del certificado de firma de código móvil empresarial de Symantec.       |
|        SdkPath        | La ruta de acceso a la carpeta raíz de Windows SDK para Windows 10. Este argumento es opcional y está establecido de forma predeterminada en ${env:ProgramFiles(x86)}\Windows Kits\10. |

El script generará la versión firmada de la aplicación del Portal de empresa para Windows 10 cuando haya terminado de ejecutarse. Después, puede implementar la versión firmada de la aplicación como una aplicación LOB mediante Intune, que actualizará las versiones implementadas actualmente a esta nueva aplicación.  
