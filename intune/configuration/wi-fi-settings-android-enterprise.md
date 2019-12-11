---
title: Configuración de Wi-Fi en Microsoft Intune para dispositivos que ejecutan Android Enterprise y el Quiosco de Android | Microsoft Docs
description: Cree o agregue un perfil de configuración de dispositivos Wi-Fi para Android Enterprise y el Quiosco de Android. Vea las diferentes configuraciones, como la adición de certificados, la elección de un tipo EAP y la selección de un método de autenticación en Microsoft Intune. Para dispositivos del quiosco, escriba también la clave precompartida de la red.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: maholdaa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04d35f49f9e07cb72a1fea92210b05e0a95ec256
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74390804"
---
# <a name="add-wi-fi-settings-for-android-enterprise-dedicated-and-fully-managed-devices-in-microsoft-intune"></a>Agregar configuración de Wi-Fi para dispositivos Android Enterprise dedicados y totalmente administrados en Microsoft Intune

Puede crear un perfil con una configuración específica de Wi-Fi y después implementar este perfil en los dispositivos Android Enterprise totalmente administrados y dedicados. Microsoft Intune ofrece muchas características, incluidas la autenticación en la red, con el uso de una clave precompartida, y mucho más.

Ambas se describen en este artículo. [Adición y uso de la configuración de Wi-Fi en los dispositivos en Microsoft Intune](wi-fi-settings-configure.md) incluye más información acerca de la característica Wi-Fi en Microsoft Intune.

## <a name="before-you-begin"></a>Antes de comenzar

