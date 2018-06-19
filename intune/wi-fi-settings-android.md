---
title: Configuración de Wi-Fi de Microsoft Intune para dispositivos que ejecutan Android
titleSuffix: ''
description: Obtenga más información sobre cómo configurar la Wi-Fi de Intune en dispositivos que ejecutan Android y Android for Work.
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
ms.openlocfilehash: ee82da997a794bb2f65929a6fd9e0de0cc776a6e
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831068"
---
# <a name="configure-wi-fi-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>Configuración de Wi-Fi en Microsoft Intune para dispositivos que ejecutan Android y Android for Work  

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se muestra la configuración de Wi-Fi que puede configurar en Microsoft Intune para dispositivos que ejecutan Android y Android for Work.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Configuración de Wi-Fi para perfiles básico y de empresa

Las siguientes opciones de Wi-Fi están disponibles para dispositivos Android y Android for Work:

- **Nombre de red**: escriba un nombre para esta conexión Wi-Fi. Este es el nombre que ven los usuarios cuando exploran la lista de conexiones disponibles en sus dispositivos.
- **SSID**: abreviatura de identificador de conjunto de servicios. Este es el nombre real de la red inalámbrica a la que se conectan los dispositivos. Con todo, los usuarios solo ven el nombre de red que ha configurado al elegir la conexión.
- **Conectar automáticamente**: el dispositivo se conecta siempre que está dentro del rango de alcance de esta red.
- **Red oculta**: impide que esta red se muestre en la lista de redes disponibles en el dispositivo.


## <a name="wi-fi-settings-for-enterprise-profiles-only"></a>Configuración de Wi-Fi solo para perfiles de empresa

- **Tipo de EAP**: elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras:
    - **EAP-TLS**
    - **EAP-TTLS**
    - **PEAP**

### <a name="further-options-when-you-choose-an-eap-type"></a>Opciones adicionales cuando elige un tipo de EAP

#### <a name="server-trust"></a>Confianza del servidor



|Nombre de la configuración|Más información|Se debe usar cuando:|
|-------------|---------------|-----------|
|**Nombres de servidor de certificados**|Especifique uno o más nombres comunes usados en los certificados emitidos por su entidad de certificación de confianza (CA). Si proporciona esta información, puede omitir el cuadro de diálogo de confianza dinámica que se muestra en los dispositivos de los usuarios cuando se conectan a esta red Wi-Fi.|El tipo de EAP es **EAP-TLS** o **EAP-TTLS**.|
|**Certificado raíz para validación del servidor**|Seleccione el perfil de certificado raíz de confianza que se usa para autenticar la conexión. |El tipo de EAP es **EAP-TLS**, **EAP-TTLS** o **PEAP**|
|**Privacidad de identidad (identidad externa)**|Especifique el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.|El tipo de EAP es **PEAP**.|


#### <a name="client-authentication"></a>Autenticación de cliente


|                                     Nombre de la configuración                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Más información                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                            Se debe usar cuando:                            |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| <strong>Certificado cliente para la autenticación del cliente (certificado de identidad)</strong> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Seleccione el perfil de certificado SCEP o PKCS que se usa para autenticar la conexión.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |              El tipo de EAP es <strong>EAP-TLS</strong>.              |
|                        <strong>Método de autenticación</strong>                        | Seleccione el método de autenticación para la conexión:<br>- <strong>Certificados</strong>: para seleccionar el certificado de cliente SCEP o PKCS que es el certificado de identidad presentado al servidor.<br><br>- <strong>Nombre de usuario y contraseña</strong> para especificar un método de autenticación diferente. <br><br>Si seleccionó <strong>Nombre de usuario y contraseña</strong>, configure:<br><br>-  <strong>Método que no es EAP (identidad interna)</strong> y, luego, seleccione cómo se autentica la conexión desde:<br>- <strong>Ninguno</strong><br>- <strong>Contraseña no cifrada (PAP)</strong><br>- <strong>Protocolo de autenticación por desafío mutuo (CHAP)</strong><br>- <strong>Microsoft CHAP (MS-CHAP)</strong><br>- <strong>Microsoft CHAP versión 2 (MS-CHAP v2)</strong><br>Las opciones disponibles dependen del tipo de EAP seleccionado.<br><br><strong>y</strong><br><br>- <strong>Método que no es EAP (identidad interna)</strong>: especifique el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro. | El tipo de EAP es <strong>EAP-TTLS</strong> o <strong>PEAP</strong>. |

