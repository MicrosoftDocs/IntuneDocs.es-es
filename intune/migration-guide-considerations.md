---
title: "Consideraciones especiales sobre la migración"
description: "En este artículo se proporcionan aspectos especiales sobre la migración que deben considerarse antes de iniciar una campaña de migración."
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 86f3f7f2c8066e1b7b50dfc5931184c394d4f15b
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="special-migration-considerations"></a>Consideraciones especiales sobre la migración

Hay consideraciones especiales sobre la migración que se pueden aplicar en función del entorno del proveedor de MDM existente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Restablecimiento de fábrica del Programa de inscripción de dispositivos (DEP) de Apple

El Programa de inscripción de dispositivos (DEP) de Apple establece configuraciones de dispositivo que el usuario final no puede quitar. Para conservar las características de administración avanzada del DEP, el dispositivo debe devolverse al estado original (nuevo) a través de un restablecimiento de fábrica al inscribirlo en Intune.

Para seguir usando DEP para administrar los dispositivos en Intune, [configure la inscripción de dispositivos iOS con el Programa de inscripción de dispositivos](device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Pasos siguientes

[Fase 2: Campaña de migración](migration-guide-campaign.md)
