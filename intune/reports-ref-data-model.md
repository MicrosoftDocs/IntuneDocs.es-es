---
title: Modelo de datos de Almacenamiento de datos | Microsoft Docs
description: "El Almacenamiento de datos de Intune muestrea los datos a diario para proporcionar una vista histórica del entorno móvil, en constante cambio."
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f720d5f9dbf91d7f098a640d640f8f35136da4fc
ms.sourcegitcommit: 5279a0bb8c5aef79aa57aa247ad95888ffe5a12b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2017
---
# <a name="data-warehouse-data-model"></a>Modelo de datos de Almacenamiento de datos

El Almacenamiento de datos de Intune muestrea los datos a diario para proporcionar una vista histórica del entorno móvil, en constante cambio.

Los datos extraídos del inquilino se agregan en un almacenamiento de datos. El almacenamiento es un conjunto de entidades y relaciones que son significativas para el tipo de preguntas que quiere realizar. Por ejemplo, puede revisar el número de instalaciones de una aplicación de Android desarrollada internamente por día durante la última semana para evaluar si la tendencia de las instalaciones va en aumento. La estructura del almacenamiento de datos permite comprender mejor el entorno móvil. A su vez, las herramientas analíticas, como Microsoft Power BI, pueden usar el modelo de datos de Almacenamiento de datos para crear visualizaciones y paneles dinámicos.

La estructura del Almacenamiento de datos de Intune usa un modelo de esquema de estrella. Un esquema de estrella organiza los hechos en una dimensión de tiempo. En el contexto del modelo, un *hecho* es una medida cuantitativa, como el número de dispositivos, el número de aplicaciones o la hora de inscripción. En este mismo contexto, una *dimensión* es un conjunto de categorías y su relación jerárquica. Por ejemplo, los días se agrupan en meses y los meses, en años. Los modelos de esquema de estrella están optimizados para la flexibilidad y el análisis de datos, de modo que pueda crear los informes necesarios para entender su entorno móvil en constante evolución.

El almacenamiento expone los datos en las siguientes categorías de alto nivel:
  -  Aplicaciones y uso habilitados para la protección de aplicaciones
  -  Dispositivos inscritos, propiedades e inventario
  -  Inventario de aplicaciones y software
  -  Configuración de dispositivos y directivas de cumplimiento

**Conjuntos de entidades del modelo de datos**

Los conjuntos de entidades se denominan colecciones de entidades en el modelo de datos. Estos conjuntos contienen entidades que definen los datos recopilados en el modelo. Cada conjunto de entidades proporciona un punto de acceso en el modelo de datos de Almacenamiento de datos. Encontrará información sobre las siguientes categorías de entidades:

  -  [Aplicación](reports-ref-application.md)
  -  [Fecha](reports-ref-date.md)
  -  [Dispositivos](reports-ref-devices.md)
  -  [Extensión de administración de Intune](reports-ref-intunemanagementextension.md)
  -  [Directiva](reports-ref-policy.md)
  -  [Administración de aplicaciones móviles (MAM)](reports-ref-mobile-app-management.md)
  -  [User](reports-ref-user.md)
  -  [Asociación de dispositivos de usuario](reports-ref-user-device.md)