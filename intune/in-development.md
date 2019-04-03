---
title: En el desarrollo - Microsoft Intune
titlesuffix: ''
description: En el desarrollo de las características de Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
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
ms.openlocfilehash: 3e068e2c9834290b705e8e7bc2f895636415f9ba
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675449"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>En el desarrollo de Microsoft Intune: abril de 2019

Para ayudar a su nivel de preparación y planeación, esta página listas Intune UI actualizaciones y características que están en desarrollo, pero aún no se ha liberado. Además:

- Si se prevé que deberá tomar medidas antes de realizar un cambio, publicaremos una entrada de centro de mensajes de Office gratuita.
- Cuando se inicia una característica en producción, ya sea como una vista previa o en disponibilidad general, se moverá la descripción de la característica fuera de esta página y en el [página Novedades](whats-new.md).
- Esta página y el [página Novedades](whats-new.md) se actualizan periódicamente. Compruebe si hay actualizaciones adicionales.
- Hacer referencia a la [guía básica de M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para entregas estratégicas y las escalas de tiempo.

> [!Note]
> Estos elementos reflejan las expectativas actuales de Microsoft sobre las capacidades de Intune que entran en una versión futura. Pueden cambiar las fechas y las características individuales. No todos los elementos de desarrollo tienen una descripción de la característica en esta página.

**Fuente RSS**: para recibir notificaciones cuando esta página se actualice, copie y pegue la dirección URL siguiente en el lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>Establecer la configuración de inicio de sesión y controlar las opciones de reinicio en dispositivos macOS <!-- 1210083 -->
En los dispositivos macOS, puede crear un perfil de configuración de dispositivo (**configuración del dispositivo** > **perfiles** > **Crear perfil** > Elija **macOS** para plataforma > **características del dispositivo** para el tipo de perfil). Nueva configuración de la ventana de inicio de sesión se incluyen elementos como mostrar un encabezado personalizado, elija cómo los usuarios iniciar sesión, mostrar u ocultar la configuración de energía y mucho más.

Para ver la configuración actual, vaya a [configuración de características de dispositivos macOS](macos-device-features-settings.md).

Se aplica a: macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Configuración avanzada de Firewall de Windows Defender <!-- 1311949 -->
Pronto podrá usar Intune para administrar las reglas de firewall personalizadas en los clientes de Windows Defender. Las reglas pueden especificar comportamiento entrante y saliente a las aplicaciones, las direcciones de red y puertos. 

### <a name="require-app-protection-conditional-access----1634317---"></a>Requieren acceso condicional de protección de aplicaciones  <!--1634317 -->
Podrá usar *directiva de protección de aplicaciones requieren*, que confirma la directiva se aplica a una aplicación de usuario antes de que finalice el inicio de sesión para impedir que los usuarios tengan acceso a datos que protege con acceso condicional. Mientras la garantía de la directiva puede ralentizar la primera experiencia de uso, ayuda a protegerse frente a problemas de red, errores de configuración administrativas o intencionados esfuerzos para frustrar directivas de protección de aplicaciones. 

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----16726660---"></a>Implementación de aplicaciones de Microsoft Store para Empresas con licencias en línea <!-- 16726660 -->
Podrá asignar las aplicaciones de Microsoft Store para Empresas con licencias en línea necesarias en el contexto del dispositivo. Implementar una aplicación de Microsoft Store para Empresas de esta forma permitirá que la aplicación se instale para todos los usuarios en el dispositivo. Esto solo es aplicable para dispositivos de escritorio de Windows 10 RS4+. La opción para instalar en el contexto del dispositivo está disponible en la página de asignación de aplicaciones del cliente para las aplicaciones con licencia en línea de MSFB.

### <a name="include-and-exclude-mixture-of-user-groups-and-device-groups-when-assigning-policies-and-profiles----1807547---"></a>Incluir y excluir la mezcla de grupos de usuarios y grupos de dispositivos al asignar directivas y perfiles <!-- 1807547 -->
Al asignar las directivas de cumplimiento o perfiles de configuración, puede asignarlos a grupos de seguridad con los usuarios o dispositivos. Actualmente, puede incluir y excluir grupos de usuarios solo *o* incluir y excluir solo los grupos de dispositivos. No se puede incluir y excluir una combinación de grupos, como incluir grupos de usuarios *y* excluir un grupo de dispositivos.

Podrá incluir y excluir una combinación de grupos de usuarios y grupos de dispositivos. Puede incluir un grupo de usuarios y excluir un grupo de dispositivos. Por ejemplo, puede asignar o implementar un perfil de configuración de dispositivo a un grupo de usuarios, pero excluir dispositivos personales.

[Asignar perfiles de configuración de dispositivo](device-profile-assign.md) incluye más información sobre cómo asignar perfiles de grupos de usuarios y grupos de dispositivos.

Se aplica a: todas las plataformas

### <a name="retire-noncompliant-devices----1827291---"></a>Retirar dispositivos no conformes <!-- 1827291 -->
Vamos a agregar una nueva acción de cumplimiento para retirar un dispositivo no compatible. Retirar un dispositivo no compatible quita todos los datos de la empresa y también quita el dispositivo que sean administrados por Intune. Esta acción se ejecuta cuando se alcanza el valor configurado en días. El valor mínimo es 30 días. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Configurar opciones para las extensiones de kernel en dispositivos macOS <!-- 2043024 -->
En los dispositivos macOS, puede crear un perfil de configuración de dispositivo (**configuración del dispositivo** > **perfiles** > **Crear perfil** > Elija **macOS** para la plataforma). Un nuevo grupo de configuración le permitirá configurar y usar extensiones de kernel en los dispositivos.

Se aplica a: macOS 10.13.2 y versiones posteriores

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configuración del perfil para omitir algunas pantallas durante el Asistente para configuración <!-- 2276470 -->
Cuando cree un perfil de inscripción de macOS, podrá configurarlo para omitir cualquiera de las siguientes pantallas cuando un usuario recorra el Asistente para configuración:
- Migración de Android
- Tono de visualización
- Privacidad
- iCloudStorage: si crea un nuevo perfil o edita uno, las pantallas de omisión seleccionadas deben sincronizarse con el servidor MDM de Apple. Los usuarios pueden emitir una sincronización manual de los dispositivos para que no haya ningún retraso en la recogida de los cambios de perfil.
Para más información, consulte el artículo [Inscripción automática de dispositivos macOS con el Programa de inscripción de dispositivos o Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Los usuarios de dispositivos pueden ver todas las aplicaciones administradas que han instalado o se ha intentado instalar <!-- 2352913 -->
Portal de empresa para Windows mostrará una lista de todas las aplicaciones administradas&ndash; requerido y disponible&ndash; que están instalados en el dispositivo del usuario. Los usuarios podrán a la vista que se ha intentado y pendiente de las instalaciones de aplicaciones y sus estados actuales. Si su organización no hace que las aplicaciones necesarias o disponibles, los usuarios verán un mensaje que explica que no hay aplicaciones de empresa se han instalado. Los usuarios también podrán ordenar o filtrar sus aplicaciones por estado de la instalación.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Etiquetas de ámbito para los tokens de PCV de Apple <!--2371886 -->
Podrá agregar las etiquetas de ámbito a los tokens de PCV de Apple. Solo los usuarios asignados con la misma etiqueta de ámbito tendrán acceso al token de PCV de Apple con esa etiqueta. Las aplicaciones de PCV y libros electrónicos comprados con ese token heredan sus etiquetas de ámbito. Para obtener más información acerca de las etiquetas de ámbito, consulte [etiquetas RBAC de uso y ámbito](scope-tags.md).

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Utilice "reglas de aplicabilidad" al crear perfiles de configuración de dispositivo Windows 10 <!-- 2549910 -->
Crear perfiles de configuración de dispositivo Windows 10 (**configuración del dispositivo** > **perfiles** > **Crear perfil**  >  **Windows 10** para la plataforma). Podrá crear un **regla de aplicabilidad** para el perfil solo se aplica a una edición específica o una versión específica. Por ejemplo, cree un perfil que permite algunas opciones de configuración de BitLocker. Una vez que agregue el perfil, use una regla de aplicabilidad para que el perfil solo se aplica a los dispositivos que ejecutan Windows 10 Enterprise.

Se aplica a: 
- Windows 10 y versiones posteriores

### <a name="enable-win32-app-dependencies----2617348---"></a>Habilitar dependencias de la aplicación Win32 <!-- 2617348 -->
Versión preliminar pública: como administrador, podrá requerir que otras aplicaciones están instaladas como dependencias antes de instalar la aplicación de Win32. En concreto, el dispositivo debe instalar las aplicaciones dependientes antes de que instale la aplicación de Win32. Esta funcionalidad estará disponible después de que el agente de administración de Intune se ha actualizado a la versión de 1904 (mayor que 1.18.120.0) que puede tardar de 1 o 2 semanas adicionales después de que se actualice el servicio en 1904. En Intune, seleccione **las aplicaciones cliente** > **aplicaciones** > **agregar** para mostrar el **Agregar aplicación** hoja. Seleccione **aplicación de Windows (Win32)** como el **tipo de aplicación**. Para obtener más información, consulte [Intune Standalone - administración de aplicaciones de Win32](apps-win32-app-management.md).

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Nueva configuración de restricción de dispositivos para Android Enterprise, el propietario del dispositivo: permite que los usuarios se conecten a redes Wi-Fi en dispositivos de Android Enterprise dedicados que ejecutan el modo de quiosco con varias aplicaciones <!--3041940 -->
Los administradores podrán activar o desactivar una nueva opción que permite a los usuarios configurar el Bluetooth en sus dispositivos Android Enterprise dedicado que ejecuta el modo de quiosco con varias aplicaciones. Para ver esta configuración en la consola de Intune, elija **Intune** > **configuración del dispositivo** > **perfiles**  >  **Crear perfil** > elija **Android Enterprise** para plataforma > **solo el propietario del dispositivo, las restricciones de dispositivos** para el tipo de perfil > **configuración**   >  **Los dispositivos dedicados** > seleccione **con varias aplicaciones** desde el **modo de quiosco** configuración de lista desplegable. Una opción denominada **configuración Wi-Fi** estarán disponibles para habilitar. 

Se aplica a: Android Enterprise dedicado a los dispositivos que ejecutan el modo de quiosco con varias aplicaciones. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Nueva configuración de restricción de dispositivos para Android Enterprise, el propietario del dispositivo: permitir que los usuarios configurar el emparejamiento en dispositivos Android Enterprise dedicado y Bluetooth <!--3041941 -->
Los administradores podrán activar o desactivar una nueva opción que permite a los usuarios configurar el Bluetooth en sus dispositivos Android Enterprise dedicado que ejecuta el modo de quiosco con varias aplicaciones. Para ver esta configuración en la consola de Intune, elija **Intune** > **configuración del dispositivo** > **perfiles**  >  **Crear perfil** > elija **Android Enterprise** para plataforma > **solo el propietario del dispositivo, las restricciones de dispositivos** para el tipo de perfil > **configuración**   >  **Los dispositivos dedicados** > seleccione **con varias aplicaciones** desde el **modo de quiosco** configuración de lista desplegable. Una opción denominada **configuración de Bluetooth** estarán disponibles para habilitar. 

Se aplica a: Android Enterprise dedicado a los dispositivos que ejecutan el modo de quiosco con varias aplicaciones. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Supervisar el estado de la línea de base de seguridad (versión preliminar) <!-- 3082047 --> 
Al supervisar el *estado del dispositivo* para sus líneas base de seguridad, la vista organizará el estado por las categorías de línea base, como *anteriormente bloqueo*, *BitLocker*y  *Explorador*. Todas las categorías de línea base disponibles se representará. Para cada categoría, podrá ver cuántos dispositivos no coinciden con una categoría específica de la línea de base, están mal configurados o no son aplicables.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Tareas de seguridad de Intune para Defender ATP (en versión preliminar pública) <!-- 3208597 -->
Estará disponible como versión preliminar pública, Intune pronto lo ampliaremos tareas de seguridad para el recién anunciado Microsoft Defender Threat & administración de vulnerabilidades.  Con esta integración, los administradores de operaciones de seguridad de Windows Defender ATP (WDATP) pueden comunicarse de forma más eficaz las correcciones recomendadas para las amenazas emergentes para los administradores de Intune. La adición de las tareas de seguridad agrega un enfoque basado en riesgos para detectar, priorizar y corregir errores de configuración y las vulnerabilidades de punto de conexión.

Para obtener más información sobre las tareas de seguridad en Intune, consulte la entrada de blog sobre [mediante tareas de seguridad de Intune para ampliar la amenaza y la administración de vulnerabilidades de Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>Crear y usar perfiles de configuración de dispositivo OEMConfig en Intune <!-- 3305883 -->
Intune admitirá la configuración de dispositivos empresariales Android con OEMConfig. En concreto, puede crear un perfil de configuración de dispositivo y aplicar la configuración para dispositivos Android Enterprise mediante OEMConfig (**configuración del dispositivo** > **perfiles**  >  **Crear perfil** > **Android enterprise** para la plataforma).

Compatibilidad con los fabricantes OEM está actualmente en una base por OEM. Si una aplicación OEMConfig desea no está disponible en la lista de aplicaciones OEMConfig, póngase en contacto con `IntuneOEMConfig@microsoft.com`.

Se aplica a: 
- Android Enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Nueva configuración de restricción de dispositivos para Android Enterprise, el propietario del dispositivo <!-- 3574254 -->
En los dispositivos Android Enterprise, puede crear un perfil de restricción de dispositivos para permitir o restringir las características, establecer reglas de contraseña etc. (**configuración del dispositivo** > **perfiles**  >  **Crear perfil** > elija **Android Enterprise** para plataforma > **solo el propietario del dispositivo > restricciones de dispositivos** para el tipo de perfil). 

Nueva configuración, incluida la configuración de contraseña, lo que completa el acceso a aplicaciones en Google Play Store para dispositivos totalmente administrados y habrá más disponibles. 

Para ver la lista actual de configuraciones, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características](device-restrictions-android-for-work.md). 

Se aplica a: dispositivos de Android Enterprise totalmente administrados

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Busque un conjunto de chips TPM en una directiva de cumplimiento de dispositivos Windows 10 <!-- 3617671 -->
Muchos de Windows 10 y dispositivos posteriores tienen conjuntos de chips del módulo de plataforma segura (TPM). Una nueva configuración de cumplimiento comprobará si es un TPM en el dispositivo.

[Windows 10 y posterior configuración de directiva de cumplimiento](compliance-policy-create-windows.md#windows-10-and-later-policy-settings) se muestra la configuración actual.

Se aplica a: 
- Windows 10 y versiones posteriores

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Configurar las aplicaciones de Win32 para instalarse en Intune inscrito los dispositivos Unidos a Azure AD <!-- 3695227 -->
Podrá para dispositivos Unidos a asignar las aplicaciones de Win32 para instalarse en Intune inscrito Azure AD. Para obtener más información acerca de las aplicaciones de Win32 en Intune, consulte [administración de aplicaciones de Win32](apps-win32-app-management.md).

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Línea de base de Advanced Threat Protection de Windows Defender <!-- 3754134 -->
Vamos a agregar la nueva línea base para ayudarle a configurar la configuración de protección de amenazas avanzada de Windows Defender.

### <a name="device-overview-shows-primary-user---794259---"></a>Información general del dispositivo muestra el usuario primario <!--794259 -->
La página de información general del dispositivo mostrará el usuario principal, también denominado el usuario de afinidad de dispositivo de usuario (UDA). Para ver el usuario primario de un dispositivo, elija **Intune** > **dispositivos** > **todos los dispositivos** > elija un dispositivo. El usuario primario aparecen cerca de la parte superior de la **Introducción** página.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>Compatibilidad ampliada con los dispositivos empresariales Android totalmente administrados <!-- 3903241, 3903244, 3903246 -->
Vamos a ampliar la compatibilidad de dispositivos empresariales Android totalmente administrados ([presentó por primera vez en enero de 2019](whats-new.md#week-of-january-14-2019) incluir lo siguiente:
- Cumplimiento
- Acceso condicional
- Nuevo usuario final App

Para configurar dispositivos Android totalmente administrados, vaya a **Dispositivo administrado** > **Inscripción de Android** > **Corporate-owned, fully managed user devices** (Dispositivos de usuario totalmente administrados de propiedad corporativa). Compatibilidad con dispositivos Android totalmente administrados permanece en versión preliminar y algunas características de Intune podrían no ser totalmente funcional. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Aplicación de Google Play administrado adicionales informes para dispositivos de perfil de trabajo de Android Enterprise <!-- 4105925 -->
Para aplicaciones de Google Play administrado implementadas en dispositivos de perfil de trabajo de Android Enterprise, es posible ver el número de versión específica de la aplicación instalada en un dispositivo. Esto se aplica solo a las aplicaciones necesarias. En una versión futura se habilitará la misma funcionalidad para las aplicaciones disponibles.

### <a name="ios-third-party-keyboards----4111843---"></a>Teclados de terceros de iOS <!-- 4111843 -->
Compatibilidad con la directiva de protección de aplicaciones de Intune (aplicación) para el **teclados de terceros** configuración finalizará debido a un cambio de plataforma de iOS. No será capaz de configurar esta opción en la consola de administración de Intune y no se aplicarán en el cliente de Intune App SDK.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>Impedir que los usuarios buscar actualizaciones de Windows <!-- 3316758 -->
Estamos agregando una nueva opción de anillo de actualización de Windows que puede usar para impedir que los usuarios buscar actualizaciones de Windows. Esta opción no estará disponible en el portal, pero puede configurarse mediante el uso de Graph API de Intune.

### <a name="windows-update-notifications----3316782---"></a>Notificaciones de actualización de Windows <!-- 3316782 -->
Estamos agregando compatibilidad para las configuraciones de anillo de actualización de Windows por lo que podrá configurar las notificaciones de actualización de Windows que ven los usuarios. Esta opción no estará disponible en el portal, pero puede configurarse mediante el uso de Graph API de Intune.

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Cambios realizados en la inscripción de Portal de empresa para los usuarios de dispositivos iOS 12 <!--3448635 --> 
Portal de empresa para iOS va a actualizar las pantallas de la inscripción de aplicación y los pasos para alinearse con los cambios de inscripción de MDM que publicó en Apple iOS 12.2. El flujo de trabajo actualizado ahora le pedirá a los usuarios:

- Permitir Safari abrir el sitio Web de Portal de empresa (a través de Safari) y descargar el perfil de administración antes de volver a la aplicación de Portal de empresa.
- Abra la aplicación de configuración para instalar el perfil de administración en su dispositivo.
- Vuelva a la aplicación de Portal de empresa para realizar la inscripción.

Para obtener más información acerca de cómo puede prepararse para estos cambios, consulte el [post de la comunidad tecnológica de Microsoft](https://aka.ms/CP_changes_iOS12). Mientras tanto, para admitir nuevas inscripciones de iOS en el Portal de empresa, hemos actualizado los pasos descritos en [inscribir dispositivos de iOS en Intune](https://docs.microsoft.com/en-us/intune/ios-enroll). Estos cambios de documento permanecerá en vigor después de Apple iOS versión 12.2 de versiones. 

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>Facilitar el acceso a la configuración de diagnóstico <!-- 3804627 -->
Vamos a agregar una nueva opción para el **registros de auditoría** hoja de cada carga de trabajo de registro de auditoría en la consola de Intune que puede usar para abrir directamente el *configuración de diagnóstico* página.

## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


