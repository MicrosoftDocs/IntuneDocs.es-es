---
title: "Adición de aplicaciones a Microsoft Intune | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: estos procedimientos le ayudarán a tener sus aplicaciones en Intune listas para ser asignadas a usuarios y dispositivos. "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 969ce8deae9142944f3481172277dc252baa5779
ms.openlocfilehash: a7838f57b2eb8bd36a875f7b5b001b12eafcbf8d

---

# <a name="how-to-add-an-app"></a>Adición de una aplicación 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Antes de poder administrar y asignar aplicaciones a los usuarios, debe agregarlos a Intune. Intune admite una gran variedad de distintos tipos de aplicaciones y las opciones podrían ser diferentes para cada tipo.

Intune permite agregar y asignar estos tipos de aplicaciones:

![Tipos de aplicaciones compatibles con Intune](./media/app-types.png)

Se admiten las siguientes plataformas. Haga clic en uno de los temas para más información sobre cómo agregar cada tipo de aplicación.

- [Aplicaciones Android de línea de negocio](/intune-azure/manage-apps/android-lob-app)
- [Aplicaciones de la Tienda Android](/intune-azure/manage-apps/android-store-app)
- [Aplicaciones iOS de línea de negocio](/intune-azure/manage-apps/ios-lob-app)
- [Aplicaciones de la Tienda iOS](/intune-azure/manage-apps/ios-store-app)
- [Aplicaciones web (para todas las plataformas)](/intune-azure/manage-apps/web-app)
- [Aplicaciones de la Tienda de Windows Phone 8.1](/intune-azure/manage-apps/windows-phone-8-1-store-app)
- [Aplicaciones de la Tienda Windows](/intune-azure/manage-apps/windows-store-app)

> [!NOTE]
> Al agregar e implementar una aplicación desde un almacén, los usuarios finales deben tener una cuenta con el almacén para poder instalar la aplicación.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Creación y edición de categorías de aplicaciones 

Se pueden usar categorías de aplicaciones para ordenar las aplicaciones de forma que sea más fácil para los usuarios finales encontrarlas en el Portal de empresa. Puede asignar una o varias categorías a una aplicación, por ejemplo, **Desarrollador de aplicaciones** o **Communication apps** (Aplicaciones de comunicación). Al agregar una aplicación a Intune, tiene la opción de seleccionar la categoría que quiera. Use los temas específicos de la plataforma para agregar una aplicación y asignar categorías. Para crear y editar sus propias categorías, use el procedimiento siguiente: 

1. Inicie sesión en el portal de Azure. 
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**. 
3. En la hoja **Intune**, elija **Administrar aplicaciones**. 
4. En la carga de trabajo **Mobile Apps**, elija **Configuración** > **Categorías de aplicaciones**. 
5. En la hoja **Categorías de aplicaciones**, se muestra una lista de las categorías actuales. Elija una de las acciones siguientes: 
    - **Crear una categoría**: en la hoja **Crear categoría**, escriba un nombre para la nueva categoría. Los nombres solo pueden escribirse en un solo idioma, Intune no los traduce. Haga clic en **Crear** cuando acabe.
    - **Editar una categoría**: para cualquier categoría de la lista, elija '**...**'. En la hoja **Propiedades**, puede escribir un nuevo nombre para la categoría o eliminarla. --->






<!--HONumber=Feb17_HO1-->


