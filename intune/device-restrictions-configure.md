---
title: "Configuración de restricciones de dispositivo de Intune"
titleSuffix: Azure portal
description: "Aprenda a usar Intune para configurar los valores y las características en los dispositivos que administra."
keywords: 
author: lleonard-msft
ms.author: alleonar
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
ms.openlocfilehash: b61ad1c0a114c8a66c174fa34c4520e2f6c6244a
ms.sourcegitcommit: af958afce3070a3044aafea490c8afc55301d9df
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Las restricciones de dispositivos permiten controlar una amplia variedad de configuraciones y características que se distribuyen en diversas categorías, como seguridad, explorador, hardware y configuración de uso compartido. Por ejemplo, puede crear un perfil de restricción de dispositivos que impida que los usuarios de dispositivos iOS accedan a la cámara del dispositivo.

Use la información de este tema para conocer los aspectos básicos de la configuración de perfiles de restricciones de dispositivos. Luego, siga leyendo los temas correspondientes a cada plataforma para saber las peculiaridades de cada dispositivo.

Para crear un perfil de dispositivo que contenga la configuración de restricciones de dispositivos:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de restricción de dispositivo.
5. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar configuración personalizada. Actualmente, puede elegir una de las siguientes plataformas para la configuración de restricciones de dispositivos:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable **Tipo de perfil**, elija **Restricciones de dispositivos**. Si quiere crear un perfil de restricciones de dispositivos para dispositivos Windows 10 Team, como Surface Hub, elija **Restricciones de dispositivos (Windows 10 Team)**.
7. Dependiendo de la plataforma que eligió, las opciones que pueda configurar serán diferentes. Vaya a uno de los siguientes temas para conocer más detalles sobre la configuración para cada plataforma:
    - [Configuración de Android](device-restrictions-android.md)
    - [Configuración de iOS](device-restrictions-ios.md)
    - [Configuración de macOS](device-restrictions-macos.md)
    - [Configuración de Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Configuración de Windows 10](device-restrictions-windows-10.md)
    - [Configuración de Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Configuración de Android for Work](device-restrictions-android-for-work.md)
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->