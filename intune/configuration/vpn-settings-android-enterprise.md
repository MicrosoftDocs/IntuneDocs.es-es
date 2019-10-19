---
title: 'Uso de la configuración de VPN en Microsoft Intune para dispositivos que ejecutan Android: Azure | Microsoft Docs'
description: Consulte toda la configuración para crear conexiones VPN en dispositivos empresariales Android en Microsoft Intune. Escriba el nombre de la conexión, la dirección IP o el FQDN del servidor VPN, elija cómo se autentican los usuarios y elija los tipos de conexión Citrix, SonicWall, Check Point cápsula y pulse Secure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9f52d3a7c40f27555a07682adf86b0339cef616
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72491935"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>Configuración de dispositivos empresariales de Android para configurar VPN en Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En este artículo se enumeran y describen las distintas configuraciones de conexión de VPN que puede controlar en los dispositivos Android Enterprise. Como parte de la solución de administración de dispositivos móviles (MDM), use esta configuración para crear una conexión VPN, elija cómo se autentica la VPN, seleccione un tipo de servidor VPN, etc.

Como administrador de Intune, puede crear y asignar estas opciones de configuración de VPN a los dispositivos Android Enterprise. 

Para más información sobre los perfiles de VPN en Intune, consulte [perfiles de VPN](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](vpn-settings-configure.md#create-a-device-profile) y elija **Android Enterprise**.

## <a name="device-owner-only"></a>Solo el propietario del dispositivo

- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando busquen en su dispositivo las conexiones VPN disponibles. Por ejemplo, escriba `Contoso VPN`.
- **Dirección IP o FQDN**: indique la dirección IP o el nombre de dominio completo (FQDN) del servidor VPN al que se conectarán los dispositivos. Por ejemplo, especifique **192.168.1.1** o **vpn.contoso.com**.

  - **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son:
  
    - **Certificados**: seleccione un perfil de certificado SCEP o PKCS existente para autenticar la conexión. [Configurar certificados](../protect/certificates-configure.md): se enumeran los pasos para crear un perfil de certificado.
    - **Nombre de usuario y contraseña**: al iniciar sesión en el servidor VPN, se le pedirá a los usuarios finales que escriban su nombre de usuario y una contraseña.

- **Tipo de conexión**: seleccione el tipo de conexión VPN. Las opciones son:

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="work-profile-only"></a>Solo perfil de trabajo

- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando busquen en su dispositivo las conexiones VPN disponibles. Por ejemplo, escriba `Contoso VPN`.
- **Dirección IP o FQDN**: indique la dirección IP o el nombre de dominio completo (FQDN) del servidor VPN al que se conectarán los dispositivos. Por ejemplo, especifique **192.168.1.1** o **vpn.contoso.com**.

  - **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son:
  
    - **Certificados**: seleccione un perfil de certificado SCEP o PKCS existente para autenticar la conexión. [Configurar certificados](../protect/certificates-configure.md): se enumeran los pasos para crear un perfil de certificado.
    - **Nombre de usuario y contraseña**: al iniciar sesión en el servidor VPN, se le pedirá a los usuarios finales que escriban su nombre de usuario y una contraseña.

- **Tipo de conexión**: seleccione el tipo de conexión VPN. Las opciones son:

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede crear perfiles de VPN para dispositivos [Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md), [MacOS](vpn-settings-macos.md), [Windows 10 y versiones posteriores](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md)y [Windows Phone 8,1](vpn-settings-windows-phone-8-1.md) .
