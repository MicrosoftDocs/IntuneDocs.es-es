---
title: "Configuración de VPN de Microsoft Intune para dispositivos macOS"
titlesuffix: 
description: "Obtenga información sobre la configuración de Intune que puede usar para configurar conexiones VPN en dispositivos macOS."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b7df56b0f15b9fd346dc786ab265d772135795a8
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-macos"></a>Configuración de VPN en Microsoft Intune para dispositivos que ejecutan macOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En este artículo, se muestra la configuración de Intune que puede usar para configurar conexiones VPN en dispositivos que ejecutan macOS.

Según la configuración que elija, no todos los valores de la lista siguiente se podrán configurar.

## <a name="base-vpn-settings"></a>Configuración de VPN base

**Connection name** (Nombre de la conexión): escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando exploren su dispositivo para ver la lista de conexiones VPN disponibles.
- **Dirección IP o FQDN**: proporcione la dirección IP o el nombre de dominio completo del servidor VPN al que se conectarán los dispositivos. Ejemplos: **192.168.1.1**, **vpn.contoso.com**.
- **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son:
    - **Certificados**: en **Certificado de autenticación**, elija un perfil de certificado SCEP o PKCS que anteriormente creó para autenticar la conexión. Para más información sobre los perfiles de certificado, consulte [Configuración de certificados](certificates-configure.md).
    - **Nombre de usuario y contraseña**: los usuarios finales debe proporcionar un nombre de usuario y una contraseña para iniciar sesión en el servidor VPN.
- **Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **VPN personalizada**
- **Tunelización dividida**: puede **Habilitar** o **Deshabilitar** esta opción, que permite que los dispositivos decidan qué conexión usar en función del tráfico. Por ejemplo, un usuario en un hotel usará la conexión VPN para acceder a los archivos de trabajo, pero usará la red normal del hotel para la exploración web habitual.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Configuración de VPN personalizada

Si seleccionó **VPN personalizado**, configure estas opciones adicionales:

- **Identificador de VPN**: es un identificador de la aplicación VPN que usa, y lo suministra el proveedor de VPN.
- **Especifique pares clave-valor para los atributos de la VPN personalizada**: agregue o importe **claves** y **valores** que personalicen su conexión VPN. De nuevo, estos valores los suministra normalmente el proveedor de VPN.


## <a name="proxy-settings"></a>Configuración del proxy

- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **dirección URL del servidor proxy** (por ejemplo **http://proxy.contoso.com**) que contiene el archivo de configuración.
- **Dirección**: escriba la dirección del servidor proxy (como una dirección IP).
- **Número de puerto**: especifique el número de puerto asociado con el servidor proxy.
