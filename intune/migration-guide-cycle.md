---
title: "Funcionamiento de un ciclo de migración normal de Intune"
description: "En este artículo se explica el funcionamiento del ciclo de migración de Intune y se ofrecen ejemplos de cómo puede controlar los ciclos de migración."
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 69cd071f4e5ac8e1c2cd7543951475a3f74bf808
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="typical-migration-cycle"></a>Ciclo de migración normal

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

Consulte [how Adatum Corporation went through the process of migration from a third-party MDM provider to Intune](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0) (Guía de migración de Intune (caso práctico de cliente) Adatum Corporation).

## <a name="monitoring-migration"></a>Supervisión de la migración

Intune ofrece varias formas de supervisar la migración:

* Vistas de grupo de usuarios de Intune

* Conjunto de informes integrados

* Alertas en la consola

Haga un seguimiento de cuántos usuarios han inscrito dispositivos después de cada fase para que pueda:

-   Evaluar la eficacia del plan de comunicación.

-   Calcular el impacto de exigir acceso condicional.


## <a name="post-migration"></a>Tareas posteriores a la migración

Retire el proveedor de MDM anterior y cancele la suscripción del servicio después de migrar a Intune. Quite también todos los requisitos de infraestructura innecesarios siguiendo las instrucciones del proveedor de MDM.
