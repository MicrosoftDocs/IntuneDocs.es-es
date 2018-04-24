---
title: Directiva
titlesuffix: Microsoft Intune
description: Tema de referencia sobre la categoría Directiva de las colecciones de entidades de la API de Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0cfeffd4cb466d8bcfc2da072e7e6c028a4e0c8a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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



La entidad **DeviceConfigurationProfileUserActivity** muestra el número de usuarios con estado correcto, pendiente, con errores o de error al día. El número refleja los perfiles de configuración de dispositivos asignados a la entidad. Por ejemplo, si un usuario muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un usuario tiene dos perfiles asignados, uno en estado correcto y otro en estado de error, se cuenta el usuario en el estado de error.  La entidad **DeviceConfigurationProfileUserActivity** muestra cuántos usuarios hay en cada estado en un día determinado de los últimos 30 días.

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
| Failed |Número de dispositivos únicos en estado con errores. |2 |

## <a name="compliance-policy"></a>Directiva de cumplimiento

La referencia de API de directiva de cumplimiento contiene entidades que proporcionan información de estado sobre las directivas de cumplimiento asignadas a dispositivos.

### <a name="compliancepolicystatusdeviceactivities"></a>CompliancePolicyStatusDeviceActivities

En la tabla siguiente se resume el estado de asignación de directivas de cumplimiento a dispositivos. Muestra el número de dispositivos que hay en cada estado de cumplimiento.


|Propiedad     |Descripción  |Ejemplo  |
|---------|---------|---------|
|DateKey  |Clave de fecha del momento en el que se creó el resumen de la directiva de cumplimiento.|20161204 |
|Unknown  |Número de dispositivos sin conexión o que no se pudieron comunicar con Intune o Azure AD por otros motivos. |5|
|No aplicable      |Número de dispositivos a los que no se aplican las directivas de cumplimiento de dispositivos asignadas por el administrador.|201 |
|Conforme      |Número de dispositivos con una o varias directivas de cumplimiento de dispositivos asignadas por el administrador aplicadas correctamente. |4083 |
|InGracePeriod      |Número de dispositivos que no son conformes, pero que se encuentran en el período de gracia definido por el administrador. |57|
|No conforme      |Número de dispositivos a los que no se pudo aplicar una o varias directivas de cumplimiento de dispositivos asignadas por el administrador o en los que el usuario no ha cumplido las directivas asignadas por el administrador.|43 |
|Error      |Número de dispositivos que no se pudieron comunicar con Intune o Azure AD y devolvieron un mensaje de error. |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>CompliancePolicyStatusDevicePerPolicyActivities 

La siguiente tabla resume el estado de asignación de directivas de cumplimiento a dispositivos por directiva y por tipo de directiva. Muestra el número de dispositivos que hay en cada estado de cumplimiento para cada directiva de cumplimiento asignada.



|Propiedad  |Descripción  |Ejemplo  |
|---------|---------|---------|
|DateKey  |Clave de fecha del momento en el que se creó el resumen de la directiva de cumplimiento.|20161219|
|PolicyKey     |Clave de la directiva de cumplimiento para la que se ha creado el resumen. |10178 |
|PolicyPlatformKey      |Clave del tipo de plataforma de la directiva de cumplimiento para la que se ha creado el resumen.|5|
|Unknown     |Número de dispositivos sin conexión o que no se pudieron comunicar con Intune o Azure AD por otros motivos.|13|
|No aplicable     |Número de dispositivos a los que no se aplican las directivas de cumplimiento de dispositivos asignadas por el administrador.|3|
|Conforme      |Número de dispositivos con una o varias directivas de cumplimiento de dispositivos asignadas por el administrador aplicadas correctamente. |45|
|En período de gracia      |Número de dispositivos que no son conformes, pero que se encuentran en el período de gracia definido por el administrador. |3|
|No conforme      |Número de dispositivos a los que no se pudo aplicar una o varias directivas de cumplimiento de dispositivos asignadas por el administrador o en los que el usuario no ha cumplido las directivas asignadas por el administrador.|7|
|Error      |Número de dispositivos que no se pudieron comunicar con Intune o Azure AD y devolvieron un mensaje de error. |3|

### <a name="policyplatformtypes"></a>PolicyPlatformTypes

La tabla siguiente contiene los tipos de plataforma de todas las directivas asignadas. Los tipos de plataforma de directivas que nunca se han asignado a ningún dispositivo no están presentes en esta tabla.


|Propiedad  |Descripción  |Ejemplo  |
|---------|---------|---------|
|PolicyPlatformTypeKey      |Clave única del tipo de plataforma de directivas. |20170519 |
|PolicyPlatformTypeId      |Identificador único del tipo de plataforma de directivas.|1|
|PolicyPlatformTypeName      |Nombre del tipo de plataforma de directivas.|AndroidForWork |

### <a name="policydeviceactivity"></a>PolicyDeviceActivity

La tabla siguiente muestra el número de dispositivos en estado correcto, pendiente, con errores o de error al día. El número refleja los datos por perfiles de tipo de directiva. Por ejemplo, si un dispositivo muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un dispositivo tiene dos perfiles asignados, uno con el estado correcto y otro con el estado de error, la entidad aumenta el contador de éxitos y coloca el dispositivo en el estado de error. La entidad PolicyDeviceActivity muestra cuántos dispositivos hay en cada estado en un día determinado de los últimos 30 días.

|Propiedad  |Descripción  |Ejemplo  |
|---------|---------|---------|
|DateKey|Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro del perfil de configuración de dispositivos.|20160703|
|Pending|Número de dispositivos únicos en estado pendiente.|123|
|Correcto|Número de dispositivos únicos en estado correcto.|12|
PolicyKey|Clave de la directiva, que puede combinarse con la directiva para obtener el nombre de la directiva.|Línea base de Windows 10|
|Error|Número de dispositivos únicos en estado de error.|10|
|Failed|Número de dispositivos únicos en estado con errores.|2|

### <a name="policyuseractivity"></a>PolicyUserActivity 

La tabla siguiente muestra el número de usuarios en estado correcto, pendiente, con errores o de error al día. El número refleja los datos por perfiles de tipo de directiva. Por ejemplo, si un usuario muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un usuario tiene dos perfiles asignados, uno en estado correcto y otro en estado de error, se cuenta el usuario en el estado de error. La entidad PolicyUserActivity muestra cuántos usuarios hay en cada estado en un día determinado de los últimos 30 días.


| Propiedad  |                                         Descripción                                         |       Ejemplo       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  DateKey  | Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro del perfil de configuración de dispositivos. |      20160703       |
|  Pending  |                         Número de dispositivos únicos en estado pendiente.                          |         123         |
| Correcto |                         Número de dispositivos únicos en estado correcto.                          |         12          |
| PolicyKey |                Clave de la directiva, que puede combinarse con la directiva para obtener el nombre de la directiva.                 | Línea base de Windows 10 |
|   Error   |                          Número de dispositivos únicos en estado de error.                           |         10          |

