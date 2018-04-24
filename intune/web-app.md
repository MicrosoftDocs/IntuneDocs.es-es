---
title: Agregar aplicaciones web a Microsoft Intune
titleSuffix: ''
description: Descubra cómo agregar aplicaciones web a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 45253e061039198aee4aa49b2bf879a1b9929e35
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Agregar aplicaciones web a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune admite diversos tipos de aplicación, incluidas las aplicaciones web. Una aplicación web es una aplicación cliente-servidor. El servidor proporciona la aplicación web, que incluye la interfaz de usuario, el contenido y la funcionalidad. Además, las plataformas de hospedaje web modernas normalmente ofrecen seguridad, equilibrio de carga y otras ventajas. Una aplicación web se mantiene por separado en la Web. Microsoft Intune se usa para que apunte a este tipo de aplicación. También puede asignar qué grupos de usuarios pueden tener acceso a esta aplicación. 

Antes de poder administrar y asignar aplicaciones a los usuarios, agregue la aplicación a Intune. Intune crea un acceso directo a la aplicación web en la pantalla principal del dispositivo del usuario.

> [!Note]
> Las aplicaciones web no se admiten en dispositivos Android for Work ni macOS.

Complete los pasos siguientes para agregar una aplicación a Intune como un acceso directo a una aplicación en la Web:

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Microsoft Intune**, seleccione **Aplicaciones móviles**.
4. En el panel **Aplicaciones móviles**, seleccione **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**. Aparece el panel **Agregar aplicación**.
6. En el panel **Agregar aplicación**, seleccione el tipo de **Vínculo web** en la lista desplegable **Tipo de aplicación**.
7. Seleccione la opción **Configurar** para mostrar el panel **Información de la aplicación**.
8. En el panel **Información de aplicación**, agregue la información siguiente:
    - **Nombre:** escriba el nombre de la aplicación tal como se mostrará en el Portal de empresa.
    - **Descripción:** escriba una descripción de la aplicación. Esta se muestra a los usuarios finales en el Portal de empresa.
    - **Publicador**: escriba el nombre del publicador de esta aplicación.
    - **Dirección URL de la aplicación**: escriba la dirección URL del sitio web que hospeda la aplicación que quiere asignar.
    - **Categoría (opcional)**: seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Así les resultará más fácil a los usuarios encontrar la aplicación cuando exploren el Portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    - **Se necesita Managed Browser para abrir este vínculo**: al asignar un vínculo a un sitio web o aplicación web para los usuarios, estos pueden abrirlo en el explorador administrado de Intune. Este explorador debe instalarse en su dispositivo.
    - **Logotipo**: cargue un logotipo que esté asociado a la aplicación. Este logotipo es el que se muestra con la aplicación cuando los usuarios examinan el Portal de empresa.
9. Cuando haya terminado, en el panel **Agregar información**, seleccione **Aceptar**.
10. Luego, en el panel **Agregar aplicación**, seleccione **Agregar**.

> [!Note]
> Los usuarios deben agregar el widget de Intune a su pantalla principal para mostrar las aplicaciones web que se han asignado a dispositivos Android.

## <a name="next-steps"></a>Pasos siguientes

- La aplicación que ha creado se muestra en la lista de aplicaciones, donde puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).