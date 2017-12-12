---
title: "Edición anticipada"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 11/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 35bf193563deb34ac59df245c622bbc011d80b76
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="the-early-edition-for-microsoft-intune---december-2017"></a>La edición anticipada para Microsoft Intune, diciembre de 2017

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

### <a name="app-protection-policies-----679615---"></a>Directivas de protección de aplicaciones  <!-- 679615 -->
Las directivas de Intune App Protection ofrecerán la capacidad de crear directivas predeterminadas globales para habilitar rápidamente la protección en todos los usuarios de todo el inquilino.

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Revocación de las aplicaciones del programa de compras por volumen de iOS  <!-- 820863 -->
Para un dispositivo determinado con una o más aplicaciones del programa de compras por volumen (VPP) de iOS, podrá revocar la licencia de aplicación basada en dispositivo asociada para el dispositivo. Revocar una licencia de aplicación no desinstalará la aplicación VPP desde el dispositivo. Para desinstalar una aplicación VPP, debe cambiar la acción de asignación a **Desinstalar**. Para más información, consulte [Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune](vpp-apps-ios.md).

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Revocación de las licencias de un token del programa de compras por volumen de iOS <!-- 820870 -->
Podrá revocar la licencia de todas las aplicaciones del programa de compras por volumen (VPP) de iOS para un token de VPP determinado.

### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Eliminación de un token del programa de compras por volumen de iOS <!-- 820879 -->
Podrá eliminar el token del programa de compras por volumen (VPP) de iOS con la consola. Esto puede resultar necesario cuando tiene instancias duplicadas de un token de VPP.

### <a name="network-access-control-nac-device-check-in-reporting-----1232250---"></a>Informes de comprobación de dispositivos de control de acceso a la red (NAC)  <!-- 1232250 -->
Antes de este cambio, los administradores de TI no podían determinar en el lado de Intune si un dispositivo administrado por NAC se comunicaba o no con su solución de NAC. Cuando un dispositivo administrado por NAC no se comunica con su solución de NAC, se considera que el dispositivo no es compatible con la solución de NAC y, por lo tanto, esta solución lo bloquea y también lo bloquean las directivas de acceso condicional que se basan en el estado de cumplimiento del dispositivo.

Con este cambio, los administradores de TI pueden ver cuáles son los dispositivos administrados por NAC que se comunican correctamente o no con su solución de NAC. Esta funcionalidad nueva consta de dos funciones de supervisión nuevas ubicadas en la carga de trabajo de cumplimiento de dispositivos dentro de Intune. Las estadísticas se muestran a continuación:
- **Promedio de llamadas de NAC en la última hora**
- **Última solicitud entrante de NAC (fecha/hora)**

### <a name="new-ios-device-action------1244701---"></a>Nueva acción de dispositivo iOS   <!-- 1244701 -->
Puede apagar los dispositivos iOS 10.3 supervisados. Esta acción apaga inmediatamente el dispositivo sin enviar una advertencia al usuario final. La acción **Shut down (supervised only)** [Apagar (solo con supervisión)] se puede encontrar en las propiedades de dispositivos cuando se selecciona un dispositivo en la carga de trabajo del **dispositivo**.

### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755-eeready---"></a>Compatibilidad de varios conectores con el control de certificados SCEP y PFX <!-- 1361755 eeready -->
Los clientes que usan el conector NDES local para entregar los certificados a los dispositivos podrán configurar varios conectores en un solo inquilino.

Esta funcionalidad nueva admite el siguiente escenario:

- **Alta disponibilidad**

    Cada conector NDES extrae solicitudes de certificado desde Intune.  Si un conector NDES queda sin conexión, el otro puede seguir procesando las solicitudes.

### <a name="new-automatic-redeployment-setting----1469168---"></a>Nueva configuración de la reimplementación automática <!-- 1469168 -->
Esta configuración permite que los usuarios con derechos administrativos eliminen todos los datos de usuario y las configuraciones con **CTRL + Win + R** en la pantalla de bloqueo del dispositivo. El dispositivo se reconfigurará y reinscribirá automáticamente en la administración.

Esta configuración se puede encontrar en Windows 10 -> Restricciones de dispositivos -> General -> Reimplementación automática.

