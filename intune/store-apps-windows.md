---
title: Adición de aplicaciones de Microsoft Store a Microsoft Intune
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
ms.openlocfilehash: 511cf2e01a2f5db93f0e0db9dbe2a32326c17723
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Agregar aplicaciones de Microsoft Store a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para poder asignar, supervisar, configurar o proteger las aplicaciones, debe agregarlas a Intune. Los pasos siguientes permiten agregar una aplicación de Microsoft Store a Microsoft Intune.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Aplicaciones móviles**.
4. En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En el panel **Agregar aplicación**, elija un **Tipo de aplicación** de **Windows** y elija **Información de la aplicación**.
7. En el panel **Información de la aplicación**, configure la información siguiente. Cuando haya terminado, haga clic en **Aceptar**. Dependiendo de la aplicación que haya elegido, algunos de los valores de este panel pueden haberse rellenado automáticamente:
    - **Nombre:** escriba el nombre de la aplicación tal como se mostrará en el portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se mostrará a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción**: Escriba una descripción para la aplicación que se mostrará a los usuarios en el Portal de empresa.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **Dirección URL de AppStore**: escriba la dirección URL de la tienda de aplicaciones de la aplicación que quiere crear.
    - **Categoría (opcional)**: seleccione una o varias categorías de aplicaciones integradas o una categoría que haya creado para facilitar que los usuarios encuentren la aplicación al buscar en el portal de la empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente,, escriba un nombre para el propietario de esta aplicación, por ejemplo, **departamento de Recursos Humanos**.
    - **Notas**: escriba notas que le gustaría asociar a esta aplicación.
    - **Logotipo**: cargue un icono que esté asociado a la aplicación. Este icono se muestra junto a la aplicación cuando los usuarios examinan el portal de empresa.
8. Cuando haya terminado, en el panel **Agregar aplicación**, elija **Agregar**.

La aplicación que ha creado se muestra en la lista de aplicaciones donde puede asignarla a los grupos que elija. 

## <a name="next-steps"></a>Pasos siguientes
- [Asignación de aplicaciones a grupos](apps-deploy.md)