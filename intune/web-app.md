---
title: Agregar aplicaciones web a Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo agregar aplicaciones web (aplicaciones cliente-servidor) a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4f0c5d79c17c3cc2ada275337d266c134eed7e91
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642547"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Agregar aplicaciones web a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune admite diversos tipos de aplicación, incluidas aplicaciones web. Una aplicación web es una aplicación cliente-servidor. El servidor proporciona la aplicación web, que incluye la interfaz de usuario, el contenido y la funcionalidad. Además, las plataformas de hospedaje web modernas normalmente ofrecen seguridad, equilibrio de carga y otras ventajas. Una aplicación web se mantiene por separado en Internet. Microsoft Intune se usa para que apunte a este tipo de aplicación. También puede asignar los grupos de usuarios que pueden acceder a esta aplicación. 

Antes de poder administrar y asignar aplicaciones a los usuarios, agregue la aplicación a Intune. Intune crea un acceso directo a la aplicación web en la pantalla principal del dispositivo del usuario.

> [!Note]
> Las aplicaciones web no se admiten en dispositivos de perfil de trabajo Android ni macOS.

## <a name="add-a-web-app-to-intune"></a>Agregar una aplicación web a Intune
Para agregar una aplicación a Intune como acceso directo a una aplicación de Internet, haga lo siguiente:

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**.  
    Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. En el panel de la carga de trabajo **Aplicaciones cliente**, en **Administrar**, seleccione **Aplicaciones**.
5. En el panel **Aplicaciones**, seleccione **Agregar**.
6. En el panel **Agregar aplicación**, en la lista desplegable **Tipo de aplicación**, seleccione el tipo **Vínculo web**.
7. Seleccione **Configurar**.
8. En el panel **Información de aplicación**, agregue la información siguiente:
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
9. Seleccione **Aceptar**.
10. Luego, en el panel **Agregar aplicación**, seleccione **Agregar**.

> [!Note]
> Los usuarios deben agregar el widget de Intune a su pantalla de inicio para mostrar las aplicaciones web asignadas a dispositivos Android.
>
> Actualmente, la implementación de aplicaciones web de Intune para dispositivos iOS está asociada al perfil de administración y no se puede quitar manualmente. Puede cambiar el tipo de implementación a **Desinstalar** en el portal de Intune; en este momento, puede quitar automáticamente la aplicación web. Sin embargo, si quita la implementación antes de cambiar la intención de asignación de aplicaciones a **Desinstalar**, la aplicación web estará de forma permanente en su sitio en el dispositivo hasta que se cancele la suscripción de este desde Intune.

## <a name="next-steps"></a>Pasos siguientes

La aplicación que ha creado aparece en la lista de aplicaciones, donde puede asignarla a los grupos que seleccione. Para obtener ayuda, vea [Asignación de aplicaciones a grupos](apps-deploy.md). 
