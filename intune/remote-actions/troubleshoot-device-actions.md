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
ms.subservice: remote-actions
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 545f287e8b7ee82e2008f239171b22e01714b8c7
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514751"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Solución de problemas de acciones de dispositivo en Intune

Microsoft Intune tiene muchas acciones que ayudan a administrar dispositivos. En este artículo se proporcionan respuestas a algunas preguntas habituales que pueden ayudarle a solucionar problemas de acciones de dispositivo.

## <a name="disable-activation-lock-action"></a>Acción Deshabilitar el bloqueo de activación

### <a name="i-clicked-the-disable-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>He hecho clic en la acción "Deshabilitar el bloqueo de activación" en el portal, pero no ha sucedido nada en el dispositivo.
Esto es lo esperado. Después de iniciar la acción Deshabilitar el bloqueo de activación, Apple solicita un código actualizado a Intune. Una vez en la pantalla Bloqueo de activación, se escribe manualmente el código en el campo de código de acceso. Este código solo es válido durante 15 días, por lo que debe asegurarse de hacer clic en la acción y copiar el código antes del borrado.

### <a name="why-dont-i-see-the-disable-activation-lock-code-in-the-hardware-overview-blade-of-my-iosipados-device"></a>¿Por qué no veo el código Deshabilitar el bloqueo de activación en la hoja Información general del hardware del dispositivo iOS/iPadOS?
Los motivos más probables incluyen:
- El código ha expirado y se ha borrado del servicio.
- El dispositivo no está supervisado con la directiva de restricción de dispositivos para permitir el bloqueo de activación.

Puede comprobar el código en el Probador de Graph con la siguiente consulta:

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-disable-activation-lock-action-greyed-out-for-my-iosipados-device"></a>¿Por qué la acción Deshabilitar el bloqueo de activación está atenuada para el dispositivo iOS/iPadOS?
Los motivos más probables incluyen: 
- El código ha expirado y se ha borrado del servicio.
- El dispositivo no está supervisado con la directiva de restricción de dispositivos para permitir el bloqueo de activación.

### <a name="is-the-disable-activation-lock-code-case-sensitive"></a>¿El código Deshabilitar el bloqueo de activación distingue entre mayúsculas y minúsculas?
No. Además, no es necesario escribir los guiones.

## <a name="remove-devices-action"></a>Acción Quitar dispositivos

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>¿Cómo puedo saber quién ha iniciado Retirar/Eliminar datos?
En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), vaya a **Administración de inquilinos** > **Registros de auditoría** > compruebe la columna **Iniciado por**.
Si no ve ninguna entrada, lo más probable es que la persona que ha iniciado la acción sea el usuario del dispositivo. Probablemente ha usado la aplicación Portal de empresa o portal.manage.microsoft.com.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>¿Por qué no se ha desinstalado la aplicación después de usar Retirar?
Porque no se ha considerado una aplicación administrada. En este contexto, una aplicación administrada es aquella que se ha instalado mediante el servicio Intune. Esto incluye:
- La aplicación se ha implementado como Requerida.
- La aplicación se ha implementado como Disponible y, luego, la ha instalado el usuario final desde la aplicación Portal de empresa.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>¿Por qué Eliminar datos está atenuado en los dispositivos de perfil de trabajo de Android Enterprise?
Este comportamiento es normal. Google no permite el restablecimiento de fábrica de dispositivos de perfil de trabajo desde el proveedor de MDM.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>¿Por qué puedo volver a iniciar sesión en las aplicaciones de Office después de la retirada del dispositivo?
Porque la retirada de un dispositivo no revoca los tokens de acceso. Puede usar directivas de acceso condicional para mitigar este problema.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>¿Cómo se puede supervisar una acción Retirar/Eliminar datos después de su emisión?
En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), vaya a **Administración de inquilinos** > **Registros de auditoría**.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>¿Por qué a veces los borrados aparecen como pendientes indefinidamente?
Los dispositivos no siempre notifican su estado al servicio Intune antes del inicio del restablecimiento. Por lo tanto, la acción se muestra como pendiente. Si ha confirmado que la acción se ha realizado correctamente, elimine el dispositivo del servicio.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>¿Qué ocurre si se inicia una acción Retirar/Eliminar datos en un dispositivo sin conexión o en uno que no se ha comunicado con el servicio en un tiempo?
El dispositivo permanece en estado **Retirar/Eliminar datos Pendiente** hasta que expira el certificado de MDM. El certificado de MDM dura un año a partir de la inscripción y se renueva automáticamente cada año. Si el dispositivo se registra antes de que expire el certificado de MDM, se retira o se borra. Si el dispositivo no se registra antes de que expire el certificado de MDM, no se puede registrar en el servicio. El dispositivo se quita automáticamente de Azure Portal 180 días después de que expire el certificado de MDM.


## <a name="reset-passcode-action"></a>Acción Restablecer el código de acceso

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>¿Por qué la acción Restablecer el código de acceso está atenuada en el dispositivo inscrito por el administrador de dispositivos Android?
Para combatir el secuestro de datos (ransomware), Google ha quitado la característica de restablecimiento del código de acceso en la API de administración de dispositivos (se aplica a los dispositivos Android, versión 7.0 o posterior).

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>¿Por qué obtengo un mensaje "No compatible" cuando emito un restablecimiento del código de acceso al dispositivo inscrito en el perfil de trabajo Android 8.0 o posterior?
Porque el token de restablecimiento no se ha activado en el dispositivo. Para activar el token de restablecimiento:
1. Debe solicitar un código de acceso de perfil de trabajo en la directiva de configuración.
2. El usuario final debe establecer un código de acceso de perfil de trabajo adecuado.
3. El usuario final debe aceptar el mensaje secundario para permitir el restablecimiento del código de acceso.
Una vez completados estos pasos, ya no debería recibir esta respuesta.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-iosipados-device-when-i-issue-the-remove-passcode-action"></a>¿Por qué se me pide que establezca un nuevo código de acceso en el dispositivo iOS/iPadOS cuando ejecuto la acción Quitar código de acceso?
Porque una de las directivas de cumplimiento requiere un código de acceso.


## <a name="wipe-action"></a>Acción de borrado

### <a name="i-cant-restart-a-windows-10-device-after-using-the-wipe-action"></a>No puedo reiniciar un dispositivo Windows 10 después de usar la acción de borrado
Esto puede ocurrir si usa la opción **Borrar dispositivo y sigue borrando aunque los dispositivos pierdan potencia. Si selecciona esta opción, tenga en cuenta que esto puede impedir que algunos dispositivos Windows 10 vuelvan a iniciarse** en un dispositivo Windows 10.

Esto puede deberse a que la instalación de Windows presenta daños importantes que impiden que el sistema operativo se vuelva a instalar. En tal caso, el proceso genera un error y deja el sistema en el [Entorno de recuperación de Windows]( https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference).

### <a name="i-cant-restart-a-bitlocker-encrypted-device-after-using-the-wipe-action"></a>No puedo reiniciar un dispositivo cifrado con BitLocker después de usar la acción de borrado
Esto puede ocurrir si usa la opción **Borrar dispositivo y sigue borrando aunque los dispositivos pierdan potencia. Si selecciona esta opción, tenga en cuenta que esto puede impedir que algunos dispositivos Windows 10 vuelvan a iniciarse** en un dispositivo cifrado con BitLocker.

Para resolver este problema, use medios de arranque para volver a instalar Windows 10 en el dispositivo.


## <a name="next-steps"></a>Pasos siguientes

Obtenga [ayuda de soporte técnico de Microsoft](../fundamentals/get-support.md) o use los [foros de la comunidad](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
