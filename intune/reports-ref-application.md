---
title: "Aplicación"
titlesuffix: Microsoft Intune
description: "Tema de referencia sobre la categoría Aplicaciones de las colecciones de entidades de la API de Almacenamiento de datos de Intune."
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e7de3ab89ff75b381d0438f49fb6015b0eb28d28
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
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


## <a name="vppprogramtypes"></a>VppProgramTypes

La entidad **VppProgramTypes** muestra los posibles tipos de programa VPP para una aplicación.

| Propiedad  | Descripción |
|---------|------------|
| VppProgramTypeID | Identificador del tipo. |
| VppProgramTypeKey | Clave suplente de la clave. |
| VppProgramTypeName | Tipo de programa VPP. |

### <a name="example"></a>Ejemplo

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

## <a name="mobileappinstallstate"></a>MobileAppInstallState

La entidad **MobileAppInstallState** representa el estado de instalación de una aplicación móvil una vez que se ha asignado a un grupo que contiene dispositivos, usuarios o ambos.

| Propiedad | Descripción |
|---|---|
| AppInstallStateKey | El identificador único del estado de instalación de aplicación de su cuenta. |
| AppInstallState | Valor de enumeración del estado de instalación de aplicación. |
| AppInstallStateName | Nombre del estado de instalación de aplicación. |

## <a name="mobileappdeviceuserinstallstatus"></a>MobileAppDeviceUserInstallStatus

El valor **MobileAppDeviceUserInstallStatus** representa un estado de instalación de aplicación móvil para un dispositivo y un usuario determinados.

| Propiedad | Descripción |
|---|---|
| DateKey | Clave de la fecha en la que se registró el estado de instalación de la aplicación. |
| AppKey | Clave de la aplicación móvil que se utiliza para identificar una instancia de AppRevision. |
| DeviceKey | Clave de un dispositivo de destino que se usa para identificar una instancia del dispositivo. |
| UserKey | Clave de un usuario de destino que se usa para identificar una instancia del usuario. |
|AppInstallStateKey | Clave del estado de instalación de aplicación utilizado para identificar una instancia de MobileAppInstallState. |
| Código de error | El código de error devuelto por el instalador de la aplicación, la plataforma móvil o el servicio que pertenece a la instalación de la aplicación. |
