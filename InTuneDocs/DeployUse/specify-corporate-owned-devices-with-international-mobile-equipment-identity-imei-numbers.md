---
title: "Especificar números IMEI | Microsoft Intune"
description: "Microsoft Intune permite a los administradores importar números IMEI de plataformas de dispositivos móviles para ayudar a identificar dispositivos móviles corporativos"
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: c6b01a5efc0f60622b95623fd91f192c267ff766
ms.openlocfilehash: 9bd2b4bb676e23712c0a668161b81c4e352bce87


---

# Especificar dispositivos corporativos con números de identidad de equipo móvil internacional (IMEI)
Microsoft Intune permite que los administradores importen números de identidad de equipo móvil internacional (IMEI) de plataformas de dispositivos móviles para ayudar a identificar dispositivos móviles corporativos. Una vez que los dispositivos se han inscrito en Intune, aquellos con números IMEI importados se pueden ver en **Grupos** > **Información general** > **Todos los dispositivos**. **Grupo de dispositivos** muestra los dispositivos con números IMEI importados como **Organización** en la columna **Propiedad**.

1. En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), elija **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos corporativos inscritos previamente** &gt; **Mediante IMEI (todas las plataformas)** y, luego, **Agregar dispositivos...** Puede agregar dispositivos de dos maneras:

    -   **Cargar un archivo .csv con números de serie**: cree una lista de valores separados por comas (.csv) de dos columnas sin encabezado y limítela a 5000 dispositivos o a 5 MB por archivo .csv.

        |||
        |-|-|
        |&lt;IMEI n.º 1&gt;|&lt;Detalles del dispositivo n.º 1&gt;|
        |&lt;IMEI n.º 2&gt;|&lt;Detalles del dispositivo n.º 2&gt;|
        Este archivo .csv, cuando se ve en un editor de texto, aparece como:

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Agregar manualmente los detalles del dispositivo**: especifique el número IMEI y los detalles de cinco dispositivos como máximo.

   La opción *Detalles* es para uso administrativo, para que pueda identificar el número IMEI asociado a un dispositivo. Esta información no se envía al dispositivo, sino que aparece en la consola de Intune.

2.   Seleccione **Siguiente**.
3.  En el panel **Revisar dispositivos**, puede confirmar los números IMEI de dispositivos importados. También puede decidir si sobrescribe los **Detalles** de los números IMEI que se van a volver a importar. Puede desactivar la casilla **Sobrescribir** para conservar los detalles actuales. Seleccione **Finalizar** para importar los números IMEI.
4.  Los números IMEI importados y las descripciones se agregan a la lista **Mediante IMEI (todas las plataformas)**.

Cuando se inscribe un dispositivo con número IMEI en Intune, normalmente cuando un usuario instala la aplicación Portal de empresa y completa el proceso de inscripción, el dispositivo se etiqueta como corporativo y aparece como inscrito en el grupo **Dispositivos IMEI**.



<!--HONumber=Oct16_HO3-->


