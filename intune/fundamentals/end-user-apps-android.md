---
title: Cómo obtienen sus aplicaciones los usuarios de Android
description: Métodos para hacer que las aplicaciones de Android estén disponibles para los usuarios finales
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: fc5362df560d2e93bf5cd7a6cdc32a441d97d05c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505418"
---
# <a name="how-your-android-users-get-their-apps"></a>Cómo obtienen sus aplicaciones los usuarios de Android

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Este artículo le ayuda a comprender cómo y dónde obtienen los usuarios finales de Android las aplicaciones que se distribuyen a través de Microsoft Intune. La información puede variar por tipo de dispositivo (dispositivos Android nativos o dispositivos Samsung Knox Standard).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Dispositivos Android nativos (distintos a Samsung KNOX Standard)

| Tipo de aplicación | Aplicaciones de línea de negocio (LOB) | Aplicaciones de Play Store  |
| ------------- |-------------| -----|
| Aplicaciones disponibles      | Los usuarios tocan **instalar** en el Portal de empresa. Aparece una notificación que los usuarios tocan para iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. | Los usuarios tocan la aplicación del Portal de empresa y se les dirige a una página de la aplicación en la Play Store. Aquí es donde inician la instalación.|
| Required apps      | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la notificación para iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece.    | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la notificación y se les dirige a una página de la aplicación en la Play Store. Aquí es donde inician la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. |

Los usuarios finales necesitan permitir la instalación desde orígenes desconocidos para poder instalar [aplicaciones de LOB](../apps/lob-apps-android.md). Normalmente, esta opción se encuentra en dos lugares diferentes:

* **Android 7.1.2 y versiones anteriores**: **Configuración** > **Seguridad** > **Orígenes desconocidos**
* **Android 8.0 y versiones posteriores**: **Configuración** > **Aplicaciones y notificaciones** > **Acceso especial a las aplicaciones** > **Instalar aplicaciones desconocidas** > **Portal de empresa** > **Permitir desde este origen**

Si ocurre esto, la aplicación Portal de empresa informará y guiará directamente al usuario final hasta la configuración adecuada. 

## <a name="samsung-knox-standard-android-devices"></a>Dispositivos Samsung Knox Standard con Android

| Tipo de aplicación | Aplicaciones de línea de negocio (LOB) | Aplicaciones de Play Store  |
| ------------- |-------------| -----|
| Aplicaciones disponibles      | Los usuarios tocan **instalar** en el Portal de empresa. La aplicación se instala sin la intervención del usuario. | Los usuarios tocan la aplicación del Portal de empresa y se les dirige a una página de la aplicación en la Play Store. Aquí es donde inician la instalación.|
| Required apps      | La aplicación se instala sin la intervención del usuario.    | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la notificación y se les dirige a una página de la aplicación en la Play Store. Aquí es donde inician la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. |

Las aplicaciones pueden ser administradas o no administradas, tal como se describe a continuación. El proceso de crear aplicaciones administradas es el mismo para todos los tipos de dispositivos Android.

**Aplicaciones administradas**: estas aplicaciones se administran a través de directivas. Intune las ha "encapsulado" o compilado mediante el SDK para aplicaciones de Intune. Estas aplicaciones pueden administrarse mediante Intune y las directivas de aplicación pueden aplicarse a estas.

**Aplicaciones no administradas**: estas aplicaciones no se administran a través de directivas. Intune no las ha encapsulado o no incorporan el SDK para aplicaciones de Intune. Las directivas de aplicación no pueden aplicarse a estas aplicaciones.

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>Dispositivos Zebra con Zebra Mobility Extensions

Intune usa el kit de herramientas Zebra Mobility Extensions (MX) para instalar de forma silenciosa aplicaciones en dispositivos Zebra administrados por el administrador de dispositivos. Esta característica permite implementar y actualizar aplicaciones en dispositivos Zebra sin intervención del usuario. Si la versión MX del dispositivo es 4.2 o anterior, las aplicaciones no se instalan de forma silenciosa. Para obtener más información, vea la página sobre la [matriz completa de características de MX](http://techdocs.zebra.com/mx/compatibility/) en el sitio web de Zebra.

Las aplicaciones de LOB implementadas en dispositivos Zebra deben instalarse desde una ubicación pública en el dispositivo. El paquete de la aplicación. apk puede ser accesible para otras aplicaciones y servicios que también tienen acceso al almacenamiento público en el dispositivo. Normalmente, este acceso es una ventana pequeña entre la finalización de la descarga de la aplicación y el principio de la instalación. Esta ventana puede permitir un ataque de temporización. Por ejemplo, un paquete. apk se podría cambiar durante esta ventana. Intune reduce la cantidad de tiempo que el .apk pasa en el almacenamiento público y no permite la instalación de aplicaciones sin firmar. Para ayudar a minimizar el riesgo de seguridad, asegúrese de que los archivos. apk que cargue no contengan información confidencial.

## <a name="see-also"></a>Consulte también

[Agregar aplicaciones con Microsoft Intune](../apps/apps-add.md)

[Cómo obtienen sus aplicaciones los usuarios de iOS](end-user-apps-ios.md)

[Cómo obtienen sus aplicaciones los usuarios de Windows](end-user-apps-windows.md)