### <a name="install-office-apps-on-macos-devices----1494311---"></a>Instalación de aplicaciones de Office en dispositivos macOS <!-- 1494311 -->
Podrá instalar aplicaciones de Office en dispositivos macOS. Este nuevo tipo de aplicación le permitirá instalar Word, Excel, PowerPoint, Outlook y OneNote. Estas aplicaciones también incluyen Microsoft AutoUpdater (MAU) para ayudar a mantener aplicaciones seguras y actualizadas.

### <a name="surface-hub-resource-account-supported----1566442-eeready---"></a>Compatibilidad con la cuenta del recurso de Surface Hub <!-- 1566442 eeready -->
Se agregará una nueva acción de dispositivo para que los administradores puedan definir y actualizar la cuenta del recurso asociada con Surface Hub.

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

### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>Intune ahora proporciona la operación Movimiento de cuenta  <!-- 1573558, 1579830 -->
El **Movimiento de cuenta** migra un inquilino de una unidad de escalado de Azure (ASU) a otra. El **Movimiento de cuenta** se puede usar para ambos escenarios iniciados por el cliente, cuando se llama al equipo de soporte técnico de Intune para solicitarlo, y también puede tratarse de un escenario de Microsoft donde este necesita hacer ajustes al servicio en el back-end. Durante el **Movimiento de cuenta**, el inquilino entra en el modo de solo lectura (ROM). Las operaciones de servicio, como la inscripción, el cambio de nombre de los dispositivos, la actualización del estado de cumplimiento, presentarán errores durante el período de ROM.

### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Nueva configuración del perfil de configuración de dispositivo del Centro de seguridad de Windows Defender (WDSC) <!-- 1335507 -->
Intune agrega una sección nueva de configuración del perfil de configuración de dispositivo en la protección del punto de conexión denominada **Centro de seguridad de Windows Defender**. Los administradores de TI pueden configurar a qué pilares de la aplicación Centro de seguridad de Windows Defender pueden acceder los usuarios finales. Si un administrador de TI oculta un pilar en la aplicación Centro de seguridad de Windows Defender, las notificaciones relativas al pilar oculto no se mostrarán en el dispositivo del usuario.

Estos son los pilares que los administradores pueden ocultar de la configuración del perfil de configuración de dispositivo del Centro de seguridad de Windows Defender:
- Protección contra amenazas y virus
- Mantenimiento y estado del dispositivo
- Firewall y protecciones de red
- Control de aplicaciones y explorador
- Opciones de familia

Los administradores de TI también pueden personalizar las notificaciones que recibirán los usuarios. Por ejemplo, puede configurar si los usuarios reciben todas las notificaciones que generan los pilares visibles en WDSC o solo las notificaciones críticas. Las notificaciones no críticas incluyen resúmenes periódicos de la actividad de Antivirus de Windows Defender y las notificaciones cuando se completan las detecciones. Todas las otras notificaciones se consideran críticas. Además, también puede personalizar el contenido mismo de la notificación. Por ejemplo, puede proporcionar la información de contacto de TI para insertarla en las notificaciones que aparecen en los dispositivos de los usuarios.




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Asignación de aplicaciones móviles de Office 365 a dispositivos iOS y Android mediante el tipo de aplicación integrada <!-- 1332318 -->
El tipo de aplicación **integrada** facilita la creación y la asignación de aplicaciones de Office 365 a los dispositivos iOS y Android administrados. Entre estas aplicaciones están las de O365, como Word, Excel, PowerPoint y OneDrive. Puede asignar aplicaciones específicas al tipo de aplicación y, luego, editar la configuración de la información de la aplicación.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Compatibilidad del inicio de sesión único con iOS <!-- 1333645 -->  
Es posible usar el inicio de sesión único para los usuarios de iOS. Las aplicaciones de iOS que están codificadas para buscar las credenciales de usuario en la carga de inicio de sesión único funcionarán con esta actualización de la configuración de carga. También puede utilizar el UPN y el identificador de dispositivo de Intune para configurar el nombre de la entidad de seguridad y el dominio Kerberos.

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocolo de texto permitido en aplicaciones administradas <!-- 1414050  -->
Las aplicaciones administradas por Intune App SDK podrán enviar mensajes SMS.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloqueo remoto de los dispositivos macOS administrados con Intune <!-- 1437691 -->
Si pierde un dispositivo macOS, puede bloquearlo y establecer en él un PIN de recuperación de 6 dígitos. Una vez bloqueado, la hoja de **información general del dispositivo** muestra el PIN hasta que se envía otra acción de dispositivo.

