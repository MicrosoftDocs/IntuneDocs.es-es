---
title: 'Configuración de Wi-Fi para dispositivos Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Agregue o cree el perfil de configuración de Wi-Fi mediante la configuración de Wi-Fi para dispositivos Windows 10 y versiones posteriores en Microsoft Intune. Puede configurar la configuración básica o de nivel empresarial.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f6532c63612b806f9824f5b9ca98f1ebbbc943f
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321734"
---
## <a name="wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Configuración de Wi-Fi para dispositivos Windows 10 y versiones posteriores en Intune

La configuración de Wi-Fi se usa en un perfil de configuración que se aplica a los dispositivos que ejecutan Windows 10 y versiones posteriores. Existen varias opciones:

- Básica
- Enterprise

## <a name="before-you-begin"></a>Antes de comenzar

[Creación de un perfil de dispositivo en Microsoft Intune](device-profile-create.md).

## <a name="settings-for-basic-and-enterprise-profiles"></a>Configuración para perfiles básico y de empresa

- **Nombre de Wi-Fi (SSID)**: abreviatura de identificador de conjunto de servicios. Este valor es el nombre real de la red inalámbrica a la que se conectan los dispositivos. Pero cuando los usuarios eligen la conexión, solo ven el **Nombre de conexión** que configure.
- **Nombre de conexión**: escriba un nombre descriptivo para esta conexión Wi-Fi. El texto que escriba es el nombre que ven los usuarios cuando exploran las conexiones disponibles en sus dispositivos.
- **Conectar automáticamente cuando se encuentre dentro del alcance**: cuando es **Sí**, los dispositivos conectan automáticamente cuando están en el alcance de esta red. Cuando es **No**, los dispositivos no se conectan automáticamente.
  - **Conectarse a una red con mayor preferencia si está disponible**: si los dispositivos están en el alcance de una red preferida, haga clic en **Sí** para usarla. Haga clic en **No** para usar la red Wi-Fi de este perfil de configuración.

    Por ejemplo, crea una red Wi-Fi **ContosoCorp** y usa **ContosoCorp** dentro de este perfil de configuración. También tiene una red Wi-Fi **ContosoGuest** dentro del alcance. Cuando los dispositivos corporativos estén dentro del alcance, quiere que se conecten automáticamente a **ContosoCorp**. En este escenario, establezca la propiedad **Conectarse a una red con mayor preferencia si está disponible** en **No**.

  - **Connect to this network, even when it is not broadcasting its SSID** (Conectarse a esta red, aunque no difunda su SSID): haga clic en **Sí** para que el perfil de configuración se conecte automáticamente a la red, incluso cuando está oculta (es decir, su SSID no se difunde públicamente). Haga clic en **No** si no quiere que este perfil de configuración se conecte a la red oculta.

- **Configuración del proxy de la empresa**: elija la configuración de proxy que se va a usar en la organización. Las opciones son:
  - **Ninguno**: no se configura ningún valor de proxy.
  - **Configurar manualmente**: escriba la **Dirección IP del servidor proxy** y su **Número de puerto**.
  - **Configurar automáticamente**: escriba la dirección URL que apunta a un script de configuración automática de proxy (PAC). Por ejemplo, escriba `http://proxy.contoso.com/proxy.pac`.

## <a name="settings-for-basic-profiles-only"></a>Configuración solo para perfiles básicos

- **Tipo de seguridad inalámbrica**: escriba el protocolo de seguridad que se usa para autenticar los dispositivos de la red. Las opciones son:
  - **Abierta (sin autenticación)**: use esta opción solo si la red no es segura.
  - **WPA/WPA2-Personal**

## <a name="settings-for-enterprise-profiles-only"></a>Configuración solo para perfiles de empresa

- **Inicio de sesión único (SSO)**: permite configurar el inicio de sesión único (SSO), donde se comparten las credenciales para el equipo y el inicio sesión de red Wi-Fi. Las opciones son:
  - **Deshabilitar**: se deshabilita el comportamiento de SSO. El usuario debe autenticarse en la red por separado.
  - **Enable before user signs into device** (Habilitar antes de que el usuario inicie sesión en el dispositivo): use SSO para autenticarse en la red justo antes del proceso de inicio de sesión del usuario.
  - **Enable after user signs into device** (Habilitar después de que el usuario inicie sesión en el dispositivo): use SSO para autenticarse en la red justo después de que finalice el proceso de inicio de sesión del usuario.
  - **Maximum time to authenticate before timeout** (Tiempo máximo para autenticarse antes del tiempo de espera): escriba el número máximo de segundos que deben transcurrir antes de autenticarse en la red, de 1 a 120 segundos.
  - **Permitir que Windows solicite al usuario credenciales de autenticación adicionales**: hacer clic en **Sí** permite que el sistema Windows solicite al usuario credenciales de autenticación adicionales si el método de autenticación lo requiere. Haga clic en **No** para ocultar estos mensajes.

