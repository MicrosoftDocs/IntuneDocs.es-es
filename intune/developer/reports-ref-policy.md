---
title: Referencia de entidades de directivas
titleSuffix: Microsoft Intune
description: Tema de referencia sobre la categoría Directiva de las colecciones de entidades de la API de Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a812234588081443c2ee8ea8d42b161c22ad4232
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940336"
---
# <a name="reference-for-policy-entities"></a>Referencia de entidades de directivas

La categoría **Directivas** contiene entidades para dispositivos móviles que realizan el seguimiento de información como la siguiente:

- Inventario de los perfiles de configuración de dispositivos, los perfiles de configuración de aplicaciones y las directivas de cumplimiento  
- Número de dispositivos con estado correcto, estado pendiente, estado con errores o estado de error por día  
- Número de usuarios con estado correcto, estado pendiente, estado con errores o estado de error por día  
- Número acumulado de dispositivos con estado correcto, estado pendiente, estado con errores o estado de error  

## <a name="policies"></a>directivas

La entidad **policy** muestra los perfiles de configuración de los dispositivos, los perfiles de configuración de las aplicaciones y las directivas de cumplimiento. Puede asignar las directivas con Administración de dispositivos móviles (MDM) a un grupo de la empresa.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| policyKey |Clave única para representar la directiva en el almacenamiento de datos. |123 |
| policyId |Identificador único de la directiva en el almacenamiento de datos. |b66bc706-ffff-7437-0340-032819502773 |
| policyName |Nombre de la directiva. |"Línea base de Windows 10" |
| policyVersion |Versión de la directiva. Cuando la directiva se modifica o se cambia, se crea una versión más reciente. |1, 2, 3 |
| isDeleted |Indica si se ha actualizado el registro de la directiva.  <br>True: la directiva tiene un nuevo registro con campos actualizados. <br>False: registro más reciente de la directiva. |Verdadero/Falso |
| startDateInclusiveUTC |Fecha y hora en formato UTC en que se ha creado la directiva en el almacenamiento de datos. |23/11/2016 12:00:00 AM |
| deletedDateUTC |Fecha y hora en formato UTC en que IsDeleted ha cambiado a True. |23/11/2016 12:00:00 AM |
| rowLastModifiedDateTimeUTC |Fecha y hora en formato UTC en que se ha modificado por última vez la directiva en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="policytypes"></a>policyTypes

La entidad **policyType** muestra los tipos de perfiles de configuración de los dispositivos, los perfiles de configuración de las aplicaciones y las directivas de cumplimiento. Puede asignar las directivas con Administración de dispositivos móviles (MDM) a un grupo de la empresa.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| policyTypeId |Identificador único de la directiva en el sistema de origen. |123 |
| policyTypeKey |Identificador único de la directiva en el almacenamiento de datos. |1 |
| policyTypeName |Nombre del tipo de directiva. |Directiva de cumplimiento de Windows 10. |

## <a name="device-configuration"></a>Configuración de dispositivos

La entidad **deviceConfigurationProfileDeviceActivity** muestra el número de **dispositivos** con estado correcto, pendiente, con errores o de error por día. El número refleja los perfiles de configuración de dispositivos asignados a la entidad. Por ejemplo, si un **dispositivo** muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un dispositivo tiene dos perfiles asignados, uno con el estado correcto y otro con el estado de error, la entidad aumenta el contador de éxitos y coloca el dispositivo en el estado de error. La entidad indica qué número de dispositivos se encuentra en cada estado en un día determinado de los últimos 30 días.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| dateKey |Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro del perfil de configuración de dispositivos. |20160703 |
| pending |Número de dispositivos únicos en estado pendiente. |123 |
| Correcto |Número de dispositivos únicos en estado correcto. |12 |
| error |Número de dispositivos únicos en estado de error. |10 |
| failed |Número de dispositivos únicos en estado con errores. |2 |