Para obtener más información, consulte [Bloqueo remoto de los dispositivos administrados con Intune](device-remote-lock.md).


### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>Modificación de la resolución de conflictos de asignación para aplicaciones de la tienda iOS <!-- 1480316 -->
Los usuarios finales pueden experimentar un cambio en la disponibilidad de las aplicaciones de la tienda iOS. Actualmente, una aplicación que se ha asignado a dos grupos con un conflicto entre **Requerido y Disponible** y **No aplicable** se resuelve como **Requerido y Disponible**. Con el cambio, una aplicación que experimente este conflicto se resuelve como **No aplicable**.

El cambio soluciona la confusión que se produce cuando una aplicación se asigna a varios grupos con propósitos de aplicación distintos.

Si quiere que la aplicación esté disponible en el portal de trabajo de la información y en el Portal de empresa antes de la publicación de la versión de noviembre, tiene dos opciones:

1. Quitar la asignación **No aplicable** para su grupo.
2. Crear un nuevo grupo que no incluya miembros con el propósito **Requerido y Disponible** asignado, y asignar ese grupo como **No aplicable**.

Para obtener más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).

> [!Note]
> Después del lanzamiento, la versión ya no podrá ver ni modificar las asignaciones de aplicación de administración de dispositivos móviles (MDM) en la consola de Intune clásica. No obstante, puede usar la consola de Azure o la API Graph de Intune para asignar las aplicaciones.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>Administración independiente de dispositivos Android for Work y dispositivos Android <!-- 1490731 -->
Intune admitirá la administración de inscripciones de dispositivos Android for Work independientemente de la plataforma Android. Esta configuración se administra en **Inscripción de dispositivos** > **Restricciones de inscripción** > **Restricciones de tipo de dispositivo**. (Anteriormente se encontraban bajo **Inscripción de dispositivos** > **Inscripción en Android for Work** > **Configuración de la inscripción de Android for Work**).

De forma predeterminada, la configuración de los dispositivos Android for Work será igual que la configuración de los dispositivos Android. Sin embargo, dejará de ser así tras modificar la configuración de Android for Work.
 
Si bloquea la inscripción de Android for Work personal, tan solo los dispositivos Android corporativos podrán inscribirse como Android for Work.

Cuando trabaje con la nueva configuración, tenga en cuenta lo siguiente:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Si es la primera vez que incorpora inscripciones de Android for Work
La nueva plataforma Android for Work está bloqueada de manera predeterminada en Restricciones de tipo de dispositivo. Después de incorporar la característica, puede permitir que los dispositivos se inscriban con Android for Work. Para ello, cambie el valor predeterminado o cree una nueva restricción de tipo de dispositivo que sustituya a la predeterminada.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Si ya ha incorporado inscripciones de Android for Work
Si no es la primera que realiza una incorporación, su situación depende de la configuración elegida:

| Configuración | Estado de Android for Work en el valor predeterminado de Restricción de tipo de dispositivo | Notas |
| --- | --- | --- |
| **Administrar todos los dispositivos como Android** | Bloqueado | Todos los dispositivos Android deben inscribirse sin Android for Work. |
| **Administrar los dispositivos compatibles como Android for Work** | Permitido | Todos los dispositivos que admiten Android for Work deben inscribirse con Android for Work. |
| **Administrar los dispositivos compatibles para usuarios solo en estos grupos como Android for Work** | Bloqueado | Para invalidar el valor predeterminado, se creó una directiva de restricción de tipo de dispositivo independiente. Esta directiva define los grupos que se seleccionaron previamente para permitir la inscripción de Android for Work. Los usuarios de los grupos seleccionados seguirán teniendo permiso para inscribir sus dispositivos Android for Work. Todos los demás usuarios tienen restringida la inscripción con Android for Work. |

