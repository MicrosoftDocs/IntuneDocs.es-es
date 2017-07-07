---
title: "Inicio de una campaña de migración de Intune"
description: "El propósito de este artículo es ofrecer orientación sobre cómo iniciar una campaña de migración."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9690572fd5f17fece0de7b533c98bfc52d77615b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="phase-2-migration-campaign"></a>Fase 2: Campaña de migración

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Las organizaciones deben usar los métodos de migración que sean más adecuados para sus necesidades y ajustar las tácticas de implementación según sus requisitos específicos. El resto de esta guía le equipará con las herramientas que necesita para alcanzar el objetivo de inscribir los dispositivos de los usuarios en Intune.

## <a name="keys-to-a-successful-migration"></a>Claves para una migración correcta

Se trata de importantes lecciones aprendidas al migrar de proveedor de MDM externo a Intune:

-   La comunicación es clave para minimizar el tiempo de inactividad del usuario final y aumentar su satisfacción.

-   Asegúrese de tener instrucciones de migración concretas y específicas.

-   Todos los dispositivos administrados deben cancelar la inscripción del proveedor de MDM existente antes de inscribirse en Intune.

-   Proporcione instrucciones del proveedor de MDM existente a los usuarios finales sobre cómo cancelar la inscripción de sus dispositivos.

-   Use un método por fases. Comience por un pequeño grupo de usuarios piloto y agregue gradualmente otros grupos de usuarios hasta llegar a la implementación a escala completa.

-   Supervise el éxito de la carga del departamento de soporte técnico y de la inscripción de cada ciclo. Deje un margen de tiempo en la programación para asegurarse de que los criterios de éxito se pueden evaluar para cada grupo antes de migrar el siguiente. La implementación piloto debe validar lo siguiente:

    -   Las tasas de éxito y error de inscripción se encuentran dentro de las expectativas.

    -   Productividad del usuario:

        -   Los recursos corporativos, como VPN, Wi-Fi, correo electrónico y certificados, funcionan.

        -   Se puede acceder a las aplicaciones aprovisionadas.

    -   Seguridad de los datos:

        -   Informes de cumplimiento

        -   Protecciones de aplicaciones móviles exigidas

-   Cuando esté satisfecho con la primera fase de migraciones, repita el ciclo de migración (que se describe más adelante en Ciclo de migración típica) para pasar a la siguiente fase.

-   Repita los ciclos por fases hasta que todos los usuarios se hayan migrado a Intune.

-   Asegúrese de que el equipo del departamento de soporte técnico esté preparado para asistir a los usuarios finales durante toda la campaña de migración. Ejecute una migración voluntaria hasta que pueda calcular la carga de trabajo de llamadas de soporte técnico.

-   No establezca fechas límite de inscripción hasta que el departamento de soporte técnico pueda controlar al resto de la población.

> [!IMPORTANT] 
> No configure Intune y la solución MDM externa existente para que apliquen controles de acceso a recursos, como Exchange o SharePoint Online. Además, los dispositivos solo deben inscribirse en una sola solución cada vez.

## <a name="next-steps"></a>Pasos siguientes

[Plan de comunicación](migration-guide-communication-plan.md)
