---
title: Edición anticipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e24414d28b8adeae7dfbedb606ca1a7d21497a3f
ms.sourcegitcommit: 698af815f6de2c4f003f6da428bbfb0680daafa0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43093204"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>La edición anticipada de Microsoft Intune: agosto de 2018

> [!Note]
> Notificación del acuerdo de confidencialidad: Los siguientes cambios están en fase de desarrollo para Intune. Esta información se comparte en el acuerdo de confidencialidad de forma muy limitada. No publique esta información en redes sociales ni sitios web públicos, como Twitter, UserVoice, Reddit, etc. 

La **edición anticipada** proporciona una lista de características, compartidas en el acuerdo de confidencialidad, que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No publique en un tweet, divulgue en UserVoice ni comparta de otra manera esta información fuera de su empresa. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure

<!-- 1808 start -->

### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello está dirigido a usuarios y dispositivos <!-- 1106609 -->
Cuando crea una directiva [Windows Hello para empresas](windows-hello.md), se aplica a todos los usuarios dentro de la organización (inquilinos). Con esta actualización, la directiva también se puede aplicar a determinados usuarios o específicos mediante una directiva de configuración de dispositivo (**Configuración del dispositivo** > **Perfiles**  >  **Crear perfil** > **Identity Protection** > **Windows Hello para empresas**).

En Intune, en Azure Portal, la configuración de Windows Hello existirá tanto en **Inscripción del dispositivo** como en **Configuración del dispositivo**. **Inscripción del dispositivo** tiene como destino toda la organización (inquilinos) y es compatible con Windows AutoPilot (OOBE). **Configuración del dispositivo** tiene como destino los dispositivos y usuarios mediante una directiva que se aplica durante la inserción en el repositorio.

Se aplica a:  
- Windows 10 y versiones posteriores
- Windows Holographic for Business

### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Control del modo S en Windows 10 y dispositivos posteriores: versión preliminar pública <!-- 1958649 -->
Podrá crear un perfil de configuración de dispositivo que haga cambiar el modo S de un dispositivo Windows 10 o evitar que los usuarios cambien el modo S del dispositivo. Esta característica estará en Intune > **Configuración del dispositivo** > **Perfiles** >  **Windows 10 and later (Windows 10 y versiones posteriores)** > **Edition upgrade and mode switch (Actualización de edición y conmutación de modo)**.
En [Presentamos Windows 10 en modo S](https://www.microsoft.com/windows/s-mode) se proporciona más información sobre el modo S.
Se aplica a Windows 10 y versiones posteriores (1809 y posteriores)

### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Actualizaciones de compatibilidad con VPN moderna para iOS <!-- 2459928, 1819876, and 2650856 -->
Una actualización futura será compatible con los siguientes clientes VPN de iOS: 
- F5 Access (versión 3.0.1 y versiones posteriores)
- SSO de Citrix
- GlobalProtect de Palo Alto Networks (versión 5.0 y versiones posteriores). También en una futura actualización:
- El nombre de los tipos de conexión de **F5 Access** existentes se cambiará a **F5 Access Legacy** (por las actualizaciones de personalización de marca de F5)
- El nombre de los tipos de conexión de **GlobalProtect de Palo Alto Networks** existentes se cambiarán a **GlobalProtect de Palo Alto Networks heredado** (por las actualizaciones de personalización de marca de Palo Alto). 

Los perfiles existentes con estos tipos de conexión siguen funcionando con el cliente heredado de VPN. Si usa Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN o GlobalProtect de Legacy Palo Alto Networks heredado con iOS, debe pasar a las nuevas aplicaciones. Hágalo tan pronto como sea posible para garantizar que el acceso VPN esté disponible para dispositivos iOS a medida que se actualicen a iOS 12.

### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Bloqueo del Portal de empresa en el modo de aplicación única hasta el inicio de sesión del usuario <!--1067692 --> 
Tendrá la opción de ejecutar Portal de empresa en el modo de aplicación única si autentica un usuario a través de dicha aplicación en lugar del Asistente para configuración durante la inscripción de DEP. Esta opción bloquea el dispositivo inmediatamente después de completar el Asistente para configuración, de manera que un usuario debe iniciar sesión para acceder al dispositivo. Este proceso garantiza que el dispositivo completa la incorporación y no está huérfano en un estado sin ningún usuario asociado.

### <a name="scope-tags-for-policies---1081974-eeready--"></a>Etiquetas de ámbito para las directivas <!--1081974 eeready-->

Podrá crear etiquetas de ámbito para limitar el acceso a los recursos de Intune. Agregue una etiqueta de ámbito a una asignación de roles y luego agregue dicha etiqueta a un perfil de configuración. El rol solo tendrá acceso a los recursos con perfiles de configuración que tengan etiquetas de ámbito coincidentes (o no tengan ninguna etiqueta de ámbito).
Para crear una etiqueta de ámbito, elija **Roles de Intune** > **Ámbito (etiquetas)** > **Crear**.
Para agregar una etiqueta de ámbito a una asignación de rol, elija **Roles de Intune** > **Todos los roles** > **Policy and profile manager (Administrador de directivas y perfiles)** > **Asignaciones** > **Ámbito (etiquetas)**.
Para agregar una etiqueta de ámbito a un perfil de configuración, elija **Configuración del dispositivo** > **Perfiles** > elija un perfil > **Propiedades** > **Ámbito (etiquetas)**.

### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Asignación de un usuario y un nombre descriptivo a un dispositivo AutoPilot <!--1346521 -->
Una versión preliminar pública futura permitirá a los administradores asignar un usuario a un único dispositivo AutoPilot.  Los administradores también podrán proporcionar nombres descriptivos para saludar a los usuarios al configurar sus dispositivos con AutoPilot.

Se aplica a Windows Insider 1809 o una compilación posterior (todavía en versión preliminar).

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP de Apple usado por otro MDM <!-- 1488946 -->
Intune detectará y mostrará los detalles si un token de programa de compras por volumen (VPP) de Apple lo está usando Intune y otro MDM.

### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Compatibilidad de túnel de paquete para perfiles de VPN por aplicación de iOS para los tipos de conexión Pulse Secure y personalizados <!-- 1520957 -->
Al usar perfiles de VPN por aplicación de iOS, podrá usar tunelización de capa de aplicación (proxy de aplicación) o tunelización de nivel de paquete (túnel de paquete). Estas opciones estarán disponibles con los siguientes tipos de conexión:
- VPN personalizada
- Pulse Secure. Si no está seguro de qué valor usar, consulte la documentación de su proveedor de VPN.
Se aplica a iOS.

### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>Zscaler es una conexión disponible para los perfiles VPN en iOS <!-- 1769858 eeready -->
Cuando crea un perfil de configuración de dispositivo de VPN para iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > plataforma **iOS** > tipo de perfil **VPN**), hay varios tipos de conexión, incluidos Cisco, Citrix, etc. Una futura actualización agrega Zscaler como un tipo de conexión. 
[Configuración de VPN para dispositivos que ejecutan iOS](vpn-settings-ios.md) enumera los tipos de conexión disponibles.

### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloqueo de inscripciones de dispositivos personales Windows <!-- 1849498 -->
Podrá bloquear la inscripción de dispositivos personales Windows con la [administración de dispositivos móviles](windows-enroll.md) en Intune. Los dispositivos inscritos con el [agente de PC de Intune](manage-windows-pcs-with-microsoft-intune.md) no se puede bloquear con esta característica.
Para ver esta característica, elija **Inscripción del dispositivo** > **Restricciones de dispositivos**.
La activación de esta restricción no tiene ningún efecto en los dispositivos ya inscritos.
Una vez activada una restricción, Intune realiza comprobaciones para asegurarse de que se ha autorizado cada nueva solicitud de inscripción de Windows como una inscripción corporativa. Los métodos siguientes se consideran como autorizados como una inscripción corporativa:
- El usuario que se inscribe usa una [cuenta de administrador de inscripción de dispositivos]( device-enrollment-manager-enroll.md).
- El dispositivo se inscribe a través de [Windows AutoPilot](enrollment-autopilot.md).
- Número IMEI del dispositivo aparece en **Inscripción del dispositivo** > **[Identificadores de dispositivo corporativos]( corporate-identifiers-add.md)**.
- El dispositivo se inscribe a través de un [paquete de aprovisionamiento en masa](windows-bulk-enroll.md).
- El dispositivo se inscribe a través de la [inscripción automática de SCCM para la administración conjunta](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management).

