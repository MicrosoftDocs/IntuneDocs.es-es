---
title: Comprender las operaciones mediante informes
description: "Cree y administre informes sobre el software, el hardware y las licencias de software de la organización."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 04/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 857309c2-61c9-4c22-becf-4839fedeaece
ms.reviewer: pbala
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 51140a1ef2739abbbc7eb7b8fd49b1cee7318362
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2017
---
# <a name="understand-microsoft-intune-operations-by-using-reports"></a>Comprender las operaciones de Microsoft Intune mediante informes

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use la información de este tema como ayuda para crear y administrar informes de Microsoft Intune que proporcionan información sobre el software, el hardware y las licencias de software en la organización.

## <a name="using-reports"></a>Uso de informes
Los informes de Intune proporcionan información sobre el software, el hardware y las licencias de software de la organización. Los informes pueden ayudar a confirmar las necesidades actuales y pronosticar gastos futuros. El área de trabajo **Informes** proporciona las herramientas para crear y administrar los informes. 

## <a name="report-types"></a>Report types (Tipos de informes)

|Tipo de informe|Descripción|
|---------------|---------------|
|**Informes de actualización**|Muestran las actualizaciones de software que se han llevado a cabo correctamente en los equipos de su organización. También muestran las actualizaciones erróneas, pendientes o necesarias. Para más información sobre las actualizaciones de software, vea [Mantener los equipos Windows al día con las actualizaciones de software en Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).|
|**Informes de software detectado**|Muestran el software instalado en los equipos de su organización. También se incluyen las versiones de software. Puede filtrar la información mostrada en función de la compañía de software y la categoría de software. Puede seleccionar la flecha situada junto al elemento de lista para expandir las actualizaciones de la lista a fin de mostrar más detalles (como los equipos en los que hay una actualización instalada).<br /><br />Al retirar equipos o cambiar su pertenencia a grupos en Intune, los cambios pueden tardar varios minutos en quedar reflejados en el informe de software detectado. Para que los datos de inventario de software sean más precisos, espere unos minutos después de retirar equipos o cambiar su pertenencia a grupos antes de ejecutar un informe de software detectado que incluya dichos equipos.|
|**Informes de inventario de equipos**|Muestra información sobre los equipos administrados en su organización. Use este informe para planear las compras de hardware y comprender mejor las necesidades de hardware de los usuarios de la organización. Para más información sobre cómo trabajar con los equipos administrados, vea [Administrar equipos de Windows con Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md).|
|**Informes de inventario de dispositivos móviles**|Muestra información sobre los dispositivos móviles en la organización. Puede filtrar la información mostrada en función de los grupos, si el dispositivo está desbloqueado o es un dispositivo raíz, y según sistema operativo.|
|**Informes de adquisición de licencias**|Muestra los títulos de software para todo el software con licencia de los grupos de licencias seleccionados, basándose en sus contratos de licencia. Si la información de la licencia de software no se ha actualizado en más de 24 horas, se actualizará cuando se genere un informe de licencias. Un informe de licencia no es un cálculo exacto de los títulos de software que se utilizan ni constituye una prueba del cumplimiento de los contratos. El informe es una herramienta que facilita la toma de decisiones sobre las licencias de su organización. Intune podría no detectar algunos productos que pueden tener una licencia por volumen de Microsoft. Los filtros disponibles son:<br /><br />**Todos los contratos** muestra todos los productos de software con licencia administrados por Intune.<br /><br />En **Contratos de licencias por volumen** solo se muestran los productos de software del Centro de servicios de licencias por volumen (VLSC).<br /><br />En **Otros contratos de licencias de software** se muestran productos de software que se administran fuera de VLSC.|
|**Informes de instalación de licencias**|Comparan el software instalado en los equipos de su organización con la cobertura del contrato de licencia actual, de acuerdo con el VLSC. Los filtros incluyen:<br /><br />**Todos los contratos** muestra todos los productos de software con licencia administrados por Intune.<br /><br />**Contratos de licencias por volumen** muestra solo productos de software VLSC.<br /><br />En **Otros contratos de licencias de software** se muestran productos de software que se administran fuera de VLSC.|
|**Informes de términos y condiciones**|Muestran si los usuarios aceptaron los términos y condiciones implementados y qué versión aceptaron. Puede mostrar la aceptación de los términos y condiciones implementados para un máximo de 10 usuarios, o bien el estado de aceptación de unas determinadas condiciones implementadas para estos.|
|**Informes de aplicaciones no compatibles**|Muestra información acerca de los usuarios que tienen aplicaciones instaladas que se encuentran en las listas de las aplicaciones compatibles y no compatibles. Utilice este informe para buscar usuarios y dispositivos que no cumplan las directivas de aplicación de la empresa.|
|**Informes de cumplimiento de certificados**|Muestra los certificados que se han emitido a los usuarios y dispositivos mediante SCEP o PKCS #12 (.PFX). Utilice este informe para buscar certificados que se hayan emitido, hayan expirado o se hayan revocado.|
|**Informes del historial de dispositivos**|Muestra un registro histórico de las acciones de retirada, borrado y eliminación. Use este informe para ver quién inició dichas acciones en los dispositivos en algún momento anterior.|
|**Informes de atestación de estado**|Muestra el estado de los dispositivos móviles.|
|**Informe de hardware de Mac OS X**|Muestra los detalles de hardware de todos los dispositivos Mac OS X inscritos de los grupos que seleccione. Para obtener información sobre el inventario de hardware recopilado de estos dispositivos, consulte [Comprender el funcionamiento de sus dispositivos mediante el inventario en Microsoft Intune](understand-your-devices-with-inventory-in-microsoft-intune.md).|
|**Informe del software de Mac OS X**|Muestra el software instalado en todos los dispositivos Mac OS X de los grupos seleccionados. El informe muestra el nombre del software (como un identificador de paquete), la versión corta o el nombre corto (o descriptivo), la versión y el número de dispositivos con el software instalado.|
|**Informes de Windows Information Protection**|Muestra información acerca de las operaciones de Windows Information Protection (WIP) en dispositivos que administra.|
|**Informes de atestación de estado**|Muestra información notificada por el servicio de atestación de estado de Windows para los dispositivos que administra.|

