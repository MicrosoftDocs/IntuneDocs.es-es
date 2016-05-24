---
# required metadata

title: Referencia de directivas de Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d27f2739-9791-4aae-a9db-01a4e59ccfe5

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Referencia de directivas de Microsoft Intune

Use la información de este tema para ayudarle a decidir qué directiva de Microsoft Intune debe usar para administrar los dispositivos.

> [!TIP]
> Para más información sobre cómo usar las directivas, consulte [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)..


## Directivas de configuración de Android

|Nombre de la directiva|Usar en los siguientes casos|
|---------------|------------------------|
|**Configuración personalizada (Android 4 y versiones posteriores, Samsung KNOX Standard 4.0 y versiones posteriores)**|Implementar la configuración de URI-OMA, como la configuración de Wi-Fi que puede usarse para controlar las características del dispositivo. Es útil cuando la configuración que necesita no está disponible en una directiva de configuración.<br /><br />Para más información, consulte [Android policy settings in Microsoft Intune](android-policy-settings-in-microsoft-intune.md) (Configuración de directivas personalizadas de Android en Microsoft Intune)..|
|**Perfil de correo electrónico (Samsung KNOX Standard 4.0 y posterior)**|Cree, implemente y supervise la configuración de correo electrónico de Exchange ActiveSync en los dispositivos administrados. Esto permite a los usuarios obtener acceso al correo electrónico corporativo en sus dispositivos personales sin tener que realizar ninguna configuración.<br /><br />Para más información, consulte [Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico con Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)..|
|**Configuración general (Android 4 y versiones posteriores, Samsung KNOX Standard 4.0 y versiones posteriores)**|Configurar opciones funcionales y de seguridad de dispositivos móviles.<br />Especificar las aplicaciones conformes y no conformes e informar del momento de su uso.<br />Configurar el modo de pantalla completa que bloquea los dispositivos para permitir que solo funcionen determinadas características como, por ejemplo, permitir que el dispositivo ejecute solo una aplicación o deshabilitar los botones de volumen.<br /><br />Para más información, consulte [Android policy settings in Microsoft Intune](android-policy-settings-in-microsoft-intune.md) (Configuración de directivas personalizadas de Android en Microsoft Intune)..|
|**Perfil de certificado PKCS n.º12 (.PFX) (Android 4 y versiones posteriores)**|Use este perfil para crear e implementar la configuración de PFX para las solicitudes de certificado de dispositivo.<br /><br />Para más información, consulte [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)..|
|**Perfil de certificado SCEP (Android 4 y versiones posteriores)**|Permite configurar un certificado de protocolo de inscripción de certificados simple que se puede utilizar con un certificado de dispositivo móvil de confianza para autenticar dispositivos móviles y permitirles acceder a los recursos de red, como los configurados por los perfiles de Wi-Fi y VPN.<br /><br />Para más información, consulte [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)..|
|**Perfil de certificado de confianza (Android 4 y versiones posteriores)**|Configure un certificado de dispositivo móvil de confianza que se puede usar para autenticar dispositivos móviles y permitirles acceder a los recursos de red como los configurados por los perfiles de Wi-Fi y VPN.<br /><br />Para más información, consulte [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)..|
|**Perfil de VPN (Android 4 y versiones posteriores)**|Configure e implemente configuraciones que proporcionen a los usuarios un acceso seguro a la red de su empresa desde sus dispositivos móviles. Mediante la implementación de esta configuración, se minimiza la intervención del usuario final necesaria para conectarse a su trabajo.<br /><br />Para más información, consulte [VPN connections in Microsoft Intune](vpn-connections-in-microsoft-intune.md) (Conexiones VPN en Microsoft Intune)..|
|**Perfil de Wi-Fi (Android 4 y versiones posteriores)**|Configure e implemente configuraciones de red inalámbrica para los usuarios de su organización. Mediante la implementación de estas opciones, se minimiza la intervención del usuario final necesaria para conectarse a la red inalámbrica.<br /><br />Para más información, consulte [Wi-Fi connections in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md) (Conexiones Wi-Fi en Microsoft Intune)..|

## Directivas de configuración de iOS

