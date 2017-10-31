---
title: Usuario | Microsoft Docs
description: "Tema de referencia sobre la categoría Usuario de las colecciones de entidades de la API de Almacenamiento de datos de Intune."
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: be8b7041882539c4e379074cffea385f582f686e
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-user-entity"></a>Referencia de la entidad User

La categoría **Usuario** contiene la entidad **User**, que define las propiedades de usuario y agente del modelo de datos.

**User**

La entidad **User** muestra todos los usuarios de Azure Active Directory (Azure AD) con licencias asignadas en la empresa.

| Propiedad  | Descripción | Ejemplo |
|---------|------------|--------|
| UserKey |Identificador único del usuario en el almacenamiento de datos. Clave suplente. |123 |
| UserId |Identificador único del usuario. Se parece a UserKey, pero es una clave natural. |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |Dirección de correo electrónico del usuario. |John@constoso.com |
| DisplayName |Nombre para mostrar del usuario. |Juan |
| IntuneLicensed |Especifica si este usuario tiene licencia de Intune o no. |Verdadero/Falso |
| IsDeleted |Indica si se ha actualizado el registro de este usuario.  True: este usuario tiene un nuevo registro con campos actualizados en esta tabla. False: registro más reciente de este usuario. |Verdadero/Falso |
| StartDateInclusiveUTC |Fecha y hora en formato UTC en que se ha creado este usuario en el almacenamiento de datos. |23/11/2016 12:00:00 AM |
| EndDateExclusiveUTC |Fecha y hora en formato UTC en que IsDeleted ha cambiado a True. |23/11/2016 12:00:00 AM |
| IsCurrent |Indica si este registro de usuario está actualizado o no en el almacenamiento de datos. |Verdadero/Falso |
| RowLastModifiedDateTimeUTC |Fecha y hora en formato UTC en que se ha modificado por última vez este usuario en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

