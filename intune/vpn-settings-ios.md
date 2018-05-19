---
title: Configuración de VPN para dispositivos iOS en Microsoft Intune - Azure | Microsoft Docs
description: Ver las opciones de configuración de red privada virtual (VPN) disponibles, así como los detalles de conexión, los métodos de autenticación y la tunelización dividida en las opciones básicas; la configuración de VPN personalizada con el identificador y los pares de clave y valor; la configuración de VPN por aplicación que incluye las direcciones URL de Safari y las VPN a petición con dominios de búsqueda DNS o SSID; y la configuración de proxy para incluir un script de configuración, una dirección IP o FQDN y un puerto TCP en Microsoft Intune en dispositivos que ejecutan iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: eb87d75512d9f04abac9db256d0d968bb85116ef
ms.sourcegitcommit: 6a9830de768dd97a0e95b366fd5d2f93980cee05
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>Configuración de VPN en Microsoft Intune para dispositivos que ejecutan iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se muestra la configuración de Intune que puede usar para configurar conexiones VPN en dispositivos que ejecutan iOS.

Según la configuración que elija, no todos los valores de la lista siguiente se podrán configurar.

## <a name="base-vpn-settings"></a>Configuración de VPN base

- **Nombre de la conexión**: escriba un nombre para esta conexión. Los usuarios finales verán este nombre cuando exploren su dispositivo para ver una lista de conexiones VPN disponibles.
- **Dirección IP o FQDN**: indique la dirección IP o el nombre de dominio completo (FQDN) del servidor VPN al que se conectarán los dispositivos. Por ejemplo, especifique **192.168.1.1** o **vpn.contoso.com**.
- **Método de autenticación**: elija cómo se autenticarán los dispositivos en el servidor VPN. Las opciones son las siguientes:
  - **Certificados**: en **Certificado de autenticación**, seleccione un perfil de certificado SCEP o PKCS existente para autenticar la conexión. En [Configurar certificados](certificates-configure.md) se proporcionan algunas directrices sobre los perfiles de certificado.
  - **Nombre de usuario y contraseña**: los usuarios finales deben introducir un nombre de usuario y una contraseña para iniciar sesión en el servidor VPN.

    > [!NOTE]
    > Si el nombre de usuario y la contraseña se usan como método de autenticación para VPN Cisco IPsec, deben entregar la credencial SharedSecret a través de un perfil personalizado de Apple Configurator.
  
- **Tipo de conexión**: seleccione el tipo de conexión VPN de la siguiente lista de proveedores:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **Cisco Legacy AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **Citrix**
  - **VPN personalizada**

    > [!NOTE]
    > - Los perfiles de **VPN de Cisco Legacy AnyConnect** son para la versión 4.0.5x y versiones anteriores de la aplicación [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924)
    > - Los perfiles de **VPN de Cisco AnyConnect** son para la versión 4.0.7x y versiones anteriores de la aplicación [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690)

- **Tunelización dividida**: puede **Habilitar** o **Deshabilitar** esta opción para que los dispositivos decidan qué conexión usar en función del tráfico. Por ejemplo, un usuario en un hotel usa la conexión VPN para acceder a los archivos de trabajo, pero usa la red normal del hotel para la exploración web habitual.

## <a name="custom-vpn-settings"></a>Configuración de VPN personalizada

Si seleccionó **VPN personalizada** como tipo de conexión, configure también las siguientes opciones:

- **Identificador de VPN**: es un identificador de la aplicación VPN que usa. Lo suministra el proveedor de VPN.
- **Especifique pares clave-valor para los atributos de la VPN personalizada**: agregue o importe **claves** y **valores** que personalicen su conexión VPN. De nuevo, estos valores los suministra normalmente el proveedor de VPN.

## <a name="apps-per-app-vpn-settings"></a>Configuración de aplicaciones (VPN por aplicación)

- **VPN por aplicación**: habilite esta opción para usar las direcciones URL que permitirán la conexión VPN cuando se visiten desde el explorador Safari. Para configurar el VPN por aplicación, debe seleccionar **Certificados** como método de autenticación en la configuración de VPN base.
  - **Direcciones URL de Safari que habilitarán esta VPN**: seleccione esta opción para agregar una o varias direcciones URL de sitios web. Cuando se visiten estas direcciones URL, se habilitará la conexión VPN.

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

- **Script de configuración automática**: use un archivo para configurar el servidor proxy. Escriba la **URL del servidor proxy** (por ejemplo, **http://proxy.contoso.com**) que contiene el archivo de configuración.
- **Dirección**: escriba la dirección IP del nombre de host completo del servidor proxy.
- **Número de puerto**: especifique el número de puerto asociado al servidor proxy.

## <a name="next-step"></a>Paso siguiente
[Crear perfiles de VPN en Intune](vpn-settings-configure.md)
