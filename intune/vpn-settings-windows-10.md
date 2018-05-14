---
title: Configuración de VPN de Windows 10 en Microsoft Intune (Azure) | Microsoft Docs
description: Obtenga información sobre la configuración de VPN disponible en Microsoft Intune, para qué se usa y qué hace, incluidas las reglas de tráfico, el acceso condicional y la configuración de DNS y proxy para dispositivos Windows 10 y Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: b6371da954aa913e1378c065b203fa197f3fc767
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="windows-10-vpn-settings-in-intune"></a>Configuración de VPN de Windows 10 en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Puede configurar conexiones VPN mediante Intune. En este artículo se describen estas opciones, las reglas de tráfico, el acceso condicional y la configuración de DNS y proxy.

Estas opciones se aplican a:

- Dispositivos que ejecutan Windows 10
- Dispositivos que ejecutan Windows Holographic for Business

Según la configuración que elija, es posible que no se puedan configurar todos los valores.

## <a name="base-vpn-settings"></a>Configuración de VPN base

- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando exploren su dispositivo para ver la lista de conexiones VPN disponibles.
- **Servidores**: agregue uno o varios servidores VPN a los que se conectarán los dispositivos. Cuando se agrega un servidor, se escribe la siguiente información:
  - **Descripción**: escriba un nombre descriptivo para el servidor, por ejemplo, **Servidor VPN de Contoso**.
  - **Dirección IP o FQDN**: escriba la dirección IP o el nombre de dominio completo del servidor VPN al que se conectarán los dispositivos, por ejemplo, **192.168.1.1** o **vpn.contoso.com**.
  - **Servidor predeterminado**: permite habilitar este servidor como el predeterminado que usarán los dispositivos para establecer la conexión. Establezca un solo servidor como predeterminado.
  - **Importar**: desplácese hasta un archivo delimitado por comas que contenga una lista de servidores en el formato siguiente: descripción, dirección IP o FQDN, servidor predeterminado. Elija **Aceptar** para importar estos servidores en la lista **Servidores**.
  - **Exportar**: exporta la lista de servidores a un archivo de valores separados con comas (csv).

- **Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Automático**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  Al elegir un tipo de conexión de VPN; puede que también se le solicite la siguiente configuración:  
    - **Always On**: permite conectarse automáticamente a la VPN si ocurre lo siguiente: 
      - Los usuarios inicien sesión en sus dispositivos
      - La red del dispositivo cambie
      - La pantalla del dispositivo se vuelva a activar después de haberse desactivado 

    - **Método de autenticación**: seleccione cómo desea que los usuarios se autentiquen en el servidor VPN. El uso de **certificados** ofrece funcionalidades mejoradas, como experiencia sin interacción del usuario, VPN a petición y VPN por aplicación.
    - **Remember credentials at each logon** (Recordar credenciales en cada inicio de sesión): elija almacenar en caché las credenciales de autenticación.
    - **XML personalizado**: escriba los comandos XML personalizados que configuran la conexión VPN.
    - **XML de EAP**: escriba algún comando de XML de EAP que configure la conexión VPN.

#### <a name="pulse-secure-example"></a>Ejemplo de Pulse Secure

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>Ejemplo de F5 Edge Client

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>Ejemplo de SonicWALL Mobile Connect
**Login group or domain** (Grupo o dominio de inicio de sesión): esta propiedad no se puede establecer en el perfil de VPN. En su lugar, Mobile Connect analiza este valor cuando el nombre de usuario y el dominio se escriben en los formatos `username@domain` o `DOMAIN\username`.

Ejemplo:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

#### <a name="checkpoint-mobile-vpn-example"></a>Ejemplo de CheckPoint Mobile VPN

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

#### <a name="writing-custom-xml"></a>Escritura de XML personalizado
Para obtener más información sobre cómo escribir comandos XML personalizados, consulte la documentación de la VPN de cada fabricante.

