---
title: "Instalación de Office 365 en dispositivos macOS con Microsoft Intune"
titlesuffix: 
description: "Obtenga información sobre cómo usar Microsoft Intune para instalar aplicaciones de Office 365 en dispositivos macOS."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8de14184c4d23adc79d5b519fdcf272f0d7f6804
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Asignación de Office 365 a dispositivos macOS con Microsoft Intune

El tipo **Aplicación de la Tienda** facilita la asignación de aplicaciones de Office 365 a los dispositivos macOS. Este tipo de aplicación permite instalar Word, Excel, PowerPoint, Outlook y OneNote. Estas aplicaciones también incluyen Microsoft AutoUpdater (MAU) para ayudar a mantener las aplicaciones más seguras y actualizadas. Las aplicaciones que desea que aparezcan como una aplicación en la lista de aplicaciones de la consola de Intune.


## <a name="before-you-start"></a>Antes de empezar

Antes de empezar a agregar Office 365 a los dispositivos macOS, debe entender los detalles siguientes:

- Los dispositivos en los que implementa estas aplicaciones deben ejecutar macOS 10.10 o una versión posterior.
- Intune solo admite la incorporación de aplicaciones de Office incluidas con el conjunto de Office 2016 para Mac.
- Si alguna aplicación de Office está abierta cuando Intune instala el conjunto de aplicaciones, es posible que los usuarios finales pierdan los datos de los archivos no guardados.

## <a name="create-and-configure-the-app-suite"></a>Creación y configuración del conjunto de aplicaciones

Agregue Office 365 utilizando la hoja **Aplicaciones**.
1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Supervisión y administración** > **Intune**.
3. Elija **Aplicaciones móviles** en la hoja **Intune**.
4. En la carga de trabajo **Aplicaciones móviles**, elija **Aplicaciones** en la sección **Administrar**. 
5. Haga clic en **Agregar** para mostrar la hoja **Agregar aplicación**.
6. En la lista **Tipo de aplicación**, seleccione **macOS** en el grupo **Conjunto de aplicaciones Office 365**.
7. Seleccione **Información del conjunto de aplicaciones** para proporcionar información sobre el conjunto de aplicaciones. Esta información ayuda a identificar el conjunto de aplicaciones en Intune y, además, ayuda a los usuarios finales a encontrarlo en la aplicación Portal de empresa.
8.  Especifique la siguiente información:
    - **Nombre del conjunto**: escriba el nombre del conjunto tal como se muestra en el portal de empresa. Asegúrese de que todos los nombres de conjuntos que use sean únicos. Si el mismo nombre del conjunto ya existe, solo se muestra una de las aplicaciones a los usuarios en el portal de empresa.
    - **Descripción del conjunto**: escriba una descripción del conjunto de aplicaciones.
    - **Publicador**: Microsoft aparece como publicador.
    - **Categoría**: seleccione una o más de las categorías de aplicaciones integradas, o una categoría que haya creado. Este valor facilita que los usuarios encuentren el conjunto de aplicaciones cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: este valor mostrará el conjunto de aplicaciones de forma destacada en la página principal del portal de empresa cuando los usuarios busquen aplicaciones.
    - **Dirección URL de información** (opcional): escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad** (opcional): escriba la dirección URL de un sitio web que contenga información de privacidad de esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: Microsoft aparece como desarrollador.
    - **Propietario**: Microsoft aparece como propietario.
    - **Notas** (opcional): escriba las notas que le gustaría asociar a esta aplicación.
    - **Logotipo**: el logotipo de Office 365 se muestra con la aplicación cuando los usuarios buscan en el Portal de empresa.
9.  Haga clic en **Aceptar** en la hoja **Información de la aplicación**.
10. Haga clic en **Agregar** en la hoja **Agregar aplicación**.
    El conjunto aparece en la lista de aplicaciones como una sola entrada.

## <a name="configure-app-assignments"></a>Configuración de asignaciones de aplicaciones

En este paso, configure las asignaciones para el conjunto de aplicaciones. 

1. Seleccione el conjunto de aplicaciones **Office 365** en la lista de aplicaciones para mostrar la hoja de información general **Office 365**.
2. Haga clic en **Asignaciones** desde la hoja **Office 365**.
3. Haga clic en **Agregar grupo** para agregar un grupo para usar el conjunto de aplicaciones. Aparece la hoja **Agregar grupo**.
3. Establezca el **Tipo de asignación** en **Obligatoria**.
4. Asigne el conjunto a los grupos que elija. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).

    >[!Note]
    > Para los grupos en los que se necesite el conjunto de aplicaciones de Office 365, no se puede desinstalar a través de Microsoft Intune.

5. Haga clic en **Aceptar** en la hoja **Asignar**.
6. Haga clic en **Aceptar** en la hoja **Agregar grupo**.
7. Seleccione **Guardar** para confirmar sus asignaciones.

## <a name="next-steps"></a>Pasos siguientes

- Para obtener información acerca de cómo agregar aplicaciones de Office 365 a dispositivos Windows 10, consulte [Asignación de aplicaciones de Office 365 ProPlus 2016 a dispositivos Windows 10 con Microsoft Intune](apps-add-office365.md).
- Para obtener información sobre cómo incluir y excluir las asignaciones de aplicaciones para grupos de usuarios, vea [Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune](apps-inc-exl-assignments.md).
