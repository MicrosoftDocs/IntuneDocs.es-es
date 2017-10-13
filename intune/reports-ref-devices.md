---
title: Dispositivos | Microsoft Docs
description: "Tema de referencia sobre la categoría Dispositivos de las colecciones de entidades de la API de Almacenamiento de datos de Intune."
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7730a799176a74f1ddb8e4b5e49a110229255428
ms.sourcegitcommit: 6fae2dfb3a5c8f2e5ccfd120fd15656b26e5d302
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2017
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

## <a name="example"></a>Ejemplo

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
| 17 |AndroidForWork |Dispositivo Android administrado mediante el propietario con perfil Android for Work |
| 100 |BlackBerry |Dispositivo BlackBerry |
| 101 |Palm |Dispositivo Palm |
| 255 |Unknown |Tipo de dispositivo desconocido |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

La entidad **ClientRegistrationStateTypes** representa el tipo de dispositivo al que hacen referencia otras tablas de almacenamiento de datos.

| Propiedad  | Descripción |
|---------|------------|
| clientRegisterationStateID |Identificador único del estado de registro. |
| clientRegisterationStateKey |Identificador único del estado de registro en el almacenamiento de datos. Clave suplente. |
| clientRegisterationStateName |Estado de registro. |

## <a name="example"></a>Ejemplo

| ClientRegisterationStateID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |NotRegistered |No registrado. |
| 1 |SMSIDConflict |Conflicto de identificador de SMS. |
| 2 |Registrado |Registrado |
| 3 |Revoked |El estado significa que el administrador de TI ha bloqueado al cliente y el cliente se puede desbloquear. Un dispositivo también puede encontrarse en estado Revoked después de que se haya borrado o retirado. |
| 4 |KeyConflict |Conflicto de clave. |
| 5 |ApprovalPending |Pendiente de aprobación. |
| 6 |ResetCert |Certificado establecido. |
| 7 |NotRegisteredPendingEnrollment |No registrado y pendiente de inscripción. |
| 8 |Unknown |Estado desconocido. |

## <a name="enrollmenttypes"></a>EnrollmentTypes

La entidad **EnrollmentTypes** indica cómo se ha inscrito un dispositivo. El tipo de inscripción captura el método de inscripción. En los ejemplos se muestran los diferentes tipos de inscripción y su significado.

| Propiedad  | Descripción |
|---------|------------|
| managementStateID |Identificador único del estado de administración. |
| managementStateKey |Identificador único del estado de administración en el almacenamiento de datos. Clave suplente. |
| managementStateName |Indica el estado de la acción remota aplicada a este dispositivo. |

## <a name="example"></a>Ejemplo

| enrollmentTypeID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Unknown |No se recopiló el tipo de inscripción |
| 1 |UserEnrollment |Inscripción iniciada por el usuario. |
| 2 |DeviceEnrollment |Inscripción del dispositivo mediante un perfil sin usuario. |
| 3 |DeviceEnrollmentWithUDA |Inscripción del dispositivo mediante un perfil UDA. |
| 4 |AzureDomainJoined |Inscripción del dispositivo iniciada por el usuario mediante Azure Active Directory. |
| 5 |UserEnrollmentWithServiceAccount |Inscripción iniciada por el usuario mediante una cuenta de servicio. |
| 6 |DepDeviceEnrollment |Inscripción de dispositivo DEP mediante un perfil sin usuario. |
| 7 |DepDeviceEnrollmentWithUDA |Inscripción de dispositivo DEP mediante un perfil UDA. |
| 8 |AutoEnrollment |Inscripción combinada de DRS y MDM para escenario BYOD. |

## <a name="ownertypes"></a>OwnerTypes

La entidad **EnrollmentTypes** indica si el dispositivo es corporativo, personal o desconocido.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| ownerTypeID |Identificador único del tipo de propietario. | |
| ownerTypeKey |Identificador único del tipo de propietario en el almacenamiento de datos. Clave suplente. | |
| ownerTypeName |Representa el tipo de propietario de los dispositivos. Empresa: el dispositivo es propiedad de la empresa. Personal: el dispositivo es de propiedad personal (BYOD).  Desconocido: no hay información sobre este dispositivo. |Empresa Personal Desconocido |

