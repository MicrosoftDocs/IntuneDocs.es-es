---
title: 'Restricción de las características de los dispositivos mediante directivas en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue un perfil de dispositivo para restringir características en dispositivos Android, macOS, iOS, iPadOS, Windows Phone y Windows 10 en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 61a8815bdbb0121d727c80dda0421922e0531cf7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724053"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Configurar restricciones de dispositivos en Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune incluye directivas de restricción de dispositivos que ayudan a los administradores a controlar dispositivos Android, iOS, macOS y Windows. Estas restricciones permiten controlar una amplia variedad de configuraciones y características para proteger los recursos de la organización. Por ejemplo, los administradores pueden:

- Permitir o bloquear la cámara del dispositivo.
- Controlar el acceso a Google Play, a las tiendas de aplicaciones, a la visualización de documentos y a juegos.
- Bloquear aplicaciones integradas o crear una lista de aplicaciones permitidas o prohibidas.
- Permitir o impedir la copia de seguridad de archivos en la nube y en cuentas de almacenamiento.
- Establecer una longitud mínima de contraseña y bloquear las contraseñas poco seguras.

Estas características están disponibles en Intune y el administrador puede configurarlas. Intune usa "perfiles de configuración" para crear y personalizar estas configuraciones para las necesidades de su organización. Después de agregar estas características en un perfil, puede insertar o implementar el perfil en dispositivos de su organización.

En este artículo se muestra cómo crear un perfil de restricciones de dispositivos. También puede ver todas las opciones de configuración disponibles para las distintas plataformas.

## <a name="create-the-profile"></a>Creación del perfil

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para la directiva. Asígnele un nombre a las directivas para que pueda identificarlas de manera sencilla más adelante. Por ejemplo, un nombre de directiva válido es **iOS: Bloquear la cámara en los dispositivos**.
    - **Descripción**: escriba una descripción para la directiva. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione la plataforma de los dispositivos. Las opciones son:  

        - **Android**
        - **Android Enterprise**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 y versiones posteriores**
        - **Windows 10 y versiones posteriores**

    - **Tipo de perfil**: Seleccione **Restricciones de dispositivos**.

        Para crear un perfil de restricciones de dispositivos para dispositivos Windows 10 Team, como Surface Hub, elija **Restricciones de dispositivos (Windows 10 Team)** .

4. Dependiendo de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. Elija la plataforma para la configuración detallada:

    - [Configuración de Android](../device-restrictions-android.md)
    - [Configuración de Android Enterprise](../device-restrictions-android-for-work.md)
    - [Configuración de iOS/iPadOS](device-restrictions-ios.md)
    - [Configuración de macOS](device-restrictions-macos.md)
    - [Configuración de Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Configuración de Windows 10](device-restrictions-windows-10.md)
    - [Configuración de Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Configuración de Windows Holographic for Business](device-restrictions-windows-holographic.md)

5. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se crea y se muestra en la lista de perfiles.

## <a name="next-steps"></a>Pasos siguientes

Una vez creado el perfil, está listo para asignarlo. Después, [asigne el perfil](../device-profile-assign.md) y [supervise el estado](../device-profile-monitor.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->
