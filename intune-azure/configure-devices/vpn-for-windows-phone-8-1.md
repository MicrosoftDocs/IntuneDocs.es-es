---
title: "Configuración de VPN de Intune para dispositivos Windows Phone 8.1"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda cómo usar la configuración de Intune para configurar conexiones VPN en dispositivos Windows Phone 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c1a9053f-02a7-4735-bc0d-fe4573b31ed4
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 2fe54f4d97c28825f06d40ec47a8a9dc40da2554
ms.lasthandoff: 02/18/2017


---

# <a name="vpn-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Configuración de VPN para dispositivos Windows Phone 8.1 en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Según la configuración que elija, no todos los valores de la siguiente lista se pueden configurar.

## <a name="base-vpn-settings"></a>Configuración de VPN base

- **Apply all settings to Windows Phone 8.1 only** (Aplicar toda la configuración solo a Windows Phone 8.1): esta es una opción que puede configurar en el portal de Intune clásico. En el portal de Azure, esta opción no se puede cambiar. Si se establece en **Configured** (Configurado), cualquier configuración solo se aplicará a dispositivos Windows Phone 8.1. Si establece en **Not Configured** (No configurado), esta configuración también se aplicará a dispositivos Windows 10 Mobile.
- **Connection name** (Nombre de la conexión): escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando exploren su dispositivo para ver la lista de conexiones VPN disponibles.
- **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son:
    - **Certificados**: en **Certificado de autenticación**, elija un perfil de certificado SCEP o PKCS que anteriormente creó para autenticar la conexión. Para más información sobre los perfiles de certificado, consulte [Configuración de certificados](how-to-configure-certificates.md).
    - **Nombre de usuario y contraseña**: los usuarios finales debe proporcionar un nombre de usuario y una contraseña para iniciar sesión en el servidor VPN.
- **Servidores**: agregue uno o más servidores VPN a los que se conectarán los dispositivos.
    - **Agregar**: abre la hoja **Add Row** (Agregar fila) donde puede especificar la siguiente información:
        - **Descripción**: especifique un nombre descriptivo para el servidor, por ejemplo, **servidor VPN de Contoso**.
        - **Dirección IP o FQDN**: proporcione la dirección IP o el nombre de dominio completo del servidor VPN al que se conectarán los dispositivos. Ejemplos: **192.168.1.1**, **vpn.contoso.com**.
        - **Servidor predeterminado**: habilita este servidor como el servidor predeterminado que usarán los dispositivos para establecer la conexión. Asegúrese de establecer un solo servidor como predeterminado.
    - **Importar**: desplácese hasta un archivo que contenga una lista separada por comas de servidores en la descripción de formato, dirección IP o FQDN y servidor predeterminado. Elija **Aceptar** para importarlos a la **Servidores**.
    - **Exportar**: exporta la lista de servidores a un archivo de valores separados con comas (csv).

- **Omitir VPN en red Wi-Fi de empresa**: habilite esta opción para especificar que la conexión VPN no se usará cuando el dispositivo se conecte a la red Wi-Fi de la empresa.
- **Omitir VPN en red Wi-Fi doméstica**: habilite esta opción para especificar que la conexión VPN no se usará cuando el dispositivo se conecte a la red Wi-Fi doméstica.

- **Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:
    - **Check Point Capsule VPN**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

- **Grupo o dominio de inicio de sesión** (solo Dell SonicWALL Mobile Connect): especifique el nombre del grupo o dominio de inicio de sesión al que quiere conectarse.
- **Rol** (solo Pulse Secure): especifique el nombre del rol de usuario que tiene acceso a esta conexión. Un rol de usuario define la configuración personal y las opciones, y habilita o deshabilita ciertas características de acceso.
- **Dominio** (solo Pulse Secure): especifique el nombre del dominio de autenticación que quiere usar. Un dominio de autenticación es una agrupación de recursos de autenticación que usa el tipo de conexión Pulse Secure.

- **Lista de búsqueda de sufijos DNS** - **agregue** uno o varios sufijos DNS. Al conectarse a un sitio web mediante un nombre corto, se buscará cada sufijo DNS que especifique. Por ejemplo, especifique los sufijos DNS **domain1.contoso.com** y **domain2.contoso.com**, visite la dirección URL **http://mywebsite**, y se buscarán las direcciones URL **http://mywebsite.domain1.contoso.com** y **http://mywebsite.domain2.contoso.com**.

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

- **Tunelización dividida** - : puede **Habilitar** o **Deshabilitar** esta opción, que permite que los dispositivos decidan qué conexión usar en función del tráfico. Por ejemplo, un usuario en un hotel usará la conexión VPN para acceder a los archivos de trabajo, pero usará la red normal del hotel para la exploración web habitual.




## <a name="proxy-settings"></a>Configuración del proxy

- **Detectar automáticamente configuración de proxy**: si el servidor VPN requiere un servidor proxy para la conexión, especifique si quiere que los dispositivos detecten automáticamente la configuración de la conexión. Para más información, vea la documentación de Windows Server.
- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **dirección URL del servidor proxy** (por ejemplo **http://proxy.contoso.com**) que contiene el archivo de configuración.
- **Usar servidor proxy**: habilite esta opción si quiere especificar manualmente la configuración del servidor proxy.
    - **Dirección**: escriba la dirección del servidor proxy (como una dirección IP).
    - **Número de puerto**: especifique el número de puerto asociado con el servidor proxy.
- **Omitir proxy para direcciones locales**: si el servidor VPN requiere un servidor proxy para la conexión, seleccione esta opción si no quiere utilizar el servidor proxy para las direcciones locales que especifique. Para más información, vea la documentación de Windows Server.

