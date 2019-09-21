---
title: Solucionar problemas de instalación de aplicaciones
titleSuffix: Microsoft Intune
description: Use el panel de solución de problemas de Microsoft Intune, el cual le ayuda a solucionar problemas de instalación de aplicaciones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/04/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 850c7a28c4df1638e9f635713695dcf2e914ffce
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166936"
---
# <a name="troubleshoot-app-installation-issues"></a>Solucionar problemas de instalación de aplicaciones

En algunas ocasiones, las instalaciones de aplicaciones en los dispositivos administrados por MDM de Microsoft Intune pueden presentar errores. Cuando esto ocurre, puede ser complicado entender el motivo del error o cómo solucionarlo. Microsoft Intune proporciona detalles del error de instalación de aplicaciones que permiten a los operadores del departamento de soporte técnico y a los administradores de Intune ver información de la aplicación para atender las solicitudes de ayuda al usuario. En el panel de solución de problemas de Intune se proporcionan detalles del error, incluidos aquellos sobre las aplicaciones administradas en el dispositivo de un usuario. Se proporcionan detalles sobre el ciclo de vida de un extremo a otro en cada dispositivo individual del panel **Aplicaciones administradas**. Puede ver problemas de instalación, por ejemplo, al crearse, modificarse, dirigirse y entregarse la aplicación a un dispositivo. 

## <a name="app-troubleshooting-details"></a>Detalles de solución de problemas de aplicaciones

Intune proporciona los detalles de solución de problemas de la aplicación en función de las aplicaciones instaladas en el dispositivo de un usuario específico.

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
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