|Nombre de la directiva|Usar en los siguientes casos|
|---------------|------------------------|
|**Configuración personalizada (iOS 7.1 y versiones posteriores)**|Implemente los perfiles de configuración en dispositivos iOS que creó utilizando la herramienta de configuración de Apple. Es útil cuando la configuración que necesita no está disponible en una directiva de configuración.<br /><br />Para obtener más información, consulte [Configuración de directivas de iOS en Microsoft Intune](ios-policy-settings-in-microsoft-intune.md)..|
|**Perfil de correo electrónico (iOS 7.1 y versiones posteriores)**|Cree, implemente y supervise la configuración de correo electrónico de Exchange ActiveSync en los dispositivos administrados. Esto permite a los usuarios obtener acceso al correo electrónico corporativo en sus dispositivos personales sin tener que realizar ninguna configuración.<br /><br />Para más información, consulte [Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico con Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)..|
|**Configuración general (iOS 7.1 y versiones posteriores)**|Configurar opciones funcionales y de seguridad de dispositivos móviles.<br />-   Especificar las aplicaciones compatibles y no compatibles e informar del momento de su uso.<br />Configurar el modo de pantalla completa que bloquea los dispositivos para permitir que solo funcionen determinadas características como, por ejemplo, permitir que el dispositivo ejecute solo una aplicación o deshabilitar los botones de volumen.<br /><br />Para obtener más información, consulte [Configuración de directivas de iOS en Microsoft Intune](ios-policy-settings-in-microsoft-intune.md)..|
|**Perfil de certificado de SCEP (iOS 7.1 y versiones posteriores)**|Permite configurar un certificado de protocolo de inscripción de certificados simple que se puede utilizar con un certificado de dispositivo móvil de confianza para autenticar dispositivos móviles y permitirles acceder a los recursos de red, como los configurados por los perfiles de Wi-Fi y VPN.<br /><br />Para más información, consulte [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)..|
|**Perfil de certificado de confianza (iOS 7.1 y versiones posteriores)**|Configure un certificado de dispositivo móvil de confianza que se puede usar para autenticar dispositivos móviles y permitirles acceder a los recursos de red como los configurados por los perfiles de Wi-Fi y VPN.<br /><br />Para más información, consulte [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)..|
|**Perfil de VPN (iOS 7.1 y versiones posteriores)**|Configure e implemente configuraciones que proporcionen a los usuarios un acceso seguro a la red de su empresa desde sus dispositivos móviles. Mediante la implementación de esta configuración, se minimiza la intervención del usuario final necesaria para conectarse a su trabajo.<br /><br />Para más información, consulte [VPN connections in Microsoft Intune](vpn-connections-in-microsoft-intune.md) (Conexiones VPN en Microsoft Intune)..|
|**Perfil de Wi-Fi (iOS 7.1 y versiones posteriores)**|Configure e implemente configuraciones de red inalámbrica para los usuarios de su organización. Mediante la implementación de estas opciones, se minimiza la intervención del usuario final necesaria para conectarse a la red inalámbrica.<br /><br />Para más información, consulte [Wi-Fi connections in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md) (Conexiones Wi-Fi en Microsoft Intune)..|
|**Directiva de configuración de aplicaciones móviles (iOS 7.1 y versiones posteriores)**|Use directivas de configuración de aplicaciones móviles para proporcionar automáticamente la configuración que podría ser necesaria cuando el usuario ejecuta una aplicación de iOS.<br /><br />Para obtener más información, consulte [Configure iOS apps with mobile app configuration policies in Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md) (Configurar aplicaciones iOS con directivas de configuración de aplicaciones móviles en Microsoft Intune)..|

## Directivas de configuración de Mac OS X

|Nombre de la directiva|Usar en los siguientes casos|
|---------------|------------------------|
|**Configuración personalizada (Mac OS X 10.9 y versiones posteriores)**|Implemente los perfiles de configuración en los equipos Mac que creó mediante la herramienta de configuración de Apple. Es útil cuando la configuración que necesita no está disponible en una directiva de configuración.<br /><br />Para más información, consulte [Mac OS X policy settings in Microsoft Intune](mac-os-x-policy-settings-in-microsoft-intune.md) (Configuración de directivas de Mac OS X en Microsoft Intune)..|
|**Configuración general (Mac OS X 10.9 y versiones posteriores)**|Configurar opciones funcionales y de seguridad de dispositivos móviles.<br />Especificar las aplicaciones conformes y no conformes e informar del momento de su uso.<br /><br />Para más información, consulte [Mac OS X policy settings in Microsoft Intune](mac-os-x-policy-settings-in-microsoft-intune.md) (Configuración de directivas de Mac OS X en Microsoft Intune)..|
|**Perfil de certificado SCEP (Mac OS X 10.9 y versiones posteriores)**|Permite configurar un certificado de protocolo de inscripción de certificados simple que se puede utilizar con un certificado de dispositivo móvil de confianza para autenticar dispositivos móviles y permitirles acceder a los recursos de red, como los configurados por los perfiles de Wi-Fi y VPN.<br /><br />Para más información, consulte [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)..|
|**Perfil de certificado de confianza (Mac OS X 10.9 y versiones posteriores)**|Configure un certificado de dispositivo móvil de confianza que se puede usar para autenticar dispositivos móviles y permitirles acceder a los recursos de red como los configurados por los perfiles de Wi-Fi y VPN.<br /><br />Para más información, consulte [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)..|
|**Perfil de VPN (Mac OS X 10.9 y versiones posteriores)**|Configure e implemente configuraciones que proporcionen a los usuarios un acceso seguro a la red de su empresa desde sus dispositivos móviles. Mediante la implementación de esta configuración, se minimiza la intervención del usuario final necesaria para conectarse a su trabajo.<br /><br />Para más información, consulte [VPN connections in Microsoft Intune](vpn-connections-in-microsoft-intune.md) (Conexiones VPN en Microsoft Intune)..|
|**Perfil de Wi-Fi (Mac OS X 10.9 y versiones posteriores)**|Configure e implemente configuraciones de red inalámbrica para los usuarios de su organización. Mediante la implementación de estas opciones, se minimiza la intervención del usuario final necesaria para conectarse a la red inalámbrica.<br /><br />Para más información, consulte [Wi-Fi connections in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md) (Conexiones Wi-Fi en Microsoft Intune)..|