## <a name="mdmstatuses"></a>MdmStatuses

La entidad **MdmStatuses** indica el estado de cumplimiento del dispositivo.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| MdmStatusName |Identificador de MdmStatus. |0: desconocido. 1: conforme. 2: no conforme. |
| MdmStatusKey |Identificador único del estado de cumplimiento en el almacenamiento de datos. Clave suplente. | |

## <a name="managementstates"></a>ManagementStates

La entidad **ManagementStates** proporciona detalles sobre el estado del dispositivo. Los detalles pueden ser útiles en los casos en los que se aplican acciones remotas o el dispositivo se ha liberado o modificado.

| Propiedad  | Descripción |
|---------|------------|
| managementStateID |Identificador único del estado de administración. |
| managementStateKey |Identificador único del estado de administración en el almacenamiento de datos. Clave suplente. |
| managementStateName |Indica el estado de la acción remota aplicada a este dispositivo. |

## <a name="example"></a>Ejemplo

| managementStateID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Administrados |Administrado sin acciones remotas pendientes. |
| 1 |RetirePending |Hay un comando de retirada pendiente para el dispositivo. |
| 2 |RetireFailed |Se ha producido un error en el comando de retirada en el dispositivo. |
| 3 |WipePending |Hay un comando de borrado pendiente para el dispositivo. |
| 4 |WipeFailed |Se ha producido un error en el comando de borrado en el dispositivo. |
| 5 |Incorrecto |Estado incorrecto. |
| 6 |DeletePending |Hay un comando de eliminación pendiente para el dispositivo. |
| 7 |RetireIssued |Se ha emitido un comando de retirada en el dispositivo. |
| 8 |WipeIssued |Se ha emitido un comando de borrado. |
| 9 |WipeCanceled |Se ha cancelado un comando de borrado. |
| 10 |RetireCanceled |Se ha cancelado un comando de retirada. |
| 11 |Discovered |Intune acaba de detectar el dispositivo. Una vez que se ha registrado por primera vez, se mueve al estado administrado. |

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

La entidad **WorkPlaceJoinStateTypes** representa el estado de Workplace Join de Azure Active Directory del dispositivo.  El flujo de trabajo de inscripción puede usar uno o varios certificados para comprobar o autenticar. Cuando se inscribe un dispositivo WorkPlace, estos certificados se usan para validar el dispositivo y el usuario. La emisión de certificados se proporciona a través de un servidor SCEP (Protocolo de inscripción de certificados simple). Los valores de la entidad indican los diferentes estados en los que puede encontrarse un dispositivo durante este proceso. Algunos de estos estados incluyen el error de Workplace Join debido a un problema en la emisión de un certificado necesario (desde un servidor SCEP). Si un dispositivo no ha pasado nunca por este flujo de trabajo, el valor se establece en Desconocido.

| Propiedad  | Descripción |
|---------|------------|
| WorkPlaceJoinStateID |Identificador único del estado de Workplace Join. |
| WorkPlaceJoinStateKey |Identificador único del estado de Workplace Join en el almacenamiento de datos. Clave suplente. |
| WorkPlaceJoinStateName |Estado de Workplace Join. |

## <a name="example"></a>Ejemplo

| workPlaceJoinStateID  | Nombre | Descripción |
|---------|------------|--------|
| 0 |Unknown |Si un dispositivo no se ha unido al área de trabajo, se encuentra en estado desconocido. |
| 1 |Correcto |Unión correcta al área de trabajo. |
| 2 |FailureToGetScepMetadata |Error al obtener metadatos de SCEP. |
| 3 |FailureToGetScepChallenge |Error al obtener el desafío SCEP. |
| 4 |DeviceFailureToInstallScepCommand |Error al instalar el comando de SCEP en el dispositivo. |
| 5 |DeviceFailureToGetCertificate |El dispositivo no pudo obtener el certificado a través de SCEP. |
| 6 |DeviceScepPending |Estado pendiente. El dispositivo todavía está en el proceso de SCEP. |
| 7 |DeviceScepFailed |El dispositivo no pudo instalar el certificado a través de SCEP. |
| 8 |AADValidationFailed |No se pudo validar que el dispositivo existe en AAD. |

