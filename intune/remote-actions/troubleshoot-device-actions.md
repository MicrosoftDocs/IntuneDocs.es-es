---
title: Solución de problemas de acciones de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Obtenga ayuda para solucionar problemas de acciones de dispositivo.
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1b3139db8b217dceb495f67e809eae8319eae0c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735706"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Solucionar problemas de acciones de dispositivo en Intune

Microsoft Intune tiene muchas acciones que le ayudan a administrar los dispositivos. En este artículo se proporcionan respuestas a algunas preguntas comunes que pueden ayudarle a solucionar problemas de acciones de dispositivo.

## <a name="bypass-activation-lock-action"></a>Acción Omitir bloqueo de activación

### <a name="i-clicked-the-bypass-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>Hago clic en la acción "omitir Bloqueo de activación" en el portal, pero no ocurrió nada en el dispositivo.
Esto es normal. Después de iniciar la acción de omitir Bloqueo de activación, Intune solicita un código actualizado de Apple. Escribirá manualmente el código en el campo de código de acceso después de que el dispositivo esté en la pantalla de Bloqueo de activación. Este código solo es válido durante 15 días, por lo que debe asegurarse de hacer clic en la acción y copiar el código antes de emitir el borrado.

### <a name="why-dont-i-see-the-bypass-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>¿Por qué no veo el código de bypass Bloqueo de activación en la hoja de información general de hardware de mi dispositivo iOS?
Los motivos más probables son:
- El código ha expirado y se ha borrado del servicio.
- El dispositivo no está supervisado con la Directiva de restricción de dispositivos para permitir el Bloqueo de activación.

Puede comprobar el código en el explorador de gráficos con la siguiente consulta:

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-bypass-activation-lock-action-greyed-out-for-my-ios-device"></a>¿Por qué el bypass Bloqueo de activación acción está atenuado para el dispositivo iOS?
Los motivos más probables son: 
- El código ha expirado y se ha borrado del servicio.
- El dispositivo no está supervisado con la Directiva de restricción de dispositivos para permitir el Bloqueo de activación.

### <a name="is-the-bypass-activation-lock-code-case-sensitive"></a>¿La omisión Bloqueo de activación distingue mayúsculas de minúsculas de código?
No. Y no es necesario escribir los guiones.

## <a name="remove-devices-action"></a>Acción quitar dispositivos

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>Cómo ¿qué inició una retirada/borrado?
Vaya a **Intune** > **dispositivos** > **acciones de dispositivo** > Compruebe la columna **Iniciado por** .
Si no ve ninguna entrada, lo más probable es que la persona que ha iniciado la acción sea el usuario del dispositivo. Probablemente usaban la aplicación Portal de empresa o portal.manage.microsoft.com.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>¿Por qué no se desinstaló la aplicación después de usar retirar?
Porque no se consideró una aplicación administrada. En este contexto, una aplicación administrada es una aplicación que se instaló mediante el servicio de Intune. Esto incluye:
- La aplicación se implementó según sea necesario
- La aplicación se ha implementado como disponible y, a continuación, la instala el usuario final desde la aplicación Portal de empresa.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>¿Por qué se atenúa el borrado de los dispositivos de Perfil de trabajo de Android Enterprise?
Este comportamiento es normal. Google no permite el restablecimiento de fábrica de los dispositivos de Perfil de trabajo del proveedor de MDM.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>¿Por qué puedo volver a iniciar sesión en mis aplicaciones de Office después de retirar el dispositivo?
Dado que la retirada de un dispositivo no revoca los tokens de acceso. Puede usar las directivas de acceso condicional para mitigar esta situación.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>¿Cómo se puede supervisar una acción de retirada/borrado después de su emisión?
Vaya a **Intune** > **dispositivos** > **acciones de dispositivo**.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>¿Por qué algunas veces los borradores aparecen como pendientes indefinidamente?
Los dispositivos no siempre notifican su estado al servicio de Intune antes de que se iniciara el restablecimiento. Por lo tanto, la acción se muestra como pendiente. Si ha confirmado que la acción se ha realizado correctamente, elimine el dispositivo del servicio.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>¿Qué ocurre si se inicia una retirada/eliminación en un dispositivo sin conexión o en un dispositivo que no se ha comunicado con el servicio en un tiempo?
El dispositivo permanecerá en estado **pendiente de retirada y borrado** hasta que expire el certificado MDM. El certificado MDM se mantiene durante un año a partir de la inscripción y se renueva automáticamente cada año. Si el dispositivo se registra antes de que expire el certificado MDM, se retirará o borrará. Si el dispositivo no se protege antes de que expire el certificado MDM, no podrá insertar en el repositorio el servicio. 180 días después de que expire el certificado MDM, el dispositivo se quitará automáticamente del Azure Portal.


## <a name="reset-passcode-action"></a>Acción restablecer código de acceso

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>¿Por qué la acción restablecer código de acceso está atenuada en el dispositivo inscrito por el administrador de dispositivos Android?
Para combatir Ransom Ware, Google quitó la característica de restablecimiento de código de acceso en la API de administración de dispositivos (se aplica a los dispositivos Android versión 7,0 o superior).

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>¿Por qué obtengo un mensaje "no admitido" cuando ejecuto un restablecimiento de código de acceso al dispositivo inscrito en el perfil de trabajo de Android 8,0 o posterior?
Porque el token de restablecimiento no se ha activado en el dispositivo. Para activar el token de restablecimiento:
1. Debe solicitar un código de acceso de Perfil de trabajo en la Directiva de configuración.
2. El usuario final debe establecer un código de acceso de Perfil de trabajo adecuado.
3. El usuario final debe aceptar el mensaje secundario para permitir el restablecimiento del código de acceso.
Una vez completados estos pasos, ya no debe recibir esta respuesta.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>¿Por qué se me pide que establezca un nuevo código de acceso en el dispositivo iOS cuando se emite la acción quitar código de acceso?
Debido a que una de las directivas de cumplimiento requiere un código de acceso.

## <a name="next-steps"></a>Pasos siguientes

Obtenga [ayuda de soporte técnico de Microsoft](../fundamentals/get-support.md) o use los [foros de la comunidad](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
