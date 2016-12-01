---
title: "Elegir cómo inscribir dispositivos móviles | Microsoft Intune"
description: "Decidir cómo inscribir dispositivos móviles en Intune respondiendo a unas preguntas sencillas"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: a563105aafb447c6e009cca09645e630709ff72d
ms.openlocfilehash: 143f77bde09648a233ff09e9740668191a50cb1e


---

# <a name="choose-how-to-enroll-mobile-devices"></a>Elegir cómo inscribir dispositivos móviles

Las respuestas a las siguientes preguntas le servirán para saber cuál es el mejor método de inscripción de los dispositivos que administra.

## <a name="do-employees-bring-their-own-devices-or-are-devices-provided-by-your-organization"></a>**¿Los empleados traen sus propios dispositivos o se los proporciona la organización?**

  - **Dispositivos de usuarios**: inscripción "Bring your own device" (BYOD)
  - **Dispositivos de empresa**: inscripción COD

> [!div class="button"]
[Inscripción BYOD >](#what-byod-devices-can-your-users-enroll)   
> [!div class="button"]
[Inscripción COD >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

## <a name="what-byod-devices-can-your-users-enroll"></a>**¿Qué dispositivos BYOD pueden inscribir sus usuarios?**

> [!div class="button"]
[Android](/intune/deploy-use/set-up-android-management-with-microsoft-intune) [iOS y Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 Mobile y Window Phone](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) [equipos PC Windows](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)

## <a name="are-your-company-owned-devices-shared-or-do-they-have-dedicated-users"></a>**¿Los dispositivos propiedad de la empresa son compartidos o se destinan a usuarios dedicados?**

> [!div class="button"]
[Compartido >](#what-operating-system-are-your-shared-devices-running)   [Dedicado >](#how-will-you-manage-dedicated-ios-devices)


## <a name="what-operating-system-are-your-shared-devices-running"></a>**¿En qué sistema operativo se ejecutan los dispositivos compartidos?**

> [!div class="button"]
[Windows >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#how-will-you-manage-shared-ios-devices)

## <a name="how-will-you-manage-shared-ios-devices"></a>**¿Cómo se administran los dispositivos iOS compartidos?**

> [!div class="button"]
[Inscripción iOS DEP >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Inscripción iOS Direct>](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)  [Inscripción DEM >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Programa de inscripción de dispositivos (DEP) de Apple**: los dispositivos iOS adquiridos o administrados con DEP se pueden asociar con un perfil de inscripción. Cuando los usuarios encienden sus dispositivos por primera vez, el dispositivo descarga el perfil de DEP y se inscribe con ese perfil.

  - **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la opción de inscripción con el Asistente de configuración. Si prefiere no restablecer la configuración de fábrica de los dispositivos, use la opción de inscripción directa.

  - **Administrador de inscripción de dispositivos (Intune)**: el administrador de inscripción de dispositivos (DEM) de Intune permite a un administrador inscribir varios dispositivos móviles con una sola cuenta de usuario. Estos dispositivos no pueden tener usuarios dedicados (afinidad de usuario) y, para inscribirlos, la instalación y el inicio de sesión deben realizarse en la aplicación de portal de empresa.

## <a name="how-will-you-manage-dedicated-ios-devices"></a>**¿Cómo se administran los dispositivos iOS dedicados?**

> [!div class="button"]
[DEP de iOS](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Asistente de configuración de iOS](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Etiquetar con IMEI](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  Puede inscribir dispositivos corporativos con usuarios dedicados de las maneras siguientes:

  - **Programa de inscripción de dispositivos (DEP) de Apple**: los dispositivos iOS adquiridos o administrados con DEP se pueden asociar con un perfil de inscripción. Cuando los usuarios encienden sus dispositivos por primera vez, el dispositivo descarga el perfil de DEP y se inscribe con Intune.

  - **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la opción de inscripción con el Asistente de configuración.

  - **Etiquetar con número IMEI**: si se importan los números de identidad de equipo móvil internacional (IMEI) de los dispositivos propiedad de la empresa, estos se pueden etiquetar como dispositivos propiedad de la empresa en Intune. De este modo, los usuarios podrán inscribir sus dispositivos como dispositivos personales instalando el portal de empresa para tener acceso a recursos de la empresa como el correo electrónico, las aplicaciones y los datos.



<!--HONumber=Nov16_HO4-->


