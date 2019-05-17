---
title: Cómo obtienen sus aplicaciones los usuarios de Android
description: Métodos para hacer que las aplicaciones de Android estén disponibles para los usuarios finales
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/21/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4169f5625965ebc7d2bbbf9153cb4183fcd22b3
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57388067"
---
# <a name="how-your-android-users-get-their-apps"></a>Cómo obtienen sus aplicaciones los usuarios de Android

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Lea esta información para comprender cómo y dónde obtienen los usuarios finales de Android las aplicaciones que se distribuyen a través de Microsoft Intune. La información puede variar por tipo de dispositivo (dispositivos Android nativos o dispositivos Samsung Knox Standard).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Dispositivos Android nativos (distintos a Samsung KNOX Standard)

| Tipo de aplicación | Aplicaciones de línea de negocio (LOB) | Aplicaciones de Play Store  |
| ------------- |-------------| -----|
| Aplicaciones disponibles      | Los usuarios tocan **instalar** en el Portal de empresa. Aparece una notificación que los usuarios tocan para iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. | Los usuarios tocan la aplicación del Portal de empresa y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación.|
| Required apps      | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la notificación para iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece.    | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la aplicación y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. |

Los usuarios finales necesitan permitir la instalación desde orígenes desconocidos para poder instalar [aplicaciones de LOB](lob-apps-android.md). Normalmente, esta opción se encuentra en dos lugares diferentes:

* **Android 7.1.2 y versiones anteriores**: **Configuración** > **Seguridad** > **Orígenes desconocidos**
* **Android 8.0 y versiones posteriores**: **Configuración** > **Aplicaciones y notificaciones** > **Acceso especial a las aplicaciones** > **Instalar aplicaciones desconocidas** > **Portal de empresa** > **Permitir desde este origen**

Si ocurre esto, la aplicación Portal de empresa informará y guiará directamente al usuario final hasta la configuración adecuada. 


## <a name="samsung-knox-standard-android-devices"></a>Dispositivos Samsung Knox Standard con Android

| Tipo de aplicación | Aplicaciones de línea de negocio (LOB) | Aplicaciones de Play Store  |
| ------------- |-------------| -----|
| Aplicaciones disponibles      | Los usuarios tocan **instalar** en el Portal de empresa. La aplicación se instala sin la intervención del usuario. | Los usuarios tocan la aplicación del Portal de empresa y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación.|
| Required apps      | La aplicación se instala sin la intervención del usuario.    | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la aplicación y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. |

Las aplicaciones pueden ser administradas o no administradas, tal como se describe a continuación. El proceso de crear aplicaciones administradas es el mismo para todos los tipos de dispositivos Android.

**Aplicaciones administradas**: son aplicaciones que se pueden administrar a través de directivas. Intune las ha "encapsulado" o compilado mediante el SDK para aplicaciones de Intune. Estas aplicaciones pueden administrarse mediante Intune y las directivas de aplicación pueden aplicarse a estas.

**Aplicaciones no administradas**: son aplicaciones que no se pueden administrar a través de directivas. Intune no las ha encapsulado o no incorporan el SDK para aplicaciones de Intune. Las directivas de aplicación no pueden aplicarse a estas aplicaciones.

### <a name="see-also"></a>Consulte también
[Agregar aplicaciones con Microsoft Intune](apps-add.md)

[Cómo obtienen sus aplicaciones los usuarios de iOS](end-user-apps-ios.md)

[Cómo obtienen sus aplicaciones los usuarios de Windows](end-user-apps-windows.md)
