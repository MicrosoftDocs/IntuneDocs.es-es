---
title: "Adición de identificadores IMEI a Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: aprenda cómo agregar identificadores corporativos (números de IMEI) a Microsoft Intune. "
keywords: 
author: staciebarker
ms.author: stabark
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: e134a6e3ff143dacce1d70ef0ab44ade0722ed57

---

# <a name="add-corporate-identifiers"></a>Adición de identificadores corporativos

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Puede crear una lista de números de identidad de equipo móvil internacional (IMEI) para identificar los dispositivos corporativos. Estos dispositivos pueden o no estar inscritos y tienen un estado de "Inscrito" o "No conectado". "No conectado" significa que el dispositivo nunca se registra con el servicio Intune.

Para crear la lista, cree una lista de dos columnas de valores separados por comas (.csv) sin un encabezado. Agregue el identificador IMEI en la columna izquierda y los detalles en la columna derecha. El número máximo actual de filas de la lista es 500.

En un editor de texto, la lista .csv tiene este aspecto:

01 234567 890123,detalles del dispositivo</br>
02 234567 890123,detalles del dispositivo

**Para agregar una lista .csv de identificadores corporativos**

1. En el portal de Azure, elija **More Services** (Más servicios), escriba **Intune** en el cuadro de texto y luego seleccione **Other** (Otros)  > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Identificadores de dispositivo corporativos**.

3. Si va a importar un archivo con nuevos detalles que sobrescribirán los existentes, seleccione **Sobrescribir detalles de identificadores existentes** para que los nuevos detalles sustituyan a los existentes.

4. Vaya al archivo CSV de IMEI y seleccione **Agregar**.

**Para eliminar una lista .csv de identificadores corporativos**

1. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Identificadores de dispositivo corporativos**.

2. Elija **Eliminar**.



<!--HONumber=Feb17_HO1-->


