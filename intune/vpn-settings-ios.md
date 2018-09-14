---
title: Configuración de VPN para dispositivos iOS en Microsoft Intune - Azure | Microsoft Docs
description: Ver las opciones de configuración de red privada virtual (VPN) disponibles, así como los detalles de conexión, los métodos de autenticación y la tunelización dividida en las opciones básicas; la configuración de VPN personalizada con el identificador y los pares de clave y valor; la configuración de VPN por aplicación que incluye las direcciones URL de Safari y las VPN a petición con dominios de búsqueda DNS o SSID; y la configuración de proxy para incluir un script de configuración, una dirección IP o FQDN y un puerto TCP en Microsoft Intune en dispositivos que ejecutan iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: deb6a230573ff20237e6eee386052baba472832a
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313877"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>Configuración de VPN en Microsoft Intune para dispositivos que ejecutan iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se muestra la configuración de Intune que puede usar para configurar conexiones VPN en dispositivos que ejecutan iOS.

Según la configuración que elija, no todos los valores de la lista siguiente se podrán configurar.

## <a name="base-vpn-settings"></a>Configuración de VPN base
La configuración real que se ve en la lista siguiente depende del tipo de conexión de VPN que se seleccione.  
- **Nombre de la conexión**: los usuarios finales verán este nombre cuando exploren su dispositivo para obtener una lista de las conexiones VPN disponibles.
- **Nombre de dominio personalizado** (solo Zscaler): rellene previamente el campo de inicio de sesión de la aplicación Zscaler con el dominio al que pertenecen los usuarios. Por ejemplo, si un nombre de usuario es **Joe@contoso.net**, el dominio **contoso.net** aparecería de forma estática en el campo al abrir la aplicación. Si no escribe un nombre de dominio, se usará la parte del dominio del UPN en Azure Active Directory.
- **Dirección IP o FQDN**: la dirección IP o el nombre de dominio completo (FQDN) del servidor VPN al que se conectan los dispositivos. Por ejemplo, especifique **192.168.1.1** o **vpn.contoso.com**. 
- **Nombre de la organización en la nube** (solo Zscaler): escriba el nombre de la nube donde se aprovisiona la organización. Examine la dirección URL que usa para iniciar sesión en Zscaler para buscar el nombre.  
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
  - **Zscaler**: requiere la integración de Zscaler Private Access (ZPA) con la cuenta de Azure Active Directory. Para obtener instrucciones detalladas, vea la [documentación de Zscaler](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO). 
  - **VPN personalizada**    

    > [!NOTE]
    > Cisco, Citrix, F5 y Palo Alto han anunciado que sus clientes heredados no funcionarán en la próxima versión de iOS 12. Tendrá que migrar a las aplicaciones nuevas tan pronto como sea posible. Para obtener más información, vea el [blog del equipo de soporte técnico de Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

* **Direcciones URL excluidas** (solo Zscaler): cuando se conecta a la VPN de Zscaler, las direcciones URL de la lista son accesibles desde fuera de la nube de Zscaler. 

- **Tunelización dividida**: puede **Habilitar** o **Deshabilitar** esta opción para que los dispositivos decidan qué conexión usar en función del tráfico. Por ejemplo, un usuario en un hotel usa la conexión VPN para acceder a los archivos de trabajo, pero usa la red normal del hotel para la exploración web habitual.   

## <a name="custom-vpn-settings"></a>Configuración de VPN personalizada

Si seleccionó **VPN personalizada** como tipo de conexión, configure las opciones siguientes. Estas opciones también son visibles para las conexiones de Zscaler y Citrix.

- **Identificador de VPN**: es un identificador de la aplicación VPN que usa. Lo suministra el proveedor de VPN.
- **Especifique pares clave-valor para los atributos de la VPN personalizada**: agregue o importe **Claves** y **Valores** que personalicen la conexión VPN. De nuevo, estos valores los suministra normalmente el proveedor de VPN.

## <a name="automatic-vpn-settings"></a>Configuración automática de VPN

- **VPN por aplicación**: si elige esta opción, se habilita la VPN por aplicación, lo que permite que la conexión VPN se active automáticamente cuando se abren determinadas aplicaciones. Además de elegir esta opción, también será necesario asociar las aplicaciones con este perfil de VPN. Consulte las [instrucciones para configurar una VPN por aplicación en iOS](vpn-setting-configure-per-app.md) para obtener más detalles. 
  - La opción **Tipo de proveedor** solo está disponible para Pulse Secure y VPN personalizada.
  - Al usar perfiles de **VPN por aplicación** de iOS con Pulse Secure o una VPN personalizada, puede elegir usar tunelización de capa de aplicación (app-proxy) o tunelización de nivel de paquete (packet-tunnel). Establezca el valor **ProviderType** en **app-proxy** para la tunelización de capa de aplicación o en **packet-tunnel** para la tunelización de nivel de paquete. Si no está seguro de qué valor usar, consulte la documentación de su proveedor de VPN. 
  - **Direcciones URL de Safari que habilitarán esta VPN**: seleccione esta opción para agregar una o varias direcciones URL de sitios web. Si se usa el explorador Safari en el dispositivo para ir a estas direcciones URL, la conexión VPN se establece automáticamente.

- **VPN a petición**: le permite configurar reglas condicionales que controlan cuándo se inicia la conexión VPN. Por ejemplo, puede crear una condición en la que la conexión VPN solo se usa cuando un dispositivo no está conectado a una red Wi-Fi de empresa. También puede crear una condición en la que, si un dispositivo no puede tener acceso a un dominio de búsqueda DNS especificado, no se iniciará la conexión VPN.

  - **SSID o dominios de búsqueda de DNS**: seleccione si esta condición usará **SSID** de red inalámbrica o **dominios de búsqueda de DNS**. Elija **Agregar** para configurar uno o varios SSID o dominios de búsqueda.
  - **Sondeo de cadena de dirección URL**: opcional. Escriba una dirección URL que la regla usará como prueba. Si el dispositivo en el que está instalado este perfil puede acceder a esta dirección URL sin redireccionamiento, se iniciará la conexión VPN y el dispositivo se conectará a la dirección URL de destino. El usuario no ve el sitio de sondeo de cadena de dirección URL. Un ejemplo de un sondeo de cadena de dirección URL es la dirección de un servidor web de auditoría que comprueba el cumplimiento del dispositivo antes de conectarse a la VPN. Otra posibilidad es que la dirección URL compruebe la capacidad de la VPN para conectarse a un sitio antes de conectar el dispositivo a la dirección URL de destino a través de VPN.
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

- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **URL del servidor proxy** (por ejemplo, **http://proxy.contoso.com**) que contiene el archivo de configuración.
- **Dirección**: escriba la dirección IP del nombre de host completo del servidor proxy.
- **Número de puerto**: especifique el número de puerto asociado al servidor proxy.

## <a name="next-step"></a>Paso siguiente
[Crear perfiles de VPN en Intune](vpn-settings-configure.md)  
