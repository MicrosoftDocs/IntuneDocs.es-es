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
ms.openlocfilehash: d71ae3c15dddedd5d9ebfaf06fcae25af89f6b82
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912645"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>En desarrollo para Microsoft Intune: enero de 2020

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

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276---"></a>Cambio del destino de clips web a Microsoft Edge en dispositivos iOS<!-- 5455276 -->
Los clips web, que actúan como aplicaciones web ancladas en dispositivos iOS, tienen que actualizarse. Los clips web recién implementados se van a abrir en Microsoft Edge en lugar de en Intune Managed Browser si tienen que abrirse en un explorador protegido. Debe cambiar el destino de los clips web existentes para asegurarse de que se abran en Microsoft Edge en lugar de en Managed Browser. 


<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración del dispositivo

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Perfiles de configuración de dispositivos de red cableada para dispositivos macOS<!-- 3508686  -->
Se va a publicar un nuevo perfil de configuración de dispositivo macOS que configura redes cableadas (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **macOS** para plataforma > **Red cableada** para tipo de perfil). Use esta característica para crear perfiles de 802.1x con el fin de administrar redes cableadas e implementarlas en los dispositivos macOS.

Se aplica a:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>Uso permanente de Always On por parte de los perfiles de VPN con conexiones VPN IKEv2 con dispositivos iOS <!-- 1947932 idready -->
En dispositivos iOS, puede crear un perfil de VPN que use una conexión IKEv2 (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS/iPadOS** para plataforma > **VPN** para tipo de perfil). En una actualización futura, puede configurar Always On con IKEv2. Cuando los perfiles de VPN IKEv2 están configurados, se conectan automáticamente y permanecen conectados (o se vuelven a conectar rápidamente) a la VPN. Permanecen conectados incluso al moverse entre redes o al reiniciar dispositivos.

En iOS, la VPN de Always On está limitada a perfiles de IKEv2.

Para ver la configuración IKEv2 actual que puede establecer, vaya a [Incorporación de VPN en dispositivos iOS en Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Se aplica a:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Experiencia de interfaz de usuario mejorada al crear perfiles de configuración en dispositivos iOS y macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Cuando se crea un perfil para dispositivos iOS o macOS, se actualiza la experiencia en el Centro de administración del Administrador de puntos de conexión. Este cambio afecta a los siguientes perfiles de configuración de dispositivos (**Dispositivos** > **Perfiles de configuración** > **Crear perfil** > **iOS** o **macOS** para plataforma):

- Personalizado: iOS, macOS
- Características de dispositivos: iOS, macOS
- Restricciones de dispositivos: iOS, macOS
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
<!--## Device management-->



<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Control de acceso basado en roles.

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Próximos cambios en la interfaz de usuario de roles de Intune<!--5801612 idready-->
La interfaz de usuario del [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Administración de inquilinos** > **Roles** va a cambiar a un diseño más sencillo e intuitivo. Esta experiencia proporciona la misma configuración y los mismos detalles que se usan ahora, pero la nueva experiencia emplea un proceso similar a un asistente.


<!-- ***********************************************-->
## <a name="security"></a>Seguridad

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Compatibilidad con credenciales derivadas en dispositivos Android COBO<!--4839592-->
Se van a poder usar credenciales derivadas en dispositivos Android Enterprise totalmente administrados. Se va a incluir compatibilidad para recuperar una credencial derivada de Entrust Datacard, Intercede y DISA Purebred. Se va a poder usar una credencial derivada para la autenticación de aplicaciones, Wi-Fi, VPN o la firma o el cifrado S/MIME en las aplicaciones que lo admitan. 

<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


