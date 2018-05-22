---
title: Adición de aplicaciones integradas a dispositivos móviles con Microsoft Intune
titlesuffix: ''
description: Obtenga información sobre cómo puede usar Intune para facilitar la instalación de aplicaciones integradas en dispositivos móviles.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5b67b50a5bd372541cf0842696e5012ca991d8b8
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Incorporación de aplicaciones integradas a Microsoft Intune

Las aplicaciones *integradas* facilitan la asignación de aplicaciones administradas y seleccionadas, como aplicaciones de Office 365, a dispositivos iOS y Android. Puede asignar aplicaciones concretas para este tipo de aplicación, como Excel, OneDrive, Outlook, Skype, etc. Después de agregar una aplicación, el tipo de aplicación se muestra como *Aplicación iOS integrada* o *Aplicación Android integrada*. Con el tipo de aplicación integrada, puede elegir cuál de estas aplicaciones quiere publicar para los usuarios del dispositivo.

En versiones anteriores de la consola de Intune, Intune ofrecía varias aplicaciones de Office 365 administradas de forma predeterminada, como Outlook y OneDrive. Los tipos de aplicación para estas aplicaciones administradas se etiquetaban como *Aplicación de la tienda iOS administrada* o *Aplicación Android de la tienda administrada*. En lugar de usar estos tipos de aplicación, se recomienda que utilice el tipo de aplicación integrada. Mediante el uso del tipo de aplicación integrada, dispone de flexibilidad adicional para editar y eliminar aplicaciones de Office 365.

>[!NOTE]
>Las aplicaciones predeterminadas de Office 365 etiquetadas como *Aplicación de la tienda iOS administrada* y *Aplicación Android de la tienda administrada* se quitan de la lista de aplicaciones cuando se eliminan todas las asignaciones.

## <a name="add-a-built-in-app"></a>Incorporación de una aplicación integrada

Para agregar una aplicación integrada a las aplicaciones que tiene disponibles en Microsoft Intune, haga lo siguiente:
1. Inicie sesión en Azure Portal.
2. Para mostrar el panel de Microsoft Intune, seleccione **Más servicios** > **Supervisión y administración** > **Intune**.
3. En el panel **Intune**, seleccione **Aplicaciones móviles**.
4. En el panel **Aplicaciones móviles**, en **Administrar** seleccione **Aplicaciones**.
5. Seleccione **Agregar**.
6. En el panel de aplicaciones **Agregar**, en la lista **Tipo de aplicación**, seleccione **Aplicación integrada**.
7. Seleccione **Seleccionar aplicación**.
8. En el panel **Aplicación integrada**, seleccione las aplicaciones que desea incluir.
9. Luego, en el panel **Agregar aplicación**, seleccione **Agregar**.


## <a name="configure-app-information"></a>Configuración de información de la aplicación

Puede modificar la información sobre la aplicación integrada. Esta información le ayuda a identificar la aplicación en Intune y ayuda a los usuarios a encontrar la aplicación en el portal de empresa.
1. En el panel **Aplicaciones móviles - Aplicaciones**, seleccione la aplicación integrada que quiera modificar.  
    Se muestra un panel de la aplicación integrada.
2. En **Administrar**, seleccione la opción **Propiedades**.
3. Para modificar la información de la aplicación integrada, seleccione la opción **Configurar**.
4. En el panel **Información de la aplicación**, puede modificar la información siguiente:
    - **Nombre**: escriba el nombre de la aplicación integrada tal como se muestra en el portal de empresa. Asegúrese de que todos los nombres que use sean únicos. Si el mismo nombre de aplicación existe dos veces, solo se muestra a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción:** escriba una descripción de la aplicación. 
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **Categoría**: opcionalmente, seleccione una o varias de las categorías de aplicaciones integradas. Configurar esta opción facilita que los usuarios puedan encontrar la aplicación cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente, escriba un nombre para el propietario de esta aplicación (por ejemplo, *Departamento de Recursos Humanos*).
    - **Notas**: escriba las notas que desea asociar a esta aplicación.
    - **Cargar icono**: cargue un icono que se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
4. Seleccione **Aceptar**.
5. En el panel **Propiedades**, seleccione **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

- Ahora puede asignar las aplicaciones a los grupos que elija. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).
