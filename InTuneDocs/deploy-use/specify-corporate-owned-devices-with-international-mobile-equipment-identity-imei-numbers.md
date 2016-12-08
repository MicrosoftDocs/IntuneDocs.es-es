---
title: "Especificar números IMEI | Microsoft Intune"
description: "Microsoft Intune permite a los administradores importar números IMEI de plataformas de dispositivos móviles para ayudar a identificar dispositivos móviles corporativos"
keywords: 
author: staciebarker
ms.author: stabar
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
ms.sourcegitcommit: 656c93771776fd317f2b8d91bc59125fba1eb0b9
ms.openlocfilehash: 8b19cb740ed34b479fa8c4f5e2c1d13f13cda1f4


---

# <a name="specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers"></a>Especificar dispositivos corporativos con números de identidad de equipo móvil internacional (IMEI)
Microsoft Intune permite que los administradores importen números de identidad de equipo móvil internacional (IMEI) de plataformas de dispositivos móviles para ayudar a identificar dispositivos móviles corporativos. Una vez que los dispositivos se han inscrito en Intune, aquellos con números IMEI importados se pueden ver en **Grupos** > **Información general** > **Todos los dispositivos**. **Grupo de dispositivos** muestra los dispositivos con números IMEI importados como **Organización** en la columna **Propiedad**.

1. En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), elija **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos corporativos inscritos previamente** &gt; **Mediante IMEI (todas las plataformas)** y, luego, **Agregar dispositivos...** Puede agregar dispositivos de dos maneras:

    -   **Cargar un archivo .csv con números de serie**: cree una lista de valores separados por comas (.csv) de dos columnas sin encabezado y limítela a 5000 dispositivos o a 5 MB por archivo .csv.

        |||
        |-|-|
        |&lt;IMEI n.º 1&gt;|&lt;Detalles del dispositivo n.º 1&gt;|
        |&lt;IMEI n.º 2&gt;|&lt;Detalles del dispositivo n.º 2&gt;|
        Este archivo .csv, cuando se ve en un editor de texto, aparece como:

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Agregar manualmente los detalles del dispositivo**: especifique el número IMEI y los detalles de 15 dispositivos como máximo.

   El campo *Detalles* es para uso administrativo. Puede especificar detalles que ayuden a identificar el dispositivo en la lista de dispositivos corporativos, ordenados por identificador de hardware. Esta información no se envía al dispositivo, sino que aparece en la consola de Intune.

2.   Seleccione **Siguiente**.
3.  En el panel **Revisar dispositivos**, puede confirmar los números IMEI de dispositivos importados. También puede decidir si sobrescribe los **Detalles** de los números IMEI que se van a volver a importar. Puede desactivar la casilla **Sobrescribir** para conservar los detalles actuales. Seleccione **Finalizar** para importar los números IMEI.
4.  Los números IMEI importados y las descripciones se agregan a la lista **Mediante IMEI (todas las plataformas)**.

Cuando se inscribe un dispositivo con número IMEI en Intune, normalmente cuando un usuario instala la aplicación Portal de empresa y completa el proceso de inscripción, el dispositivo se etiqueta como corporativo y aparece como inscrito en el grupo **Dispositivos IMEI**.



<!--HONumber=Nov16_HO3-->


