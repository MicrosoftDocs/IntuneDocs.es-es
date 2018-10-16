---
title: 'Novedades de Microsoft Intune en los meses anteriores: Azure | Microsoft Docs'
titlesuffix: ''
description: Revise los anuncios anteriores en la página de novedades de Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8b76ad64395fc8a0ffa5248a6131df2ee287630a
ms.sourcegitcommit: a78c64ea755ef9e261d3b07390493300977b724b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2018
ms.locfileid: "49324801"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Novedades de Microsoft Intune: meses anteriores

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="march-2018"></a>Marzo de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Alertas para aplicaciones de línea de negocio (LOB) iOS a punto de expirar para Microsoft Intune <!-- 748789 -->

En Azure Portal, Intune le avisa de las aplicaciones de línea de negocio iOS que están a punto de expirar. Al cargar una nueva versión de la aplicación de línea de negocio iOS, Intune quita la notificación de expiración de la lista de aplicaciones. Esta notificación de expiración solo está activa para las aplicaciones de línea de negocio iOS recién cargadas. 30 días antes de que expire el perfil de aprovisionamiento de la aplicación LOB iOS, aparece una advertencia. Cuando expira, la alerta cambia a Expirada.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personalice los temas del Portal de empresa con códigos hexadecimales <!--1049561 -->

Puede personalizar el color del tema de las aplicaciones del Portal de empresa mediante códigos hexadecimales. Cuando escribe el código hexadecimal, Intune determina el color del texto que proporciona el nivel más alto de contraste entre el color del texto y el color del fondo. Puede obtener una vista previa del color de texto y el logotipo de la empresa con el color en **Aplicaciones cliente** > **Portal de empresa**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusión o exclusión de la asignación de aplicaciones con base en grupos para Android Enterprise <!-- 1813081 -->

