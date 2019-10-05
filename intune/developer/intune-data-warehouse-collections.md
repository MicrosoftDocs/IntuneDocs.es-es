---
title: Colecciones de almacenamiento de datos de Intune
titleSuffix: Microsoft Intune
description: Las colecciones de almacenamiento de datos de Intune proporcionan detalles relacionados con la API de almacenamiento de datos.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 29f09230-dc56-43db-b599-d961967bda49
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb470885be8f09f0c99dfe26a1d982570644ac8a
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733535"
---
# <a name="intune-data-warehouse-collections"></a>Colecciones de almacenamiento de datos de Intune

Las siguientes colecciones de almacenamiento de datos de Intune proporcionan propiedades, descripciones y ejemplos de las colecciones v1.0 de las entidades de API de almacenamiento de datos. 

## <a name="apprevisions"></a>appRevisions
La entidad **appRevision** muestra todas las versiones de las aplicaciones.

|          Propiedad          |                                      Descripción                                      |                Ejemplo               |
|:--------------------------:|:-------------------------------------------------------------------------------------:|:------------------------------------:|
| AppKey                     | Identificador único de la aplicación.                                                         | 123                                  |
| ApplicationId              | Identificador único de la aplicación. Se parece a AppKey, pero es una clave natural.        | b66bc706-ffff-7437-0340-032819502773 |
| Revisión                   | Versión tal como la indicó el administrador durante la carga del archivo binario.                   | 2                                    |
| Título                      | Título de la aplicación.                                                                     | Excel                                |
| Publicador                  | Editor de la aplicación.                                                                 | Microsoft                            |
| UploadState                | Estado de carga de la aplicación.                                                              | 1                                    |
| AppTypeKey                 | Referencia a AppType descrita en la sección siguiente.                            | 1                                    |
| VppProgramTypeKey          | Referencia a VppProgramType descrita a continuación.                                        | 30876                                |
| CreationTime               | La hora de creación de esta revisión.                                            | 23/11/2016 0:00                      |
| ModifiedTime               | Hora de la última modificación de cualquier elemento relacionado con esta revisión.                            | 23/11/2016 0:00                      |
| Tamaño                       | Tamaño del archivo binario en bytes.                                                          | 120,392,000                          |
| StartDateInclusiveUTC      | Fecha y hora en formato UTC en que se ha creado esta revisión de la aplicación en el almacenamiento de datos.      | 23/11/2016 0:00                      |
| EndDateExclusiveUTC        | Fecha y hora en formato UTC en que ha quedado obsoleta esta revisión de la aplicación.                        | 23/11/2016 0:00                      |
| IsCurrent                  | Indica si esta versión de la aplicación está actualizada o no en el almacenamiento de datos.         | Verdadero/Falso                           |
| RowLastModifiedDateTimeUTC | Fecha y hora en formato UTC en que se ha modificado por última vez esta versión de la aplicación en el almacenamiento de datos. | 23/11/2016 0:00                      |

## <a name="apptypes"></a>appTypes
La entidad **appTypes** muestra el origen de instalación de una aplicación.

|   Propiedad  |        Descripción        |
|:-----------:|:-------------------------:|
| AppTypeID   | Identificador del tipo.           |
| AppTypeKey  | Clave suplente de la clave. |
| AppTypeName | Tipo de aplicación                  |

### <a name="example"></a>Ejemplo

| AppTypeID |                Nombre               |                     Descripción                     |
|:---------:|:---------------------------------:|:---------------------------------------------------:|
| 0         | Aplicación de la tienda Android               | Una aplicación de la tienda Android.                             |
| 1         | Aplicación de LOB de Android                 | Una aplicación de línea de negocio de Android.                  |
| 2         | Aplicación administrada de la tienda Android (MAM) | Una aplicación de la tienda Android habilitada para la administración. |
| 3         | Aplicación de la tienda iOS                   | Una aplicación de la tienda iOS.                                 |
| 4         | Aplicación de LOB de iOS                     | Una aplicación de línea de negocio de iOS.                      |
| 5         | Aplicación administrada de la tienda iOS (MAM)     | Una aplicación de la tienda iOS habilitada para la administración.       |
| 6         | Conjunto de aplicaciones de O365 ProPlus             | El conjunto de aplicaciones de Office 365 ProPlus para Windows 10.     |
| 7         | Aplicación web                         | Una aplicación web.                                        |
| 8         | Aplicación de la Tienda Windows Phone 8.1     | Una aplicación de la Tienda Windows Phone 8.1.                    |
| 9         | Aplicación de la Tienda Windows               | Una aplicación de la Tienda Windows.                              |
| 10        | Aplicaciones de LOB de Windows                | Una aplicación de línea de negocio AppX de Windows.              |
| 11        | MSI para Windows Mobile              | Una aplicación de línea de negocio de MSI.                      |
| 12        | Aplicación de línea de negocio de Windows Phone           | Una aplicación de línea de negocio de Windows Phone.             |

## <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities
En la tabla siguiente se resume el estado de asignación de directivas de cumplimiento a dispositivos. Muestra el número de dispositivos que hay en cada estado de cumplimiento.

|    Propiedad   |                                                                                      Descripción                                                                                     |  Ejemplo |
|:-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey       | Clave de fecha del momento en el que se creó el resumen de la directiva de cumplimiento.                                                                                                                   | 20161204 |
| Unknown       | Número de dispositivos sin conexión o que no se pudieron comunicar con Intune o Azure AD por otros motivos.                                                                           | 5        |
| No aplicable | Número de dispositivos a los que no se aplican las directivas de cumplimiento de dispositivos asignadas por el administrador.                                                                                     | 201      |
| Conforme     | Número de dispositivos con una o varias directivas de cumplimiento de dispositivos asignadas por el administrador aplicadas correctamente.                                                                        | 4083     |
| En período de gracia | Número de dispositivos que no son conformes, pero que se encuentran en el período de gracia definido por el administrador.                                                                                  | 57       |
| No conforme  | Número de dispositivos a los que no se pudo aplicar una o varias directivas de cumplimiento de dispositivos asignadas por el administrador o en los que el usuario no ha cumplido las directivas asignadas por el administrador. | 43       |
|    Error      |    Número de dispositivos que no se pudieron comunicar con Intune o Azure AD y devolvieron un mensaje de error.                                                                          |    3     |

## <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities
La siguiente tabla resume el estado de asignación de directivas de cumplimiento a dispositivos por directiva y por tipo de directiva. Muestra el número de dispositivos que hay en cada estado de cumplimiento para cada directiva de cumplimiento asignada.

