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
ms.openlocfilehash: 2e12792445b36ba6657cbe6b2f6c924f6d97fe3c
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2017
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
| Publicador |Publicador de la aplicación. |Microsoft |
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

## <a name="appinstallertypes"></a>AppInstallerTypes

La entidad **AppInstallerTypes** muestra el origen de instalación de una aplicación.

| Propiedad  | Descripción |
|---------|------------|
| AppTypeID |Identificador del tipo. |
| AppTypeKey |Clave suplente de la clave. |
| AppTypeName |Tipo de aplicación |

## <a name="example"></a>Ejemplo

| AppTypeID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Aplicación de la tienda Android |Aplicación de la tienda Android. |
| 1 |Aplicación de LOB de Android |Aplicación de línea de negocio de Android. |
| 2 |Aplicación administrada de la tienda Android (MAM) |Aplicación de la tienda Android habilitada para la administración. |
| 3 |Aplicación de la tienda iOS |Aplicación de la tienda iOS. |
| 4 |Aplicación de LOB de iOS |Aplicación de línea de negocio de iOS. |
| 5 |Aplicación administrada de la tienda iOS (¿MAM?) |Aplicación de la tienda iOS habilitada para la administración. |
| 6 |Conjunto de aplicaciones de O365 ProPlus |Conjunto de aplicaciones de Office 365 ProPlus para Windows 10. |
| 7 |Aplicación web |Aplicación web. |
| 8 |Aplicación de la Tienda Windows Phone 8.1 |Aplicación de la Tienda Windows Phone 8.1. |
| 9 |Aplicación de la Tienda Windows |Aplicación de la Tienda Windows. |
| 10 |Aplicaciones de LOB de Windows |Aplicación de línea de negocio AppX de Windows. |
| 11 |MSI para Windows Mobile |Aplicación de línea de negocio de MSI. |
| 12 |Aplicación de línea de negocio de Windows Phone |Aplicación de línea de negocio de Windows Phone. |

## <a name="applicationtypes"></a>ApplicationTypes

La entidad **ApplicationTypes** muestra los posibles tipos de una aplicación.

| Propiedad  | Descripción |
|---------|------------|
| ApplicationTypeID |Identificador del tipo. |
| ApplicationTypeKey |Clave suplente de la clave. |
| ApplicationTypeName |Tipo de aplicación |

## <a name="example"></a>Ejemplo

| ApplicationTypeID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |InHouse |Aplicación desarrollada internamente. |
| 1 |DeepLink |Vínculo a una aplicación en una tienda de aplicaciones. |
| 2 |WebLink |Vínculo a una aplicación web. |

## <a name="managedsoftwaretypes"></a>ManagedSoftwareTypes

La entidad **ManagedSoftwareTypes** enumera los posibles tipos de software administrado de una aplicación.

| Propiedad  | Descripción |
|---------|------------|
| SoftwareTypeID |Identificador del tipo. |
| SoftwareTypeKey |Clave suplente de la clave. |
| SoftwareTypeName |Tipo de software |

## <a name="example"></a>Ejemplo

| SoftwareTypeID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Escritorio |Aplicación de escritorio. |
| 2 |Actualizar |Actualización de ventana. |
| 5 |SideCarAgent | |
| 1 |Móvil |Aplicación móvil. |
| 3 |WebLink |Vínculo web. |
| 4 |VppDeepLink |Vínculo a una aplicación en una tienda de aplicaciones que forma parte de un VPP (Programa de Compras por Volumen) |

## <a name="vppprogramtypes"></a>VppProgramTypes

La entidad **VppProgramTypes** muestra los posibles tipos de programa VPP para una aplicación.

| Propiedad  | Descripción |
|---------|------------|
| VppProgramTypeID |Identificador del tipo. |
| VppProgramTypeKey |Clave suplente de la clave. |
| VppProgramTypeName |Tipo de programa VPP. |

## <a name="example"></a>Ejemplo

| VppProgramID  | Nombre | Descripción |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 |Microsoft |Programa VPP de Microsoft. |
| 00000000-0000-0000-0000-000000000000 |No disponible aún |Valor predeterminado. Sin VPP. |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B |Apple |Programa VPP de Apple. |