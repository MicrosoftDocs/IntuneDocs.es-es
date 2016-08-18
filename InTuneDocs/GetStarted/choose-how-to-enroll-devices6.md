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
ms.assetid: 40262e47-1ab4-437d-8ca5-c89b5022f91f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: e1fe6b167b7d46f03472833bc1c3c19030f47bce
ms.openlocfilehash: 38dce11fa7df302bc2dffc3a2352d516c873fedb


---
# Elegir cómo inscribir dispositivos móviles

Las respuestas a la siguiente serie de preguntas le servirán para saber cuál es el mejor método de inscripción de los dispositivos bajo su administración.

## **¿Cómo se administran los dispositivos iOS dedicados?**

  > [!div class="button"]
  [Etiqueta con IMEI >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers) [iOS DEP](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Asistente para la configuración de iOS](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Etiqueta con IMEI](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  Puede inscribir dispositivos corporativos con usuarios dedicados de las maneras siguientes:

  - **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando estos dispositivos se encienden por primera vez, descargan el perfil de DEP y se inscriben con Intune.

  - **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración.

  - **Etiquetar con número IMEI:** si se importan los números de identidad de equipo móvil internacional (IMEI) de los dispositivos de la empresa, estos se pueden etiquetar como dispositivos de la empresa en Intune. De este modo, los usuarios podrán inscribir sus dispositivos como dispositivos personales instalando el portal de empresa para tener acceso a recursos de la empresa como el correo electrónico, las aplicaciones y los datos.

  > [!div class="button"]
  [< Atrás](choose-how-to-enroll-devices3.md)



<!--HONumber=Aug16_HO2-->