[Creación de un perfil de dispositivo en Microsoft Intune](wi-fi-settings-configure.md#create-a-device-profile).

## <a name="device-owner-only"></a>Solo el propietario del dispositivo

Seleccione esta opción si va a implementar en un dispositivo Android Enterprise dedicado o totalmente administrado.  Los dispositivos Android Enterprise dedicados y totalmente administrados admiten actualmente la implementación de certificados SCEP, pero no PKCS.

### <a name="basic"></a>Básica

- **Tipo de Wi-Fi**: elija **Básico**.
- **Nombre de red**: escriba un nombre para esta conexión Wi-Fi. Los usuarios finales verán este nombre cuando busquen en su dispositivo las conexiones Wi-Fi disponibles. Por ejemplo, escriba **Contoso WiFi**.
- **SSID**: escriba el **identificador del conjunto de servicios**, que es el nombre real de la red inalámbrica a la que se conectan los dispositivos. Sin embargo, los usuarios solo ven el **nombre de red** que ha configurado al elegir la conexión.
- **Red oculta**: elija **Habilitar** para ocultar esta red en la lista de redes disponibles en el dispositivo. No se difunde el SSID. Elija **Deshabilitar** para mostrar esta red en la lista de redes disponibles en el dispositivo.
- **Tipo de Wi-Fi**: seleccione el protocolo de seguridad para autenticarse en la red Wi-Fi. Las opciones son:

  - **Abierta (sin autenticación)** : use esta opción solo si la red no es segura.
  - **Clave precompartida WEP**: escriba la contraseña en **Clave precompartida**. Una vez configurada la red de su organización, también se configuran una contraseña o una clave de red. Escriba esta contraseña o clave de red para el valor PSK.
  - **Clave precompartida WPA**: escriba la contraseña en **Clave precompartida**. Una vez configurada la red de su organización, también se configuran una contraseña o una clave de red. Escriba esta contraseña o clave de red para el valor PSK.

### <a name="enterprise"></a>Enterprise

- **Tipo de Wi-Fi**: elija **Empresa**.
- **SSID**: escriba el **identificador del conjunto de servicios**, que es el nombre real de la red inalámbrica a la que se conectan los dispositivos. Sin embargo, los usuarios solo ven el **nombre de red** que ha configurado al elegir la conexión.
- **Red oculta**: elija **Habilitar** para ocultar esta red en la lista de redes disponibles en el dispositivo. No se difunde el SSID. Elija **Deshabilitar** para mostrar esta red en la lista de redes disponibles en el dispositivo.
- **Tipo de EAP**: elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras. Las opciones son:

  - **EAP-TLS**: especifique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Cuando el cliente se conecta a la red, este certificado se presenta al servidor y autentica la conexión.

    - **Autenticación de cliente** - **Certificado para la autenticación de cliente (certificado de identidad)** : elija el perfil de certificado de cliente SCEP que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

    - **Privacidad de identidad (identidad interna)** : escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

  - **EAP-TTLS**: especifique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Cuando el cliente se conecta a la red, este certificado se presenta al servidor y autentica la conexión.

    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:

      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. Indique también:
        - **Método que no es EAP (identidad interna)** : seleccione cómo se autentica la conexión. Asegúrese de elegir el mismo protocolo que está configurado en su red Wi-Fi. Las opciones son:

          - **Contraseña no cifrada (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP versión 2 (MS-CHAP v2)**

      - **Certificados**: elija el perfil de certificado de cliente SCEP que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

      - **Privacidad de identidad (identidad interna)** : escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

  - **PEAP**: especifique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Cuando el cliente se conecta a la red, este certificado se presenta al servidor y autentica la conexión.

    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:

      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. Indique también:
        - **Método de autenticación que no es EAP (identidad interna)** : seleccione cómo se autentica la conexión. Asegúrese de elegir el mismo protocolo que está configurado en su red Wi-Fi. Las opciones son:

          - **Ninguno**
          - **Microsoft CHAP versión 2 (MS-CHAP v2)**

      - **Certificados**: elija el perfil de certificado de cliente SCEP que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

      - **Privacidad de identidad (identidad interna)** : escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

## <a name="work-profile-only"></a>Solo perfil de trabajo

### <a name="basic"></a>Básica

- **Tipo de Wi-Fi**: elija **Básico**.
- **SSID**: escriba el **identificador del conjunto de servicios**, que es el nombre real de la red inalámbrica a la que se conectan los dispositivos. Sin embargo, los usuarios solo ven el **nombre de red** que ha configurado al elegir la conexión.
- **Red oculta**: elija **Habilitar** para ocultar esta red en la lista de redes disponibles en el dispositivo. No se difunde el SSID. Elija **Deshabilitar** para mostrar esta red en la lista de redes disponibles en el dispositivo.

### <a name="enterprise"></a>Enterprise

- **Tipo de Wi-Fi**: elija **Empresa**.
- **SSID**: escriba el **identificador del conjunto de servicios**, que es el nombre real de la red inalámbrica a la que se conectan los dispositivos. Sin embargo, los usuarios solo ven el **nombre de red** que ha configurado al elegir la conexión.
- **Red oculta**: elija **Habilitar** para ocultar esta red en la lista de redes disponibles en el dispositivo. No se difunde el SSID. Elija **Deshabilitar** para mostrar esta red en la lista de redes disponibles en el dispositivo.
- **Tipo de EAP**: elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras. Las opciones son:

  - **EAP-TLS**: especifique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Cuando el cliente se conecta a la red, este certificado se presenta al servidor y autentica la conexión.

    - **Autenticación de cliente** - **Certificado para la autenticación de cliente (certificado de identidad)** : elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

    - **Privacidad de identidad (identidad interna)** : escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

  - **EAP-TTLS**: especifique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Cuando el cliente se conecta a la red, este certificado se presenta al servidor y autentica la conexión.

    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:

      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. Indique también:
        - **Método que no es EAP (identidad interna)** : seleccione cómo se autentica la conexión. Asegúrese de elegir el mismo protocolo que está configurado en su red Wi-Fi. Las opciones son:

          - **Contraseña no cifrada (PAP)**
          - **Microsoft CHAP (MS-CHAP)**
          - **Microsoft CHAP versión 2 (MS-CHAP v2)**

      - **Certificados**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

      - **Privacidad de identidad (identidad interna)** : escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

  - **PEAP**: especifique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Cuando el cliente se conecta a la red, este certificado se presenta al servidor y autentica la conexión.

    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:

      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. Indique también:
        - **Método de autenticación que no es EAP (identidad interna)** : seleccione cómo se autentica la conexión. Asegúrese de elegir el mismo protocolo que está configurado en su red Wi-Fi. Las opciones son:

          - **Ninguno**
          - **Microsoft CHAP versión 2 (MS-CHAP v2)**

      - **Certificados**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

      - **Privacidad de identidad (identidad interna)** : escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero no hacen nada. Después, [asigne este perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).

También puede crear perfiles Wi-Fi para dispositivos [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md), [macOS](wi-fi-settings-macos.md), [Windows 10](wi-fi-settings-windows.md) y [Windows 8.1](wi-fi-settings-import-windows-8-1.md).
