---
title: Creación de perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Agregue o configure un perfil de dispositivo en Microsoft Intune, incluida la selección del tipo de plataforma y la configuración de los ajustes en Azure Portal.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7195b9d2d64c2282f2380624a209ad45220d3a4f
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313945"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Creación de un perfil de dispositivo en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Creación del perfil
1. En [Azure Portal](https://portal.azure.com), seleccione **All services** (Todos los servicios) y busque **Microsoft Intune**.

2. En **Microsoft Intune**, seleccione **Configuración del dispositivo** y **Perfiles**. Luego, seleccione **Crear perfil**.

3. Introduzca las siguientes propiedades:

   - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
   - **Descripción**: escriba una descripción para el perfil (es opcional, pero se recomienda hacerlo).
   - **Plataforma**: seleccione el tipo de plataforma:  

       - **Android**
       - **Perfiles de trabajo Android**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 y versiones posteriores**
       - **Windows 10 y versiones posteriores**

   - **Tipo de perfil**: seleccione el tipo de perfil que quiere crear. La lista dependerá de la plataforma que seleccione.
   - **Configuración**: en los siguientes temas se describen los valores para cada tipo de perfil:

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
