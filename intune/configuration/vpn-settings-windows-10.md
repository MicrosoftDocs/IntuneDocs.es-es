---
title: 'Configuración de VPN de Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Obtenga información sobre toda la configuración de VPN que está disponible en Microsoft Intune, para qué se usa y qué hace, incluidas las reglas de tráfico, el acceso condicional y la configuración de DNS y proxy para dispositivos con Windows 10 y Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5d5bd16964162bd30e1c246215ce5fafd23df5dd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734133"
---
# <a name="windows-10-and-windows-holographic-device-settings-to-add-vpn-connections-using-intune"></a>Configuración de dispositivos con Windows 10 y Windows Holographic para agregar conexiones VPN mediante Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Puede agregar y configurar conexiones VPN para dispositivos con Microsoft Intune. En este artículo se enumeran y describen las características y los valores de configuración más usados al crear redes privadas virtuales (VPN). Estas características y valores de configuración de VPN se usan en los perfiles de configuración de dispositivo en Intune que se insertan o implementan en dispositivos.

Como parte de la solución de administración de dispositivos móviles (MDM), use esta configuración para permitir o deshabilitar características, como el uso de un proveedor de VPN, la habilitación de Always On, el uso de DNS, la adición de un servidor proxy y mucho más.

Esta configuración se aplica a los dispositivos que ejecuten lo siguiente:

- Windows 10
- Windows Holographic for Business

Según la configuración que elija, es posible que no se puedan configurar todos los valores.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo VPN](vpn-settings-configure.md).

## <a name="base-vpn-settings"></a>Configuración de VPN base

- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando exploren su dispositivo para ver la lista de conexiones VPN disponibles.
- **Servidores**: agregue uno o varios servidores VPN a los que se conectarán los dispositivos. Cuando se agrega un servidor, se escribe la siguiente información:
  - **Descripción**: escriba un nombre descriptivo para el servidor, por ejemplo, **Servidor VPN de Contoso**.
  - **Dirección IP o FQDN**: escriba la dirección IP o el nombre de dominio completo (FQDN) del servidor VPN al que se conectan los dispositivos, por ejemplo, **192.168.1.1** o **vpn.contoso.com**.
  - **Servidor predeterminado**: permite habilitar este servidor como el predeterminado que usarán los dispositivos para establecer la conexión. Establezca un solo servidor como predeterminado.
  - **Importar**: desplácese hasta un archivo delimitado por comas que incluya una lista de servidores en el formato siguiente: descripción, dirección IP o FQDN, servidor predeterminado. Elija **Aceptar** para importar estos servidores en la lista **Servidores**.
  - **Exportar**: exporta la lista de servidores a un archivo de valores separados con comas (csv).

- **Registrar direcciones IP en DNS interno**: seleccione **Habilitar** para configurar el perfil de VPN de Windows 10 para registrar dinámicamente las direcciones IP asignadas a la interfaz VPN con el DNS interno. Seleccione **Deshabilitar** para no registrar dinámicamente las direcciones IP.

- **Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Palo Alto Networks GlobalProtect**
  - **Automático**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  Al elegir un tipo de conexión de VPN; puede que también se le solicite la siguiente configuración:  
  - **Always On**: elija **Habilitar** para conectarse automáticamente a la VPN cuando se produzcan estas situaciones: 
    - Los usuarios inicien sesión en sus dispositivos
    - La red del dispositivo cambie
    - La pantalla del dispositivo se vuelva a activar después de haberse desactivado 

  - **Método de autenticación**: seleccione cómo desea que los usuarios se autentiquen en el servidor VPN. El uso de **certificados** ofrece características mejoradas, como experiencia sin interacción del usuario, VPN a petición y VPN por aplicación.
  - **Remember credentials at each logon** (Recordar credenciales en cada inicio de sesión): elija almacenar en caché las credenciales de autenticación.
  - **XML personalizado**: escriba los comandos XML personalizados que configuran la conexión VPN.
  - **XML de EAP**: escriba algún comando de XML de EAP que configure la conexión VPN.

### <a name="pulse-secure-example"></a>Ejemplo de Pulse Secure

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

### <a name="f5-edge-client-example"></a>Ejemplo de F5 Edge Client

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

### <a name="sonicwall-mobile-connect-example"></a>Ejemplo de SonicWALL Mobile Connect
**Login group or domain** (Grupo o dominio de inicio de sesión): esta propiedad no se puede establecer en el perfil de VPN. En su lugar, Mobile Connect analiza este valor cuando el nombre de usuario y el dominio se escriben en los formatos `username@domain` o `DOMAIN\username`.

