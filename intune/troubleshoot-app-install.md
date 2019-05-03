---
title: Solucionar problemas de instalación de aplicaciones
titleSuffix: Microsoft Intune
description: Use el panel de solución de problemas de Microsoft Intune, el cual le ayuda a solucionar problemas de instalación de aplicaciones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/19/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 574f509383891ff3e8e0f4c1b04a19832a378829
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799508"
---
# <a name="troubleshoot-app-installation-issues"></a>Solucionar problemas de instalación de aplicaciones

En algunas ocasiones, las instalaciones de aplicaciones en los dispositivos administrados por MDM de Microsoft Intune pueden presentar errores. Cuando esto ocurre, puede ser complicado entender el motivo del error o cómo solucionarlo. Microsoft Intune proporciona detalles del error de instalación de aplicaciones que permiten a los operadores del departamento de soporte técnico y a los administradores de Intune ver información de la aplicación para atender las solicitudes de ayuda al usuario. En el panel de solución de problemas de Intune se proporcionan detalles del error, incluidos aquellos sobre las aplicaciones administradas en el dispositivo de un usuario. Se proporcionan detalles sobre el ciclo de vida de un extremo a otro en cada dispositivo individual del panel **Aplicaciones administradas**. Puede ver problemas de instalación, por ejemplo, al crearse, modificarse, dirigirse y entregarse la aplicación a un dispositivo. 

## <a name="app-troubleshooting-details"></a>Información para solucionar errores de aplicación

Intune proporciona los detalles de solución de problemas de la aplicación en función de las aplicaciones instaladas en el dispositivo de un usuario específico.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
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

## <a name="win32-app-installation-troubleshooting"></a>Solución de problemas de instalación aplicación Win32

Seleccione la aplicación de Win32 que se implementó mediante la extensión de administración de Intune. Puede seleccionar la **recopilar registros** cuando se produce un error en la instalación de la aplicación de Win32. 

