---
title: "Cómo agregar aplicaciones a Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: estos procedimientos le ayudarán a tener sus aplicaciones en Intune listas para ser asignadas a usuarios y dispositivos. "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e4a6aaa1a8e23dc2c58345f73ff8db86018843e1
ms.openlocfilehash: fe12a6b890c2d5cba874e820afbe7671b754deb5
ms.lasthandoff: 04/11/2017

---

# <a name="how-to-add-an-app-to-microsoft-intune"></a>Agregar una aplicación a Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Antes de poder administrar y asignar aplicaciones a los usuarios, debe agregarlos a Intune. Intune admite una gran variedad de distintos tipos de aplicaciones y las opciones podrían ser diferentes para cada tipo.

Intune permite agregar y asignar estos tipos de aplicaciones:

![Tipos de aplicaciones compatibles con Intune](./media/app-types.png)

Se admiten las siguientes plataformas. Haga clic en uno de los temas para más información sobre cómo agregar cada tipo de aplicación.

- [Aplicaciones de la Tienda Android](/intune-azure/manage-apps/android-store-app)
- [Aplicaciones de la Tienda iOS](/intune-azure/manage-apps/ios-store-app)
- [Aplicaciones web (para todas las plataformas)](/intune-azure/manage-apps/web-app)
- [Aplicaciones de la Tienda de Windows Phone 8.1](/intune-azure/manage-apps/windows-phone-8-1-store-app)
- [Aplicaciones de la Tienda Windows](/intune-azure/manage-apps/windows-store-app)

> [!NOTE]
> Al agregar e implementar una aplicación desde un almacén, los usuarios finales deben tener una cuenta con el almacén para poder instalar la aplicación.

## <a name="cloud-storage-space"></a>Espacio de almacenamiento en nube
Todas las aplicaciones que cree mediante el tipo de instalación del instalador de software (por ejemplo, una aplicación de línea de negocio) se deben empaquetar y cargar en el almacenamiento en la nube de Microsoft Intune. Una suscripción de prueba de Intune incluye 2 gigabytes (GB) de almacenamiento en nube destinados a almacenar actualizaciones y aplicaciones administradas. Una suscripción completa incluye 20 GB de espacio de almacenamiento.

Puede adquirir almacenamiento adicional para Intune usando el método de compra original.  Si el importe se le ha facturado o lo ha abonado con tarjeta de crédito, visite el [portal de administración de suscripciones](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  De lo contrario, póngase en contacto con su asociado o agente de ventas.

Los requisitos de espacio de almacenamiento en nube son los siguientes:

-   Todos los archivos de instalación deben encontrarse en la misma carpeta.
-   El tamaño máximo de archivo de cualquier archivo que se cargue es de 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Creación y edición de categorías de aplicaciones 

Se pueden usar categorías de aplicaciones para ordenar las aplicaciones de forma que sea más fácil para los usuarios finales encontrarlas en el Portal de empresa. Puede asignar una o varias categorías a una aplicación, por ejemplo, **Desarrollador de aplicaciones** o **Communication apps** (Aplicaciones de comunicación). Al agregar una aplicación a Intune, tiene la opción de seleccionar la categoría que quiera. Use los temas específicos de la plataforma para agregar una aplicación y asignar categorías. Para crear y editar sus propias categorías, use el procedimiento siguiente: 

1. Inicie sesión en el portal de Azure. 
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**. 
3. En la hoja **Intune**, elija **Administrar aplicaciones**. 
4. En la carga de trabajo **Mobile Apps**, elija **Configuración** > **Categorías de aplicaciones**. 
5. En la hoja **Categorías de aplicaciones**, se muestra una lista de las categorías actuales. Elija una de las acciones siguientes: 
    - **Crear una categoría**: en la hoja **Crear categoría**, escriba un nombre para la nueva categoría. Los nombres solo pueden escribirse en un solo idioma, Intune no los traduce. Haga clic en **Crear** cuando acabe.
    - **Editar una categoría**: para cualquier categoría de la lista, elija '**...**'. En la hoja **Propiedades**, puede escribir un nuevo nombre para la categoría o eliminarla.




