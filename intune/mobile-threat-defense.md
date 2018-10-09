---
title: Mobile Threat Defense con Microsoft Intune
titleSuffix: ''
description: Use Mobile Threat Defense (MTD) con su asociado de defensa contra las amenazas móviles para proteger el acceso a recursos de empresa en función del riesgo del dispositivo.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b94b4014fdf8226696f1979b87d730d2f4cccd1c
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231543"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>¿Qué es la integración de Mobile Threat Defense con Intune?


Los conectores Intune Mobile Threat Defense le permiten aprovechar el proveedor de Mobile Threat Defense que elija como una fuente de información para las directivas de cumplimiento normativo y las reglas de acceso condicional. Esto permite a los administradores de TI agregar una capa de protección a los recursos corporativos, como Exchange y SharePoint, específicamente desde dispositivos móviles que están en peligro.

## <a name="what-problem-does-this-solve"></a>¿Qué problema soluciona esto?

Las empresas necesitan proteger datos confidenciales frente a amenazas emergentes que incluyen amenazas físicas, basadas en aplicaciones y basadas en redes, así como frente a vulnerabilidades del sistema operativo.

Históricamente, las empresas han sido proactivas a la hora de proteger PC de los ataques, mientras que los dispositivos móviles no estaban supervisados ni protegidos. Las plataformas móviles cuentan con protección integrada como el aislamiento de aplicaciones y las tiendas de aplicaciones de consumidor seguras, pero estas plataformas siguen siendo vulnerables a ataques sofisticados. Hoy en día, más empleados usan dispositivos para trabajar y necesitan acceso a información confidencial. Los dispositivos deben estar protegidos ante los ataques cada vez más sofisticados.

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>¿Cómo funcionan los conectores de Intune Mobile Threat Defense?

El conector protege los recursos de empresa mediante la creación de un canal de comunicación entre Intune y el proveedor de Mobile Threat Defense que elija. Los socios de Intune Mobile Threat Defense ofrecen aplicaciones intuitivas y fáciles de implementar para dispositivos móviles que exploran y analizan activamente la información sobre amenazas para compartirla con Intune y para fines de elaboración de informes o cumplimiento. 

Por ejemplo, si una aplicación conectada de Mobile Threat Defense informa al proveedor de Mobile Threat Defense de que un teléfono de la red está actualmente conectado a una red que es vulnerable a ataques de tipo "Man-in-the-middle", esta información se comparte y se categoriza en el nivel de riesgo apropiado (bajo, medio o alto), que después se puede comparar con las asignaciones de nivel de riesgo configuradas en Intune para determinar si se debe revocar el acceso a determinados recursos de su elección mientras el dispositivo esté en peligro.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>¿Qué datos recopila Intune para Mobile Threat Defense?

Si está activado, Intune recopila la información de inventario de aplicaciones de los dispositivos personales y corporativos, y la pone a disposición de los proveedores de Mobile Threat Defense (MTD), como Lookout for Work. Puede recopilar un inventario de aplicaciones de los usuarios de dispositivos iOS.

Este servicio es de suscripción, y no se comparte información de inventario de la aplicación de forma predeterminada. Un administrador de Intune debe habilitar la sincronización de aplicaciones para dispositivos iOS en la configuración del servicio antes de compartir cualquier información de inventario de la aplicación.

**Inventario de aplicaciones**  
Si activa la sincronización de aplicaciones para dispositivos iOS, los inventarios de los dispositivos iOS, tanto de empresa como personales, se envían al proveedor de servicios MTD. El inventario de aplicaciones incluye los datos siguientes:

 - Identificador de la aplicación
 - Versión de la aplicación
 - Nombre corto de la versión
 - Nombre de la aplicación
 - Tamaño del lote de aplicaciones
 - Tamaño dinámico de la aplicación
 - Independientemente de si la aplicación está validada o no
 - Independientemente de si la aplicación está administrada o no

## <a name="sample-scenarios"></a>Escenarios de ejemplo

Cuando un dispositivo se considera infectado por la solución de Mobile Threat Defense:

![Imagen en que se muestra un dispositivo de Mobile Threat Defense infectado](./media/MTD-image-1.png)

Se concede el acceso cuando se corrige el dispositivo:

![Imagen en que se muestra un acceso concedido por Mobile Threat Defense](./media/MTD-image-2.png)

> [!NOTE] 
> No se admite el uso de varios proveedores de Mobile Threat Defense con Intune. Si tiene varias herramientas de MTD habilitadas, se forzará la instalación de todas las aplicaciones de MTD y un análisis en todos los dispositivos en busca de amenazas.

## <a name="mobile-threat-defense-partners"></a>Socios de Mobile Threat Defense

Obtenga información sobre cómo proteger el acceso al recurso de la empresa en función del riesgo del dispositivo, la red y la aplicación con:

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [SandBlast Mobile de Check Point](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
