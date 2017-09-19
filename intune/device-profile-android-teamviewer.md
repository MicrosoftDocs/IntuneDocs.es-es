---
title: "Administración remota de dispositivos Android mediante TeamViewer"
titlesuffix: Azure portal
description: Aprenda a administrar de forma remota dispositivos Android con TeamViewer.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a6286760e1e49cdb090736e9444fe8ce18ddeb7
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2017
---
# <a name="provide-remote-assistance-for-intune-managed-android-devices"></a>Asistencia remota para dispositivos Android administrados con Intune

Intune puede usar el software [TeamViewer](https://www.teamviewer.com), que se compra de forma independiente, para permitirle ofrecer asistencia remota a los usuarios de dispositivos Android. Use la información de este tema para empezar a trabajar.

## <a name="before-you-start"></a>Antes de empezar

### <a name="required-permissions"></a>Permisos necesarios

Asegúrese de que el usuario del portal de Azure tenga asignados los siguientes permisos como un [rol de Intune](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control):
- Para dejar que el administrador modifique la configuración del conector de TeamViewer, conceda el permiso para **actualizar la Asistencia remota**.
- Para permitir que el administrador inicie una nueva solicitud de asistencia remota, conceda el permiso **Solicitar asistencia remota**. Los usuarios con el permiso **Solicitar asistencia remota** pueden solicitar iniciar una sesión de cualquier usuario. El ámbito de la asignación de roles de Intune no impone ninguna limitación. Los ámbitos de asignación de roles de Intune no limitan los dispositivos o los usuarios para los que se puede iniciar solicitudes de Asistencia remota.

>[!NOTE]
>Al habilitar TeamViewer, va a permitir que el conector TeamViewer para Intune cree sesiones de TeamViewer, lea datos de Active Directory y guarde el token de acceso de la cuenta de TeamViewer.

### <a name="configure-the-intune-teamviewer-connector"></a>Configuración del conector de TeamViewer

Para proporcionar asistencia remota a dispositivos Android, debe configurar el conector TeamViewer para Intune mediante los pasos siguientes:


1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Configuración** > **TeamViewer Connector**.
5. En la hoja **TeamViewer Connector**, haga clic en **Habilitar** y luego vea y acepte el contrato de licencia del servicio de TeamViewer.
6. Elija **Inicie sesión en TeamViewer para autorizar**.
7. Se abre una página web en el sitio de TeamViewer. Escriba sus credenciales de la licencia de TeamViewer y, a continuación, haga clic en **Iniciar sesión**.


## <a name="how-to-remotely-administer-an-android-device"></a>Administración de un dispositivo Android de forma remota

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos**, elija **Administrar** > **Todos los dispositivos**.
5. Seleccione el dispositivo que desea administrar de forma remota y luego, en la hoja de propiedades del dispositivo, elija **Más** > **Nueva sesión de Asistencia remota**.
6. Después de que Intune se conecte al servicio TeamViewer, verá alguna información sobre el dispositivo de Android. Elija **Conectar** para iniciar la sesión remota.

![Ventanas de TeamViewer en Android](./media/android-teamviewer.png)

En la ventana de TeamViewer, puede realizar diversas acciones remotas en el dispositivo Android, como el control remoto del dispositivo. Para obtener detalles completos de las acciones que puede realizar, consulte la [documentación de TeamViewer](https://www.teamviewer.com/support/documents/).

Cuando haya finalizado, cierre la ventana de TeamViewer.

## <a name="end-user-notifications"></a>Notificaciones de usuario final

Los usuarios finales verán una marca de notificación en el icono de la aplicación del Portal de empresa de su dispositivo y también verán una notificación cuando abran la aplicación. A continuación, pueden aceptar la solicitud de asistencia remota.

