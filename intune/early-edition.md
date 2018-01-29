---
title: "Edición anticipada"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/18/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 12f4a09fe10ec792abe8183369a21f53c23f5d1a
ms.sourcegitcommit: 53d272defd2ec061dfdfdae3668d1b676c8aa7c6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="the-early-edition-for-microsoft-intune---january-2018"></a>La edición anticipada de Microsoft Intune: enero de 2018

La **edición anticipada** proporciona una lista de características que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No comparta esta información fuera de la compañía. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

> [!Note]
>Los siguientes cambios están en fase de desarrollo de Intune. Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->


## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure

### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546---"></a>Resolución más sencilla de los problemas de compatibilidad de la aplicación Portal de empresa para Windows 10 <!--676546 -->

Los usuarios finales que tienen dispositivos Windows podrán seleccionar el motivo de no compatibilidad en la aplicación Portal de empresa. Cuando sea posible, se les llevará directamente a la ubicación correcta de la aplicación de configuración para poder resolver el problema.

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>Nueva opción para la autenticación de usuario para la inscripción masiva de Apple <!-- 747625 -->
Intune le ofrecerá la opción de autenticar los dispositivos mediante la aplicación Portal de empresa para los siguientes métodos de inscripción:

- Programa de inscripción de dispositivos de Apple
- Apple School Manager
- Inscripción de Apple Configurator

Al usar la opción Portal de empresa, se puede aplicar la autenticación multifactor de Azure Active Directory sin bloquear estos métodos de inscripción.

Al usar la opción Portal de empresa, Intune omite la autenticación de usuario en el Asistente de configuración de iOS para la inscripción de afinidad del usuario. Esto significa que el dispositivo se inscribe inicialmente como un dispositivo sin usuario, por lo que no recibirá las configuraciones ni las directivas de grupos de usuarios. Solo recibirá las configuraciones y las directivas de grupos de dispositivos. Sin embargo, Intune instalará automáticamente la aplicación Portal de empresa en el dispositivo. El primer usuario que inicie la aplicación Portal de empresa e inicie sesión en ella se asociará con el dispositivo en Intune. En este momento, el usuario recibirá las configuraciones y las directivas de sus grupos de usuarios. No se puede cambiar la asociación del usuario sin volver a realizar la inscripción.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Compatibilidad de Intune con varias cuentas del programa del Programa de inscripción de dispositivos (DEP) de Apple o de Apple School Manager (ASM) <!-- 747685 -->
Intune admitirá la inscripción de dispositivos de hasta 100 cuentas distintas del Programa de inscripción de dispositivos de Apple o de Apple School Manager. Cada token cargado puede administrarse por separado para los perfiles y los dispositivos de inscripción. Es posible asignar un perfil de inscripción diferente para cada token de DEP/School Manager. Si se cargan varios tokens de School Manager, solo pueden compartirse de uno en uno con Microsoft School Data Sync.

