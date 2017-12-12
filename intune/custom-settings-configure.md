---
title: "Configuración personalizada de dispositivos de Intune"
titleSuffix: Azure portal
description: Aprenda a usar Intune para configurar valores personalizados en los dispositivos que administra.
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7568a74256688271794b6baa752a23e24cf8d67
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="how-to-configure-custom-device-settings-in-microsoft-intune"></a>Configuración personalizada de dispositivos en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="when-to-use-custom-settings"></a>Cuándo usar la configuración personalizada

La configuración personalizada del dispositivo puede ser útil cuando Intune no lleva integradas las opciones que quiere configurar en el dispositivo y estas se encuentran disponibles en otros perfiles.
La configuración personalizada se puede realizar de forma diferente en cada plataforma. Por ejemplo, con dispositivos Android y Windows, puede especificar valores de identificador uniforme de recursos de Open Mobile Alliance (OMA-URI) para controlar características en los dispositivos. Para dispositivos Apple, puede importar un archivo creado con [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

Use la información de este tema para conocer los aspectos básicos de la configuración de perfiles con valores personalizados. Luego, siga leyendo los temas correspondientes a cada plataforma para saber las peculiaridades de cada dispositivo.

## <a name="create-a-device-profile-containing-custom-settings"></a>Creación de un perfil de dispositivo que contiene la configuración personalizada

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil personalizado.
5. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar configuración personalizada. Actualmente, puede elegir una de las siguientes plataformas para la configuración de dispositivo personalizada:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **tipos de perfil**, elija **Personalizado**.
7. Dependiendo de la plataforma que eligió, las opciones que pueda configurar serán diferentes. Vaya a uno de los siguientes temas para conocer más detalles sobre la configuración para cada plataforma:
    - [Configuración de Android](custom-settings-android.md)
    - [Configuración de iOS](custom-settings-ios.md)
    - [Configuración de macOS](custom-settings-macos.md)
    - [Configuración de Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
    - [Configuración de Windows 10](custom-settings-windows-10.md)
    - [Configuración de Android for Work](custom-settings-android-for-work.md)
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).
