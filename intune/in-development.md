---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7dd6f62cb53dd0cc373fb3f2ffa7d9434b135cd
ms.sourcegitcommit: 116ef72b9da4d114782d4b8dd9f57556c9b01511
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2019
ms.locfileid: "67494240"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>En desarrollo para Microsoft Intune: julio de 2019

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


### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>Notificaciones personalizadas para usuarios y grupos    <!-- 16766574   -->
Pronto podrá enviar notificaciones de inserción personalizadas de ad-hoc de la aplicación de Portal de empresa a los usuarios de iOS y Android dispositivos administrados con Intune. Estas notificaciones personalizadas no están vinculadas a determinadas características de Intune y se puede usar para cualquier propósito que requiera, incluidas las notificaciones generales que desea enviar a algunos o todos los empleados.  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar el contenido de la notificación de aplicación para las cuentas de organización <!-- 2576686 -->
Directivas de protección de aplicación (aplicación) de Intune en dispositivos iOS y Android le permitirá al contenido de notificación de aplicación de control de cuentas de organización. Esta característica requiere compatibilidad de aplicaciones y puede no estar disponible para todas las aplicaciones de la aplicación habilitada. Consulte [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) para obtener más información sobre APP.

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Notificación de aplicaciones de Google Play disponibles para perfiles de trabajo de Android <!-- 3041956  -->
En las instalaciones de aplicaciones disponibles en dispositivos de perfil de trabajo de Android, puede ver el estado de instalación de la aplicación, así como la versión instalada de aplicaciones administradas de Google Play. Para obtener más información, vea [Supervisión de las directivas de protección de aplicaciones](app-protection-policies-monitor.md), [Administrar dispositivos de perfil de trabajo Android con Intune](android-enterprise-overview.md) y [Tipo de aplicación de Google Play administrado](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración de los dispositivos


### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Compatibilidad con perfiles VPN de IKEv2 para iOS <!-- 1943438 -->
Va a poder crear perfiles VPN para el cliente VPN nativo de iOS mediante el protocolo IKEv2. IKEv2 es un nuevo tipo de conexión en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **VPN** para tipo de perfil > **Configuración**.

Estos perfiles VPN configuran el cliente VPN nativo. Por lo tanto, ninguna aplicación cliente VPN se instala ni se inserta en dispositivos administrados. Esta característica exige que los dispositivos estén inscritos en Intune (inscripción de MDM).

Para ver la configuración VPN actual que puede establecer, vaya a [Configuración de VPN en dispositivos iOS en Microsoft Intune](vpn-settings-ios.md).

Se aplica a iOS.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Uso de "reglas de aplicabilidad" al crear perfiles de configuración de dispositivo Windows 10 <!-- 2549910 -->
Puede crear perfiles de configuración de dispositivo Windows 10 (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10** como plataforma). Podrá crear una **regla de aplicabilidad** para que el perfil solo se aplique a una edición o una versión en concreto. Por ejemplo, cree un perfil que permita algunas opciones de configuración de BitLocker. Una vez que agregue el perfil, use una regla de aplicabilidad para que este solo se aplique a los dispositivos que ejecuten Windows 10 Enterprise.

Se aplica a: 
- Windows 10 y versiones posteriores

### <a name="administrative-templates-for-group-policy---------3510695---"></a>Plantillas administrativas para directiva de grupo     <!--  3510695 -->
Para ayudar a mejorar la seguridad de los dispositivos en la nube, se van a lanzar plantillas administrativas que permiten usar Intune para configurar y seleccionar opciones de directiva de grupo para equipos Windows.  Estas plantillas usan el proveedor de servicios de configuración (CSP) de directivas para proporcionar hasta 2500 opciones adicionales de Office, Windows y OneDrive.

### <a name="manage-filevault-for-macos-------3858502--1210104-----"></a>Administrar FileVault para macOS   <!--  3858502 + 1210104   -->
Podrá usar un perfil de configuración de dispositivo de Intune endpoint protection para administrar el cifrado de clave FileVault para dispositivos macOS. Esto incluye la custodia de visualización de y rotar las claves de cifrado de los dispositivos corporativos. Los usuarios finales podrán recuperar dichas claves en el sitio Web de Portal de empresa.

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Configuración avanzada del Firewall de Windows Defender   <!--  1311949     -->
Como versión preliminar pública, pronto podrá usar Intune para administrar las reglas de firewall personalizadas en los clientes de Windows Defender.  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Nuevo diseñador de configuración al crear un perfil de OEMConfig para Android Enterprise <!-- 3712769  -->
En Intune, puede crear un perfil de configuración de dispositivo que usa una aplicación OEMConfig (configuración del dispositivo > perfiles > Crear perfil > Android enterprise para plataforma > OEMConfig para el tipo de perfil). Al hacerlo, se abre un editor de JSON con una plantilla y valores para que pueda cambiar. Esta actualización incluye un diseñador de configuración con una experiencia de usuario mejorada que muestre detalles incrustados en la aplicación, incluidos los títulos, descripciones y mucho más. El editor de JSON sigue estando disponible y muestra todos los cambios realizados en el Diseñador de configuración.

Para ver la configuración actual, vaya a [uso y administración de dispositivos empresariales Android con OEMConfig](android-oem-configuration-overview.md).

Se aplica a: Android Enterprise


<!-- ***********************************************-->
## <a name="device-management"></a>Administración de dispositivos

### <a name="improve-device-location---3855417---"></a>Mejorar la ubicación del dispositivo<!-- 3855417 -->
Podrá acercar las coordenadas exactas de un dispositivo mediante el **Buscar dispositivo** acción. Para obtener más información acerca de cómo buscar dispositivos perdidos de iOS, consulte [buscar dispositivos iOS perdidos](device-locate.md).

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurar el límite de tiempo de limpieza automática de dispositivos hasta 30 días <!--4231059  -->
Podrá establecer el límite de tiempo de limpieza automática de dispositivos lo más corto 30 días (en lugar de límite actual de 90 días) después del último inicio de sesión. Para ello, vaya a **Intune** > **dispositivos** > **instalación** > **limpia de las reglas de dispositivo**.


<!-- ***********************************************-->
## <a name="security"></a>Seguridad

### <a name="import-and-export-security-baselines------3408610------------"></a>Importar y exportar líneas base de seguridad    <!--3408610          -->  
Estamos agregando la capacidad de exportar e importar líneas base de seguridad para que pueda realizar las personalizaciones con usted y compartirlos entre los entornos de Intune.



<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


