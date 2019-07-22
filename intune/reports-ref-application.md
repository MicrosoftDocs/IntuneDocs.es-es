---
title: Referencia de entidades de aplicaciones
titleSuffix: Microsoft Intune
description: Tema de referencia sobre la categoría Aplicaciones de las colecciones de entidades de la API de Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5436de6b972e5cbe8b2b17d42f0974cb38df47e
ms.sourcegitcommit: c3ac858bbadb63d248ed54069e48160d703bbaf2
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313806"
---
# <a name="reference-for-application-entities"></a>Referencia de entidades de aplicaciones

La categoría **Application** contiene entidades para dispositivos móviles que realizan el seguimiento de información como la siguiente:

- Versiones de una aplicación
- Origen de instalación de una aplicación
- Tipo de los desarrolladores que han creado una aplicación
- Tipos de software administrado para una aplicación, por ejemplo **asociado** o **escritorio**
- Estado del Programa de Compras por Volumen (VPP) de una aplicación

## <a name="apprevisions"></a>appRevisions

La entidad **appRevision** muestra todas las versiones de las aplicaciones.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| appKey |Identificador único de la aplicación. |123 |
| applicationId |Identificador único de la aplicación. Se parece a AppKey, pero es una clave natural. |b66bc706-ffff-7437-0340-032819502773 |
| revision |Versión tal como la indicó el administrador durante la carga del archivo binario. |2 |
| title |Título de la aplicación. |Excel |
| publisher |Editor de la aplicación. |Microsoft |
| uploadState |Estado de carga de la aplicación. |1 |
| appTypeKey |Referencia a AppType, descrito en la sección siguiente. | |
| vppProgramTypeKey |Referencia a VppProgramType, descrito más adelante. | |
| creationTime |Fecha y hora de creación de esta revisión. |23/11/2016 12:00:00 AM |
| modifiedTime |Fecha y hora de la última modificación de cualquier elemento relacionado con esta revisión. |23/11/2016 12:00:00 AM |
| tamaño |Tamaño del archivo binario. | |
| startDateInclusiveUTC |Fecha y hora en formato UTC en que se ha creado esta revisión de la aplicación en el almacenamiento de datos. |23/11/2016 12:00:00 AM |
| endDateExclusiveUTC |Fecha y hora en formato UTC en que esta revisión de la aplicación ha quedado obsoleta. |23/11/2016 12:00:00 AM |
| isCurrent |Indica si esta versión de la aplicación está actualizada o no en el almacenamiento de datos. |Verdadero/Falso |
| rowLastModifiedDateTimeUTC |Fecha y hora en formato UTC en que se ha modificado por última vez esta versión de la aplicación en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="apptypes"></a>appTypes

La entidad **appTypes** muestra el origen de instalación de una aplicación.

| Propiedad  | Descripción |
|---------|------------|
| appTypeID |Identificador del tipo. |
| appTypeKey |Clave suplente de la clave. |
| appTypeName |Tipo de aplicación |

### <a name="example"></a>Ejemplo

| AppTypeID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Aplicación de la tienda Android | Una aplicación de la tienda Android. |
| 1 |Aplicación de LOB de Android | Una aplicación de línea de negocio de Android. |
| 2 |Aplicación administrada de la tienda Android (MAM) | Una aplicación de la tienda Android habilitada para la administración. |
| 3 |Aplicación de la tienda iOS | Una aplicación de la tienda iOS. |
| 4 |Aplicación de LOB de iOS | Una aplicación de línea de negocio de iOS. |
| 5 |Aplicación administrada de la tienda iOS (¿MAM?) | Una aplicación de la tienda iOS habilitada para la administración. |
| 6 |Conjunto de aplicaciones de O365 ProPlus | El conjunto de aplicaciones de Office 365 ProPlus para Windows 10. |
| 7 |Aplicación web | Una aplicación web. |
| 8 |Aplicación de la Tienda Windows Phone 8.1 | Una aplicación de la Tienda Windows Phone 8.1. |
| 9 |Aplicación de la Tienda Windows | Una aplicación de la Tienda Windows. |
| 10 |Aplicaciones de LOB de Windows | Una aplicación de línea de negocio AppX de Windows. |
| 11 |MSI para Windows Mobile | Una aplicación de línea de negocio de MSI. |
| 12 |Aplicación de línea de negocio de Windows Phone | Una aplicación de línea de negocio de Windows Phone. |


## <a name="vppprogramtypes"></a>vppProgramTypes

La entidad **vppProgramTypes** muestra los posibles tipos de programa VPP para una aplicación.

| Propiedad  | Descripción |
|---------|------------|
| vppProgramTypeID | Identificador del tipo. |
| vppProgramTypeKey | Clave suplente de la clave. |
| vppProgramTypeName | Tipo de programa VPP. |

### <a name="example"></a>Ejemplo

| VppProgramID  | Nombre | Descripción |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Programa VPP de Microsoft. |
| 00000000-0000-0000-0000-000000000000 | No disponible aún | Valor predeterminado. Sin VPP. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Programa VPP de Apple. |



## <a name="applicationinventories"></a>applicationInventories

La entidad **applicationInventory** muestra las aplicaciones que se encuentran en el dispositivo en el momento de la recopilación del inventario.

| Propiedad  | Descripción |
|---------|------------|
| deviceKey | Se trata de una referencia a la tabla de dispositivos que contiene el identificador de dispositivo de Intune. |
| dateKey | Referencia a la tabla de fechas que indica el día del inventario. |
| applicationName | El nombre de la aplicación. |
| applicationVersion | Versión de la aplicación. |
| bundleSize | El tamaño de la aplicación en bytes. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates

La entidad **mobileAppInstallState** representa el estado de la instalación de una aplicación móvil una vez asignada a un grupo que contiene dispositivos, usuarios o ambos.

| Propiedad | Descripción |
|---|---|
| appInstallStateKey | El identificador único del estado de instalación de aplicación de su cuenta. |
| appInstallState | Valor de enumeración del estado de instalación de aplicación. |
| appInstallStateName | Nombre del estado de instalación de aplicación. |