|      Propiedad     |                                                                                      Descripción                                                                                     |  Ejemplo |
|:-----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey           | Clave de fecha del momento en el que se creó el resumen de la directiva de cumplimiento.                                                                                                                   | 20161219 |
| PolicyKey         | Clave de la directiva de cumplimiento para la que se ha creado el resumen.                                                                                                                   | 10178    |
| PolicyPlatformKey | Clave del tipo de plataforma de la directiva de cumplimiento para la que se ha creado el resumen.                                                                                            | 5        |
| Unknown           | Número de dispositivos sin conexión o que no se pudieron comunicar con Intune o Azure AD por otros motivos.                                                                           | 13       |
| No aplicable     | Número de dispositivos a los que no se aplican las directivas de cumplimiento de dispositivos asignadas por el administrador.                                                                                     | 3        |
| Conforme         | Número de dispositivos con una o varias directivas de cumplimiento de dispositivos asignadas por el administrador aplicadas correctamente.                                                                        | 45       |
| En período de gracia     | Número de dispositivos que no son conformes, pero que se encuentran en el período de gracia definido por el administrador.                                                                                  | 3        |
| No conforme      | Número de dispositivos a los que no se pudo aplicar una o varias directivas de cumplimiento de dispositivos asignadas por el administrador o en los que el usuario no ha cumplido las directivas asignadas por el administrador. | 7        |
| Error             | Número de dispositivos que no se pudieron comunicar con Intune o Azure AD y devolvieron un mensaje de error.                                                                             | 3        |
## <a name="compliancestates"></a>complianceStates

|      Propiedad      |                       Descripción                      |
|:------------------:|:------------------------------------------------------:|
| complianceStatus   | Estado de cumplimiento de dispositivos con mdmStatusKey       |
| complianceStateKey | Clave de cumplimiento que debe coincidir con el dispositivo y el estado de cumplimiento |
| complianceStateID  | El identificador que debe coincidir con este estado de cumplimiento                |

### <a name="example"></a>Ejemplo

|  complianceStatus  |                       Descripción                      |
|:------------------:|:------------------------------------------------------:|
|    Unknown         |    Desconocido.                                                                        |
|    Conforme       |    Conforme.                                                                      |
|    No conforme    |       Dispositivo no conforme y con acceso bloqueado a los recursos corporativos.             |
|    Conflicto        |    Conflicto con otras reglas.                                                      |
|    Error           |       Error.                                                                       |
|    ConfigManager   |    Administrado por el Administrador de configuración.                                                      |
|    En período de gracia   |       Dispositivo no conforme pero aún con acceso a los recursos corporativos          |

## <a name="dates"></a>fechas
La entidad **date** representa fechas a las que se hace referencia en varias entidades de almacenamiento de datos.

|     Propiedad    |                       Descripción                      |    Ejemplo    |
|:---------------:|:------------------------------------------------------:|:-------------:|
| DateKey         | Identificador único de esta fecha en el almacenamiento de datos. | 20160703      |
| FullDate        | Esta fecha representada en formato completo de fecha y hora.        | 3/7/2016 0:00 |
| DayOfWeek       | Día de la semana.                                            | 1             |
| DayOfMonth      | Día del mes.                                           | 3             |
| DayOfYear       | Día del año.                                            | 185           |
| WeekOfYear      | Semana del año.                                           | 28            |
| MonthOfYear     | Mes del año.                                      | 7             |
| CalendarQuarter | Trimestre natural.                                       | 3             |
| CalendarYear    | Año natural.                                          | 2016          |
| DateKey         | Identificador único de esta fecha en el almacenamiento de datos. | 20160703      |
| FullDate        | Esta fecha representada en formato completo de fecha y hora.        | 3/7/2016 0:00 |
| DayOfWeek       | Día de la semana.                                            | 1             |
| DayOfMonth      | Día del mes.                                           | 3             |
| DayOfYear       | Día del año.                                            | 185           |
| WeekOfYear      | Semana del año.                                           | 28            |
| MonthOfYear     | Mes del año.                                      | 7             |
| CalendarQuarter | Trimestre natural.                                       | 3             |
| CalendarYear    | Año natural.                                          | 2016          |

## <a name="devicecategories"></a>deviceCategories

|      Propiedad      |                                    Descripción                                   |                Ejemplo               |
|:------------------:|:--------------------------------------------------------------------------------:|:------------------------------------:|
| deviceCategoryID   | Identificador único de la categoría del dispositivo.                                       | fb415ba2-7c08-41f6-a5e5-685b50da2c4c |
| deviceCategoryKey  | Identificador único de la categoría del dispositivo en el almacenamiento de datos. Clave suplente. | 1                                    |
| deviceCategoryName | Nombre para mostrar de la categoría del dispositivo.                                            | Smartphones                          |

## <a name="deviceconfigurationprofiledeviceactivities"></a>deviceConfigurationProfileDeviceActivities
La entidad **DeviceConfigurationProfileDeviceActivity** muestra el número de dispositivos con estado correcto, estado pendiente, estado con errores o estado de error por día. El número refleja los perfiles de configuración de dispositivos asignados a la entidad. Por ejemplo, si un dispositivo muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un dispositivo tiene dos perfiles asignados, uno con el estado correcto y otro con el estado de error, la entidad aumenta el contador de éxitos y coloca el dispositivo en el estado de error. La entidad indica qué número de dispositivos se encuentra en cada estado en un día determinado de los últimos 30 días.

|  Propiedad |                                          Descripción                                          |  Ejemplo |
|:---------:|:---------------------------------------------------------------------------------------------:|:--------:|
| DateKey   | Clave de fecha en la que se registró la inserción en el repositorio del perfil de configuración de dispositivos en el almacenamiento de datos. | 20160703 |
| Pending   | Número de dispositivos únicos en estado pendiente.                                                    | 123      |
| Correcto | Número de dispositivos únicos en estado correcto.                                                    | 12       |
| Error     | Número de dispositivos únicos en estado de error.                                                      | 10       |
| Failed    | Número de dispositivos únicos en estado con errores.                                                     | 2        |

## <a name="deviceconfigurationprofileuseractivities"></a>deviceConfigurationProfileUserActivities 
La entidad **DeviceConfigurationProfileUserActivity** muestra el número de usuarios con estado correcto, pendiente, con errores o de error al día. El número refleja los perfiles de configuración de dispositivos asignados a la entidad. Por ejemplo, si un usuario muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un usuario tiene dos perfiles asignados, uno en estado correcto y otro en estado de error, se cuenta el usuario en el estado de error. La entidad **DeviceConfigurationProfileUserActivity** muestra cuántos usuarios hay en cada estado en un día determinado de los últimos 30 días. 

| Propiedad  | Descripción  | Ejemplo  |
|------------|----------------------------------------------------------------------------------------------|-----------|
| DateKey  | Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro del perfil de configuración de dispositivos.  | 20160703  |
| Pending  | Número de usuarios únicos en estado pendiente.  | 123  |
| Correcto  | Número de usuarios únicos en estado correcto.  | 12  |
| Error  | Número de usuarios únicos en estado de error.  | 10  |
| Failed  | Número de usuarios únicos en estado con errores.  | 2  |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

