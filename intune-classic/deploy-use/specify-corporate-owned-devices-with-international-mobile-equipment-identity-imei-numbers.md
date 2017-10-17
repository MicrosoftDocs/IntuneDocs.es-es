---
title: "Especificación de los números IMEI"
description: "Microsoft Intune permite a los administradores importar números IMEI de plataformas de dispositivos móviles para ayudar a identificar dispositivos móviles corporativos"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9038670a4c0b4bf52868ba739336dd35366eed2f
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers"></a>Especificar dispositivos corporativos con números de identidad de equipo móvil internacional (IMEI)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune permite que los administradores importen números de identidad de equipo móvil internacional (IMEI) de plataformas de dispositivos móviles para ayudar a identificar dispositivos móviles corporativos. Una vez que los dispositivos se han inscrito en Intune, aquellos con números IMEI importados se pueden ver en **Grupos** > **Información general** > **Todos los dispositivos**. **Grupo de dispositivos** muestra los dispositivos con números IMEI importados como **Organización** en la columna **Propiedad**.

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos corporativos inscritos previamente** &gt; **Mediante IMEI (todas las plataformas)** y, luego, **Agregar dispositivos...** Puede agregar dispositivos de dos maneras:

    -   **Cargar un archivo .csv con números de serie**: cree una lista de valores separados por comas (.csv) de dos columnas sin encabezado y limítela a 5000 dispositivos o a 5 MB por archivo .csv. El campo de detalles tiene un límite de 128 caracteres. 

        |||
        |-|-|
        |&lt;IMEI n.º 1&gt;|&lt;Detalles del dispositivo n.º 1&gt;|
        |&lt;IMEI n.º 2&gt;|&lt;Detalles del dispositivo n.º 2&gt;|
        Este archivo .csv, cuando se ve en un editor de texto, aparece como:

        ```
        01234567890123,device details
        02234567890123,device details
        ```

    -   **Agregar manualmente los detalles del dispositivo**: especifique el número IMEI y los detalles de 15 dispositivos como máximo.

   El campo *Detalles* es para uso administrativo. Puede especificar detalles que ayuden a identificar el dispositivo en la lista de dispositivos corporativos, ordenados por identificador de hardware. Esta información no se envía al dispositivo, sino que aparece en la consola de Intune.

2.   Seleccione **Siguiente**.
3.  En el panel **Revisar dispositivos**, puede confirmar los números IMEI de dispositivos importados. También puede decidir si sobrescribe los **Detalles** de los números IMEI que se van a volver a importar. Puede desactivar la casilla **Sobrescribir** para conservar los detalles actuales. Seleccione **Finalizar** para importar los números IMEI.
4.  Los números IMEI importados y las descripciones se agregan a la lista **Mediante IMEI (todas las plataformas)**.

> [!IMPORTANT]
> Si va a importar los números IMEI para dispositivos Android, tenga en cuenta que algunos dispositivos Android pueden tener varios números IMEI. Si importa un número IMEI pero no es el IMEI notificado por el dispositivo a Intune, el dispositivo se clasificará como un dispositivo personal en lugar de como un dispositivo propiedad de la empresa.

Cuando se inscribe un dispositivo con número IMEI en Intune, normalmente cuando un usuario instala la aplicación Portal de empresa y completa el proceso de inscripción, el dispositivo se etiqueta como corporativo y aparece como inscrito en el grupo **Dispositivos IMEI**.

>[!NOTE]
> Cuando su organización se migre al nuevo Azure Portal en un futuro próximo, verá un cambio en esta característica. En la consola de administrador de Intune existente, los administradores pueden aceptar detalles asociados desde un archivo CSV cargado y sobrescribir los detalles existentes de identificadores de hardware individuales. En el nuevo Azure Portal, podrá sobrescribir de forma automática los detalles de todos los identificadores de hardware o ignorar todos los nuevos detalles de los identificadores existentes.

Para obtener especificaciones detalladas sobre identificadores internacionales de equipos móviles, consulte [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).
