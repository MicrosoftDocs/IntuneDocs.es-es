---
title: Mobile Threat Defense con Microsoft Intune
titleSuffix: Microsoft Intune
description: Use Mobile Threat Defense (MTD) con su asociado de defensa contra las amenazas móviles para proteger el acceso a recursos de empresa en función del riesgo del dispositivo.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b67e3b14fd94376fb6dacad88fa58ddc460a6bc5
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "73057579"
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Integración de Mobile Threat Defense con Intune

Intune puede integrar datos de un proveedor de Mobile Threat Defense (MTD) como un origen de información para las directivas de cumplimiento de dispositivos y reglas de acceso condicional de dispositivos. Puede usar esta información para proteger mejor los recursos corporativos, como Exchange y SharePoint, bloqueando el acceso de dispositivos móviles en peligro.

Intune puede usar estos mismos datos como origen para los dispositivos no inscritos mediante directivas de protección de aplicaciones de Intune. Por tanto, los administradores pueden usar esta información para facilitar la protección de los datos corporativos dentro de una [aplicación protegida de Microsoft Intune](~/apps/apps-supported-intune-apps.md) y emitir un bloqueo o un borrado selectivo.

## <a name="protect-corporate-resources"></a>Protección de los recursos corporativos

Integrar información de los proveedores de MTD puede ayudarle a proteger los recursos corporativos frente a las amenazas que afectan a las plataformas para dispositivos móviles.  

Normalmente, las empresas toman la iniciativa de proteger sus PC frente a vulnerabilidades y ataques, pero a menudo no supervisan sus dispositivos móviles y quedan desprotegidos. Aunque las plataformas móviles cuentan con protección integrada, como el aislamiento de aplicaciones y las tiendas de aplicaciones seguras para los consumidores, estas plataformas siguen siendo vulnerables a ataques sofisticados. A medida que crece el número de empleados que usan dispositivos para trabajar y acceder a información confidencial, la información procedente de los proveedores de MTD puede ayudarle a proteger los dispositivos y los recursos frente a ataques cada vez más sofisticados.

## <a name="intune-mobile-threat-defense-connectors"></a>Conectores Intune Mobile Threat Defense

Intune usa un conector Mobile Threat Defense para crear un canal de comunicación entre Intune y el proveedor de MTD que elija. Los asociados de Intune MTD ofrecen aplicaciones para dispositivos móviles intuitivas y fáciles de implementar. Estas aplicaciones examinan y analizan de manera activa la información de amenazas y la comparten con Intune. Intune puede usar estos datos para crear informes o para cumplimiento normativo.

Por ejemplo: Una aplicación de MTD conectada informa al proveedor de MTD de que un teléfono de la red está conectado en ese momento a una red que es vulnerable a ataques de tipo "Man in the Middle". Esta información se clasifica por categorías en función del nivel de riesgo adecuado: bajo, medio o alto. Después, se compara este nivel de riesgo con las provisiones de nivel de riesgo que se definen en Intune. Según esta comparación, se puede revocar el acceso a determinados recursos de su elección mientras el dispositivo está en peligro.

## <a name="data-that-intune-collects-for-mobile-threat-defense"></a>Datos que recopila Intune para Mobile Threat Defense

Si está habilitado, Intune recopila la información de inventario de aplicaciones de los dispositivos personales y corporativos y la pone a disposición de los proveedores de MTD, como Lookout for Work. Puede recopilar un inventario de aplicaciones de los usuarios de dispositivos iOS.

Este servicio es de suscripción, y no se comparte información de inventario de la aplicación de forma predeterminada. Un administrador de Intune debe habilitar la **sincronización de aplicaciones para dispositivos iOS** en la configuración del conector de Mobile Threat Defense antes de compartir la información de inventario de una aplicación.

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

## <a name="sample-scenarios-for-enrolled-devices-using-device-compliance-policies"></a>Escenarios de ejemplo para dispositivos inscritos mediante directivas de cumplimiento de dispositivos

Cuando un dispositivo se considera infectado por la solución de Mobile Threat Defense:

![Imagen en que se muestra un dispositivo de Mobile Threat Defense infectado](./media/mobile-threat-defense/MTD-image-1.png)

Se concede el acceso cuando se corrige el dispositivo:

![Imagen en que se muestra un acceso concedido por Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-2.png)

## <a name="sample-scenarios-for-unenrolled-devices-using-intune-app-protection-policies"></a>Escenarios de ejemplo para dispositivos no inscritos mediante directivas de protección de aplicaciones de Intune

Cuando un dispositivo se considera infectado por la solución de Mobile Threat Defense:<br>
![Imagen en la que se muestra un dispositivo de Mobile Threat Defense infectado](./media/mobile-threat-defense/MTD-image-3.png)

Se concede el acceso cuando se corrige el dispositivo:<br>
![Imagen en la que se muestra un acceso concedido por Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-4.png)

> [!NOTE]
> Puede usar varios proveedores de Mobile Defense con un solo inquilino de Intune. Sin embargo, cuando se configuran dos o más proveedores para usarlos en la misma plataforma, todos los dispositivos que ejecutan esa plataforma deben instalar cada aplicación MTD y examinar las posibles amenazas. Si no se envía un examen desde alguna aplicación configurada, el dispositivo se marca como no conforme. 

## <a name="mobile-threat-defense-partners"></a>Socios de Mobile Threat Defense

Obtenga información sobre cómo proteger el acceso al recurso de la empresa en función del riesgo del dispositivo, la red y la aplicación con:

- [Lookout for Work](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [SandBlast Mobile de Check Point](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile Threat Defense](wandera-mtd-connector.md)
