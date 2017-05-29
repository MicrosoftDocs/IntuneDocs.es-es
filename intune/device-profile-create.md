---
title: "Creación de perfiles de configuración de dispositivo de Intune | Versión preliminar de Azure de Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a crear perfiles de configuración de dispositivo de Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: a719b3f53076a55f1e888a9ddf8e98c7074dd25f
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-create-device-configuration-profiles-in-microsoft-intune"></a>Creación de perfiles de configuración de dispositivos en Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]


1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
2. En la hoja que muestra la lista de perfiles, elija **Create Profile** (Crear perfil).
3. En la hoja **Create Profile** (Crear perfil), especifique lo siguiente:
    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción opcional para el perfil.
    - **Plataforma**: seleccione el tipo de plataforma para el perfil que quiere crear.
    - **Tipo de perfil**: seleccione el tipo de perfil que quiere crear. La lista de tipos disponibles variará dependiendo de la plataforma que eligiera.
    - **Configuración**: consulte los siguientes temas para información sobre la configuración de cada tipo de perfil:
        -  [Configuración de características de dispositivo](device-features-configure.md)
        -  [Configuración de restricciones de dispositivo](device-restrictions-configure.md)
        -  [Configuración de correo electrónico](email-settings-configure.md)
        -  [Configuración de VPN](vpn-settings-configure.md)
        -  [Configuración de Wi-Fi](wi-fi-settings-configure.md)
        -  [Configuración de actualización de la edición de Windows 10](edition-upgrade-configure-windows-10.md)
        -  [Configuración de certificados](certificates-configure.md)
        -  [Configuración de Windows Information Protection](windows-information-protection-configure.md)
        -  [Configuración de educación](education-settings-configure.md)
        -  [Configuración personalizada](custom-settings-configure.md)

    ![Creación del perfil de dispositivo](./media/create-device-profile.png)
4. Después de haber configurado las opciones, en la hoja **Create Profile** (Crear perfil), elija **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).


### <a name="next-steps"></a>Pasos siguientes
Para más información sobre cómo asignar perfiles de dispositivo, consulte [Asignación de perfiles de dispositivo con Microsoft Intune](device-profile-assign.md).

