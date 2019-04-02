---
title: Dispositivos - Almacenamiento de datos de Intune
titlesuffix: Microsoft Intune
description: Tema de referencia sobre la categoría Dispositivos de las colecciones de entidades de la API de Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 29213400b5baf9705c188bb45b3666b65262d577
ms.sourcegitcommit: 93286c22426dcb59191a99e3cf2af4ff6ff16522
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2019
ms.locfileid: "58358240"
---
# <a name="reference-for-devices-entities"></a>Referencia de las entidades Devices

La categoría **Dispositivos** contiene entidades para dispositivos móviles que realizan el seguimiento de información como la siguiente:

  -  Tipo de dispositivo
  -  Estado de registro e inscripción del dispositivo
  -  Propiedad del dispositivo
  -  Estado de administración del dispositivo
  -  Estado de pertenencia del dispositivo en Azure AD
  -  Estado de inscripción
  -  Información histórica sobre el dispositivo
  -  Inventario de aplicaciones del dispositivo

## <a name="devicetypes"></a>DeviceTypes

La entidad **DeviceTypes** representa el tipo de dispositivo al que hacen referencia otras entidades de almacenamiento de datos. Normalmente, el tipo de dispositivo describe el modelo del dispositivo, el fabricante o una combinación de ambos.

| Propiedad  | Descripción |
|---------|------------|
| DeviceTypeID |Identificador único del tipo de dispositivo. |
| DeviceTypeKey |Identificador único del tipo de dispositivo en el almacenamiento de datos. Clave suplente. |
| DeviceTypeName |Tipo de dispositivo |

### <a name="example"></a>Ejemplo

| deviceTypeID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Escritorio |Dispositivo de escritorio de Windows |
| 1 |WindowsRT |Dispositivo WindowsRT |
| 2 |WinMO6 |Dispositivo Windows Mobile 6.0 |
| 3 |Nokia |Dispositivo Nokia |
| 4 |WindowsPhone |Dispositivo Windows Phone |
| 5 |Mac |Dispositivo Mac |
| 6 |WinCE |Dispositivo Windows CE |
| 7 |WinEmbedded |Dispositivo Windows Embedded |
| 8 |IPhone |Dispositivo iPhone |
| 9 |IPad |Dispositivo iPad |
| 10 |IPod |Dispositivo iPod |
| 11 |Android |Dispositivo Android administrado mediante el Administrador de dispositivos |
| 12 |ISocConsumer |Dispositivo iSoc Consumer |
| 14 |MacMDM |Dispositivo Mac OS X administrado con el agente MDM integrado |
| 15 |HoloLens |Dispositivo HoloLens |
| 16 |SurfaceHub |Dispositivo Surface Hub |
| 17 |AndroidForWork |Dispositivo Android administrado mediante el propietario con perfil Android |
| 100 |BlackBerry |Dispositivo BlackBerry |
| 101 |Palm |Dispositivo Palm |
| 255 |Unknown |Tipo de dispositivo desconocido |

## <a name="enrollmentactivities"></a>enrollmentActivities 
La entidad **EnrollmentActivity** indica la actividad de una inscripción de dispositivos.

| Propiedad                      | Descripción                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | Clave de la fecha en la que se ha registrado esta actividad de inscripción.               |
| deviceEnrollmentTypeKey       | Clave del tipo de inscripción.                                        |
| enrollmentEventStatusKey      | Clave del estado que indica si la inscripción se ha realizado correctamente o si se ha producido un error.    |
| enrollmentFailureCategoryKey  | Clave de la categoría del error de la inscripción (si se ha producido un error en la inscripción).        |
| enrollmentFailureReasonKey    | Clave del motivo del error de la inscripción (si se ha producido un error en la inscripción).          |
| osVersion                     | Versión del sistema operativo del dispositivo.                               |
| count                         | Recuento total de las actividades de inscripción que coinciden con las clasificaciones anteriores.  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
La entidad **EnrollmentEventStatus** indica el resultado de una inscripción de dispositivos.

| Propiedad                   | Descripción                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | Identificador único del estado de la inscripción en el almacenamiento de datos (clave suplente).  |
| enrollmentEventStatusName  | Nombre del estado de la inscripción. Vea los ejemplos siguientes.                            |

