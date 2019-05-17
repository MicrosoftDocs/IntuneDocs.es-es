---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa38a684a32756d4f2c3be3b750f8e79b66e98f6
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587389"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>En desarrollo para Microsoft Intune: abril de 2019

Para ayudarle con la preparación y planeación, en esta página se enumeran las actualizaciones y características de la interfaz de usuario de Intune que están en desarrollo, pero que aún no se han publicado. Además:

- Si prevemos que tendrá que tomar medidas antes de realizar un cambio, haremos una publicación complementaria en el Centro de mensajes de Office.
- Cuando se publique una característica en producción, ya sea como versión preliminar o disponible de forma general, su descripción se quitará de esta página y se moverá a la [página Novedades](whats-new.md).
- Esta página y la [página Novedades](whats-new.md) se actualizan periódicamente. Compruebe si hay actualizaciones adicionales.
- Consulte el [plan de desarrollo de M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para conocer los plazos de tiempo y los productos estratégicos.

> [!Note]
> Estos elementos reflejan las expectativas actuales de Microsoft sobre las funcionalidades de Intune que se publicarán en una versión futura. Las fechas y las características individuales pueden cambiar. No todos los elementos que están en desarrollo tienen una descripción de la característica en esta página.

**Fuente RSS**: para recibir notificaciones cuando esta página se actualice, copie y pegue la dirección URL siguiente en el lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>Establecer configuración de inicio de sesión y opciones de reinicio de control en dispositivos macOS <!-- 1210083 -->
En dispositivos macOS, puede crear un perfil de configuración de dispositivos (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > elija **macOS** como plataforma > **Características del dispositivo** para tipo de perfil). Una nueva configuración de la ventana de inicio de sesión incluirá elementos como, por ejemplo, mostrar un encabezado personalizado, elegir cómo inician sesión los usuarios, mostrar u ocultar la configuración de energía y mucho más.

Para ver la configuración actual, vaya a [Configuración de características de dispositivos macOS](macos-device-features-settings.md).

Se aplica a: macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Configuración avanzada del Firewall de Windows Defender <!-- 1311949 -->
Pronto podrá usar Intune para administrar las reglas de firewall personalizadas en los clientes de Windows Defender. Las reglas pueden especificar un comportamiento entrante y saliente en las aplicaciones, las direcciones de red y los puertos. 

### <a name="require-app-protection-conditional-access----1634317---"></a>Requerir acceso condicional de protección de aplicaciones  <!--1634317 -->
Podrá usar la opción *Requerir la directiva de protección de aplicaciones*, que confirma que la directiva se aplica a la aplicación de un usuario antes de que se complete el inicio de sesión para impedir que los usuarios accedan a datos que protege con acceso condicional. Aunque el control de la directiva puede ralentizar la primera experiencia de uso, ayuda a protegerse frente a problemas de red, errores de configuración administrativa o intentos deliberados de evitar las directivas de protección de aplicaciones. 

### <a name="retire-noncompliant-devices----1827291---"></a>Retirar dispositivos no compatibles <!-- 1827291 -->
Vamos a agregar una nueva acción de cumplimiento para retirar un dispositivo no compatible. Al retirar un dispositivo no compatible, se quitan todos los datos de la empresa de él y también se quita el dispositivo de la administración de Intune. Esta acción se lleva a cabo cuando se alcanza el valor en días configurado. El valor mínimo es 30 días. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Configuración de las extensiones de kernel en dispositivos macOS <!-- 2043024 -->
En dispositivos macOS, puede crear un perfil de configuración de dispositivos (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > elija **macOS** como plataforma). Un nuevo grupo de configuración le permitirá configurar y usar las extensiones de kernel en los dispositivos.

Se aplica a: macOS 10.13.2 y versiones posteriores

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configuración del perfil para omitir algunas pantallas durante el Asistente para configuración <!-- 2276470 -->
Cuando cree un perfil de inscripción de macOS, podrá configurarlo para omitir cualquiera de las siguientes pantallas cuando un usuario recorra el Asistente para configuración:
- Migración de Android
- Tono de visualización
- Privacidad
- iCloudStorage: si crea un nuevo perfil o edita uno, las pantallas de omisión seleccionadas deben sincronizarse con el servidor MDM de Apple. Los usuarios pueden emitir una sincronización manual de los dispositivos para que no haya ningún retraso en la recogida de los cambios de perfil.
Para más información, consulte el artículo [Inscripción automática de dispositivos macOS con el Programa de inscripción de dispositivos o Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Los usuarios del dispositivo pueden ver todas las aplicaciones administradas que han instalado o han intentado instalar <!-- 2352913 -->
En Portal de empresa para Windows se mostrará una lista de todas las aplicaciones administradas, tanto las requeridas como las disponibles, que están instaladas en el dispositivo de un usuario. Los usuarios podrán ver las instalaciones de aplicaciones intentadas y pendientes, así como sus estados actuales. Si su organización no hace que las aplicaciones sean obligatorias o estén disponibles, los usuarios verán un mensaje en el que se explica que no se ha instalado ninguna aplicación de empresa. Los usuarios también podrán ordenar o filtrar sus aplicaciones por estado de instalación.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Etiquetas de ámbito para los tokens del Programa de compras por volumen (VPP) de Apple <!--2371886 -->
Podrá agregar etiquetas de ámbito a los tokens de VPP de Apple. Solo los usuarios que tienen asignada la misma etiqueta de ámbito tendrán acceso al token de VPP de Apple con esa etiqueta. Las aplicaciones y libros electrónicos de VPP comprados con ese token heredan sus etiquetas de ámbito. Para más información sobre las etiquetas de ámbito, vea [Use RBAC and scope tags](scope-tags.md) (Usar RBAC y etiquetas de ámbito).

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Uso de "reglas de aplicabilidad" al crear perfiles de configuración de dispositivo Windows 10 <!-- 2549910 -->
Puede crear perfiles de configuración de dispositivo Windows 10 (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10** como plataforma). Podrá crear una **regla de aplicabilidad** para que el perfil solo se aplique a una edición o una versión en concreto. Por ejemplo, cree un perfil que permita algunas opciones de configuración de BitLocker. Una vez que agregue el perfil, use una regla de aplicabilidad para que este solo se aplique a los dispositivos que ejecuten Windows 10 Enterprise.

Se aplica a: 
- Windows 10 y versiones posteriores

### <a name="enable-win32-app-dependencies----2617348---"></a>Habilitar dependencias de la aplicación Win32 <!-- 2617348 -->
Versión preliminar pública: como administrador, podrá exigir que se instalen otras aplicaciones como dependencias antes de instalar la aplicación Win32. En concreto, el dispositivo debe instalar las aplicaciones dependientes antes de que se instale la aplicación Win32. Esta funcionalidad solo estará disponible después de actualizar el agente de administración de Intune a la versión 1904 (posterior a 1.18.120.0), y podría tardar una o dos semanas más después de actualizar el servicio a 1904. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar** para mostrar la hoja **Agregar aplicación**. Seleccione **Aplicación de Windows (Win32)** como **Tipo de aplicación**. Para más información, vea [Intune independiente: administración de aplicaciones Win32](apps-win32-app-management.md).

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Nueva configuración de restricción de dispositivos de Propietario del dispositivo en Android Enterprise: permitir que los usuarios se conecten a redes Wi-Fi en dispositivos dedicados Android Enterprise que se ejecutan en pantalla completa con varias aplicaciones <!--3041940 -->
Los administradores podrán activar o desactivar una nueva opción que permite a los usuarios configurar el Bluetooth en sus dispositivos dedicados Android Enterprise que se ejecutan en pantalla completa con varias aplicaciones. Para ver esta configuración en la consola de Intune, elija **Intune** > **Configuración de dispositivo** > **Perfiles** > **Crear perfil** > elija **Android Enterprise** como plataforma > **Solo el propietario del dispositivo, Restricciones de dispositivos** como tipo de perfil > **Configuración** > **Dispositivos dedicados** > seleccione **Varias aplicaciones** en el menú desplegable de la configuración **Pantalla completa**. Podrá habilitar una configuración denominada **Configuración de Wi-Fi**. 

Se aplica a: dispositivos dedicados Android Enterprise que se ejecutan en pantalla completa con varias aplicaciones. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Nueva configuración de restricción de dispositivos de Propietario del dispositivo en Android Enterprise: permitir que los usuarios configuren el Bluetooth y el emparejamiento en dispositivos dedicados Android Enterprise <!--3041941 -->
Los administradores podrán activar o desactivar una nueva opción que permite a los usuarios configurar el Bluetooth en sus dispositivos dedicados Android Enterprise que se ejecutan en pantalla completa con varias aplicaciones. Para ver esta configuración en la consola de Intune, elija **Intune** > **Configuración de dispositivo** > **Perfiles** > **Crear perfil** > elija **Android Enterprise** como plataforma > **Solo el propietario del dispositivo, Restricciones de dispositivos** como tipo de perfil > **Configuración** > **Dispositivos dedicados** > seleccione **Varias aplicaciones** en el menú desplegable de la configuración **Pantalla completa**. Podrá habilitar una configuración denominada **Configuración de Bluetooth**. 

Se aplica a: dispositivos dedicados Android Enterprise que se ejecutan en pantalla completa con varias aplicaciones. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Supervisar el estado de las líneas bases de seguridad (versión preliminar) <!-- 3082047 --> 
Al supervisar el *Estado del dispositivo* de sus líneas base de seguridad, la vista organizará el estado por categorías de línea base, como *Above lock* (Por encima de la pantalla de bloqueo), *BitLocker* y  *Explorador*. Se representarán todas las categorías de línea base disponibles. Para cada categoría, podrá ver cuántos dispositivos no coinciden con una categoría de línea base específica, están mal configurados o no son aplicables.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Tareas de seguridad de Intune para ATP de Defender (en versión preliminar pública) <!-- 3208597 -->
Intune agregará pronto tareas de seguridad en forma de versión preliminar pública para el recién anunciado Microsoft Defender Threat & Vulnerability Management.  Con esta integración, los administradores de operaciones de seguridad de ATP de Windows Defender (WDATP) pueden comunicar de forma más eficaz las correcciones recomendadas para las amenazas emergentes a los administradores de Intune. Al incluir las tareas de seguridad, se agrega un enfoque basado en riesgos para detectar, priorizar y corregir los errores de configuración y las vulnerabilidades del punto de conexión.

Para obtener más información sobre las tareas de seguridad en Intune, consulte la entrada de blog sobre [cómo usar las tareas de seguridad de Intune para ampliar Threat and Vulnerability Management de ATP de Microsoft Defender](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>Crear y usar perfiles de configuración de dispositivos OEMConfig en Intune <!-- 3305883 -->
Intune admitirá la configuración de dispositivos Android Enterprise con OEMConfig. En concreto, puede crear un perfil de configuración de dispositivo y aplicar la configuración a los dispositivos Android Enterprise mediante OEMConfig (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma).

Actualmente, la compatibilidad con fabricantes de equipos originales depende del fabricante. Si quiere una aplicación OEMConfig que no está disponible en la lista de aplicaciones OEMConfig, póngase en contacto con `IntuneOEMConfig@microsoft.com`.

Se aplica a: 
- Android Enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Nueva configuración de restricción de dispositivos para Propietario del dispositivo en Android Enterprise <!-- 3574254 -->
En dispositivos Android Enterprise, puede crear un perfil de restricción de dispositivos para permitir o restringir características, establecer reglas de contraseña y mucho más (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > elija **Android Enterprise** para plataforma > **Solo el propietario del dispositivo > Restricciones de dispositivos** para el tipo de perfil). 

Nueva configuración que incluye opciones de configuración de contraseñas y que permite el acceso total a las aplicaciones en Google Play Store para dispositivos totalmente administrados y mucho más. 

Para ver la lista actual de configuraciones, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características](device-restrictions-android-for-work.md). 

Se aplica a: dispositivos Android Enterprise totalmente administrados

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Buscar un conjunto de chips TPM en una directiva de cumplimiento de dispositivos Windows 10 <!-- 3617671 -->
Muchos dispositivos Windows 10 y posteriores tienen conjuntos de chips del Módulo de plataforma segura (TPM). Una nueva configuración de cumplimiento comprobará si hay un TPM en el dispositivo.

En la [configuración de directivas de cumplimiento de Windows 10 y versiones posteriores](compliance-policy-create-windows.md) se muestra la configuración actual.

Se aplica a: 
- Windows 10 y versiones posteriores

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Configurar las aplicaciones Win32 para instalarlas en dispositivos unidos a Azure AD inscritos en Intune <!-- 3695227 -->
Podrá asignar las aplicaciones Win32 para instalarlas en dispositivos unidos a Azure AD inscritos en Intune. Para más información sobre las aplicaciones Win32 en Intune, vea [Administración de aplicaciones Win32](apps-win32-app-management.md).

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Línea de base de Advanced Threat Protection de Windows Defender <!-- 3754134 -->
Vamos a agregar una nueva línea base para ayudarle a configurar las opciones de Protección contra amenazas avanzada de Windows Defender.

### <a name="device-overview-shows-primary-user---794259---"></a>Usuario primario mostrado en Resumen del dispositivo <!--794259 -->
La página Resumen del dispositivo mostrará el usuario primario, también denominado el usuario de afinidad de dispositivo de usuario (UDA). Para ver el usuario primario de un dispositivo, seleccione **Intune** > **Dispositivos** > **Todos los dispositivos** y elija un dispositivo. El usuario primario se muestra cerca de la parte superior de la página **Resumen**.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>Compatibilidad ampliada para dispositivos Android Enterprise totalmente administrados <!-- 3903241, 3903244, 3903246 -->
Vamos a ampliar la compatibilidad de los dispositivos Android Enterprise totalmente administrados ([se anunció por primera vez en enero de 2019](whats-new.md#week-of-january-14-2019)) para incluir lo siguiente:
- Cumplimiento
- Acceso condicional
- Nueva aplicación de usuario final

Para configurar dispositivos Android totalmente administrados, vaya a **Dispositivo administrado** > **Inscripción de Android** > **Corporate-owned, fully managed user devices** (Dispositivos de usuario totalmente administrados de propiedad corporativa). La compatibilidad con dispositivos Android totalmente administrados sigue en versión preliminar y algunas características de Intune podrían no ser totalmente funcionales. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Otros informes de aplicaciones de Google Play administrado para dispositivos de perfil de trabajo de Android Enterprise <!-- 4105925 -->
Para las aplicaciones de Google Play administrado implementadas en dispositivos de perfil de trabajo Android Enterprise, podrá ver el número de versión específica de la aplicación instalada en un dispositivo. Esto se aplica solo a las aplicaciones necesarias. En una versión futura se habilitará la misma función para las aplicaciones disponibles.

### <a name="ios-third-party-keyboards----4111843---"></a>Teclados de terceros de iOS <!-- 4111843 -->
La compatibilidad de la directiva de protección de aplicaciones (APP) de Intune con la configuración **Teclados de terceros** finalizará debido a un cambio de la plataforma iOS. No podrá configurar esta opción en la consola de administración de Intune y no se aplicará en el cliente en Intune App SDK.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>Impedir que los usuarios busquen actualizaciones de Windows <!-- 3316758 -->
Vamos a agregar una nueva configuración del anillo de Windows Update que puede usar para impedir que los usuarios busquen actualizaciones de Windows. Esta configuración no estará disponible en el portal, pero se puede configurar mediante Graph API de Intune.

### <a name="windows-update-notifications----3316782---"></a>Notificaciones de Windows Update <!-- 3316782 -->
Vamos a agregar compatibilidad con las configuraciones del anillo de Windows Update, de modo que podrá configurar las notificaciones de Windows Update que ven los usuarios. Esta configuración no estará disponible en el portal, pero se puede configurar mediante Graph API de Intune.

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>Acceso más fácil a la configuración de diagnóstico <!-- 3804627 -->
Vamos a agregar una nueva opción a la hoja **Registros de auditoría** de cada carga de trabajo de registro de auditoría en la consola de Intune que puede usar para abrir directamente la página *Configuración de diagnóstico*.

## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


