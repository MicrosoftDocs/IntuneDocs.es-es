---
title: 'Uso de una configuración de dispositivo personalizada en Microsoft Intune: Azure | Microsoft Docs'
description: Agregar o crear un perfil para usar una configuración personalizada para dispositivos Windows Phone, Windows 8.1, Windows 10 y versiones posteriores, Android, Android Enterprise, macOS e iOS mediante Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9dd1ea3b6365cd93d7df78597a2e379ebaec7103
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836377"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Crear un perfil con una configuración personalizada en Intune

## <a name="what-are-custom-profiles"></a>¿Qué son los perfiles personalizados?

Microsoft Intune incluye muchas configuraciones integradas para controlar diversas características de un dispositivo. También es posible crear perfiles personalizados para usar las configuraciones de dispositivo y las características que no están integradas en Intune. Estos perfiles incluyen características y configuraciones para controlar dispositivos de la organización. Por ejemplo, puede crear un perfil personalizado que establece la misma función para todos los dispositivos iOS.

Para obtener más información sobre los perfiles de configuración, vea [¿Qué son los perfiles de dispositivo de Microsoft Intune?](device-profiles.md) 

Este artículo contiene vínculos para crear perfiles personalizados para Android, Android Enterprise, iOS, macOS y Windows.

## <a name="available-platforms"></a>Plataformas disponibles

La configuración personalizada se puede realizar de forma diferente en cada plataforma. Por ejemplo, para controlar características en dispositivos Android y Windows, puede especificar valores de identificador uniforme de recursos de Open Mobile Alliance (OMA-URI). Para dispositivos Apple, puede importar un archivo creado con [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) o [Apple Profile Manager](https://support.apple.com/profile-manager).

Los perfiles personalizados se crean como los perfiles integrados y están disponibles en las plataformas siguientes:

- [Android](custom-settings-android.md)
- [Android Enterprise](custom-settings-android-for-work.md)
- [iOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)

## <a name="next-steps"></a>Pasos siguientes

Elija la plataforma y empiece a trabajar:

- [Android](custom-settings-android.md)
- [Android Enterprise](custom-settings-android-for-work.md)
- [iOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
