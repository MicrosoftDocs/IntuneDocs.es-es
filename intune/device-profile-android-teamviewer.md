---
title: "Cómo usar dispositivos administrados de forma remota con TeamViewer"
titlesuffix: Azure portal
description: "Obtenga más información sobre cómo administrar dispositivos de forma remota con TeamViewer."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 2/14/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0219993e0322be06dbf9b26707789332039001f1
ms.sourcegitcommit: cccbb6730a8c84dc3a62093b8910305081ac9d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="provide-remote-assistance-for-intune-managed-devices"></a>Proporcione asistencia remota para dispositivos administrados con Intune

Intune puede usar el software [TeamViewer](https://www.teamviewer.com), que se compra por separado, para permitirle ofrecer asistencia remota a los usuarios de los dispositivos que administra. Use la información de este tema para empezar a trabajar.

## <a name="before-you-start"></a>Antes de empezar

### <a name="supported-devices"></a>Dispositivos compatibles

Los dispositivos Android y Windows administrados por Intune se pueden administrar de forma remota.

>[!NOTE]
>Windows Holographic (HoloLens), el equipo de Windows (Surface Hub) y Windows 10 S no son compatibles con el software de TeamViewer.



### <a name="required-permissions"></a>Permisos necesarios

Asegúrese de que el usuario del portal de Azure tenga asignados los siguientes permisos como un [rol de Intune](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control):
- Para dejar que el administrador modifique la configuración del conector de TeamViewer, conceda el permiso para **actualizar la Asistencia remota**.
- Para permitir que el administrador inicie una nueva solicitud de asistencia remota, conceda el permiso **Solicitar asistencia remota**. Los usuarios con el permiso **Solicitar asistencia remota** pueden solicitar iniciar una sesión de cualquier usuario. El ámbito de la asignación de roles de Intune no impone ninguna limitación. Los ámbitos de asignación de roles de Intune no limitan los dispositivos o los usuarios para los que se puede iniciar solicitudes de Asistencia remota.

>[!NOTE]
>Al habilitar TeamViewer, va a permitir que el conector TeamViewer para Intune cree sesiones de TeamViewer, lea datos de Active Directory y guarde el token de acceso de la cuenta de TeamViewer.

### <a name="configure-the-intune-teamviewer-connector"></a>Configuración del conector de TeamViewer

Para proporcionar asistencia remota a los dispositivos, debe configurar el conector TeamViewer de Intune siguiendo estos pasos:


1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Configuración** > **TeamViewer Connector**.
5. En la hoja **TeamViewer Connector**, haga clic en **Habilitar** y luego vea y acepte el contrato de licencia del servicio de TeamViewer.
6. Elija **Inicie sesión en TeamViewer para autorizar**.
7. Se abre una página web en el sitio de TeamViewer. Escriba sus credenciales de la licencia de TeamViewer y, a continuación, haga clic en **Iniciar sesión**.


## <a name="how-to-remotely-administer-a-device"></a>Cómo administrar un dispositivo de forma remota

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos**, elija **Administrar** > **Todos los dispositivos**.
5. Seleccione el dispositivo que desea administrar de forma remota y luego, en la hoja de propiedades del dispositivo, elija **Más** > **Nueva sesión de Asistencia remota**.
6. Cuando Intune se conecte al servicio TeamViewer, verá información sobre el dispositivo. Elija **Conectar** para iniciar la sesión remota.

![Ejemplo de TeamViewer en Android](./media/android-teamviewer.png)

En la ventana de TeamViewer, puede realizar diversas acciones remotas en el dispositivo, como controlarlo de forma remota. Para obtener detalles completos de las acciones que puede realizar, consulte la [documentación de TeamViewer](https://www.teamviewer.com/support/documents/).

Cuando haya finalizado, cierre la ventana de TeamViewer.

## <a name="next-steps"></a>Pasos siguientes

Los usuarios finales ven una marca de notificación en el icono de la aplicación Portal de empresa de los dispositivos y, además, una notificación al abrir la aplicación. A continuación, pueden aceptar la solicitud de asistencia remota.
