---
title: Directiva | Microsoft Docs
description: "Tema de referencia sobre la categoría Directiva de las colecciones de entidades de la API de Almacenamiento de datos de Intune."
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D5ADB9D8-D46A-43BD-AB0F-D6927508E3F4
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 079cfe097d6cf462f9ccd0a32d2e327b3b605e40
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-policy-entities"></a>Referencia de entidades de directivas

La categoría **Directiva** contiene entidades para dispositivos móviles que realizan el seguimiento de información como la siguiente:

  -  Inventario de los perfiles de configuración de dispositivos, los perfiles de configuración de aplicaciones y las directivas de cumplimiento  
  -  Número de dispositivos con estado correcto, estado pendiente, estado con errores o estado de error por día  
  -  Número de usuarios con estado correcto, estado pendiente, estado con errores o estado de error por día  
  -  Número acumulado de dispositivos con estado correcto, estado pendiente, estado con errores o estado de error  

## <a name="policy"></a>Directiva

La entidad **Policy** muestra los perfiles de configuración de dispositivos, los perfiles de configuración de aplicaciones y las directivas de cumplimiento. Puede asignar las directivas con Administración de dispositivos móviles (MDM) a un grupo de la empresa.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| PolicyKey |Clave única para representar la directiva en el almacenamiento de datos. |123 |
| PolicyId |Identificador único de la directiva en el almacenamiento de datos. |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |Nombre de la directiva. |"Línea base de Windows 10" |
| PolicyVersion |Versión de la directiva. Cuando la directiva se modifica o se cambia, se crea una versión más reciente. |1, 2, 3 |
| IsDeleted |Indica si se ha actualizado el registro de la directiva.  <br>True: la directiva tiene un nuevo registro con campos actualizados. <br>False: registro más reciente de la directiva. |Verdadero/Falso |
| StartDateInclusiveUTC |Fecha y hora en formato UTC en que se ha creado la directiva en el almacenamiento de datos. |23/11/2016 12:00:00 AM |
| DeletedDateUTC |Fecha y hora en formato UTC en que IsDeleted ha cambiado a True. |23/11/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Fecha y hora en formato UTC en que se ha modificado por última vez la directiva en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="policytype"></a>PolicyType

La entidad **PolicyType** muestra los tipos de perfiles de configuración de dispositivos, perfiles de configuración de aplicaciones y directivas de cumplimiento. Puede asignar las directivas con Administración de dispositivos móviles (MDM) a un grupo de la empresa.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| PolicyTypeId |Identificador único de la directiva en el sistema de origen. |123 |
| PolicyTypeKey |Identificador único de la directiva en el almacenamiento de datos. |1 |
| PolicyTypeName |Nombre del tipo de directiva. |Directiva de cumplimiento de Windows 10. |

## <a name="deviceconfiguration"></a>DeviceConfiguration

La entidad **DeviceConfigurationProfileDeviceActivity** muestra el número de dispositivos con estado correcto, estado pendiente, estado con errores o estado de error por día. El número refleja los perfiles de configuración de dispositivos asignados a la entidad. Por ejemplo, si un dispositivo muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un dispositivo tiene dos perfiles asignados, uno con el estado correcto y otro con el estado de error, la entidad aumenta el contador de éxitos y coloca el dispositivo en el estado de error. La entidad indica qué número de dispositivos se encuentra en cada estado en un día determinado de los últimos 30 días.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| DateKey |Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro del perfil de configuración de dispositivos. |20160703 |
| Pending |Número de dispositivos únicos en estado pendiente. |123 |
| Correcto |Número de dispositivos únicos en estado correcto. |12 |
| Error |Número de dispositivos únicos en estado de error. |10 |
| Failed |Número de dispositivos únicos en estado con errores. |2 |

## <a name="userconfiguration"></a>UserConfiguration

La entidad **UserConfigurationProfileDeviceActivity** muestra el número de usuarios con estado correcto, estado pendiente, estado con errores o estado de error por día. El número refleja los perfiles de configuración de dispositivos asignados a la entidad. Por ejemplo, si un usuario muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un usuario tiene dos perfiles asignados, uno con el estado correcto y otro con el estado de error, se cuenta el usuario con el estado de error.  La entidad **UserConfigurationProfileDeviceActivity** muestra cuántos usuarios se encuentran en cada estado en un día determinado de los últimos 30 días.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| DateKey |Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro del perfil de configuración de dispositivos. |20160703 |
| Pending |Número de usuarios únicos en estado pendiente. |123 |
| Correcto |Número de usuarios únicos en estado correcto. |12 |
| Error |Número de usuarios únicos en estado de error. |10 |
| Failed |Número de usuarios únicos en estado con errores. |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

La entidad **PolicyTypeActivity** muestra el número acumulado de dispositivos con estado correcto, estado pendiente, estado con errores o estado de error. Muestra estos estados con respecto a un perfil de configuración de dispositivos, un perfil de configuración de aplicaciones o una directiva de cumplimiento por día.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| DateKey |Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro del perfil de configuración de dispositivos. |20160703 |
| PolicyKey |Clave de la directiva, que puede combinarse con la directiva para obtener el nombre de la directiva. |Línea base de Windows 10 |
| PolicyTypeKey |Clave del tipo de directiva, que puede combinarse con el tipo de directiva para obtener el nombre del tipo de directiva. |Directiva de cumplimiento de Windows 10 |
| Pending |Número de dispositivos únicos en estado pendiente. |123 |
| Correcto |Número de dispositivos únicos en estado correcto. |12 |
| Error |Número de dispositivos únicos en estado de error. |10 |
| Fail- |Número de dispositivos únicos en estado con errores. |2 |