## Directivas de configuración de Windows
Se aplica únicamente a dispositivos Windows Phone y Windows inscritos.

|Nombre de la directiva|Usar en los siguientes casos|
|---------------|------------------------|
|**Configuración personalizada (Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores)**|Implementar la configuración de URI-OMA que puede usarse para controlar las características del dispositivo. Es útil cuando la configuración que necesita no está disponible en una directiva de configuración.<br />    Para más información, consulte [Windows 10 policy settings in Microsoft Intune](windows-10-policy-settings-in-microsoft-intune.md) (Configuración de directivas de Windows 10 en Microsoft Intune)..|
|**Configuración personalizada (Windows Phone 8.1 y versiones posteriores)**|Implementar la configuración de URI-OMA que puede usarse para controlar las características del dispositivo. Es útil cuando la configuración que necesita no está disponible en una directiva de configuración.<br /><br />Para más información, consulte [Windows Phone 8.1 settings in Microsoft Intune](windows-phone-8-1-policy-settings-in-microsoft-intune.md) (Configuración de Windows Phone 8.1 en Microsoft Intune)..|
|**Directiva de actualización de edición (Windows 10 de escritorio y versiones posteriores)**<br><br>**Directiva de actualización de edición (Windows 10 Holographic y versiones posteriores)**|Configurar e implementar directivas que contengan información de clave de producto o de licencia usada para actualizar los dispositivos de Windows 10 a una versión más reciente.<br><br>Para más información, consulte [Configuración de directivas de actualización de edición en Microsoft Intune](edition-upgrade-policy-settings-in-microsoft-intune.md)..|  
|**Perfil de correo electrónico (Windows Phone 8 y versiones posteriores)**<br /><br />**Perfil de correo electrónico (Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores)**|Cree, implemente y supervise la configuración de correo electrónico de Exchange ActiveSync en los dispositivos administrados. Esto permite a los usuarios obtener acceso al correo electrónico corporativo en sus dispositivos personales sin tener que realizar ninguna configuración.<br /><br />Para más información, consulte [Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico con Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)..|
|**Configuración general (Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores)**|Configure las funciones y la seguridad en dispositivos móviles para los equipos Windows 10 de escritorio y Windows 10 Mobile inscritos.<br /><br />Para más información, consulte [Windows 10 policy settings in Microsoft Intune](windows-10-policy-settings-in-microsoft-intune.md) (Configuración de directivas de Windows 10 en Microsoft Intune)..|
|**Configuración general (Windows 10 Team y versiones posteriores)**|Configurar la seguridad de los dispositivos y las opciones funcionales para dispositivos Windows 10 Team inscritos (por ejemplo, un dispositivo Surface Hub).<br /><br />Para más información, consulte [Configuración de directivas de configuración de Equipo de Windows en Microsoft Intune](windows-team-configuration-policy-settings-in-microsoft-intune.md)..|
|**Configuración general (Windows 8.1 y versiones posteriores)**|Configurar la seguridad en dispositivos móviles y la configuración funcional para dispositivos Windows inscritos.<br /><br />Para más información, consulte [Windows policy settings in Microsoft Intune](windows-configuration-policy-settings-in-microsoft-intune.md) (Configuración de directivas de Windows en Microsoft Intune)..|
|**Configuración general (Windows Phone 8.1 y versiones posteriores)**|Configurar opciones funcionales y de seguridad de dispositivos móviles.<br />Especifique especificar las aplicaciones que los usuarios pueden o no usar en dispositivos, e impida que se instalen o se usen aplicaciones no conformes.<br /><br />Para más información, consulte [Windows Phone 8.1 settings in Microsoft Intune](windows-phone-8-1-policy-settings-in-microsoft-intune.md) (Configuración de Windows Phone 8.1 en Microsoft Intune)..|
|**Perfil de certificado PKCS n.º12 (.PFX) (Windows 10 para escritorio y Windows 10 Mobile y versiones posteriores)**|Use este perfil para crear e implementar la configuración de PFX para las solicitudes de certificado de dispositivo.<br /><br />Para más información, consulte [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)..|
|**Perfil de certificado SCEP (Windows 8.1 y versiones posteriores)**<br /><br />**Perfil de certificado SCEP (Windows Phone 8.1 y versiones posteriores)**|Permite configurar un certificado de protocolo de inscripción de certificados simple que se puede utilizar con un certificado de dispositivo móvil de confianza para autenticar dispositivos móviles y permitirles acceder a los recursos de red, como los configurados por los perfiles de Wi-Fi y VPN.<br /><br />Para más información, consulte [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)..|
|**Perfil de certificado de confianza (Windows 8.1 y versiones posteriores)**<br /><br />**Perfil de certificado de confianza (Windows Phone 8.1 y versiones posteriores)**|Configure un certificado de dispositivo móvil de confianza que se puede usar para autenticar dispositivos móviles y permitirles acceder a los recursos de red como los configurados por los perfiles de Wi-Fi y VPN.<br /><br />Para más información, consulte [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md) (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune).).|
|**Perfil de VPN (Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores)**<br /><br />**Perfil de VPN (Windows 8.1 y versiones posteriores)**<br /><br />**Perfil de VPN (Windows Phone 8.1 y versiones posteriores)**|Configure e implemente configuraciones que proporcionen a los usuarios un acceso seguro a la red de su empresa desde sus dispositivos móviles. Mediante la implementación de esta configuración, se minimiza la intervención del usuario final necesaria para conectarse a su trabajo.<br /><br />Para más información, consulte [VPN connections in Microsoft Intune](vpn-connections-in-microsoft-intune.md) (Conexiones VPN en Microsoft Intune)..|
|**Importación de Wi-Fi**|Importe e implemente configuraciones de Windows Wi-Fi que haya exportado previamente a un archivo.<br /><br />Para más información, consulte [Wi-Fi connections in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md) (Conexiones Wi-Fi en Microsoft Intune)..|

