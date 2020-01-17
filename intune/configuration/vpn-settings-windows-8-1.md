---
title: 'Configuración de VPN para dispositivos Windows 8.1 en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue o cree un perfil de configuración de VPN con las opciones de configuración de red privada virtual (VPN), incluidos los detalles de conexión y la configuración de proxy para incluir la dirección IP o FQDN, y el puerto TCP en Microsoft Intune en los dispositivos que ejecutan Windows 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f9a1399d5474d79ac8fd48a8aa3a844f20eb640
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207050"
---
# <a name="add-vpn-settings-on-windows-81-devices-in-microsoft-intune"></a>Configuración de VPN para dispositivos Windows 8.1 en Microsoft Intune



En este artículo, se muestra la configuración de Intune que puede usar para configurar conexiones VPN en dispositivos que ejecutan Windows 8.1.

Según la configuración que elija, no todos los valores de la lista siguiente se podrán configurar.

## <a name="base-vpn-settings"></a>Configuración de VPN base

- **Aplicar toda la configuración solo a Windows 8.1**: Configure esta opción en el portal clásico de Intune. En el centro de administración de Microsoft Endpoint Manager, esta configuración no se puede cambiar. Cuando se establece en **Configurado**, cualquier configuración solo se aplica a dispositivos Windows 8.1. Cuando establece en **No configurado**, esta configuración también se aplica a dispositivos Windows 10.
- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios ven este nombre cuando exploran su dispositivo para ver la lista de conexiones VPN disponibles.
- **Servidores**: agregue uno o varios servidores VPN a los que se conectarán los dispositivos.
  - **Agregar**: abre la página **Agregar fila**, donde puede especificar la siguiente información:
    - **Descripción**: especifique un nombre descriptivo para el servidor, por ejemplo, **Servidor VPN de Contoso**.
    - **Dirección IP o FQDN**: proporcione la dirección IP o el nombre de dominio completo del servidor VPN al que se conectan los dispositivos. Ejemplos: **192.168.1.1**, **vpn.contoso.com**.
    - **Servidor predeterminado**: se permite habilitar este servidor como el predeterminado que usarán los dispositivos para establecer la conexión. Asegúrese de establecer un solo servidor como predeterminado.
  - **Importar**: vaya a un archivo delimitado por comas con la lista de servidores en el formato siguiente: descripción, dirección IP o FQDN, servidor predeterminado. Elija **Aceptar** para importar estos servidores en la lista **Servidores**.
  - **Exportar**: exporta la lista de servidores a un archivo de valores separados por comas (csv).

- **Tipo de conexión**: Seleccione el tipo de conexión VPN de la siguiente lista de proveedores:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only): Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Grupo o dominio de inicio de sesión** (solo SonicWall Mobile Connect): Especifique el nombre del grupo o dominio de inicio de sesión al que quiere conectarse.

- **Rol** (solo Pulse Secure): Especifique el nombre del rol de usuario que tiene acceso a esta conexión. Un rol de usuario define la configuración personal y las opciones, y habilita o deshabilita ciertas características de acceso.

- **Dominio kerberos** (solo Pulse Secure): Especifique el nombre de dominio de autenticación que quiere usar. Un dominio de autenticación es una agrupación de recursos de autenticación que usa el tipo de conexión Pulse Secure.

- **XML personalizado**: especifique cualquier comando XML personalizado que configure la conexión VPN.

  **Ejemplo de Pulse Secure**:

  ```xml
  <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
  ```

  **Ejemplo de CheckPoint Mobile VPN**:

  ```xml
  <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
  ```

  **Ejemplo de SonicWall Mobile Connect**:

  ```xml
  <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
  ```

  **Ejemplo de F5 Edge Client**:

  ```xml
  <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
  ```

  Para obtener más información sobre la escritura de comandos XML personalizados, vea la documentación de la VPN del fabricante.

## <a name="proxy-settings"></a>Configuración del proxy

- **Detectar automáticamente configuración de proxy**: Si el servidor VPN requiere un servidor proxy para la conexión, especifique si quiere que los dispositivos detecten automáticamente la configuración de la conexión.
- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **URL del servidor proxy** que contiene el archivo de configuración. Por ejemplo, escriba `http://proxy.contoso.com`.
- **Usar servidor proxy**: habilite esta opción si quiere especificar manualmente la configuración del servidor proxy.
  - **Dirección**: escriba la dirección del servidor proxy (como una dirección IP).
  - **Número de puerto**: especifique el número de puerto asociado al servidor proxy.
- **Omitir proxy para direcciones locales**: si el servidor VPN requiere un servidor proxy para la conexión y no quiere usar el servidor proxy para las direcciones locales que especifica, seleccione esta opción.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

Configure las opciones de VPN en dispositivos [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [MacOS](vpn-settings-macos.md)y [Windows 10](vpn-settings-windows-10.md) .
