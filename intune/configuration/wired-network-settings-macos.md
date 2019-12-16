---
title: Configuración de red cableada para dispositivos macOS en Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Cree o agregue un perfil de configuración de dispositivos de red cableada para dispositivos macOS. Vea las diferentes configuraciones, como la adición de certificados, la elección de un tipo EAP y la selección de un método de autenticación en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/4/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dba36d03489bcdeee3c3c1f69a4995823dd21ee
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74994337"
---
# <a name="add-wired-network-settings-for-macos-devices-in-microsoft-intune"></a>Agregar configuración de red cableada para dispositivos macOS en Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Puede crear un perfil con una configuración específica de red cableada y después implementar este perfil en los dispositivos macOS. Microsoft Intune ofrece muchas características, incluidas la autenticación en la red, agregar un certificado PKS o SCEP y muchas más. 

## <a name="before-you-begin"></a>Antes de comenzar

[Creación de un perfil de dispositivo en Microsoft Intune](device-profile-create.md).

> [!NOTE]
> Estas opciones están disponibles para todos los tipos de inscripción. Para obtener más información sobre los tipos de inscripción, consulte [inscripción de MacOS](../enrollment/macos-enroll.md).

## <a name="profiles"></a>Profiles

- **Tipo de perfil**: elija **red cableada**.
- **Interfaz de red**: 
- **Tipo de EAP**: elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras. Las opciones son:
  - **EAP-FAST**: escriba la **Configuración de las credenciales de acceso protegido (PAC)** . Esta opción usa credenciales de acceso protegido para crear un túnel autenticado entre el cliente y el servidor de autenticación. Las opciones son:
    - **No usar (PAC)**
    - **Usar (PAC)** : si existe un archivo PAC, úselo.
    - **Usar y aprovisionar PAC**: cree y agregue el archivo PAC a los dispositivos.
    - **Usar y aprovisionar PAC anónimamente**: cree y agregue el archivo PAC a los dispositivos sin autenticación en el servidor.
  - **EAP-TLS**: especifique también:
    - **Confianza del servidor** - **Nombres de servidor de certificados**: **agregue** uno o más nombres comunes usados en los certificados emitidos por la entidad de certificación (CA) de confianza. Si escribe esta información, puede omitir la ventana de confianza dinámica que se muestra en los dispositivos de los usuarios cuando se conectan a esta red Wi-Fi.
    - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.
    - **Autenticación de cliente** - **Certificado para la autenticación de cliente (certificado de identidad)** : elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.
  - **EAP-TTLS**: especifique también:
    - **Confianza del servidor** - **Nombres de servidor de certificados**: **agregue** uno o más nombres comunes usados en los certificados emitidos por la entidad de certificación (CA) de confianza. Si escribe esta información, puede omitir la ventana de confianza dinámica que se muestra en los dispositivos de los usuarios cuando se conectan a esta red Wi-Fi.
    - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.
    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:
      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. Indique también:
        - **Método que no es EAP (identidad interna)** : seleccione cómo se autentica la conexión. Asegúrese de elegir el mismo protocolo que está configurado en su red Wi-Fi.
          Opciones: **Contraseña no cifrada (PAP)** , **Protocolo de autenticación por desafío mutuo (CHAP)** , **Microsoft CHAP (MS-CHAP** o **Microsoft CHAP versión 2 (MS-CHAP v2)** .
      - **Certificados**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.
      - **Privacidad de identidad (identidad interna)** : escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.
  - **LEAP**
  - **PEAP**: especifique también:
    - **Confianza del servidor** - **Nombres de servidor de certificados**: **agregue** uno o más nombres comunes usados en los certificados emitidos por la entidad de certificación (CA) de confianza. Si escribe esta información, puede omitir la ventana de confianza dinámica que se muestra en los dispositivos de los usuarios cuando se conectan a esta red Wi-Fi.
    - **Certificado raíz para validación del servidor**: elija el perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.
    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:
      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. 
      - **Certificados**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.
      - **Privacidad de identidad (identidad interna)** : escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero no hacen nada. Después, [asigne este perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).

Configure las opciones de Wi-Fi en dispositivos [Android](wi-fi-settings-android.md), [Android Enterprise](wi-fi-settings-android-enterprise.md), [iOS](wi-fi-settings-ios.md)y [Windows 10](wi-fi-settings-windows.md) .
