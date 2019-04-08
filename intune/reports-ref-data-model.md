---
title: Modelo de datos de Almacenamiento de datos
titleSuffix: Microsoft Intune
description: El almacenamiento de datos de Microsoft Intune muestrea los datos a diario para proporcionar una vista histórica del entorno móvil, en constante cambio.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43e555a27565de43d417adc473d48254d8b7d5a2
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798180"
---
# <a name="microsoft-intune-data-warehouse-data-model"></a>Modelo de datos de Data Warehouse de Microsoft Intune

El Almacenamiento de datos de Intune muestrea los datos a diario para proporcionar un historial del entorno móvil de los dispositivos móviles, en constante cambio. La vista se compone de entidades relacionadas a lo largo del tiempo.

## <a name="entities-entity-sets"></a>Entidades: conjuntos de entidades

El almacenamiento expone los datos en las siguientes áreas de alto nivel:

  -  Aplicaciones y uso habilitados para la protección de aplicaciones
  -  Dispositivos inscritos, propiedades e inventario
  -  Inventario de aplicaciones y software
  -  Configuración de dispositivos y directivas de cumplimiento

Estas áreas contienen las entidades que son significativas para el entorno de Intune. Encontrará más detalles sobre los conjuntos de entidades en los temas siguientes:

  -  [Aplicación](reports-ref-application.md)
  -  [Fecha](reports-ref-date.md)
  -  [Dispositivos](reports-ref-devices.md)
  -  [Extensión de administración de Intune](reports-ref-intunemanagementextension.md)
  -  [Directiva](reports-ref-policy.md)
  -  [Administración de aplicaciones móviles (MAM)](reports-ref-mobile-app-management.md)
  -  [User](reports-ref-user.md)
  -  [Usuario actual](reports-ref-current-user.md)
  -  [Asociación de dispositivos de usuario](reports-ref-user-device.md)

## <a name="relationships-star-schema-model"></a>Relaciones: modelo de esquema de estrella

El almacenamiento organiza las entidades en relaciones que son significativas para el tipo de preguntas que quiere formular. Por ejemplo, puede consultar el número de instalaciones de una aplicación de Android desarrollada internamente. La estructura del almacenamiento de datos permite comprender mejor el entorno móvil. A su vez, las herramientas analíticas, como Microsoft Power BI, pueden usar el modelo de datos de Almacenamiento de datos para crear visualizaciones y paneles dinámicos.

Las entidades y las relaciones usan un modelo de esquema de estrella. Un esquema de estrella pone en correlación los hechos en una dimensión temporal. En el contexto del modelo, un *hecho* es una medida cuantitativa, como el número de dispositivos, el número de aplicaciones o la hora de inscripción. Las tablas de hechos almacenan una gran cantidad de datos. Pueden llegar a tener un tamaño considerable, de modo que normalmente limitan la información a 30 días. Una *dimensión* proporciona el contexto de los hechos. Mientras que el hecho mide lo ocurrido, las dimensiones indican a quién le ha ocurrido. Las tablas de dimensiones, como la tabla **Usuario**, son más pequeñas y pueden retener datos durante períodos de tiempo más largos que las tablas de hechos. 

Los modelos de esquema de estrella están optimizados para la flexibilidad y el análisis de datos, de modo que pueda crear los informes necesarios para entender su entorno móvil en constante evolución.

## <a name="time-daily-snapshots"></a>Tiempo: instantáneas diarias

El almacén de datos es descendiente en relación con los datos de Intune. Todos los días a medianoche (UTC) Intune toma una instantánea y la guarda en el almacén. La duración de las instantáneas retenidas varía en función de cada tabla de hechos. En algunos casos puede ser de 7 días, en otros de 30, o incluso superiores.

## <a name="next-steps"></a>Pasos siguientes

 - Para más información sobre cómo el almacenamiento de datos realiza un seguimiento de la duración de un usuario en Intune, vea [Representación de la duración del usuario en el Almacenamiento de datos de Intune](reports-ref-user-timeline.md).
 - Para más información sobre cómo trabajar con almacenamientos de datos, vea [Create First Data WareHouse](https://www.codeproject.com/Articles/652108/Create-First-Data-WareHouse) (Creación del primer almacenamiento de datos).
 - Para obtener más información sobre cómo trabajar con Power BI y un almacén de datos, consulte [Creación de un informe de Power BI nuevo mediante la importación de un conjunto de datos](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-new-report/). 