Los detalles del error de instalación de la aplicación indicarán el problema. Puede usar estos detalles para determinar cuál es la mejor acción para resolver el problema. Para obtener más información sobre la solución de problemas de instalación de aplicaciones, vea [Errores de instalación de la aplicación](troubleshoot-app-install.md#app-installation-errors).

> [!Note]  
> También puede acceder al panel de **solución de problemas** visitando la página [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) desde el explorador.

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>La instalación de la aplicación de destino del grupo de usuarios no alcanza el dispositivo
Se deben tener en cuenta las siguientes acciones cuando tenga problemas al instalar aplicaciones:
- Si la aplicación no se muestra en el Portal de empresa, asegúrese de que la aplicación se implementa con la intención **disponible** y de que el usuario accede a la portal de empresa con el tipo de dispositivo admitido por la aplicación.
- En el caso de los dispositivos BYOD de Windows, el usuario debe agregar una cuenta profesional al dispositivo.
- Compruebe si el usuario está por encima del límite de dispositivos de AAD:
  1. Vaya a [Azure Active Directory configuración del dispositivo](https://portal.azure.com/#blade/Microsoft_AAD_IAM/DevicesMenuBlade/DeviceSettings/menuId).
  2. Tome nota del valor establecido para el **número máximo de dispositivos por usuario**.
  3. Vaya a [Azure Active Directory usuarios](https://portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/AllUsers).
  4. Seleccione el usuario afectado y haga clic en **dispositivos**.
  5. Si el usuario supera el límite establecido, elimine los registros obsoletos que ya no sean necesarios.
- En el caso de dispositivos DEP de iOS, asegúrese de que el usuario aparece como **inscrito por el usuario** en la hoja de información general del dispositivo de Intune. Si muestra NA, implemente una directiva de configuración para el Portal de empresa de Intune. Para obtener más información, consulte [configuración de la aplicación portal de empresa](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Solución de problemas de instalación de aplicaciones Win32

Seleccione la aplicación Win32 que se implementó mediante la extensión de administración de Intune. Puede seleccionar la opción **Recopilar registros** cuando se produce un error de instalación de la aplicación Win32. 

> [!IMPORTANT]
> La opción **Recopilar registros** no se habilitará cuando la aplicación Win32 se haya instalado correctamente en el dispositivo.<p>Para poder recopilar información de registro de la aplicación Win32, debe instalarse la extensión de administración de Intune en el cliente de Windows. La extensión de administración de Intune se instala cuando se implementa un script de PowerShell o una aplicación Win32 en un grupo de seguridad de dispositivos o usuarios. Para más información, vea [Requisitos previos de la extensión de administración de Intune](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Recopilar archivos de registro

Para recopilar los registros de instalación de la aplicación Win32, primero siga los pasos indicados en la sección [Detalles de solución de problemas de la aplicación](troubleshoot-app-install.md#app-troubleshooting-details). Después, siga con estos pasos:

1. Haga clic en la opción **Recopilar registros** en la hoja **Detalles de la instalación**.

    <image alt="Win32 app installation details - Collect log option" src="media/troubleshoot-app-install-04.png" width="500" />

2. Proporcione rutas de acceso de archivo con nombres de archivo de registro para iniciar el proceso de recopilación de archivos de registro y haga clic en **Aceptar**.
    
    > [!NOTE]
    > La recopilación de registros tardará menos de dos horas. Tipos de archivo admitidos: *.log, .txt, .dmp, .cab, .zip, .xml, .evtx y .evtl*. Se permite un máximo de 25 rutas de acceso de archivo.

3. Una vez que se han recopilado los archivos de registro, puede seleccionar el vínculo **Registros** para descargarlos.

    <image alt="Win32 app log details - Download logs" src="media/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Se mostrará una notificación que indica que la recopilación de registros de la aplicación se ha realizado correctamente.

#### <a name="win32-log-collection-requirements"></a>Requisitos de recopilación de registros de Win32

Para recopilar archivos de registro, es necesario seguir unos requisitos específicos:

- Debe especificar la ruta completa del archivo de registro. 
- Puede especificar variables de entorno para la recopilación de registros, como las siguientes:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Solo se permiten extensiones de archivo exactas, como:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- Se puede cargar un máximo de 25 archivos de registro o de 60 MB, lo que ocurra primero. 
- La recopilación de registros de instalación de la aplicación Win32 está habilitada para las aplicaciones que cumplen la intención de asignación de aplicación necesaria, disponible y de instalación.
- Los registros almacenados se cifran para proteger cualquier información de identificación personal incluida en los registros.
- Si se produce un error al abrir incidencias de soporte técnico para aplicaciones Win32, adjunte los registros de error relacionados siguiendo los pasos arriba indicados.

## <a name="app-installation-errors"></a>Errores de instalación de la aplicación

Los siguientes mensajes de error y descripciones proporcionan detalles sobre errores de instalación de iOS y Android. 

### <a name="android-errors"></a>Errores de Android

En esta sección se menciona la inscripción de administrador de dispositivos (DA) y Samsung Knox. Para obtener más información, consulte [inscripción de administrador de dispositivos Android](android-enroll-device-administrator.md) e inscripción [automática de dispositivos Android mediante la inscripción de Knox Mobile de Samsung](android-samsung-knox-mobile-enroll.md). 

| Mensaje o código de error | Descripción |
|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| No se pudo instalar la aplicación. (0xC7D14FB5) | Este mensaje de error se muestra cuando Intune no puede determinar la causa del error de instalación de la aplicación de Android. Durante el error Android no proporciona ninguna información. Este error se devuelve cuando la descarga de APK se realizó correctamente, pero no se pudo instalar la aplicación. Este error se puede producir con más frecuencia debido a un archivo APK incorrecto que no se puede instalar en el dispositivo. Una posible causa puede ser cuando Google Play Protect bloquea la instalación de la aplicación por motivos de seguridad. Otra causa posible de este error es cuando un dispositivo no es compatible con la aplicación. Por ejemplo, si la aplicación requiere la versión 21+ de la API y el dispositivo actualmente tiene la versión 19. Intune devuelve este error para los dispositivos DA y KNOX y, aunque puede haber una notificación de que los usuarios pueden hacer clic para volverlo a intentar, si hay un problema con el APK, nunca seguirá generando un error. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. |
| La instalación de la aplicación se ha cancelado porque el archivo de instalación (APK) se ha eliminado después de la descarga, pero antes de la instalación. (0xC7D14FBA) | La descarga del archivo APK se realizó correctamente pero, antes de que el usuario instalara la aplicación, el archivo se quitó del dispositivo. Esto podría ocurrir si se ha producido una diferencia de tiempo considerable entre la descarga y la instalación. Por ejemplo, el usuario canceló la instalación original, esperó y, después, hizo clic en la notificación para intentarlo de nuevo. Este mensaje de error solo se devuelve para escenarios de DA. Los escenarios de KNOX se pueden realizar en modo silencioso. Se presenta una notificación de reintento para que el usuario pueda aceptar en lugar de cancelar. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. |
| La instalación de la aplicación se ha cancelado porque el proceso se ha reiniciado durante la instalación. (0xC7D14FBB) | El dispositivo se ha reiniciado durante el proceso de instalación de APK, lo que resultó en una instalación cancelada. Este mensaje de error se devuelve para los dispositivos DA y KNOX. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. |
| La aplicación no se encontró después de que la instalación se completara correctamente. (0x87D1041C) | El usuario ha desinstalado la aplicación de forma explícita. Este error no se devuelve desde el cliente. Es un error que se produce cuando la aplicación estaba instalada en algún momento pero que después el usuario desinstaló. Este error solo debería producirse para las aplicaciones necesarias. Los usuarios pueden desinstalar las aplicaciones que no son requeridas. Este error solo puede ocurrir en DA. KNOX bloquea la desinstalación de las aplicaciones administradas. En la sincronización siguiente se volverá a publicar la notificación en el dispositivo para que el usuario lo instale. El usuario puede ignorar la notificación. Este error se seguirá notificando hasta que el usuario instale la aplicación. |
| Error desconocido en la descarga. (0xC7D14FB2) | Este error aparece cuando no se produce la descarga. Normalmente, este error puede producirse debido a problemas de Wi-Fi o conexiones lentas. Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. |
| Error desconocido en la descarga. La directiva se reintentará la próxima vez que el dispositivo se sincronice. (0xC7D15078) | Este error aparece cuando no se produce la descarga. Normalmente, este error puede producirse debido a problemas de Wi-Fi o conexiones lentas. Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. |
| El usuario final canceló la instalación de la aplicación. (0xC7D14FB1) | El usuario ha desinstalado la aplicación de forma explícita. Este error se devuelve cuando la actividad de instalación del sistema operativo Android ha sido cancelada por el usuario. El usuario presionó el botón de cancelación cuando se presentó el mensaje de instalación del sistema operativo, o bien hizo clic fuera del mensaje. Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. Pida al usuario que cancele la instalación. |
| El proceso de descarga de archivo se detuvo de manera inesperada. (0xC7D15015) | El sistema operativo detuvo el proceso de descarga antes de que se completara. Este error se puede producir cuando el dispositivo tiene poca batería o la descarga está tardando demasiado. Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar. Asegúrese de que el dispositivo tiene una conexión de red confiable.  |
| El servicio de descarga de archivo se detuvo de manera inesperada. La directiva se reintentará la próxima vez que el dispositivo se sincronice. (0xC7D1507C) | El sistema operativo finalizó el proceso de descarga antes de que se completara. Este error se puede producir cuando el dispositivo tiene poca batería o la descarga está tardando demasiado. Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Sincronice manualmente el dispositivo o espere 24 horas y compruebe el estado. |
| No se pudo desinstalar la aplicación. (0xc7d14fb8) | Este error es un error genérico de desinstalación. El sistema operativo no especificó el motivo por el que no se pudo desinstalar la aplicación. Algunas aplicaciones de administración no se pueden desinstalar simplemente. Compruebe que la aplicación se puede desinstalar manualmente y recopile los registros de Portal de empresa si se produce un error en la desinstalación. |
| El archivo APK de instalación de la aplicación que se usa para la actualización no coincide con la firma de la aplicación actual en el dispositivo. (0xc7d14fb7) | El sistema operativo Android tiene la limitación de requerir que el certificado de firma para la versión de actualización sea exactamente el mismo que el certificado usado para firmar la versión existente. Si el desarrollador no puede usar el mismo certificado para firmar la nueva versión, tendrá que desinstalar la aplicación existente y volver a implementar la nueva aplicación en lugar de actualizar la aplicación existente. |
| El usuario final canceló la instalación de la aplicación. (0xc7d14fb9) | Instruya al usuario para que acepte la aplicación implementada de Intune e instale la aplicación cuando se le solicite. |
| La desinstalación de la aplicación se ha cancelado porque el proceso se ha reiniciado durante la instalación. (0xc7d14fbc) | El sistema operativo finalizó el proceso de instalación de la aplicación o el dispositivo se reinició. Vuelva a intentar la instalación y recopile los registros de Portal de empresa si se produce este error de nuevo. |
| No se puede instalar el archivo APK de instalación de la aplicación porque no estaba firmado. (0xc7d14fb6) | De forma predeterminada, el sistema operativo Android requiere que las aplicaciones estén firmadas. Asegúrese de que la aplicación está firmada antes de la implementación. |

### <a name="ios-errors"></a>Errores de iOS

| Mensaje o código de error | Descripción/Sugerencias de solución de problemas |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | El agente MDM de Apple ha devuelto que no se pudo ejecutar el comando de instalación. |
| (0x87D1313C) | Se perdió la conexión de red mientras se enviaba la dirección URL del servicio de descarga actualizada al dispositivo. En concreto, no se encontró un servidor con el nombre de host especificado. |
| El dispositivo iOS está ocupado actualmente. (0x87D11388) | El dispositivo iOS estaba ocupado, lo que provocó un error. El dispositivo estaba bloqueado. El usuario debe desbloquear el dispositivo para instalar la aplicación. |
| Error al instalar la aplicación. (0x87D13B64) | Se ha producido un error de instalación de la aplicación. Para solucionar este error se necesitan los registros de la consola de iOS. |
| La aplicación está administrada, pero ha expirado o el usuario la ha quitado. (0x87D13B66) | El usuario desinstaló explícitamente la aplicación o la aplicación expiró pero no se pudo descargar o la detección de la aplicación no coincide con la respuesta del dispositivo. Además, este error se puede producir debido a un error en la plataforma iOS 9.2.2. |
| La aplicación está programada para la instalación, pero necesita un código de canje para completar la transacción. (0x87D13B60) | Este error se suele producir con las aplicaciones de la tienda iOS que son de pago. |
| La aplicación no se encontró después de que la instalación se completara correctamente. (0x87D1041C) | El proceso de detección de la aplicación no coincidía con la respuesta del dispositivo. |
| El usuario ha rechazado la oferta para instalar la aplicación. (0x87D13B62) | Durante la instalación de la aplicación inicial, el usuario hizo clic en Cancelar. Pida al usuario que acepte la solicitud de instalación la próxima vez. |
| El usuario ha rechazado la oferta para actualizar la aplicación. (0x87D13B63) | El usuario final hizo clic en Cancelar durante el proceso de actualización. Implemente como sea necesario o instruya al usuario para que acepte la solicitud de actualización. |
| Error desconocido (0x87D103E8) | Se ha producido un error desconocido durante la instalación de la aplicación. Este es el error resultante cuando no se han producido los otros. |
| Solo se pueden instalar aplicaciones de VPP en iPad compartido (-2016330861). | Las aplicaciones deben obtenerse mediante el Programa de Compras por Volumen de Apple para instalarlas en un iPad compartido. |
| No se pueden instalar las aplicaciones cuando App Store está deshabilitada (-2016330860). | App Store debe estar habilitada para que el usuario pueda instalar la aplicación. |
| No se encuentra la licencia de VPP de la aplicación (-2016330859). | Pruebe a revocar y reasignar la licencia de aplicación. |
| No se pueden instalar aplicaciones del sistema con el proveedor de MDM (-2016330858). | No se permite la instalación de aplicaciones que se instalaron previamente a través del sistema operativo iOS. |
| No se pueden instalar aplicaciones cuando el dispositivo está en modo perdido (-2016330857). | En el modo perdido, se bloquea totalmente el uso del dispositivo. Para instalar aplicaciones, hay que deshabilitar el modo perdido. |
| No se pueden instalar aplicaciones cuando el dispositivo está en pantalla completa (-2016330856). | Pruebe a agregar este dispositivo a un grupo de exclusión para que la directiva de configuración de pantalla completa instale las aplicaciones. |
| No se pueden instalar aplicaciones de 32 bits en este dispositivo (-2016330852). | El dispositivo no admite la instalación de aplicaciones de 32 bits. Pruebe a implementar la versión de 64 bits de la aplicación. |
| Los usuarios deben iniciar sesión en App Store (-2016330855). | El usuario debe iniciar sesión en App Store para que la aplicación se pueda instalar. |
| Problema desconocido. Inténtelo de nuevo (-2016330854). | No se pudo instalar la aplicación debido a un motivo desconocido. Inténtelo más tarde. |
| Error al instalar la aplicación. Intune lo intentará de nuevo la próxima vez que el dispositivo se sincronice (-2016330853). | Se produjo un error de dispositivo en la instalación de la aplicación. Sincronice el dispositivo para intentar instalar la aplicación de nuevo. |
| Error de asignación de licencia con el error de Apple "no hay licencias de PCV restantes" (0x87d13b7e) | Este es el comportamiento esperado. Para solucionarlo, adquiera licencias de PCV adicionales o reclame licencias de usuarios que ya no tengan como destino. |
| Error de instalación de la aplicación 12024: causa desconocida. (0x87d13b6e) | Apple no nos ha proporcionado información suficiente para determinar por qué se produjo un error en la instalación. No hay nada que notificar. |
| Directiva de configuración de aplicaciones necesaria no presente, asegúrese de que la Directiva está destinada a los mismos grupos. (0x87d13b7f) | La aplicación requiere la configuración de la aplicación, pero no hay ninguna configuración de aplicación de destino. El administrador debe asegurarse de que los grupos de destino de la aplicación también tienen la configuración de la aplicación necesaria destinada a los grupos. |
| Las licencias de PCV de dispositivo solo se pueden aplicar a dispositivos iOS 9.0 +. (0x87d13b69) | Actualice los dispositivos iOS afectados a iOS 9.0 +. |
| La aplicación se instala en el dispositivo, pero no está administrada. (0x87d13b8f) | Este error solo se produce en aplicaciones LOB. La aplicación se instaló fuera de Intune. Para solucionar este error, desinstale la aplicación del dispositivo. La próxima vez que se produzca la sincronización del dispositivo, el dispositivo debe instalar la aplicación desde Intune. |
| El usuario rechazó la administración de aplicaciones (0x87d13b68) | Pida al usuario que acepte la administración de aplicaciones. |
| Error desconocido. (0x87d1279d) | Este error se produce en las aplicaciones de la tienda iOS, pero se desconoce el escenario de error. |
| No se pudo actualizar la versión más reciente de la aplicación desde una versión anterior. (0x87D13B9D) | Este mensaje de error se muestra si la aplicación está instalada y administrada, pero con la versión incorrecta en el dispositivo. Esta situación incluye el momento en que un dispositivo ha recibido un comando para actualizar una aplicación, pero la nueva versión aún no se ha instalado y se ha devuelto. Este error se notificará para la primera inserción en el repositorio de un dispositivo después de la implementación de la actualización y se producirá hasta que el dispositivo informe de que la nueva versión está instalada o se produce un error debido a un error diferente.  |


### <a name="other-installation-errors"></a>Otros errores de instalación

|  Mensaje o código de error  |  Descripción  |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  0x80073CFF, 0x80CF201C (error del cliente)  |  Para instalar esta aplicación, debe tener un sistema habilitado para instalación de prueba. Asegúrese de que el paquete de la aplicación tenga una firma de confianza y se haya instalado en un dispositivo unido al dominio que tenga habilitada la directiva **AllowAllTrustedApps** o en un dispositivo que tenga una licencia de instalación de prueba de Windows con la directiva **AllowAllTrustedApps** habilitada. Para más información, consulte [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows).   |
|  0x80073CF0  |  No se pudo abrir el paquete. Posibles causas:<ul><li> El paquete no está firmado.</li><li> El nombre del publicador no coincide con el sujeto que firma el certificado.</li></ul> Compruebe el registro de eventos **AppxPackagingOM** para más información. Para más información, consulte [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows).  |
|  0x80073CF3  |  Error de actualización, dependencia o validación de conflicto en el paquete. Posibles causas:<ul><li> El paquete entrante entra en conflicto con un paquete instalado.</li><li> No se encuentra una dependencia del paquete especificado.</li><li> El paquete no es compatible con la arquitectura correcta del procesador.</li></ul> Compruebe el registro de eventos **AppXDeployment-Server** para información. Para más información, consulte [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows).  |
|  0x80073CFB  |  El paquete suministrado ya está instalado y se ha bloqueado la reinstalación del paquete. Podría recibir este error si está instalando un paquete que no es idéntico al paquete que ya está instalado. Confirme que la firma digital también forma parte del paquete. Cuando un paquete se vuelve a generar o a firmar, dicho paquete ya no es idéntico bit a bit al paquete instalado previamente. Dos opciones para corregir este error son:<ul><li> Incrementar el número de versión de la aplicación y, a continuación, volver a generar y a firmar el paquete.</li><li> Quitar el paquete antiguo para todos los usuarios del sistema antes de instalar el nuevo paquete.</li></ul> Para más información, consulte [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows).  |
|  0x87D1041C  |  La instalación de la aplicación se realizó correctamente, pero esta no se detecta. La aplicación se implementó correctamente mediante Intune y luego se desinstaló. Las razones por las que la aplicación se va a desinstalar son:<ul><li> El usuario final desinstaló la aplicación.</li><li> La información de identidad en el paquete no coincide con lo que el dispositivo informa para las aplicaciones incorrectas.</li><li>Para los MSI de actualización automática, la versión del producto no coincide con la información de la aplicación después de que se actualiza fuera de Intune.</li></ul> Indique al usuario que vuelva a instalar la aplicación desde el portal de empresa. Tenga en cuenta que las aplicaciones necesarias se reinstalarán automáticamente cuando se vuelva a registrar el dispositivo.  |
|  0x8000FFFF  |  Error inesperado durante la instalación. Compruebe los registros de instalación para obtener más información.  |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Solucionar problemas de aplicaciones de la Microsoft Store

La información contenida en el tema [Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (Solucionar problemas de empaquetado, implementación y consulta de aplicaciones de la Microsoft Store) le ayuda a solucionar problemas comunes que pueden surgir al instalar aplicaciones desde la Microsoft Store, tanto si usa Intune como otros medios.

## <a name="app-troubleshooting-resources"></a>Recursos de solución de problemas de aplicaciones
- [Implementación de Visio y Project como parte de la implementación de Office Pro Plus](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Tomar medidas para garantizar que las aplicaciones de MSfB implementadas a través de Intune se instalen en Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Solución de problemas de implementaciones de aplicaciones MSI en Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Prácticas recomendadas para la distribución de software en el agente de PC de Windows clásico de Intune](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Pasos siguientes

- Para obtener información adicional sobre la solución de problemas de Intune, consulte [Uso del portal de solución de problemas para ayudar a los usuarios de su empresa](help-desk-operators.md). 
- Obtenga información sobre los problemas conocidos de Microsoft Intune. Para obtener más información, vea [éxito de clientes](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)de Intune.
- ¿Necesita más ayuda? Consulte [Cómo obtener asistencia para Microsoft Intune](get-support.md).
