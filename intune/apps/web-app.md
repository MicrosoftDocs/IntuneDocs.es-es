---
title: Agregar aplicaciones web a Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo agregar aplicaciones web (aplicaciones cliente-servidor) a Microsoft Intune.
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
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e018fb9888db19995556a6671d93a1db5fa78c2a
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415440"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Agregar aplicaciones web a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune admite diversos tipos de aplicación, incluidas aplicaciones web. Una aplicación web es una aplicación cliente-servidor. El servidor proporciona la aplicación web, que incluye la interfaz de usuario, el contenido y la funcionalidad. Además, las plataformas de hospedaje web modernas normalmente ofrecen seguridad, equilibrio de carga y otras ventajas. Una aplicación web se mantiene por separado en Internet. Microsoft Intune se usa para que apunte a este tipo de aplicación. También puede asignar los grupos de usuarios que pueden acceder a esta aplicación. 

Antes de poder administrar y asignar aplicaciones a los usuarios, agregue la aplicación a Intune. 

Intune crea un acceso directo a la aplicación web en el dispositivo del usuario. Si se trata de dispositivos iOS/iPadOS, se agrega un acceso directo a la aplicación web en la pantalla principal. En el caso de los dispositivos de Administración de dispositivos Android, se agrega un acceso directo a la aplicación web en el widget del portal de empresa de Intune, que el usuario debe anclar manualmente. En el caso de los dispositivos Windows, se coloca un acceso directo a la aplicación web en el menú Inicio.

> [!Note]
> Para poder iniciar aplicaciones web, debe haber un explorador instalado en el dispositivo del usuario. 

> [!Note]
> Para dispositivos Android Enterprise, consulte [Vínculos web de Google Play](apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="add-a-web-app-to-intune"></a>Agregar una aplicación web a Intune
Para agregar una aplicación a Intune como acceso directo a una aplicación de Internet, haga lo siguiente:

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**.
3. En el panel **Seleccionar el tipo de aplicación**, en los **Otros** disponibles, seleccione **Enlace web**.
4. Haga clic en **Seleccionar**. Se muestran los pasos para **Agregar aplicación**.
5. En el panel **Información de aplicación**, agregue la información siguiente:
    - **Nombre**:  escriba el nombre de la aplicación como se va a mostrar en el Portal de empresa. 

        > [!NOTE]
        > Si cambia el nombre de la aplicación a través de Azure Portal de Intune una vez que ha implementado e instalado la aplicación, ya no se podrá llegar a la aplicación mediante comandos.

    - **Descripción**: Escriba una descripción de la aplicación. Esta descripción se muestra a los usuarios del Portal de empresa.
    - **Publicador**: escriba el nombre del publicador de esta aplicación.
    - **Dirección URL de la aplicación**: escriba la dirección URL del sitio web que hospeda la aplicación que quiere asignar.
    - **Categoría**: de manera opcional, seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Esto facilita que los usuarios puedan encontrar la aplicación cuando exploran el Portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: seleccione esta opción para mostrar el conjunto de aplicaciones de forma destacada en la página principal del Portal de empresa cuando los usuarios busquen aplicaciones.
    - **Se necesita Managed Browser para abrir este vínculo**: seleccione esta opción para asignar a los usuarios un vínculo a un sitio web o aplicación web que puedan abrir en Intune Managed Browser. Este explorador debe instalarse en su dispositivo.
    - **Logotipo**: Cargue un icono que se asociará con la aplicación. Este icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
6. Haga clic en **Siguiente** para mostrar la página **Etiquetas de ámbito**.
7. Si quiere, haga clic en **Seleccionar etiquetas de ámbito** para agregar etiquetas de ámbito para la aplicación. Para más información, consulte [Usar control de acceso basado en rol (RBAC) y etiquetas de ámbito para TI distribuida](~/fundamentals/scope-tags.md).
8. Haga clic en **Siguiente** para abrir la página **Asignaciones**.
9. Seleccione las asignaciones de grupo para la aplicación. Para más información, consulte [Agregar grupos para organizar usuarios y dispositivos](~/fundamentals/groups-add.md). 
10. Elija **Siguiente** para mostrar la página **Revisar y crear**. Revise los valores y la configuración que especificó para la aplicación.
11. Cuando haya terminado, haga clic en **Crear** para agregar la aplicación a Intune.

    Se muestra la hoja **Información general** de la aplicación que creó.

> [!Note]
> Actualmente, la implementación de aplicaciones web de Intune para dispositivos iOS/iPadOS está asociada al perfil de administración y no se puede quitar manualmente. Puede cambiar el tipo de implementación a **Desinstalar** en el portal de Intune; en este momento, puede quitar automáticamente la aplicación web. Sin embargo, si quita la implementación antes de cambiar la intención de asignación de aplicaciones a **Desinstalar**, la aplicación web estará de forma permanente en su sitio en el dispositivo hasta que se cancele la suscripción de este desde Intune.

Los usuarios finales pueden iniciar aplicaciones web directamente desde la aplicación Portal de empresa de Windows seleccionando la aplicación web y eligiendo la opción **Abrir en el explorador**. La dirección URL web publicada se abre directamente en un explorador web. 

## <a name="next-steps"></a>Pasos siguientes

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione. Para obtener ayuda, vea [Asignación de aplicaciones a grupos](apps-deploy.md). 
