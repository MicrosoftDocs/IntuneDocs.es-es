---
title: "Elegir cómo inscribir dispositivos móviles | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 364064f3507c00f87b367c0aa4ff7b0f31cea4b7
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---
# <a name="choose-how-to-enroll-mobile-devices"></a>Elegir cómo inscribir dispositivos móviles

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Las respuestas a la siguiente serie de preguntas le servirán para saber cuál es el mejor método de inscripción de los dispositivos bajo su administración.

## <a name="how-will-you-manage-dedicated-corporate-owned-devices"></a>**¿Cómo se administran los dispositivos de empresa dedicados?**

  > [!div class="button"]
DEP de iOS >  
> [!div class="button"]
Asistente de configuración de iOS > [!div class="button"]
> Etiquetado con IMEI >

  Puede inscribir dispositivos corporativos con usuarios dedicados de las maneras siguientes:

  - **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando estos dispositivos se encienden por primera vez, descargan el perfil de DEP y se inscriben con Intune.

  - **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración.

  - **Etiquetar con número IMEI:** si se importan los números de identidad de equipo móvil internacional (IMEI) de los dispositivos de la empresa, estos se pueden etiquetar como dispositivos de la empresa en Intune. Esta es la única manera de identificar dispositivos dedicados ("usuario único") de Windows y Android de la empresa. Los dispositivos iOS que no tienen que estar inscritos con el programa de inscripción de dispositivos de Apple o de Apple Configurator también se pueden etiquetar con un número IMEI. Después de la declaración previa del dispositivo, por lo que se etiquetarán como "empresa", puede distribuir los dispositivos a los usuarios. De este modo, los usuarios podrán inscribir sus dispositivos como dispositivos dedicados instalando el portal de empresa para tener acceso a recursos de la empresa como el correo electrónico, las aplicaciones y los datos.

> [!div class="button"]
[< Atrás](choose-how-to-enroll-devices3.md)

