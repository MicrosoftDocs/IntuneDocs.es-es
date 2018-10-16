---
title: Solucionar problemas de instalación de aplicaciones
titlesuffix: Microsoft Intune
description: Use el panel de solución de problemas de Microsoft Intune, el cual le ayuda a solucionar problemas de instalación de aplicaciones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
ms.custom: intune-azure
ms.openlocfilehash: 6e25149199c9362f628fa108d20247bb6b86d895
ms.sourcegitcommit: f69f2663ebdd9c1def68423e8eadf30f86575f7e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2018
ms.locfileid: "49075836"
---
# <a name="troubleshoot-app-installation-issues"></a>Solucionar problemas de instalación de aplicaciones

En algunas ocasiones, las instalaciones de aplicaciones en los dispositivos administrados por MDM de Microsoft Intune pueden presentar errores. Cuando esto ocurre, puede ser complicado entender el motivo del error o cómo solucionarlo. Microsoft Intune proporciona detalles del error de instalación de aplicaciones que permiten a los operadores del departamento de soporte técnico y a los administradores de Intune ver información de la aplicación para atender las solicitudes de ayuda al usuario. En el panel de solución de problemas de Intune se proporcionan detalles del error, incluidos aquellos sobre las aplicaciones administradas en el dispositivo de un usuario. Se proporcionan detalles sobre el ciclo de vida de un extremo a otro en cada dispositivo individual del panel **Aplicaciones administradas**. Puede ver problemas de instalación, por ejemplo, al crearse, modificarse, dirigirse y entregarse la aplicación a un dispositivo. 

## <a name="to-review-app-troubleshooting-details"></a>Para ver los detalles de solución de problemas de la aplicación, siga estos pasos:

Intune proporciona los detalles de solución de problemas de la aplicación en función de las aplicaciones instaladas en el dispositivo de un usuario específico.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Solucionar problema**.
4. Haga clic en **Seleccionar usuario** para seleccionar un usuario para solucionar problemas. Se mostrará el panel **Seleccionar usuarios**.
5. Seleccione un usuario escribiendo su nombre o dirección de correo electrónico. Haga clic en **Seleccionar** en la parte inferior del panel. La información de solución de problemas del usuario se muestra en el panel de **solución de problemas**. 
6. Seleccione el dispositivo del que desea solucionar problemas en la lista **Dispositivos**.
    ![El panel de solución de problemas de Intune.](media/troubleshoot-app-install-01.png)
7. Seleccione **Aplicaciones administradas** en el panel de dispositivo seleccionado. Se muestra una lista de aplicaciones administradas.
    ![Detalles de un dispositivo específico administrado por Intune.](media/troubleshoot-app-install-02.png)
