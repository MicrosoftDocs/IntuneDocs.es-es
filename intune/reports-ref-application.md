---
title: "Aplicación | Microsoft Docs"
description: "Tema de referencia sobre la categoría Aplicaciones de las colecciones de entidades de la API de Almacenamiento de datos de Intune."
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9fd14c985b4cedcd0575b2b6ea29e7aa4d8bb2d4
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-application-entities"></a>Referencia de entidades de aplicaciones

La categoría **Application** contiene entidades para dispositivos móviles que realizan el seguimiento de información como la siguiente:

  -  Versiones de una aplicación
  -  Origen de instalación de una aplicación
  -  Tipo de los desarrolladores que han creado una aplicación
  -  Tipos de software administrado para una aplicación, por ejemplo **asociado** o **escritorio**
  -  Estado del Programa de Compras por Volumen (VPP) de una aplicación

## <a name="apprevision"></a>AppRevision

La entidad **AppRevision** muestra todas las versiones de las aplicaciones.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| AppKey |Identificador único de la aplicación. |123 |
| ApplicationId |Identificador único de la aplicación. Se parece a AppKey, pero es una clave natural. |b66bc706-ffff-7437-0340-032819502773 |
| Revisión |Versión tal como la indicó el administrador durante la carga del archivo binario. |2 |
| Título |Título de la aplicación. |Excel |
| Publicador |Editor de la aplicación. |Microsoft |
| UploadState |Estado de carga de la aplicación. |1 |
| AppTypeKey |Referencia a AppType, descrito en la sección siguiente. | |
| VppProgramTypeKey |Referencia a VppProgramType, descrito más adelante. | |
| CreationTime |Fecha y hora de creación de esta revisión. |23/11/2016 12:00:00 AM |
| ModifiedTime |Fecha y hora de la última modificación de cualquier elemento relacionado con esta revisión. |23/11/2016 12:00:00 AM |
| Tamaño |Tamaño del archivo binario. | |
| StartDateInclusiveUTC |Fecha y hora en formato UTC en que se ha creado esta revisión de la aplicación en el almacenamiento de datos. |23/11/2016 12:00:00 AM |
| EndDateExclusiveUTC |Fecha y hora en formato UTC en que esta revisión de la aplicación ha quedado obsoleta. |23/11/2016 12:00:00 AM |
| IsCurrent |Indica si esta versión de la aplicación está actualizada o no en el almacenamiento de datos. |Verdadero/Falso |
| RowLastModifiedDateTimeUTC |Fecha y hora en formato UTC en que se ha modificado por última vez esta versión de la aplicación en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="apptypes"></a>AppTypes

La entidad **AppTypes** muestra el origen de instalación de una aplicación.

| Propiedad  | Descripción |
|---------|------------|
| AppTypeID |Identificador del tipo. |
| AppTypeKey |Clave suplente de la clave. |
| AppTypeName |Tipo de aplicación |

## <a name="example"></a>Ejemplo

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


## <a name="vppprogramtypes"></a>VppProgramTypes

La entidad **VppProgramTypes** muestra los posibles tipos de programa VPP para una aplicación.

| Propiedad  | Descripción |
|---------|------------|
| VppProgramTypeID | Identificador del tipo. |
| VppProgramTypeKey | Clave suplente de la clave. |
| VppProgramTypeName | Tipo de programa VPP. |

## <a name="example"></a>Ejemplo

| VppProgramID  | Nombre | Descripción |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | Programa VPP de Microsoft. |
| 00000000-0000-0000-0000-000000000000 | No disponible aún | Valor predeterminado. Sin VPP. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | Programa VPP de Apple. |



## <a name="applicationinventory"></a>ApplicationInventory

La entidad **ApplicationInventory** muestra las aplicaciones que se encuentran en el dispositivo en el momento de recopilación del inventario.

| Propiedad  | Descripción |
|---------|------------|
| DeviceKey | Se trata de una referencia a la tabla de dispositivos que contiene el identificador de dispositivo de Intune. |
| DateKey | Referencia a la tabla de fechas que indica el día del inventario. |
| ApplicationName | El nombre de la aplicación. |
| ApplicationVersion | Versión de la aplicación. |
| BundleSize | El tamaño de la aplicación en bytes. |
