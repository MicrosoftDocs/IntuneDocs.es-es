---
title: "Visualización de la configuración de VPN en Microsoft Intune: Azure | Microsoft Docs"
description: "Obtenga información sobre la configuración de VPN disponible en Microsoft Intune, para qué se usa y qué hace, incluidas las reglas de tráfico, el acceso condicional y la configuración de DNS y proxy para dispositivos Windows 10 y Windows Holographic for Business."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/8/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 1c1ed2946782f92313aacec05a65a80b2704ddaa
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="read-about-the-vpn-settings-in-intune"></a>Más información sobre la configuración de VPN en Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Puede configurar conexiones VPN mediante Intune. En este artículo se describen estas opciones, las reglas de tráfico, el acceso condicional y la configuración de DNS y proxy.

Estas opciones se aplican a:

- Dispositivos que ejecutan Windows 10
- Dispositivos que ejecutan Windows Holographic for Business

Según la configuración que elija, es posible que no se puedan configurar todos los valores.

## <a name="base-vpn-settings"></a>Configuración de VPN base

- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando exploren su dispositivo para ver la lista de conexiones VPN disponibles.
- **Servidores**: agregue uno o varios servidores VPN a los que se conectarán los dispositivos.
  - **Agregar**: abre **Agregar fila** donde se especifica la información siguiente:
    - **Descripción**: escriba un nombre descriptivo para el servidor, por ejemplo, **Servidor VPN de Contoso**.
    - **Dirección IP o FQDN**: escriba la dirección IP o el nombre de dominio completo del servidor VPN al que se conectarán los dispositivos, por ejemplo, **192.168.1.1** o **vpn.contoso.com**.
    - **Servidor predeterminado**: permite habilitar este servidor como el predeterminado que usarán los dispositivos para establecer la conexión. Establezca un solo servidor como predeterminado.
  - **Importar**: desplácese hasta un archivo delimitado por comas que contenga una lista de servidores en el formato siguiente: descripción, dirección IP o FQDN, servidor predeterminado. Elija **Aceptar** para importar los servidores a la lista **Servidores**.
  - **Exportar**: exporta la lista de servidores a un archivo de valores separados con comas (csv).

**Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:

- **Automático**
- **Check Point Capsule VPN**
- **Citrix VPN**
- **SonicWALL Mobile Connect**
- **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**

**Grupo o dominio de inicio de sesión** (solo SonicWALL Mobile Connect): esta propiedad no se puede establecer en el perfil de VPN. En su lugar, Mobile Connect analiza este valor cuando el nombre de usuario y el dominio se escriben en los formatos `username@domain` o `DOMAIN\username`.

**XML personalizado**/**XML de EAP**: escriba cualquier comando XML personalizado que configure la conexión VPN.

**Ejemplo para Pulse Secure:**

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Ejemplo para CheckPoint Mobile VPN:**

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Ejemplo de SonicWALL Mobile Connect:**

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Ejemplo para F5 Edge Client:**

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Para obtener más información sobre cómo escribir comandos XML personalizados, consulte la documentación de la VPN de cada fabricante.

Para obtener más información sobre la creación de XML de EAP personalizado, consulte [configuración de EAP](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

**Tunelización dividida**: puede **Habilitar** o **Deshabilitar** esta opción para que los dispositivos decidan qué conexión usar en función del tráfico. Por ejemplo, un usuario en un hotel usa la conexión VPN para acceder a los archivos de trabajo, pero usa la red normal del hotel para la exploración web habitual.
- **Rutas de tunelización dividida para esta conexión VPN**: agregue rutas opcionales para proveedores de VPN de terceros. Escriba un prefijo de destino y un tamaño de prefijo para cada uno.

## <a name="apps-and-traffic-rules"></a>Aplicaciones y reglas de tráfico

**Restringir conexión VPN a estas aplicaciones**: habilite este valor si quiere que solo algunas aplicaciones usen la conexión VPN.
**Aplicaciones asociadas**: escriba una lista de aplicaciones que usarán automáticamente la conexión VPN. El tipo de aplicación determinará el identificador de la aplicación. Para una aplicación universal, escriba el nombre de familia de paquete. Para una aplicación de escritorio, escriba la ruta de acceso al archivo de la aplicación.

>[!IMPORTANT]
>Le recomendamos que proteja todas las listas de aplicaciones creadas para VPN por aplicación. Si un usuario no autorizado cambia esta lista y, luego, esta se importa a la lista de aplicaciones de VPN por aplicación, se estará corriendo el riesgo de autorizar el acceso a la VPN a aplicaciones que no deberían tenerlo. Una forma de proteger las listas de aplicaciones consiste en usar una lista de control de acceso (ACL).

**Reglas de tráfico de red para esta conexión VPN**: seleccione qué protocolos y qué puertos locales y remotos, e intervalos de direcciones se habilitarán para la conexión VPN. Si no se crea ninguna regla de tráfico de red, se habilitan todos los protocolos, puertos e intervalos de direcciones. Una vez creada una regla, la conexión VPN solo usa los protocolos, puertos e intervalos de direcciones que escriba en esa regla.

## <a name="conditional-access"></a>Acceso condicional

**Acceso condicional para esta conexión VPN**: habilita el flujo de cumplimiento del dispositivo desde el cliente. Si esta opción está habilitada, el cliente VPN intentará comunicarse con Azure Active Directory para obtener un certificado que se usará para la autenticación. La VPN debe estar configurada para usar la autenticación de certificado, y el servidor VPN debe confiar en el servidor que devuelva Azure Active Directory.

**Inicio de sesión único (SSO) con certificado alternativo**: para el cumplimiento del dispositivo, use un certificado diferente al certificado de autenticación de la VPN para la autenticación Kerberos. Escriba el certificado con la configuración siguiente:

- **Uso mejorado de clave**: nombre para el uso mejorado de clave (EKU).
- **Identificador de objeto**: identificador de objeto del EKU.
- **Hash del emisor**: huella digital del certificado de SSO.

## <a name="dns-settings"></a>Configuración de DNS

**Nombres y servidores DNS para esta conexión VPN**: seleccione qué servidores DNS usa la conexión VPN después de establecerse la comunicación.
Para cada servidor, escriba:
- **Nombre DNS**
- **Servidor DNS**
- **Proxy**

## <a name="proxy-settings"></a>Configuración del proxy

- **Detectar automáticamente configuración de proxy**: si el servidor VPN requiere un servidor proxy para la conexión, elija si quiere que los dispositivos detecten automáticamente la configuración de la conexión.
- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **URL del servidor proxy**, como `http://proxy.contoso.com`, que contiene el archivo de configuración.
- **Usar servidor proxy**: habilite esta opción para especificar manualmente la configuración del servidor proxy.
  - **Dirección**: escriba la dirección del servidor proxy (como una dirección IP).
  - **Número de puerto**: especifique el número de puerto asociado al servidor proxy.
- **Omitir proxy para direcciones locales**: si el servidor VPN requiere un servidor proxy para la conexión, seleccione este valor si no quiere usar el servidor proxy para las direcciones locales que escriba.
