---
title: "Configuración de VPN de Intune para dispositivos Windows 10"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda sobre la configuración de Intune que puede usar para configurar conexiones VPN en dispositivos Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 495e4ed6-b2ef-47cc-a110-13fa9b5f85a6
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 87004408ddcb07571507f68d5b9925b7e475282a
ms.lasthandoff: 02/18/2017


---

# <a name="vpn-settings-for-windows-10-devices-in-microsoft-intune"></a>Configuración de VPN para dispositivos Windows 10 en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Según la configuración que elija, no todos los valores de la siguiente lista se pueden configurar.


## <a name="base-vpn-settings"></a>Configuración de VPN base


- **Connection name** (Nombre de la conexión): escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando exploren su dispositivo para ver la lista de conexiones VPN disponibles.
- **Servidores**: agregue uno o más servidores VPN a los que se conectarán los dispositivos.
    - **Agregar**: abre la hoja **Add Row** (Agregar fila) donde puede especificar la siguiente información:
        - **Descripción**: especifique un nombre descriptivo para el servidor, por ejemplo, **servidor VPN de Contoso**.
        - **Dirección IP o FQDN**: proporcione la dirección IP o el nombre de dominio completo del servidor VPN al que se conectarán los dispositivos. Ejemplos: **192.168.1.1**, **vpn.contoso.com**.
        - **Servidor predeterminado**: habilita este servidor como el servidor predeterminado que usarán los dispositivos para establecer la conexión. Asegúrese de establecer un solo servidor como predeterminado.
    - **Importar**: desplácese hasta un archivo que contenga una lista separada por comas de servidores en la descripción de formato, dirección IP o FQDN y servidor predeterminado. Elija **Aceptar** para importarlos a la **Servidores**.
    - **Exportar**: exporta la lista de servidores a un archivo de valores separados con comas (csv).

**Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:
- **Pulse Secure**
- **F5 Edge Client**
- **Dell SonicWALL Mobile Connect**
- **Check Point Capsule VPN**
- **Automático**
- **IKEv2**
- **L2TP**
- **PPTP**

**Grupo o dominio de inicio de sesión** (solo Dell SonicWALL Mobile Connect): especifique el nombre del grupo o dominio de inicio de sesión al que quiere conectarse.

**XML personalizado**/**EAP XML**: especifique cualquier comando XML personalizado que configure la conexión VPN.

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

**Tunelización dividida** - : puede **Habilitar** o **Deshabilitar** esta opción, que permite que los dispositivos decidan qué conexión usar en función del tráfico. Por ejemplo, un usuario en un hotel usará la conexión VPN para acceder a los archivos de trabajo, pero usará la red normal del hotel para la exploración web habitual.
- **Rutas de tunelización dividida para esta conexión VPN**: agregue rutas opcionales para proveedores de VPN de terceros. Especifique un prefijo de destino y un tamaño de prefijo para cada uno.

## <a name="apps-and-traffic-rules"></a>Aplicaciones y reglas de tráfico

**Restringir conexión VPN a estas aplicaciones**: habilite esta opción si quiere que las aplicaciones que especifique usen la conexión VPN.
**Aplicaciones asociadas**: proporcione una lista de las aplicaciones que usarán automáticamente la conexión VPN. El tipo de aplicación determinará el identificador de la aplicación. Para una aplicación universal, proporcione el nombre de familia de paquete. Para una aplicación de escritorio, proporcione la ruta de acceso al archivo de la aplicación.

>[!IMPORTANT]
>Se recomienda proteger todas las listas de aplicaciones que se compilen para su uso en la configuración de VPN por aplicación. Si un usuario no autorizado modifica la lista y, luego, se importa a la lista de aplicaciones de VPN por aplicación, se estará corriendo el riesgo de autorizar el acceso a VPN a aplicaciones que no deberían tenerlo. Una forma de proteger las listas de aplicaciones consiste en usar una lista de control de acceso (ACL).

**Reglas de tráfico de red para esta conexión VPN**: seleccione qué protocolos y qué puertos locales y remotos e intervalos de direcciones se habilitarán para las conexiones VPN. Si no se crea ninguna regla de tráfico de red, se habilitan todos los protocolos, puertos e intervalos de direcciones. Una vez creada una regla, la conexión VPN solo usará los protocolos, puertos e intervalos de direcciones que especifique en esa regla.


## <a name="conditional-access"></a>Acceso condicional

**Acceso condicional para esta conexión VPN** -
**Inicio de sesión único (SSO) con certificado alternativo** -
**Uso mejorado de clave** -
**Hash del emisor** -

## <a name="dns-settings"></a>Configuración de DNS

**Nombres y servidores DNS para esta conexión VPN**: seleccione qué servidores DNS usará la conexión VPN después de establecerse la comunicación.
Para cada servidor, especifique:
- **Nombre DNS**
- **Servidor DNS**
- **Proxy**

## <a name="proxy-settings"></a>Configuración del proxy

- **Detectar automáticamente configuración de proxy**: si el servidor VPN requiere un servidor proxy para la conexión, especifique si quiere que los dispositivos detecten automáticamente la configuración de la conexión. Para más información, vea la documentación de Windows Server.
- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **dirección URL del servidor proxy** (por ejemplo **http://proxy.contoso.com**) que contiene el archivo de configuración.
- **Usar servidor proxy**: habilite esta opción si quiere especificar manualmente la configuración del servidor proxy.
    - **Dirección**: escriba la dirección del servidor proxy (como una dirección IP).
    - **Número de puerto**: especifique el número de puerto asociado con el servidor proxy.
- **Omitir proxy para direcciones locales**: si el servidor VPN requiere un servidor proxy para la conexión, seleccione esta opción si no quiere utilizar el servidor proxy para las direcciones locales que especifique. Para más información, vea la documentación de Windows Server.

