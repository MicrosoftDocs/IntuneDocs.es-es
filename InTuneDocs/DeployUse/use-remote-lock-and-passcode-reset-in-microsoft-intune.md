---
title: "Usar bloqueo remoto y restablecimiento de código de acceso | Microsoft Intune"
description: "Intune proporciona funciones de bloqueo remoto y restablecimiento de código de acceso."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
translationtype: Human Translation
ms.sourcegitcommit: 899f50cfec9e7c20d2981c077f93e0fccf37dc2b
ms.openlocfilehash: 0b52bd8360f11e226674aefe80a578c451c2679d

---
# Protección de los dispositivos mediante el bloqueo remoto y el restablecimiento de código de acceso
Microsoft Intune proporciona funciones de bloqueo remoto y restablecimiento de código de acceso.

## Bloquear un dispositivo de forma remota
Si un usuario pierde su dispositivo, es posible bloquear el dispositivo de forma remota. La tabla siguiente muestra el modo en que se puede utilizar el bloqueo remoto en distintas plataformas móviles. No se admite el bloqueo remoto

|Plataforma|Bloqueo remoto|
|------------|---------------|
|iOS|Compatible.|
|Android|Compatible.|
|Windows 10 y Windows 10 Mobile|Compatible.|
|Windows Phone 8 y Windows Phone 8.1|Compatible.|
|Windows RT 8.1 y Windows RT|Compatible si el usuario actual del dispositivo es el mismo usuario que inscribió el dispositivo.|
|Windows 8.1|Compatible si el usuario actual del dispositivo es el mismo usuario que inscribió el dispositivo.|

No se admite el bloqueo remoto para equipos Windows inscritos con el cliente de software de Intune.

### Para bloquear un dispositivo móvil de forma remota a través de la consola de Intune

1.  En la [consola de administrador de Intune](https://manage.microsoft.com/), elija **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos móviles**.

2.  Elija **Todos los dispositivos administrados directamente** para ver los dispositivos inscritos en Intune o en **Todos los dispositivos administrados por Exchange ActiveSync**.

    > [!TIP]
    > También puede desplazarse a un dispositivo mediante un usuario. Elija **Todos los usuarios**. En la página de propiedades del usuario, elija **Dispositivos** y luego elija el nombre del dispositivo móvil que quiera borrar.

3.  En la lista, elija los dispositivos que quiera bloquear. En la barra de tareas, elija **Tareas remotas** y seleccione **Bloqueo remoto**.

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

No se admite el restablecimiento de código de acceso para equipos Windows inscritos con el cliente de software de Intune.

### Para restablecer un código de acceso

1.  En la [consola de administrador de Intune](https://manage.microsoft.com/), elija **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los dispositivos móviles**.

2.  Elija **Todos los dispositivos administrados directamente** para ver los dispositivos inscritos en Intune o en **Todos los dispositivos administrados por Exchange ActiveSync**.

    > [!TIP]
    > También puede desplazarse a un dispositivo mediante un usuario. Haga clic en **Todos los usuarios**. En la página de propiedades del usuario, haga clic en **Dispositivos** y luego haga clic en el nombre del dispositivo móvil que quiera borrar.

3.  En la lista, elija los dispositivos que quiera bloquear. En la barra de tareas, elija **Tareas remotas** y seleccione **Restablecimiento de código de acceso**.


### Consulte también
[Retirar dispositivos](retire-devices-from-microsoft-intune-management.md)
[Borrado selectivo de Windows para la administración de datos del dispositivo](http://technet.microsoft.com/library/dn486874.aspx)



<!--HONumber=Sep16_HO2-->


