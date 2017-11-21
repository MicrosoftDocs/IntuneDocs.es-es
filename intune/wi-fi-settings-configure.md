---
title: "Cómo configurar opciones de Wi-Fi de Intune"
titleSuffix: Azure portal
description: "Obtenga información sobre cómo usar Intune para configurar conexiones Wi-Fi en los dispositivos que administra\"."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1fadb488-9c6c-43c1-ba23-8c69db633b96
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ae5210cb3da5503c4cf1b85be8b8522fa1cfd6ce
ms.sourcegitcommit: 1df625330f4e8f7f661b5f2b9f16b5590971838d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2017
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>Configuración de Wi-Fi en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use perfiles de Wi-Fi de Microsoft Intune para asignar la configuración de red inalámbrica a los usuarios y los dispositivos de la organización. Al asignar un perfil de Wi-Fi, los usuarios tendrán acceso a su red Wi-Fi corporativa sin tener que configurarla ellos mismos.

Por ejemplo, suponga que instala una nueva red Wi-Fi denominada Contoso Wi-Fi y quiere configurar todos los dispositivos iOS para que se conecten a esta red. Este es el proceso:

1. Cree un perfil de Wi-Fi que contenga la configuración necesaria para conectarse a la red inalámbrica Contoso Wi-Fi.
2. Asigne el perfil a un grupo que contenga todos los usuarios de dispositivos iOS.
3. Los usuarios encuentran la nueva red Contoso Wi-Fi en la lista de redes inalámbricas de su dispositivo y pueden conectarse fácilmente a ella.

Los perfiles de Wi-Fi admiten las siguientes plataformas de dispositivo:

- Android 4 y versiones posteriores
- Android for Work
- iOS 8.0 y versiones posteriores
- macOS (Mac OS X 10.9 y versiones posteriores)

Para dispositivos que ejecutan Windows 8.1, Windows 10 y Windows 10 Mobile, puede importar una configuración de Wi-Fi que se haya exportado anteriormente desde otro dispositivo.

Use la información de este tema para conocer los aspectos básicos de la configuración de un perfil de Wi-Fi. Luego, siga leyendo los temas correspondientes a cada plataforma para saber las peculiaridades de cada dispositivo.

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de Wi-Fi

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de Wi-Fi.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo a la que quiere aplicar la configuración de Wi-Fi. Actualmente, puede elegir una de las siguientes plataformas para la configuración de Wi-Fi:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows 8.1 y versiones posteriores (importe un perfil)**
6. En la lista desplegable de **tipos de perfil**, elija **Wi-Fi básica** o **Wi-Fi empresarial**. Puede usar **Wi-Fi básica** para proporcionar características básicas, como el nombre de red y el SSID. **Wi-Fi empresarial** le permite proporcionar información más avanzada, como el Protocolo de autenticación extensible (EAP) si la red Wi-Fi lo utiliza. **Importación de Wi-Fi** (para Windows 8.1 y Windows 10) le permite importar la configuración de Wi-Fi como archivo XML exportado previamente de otro dispositivo.
7. Dependiendo de la plataforma que eligió, las opciones que pueda configurar serán diferentes. Vaya a uno de los siguientes temas para conocer más detalles sobre la configuración para cada plataforma:
    - [Configuración de Android y Android for Work](wi-fi-settings-android.md)
    - [Configuración de iOS](wi-fi-settings-ios.md)
    - [Configuración de macOS](wi-fi-settings-macos.md)
    - [Configuración de Windows Phone 8.1](wi-fi-settings-import-windows-8-1.md)
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).
