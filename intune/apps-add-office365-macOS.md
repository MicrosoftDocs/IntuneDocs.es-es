---
title: "Instalación de Office 365 en dispositivos de Mac OS con Intune"
titlesuffix: Azure portal
description: "Obtenga información sobre cómo puede usar Intune para facilitar la instalación de aplicaciones de Office 365 en dispositivos macOS."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e0ad0b99a2c8a602b5e542530a1d437065461b2
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Asignación de Office 365 a dispositivos macOS con Microsoft Intune

Este tipo de aplicación facilita la asignación de aplicaciones de Office 365 a los dispositivos macOS. Este nuevo tipo de aplicación le permite instalar Word, Excel, PowerPoint, Outlook y OneNote. Estas aplicaciones también incluyen Microsoft AutoUpdater (MAU) para ayudar a mantener las aplicaciones más seguras y actualizadas. Las aplicaciones que desea que aparezcan como una aplicación en la lista de aplicaciones de la consola de Intune.


## <a name="before-you-start"></a>Antes de empezar

- Los dispositivos en los que implementa estas aplicaciones deben ejecutar macOS 10.10 o una versión posterior.
- Intune solo admite la incorporación de aplicaciones de Office incluidas con el conjunto de Office 2016 para Mac.
- Si alguna aplicación de Office está abierta cuando Intune instala el conjunto de aplicaciones, es posible que los usuarios finales pierdan los datos de los archivos no guardados.


## <a name="get-started"></a>Introducción
Agregue Office 365 utilizando la hoja **Aplicaciones**.
1.  Inicie sesión en el portal de Azure.
2.  Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3.  En la hoja **Intune**, elija **Aplicaciones móviles**.
4.  En la carga de trabajo **Aplicaciones móviles**, elija **Aplicaciones** en el grupo **Administrar**. Seleccione **Agregar**.
5.  En la hoja **Agregar aplicación**, elija **Office 365** > **macOS**.
6.  Seleccione **Agregar**.

## <a name="configure-the-app-suite"></a>Configuración del conjunto de aplicaciones

Proporcione información sobre el conjunto de aplicaciones. Esta información le ayuda a identificarlo en Intune y, además, ayuda a los usuarios finales a encontrarlo en la aplicación Portal de empresa.

1.  En la hoja **Agregar aplicación**, elija **App Suite Information** (Información del conjunto de aplicaciones).
2.  Especifique la siguiente información:
    - **Nombre del conjunto**: escriba el nombre del conjunto tal como se muestra en el portal de empresa. Asegúrese de que todos los nombres de conjuntos que use sean únicos. Si el mismo nombre del conjunto ya existe, solo se muestra una de las aplicaciones a los usuarios en el portal de empresa.
    - **Descripción del conjunto**: escriba una descripción del conjunto de aplicaciones.
    - **Publicador**: Microsoft aparece como publicador.
    - **Categoría**: de manera opcional, seleccione una o más categorías de aplicaciones integradas o una categoría que haya creado. Esto facilita que los usuarios encuentren el conjunto de aplicaciones cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: el conjunto de aplicaciones se muestra de forma destacada en la página principal de Portal de empresa de Intune cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: Microsoft aparece como desarrollador.
    - **Propietario**: Microsoft aparece como propietario.
    - **Notas**: escriba notas que le gustaría asociar a esta aplicación.
    - **Cargar icono**: Cargar un icono que se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
3.  Seleccione **Aceptar**. El conjunto aparece en la lista de aplicaciones como una sola entrada.

## <a name="configure-app-assignments"></a>Configuración de asignaciones de aplicaciones

En este paso, configure las asignaciones para el conjunto de aplicaciones. Tenga en cuenta que el tipo de aplicación disponible llegará próximamente.

1.  Seleccione el conjunto de aplicaciones en la lista de aplicaciones y seleccione **Asignaciones**.
2.  Elija **Seleccionar grupos**.
3.  Asigne el conjunto a los grupos que elija. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](/intune/apps-deploy).
4.  Para cada grupo, seleccione **Require Install** (Requerir instalación).
        >[!Note]
        > You cannot uninstall Office 365 through Intune.

5. Seleccione **Guardar** para confirmar sus asignaciones.

## <a name="next-steps"></a>Pasos siguientes

Para obtener información acerca de cómo agregar aplicaciones de Office 365 a dispositivos Windows 10, consulte [Asignación de aplicaciones de Office 365 ProPlus 2016 a dispositivos Windows 10 con Microsoft Intune](/intune/apps-add-office365).
