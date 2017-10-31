---
title: "Administración de aplicaciones móviles (MAM) | Microsoft Docs"
description: "Tema de referencia sobre la categoría Administración de aplicaciones móviles de las colecciones de entidades de la API de Almacenamiento de datos de Intune."
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 32b5f3515c0b77ea8f411c1c1f42e7b44669ca23
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/20/2017
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Referencia de entidades de administración de aplicaciones móviles (MAM)

La categoría **Administración de aplicaciones móviles** contiene entidades para las aplicaciones móviles como las siguientes:

  -  Aplicaciones
  -  Instancias
  -  Estado de registro
  -  Estado de mantenimiento
  -  Estado de directiva
  -  Estado de inscripción
  -  Tipos de plataforma

## <a name="mamapplication"></a>MamApplication

La entidad **MamApplication** muestra las aplicaciones de línea de negocio (LOB) que se administran mediante la administración de aplicaciones móviles (MAM) sin inscripción en la empresa.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| ApplicationKey |Identificador único de la aplicación MAM en el almacenamiento de datos. |123 |
| ApplicationName |Nombre de la aplicación MAM. |"Palabra" |
| ApplicationId |Identificador de la aplicación MAM. |b66bc706-ffff-7437-0340-032819502773 |
| IsDeleted |Indica si se ha actualizado el registro de la aplicación MAM. <br>True: la aplicación MAM tiene un nuevo registro con campos actualizados en esta tabla. <br>False: registro más reciente de esta aplicación MAM. |Verdadero/Falso |
| StartDateInclusiveUTC |Fecha y hora en formato UTC en que se ha creado esta aplicación MAM en el almacenamiento de datos. |23/11/2016 12:00:00 AM |
| DeletedDateUTC |Fecha y hora en formato UTC en que IsDeleted ha cambiado a True. |23/11/2016 12:00:00 AM |
| RowLastModifiedDateTimeUTC |Fecha y hora en formato UTC en que se ha modificado por última vez esta aplicación MAM en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="mamapplicationinstance"></a>MamApplicationInstance

La entidad **MamApplicationInstance** muestra las aplicaciones de administración de aplicaciones móviles (MAM) administradas como instancias singulares por usuario y dispositivo. Todos los usuarios y dispositivos enumerados en la entidad están protegidos, como si tuvieran al menos una directiva de MAM asignada.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| ApplicationInstanceKey |Identificador único de la instancia de la aplicación MAM en el almacenamiento de datos. Clave suplente. |123 |
| UserId |Identificador del usuario que tiene instalada esta aplicación MAM. |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationInstanceId |Identificador único de la instancia de la aplicación MAM. Se parece a ApplicationInstanceKey, pero el identificador es una clave natural. |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationId |Identificador de esta aplicación MAM. |com.microsoft.groupies-daily.<IOS> |
| ApplicationVersion |Versión de esta aplicación MAM. |2 |
| CreatedDate |Fecha en la que se ha creado este registro de la instancia de la aplicación MAM. El valor puede ser NULL. |23/11/2016 12:00:00 AM |
| Plataforma |Plataforma del dispositivo en el que está instalada esta aplicación MAM. |2 |
| PlatformVersion |Versión de la plataforma del dispositivo en el que está instalada esta aplicación MAM. |2.2 |
| SdkVersion |Versión de SDK de MAM con la que se ha encapsulado esta aplicación MAM. |3.2 |
| DeviceId |Identificador del dispositivo en el que está instalada esta aplicación MAM. |b66bc706-ffff-7437-0340-032819502773 |
| DeviceName |Nombre del dispositivo en el que está instalada esta aplicación MAM. |"MiDispositivo" |
| IsDeleted |Indica si se ha actualizado el registro de la instancia de esta aplicación MAM. <br>True: la instancia de esta aplicación MAM tiene un nuevo registro con campos actualizados en esta tabla. <br>False: registro más reciente de la instancia de esta aplicación MAM. |Verdadero/Falso |
| StartDateInclusiveUtc |Fecha y hora en formato UTC en que se ha creado la instancia de esta aplicación MAM en el almacenamiento de datos. |23/11/2016 12:00:00 AM |
| DeletedDateUtc |Fecha y hora en formato UTC en que IsDeleted ha cambiado a True. |23/11/2016 12:00:00 AM |
| RowLastModifiedDateTimeUtc |Fecha y hora en formato UTC en que se ha modificado por última vez la instancia de esta aplicación MAM en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="mamcheckin"></a>MamCheckin

La entidad **MamCheckin** representa los datos recopilados cuando una instancia de la aplicación de administración de aplicaciones móviles (MAM) se ha registrado con el servicio de Intune. 