8. Seleccione una aplicación en la lista donde **Estado de la instalación** indica un error.
    ![Una aplicación seleccionada que muestra detalles del error de instalación.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > La misma aplicación podría asignarse a varios grupos, pero con diferentes acciones previstas (intenciones) para la aplicación. Por ejemplo, una intención resuelta para una aplicación se mostrará como **excluida** si la aplicación se excluye para un usuario durante la asignación de aplicaciones. Para obtener más información, consulte [Cómo se resuelven los conflictos entre las intenciones de aplicación](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Si se produce un error de instalación para una aplicación requerida, usted o su departamento de soporte técnico podrán sincronizar el dispositivo y volver a intentar instalar la aplicación.

Los detalles del error de instalación de la aplicación indicarán el problema. Puede usar estos detalles para determinar cuál es la mejor acción para resolver el problema. Para obtener más información sobre la solución de problemas de instalación de la aplicación, consulte [Error Codes For Troubleshooting App Installation Issues](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues) (Códigos de error para la solución de problemas de instalación de la aplicación).

> [!Note]  
> También puede acceder al panel de **solución de problemas** visitando la página [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) desde el explorador.

## <a name="app-installation-errors"></a>Errores de instalación de la aplicación

Los siguientes mensajes de error y descripciones proporcionan detalles sobre errores de instalación de iOS y Android. 

### <a name="android-errors"></a>Errores de Android

|    Mensaje o código de error    |    Descripción    |
|----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    No se pudo instalar la aplicación. (0xC7D14FB5)    |    Este mensaje de error se muestra cuando Intune no puede determinar la causa del error de instalación de la aplicación de Android. Durante el error Android no proporciona ninguna información.       Este error se devuelve cuando la descarga de APK se realizó correctamente, pero no se pudo instalar la aplicación. Este error se puede producir con más frecuencia debido a un archivo APK incorrecto que no se puede instalar en el dispositivo. Una posible causa puede ser cuando Google Play Protect bloquea la instalación de la aplicación por motivos de seguridad. Otra causa posible de este error es cuando un dispositivo no es compatible con la aplicación. Por ejemplo, si la aplicación requiere la versión 21+ de la API y el dispositivo actualmente tiene la versión 19.         Intune devuelve este error para los dispositivos DA y KNOX, y aunque puede haber una notificación de que los usuarios pueden hacer clic para volverlo a intentar, si hay un problema con el APK, nunca seguirá generando un error. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.        |
|    La instalación de la aplicación se canceló porque el archivo de instalación (APK) se eliminó después de la descarga, pero antes de la instalación. (0xC7D14FBA)    |    La descarga del archivo APK se realizó correctamente pero, antes de que el usuario instalara la aplicación, el archivo se quitó del dispositivo. Esto podría ocurrir si se ha producido una diferencia de tiempo considerable entre la descarga y la instalación. Por ejemplo, el usuario canceló la instalación original, esperó y, después, hizo clic en la notificación para intentarlo de nuevo.         Este mensaje de error solo se devuelve para escenarios de DA. Los escenarios de KNOX se pueden realizar en modo silencioso. Se presenta una notificación de reintento para que el usuario pueda aceptar en lugar de cancelar. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.    |
|    La instalación de la aplicación se canceló porque el proceso se reinició durante la instalación. (0xC7D14FBB)    |    El dispositivo se reinició durante el proceso de instalación de APK, lo que resultó en una instalación cancelada.        Este mensaje de error se devuelve para los dispositivos DA y KNOX. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.    |
|    La aplicación no se encontró después de que la instalación se completara correctamente. (0x87D1041C)    |    El usuario desinstaló la aplicación de forma explícita. Este error no se devuelve desde el cliente. Es un error que se produce cuando la aplicación estaba instalada en algún momento pero que después el usuario desinstaló. Este error solo debería producirse para las aplicaciones necesarias. Los usuarios pueden desinstalar las aplicaciones que no son requeridas. Este error solo puede ocurrir en DA. KNOX bloquea la desinstalación de las aplicaciones administradas.       En la sincronización siguiente se volverá a publicar la notificación en el dispositivo para que el usuario lo instale.   El usuario puede ignorar la notificación. Este error se seguirá notificando hasta que el usuario instale la aplicación.    |
|    Error desconocido en la descarga. (0xC7D14FB2)    |    Este error aparece cuando se produce un error en la descarga. Normalmente, este error puede producirse debido a problemas de Wi-Fi o conexiones lentas.       Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.    |
|    Error desconocido en la descarga. La directiva se reintentará la próxima vez que el dispositivo se sincronice. (0xC7D15078)    |    Este error aparece cuando se produce un error en la descarga. Normalmente, este error puede producirse debido a problemas de Wi-Fi o conexiones lentas.       Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa.    |
|    El usuario final canceló la instalación de la aplicación. (0xC7D14FB1)    |    El usuario desinstaló la aplicación de forma explícita. Este error se devuelve cuando la actividad de instalación del sistema operativo Android es cancelada por el usuario. El usuario presionó el botón de cancelación cuando se presentó el mensaje de instalación del sistema operativo, o bien hizo clic fuera del mensaje.        Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.    |
|    El proceso de descarga de archivo se detuvo de manera inesperada. (0xC7D15015)    |    El sistema operativo detuvo el proceso de descarga antes de que se completara. Este error se puede producir cuando el dispositivo tiene poca batería o la descarga está tardando demasiado.       Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.    |
|    El servicio de descarga de archivo se detuvo de manera inesperada. La directiva se reintentará la próxima vez que el dispositivo se sincronice. (0xC7D1507C)    |    El sistema operativo detuvo el proceso de descarga antes de que se completara. Este error se puede producir cuando el dispositivo tiene poca batería o la descarga está tardando demasiado.       Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa.    |

### <a name="ios-errors"></a>Errores de iOS

|    Mensaje o código de error    |    Descripción    |
|:----------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    (0x87D12906)    |    El agente MDM de Apple ha devuelto que no se puede ejecutar el comando de instalación.        |
|    (0x87D1313C)    |    Se perdió la conexión de red mientras se enviaba la dirección URL del servicio de descarga actualizada al dispositivo. En concreto, no se encontró un servidor con el nombre de host especificado.    |
|    El dispositivo iOS está ocupado actualmente. (0x87D11388)    |    El dispositivo iOS estaba ocupado, lo que provocó un error.    |
|    Error al instalar la aplicación. (0x87D13B64)    |    Se ha producido un error de instalación de la aplicación. Para solucionar este error se necesitan los registros de XCODE.    |
|    La aplicación está administrada, pero ha expirado o el usuario la ha quitado. (0x87D13B66)    |    El usuario desinstaló la aplicación de forma explícita. O bien, la aplicación ha expirado, pero no se pudo descargar o la detección de la aplicación no coincide con la respuesta del dispositivo.   Además, este error se puede producir debido a un error en la plataforma iOS 9.2.2.    |
|    La aplicación está programada para la instalación, pero necesita un código de canje para completar la transacción.   (0x87D13B60)    |    Este error se suele producir con las aplicaciones de la tienda iOS que son de pago.     |
|    La aplicación no se encontró después de que la instalación se completara correctamente. (0x87D1041C)    |    El proceso de detección de la aplicación no coincide con la respuesta del dispositivo.    |
|    El usuario rechazó la oferta para instalar la aplicación. (0x87D13B62)    |    Durante la instalación de la aplicación inicial, el usuario hizo clic en Cancelar.    |
|    El usuario rechazó la oferta para actualizar la aplicación. (0x87D13B63)    |    El usuario final hizo clic en Cancelar durante el proceso de actualización.     |
|    Error desconocido   (0x87D103E8)    |    Se ha producido un error desconocido durante la instalación de la aplicación. Este es el error resultante cuando no se han producido los otros.    |


## <a name="next-steps"></a>Pasos siguientes

- Para obtener información adicional sobre la solución de problemas de Intune, consulte [Uso del portal de solución de problemas para ayudar a los usuarios de su empresa](help-desk-operators.md). 
- Obtenga información sobre los problemas conocidos de Microsoft Intune. Para obtener más información, consulte [Problemas conocidos de Microsoft Intune](known-issues.md).
- ¿Necesita más ayuda? Consulte [Cómo obtener asistencia para Microsoft Intune](get-support.md).