## <a name="managementagenttypes"></a>ManagementAgentTypes

La entidad **ManagementAgentTypes** representa los agentes usados para administrar un dispositivo.

| Propiedad  | Descripción |
|---------|------------|
| ManagementAgentTypeID |Identificador único del tipo de agente de administración. |
| ManagementAgentTypeKey |Identificador único del tipo de agente de administración en el almacenamiento de datos. Clave suplente. |
| ManagementAgentTypeName |Indica qué tipo de agente se usa para administrar el dispositivo. |

## <a name="example"></a>Ejemplo

| ManagementAgentTypeID  | Nombre | Descripción |
|---------|------------|--------|
| 1 |EAS |El dispositivo se administra a través de Exchange Active Sync. |
| 2 |MDM |El dispositivo se administra mediante un agente MDM. |
| 3 |EasMdm |El dispositivo se administra mediante Exchange Active Sync y un agente MDM. |
| 4 |IntuneClient |El dispositivo se administra mediante el agente del equipo de Intune. |
| 5 |EasIntuneClient |El dispositivo se administra mediante Exchange Active Sync y el agente del equipo de Intune. |
| 8 |ConfigManagerClient |El dispositivo se administra mediante el agente de System Center Configuration Manager. |
| 16 |Unknown |Tipo de agente de administración desconocido. |

## <a name="devices"></a>Dispositivos

La entidad **Devices** muestra todos los dispositivos inscritos en administración y sus propiedades correspondientes.

| Propiedad  | Descripción |
|---------|------------|
| DeviceKey |Identificador único del dispositivo en el almacenamiento de datos. Clave suplente. |
| DeviceId |Identificador único del dispositivo. |
| DeviceName |Nombre del dispositivo en plataformas que permiten asignar nombre a un dispositivo. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos. |
| DeviceTypeKey |Clave del atributo de tipo de dispositivo para este dispositivo. |
| ClientRegisterationStateKey |Clave del atributo de estado de registro del cliente para este dispositivo. |
| OwnerTypeKey |Clave del atributo de tipo de propietario para este dispositivo: corporativo, personal o desconocido. |
| objectSourceKey |Ignore esta columna. |
| CreatedDate |Fecha de inscripción del dispositivo. |
| LastContact |Último registro de dispositivo conocido con Intune. |
| LastContactNotification |Última vez que Intune ha notificado al dispositivo que se registre con Intune. |
| LastContactWorkplaceJoin |Marca de tiempo que indica el último estado conocido de Workplace Join para este dispositivo. |
| ManagementAgentKey |Clave del agente de administración asociado a este dispositivo. |
| ManagementStateKey |Clave del estado de administración asociado a este dispositivo, que indica el estado más reciente de una acción remota o si estaba liberado o modificado. |
| ReferenceId |Identificador del dispositivo en Azure Active Directory. |
| WorkPlaceJoinStateKey |Clave del estado de Workplace Join asociado a este dispositivo. |
| CategoryId |Ignore esta columna. |
| EnrollmentTypeKey |Clave del tipo de inscripción asociado a este dispositivo, que indica el método de inscripción. |
| CertExpirationDate |Fecha de expiración del certificado de administración de MDM. |
| MdmStatusKey |Clave para MdmStatus. |
| OSFamily |Familia de sistemas operativos (Windows, iOS, Android, etc.). |
| OSVersion |Versión del sistema operativo |
| OSMajorVersion |Componente de versión principal de la versión del sistema operativo (principal.secundaria.compilación.revisión) |
| OSMinorVersion |Componente de versión secundaria de la versión del sistema operativo (principal.secundaria.compilación.revisión) |
| OSBuildNumber |Componente de versión de compilación de la versión del sistema operativo (principal.secundaria.compilación.revisión) |
| OSRevisionNumber |Componente de versión de revisión de la versión del sistema operativo (principal.secundaria.compilación.revisión) |
| EasID |Identificador de EAS de este dispositivo, si está administrado mediante Exchange Active Sync. |
| GraphDeviceIsManaged |Último estado de administración que Intune ha establecido en AAD. |
| GraphDeviceIsCompliant |Último estado de cumplimiento que Intune ha establecido en AAD. |
| SerialNumber |Número de serie del dispositivo, si está disponible. |
| EnrolledByUser |Identificador del usuario que ha inscrito el dispositivo, que hace referencia a la columna userId de la tabla de usuario. |
| RowLastModifiedDateTimeUTC |Fecha y hora de la última modificación de este registro. |
| ProcessorArchitecture |Arquitectura de procesador |
| DeviceAction |Última acción de dispositivo emitida. Ignórela por el momento. |
| Fabricante |Fabricante del dispositivo. |
| Modelo |Modelo del dispositivo. |
| LastPolicyUpdateUtc |Hora más reciente en la que se ha actualizado la directiva del dispositivo. |
| LastExchangeStatusUtc |Hora más reciente en la que se ha sincronizado el dispositivo con Exchange. |
| IsDeleted |Establecido en True si el dispositivo ya no se administra mediante Intune. Conserva el último estado conocido. |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

