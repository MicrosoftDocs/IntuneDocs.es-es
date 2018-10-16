---
title: Instalación de Office 365 en dispositivos macOS con Microsoft Intune
titlesuffix: ''
description: Obtenga información sobre cómo usar Microsoft Intune para instalar aplicaciones de Office 365 en dispositivos macOS.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b348d785d12cd044b12dca4cad9d2daaa1baedf4
ms.sourcegitcommit: 11bd3dbbc9dd762df7c6d20143f2171799712547
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2018
ms.locfileid: "48903450"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Asignación de Office 365 a dispositivos macOS con Microsoft Intune

Este tipo de aplicación facilita la asignación de aplicaciones de Office 365 2016 a los dispositivos macOS. Con este tipo de aplicación, puede instalar Word, Excel, PowerPoint, Outlook y OneNote. Para ayudar a mantener las aplicaciones más seguras y actualizadas, las aplicaciones incluyen Microsoft AutoUpdate (MAU). Las aplicaciones que desea se muestran como una aplicación en la lista de aplicaciones de la consola de Intune.


## <a name="before-you-start"></a>Antes de empezar

Antes de empezar a agregar Office 365 a dispositivos macOS, debe entender la siguiente información:

- Los dispositivos en los que implementa estas aplicaciones deben ejecutar macOS 10.10 o una versión posterior.
- Intune admite la adición de aplicaciones de Office que se incluyen únicamente con el conjunto de aplicaciones de Office 2016 para Mac.
- Si alguna aplicación de Office está abierta cuando Intune instala el conjunto de aplicaciones, los usuarios podrían perder los datos de los archivos no guardados.

## <a name="create-and-configure-the-app-suite"></a>Creación y configuración del conjunto de aplicaciones

Agregue Office 365 desde el panel **Aplicaciones**.
1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Supervisión y administración** > **Intune**.
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. En el panel de la carga de trabajo **Aplicaciones cliente**, en **Administrar**, seleccione **Aplicaciones**. 
5. Seleccione **Agregar**.
6. En la lista **Tipo de aplicación**, seleccione **macOS** en el grupo **Conjunto de aplicaciones Office 365**.
7. Para obtener información sobre el conjunto de aplicaciones, seleccione **Información del conjunto de aplicaciones**.  
    Esta información le ayuda a identificar el conjunto de aplicaciones en Intune y, además, ayuda a los usuarios finales a encontrarlo en el Portal de empresa.
8. Escriba la información siguiente:
    - **Nombre del conjunto**: escriba el nombre del conjunto tal como se muestra en el Portal de empresa. Asegúrese de que todos los nombres de conjuntos de aplicaciones que use sean únicos. Si el mismo nombre del conjunto ya existe, solo se muestra una de las aplicaciones a los usuarios en el portal de empresa.
    - **Descripción del conjunto**: escriba una descripción del conjunto de aplicaciones.
    - **Publicador**: Microsoft aparece como publicador.
    - **Categoría**: seleccione una o más de las categorías de aplicaciones integradas, o una categoría que haya creado. Este valor facilita que los usuarios encuentren el conjunto de aplicaciones cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: seleccione esta opción para mostrar el conjunto de aplicaciones de forma destacada en la página principal del Portal de empresa cuando los usuarios busquen aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: Microsoft aparece como desarrollador.
    - **Propietario**: Microsoft aparece como propietario.
    - **Notas**: opcionalmente, escriba las notas que desea asociar a esta aplicación.
    - **Logotipo**: el logotipo de Office 365 se muestra con la aplicación cuando los usuarios buscan en el Portal de empresa.
9. Seleccione **Aceptar**.
10. En el panel **Agregar aplicación**, seleccione **Agregar**.  
    El conjunto aparece en la lista de aplicaciones como una sola entrada.

## <a name="configure-app-assignments"></a>Configuración de asignaciones de aplicaciones

En este paso, configure las asignaciones para el conjunto de aplicaciones. 

1. En la lista de aplicaciones, seleccione el conjunto de aplicaciones **Office 365** para mostrar la hoja de información general de **Office 365**.
2. En el panel **Office 365**, seleccione **Asignaciones**.
3. Para agregar un grupo que usará el conjunto de aplicaciones, seleccione **Agregar grupo**.  
    Aparece el panel **Agregar grupo**.
4. Establezca **Tipo de asignación** en **Obligatoria** o **Disponible**.
5. Asigne el conjunto de aplicaciones a los grupos seleccionados. Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).

    >[!Note]
    > No se puede desinstalar el conjunto de aplicaciones de Office 365 a través de Intune.

5. En el panel **Asignar**, seleccione **Aceptar**.
6. En el panel **Agregar grupo**, seleccione **Aceptar**.
7. Seleccione **Guardar** para confirmar sus asignaciones.

## <a name="next-steps"></a>Pasos siguientes

- Para información sobre cómo agregar aplicaciones de Office 365 a dispositivos Windows 10, consulte [Asignación de aplicaciones de Office 365 ProPlus 2016 a dispositivos Windows 10 con Microsoft Intune](apps-add-office365.md).
- Para información sobre cómo incluir y excluir las asignaciones de aplicaciones para grupos de usuarios, consulte [Inclusión y exclusión de asignaciones de aplicaciones](apps-inc-exl-assignments.md).
