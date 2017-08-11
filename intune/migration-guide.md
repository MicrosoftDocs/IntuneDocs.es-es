---
title: "Guía de migración de administración de dispositivos móviles de Intune"
description: "Esta guía le conduce por los diversos detalles implicados en la migración de un proveedor de MDM externo a Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: d86260872230bb0a9274fa302acac5caeaa682a7
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="intune-migration-guide"></a>Guía de migración de Intune

![Ilustración de la guía de migración de Intune](./media/MDM-migration-guide-art.PNG)

Una migración correcta a Intune comienza por un plan sólido que tenga en cuenta su entorno actual de administración de dispositivos móviles (MDM), los objetivos empresariales y los requisitos técnicos. Además, debe contar con las principales partes interesadas que apoyen el plan de migración y colaboren con él.

Esta guía le conduce por los diversos detalles implicados en la migración de un proveedor de MDM externo a Intune.

## <a name="whats-included-in-this-guide"></a>¿Qué se incluye en esta guía?

Esta guía desglosa la migración en dos fases que incluyen tareas, estrategias y orientación táctica que le ayudarán a seguir de principio a fin el proceso de migración a la MDM de Intune.

-   [Fase 1: Preparar Intune para la administración de dispositivos móviles](migration-guide-prepare.md)

    -   [Evaluar los requisitos de migración de MDM](migration-guide-prepare.md#assess-mdm-requirements)

    -   [Configuración básica](migration-guide-setup.md)

    -   [Configurar las directivas de administración de dispositivos y aplicaciones](migration-guide-configure-policies.md)

    -   [Configurar las directivas de protección de aplicaciones](migration-guide-app-protection-policies.md)

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

## <a name="before-you-begin"></a>Antes de comenzar

Es importante reconocer que la nueva implementación de Intune puede ser diferente de la implementación de MDM antigua. A diferencia de los servicios tradicionales de MDM, Intune se centra en el control de acceso por identidad, por lo que no requiere una aplicación proxy de red para controlar el acceso a los datos corporativos desde dispositivos móviles externos al perímetro de red de la organización. Microsoft ofrece soluciones para proteger los servicios de datos dentro de la propia nube mediante un conjunto de servicios en la nube estrechamente integrados, denominados colectivamente como Enterprise Mobility + Security.

-   Revise las [formas más habituales de usar Intune](common-scenarios.md).

## <a name="next-steps"></a>Pasos siguientes

[Fase 1: Preparar Intune para la administración de dispositivos móviles](migration-guide-prepare.md)