|          Propiedad          |                                                                                      Descripción                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | Referencia a la tabla de fechas que indica el día.                                                                                                                                          |
| DeviceKey                  | Identificador único del dispositivo en el almacenamiento de datos. Clave suplente. Es una referencia a la tabla de dispositivos que contiene el identificador de dispositivo de Intune.                               |
| DeviceName                 | Nombre del dispositivo en plataformas que permiten asignar nombres a dispositivos. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos. |
| DeviceRegistrationStateKey | Clave del atributo de estado de registro para este dispositivo.                                                                                                                    |
| OwnerTypeKey               | Clave del atributo de tipo de propietario de este dispositivo: corporativo, personal o desconocido.                                                                                                  |
| ManagementStateKey         | Clave del estado de administración asociada a este dispositivo, que indica el estado más reciente de una acción remota o si estaba liberado o modificado.                                                |
| AzureADRegistered          | Si el dispositivo está registrado en Azure Active Directory.                                                                                                                             |
| ComplianceStateKey         | Clave de ComplianceState.                                                                                                                                                            |
| OSVersion                  | Versión del SO.                                                                                                                                                                          |
| JailBroken                 | Si el dispositivo está liberado.                                                                                                                                         |
| DeviceCategoryKey          | Clave del atributo de categoría de dispositivo para este dispositivo.                                                                                                                                    |
## <a name="deviceregistrationstates"></a>deviceRegistrationStates
La entidad **DeviceRegistrationState** representa el tipo de registro al que hacen referencia otras colecciones de almacenamiento de datos. 

|           Propiedad          |                                     Descripción                                     |
|:---------------------------:|:-----------------------------------------------------------------------------------:|
| deviceRegistrationStateID   | Identificador único del estado de registro.                                            |
| deviceRegistrationStateKey  | Identificador único del estado de registro en el almacenamiento de datos. Clave suplente. |
| deviceRegistrationStateName | Estado de registro.                                                                  |
|    NotRegistered                     |    No registrado.                                                                                                                                                                  |
|    Registrado                        |       Registrado                                                                                                                                                                   |
|    Revoked                           |       El estado significa que el administrador de TI ha bloqueado al cliente y el cliente se puede desbloquear. Un dispositivo también puede encontrarse en estado revocado después de que se haya borrado o retirado.        |
|    KeyConflict                       |    Conflicto de clave.                                                                                                                                                                    |
|    ApprovalPending                   |    Pendiente de aprobación.                                                                                                                                                                |
|    CertificateReset                  |    Certificado establecido.                                                                                                                                                               |
|    NotRegisteredPendingEnrollment    |    No registrado y pendiente de inscripción.                                                                                                                                               |
|    Unknown                           |    Estado desconocido.                                                                                                                                                                   |

## <a name="devices"></a>dispositivos
La entidad **device** muestra todos los dispositivos inscritos en administración y sus propiedades correspondientes.

|          Propiedad          |                                                                                       Descripción                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | Identificador único del dispositivo en el almacenamiento de datos. Clave suplente.                                                                                                               |
| DeviceId                   | Identificador único del dispositivo.                                                                                                                                                     |
| DeviceName                 | Nombre del dispositivo en plataformas que permiten asignar nombres a dispositivos. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos. |
| DeviceTypeKey              | Clave del atributo de tipo de dispositivo de este dispositivo.                                                                                                                                    |
| DeviceRegistrationState    | Clave del atributo de estado de registro de cliente de este dispositivo.                                                                                                                      |
| OwnerTypeKey               | Clave del atributo de tipo de propietario de este dispositivo: corporativo, personal o desconocido.                                                                                                    |
| EnrolledDateTime           | Fecha y hora en que se inscribió este dispositivo.                                                                                                                                         |
| LastSyncDateTime           | Última inserción conocida del dispositivo en el repositorio con Intune.                                                                                                                                              |
| ManagementAgentKey         | Clave del agente de administración asociada a este dispositivo.                                                                                                                             |
| ManagementStateKey         | Clave del estado de administración asociada a este dispositivo, que indica el estado más reciente de una acción remota o si estaba liberado o modificado.                                                |
| AzureADDeviceId            | El valor de deviceID de Azure para este dispositivo.                                                                                                                                                  |
| AzureADRegistered          | Si el dispositivo está registrados en Azure Active Directory.                                                                                                                             |
| DeviceCategoryKey          | Clave de la categoría asociada a este dispositivo.                                                                                                                                     |
| DeviceEnrollmentType       | Clave del tipo de inscripción asociada a este dispositivo, que indica el método de inscripción.                                                                                             |
| ComplianceStateKey         | Clave del estado de cumplimiento de normas asociada a este dispositivo.                                                                                                                             |
| OSVersion                  | Versión de sistema operativo del dispositivo                                                                                                                                                |
| EasDeviceId                | Identificador de Exchange ActiveSync del dispositivo.                                                                                                                                                  |
| SerialNumber               | SerialNumber                                                                                                                                                                           |
| UserId                     | Identificador único para el usuario asociado al dispositivo.                                                                                                                           |
| RowLastModifiedDateTimeUTC | Fecha y hora en formato UTC en que se modificó por última vez este dispositivo en el almacenamiento de datos.                                                                                                       |
| Fabricante               | Fabricante del dispositivo.                                                                                                                                                             |
| Modelo                      | Modelo del dispositivo.                                                                                                                                                                    |
| OperatingSystem            | Sistema operativo del dispositivo. Windows, iOS, etc.                                                                                                                                   |
| IsDeleted                  | Archivo binario para mostrar si el dispositivo se ha eliminado o no.                                                                                                                                 |
| AndroidSecurityPatchLevel  | Nivel de revisión de seguridad de Android                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| IsSupervised               | Estado del dispositivo supervisado                                                                                                                                                               |
| FreeStorageSpaceInBytes    | Almacenamiento libre en bytes.                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | Almacenamiento total en bytes.                                                                                                                                                                |
| EncryptionState            | Estado de cifrado en el dispositivo                                                                                                                                                      |
| SubscriberCarrier          | Operador del suscriptor del dispositivo                                                                                                                                                       |
| PhoneNumber                | Número de teléfono del dispositivo                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | Tecnología de datos móviles del dispositivo                                                                                                                                                    |
| WiFiMacAddress             | MAC Wi-Fi                                                                                                                                                                              |


## <a name="devicetypes"></a>DeviceTypes
La entidad **deviceType** representa el tipo de dispositivo al que hacen referencia otras entidades de almacenamiento de datos. Normalmente, el tipo de dispositivo describe el modelo del dispositivo, el fabricante o una combinación de ambos.

|    Propiedad    |                                  Descripción                                 |
|:--------------:|:----------------------------------------------------------------------------:|
| DeviceTypeID   | Identificador único del tipo de dispositivo                                       |
| DeviceTypeKey  | Identificador único del tipo de dispositivo en el almacenamiento de datos. Clave suplente. |
| DeviceTypeName | Tipo de dispositivo                                                                |

