---
title: "Creación de perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs"
description: "Agregue o configure un perfil de dispositivo en Microsoft Intune, incluida la selección del tipo de plataforma y la configuración de los ajustes en Azure Portal"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e4e1febb5f12de038d2ddd543be883f71ef79005
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Creación de un perfil de dispositivo en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Creación del perfil
1. En [Azure Portal](https://portal.azure.com), seleccione **All Services** (Todos los servicios) y busque **Microsoft Intune**.

2. En **Microsoft Intune**, seleccione **Configuración del dispositivo**, **Perfiles** y, luego, **Crear perfil**.

3. Introduzca las siguientes propiedades:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: opcional pero recomendado. Escriba una descripción para el perfil.
    - **Plataforma**: seleccione el tipo de plataforma:  

        - **Android**
        - **Android for Work**
        - **iOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 y versiones posteriores**
        - **Windows 10 y versiones posteriores**

    - **Tipo de perfil**: seleccione el tipo de perfil que quiere crear. La lista dependerá de la plataforma que seleccione.
    - **Configuración**: en los siguientes temas se describen los valores para cada tipo de perfil:

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

    ![Especificación de la configuración para crear un perfil de dispositivo](./media/create-device-profile.png)

4. Seleccione **Crear** cuando termine.

Se creará el perfil y aparecerá en la lista. Para asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).


## <a name="next-steps"></a>Pasos siguientes
Para asignar perfiles de dispositivo, consulte [Asignación de perfiles de dispositivo de Microsoft Intune](device-profile-assign.md).
