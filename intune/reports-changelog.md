---
title: Registro de cambios del Almacenamiento de datos de Intune
titlesuffix: Microsoft Intune
description: En este tema se proporciona una lista de cambios para la API Data Warehouse de Microsoft Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 20c9c1bf5eea12407cba2e00288a039b74fcaca7
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565645"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registro de cambios en la API Almacenamiento de datos de Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Manténgase al día de los cambios producidos en el Almacén de datos de Intune.

## <a name="1902"></a>1902 
_Publicado en febrero de 2019_

### <a name="power-bi-compliance-app"></a>Aplicación del cumplimiento de Power BI 

Obtener acceso a su almacén de datos de Intune en Power BI Online mediante el [cumplimiento de Intune (Data Warehouse)](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance) app. Con esta aplicación de Power BI, ahora puede acceder y compartir informes creados previamente sin necesidad de configuración y sin salir de su explorador web. 

> [!NOTE]
> Hay dos filtros adicionales que puede aplicar a la aplicación del cumplimiento de Intune.

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>Agregar filtros adicionales a la aplicación del cumplimiento de Intune
1. Abra el [cumplimiento de Intune (Data Warehouse)](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance) aplicación en los exploradores web.
2. Haga clic en **dispositivos no conformes** y seleccione **no compatible** en el **complianceStatus** filtro. 
3. Haga clic en **desconocido dispositivos** y seleccione **todavía no está disponible** en el **complianceStatus** filtro. 

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

 - Se ha agregado la entidad [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md#mobileappdeviceuserinstallstatus). El valor **MobileAppDeviceUserInstallStatus** representa un estado de instalación de aplicación móvil para un dispositivo y un usuario determinados.
 - Se ha agregado la entidad [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstate). La entidad **MobileAppInstallState** representa el estado de instalación de una aplicación móvil una vez que se ha asignado a un grupo que contiene dispositivos, usuarios o ambos. 

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
