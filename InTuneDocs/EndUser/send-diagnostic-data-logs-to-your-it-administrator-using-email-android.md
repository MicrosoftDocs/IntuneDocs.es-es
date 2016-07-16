---
title: "Enviar registros de datos de diagnóstico al administrador de TI mediante correo electrónico | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 05/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 85c868e7-8d63-480c-9770-4e99614a5c94
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0bb435b87c937ea118a0794c8332b9a8f268d36e
ms.openlocfilehash: 57646f103fb0520295729a89a30692c657896e55


---


# Enviar registros de datos de diagnóstico al administrador de TI mediante correo electrónico

Si se produce un error en el dispositivo Android mientras está trabajando con las aplicaciones de su centro educativo o empresa o mientras se encuentra en la aplicación Portal de empresa, puede enviar registros de datos de diagnóstico a su administrador de TI para que pueda determinar cuál fue el error y corregirlo. Para incluir todos los detalles en los registros y que así su administrador de TI pueda averiguar cuál fue el problema, active el registro detallado. Puede leer más información sobre el [registro detallado](use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android.md).

Para activar el registro detallado:

1.  Abra la aplicación del portal de empresa.

2.  Pulse en **Menú** &gt; **Configuración**.

    > [!NOTE] 
    > **Menú** puede ser un botón de software o hardware, según el dispositivo Android que tenga.

3.  En la opción **Datos de diagnóstico**, pulse **Enviar datos**.

    > [!NOTE]
    > **Solo si usa dispositivos con Android 6.0 o una versión posterior:** cuando pulse en **Enviar datos**, verá el mensaje **¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?**. 

    Este mensaje puede inducir a error, ya que **Microsoft nunca accede a las fotografías, a los elementos multimedia ni a los archivos del dispositivo**. Google controla el texto del mensaje, por lo que Microsoft no puede cambiarlo.  Al permitir el acceso, lo único que está haciendo es dejar que el dispositivo escriba registros de datos en la tarjeta SD del dispositivo, lo que permite mover esos registros mediante un cable USB.

    Si se deniega el acceso, el mensaje aparecerá de nuevo la próxima vez que pulse **Enviar datos**, pero puede desactivar los mensajes futuros si pulsa en la casilla **No volver a preguntar**.  Si más adelante decide permitir el acceso, vaya a **Configuración** &gt; **Aplicaciones** &gt; **Portal de empresa** &gt; **Permisos** &gt; **Almacenamiento**y active el permiso.

4.  Siga las indicaciones para elegir la aplicación de correo electrónico a través de la cual enviará los registros a su administrador de TI. La aplicación creará un correo electrónico con dirección previa con todos los registros adjuntos.


### Consulte también
[Uso de un dispositivo Android con Intune](using-your-android-device-with-intune.md)


<!--HONumber=Jun16_HO4-->


