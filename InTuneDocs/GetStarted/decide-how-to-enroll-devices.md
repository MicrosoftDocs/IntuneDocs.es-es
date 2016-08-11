---
title: "Elegir cómo inscribir dispositivos móviles | Microsoft Intune"
description: "Decidir cómo inscribir dispositivos móviles en Intune respondiendo a unas preguntas sencillas"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: c671610b9c56d8b92d126d9902cce9c8c689ed63
ms.openlocfilehash: 9f1612ffd9ab85e38058edb09870297a44b37c16


---

# Elegir cómo inscribir dispositivos móviles

La inscripción de dispositivos móviles es un proceso en el que los smartphones, las tabletas y los equipos se incorporan a la administración de Microsoft Intune. Como administrador, su tarea consiste en averiguar cuál es la mejor forma de inscribir dispositivos a partir de los siguientes aspectos:

 -  Propiedad (personal o de la empresa)
 -  Uso (compartido o personal)
 -  Plataforma (iOS, Android, Windows Phone, PC Windows o PC Mac)

Las respuestas a las siguientes preguntas le servirán para saber cuál es el mejor método de inscripción de los dispositivos bajo su administración.

## **¿Los empleados traen sus propios dispositivos o se los proporciona la organización?**

  - **Dispositivos propiedad de los usuarios** (Bring your own device o "BYOD"): los usuarios pueden instalar la aplicación de portal de empresa de Intune en sus dispositivos y, luego, inscribirlos para obtener acceso a recursos de la empresa, como el correo electrónico, aplicaciones de empresa, datos de la compañía y soporte técnico.  

  - **Dispositivos propiedad de la empresa:** los dispositivos propiedad de la empresa (COD) se pueden inscribir de diversas formas, según cuáles sean las necesidades de la organización y los tipos de dispositivos administrados.

> [!div class="button"]
[Inscripción BYOD >](#what-byod-devices-can-your-users-enroll)   [Inscripción COD >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

## **¿Qué dispositivos BYOD pueden inscribir sus usuarios?**

> [!div class="button"]
[Android](/intune/deploy-use/set-up-android-management-with-microsoft-intune) [iOS y Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 Mobile y Window Phone](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) [equipos PC Windows](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)

## **¿Los dispositivos propiedad de la empresa son compartidos o se destinan a usuarios dedicados?**

- **Dispositivos propiedad de la empresa compartidos:** estos dispositivos no tienen un único usuario y no suelen estar configurados para obtener acceso al correo electrónico. Ejemplos de esto son los dispositivos de pantalla completa o los dispositivos orientados a tareas que los usuarios eligen de un grupo cuando lo necesitan y, luego, lo devuelven. Los métodos de inscripción recomendados dependerán de la plataforma de los dispositivos.

- **Usuarios dedicados:** los dispositivos propiedad de la empresa destinados a usuarios individuales deben someterse a un seguimiento como activos de la empresa y, al mismo tiempo, dejar que los usuarios puedan tener acceso a los datos y al correo electrónico como si se tratara de dispositivos personales. Los métodos de inscripción recomendados dependerán de la plataforma de los dispositivos.

> [!div class="button"]
[Compartido >](#what-operating-system-are-your-shared-devices-running)   [Dedicado >](#how-will-you-manage-dedicated-ios-devices)


## **¿En qué sistema operativo se ejecutan los dispositivos compartidos?**

  > [!div class="button"]
  [Windows >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#how-will-you-manage-shared-ios-devices)

## **¿Cómo se administran los dispositivos iOS compartidos?**

- **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando esos dispositivos se encienden por primera vez, descargan el perfil de DEP y se inscriben con ese perfil de DEP.

- **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración. Si prefiere no restablecer la configuración de fábrica de los dispositivos, use la inscripción directa.

- **Administrador de inscripción de dispositivos:** el administrador de inscripción de dispositivos (DEM) de Intune permite a un administrador inscribir varios dispositivos móviles con una sola cuenta de usuario. Estos dispositivos no pueden tener afinidad de usuario (es decir, usuarios dedicados) y, para inscribirlos, la instalación y el inicio de sesión deben realizarse en la aplicación Portal de empresa.

  > [!div class="button"]
  [Inscripción iOS DEP >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Inscripción iOS Direct>](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)  [Inscripción DEM >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

## **¿Cómo se administran los dispositivos iOS dedicados?**

Puede inscribir dispositivos corporativos con usuarios dedicados de las maneras siguientes:

- **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando estos dispositivos se encienden por primera vez, descargan el perfil de DEP y se inscriben con Intune.

- **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración.

- **Etiquetar con número IMEI:** si se importan los números de identidad de equipo móvil internacional (IMEI) de los dispositivos de la empresa, estos se pueden etiquetar como dispositivos de la empresa en Intune. De este modo, los usuarios podrán inscribir sus dispositivos como dispositivos personales instalando el portal de empresa para tener acceso a recursos de la empresa como el correo electrónico, las aplicaciones y los datos.

  > [!div class="button"]
  [Etiqueta con IMEI >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers) [iOS DEP](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Asistente de configuración de iOS](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Etiqueta con IMEI](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)



<!--HONumber=Aug16_HO1-->


