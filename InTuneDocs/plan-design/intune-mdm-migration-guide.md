---
title: "Guía de migración de administración de dispositivos móviles (MDM) de Intune | Microsoft Docs"
description: "El propósito de esta guía es conducir a los clientes por los diversos detalles implicados en la migración de un proveedor de MDM externo a Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8da2695c4c6dc8b45559323b83a4bb77167303b7
ms.openlocfilehash: 444cb61ea57b92924a681c564a1a913f4204ea89
ms.lasthandoff: 03/28/2017


---

# <a name="intune-migration-guide"></a>Guía de migración de Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

![Ilustración de la guía de migración de Intune](../media/MDM-migration-guide-art.PNG)

Una migración correcta a Intune comienza por un plan sólido que tenga en cuenta el entorno actual de MDM, los objetivos empresariales y los requisitos técnicos. Además, debe contar con las principales partes interesadas que apoyen el plan de migración y colaboren con él.

El propósito de esta guía es conducirle por los diversos detalles implicados en la migración de un proveedor de MDM externo a Intune.

## <a name="whats-included-in-this-guide"></a>¿Qué se incluye en esta guía?

Esta guía incluye dos fases que incluyen tareas, estrategias y orientación táctica que le ayudarán a seguir de principio a fin el proceso de migración a la MDM de Intune.

-   [Fase 1: Preparar Intune para la administración de dispositivos móviles (MDM)](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)

    -   [Evaluar los requisitos de migración de MDM](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements)

    -   [Configuración básica](https://docs.microsoft.com/intune/plan-design/migration-phase1-basic-setup)

    -   [Configurar las directivas de administración de dispositivos y aplicaciones](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-device-and-app-management-policies)

    -   [Configurar directivas de protección de aplicaciones (opcional)](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-app-protection-policies)

    -   [Consideraciones especiales de la migración](https://docs.microsoft.com/intune/plan-design/migration-phase1-special-migration-considerations)

-   [Fase 2: Campaña de migración](https://docs.microsoft.com/intune/plan-design/migration-phase2-migration-campaign)

    -   [Plan de comunicación](https://docs.microsoft.com/intune/plan-design/migration-phase2-communication-plan)

    -   [Impulsar la adopción de usuarios finales con acceso condicional](https://docs.microsoft.com/intune/plan-design/migration-phase2-drive-end-user-adoption-with-conditional-access)
    
    -   [Ciclo de migración típica](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle)
        -   [Supervisión de la migración](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle#monitoring-migration)
        -   [Tareas posteriores a la migración](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle#post-migration)

## <a name="assumptions"></a>Suposiciones

-   Ya ha evaluado Intune en un entorno de prueba de concepto (PoC) y ha decidido usarlo como la solución MDM de su organización.

-   Ya está familiarizado con Intune y sus características. 

> [!NOTE]
> Consulte la [guía de evaluación de Intune](https://docs.microsoft.com/intune/understand-explore/sign-up-for-30-day-trial-microsoft-intune) si quiere familiarizarse más con Intune antes de migrar.

## <a name="before-you-begin"></a>Antes de comenzar

Es importante reconocer que la nueva implementación de Intune puede ser diferente de la implementación de MDM antigua. A diferencia de los servicios tradicionales de MDM, Intune se centra en el control de acceso por identidad, por lo que no requiere una aplicación proxy de red para controlar el acceso a los datos corporativos desde dispositivos móviles externos al perímetro de red de la organización. Microsoft ofrece soluciones para proteger los servicios de datos dentro de la propia nube mediante un conjunto de servicios en la nube estrechamente integrados, denominados colectivamente como Enterprise Mobility + Security.

-   Revise los [usos habituales de Intune](https://docs.microsoft.com/intune/understand-explore/common-ways-to-use-intune) y comience a reunir respuestas a las preguntas que aparecen en la sección [Fase 1: Evaluar los requisitos de MDM](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements).

## <a name="next-steps"></a>Pasos siguientes

[Fase 1: Preparar Intune para la administración de dispositivos móviles (MDM)](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)

