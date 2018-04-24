---
title: Registro de cambios del Almacenamiento de datos de Intune
titlesuffix: Microsoft Intune
description: Lista de cambios en la API Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8e11585adf570ba9155861f89688c33ac6cecbeb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registro de cambios en la API Almacenamiento de datos de Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Manténgase al día de los cambios producidos en el Almacén de datos de Intune.

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

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>Nuevas entidades en el modelo de datos de almacenamiento de datos <!-- 2077804 -->

 - Se ha agregado la entidad [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md#mobileappdeviceuserinstallstatus). El valor **MobileAppDeviceUserInstallStatus** representa un estado de instalación de aplicación móvil para un dispositivo y un usuario determinados.
 - Se ha agregado la entidad [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstate). La entidad **MobileAppInstallState** representa el estado de instalación de una aplicación móvil una vez que se ha asignado a un grupo que contiene dispositivos, usuarios o ambos. 

## <a name="1710"></a>1710
_Publicado en noviembre de 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>Limitación de la nueva colección de entidades "Usuario actual" a los datos de los usuarios activos actualmente <!-- 1544273 -->

La colección de entidades **Usuarios** muestra todos los usuarios de Azure Active Directory (Azure AD) con licencias asignadas en la empresa. Dichos registros incluyen los estados de los usuarios durante el período de recopilación de datos, incluso aunque se haya eliminado a alguno de ellos. Por ejemplo, es posible que durante el último mes se haya agregado a un usuario a Intune y, luego, se haya eliminado. A pesar de que no esté presente a la hora de generar el informe, el usuario en cuestión y su estado sí que figuran en los datos. Una opción podría ser crear un informe que incluya el historial relativo a la duración de la presencia del usuario en sus datos.

Por otro lado, la nueva colección de entidades **Usuario actual** solo contiene los usuarios que no se hayan eliminado. En otras palabras, la colección de entidades **Usuario actual** solo contiene los usuarios que estén activos actualmente. Para obtener más información sobre la colección de entidades **Usuario actual**, consulte [Referencia de la entidad de usuario actual](reports-ref-current-user.md).

## <a name="1709"></a>1709
_Publicado en octubre de 2017_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Colección de entidades de asociación de dispositivos de usuario agregada al modelo de datos de Almacenamiento de datos de Intune <!-- 1187917 -->

Ahora puede generar informes y visualizaciones de datos con la información de asociación de dispositivo de usuario que asocia las colecciones de la entidad de dispositivo y de usuario. Es posible tener acceso al modelo de datos a través del archivo de Power BI (PBIX) recuperado de la página de almacenamiento de datos de Intune, a través del punto de conexión de OData o mediante el desarrollo de un cliente personalizado. Para obtener más información, consulte [Asociación de dispositivos de usuario](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Nuevas entidades en el modelo de datos de almacenamiento de datos <!-- 1479526 --><!-- -->

 - La entidad, [**UserDeviceAssociation**](reports-ref-user-device.md), agregada. **UserDeviceAssociation** contiene las asociaciones de dispositivos de usuario que se dan en su organización. Ahora puede generar informes y visualizaciones de datos con la información de asociación de dispositivo de usuario que asocia las colecciones de la entidad de dispositivo y de usuario.  
 - Se ha agregado la entidad [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md). **IntuneManagementExtension** contiene entidades para dispositivos móviles que realizan el seguimiento de información como la versión y el estado de la instalación.

## <a name="next-steps"></a>Pasos siguientes
 - Conozca las [novedades semanales de Intune](whats-new.md). También podrá obtener información sobre los próximos cambios, notificaciones importantes sobre el servicio e información sobre las versiones anteriores.
 - Lea el [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882).
