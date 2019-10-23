---
title: Inicio de una campaña de migración de Intune
titleSuffix: Microsoft Intune
description: En este artículo se proporcionan instrucciones sobre cómo iniciar una campaña de migración de Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 490f2c538a9fd5c10f9812679c9f72fd78fefed5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505356"
---
# <a name="phase-2-migration-campaign"></a>Fase 2: Campaña de migración

Elija un método de migración que sea adecuado para las necesidades de su organización y ajuste las tácticas de implementación en función de sus requisitos específicos. El resto de esta guía le equipará con las herramientas que necesita para alcanzar el objetivo de inscribir los dispositivos de los usuarios en Intune.

## <a name="keys-to-a-successful-migration"></a>Claves para una migración correcta

Estas son las claves para llevar a cabo una migración correcta de un proveedor de MDM externo a Intune:

- Una comunicación clara y útil puede minimizar el descontento y el tiempo de inactividad del usuario final.

- Asegúrese de tener instrucciones de migración concretas y específicas.

- Se debe cancelar la inscripción de todos los dispositivos administrados del proveedor de MDM existente antes de inscribirlos en Intune.

- Proporcione instrucciones del proveedor de MDM existente a los usuarios finales sobre cómo cancelar la inscripción de sus dispositivos.

- Use un método por fases. Comience por un pequeño grupo de usuarios piloto y agregue gradualmente otros grupos de usuarios hasta llegar a la implementación a escala completa.

- Supervise la carga del departamento de soporte técnico y el éxito de la inscripción de cada ciclo. Deje un margen de tiempo en la programación para asegurarse de que los criterios de éxito se pueden evaluar para cada grupo antes de migrar el siguiente. La implementación piloto debe validar lo siguiente:

  - Las tasas de éxito y error de inscripción se encuentran dentro de las expectativas.

  - Productividad del usuario:

    - Los recursos corporativos, como VPN, Wi-Fi, correo electrónico y certificados, funcionan.

    - Se puede obtener acceso a las aplicaciones aprovisionadas.

  - Seguridad de los datos:

    - Se generan informes de cumplimiento.

    - Se aplican protecciones de aplicaciones móviles.

Cuando esté satisfecho con la primera fase de las migraciones, repita el [ciclo de migración](migration-guide-cycle.md) para la siguiente fase.

- Repita los ciclos por fases hasta que todos los usuarios se hayan migrado a Intune.

- Asegúrese de que el equipo del departamento de soporte técnico esté preparado para asistir a los usuarios finales durante toda la campaña de migración. Ejecute una migración voluntaria hasta que pueda calcular la carga de trabajo de llamadas de soporte técnico.

- No establezca fechas límite de inscripción hasta que el departamento de soporte técnico pueda controlar al resto de la población.

> [!IMPORTANT]
> No configure Intune y la solución MDM externa existente para que apliquen controles de acceso a recursos, como Exchange o SharePoint Online. Además, los dispositivos solo deben inscribirse en una sola solución cada vez.

## <a name="next-steps"></a>Pasos siguientes

Cree su [plan de comunicación](migration-guide-communication-plan.md).
