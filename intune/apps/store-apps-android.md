---
title: Agregar aplicaciones de la Tienda Android a Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo agregar aplicaciones de la tienda Android desde Google Play Store a Microsoft Intune.
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
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6b9f6a9303e53652959639193633cdcc00dfb99
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755092"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Agregar aplicaciones de la Tienda Android a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Antes de asignar una aplicación a un dispositivo o a un grupo de usuarios, primero debe agregar la aplicación a Microsoft Intune. 

## <a name="add-an-app"></a>Agregar una aplicación

Puede agregar una aplicación de la Tienda Android a Intune desde Azure Portal si hace lo siguiente:

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Seleccionar tipo de aplicación**, en los tipos de **Aplicación de la Tienda** disponibles, seleccione la **Aplicación de la tienda Android**.
4. Haga clic en **Seleccionar**.<br>
   Se muestran los pasos para **Agregar aplicación**.
5. Para configurar la **Información de la aplicación** correspondiente a la aplicación Android, vaya a [Google Play Store](https://play.google.com/store) y busque la aplicación que quiere implementar. Muestre la página de la aplicación y tome nota de los detalles de la aplicación. 
6. En la página **Información de la aplicación**, agregue los detalles de la aplicación:
    - **Nombre**: escriba el nombre de la aplicación como se va a mostrar en el Portal de empresa. Asegúrese de que cualquier nombre de aplicación que use sea exclusivo. Si hay un nombre de aplicación duplicado, solo se muestra uno a los usuarios del Portal de empresa.
    - **Descripción**: Escriba una descripción de la aplicación. Esta descripción se muestra a los usuarios del Portal de empresa.
    - **Publicador**: Escriba el nombre del publicador de la aplicación.
    - **Dirección URL de Appstore**: escriba la dirección URL de App Store de la aplicación que quiere crear. Use la dirección URL de la página de la aplicación cuando se muestren los detalles de la aplicación en el almacén. 
    - **Versión mínima del sistema operativo**: en la lista, seleccione la versión mínima del sistema operativo en la que se puede instalar la aplicación. Si la aplicación se asigna a un dispositivo con un sistema operativo anterior, no se instalará.
    - **Categoría**: de manera opcional, seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Esto facilita que los usuarios puedan encontrar la aplicación cuando exploran el Portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: seleccione esta opción para mostrar el conjunto de aplicaciones de forma destacada en la página principal del Portal de empresa cuando los usuarios busquen aplicaciones. Se aplica a las aplicaciones implementadas con intención disponible.
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

## <a name="next-steps"></a>Pasos siguientes

- [Asignar aplicaciones a grupos](apps-deploy.md)
