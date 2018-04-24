---
title: Restablecimiento del bloqueo remoto y el código de acceso
description: Intune proporciona funcionalidades de restablecimiento de código de acceso y de bloqueo remoto.
keywords: ''
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.custom: intune-classic
ms.openlocfilehash: fc1cad418904de335b434a3726e2772d0558b303
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="help-protect-your-devices-with-remote-lock-and-passcode-reset"></a>Ayudar a proteger los dispositivos con el restablecimiento de código de acceso y el bloqueo remoto

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune proporciona funcionalidades de restablecimiento de código de acceso y de bloqueo remoto.

## <a name="lock-a-device-remotely"></a>Bloquear un dispositivo de forma remota
Si un usuario pierde su dispositivo, es posible bloquearlo de forma remota. El dispositivo debe tener ya un PIN o código de acceso establecido en él para poder usar el bloqueo remoto.

La tabla siguiente muestra el modo en que se puede usar el bloqueo remoto en distintas plataformas móviles.

|Plataforma|Bloqueo remoto|
|------------|---------------|
|macOS|No compatible|
|iOS|Compatible.|
|Android|Compatible.|
|Android for Work|Compatible.|
|Windows 10 Mobile|Compatible.|
|Windows 10 Escritorio|No compatible|
|Windows Phone 8 y Windows Phone 8.1|Compatible.|
|Windows RT 8.1 y Windows RT|Compatible si el usuario actual del dispositivo es el mismo usuario que inscribió el dispositivo.|
|Windows 8.1|Compatible si el usuario actual del dispositivo es el mismo usuario que inscribió el dispositivo.|

No se admite el bloqueo remoto para equipos Windows inscritos con el cliente de software de Intune.

### <a name="lock-a-mobile-device-remotely-through-the-intune-console"></a>Bloqueo de un dispositivo móvil de forma remota a través de la consola de Intune

1.  En la [consola de administrador de Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos móviles**.

2.  Seleccione **Todos los dispositivos administrados directamente** para ver los dispositivos inscritos en Intune o **Todos los dispositivos administrados por Exchange ActiveSync**.

    > [!TIP]
    > También puede desplazarse a un dispositivo mediante un usuario. Elija **Todos los usuarios**. En la página de propiedades del usuario, elija **Dispositivos** y luego elija el nombre del dispositivo móvil que quiere bloquear.

3.  En la lista, elija el dispositivo o los dispositivos que quiere bloquear. En la barra de tareas, seleccione **Tareas remotas** y luego **Bloqueo remoto**.

## <a name="reset-the-passcode-on-a-device"></a>Restablecer el código de acceso en un dispositivo
Si un usuario olvida su código de acceso, puede quitar la contraseña de un dispositivo o forzar el uso de una nueva contraseña temporal en un dispositivo. En la tabla siguiente se muestra cómo se puede restablecer la contraseña en distintas plataformas móviles.

|Plataforma|Restablecimiento de la contraseña|
|------------|------------------|
|macOS|No compatible|
|iOS|Permite borrar la contraseña de un dispositivo. No admite la creación de una nueva contraseña temporal.|
|Android|Compatible con versiones anteriores a Android 7.0. Crea un código de acceso temporal.|
|Android for Work|No compatible|
|Windows 10 Mobile|Compatible con los dispositivos móviles con la versión Windows 10 Creator y posteriores que están unidos a Azure AD.|
|Windows Phone 8 y Windows Phone 8.1|Compatible.|
|Windows RT 8.1|No compatible.|
|Windows 8.1|No compatible.|
|Windows 10 Escritorio|No compatible.|

No se admite el restablecimiento de código de acceso para equipos Windows inscritos con el cliente de software de Intune.

### <a name="reset-a-passcode"></a>Restablecer un código de acceso

1.  En la [consola de administrador de Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos móviles**.

2.  Seleccione **Todos los dispositivos administrados directamente** para ver los dispositivos inscritos en Intune o **Todos los dispositivos administrados por Exchange ActiveSync**.

    > [!TIP]
    > También puede desplazarse a un dispositivo mediante un usuario. Haga clic en **Todos los usuarios**. En la página de propiedades del usuario, haga clic en **Dispositivos** y luego haga clic en el nombre del dispositivo móvil que quiera borrar.

3.  En la lista, elija el dispositivo o los dispositivos que quiere bloquear. En la barra de tareas, seleccione **Tareas remotas** y luego **Restablecimiento de código de acceso**.


### <a name="see-also"></a>Vea también
[Retirar dispositivos](retire-devices-from-microsoft-intune-management.md) y [Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx) (Eliminación selectiva de Windows para la administración de datos del dispositivo)
