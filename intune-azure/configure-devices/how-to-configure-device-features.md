---
title: "Configuración de características de dispositivos de Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a usar Intune para configurar características en los dispositivos que administra."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: e1bc6388ec1927693bac676a20a18935cdbf894e
ms.lasthandoff: 04/19/2017


---

# <a name="how-to-configure-device-feature-settings-in-microsoft-intune"></a>Configuración de características de dispositivos en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Las restricciones del dispositivo permiten controlar características en dispositivos iOS y macOS, como configuraciones de AirPrint, notificaciones y dispositivos compartidos.

Use la información de este tema para conocer los aspectos básicos de la configuración de perfiles de características de dispositivos. Luego, siga leyendo los temas correspondientes a cada plataforma para saber las peculiaridades de cada dispositivo.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de restricciones de dispositivos

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Crear perfil	**, escriba un **Nombre** y una **Descripción** para el perfil de características del dispositivo.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo a la que quiere aplicar la configuración. Actualmente, puede elegir una de las siguientes plataformas para las características del dispositivo:
    - **iOS**
    - **macOS**
6. En la lista desplegable **Tipo de perfil**, elija **Características de dispositivos**. 
7. Dependiendo de la plataforma que eligió, las opciones que pueda configurar serán diferentes. Vaya a uno de los siguientes temas para conocer más detalles sobre la configuración para cada plataforma:
    - [Configuración de AirPrint para iOS y MacOS](air-print-settings-for-ios-and-macos.md)
     - [Configuración de AirPlay para iOS](airplay-settings-for-ios-devices.md)
    - [Configuración de diseño de pantalla principal para iOS](home-screen-settings-for-ios.md)
    - [Configuración de notificaciones de aplicación para iOS](app-notification-settings-for-ios.md)
    - [Valores de configuración de dispositivo compartido para iOS](shared-device-settings-for-ios.md)
    - [Configuración de filtro de contenido web para iOS](web-content-filter-settings-for-ios.md)

8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](how-to-assign-device-profiles.md).