Las inscripciones no autorizadas se bloquearán. Intune marca las inscripciones siguientes como corporativas, pero dado que no ofrecen control por dispositivo del administrador de Intune, se bloquearán:
- [Inscripción automática de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con [combinación de Azure Active Directory durante la instalación de Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).
- [Inscripción automática de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con [combinación de Azure Active Directory desde la instalación de Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).

También se bloquearán los siguientes métodos de inscripción personal:
- [Inscripción automática de MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) con [incorporación de cuenta profesional desde la instalación de Windows](https://docs.microsoft.com/azure/active-directory/user-help/device-management-azuread-registered-devices-windows10-setup).
- Opción de [solo inscripción de MDM]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) desde la instalación de Windows.

### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Especificación de patrones de nombre de equipo en un perfil de AutoPilot <!--1849855-->
Podrá especificar una plantilla de nombre de equipo para generar y establecer el [nombre de equipo](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) durante una inscripción de AutoPilot. Necesitará especificar esto en el perfil de AutoPilot ubicado en **Inscripción del dispositivo** > **Inscripción de Windows** > **Windows Autopilot Deployment service (Servicio Windows Autopilot Deployment)** > **Perfiles**. Solo se pueden usar caracteres alfanuméricos y guiones.
Se aplica a Windows Insider 1809 o una compilación posterior (todavía en versión preliminar).

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>Se muestran el número de versión y el número de compilación de iOS <!-- 1892471 -->
En **Cumplimiento del dispositivo** > **Cumplimiento del dispositivo**, se muestra la versión del sistema operativo iOS. En una actualización futura, también se mostrará el número de compilación.
Cuando se publican las actualizaciones de seguridad, Apple normalmente deja el número de versión como está, pero actualiza el número de compilación. Al mostrar el número de compilación, puede comprobar fácilmente si se instala una actualización de vulnerabilidad.

### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Para los perfiles de Windows AutoPilot, oculte las opciones de cambio de cuenta en las páginas de inicio de sesión de la compañía y de error de dominio <!--1901669 -->
Una versión preliminar pública incluirá nuevas opciones de perfil de Windows AutoPilot para que los administradores oculten las opciones de cambio de cuenta en las páginas de inicio de sesión de la compañía y de error de dominio. La ocultación de estas opciones requiere que se configure la personalización de marca de empresa en Azure Active Directory. Se aplica a Windows Insider 1809 o una compilación posterior (todavía en versión preliminar).

### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Retraso cuando las actualizaciones de software de iOS se muestran en el dispositivo <!-- 1949583 -->
En Intune > **Actualizaciones de software** > **Directivas de actualización para iOS**, puede configurar los días y las horas en los que no desea que los dispositivos instalen ninguna actualización. En una actualización futura, podrá retrasar entre 1 y 90 días el momento en el que una actualización de software se muestra de forma visible en el dispositivo. 
[Configurar directivas de actualización de iOS en Microsoft Intune](software-updates-ios.md) enumera la configuración actual.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos retirados en el panel de cumplimiento del dispositivos <!-- 1981119 -->
En una actualización futura, los dispositivos retirados se quitarán del panel de cumplimiento del dispositivo. Esto cambiará los números de cumplimiento.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Actualización de la experiencia de usuario en el sitio web de Portal de empresa <!--2000968 -->
Tras escuchar los comentarios de los clientes, se agregarán nuevas características al sitio web de Portal de empresa. Podrá comprobar una mejora considerable en las funciones y la facilidad de uso actual de los dispositivos Android, iOS y Windows. Se aplicará un diseño moderno y receptivo a las áreas del sitio, como los detalles del dispositivo, los comentarios, el soporte técnico y la descripción general del dispositivo. También verá:
- Flujos de trabajo simplificados en todas las plataformas del dispositivo
- Flujos mejorados para la identificación y la inscripción de dispositivos
- Mensajes de error más útiles
- Lenguaje más descriptivo con menos jerga técnica
- Posibilidad de compartir vínculos directos a aplicaciones
- Mejor rendimiento de los catálogos de aplicaciones de gran tamaño
- Mayor accesibilidad para todos los usuarios

### <a name="office-365-proplus-version----2213968-eeready---"></a>Versión de Office 365 ProPlus <!-- 2213968 eeready -->
Al asignar las aplicaciones de Office 365 ProPlus a dispositivos Windows 10 mediante Intune, podrá seleccionar la versión de Office. En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones** > **Agregar aplicación**. Después, seleccione **Conjunto de aplicaciones Office 365 ProPlus (Windows 10)** en la lista desplegable **Tipo**. Seleccione **Configuración del conjunto de aplicaciones** para mostrar la hoja asociada. Establezca **Canal de actualización** en un valor, como **Mensualmente**. Si lo desea, quite otra versión de Office (msi) de los dispositivos del usuario final seleccionando **Sí**. Seleccione **Específico** para instalar una versión específica de Office del canal seleccionado en los dispositivos del usuario final. En este momento, en **Versión específica**, puede seleccionar la versión de Office que desee usar. Las versiones disponibles cambiarán con el tiempo. Por lo tanto, al crear una nueva implementación, las versiones disponibles pueden ser más recientes y no tener determinadas versiones anteriores disponibles. Las implementaciones actuales seguirán implementando la versión anterior, pero la lista de versiones se actualizará continuamente por canal. Para más información, vea [Información general de los canales de actualización para Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configuración del perfil para omitir algunas pantallas durante el Asistente para configuración <!-- 2276470 -->
Cuando cree un perfil de inscripción de macOS, podrá configurarlo para omitir cualquiera de las siguientes pantallas cuando un usuario recorra el Asistente para configuración:
- Migración de Android
- Tono de visualización
- Privacidad
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Cambio en el proceso de actualización para conectores locales <!-- 2277554 -->
Según los comentarios de clientes, se cambiará la manera en que se realizan las actualizaciones en los conectores locales. Después de instalar inicialmente un conector local, las actualizaciones se producirán automáticamente. Este cambio se iniciará con el nuevo conector de certificado PFX para Microsoft Intune y posteriormente se implementará en otros tipos de conectores locales. 

### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Compatibilidad con la configuración de DNS de registro para VPN de Windows 10 <!-- 2282852 -->
Podrá configurar perfiles de VPN de Windows 10 para registrar dinámicamente las direcciones IP asignadas a la interfaz VPN con el DNS interno, sin necesidad de usar perfiles personalizados.
[Configuración de VPN de Windows 10](vpn-settings-windows-10.md) muestra la configuración de perfil de VPN disponible. 

### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-for-work-devices----2451462---"></a>Restricción de aplicaciones y bloqueo del acceso a los recursos de la compañía en iOS y Android para dispositivos de trabajo <!-- 2451462 -->
En **Cumplimiento del dispositivo** > **Directivas** > **Crear directiva** > **Android for Work (Android para el trabajo)** > **Seguridad del sistema**, estará la nueva opción **Restricted applications (Aplicaciones restringidas)**. Esta nueva opción usa una directiva de cumplimiento para bloquear el acceso a recursos de la compañía si ciertas aplicaciones están instaladas en el dispositivo. El dispositivo se considera no compatible hasta que las aplicaciones restringidas se quitan del dispositivo.
Se aplica a: 
- iOS

### <a name="export-azure-classic-portal-compliance-policies-to-csv-file----2469637---"></a>Exportación de las directivas de cumplimiento del Portal de Azure clásico al archivo .csv <!-- 2469637 -->
Las directivas de cumplimiento creadas en el Portal de Azure clásico dejarán de utilizarse.  Cuando esto suceda, podrá revisar y eliminar todas las directivas existentes, pero no podrá actualizarlas. Puede exportar las directivas como un archivo separado por comas (archivo .csv). Después, utilice los detalles del archivo para volver a crear estas directivas en Intune en Azure Portal.
> [!IMPORTANT]
> Cuando el Portal de Azure clásico se retire, no podrá acceder a sus directivas ni tampoco verlas. Por lo tanto, asegúrese de exportarlas y volverlas a crear en Azure Portal antes de la retirada del Portal de Azure clásico.

### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Cambio de terminología a "retirar" y "borrar" <!-- 2175759 -->
Para mantener la coherencia con Graph API, la documentación y la interfaz de usuario de Intune cambiarán los términos siguientes:
- **Eliminar datos de la compañía** cambiará a **retirar**
- **Restablecimiento de fábrica** cambiará a **borrar**

### <a name="delete-jamf-devices----2653306---"></a>Eliminación de dispositivos Jamf <!-- 2653306 -->
Podrá eliminar los dispositivos administrados por Jamf en **Dispositivos** > Dispositivo de Jamf > **Eliminar**.

<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>Más oportunidades de sincronización en la aplicación Portal de empresa para Windows <!-- 2683177 -->
La aplicación Portal de empresa para Windows agrega una acción de sincronización de dispositivo a la barra de tareas de Windows y listas de salto al menú Inicio. Haga clic en cualquier ubicación para sincronizar rápidamente los dispositivos y obtener acceso a recursos corporativos.  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Códigos de acceso para restablecer el dispositivo desde la aplicación Portal de empresa para Windows 10 <!-- 2101282 --> 
Los empleados pronto podrán restablecer el PIN o el código de acceso de su dispositivo directamente desde la aplicación Portal de empresa para Windows 10. Esta funcionalidad estará disponible en los dispositivos remotos y locales administrados por Intune que admiten el restablecimiento de la contraseña. Según el tipo de dispositivo, una solicitud realizada para un dispositivo remoto eliminará el código de acceso actual del dispositivo o creará una contraseña temporal. Si un usuario solicita el restablecimiento para un dispositivo local, se le redirigirá a la aplicación de configuración del dispositivo.  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>Nuevas experiencias de navegación en la aplicación Portal de empresa para Windows <!-- 2317227 -->  
Al examinar o buscar aplicaciones en la aplicación Portal de empresa para Windows, podrá alternar entre la vista **Elementos** existente y la vista recién añadida **Detalles**. En la nueva vista se muestran detalles de la aplicación, como el nombre, el editor, la fecha de publicación y el estado de la instalación.  

La página **Aplicaciones** presentará una vista **Instaladas** que le permite ver detalles sobre las instalaciones de aplicaciones completadas y en curso. ¿Quiere compartir comentarios y opiniones sobre los nuevos cambios? Envíenos sus comentarios en la aplicación Portal de empresa.

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Mejora de la experiencia en la aplicación Portal de empresa para usuarios administradores de inscripciones de dispositivos <!-- 675800 -->
Cuando un administrador de inscripciones de dispositivos (DEM) inicia sesión en la aplicación Portal de empresa para Windows, la aplicación solo mostrará el dispositivo actual en ejecución de DEM. Esta mejora reduce los tiempos de espera que se han producido anteriormente cuando la aplicación ha intentado cargar todos los dispositivos inscritos en DEM.  

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Paquete de configuración de ATP de Windows Defender agregado automáticamente al perfil de configuración <!-- 2144658 -->
Cuando se usa la [Protección contra amenazas avanzada y la incorporación](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) de dispositivos en Intune, se descarga un paquete de configuración y se agrega al perfil de configuración. En una actualización futura, Intune obtendrá automáticamente el paquete del Centro de seguridad avanzada de Windows Defender y lo agregará al perfil.

Se aplica a Windows 10 y versiones posteriores.

### <a name="check-for-sccm-compliance----2192052---"></a>Comprobación de la conformidad de SCCM <!-- 2192052 -->
Una actualización futura incluirá una nueva configuración de conformidad de System Center Configuration Manager (SCCM) (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Windows 10**). SCCM envía señales a la conformidad de Intune. Mediante la configuración de Intune, puede exigir que todas las señales de SCCM devuelvan "conforme".

Por ejemplo, exige que todas las actualizaciones de software se instalen en los dispositivos. En SCCM, este requisito tiene el estado "Instalado". Si algún programa del dispositivo se encuentra en estado desconocido, el dispositivo no será conforme en Intune.

Se aplica a Windows 10 y versiones posteriores

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas sobre tokens de VPP que expiran próximamente o licencias del Portal de empresa a punto de agotarse <!-- 2237572 -->
Si usa el Programa de Compras por Volumen (VPP) para tener en servicio el Portal de empresa durante la inscripción de DEP, Intune le avisará cuando el token de VPP esté a punto de expirar y las licencias del Portal de empresa se estén agotando.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmación requerida para eliminar el token de VPP que se usa para tener en servicio el Portal de empresa <!-- 2237634 -->
Se solicitará confirmación para eliminar un token del Programa de Compras por Volumen (VPP) si se usa para tener en servicio el Portal de empresa durante la inscripción de DEP.

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Configuración de seguridad adicional de Windows Installer <!-- 2282430 -->
Podrá dejar que los usuarios controlen las instalaciones de aplicaciones. Si lo permite, las instalaciones que antes se detendrían debido a una infracción de seguridad podrán seguir funcionando. Podrá indicar a Windows Installer que use permisos elevados cuando instale un programa en un sistema. Además, podrá habilitar elementos protegidos por WIP (Windows Information Protection) para indexarlos y almacenar los metadatos relativos a estos elementos en una ubicación sin cifrar. Cuando la directiva está deshabilitada, los elementos protegidos por WIP no se indexarán ni se mostrarán en los resultados de Cortana o del explorador de archivos. La funcionalidad de estas opciones estará deshabilitada de forma predeterminada. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Configuración de la directiva de protección de aplicaciones para el bloqueo de teclados de terceros en iOS <!-- 1248481 -->
En dispositivos iOS, los administradores de Intune podrán bloquear el uso de teclados de terceros al acceder a datos de la organización en aplicaciones protegidas mediante directiva. Cuando la directiva de protección de aplicación (APP) esté configurada para bloquear teclados de terceros, el usuario del dispositivo recibirá un mensaje la primera vez que interactúe con datos corporativos usando un teclado de terceros. Se bloquearán todas las demás opciones, que no afecten al teclado nativo, y los usuarios de los dispositivos no podrán verlas. Los usuarios de los dispositivos verán el mensaje del cuadro de diálogo una vez. 

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Exigir código de acceso no biométrico al transcurrir tiempo de espera y al iniciar la aplicación <!-- 1506985 -->

Al exigir un código de acceso no biométrico al iniciar la aplicación y después de transcurrir un tiempo de espera especificado por el administrador, Intune proporcionará una mayor seguridad para las aplicaciones compatibles con Administración de aplicaciones de móviles (MAM), ya que restringe el uso de identificación biométrica para el acceso a datos corporativos. La configuración afectará a los usuarios que dependen de Touch ID (iOS), Face ID (iOS), Android Biometric u otros métodos de autenticación biométrica futuros para tener acceso a aplicaciones compatibles con APP/MAM. Con esta configuración, los administradores de Intune tendrán un control más detallado sobre el acceso de los usuarios. De este modo, se evitan situaciones en las que un dispositivo con varias huellas digitales u otros métodos de acceso biométrico pueda revelar datos corporativos a un usuario incorrecto. En Azure Portal, abra **Microsoft Intune**. Seleccione **Aplicaciones móviles** > **Directivas de protección de aplicaciones** > **Agregar una directiva** > **Configuración**. En la **Acceso** encontrará ajustes específicos.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Paquetes de idioma de Office 365 Pro Plus <!-- 1833450 -->
Como administrador de Intune, podrá implementar idiomas adicionales para las aplicaciones Office 365 Pro Plus administradas mediante Intune. La lista de idiomas disponibles incluye el **Tipo** de paquete de idioma (núcleo, parcial y corrección). En el portal de Azure, seleccione **Microsoft Intune** > **Aplicaciones móviles** > **Aplicaciones** > **Agregar**. En la lista **Tipo de aplicación** de la hoja **Agregar aplicación**, seleccione **Windows 10** en **Conjunto de aplicaciones de Office 365**. Seleccione **Idiomas** en la hoja **Configuración del conjunto de aplicaciones**.

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Obtener una versión preliminar de una actualización de la experiencia de usuario en el sitio web de Portal de empresa <!--2000968 -->
Tras escuchar las opiniones de los clientes, estamos agregando nuevas características al sitio web de Portal de empresa y al catálogo de aplicaciones de iOS. Podrá comprobar una mejora considerable en las funciones y la facilidad de uso actual de los dispositivos Android, iOS y Windows. Se aplicará un diseño moderno y receptivo a las áreas del sitio, como los detalles del dispositivo, los comentarios, el soporte técnico y la descripción general del dispositivo. También verá:

- Flujos de trabajo simplificados en todas las plataformas del dispositivo
- Flujos mejorados para la identificación y la inscripción de dispositivos
- Mensajes de error más útiles
- Lenguaje más descriptivo con menos jerga técnica
- Posibilidad de compartir vínculos directos a aplicaciones
- Mejor rendimiento de los catálogos de aplicaciones de gran tamaño
- Mayor accesibilidad para todos los usuarios

Actualmente, la actualización está disponible en versión preliminar. Puede registrarse para unirse a la versión preliminar en http://aka.ms/webcpflighting.

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Exigir código de acceso no biométrico al transcurrir tiempo de espera y al iniciar la aplicación en frío<!-- 1506985 --> 

Al exigir un código de acceso no biométrico al iniciar la aplicación en frío y después de transcurrir un tiempo de espera especificado por el administrador, Intune proporcionará una mayor seguridad para las aplicaciones compatibles con Administración de aplicaciones de móviles (MAM), ya que restringe el uso de identificación biométrica para el acceso a datos corporativos. La configuración afectará a los usuarios que dependen de Touch ID (iOS), Face ID (iOS), Android Biometric u otros métodos de autenticación biométrica futuros para tener acceso a aplicaciones compatibles con APP/MAM. Con esta configuración, los administradores de Intune tendrán un control más detallado sobre el acceso de los usuarios. De este modo, se evitan situaciones en las que un dispositivo con varias huellas digitales u otros métodos de acceso biométrico pueda revelar datos corporativos a un usuario incorrecto. En Azure Portal, abra **Microsoft Intune**. Seleccione **Aplicaciones móviles** > **Directivas de protección de aplicaciones** > **Agregar una directiva** > **Configuración**. En la **Acceso** encontrará ajustes específicos.

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidad de implementar aplicaciones de línea de negocio (LOB) requeridas en todos los usuarios en dispositivos Windows 10 Escritorio <!-- 1627835 RS4 -->
Los clientes podrán implementar aplicaciones de Windows 10 de línea de negocio requeridas para instalarlas en contextos de dispositivo. Esto permitirá que estas aplicaciones estén disponibles para todos los usuarios del dispositivo. Esto solo es aplicable a dispositivos Windows 10 Escritorio.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Actualización de la experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android <!--1631531 -->

La experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android se actualizará de acuerdo con los procedimientos recomendados para las aplicaciones Android. En los próximos meses actualizaremos la aplicación Portal de empresa para Android para dividir el elemento de menú **Ayuda y comentarios** en los elementos de menú independientes **Ayuda** y **Enviar comentarios**. En la página **Ayuda** se incluirá una sección **Preguntas más frecuentes** y un botón **Soporte por correo electrónico** para permitir a los usuarios finales cargar registros a Microsoft y enviar al equipo de soporte técnico de la empresa un correo electrónico en el que se describa el problema. **Enviar comentarios** llevará al usuario a través de un proceso estándar de envío de comentarios de Microsoft, en el que se le pedirá elegir entre "Me gusta algo", "No me gusta algo" o "Tengo una idea".

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Directivas de protección de aplicaciones  <!-- 679615 -->
Las directivas de Intune App Protection ofrecerán la capacidad de crear directivas predeterminadas globales para habilitar rápidamente la protección en todos los usuarios de todo el inquilino.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.

### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.



