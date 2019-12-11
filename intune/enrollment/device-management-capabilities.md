---
title: Capacidades de administración de dispositivos en Microsoft Intune
description: Lea este tema para averiguar cómo puede ayudar Intune a administrar los dispositivos que inscriba.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 64df7ccad203109c201b0e18c3d20023690e31aa
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503230"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Funcionalidades de administración de dispositivos inscritos en Microsoft Intune

Microsoft Intune le permite administrar una variedad de dispositivos si los *inscribe* en el servicio. Puede inscribir algunos tipos de dispositivos o los usuarios pueden inscribirlos mediante la aplicación *Portal de empresa*. La inscripción permite explorar e instalar aplicaciones, asegurarse de que los dispositivos cumplen con las directivas de la empresa y ponerse en contacto con el soporte técnico del departamento de TI.

En este artículo se facilita una lista completa de las funcionalidades que se le proporcionan después de la inscripción de los dispositivos.

La administración, el inventario, la implementación de aplicaciones, el aprovisionamiento y la retirada se controlan a través de Intune en Azure Portal.

Los usuarios obtienen acceso al Portal de empresa que les permite instalar aplicaciones, inscribir y quitar dispositivos, y ponerse en contacto con su departamento de TI o departamento de soporte técnico.



## <a name="device-security-and-configuration"></a>Seguridad y configuración de dispositivos