Tras la migración, la versión beta de las API Graph y los scripts publicados para la administración de Apple DEP o ASM en Graph ya no funcionará. Las nuevas versiones beta de las API Graph están en desarrollo y se publicarán después de la migración.

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eeready---"></a>Selección de las categorías de dispositivos mediante el valor de configuración Obtener acceso a trabajo o escuela <!-- 1058963 eeready -->
Si ha habilitado la [asignación de grupos de dispositivos](https://docs.microsoft.com/en-us/intune/device-group-mapping), se pedirá a los usuarios de Windows 10 que seleccionen una categoría de dispositivo después de la inscripción a través del botón **Conectar** en **Configuración** > **Cuentas** > **Obtener acceso a trabajo o escuela** o durante la configuración rápida.

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Destinación de las directivas de cumplimiento a dispositivos en grupos de dispositivos <!--1307012 -->

Podrá destinar las directivas de cumplimiento a usuarios en los grupos de usuarios. Podrá destinar las directivas de cumplimiento a dispositivos en los grupos de dispositivos.

### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inclusión o exclusión de la asignación de aplicaciones con base en grupos <!-- 1406920 -->

Durante la asignación de aplicaciones y después de seleccionar un tipo de asignación, podrá seleccionar los grupos para incluir, así como los grupos para excluir.

### <a name="remote-erase-command-support----1438084---"></a>Compatibilidad con el comando "Borrar" remoto <!-- 1438084 -->

Los administradores podrán emitir un comando de borrado de forma remota.

> [!IMPORTANT]
> El comando de borrado no se puede deshacer y debe utilizarse con precaución.

El comando de borrado quita todos los datos, incluido el sistema operativo, de un dispositivo. También quita el dispositivo de la administración de Intune. No se genera ninguna advertencia al usuario y el borrado se produce inmediatamente al emitir el comando.

Podrá configurar un código PIN de recuperación de 6 dígitos. Este código PIN se puede usar para desbloquear el dispositivo borrado, momento en que comenzará la reinstalación del sistema operativo. Una vez iniciado el borrado, el PIN aparece en una barra de estado en la hoja de información general del dispositivo en Intune. El PIN permanecerá mientras el borrado esté en curso. Una vez completada la eliminación, el dispositivo desaparecerá por completo de la administración de Intune. Asegúrese de registrar el PIN de recuperación para que la persona que esté restaurando el dispositivo lo pueda usar.

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Datos cifrados de Windows Information Protection (WIP) en los resultados de la búsqueda de Windows <!-- 1469193 -->

Un nuevo parámetro de configuración de la directiva de Windows Information Protection (WIP) permitirá controlar si los datos cifrados por WIP se incluyen en los resultados de la búsqueda de Windows.

### <a name="website-learning-mode----1631908---"></a>Modo de aprendizaje del sitio web <!-- 1631908 -->

Intune presentará una extensión del modo de aprendizaje de Windows Information Protection (WIP). Además de ver información sobre las aplicaciones habilitadas para WIP, podrá ver un resumen de los dispositivos que han compartido datos de trabajo con sitios web. Con esta información, puede determinar qué sitios web se deben agregar a las directivas WIP de grupo y de usuario.

### <a name="updates-to-compliance-emails---1637547---"></a>Actualizaciones de los correos electrónicos sobre compatibilidad <!--1637547 -->

Cuando se envía un correo electrónico para informar de un dispositivo no compatible, se incluirán detalles acerca de los dispositivos no compatibles. El siguiente artículo se actualizará para indicar este hecho: [Acciones automáticas en caso de incumplimiento](#actions-for-noncompliance).

### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Directivas de acceso condicional de Intune solo disponibles en Azure Portal <!-- 1737088 1634311 -->
Simplificaremos la ubicación en la que se configura y administra el acceso condicional. Solo podrá configurar y administrar sus directivas en [Azure Portal](https://portal.azure.com), en **Azure Active Directory** > **Acceso condicional**. Para su comodidad, también podrá acceder a esta hoja desde Intune, en Azure Portal, en **Intune** > **Acceso condicional**.

###  <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Alertas de tokens caducados y tokens que caducan pronto <!-- 1639263 -->
La página de información general mostrará las alertas de los tokens caducados y los tokens que caducan pronto. Al hacer clic en una alerta para un único token, se le dirigirá a la página de detalles del token.  Si hace clic en la alerta con varios tokens, se le dirigirá a una lista de todos los tokens con su estado. Los administradores deben renovar sus tokens antes de la fecha de caducidad.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Impresión remota a través de una red segura <!-- 1709994  -->
Las soluciones de impresión móvil inalámbricas de PrinterOn permitirán a los usuarios imprimir remotamente desde cualquier lugar en cualquier momento a través de una red segura. PrinterOn se integrará con el SDK de aplicaciones de Intune para iOS y Android. Podrá destinar las directivas de protección de aplicaciones a esta aplicación a través de la hoja **Directivas de protección de aplicaciones** de Intune de la consola de administración. Los usuarios finales podrán descargar la aplicación "PrinterOn for Microsoft" a través de Play Store o iTunes para usarla dentro de su ecosistema de Intune.

### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>Aprobación de la aplicación Portal de empresa para Android for Work <!--1797090 -->
Si su organización usa Android for Work, debe aprobar manualmente la aplicación Portal de empresa para Android para seguir recibiendo actualizaciones automáticas desde la tienda de Google Play administrada.

### <a name="faceid-on-ios-devices----1807377---"></a>FaceID en dispositivos iOS<!-- 1807377 -->
Las directivas de protección de aplicaciones de Intune ahora admiten una configuración que controla FaceID en dispositivos iOS. Esta configuración es para los dispositivos que admiten la funcionalidad FaceID (actualmente solo el iPhone X). Esta configuración es independiente de los controles de TouchID admitidos actualmente. Las organizaciones tienen la posibilidad de elegir si se debe confiar en FaceID como una solicitud de PIN válida como alternativa a los controles de TouchID.

### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>API Graph de Microsoft para Intune - Disponibilidad General<!-- 1833289 -->
Las API de Intune en Microsoft Graph proporcionarán acceso mediante programación a los datos y métodos para automatizar acciones administrativas para el servicio de Intune.  Con la **disponibilidad general** de estas API, los clientes, socios y desarrolladores podrán aprovechar las API para integrarse con soluciones internas o comerciales que guardan relación o requieren la compatibilidad de Intune, o bien con otros servicios de Microsoft a través de Microsoft Graph.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Directivas de protección de aplicaciones  <!-- 679615 -->
Las directivas de Intune App Protection ofrecerán la capacidad de crear directivas predeterminadas globales para habilitar rápidamente la protección en todos los usuarios de todo el inquilino.

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Revocación de las aplicaciones del programa de compras por volumen de iOS  <!-- 820863 -->
Para un dispositivo determinado con una o más aplicaciones del programa de compras por volumen (VPP) de iOS, podrá revocar la licencia de aplicación basada en dispositivo asociada para el dispositivo. Revocar una licencia de aplicación no desinstalará la aplicación VPP desde el dispositivo. Para desinstalar una aplicación VPP, debe cambiar la acción de asignación a **Desinstalar**. Para más información, consulte [Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune](vpp-apps-ios.md).

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Revocación de las licencias de un token del programa de compras por volumen de iOS <!-- 820870 -->
Podrá revocar la licencia de todas las aplicaciones del programa de compras por volumen (VPP) de iOS para un token de VPP determinado.

### <a name="new-ios-device-action------1244701---"></a>Nueva acción de dispositivo iOS   <!-- 1244701 -->
Puede apagar los dispositivos iOS 10.3 supervisados. Esta acción apaga inmediatamente el dispositivo sin enviar una advertencia al usuario final. La acción **Shut down (supervised only)** [Apagar (solo con supervisión)] se puede encontrar en las propiedades de dispositivos cuando se selecciona un dispositivo en la carga de trabajo del **dispositivo**.


### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>Intune ahora proporciona la operación Movimiento de cuenta  <!-- 1573558, 1579830 -->
El **Movimiento de cuenta** migra un inquilino de una unidad de escalado de Azure (ASU) a otra. El **Movimiento de cuenta** se puede usar para ambos escenarios iniciados por el cliente, cuando se llama al equipo de soporte técnico de Intune para solicitarlo, y también puede tratarse de un escenario de Microsoft donde este necesita hacer ajustes al servicio en el back-end. Durante el **Movimiento de cuenta**, el inquilino entra en el modo de solo lectura (ROM). Las operaciones de servicio, como la inscripción, el cambio de nombre de los dispositivos, la actualización del estado de cumplimiento, presentarán errores durante el período de ROM.




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Asignación de aplicaciones móviles de Office 365 a dispositivos iOS y Android mediante el tipo de aplicación integrada <!-- 1332318 -->
El tipo de aplicación **integrada** facilita la creación y la asignación de aplicaciones de Office 365 a los dispositivos iOS y Android administrados. Entre estas aplicaciones están las de O365, como Word, Excel, PowerPoint y OneDrive. Puede asignar aplicaciones específicas al tipo de aplicación y, luego, editar la configuración de la información de la aplicación.


### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>Modificación de la resolución de conflictos de asignación para aplicaciones de la tienda iOS <!-- 1480316 -->
Los usuarios finales pueden experimentar un cambio en la disponibilidad de las aplicaciones de la tienda iOS. Actualmente, una aplicación que se ha asignado a dos grupos con un conflicto entre **Requerido y Disponible** y **No aplicable** se resuelve como **Requerido y Disponible**. Con el cambio, una aplicación que experimente este conflicto se resuelve como **No aplicable**.

El cambio soluciona la confusión que se produce cuando una aplicación se asigna a varios grupos con propósitos de aplicación distintos.

Si quiere que la aplicación esté disponible en el portal de trabajo de la información y en el Portal de empresa antes de la publicación de la versión de noviembre, tiene dos opciones:

1. Quitar la asignación **No aplicable** para su grupo.
2. Crear un nuevo grupo que no incluya miembros con el propósito **Requerido y Disponible** asignado, y asignar ese grupo como **No aplicable**.

Para obtener más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).

> [!Note]
> Después del lanzamiento, la versión ya no podrá ver ni modificar las asignaciones de aplicación de administración de dispositivos móviles (MDM) en la consola de Intune clásica. No obstante, puede usar la consola de Azure o Graph API de Intune para asignar las aplicaciones.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>Administración independiente de dispositivos Android for Work y dispositivos Android <!-- 1490731 -->
Intune admitirá la administración de inscripciones de dispositivos Android for Work independientemente de la plataforma Android. Esta configuración se administra en **Inscripción de dispositivos** > **Restricciones de inscripción** > **Restricciones de tipo de dispositivo**. (Anteriormente se encontraban bajo **Inscripción de dispositivos** > **Inscripción en Android for Work** > **Configuración de la inscripción de Android for Work**).

De forma predeterminada, la configuración de los dispositivos Android for Work será igual que la configuración de los dispositivos Android. Sin embargo, dejará de ser así tras modificar la configuración de Android for Work.
 
Si bloquea la inscripción de Android for Work personal, tan solo los dispositivos Android corporativos podrán inscribirse como Android for Work.

Cuando trabaje con la nueva configuración, tenga en cuenta lo siguiente:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Si es la primera vez que incorpora inscripciones de Android for Work
La nueva plataforma Android for Work está bloqueada de manera predeterminada en Restricciones de tipo de dispositivo. Después de incorporar la característica, puede permitir que los dispositivos se inscriban con Android for Work. Para ello, cambie el valor predeterminado o cree una nueva restricción de tipo de dispositivo que sustituya a la predeterminada.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Si ya ha incorporado inscripciones de Android for Work
Si no es la primera que realiza una incorporación, su situación depende de la configuración elegida:

| Setting | Estado de Android for Work en el valor predeterminado de Restricción de tipo de dispositivo | Notas |
| --- | --- | --- |
| **Administrar todos los dispositivos como Android** | Bloqueado | Todos los dispositivos Android deben inscribirse sin Android for Work. |
| **Administrar los dispositivos compatibles como Android for Work** | Permitido | Todos los dispositivos que admiten Android for Work deben inscribirse con Android for Work. |
| **Administrar los dispositivos compatibles para usuarios solo en estos grupos como Android for Work** | Bloqueado | Para invalidar el valor predeterminado, se creó una directiva de restricción de tipo de dispositivo independiente. Esta directiva define los grupos que se seleccionaron previamente para permitir la inscripción de Android for Work. Los usuarios de los grupos seleccionados seguirán teniendo permiso para inscribir sus dispositivos Android for Work. Todos los demás usuarios tienen restringida la inscripción con Android for Work. |

En todos los casos, se conserva la normativa que haya previsto. No se requiere ninguna acción por su parte para seguir permitiendo Android for Work en su entorno, tanto de forma global como por grupo.

El lanzamiento de estos cambios se iniciará con la actualización de noviembre, pero pueden tardar un tiempo en ejecutarse en su cuenta. Cuando estos cambios entren en vigor en su cuenta, recibirá una notificación de confirmación en el portal de Office 365.


### <a name="configure-an-ios-app-pin----1586774---"></a>Configurar un PIN de aplicación iOS <!-- 1586774 -->
Pronto podrá solicitar un PIN para las aplicaciones iOS de destino. En Azure Portal puede configurar el requisito de PIN y la fecha de expiración en días. Para obtener acceso a una aplicación de iOS, se le pedirá al usuario que establezca y use un nuevo PIN. Solo las aplicaciones iOS que tienen habilitada la protección aplicaciones con Intune App SDK serán compatibles con esta característica.

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Actualización de la experiencia del usuario en la aplicación del Portal de empresa para iOS <!--1412866-->

Lanzaremos una actualización importante de la experiencia de usuario para la aplicación del Portal de empresa para iOS. La actualización contará con un cambio de diseño visual completo, que incluye una apariencia y aspecto modernizados con mayor facilidad de uso y accesibilidad. Se mantendrán todas las funcionalidades del Portal de empresa de iOS actuales.

Ofrecemos una versión preliminar de la aplicación del Portal de empresa actualizada para iOS a través del programa TestFlight de Apple para que la use y nos envíe sus comentarios. Regístrese en https://aka.ms/intune_ios_cp_testflight para obtener acceso a TestFlight. 

![imágenes de avance para la nueva aplicación del Portal de empresa de iOS](./media/ios-cp-app-redesign-1801-teaser.png)


<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Los sitios web de Azure Active Directory pueden requerir la aplicación Intune Managed Browser y compatibilidad con el inicio de sesión único para Managed Browser (versión preliminar pública) <!-- 710595 -->   
Con Azure Active Directory (Azure AD), podrá restringir el acceso a sitios web en dispositivos móviles a la aplicación Intune Managed Browser. En Managed Browser, los datos del sitio web permanecen seguros y separados de los datos personales del usuario final. Además, Managed Browser admite funciones de inicio de sesión único para sitios protegidos por Azure AD. Al iniciar sesión en Managed Browser, o al usarlo en un dispositivo con otra aplicación administrada por Intune, se permite que Managed Browser tenga acceso a sitios corporativos protegidos por Azure AD sin necesidad de que el usuario escriba sus credenciales. Esta funcionalidad se aplica a sitios como Outlook Web Access (OWA) y SharePoint Online, así como a otros sitios corporativos, como los recursos de intranet a los que se tiene acceso a través de Azure App Proxy.


<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Compatibilidad con una directiva de actualización de la edición de Windows 10   <!-- 903672(archived), 1119689 -->  
Podrá crear una directiva de actualización de la edición de Windows 10 que actualice los dispositivos con Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education y Windows 10 Professional Education N. Para obtener más información sobre las actualizaciones de la edición de Windows 10, vea [Configuración de actualizaciones de la edición de Windows 10](edition-upgrade-configure-windows-10.md).




<!-- the following are present prior to 1709 -->


### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune App Protection y Herramientas de desarrollo de Citrix MDX <!-- 709185 -->
Puede administrar dispositivos y aplicaciones con una combinación de Citrix XenMobile MDX y Microsoft Intune. Esto le permite administrar aplicaciones con la directiva de protección de aplicaciones de Intune mientras usa tecnología mVPN de Citrix.

Puede buscar un repositorio de código que contiene la herramienta de ajuste de aplicaciones de Intune e Intune App SDK para iOS y Android, que se integra con la tecnología mVPN de Citrix MDX.




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Redireccionamiento a los usuarios de macOS a nuestra nueva aplicación Portal de empresa <!--1380728-->   
Cuando un usuario final inicia sesión en el sitio web del Portal de empresa para inscribir su dispositivo macOS, se le dirigirá a la descarga de la nueva aplicación Portal de empresa para macOS a fin de que complete el proceso. Esto ocurre con los dispositivos macOS que usan OS X El Capitan 10.11 o una versión posterior. 



<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Compatibilidad de Intune Managed Browser con iOS y Android <!-- 1374196 -->
A partir de octubre de 2017, la aplicación Intune Managed Browser en dispositivos Android admitirá solo los dispositivos con Android 4.4 y versiones posteriores. La aplicación Intune Managed Browser en iOS solo admitirá dispositivos con iOS 9.0 y versiones posteriores. Las versiones anteriores de iOS y Android podrán seguir usando Intune Managed Browser, pero no podrán instalar nuevas versiones de la aplicación y es posible que no puedan tener acceso a todas las funcionalidades de la aplicación. Le recomendamos que actualice la versión del sistema operativo de estos dispositivos a una que sea compatible.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensaje de error mejorado cuando un usuario alcanza el número máximo de dispositivos permitidos para la inscripción <!-- 1270370 -->
En lugar de un mensaje de error genérico, los usuarios finales con dispositivos Android ven un mensaje de error descriptivo que requiere acción: "Ya ha inscrito el máximo número de dispositivos permitidos por su administrador de TI. Quite un dispositivo inscrito o reciba ayuda de su administrador de TI".




## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.




### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.
