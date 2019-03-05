---
title: Creación de un perfil de Wi-Fi para dispositivos en Microsoft Intune - Azure | Microsoft Docs
description: Consulte estos pasos para crear un perfil de configuración de dispositivos Wi-Fi en Microsoft Intune. Cree perfiles para Android, Android Enterprise, quiosco de Android, iOS, macOS, Windows 10 y versiones posteriores y Windows Holographic for Business. Use estos perfiles para crear una conexión Wi-Fi para usar certificados, elegir un tipo de EAP, seleccionar un método de autenticación, habilitar un proxy y mucho más.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a11b99a52fe1aec8d8908cdffa2a763e7462bd4
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233770"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Adición y uso de la configuración de Wi-Fi en los dispositivos en Microsoft Intune

Wi-Fi es una red inalámbrica que muchos dispositivos móviles utilizan para acceder a la red. Microsoft Intune incluye configuraciones Wi-Fi integradas que se pueden implementar en usuarios y dispositivos de su organización. Este grupo de configuración se conoce como un "perfil" y se puede asignar a distintos usuarios y grupos. Una vez asignado, los usuarios acceden a la red Wi-Fi de la organización sin tener que configurarla ellos mismos.

Por ejemplo, instale una nueva red Wi-Fi denominada Contoso Wi-Fi. Desea configurar todos los dispositivos iOS para conectarse a esta red. Este es el proceso:

1. Cree un perfil de Wi-Fi que contenga la configuración para conectarse a la red inalámbrica Contoso Wi-Fi.
2. Asigne el perfil a un grupo que incluya todos los usuarios de dispositivos iOS.
3. Los usuarios encuentran la nueva red Contoso Wi-Fi en la lista de redes inalámbricas de su dispositivo. Pueden conectarse a ella fácilmente con el método de autenticación de su elección.

En este artículo se enumeran los pasos para crear un perfil Wi-Fi. También incluye vínculos que describen las distintas configuraciones para cada plataforma.

## <a name="supported-device-platforms"></a>Plataformas de dispositivos compatibles

Los perfiles de Wi-Fi admiten las siguientes plataformas de dispositivo:

- Android 4 y versiones posteriores
- Quiosco de Android y Android Enterprise
- iOS 8.0 y versiones posteriores
- macOS (Mac OS X 10.11 y versiones posteriores)
- Windows 10 y versiones posteriores, Windows 10 Mobile y Windows Holographic for Business

> [!NOTE]
> Para dispositivos que ejecutan Windows 8.1, puede importar una configuración de Wi-Fi que se haya exportado anteriormente desde otro dispositivo.

## <a name="create-a-device-profile"></a>Creación del perfil de un dispositivo

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**. 
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba un **nombre** y una **descripción** para el perfil de Wi-Fi.
4. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar la configuración de Wi-Fi. Las opciones son:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
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

Se crea el perfil, pero no hacen nada. Después, [asigne este perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).
