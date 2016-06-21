---
# required metadata

title: Implementación de aplicaciones | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0fc32ed3-bcf4-472a-80e7-eb20986f78fa

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Implementación de aplicaciones
En este tema se proporcionan recomendaciones concretas para implementar aplicaciones por fases en Microsoft Intune. Para obtener información general sobre las fases de implementación, vea [Rollout phases for Microsoft Intune deployment](rollout-phases-for-microsoft-intune-deployment.md) (Fases de implementación de Microsoft Intune)..

### Fases de implementación de una aplicación
Las fases de implementación de una aplicación son las siguientes:

-   Ámbito del proyecto

-   Prueba de concepto

-   Fase piloto

-   Implementación empresarial

-   Operaciones y mantenimiento

## Ámbito del proyecto
Tenga en cuenta lo siguiente:

-   La tarea de usuario que la aplicación está destinada a habilitar.

-   La idoneidad de la aplicación para los usuarios y sus dispositivos (todos los sistemas operativos que se van a poder usar).

-   Compruebe que el instalador de la aplicación seleccionado sea compatible con la distribución de aplicaciones de Intune, según se describe en [Agregar aplicaciones con Microsoft Intune](/intune/deploy-use/add-apps)..

-   Procure tener instalados los requisitos previos de distribución de aplicaciones. <!---, as described in [Plan for app deployment in Microsoft Intune](plan-for-app-deployment-in-microsoft-intune.md--->).

-   Determine que el tipo de aplicación es compatible con Intune.

-   Compruebe que tiene suficiente espacio de almacenamiento en nube disponible para cargar la aplicación. En [Agregar aplicaciones con Microsoft Intune](/intune/deploy-use/add-apps) encontrará instrucciones para adquirir más almacenamiento..

## Prueba de concepto
En la fase de prueba de concepto, pruebe la implementación de la aplicación en un entorno de laboratorio en dispositivos y usuarios que haya configurado estrictamente con fines de prueba.

-   Involucre al departamento de soporte técnico en esta fase para saber qué problemas pueden surgir durante la fase piloto y la implementación de producción. Hay información sobre solución de problemas disponible en [Troubleshoot app deployment problems in Microsoft Intune](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune) (Solucionar problemas de implementación de aplicaciones en Microsoft Intune)..

-   En este punto del proceso, se aconseja desarrollar planes de comunicación dirigidos a los usuarios de la fase piloto y la de producción. Como mínimo, este plan debe contemplar qué aplicación se va a implementar, cómo y cuándo podrán obtenerla los usuarios, el propósito empresarial de la implementación y, también, qué hacer si los usuarios o el personal de TI detectan problemas (tanto información de autoayuda como la forma de ponerse en contacto con el departamento de soporte técnico).

## Fase piloto
Durante la fase piloto, la aplicación se implementará en un grupo reducido de dispositivos y usuarios de prueba. Tenga en cuenta lo siguiente:

-   Asegúrese de que el grupo de prueba sea representativo de los usuarios y dispositivos que van a usar la aplicación tras la fase de producción.

-   Forme al departamento de soporte técnico en la implementación de la aplicación y asegúrese de que estén preparados para ayudar a los usuarios del grupo de prueba.

-   Elija usuarios de prueba que hagan un uso típico de la aplicación y que notifiquen de forma confiable las posibles incidencias a los administradores de la fase piloto.

-   Active el plan de comunicación de usuarios de la fase piloto.

## Implementación empresarial

-   Emplee los resultados de la fase piloto para ajustar la implementación empresarial.

-   Avise al departamento de soporte técnico de la programación de la implementación de la aplicación. Disponga de mecanismos para responder a las solicitudes de ayuda y para ajustar la implementación según sea necesario.

-   Esté preparado para solucionar problemas de la implementación, si surge alguno.

-   Active el plan de comunicación de usuarios de producción.

-   Use un método por fases para implementar la aplicación, agregando grupos de forma incremental para garantizar que la implementación se desarrolla sin problemas.

## Operaciones y mantenimiento
**Operaciones:** consulte la consola de Intune para ver las alertas y los problemas de usuarios o dispositivos y para comprobar que la distribución de la aplicación va según lo diseñado.

**Departamento de soporte técnico:** asegúrese de que el departamento de soporte técnico está al tanto de los cambios en la disponibilidad de la aplicación que puedan dar lugar a solicitudes de soporte técnico.

### Consulte también
[Implementación de aplicaciones](/intune/deploy-use/deploy-apps)

[Solucionar problemas de implementación de aplicaciones en Microsoft Intune](/intune/troubleshoot/troubleshoot-app-deployment-problems-in-microsoft-intune)


<!--HONumber=May16_HO1-->


