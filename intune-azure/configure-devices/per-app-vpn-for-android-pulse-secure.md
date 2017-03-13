---
title: "Perfil VPN por aplicación para Pulse Secure para Android"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a crear un perfil de VPN por aplicación para dispositivos Android administrados por Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 0cf638348df2f01d70c0765a4932abc3eb801f23
ms.lasthandoff: 02/18/2017


---

# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Use un perfil personalizado de Microsoft Intune para crear un perfil de VPN por aplicación para dispositivos Android

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Puede crear un perfil de VPN por aplicación para dispositivos Android 5.0 y versiones posteriores administrados con Intune. Primero, cree un perfil de VPN que use el tipo de conexión Pulse Secure. Después, cree una directiva de configuración personalizada que asocie el perfil de VPN con las aplicaciones específicas.

Después de implementar la directiva en los grupos de usuarios o en el dispositivo Android, los usuarios deben iniciar la VPN PulseSecure, que permitirá el tráfico solo desde las aplicaciones especificadas para usar la conexión VPN abierta.

> [!NOTE]
>
> Para este perfil solo se admite el tipo de conexión Pulse Secure.


## <a name="step-1-create-a-vpn-profile"></a>Paso 1: Crear un perfil de VPN


1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
2. En la hoja de lista de perfiles, elija **Create Profile** (Crear perfil).
3. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** opcional para el perfil de VPN.
4. En la lista desplegable **Plataforma**, elija **Android**.
5. En la lista desplegable de **tipos de perfil**, elija **VPN**.
3. Elija **Configuración** > **Configurar** y luego configure el perfil de VPN según la configuración de [Configuración de VPN](how-to-configure-vpn-settings.md) y [Configuración de VPN de Intune para dispositivos Android](vpn-for-android.md).

Tome nota del nombre del perfil de VPN para usarlo en el paso siguiente. Por ejemplo, **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Paso 2: Crear una directiva de configuración personalizada

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
3. En la hoja de perfiles, haga clic en **Create Profile** (Crear perfil).
4. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** para el perfil personalizado.
5. En la lista desplegable **Plataforma**, elija **Android**.
6. En la lista desplegable de **tipos de perfil**, elija **Personalizado**.
7. Elija **Configuración** > **Configurar**.
3. En la hoja **Configuración OMA-URI personalizada**, elija **Agregar**.
    - Proporcione un nombre de configuración.
    - Para **Tipo de datos**, especifique **Cadena**.
    - Para **OMA-URI**, especifique esta cadena: **./Vendor/MSFT/VPN/Profile/*Name*/PackageList**, donde *Name* es el nombre del perfil de VPN que ha anotado en el paso 1. En nuestro ejemplo, la cadena sería **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
    - En **Valor**, cree una lista de los paquetes que se van a asociar con el perfil separados por punto y coma. Por ejemplo, si quiere que Excel y el explorador Google Chrome usen la conexión VPN, escriba: **com.microsoft.office.excel;com.android.chrome**.

![Directiva personalizada de ejemplo de VPN por aplicación de Android](./media/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Establecer la lista de aplicaciones como lista negra o lista blanca (opcional)
  Puede especificar una lista de aplicaciones que *no pueden* usar la conexión VPN mediante el valor **BLACKLIST**. Todas las demás aplicaciones se conectarán a través de la VPN.
De manera alternativa, puede usar el valor **WHITELIST** para especificar una lista de aplicaciones que *pueden* usar la conexión VPN. Las aplicaciones que no están en la lista no se conectarán a través de la VPN.
  1.    En la hoja **Configuración OMA-URI personalizada**, elija **Agregar**.
  2.    Proporcione un nombre de configuración.
  3.    Para **Tipo de datos**, especifique **Cadena**.
  4.    Para **OMA-URI**, use esta cadena: **./Vendor/MSFT/VPN/Profile/*Name*/Mode**, donde *Name* es el nombre del perfil de VPN que ha anotado en el paso 1. En nuestro ejemplo, la cadena sería **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  5.    En **Valor**, escriba **BLACKLIST** o **WHITELIST**.



## <a name="step-3-assign-both-policies"></a>Paso 3: Asignación de ambas directivas

Siga las instrucciones que se indican en [Asignación de perfiles de dispositivo](how-to-assign-device-profiles.md) para asignar ambos perfiles a los usuarios o dispositivos necesarios.

