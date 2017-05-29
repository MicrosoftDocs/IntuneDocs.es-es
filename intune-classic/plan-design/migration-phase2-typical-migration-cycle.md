---
title: "Cómo funciona un ciclo de migración típica de Intune | Microsoft Docs"
description: "El propósito de este artículo es explicar el funcionamiento del ciclo de migración de Intune y se ofrecen ejemplos de cómo controla los ciclos de migración el cliente."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 7130d09d7340aba94f3f9ac72743a281e0aa45ca
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="phase-2-typical-migration-cycle"></a>Fase 2: Ciclo de migración típica

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Es habitual que una organización inicie la migración de Intune con un pequeño grupo piloto destinando un subconjunto de sus usuarios del departamento de TI. Además, puede que la organización necesite analizar factores tales como la disposición a cambiar del grupo, el número de usuarios, la complejidad, los requisitos, la ubicación y el riesgo empresarial para ayudar a determinar el intervalo de tiempo de migración.

Aquí tiene un ejemplo de cómo podrían programarse los grupos de destino:

  | **Grupos destinatarios de la migración** | **Período de tiempo 1** | **Período de tiempo 2** | **Período de tiempo 3** | **Período de tiempo 4** | **...**
|:---:|:---:|:---:|:---:|:---:|:---:|
| Org. de TI piloto limitado (50 usuarios) | Anunciar el plan | Dar órdenes de inscripción | Establecer fecha límite | Exigir acceso condicional |  |                                                        
| Org. de TI piloto expandido (200 usuarios) |  | Anunciar el plan | Dar órdenes de inscripción | Establecer fecha límite | Exigir acceso condicional | 
| Fase 1 de la migración: Usuarios con conocimientos técnicos (2000) |  |  | Anunciar el plan | Dar órdenes de inscripción | Establecer fecha límite | 
| Fase 2 de la migración: Este de EE.UU. |  |  |  | Anunciar el plan | Dar órdenes de inscripción | 
| Todas las regiones |  |  |  |  | Anunciar el plan | 

## <a name="customer-migration-case-study"></a>Caso práctico de migración de clientes

### <a name="adatum-corporation"></a>Adatum Corporation

- Consulte [how Adatum Corporation went through the process of migration from a third-party MDM provider to Intune](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0) (Guía de migración de Intune (caso práctico de cliente) Adatum Corporation).

## <a name="monitoring-migration"></a>Supervisión de la migración

Microsoft Intune ofrece varias formas de supervisar la migración:

1.  Vistas de grupo de usuarios de Intune

2.  Conjunto de informes integrados

3.  Alertas en la consola

Debe hacer el seguimiento de cuántos usuarios han inscrito dispositivos después de cada fase para que pueda:

-   Evaluar la eficacia del plan de comunicación.

-   Calcular el impacto de exigir acceso condicional.

Aprender a [supervisar una migración de Intune](/intune-classic/deploy-use/understand-microsoft-intune-operations-by-using-reports).

## <a name="post-migration"></a>tareas posteriores a la migración

Tiene que retirar el proveedor de MDM anterior o cancelar la suscripción del servicio después de migrar a Intune. Además, tiene que quitar los requisitos de infraestructura innecesarios siguiendo las instrucciones del proveedor de MDM.

