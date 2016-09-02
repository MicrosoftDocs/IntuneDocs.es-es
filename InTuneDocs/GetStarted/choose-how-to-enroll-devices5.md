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
ms.assetid: ed9250aa-e894-4eac-92b8-5f1a3748e255
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: e1fe6b167b7d46f03472833bc1c3c19030f47bce
ms.openlocfilehash: 825392d060229a6b3f3bd3e84ad4be127118aa21


---
# Elegir cómo inscribir dispositivos móviles

Las respuestas a la siguiente serie de preguntas le servirán para saber cuál es el mejor método de inscripción de los dispositivos bajo su administración.


## **¿Cómo se administran los dispositivos iOS compartidos?**

  > [!div class="button"]
  [Inscripción iOS DEP >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Inscripción iOS Direct>](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)  [Inscripción DEM >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando esos dispositivos se encienden por primera vez, descargan el perfil de DEP y se inscriben con ese perfil de DEP.

  - **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración. Si prefiere no restablecer la configuración de fábrica de los dispositivos, use la inscripción directa.

  - **Administrador de inscripción de dispositivos:** el administrador de inscripción de dispositivos (DEM) de Intune permite a un administrador inscribir varios dispositivos móviles con una sola cuenta de usuario. Estos dispositivos no pueden tener afinidad de usuario (es decir, usuarios dedicados) y, para inscribirlos, la instalación y el inicio de sesión deben realizarse en la aplicación Portal de empresa.

  > [!div class="button"]
  [< Atrás](choose-how-to-enroll-devices3.md)



<!--HONumber=Aug16_HO2-->

