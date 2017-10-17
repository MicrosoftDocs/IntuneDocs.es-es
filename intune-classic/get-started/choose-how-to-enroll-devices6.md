---
title: "Elegir cómo inscribir dispositivos móviles"
description: "Decidir cómo inscribir dispositivos móviles en Intune respondiendo a unas preguntas sencillas"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40262e47-1ab4-437d-8ca5-c89b5022f91f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.custom: intune-classic EXPIERIMENT
ms.openlocfilehash: 364f67222ec44754dcee9fea6475777822a9886e
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="choose-how-to-enroll-mobile-devices"></a>Elegir cómo inscribir dispositivos móviles

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Las respuestas a la siguiente serie de preguntas le servirán para saber cuál es el mejor método de inscripción de los dispositivos bajo su administración.

## <a name="how-will-you-manage-dedicated-corporate-owned-devices"></a>**¿Cómo se administran los dispositivos de empresa dedicados?**

  > [!div class="button"]
[iOS DEP >](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)  
> [!div class="button"]
[Asistente de configuración de iOS >](/intune-classic/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
> [!div class="button"]
[Etiquetar con IMEI >](/intune-classic/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  Puede inscribir dispositivos corporativos con usuarios dedicados de las maneras siguientes:

  - **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando estos dispositivos se encienden por primera vez, descargan el perfil de DEP y se inscriben con Intune.

  - **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración.

  - **Etiquetar con número IMEI:** si se importan los números de identidad de equipo móvil internacional (IMEI) de los dispositivos de la empresa, estos se pueden etiquetar como dispositivos de la empresa en Intune. Esta es la única manera de identificar dispositivos dedicados ("usuario único") de Windows y Android de la empresa. Los dispositivos iOS que no tienen que estar inscritos con el programa de inscripción de dispositivos de Apple o de Apple Configurator también se pueden etiquetar con un número IMEI. Después de la declaración previa del dispositivo, por lo que se etiquetarán como "empresa", puede distribuir los dispositivos a los usuarios. De este modo, los usuarios podrán inscribir sus dispositivos como dispositivos dedicados instalando el portal de empresa para tener acceso a recursos de la empresa como el correo electrónico, las aplicaciones y los datos.

> [!div class="button"]
[< Atrás](choose-how-to-enroll-devices3.md)
