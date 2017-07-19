---
title: Agregar identificadores IMEI a Intune
titleSuffix: Intune on Azure
description: "Aprenda a agregar identificadores corporativos (números IMEI) a Microsoft Intune. \""
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 57ab3b79ad53a4b195fac426d211a114f054602f
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="add-corporate-identifiers"></a>Adición de identificadores corporativos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Como administrador de TI, puede crear e importar un archivo de valores separados por comas (.csv) que muestre los números de identidad internacional de equipos móviles (IMEI) o números de serie para identificar los dispositivos de la empresa. Solo puede declarar números de serie para dispositivos iOS y Android. Cada número IMEI o de serie puede tener detalles especificados en la lista para fines administrativos.

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

[Obtenga información sobre cómo buscar el número de serie de un dispositivo de Apple](https://support.apple.com/HT204308).
[Obtenga información sobre cómo buscar el número de serie del dispositivo de Android](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers"></a>Adición de identificadores corporativos
Para crear la lista, cree una lista de dos columnas de valores separados por comas (.csv) sin un encabezado. Agregue el número IMEI o de serie en la columna izquierda y los detalles en la columna derecha. Solo puede importarse un tipo de identificador, número IMEI o de serie en un único archivo .csv. Los detalles están limitados a 128 caracteres y son solo de uso administrativo. Los detalles no se muestran en el dispositivo. El límite actual es 500 filas por archivo. csv.

**Cargar un archivo .csv con números de serie**: cree una lista de valores separados por comas (.csv) de dos columnas sin encabezado y limítela a 5000 dispositivos o a 5 MB por archivo .csv.

|||
|-|-|
|&lt;ID #1&gt;|&lt;Detalles del dispositivo n.º 1&gt;|
|&lt;ID #2&gt;|&lt;Detalles del dispositivo n.º 2&gt;|

Este archivo .csv, cuando se ve en un editor de texto, aparece como:

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> Algunos dispositivos Android tienen varios números IMEI. Intune solo lee un número IMEI por dispositivo inscrito. Si importa un número IMEI pero no es el IMEI inventariado por Intune, el dispositivo se clasificará como un dispositivo personal en lugar de como un dispositivo propiedad de la empresa. Si importa varios números IMEI para un dispositivo, en el estado de inscripción de los números no inventariados se mostrará **Desconocido**.

**Para agregar una lista .csv de identificadores corporativos**

1. En el portal de Intune, elija **Inscripción de dispositivos** > **Restricciones de inscripción**, **Identificadores de dispositivo corporativos** y, luego, haga clic en **Agregar**.

 ![Captura de pantalla del área de trabajo del identificador de dispositivo corporativo con el botón Agregar resaltado.](./media/add-corp-id.png)

2. En la hoja **Agregar identificadores**, especifique el tipo de identificador **IMEI** o **Serie**. Puede especificar la opción **Sobrescribir detalles de identificadores existentes** para los números importados previamente.

3. Haga clic en el icono de la carpeta y especifique la ruta de acceso de la lista que quiera importar. Vaya al archivo .csv y seleccione **Agregar**. Puede hacer clic en **Actualizar** para ver los nuevos identificadores de dispositivo.

Una vez importados, estos dispositivos pueden o no estar inscritos y su estado es **Inscrito** o **No contactado**. **No contactado** significa que el dispositivo nunca se ha comunicado con el servicio Intune.

## <a name="delete--corporate-identifiers"></a>Eliminación de identificadores corporativos

1. En la hoja de Intune, elija **Inscripción de dispositivos** > **Restricciones de inscripción**, **Identificadores de dispositivo corporativos** y, luego, elija **Eliminar**.

3. En la hoja **Eliminar identificadores**, localice el archivo .csv con los id. de dispositivo que quiera eliminar y, luego, haga clic en **Eliminar**.

## <a name="imei-specifications"></a>Especificaciones de IMEI
Para obtener especificaciones detalladas sobre identificadores internacionales de equipos móviles, consulte [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).
