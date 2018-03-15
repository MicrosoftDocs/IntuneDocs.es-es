---
title: "Configuración de VPN de Microsoft Intune para dispositivos que ejecutan Android"
titlesuffix: 
description: "Obtenga información sobre la configuración de Intune que puede usar para configurar conexiones VPN en dispositivos que ejecutan Android"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3fe05b5fdd87e92f5acc35c0a750287f8fd01b92
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-android"></a>Configuración de VPN en Microsoft Intune para dispositivos que ejecutan Android 

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Puede establecer la configuración de VPN de las siguientes plataformas:

- [Android](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

Según la configuración que elija, no se podrán configurar todos los valores que se muestran a continuación.

## <a name="android-vpn-settings"></a>Configuración de VPN de Android
**Connection name** (Nombre de la conexión): escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando exploren su dispositivo para ver la lista de conexiones VPN disponibles.
- **Dirección IP o FQDN**: proporcione la dirección IP o el nombre de dominio completo del servidor VPN al que se conectarán los dispositivos. Ejemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son:
    - **Certificados**: seleccione un perfil de certificado SCEP o PKCS que haya creado anteriormente para autenticar la conexión. Para más información sobre los perfiles de certificado, consulte [Configuración de certificados](certificates-configure.md).
    - **Nombre de usuario y la contraseña**: los usuarios finales deben proporcionar un nombre de usuario y una contraseña para iniciar sesión en el servidor VPN.
- **Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **Huella digital** (solo Check Point Capsule VPN): especifique una cadena (por ejemplo "Código de huella digital de Contoso") que se usa para comprobar que se puede confiar en el servidor VPN. Una huella digital se puede enviar al cliente para que sepa que puede confiar en cualquier servidor que presente esa misma huella digital al conectarse. Si el dispositivo todavía no tiene la huella digital, pide al usuario que confíe en el servidor VPN al que se está conectando mientras muestra la huella digital (el usuario comprueba la huella digital manualmente y selecciona Confiar para conectarse).
- **Especifique pares clave-valor para los atributos de la VPN de Citrix** (solo Citrix): escriba los pares de clave y valor, que ha suministrado Citrix, para configurar las propiedades de la conexión VPN.

## <a name="android-for-work-vpn-settings"></a>Configuración de VPN de Android for Work

**Connection name** (Nombre de la conexión): escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando exploren su dispositivo para ver la lista de conexiones VPN disponibles.
- **Dirección IP o FQDN**: proporcione la dirección IP o el nombre de dominio completo del servidor VPN al que se conectarán los dispositivos. Ejemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son:
    - **Certificados**: seleccione un perfil de certificado SCEP o PKCS que haya creado anteriormente para autenticar la conexión. Para más información sobre los perfiles de certificado, consulte [Configuración de certificados](certificates-configure.md).
    - **Nombre de usuario y la contraseña**: los usuarios finales deben proporcionar un nombre de usuario y una contraseña para iniciar sesión en el servidor VPN.
- **Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

