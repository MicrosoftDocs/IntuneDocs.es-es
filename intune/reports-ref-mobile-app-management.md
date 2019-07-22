---
title: Administración de aplicaciones móviles (MAM)
titleSuffix: Microsoft Intune
description: Tema de referencia sobre la categoría Administración de aplicaciones móviles de las colecciones de entidades de la API de Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c549a7063883f637ac7b5316e767b159d2328d0b
ms.sourcegitcommit: c3ac858bbadb63d248ed54069e48160d703bbaf2
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313654"
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Referencia de entidades de administración de aplicaciones móviles (MAM)

La categoría **Administración de aplicaciones móviles** contiene entidades para las aplicaciones móviles como las siguientes:

- Aplicaciones
- Instancias
- Estado de registro
- Estado de mantenimiento
- Estado de directiva
- Estado de inscripción
- Tipos de plataforma

## <a name="mamapplications"></a>mamApplication

La entidad **mamApplication** muestra las aplicaciones de línea de negocio (LOB) que se administran mediante la administración de aplicaciones móviles (MAM) sin inscripción en la empresa.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| mamApplicationKey |Identificador único de la aplicación MAM. | 432 |
| mamApplicationName |Nombre de la aplicación MAM. |Nombre de ejemplo de la aplicación MAM |
| mamApplicationId |Identificador de la aplicación MAM. | 123 |
| isDeleted |Indica si se ha actualizado el registro de la aplicación MAM. <br>True: la aplicación MAM tiene un nuevo registro con campos actualizados en esta tabla. <br>False: registro más reciente de esta aplicación MAM. |Verdadero/Falso |
| startDateInclusiveUTC |Fecha y hora en formato UTC en que se ha creado esta aplicación MAM en el almacenamiento de datos. |23/11/2016 12:00:00 AM |
| deletedDateUTC |Fecha y hora en formato UTC en que IsDeleted ha cambiado a True. |23/11/2016 12:00:00 AM |
| rowLastModifiedDateTimeUTC |Fecha y hora en formato UTC en que se ha modificado por última vez esta aplicación MAM en el almacenamiento de datos. |23/11/2016 12:00:00 AM |


## <a name="mamapplicationinstances"></a>mamApplicationInstance

La entidad **mamApplicationInstance** muestra las aplicaciones de administración de aplicaciones móviles (MAM) administradas como instancias singulares por usuario y dispositivo. Todos los usuarios y dispositivos enumerados en la entidad están protegidos, como si tuvieran al menos una directiva de MAM asignada.


|          Propiedad          |                                                                                                  Descripción                                                                                                  |               Ejemplo                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   applicationInstanceKey   |                                                               Identificador único de la instancia de la aplicación MAM en el almacenamiento de datos. Clave suplente.                                                                |                 123                  |
|           userId           |                                                                              Identificador del usuario que tiene instalada esta aplicación MAM.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   applicationInstanceId    |                                              Identificador único de la instancia de la aplicación MAM. Se parece a ApplicationInstanceKey, pero el identificador es una clave natural.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | Identificador de la aplicación MAM para la que se creó esta instancia de la aplicación MAM.   | 23/11/2016 12:00:00 AM   |
|     applicationVersion     |                                                                                     Versión de esta aplicación MAM.                                                                                      |                  2                   |
|        createdDate         |                                                                 Fecha en la que se ha creado este registro de la instancia de la aplicación MAM. El valor puede ser NULL.                                                                 |        23/11/2016 12:00:00 AM        |
|          plataforma          |                                                                          Plataforma del dispositivo en el que está instalada esta aplicación MAM.                                                                           |                  2                   |
|      platformVersion       |                                                                      Versión de la plataforma del dispositivo en el que está instalada esta aplicación MAM.                                                                       |                 2.2                  |
|         sdkVersion         |                                                                            Versión de SDK de MAM con la que se ha encapsulado esta aplicación MAM.                                                                            |                 3.2                  |
| mamDeviceId | Identificador de dispositivo al que está asociada la instancia de la aplicación MAM.   | 23/11/2016 12:00:00 AM   |
| mamDeviceType | Tipo de dispositivo al que está asociada la instancia de la aplicación MAM.   | 23/11/2016 12:00:00 AM   |
| mamDeviceName | Nombre de dispositivo al que está asociada la instancia de la aplicación MAM.   | 23/11/2016 12:00:00 AM   |
|         isDeleted          | Indica si se ha actualizado el registro de la instancia de esta aplicación MAM. <br>True: la instancia de esta aplicación MAM tiene un nuevo registro con campos actualizados en esta tabla. <br>False: registro más reciente de la instancia de esta aplicación MAM. |              Verdadero/Falso              |
|   startDateInclusiveUtc    |                                                              Fecha y hora en formato UTC en que se ha creado la instancia de esta aplicación MAM en el almacenamiento de datos.                                                               |        23/11/2016 12:00:00 AM        |
|       deletedDateUtc       |                                                                             Fecha y hora en formato UTC en que IsDeleted ha cambiado a True.                                                                              |        23/11/2016 12:00:00 AM        |
| rowLastModifiedDateTimeUtc |                                                           Fecha y hora en formato UTC en que se ha modificado por última vez la instancia de esta aplicación MAM en el almacenamiento de datos.                                                            |        23/11/2016 12:00:00 AM        |


