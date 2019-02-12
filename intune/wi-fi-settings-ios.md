---
title: Configuración de Wi-Fi para dispositivos iOS en Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Cree o agregue un perfil de configuración de dispositivos Wi-Fi para dispositivos iOS. Vea las diferentes configuraciones, como la adición de certificados, la elección de un tipo EAP y la selección de un método de autenticación en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a17be2e6cb30612fbf8a91f63d3b99ed6c7e19b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837449"
---
# <a name="add-wi-fi-settings-for-ios-devices-in-microsoft-intune"></a>Adición de la configuración de Wi-Fi para dispositivos iOS en Microsoft Intune

Puede crear un perfil con una configuración específica de Wi-Fi y después implementar este perfil en los dispositivos iOS. Microsoft Intune ofrece muchas características, incluidas la autenticación en la red, agregar un certificado PKS o SCEP y muchas más.

Esta configuración de Wi-Fi se divide en dos categorías: configuración básica y configuración de nivel de empresa.

Ambas se describen en este artículo.

## <a name="before-you-begin"></a>Antes de comenzar

[Creación de un perfil de dispositivo en Microsoft Intune](device-profile-create.md).

## <a name="basic-profiles"></a>Perfiles básicos

- **Tipo de Wi-Fi**: Elija **Básica**.
- **Nombre de red**: escriba un nombre para esta conexión Wi-Fi. Este valor es el nombre que ven los usuarios cuando exploran la lista de conexiones disponibles en sus dispositivos.
- **SSID**: abreviatura de **identificador de conjunto de servicios**. Esta propiedad es el nombre real de la red inalámbrica a la que se conectan los dispositivos. Con todo, los usuarios solo ven el nombre de red que ha configurado al elegir la conexión.
- **Conectar automáticamente**: elija **Habilitar** para conectarse automáticamente a esta red cuando el dispositivo está en el intervalo. Elija **Deshabilitar** para impedir que los dispositivos se conecten automáticamente.
- **Red oculta**: elija **Habilitar** si no se difunde el SSID de la red. Elija **Deshabilitar** si el SSID de la red se difunde y está visible.
- **Tipo de seguridad**: seleccione el protocolo de seguridad para autenticarse en la red Wi-Fi. Las opciones son:

  - **Abierta (sin autenticación)**: use esta opción solo si la red no es segura.
  - **WPA o WPA2 - Personal**: escriba la contraseña en **Clave precompartida**. Una vez configurada la red de su organización, también se configuran una contraseña o una clave de red. Escriba esta contraseña o clave de red para el valor PSK.
  - **WEP**

- **Configuración de proxy**: Las opciones son:
  - **Ninguna**: no se ha configurado ningún valor de proxy.
  - **Manual**: especifique la **dirección del servidor proxy** como una dirección IP y su **número de puerto**.
  - **Automática**: use un archivo para configurar el servidor proxy. Escriba la **URL del servidor proxy** (por ejemplo, `http://proxy.contoso.com`) que contiene el archivo de configuración.

## <a name="enterprise-profiles"></a>Perfiles de empresa

- **Tipo de Wi-Fi**: elija **Empresa**.
- **SSID**: abreviatura de **identificador de conjunto de servicios**. Esta propiedad es el nombre real de la red inalámbrica a la que se conectan los dispositivos. Con todo, los usuarios solo ven el nombre de red que ha configurado al elegir la conexión.
- **Conectar automáticamente**: elija **Habilitar** para conectarse automáticamente a esta red cuando el dispositivo está en el intervalo. Elija **Deshabilitar** para impedir que los dispositivos se conecten automáticamente.
- **Red oculta**: elija **Habilitar** para ocultar esta red en la lista de redes disponibles en el dispositivo. No se difunde el SSID. Elija **Deshabilitar** para mostrar esta red en la lista de redes disponibles en el dispositivo.

- **Tipo de EAP**: elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras. Las opciones son:

  - **EAP-FAST**: escriba la **Configuración de las credenciales de acceso protegido (PAC)**. Esta opción usa credenciales de acceso protegido para crear un túnel autenticado entre el cliente y el servidor de autenticación. Las opciones son:
    - **No usar (PAC)**
    - **Usar (PAC)**: si existe un archivo PAC, úselo.
    - **Usar y aprovisionar PAC**: cree y agregue el archivo PAC a los dispositivos.
    - **Usar y aprovisionar PAC anónimamente**: cree y agregue el archivo PAC a los dispositivos sin autenticación en el servidor.

  - **EAP-SIM**

  - **EAP-TLS**: Indique también:

    - **Confianza del servidor** - **Nombres de servidor de certificados**: **agregue** uno o varios nombres comunes usados en los certificados emitidos por la entidad de certificación (CA) de confianza. Si escribe esta información, puede omitir la ventana de confianza dinámica que se muestra en los dispositivos de los usuarios cuando se conectan a esta red Wi-Fi.
    - **Certificado raíz para validación del servidor**: elija un perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Autenticación de cliente** - **Certificado cliente para la autenticación del cliente (certificado de identidad)**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

  - **EAP-TTLS**: Indique también:

    - **Confianza del servidor** - **Nombres de servidor de certificados**: **agregue** uno o varios nombres comunes usados en los certificados emitidos por la entidad de certificación (CA) de confianza. Si escribe esta información, puede omitir la ventana de confianza dinámica que se muestra en los dispositivos de los usuarios cuando se conectan a esta red Wi-Fi.
    - **Certificado raíz para validación del servidor**: elija un perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:

      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. Indique también:
        - **Método que no es EAP (identidad interna)**: elija cómo autenticar la conexión. Asegúrese de elegir el mismo protocolo que está configurado en su red Wi-Fi.

          Las opciones son: **Contraseña no cifrada (PAP)**, **Protocolo de autenticación por desafío mutuo (CHAP)**, **Microsoft CHAP (MS-CHAP)** o **Microsoft CHAP versión 2 (MS-CHAP v2)**

      - **Certificados**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

        Haga clic en **Aceptar** para guardar los cambios.

      - **Privacidad de identidad (identidad externa)**: escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

  - **LEAP**

  - **PEAP**: Indique también:

    - **Confianza del servidor** - **Nombres de servidor de certificados**: **agregue** uno o varios nombres comunes usados en los certificados emitidos por la entidad de certificación (CA) de confianza. Si escribe esta información, puede omitir la ventana de confianza dinámica que se muestra en los dispositivos de los usuarios cuando se conectan a esta red Wi-Fi.
    - **Certificado raíz para validación del servidor**: elija un perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:

      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. 

      - **Certificados**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

        Haga clic en **Aceptar** para guardar los cambios.

      - **Privacidad de identidad (identidad externa)**: escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

- **Configuración de proxy**: Las opciones son:
  - **Ninguna**: no se ha configurado ningún valor de proxy.
  - **Manual**: especifique la **dirección del servidor proxy** como una dirección IP y su **número de puerto**.
  - **Automática**: use un archivo para configurar el servidor proxy. Escriba la **URL del servidor proxy** (por ejemplo, `http://proxy.contoso.com`) que contiene el archivo de configuración.

Seleccione **Aceptar** > **Crear** para guardar los cambios. El perfil se crea y se muestra en la lista de perfiles.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero no hacen nada. A continuación, [asigne este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Más recursos

[Introducción a la configuración de Wi-Fi](wi-fi-settings-configure.md), incluidas otras plataformas disponibles.
