---
title: Creación de un perfil de Wi-Fi para dispositivos en Microsoft Intune - Azure | Microsoft Docs
description: Consulte estos pasos para crear un perfil de configuración de dispositivos Wi-Fi en Microsoft Intune. Cree perfiles para Android, Android Enterprise, quiosco de Android, iOS, macOS, Windows 10 y versiones posteriores, y Windows Holographic for Business. Use estos perfiles para crear una conexión Wi-Fi para usar certificados, elegir un tipo de EAP, seleccionar un método de autenticación, habilitar un proxy y mucho más.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 75cdd958d9663d5b2d330a947a19963c219feaea
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545919"
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
- macOS X 10.11 y versiones más recientes
- Windows 10 y versiones posteriores, Windows 10 Mobile y Windows Holographic for Business

> [!NOTE]
> Para dispositivos que ejecutan Windows 8.1, puede importar una configuración de Wi-Fi que se haya exportado anteriormente desde otro dispositivo.

## <a name="create-a-device-profile"></a>Creación del perfil de un dispositivo

1. En [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
2. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. Asígnele un nombre a los perfiles para que pueda identificarlos de manera sencilla más adelante. Por ejemplo, un buen nombre de perfil sería **Perfil WiFi para toda la empresa**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione la plataforma de los dispositivos. Las opciones son:

      - **Android**
      - **Android Enterprise**
      - **iOS**
      - **macOS**
      - **Windows 8.1 y versiones posteriores**
      - **Windows 10 y versiones posteriores**

    - **Tipo de perfil**: Seleccione **Wi-Fi**.

      > [!TIP]
      >
      > - Para dispositivos **Android Enterprise** que se ejecutan como un dispositivo dedicado (quiosco), elija **Solo el propietario del dispositivo** > **Wi-Fi**.
      > - Para **Windows 8.1 y versiones posteriores**, puede elegir **Importación de Wi-Fi**. Esta opción le permite importar la configuración de Wi-Fi como archivo XML exportado previamente de otro dispositivo.

3. Alguna configuración de Wi-Fi varía en función de la plataforma. Para ver la configuración de una plataforma concreta, elija la plataforma:

    - [Android](wi-fi-settings-android.md)
    - [Android Enterprise](wi-fi-settings-android-enterprise.md), incluidos los dispositivos dedicados
    - [iOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 y versiones posteriores](wi-fi-settings-windows.md)
    - [Windows 8.1 y versiones posteriores](wi-fi-settings-import-windows-8-1.md), incluido Windows Holographic for Business

4. Cuando termine, seleccione **Crear perfil** > **Crear**.

El perfil se crea y se muestra en la lista de perfiles (**Configuración del dispositivo** > **Perfiles**).

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero no hacen nada. Después, [asigne este perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).
