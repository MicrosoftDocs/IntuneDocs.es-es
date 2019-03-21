---
title: Creación de un informe desde la fuente de OData con Power BI
titlesuffix: Microsoft Intune
description: Cree una vista de gráfico de rectángulos mediante Power BI Desktop con un filtro interactivo de la API de Almacenamiento de datos de Intune.
keywords: Almacenamiento de datos de Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3cd0f8b5337ad562bddd65bc449a35ec0773f5ed
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565628"
---
# <a name="create-a-report-from-the-odata-feed-with-power-bi"></a>Creación de un informe desde la fuente de OData con Power BI

En este artículo se explica cómo crear una visualización de gráfico de rectángulos mediante Power BI Desktop con un filtro interactivo. Por ejemplo, puede ser que su directora financiera quiera conocer cuál es la distribución global de los dispositivos según si son propiedad de la empresa o personales. El gráfico de rectángulos ofrece información sobre el número total de tipos de dispositivos. Puede revisar el número de dispositivos iOS, Android y Windows que son propiedad de la empresa o de uso personal.

### <a name="overview-of-creating-the-chart"></a>Información general para crear el gráfico

Para crear este gráfico, es necesario:
1. Instalar Power BI Desktop, si aún no lo tiene.
2. Conectar con el modelo de datos de Almacenamiento de datos de Intune y recuperar los datos actuales para el modelo.
3. Crear o administrar las relaciones del modelo de datos.
4. Crear el gráfico con los datos de la tabla **dispositivos**.
5. Crear un filtro interactivo.
6. Ver el diagrama terminado.

### <a name="a-note-about-tables-and-entities"></a>Información sobre tablas y entidades

En Power BI va a trabajar con tablas. Una tabla contiene campos de datos. Cada campo de datos admite un tipo de datos. El campo solo puede contener datos del tipo de datos en cuestión. Los tipos de datos pueden ser números, texto, fechas, etc. Las tablas de Power BI se rellenan con datos recientes del historial del inquilino al cargar el modelo. Aunque los datos específicos cambian con el tiempo, la estructura de la tabla no cambiará a menos que se actualice el modelo de datos subyacente.

El uso de los términos _entidad_ y _tabla_ puede llevar a confusión. Se puede acceder al modelo de datos desde una fuente OData. Los contenedores que se denominan tablas en Power BI se denominan entidades en el universo de OData. Estos términos hacen referencia al mismo lugar que contiene sus datos.

## <a name="install-power-bi-desktop"></a>Instalar Power BI Desktop

