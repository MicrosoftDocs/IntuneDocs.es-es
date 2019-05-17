---
title: Perfil de VPN por aplicación personalizado para Android
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo crear un perfil de VPN por aplicación para dispositivos Android administrados por Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/05/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38763d5c16d5cba36220c03e9d74b30a465d752b
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568471"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Use un perfil personalizado de Microsoft Intune para crear un perfil de VPN por aplicación para dispositivos Android

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Puede crear un perfil de VPN por aplicación para dispositivos Android 5.0 y versiones posteriores administrados con Intune. Primero, cree un perfil de VPN que use el tipo de conexión Pulse Secure o Citrix. Después, cree una directiva de configuración personalizada que asocie el perfil de VPN con las aplicaciones específicas.

Después de asignar la directiva al dispositivo Android o a los grupos de usuarios, los usuarios deben iniciar el cliente de la VPN Pulse Secure o Citrix. El cliente de VPN permite el tráfico solo desde las aplicaciones especificadas para usar la conexión VPN abierta.

> [!NOTE]
>
> Para este perfil solo se admite el tipo de conexión Pulse Secure y Citrix.


## <a name="step-1-create-a-vpn-profile"></a>Paso 1: Crear un perfil de VPN


1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Configuración del dispositivo**.
2. En el panel **Configuración del dispositivo**, en la sección **Administrar**, elija **Perfiles**.
2. En el panel de la lista de perfiles, elija **Crear perfil**.
3. En el panel **Crear perfil**, escriba un **Nombre** y una **Descripción** opcional para el perfil de VPN.
4. En la lista desplegable **Plataforma**, elija **Android**.
5. En la lista desplegable de **tipos de perfil**, elija **VPN**.
3. Elija **Configuración** > **Configurar** y luego configure el perfil de VPN según la configuración de [Configuración de VPN](vpn-settings-configure.md) y [Configuración de VPN de Intune para dispositivos Android](vpn-settings-android.md).

Anote el **nombre de la conexión**, que es el valor que debe especificar al crear el perfil de VPN. Lo necesitará en el paso siguiente. Por ejemplo, **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Paso 2: Crear una directiva de configuración personalizada

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Configuración del dispositivo**.
2. En el panel **Configuración del dispositivo**, en la sección **Administrar**, elija **Perfiles**.
3. En el panel Perfiles, haga clic en **Crear perfil**.
4. En el panel **Crear perfil**, escriba un **Nombre** y una **Descripción** para el perfil personalizado.
5. En la lista desplegable **Plataforma**, elija **Android**.
6. En la lista desplegable de **tipos de perfil**, elija **Personalizado**.
7. Elija **Configuración** > **Configurar**.
3. En el panel **Configuración OMA-URI personalizada**, elija **Agregar**.
    - Proporcione un nombre de configuración.
    - En **OMA-URI**, escriba esta cadena: **./Vendor/MSFT/VPN/Profile/*Nombre*/PackageList**, donde *Nombre* es el nombre de la conexión que anotó en el paso 1. En nuestro ejemplo, la cadena sería **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
    - Para **Tipo de datos**, especifique **Cadena**.
    - En **Valor**, cree una lista de los paquetes que se van a asociar con el perfil separados por punto y coma. Por ejemplo, si quiere que Excel y el explorador Google Chrome usen la conexión VPN, escriba: **com.microsoft.office.excel;com.android.chrome**.

![Directiva personalizada de ejemplo de VPN por aplicación de Android](./media/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Establecer la lista de aplicaciones como lista de bloqueados o lista de permitidos (opcional)
  Puede especificar una lista de aplicaciones que *no pueden* usar la conexión VPN mediante el valor **BLACKLIST**. Todas las demás aplicaciones se conectan a través de la VPN.
De manera alternativa, puede usar el valor **WHITELIST** para especificar una lista de aplicaciones que *pueden* usar la conexión VPN. Las aplicaciones que no están en la lista no se conectan a través de la VPN.
  1.    En el panel **Configuración OMA-URI personalizada**, elija **Agregar**.
  2.    Proporcione un nombre de configuración.
  3.    Para **OMA-URI**, use esta cadena: **./Vendor/MSFT/VPN/Profile/*Nombre*/Mode**, donde *Nombre* es el nombre del perfil de VPN que anotó en el paso 1. En nuestro ejemplo, la cadena sería **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  4.    Para **Tipo de datos**, especifique **Cadena**.
  5.    En **Valor**, escriba **BLACKLIST** o **WHITELIST**.



## <a name="step-3-assign-both-policies"></a>Paso 3: Asignar ambas directivas

Siga las instrucciones que se indican en [Asignación de perfiles de dispositivo](device-profile-assign.md) para asignar ambos perfiles a los usuarios o dispositivos necesarios.
