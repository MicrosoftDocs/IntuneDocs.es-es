---
title: "Cómo configurar opciones de VPN de Intune"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a usar Intune para configurar conexiones VPN en los dispositivos que administra.¡"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 2d93edb688dbf296137a133f0b7ae065fc1cc89d
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-configure-vpn-settings-in-microsoft-intune"></a>Configuración de VPN en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Las redes privadas virtuales (VPN) ofrecen a los usuarios un acceso remoto seguro a la red de la empresa. Los dispositivos utilizan un perfil de conexión VPN para iniciar una conexión con el servidor VPN. Use los **Perfiles de VPN** en Microsoft Intune para implementar la configuración de VPN para los usuarios y dispositivos de su organización, para que puedan conectarse de forma fácil y segura a la red.

Por ejemplo, suponga que quiere aprovisionar todos los dispositivos iOS con la configuración necesaria para conectarse a un recurso compartido de archivos de la red corporativa. Debe crear un perfil de VPN con la configuración necesaria para conectarse a la red corporativa y, a continuación, debe implementar este perfil en todos los usuarios con dispositivos iOS. Los usuarios ven la conexión VPN en la lista de redes disponibles y pueden conectarse realizando un mínimo esfuerzo.

## <a name="vpn-connection-types"></a>Tipos de conexión VPN

Puede crear perfiles de VPN mediante los siguientes tipos de conexión:

|||
|-|-|
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
> Para poder usar perfiles de VPN que se implementen en un dispositivo, debe instalar la aplicación VPN aplicable para el perfil. Puede usar la información del tema [What is app management in Microsoft Intune?](/intune-azure/manage-apps/what-is-app-management) (¿Qué es la administración de aplicaciones en Microsoft Intune?) para ayudarle a implementar la aplicación con Intune.  

Aprenda a crear perfiles de VPN personalizados mediante la configuración de URI en [Configuraciones personalizadas para perfiles de VPN de Microsoft Intune](create-custom-vpn-profiles.md).     

## <a name="create-a-device-profile-containing-vpn-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de VPN

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
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
    - [Configuración de Android](vpn-for-android.md)
    - [Configuración de iOS](vpn-for-ios.md)
    - [Configuración de macOS](vpn-for-macos.md)
    - [Configuración de Windows Phone 8.1](vpn-for-windows-phone-8-1.md)
    - [Configuración de Windows 8.1](vpn-for-windows-8-1.md)
    - [Configuración de Windows 10](vpn-for-windows-10.md)
8. Cuando haya terminado, vuelva a la hoja **Create Profile** (Crear perfil) y presione **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.
Si desea continuar y asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](how-to-assign-device-profiles.md).


## <a name="methods-of-securing-vpn-profiles"></a>Métodos para proteger los perfiles de VPN

Los perfiles de VPN pueden utilizar diferentes tipos de conexiones y protocolos de diferentes fabricantes. Estas conexiones normalmente se protegen con uno de dos métodos.

### <a name="certificates"></a>Certificados

Al crear el perfil de VPN, elija un perfil de certificado SCEP o PKCS que haya creado previamente en Intune. Esto se conoce como certificado de identidad y se utiliza para autenticar con un perfil de certificado de confianza (o un *certificado raíz*) que ha creado para establecer que el dispositivo del usuario tiene permiso para conectarse. El certificado de confianza se implementa en el equipo que autentica la conexión VPN, por lo general, el servidor de VPN.

Para más información sobre cómo crear y usar perfiles de certificado en Intune, consulte [How to configure certificates with Microsoft Intune](how-to-configure-certificates.md) (Configuración de certificados con Microsoft Intune).

### <a name="user-name-and-password"></a>Nombre de usuario y contraseña

El usuario se autentica en el servidor de VPN proporcionando el nombre de usuario y contraseña.

