---
title: "Edición anticipada | Microsoft Docs"
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 249a902e6e10f799dcff4e1c46da90cd62f2c125
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="the-early-edition-for-microsoft-intune---may-2017"></a>La edición anticipada de Microsoft Intune: mayo de 2017

La **edición anticipada** proporciona una lista de características que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme al NDA en una base extremadamente limitada y está vinculada a cambios. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Póngase en contacto con su persona conocida de Intune/PM si tiene alguna pregunta o problema.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

> [!Note]
> Los siguientes cambios están en fase de desarrollo de Intune. Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuevas funcionalidades

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Compatibilidad del inicio de sesión único desde el Portal de empresa para iOS con Outlook para iOS <!--834012-->

Los usuarios ya no tendrán que iniciar sesión en la aplicación de Outlook si ya lo han hecho en la aplicación Portal de empresa para iOS en el mismo dispositivo con la misma cuenta. Cuando los usuarios inicien la aplicación de Outlook, podrán seleccionar su cuenta e iniciar sesión automáticamente. También estamos trabajando para agregar esta funcionalidad en otras aplicaciones de Microsoft.

### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notificación mejorada para PIN de inicio en Samsung KNOX <!--1087143-->

Si los usuarios finales necesitan establecer un PIN de inicio en dispositivos Samsung KNOX a efectos de compatibilidad con el cifrado, cuando dichos usuarios pulsen en la notificación que aparece, se les remitirá al lugar exacto de la aplicación de configuración.  Anteriormente, la notificación remitía al usuario final a la pantalla de cambio de contraseña.

### <a name="promoting-the-most-current-version-of-the-company-portal-for-android---1098661--"></a>Promoción de la versión más actual del Portal de empresa para Android <!--1098661-->

Los usuarios finales verán una notificación en aplicación cuando se publique una nueva versión recomendada de la aplicación de Portal de empresa para Android en la pantalla de notificaciones de la aplicación. Esta notificación indicará a los usuarios que "se encuentra disponible una actualización del Portal de empresa". Al pulsar en la notificación, se abrirá una página web en la que se mostrará la lista de tiendas de aplicaciones disponibles desde las que pueden descargar la versión actualizada. 

### <a name="improvements-to-app-syncing-with-windows-10-creators-update----676505---"></a>Mejoras en la sincronización de aplicaciones con Windows 10 Creators Update <!-- 676505 -->

El Portal de empresa para Windows 10 iniciará automáticamente una sincronización de las solicitudes de instalación de aplicaciones para dispositivos con Windows 10 Creators Update (1704). De esta forma, se reducirá el problema de estancamiento de las instalaciones de aplicaciones durante el estado "Pending Sync" (Sincronización pendiente). Además, los usuarios podrán iniciar manualmente la sincronización desde dentro de la aplicación. 

El Portal de empresa para Windows 10 también expondrá un botón de actualización para permitir al usuario que actualice el contenido de la aplicación siempre que lo necesite. 

## <a name="notices"></a>Notificaciones

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->