La entidad **deviceConfigurationProfileUserActivity** muestra el número de **usuarios** con estado correcto, pendiente, con errores o de error al día. El número refleja los perfiles de configuración de dispositivos asignados a la entidad. Por ejemplo, si un **usuario** muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un usuario tiene dos perfiles asignados, uno en estado correcto y otro en estado de error, se cuenta el usuario en el estado de error.  La entidad **deviceConfigurationProfileUserActivity** muestra cuántos usuarios hay en cada estado en un día determinado de los últimos 30 días.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| dateKey |Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro del perfil de configuración de dispositivos. |20160703 |
| pending |Número de usuarios únicos en estado pendiente. |123 |
| Correcto |Número de usuarios únicos en estado correcto. |12 |
| error |Número de usuarios únicos en estado de error. |10 |
| failed |Número de usuarios únicos en estado con errores. |2 |

## <a name="policytypeactivities"></a>policyTypeActivities

La entidad **policyTypeActivity** muestra el número acumulado de dispositivos con estado correcto, estado pendiente, estado con errores o estado de error. Muestra estos estados con respecto a un perfil de configuración de dispositivos, un perfil de configuración de aplicaciones o una directiva de cumplimiento por día.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| dateKey |Valor dateKey que corresponde a la fecha de registro de la inserción en el repositorio del perfil de configuración de los dispositivos en el almacenamiento de datos. |20160703 |
| policyKey |Valor policyKey, que puede combinarse con la directiva para obtener el nombre de la directiva. |Línea base de Windows 10 |
| policyTypeKey |Clave del tipo de directiva, que puede combinarse con el tipo de directiva para obtener el nombre del tipo de directiva. |Directiva de cumplimiento de Windows 10 |
| pending |Número de dispositivos únicos en estado pendiente. |123 |
| Correcto |Número de dispositivos únicos en estado correcto. |12 |
| error |Número de dispositivos únicos en estado de error. |10 |
| failed |Número de dispositivos únicos en estado con errores. |2 |

## <a name="compliance-policy"></a>Directiva de cumplimiento

La referencia de API de directiva de cumplimiento contiene entidades que proporcionan información de estado sobre las directivas de cumplimiento asignadas a dispositivos.

### <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities

En la tabla siguiente se resume el estado de asignación de directivas de cumplimiento a dispositivos. Muestra el número de dispositivos que hay en cada estado de cumplimiento.


|Propiedad     |Descripción  |Ejemplo  |
|---------|---------|---------|
|dateKey  |Clave de fecha del momento en el que se creó el resumen de la directiva de cumplimiento.|20161204 |
|unknown  |Número de dispositivos sin conexión o que no se pudieron comunicar con Intune o Azure AD por otros motivos. |5|
|notApplicable      |Número de dispositivos a los que no se aplican las directivas de cumplimiento de dispositivos asignadas por el administrador.|201 |
|compliant      |Número de dispositivos con una o varias directivas de cumplimiento de dispositivos asignadas por el administrador aplicadas correctamente. |4083 |
|inGracePeriod      |Número de dispositivos que no son conformes, pero que se encuentran en el período de gracia definido por el administrador. |57|
|nonCompliant      |Número de dispositivos a los que no se pudo aplicar una o varias directivas de cumplimiento de dispositivos asignadas por el administrador o en los que el usuario no ha cumplido las directivas asignadas por el administrador.|43 |
|error      |Número de dispositivos que no se pudieron comunicar con Intune o Azure AD y devolvieron un mensaje de error. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities 

La siguiente tabla resume el estado de asignación de directivas de cumplimiento a dispositivos por directiva y por tipo de directiva. Muestra el número de dispositivos que hay en cada estado de cumplimiento para cada directiva de cumplimiento asignada.



