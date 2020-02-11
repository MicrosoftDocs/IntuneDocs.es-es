---
title: Agregar aplicaciones de la Tienda de Windows Phone 8.1 a Microsoft Intune
titleSuffix: ''
description: En este tema se describe cómo agregar aplicaciones de la Tienda de Windows Phone 8.1 a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d43e0f913020e3e2e8b0ac463d5983447d7c1fa2
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754956"
---
# <a name="add-windows-phone-81-store-apps-to-microsoft-intune"></a>Agregar aplicaciones de la Tienda de Windows Phone 8.1 a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Antes de asignar una aplicación a un dispositivo o a un grupo de usuarios, primero debe agregar la aplicación a Microsoft Intune. 

## <a name="add-an-app-to-intune"></a>Agregar una aplicación a Intune
Puede agregar una aplicación de la Tienda de Windows Phone 8.1 a Intune desde Azure Portal si hace lo siguiente:

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Seleccionar tipo de aplicación**, en los tipos de **Aplicación de la Tienda** disponibles, seleccione **Aplicación de la Tienda Windows Phone 8.1**.
4. Haga clic en **Seleccionar**.<br>
   Se muestran los pasos para **Agregar aplicación**.
5. Para configurar la **Información de la aplicación** para las aplicaciones de la Tienda de Windows Phone 8.1, vaya a [Microsoft Store](https://www.microsoft.com/store/apps/windows-phone) y busque la aplicación que quiere implementar. Muestre la página de la aplicación y tome nota de los detalles de la aplicación. 
6. En la página **Información de la aplicación**, agregue los detalles de la aplicación:
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
7. Haga clic en **Siguiente** para mostrar la página **Etiquetas de ámbito**.
8. Si quiere, haga clic en **Seleccionar etiquetas de ámbito** para agregar etiquetas de ámbito para la aplicación. Para más información, consulte [Usar control de acceso basado en rol (RBAC) y etiquetas de ámbito para TI distribuida](~/fundamentals/scope-tags.md).
9. Haga clic en **Siguiente** para abrir la página **Asignaciones**.
10. Seleccione las asignaciones de grupo para la aplicación. Para más información, consulte [Agregar grupos para organizar usuarios y dispositivos](~/fundamentals/groups-add.md). 
11. Elija **Siguiente** para mostrar la página **Revisar y crear**. Revise los valores y la configuración que especificó para la aplicación.
12. Cuando haya terminado, haga clic en **Crear** para agregar la aplicación a Intune.

Se muestra la hoja **Información general** de la aplicación que creó.


La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione.

## <a name="next-steps"></a>Pasos siguientes

- [Asignar aplicaciones a grupos](apps-deploy.md)
