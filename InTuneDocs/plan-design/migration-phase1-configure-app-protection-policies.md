---
title: "Configurar directivas de protección de aplicaciones durante una migración de Intune | Microsoft Docs"
description: "El propósito de este artículo es proporcionar los pasos necesarios para configurar directivas de protección de aplicaciones durante una migración de Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 35543604ed68393e859517e32f5186247be001df
ms.lasthandoff: 03/27/2017


---

# <a name="phase-1-configure-app-protection-policies-optional"></a>Fase 1: Configurar directivas de protección de aplicaciones (opcional)

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Las directivas de protección de aplicaciones le permiten cifrar aplicaciones, definir un PIN cuando se accede a la aplicación, bloquear la ejecución de aplicaciones en dispositivos liberados o modificados y muchas otras protecciones. Si el teléfono del usuario se pierde o se roba, puede aplicar selectivamente el borrado remoto de los datos corporativos mientras deja intactos los datos personales mediante la aplicación de directivas de protección de aplicaciones móviles.

Las directivas de protección de aplicaciones aplican seguridad en el nivel de aplicación y no requieren la inscripción de dispositivos. Se pueden usar con dispositivos inscritos en Intune o no. Además, pueden usarse con dispositivos inscritos en un proveedor MDM externo.

## <a name="app-protection-policies-with-lob-apps"></a>Directivas de protección de aplicaciones con aplicaciones LOB

También puede ampliar las directivas de protección de aplicaciones móviles a las aplicaciones de línea de negocio (LOB) aprovechado el [Microsoft Intune App SDK](https://docs.microsoft.com/intune/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management) o la herramienta de ajuste de aplicaciones de Microsoft Intune para ambas plataformas, [IOS](https://www.microsoft.com/en-us/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True) y [Android](https://www.microsoft.com/en-us/download/details.aspx?id=47267).

## <a name="how-do-app-protection-policies-help-during-migration"></a>¿Cómo ayudan las directivas de protección de aplicaciones durante la migración?

La migración requiere quitar dispositivos del proveedor de MDM antiguo e inscribirlos en Intune. Debe planear esto y animar a los usuarios finales a dejar el proveedor de MDM antiguo e inscribirse inmediatamente en Intune. Pero durante la migración puede haber usuarios que retrasen la finalización del proceso de inscripción y cuyos dispositivos no estén administrados por ningún proveedor de MDM.

Este período puede dejar a su organización más vulnerable al robo de dispositivos y la pérdida de datos corporativos si todavía se permite el acceso a los recursos corporativos o llevar a pérdida de productividad de los usuarios si se bloquea el acceso a los recursos corporativos.

Intune puede ofrecer protección de datos corporativos durante la migración para que todavía puede tener cobertura de seguridad para los datos corporativos cuando no hay ninguna administración de nivel de dispositivo.

Cuando deshabilita el acceso condicional en el proveedor de MDM antiguo, los usuarios pueden seguir siendo productivos mientras los incorpora a Intune.

## <a name="task-list-for-app-protection-policies"></a>Lista de tareas para directivas de protección de aplicaciones

-   Tarea 1: Aprender a [prepararse para configurar directivas de protección de aplicaciones móviles](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

-   Tarea 2: Aprender a [crear e implementar directivas de protección de aplicaciones móviles](https://docs.microsoft.com/en-us/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

## <a name="next-steps"></a>Pasos siguientes 

[Fase 1: Consideraciones especiales sobre la migración](https://docs.microsoft.com/intune/plan-design/migration-phase1-special-migration-considerations)

