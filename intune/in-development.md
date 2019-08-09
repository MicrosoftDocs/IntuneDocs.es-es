---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 969e7bc4804e1f66230c76d742bec2c67c2fa006
ms.sourcegitcommit: 99b74d7849fbfc8f5cf99cba33e858eeb9f537aa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670908"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>En desarrollo para Microsoft Intune: agosto de 2019

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

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Administración de aplicaciones

### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144---"></a>Control del comportamiento de desinstalación de aplicaciones iOS en anulación de la inscripción de dispositivos <!-- 3504144 -->
Los administradores podrán administrar si se quita o se conserva una aplicación en un dispositivo cuando se anula la inscripción del dispositivo en el nivel de grupo de usuarios o dispositivos. 

### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Categorización de aplicaciones de Microsoft Store para Empresas <!-- 3926922 -->
Podrá clasificar Microsoft Store para aplicaciones empresariales. Para ello, elija aplicaciones  > **cliente** > de **Intune** **aplicaciones** > seleccione una aplicación de Microsoft Store para empresas  > **categoría**de **información**de la aplicación. En el menú desplegable, asigne una categoría.
### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar el contenido de notificación de aplicación para las cuentas de la organización <!-- 2576686 -->
Las directivas de protección de aplicaciones (APP) de Intune en dispositivos iOS y Android le permitirán controlar el contenido de las notificaciones de la aplicación para las cuentas de la organización. Esta característica requerirá la compatibilidad de las aplicaciones y es posible que no esté disponible para todas las aplicaciones habilitadas para la aplicación. Consulte [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) para obtener más información sobre APP.

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Notificación de aplicaciones de Google Play disponibles para perfiles de trabajo de Android <!-- 3041956  -->
En las instalaciones de aplicaciones disponibles en dispositivos de perfil de trabajo de Android, puede ver el estado de instalación de la aplicación y la versión instalada de aplicaciones administradas de Google Play. Para obtener más información, vea [Supervisión de las directivas de protección de aplicaciones](app-protection-policies-monitor.md), [Administrar dispositivos de perfil de trabajo Android con Intune](android-enterprise-overview.md) y [Tipo de aplicación de Google Play administrado](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración de los dispositivos

### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809----"></a>Algunas restricciones de dispositivos iOS no supervisadas se supervisarán solo con la versión iOS 13,0 <!-- 4867809  -->
Algunos valores de configuración se aplicarán a los dispositivos solo supervisados con la versión iOS 13,0. Estas opciones incluyen:

- Tienda de aplicaciones, presentación de documentos, juegos
  - Tienda de aplicaciones
  - Contenido de iTunes, música, podcast o News explícito
  - Incorporación de amigos a Game Center
  - Juego multijugador
- Aplicaciones integradas
  - Cámara
    - FaceTime
  - Safari
    - Autorrellenar
- Nube y almacenamiento
  - Copia de seguridad en iCloud
  - Bloquear la sincronización de documentos de iCloud
  - Bloquear la sincronización de Keychain en iCloud

Si estas opciones se configuran y se asignan a dispositivos no supervisados antes de la versión de iOS 13,0, la configuración se seguirá aplicando a esos dispositivos no supervisados. También se aplican después de que los dispositivos se actualicen a iOS 13,0. Estas restricciones se quitan de los dispositivos no supervisados de los que se realiza una copia de seguridad y se restauran. 

Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](device-restrictions-ios.md).

Se aplica a:  
- iOS 13,0 y versiones más recientes

### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709----"></a>Nuevas configuraciones y cambios en la configuración existente para restringir características en dispositivos iOS y macOS <!-- 4867699 4867709  -->
Podrá crear perfiles para restringir la configuración de los dispositivos que ejecutan iOS y MacOS (**perfiles** > de**configuración** > de dispositivo**crear perfil** > **iOS** o **MacOS** para plataforma Escriba > **restricciones de dispositivos**). Se agregarán las siguientes características:

- En**la nube y el almacenamiento**de**restricciones** > de dispositivos **MacOS** > , use la nueva configuración de **entrega** para impedir que los usuarios inicien el trabajo en un dispositivo MacOS y continúe trabajando en otro dispositivo MacOS o iOS.
  Para ver la configuración actual, vaya a [Configuración de dispositivos macOS para permitir o restringir características mediante Intune](device-restrictions-macos.md).
