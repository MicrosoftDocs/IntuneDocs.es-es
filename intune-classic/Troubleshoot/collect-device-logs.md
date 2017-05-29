---
title: Recopilar registros de dispositivo| Microsoft Docs
description: "Obtenga información sobre cómo recopilar registros desde sus dispositivos administrados."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: f75719a02e37f6285fb1d7c5de32bb7eb4b3a1ed
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="device-logs"></a>Registros de dispositivo

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Su trabajo de solución de problemas es posible que exija la recopilación de registros de dispositivos de usuario. Las instrucciones para recopilar esos registros se detallan aquí. Normalmente necesitará acceso al dispositivo para obtener estos registros o solicitar al usuario que recopile los registros y se los envíe.

### <a name="android-logs"></a>Registros de Android
Los registros de Android se encuentran en *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*.

A veces, los archivos no aparecen, especialmente en dispositivos Android más recientes. Si esto ocurre, pida a los usuarios que abran la aplicación de Portal de empresa para Android. A continuación, deben elegir **Configuración**>**Copiar registros** y reiniciar el dispositivo.

Para obtener más información acerca de cómo los usuarios pueden enviarle los registros de datos, consulte los artículos siguientes:

- [Usar el registro detallado para que el administrador de TI pueda solucionar los problemas del dispositivo](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android): describe cómo los usuarios activan el registro detallado, que le enviará todos sus registros de datos automáticamente. De forma predeterminada, el registro detallado está activado.

- [Enviar registros de datos de diagnóstico de Android al administrador de TI mediante correo electrónico](/intune-user-help/send-logs-to-your-it-admin-by-email-android)

- [Enviar registros de datos de diagnóstico al administrador de TI mediante un cable USB](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>Registros de iOS

Los usuarios puede enviar los errores de inscripción como se explica en [Enviar errores de inscripción de iOS al administrador de TI](/intune-user-help/send-errors-to-your-it-admin-ios).

Los usuarios pueden enviar registros de dispositivo, tal como se describe en [Envío de registros de dispositivo de iOS](/intune-user-help/send-logs-to-your-it-admin-by-email-ios).

### <a name="mac-os-x-logs"></a>Registros de Mac OS X

1. Abra la aplicación **Consola**.
2. En **ARCHIVOS**, seleccione **system.log**.
3. En la barra de menús de la parte superior, seleccione **Archivo** > **Guardar una copia como…** A continuación, guarde el archivo.

### <a name="windows-phone"></a>Windows Phone

En la aplicación de Portal de empresa de Windows Phone, los usuarios eligen los tres puntos (**...**) para obtener acceso al menú y, a continuación, elegir **Enviar registros**. Esta opción está disponible tanto antes como después de iniciar sesión en la aplicación de portal de empresa.

### <a name="windows"></a>Windows

En el portal de empresa para Windows, los registros se encuentran en *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.

