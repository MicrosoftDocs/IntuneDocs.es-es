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
ms.sourcegitcommit: 4ebd74c77145464574a1fed878ec4dbc2eb3c271
ms.openlocfilehash: 7bb8168c442a3340e8c185f1908acd9be15cab05
ms.lasthandoff: 04/05/2017

---

# <a name="add-corporate-identifiers"></a>Adición de identificadores corporativos

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Como administrador de TI, puede crear e importar un archivo de valores separados por comas (.csv) que incluye los números de identidad internacional de equipos móviles (IMEI) para identificar los dispositivos de la empresa. Cada número IMEI puede tener detalles especificados en la lista para fines administrativos.

Al cargar los números de serie para dispositivos iOS que pertenecen a la empresa, deben estar emparejados con un perfil de inscripción corporativa. Los dispositivos deben inscribirse posteriormente mediante el Programa de inscripción de dispositivos (DEP) de Apple o Apple Configurator para que aparezcan como dispositivos que pertenecen a la empresa. 

## <a name="create-a-csv-file"></a>Creación de un archivo .csv
Para crear la lista, cree una lista de dos columnas de valores separados por comas (.csv) sin un encabezado. Agregue el identificador IMEI en la columna izquierda y los detalles en la columna derecha. Los detalles se limitan a 128 caracteres. El límite actual es 500 filas por archivo. csv.

**Cargar un archivo .csv con números de serie**: cree una lista de valores separados por comas (.csv) de dos columnas sin encabezado y limítela a 5000 dispositivos o a 5 MB por archivo .csv.

|||
|-|-|
|&lt;IMEI n.º 1&gt;|&lt;Detalles del dispositivo n.º 1&gt;|
|&lt;IMEI n.º 2&gt;|&lt;Detalles del dispositivo n.º 2&gt;|

    This .csv file when viewed in a text editor appears as:

    ```
    01 234567 890123,device details
    02 234567 890123,device details
    ```

**Para agregar una lista .csv de identificadores corporativos**

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Identificadores de dispositivo corporativos**.

3. Si va a importar un archivo con nuevos detalles que sobrescribirán los existentes, seleccione **Sobrescribir detalles de identificadores existentes** para que los nuevos detalles sustituyan a los existentes.

4. Vaya al archivo CSV de IMEI y seleccione **Agregar**.

> [!IMPORTANT]
> Algunos dispositivos Android tienen varios números IMEI. Intune inventaría un número IMEI por dispositivo. Si importa un número IMEI pero no es el IMEI inventariado por Intune, el dispositivo se clasificará como un dispositivo personal en lugar de como un dispositivo propiedad de la empresa. Si importa varios números IMEI para un dispositivo, en el estado de inscripción de los números no inventariados se mostrará **Desconocido**.

Una vez importados, estos dispositivos pueden o no estar inscritos y su estado es **Inscrito** o **No contactado**. **No contactado** significa que el dispositivo nunca se ha comunicado con el servicio Intune.

## <a name="delete-a-csv-list"></a>Eliminación de una lista de .csv

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Identificadores de dispositivo corporativos**.

3. Elija **Eliminar**.

Para obtener especificaciones detalladas sobre identificadores internacionales de equipos móviles, consulte [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