> [!IMPORTANT]
> El **recopilar registros** opción no se habilitará cuando se ha instalado correctamente la aplicación de Win32 en el dispositivo.<p>Para poder recopilar información de registro de aplicación de Win32, debe instalarse la extensión de administración de Intune en el cliente de Windows. La extensión de administración de Intune se instala cuando se implementa un script de PowerShell o una aplicación Win32 en un grupo de seguridad de dispositivos o usuarios. Para obtener más información, consulte [extensión Administración de Intune: requisitos previos](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Recopilar archivos de registro

Para recopilar los registros de instalación de la aplicación de Win32, primero siga los pasos indicados en la sección [detalles de la solución de problemas de aplicación](troubleshoot-app-install.md#app-troubleshooting-details). A continuación, continúe con los pasos siguientes:

1. Haga clic en el **recopilar registros** opción el **detalles de la instalación** hoja.

    <image alt="Win32 app installation details - Collect log option" src="media/troubleshoot-app-install-04.png" width="500" />

2. Proporcionar las rutas de acceso de archivo con el registro de nombres de archivo para iniciar el proceso de recopilación de archivos de registro y haga clic en **Aceptar**.
    
    > [!NOTE]
    > Recopilación de registros tardará menos de dos horas. Tipos de archivo admitidos: *. log, .txt, .dmp, .cab, .zip, .xml, .evtx y .evtl*. Se permite un máximo de 25 rutas de acceso de archivo.

3. Una vez que se han recopilado los archivos de registro, puede seleccionar la **registros** vínculo para descargar los archivos de registro.

    <image alt="Win32 app log details - Download logs" src="media/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Se mostrará una notificación que indica el éxito de la recopilación de registros de aplicación.

#### <a name="win32-log-collection-requirements"></a>Requisitos de recopilación del registro de Win32

Hay requisitos específicos que se deben seguir para recopilar archivos de registro:

- Debe especificar la ruta de acceso del archivo de registro completo. 
- Puede especificar variables de entorno para la recopilación de registros, como las siguientes:<br>
  *% PROGRAMFILES %, % PROGRAMDATA % PÚBLICA %, % WINDIR %, % TEMP %, % TMP %*
- Extensiones de archivo exacto sólo se permiten, como:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- El archivo de registro máximo para cargar es 60 MB o 25 archivos, lo que ocurra primero. 
- Recopilación de registros de instalación de aplicación Win32 está habilitada para las aplicaciones que cumplen el necesarios disponibles y desinstalar la intención de asignación de aplicación.
- Los registros almacenados se cifran para proteger cualquier información PII contenido en los registros.
- Mientras los vales de soporte técnico de apertura para errores de aplicaciones de Win32, adjunte los registros de error relacionados con los pasos indicados anteriormente.

## <a name="app-installation-errors"></a>Errores de instalación de la aplicación

Los siguientes mensajes de error y descripciones proporcionan detalles sobre errores de instalación de iOS y Android. 

### <a name="android-errors"></a>Errores de Android

|    Mensaje o código de error    |    Descripción    |
|----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    No se pudo instalar la aplicación. (0xC7D14FB5)    |    Este mensaje de error se muestra cuando Intune no puede determinar la causa del error de instalación de la aplicación de Android. Durante el error Android no proporciona ninguna información.       Este error se devuelve cuando la descarga de APK se realizó correctamente, pero no se pudo instalar la aplicación. Este error se puede producir con más frecuencia debido a un archivo APK incorrecto que no se puede instalar en el dispositivo. Una posible causa puede ser cuando Google Play Protect bloquea la instalación de la aplicación por motivos de seguridad. Otra causa posible de este error es cuando un dispositivo no es compatible con la aplicación. Por ejemplo, si la aplicación requiere la versión 21+ de la API y el dispositivo actualmente tiene la versión 19.         Intune devuelve este error para los dispositivos DA y KNOX, y aunque puede haber una notificación de que los usuarios pueden hacer clic para volverlo a intentar, si hay un problema con el APK, nunca seguirá generando un error. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.        |
|    La instalación de la aplicación se ha cancelado porque el archivo de instalación (APK) se ha eliminado después de la descarga, pero antes de la instalación. (0xC7D14FBA)    |    La descarga del archivo APK se realizó correctamente pero, antes de que el usuario instalara la aplicación, el archivo se quitó del dispositivo. Esto podría ocurrir si se ha producido una diferencia de tiempo considerable entre la descarga y la instalación. Por ejemplo, el usuario canceló la instalación original, esperó y, después, hizo clic en la notificación para intentarlo de nuevo.         Este mensaje de error solo se devuelve para escenarios de DA. Los escenarios de KNOX se pueden realizar en modo silencioso. Se presenta una notificación de reintento para que el usuario pueda aceptar en lugar de cancelar. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.    |
|    La instalación de la aplicación se ha cancelado porque el proceso se ha reiniciado durante la instalación. (0xC7D14FBB)    |    El dispositivo se ha reiniciado durante el proceso de instalación de APK, lo que resultó en una instalación cancelada.        Este mensaje de error se devuelve para los dispositivos DA y KNOX. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.    |
|    La aplicación no se encontró después de que la instalación se completara correctamente. (0x87D1041C)    |    El usuario desinstaló la aplicación de forma explícita. Este error no se devuelve desde el cliente. Es un error que se produce cuando la aplicación estaba instalada en algún momento pero que después el usuario desinstaló. Este error solo debería producirse para las aplicaciones necesarias. Los usuarios pueden desinstalar las aplicaciones que no son requeridas. Este error solo puede ocurrir en DA. KNOX bloquea la desinstalación de las aplicaciones administradas.       En la sincronización siguiente se volverá a publicar la notificación en el dispositivo para que el usuario lo instale.   El usuario puede ignorar la notificación. Este error se seguirá notificando hasta que el usuario instale la aplicación.    |
|    Error desconocido en la descarga. (0xC7D14FB2)    |    Este error aparece cuando se produce un error en la descarga. Normalmente, este error puede producirse debido a problemas de Wi-Fi o conexiones lentas.       Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.    |
|    Error desconocido en la descarga. La directiva se reintentará la próxima vez que el dispositivo se sincronice. (0xC7D15078)    |    Este error aparece cuando se produce un error en la descarga. Normalmente, este error puede producirse debido a problemas de Wi-Fi o conexiones lentas.       Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa.    |
|    El usuario final ha cancelado la instalación de la aplicación. (0xC7D14FB1)    |    El usuario desinstaló la aplicación de forma explícita. Este error se devuelve cuando la actividad de instalación del sistema operativo Android ha sido cancelada por el usuario. El usuario presionó el botón de cancelación cuando se presentó el mensaje de instalación del sistema operativo, o bien hizo clic fuera del mensaje.        Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.    |
|    El proceso de descarga de archivo se detuvo de manera inesperada. (0xC7D15015)    |    El sistema operativo detuvo el proceso de descarga antes de que se completara. Este error se puede producir cuando el dispositivo tiene poca batería o la descarga está tardando demasiado.       Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa. Intune presenta una notificación en la que los usuarios pueden hacer clic para volver a intentarlo. Si la aplicación es una aplicación disponible, la notificación se puede descartar. Pero si la aplicación es requerida, no se podrá descartar.    |
|    El servicio de descarga de archivo se detuvo de manera inesperada. La directiva se reintentará la próxima vez que el dispositivo se sincronice. (0xC7D1507C)    |    El sistema operativo detuvo el proceso de descarga antes de que se completara. Este error se puede producir cuando el dispositivo tiene poca batería o la descarga está tardando demasiado.       Este error solo se devuelve para escenarios de DA. Para escenarios de KNOX, no se le pide al usuario que realice la instalación, esto se puede hacer de forma silenciosa.    |

### <a name="ios-errors"></a>Errores de iOS

| Mensaje o código de error | Sugerencias de descripción y solución de problemas |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | El agente MDM de Apple ha devuelto que no se pudo ejecutar el comando de instalación. |
| (0x87D1313C) | Se perdió la conexión de red mientras se enviaba la dirección URL del servicio de descarga actualizada al dispositivo. En concreto, no se encontró un servidor con el nombre de host especificado. |
| El dispositivo iOS está ocupado actualmente. (0x87D11388) | El dispositivo iOS estaba ocupado, lo que provocó un error. |
| Error al instalar la aplicación. (0x87D13B64) | Se ha producido un error de instalación de la aplicación. Para solucionar este error se necesitan los registros de XCODE. |
| La aplicación está administrada, pero ha expirado o el usuario la ha quitado. (0x87D13B66) | El usuario ha desinstalado la aplicación de forma explícita. O bien, la aplicación ha expirado, pero no se pudo descargar o la detección de la aplicación no coincide con la respuesta del dispositivo.   Además, este error se puede producir debido a un error en la plataforma iOS 9.2.2. |
| La aplicación está programada para la instalación, pero necesita un código de canje para completar la transacción. (0x87D13B60) | Este error se suele producir con las aplicaciones de la tienda iOS que son de pago. |
| La aplicación no se encontró después de que la instalación se completara correctamente.   (0x87D1041C) | El proceso de detección de la aplicación no coincidía con la respuesta del dispositivo. |
| El usuario ha rechazado la oferta para instalar la aplicación. (0x87D13B62) | Durante la instalación de la aplicación inicial, el usuario hizo clic en Cancelar. |
| El usuario ha rechazado la oferta para actualizar la aplicación. (0x87D13B63) | El usuario final hizo clic en Cancelar durante el proceso de actualización. |
| Error desconocido (0x87D103E8) | Se ha producido un error desconocido durante la instalación de la aplicación. Este es el error resultante cuando no se han producido los otros. |
| Solo se puede instalar aplicaciones de PCV en iPad compartido (-2016330861). | Las aplicaciones deben obtenerse mediante el programa de compras por volumen de Apple para instalar en un iPad compartido. |
| No se puede instalar las aplicaciones cuando se deshabilita App Store (-2016330860).  | Store de la aplicación debe estar habilitada para que el usuario que instale la aplicación. |
| No se encuentra la licencia VPP para aplicación (-2016330859).  | Pruebe a revocar y reasignar la licencia de aplicación. |
| No se puede instalar las aplicaciones del sistema con su proveedor de MDM (-2016330858). | Instalación de aplicaciones que se instalaron previamente por el sistema operativo iOS no es un escenario admitido. |
| No se puede instalar las aplicaciones cuando el dispositivo está en modo perdido (-2016330857). | Todo el uso del dispositivo está bloqueado en el modo perdido.   Deshabilitar modo perdido para instalar aplicaciones. |
| No se puede instalar las aplicaciones cuando el dispositivo está en modo de pantalla completa (-2016330856). | Pruebe a agregar este dispositivo a un grupo de exclusión para la directiva de configuración del modo de pantalla completa para instalar aplicaciones. |
| No se puede instalar aplicaciones de 32 bits en este dispositivo (-2016330852). | El dispositivo no admite la instalación de aplicaciones de 32 bits. Intente implementar la versión de 64 bits de la aplicación. |
| Usuario debe iniciar sesión en el Store de la aplicación (-2016330855). | El usuario debe iniciar sesión en el Store de la aplicación antes de que se puede instalar la aplicación. |
| Problema desconocido. Inténtelo de nuevo (-2016330854). | No se pudo instalar la aplicación debido a un motivo desconocido.   Inténtelo de nuevo más tarde. |
| No se pudo instalar la aplicación. Intune intentará la próxima vez que el dispositivo se sincronice (-2016330853). | Instalación de la aplicación detectó un error de dispositivo. Sincronice el dispositivo para intentar instalar de nuevo la aplicación. |

### <a name="other-installation-errors"></a>Otros errores de instalación

|    Mensaje o código de error    |    Descripción    |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    0x80073CFF, 0x80CF201C (error del cliente)    |    Para instalar esta aplicación, debe tener un sistema habilitado para instalación de prueba. Asegúrese de que el paquete de la aplicación tenga una firma de confianza y se haya instalado en un dispositivo unido al dominio que tenga habilitada la directiva **AllowAllTrustedApps** o en un dispositivo que tenga una licencia de instalación de prueba de Windows con la directiva **AllowAllTrustedApps** habilitada. Para más información, consulte [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows).     |
|    0x80073CF0    |    No se pudo abrir el paquete. Posibles causas:<ul><li> El paquete no está firmado.</li><li> El nombre del publicador no coincide con el sujeto que firma el certificado.</li></ul> Compruebe el registro de eventos **AppxPackagingOM** para más información. Para más información, consulte [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows).    |
|    0x80073CF3    |    Error de actualización, dependencia o validación de conflicto en el paquete. Posibles causas:<ul><li> El paquete entrante entra en conflicto con un paquete instalado.</li><li> No se encuentra una dependencia del paquete especificado.</li><li> El paquete no es compatible con la arquitectura correcta del procesador.</li></ul> Compruebe el registro de eventos **AppXDeployment-Server** para información. Para más información, consulte [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows).    |
|    0x80073CFB    |    El paquete suministrado ya está instalado y se ha bloqueado la reinstalación del paquete. Podría recibir este error si está instalando un paquete que no es idéntico al paquete que ya está instalado. Confirme que la firma digital también forma parte del paquete. Cuando un paquete se vuelve a generar o a firmar, dicho paquete ya no es idéntico bit a bit al paquete instalado previamente. Dos opciones para corregir este error son:<ul><li> Incrementar el número de versión de la aplicación y, a continuación, volver a generar y a firmar el paquete.</li><li> Quitar el paquete antiguo para todos los usuarios del sistema antes de instalar el nuevo paquete.</li></ul> Para más información, consulte [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Solución de problemas de empaquetado, implementación y consulta de aplicaciones de la Tienda Windows).    |
|    0x87D1041C    |    La instalación de la aplicación se realizó correctamente, pero esta no se detecta. La aplicación se implementó correctamente mediante Intune y luego se desinstaló. Las razones por las que la aplicación se va a desinstalar son:<ul><li> El usuario final desinstaló la aplicación.</li><li> La información de identidad en el paquete no coincide con lo que el dispositivo informa para las aplicaciones incorrectas.</li><li>Para los MSI de actualización automática, la versión del producto no coincide con la información de la aplicación después de que se actualiza fuera de Intune.</li></ul> Indique al usuario que vuelva a instalar la aplicación desde el portal de empresa. Tenga en cuenta que las aplicaciones necesarias se reinstalarán automáticamente cuando se vuelva a registrar el dispositivo.    |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Solucionar problemas de aplicaciones de la Microsoft Store

La información contenida en el tema [Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (Solucionar problemas de empaquetado, implementación y consulta de aplicaciones de la Microsoft Store) le ayuda a solucionar problemas comunes que pueden surgir al instalar aplicaciones desde la Microsoft Store, tanto si usa Intune como otros medios.

## <a name="next-steps"></a>Pasos siguientes

- Para obtener información adicional sobre la solución de problemas de Intune, consulte [Uso del portal de solución de problemas para ayudar a los usuarios de su empresa](help-desk-operators.md). 
- Obtenga información sobre los problemas conocidos de Microsoft Intune. Para obtener más información, consulte [Problemas conocidos de Microsoft Intune](known-issues.md).
- ¿Necesita más ayuda? Consulte [Cómo obtener asistencia para Microsoft Intune](get-support.md).
