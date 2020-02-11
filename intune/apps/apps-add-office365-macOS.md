---
title: Instalación de Office 365 en dispositivos macOS con Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo usar Microsoft Intune para instalar aplicaciones de Office 365 en dispositivos macOS.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3cf4c2abb5506f297af8a4e77145abea5360381b
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755364"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Asignación de Office 365 a dispositivos macOS con Microsoft Intune

Este tipo de aplicación facilita la asignación de aplicaciones de Office 365 2016 a los dispositivos macOS. Con este tipo de aplicación, puede instalar Word, Excel, PowerPoint, Outlook y OneNote. Para ayudar a mantener las aplicaciones más seguras y actualizadas, las aplicaciones incluyen Microsoft AutoUpdate (MAU). Las aplicaciones que desea se muestran como una aplicación en la lista de aplicaciones de la consola de Intune.


## <a name="before-you-start"></a>Antes de empezar

Antes de empezar a agregar Office 365 a dispositivos macOS, debe entender la siguiente información:

- Los dispositivos en los que implementa estas aplicaciones deben ejecutar macOS 10.10 o una versión posterior.
- Intune admite la adición de aplicaciones de Office que se incluyen únicamente con el conjunto de aplicaciones de Office 2016 para Mac.
- Si alguna aplicación de Office está abierta cuando Intune instala el conjunto de aplicaciones, los usuarios podrían perder los datos de los archivos no guardados.

## <a name="select-the-office-365-suite-app-type"></a>Selección del tipo de aplicación Conjunto de aplicaciones Office 365

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. Seleccione **macOS** en la sección **Conjunto de aplicaciones Office 365** del panel **Seleccionar tipo de aplicación**.
4. Haga clic en **Seleccionar**. Se muestran los pasos para **agregar Conjunto de aplicaciones Office 365**.

## <a name="step-1---app-suite-information"></a>Paso 1: Información del conjunto de aplicaciones

En este paso, proporcionará información sobre el conjunto de aplicaciones. Esta información le ayuda a identificar el conjunto de aplicaciones en Intune y, además, ayuda a los usuarios finales a encontrarlo en el Portal de empresa.

1. En la página **Información del conjunto de aplicaciones**, puede confirmar o modificar los valores predeterminados:
    - **Nombre del conjunto de aplicaciones**: escriba el nombre del conjunto tal como se muestra en el Portal de empresa. Asegúrese de que todos los nombres de conjuntos de aplicaciones que use sean únicos. Si el mismo nombre del conjunto ya existe, solo se muestra una de las aplicaciones a los usuarios en el portal de empresa.
    - **Descripción del conjunto de aplicaciones** : escriba una descripción del conjunto de aplicaciones. Por ejemplo, podría mostrar las aplicaciones que seleccionó para incluir.
    - **Publicador**: Microsoft aparece como publicador.
    - **Categoría**: de manera opcional, seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Este valor facilita que los usuarios encuentren el conjunto de aplicaciones cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: seleccione esta opción para mostrar el conjunto de aplicaciones de forma destacada en la página principal del Portal de empresa cuando los usuarios busquen aplicaciones.
    - **Dirección URL de información**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: Microsoft aparece como desarrollador.
    - **Propietario**: Microsoft aparece como propietario.
    - **Notas**: escriba las notas que desea asociar a esta aplicación.
    - **Logotipo**: el logotipo de Office 365 se muestra con la aplicación cuando los usuarios buscan en el Portal de empresa.
2. Haga clic en **Siguiente** para mostrar la página **Etiquetas de ámbito**.

## <a name="step-2---select-scope-tags-optional"></a>Paso 2: Selección de Etiquetas de ámbito (opcional)
Puede usar las etiquetas de ámbito para determinar quién puede ver información de la aplicación cliente en Intune. Para obtener más información sobre las etiquetas de ámbito, consulte [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Uso del control de acceso basado en roles y de las etiquetas de ámbito para la TI distribuida).

1. Si quiere, haga clic en **Seleccionar etiquetas de ámbito** para agregar etiquetas de ámbito para el conjunto de aplicaciones. 
2. Haga clic en **Siguiente** para abrir la página **Asignaciones**.

## <a name="step-3---assignments"></a>Paso 3: Asignaciones

1. Seleccione las asignaciones de grupo **Requerido**, **Disponible para dispositivos inscritos** para el conjunto de aplicaciones. Para más información, consulte [Agregar grupos para organizar usuarios y dispositivos](~/fundamentals/groups-add.md) y [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).

    >[!Note]
    > No se puede desinstalar el conjunto de aplicaciones de Office 365 para macOS a través de Intune.

2. Elija **Siguiente** para mostrar la página **Revisar y crear**. 

## <a name="step-4---review--create"></a>Paso 4: Revisión y creación

1. Revise los valores y la configuración que especificó para el conjunto de aplicaciones.
2. Cuando haya terminado, haga clic en **Crear** para agregar la aplicación a Intune.

    Se muestra la hoja **Información general** correspondiente al conjunto de aplicaciones de Office 365 para Windows 10. El conjunto aparece en la lista de aplicaciones como una sola entrada.

## <a name="next-steps"></a>Pasos siguientes

- Para información sobre cómo agregar aplicaciones de Office 365 a dispositivos Windows 10, consulte [Asignación de aplicaciones de Office 365 ProPlus 2016 a dispositivos Windows 10 con Microsoft Intune](apps-add-office365.md).
- Para información sobre cómo incluir y excluir las asignaciones de aplicaciones para grupos de usuarios, consulte [Inclusión y exclusión de asignaciones de aplicaciones](apps-inc-exl-assignments.md).
