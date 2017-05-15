---
title: "Incorporación de aplicaciones a Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune en Azure: estos procedimientos le ayudan a tener las aplicaciones en Intune preparadas para poder asignarlas a usuarios y dispositivos. "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 92fb84726846c1eb0fb44db1961a225922e9d9aa
ms.contentlocale: es-es
ms.lasthandoff: 04/24/2017

---

# <a name="how-to-add-an-app-to-microsoft-intune"></a>Incorporación de una aplicación a Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Para poder administrar y asignar aplicaciones a los usuarios, debe agregarlas a Intune. Intune admite una amplia gama de tipos de aplicación diferentes y las opciones pueden ser diferentes para cada tipo.

Intune le permite agregar y asignar los siguientes tipos de aplicación:

![Tipos de aplicación compatibles con Intune](./media/app-types.png)

Se admiten las siguientes plataformas.

- Aplicaciones de Google Play Store
- Aplicaciones de línea de negocio (LOB) Android
- Aplicaciones de App Store
- Aplicaciones de línea de negocio (LOB) iOS
- Aplicaciones web
- Aplicaciones de la Tienda Windows Phone 8.1
- Aplicaciones de la Tienda Windows

>[!TIP]
> Una aplicación de línea de negocio (LOB) no se instala desde una tienda de aplicaciones, sino desde el archivo de instalación de la aplicación. Por ejemplo, para instalar una aplicación de línea de negocio de iOS, agregará el archivo de aplicación (con la extensión .ipa). Estas suelen ser aplicaciones que se han escrito internamente.

## <a name="before-you-start"></a>Antes de empezar

Tenga en cuenta lo siguiente antes de empezar a agregar y asignar aplicaciones.

- Al agregar e implementar una aplicación desde una tienda, los usuarios finales deben tener una cuenta con dicha tienda para poder instalar la mencionada aplicación.
- Algunas aplicaciones o elementos que implementa puede depender de aplicaciones de iOS integradas. Por ejemplo, si implementa un libro desde App Store, la aplicación de iBooks debe estar presente en el dispositivo. Si ha quitado la aplicación integrada de iBooks, no puede usar Intune para restablecerla.

## <a name="cloud-storage-space"></a>Espacio de almacenamiento en nube
Todas las aplicaciones que cree mediante el tipo de instalación del instalador de software (por ejemplo, una aplicación de línea de negocio) se empaquetan y cargan en el almacenamiento en la nube de Intune. Una suscripción de prueba de Intune incluye 2 gigabytes (GB) de almacenamiento en nube que sirve para almacenar actualizaciones y aplicaciones administradas. Una suscripción completa incluye 20 GB de espacio de almacenamiento.

Puede adquirir almacenamiento adicional para Intune mediante el método de compra original.  Si pagó con factura o tarjeta de crédito, visite el [portal de administración de suscripciones](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  De lo contrario, póngase en contacto con su asociado o socio de ventas.

Estos son los requisitos de espacio de almacenamiento en la nube:

-   Todos los archivos de instalación de la aplicación deben estar en la misma carpeta.
-   El tamaño máximo de archivo para cualquier archivo que cargue es de 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Creación y edición de categorías para las aplicaciones

Las categorías de aplicación se pueden utilizar para ayudarle a ordenar las aplicaciones para facilitar a los usuarios finales la búsqueda en el portal de empresa. Puede asignar una o varias categorías a una aplicación, por ejemplo, **Aplicaciones de desarrollador** o **Aplicaciones de comunicación**.
Al agregar una aplicación a Intune, tiene la opción de seleccionar la categoría que desee. Utilice los temas específicos de la plataforma para agregar una aplicación y asignar categorías. Para crear y editar sus propias categorías, use el procedimiento siguiente:

1. Inicie sesión en Azure Portal.
2. Elija **Más servicios** > **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Administrar aplicaciones**.
4. En la carga de trabajo **Aplicaciones móviles**, elija **Instalación** > **Categorías de aplicaciones**.
5. En la hoja **Categorías de aplicaciones**, se muestra una lista de las categorías actuales. Elija una de las siguientes acciones:
    - **Crear una categoría**: en la hoja **Crear categoría**, escriba un nombre para la nueva categoría. Los nombres pueden escribirse en un solo idioma e Intune no los traduce. Cuando haya terminado, haga clic en **Crear**.
    - **Editar una categoría**: para una categoría en la lista, elija '**...** '. En la hoja **Propiedad**, puede escribir un nuevo nombre para la categoría o eliminar la categoría.


## <a name="apps-added-automatically-by-intune"></a>Aplicaciones agregadas automáticamente mediante Intune

Las siguientes aplicaciones, publicadas por Microsoft, están integradas en Intune y preparadas para asignarse:

|||
|-|-|
|Nombre|Plataforma|Tipo de aplicación|
|Windows Information Protection|Android|Aplicación de Google Play Store administrada|
|Dynamics CRM para teléfonos|Android|Aplicación de Google Play Store administrada|
|Dynamics CRM para tabletas|Android|Aplicación de Google Play Store administrada|
|Excel|iOS|Aplicación de App Store administrada|
|Excel|Android|Aplicación de Google Play Store administrada|
|Explorador administrado|Android|Aplicación de Google Play Store administrada|
|Explorador administrado|iOS|Aplicación de App Store administrada|
|Microsoft Dynamics CRM en teléfonos|iOS|Aplicación de App Store administrada|
|Microsoft Dynamics CRM en tabletas|iOS|Aplicación de App Store administrada|
|Microsoft Power BI|iOS|Aplicación de App Store administrada|
|Microsoft Power BI|Android|Aplicación de Google Play Store administrada|
|Microsoft SharePoint|iOS|Aplicación de App Store administrada|
|Microsoft SharePoint|Android|Aplicación de Google Play Store administrada|
|Microsoft Teams|Android|Aplicación de Google Play Store administrada|
|Microsoft Teams|iOS|Aplicación de App Store administrada|
|OneDrive|iOS|Aplicación de App Store administrada|
|OneDrive|Android|Aplicación de Google Play Store administrada|
|OneNote|iOS|Aplicación de App Store administrada|
|Outlook|Android|Aplicación de Google Play Store administrada|
|Outlook|iOS|Aplicación de App Store administrada|
|Grupos de Outlook|Android|Aplicación de Google Play Store administrada|
|Grupos de Outlook|iOS|Aplicación de App Store administrada|
|PowerPoint|iOS|Aplicación de App Store administrada|

## <a name="next-steps"></a>Pasos siguientes

Elija uno de los siguientes temas para obtener información sobre cómo agregar aplicaciones ara cada plataforma a Intune:

- [Aplicaciones de Google Play Store](/intune-azure/manage-apps/android-store-app)
- [Aplicaciones de línea de negocio para Android](/intune-azure/manage-apps/android-lob-app)
- [Aplicaciones de App Store](/intune-azure/manage-apps/ios-store-app)
- [Aplicaciones de línea de negocio para iOS](/intune-azure/manage-apps/ios-lob-app)
- [Aplicaciones web (para todas las plataformas)](/intune-azure/manage-apps/web-app)
- [Aplicaciones de la Tienda Windows Phone 8.1](/intune-azure/manage-apps/windows-phone-8-1-store-app)
- [Aplicaciones de la Tienda Windows](/intune-azure/manage-apps/windows-store-app)
