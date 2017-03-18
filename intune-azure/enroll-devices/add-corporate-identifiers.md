---
title: Agregar identificadores IMEI a Intune
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda cómo agregar identificadores corporativos (números de IMEI) a Microsoft Intune. "
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: d8cb15d1b8c1c100f15084e43d2c3c4633fd64b5
ms.openlocfilehash: f12d538b1f4cd327b893d234f2b558185cdd9d85
ms.lasthandoff: 03/09/2017

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

> [!IMPORTANT]
> Algunos dispositivos Android tienen varios números IMEI. Intune inventaría un número IMEI por dispositivo. Si importa un número IMEI pero no es el IMEI inventariado por Intune, el dispositivo se clasificará como un dispositivo personal en lugar de como un dispositivo propiedad de la empresa. Si importa varios números IMEI para un dispositivo, en el estado de inscripción de los números no inventariados se mostrará **Desconocido**.

**Para eliminar una lista .csv de identificadores corporativos**

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Identificadores de dispositivo corporativos**.

3. Elija **Eliminar**.

