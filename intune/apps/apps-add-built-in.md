---
title: Adición de aplicaciones integradas a dispositivos móviles con Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo puede usar Intune para facilitar la instalación de aplicaciones integradas en dispositivos móviles.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a92699ccce4f0b2590e526b3442cd45bfda6407c
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563598"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Incorporación de aplicaciones integradas a Microsoft Intune

Las aplicaciones *integradas* facilitan la asignación de aplicaciones administradas y seleccionadas, como aplicaciones de Office 365, a dispositivos iOS y Android. Puede asignar aplicaciones concretas para este tipo de aplicación, como Excel, OneDrive, Outlook, Skype, etc. Después de agregar una aplicación, el tipo de aplicación se muestra como *Aplicación iOS integrada* o *Aplicación Android integrada*. Con el tipo de aplicación integrada, puede elegir cuál de estas aplicaciones quiere publicar para los usuarios del dispositivo.

En versiones anteriores de la consola de Intune, Intune ofrecía varias aplicaciones de Office 365 administradas de forma predeterminada, como Outlook y OneDrive. Los tipos de aplicación para estas aplicaciones administradas se etiquetaban como *Aplicación de la tienda iOS administrada* o *Aplicación Android de la tienda administrada*. En lugar de usar estos tipos de aplicación, se recomienda que utilice el tipo de aplicación integrada. Mediante el uso del tipo de aplicación integrada, dispone de flexibilidad adicional para editar y eliminar aplicaciones de Office 365.

>[!NOTE]
>Las aplicaciones predeterminadas de Office 365 etiquetadas como *Aplicación de la tienda iOS administrada* y *Aplicación Android de la tienda administrada* se quitan de la lista de aplicaciones cuando se eliminan todas las asignaciones.

## <a name="add-a-built-in-app"></a>Incorporación de una aplicación integrada

Para agregar una aplicación integrada a las aplicaciones que tiene disponibles en Microsoft Intune, haga lo siguiente:
1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel de aplicaciones **Agregar**, en la lista **Tipo de aplicación**, seleccione **Aplicación integrada**.
4. Seleccione **Seleccionar aplicación**.
5. En el panel **Aplicación integrada**, seleccione las aplicaciones que desea incluir.
6. Luego, en el panel **Agregar aplicación**, seleccione **Agregar**.


## <a name="configure-app-information"></a>Configuración de información de la aplicación

Puede modificar la información sobre la aplicación integrada. Esta información le ayuda a identificar la aplicación en Intune y ayuda a los usuarios a encontrar la aplicación en el portal de empresa.
1. Seleccione **Aplicaciones** > **Todas las aplicaciones** y seleccione la aplicación integrada que quiera modificar.  
   Se muestra un panel de la aplicación integrada.
2. Seleccione **Propiedades** > **Configurar**.
4. En el panel **Información de la aplicación**, puede modificar la información siguiente:
    - **Nombre**: Escriba el nombre de la aplicación integrada tal como se muestra en el portal de empresa. Asegúrese de que todos los nombres que use sean únicos. Si el mismo nombre de aplicación existe dos veces, solo se muestra a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción**: Escriba una descripción de la aplicación. 
    - **Publicador**: Escriba el nombre del publicador de la aplicación.
    - **Categoría**: Opcionalmente, seleccione una o varias de las categorías de aplicaciones integradas. Configurar esta opción facilita que los usuarios puedan encontrar la aplicación cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el portal de empresa**: Muestra la aplicación de forma destacada en la página principal del portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: Opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: Opcionalmente, escriba un nombre para el propietario de esta aplicación (por ejemplo, *Departamento de Recursos Humanos*).
    - **Notas**: escriba las notas que desea asociar a esta aplicación.
    - **Cargar icono**: Cargue un icono que se muestre con la aplicación cuando los usuarios examinen el portal de empresa.
4. Seleccione **Aceptar**.
5. En el panel **Propiedades**, seleccione **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

- Ahora puede asignar las aplicaciones a los grupos que elija. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).
