---
title: Registro de cambios del Almacenamiento de datos de Intune | Microsoft Docs
description: Lista de cambios en la API Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d1078dfeebae22f0754502935c983db13de60a60
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/30/2017
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registro de cambios en la API Almacenamiento de datos de Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Manténgase al día de los cambios producidos en el Almacén de datos de Intune.

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
