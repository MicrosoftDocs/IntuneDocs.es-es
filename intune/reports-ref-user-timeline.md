---
title: Escala de tiempo de la entidad de usuario de Almacenamiento de datos
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo Data Warehouse de Microsoft Intune representa los usuarios en una escala de tiempo.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 363D148E-688F-4830-B6DE-AB4FE3648817
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfa1df8053301b92c04d92f8c48d2c6c34e30129
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799758"
---
# <a name="user-lifetime-representation-in-the-microsoft-intune-data-warehouse"></a>Representación de la duración del usuario en el Almacenamiento de datos de Microsoft Intune

Puede usar el mes de las instantáneas de datos almacenadas en Almacenamiento de datos de Intune para responder las preguntas sobre las tendencias basadas en el tiempo. Por ejemplo, puede consultar el número de usuarios que se agregan durante un mes. También podría preguntar el número de usuarios que se quitó del sistema.

Para proporcionar esta información de tipo, el almacenamiento de datos almacena información histórica. El almacenamiento de datos puede hacer seguimiento de la duración de una entidad. Este almacenamiento registra cuándo se creó una entidad, cuándo cambia el estado de la entidad y cuándo se elimina la entidad. Con el historial que se capturó con instantáneas diarias de medidas cuantitativas, puede comparar un día con el día anterior, y así sucesivamente.

Trabajar con las duraciones de las entidades puede resultar confuso, porque las entidades cambian de estado. Esto significa que si observa una instantánea el día 30, es posible que un registro de usuario no exista con un estado activo en los datos, mientras que el día 29 y 28, el registro de la entidad puede existir como activo. Y, antes del día 28, el usuario no existía en absoluto.

Este escenario puede ser más claro si se recorre la duración de una entidad.

Imaginemos que el 01/06/2017 se asigna una licencia al usuario **John Smith**. La tabla **Usuario** tendría entonces la entrada siguiente: 
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 01/06/2017 | 12/31/9999 | TRUE
 
John Smith deja la licencia el 25/07/2017. La tabla **Usuario** tiene las entradas siguientes. Los cambios en los registros existentes son `marked`. 

| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 01/06/2017 | `07/26/2017` | `FALSE` 
| John Smith | TRUE | 26/07/2017 | 12/31/9999 | TRUE 

La primera fila indica que John Smith existió en Intune desde el 01/06/2017 al 25/07/2017. El segundo registro indica que el usuario se eliminó el 25/07/2017 y ya no existe en Intune.

Ahora imaginemos que se asigna una licencia nueva a John Smith el 31/08/2017. La tabla Usuario tendría entonces las entradas siguientes:
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 01/06/2017 | 26/07/2017 | FALSE 
| John Smith | TRUE | 26/07/2017 | `08/31/2017` | `FALSE` 
| John Smith | FALSE | 08/31/2017 | 12/31/9999 | TRUE 
 
Una persona que desea ver el estado actual de todos los usuarios querría aplicar un filtro donde `IsCurrent = TRUE`. 
 
Una persona que espera ver solo los usuarios existentes querría aplicar un filtro donde `IsCurrent = TRUE AND IsDeleted = FALSE`.

## <a name="dimension-tables-in-the-entity-lifetime"></a>Tablas de dimensiones en la duración de la entidad

Con el fin de almacenar el historial de los cambios de estado de las entidades, Intune no elimina los registros. En su lugar, marca el registro como eliminado. Esto se denomina una eliminación temporal. Las tablas de dimensiones usan varias columnas de metadatos para hacer seguimiento de la duración de los registros. 

Las columnas de metadatos más usadas son: 

| Nombre de la propiedad de metadatos  | Interpretación de los valores |
|--|--|
| IsDeleted | Indica si la entidad se eliminó en Intune. |
| StartDateInclusiveUTC  | La fecha UTC en que la entidad se cargó en Almacenamiento de datos de Intune. Es posible que la entidad se haya creado antes de importarla a Almacenamiento de datos de Intune. |
| DeletedDateUTC  | La fecha UTC en que la entidad se eliminó en Intune. |  

Cualquier columna de metadatos que comience con el prefijo **Row**, como **RowLastModifiedDateTimeUTC**, indica cuándo se creó o modificó un registro en Almacenamiento de datos de Intune. El almacén de datos es descendente en relación con los datos de Intune. Este valor no tiene relación con la duración de la entidad en Intune.  
 
Toda persona que quiera ver solo las entidades de dimensiones que existen actualmente querrían aplicar un filtro donde **IsDeleted = FALSE**.

## <a name="next-steps"></a>Pasos siguientes

 - Para más información sobre la entidad **Usuario actual**, vea [Referencia de la entidad de usuario actual](reports-ref-current-user.md).
 - Para más información sobre la entidad **Usuario**, vea [Referencia de la entidad de usuario](reports-ref-user.md).