Instale la versión más reciente de Power BI Desktop. Puede descargar Power BI Desktop desde [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Conectarse a la fuente OData para el Almacén de datos de Intune para su inquilino

> [!Note]  
> Necesita permiso para acceder a los **Informes** en Intune. Para obtener más información, vea la [Autorización](reports-api-url.md).

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Abra el panel **Almacenamiento de datos de Intune**.
4. Copie la dirección URL de la fuente personalizada. Por ejemplo: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
5. Abra Power BI Desktop.
6. Elija **Obtener datos** > **Fuente OData**.
7. Pegue la dirección URL de la fuente personalizada en el cuadro para la URL de la ventana **Fuente OData**.
8. Seleccione **Básica**.

    ![Fuente OData para el Almacén de datos de Intune para su inquilino](media/reports-create-01-odatafeed.png)

9. Seleccione **Aceptar**.
10. Seleccione **Cuenta de la organización** y después inicie sesión con sus credenciales de Intune.

    ![Credenciales de la cuenta de la organización](media/reports-create-02-org-account.png)

11. Seleccione **Conectar**. Se abrirá el navegador y mostrará la lista de tablas en el Almacén de datos de Intune.

    ![Captura de pantalla del navegador: la lista de tablas de almacenamiento de datos](media/reports-create-02-loadentities.png)

12. Seleccione las tablas **dispositivos** y **ownerTypes**.  Seleccione **Cargar**. Power BI cargará los datos en el modelo.

## <a name="create-a-relationship"></a>Crear una relación

Puede importar varias tablas para analizar no solo los datos en una sola tabla sino los datos relacionados en diferentes tablas.  Power BI tiene una característica denominada **detección automática**, que intenta buscar y crear relaciones automáticamente. Se han creado tablas en el Almacén de datos para trabajar con la característica de detección automática de Power BI. En cambio, aunque Power BI no encuentre automáticamente las relaciones, usted puede administrarlas.

![Administrar las relaciones de los datos relacionados en las tablas](media/reports-create-03-managerelationships.png)

1. Seleccione **Administrar relaciones**.
2. Si Power BI todavía no ha detectado las relaciones, seleccione**Detección automática...**

La relación se muestra en una columna Desde a una columna Hasta. En este ejemplo, el campo de datos **ownerTypeKey** de la tabla **dispositivos** enlaza con el campo de datos **ownerTypeKey** de la tabla **ownerTypes**. La relación le servirá para buscar el nombre simple del código del tipo de dispositivo en la tabla **dispositivos**.

## <a name="create-a-treemap-visualization"></a>Crear una visualización de gráfico de rectángulos

En un gráfico de rectángulos se muestran datos jerárquicos en forma de cuadros dentro de cuadros. Cada rama de la jerarquía es un cuadro que contiene cuadros más pequeños que representan las subramas. Puede usar Power BI Desktop para crear un gráfico de rectángulos de los datos de Intune.

![Visualizaciones de gráfico de rectángulos de Power BI](media/reports-create-03-treemap.png)

1. Seleccione un tipo de gráfico. Seleccione **Gráfico de rectángulos**.
2. En el modelo de datos, busque la tabla **dispositivos**.
3. Expanda la **tabla de dispositivos** y seleccione el campo de datos **fabricante** en el panel **Campos**.
4. Arrastre el campo de datos **fabricante** al gráfico de rectángulos en el lienzo del informe.
5. Arrastre el campo de datos **deviceKey** de la tabla **dispositivos** a la sección **Valores** del panel **Visualizaciones** y suéltelo en el cuadro con la etiqueta **Arrastrar el campo de datos aquí**.  

Ahora dispone de un objeto visual en el que se muestra la distribución de los fabricantes de dispositivos en la organización.

![Gráfico de rectángulos con datos: la distribución de los fabricantes de dispositivos](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Agregar un filtro

Puede agregar un filtro al gráfico de rectángulos para poder responder a preguntas adicionales con la aplicación.


1. Para agregar un filtro, seleccione el lienzo del informe y, después, haga clic en el **icono de segmentación de datos** (![Gráfico de rectángulos con modelo de datos y relaciones admitidas](media/reports-create-slicer.png)) en **Visualizaciones**.
2. Busque la tabla **ownerTypes** y arrastre el campo de datos **ownerTypeName** de la sección **Filtros** en el panel **Visualizaciones**.  

   En la tabla de dispositivos, hay un campo de datos denominado **OwnerTypeKey** que contiene un código que indica si un dispositivo es propiedad de la empresa o personal. Puesto que le interesa que se muestren nombres descriptivos en este filtro, busque la tabla **ownerTypes** y arrastre el **ownerTypeName**. En este ejemplo se muestra cómo el modelo de datos es compatible con las relaciones entre tablas.

![Gráfico de rectángulos con filtro: compatible con las relaciones entre tablas](media/reports-create-08_ownertype.png)

Ahora tiene un filtro interactivo que puede usar para alternar entre dispositivos que son propiedad de la empresa y dispositivos personales. Use este filtro para ver cómo cambia la distribución.

1. Seleccione **Empresa** para ver la distribución de los dispositivos que son propiedad de la empresa.
2. Seleccione **Personal** para ver los dispositivos personales.

## <a name="next-steps"></a>Pasos siguientes

 - Obtenga más información sobre cómo [crear y administrar relaciones](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) en Power BI Desktop en la documentación de Power BI.
 - Abra el [Modelo de Almacenamiento de datos de Intune](https://docs.microsoft.com/intune/reports-ref-data-model).
