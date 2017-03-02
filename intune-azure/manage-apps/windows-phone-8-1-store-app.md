---
title: "Adición de aplicaciones de la tienda de Windows Phone 8.1 a Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda sobre cómo agregar aplicaciones de la tienda de Windows Phone 8.1 a Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 7b09c7425f9649cd14ae4a9970577a33aeb83ac6
ms.lasthandoff: 02/18/2017

---

# <a name="how-to-add-windows-phone-81-store-apps-to-microsoft-intune"></a>Adición de aplicaciones de la Tienda de Windows Phone 8.1 a Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Administrar aplicaciones**.
4. En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En la hoja **Agregar aplicación**, elija **Información de la aplicación**.
7. En la hoja **Editar aplicación**, configure la siguiente información. Cuando haya terminado, haga clic en **Aceptar**. Dependiendo de la aplicación que haya elegido, algunos de los valores de esta hoja pueden haber sido rellenados automáticamente:
    - **Nombre de la aplicación**: escriba el nombre de la aplicación tal como se mostrará en el Portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se mostrará a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción de la aplicación**: escriba una descripción de la aplicación. Se mostrará a los usuarios en el portal de empresa.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **URL de la tienda de aplicaciones**: escriba la dirección URL de la tienda de aplicaciones de la aplicación que quiere crear.
    - **Sistema operativo mínimo**: en la lista, elija la versión mínima del sistema operativo en la que se puede instalar la aplicación. Si la aplicación se asigna a un dispositivo con un sistema operativo anterior, no se instalará.
    - **Categoría (opcional)**: seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Así les resultará más fácil a los usuarios encontrar la aplicación cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente,, escriba un nombre para el propietario de esta aplicación, por ejemplo, **departamento de Recursos Humanos**.
    - **Notas**: escriba notas que le gustaría asociar a esta aplicación.
    - **Cargar icono**: carga un icono que se asociará a la aplicación. Será el icono que se muestre con la aplicación cuando los usuarios examinen el portal de empresa.
8. Cuando haya terminado, en la hoja **Agregar aplicación**, elija **Guardar**.

La aplicación que ha creado se muestra en la lista de aplicaciones donde puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](/intune-azure/manage-apps/deploy-apps).