- **Habilitar almacenamiento en caché de Clave maestra en pares (PMK)**: haga clic en **Sí** para almacenar en caché la PMK que se usa en la autenticación. Este almacenamiento en caché normalmente permite que la autenticación en la red se complete más rápido. Haga clic en **No** para forzar el protocolo de enlace de autenticación al conectarse a la red Wi-Fi cada vez.

  - **Maximum time a PMK is stored in cache** (Tiempo máximo que se almacena en caché una PMK): escriba el número de minutos que una clave maestra en pares (PMK) se almacena en la caché, de 5 a 1440 minutos.
  - **Maximum number of PMKs stored in cache** (Número máximo de PMK almacenadas en caché): escriba el número de claves almacenadas en caché, de 1 a 255.

- **Habilitar la autenticación previa**: la autenticación previa permite que el perfil se autentique en todos los puntos de acceso para la red del perfil antes de conectarse. Al moverse entre puntos de acceso, la autenticación previa vuelva a conectar al usuario o los dispositivos más rápidamente. Haga clic en **Sí** para que el perfil se autentique en todos los puntos de acceso para esta red que estén dentro del alcance. Haga clic en **No** para requerir que el usuario o dispositivo se autentique por separado en cada punto de acceso.

  - **Número máximo de intentos de autenticación previa**: escriba el número de intentos de autenticación previa, de 1 a 16.

- **Tipo de EAP**: elija el tipo de Protocolo de autenticación extensible (EAP) para autenticar las conexiones inalámbricas seguras. Las opciones son:

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **EAP protegido** (PEAP)

### <a name="more-options-when-you-choose-the-eap-type"></a>Más opciones al elegir el tipo de EAP

> [!NOTE]
> Actualmente, solo se admiten los perfiles de certificado SCEP cuando se usa un tipo de EAP. No se admiten los perfiles de certificado PKCS. Cada vez que se le pida a un usuario que escriba un certificado, asegúrese de que se elige un certificado SCEP.

#### <a name="server-trust"></a>Confianza del servidor

|Nombre de la configuración|Más información|Se debe usar cuando:|
|--------------|-------------|----------|
|**Nombres de servidor de certificados**|Escriba uno o más nombres comunes usados en los certificados emitidos por la entidad de certificación (CA) de confianza. Si escribe esta información, puede omitir el cuadro de diálogo de confianza dinámica que se muestra en los dispositivos de los usuarios cuando se conectan a esta red Wi-Fi.|El tipo de EAP es **EAP-TLS**, **EAP-TTLS** o **PEAP**|
|**Certificado raíz para validación del servidor**|Seleccione el perfil de certificado raíz de confianza que se usa para autenticar la conexión. |El tipo de EAP es **EAP-TLS**, **EAP-TTLS** o **PEAP**|
|**Privacidad de identidad (identidad externa)**|Escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.|El tipo de EAP es **PEAP**.|

#### <a name="client-authentication"></a>Autenticación de cliente

| Nombre de la configuración | Más información | Se debe usar cuando: |
|---|---|---|
| **Certificado cliente para la autenticación del cliente (certificado de identidad)** |  Seleccione el perfil de certificado SCEP que se usa para autenticar la conexión. | El tipo de EAP es **EAP-TLS**. |
| **Método de autenticación** | Seleccione el método de autenticación para la conexión:<br><br>- **Certificados**: seleccione el certificado de cliente SCEP que es el certificado de identidad presentado al servidor.<br><br>- **Nombre de usuario y contraseña**: escriba un **Método que no es EAP (identidad interna)** para la autenticación. Las opciones son:<br><br>- **Contraseña no cifrada (PAP)**<br>- **Desafío mutuo (CHAP)**<br>- **Microsoft CHAP (MS-CHAP)**<br>- **Microsoft CHAP versión 2 (MS-CHAP v2)**<br><br>- **Privacidad de identidad (identidad interna)**: escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro. | El tipo de EAP es **EAP-TTLS**. |

## <a name="use-an-imported-settings-file"></a>Usar un archivo de configuración importado

Para cualquier configuración que no esté disponible en Intune, puede exportar la configuración de Wi-Fi desde otro dispositivo Windows. Esta exportación crea un archivo XML con toda la configuración. Después, importe este archivo en Intune y úselo como el perfil de Wi-Fi. Vea [Exportación e importación de la configuración de Wi-Fi para dispositivos Windows](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>Pasos siguientes
[Configuración de Wi-Fi en Microsoft Intune](wi-fi-settings-configure.md)
