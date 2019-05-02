---
title: Mobile Threat Defense con Microsoft Intune
titleSuffix: Microsoft Intune
description: Use Mobile Threat Defense (MTD) con su asociado de defensa contra las amenazas móviles para proteger el acceso a recursos de empresa en función del riesgo del dispositivo.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/20/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e364ad88591b8ecc945702659255d9378723624f
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513041"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>¿Qué es la integración de Mobile Threat Defense con Intune?
Intune puede integrar datos de un proveedor de Mobile Threat Defense como una fuente de información para directivas de cumplimiento y reglas de acceso condicional. Puede usar esta información para proteger mejor los recursos corporativos, como Exchange y SharePoint, bloqueando el acceso de dispositivos móviles en peligro.  

## <a name="what-problem-does-this-solve"></a>¿Qué problema soluciona esto?
Al integrar la información de un proveedor de Mobile Threat Defense, es más fácil proteger los recursos corporativos frente a amenazas que afectan a las plataformas móviles.  

Normalmente, las empresas toman la iniciativa de proteger sus PC frente a vulnerabilidades y ataques, pero a menudo no supervisan sus dispositivos móviles y quedan desprotegidos. Aunque las plataformas móviles cuentan con protección integrada, como el aislamiento de aplicaciones y las tiendas de aplicaciones seguras para los consumidores, estas plataformas siguen siendo vulnerables a ataques sofisticados. A medida que crece el número de empleados que usan dispositivos para trabajar y acceder a información confidencial, con la información proporcionada por un proveedor de Mobile Threat Defense será más sencillo proteger los dispositivos y los recursos frente a ataques cada vez más sofisticados.  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>¿Cómo funcionan los conectores de Intune Mobile Threat Defense?

Intune usa un conector de Mobile Threat Defense para crear un canal de comunicación entre Intune y el proveedor de Mobile Threat Defense que elija. Los asociados de Mobile Threat Defense para Intune ofrecen aplicaciones para dispositivos móviles intuitivas y fáciles de implementar. Estas aplicaciones examinan y analizan de manera activa la información de amenazas y la comparten con Intune. Intune puede usar estos datos para crear informes o para cumplimiento normativo.  

Por ejemplo: Una aplicación de Mobile Threat Defense conectada informa al proveedor de Mobile Threat Defense de que un teléfono de la red está conectado en este momento a una red que es vulnerable a ataques de tipo Man in the Middle. Esta información se clasifica por categorías en función del nivel de riesgo adecuado: bajo, medio o alto. Después, se compara este nivel de riesgo con las provisiones de nivel de riesgo que se definen en Intune. Según esta comparación, se puede revocar el acceso a determinados recursos de su elección mientras el dispositivo está en peligro.

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
- Sophos (detalles próximamente)
- Wandera (detalles próximamente)
