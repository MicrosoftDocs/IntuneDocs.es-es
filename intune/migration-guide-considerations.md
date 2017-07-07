---
title: "Consideraciones especiales sobre la migración"
description: "El propósito de este artículo es proporcionar al cliente consideraciones especiales sobre la migración antes de iniciar una campaña de migración."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bc39ffd3a4f11a4c2b32f75dc5befcd8ce42f43e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="special-migration-considerations"></a>Consideraciones especiales sobre la migración

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Hay consideraciones especiales sobre la migración que pueden ser aplicables en función del entorno del proveedor de MDM existente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Restablecimiento de fábrica del Programa de inscripción de dispositivos (DEP) de Apple

El Programa de inscripción de dispositivos (DEP) de Apple establece configuraciones de dispositivo que el usuario final no puede quitar. Para conservar las características de administración avanzada del DEP, el dispositivo debe devolverse al estado original (nuevo) a través del restablecimiento de fábrica al inscribirlo en Intune.

Para seguir usando DEP para administrar los dispositivos en Intune, [configure la inscripción de dispositivos iOS con el Programa de inscripción de dispositivos](/intune/device-enrollment-program-enroll-ios).


## <a name="next-steps"></a>Pasos siguientes 

[Fase 2: Campaña de migración](migration-guide-campaign.md)