### <a name="example"></a>Ejemplo

| deviceTypeID |        Nombre       |                      Descripción                      |
|:------------:|:-----------------:|:-----------------------------------------------------:|
| -1           | No disponible   | El tipo de dispositivo no está disponible.                     |
| 0            | Escritorio           | Dispositivo de escritorio de Windows                              |
| 1            | Windows           | Dispositivo Windows                                      |
| 2            | WinMO6            | Dispositivo Windows Mobile 6.0                           |
| 3            | Nokia             | Dispositivo Nokia                                        |
| 4            | WindowsPhone      | Dispositivo Windows Phone                                |
| 5            | Mac               | Dispositivo Mac                                          |
| 6            | WinCE             | Dispositivo Windows CE                                   |
| 7            | WinEmbedded       | Dispositivo Windows Embedded                             |
| 8            | IPhone            | Dispositivo iPhone                                       |
| 9            | IPad              | Dispositivo iPad                                         |
| 10           | IPod              | Dispositivo iPod                                         |
| 11           | Android           | Dispositivo Android administrado mediante el Administrador de dispositivos   |
| 12           | ISocConsumer      | Dispositivo iSoc Consumer                                |
| 13           | Unix              | Dispositivo UNIX                                         |
| 14           | MacMDM            | Dispositivo Mac OS X administrado con el agente MDM integrado |
| 15           | HoloLens          | Dispositivo HoloLens                                       |
| 16           | SurfaceHub        | Dispositivo Surface Hub                                  |
| 17           | AndroidForWork    | Dispositivo Android administrado mediante el propietario con perfil Android  |
| 18           | AndroidEnterprise | Dispositivo Android Enterprise                          |
| 100          | BlackBerry        | Dispositivo BlackBerry                                   |
| 101          | Palm              | Dispositivo Palm                                         |
| 255          | Unknown           | Tipo de dispositivo desconocido                                 |

## <a name="deviceenrollmenttypes"></a>deviceEnrollmentTypes
La entidad **deviceEnrollmentType** indica cómo se ha inscrito un dispositivo. El tipo de inscripción captura el método de inscripción. En los ejemplos se muestran los diferentes tipos de inscripción y su significado.

|         Propiedad         |                                    Descripción                                    |
|:------------------------:|:---------------------------------------------------------------------------------:|
| deviceEnrollmentTypeID   | Identificador único del tipo de inscripción.                                       |
| deviceEnrollmentTypeKey  | Identificador único del tipo de propietario en el almacenamiento de datos. Clave suplente. |
| deviceEnrollmentTypeName | Nombre del tipo de inscripción.                                                           |

### <a name="example"></a>Ejemplo

| enrollmentTypeID |                Nombre                |                                        Descripción                                       |
|:----------------:|:----------------------------------:|:----------------------------------------------------------------------------------------:|
| 0                | Unknown                            | No se recopiló el tipo de inscripción                                                      |
| 1                | UserEnrollment                     | Inscripción basada en el usuario mediante el canal BYOD.                                           |
| 2                | DeviceEnrollmentManager            | Inscripción del usuario con una cuenta de administrador de inscripción de dispositivos.                              |
| 3                | AppleBulkWithUser                  | Inscripción masiva de Apple con desafío de usuario. (DEP, Apple Configurator)                   |
| 4                | AppleBulkWithoutUser               | Inscripción masiva de Apple sin desafío de usuario.   (DEP, Apple Configurator, configuración móvil) |
| 5                | WindowsAzureADJoin                 | Unión a Azure AD de Windows 10.                                                                |
| 6                | WindowsBulkUserless                | Inscripción masiva de Windows 10 mediante ICD con certificado.                               |
| 7                | WindowsAutoEnrollment              | Inscripción automática de Windows 10.   (Agregar cuenta del trabajo)                                    |
| 8                | WindowsBulkAzureDomainJoin         | Unión masiva a Azure AD de Windows 10.                                                           |
| 9                | WindowsCoManagement                | Administración conjunta de Windows 10 desencadenada por AutoPilot o directiva de grupo.                       |
| 10               | WindowsAzureADJoinsUsingDeviceAuth | Unión a Azure AD de Windows 10 mediante autorización de dispositivos.                                            |

## <a name="enrollmentactivities"></a>enrollmentActivities 
La entidad **EnrollmentActivity** indica la actividad de una inscripción de dispositivos.

| Propiedad                      | Descripción                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | Clave de la fecha en la que se ha registrado esta actividad de inscripción.               |
| deviceEnrollmentTypeKey       | Clave del tipo de inscripción.                                        |
| deviceTypeKey                 | Clave del tipo de dispositivo.                                                |
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
| UserAbandonment                 | El usuario final ha abandonado la inscripción. (El usuario final ha iniciado la inscripción, pero no se ha completado de manera oportuna).  |

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
| UserAbandonment                  | El usuario final ha abandonado la inscripción. (El usuario final ha iniciado la inscripción, pero no se ha completado de manera oportuna).                                                                                           |
| APNSCertificateExpired           | No se pueden administrar dispositivos de Apple con un certificado push MDM de Apple expirado.                                                                                                                            |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions
**IntuneManagementExtension** muestra el mantenimiento de **intuneManagementExtension** de cada dispositivo Windows 10 cada día. Los datos se conservan durante 60 días.

|       Propiedad      |                          Descripción                          | Ejemplo |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| DateKey             | Identificador único de la fecha.                                | 123     |
| TenantKey           | Identificador único del inquilino.                              | 456     |
| DeviceKey           | Identificador único del dispositivo.                              | 789     |
| ExtensionVersionKey | Identificador único de la versión de IntuneManagementExtension. | 1       |
| ExtensionStateKey   | Identificador único del estado de mantenimiento.                            | 2       |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates
**IntuneManagementExtensionHealthState** muestra todos los estados de mantenimiento posibles de **IntuneManagementExtension**.

|      Propiedad     |                   Descripción                  | Ejemplo |
|:-----------------:|:----------------------------------------------:|:-------:|
| ExtensionStateKey | Identificador único del estado de mantenimiento.           | 2       |
| ExtensionState    | Estado de mantenimiento de una entidad IntuneManagementExtension. | Correcto |

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions
La entidad **IntuneManagementExtensionVersion** muestra todas las versiones usadas por **IntuneManagementExtension**.

|       Propiedad      |                          Descripción                          | Ejemplo |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| ExtensionVersionKey | Identificador único de la versión de IntuneManagementExtension. | 1       |
| ExtensionVersion    | Número de versión de 4 dígitos.                                   | 1.0.2.0 |

## <a name="mamapplications"></a>MamApplications

