---
# required metadata

title: Ayudar a que los usuarios finales comprendan los mensajes de la aplicación Portal de empresa | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Ayudar a que los usuarios finales comprendan los mensajes de la aplicación Portal de empresa

La siguiente información se aplica solo a dispositivos Android 6.0 y versiones posteriores. Durante el proceso de inscripción de los dispositivos, los usuarios finales ven dos mensajes:

- ¿Permitir que Portal de empresa realice y administre llamadas telefónicas?
- ¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?

Siga leyendo para obtener más información sobre estos mensajes y ver la información que puede compartir con los usuarios finales.

## ¿Permitir que Portal de empresa realice y administre llamadas telefónicas?

### Texto del mensaje y dónde aparece
El texto del mensaje es **¿Permitir que Portal de empresa realice y administre llamadas telefónicas?** y aparece cuando los usuarios inician sesión en la aplicación Portal de empresa por primera vez para inscribir el dispositivo.

### Significado del mensaje
El mensaje solicita permiso a los usuarios para que el número de teléfono y el IMEI del dispositivo del usuario se envíen al servicio Intune y que aparezcan en la consola de administración de la página de hardware.

> [!NOTE]
> **La aplicación Portal de empresa nunca hace ni administra llamadas telefónicas.** Google controla el texto del mensaje y no se puede cambiar.

Para ver la página **Hardware**, vaya a **Grupos** > **Todos los dispositivos móviles** > **Dispositivos**. Seleccione el dispositivo del usuario y vaya a **Ver propiedades** > **Hardware**..

### Qué sucede si los usuarios permiten o deniegan el acceso
Si los usuarios permiten el acceso, el número de teléfono y el IMEI del dispositivo aparecerán en la página de hardware de la consola de administración.

Si los usuarios deniegan el acceso, podrán seguir usando la aplicación Portal de empresa e inscribir sus dispositivos, pero el número de teléfono y el IMEI de los dispositivos de los usuarios aparecerán en blanco en la página de hardware de la consola de administración. La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla **No volver a preguntar** que los usuarios pueden seleccionar para que el mensaje no se vuelva a mostrar.

Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparece la próxima vez que los usuarios inicien sesión en la aplicación Portal de empresa después de la inscripción.</br></br>Si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración** > **Aplicaciones** > **Portal de empresa** > **Permisos** > **Teléfono** y activar el permiso.

### Dónde pueden obtener más información los usuarios
[Iniciar sesión en la aplicación Portal de empresa](/Intune/EndUser/sign-in-to-the-company-portal-app-android)

## ¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?

### Texto del mensaje y dónde aparece
El texto del mensaje es **¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?**, y aparece cuando los usuarios pulsan **Enviar datos** para enviar registros de datos a su administrador de TI.

### Significado del mensaje
El mensaje solicita permiso a los usuarios para que su dispositivo escriba datos de registros en la tarjeta SD del dispositivo y para permitir que esos registros se muevan mediante un cable USB.   

> [!NOTE]
> **La aplicación Portal de empresa nunca tiene acceso a las fotos, elementos multimedia ni archivos de los usuarios.** Google controla el texto del mensaje y no se puede cambiar.

### Qué sucede si los usuarios permiten o deniegan el acceso
Si el usuario permite el acceso, los registros se copiarán en la tarjeta SD.

Si los usuarios deniegan el acceso, podrán enviar registros de datos, pero los registros no se copiarán en la tarjeta SD del dispositivo.

La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla **No volver a preguntar** que los usuarios pueden seleccionar para que el mensaje no se vuelva a mostrar. Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparece la próxima vez que los usuarios intenten enviar registros. Si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración**  >  **Aplicaciones**  >  **Portal de empresa**  >  **Permisos**  >  **Almacenamiento** y activar el permiso.

### Dónde pueden obtener más información los usuarios
[Enviar registros de datos de diagnóstico al administrador de TI mediante correo electrónico](/Intune/EndUser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)


### Consulte también
[Qué decirles a los usuarios finales sobre el uso de Intune](/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune.md)


<!--HONumber=May16_HO1-->