## Directivas de software

|Nombre de la directiva|Usar en los siguientes casos|
|---------------|------------------------|
|**Directiva de explorador administrado (Android 4 y posterior)**<br /><br />**Directiva de explorador administrado (iOS 7.1 y versiones posteriores)**|Especifique los sitios web a los que los usuarios pueden acceder y a los que no cuando usen la aplicación de explorador administrado.<br /><br />Para más información, consulte [Administrar el acceso a Internet mediante directivas de explorador administrado con Microsoft Intune](manage-internet-access-using-managed-browser-policies.md)..|
|**Directiva de administración de aplicaciones móviles (Android 4 y posterior)**<br /><br />**Directiva de administración de aplicaciones móviles (iOS 7.1 y versiones posteriores)**|Modifique la funcionalidad de las aplicaciones que implementa para que se ajusten a los requisitos de cumplimiento y las directivas de seguridad de su empresa. Por ejemplo, puede limitar las funcionalidades de cortar, copiar y pegar dentro de una aplicación restringida, o configurar una aplicación para abrir todos los vínculos web dentro del explorador administrado.<br /><br />Para más información, consulte [Configure and deploy mobile application management policies in the Microsoft Intune console](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) (Configurar e implementar directivas de administración de aplicaciones móviles en la consola de Microsoft Intune).|

## Configuración de dispositivo móvil común