Ejemplo:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

### <a name="checkpoint-mobile-vpn-example"></a>Ejemplo de CheckPoint Mobile VPN

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

### <a name="writing-custom-xml"></a>Escritura de XML personalizado
Para obtener más información sobre cómo escribir comandos XML personalizados, consulte la documentación de la VPN de cada fabricante.

Para obtener más información sobre la creación de XML de EAP personalizado, consulte [configuración de EAP](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

## <a name="apps-and-traffic-rules"></a>Aplicaciones y reglas de tráfico

- **Associate WIP or apps with this VPN** (Asociar WIP o aplicaciones con esta VPN): habilite esta opción solo si quiere que algunas aplicaciones usen la conexión VPN. Las opciones son:

  - **Associate a WIP with this connection** (Asociar un WIP con esta conexión): escriba un **dominio WIP para esta conexión**.
  - **Associate apps with this connection** (Asociar aplicaciones con esta conexión): puede **Restrict VPN connection to these apps** (Restringir la conexión VPN a estas aplicaciones) y, luego, agregar**aplicaciones asociadas**. Las aplicaciones que escriba automáticamente usan la conexión VPN. El tipo de aplicación determinará el identificador de la aplicación. Para una aplicación universal, escriba el nombre de familia de paquete. Para una aplicación de escritorio, escriba la ruta de acceso al archivo de la aplicación.
  >[!IMPORTANT]
  >Le recomendamos que proteja todas las listas de aplicaciones creadas para VPN por aplicación. Si un usuario no autorizado cambia esta lista y, luego, esta se importa a la lista de aplicaciones de VPN por aplicación, se estará corriendo el riesgo de autorizar el acceso a la VPN a aplicaciones que no deberían tenerlo. Una forma de proteger las listas de aplicaciones consiste en usar una lista de control de acceso (ACL).

- **Reglas de tráfico de red para esta conexión VPN**: seleccione qué protocolos y qué puertos locales y remotos, e intervalos de direcciones se habilitarán para la conexión VPN. Si no se crea ninguna regla de tráfico de red, se habilitan todos los protocolos, puertos e intervalos de direcciones. Una vez creada una regla, la conexión VPN solo usa los protocolos, puertos e intervalos de direcciones que escriba en esa regla.

## <a name="conditional-access"></a>Acceso condicional

- **Acceso condicional para esta conexión VPN**: habilita el flujo de cumplimiento del dispositivo desde el cliente. Si esta opción está habilitada, el cliente VPN se comunica con Azure Active Directory (AD) para obtener un certificado que se usará para la autenticación. La VPN debe estar configurada para usar la autenticación de certificado, y el servidor VPN debe confiar en el servidor que devuelva Azure AD.

- **Inicio de sesión único (SSO) con certificado alternativo**: para el cumplimiento del dispositivo, use un certificado diferente al certificado de autenticación de la VPN para la autenticación Kerberos. Escriba el certificado con la configuración siguiente:

  - **Nombre**: nombre del uso mejorado de clave (EKU)
  - **Identificador de objeto**: identificador de objeto del EKU.
  - **Hash del emisor**: huella digital del certificado de SSO.

## <a name="dns-settings"></a>Configuración de DNS

- **Lista de búsqueda de sufijos DNS**: en **Sufijos DNS**, escriba un sufijo DNS y haga clic en **Agregar**. Puede agregar varios sufijos.

  Al usar los sufijos DNS, puede buscar un recurso de red mediante su nombre corto, en lugar del nombre de dominio completo (FQDN). Al realizar búsquedas mediante el nombre corto, el servidor DNS determina automáticamente el sufijo. Por ejemplo, `utah.contoso.com` está en la lista de sufijos DNS. Se hace ping a `DEV-comp`. En este escenario, se resuelve en `DEV-comp.utah.contoso.com`.

  Los sufijos DNS se resuelven en el orden enumerado y este orden se puede cambiar. Por ejemplo, `colorado.contoso.com` y `utah.contoso.com` están en la lista de sufijos DNS y ambos tienen un recurso denominado `DEV-comp`. Como `colorado.contoso.com` es el primero de la lista, se resuelve como `DEV-comp.colorado.contoso.com`.
  
  Para cambiar el orden, haga clic en los puntos que aparecen a la izquierda del sufijo DNS y luego arrastre el sufijo a la parte superior:

  ![Seleccione los tres puntos y haga clic y arrastre para mover el sufijo DNS.](./media/vpn-settings-windows-10/vpn-settings-windows10-move-dns-suffix.png)

- **Reglas de la tabla de directivas de resolución de nombres (NRPT)** : las reglas de la tabla de directivas de resolución de nombres (NRPT) definen el modo en que DNS resuelve los nombres cuando se conecta a la VPN. Después de haber establecido la conexión VPN, elija qué servidores DNS usa la conexión VPN.

  Puede agregar reglas a la tabla que incluyan el dominio, el servidor DNS, el proxy y otros detalles para resolver el dominio que escriba. La conexión VPN usa estas reglas cuando los usuarios se conectan a los dominios que escriba.

  Haga clic en **Agregar** para agregar una nueva regla. Para cada servidor, escriba:

  - **Dominio**: escriba el nombre de dominio completo (FQDN) o un sufijo DNS para aplicar la regla. También puede escribir un punto (.) al principio de un sufijo DNS. Por ejemplo, escriba `contoso.com` o `.allcontososubdomains.com`.
  - **Servidores DNS**: escriba la dirección IP o el servidor DNS que resuelve el dominio. Por ejemplo, escriba `10.0.0.3` o `vpn.contoso.com`.
  - **Proxy**: escriba el servidor proxy web que resuelve el dominio. Por ejemplo, escriba `http://proxy.com`.
  - **Conectarse automáticamente**: si la opción está **habilitada**, el dispositivo se conecta automáticamente a la VPN cuando un dispositivo se conecta a un dominio especificado, como `contoso.com`. Si la opción es **Sin configurar** (valor predeterminado), el dispositivo no se conecta automáticamente a la VPN.
  - **Persistente**: cuando se establece en **Habilitada**, la regla permanece en la tabla de directivas de resolución de nombres (NRPT) hasta que se quita de forma manual del dispositivo, incluso después de que se desconecte la VPN. Cuando se establece en **Sin configurar** (valor predeterminado), se quitan las reglas de NRPT en el perfil de VPN del dispositivo cuando se desconecta la VPN.

## <a name="proxy-settings"></a>Configuración del proxy

- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **URL del servidor proxy**, como `http://proxy.contoso.com`, que incluye el archivo de configuración.
- **Dirección**: escriba la dirección del servidor proxy, por ejemplo, una dirección IP o `vpn.contoso.com`.
- **Número de puerto**: escriba el número de puerto TCP utilizado por el servidor proxy.
- **Bypass proxy for local addresses** (Omitir proxy para direcciones locales): si no quiere usar un servidor proxy para las direcciones locales, elija Habilitar. Esta configuración se aplica si el servidor VPN requiere un servidor proxy para la conexión.

## <a name="split-tunneling"></a>Tunelización dividida

- **Tunelización dividida**: puede **Habilitar** o **Deshabilitar** esta opción para que los dispositivos decidan qué conexión usar en función del tráfico. Por ejemplo, un usuario en un hotel usa la conexión VPN para acceder a los archivos de trabajo, pero usa la red normal del hotel para la exploración web habitual.
- **Rutas de tunelización dividida para esta conexión VPN**: agregue rutas opcionales para proveedores de VPN de terceros. Escriba un prefijo de destino y un tamaño de prefijo para cada conexión.

## <a name="trusted-network-detection"></a>Detección de redes de confianza

**Sufijos DNS de red de confianza**: si los usuarios ya están conectados a una red de confianza, puede evitar que los dispositivos se conecten automáticamente a otras VPN.

En **Sufijos DNS**, escriba un sufijo DNS en el que quiera confiar (por ejemplo, contoso.com) y seleccione **Agregar**. Puede agregar tantos sufijos como quiera.

Si un usuario está conectado a un sufijo DNS de la lista, el usuario no se conectará automáticamente a otra VPN. El usuario sigue usando la lista de confianza de sufijos DNS que ha especificado. Se sigue usando la red de confianza, incluso si se establece algún desencadenamiento automático.

Por ejemplo, si el usuario ya está conectado a un sufijo DNS de confianza, se omiten los siguientes desencadenamientos automáticos. En concreto, los sufijos DNS de la lista cancelan todos los demás desencadenamientos automáticos de conexión, incluidos los siguientes:

- Siempre disponible
- Desencadenamiento basado en la aplicación
- Desencadenamiento automático de DNS

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).

Configure los valores de VPN en dispositivos [Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md) y [macOS](vpn-settings-macos.md).
