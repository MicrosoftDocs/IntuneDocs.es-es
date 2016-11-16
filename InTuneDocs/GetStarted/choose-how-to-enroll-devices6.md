---
title: "Elegir cómo inscribir dispositivos móviles | Microsoft Intune"
description: "Decidir cómo inscribir dispositivos móviles en Intune respondiendo a unas preguntas sencillas"
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 55377981cfcf1f7c9a0de7c9dbcd8fc80417d1e2


---
# Elegir cómo inscribir dispositivos móviles

Las respuestas a la siguiente serie de preguntas le servirán para saber cuál es el mejor método de inscripción de los dispositivos bajo su administración.

## **¿Cómo se administran los dispositivos dedicados y de la empresa?**

  > [!div class="button"]
[iOS DEP >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune)  
> [!div class="button"]
[Asistente de configuración de iOS >](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
> [!div class="button"]
[Etiquetar con IMEI >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  Puede inscribir dispositivos corporativos con usuarios dedicados de las maneras siguientes:

  - **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando estos dispositivos se encienden por primera vez, descargan el perfil de DEP y se inscriben con Intune.

  - **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración.

  - **Etiquetar con número IMEI:** si se importan los números de identidad de equipo móvil internacional (IMEI) de los dispositivos de la empresa, estos se pueden etiquetar como dispositivos de la empresa en Intune. Esta es la única manera de identificar dispositivos dedicados ("usuario único") de Windows y Android de la empresa. Los dispositivos iOS que no tienen que estar inscritos con el programa de inscripción de dispositivos de Apple o de Apple Configurator también se pueden etiquetar con un número IMEI. Después de la declaración previa del dispositivo, por lo que se etiquetarán como "empresa", puede distribuir los dispositivos a los usuarios. De este modo, los usuarios podrán inscribir sus dispositivos como dispositivos dedicados instalando el portal de empresa para tener acceso a recursos de la empresa como el correo electrónico, las aplicaciones y los datos.

  > [!div class="button"]
  [< Atrás](choose-how-to-enroll-devices3.md)



<!--HONumber=Oct16_HO4-->


