---
title: Configuración de Wi-Fi de Microsoft Intune para dispositivos que ejecutan Android
titleSuffix: ''
description: Aprenda a configurar la Wi-Fi de Intune en dispositivos que ejecutan Android.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0157815322488525a4ce7a3d6d2c90cbb8d3ff2a
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905673"
---
# <a name="configure-wi-fi-settings-in-microsoft-intune-for-devices-running-android-android-work-profiles-and-android-kiosk-devices"></a>Configuración de Wi-Fi en Microsoft Intune para dispositivos que ejecutan Android, perfiles de trabajo Android y dispositivos de quiosco Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se muestra la configuración de Wi-Fi que puede configurar en Microsoft Intune para dispositivos que ejecutan Android y perfiles de trabajo Android.

## <a name="wi-fi-settings-for-basic-and-enterprise-profiles"></a>Configuración de Wi-Fi para perfiles básico y de empresa

Las siguientes opciones de Wi-Fi están disponibles para dispositivos Android y dispositivos de perfil de trabajo Android:

- **Nombre de red**: escriba un nombre para esta conexión Wi-Fi. Este es el nombre que ven los usuarios cuando exploran la lista de conexiones disponibles en sus dispositivos.
- **SSID**: abreviatura de identificador de conjunto de servicios. Este es el nombre real de la red inalámbrica a la que se conectan los dispositivos. Con todo, los usuarios solo ven el nombre de red que ha configurado al elegir la conexión.
- **Conectar automáticamente**: el dispositivo se conecta siempre que está dentro del rango de alcance de esta red.
- **Red oculta**: impide que esta red se muestre en la lista de redes disponibles en el dispositivo.

## <a name="wi-fi-settings-available-for-enterprise-kiosk-profiles"></a>Configuraciones de Wi-Fi disponibles para los perfiles de quiosco empresariales
- **Tipo de Wi-Fi**: estos tipos de configuración Wi-Fi solo están disponibles al elegir **Tipo de perfil** > **Solo propietario del dispositivo** > **Wi-Fi**.
    - **Abierta (sin autenticación)**
    - **Clave precompartida WEP**: debe proporcionar la contraseña en el cuadro **Clave precompartida**.
    - **Clave precompartida WPA**: debe proporcionar la contraseña en el cuadro **Clave precompartida**.

## <a name="wi-fi-settings-for-android-legacy-and-android-work-profiles-only"></a>Configuraciones de Wi-Fi solo para dispositivos obsoletos de Android y perfiles de trabajo Android

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

