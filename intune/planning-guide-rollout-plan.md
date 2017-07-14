---
title: "Determinación de grupos de destino para lanzamientos y de períodos de tiempo"
description: "En este artículo se ofrece ayuda para decidir qué grupos implementar en Intune y los períodos de tiempo para tales implementaciones."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9dda530be47b5449a9c1ed610d8e409fd62148d7
ms.sourcegitcommit: ce363409d1206e4a3d669709863ccc9eb22b7d5f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2017
---
# Desarrollo de un plan de lanzamiento
<a id="develop-a-rollout-plan" class="xliff"></a>

En el plan de lanzamiento se identifican los grupos de la organización a los que destinar el lanzamiento de Intune, el período de tiempo de lanzamiento para cada grupo y el método de inscripción que se usará.

## Grupos de destino y períodos de tiempo
<a id="targeted-groups-and-timeframes" class="xliff"></a>

En primer lugar, revise los grupos de destino del lanzamiento de Intune identificados en los [escenarios de casos de uso](planning-guide-scenarios.md).

En segundo lugar, determine el período de tiempo para cada grupo de destino. Esta tarea suele requerir una discusión entre el equipo de implementación de Intune y los grupos de destino para determinar el período de tiempo de lanzamiento más apropiado para cada grupo. Los puntos que se deben tratar en tal discusión incluyen:
* Disposición del grupo a los cambios
* El número de usuarios y dispositivos
* Tipos de plataformas de dispositivos
* Requisitos
* Ubicación geográfica
* Riesgo empresarial

## Fases de implementación
<a id="rollout-phases" class="xliff"></a>
Normalmente, las organizaciones deciden comenzar la implementación de Intune con un piloto inicial, dirigiéndose a un grupo de usuarios pequeño del departamento de TI. El piloto puede expandirse para incluir un conjunto más amplio de usuarios de TI y, además, puede englobar la participación de otros grupos de la organización.

### Fase piloto
<a id="pilot" class="xliff"></a>
La primera fase del lanzamiento debe estar destinada a usuarios piloto. Estos deben saber que son los primeros usuarios de una solución nueva. Además, deben estar dispuestos a proporcionar comentarios para ayudar a mejorar la configuración, la documentación, las notificaciones, y facilitar el camino a los demás usuarios en fases de lanzamiento posteriores. Estos usuarios no deben ser ejecutivos ni personas VIP.

La fase piloto es una buena oportunidad para probar los [desafíos](planning-guide-deployment-goals.md) y restringir los [requisitos](planning-guide-requirements.md) que recopiló anteriormente.

Incluya el plan de [comunicación](planning-guide-communication-plan.md), el plan de [soporte técnico](planning-guide-support-plan.md) y las [pruebas y la validación](planning-guide-test-validation.md) para solucionar cualquier problema mientras el impacto en los usuarios todavía es de menor importancia.

### Lanzamiento en producción
<a id="production-rollout" class="xliff"></a>
Tras una fase piloto satisfactoria, ya puede iniciar un lanzamiento completo en producción, destinado al resto de los grupos de la organización. Algunos ejemplos de grupos y fases de lanzamiento distintos son:

-   **Departamentos** <br/>Cada departamento puede ser una fase de lanzamiento. Puede centrarse en un departamento completo a la vez. En este tipo de lanzamiento, los usuarios de cada departamento tienden a usar el dispositivo móvil de la misma forma y acceden a las mismas aplicaciones. Los usuarios probablemente tendrán los mismos tipos de directivas.

-   **Geografía** <br/>Con este método, la implementación está destinada a todos los usuarios de una geografía determinada; ya sea el mismo continente, país, región o el mismo edificio de la empresa. Este tipo de implementación por fases permite centrarse en la ubicación específica de los usuarios. Esto puede permitir un enfoque más [preferencial](#user-assisted-enrollment), ya que se reduce el número de ubicaciones que implementa Intune al mismo tiempo. Como existen posibilidades de que departamentos o casos de uso diferentes se encuentren en la misma ubicación, los casos de uso diferentes deben implementarse al mismo tiempo.

-   **Plataforma** <br/>Este tipo de implementación consiste en la implementación de plataformas similares a la vez. Un ejemplo puede ser todos los dispositivos iOS el primer mes, seguidos de Android y, después, de Windows. Este tipo de implementación por fases permite simplificar el soporte técnico porque el departamento competente en este ámbito solo tendría que prestar asistencia en una única plataforma a la vez.

Aquí se muestra un ejemplo de un plan de implementación de Intune que incluye grupos de destino y escalas de tiempo:

| **Fase de implementación** | **Julio** | **Agosto** | **Septiembre** | **Octubre** |
|:---:|:---:|:---:|:---:|:---:|
| Piloto limitado | TI (50 usuarios) |  |  |  |                                                         
| Piloto expandido | TI (200 usuarios), ejecutivos de TI (10 usuarios) |  |  |  |                                                         
| Fase de implementación de producción 1 |  | Ventas y marketing (2000 usuarios) |  |  |
| Fase de implementación de producción 2 |  |  | Venta al por menor (1000 usuarios) |  |
| Fase de implementación de producción 3 |  |  |  | Recursos humanos (50 usuarios), Finanzas (40 usuarios), Ejecutivos (30 usuarios) |

Puede [descargar una plantilla de la tabla anterior](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para especificar las fases de lanzamiento de la organización.
## Correspondencia de los grupos de lanzamiento con los métodos de inscripción
<a id="match-rollout-groups-to-enrollment-approaches" class="xliff"></a>

Ahora que ha determinado los grupos de destino y los períodos de tiempo para el lanzamiento de Intune, el siguiente paso consiste en elegir el método de inscripción de Intune más apropiado para cada grupo. Puede usar distintos métodos de inscripción, entre ellos:
* Autoservicio del usuario
* Inscripción asistida de usuario
* Feria técnica de TI

### Autoservicio del usuario
<a id="user-self-service" class="xliff"></a>

En este caso, el usuario es responsable de la inscripción de su propio dispositivo, normalmente siguiendo las instrucciones de inscripción que le ha proporcionado su organización de TI. Este método es el que más se usa en las organizaciones y es más escalable que la inscripción asistida por el usuario.

### Inscripción asistida por el usuario
<a id="user-assisted-enrollment" class="xliff"></a>

Se conoce como un método "preferencial". Un miembro del equipo de TI ayuda al usuario durante el proceso de inscripción, en persona o con Skype. Este método se usa normalmente con personal ejecutivo y otros grupos que pueden necesitar más ayuda durante el proceso de inscripción.

### Feria técnica de TI
<a id="it-tech-fair" class="xliff"></a>

Otra opción para la inscripción de usuarios de Intune es tener una feria técnica de TI. En este evento, el grupo de TI configura un área de asistencia de inscripción de Intune donde los usuarios pueden recibir información sobre la inscripción de Intune, realizar preguntas y obtener ayuda con el proceso de inscripción. Esta opción puede resultar beneficiosa para los usuarios y grupos de TI, sobre todo, durante las primeras fases del lanzamiento de Intune.

A continuación se muestra un ejemplo actualizado del plan de lanzamiento de Intune anterior para incluir los métodos de inscripción:

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

## Pasos siguientes
<a id="next-steps" class="xliff"></a>

En la sección siguiente se proporcionan instrucciones sobre el [desarrollo de un plan de comunicación de implementación de Intune](planning-guide-communication-plan.md).
