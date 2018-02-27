---
title: Novedades de Microsoft Intune
titlesuffix: Azure portal
description: Descubra las novedades del portal de Intune Azure
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/01/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5058428dca9212d8b20364f58ac463939a699221
ms.sourcegitcommit: 6d69403266dbcb31c879432719798935c94917fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2018
---
# <a name="whats-new-in-microsoft-intune"></a>Novedades de Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Conozca las novedades semanales de Microsoft Intune. También podrá obtener información sobre los [próximos cambios](#whats-coming), [notificaciones importantes](#notices) sobre el servicio e información sobre las [versiones anteriores](whats-new-archive.md).

> [!Note]
> Para obtener más información sobre la nueva funcionalidad de administración híbrida de dispositivos móviles (MDM), consulte la [página Novedades de MDM híbrida](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

## <a name="week-of-february-5-2018"></a>Semana del 5 de febrero de 2018

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Nueva opción para la autenticación de usuario para la inscripción masiva de Apple <!-- 747625 eeready -->

> [!NOTE]
> Los nuevos inquilinos verán esta característica inmediatamente. En cambio, en el caso de los inquilinos existentes, se implementará en abril. Es posible que no tenga acceso a estas nuevas características hasta que la implementación se haya completado.

Intune ofrece ahora la opción de autenticar los dispositivos mediante la aplicación Portal de empresa para los siguientes métodos de inscripción:

- Programa de inscripción de dispositivos de Apple
- Apple School Manager
- Inscripción de Apple Configurator

Al usar la opción Portal de empresa, se puede aplicar la autenticación multifactor de Azure Active Directory sin bloquear estos métodos de inscripción.

Al usar la opción Portal de empresa, Intune omite la autenticación de usuario en el Asistente de configuración de iOS para la inscripción de afinidad del usuario. Esto significa que el dispositivo se inscribe inicialmente como un dispositivo sin usuario, por lo que no recibe las configuraciones ni las directivas de grupos de usuarios. Solo recibe las configuraciones y las directivas de grupos de dispositivos. Sin embargo, Intune instalará automáticamente la aplicación Portal de empresa en el dispositivo. El primer usuario que inicie la aplicación Portal de empresa e inicie sesión en ella se asociará con el dispositivo en Intune. En este momento, el usuario recibirá las configuraciones y las directivas de sus grupos de usuarios. No se puede cambiar la asociación del usuario sin volver a realizar la inscripción.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Compatibilidad de Intune con varias cuentas del programa del Programa de inscripción de dispositivos (DEP) de Apple o de Apple School Manager (ASM) <!-- 747685 eeready -->

Intune ahora admite la inscripción de dispositivos de hasta 100 cuentas distintas del Programa de inscripción de dispositivos de Apple o de Apple School Manager. Cada token cargado puede administrarse por separado para los perfiles y los dispositivos de inscripción. Es posible asignar un perfil de inscripción diferente para cada token de DEP/School Manager. Si se cargan varios tokens de School Manager, solo pueden compartirse de uno en uno con Microsoft School Data Sync.

Tras la migración, la versión beta de las API Graph y los scripts publicados para la administración de Apple DEP o ASM en Graph ya no funcionará. Las nuevas versiones beta de las API Graph están en desarrollo y se publicarán después de la migración.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Impresión remota a través de una red segura <!-- 1709994  -->
Las soluciones de impresión móvil inalámbricas de PrinterOn permitirán a los usuarios imprimir remotamente desde cualquier lugar en cualquier momento a través de una red segura. PrinterOn se integrará con el SDK de aplicaciones de Intune para iOS y Android. Podrá destinar las directivas de protección de aplicaciones a esta aplicación a través de la hoja **Directivas de protección de aplicaciones** de Intune de la consola de administración. Los usuarios finales podrán descargar la aplicación "PrinterOn for Microsoft" a través de Play Store o iTunes para usarla dentro de su ecosistema de Intune.

## <a name="week-of-january-29-2018"></a>Semana del 29 de enero de 2018

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Alertas de tokens caducados y tokens que caducan pronto <!-- 1639263 -->
Ahora en la página de introducción se muestran las alertas de los tokens caducados y los tokens que caducan pronto. Al hacer clic en una alerta para un único token, se le dirigirá a la página de detalles del token.  Si hace clic en la alerta con varios tokens, se le dirigirá a una lista de todos los tokens con su estado. Los administradores deben renovar sus tokens antes de la fecha de caducidad.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Compatibilidad con el comando "Borrar" de forma remota en dispositivos macOS <!-- 1438084 -->

Los administradores pueden emitir un comando Borrar de forma remota en dispositivos macOS.

> [!IMPORTANT]
> El comando de borrado no se puede deshacer y debe utilizarse con precaución.

El comando de borrado quita todos los datos, incluido el sistema operativo, de un dispositivo. También quita el dispositivo de la administración de Intune. No se genera ninguna advertencia al usuario y el borrado se produce inmediatamente al emitir el comando.

Debe configurar un PIN de recuperación de 6 dígitos. Este código PIN se puede usar para desbloquear el dispositivo borrado, momento en que comenzará la reinstalación del sistema operativo. Una vez iniciado el borrado, el PIN aparece en una barra de estado en la hoja de información general del dispositivo en Intune. El PIN permanecerá mientras el borrado esté en curso. Una vez completada la eliminación, el dispositivo desaparecerá por completo de la administración de Intune. Asegúrese de registrar el PIN de recuperación para que la persona que esté restaurando el dispositivo lo pueda usar.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Revocación de las licencias de un token del programa de compras por volumen de iOS <!-- 820870 --> 
Puede revocar la licencia de todas las aplicaciones del programa de compras por volumen (VPP) de iOS para un token de VPP determinado.

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Revocación de las aplicaciones del programa de compras por volumen de iOS  <!-- 820863 -->
En el caso de un dispositivo determinado con una o más aplicaciones del programa de compras por volumen (VPP) de iOS, puede revocar la licencia de aplicación basada en dispositivo asociada para el dispositivo. Revocar una licencia de aplicación no desinstalará la aplicación VPP desde el dispositivo. Para desinstalar una aplicación VPP, debe cambiar la acción de asignación a **Desinstalar**. Para más información, consulte [Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune](vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Asignación de aplicaciones móviles de Office 365 a dispositivos iOS y Android mediante el tipo de aplicación integrada <!-- 1332318 -->
El tipo de aplicación **integrada** facilita la creación y la asignación de aplicaciones de Office 365 a los dispositivos iOS y Android administrados. Entre estas aplicaciones están las de O365, como Word, Excel, PowerPoint y OneDrive. Puede asignar aplicaciones específicas al tipo de aplicación y, luego, editar la configuración de la información de la aplicación.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inclusión o exclusión de la asignación de aplicaciones con base en grupos <!-- 1406920 -->

Durante la asignación de aplicaciones y después de seleccionar un tipo de asignación, puede seleccionar los grupos para incluir, así como los grupos para excluir.

#### <a name="website-learning-mode----1631908---"></a>Modo de aprendizaje del sitio web <!-- 1631908 -->

Ahora Intune presenta una extensión del modo de aprendizaje de Windows Information Protection (WIP). Además de ver información sobre las aplicaciones habilitadas para WIP, puede ver un resumen de los dispositivos que han compartido datos de trabajo con sitios web. Con esta información, puede determinar qué sitios web se deben agregar a las directivas WIP de grupo y de usuario.

#### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>Aprobación de la aplicación Portal de empresa para Android for Work <!--1797090 -->
Si su organización usa Android for Work, debe aprobar manualmente la aplicación Portal de empresa para Android para seguir recibiendo actualizaciones automáticas desde la tienda de Google Play administrada.

#### <a name="faceid-on-ios-devices----1807377---"></a>FaceID en dispositivos iOS<!-- 1807377 -->
Las directivas de protección de aplicaciones de Intune ahora admiten una configuración que controla FaceID en dispositivos iOS. Esta configuración es para los dispositivos que admiten la funcionalidad FaceID (actualmente solo el iPhone X). Esta configuración es independiente de los controles de TouchID admitidos actualmente. Las organizaciones tienen la posibilidad de elegir si se debe confiar en FaceID como una solicitud de PIN válida como alternativa a los controles de TouchID.

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>Puede asignar una directiva de configuración de aplicación a grupos mediante asignaciones de inclusión o exclusión <!-- 1480316 --> 

Puede asignar una directiva de configuración de aplicación a un grupo de usuarios y dispositivos mediante una combinación de asignaciones de inclusión y exclusión. Las asignaciones se pueden elegir como una selección personalizada de grupos o como un grupo virtual. Un grupo virtual puede incluir **Todos los usuarios**, **Todos los dispositivos** o **Todos los usuarios + todos los dispositivos**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Compatibilidad con una directiva de actualización de la edición de Windows 10   <!-- 903672(archived), 1119689 -->  
Puede crear una directiva de actualización de la edición de Windows 10 que actualice los dispositivos con Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education y Windows 10 Professional Education N. Para obtener más información sobre las actualizaciones de la edición de Windows 10, vea [Configuración de actualizaciones de la edición de Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Directivas de acceso condicional de Intune solo disponibles en Azure Portal <!-- 1737088 1634311 -->

A partir de esta versión, deberá configurar y administrar las directivas de acceso condicional en [Azure Portal](https://portal.azure.com), en **Azure Active Directory** > **Acceso condicional**. Para su comodidad, también puede acceder a esta hoja desde Intune, en Azure Portal, en **Intune** > **Acceso condicional**.

#### <a name="updates-to-compliance-emails---1637547---"></a>Actualizaciones de los correos electrónicos sobre compatibilidad <!--1637547 -->

Cuando se envía un correo electrónico para informar de un dispositivo no compatible, se incluyen detalles sobre los dispositivos no compatibles. 


## <a name="week-of-january-22-2018"></a>Semana del 22 de enero de 2018

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Nueva funcionalidad para la acción "Resolver" en dispositivos Android<!--1583480-->

La aplicación Portal de empresa para Android expande la acción "Resolver" para la opción **Actualizar configuración del dispositivo** para resolver [problemas con el cifrado del dispositivo](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Bloqueo remoto disponible en la aplicación del Portal de empresa para Windows 10 <!--676506-->
Los usuarios finales ya pueden bloquear de forma remota sus dispositivos desde la aplicación del Portal de empresa para Windows 10. No se mostrará para el dispositivo local que usen activamente.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Resolución más sencilla de los problemas de compatibilidad de la aplicación Portal de empresa para Windows 10 <!--676546-->
Los usuarios finales que tengan dispositivos Windows podrán seleccionar el motivo de no compatibilidad en la aplicación Portal de empresa. Cuando sea posible, se les llevará directamente a la ubicación correcta de la aplicación de configuración para poder resolver el problema.

## <a name="week-of-december-11-2017"></a>Semana del 11 de diciembre de 2017

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Nueva configuración de la reimplementación automática <!-- 1469168 -->
La opción de configuración **Reimplementación automática** permite a los usuarios con derechos administrativos eliminar todos los datos de usuario y las opciones de configuración con **Ctrl + Win + R** en la pantalla de bloqueo del dispositivo. En este caso, el dispositivo se vuelve a configurar e inscribir automáticamente para la administración. Esta opción de configuración se puede encontrar en Windows 10 > Restricciones de dispositivos > General > Reimplementación automática. Para más detalles, consulte [Configuración de restricciones de dispositivo de Intune para Windows 10](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Compatibilidad con las ediciones de origen adicionales en la directiva de actualización de edición de Windows 10  <!-- 903672,  1119689 -->
Ahora puede usar la directiva de actualización de edición de Windows 10 para actualizar desde ediciones de Windows 10 adicionales (Windows 10 Pro, Windows 10 Pro Education, Windows 10 Cloud, etc.). Antes de esta versión, las rutas de actualización de edición admitidas estaban más limitadas. Para obtener más información, consulte [Configuración de actualizaciones de la edición de Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Nueva configuración del perfil de configuración de dispositivo del Centro de seguridad de Windows Defender (WDSC) <!-- 1335507 -->

Intune agrega una sección nueva de configuración del perfil de configuración de dispositivo en la protección del punto de conexión denominada **Centro de seguridad de Windows Defender**. Los administradores de TI pueden configurar a qué pilares de la aplicación Centro de seguridad de Windows Defender pueden acceder los usuarios finales. Si un administrador de TI oculta un pilar en la aplicación Centro de seguridad de Windows Defender, las notificaciones relativas al pilar oculto no se mostrarán en el dispositivo del usuario.

Estos son los pilares que los administradores pueden ocultar de la configuración del perfil de configuración de dispositivo del Centro de seguridad de Windows Defender:
- Protección contra amenazas y virus
- Mantenimiento y estado del dispositivo
- Firewall y protecciones de red
- Control de aplicaciones y explorador
- Opciones de familia

Los administradores de TI también pueden personalizar las notificaciones que recibirán los usuarios. Por ejemplo, puede configurar si los usuarios reciben todas las notificaciones que generan los pilares visibles en WDSC o solo las notificaciones críticas. Las notificaciones no críticas incluyen resúmenes periódicos de la actividad de Antivirus de Windows Defender y las notificaciones cuando se completan las detecciones. Todas las otras notificaciones se consideran críticas. Además, también puede personalizar el contenido mismo de la notificación. Por ejemplo, puede proporcionar la información de contacto de TI para insertarla en las notificaciones que aparecen en los dispositivos de los usuarios.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Compatibilidad de varios conectores con el control de certificados SCEP y PFX <!-- 1361755 -->

Los clientes que usan el conector NDES local para entregar los certificados a los dispositivos ahora pueden configurar varios conectores en un solo inquilino.

Esta funcionalidad nueva admite el siguiente escenario:

- **Alta disponibilidad**

Cada conector NDES extrae solicitudes de certificado desde Intune.  Si un conector NDES queda sin conexión, el otro puede seguir procesando las solicitudes.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>El nombre de sujeto de cliente puede utilizar la variable AAD_DEVICE_ID  <!-- 1468599 -->

Cuando se crea un perfil de certificado de SCEP en Intune, ahora puede usar la variable AAD_DEVICE_ID cuando se compila el nombre de sujeto personalizado.   Si se solicita el certificado con este perfil SCEP, la variable se reemplaza por el identificador de dispositivo de AAD del dispositivo que realiza la solicitud de certificado.


### <a name="device-management"></a>Administración de dispositivos

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Administración de dispositivos macOS inscritos en Jamf con el motor conformidad de dispositivos de Intune <!-- 1592747 -->
Ahora puede usar Jamf para enviar la información del estado del dispositivo macOS a Intune, y este a continuación evaluará su conformidad con las directivas definidas en la consola de Intune. En función del estado de conformidad del dispositivo, así como otras condiciones tales como la ubicación, el riesgo del usuario, etc., el acceso condicional aplicará la conformidad para los dispositivos macOS que accedan a la nube y a aplicaciones locales conectadas a Azure AD, incluido Office 365. Consulte más información sobre la [configuración de la integración de Jamf](conditional-access-integrate-jamf.md) y [la exigencia de compatibilidad para dispositivos administrados por Jamf](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Nueva acción de dispositivo iOS   <!-- 1424701 -->

Ahora puede apagar los dispositivos iOS 10.3 supervisados. Esta acción apaga inmediatamente el dispositivo sin enviar una advertencia al usuario final. La acción **Shut down (supervised only)** [Apagar (solo con supervisión)] se puede encontrar en las propiedades de dispositivos cuando se selecciona un dispositivo en la carga de trabajo del **dispositivo**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>No permitir cambios de fecha y hora en dispositivos Samsung Knox <!-- 1468103 -->

Ya puede bloquear los cambios de fecha y hora en dispositivos Samsung KNOX. Encontrará esta característica en **Perfiles de configuración de dispositivo** > **Restricciones de dispositivos (Android)** > **General**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Compatibilidad con la cuenta del recurso de Surface Hub <!-- 1566442  -->

Se ha agregado una nueva acción de dispositivo para que los administradores puedan definir y actualizar la cuenta del recurso asociada con Surface Hub.

Una instancia de Surface Hub usa la cuenta del recurso para autenticarse con Skype o Exchange y así poder unirse a una reunión. Puede crear una cuenta del recurso única para que Surface Hub aparezca en la reunión como la sala de conferencias. Por ejemplo, la cuenta del recurso puede aparecer como *Sala de conferencias B41/6233*. La cuenta del recurso (conocida como la cuenta del dispositivo) de Surface Hub habitualmente se debe configurar para la ubicación de la sala de conferencias y cuando sea necesario cambiar otros parámetros de la cuenta del recurso.

Cuando los administradores deseen actualizar la cuenta del recurso de un dispositivo, deben proporcionar las credenciales actuales de Active Directory o Azure Active Directory asociadas con el dispositivo. Si la rotación de contraseñas está activada en el dispositivo, los administradores deben ir a Azure Active Directory para encontrar la contraseña.

> [!NOTE]
> Todos los campos se envían en un conjunto y sobrescriben todos los campos que ya estaban configurados. Los campos vacíos también sobrescriben los campos existentes.

Los administradores pueden configurar los valores siguientes:

- **Cuenta del recurso**
   - **Usuario de Active Directory**

      NombreDeUsuario\nombredeusuario o nombre principal de usuario (UPN): user@domainname.com

   - **Contraseña**

- **Parámetros opcionales de la cuenta del recurso** (se deben establecer con la cuenta del recurso especificada)

   - **Período de rotación de contraseñas**

     Garantiza que Surface Hub actualice automáticamente la contraseña de la cuenta cada semana por motivos de seguridad. Para configurar cualquier parámetro una vez que esto esté habilitado, la cuenta en Azure Active Directory debe tener primero el restablecimiento de contraseña.

   - **Dirección de SIP (protocolo de inicio de sesión)**

     Solo se usa cuando se produce un error en la detección automática.

   - **Correo electrónico**

     Dirección de correo electrónico de la cuenta del recurso o dispositivo.

   - **Exchange Server**

     Solo se necesita cuando se produce un error en la detección automática.

   - **Sincronización de calendario**

     Especifica si la sincronización de calendario y otros servicios de Exchange Server están habilitados. Por ejemplo: sincronización de reunión.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Instalación de aplicaciones de Office en dispositivos macOS <!-- 1494311 -->
Ahora podrá instalar aplicaciones de Office en dispositivos macOS. Este nuevo tipo de aplicación le permite instalar Word, Excel, PowerPoint, Outlook y OneNote. Estas aplicaciones también incluyen Microsoft AutoUpdater (MAU) para ayudar a mantener aplicaciones seguras y actualizadas.

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Eliminación de un token del programa de compras por volumen de iOS <!-- 820879 -->
Puede eliminar el token del programa de compras por volumen (VPP) de iOS con la consola. Esto puede resultar necesario cuando tiene instancias duplicadas de un token de VPP.

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="end-user-messaging-for-accounts---1573558-for-1712--"></a>Mensajería para las cuentas del usuario final <!--1573558 for 1712-->

Los usuarios del sitio web de Portal de empresa no podrán realizar acciones que requieran acceso de escritura a su inquilino. Verán el mensaje de error correspondiente que explica que su cuenta está en mantenimiento. Próximamente se incorporarán modificaciones similares a las aplicaciones de Portal de empresa para Android, iOS, macOS y Windows. Puede ver este error en las [novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md).



### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>Limitación de la nueva colección de entidades "Usuario actual" a los datos de los usuarios activos actualmente <!-- 1667026 -->

La colección de entidades **Usuarios** muestra todos los usuarios de Azure Active Directory (Azure AD) con licencias asignadas en la empresa. Por ejemplo, es posible que durante el último mes se haya agregado a un usuario a Intune y, luego, se haya eliminado. A pesar de que no esté presente a la hora de generar el informe, el usuario en cuestión y su estado sí que figuran en los datos. Una opción podría ser crear un informe que incluya el historial relativo a la duración de la presencia del usuario en sus datos.

Por otro lado, la nueva colección de entidades **Usuario actual** solo contiene los usuarios que no se hayan eliminado. En otras palabras, la colección de entidades **Usuario actual** solo contiene los usuarios que estén activos actualmente. Para obtener más información sobre la colección de entidades **Usuario actual**, consulte [Referencia de la entidad de usuario actual](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>Actualización de las API Graph <!-- 1736360 -->

Hemos actualizado algunas de las Graph API para Intune que están en versión beta. Consulte el [registro de cambios de Graph API](https://developer.microsoft.com/graph/docs/concepts/changelog) mensual para obtener más información.


## <a name="week-of-december-4-2017"></a>Semana del 4 de diciembre de 2017

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune admite aplicaciones denegadas de Windows Information Protection (WIP) <!-- 1479103 -->
En Intune puede especificar aplicaciones denegadas. Si una aplicación queda denegada, se la bloquea para que no pueda acceder a la información de la empresa, es decir, lo contrario a la lista de aplicaciones permitidas. Para obtener más información, consulte [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Recomendación de lista de aplicaciones denegadas para Windows Information Protection).


## <a name="week-of-november-27-2017"></a>Semana del 27 de noviembre de 2017

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>Solución de problemas de inscripción <!-- 746324 -->

En el área de trabajo **Solución de problemas** ahora se muestran los problemas de inscripción del usuario. Los detalles del problema y los pasos de corrección sugeridos pueden ayudar a los administradores y a los operadores del departamento de soporte técnico a solucionar los problemas. Ciertos problemas de inscripción no se capturan, y es posible que no se sugieran correcciones para algunos errores.

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restricciones de inscripción asignada a grupos <!-- 747598 -->

Como administrador de Intune, ahora puede [crear restricciones de inscripción personalizadas de tipo de dispositivo y de límite de dispositivos para grupos de usuarios](enrollment-restrictions-set.md).

Azure Portal de Intune permite crear un máximo de 25 instancias de cada tipo de restricción que pueden asignarse luego a grupos de usuarios. Las restricciones asignadas por grupo invalidan las restricciones predeterminadas.

Todas las instancias de un tipo de restricción se mantienen en una lista ordenada de forma estricta. Este orden define un valor de prioridad para la resolución de conflictos. Un usuario afectado por más de una instancia de la restricción solo está limitado por la instancia con el valor de prioridad más alto. Para cambiar la prioridad de una determinada instancia, arrástrela a una posición diferente en la lista.

Esta funcionalidad se publicará con la migración de la configuración de Android for Work desde el menú de inscripción de Android for Work al menú de restricciones de inscripción. Puesto que esta migración puede tardar varios días, la versión de noviembre puede afectar primero a otras partes de su cuenta antes de habilitar la asignación de grupo para las restricciones de inscripción.

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Compatibilidad con varios conectores de Servicio de inscripción de dispositivos de red (NDES) <!-- 1528104 -->

NDES permite que los dispositivos móviles que se ejecutan sin credenciales de dominio puedan obtener certificados a través del Protocolo de inscripción de certificados simple (SCEP).
Con esta actualización, se admiten varios conectores NDES.

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Administración independiente de dispositivos Android for Work y dispositivos Android <!-- 1490731 EEready-->

**Nota**: Los cambios siguientes empezarán a implementarse con la actualización de noviembre, pero es posible que se tarde un tiempo en ejecutarse en su cuenta. Cuando estos cambios entren en vigor en su cuenta, recibirá una notificación de confirmación en el portal de Office 365. Después de la implementación, tendrá opciones adicionales de capacidad de administración. No habrá ningún cambio en la experiencia del usuario final durante la implementación.

Intune admite la administración de inscripciones de dispositivos Android for Work independientemente de la plataforma Android. Esta configuración se administra en **Inscripción de dispositivos** > **Restricciones de inscripción** > **Restricciones de tipo de dispositivo**. (Anteriormente se encontraban bajo **Inscripción de dispositivos** > **Inscripción en Android for Work** > **Configuración de la inscripción de Android for Work**).

De forma predeterminada, la configuración de los dispositivos Android for Work es igual que la configuración de los dispositivos Android. Sin embargo, dejará de ser así tras modificar la configuración de Android for Work.

Si bloquea la inscripción de Android for Work personal, tan solo los dispositivos Android corporativos podrán inscribirse como Android for Work.

Cuando trabaje con la nueva configuración, tenga en cuenta estos puntos:

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Si es la primera vez que incorpora inscripciones de Android for Work

La nueva plataforma Android for Work está bloqueada de manera predeterminada en Restricciones de tipo de dispositivo. Después de incorporar la característica, puede permitir que los dispositivos se inscriban con Android for Work. Para ello, cambie el valor predeterminado o cree una nueva restricción de tipo de dispositivo que sustituya a la predeterminada.

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Si ya ha incorporado inscripciones de Android for Work

Si no es la primera que realiza una incorporación, su situación depende de la configuración elegida:

| Setting | Estado de Android for Work en el valor predeterminado de Restricción de tipo de dispositivo | Notas |
| --- | --- | --- |
| **Administrar todos los dispositivos como Android** | Bloqueado | Todos los dispositivos Android deben inscribirse sin Android for Work. |
| **Administrar los dispositivos compatibles como Android for Work** | Permitido | Todos los dispositivos que admiten Android for Work deben inscribirse con Android for Work. |
| **Administrar los dispositivos compatibles para usuarios solo en estos grupos como Android for Work** | Bloqueado | Para invalidar el valor predeterminado, se creó una directiva de restricción de tipo de dispositivo independiente. Esta directiva define los grupos que se seleccionaron previamente para permitir la inscripción de Android for Work. Los usuarios de los grupos seleccionados seguirán teniendo permiso para inscribir sus dispositivos Android for Work. Todos los demás usuarios tienen restringida la inscripción con Android for Work. |

En todos los casos, se conserva la normativa que haya previsto. No se requiere ninguna acción por su parte para seguir permitiendo Android for Work en su entorno, tanto de forma global como por grupo.

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>Actualización del informe de instalación de aplicaciones para incluir el estado Instalación pendiente <!-- 1249446 -->  

El informe **Estado de instalación de la aplicación**, accesible para todas las aplicaciones a través de la lista **Aplicación** de la carga de trabajo **Aplicaciones móviles**, contiene ahora un recuento **Instalación pendiente** para usuarios y dispositivos.

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API de inventario de aplicaciones iOS 11 para la detección de amenazas en dispositivos móviles <!-- 1391759 -->

Intune recopila la información de inventario de aplicaciones de los dispositivos personales y corporativos, y la pone a disposición de los proveedores de detección de amenazas en dispositivos móviles (MTD), como Lookout for Work. Puede recopilar un inventario de aplicaciones de los usuarios de dispositivos iOS 11 y posteriores.

**Inventario de aplicaciones**  
Los inventarios de los dispositivos iOS 11 y versiones posteriores, tanto de empresa como personales, se envían al proveedor de servicios MTD. El inventario de aplicaciones incluye los datos siguientes:

 - Identificador de la aplicación
 - Versión de la aplicación
 - Nombre corto de la versión
 - Nombre de la aplicación
 - Tamaño del lote de aplicaciones
 - Tamaño dinámico de la aplicación
 - Aplicación validada o no validada
 - Aplicación administrada o no administrada


### <a name="device-management"></a>Administración de dispositivos

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Migración de dispositivos y usuarios de MDM híbrida a Intune independiente <!-- 1463747 wnready -->
Ya hay disponibles nuevos procesos y herramientas para mover usuarios y sus dispositivos de MDM híbrida a Intune en Azure Portal, lo que le permitirá llevar a cabo las tareas siguientes:
- Copiar directivas y perfiles de la consola de Configuration Manager a Intune en Azure Portal
- Mover un subconjunto de usuarios a Intune en Azure Portal conservando el resto en MDM híbrida
- Migrar dispositivos a Intune en Azure Portal sin tener que volver a inscribirlos

Para obtener más información, consulte [Migración de dispositivos y usuarios de MDM híbrida a Intune independiente](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Compatibilidad de alta disponibilidad de On-premises Exchange Connector <!-- 676614 -->
Una vez que el conector de Exchange cree una conexión a Exchange mediante la CAS especificada, el conector tendrá la capacidad de detectar otras CAS. Si la CAS principal deja de estar disponible, el conector efectuará una conmutación por error en otra CAS, si está disponible, hasta que la CAS principal esté disponible. Para obtener más información, consulte [Compatibilidad de alta disponibilidad de On-premises Exchange Connector](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Reinicio remoto de dispositivos iOS (solo supervisado) <!-- 1424595 -->

Con una acción del dispositivo, ahora puede reiniciar un dispositivo supervisado de iOS 10.3 y versiones posteriores. Para obtener más información sobre el uso de la acción de reinicio del dispositivo, consulte [Reinicio remoto de los dispositivos con Intune](device-restart.md).

> [!Note]
> Para usar este comando es necesario que el dispositivo esté supervisado y disponer del derecho de acceso **Bloqueo del dispositivo**. El dispositivo se reinicia inmediatamente. Después de un reinicio, los dispositivos iOS bloqueados mediante código de acceso no volverán a unirse a una red Wi-Fi y es posible que no puedan comunicarse con el servidor.

#### <a name="single-sign-on-support-for-ios----1333645---"></a>Compatibilidad del inicio de sesión único con iOS <!-- 1333645 -->  

En el caso de los usuarios de iOS, puede usar el inicio de sesión único. Las aplicaciones de iOS que están codificadas para buscar las credenciales de usuario en la carga de inicio de sesión único funcionarán con esta actualización de la configuración de carga. También puede utilizar el UPN y el identificador de dispositivo de Intune para configurar el nombre de la entidad de seguridad y el dominio Kerberos. Para obtener más información, consulte [Configuración del inicio de sesión único de Intune para dispositivos iOS](sso-ios.md).

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Agregar "Buscar mi iPhone" para dispositivos personales <!--1427287-->
Ahora puede ver si los dispositivos iOS tienen activado el Boqueo de activación. Esta característica se encontraba anteriormente en Intune, en el portal clásico.


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloqueo remoto de los dispositivos macOS administrados con Intune <!-- 1437691 -->

Si pierde un dispositivo macOS, puede bloquearlo y establecer un PIN de recuperación de seis dígitos. Una vez bloqueado, la hoja de **información general del dispositivo** muestra el PIN hasta que se envía otra acción de dispositivo.

Para obtener más información, consulte [Bloqueo remoto de los dispositivos administrados con Intune](device-remote-lock.md).

#### <a name="new-scep-profile-details-supported----1559808---"></a>Nuevos detalles admitidos del perfil SCEP <!-- 1559808 -->

Ahora los administradores pueden establecer configuraciones adicionales al crear un perfil de SCEP en las plataformas Windows, iOS, macOS y Android.  Los administradores pueden establecer el IMEI, el número de serie o el nombre común, incluido el correo electrónico en el formato de nombre de sujeto.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>Conservar los datos durante un restablecimiento de fábrica <!--1588489 -->
Al restablecer la versión 1709 de Windows 10 y versiones posteriores a la configuración de fábrica, está disponible una nueva funcionalidad. Los administradores pueden especificar si la inscripción de dispositivos y otros datos aprovisionados se conservan en un dispositivo tras un restablecimiento de fábrica.

Los siguientes datos se conservan tras un restablecimiento de fábrica:
- Cuentas de usuario asociadas con el dispositivo
- Estado del equipo (unión a un dominio, unido a Azure Active Directory)
- Inscripción de MDM
- Aplicaciones instaladas por OEM (aplicaciones de Win32 y tienda)
- Perfil de usuario
- Datos de usuario fuera del perfil de usuario
- Inicio de sesión automático del usuario

Los datos siguientes no se conservan:
- Archivos de usuario
- Aplicaciones instaladas por el usuario (aplicaciones de Win32 y tienda)
- Configuración del dispositivo no predeterminada

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Se muestran las asignaciones del círculo de actualizaciones de Windows 10 <!-- 1621837 -->
Cuando esté **solucionando problemas**, y en relación al usuario que está visualizando, puede ver las asignaciones de círculos de actualizaciones de Windows 10.  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Configuración de la frecuencia de informes de Protección contra amenazas avanzada de Windows Defender <!-- 1455974  -->
El servicio Protección contra amenazas avanzada de Windows Defender (WDATP) permite a los administradores gestionar la frecuencia con la que se generan informes relativos a los dispositivos administrados. Con la nueva opción **Frecuencia de informes de telemetría urgentes**, WDATP recopila datos y evalúa los riesgos con una frecuencia mayor. El valor predeterminado para los informes optimiza el rendimiento y la velocidad. Aumentar la frecuencia de los informes puede ser muy útil para dispositivos de alto riesgo. Esta configuración puede encontrarse en el perfil **ATP de Windows Defender** en **Configuraciones de dispositivos**.

#### <a name="audit-updates----1412961---"></a>Actualizaciones de auditoría <!-- 1412961 -->  
La auditoría de Intune proporciona un registro de las operaciones que implican cambios en Intune.  Todas las operaciones de creación, actualización, eliminación y tareas remotas se registran y se conservan durante un año.  Azure Portal proporciona una vista filtrable de los datos auditados durante los últimos 30 días en cada carga de trabajo.  Con la correspondiente API de Graph es posible recuperar los datos de auditoría almacenados durante el último año.

La auditoría se encuentra en el grupo **MONITOR**. El elemento de menú **Registros de auditoría** está disponible para cada una de las carga de trabajo.




## <a name="week-of-november-20-2017"></a>Semana del 20 de noviembre de 2017

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="google-play-protect-support-on-android----908720---"></a>Compatibilidad con Google Play Protect en Android <!-- 908720 -->

Con el lanzamiento de Android Oreo, Google presenta un conjunto de características de seguridad denominado Google Play Protect que permite a los usuarios y las organizaciones ejecutar aplicaciones e imágenes de Android seguras. Intune ya admite las características de Google Play Protect, incluida la atestación remota de SafetyNet. Los administradores pueden establecer requisitos para directivas de cumplimiento que exijan que Google Play Protect esté configurado y en buen estado.
La opción **SafetyNet device attestation** (Atestación de dispositivo SafetyNet) requiere que el dispositivo se conecte con un servicio de Google para comprobar que se encuentra en buen estado y no está en riesgo. Los administradores también pueden establecer una opción en el perfil de configuración de Android for Work para requerir que se comprueben las aplicaciones instaladas por los servicios de Google Play. Si un dispositivo no es compatible con los requisitos de Google Play Protect, el acceso condicional puede impedir que los usuarios accedan a los recursos corporativos.

- Obtenga información sobre la [Creación de una directiva de cumplimiento de dispositivos para habilitar Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocolo de texto permitido en aplicaciones administradas <!-- 1414050  -->

Las aplicaciones administradas por Intune App SDK pueden enviar mensajes SMS.

## <a name="week-of-november-13-2017"></a>Semana del 13 de noviembre de 2017

### <a name="intune-apps"></a>Aplicaciones de Intune
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>Aplicación Portal de empresa ya disponible para macOS <!--1541700-->
La aplicación Portal de empresa de Intune para macOS presenta una experiencia actualizada, ya que se ha optimizado para mostrar correctamente toda la información y las notificaciones de conformidad que los usuarios necesitan para los dispositivos que hayan inscrito. Además, una vez que Portal de empresa se haya implementado en un dispositivo, las actualizaciones se proporcionarán a través de Microsoft AutoUpdate para macOS. Para descargar la nueva aplicación, inicie sesión en el sitio web de Portal de empresa de Intune desde un dispositivo macOS.

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Inclusión de Microsoft Planner en la lista de aplicaciones aprobadas para la administración de aplicaciones móviles (MAM) <!-- 1248473 -->
La aplicación Microsoft Planner para iOS y Android ahora está incluida entre las aplicaciones aprobadas para la administración de dispositivos móviles (MAM). La aplicación puede configurarse para todos los inquilinos mediante la hoja Intune App Protection de Azure Portal.
- Para obtener más información, consulte la [lista de aplicaciones aprobadas para MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Frecuencia de actualización de requisitos de VPN por aplicación en dispositivos iOS <!-- 1547061 -->  
En el caso de las aplicaciones en dispositivos iOS, los administradores ahora pueden quitar los requisitos de VPN por aplicación. Los dispositivos afectados se actualizarán tras la siguiente validación de Intune, que por lo general se produce cada 15 minutos.  

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Compatibilidad con el módulo de administración de System Center Operations Manager para Exchange Connector <!-- 885457 -->
El módulo de administración de System Center Operations Manager (SCOM) para Exchange Connector ya está disponible para ayudarle a analizar los registros de Exchange Connector. Esta característica ofrece distintas maneras de supervisar el servicio cuando haya que resolver problemas.

## <a name="week-of-november-6-2017"></a>Semana del 6 de noviembre de 2017

### <a name="device-enrollment"></a>Inscripción de dispositivos
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Administración conjunta para dispositivos de Windows 10 <!-- 1243445 -->
La administración conjunta es una solución que sirve para ofrecer un vínculo entre la administración tradicional y la administración moderna. Además, le proporciona una guía para llevar a cabo la transición con un enfoque por fases. Básicamente, la administración conjunta es una solución en la que los dispositivos de Windows 10 se administran de forma simultánea mediante Configuration Manager y Microsoft Intune. También se unen a Active Directory (AD) y a Azure Active Directory (Azure AD).  Esta configuración proporciona un método para poder modernizar la administración con el tiempo, a la velocidad que sea adecuada para su organización si no puede moverlo todo a la vez.  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Restricción de la inscripción de Windows según la versión del sistema operativo <!-- 245498 -->
Como administrador de Intune, ahora puede especificar una versión mínima y máxima de Windows 10 para poder inscribir dispositivos. Estas restricciones se pueden establecer en la hoja **Configuraciones de plataforma**.

Intune seguirá permitiendo la inscripción de teléfonos y equipos con Windows 8.1, pero solo se pueden establecer los límites mínimo y máximo de las versiones de Windows 10. Para permitir la inscripción de dispositivos 8.1, deje vacío el límite mínimo.

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Alertas de dispositivos sin asignar de Windows AutoPilot <!-- 1631236 -->
Hay una nueva alerta disponible relativa a los dispositivos sin asignar de Windows AutoPilot en la página **Microsoft Intune** > **Inscripción de dispositivos** > **Información general**. Esta alerta indica cuántos dispositivos del programa AutoPilot no tienen asignados perfiles de implementación de AutoPilot. Use la información provista en la alerta para crear perfiles y asignarlos a los dispositivos sin asignar. Al hacer clic en la alerta, verá una lista completa de dispositivos de Windows AutoPilot e información detallada sobre ellos. Para obtener más información, vea [Inscribir dispositivos mediante el programa Windows AutoPilot Deployment](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="device-management"></a>Administración de dispositivos

#### <a name="refresh-button-for-devices-list-------1333581---"></a>Botón Actualizar de la lista de dispositivos    <!-- 1333581 -->
La lista de dispositivos no se actualiza automáticamente, de modo que puede usar el nuevo botón Actualizar para actualizar los dispositivos que figuran en esa lista.

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Compatibilidad con la entidad de certificación (CA) en la nube de Symantec <!-- 1333638 -->    
Intune admite ahora la entidad de certificación en la nube de Symantec, que permite que Intune Certificate Connector emita certificados PKCS desde la entidad de certificación en la nube de Symantec para dispositivos administrados por Intune. Si ya usa Intune Certificate Connector con la entidad de certificación de Microsoft, puede usar la configuración existente de Intune Certificate Connector para agregar compatibilidad con la entidad de certificación de Symantec.

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>Nuevos elementos agregados al inventario de dispositivos   <!--1404455 -->
Los nuevos elementos que se indican a continuación ya están disponibles en el [inventario de los dispositivos inscritos](device-inventory.md):

- Dirección MAC de Wi-Fi
- Espacio de almacenamiento total
- Espacio disponible total
- MEID
- Operador del suscriptor


### <a name="app-management"></a>Administración de aplicaciones
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Establecimiento del acceso para las aplicaciones mediante una revisión de seguridad mínima de Android en el dispositivo <!-- 1278463 -->   
Un administrador puede definir la revisión de seguridad mínima de Android que debe estar instalada en el dispositivo para poder obtener acceso a una aplicación administrada en una cuenta administrada.

> [!Note]  
> Esta característica solamente restringe las revisiones de seguridad publicadas por Google en dispositivos Android 6.0 y versiones posteriores.

#### <a name="app-conditional-launch-support----1193313---"></a>Compatibilidad con inicio condicional de aplicación <!-- 1193313 -->
Los administradores de TI ahora pueden establecer un requisito a través del portal de administración de Azure para exigir un código de acceso en lugar de un PIN numérico mediante la administración de aplicaciones móviles (MAM) cuando se inicia la aplicación. Si se configura, se le pide al usuario que establezca y use un código de acceso cuando se le solicite antes de obtener acceso a aplicaciones habilitadas para MAM. Un código de acceso se define como un PIN numérico con al menos un carácter especial o un carácter alfabético en mayúsculas/minúsculas. Esta versión de Intune habilitará esta característica **solo en iOS**. Intune admite un código de acceso de forma similar al PIN numérico. Establece una longitud mínima y permite la repetición de caracteres y secuencias. Esta característica requiere el uso de ciertas aplicaciones (es decir, WXP, Outlook, Managed Browser o Yammer) para integrar Intune App SDK con el código de esta y aplicar la configuración del código de acceso en las aplicaciones de destino.

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Número de versión de la aplicación para línea de negocio en el informe de estado de instalación del dispositivo <!-- 1233999 -->
Con esta versión, el informe de estado de instalación del dispositivo mostrará el número de versión de aplicación de las aplicaciones de línea de negocio para iOS y Android. Puede usar esta información para solucionar problemas de las aplicaciones o buscar los dispositivos que ejecuten versiones obsoletas de la aplicación.


### <a name="device-configuration"></a>Configuración de los dispositivos
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Los administradores ya pueden configurar las opciones del firewall en un dispositivo mediante un perfil de configuración de dispositivo <!-- 951708 -->   
Los administradores pueden activar el firewall para los dispositivos y, además, configurar varios protocolos para redes públicas, privadas y de dominio.  Esta configuración del firewall se encuentra en el perfil "Endpoint Protection".

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>La Protección de aplicaciones de Windows Defender ayuda a proteger los dispositivos de sitios web que no son de confianza, en función de la definición de la organización <!-- 958257 -->   
Los administradores pueden definir sitios como "de confianza" o "corporativos" mediante un flujo de trabajo de Windows Information Protection o el nuevo perfil de "límite de red" en las configuraciones del dispositivo. Si se visualizan con Microsoft Edge, todos los sitios que no aparezcan en un límite de red de confianza de un dispositivo de Windows 10 de 64 bits se abrirán en un explorador de un equipo virtual de Hyper-V.

La Protección de aplicaciones se encuentra en los perfiles de configuración del dispositivo, en el perfil "Endpoint Protection". Desde allí, los administradores pueden configurar la interacción entre el explorador virtualizado y el equipo host, los sitios que son y que no son de confianza, y el almacenamiento de datos generado en el explorador virtualizado. Para usar la Protección de aplicaciones en un dispositivo, debe configurarse primero un límite de red. Es importante definir un solo límite de red para un dispositivo.  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows Defender Application Control en Windows 10 Enterprise ofrece el modo de confiar solo en aplicaciones autorizadas <!-- 1031096 -->    
Teniendo en cuenta que cada día se crean miles de archivos malintencionados, el uso de la detección antivirus basada en firma para luchar contra el malware podría ser insuficiente para proporcionar una defensa adecuada contra nuevos ataques. Mediante Windows Defender Application Control en Windows 10 Enterprise, puede cambiar la configuración del dispositivo de un modo en el que las aplicaciones son de confianza a menos que las bloquee un antivirus u otra solución de seguridad, a un modo en el que el sistema operativo solo confía en las aplicaciones autorizadas por la empresa. La confianza se asigna a las aplicaciones en Windows Defender Application Control.

Mediante Intune, puede configurar las directivas de control de aplicaciones en modo de "solo auditoría" o en el modo de uso forzoso. Las aplicaciones no se bloquean cuando se ejecutan en modo de "solo auditoría". El modo de "solo auditoría" registra todos los eventos en registros del cliente local. También puede configurar si solo se pueden ejecutar componentes de Windows y aplicaciones de Microsoft Store, o si también se pueden ejecutar otras aplicaciones con buena reputación de acuerdo con la definición de Intelligent Security Graph.

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>La Protección contra vulnerabilidades de seguridad de Windows Defender es un nuevo conjunto de funciones de prevención de intrusiones para Windows 10 <!-- 1063615 -->   
La Protección contra vulnerabilidades de seguridad de Windows Defender incluye reglas personalizadas para reducir la explotabilidad de las aplicaciones. También impide las amenazas de macros y scripts, bloquea automáticamente las conexiones de red a direcciones IP de mala reputación y puede proteger los datos contra el ransomware y amenazas desconocidas. La Protección contra vulnerabilidades de seguridad de Windows Defender consta de los componentes siguientes:

- La **reducción de la superficie expuesta a ataques (ASR)** proporciona reglas que permiten impedir las amenazas de macros, scripts y correos electrónicos.
- El **acceso controlado a carpetas** bloquea automáticamente el acceso a contenido en las carpetas protegidas.
- El **filtro de red** bloquea las conexiones salientes desde cualquier aplicación a IP o dominios de mala reputación.
- La **protección contra vulnerabilidades** proporciona restricciones de memoria, flujo de control y directivas que pueden usarse para proteger una aplicación contra las vulnerabilidades.


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Administrar scripts de PowerShell en Intune para dispositivos Windows 10 <!-- 790537 -->

La extensión de administración de Intune permite cargar los scripts de PowerShell en Intune para ejecutarse en dispositivos Windows 10. Esta extensión complementa las capacidades de administración de dispositivos móviles (MDM) de Windows 10 y facilita la transición a una administración moderna. Para conocer más detalles, vea [Administrar scripts de PowerShell en Intune para dispositivos Windows 10](intune-management-extension.md).

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Nueva configuración de restricciones de dispositivos para Windows 10 <!-- 1308850 -->
-    Mensajería (solo móvil): deshabilitar pruebas o mensajes MMS
-    Contraseña: configuración para habilitar FIPS y el uso de dispositivos secundarios Windows Hello para la autenticación 
-    Pantalla: configuración para activar o desactivar el ajuste de escala de GDI para las aplicaciones heredadas

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Restricciones de dispositivos Windows 10 a pantalla completa <!-- 1308872 -->   
Puede restringir usuarios de dispositivos Windows 10 a pantalla completa, lo que les limita a un conjunto de aplicaciones predefinidas.  Para ello, cree un perfil de restricción de dispositivo Windows 10 y defina la configuración de pantalla completa.

La pantalla completa admite dos modos: **aplicación única**, que permite que un usuario ejecute una sola aplicación, o **varias aplicaciones**, que permite el acceso a un conjunto de aplicaciones.  Para determinar las aplicaciones compatibles, debe definir la cuenta de usuario y el nombre del dispositivo.  Cuando el usuario ha iniciado sesión, verá únicamente las aplicaciones definidas.  Para obtener más información, vea [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) (CSP AssignedAccess). 

La pantalla completa requiere lo siguiente:

- Intune debe ser la entidad de MDM.
- Las aplicaciones deben estar ya instaladas en el dispositivo de destino.
- El dispositivo debe estar [aprovisionado correctamente](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Nuevo perfil de configuración de dispositivo para crear límites de red <!-- 1311967 -->   
En los otros perfiles de configuración de dispositivo encontrará un nuevo perfil de configuración de dispositivo llamado **Límite de red**. Use este perfil para definir los recursos en línea que quiere que se consideren corporativos y de confianza. Debe definir un límite de red para un dispositivo *antes* de que en el dispositivo se puedan usar características como la Protección de aplicaciones de Windows Defender y Windows Information Protection. Es importante definir un solo límite de red para cada dispositivo.

Puede definir los recursos de empresa en la nube, los intervalos de direcciones IP y los servidores proxy internos que quiere que se consideren de confianza. Una vez definidos, pueden usar el límite de red otras características como la Protección de aplicaciones de Windows Defender y Windows Information Protection.

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Dos opciones de configuración adicionales para Antivirus de Windows Defender <!-- 1338409 -->  
**Nivel de bloqueo de archivos**

| | |
|---|---|
| No configurado | **No configurado** usa el nivel de bloqueo predeterminado de Antivirus de Windows Defender y proporciona una detección segura sin aumentar el riesgo de detectar archivos legítimos. |
| Alto | **Alto** se aplica a un alto nivel de detección.
| Alto +  | **Alto +** proporciona el nivel Alto con medidas de protección adicionales que podrían afectar al rendimiento del cliente.
| Tolerancia cero  | **Tolerancia cero** bloquea todos los ejecutables desconocidos. |

Aunque es improbable, si se establece en **Alto** puede hacer que se detecten algunos archivos legítimos.
Se recomienda establecer el nivel de bloqueo de archivos en el valor predeterminado (**No configurado**).

**Ampliación del tiempo de espera para la detección de archivos en la nube**  

| | |
|--|--|
| Número de segundos (0-50) | Especifique el tiempo máximo durante el que Antivirus de Windows Defender debe bloquear un archivo mientras espera un resultado de la nube. El valor predeterminado es de 10 segundos. El tiempo adicional que se especifique aquí (hasta 50 segundos) se agregará a los 10 segundos. En la mayoría de los casos, la detección tarda mucho menos que el tiempo máximo. Si amplía el tiempo, permitirá que la nube investigue a fondo los archivos sospechosos. Se recomienda que habilite esta opción y que especifique al menos 20 segundos adicionales. |

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Adición de la VPN de Citrix a dispositivos Windows 10 <!-- 1512457 -->  
Puede configurar la VPN de Citrix para sus dispositivos Windows 10. Puede elegir la VPN de Citrix en la lista *Seleccione un tipo de conexión* en la hoja **VPN base** al configurar una VPN para Windows 10 y versiones posteriores.

> [!Note]
> La configuración de Citrix ya existía para iOS y Android.

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Las conexiones Wi-Fi admiten claves precompartidas en iOS <!-- 1550823 -->
Los clientes pueden configurar perfiles de Wi-Fi para usar claves precompartidas (PSK) en las conexiones WPA o WPA2 Personal en dispositivos iOS. Estos perfiles se insertan en el dispositivo del usuario al inscribirlo en Intune.

Cuando el perfil se haya insertado en el dispositivo, el siguiente paso dependerá de la configuración del perfil.  Si está establecido para conectarse automáticamente, lo hace cuando la red se necesite.  Cuando el perfil se conecta de forma manual, el usuario deberá activar manualmente la conexión.  

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Acceso a los registros de aplicación administrada de iOS <!-- 1469920 -->
Ahora, los usuarios finales que tengan Managed Browser instalado pueden ver el estado de administración de todas las aplicaciones publicadas de Microsoft, así como enviar registros para solucionar problemas con sus aplicaciones iOS administradas.

Para más información sobre cómo habilitar el modo de solución de problemas en Managed Browser en un dispositivo iOS, vea [Cómo tener acceso a los registros de aplicación administrada con Managed Browser en iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Mejoras en el flujo de trabajo de configuración de dispositivos en la versión 2.9.0 de Portal de empresa para iOS <!-- 1417174 -->

El flujo de trabajo de configuración de dispositivos se ha mejorado en la aplicación Portal de empresa para iOS. El lenguaje ahora es más fácil de entender, y también hemos combinado las pantallas que hemos podido. Además, hemos utilizado el nombre de su empresa en el texto del proceso de configuración para que el lenguaje sea más específico. Puede consultar el flujo de trabajo actualizado en la  [página de novedades de la interfaz de usuario de la aplicación](whats-new-app-ui.md).

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>La entidad de usuario contiene los datos de usuario más recientes en el modelo de datos de Almacenamiento de datos <!-- 1544273 -->
La primera versión del modelo de datos del Almacenamiento de datos de Intune solo contenía datos de Intune recientes e históricos. Los creadores de informes no podían capturar el estado actual de un usuario. En esta actualización, la **entidad de usuario** se rellena con los datos más recientes del usuario.


## <a name="notices"></a>Notificaciones

### <a name="plan-for-change-update-where-you-configure-your-app-protection-policies"></a>Plan de cambio: actualización de la ubicación en la que se configuran las directivas de protección de aplicaciones

A partir de marzo de 2018, le redirigiremos de forma temporal de la hoja de servicio de Intune App Protection a la hoja de aplicación móvil de Intune, ambas hojas disponibles en Azure Portal. Debe tener en cuenta que todas las directivas de protección de aplicaciones ya se encuentran en la hoja de aplicación móvil de Intune, en la configuración de aplicaciones. En lugar de acceder a Intune App Protection, se dirigirá a Intune. En abril, se retirará el redireccionamiento y se eliminará por completo la hoja de servicio de Intune App Protection, ya que también se duplica lo que se ha integrado en Intune. 

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Este cambio afectará tanto a los clientes de la versión independiente de Intune como a los de la versión híbrida (Intune con Configuration Manager). Esta integración le permitirá simplificar la administración en la nube. De esta forma, solo tendrá que acceder a una hoja en Azure, la de Intune, para administrar grupos, directivas, aplicaciones y dispositivos móviles.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Etiquete Intune como favorito en lugar de la hoja de servicio de Intune App Protection y familiarícese con el flujo de trabajo de directivas de protección de aplicaciones de la hoja de aplicación móvil que hay en Intune. Proporcionaremos el redireccionamiento durante un breve período de tiempo y, después, eliminaremos la hoja de protección de aplicaciones. Recuerde que todas las directivas de protección de aplicaciones se han quitado de Intune y que puede modificar las directivas de acceso condicional mediante la documentación que encontrará en [https://aka.ms/azuread_ca](https://aka.ms/azuread_ca).

**Información adicional**: [https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="updated-new-security-enhancements-in-the-intune-service-----1637539---"></a>Actualizado: nuevas mejoras de seguridad en el servicio de Intune <!-- 1637539 -->   

Implementaremos mejoras de seguridad en el servicio de Intune. Como parte de este cambio, con la actualización de marzo aplicada al servicio de Intune, dispondrá de un botón de alternancia en la consola de Azure de Intune para activar y desactivar esta característica de seguridad. Cuando esté activada, los dispositivos que no tengan ninguna directiva de cumplimiento asignada se marcarán como no conformes.

**Clientes de la versión híbrida**: de momento no incorporaremos este cambio para los clientes de la versión híbrida. No es necesario hacer nada. Sin embargo, le recomendamos encarecidamente que se asegure de que los dispositivos tengan, como mínimo, una directiva de cumplimiento asignada.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?

Cuando empecemos a implementar este cambio en la actualización de marzo, esta característica le afectará de forma distinta en función de si tiene o no asignadas directivas de cumplimiento.

- Si utiliza un inquilino nuevo o existente y no tiene ninguna directiva de cumplimiento asignada a sus dispositivos, el botón de alternancia se establecerá automáticamente en **Conforme**. De forma predeterminada, la característica estará desactivada en la consola. Los usuarios finales no se verán afectados.
- Si utiliza un inquilino existente y tiene algún dispositivo con una directiva de cumplimiento asignada, el botón de alternancia se establecerá automáticamente en "No conforme". Cuando se implemente la actualización de marzo, esta característica estará activada de forma predeterminada. 

Si utiliza directivas de cumplimiento con acceso condicional (CA) y tiene la característica activada, los dispositivos que no tengan asignada como mínimo una directiva de cumplimiento se bloquearán mediante el acceso condicional. Los usuarios finales que estén asociados a estos dispositivos y a los que se haya concedido acceso previamente al correo electrónico perderán el acceso a menos que usted asigne como mínimo una directiva de cumplimiento a todos los dispositivos.   
 
#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?  

Si utiliza el acceso condicional, le recomendamos que tenga esta característica activada y que deje el botón de alternancia establecido en **No conforme**. Para que sus usuarios finales no pierdan el acceso al correo electrónico, debe asegurarse de que todos los dispositivos tienen asignada al menos una directiva de cumplimiento. A continuación se muestran algunos de los cambios que hemos aplicado para ayudarle a hacerlo:   

- Hemos incorporado un informe llamado **Dispositivos sin directiva de cumplimiento** en el portal de Intune que puede usar para identificar todos los dispositivos de su entorno que no tengan ninguna directiva de cumplimiento asignada. 
- Existe la opción **Todos los usuarios** para que resulte fácil asignar una directiva de cumplimiento a todos los usuarios.

Si opta por dejar el botón de alternancia desactivado, no es necesario que haga nada más.

**Información adicional**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Plan de cambio: cambio en la compatibilidad con el complemento de Microsoft Intune App SDK Cordova
La compatibilidad de Intune con el [complemento de Microsoft Intune App SDK Cordova](app-sdk-cordova.md) finalizará el 1 de mayo de 2018. Le recomendamos que utilice la herramienta de ajuste de aplicaciones de Intune para preparar sus aplicaciones basadas en Cordova para que estén disponibles y sean más fáciles de utilizar en Intune. Cuando este cambio surta efecto, ya no se ofrecerán actualizaciones ni soporte técnico para el complemento de Microsoft Intune App SDK Cordova. Los desarrolladores de aplicaciones no podrán usar este complemento. Está previsto que Intune siga admitiendo aplicaciones creadas con Cordova. Sin embargo, las aplicaciones creadas con el complemento de Microsoft Intune App SDK Cordova verán reducida su funcionalidad en Intune. Después de ajustar las aplicaciones con la herramienta de ajuste de aplicaciones de Intune, las aplicaciones se pueden implementar para los usuarios finales como lo haría normalmente. En el caso de aplicaciones Android basadas en Cordova que se publiquen en Google Play Store:
- La primera vez que las utilicen, los usuarios finales deberán proporcionar sus credenciales para recibir la directiva de Intune.
- Las aplicaciones deben publicarse en la tienda de aplicaciones y destinarse a usuarios de Intune, por ejemplo, "Aplicación Contoso para Intune". 

Para obtener más información sobre la herramienta de ajuste de aplicaciones, consulte información sobre la [herramienta de ajuste de aplicaciones para iOS](app-wrapper-prepare-ios.md) o la [herramienta de ajuste de aplicaciones para Android](app-wrapper-prepare-android.md). Si tiene algún problema o alguna pregunta, póngase en contacto con [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com). 

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Plan de cambio: use Intune en Azure ahora para la administración de MDM<!-- 1227338 -->
Hace más de un año anunciamos una [versión preliminar pública de Intune en Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) y hace seis meses seguimos con la [disponibilidad general de la nueva experiencia de administración](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) para Intune. A partir del 2 de abril de 2018 se desactivará la administración de dispositivos móviles (MDM) en la consola de Silverlight clásica para los clientes que usan Intune de forma independiente. En su lugar, puede usar [Intune en Azure](https://aka.ms/Intune_on_Azure) para cubrir sus necesidades de MDM. Si todavía usa la consola clásica de MDM, deje de hacerlo y familiarícese con Intune en Azure. No se espera que este cambio afecte de ningún modo a los usuarios finales. La administración de PC clásica permanecerá en Silverlight. Puede obtener más información sobre este cambio y cómo le afecta [aquí](https://aka.ms/Intune_on_Azure_mdm).


### <a name="plan-for-change-easy-assist-end-of-life----1556480---"></a>Plan de cambio: final de ciclo de vida de Easy Assist <!-- 1556480 -->
Intune usa Microsoft Easy Assist para la asistencia remota de administración de PC. Algo que quizá no sepa es que Microsoft Easy Assist es un componente de Office Live Meeting, un servicio que quedó en desuso el 31 de diciembre de 2017. Por lo tanto, Easy Assist de Intune dejará también de ofrecerse el 31 de diciembre de 2017.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Administración independiente de dispositivos Android for Work y dispositivos Android <!-- 1490731 EEready-->    
**Nota**: Los cambios siguientes empezarán a implementarse con la actualización de noviembre, pero es posible que se tarde un tiempo en ejecutarse en su cuenta. Cuando estos cambios entren en vigor en su cuenta, recibirá una notificación de confirmación en el portal de Office 365. Después de la implementación, tendrá opciones adicionales de capacidad de administración. No habrá ningún cambio en la experiencia del usuario final durante la implementación.

Intune admite la administración de inscripciones de dispositivos Android for Work independientemente de la plataforma Android. Esta configuración se administra en **Inscripción de dispositivos** > **Restricciones de inscripción** > **Restricciones de tipo de dispositivo**. (Anteriormente se encontraban bajo **Inscripción de dispositivos** > **Inscripción en Android for Work** > **Configuración de la inscripción de Android for Work**).

De forma predeterminada, la configuración de los dispositivos Android for Work será igual que la configuración de los dispositivos Android. Sin embargo, dejará de ser así tras modificar la configuración de Android for Work.

Si bloquea la inscripción de Android for Work personal, tan solo los dispositivos Android corporativos podrán inscribirse como Android for Work.

Cuando trabaje con la nueva configuración, tenga en cuenta estos puntos:

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

### <a name="deprecating-support-for-os-x-mavericks-1010-and-previous-versions-of-macos---1489263-plan-for-change-for-1802--"></a>Se está poniendo en desuso el soporte técnico de OS X Mavericks 10.10 y versiones anteriores de macOS <!--1489263, plan for change for 1802-->
A partir de febrero de 2018, la inscripción de dispositivos con OS X Yosemite 10.10 y versiones anteriores de macOS dejará de estar disponible. Intune es totalmente compatible con OS X El Capitan 10.11 y otras versiones más recientes.

### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Nueva ruta de acceso para los dispositivos administrados en Graph API <!-- 1586728 -->
Se cambiará la ruta de acceso que se usa para acceder a los dispositivos administrados en la versión beta de Graph API. 

| | |
|--|--|
| Ruta de acceso actual |  https://graph.microsoft.com/beta/managedDevices |
| Nueva ruta de acceso | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

Ambas rutas de acceso funcionarán durante el mes de octubre. Después de la versión del servicio de octubre, solo funcionará la nueva ruta de acceso.  Si usa Graph API para acceder a los dispositivos administrados, actualice y compruebe los scripts y las aplicaciones con la nueva ruta de acceso. Para conocer otros cambios, consulte el [registro de cambios mensual de Graph API](https://developer.microsoft.com/graph/docs/concepts/changelog).


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->
Para las cuentas de Intune creadas después de enero de 2017, Intune habilitó el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en Azure Portal. Anteriormente, la vista preliminar de inscripción de Apple solo era accesible desde los vínculos del portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requieren una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero la información estará disponible tan pronto como sea posible. Si su cuenta existente no puede acceder a Azure Portal, le recomendamos encarecidamente que cree una cuenta de prueba para probar la nueva experiencia.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Roles de administración que se reemplazan en el Portal de Azure
Los roles de administración de aplicaciones móviles (MAM) existentes (colaborador, propietario y de solo lectura) usados en el portal clásico de Intune (Silverlight) se reemplazan por un conjunto completo de nuevos controles de administración basada en roles (RBAC) en el Portal de Intune Azure. Cuando haya migrado a Azure Portal, tendrá que reasignar estos nuevos roles de administración a los administradores. Para obtener más información sobre RBAC y los nuevos roles, vea [Roles de Intune (RBAC) para Microsoft Intune](/intune/role-based-access-control).

## <a name="whats-coming"></a>Próximas novedades

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Actualización de la experiencia del usuario en la aplicación del Portal de empresa para iOS <!--1412866-->

Lanzaremos una actualización importante de la experiencia de usuario para la aplicación del Portal de empresa para iOS. La actualización contará con un cambio de diseño visual completo, que incluye una apariencia y aspecto modernizados con mayor facilidad de uso y accesibilidad. Se mantendrán todas las funcionalidades del Portal de empresa de iOS actuales.

Ofrecemos una versión preliminar de la aplicación del Portal de empresa actualizada para iOS a través del programa TestFlight de Apple para que la use y nos envíe sus comentarios. Regístrese en https://aka.ms/intune_ios_cp_testflight para obtener acceso a TestFlight.

### <a name="conditional-access-policies-for-intune-will-only-be-available-from-the-azure-portal-----1737088---"></a>Directivas de acceso condicional de Intune solo disponibles en Azure Portal <!-- 1737088 -->
Se ha simplificado la ubicación en la que se configura y administra el acceso condicional. En estos momentos, puede administrar el acceso condicional en la hoja de Intune App Protection (MAM) y en la experiencia clásica de Azure AD, en [Microsoft Azure Portal](https://manage.windowsazure.com). A partir de enero, solo podrá configurar y administrar sus directivas en [Azure Portal](https://portal.azure.com), en **Azure Active Directory** > **Acceso condicional**. Para su comodidad, también puede acceder a esta hoja desde Intune, en Azure Portal, en **Intune** > **Acceso condicional**.

### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747--"></a>Administración de dispositivos macOS inscritos en Jamf con el motor conformidad de dispositivos de Intune <!--1592747-->
A partir de principios de 2018, Jamf enviará la información del estado del dispositivo macOS a Intune, y este a continuación evaluará su conformidad con las directivas definidas en la consola de Intune. En función del estado de conformidad del dispositivo, así como otras condiciones tales como la ubicación, el riesgo del usuario, etc., el acceso condicional aplicará la conformidad para los dispositivos macOS que accedan a la nube y a aplicaciones locales conectadas a Azure AD, incluido Office 365.

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Cambios en la compatibilidad de la aplicación de portal de empresa de iOS de Intune <!-- 1164474  -->
Próximamente, habrá una nueva versión de la aplicación de portal de empresa de Microsoft Intune para iOS que solo admitirá dispositivos que ejecuten iOS 9.0 o posterior. La versión de Portal de empresa que admite iOS 8 todavía estará disponible durante un breve período de tiempo. En cambio, si también usa aplicaciones iOS habilitadas para MAM, se admiten iOS 9.0 y versiones posteriores, por lo que es recomendable que se asegure de que sus usuarios finales actualicen al sistema operativo más reciente. 

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Le informamos de esto con antelación, incluso cuando no tenemos fechas específicas, para que tenga tiempo para planear. Asegúrese de que sus usuarios hayan actualizado a iOS 9 o versiones posteriores y, cuando se publique la aplicación Portal de empresa, solicite a sus usuarios finales que la actualicen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Anime a los usuarios a que actualicen a iOS 9.0 o posterior para aprovechar las nuevas características de Intune.  Anime a los usuarios a que instalen la última versión del portal de empresa y se aprovechen de las nuevas características que ofrecerá.

Vaya a Intune en Azure Portal y vea Dispositivos > Todos los dispositivos y filtre por la versión de iOS para ver cualquier dispositivo actual con sistemas operativos anteriores a iOS 9.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->
Apple ha anunciado que se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS.

Hay disponible una versión de la aplicación Portal de empresa para iOS a través del programa Apple TestFlight que aplica los nuevos requisitos de ATS. Si desea probarla para que pueda experimentar el cumplimiento de ATS, envíe un correo electrónico a <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> con su nombre, apellidos, dirección de correo electrónico y nombre de la empresa. Visite nuestro [blog de soporte técnico de Intune](https://aka.ms/compportalats) para obtener más información.

## <a name="see-also"></a>Vea también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades de la interfaz de usuario del portal de empresa](whats-new-app-ui.md)
* [Novedades de los meses anteriores](whats-new-archive.md)