- En las**restricciones de dispositivos** **iOS** > , hay algunos cambios:
  - **Aplicaciones integradas** **Buscar mi iPhone (solo supervisado)** : nueva configuración que bloquea esta característica en la característica buscar mi aplicación. >  
  - **Aplicaciones integradas** **Buscar mis amigos (solo supervisado)** : nueva configuración que bloquea esta característica en la característica buscar mi aplicación. >  
  - **Modificación inalámbrica** > **del estado de Wi-Fi (solo supervisado)** : nueva configuración que impide que los usuarios enciendan o desactiven Wi-Fi en el dispositivo.
  - **Teclado y Diccionario** > **QuickPath (solo supervisado)** : nueva configuración que bloquea la característica QuickPath.
  - **Nube y almacenamiento: la**continuación de la **actividad** cambia de nombre a **entrega**.

  Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](device-restrictions-ios.md).

Se aplica a:  
- macOS 10,15 y versiones más recientes
- iOS 13 y versiones más recientes

### <a name="control-the-apps-files-documents-and-folders-that-open-when-user-signs-in-to-macos-devices---3914202----"></a>Controle las aplicaciones, los archivos, los documentos y las carpetas que se abren cuando el usuario inicia sesión en dispositivos macOS <!--3914202  -->
Podrá habilitar y configurar características en dispositivos MacOS (**perfiles** > de**configuración** > de dispositivos**crear perfil** > **MacOS** para plataformas > características de **dispositivo** para tipo de perfil). 

Habrá nuevas opciones de configuración de elementos de inicio de sesión para controlar qué aplicaciones, archivos, documentos y carpetas se abren cuando un usuario inicia sesión en el dispositivo inscrito. 

Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](macos-device-features-settings.md).

Se aplica a:  
- macOS

### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946----"></a>Nuevas características para dispositivos Android Enterprise dedicados en modo de varias aplicaciones <!-- 3755304 3041943 3041946  -->
Podrá controlar las características y la configuración en una experiencia de estilo quiosco en los dispositivos de Android Enterprise dedicados. Para ello, elija **configuración** > de dispositivos**perfiles** > **crear perfil** > **Android Enterprise** para plataforma > **propietario del dispositivo solo, restricciones de dispositivo** para el tipo de perfil.

Se agregarán las siguientes características:
- **Dispositivos dedicados** > **varias aplicaciones**: el **botón Inicio virtual** se puede mostrar al avanzar en el dispositivo o flotar en la pantalla para que los usuarios puedan moverla.
- **Dispositivos dedicados** > **múltiples aplicaciones**: el acceso a la **linterna** permite a los usuarios usar la linterna. 
- **Dispositivos dedicados** > **múltiples aplicaciones**: **control de volumen multimedia** permite a los usuarios controlar el volumen multimedia del dispositivo con un control deslizante. 
- **Dispositivos dedicados:** **aplicación múltiple**: habilita un protector de la imagen, carga una imagen personalizada y controla cuándo se muestra el protector de la cámara. > 