Android Enterprise (anteriormente conocido como Android for Work) admite la inclusión y exclusión de grupos, pero no los grupos integrados creados previamente **Todos los usuarios** y **Todos los dispositivos**. Para obtener más información, vea [Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Administración de dispositivos

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>Exportar todos los dispositivos a archivos CSV en IE, Edge o Chrome <!-- 2258071 -->
En **Dispositivos** > **Todos los dispositivos**, puede **Exportar** los dispositivos a una lista con formato CSV. Los usuarios de Internet Explorer (IE) con >10.000 dispositivos pueden exportar correctamente sus dispositivos a varios archivos. Cada archivo tiene un máximo de 10.000 dispositivos.

Los usuarios de Edge y Chrome con >30.000 dispositivos pueden exportar correctamente sus dispositivos a varios archivos. Cada archivo tiene un máximo de 30.000 dispositivos.

[Administrar dispositivos](device-management.md) proporciona más detalles sobre lo que puede hacer con los dispositivos que administra.

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Nuevas mejoras de seguridad en el servicio de Intune <!-- 1637539 -->   

Se ha incorporado un botón de alternancia en Intune en Azure que los clientes independientes de Intune pueden usar para tratar dispositivos sin ninguna directiva asignada como **Compatible** (característica de seguridad desactivada) o como **No compatible**(característica de seguridad activada). Esto garantiza el acceso a los recursos únicamente después de que se haya evaluado el cumplimiento del dispositivo.

Esta característica afecta al usuario de forma distinta según tenga ya directivas de cumplimiento asignadas o no.

- Si es una cuenta nueva o existente y no tiene ninguna directiva de cumplimiento asignada a los dispositivos, el botón de alternancia se establece automáticamente en **Compatible**. La característica está desactivada como opción predeterminada en la consola. Los usuarios finales no se ven afectados.
- Si es una cuenta existente y tiene algún dispositivo con una directiva de cumplimiento asignada, el botón de alternancia se establece automáticamente en **No compatible**. La característica está activada como opción predeterminada en cuanto se lanza la actualización de marzo.

Si usa directivas de cumplimiento con acceso condicional (CA) y tiene la característica activada, los dispositivos que no tengan asignada como mínimo una directiva de cumplimiento son bloqueados por CA. Los usuarios finales asociados a estos dispositivos y a los que se haya concedido acceso previamente al correo electrónico pierden el acceso a menos que se asigne como mínimo una directiva de cumplimiento a todos los dispositivos.   

Tenga en cuenta que aunque el estado predeterminado del botón de alternancia se muestra en la interfaz de usuario inmediatamente con las actualizaciones de marzo del servicio de Intune, este estado del botón de alternancia no se aplica de inmediato. Los cambios que realice en el botón de alternancia no afectan al cumplimiento del dispositivo hasta la distribución de paquetes piloto a la cuenta para que tenga un botón de alternancia que funcione. Se le informa mediante el centro de mensajes una vez que se terminan de distribuir paquetes piloto a la cuenta. Esto podría tardar unos días después de la actualización del servicio de Intune de marzo.

**Información adicional**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Detección de jailbreak mejorada <!-- 846515 -->

La detección de jailbreak mejorada es una nueva opción de cumplimiento que mejora la forma en que Intune evalúa los dispositivos con Jailbreak. La opción hace que el dispositivo se comunique con Intune con más frecuencia, lo que usa los servicios de ubicación del dispositivo y afecta al uso de la batería.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Restablecer contraseñas para dispositivos Android O <!-- 1238299 -->
Puede restablecer las contraseñas de los dispositivos Android 8.0 inscritos con perfiles de Work. Cuando se envía una solicitud de "Restablecer contraseña" a un dispositivo Android 8.0, se establece una nueva contraseña de desbloqueo de dispositivo o un desafío de perfil administrado al usuario actual. La contraseña o el desafío se envían y se aplican de inmediato.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Destinación de las directivas de cumplimiento a dispositivos en grupos de dispositivos <!--1307012 -->

Puede destinar directivas de cumplimiento a usuarios de grupos de usuarios. Con esta actualización, puede destinar directivas de cumplimiento a dispositivos de grupos de dispositivos. Los dispositivos de destino como parte de grupos de dispositivos no reciben ninguna acción de cumplimiento.

#### <a name="new-management-name-column----1333586---"></a>Nueva columna Nombre de administración <!-- 1333586 -->
 Hay una nueva columna denominada **Nombre de administración** disponible en la hoja de dispositivos. Se trata de un nombre generado automáticamente y que no se puede modificar asignado por cada dispositivo, en función de la fórmula siguiente:
- Nombre predeterminado para todos los dispositivos: <username><em><devicetype></em><enrollmenttimestamp>
- Para dispositivos agregados en masa: <IdentificadorPaquete/IdentificadorPerfil><em><DeviceType></em><EnrollmentTime>

Se trata de una columna opcional en la hoja de dispositivos. No está disponible de forma predeterminada y solo se puede acceder a ella mediante el selector de columnas. El nombre del dispositivo no se ve afectado por esta nueva columna.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>Los dispositivos iOS solicitan un PIN cada 15 minutos <!--1550837 -->
Después de aplicar una directiva de configuración o cumplimiento a un dispositivo iOS, cada 15 minutos se pide al usuario que establezca un PIN, y se le sigue pidiendo hasta que lo hace.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Programar las actualizaciones automáticas <!--1805514 -->
Intune le permite controlar la instalación de las actualizaciones automáticas por medio de la opción [Anillo de actualización de Windows](windows-update-for-business-configure.md). Con esta actualización, puede programar actualizaciones recurrentes, incluidos la semana, el día y la hora.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Uso de un nombre completo como sujeto de un certificado SCEP <!--2221763 -->
Cuando se crea un perfil de certificado SCEP, hay que indicar el nombre del sujeto. Con esta actualización, puede usar el nombre completo como sujeto. En **Nombre del sujeto**, seleccione **Personalizado** y, después, escriba `CN={{OnPrem_Distinguished_Name}}`. Para usar la variable `{{OnPrem_Distinguished_Name}}`, no olvide sincronizar el atributo de usuario `onpremisesdistingishedname` por medio de [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con Azure AD.

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Permitir el uso compartido de contactos a través de Bluetooth: Android for Work <!--1098983 -->
Android impide de forma predeterminada que los contactos del perfil del trabajo se sincronicen con dispositivos Bluetooth. Como consecuencia, los contactos del perfil de trabajo no aparecen en la identificación de llamadas en los dispositivos Bluetooth.

Con esta actualización, hay una nueva opción en **Android for Work** > **Restricciones de dispositivos** > **Configuración del perfil de trabajo**:
- Uso compartido de contactos a través de Bluetooth

El administrador de Intune puede configurar esta opción para permitir el uso compartido de contactos. Esto resulta útil para emparejar un dispositivo con el dispositivo Bluetooth de un coche que muestra el identificador de llamada cuando se usa el manos libres. Si se habilita, se mostrarán los contactos del perfil de trabajo. Si no, no se mostrarán.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>Configuración del equipo selector para controlar el origen de descarga de las aplicaciones macOS <!-- 1690459 -->

Puede configurar el equipo selector para proteger los dispositivos desde las aplicaciones mediante el control del origen de descarga de las aplicaciones. Puede configurar los orígenes de descarga siguientes: **Mac App Store**, **Mac App Store y desarrolladores identificados** o **Cualquier ubicación**. Puede configurar si los usuarios pueden instalar una aplicación al presionar Control+clic para invalidar estos controles del equipo selector.

Esta configuración se puede encontrar en **Configuración del dispositivo** -> **Crear perfil** -> **macOS** -> **Endpoint Protection**.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Configuración del firewall de aplicaciones Mac <!-- 1690461 -->

Puede configurar el firewall de aplicaciones Mac. Puede usarlo para controlar las conexiones en cada aplicación, en lugar de en cada puerto. Esto facilita la capacidad de aprovechar las ventajas de protección de firewall y ayuda a evitar que aplicaciones no deseadas tomen el control de los puertos de red abiertos para las aplicaciones legítimas.

Esta característica se puede encontrar en **Configuración del dispositivo** -> **Crear perfil** -> **macOS** -> **Endpoint Protection**.

Una vez que habilite la opción Firewall, puede configurar el firewall con dos estrategias:

- Bloqueo de todas las conexiones entrantes

   Puede bloquear todas las conexiones entrantes para los dispositivos de destino. Si decide hacerlo, las conexiones entrantes se bloquean para todas las aplicaciones.

- Permiso o bloqueo de aplicaciones específicas

   Puede permitir o bloquear la recepción de conexiones entrantes en aplicaciones específicas. También puede habilitar el modo sigiloso para impedir respuestas a las solicitudes de sondeo.

####  <a name="detailed-error-codes-and-messages----1376342---"></a>Códigos de error y mensajes detallados <!-- 1376342 -->

En la configuración del dispositivo, se pueden ver mensajes y códigos de error más detallados. Este informe detallado muestra la configuración, el estado de esta configuración y los detalles sobre cómo solucionar problemas.

##### <a name="more-information"></a>Más información

- Bloqueo de todas las conexiones entrantes

   Esto impide que todos los servicios de uso compartido (como Uso compartido de archivos y Pantalla compartida) reciban conexiones entrantes. Los servicios del sistema a los que se sigue permitiendo recibir conexiones entrantes son los siguientes:
  - configd: implementa DHCP y otros servicios de configuración de red
  - mDNSResponder: implementa Bonjour
  - racoon: implementa IPSec

    Para usar los servicios de uso compartido, asegúrese de que **Conexiones entrantes** esté establecido en **Sin configurar**, y no en **Bloquear**.

- Modo sigiloso

   Habilite esta opción para impedir que el equipo responda a las solicitudes de sondeo. El equipo seguirá respondiendo a las solicitudes entrantes de las aplicaciones autorizadas. Las solicitudes inesperadas, como ICMP (ping), se ignoran.

#### <a name="disable-checks-on-device-restart---1805490---"></a>Deshabilitar las comprobaciones cuando el dispositivo se reinicia <!--1805490 -->
Intune proporciona control para [administrar actualizaciones de software]](windows-update-for-business-configure.md). Con esta actualización, la propiedad <strong>Comprobaciones de reinicio</strong> está disponible y habilitada de forma predeterminada. Para omitir las comprobaciones típicas que tienen lugar cuando un dispositivo se reinicia (por ejemplo, usuarios activos, niveles de batería, etc.), seleccione <strong>Omitir</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Nuevos canales de Windows 10 Insider Preview disponibles para anillos de implementación <!-- 1746293 -->
Ahora tiene la opción de seleccionar los siguientes canales de servicio de Windows 10 Insider Preview al crear un anillo de implementación de Windows 10:
- Compilación de Windows Insider: Rápida
- Compilación de Windows Insider: Lenta
- Versión de lanzamiento de Windows Insider 

Para obtener más información sobre estos canales, vea [Manage Insider Preview Builds](https://insider.windows.com/for-business-organization-admin/) (Administrar compilaciones de Insider Preview).   
Para obtener más información sobre cómo crear canales de implementación en Intune, vea [Manage software updates in Intune](windows-update-for-business-configure.md) (Administrar actualizaciones de software en Intune).

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Nueva configuración de protección contra vulnerabilidades de seguridad de Windows Defender <!-- 1631893 -->

Ya hay disponibles seis nuevas opciones de <strong>reducción de la superficie expuesta a ataques</strong> y funcionalidades ampliadas de <strong>acceso controlado a carpetas: protección de carpetas</strong>. Puede encontrar estas opciones en: Configuración de dispositivo\Perfiles\
Crear perfil\Endpoint protection\Protección contra vulnerabilidades de seguridad de Windows Defender.

#### <a name="attack-surface-reduction"></a>Reducción de la superficie expuesta a ataques

|Nombre de la configuración  |Opciones de configuración  |Descripción  |
|---------|---------|---------|
|Protección de ransomware avanzada|Habilitado, Auditoría, No configurado|Usar protección ransomware intensa.|
|Marcar el robo de credenciales desde el subsistema de autoridad de seguridad local de Windows|Habilitado, Auditoría, No configurado|Marcar el robo de credenciales desde el subsistema de autoridad de seguridad local de Windows (lsass.exe).|
|Creación del proceso desde comandos PSExec y WMI|Bloquear, Auditoría, No configurado|Bloquear creaciones del proceso que se originan desde comandos PSExec y WMI.|
|Procesos que no son de confianza y sin firma que se ejecutan desde una unidad USB|Bloquear, Auditoría, No configurado|Bloquear los procesos que no son de confianza y sin firma que se ejecutan desde una unidad USB.|
|Archivos ejecutables que no cumplen unos criterios de uso habitual, edad o lista de confianza|Bloquear, Auditoría, No configurado|Bloquear la ejecución de los archivos ejecutables a menos que cumplan unos criterios de uso habitual, edad o lista de confianza.|

#### <a name="controlled-folder-access"></a>Acceso controlado a carpetas

|              Nombre de la configuración               |                                                              Opciones de configuración                                                              | Descripción |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protección de carpetas (ya implementado) | No configurado, Habilitar, Solo auditoría (ya implementado)<br><br> <strong>Nuevo</strong><br>Impedir la modificación del disco, Auditar la modificación del disco |             |

Proteger los archivos y carpetas frente a cambios no autorizados de aplicaciones hostiles.<br><br>**Habilitar**: impedir que las aplicaciones que no son de confianza modifiquen o eliminen archivos en carpetas protegidas y que escriban en los sectores de disco.<br><br>
**Solo impedir la modificación del disco**:<br>Impedir que las aplicaciones que no son de confianza escriban en los sectores de disco. Las aplicaciones que no son de confianza todavía podrán modificar o eliminar archivos en las carpetas protegidas.|

### <a name="intune-apps"></a>Aplicaciones de Intune

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Los sitios web de Azure Active Directory pueden requerir la aplicación Intune Managed Browser y compatibilidad con el inicio de sesión único para Managed Browser (versión preliminar pública) <!-- 710595 -->

Con Azure Active Directory (Azure AD), ya puede restringir el acceso a sitios web en dispositivos móviles para la aplicación Intune Managed Browser. En Managed Browser, los datos del sitio web permanecen seguros y separados de los datos personales del usuario final. Además, Managed Browser admite funciones de inicio de sesión único para sitios protegidos por Azure AD. Al iniciar sesión en Managed Browser, o al usarlo en un dispositivo con otra aplicación administrada por Intune, se permite que Managed Browser tenga acceso a sitios corporativos protegidos por Azure AD sin necesidad de que el usuario escriba sus credenciales. Esta funcionalidad se aplica a sitios como Outlook Web Access (OWA) y SharePoint Online, así como a otros sitios corporativos, como los recursos de intranet a los que se tiene acceso a través de Azure App Proxy. Para obtener más información, consulte [Controles de acceso en el acceso condicional de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Actualizaciones visuales de la aplicación Portal de empresa para Android <!--976944 -->

Hemos actualizado la aplicación Portal de empresa para Android para seguir las directrices de [Material Design](https://material.io/) de Android. Puede ver las imágenes de los iconos nuevos en el artículo [Novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md).

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Mejora de la inscripción de Portal de empresa <!-- 1874230 eeready-->
Los usuarios que inscriben un dispositivo mediante el Portal de empresa en Windows 10, compilación 1703 y versiones posteriores, ahora pueden realizar el primer paso de la inscripción sin salir de la aplicación.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens y Surface Hub ahora aparecen en las listas de dispositivos <!--1725868 -->
Se ha agregado compatibilidad para mostrar los dispositivos HoloLens y Surface Hub inscritos en Intune en la aplicación Portal de empresa para Android.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Categorías personalizadas para libros electrónicos comprados a través de un programa de compras por volumen (VPP) <!-- 1488911 -->
Puede crear categorías personalizadas de libros electrónicos y, después, asignar libros electrónicos de VPP a esas categorías personalizadas. Después, los usuarios finales podrán ver las categorías de libros electrónicos recién creadas y los libros asignados a las categorías. Para obtener más información, vea [Administración de aplicaciones y libros comprados por volumen con Microsoft Intune](vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>Cambios de compatibilidad con la opción Enviar comentarios de la aplicación Portal de empresa para Windows <!-- 2070166 -->
A partir del 30 de abril de 2018 la opción **Enviar comentarios** de la aplicación Portal de empresa para Windows solo funcionará en dispositivos que ejecuten la Actualización de aniversario de Windows 10 (1607) y versiones posteriores. La opción Enviar comentarios ya no se admite cuando se usa la aplicación Portal de empresa para Windows con:  
- Windows 10, versión 1507  
- Windows 10, versión 1511  
- Windows Phone 8,1 

Si su dispositivo ejecuta Windows 10 RS1 o una versión posterior, descargue de la tienda la versión más reciente de la aplicación Portal de empresa para Windows. Si ejecuta una versión no compatible, siga enviando los comentarios a través de los canales siguientes: 
- La aplicación Concentrador de comentarios en Windows 10
- Un correo electrónico a WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nueva configuración de Protección de aplicaciones de Windows Defender <!-- 1631890 -->

- **Habilitar la aceleración gráfica**: los administradores pueden habilitar un procesador de gráficos virtuales para Protección de aplicaciones de Windows Defender. Esta configuración permite que la CPU descargue el procesamiento de gráficos a la vGPU. Esto puede mejorar el rendimiento cuando se trabaja con sitios web con gran cantidad de datos gráficos o se ve un vídeo dentro del contenedor.

- **SaveFilestoHost**: los administradores pueden habilitar que los archivos pasen de Microsoft Edge ejecutándose en el contenedor al sistema de archivos de host. Su activación permite que los usuarios descarguen archivos de Microsoft Edge en el contenedor al sistema de archivos de host.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>Destino de directivas de protección de MAM en función del estado de administración <!-- 1665993 -->
Puede destinar las directivas de MAM en función del estado de administración del dispositivo:
- **Dispositivos Android**: puede tener como destino dispositivos no administrados, dispositivos administrados con Intune y perfiles de Android Enterprise administrados con Intune (anteriormente Android for Work).
- **Dispositivos iOS**: puede tener como destino dispositivos no administrados (solo MAM) o dispositivos administrados con Intune.

    > [!NOTE]
    > - La compatibilidad de iOS con esta funcionalidad se ha ido lanzando a lo largo de abril de 2018.

Para obtener más información, vea [Target app protection policies based on device management state](app-protection-policies.md) (Destinar directivas de protección de aplicaciones en función del estado de administración del dispositivo).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Mejoras en el lenguaje de la aplicación Portal de empresa para Windows <!-- 1683758 -->
Se ha mejorado el lenguaje del Portal de empresa para Windows 10 para que sea más fácil de usar y más específico para la empresa. Para ver algunas imágenes de ejemplo de lo que se ha hecho, vea [Novedades en la UI de la aplicación](whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>Nuevas adiciones a los documentos sobre privacidad del usuario <!-- 1440709 -->
Como parte del esfuerzo por proporcionar a los usuarios finales más control sobre sus datos y su privacidad, se han publicado actualizaciones de los documentos que explican cómo ver y quitar datos almacenados localmente por las aplicaciones del Portal de empresa. Puede encontrar estas actualizaciones en:

- **Android**: [Cómo anular la inscripción del dispositivo Android de Intune](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android, si el usuario ha rechazado los términos de uso**: [Anular la inscripción del dispositivo si ha rechazado los "Términos de uso"](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS**: [Anular la inscripción del dispositivo iOS de Intune](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows**: [Anular la inscripción del dispositivo Windows de Intune](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="february-2018"></a>Febrero de 2018

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Compatibilidad de Intune con varias cuentas del programa del Programa de inscripción de dispositivos (DEP) de Apple o de Apple School Manager (ASM) <!-- 747685 -->

Intune ahora admite la inscripción de dispositivos de hasta 100 cuentas distintas del [Programa de inscripción de dispositivos de Apple](device-enrollment-program-enroll-ios.md) o de [Apple School Manager](apple-school-manager-set-up-ios.md). Cada token cargado puede administrarse por separado para los perfiles y los dispositivos de inscripción. Es posible asignar un perfil de inscripción diferente para cada token de DEP/School Manager. Si se cargan varios tokens de School Manager, solo pueden compartirse de uno en uno con Microsoft School Data Sync.

Tras la migración, la versión beta de las API Graph y los scripts publicados para la administración de Apple DEP o ASM en Graph ya no funcionará. Las nuevas versiones beta de las API Graph están en desarrollo y se publicarán después de la migración.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Vea las restricciones de inscripción por usuario <!-- 1634444 eeready wnready -->
En la hoja **Solución de problemas**, ahora puede ver las [restricciones de inscripción](enrollment-restrictions-set.md) que están en vigor para cada usuario si selecciona **Restricciones de inscripción** en la lista **Asignaciones**.

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

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>compatibilidad del Portal de empresa de macOS para las inscripciones que usen el administrador de inscripciones de dispositivos <!-- 1352411 -->

Los usuarios ya pueden usar el administrador de inscripciones de dispositivos cuando se inscriban con Portal de empresa para macOS.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Informes de estado de mantenimiento y de estado de amenazas de Windows defender <!--854704 -->

Conocer el estado de mantenimiento de Windows Defender es clave para la administración de equipos de Windows.  Con esta actualización, Intune agrega nuevos informes y acciones para el estado y el mantenimiento del agente de Windows Defender. Con un informe de resumen de estado en la [carga de trabajo Cumplimiento de dispositivos](compliance-policy-monitor.md), puede ver los dispositivos que necesitan alguna de las acciones siguientes:
- actualización de la firma
- Reiniciar
- intervención manual
- examen completo
- otros estados del agente que requieren intervención

Un informe de obtención de detalles para cada categoría de estado muestra los equipos individuales que requieren atención o identificados como **limpios**.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Nueva configuración de privacidad para las restricciones de dispositivos <!--1308926 -->
Hay [dos nuevas opciones de privacidad](device-restrictions-windows-10.md#privacy) disponibles para los dispositivos:
- **Publicar las actividades del usuario**: establezca esta propiedad en **Bloquear** para evitar experiencias compartidas y la detección de recursos usados recientemente en el selector de tareas.
- **Solo actividades locales**: establezca esta propiedad en **Bloquear** para evitar experiencias compartidas y la detección de recursos usados recientemente en el selector de tareas según la actividad local únicamente.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Nueva configuración para el explorador Microsoft Edge <!--1469166 -->
Hay [dos nuevas opciones](device-restrictions-windows-10.md#edge-browser) disponibles para dispositivos con el explorador Microsoft Edge: **Ruta de acceso al archivo de favoritos** y **Cambios a Favoritos**.

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="protocol-exceptions-for-applications---1035509---"></a>Excepciones de protocolo para las aplicaciones <!--1035509 -->

Puede crear excepciones a la directiva de transferencia de datos de la administración de aplicaciones móviles (MAM) de Intune para abrir determinadas aplicaciones no administradas. Dichas aplicaciones deben ser de confianza para el departamento de TI. Aparte de las excepciones que cree, la transferencia de datos sigue estando limitada a las aplicaciones que se administran mediante Intune cuando la directiva de transferencia de datos se establece en **Managed apps only** (Solo aplicaciones administradas). Puede crear las restricciones mediante protocolos (iOS) o paquetes (Android).

Por ejemplo, puede agregar el paquete de WebEx como una excepción a la directiva de transferencia de datos de MAM. Esto permitirá que los vínculos de WebEx en un mensaje de correo electrónico de Outlook administrado se abran directamente en la aplicación de WebEx. Se seguirá restringiendo la transferencia de datos en otras aplicaciones no administradas. Para obtener más información, consulte [Data transfer policy exceptions for apps](app-protection-policies-exception.md) (Excepciones de la directiva de transferencia de datos para aplicaciones).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Datos cifrados de Windows Information Protection (WIP) en los resultados de la búsqueda de Windows <!-- 1469193 -->
Un parámetro de configuración de la directiva de Windows Information Protection (WIP) le permite controlar si los datos cifrados por WIP se incluyen en los resultados de la búsqueda de Windows. Para establecer esta opción de la directiva de protección de aplicaciones, seleccione **Permitir que el indizador de Windows Search busque elementos cifrados** en la **Configuración avanzada** de la directiva de Windows Information Protection. La directiva de protección de aplicaciones debe establecerse en la plataforma *Windows 10* y la directiva de aplicación **Estado de inscripción** debe establecerse en **Con inscripción**. Para obtener más información, consulte [Permitir que el indizador de Windows Search busque elementos cifrados](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configurar una aplicación MSI móvil de auto-actualización <!-- 1740840 -->
Puede configurar una aplicación móvil MSI con auto-actualización para que omita el proceso de comprobación de versión. Esta capacidad resulta útil para evitar que se produzca una condición de carrera. Por ejemplo, este tipo de condición de carrera podría producirse cuando la aplicación que el desarrollador de aplicaciones actualiza automáticamente también la estuviera actualizando Intune. Ambos podrían tratar de aplicar una versión de la aplicación en un cliente de Windows, lo que podría crear un conflicto. Para estas aplicaciones MSI que se actualizan automáticamente, puede configurar el valor **Omitir la versión de la aplicación** en la hoja **Información de la aplicación**. Cuando se cambia esta configuración a **Sí**, Microsoft Intune omite la versión de la aplicación instalada en el cliente de Windows.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Conjuntos de licencias de aplicaciones relacionadas admitidas en Intune <!-- 1864117 -->
Intune en Azure Portal ya admite conjuntos de licencias de aplicaciones relacionadas como un elemento de aplicación único en la interfaz de usuario. Además, las aplicaciones con licencia sin conexión sincronizadas desde Microsoft Store para Empresas se consolidarán en una entrada de aplicación única y los detalles de implementación de los paquetes individuales se migrarán a la entrada única. Para ver los conjuntos de licencias de aplicaciones relacionadas en Azure Portal, seleccione **Licencias de aplicación** en la hoja **Aplicaciones cliente**.

### <a name="device-configuration"></a>Configuración de los dispositivos
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Extensiones de archivo de Windows Information Protection (WIP) para el cifrado automático <!-- 1463582 -->
Un valor de la directiva de Windows Information Protection (WIP) le permite ahora especificar qué extensiones de archivo se cifran automáticamente al copiar desde un recurso compartido del bloque de mensajes del servidor (SMB) dentro de los límites corporativos, como se define en la directiva de WIP.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Configurar las opciones de la cuenta del recurso para Surface Hubs

Ya puede configurar de forma remota las opciones de la cuenta del recurso para Surface Hubs.

Una instancia de Surface Hub usa la cuenta del recurso para autenticarse en Skype o Exchange y así poder unirse a una reunión.
Deberá crear una cuenta del recurso única para que Surface Hub pueda aparecer en la reunión como la sala de conferencias.
Por ejemplo, una cuenta del recurso como **Sala de conferencias B41/6233**.

> [!NOTE]
> - Si deja campos en blanco invalidará los atributos configurados previamente en el dispositivo.
>
> - Las propiedades de la cuenta del recurso pueden cambiar dinámicamente en Surface Hub. Por ejemplo, si el cambio de contraseñas está activado. Por lo tanto, es posible que los valores de la consola de Azure tarden algún tiempo en reflejar la realidad en el dispositivo.
>
>   Para entender lo que está configurado actualmente en Surface Hub, se puede incluir la información de la cuenta del recurso en el inventario de hardware (que ya tiene un intervalo de 7 días) o como propiedades de solo lectura. Para mejorar la precisión después de llevar a cabo la acción remota, puede obtener el estado de los parámetros inmediatamente después de ejecutar la acción para actualizar la cuenta o los parámetros en Surface Hub.

##### <a name="attack-surface-reduction"></a>Reducción de la superficie expuesta a ataques

|Nombre de la configuración  |Opciones de configuración  |Descripción  |
|---------|---------|---------|
|Ejecución de contenido ejecutable protegido por contraseña del correo electrónico|Bloquear, Auditoría, No configurado|Evitar que se ejecuten los archivos ejecutables protegidos por contraseña descargados a través del correo electrónico.|
|Protección de ransomware avanzada|Habilitado, Auditoría, No configurado|Usar protección ransomware intensa.|
|Marcar el robo de credenciales desde el subsistema de autoridad de seguridad local de Windows|Habilitado, Auditoría, No configurado|Marcar el robo de credenciales desde el subsistema de autoridad de seguridad local de Windows (lsass.exe).|
|Creación del proceso desde comandos PSExec y WMI|Bloquear, Auditoría, No configurado|Bloquear creaciones del proceso que se originan desde comandos PSExec y WMI.|
|Procesos que no son de confianza y sin firma que se ejecutan desde una unidad USB|Bloquear, Auditoría, No configurado|Bloquear los procesos que no son de confianza y sin firma que se ejecutan desde una unidad USB.|
|Archivos ejecutables que no cumplen unos criterios de uso habitual, edad o lista de confianza|Bloquear, Auditoría, No configurado|Bloquear la ejecución de los archivos ejecutables a menos que cumplan unos criterios de uso habitual, edad o lista de confianza.|

##### <a name="controlled-folder-access"></a>Acceso controlado a carpetas

|              Nombre de la configuración               |                                                              Opciones de configuración                                                              | Descripción |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protección de carpetas (ya implementado) | No configurado, Habilitar, Solo auditoría (ya implementado)<br><br> <strong>Nuevo</strong><br>Impedir la modificación del disco, Auditar la modificación del disco |             |

Proteger los archivos y carpetas frente a cambios no autorizados de aplicaciones hostiles.<br><br>**Habilitar**: impedir que las aplicaciones que no son de confianza modifiquen o eliminen archivos en carpetas protegidas y que escriban en los sectores de disco.<br><br>
**Solo impedir la modificación del disco**:<br>Impedir que las aplicaciones que no son de confianza escriban en los sectores de disco. Las aplicaciones que no son de confianza todavía podrán modificar o eliminar archivos en las carpetas protegidas.|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Adiciones a la configuración de seguridad del sistema para las directivas de cumplimiento de Windows 10 y posteriores <!--1704133-->

Ya hay disponibles adiciones a la configuración de cumplimiento de Windows 10, incluida la necesidad del Firewall y el Antivirus de Windows Defender.

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Compatibilidad con aplicaciones sin conexión desde la Tienda Microsoft para Empresas <!--1222672-->
Las aplicaciones sin conexión que ha adquirido en Microsoft Store para Empresas ahora se sincronizan con Azure Portal. Puede implementar estas aplicaciones en grupos de usuarios o dispositivos. Las aplicaciones sin conexión se instalan mediante Intune, no Microsoft Store.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Impedir que los usuarios finales agreguen o quiten cuentas manualmente en el perfil de trabajo <!-- 1728700 -->

Al implementar la aplicación Gmail en un perfil de Android for Work, puede impedir que los usuarios finales agreguen o quiten cuentas en el perfil de trabajo mediante la opción de configuración **Agregar y quitar cuentas** del perfil de restricciones del dispositivo Android for Work.


## <a name="january-2018"></a>Enero de 2018

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

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>Puede asignar una directiva de configuración de aplicación a grupos mediante asignaciones de inclusión o exclusión <!-- 1480316 -->

Puede asignar una directiva de configuración de aplicación a un grupo de usuarios y dispositivos mediante una combinación de asignaciones de inclusión y exclusión. Las asignaciones se pueden elegir como una selección personalizada de grupos o como un grupo virtual. Un grupo virtual puede incluir **Todos los usuarios**, **Todos los dispositivos** o **Todos los usuarios + todos los dispositivos**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Compatibilidad con una directiva de actualización de la edición de Windows 10   <!-- 903672(archived), 1119689 -->  
Puede crear una directiva de actualización de la edición de Windows 10 que actualice los dispositivos con Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education y Windows 10 Professional Education N. Para obtener más información sobre las actualizaciones de la edición de Windows 10, vea [Configuración de actualizaciones de la edición de Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Directivas de acceso condicional de Intune solo disponibles en Azure Portal <!-- 1737088 1634311 -->

A partir de esta versión, deberá configurar y administrar las directivas de acceso condicional en [Azure Portal](https://portal.azure.com), en **Azure Active Directory** > **Acceso condicional**. Para su comodidad, también puede acceder a esta hoja desde Intune, en Azure Portal, en **Intune** > **Acceso condicional**.

#### <a name="updates-to-compliance-emails---1637547---"></a>Actualizaciones de los correos electrónicos sobre compatibilidad <!--1637547 -->

Cuando se envía un correo electrónico para informar de un dispositivo no compatible, se incluyen detalles sobre los dispositivos no compatibles.

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Nueva funcionalidad para la acción "Resolver" en dispositivos Android<!--1583480-->

La aplicación Portal de empresa para Android expande la acción "Resolver" para la opción **Actualizar configuración del dispositivo** para resolver [problemas con el cifrado del dispositivo](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Bloqueo remoto disponible en la aplicación del Portal de empresa para Windows 10 <!--676506-->
Los usuarios finales ya pueden bloquear de forma remota sus dispositivos desde la aplicación del Portal de empresa para Windows 10. No se mostrará para el dispositivo local que usen activamente.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Resolución más sencilla de los problemas de compatibilidad de la aplicación Portal de empresa para Windows 10 <!--676546-->
Los usuarios finales que tengan dispositivos Windows podrán seleccionar el motivo de no compatibilidad en la aplicación Portal de empresa. Cuando sea posible, se les llevará directamente a la ubicación correcta de la aplicación de configuración para poder resolver el problema.

## <a name="december-2017"></a>Diciembre de 2017

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

Hemos agregado una nueva característica que permite bloquear los cambios de fecha y hora en los dispositivos Samsung Knox. Puede encontrarla en **Perfiles de configuración de dispositivo** > **Device restrictions (Android)**(Restricciones de dispositivos [Android]) > **General**.

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
Ahora podrá instalar aplicaciones de Office en dispositivos macOS. Este nuevo tipo de aplicación le permitirá instalar Word, Excel, PowerPoint, Outlook y OneNote. Estas aplicaciones también incluyen Microsoft AutoUpdater (MAU) para ayudar a mantener aplicaciones seguras y actualizadas.

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Eliminación de un token del programa de compras por volumen de iOS <!-- 820879 -->
Puede eliminar el token del programa de compras por volumen (VPP) de iOS con la consola. Esto puede resultar necesario cuando tiene instancias duplicadas de un token de VPP.

### <a name="intune-apps"></a>Aplicaciones de Intune


### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>Limitación de la nueva colección de entidades "Usuario actual" a los datos de los usuarios activos actualmente <!-- 1667026 -->

La colección de entidades **Usuarios** muestra todos los usuarios de Azure Active Directory (Azure AD) con licencias asignadas en la empresa. Por ejemplo, es posible que durante el último mes se haya agregado a un usuario a Intune y, luego, se haya eliminado. A pesar de que no esté presente a la hora de generar el informe, el usuario en cuestión y su estado sí que figuran en los datos. Una opción podría ser crear un informe que incluya el historial relativo a la duración de la presencia del usuario en sus datos.

Por otro lado, la nueva colección de entidades **Usuario actual** solo contiene los usuarios que no se hayan eliminado. En otras palabras, la colección de entidades **Usuario actual** solo contiene los usuarios que estén activos actualmente. Para obtener más información sobre la colección de entidades **Usuario actual**, consulte [Referencia de la entidad de usuario actual](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>Actualización de las API Graph <!-- 1736360 -->

En esta versión, hemos actualizado algunas de las API Graph para Intune que están en versión beta. Consulte el [registro de cambios de API Graph](https://developer.microsoft.com/graph/docs/concepts/changelog) mensual para obtener más información.

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune admite aplicaciones denegadas de Windows Information Protection (WIP) <!-- 1479103 -->
En Intune puede especificar aplicaciones denegadas. Si una aplicación queda denegada, se la bloquea para que no pueda acceder a la información de la empresa, es decir, lo contrario a la lista de aplicaciones permitidas. Para obtener más información, consulte [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Recomendación de lista de aplicaciones denegadas para Windows Information Protection).


## <a name="november-2017"></a>Noviembre de 2017

### <a name="troubleshoot-enrollment-issues-----746324---"></a>Solución de problemas de inscripción <!-- 746324 -->

En el área de trabajo **Solución de problemas** ahora se muestran los problemas de inscripción del usuario. Los detalles del problema y los pasos de corrección sugeridos pueden ayudar a los administradores y a los operadores del departamento de soporte técnico a solucionar los problemas. Ciertos problemas de inscripción no se capturan, y es posible que no se sugieran correcciones para algunos errores.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restricciones de inscripción asignada a grupos <!-- 747598 -->

Como administrador de Intune, ahora puede [crear restricciones de inscripción personalizadas de tipo de dispositivo y de límite de dispositivos para grupos de usuarios](enrollment-restrictions-set.md).

Azure Portal de Intune permite crear un máximo de 25 instancias de cada tipo de restricción que pueden asignarse luego a grupos de usuarios. Las restricciones asignadas por grupo invalidan las restricciones predeterminadas.

Todas las instancias de un tipo de restricción se mantienen en una lista ordenada de forma estricta. Este orden define un valor de prioridad para la resolución de conflictos. Un usuario afectado por más de una instancia de la restricción solo está limitado por la instancia con el valor de prioridad más alto. Para cambiar la prioridad de una determinada instancia, arrástrela a una posición diferente en la lista.

Esta funcionalidad se publicará con la migración de la configuración de Android for Work desde el menú de inscripción de Android for Work al menú de restricciones de inscripción. Puesto que esta migración puede tardar varios días, la versión de noviembre puede afectar primero a otras partes de su cuenta antes de habilitar la asignación de grupo para las restricciones de inscripción.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Compatibilidad con varios conectores de Servicio de inscripción de dispositivos de red (NDES) <!-- 1528104 -->

NDES permite que los dispositivos móviles que se ejecutan sin credenciales de dominio puedan obtener certificados a través del Protocolo de inscripción de certificados simple (SCEP).
Con esta actualización, se admiten varios conectores NDES.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Administración independiente de dispositivos Android for Work y dispositivos Android <!-- 1490731 EEready-->

Intune admite la administración de inscripciones de dispositivos Android for Work independientemente de la plataforma Android. Esta configuración se administra en **Inscripción de dispositivos** > **Restricciones de inscripción** > **Restricciones de tipo de dispositivo**. (Anteriormente se encontraban bajo **Inscripción de dispositivos** > **Inscripción en Android for Work** > **Configuración de la inscripción de Android for Work**).

De forma predeterminada, la configuración de los dispositivos Android for Work es igual que la configuración de los dispositivos Android. Sin embargo, dejará de ser así tras modificar la configuración de Android for Work.

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

### <a name="google-play-protect-support-on-android----908720---"></a>Compatibilidad con Google Play Protect en Android <!-- 908720 -->

Con el lanzamiento de Android Oreo, Google presenta un conjunto de características de seguridad denominado Google Play Protect que permite a los usuarios y las organizaciones ejecutar aplicaciones e imágenes de Android seguras. Intune ya admite las características de Google Play Protect, incluida la atestación remota de SafetyNet. Los administradores pueden establecer requisitos para directivas de cumplimiento que exijan que Google Play Protect esté configurado y en buen estado.
La opción **SafetyNet device attestation** (Atestación de dispositivo SafetyNet) requiere que el dispositivo se conecte con un servicio de Google para comprobar que se encuentra en buen estado y no está en riesgo. Los administradores también pueden establecer una opción en el perfil de configuración de Android for Work para requerir que se comprueben las aplicaciones instaladas por los servicios de Google Play. Si un dispositivo no es compatible con los requisitos de Google Play Protect, el acceso condicional puede impedir que los usuarios accedan a los recursos corporativos.

- Obtenga información sobre la [Creación de una directiva de cumplimiento de dispositivos para habilitar Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocolo de texto permitido en aplicaciones administradas <!-- 1414050  -->

Las aplicaciones administradas por Intune App SDK pueden enviar mensajes SMS.


### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>Actualización del informe de instalación de aplicaciones para incluir el estado Instalación pendiente <!-- 1249446 -->  

El informe **Estado de instalación de la aplicación**, accesible para todas las aplicaciones a través de la lista **Aplicación** de la carga de trabajo **Aplicaciones cliente**, contiene ahora un recuento **Instalación pendiente** para usuarios y dispositivos.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API de inventario de aplicaciones iOS 11 para la detección de amenazas en dispositivos móviles <!-- 1391759 -->

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

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Migración de dispositivos y usuarios de MDM híbrida a Intune independiente <!-- 1463747 wnready -->
Ya hay disponibles nuevos procesos y herramientas para mover usuarios y sus dispositivos de MDM híbrida a Intune en Azure Portal, lo que le permitirá llevar a cabo las tareas siguientes:
- Copiar directivas y perfiles de la consola de Configuration Manager a Intune en Azure Portal
- Mover un subconjunto de usuarios a Intune en Azure Portal conservando el resto en MDM híbrida
- Migrar dispositivos a Intune en Azure Portal sin tener que volver a inscribirlos

Para obtener más información, consulte [Migración de dispositivos y usuarios de MDM híbrida a Intune independiente](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Compatibilidad de alta disponibilidad de On-premises Exchange Connector <!-- 676614 -->
Una vez que el conector de Exchange cree una conexión a Exchange mediante la CAS especificada, el conector tendrá la capacidad de detectar otras CAS. Si la CAS principal deja de estar disponible, el conector efectuará una conmutación por error en otra CAS, si está disponible, hasta que la CAS principal esté disponible. Para obtener más información, consulte [Compatibilidad de alta disponibilidad de On-premises Exchange Connector](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Reinicio remoto de dispositivos iOS (solo supervisado) <!-- 1424595 -->

Con una acción del dispositivo, ahora puede reiniciar un dispositivo supervisado de iOS 10.3 y versiones posteriores. Para obtener más información sobre el uso de la acción de reinicio del dispositivo, consulte [Reinicio remoto de los dispositivos con Intune](device-restart.md).

> [!Note]
> Para usar este comando es necesario que el dispositivo esté supervisado y disponer del derecho de acceso **Bloqueo del dispositivo**. El dispositivo se reinicia inmediatamente. Después de un reinicio, los dispositivos iOS bloqueados mediante código de acceso no volverán a unirse a una red Wi-Fi y es posible que no puedan comunicarse con el servidor.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Compatibilidad del inicio de sesión único con iOS <!-- 1333645 -->  

En el caso de los usuarios de iOS, puede usar el inicio de sesión único. Las aplicaciones de iOS que están codificadas para buscar las credenciales de usuario en la carga de inicio de sesión único funcionarán con esta actualización de la configuración de carga. También puede utilizar el UPN y el identificador de dispositivo de Intune para configurar el nombre de la entidad de seguridad y el dominio Kerberos. Para obtener más información, consulte [Configuración del inicio de sesión único de Intune para dispositivos iOS](sso-ios.md).

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Agregar "Buscar mi iPhone" para dispositivos personales <!--1427287-->
Ahora puede ver si los dispositivos iOS tienen activado el Boqueo de activación. Esta característica se encontraba anteriormente en Intune, en el portal clásico.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloqueo remoto de los dispositivos macOS administrados con Intune <!-- 1437691 -->

Si pierde un dispositivo macOS, puede bloquearlo y establecer un PIN de recuperación de seis dígitos. Una vez bloqueado, la hoja de **información general del dispositivo** muestra el PIN hasta que se envía otra acción de dispositivo.

Para obtener más información, consulte [Bloqueo remoto de los dispositivos administrados con Intune](device-remote-lock.md).

### <a name="new-scep-profile-details-supported----1559808---"></a>Nuevos detalles admitidos del perfil SCEP <!-- 1559808 -->

Ahora los administradores pueden establecer configuraciones adicionales al crear un perfil de SCEP en las plataformas Windows, iOS, macOS y Android.  Los administradores pueden establecer el IMEI, el número de serie o el nombre común, incluido el correo electrónico en el formato de nombre de sujeto.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset----1588489---"></a>Conservar los datos durante un restablecimiento de fábrica <!--1588489 -->
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


### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Se muestran las asignaciones del círculo de actualizaciones de Windows 10 <!-- 1621837 -->
Cuando esté **solucionando problemas**, y en relación al usuario que está visualizando, puede ver las asignaciones de círculos de actualizaciones de Windows 10.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Configuración de la frecuencia de informes de Protección contra amenazas avanzada de Windows Defender <!-- 1455974  -->
El servicio Protección contra amenazas avanzada de Windows Defender (WDATP) permite a los administradores gestionar la frecuencia con la que se generan informes relativos a los dispositivos administrados. Con la nueva opción **Frecuencia de informes de telemetría urgentes**, WDATP recopila datos y evalúa los riesgos con una frecuencia mayor. El valor predeterminado para los informes optimiza el rendimiento y la velocidad. Aumentar la frecuencia de los informes puede ser muy útil para dispositivos de alto riesgo. Esta configuración puede encontrarse en el perfil **ATP de Windows Defender** en **Configuraciones de dispositivos**.

### <a name="audit-updates----1412961---"></a>Actualizaciones de auditoría <!-- 1412961 -->  
La auditoría de Intune proporciona un registro de las operaciones que implican cambios en Intune.  Todas las operaciones de creación, actualización, eliminación y tareas remotas se registran y se conservan durante un año.  Azure Portal proporciona una vista filtrable de los datos auditados durante los últimos 30 días en cada carga de trabajo.  Con la correspondiente API de Graph es posible recuperar los datos de auditoría almacenados durante el último año.

La auditoría se encuentra en el grupo **MONITOR**. El elemento de menú **Registros de auditoría** está disponible para cada una de las carga de trabajo.

### <a name="company-portal-app-for-macos-is-available---1541700--"></a>Aplicación Portal de empresa ya disponible para macOS <!--1541700-->
La aplicación Portal de empresa de Intune para macOS presenta una experiencia actualizada, ya que se ha optimizado para mostrar correctamente toda la información y las notificaciones de conformidad que los usuarios necesitan para los dispositivos que hayan inscrito. Además, una vez que Portal de empresa se haya implementado en un dispositivo, las actualizaciones se proporcionarán a través de Microsoft AutoUpdate para macOS. Para descargar la nueva aplicación, inicie sesión en el sitio web de Portal de empresa de Intune desde un dispositivo macOS.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Inclusión de Microsoft Planner en la lista de aplicaciones aprobadas para la administración de aplicaciones móviles (MAM) <!-- 1248473 -->
La aplicación Microsoft Planner para iOS y Android ahora está incluida entre las aplicaciones aprobadas para la administración de dispositivos móviles (MAM). La aplicación puede configurarse para todos los inquilinos mediante la hoja Intune App Protection de Azure Portal.
- Para obtener más información, consulte la [lista de aplicaciones aprobadas para MAM](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Frecuencia de actualización de requisitos de VPN por aplicación en dispositivos iOS <!-- 1547061 -->  
En el caso de las aplicaciones en dispositivos iOS, los administradores ahora pueden quitar los requisitos de VPN por aplicación. Los dispositivos afectados se actualizarán tras la siguiente validación de Intune, que por lo general se produce cada 15 minutos.  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Compatibilidad con el módulo de administración de System Center Operations Manager para Exchange Connector <!-- 885457 -->
El módulo de administración de System Center Operations Manager (SCOM) para Exchange Connector ya está disponible para ayudarle a analizar los registros de Exchange Connector. Esta característica ofrece distintas maneras de supervisar el servicio cuando haya que resolver problemas.

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Administración conjunta para dispositivos de Windows 10 <!-- 1243445 -->
La administración conjunta es una solución que sirve para ofrecer un vínculo entre la administración tradicional y la administración moderna. Además, le proporciona una guía para llevar a cabo la transición con un enfoque por fases. Básicamente, la administración conjunta es una solución en la que los dispositivos de Windows 10 se administran de forma simultánea mediante Configuration Manager y Microsoft Intune. También se unen a Active Directory (AD) y a Azure Active Directory (Azure AD).  Esta configuración proporciona un método para poder modernizar la administración con el tiempo, a la velocidad que sea adecuada para su organización si no puede moverlo todo a la vez.  

### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Restricción de la inscripción de Windows según la versión del sistema operativo <!-- 245498 -->
Como administrador de Intune, ahora puede especificar una versión mínima y máxima de Windows 10 para poder inscribir dispositivos. Estas restricciones se pueden establecer en la hoja **Configuraciones de plataforma**.

Intune seguirá permitiendo la inscripción de teléfonos y equipos con Windows 8.1, pero solo se pueden establecer los límites mínimo y máximo de las versiones de Windows 10. Para permitir la inscripción de dispositivos 8.1, deje vacío el límite mínimo.

### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Alertas de dispositivos sin asignar de Windows AutoPilot <!-- 1631236 -->
Hay una nueva alerta disponible relativa a los dispositivos sin asignar de Windows AutoPilot en la página **Microsoft Intune** > **Inscripción de dispositivos** > **Información general**. Esta alerta indica cuántos dispositivos del programa AutoPilot no tienen asignados perfiles de implementación de AutoPilot. Use la información provista en la alerta para crear perfiles y asignarlos a los dispositivos sin asignar. Al hacer clic en la alerta, verá una lista completa de dispositivos de Windows AutoPilot e información detallada sobre ellos. Para obtener más información, vea [Inscribir dispositivos mediante el programa Windows AutoPilot Deployment](https://docs.microsoft.com/intune/enrollment-autopilot).


### <a name="refresh-button-for-devices-list-------1333581---"></a>Botón Actualizar de la lista de dispositivos    <!-- 1333581 -->
La lista de dispositivos no se actualiza automáticamente, de modo que puede usar el nuevo botón Actualizar para actualizar los dispositivos que figuran en esa lista.

### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Compatibilidad con la entidad de certificación (CA) en la nube de Symantec <!-- 1333638 -->    
Intune admite ahora la entidad de certificación en la nube de Symantec, que permite que Intune Certificate Connector emita certificados PKCS desde la entidad de certificación en la nube de Symantec para dispositivos administrados por Intune. Si ya usa Intune Certificate Connector con la entidad de certificación de Microsoft, puede usar la configuración existente de Intune Certificate Connector para agregar compatibilidad con la entidad de certificación de Symantec.

### <a name="new-items-added-to-device-inventory-----1404455---"></a>Nuevos elementos agregados al inventario de dispositivos   <!--1404455 -->
Los nuevos elementos que se indican a continuación ya están disponibles en el [inventario de los dispositivos inscritos](device-inventory.md):

- Dirección MAC de Wi-Fi
- Espacio de almacenamiento total
- Espacio disponible total
- MEID
- Operador del suscriptor

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Establecimiento del acceso para las aplicaciones mediante una revisión de seguridad mínima de Android en el dispositivo <!-- 1278463 -->   
Un administrador puede definir la revisión de seguridad mínima de Android que debe estar instalada en el dispositivo para poder obtener acceso a una aplicación administrada en una cuenta administrada.

> [!Note]  
> Esta característica solamente restringe las revisiones de seguridad publicadas por Google en dispositivos Android 6.0 y versiones posteriores.

### <a name="app-conditional-launch-support----1193313---"></a>Compatibilidad con inicio condicional de aplicación <!-- 1193313 -->
Los administradores de TI ahora pueden establecer un requisito a través del portal de administración de Azure para exigir un código de acceso en lugar de un PIN numérico mediante la administración de aplicaciones móviles (MAM) cuando se inicia la aplicación. Si se configura, se le pide al usuario que establezca y use un código de acceso cuando se le solicite antes de obtener acceso a aplicaciones habilitadas para MAM. Un código de acceso se define como un PIN numérico con al menos un carácter especial o un carácter alfabético en mayúsculas/minúsculas. Esta versión de Intune habilitará esta característica **solo en iOS**. Intune admite un código de acceso de forma similar al PIN numérico. Establece una longitud mínima y permite la repetición de caracteres y secuencias. Esta característica requiere el uso de ciertas aplicaciones (es decir, WXP, Outlook, Managed Browser o Yammer) para integrar Intune App SDK con el código de esta y aplicar la configuración del código de acceso en las aplicaciones de destino.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Número de versión de la aplicación para línea de negocio en el informe de estado de instalación del dispositivo <!-- 1233999 -->
Con esta versión, el informe de estado de instalación del dispositivo mostrará el número de versión de aplicación de las aplicaciones de línea de negocio para iOS y Android. Puede usar esta información para solucionar problemas de las aplicaciones o buscar los dispositivos que ejecuten versiones obsoletas de la aplicación.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Los administradores ya pueden configurar las opciones del firewall en un dispositivo mediante un perfil de configuración de dispositivo <!-- 951708 -->   
Los administradores pueden activar el firewall para los dispositivos y, además, configurar varios protocolos para redes públicas, privadas y de dominio.  Esta configuración del firewall se encuentra en el perfil "Endpoint Protection".

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>La Protección de aplicaciones de Windows Defender ayuda a proteger los dispositivos de sitios web que no son de confianza, en función de la definición de la organización <!-- 958257 -->   
Los administradores pueden definir sitios como "de confianza" o "corporativos" mediante un flujo de trabajo de Windows Information Protection o el nuevo perfil de "límite de red" en las configuraciones del dispositivo. Si se visualizan con Microsoft Edge, todos los sitios que no aparezcan en un límite de red de confianza de un dispositivo de Windows 10 de 64 bits se abrirán en un explorador de un equipo virtual de Hyper-V.

La Protección de aplicaciones se encuentra en los perfiles de configuración del dispositivo, en el perfil "Endpoint Protection". Desde allí, los administradores pueden configurar la interacción entre el explorador virtualizado y el equipo host, los sitios que son y que no son de confianza, y el almacenamiento de datos generado en el explorador virtualizado. Para usar la Protección de aplicaciones en un dispositivo, debe configurarse primero un límite de red. Es importante definir un solo límite de red para un dispositivo.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows Defender Application Control en Windows 10 Enterprise ofrece el modo de confiar solo en aplicaciones autorizadas <!-- 1031096 -->    
Teniendo en cuenta que cada día se crean miles de archivos malintencionados, el uso de la detección antivirus basada en firma para luchar contra el malware podría ser insuficiente para proporcionar una defensa adecuada contra nuevos ataques. Mediante Windows Defender Application Control en Windows 10 Enterprise, puede cambiar la configuración del dispositivo de un modo en el que las aplicaciones son de confianza a menos que las bloquee un antivirus u otra solución de seguridad, a un modo en el que el sistema operativo solo confía en las aplicaciones autorizadas por la empresa. La confianza se asigna a las aplicaciones en Windows Defender Application Control.

Mediante Intune, puede configurar las directivas de control de aplicaciones en modo de "solo auditoría" o en el modo de uso forzoso. Las aplicaciones no se bloquean cuando se ejecutan en modo de "solo auditoría". El modo de "solo auditoría" registra todos los eventos en registros del cliente local. También puede configurar si solo se pueden ejecutar componentes de Windows y aplicaciones de Microsoft Store, o si también se pueden ejecutar otras aplicaciones con buena reputación de acuerdo con la definición de Intelligent Security Graph.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>La Protección contra vulnerabilidades de seguridad de Windows Defender es un nuevo conjunto de funciones de prevención de intrusiones para Windows 10 <!-- 1063615 -->   
La Protección contra vulnerabilidades de seguridad de Windows Defender incluye reglas personalizadas para reducir la explotabilidad de las aplicaciones. También impide las amenazas de macros y scripts, bloquea automáticamente las conexiones de red a direcciones IP de mala reputación y puede proteger los datos contra el ransomware y amenazas desconocidas. La Protección contra vulnerabilidades de seguridad de Windows Defender consta de los componentes siguientes:

- La **reducción de la superficie expuesta a ataques (ASR)** proporciona reglas que permiten impedir las amenazas de macros, scripts y correos electrónicos.
- El **acceso controlado a carpetas** bloquea automáticamente el acceso a contenido en las carpetas protegidas.
- El **filtro de red** bloquea las conexiones salientes desde cualquier aplicación a IP o dominios de mala reputación.
- La **protección contra vulnerabilidades** proporciona restricciones de memoria, flujo de control y directivas que pueden usarse para proteger una aplicación contra las vulnerabilidades.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Administrar scripts de PowerShell en Intune para dispositivos Windows 10 <!-- 790537 -->

La extensión de administración de Intune permite cargar los scripts de PowerShell en Intune para ejecutarse en dispositivos Windows 10. Esta extensión complementa las capacidades de administración de dispositivos móviles (MDM) de Windows 10 y facilita la transición a una administración moderna. Para conocer más detalles, vea [Administrar scripts de PowerShell en Intune para dispositivos Windows 10](intune-management-extension.md).

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Nueva configuración de restricciones de dispositivos para Windows 10 <!-- 1308850 -->
-    Mensajería (solo móvil): deshabilitar pruebas o mensajes MMS
-    Contraseña: configuración para habilitar FIPS y el uso de dispositivos secundarios Windows Hello para la autenticación 
-    Pantalla: configuración para activar o desactivar el ajuste de escala de GDI para las aplicaciones heredadas

### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Restricciones de dispositivos Windows 10 a pantalla completa <!-- 1308872 -->   
Puede restringir usuarios de dispositivos Windows 10 a pantalla completa, lo que les limita a un conjunto de aplicaciones predefinidas.  Para ello, cree un perfil de restricción de dispositivo Windows 10 y defina la configuración de pantalla completa.

La pantalla completa admite dos modos: **aplicación única**, que permite que un usuario ejecute una sola aplicación, o **varias aplicaciones**, que permite el acceso a un conjunto de aplicaciones.  Para determinar las aplicaciones compatibles, debe definir la cuenta de usuario y el nombre del dispositivo.  Cuando el usuario ha iniciado sesión, verá únicamente las aplicaciones definidas.  Para obtener más información, vea [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) (CSP AssignedAccess). 

La pantalla completa requiere lo siguiente:

- Intune debe ser la entidad de MDM.
- Las aplicaciones deben estar ya instaladas en el dispositivo de destino.
- El dispositivo debe estar [aprovisionado correctamente](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Nuevo perfil de configuración de dispositivo para crear límites de red <!-- 1311967 -->   
En los otros perfiles de configuración de dispositivo encontrará un nuevo perfil de configuración de dispositivo llamado **Límite de red**. Use este perfil para definir los recursos en línea que quiere que se consideren corporativos y de confianza. Debe definir un límite de red para un dispositivo *antes* de que en el dispositivo se puedan usar características como la Protección de aplicaciones de Windows Defender y Windows Information Protection. Es importante definir un solo límite de red para cada dispositivo.

Puede definir los recursos de empresa en la nube, los intervalos de direcciones IP y los servidores proxy internos que quiere que se consideren de confianza. Una vez definidos, pueden usar el límite de red otras características como la Protección de aplicaciones de Windows Defender y Windows Information Protection.

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Dos opciones de configuración adicionales para Antivirus de Windows Defender <!-- 1338409 -->  
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

### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Adición de la VPN de Citrix a dispositivos Windows 10 <!-- 1512457 -->  
Puede configurar la VPN de Citrix para sus dispositivos Windows 10. Puede elegir la VPN de Citrix en la lista *Seleccione un tipo de conexión* en la hoja **VPN base** al configurar una VPN para Windows 10 y versiones posteriores.

> [!Note]
> La configuración de Citrix ya existía para iOS y Android.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Las conexiones Wi-Fi admiten claves precompartidas en iOS <!-- 1550823 -->
Los clientes pueden configurar perfiles de Wi-Fi para usar claves precompartidas (PSK) en las conexiones WPA o WPA2 Personal en dispositivos iOS. Estos perfiles se insertan en el dispositivo del usuario al inscribirlo en Intune.

Cuando el perfil se haya insertado en el dispositivo, el siguiente paso dependerá de la configuración del perfil.  Si está establecido para conectarse automáticamente, lo hace cuando la red se necesite.  Cuando el perfil se conecta de forma manual, el usuario deberá activar manualmente la conexión.  

### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Acceso a los registros de aplicación administrada de iOS <!-- 1469920 -->
Ahora, los usuarios finales que tengan Managed Browser instalado pueden ver el estado de administración de todas las aplicaciones publicadas de Microsoft, así como enviar registros para solucionar problemas con sus aplicaciones iOS administradas.

Para más información sobre cómo habilitar el modo de solución de problemas en Managed Browser en un dispositivo iOS, vea [Cómo tener acceso a los registros de aplicación administrada con Managed Browser en iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Mejoras en el flujo de trabajo de configuración de dispositivos en la versión 2.9.0 de Portal de empresa para iOS <!-- 1417174 -->

El flujo de trabajo de configuración de dispositivos se ha mejorado en la aplicación Portal de empresa para iOS. El lenguaje ahora es más fácil de entender, y también hemos combinado las pantallas que hemos podido. Además, hemos utilizado el nombre de su empresa en el texto del proceso de configuración para que el lenguaje sea más específico. Puede consultar el flujo de trabajo actualizado en la  [página de novedades de la interfaz de usuario de la aplicación](whats-new-app-ui.md).


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>La entidad de usuario contiene los datos de usuario más recientes en el modelo de datos de Almacenamiento de datos <!-- 1544273 -->
La primera versión del modelo de datos del Almacenamiento de datos de Intune solo contenía datos de Intune recientes e históricos. Los creadores de informes no podían capturar el estado actual de un usuario. En esta actualización, la **entidad de usuario** se rellena con los datos más recientes del usuario.


## <a name="october-2017"></a>Octubre de 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>El número de versión de la aplicación de línea de negocio de Android y iOS es visible <!-- 1380712 -->

Las aplicaciones de Intune ahora muestran el número de versión para las aplicaciones de línea de negocio de iOS y Android. El número se muestra en la lista de aplicaciones de Azure Portal y en la hoja de información general de la aplicación. Los usuarios finales pueden ver este número en la aplicación Portal de empresa y en el portal web.

__Número de versión completo__ El número de versión completo identifica una versión específica de la aplicación. El número aparece como _versión_(_compilación_). Por ejemplo, 2.2(2.2.17560800).

El número de versión completo consta de dos componentes:

 - **Versión**  
   El número de versión es el número que pueden ver los usuarios. Sirve para que los usuarios finales distingan las diferentes versiones de la aplicación.

 - **Número de compilación**  
    El número de compilación es un número interno que puede usarse para la detección de la aplicación y para administrar la aplicación mediante programación. El número de compilación alude a una iteración de la aplicación que hace referencia a los cambios en el código.

Obtenga más información sobre los números de versión y el desarrollo de aplicaciones de línea de negocio en [Introducción al SDK para aplicaciones de Microsoft Intune](app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration----677972---"></a>Integración de la administración de dispositivos y aplicaciones <!-- 677972 -->   
Ahora que se puede tener acceso a la administración de dispositivos móviles (MDM) y a la administración de aplicaciones móviles (MAM) de Intune desde Azure Portal, Intune ha empezado a integrar la experiencia de administración de TI en torno a la administración de aplicaciones y dispositivos. Estos cambios están pensados para simplificar la experiencia de administración de dispositivos y aplicaciones.

Obtenga más información sobre los cambios anunciados en MDM y MAM en el [blog del equipo de soporte técnico de Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Nuevas alertas de inscripción de dispositivos de Apple <!-- 1471790 -->
En la página de información general de la inscripción se mostrarán alertas relacionadas con la administración de dispositivos de Apple que resultarán útiles para los administradores de TI. Las alertas se mostrarán en la página de información general cuando el certificado de inserción MDM de Apple esté a punto de expirar o ya lo haya hecho; cuando el token del Programa de inscripción de dispositivos vaya a expirar o ya lo haya hecho; y cuando haya dispositivos sin asignar en el Programa de inscripción de dispositivos.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Reemplazo de tokens en la configuración de aplicaciones sin inscripción de dispositivos <!-- 1080364 -->

Puede usar tokens para valores dinámicos de la configuración de las aplicaciones en dispositivos que no están inscritos. Para obtener más información, consulte [Agregar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos](app-configuration-policies-managed-app.md).

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Actualizaciones de la aplicación Portal de empresa para Windows 10 <!--1299474-->
La página Configuración de la aplicación de Portal de empresa para Windows 10 se ha actualizado para que las opciones y las acciones de usuario previstas sean más coherentes en relación con el resto de opciones de configuración. También se ha actualizado para que el diseño coincida con el de otras aplicaciones de Windows. Puede ver imágenes del antes y el después en la [página de novedades de la interfaz de usuario de la aplicación](whats-new-app-ui.md).

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Informar a los usuarios finales de la información del dispositivo que puede verse en el caso de los dispositivos Windows 10 <!--1337920-->
Hemos agregado **Tipo de propiedad** a la pantalla Detalles del dispositivo en la aplicación Portal de empresa para Windows 10. Esto permitirá que los usuarios obtengan más información sobre privacidad directamente desde esta página de los documentos de usuario final de Intune. También podrán encontrar esta información en la pantalla **Acerca de**.

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Solicitudes de comentarios sobre la aplicación Portal de empresa para Android <!--1165249-->
La aplicación Portal de empresa para Android ahora solicita comentarios al usuario final. Estos comentarios se envían directamente a Microsoft, y los usuarios finales pueden valorar la aplicación de forma pública en Google Play Store. No es obligatorio enviar comentarios al respecto, ya que se pueden descartar fácilmente para continuar usando la aplicación.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Ayudar a los usuarios con la aplicación Portal de empresa para Android <!-- 1573324, 1573150, 1558616, 1564878 -->

La aplicación Portal de empresa para Android incorpora instrucciones adicionales para los usuarios finales con la finalidad de ayudarles a comprender y, siempre que sea posible, resolver por ellos mismos los nuevos casos de uso.
- Los usuarios finales serán guiados al [Portal de Azure Active Directory](https://account.activedirectory.windowsazure.com/r/#/profile) para quitar un dispositivo en caso de que hayan alcanzado el número máximo de dispositivos que se permite agregar.
- A los usuarios finales se les indican los pasos que deben seguir para ayudarles a [corregir errores de activación en dispositivos Samsung Knox](https://go.microsoft.com/fwlink/?linkid=859718) o a [desactivar el modo de ahorro de energía](/intune-user-help/power-saving-mode-android). Si ninguna de esas soluciones resuelve su problema, se les proporcionará una explicación de cómo [enviar registros a Microsoft](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nueva acción “Resolver” disponible para dispositivos Android <!-- 1583480 -->

La aplicación Portal de empresa para Android presenta la acción “Resolve” en la página _Actualizar configuración del dispositivo_. Si selecciona esta opción, el usuario final irá directamente a la configuración que causa la no conformidad de su dispositivo. La aplicación Portal de empresa para Android admite actualmente esta acción para las opciones de configuración [código de acceso de dispositivo](/intune-user-help/set-your-pin-or-password-android), [depuración USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) y [orígenes desconocidos](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Indicador de progreso de configuración de dispositivos en Portal de empresa para Android <!-- 1565657 -->
Cuando un usuario está inscribiendo su dispositivo, la aplicación Portal de empresa para Android muestra un indicador de progreso de configuración de dispositivos. Dicho indicador muestra nuevos estados: empieza con "Configurando el dispositivo...", sigue con "Registrando el dispositivo..." y "Finalizando el registro del dispositivo...", y acaba con "Finalizando la configuración del dispositivo...".

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Compatibilidad con la autenticación basada en certificados en el Portal de empresa para iOS <!--1029830-->
Hemos agregado compatibilidad con la autenticación basada en certificados (CBA) en la aplicación Portal de empresa para iOS. Los usuarios con CBA deben escribir su nombre de usuario y, después, pulsar el vínculo para iniciar sesión con un certificado. CBA ya se admite en las aplicaciones Portal de empresa para Android y Windows. Puede obtener más información en la página [Sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) (Iniciar sesión en la aplicación Portal de empresa).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Las aplicaciones que están disponibles con o sin inscripción ahora se pueden instalar sin que se les solicite la inscripción. <!-- 1334712 -->

Ahora, las aplicaciones de empresa que se han puesto a disposición de los usuarios con o sin inscripción en la aplicación de Portal de empresa de Android pueden instalarse sin necesidad de una solicitud de inscripción.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Compatibilidad del programa Windows AutoPilot Deployment en Microsoft Intune<!-- 747617  -->
Ahora puede usar Microsoft Intune con el programa Windows AutoPilot Deployment para que los usuarios puedan aprovisionar sus dispositivos de empresa sin necesidad de recurrir al departamento de TI. Puede personalizar la experiencia de configuración rápida y guiar a los usuarios durante la combinación de sus dispositivos con Azure AD y la inscripción en Intune. Al usar conjuntamente Microsoft Intune y Windows AutoPilot, se acaba con la necesidad de implementar, mantener y administrar imágenes del sistema operativo. Para obtener información, consulte [Inscribir dispositivos mediante el programa Windows AutoPilot Deployment](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="quick-start-for-device-enrollment-----1425655---"></a>Inicio rápido para la inscripción de dispositivos <!-- 1425655 --> 
Ahora el inicio rápido está disponible en **Inscripción de dispositivos** y proporciona una tabla de referencias para administrar plataformas y configurar el proceso de inscripción. Para simplificar la iniciación, se ofrece documentación útil en forma de una breve descripción de cada elemento y enlaces a documentación con instrucciones paso a paso.

### <a name="device-categorization----1427491---"></a>Categorización de dispositivos <!-- 1427491 -->
En el gráfico de la plataforma de dispositivos inscritos de la hoja **Dispositivos > Información general** se organizan los dispositivos por plataforma, incluidos Android, iOS, macOS, Windows y Windows Mobile.  Los dispositivos que ejecutan otros sistemas operativos se agrupan en "Otros",  por ejemplo, dispositivos fabricados por Blackberry, NOKIA u otros fabricantes.  

Para obtener información sobre los dispositivos que se ven afectados en el inquilino, elija **Administrar > Todos los dispositivos** y después use **Filtrar** para limitar el campo **Sistema operativo**.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium: nuevo socio de defensa contra amenazas móviles <!-- 954681 -->  
Puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Zimperium, una solución de defensa contra amenazas móviles integrada en Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funcionamiento de la integración con Intune
El riesgo se evalúa según la telemetría recopilada de dispositivos con Zimperium. Se pueden configurar directivas de acceso condicional de EMS según la evaluación de riesgos de Zimperium habilitada mediante las directivas de cumplimiento de los dispositivos de Intune, que puede usar para permitir o bloquear el acceso de los dispositivos no compatibles a los recursos corporativos en función de las amenazas detectadas.

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Nueva configuración del perfil de restricción de dispositivo Windows 10 <!--- 978575, 1308849, -->  
Estamos agregando nuevas configuraciones al perfil de restricción de dispositivos Windows 10 en la categoría de SmartScreen de Windows Defender.

Para obtener información sobre el perfil de restricción de dispositivos Windows 10, vea [Configuración de restricciones de dispositivos Windows 10 y versiones posteriores]( device-restrictions-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Soporte remoto para Windows y dispositivos Windows Mobile  <!-- 1070473 -->  
Ahora Intune puede usar el software [TeamViewer](https://www.teamviewer.com), que se compra por separado, para que pueda ofrecer asistencia remota a los usuarios que estén ejecutando Windows y dispositivos Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Examen de dispositivos con Windows Defender <!-- 1280988  1280990   -->
Ahora puede ejecutar un **Examen rápido** y un **Examen completo**, además de **Actualizar firmas**, con el antivirus Windows Defender en los dispositivos Windows 10 administrados. En la hoja de información general del dispositivo, elija la acción que desea ejecutar en el dispositivo. Se le pide que confirme la acción antes de que el comando se envíe al dispositivo. 

**Examen rápido**: un examen rápido examina ubicaciones donde el malware se registra para iniciarse, como las claves del registro y las carpetas de inicio de Windows conocidas. Un examen rápido tarda de media cinco minutos. Al combinarlo con la opción **Always-on real-time protection** (Protección en tiempo real siempre activa), que examina los archivos cuando están abiertos o cerrados y siempre que un usuario navega a una carpeta, el examen rápido ayuda a proporcionar protección frente a malware que podría estar en el sistema o el kernel. Los usuarios ven los resultados del examen en sus dispositivos cuando termina. 

**Examen completo**: un examen completo puede resultar útil en los dispositivos que han encontrado una amenaza de malware para identificar si existe algún componente inactivo que requiera una limpieza más exhaustiva, además de para ejecutar exámenes a petición. El examen completo puede tardar una hora en ejecutarse. Los usuarios ven los resultados del examen en sus dispositivos cuando termina. 

**Actualizar firmas**: el comando de actualización de firmas actualiza las definiciones y las firmas de malware del antivirus de Windows Defender. Esto le ayuda a asegurarse de que el antivirus de Windows Defender es eficaz en la detección de malware. Esta característica es para dispositivos Windows 10 únicamente, está pendiente la conectividad a Internet de los dispositivos. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Se ha quitado el botón Habilitar/Deshabilitar de la página de la entidad emisora de certificados de Azure Portal de Intune <!-- 1400455 -->
 Se está eliminando un paso adicional para configurar el conector de certificados en Intune. Actualmente, descarga el conector del certificado y después lo habilita en la consola de Intune. En cambio, si deshabilita el conector en la consola de Intune, el conector sigue emitiendo certificados.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
A partir de octubre, el botón Habilitar/Deshabilitar ya no aparecerá en la página de la entidad emisora de certificados en Azure Portal. La funcionalidad del conector sigue siendo la misma. Los certificados todavía se implementan en dispositivos inscritos en Intune. Puede continuar descargando e instalando el conector del certificado. Para detener la emisión de certificados, ahora deberá desinstalar el conector del certificado en vez de deshabilitarlo.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Si actualmente tiene el conector del certificado deshabilitado, primero debe desinstalarlo.

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Nueva configuración del perfil de restricción de dispositivo Windows 10 Team  <!--- 1308838 -->
En esta versión, hemos agregado muchas configuraciones nuevas al perfil de restricción de dispositivo de Windows 10 Team para ayudarle a controlar los dispositivos de Surface Hub.

Para obtener más información sobre este perfil, vea [Configuración de restricciones de dispositivos Windows 10 Team en Microsoft Intune](device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Restricción para impedir que los usuarios de dispositivos Android puedan cambiar la fecha y la hora de sus dispositivos <!-- 1333292 -->
Puede usar una [directiva de dispositivo personalizada de Android](custom-settings-android.md) para impedir que los usuarios de dispositivos Android cambien la fecha y la hora del dispositivo.

Para ello, configure una directiva personalizada de Android con el URI de configuración ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange. Establezca este parámetro en **TRUE** y luego asígnelo a los grupos requeridos.

### <a name="bitlocker-device-configuration----1397398---"></a>Configuración del dispositivo de BitLocker <!-- 1397398 -->
La opción **Cifrado de Windows > Configuración base**  incluye el nuevo ajuste **Advertencia para otro cifrado de disco** que le permite deshabilitar el [mensaje de advertencia](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) para otro cifrado de disco que podría estar en uso en el dispositivo del usuario.  El mensaje de advertencia requiere el consentimiento del usuario final antes de configurar BitLocker en el dispositivo y bloquea la instalación de BitLocker hasta que este la confirme.  La nueva configuración deshabilita la advertencia del usuario final.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Ahora el programa de compras por volumen para las aplicaciones de empresa se sincronizará con su inquilino de Intune <!-- 800882 -->  
Los desarrolladores de terceros también pueden distribuir aplicaciones de forma privada a miembros autorizados del Programa de compras por volumen (VPP) para Empresas, especificados en iTunes Connect. Estos miembros pueden iniciar sesión en la tienda de aplicaciones del Programa de Compras por Volumen y comprar aplicaciones.

Con esta versión, el VPP para aplicaciones de empresa que haya comprado el usuario final se sincronizarán con sus inquilinos de Intune.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selección de la instancia de App Store de Apple del país para la sincronización de aplicaciones de VPP  <!-- 1332311 -->  
Puede configurar la instancia de App Store del país para el Programa de Compras por Volumen de Apple (VPP) al cargar el token de VPP. Intune sincroniza las aplicaciones de VPP para todas las configuraciones regionales desde la instancia de App Store del país de VPP especificada.

> [!NOTE]  
> En la actualidad, Intune solo sincroniza las aplicaciones de VPP de la instancia de App Store del país de VPP que coinciden con la configuración regional de Intune en la que se creó el inquilino de Intune.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloqueo de las acciones de copiar y pegar entre perfiles profesionales y personales en Android for Work <!-- 1098994 -->
Con esta versión, es posible configurar el perfil del trabajo para Android for Work a fin de bloquear las acciones de copiar y pegar entre aplicaciones profesionales y personales. Puede encontrar esta nueva opción de configuración en el perfil **Restricciones de dispositivos** para la plataforma **Android for Work** en **Configuración del perfil de trabajo**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Creación de aplicaciones iOS limitadas a determinadas instancias regionales de App Store de Apple <!-- 1281692 -->
Podrá especificar la configuración regional del país durante la creación de una aplicación administrada de App Store de Apple.

> [!Note]  
> Actualmente, solo puede crear aplicaciones administradas del App Store de Apple que se encuentren en tiendas de Estados Unidos.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Actualización de aplicaciones con licencia para dispositivos y usuarios de VPP de iOS  <!-- 1305564 -->  
Podrá configurar el token de VPP de iOS para actualizar todas las aplicaciones adquiridas para ese token a través del servicio de Intune. Intune detectará las actualizaciones de la aplicación de VPP dentro de la App Store y las insertará automáticamente en el dispositivo cuando este se registra.

Para consultar los pasos necesarios para establecer un token de VPP y habilitar las actualizaciones automáticas, consulte [Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune] (/intune/vpp-apps-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Adición de colección de entidad de asociación de dispositivo de usuario al modelo de datos de almacenamiento de datos de Intune <!-- 1187917 -->
Ahora puede generar informes y visualizaciones de datos con la información de asociación de dispositivo de usuario que asocia las colecciones de la entidad de dispositivo y de usuario. Es posible tener acceso al modelo de datos a través del archivo de Power BI (PBIX) recuperado de la página de almacenamiento de datos de Intune, a través del punto de conexión de OData o mediante el desarrollo de un cliente personalizado.

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Revisión del cumplimiento de directivas para los anillos de actualizaciones de Windows 10 <!-- 1067886 -->
Podrá revisar un informe de directiva para los círculos de actualizaciones de Windows 10 desde Actualizaciones de software > Estado de implementación por anillo de actualización. El informe de directiva incluye el estado de implementación para los anillos de actualización que ha configurado. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Nuevo informe que muestra los dispositivos iOS con versiones anteriores de iOS <!-- 1352223 -->
El informe **Dispositivos iOS obsoletos** está disponible desde el área de trabajo **Actualizaciones de software**. En el informe, puede ver una lista de dispositivos iOS supervisados destinados mediante una directiva de actualización iOS y que tienen actualizaciones disponibles. Para cada dispositivo, puede ver un estado por el que el dispositivo no se ha actualizado automáticamente. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Visualización de las asignaciones de directivas de protección de aplicaciones para la solución de problemas <!--  1475003 -->
En la próxima versión, la opción **Directiva de protección de aplicaciones** se agregará a la lista desplegable **Asignaciones** disponible en la hoja de la solución de problemas. Ahora puede seleccionar las directivas de protección de aplicaciones para ver las directivas de protección de aplicaciones asignadas a los usuarios seleccionados.



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Mejoras en el flujo de trabajo de configuración de dispositivos en el Portal de empresa <!--1490692-->
Hemos mejorado el flujo de trabajo de configuración de dispositivos en la aplicación Portal de empresa para Android. El lenguaje es más fácil de usar y es específico de su empresa. Además, hemos combinado pantallas siempre que hemos podido. Puede verlas en la página [Novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md#week-of-october-2-2017).

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Se ha mejorado la guía sobre la solicitud de acceso a los contactos en dispositivos Android <!--1484985-->

La aplicación Portal de empresa para Android suele pedir al usuario final que acepte el permiso de los contactos. Si un usuario final no acepta este acceso, ahora verá una notificación en la aplicación en la que se le alerta de concederlo para el acceso condicional. 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Corrección del inicio seguro para Android <!--1490712-->

Los usuarios finales que tienen dispositivos Android podrán seleccionar el motivo de no compatibilidad en la aplicación del Portal de empresa. Cuando sea posible, se les llevará directamente a la ubicación correcta de la aplicación de configuración para poder resolver el problema. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Notificaciones de inserción adicionales para los usuarios finales en la aplicación Portal de empresa para Android Oreo <!--1475932-->

Los usuarios finales verán notificaciones adicionales que les indicarán cuándo la aplicación Portal de empresa para Android Oreo está realizando tareas en segundo plano, como la recuperación de directivas desde el servicio Intune. Con esto se aumenta la transparencia para los usuarios finales con respecto a cuando Portal de empresa realiza tareas administrativas en el dispositivo. Esto forma parte de la [optimización de la interfaz de usuario de Portal de empresa](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) general para la aplicación Portal de empresa para Android Oreo. 

Existen más optimizaciones para nuevos elementos de la IU que ya están habilitados para Android Oreo.  Los usuarios finales verán notificaciones adicionales en las que se les indicará el momento en el que la aplicación Portal de empresa esté realizando tareas en segundo plano, como la recuperación de directivas desde el servicio Intune.  Esto aumenta la transparencia para los usuarios finales sobre cuándo el Portal de empresa está realizando tareas administrativas en el dispositivo.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nuevos comportamientos para la aplicación de Portal de empresa para Android con perfiles de trabajo <!-- 1485783 -->

Cuando inscribe un dispositivo de Android for Work con un perfil de trabajo, la aplicación de Portal de empresa del perfil de trabajo es quien realiza las tareas de administración en el dispositivo. 

A menos que utilice una aplicación habilitada para MAM en el perfil personal, la aplicación de Portal de empresa para Android ya no tiene ninguna utilidad. Para mejorar la experiencia de perfil de trabajo, Intune ocultará automáticamente la aplicación de Portal de empresa personal una vez que se complete correctamente la inscripción del perfil de trabajo.

La aplicación Portal de empresa para Android se puede habilitar en cualquier momento en el perfil personal; para ello, vaya a [Portal de empresa de en Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) y pulse en **Habilitar**.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Puesta en modo de mantenimiento del Portal de empresa para Windows 8.1 y Windows Phone 8.1 <!--1428681-->

A partir de octubre de 2017, las aplicaciones de Portal de empresa para Windows 8.1 y Windows Phone 8.1 pasarán a modo de mantenimiento. Esto significa que las aplicaciones y los escenarios existentes, como la inscripción y el cumplimiento, seguirán siendo compatibles para estas plataformas. Estas aplicaciones seguirán estando disponibles para su descarga a través de los canales de lanzamiento existentes, como Microsoft Store. 

Una vez que se encuentre en modo de mantenimiento, estas aplicaciones solo recibirán actualizaciones de seguridad críticas. No se publicarán actualizaciones ni características para estas aplicaciones. Para las nuevas características, se recomienda que actualice los dispositivos a Windows 10 o Windows 10 Mobile. 


### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>Bloqueo de la inscripción de dispositivos Samsung KNOX no compatible <!-- 1490695 -->

La aplicación del Portal de empresa solo intenta inscribir dispositivos Samsung KNOX compatibles. Para evitar errores de activación de Knox que impidan la inscripción de MDM, la inscripción de dispositivos solo se intenta si el dispositivo aparece en la [lista de dispositivos publicados por Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Los dispositivos Samsung pueden tener números de modelo que admitan Knox, mientras que otros no. Compruebe la compatibilidad de KNOX con el distribuidor de su dispositivo antes de la compra y la implementación. Encontrará la lista completa de dispositivos comprobados en la [configuración de directivas de Android y Samsung Knox Standard](/intune/supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Fin de la compatibilidad con Android 4.3 y anterior <!-- 1171126, 1326920 -->
Las aplicaciones administradas y la aplicación Portal de empresa para Android exigirán Android 4.4 y versiones posteriores para acceder a recursos de empresa. En diciembre, todos los dispositivos inscritos se eliminarán, lo que provocará su pérdida de acceso a los recursos de empresa. Si está usando directivas de protección de aplicaciones sin MDM, las aplicaciones no recibirán actualizaciones y la calidad de su experiencia empeorará con el tiempo.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Informar a los usuarios finales de la información de dispositivo que puede verse en los dispositivos inscritos <!--1165314-->
Estamos agregando **Tipo de propiedad** a la pantalla Detalles del dispositivo en todas las aplicaciones del Portal de empresa. Esto permitirá que los usuarios obtengan más información sobre la privacidad directamente en el artículo [¿Qué información puede ver mi empresa cuando inscribo mi dispositivo en Intune?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) Se irá implementando en todas las aplicaciones del Portal de empresa en un futuro próximo (se anunció para iOS en [septiembre](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)).

## <a name="september-2017"></a>Septiembre de 2017

### <a name="intune-supports-ios-11---1428975--"></a>Intune es compatible con iOS 11 <!--1428975-->
Intune es compatible con iOS 11. Ya se anunció anteriormente en el [blog de soporte técnico de Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80----1164477---"></a>Fin de la compatibilidad con iOS 8.0 <!-- 1164477 -->
Las aplicaciones administradas y la aplicación Portal de empresa para iOS exigirán iOS 9.0 y versiones posteriores para acceder a recursos de empresa. Los dispositivos que no estén actualizados antes de septiembre de este año ya no podrán acceder a esas aplicaciones ni al Portal de empresa. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Adición de acción de actualización a la aplicación de Portal de empresa para Windows 10 <!--1132468-->
La aplicación de Portal de empresa para Windows 10 permite a los usuarios actualizar los datos de la aplicación tirando para actualizar o, en equipos de escritorio, presionando F5.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informar a los usuarios finales de la información de dispositivo que puede verse para iOS <!--739894-->

Hemos agregado **Tipo de propiedad** a la pantalla Detalles del dispositivo en la aplicación del portal de empresa para iOS. Esto permitirá que los usuarios obtengan más información sobre la privacidad directamente en esta página de los documentos para el usuario final de Intune. También podrán encontrar esta información en la pantalla Acerca de.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Permitir que los usuarios finales accedan a la aplicación Portal de empresa para Android sin inscripción <!---1169910--->

Pronto los usuarios finales no tendrán que inscribir sus dispositivos para acceder a la aplicación Portal de empresa para Android. Los usuarios finales de las organizaciones que usen directivas de protección de aplicaciones dejarán de recibir mensajes para inscribir sus dispositivos cuando abran la aplicación Portal de empresa. Los usuarios finales también podrán instalar aplicaciones desde el Portal de empresa sin inscribir el dispositivo. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Expresión más fácil de entender para la aplicación de Portal de empresa para Android <!---1396349--->  

El proceso de inscripción para la aplicación de Portal de empresa para Android se ha simplificado con nuevo texto para que resulte más sencillo para los usuarios finales. Si tiene documentación de inscripción personalizada, deberá actualizarla para reflejar las pantallas nuevas. También puede encontrar imágenes de muestra en nuestra página [Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune](whats-new-app-ui.md#week-of-september-11-2017).

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Adición de la aplicación de Portal de empresa de Windows 10 a la directiva de permiso de Windows Information Protection <!-- 677129 -->

La aplicación de Portal de empresa de Windows 10 se ha actualizado para admitir Windows Information Protection (WIP). La aplicación se puede agregar a la directiva de autorización de WIP. Con este cambio, la aplicación ya no tiene que agregarse a la lista **Excluir**.


## <a name="august-2017"></a>Agosto de 2017

### <a name="improvements-to-device-overview----1404453---"></a>Mejoras en la información general de dispositivos <!-- 1404453 -->  
La información general de dispositivos ahora muestra los que están inscritos, pero excluye a los que administra Exchange ActiveSync. Los dispositivos de Exchange ActiveSync no ofrecen las mismas opciones de administración que los inscritos. Para ver el número de dispositivos inscritos y el de dispositivos inscritos por plataforma en la sección Intune de Azure Portal, vaya a **Dispositivos** > **Información general**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Mejoras en el inventario de dispositivos recopilado mediante Intune
<!-- 961134, 1104426, 1281327, 1333543 --> En esta versión, hemos realizado las mejoras siguientes en la información de inventario que recopilan los dispositivos que administra:
 
-   En dispositivos Android, ahora puede agregar una columna al inventario de dispositivos que muestra el nivel de revisión más reciente de cada uno. Agregue la columna **Nivel de revisión de seguridad** a la lista de dispositivos para verlo.
-   Al filtrar la vista de dispositivos, podrá filtrarlos según su fecha de inscripción. Por ejemplo, puede mostrar solo los dispositivos que se hayan inscrito después de una fecha específica.
-   Hemos realizado mejoras en el filtro que usa el elemento **Ultima fecha de inserción**.
-   En la lista de dispositivos, ahora puede mostrar el número de teléfono de los dispositivos corporativos.
Además, puede usar el panel de filtros para buscar dispositivos por el número de teléfono.
 
Para obtener más información sobre el inventario de dispositivos, consulte [Visualización del inventario de dispositivos de Intune](device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Compatibilidad del acceso condicional con dispositivos macOS 
<!-- 720172 --> Ya puede establecer una directiva de acceso condicional que exija que los dispositivos Mac se inscriban en Intune y cumplan las directivas de cumplimiento de dispositivos. Por ejemplo, los usuarios pueden descargar la aplicación Portal de empresa de Intune para macOS e inscribir los dispositivos Mac en Intune. Intune evalúa si el dispositivo Mac es conforme o no con requisitos como el PIN, el cifrado, la versión del sistema operativo y la integridad del sistema.

- Obtenga más información sobre la [compatibilidad con el acceso condicional para dispositivos macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>La aplicación Portal de empresa para macOS está en versión preliminar pública <!---1484796--->
La aplicación Portal de empresa para macOS ya está disponible como parte de la versión preliminar pública para el acceso condicional en Enterprise Mobility + Security. Esta versión admite macOS 10.11 y versiones posteriores. Obténgala en [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Nueva configuración de restricciones de dispositivos para Windows 10    
<!--1063965, 1308850  --> En esta versión, se han agregado opciones nuevas para el [perfil de restricción de dispositivos Windows 10](/intune/device-restrictions-windows-10) en las categorías siguientes:

-   SmartScreen de Windows Defender
-   Tienda de aplicaciones

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Actualizaciones en el perfil de dispositivo de Endpoint Protection de Windows 10 para la configuración de BitLocker
<!--1459533 -->    
En esta versión, hemos realizado las mejoras siguientes al funcionamiento de la configuración de BitLocker en un perfil de dispositivo de Endpoint Protection de Windows 10:
 
-   En **Configuración de BitLocker para unidades de sistema operativo**, en el ajuste **BitLocker con un chip TPM no compatible** BitLocker estaba permitido tras seleccionar **Bloquear**. Se ha corregido este problema para poder bloquear BitLocker cuando se selecciona.
-   En **Configuración de BitLocker para unidades de sistema operativo**, en el ajuste **Agente de recuperación de datos basada en certificado**, ya puede bloquear explícitamente el agente de recuperación de datos basada en certificado. De forma predeterminada, el agente está permitido.
-   En **Configuración de BitLocker para unidades de datos fijas**, en el ajuste **Agente de recuperación de datos**, ya puede bloquear explícitamente el agente de recuperación de datos.
Para obtener más información, vea [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Configuración de Endpoint Protection para Windows 10 y versiones posteriores).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nueva experiencia de sesión iniciada para los usuarios del portal de empresa de Android y para los usuarios de la directiva de protección de aplicaciones <!-- 621669 -->
Los usuarios finales pueden ahora examinar aplicaciones, administrar dispositivos y ver la información de contacto de TI mediante la aplicación del Portal de empresa de Android sin inscribir sus dispositivos Android. Además, si un usuario final ya usa una aplicación protegida mediante las directivas de Intune App Protection e inicia el portal de empresa de Android, el usuario final ya no recibirá una solicitud para inscribir el dispositivo.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nueva configuración de la aplicación de portal de empresa para Android para alternar la optimización de la batería <!--1405990-->
La página **Configuración** de la aplicación Portal de empresa para Android tiene una nueva opción que permite a los usuarios desactivar fácilmente la optimización de la batería para las aplicaciones Portal de empresa y Microsoft Authenticator. El nombre de la aplicación que se muestra en la configuración variará dependiendo de qué aplicación administre la cuenta profesional. Recomendamos que los usuarios desactiven la optimización de la batería para obtener un rendimiento mejor de las aplicaciones de trabajo que sincronizan el correo electrónico y los datos. 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Compatibilidad con varias identidades en OneNote para iOS      <!-- 1234281 -->
Los usuarios finales ahora pueden usar cuentas diferentes (profesionales o educativas) en Microsoft OneNote para iOS. Las directivas de protección de aplicaciones se pueden aplicar a los datos corporativos en blocs de notas del trabajo sin que esto afecte a sus blocs de notas personales. Por ejemplo, una directiva puede permitir que un usuario busque información en blocs de notas del trabajo, pero impedir que copie datos corporativos desde un bloc de notas del trabajo a uno personal.
 
- Obtenga más información sobre las aplicaciones que admiten [protección de aplicaciones y varias identidades](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Nueva configuración para permitir y bloquear aplicaciones en dispositivos Samsung Knox Standard
<!-- 1305423 822899-->  
En esta versión, se ha agregado una nueva [configuración de restricción de dispositivos](device-restrictions-android.md) que permite especificar las listas de aplicaciones siguientes:
 
- Aplicaciones que los usuarios pueden instalar
- Aplicaciones que los usuarios no pueden ejecutar
- Aplicaciones ocultas para el usuario en el dispositivo
 
Puede especificar la aplicación por dirección URL, nombre del paquete o desde la lista de aplicaciones que administra.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Nuevo vínculo de interfaz de usuario de la directiva de acceso condicional basado en la aplicación de Azure AD desde Intune
<!-- 1016201 --> Ahora los administradores de TI pueden establecer directivas condicionales basadas en aplicaciones mediante la nueva interfaz de usuario de directivas de acceso condicional en la carga de trabajo de Azure AD. El acceso condicional basado en la aplicación de la sección de Intune App Protection en Azure Portal por el momento no se moverá y se aplicará en paralelo. También encontrará un práctico vínculo a la interfaz de usuario de la nueva directiva de acceso condicional en la carga de trabajo de Intune.

- Obtenga más información sobre el [acceso condicional basado en la aplicación en Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).



## <a name="july-2017"></a>Julio de 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Restricción de la inscripción de dispositivos Android e iOS por versión del SO <!--- 1333256,  1245463 --->
Intune ya permite restringir la inscripción de Android e iOS por número de versión del sistema operativo. En **Restricción de tipo de dispositivo**, los administradores de TI ahora pueden establecer una configuración de plataforma para restringir la inscripción entre un valor del sistema operativo mínimo y máximo. Las versiones del sistema operativo Android se deben especificar como Principal.Secundaria.Compilación.Revisión, donde Secundaria, Compilación y Revisión son opcionales. Las versiones de iOS deben especificarse como Principal.Secundaria.Compilación, donde Compilación es opcional. Obtenga más información sobre las [restricciones de inscripción de dispositivos](enrollment-restrictions-set.md).

>[!NOTE]
>No se restringe la inscripción a través de los programas de inscripción de Apple o Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Restricción de la inscripción de dispositivos de propiedad personal macOS, iOS y Android <!--- 1333272,  1333275, 1245709 --->
Intune puede restringir la inscripción de dispositivos personales al incluir los números IMEI de los dispositivos corporativos en la lista aprobada. Intune ha ampliado esta funcionalidad para iOS, Android y macOS con números de serie del dispositivo. Al cargar los números de serie en Intune, puede declarar los dispositivos como de propiedad corporativa. Con las restricciones de inscripción puede bloquear los dispositivos de propiedad personal (BYOD), lo que permitiría la inscripción de dispositivos de propiedad corporativa únicamente. Obtenga más información sobre las [restricciones de inscripción de dispositivos](enrollment-restrictions-set.md).

Para importar números de serie, vaya a **Inscripción de dispositivos** > **Identificadores de dispositivo corporativos** y haga clic en **Agregar**; luego, cargue un archivo .CSV (sin encabezado, dos columnas para el número de serie y detalles como los números IMEI).  Para restringir dispositivos de propiedad personal, vaya a **Inscripción de dispositivos** > **Restricciones de inscripción**. En **Restricciones de tipo de dispositivo**, seleccione **Predeterminado** y luego **Configuraciones de plataforma**. Puede **Permitir** o **Bloquear** dispositivos de propiedad personal iOS, Android y macOS. 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nueva acción de dispositivo para forzar la sincronización de los dispositivos con Intune <!-- 711369 -->
En esta versión, se ha agregado una nueva acción de dispositivo que fuerza al dispositivo seleccionado a registrarse inmediatamente en Intune. Cuando un dispositivo se registra, recibe de inmediato las acciones o las directivas pendientes que se le han asignado.  Esta acción puede ayudarle a validar y a solucionar problemas de directivas que se le hayan asignado inmediatamente, sin tener que esperar al siguiente registro programado.
Para obtener detalles, vea [Synchronize device](device-sync.md) (Sincronizar dispositivos).

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forzar a dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible <!-- 777100 -->
En el área de trabajo Actualizaciones de software hay disponible una nueva directiva que permite forzar a los dispositivos iOS supervisados a instalar automáticamente la última actualización de software disponible. Para obtener información detallada, consulte [Configure iOS update policies](/intune/software-updates-ios) (Configuración de directivas de actualización de iOS).

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile: nuevo socio de defensa contra amenazas móviles <!-- 954651, 1172027 -->
Puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por SandBlast Mobile de Check Point, una solución de defensa contra amenazas móviles integrada en Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funcionamiento de la integración con Intune
El riesgo se evalúa según la telemetría recopilada de dispositivos que ejecutan SandBlast Mobile de Check Point. Puede configurar directivas de acceso condicional de EMS basadas en la evaluación de riesgos de SandBlast Mobile de Check Point habilitada mediante las directivas de cumplimiento de los dispositivos de Intune. Puede permitir o bloquear el acceso de dispositivos no compatibles a recursos corporativos en función de las amenazas detectadas.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Implementar una aplicación como disponible en la Tienda Microsoft para Empresas <!-- 748101 -->
Con esta versión, ahora los administradores pueden asignar la Tienda Microsoft para Empresas como disponible. Cuando se establece como disponible, los usuarios finales pueden instalar la aplicación desde la aplicación de Portal de empresa o un sitio web sin que se les redirija a Microsoft Store.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Actualizaciones de la interfaz de usuario en el sitio web del portal de empresa <!--1313244 part 1-->
Hemos realizado varias actualizaciones en la interfaz de usuario del [sitio web del portal de empresa](https://portal.manage.microsoft.com) para mejorar la experiencia del usuario final.

- __Mejoras en los iconos de aplicación__: Los iconos de aplicación ahora se muestran con un fondo generado automáticamente basándose en el color dominante del icono (si se puede detectar). Si procede, este fondo reemplaza el borde gris que antes era visible en los iconos de aplicación.

    En una próxima versión, el sitio web del Portal de empresa mostrará iconos grandes siempre que sea posible. Recomendamos que los administradores de TI publiquen aplicaciones con iconos de alta resolución, con un tamaño mínimo de 120 x 120 píxeles. 

- __Cambios de navegación__: Los elementos de barra de navegación se han movido al menú hamburguesa de la parte superior izquierda. Se ha quitado la página Categorías. Los usuarios ahora pueden filtrar el contenido por categoría durante la exploración.

- __Actualizaciones de aplicaciones destacadas__: Hemos agregado al sitio una página dedicada donde los usuarios pueden buscar aplicaciones que ha decidido presentar, y hemos realizado algunos ajustes a la interfaz de usuario de la sección Destacado en la página principal.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Compatibilidad de iBooks con el sitio web del Portal de empresa <!--1231841-->
Hemos agregado una página dedicada al sitio web del Portal de empresa que permite a los usuarios buscar y descargar iBooks. 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>Detalles adicionales para la solución de problemas del departamento de soporte técnico <!---  Applies to 1263399, 1326964, 1341642 --->
Intune ha actualizado la visualización de información para la solución de problemas, y la ha agregado a la información que se proporciona a los administradores y al personal del departamento de soporte técnico. Ahora puede consultar la tabla **Asignaciones**, en la que se resumen todas las asignaciones para el usuario en función de la pertenencia al grupo. La lista incluye lo siguiente:
- Aplicaciones móviles
- Directivas de cumplimiento
- Perfiles de configuración
 
Además, en la tabla **Dispositivos** se incluyen ahora las columnas **Tipo de combinación de Azure AD** y **Conforme con Azure AD**. Para obtener más información, consulte [Help users troubleshoot problems (Ayudar a los usuarios a solucionar problemas)](help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Almacenamiento de datos de Intune (versión preliminar pública)
El Almacenamiento de datos de Intune muestrea los datos a diario para proporcionar una vista histórica del inquilino. Puede tener acceso a los datos mediante un archivo de Power BI (PBIX), un vínculo de OData que es compatible con muchas herramientas de análisis o al interactuar con la API de REST. Para obtener más información, vea [Usar el Almacenamiento de datos de Intune](reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modos claro y oscuro disponibles para la aplicación Portal de empresa para Windows 10 <!---676547--->
Los usuarios finales podrán personalizar el modo de color de la aplicación Portal de empresa para Windows 10. El usuario puede realizar el cambio en la sección Configuración de la aplicación Portal de empresa. El cambio aparecerá una vez que el usuario haya reiniciado la aplicación. En Windows 10 versión 1607 y posteriores, el valor predeterminado del modo de la aplicación es la configuración del sistema. En Windows 10 versión 1511 y anteriores, el valor predeterminado del modo de la aplicación es el modo claro.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Permitir que los usuarios finales etiqueten su grupo de dispositivos en la aplicación Portal de empresa para Windows 10 <!---807046-->
Los usuarios finales ahora pueden seleccionar el grupo al que pertenece su dispositivo al etiquetarlo directamente desde la aplicación de portal de empresa para Windows 10.



## <a name="june-2017"></a>Junio de 2017

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Nuevo acceso de administración basada en roles para los administradores de Intune <!-- 1099990 -->  
Se va a agregar un nuevo rol de administrador de acceso condicional para ver, crear, modificar y eliminar directivas de acceso condicional de Azure AD. Anteriormente, solo los administradores globales y de seguridad tenían este permiso. Se puede conceder a los administradores de Intune el permiso de este rol para que tengan acceso a las directivas de acceso condicional.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Etiquetado de los dispositivos corporativos con el número de serie<!-- 1215070 -->  
Intune ahora admite la carga de números de serie de iOS, macOS y Android como identificadores de dispositivos corporativos. No puede usar en este momento números de serie para impedir que los dispositivos personales se inscriban, ya que los números de serie no se comprueban durante la inscripción. Próximamente se podrán bloquear los dispositivos personales por el número de serie.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Nuevas acciones remotas para los dispositivos iOS <!-- 854689 -->
En esta versión, hemos agregado dos nuevas acciones de dispositivo remoto para los dispositivos iPad compartidos que administran la aplicación Classroom de Apple:

-   [Cerrar sesión del usuario actual](device-logout-user.md): cierra la sesión del usuario actual de un dispositivo iOS que seleccione.
-   [Quitar usuario](device-remove-user.md): elimina un usuario que seleccione de la memoria caché local en un dispositivo iOS.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Compatibilidad con dispositivos iPad compartidos con la aplicación Classroom de iOS<!-- 1044681 -->
En esta versión, hemos ampliado la compatibilidad con la administración de la aplicación Classroom en iOS, a fin de incluir a los estudiantes que se registran en dispositivos iPad compartidos con sus identificadores de Apple administrados.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Cambios en las aplicaciones integradas de Intune <!-- 1332306 -->
Anteriormente, Intune tenía numerosas aplicaciones integradas que se podían asignar rápidamente. Basándonos en los comentarios de los usuarios, hemos quitado esta lista y ya no se verán las aplicaciones integradas.
Sin embargo, si las aplicaciones integradas ya están asignadas, seguirán mostrándose en la lista de aplicaciones. Las aplicaciones podrán seguir asignándose según se necesite.
En una versión posterior, vamos a agregar un método sencillo para seleccionar y asignar aplicaciones integradas de Azure Portal.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Instalación más sencilla de aplicaciones de Office 365 <!--- 1121362 --->
El nuevo tipo de aplicación de **Office 365 ProPlus** facilita la asignación de aplicaciones de Office 365 ProPlus 2016 a dispositivos que administre con la versión más reciente de Windows 10. Además, también puede instalar Microsoft Project y Microsoft Visio si dispone de licencias para ellos. Las aplicaciones que quiera se agrupan y aparecen como una única aplicación en la lista de aplicaciones de la consola de Intune.
Para obtener más información, consulte el artículo sobre [cómo agregar aplicaciones de Office 365 para Windows 10](apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Compatibilidad con aplicaciones sin conexión desde la Tienda Microsoft para Empresas <!--- 777044 --->
Las aplicaciones sin conexión que ha adquirido en la Tienda Microsoft para Empresas ahora se sincronizarán con Azure Portal. Así, puede implementar estas aplicaciones en grupos de usuarios o grupos de dispositivos. Las aplicaciones sin conexión no se instalan desde la Tienda, sino mediante Intune.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft Teams ahora forma parte de la lista de CA basada en aplicación de aplicaciones aprobadas <!-- 1257019 -->
La aplicación Microsoft Teams para iOS y Android ahora forma parte de las aplicaciones aprobadas para las directivas de acceso condicional basado en la aplicación en Exchange y SharePoint Online. La aplicación puede configurarse para todos los inquilinos mediante la hoja Intune App Protection de Azure Portal en estos momentos mediante el acceso condicional basado en la aplicación.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Integración de App Proxy y Managed Browser <!-- 1287310 -->
Intune Managed Browser ahora puede integrarse con el servicio de Azure AD Application Proxy para permitir que los usuarios tengan acceso a los sitios web internos incluso cuando están trabajando en remoto. Los usuarios del explorador simplemente especifican la URL del sitio como lo harían normalmente y Managed Browser enruta la solicitud mediante la puerta de enlace web de Application Proxy. Para obtener más información, vea [Administrar el acceso a Internet mediante directivas de Managed Browser](app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Nuevas opciones de configuración de aplicaciones para Intune Managed Browser<!-- 682951 -->
En esta versión, hemos agregado más configuraciones para la aplicación Intune Managed Browser para iOS y Android. Ahora puede usar una directiva de configuración de aplicaciones para configurar la página principal predeterminada y los marcadores para el explorador.
Para obtener más información, vea [Administrar el acceso a Internet mediante directivas de Managed Browser](app-configuration-managed-browser.md).

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Configuración de BitLocker para Windows 10 <!-- 951707 -->
Ahora puede configurar las opciones de BitLocker para dispositivos Windows 10 con un nuevo perfil de dispositivo de Intune. Por ejemplo, puede que necesite que los dispositivos estén cifrados, y también configurar más opciones que se apliquen cuando BitLocker esté activado.
Para obtener más información, vea [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Configuración de Endpoint Protection para Windows 10 y versiones posteriores).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Nueva configuración del perfil de restricción de dispositivo Windows 10<!--- 978527,  978550, 978569, 1050031, 1058611,  --->
En esta versión, hemos agregado nuevas opciones para el perfil de restricción de dispositivos Windows 10, en las categorías siguientes:

-  Windows Defender
-  Red de telefonía móvil y conectividad
-  Experiencia de pantalla bloqueada
-  Privacidad
-  Buscar
-  Contenido destacado de Windows
-  Explorador Microsoft Edge

Para obtener más información sobre la configuración de Windows 10, vea [Configuración de restricciones de dispositivos Windows 10 y versiones posteriores](device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>La aplicación portal de empresa para Android ahora tiene una nueva experiencia de usuario final para las directivas de protección de aplicaciones <!--1305217-->
Basándonos en los comentarios de los clientes, hemos modificado la aplicación del portal de empresa para Android para mostrar un botón **Acceso al contenido de la empresa**. El objetivo es impedir que los usuarios finales pasen innecesariamente por el proceso de inscripción cuando solo necesitan tener acceso a las aplicaciones que admiten directivas de protección de aplicaciones, una característica de administración de aplicaciones móviles de Intune. Puede ver estos cambios en la página [Novedades en la interfaz de usuario de la aplicación](whats-new-app-ui.md).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nueva acción de menú para quitar fácilmente Portal de empresa de Intune <!--1164569-->
Según los comentarios de los usuarios, se agregó una nueva acción de menú en la aplicación Portal de empresa de Intune para Android con el fin de iniciar su eliminación del dispositivo. Con esta acción se quita el dispositivo de administración de Intune para que la aplicación se pueda quitar del dispositivo por parte del usuario. Puede ver estos cambios en la página de [novedades en la UI de la aplicación](whats-new-app-ui.md) y en la [documentación para el usuario final de Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Mejoras en la sincronización de aplicaciones con Windows 10 Creators Update <!--676505-->
La aplicación Portal de empresa de Intune para Windows 10 ahora iniciará automáticamente una sincronización de las solicitudes de instalación de aplicaciones para dispositivos con Windows 10 Creators Update (versión 1703). De esta forma, se reducirá el problema de estancamiento de las instalaciones de aplicaciones durante el estado "Pending Sync" (Sincronización pendiente). Además, los usuarios podrán iniciar manualmente la sincronización desde dentro de la aplicación. Puede ver estos cambios en la página [Novedades en la interfaz de usuario de la aplicación](whats-new-app-ui.md).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nueva experiencia guiada del Portal de empresa de Windows 10<!---1058938--->
La aplicación del Portal de empresa para Windows 10 incluirá la experiencia de un tutorial de Intune guiado para dispositivos que no se han identificado ni inscrito. La nueva experiencia proporciona instrucciones paso a paso que llevan al usuario por el registro en Azure Active Directory (que es necesario para las características de acceso condicional) y la inscripción en MDM (que es necesaria para las características de administración de dispositivos). La experiencia guiada será accesible desde la página principal del Portal de empresa. Los usuarios pueden seguir utilizando la aplicación si no completan el registro y la inscripción, pero experimentarán una funcionalidad limitada.

Esta actualización solo es visible en dispositivos que ejecuten la Actualización de aniversario de Windows 10 (compilación 1607) o superior. Puede ver estos cambios en la página [Novedades en la interfaz de usuario de la aplicación](whats-new-app-ui.md).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Las consolas de administración de Microsoft Intune y Acceso condicional están disponibles con carácter general
Se anuncia la disponibilidad general de la nueva consola de administración tanto de Intune en Azure Portal como de Acceso condicional. A través de Intune en Azure Portal, ahora puede administrar todas las funcionalidades MAM y MDM de Intune en una experiencia de administración consolidada y aprovechar la agrupación y la selección de destino de Azure AD. Acceso condicional de Azure reúne las amplias funcionalidades de Azure AD e Intune en una consola unificada. Y, desde una experiencia administrativa, migrar a la plataforma Azure permite usar exploradores modernos.

Intune ya está visible sin la etiqueta de **versión preliminar** en Azure portal en portal.azure.com.

No es necesario que los clientes existentes tomen ninguna medida en este momento, a menos que se haya recibido un mensaje de una serie de estos en el centro de mensajes en el que se le solicite llevar a cabo una acción para que sea posible migrar sus grupos. Es posible que también haya recibido una notificación del centro de mensajes en el que se le informe que la migración está tardando más de lo debido producto de errores en nuestro lado. Seguimos trabajando con diligencia para migrar cualquier cliente afectado.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Mejoras de los iconos de aplicación en la aplicación Portal de empresa de Intune para iOS
Se actualizó el diseño de los iconos de aplicación en la página principal para reflejar el color de personalización de marca que estableció para Portal de empresa de Intune. Para más información, consulte las [novedades en la UI de la aplicación](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Ahora el selector de cuenta está disponible en la aplicación Portal de empresa de Intune para iOS
Los usuarios de dispositivos iOS pueden ver el nuevo selector de cuenta cuando inician sesión en Portal de empresa de Intune si usan su cuenta profesional o educativa para iniciar sesión en otras aplicaciones de Microsoft. Para más información, consulte las [novedades en la UI de la aplicación](whats-new-app-ui.md).

## <a name="may-2017"></a>Mayo de 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Cambio de la entidad de MDM sin anular la inscripción de dispositivos administrados <!--1103950-->
Ahora puede cambiar la entidad de MDM sin tener que ponerse en contacto con el Soporte técnico de Microsoft y sin necesidad de anular la inscripción ni de volver a inscribir los dispositivos administrados existentes. En la consola de Configuration Manager, puede [cambiar la entidad de MDM](/sccm/mdm/deploy-use/change-mdm-authority) de Configurar como Configuration Manager (híbrido) a Microsoft Intune (independiente), o viceversa.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notificación mejorada para PIN de inicio en Samsung Knox <!--1087143-->
Si los usuarios finales necesitan establecer un PIN de inicio en dispositivos Samsung Knox a efectos de compatibilidad con el cifrado, cuando dichos usuarios pulsen en la notificación que aparece, se les remitirá al lugar exacto de la aplicación de configuración.  Anteriormente, la notificación remitía al usuario final a la pantalla de cambio de contraseña.

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
Algunas aplicaciones Android de la tienda admiten opciones de configuración administradas que permiten que un administrador de TI controle cómo se ejecuta la aplicación en el perfil de trabajo. Con Intune, ahora puede ver las configuraciones que son compatibles con una aplicación y configurarlas desde Azure Portal con un diseñador de configuración o un editor de JSON. Para más información, consulte el artículo sobre el [uso de configuraciones de aplicación para Android for Work](app-configuration-policies-use-android.md).

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
- Definir una directiva de código de acceso solo a nivel de perfil de trabajo: a los usuarios se les pedirá que escriban un código de acceso cada vez que se abra cualquier aplicación del perfil de trabajo.
- Definir una directiva para el dispositivo y el perfil de trabajo: el administrador de TI tiene la opción de definir una directiva de código de acceso para el dispositivo y otra para el perfil de trabajo con diferentes intensidades (por ejemplo, un PIN de cuatro dígitos para desbloquear el dispositivo y uno de seis para abrir cualquier aplicación de trabajo).

Para más información, consulte [Configuración de restricciones de dispositivos Android for Work en Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> Esta opción solo está disponible en Android 7.0 y versiones posteriores.  De forma predeterminada, el usuario final puede usar los dos PIN definidos por separado o de optar por combinar los dos en el más seguro de ellos.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Nuevas opciones de configuración para dispositivos Windows 10 <!-- 978585 -->
Agregamos una nueva [configuración de restricción de dispositivos Windows](device-restrictions-windows-10.md) que controla características como la proyección inalámbrica, la detección de dispositivos, la conmutación de tareas y los mensajes de error de tarjetas SIM.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Actualizaciones de la configuración de certificados <!-- 918991 and 823198 -->
Cuando crea un perfil de certificado SCEP, en el <strong>formato del nombre del sujeto</strong>, la opción <strong>Personalizar</strong> está disponible para dispositivos iOS, Android y Windows. Antes de esta actualización, el campo <strong>Personalizar</strong> solo estaba disponible para dispositivos iOS. Para obtener más información, vea [Creación de un perfil de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile).

Cuando crea un perfil de certificado PKCS, en el **nombre alternativo del sujeto**, está disponible la opción **Atributo de Azure AD personalizado**. La opción **Departamento** está disponible cuando se selecciona **Atributo de Azure AD personalizado**. Para obtener más información, vea [Creación de un perfil de certificado PKCS](certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Configuración de varias aplicaciones que se pueden ejecutar cuando un dispositivo Android está en el modo de pantalla completa <!-- 662059 -->
Si un dispositivo Android está en el modo de pantalla completa, anteriormente solo podía configurar una aplicación que se podía ejecutar. Ahora puede configurar varias aplicaciones con el id. de la aplicación, la dirección URL de la tienda o seleccionando una aplicación Android que ya administra. Para más información, consulte [Configuración del modo de pantalla completa](device-restrictions-android.md#kiosk).



## <a name="april-2017"></a>Abril de 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Compatibilidad para administrar la aplicación Classroom de Apple
Ahora puede administrar la aplicación Classroom de iOS en dispositivos iPad. Configure la aplicación Classroom en el iPad de los profesores con los datos correctos de la clase y los estudiantes y, a continuación, configure los iPad de los estudiantes registrados en la clase, de modo que pueda controlarlos mediante la aplicación.
Para obtener más detalles, vea [Configuración de dispositivos iOS para el entorno educativo](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Compatibilidad con las opciones de configuración administradas para aplicaciones Android <!-- 621621 -->
Intune ahora puede configurar las aplicaciones Android de Play Store que admiten opciones de configuración administradas.  Esta característica permite al equipo de TI ver la lista de valores de configuración que admite una aplicación y proporciona una interfaz de usuario interactiva y de primera clase que les permite configurar dichos valores.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nueva directiva de Android para PIN complejos <!-- 722069 -->
Ahora puede establecer un tipo de [contraseña](device-restrictions-android.md#password) obligatoria de complejo numérico en un perfil de dispositivo Android para dispositivos que ejecutan Android 5.0 y versiones posteriores.  Use esta opción para impedir que los usuarios de los dispositivos creen un PIN que contenga números repetidos o consecutivos, como 1111 o 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Soporte adicional para dispositivos Android for Work
- **Administrar la configuración del perfil de trabajo y la contraseña** <!-- 612808 -->

  Esta nueva directiva de restricción de dispositivos Android for Work ahora permite administrar la configuración del perfil de trabajo y la contraseña en los dispositivos Android for Work que administre.

- **Permitir el uso compartido de datos entre perfiles profesionales y personales** <!-- 1045102 -->

Este perfil de restricción de dispositivos Android for Work ahora tiene opciones nuevas que le ayudarán a configurar el uso compartido de datos entre el perfil profesional y el perfil personal.

- **Restringir las acciones de copiar y pegar entre perfiles profesionales y personales** <!-- 1046094 -->

  Un perfil de dispositivo personalizado para dispositivos Android for Work ahora permite restringir si se permiten las acciones de copiar y pegar entre aplicaciones profesionales y personales.

Para más información, consulte [Restricciones de dispositivos para Android for Work](device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Asignar aplicaciones de LOB a dispositivos iOS y Android <!-- 1057568 -->
Ahora puede asignar aplicaciones de línea de negocio para [iOS](lob-apps-ios.md) (archivos .ipa) y [Android](lob-apps-android.md) (archivos .apk) a usuarios o dispositivos.


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Nuevas directivas de dispositivo para iOS <!-- 723774, 723815, 723826, 723830 -->
- **Aplicaciones en la pantalla principal**: controla qué aplicaciones ven los usuarios en la [pantalla principal de sus dispositivos iOS](home-screen-settings-ios.md). Esta directiva cambia el diseño de la pantalla principal, pero no implementa ninguna aplicación.

- **Conexiones con dispositivos AirPrint**: controla a qué [dispositivos AirPrint](air-print-settings-ios-macos.md) (impresoras de red) se pueden conectar los usuarios finales de dispositivos iOS.

- **Conexiones con dispositivos AirPlay**: controla a qué [dispositivos AirPlay](airplay-settings-ios.md) (como Apple TV) se pueden conectar los usuarios finales de dispositivos iOS.

- **Mensaje personalizado de la pantalla de bloqueo**: configurar un mensaje personalizado que verán los usuarios en la pantalla de bloqueo de sus dispositivos iOS y que reemplaza al mensaje predeterminado de esa pantalla. Para más información, consulte [Activación del modo perdido en dispositivos iOS](device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Restringir las notificaciones de inserción para aplicaciones iOS <!-- 723767 -->
En un perfil de restricción de dispositivos de Intune, ahora puede configurar los siguientes [ajustes de notificación](app-notification-settings-ios.md) para dispositivos iOS:

- Activar o desactivar completamente las notificaciones para una aplicación especificada.
- Activar o desactivar la notificación en el centro de notificaciones para una aplicación especificada.
- Especificar el tipo de alerta como **None** (Ninguna), **Banner** (Mensaje emergente) o **Modal Alert** (Alerta modal).
- Especificar si se permiten los distintivos para esta aplicación.
- Especificar si se permiten los sonidos de notificaciones.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurar aplicaciones iOS para que se ejecuten en el modo de aplicación única de forma autónoma <!-- 737837 -->
Puede usar un perfil de dispositivo de Intune para configurar dispositivos iOS de modo que ejecuten aplicaciones especificadas en [modo de aplicación única autónoma](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). Cuando se configura este modo y se ejecuta la aplicación, el dispositivo se bloquea para que solo pueda ejecutar esa aplicación. Un ejemplo es cuando se configura una aplicación que permite a los usuarios hacer un examen en el dispositivo. Cuando se completan las acciones de la aplicación, o quita esta directiva, el dispositivo vuelve a su estado normal.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurar dominios de confianza para el correo electrónico y la exploración web en dispositivos iOS <!-- 723765 -->
Desde un perfil de restricción de dispositivos iOS, ahora puede configurar los [valores de dominio](device-restrictions-ios.md#domains) siguientes:

- **Dominios de correo electrónico sin marcar**: los correos electrónicos que el usuario envía o recibe y no coinciden con los dominios que especifique aquí se marcarán como que no son de confianza.

- **Dominios web administrados**: los documentos que se descargan de las direcciones URL que especifique aquí se considerarán administrados (solo en Safari).  

- **Dominios de relleno automático de contraseña de Safari**: los usuarios pueden guardar en Safari las contraseñas solo de las direcciones URL que coincidan con los patrones que especifique aquí. Para usar esta opción, el dispositivo debe estar en modo supervisado y no estar configurado para varios usuarios. (iOS 9.3 y versiones posteriores)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>Aplicaciones de PCV disponibles en el Portal de empresa de iOS <!-- 748782 -->
Ahora puede asignar aplicaciones de compras por volumen (PCV) de iOS como instalaciones **Disponibles** para usuarios finales. Los usuarios finales necesitarán una cuenta de Apple Store para instalar la aplicación.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizar libros electrónicos de la tienda de compras por volumen de Apple <!-- 800878 -->
Ahora puede [sincronizar los libros](vpp-apps-ios.md) que haya adquirido a través de la tienda del Programa de Compras por Volumen de Apple con Intune y asignarlos a los usuarios.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Administración de varios usuarios para dispositivos Samsung Knox Standard <!-- 971988 -->
Intune es compatible ahora con dispositivos que ejecutan Samsung Knox Standard para la [administración de varios usuarios](android-enroll.md). Esto significa que los usuarios finales pueden iniciar y cerrar sesión en el dispositivo con sus credenciales de Azure Active Directory, y que el dispositivo se administra centralmente tanto si está en uso como si no.  Cuando los usuarios finales inician sesión, tienen acceso a las aplicaciones y se les aplican las directivas. Cuando los usuarios cierran sesión, se borran todos los datos de la aplicación.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Configuración adicional de restricción de dispositivos Windows <!-- 818566 -->
Hemos agregado compatibilidad con [opciones de configuración adicionales de restricción de dispositivos Windows](device-restrictions-windows-10.md), como la compatibilidad adicional con el explorador Edge, la personalización de la pantalla de bloqueo del dispositivo, las personalizaciones del menú Inicio, el papel tapiz del conjunto de búsqueda de Contenido destacado de Windows y la configuración de proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Compatibilidad con varios usuarios para Windows 10 Creators Update <!-- 822547 -->
Hemos agregado compatibilidad para la [administración de varios usuarios](windows-enroll.md) en dispositivos que ejecutan Windows 10 Creators Update y están unidos al dominio de Azure Active Directory. Esto significa que cuando varios usuarios estándar inicien sesión en el dispositivo con sus credenciales de Azure AD, recibirán las aplicaciones y las directivas que se hayan asignado a sus nombres de usuario. Actualmente, los usuarios no puede usar Portal de empresa para escenarios de autoservicio, como la instalación de aplicaciones.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start para equipos con Windows 10<!-- 1004830 -->
Ahora hay disponible una nueva [acción de dispositivo Fresh Start](device-fresh-start.md) para equipos Windows 10.  Cuando se lleva a cabo esta acción, se quitan las aplicaciones que hubiera instaladas en el equipo y este se actualiza automáticamente a la última versión de Windows. Esto puede servir para ayudar a quitar las aplicaciones de OEM preinstaladas que a menudo se entregan con los nuevos PC. Puede configurar si se conservan los datos de usuario cuando se lleva a cabo esta acción de dispositivo.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Rutas de actualización adicionales de Windows 10 <!-- 903672 -->
Ahora puede crear una [directiva de actualización de edición para actualizar los dispositivos](edition-upgrade-configure-windows-10.md) a las siguientes ediciones adicionales de Windows 10:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscripción masiva de dispositivos Windows 10 <!-- 747607 -->
Ahora puede unir grandes cantidades de dispositivos que ejecutan Windows 10 Creator Update a Azure Active Directory e Intune con Windows Configuration Designer (WCD). Para habilitar la [inscripción masiva de MDM](windows-bulk-enroll.md) para el inquilino de Azure AD, cree un paquete de aprovisionamiento que una dispositivos al inquilino de Azure AD a través de Windows Configuration Designer y aplique el paquete a los dispositivos corporativos que desea inscribir y administrar de forma masiva. Una vez que el paquete se aplica a los dispositivos, se unirán a Azure AD, se inscribirán en Intune y estarán listos para que los usuarios de Azure AD inicien sesión.  Los usuarios de Azure AD son usuarios estándar en estos dispositivos y reciben las aplicaciones requeridas y las directivas asignadas. En este momento, no se admiten los escenarios de autoservicio ni de portal de empresa.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Nueva configuración de MAM para PIN y ubicaciones de almacenamiento administrado <!-- 581122, 736644 -->
Ahora hay disponibles dos nuevas opciones de configuración de aplicaciones que le ayudarán con los escenarios de administración de aplicaciones móviles (MAM):

- **Disable app PIN when device PIN is managed** (Deshabilitar el PIN de aplicación cuando se administra el PIN del dispositivo): detecta si hay un PIN de dispositivo en el dispositivo inscrito y, si es así, omite el PIN de aplicación desencadenado por las directivas de protección de aplicaciones. Esta configuración permitirá reducir el número de veces que se muestra una solicitud de PIN a los usuarios que abran una aplicación habilitada para MAM en un dispositivo inscrito. Esta característica está disponible para iOS y Android.

- **Seleccione en qué servicios de almacenamiento se puede guardar datos empresariales**: permite especificar en qué ubicaciones de almacenamiento quiere guardar los datos corporativos. Los usuarios pueden guardar en los servicios de ubicación de almacenamiento seleccionados, lo que implica que se bloquearán todos los demás servicios de ubicación de almacenamiento no indicados.

  Lista de servicios de ubicación de almacenamiento compatibles:

  - OneDrive
  - OneDrive para la Empresa/SharePoint Online
  - Almacenamiento local

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portal de solución de problemas del departamento de soporte técnico <!-- 907448 -->
El nuevo [portal de solución de problemas](help-desk-operators.md) permite que los operadores del departamento de soporte técnico y los administradores de Intune vean a los usuarios y sus dispositivos y, además, realicen tareas para solucionar problemas técnicos de Intune.

## <a name="march-2017"></a>Marzo de 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Compatibilidad con Modo Perdido de iOS <!--431695-->
En iOS 9.3 y dispositivos posteriores, Intune agrega compatibilidad con **Modo Perdido**. Ahora puede bloquear un dispositivo para evitar su uso, así como mostrar un mensaje y llamar al número de teléfono de la pantalla de bloqueo del dispositivo.

El usuario final no podrá desbloquear el dispositivo hasta que un administrador deshabilite Modo Perdido. Cuando está activado el Modo Perdido, puede usar la acción **Buscar dispositivo** para ver la ubicación geográfica del dispositivo en un mapa en la consola de Intune.

El dispositivo debe ser un dispositivo iOS de la empresa, inscrito mediante DEP, que esté en modo supervisado.

Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](device-management.md)

### <a name="improvements-to-device-actions-report---677150--"></a>Mejoras en los informes de las acciones del dispositivo <!--677150-->
Hemos realizado mejoras en el informe de las acciones del dispositivo para mejorar el rendimiento. Además, ahora puede filtrar el informe por estado. Por ejemplo, puede filtrar el informe para mostrar únicamente las acciones de dispositivo que se han completado".

### <a name="custom-app-categories---748805--"></a>Categorías de aplicaciones personalizadas <!--748805-->
Ahora puede crear, editar y asignar categorías a las aplicaciones que agregue a Intune. En estos momentos, las categorías solo pueden especificarse en inglés.
Consulte [How to add an app to Intune](apps-add.md) (Cómo agregar una aplicación a Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Asignación de aplicaciones LOB a los usuarios con dispositivos no inscritos <!--748823-->
Ahora puede asignar aplicaciones de línea de negocio desde la tienda a usuarios tengan o no inscritos sus dispositivos con Intune. Si el dispositivo de los usuarios no está inscrito con Intune, deben ir al sitio web del Portal de empresa para instalarlo, en lugar de a la aplicación del Portal de empresa.

### <a name="new-compliance-reports---846671--"></a>Nuevos informes de cumplimiento <!--846671-->
Ahora dispone de informes de cumplimiento que proporcionan la posición de cumplimiento de los dispositivos de su empresa y le permiten solucionar rápidamente los problemas relacionados con el cumplimiento detectados por los usuarios. Puede ver información acerca de

- Estado de cumplimiento general de los dispositivos
- Estado de cumplimiento de una configuración individual
- Estado de cumplimiento de una directiva individual

También puede usar estos informes para profundizar en un dispositivo individual para ver la configuración específica y las directivas que afectan a dicho dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->
Para las cuentas de Intune creadas después de enero de 2017, Intune habilitó el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en Azure Portal. Anteriormente, la vista preliminar de inscripción de Apple solo era accesible desde los vínculos de Azure Portal. Las cuentas de Intune creadas antes de enero de 2017 requerirán una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero pronto habrá detalles disponibles. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta no tiene acceso a la versión preliminar.


## <a name="february-2017"></a>Febrero de 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Capacidad para restringir la inscripción de dispositivos móviles <!--747600, 795782-->
Intune está agregando nuevas restricciones de inscripción que controlan qué plataformas de dispositivos móviles pueden inscribir. Intune separa las plataformas de dispositivos móviles como iOS, Mac OS, Android, Windows y Windows Mobile.

* La restricción la inscripción de dispositivos móviles no restringe la inscripción del cliente de PC.  
* Solo para iOS y Android, hay una opción adicional para bloquear la inscripción de dispositivos de propiedad personal.

Intune marca todos los dispositivos nuevos como personal a menos que el administrador de TI tome la medida de marcarlos como propiedad de la empresa, como se explica en [este artículo](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Ver todas las acciones en los dispositivos administrados <!--677150-->
Un nuevo informe __Acciones de dispositivo__ muestra quién ha realizado acciones remotas como el restablecimiento de fábrica en dispositivos y, además, muestra el estado de esa acción. Vea [¿Qué es la administración de dispositivos?](device-management.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Los dispositivos no administrados puedan acceder a aplicaciones asignadas <!--664691-->
Como parte de los cambios de diseño en el sitio web del portal de empresa, los usuarios de iOS y Android podrán instalar aplicaciones asignadas a ellos como "disponibles sin inscripción" en sus dispositivos no administrados. Con sus credenciales de Intune, los usuarios podrán iniciar sesión en el sitio web del portal de empresa y ver la lista de aplicaciones asignadas. Los paquetes de aplicación de las aplicaciones "disponibles sin inscripción" se encuentran disponibles para descargar a través del sitio web del portal de empresa. Las aplicaciones que requieren la inscripción para la instalación no se ven afectadas por este cambio, ya que se les pedirá a los usuarios que inscriban su dispositivo si quieren instalar esas aplicaciones.

### <a name="custom-app-categories---748805--"></a>Categorías de aplicaciones personalizadas <!--748805-->
Ahora puede crear, editar y asignar categorías a las aplicaciones que agregue a Intune. En estos momentos, las categorías solo pueden especificarse en inglés.
Consulte [How to add an app to Intune](apps-add.md) (Cómo agregar una aplicación a Intune).

### <a name="display-device-categories---814654--"></a>Mostrar categorías de dispositivos <!--814654-->
Ahora puede ver la categoría del dispositivo como una columna en la lista de dispositivos. También puede editar la categoría desde la sección de propiedades de la hoja de propiedades del dispositivo. Consulte [How to add an app to Intune](apps-add.md) (Cómo agregar una aplicación a Intune).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configuración de Windows Update para empresas <!--776716-->

Windows como servicio es la nueva forma de proporcionar actualizaciones para Windows 10. A partir de Windows 10, todas las nuevas actualizaciones de calidad y características contienen las actualizaciones anteriores. Es decir, siempre que haya instalado la más reciente, sabrá que sus dispositivos Windows 10 están completamente actualizados. A diferencia de las versiones anteriores de Windows, ahora debe instalar la actualización completa en lugar de una parte.

Gracias a Windows Update para empresas, puede simplificar la administración de actualizaciones, ya que no tendrá que aprobar actualizaciones individuales para grupos de dispositivos. Todavía puede administrar los riesgos en sus entornos configurando una estrategia de implementación de actualizaciones; Windows Update se asegurará de que las actualizaciones se instalen en el momento oportuno. Microsoft Intune ofrece la posibilidad de configurar las actualizaciones en los dispositivos y de aplazar su instalación. Intune no almacena las actualizaciones, sino únicamente la asignación de las directivas de actualización. Los dispositivos acceden a Windows Update directamente para instalar las actualizaciones. Use Intune para configurar y administrar los **anillos de actualización de Windows 10**. Un anillo de actualización contiene un grupo de opciones que configuran cuándo y cómo se instalan las actualizaciones de Windows 10. Para obtener más información, consulte [Configuración de Windows Update para empresas](windows-update-for-business-configure.md).