### <a name="example"></a>Ejemplo

| enrollmentEventStatusName  | Descripción                            |
|----------------------------|----------------------------------------|
| Correcto                    | Inscripción de dispositivo correcta.         |
| Failed                     | Inscripción de dispositivo errónea.             |
| No disponible              | El estado de la inscripción no está disponible.  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
La entidad **EnrollmentFailureCategory** indica el motivo del error de una inscripción de dispositivos. 

| Propiedad                       | Descripción                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | Identificador único de la categoría del error de la inscripción en el almacenamiento de datos (clave suplente).  |
| enrollmentFailureCategoryName  | Nombre de la categoría del error de la inscripción. Vea los ejemplos siguientes.                            |

### <a name="example"></a>Ejemplo

| enrollmentFailureCategoryName   | Descripción                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| No aplicable                  | La categoría del error de la inscripción no es aplicable.                                                            |
| No disponible                   | La categoría del error de la inscripción no está disponible.                                                             |
| Unknown                         | Error desconocido.                                                                                                |
| Autenticación                  | Error de autenticación.                                                                                        |
| Autorización                   | La llamada se ha autenticado, pero no tiene autorización para inscribirse.                                                         |
| AccountValidation               | Error al validar la cuenta para la inscripción. (Cuenta bloqueada, inscripción no habilitada).                      |
| UserValidation                  | No se ha podido validar al usuario. (El usuario no existe, falta la licencia).                                           |
| DeviceNotSupported              | El dispositivo no es compatible con la administración de dispositivos móviles.                                                         |
| InMaintenance                   | La cuenta está en mantenimiento.                                                                                    |
| BadRequest                      | El cliente ha enviado una solicitud que el servicio no entiende o no admite.                                        |
| FeatureNotSupported             | Las características que usa esta inscripción no se admiten en esta cuenta.                                        |
| EnrollmentRestrictionsEnforced  | Las restricciones de inscripción que ha configurado el administrador han bloqueado esta inscripción.                                          |
| ClientDisconnected              | El cliente ha agotado el tiempo de espera o el usuario final ha anulado la inscripción.                                                        |
| UserAbandonment                 | El usuario final ha anulado la inscripción. (El usuario final ha iniciado la inscripción, pero no se ha completado de manera oportuna).  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
La entidad **EnrollmentFailureReason** indica un motivo más detallado para el error de inscripción de un dispositivo dentro de una categoría de error determinada.  

| Propiedad                     | Descripción                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | Identificador único del motivo del error de la inscripción en el almacenamiento de datos (clave suplente).  |
| enrollmentFailureReasonName  | Nombre del motivo del error de la inscripción. Vea los ejemplos siguientes.                            |

### <a name="example"></a>Ejemplo

| enrollmentFailureReasonName      | Descripción                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| No aplicable                   | El motivo del error de la inscripción no es aplicable.                                                                                                                                                       |
| No disponible                    | El motivo del error de la inscripción no está disponible.                                                                                                                                                        |
| Unknown                          | Error desconocido.                                                                                                                                                                                         |
| UserNotLicensed                  | No se ha encontrado al usuario en Intune o no tiene una licencia válida.                                                                                                                                     |
| UserUnknown                      | No se conoce al usuario en Intune.                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | Solo un usuario puede inscribir un dispositivo. Otro usuario ha inscrito este dispositivo anteriormente.                                                                                                                |
| EnrollmentOnboardingIssue        | La entidad de administración de dispositivos móviles (MDM) de Intune aún no se ha configurado.                                                                                                                                 |
| AppleChallengeIssue              | La instalación del perfil de administración de iOS se ha retrasado o se ha producido un error.                                                                                                                                         |
| AppleOnboardingIssue             | Se necesita un certificado push MDM de Apple para inscribir en Intune.                                                                                                                                       |
| DeviceCap                        | El usuario ha intentado inscribir más dispositivos que el máximo permitido.                                                                                                                                        |
| AuthenticationRequirementNotMet  | El servicio de inscripción de Intune no pudo autorizar esta solicitud.                                                                                                                                            |
| UnsupportedDeviceType            | El dispositivo no cumple los requisitos mínimos para la inscripción en Intune.                                                                                                                                  |
| EnrollmentCriteriaNotMet         | No se pudo inscribir este dispositivo debido a una regla de restricción de inscripción configurada.                                                                                                                          |
| BulkDeviceNotPreregistered       | No se han encontrado el identificador de equipo móvil internacional (IMEI) o el número de serie del dispositivo.  Sin este identificador, los dispositivos se reconocen como dispositivos personales que están bloqueados.  |
| FeatureNotSupported              | El usuario ha intentado acceder a una característica que todavía no está disponible para todos los clientes o no es compatible con la configuración de Intune.                                                            |
| UserAbandonment                  | El usuario final ha anulado la inscripción. (El usuario final ha iniciado la inscripción, pero no se ha completado de manera oportuna).                                                                                           |
| APNSCertificateExpired           | No se pueden administrar dispositivos de Apple con un certificado push MDM de Apple expirado.                                                                                                                            |
## <a name="ownertypes"></a>OwnerTypes