|Propiedad  |Descripción  |Ejemplo  |
|---------|---------|---------|
|dateKey  |Clave de fecha del momento en el que se creó el resumen de la directiva de cumplimiento.|20161219|
|policyKey     |Clave de la directiva de cumplimiento para la que se ha creado el resumen. |10178 |
|policyPlatformKey      |Clave del tipo de plataforma de la directiva de cumplimiento para la que se ha creado el resumen.|5|
|unknown     |Número de dispositivos sin conexión o que no se pudieron comunicar con Intune o Azure AD por otros motivos.|13|
|notApplicable     |Número de dispositivos a los que no se aplican las directivas de cumplimiento de dispositivos asignadas por el administrador.|3|
|compliant      |Número de dispositivos con una o varias directivas de cumplimiento de dispositivos asignadas por el administrador aplicadas correctamente. |45|
|inGracePeriod      |Número de dispositivos que no son conformes, pero que se encuentran en el período de gracia definido por el administrador. |3|
|nonCompliant      |Número de dispositivos a los que no se pudo aplicar una o varias directivas de cumplimiento de dispositivos asignadas por el administrador o en los que el usuario no ha cumplido las directivas asignadas por el administrador.|7|
|error      |Número de dispositivos que no se pudieron comunicar con Intune o Azure AD y devolvieron un mensaje de error. |3|

### <a name="policyplatformtypes"></a>policyPlatformTypes

La tabla siguiente contiene los tipos de plataforma de todas las directivas asignadas. Los tipos de plataforma de directivas que nunca se han asignado a ningún dispositivo no están presentes en esta tabla.


|Propiedad  |Descripción  |Ejemplo  |
|---------|---------|---------|
|policyPlatformTypeKey      |Clave única del tipo de plataforma de directivas. |20170519 |
|policyPlatformTypeId      |Identificador único del tipo de plataforma de directivas.|1|
|policyPlatformTypeName      |Nombre del tipo de plataforma de directivas.|AndroidForWork |

### <a name="policydeviceactivities"></a>policyDeviceActivities

La tabla siguiente muestra el número de dispositivos en estado correcto, pendiente, con errores o de error al día. El número refleja los datos por perfiles de tipo de directiva. Por ejemplo, si un dispositivo muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un dispositivo tiene dos perfiles asignados, uno con el estado correcto y otro con el estado de error, la entidad aumenta el contador de éxitos y coloca el dispositivo en el estado de error. La entidad policyDeviceActivity muestra cuántos dispositivos hay en cada estado en un día determinado de los últimos 30 días.

|Propiedad  |Descripción  |Ejemplo  |
|---------|---------|---------|
|dateKey|Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro del perfil de configuración de dispositivos.|20160703|
|pending|Número de dispositivos únicos en estado pendiente.|123|
|Correcto|Número de dispositivos únicos en estado correcto.|12|
|policyKey|Valor policyKey, que puede combinarse con la directiva para obtener el nombre de la directiva.|Línea base de Windows 10|
|error|Número de dispositivos únicos en estado de error.|10|
|failed|Número de dispositivos únicos en estado con errores.|2|

### <a name="policyuseractivities"></a>policyUserActivities

La tabla siguiente muestra el número de usuarios en estado correcto, pendiente, con errores o de error al día. El número refleja los datos por perfiles de tipo de directiva. Por ejemplo, si un usuario muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un usuario tiene dos perfiles asignados, uno en estado correcto y otro en estado de error, se cuenta el usuario en el estado de error. La entidad PolicyUserActivity muestra cuántos usuarios hay en cada estado en un día determinado de los últimos 30 días.


| Propiedad  |                                         Descripción                                         |       Ejemplo       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  dateKey  | Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro del perfil de configuración de dispositivos. |      20160703       |
|  pending  |                         Número de dispositivos únicos en estado pendiente.                          |         123         |
| Correcto |                         Número de dispositivos únicos en estado correcto.                          |         12          |
| policyKey |                 Valor policyKey, que puede combinarse con la directiva para obtener el nombre de la directiva.                 | Línea base de Windows 10 |
|   error   |                          Número de dispositivos únicos en estado de error.                           |         10          |

