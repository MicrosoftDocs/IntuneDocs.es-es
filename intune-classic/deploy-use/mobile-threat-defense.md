---
title: Intune Mobile Threat Defense | Microsoft Docs
description: "Proteja el acceso a recursos de la empresa en función del riesgo del dispositivo."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08d87906-8158-4d5e-a49d-ad919efef3d1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 56cd18e1a5556178d951ec47c6e894d8fc2e6f86
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="intune-mobile-threat-defense-connectors"></a>Conectores Intune Mobile Threat Defense

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Los conectores Intune Mobile Threat Defense le permiten aprovechar el proveedor de Mobile Threat Defense que elija como una fuente de información para las directivas de cumplimiento normativo y las reglas de acceso condicional. Esto permite a los administradores de TI agregar una capa de protección a los recursos corporativos, como Exchange y SharePoint, específicamente desde dispositivos móviles en peligro.

## <a name="what-problem-does-this-solve"></a>¿Qué problema soluciona esto?

Las empresas necesitan proteger datos confidenciales frente a amenazas emergentes que incluyen amenazas físicas, basadas en aplicaciones y basadas en redes, así como frente a vulnerabilidades del sistema operativo.
Históricamente, las empresas han sido proactivas a la hora de proteger PC de los ataques, mientras que los dispositivos móviles no estaban supervisados ni protegidos. Las plataformas móviles cuentan con protección integrada como el aislamiento de aplicaciones y las tiendas de aplicaciones de consumidor seguras, pero estas plataformas siguen siendo vulnerables a ataques sofisticados. Hoy en día, más empleados usan dispositivos para trabajar y necesitan acceso a información confidencial. Los dispositivos necesitan estar protegidos de los ataques sofisticados que cada vez son más frecuentes.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>¿Cómo funcionan los conectores Intune Mobile Threat Defense?

El conector protege los recursos de empresa mediante la creación de un canal de comunicación entre Intune y el proveedor de Mobile Threat Defense que elija. Los socios de Intune Mobile Threat Defense ofrecen aplicaciones intuitivas y fáciles de implementar para dispositivos móviles que exploran y analizan activamente la información sobre amenazas para compartirla con Intune, para fines de elaboración de informes o cumplimiento. Por ejemplo, si una aplicación conectada de Mobile Threat Defense informa al proveedor de Mobile Threat Defense que un teléfono en la red está actualmente conectado a una red que es vulnerable a ataques de tipo "Man-in-the-middle", esta información se comparte y se categoriza en el nivel de riesgo apropiado (bajo, medio o alto), que después se puede comparar con las asignaciones de nivel de riesgo configuradas en Intune para determinar si se debe revocar el acceso a determinados recursos de su elección mientras el dispositivo esté en peligro.

## <a name="sample-scenarios"></a>Escenarios de ejemplo

Cuando un dispositivo se considera infectado por la solución de Mobile Threat Defense:

![Mobile Threat Defense: dispositivo infectado](../media/mtp/MTD-image-1.png)

Se concede el acceso cuando se corrige el dispositivo:

![Mobile Threat Defense: acceso concedido](../media/mtp/MTD-image-2.png)

## <a name="mobile-threat-defense-partners"></a>Socios de Mobile Threat Defense

Obtenga información sobre cómo proteger el acceso al recurso de la empresa en función del riesgo del dispositivo, la red y la aplicación con:

- [Lookout](/intune-classic/deploy-use/lookout-mobile-threat-defense-connector)
- [Skycure](/intune-classic/deploy-use/skycure-mobile-threat-defense-connector)

