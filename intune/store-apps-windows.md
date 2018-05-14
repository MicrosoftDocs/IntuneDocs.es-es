---
title: Agregar aplicaciones de Microsoft Store a Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo agregar aplicaciones de Microsoft Store (Tienda Windows) a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: baa9b20ee8820915f3cdee6ee26ec2429c93d63b
ms.sourcegitcommit: 2b5d88c434bda7f1cdc32d1ccacc6b341a9a399b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Agregar aplicaciones de Microsoft Store a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para poder asignar, supervisar, configurar o proteger las aplicaciones, debe agregarlas a Intune. 

## <a name="add-an-app-to-intune"></a>Agregar una aplicación a Intune
Puede agregar una aplicación de Microsoft Store a Intune si hace lo siguiente:

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**.  
    Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, seleccione **Aplicaciones móviles**.
4. En el panel de carga de trabajo **Aplicaciones móviles**, en **Administrar**, seleccione **Aplicaciones**.
5. En el panel **Aplicaciones**, seleccione **Agregar**.
6. En el panel **Agregar aplicación**, seleccione un **Tipo de aplicación** **Windows** y luego seleccione **Información de la aplicación**.
7. En el panel **Información de la aplicación**, agregue la información de la aplicación. Según la aplicación que haya elegido, algunos de los valores de este panel pueden haberse rellenado automáticamente:
    - **Nombre**: escriba el nombre de la aplicación como se va a mostrar en el Portal de empresa. Asegúrese de que cualquier nombre de aplicación que use sea exclusivo. Si hay un nombre de aplicación duplicado, solo se muestra uno a los usuarios del Portal de empresa.
    - **Descripción:** escriba una descripción de la aplicación. Esta descripción se muestra a los usuarios del Portal de empresa.
    - **Editor**: escriba el nombre del editor de la aplicación.
    - **Dirección URL de AppStore**: escriba la dirección URL de App Store de la aplicación que quiere crear.
    - **Categoría**: de manera opcional, seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Esto facilita que los usuarios puedan encontrar la aplicación cuando exploran el Portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: seleccione esta opción para mostrar el conjunto de aplicaciones de forma destacada en la página principal del Portal de empresa cuando los usuarios busquen aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente, escriba un nombre para el propietario de esta aplicación, por ejemplo, *Departamento de Recursos Humanos*.
    - **Notas**: opcionalmente, escriba las notas que desea asociar a esta aplicación.
    - **Logotipo**: opcionalmente, cargue un icono que se asociará con la aplicación. Este icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
8. Seleccione **Aceptar**.
9. Seleccione **Agregar**.

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione. 

## <a name="next-steps"></a>Pasos siguientes
- [Asignar aplicaciones a grupos](apps-deploy.md)
