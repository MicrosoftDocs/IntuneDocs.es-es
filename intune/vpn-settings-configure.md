---
title: "Cómo configurar opciones de VPN de Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a usar Intune para configurar conexiones VPN en los dispositivos que administra.¡"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8a8742d0b579fec734dd8335e2a610d126db21fa
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-configure-vpn-settings-in-microsoft-intune"></a>Configuración de VPN en Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Las redes privadas virtuales (VPN) ofrecen a los usuarios un acceso remoto seguro a la red de la empresa. Los dispositivos utilizan un perfil de conexión VPN para iniciar una conexión con el servidor VPN. Use los **perfiles de VPN** en Microsoft Intune para asignar la configuración de VPN a los usuarios y dispositivos de la organización, para que puedan conectarse a la red de forma fácil y segura.

Por ejemplo, suponga que quiere aprovisionar todos los dispositivos iOS con la configuración necesaria para conectarse a un recurso compartido de archivos de la red corporativa. Debe crear un perfil de VPN con la configuración necesaria para conectarse a la red corporativa y, a continuación, debe implementar este perfil en todos los usuarios con dispositivos iOS. Los usuarios ven la conexión VPN en la lista de redes disponibles y pueden conectarse realizando un mínimo esfuerzo.

## <a name="vpn-connection-types"></a>Tipos de conexión VPN

Puede crear perfiles de VPN mediante los siguientes tipos de conexión:

||||||||
|-|-|-|-|-|-|-|
|Tipo de conexión|Android|iOS|macOS|Windows Phone 8,1|Windows 8.1|Windows 10|
|Pulse Secure|Sí|Sí|Sí|Sí|Sí|Sí|
|Cisco (IPSec)|No|Sí|No|No|No|No|
|Citrix|Sí|Sí|No|No|No|No|
|F5 Edge Client|Sí|Sí|Sí|Sí|Sí|Sí|
|Dell SonicWALL Mobile Connect|Sí|Sí|Sí|Sí|Sí|Sí|
|Check Point Capsule VPN|Sí|Sí|Sí|Sí|Sí|Sí|
|Cisco AnyConnect|Sí|Sí|Sí|No|No|No|
|Automático|No|No|No|No|No|Sí|
|IKEv2|No|No|No|No|No|Sí|
|L2TP|No|No|No|No|No|Sí|
|PPTP|No|No|No|No|No|Sí|
|Personalizada|No|Sí|Sí|No|No|No|


> [!IMPORTANT]
> Para poder usar perfiles de VPN asignados a un dispositivo, debe instalar la aplicación VPN aplicable al perfil. Puede usar la información del tema [¿Qué es la administración de aplicaciones de Microsoft Intune?](app-management.md) para ayudarlo a implementar la aplicación con Intune.  

Aprenda a crear perfiles de VPN personalizados mediante la configuración de URI en [Configuraciones personalizadas para perfiles de VPN de Microsoft Intune](custom-vpn-profiles-create.md).     

## <a name="create-a-device-profile-containing-vpn-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de VPN

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil de VPN.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo a la que quiere aplicar la configuración de VPN. Actualmente, puede elegir una de las siguientes plataformas para la configuración del dispositivo VPN:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **tipos de perfil**, elija **VPN**.
7. Dependiendo de la plataforma que eligió, las opciones que pueda configurar serán diferentes. Vaya a uno de los siguientes temas para conocer más detalles sobre la configuración para cada plataforma:
    - [Configuración de Android](vpn-settings-android.md)
    - [Configuración de iOS](vpn-settings-ios.md)
    - [Configuración de macOS](vpn-settings-macos.md)
    - [Configuración de Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
    - [Configuración de Windows 8.1](vpn-settings-windows-8-1.md)
    - [Configuración de Windows 10](vpn-settings-windows-10.md)
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).


## <a name="methods-of-securing-vpn-profiles"></a>Métodos para proteger los perfiles de VPN

Los perfiles de VPN pueden utilizar diferentes tipos de conexiones y protocolos de diferentes fabricantes. Estas conexiones normalmente se protegen con uno de dos métodos.

### <a name="certificates"></a>Certificados

Al crear el perfil de VPN, elija un perfil de certificado SCEP o PKCS que haya creado previamente en Intune. Esto se conoce como certificado de identidad y se utiliza para autenticar con un perfil de certificado de confianza (o un *certificado raíz*) que ha creado para establecer que el dispositivo del usuario tiene permiso para conectarse. El certificado de confianza se asigna al equipo que autentica la conexión VPN, por lo general, el servidor de VPN.

Para más información sobre cómo crear y usar perfiles de certificado en Intune, consulte [How to configure certificates with Microsoft Intune](certificates-configure.md) (Configuración de certificados con Microsoft Intune).

### <a name="user-name-and-password"></a>Nombre de usuario y contraseña

El usuario se autentica en el servidor de VPN proporcionando el nombre de usuario y contraseña.

