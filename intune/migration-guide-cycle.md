---
title: "Funcionamiento de un ciclo de migración normal de Intune"
description: "El propósito de este artículo es explicar el funcionamiento del ciclo de migración de Intune y se ofrecen ejemplos de cómo controla los ciclos de migración el cliente."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 70aa7155e050450a2d786a1f16e42ce2a3c77f9e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="typical-migration-cycle"></a>Ciclo de migración normal

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

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


## <a name="post-migration"></a>tareas posteriores a la migración

Deberá retirar el proveedor de MDM anterior y cancelar la suscripción del servicio después de migrar a Intune. Además, tiene que quitar los requisitos de infraestructura innecesarios siguiendo las instrucciones del proveedor de MDM.
