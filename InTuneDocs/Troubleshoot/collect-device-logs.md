---
title: Recopilar registros de dispositivo| Microsoft Intune
description: "Obtenga información sobre cómo recopilar registros desde sus dispositivos administrados."
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3a081109cd499d3bdda75cb6c8a4dab9d9d28fab
ms.openlocfilehash: ec7d522e8dcff66d1b84fed3c4c0cc708e555e67


---

# <a name="device-logs"></a>Registros de dispositivo

Su trabajo de solución de problemas es posible que exija la recopilación de registros de dispositivos de usuario. Las instrucciones para recopilar esos registros se detallan aquí. Normalmente necesitará acceso al dispositivo o tendrá que solicitar al usuario que recopile los registros y se los envíe.

### <a name="android-log-location"></a>Ubicación del registro de Android
Los registros de Android se encuentran en *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. El usuario también puede enviar archivos de registro por correo electrónico, como se explica en [Send Android diagnostic data logs to your IT administrator using email (Enviar registros de datos de diagnóstico de Android al administrador de TI por correo electrónico)](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android).

### <a name="ios-logs"></a>Registros de iOS

El usuario puede enviar los errores de inscripción como se explica en [Send iOS enrollment errors to your IT administrator (Enviar errores de inscripción de iOS al administrador de TI)](/intune/enduser/send-errors-to-your-it-admin-ios)

### <a name="mac-os-x-devices"></a>Dispositivos Mac OS X

1. Abra la aplicación **Consola**.
2. En **ARCHIVOS**, seleccione **system.log**.
3. En la barra de menús de la parte superior, seleccione **Archivo** > **Guardar una copia como…** y guarde el archivo.

### <a name="windows-phone"></a>Windows Phone

En el **portal de empresa para Windows Phone**, el usuario tendrá que seleccionar **…** para acceder al menú y luego seleccionar **Enviar registros**. Esta opción está disponible tanto antes como después de iniciar sesión en el portal.

### <a name="windows"></a>Windows

En el portal de empresa para Windows, los registros se encuentran en *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Oct16_HO3-->


