---
title: Entidad IntuneManagementExtension
titleSuffix: Microsoft Intune
description: Tema de referencia sobre la categoría de entidad IntuneManagementExtension de las colecciones de entidades de la API de almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2efddc75c5819a25d9ba097cb24726e80df14f2
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654199"
---
# <a name="reference-for-intune-management-extensions"></a>Referencia de las extensiones de administración de Intune

La categoría **intuneManagementExtension** contiene entidades para dispositivos móviles que realizan el seguimiento de información como la siguiente:

- Versiones de una entidad IntuneManagementExtension
- Estado de instalación de una entidad IntuneManagementExtension

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

La entidad **intuneManagementExtensionVersion** muestra todas las versiones usadas por intuneManagementExtension.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| extensionVersionKey |Identificador único de la versión de intuneManagementExtension. | 1 |
| extensionVersion |Número de versión de 4 dígitos. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

El valor **intuneManagementExtensionHealthState** muestra todos los estados de mantenimiento posibles de intuneManagementExtension.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| extensionStateKey |Identificador único del estado de mantenimiento. | 2 |
| extensionState |Estado de mantenimiento de una entidad IntuneManagementExtension. | Correcto |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

El valor **intuneManagementExtension** muestra el mantenimiento diario de intuneManagementExtension de cada dispositivo Windows 10.
Los datos se conservan durante 60 días. 


|      Propiedad       |                         Descripción                         | Ejemplo |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               Identificador único de la fecha.                |   123   |
|      tenantKey      |              Identificador único del inquilino.               |   456   |
|      deviceKey      |              Identificador único del dispositivo.               |   789   |
| extensionVersionKey | Identificador único de la versión de IntuneManagementExtension. |    1    |
|  extensionStateKey  |             Identificador único del estado de mantenimiento.              |    2    |

