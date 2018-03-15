---
title: "Configuración de características de dispositivos de Microsoft Intune"
titleSuffix: 
description: "Aprenda a usar Microsoft Intune para configurar características en los dispositivos que administra."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6cd646976deb1599c4cbc9154b6f2a487029dd79
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
#<a name="configure-device-feature-settings-in-microsoft-intune"></a>Configuración de características de dispositivos en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Las características del dispositivo permiten controlar características de dispositivos iOS y macOS, como configuraciones de AirPrint, notificaciones y dispositivos compartidos.

Use la información de este artículo para conocer los aspectos básicos de la configuración de perfiles de características de dispositivos. Luego, lea los artículos adicionales correspondientes a cada plataforma para descubrir las peculiaridades de cada dispositivo.

## <a name="create-a-device-profile-containing-device-feature-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de características de dispositivos

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services (Todos los servicios)** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la página **Intune**, elija **Configuración del dispositivo**.
2. En la página **Configuración del dispositivo**, en la sección **Administrar**, elija **Perfiles**.
3. En la página de perfiles, elija **Crear perfil**.
4. En la página **Crear perfil**, escriba un **Nombre** y una **Descripción** para el perfil de características de dispositivos.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo a la que quiere aplicar la configuración. Actualmente, puede elegir una de las siguientes plataformas para las características del dispositivo:
    - **iOS**
    - **macOS**
6. En la lista desplegable **Tipo de perfil**, elija **Características del dispositivo**. 
7. Dependiendo de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. Vaya a uno de los siguientes artículos para conocer más detalles sobre la configuración para cada plataforma:
    - [Configuración de AirPrint para iOS y MacOS](air-print-settings-ios-macos.md)
    - [Configuración de AirPlay para iOS](airplay-settings-ios.md)
    - [Configuración de diseño de pantalla principal para iOS](home-screen-settings-ios.md)
    - [Configuración de notificaciones de aplicación para iOS](app-notification-settings-ios.md)
    - [Valores de configuración de dispositivo compartido para iOS](shared-device-settings-ios.md)
    - [Configuración del inicio de sesión único de Intune para dispositivos iOS](sso-ios.md)
    - [Configuración de filtro de contenido web para iOS](web-content-filter-settings-ios.md)

8. Cuando haya terminado, seleccione **Aceptar**, vuelva a la página **Crear perfil** y elija **Crear**.

Se creará el perfil y aparecerá en la página con la lista de perfiles.
## <a name="next-steps"></a>Pasos siguientes

Si quiere asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).



