---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e099537bce6327e9a8991bc42f406e4abd3dfd2e
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260238"
---
# <a name="in-development-for-microsoft-intune---march-2020"></a>En desarrollo para Microsoft Intune: marzo de 2020

Para ayudarle con la preparación y planeación, en esta página se enumeran las actualizaciones y características de la interfaz de usuario de Intune que están en desarrollo, pero que aún no se han publicado. Además de la información de esta página: 

- Si prevemos que tendrá que tomar medidas antes de realizar un cambio, haremos una publicación complementaria en el Centro de mensajes de Office.
- Cuando una característica entra en producción, ya sea una versión preliminar o disponible con carácter general, la descripción de la característica pasa de esta página a [Novedades](whats-new.md).
- Esta página y la página [Novedades](whats-new.md) se actualizan periódicamente. Compruebe si hay actualizaciones adicionales.
- Consulte el [plan de desarrollo de Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para conocer los plazos de tiempo y los productos estratégicos.

> [!NOTE]
> Esta página refleja las expectativas actuales sobre las capacidades de Intune en una versión futura. Las fechas y las características individuales pueden cambiar. En esta página no se describen todas las características en desarrollo.

**Fuente RSS**: para recibir notificaciones cuando esta página se actualice, copie y pegue la dirección URL siguiente en el lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Administración de aplicaciones

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Cambio del destino de clips web a Microsoft Edge en dispositivos iOS/iPadOS<!-- 5455276 -->
Los clips web, que actúan como aplicaciones web ancladas en dispositivos iOS/iPadOS, deberán actualizarse. Los clips web recién implementados se van a abrir en Microsoft Edge en lugar de en Intune Managed Browser si tienen que abrirse en un explorador protegido. Debe cambiar el destino de los clips web existentes para asegurarse de que se abran en Microsoft Edge en lugar de en Managed Browser.

### <a name="macos-and-ios-company-portal-updates---5779439-5780234----"></a>Actualizaciones del Portal de empresa de iOS y macOS<!-- 5779439, 5780234  -->
El panel Perfil del Portal de empresa en macOS e iOS se actualizará para incluir el botón Cerrar sesión. Además, esta actualización incluirá mejoras de la interfaz de usuario en el panel Perfil en el Portal de empresa para macOS. Para más información sobre Portal de empresa, vea [Configuración de la aplicación Portal de empresa de Microsoft Intune](~/apps/company-portal-app.md).

### <a name="updates-to-branding-and-customization-pane---5236032---"></a>Actualizaciones del panel Personalización de marca y personalización<!-- 5236032 -->
Se va a actualizar el panel de Intune que actualmente se denomina "Personalización de marca y personalización" con mejoras, como las siguientes:

- Se va a cambiar el nombre del panel a **Personalización**.
- Se va a mejorar la organización y el diseño de las opciones.
- Se va a mejorar el texto y la información sobre herramientas de las opciones.

Para encontrar estas opciones en Intune, vaya al [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) y, seleccione **Administración de inquilinos** > **Personalización**. Para obtener información sobre la personalización existente, vea [Configuración de la aplicación Portal de empresa de Microsoft Intune](~/apps/company-portal-app.md).

### <a name="configure-the-ios-microsoft-azure-ad-sso-app-extension---567534----"></a>Configuración de la extensión de aplicación de inicio de sesión único de Microsoft Azure AD en iOS<!-- 567534  -->
El equipo de Microsoft Azure AD va a desarrollar una extensión de aplicación de inicio de sesión único (SSO) de redireccionamiento que permite a los usuarios de iOS e iPadOS 13.0+ obtener acceso sin problemas a aplicaciones y sitios web de Microsoft con un inicio de sesión. Cuando se publique la extensión de aplicación de SSO de AAD, podrá configurar la extensión de SSO con el perfil **Características del dispositivo** > **Extensión de aplicación de inicio de sesión único** en la consola de administración con tan solo unos clics. 

Para obtener más información sobre las extensiones de aplicación de SSO de iOS o cómo configurar las características del dispositivo, vea [Extensión de aplicación de inicio de sesión único](~/configuration/device-features-configure.md#single-sign-on-app-extension).

### <a name="company-portal-for-ios-to-support-landscape-mode--6048329----"></a>Modo horizontal admitido en Portal de empresa para iOS<!--6048329  -->
Los usuarios podrán inscribir sus dispositivos, buscar aplicaciones y obtener soporte técnico de TI con la orientación de pantalla que prefieran. La aplicación detectará y ajustará automáticamente las pantallas para ajustarse al modo horizontal o vertical, a menos que los usuarios bloqueen la pantalla en modo vertical. 

### <a name="configure-if-enrollment-is-available-in-company-portal-for-android-and-ios---4260128-idready-idstaged---"></a>Configuración de la disponibilidad de la inscripción en Portal de empresa para iOS y Android<!-- 4260128 idready idstaged -->
Habrá una nueva opción disponible para configurar si la inscripción de dispositivos en el Portal de empresa en dispositivos iOS y Android está disponible con mensajes, sin mensajes o no está disponible para los usuarios. Para encontrar estas opciones en Intune, vaya al [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) y, seleccione **Administración de inquilinos** > **Personalización** > **Editar** > **Inscripción de dispositivos**. Para obtener más información sobre la personalización existente del Portal de empresa, vea [Configuración de la aplicación Portal de empresa de Microsoft Intune](~/apps/company-portal-app.md).

### <a name="improved-sign-in-experience-in-company-portal-for-android---6103997----"></a>Experiencia de inicio de sesión mejorada en la aplicación Portal de empresa para Android<!-- 6103997  -->
Se va a actualizar el diseño de varias pantallas de inicio de sesión en la aplicación Portal de empresa para Android a fin de que la experiencia sea más moderna, sencilla y limpia para los usuarios.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración del dispositivo

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Perfiles de configuración de dispositivos de red cableada para dispositivos macOS<!-- 3508686  -->
Se va a publicar un nuevo perfil de configuración de dispositivo macOS que configura redes cableadas (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **macOS** para plataforma > **Red cableada** para tipo de perfil). Use esta característica para crear perfiles de 802.1x con el fin de administrar redes cableadas e implementarlas en los dispositivos macOS.

Se aplica a:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932----"></a>Uso permanente de Always On por parte de los perfiles de VPN con conexiones VPN IKEv2 con dispositivos iOS/iPadOS <!-- 1947932  -->
En dispositivos iOS/iPadOS, puede crear un perfil de VPN que use una conexión IKEv2 (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS/iPadOS** para plataforma > **VPN** para tipo de perfil). En una actualización futura, puede configurar Always On con IKEv2. Cuando los perfiles de VPN IKEv2 están configurados, se conectan automáticamente y permanecen conectados (o se vuelven a conectar rápidamente) a la VPN. Permanecen conectados incluso al moverse entre redes o al reiniciar dispositivos.

En iOS/iPadOS, la VPN de Always On está limitada a perfiles de IKEv2.

Para ver la configuración IKEv2 actual que puede establecer, vaya a [Incorporación de VPN en dispositivos iOS/iPadOS en Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Se aplica a:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984----"></a>Experiencia de interfaz de usuario mejorada al crear perfiles de configuración en dispositivos iOS/iPadOS y macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984  -->
Cuando se crea un perfil para dispositivos iOS/iPadOS o macOS, se actualiza la experiencia en el Centro de administración de Endpoint Manager. Este cambio afecta a los siguientes perfiles de configuración de dispositivos (**Dispositivos** > **Perfiles de configuración** > **Crear perfil** > **iOS** o **macOS** para plataforma):

- Personalizado: iOS/iPadOS y macOS
- Características del dispositivo: iOS/iPadOS y macOS
- Restricciones de dispositivos: iOS/iPadOS y macOS
- Endpoint Protection: macOS
- Extensiones: macOS
- Archivo de preferencias: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-----"></a>Experiencia de interfaz de usuario mejorada al crear perfiles de configuración de OEMConfig en dispositivos Android Enterprise<!-- 5568645   -->
Al crear o editar un perfil de OEMConfig para dispositivos Android Enterprise, se actualiza la experiencia en el Centro de administración del Administrador de puntos de conexión. La experiencia actualizada proporciona un resumen de los valores que se han configurado de un vistazo. Este cambio afecta al perfil de configuración del dispositivo de OEMConfig (**Dispositivos** > **Perfiles de configuración** > **Crear perfil** > **Android Enterprise** para plataforma > **OEMConfig** para tipo de perfil).

Esta característica se aplica a:
- Android Enterprise 

### <a name="enterprise-app-trust-settings-modification-setting-will-be-removed-from-iosipados-device-restriction-profiles---6225131----"></a>La opción de modificación de la configuración de confianza de aplicaciones empresariales se quitará de los perfiles de restricción de dispositivos iOS/iPadOS<!-- 6225131  -->
En los dispositivos iOS/iPadOS puede crear un perfil de restricciones de dispositivo (**Dispositivos** > **Perfiles de configuración** > **Crear perfil** > **iOS/iPadOS** para la plataforma > **Restricciones de dispositivos** para el tipo de perfil). Apple quitará la opción **Modificación de la configuración de confianza de aplicaciones empresariales** y se quitará de Intune. Si en la actualidad usa esta opción en un perfil, no tiene ningún impacto y permanecerá en el perfil hasta que cree uno. Esta opción también se quitará de los informes en Intune.

Se aplica a:
- iOS/iPadOS

Para ver los valores que puede restringir, vaya a [Configuración de dispositivos iOS e iPadOS para permitir o restringir características](../configuration/device-restrictions-ios.md).

### <a name="device-configuration-profile-settings-and-values-will-be-updated-for-windows-platforms---4091122---"></a>Las opciones y valores de los perfiles de configuración de dispositivos se actualizarán para las plataformas Windows<!-- 4091122 -->
Al crear perfiles de configuración de dispositivos para plataformas Windows (**Dispositivos** > **Perfiles de configuración** >  **Crear perfil** > cualquier opción **Windows** para la plataforma), algunas opciones y sus valores son diferentes del CSP y pueden ser confusos. Los nombres de las opciones y sus valores se actualizarán para que sean más claros.

Se aplica a:

- Perfiles de configuración de dispositivos Windows 10 y versiones posteriores
- Perfiles de configuración de dispositivos Windows Holographic for Business
- Perfiles de configuración de dispositivos Windows 8.1
- Perfiles de configuración de dispositivos Windows Phone 8.1

### <a name="improved-user-interface-experience-when-creating-device-restrictions-profiles-on-android-and-android-enterprise-devices---5841361---"></a>Experiencia de interfaz de usuario mejorada al crear perfiles de restricciones de dispositivo en dispositivos Android y Android Enterprise<!-- 5841361 -->
Al crear un perfil para dispositivos Android o Android Enterprise, se actualizará la experiencia en el Centro de administración del Administrador de puntos de conexión. Este cambio afecta a los perfiles de configuración de dispositivo siguientes (**Dispositivos** > **Perfiles de configuración** > **Crear perfil** > **Administrador de dispositivos Android** o **Android Enterprise** para la plataforma):

- Restricciones de dispositivos: Administrador de dispositivos Android
- Restricciones de dispositivos: Propietario del dispositivo Android Enterprise
- Restricciones de dispositivos: Perfil de trabajo de Android Enterprise

Para obtener más información sobre las restricciones de dispositivos que se pueden configurar, vea [Administrador de dispositivos Android](../configuration/device-restrictions-android.md) y [Android Enterprise](../configuration/device-restrictions-android-for-work.md).

### <a name="delete-bundles-and-bundle-arrays-in-oemconfig-device-configuration-profiles-on-android-enterprise-devices---5550355----"></a>Eliminación de agrupaciones y matrices de agrupaciones en perfiles de configuración de dispositivos OEMConfig en dispositivos Android Enterprise<!-- 5550355  -->
En dispositivos Android Enterprise, puede crear y actualizar perfiles de OEMConfig. Los usuarios podrán eliminar agrupaciones y matrices de agrupaciones mediante el **Diseñador de configuraciones** de Intune.

Para obtener más información sobre los perfiles OEMConfig, vea [Uso y administración de dispositivos Android Enterprise con OEMConfig en Microsoft Intune](../configuration/android-oem-configuration-overview.md).

Esta característica se aplica a:
- Android Enterprise

### <a name="support-for-wpa-and-wpa2-in-ios-enterprise-wi-fi-profiles--6215273-----"></a>Compatibilidad con WPA y WPA2 en perfiles de Wi-Fi Empresarial de iOS<!--6215273   -->
Se va a agregar el campo *Tipo de seguridad* al [Perfil de Wi-Fi Empresarial para iOS](../configuration/wi-fi-settings-ios.md) (**Dispositivos** > **Perfiles de configuración** > **Crear perfil** y seleccione **iOS/iPadOS** para *Plataforma* y, después **Wi-Fi** para *Perfil*). Esto es similar a las opciones disponibles para un perfil de Wi-Fi Básico para iOS. Con este cambio podrá crear perfiles que especifiquen un tipo de seguridad **WPA-Enterprise** o **WPA/WPA2-Enterprise** y, después, especificar una selección para *Tipo de EAP*.

### <a name="new-user-experience-for-certificate-email-vpn-and-wi-fi-profiles---5615208-----"></a>Nueva experiencia de usuario para perfiles de certificado, correo electrónico, VPN y Wi-Fi<!-- 5615208   -->
Se va a actualizar la [experiencia del usuario](../configuration/device-profile-create.md) en el Centro de administración del Administrador de puntos de conexión (**Dispositivos** > **Perfiles de configuración** > **Crear perfil**) para crear y modificar los siguientes tipos de perfil. La nueva experiencia presentará las mismas opciones que antes, pero usa una experiencia similar a un asistente que no requiere tanto desplazamiento horizontal. Con la nueva experiencia no tendrá que modificar las configuraciones existentes.
- Credencial derivada
- Correo electrónico
- Certificado PKCS
- Certificado PKCS importado
- Certificado SCEP
- Certificado de confianza
- VPN
- Wi-Fi

(**Dispositivos** > **Perfiles de configuración** > **Crear perfil** y, después, para *Tipo de perfil* seleccione cualquiera de los perfiles anteriores).

### <a name="configure-the-microsoft-defender-atp-app-for-macos-----5520115----"></a>Configuración de la aplicación ATP de Microsoft Defender para macOS  <!-- 5520115  -->
Pronto podrá configurar las [opciones](../protect/endpoint-protection-macos.md) para la aplicación ATP de Microsoft Defender para dispositivos que ejecuten macOS como parte de un perfil de configuración de dispositivo de protección de puntos de conexión (**Dispositivos** > **Perfiles de configuración** > **Crear perfil**, seleccione **macOS** para *Plataforma* y, después, **Endpoint Protection** para el *Tipo de perfil*). Habrá ocho opciones para la configuración de dispositivos macOS. 

ATP de Microsoft Defender es compatible con macOS 10.13 (High Sierra) y versiones posteriores, y la aplicación [ATP de Microsoft Defender](../apps/apps-advanced-threat-protection-macos.md) se debe implementar en el dispositivo *después* de aplicar esta opción. Las opciones se deben enviar al dispositivo antes de que se implemente la aplicación. No se admiten las versiones beta de macOS.

### <a name="new-filevault-setting-for-macos-endpoint-protection-device-configuration-policy---5459801-----"></a>Nueva configuración de FileVault para la directiva de configuración de dispositivos Endpoint Protection de macOS<!-- 5459801   -->
Se va a agregar una opción nueva a la categoría FileVault dentro de la plantilla [Endpoint Protection de macOS](../protect/endpoint-protection-macos.md): Ocultar clave de recuperación. (**Dispositivos** > **Perfiles de configuración** > **Crear perfil**, seleccione **macOS** para la *Plataforma* y, después, **Endpoint Protection** para el *Tipo de perfil*). Esta opción oculta la clave personal del usuario final durante el cifrado de FileVault 2. Un usuario del dispositivo puede ver su clave de recuperación personal en cualquier momento desde la aplicación Portal de empresa de iOS o desde el sitio web del Portal de empresa para el dispositivo macOS cifrado. Para ver la clave de recuperación personal, puede ir a los detalles del dispositivo y hacer clic en *Obtener clave de recuperación*.

Esta opción no estará disponible en una directiva creada anteriormente. Tendrá que volver a crear las directivas de FileVault para configurar esta opción y poder usarla. 

###  <a name="ui-update-when-configuring-compliance-policy----3961639----"></a>Actualización de la interfaz de usuario al configurar la directiva de cumplimiento <!-- 3961639  -->
Se va a actualizar la interfaz de usuario para configurar directivas de cumplimiento en el Administrador de puntos de conexión de Microsoft (**Dispositivos** > **Directivas de cumplimiento** > **Directivas** > **Crear directiva**). Verá una nueva experiencia de usuario que proporciona la misma configuración y los mismos detalles que ha usado antes. La nueva experiencia seguirá un proceso similar a un asistente para crear una directiva de cumplimiento e incluirá la página en la que puede agregar *Asignaciones* a la directiva y, después, una página *Resumen* en la que puede revisar la configuración antes de crear la directiva. 

### <a name="configure-delivery-optimization-agent-when-downloading-win32-app-content---5410945----"></a>Configuración del agente de optimización de entrega al descargar contenido de aplicaciones Win32<!-- 5410945  -->
Podrá configurar el agente de optimización de entrega para descargar contenido de aplicaciones Win32 en modo de segundo plano o de primer plano, en función de la asignación. En el caso de las aplicaciones Win32 existentes, el contenido se seguirá descargando en el modo de segundo plano. En el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**. Seleccione **Windows 10 y versiones posteriores** como **Plataforma**. En **Tipo de perfil**, seleccione **Optimización de entrega**. Para obtener más información sobre la Optimización de entrega, vea [Administración de aplicaciones Win32: Optimización de entrega](~/apps/apps-win32-app-management.md#delivery-optimization).


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Administración de dispositivos

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Cambio del usuario primario para dispositivos Windows <!-- 3794742 -->
Podrá cambiar el usuario primario para dispositivos híbridos de Windows y unidos a Azure AD. Para ello, vaya a **Intune** > **Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Propiedades** > **Usuario primario**. 

### <a name="new-android-report-on-android-devices-overview-page---5435435---"></a>Nuevo informe de Android en la página de información general de dispositivos Android<!-- 5435435 -->
Se va a agregar un informe a la consola de administración del Administrador de puntos de conexión de Microsoft en la página de información general de dispositivos Android, en la que se muestra el número de dispositivos Android inscritos en cada solución de administración de dispositivos. En este gráfico (como en el de la consola de Azure) se muestra la cantidad de dispositivos inscritos de perfil de trabajo, totalmente administrados, dedicados y de administrador de dispositivos. Para ver el informe, elija **Dispositivos** > **Android** > **Información general**.

### <a name="powershell-scripts-support-for-byod-devices---1862833----"></a>Compatibilidad de scripts de PowerShell con dispositivos BYOD<!-- 1862833  -->
Los scripts de PowerShell admitirán dispositivos registrados de Azure AD en Intune. Para más información sobre PowerShell, vea [Uso de scripts de PowerShell para dispositivos Windows 10 en Intune](~/apps/intune-management-extension.md). Esta funcionalidad no es compatible con dispositivos que ejecutan Windows 10 Home Edition.

### <a name="additional-data-warehouse-device-inventory-properties---6125732----"></a>Propiedades de inventario de dispositivos de almacenamiento de datos adicionales<!-- 6125732  -->
Las propiedades adicionales de inventario de dispositivos estarán disponibles mediante el Almacenamiento de datos de Intune. Las propiedades siguientes se expondrán a través de la colección de [dispositivos](~/developer/intune-data-warehouse-collections.md#devices):
- Capacidad de almacenamiento 
- Capacidad de memoria
- Versión de Office 365
- Modelo del dispositivo

Para obtener más información sobre el almacenamiento de datos, vea [API de Almacenamiento de datos de Microsoft Intune](~/developer/reports-nav-intune-data-warehouse.md).

### <a name="guide-users-from-android-device-administrator-management-to-work-profile-management--5857738--"></a>Guía para usuarios desde la administración de administradores de dispositivos Android a la administración de perfiles de trabajo<!--5857738-->
Se va a publicar una nueva opción de cumplimiento para la plataforma de administrador de dispositivos Android. Esta opción permite hacer que un dispositivo no sea compatible si se administra con el administrador de dispositivos.

En estos dispositivos no compatibles, en la página **Actualizar configuración del dispositivo**, los usuarios verán el mensaje **Mover a la nueva configuración de administración de dispositivos**. Si pulsan el botón **Resolver**, se les guiará por lo siguiente:

1. Anulación de la inscripción desde la administración de administradores de dispositivos
2. Inscripción en la administración de perfiles de trabajo
3. Resolución de problemas de cumplimiento 
 
En un esfuerzo por cambiar a la administración de dispositivos moderna, más completa y segura, Google va a reducir la compatibilidad con el administrador de dispositivos en las nuevas versiones de Android.  Intune solo puede proporcionar compatibilidad completa con dispositivos Android administrados por el administrador de dispositivos que ejecuten Android 10 y versiones posteriores hasta el segundo trimestre de 2020. Los dispositivos administrados por el administrador de dispositivos (menos Samsung) que ejecuten Android 10 o versiones posteriores después de este periodo ya no se podrán administrar de forma completa. En concreto, los dispositivos afectados no recibirán nuevos requisitos de contraseña. Para más información, vea este [Aviso](#decreasing-support-for-android-device-administrator).

### <a name="retire-noncompliant-devices---1827291---"></a>Retirar dispositivos no compatibles<!-- 1827291 -->
Se va a agregar una nueva acción de cumplimiento opcional para retirar un dispositivo no compatible (**Dispositivos** > **Directivas de cumplimiento** > **Directivas** > **Crear directiva** y, después, ver las *Acciones* disponibles en la página *Acciones en caso de incumplimiento*).  Al retirar un dispositivo no compatible, se quitan todos los datos de la empresa de él y también se quita el dispositivo de la administración de Intune. Esta acción se lleva a cabo cuando se alcanza el valor en días configurado. El valor mínimo es 30 días.  Se requerirá la aprobación explícita del administrador de TI para retirar los dispositivos mediante la sección *Retirada de los dispositivos no compatibles*, donde los administradores pueden retirar todos los dispositivos que cumplan los requisitos.

### <a name="new-information-in-device-details---5604099---"></a>Nueva información en los detalles del dispositivo<!-- 5604099 -->
La información siguiente estará en la página **Información general** de los dispositivos:
- Capacidad de almacenamiento (cantidad de almacenamiento físico en el dispositivo)
- Capacidad de memoria (cantidad de memoria física en el dispositivo)

### <a name="script-support-for-macos-devices---4280361----"></a>Compatibilidad con scripts para dispositivos macOS<!-- 4280361  -->
Podrá agregar e implementar scripts en dispositivos macOS. Esta compatibilidad amplía la capacidad de configurar dispositivos macOS más allá de lo que es posible con las funcionalidades de MDM nativas en dispositivos macOS. 

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
## <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

### <a name="help-and-support-workflow-update-to-support-additional-services---5654170---"></a>Actualización del flujo de trabajo de ayuda y soporte técnico para admitir servicios adicionales<!-- 5654170 -->
Se va a actualizar la página Ayuda y soporte técnico del Centro de administración del Administrador de puntos de conexión de Microsoft, para que pueda elegir el tipo de administración que usa, y ofrecer soporte técnico específico (**Solución de problemas + soporte técnico** >  **Ayuda y soporte técnico**). Con este cambio podrá seleccionar entre los tipos de administración siguientes:
- Configuration Manager (incluye Análisis de escritorio)
- Intune
- Administración conjunta

<!-- ***********************************************-->
<!--
## Role-based access control
-->

<!-- ***********************************************-->
## <a name="security"></a>Seguridad

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Compatibilidad con credenciales derivadas en dispositivos Android COBO<!--4839592-->
Se van a poder usar credenciales derivadas en dispositivos Android Enterprise totalmente administrados. Se va a incluir compatibilidad para recuperar una credencial derivada de Entrust Datacard, Intercede y DISA Purebred. Se va a poder usar una credencial derivada para la autenticación de aplicaciones, Wi-Fi, VPN o la firma o el cifrado S/MIME en las aplicaciones que lo admitan.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Uso de la directiva antivirus para administrar la configuración del antivirus de Microsoft Defender y la experiencia de Seguridad de Windows<!--6131401 -->
En el nodo *Seguridad del punto de conexión*, podrá configurar las opciones del **antivirus**. Al configurar la directiva del antivirus, definirá la configuración de los dispositivos Windows 10 a través de dos tipos de perfil:

- Antivirus de Microsoft Defender: administre la configuración de protección en la nube, exclusiones del antivirus, correcciones, opciones de análisis, etc.
- Experiencia de Seguridad de Windows: administre el modo en que los usuarios experimentan la configuración de Seguridad de Windows en sus dispositivos. Podrá configurar lo que pueden ver los usuarios finales en el centro de seguridad de Microsoft Defender y las notificaciones que reciben.

### <a name="users-personal-encrypted-recovery-key---6273943---"></a>Clave de recuperación cifrada personal del usuario<!-- 6273943 -->
Habrá una nueva característica de Intune disponible que permitirá a los usuarios recuperar su clave de recuperación de **FileVault** cifrada personal para dispositivos Mac a través de la aplicación Portal de empresa de Android o la aplicación de Intune de Android. Habrá un vínculo en la aplicación Portal de empresa y en la aplicación de Intune que abrirá un explorador Chrome en el Portal de empresa web, donde el usuario puede ver la clave de recuperación de **FileVault** necesaria para acceder a sus dispositivos Mac. Para obtener más información sobre el cifrado, vea [Uso del cifrado de dispositivos con Intune](~/protect/encrypt-devices.md).

### <a name="privacy-preferences-settings-for-macos-devices---2934232---"></a>Configuración de preferencias de privacidad para dispositivos macOS<!-- 2934232 --> 
Con el lanzamiento de macOS Catalina 10.15, Apple ha agregado nuevas mejoras de seguridad y privacidad. De forma predeterminada, las aplicaciones y los procesos no pueden acceder a datos específicos sin el consentimiento del usuario. Si los usuarios no proporcionan su consentimiento, es posible que las aplicaciones y los procesos no funcionen. Intune va a agregar compatibilidad con opciones que permiten a los administradores de TI permitir o impedir el consentimiento del acceso a datos en nombre de los usuarios finales en dispositivos que ejecuten macOS 10.14 y versiones posteriores. Estas opciones garantizarán que las aplicaciones y los procesos sigan funcionando correctamente y reducirán el número de mensajes que experimentan los usuarios finales. 

### <a name="updated-ui-text-and-labels-for-windows-10-endpoint-protection-profile-settings---5983747---"></a>Texto y etiquetas actualizados de la interfaz de usuario para la configuración del perfil de Endpoint Protection de Windows 10<!-- 5983747 -->
Se va a actualizar el texto de varias opciones que se configuran como perfiles de configuración de dispositivos Windows 10 para facilitar la comprensión del uso y los resultados previstos de las opciones. 

Las opciones que se van a actualizar incluyen perfiles de configuración de dispositivos Windows 10 para: 
- [Restricciones de dispositivos](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus) > Antivirus de Microsoft Defender  
- [Endpoint Protection](../protect/endpoint-protection-windows-10.md) > Antivirus de Microsoft Defender

Las opciones que se admiten con Intune no se van a cambiar. Esta actualización es solo para el texto de la interfaz de usuario del Centro de administración del Administrador de puntos de conexión de Microsoft. 


<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.



