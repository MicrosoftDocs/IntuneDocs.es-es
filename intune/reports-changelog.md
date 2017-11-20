---
title: Registro de cambios del Almacenamiento de datos de Intune | Microsoft Docs
description: Lista de cambios en la API Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b81846c2e45f968184d50d2ea7c50aabb86b4964
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2017
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Registro de cambios en la API Almacenamiento de datos de Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Manténgase al día de los cambios producidos en el Almacén de datos de Intune.

## <a name="1710"></a>1710
_Publicado en octubre de 2017_

### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>La entidad de usuario contiene los datos de usuario más recientes en el modelo de datos de Almacenamiento de datos <!-- 1544273 -->

La primera versión del modelo de datos del Almacenamiento de datos de Intune solo contenía datos de Intune recientes e históricos. Los creadores de informes no podían capturar el estado actual de un usuario. En esta actualización, la [**entidad de usuario**](reports-ref-user.md) se rellenará con los datos más recientes del usuario.

### <a name="new-entity-in-the-in-data-warehouse-data-model----1479526---"></a>Nueva entidad en el modelo de datos de Almacenamiento de datos <!-- 1479526 -->

La entidad, [**UserDeviceAssociation**](reports-ref-user-device.md), agregada. **UserDeviceAssociation** contiene las asociaciones de dispositivos de usuario que se dan en su organización.

## <a name="next-steps"></a>Pasos siguientes
 - Conozca las [novedades semanales de Intune](whats-new.md). También podrá obtener información sobre los próximos cambios, notificaciones importantes sobre el servicio e información sobre las versiones anteriores. 
 - Lea el [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882).