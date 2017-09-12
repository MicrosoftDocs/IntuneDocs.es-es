---
title: Mobile Threat Defense con Intune
titleSuffix: Azure portal
description: "Protección del acceso a los recursos de la compañía en función del riesgo del dispositivo"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f9c28bbd06fbee620466d4f269fbb08d98bbcde2
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Integración de Mobile Threat Defense con Intune


Los conectores Intune Mobile Threat Defense le permiten aprovechar el proveedor de Mobile Threat Defense que elija como una fuente de información para las directivas de cumplimiento normativo y las reglas de acceso condicional. Esto permite a los administradores de TI agregar una capa de protección a los recursos corporativos, como Exchange y SharePoint, específicamente desde dispositivos móviles en peligro.

## <a name="what-problem-does-this-solve"></a>¿Qué problema soluciona esto?

Las empresas necesitan proteger datos confidenciales frente a amenazas emergentes que incluyen amenazas físicas, basadas en aplicaciones y basadas en redes, así como frente a vulnerabilidades del sistema operativo.
Históricamente, las empresas han sido proactivas a la hora de proteger PC de los ataques, mientras que los dispositivos móviles no estaban supervisados ni protegidos. Las plataformas móviles cuentan con protección integrada como el aislamiento de aplicaciones y las tiendas de aplicaciones de consumidor seguras, pero estas plataformas siguen siendo vulnerables a ataques sofisticados. Hoy en día, más empleados usan dispositivos para trabajar y necesitan acceso a información confidencial. Los dispositivos necesitan estar protegidos de los ataques sofisticados que cada vez son más frecuentes.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>¿Cómo funcionan los conectores Intune Mobile Threat Defense?

El conector protege los recursos de empresa mediante la creación de un canal de comunicación entre Intune y el proveedor de Mobile Threat Defense que elija. Los socios de Intune Mobile Threat Defense ofrecen aplicaciones intuitivas y fáciles de implementar para dispositivos móviles que exploran y analizan activamente la información sobre amenazas para compartirla con Intune, para fines de elaboración de informes o cumplimiento. Por ejemplo, si una aplicación conectada de Mobile Threat Defense informa al proveedor de Mobile Threat Defense que un teléfono en la red está actualmente conectado a una red que es vulnerable a ataques de tipo "Man-in-the-middle", esta información se comparte y se categoriza en el nivel de riesgo apropiado (bajo, medio o alto), que después se puede comparar con las asignaciones de nivel de riesgo configuradas en Intune para determinar si se debe revocar el acceso a determinados recursos de su elección mientras el dispositivo esté en peligro.

## <a name="sample-scenarios"></a>Escenarios de ejemplo

Cuando un dispositivo se considera infectado por la solución de Mobile Threat Defense:

![Mobile Threat Defense: dispositivo infectado](./media/MTD-image-1.png)

Se concede el acceso cuando se corrige el dispositivo:

![Mobile Threat Defense: acceso concedido](./media/MTD-image-2.png)

## <a name="mobile-threat-defense-partners"></a>Socios de Mobile Threat Defense

Obtenga información sobre cómo proteger el acceso al recurso de la empresa en función del riesgo del dispositivo, la red y la aplicación con:

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Skycure](skycure-mobile-threat-defense-connector.md)
- [SandBlast Mobile de Check Point](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)