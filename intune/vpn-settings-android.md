---
title: 'Uso de la configuración de VPN en Microsoft Intune para dispositivos que ejecutan Android: Azure | Microsoft Docs'
description: Vea todas las opciones para crear conexiones VPN en dispositivos Android en Microsoft Intune. Escriba el nombre de la conexión, la dirección IP o el FQDN del servidor VPN, elija cómo se autentican los usuarios y elija los tipos de conexión Citrix, SonicWall, Check Point cápsula y pulse Secure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36806769e3b4c2c726038c23edf22cb006819d8c
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "71302805"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Configuración de dispositivos Android para configurar VPN en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo se enumeran y describen las distintas configuraciones de conexión de VPN que puede controlar en los dispositivos Android y Android Enterprise. Como parte de la solución de administración de dispositivos móviles (MDM), use esta configuración para crear una conexión VPN, elija cómo se autentica la VPN, seleccione un tipo de servidor VPN, etc.

Como administrador de Intune, puede crear y asignar estas opciones de configuración de VPN a los dispositivos Android. 

Para más información sobre los perfiles de VPN en Intune, consulte [perfiles de VPN](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](vpn-settings-configure.md#create-a-device-profile) y elija **Android**.

## <a name="base-vpn"></a>VPN de base

- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando busquen en su dispositivo las conexiones VPN disponibles. Por ejemplo, escriba `Contoso VPN`.
- **Dirección IP o FQDN**: indique la dirección IP o el nombre de dominio completo (FQDN) del servidor VPN al que se conectarán los dispositivos. Por ejemplo, especifique **192.168.1.1** o **vpn.contoso.com**.

  - **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son:

    - **Certificados**: seleccione un perfil de certificado SCEP o PKCS existente para autenticar la conexión. [Configurar certificados](certificates-configure.md): se enumeran los pasos para crear un perfil de certificado.
    - **Nombre de usuario y contraseña**: al iniciar sesión en el servidor VPN, se le pedirá a los usuarios finales que escriban su nombre de usuario y una contraseña.

- **Tipo de conexión**: seleccione el tipo de conexión VPN. Las opciones son:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **Huella digital** (solo Check Point Capsule VPN): escriba una cadena (por ejemplo **Código de huella digital de Contoso**) para comprobar que se puede confiar en el servidor VPN. Se envía una huella digital al cliente para que el cliente sepa confiar en cualquier servidor que tenga la misma huella digital. Si el dispositivo no tiene la huella digital, le pide al usuario que confíe en el servidor VPN mientras muestra la huella digital. El usuario comprueba la huella digital manualmente y opta por confiar para conectarse.
- **Especifique pares clave-valor para los atributos de VPN de Citrix** (solo Citrix): escriba los pares de clave y valor, proporcionados por Citrix. Estos valores configuran las propiedades de la conexión VPN. 

  También puede **importar** un archivo de valores separados por comas (. csv) con pares de clave y valor. Asegúrese de revisar las propiedades **mis datos tiene encabezados** y **claves** .

  Después de agregar los pares de clave y valor, use **exportar** para realizar una copia de seguridad de los datos en un archivo. csv.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede crear perfiles de VPN para dispositivos [Android Enterprise](vpn-settings-android-enterprise.md), [iOS](vpn-settings-ios.md), [MacOS](vpn-settings-macos.md), [Windows 10 y versiones posteriores](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md)y [Windows Phone 8,1](vpn-settings-windows-phone-8-1.md) .
