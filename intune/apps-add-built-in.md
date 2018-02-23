---
title: "Agregar aplicaciones integradas a dispositivos móviles mediante Intune"
titlesuffix: Azure portal
description: "Obtenga información sobre cómo puede usar Intune para facilitar la instalación de aplicaciones integradas en dispositivos móviles."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d622f2cb8c6b3e8c9aace4e805108ccfa71eb4d2
ms.sourcegitcommit: 754fcc31155b28d6910bba45419c6be745f8793e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-add-built-in-apps-to-microsoft-intune"></a>Cómo agregar aplicaciones integradas a Microsoft Intune

Las aplicaciones **integradas** facilitan la asignación de aplicaciones administradas y seleccionadas, como aplicaciones de Office 365, a dispositivos iOS y Android. Puede asignar aplicaciones concretas para este tipo de aplicación, como Excel, OneDrive, Outlook, Skype, etc. Después de agregar una aplicación, verá el tipo de aplicación como **Aplicación iOS integrada** o **Aplicación Android integrada**. Con el tipo de aplicación integrada, puede elegir cuál de estas aplicaciones específicas quiere publicar para los usuarios del dispositivo.

 En ediciones anteriores de la consola de Intune, Intune ofrecía varias aplicaciones de Office 365 administradas de forma predeterminada, como Outlook y OneDrive. El tipo de aplicación de estas aplicaciones administradas se etiquetaba como "Aplicación de la tienda iOS administrada" o "Aplicación Android administrada". Se recomienda usar el tipo de aplicación integrada en lugar de "Aplicación de la tienda iOS administrada" o "Aplicación Android administrada". El tipo de aplicación integrada proporciona más flexibilidad para editar y eliminar aplicaciones de Office 365.

>[!NOTE]
>Las aplicaciones predeterminadas de Office 365 etiquetadas como "Aplicación de la tienda iOS administrada" y "Aplicación Android administrada" se quitan de la lista de aplicaciones cuando se eliminan todas las asignaciones.

## <a name="add-built-in-app"></a>Agregar una aplicación integrada

Para agregar una aplicación integrada a las aplicaciones que tiene disponibles en Microsoft Intune, siga los pasos que se describen a continuación.
1.  Inicie sesión en el portal de Azure.
2.  Visualice la hoja de Microsoft Intune, eligiendo **Más servicios** > **Supervisión y administración** > **Intune**.
3.  En la hoja **Intune**, elija **Aplicaciones móviles**.
4.  En la hoja **Aplicaciones móviles**, elija **Aplicaciones** en el grupo **Administrar**.
5.  Elija **Agregar** para agregar una nueva aplicación.
6.  En la hoja de la aplicación **Agregar**, elija **Aplicación integrada** en la lista **Tipo de aplicación**.
7.  Haga clic en **Seleccionar aplicación** para elegir las aplicaciones integradas que quiera incluir.
8.  En la hoja de aplicaciones integradas, seleccione la aplicación que quiera incluir.
9.  En la hoja **Agregar aplicación**, haga clic en **Agregar** para incluir las aplicaciones.


## <a name="configure-app-information"></a>Configuración de información de la aplicación

Puede modificar la información sobre la aplicación integrada. Esta información le ayuda a identificar la aplicación en Intune y, además, ayuda a los usuarios a encontrar la aplicación en el portal de empresa.
1.  En la hoja **Aplicaciones móviles - Aplicaciones**, elija la aplicación integrada que quiera modificar. Se muestra la hoja de la aplicación integrada.
2.  Seleccione la opción **Propiedades** desde el grupo **Administrar**.
3.  Seleccione la opción **Configurar** para modificar la información de la aplicación integrada.
4.  En la hoja **Información de aplicación**, puede modificar la información siguiente:
    -   **Nombre**: escriba el nombre de la aplicación integrada tal como se muestra en el portal de empresa. Asegúrese de que todos los nombres que use sean únicos. Si el mismo nombre de aplicación existe dos veces, solo se muestra a los usuarios una de las aplicaciones en el portal de empresa.
    -   **Descripción:** escriba una descripción de la aplicación. 
    -   **Editor:** escriba el nombre del editor de la aplicación.
    -   **Categoría** (opcional): seleccione una o varias categorías de aplicaciones integradas. Configurar esta opción facilita que los usuarios puedan encontrar la aplicación cuando exploren el portal de empresa.
    -   **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    -   **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    -   **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    -   **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    -   **Propietario**: opcionalmente, escriba un nombre para el propietario de esta aplicación, por ejemplo, departamento de Recursos Humanos.
    -   **Notas**: escriba notas que le gustaría asociar a esta aplicación.
    -   **Cargar icono**: Cargar un icono que se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
3.  Cuando haya terminado, en la hoja **Información de la aplicación**, haga clic en **Aceptar**.
4.  En la hoja **Propiedades**, haga clic en **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

Ahora puede asignar las aplicaciones a los grupos de su preferencia. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).
