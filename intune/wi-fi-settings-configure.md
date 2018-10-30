---
title: Creación de un perfil de Wi-Fi para dispositivos en Microsoft Intune - Azure | Microsoft Docs
description: Consulte estos pasos para crear un perfil de configuración de dispositivos Wi-Fi en Microsoft Intune. Cree perfiles para Android, Android Enterprise, quiosco de Android, iOS, macOS, Windows 10 y versiones posteriores y Windows Holographic for Business. Use estos perfiles para crear una conexión Wi-Fi para usar certificados, elegir un tipo de EAP, seleccionar un método de autenticación, habilitar un proxy y mucho más.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16273910220dae238e15910af0557dd8b73646b9
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2018
ms.locfileid: "49425264"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Adición y uso de la configuración de Wi-Fi en los dispositivos en Microsoft Intune

Use perfiles de Wi-Fi de Microsoft Intune para asignar la configuración de red inalámbrica a los usuarios y los dispositivos de la organización. Al asignar un perfil de Wi-Fi, los usuarios pueden acceder a la red Wi-Fi de su organización sin tener que configurarla ellos mismos.

Por ejemplo, instale una nueva red Wi-Fi denominada Contoso Wi-Fi. Desea configurar todos los dispositivos iOS para conectarse a esta red. Este es el proceso:

1. Cree un perfil de Wi-Fi que contenga la configuración para conectarse a la red inalámbrica Contoso Wi-Fi.
2. Asigne el perfil a un grupo que contenga todos los usuarios de dispositivos iOS.
3. Los usuarios encuentran la nueva red Contoso Wi-Fi en la lista de redes inalámbricas de su dispositivo. Pueden conectarse a ella fácilmente con el método de autenticación de su elección.

Use los pasos de este artículo para crear un perfil de Wi-Fi. A continuación, revise los temas sobre la configuración y los detalles específicos de la plataforma.

## <a name="supported-device-platforms"></a>Plataformas de dispositivos compatibles

Los perfiles de Wi-Fi admiten las siguientes plataformas de dispositivo:

- Android 4 y versiones posteriores
- Quiosco de Android y Android Enterprise
- iOS 8.0 y versiones posteriores
- macOS (Mac OS X 10.11 y versiones posteriores)
- Windows 10 y versiones posteriores, Windows 10 Mobile y Windows Holographic for Business

> [!NOTE]
> Para dispositivos que ejecutan Windows 8.1, puede importar una configuración de Wi-Fi que se haya exportado anteriormente desde otro dispositivo.

## <a name="create-a-wi-fi-device-profile"></a>Creación de un perfil para dispositivos Wi-Fi

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**. 
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba un **nombre** y una **descripción** para el perfil de Wi-Fi.
4. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar la configuración de Wi-Fi. Las opciones son:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**

5. En **Tipo de perfil**, elija **Wi-Fi**.

    - Para dispositivos **Android Enterprise** que se ejecutan como un quiosco, puede elegir **Solo el propietario del dispositivo** > **Wi-Fi**.
    - Para **Windows 8.1 y versiones posteriores**, puede elegir **Importación de Wi-Fi**. Esta opción le permite importar la configuración de Wi-Fi como archivo XML exportado previamente de otro dispositivo.

6. Alguna configuración de Wi-Fi varía en función de la plataforma. Para ver la configuración de una plataforma concreta, elija:

    - [Android](wi-fi-settings-android.md)
    - [Quiosco de Android y Android Enterprise](wi-fi-settings-android-enterprise.md)
    - [iOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 y versiones posteriores](wi-fi-settings-windows.md)
    - [Windows 8.1 y versiones posteriores](wi-fi-settings-import-windows-8-1.md), incluido Windows Holographic for Business

    La mayoría de las plataformas tienen una configuración **Básica** y de **Empresa**. La **Básica** incluye características como el nombre de red y el SSID. La opción **Empresa** permite proporcionar información más avanzada, como el Protocolo de autenticación extensible (EAP).

7. Cuando termine de agregar la configuración de Wi-Fi, seleccione **Crear perfil** > **Crear** para agregar el perfil de configuración. El perfil se crea y se muestra en la lista de perfiles (**Configuración del dispositivo** > **Perfiles**).

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero no hacen nada. A continuación, [asigne este perfil](device-profile-assign.md).
