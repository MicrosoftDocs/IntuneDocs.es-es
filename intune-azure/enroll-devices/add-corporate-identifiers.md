---
title: Agregar identificadores IMEI a Intune
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda cómo agregar identificadores corporativos (números de IMEI) a Microsoft Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 0d7c8eedbdad917a43d43d2e79ead5663e8e2871
ms.lasthandoff: 02/18/2017

---

# <a name="add-corporate-identifiers"></a>Adición de identificadores corporativos

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Puede crear una lista de números de identidad de equipo móvil internacional (IMEI) para identificar los dispositivos corporativos. Estos dispositivos pueden o no estar inscritos y tienen un estado de "Inscrito" o "No conectado". "No conectado" significa que el dispositivo nunca se registra con el servicio Intune.

Para crear la lista, cree una lista de dos columnas de valores separados por comas (.csv) sin un encabezado. Agregue el identificador IMEI en la columna izquierda y los detalles en la columna derecha. El número máximo actual de filas de la lista es 500.

En un editor de texto, la lista .csv tiene este aspecto:

01 234567 890123,detalles del dispositivo</br>
02 234567 890123,detalles del dispositivo

**Para agregar una lista .csv de identificadores corporativos**

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Identificadores de dispositivo corporativos**.

3. Si va a importar un archivo con nuevos detalles que sobrescribirán los existentes, seleccione **Sobrescribir detalles de identificadores existentes** para que los nuevos detalles sustituyan a los existentes.

4. Vaya al archivo CSV de IMEI y seleccione **Agregar**.

**Para eliminar una lista .csv de identificadores corporativos**

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Identificadores de dispositivo corporativos**.

3. Elija **Eliminar**.

