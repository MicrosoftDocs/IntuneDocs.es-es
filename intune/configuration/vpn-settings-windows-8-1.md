---
title: Configuración de VPN de Microsoft Intune para dispositivos Windows 8.1
titleSuffix: ''
description: Obtenga información sobre la configuración de Intune que puede usar para configurar conexiones VPN en dispositivos que ejecutan Windows 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 12267ce4e29fe2d53d01aa8115cafbf2196d50ed
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72490844"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-81"></a>Configuración de VPN en Microsoft Intune para dispositivos que ejecutan Windows 8.1

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En este artículo, se muestra la configuración de Intune que puede usar para configurar conexiones VPN en dispositivos que ejecutan Windows 8.1.

Según la configuración que elija, no todos los valores de la lista siguiente se podrán configurar.

## <a name="base-vpn-settings"></a>Configuración de VPN base


- **Apply all settings to Windows 8.1 only** (Aplicar toda la configuración solo a Windows 8.1): esta es una opción que puede configurar en el portal clásico de Intune. En el portal de Azure, esta opción no se puede cambiar. Si se establece en **Configurado**, cualquier configuración solo se aplica a dispositivos Windows 8.1. Si establece en **No configurado**, esta configuración también se aplica a dispositivos Windows 10.
- **Connection name** (Nombre de la conexión): escriba un nombre para esta conexión. Los usuarios ven este nombre cuando exploran su dispositivo para ver la lista de conexiones VPN disponibles.
- **Servidores**: agregue uno o varios servidores VPN a los que se conectarán los dispositivos.
  - **Agregar**: abre la página **Agregar fila** donde puede especificar la siguiente información:
    - **Descripción**: especifique un nombre descriptivo para el servidor, por ejemplo, **servidor VPN de Contoso**.
    - **Dirección IP o FQDN**: proporcione la dirección IP o el nombre de dominio completo del servidor VPN al que se conectarán los dispositivos. Ejemplos: **192.168.1.1**, **vpn.contoso.com**.
    - **Servidor predeterminado**: permite habilitar este servidor como el predeterminado que usarán los dispositivos para establecer la conexión. Asegúrese de establecer un solo servidor como predeterminado.
  - **Importar**: desplácese hasta un archivo que contenga una lista separada por comas de servidores en la descripción de formato, dirección IP o FQDN y servidor predeterminado. Elija **Aceptar** para importarlos a la **Servidores**.
  - **Exportar**: exporta la lista de servidores a un archivo de valores separados con comas (csv).

- **Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:
- **Check Point Capsule VPN**
- **SonicWall Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Grupo o dominio de inicio de sesión** (solo SonicWall Mobile Connect): especifique el nombre del grupo o dominio de inicio de sesión al que quiere conectarse.

- **Rol** (solo Pulse Secure): especifique el nombre del rol de usuario que tiene acceso a esta conexión. Un rol de usuario define la configuración personal y las opciones, y habilita o deshabilita ciertas características de acceso.

- **Dominio** (solo Pulse Secure): especifique el nombre del dominio de autenticación que quiere usar. Un dominio de autenticación es una agrupación de recursos de autenticación que usa el tipo de conexión Pulse Secure.


- **XML personalizado**: especifique cualquier comando XML personalizado que configure la conexión VPN.

**Ejemplo para Pulse Secure:**

```xml
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Ejemplo para CheckPoint Mobile VPN:**

```xml
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Ejemplo de SonicWall Mobile Connect:**

```xml
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Ejemplo para F5 Edge Client:**

```xml
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Para obtener más información, consulte la documentación de VPN de cada fabricante sobre cómo escribir comandos XML personalizados.


## <a name="proxy-settings"></a>Configuración del proxy

- **Detectar automáticamente configuración de proxy**: si el servidor VPN requiere un servidor proxy para la conexión, especifique si quiere que los dispositivos detecten automáticamente la configuración de la conexión. Para más información, vea la documentación de Windows Server.
- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **URL del servidor proxy** que contiene el archivo de configuración. Por ejemplo, escriba `http://proxy.contoso.com`.
- **Usar servidor proxy**: habilite esta opción si quiere especificar manualmente la configuración del servidor proxy.
  - **Dirección**: escriba la dirección del servidor proxy (como una dirección IP).
  - **Número de puerto**: especifique el número de puerto asociado con el servidor proxy.
- **Omitir proxy para direcciones locales**: si el servidor VPN requiere un servidor proxy para la conexión, seleccione esta opción si no quiere utilizar el servidor proxy para las direcciones locales que especifique. Para más información, vea la documentación de Windows Server.