Apple ha anunciado que, a partir de la primavera de 2017, se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS. Visite nuestro [blog de soporte técnico de Intune](https://aka.ms/compportalats) para obtener más información.

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->

Para las cuentas de Intune creadas después de enero de 2017, Intune ha habilitado el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en el portal de vista previa de Azure. Anteriormente, la vista previa de inscripción de Apple solo era accesible desde los vínculos al portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requerirán una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero la información estará disponible tan pronto como sea posible. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta no tiene acceso a la versión preliminar.

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Novedades para Appx en Intune en Azure <!-- 1000270 -->

Como parte de la migración a Intune en Azure, estamos realizando tres cambios de appx:

1. Agregar un nuevo tipo de aplicación appx en la consola clásica de Intune que solo se puede implementar en dispositivos inscritos en MDM.
2. Reasignar el tipo de aplicación appx existente para que solo esté dirigido a equipos administrados mediante el agente de PC de Intune.
3. Convertir todos los appxs existentes en appxs de MDM con la migración.

Esto no afectará a ninguna de sus implementaciones existentes en dispositivos que estén administrados mediante el agente de PC de Intune. No obstante, tras la migración, no podrá implementar esos appxs migrados en ningún dispositivo nuevo administrado mediante el agente de PC de Intune que no estuviera seleccionado anteriormente.

Tras la migración, deberá volver a cargar el appx de nuevo como un appx de PC si quiere realizar nuevas implementaciones de PC. Para obtener más información, consulte [Appx changes in Intune on Azure](https://aka.ms/appxchange) (Cambios de appx en Intune en Azure) en el blog del equipo de soporte técnico de Intune.  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Versión preliminar pública de la nueva experiencia de administración de Intune en Azure <!--736542-->

A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API Graph.

Nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en el portal de Azure de este mes. Durante el estado de versión preliminar, se proporcionarán funcionalidades y paridad con la consola de Intune existente de manera iterativa.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si quiere probar o examinar alguna de las nuevas características hasta que se migre su inquilino, regístrese para obtener una nueva cuenta de prueba de Intune o revise la [nueva documentación](https://docs.microsoft.com/intune/what-is-intune).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Compatibilidad con las opciones de configuración administradas para aplicaciones Android <!-- 621621 -->

Podrá configurar las aplicaciones Android de Play Store que admiten opciones de configuración administradas.  Esta característica permite ver la lista de valores de configuración que admite una aplicación y proporciona una interfaz de usuario interactiva y de primera clase que permite configurar dichos valores.

### <a name="remote-assistance-for-android-devices----675418---"></a>Asistencia remota para dispositivos Android <!-- 675418 -->

Intune usará el software [TeamViewer](https://www.teamviewer.com), comprado por separado, para que pueda ofrecer asistencia remota a los usuarios que estén ejecutando dispositivos Android.

### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Configuración previa de permisos de dispositivo para aplicaciones de Android for Work <!-- 621614 -->

En el caso de las aplicaciones implementadas en perfiles de trabajo de dispositivos Android for Work, podrá configurar el estado de los permisos en cada aplicación. De forma predeterminada, las aplicaciones de Android que requieren permisos de dispositivo como el acceso a la ubicación o la cámara del dispositivo solicitarán a los usuarios que acepten o denieguen permisos.  Por ejemplo, si una aplicación usa el micrófono del dispositivo, se solicita al usuario final que conceda a la aplicación el permiso para usar el micrófono. Esta característica le permitirá definir permisos en nombre del usuario final.  El administrador puede configurar permisos para

- Denegar automáticamente sin notificar al usuario
- Aprobar automáticamente sin notificar al usuario
- Pedir al usuario que acepte o deniegue

### <a name="define-app-specific-pin-for-android-for-work-devices---728976--"></a>Establecimiento de un PIN específico de la aplicación para dispositivos Android for Work <!--728976-->

Podrá definir una directiva de código de acceso que solo se aplique a aplicaciones del perfil de trabajo de dispositivos Android 7.0 y versiones posteriores administrados como un dispositivo Android for Work.  Las opciones son:

- Definir una contraseña de código de acceso a nivel de dispositivo: se trata del código de acceso que el usuario final debe usar para desbloquear todo el dispositivo.
- Definir una directiva de código de acceso solo a nivel de perfil de trabajo: a los usuarios finales se les pedirá que escriban un código de acceso cada vez que se abra cualquier aplicación del perfil de trabajo.
- Definir una directiva para el dispositivo y el perfil de trabajo: los profesionales de TI tienen la opción de definir una directiva de código de acceso para el dispositivo y otra para el perfil de trabajo con diferentes intensidades (por ejemplo, un PIN de cuatro dígitos para desbloquear el dispositivo y un PIN de seis dígitos para abrir cualquier aplicación de trabajo).

>[!NOTE]
> Esta opción sólo estará disponible en Android 7.0 y versiones posteriores.  De forma predeterminada, el usuario final tendrá la opción de usar los dos PIN definidos por separado o de optar por combinar los dos en el más seguro de ellos.

### <a name="manage-password-and-other-android-for-work-settings---1102534--"></a>Administración de contraseñas y de otra configuración de Android for Work <!--1102534-->

Se va a incorporar una nueva directiva de restricción de dispositivos Android for Work que permite administrar la configuración del perfil de trabajo y la contraseña en los dispositivos Android for Work.

###  <a name="new-web-content-filter-policy-for-ios-devices----723832---"></a>Nueva directiva de filtro de contenido web para dispositivos iOS <!-- 723832 -->

Podrá controlar qué sitios web pueden visitar los usuarios de dispositivos iOS mediante uno de los dos métodos siguientes:

  - Agregar direcciones URL permitidas y bloqueadas mediante el filtro de contenido web integrado de Apple.
  - Permitir que el explorador Safari acceda solo a sitios web especificados. Se crearán marcadores en Safari para cada sitio que especifique.

### <a name="apple-school-manager-asm-support---748864--"></a>Compatibilidad de Apple School Manager (ASM) <!--748864-->

Intune admitirá el uso de Apple School Manager (ASM) en lugar del Programa de inscripción de dispositivos de Apple para permitir la inscripción inmediata de dispositivos iOS. Es necesario incorporar ASM para usar la aplicación Classroom para Shared iPads, así como habilitar la sincronización de datos de ASM en Azure Active Directory mediante Microsoft School Data Sync (SDS).  

### <a name="shared-ipad-support---770395-1044681---"></a>Compatibilidad de Shared iPad <!--770395, 1044681 -->

Intune permitirá configurar el modo Shared iPad en el perfil de inscripción para el Programa de inscripción de dispositivos de Apple o para Apple School Manager. Esta configuración permite que varios identificadores de Apple administrados inicien sesión en el mismo dispositivo.

También se expandirá la compatibilidad para administrar la aplicación Classroom en iOS, a fin de incluir a los estudiantes que se registran en dispositivos iPad compartidos con sus identificadores de Apple administrados.

### <a name="new-windows-device-restriction-settings---978585--"></a>Configuración nueva de restricción de dispositivos Windows <!--978585-->

Se va a incorporar una configuración nueva al perfil de restricción de dispositivos Windows que controla características como la proyección inalámbrica, la detección de dispositivos, la conmutación de tareas y los mensajes de error de tarjetas SIM.

### <a name="office-365-proplus-app-available-for-windows-10-devices---1121362--"></a>Disponibilidad de la aplicación Office 365 ProPlus para dispositivos Windows 10 <!--1121362-->

Se va a incorporar el nuevo tipo de aplicación Office 365 ProPlus que facilita la asignación de aplicaciones Office 365 ProPlus a dispositivos Windows 10. Además, también podrá instalar Microsoft Project y Microsoft Visio si dispone de licencias para ellos. Las aplicaciones que desee se agruparán y aparecerán como una única aplicación en la lista de aplicaciones de la consola de Intune.

### <a name="new-allowblock-list-for-the-managed-browser---682960--"></a>Nueva lista de permitidos y bloqueados para Managed Browser <!--682960-->

Podrá configurar la lista de dominios y direcciones URL permitidos y bloqueados para Managed Browser con la opción de configuración de aplicaciones de Intune disponible en Azure Portal. Esta configuración se puede determinar para Managed Browser con independencia de si se usa en un dispositivo administrado o no administrado.

### <a name="new-app-configuration-capabilities----677969---"></a>Nuevas funcionalidades de configuración de aplicaciones <!-- 677969 -->

Esta característica será la equivalente a la configuración de aplicaciones en la Administración de dispositivos móviles (MDM). Permite a los administradores aplicar más valores de configuración de aplicaciones aparte de solo aquellos que se encuentran disponibles a través de las directivas de protección de aplicaciones de MAM sin canal de inscripción.

### <a name="new-app-protection-policies-conditions-for-mam---679864--"></a>Nuevas condiciones de las directivas de protección de aplicaciones para MAM <!--679864-->

Podrá establecer un requisito para MAM sin inscripción de usuarios a través de la consola de administración que exige lo siguiente:

- Versión mínima de la aplicación
- Versión mínima del sistema operativo
- Versión mínima del SDK para aplicaciones de Intune de la aplicación de destino (solo iOS)

Esta característica estará disponible para iOS y Android. Intune admite el cumplimiento del requisito de versiones mínimas de la plataforma de SO, las aplicaciones y el SDK para aplicaciones de Intune. En iOS, las aplicaciones que tienen el SDK integrado también pueden establecer el cumplimiento de una versión mínima a nivel del SDK.

El usuario no podrá acceder a la aplicación de destino si no se cumplen los requisitos mínimos a través de la directiva de protección de aplicaciones a los tres niveles distintos mencionados anteriormente. En este punto, el usuario puede eliminar la cuenta (en aplicaciones con varias identidades), cerrar la aplicación o actualizar la versión del SO o de la aplicación a fin de satisfacer el requisito.

Además, también podrá configurar valores adicionales a través de la consola de administración para proporcionar una notificación sin bloqueo que recomienda una actualización del SO o de la aplicación. Puede cerrar esta notificación, y la aplicación puede usarse de la forma habitual.

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Cambio de la entidad de MDM sin anular la inscripción de dispositivos administrados <!--1103950-->

Podrá cambiar la entidad de MDM sin tener que ponerse en contacto con el Soporte técnico de Microsoft y sin necesidad de anular la inscripción ni de volver a inscribir los dispositivos administrados existentes. En la consola de Configuration Manager, puede cambiar la entidad de MDM de Configurar como Configuration Manager (híbrido) a Microsoft Intune (independiente), o viceversa.


### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new-in-microsoft-intune.md) para obtener más información sobre los desarrollos recientes.

