---
title: Recopilar registros de dispositivo| Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: angrobe
ms.date: 06/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9915b275101e287498217c4f35e1c0e56d2425c2
ms.openlocfilehash: 46579569c33b50f4b19a62d83c1db5e0e304621b


---

# Registros de dispositivo

Su trabajo de solución de problemas es posible que exija la recopilación de registros de dispositivos de usuario. Las instrucciones para recopilar esos registros se detallan aquí. Normalmente necesitará acceso al dispositivo o tendrá que solicitar al usuario que recopile los registros y se los envíe.

### Ubicación del registro de Android
Los registros de Android se encuentran en *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. El usuario también puede enviar archivos de registro por correo electrónico, como se explica en [Send Android diagnostic data logs to your IT administrator using email (Enviar registros de datos de diagnóstico de Android al administrador de TI por correo electrónico)](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android).

### Registros de iOS

El usuario puede enviar los errores de inscripción como se explica en [Send iOS enrollment errors to your IT administrator (Enviar errores de inscripción de iOS al administrador de TI)](/intune/enduser/send-errors-to-your-it-admin-ios)

### Dispositivos Mac OS X

1. Abra la aplicación **Consola**.
2. En **ARCHIVOS**, seleccione **system.log**.
3. En la barra de menús de la parte superior, seleccione **Archivo** > **Guardar una copia como…** y guarde el archivo.

### Windows Phone

En el **portal de empresa para Windows Phone**, el usuario tendrá que seleccionar **…** para acceder al menú y luego seleccionar **Enviar registros**. Esta opción está disponible tanto antes como después de iniciar sesión en el portal.

### Windows

En el portal de empresa para Windows, los registros se encuentran en *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Jul16_HO4-->


