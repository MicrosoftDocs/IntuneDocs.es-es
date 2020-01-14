---
title: 'Uso de un PIN para iniciar sesión en dispositivos Windows 10 con Microsoft Intune: Azure | Microsoft Docs'
description: Use Windows Hello para empresas para permitir que los usuarios inicien sesión en dispositivos mediante un PIN, una huella digital, etc. Cree un perfil de configuración de protección de identidad en Intune para dispositivos Windows 10 con esta configuración y asigne el perfil a grupos de usuarios y grupos de dispositivos.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4f5d3a232cab25c60189132732a0ea3f347c74a
ms.sourcegitcommit: 107fef144013b01ed768ca8973373f9cb3f0f7dc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2020
ms.locfileid: "75683806"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>Uso de Windows Hello para empresas en dispositivos Windows 10 que tienen Microsoft Intune

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

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

3. Escriba las propiedades siguientes:

   - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
   - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
   - **Plataforma**: seleccione **Windows 10 y versiones posteriores**. Windows Hello para empresas solo es compatible con dispositivos que ejecutan Windows 10 y versiones posteriores.
   - **Tipo de perfil**: seleccione **Identity Protection**.

4. En el panel *Windows Hello para empresas*, configure las opciones siguientes:

   - **Configurar Windows Hello para empresas**: elija cómo desea configurar Windows Hello para empresas.

     - **Sin configurar** (valor predeterminado): [aprovisiona Windows Hello para empresas](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) en el dispositivo. Al asignar perfiles de protección de identidad solo a los usuarios, el contexto de dispositivo tiene como valor predeterminado **Sin configurar**.

     - **Disabled**: si no quiere usar Windows Hello para empresas, seleccione esta opción. Esta opción deshabilita Windows Hello para empresas para todos los usuarios.

     - **Habilitada**: elija esta opción para [aprovisionar](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) y configurar Windows Hello para empresas en Intune. especifique la configuración que desee definir. Para obtener una lista de todas las configuraciones y saber para qué sirve cada una, consulte [Configuración de dispositivos Windows 10 para habilitar Windows Hello para empresas](identity-protection-windows-settings.md).

   - **Utilice las claves de seguridad para el inicio de sesión**: habilite la clave de seguridad de Windows Hello como credencial de inicio de sesión para todos los equipos del inquilino.

     - **Habilitar**
     - **Sin configurar** (valor predeterminado)

5. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se crea y aparece en la lista de perfiles. Después, [asigne](../configuration/device-profile-assign.md) este perfil a grupos de usuarios y dispositivos para satisfacer sus necesidades.

> [!IMPORTANT]
> Para permitir el aprovisionamiento de varios usuarios a un dispositivo, especifique que la directiva de Windows Hello para empresas se aplique a los dispositivos. Si la directiva se aplica solo a los usuarios, solo se puede aprovisionar un usuario a un dispositivo.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/identity-protection-configure/disable-android-camera.png)

-->

## <a name="next-steps"></a>Pasos siguientes

- Consulte una lista de todas [las configuraciones y lo que hacen](identity-protection-windows-settings.md).
- [Asigne el perfil](../configuration/device-profile-assign.md) y [supervise el estado](../configuration/device-profile-monitor.md).
