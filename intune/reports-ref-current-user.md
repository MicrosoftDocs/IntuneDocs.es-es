---
title: Usuario actual - Almacenamiento de datos de Intune
titlesuffix: Microsoft Intune
description: Tema de referencia sobre la categoría Usuario de las colecciones de entidades de la API de Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: C10E6752-E925-40AD-ABBF-6B621FB7AFC4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3b94001310f9117b2c3ba7591d40891db891e86d
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="reference-for-current-user-entity"></a>Referencia de la entidad de usuario actual

La categoría **Usuario actual** contiene las propiedades de usuario del modelo de datos. La colección de entidades **Usuario actual** está limitada a los usuarios actualmente activos. La entidad contiene todos los usuarios de Azure Active Directory que actualmente tienen una licencia asignada. La licencia puede ser una licencia de Intune, una licencia híbrida o una licencia de Microsoft Office 365. Si se quitó un usuario, no se representará en la colección Usuario actual. Para una colección que contiene un historial de cambios en el estado de un usuario, consulte [Referencia de la entidad de usuario](reports-ref-user.md).


## <a name="current-user"></a>Usuario actual

La entidad **Usuario actual** muestra todos los usuarios de Azure Active Directory (Azure AD) con licencias asignadas en la empresa.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| UserKey |Identificador único del usuario en el almacenamiento de datos. Clave suplente. |123 |
| UserId |Identificador único del usuario. Se parece a UserKey, pero es una clave natural. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Dirección de correo electrónico del usuario. |John@constoso.com |
| UPN | Nombre principal del usuario. | John@constoso.com |
| DisplayName |Nombre para mostrar del usuario. |Juan |
| IntuneLicensed |Especifica si este usuario tiene licencia de Intune o no. |Verdadero/Falso |
| StartDateInclusiveUTC |Fecha y hora en formato UTC en que se ha creado este usuario en el almacenamiento de datos. |23/11/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Fecha y hora en formato UTC en que se ha modificado por última vez este usuario en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="next-steps"></a>Pasos siguientes
 - Puede usar la colección de entidades **Usuarios** para expandir los datos de usuario a los usuarios que no están activos actualmente. Para más información, consulte [Referencia de la entidad de usuario](reports-ref-user.md).
 - Para más información sobre cómo el almacenamiento de datos realiza un seguimiento de la duración de un usuario en Intune, consulte [Representación de la duración del usuario en el Almacenamiento de datos de Intune](reports-ref-user-timeline.md).
