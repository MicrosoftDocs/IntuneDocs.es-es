---
title: Creación de un perfil de dispositivo VPN en Microsoft Intune - Azure | Microsoft Docs
description: Para los dispositivos iOS, puede ver los tipos de conexión de red privada virtual (VPN), crear un perfil de dispositivo VPN en Azure Portal y ver las opciones disponibles para proteger el perfil de VPN con certificados o con un nombre de usuario y una contraseña en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2d0bde56c6622648d47fe47458bdac62d7843ca
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838468"
---
# <a name="create-vpn-profiles-in-intune"></a>Crear perfiles de VPN en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Las redes privadas virtuales (VPN) ofrecen a los usuarios un acceso remoto seguro a la red de la empresa. Los dispositivos utilizan un perfil de conexión VPN para iniciar una conexión con el servidor VPN. Use los **perfiles de VPN** en Microsoft Intune para asignar la configuración de VPN a los usuarios y dispositivos de la organización, para que puedan conectarse a la red de forma fácil y segura.

Por ejemplo, suponga que quiere aprovisionar todos los dispositivos iOS con la configuración necesaria para conectarse a un recurso compartido de archivos de la red corporativa. Crea un perfil de VPN que contiene la configuración necesaria para conectarse a la red corporativa. Después asigna este perfil a todos los usuarios que tienen dispositivos iOS. Los usuarios verán la conexión VPN en la lista de redes disponibles y podrán conectarse con un esfuerzo mínimo.

Puede usar directivas de configuración personalizadas de Intune para crear perfiles de VPN para las siguientes plataformas:

* Android 4 y versiones posteriores
* Dispositivos inscritos que ejecutan Windows 8.1 y versiones posteriores
* Windows Phone 8.1 y versiones posteriores
* Dispositivos inscritos que ejecutan Windows 10 Escritorio
* Windows 10 Mobile
* Windows Holographic for Business

## <a name="vpn-connection-types"></a>Tipos de conexión VPN

Puede crear perfiles de VPN mediante los siguientes tipos de conexión:

|Tipo de conexión|Android<br>Perfiles de trabajo Android|iOS|macOS|Windows Phone 8,1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Automático|No|No|No|No|No|Sí|
|Check Point Capsule VPN|Sí|Sí|Sí|Sí|Sí|Sí|
|Cisco AnyConnect|Sí|Sí|Sí|No|No|No|
|SonicWall Mobile Connect|Sí|Sí|Sí|Sí|Sí|Sí|
|F5 Edge Client|Sí|Sí|Sí|Sí|Sí|Sí|
|Palo Alto Networks GlobalProtect|No|Sí|No|No|No|Sí|
|Pulse Secure|Sí|Sí|Sí|Sí|Sí|Sí|
|Cisco (IPSec)|No|Sí|No|No|No|No|
|Citrix|Sí (solo Android)|Sí|No|No|No|Sí|
|IKEv2|No|No|No|No|No|Sí|
|L2TP|No|No|No|No|No|Sí|
|PPTP|No|No|No|No|No|Sí|
|Zscaler|No|Sí|No|No|No|No|
|VPN personalizada|No|Sí|Sí|No|No|No|

> [!IMPORTANT]
> Para poder usar perfiles de VPN asignados a un dispositivo, debe instalar la aplicación VPN aplicable al perfil. Puede usar la información del artículo [¿Qué es la administración de aplicaciones de Microsoft Intune?](app-management.md) para obtener ayuda sobre cómo asignar la aplicación con Intune.  

Aprenda a crear perfiles de VPN personalizados usando la configuración de URI de [Crear un perfil con una configuración personalizada](custom-settings-configure.md).

## <a name="create-a-device-profile-containing-vpn-settings"></a>Creación de un perfil de dispositivo que contenga la configuración de VPN

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
4. Escriba un **nombre** y una **descripción** para el perfil de VPN.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo a la que quiere aplicar la configuración de VPN. Actualmente, puede elegir una de las siguientes plataformas para la configuración del dispositivo VPN:
   - **Android**
   - **Android Enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 y versiones posteriores**
   - **Windows 10 y versiones posteriores**
6. En la lista desplegable de **tipos de perfil**, elija **VPN**.
7. Dependiendo de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. Vaya a uno de los siguientes temas para conocer más detalles sobre la configuración para cada plataforma:
   - [Configuración de perfil de trabajo de Android y Android](vpn-settings-android.md)
   - [Configuración de iOS](vpn-settings-ios.md)
   - [Configuración de macOS](vpn-settings-macos.md)
   - [Configuración de Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
   - [Configuración de Windows 8.1](vpn-settings-windows-8-1.md)
   - [Configuración de Windows 10](vpn-settings-windows-10.md) (incluido Windows Holographic for Business)
8. Cuando haya terminado, **cree** su perfil.

El perfil se crea y aparece en la lista de perfiles. Para asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

## <a name="methods-of-securing-vpn-profiles"></a>Métodos para proteger los perfiles de VPN

Los perfiles de VPN pueden utilizar diferentes tipos de conexiones y protocolos de diferentes fabricantes. Estas conexiones normalmente se protegen con uno de dos métodos.

### <a name="certificates"></a>Certificados

Al crear el perfil de VPN, elija un perfil de certificado SCEP o PKCS que haya creado previamente en Intune. Este perfil se conoce como “certificado de identidad”. Se usa para autenticar con un perfil de certificado de confianza (o un *certificado raíz*) que se crea para que el dispositivo del usuario pueda conectarse. El certificado de confianza se asigna al equipo que autentica la conexión VPN, por lo general, el servidor de VPN.

Para más información sobre cómo crear y usar perfiles de certificado en Intune, consulte [How to configure certificates with Microsoft Intune](certificates-configure.md) (Configuración de certificados con Microsoft Intune).

### <a name="user-name-and-password"></a>Nombre de usuario y contraseña

El usuario se autentica en el servidor de VPN proporcionando el nombre de usuario y contraseña.