Para ver la configuración actual, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](device-restrictions-android-for-work.md#dedicated-device-settings).

Se aplica a:  
- Dispositivos Android Enterprise dedicados

### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215----"></a>Nuevos perfiles de aplicación y configuración para dispositivos Android Enterprise totalmente administrados <!-- 3574215  -->
Mediante el uso de perfiles, podrá configurar las opciones que aplican la configuración de VPN, correo electrónico y Wi-Fi a los dispositivos administrados por completo de Android Enterprise. Podrá:
- Use perfiles de aplicación para implementar la configuración de correo electrónico de Outlook, gmail y Nine work.
- Use los perfiles de configuración de dispositivos para implementar la configuración de certificados raíz de confianza.
- Use los perfiles de configuración de dispositivos para implementar la configuración de VPN y Wi-Fi.

Los usuarios se autenticarán con su nombre de usuario y contraseña para los perfiles de VPN, Wi-Fi y correo electrónico. Actualmente, la autenticación basada en certificados no está disponible. 

Se aplica a:  
- Android Enterprise totalmente administrado

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Compatibilidad con perfiles VPN de IKEv2 para iOS <!-- 1943438 -->
Va a poder crear perfiles VPN para el cliente VPN nativo de iOS mediante el protocolo IKEv2. IKEv2 es un nuevo tipo de conexión en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **VPN** para tipo de perfil > **Configuración**.

Estos perfiles VPN configuran el cliente VPN nativo. Por lo tanto, ninguna aplicación cliente VPN se instala ni se inserta en dispositivos administrados. Esta característica exige que los dispositivos estén inscritos en Intune (inscripción de MDM).

Para ver la configuración VPN actual que puede establecer, vaya a [Configuración de VPN en dispositivos iOS en Microsoft Intune](vpn-settings-ios.md).

Se aplica a iOS.

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscripción de dispositivos

### <a name="skip-more-screens-in-setup-assistant---4877451---"></a>Omitir más pantallas en el Asistente de configuración <!--4877451 -->
Podrá establecer perfiles de Programa de inscripción de dispositivos para omitir las siguientes pantallas del asistente de configuración: 
- Tiempo de pantalla
- Configuración de Touch ID

Para ello, vaya a **inscripción** > de dispositivos inscripción de**Apple** > tokens del**programa de inscripción** > Elija un token > **perfiles** > elegir un perfil > **propiedades** > **Editar.** junto a **Personalización del asistente**para la instalación.
Para obtener más información sobre la personalización del Asistente para la configuración, consulte [creación de un perfil de inscripción de Apple ](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile).

### <a name="android-enrollment-device-administrator-support----4869749----"></a>Compatibilidad con el administrador de dispositivos de inscripción de Android <!-- 4869749  -->
La opción de inscripción del administrador de dispositivos Android se agregará a la página  > de inscripción de Android (inscripción de**dispositivos** > de **Intune** inscripción de**Android**). El administrador de dispositivos Android seguirá estando habilitado de forma predeterminada para todos los inquilinos.  

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Para dispositivos iOS, personalice la pantalla de privacidad del proceso de inscripción del Portal de empresa <!-- 4394993  -->
Con Markdown, podrá personalizar la pantalla de privacidad del Portal de empresa que los usuarios finales ven durante la inscripción de iOS. En concreto, podrá personalizar la lista de elementos que su organización no puede ver o realizar en el dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Administración de dispositivos

### <a name="build-number-included-on-android-device-hardware-page----4461910----"></a>Número de compilación incluido en la página hardware de dispositivo Android <!-- 4461910  -->
Una nueva entrada en la página de hardware de cada dispositivo Android incluirá el número de compilación del sistema operativo del dispositivo.

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurar el límite de tiempo de limpieza automática de dispositivos en 30 días <!--4231059  -->
Podrá establecer el límite de tiempo de limpieza automática del dispositivo en un plazo de 30 días (en lugar de en el límite actual de 90 días) después del último inicio de sesión. Para ello, vaya a **Intune** > **configuración** > de**dispositivos** > **limpiar reglas**.

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Control de acceso basado en roles

### <a name="default-scope-tag----3702875---"></a>Etiqueta de ámbito predeterminada <!-- 3702875 -->
Habrá disponible una nueva etiqueta de ámbito predeterminada integrada. Todos los objetos de Intune no etiquetados que admiten etiquetas de ámbito se asignarán automáticamente a la etiqueta de ámbito predeterminada. La etiqueta de ámbito **predeterminada** se agregará a todas las asignaciones de roles existentes para mantener la paridad con la experiencia de administración hoy mismo. Si no desea que un administrador vea los objetos de Intune con etiquetas de ámbito predeterminadas, quite la etiqueta de ámbito predeterminada de la asignación de roles. Esta característica es similar a la característica de ámbitos de seguridad en System Center Configuration Manager.

<!-- ***********************************************-->
## <a name="security"></a>Seguridad

### <a name="import-and-export-security-baselines------3408610------------"></a>Importar y exportar líneas base de seguridad    <!--3408610          -->  
Estamos agregando la capacidad de exportar e importar líneas de base de seguridad. Esta característica le permitirá realizar sus personalizaciones y compartirlas entre entornos de Intune.

<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.




