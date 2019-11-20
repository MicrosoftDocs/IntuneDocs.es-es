---
title: Perfil de VPN por aplicación personalizado para Android
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo crear un perfil de VPN por aplicación para dispositivos Android administrados por Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3683d2aeada791c6ec827e915e02365a336e6045
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059675"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Use un perfil personalizado de Microsoft Intune para crear un perfil de VPN por aplicación para dispositivos Android

[!INCLUDE[azure_portal](../includes/azure_portal.md)]

Puede crear un perfil de VPN por aplicación para dispositivos Android 5.0 y versiones posteriores administrados con Intune. Primero, cree un perfil de VPN que use el tipo de conexión Pulse Secure o Citrix. Después, cree una directiva de configuración personalizada que asocie el perfil de VPN con las aplicaciones específicas.

Después de asignar la directiva al dispositivo Android o a los grupos de usuarios, los usuarios deben iniciar el cliente de la VPN Pulse Secure o Citrix. El cliente de VPN permite el tráfico solo desde las aplicaciones especificadas para usar la conexión VPN abierta.

> [!NOTE]
>
> Para este perfil solo se admite el tipo de conexión Pulse Secure y Citrix.

## <a name="step-1-create-a-vpn-profile"></a>Paso 1: Crear un perfil de VPN

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. Asígnele un nombre a los perfiles para que pueda identificarlos de manera sencilla más adelante. Por ejemplo, un buen nombre de perfil sería **Perfil de VPN de Android por aplicación en toda la empresa**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: Seleccione **Android**.
    - **Tipo de perfil**: seleccione **VPN**.

4. Elija **Configuración** > **Configurar** y luego configure el perfil de VPN según la configuración de [Configuración de VPN](vpn-settings-configure.md) y [Configuración de VPN de Intune para dispositivos Android](vpn-settings-android.md).

Anote el **nombre de la conexión**, que es el valor que debe especificar al crear el perfil de VPN. Lo necesitará en el paso siguiente. Por ejemplo, **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Paso 2: Crear una directiva de configuración personalizada

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para el perfil personalizado. Asígnele un nombre a los perfiles para que pueda identificarlos de manera sencilla más adelante. Por ejemplo, un buen nombre de perfil es **Perfil de VPN de Android de OMA-URI personalizado en toda la compañía**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: Seleccione **Android**.
    - **Tipo de perfil**: seleccione **Personalizado**.

4. Elija **Configuración** > **Configurar**.
5. En el panel **Configuración OMA-URI personalizada**, elija **Agregar**.
    - **Nombre**: escriba un nombre para la configuración.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **OMA-URI**: escriba `./Vendor/MSFT/VPN/Profile/*Name*/PackageList`, donde *Nombre* es el nombre de la conexión que anotó en el paso 1. En este ejemplo, la cadena es `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`.
    - **Tipo de datos**: escriba **Cadena**.
    - **Valor**: escriba una lista separada por punto y coma de los paquetes que se van a asociar con el perfil. Por ejemplo, si quiere que Excel y el explorador Google Chrome usen la conexión VPN, escriba `com.microsoft.office.excel;com.android.chrome`.

![Directiva personalizada de ejemplo de VPN por aplicación de Android](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Establecer la lista de aplicaciones como lista de bloqueados o lista de permitidos (opcional)

Puede especificar una lista de aplicaciones que *no pueden* usar la conexión VPN mediante el valor **BLACKLIST**. Todas las demás aplicaciones se conectan a través de la VPN. También, puede usar el valor **WHITELIST** para especificar una lista de aplicaciones que *pueden* usar la conexión VPN. Las aplicaciones que no están en la lista no se conectan a través de la VPN.

1. En el panel **Configuración OMA-URI personalizada**, elija **Agregar**.
2. Proporcione un nombre de configuración.
3. En **OMA-URI**, escriba `./Vendor/MSFT/VPN/Profile/*Name*/Mode`, donde *Name* es el nombre del perfil de VPN que anotó en el paso 1. En nuestro ejemplo, la cadena es `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`.
4. En **Tipo de datos**, escriba **Cadena**.
5. En **Valor**, escriba **BLACKLIST** o **WHITELIST**.

## <a name="step-3-assign-both-policies"></a>Paso 3: Asignar ambas directivas

[Asigne ambos perfiles de dispositivo](device-profile-assign.md) a los usuarios o dispositivos necesarios.
