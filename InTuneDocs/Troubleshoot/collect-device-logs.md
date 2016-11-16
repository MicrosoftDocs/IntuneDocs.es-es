---
title: Recopilar registros de dispositivo| Microsoft Intune
description: "Obtenga información sobre cómo recopilar registros desde sus dispositivos administrados."
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 11/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 19b0b502d2c8c261947c461f27a0e8153df5b186
ms.openlocfilehash: 1e65c1fa25e273ba03218f79ebeff611138e8013


---

# <a name="device-logs"></a>Registros de dispositivo

Su trabajo de solución de problemas es posible que exija la recopilación de registros de dispositivos de usuario. Las instrucciones para recopilar esos registros se detallan aquí. Normalmente necesitará acceso al dispositivo o tendrá que solicitar al usuario que recopile los registros y se los envíe.

### <a name="android-logs"></a>Registros de Android
Los registros de Android se encuentran en *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. 

A veces, los archivos no aparecen, especialmente en dispositivos Android más recientes. Si ocurre esto, pida a los usuarios finales que abran la aplicación de portal de empresa para Android y que, a continuación, vayan a **Configuración**, elijan **Copiar registros** y, finalmente, reinicien el dispositivo. 

Para obtener más información acerca de cómo los usuarios pueden enviarle los registros de datos, consulte los artículos siguientes:

- [Usar el registro detallado para que el administrador de TI pueda solucionar los problemas del dispositivo](/intune/enduser/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android): describe cómo los usuarios activan el registro detallado, que le enviará todos sus registros de datos automáticamente. De forma predeterminada, el registro detallado está activado.

- [Enviar registros de datos de diagnóstico de Android al administrador de TI mediante correo electrónico](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android) 

- [Enviar registros de datos de diagnóstico al administrador de TI mediante un cable USB](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>Registros de iOS

Los usuarios puede enviar los errores de inscripción como se explica en [Enviar errores de inscripción de iOS al administrador de TI](/intune/enduser/send-errors-to-your-it-admin-ios).

### <a name="mac-os-x-logs"></a>Registros de Mac OS X

1. Abra la aplicación **Consola**.
2. En **ARCHIVOS**, seleccione **system.log**.
3. En la barra de menús de la parte superior, seleccione **Archivo** > **Guardar una copia como…** y guarde el archivo.

### <a name="windows-phone"></a>Windows Phone

En la aplicación de portal de empresa de Windows Phone, los usuarios deben seleccionar **...** para acceder al menú y luego seleccionar **Enviar registros**. Esta opción está disponible tanto antes como después de iniciar sesión en la aplicación de portal de empresa.

### <a name="windows"></a>Windows

En el portal de empresa para Windows, los registros se encuentran en *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Nov16_HO2-->