La entidad **MamApplication** muestra las aplicaciones de línea de negocio (LOB) que se administran mediante la administración de aplicaciones móviles (MAM) sin inscripción en la empresa.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| mamApplicationKey |Identificador único de la aplicación MAM. | 432 |
| mamApplicationName |Nombre de la aplicación MAM. |Nombre de ejemplo de la aplicación MAM |
| mamApplicationId |Identificador de la aplicación MAM. | 123 |
| IsDeleted |Indica si se ha actualizado el registro de la aplicación MAM. <br>True: la aplicación MAM tiene un nuevo registro con campos actualizados en esta tabla. <br>False: registro más reciente de esta aplicación MAM. |Verdadero/Falso |
| StartDateInclusiveUTC |Fecha y hora en formato UTC en que se ha creado esta aplicación MAM en el almacenamiento de datos. |23/11/2016 12:00:00 AM |
| DeletedDateUTC |Fecha y hora en formato UTC en que IsDeleted ha cambiado a True. |23/11/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Fecha y hora en formato UTC en que se ha modificado por última vez esta aplicación MAM en el almacenamiento de datos. |23/11/2016 12:00:00 AM |


## <a name="mamapplicationinstances"></a>MamApplicationInstances

La entidad **MamApplicationInstance** muestra las aplicaciones de administración de aplicaciones móviles (MAM) administradas como instancias singulares por usuario y dispositivo. Todos los usuarios y dispositivos enumerados en la entidad están protegidos, como si tuvieran al menos una directiva de MAM asignada.


|          Propiedad          |                                                                                                  Descripción                                                                                                  |               Ejemplo                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   ApplicationInstanceKey   |                                                               Identificador único de la instancia de la aplicación MAM en el almacenamiento de datos. Clave suplente.                                                                |                 123                  |
|           UserId           |                                                                              Identificador del usuario que tiene instalada esta aplicación MAM.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   ApplicationInstanceId    |                                              Identificador único de la instancia de la aplicación MAM. Se parece a ApplicationInstanceKey, pero el identificador es una clave natural.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | Identificador de la aplicación MAM para el que se creó esta instancia de la aplicación MAM.   | 23/11/2016 12:00:00 AM   |
|     ApplicationVersion     |                                                                                     Versión de esta aplicación MAM.                                                                                      |                  2                   |
|        CreatedDate         |                                                                 Fecha en la que se ha creado este registro de la instancia de la aplicación MAM. El valor puede ser NULL.                                                                 |        23/11/2016 12:00:00 AM        |
|          Plataforma          |                                                                          Plataforma del dispositivo en el que está instalada esta aplicación MAM.                                                                           |                  2                   |
|      PlatformVersion       |                                                                      Versión de la plataforma del dispositivo en el que está instalada esta aplicación MAM.                                                                       |                 2.2                  |
|         SdkVersion         |                                                                            Versión de SDK de MAM con la que se ha encapsulado esta aplicación MAM.                                                                            |                 3.2                  |
| mamDeviceId | Identificador de dispositivo al que está asociada la instancia de la aplicación MAM.   | 23/11/2016 12:00:00 AM   |
| mamDeviceType | Tipo de dispositivo al que está asociada la instancia de la aplicación MAM.   | 23/11/2016 12:00:00 AM   |
| mamDeviceName | Nombre de dispositivo al que está asociada la instancia de la aplicación MAM.   | 23/11/2016 12:00:00 AM   |
|         IsDeleted          | Indica si se ha actualizado el registro de la instancia de esta aplicación MAM. <br>True: la instancia de esta aplicación MAM tiene un nuevo registro con campos actualizados en esta tabla. <br>False: registro más reciente de la instancia de esta aplicación MAM. |              Verdadero/Falso              |
|   StartDateInclusiveUtc    |                                                              Fecha y hora en formato UTC en que se ha creado la instancia de esta aplicación MAM en el almacenamiento de datos.                                                               |        23/11/2016 12:00:00 AM        |
|       DeletedDateUtc       |                                                                             Fecha y hora en formato UTC en que IsDeleted ha cambiado a True.                                                                              |        23/11/2016 12:00:00 AM        |
| RowLastModifiedDateTimeUtc |                                                           Fecha y hora en formato UTC en que se ha modificado por última vez la instancia de esta aplicación MAM en el almacenamiento de datos.                                                            |        23/11/2016 12:00:00 AM        |

## <a name="mamcheckins"></a>MamCheckins

La entidad **MamCheckin** representa los datos recopilados cuando una instancia de la aplicación de administración de aplicaciones móviles (MAM) se ha registrado con el servicio de Intune. 

> [!Note]  
> Cuando una instancia de la aplicación se registra varias veces al día, el almacenamiento de datos la almacena como un único registro.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| DateKey |Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro de la aplicación MAM. | 20160703 |
| ApplicationInstanceKey |Clave de la instancia de la aplicación asociada a este registro de la aplicación MAM. | 123 |
| UserKey |Clave del usuario asociado a este registro de la aplicación MAM. | 4323 |
| mamApplicationKey |Clave de aplicación asociada con el registro de la aplicación MAM. | 432 |
| DeviceHealthKey |Clave de DeviceHealth asociada a este registro de la aplicación MAM. | 321 |
| PlatformKey |Representa la plataforma del dispositivo asociado a este registro de la aplicación MAM. |123 |
| LastCheckInDate |Fecha y hora en que se ha registrado por última vez esta aplicación MAM. El valor puede ser NULL. |23/11/2016 12:00:00 AM |

## <a name="mamdevicehealths"></a>MamDeviceHealths

La entidad **MamDeviceHealth** representa los dispositivos que tienen implementadas directivas de administración de aplicaciones móviles (MAM), incluso si están liberados.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| DeviceHealthKey |Identificador único del dispositivo y su mantenimiento asociado en el almacenamiento de datos. Clave suplente. |123 |
| DeviceHealth |Identificador único del dispositivo y su mantenimiento asociado. Es parecido a DeviceHealthKey, pero el identificador es una clave natural. |b66bc706-ffff-7777-0340-032819502773 |
| DeviceHealthName |Representa el estado del dispositivo. <br>No disponible: no hay información sobre este dispositivo. <br>Correcto: el dispositivo no está liberado. <br>Incorrecto: el dispositivo está liberado. |No disponible Correcto Incorrecto |
| RowLastModifiedDateTimeUtc |Fecha y hora en formato UTC en que se ha modificado por última vez el estado del dispositivo MAM específico en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="mamplatforms"></a>MamPlatforms

La entidad **MamPlatform** muestra nombres y tipos de plataforma en los que se ha instalado una aplicación de administración de aplicaciones móviles (MAM).


|          Propiedad          |                                    Descripción                                    |                         Ejemplo                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        PlatformKey         |     Identificador único de la plataforma en el almacenamiento de datos. Clave suplente.      |                           123                           |
|          Plataforma          | Identificador único de la plataforma. Se parece a PlatformKey, pero es una clave natural. |                           123                           |
|        PlatformName        |                                   Nombre de la plataforma.                                   | No disponible <br>Ninguno <br>Windows <br>iOS <br>Android. |
| RowLastModifiedDateTimeUtc | Fecha y hora en formato UTC en que se ha modificado por última vez esta plataforma en el almacenamiento de datos.  |                 23/11/2016 12:00:00 AM                  |

