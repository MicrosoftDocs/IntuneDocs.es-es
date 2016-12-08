---
title: Ver el inventario de software y hardware para PC de Windows | Microsoft Intune
description: "Cómo ver información de hardware y software sobre PC de Windows que se administran con Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 807599d4a6a979c88732ab969fdecb64552a83d5


---

# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Vea el inventario de software y hardware para equipos Windows

Intune recopila información detallada sobre el hardware y el software de los equipos administrados. Use la información de los siguientes procedimientos para aprender a crear:

-   Un informe que muestra información acerca de las capacidades de hardware de los equipos que administra.

-   Un informe que muestra la lista de software instalado en cada equipo.

-   Cómo actualizar un inventario de equipos para asegurarse de que los datos del informe estén al día.

## <a name="to-display-information-about-computers-you-manage"></a>Para mostrar información acerca de los equipos que administra

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Informes** &gt; **Informes de inventario de equipos**.

2.  En la página **Crear nuevo informe** , acepte los valores predeterminados o personalícelos para filtrar los resultados devueltos por el informe. Por ejemplo, puede seleccionar que en el informe sólo se muestren los equipos que ejecutan Windows 8.1.

3.  Elija **Ver informe** para abrir el **Informe de inventario de equipos** en otra ventana.

    Para ordenar el informe por cualquiera de las columnas, seleccione el encabezado de columna correspondiente, como **Nombre**, **Tipo de chasis** o **Fabricante**.

## <a name="to-display-software-installed-on-computers-you-manage"></a>Para mostrar el software instalado en equipos que administra

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Informes** &gt; **Informes de software detectado**.

2.  En la página **Crear nuevo informe** , acepte los valores predeterminados o personalícelos para filtrar los resultados devueltos por el informe. Por ejemplo, puede seleccionar que en el informe sólo se muestre el software publicado por Microsoft.

3.  Elija **Ver informe** para abrir el **Informe de software detectado** en otra ventana.

    Para ordenar el informe por cualquiera de las columnas, seleccione el encabezado de columna correspondiente, como **Nombre**, **Editor** o **Categoría**. Puede seleccionar la flecha situada junto al elemento de lista para expandir las actualizaciones de la lista a fin de mostrar más detalles (como los equipos en los que están instaladas).

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>Para actualizar el inventario de equipos a fin de asegurarse de que está al día

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos ** (u otro grupo que contenga el equipo para el que quiera actualizar el inventario).

2.  Seleccione un equipo o mantenga presionada la tecla **Ctrl** para seleccionar varios equipos.

3.  En la barra de tareas, seleccione **Tareas remotas** &gt; **Actualizar inventario**.

4.  Para ver el estado de la tarea, seleccione **Tareas remotas** en la esquina inferior derecha de la página.

    Se abre el cuadro de diálogo **Estado de la tarea** , que muestra las tareas remotas actuales, el estado de la tarea, el nombre del dispositivo y los errores notificados, y proporciona un vínculo a información de solución de problemas, si es necesario.

### <a name="see-also"></a>Consulte también

[Tareas comunes de administración de equipos Windows con el cliente de software de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->


