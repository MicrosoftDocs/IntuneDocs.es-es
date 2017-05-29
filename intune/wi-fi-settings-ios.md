---
title: "Configuración de Wi-Fi de Intune para dispositivos iOS"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda sobre la configuración de Intune que puede usar para configurar conexiones Wi-Fi en dispositivos iOS."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89229a5e-3421-4221-a62f-fa800620cc0d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: edd7cfc8ed6e444105f58002b3ba7c0086fde518
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>Configuración de Wi-Fi para dispositivos iOS en Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]



## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Configuración de Wi-Fi para perfiles básico y de empresa

- **Nombre de red**: escriba un nombre para esta conexión Wi-Fi. Este es el nombre que los usuarios verán cuando exploren la lista de conexiones disponibles en sus dispositivos.
- **SSID**: abreviatura de identificador de conjunto de servicios. Este es el nombre real de la red inalámbrica a la que se conectarán los dispositivos. Sin embargo, los usuarios verán únicamente el nombre de red que creó anteriormente cuando eligió la conexión.
- **Conectar automáticamente**: el dispositivo se conecta siempre que está dentro del rango de alcance de esta red.
- **Red oculta**: impide que esta red se muestre en la lista de redes disponibles en el dispositivo.
- **Configuración de proxy**: elija entre:
    - **Ninguna**: no se configura ninguna configuración de proxy.
    - **Manual**: especifique la **dirección del servidor proxy** (como una dirección IP) y su **número de puerto** asociado.
    - **Automática**: use un archivo para configurar el servidor proxy. Escriba la **dirección URL del servidor proxy** (por ejemplo **http://proxy.contoso.com**) que contiene el archivo de configuración.

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
|**Nombres de servidor de certificados**|Especifique uno o más nombres comunes usados en los certificados emitidos por su entidad de certificación de confianza (CA). Si proporciona esta información, puede omitir el cuadro de diálogo de confianza dinámicas que se muestra en los dispositivos de los usuarios finales cuando se conectan a esta red Wi-Fi.|El tipo de EAP es **EAP-TLS**, **EAP-TTLS** o **PEAP**.|
|**Certificado raíz para validación del servidor**|Seleccione el perfil de certificado raíz de confianza que se usa para autenticar la conexión. |El tipo de EAP es **EAP-TLS**, **EAP-TTLS** o **PEAP**|
|**Privacidad de identidad (identidad externa)**|Especifique el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.|El tipo de EAP es **PEAP**.|


#### <a name="client-authentication"></a>Autenticación de cliente


|Nombre de la configuración|Más información|Se debe usar cuando:|
|--------------|-------------|----------|
|**Certificado cliente para la autenticación del cliente (certificado de identidad)**|Seleccione el perfil de certificado SCEP o PKCS que se usa para autenticar la conexión.|El tipo de EAP es **EAP-TLS**.|
|**Método de autenticación**|Seleccione el método de autenticación para la conexión:<br>- **Certificados**: para seleccionar el certificado de cliente SCEP o PKCS que es el certificado de identidad presentado al servidor.<br><br>- **Nombre de usuario y contraseña** para especificar un método de autenticación diferente. <br><br>Si seleccionó **Nombre de usuario y contraseña**, configure:<br><br>-  **Método que no es EAP (identidad interna)** y luego seleccione cómo se autenticará la conexión desde:<br>- **Ninguno**<br>- **Contraseña no cifrada (PAP)**<br>- **Protocolo de autenticación por desafío mutuo (CHAP)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP versión 2 (MS-CHAP v2)**<br>Las opciones disponibles dependen del tipo de EAP seleccionado.<br><br>**y**<br><br>- **Método que no es EAP (identidad interna)**: especifique el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.|El tipo de EAP es **EAP-TTLS** o *.