## <a name="managementagenttypes"></a>managementAgentTypes
La entidad **managementAgentTypes** representa los agentes usados para administrar un dispositivo.

|         Propiedad        |                                       Descripción                                       |
|:-----------------------:|:---------------------------------------------------------------------------------------:|
| ManagementAgentTypeID   | Identificador único del tipo de agente de administración.                                         |
| ManagementAgentTypeKey  | Identificador único del tipo de agente de administración en el almacenamiento de datos. Clave suplente. |
| ManagementAgentTypeName | Indica qué tipo de agente se usa para administrar el dispositivo.                              |

### <a name="example"></a>Ejemplo

| ManagementAgentTypeID |                Nombre               |                                  Descripción                                 |
|:---------------------:|:---------------------------------:|:----------------------------------------------------------------------------:|
| 1                     | EAS                               | El dispositivo se administra mediante Exchange Active Sync                         |
| 2                     | MDM                               | El dispositivo se administra mediante un agente MDM                                   |
| 3                     | EasMdm                            | El dispositivo se administra mediante Exchange Active Sync y un agente MDM        |
| 4                     | IntuneClient                      | El dispositivo se administra mediante el agente del equipo de Intune                               |
| 5                     | EasIntuneClient                   | El dispositivo se administra mediante Exchange Active Sync y el agente del equipo de Intune |
| 8                     | ConfigManagerClient               | El dispositivo se administra mediante el agente de System Center Configuration Manager     |
| 10                    | ConfigurationManagerClientMdm     | El dispositivo se administra mediante Configuration Manager y MDM.                    |
| 11                    | ConfigurationManagerCLientMdmEas  | El dispositivo se administra mediante Configuration Manager, MDM y Exchange Active Sync.               |
| 16                    | Unknown                           | Tipo de agente de administración desconocido                                              |
| 32                    | Jamf                              | Los atributos del dispositivo se capturan de Jamf.                               |
| 64                    | GoogleCloudDevicePolicyController |  El dispositivo se administra mediante CloudDPC de Google.                                 |

## <a name="managementstates"></a>managementStates
La entidad **ManagementStates** proporciona detalles sobre el estado del dispositivo. Los detalles pueden ser útiles en los casos en los que se aplican acciones remotas o el dispositivo se ha liberado o modificado.

|       Propiedad      |                                     Descripción                                    |
|:-------------------:|:----------------------------------------------------------------------------------:|
| managementStateID   | Identificador único del estado de administración.                                       |
| managementStateKey  | Identificador único del estado de administración en el almacenamiento de datos. Clave suplente. |
| managementStateName | Indica el estado de la acción remota aplicada a este dispositivo.                 |

### <a name="example"></a>Ejemplo

| managementStateID |      Nombre      |                                                   Descripción                                                   |
|:-----------------:|:--------------:|:---------------------------------------------------------------------------------------------------------------:|
| 0                 | Administrados        | Administrado sin acciones remotas pendientes.                                                                       |
| 1                 | RetirePending  | Hay un comando de retirada pendiente para el dispositivo.                                                             |
| 2                 | RetireFailed   | Se ha producido un error en el comando de retirada en el dispositivo.                                                                      |
| 3                 | WipePending    | Hay un comando de borrado pendiente para el dispositivo.                                                               |
| 4                 | WipeFailed     | Se ha producido un error en el comando de borrado en el dispositivo.                                                                        |
| 5                 | Incorrecto      | Estado incorrecto.                                                                                              |
| 6                 | DeletePending  | Hay un comando de eliminación pendiente para el dispositivo.                                                             |
| 7                 | RetireIssued   | Se ha emitido un comando de retirada en el dispositivo.                                                               |
| 8                 | WipeIssued     | Se ha emitido un comando de borrado.                                                                               |
| 9                 | WipeCanceled   | Se ha cancelado un comando de borrado.                                                                               |
| 10                | RetireCanceled | Se ha cancelado un comando de retirada.                                                                             |
| 11                | Discovered     | Intune acaba de detectar el dispositivo. Una vez que se ha registrado por primera vez, se mueve al estado administrado. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates
La entidad MobileAppInstallState representa el estado de instalación de una aplicación móvil una vez que se ha asignado a un grupo que contiene dispositivos, usuarios o ambos.

|       Propiedad      |                        Descripción                       |
|:-------------------:|:--------------------------------------------------------:|
| AppInstallStateKey  | El identificador único del estado de instalación de aplicación de su cuenta. |
| AppInstallState     | Valor de enumeración del estado de instalación de aplicación.                     |
| AppInstallStateName | Nombre del estado de instalación de aplicación.                           |

## <a name="mobileappinstallstatuscounts"></a>mobileAppInstallStatusCounts
Representa el estado de instalación de una aplicación móvil para un tipo de dispositivo de destino dado mediante la administración de aplicaciones móviles con Microsoft Intune.

|      Propiedad      |                                                          Descripción                                                          |
|:------------------:|:-----------------------------------------------------------------------------------------------------------------------------:|
| DateKey            | Clave de la fecha en la que se registró el estado de instalación de la aplicación.                                                                     |
| AppKey             | Clave de la aplicación móvil usada para identificar una instancia de AppRevision.                                                          |
| DeviceTypeKey      | Clave del tipo de dispositivo asociada a la aplicación móvil.                                                              |
| AppInstallStateKey | Clave del estado de instalación de la aplicación usada para identificar una instancia de MobileAppInstallState.                                         |
| ErrorCode          | El código de error devuelto por el instalador de la aplicación, la plataforma móvil o el servicio referente a la instalación de la aplicación. |
| Número              | Número total.                                                                                                                  |

## <a name="ownertypes"></a>ownerTypes
La entidad **ownerType** indica si un dispositivo es corporativo, personal o desconocido.

|    Propiedad   |                                                                                     Descripción                                                                                    |           Ejemplo          |
|:-------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
| ownerTypeID   | Identificador único del tipo de propietario.                                                                                                                                               |                            |
| ownerTypeKey  | Identificador único del tipo de propietario en el almacenamiento de datos. Clave suplente.                                                                                                       |                            |
| ownerTypeName | Representa el tipo de propietario de los dispositivos: Corporativo: el dispositivo es propiedad de la empresa.  Personal: el dispositivo es de propiedad personal (BYOD).   Desconocido: no hay información sobre este dispositivo. | Empresa Personal Desconocido |

