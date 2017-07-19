---
title: Novedades de Microsoft Intune
titleSuffix: Intune on Azure
description: Descubra las novedades del portal de Intune Azure
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 07/03/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fdda99bfd72c71d36a19449d43bc6cbf6a00babe
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Novedades de Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Conozca las novedades semanales de Microsoft Intune. También podrá obtener información sobre los [próximos cambios](#whats-coming), [notificaciones importantes](#notices) sobre el servicio e información sobre las [versiones anteriores](whats-new-archive.md).

> [!Note]
> Muchas de estas características finalmente serán compatibles con las implementaciones híbridas con Configuration Manager. Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Role-based access control
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
-->   



## <a name="week-of-june-26th-2017"></a>Semana del 26 de junio de 2017

### <a name="role-based-access-control"></a>Control de acceso basado en roles
#### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Nuevo acceso de administración basada en roles para los administradores de Intune <!-- 1099990 -->  
Se va a agregar un nuevo rol de administrador de acceso condicional para ver, crear, modificar y eliminar directivas de acceso condicional de Azure AD. Anteriormente, solo los administradores globales y de seguridad tenían este permiso. Se puede conceder a los administradores de Intune el permiso de este rol para que tengan acceso a las directivas de acceso condicional.


### <a name="device-enrollment"></a>Inscripción de dispositivos
#### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Etiquetado de los dispositivos corporativos con el número de serie<!-- 1215070 -->  
Intune ahora admite la carga de números de serie de iOS, macOS y Android como identificadores de dispositivos corporativos. No puede usar en este momento números de serie para impedir que los dispositivos personales se inscriban, ya que los números de serie no se comprueban durante la inscripción. Próximamente se podrán bloquear los dispositivos personales por el número de serie.


### <a name="device-management"></a>Administración de dispositivos
#### <a name="new-remote-actions-for-ios-devices----854689---"></a>Nuevas acciones remotas para los dispositivos iOS <!-- 854689 -->
En esta versión, hemos agregado dos nuevas acciones de dispositivo remoto para dispositivos iOS:

-   [Cerrar sesión del usuario actual](device-logout-user.md): cierra la sesión del usuario actual de un dispositivo iOS que seleccione.
-   [Quitar usuario](device-remove-user.md): elimina un usuario que seleccione de la memoria caché local en un dispositivo iOS.


Con estas acciones remotas, los administradores pueden administrar las cuentas de los usuarios almacenadas en caché en un dispositivo iPad compartido y también cerrar la sesión del usuario que tiene la sesión iniciada en esos momentos en el dispositivo.

Durante la inscripción, el administrador determina el número máximo de cuentas de usuario que pueden almacenarse en caché en un dispositivo. "Quitar usuario" permite a los administradores quitar usuarios determinados que están almacenados en caché.

"Cerrar sesión del usuario actual" cerrará la sesión del usuario que tiene la sesión iniciada en esos momentos en el dispositivo. Esta acción puede encontrarse en la parte superior de la hoja de información general del dispositivo donde se encuentran normalmente las acciones del dispositivo.

"Quitar usuario" eliminará un usuario especificado de la caché local del dispositivo. Esta acción puede encontrarse yendo a "Supervisar" -> "Usuarios" -> clic con el botón derecho en un usuario específico de la lista. Cualquier dato que esté asociado a la cuenta de usuario que no se haya sincronizado se perderá. Además, la lista de usuarios puede tardar hasta 24 horas en reflejar que el usuario se ha eliminado.

#### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Compatibilidad con dispositivos iPad compartidos con la aplicación Classroom de iOS<!-- 1044681 -->
En esta versión, hemos ampliado la compatibilidad con la administración de la aplicación Classroom en iOS, a fin de incluir a los estudiantes que se registran en dispositivos iPad compartidos con sus identificadores de Apple administrados.


### <a name="app-management"></a>Administración de aplicaciones  
#### <a name="support-for-offline-apps-from-the-windows-store-for-business-----777044----"></a>Compatibilidad con aplicaciones sin conexión desde la Tienda Windows para empresas<!--- 777044 --->
Las aplicaciones sin conexión que ha adquirido en la Tienda Windows para empresas ahora se sincronizarán con el portal de Intune. Así, puede implementar estas aplicaciones en grupos de usuarios o grupos de dispositivos. Las aplicaciones sin conexión no se instalan desde la Tienda, sino mediante Intune.

#### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft Teams ahora forma parte de la lista de CA basada en aplicación de aplicaciones aprobadas <!-- 1257019 -->

La aplicación Microsoft Teams para iOS y Android ahora forma parte de las aplicaciones aprobadas para las directivas de acceso condicional basado en la aplicación en Exchange y SharePoint Online. La aplicación puede configurarse para todos los inquilinos mediante la hoja Intune App Protection de Azure Portal en estos momentos mediante el acceso condicional basado en la aplicación.

#### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Integración de App Proxy y Managed Browser <!-- 1287310 -->
 Intune Managed Browser ahora puede integrarse con el servicio de Azure AD Application Proxy para permitir que los usuarios tengan acceso a los sitios web internos incluso cuando están trabajando en remoto. Los usuarios del explorador simplemente especifican la URL del sitio como lo harían normalmente y Managed Browser enruta la solicitud mediante la puerta de enlace web de Application Proxy. Para obtener más información, vea [Administrar el acceso a Internet mediante directivas de Managed Browser](app-configuration-managed-browser.md).


#### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Nuevas opciones de configuración de aplicaciones para Intune Managed Browser<!-- 682951 -->
En esta versión, hemos agregado más configuraciones para la aplicación Intune Managed Browser para iOS y Android. Ahora puede usar una directiva de configuración de aplicaciones para configurar la página principal predeterminada y los marcadores para el explorador.
Para obtener más información, vea [Administrar el acceso a Internet mediante directivas de Managed Browser](app-configuration-managed-browser.md).




### <a name="device-configuration"></a>Configuración de los dispositivos  
#### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Configuración de BitLocker para Windows 10 <!-- 951707 -->
Ahora puede configurar las opciones de BitLocker para dispositivos Windows 10 con un nuevo perfil de dispositivo de Intune. Por ejemplo, puede que necesite que los dispositivos estén cifrados, y también configurar más opciones que se apliquen cuando BitLocker esté activado.
Para obtener más información, vea [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Configuración de Endpoint Protection para Windows 10 y versiones posteriores).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Nueva configuración del perfil de restricción de dispositivo Windows 10<!--- 978527,  978550, 978569, 1050031, 1058611,  --->

En esta versión, hemos agregado nuevas opciones para el perfil de restricción de dispositivos Windows 10, en las categorías siguientes:

 -  Windows Defender
-  Red de telefonía móvil y conectividad
-  Experiencia de pantalla bloqueada
-  Privacidad
-  Búsqueda
-  Contenido destacado de Windows
-  Explorador Edge

Para obtener más información sobre la configuración de Windows 10, vea [Configuración de restricciones de dispositivos Windows 10 y versiones posteriores](device-restrictions-windows-10.md).

## <a name="week-of-june-12-2017"></a>Semana del 12 de junio de 2017

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>La aplicación portal de empresa para Android ahora tiene una nueva experiencia de usuario final para las directivas de protección de aplicaciones <!--1305217-->
Basándonos en los comentarios de los clientes, hemos modificado la aplicación del portal de empresa para Android para mostrar un botón **Acceso al contenido de la empresa**. El objetivo es impedir que los usuarios finales pasen innecesariamente por todo el proceso de inscripción cuando solo necesitan tener acceso a las aplicaciones que admiten las directivas de protección de aplicaciones, una característica de la administración de aplicaciones móviles de Intune. Puede ver estos cambios en la página [Novedades en la interfaz de usuario de la aplicación](whats-new-app-ui.md).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nueva acción de menú para quitar fácilmente Portal de empresa de Intune <!--1164569-->
Según los comentarios de los usuarios, se agregó una nueva acción de menú en la aplicación Portal de empresa de Intune para Android con el fin de iniciar su eliminación del dispositivo. Esta acción quita el dispositivo de la administración de Intune, por lo que el usuario puede quitar la aplicación del dispositivo. Puede ver estos cambios en la página de [novedades en la UI de la aplicación](whats-new-app-ui.md) y en la [documentación para el usuario final de Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Mejoras en la sincronización de aplicaciones con Windows 10 Creators Update <!--676505-->

La aplicación Portal de empresa de Intune para Windows 10 ahora iniciará automáticamente una sincronización de las solicitudes de instalación de aplicaciones para dispositivos con Windows 10 Creators Update (versión 1703). De esta forma, se reducirá el problema de estancamiento de las instalaciones de aplicaciones durante el estado "Pending Sync" (Sincronización pendiente). Además, los usuarios podrán iniciar manualmente la sincronización desde dentro de la aplicación. Puede ver estos cambios en la página [Novedades en la interfaz de usuario de la aplicación](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nueva experiencia guiada del Portal de empresa de Windows 10<!---1058938--->

La aplicación del Portal de empresa para Windows 10 incluirá la experiencia de un tutorial de Intune guiado para dispositivos que no se han identificado ni inscrito. La nueva experiencia proporciona instrucciones paso a paso que llevan al usuario por el registro en Azure Active Directory (que es necesario para las características de acceso condicional) y la inscripción en MDM (que es necesaria para las características de administración de dispositivos). La experiencia guiada será accesible desde la página principal del Portal de empresa. Los usuarios pueden seguir usando la aplicación aunque no completen el registro y la inscripción, pero experimentarán una funcionalidad limitada.

Esta actualización solo es visible en dispositivos que ejecuten la Actualización de aniversario de Windows 10 (compilación 1607) o superior. Puede ver estos cambios en la página [Novedades en la interfaz de usuario de la aplicación](whats-new-app-ui.md).

## <a name="week-of-june-5-2017"></a>Semana del 5 de junio de 2017

### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Las consolas de administración de Microsoft Intune y Acceso condicional están disponibles con carácter general

Se anuncia la disponibilidad general de la nueva consola de administración tanto de Intune en Azure como de Acceso condicional. A través de Intune en Azure, ahora puede administrar todas las funcionalidades MAM y MDM de Intune en una experiencia de administración consolidada y aprovechar la agrupación y la selección de destino de Azure AD. Acceso condicional de Azure reúne las amplias funcionalidades de Azure AD e Intune en una consola unificada. Y, desde una experiencia administrativa, migrar a la plataforma Azure permite usar exploradores modernos.

Intune ya está visible sin la etiqueta de **versión preliminar** en la consola de Azure en portal.azure.com.

No es necesario que los clientes existentes tomen ninguna medida en este momento, a menos que se haya recibido un mensaje de una serie de estos en el centro de mensajes en el que se le solicite llevar a cabo una acción para que sea posible migrar sus grupos. Es posible que también haya recibido una notificación del centro de mensajes en el que se le informe que la migración está tardando más de lo debido producto de errores en nuestro lado. Seguimos trabajando con diligencia para migrar cualquier cliente afectado.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Mejoras de los iconos de aplicación en la aplicación Portal de empresa de Intune para iOS
Se actualizó el diseño de los iconos de aplicación en la página principal para reflejar el color de personalización de marca que estableció para Portal de empresa de Intune. Para más información, consulte las [novedades en la UI de la aplicación](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Ahora el selector de cuenta está disponible en la aplicación Portal de empresa de Intune para iOS
Los usuarios de dispositivos iOS pueden ver el nuevo selector de cuenta cuando inician sesión en Portal de empresa de Intune si usan su cuenta profesional o educativa para iniciar sesión en otras aplicaciones de Microsoft. Para más información, consulte las [novedades en la UI de la aplicación](whats-new-app-ui.md).

## <a name="week-of-may-29-2017"></a>Semana del 29 de mayo de 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Cambio de la entidad de MDM sin anular la inscripción de dispositivos administrados <!--1103950-->

Ahora puede cambiar la entidad de MDM sin tener que ponerse en contacto con el Soporte técnico de Microsoft y sin necesidad de anular la inscripción ni de volver a inscribir los dispositivos administrados existentes. En la consola de Configuration Manager, puede [cambiar la entidad de MDM](/sccm/mdm/deploy-use/change-mdm-authority) de Configurar como Configuration Manager (híbrido) a Microsoft Intune (independiente), o viceversa.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notificación mejorada para PIN de inicio en Samsung KNOX <!--1087143-->
Si los usuarios finales necesitan establecer un PIN de inicio en dispositivos Samsung KNOX a efectos de compatibilidad con el cifrado, cuando dichos usuarios pulsen en la notificación que aparece, se les remitirá al lugar exacto de la aplicación de configuración.  Anteriormente, la notificación remitía al usuario final a la pantalla de cambio de contraseña.


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>Compatibilidad de Apple School Manager (ASM) con iPad compartido <!-- 748864, 770395-->

Intune ahora admite el uso de Apple School Manager (ASM) en lugar del Programa de inscripción de dispositivos de Apple para permitir la inscripción inmediata de dispositivos iOS. Es necesario incorporar ASM para usar la aplicación Classroom para Shared iPads, así como habilitar la sincronización de datos de ASM en Azure Active Directory mediante Microsoft School Data Sync (SDS). Para más información, consulte el artículo sobre la [habilitación de la inscripción de dispositivos iOS con Apple School Manager](apple-school-manager-set-up-ios.md).

> [!NOTE]
> Configurar iPad compartidos para que funcionen con la aplicación Classroom requiere configuraciones de dispositivos iOS para Education en Azure que todavía no están disponibles.  Esta funcionalidad se agregará pronto.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>Asistencia remota para dispositivos Android con TeamViewer <!-- 675418 -->

Intune ahora puede usar el software [TeamViewer](https://www.teamviewer.com), que se compra de forma independiente, para permitirle ofrecer asistencia remota a los usuarios que ejecutan dispositivos Android. Para más información, consulte [Asistencia remota para dispositivos Android administrados con Intune](device-profile-android-teamviewer.md).

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Nuevas condiciones de las directivas de protección de aplicaciones para MAM <!-- 679864 -->

Ahora puede establecer un requisito para MAM sin inscripción de usuarios que exige las siguientes directivas:

- Versión mínima de la aplicación
- Versión mínima del sistema operativo
- Versión mínima del SDK para aplicaciones de Intune de la aplicación de destino (solo iOS)

Esta característica está disponible en iOS y Android. Intune admite el cumplimiento del requisito de versiones mínimas de la plataforma de SO, las aplicaciones y el SDK para aplicaciones de Intune. En iOS, las aplicaciones que tienen el SDK integrado también pueden establecer el cumplimiento de una versión mínima a nivel del SDK. El usuario no podrá acceder a la aplicación de destino si no se cumplen los requisitos mínimos a través de la directiva de protección de aplicaciones a los tres niveles distintos mencionados anteriormente. En este punto, el usuario puede quitar la cuenta (en aplicaciones con varias identidades), cerrar la aplicación o actualizar la versión del SO o de la aplicación.

También puede configurar valores adicionales para proporcionar una notificación sin bloqueo que recomienda una actualización del SO o de la aplicación. Puede cerrar esta notificación, y la aplicación puede usarse de la forma habitual.

Para más información, consulte [Configuración de directivas de protección de aplicaciones de iOS](app-protection-policy-settings-ios.md) y [Configuración de directivas de protección de aplicaciones de Android](app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Configuración de aplicación para Android for Work <!-- 621621 -->
Algunas aplicaciones Android de la tienda admiten opciones de configuración administradas que permiten que un administrador de TI controle cómo se ejecuta la aplicación en el perfil de trabajo. Con Intune, ahora puede ver las configuraciones que son compatibles con una aplicación y configurarlas desde el portal de Intune con un diseñador de configuración o un editor de JSON. Para más información, consulte el artículo sobre el [uso de configuraciones de aplicación para Android for Work](app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Nueva funcionalidad de configuración de aplicación para MAM sin inscripción <!-- 677969 -->

Ahora puede crear directivas de configuración de aplicación a través de MAM sin canal de inscripción. Esta característica es equivalente a las directivas de configuración de aplicación disponibles en la configuración de aplicación de administración de dispositivos móviles (MDM). Si desea un ejemplo de configuración de aplicación con MAM sin inscripción, consulte [Administrar el acceso a Internet mediante directivas de Managed Browser con Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Configuración de las listas de direcciones URL permitidas y bloqueadas para Managed Browser <!-- 682960 -->

Ahora puede configurar una lista de direcciones URL y dominios permitidos y bloqueados para Intune Manager Browser con los valores de configuración de aplicación en Azure Portal. Estos valores se pueden configurar independientemente de si se usa en un dispositivo administrado o no administrado. Para más información, consulte [Administrar el acceso a Internet mediante directivas de Managed Browser con Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Vista de departamento de soporte técnico de directiva de protección de aplicaciones <!-- 1069473 -->

Los usuarios del departamento de soporte técnico de TI ahora pueden comprobar el estado de la licencia de usuario y el estado de las aplicaciones de directiva de protección de aplicaciones asignadas a los usuarios en la hoja Solución de problemas. Para información detallada, consulte [Solución de problemas](./help-desk-operators.md).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Control de las visitas a sitios web en dispositivos iOS <!-- 723832 -->

Ahora puede controlar qué sitios web pueden visitar los usuarios de dispositivos iOS mediante uno de los dos métodos siguientes:

- Agregar direcciones URL permitidas y bloqueadas mediante el filtro de contenido web integrado de Apple.

- Permitir que el explorador Safari acceda solo a sitios web especificados. Se crean marcadores en Safari para cada sitio que especifique.

Para más información, consulte [Configuración de filtro de contenido web para dispositivos iOS](web-content-filter-settings-ios.md).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Configuración previa de permisos de dispositivo para aplicaciones de Android for Work <!-- 621614 -->

En el caso de las aplicaciones implementadas en perfiles de trabajo de dispositivos Android for Work, ahora puede configurar el estado de los permisos en cada aplicación.  De forma predeterminada, las aplicaciones de Android que requieren permisos de dispositivo como el acceso a la ubicación o la cámara del dispositivo solicitarán a los usuarios que acepten o denieguen permisos.  Por ejemplo, si una aplicación usa el micrófono del dispositivo, se solicita al usuario final que conceda a la aplicación el permiso para usar el micrófono. Esta característica le permite definir permisos en nombre del usuario final.  Ahora puede configurar permisos para a) denegar automáticamente sin notificar al usuario, b) aprobar automáticamente sin notificar al usuario, o c) pedirle al usuario que acepte o deniegue los permisos. Para más información, consulte [Configuración de restricciones de dispositivos Android for Work en Microsoft Intune](device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Establecimiento de un PIN específico de la aplicación para dispositivos Android for Work <!-- 728976, 1102534 -->

Los dispositivos Android 7.0 y versiones posteriores con un perfil de trabajo administrado como un dispositivo Android for Work permiten que el administrador defina una directiva de código de acceso que solo se aplique a aplicaciones del perfil de trabajo.  Las opciones son:

- Definir una contraseña de código de acceso a nivel de dispositivo: se trata del código de acceso que el usuario debe usar para desbloquear todo el dispositivo.
 Definir una directiva de código de acceso solo a nivel de perfil de trabajo: a los usuarios se les pedirá que escriban un código de acceso cada vez que se abra cualquier aplicación del perfil de trabajo.
- Definir una directiva para el dispositivo y el perfil de trabajo: el administrador de TI tiene la opción de definir una directiva de código de acceso para el dispositivo y otra para el perfil de trabajo con diferentes intensidades (por ejemplo, un PIN de cuatro dígitos para desbloquear el dispositivo y uno de seis para abrir cualquier aplicación de trabajo).

Para más información, consulte [Configuración de restricciones de dispositivos Android for Work en Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> Esta opción solo está disponible en Android 7.0 y versiones posteriores.  De forma predeterminada, el usuario final puede usar los dos PIN definidos por separado o de optar por combinar los dos en el más seguro de ellos.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Nuevas opciones de configuración para dispositivos Windows 10 <!-- 978585 -->

Agregamos una nueva [configuración de restricción de dispositivos Windows](device-restrictions-windows-10.md) que controla características como la proyección inalámbrica, la detección de dispositivos, la conmutación de tareas y los mensajes de error de tarjetas SIM.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Actualizaciones de la configuración de certificados <!-- 918991 and 823198 -->

Cuando crea un perfil de certificado SCEP, en el **formato del nombre del sujeto**, la opción **Personalizar** está disponible para dispositivos iOS, Android y Windows. Antes de esta actualización, el campo **Personalizar** solo estaba disponible para dispositivos iOS. Para más información, consulte [Creación de un perfil de certificado SCEP] (certificates-scep-configure.md#how-to-create-a-scep-certificate-profile).

Cuando crea un perfil de certificado PKCS, en el **nombre alternativo del sujeto**, está disponible la opción **Atributo de Azure AD personalizado**. La opción **Departamento** está disponible cuando se selecciona **Atributo de Azure AD personalizado**. Para más información, consulte [Creación de un perfil de certificado PKCS] (certficates-pfx-configure.md#how-to-create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Configuración de varias aplicaciones que se pueden ejecutar cuando un dispositivo Android está en el modo de pantalla completa <!-- 662059 -->

Si un dispositivo Android está en el modo de pantalla completa, anteriormente solo podía configurar una aplicación que se podía ejecutar. Ahora puede configurar varias aplicaciones con el id. de la aplicación, la dirección URL de la tienda o seleccionando una aplicación Android que ya administra. Para más información, consulte [Configuración del modo de pantalla completa](device-restrictions-android.md#kiosk).


## <a name="notices"></a>Notificaciones

### <a name="ip-addresses-for-intune-updated----1175274---"></a>Actualización de direcciones IP para Intune <!-- 1175274 -->

Hay una [lista actualizada de nombres DNS y direcciones IP](/intune/network-bandwidth-use) disponibles para la configuración de proxy del firewall.

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>Uso de Azure Active Directory para acceso condicional <!-- 967947 -->

El acceso condicional está disponible en la sección Azure Active Directory de la consola de Azure y proporciona un marco más eficaz y flexible para establecer directivas de aplicaciones en la nube como Office 365 Exchange Online y SharePoint Online.  Use la hoja **Acceso condicional en Azure Active Directory** para configurar directivas en lugar de la consola de Intune clásica. Es necesario volver a crear las directivas existentes de la consola de Intune clásica en la consola de Azure. Para más información, consulte [Creación de directivas de acceso condicional de Azure AD](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview)

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->

Para las cuentas de Intune creadas después de enero de 2017, Intune habilitó el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en Azure Portal. Anteriormente, la vista previa de inscripción de Apple solo era accesible desde los vínculos al portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requieren una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero la información estará disponible tan pronto como sea posible. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta no tiene acceso a Azure Portal.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Roles de administración que se reemplazan en el Portal de Azure

Los roles de administración de aplicaciones móviles (MAM) existentes (colaborador, propietario y de solo lectura) usados en el portal clásico de Intune (Silverlight) se reemplazan por un conjunto completo de nuevos controles de administración basada en roles (RBAC) en el Portal de Intune Azure. Cuando haya migrado a Azure Portal, tendrá que reasignar estos nuevos roles de administración a los administradores. Para obtener más información sobre RBAC y los nuevos roles, vea [Roles de Intune (RBAC) para Microsoft Intune](/intune/role-based-access-control).

## <a name="whats-coming"></a>Próximas novedades

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017"></a>Recordatorio de compatibilidad de plataforma: la compatibilidad estándar de Windows Phone 8.1 finalizará el 11 de julio de 2017
<!-- 1327781 -->

El 11 de julio de 2017 terminará la compatibilidad estándar de la plataforma Windows Phone 8.1. La compatibilidad de los equipos Windows 8.1 no se verá afectada.

No hay ningún impacto inmediato en ningún dispositivo Windows Phone 8.1 administrado por el servicio Intune. Los dispositivos inscritos continuarán funcionando y todas las directivas, configuraciones y aplicaciones seguirán funcionando según lo previsto. Tenga en cuenta que no hay mejoras destinadas a la plataforma Windows Phone 8.1 en el servicio Intune ni para la aplicación Portal de empresa de Windows Phone 8.1. 

Se recomienda que actualice los dispositivos Windows Phone 8.1 aptos a Windows 10 Mobile en cuanto pueda. 

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Cambios en la compatibilidad de la aplicación de portal de empresa de iOS de Intune <!-- 1164474  -->


Próximamente, habrá una nueva versión de la aplicación de portal de empresa de Microsoft Intune para iOS que solo admitirá dispositivos que ejecuten iOS 9.0 o posterior. La versión del portal de empresa que admite iOS 8 todavía estará disponible durante un período de tiempo muy breve. En cambio, tenga en cuenta que si también usa aplicaciones iOS habilitadas para MAM, admitimos iOS 9.0 y versiones posteriores, por lo que querrá asegurarse de que sus usuarios finales actualizan al último sistema operativo. 

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Le informamos de esto con antelación, incluso cuando no tenemos fechas específicas, para que tenga tiempo para planear. Asegúrese de que sus usuarios han actualizado a iOS 9+ y cuando se presente la aplicación de portal de empresa, solicite que sus usuarios finales actualicen su aplicación de portal de empresa.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?

Anime a los usuarios a que actualicen a iOS 9.0 o posterior para aprovechar las nuevas características de Intune.  Anime a los usuarios a que instalen la última versión del portal de empresa y se aprovechen de las nuevas características que ofrecerá.

Vaya a Intune en Azure Portal y vea Dispositivos > Todos los dispositivos y filtre por la versión de iOS para ver cualquier dispositivo actual con sistemas operativos anteriores a iOS 9.

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Se mejoró la experiencia de inicio de sesión en todas las aplicaciones del Portal de empresa para todas las plataformas <!--User Story 1132123-->

Estamos anunciando un cambio que aparecerá en los próximos meses que mejorará la experiencia de inicio de sesión para las aplicaciones de Portal de empresa de Intune para Android, iOS y Windows. La nueva experiencia del usuario aparecerá automáticamente en todas las plataformas de la aplicación Portal de empresa cuando Azure AD haga este cambio. Además, los usuarios ahora pueden iniciar sesión en Portal de empresa desde otro dispositivo con un código generado de un solo uso. Esto resulta útil especialmente en casos en los que los usuarios necesitan iniciar sesión sin credenciales.

Para ver capturas de pantalla de la experiencia de inicio de sesión anterior, la nueva experiencia de inicio de sesión con credenciales y la nueva experiencia de inicio de sesión desde otro dispositivo, consulte [Novedades en la UI de la aplicación](/intune/whats-new-app-ui).

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Plan de cambio: Intune está cambiando la experiencia del portal Partner de Intune<!-- 1050016 -->

Estamos quitando la página Partner de Intune de manage.microsoft.com a partir de la actualización de servicio de mediados de mayo de 2017.  

Si es un administrador de partners, ya no podrá ver y realizar acciones en nombre de sus clientes desde la página Partner de Intune pero, en su lugar, tendrá que iniciar sesión en uno de los dos portales de partners de Microsoft.

Tanto el [Centro de partners de Microsoft](https://partnercenter.microsoft.com/) como el [Centro de administración de partners de Microsoft Office 365](https://portal.office.com/) le permitirá iniciar sesión en las cuentas de cliente que administra. En adelante, como partner, use uno de estos sitios para administrar a sus clientes.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->

Apple ha anunciado que se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS.

Hay disponible una versión de la aplicación Portal de empresa para iOS a través del programa Apple TestFlight que aplica los nuevos requisitos de ATS. Si desea probarla para que pueda experimentar el cumplimiento de ATS, envíe un correo electrónico a <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> con su nombre, apellidos, dirección de correo electrónico y nombre de la empresa. Visite nuestro [blog de soporte técnico de Intune](https://aka.ms/compportalats) para obtener más información.

### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades de la interfaz de usuario del portal de empresa](whats-new-app-ui.md)
* [Novedades de los meses anteriores](whats-new-archive.md)
