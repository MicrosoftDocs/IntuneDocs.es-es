---
title: "Configuración de restricciones de dispositivos en Microsoft Intune"
titleSuffix: 
description: "Aprenda a usar Microsoft Intune para configurar los valores y las características en los dispositivos que administra."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 62c12cde5ca128a26b10e0e4516e0bbf7e0f0bbb
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Las restricciones de dispositivos permiten controlar una amplia gran de opciones y características que se distribuyen en diversas categorías, por ejemplo:
- Seguridad
- Explorador
- Hardware
- Configuración del uso compartido de los datos

Por ejemplo, puede crear un perfil de restricción de dispositivos que impida que los usuarios de dispositivos iOS accedan a la cámara del dispositivo.

Descubra los conceptos básicos sobre los perfiles de restricción de dispositivos y lea los artículos de las distintas plataformas para obtener información sobre aspectos específicos de los dispositivos.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de restricciones de dispositivos

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services (Todos los servicios)** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la página **Intune**, elija **Configuración del dispositivo**.
2. En la página **Configuración del dispositivo**, en la sección **Administrar**, elija **Perfiles**.
3. En la página **Perfiles**, elija **Crear perfil**.
4. En la página **Crear perfil**, escriba un **Nombre** y una **Descripción** para el perfil de restricción de dispositivos.
5. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar configuración personalizada. Actualmente, puede elegir una de las siguientes plataformas para la configuración de restricciones de dispositivos:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable **Tipo de perfil**, elija **Restricciones de dispositivos**. Si quiere crear un perfil de restricciones de dispositivos para dispositivos Windows 10 Team, como Surface Hub, elija **Restricciones de dispositivos (Windows 10 Team)**.
7. Dependiendo de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. Vaya a uno de los siguientes temas para conocer más detalles sobre la configuración para cada plataforma:
    - [Configuración de Android](device-restrictions-android.md)
    - [Configuración de iOS](device-restrictions-ios.md)
    - [Configuración de macOS](device-restrictions-macos.md)
    - [Configuración de Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Configuración de Windows 10](device-restrictions-windows-10.md)
    - [Configuración de Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Configuración de Windows Holographic for Business](device-restrictions-windows-holographic.md)
    - [Configuración de Android for Work](device-restrictions-android-for-work.md)
8. Cuando haya terminado, vuelva a la página **Crear perfil** y haga clic en **Crear**.

Se creará el perfil y aparecerá en la página con la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->