La entidad **DevicePropertyHistory** tiene las mismas propiedades que las tablas de dispositivos y las instantáneas diarias de cada registro de dispositivo por día de los últimos 90 días. La columna DateKey indica el día de cada fila.

| Propiedad  | Descripción |
|---------|------------|
| DateKey |Referencia a la tabla de fechas que indica el día. |
| DeviceKey |Identificador único del dispositivo en el almacenamiento de datos. Clave suplente. Se trata de una referencia a la tabla de dispositivos que contiene el identificador de dispositivo de Intune. |
| DeviceName |Nombre del dispositivo en plataformas que permiten asignar nombre a un dispositivo. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos. |
| DeviceTypeKey |Clave del atributo de tipo de dispositivo para este dispositivo. |
| ClientRegisterationStateKey |Clave del atributo de estado de registro del cliente para este dispositivo. |
| OwnerTypeKey |Clave del atributo de tipo de propietario para este dispositivo: corporativo, personal o desconocido. |
| objectSourceKey |Ignore esta columna. |
| CreatedDate |Fecha de inscripción del dispositivo. |
| LastContact |Último registro de dispositivo conocido con Intune. |
| LastContactNotification |Última vez que Intune ha notificado al dispositivo que se registre con Intune. |
| LastContactWorkplaceJoin |Marca de tiempo que indica el último estado conocido de Workplace Join para este dispositivo. |
| ManagementAgentKey |Clave del agente de administración asociado a este dispositivo. |
| ManagementStateKey |Clave del estado de administración asociado a este dispositivo, que indica el estado más reciente de una acción remota o si estaba liberado o modificado. |
| ReferenceId |Identificador del dispositivo en Azure Active Directory. |
| WorkPlaceJoinStateKey |Clave del estado de Workplace Join asociado a este dispositivo. |
| CategoryId |Ignore esta columna. |
| EnrollmentTypeKey |Clave del tipo de inscripción asociado a este dispositivo, que indica el método de inscripción. |
| CertExpirationDate |Fecha de expiración del certificado de administración de MDM. |
| MdmStatusKey |Clave para MdmStatus. |
| OSFamily |Familia de sistemas operativos (Windows, iOS, Android, etc.). |
| OSVersion |Versión del sistema operativo |
| OSMajorVersion |Componente de versión principal de la versión del sistema operativo (principal.secundaria.compilación.revisión) |
| OSMinorVersion |Componente de versión secundaria de la versión del sistema operativo (principal.secundaria.compilación.revisión) |
| OSBuildNumber |Componente de versión de compilación de la versión del sistema operativo (principal.secundaria.compilación.revisión) |
| OSRevisionNumber |Componente de versión de revisión de la versión del sistema operativo (principal.secundaria.compilación.revisión) |
| EasID |Identificador de EAS de este dispositivo, si está administrado mediante Exchange Active Sync. |
| GraphDeviceIsManaged |Último estado de administración que Intune ha establecido en AAD. |
| GraphDeviceIsCompliant |Último estado de cumplimiento que Intune ha establecido en AAD. |
| SerialNumber |Número de serie del dispositivo, si está disponible. |
| EnrolledByUser |Identificador del usuario que ha inscrito el dispositivo, que hace referencia a la columna userId de la tabla de usuario. |
| RowLastModifiedDateTimeUTC |Fecha y hora de la última modificación de este registro. |
| ProcessorArchitecture |Arquitectura de procesador |
| DeviceAction |Última acción de dispositivo emitida. Ignórela por el momento. |
| Fabricante |Fabricante del dispositivo. |
| Modelo |Modelo del dispositivo. |
| LastPolicyUpdateUtc |Hora más reciente en la que se ha actualizado la directiva del dispositivo. |
| LastExchangeStatusUtc |Hora más reciente en la que se ha sincronizado el dispositivo con Exchange. |
## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

