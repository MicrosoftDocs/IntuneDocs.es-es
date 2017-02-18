---
title: "Cómo obtienen sus aplicaciones los usuarios de Android | Microsoft Docs"
description: "Métodos para hacer que las aplicaciones de Android estén disponibles para los usuarios finales"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 370dd5d4a96253f0b7d208ef85659beeace18739


---


# <a name="how-your-android-users-get-their-apps"></a>Cómo obtienen sus aplicaciones los usuarios de Android

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Lea esta información para comprender cómo y dónde obtienen los usuarios finales de Android las aplicaciones que se distribuyen a través de Microsoft Intune. La información puede variar por tipo de dispositivo (dispositivos Android nativos o dispositivos Samsung Knox Standard).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Dispositivos Android nativos (distintos a Samsung KNOX Standard)

| Tipo de aplicación | Aplicaciones de línea de negocio (LOB) | Aplicaciones de Play Store  |
| ------------- |-------------| -----|
| Aplicaciones disponibles      | Los usuarios tocan **instalar** en el Portal de empresa. Aparece una notificación que los usuarios tocan para iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. | Los usuarios tocan la aplicación del Portal de empresa y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación.|
| Required apps      | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la notificación para iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece.    | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la aplicación y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. |

## <a name="samsung-knox-standard-android-devices"></a>Dispositivos Samsung Knox Standard con Android

| Tipo de aplicación | Aplicaciones de línea de negocio (LOB) | Aplicaciones de Play Store  |
| ------------- |-------------| -----|
| Aplicaciones disponibles      | Los usuarios tocan **instalar** en el Portal de empresa. La aplicación se instala sin la intervención del usuario. | Los usuarios tocan la aplicación del Portal de empresa y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación.|
| Required apps      | La aplicación se instala sin la intervención del usuario.    | Los usuarios ven una notificación, que no se puede descartar y que indica que deben instalar una aplicación. Los usuarios tocan la aplicación y se les dirige a una página de la aplicación en la Play Store donde puede iniciar la instalación. Una vez realizada la instalación correctamente, la notificación desaparece. |

Las aplicaciones pueden ser administradas o no administradas, tal como se describe a continuación. El proceso de crear aplicaciones administradas es el mismo para todos los tipos de dispositivos Android.

**Aplicaciones administradas**: son aplicaciones que se pueden administrar a través de directivas. Se han "encapsulado" por Intune o se han creado con el kit de desarrollo de software (SDK) de administración de aplicaciones móviles (MAM) de Intune. Estas aplicaciones pueden administrarse mediante Intune y las directivas de aplicación pueden aplicarse a estas.

**Aplicaciones no administradas**: son aplicaciones que no se pueden administrar a través de directivas. No están encapsuladas por Intune o no incorporan el SDK de MAM de Intune. Las directivas de aplicación no pueden aplicarse a estas aplicaciones.

### <a name="see-also"></a>Consulte también
[Agregar aplicaciones con Microsoft Intune](/intune/deploy-use/add-apps)

[Cómo obtienen sus aplicaciones los usuarios de iOS](how-your-ios-users-get-their-apps.md)

[Cómo obtienen sus aplicaciones los usuarios de Windows](how-your-windows-users-get-their-apps.md)



<!--HONumber=Dec16_HO2-->


