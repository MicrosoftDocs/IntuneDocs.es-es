---
title: Configuración de Wi-Fi en Microsoft Intune para dispositivos Android - Azure | Microsoft Docs
titleSuffix: ''
description: Cree o agregue un perfil de configuración de dispositivos Wi-Fi para Android. Vea las diferentes configuraciones, como la adición de certificados, la elección de un tipo EAP y la selección de un método de autenticación en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bac109164a1e75ce14efc5d61201e829e572e502
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565985"
---
# <a name="add-wi-fi-settings-for-devices-running-android-in-microsoft-intune"></a>Adición de la configuración de Wi-Fi en Microsoft Intune para dispositivos que ejecutan Android

Puede crear un perfil con una configuración específica de Wi-Fi y después implementar este perfil en los dispositivos Android. Microsoft Intune ofrece muchas características, incluidas la autenticación en la red, agregar un certificado PKS o SCEP y muchas más.

Estas configuraciones de Wi-Fi se dividen en dos categorías: configuración básica y a nivel de empresa.

Ambas se describen en este artículo.

## <a name="before-you-begin"></a>Antes de comenzar

[Creación de un perfil de dispositivo en Microsoft Intune](device-profile-create.md).

## <a name="basic-profile"></a>Perfil básico

- **Tipo de Wi-Fi**: elija **Básico**.
- **SSID**: abreviatura de **identificador de conjunto de servicios**. Esta configuración es el nombre real de la red inalámbrica a la que se conectan los dispositivos.
- **Conectar automáticamente**: elija **Habilitar** para conectarse automáticamente a esta red cuando el dispositivo está en el intervalo. Elija **Deshabilitar** para impedir que los dispositivos se conecten automáticamente.
- **Red oculta**: elija **Habilitar** para ocultar esta red en la lista de redes disponibles en el dispositivo. No se difunde el SSID. Elija **Deshabilitar** para mostrar esta red en la lista de redes disponibles en el dispositivo.

## <a name="enterprise-profile"></a>Perfil de empresa

- **Tipo de Wi-Fi**: elija **Empresa**.
- **SSID**: abreviatura de **identificador de conjunto de servicios**. Esta configuración es el nombre real de la red inalámbrica a la que se conectan los dispositivos.
- **Conectar automáticamente**: elija **Habilitar** para conectarse automáticamente a esta red cuando el dispositivo está en el intervalo. Elija **Deshabilitar** para impedir que los dispositivos se conecten automáticamente.
- **Red oculta**: elija **Habilitar** para ocultar esta red en la lista de redes disponibles en el dispositivo. No se difunde el SSID. Elija **Deshabilitar** para mostrar esta red en la lista de redes disponibles en el dispositivo.
- **Tipo de EAP**: elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras. Las opciones son: 

  - **EAP-TLS**: especifique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Autenticación de cliente** - **Certificado para la autenticación de cliente (certificado de identidad)**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

  - **EAP-TTLS**: especifique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:

      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. Indique también:
        - **Método que no es EAP (identidad interna)**: seleccione cómo se autentica la conexión. Asegúrese de elegir el mismo protocolo que está configurado en su red Wi-Fi.

          Opciones: **Contraseña no cifrada (PAP)**, **Protocolo de autenticación por desafío mutuo (CHAP)**, **Microsoft CHAP (MS-CHAP** o **Microsoft CHAP versión 2 (MS-CHAP v2)**.

      - **Certificados**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

        Haga clic en **Aceptar** para guardar los cambios.

      - **Privacidad de identidad (identidad interna)**: escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

  - **PEAP**: especifique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:

      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. Indique también:
        - **Método de autenticación que no es EAP (identidad interna)**: seleccione cómo se autentica la conexión. Asegúrese de elegir el mismo protocolo que está configurado en su red Wi-Fi.

          Opciones: **Ninguno** o **Microsoft CHAP versión 2 (MS-CHAP v2)**

      - **Certificados**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

        Haga clic en **Aceptar** para guardar los cambios.

      - **Privacidad de identidad (identidad interna)**: escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

Seleccione **Aceptar** > **Crear** para guardar los cambios. El perfil se crea y se muestra en la lista de perfiles.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero no hacen nada. A continuación, [asigne este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Más recursos

- [Introducción a la configuración de Wi-Fi](wi-fi-settings-configure.md), incluidas otras plataformas.

- ¿Usa dispositivos Android Enterprise o del Quiosco de Android? En caso afirmativo, consulte [Configuración de Wi-Fi para dispositivos que ejecutan Android Enterprise y el Quiosco de Android](wi-fi-settings-android-enterprise.md).