En todos los casos, se conserva la normativa que haya previsto. No se requiere ninguna acción por su parte para seguir permitiendo Android for Work en su entorno, tanto de forma global como por grupo.

El lanzamiento de estos cambios se iniciará con la actualización de noviembre, pero pueden tardar un tiempo en ejecutarse en su cuenta. Cuando estos cambios entren en vigor en su cuenta, recibirá una notificación de confirmación en el portal de Office 365.


### <a name="configure-an-ios-app-pin----1586774---"></a>Configurar un PIN de aplicación iOS <!-- 1586774 -->
Pronto podrá solicitar un PIN para las aplicaciones iOS de destino. En Azure Portal puede configurar el requisito de PIN y la fecha de expiración en días. Para obtener acceso a una aplicación de iOS, se le pedirá al usuario que establezca y use un nuevo PIN. Solo las aplicaciones iOS que tienen habilitada la protección aplicaciones con Intune App SDK serán compatibles con esta característica.

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Agregar "Buscar mi iPhone" para dispositivos personales <!--1427287-->
Podrá ver si los dispositivos iOS tienen activado el bloqueo de activación. Esta característica se encontraba anteriormente en Intune, en el portal clásico.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Los sitios web de Azure Active Directory pueden requerir la aplicación Intune Managed Browser y compatibilidad con el inicio de sesión único para Managed Browser (versión preliminar pública) <!-- 710595 -->   
Con Azure Active Directory (Azure AD), podrá restringir el acceso a sitios web en dispositivos móviles a la aplicación Intune Managed Browser. En Managed Browser, los datos del sitio web permanecen seguros y separados de los datos personales del usuario final. Además, Managed Browser admite funciones de inicio de sesión único para sitios protegidos por Azure AD. Al iniciar sesión en Managed Browser, o al usarlo en un dispositivo con otra aplicación administrada por Intune, se permite que Managed Browser tenga acceso a sitios corporativos protegidos por Azure AD sin necesidad de que el usuario escriba sus credenciales. Esta funcionalidad se aplica a sitios como Outlook Web Access (OWA) y SharePoint Online, así como a otros sitios corporativos, como los recursos de intranet a los que se tiene acceso a través de Azure App Proxy.


<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Compatibilidad con una directiva de actualización de la edición de Windows 10   <!-- 903672(archived), 1119689 -->  
Podrá crear una directiva de actualización de la edición de Windows 10 que actualice los dispositivos con Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education y Windows 10 Professional Education N. Para obtener más información sobre las actualizaciones de la edición de Windows 10, vea [Configuración de actualizaciones de la edición de Windows 10](edition-upgrade-configure-windows-10.md).




<!-- the following are present prior to 1709 -->



### <a name="android-for-work-support-for-lookout----1087312---"></a>Compatibilidad de Android for Work con Lookout <!-- 1087312 -->   
El conector de Intune con Lookout admitirá dispositivos de Android for Work cuando se use la aplicación Lookout for Work. Puede implementar la aplicación Lookout dentro o fuera del contenedor.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune App Protection y Herramientas de desarrollo de Citrix MDX <!-- 709185 -->
Puede administrar dispositivos y aplicaciones con una combinación de Citrix XenMobile MDX y Microsoft Intune. Esto le permite administrar aplicaciones con la directiva de protección de aplicaciones de Intune mientras usa tecnología mVPN de Citrix.

Puede buscar un repositorio de código que contiene la herramienta de ajuste de aplicaciones de Intune e Intune App SDK para iOS y Android, que se integra con la tecnología mVPN de Citrix MDX.


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Compatibilidad de alta disponibilidad de On-premises Exchange Connector <!-- 676614 -->   
Puede tener varios roles de servidor de acceso de cliente (CAS) para el conector de Exchange local. Por ejemplo, si se produce un error en el CAS principal, Exchange Connector recibe una consulta para recurrir a otros CAS. Esta característica garantiza que no se interrumpa el servicio.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Módulo de administración de System Center Operations Manager para Exchange Connector <!-- 885457 -->   
El módulo de administración de System Center Operations Manager para Exchange Connector está disponible para ayudarle a analizar los registros de Exchange Connector. Este módulo de administración le proporciona distintas maneras de supervisar Intune cuando tenga que resolver problemas.





