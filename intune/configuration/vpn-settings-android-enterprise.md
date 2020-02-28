---
title: 'Uso de la configuración de VPN en Microsoft Intune para dispositivos que ejecutan Android: Azure | Microsoft Docs'
description: Consulte toda la configuración para crear conexiones VPN en dispositivos Android Enterprise en Microsoft Intune. Escriba el nombre de la conexión, la dirección IP o el FQDN del servidor VPN, elija cómo se autentican los usuarios y elija los tipos de conexión Citrix, SonicWall, Check Point Capsule y Pulse Secure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81300651355e52f438ea2a314eeb1d0d48e3fcbc
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510871"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>Configuración de dispositivos Android Enterprise para configurar VPN en Intune

En este artículo se enumeran y describen las distintas configuraciones de conexión de VPN que puede controlar en los dispositivos Android Enterprise. Como parte de la solución de administración de dispositivos móviles (MDM), use esta configuración para crear una conexión VPN, elegir cómo se autentica dicha conexión, seleccionar un tipo de servidor VPN, etc.

Como administrador de Intune, puede crear y asignar estas opciones de configuración de VPN a los dispositivos Android Enterprise. 

Para más información sobre los perfiles de VPN en Intune, consulte [Perfiles de VPN](vpn-settings-configure.md).

> [!NOTE]
> Para configurar una VPN AlwaysOn, debe crear un perfil de VPN y también un perfil de [restricciones de dispositivos](device-restrictions-android-for-work.md#connectivity) con los valores de VPN AlwaysOn configurados.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](vpn-settings-configure.md#create-a-device-profile) y elija **Android Enterprise**.

## <a name="device-owner-only"></a>Solo el propietario del dispositivo

- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando busquen en su dispositivo las conexiones VPN disponibles. Por ejemplo, escriba `Contoso VPN`.
- **Dirección IP o FQDN**: indique la dirección IP o el nombre de dominio completo (FQDN) del servidor VPN al que se conectarán los dispositivos. Por ejemplo, especifique **192.168.1.1** o **vpn.contoso.com**.

  - **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son:
  
    - **Certificados**: seleccione un perfil de certificado SCEP o PKCS existente para autenticar la conexión. [Configurar certificados](../protect/certificates-configure.md): se enumeran los pasos para crear un perfil de certificado.
    - **Nombre de usuario y contraseña**: al iniciar sesión en el servidor VPN, se pide a los usuarios finales que escriban su nombre de usuario y contraseña.

- **Tipo de conexión**: seleccione el tipo de conexión VPN. Las opciones son:

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="work-profile-only"></a>Solo perfil de trabajo

- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando busquen en su dispositivo las conexiones VPN disponibles. Por ejemplo, escriba `Contoso VPN`.
- **Dirección IP o FQDN**: indique la dirección IP o el nombre de dominio completo (FQDN) del servidor VPN al que se conectarán los dispositivos. Por ejemplo, especifique **192.168.1.1** o **vpn.contoso.com**.

  - **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son:
  
    - **Certificados**: seleccione un perfil de certificado SCEP o PKCS existente para autenticar la conexión. [Configurar certificados](../protect/certificates-configure.md): se enumeran los pasos para crear un perfil de certificado.
    - **Nombre de usuario y contraseña**: al iniciar sesión en el servidor VPN, se pide a los usuarios finales que escriban su nombre de usuario y contraseña.

- **Tipo de conexión**: seleccione el tipo de conexión VPN. Las opciones son:

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede crear perfiles de VPN para dispositivos [Android](vpn-settings-android.md), [iOS/iPadOS](vpn-settings-ios.md), [macOS](vpn-settings-macos.md), [Windows 10 y posterior](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md) y [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md).
