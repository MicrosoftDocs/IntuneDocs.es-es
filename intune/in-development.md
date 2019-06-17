---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1c8a7be6646c0035eaefed6d61d749c8469c8a4e
ms.sourcegitcommit: 119962948045079022aa48f968dde3e961d7cd0c
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031652"
---
# <a name="in-development-for-microsoft-intune---june-2019"></a>En desarrollo para Microsoft Intune: junio de 2019

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

<!-- ***********************************************-->
### <a name="app-management"></a>Administración de aplicaciones

#### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Los usuarios del dispositivo pueden ver todas las aplicaciones administradas que han instalado o han intentado instalar <!-- 2352913 -->
Portal de empresa para Windows va a mostrar una lista de todas las aplicaciones administradas (tanto las requeridas como las disponibles) que están instaladas en el dispositivo de un usuario. Los usuarios podrán ver las instalaciones de aplicaciones intentadas y pendientes, así como sus estados actuales. Si su organización no hace que las aplicaciones sean obligatorias o estén disponibles, los usuarios verán un mensaje en el que se explica que no se ha instalado ninguna aplicación de empresa. Los usuarios también podrán ordenar o filtrar sus aplicaciones por estado de instalación.

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Configuración del explorador que se puede vincular a datos organizativos <!-- 3145939 -->
Las directivas de protección de aplicaciones (APP) de Intune en dispositivos iOS y Android van a permitir transferir vínculos web Org a un explorador determinado más allá de Intune Managed Browser o Microsoft Edge.  Consulte [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) para obtener más información sobre APP.

