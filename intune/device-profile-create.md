---
title: Creación de perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Agregue o configure un perfil de dispositivo en Microsoft Intune, incluida la selección del tipo de plataforma y la configuración de los ajustes en Azure Portal.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aaa8692a17e7e78378905e79b4046727d91c7c92
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238887"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Creación de un perfil de dispositivo en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Creación del perfil

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Intune**.

2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.

3. Escriba las propiedades siguientes:

   - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
   - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
   - **Plataforma**: seleccione el tipo de plataforma:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 y versiones posteriores**
       - **Windows 10 y versiones posteriores**

   - **Tipo de perfil**: seleccione el tipo que quiere crear. La lista dependerá de la plataforma que seleccione.
   - **Configuración**: En los siguientes temas se describen los valores de cada tipo de perfil:

       -  [Características del dispositivo](device-features-configure.md)
       -  [Restricciones de dispositivos](device-restrictions-configure.md)
       -  [Endpoint Protection](endpoint-protection-configure.md)
       -  [Protección de identidad](identity-protection-configure.md)  
       -  [Quiosco](kiosk-settings.md)
       -  [Correo electrónico](email-settings-configure.md)
       -  [VPN](vpn-settings-configure.md)
       -  [Wi-Fi](wi-fi-settings-configure.md)
       -  [Windows 10 Education](education-settings-configure.md) y [iOS](wi-fi-settings-ios.md)
       -  [Actualización de edición de Windows 10](edition-upgrade-configure-windows-10.md)
       -  [Directivas de actualización de iOS](software-updates-ios.md)
       -  [Certificados](certificates-configure.md)
       -  [Windows Information Protection](windows-information-protection-configure.md)
       -  [Personalizado](custom-settings-configure.md)

     ![Captura de pantalla de Crear perfil](./media/create-device-profile.png)

4. Seleccione **Crear** cuando termine.

Se creará el perfil y aparecerá en la lista.

## <a name="next-steps"></a>Pasos siguientes
[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
