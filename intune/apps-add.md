---
title: "Cómo agregar aplicaciones a Microsoft Intune"
titleSuffix: Intune on Azure
description: "Estos procedimientos le ayudarán a tener sus aplicaciones en Intune listas para ser asignadas a usuarios y dispositivos. \""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6a4dfa9e0066a2ac6f410aa9f8e4d77a40484ea5
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>Agregar una aplicación a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Antes de poder administrar y asignar aplicaciones a los usuarios, debe agregarlos a Intune. Intune admite una gran variedad de distintos tipos de aplicaciones y las opciones podrían ser diferentes para cada tipo.

Intune permite agregar y asignar estos tipos de aplicación:

![Tipos de aplicaciones compatibles con Intune](./media/app-types.png)

Se admiten las siguientes plataformas.

- Aplicaciones de Google Play Store
- Aplicaciones de línea de negocio (LOB) Android
- Aplicaciones de App Store
- Aplicaciones de línea de negocio (LOB) iOS
- Aplicaciones web
- Aplicaciones de la Tienda Windows Phone 8.1
- Aplicaciones de línea de negocio de Windows Phone (archivos .xap)
- Aplicaciones de la Tienda Windows
- Aplicaciones de línea de negocio de Windows (solo archivos .msi)

>[!TIP]
> Una aplicación de línea de negocio (LOB) no se instala desde una tienda de aplicaciones, sino desde el archivo de instalación de la aplicación. Por ejemplo, para instalar una aplicación de línea de negocio de iOS, agregará el archivo de aplicación (con la extensión .ipa). Estas suelen ser aplicaciones que se han escrito internamente.

## <a name="before-you-start"></a>Antes de empezar

Considere los puntos siguientes antes de empezar a agregar y asignar aplicaciones.

- Al agregar y asignar una aplicación desde un almacén, los usuarios finales deben tener una cuenta con el almacén para poder instalar la aplicación.
- Algunas aplicaciones o elementos que asigna pueden depender de aplicaciones iOS integradas. Por ejemplo, si asigna un libro desde la tienda iOS, la aplicación iBooks debe existir en el dispositivo. Si quitó la aplicación integrada iBooks, no puede usar Intune para restablecerla.

## <a name="cloud-storage-space"></a>Espacio de almacenamiento en nube
Todas las aplicaciones que cree mediante el tipo de instalación del instalador de software (por ejemplo, una aplicación de línea de negocio) se empaquetan y cargan en el almacenamiento en la nube de Intune. Una suscripción de prueba de Intune incluye 2 gigabytes (GB) de almacenamiento en nube que sirve para almacenar actualizaciones y aplicaciones administradas. Una suscripción completa incluye 20 GB de espacio de almacenamiento.

Puede adquirir almacenamiento adicional para Intune mediante el método de compra original.  Si el importe se le ha facturado o lo ha abonado con tarjeta de crédito, visite el [portal de administración de suscripciones](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  De lo contrario, póngase en contacto con su asociado o agente de ventas.

Los requisitos de espacio de almacenamiento en nube son los siguientes:

-   Todos los archivos de instalación deben encontrarse en la misma carpeta.
-   El tamaño máximo de archivo de cualquier archivo que se cargue es de 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Creación y edición de categorías de aplicaciones

Se pueden usar categorías de aplicaciones para ordenar las aplicaciones de forma que sea más fácil para los usuarios encontrarlas en el portal de empresa. Puede asignar una o varias categorías a una aplicación, por ejemplo, **Desarrollador de aplicaciones** o **Communication apps** (Aplicaciones de comunicación).
Al agregar una aplicación a Intune, tiene la opción de seleccionar la categoría que quiera. Use los temas específicos de la plataforma para agregar una aplicación y asignar categorías. Para crear y editar sus propias categorías, use el procedimiento siguiente:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Mobile apps**.
4. En la carga de trabajo **Mobile Apps**, elija **Configuración** > **Categorías de aplicaciones**.
5. En la hoja **Categorías de aplicaciones**, se muestra una lista de las categorías actuales. Elija una de las acciones siguientes:
    - **Crear una categoría**: en la hoja **Crear categoría**, escriba un nombre para la nueva categoría. Los nombres solo pueden escribirse en un solo idioma, Intune no los traduce. Haga clic en **Crear** cuando acabe.
    - **Editar una categoría**: para cualquier categoría de la lista, elija '**...**'. En la hoja **Propiedades**, puede escribir un nuevo nombre para la categoría o eliminarla.


## <a name="apps-added-automatically-by-intune"></a>Aplicaciones que Intune agrega automáticamente

Las aplicaciones siguientes, publicadas por Microsoft, están integradas en Intune y, además, están listas para que asigne lo siguiente:

|||
|-|-|
|Nombre|Plataforma|Tipo de aplicación|
|Azure Information Protection|Android|Aplicación administrada de la tienda Android|
|Dynamics CRM para teléfonos|Android|Aplicación administrada de la tienda Android|
|Dynamics CRM para tabletas|Android|Aplicación administrada de la tienda Android|
|Excel|iOS|Aplicación administrada de la tienda iOS|
|Excel|Android|Aplicación administrada de la tienda Android|
|Explorador administrado|Android|Aplicación administrada de la tienda Android|
|Explorador administrado|iOS|Aplicación administrada de la tienda iOS|
|Microsoft Dynamics CRM en teléfonos|iOS|Aplicación administrada de la tienda iOS|
|Microsoft Dynamics CRM en tabletas|iOS|Aplicación administrada de la tienda iOS|
|Microsoft Power BI|iOS|Aplicación administrada de la tienda iOS|
|Microsoft Power BI|Android|Aplicación administrada de la tienda Android|
|Microsoft SharePoint|iOS|Aplicación administrada de la tienda iOS|
|Microsoft SharePoint|Android|Aplicación administrada de la tienda Android|
|Microsoft Teams|Android|Aplicación administrada de la tienda Android|
|Microsoft Teams|iOS|Aplicación administrada de la tienda iOS|
|OneDrive|iOS|Aplicación administrada de la tienda iOS|
|OneDrive|Android|Aplicación administrada de la tienda Android|
|OneNote|iOS|Aplicación administrada de la tienda iOS|
|Outlook|Android|Aplicación administrada de la tienda Android|
|Outlook|iOS|Aplicación administrada de la tienda iOS|
|Grupos de Outlook|Android|Aplicación administrada de la tienda Android|
|Grupos de Outlook|iOS|Aplicación administrada de la tienda iOS|
|PowerPoint|iOS|Aplicación de App Store administrada|

## <a name="next-steps"></a>Pasos siguientes

Elija uno de los siguientes temas para obtener información sobre cómo agregar aplicaciones ara cada plataforma a Intune:

- [Aplicaciones de Google Play Store](store-apps-android.md)
- [Aplicaciones LOB para Android](lob-apps-android.md)
- [Aplicaciones de la Tienda iOS](store-apps-ios.md)
- [Aplicaciones LOB para iOS](lob-apps-ios.md)
- [Aplicaciones web (para todas las plataformas)](web-app.md)
- [Aplicaciones de la Tienda de Windows Phone 8.1](store-apps-windows-phone-8-1.md)
- [Aplicaciones de línea de negocio de Windows Phone](lob-apps-windows-phone.md)
- [Aplicaciones de la Tienda Windows](store-apps-windows.md)
- [Aplicación de línea de negocio de Windows](lob-apps-windows.md)

