---
title: "Implementación de directivas | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 390d5adf-86d2-4e23-ba93-1e61e6b1028b
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d82d0ae4820d2e2141848235b8741abccaec3bc6
ms.openlocfilehash: 8935fbc42d7b406a5bcdbfc4353209b4447ae413


---

# Implementación de directivas
En este tema se proporcionan recomendaciones concretas para una implementación de directivas por fases en Microsoft Intune. Este método se aplica a las primeras directivas aplicadas a una nueva implementación de Intune o a las directivas agregadas a una implementación existente.

Para obtener información general sobre las fases de implementación, vea [Fases de implementación para Microsoft Intune](rollout-phases-for-microsoft-intune-deployment.md).

### Fases de implementación de directivas
Las fases de implementación de directivas son:

-   Ámbito del proyecto

-   Prueba de concepto

-   Fase piloto

-   Implementación empresarial

-   Operaciones y mantenimiento

## Ámbito del proyecto
Defina el ámbito de la implementación de directivas de Intune:

-   Si se trata de una nueva implementación, deberá definir todos los comportamientos de dispositivo que quiera y los requisitos de seguridad que desee crear con el conjunto de directivas.

-   Decida a qué usuarios y dispositivos se van a aplicar estas directivas.

-   Diseñe los grupos de usuarios y dispositivos para poder aplicar las nuevas directivas de forma adecuada.

-   Determine si existen limitaciones o requisitos asociados con cada sistema operativo que afecten a las intenciones de la directiva.

-   Tenga en cuenta los aspectos de diseño de la directiva, como su tipo y la plantilla que se usará.

-   Tanto si está publicando su primer conjunto de directivas como si está agregando nuevas directivas a un conjunto de directivas existente, tenga en cuenta cómo interactúan las distintas directivas y cuál será el comportamiento probable del dispositivo. Durante la fase de piloto se pueden detectar los problemas de interacciones y conflictos de directivas, aunque su detección en la planificación inicial simplificará la ejecución del piloto.

## Prueba de concepto
En la fase de prueba de concepto, pruebe la implementación de directivas en un entorno de laboratorio en dispositivos y usuarios que haya configurado estrictamente con fines de prueba.

-   Involucre al departamento de soporte técnico en esta fase para conocer qué problemas pueden surgir durante la fase piloto y la implementación de producción. Hay información sobre solución de problemas disponible en [Directivas de solución de problemas en Microsoft Intune](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune).

-   En este punto del proceso, debe desarrollar planes de comunicación para los usuarios de la fase piloto y la de producción. Como mínimo, el plan debe incluir los comportamientos de dispositivo que cambiarán y en qué momento lo harán, el propósito empresarial del cambio y qué hacer si los usuarios o el personal de TI detectan problemas (tanto información de autoayuda como la forma de ponerse en contacto con el departamento de soporte técnico).

## Piloto
Durante el piloto, se implementará la directiva en un grupo reducido de dispositivos y usuarios de prueba. Existen consideraciones específicas para las directivas de piloto en Intune:

-   El grupo de prueba debe ser representativo del grupo al que se aplicará la directiva para la implementación de producción.

-   Enseñe al departamento de soporte técnico los cambios en las directivas y asegúrese de que estén preparados para ayudar a los usuarios del grupo de prueba.

-   Active el plan de comunicación de usuarios piloto.

-   El piloto puede realizarse primero en modo aislado, donde el dispositivo no esté sujeto a otras directivas que puedan causar conflictos y comportamientos no deseados.

-   La prueba final debe tener en cuenta la nueva directiva y todas las directivas existentes que se aplicarán al mismo dispositivo.

## Implementación empresarial

-   Basándose en los resultados del piloto, ajuste la directiva planeada para corregir los conflictos de directivas y los comportamientos inesperados.

-   Notifique al departamento de soporte técnico la programación de la implementación empresarial. Debe disponer de mecanismos para responder a las solicitudes de ayuda y para ajustar la implementación según sea necesario.

-   Debe estar listo para solucionar los problemas de la directiva, en caso de que surja alguno.

-   Active el plan de comunicación de usuarios de producción.

-   Aplique las directivas de forma incremental a otros grupos, a la vez que supervisa el estado de la directiva para los dispositivos afectados y sigue las solicitudes del departamento de soporte técnico que puedan estar relacionadas con la nueva directiva.

## Operaciones y mantenimiento
**Operaciones:** supervise la consola de Intune para detectar las alertas y los problemas de usuarios o dispositivos y compruebe que las directivas funcionen según su diseño.

**Departamento de soporte técnico:** asegúrese de que el departamento de soporte técnico sea consciente de los cambios en las directivas que afecten a la experiencia del usuario, ya que pueden dar lugar a solicitudes de soporte técnico.


### Consulte también
[Get ready to configure mobile app management policies with Microsoft Intune (Preparación para configurar directivas de administración de aplicaciones móviles con Microsoft Intune)](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

[Directivas de solución de problemas en Microsoft Intune](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune)



<!--HONumber=Jun16_HO4-->


