---
title: Registro de cambios del Almacenamiento de datos de Intune
titleSuffix: Microsoft Intune
description: En este tema se proporciona una lista de cambios para la API Data Warehouse de Microsoft Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0aaa305ac216e0f80f82116e626b21f3ae7a8510
ms.sourcegitcommit: c8cb314256c4896e838918f015ffaefb8f00ace5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2019
ms.locfileid: "71303310"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registro de cambios en la API Almacenamiento de datos de Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Manténgase al día de los cambios producidos en el Almacén de datos de Intune.

## <a name="1903-part-2"></a>1903 (Parte 2)
_Fecha de publicación: abril de 2019_

### <a name="beta-changes"></a>Cambios de la versión beta

En esta tabla se enumeran las colecciones quitadas recientemente y las colecciones de reemplazos en el almacenamiento de datos de Intune.

|    Colección                          |    Cambio     |    Información adicional                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    MobileAppDeviceUserInstallStatus    |    Quitado    |    Use mejor [mobileAppInstallStatusCounts](intune-data-warehouse-collections.md#mobileappinstallstatuscounts).                                                                                                                                                                                                                                                                     |
|    enrollmentTypes                     |    Quitado    |    Use mejor [deviceEnrollmentTypes](intune-data-warehouse-collections.md#deviceenrollmenttypes).                                                                                                                                                                                                                                                                                      |
|    mdmStatuses                         |    Quitado    |    Use mejor [complianceStates](intune-data-warehouse-collections.md#compliancestates).                                                                                                                                                                                                                                                                                               |
|    workPlaceJoinStateTypes             |    Quitado    |    Use mejor la propiedad `azureAdRegistered` en las colecciones [devices](intune-data-warehouse-collections.md#devices) y [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories).                                                                                                                                                                                                             |
|    clientRegistrationStateTypes        |    Quitado    |    Use mejor [deviceRegistrationStates](intune-data-warehouse-collections.md#deviceregistrationstates).                                                                                                                                                                                                                                                                             |
|    currentUser                         |    Quitado    |    Use mejor la colección [users](intune-data-warehouse-collections.md#users).                                                                                                                                                                                                                                                                                                      |
|    mdmDeviceInventoryHistories         |    Quitado    |    Muchas de las propiedades eran redundantes o ahora se encuentran en las colecciones [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) o [devices](intune-data-warehouse-collections.md#devices). Cualquier propiedad **mdmDeviceInventoryHistories** que ya no se muestra con estas dos colecciones no estará disponible. Vea los detalles más abajo.    |

En la tabla siguiente se enumeran las propiedades antiguas que anteriormente estaban incluidas en la colección **mdmDeviceInventoryHistories** y el cambio/reemplazo. Se han quitado las propiedades que se encontraban en **mdmDeviceInventoryHistories** pero no aparecen más abajo.

|    Propiedad antigua                |    Cambio/Reemplazo                                                           |
|--------------------------------|---------------------------------------------------------------------------------|
|    cellularTechnology          |    cellularTechnology en la colección devices                                     |
|    deviceClientId              |    deviceId en la colección devices                                               |
|    deviceManufacturer          |    manufacturer en la colección devices                                           |
|    deviceModel                 |    model en la colección devices                                                  |
|    deviceName                  |    deviceName en la colección devices                                             |
|    deviceOsPlatform            |    deviceTypeKey en la colección devices                                          |
|    deviceOsVersion             |    osVersion en la colección devicePropertyHistories                              |
|    deviceType                  |    deviceTypeKey en la colección devices, que hace referencia a la colección deviceTypes    |
|    encryptionState             |    Propiedad encryptionState en la colección devices                           |
|    exchangeActiveSyncId        |    Propiedad easDeviceId en la colección devices                               |
|    exchangeDeviceId            |    easDeviceId en la colección devices                                            |
|    IMEI                        |    imei en la colección devices                                                   |
|    IsSupervised                |    Propiedad isSupervised en la colección devices                              |
|    jailBroken                  |    jailBroken en la colección devicePropertyHistories                             |
|    MEID                        |    Propiedad meid en la colección devices                                      |
|    oem                         |    manufacturer en la colección devices                                           |
|    osName                      |    deviceTypeKey en la colección devices, que hace referencia a la colección deviceTypes    |
|    phoneNumber                 |    phoneNumber en la colección devices                                            |
|    platformType                |    model en la colección devices                                                  |
|    product                     |    deviceTypeKey en la colección devices                                          |
|    productVersion              |    osVersion en la colección devicePropertyHistories                              |
|    serialNumber                |    serialNumber en la colección devices                                           |
|    storageFree                 |    Propiedad freeStorageSpaceInBytes en la colección devices                   |
|    storageTotal                |    Propiedad totalStorageSpaceInBytes en la colección devices                |
|    subscriberCarrierNetwork    |    Propiedad subscriberCarrier en la colección devices                         |
|    wifimac                     |    wiFiMacAddress en la colección devices                                         |

En esta tabla se enumeran los cambios realizados en las propiedades que se encuentran en la colección [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories): 

|    Propiedad antigua                  |    Cambio/Reemplazo                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey, que hace referencia a la colección deviceCategories       |
|    certExpirationDate            |    Quitado                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime en la colección devices                           |
|    deviceTypeKey                 |    deviceTypeKey en la colección devices                              |
|    easID                         |    easDeviceId en la colección devices                                |
|    enrolledByUser                |    userId en la colección devices                                     |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey en la colección devices                    |
|    graphDeviceIsCompliant        |    Quitado                                                          |
|    graphDeviceIsManaged          |    Quitado                                                          |
|    lastContact                   |    lastSyncDateTime en la colección devices                           |
|    lastContactNotification       |    Quitado                                                          |
|    lastContactWorkplaceJoin      |    Quitado                                                          |
|    lastExchangeStatusUtc         |    Quitado                                                          |
|    lastModifiedDateTimeUTC       |    Quitado                                                          |
|    lastPolicyUpdateUtc           |    Quitado                                                          |
|    managementAgentKey            |    managementStateKey                                               |
|    fabricante                  |    manufacturer en la colección devices                               |
|    mdmStatusKey                  |    complianceStateKey, que hace referencia a la colección complianceStates    |
|    modelo                         |    model en la colección devices                                      |
|    osFamily                      |    operatingSystem en la colección devices                            |
|    osRevisionNumber              |    osVersion en la colección devices                                  |
|    processorArchitecture         |    Quitado                                                          |
|    referenceId                   |    azureAdDeviceId en la colección devices                            |
|    serialNumber                  |    serialNumber en la colección devices                               |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

En esta tabla se enumeran los cambios realizados en las propiedades que se encuentran en la colección [devices](intune-data-warehouse-collections.md#devices): 

|    Propiedad antigua                  |    Cambio/Reemplazo                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey, que hace referencia a la colección deviceCategories       |
|    certExpirationDate            |    Quitado                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime                                                 |
|    easId                         |    easDeviceId                                                      |
|    enrolledByUser                |    userId                                                           |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey                                          |
|    graphDeviceIsCompliant        |    Quitado                                                          |
|    graphDeviceIsManaged          |    Quitado                                                          |
|    lastContact                   |    lastSyncDateTime                                                 |
|    lastContactNotification       |    Quitado                                                          |
|    lastContactWorkplaceJoin      |    Quitado                                                          |
|    lastExchangeStatusUtc         |    Quitado                                                          |
|    lastPolicyUpdateUtc           |    Quitado                                                          |
|    mdmStatusKey                  |    complianceStateKey, que hace referencia a la colección complianceStates    |
|    osFamily                      |    operatingSystem                                                  |
|    processorArchitecture         |    Quitado                                                          |
|    referenceId                   |    azureAdDeviceId                                                  |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

En esta tabla se enumeran los cambios realizados en las propiedades que se encuentran en la colección [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities): 

|    Propiedad antigua         |    Cambio/Reemplazo         |
|-------------------------|-------------------------------|
|    enrollmentTypeKey    |    deviceEnrollmentTypeKey    |

En esta tabla se enumeran los cambios realizados en las propiedades que se encuentran en la colección [mamApplications](intune-data-warehouse-collections.md#mamapplications): 

|    Propiedad antigua       |    Cambio/Reemplazo    |
|-----------------------|--------------------------|
|    applicationKey     |    mamApplicationKey     |
|    applicationName    |    mamApplicationName    |
|    applicationId      |    mamApplicationId      |

En esta tabla se enumeran los cambios realizados en las propiedades que se encuentran en la colección [mamApplicationInstances](intune-data-warehouse-collections.md#mamapplicationinstances): 

|    Propiedad antigua     |    Cambio/Reemplazo    |
|---------------------|--------------------------|
|    applicationId    |    mamApplicationId      |
|    deviceId         |    mamDeviceId           |
|    deviceType       |    mamDeviceType         |
|    deviceName       |    mamDeviceName         |

En esta tabla se enumeran los cambios realizados en las propiedades que se encuentran en la colección [mamCheckins](intune-data-warehouse-collections.md#mamcheckins): 

|    Propiedad antigua      |    Cambio/Reemplazo    |
|----------------------|--------------------------|
|    applicationKey    |    mamApplicationKey     |

En esta tabla se enumeran los cambios realizados en las propiedades que se encuentran en la colección [users](intune-data-warehouse-collections.md#users): 

|    Propiedad antigua             |    Cambio/Reemplazo    |
|-----------------------------|--------------------------|
|    startDateInclusiveUtc    |    Quitado               |
|    endDateInclusiveUtc      |    Quitado               |
|    isCurrent                |    Quitado               |

## <a name="1903"></a>1903
_Fecha de publicación: marzo de 2019_

### <a name="v10-changes-reflecting-back-to-beta"></a>Cambios de V1.0 reflejados hasta la versión beta
Cuando V1.0 apareció por primera vez en agosto de 2018, difería en algunos aspectos importantes de la versión beta de API. En marzo de 2019 esos cambios se reflejan en la versión beta de la API. Si tiene informes importantes que usan la versión beta de API, se recomienda encarecidamente cambiar dichos informes a V1.0 para evitar cambios bruscos. Vea la [información de versión de API](reports-api-url.md) para saber más sobre las versiones de API de almacenamiento de datos y compatibilidad con versiones anteriores. 

## <a name="1902"></a>1902 
_Publicado en febrero de 2019_

### <a name="power-bi-compliance-app"></a>Aplicación de cumplimiento de Power BI 

Acceda al almacenamiento de datos de Intune en Power BI Online mediante la aplicación [Cumplimiento de Intune (Almacenamiento de datos)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp). Con esta aplicación de Power BI, ahora puede acceder y compartir informes creados previamente sin necesidad de configuración y sin salir de su explorador web. 

> [!NOTE]
> Hay dos filtros más que se pueden aplicar a la aplicación de cumplimiento de Intune.

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>Agregar filtros adicionales a la aplicación de cumplimiento de Intune
1. Abra la aplicación [Cumplimiento de Intune (almacenamiento de datos)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) en el explorador web.
2. Haga clic en **Dispositivos no compatibles** y seleccione **No compatible** en el filtro **complianceStatus**. 
3. Haga clic en **Dispositivos no compatibles** y seleccione **No disponible aún** en el filtro **complianceStatus**. 

## <a name="1812"></a>1812 
_Fecha de publicación: diciembre de 2018_

### <a name="enrollment-activities-collection-released-to-v10"></a>Colección de actividades de inscripción publicada para v1.0 

La colección de actividades de inscripción ya está disponible en v1.0. Puede usar esta colección para entender el volumen y las tendencias de los errores de inscripción del entorno. Para obtener más información, vea [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities), [enrollmentEventStatuses](intune-data-warehouse-collections.md#enrollmenteventstatuses), [enrollmentFailureCategories](intune-data-warehouse-collections.md#enrollmentfailurecategories) y [enrollmentFailureReasons](intune-data-warehouse-collections.md#enrollmentfailurereasons).

## <a name="1808"></a>1808
_Publicado en agosto de 2018_

### <a name="v10-collections"></a>Colecciones de v1.0  

Ahora puede usar la versión v1.0 del almacenamiento de datos de Intune mediante la configuración del parámetro de consulta `api-version=v1.0`. Las actualizaciones de las colecciones en el almacenamiento de datos son aditivas por naturaleza y no interrumpen los escenarios existentes.

### <a name="enrollment-activities-collection-released-to-beta"></a>Colección de actividades de inscripción publicada para la versión beta

La nueva colección `Enrollment Activities` se ha lanzado en versión beta. Puede usar esta colección para ver los errores más comunes y así comprender cómo evoluciona su suscripción. 


## <a name="1805"></a>1805
_Fecha de publicación: mayo de 2018_

### <a name="correction-to-device-count-in-devices-collection"></a>Corrección al número de dispositivos en la colección **Dispositivos**. 

Se ha realizado una corrección a la colección **Dispositivos** que puede reducir el número total de dispositivos que se filtran por el atributo `isDeleted`. Esta disminución no es un error, sino que es el resultado de la corrección. Para más información sobre la colección **Dispositivos**, consulte [Referencia de las entidades Devices](reports-ref-devices.md). 


## <a name="1801"></a>1801
_Publicado en enero de 2018_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Autenticación de solo aplicación de Almacenamiento de datos de Intune <!-- 1867540 -->

Puede configurar una aplicación con Azure Active Directory (Azure AD) y autenticarla en el Almacenamiento de datos de Intune. Para obtener más información, vea [Autenticación de solo aplicación de Almacenamiento de datos de Intune](data-warehouse-app-only-auth.md).

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Requisitos de credenciales de Azure AD e Intune <!-- 2077525 -->

- Ya no es necesario asignar una licencia de Intune al usuario al acceder al Almacenamiento de datos de Intune (incluida la API).
- Se ha cambiado el nombre del rol de Intune de **Informes** a **Almacenamiento de datos de Intune**. 

    Para obtener más información, consulte [Requisitos de credenciales de Azure AD e Intune](reports-api-url.md#azure-ad-and-intune-credential-requirements).

### <a name="odata-query-options----2077711---"></a>Opciones de consulta OData <!-- 2077711 -->

Puede usar <code>$select</code> como un parámetro de consulta OData. La versión actual admite los siguientes parámetros de consulta OData: <code>$filter</code>, <code>$orderby</code>, <code>$select</code>, <code>$skip</code> y <code>$top</code>. Para obtener más información, vea [Opciones de consulta OData](reports-api-url.md#odata-query-options).

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>Nuevas entidades en el modelo de datos de Data Warehouse <!-- 2077804 -->

- Se ha agregado la entidad [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md). El valor **MobileAppDeviceUserInstallStatus** representa un estado de instalación de aplicación móvil para un dispositivo y un usuario determinados.
- Se ha agregado la entidad [**MobileAppInstallStates**](reports-ref-application.md#mobileappinstallstates). La entidad **MobileAppInstallState** representa el estado de instalación de una aplicación móvil una vez que se ha asignado a un grupo que contiene dispositivos, usuarios o ambos. 

## <a name="1710"></a>1710
_Publicado en noviembre de 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>Limitación de la nueva colección de entidades Usuario actual a los datos de los usuarios activos actualmente <!-- 1544273 -->

La colección de entidades **Usuarios** muestra todos los usuarios de Azure Active Directory (Azure AD) con licencias asignadas en la empresa. Dichos registros incluyen los estados de los usuarios durante el período de recopilación de datos, incluso aunque se haya eliminado a alguno de ellos. Por ejemplo, es posible que durante el último mes se haya agregado a un usuario a Intune y, luego, se haya eliminado. A pesar de que no esté presente a la hora de generar el informe, el usuario en cuestión y su estado sí que figuran en los datos. Una opción podría ser crear un informe que incluya el historial relativo a la duración de la presencia del usuario en sus datos.

Por otro lado, la nueva colección de entidades **Usuario actual** solo contiene los usuarios que no se hayan eliminado. En otras palabras, la colección de entidades **Usuario actual** solo contiene los usuarios que estén activos actualmente. Para obtener más información sobre la colección de entidades **Usuario actual**, consulte [Referencia de la entidad de usuario actual](reports-ref-current-user.md).

## <a name="1709"></a>1709
_Publicado en octubre de 2017_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Colección de entidades de asociación de dispositivos de usuario agregada al modelo de datos Data Warehouse de Intune <!-- 1187917 -->

Ahora puede generar informes y visualizaciones de datos con la información de asociación de dispositivo de usuario que asocia las colecciones de la entidad de dispositivo y de usuario. Es posible tener acceso al modelo de datos a través del archivo de Power BI (PBIX) recuperado de la página de almacenamiento de datos de Intune, a través del punto de conexión de OData o mediante el desarrollo de un cliente personalizado. Para obtener más información, consulte [Asociación de dispositivos de usuario](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Nuevas entidades en el modelo de datos de Data Warehouse <!-- 1479526 --><!-- -->

- La entidad, [**UserDeviceAssociation**](reports-ref-user-device.md), agregada. **UserDeviceAssociation** contiene las asociaciones de dispositivos de usuario que se dan en su organización. Ahora puede generar informes y visualizaciones de datos con la información de asociación de dispositivo de usuario que asocia las colecciones de la entidad de dispositivo y de usuario.  
- Se ha agregado la entidad [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md). **IntuneManagementExtension** contiene entidades para dispositivos móviles que realizan el seguimiento de información como la versión y el estado de la instalación.

## <a name="next-steps"></a>Pasos siguientes
- Conozca las [novedades semanales de Intune](whats-new.md). También podrá obtener información sobre los próximos cambios, notificaciones importantes sobre el servicio e información sobre las versiones anteriores.
- Lea el [Blog de Microsoft Intune](https://go.microsoft.com/fwlink/?LinkID=273882).