Para obtener más información sobre la creación de XML de EAP personalizado, consulte [configuración de EAP](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

## <a name="apps-and-traffic-rules"></a>Aplicaciones y reglas de tráfico

<<<<<<< HEAD
- **Associate WIP or apps with this VPN** (Asociar WIP o aplicaciones con esta VPN): habilite esta opción solo si quiere que algunas aplicaciones usen la conexión VPN. Las opciones son:

  - **Associate a WIP with this connection** (Asociar un WIP con esta conexión): escriba un **dominio WIP para esta conexión**.
  - **Associate apps with this connection** (Asociar aplicaciones con esta conexión): puede **Restrict VPN connection to these apps** (Restringir la conexión VPN a estas aplicaciones) y, luego, agregar**aplicaciones asociadas**. Las aplicaciones que escriba automáticamente usan la conexión VPN. El tipo de aplicación determinará el identificador de la aplicación. Para una aplicación universal, escriba el nombre de familia de paquete. Para una aplicación de escritorio, escriba la ruta de acceso al archivo de la aplicación.
=======
**Restrict VPN connection to these apps** (Restringir la conexión VPN a estas aplicaciones): habilite esta opción solo si quiere que algunas aplicaciones usen la conexión VPN.

**Aplicaciones asociadas**: escriba una lista de aplicaciones que usarán automáticamente la conexión VPN. El tipo de aplicación determinará el identificador de la aplicación. Para una aplicación universal, escriba el nombre de familia de paquete. Para una aplicación de escritorio, escriba la ruta de acceso al archivo de la aplicación.
>>>>>>> b2f641d045b7649f641fb98e07accc745e697d84

  >[!IMPORTANT]
  >Le recomendamos que proteja todas las listas de aplicaciones creadas para VPN por aplicación. Si un usuario no autorizado cambia esta lista y, luego, esta se importa a la lista de aplicaciones de VPN por aplicación, se estará corriendo el riesgo de autorizar el acceso a la VPN a aplicaciones que no deberían tenerlo. Una forma de proteger las listas de aplicaciones consiste en usar una lista de control de acceso (ACL).

- **Reglas de tráfico de red para esta conexión VPN**: seleccione qué protocolos y qué puertos locales y remotos, e intervalos de direcciones se habilitarán para la conexión VPN. Si no se crea ninguna regla de tráfico de red, se habilitan todos los protocolos, puertos e intervalos de direcciones. Una vez creada una regla, la conexión VPN solo usa los protocolos, puertos e intervalos de direcciones que escriba en esa regla.

## <a name="conditional-access"></a>Acceso condicional

- **Acceso condicional para esta conexión VPN**: habilita el flujo de cumplimiento del dispositivo desde el cliente. Si esta opción está habilitada, el cliente VPN intenta comunicarse con Azure Active Directory (AD) para obtener un certificado que se usará para la autenticación. La VPN debe estar configurada para usar la autenticación de certificado, y el servidor VPN debe confiar en el servidor que devuelva Azure AD.

- **Inicio de sesión único (SSO) con certificado alternativo**: para el cumplimiento del dispositivo, use un certificado diferente al certificado de autenticación de la VPN para la autenticación Kerberos. Escriba el certificado con la configuración siguiente:

  - **Nombre**: nombre del uso mejorado de clave (EKU)
  - **Identificador de objeto**: identificador de objeto del EKU.
  - **Hash del emisor**: huella digital del certificado de SSO.

## <a name="dns-settings"></a>Configuración de DNS

**Domain and servers for this VPN connection** (Dominio y servidores de esta conexión VPN): agregue el dominio y el servidor DNS que usará esta VPN. Puede elegir qué servidores DNS usan la conexión VPN después de establecerse la conexión. Para cada servidor, escriba:
- **Dominio**
- **Servidor DNS**
- **Proxy**

## <a name="proxy-settings"></a>Configuración del proxy

- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **URL del servidor proxy**, como `http://proxy.contoso.com`, que contiene el archivo de configuración.
- **Dirección**: escriba la dirección del servidor proxy, por ejemplo, una dirección IP o `vpn.contoso.com`.
- **Número de puerto**: escriba el número de puerto TCP utilizado por el servidor proxy.
- **Bypass proxy for local addresses** (Omitir proxy para direcciones locales): si no quiere usar un servidor proxy para las direcciones locales, elija Habilitar. Esta configuración se aplica si el servidor VPN requiere un servidor proxy para la conexión.

## <a name="split-tunneling"></a>Tunelización dividida

- **Tunelización dividida**: puede **Habilitar** o **Deshabilitar** esta opción para que los dispositivos decidan qué conexión usar en función del tráfico. Por ejemplo, un usuario en un hotel usa la conexión VPN para acceder a los archivos de trabajo, pero usa la red normal del hotel para la exploración web habitual.
- **Rutas de tunelización dividida para esta conexión VPN**: agregue rutas opcionales para proveedores de VPN de terceros. Escriba un prefijo de destino y un tamaño de prefijo para cada conexión.
