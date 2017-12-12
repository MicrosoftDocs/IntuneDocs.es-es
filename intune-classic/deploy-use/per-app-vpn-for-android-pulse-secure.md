---
title: "VPN por aplicación para Android mediante Pulse Secure"
description: "Puede crear un perfil de VPN por aplicación para dispositivos Android administrados por Intune."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 65bd7e15a49d5b563b6a095593ca5d8d5316a1fa
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="use-a-custom-policy-to-create-a-per-app-vpn-profile-for-android-devices"></a>Usar una directiva personalizada para crear un perfil de VPN por aplicación para dispositivos Android

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Puede crear un perfil de VPN por aplicación para dispositivos Android 5.0 y versiones posteriores administrados con Intune. Primero, cree un perfil de VPN que use el tipo de conexión Pulse Secure o Citrix. Después, cree una directiva de configuración personalizada que asocie el perfil de VPN con las aplicaciones específicas. 

Después de implementar la directiva en los grupos de usuarios o en el dispositivo Android, los usuarios deben iniciar la VPN Pulse Secure o Citrix, que permitirá el tráfico solo desde las aplicaciones especificadas para usar la conexión VPN abierta.

> [!NOTE]
>
> Para este perfil solo se admite el tipo de conexión Pulse Secure y Citrix.


### <a name="step-1-create-a-vpn-profile"></a>Paso 1: Crear un perfil de VPN

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Directiva** > **Agregar directiva**.
2. Para seleccionar una plantilla para la nueva directiva, expanda **Android** y, después, elija **Perfil de VPN (Android 4 y versiones posteriores)**.
3. En la plantilla, para **Tipo de conexión**, seleccione **Pulse Secure** o **Citrix**.
4. Complete y guarde el perfil de VPN. Para obtener más información sobre los perfiles de VPN, vea [Conexiones VPN](../deploy-use/vpn-connections-in-microsoft-intune.md).

> [!NOTE]
>
> Anote el **nombre de la conexión VPN (mostrado a los usuarios):** el valor especificado al crear el perfil de VPN. Lo necesitará en el paso siguiente. Por ejemplo, **MyAppVpnProfile**.

### <a name="step-2-create-a-custom-configuration-policy"></a>Paso 2: Crear una directiva de configuración personalizada

   1. En la consola de administración de Intune, elija **Directiva** > **Agregar directiva** > **Android** > **Configuración personalizada** > **Crear directiva**.
   2. Especifique un nombre para la directiva.
   3. En **Configuración de OMA-URI**, elija **Agregar**.
   4. Proporcione un nombre de configuración.
   5. Para **Tipo de datos**, especifique **Cadena**.
   6. Para **OMA-URI**, especifique esta cadena: **./Vendor/MSFT/VPN/Profile/*Name*/PackageList**, donde *Name* es el nombre del perfil de VPN que anotó en el paso 1. En nuestro ejemplo, la cadena sería **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
   7.   En **Valor**, cree una lista de los paquetes que se van a asociar con el perfil separados por punto y coma. Por ejemplo, si quiere que Excel y el explorador Google Chrome usen la conexión VPN, escriba: **com.microsoft.office.excel;com.android.chrome**.

![Directiva personalizada de ejemplo de VPN por aplicación de Android](./media/android_per_app_vpn_oma_uri.png)

#### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Establecer la lista de aplicaciones como lista de bloqueados o lista de permitidos (opcional)
  Puede especificar una lista de aplicaciones que *no pueden* usar la conexión VPN mediante el valor **BLACKLIST**. Todas las demás aplicaciones se conectarán a través de la VPN.
De manera alternativa, puede usar el valor **WHITELIST** para especificar una lista de aplicaciones que *pueden* usar la conexión VPN. Las aplicaciones que no están en la lista no se conectarán a través de la VPN.
  1.    En **Configuración de OMA-URI**, elija **Agregar**.
  2.    Proporcione un nombre de configuración.
  3.    Para **Tipo de datos**, especifique **Cadena**.
  4.    Para **OMA-URI**, use esta cadena: **./Vendor/MSFT/VPN/Profile/*Name*/Mode**, donde *Name* es el nombre del perfil de VPN que anotó en el paso 1. En nuestro ejemplo, la cadena sería **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  5.    En **Valor**, escriba **BLACKLIST** o **WHITELIST**.



### <a name="step-3-deploy-both-policies"></a>Paso 3: Implementar ambas directivas

Debe implementar *ambas* directivas en los *mismos* grupos de Intune.

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, después, haga clic en **Administrar implementación**.
2.  En el cuadro de diálogo **Administrar la implementación** :
    -   **Para implementar la directiva**, seleccione uno o más grupos en los que quiera implementar la directiva y elija **Agregar** > **Aceptar**.
    -   **Para cerrar el cuadro de diálogo sin implementar la directiva**, elija **Cancelar**.

En el área de trabajo **Directiva** de la página **General** , un resumen de estado y las alertas identifican los problemas de la directiva que requieren su atención. Además, aparece un resumen de estado en el área de trabajo **Panel**.
