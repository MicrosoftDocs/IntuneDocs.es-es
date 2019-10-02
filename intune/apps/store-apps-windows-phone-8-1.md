---
title: Agregar aplicaciones de la Tienda de Windows Phone 8.1 a Microsoft Intune
titleSuffix: ''
description: En este tema se describe cómo agregar aplicaciones de la Tienda de Windows Phone 8.1 a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b47d19517549d062e0bfae3add4870868ac7d503
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724508"
---
# <a name="add-windows-phone-81-store-apps-to-microsoft-intune"></a>Agregar aplicaciones de la Tienda de Windows Phone 8.1 a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Antes de asignar una aplicación a un dispositivo o a un grupo de usuarios, primero debe agregar la aplicación a Microsoft Intune. 

## <a name="add-an-app-to-intune"></a>Agregar una aplicación a Intune
Puede agregar una aplicación de la Tienda de Windows Phone 8.1 a Intune desde Azure Portal si hace lo siguiente:

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. En el panel de la carga de trabajo **Aplicaciones cliente**, en **Administrar**, seleccione **Aplicaciones**.
5. En el panel **Aplicaciones**, seleccione **Agregar**.
6. En el panel **Agregar aplicación**, seleccione un **Tipo de aplicación** **Windows Phone 8.1** y luego seleccione **Información de la aplicación**.
7. En el panel **Información de la aplicación**, agregue la información de la aplicación. Según la aplicación que haya elegido, algunos de los valores de este panel pueden haberse rellenado automáticamente:
    - **Nombre**: escriba el nombre de la aplicación como se va a mostrar en el Portal de empresa. Asegúrese de que cualquier nombre de aplicación que use sea exclusivo. Si hay un nombre de aplicación duplicado, solo se muestra uno a los usuarios del Portal de empresa.
    - **Descripción**: Escriba una descripción de la aplicación. Esta descripción se muestra a los usuarios del Portal de empresa.
    - **Publicador**: Escriba el nombre del publicador de la aplicación.
    - **Dirección URL de Appstore**: escriba la dirección URL de App Store de la aplicación que quiere crear.
    - **Categoría**: de manera opcional, seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Esto facilita que los usuarios puedan encontrar la aplicación cuando exploran el Portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: seleccione esta opción para mostrar el conjunto de aplicaciones de forma destacada en la página principal del Portal de empresa cuando los usuarios busquen aplicaciones.
    - **Dirección URL de información**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente, escriba un nombre para el propietario de esta aplicación, por ejemplo, *Departamento de Recursos Humanos*.
    - **Notas**: opcionalmente, escriba las notas que desea asociar a esta aplicación.
    - **Logotipo**: opcionalmente, cargue un icono que se asociará con la aplicación. Este icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
8. Seleccione **Aceptar**.
9. Seleccione **Agregar**.

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione.

## <a name="next-steps"></a>Pasos siguientes

- [Asignar aplicaciones a grupos](apps-deploy.md)
