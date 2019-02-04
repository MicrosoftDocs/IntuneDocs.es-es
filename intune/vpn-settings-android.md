---
title: 'Configuración de VPN en Microsoft Intune para dispositivos que ejecutan Android: Azure | Microsoft Docs'
description: Al crear un perfil de configuración de VPN para dispositivos Android y Android for Work, escriba el nombre de conexión, la dirección IP o FQDN del servidor VPN, elija cómo se autentican los usuarios con el servidor VPN y, después, elija los tipos de conexión Citrix, SonicWall, Check Point Capsule, Pulse Secure y Microsoft Edge.
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
ms.openlocfilehash: 5e442ae550d138d532f7a2d8e829c623d09f240a
ms.sourcegitcommit: 9739a9aab032ebb2c4b52ccfb454a9e0f78b2ee4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54751168"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>Configuración de VPN en Intune para dispositivos que ejecutan Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se muestra la configuración de Intune que puede usar para configurar conexiones VPN en dispositivos que ejecutan Android.

Puede establecer la configuración de VPN de las siguientes plataformas:

- [Android](#android-vpn-settings)
- [Android Enterprise](#android-enterprise-vpn-settings)

Según la configuración que elija, no se podrán configurar todos los valores que se muestran a continuación.

## <a name="android-vpn-settings"></a>Configuración de VPN de Android

- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando busquen en su dispositivo las conexiones VPN disponibles.
- **Dirección IP o FQDN**: indique la dirección IP o el nombre de dominio completo (FQDN) del servidor VPN al que se conectarán los dispositivos. Por ejemplo, especifique **192.168.1.1** o **vpn.contoso.com**.

  - **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son:

    - **Certificados**: seleccione un perfil de certificado SCEP o PKCS existente para autenticar la conexión. [Configurar certificados](certificates-configure.md): se enumeran los pasos para crear un perfil de certificado.
    - **Nombre de usuario y contraseña**: al iniciar sesión en el servidor VPN, se pedirá a los usuarios finales que escriban un nombre de usuario y una contraseña.

- **Tipo de conexión**: seleccione el tipo de conexión VPN. Las opciones son:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Citrix**

- **Huella digital** (solo Check Point Capsule VPN): escriba una cadena (por ejemplo **Código de huella digital de Contoso**) para comprobar que se puede confiar en el servidor VPN. Una huella digital se puede enviar al cliente para que sepa que puede confiar en cualquier servidor que tenga la misma huella digital al conectarse. Si el dispositivo no tiene la huella digital, le pide al usuario que confíe en el servidor VPN mientras muestra la huella digital. El usuario comprueba la huella digital manualmente y hace clic en Confiar para conectarse.
- **Especifique pares clave-valor para los atributos de VPN de Citrix** (solo Citrix): escriba los pares de clave y valor, proporcionados por Citrix. Estos valores configuran las propiedades de la conexión VPN.

## <a name="android-enterprise-vpn-settings"></a>Configuración VPN de Android Enterprise

- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando busquen en su dispositivo las conexiones VPN disponibles.
- **Dirección IP o FQDN**: indique la dirección IP o el nombre de dominio completo (FQDN) del servidor VPN al que se conectarán los dispositivos. Por ejemplo, especifique **192.168.1.1** o **vpn.contoso.com**.

  - **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son:
  
    - **Certificados**: seleccione un perfil de certificado SCEP o PKCS existente para autenticar la conexión. [Configurar certificados](certificates-configure.md): se enumeran los pasos para crear un perfil de certificado.
    - **Nombre de usuario y contraseña**: al iniciar sesión en el servidor VPN, se pedirá a los usuarios finales que escriban un nombre de usuario y una contraseña.

- **Tipo de conexión**: seleccione el tipo de conexión VPN. Las opciones son:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="next-steps"></a>Pasos siguientes
[Perfiles de VPN en Intune](vpn-settings-configure.md)
