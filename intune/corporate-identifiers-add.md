---
title: Agregar identificadores corporativos a Intune
titlesuffix: Microsoft Intune
description: Aprenda a agregar identificadores corporativos (método de inscripción, números IMEI y de serie) a Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cc65cc3440d260adc3bd2c7de3a311374681327d
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183458"
---
# <a name="identify-devices-as-corporate-owned"></a>Identificar dispositivos como corporativos

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Como administrador de Intune, puede identificar dispositivos como propiedad de la empresa para restringir la identificación y administración. Intune puede realizar tareas de administración adicionales y recopilar información adicional, como el número de teléfono completo y un inventario de las aplicaciones de dispositivos propiedad de la empresa. También puede establecer restricciones de dispositivos para bloquear la inscripción de dispositivos que no sean propiedad de la empresa.

A la hora de efectuar la inscripción, Intune asigna de forma automática estados de propiedad de la empresa a los dispositivos que cumplan los siguientes criterios:

- Se ha inscrito con una cuenta de [administrador de inscripción de dispositivos](device-enrollment-manager-enroll.md) (todas las plataformas).
- Se ha inscrito mediante el [Programa de inscripción de dispositivos](device-enrollment-program-enroll-ios.md) de Apple, [Apple School Manager](apple-school-manager-set-up-ios.md) o [Apple Configurator](apple-configurator-enroll-ios.md) (solo iOS).
- [Se ha identificado como corporativo antes de la inscripción](#identify-corporate-owned-devices-with-imei-or-serial-number) mediante un número de identidad internacional de dispositivos móviles IMEI (todas las plataformas con números IMEI) o un número de serie (iOS y Android).
- Unido a Azure Active Directory como un dispositivo Windows 10 Enterprise
- Se ha establecido como corporativo en la [lista de propiedades del dispositivo](#change-device-ownership).

Una vez realizada la inscripción, [podrá cambiar la opción de propiedad](#change-device-ownership) entre **Personal** y **Corporativo**.

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>Identificar dispositivos corporativos con número de serie IMEI

Los administradores de Intune pueden crear e importar un archivo de valores separados por comas (.csv) que muestre los números IMEI o de serie. Intune usa estos identificadores para especificar que la propiedad de los dispositivos es corporativa durante la inscripción del dispositivo. Los números IMEI se pueden declarar para todas las plataformas compatibles. Solo puede declarar números de serie para dispositivos iOS, macOS y Android. Cada número IMEI o de serie puede tener detalles especificados en la lista para fines administrativos.

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

[Obtenga información sobre cómo buscar el número de serie de un dispositivo de Apple](https://support.apple.com/HT204308).<br>
[Obtenga información sobre cómo buscar el número de serie del dispositivo de Android](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>Agregar identificadores corporativos usando un archivo .csv
Para crear la lista, cree una lista de dos columnas de valores separados por comas (.csv) sin un encabezado. Agregue el número IMEI o de serie en la columna izquierda y los detalles en la columna derecha. Solo puede importarse un tipo de identificador, número IMEI o de serie en un único archivo .csv. Los detalles están limitados a 128 caracteres y son solo de uso administrativo. Los detalles no se muestran en el dispositivo. El límite actual es 5000 filas por archivo. csv.

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
> Algunos dispositivos Android tienen varios números IMEI. Intune solo lee un número IMEI por dispositivo inscrito. Si importa un número IMEI, pero no es el que ha inventariado Intune, el dispositivo se clasificará como dispositivo personal en lugar de como dispositivo propiedad de la empresa. Si importa varios números IMEI de un dispositivo, en el estado de inscripción de los números no inventariados se mostrará **Desconocido**.<br>
>Tenga en cuenta también que no se garantiza que los números de serie de Android sean únicos o estén presentes. Póngase en contacto con el proveedor del dispositivo para saber si el número de serie es un identificador de dispositivo de confianza.
>Los números de serie que el dispositivo notifica a Intune podrían no coincidir con el identificador que aparece en los menús del dispositivo Configuración de Android/Acerca de. Compruebe el tipo de número de serie que ha notificado el fabricante del dispositivo.
>Al intentar cargar un archivo con números de serie que contengan puntos (.), se producirán errores de carga. Los números de serie con puntos no se admiten.

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>Actualizar una lista en formato .csv de identificadores corporativos

1. En [Azure Portal, en Intune](https://portal.azure.com), elija **Inscripción de dispositivos** > **Identificadores de dispositivo corporativos** > **Agregar** > **Cargar un archivo CSV**.

   ![Área de trabajo del identificador de dispositivo corporativo con el botón Agregar resaltado](./media/add-corp-id.png)

2. En la hoja **Agregar identificadores**, especifique el tipo de identificador **IMEI** o **Serie**.

3. Haga clic en el icono de la carpeta y especifique la ruta de acceso de la lista que quiera importar. Vaya al archivo .csv y elija **Agregar**. 

4. Si el archivo .csv contiene identificadores corporativos que ya están en Intune, pero con detalles distintos, aparece el menú emergente **Revisar los identificadores duplicados**. Seleccione los identificadores que quiera sobrescribir en Intune y elija **Aceptar** para agregarlos. En cada identificador solo se comparará el primer duplicado.

## <a name="manually-enter-corporate-identifiers"></a>Especificar identificadores corporativos manualmente

1. En [Azure Portal, en Intune](https://portal.azure.com), elija **Inscripción de dispositivos** > **Identificadores de dispositivo corporativos** > **Agregar** > **Escribir manualmente**.

2. En la hoja **Agregar identificadores**, especifique el tipo de identificador **IMEI** o **Serie**.

3. Escriba el **identificador** y los **detalles** de cada identificador que quiera agregar. Cuando haya terminado de especificar los identificadores, elija **Agregar**.

5. Si ha especificado identificadores corporativos que ya están en Intune, pero con detalles distintos, aparece el menú emergente **Revisar los identificadores duplicados**. Seleccione los identificadores que quiera sobrescribir en Intune y elija **Aceptar** para agregarlos. En cada identificador solo se comparará el primer duplicado.

Puede hacer clic en **Actualizar** para ver los nuevos identificadores de dispositivo.

Los dispositivos importados no tienen por qué inscribirse. Además, pueden tener un estado **Inscrito** o **Sin contacto**. **No contactado** significa que el dispositivo nunca se ha comunicado con el servicio Intune.

## <a name="delete-corporate-identifiers"></a>Eliminación de identificadores corporativos

1. En [Azure Portal, en Intune](https://portal.azure.com), elija **Inscripción de dispositivos** > **Identificadores de dispositivo corporativos**.
2. Seleccione los identificadores de dispositivo que quiera eliminar y elija **Eliminar**.
3. Confirme la eliminación.

Eliminar un identificador corporativo de un dispositivo inscrito no modifica su propiedad. Para modificar la propiedad de un dispositivo, vaya a **Dispositivos**, seleccione el dispositivo, elija **Propiedades** y cambie **Propiedad del dispositivo**.

## <a name="imei-specifications"></a>Especificaciones de IMEI
Para obtener especificaciones detalladas sobre identificadores internacionales de equipos móviles, consulte [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

## <a name="change-device-ownership"></a>Cambiar la propiedad del dispositivo

Las propiedades del dispositivo muestran **Propiedad** en los registros de Intune para cada dispositivo. Como administrador, puede especificar un dispositivo como **Personal** o **Corporativo**.

**Para cambiar la propiedad del dispositivo:**
1. En [Azure Portal, en Intune](https://portal.azure.com), vaya a **Dispositivos** y elija el dispositivo.
2. Seleccione **Propiedades**.
3. Establezca **Propiedad del dispositivo** como **Personal** o **Corporativo**.

   ![Propiedades del dispositivo con las opciones Categoría de dispositivo y Propiedad del dispositivo](./media/device-properties.png)
