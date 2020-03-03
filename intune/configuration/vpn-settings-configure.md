---
title: 'Incorporación de una configuración de VPN a dispositivos iOS en Microsoft Intune: Azure | Microsoft Docs'
description: En el caso de dispositivos Android, Android Enterprise, iOS, iPadOS, macOS y Windows, use la configuración integrada para crear conexiones de red privada virtual (VPN) en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 134ef9a2a4dfe8a4576c753a001439c42f678adc
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510820"
---
# <a name="create-vpn-profiles-to-connect-to-vpn-servers-in-intune"></a>Creación de perfiles de VPN para conectarse a servidores VPN en Intune



Las redes privadas virtuales (VPN) ofrecen a los usuarios acceso remoto seguro a la red de la empresa. Los dispositivos usan un perfil de conexión VPN para iniciar una conexión con el servidor VPN. Los **perfiles de VPN** de Microsoft Intune asignan la configuración de VPN a los usuarios y dispositivos de la organización, para que puedan conectarse de forma fácil y segura a la red de la empresa.

Por ejemplo, quiere configurar todos los dispositivos iOS/iPadOS con las opciones de configuración necesarias para conectarse a un recurso compartido de archivos de la red de la empresa. Cree un perfil de VPN que incluya estas opciones de configuración. Después, asigne este perfil a todos los usuarios que tengan dispositivos iOS/iPadOS. Los usuarios verán la conexión VPN en la lista de redes disponibles y podrán conectarse con un esfuerzo mínimo.

> [!NOTE]
> Puede usar [directivas de configuración personalizadas](custom-settings-configure.md) de Intune para crear perfiles de VPN para las siguientes plataformas:
>
> * Android 4 y versiones posteriores
> * Dispositivos inscritos que ejecutan Windows 8.1 y versiones posteriores
> * Windows Phone 8.1 y versiones posteriores
> * Dispositivos inscritos que ejecutan Windows 10 Escritorio
> * Windows 10 Mobile
> * Windows Holographic for Business

## <a name="vpn-connection-types"></a>Tipos de conexión VPN

Puede crear perfiles de VPN mediante los siguientes tipos de conexión:

|Tipo de conexión|Plataforma|
|-|-|
|Automático|Windows 10|
|Check Point Capsule VPN|- Android<br/>- Perfiles de trabajo de Android Enterprise<br/>- iOS/iPadOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Cisco AnyConnect|- Android<br/>- Perfiles de trabajo de Android Enterprise<br/>- Propietario del dispositivo Android Enterprise (totalmente administrado)<br/>- iOS/iPadOS<br/>- macOS|
|Cisco (IPsec)|iOS/iPadOS|
|SSO de Citrix|- Android<br/>- Perfiles de trabajo de Android Enterprise: uso de la [directiva de configuración de aplicaciones](../apps/app-configuration-policies-use-android.md)<br/>- Propietario del dispositivo Android Enterprise (totalmente administrado): uso de la [directiva de configuración de aplicaciones](../apps/app-configuration-policies-use-android.md)<br/>- iOS/iPadOS<br/>- Windows 10|
|VPN personalizada|- iOS/iPadOS<br/>- macOS|
|F5 Access|- Android<br/>- Perfiles de trabajo de Android Enterprise<br/>- Propietario del dispositivo Android Enterprise (totalmente administrado)<br/>- iOS/iPadOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|IKEv2| - iOS/iPadOS<br/>- Windows 10|
|L2TP|Windows 10|
|Palo Alto Networks GlobalProtect|- Perfiles de trabajo de Android Enterprise: uso de la [directiva de configuración de aplicaciones](../apps/app-configuration-policies-use-android.md)<br/>- iOS/iPadOS<br/>- Windows 10|
|PPTP|Windows 10|
|Pulse Secure|- Android<br/>- Perfiles de trabajo de Android Enterprise<br/>- Propietario del dispositivo Android Enterprise (totalmente administrado)<br/>- iOS/iPadOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|SonicWall Mobile Connect|- Android<br/>- Perfiles de trabajo de Android Enterprise<br/>- iOS/iPadOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Zscaler|- Perfiles de trabajo de Android Enterprise: uso de la [directiva de configuración de aplicaciones](../apps/app-configuration-policies-use-android.md)<br/>- iOS/iPadOS|

> [!IMPORTANT]
> Para poder usar perfiles de VPN asignados a un dispositivo, debe instalar la aplicación VPN aplicable al perfil. Puede usar la información del artículo [¿Qué es la administración de aplicaciones de Microsoft Intune?](../apps/app-management.md) para obtener ayuda sobre cómo asignar la aplicación con Intune.  

Aprenda a crear perfiles de VPN personalizados usando la configuración de URI de [Crear un perfil con una configuración personalizada](custom-settings-configure.md).

## <a name="create-a-device-profile"></a>Creación del perfil de un dispositivo

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. Asígnele un nombre a los perfiles para que pueda identificarlos de manera sencilla más adelante. Por ejemplo, un buen nombre de perfil sería **Perfil de VPN de toda la empresa**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione la plataforma de los dispositivos. Las opciones son:

      - **Android**
      - **Android Enterprise** > **Solo el propietario del dispositivo**
      - **Android Enterprise** > **Solo perfil de trabajo **
      - **iOS/iPadOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 y versiones posteriores**
      - **Windows 10 y versiones posteriores**

    - **Tipo de perfil**: seleccione **VPN**.

4. Dependiendo de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. Consulte los siguientes artículos para conocer más detalles sobre la configuración en cada plataforma:

    - [Configuración de Android](vpn-settings-android.md)
    - [Configuración de Android Enterprise](vpn-settings-android-enterprise.md)
    - [Configuración de iOS/iPadOS](vpn-settings-ios.md)
    - [Configuración de macOS](vpn-settings-macos.md)
    - [Configuración de Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
    - [Configuración de Windows 8.1](vpn-settings-windows-8-1.md)
    - [Configuración de Windows 10](vpn-settings-windows-10.md) (incluido Windows Holographic for Business)

5. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se crea y aparece en la lista de perfiles. Para asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

## <a name="secure-your-vpn-profiles"></a>Protección de los perfiles de VPN

Los perfiles de VPN pueden utilizar diferentes tipos de conexiones y protocolos de diferentes fabricantes. Estas conexiones suelen protegerse con los siguientes métodos.

### <a name="certificates"></a>Certificados

Al crear el perfil de VPN, elija un perfil de certificado SCEP o PKCS que haya creado previamente en Intune. Este perfil se conoce como “certificado de identidad”. Se usa para autenticar con un perfil de certificado de confianza (o un *certificado raíz*) que se crea para que el dispositivo del usuario pueda conectarse. El certificado de confianza se asigna al equipo que autentica la conexión VPN, por lo general, el servidor de VPN.

Para más información sobre cómo crear y usar perfiles de certificado en Intune, consulte [How to configure certificates with Microsoft Intune](../protect/certificates-configure.md) (Configuración de certificados con Microsoft Intune).

### <a name="user-name-and-password"></a>Nombre de usuario y contraseña

El usuario se autentica en el servidor de VPN proporcionando el nombre de usuario y contraseña.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. A continuación, [asigne el perfil](device-profile-assign.md) a algunos dispositivos.

También puede crear y usar instancias de VPN por aplicación en dispositivos [Android](android-pulse-secure-per-app-vpn.md) e [iOS/iPadOS](vpn-setting-configure-per-app.md).