## <a name="mamcheckins"></a>mamCheckin

La entidad **mamCheckin** representa los datos recopilados cuando una instancia de la aplicación de administración de aplicaciones móviles (MAM) se ha registrado con el servicio de Intune. 

> [!Note]  
> Cuando una instancia de la aplicación se registra varias veces al día, el almacenamiento de datos la almacena como un único registro.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| dateKey |Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro de la aplicación MAM. | 20160703 |
| applicationInstanceKey |Clave de la instancia de la aplicación asociada a este registro de la aplicación MAM. | 123 |
| userKey |Clave del usuario asociado a este registro de la aplicación MAM. | 4323 |
| mamApplicationKey |Clave de aplicación asociada con el registro de la aplicación MAM. | 432 |
| deviceHealthKey |Clave de DeviceHealth asociada a este registro de la aplicación MAM. | 321 |
| platformKey |Representa la plataforma del dispositivo asociado a este registro de la aplicación MAM. |123 |
| effectiveAppliedPolicyKey |Representa la directiva aplicada efectiva que está asociada a la aplicación MAM registrada. Una directiva aplicada efectiva es el resultado de la combinación de todas las directivas pertinentes para una aplicación y un usuario determinados. | 322 |
| pastCheckInDate |Fecha y hora en que se ha registrado por última vez esta aplicación MAM. El valor puede ser NULL. |23/11/2016 12:00:00 AM |


## <a name="mamdevicehealth"></a>mamDeviceHealth

La entidad **mamDeviceHealth** representa los dispositivos que tienen implementadas directivas de administración de aplicaciones móviles (MAM), incluso aunque estén liberados.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| deviceHealthKey |Identificador único del dispositivo y su mantenimiento asociado en el almacenamiento de datos. Clave suplente. |123 |
| deviceHealth |Identificador único del dispositivo y su mantenimiento asociado. Es parecido a DeviceHealthKey, pero el identificador es una clave natural. |b66bc706-ffff-7777-0340-032819502773 |
| deviceHealthName |Representa el estado del dispositivo. <br>No disponible: no hay información sobre este dispositivo. <br>Correcto: el dispositivo no está liberado. <br>Incorrecto: el dispositivo está liberado. |No disponible Correcto Incorrecto |
| rowLastModifiedDateTimeUtc |Fecha y hora en formato UTC en que se ha modificado por última vez el estado del dispositivo MAM específico en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="mameffectivepolicies"></a>mamEffectivePolicies

La entidad **mamEffectivePolicy** muestra todas las directivas efectivas de administración de aplicaciones móviles (MAM) aplicadas en la organización. Una directiva aplicada efectiva es el resultado de la combinación de todas las directivas pertinentes para una aplicación y un usuario determinados.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| effectivePolicyKey |Identificador único de la directiva de MAM efectiva en el almacenamiento de datos. |2 |
| realPolicyKey |Identificador único de la directiva de MAM creada por profesionales de TI. |1 |
| rowCreatedDateTimeUtc |Fecha y hora en formato UTC en que se ha creado esta directiva de MAM efectiva en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="mamplatforms"></a>mamPlatform

La entidad **mamPlatform** muestra nombres y tipos de plataforma en los que se ha instalado una aplicación de administración de aplicaciones móviles (MAM).


|          Propiedad          |                                    Descripción                                    |                         Ejemplo                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        platformKey         |     Identificador único de la plataforma en el almacenamiento de datos. Clave suplente.      |                           123                           |
|          plataforma          | Identificador único de la plataforma. Se parece a PlatformKey, pero es una clave natural. |                           123                           |
|        platformName        |                                   Nombre de la plataforma.                                   | No disponible <br>Ninguno <br>Windows <br>iOS <br>Android. |
| rowLastModifiedDateTimeUtc | Fecha y hora en formato UTC en que se ha modificado por última vez esta plataforma en el almacenamiento de datos.  |                 23/11/2016 12:00:00 AM                  |

