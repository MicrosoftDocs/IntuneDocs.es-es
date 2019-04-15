---
title: Agregar aplicaciones de la Tienda Android a Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo agregar aplicaciones de la tienda Android desde Google Play Store a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe313fb43c838e3fc41a6c911668b46f7d3dc9de
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57388572"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Agregar aplicaciones de la Tienda Android a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Antes de asignar una aplicación a un dispositivo o a un grupo de usuarios, primero debe agregar la aplicación a Microsoft Intune. 

## <a name="add-an-app"></a>Agregar una aplicación

Puede agregar una aplicación de la Tienda Android a Intune desde Azure Portal si hace lo siguiente:

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**.  
    Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. En el panel de la carga de trabajo **Aplicaciones cliente**, en **Administrar**, seleccione **Aplicaciones**.
5. Seleccione **Agregar**.
6. En el panel **Agregar aplicación**, en los tipos de **Aplicaciones de la Tienda** disponibles, seleccione **Android**.
7. Para configurar la información de la aplicación, seleccione **Configurar** y luego proporcione la siguiente información. Para aplicaciones Android, vaya a [Google Play](https://play.google.com/store) y busque la aplicación que quiera implementar. Seleccione la aplicación y anote los detalles de la aplicación. Según la aplicación que haya elegido, algunos de los valores pueden haberse rellenado automáticamente.
    - **Nombre**: escriba el nombre de la aplicación como se va a mostrar en el Portal de empresa. Asegúrese de que cualquier nombre de aplicación que use sea exclusivo. Si hay un nombre de aplicación duplicado, solo se muestra uno a los usuarios del Portal de empresa.
    - **Descripción**: Escriba una descripción de la aplicación. Esta descripción se muestra a los usuarios del Portal de empresa.
    - **Publicador**: Escriba el nombre del publicador de la aplicación.
    - **Dirección URL de Appstore**: escriba la dirección URL de App Store de la aplicación que quiere crear.
    - **Versión mínima del sistema operativo**: en la lista, seleccione la versión mínima del sistema operativo en la que se puede instalar la aplicación. Si la aplicación se asigna a un dispositivo con un sistema operativo anterior, no se instalará.
    - **Categoría**: de manera opcional, seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Esto facilita que los usuarios puedan encontrar la aplicación cuando exploran el Portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: seleccione esta opción para mostrar el conjunto de aplicaciones de forma destacada en la página principal del Portal de empresa cuando los usuarios busquen aplicaciones.
    - **Dirección URL de información**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente, escriba un nombre para el propietario de esta aplicación, por ejemplo, *Departamento de Recursos Humanos*.
    - **Notas**: opcionalmente, escriba las notas que desea asociar a esta aplicación.
    - **Logotipo**: opcionalmente, cargue un icono que se asociará con la aplicación. Este icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
1. Seleccione **Aceptar**.
2. Seleccione **Agregar**.

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione. 

## <a name="next-steps"></a>Pasos siguientes

- [Asignar aplicaciones a grupos](apps-deploy.md)
