---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7113552e09a7c7fa145a452e56575bfaf5297c3e
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514578"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>En desarrollo para Microsoft Intune: febrero de 2020

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Visualización de notificaciones de la aplicación Portal de empresa en Windows<!-- 1808082  -->
Se va a actualizar la aplicación Portal de empresa en dispositivos Windows para mostrar notificaciones del sistema a los usuarios, aunque la aplicación esté cerrada. La actualización va a mostrar notificaciones de las aplicaciones disponibles solo cuando el estado de la instalación sea completado o erróneo. La aplicación Portal de empresa no va a mostrar notificaciones de las aplicaciones requeridas. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Visualización de mensajes de estado de instalación de la aplicación Portal de empresa<!-- 2514416  -->
La aplicación Portal de empresa va a mostrar mensajes de estado de la instalación de aplicaciones adicionales a los usuarios finales. Las condiciones siguientes se aplican a las nuevas características de dependencia de Win32:
- No se pudo instalar la aplicación. No se cumplieron las dependencias definidas por el administrador.

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Cambio del destino de clips web a Microsoft Edge en dispositivos iOS/iPadOS<!-- 5455276 -->
Los clips web, que actúan como aplicaciones web ancladas en dispositivos iOS/iPadOS, deberán actualizarse. Los clips web recién implementados se van a abrir en Microsoft Edge en lugar de en Intune Managed Browser si tienen que abrirse en un explorador protegido. Debe cambiar el destino de los clips web existentes para asegurarse de que se abran en Microsoft Edge en lugar de en Managed Browser.

### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>mejoras en la experiencia del usuario del Portal de empresa de macOS<!-- 5568987 -->
Estamos realizando mejoras en la experiencia de inscripción de dispositivos macOS y en la aplicación Portal de empresa para Mac. Se puede esperar lo siguiente:
- Mejora de la experiencia de Microsoft **AutoUpdate** durante la inscripción que garantizará que los usuarios tengan la versión más reciente del Portal de empresa.
- Paso de comprobación de cumplimiento mejorado durante la inscripción.
- Compatibilidad con los identificadores de incidentes copiados, por lo que los usuarios pueden enviar los errores más rápido desde sus dispositivos al equipo de soporte técnico de su empresa.

Para obtener más información sobre la inscripción y la aplicación del Portal de empresa aplicación para Mac, consulte inscribir un dispositivo macOS con la aplicación Portal de empresa (https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp). 


### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>Pantalla quitada del Portal de empresa, inscripción del perfil de trabajo de Android<!--6103987 -->
La pantalla **¿Cuál es el paso siguiente?** se quitará del flujo de inscripción del perfil de trabajo de Android en el Portal de empresa para simplificar la experiencia del usuario. Vaya a [Inscripción con el perfil de trabajo de Android]( https://docs.microsoft.com/intune-user-help/enroll-device-android-work-profile) para ver el flujo de inscripción del perfil de trabajo de Android actual.

### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424518-idready---"></a>Aplicación Advanced Threat Protection (ATP) de Microsoft Defender para macOS<!-- 5424518 idready -->
Intune proporcionará una manera sencilla de implementar la aplicación Advanced Threat Protection (ATP) de Microsoft Defender para macOS en dispositivos Mac administrados. Para obtener más información, consulte [Advanced Threat Protection de Microsoft Defender para Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac). 

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración del dispositivo

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Perfiles de configuración de dispositivos de red cableada para dispositivos macOS<!-- 3508686  -->
Se va a publicar un nuevo perfil de configuración de dispositivo macOS que configura redes cableadas (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **macOS** para plataforma > **Red cableada** para tipo de perfil). Use esta característica para crear perfiles de 802.1x con el fin de administrar redes cableadas e implementarlas en los dispositivos macOS.

Se aplica a:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932-idready---"></a>Uso permanente de Always On por parte de los perfiles de VPN con conexiones VPN IKEv2 con dispositivos iOS/iPadOS <!-- 1947932 idready -->
En dispositivos iOS/iPadOS, puede crear un perfil de VPN que use una conexión IKEv2 (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS/iPadOS** para plataforma > **VPN** para tipo de perfil). En una actualización futura, puede configurar Always On con IKEv2. Cuando los perfiles de VPN IKEv2 están configurados, se conectan automáticamente y permanecen conectados (o se vuelven a conectar rápidamente) a la VPN. Permanecen conectados incluso al moverse entre redes o al reiniciar dispositivos.

En iOS/iPadOS, la VPN de Always On está limitada a perfiles de IKEv2.

Para ver la configuración IKEv2 actual que puede establecer, vaya a [Incorporación de VPN en dispositivos iOS/iPadOS en Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Se aplica a:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Experiencia de interfaz de usuario mejorada al crear perfiles de configuración en dispositivos iOS/iPadOS y macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Cuando se crea un perfil para dispositivos iOS/iPadOS o macOS, se actualiza la experiencia en el Centro de administración de Endpoint Manager. Este cambio afecta a los siguientes perfiles de configuración de dispositivos (**Dispositivos** > **Perfiles de configuración** > **Crear perfil** > **iOS** o **macOS** para plataforma):

- Personalizado: iOS/iPadOS y macOS
- Características del dispositivo: iOS/iPadOS y macOS
- Restricciones de dispositivos: iOS/iPadOS y macOS
- Endpoint Protection: macOS
- Extensiones: macOS
- Archivo de preferencias: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Experiencia de interfaz de usuario mejorada al crear perfiles de configuración de OEMConfig en dispositivos Android Enterprise<!-- 5568645 idready  -->
Al crear o editar un perfil de OEMConfig para dispositivos Android Enterprise, se actualiza la experiencia en el Centro de administración del Administrador de puntos de conexión. La experiencia actualizada proporciona un resumen de los valores que se han configurado de un vistazo. Este cambio afecta al perfil de configuración del dispositivo de OEMConfig (**Dispositivos** > **Perfiles de configuración** > **Crear perfil** > **Android Enterprise** para plataforma > **OEMConfig** para tipo de perfil).

Esta característica se aplica a:
- Android Enterprise 


<!-- ***********************************************-->
<!--## Device enrollment-->


<!-- ***********************************************-->
## <a name="device-management"></a>Administración de dispositivos

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Cambio del usuario primario para dispositivos Windows <!-- 3794742 -->
Podrá cambiar el usuario primario para dispositivos híbridos de Windows y unidos a Azure AD. Para ello, vaya a **Intune** > **Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Propiedades** > **Usuario primario**. 

### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765---"></a>Número de serie en la página del certificado push MDM de Apple<!--5947765 -->
La página del certificado push MDM de Apple mostrará el número de serie. El número de serie es necesario para recuperar el acceso al certificado de extracción MDM de Apple si se pierde el acceso al id. de Apple que creó el certificado. Para ver el número de serie, vaya a **Dispositivos** > **iOS** > **Inscripción de iOS** > **Certificado push MDM de Apple**.

### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689---"></a>Elección de las actualizaciones de iOS/iPadOS que se van a insertar en los dispositivos inscritos<!--5879689 -->
Podrá elegir una actualización específica de iOS/iPadOS para insertarla en los dispositivos inscritos mediante Apple Business Manager o Apple School Manager. Estos dispositivos deben tener una directiva de configuración de dispositivos establecida para retrasar la visibilidad de las actualizaciones de software durante un número determinado de días. Para ver esta característica, vaya a MEM > **Dispositivos** >  **iOS** > **Directivas de actualización para iOS/iPadOS** > **Crear perfil**.

### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689--"></a>Nuevas opciones de programación de actualización para insertar actualizaciones del sistema operativo en dispositivos iOS/iPadOS inscritos<!--5879689-->
Podrá elegir entre las siguientes opciones al programar las actualizaciones del sistema operativo para dispositivos iOS/iPadOS. Esto se aplica a los dispositivos que usaron los tipos de inscripción Apple Business Manager o Apple School Manager.
- Actualización en la siguiente inserción
- Actualización durante la hora programada
- Actualización fuera de la hora programada

En las dos últimas opciones, puede crear varias ventanas de tiempo.

Para ver las nuevas opciones, vaya a MEM > **Dispositivos** >  **iOS** > **Directivas de actualización para iOS/iPadOS** > **Crear perfil**.


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Supervisión y solución de problemas

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>Mejora de la experiencia de informes de Intune<!-- 3791418 idready -->
Intune ahora proporciona una experiencia de informes mejorada, con nuevos tipos de informes, una mejor organización de informes, vistas más centradas y una funcionalidad de informes más eficiente, así como datos más coherentes y precisos. La experiencia de informes pasará de la versión preliminar pública a GA (disponibilidad general). Además, la versión de GA proporcionará compatibilidad para la localización, correcciones de errores, mejoras de diseño y datos de cumplimiento de dispositivos agregados en los mosaicos del [centro de administración de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

Los nuevos tipos de informe se centran en lo siguientes aspectos:
- **Operativo**: proporciona registros nuevos con un enfoque de estado negativo. 
- **Organizativo**: proporciona un resumen más amplio del estado general.
- **Histórico**: proporciona patrones y tendencias a lo largo de un período de tiempo.
- **Especialista**: le permite usar datos sin procesar para crear sus propios informes personalizados.

El primer conjunto de informes nuevos se centra en el cumplimiento de los dispositivos. Para obtener más información, vea [Blog:marco de creación de informes de Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) e [Informes de Intune](~/fundamentals/reports.md).



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Control de acceso basado en roles.

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Próximos cambios en la interfaz de usuario de roles de Intune<!--5801612 idready-->
La interfaz de usuario del [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Administración de inquilinos** > **Roles** va a cambiar a un diseño más sencillo e intuitivo. Esta experiencia proporciona la misma configuración y los mismos detalles que se usan ahora, pero la nueva experiencia emplea un proceso similar a un asistente.


<!-- ***********************************************-->
## <a name="security"></a>Seguridad

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Compatibilidad con credenciales derivadas en dispositivos Android COBO<!--4839592-->
Se van a poder usar credenciales derivadas en dispositivos Android Enterprise totalmente administrados. Se va a incluir compatibilidad para recuperar una credencial derivada de Entrust Datacard, Intercede y DISA Purebred. Se va a poder usar una credencial derivada para la autenticación de aplicaciones, Wi-Fi, VPN o la firma o el cifrado S/MIME en las aplicaciones que lo admitan.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Uso de la directiva antivirus para administrar la configuración del antivirus de Microsoft Defender y la experiencia de Seguridad de Windows<!--6131401 -->
En el nodo *Seguridad del punto de conexión*, podrá configurar las opciones del **antivirus**. Al configurar la directiva del antivirus, definirá la configuración de los dispositivos Windows 10 a través de dos tipos de perfil:

- Antivirus de Microsoft Defender: administre la configuración de protección en la nube, exclusiones del antivirus, correcciones, opciones de análisis, etc.
- Experiencia de Seguridad de Windows: administre el modo en que los usuarios experimentan la configuración de Seguridad de Windows en sus dispositivos. Podrá configurar lo que pueden ver los usuarios finales en el centro de seguridad de Microsoft Defender y las notificaciones que reciben. 

<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


