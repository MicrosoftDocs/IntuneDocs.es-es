---
title: "Consideraciones especiales sobre la migración | Microsoft Docs"
description: "El propósito de este artículo es proporcionar al cliente consideraciones especiales sobre la migración antes de iniciar una campaña de migración."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 7e0adb862d8c60805b3b34406e193df5a93be381
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="phase-1-special-migration-considerations"></a>Fase 1: Consideraciones especiales sobre la migración

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Hay consideraciones especiales sobre la migración que pueden ser aplicables en función del entorno del proveedor de MDM existente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Restablecimiento de fábrica del Programa de inscripción de dispositivos (DEP) de Apple

El Programa de inscripción de dispositivos (DEP) de Apple establece configuraciones de dispositivo que el usuario final no puede quitar. Para conservar las características de administración avanzada del DEP, el dispositivo debe devolverse al estado original (nuevo) a través del restablecimiento de fábrica al inscribirlo en Intune.

Para seguir usando DEP para administrar los dispositivos en Intune:

1.  Incorpore [DEP a Intune](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune).

2.  Vaya a su cuenta DEP de Apple y [reasigne los números de serie del dispositivo de DEP](https://help.apple.com/deployment/business/#/tesf9562af26) del proveedor de MDM existente a Intune.

3.  [Sincronice](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune) su cuenta DEP con Intune.

4.  [Cree y asigne](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune) los perfiles de inscripción de DEP correspondientes a los números de serie en Intune.

5.  Aplique el restablecimiento de fábrica a los dispositivos (de manera remota a través del proveedor de MDM actual o de manera manual en cada dispositivo).

6.  Distribuya los dispositivos a los usuarios finales.

## <a name="next-steps"></a>Pasos siguientes 

[Fase 2: Campaña de migración](/intune-classic/plan-design/migration-phase2-migration-campaign)