#### <a name="installed-apps-page-on-the-company-portal-website-----4224326---"></a>Página Aplicaciones instaladas en el sitio web Portal de empresa  <!-- 4224326 -->
El [sitio web Portal de empresa](https://portal.manage.microsoft.com/) va a incluir una nueva página para mostrar a los usuarios todas las aplicaciones que se han instalado en el dispositivo. Esta lista incluye las aplicaciones disponibles y las requeridas por la organización. Desde esta página, los usuarios van a poder ver los estados de instalación y requisitos de las aplicaciones del dispositivo. Para obtener más información sobre el sitio web Portal de empresa, vea [Usar el sitio web del Portal de empresa de Intune](/intune-user-help/using-the-intune-company-portal-website) y [Configuración de la aplicación Portal de empresa de Microsoft Intune](company-portal-app.md).

#### <a name="call-graph-api-read-operations-from-an-application-without-user-credentials----4655885---"></a>Llamada a operaciones de lectura de Graph API desde una aplicación sin credenciales de usuario <!-- 4655885 -->
Las aplicaciones van a poder llamar a operaciones de lectura de Graph API de Intune con la identidad de la aplicación y sin credenciales de usuario. Para obtener más información, vea [Obtener acceso sin un usuario](https://docs.microsoft.com/graph/auth-v2-service).

<!-- ***********************************************-->
### <a name="device-configuration"></a>Configuración del dispositivo


#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Compatibilidad con perfiles VPN de IKEv2 para iOS <!-- 1943438 -->
Va a poder crear perfiles VPN para el cliente VPN nativo de iOS mediante el protocolo IKEv2. IKEv2 es un nuevo tipo de conexión en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **VPN** para tipo de perfil > **Configuración**.

Estos perfiles VPN configuran el cliente VPN nativo. Por lo tanto, ninguna aplicación cliente VPN se instala ni se inserta en dispositivos administrados. Esta característica exige que los dispositivos estén inscritos en Intune (inscripción de MDM).

Para ver la configuración VPN actual que puede establecer, vaya a [Configuración de VPN en dispositivos iOS en Microsoft Intune](vpn-settings-ios.md).

Se aplica a iOS.

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----20430240---"></a>Configuración de las extensiones de kernel en dispositivos macOS <!-- 20430240 -->
En dispositivos macOS, puede crear un perfil de configuración de dispositivos (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > elija **macOS** como plataforma). Una próxima actualización va a incluir un nuevo grupo de opciones de configuración que permite configurar y usar las extensiones de kernel en los dispositivos.

Se aplica a: macOS 10.13.2 y versiones posteriores

#### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Compatibilidad con la línea de base para la búsqueda de palabras clave  <!-- 3082036         -->
Al crear o editar un perfil de línea de base de seguridad, pronto se podrá usar la *búsqueda* para filtrar la configuración que se muestra en la consola.   

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Uso de "reglas de aplicabilidad" al crear perfiles de configuración de dispositivo Windows 10 <!-- 2549910 -->
Puede crear perfiles de configuración de dispositivo Windows 10 (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10** como plataforma). Podrá crear una **regla de aplicabilidad** para que el perfil solo se aplique a una edición o una versión en concreto. Por ejemplo, cree un perfil que permita algunas opciones de configuración de BitLocker. Una vez que agregue el perfil, use una regla de aplicabilidad para que este solo se aplique a los dispositivos que ejecuten Windows 10 Enterprise.

Se aplica a: 
- Windows 10 y versiones posteriores

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002----"></a>La opción Permitir solo aplicaciones de la Tienda para dispositivos Windows 10 incluye más opciones de configuración <!-- 2697002  -->

Al crear un perfil de restricciones de dispositivos para dispositivos Windows, se puede usar la opción **Permitir solo aplicaciones de la Tienda** de modo que los usuarios solo instalen aplicaciones de la Tienda Windows (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **Restricciones de dispositivos** para tipo de perfil). En una próxima actualización, este valor se va a ampliar para admitir más opciones. 

Para ver la configuración actual, vaya a [Configuración de dispositivos con Windows 10 y versiones posteriores para permitir o restringir características mediante Intune](device-restrictions-windows-10.md#app-store).

Se aplica a: Windows 10 y versiones posteriores

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Implementación de varios perfiles de dispositivo de extensiones de movilidad de Zebra en un dispositivo, el mismo grupo de usuarios o el mismo grupo de dispositivos <!-- 4089955 -->
En Intune, puede usar extensiones de movilidad (MX) de Zebra en un perfil de configuración de dispositivo para personalizar la configuración o agregar opciones de configuración no integradas en Intune. Actualmente, puede implementar un perfil en un único dispositivo. En una próxima actualización, se van a poder implementar varios perfiles en:

- Mismo grupo de usuarios
- Mismo grupo de dispositivos
- Dispositivo único

En [Usar y administrar dispositivos Zebra con extensiones de movilidad de Zebra en Microsoft Intune](android-zebra-mx-overview.md) se muestra cómo usar MX en Intune.

Se aplica a: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Algunas opciones de configuración de pantalla completa en dispositivos iOS se establecen mediante "Bloquear", en sustitución de "Permitir" <!-- 4404075  -->
Al crear un perfil de restricciones de dispositivos en dispositivos iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **Pantalla completa**), se establecen el **Bloqueo automático**, el **Cambio de timbre**, la **Rotación de pantalla**, el **Botón de suspensión de pantalla** y los **Botones de volumen**. 

Actualmente, estas opciones se configuran mediante **Permitir** (bloquea la característica) o **Sin configurar** (permite la característica). En una próxima actualización, los valores van a ser **Bloquear** (bloquea la característica) o **Sin configurar** (permite la característica).

Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características ](device-restrictions-ios.md). 

Se aplica a iOS.

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704----"></a>Uso de Face ID para la autenticación de contraseña en dispositivos iOS <!-- 4490704  -->
Al crear un perfil de restricciones de dispositivos para dispositivos iOS, puede usar una huella digital para una contraseña. En una próxima actualización, la configuración de contraseña de huella digital también va a permitir el reconocimiento facial (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **Contraseña**). Como resultado, van a cambiar las opciones de configuración siguientes:

- **Desbloqueo con huella digital** es ahora **Desbloqueo de Touch ID y Face ID**.
- **Modificación de huella digital (solo con supervisión)** es ahora **Modificación de Touch ID y Face ID (solo con supervisión)** .

Face ID está disponible en iOS 11.0 y versiones posteriores. Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](device-restrictions-ios.md#password).

Se aplica a iOS.

#### <a name="apps-feature-is-dependent-on-ratings-region-when-restricting-gaming-and-app-store-features-on-ios-devices----4593948----"></a>La característica Aplicaciones depende de la región de clasificación a la hora de restringir características de juegos y aplicaciones de la tienda en dispositivos iOS <!-- 4593948  -->
En dispositivos iOS, puede permitir o restringir características relacionadas con los juegos, la tienda de aplicaciones y la visualización de documentos (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **App Store, presentación de documentos, juegos**). También puede elegir la región de clasificación, por ejemplo, Estados Unidos. En una próxima actualización, la característica **Aplicaciones** pasará a ser un elemento secundario de **Región de clasificación** y a depender de **Región de clasificación**.

Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Se aplica a iOS.

#### <a name="administrative-templates-for-group-policy---------3510695---"></a>Plantillas administrativas para directiva de grupo     <!--  3510695 -->
Para ayudar a mejorar la seguridad de los dispositivos en la nube, se van a lanzar plantillas administrativas que permiten usar Intune para configurar y seleccionar opciones de directiva de grupo para equipos Windows.  Estas plantillas usan el proveedor de servicios de configuración (CSP) de directivas para proporcionar hasta 2500 opciones adicionales de Office, Windows y OneDrive.

####  <a name="new-settings-for-the-windows-security-baseline-----3534649-4217151------------"></a>Nueva configuración para la línea de base de seguridad de Windows  <!-- 3534649, 4217151          -->
Se han agregado nuevas opciones a la línea de base de seguridad de Windows. La primera es la seguridad basada en la virtualización, que requiere Arranque seguro. La segunda opción permite administrar la activación por voz de las aplicaciones Windows cuando la pantalla está bloqueada.

#### <a name="security-baselines-will-be-generally-available------3785395---------"></a>Disponibilidad general de Líneas de base de seguridad  <!--  3785395       -->
La característica Líneas de base de seguridad pronto va a dejar de estar en versión preliminar para estar disponible con carácter general. 

#### <a name="the-windows-security-baseline-template-will-be-generally-available-------3794072---------"></a>Disponibilidad general de la plantilla Línea de base de seguridad de Windows   <!--  3794072       -->
La plantilla Línea de base de seguridad de Windows pronto va a dejar de estar en versión preliminar para estar disponible con carácter general. La versión preliminar de la plantilla se va a retirar y habrá disponible una nueva plantilla.

<!-- ***********************************************-->
### <a name="device-management"></a>Administración de dispositivos

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Asignación de etiquetas de ámbito a todos los dispositivos administrados de un grupo de seguridad <!-- 3173810 -->
Actualmente, puede asignar una etiqueta de ámbito a un dispositivo en la página **Propiedades** de cada dispositivo individual; allí, seleccione las etiquetas de ámbito. En una próxima actualización, va a poder asignar etiquetas de ámbito a un grupo de seguridad y todos los dispositivos del grupo de seguridad también se asociarán a esas etiquetas de ámbito. Para ello, seleccione **Intune** > **Roles** > **Ámbito (etiquetas)**  > **Crear** > **Ámbito (etiquetas)** > seleccione los grupos a los que quiere asignar la etiqueta de ámbito. La etiqueta de ámbito también se asigna a todos los dispositivos de estos grupos. Las etiquetas de ámbito establecidas con esta característica sobrescriben a las establecidas con el flujo de etiquetas de ámbito de dispositivo actual. (En una próxima actualización, el flujo actual para asignar etiquetas de ámbito a dispositivos será de solo lectura).

#### <a name="see-the-security-patch-level-for-android-devices----4461911----"></a>Consulta del nivel de revisión de seguridad para dispositivos Android <!-- 4461911  -->
Puede ver el nivel de revisión de seguridad de dispositivos Android. Para ello, seleccione **Intune** > **Dispositivos** > **Todos los dispositivos** > seleccione un dispositivo > **Monitor** > **Hardware**.


<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para más información sobre los desarrollos recientes.


