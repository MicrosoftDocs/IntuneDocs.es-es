---
title: Novedades de Microsoft Intune (Azure) | Microsoft Docs
titlesuffix: ''
description: Descubra las novedades del portal de Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: 0205715a8e35d009401886af4bd0bf88fb9cf662
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347294"
---
# <a name="whats-new-in-microsoft-intune"></a>Novedades de Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Conozca las novedades semanales de Microsoft Intune. También podrá obtener información sobre los [próximos cambios](#whats-coming), [notificaciones importantes](#notices) sobre el servicio e información sobre las [versiones anteriores](whats-new-archive.md). Algunas características pueden lanzarse a lo largo de varias semanas y pueden no estar disponibles para todos los clientes durante la primera semana.

> [!Note]
> Para obtener más información sobre la nueva funcionalidad de administración híbrida de dispositivos móviles (MDM), consulte la [página Novedades de MDM híbrida](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   

## <a name="week-of-august-27-2018"></a>Semana del 27 de agosto de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Compatibilidad de túnel de paquete para perfiles de VPN por aplicación de iOS para los tipos de conexión Pulse Secure y personalizados <!-- 1520957 -->
Al usar perfiles de VPN por aplicación de iOS, puede elegir entre usar tunelización de capa de aplicación (app-proxy) o tunelización de nivel de paquete (packet-tunnel). Estas opciones están disponibles con los tipos de conexión siguientes:
- VPN personalizada
- Pulse Secure. Si no está seguro de qué valor usar, consulte la documentación de su proveedor de VPN.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Retraso cuando las actualizaciones de software de iOS se muestran en el dispositivo <!-- 1949583 -->
En Intune > **Actualizaciones de software** > **Directivas de actualización para iOS**, puede configurar los días y las horas en los que no desea que los dispositivos instalen ninguna actualización. En una actualización futura, podrá retrasar entre 1 y 90 días el momento en el que una actualización de software se muestra de forma visible en el dispositivo. 
[Configurar directivas de actualización de iOS en Microsoft Intune](software-updates-ios.md) enumera la configuración actual.

#### <a name="office-365-proplus-version----2213968---"></a>Versión de Office 365 ProPlus <!-- 2213968 -->
Al asignar las aplicaciones de Office 365 ProPlus a dispositivos Windows 10 mediante Intune, podrá seleccionar la versión de Office. En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones** > **Agregar aplicación**. Después, seleccione **Conjunto de aplicaciones Office 365 ProPlus (Windows 10)** en la lista desplegable **Tipo**. Seleccione **Configuración del conjunto de aplicaciones** para mostrar la hoja asociada. Establezca **Canal de actualización** en un valor, como **Mensualmente**. Si lo desea, quite otra versión de Office (msi) de los dispositivos del usuario final seleccionando **Sí**. Seleccione **Específico** para instalar una versión específica de Office del canal seleccionado en los dispositivos del usuario final. En este momento, en **Versión específica**, puede seleccionar la versión de Office que desee usar. Las versiones disponibles cambiarán con el tiempo. Por lo tanto, al crear una nueva implementación, las versiones disponibles pueden ser más recientes y no tener determinadas versiones anteriores disponibles. Las implementaciones actuales seguirán implementando la versión anterior, pero la lista de versiones se actualizará continuamente por canal. Para más información, vea [Información general de los canales de actualización para Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Compatibilidad con la configuración de DNS de registro para VPN de Windows 10 <!-- 2282852 -->
Con esta actualización, puede configurar perfiles de VPN de Windows 10 para registrar dinámicamente las direcciones IP asignadas a la interfaz VPN con el DNS interno, sin necesidad de usar perfiles personalizados.
Para obtener información sobre la configuración de perfil de VPN actual disponible, vea [Configuración de VPN de Windows 10](vpn-settings-windows-10.md). 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>El instalador de Portal de empresa para macOS ahora incluye el número de versión en el nombre de archivo del instalador <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759-wnready---"></a>Actualizaciones de aplicaciones automáticas de iOS <!-- 2729759 wnready -->
Las actualizaciones de aplicaciones automáticas funcionan para las aplicaciones con licencia de dispositivo y usuario para la versión 11.0 de iOS y versiones posteriores.




### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello está dirigido a usuarios y dispositivos <!-- 1106609 -->
Cuando crea una directiva [Windows Hello para empresas](windows-hello.md), se aplica a todos los usuarios dentro de la organización (inquilinos). Con esta actualización, la directiva también se puede aplicar a determinados usuarios o específicos mediante una directiva de configuración de dispositivo (**Configuración del dispositivo** > **Perfiles**  >  **Crear perfil** > **Identity Protection** > **Windows Hello para empresas**).
En Intune en Azure Portal, la configuración de Windows Hello ahora existe tanto en **Inscripción del dispositivo** como en **Configuración del dispositivo**. **Inscripción del dispositivo** tiene como destino toda la organización (inquilinos) y es compatible con Windows AutoPilot (OOBE). **Configuración del dispositivo** tiene como destino los dispositivos y usuarios mediante una directiva que se aplica durante la inserción en el repositorio.
Esta característica se aplica a:  
- Windows 10 y versiones posteriores
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>Zscaler es una conexión disponible para los perfiles VPN en iOS <!-- 1769858 eeready -->
Cuando crea un perfil de configuración de dispositivo de VPN para iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > plataforma **iOS** > tipo de perfil **VPN**), hay varios tipos de conexión, incluidos Cisco, Citrix, etc. Esta actualización agrega Zscaler como un tipo de conexión. 
[Configuración de VPN para dispositivos que ejecutan iOS](vpn-settings-ios.md) enumera los tipos de conexión disponibles.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077-eeready---"></a>Modo FIPS para perfiles de Wi-Fi de empresa para Windows 10 <!-- 1879077 eeready -->
Ahora puede habilitar el modo Estándar federal de procesamiento de información (FIPS) para los perfiles de Wi-Fi de empresa para Windows 10 en Intune en Azure Portal. Asegúrese de que el modo FIPS está habilitado en la infraestructura de Wi-Fi si lo habilita en los perfiles de Wi-Fi.
En [Configuración de Wi-Fi para dispositivos Windows 10 y versiones posteriores en Intune](wi-fi-settings-windows.md) se muestra cómo crear un perfil de Wi-Fi.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Control del modo S en Windows 10 y dispositivos posteriores: versión preliminar pública <!-- 1958649 -->
Con esta actualización de características, puede crear un perfil de configuración de dispositivo que haga cambiar el modo S de un dispositivo Windows 10 o evitar que los usuarios cambien el modo S del dispositivo. Esta característica está en Intune > **Configuración del dispositivo** > **Perfiles** >  **Windows 10 y versiones posteriores** > **Edition upgrade and mode switch (Actualización de edición y conmutación de modo)**.
En [Presentamos Windows 10 en modo S](https://www.microsoft.com/windows/s-mode) se proporciona más información sobre el modo S.
Se aplica a Windows 10 y versiones posteriores (1809 y posteriores)

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Paquete de configuración de ATP de Windows Defender agregado automáticamente al perfil de configuración <!-- 2144658 -->
Cuando se usa la [Protección contra amenazas avanzada y la incorporación](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) de dispositivos en Intune, antes era necesario descargar un paquete de configuración y agregarlo al perfil de configuración. Con esta actualización, Intune obtiene de forma automática el paquete del Centro de seguridad avanzada de Windows Defender y lo agrega al perfil.
Se aplica a Windows 10 y versiones posteriores.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Requerir que los usuarios se conecten durante la instalación del dispositivo <!--2311457-->
Ahora puede establecer los perfiles de dispositivo para requerir que el dispositivo se conecte a una red antes de continuar más allá de la página Red durante la instalación de Windows 10. Aunque esta característica está en versión preliminar, se requiere una compilación 1809 de Windows Insider o una versión posterior para usar esta configuración.

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Restricción de aplicaciones y bloqueo del acceso a los recursos de la empresa en dispositivos iOS y Android Enterprise <!-- 2451462 -->
En **Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **iOS** > **Seguridad del sistema**, hay una nueva opción **Aplicaciones restringidas**. Esta nueva opción usa una directiva de cumplimiento para bloquear el acceso a recursos de la compañía si ciertas aplicaciones están instaladas en el dispositivo. El dispositivo se considera no compatible hasta que las aplicaciones restringidas se quitan del dispositivo.
Se aplica a iOS.

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Actualizaciones de compatibilidad con VPN moderna para iOS <!-- 2459928, 1819876, and 2650856 -->
Esta actualización agrega compatibilidad con los siguientes clientes VPN de iOS: 
- F5 Access (versión 3.0.1 y versiones posteriores)
- SSO de Citrix
- GlobalProtect de Palo Alto Networks versión 5.0 y versiones posteriores. También en esta actualización:
- El nombre del tipo de conexión de **F5 Access** existente se cambia a **F5 Access Legacy** para iOS.
- El nombre del tipo de conexión de **GlobalProtect de Palo Alto Networks** existente se cambia a **GlobalProtect de Palo Alto Networks (legacy)** para iOS.
Los perfiles existentes con estos tipos de conexión siguen funcionando con su correspondiente cliente heredado de VPN. Si usa Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN o GlobalProtect de Legacy Palo Alto Networks versión 4.1 y versiones anteriores con iOS, debe cambiar a las nuevas aplicaciones. Hágalo tan pronto como sea posible para garantizar que el acceso VPN esté disponible para dispositivos iOS a medida que se actualicen a iOS 12.
Para obtener más información sobre iOS 12 y los perfiles de VPN, vea el [blog del equipo de soporte técnico de Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Exportación de las directivas de cumplimiento del Portal de Azure clásico para volver a crearlas en Intune en Azure Portal <!-- 2469637 -->
Las directivas de cumplimiento creadas en el Portal de Azure clásico dejarán de utilizarse. Puede revisar y eliminar todas las directivas de cumplimiento existentes, pero no podrá actualizarlas. Si tiene que migrar las directivas de cumplimiento a Intune en Azure Portal, puede exportarlas como un archivo separado por comas (archivo *.csv*). Después, use los detalles del archivo para volver a crear estas directivas en Intune en Azure Portal.

> [!IMPORTANT]
> Cuando se retire el Portal de Azure clásico, ya no podrá acceder ni ver las directivas de cumplimiento. Por tanto, asegúrese de exportar las directivas y volverlas a crear en Azure Portal antes de la retirada del Portal de Azure clásico.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile: nuevo socio de Mobile Threat Defense <!-- 22662717 -->
Puede controlar el acceso desde dispositivos móviles a los recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Better Mobile, una solución de Mobile Threat Defense integrada en Microsoft Intune.

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Bloqueo del Portal de empresa en el modo de aplicación única hasta el inicio de sesión del usuario <!--1067692 --> 
Ahora tiene la opción de ejecutar Portal de empresa en el modo de aplicación única si autentica un usuario a través de Portal de empresa en lugar del Asistente para configuración durante la inscripción de DEP. Esta opción bloquea el dispositivo inmediatamente después de completar el Asistente para configuración, de manera que un usuario debe iniciar sesión para acceder al dispositivo. Este proceso garantiza que el dispositivo completa la incorporación y no está huérfano en un estado sin ningún usuario asociado.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Asignación de un usuario y un nombre descriptivo a un dispositivo AutoPilot <!--1346521 -->
Ahora puede [asignar un usuario a un único dispositivo Autopilot ](enrollment-autopilot.md). Los administradores también podrán proporcionar nombres descriptivos para saludar a los usuarios al configurar sus dispositivos con AutoPilot.
Se aplica a Windows Insider 1809 o una compilación posterior (todavía en versión preliminar).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Use licencias de dispositivo de VPP para tener en servicio el Portal de empresa durante la inscripción de DEP <!-- 1608345 -->
Ahora puede usar licencias de dispositivo del Programa de compras por volumen (VPP) para aprovisionar previamente Portal de empresa durante las inscripciones en el Programa de inscripción de dispositivos (DEP). Para ello, al [crear o editar un perfil de inscripción](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), especifique el token de VPP que quiera usar para instalar Portal de empresa. Asegúrese de que el token no expire y que dispone de suficientes licencias para la aplicación de Portal de empresa. En los casos en los que el token expire o se agoten las licencias, Intune instalará el Portal de empresa del App Store (se solicitará un identificador de Apple).

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloqueo de inscripciones de dispositivos personales Windows <!-- 1849498 -->
Puede [bloquear la inscripción de dispositivos personales Windows](enrollment-restrictions-set.md#set-device-type-restrictions) con la [administración de dispositivos móviles](windows-enroll.md) en Intune. Los dispositivos inscritos con el [agente de PC de Intune](manage-windows-pcs-with-microsoft-intune.md) no se puede bloquear con esta característica.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Especificación de patrones de nombre de equipo en un perfil de AutoPilot <!--1849855-->
Puede [especificar una plantilla de nombre de equipo](enrollment-autopilot.md#create-an-autopilot-deployment-profile) para generar y establecer el [nombre de equipo](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) durante la inscripción de AutoPilot.

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Para los perfiles de Windows AutoPilot, oculte las opciones de cambio de cuenta en las páginas de inicio de sesión de la compañía y de error de dominio <!--1901669 -->
Hay [nuevas opciones de perfil de Windows AutoPilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile) para que los administradores oculten las opciones de cambio de cuenta en las páginas de inicio de sesión de la empresa y de error de dominio. La ocultación de estas opciones requiere que se configure la personalización de marca de empresa en Azure Active Directory. Se aplica a Windows Insider 1809 o una compilación posterior (todavía en versión preliminar).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Use licencias de dispositivo de VPP para tener en servicio el Portal de empresa durante la inscripción de DEP <!-- 1608345 -->
Ahora puede usar licencias de dispositivo del Programa de compras por volumen (VPP) para aprovisionar previamente Portal de empresa durante las inscripciones en el Programa de inscripción de dispositivos (DEP). Para ello, al [crear o editar un perfil de inscripción](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), especifique el token de VPP que quiera usar para instalar Portal de empresa. Asegúrese de que el token no expire y que dispone de suficientes licencias para la aplicación de Portal de empresa. En los casos en los que el token expire o se agoten las licencias, Intune instalará el Portal de empresa del App Store (se solicitará un identificador de Apple).

### <a name="device-management"></a>Administración de dispositivos

#### <a name="delete-jamf-devices----2653306--"></a>Eliminación de dispositivos Jamf <!-- 2653306-->
Puede eliminar los dispositivos administrados por JAMF desde **Dispositivos** > seleccione el dispositivo de Jamf > **Eliminar**.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Cambio de terminología a "retirar" y "borrar" <!-- 2175759 -->
Para mantener la coherencia con Graph API, en la documentación y la interfaz de usuario de Intune se han cambiado los términos siguientes:
- **Eliminar datos de la compañía** se cambiará por "retirar".
- **Restablecimiento de fábrica** cambiará a **borrar**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>Cuadro de diálogo de confirmación si el administrador intenta eliminar el certificado push MDM <!-- 297909500-->
Si alguien intenta eliminar un certificado push MDM de Apple, en un cuadro de diálogo de confirmación se muestra el número de dispositivos iOS y macOS relacionados. Si se elimina el certificado, será necesario volver a inscribir estos dispositivos.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Configuración de seguridad adicional de Windows Installer <!-- 2282430 -->
Puede dejar que los usuarios controlen las instalaciones de aplicaciones. Si lo permite, las instalaciones que antes se detendrían debido a una infracción de seguridad podrán seguir funcionando. Puede indicar a Windows Installer que use permisos elevados cuando instale un programa en un sistema. Además, los elementos protegidos por WIP (Windows Information Protection) se pueden indexar y los metadatos relativos a estos elementos se pueden almacenar en una ubicación sin cifrar. Cuando la directiva está deshabilitada, los elementos protegidos por WIP no se indexan y no se muestran en los resultados de Cortana o del explorador de archivos. La funcionalidad de estas opciones está deshabilitada de forma predeterminada. 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Actualización de la experiencia de usuario en el sitio web de Portal de empresa <!--2000968 -->
Tras escuchar las opiniones de los clientes, se han agregado características nuevas al sitio web de Portal de empresa. Experimentará una mejora considerable en las funciones y la facilidad de uso actual de los dispositivos. Se ha aplicado un nuevo diseño moderno y dinámico a las áreas del sitio, como los detalles del dispositivo, los comentarios, el soporte técnico y la descripción general del dispositivo. También verá:

- Flujos de trabajo simplificados en todas las plataformas del dispositivo
- Flujos mejorados para la identificación y la inscripción de dispositivos
- Mensajes de error más útiles
- Lenguaje más descriptivo con menos jerga técnica
- Posibilidad de compartir vínculos directos a aplicaciones
- Mejor rendimiento de los catálogos de aplicaciones de gran tamaño
- Mayor accesibilidad para todos los usuarios  

Se ha actualizado la [documentación del sitio web de Portal de empresa de Intune](https://docs.microsoft.com/en-us/intune-user-help/using-the-intune-company-portal-website) para reflejar estos cambios. Para ver un ejemplo de las mejoras de la aplicación, vea [Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Detección de jailbreak mejorada en informes de cumplimiento<!-- 2198738 -->
Ahora la configuración de detección de jailbreak mejorada aparece en todos los informes de cumplimiento en la consola de administración.

### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="scope-tags-for-policies---1081974-eeready--"></a>Etiquetas de ámbito para las directivas <!--1081974 eeready-->
Puede crear [etiquetas de ámbito](scope-tags.md) para limitar el acceso a los recursos de Intune. Agregue una etiqueta de ámbito a una asignación de roles y luego agregue dicha etiqueta a un perfil de configuración. El rol solo tendrá acceso a los recursos con perfiles de configuración que tengan etiquetas de ámbito coincidentes (o no tengan ninguna etiqueta de ámbito).

## <a name="week-of-august-14-2018"></a>Semana del 14 de agosto de 2018

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Compatibilidad de macOS para el Programa de inscripción de dispositivos de Apple <!-- 747651 -->
Intune ahora admite la inscripción de dispositivos macOS el Programa de inscripción de dispositivos de Apple (DEP). Para obtener más información, vea [Inscripción automática de dispositivos macOS con el Programa de inscripción de dispositivos de Apple](device-enrollment-program-enroll-macos.md).

## <a name="week-of-july-23-2018"></a>Semana del 23 de julio de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Compatibilidad con aplicaciones de línea de negocio (LOB) para macOS <!-- 1895847 -->
Microsoft Intune permite implementar aplicaciones de LOB macOS como **Required** (Obligatoria) o como **Available with enrollment** (Disponible con inscripción). Los usuarios finales pueden obtener las aplicaciones implementadas como **Available** (Disponible) a través del Portal de empresa para macOS o del [sitio web del Portal de empresa](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Compatibilidad con aplicaciones integradas de iOS para pantalla completa <!-- 2051098 -->
Además de las aplicaciones de la Tienda y las aplicaciones administradas, ahora puede seleccionar una aplicación integrada (como Safari) que se ejecuta en pantalla completa en un dispositivo iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Editar implementaciones de aplicaciones de Office 365 Pro Plus <!-- 2150145 -->
Como administrador de Microsoft Intune, tiene más capacidad para editar las implementaciones de aplicaciones de Office 365 Pro Plus. Además, ya no tiene que eliminar las implementaciones para cambiar las propiedades del conjunto. En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones cliente** > **Aplicaciones**. En la lista de aplicaciones, seleccione su conjunto de aplicaciones Office 365 ProPlus.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>El SDK para aplicaciones de Intune para Android actualizado ya está disponible <!-- 2744271-->

Hay disponible una versión actualizada del SDK para aplicaciones de Intune para Android compatible con la versión de Android P. Si es desarrollador de aplicaciones y usa el SDK de Intune para Android, debe instalar la versión actualizada del SDK para aplicaciones de Intune a fin de garantizar que la funcionalidad de Intune dentro de las aplicaciones Android seguirá funcionando según lo esperado en dispositivos de Android P. En esta versión del SDK para aplicaciones de Intune se proporciona un complemento integrado que lleva a cabo las actualizaciones del SDK. No es necesario que reescriba ningún código existente que ya esté integrado. Para detalles, consulte el artículo sobre el [SDK de Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Si usa el anterior estilo de distintivo para Intune, se recomienda usar el icono de maletín. Para detalles de personalización de la marca, consulte [este repositorio de GitHub](https://github.com/msintuneappsdk/intune-app-partner-badge).


### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Uso de S/MIME para cifrar y firmar varios dispositivos de un usuario <!-- 1333642 -->
Esta actualización incluye cifrado de correo electrónico S/MIME mediante un nuevo perfil de certificado importado (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > seleccione la plataforma > tipo de perfil **Certificado PKCS importado**). En Intune, puede importar los certificados en formato PFX. Después, Intune puede entregar esos mismos certificados a varios dispositivos inscritos por un solo usuario. Esto también incluye lo siguiente:

- El perfil de correo electrónico de iOS nativo permite habilitar el cifrado S/MIME mediante certificados importados en formato PFX.
- La aplicación de correo nativo de los dispositivos Windows Phone 10 usa automáticamente el certificado S/MIME.
- Los certificados privados se pueden entregar en varias plataformas. Aun así, no todas las aplicaciones de correo electrónico son compatibles con S/MIME.
- En otras plataformas, podría tener que configurar manualmente la aplicación de correo electrónico para habilitar S/MIME.  
- Las aplicaciones de correo electrónico que admiten el cifrado S/MIME pueden controlar la recuperación de certificados para el cifrado de correo electrónico S/MIME de una manera que no es compatible con un servicio MDM, por ejemplo, si los lee desde el almacén de certificados del publicador.

Compatible con: Windows, Windows Phone 10, macOS, iOS y Android

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Crear directiva de cumplimiento de dispositivos usando la configuración de firewall en dispositivos macOS <!-- 1497640 -->
Cuando se crea una directiva de cumplimiento de macOS (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Plataforma: macOS** > **Seguridad del sistema**), hay nuevas opciones de **Firewall** disponibles: 

- **Firewall**: configure cómo se administran las conexiones entrantes en el entorno.
- **Conexiones entrantes**: **bloquee** todas las conexiones entrantes excepto las necesarias para los servicios básicos de Internet, como DHCP, Bonjour e IPSec. Esta opción también bloquea todos los servicios de uso compartido.
- **Modo sigiloso**: **habilite** el modo sigiloso para evitar que el dispositivo responda a solicitudes de sondeo. El dispositivo sigue respondiendo a las solicitudes entrantes de las aplicaciones autorizadas.

Se aplica a: macOS 10.12 y versiones posteriores

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Nuevo perfil de configuración de dispositivos Wi-Fi para Windows 10 y versiones posteriores <!-- 1879077 -->
Actualmente, puede importar y exportar perfiles de Wi-Fi mediante archivos XML. Con esta actualización, puede crear un perfil de configuración de dispositivo Wi-Fi directamente en Intune, igual que en otras plataformas.

Para crear el perfil, abra **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** > **Wi-Fi**. 

Se aplica a Windows 10 y versiones posteriores.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998-eeready---"></a>La característica Quiosco (obsoleto) aparece atenuada y no se puede cambiar <!-- 2149998 eeready -->
La [característica Quiosco](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** > **Restricciones de dispositivos**) está obsoleta y se sustituye por la [configuración de Quiosco para Windows 10 y versiones posteriores](kiosk-settings.md). Con esta actualización, la característica **Quiosco (obsoleto)** está atenuada y la interfaz de usuario no se puede modificar ni actualizar. 

Para habilitar el modo quiosco, vea [Configuración de quiosco para Windows 10 (y versiones posteriores)](kiosk-settings.md).

Se aplica a Windows 10 y versiones posteriores, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>API para usar entidades de certificación de terceros <!-- 2184013 -->
En esta actualización, hay una API de Java que permite que las entidades de certificación de terceros se integren con Intune y SCEP. Después, los usuarios pueden agregar el certificado SCEP a un perfil y aplicarlo a los dispositivos mediante MDM.

Actualmente, Intune admite [solicitudes SCEP mediante Servicios de certificados de Active Directory](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Alternar para mostrar u ocultar el botón Finalizar sesión en un explorador de Quiosco <!-- 2455253 -->
Ahora puede configurar si los exploradores de Quiosco muestran o no el botón Finalizar sesión. Puede ver el control en **Configuración del dispositivo** > **Quiosco (versión preliminar)** > **Kiosk Web Browser**. Si está activado, cuando un usuario hace clic en el botón, la aplicación solicita confirmación para finalizar la sesión. Cuando se confirma, el explorador borra todos los datos de exploración y vuelve a la dirección URL predeterminada.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Creación de un perfil de configuración de red de telefonía móvil eSIM <!-- 2564077 -->
En **Configuración del dispositivo**, puede crear un perfil de red de telefonía móvil eSIM. Puede importar un archivo que contenga códigos de activación de red de telefonía móvil proporcionados por el operador de telefonía móvil. Después, puede implementar estos perfiles en sus dispositivos Windows 10 habilitados para eSIM LTE, como Surface Pro LTE y otros dispositivos compatibles con eSIM.

Compruebe si sus [dispositivos admiten perfiles de eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Se aplica a Windows 10 y versiones posteriores. 




### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Marcado automático de dispositivos Android inscritos mediante Samsung Knox Mobile Enrollment como "corporativos". <!-- 2404851 -->
De forma predeterminada, los dispositivos Android inscritos mediante Samsung Knox Mobile Enrollment ahora se marcan como **corporativos** en **Propiedad del dispositivo**. No es necesario identificar manualmente los dispositivos corporativos mediante IMEI o números de serie antes de realizar la inscripción mediante Knox Mobile Enrollment.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Eliminación en masa de dispositivos en la hoja de dispositivos <!-- 1793693 -->

Ahora puede eliminar varios dispositivos a la vez en la hoja de dispositivos. Elija **Dispositivos** > **Todos los dispositivos** > seleccione los dispositivos que quiere eliminar > **Eliminar**. En el caso de los dispositivos que no se puedan eliminar, se mostrará una alerta.

## <a name="week-of-july-16-2018"></a>Semana del 16 de julio de 2018  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Más oportunidades de sincronización en la aplicación Portal de empresa para Windows  
La aplicación Portal de empresa para Windows ahora permite iniciar una sincronización directamente desde la barra de tareas de Windows y el menú Inicio. Esta característica es especialmente útil si la única tarea es sincronizar los dispositivos y obtener acceso a los recursos corporativos. Para acceder a la nueva característica, haga clic con el botón derecho en el icono de Portal de empresa que está anclado a la barra de tareas o el menú Inicio. En las opciones de menú (también denominada lista de accesos directos), seleccione **Sincronizar este dispositivo**. El Portal de empresa se abrirá en la página **Configuración** e iniciará la sincronización. Para comprobar la nueva funcionalidad, vea [Novedades de la interfaz de usuario](whats-new-app-ui.md).   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Nuevas experiencias de navegación en la aplicación Portal de empresa para Windows  

Ahora al examinar o buscar aplicaciones en la aplicación Portal de empresa para Windows, puede alternar entre la vista **Iconos** existente y la vista **Detalles** recién agregada. En la nueva vista se muestran detalles de la aplicación, como el nombre, el editor, la fecha de publicación y el estado de la instalación.  

La vista **Instaladas** de la página **Aplicaciones** permite ver detalles sobre las instalaciones de aplicaciones completadas y en curso. Para ver el aspecto de la vista nueva, vea [Novedades de la interfaz de usuario](whats-new-app-ui.md).  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Mejora de la experiencia en la aplicación Portal de empresa para administradores de inscripciones de dispositivos  
Cuando un administrador de inscripciones de dispositivos (DEM) inicia sesión en la aplicación Portal de empresa para Windows, ahora la aplicación solo mostrará el dispositivo en ejecución actual de DEM. Esta mejora reducirá los tiempos de espera que se producían anteriormente cuando la aplicación intentaba mostrar todos los dispositivos inscritos en DEM.  


## <a name="week-of-july-9-2018"></a>Semana del 9 de julio de 2018

### <a name="app-management"></a>Administración de aplicaciones

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloqueo del acceso a aplicaciones según proveedores y modelos de dispositivos no aprobados <!-- 1425689 ! -->
El administrador de TI de Intune puede aplicar una lista específica de fabricantes de dispositivos Android o modelos de iOS a través de las directivas de Intune App Protection. El administrador de TI puede brindar una lista de fabricantes separados por punto y coma para las directivas Android y los modelos de dispositivo para las directivas iOS. Las directivas de Intune App Protection solo son para Android e iOS. Se pueden realizar dos acciones independientes en esta lista especificada:
- Bloquear el acceso a la aplicación en dispositivos no especificados.
- O bien, borrar de manera selectiva los datos corporativos en dispositivos no especificados. 

El usuario no podrá acceder a la aplicación de destino si no se cumplen los requisitos que establece la directiva. En función de la configuración, se podrá bloquear al usuario o borrar de manera selectiva sus datos corporativos dentro de la aplicación. En dispositivos iOS, esta característica requiere el uso de ciertas aplicaciones (como WXP, Outlook, Managed Browser o Yammer) para integrar Intune APP SDK para que esta característica se aplique en las aplicaciones de destino. Esta integración se produce de manera gradual y depende de los equipos de la aplicación específica. En Android, esta característica requiere la versión más reciente de Portal de empresa. 

En dispositivos de usuario final, el cliente de Intune actúa en función de una coincidencia simple de las cadenas especificadas en la hoja de Intune para directivas de protección de aplicaciones. Esto depende por completo del valor que informa el dispositivo. Por lo tanto, se recomienda que el administrador de TI se asegure de que el comportamiento previsto sea preciso. Para ello, pruebe esta configuración en función de una variedad de fabricantes de dispositivos y de modelos dirigidos a un grupo de usuarios pequeño. En Microsoft Intune, seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones** para ver y agregar directivas de protección de aplicaciones. Para obtener más información sobre las directivas de protección de aplicaciones, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) y [Borrar los datos de forma selectiva mediante acciones de acceso de la directiva de protección de aplicaciones en Intune](app-protection-policies-access-actions.md).

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Acceso a la compilación de versión preliminar del Portal de empresa de macOS <!-- 1734766 -->
Con Microsoft AutoUpdate, puede registrarse para recibir antes las compilaciones si se une al programa Insider. El registro le permite usar el Portal de empresa actualizado antes de que esté disponible para los usuarios finales. Para obtener más información, vea el [blog de Microsoft Intune](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

## <a name="week-of-july-2-2018"></a>Semana del 2 de julio de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>Supervisar el estado de configuración de aplicaciones iOS por dispositivo <!-- 880037 -->
Como administrador de Microsoft Intune, puede supervisar el estado de configuración de aplicaciones iOS para cada dispositivo administrado. Desde **Microsoft Intune** en Azure Portal, seleccione **Dispositivos** > **Todos los dispositivos**. En la lista de dispositivos administrados, seleccione un dispositivo específico para mostrar una hoja para el dispositivo. En la hoja del dispositivo, seleccione **Configuración de aplicaciones**.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>Acceso a acciones para las directivas de protección de aplicaciones <!-- 1483510 -->
Puede configurar directivas de protección de aplicaciones para borrar, bloquear o advertir de forma expresa los dispositivos que no cumplan directivas. La acción *borrado* quita los datos corporativos de su empresa de un dispositivo. Si se lleva a cabo esta acción, el usuario del dispositivo recibe una notificación sobre el motivo del borrado y los pasos para corregirlo. En el caso de algunas configuraciones, como la versión mínima de SO, podrá aplicar varias acciones, como el bloqueo o el borrado. Cabe reseñar que estas acciones se desencadenan cuando la aplicación se inicia.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Borrado selectivo de datos de aplicaciones de la organización <!-- 1507030 -->
Ahora, los administradores pueden configurar un borrado selectivo de los datos de la organización como una nueva acción cuando no se cumplan las condiciones de Configuración de acceso de las Directivas de protección de aplicaciones (APP).  Mediante esta característica, los administradores podrán proteger y eliminar automáticamente datos confidenciales de la organización en las aplicaciones, en función de criterios configurados previamente.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Revocar una aplicación iOS adquirida a través de PCV <!-- 1777384 -->
Como administrador de Microsoft Intune, puede revocar todas las licencias de una determinada aplicación iOS adquirida a través del Programa de Compras por Volumen de Apple (VPP). Puede notificar a los usuarios cuando una aplicación con licencia de usuario ya no esté asignada a ellos. Revocar una licencia de aplicación no desinstalará la aplicación VPP desde el dispositivo. Para desinstalar una aplicación VPP, debe cambiar la acción de asignación a **Desinstalar**. El número de licencias reclamadas se indicará en el nodo **Aplicaciones con licencia** en la carga de trabajo **Aplicación** de Intune. Para más información relacionada con las aplicaciones iOS de PCV, vea [How to manage iOS apps purchased through a volume-purchase program with Microsoft Intune](vpp-apps-ios.md) (Administración de aplicaciones iOS adquiridas a través de un Programa de Compra de Licencias por Volumen con Microsoft Intune).

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Actualizaciones en los mensajes de no conformidad en la aplicación Portal de empresa <!-- 1832222 -->
Hemos revisado los mensajes que ven los usuarios cuando un dispositivo no es conforme. Estos mensajes conservan su significado original, pero se han actualizado con un lenguaje más descriptivo y menos jerga técnica. También se han actualizado los vínculos a la documentación y los pasos de corrección para mantenerlos actualizados.
Los textos siguientes son un ejemplo de las mejoras que verá en los mensajes:
- **Antes**: *Este dispositivo no ha contactado con el servicio de Intune en el período de tiempo especificado que requiere el administrador de TI. Para resolver este problema, abra la aplicación de Portal de empresa en el dispositivo y haga clic en el botón Comprobar cumplimiento.*
- **Después**:  *Hace tiempo que el dispositivo no se registra en la organización. Para volver a establecer una conexión, abra la aplicación de Portal de empresa en el dispositivo y pulse en Comprobar configuración del dispositivo.*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>Revocar licencias de aplicaciones iOS de PCV<!-- 1863797 -->
Como administrador, puede recuperar la licencia de una aplicación iOS de VPP asignada a un usuario o un dispositivo. Al desinstalar una aplicación iOS de PCV, también podrá recuperar la licencia de la aplicación. Antes de desinstalar la aplicación, hay que quitar el usuario o el dispositivo del grupo al que se destina la aplicación. Al quitarlos, se evita que la aplicación vuelva a instalarse. Tras completar estos pasos, puede optar por asignar la licencia de la aplicación a otro usuario o dispositivo. Para más información sobre las licencias de aplicaciones iOS de PCV, vea [Manage iOS volume-purchased apps in Microsoft Intune](vpp-apps-ios.md) (Administración de aplicaciones iOS compradas por volumen en Microsoft Intune).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Selección de las categorías de dispositivos mediante el valor de configuración Obtener acceso a trabajo o escuela <!-- 1058963 eenotready --> 
Si ha habilitado la [asignación de grupos de dispositivos](https://docs.microsoft.com/en-us/intune/device-group-mapping), ahora se pedirá a los usuarios de Windows 10 que seleccionen una categoría de dispositivo después de la inscripción a través del botón **Conectar** en **Configuración** > **Cuentas** > **Obtener acceso a trabajo o escuela**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Usar sAMAccountName como nombre de usuario de cuenta para perfiles de correo electrónico <!-- 1500307 -->
Puede usar el nombre local **sAMAccountName** como nombre de usuario de cuenta de los perfiles de correo electrónico para Android, iOS y Windows 10. También puede obtener el dominio de los atributos `domain` o `ntdomain` en Azure Active Directory (Azure AD). O si lo prefiere, podrá especificar un dominio estático personalizado.

Para usar esta característica, debe sincronizar el atributo `sAMAccountName` desde el entorno de Active Directory local con Azure AD.

Se aplica a [Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 y versiones posteriores](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Ver perfiles de configuración de dispositivos en conflicto <!-- 1556983 -->
En **Configuración del dispositivo**, se muestra una lista de los perfiles existentes. Con esta actualización, se agrega una nueva columna que proporciona información detallada sobre los perfiles que tienen un conflicto. Puede seleccionar una fila en conflicto para ver la configuración y el perfil que tiene el conflicto. 

Obtenga más información sobre cómo [administrar perfiles de configuración](device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Nuevo estado para dispositivos en la conformidad de dispositivos <!-- 2308882 -->
En **Conformidad de dispositivos** > **Directivas** > seleccione una directiva > **Información general**, se han agregado los estados nuevos siguientes:
- Correcto
- error
- Conflicto
- pendiente
- No aplicable: una imagen que también muestra el número de dispositivos de una plataforma diferente. Por ejemplo, si está buscando un perfil de iOS, el nuevo icono muestra el número de dispositivos que no son de iOS que también están asignados a este perfil. Vea [Directivas de cumplimiento de dispositivos](compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Conformidad de dispositivos compatible con soluciones antivirus de terceros <!-- 2325484 -->
Cuando cree una directiva de cumplimiento de dispositivos (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Plataforma: Windows 10 y versiones posteriores** > **Configuración** > **Seguridad del sistema**), existen nuevas opciones disponibles de **[Seguridad del dispositivo](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)**: 
- **Antivirus**: cuando se establece en **Requerir**, puede comprobar la conformidad a través de soluciones antivirus registradas con Centro de seguridad de Windows, como Symantec y Windows Defender. 
- **Antispyware**: cuando se establece en **Requerir**, puede comprobar la conformidad a través de soluciones antispyware registradas con Windows Security Center, como Symantec y Windows Defender. 

Se aplica a: Windows 10 y versiones posteriores 

### <a name="device-enrollment"></a>Inscripción de dispositivos

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Dispositivos sin columna de perfiles en la lista de tokens del programa de inscripción <!-- 1853904 -->
En la lista de tokens del programa de inscripción hay una nueva columna que muestra el número de dispositivos sin un perfil asignado. Esto ayuda a los administradores a asignar perfiles a estos dispositivos antes de entregarlos a los usuarios. Para ver la nueva columna, vaya a **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción**.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Cambio de nombre en Google para Android for Work y Play for Work <!--842873 -->
Intune ha actualizado el término "Android for Work" para reflejar los cambios de personalización de marca de Google. Ya no se usan los términos "Android for Work" ni "Play for Work". Se usa otra terminología en función del contexto:
- "Android Enterprise" hace referencia a la pila de administración general de Android moderna.
- "Perfil de trabajo" o "Propietario de perfil" hacen referencia a dispositivos BYOD administrados con perfiles de trabajo.
- "Google Play administrada" hace referencia a la tienda de aplicaciones de Google.

#### <a name="rules-for-removing-devices----1609459---"></a>Reglas para quitar dispositivos <!-- 1609459 -->
Hay disponibles nuevas reglas que permiten quitar automáticamente dispositivos que no se hayan protegido durante un número de días que establezca. Para ver la nueva regla, vaya al panel **Intune**, seleccione **Dispositivos** y, luego, **Reglas de limpieza de dispositivos**.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Compatibilidad con dispositivos Android de un solo uso y propiedad corporativa <!-- 1630973 -->

Ahora, Intune admite dispositivos Android de estilo quiosco, que estén bloqueados y con una elevada administración. De este modo, los administradores pueden bloquear aún más el uso de un dispositivo para restringir su uso a una sola aplicación o un pequeño conjunto de aplicaciones, impidiendo así que los usuarios habiliten otras aplicaciones o realicen otras acciones en el dispositivo. Para configurar el quiosco de Android, vaya a Intune > **Inscripción de dispositivos** > **Inscripción de Android** > **Inscripciones de dispositivos de tareas y quiosco**. Para obtener más información, vea [Set up enrollment of Android enterprise kiosk devices](android-kiosk-enroll.md) (Configurar la inscripción de dispositivos de quiosco de Android Enterprise).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Revisión por fila de los identificadores de dispositivos corporativos duplicados cargados <!-- 2203794-->
Ahora, al cargar identificadores corporativos, Intune facilita una lista de cualquier dispositivo duplicado y ofrece la posibilidad de reemplazar o conservar la información existente. El informe se mostrará si hay duplicados después de elegir **Inscripción de dispositivos** > **Identificadores de dispositivos corporativos** > **Agregar identificadores**. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Agregar manualmente identificadores de dispositivos corporativos <!-- 2203803 -->
Ahora puede agregar manualmente identificadores de dispositivos corporativos. Elija **Inscripción de dispositivos** > **Identificadores de dispositivos corporativos** > **Agregar**. 

## <a name="week-of-june-25-2018"></a>Semana del 25 de junio de 2018

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo, nuevo colaborador de Mobile Threat Defense <!-- 1169249 -->

Puede controlar el acceso desde dispositivos móviles a recursos corporativos en función de la evaluación de riesgos efectuada por Pradeo, una solución de Mobile Threat Defense integrada con Microsoft Intune.

## <a name="week-of-june-18-2018"></a>Semana del 18 de junio de 2018

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Compatibilidad móvil de Edge para directivas de Intune App Protection <!-- 1817882 -->

El navegador Microsoft Edge para dispositivos móviles ahora admite las directivas de protección de aplicaciones definidas en Intune.

## <a name="week-of-june-11-2018"></a>Semana del 11 de junio de 2018

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Uso del modo FIPS con el conector de certificado NDES <!-- 1333688 -->
Al instalar el conector de certificado NDES en un equipo con el modo Estándar federal de procesamiento de información (FIPS) habilitado, la emisión y revocación de certificados no funciona según lo previsto. Con esta actualización, con el conector de certificado NDES se incluye la compatibilidad con FIPS. 

Esta actualización también incluye:

- El conector de certificado NDES requiere .NET 4.5 Framework, que se incluye automáticamente con Windows Server 2016 y Windows Server 2012 R2. Anteriormente, .NET 3.5 Framework era la versión mínima requerida.
- Con el conector de certificado NDES se incluye la compatibilidad con TLS 1.2. Por tanto, si el servidor con el conector de certificado NDES instalado es compatible con TLS 1.2, entonces se usará TLS 1.2. Si el servidor no admite TLS 1.2, entonces se usará TLS 1.1. Actualmente, se usa TLS 1.1 para la autenticación entre los dispositivos y el servidor.

Para obtener más información, vea [Configuración y uso de certificados SCEP](certificates-scep-configure.md) y [Configuración y uso de certificados PKCS](certficates-pfx-configure.md).

## <a name="week-of-june-4-2018"></a>Semana del 4 de junio de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Recuperación del identificador de modelo de usuario de la aplicación (AUMID) asociado para aplicaciones de Microsoft Store para Empresas en pantalla completa <!-- 1560077 ! -->
Intune ya puede recuperar los identificadores de modelo de usuario de la aplicación (AUMID) para aplicaciones de Microsoft Store para Empresas (WSfB) con el fin de mejorar la configuración del perfil de quiosco.

Para más información sobre las aplicaciones de Microsoft Store para Empresas, consulte el artículo sobre la [administración de aplicaciones de Microsoft Store para Empresas](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Nueva página de personalización de marca del Portal de empresa <!-- 1916370 -->
La página de personalización de marca del Portal de empresa tiene un nuevo diseño, mensajes e información sobre herramientas.


### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Compatibilidad con perfiles de VPN de Palo Alto Networks GlobalProtect <!-- 1333680 eeready ! -->
Con esta actualización, puede elegir Palo Alto Networks GlobalProtect como un tipo de conexión VPN para perfiles de VPN en Intune (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Tipo de perfil** > **VPN**). En esta versión, se admiten las siguientes plataformas: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Adiciones a la configuración de opciones de seguridad del dispositivo local <!-- 1403702 -->
Ya puede configurar opciones adicionales de seguridad del dispositivo local para dispositivos con Windows 10. Las opciones adicionales están disponibles en las áreas Cliente de redes de Microsoft, Servidor de red Microsoft, Acceso y seguridad de red e Inicio de sesión interactivo. Encuentre estos valores en la categoría de Endpoint Protection cuando cree una directiva de configuración de dispositivo de Windows 10.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Habilitación de la pantalla completa en dispositivos Windows 10 <!-- 1560072 ! -->
En los dispositivos Windows 10, puede crear un perfil de configuración y habilitar la pantalla completa (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Windows 10** > **Restricciones de dispositivos** > **Quiosco**). En esta actualización, la configuración **Quiosco (versión preliminar)** cambia de nombre a **Quiosco (obsoleto)**. Ya no se recomienda usar **Quiosco (obsoleto)**, pero seguirá funcionando hasta la actualización de julio. El nuevo tipo de perfil **Quiosco** reemplaza a **Quiosco (obsoleto)** (**Crear perfil** > **Windows 10** > **Quiosco (versión preliminar)**), que contendrá los valores para configurar Quioscos en Windows 10 RS4 y versiones posteriores.

Se aplica a Windows 10 y versiones posteriores.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Vuelve el gráfico de usuario del perfil del dispositivo <!-- 2160133 -->
Si bien mejoraba el valor numérico que aparece en el gráfico del perfil del dispositivo (**Configuración de dispositivos** > **Perfiles** > seleccione un perfil existente > **Información general**), el gráfico de usuario se quitó de manera temporal.

Con esta actualización, dicho gráfico vuelve y aparece en Azure Portal.

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>Compatibilidad con la inscripción de Windows Autopilot sin autenticación de usuario <!-- 1165118 wnready -->
Intune admite la inscripción de Windows Autopilot sin autenticación de usuario. Se trata de una nueva opción en el perfil de implementación de Windows Autopilot "Modo de implementación Autopilot" establecido en "Self-Deploying" (Autoimplementable).  El dispositivo debe ejecutar Windows 10 Insider Preview, compilación 17672 o posterior, y poseer un chip de TPM 2.0 para completar correctamente este tipo de inscripción. Puesto que no se requiere ninguna autenticación de usuario, solo puede asignar esta opción a dispositivos sobre los que tenga control físico.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766-eeready---"></a>Nueva configuración de idioma y región al realizar la configuración rápida de Autopilot <!-- 1821766 eeready -->
Hay disponible una nueva configuración para establecer el idioma y la región de los perfiles de Autopilot durante la configuración rápida. Para ver la nueva configuración, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Implementación perfiles** > **Crear perfil** > **Modo de implementación** = **Self-deploying (Autoimplementable)** > **Valores predeterminados configurados**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nuevo valor para configurar el teclado del dispositivo <!-- 1821768 -->
Habrá disponible un valor nuevo para configurar el teclado de los perfiles de Autopilot durante la configuración rápida. Para ver la nueva configuración, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Implementación perfiles** > **Crear perfil** > **Modo de implementación** = **Self-deploying (Autoimplementable)** > **Valores predeterminados configurados**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Los perfiles AutoPilot se migran a un destinatario de grupo <!-- 1877935 -->
Se pueden asignar perfiles de implementación de AutoPilot a grupos de Azure AD que contengan dispositivos AutoPilot.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="set-compliance-by-device-location----851881----"></a>Establecimiento del cumplimiento por ubicación del dispositivo <!-- 851881 ! -->
En algunas situaciones, es posible que desee restringir el acceso a los recursos corporativos a una ubicación específica, definida por una conexión de red. Ya puede crear una directiva de cumplimiento (**Cumplimiento de dispositivos** > **Ubicaciones**) en función de la dirección IP del dispositivo. Si el dispositivo sale del intervalo IP, no podrá acceder a los recursos corporativos.

Se aplica a: dispositivos Android 6.0 y versiones posteriores, con la aplicación Portal de empresa actualizada

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Evitar aplicaciones y experiencias de consumidor en dispositivos Windows 10 Enterprise RS4 Autopilot<!-- 1621980 -->
Puede evitar la instalación de aplicaciones y experiencias de consumidor en los dispositivos Windows 10 Enterprise RS4 Autopilot. Para ver esta característica, vaya a **Intune** > **Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Plataforma** = **Windows 10 o versiones posteriores** > **Tipo de perfil** = **Restricciones de dispositivo** > **Configurar** > **Windows Spotlight** > **Características de consumidor**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948-eeready---"></a>Desinstalar las últimas actualizaciones de software de Windows 10 <!-- 1732948 eeready -->
En caso de que detecte un problema importante en las máquinas con Windows 10, puede optar por desinstalar (revertir) la última actualización de características o la última actualización de calidad. La desinstalación de una actualización de característica o de calidad solo está disponible para el canal de servicio en el que se encuentra el dispositivo. La desinstalación desencadenará una directiva para restaurar la actualización anterior en las máquinas con Windows 10. Para las actualizaciones de características concretamente, puede limitar el tiempo de 2 a 60 días durante el cual se puede aplicar una desinstalación de la versión más reciente. Para configurar las opciones de desinstalación de actualización de software, seleccione **Actualizaciones de software** en la hoja **Microsoft Intune** en el portal de Azure. Después, seleccione **Anillos de actualización de Windows 10** en la hoja **Actualizaciones de software**. Elija después la opción **Desinstalar** en la sección **Información general**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Buscar IMEI y número de serie en todos los dispositivos <!-- 1793685 -->
Ya puede buscar IMEI y los números de serie en la hoja Todos los dispositivos (correo electrónico, UPN, nombre de dispositivo y nombre de la administración siguen estando disponibles). En Intune, elija **Dispositivos** > **Todos los dispositivos** y escriba la búsqueda en el cuadro de búsqueda.

#### <a name="management-name-field-will-be-editable----1875989---"></a>El campo de nombre de administración se podrá editar <!-- 1875989 -->
Ya puede editar el campo de nombre de administración en la hoja **Propiedades** de un dispositivo. Para editar este campo, elija **Dispositivos** > **Todos los dispositivos** > elija el dispositivo > **Propiedades**. Puede usar el campo de nombre de administración para identificar un dispositivo de manera única.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Nuevo filtro Todos los dispositivos: categoría de dispositivo <!-- 1878520 -->
Ya puede filtrar la lista **Todos los dispositivos** por categoría de dispositivo. Para ello, elija **Dispositivos** > **Todos los dispositivos** > **Filtro** > **Categoría de dispositivo**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Use TeamViewer para compartir la pantalla de dispositivos iOS y MacOS <!-- 1985547 -->
Los administradores podrán conectarse a [TeamViewer](device-profile-android-teamviewer.md) e iniciar una sesión de uso compartido de pantalla con dispositivos iOS y macOS. Los usuarios de iPhone, iPad y macOS pueden compartir sus pantallas en vivo con cualquier otro dispositivo móvil o de escritorio. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Compatibilidad con múltiples instancias de Exchange Connector <!-- 2070451 -->
Ya no estará limitado a una instancia de Microsoft Intune Exchange Connector por inquilino. Intune admite varias instancias de Exchange Connector para que pueda configurar el acceso condicional de Intune con varias organizaciones de Exchange local.

Con un conector de Exchange local de Intune, se puede controlar el acceso de los dispositivos a los buzones de Exchange locales en función de si un dispositivo está inscrito en Intune y cumple con las directivas de cumplimiento de dispositivos de Intune. Para configurar un conector, descargue el conector de Exchange local de Intune desde Azure Portal e instálelo en un servidor en la organización de Exchange. En el panel de Microsoft Intune, elija **Acceso local** y, después, en **Instalación**, elija **Conector de Exchange ActiveSync**. Descargue el conector de Exchange local e instálelo en un servidor en la organización de Exchange. Ahora que ya no está limitado a un conector de Exchange por inquilino, si tiene otras organizaciones de Exchange, puede seguir el mismo proceso para descargar e instalar un conector para cada organización de Exchange adicional.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Nuevos detalles de hardware de dispositivo: CCID <!-- 2156657 -->
La información de dispositivo de interfaz de tarjeta de chip (CCID) ya se incluye para cada dispositivo. Para verla, elija **Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Hardware**> compruebe en **Detalles de red**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Asignación de todos los usuarios y dispositivos como grupos de ámbito <!-- 2196803 -->
Podrá asignar todos los usuarios, todos los dispositivos y todos los usuarios y dispositivos en los grupos de ámbito. Para ello, elija **Roles de Intune** > **Todos los roles** > **Policy and profile manager (Administrador de directivas y perfiles)** > **Asignaciones**  > elija una asignación > **Ámbito (grupos)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>La información de UDID ahora se incluye para dispositivos iOS y macOS <!-- 2219806 wnready-->
Para ver el identificador único de dispositivo (UDID) para dispositivos iOS y macOS, vaya a **Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Hardware**. UDID solo está disponible para dispositivos corporativos, tal y como se configura en **Dispositivos** > **Todos los dispositivos** > dispositivo > **Propiedades** > **Propiedad del dispositivo**.

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Solución de problemas mejorada para la instalación de aplicaciones <!-- 928990 -->
En algunas ocasiones, las instalaciones de aplicaciones en los dispositivos administrados por MDM de Microsoft Intune pueden presentar errores. Cuando esto ocurre, puede ser complicado entender el motivo del error o cómo solucionarlo. Incluimos una Versión preliminar pública de las características de solución de problemas de las aplicaciones. Verá un nodo nuevo bajo cada dispositivo individual denominado **Aplicaciones administradas**. En él aparecen las aplicaciones que se han entregado a través de MDM de Intune. Dentro del nodo, verá una lista de los estados de instalación de las aplicaciones. Si selecciona una aplicación individual, aparecerá la vista de solución de problemas de esa aplicación específica. En la vista de solución de problemas, verá el ciclo de vida completo de la aplicación, como cuándo se creó y modificó la aplicación, el momento en que se estableció su destino y cuándo se entregó a un dispositivo. Además, si la instalación de la aplicación no se realizó correctamente, verá el código de error y un mensaje útil sobre la causa del mismo. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Directivas de protección de aplicaciones de Intune y Microsoft Edge <!-- 1818968 -->
El explorador Microsoft Edge para dispositivos móviles (iOS y Android) ahora admite las directivas de protección de aplicaciones Microsoft Intune. Intune protegerá a los usuarios de dispositivos iOS y Android que inicien sesión con sus cuentas corporativas de Azure AD en la aplicación Edge. En dispositivos iOS, la directiva **Require managed browser for web content** (Requerir explorador administrado para contenido web) permitirá a los usuarios abrir vínculos en Edge cuando esté administrado.

## <a name="week-of-may-14-2018"></a>Semana del 14 de mayo de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Exigencia de instalación de perfiles de directivas, aplicaciones, certificados y red <!-- 1553555 -->

Los administradores pueden evitar que los usuarios finales accedan al escritorio de Windows 10 RS4 hasta que Intune instale los perfiles de red y certificado, las aplicaciones y las directivas durante el aprovisionamiento de dispositivos AutoPilot. Para obtener más información, consulte [Configurar una página de estado de inscripción](windows-enrollment-status.md).

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Configurar las directivas de protección de aplicaciones <!-- 2144597 Part 2 -->

En Azure Portal, en lugar de dirigirse a la hoja del servicio Intune App Protection, solo tiene que ir a Intune. Ahora hay una única ubicación para las directivas de protección de aplicaciones en Intune. Tenga en cuenta que todas las directivas de protección de aplicaciones se encuentran en la hoja **Aplicación móvil** de Intune, en **Directivas de protección de aplicaciones**. Esta integración ayuda a simplificar la administración en la nube. Recuerde que todas las directivas de protección de aplicaciones ya están en Intune y que puede modificar cualquiera de las directivas configuradas anteriormente. Las directivas de protección de aplicaciones (APP) y acceso condicional (CA) de Intune se encuentran ahora en **Acceso condicional**, que se encuentra en la sección **Administrar** de la hoja **Microsoft Intune** o en la sección **Seguridad** de la hoja **Azure Active Directory**. Para obtener más información sobre cómo modificar directivas de acceso condicional, vea [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Para obtener más información, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>Semana del 7 de mayo de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Compatibilidad con Samsung Knox Mobile Enrollment <!--1112863-->

Al usar Intune con Samsung Knox Mobile Enrollment (KME), puede inscribir un gran número de dispositivos Android propiedad de la empresa. Los usuarios en redes Wi-Fi o de telefonía móvil se pueden inscribir con unas pocas pulsaciones al encender sus dispositivos por primera vez. Con la aplicación de implementación Knox, los dispositivos se pueden inscribir mediante Bluetooth o NFC. Para más información, vea [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Inscripción automática de dispositivos Android mediante Samsung Knox Mobile Enrollment).

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Solicitar ayuda en el Portal de empresa para Windows 10 <!-- 1874137 -->

El Portal de empresa para Windows 10 ahora enviará registros de aplicaciones directamente a Microsoft cuando el usuario inicie el flujo de trabajo para obtener ayuda con un problema. Esto permitirá que sea más fácil solucionar los problemas que se envían a Microsoft.

## <a name="week-of-april-23-2018"></a>Semana del 23 de abril de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Compatibilidad de código de acceso con el PIN de MAM en Android<!-- 1438086 -->

Los administradores de Intune pueden establecer un requisito de inicio de aplicación para exigir un código de acceso en lugar de un PIN numérico de MAM. Si se configura, se le pide al usuario que establezca y use un código de acceso cuando se le solicite antes de obtener acceso a aplicaciones habilitadas para MAM. Un código de acceso se define como un PIN numérico con al menos un carácter especial o un carácter alfabético en mayúsculas/minúsculas. Intune admite un código de acceso de forma similar al PIN numérico existente... puede establecer una longitud mínima y permite la repetición de caracteres y secuencias en la consola de administración. Esta característica requiere la versión más reciente del Portal de empresa en Android. Esta característica ya está disponible para iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Compatibilidad con aplicaciones de línea de negocio (LOB) para macOS <!-- 1473977 -->
Microsoft Intune proporciona la capacidad de instalar aplicaciones LOB de macOS desde Azure Portal. Se puede agregar una aplicación LOB de macOS a Intune una vez procesada por la herramienta disponible en GitHub. En Azure Portal, seleccione **Aplicaciones cliente** en la hoja **Intune**. En la hoja **Aplicaciones cliente**, elija **Aplicaciones** > **Agregar**. En la hoja **Agregar aplicación**, seleccione **Aplicación de línea de negocio**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Asignación de aplicaciones a los grupos integrados Todos los usuarios y Todos los dispositivos de Android for Work (AFW) <!-- 1813073 -->
Puede aprovechar los grupos integrados **Todos los usuarios** y **Todos los dispositivos** para la asignación de aplicaciones de AFW. Para obtener más información, vea [Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune volverá a instalar las aplicaciones necesarias desinstaladas por los usuarios <!-- 1947010 -->
Si un usuario final desinstala una aplicación requerida, Intune la reinstala de forma automática antes de que transcurran 24 horas en lugar de esperar al ciclo de reevaluación de siete días.

### <a name="device-configuration"></a>Configuración de los dispositivos

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>El gráfico de perfiles de dispositivos y la lista de estado muestran todos los dispositivos de un grupo <!-- 1449153 eeready -->
Al configurar un perfil de dispositivo (**Configuración del dispositivo** > **Perfiles**), elija el perfil del dispositivo, por ejemplo, iOS. Este perfil se asigna a un grupo que incluye los dispositivos iOS y los dispositivos que no son iOS. El recuento del gráfico muestra que el perfil se aplica a dispositivos iOS *y* no iOS (**Configuración del dispositivo** > **Perfiles** > seleccionar un perfil existente > **Información general**). Cuando se selecciona el gráfico en la pestaña **Información general**, el **Estado del dispositivo** enumera todos los dispositivos del grupo, en lugar de solo los dispositivos iOS. 

Con esta actualización, el gráfico (**Configuración del dispositivo** > **Perfiles** > seleccionar un perfil existente > **Información general**) solo muestra el recuento del perfil de dispositivo determinado. Por ejemplo, si el perfil de dispositivo de configuración se aplica a dispositivos iOS, el gráfico muestra solo el número de dispositivos iOS. Al seleccionar el gráfico y abrir **Estado del dispositivo**, solo se muestran los dispositivos iOS.

Mientras se realiza esta actualización, se quita temporalmente el gráfico de usuario. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>VPN de Always On para Windows 10 <!--1333666 -->

Actualmente, [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) puede usarse en dispositivos Windows 10 mediante un perfil de red privada virtual (VPN) personalizado creado con OMA-URI.

Con esta actualización, los administradores pueden habilitar Always On para perfiles de VPN de Windows 10 directamente en Intune en Azure Portal. Los perfiles VPN de Always On se conectarán automáticamente cuando:

- Los usuarios inicien sesión en sus dispositivos
- La red del dispositivo cambie
- La pantalla del dispositivo se vuelva a activar después de haberse desactivado

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nueva configuración de impresora para perfiles de educación <!-- 1308900 -->

Para los perfiles de educación, hay nueva configuración disponible en la categoría **Impresoras**: **Impresoras**, **Impresora predeterminada**, **Agregar nuevas impresoras**.

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>Mostrar el identificador del autor de la llamada en el perfil personal - Android for Work <!--1098984 -->
Al usar un perfil personal en un dispositivo, es posible que los usuarios finales no vean los detalles del identificador del autor de la llamada de un contacto de trabajo. 

Con esta actualización, hay una nueva opción en **Android for Work** > **Restricciones de dispositivos** > **Configuración del perfil de trabajo**:
- Mostrar el identificador de llamada de contacto profesional en el perfil personal

Cuando se habilita (sin configurar), se muestran los detalles del autor de la llamada del contacto en el perfil personal. Cuando se bloquea, no se muestra el número del autor de la llamada del contacto en el perfil personal. 

Se aplica a: dispositivos de perfil de trabajo Android con la versión de SO Android 6.0 y versiones más recientes

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nueva configuración de Credential Guard de Windows Defender agregada a la configuración de Endpoint Protection <!--1102252 --><!--from 1802 and 1804-->

Con esta actualización, [Credential Guard de Windows Defender](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configuración de dispositivos** > **Perfiles** > **Endpoint Protection**) incluye la siguiente configuración: 

- **Credential Guard de Windows Defender**: activa Credential Guard con seguridad basada en virtualización. Habilitar esta característica ayuda a proteger las credenciales en el siguiente reinicio cuando las opciones **///Platform Security Level with Secure Boot** (Nivel de seguridad de plataforma con arranque seguro) y **///Virtualization Based Security** (Seguridad basada en virtualización) are están ambas habilitadas. Las opciones son:
  - **Deshabilitado**: si Credential Guard se activó anteriormente con la opción **Habilitar sin bloqueo**", entonces Credential Guard se desactiva de forma remota.

  - **Habilitar con bloqueo UEFI**: garantiza que Credential Guard no se puede deshabilitar mediante una clave de Registro o por medio de directiva de grupo. Para deshabilitar Credential Guard después de usar esta opción, debe establecer la directiva de grupo en "Deshabilitado". A continuación, quite la funcionalidad de seguridad de cada equipo, con un usuario físicamente presente. Estos pasos borrar la configuración almacenada en UEFI. Mientras se conserve la configuración de UEFI, Credential Guard estará habilitado.

  - **habilitar sin bloqueo**: permite deshabilitar Credential Guard de forma remota mediante la directiva de grupo. Los dispositivos que usen esta configuración deben ejecutar al menos Windows 10 (versión 1511).

Las siguientes tecnologías dependientes se habilitan automáticamente al configurar Credential Guard: 

  - **Enable Virtualization-based Security (VBS)** (Habilitar la seguridad basada en la virtualización [VBS]): activa la seguridad basada en la virtualización (VBS) en el siguiente reinicio. La seguridad basada en la virtualización emplea el hipervisor de Windows para proporcionar compatibilidad con servicios de seguridad, y requiere arranque seguro.
  - **Secure Boot with Direct Memory Access (DMA)**: activa VBS con arranque seguro y acceso directo a memoria. La protección de DMA requiere compatibilidad con el hardware y solo se habilita en los dispositivos configurados correctamente. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Usar un nombre de firmante personalizado en certificado SCEP <!-- 2064190 -->
Puede usar el nombre común **OnPremisesSamAccountName** de un sujeto personalizado en un perfil de certificado SCEP. Por ejemplo, puede usar `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Bloqueo de cámara y capturas de pantalla en Android for Work <!-- 1098977 eeready-->
Hay dos nuevas propiedades disponibles para bloquear al configurar restricciones de dispositivo para dispositivos Android: 
- Cámara: bloquea el acceso a todas las cámaras en el dispositivo
- Captura de pantalla: bloquea la captura de pantalla y además evita que el contenido se muestre en los dispositivos de pantalla que no tengan una salida de vídeo segura

Se aplica a Android for Work.


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nuevos pasos de inscripción para los usuarios en dispositivos con macOS High Sierra 10.13.2+ <!--1734567 -->
macOS high Sierra 10.13.2 presentó el concepto de inscripción de inscripción de MDM "aprobada por el usuario". Las inscripciones aprobadas permiten a Intune administrar algunas configuraciones dependientes de la seguridad. Para obtener más información, vea la documentación de soporte técnico de Apple aquí: https://support.apple.com/HT208019.

Los dispositivos inscritos mediante el Portal de empresa de macOS se consideran "No aprobados por el usuario", a menos que el usuario final abra las preferencias del sistema y los apruebe de forma manual. Así, el Portal de empresa de macOS ahora insta a los usuarios de macOS 10.13.2 y versiones posteriores a aprobar manualmente su inscripción al final del proceso de inscripción. La consola de administración de Intune indicará si un dispositivo inscrito está aprobado por el usuario.



### <a name="device-management"></a>Administración de dispositivos

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>Protección contra amenazas avanzada (ATP) e Intune están totalmente integrados <!-- EEready 1629303 -->

[Protección contra amenazas avanzada (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) muestra el nivel de riesgo de los dispositivos Windows 10. En el Centro de seguridad de Windows Defender (portal de ATP), puede crear una conexión a Microsoft Intune. Una vez creada, se usa una directiva de cumplimiento de Intune para determinar un nivel de amenaza aceptable. Si se supera el nivel de amenaza, una directiva de acceso condicional de Azure Active Directory (AD) puede bloquear el acceso a diferentes aplicaciones dentro de su organización.

Esta característica permite que ATP examine archivos, detecte amenazas y notifique cualquier riesgo en los dispositivos Windows 10.

Consulte [Habilitación de ATP con acceso condicional en Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Compatibilidad con dispositivos sin usuario <!-- 1637553 -->
Intune ofrece la posibilidad de evaluar el cumplimiento en dispositivos sin usuario, como Microsoft Surface Hub. La directiva de cumplimiento puede tener como destino dispositivos concretos. Así, es posible determinar el cumplimiento (y no cumplimiento) de dispositivos sin un usuario asociado.

#### <a name="delete-autopilot-devices----1713650---"></a>Eliminar dispositivos Autopilot <!-- 1713650 -->
Los administradores de Intune pueden [eliminar dispositivos Autopilot](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Experiencia de eliminación de dispositivos mejorada <!--1832333 -->
Ya no se le pide que quite los datos de la empresa o que restablezca el dispositivo a los valores de fábrica para [eliminar un dispositivo de Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Para ver la nueva experiencia, inicie sesión en Intune y seleccione **Dispositivos** > **Todos los dispositivos** > el nombre del dispositivo > **Eliminar**.

Si todavía quiere confirmar el borrado o eliminación, puede usar la ruta de ciclo de vida de dispositivo estándar al usar **Eliminar datos de la compañía** y **Restablecimiento de fábrica** antes de **Eliminar**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Reproducir sonidos en iOS en modo Perdido <!-- 1947769 -->
Cuando los dispositivos iOS supervisados están en el [modo perdido](device-lost-mode.md) de administración de dispositivos móviles (MDM), puede [reproducir un sonido](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Dispositivos** > **Todos los dispositivos** > seleccionar un dispositivo iOS > **Información general** > **Más**). El sonido sigue reproduciéndose hasta que el dispositivo se quita del modo Perdido o un usuario deshabilita el sonido en el dispositivo. Se aplica a dispositivos iOS 9.3 y versiones más recientes.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Bloquear o permitir resultados web en búsquedas realizadas en un dispositivo de Intune <!--1972804-->

Ahora, los administradores pueden bloquear los resultados web en las búsquedas realizadas en un dispositivo.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Mensajes de error mejorados para errores de carga del certificado push MDM de Apple <!-- 2172331 -->

El mensaje de error explica que se debe usar el mismo identificador de Apple al renovar un certificado MDM existente.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Probar el Portal de empresa para macOS en máquinas virtuales <!-- 2216679 -->

Se han publicado instrucciones para ayudar a los administradores de TI a probar la aplicación de Portal de empresa para macOS en máquinas virtuales en Parallels Desktop y VMware Fusion. Encuentre más información en [Inscribir máquinas virtuales macOS para realizar pruebas](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Interfaz de usuario

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Mejora de iconos de dispositivos en el Portal de empresa de Windows 10 <!--2213364 -->

Se han actualizado los iconos para hacerlos más accesibles para los usuarios con deficiencia visual y para que funcionen mejor con las herramientas de lectura de pantalla.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Enviar informes de diagnóstico en la aplicación Portal de empresa para macOS <!-- 2216677 -->
La aplicación Portal de empresa para dispositivos macOS se actualizó para mejorar la forma en que los usuarios notifican errores relacionados con Intune. Desde la aplicación Portal de empresa, los empleados pueden:

- Cargar informes de diagnóstico directamente para el equipo de desarrollo de Microsoft.
- Enviar por correo electrónico un Id. de incidente al equipo de soporte técnico de TI de la empresa.

Para más información, consulte [Envío de errores de macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune se adapta al sistema de diseño fluido de la aplicación Portal de empresa de Windows 10 <!-- 1195010 WNready -->
La aplicación Portal de empresa de Windows 10 se ha actualizado con la [vista de navegación del sistema de diseño fluido](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics). En la parte lateral de la aplicación, verá una lista estática vertical de todas las páginas de nivel superior. Haga clic en cualquier vínculo para ver y cambiar entre páginas rápidamente. Esta es la primera de varias actualizaciones que verá como parte de nuestros esfuerzos para crear una experiencia más adaptable, empática y familiar en Intune. Para ver el aspecto actualizado, vaya a [Novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Semana del 16 de abril de 2018

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>Usar el cliente de Cisco AnyConnect para iOS <!-- EEready 1333708 -->

Cuando se crea un nuevo perfil de VPN para iOS, ahora hay dos opciones: **Cisco AnyConnect** y **Cisco Legacy AnyConnect**. Los perfiles de Cisco AnyConnect admiten las versiones 4.0.7x y más recientes. Los perfiles de VPN existentes de Cisco AnyConnect para iOS se etiquetan como **Cisco Legacy AnyConnect**, y siguen funcionando con Cisco AnyConnect 4.0.5x y versiones posteriores, como lo hacen en la actualidad.

> [!NOTE]
> Este cambio sólo se aplica a iOS. Sigue habiendo una única opción de Cisco AnyConnect para las plataformas Android, Android for Work y macOS.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Ahora, los dispositivos macOS inscritos en Jamf se pueden registrar en Intune <!-- 2370684 -->

Las versiones 1.3 y 1.4 del portal de empresa de macOS no registraban correctamente los dispositivos Jamf en Intune. La versión 1.4.2 del portal de macOS corrige este problema.


## <a name="week-of-april-9-2018"></a>Semana del 9 de abril de 2018  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Experiencia de ayuda actualizada en la aplicación Portal de empresa para Android <!-- 1631531 -->

Se ha actualizado la experiencia de ayuda en la aplicación Portal de empresa para Android de acuerdo con los procedimientos recomendados para la plataforma Android. Ahora, cuando los usuarios detectan un problema en la aplicación, pueden pulsar en **Menú** > **Ayuda** y:
- Cargar registros de diagnóstico en Microsoft.
- Enviar un mensaje de correo electrónico que describe el problema y un Id. de incidente a un miembro del equipo de soporte técnico de la empresa.  

Para ver la experiencia de ayuda actualizada, vaya a [Send logs using email](/intune-user-help/send-logs-to-your-it-admin-by-email-android) (Enviar registros por correo electrónico) y [Send errors to Microsoft](/intune-user-help/send-logs-to-microsoft-android) (Enviar errores a Microsoft).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nuevo gráfico de tendencias sobre errores de inscripción y tabla de motivos de error <!-- 1471783 -->

En la página de información general de inscripción, puede ver la tendencia de los errores de inscripción y los cinco motivos de error principales. Al hacer clic en el gráfico o la tabla, puede explorar los detalles para obtener consejos de resolución de problemas y sugerencias de corrección.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Actualización de la ubicación en la que se configuran las directivas de protección de aplicaciones <!-- 2144597 -->

En Azure Portal, dentro del servicio Microsoft Intune, se le va a redirigir de forma temporal desde la hoja del servicio **Intune App Protection** a la hoja **Aplicación móvil**. Tenga en cuenta que todas las directivas de protección de aplicaciones ya se encuentran en la hoja **Aplicación móvil** de Intune, en Configuración de aplicaciones. En lugar de ir a Intune App Protection, simplemente irá a Intune. En abril de 2018, se suspenderá el redireccionamiento y se quitará por completo la hoja del servicio **Intune App Protection**, para que haya una sola ubicación para las directivas de protección de aplicaciones en Intune. 

**¿Cómo me afecta esto a mí?**
Este cambio afectará tanto a los clientes de Intune independientes como a los clientes híbridos (Intune con Configuration Manager). Esta integración le ayudará a simplificar la administración en la nube.

**¿Qué he de hacer para prepararme para este cambio?**
Etiquete **Intune** como favorito en lugar de la hoja del servicio **Intune App Protection** y familiarícese con el flujo de trabajo de directivas de protección de aplicaciones de la hoja **Aplicación móvil** de Intune. Se proporciona el redireccionamiento durante un breve período de tiempo y, después, se elimina la hoja **Intune App Protection**. Recuerde que todas las directivas de protección de aplicaciones ya están en Intune y que puede modificar las directivas de acceso condicional. Para obtener más información sobre cómo modificar directivas de acceso condicional, vea [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Para obtener más información, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Semana del 2 de abril de 2018

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Actualización de la experiencia del usuario en la aplicación del Portal de empresa para iOS <!--1412866 -->
Se ha lanzado una actualización importante de la experiencia de usuario para la aplicación Portal de empresa para iOS. La actualización incorpora un rediseño visual completo con una apariencia modernizada. Se ha mantenido la funcionalidad de la aplicación, pero se han mejorado la facilidad de uso y la accesibilidad.  

También verá:
- Compatibilidad con iPhone X.
- Inicio de la aplicación y carga de respuestas más rápidos, para ahorrar tiempo a los usuarios.
- Barras de progreso adicionales para proporcionar a los usuarios la información de estado más reciente.
- Mejoras en la forma en que los usuarios cargan registros, de modo que, si hay algún problema, resulte más fácil informar.  

Para ver el aspecto actualizado, vaya a [Novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Protección de los datos locales de Exchange mediante APP y CA de Intune <!-- 1056954 -->
Ahora puede usar directivas de protección de aplicaciones (APP) y acceso condicional (CA) de Intune para proteger el acceso a datos locales de Exchange con Outlook Mobile. Para agregar o modificar una directiva de protección de aplicaciones en Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones cliente** > **Directivas de protección de aplicaciones**. Antes de usar esta característica, asegúrese de cumplir los [requisitos de Outlook para iOS y Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="week-of-march-26-2018"></a>Semana del 26 de marzo de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Alertas para aplicaciones de línea de negocio (LOB) iOS a punto de expirar para Microsoft Intune <!-- 748789 -->

En Azure Portal, Intune le avisa de las aplicaciones de línea de negocio iOS que están a punto de expirar. Al cargar una nueva versión de la aplicación de línea de negocio iOS, Intune quita la notificación de expiración de la lista de aplicaciones. Esta notificación de expiración solo está activa para las aplicaciones de línea de negocio iOS recién cargadas. 30 días antes de que expire el perfil de aprovisionamiento de la aplicación LOB iOS, aparece una advertencia. Cuando expira, la alerta cambia a Expirada.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personalice los temas del Portal de empresa con códigos hexadecimales <!--1049561 -->

Puede personalizar el color del tema de las aplicaciones del Portal de empresa mediante códigos hexadecimales. Cuando escribe el código hexadecimal, Intune determina el color del texto que proporciona el nivel más alto de contraste entre el color del texto y el color del fondo. Puede obtener una vista previa del color de texto y el logotipo de la empresa con el color en **Aplicaciones cliente** > **Portal de empresa**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusión o exclusión de la asignación de aplicaciones con base en grupos para Android Enterprise <!-- 1813081 -->

Android Enterprise (anteriormente conocido como Android for Work) admite la inclusión y exclusión de grupos, pero no los grupos integrados creados previamente **Todos los usuarios** y **Todos los dispositivos**. Para obtener más información, vea [Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Administración de dispositivos

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

Para obtener más información sobre estos canales, vea [Manage Insider Preview Builds](https://insider.windows.com/en-us/for-business-organization-admin/) (Administrar compilaciones de Insider Preview).   
Para obtener más información sobre cómo crear canales de implementación en Intune, vea [Manage software updates in Intune](windows-update-for-business-configure.md) (Administrar actualizaciones de software en Intune).

### <a name="intune-apps"></a>Aplicaciones de Intune

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

## <a name="week-of-march-19-2018"></a>Semana del 19 de marzo de 2018

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>Exportar todos los dispositivos a archivos CSV en IE, Edge o Chrome <!-- 2258071 -->
En **Dispositivos** > **Todos los dispositivos**, puede **Exportar** los dispositivos a una lista con formato CSV. Los usuarios de Internet Explorer (IE) con >10.000 dispositivos pueden exportar correctamente sus dispositivos a varios archivos. Cada archivo tiene un máximo de 10.000 dispositivos.

Los usuarios de Edge y Chrome con >30.000 dispositivos pueden exportar correctamente sus dispositivos a varios archivos. Cada archivo tiene un máximo de 30.000 dispositivos.

[Administrar dispositivos](device-management.md) proporciona más detalles sobre lo que puede hacer con los dispositivos que administra.

## <a name="week-of-march-12-2018"></a>Semana del 12 de marzo de 2018

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Los sitios web de Azure Active Directory pueden requerir la aplicación Intune Managed Browser y compatibilidad con el inicio de sesión único para Managed Browser (versión preliminar pública) <!-- 710595 -->

Con Azure Active Directory (Azure AD), ya puede restringir el acceso a sitios web en dispositivos móviles para la aplicación Intune Managed Browser. En Managed Browser, los datos del sitio web permanecen seguros y separados de los datos personales del usuario final. Además, Managed Browser admite funciones de inicio de sesión único para sitios protegidos por Azure AD. Al iniciar sesión en Managed Browser, o al usarlo en un dispositivo con otra aplicación administrada por Intune, se permite que Managed Browser tenga acceso a sitios corporativos protegidos por Azure AD sin necesidad de que el usuario escriba sus credenciales. Esta funcionalidad se aplica a sitios como Outlook Web Access (OWA) y SharePoint Online, así como a otros sitios corporativos, como los recursos de intranet a los que se tiene acceso a través de Azure App Proxy. Para obtener más información, consulte [Controles de acceso en el acceso condicional de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Actualizaciones visuales de la aplicación Portal de empresa para Android <!--976944 -->

Hemos actualizado la aplicación Portal de empresa para Android para seguir las directrices de [Material Design](https://material.io/) de Android. Puede ver las imágenes de los iconos nuevos en el artículo [Novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md).

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

## <a name="week-of-february-19-2018"></a>Semana del 19 de febrero de 2018

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Compatibilidad de Intune con varias cuentas del programa del Programa de inscripción de dispositivos (DEP) de Apple o de Apple School Manager (ASM) <!-- 747685 -->

Intune ahora admite la inscripción de dispositivos de hasta 100 cuentas distintas del [Programa de inscripción de dispositivos de Apple](device-enrollment-program-enroll-ios.md) o de [Apple School Manager](apple-school-manager-set-up-ios.md). Cada token cargado puede administrarse por separado para los perfiles y los dispositivos de inscripción. Es posible asignar un perfil de inscripción diferente para cada token de DEP/School Manager. Si se cargan varios tokens de School Manager, solo pueden compartirse de uno en uno con Microsoft School Data Sync.

Tras la migración, la versión beta de las API Graph y los scripts publicados para la administración de Apple DEP o ASM en Graph ya no funcionará. Las nuevas versiones beta de las API Graph están en desarrollo y se publicarán después de la migración.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Vea las restricciones de inscripción por usuario <!-- 1634444 eeready wnready -->
En la hoja **Solución de problemas**, ahora puede ver las [restricciones de inscripción](enrollment-restrictions-set.md) que están en vigor para cada usuario si selecciona **Restricciones de inscripción** en la lista **Asignaciones**.

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


### <a name="role-based-access-control"></a>Control de acceso basado en roles
### <a name="intune-apps"></a>Aplicaciones de Intune
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Compatibilidad con aplicaciones sin conexión desde la Tienda Microsoft para Empresas <!--1222672-->
Las aplicaciones sin conexión que ha adquirido en Microsoft Store para Empresas ahora se sincronizan con Azure Portal. Puede implementar estas aplicaciones en grupos de usuarios o dispositivos. Las aplicaciones sin conexión se instalan mediante Intune, no Microsoft Store.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Impedir que los usuarios finales agreguen o quiten cuentas manualmente en el perfil de trabajo <!-- 1728700 -->

Al implementar la aplicación Gmail en un perfil de Android for Work, puede impedir que los usuarios finales agreguen o quiten cuentas en el perfil de trabajo mediante la opción de configuración **Agregar y quitar cuentas** del perfil de restricciones del dispositivo Android for Work.

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

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>compatibilidad del Portal de empresa de macOS para las inscripciones que usen el administrador de inscripciones de dispositivos <!-- 1352411 -->

Los usuarios ya pueden usar el administrador de inscripciones de dispositivos cuando se inscriban con Portal de empresa para macOS.

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

## <a name="week-of-december-4-2017"></a>Semana del 4 de diciembre de 2017

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune admite aplicaciones denegadas de Windows Information Protection (WIP) <!-- 1479103 -->
En Intune puede especificar aplicaciones denegadas. Si una aplicación queda denegada, se la bloquea para que no pueda acceder a la información de la empresa, es decir, lo contrario a la lista de aplicaciones permitidas. Para obtener más información, consulte [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Recomendación de lista de aplicaciones denegadas para Windows Information Protection).



## <a name="notices"></a>Notificaciones

### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Acción necesaria: actualización de la restricción de dispositivos Android o configuración de contraseña de directiva de cumplimiento en Intune
Intune ya no dispondrá del tipo de contraseña "predeterminada del dispositivo" para dispositivos Android 4.4 y versiones superiores. Debido a las diferencias entre las plataformas de Android y la configuración predeterminada del dispositivo, este suele tratar esta directiva como opcional. Para que no se produzcan confusiones al aplicar esta configuración en Android, se eliminará de la interfaz de usuario en una versión posterior. 
#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
- Si quiere que sea obligatorio indicar una contraseña en los dispositivos, le recomendamos que edite los perfiles de plataforma de Android para definir el tipo de contraseña necesario, en vez de usar la opción predeterminada del dispositivo.
- Si quiere que el usuario final decida si crear una contraseña o no, seleccione el botón "Sin configurar". Cuando se quite esta opción de la interfaz de usuario, si todavía está activada, recibirá una solicitud para elegir una opción distinta a la predeterminada del dispositivo al editar el perfil.
¿Qué necesito hacer para prepararme para este cambio?
Revise la configuración de contraseña en las directivas de cumplimiento y restricción de dispositivos Android y dispositivos empresariales Android. Figuran en las directivas Seguridad del sistema para cumplimiento y en las restricciones Contraseña de dispositivo o Configuración de perfil de trabajo para el dispositivo. En la información adicional encontrará un vínculo para obtener más información y capturas de pantalla sobre cómo configurar dichas opciones.
####<a name="additional-information"></a>Información adicional
https://aka.ms/PasswordSettings 

### <a name="plan-for-change-change-password-at-next-auth-added-to-intune---1873216---"></a>Plan de cambio: opción Change Password at Next Auth (Cambiar contraseña en la siguiente autenticación) agregada a Intune<!-- 1873216 -->
En la versión de servicio de septiembre, Intune planea integrar la opción **Change Password at Next Auth** (Cambiar la contraseña en la siguiente autenticación) que Apple lanzó recientemente para dispositivos que ejecutan la versión 10.13 de macOS y versiones más recientes de este sistema operativo. Antes de esta opción de configuración, los proveedores de MDM no podían comprobar que el código de paso del dispositivo se cambiaba para que fuera compatible. Las directivas de configuración y cumplimiento de Intune solo validan eso la siguiente vez que se cambia una contraseña del dispositivo, que está marcada como compatible. Cuando se agregue esta nueva característica de Apple, los usuarios de macOS recibirán una solicitud para actualizar su contraseña, aunque esta fuera compatible.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Esto afecta a los entornos con una directiva de dispositivos macOS que usan Intune o MDM híbrida. Ahora que Apple tiene la opción **Change Password at New Auth** (Cambiar contraseña en la siguiente autenticación), Intune puede exigir a los usuarios que actualicen su contraseña cuando se inserta una directiva de contraseña. Si bloquea los recursos de la empresa hasta que el dispositivo se marca como compatible, se puede bloquear a los usuarios finales para que no puedan acceder a los recursos de la empresa, como pueden ser el correo electrónico o los sitios de SharePoint, hasta que restablezcan su contraseña. En el futuro, todas las actualizaciones a las directivas de contraseña de configuración y cumplimiento exigirán a los usuarios de destino que actualicen sus contraseñas.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Hágaselo saber a su departamento de soporte técnico. Si no desea aplicar esta directiva de dispositivo de macOS, se recomienda anular la asignación de la directiva de macOS existente o eliminar dicha directiva. La investigación en los clientes sugiere que la mayoría de los clientes no se ven afectados por este cambio. La mayoría de los usuarios finales actualizan su contraseña después de recibir una solicitud para inscribirse con una contraseña o restablecen su contraseña para que siga siendo compatible.


### <a name="plan-for-change-intune-moving-to-support-ios-10-and-later-in-september----2454656---"></a>Plan de cambio: Intune admitirá iOS 10 y versiones posteriores a partir de septiembre <!-- 2454656 -->
En septiembre, se espera que Apple lance la versión iOS 12. Poco después de este lanzamiento, la inscripción de Intune, el Portal de empresa y el explorador administrado admitirán iOS 10 y versiones posteriores.  

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?  
iOS 10 y las versiones posteriores admiten aplicaciones móviles de Office 365, por lo que es posible que ya haya actualizado su sistema operativo o sus dispositivos. Si así es, este cambio no le afectará.  

Con todo, si posee o quiere inscribir alguno de los siguientes dispositivos, debe estar al tanto de que solo admiten iOS 9 y versiones anteriores.  Para seguir accediendo al Portal de empresa de Intune, debe actualizar estos dispositivos antes de septiembre a los dispositivos compatibles con iOS 10 o versión posterior:  

* iPhone 4S  
* iPod Touch  
* iPad 2  
* iPad (3ª generación)  
* iPad (1ª generación)  

A partir de julio, los dispositivos inscritos en MDM con iOS 9 y el Portal de empresa recibirán un aviso para actualizar el sistema operativo o el dispositivo. Si usa directivas de protección de aplicaciones, también puede establecer la configuración de acceso "Requerir sistema operativo iOS mínimo (solo es una advertencia)".  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?   
Busque los dispositivos o usuarios afectados de la organización. En Azure Portal, en Intune, vaya a Dispositivos > Todos los dispositivos y filtre por sistema operativo.  Haga clic en las columnas para ver detalles como la versión del sistema operativo. Pida a los usuarios que actualicen sus dispositivos a una versión del sistema operativo compatible antes de septiembre.  

### <a name="plan-for-change-intune-moving-to-tls-12"></a>Previsión de cambio: traspaso de Intune a TLS 1.2
A partir del 31 de octubre de 2018, Intune admitirá la versión 1.2 del protocolo de Seguridad de la capa de transporte (TLS) para proporcionar el mejor cifrado y garantizar que nuestro servicio sea más seguro de forma predeterminada, y para adaptarse a otros servicios de Microsoft, como Microsoft Office 365. Office comunicó este cambio en MC128929.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
A partir del 31 de octubre de 2018, Intune ya no será compatible con las versiones 1.0 o 1.1 del protocolo TLS. Todas las combinaciones de cliente y servidor, y de explorador y servidor deben usar la versión 1.2 de TLS para garantizar una conexión sin problemas a Intune. Tenga en cuenta que este cambio afectará a los dispositivos de usuario final que ya no son compatibles con Intune, pero que todavía reciben la directiva a través de Intune, y que no pueden usar la versión 1.2 de TLS. Esto incluye los dispositivos que ejecutan Android 4.3 y versiones anteriores. Para obtener una lista de exploradores y dispositivos afectados, vea la información adicional a continuación.

Después del 31 de octubre de 2018, si experimenta algún problema relacionado con el uso de una versión antigua de TLS, será necesario que actualice a TLS 1.2 o a un dispositivo que admita TLS 1.2 como parte de la resolución.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Se recomienda que quite las dependencias de TLS 1.0 y 1.1 de manera anticipada en sus entornos y deshabilite TLS 1.0 y 1.1 en el nivel de sistema operativo, en los casos en los que sea posible. Comience ya a planear la migración a TLS 1.2. Compruebe la siguiente entrada de blog de soporte técnico para obtener la lista de dispositivos que no son compatibles actualmente con Intune, pero que es posible que todavía reciban directivas, y que no podrán comunicarse con la versión 1.2 de TLS. Es posible que deba notificar a los usuarios finales de que perderán el acceso a los recursos corporativos.

**Información adicional**: [Intune moving to TLS 1.2 for encryption](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/) (Traspaso de Intune a TLS 1.2 para el cifrado)


### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Plan de cambio: cambio en la compatibilidad con el complemento de Microsoft Intune App SDK Cordova
La compatibilidad de Intune con el [complemento de Microsoft Intune App SDK Cordova](app-sdk-cordova.md) finalizará el 1 de mayo de 2018. Le recomendamos que utilice la herramienta de ajuste de aplicaciones de Intune para preparar sus aplicaciones basadas en Cordova para que estén disponibles y sean más fáciles de utilizar en Intune. Cuando este cambio surta efecto, ya no se ofrecerán actualizaciones ni soporte técnico para el complemento de Microsoft Intune App SDK Cordova. Los desarrolladores de aplicaciones no podrán usar este complemento. Está previsto que Intune siga admitiendo aplicaciones creadas con Cordova. Sin embargo, las aplicaciones creadas con el complemento de Microsoft Intune App SDK Cordova verán reducida su funcionalidad en Intune. Después de ajustar las aplicaciones con la herramienta de ajuste de aplicaciones de Intune, las aplicaciones se pueden implementar para los usuarios finales como lo haría normalmente. En el caso de aplicaciones Android basadas en Cordova que se publiquen en Google Play Store:
- La primera vez que las utilicen, los usuarios finales deberán proporcionar sus credenciales para recibir la directiva de Intune.
- Las aplicaciones deben publicarse en la tienda de aplicaciones y destinarse a usuarios de Intune, por ejemplo, "Aplicación Contoso para Intune".

Para obtener más información sobre la herramienta de ajuste de aplicaciones, consulte información sobre la [herramienta de ajuste de aplicaciones para iOS](app-wrapper-prepare-ios.md) o la [herramienta de ajuste de aplicaciones para Android](app-wrapper-prepare-android.md). Si tiene algún problema o alguna pregunta, póngase en contacto con [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com).

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Plan de cambio: use Intune en Azure ahora para la administración de MDM<!-- 1227338 -->
Hace más de un año anunciamos una [versión preliminar pública de Intune en Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) y hace seis meses seguimos con la [disponibilidad general de la nueva experiencia de administración](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) para Intune. A partir del 31 de agosto de 2018, se desactivará la administración de dispositivos móviles (MDM) en la consola de Silverlight clásica para los clientes que usan Intune de forma independiente. En su lugar, puede usar [Intune en Azure](https://aka.ms/Intune_on_Azure) para cubrir sus necesidades de MDM. Si todavía usa la consola clásica de MDM, deje de hacerlo y familiarícese con Intune en Azure. No se espera que este cambio afecte de ningún modo a los usuarios finales. La administración de PC clásica permanecerá en Silverlight. Puede obtener más información sobre este cambio y cómo le afecta [aquí](https://aka.ms/Intune_on_Azure_mdm).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->
Para las cuentas de Intune creadas después de enero de 2017, Intune habilitó el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en Azure Portal. Anteriormente, la vista preliminar de inscripción de Apple solo era accesible desde los vínculos del portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requieren una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero la información estará disponible tan pronto como sea posible. Si su cuenta existente no puede acceder a Azure Portal, le recomendamos encarecidamente que cree una cuenta de prueba para probar la nueva experiencia.

## <a name="whats-coming"></a>Próximas novedades

### <a name="local-device-security-option-settings----1251887---"></a>Configuración de opciones de seguridad del dispositivo local <!-- 1251887 -->
Podrá habilitar la configuración de seguridad en dispositivos Windows 10 con la nueva configuración de opciones de seguridad del dispositivo local. Encuentre estos valores en la categoría de Endpoint Protection cuando cree una directiva de configuración de dispositivo de Windows 10.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>Actualización de la experiencia de usuario en el sitio web de Portal de empresa <!--2000968-->

A partir de agosto se va a presentar una nueva experiencia de sitio web de Portal de empresa con actualizaciones de la interfaz de usuario, flujos de trabajo mejorados y mejoras de accesibilidad. Esto abarca mejoras orientadas al cliente, como el uso compartido de aplicaciones y un mejor rendimiento global, para proporcionarle una experiencia más sencilla.
Hemos incorporado algunas características nuevas (a raíz de comentarios de clientes como usted) que supondrán una tremenda mejora con respecto a la funcionalidad y facilidad de uso actuales:

* Mejoras de la interfaz de usuario en todo el sitio web
* Posibilidad de compartir vínculos directos a aplicaciones
* Mejor rendimiento de los catálogos de aplicaciones de gran tamaño

No hay que hacer nada para prepararse para este cambio. Le avisaremos cuando el sitio web de Portal de empresa actualizado esté disponible. Puede que, en última instancia, deba actualizar los documentos de los usuarios finales con capturas de pantalla actualizadas. Cabe mencionar que puede que también deba actualizar la documentación de la aplicación Portal de empresa en iOS, dado que la sección **Aplicaciones** de la aplicación iOS se nutre del sitio web. Puede ver una imagen de ejemplo para ello en la página de [novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->
Apple ha anunciado que se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS. Se mantendrá el [Blog de soporte técnico de Intune](https://aka.ms/compportalats) con detalles.



## <a name="see-also"></a>Vea también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](https://www.microsoft.com/cloud-platform/roadmap)
* [Novedades de la interfaz de usuario del portal de empresa](whats-new-app-ui.md)
* [Novedades de los meses anteriores](whats-new-archive.md)