## <a name="to-create-a-report"></a>Para crear un informe

1.  En la consola de administración de Intune, elija **Informes**. Después, elija el tipo de informe que quiere generar, como se describe en la tabla anterior.

2.  En la página **Crear nuevo informe**, acepte los valores predeterminados o personalícelos para filtrar los resultados devueltos por el informe. Por ejemplo, puede seleccionar que en el informe de software detectado solo se muestre el software publicado por Microsoft.

3.  Elija **Ver informe** para abrir el informe en una nueva ventana.

Para ordenar el informe por cualquiera de las columnas mostradas, elija el encabezado de la columna. Además, algunos informes permiten expandir elementos de la lista para mostrar más detalles.

## <a name="more-report-actions"></a>Más acciones de los informe
Además, los informes admiten las siguientes acciones:

|Acción|Más información|
|----------|--------------------|
|**Imprimir**|En un informe abierto, elija el icono de impresión y siga las instrucciones.|
|**Exportarar**|En un informe abierto, elija el icono de exportación y siga las instrucciones. Puede exportar un informe en formato de valores separados por comas (.csv) o HTML.|
|**Guardar**|En la página **Crear nuevo informe** , cada usuario puede guardar hasta 100 informes. Configure los parámetros del informe según sus requisitos y, después, elija **Guardar**o **Guardar como** (si quiere usar otro nombre).|
|**Cargar**|En la página **Crear nuevo informe**, elija **Cargar** para recuperar cualquier conjunto de parámetros de informe que haya guardado.|
|**Eliminar**|En el área de trabajo **Informes**, seleccione el tipo de informe deseado y elija **Cargar**. Luego, en la lista de informes, elija el icono de eliminación (x), situado junto al informe.|


