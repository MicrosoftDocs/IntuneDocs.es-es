---
title: "Creación de perfiles de configuración de dispositivos de Intune"
titleSuffix: Intune on Azure
description: "Aprenda a crear perfiles de configuración de dispositivos de Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6df6813667241d3ad5f8768585f2e1a34f0fe6e3
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-create-device-configuration-profiles-in-microsoft-intune"></a>Creación de perfiles de configuración de dispositivos en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
2. En la hoja que muestra la lista de perfiles, elija **Create Profile** (Crear perfil).
3. En la hoja **Crear perfil**, especifique los siguientes elementos:
    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción opcional para el perfil.
    - **Plataforma**: seleccione el tipo de plataforma para el perfil que quiere crear.
    - **Tipo de perfil**: seleccione el tipo de perfil que quiere crear. La lista de tipos disponibles variará en función de la plataforma que haya elegido.
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
