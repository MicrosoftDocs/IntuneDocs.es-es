---
title: "Usar el restablecimiento de código de acceso y el bloqueo remoto | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
translationtype: Human Translation
ms.sourcegitcommit: 6d9b79a09eef2546d78a19e061ba5cc3f24f645c
ms.openlocfilehash: 34379881b8299a2e3f9886b14b6d83e9dfe83373

---
# Ayudar a proteger los dispositivos con el restablecimiento de código de acceso y el bloqueo remoto
Microsoft Intune proporciona funcionalidades de restablecimiento de código de acceso y de bloqueo remoto.

## Bloquear un dispositivo de forma remota
Si un usuario pierde su dispositivo, es posible bloquear el dispositivo de forma remota. La tabla siguiente muestra el modo en que se puede utilizar el bloqueo remoto en distintas plataformas móviles.

|Plataforma|Bloqueo remoto|
|------------|---------------|
|iOS|Compatible.|
|Android|Compatible.|
|Windows 10 Mobile|Compatible.|
|Windows Phone 8 y Windows Phone 8.1|Compatible.|
|Windows RT 8.1 y Windows RT|Compatible si el usuario actual del dispositivo es el mismo usuario que inscribió el dispositivo.|
|Windows 8.1|Compatible si el usuario actual del dispositivo es el mismo usuario que inscribió el dispositivo.|


### Cómo bloquear un dispositivo móvil de forma remota a través de la consola de Intune

1.  En la [consola de administrador de Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos móviles**.

2.  Seleccione **Todos los dispositivos administrados directamente** para ver los dispositivos inscritos en Intune o **Todos los dispositivos administrados por Exchange ActiveSync**.

    > [!TIP]
    > También puede desplazarse a un dispositivo mediante un usuario. Elija **Todos los usuarios**. En la página Propiedades del usuario, elija **Dispositivos** y después elija el nombre del dispositivo móvil que quiere borrar.

3.  En la lista, elija el dispositivo o los dispositivos que quiere bloquear. En la barra de tareas, seleccione **Tareas remotas** y luego **Bloqueo remoto**.

## Restablecer el código de acceso en un dispositivo
Si un usuario olvida su contraseña, puede ayudarle quitando la contraseña de un dispositivo o forzar el uso de una nueva contraseña temporal en un dispositivo. La tabla siguiente muestra el modo en que se puede restablecer la contraseña en distintas plataformas móviles.

|Plataforma|Restablecimiento de la contraseña|
|------------|------------------|
|iOS|Permite borrar la contraseña de un dispositivo. No admite la creación de una nueva contraseña temporal.|
|Android|Permite restablecer y crear una contraseña temporal.|
|Windows 10 Mobile|Compatible.|
|Windows Phone 8 y Windows Phone 8.1|Compatible.|
|Windows RT 8.1 y Windows RT|No compatible.|
|Windows 8.1|No compatible.|

### Cómo restablecer un código de acceso

1.  En la [consola de administrador de Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos móviles**.

2.  Seleccione **Todos los dispositivos administrados directamente** para ver los dispositivos inscritos en Intune o **Todos los dispositivos administrados por Exchange ActiveSync**.

    > [!TIP]
    > También puede desplazarse a un dispositivo mediante un usuario. Haga clic en **Todos los usuarios**. En la página Propiedades del usuario, haga clic en **Dispositivos** y luego haga clic en el nombre del dispositivo móvil que quiere borrar.

3.  En la lista, elija el dispositivo o los dispositivos que quiere bloquear. En la barra de tareas, seleccione **Tareas remotas** y luego **Restablecimiento de código de acceso**.


### Consulte también
[Retirar dispositivos](retire-devices-from-microsoft-intune-management.md)
[Windows Selective Wipe for Device Data Management (Borrado selectivo de Windows para la administración de datos del dispositivo)](http://technet.microsoft.com/library/dn486874.aspx)



<!--HONumber=Jul16_HO3-->