|Nombre de la directiva|Usar en los siguientes casos|
|---------------|------------------------|
|**Directiva de Exchange ActiveSync**|Configurar la seguridad en dispositivos móviles y la configuración funcional en dispositivos administrados con Exchange ActiveSync.<br /><br />Para más información, consulte [Configuración de directivas de Exchange ActiveSync en Microsoft Intune](exchange-activesync-policy-settings-in-microsoft-intune.md)..|
|**Directiva de seguridad de dispositivos móviles**|<ul><li>Configura las opciones para dispositivos móviles (todas las plataformas), incluyendo:<br /><br /><ul><li>Seguridad</li><li>Cifrado</li><li>System</li><li>Correo electrónico</li><li>Aplicaciones</li></ul></li></ul> **Importante:** Microsoft Intune ofrece ahora **directivas de configuración** independientes para cada plataforma de dispositivo. Estas directivas contienen la configuración más actualizada que se puede usar. Aún puede usar la directiva de seguridad de dispositivos móviles y las implementaciones existentes seguirán funcionando, pero debe planear la migración a las nuevas directivas de configuración tan pronto como sea posible.<br />Para más información, consulte [Configuración de directivas de seguridad de dispositivos móviles en Microsoft Intune](mobile-device-security-policy-settings-in-microsoft-intune.md)..|

## Directivas de acceso condicional y cumplimiento

### Acceso condicional

|Nombre de la directiva|Usar en los siguientes casos|
|---------------|------------------------|
|**Directiva de Exchange Online**<br /><br />**Directiva local de Exchange**|Administrar el acceso al correo electrónico de Microsoft Exchange desde dispositivos no administrados con Intune o no compatibles con alguna de las directivas de cumplimiento que ha creado.<br /><br />Para más información, consulte [Restrict email access to Exchange Online and new Exchange Online Dedicated environment with Intune](restrict-access-to-exchange-online-with-microsoft-intune.md) (Restringir el acceso de correo electrónico a Exchange Online y nuevo Exchange Online dedicado)..|
|**Directiva de SharePoint Online**|Administrar el acceso a SharePoint Online desde dispositivos no administrados con Intune o no compatibles con alguna de las directivas de cumplimiento que ha creado.<br /><br />Para más información, consulte [Restrict access to SharePoint Online with Microsoft Intune](restrict-access-to-sharepoint-online-with-microsoft-intune.md) (Restringir el acceso a SharePoint Online con Microsoft Intune)..|
|**Skype Empresarial**|Administrar el acceso a Skype Empresarial desde dispositivos no administrados con Intune o no compatibles con alguna de las directivas de cumplimiento que ha creado.<br /><br />Para más información, consulte [Restrict access to Skype for Business with Microsoft Intune](restrict-access-to-skype-for-business-online-with-microsoft-intune.md) (Restringir el acceso a Skype Empresarial Online con Microsoft Intune)..|
> [!NOTE]
> No implemente directivas de acceso condicional para usuarios y dispositivos. En su lugar, configure la directiva necesaria que se aplicará a todos los grupos de destino de la directiva.

### Directivas de cumplimiento

|Nombre de la directiva|Usar en los siguientes casos|
|---------------|------------------------|
|**Directivas de cumplimiento**|Definir el nivel de cumplimiento de los dispositivos y, a continuación, informar acerca de los dispositivos no conformes. Estas directivas se usan con acceso condicional para ayudar a evaluar los dispositivos cuyo acceso a determinados servicios se debe bloquear.<br /><br />Para más información, consulte [Device compliance policies in Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md) (Directivas de cumplimiento de dispositivos de Microsoft Intune)..|

## Administración de PC Windows

|Nombre de la directiva|Usar en los siguientes casos|
|---------------|------------------------|
|**Configuración del agente de Microsoft Intune**|Configurar el cliente PC de Intune en equipos, incluida la configuración de:<br /><br />-   Endpoint Protection<br />-   Actualizaciones de software<br />-   Programación de comprobación de directiva<br /><br />Este tipo de directiva se puede implementar únicamente para grupos de dispositivos.<br /><br />Los clientes de Intune descargan una directiva nueva y actualizada según el valor de **Frecuencia de detección de la aplicación y la actualización**, que es 8 horas de forma predeterminada. Sin embargo, puede forzar en cualquier momento la actualización de la directiva en los equipos.<br /><br />Para más información, consulte [Mantener los equipos Windows al día con las actualizaciones de software de Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)..|
|**Configuración de Microsoft Intune Center**|Configurar los detalles que aparecen en el Microsoft Intune Center en los equipos administrados.<br /><br />Este tipo de directiva se puede implementar únicamente para grupos de dispositivos.<br /><br />Para más información, consulte [Tareas comunes de administración de PC Windows con el cliente de equipo de Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)..|
|**Configuración del firewall de Windows**|Configura las opciones y las excepciones de Firewall de Windows para las comunicaciones de red comunes en los equipos, incluidas:<br /><br />-   BranchCache<br />-   Asistencia remota<br />-   Uso compartido de multimedia<br /><br />Este tipo de directiva se puede implementar únicamente para grupos de dispositivos.<br /><br />Para más información, consulte [Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)..|

### Véase también

[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


