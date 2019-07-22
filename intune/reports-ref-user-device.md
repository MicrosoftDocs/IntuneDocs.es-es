---
title: Asociación de dispositivos de usuario - Almacenamiento de datos de Intune
titleSuffix: Microsoft Intune
description: La entidad userDeviceAssociation contiene las asociaciones de dispositivos de usuario que se dan en su organización.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8d24716f65d5ff8afba5fc0a89cfef082712429
ms.sourcegitcommit: c3ac858bbadb63d248ed54069e48160d703bbaf2
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313670"
---
# <a name="reference-for-user-device-association-entity"></a>Referencia de la entidad Asociación de dispositivos del usuario

La entidad **userDeviceAssociation** contiene las asociaciones de dispositivos de usuario que se dan en su organización.

## <a name="userdeviceassociations"></a>userDeviceAssociations


|        Nombre        |                                           Descripción                                            |        Ejemplo         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      userKey       |              Identificador único del usuario en el almacenamiento de datos. (Clave suplente).               |          123           |
|     deviceKey      |                      Identificador único del dispositivo en el almacenamiento de datos.                      |          123           |
| createdDateTimeUTC |           Fecha y hora de creación de la asociación de dispositivos de usuario. Utiliza el formato UTC.           | 23/11/2016 12:00:00 AM |
|     isDeleted      | Indica que el usuario ha anulado la inscripción del dispositivo y que la asociación ya no está activa. |       Verdadero/Falso       |
|  endedDateTimeUTC  |              Fecha y hora (UTC) en que IsDeleted cambió a <strong>True</strong>.               | 06/23/2017 12:00:00 AM |

## <a name="next-steps"></a>Pasos siguientes

- Obtenga más información sobre [Data Warehouse de Intune](reports-nav-create-intune-reports.md).
