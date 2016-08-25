---
title: "VPN por aplicación para Android mediante Pulse Secure | Microsoft Intune"
description: "Puede crear un perfil de VPN por aplicación para dispositivos Android administrados por Intune."
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a2464a9d2276319f75a3da7db70c2613152bed9b
ms.openlocfilehash: 177ed5f693b8f1ce16d96e1b3e729630d661475f


---

# Usar una directiva personalizada para crear un perfil de VPN por aplicación para dispositivos Android

Puede crear un perfil de VPN por aplicación para dispositivos Android administrados por Intune. Primero, cree un perfil de VPN que use el tipo de conexión Pulse Secure. Después, cree una directiva de configuración personalizada que asocie el perfil de VPN con las aplicaciones específicas. Después de implementar la directiva en sus grupos de usuarios o dispositivo Android, cuando un usuario abra una de las aplicaciones especificadas en uno de esos dispositivos, una conexión VPN se abre para esa aplicación.

> [!NOTE]
>
> Para este perfil solo se admite el tipo de conexión Pulse Secure.


### Paso 1: Crear un perfil de VPN

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Directiva** > **Agregar directiva**.
2. Para seleccionar una plantilla para la nueva directiva, expanda **Android** y, después, elija **Perfil de VPN (Android 4 y versiones posteriores)**.
3. En la plantilla, para **Tipo de conexión**, elija **Pulse Secure**.
4. Complete y guarde el perfil de VPN. Para obtener más información sobre los perfiles de VPN, vea [Conexiones VPN](../deploy-use/vpn-connections-in-microsoft-intune.md).

> [!NOTE]
>
> Tome nota del nombre del perfil de VPN para usarlo en el paso siguiente. Por ejemplo, MyAppVpnProfile.

### Paso 2: Crear una directiva de configuración personalizada

   1. En la consola de administración de Intune, elija **Directiva** > **Agregar directiva** > **Android** > **Configuración personalizada** > **Crear directiva**.
   2. Especifique un nombre para la directiva.
   3. En **Configuración de OMA-URI**, elija **Agregar**.
   4. Proporcione un nombre de configuración.
   5. Para **Tipo de datos**, especifique **Cadena**.
   6. Para **OMA-URI**, especifique esta cadena: **./Vendor/MSFT/VPN/Profile/*Name*/PackageList**, donde *Name* es el nombre del perfil de VPN que ha anotado en el paso 1. En nuestro ejemplo, la cadena sería **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
   7.   En **Valor**, cree una lista de los paquetes que se van a asociar con el perfil separados por punto y coma. Por ejemplo, si quiere que Excel y el explorador Google Chrome usen la conexión VPN, escriba: **com.microsoft.office.excel;com.android.chrome**.


    ![Directiva personalizada de ejemplo de VPN por aplicación de Android](..\media\android_per_app_vpn_oma_uri.png)

#### Establecer la lista de aplicaciones como lista negra o lista blanca (opcional)
  Puede especificar una lista de aplicaciones que *no pueden* usar la conexión VPN mediante el valor **BLACKLIST**. Todas las demás aplicaciones se conectarán a través de la VPN.
De manera alternativa, puede usar el valor **WHITELIST** para especificar una lista de aplicaciones que *pueden* usar la conexión VPN. Las aplicaciones que no están en la lista no se conectarán a través de la VPN.
  1.    En **Configuración de OMA-URI**, elija **Agregar**.
  2.    Proporcione un nombre de configuración.
  3.    Para **Tipo de datos**, especifique **Cadena**.
  4.    Para **OMA-URI**, use esta cadena: **./Vendor/MSFT/VPN/Profile/*Name*/Mode**, donde *Name* es el nombre del perfil de VPN que ha anotado en el paso 1. En nuestro ejemplo, la cadena sería **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  5.    En **Valor**, escriba **BLACKLIST** o **WHITELIST**.



### Paso 3: Implementar ambas directivas

Debe implementar *ambas* directivas en los *mismos* grupos de Intune.

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, después, haga clic en **Administrar implementación**.
2.  En el cuadro de diálogo **Administrar la implementación** :
    -   **Para implementar la directiva**, seleccione uno o más grupos en los que quiera implementar la directiva y elija **Agregar** > **Aceptar**.
    -   **Para cerrar el cuadro de diálogo sin implementar la directiva**, elija **Cancelar**.

En el área de trabajo **Directiva** de la página **General** , un resumen de estado y las alertas identifican los problemas de la directiva que requieren su atención. Además, aparece un resumen de estado en el área de trabajo **Panel**.



<!--HONumber=Aug16_HO3-->


