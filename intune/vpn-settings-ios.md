---
title: 'Agregar una configuración de VPN a dispositivos iOS en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue o cree un perfil de configuración de VPN mediante opciones de configuración de red privada virtual (VPN), incluidos los detalles de conexión, los métodos de autenticación y la tunelización dividida en la configuración básica; la configuración de VPN personalizada con el identificador y los pares clave-valor; la configuración de VPN por aplicación que incluye las direcciones URL de Safari y las VPN a petición con dominios de búsqueda DNS o SSID; y la configuración de proxy para incluir un script de configuración, una dirección IP o FQDN y un puerto TCP en Microsoft Intune en dispositivos que ejecutan iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b794ec40d05358ddd1aa3179c2f4060b2cd6fe1d
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236516"
---
# <a name="configure-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Configuración de VPN en dispositivos iOS en Microsoft Intune

Microsoft Intune incluye muchas opciones de configuración de VPN que se pueden implementar en los dispositivos iOS. Estas opciones se usan para crear y configurar conexiones VPN a la red de su organización. Ambas se describen en este artículo. Algunas opciones solo están disponibles para algunos clientes VPN, como Citrix, Zscaler y otros.

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
  
- **Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:
  - **Check Point Capsule VPN**
  - **Cisco Legacy AnyConnect**: para la versión 4.0.5x y versiones anteriores de la aplicación [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924).
  - **Cisco AnyConnect**: para la versión 4.0.7x y versiones anteriores de la aplicación [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690).
  - **SonicWall Mobile Connect**
  - **F5 Access Legacy**: aplicable a la versión 2.1 de la aplicación F5 Access y versiones anteriores.
  - **F5 Access**: aplicable a la versión 3.0 de la aplicación F5 Access y versiones posteriores.
  - **GlobalProtect de Palo Alto Networks (Legacy)**: aplicable a la aplicación GlobalProtect de Palo Alto Networks, versión 4.1 y anteriores.
  - **GlobalProtect de Palo Alto Networks**: aplicable a la aplicación GlobalProtect de Palo Alto Networks, versión 5.0 y posteriores.
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **Citrix VPN**
  - **Citrix SSO**
  - **Zscaler**: requiere la integración de Zscaler Private Access (ZPA) con la cuenta de Azure AD. Para obtener instrucciones detalladas, vea la [documentación de Zscaler](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO). 
  - **VPN personalizada**    

    > [!NOTE]
    > Cisco, Citrix, F5 y Palo Alto han anunciado que sus clientes heredados no funcionan en iOS 12. Tendrá que migrar a las aplicaciones nuevas tan pronto como sea posible. Para obtener más información, vea el [blog del equipo de soporte técnico de Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

* **Direcciones URL excluidas** (solo Zscaler): cuando se conecta a la VPN de Zscaler, las direcciones URL de la lista son accesibles desde fuera de la nube de Zscaler. 

- **Tunelización dividida**: puede **Habilitar** o **Deshabilitar** esta opción para que los dispositivos decidan qué conexión usar en función del tráfico. Por ejemplo, un usuario en un hotel usa la conexión VPN para acceder a los archivos de trabajo, pero usa la red normal del hotel para la exploración web habitual.

- **Habilitar el control de acceso a la red (NAC)**: esta configuración es un marcador de posición para los clientes VPN, como Citrix, para permitir que haya un identificador de dispositivo en el perfil de VPN a fin de usarlo con el control de acceso a la red (NAC). Si elige **Acepto**, este identificador de dispositivo se incluirá en el perfil de VPN. Actualmente, no hay ningún cliente VPN ni solución de asociado de NAC que admita este nuevo identificador, por lo que los dispositivos podrán conectarse a la VPN independientemente del estado de cumplimiento. Actualizaremos este documento cuando nuestros asociados admitan el identificador.

  Detalles importantes:  

  - Si esta opción está habilitada, la VPN se desconecta cada 24 horas.
  - El identificador de dispositivo forma parte del perfil, pero no se puede ver en Intune ni en el perfil. Microsoft no almacena este identificador en ningún lugar ni tampoco lo comparte. Una vez que los asociados de VPN lo admitan, el cliente VPN, como Citrix SSO, puede obtener el identificador y consultar Intune para confirmar que el dispositivo está inscrito y si el perfil de VPN es conforme o no.
  - Para quitar esta configuración, vuelva a crear el perfil y no seleccione **Acepto**. Después, vuelva a asignar el perfil.

## <a name="custom-vpn-settings"></a>Configuración de VPN personalizada

Si seleccionó **VPN personalizada** como tipo de conexión, configure las opciones siguientes. Estas opciones también son visibles para las conexiones de Zscaler y Citrix.

- **Identificador de VPN**: es un identificador de la aplicación VPN que usa. Lo suministra el proveedor de VPN.
- **Especifique pares clave-valor para los atributos de la VPN personalizada**: agregue o importe **Claves** y **Valores** que personalicen la conexión VPN. Recuerde que estos valores los suele suministrar el proveedor de VPN.

## <a name="automatic-vpn-settings"></a>Configuración automática de VPN

- **VPN por aplicación**: permite la VPN por aplicación. Permite que la conexión VPN se desencadene de forma automática cuando se abren determinadas aplicaciones. También se asocian las aplicaciones con este perfil de VPN. Para obtener más información, vea las [instrucciones para configurar una VPN por aplicación para iOS](vpn-setting-configure-per-app.md).
  - **Tipo de proveedor**: solo está disponible para Pulse Secure y VPN personalizada.
  - Al usar perfiles de **VPN por aplicación** de iOS con Pulse Secure o una VPN personalizada, elija la tunelización de la capa de la aplicación (app-proxy) o la tunelización de nivel de paquete (packet-tunnel). Establezca el valor **ProviderType** en **app-proxy** para la tunelización de la capa de la aplicación o **packet-tunnel** para la tunelización de la capa de paquetes. Si no tiene claro qué valor usar, consulte la documentación de su proveedor de VPN.
  - **Direcciones URL de Safari que habilitarán esta VPN**: agregue una o varias direcciones URL de sitios web. Si se usa el explorador Safari en el dispositivo para ir a estas direcciones URL, la conexión VPN se establece automáticamente.

- **VPN a petición**: configure reglas condicionales que controlan cuándo se inicia la conexión VPN. Por ejemplo, cree una condición en la que la conexión VPN solo se usa cuando un dispositivo no está conectado a una red Wi-Fi de empresa. O bien, cree una condición en la que, si un dispositivo no puede acceder a un dominio de búsqueda DNS que escriba, no se iniciará la conexión VPN.

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

## <a name="next-step"></a>Paso siguiente
[Crear perfiles de VPN en Intune](vpn-settings-configure.md)  
