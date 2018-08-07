---
title: Configuración de Wi-Fi de Microsoft Intune para dispositivos que ejecutan iOS
titleSuffix: ''
description: Aprenda a configurar la Wi-Fi de Intune en dispositivos que ejecutan iOS
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4b723bd23681d98463adae83be5f74b556dc779e
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321159"
---
# <a name="wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>Configuración de Wi-Fi para dispositivos iOS en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se muestra la configuración de Wi-Fi que puede configurar en Microsoft Intune para dispositivos que ejecutan iOS.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Configuración de Wi-Fi para perfiles básico y de empresa

- **Nombre de red**: escriba un nombre para esta conexión Wi-Fi. Este es el nombre que ven los usuarios cuando exploran la lista de conexiones disponibles en sus dispositivos.
- **SSID**: abreviatura de identificador de conjunto de servicios. Este es el nombre real de la red inalámbrica a la que se conectan los dispositivos. Con todo, los usuarios solo ven el nombre de red que ha configurado al elegir la conexión.
- **Conectar automáticamente**: el dispositivo se conecta siempre que está dentro del rango de alcance de esta red.
- **Red oculta**: impide que esta red se muestre en la lista de redes disponibles en el dispositivo.
- **Clave compartida previamente** - 
- **Configuración de proxy**: elija entre:
    - **Ninguna**: no se configura ningún valor de proxy.
    - **Manual**: especifique la **dirección del servidor proxy** (como una dirección IP) y su **número de puerto** asociado.
    - **Automática**: use un archivo para configurar el servidor proxy. Escriba la **URL del servidor proxy** (por ejemplo, **http://proxy.contoso.com**) que contiene el archivo de configuración.

## <a name="wi-fi-settings-for-basic-profiles-only"></a>Configuración de Wi-Fi solo para perfiles básicos

- **Tipo de seguridad**: seleccione el protocolo de seguridad que se usará para autenticarse en la red Wi-Fi. Las opciones son:
    - **Open (sin autenticación)**: use esta opción solo si la red es segura.
    - **WPA o WPA2 - Personal**
    - **WEP**

## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>Configuración de Wi-Fi solo para perfiles de empresa

- **Tipo de EAP**: elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras:
    - **EAP-FAST**
    - **EAP-SIM**
    - **EAP-TLS**
    - **EAP-TTLS**
    - **LEAP**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Opciones adicionales cuando elige un tipo de EAP


|Nombre de la configuración|Más información|Se debe usar cuando:|
|--------------|-------------|----------|
|**Configuración de las credenciales de acceso protegido (PAC)**|Seleccione esta opción para usar credenciales de acceso protegido para establecer un túnel autenticado entre el cliente y el servidor de autenticación. Seleccione una de las siguientes opciones:<br>- **Usar (PAC)**: usa un archivo PAC existente si está presente.<br>- **Usar y aprovisionar PAC**: aprovisiona el archivo PAC en los dispositivos.<br>- **Usar y aprovisionar PAC anónimamente**: aprovisiona el archivo PAC para sus dispositivos y garantiza que lo hace sin autenticar el servidor.|El tipo de EAP es **EAP-FAST**.|

#### <a name="server-trust"></a>Confianza del servidor


|Nombre de la configuración|Más información|Se debe usar cuando:|
|--------------|-------------|----------|
|**Nombres de servidor de certificados**|Especifique uno o más nombres comunes usados en los certificados emitidos por su entidad de certificación de confianza (CA). Si proporciona esta información, puede omitir el cuadro de diálogo de confianza dinámica que se muestra en los dispositivos de los usuarios cuando se conectan a esta red Wi-Fi.|El tipo de EAP es **EAP-TLS**, **EAP-TTLS** o **PEAP**.|
|**Certificado raíz para validación del servidor**|Seleccione el perfil de certificado raíz de confianza que se usa para autenticar la conexión. |El tipo de EAP es **EAP-TLS**, **EAP-TTLS** o **PEAP**|
|**Privacidad de identidad (identidad externa)**|Especifique el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.|El tipo de EAP es **PEAP**.|


#### <a name="client-authentication"></a>Autenticación de cliente


| Nombre de la configuración | Más información | Se debe usar cuando: |
|---|---|---|
| **Certificado cliente para la autenticación del cliente (certificado de identidad)**** |  Seleccione el perfil de certificado SCEP o PKCS que se usa para autenticar la conexión.  |    El tipo de EAP es **EAP-TLS**.    |
| **Método de autenticación** | Seleccione el método de autenticación para la conexión:<br>- **Certificados**: para seleccionar el certificado de cliente SCEP o PKCS que es el certificado de identidad presentado al servidor.<br><br>- **Nombre de usuario y contraseña** para especificar un método de autenticación diferente. <br><br>Si seleccionó **Nombre de usuario y contraseña**, configure:<br><br>-  **Método que no es EAP (identidad interna)** y, luego, seleccione cómo se autentica la conexión desde:<br>- **Ninguno**<br>- **Contraseña no cifrada (PAP)**<br>- **Protocolo de autenticación por desafío mutuo (CHAP)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP versión 2 (MS-CHAP v2)**<br>Las opciones disponibles dependen del tipo de EAP seleccionado.<br><br>**y**<br><br>- **Método que no es EAP (identidad interna)**: especifique el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro. | El tipo de EAP es **EAP-TTLS** o *. |