> [!Note]  
> Para el filtro `ownerTypeName` en Azure AD al crear grupos dinámicos para los dispositivos, deberá establecer el valor `deviceOwnership` como `Company`. Para más información, vea [Reglas de dispositivos](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="policies"></a>directivas
La entidad **Policy** muestra los perfiles de configuración de dispositivos, los perfiles de configuración de aplicaciones y las directivas de cumplimiento. Puede asignar las directivas con Administración de dispositivos móviles (MDM) a un grupo de la empresa.

|          Propiedad          |                                                                       Descripción                                                                      |                Ejemplo               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| PolicyKey                  | Clave única para representar la directiva en el almacenamiento de datos.                                                                                              | 123                                  |
| PolicyId                   | Identificador único de la directiva en el almacenamiento de datos.                                                                                                 | b66bc706-ffff-7437-0340-032819502773 |
| PolicyName                 | Nombre de la directiva.                                                                                                                                    | "Línea base de Windows 10"                |
| PolicyVersion              | Versión de la directiva. Cuando la directiva se modifica o se cambia, se crea una versión más reciente.                                                             | 1, 2, 3                              |
| IsDeleted                  | Indica si se ha actualizado el registro de la directiva.  True: la directiva tiene un nuevo registro con campos actualizados.  False: registro más reciente de la directiva. | Verdadero/Falso                           |
| StartDateInclusiveUTC      | Fecha y hora en formato UTC en que se ha creado la directiva en el almacenamiento de datos.                                                                              | 23/11/2016 0:00                      |
| DeletedDateUTC             | Fecha y hora en formato UTC en que IsDeleted ha cambiado a True.                                                                                                   | 23/11/2016 0:00                      |
| RowLastModifiedDateTimeUTC | Fecha y hora en formato UTC en que se ha modificado por última vez la directiva en el almacenamiento de datos.                                                                        | 23/11/2016 0:00                      |

## <a name="policydeviceactivities"></a>policyDeviceActivities
La tabla siguiente muestra el número de dispositivos en estado correcto, pendiente, con errores o de error al día. El número refleja los datos por perfiles de tipo de directiva. Por ejemplo, si un dispositivo muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un dispositivo tiene dos perfiles asignados, uno con el estado correcto y otro con el estado de error, la entidad aumenta el contador de éxitos y coloca el dispositivo en el estado de error. La entidad **policyDeviceActivity** muestra cuántos dispositivos hay en cada estado en un día determinado de los últimos 30 días.

|  Propiedad |                                           Descripción                                           |        Ejemplo        |
|:---------:|:-----------------------------------------------------------------------------------------------:|:---------------------:|
| DateKey   | Clave de fecha en la que se ha registrado la inserción en el repositorio del perfil de configuración de dispositivos en el almacenamiento de datos. | 20160703              |
| Pending   | Número de dispositivos únicos en estado pendiente.                                                    | 123                   |
| Correcto | Número de dispositivos únicos en estado correcto.                                                    | 12                    |
| PolicyKey | Clave de la directiva, que puede combinarse con la directiva para obtener el nombre de la directiva.                                  | Línea base de Windows 10 |
| Error     | Número de dispositivos únicos en estado de error.                                                      | 10                    |
| Failed    | Número de dispositivos únicos en estado incorrecto.                                                     | 2                     |

## <a name="policyplatformtypes"></a>policyPlatformTypes

|        Propiedad        |                      Descripción                      |     Ejemplo    |
|:----------------------:|:-----------------------------------------------------:|:--------------:|
| PolicyPlatformTypeKey  | Clave única del tipo de plataforma de directivas.        | 20170519       |
| PolicyPlatformTypeId   | Identificador único del tipo de plataforma de directivas. | 1              |
| PolicyPlatformTypeName | Nombre del tipo de plataforma de directivas.              | AndroidForWork |

## <a name="policytypeactivities"></a>policyTypeActivities
La entidad **PolicyTypeActivity** muestra el número acumulado de dispositivos con estado correcto, estado pendiente, estado con errores o estado de error. Muestra estos estados con respecto a un perfil de configuración de dispositivos, un perfil de configuración de aplicaciones o una directiva de cumplimiento por día.

|    Propiedad   |                                          Descripción                                          |           Ejemplo           |
|:-------------:|:---------------------------------------------------------------------------------------------:|:---------------------------:|
| DateKey       | Clave de fecha en la que se ha registrado la inserción en el repositorio del perfil de configuración de dispositivos en el almacenamiento de datos. | 20160703                    |
| PolicyKey     | Clave de la directiva, que puede combinarse con la directiva para obtener el nombre de la directiva.                                | Línea base de Windows 10         |
| PolicyTypeKey | Tipo de clave de directiva, que puede combinarse con el tipo de directiva para obtener el nombre del tipo de directiva.             | Directiva de cumplimiento de Windows 10 |
| Pending       | Número de dispositivos únicos en estado pendiente.                                                    | 123                         |
| Correcto     | Número de dispositivos únicos en estado correcto.                                                    | 12                          |
| Error         | Número de dispositivos únicos en estado de error.                                                      | 10                          |
| Failed        | Número de dispositivos únicos en estado con errores.                                                     | 2                           |

## <a name="policytypes"></a>policyTypes
La entidad **PolicyType** muestra los tipos de perfiles de configuración de dispositivos, perfiles de configuración de aplicaciones y directivas de cumplimiento. Puede asignar las directivas con Administración de dispositivos móviles (MDM) a un grupo de la empresa.

|    Propiedad    |                       Descripción                      |            Ejemplo            |
|:--------------:|:------------------------------------------------------:|:-----------------------------:|
| PolicyTypeId   | Identificador único de la directiva en el sistema de origen.  | 123                           |
| PolicyTypeKey  | Identificador único de la directiva en el almacenamiento de datos. | 1                             |
| PolicyTypeName | Nombre del tipo de directiva.                               | Directiva de cumplimiento de Windows 10. |

## <a name="policyuseractivities"></a>policyUserActivities
La tabla siguiente muestra el número de usuarios en estado correcto, pendiente, con errores o de error al día. El número refleja los datos por perfiles de tipo de directiva. Por ejemplo, si un usuario muestra el estado correcto para todas las directivas que tiene asignadas, aumenta en uno el contador de éxitos de ese día. Si un usuario tiene dos perfiles asignados, uno en estado correcto y otro en estado de error, se cuenta el usuario en el estado de error. La entidad **PolicyUserActivity** muestra cuántos usuarios hay en cada estado en un día determinado de los últimos 30 días.

|  Propiedad |                                          Descripción                                          |       Ejemplo       |
|:---------:|:---------------------------------------------------------------------------------------------:|:-------------------:|
| DateKey   | Clave de fecha en la que se registró la inserción en el repositorio del perfil de configuración de dispositivos en el almacenamiento de datos. | 20160703            |
| Pending   | Número de dispositivos únicos en estado pendiente.                                                    | 123                 |
| Correcto | Número de dispositivos únicos en estado correcto.                                                    | 12                  |
| PolicyKey | Clave de la directiva, que puede combinarse con la directiva para obtener el nombre de la directiva.                                | Línea base de Windows 10 |
| Error     | Número de dispositivos únicos en estado de error.                                                      | 10                  |

## <a name="termsandconditions"></a>termsAndConditions
Una entidad **termsAndConditions** representa los metadatos y el contenido de una determinada directiva de términos y condiciones (T&C). El contenido de las directivas T&C se presenta a los usuarios tras su primer intento de inscribirse en Intune y posteriormente tras las ediciones en las que un administrador ha solicitado aceptación. Permite a los administradores comunicar las disposiciones con las que debe estar de acuerdo un usuario para tener dispositivos inscritos en Intune.

|    Propiedad        |    Descripción    |    Ejemplo        |
|----------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
|    termsAndConditionsKey    |    Una clave que corresponde a una entrada en la colección "userTermsAndConditionsAcceptances"    |    123    |
|    termsAndCondidionsId    |    El identificador de esta entrada termsAndConditions    |    276edcb7-7440-4339-b6c5-8b6fc556fee6    |
|    termsAndConditionsVersion    |    La versión de esta entrada de términos y condiciones    |    1    |
|    name    |    El nombre de esta entrada termsAndConditions.        |    Términos de uso de Intune     |
|    description    |    La descripción de estos términos y condiciones.     |         |
|    title    |    El título de estos términos y condiciones.     |    Directiva corporativa de administración de dispositivos        |
|    summaryOfTerms    |    El resumen de términos dados al usuario.     |    Acepto los términos y condiciones.    |
|    termsAndConditionsBodyText    |    El cuerpo del texto de estos términos y condiciones.       |    *Cifrado de dispositivo* Exigencia de PIN de 6 dígitos    |
|    isDeleted    |    Valor true o false para si se elimina este valor.     |    False    |
|    startDateInclusiveUTC    |    La fecha de inicio de estos términos y condiciones.     |    23/8/2018 4:01:34 a.m.    |
|    endDateEclusiveUTC    |    La fecha de finalización de estos términos y condiciones.     |    12/31/9999 12:00:00 a.m.    |

## <a name="userdeviceassociations"></a>userDeviceAssociations
La entidad **UserDeviceAssociation** contiene las asociaciones de dispositivos de usuario que se dan en su organización.

|        Nombre        |                                             Descripción                                            |     Ejemplo     |
|:------------------:|:--------------------------------------------------------------------------------------------------:|:---------------:|
| UserKey            | Identificador único del usuario en el almacenamiento de datos.   (Clave suplente).                            | 123             |
| DeviceKey          | Identificador único del dispositivo en el almacenamiento de datos.                                             | 123             |
| CreatedDateTimeUTC | Fecha y hora de creación de la asociación de dispositivos de usuario. Utiliza el formato UTC.                     | 23/11/2016 0:00 |
| IsDeleted          | Indica que el usuario ha anulado la inscripción del dispositivo y que la asociación ya no está activa. | Verdadero/Falso      |
| EndedDateTimeUTC   | Fecha y hora en formato UTC en que IsDeleted ha cambiado a True.                                               | 23/6/2017 0:00  |

## <a name="users"></a>usuarios
La entidad **user** muestra todos los usuarios de Azure Active Directory (Azure AD) con licencias asignadas en la empresa.

La colección de entidades **user** contiene los datos de usuario. Dichos registros incluyen los estados de los usuarios durante el período de recopilación de datos, incluso aunque se haya eliminado a alguno de ellos. Por ejemplo, es posible que durante el último mes se haya agregado a un usuario a Intune y, luego, se haya eliminado. A pesar de que este usuario no esté presente a la hora de generar el informe, el usuario en cuestión y su estado sí que figuran en los datos del mes anterior. Una opción podría ser crear un informe que incluya el historial relativo a la duración de la presencia del usuario en sus datos.

|          Propiedad          |                                                                                                           Descripción                                                                                                          |                Ejemplo               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | Identificador único del usuario en el almacenamiento de datos. Clave suplente.                                                                                                                                                         | 123                                  |
| UserId                     | Identificador único del usuario. Se parece a UserKey, pero es una clave natural.                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| UserEmail                  | Dirección de correo electrónico del usuario.                                                                                                                                                                                                     | John@constoso.com                    |
| userPrincipalName                        | Nombre principal del usuario.                                                                                                                                                                                               | John@constoso.com                    |
| DisplayName                | Nombre para mostrar del usuario.                                                                                                                                                                                                      | Juan                                 |
| IntuneLicensed             | Especifica si este usuario tiene licencia de Intune o no.                                                                                                                                                                              | Verdadero/Falso                           |
| IsDeleted                  | Indica si todas las licencias del usuario expiraron y si, por lo tanto, el usuario se quitó de Intune. Esta marca no cambia si se trata de un solo registro. En su lugar, se crea un registro para un estado de usuario nuevo. | Verdadero/Falso                           |
| RowLastModifiedDateTimeUTC | Fecha y hora en formato UTC en que se modificó por última vez el registro en el almacenamiento de datos                                                                                                                                                 | 23/11/2016 0:00                      |

## <a name="usertermsandconditionsacceptances"></a>userTermsAndConditionsAcceptances
Una entidad **userTermsAndConditionsAcceptance** representa el estado de aceptación de una determinada directiva de términos y condiciones (T&C) por un usuario determinado. Los usuarios deben aceptar la versión más actualizada de los términos para conservar el acceso al Portal de empresa.

|    Propiedad    |    Descripción    |    Ejemplo    |
|-------------------------------|--------------------------------------------------------------------------------|----------------------------|
|    dateKey    |    Una clave correspondiente a los de valores de fecha en la colección "dates".     |    20180823    |
|    userKey    |    Asignación de claves de usuario a un usuario de la colección de "users".     |    20000    |
|    termsAndConditionsKey    |    Una clave correspondiente a una entrada de la colección "termsAndConditions"    |    1    |
|    acceptedDateTimeUTC    |    La hora a la que el usuario acepta estos términos y condiciones    |    23/8/2018 4:01:34 a.m.    |
|    lastModifiedDateTimeUTC    |    La última vez que se modificó esta entrada.     |    23/8/2018 4:01:34 a.m.    |

## <a name="vppprogramtypes"></a>vppProgramTypes 
La entidad **vppProgramTypes** muestra los posibles tipos de programa VPP para una aplicación.

|      Propiedad      |          Descripción         |
|:------------------:|:----------------------------:|
| VppProgramTypeID   | Identificador del tipo.           |
| VppProgramTypeKey  | Clave suplente de la clave. |
| VppProgramTypeName | Tipo de programa VPP.          |

### <a name="example"></a>Ejemplo

|             VppProgramID             |         Nombre        | Descripción                |
|:------------------------------------:|:-------------------:|----------------------------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft           | Programa VPP de Microsoft. |
| 00000000-0000-0000-0000-000000000000 | No disponible aún | Valor predeterminado: Sin VPP.   |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple               | Programa VPP de Apple.     |

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre el almacenamiento de datos de Intune, consulte [Modelo de datos de Almacenamiento de datos](reports-ref-data-model.md).
