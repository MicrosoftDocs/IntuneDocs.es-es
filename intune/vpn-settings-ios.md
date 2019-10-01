---
title: 'Configuración de VPN para dispositivos iOS en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue o cree un perfil de configuración de VPN mediante opciones de configuración de red privada virtual (VPN), incluidos los detalles de conexión, los métodos de autenticación y la tunelización dividida en la configuración básica; la configuración de VPN personalizada con el identificador y los pares clave-valor; la configuración de VPN por aplicación que incluye las direcciones URL de Safari y las VPN a petición con dominios de búsqueda DNS o SSID; y la configuración de proxy para incluir un script de configuración, una dirección IP o FQDN y un puerto TCP en Microsoft Intune en dispositivos que ejecutan iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 696e335e422ed45af7b7c53db9e91dead5ea8502
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2019
ms.locfileid: "71302775"
---
# <a name="add-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Incorporación de VPN en dispositivos iOS en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune incluye muchas opciones de configuración de VPN que se pueden implementar en los dispositivos iOS. Estas opciones se usan para crear y configurar conexiones VPN a la red de su organización. Ambas se describen en este artículo. Algunas opciones solo están disponibles para algunos clientes VPN, como Citrix, Zscaler y otros.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](vpn-settings-configure.md).

> [!NOTE]
> Estas opciones están disponibles para todos los tipos de inscripción. Para obtener más información sobre los tipos de inscripción, consulte [inscripción de iOS](ios-enroll.md).

## <a name="connection-type"></a>Tipo de conexión

Seleccione el tipo de conexión VPN de la siguiente lista de proveedores:

