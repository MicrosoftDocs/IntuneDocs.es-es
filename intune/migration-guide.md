---
title: "Guía de migración de administración de dispositivos móviles de Intune"
description: "El propósito de esta guía es conducir a los clientes por los diversos detalles implicados en la migración de un proveedor de MDM externo a Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9e86f342413a0f31c51d7a56f862986c433309eb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="intune-migration-guide"></a>Guía de migración de Intune

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

![Ilustración de la guía de migración de Intune](./media/MDM-migration-guide-art.PNG)

Una migración correcta a Intune comienza por un plan sólido que tenga en cuenta el entorno actual de administración de dispositivos móviles (MDM), los objetivos empresariales y los requisitos técnicos. Además, debe contar con las principales partes interesadas que apoyen el plan de migración y colaboren con él.

El propósito de esta guía es conducirle por los diversos detalles implicados en la migración de un proveedor de MDM externo a Intune.

## <a name="whats-included-in-this-guide"></a>¿Qué se incluye en esta guía?

Esta guía incluye dos fases que incluyen tareas, estrategias y orientación táctica que le ayudarán a seguir de principio a fin el proceso de migración a la MDM de Intune.

-   [Fase 1: Preparación de Intune para la administración de dispositivos móviles] (migration-guide-prepare.md)

    -   [Evaluar los requisitos de migración de MDM](migration-guide-prepare.md#assess-mdm-requirements)

    -   [Configuración básica](migration-guide-setup.md)

    -   [Configurar las directivas de administración de dispositivos y aplicaciones](migration-guide-configure-policies.md)

    -   [Configuración de directivas de protección de aplicaciones] (migration-guide-app-protection-policies.md)

    -   [Consideraciones especiales de la migración](migration-guide-considerations.md)

-   [Fase 2: Campaña de migración](migration-guide-campaign.md)

    -   [Plan de comunicación](migration-guide-communication-plan.md)

    -   [Impulsar la adopción de usuarios finales con acceso condicional](migration-guide-drive-adoption.md)
    
    -   [Ciclo de migración típica](migration-guide-cycle.md)
        -   [Supervisión de la migración](migration-guide-cycle.md#monitoring-migration)
        -   [Tareas posteriores a la migración](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>Suposiciones

-   Ya ha evaluado Intune en un entorno de prueba de concepto (PoC) y ha decidido usarlo como la solución MDM de su organización.

-   Ya está familiarizado con Intune y sus características. 

> [!NOTE]
> Consulte la [guía de evaluación de Intune](/intune-classic/understand-explore/sign-up-for-30-day-trial-microsoft-intune) si quiere familiarizarse más con Intune antes de migrar.

## <a name="before-you-begin"></a>Antes de comenzar

Es importante reconocer que la nueva implementación de Intune puede ser diferente de la implementación de MDM antigua. A diferencia de los servicios tradicionales de MDM, Intune se centra en el control de acceso por identidad, por lo que no requiere una aplicación proxy de red para controlar el acceso a los datos corporativos desde dispositivos móviles externos al perímetro de red de la organización. Microsoft ofrece soluciones para proteger los servicios de datos dentro de la propia nube mediante un conjunto de servicios en la nube estrechamente integrados, denominados colectivamente como Enterprise Mobility + Security.

-   Revise las [formas más habituales de usar Intune](migration-guide-prepare.md#assess-mdm-requirements).

## <a name="next-steps"></a>Pasos siguientes

[Fase 1: Preparación de Intune para la administración de dispositivos móviles] (migration-guide-prepare.md)