## <a name="intune-apps"></a>Aplicaciones de Intune

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Ayudar a los usuarios con la aplicación Portal de empresa para Android <!---1573324, 1573150, 1558616, 1564878--->
La aplicación de Portal de empresa para Android incorpora instrucciones dirigidas a los usuarios finales con la finalidad de ayudarles a comprender y, siempre que sea posible, resolver por ellos mismos los nuevos casos de uso. 

- Se mostrará un nuevo mensaje de error que explica que se ha implementado una directiva de cumplimiento para el cifrado, pero que el [fabricante no cifra el dispositivo](/intune-user-help/your-device-appears-encrypted-but-cp-says-otherwise-android) de acuerdo con las [recomendaciones de Google](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setStorageEncryption(android.content.ComponentName, boolean).
- Los usuarios finales serán guiados al (portal de Azure Active Directory)[https://account.activedirectory.windowsazure.com/r/#/profile] para quitar un dispositivo en caso de que hayan alcanzado el número máximo de dispositivos que se permite agregar. 
- Los usuarios finales tienen a su disposición una serie de instrucciones que pueden seguir para [corregir errores de activación en dispositivos Samsung KNOX](https://go.microsoft.com/fwlink/?linkid=859718) o [desactivar el modo de ahorro de energía](/intune-user-help/power-saving-mode-android). Si ninguna de esas soluciones resuelve su problema, se les proporcionará una explicación de cómo [enviar registros a Microsoft](/intune-user-help/send-logs-to-microsoft-ios). 


### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nueva acción “Resolver” disponible para dispositivos Android <!---1583480--->
La aplicación Portal de empresa para Android presenta la acción “Resolve” en la página _Actualizar configuración del dispositivo_. Si selecciona esta opción, el usuario final irá directamente a la configuración que causa la no conformidad de su dispositivo. La aplicación Portal de empresa para Android admite actualmente esta acción para las opciones de configuración [código de acceso de dispositivo](/intune-user-help/set-your-pin-or-password-android), [cifrado de dispositivo](/intune-user-help/encrypt-your-device-android), [depuración USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) y [orígenes desconocidos](/intune-user-help/you-need-to-turn-off-unknown-sources-android). 




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Redireccionamiento a los usuarios de macOS a nuestra nueva aplicación Portal de empresa <!--1380728-->   
Cuando un usuario final inicia sesión en el sitio web del Portal de empresa para inscribir su dispositivo macOS, se le dirigirá a la descarga de la nueva aplicación Portal de empresa para macOS a fin de que complete el proceso. Esto ocurre con los dispositivos macOS que usan OS X El Capitan 10.11 o una versión posterior. 


<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Las aplicaciones que están disponibles con o sin inscripción ahora se pueden instalar sin que se les solicite la inscripción. <!-- 1334712 -->
Las aplicaciones de empresa que se han puesto a disposición de los usuarios con o sin inscripción en la aplicación de Portal de empresa de Android pueden instalarse sin necesidad de una solicitud de inscripción.


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Compatibilidad de Intune Managed Browser con iOS y Android <!-- 1374196 -->
A partir de octubre de 2017, la aplicación Intune Managed Browser en dispositivos Android admitirá solo los dispositivos con Android 4.4 y versiones posteriores. La aplicación Intune Managed Browser en iOS solo admitirá dispositivos con iOS 9.0 y versiones posteriores. Las versiones anteriores de iOS y Android podrán seguir usando Intune Managed Browser, pero no podrán instalar nuevas versiones de la aplicación y es posible que no puedan tener acceso a todas las funcionalidades de la aplicación. Le recomendamos que actualice la versión del sistema operativo de estos dispositivos a una que sea compatible.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensaje de error mejorado cuando un usuario alcanza el número máximo de dispositivos permitidos para la inscripción <!-- 1270370 -->
En lugar de un mensaje de error genérico, los usuarios finales ven un mensaje de error descriptivo que requiere acción: "Ya ha inscrito el máximo número de dispositivos permitidos por su administrador de TI. Quite un dispositivo inscrito o reciba ayuda de su administrador de TI".




## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.




### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.
