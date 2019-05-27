---
title: Usuario - Almacenamiento de datos de Intune
titleSuffix: Microsoft Intune
description: Tema de referencia sobre la categoría Usuario de las colecciones de entidades de la API de Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0551327bfe2b320bb91699e1176985bbdf94de92
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66045227"
---
# <a name="reference-for-user-entity"></a>Referencia de la entidad de usuario

La categoría **Usuario** contiene la entidad **Usuario**, que define las propiedades de usuario en el modelo de datos.

## <a name="user"></a>Usuario

La entidad **User** muestra todos los usuarios de Azure Active Directory (Azure AD) con licencias asignadas en la empresa.

La colección de entidades **Usuario** contiene los datos del usuario. Dichos registros incluyen los estados de los usuarios durante el período de recopilación de datos, incluso aunque se haya eliminado a alguno de ellos. Por ejemplo, es posible que durante el último mes se haya agregado a un usuario a Intune y, luego, se haya eliminado. A pesar de que este usuario no esté presente a la hora de generar el informe, el usuario en cuestión y su estado sí que figuran en los datos del mes anterior. Una opción podría ser crear un informe que incluya el historial relativo a la duración de la presencia del usuario en sus datos.

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


## <a name="next-steps"></a>Pasos siguientes
 - Puede usar la colección de entidades **Usuario actual** para limitar los datos de usuario a los usuarios actualmente activos. Para más información, consulte [Referencia de la entidad de usuario actual](reports-ref-current-user.md).
 - Para más información sobre cómo el almacenamiento de datos realiza un seguimiento de la duración de un usuario en Intune, vea [Representación de la duración del usuario en el Almacenamiento de datos de Intune](reports-ref-user-timeline.md).