|Capacidad|Detalles|Más información|
|--------------|-----------|--------------------|
|Directivas de configuración<br><br>Directivas personalizadas| Le permiten administrar numerosas opciones y características de los dispositivos móviles de su organización. Por ejemplo, puede exigir una contraseña, limitar el número de intentos erróneos, limitar la cantidad de tiempo antes de que la pantalla se bloquee, establecer el plazo de expiración de una contraseña e impedir que se usen contraseñas que se han usado previamente. También puede controlar el uso de las características de hardware y software, como la cámara del dispositivo o el explorador web.<br><br>Use directivas personalizadas cuando las directivas de configuración no contengan la configuración que necesita. Para dispositivos iOS, puede importar la configuración que ha exportado desde la herramienta Apple Configurator. Para otros dispositivos, puede usar la configuración OMA-URI (identificador uniforme de recursos de Open Mobile Alliance) para configurar opciones y características en el dispositivo.|[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](../protect/device-compliance-get-started.md)|
|Eliminación remota, bloqueo remoto y restablecimiento de código de acceso|Borra información confidencial tras la pérdida o el robo de un dispositivo. Por ejemplo, puede bloquear el dispositivo de forma remota, restaurar la configuración de fábrica o borrar solo los datos corporativos.<br><br>Puede restablecer los códigos de acceso si los usuarios dejan de tener acceso a sus dispositivos, bloquear dispositivos extraviados o robados, e incluso borrar los datos de dispositivos extraviados o robados.|Ayudar a proteger los dispositivos con el [bloqueo remoto](../remote-actions/device-remote-lock.md) y el [restablecimiento de código de acceso](../remote-actions/device-passcode-reset.md)|
|Modo de quiosco|Le permite bloquear determinadas características de dispositivos móviles, como las capturas de pantalla y los interruptores de alimentación. También le permite restringir dispositivos para que ejecuten una única aplicación que especifique. |[Configuración de directivas de configuración de iOS en Microsoft Intune](../configuration/device-restrictions-ios.md)|
|Restablecimiento de Autopilot|Envía una tarea al dispositivo para iniciar el proceso de restablecimiento de forma remota, sin que así sea necesario que el personal de TI u otros administradores visiten cada máquina para iniciar el proceso. Al usarse el restablecimiento de Autopilot en un dispositivo, se quitará el usuario primario del dispositivo. El próximo usuario que inicie sesión tras el restablecimiento se establecerá como usuario primario.|[Restablecimiento remoto de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset#reset-devices-with-remote-windows-autopilot-reset)|

## <a name="app-management"></a>Administración de aplicaciones

|Capacidad|Detalles|Más información|
|--------------|-----------|--------------------|
|Administración e implementación de aplicaciones|Proporciona diversas herramientas que le ayudarán a administrar aplicaciones móviles durante todo su ciclo de vida, incluida la implementación de aplicaciones desde archivos de instalación y tiendas de aplicaciones, la supervisión detallada del estado de las aplicaciones y la eliminación de aplicaciones.|[Implementar aplicaciones en Microsoft Intune](../apps/apps-deploy.md)|
|Aplicaciones conformes y no conformes|Le permite especificar listas de aplicaciones conformes (que los usuarios pueden instalar) y aplicaciones no conformes (que los usuarios no pueden instalar).|[Configuración de directivas de iOS en Microsoft Intune](../configuration/device-restrictions-ios.md)|
|Administración de aplicaciones móviles|Use la administración de aplicaciones móviles para configurar restricciones para las aplicaciones, tanto en los dispositivos administrados con Intune como en los no administrados por Intune. Puede aumentar la seguridad de los datos de su compañía mediante la restricción de operaciones como copiar y pegar, la realización de copias de seguridad externas de los datos y la transferencia de datos entre las aplicaciones.|[Configurar e implementar directivas de administración de aplicaciones móviles en la consola de Microsoft Intune](../developer/app-wrapper-prepare-android.md)|
|Configuración de aplicaciones móviles iOS|Usa las directivas de configuración de aplicaciones móviles para proporcionar la configuración de aplicaciones iOS que puede ser necesaria cuando el usuario ejecuta la aplicación. Por ejemplo, una aplicación puede necesitar que el usuario especifique un número de puerto o la información de inicio de sesión. Puede simplificar la configuración de la aplicación y reducir el número de llamadas al servicio de soporte técnico.|[Configurar aplicaciones de iOS con directivas de configuración de aplicaciones móviles en Microsoft Intune](../apps/app-configuration-policies-use-ios.md)|
|Perfiles de aprovisionamiento de aplicaciones móviles iOS|Le ayuda a implementar el aprovisionamiento de perfiles en aplicaciones iOS que están a punto de expirar. |[Uso de directivas de perfil de aprovisionamiento móvil iOS para evitar que las aplicaciones expiren](../apps/app-provisioning-profile-ios.md)|
|Explorador administrado|Configura las directivas de explorador administrado para controlar los sitios web que los usuarios del dispositivo pueden visitar. Además, también puede aplicar directivas de administración de aplicaciones móviles al explorador administrado.|[Administrar el acceso a Internet mediante directivas de Managed Browser con Microsoft Intune](../apps/app-configuration-managed-browser.md)|
|Windows Hello para empresas|Le permite la integración con Windows Hello para empresas, que es un método de inicio de sesión alternativo para Windows 10 que usa Active Directory local o Azure Active Directory para reemplazar contraseñas, tarjetas inteligentes o tarjetas inteligentes virtuales.|[Controlar la configuración de Windows Hello para empresas en dispositivos que tienen Microsoft Intune](../protect/windows-hello.md)|
|Aplicaciones de programas de compras por volumen|Le ayuda a administrar las aplicaciones compradas mediante un programa de compras por volumen. Para ello, importa la información de licencia desde la App Store, efectúa el seguimiento de la cantidad de licencias usadas y le impide instalar más copias de la aplicación de las que posee.|[Administrar aplicaciones compradas por volumen con Microsoft Intune](../apps/vpp-apps.md)|

## <a name="company-resource-access"></a>Acceso a los recursos de la empresa

|Capacidad|Detalles|Más información|
|--------------|-----------|--------------------|
|Perfiles de certificado|Crea e implementa perfiles de certificado de confianza y certificados de protocolo de inscripción de certificados simple (SCEP) que pueden usarse para ayudar a proteger y autenticar los perfiles de Wi-Fi, VPN y correo electrónico.|[Proteger el acceso a recursos con perfiles de certificado en Microsoft Intune](../protect/certificates-configure.md)|
|Perfiles de Wi-Fi|Implementa la configuración de red inalámbrica para los usuarios. Mediante la implementación de esta configuración, se minimiza la intervención del usuario necesaria para conectarse a la red corporativa.|[Wi-Fi connections in Microsoft Intune](../configuration/wi-fi-settings-configure.md) (Conexiones Wi-Fi en Microsoft Intune)|
|Perfiles de correo electrónico|Esto crea e implementa la configuración de correo electrónico en los dispositivos para que los usuarios puedan acceder al correo electrónico corporativo en sus dispositivos personales sin tener que realizar ninguna configuración.|[Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico con Microsoft Intune](../configuration/email-settings-configure.md)|
|Perfiles de VPN|Implementa la configuración de VPN a los usuarios y dispositivos de su organización. Mediante la implementación de esta configuración, se minimiza la intervención del usuario necesaria para conectarse a los recursos de la red de la compañía.|[Conexiones VPN en Microsoft Intune](../configuration/device-profiles.md#vpn)|
|Directivas de acceso condicional|Administra el acceso al correo electrónico de Microsoft Exchange y SharePoint Online desde dispositivos que no se administran con Intune.|[Restringir el acceso al correo electrónico y SharePoint con Microsoft Intune](../protect/app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>Pasos siguientes

[Vea una lista de dispositivos que puede administrar](../remote-actions/device-management.md).
