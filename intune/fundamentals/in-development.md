---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 01ea2f75d166e5cc6aef4b890dba5722a74c1f61
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827826"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>En desarrollo para Microsoft Intune: enero de 2020

Para ayudarle con la preparación y planeación, en esta página se enumeran las actualizaciones y características de la interfaz de usuario de Intune que están en desarrollo, pero que aún no se han publicado. Además de la información de esta página: 

- Si prevemos que tendrá que tomar medidas antes de realizar un cambio, haremos una publicación complementaria en el Centro de mensajes de Office.
- Cuando una característica [entra en producción](whats-new.md), ya sea una vista previa o disponible con carácter general, la descripción de la característica pasará de esta página a las novedades.
- Esta página y la página [Novedades](whats-new.md) se actualizan periódicamente. Compruebe si hay actualizaciones adicionales.
- Consulte el [plan de desarrollo de Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para conocer los plazos de tiempo y los productos estratégicos.

> [!NOTE]
> Esta página refleja nuestras expectativas actuales sobre las funcionalidades de Intune en una versión futura. Las fechas y las características individuales pueden cambiar. En esta página no se describen todas las características de desarrollo.

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Mostrar notificaciones para la aplicación Portal de empresa en Windows<!-- 1808082  -->
Actualizaremos la aplicación Portal de empresa en dispositivos Windows para mostrar las notificaciones del sistema a los usuarios, incluso cuando la aplicación está cerrada. La actualización mostrará las notificaciones de las aplicaciones disponibles solo cuando el estado de la instalación sea completado o erróneo. La aplicación Portal de empresa no mostrará notificaciones de las aplicaciones necesarias. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Mostrar mensajes de estado de instalación de la aplicación Portal de empresa<!-- 2514416  -->
La aplicación Portal de empresa mostrará mensajes de estado de instalación de aplicaciones adicionales a los usuarios finales. Las condiciones siguientes se aplicarán a las nuevas características de dependencia de Win32:
- No se pudo instalar la aplicación. No se cumplieron las dependencias definidas por el administrador.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276-idready---"></a>Redestinar clips web a Microsoft Edge en dispositivos iOS<!-- 5455276 idready -->
Los clips Web, que actúan como aplicaciones web ancladas en dispositivos iOS, tendrán que actualizarse. Los clips web recién implementados se abrirán en Microsoft Edge en lugar de en el Intune Managed Browser, si es necesario, para abrirse en un explorador protegido. Debe redestinar los clips web preexistentes para asegurarse de que se abren en Microsoft Edge en lugar de en el Managed Browser. 

### <a name="user-experience-change-when-adding-apps-to-intune---4705829-idready---"></a>Cambio en la experiencia del usuario al agregar aplicaciones a Intune<!-- 4705829 idready -->
Verá una nueva experiencia de usuario al agregar aplicaciones a través de Intune. Esta experiencia proporciona la misma configuración y los detalles que se han usado anteriormente, pero la nueva experiencia sigue un proceso similar a un asistente antes de agregar una aplicación a Intune. Esta nueva experiencia también proporciona una página de revisión antes de agregar la aplicación. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Aplicaciones** > **Todas las aplicaciones** > **Agregar**. Para más información, vea [Agregar aplicaciones a Microsoft Intune](~/apps/apps-add.md).

#### <a name="require-win32-apps-to-restart----3136567--"></a>Requerir que las aplicaciones Win32 se reinicien <!-- 3136567-->
Puede requerir que una aplicación Win32 se reinicie después de una instalación correcta. Además, puede elegir la cantidad de tiempo (el período de gracia) antes de que se produzca el reinicio.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración del dispositivo

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Agregar configuración de proxy automática a perfiles de Wi-Fi para perfiles de trabajo de Android Enterprise<!-- 4490822 idready -->
En los dispositivos de Perfil de trabajo de Android Enterprise, puede crear perfiles de Wi-Fi. Al elegir el tipo de Wi-Fi Enterprise, también puede especificar el tipo de protocolo de autenticación extensible (EAP) que se usa en la red Wi-Fi.

En una actualización futura, al elegir el tipo de empresa, podrá especificar la configuración de proxy automática, incluida una dirección URL del servidor proxy, como `proxy.contoso.com`.

Para ver la configuración actual de Wi-Fi que puede configurar, vaya a [Agregar configuración de Wi-Fi para dispositivos que ejecutan Android Enterprise y Android quiosco en Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Se aplica a:
- Perfil de trabajo de Android Enterprise

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Perfiles de configuración de dispositivo de red cableada para dispositivos macOS<!-- 3508686  -->
Hay disponible un nuevo perfil de configuración de dispositivo macOS que configura las redes cableadas **(configuración de dispositivos** > **perfiles** > **crear perfil** > **MacOS** para plataforma > **red cableada** para el tipo de perfil). Use esta característica para crear perfiles de 802.1 x con el fin de administrar redes cableadas e implementar estas redes cableadas en los dispositivos macOS.

Se aplica a:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>Los perfiles de VPN con conexiones VPN de IKEv2 pueden usar AlwaysOn con dispositivos iOS <!-- 1947932 idready -->
En dispositivos iOS, puede crear un perfil de VPN que use una conexión IKEv2 (**configuración de dispositivo** > **perfiles** > **crear perfil** > **iOS/ipados** para la plataforma > **VPN** para el tipo de perfil). En una actualización futura, puede configurar AlwaysOn con IKEv2. Cuando se configura, los perfiles de VPN de IKEv2 se conectan automáticamente y permanecen conectados (o se vuelven a conectar rápidamente) a la VPN. Permanece conectado incluso cuando se mueve entre redes o se reinician dispositivos.

En iOS, la VPN de AlwaysOn está limitada a los perfiles de IKEv2.

Para ver la configuración IKEv2 actual que puede establecer, vaya a [Incorporación de VPN en dispositivos iOS en Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Se aplica a:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Mejora de la experiencia de interfaz de usuario al crear perfiles de configuración en dispositivos iOS y macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Cuando se crea un perfil para dispositivos iOS o macOS, se actualiza la experiencia en el centro de administración de Endpoint Management. Este cambio afecta a los siguientes perfiles de configuración de dispositivo (**dispositivos** > **perfiles de configuración** > **crear perfil** > **iOS** o **MacOS** para la plataforma):

- Personalizado: iOS, macOS
- Características del dispositivo: iOS, macOS
- Restricciones de dispositivos: iOS, macOS
- Endpoint Protection: macOS
- Extensiones: macOS
- Archivo de preferencias: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Mejora de la experiencia de interfaz de usuario al crear perfiles de configuración de OEMConfig en dispositivos empresariales Android<!-- 5568645 idready  -->
Al crear o editar un perfil de OEMConfig para dispositivos empresariales Android, se actualiza la experiencia del centro de administración de Endpoint Management. La experiencia actualizada le proporcionará un resumen de la configuración que ha configurado de un vistazo. Este cambio afecta al perfil de configuración del dispositivo OEMConfig (**dispositivos** > **perfiles de configuración** > **crear perfil** > **Android Enterprise** for Platform > **OEMConfig** para el tipo de perfil).

Esta característica se aplica a:
- Android Enterprise 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscripción de dispositivos

### <a name="block-android-enrollments-by-device-manufacturer--5197392-idready--"></a>Bloquear las inscripciones de Android por el fabricante del dispositivo<!--5197392 idready-->
Podrá bloquear la inscripción de los dispositivos en función del fabricante del dispositivo. Esto se aplica a los dispositivos de Perfil de trabajo de Android Enterprise y de administrador de dispositivos Android. Para ver las restricciones de inscripción, vaya al [centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)> **dispositivos** > **restricciones de inscripción**.



<!-- ***********************************************-->
## <a name="device-management"></a>Administración de dispositivos


### <a name="new-information-in-device-details---4471759-5604099----"></a>Nueva información en detalles del dispositivo<!-- 4471759 5604099  -->
La siguiente información se agregará a la página de **información general** de los dispositivos:
- Capacidad de memoria (cantidad de memoria física en el dispositivo)
- Capacidad de almacenamiento (cantidad de almacenamiento físico en el dispositivo) 
- Tipo de procesador de CPU y velocidad
- RAM y datos del procesador

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Control de acceso basado en roles.

### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-idready--"></a>Nuevo rol integrado de Intune administrador de seguridad de puntos de conexión<!--4253397 idready-->
Habrá un nuevo rol integrado de Intune disponible: el administrador de seguridad de puntos de conexión. Este nuevo rol concede a los administradores acceso completo al nodo de administrador de puntos de conexión en Intune y acceso de solo lectura a otras áreas. El rol es una expansión del rol "Administrador de seguridad" desde Azure AD. Si actualmente solo tiene administradores globales como roles, no es necesario realizar ningún cambio. Si usa roles y desea la granularidad que proporciona el administrador de seguridad de puntos de conexión, asigne ese rol cuando esté disponible. Para obtener más información acerca de los roles integrados, consulte [control de acceso basado en roles](role-based-access-control.md).

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Cambios en la interfaz de usuario de roles de Intune<!--5801612 idready-->
La interfaz de usuario del [centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **roles** de > de **Administración de inquilinos** va a cambiar a un diseño más sencillo e intuitivo. Esta experiencia proporciona la misma configuración y los mismos detalles que utiliza ahora, pero la nueva experiencia emplea un proceso similar a un asistente.


<!-- ***********************************************-->
## <a name="security"></a>Seguridad

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Compatibilidad de credenciales derivadas en dispositivos Android COBO<!--4839592-->
Podrá usar credenciales derivadas en dispositivos Android Enterprise totalmente administrados. Se incluirá compatibilidad para recuperar una credencial derivada para Entrust Datacard, intervenir y DISA purebred. Podrá usar una credencial derivada para la autenticación de aplicaciones, la red Wi-Fi, VPN o la firma y/o el cifrado de S/MIME con aplicaciones que lo admitan. 

<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


