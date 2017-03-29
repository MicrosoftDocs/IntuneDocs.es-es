---
title: "Configuración de restricciones de dispositivo de Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a usar Intune para configurar valores y características en los dispositivos que administra."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: b593b2ddd756bc5bf7700eca4f2544b87008a8ab
ms.lasthandoff: 03/17/2017


---

# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Las restricciones de dispositivos permiten controlar una amplia variedad de configuraciones y características que se distribuyen en diversas categorías, como seguridad, explorador, hardware y configuración de uso compartido. Por ejemplo, puede crear un perfil de restricción de dispositivos que impida que los usuarios de dispositivos iOS accedan a la cámara del dispositivo.

Use la información de este tema para conocer los aspectos básicos de la configuración de perfiles de restricciones de dispositivos. Luego, siga leyendo los temas correspondientes a cada plataforma para saber las peculiaridades de cada dispositivo.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de restricciones de dispositivos

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
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
    - [Configuración de Android](device-restrictions-for-android.md)
    - [Configuración de iOS](device-restrictions-for-ios.md)
    - [Configuración de macOS](device-restrictions-for-macos.md)
    - [Configuración de Windows Phone 8.1](device-restrictions-for-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-for-windows-8-1.md)
    - [Configuración de Windows 10](device-restrictions-for-windows-10.md)
    - [Configuración de Windows 10 Team](device-restrictions-for-windows-10-team.md)
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](how-to-assign-device-profiles.md).

## <a name="example-of-device-restriction-settings"></a>Ejemplo de configuración de restricciones de dispositivos

En este ejemplo de alto nivel, creará una directiva de restricción de dispositivo que bloquee el uso de la aplicación de cámara integrada en dispositivos Android.

![Deshabilitación de la cámara en dispositivos Android](./media/disable-android-camera.png)


