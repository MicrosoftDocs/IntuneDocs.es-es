---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04b284a62076122cec70b6b455151a0377470521
ms.sourcegitcommit: 16a9109b4028589c17695d41271ca4fee8b1d697
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74540735"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>En desarrollo para Microsoft Intune: diciembre de 2019

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

### <a name="ios-user-licensed-vpp-apps---5619268-idready---"></a>aplicaciones de PCV con licencia de usuario de iOS<!-- 5619268 idready -->
En el caso de los dispositivos iOS de inscripción de usuarios, los usuarios finales ya no se mostrarán con las aplicaciones de PCV con licencia de dispositivo implementadas como disponibles. Sin embargo, los usuarios finales seguirán viendo todas las aplicaciones de PCV con licencia de usuario en el Portal de empresa. Para más información relacionada con las aplicaciones VPP, vea [Administración de aplicaciones de iOS y macOS compradas a través del Programa de Compras por Volumen de Apple con Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745-idready---"></a>Recuperación de la clave de recuperación personal desde dispositivos de macOS cifrados de memoria<!-- 4851745 idready -->
Los usuarios finales podrán recuperar su clave de recuperación personal (clave FileVault) mediante la aplicación de Portal de empresa de iOS. El dispositivo que tiene la clave de recuperación personal debe inscribirse en Intune y cifrarse con FileVault a través de Intune. Mediante la aplicación de Portal de empresa de iOS, un usuario final puede abrir la vista Web de Safari y recuperar su clave de recuperación personal. En Intune, seleccione **dispositivos** > *el dispositivo MacOS cifrado y inscrito* > **obtener clave de recuperación**. Para obtener más información sobre FileVault, consulte [cifrado de FileVault para MacOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

### <a name="microsoft-app-icons-update--4677605--"></a>Actualización de iconos de aplicación de Microsoft<!--4677605-->
Los iconos que se usan para las aplicaciones de Microsoft en el panel de destinatarios de aplicación para las directivas de protección de aplicaciones y las directivas de configuración de aplicaciones se actualizarán.

### <a name="smime-support-for-microsoft-outlook-mobile---2669398----"></a>Compatibilidad con S/MIME para Microsoft Outlook Mobile<!-- 2669398  -->
Intune admitirá la entrega de certificados de cifrado y firma S/MIME que se pueden usar con Outlook Mobile en iOS y Android. Para obtener información relacionada, consulte [configuración de correo electrónico para dispositivos iOS](~/configuration/email-settings-ios.md) y [configuración de correo electrónico para dispositivos Android](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications---4736278----"></a>Compatibilidad con la configuración personalizada para aplicaciones macOS<!-- 4736278  -->
Intune será compatible con la configuración personalizada, lo que le permite agregar claves y valores específicos a un archivo de lista de propiedades de preferencias (. plist) existente para configurar las aplicaciones de macOS y el dispositivo. No todas las aplicaciones admiten preferencias administradas y, en algunos casos, solo se puede administrar la configuración específica. La configuración se implementa solo a través del canal de dispositivo. Solo debe cargar los archivos de lista de propiedades o los archivos. XML que tienen como destino la configuración de canal de dispositivo.

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Mostrar notificaciones para la aplicación Portal de empresa en Windows<!-- 1808082  -->
Actualizaremos la aplicación Portal de empresa en dispositivos Windows para mostrar las notificaciones del sistema a los usuarios, incluso cuando la aplicación está cerrada. La actualización mostrará las notificaciones de las aplicaciones disponibles solo cuando el estado de la instalación sea completado o erróneo. La aplicación Portal de empresa no mostrará notificaciones de las aplicaciones necesarias.

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Mostrar mensajes de estado de instalación de la aplicación Portal de empresa<!-- 2514416  -->
La aplicación Portal de empresa mostrará mensajes de estado de instalación de aplicaciones adicionales a los usuarios finales. Las condiciones siguientes se aplicarán a las nuevas características de dependencia de Win32:
- No se pudo instalar la aplicación. No se cumplieron las dependencias definidas por el administrador.

### <a name="configure-app-notification-content-for-organization-accounts---2576686---"></a>Configurar el contenido de notificación de aplicación para las cuentas de la organización<!-- 2576686 -->
La aplicación de Intune en dispositivos iOS y Android le permitirá controlar el contenido de las notificaciones de la aplicación para las cuentas de la organización. Esta característica requerirá la compatibilidad de las aplicaciones y es posible que no esté disponible para todas las aplicaciones habilitadas para la aplicación. Para más información sobre la aplicación, consulte [¿Qué son las directivas de protección de aplicaciones?](../apps/app-protection-policy.md)

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración de los dispositivos

### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998-idready---"></a>Impedir que los usuarios configuren las credenciales de certificado en el almacén de claves administrado en dispositivos de propietario de dispositivos empresariales Android<!-- 3311998 idready -->
En dispositivos Android de dispositivo propietario, habrá una nueva opción para impedir que los usuarios configuren sus credenciales de certificado en el almacén de claves administrado (**configuración de dispositivo** > **perfiles** > **crear perfil** > **Android Enterprise** para la plataforma > **propietario del dispositivo solo > restricciones de dispositivo** para el tipo de perfil > **usuarios + cuentas**).

Para ver la configuración actual, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](../configuration/device-restrictions-android-for-work.md).

Se aplica a:
- Propietario del dispositivo Android Enterprise, incluidos dispositivos dedicados y totalmente administrados

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686-idready---"></a>Perfiles de configuración de dispositivo de red cableada para dispositivos macOS<!-- 3508686 idready -->
En los dispositivos macOS, una actualización futura incluirá un nuevo perfil de configuración de dispositivo que configura las redes cableadas (**configuración de dispositivo** > **perfiles** > **crear perfil** > **MacOS** para plataforma > **red cableada** para el tipo de perfil). Use esta característica para crear perfiles de 802.1 x con el fin de administrar redes cableadas e implementar estas redes cableadas en los dispositivos macOS.

Se aplica a:
- macOS

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Agregar configuración de proxy automática a perfiles de Wi-Fi para perfiles de trabajo de Android Enterprise<!-- 4490822 idready -->
En los dispositivos de Perfil de trabajo de Android Enterprise, puede crear perfiles de Wi-Fi. Al elegir el tipo de Wi-Fi Enterprise, también puede especificar el tipo de protocolo de autenticación extensible (EAP) que se usa en la red Wi-Fi.

En una actualización futura, al elegir el tipo de empresa, podrá especificar la configuración de proxy automática, incluida una dirección URL del servidor proxy, como `proxy.contoso.com`.

Para ver la configuración actual de Wi-Fi que puede configurar, vaya a [Agregar configuración de Wi-Fi para dispositivos que ejecutan Android Enterprise y Android quiosco en Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Se aplica a:
- Perfil de trabajo de Android Enterprise

### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111-idready---"></a>Habilitación del control de acceso a la red (NAC) con la VPN de Cisco AnyConnect en dispositivos iOS<!-- 4860111 idready -->
En dispositivos iOS, puede crear un perfil de VPN y usar tipos de conexión diferentes, entre los que se incluyen Cisco AnyConnect (**configuración de dispositivo** > **perfiles** > **crear perfil** > **iOS** para platform > **VPN** para el tipo de perfil > **Cisco AnyConnect** para el tipo de conexión). 

En una actualización futura, podrá habilitar el control de acceso a la red (NAC) con Cisco AnyConnect. Para usar esta característica,:

1. En la [Guía del administrador del motor de Cisco Identity Services](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html), siga los pasos que se describen en configuración de **Microsoft Intune como un servidor MDM** para configurar el motor de Cisco Identity Services (ISE) en Azure.
2. En el perfil de configuración de dispositivos de Intune, seleccione la opción **habilitar Access Control de red (NAC)** .

Para ver todas las opciones de configuración de VPN disponibles, vaya a configuración [de VPN en dispositivos iOS](../configuration/vpn-settings-ios.md).

Se aplica a:
- iOS

### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578-idready---"></a>Experiencia de inicio de sesión único actualizada para aplicaciones y sitios web en dispositivos iOS, iPados y macOS<!-- 4999578 idready -->
Intune está agregando más opciones de configuración de inicio de sesión único para iOS, iPados y dispositivos macOS. Actualmente, puede configurar las extensiones de aplicación de SSO de credenciales y la extensión integrada de Kerberos de Apple en Intune. En una actualización futura, podrá configurar las extensiones de aplicación de SSO de redirección escritas por su organización o por el proveedor de identidades. 

Use estas opciones para configurar una experiencia de inicio de sesión único de conexión directa para aplicaciones y sitios web que usan métodos de autenticación modernos, como OAuth y SAML2. 

Para ver la configuración de la extensión de la aplicación de SSO que puede configurar, vaya a Inicio [de sesión único en iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) y [SSO en MacOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

Se aplica a:
- iOS/iPadOS
- macOS

### <a name="require-use-of-approved-keyboards-on-android--4761794-idready---"></a>Requerir el uso de teclados aprobados en Android<!--4761794 IDready -->
Podrá especificar una lista de teclados aprobados para su uso en aplicaciones Android administradas. Desde la aplicación administrada, se solicitará al usuario que cambie a uno de los teclados aprobados que ya están instalados en el dispositivo o, si es necesario, se le dirigirá al Google Play Store para descargar y configurar uno de los teclados aprobados. El usuario solo podrá editar los campos de texto en una aplicación administrada si su teclado activo es uno de los teclados aprobados.

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices---3246388----"></a>Uso de certificados PKCS con perfiles de Wi-Fi en dispositivos Windows 10 y versiones posteriores<!-- 3246388  -->
Actualmente, puede autenticar los perfiles de Wi-Fi de Windows con certificados SCEP (**configuración de dispositivos** > **perfiles** > **crear un perfil** > **Windows 10 y versiones posteriores** para la plataforma > **Wi-Fi** para tipo de perfil > **tipo de EAP**de > **empresarial** ). Podrá usar certificados PKCS con los perfiles de Wi-Fi de Windows. Esta característica permite a los usuarios autenticar perfiles de Wi-Fi mediante perfiles de certificado PKCS nuevos o existentes en el inquilino. 

Para obtener más información sobre los perfiles de Wi-Fi, consulte [Agregar configuración de Wi-Fi para dispositivos Windows 10 y versiones posteriores en Intune](../configuration/wi-fi-settings-windows.md).

Se aplica a:
- Windows 10 y versiones posteriores

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824----"></a>Nueva configuración de ExchangeActiveSync al crear un perfil de configuración de dispositivo de correo electrónico en dispositivos iOS<!-- 4892824  --> 
En dispositivos iOS/iPados, puede configurar la conectividad de correo electrónico en un perfil de configuración de dispositivo (**configuración de dispositivo** > **perfiles** > **crear perfil** > **iOS/ipad** para el **correo electrónico** de plataforma > para el tipo de perfil). 

Habrá nuevas opciones de configuración de ExchangeActiveSync disponibles, entre las que se incluyen:
- Elija los servicios que desea sincronizar (o bloquear la sincronización), como correo electrónico, calendario y contactos.
- Permita (o bloquee) a los usuarios cambiar la configuración de sincronización para estos servicios en sus dispositivos. 

Para ver la configuración actual, vaya a [configuración de Perfil de correo electrónico para dispositivos iOS en Intune](../configuration/email-settings-ios.md).

Se aplica a:
- iOS 13.0 y versiones más recientes
- IPadOS 13.0 y versiones más recientes

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices---5353228----"></a>Impedir que los usuarios agreguen cuentas personales de Google al propietario del dispositivo de Android y a los dispositivos dedicados<!-- 5353228  -->
Podrá evitar que los usuarios creen cuentas personales de Google en el propietario del dispositivo de Android Enterprise y en los dispositivos dedicados (**configuración del dispositivo** > **perfiles** > **crear un perfil** > **Android Enterprise** para la plataforma > **propietario del dispositivo solo > restricciones de dispositivo** para el tipo de perfil > la configuración de **usuarios y cuentas**).

Para ver los valores actuales que puede configurar, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](../configuration/device-restrictions-android-for-work.md).

Se aplica a:
- Propietario del dispositivo Android Enterprise
- Dispositivos Android Enterprise dedicados

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile---5468501----"></a>Se ha quitado el valor de registro del lado servidor para comandos Siri en el perfil de restricciones de dispositivos iOS<!-- 5468501  -->
En los dispositivos iOS, puede crear perfiles de restricciones de dispositivo que configure el registro del lado servidor para los comandos de Siri (**configuración del dispositivo** > **perfiles** > **crear perfil** > **iOS/ipados** para la plataforma > **Restricciones de dispositivo** para el tipo de perfil > **aplicaciones integradas**). Se quitará el valor **de configuración de registro del lado servidor para comandos Siri** .

Esta configuración se quitará de la consola de administración de Intune. Esta configuración no tiene ningún efecto en el dispositivo, aunque las directivas existentes que tienen configurada esta configuración seguirán mostrando el valor. Si desea quitar la configuración de las directivas existentes, vaya a la Directiva, haga una edición menor, guárdela y la Directiva se actualizará.

Para ver los valores que puede configurar, vea [Configuración de dispositivos iOS e iPadOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-ios.md).

Se aplica a:
- iOS

<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
<!--## Device management-->


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Supervisión y solución de problemas

### <a name="centralized-audit-logs--5603185-5697164--"></a>Registros de auditoría centralizados<!--5603185, 5697164-->
Una nueva experiencia de registro de auditoría centralizada recopilará los registros de auditoría de todas las categorías en una sola página. You'l puede filtrar los registros para obtener los datos que está buscando. Para ver los registros de auditoría, vaya a **Administración de inquilinos** > **registros de auditoría**. Para obtener más información, consulte [próximos cambios en los registros de auditoría en Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Upcoming-change-to-Audit-logs-in-Intune/ba-p/1015858).

<!-- ***********************************************-->
<!--## Role-based access control-->


<!-- ***********************************************-->

## <a name="security"></a>Seguridad

### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529-idready---"></a>Usar perfiles de certificado PKCS para aprovisionar dispositivos con certificados<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529 IDready -->
Podrá usar un perfil de certificado PKCS para emitir certificados a los dispositivos y ampliar la compatibilidad actual con los certificados basados en usuario. Los certificados basados en dispositivos serán compatibles con las plataformas Android, iOS y Windows, y se pueden usar para perfiles de Wi-Fi y VPN.

<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


