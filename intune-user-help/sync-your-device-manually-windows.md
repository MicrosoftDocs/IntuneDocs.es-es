---
title: Sincronizar manualmente el dispositivo Windows | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4666779620aa0404c12107a374280c403d66bec3
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55840219"
---
# <a name="sync-your-windows-device-manually"></a>Sincronización manual del dispositivo Windows

Cuando la velocidad de la instalación de las aplicaciones no sea la ideal, inicie una sincronización manual del dispositivo. Las sincronizaciones manuales obligan al dispositivo a conectarse con Intune para recibir las actualizaciones y comunicaciones más recientes. La velocidad de instalación puede aumentar una vez que se completa la sincronización del dispositivo.

Intune admite la sincronización manual desde la aplicación Portal de empresa, desde la barra de tareas del escritorio o el menú Inicio y desde la aplicación de configuración del dispositivo. 

La funcionalidad de la aplicación Portal de empresa es compatible con dispositivos Windows 10 que ejecutan Creator's Update (1703) o una versión posterior. 
* [Sincronización desde la aplicación Portal de empresa](#Sync-from-Company-Portal-app-for-Windows)  

Todos los dispositivos Windows se pueden sincronizar desde la aplicación de configuración del dispositivo, incluidos:

* [Windows 10 desktop](#windows-10-desktop)  
* [Microsoft HoloLens](#microsoft-hololens)   
* [Windows 10 Mobile](#windows-10-mobile)  
* [Windows Phone 8.1](#windows-phone-81)    

## <a name="sync-directly-from-company-portal-app-for-windows"></a>Sincronización directa desde la aplicación Portal de empresa para Windows
Complete estos pasos para sincronizar manualmente cualquier dispositivo Windows 10 que ejecute Creator's Update (versión 1703) o posterior.

1.  Abra la aplicación Portal de empresa en el dispositivo.

2.  Seleccione **Configuración** > **Sincronizar**.

    ![Captura de pantalla de la página principal de la aplicación Portal de empresa, con la opción Configuración resaltada](./media/RS1_homePage_settings_04.png)  
    
    ![Captura de pantalla de la página de configuración de la aplicación Portal de empresa, con el botón Sincronizar resaltado](./media/RS1_settingspage_sync05.png)  

## <a name="sync-from-device-taskbar-or-start-menu"></a>Sincronización desde la barra de tareas del dispositivo o el menú Inicio   

También puede acceder al control de sincronización fuera de la aplicación, desde el escritorio del dispositivo. Esta manera es útil si tiene la aplicación anclada directamente a la barra de tareas o al menú Inicio y desea sincronizar rápidamente.  

1. Busque el icono de la aplicación Portal de empresa en la barra de tareas o el menú Inicio.  
2. Haga clic con el botón derecho en el icono de la aplicación para que aparezca su menú (que también se denomina lista de accesos directos).  

    ![Captura de pantalla de la barra de tareas de Windows en el escritorio de un dispositivo. Se ha hecho clic en el icono de la aplicación Portal de empresa para mostrar un menú con las opciones "Pin to taskbar" (Anclar a la barra de tareas) y "Cerrar ventana", y la acción "Sync this device" (Sincronizar este dispositivo).](./media/sync-device-from-start-menu-1807.png)  

3. Seleccione **Sync this device** (Sincronizar este dispositivo). La aplicación Portal de empresa se abrirá en la página **Configuración** e iniciará la sincronización.  

## <a name="sync-from-settings-app"></a>Sincronización desde la aplicación de configuración 
Complete estos pasos para sincronizar manualmente los dispositivos Microsoft HoloLens, Windows 10 Escritorio, Windows 10 Mobile o Windows Phone 8.1 desde la aplicación de configuración.  

### <a name="windows-10-desktop"></a>Windows 10 Escritorio
1. En el dispositivo, seleccione **Inicio** > **Configuración**.

2. Seleccione **Cuentas**.

    ![Elección de cuentas en la página de configuración](./media/win10pc-sync-2-settings-accounts.png)  

3. Existen varias versiones de Windows 10 para equipos de escritorio. Compare su pantalla con las capturas de pantalla que aparecen a continuación para determinar los pasos que debe seguir. 

    * Si su pantalla indica **Acceso profesional o educativo**, vaya a los pasos que aparecen en [Acceso profesional o educativo](#access-work-or-school).

    ![Opción Acceso profesional o educativo en la aplicación de configuración](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

    * Si la pantalla indica **Acceso al trabajo**, vaya a los pasos que aparecen en [Acceso al trabajo](#work-access).  

    ![Elección del acceso al trabajo como tipo de cuenta](./media/win10pc-sync-3-work-access.png)

#### <a name="access-work-or-school-steps"></a>Pasos de Acceso profesional o educativo

1. Haga clic en **Acceso profesional o educativo**.

    ![Captura de pantalla que muestra la opción Acceso al trabajo o educativo](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

2. Seleccione la cuenta con el icono de maletín. Si no ve esta cuenta, es posible que la empresa haya aplicado una configuración distinta. En su lugar, haga clic en la cuenta con el logotipo de Microsoft.

     ![Elija el nombre de la cuenta junto al maletín o el logotipo de Microsoft](./media/win10pc-rs1-sync-info-button.png)

3. Haga clic en **Información**. 

4. Haga clic en **Sincronizar**. 

#### <a name="work-access-steps"></a>Pasos de Acceso al trabajo

1.  Haga clic en **Acceso al trabajo**.

    ![Elección del acceso al trabajo como tipo de cuenta](./media/win10pc-sync-3-work-access.png)

2. En **Enroll in to device management** (Inscribirse en la administración de dispositivos), seleccione el nombre de la empresa.

    ![Elección del nombre de la empresa para la administración de dispositivos](./media/win10pc-sync-4-tap-com-name.png)

3. Haga clic en **Sincronizar**. El botón queda deshabilitado hasta que se completa la sincronización.

    ![Elección del botón Sincronizar](./media/win10pc-sync-5-tap-sync.png)  


### <a name="windows-10-mobile"></a>Windows 10 Mobile

   1. En el dispositivo, vaya a **Todas las aplicaciones** > **Configuración** > **Cuentas**.

       ![Elección de cuentas en la pantalla de configuración](./media/win10m-sync-1-settings-accounts.png)

   2. Seleccione **Acceso al trabajo**.

       ![Elección del acceso al trabajo como tipo de cuenta](./media/win10m-sync-2-work-access.png)

   3. En **Enroll in to device management** (Inscribirse en la administración de dispositivos), seleccione el nombre de la empresa.

       ![Elección del nombre de la empresa para la administración de dispositivos](./media/win10m-sync-3-tap-comp-name.png)

   4. Seleccione el icono **Sincronizar**. El botón queda deshabilitado hasta que se completa la sincronización.

       ![Elección del icono Sincronizar](./media/win10m-sync-4-tap-sync.png)  
### <a name="microsoft-hololens"></a>Microsoft HoloLens  
Estas instrucciones se aplican a los dispositivos HoloLens que ejecutan la Actualización de aniversario de Windows 10 (también conocida como RS1). 
1.  Abra la aplicación de configuración del dispositivo.  

2.  Seleccione **Cuentas** > **Acceso al trabajo**.  
    ![Captura de pantalla de la aplicación de configuración de HoloLens, con el vínculo de cuentas resaltado](./media/RS1_holoLens_SettingsRS1_Accounts_06.png)  

3.  Seleccione la cuenta conectada > **Sincronizar**. ![Captura de pantalla de la aplicación de configuración de HoloLens, con el botón de sincronización resaltado](./media/RS1_holoLens_SyncRS1_Sync_08.png)  

### <a name="windows-phone-81"></a>Windows Phone 8,1

1. Vaya a **Todas las aplicaciones** > **Configuración** > **Área de trabajo**.

    ![Lista de configuración](./media/wp81-1-sync-settings-workplace.png)

2. Seleccione el nombre de la empresa.

    ![Elección del nombre de la empresa para la cuenta de trabajo](./media/wp81-2-sync-tap-compname.png)

3. Seleccione el icono **Sincronizar**.

    ![Elección del icono Sincronizar](./media/wp81-3-sync-tap-sync-button.png)

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
