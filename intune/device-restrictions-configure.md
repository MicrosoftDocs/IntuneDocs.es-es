---
title: Configuración de restricciones de dispositivos en Microsoft Intune - Azure | Microsoft Docs
description: Agregue un perfil de dispositivo para restringir características en dispositivos Android, macOS, iOS, Windows Phone y Windows 10 en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e040743975a482c702e0c0168a4fd6315a2dac8
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61505750"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Configurar restricciones de dispositivos en Microsoft Intune

Las restricciones de dispositivos permiten controlar una amplia gran de opciones y características que se distribuyen en diversas categorías, por ejemplo:
- Seguridad
- Explorador
- Hardware
- Configuración del uso compartido de los datos

Por ejemplo, puede crear un perfil de restricción de dispositivos que impida que los usuarios de dispositivos iOS accedan a la cámara del dispositivo.

Descubra los conceptos básicos sobre los perfiles de restricción de dispositivos y lea los artículos de las distintas plataformas para obtener información sobre aspectos específicos de los dispositivos.

## <a name="create-the-profile"></a>Creación del perfil

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los dispositivos** > filtre por **Intune** > seleccione **Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba un **nombre** y una **descripción** para el perfil de restricción de dispositivos.
4. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar configuración personalizada. Actualmente, puede elegir una de las siguientes plataformas para la configuración de restricciones de dispositivos:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**

5. En la lista desplegable **Tipo de perfil**, elija **Restricciones de dispositivos**. Para crear un perfil de restricciones de dispositivos para dispositivos Windows 10 Team, como Surface Hub, elija **Restricciones de dispositivos (Windows 10 Team)**.
6. Dependiendo de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. Elija la plataforma para la configuración detallada:

    - [Configuración de Android](device-restrictions-android.md)
    - [Configuración de Android Enterprise](device-restrictions-android-for-work.md)
    - [Configuración de iOS](device-restrictions-ios.md)
    - [Configuración de macOS](device-restrictions-macos.md)
    - [Configuración de Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Configuración de Windows 10](device-restrictions-windows-10.md)
    - [Configuración de Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Configuración de Windows Holographic for Business](device-restrictions-windows-holographic.md)

7. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se crea y se muestra en la lista de perfiles.

## <a name="next-steps"></a>Pasos siguientes

Una vez creado el perfil, está listo para asignarlo. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
