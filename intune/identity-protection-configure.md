---
title: 'Uso de un PIN para iniciar sesión en dispositivos Windows 10 con Microsoft Intune: Azure | Microsoft Docs'
description: Use Windows Hello para empresas para permitir que los usuarios inicien sesión en dispositivos mediante un PIN, una huella digital, etc. Cree un perfil de configuración de protección de identidad en Intune para dispositivos Windows 10 con esta configuración y asigne el perfil a grupos de usuarios y grupos de dispositivos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 843806681fcee4ddec175207c2c49d6db95e0f0d
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831396"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>Uso de Windows Hello para empresas en dispositivos Windows 10 que tienen Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows Hello para empresas es un método para iniciar sesión en dispositivos Windows mediante la sustitución de contraseñas, tarjetas inteligentes y tarjetas inteligentes virtuales. Intune incluye configuraciones integradas para que los administradores puedan configurar y usar Windows Hello para empresas. Por ejemplo, puede usar estas configuraciones para:

- Habilitar Windows Hello para empresas para los dispositivos y usuarios
- Establecer requisitos de PIN de dispositivo, incluida una longitud de PIN mínima o máxima
- Permitir gestos, como una huella digital, que los usuarios pueden usar (o no) para iniciar sesión en dispositivos

Esta característica se aplica a los dispositivos que ejecutan:

- Windows 10 y versiones posteriores
- Windows 10 Mobile
- Windows Holographic for Business

Intune usa "perfiles de configuración" para crear y personalizar estas configuraciones para las necesidades de su organización. Después de agregar estas características a un perfil, inserte o implemente estas configuraciones en grupos de usuarios o dispositivos de la organización.

En este artículo se muestra cómo crear un perfil de configuración de dispositivo. Para obtener una lista de todas las configuraciones, y lo que hacen, consulte [Windows 10 device settings to enable Windows Hello for Business](identity-protection-windows-settings.md) (Configuración de dispositivos Windows 10 para habilitar Windows Hello para empresas).

## <a name="create-the-device-profile"></a>Creación del perfil de dispositivo

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione **Windows 10 y versiones posteriores**. Windows Hello para empresas solo es compatible con dispositivos que ejecutan Windows 10 y versiones posteriores.
    - **Tipo de perfil**: seleccione **Identity Protection**.
    - **Configurar Windows Hello para empresas**: elija cómo desea configurar Windows Hello para empresas. Las opciones son:

        - **No configurado**: [aprovisiona Windows Hello para empresas](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) en el dispositivo. Al asignar perfiles de protección de identidad solo a los usuarios, el contexto de dispositivo tiene como valor predeterminado **Sin configurar**.
        - **Deshabilitado**: si no quiere usar Windows Hello para empresas, seleccione esta opción. Esta opción deshabilita Windows Hello para empresas para todos los usuarios.
        - **Habilitada**: elija esta opción para [aprovisionar]((https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning)) y configurar Windows Hello para empresas en Intune. Especifique la configuración que desee definir. Para una lista de todas las configuraciones, y lo que hacen, consulte:

            - [Configuración de dispositivos Windows 10 para habilitar Windows Hello para empresas](identity-protection-windows-settings.md) (Configuración de dispositivos Windows 10 para habilitar Windows Hello para empresas).

4. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se crea y aparece en la lista de perfiles. A continuación, [asigne](device-profile-assign.md) este perfil a grupos.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->

## <a name="next-steps"></a>Pasos siguientes

- Consulte una lista de todas [las configuraciones y lo que hacen](identity-protection-windows-settings.md).
- [Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).