---
title: "Especificar números IMEI | Microsoft Intune"
description: "Microsoft Intune permite a los administradores importar números IMEI para plataformas de dispositivos móviles para ayudar a identificar los dispositivos móviles corporativos"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: 4e2092182dbda4523c19afeabc34aa0166962c40


---

# Especificar dispositivos corporativos con números de identidad de equipo móvil internacional (IMEI)
Microsoft Intune permite que los administradores importen números de identidad de equipo móvil internacional (IMEI) para plataformas de dispositivos móviles con números IMEI para ayudar a identificar los dispositivos móviles corporativos. Una vez inscritos en Intune, los dispositivos con números IMEI importados se pueden ver en **Grupos** > **Información general** > **Todos los dispositivos**. Las listas **Grupo de dispositivos** muestran los dispositivos con los números IMEI importados como **Corporativo** en la columna **Propiedad**.

1. En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), seleccione **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos corporativos inscritos previamente** &gt; **Mediante IMEI (todas las plataformas)** y luego **Agregar dispositivos...**. Puede agregar dispositivos de dos maneras:

    -   **Cargar un archivo CSV que contiene números de serie**: cree una lista de valores separados por comas (.csv) con dos columnas sin encabezado, limitada a 5000 dispositivos o 5 MB por archivo .csv.

        |||
        |-|-|
        |&lt;IMEI n.º 1&gt;|&lt;Detalles del dispositivo n.º 1&gt;|
        |&lt;IMEI n.º 2&gt;|&lt;Detalles del dispositivo n.º 2&gt;|
        Este archivo .csv, cuando se ve en un editor de texto, aparece como:

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Agregar manualmente los detalles del dispositivo**: especifique el número de serie y los detalles de cinco dispositivos como máximo.

   Los *detalles* son para uso administrativo para que pueda identificar qué número IMEI está asociado a un dispositivo. Esta información no se envía al dispositivo, pero aparecerá en la consola de Intune.

2.   Seleccione **Siguiente**.
3.  En el panel **Revisar dispositivos**, puede confirmar que números IMEI de dispositivos se importan. También puede decidir si quiere sobrescribir los **detalles** para volver a importar los números IMEI. Puede desactivar la casilla **Sobrescribir** para conservar los detalles actuales. Seleccione **Finalizar** para importar los números IMEI.
4.  Los números IMEI agregados y las descripciones se agregan a la lista **Mediante IMEI (todas las plataformas)**.

Cuando se inscribe el dispositivo con ese número IMEI, normalmente cuando un usuario instala la aplicación Portal de empresa y completa el proceso de inscripción, el dispositivo se etiqueta como Propiedad corporativa y aparece como inscrito en el grupo **Dispositivos IMEI**.



<!--HONumber=Jul16_HO4-->