La entidad **MdmDeviceInventoryHistories** contiene instantáneas diarias de los datos del inventario para dispositivos administrados por MDM durante los últimos 90 días. La columna DateKey indica el día de la fila. Es posible que algunas propiedades no se puedan aplicar o rellenar para todos los dispositivos, por lo que debe consultar esta página. Para obtener más información, vea [Comprender el funcionamiento de sus dispositivos mediante el inventario en Microsoft Intune](https://docs.microsoft.com/Intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-Intune).

| Propiedad  | Descripción |
|---------|------------|
| DateKey |Referencia a la tabla de fechas que indica el día. |
| DeviceKey |Identificador único del dispositivo en el almacenamiento de datos. Clave suplente. Se trata de una referencia a la tabla de dispositivos que contiene el identificador de dispositivo de Intune. |
| DeviceModel |Modelo del dispositivo. |
| Sistema operativo |Sistema operativo del dispositivo. |
| DeviceName |Nombre del dispositivo en plataformas que permiten asignar nombre a un dispositivo. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos. |
| SoftwareVersion |En la mayoría de los casos es la versión del sistema operativo, excepto en plataformas de Apple, en cuyo caso es diferente de la versión del sistema operativo. |
| Imei |Número IMEI. |
| HardwareInventoryTimeUtc |Primera vez que se notificó el inventario de este dispositivo. |
| InventoryModifiedTimeUtc |Última vez que se almacenó el inventario al tomarse esta instantánea. |
| InventoryReportingTimeUtc |Última vez que se recopiló el inventario de este dispositivo. |
| ExchangeActiveSyncId |Identificador de dispositivo de Exchange ActiveSync. |
| ComputerSystemDescription |Descripción del sistema. |
| ComputerSystemName |Nombre del sistema |
| ComputerSystemManufacturer |Fabricante del sistema. |
| ComputerSystemModel |Modelo del sistema. |
| UserName |Nombre de usuario |
| OSType |Tipo de SO |
| OSCaption |Descripción del sistema operativo. |
| OSName |Nombre del sistema operativo. |
| OSManufacturer |Fabricante del sistema operativo. |
| OSProductSuite |Conjunto de productos del sistema operativo. |
| OSProductType |Tipo de producto del sistema operativo. |
| Configuración regional |Configuración regional. |
| PhysicalMemoryCapacity |Capacidad de memoria física (en bytes). |
| PhysicalMemoryRemovable |Memoria extraíble física (en bytes). |
| SystemEnclosureChassisTypesInnerText |Define el tipo de chasis del sistema para este dispositivo. Los números indican los valores siguientes: 0 o vacío = desconocido; 1 = escritorio; 2 = portátil; 3 = estación de trabajo; 4 = Enterprise Server; 100 = teléfono; 101 = tableta; 102/103 = otro tipo desconocido de dispositivo móvil. |
| SystemEnclosureModel |Modelo de revestimiento de hardware del sistema. |
| SystemEnclosureSerialNumber |Número de serie del revestimiento de hardware del sistema. |
| NetworkAdapterConfigurationText |Texto de configuración del adaptador de red. |
| MacAddress |Dirección MAC |
| SmsID |Identificador de dispositivo de Intune. |
| CertExpiry |Fecha de expiración del certificado de administración de MDM. |
| DeviceClientAgentVersion |Versión del agente de cliente. |
| DeviceClientID |Identificador de cliente del dispositivo. |
| SerialNumber |Número de serie |
| DeviceManufacturer |Fabricante del dispositivo |
| DMVersion |Versión de DM. |
| FirmwareVersion |Versión de firmware |
| HardwareVersion |Versión de hardware |
| PlatformType |Tipo de plataforma |
| ProcessorLevel |Nivel de procesador. |
| ProcessorRevision |Revisión del procesador. |
| Product |Product |
| ProductVersion |Versión del producto |
| OEM |Fabricante de equipo original. |
| DeviceBuildVersion |Versión de compilación del dispositivo. |
| Meid |Identificador de equipo móvil. |
| PhoneNumber |Número de teléfono |
| SubscriberCarrierNetwork |Nombre de red del operador de telefonía. |
| CellularTechnology |Tipo de red del operador de telefonía (CDMA/GSM). |
| Imsi |Número IMSI. |
| JailBroken |True si el dispositivo está liberado o modificado. |
| IsActivationLockEnabled |True si el bloqueo de activación está habilitado. |
| DeviceType |Tipo de dispositivo |
| IsSupervised |Está supervisado |
| DeviceDisplayNumberOfColors |Número de colores de la pantalla del dispositivo. |
| HorizontalResolution |Resolución de pantalla horizontal del dispositivo. |
| VerticalResolution |Resolución de pantalla vertical del dispositivo. |
| StorageFree |Almacenamiento libre (en bytes). |
| StorageTotal |Almacenamiento total (en bytes). |
| ProgramFree |Memoria de programa libre (en bytes). |
| ProgramTotal |Memoria de programa total (en bytes). |
| RemovableStorageFree |Almacenamiento extraíble libre (en bytes). |
| RemovableStorageTotal |Almacenamiento extraíble total (en bytes). |
| DeviceMemoryDeviceCapacity |Capacidad de memoria del dispositivo. |
| DeviceMemoryAvailableDeviceCapacity |Capacidad disponible de memoria del dispositivo. |
| DeviceOSVersion |Versión del SO |
| DeviceOSPlatform |Plataforma del sistema operativo. |
| DeviceOSLanguage |Idioma del sistema operativo. |
| PasswordMaxAttemptsBeforeWipe |Número máximo de intentos de contraseña permitidos antes de que se produzca el borrado del dispositivo. |
| PasswordMinComplexChars |Número mínimo de caracteres complejos que se requieren en la contraseña. |
| PasswordMinLength |Longitud mínima necesaria de la contraseña. |
| PasswordHistory |Contraseña: número mínimo de contraseñas históricas que no se aceptan. |
| PasswordEnabled |Contraseña: ¿habilitada? |
| PasswordExpiration |Contraseña: fecha de expiración. |
| AllowRecoveryPassword |Permitir recuperación de contraseña |
| PasswordAutoLockTimeout |Contraseña: tiempo de espera de bloqueo automático. |
| PasswordType |Tipo de contraseña. |
| BacklightACTimeout |Tiempo de espera de retroiluminación cuando se está conectado a una fuente de alimentación. |
| BacklightBatTimeout |Tiempo de espera de retroiluminación con batería. |
| PowerBackupPercent |Porcentaje de energía de reserva. |
| BatteryPercent |Porcentaje de batería restante. |
| PlatformID |Identificador de plataforma. |
| ExchangeDeviceID |Identificador de dispositivo de Exchange. |
| SmsProcessorDescription |Descripción del procesador. |
| OwnerEmailAddress |Dirección de correo electrónico del propietario. |
| DeviceOSName |Nombre del sistema operativo. |
| WifiMac |Dirección MAC de Wi-Fi. |
| EthernetMac |Dirección MAC de Ethernet. |
| RequireEncryption |Indica si el dispositivo está cifrado. |
| ActivationLockBypassCode |Código de omisión del bloqueo de activación. |

## <a name="applicationinventory"></a>ApplicationInventory

La entidad **ApplicationInventory** muestra las aplicaciones que se encuentran en el dispositivo en el momento de recopilación del inventario.

| Propiedad  | Descripción |
|---------|------------|
| DeviceKey |Referencia a la tabla de dispositivos. |
| ApplicationKey |? (copiado de ExchangeDeviceService\DeviceApplication). |
| ApplicationName |? (copiado de ExchangeDeviceService\DeviceApplication). |
| ApplicationVersion |? (copiado de ExchangeDeviceService\DeviceApplication). |
| BundleSize |? (copiado de ExchangeDeviceService\DeviceApplication). |
