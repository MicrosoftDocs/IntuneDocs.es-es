---
title: Conectarse al Almacenamiento de datos con Power BI | Microsoft Docs
description: "Puede descargar un archivo para su uso con Microsoft Power BI que le permite cargar informes interactivos generados de forma dinámica para el inquilino de Intune."
keywords: Almacenamiento de datos de Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b70bf3410e20dd792c0fcff050292ddea714d63e
ms.sourcegitcommit: 99ffed621855357de427d6fdf7b70d4e543197e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2017
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Conectarse al Almacenamiento de datos con Power BI

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Puede descargar un archivo para su uso con Microsoft Power BI que le permite cargar informes interactivos generados de forma dinámica para el inquilino de Intune. El archivo de Almacenamiento de datos de Power BI (pbix) contiene la configuración de conexión del inquilino y los siguientes informes y gráficos de ejemplo:  

  -  Dispositivos
  -  Inscripción
  -  Directiva de protección de aplicaciones
  -  Directiva de cumplimiento
  -  Perfiles de configuración de dispositivos
  -  Actualizaciones de software
  -  Registros de inventario de dispositivos

También se resaltan las tendencias de la inscripción, el cumplimiento, el perfil de configuración de dispositivos y las actualizaciones de software. Los gráficos e informes de ejemplo aplican al lienzo filtros fáciles de usar. Para usar filtros avanzados, vea el panel **Filtro** de Power BI Desktop. 

En los pasos siguientes se muestra cómo descargar el archivo de Power BI y cómo usar el vínculo de OData con Power BI.

## <a name="install-power-bi"></a>Instalar Power BI

Instale la versión más reciente de Power BI Desktop. Puede descargar Power BI Desktop desde [PowerBI.microsoft.com](https://powerbi.microsoft.com/en-us/desktop) 

## <a name="load-the-data-and-reports-using-the-power-bi-file-pbix"></a>Cargar los datos e informes mediante el archivo de Power BI (pbix)

El archivo de Power BI (pbix) contiene información de conexión del inquilino y un conjunto de informes creados previamente basados en el modelo de datos del Almacenamiento de datos. Abra el archivo en Power BI Desktop e inicie sesión en Azure AD. El informe carga los datos del inquilino de Intune.

> [!Important]  
> Cada archivo de Power BI (pbix) pueden variar según la ubicación del inquilino. Si administra varios inquilinos de Intune, asegúrese de usar el archivo descargado desde Azure Portal durante una sesión iniciada en ese inquilino.  

1.  Inicie sesión en Azure Portal y seleccione **Supervisión y administración** > **Intune**. También puede buscar recursos para **Intune**.  
2.  Abra la hoja **Microsoft Intune Data Warehouse API (Preview)** (API de Almacenamiento de datos de Microsoft Intune (versión preliminar)).
3.  Haga clic en **Descargar archivo de Power BI**. El archivo, con extensión (pbix), se descarga en la ubicación especificada.
4.  Abra el archivo con Power BI. Se carga *Intune Data Warehouse Reports* (Informes de Almacenamiento de datos de Intune), pero puede tardar un poco, ya que debe obtener los datos de inquilino.
5.  Haga clic en **Actualizar** para cargar los datos del inquilino y revisar los informes.
6.  Si no se ha autenticado Power BI con las credenciales de Azure Active Directory, Power BI le pedirá que proporcione sus credenciales. Al seleccionar las credenciales, elija **Cuenta de organización** como método de autenticación.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>Cargar los datos en Power BI mediante el vínculo de OData

Con un cliente autenticado en Azure AD, la dirección URL de OData se conecta al punto de conexión de RESTful en la API de Almacenamiento de datos que expone el modelo de datos al cliente de informes. Siga estas instrucciones para usar Power BI Desktop para conectarse y crear sus propios informes. No hace falta que se limite a Power BI Desktop, ya que puede usar la herramienta de análisis que prefiera con la dirección URL de OData, siempre y cuando el cliente admita la autenticación de OAUTH2.0 y el estándar de OData v4.0.

1.  Recupere la **URL de OData** desde la hoja de informes, por ejemplo, `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`.
2.  Abra **Power BI Desktop**.
3.  Seleccione **Inicio** > **Obtener datos**. Seleccione **Fuente OData**.
4.  Elija **Básica**.
5.  Escriba o pegue la **URL de OData** en el cuadro de dirección URL.
6.  Haga clic en **Aceptar**.
7.  Si no se ha autenticado en Azure AD para el inquilino desde el cliente de Power BI Desktop, escriba sus credenciales.  
    a.  Seleccione **Cuenta de organización**.  
    b.  Escriba su nombre de usuario y su contraseña.  
    c.  Haga clic en **Iniciar sesión**.  
    d.  Haga clic en **Conectar**.  
8.  Haga clic en **Cargar**.

## <a name="next-steps"></a>Pasos siguientes

Puede encontrar respuestas a preguntas sobre su entorno, como el número de dispositivos inscritos por día durante la última semana. Puede obtener una visión general de los inquilinos y los clientes de Intune mediante los informes. Para ello, use el archivo de Almacenamiento de datos de Intune de Power BI (pbix), que puede recuperar en la hoja de Azure. Además, Intune proporciona diversas formas adicionales de ampliar o reutilizar los datos. Puede hacer muchas más cosas con Power BI y la API de Almacenamiento de datos de Intune, por ejemplo:

<!-- -  You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
 -  Los datos de inquilino están organizados de una manera que le ayuda a obtener información a partir de los datos. Para obtener más información sobre cómo se organizan los datos, vea [Data Warehouse Data Model](reports-ref-data-model.md) (Modelo de datos de Almacenamiento de datos). 
<!-- -  You can also access the data from a RESTful interface and incorporate the data into your own app. For more information, see [Get data from the Data Warehouse API with a REST client](reports-proc-data-rest.md). -->