---
title: "Configuración de características de dispositivos con Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune en Azure: Aprenda a usar Intune para configurar características en dispositivos que administre."
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
ms.translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: fddd4963ceea09b37ad4d8c739f437dbcf3b053e
ms.contentlocale: es-es
ms.lasthandoff: 04/26/2017


---

# <a name="how-to-configure-device-feature-settings-in-microsoft-intune"></a>Configuración de características de dispositivos en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Las restricciones de dispositivo le permiten controlar características en dispositivos iOS y macOS como AirPrint, notificaciones y configuraciones de dispositivo compartidas.

Utilice la información de este tema para aprender los conceptos básicos sobre la configuración de perfiles de características de dispositivos y, luego, lea más temas para cada plataforma para obtener información sobre aspectos específicos del dispositivo.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creación de un perfil de dispositivo que contiene la configuración de restricción de dispositivo

1. Inicie sesión en Azure Portal.
2. Elija **Más servicios** > **Otros** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Crear perfil**.
4. En la hoja **Crear perfil**, escriba la información pertinente en **Nombre** y **Descripción** para el perfil de características del dispositivo.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo a la que desea aplicar la configuración. Actualmente, puede elegir una de las siguientes plataformas para características del dispositivo:
    - **iOS**
    - **macOS**
6. En la lista desplegable **Tipo de perfil**, elija **Características del dispositivo**. 
7. Dependiendo de la plataforma elegida, las opciones que puede configurar serán diferentes. Vaya a uno de los siguientes temas para la configuración detallada para cada plataforma:
    - [Configuración de AirPrint para iOS y MacOS](air-print-settings-for-ios-and-macos.md)
     - [Configuración de AirPlay para iOS](airplay-settings-for-ios-devices.md)
    - [Configuración del diseño de pantalla principal para iOS](home-screen-settings-for-ios.md)
    - [Configuración de notificaciones de aplicación para iOS](app-notification-settings-for-ios.md)
    - [Opciones de configuración de dispositivos compartidos para iOS](shared-device-settings-for-ios.md)

8. Cuando haya terminado, vuelva a la hoja **Crear perfil** y presione **Crear**.

El perfil se creará y aparecerá en la hoja de lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo de Microsoft Intune](how-to-assign-device-profiles.md).




