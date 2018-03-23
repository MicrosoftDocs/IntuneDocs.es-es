---
title: Edición anticipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e91745abb7c3409b31724101b3071157407acec9
ms.sourcegitcommit: 54fc806036f84a8667cf8f74086358bccd30aa7d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2018
---
# <a name="the-early-edition-for-microsoft-intune---march-2018"></a>Edición anticipada de Microsoft Intune: marzo de 2018

La **edición anticipada** proporciona una lista de características que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No comparta esta información fuera de la compañía. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

> [!Note]
>Los siguientes cambios están en fase de desarrollo de Intune. Para obtener más información sobre las nuevas características híbridas, vea la [página sobre las novedades de implementaciones híbridas](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->

## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Compatibilidad con múltiples instancias de Exchange Connector <!-- 2070451 -->

La limitación de una instancia de Microsoft Intune Exchange Connector por inquilino ya no se aplica. Intune admitirá varias instancias de Exchange Connector para que pueda configurar el acceso condicional de Intune con varias organizaciones de Exchange local.

Con un conector de Exchange local de Intune, se puede controlar el acceso de los dispositivos a los buzones de Exchange locales en función de si un dispositivo está inscrito en Intune y cumple con las directivas de cumplimiento de dispositivos de Intune. Para configurar un conector, descargue el conector de Exchange local de Intune desde Azure Portal e instálelo en un servidor en la organización de Exchange. En el panel de Microsoft Intune, elija **Acceso local** y, después, en **Instalación**, elija **Conector de Exchange ActiveSync**. Descargue el conector de Exchange local e instálelo en un servidor en la organización de Exchange. Ahora que ya no está limitado a un conector de Exchange por inquilino, si tiene otras organizaciones de Exchange, puede seguir el mismo proceso para descargar e instalar un conector para cada organización de Exchange adicional.

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>Disponibilidad próximamente de soporte técnico para el nuevo cliente Cisco AnyConnect para iOS <!-- 1333708 -->

Los nuevos perfiles de VPN creados para Cisco AnyConnect para iOS funcionarán con Cisco AnyConnect 4.0.7x y versiones posteriores. Los perfiles de VPN existentes de Cisco AnyConnect para iOS se etiquetarán como **Cisco Legacy AnyConnect** y continuarán funcionando con Cisco AnyConnect 4.0.5x como lo hacen en la actualidad.

> [!NOTE]
> Este cambio es solo para iOS; seguirá existiendo una sola opción de Cisco AnyConnect para Android, Android for Work y macOS. 

#### <a name="more-information"></a>Más información

Debe crear un nuevo perfil de VPN de Cisco AnyConnect para iOS para admitir la nueva aplicación, ya que la nueva aplicación de Cisco AnyConnect y la aplicación de Cisco Legacy AnyConnect son independientes. Si administra el cliente AnyConnect en su entorno, también debe implementar la nueva aplicación de Cisco AnyConnect. Para completar una actualización, también debe eliminar el perfil de VPN de Cisco Legacy AnyConnect y quitar la aplicación de Cisco Legacy AnyConnect. 

La integración del control de acceso de red (NAC) no funcionará para el nuevo cliente AnyConnect en la versión inicial. Estamos trabajando con Cisco para proporcionar una integración NAC en una futura versión de Intune.

### <a name="enhanced-jailbreak-detection----846515---"></a>Detección de jailbreak mejorada <!-- 846515 -->

La detección de jailbreak mejorada es una nueva configuración de cumplimiento que mejorará la forma en la que Intune evalúa los dispositivos con Jailbreak. La configuración hará que el dispositivo se inserte en el repositorio con Intune con más frecuencia, lo que usará los servicios de ubicación del dispositivo y afectará al uso de la batería.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidad de implementar aplicaciones de línea de negocio (LOB) requeridas en todos los usuarios en dispositivos Windows 10 Escritorio <!-- 1627835 RS4 -->
Los clientes podrán implementar aplicaciones de Windows 10 de línea de negocio requeridas para instalarlas en contextos de dispositivo. Esto permitirá que estas aplicaciones estén disponibles para todos los usuarios del dispositivo. Esto solo es aplicable a dispositivos Windows 10 Escritorio. 

### <a name="expiring-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Aplicaciones de línea de negocio (LOB) a punto de expirar para Microsoft Intune <!-- 748789 -->
En Azure Portal, Intune le avisará de las aplicaciones de línea de negocio que estén a punto de expirar. Al cargar una nueva versión de la aplicación de línea de negocio, Intune quitará la notificación de expiración de la lista de aplicaciones.

### <a name="company-portal-enrollment-improved----1874230--"></a>Mejora de la inscripción de Portal de empresa <!-- 1874230-->
Los usuarios que inscriban un dispositivo mediante el Portal de empresa en Windows 10, compilación 1703, y versiones posteriores podrán completar el primer paso de la inscripción sin salir de la aplicación.

### <a name="new-management-name-column----1333586---"></a>Nueva columna Nombre de administración <!-- 1333586 -->
Una nueva columna denominada **Nombre de administración** se agregará a la hoja de dispositivos. Se trata de un nombre generado automáticamente y que no se puede modificar asignado por cada dispositivo, en función de la fórmula siguiente: 
- Nombre predeterminado para todos los dispositivos: <username>_<devicetype>_<enrollmenttimestamp>
- Para dispositivos agregados en masa: <IdentificadorPaquete/IdentificadorPerfil>_<DeviceType>_<EnrollmentTime> 
 
Se trata de una columna opcional en la hoja de dispositivos. No estará disponible de forma predeterminada y solo se puede obtener acceso a ella mediante el selector de columnas. El nombre del dispositivo no se ve afectado por esta nueva columna.

### <a name="new-settings-for-windows-defender-security-center-notifications-device-configuration-profile----1631906---"></a>Nueva configuración del perfil de configuración de dispositivo de notificaciones del Centro de seguridad de Windows Defender <!-- 1631906 -->

Se agregarán tres nuevas opciones para el perfil de configuración de dispositivo de notificaciones del Centro de seguridad de Windows Defender (WDSC).

Los administradores podrán hacer lo siguiente:

- Ocultar el pilar Identidad
- Ocultar el pilar Hardware y su configuración secundaria
- Ocultar el pilar Ransomware (restauración de archivos de OneDrive para la Empresa)

Al ocultar estos pilares de la aplicación WDSC, los usuarios finales no podrán configurar estas opciones y no se generará ninguna notificación asociada a los componentes ocultos.

### <a name="mam-policies-targeted-based-on-management-state----1665993---"></a>Destino de directivas de MAM en función del estado de administración <!-- 1665993 -->

Podrá destinar las directivas MAM en función del estado de administración del dispositivo:

- **Dispositivos iOS**: podrá tener como destino dispositivos no administrados (solo MAM) o dispositivos administrados con Intune.
- **Dispositivos Android**: podrá tener como destino dispositivos no administrados, dispositivos administrados con Intune y perfiles de Android Enterprise administrados con Intune (anteriormente Android for Work).

### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459--"></a>Configuración del equipo selector para controlar el origen de descarga de las aplicaciones macOS <!-- 1690459-->

Podrá configurar el equipo selector para proteger los dispositivos de las aplicaciones mediante el control del origen de descarga de las aplicaciones. Podrá configurar los orígenes de descarga siguientes: **Mac App Store**, **Mac App Store y desarrolladores identificados** o **Cualquier lugar**. También podrá configurar si los usuarios pueden instalar una aplicación presionando Control y haciendo clic para invalidar estos controles del equipo selector.

Esta configuración se puede encontrar en **Configuración del dispositivo** -> **Crear perfil** -> **macOS** -> **Endpoint Protection**.

### <a name="configure-the-mac-application-firewall----1690461---"></a>Configuración del firewall de aplicaciones Mac <!-- 1690461 -->

Podrá configurar el firewall de aplicaciones Mac. Puede usarlo para controlar las conexiones en cada aplicación, en lugar de en cada puerto. Esto facilita la capacidad de aprovechar las ventajas de protección de firewall y ayuda a evitar que aplicaciones no deseadas tomen el control de los puertos de red abiertos para las aplicaciones legítimas.
 
Esta característica se puede encontrar en **Configuración del dispositivo** -> **Crear perfil** -> **macOS** -> **Endpoint Protection**.

Una vez que habilite la opción Firewall, puede configurar el firewall con dos estrategias:

- Bloqueo de todas las conexiones entrantes

   Puede bloquear todas las conexiones entrantes para los dispositivos de destino. Si decide hacerlo, las conexiones entrantes se bloquearán para todas las aplicaciones. 

- Permiso o bloqueo de aplicaciones específicas

   Puede permitir o bloquear la recepción de conexiones entrantes en aplicaciones específicas. También puede habilitar el modo sigiloso para impedir respuestas a las solicitudes de sondeo.
 
#### <a name="more-information"></a>Más información

- Bloqueo de todas las conexiones entrantes

   Esto impide que todos los servicios de uso compartido (como Uso compartido de archivos y Pantalla compartida) reciban conexiones entrantes. Los servicios del sistema a los que se sigue permitiendo recibir conexiones entrantes son los siguientes:
   - configd: implementa DHCP y otros servicios de configuración de red
   - mDNSResponder: implementa Bonjour
   - racoon: implementa IPSec

   Para usar los servicios de uso compartido, asegúrese de que **Conexiones entrantes** esté establecido en **Sin configurar**, y no en **Bloquear**.

- Modo sigiloso

   Habilite esta opción para impedir que el equipo responda a las solicitudes de sondeo. El equipo seguirá respondiendo a las solicitudes entrantes de las aplicaciones autorizadas. Las solicitudes inesperadas, como ICMP (ping), se ignoran.
 

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Actualización de la experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android <!--1631531 -->

Actualizaremos la experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android de acuerdo con los procedimientos recomendados para las aplicaciones Android. En los próximos meses actualizaremos la aplicación Portal de empresa para Android para dividir el elemento de menú **Ayuda y comentarios** en los elementos de menú independientes **Ayuda** y **Enviar comentarios**. En la página **Ayuda** se incluirá una sección **Preguntas más frecuentes** y un botón **Soporte por correo electrónico** para permitir a los usuarios finales cargar registros a Microsoft y enviar al equipo de soporte técnico de la empresa un correo electrónico en el que se describa el problema. **Enviar comentarios** llevará al usuario a través de un proceso estándar de envío de comentarios de Microsoft, en el que se le pedirá elegir entre "Me gusta algo", "No me gusta algo" o "Tengo una idea".

### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Categorías personalizadas para libros electrónicos comprados a través de un programa de compras por volumen (VPP) <!-- 1488911 -->
Podrá crear categorías personalizadas de libros electrónicos y, después, asignar libros electrónicos de VPP a esas categorías personalizadas. Después, los usuarios finales podrán ver las categorías de libros electrónicos recién creadas y los libros asignados a las categorías.

#### <a name="company-portal-for-android-visual-updates---976944---"></a>Actualizaciones visuales de Portal de empresa para Android <!--976944 -->

Actualizaremos la aplicación Portal de empresa para Android para seguir las directrices de [Material Design](https://material.io/) de Android. Publicaremos imágenes de los iconos nuevos en el artículo [What's new in app UI](whats-new-app-ui.md) (Novedades en la interfaz de usuario de la aplicación) cuando se publique la aplicación. 

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Compatibilidad móvil de Edge para directivas de Intune App Protection <!-- 1817882 -->

El navegador Microsoft Edge para dispositivos móviles admitirá las directivas de protección de aplicaciones definidas en Intune.

### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763-eeready--"></a>Uso de un nombre completo como sujeto de un certificado SCEP <!--2221763 eeready-->
Cuando se crea un perfil de certificado SCEP, hay que indicar el nombre del sujeto. Podrá usar el nombre completo como sujeto. En **Nombre del sujeto**, seleccione **Personalizado** y, después, escriba `CN={{OnPrem_Distinguished_Name}}`. Para usar la variable `{{OnPrem_Distinguished_Name}}`, no olvide sincronizar el atributo de usuario `onpremisesdistingishedname` por medio de [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con Azure AD. 

### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837-eeready--"></a>Los dispositivos iOS solicitan un PIN cada 15 minutos <!--1550837 eeready-->
Después de poner en marcha una directiva de configuración o cumplimiento en un dispositivo iOS, cada 15 minutos se pedirá al usuario que establezca un PIN, y se le seguirá pidiendo hasta que se establezca un PIN.

### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983-eeready--"></a>Permitir el uso compartido de contactos a través de Bluetooth: Android for Work <!--1098983 eeready-->
Android impide de forma predeterminada que los contactos del perfil del trabajo se sincronicen con dispositivos Bluetooth. Como consecuencia, los contactos del perfil de trabajo no aparecen en la identificación de llamadas en los dispositivos Bluetooth.

Habrá una nueva opción en **Android for Work** > **Restricciones de dispositivos** > **Configuración del perfil de trabajo**:
- Uso compartido de contactos a través de Bluetooth

El administrador de Intune puede configurar esta opción para permitir el uso compartido de contactos. Esto resulta útil para emparejar un dispositivo con el dispositivo Bluetooth de un coche que muestra el identificador de llamada cuando se usa el manos libres. Si se habilita, se mostrarán los contactos del perfil de trabajo. Si no, no se mostrarán.

Se aplica a: dispositivos de perfil de trabajo Android con la versión de SO Android 6.0 y versiones más recientes.

### <a name="schedule-your-automatic-updates---1805514---"></a>Programar las actualizaciones automáticas <!--1805514 -->

Intune le permite controlar la instalación de las actualizaciones automáticas por medio de la opción [Anillo de actualización de Windows](windows-update-for-business-configure.md). Podrá programar las actualizaciones recurrentes, así como la semana, el día y la hora en que deben producirse. 

### <a name="disable-checks-on-device-restart---1805490---"></a>Deshabilitar las comprobaciones cuando el dispositivo se reinicia <!--1805490 -->

Intune le permite controlar la [administración de las actualizaciones de software](windows-update-for-business-configure.md). La propiedad **Comprobaciones de reinicio** estará agregada y habilitada de forma predeterminada. Para omitir las comprobaciones típicas que tienen lugar cuando un dispositivo se reinicia (por ejemplo, usuarios activos, niveles de batería, etc.), seleccione **Omitir**. 

<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nuevo gráfico de tendencias sobre errores de inscripción y tabla de motivos de error <!-- 1471783 -->

En la página de información general de inscripción, verá la tendencia de los errores de inscripción y los cinco motivos de error principales. Al hacer clic en un gráfico o una tabla, podrá explorar los detalles para obtener consejos de resolución de problemas y sugerencias de corrección.

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personalice los temas del Portal de empresa con códigos hexadecimales <!--1049561 -->

Podrá personalizar el color del tema en las aplicaciones del Portal de empresa mediante los códigos hexadecimales. Cuando se escriba el código hexadecimal, Intune determinará el color del texto que proporciona el nivel más alto de contraste entre el color del texto y el color de fondo según los [estándares de WCAG 2.0](http://www.w3.org/TR/WCAG20). Puede ver el color del texto y el logotipo de su empresa con el color en **Aplicaciones móviles** > **Portal de empresa**. 

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Nueva configuración de protección de credenciales de Windows Defender agregada a la configuración de endpoint protection<!--1102252 --> 

La nueva opción [Credential Guard de Windows Defender] (https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) estará incluida en **Configuración de dispositivo** > **Perfiles** > **Endpoint Protection**. Se agregará la configuración siguiente: 

- Nivel de seguridad de la plataforma: especifique si el nivel de seguridad de plataforma está habilitado en el siguiente reinicio. La seguridad basada en la virtualización requiere el arranque seguro. Opcionalmente, la seguridad basada en la virtualización se puede habilitar con el uso de protecciones de acceso directo a memoria (DMA). Las protecciones de DMA requieren compatibilidad con el hardware y solo se habilitarán en dispositivos configurados correctamente.
- Seguridad basada en la virtualización: especifique si está habilitada la seguridad basada en la virtualización en el siguiente reinicio. 
- Credential Guard de Windows Defender: active Credential Guard con seguridad basada en la virtualización para ayudar a proteger las credenciales en el siguiente reinicio cuando están activados tanto el nivel de seguridad de la plataforma con arranque seguro como la seguridad basada en la virtualización. Las opciones disponibles son **Deshabilitado**, **Habilitado con el bloqueo UEFI**, **Habilitado sin bloqueo** y **No configurado**. 
  - La opción "Deshabilitado" desactiva Credential Guard remotamente si previamente se ha activado con la opción "Habilitado sin bloqueo".

  - La opción "Habilitado con el bloqueo UEFI" garantiza que no se puede deshabilitar Credential Guard con la clave del registro o mediante la directiva de grupo. Para deshabilitar Credential Guard después de usar esta opción, debe establecer la directiva de grupo en "Deshabilitado" y eliminar la funcionalidad de seguridad de cada equipo, con un usuario presente de forma física, para poder borrar la configuración persistente en UEFI. Mientras persista la configuración de UEFI, Credential Guard estará habilitado.

  - La opción "Habilitado sin bloqueo" permite que se deshabilite de forma remota Credential Guard mediante una directiva de grupo. Los dispositivos que usen esta configuración deben ejecutar al menos Windows 10 (versión 1511).

  - La opción "No configurado" deja la configuración de la directiva sin definir. La directiva de grupo no escribe la configuración de directiva en el Registro, por lo que no existe un impacto en los equipos o los usuarios. Si hay una configuración actual en el registro, esta no se modificará.

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Restablecer contraseñas para dispositivos Android O <!-- 1238299 -->
Podrá restablecer las contraseñas para los dispositivos Android O inscritos. Cuando se envía una solicitud de "Restablecer contraseña" en un dispositivo Android O, se establece un nueva contraseña de desbloqueo de dispositivo o un desafío de perfil administrado al usuario actual. La contraseña o el desafío se envía en función de si el dispositivo tiene un propietario del perfil o un propietario de dispositivo y surte efecto de inmediato.

### <a name="local-device-security-option-settings----1251887---"></a>Configuración de opciones de seguridad del dispositivo local <!-- 1251887 -->
Podrá habilitar la configuración de seguridad en dispositivos Windows 10 con los nuevos valores de opción de seguridad del dispositivo local. Encuentre estos valores en la categoría de Endpoint Protection cuando cree una directiva de configuración de dispositivo de Windows 10.

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nueva configuración de impresora para perfiles de educación <!-- 1308900 -->

Para los perfiles de educación, habrá nueva configuración disponible en la categoría **Impresoras**: **Impresoras**, **Impresora predeterminada**, **Agregar nuevas impresoras**. 

### <a name="ios-app-provisioning-configuration----1581650---"></a>configuración de aprovisionamiento de aplicaciones de iOS <!-- 1581650 -->
Podrá asignar perfiles de aprovisionamiento de aplicaciones de iOS para evitar que las aplicaciones expiren mediante la inclusión o exclusión de grupos de seguridad.

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nueva configuración de Protección de aplicaciones de Windows Defender <!-- 1631890 -->

- **Habilitar la aceleración gráfica**

Los administradores pueden habilitar un procesador de gráficos virtuales para la Protección de aplicaciones de Windows Defender. Esta configuración permite que la CPU descargue el procesamiento de gráficos a la vGPU. Esto puede mejorar el rendimiento cuando se trabaja con sitios web con gran cantidad de datos gráficos o se ve un vídeo dentro del contenedor.

- **SaveFilestoHost**

Los administradores podrán habilitar que los archivos pasen de Microsoft Edge ejecutándose en el contenedor al sistema de archivos de host. Al activarlo, permitirá que los usuarios descarguen los archivos de Microsoft Edge en el contenedor al sistema de archivos de host.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusión o exclusión de la asignación de aplicaciones con base en grupos para Android Enterprise <!-- 1813081 -->
Durante la asignación de aplicaciones y después de seleccionar un tipo de asignación, Android Enterprise (anteriormente conocido como Android for Work) es compatible con la funcionalidad de exclusión.

<!-- the following are present prior to 1802 -->

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Destinación de las directivas de cumplimiento a dispositivos en grupos de dispositivos <!--1307012 -->

Podrá destinar las directivas de cumplimiento a usuarios en los grupos de usuarios. Podrá destinar las directivas de cumplimiento a dispositivos en los grupos de dispositivos.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Directivas de protección de aplicaciones  <!-- 679615 -->
Las directivas de Intune App Protection ofrecerán la capacidad de crear directivas predeterminadas globales para habilitar rápidamente la protección en todos los usuarios de todo el inquilino.

### <a name="configure-an-ios-app-pin----1586774---"></a>Configurar un PIN de aplicación iOS <!-- 1586774 -->
Pronto podrá solicitar un PIN para las aplicaciones iOS de destino. En Azure Portal puede configurar el requisito de PIN y la fecha de expiración en días. Para obtener acceso a una aplicación de iOS, se le pedirá al usuario que establezca y use un nuevo PIN. Solo las aplicaciones iOS que tienen habilitada la protección aplicaciones con Intune App SDK serán compatibles con esta característica.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Los sitios web de Azure Active Directory pueden requerir la aplicación Intune Managed Browser y compatibilidad con el inicio de sesión único para Managed Browser (versión preliminar pública) <!-- 710595 -->   
Con Azure Active Directory (Azure AD), podrá restringir el acceso a sitios web en dispositivos móviles a la aplicación Intune Managed Browser. En Managed Browser, los datos del sitio web permanecen seguros y separados de los datos personales del usuario final. Además, Managed Browser admite funciones de inicio de sesión único para sitios protegidos por Azure AD. Al iniciar sesión en Managed Browser, o al usarlo en un dispositivo con otra aplicación administrada por Intune, se permite que Managed Browser tenga acceso a sitios corporativos protegidos por Azure AD sin necesidad de que el usuario escriba sus credenciales. Esta funcionalidad se aplica a sitios como Outlook Web Access (OWA) y SharePoint Online, así como a otros sitios corporativos, como los recursos de intranet a los que se tiene acceso a través de Azure App Proxy.

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>Redireccionamiento de los usuarios de macOS a la nueva aplicación Portal de empresa <!--1380728-->   
Cuando un usuario final inicia sesión en el sitio web del Portal de empresa para inscribir su dispositivo macOS, se le dirigirá a la descarga de la nueva aplicación Portal de empresa para macOS a fin de que complete el proceso. Esto ocurre con los dispositivos macOS que usan OS X El Capitan 10.11 o una versión posterior. 

<!-- the following are present prior to 1709 -->

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensaje de error mejorado cuando un usuario alcanza el número máximo de dispositivos permitidos para la inscripción <!-- 1270370 -->
En lugar de un mensaje de error genérico, los usuarios finales con dispositivos Android ven un mensaje de error descriptivo que requiere acción: "Ya ha inscrito el máximo número de dispositivos permitidos por su administrador de TI. Quite un dispositivo inscrito o reciba ayuda de su administrador de TI".



## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.



### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


