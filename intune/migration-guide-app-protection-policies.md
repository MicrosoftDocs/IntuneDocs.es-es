---
title: Configuración de directivas de protección de aplicaciones durante una migración a Intune
titlesuffix: Microsoft Intune
description: En este artículo se proporcionan los pasos necesarios para configurar directivas de protección de aplicaciones durante una migración de Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cf2ccc9dd8db4457aa5f17738b1f42720735890
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57237000"
---
# <a name="configure-app-protection-policies-optional"></a>Configuración de directivas de protección de aplicaciones (opcional)


Las directivas de protección de aplicaciones le permiten:
* Cifrar aplicaciones
* Definir un PIN cuando se obtiene acceso a la aplicación
* Impedir que las aplicaciones se ejecuten en dispositivos desbloqueados o modificados, así como muchas otras protecciones

Si el teléfono del usuario se ha perdido o robado, puede aplicar selectivamente el borrado de los datos corporativos de forma remota, a la vez que deja intactos los datos personales.

Las directivas de protección de aplicaciones aplican seguridad en el nivel de aplicación y no requieren la inscripción de dispositivos. Se pueden usar con dispositivos inscritos en Intune o no. Además, se pueden aplicar a dispositivos inscritos en un proveedor de MDM externo.

## <a name="app-protection-policies-with-lob-apps"></a>Directivas de protección de aplicaciones con aplicaciones LOB

También puede ampliar las directivas de protección de aplicaciones móviles a las aplicaciones de línea de negocio (LOB) con el [SDK para aplicaciones de Microsoft Intune](app-sdk-get-started.md) o la herramienta de ajuste de aplicaciones de Microsoft Intune para ambas plataformas, iOS y Android. Para más información, vea la [herramienta de ajuste de aplicaciones para iOS](app-wrapper-prepare-ios.md) o la [herramienta de ajuste de aplicaciones para Android](app-wrapper-prepare-android.md). Además, vea [Preparar aplicaciones de línea de negocio para las directivas de protección de aplicaciones](apps-prepare-mobile-application-management.md).

## <a name="how-do-app-protection-policies-help-during-migration"></a>¿Cómo ayudan las directivas de protección de aplicaciones durante la migración?

En una migración, debe quitar los dispositivos del proveedor de MDM antiguo e inscribirlos en Intune. Debe planear esto y animar a los usuarios finales a dejar el proveedor de MDM antiguo e inscribirse inmediatamente en Intune. Pero durante la migración puede haber usuarios que retrasen la finalización del proceso de inscripción y cuyos dispositivos no estén administrados por ningún proveedor de MDM.

Este período puede dejar a su organización más vulnerable al robo de dispositivos y a la pérdida de datos corporativos si todavía se permite el acceso a los recursos corporativos. También puede dar lugar a una reducción de la productividad del usuario si se bloquea el acceso a los recursos corporativos.

Intune puede ofrecer protección de datos corporativos durante la migración para que todavía puede tener cobertura de seguridad para los datos corporativos cuando no hay ninguna administración de nivel de dispositivo.

Cuando deshabilita el acceso condicional en el proveedor de MDM antiguo, los usuarios pueden seguir siendo productivos mientras los incorpora a Intune.

## <a name="task-list-for-app-protection-policies"></a>Lista de tareas para directivas de protección de aplicaciones

1. [Crear una directiva de protección de aplicaciones](app-protection-policies.md#create-an-app-protection-policy)
2. [Implementar una directiva](app-protection-policies.md#deploy-a-policy-to-users)


## <a name="next-steps"></a>Pasos siguientes

[Consideraciones especiales de la migración](migration-guide-considerations.md)
