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
ms.assetid: ed9250aa-e894-4eac-92b8-5f1a3748e255
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.custom: intune-classic EXPIERIMENT
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 64f8a051cfa873df034e3d260862181ce637948c
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---
# <a name="choose-how-to-enroll-mobile-devices"></a>Elegir cómo inscribir dispositivos móviles

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Las respuestas a la siguiente serie de preguntas le servirán para saber cuál es el mejor método de inscripción de los dispositivos bajo su administración.

## <a name="how-will-you-manage-shared-ios-devices"></a>**¿Cómo se administran los dispositivos iOS compartidos?**

> [!div class="button"]
Inscripción de DEP de iOS > [!div class="button"]
> Inscripción directa de iOS > [!div class="button"]
Inscripción de DEM >

  - **Programa de inscripción de dispositivos (DEP) de Apple:** los dispositivos iOS adquiridos o administrados con DEP se pueden inscribir con un perfil de inscripción. Cuando esos dispositivos se encienden por primera vez, descargan el perfil de DEP y se inscriben con ese perfil de DEP.

  - **Apple Configurator en un equipo Mac:** Apple Configurator es una aplicación de Apple que se ejecuta en equipos Mac. Los dispositivos iOS se pueden conectar al Mac con un cable USB para instalar un perfil de inscripción en ellos. Si puede restablecer la configuración de fábrica de los dispositivos para inscribirlos, use la inscripción con el Asistente de configuración. Si prefiere no restablecer la configuración de fábrica de los dispositivos, use la inscripción directa.

  - **Administrador de inscripción de dispositivos:** el administrador de inscripción de dispositivos (DEM) de Intune permite a un administrador inscribir varios dispositivos móviles con una sola cuenta de usuario. Estos dispositivos no pueden tener afinidad de usuario (es decir, usuarios dedicados) y, para inscribirlos, la instalación y el inicio de sesión deben realizarse en la aplicación Portal de empresa.

> [!div class="button"]
[< Atrás](choose-how-to-enroll-devices3.md)

