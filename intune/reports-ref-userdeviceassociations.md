---
title: "Asociación de dispositivos del usuario | Microsoft Docs"
description: "Tema de referencia sobre la categoría Asociación de dispositivos del usuario de las colecciones de entidades de la API de Almacenamiento de datos de Intune."
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 09/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: BCDBABCB-A7B1-42F2-BDD1-D055E33F2239
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 490e29f87c65875a385472e6abe9400363383f9b
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-user-device-association-entity"></a>Referencia de la entidad Asociación de dispositivos del usuario

La categoría **Asociación de dispositivos del usuario** contiene la entidad **Asociación de dispositivos del usuario** que se usa para definir las asociaciones de dispositivos en la organización.

**Asociación de dispositivos del usuario**

La entidad **Asociación de dispositivos del usuario** representa las asociaciones de dispositivos en la organización.

| Nombre               | Descripción                                                                                      | Ejemplo                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | Identificador único del usuario en el almacenamiento de datos. Clave suplente.                             | 123                    |
| DeviceKey          | Identificador único del dispositivo en el almacenamiento de datos.                                           | 123                    |
| CreatedDateTimeUTC | Fecha y hora (UTC) en que se creó la asociación de dispositivos del usuario.                               | 23/11/2016 12:00:00 AM |
| IsDeleted          | Indica que el usuario ha anulado la inscripción del dispositivo y que la asociación ya no está activa. | True                   |
| EndedDateTimeUTC   | Fecha y hora (UTC) en que IsDeleted cambió a **True**.                                         | 06/23/2017 12:00:00 AM |