> [!Note]  
> Cuando una instancia de la aplicación se registra varias veces al día, el almacenamiento de datos la almacena como un único registro.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| DateKey |Clave de fecha en la que se ha anotado en el almacenamiento de datos el registro de la aplicación MAM. | 20160703 |
| ApplicationInstanceKey |Clave de la instancia de la aplicación asociada a este registro de la aplicación MAM. |2/5/1900 12:00:00 AM |
| UserKey |Clave del usuario asociado a este registro de la aplicación MAM. |12/1/1900 12:00:00 AM |
| ApplicationKey |Clave de la aplicación MAM que ha registrado. |10/1/1900 12:00:00 AM |
| DeviceHealthKey |Clave de DeviceHealth asociada a este registro de la aplicación MAM. |2/1/1900 12:00:00 AM |
| PlatformKey |Representa la plataforma del dispositivo asociado a este registro de la aplicación MAM. |1/1/1900 12:00:00 AM |
| EffectiveAppliedPolicyKey |Representa la directiva aplicada efectiva que está asociada a la aplicación MAM registrada. Una directiva aplicada efectiva es el resultado de la combinación de todas las directivas pertinentes para una aplicación y un usuario determinados. |2/5/1900 12:00:00 AM |
| LastCheckInDate |Fecha y hora en que se ha registrado por última vez esta aplicación MAM. El valor puede ser NULL. |23/11/2016 12:00:00 AM |

## <a name="mamdevicehealth"></a>MamDeviceHealth

La entidad **MamDeviceHealth** representa los dispositivos que tienen implementadas directivas de administración de aplicaciones móviles (MAM), incluso si están liberados.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| DeviceHealthKey |Identificador único del dispositivo y su mantenimiento asociado en el almacenamiento de datos. Clave suplente. |1/1/1900 12:00:00 AM |
| DeviceHealth |Identificador único del dispositivo y su mantenimiento asociado. Es parecido a DeviceHealthKey, pero el identificador es una clave natural. |1/1/1900 12:00:00 AM |
| DeviceHealthName |Representa el estado del dispositivo. <br>No disponible: no hay información sobre este dispositivo. <br>Correcto: el dispositivo no está liberado. <br>Incorrecto: el dispositivo está liberado. |No disponible Correcto Incorrecto |
| RowLastModifiedDateTimeUtc |Fecha y hora en formato UTC en que se ha modificado por última vez el estado del dispositivo MAM específico en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

La entidad **MamEffectivePolicy** muestra todas las directivas efectivas de administración de aplicaciones móviles (MAM) aplicadas en la organización. Una directiva aplicada efectiva es el resultado de la combinación de todas las directivas pertinentes para una aplicación y un usuario determinados.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| EffectivePolicyKey |Identificador único de la directiva de MAM efectiva en el almacenamiento de datos. |2 |
| RealPolicyKey |Identificador único de la directiva de MAM creada por profesionales de TI. |1 |
| RowCreatedDateTimeUtc |Fecha y hora en formato UTC en que se ha creado esta directiva de MAM efectiva en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="mamglobalapplication"></a>MamGlobalApplication

La entidad **MamGlobalApplication** muestra las aplicaciones de la tienda que se administran mediante la administración de aplicaciones móviles (MAM) sin inscripción en la empresa.

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| ApplicationKey |Identificador único de la aplicación de la tienda en el almacenamiento de datos, conocido como clave suplente. |123 |
| ApplicationId |Identificador único de la aplicación de la tienda. El identificador se parece a ApplicationKey, pero es una clave natural. |com.microsoft.skydrive.<ios> |
| ApplicationName |Nombre de aplicación global de MAM. |Skydrive |
| RowLastModifiedDateTimeUtc |Fecha y hora en formato UTC en que se ha modificado por última vez esta aplicación global de MAM específica en el almacenamiento de datos. |23/11/2016 12:00:00 AM |

## <a name="mamplatform"></a>MamPlatform

La entidad **MamPlatform** muestra nombres y tipos de plataforma en los que se ha instalado una aplicación de administración de aplicaciones móviles (MAM).

| Propiedad | Descripción | Ejemplo |
|---------|------------|--------|
| PlatformKey |Identificador único de la plataforma en el almacenamiento de datos. Clave suplente. |123 |
| Plataforma |Identificador único de la plataforma. Se parece a PlatformKey, pero es una clave natural. |123 |
| PlatformName |Nombre de la plataforma. |No disponible <br>Ninguno <br>Windows <br>iOS <br>Android. |
| RowLastModifiedDateTimeUtc |Fecha y hora en formato UTC en que se ha modificado por última vez esta plataforma en el almacenamiento de datos. |23/11/2016 12:00:00 AM |