La entidad **EnrollmentTypes** indica si el dispositivo es corporativo, personal o desconocido.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| ownerTypeID |Identificador único del tipo de propietario. | |
| ownerTypeKey |Identificador único del tipo de propietario en el almacenamiento de datos. Clave suplente. | |
| ownerTypeName |Representa el tipo de propietario de los dispositivos:  <br>Corporativo: dispositivo es propiedad de la empresa. <br>Personal: el dispositivo es de propiedad personal (BYOD).  <br>Desconocido: no hay información sobre este dispositivo. |Empresa Personal desconocido |

> [!Note]  
> Para el `ownerTypeName` en Azure AD al crear grupos dinámicos para los dispositivos, deberá establecer el valor de filtro `deviceOwnership` como `Company`. Para obtener más información, consulte [reglas para dispositivos](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="managementstates"></a>ManagementStates

La entidad **ManagementStates** proporciona detalles sobre el estado del dispositivo. Los detalles pueden ser útiles en los casos en los que se aplican acciones remotas o el dispositivo se ha liberado o modificado.

| Propiedad  | Descripción |
|---------|------------|
| managementStateID | Identificador único del estado de administración. |
| managementStateKey | Identificador único del estado de administración en el almacenamiento de datos. Clave suplente. |
| managementStateName | Indica el estado de la acción remota aplicada a este dispositivo. |

### <a name="example"></a>Ejemplo

| managementStateID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Administrados | Administrado sin acciones remotas pendientes. |
| 1 |RetirePending | Hay un comando de retirada pendiente para el dispositivo. |
| 2 |RetireFailed | Se ha producido un error en el comando de retirada en el dispositivo. |
| 3 |WipePending | Hay un comando de borrado pendiente para el dispositivo. |
| 4 |WipeFailed | Se ha producido un error en el comando de borrado en el dispositivo. |
| 5 |Incorrecto | Estado incorrecto. |
| 6 |DeletePending | Hay un comando de eliminación pendiente para el dispositivo. |
| 7 |RetireIssued | Se ha emitido un comando de retirada en el dispositivo. |
| 8 |WipeIssued | Se ha emitido un comando de borrado. |
| 9 |WipeCanceled | Se ha cancelado un comando de borrado. |
| 10 |RetireCanceled | Se ha cancelado un comando de retirada. |
| 11 |Discovered | Intune acaba de detectar el dispositivo. Una vez que se ha registrado por primera vez, se mueve al estado administrado. |

## <a name="managementagenttypes"></a>ManagementAgentTypes

La entidad **ManagementAgentTypes** representa los agentes usados para administrar un dispositivo.

| Propiedad  | Descripción |
|---------|------------|
| ManagementAgentTypeID | Identificador único del tipo de agente de administración. |
| ManagementAgentTypeKey | Identificador único del tipo de agente de administración en el almacenamiento de datos. Clave suplente. |
| ManagementAgentTypeName |Indica qué tipo de agente se usa para administrar el dispositivo. |

### <a name="example"></a>Ejemplo

| ManagementAgentTypeID  | Nombre | Descripción |
|---------|------------|--------|
| 1 |EAS | El dispositivo se administra a través de Exchange Active Sync. |
| 2 |MDM | El dispositivo se administra mediante un agente MDM. |
| 3 |EasMdm | El dispositivo se administra mediante Exchange Active Sync y un agente MDM. |
| 4 |IntuneClient | El dispositivo se administra mediante el agente del equipo de Intune. |
| 5 |EasIntuneClient | El dispositivo se administra mediante Exchange Active Sync y el agente del equipo de Intune. |
| 8 |ConfigManagerClient | El dispositivo se administra mediante el agente de System Center Configuration Manager. |
| 16 |Unknown | Tipo de agente de administración desconocido. |

## <a name="devices"></a>Dispositivos

La entidad **Devices** muestra todos los dispositivos inscritos en administración y sus propiedades correspondientes.

| Propiedad  | Descripción |
|---------|------------|
| DeviceKey | Identificador único del dispositivo en el almacenamiento de datos. Clave suplente. |
| DeviceId | Identificador único del dispositivo. |
| DeviceName | Nombre del dispositivo en plataformas que permiten asignar nombre a un dispositivo. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos. |
| DeviceTypeKey | Clave del atributo de tipo de dispositivo para este dispositivo. |
| OwnerTypeKey | Clave del atributo de tipo de propietario para este dispositivo: corporativo, personal o desconocido. |
| objectSourceKey | Ignore esta columna. |
| ManagementAgentKey | Clave del agente de administración asociado a este dispositivo. |
| ManagementStateKey | Clave del estado de administración asociado a este dispositivo, que indica el estado más reciente de una acción remota o si estaba liberado o modificado. |
| OSVersion | Versión del sistema operativo |
| OSMajorVersion | Componente de versión principal de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| OSMinorVersion | Componente de versión secundaria de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| OSBuildNumber | Componente de versión de compilación de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| OSRevisionNumber | Componente de versión de revisión de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| SerialNumber | Número de serie del dispositivo, si está disponible. |
| RowLastModifiedDateTimeUTC | Fecha y hora de la última modificación de este registro. |
| DeviceAction | Última acción de dispositivo emitida. Ignórela por el momento. |
| Fabricante | Fabricante del dispositivo. |
| Modelo | Modelo del dispositivo. |
| IsDeleted | Establecido en True si el dispositivo ya no se administra mediante Intune. Conserva el último estado conocido. |
| AndroidSecurityPatchLevel |La fecha de la revisión de seguridad más reciente del dispositivo. |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

La entidad **DevicePropertyHistory** tiene las mismas propiedades que las tablas de dispositivos y las instantáneas diarias de cada registro de dispositivo por día de los últimos 90 días. La columna DateKey indica el día de cada fila.

| Propiedad  | Descripción |
|---------|------------|
| DateKey |Referencia a la tabla de fechas que indica el día. |
| DeviceKey |Identificador único del dispositivo en el almacenamiento de datos. Clave suplente. Se trata de una referencia a la tabla de dispositivos que contiene el identificador de dispositivo de Intune. |
| DeviceName |Nombre del dispositivo en plataformas que permiten asignar nombre a un dispositivo. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos. |
| OwnerTypeKey |Clave del atributo de tipo de propietario para este dispositivo: corporativo, personal o desconocido. |
| objectSourceKey |Ignore esta columna. |
| ManagementStateKey |Clave del estado de administración asociado a este dispositivo, que indica el estado más reciente de una acción remota o si estaba liberado o modificado. |
| OSVersion |Versión del SO. |
| OSMajorVersion |Componente de versión principal de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| OSMinorVersion |Componente de versión secundaria de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| OSBuildNumber |Componente de versión de compilación de la versión del sistema operativo (principal.secundaria.compilación.revisión). |
| DeviceAction |Última acción de dispositivo emitida. Ignórela por el momento. |

## <a name="applicationinventory"></a>ApplicationInventory

La entidad **ApplicationInventory** muestra las aplicaciones que se encuentran en el dispositivo en el momento de recopilación del inventario.


|      Propiedad      |                       Descripción                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              Referencia a la tabla de dispositivos.               |
|   ApplicationKey   | ? (copiado de ExchangeDeviceService\DeviceApplication). |
|  ApplicationName   | ? (copiado de ExchangeDeviceService\DeviceApplication). |
| ApplicationVersion | ? (copiado de ExchangeDeviceService\DeviceApplication). |
|     BundleSize     | ? (copiado de ExchangeDeviceService\DeviceApplication). |

