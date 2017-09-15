---
title: "Configuración de VPN de Intune para dispositivos Windows 8.1"
titleSuffix: Azure portal
description: "Conozca la configuración de Intune que puede usar para configurar conexiones VPN en los dispositivos Windows 8.1\"."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: de811d4a41aa8bdf9fd016b6ee439e1ed2ef2a92
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="vpn-settings-for-windows-81-devices-in-microsoft-intune"></a>Configuración de VPN para dispositivos Windows 8.1 en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Según la configuración que elija, no todos los valores de la siguiente lista se pueden configurar.

## <a name="base-vpn-settings"></a>Configuración de VPN base


- **Apply all settings to Windows 8.1 only** (Aplicar toda la configuración solo a Windows 8.1): esta es una opción que puede configurar en el portal clásico de Intune. En el portal de Azure, esta opción no se puede cambiar. Si se establece en **Configured** (Configurado), cualquier configuración solo se aplicará a dispositivos Windows 8.1. Si establece en **Not Configured** (No configurado), esta configuración también se aplicará a dispositivos Windows 10.
- **Connection name** (Nombre de la conexión): escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando exploren su dispositivo para ver la lista de conexiones VPN disponibles.
- **Servidores**: agregue uno o más servidores VPN a los que se conectarán los dispositivos.
    - **Agregar**: abre la hoja **Add Row** (Agregar fila) donde puede especificar la siguiente información:
        - **Descripción**: especifique un nombre descriptivo para el servidor, por ejemplo, **servidor VPN de Contoso**.
        - **Dirección IP o FQDN**: proporcione la dirección IP o el nombre de dominio completo del servidor VPN al que se conectarán los dispositivos. Ejemplos: **192.168.1.1**, **vpn.contoso.com**.
        - **Servidor predeterminado**: habilita este servidor como el servidor predeterminado que usarán los dispositivos para establecer la conexión. Asegúrese de establecer un solo servidor como predeterminado.
    - **Importar**: desplácese hasta un archivo que contenga una lista separada por comas de servidores en la descripción de formato, dirección IP o FQDN y servidor predeterminado. Elija **Aceptar** para importarlos a la **Servidores**.
    - **Exportar**: exporta la lista de servidores a un archivo de valores separados con comas (csv).

- **Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:
- **Check Point Capsule VPN**
- **Dell SonicWALL Mobile Connect**
- **F5 Edge Client**
- **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only) - Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Grupo o dominio de inicio de sesión** (solo Dell SonicWALL Mobile Connect): especifique el nombre del grupo o dominio de inicio de sesión al que quiere conectarse.

- **Rol** (solo Pulse Secure): especifique el nombre del rol de usuario que tiene acceso a esta conexión. Un rol de usuario define la configuración personal y las opciones, y habilita o deshabilita ciertas características de acceso.

- **Dominio** (solo Pulse Secure): especifique el nombre del dominio de autenticación que quiere usar. Un dominio de autenticación es una agrupación de recursos de autenticación que usa el tipo de conexión Pulse Secure.


- **XML personalizado**: especifique cualquier comando XML personalizado que configure la conexión VPN.

**Ejemplo para Pulse Secure:**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>

```

**Ejemplo para CheckPoint Mobile VPN:**
```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />

```

**Ejemplo para Dell SonicWALL Mobile Connect:**
```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>

```

**Ejemplo para F5 Edge Client:**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>

```

Consulte la documentación de VPN de cada fabricante para más información sobre cómo escribir comandos XML personalizados.


## <a name="proxy-settings"></a>Configuración del proxy

- **Detectar automáticamente configuración de proxy**: si el servidor VPN requiere un servidor proxy para la conexión, especifique si quiere que los dispositivos detecten automáticamente la configuración de la conexión. Para más información, vea la documentación de Windows Server.
- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **dirección URL del servidor proxy** (por ejemplo **http://proxy.contoso.com**) que contiene el archivo de configuración.
- **Usar servidor proxy**: habilite esta opción si quiere especificar manualmente la configuración del servidor proxy.
    - **Dirección**: escriba la dirección del servidor proxy (como una dirección IP).
    - **Número de puerto**: especifique el número de puerto asociado con el servidor proxy.
- **Omitir proxy para direcciones locales**: si el servidor VPN requiere un servidor proxy para la conexión, seleccione esta opción si no quiere utilizar el servidor proxy para las direcciones locales que especifique. Para más información, vea la documentación de Windows Server.
