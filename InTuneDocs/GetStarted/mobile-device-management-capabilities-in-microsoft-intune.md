---
# required metadata

title: Capacidades de administración de dispositivos móviles | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
# Funcionalidades de administración de dispositivos móviles en Microsoft Intune

Microsoft Intune le permite administrar una variedad de dispositivos si los *inscribe* en el servicio. Tras la inscripción, los usuarios pueden usar un *portal de la empresa* para realizar diversas operaciones, como inscribir sus dispositivos, examinar e instalar aplicaciones, garantizar que los dispositivos cumplen con las directivas de la empresa y ponerse en contacto con el equipo de TI.
En este tema se facilita una lista completa de las funcionalidades que le proporciona la inscripción de dispositivos.

La administración, el inventario, la implementación de aplicaciones, el aprovisionamiento y la retirada se controlan a través de la consola de administración de Intune. Los usuarios obtienen acceso al portal de empresa que les permite instalar aplicaciones, inscribir y quitar dispositivos, y les ayuda a ponerse en contacto con su departamento de TI o departamento de soporte técnico.



## Seguridad y configuración de dispositivos

|Capacidad|Detalles|Más información|
|--------------|-----------|--------------------|
|Directivas de configuración<br><br>Directivas personalizadas|Las directivas de configuración de dispositivos móviles permiten administrar numerosas opciones y características de los dispositivos móviles de su organización. Por ejemplo, puede exigir una contraseña, limitar el número de intentos erróneos, limitar los minutos antes de que la pantalla se bloquee, establecer el plazo de expiración de una contraseña e impedir que se usen contraseñas usadas previamente. También puede controlar el uso de las características de hardware y software, como la cámara del dispositivo o el explorador web.<br><br>Use directivas personalizadas cuando las directivas de configuración no contengan la configuración que necesita. Para dispositivos iOS, puede importar la configuración exportada desde la herramienta Apple Configurator. Para otros dispositivos, puede usar la configuración OMA-URI para configurar opciones y características en el dispositivo.|[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)<br />|
|Eliminación remota, bloqueo remoto y restablecimiento de código de acceso|Borrar información confidencial tras la pérdida o el robo de un dispositivo. Por ejemplo, puede bloquear el dispositivo de forma remota, restaurar la configuración de fábrica o borrar solo los datos corporativos.<br>Puede restablecer los códigos de acceso si los usuarios dejan de tener acceso a sus dispositivos, bloquear dispositivos extraviados o robados, e incluso borrar los datos de dispositivos extraviados o robados.|[Help protect your devices with remote lock and passcode reset](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune) (Ayudar a proteger los dispositivos con el restablecimiento de contraseña y el bloqueo remoto) y [Retire devices from Intune management](/intune/deploy-use/retire-devices-from-microsoft-intune-management)(Retirar dispositivos de la administración de Intune)|
|Modo de quiosco|Le permite bloquear determinadas características de dispositivos móviles, como la funcionalidad de captura de pantalla y el interruptor de alimentación. También le permite restringir dispositivos para que ejecuten una única aplicación que especifique.|[Configuración de directivas de configuración de iOS en Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|

## Administración de aplicaciones

|Capacidad|Detalles|Más información|
|--------------|-----------|--------------------|
|Administración e implementación de aplicaciones|Proporciona diversas herramientas que le ayudarán a administrar aplicaciones móviles durante todo su ciclo de vida, incluida la implementación de aplicaciones desde archivos de instalación y tiendas de aplicaciones, la supervisión detallada del estado de las aplicaciones y la eliminación de aplicaciones.|[Deploy apps in Microsoft Intune (Implementar aplicaciones en Microsoft Intune)](/intune/deploy-use/deploy-apps)|
|Aplicaciones conformes y no conformes|Le permite especificar listas de aplicaciones conformes (que los usuarios pueden instalar) y aplicaciones no conformes (que los usuarios no deben instalar).|[Configuración de directivas de iOS en Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|
|Administración de aplicaciones móviles|Use la administración de aplicaciones móviles para configurar restricciones para las aplicaciones, tanto en los dispositivos administrados con Intune como en los no administrados por Intune. Esto contribuye a aumentar la seguridad de los datos de su empresa mediante la restricción de operaciones como la funcionalidad de copiar y pegar, la realización de copias de seguridad externas de los datos y la transferencia de datos entre las aplicaciones.|[Configure and deploy mobile application management policies in the Microsoft Intune console](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)<br><br>[Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)<br /><br />[Preparar aplicaciones iOS para la administración de aplicaciones móviles con la herramienta de ajuste de aplicaciones de Microsoft Intune](/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)<br /><br />[Preparar aplicaciones de Android para la administración de aplicaciones móviles con Microsoft Intune App Wrapping Tool](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)|
|Configuración de aplicaciones móviles|Use las directivas de configuración de aplicaciones móviles para proporcionar la configuración de aplicaciones iOS que puede ser necesaria cuando el usuario ejecuta la aplicación. Por ejemplo, una aplicación puede necesitar que el usuario especifique un número de puerto de la información de inicio de sesión. Esto puede ayudar a simplificar la configuración de la aplicación y reducir el número de llamadas al soporte técnico.|[Configurar aplicaciones de iOS con directivas de configuración de aplicaciones móviles en Microsoft Intune](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|Explorador administrado|Tras implementar el explorador administrado para los usuarios, puede configurar una directiva de explorador administrado para controlar los sitios web que pueden visitar. Además, también puede aplicar directivas de administración de aplicaciones móviles al explorador administrado.|[Administrar el acceso a Internet mediante directivas de explorador administrado con Microsoft Intune](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Microsoft Passport|Con Intune, es posible la integración con Microsoft Passport for Work, que es un método de inicio de sesión alternativo para Windows 10 que usa Active Directory, o una cuenta de Azure Active Directory, para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual.|[Controlar la configuración de Microsoft Passport en dispositivos mediante Microsoft Intune](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|

## Acceso a los recursos de la empresa

|Capacidad|Detalles|Más información|
|--------------|-----------|--------------------|
|Perfiles de certificado|Permite crear e implementar perfiles de certificado de confianza y certificados de protocolo de inscripción de certificados simple (SCEP) que pueden utilizarse para ayudar a proteger y autenticar los perfiles de Wi-Fi, VPN y correo electrónico.|[Secure resource access with certificate profiles in Microsoft Intune (Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune)](/intune/deploy-use/secure-resource-access-with-certificate-profiles)|
|Perfiles de Wi-Fi|Implementar la configuración de red inalámbrica para los usuarios. Mediante la implementación de esta configuración, se minimiza la intervención del usuario final necesaria para conectarse a la red corporativa.|[Wi-Fi connections in Microsoft Intune (Conexiones Wi-Fi en Microsoft Intune)](/intune/deploy-use/wi-fi-connections-in-microsoft-intune)|
|Perfiles de correo electrónico|Crear e implementar la configuración de correo electrónico para los dispositivos. Esto permite a los usuarios obtener acceso al correo electrónico corporativo en sus dispositivos personales sin tener que realizar ninguna configuración.|[Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico con Microsoft Intune](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|Perfiles de VPN|Permite implementar la configuración de VPN a los usuarios y dispositivos de su organización. Mediante la implementación de esta configuración, se minimiza la intervención del usuario final necesaria para conectarse a los recursos de la red de la empresa.|[VPN connections in Microsoft Intune (Conexiones VPN en Microsoft Intune)](/intune/deploy-use/vpn-connections-in-microsoft-intune)|
|Directivas de acceso condicional|Administre el acceso al correo electrónico de Microsoft Exchange y SharePoint Online desde dispositivos que no se administren con Intune.|[Restrict access to email and SharePoint with Microsoft Intune (Restringir el acceso al correo electrónico y SharePoint con Microsoft Intune)](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## Inventario e informes

|Capacidad|Detalles|Más información|
|--------------|-----------|--------------------|
|Inventario e informes|Obtenga información acerca de los dispositivos que usted administra y el software que estos utilizan.|[Comprender el funcionamiento de sus dispositivos mediante el inventario en Microsoft Intune](./deploy-use/understand-your-devices-with-inventory-in-microsoft-intune)|


### Consulte también
[Funciones de administración de equipos Windows en Microsoft Intune](./windows-pc-management-capabilities-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


