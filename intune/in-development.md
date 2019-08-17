---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c2b9429bf5b50ac5e416c4a7b356627e9cc9fb1
ms.sourcegitcommit: f75386986d24e7d5dd63a3f1a0a014cb52056063
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560109"
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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar el contenido de notificación de aplicación para las cuentas de la organización <!-- 2576686 -->
Las directivas de protección de aplicaciones (APP) de Intune en dispositivos iOS y Android le permitirán controlar el contenido de las notificaciones de la aplicación para las cuentas de la organización. Esta característica requerirá la compatibilidad de las aplicaciones y es posible que no esté disponible para todas las aplicaciones habilitadas para la aplicación. Consulte [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) para obtener más información sobre APP.

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Notificación de aplicaciones de Google Play disponibles para perfiles de trabajo de Android <!-- 3041956  -->
En las instalaciones de aplicaciones disponibles en dispositivos de perfil de trabajo de Android, puede ver el estado de instalación de la aplicación y la versión instalada de aplicaciones administradas de Google Play. Para obtener más información, vea [Supervisión de las directivas de protección de aplicaciones](app-protection-policies-monitor.md), [Administrar dispositivos de perfil de trabajo Android con Intune](android-enterprise-overview.md) y [Tipo de aplicación de Google Play administrado](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración de los dispositivos

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Compatibilidad con perfiles VPN de IKEv2 para iOS <!-- 1943438 -->
Va a poder crear perfiles VPN para el cliente VPN nativo de iOS mediante el protocolo IKEv2. IKEv2 es un nuevo tipo de conexión en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **VPN** para tipo de perfil > **Configuración**.

Estos perfiles VPN configuran el cliente VPN nativo. Por lo tanto, ninguna aplicación cliente VPN se instala ni se inserta en dispositivos administrados. Esta característica exige que los dispositivos estén inscritos en Intune (inscripción de MDM).

Para ver la configuración VPN actual que puede establecer, vaya a [Configuración de VPN en dispositivos iOS en Microsoft Intune](vpn-settings-ios.md).

Se aplica a iOS.

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscripción de dispositivos

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Para dispositivos iOS, personalice la pantalla de privacidad del proceso de inscripción del Portal de empresa <!-- 4394993  -->
Con Markdown, podrá personalizar la pantalla de privacidad del Portal de empresa que los usuarios finales ven durante la inscripción de iOS. En concreto, podrá personalizar la lista de elementos que su organización no puede ver o realizar en el dispositivo.

<!-- ***********************************************-->
## <a name="security"></a>Seguridad

### <a name="import-and-export-security-baselines------3408610------------"></a>Importar y exportar líneas base de seguridad    <!--3408610          -->  
Estamos agregando la capacidad de exportar e importar líneas de base de seguridad. Esta característica le permitirá realizar sus personalizaciones y compartirlas entre entornos de Intune.

<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.




