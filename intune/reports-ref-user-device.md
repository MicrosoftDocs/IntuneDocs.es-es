---
title: "Asociación de dispositivos de usuario - Almacenamiento de datos de Intune | Microsoft Docs"
description: Lista de cambios en la API Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9032ffa547daeb19e694a0245dfec676d85a5793
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="user-device-association"></a>Asociación de dispositivos de usuario

La entidad **UserDeviceAssociation** contiene las asociaciones de dispositivos de usuario que se dan en su organización.

| Nombre               | Descripción                                                                                      | Ejemplo                |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
| UserKey            | Identificador único del usuario en el almacenamiento de datos. (Clave suplente).                              | 123                    |
| DeviceKey          | Identificador único del dispositivo en el almacenamiento de datos.                                            | 123                    |
| CreatedDateTimeUTC | Fecha y hora de creación de la asociación de dispositivos de usuario. Utiliza el formato UTC.                                | 23/11/2016 12:00:00 AM |
| IsDeleted          | Indica que el usuario ha anulado la inscripción del dispositivo y que la asociación ya no está activa. | Verdadero/Falso             |
| EndedDateTimeUTC   | Fecha y hora (UTC) en que IsDeleted cambió a **True**.                                              | 06/23/2017 12:00:00 AM |