- **Check Point Capsule VPN**
- **Cisco Legacy AnyConnect**: para la versión 4.0.5x y versiones anteriores de la aplicación [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924).
- **Cisco AnyConnect**: para la versión 4.0.7x y versiones anteriores de la aplicación [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690).
- **SonicWall Mobile Connect**
- **F5 Access Legacy**: aplicable a la versión 2.1 de la aplicación F5 Access y versiones anteriores.
- **F5 Access**: aplicable a la versión 3.0 de la aplicación F5 Access y versiones posteriores.
- **GlobalProtect de Palo Alto Networks (Legacy)** : aplicable a la aplicación GlobalProtect de Palo Alto Networks, versión 4.1 y anteriores.
- **GlobalProtect de Palo Alto Networks**: aplicable a la aplicación GlobalProtect de Palo Alto Networks, versión 5.0 y posteriores.
- **Pulse Secure**
- **Cisco (IPSec)**
- **Citrix VPN**
- **Citrix SSO**
- **Zscaler**: para usar el acceso condicional o permitir a los usuarios que omitan la pantalla de inicio de sesión de Zscaler, después debe integrar Zscaler Private Access (ZPA) con la cuenta de Azure AD. Para obtener instrucciones detalladas, vea la [documentación de Zscaler](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad). 
- **IKEv2**: la [configuración de IKEv2](#ikev2-settings) (en este artículo) describe las propiedades.
- **VPN personalizada**

> [!NOTE]
> Cisco, Citrix, F5 y Palo Alto han anunciado que sus clientes heredados no funcionan en iOS 12. Tendrá que migrar a las aplicaciones nuevas tan pronto como sea posible. Para obtener más información, vea el [blog del equipo de soporte técnico de Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

## <a name="base-vpn-settings"></a>Configuración de VPN base

La configuración que se muestra en la siguiente lista se determina según el tipo de conexión VPN que elija.  

- **Nombre de la conexión**: los usuarios finales verán este nombre cuando exploren su dispositivo para obtener una lista de las conexiones VPN disponibles.
- **Nombre de dominio personalizado** (solo Zscaler): rellene previamente el campo de inicio de sesión de la aplicación Zscaler con el dominio al que pertenecen los usuarios. Por ejemplo, si un nombre de usuario es `Joe@contoso.net`, el dominio `contoso.net` aparece de forma estática en el campo al abrir la aplicación. Si no escribe un nombre de dominio, se usa la parte del dominio del UPN en Azure Active Directory (AD).
- **Dirección IP o FQDN**: la dirección IP o el nombre de dominio completo (FQDN) del servidor VPN al que se conectan los dispositivos. Por ejemplo, escriba `192.168.1.1` o `vpn.contoso.com`.
- **Nombre de nube de la organización** (solo Zscaler): escriba el nombre de la nube donde se aprovisiona la organización. El nombre aparece en la URL que usa para iniciar sesión en Zscaler.  
- **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. 
  - **Certificados**: en **Certificado de autenticación**, seleccione un perfil de certificado SCEP o PKCS existente para autenticar la conexión. En [Configurar certificados](certificates-configure.md) se proporcionan algunas directrices sobre los perfiles de certificado.
  - **Nombre de usuario y contraseña**: los usuarios finales deben introducir un nombre de usuario y una contraseña para iniciar sesión en el servidor VPN.  

    > [!NOTE]
    > Si el nombre de usuario y la contraseña se usan como método de autenticación para VPN Cisco IPsec, deben entregar la credencial SharedSecret a través de un perfil personalizado de Apple Configurator.

- **Direcciones URL excluidas** (solo Zscaler): cuando se conecta a la VPN de Zscaler, las direcciones URL de la lista son accesibles desde fuera de la nube de Zscaler. 

- **Tunelización dividida**: puede **Habilitar** o **Deshabilitar** esta opción para que los dispositivos decidan qué conexión usar en función del tráfico. Por ejemplo, un usuario en un hotel usa la conexión VPN para acceder a los archivos de trabajo, pero usa la red normal del hotel para la exploración web habitual.

- **Identificador de VPN** (VPN personalizada, Zscaler y Citrix): es un identificador de la aplicación VPN que usa. Lo suministra el proveedor de VPN.
  - **Especifique pares clave-valor para los atributos de la VPN personalizada**: agregue o importe **Claves** y **Valores** que personalicen la conexión VPN. Recuerde que estos valores los suele suministrar el proveedor de VPN.

- **Habilitar el control de acceso de red (NAC)** (Citrix SSO, F5 Access): cuando se elige **Acepto**, se incluye el identificador del dispositivo en el perfil de VPN. Este identificador puede usarse con la autenticación en la VPN para permitir o impedir el acceso de red.

  **Cuando use F5 Access**, no olvide:

  - Confirmar que está usando F5 BIG-IP 13.1.1.5. No se admite BIG-IP 14.
  - Integre BIG-IP con Intune para NAC. Vea la guía de F5 [Configuring APM for device posture checks with endpoint management systems](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) (Información general: Configuración de APM para comprobaciones de posición del dispositivo con sistemas de administración de puntos de conexión).
  - Habilitar NAC en el perfil de VPN.

  **Si utiliza Citrix SSO con puerta de enlace**, no olvide:

  - Confirmar que utiliza Citrix Gateway 12.0.59 o superior.
  - Confirmar que los usuarios tienen Citrix SSO 1.1.6 o posterior instalado en sus dispositivos.
  - Integrar Citrix Gateway con Intune para el control de acceso de red. Vea la guía de implementación de Citrix sobre [integración de Microsoft Intune/Enterprise Mobility Suite con NetScaler (escenario LDAP+OTP)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf).
  - Habilitar NAC en el perfil de VPN.

  **Detalles importantes**:  

  - Si NAC está habilitada, la VPN se desconecta cada 24 horas. VPN se puede volver a conectar inmediatamente.
  - El identificador de dispositivo forma parte del perfil, pero no se muestra en Intune. Microsoft no almacena este identificador en ningún lugar ni tampoco lo comparte.

  Cuando el identificador de dispositivo es compatible con los asociados de VPN, el cliente VPN, como Citrix SSO, puede obtener el identificador. Después, puede consultar a Intune para confirmar que el dispositivo está inscrito y si el perfil de VPN es compatible o no.

  - Para quitar esta configuración, vuelva a crear el perfil y no seleccione **Acepto**. Después, vuelva a asignar el perfil.

## <a name="ikev2-settings"></a>Configuración de IKEv2

Esta configuración se aplica cuando se elige el **tipo de conexión** > **IKEv2**.

- **Identificador remoto**: escriba la dirección IP de red, el FQDN, USERFQDN o ASN1DN del servidor IKEv2. Por ejemplo, escriba `10.0.0.3` o `vpn.contoso.com`. Normalmente, se escribe el mismo valor que el [**nombre**](#base-vpn-settings) de la conexión (en este artículo). Pero depende de la configuración del servidor IKEv2.

- **Tipo de autenticación de cliente**: elija cómo el cliente VPN se autentica en la VPN. Las opciones son:
  - **Autenticación de usuario** (valor predeterminado): las credenciales de usuario se autentican en la VPN.
  - **Autenticación del equipo**: las credenciales del dispositivo se autentican en la VPN.

- **Método de autenticación**: elija el tipo de credenciales de cliente que se enviarán al servidor. Las opciones son:
  - **Certificados**: usa un perfil de certificado existente para autenticarse en la VPN. Asegúrese de que este perfil de certificado ya está asignado al usuario o dispositivo. De lo contrario, se produce un error en la conexión VPN.
    - **Tipo de certificado**: seleccione el tipo de cifrado que usa el certificado. Asegúrese de que el servidor VPN está configurado para aceptar este tipo de certificado. Las opciones son:
      - **RSA** (valor predeterminado)
      - **ECDSA256**
      - **ECDSA384**
      - **ECDSA521**

  - **Nombre de usuario y contraseña** (solo autenticación de usuario): cuando los usuarios se conectan a la VPN, se les pide su nombre de usuario y contraseña.
  - **Secreto compartido** (solo autenticación de equipo): le permite especificar un secreto compartido para enviar al servidor VPN.
    - **Secreto compartido**: escriba el secreto compartido, también conocido como clave precompartida (PSK). Asegúrese de que el valor coincide con el secreto compartido configurado en el servidor VPN.

- **Nombre común del emisor del certificado de servidor**: permite que el servidor VPN se autentique en el cliente VPN. Escriba el nombre común (CN) del emisor de certificados del certificado de servidor VPN que se envía al cliente VPN en el dispositivo. Asegúrese de que el valor CN coincide con la configuración en el servidor VPN. De lo contrario, se produce un error en la conexión VPN.
- **Nombre común del certificado de servidor**: escriba el CN para el propio certificado. Si se deja en blanco, se usa el valor del identificador remoto.

- **Tasa de detección del mismo nivel muerto**: elija la frecuencia con la que el cliente VPN comprueba si el túnel VPN está activo. Las opciones son:
  - **No configurado**: utiliza el valor predeterminado del sistema iOS, que puede ser el mismo que elegir **medio**.
  - **Ninguno**: deshabilita la detección de equipos inactivos.
  - **Bajo**: envía un mensaje keepalive cada 30 minutos.
  - **Medium** (valor predeterminado): envía un mensaje keepalive cada 10 minutos.
  - **Alto**: envía un mensaje keepalive cada 60 segundos.

- **Intervalo de versión de TLS mínimo**: escriba la versión de TLS mínima que se va a usar. Escriba `1.0`, `1.1` o `1.2`. Si se deja en blanco, se usa el valor predeterminado de `1.0`.
- **Intervalo de versión máximo de TLS**: escriba la versión máxima de TLS que se va a usar. Escriba `1.0`, `1.1` o `1.2`. Si se deja en blanco, se usa el valor predeterminado de `1.2`.
- **Confidencialidad directa perfecta**: seleccione **Habilitar** para activar la confidencialidad directa perfecta (PFS). PFS es una característica de seguridad IP que reduce el impacto si una clave de sesión se ve comprometida. **Deshabilitar** (valor predeterminado) no usa PFS.
- **Comprobación de revocación de certificados**: seleccione **Habilitar** para asegurarse de que no se revocan los certificados antes de permitir que la conexión VPN se realice correctamente. Esta comprobación es el mejor esfuerzo. Si el servidor VPN agota el tiempo de espera antes de determinar si el certificado se ha revocado, se concede el acceso. **Deshabilitar** (valor predeterminado) no comprueba los certificados revocados.

- **Configurar parámetros**de la Asociación de seguridad: **no configurado** (valor predeterminado) usa el valor predeterminado del sistema iOS. Seleccione **Habilitar** para especificar los parámetros que se usan al crear asociaciones de seguridad con el servidor VPN:
  - **Algoritmo de cifrado**: seleccione el algoritmo que desee:
    - DES
    - DICHA
    - AES-128
    - AES-256 (valor predeterminado)
    - AES-128-GCM
    - AES-256-GCM
  - **Algoritmo de integridad**: seleccione el algoritmo que desee:
    - SHA1-96
    - SHA1:160
    - SHA2-256 (valor predeterminado)
    - SHA2-384
    - SHA2-512
  - **Grupo Diffie-Hellman**: seleccione el grupo que desee. El valor predeterminado es Group `2`.
  - **Duración** (minutos): elija cuánto tiempo permanece activo la Asociación de seguridad hasta que se rotan las claves. Escriba un valor entero entre `10` y `1440` (1440 minutos es 24 horas). El valor `1440`predeterminado es.

- **Configurar un conjunto independiente de parámetros para las asociaciones de seguridad secundarias**: iOS le permite configurar parámetros independientes para la conexión IKE y cualquier conexión secundaria. 

  **No configurado** (valor predeterminado) usa los valores especificados en la configuración anterior **Configurar parámetros** de la Asociación de seguridad. Seleccione **Habilitar** para especificar los parámetros que se usan al crear asociaciones de seguridad *secundarias* con el servidor VPN:
  - **Algoritmo de cifrado**: seleccione el algoritmo que desee:
    - DES
    - DICHA
    - AES-128
    - AES-256 (valor predeterminado)
    - AES-128-GCM
    - AES-256-GCM
  - **Algoritmo de integridad**: seleccione el algoritmo que desee:
    - SHA1-96
    - SHA1:160
    - SHA2-256 (valor predeterminado)
    - SHA2-384
    - SHA2-512
  - **Grupo Diffie-Hellman**: seleccione el grupo que desee. El valor predeterminado es Group `2`.
  - **Duración** (minutos): elija cuánto tiempo permanece activo la Asociación de seguridad hasta que se rotan las claves. Escriba un valor entero entre `10` y `1440` (1440 minutos es 24 horas). El valor `1440`predeterminado es.

## <a name="automatic-vpn-settings"></a>Configuración automática de VPN

- **VPN por aplicación**: permite la VPN por aplicación. Permite que la conexión VPN se desencadene de forma automática cuando se abren determinadas aplicaciones. También se asocian las aplicaciones con este perfil de VPN. Para obtener más información, vea las [instrucciones para configurar una VPN por aplicación para iOS](vpn-setting-configure-per-app.md).
  - **Tipo de proveedor**: solo está disponible para Pulse Secure y VPN personalizada.
  - Al usar perfiles de **VPN por aplicación** de iOS con Pulse Secure o una VPN personalizada, elija la tunelización de la capa de la aplicación (app-proxy) o la tunelización de nivel de paquete (packet-tunnel). Establezca el valor **ProviderType** en **app-proxy** para la tunelización de la capa de la aplicación o **packet-tunnel** para la tunelización de la capa de paquetes. Si no tiene claro qué valor usar, consulte la documentación de su proveedor de VPN.
  - **Direcciones URL de Safari que habilitarán esta VPN**: agregue una o varias direcciones URL de sitios web. Si se usa el explorador Safari en el dispositivo para ir a estas direcciones URL, la conexión VPN se establece automáticamente.

- **VPN a petición**: configure reglas condicionales que controlan cuándo se inicia la conexión VPN. Por ejemplo, cree una condición en la que la conexión VPN solo se usa cuando un dispositivo no está conectado a una red Wi-Fi de empresa. O bien, cree una nueva condición. Por ejemplo, si un dispositivo no puede acceder a un dominio de búsqueda DNS que escriba, no se iniciará la conexión VPN.

  - **SSID o dominios de búsqueda de DNS**: seleccione si esta condición usará **SSID** de red inalámbrica o **dominios de búsqueda de DNS**. Elija **Agregar** para configurar uno o varios SSID o dominios de búsqueda.
  - **Sondeo de cadena de dirección URL**: opcional. Escriba una dirección URL que la regla usará como prueba. Si el dispositivo con este perfil accede a esta dirección URL sin redireccionamiento, se inicia la conexión VPN. Además, el dispositivo se conecta a la dirección URL de destino. El usuario no ve el sitio de sondeo de cadena de dirección URL. Un ejemplo de un sondeo de cadena de dirección URL es la dirección de un servidor web de auditoría que comprueba el cumplimiento del dispositivo antes de conectarse a la VPN. Otra posibilidad es que la dirección URL compruebe la capacidad de la VPN para conectarse a un sitio antes de conectar el dispositivo a la dirección URL de destino a través de VPN.
  - **Acción del dominio**: elija uno de los elementos siguientes:
    - Conectarse si es necesario
    - No conectarse nunca
  - **Acción**: elija uno de los elementos siguientes:
    - Conectar
    - Evaluar conexión
    - Ignorar
    - Desconectar

## <a name="proxy-settings"></a>Configuración del proxy

Si usa un proxy, configure las opciones siguientes. La configuración de proxy no está disponible para las conexiones VPN de Zscaler.  

- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **URL del servidor proxy** (por ejemplo, `http://proxy.contoso.com`) que incluye el archivo de configuración.
- **Dirección**: escriba la dirección IP del nombre de host completo del servidor proxy.
- **Número de puerto**: especifique el número de puerto asociado al servidor proxy.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

Configure las opciones de VPN en dispositivos [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [MacOS](vpn-settings-macos.md)y [Windows 10](vpn-settings-windows-10.md) .
