---
title: Agregar identificadores IMEI a Intune
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda cómo agregar identificadores corporativos (números de IMEI) a Microsoft Intune. "
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 15415f9f31d520d66257df3a7e134e4b1de8467c
ms.openlocfilehash: 8c9e6b39ee01697d993e5738ec35e8a64fc8e236
ms.lasthandoff: 04/07/2017

---

# <a name="add-corporate-identifiers"></a>Adición de identificadores corporativos

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Como administrador de TI, puede crear e importar un archivo de valores separados por comas (.csv) que incluye los números de identidad internacional de equipos móviles (IMEI) para identificar los dispositivos de la empresa. Cada número IMEI puede tener detalles especificados en la lista para fines administrativos.

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

## <a name="add-corporate-identifiers"></a>Adición de identificadores corporativos
Para crear la lista, cree una lista de dos columnas de valores separados por comas (.csv) sin un encabezado. Agregue el identificador IMEI en la columna izquierda y los detalles en la columna derecha. Los detalles están limitados a 128 caracteres y son solo de uso administrativo. Los detalles no se muestran en el dispositivo. El límite actual es 500 filas por archivo. csv.

**Cargar un archivo .csv con números de serie**: cree una lista de valores separados por comas (.csv) de dos columnas sin encabezado y limítela a 5000 dispositivos o a 5 MB por archivo .csv. 

|||
|-|-|
|&lt;IMEI n.º 1&gt;|&lt;Detalles del dispositivo n.º 1&gt;|
|&lt;IMEI n.º 2&gt;|&lt;Detalles del dispositivo n.º 2&gt;|

Este archivo .csv, cuando se ve en un editor de texto, aparece como:

```
01234567890123,device details
02234567890123,device details
```


> [!IMPORTANT]
> Algunos dispositivos Android tienen varios números IMEI. Intune inventaría un número IMEI por dispositivo. Si importa un número IMEI pero no es el IMEI inventariado por Intune, el dispositivo se clasificará como un dispositivo personal en lugar de como un dispositivo propiedad de la empresa. Si importa varios números IMEI para un dispositivo, en el estado de inscripción de los números no inventariados se mostrará **Desconocido**.

**Para agregar una lista .csv de identificadores corporativos**

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscripción de dispositivos** > **Restricciones de inscripción**, elija **Identificadores de dispositivo corporativos** y, luego, haga clic en **Agregar**.

3. En la hoja **Agregar identificadores**, especifique el tipo de identificador **IMEI**. Puede especificar la opción **Sobrescribir detalles de identificadores existentes** para los números importados previamente.  

4. Haga clic en el icono de la carpeta y especifique la ruta de acceso de la lista que quiera importar. Vaya al archivo CSV de IMEI y seleccione **Agregar**.

Una vez importados, estos dispositivos pueden o no estar inscritos y su estado es **Inscrito** o **No contactado**. **No contactado** significa que el dispositivo nunca se ha comunicado con el servicio Intune.

## <a name="delete--corporate-identifiers"></a>Eliminación de identificadores corporativos

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscripción de dispositivos** > **Restricciones de inscripción**, elija **Identificadores de dispositivo corporativos** y, luego, elija **Eliminar**.

3. En la hoja **Eliminar identificadores**, localice el archivo .csv con los id. de dispositivo que quiera eliminar y, luego, haga clic en **Eliminar**.

## <a name="imei-specifications"></a>Especificaciones de IMEI
Para obtener especificaciones detalladas sobre identificadores internacionales de equipos móviles, consulte [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

