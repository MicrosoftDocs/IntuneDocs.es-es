---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b96fa9fac25f6de4180d3dcc9ee4022a2cc43fe
ms.sourcegitcommit: 7484ef8006f6b81d8976c328dd704512a31872ec
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70190251"
---
# <a name="in-development-for-microsoft-intune---september-2019"></a>En desarrollo para Microsoft Intune: septiembre de 2019

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

### <a name="managed-google-play-private-lob-apps----1464182----"></a>Aplicaciones de LOB privadas Google Play administradas <!-- 1464182  -->
Intune permitirá a los administradores de TI publicar aplicaciones LOB de Android privadas en Google Play administrados a través de un iframe incrustado en la consola de Intune.  Actualmente, los administradores de TI necesitan publicar aplicaciones LOB directamente en la consola de publicación de reproducción de Google, lo que requiere muchos pasos y lleva mucho tiempo.  Esta nueva característica permite publicar fácilmente aplicaciones LOB con un conjunto mínimo de pasos sin necesidad de salir de la consola de Intune.  Cualquiera de los escenarios de administración empresarial de Android que usan Google Play administrados puede aprovechar esta característica (Perfil de trabajo, dispositivos dedicados, totalmente administrados y no inscritos).  En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. A continuación, seleccione **Google Play administrados** en la lista **tipo de aplicación** . Para obtener más información sobre las aplicaciones de Google Play administradas, consulte [agregar aplicaciones de Google Play administradas a dispositivos empresariales Android con Intune](apps-add-android-for-work.md).

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Portal de empresa mensajes de estado de instalación de aplicaciones <!-- 2514416  -->
La aplicación Portal de empresa mostrará mensajes de estado de instalación de aplicaciones adicionales a los usuarios finales. Las condiciones siguientes se aplicarán a las nuevas características de dependencia de Win32:
- No se pudo instalar la aplicación. No se cumplieron las dependencias definidas por el administrador.
- La aplicación se instaló correctamente, pero requiere un reinicio.
- La aplicación está en proceso de instalación, pero requiere un reinicio para continuar.

### <a name="managed-google-play-iframe-support----2871756----"></a>Compatibilidad con Google Play de iframe administrado <!-- 2871756  -->
Intune proporcionará compatibilidad para agregar y administrar vínculos Web directamente en la consola de Intune, a través del iframe de Google Play administrado.  Esto permite a los administradores de ti enviar una dirección URL y un gráfico de iconos y, a continuación, implementar esos vínculos en dispositivos como aplicaciones Android normales. Cualquiera de los escenarios de administración empresarial de Android que usan Google Play administrados puede aprovechar esta característica (Perfil de trabajo, dispositivos dedicados, totalmente administrados y no inscritos).  En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. A continuación, seleccione **Google Play administrados** en la lista **tipo de aplicación** . Para obtener más información sobre las aplicaciones de Google Play administradas, consulte [agregar aplicaciones de Google Play administradas a dispositivos empresariales Android con Intune](apps-add-android-for-work.md).

### <a name="macos-support-for-vpp-apps----3173501----"></a>compatibilidad de macOS con las aplicaciones de PCV <!-- 3173501  -->
las aplicaciones de macOS que haya adquirido con Apple Business Manager se mostrarán en la consola de cuando se sincronicen los tokens de PCV de Apple en Intune. Puede asignar, revocar y reasignar licencias basadas en el dispositivo y en el usuario para grupos mediante la consola de. Microsoft Intune le ayuda a administrar las aplicaciones de PCV compradas para su uso en su empresa:
- Informes sobre la información de licencia desde la tienda de aplicaciones.
- Realizando un seguimiento de cuántas licencias ha usado.
- Le ayudamos a no instalar más copias de la aplicación que las que tiene.
Para más información, consulte [Administración de aplicaciones y libros comprados por volumen con Microsoft Intune](vpp-apps.md).

### <a name="macos-support-for-web-apps----3174427----"></a>compatibilidad de macOS con Web Apps <!-- 3174427  -->
Podrá instalar Web Apps, que le permite agregar un acceso directo a una dirección URL en la web, con el Portal de empresa macOS. Los usuarios finales pueden tener acceso a la acción de **instalación** desde la página de detalles de la aplicación para una aplicación web en el portal de empresa MacOS. Para obtener más información sobre el tipo de aplicación de **vínculo Web** , consulte [agregar aplicaciones a Microsoft Intune](apps-add.md).

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Asignación de la versión beta de Microsoft Edge para macOS <!-- 4678761  -->
Podrá agregar y asignar la versión más reciente de Microsoft Edge beta a Intune para dispositivos macOS. En Intune, seleccione aplicaciones de **cliente** > **aplicaciones** > **Agregar aplicación** > **Microsoft Edge-MacOS**. A continuación, asigne la versión beta de Microsoft Edge a los grupos deseados. Microsoft AutoUpdate (MAU) mantiene Microsoft Edge actualizado. Para obtener más información sobre Microsoft Edge, consulte [Administración del acceso web con Microsoft Edge con Microsoft Intune](manage-microsoft-edge.md).

### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Operaciones de lectura y escritura Graph API para aplicaciones de Intune <!-- 5031704  -->
Las aplicaciones podrán llamar al Graph API de Intune con operaciones de lectura y escritura mediante la identidad de la aplicación sin credenciales de usuario. Para obtener más información sobre cómo obtener acceso a Microsoft Graph API para Intune, consulte [Trabajar con Intune en Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar el contenido de notificación de aplicación para las cuentas de la organización <!-- 2576686 -->
Las directivas de protección de aplicaciones (APP) de Intune en dispositivos iOS y Android le permitirán controlar el contenido de las notificaciones de la aplicación para las cuentas de la organización. Esta característica requerirá la compatibilidad de las aplicaciones y es posible que no esté disponible para todas las aplicaciones habilitadas para la aplicación. Consulte [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) para obtener más información sobre APP.

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Notificación de aplicaciones de Google Play disponibles para perfiles de trabajo de Android <!-- 3041956  -->
En las instalaciones de aplicaciones disponibles en dispositivos de perfil de trabajo de Android, puede ver el estado de instalación de la aplicación y la versión instalada de aplicaciones administradas de Google Play. Para obtener más información, vea [Supervisión de las directivas de protección de aplicaciones](app-protection-policies-monitor.md), [Administrar dispositivos de perfil de trabajo Android con Intune](android-enterprise-overview.md) y [Tipo de aplicación de Google Play administrado](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración de los dispositivos

### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161----"></a>Las características del dispositivo, las restricciones de dispositivos y los perfiles de extensión de la configuración de iOS y macOS se muestran mediante el tipo de inscripción <!-- 4886161  -->

En Intune, puede crear perfiles para dispositivos iOS y MacOS (**perfiles** > de**configuración** > de dispositivos**crear perfil** > **iOS** o **MacOS** para plataformas > **características del dispositivo** , **Restricciones de dispositivos**o **extensiones** para el tipo de perfil). Actualmente, se muestra la configuración disponible en estos perfiles. 

En una actualización futura, la configuración disponible en el portal de Intune se clasificará por el tipo de inscripción al que se aplican:

- iOS
  - Todos los tipos de inscripción
  - Inscripción de dispositivos e inscripción de dispositivos automatizada
  - Inscripción de dispositivo automatizada

- macOS
  - Todos los tipos de inscripción
  - Inscripción de dispositivos
  - Inscripción de dispositivos aprobados por el usuario y automatizada
  - Inscripción de dispositivo automatizada

Se aplica a:

- iOS
  - [Características del dispositivo](ios-device-features-settings.md)
  - [Restricciones de dispositivos](device-restrictions-ios.md)

- macOS
  - [Características del dispositivo](macos-device-features-settings.md)
  - [Restricciones de dispositivos](device-restrictions-macos.md)
  - [Extensiones](kernel-extensions-settings-macos.md)

### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835----"></a>Nueva configuración de control de voz para dispositivos iOS supervisados que se ejecutan en pantalla completa <!-- 4892835  -->

En Intune, puede crear directivas para ejecutar dispositivos iOS supervisados como un quiosco o un dispositivo dedicado (**perfiles** > de**configuración** > de dispositivo**crear perfil** > **iOS** para plataforma >  **Restricciones de dispositivos** para el tipo de perfil > **quiosco (solo supervisado)** ). 

En una actualización futura, habrá nuevas opciones de configuración que puede controlar:

- **Control de voz**: habilita el control de voz en el dispositivo mientras está en el modo de pantalla completa.
- **Modificación del control de voz**: permite a los usuarios cambiar la configuración de control de voz en el dispositivo en modo de pantalla completa.

Para ver la configuración actual, vaya a [configuración de pantalla completa de iOS (solo supervisado)](device-restrictions-ios.md#kiosk-supervised-only).

Se aplica a:

- iOS 13.0 y versiones posteriores

### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175----"></a>Uso del inicio de sesión único para aplicaciones y sitios web en los dispositivos iOS y macOS <!-- 4893175  -->
En una actualización futura, habrá algunas nuevas opciones de inicio de sesión único para dispositivos iOS y MacOS (**perfiles** > de**configuración** > de dispositivo**crear perfil** > **iOS** o **MacOS** para Plataforma > **características de dispositivo** para el tipo de perfil).

Use estas opciones para configurar una experiencia de inicio de sesión único, especialmente para aplicaciones y sitios web que usan la autenticación Kerberos. Puede elegir entre una extensión de aplicación de inicio de sesión único de credencial genérica y la extensión integrada de Kerberos de Apple.

Para ver las características de dispositivo actuales que puede configurar, vaya a [características de dispositivos iOS](ios-device-features-settings.md) y [características de dispositivos MacOS](macos-device-features-settings.md).

Se aplica a:

- iOS 13.0 y versiones más recientes
- macOS 10.15 y versiones más recientes

### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079----"></a>Asociación de dominios a aplicaciones en dispositivos macOS 10.15 + <!-- 4898079  -->
En los dispositivos MacOS, puede configurar diferentes características e introducir estas características en los dispositivos con una directiva (**perfiles** > de**configuración** > de dispositivos**crear perfil** > **MacOS** para Plataforma > **características de dispositivo** para el tipo de perfil). En una actualización futura, podrá asociar dominios a sus aplicaciones. Esta característica ayuda a compartir credenciales con sitios web relacionados con la aplicación y se puede usar con la extensión de inicio de sesión único de Apple, vínculos universales y Autorrellenar de contraseñas. 

Para ver las características actuales que puede configurar, vaya a [configuración de características de dispositivos MacOS en Intune](macos-device-features-settings.md).

Se aplica a:

- macOS 10.15 y versiones más recientes

### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474----"></a>Usar "iTunes" y "apps" en la dirección URL de la tienda de aplicaciones de iTunes al mostrar u ocultar aplicaciones en dispositivos iOS supervisados <!-- 4928474  --> 
En Intune, puede crear directivas para mostrar u ocultar aplicaciones en los dispositivos iOS supervisados (**perfiles** > de**configuración** > de dispositivo**crear perfil** > **iOS** para plataforma > **dispositivo restricciones** para el tipo de perfil > **Mostrar u ocultar aplicaciones (solo supervisado)** ). 

Puede escribir la dirección URL de la tienda de aplicaciones de iTunes `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`, como. En una actualización futura, podrá usar `apps` y `itunes` en la dirección URL, como:

- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Para obtener más información sobre esta configuración, vea [Mostrar u ocultar aplicaciones (solo supervisado)](device-restrictions-ios.md#show-or-hide-apps-supervised-only).

Se aplica a:

- iOS

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Compatibilidad con perfiles VPN de IKEv2 para iOS <!-- 1943438 -->
Va a poder crear perfiles VPN para el cliente VPN nativo de iOS mediante el protocolo IKEv2. IKEv2 es un nuevo tipo de conexión en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **VPN** para tipo de perfil > **Configuración**.

Estos perfiles VPN configuran el cliente VPN nativo. Por lo tanto, ninguna aplicación cliente VPN se instala ni se inserta en dispositivos administrados. Esta característica exige que los dispositivos estén inscritos en Intune (inscripción de MDM).

Para ver la configuración VPN actual que puede establecer, vaya a [Configuración de VPN en dispositivos iOS en Microsoft Intune](vpn-settings-ios.md).

Se aplica a iOS.


<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscripción de dispositivos

### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790----"></a>Los nuevos inquilinos desaparecerán de forma predeterminada administración de administradores de dispositivos Android <!-- 4869790  -->
Las funcionalidades de administrador de dispositivos de Android se han sustituido por Android Enterprise. Por lo tanto, se recomienda usar Android Enterprise para nuevas inscripciones en su lugar. En una actualización futura, los nuevos inquilinos deberán completar los siguientes pasos de requisitos previos de la inscripción de Android para usar la administración de **administrador** >  de dispositivos: ir a Intune**inscripción** > de dispositivos**inscripción de Android** >  Los dispositivos **personales y corporativos con privilegios** > de administración de dispositivos**usan el administrador de dispositivos para administrar los dispositivos**.

Los inquilinos existentes no experimentarán ningún cambio en sus entornos. 

Para obtener más información sobre el administrador de dispositivos Android en Intune, consulte [inscripción de administrador de dispositivos Android](https://docs.microsoft.com/intune/android-enroll-device-administrator).

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Para dispositivos iOS, personalice la pantalla de privacidad del proceso de inscripción del Portal de empresa <!-- 4394993  -->
Con Markdown, podrá personalizar la pantalla de privacidad del Portal de empresa que los usuarios finales ven durante la inscripción de iOS. En concreto, podrá personalizar la lista de elementos que su organización no puede ver o realizar en el dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Administración de dispositivos

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Implementar actualizaciones de software en dispositivos macOS <!-- 3194876 -->
Podrá implementar actualizaciones de software en grupos de dispositivos macOS. Esta característica incluye el archivo crítico, el firmware, el archivo de configuración y otras actualizaciones. Podrá enviar actualizaciones en la siguiente protección del dispositivo o seleccionar una programación semanal para implementar actualizaciones dentro o fuera de las ventanas que establezca. Esto le ayuda a actualizar dispositivos fuera de las horas de trabajo estándar o cuando el Departamento de soporte técnico está totalmente personal. También obtendrá un informe detallado de todos los dispositivos macOS con actualizaciones implementadas. Puede profundizar en el informe en función de cada dispositivo para ver los Estados de las actualizaciones determinadas.

### <a name="send-custom-notifications-to-a-device----4928910----"></a>Envío de notificaciones personalizadas a un dispositivo <!-- 4928910  -->
Podrá enviar notificaciones personalizadas a dispositivos específicos que tengan instalada la aplicación Portal de empresa o Intune. Para ello, vaya a **Intune** > **dispositivos** > **todos los dispositivos** > Elija un dispositivo > **más** > **Enviar notificación personalizada**. 

### <a name="updates-to-android-enterprise-fully-managed-features----3464667-5227935-4062195-4631425-4631440---"></a>Actualizaciones de características de Android Enterprise totalmente administradas <!-- 3464667, 5227935, 4062195, 4631425, 4631440 -->

Agregaremos la siguiente compatibilidad para dispositivos Android totalmente administrados:

- Los certificados SCEP para Android totalmente administrado estarán disponibles para la autenticación de certificados en los dispositivos administrados como propietario del dispositivo. Los certificados SCEP ya se admiten en los dispositivos de Perfil de trabajo.  Con los certificados SCEP para el propietario del dispositivo, podrá: <!-- 5227935 -->
    - crear un perfil de SCEP en la sección DO de Android Enterprise
    - vinculación de certificados SCEP para el perfil de Wi-Fi para la autenticación
    - vinculación de certificados SCEP para realizar perfiles de VPN para la autenticación
    - vinculación de certificados SCEP a perfiles de correo electrónico para la autenticación (a través de AppConfig)
- Las aplicaciones del sistema se admitirán en dispositivos empresariales Android. En Intune, agregará una aplicación de sistema de Android Enterprise seleccionando aplicaciones de **cliente** > **Aplicaciones** > **Agregar**. En la lista **tipo de aplicación** , seleccione aplicación de **sistema empresarial Android**. Para obtener más información sobre agregar aplicaciones en Intune, vea [Incorporación de aplicaciones a Microsoft Intune](apps-add.md). <!-- 4062195 -->
- En **cumplimiento** > de dispositivos, el**propietario del dispositivo** **Android Enterprise** > , podrá crear una directiva de cumplimiento que establezca el nivel de atestación de Google SafetyNet.   <!-- 4631425 -->
- En dispositivos Android Enterprise totalmente administrados, se admitirán los proveedores de Mobile Threat Defense. En **cumplimiento** > de dispositivos, el**propietario del dispositivo** **Android Enterprise** > , puede elegir un nivel de amenaza aceptable. <!-- 4631440 --> En [Configuración de Android Enterprise para marcar dispositivos como compatibles o no compatibles con Intune](compliance-policy-create-android-for-work.md#device-owner) se muestra la configuración actual.


Se aplica a: 
- Dispositivos totalmente administrados de Android Enterprise

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

### <a name="updated-support-experience-------5012398------"></a>Experiencia de soporte actualizada   <!--  5012398    -->
Como parte de las mejoras continuas, actualizaremos la experiencia de soporte técnico en la consola de Intune.  Vamos a mejorar la búsqueda en la consola y los comentarios de los problemas comunes y a optimizar el flujo de trabajo para ponerse en contacto con el soporte técnico.     

<!-- ***********************************************-->
## <a name="security"></a>Seguridad

### <a name="tamper-protection-for-windows-defender-antivirus-----4705448---------"></a>Protección contra alteraciones para antivirus de Windows Defender  <!-- 4705448       -->
Agregaremos *protección contra manipulaciones* a la configuración que Intune puede administrar para el antivirus de Windows Defender. Podrá usar un perfil de configuración de dispositivo para Windows 10 Endpoint Protection para activar o desactivar la protección contra alteraciones.  Para obtener más información acerca de la protección contra alteraciones, consulte [impedir cambios de configuración de seguridad con la protección contra manipulaciones](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) en la documentación de Windows. 


<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.




