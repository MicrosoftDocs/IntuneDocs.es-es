---
title: "Determinar los períodos de tiempo y los grupos de destino de la implementación de Intune | Microsoft Docs"
description: "Este artículo ayuda a determinar los períodos de tiempo y los grupos de destino de una implementación solo en la nube de Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2a970badf5ac18a05115a72dc267ee455ba4628d
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="develop-an-intune-rollout-plan"></a>Desarrollar un plan de implementación de Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Esta sección le ayudará a determinar los grupos de la organización a los que se dirigirá la implementación de Intune, así como el período de tiempo de implementación de cada grupo, y los enfoques de inscripción que se usarán.

## <a name="determine-intune-rollout-targeted-groups-and-timeframes"></a>Determinar los períodos de tiempo y los grupos de destino de implementación de Intune

Es importante identificar primero los grupos a los que se dirigirá con su implementación de Intune. Los grupos de destino se trataron anteriormente en la sección Identificar escenarios de casos de uso de Intune de esta guía.

En segundo lugar, necesitará determinar el período de tiempo al que se destinará cada grupo para la implementación de Intune. Esto requiere normalmente un análisis dentro del equipo de implementación de Intune y con los grupos de destino para determinar el período de tiempo de implementación más apropiado para cada grupo.

Por ejemplo, el equipo de implementación de Intune puede analizar factores como la disposición del grupo al cambio, el número de usuarios y dispositivos, los tipos de plataformas de dispositivos, los requisitos, la ubicación geográfica y el riesgo empresarial para determinar el período de tiempo de implementación.

Normalmente, las organizaciones deciden comenzar la implementación de Intune con un piloto inicial, dirigiéndose a un grupo de usuarios pequeño del departamento de TI. El piloto puede expandirse posteriormente para incluir un conjunto más amplio de usuarios de TI y la participación de otros grupos de la organización. Después de un piloto correcto, las organizaciones están listas para comenzar una implementación de producción completa, dirigiéndose al resto de los grupos de la organización. Algunos ejemplos de diferentes fases y grupos de implementación se proporcionan a continuación:

-   **Piloto:** la primera fase de implementación deben ser usuarios piloto. Los usuarios piloto deben entender que son los primeros usuarios de una nueva solución y deben estar dispuestos a proporcionar comentarios para ayudar a mejorar la configuración, la documentación, las notificaciones, y facilitar el camino a los demás usuarios en fases de implementación posteriores. Estos usuarios no deben ser ejecutivos ni personas VIP.

-   **Departamentos:** cada departamento puede ser una fase de implementación. En este escenario, se dirigirá a un departamento entero a la vez. En este tipo de implementación, cada fase estará usando probablemente el dispositivo móvil de la misma manera y accediendo a las mismas aplicaciones. Además, probablemente los usuarios también tendrán los mismos tipos de directivas.

-   **Geografía:** este tipo de implementación consiste en implementar todos los usuarios de una geografía determinada; ya sea el mismo continente, país, región o el mismo edificio de la empresa. Este tipo de implementación en fases permite centrarse en la ubicación específica de los usuarios. Esto puede permitir un enfoque más [preferencial](#user-assisted-enrollment), ya que se reduce el número de ubicaciones que implementa Intune al mismo tiempo. Como existen posibilidades de que departamentos o casos de uso diferentes se encuentren en la misma ubicación, los casos de uso diferentes deben implementarse al mismo tiempo.

-   **Plataforma:** este tipo de implementación consiste en la implementación de plataformas similares a la vez. Un ejemplo puede ser todos los dispositivos iOS el primer mes, seguidos de Android y, después, de Windows. Este tipo de implementación en fases ayuda a simplificar la asistencia del departamento de soporte técnico. La asistencia del departamento de soporte técnico solo tendrá que proporcionar ayuda a una única plataforma a la vez.

Aquí se muestra un ejemplo de un plan de implementación de Intune que incluye grupos de destino y escalas de tiempo:

| **Fase de implementación** | **Julio** | **Agosto** | **Septiembre** | **Octubre** |
|:---:|:---:|:---:|:---:|:---:|
| Piloto limitado | TI (50 usuarios) |  |  |  |                                                         
| Piloto expandido | TI (200 usuarios), ejecutivos de TI (10 usuarios) |  |  |  |                                                         
| Fase de implementación de producción 1 |  | Ventas y marketing (2000 usuarios) |  |  |
| Fase de implementación de producción 2 |  |  | Venta al por menor (1000 usuarios) |  |
| Fase de implementación de producción 3 |  |  |  | Recursos humanos (50 usuarios), Finanzas (40 usuarios), Ejecutivos (30 usuarios) |

## <a name="determine-the-intune-enrollment-approach"></a>Determinar el enfoque de inscripción de Intune

Ahora que ha determinado los grupos de destino y los períodos de tiempo para la implementación de Intune, el siguiente paso es elegir el enfoque de inscripción de Intune más apropiado para cada grupo. Existen diferentes enfoques de inscripción que las organizaciones pueden usar para su implementación de Intune. Algunos enfoques comunes de inscripción incluyen el autoservicio del usuario, la inscripción asistida de usuario y la feria técnica de TI.

### <a name="user-self-service"></a>Autoservicio del usuario

Con este enfoque, el usuario es responsable de la inscripción de su propio dispositivo, normalmente siguiendo las instrucciones de inscripción que le ha proporcionado su organización de TI. Este enfoque es el que más se usa en las organizaciones y es más escalable que la inscripción asistida de usuario.

### <a name="user-assisted-enrollment"></a>Inscripción asistida de usuario

Este se conoce como enfoque "preferencial", en el que un miembro del equipo de TI ayudaría al usuario en el proceso de inscripción, en persona o a través de Skype. Este enfoque se usa normalmente con personal ejecutivo y otros grupos que puede que necesiten más ayuda durante el proceso de inscripción.

### <a name="it-tech-fair"></a>Feria técnica de TI

Otra opción para la inscripción de usuarios de Intune es tener una feria técnica de TI. En este evento, el grupo de TI creará un área de asistencia de inscripción de Intune donde los usuarios pueden recibir información sobre la inscripción de Intune, realizar preguntas y obtener ayuda con el proceso de inscripción. Aprovechar esta opción puede resultar beneficioso para el grupo de TI y para el usuario, especialmente durante las fases iniciales de la implementación de Intune.

Aquí se muestra un ejemplo de un plan de implementación de Intune con los grupos de destino, las escalas de tiempo y los enfoques de inscripción:

| **Fase de implementación** | **Julio** | **Agosto** | **Septiembre** | **Octubre** |
|:---:|:---:|:---:|:---:|:---:|
| Piloto limitado |  |  |  |  |                                                         
| Autoservicio | TI |  |  |  |
| Piloto expandido |  |  |  |  |                                                         
| Autoservicio | TI |  |  |  |
| Preferencial | Ejecutivos de TI |  |  |  |
| Fase de implementación de producción 1 |  | Ventas, Marketing |  |  |
| Autoservicio |  | Ventas y marketing |  |  |
| Fase de implementación de producción 2 |  |  | Venta directa |  |
| Autoservicio |  |  |  |  |
| Fase de implementación de producción 3 |  |  | Venta directa |  |
| Autoservicio |  |  |  | Recursos humanos, finanzas |
| Preferencial |  |  |  | Ejecutivos |

## <a name="next-section"></a>Sección siguiente

En la sección siguiente se proporcionan instrucciones sobre el [desarrollo de un plan de comunicación de implementación de Intune](section-5-develop-a-rollout-communication-plan.md).

