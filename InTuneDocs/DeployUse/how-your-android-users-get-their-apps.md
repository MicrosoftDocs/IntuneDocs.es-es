---
title: "Cómo obtienen sus aplicaciones los usuarios de Android | Microsoft Intune"
description: "Métodos para hacer que las aplicaciones de Android estén disponibles para los usuarios finales"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 7/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a3db9269bf4f93021d16d8ea23a2a13b87b43677
ms.openlocfilehash: d3d37b9bcf8cc5833b4e11185b49902e26a625dc


---


# Cómo obtienen sus aplicaciones los usuarios de Android
Lea esta información para comprender cómo y dónde obtienen los usuarios finales de Android las aplicaciones que se distribuyen a través de Microsoft Intune. La información puede variaren función de si se trata de dispositivos Android nativos o dispositivos Samsung Knox.

## Dispositivos Android nativos (distintos de Samsung Knox)

| Tipo de aplicación | Aplicaciones de línea de negocio (LOB) | Aplicaciones de Play Store  |
| ------------- |-------------| -----|
| Aplicaciones disponibles      | Los usuarios tocan **instalar** en el Portal de empresa. Aparece una notificación que los usuarios tocan para iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. | Los usuarios tocan la aplicación del Portal de empresa y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación.|
| Required apps      | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la notificación para iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece.    | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la aplicación y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. |

## Dispositivos Android Samsung Knox

| Tipo de aplicación | Aplicaciones de línea de negocio (LOB) | Aplicaciones de Play Store  |
| ------------- |-------------| -----|
| Aplicaciones disponibles      | Los usuarios tocan **instalar** en el Portal de empresa. La aplicación se instala sin la intervención del usuario. | Los usuarios tocan la aplicación del Portal de empresa y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación.|
| Required apps      | La aplicación se instala sin la intervención del usuario.    | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la aplicación y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. |

Las aplicaciones pueden ser administradas o no administradas, tal como se describe a continuación. El proceso de crear aplicaciones administradas es el mismo para todos los tipos de dispositivos Android.

**Aplicaciones administradas**: son aplicaciones que se pueden administrar mediante directivas y que están “encapsuladas” con Intune o se han creado con el kit de desarrollo de software (SDK) de administración de aplicaciones móviles (MAM) de Intune. Estas aplicaciones pueden administrarse mediante Intune y las directivas de aplicación pueden aplicarse a estas.

**Aplicaciones no administradas**: son aplicaciones que se pueden administrar mediante directivas y que no están encapsuladas con Intune o no incorporan el SDK de MAM de Intune. Las directivas de aplicación no pueden aplicarse a estas aplicaciones.

### Consulte también
[Agregar aplicaciones con Microsoft Intune](/intune/deploy-use/add-apps)

[Cómo obtienen sus aplicaciones los usuarios de iOS](how-your-ios-users-get-their-apps.md)

[Cómo obtienen sus aplicaciones los usuarios de Windows](how-your-windows-users-get-their-apps.md)



<!--HONumber=Sep16_HO5-->


