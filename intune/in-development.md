---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7bba992c79f69a126f0199d9cdac52779910ff38
ms.sourcegitcommit: 068c4e4bc6e6d778ece4a83d000128c4d2b732db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910328"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>En desarrollo para Microsoft Intune: mayo de 2019

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


<!-- 1905 start-->


### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Reflejo de la eliminación de un dispositivo del portal de Apple en el portal de Intune <!--2489996 -->
Si se elimina un dispositivo de los portales del Programa de inscripción de dispositivos de Apple o de Apple Business Manager, el dispositivo se eliminará automáticamente de Intune durante la siguiente sincronización.

### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Compatibilidad con la línea de base para la búsqueda de palabras clave  <!-- 3082036         -->
Al crear o editar un perfil de línea de base de seguridad, pronto se podrá usar la *búsqueda* para filtrar la configuración que se muestra en la consola.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Restablecimiento y borrado de dispositivos de forma masiva mediante Graph API <!-- 3295288 -->
Podrá restablecer y borrar hasta 100 dispositivos de forma masiva mediante Graph API.

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Buscar un conjunto de chips TPM en una directiva de cumplimiento de dispositivos Windows 10 <!-- 3617671 -->
Muchos dispositivos Windows 10 y posteriores tienen conjuntos de chips del Módulo de plataforma segura (TPM). Esta actualización incluye una nueva configuración de cumplimiento que comprueba la versión del chip TPM en el dispositivo. 

[La configuración de directivas de cumplimiento de Windows 10 y versiones posteriores](compliance-policy-create-windows.md#device-security) describe esta configuración.

Se aplica a: Windows 10 y versiones posteriores

### <a name="intune-management-extension-powershell-scripts-----3734186------"></a>Scripts de PowerShell de extensión de administración de Intune  <!-- 3734186    -->
Podrá configurar los scripts de PowerShell para que se ejecuten con los privilegios de administrador del usuario en el dispositivo. Para más información, consulte [Uso de scripts de PowerShell para dispositivos Windows 10 en Intune](intune-management-extension.md).

### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-supervised-devices----4097904----"></a>Impedir que los usuarios finales modifiquen su punto de acceso personal y deshabilitar el registro del servidor Siri en dispositivos supervisados por iOS <!-- 4097904  --> 
Crear un perfil de restricciones de dispositivo en el dispositivo iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para la plataforma y **Restricciones de dispositivo** para el tipo de perfil). Esta actualización incluye nuevas opciones que puede configurar:

- Punto de acceso personal
- Registro del servidor de Siri

Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características ](device-restrictions-ios.md). 

Se aplica a iOS 12.2 y versiones más recientes.

### <a name="new-classroom-app-device-restriction-settings-for-dep-enrolled-macos-devices----4097905----"></a>Nueva configuración de restricción de dispositivos de aplicaciones en el aula para dispositivos macOS inscritos en DEP <!-- 4097905  --> 
Puede crear un perfil de configuración de dispositivos para dispositivos MacOS (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **macOS** como plataforma >**Restricciones del dispositivo** para tipo de perfil). Esta actualización incluye una nueva configuración de aplicaciones de aula para dispositivos inscritos en DEP y la opción de deshabilitar la fototeca de iCloud.

Para ver la configuración actual, vaya a [Configuración de dispositivos macOS para permitir o restringir características mediante Intune](device-restrictions-macos.md).

Se aplica a macOS 10.14.4 y versiones posteriores.

### <a name="android-enterprise-app-management----4459905-idready---"></a>Administración de aplicaciones de Android Enterprise <!-- 4459905 idready -->
Para facilitar a los administradores de TI la configuración y el uso de la administración de Android Enterprise, Intune agregará automáticamente cuatro aplicaciones comunes relacionadas con Android Enterprise a la consola de administración de Intune. Las cuatro aplicaciones de Android Enterprise son las siguientes:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)**: se usa para escenarios totalmente administrados de Android Enterprise.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)**: ayuda a iniciar sesión en las cuentas si se usa la verificación de dos fases.
- **[Portal de empresa de Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)**: se usa para las directivas de protección de aplicación y escenarios de perfil de trabajo de Android Enterprise.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise): se usa para los escenarios de pantalla completa o dedicados de Android Enterprise.

Anteriormente, los administradores de TI tenían que buscar y aprobar manualmente estas aplicaciones en la [Tienda de Google Play administrada](https://play.google.com/store/apps) como parte de la configuración. Este cambio elimina los pasos que antes eran manuales para facilitar y agilizar el uso de la administración de Android Enterprise por parte de los clientes.

Los administradores verán que estas cuatro aplicaciones se agregan automáticamente a la lista de aplicaciones de Intune en el momento en que conecten por primera vez a su inquilino de Intune con Google Play administrado. Para más información, consulte [Conexión de una cuenta de Intune a una cuenta de Google Play administrado](connect-intune-android-enterprise.md). Para los inquilinos que ya han conectado a su inquilino o que ya utilizan Android Enterprise, no hay nada que los administradores tengan que hacer. Estas cuatro aplicaciones aparecerán automáticamente dentro de los siete días siguientes a la finalización de la implementación del servicio en mayo de 2019.

<!-- 1904 start-->

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Configuración avanzada del Firewall de Windows Defender <!-- 1311949 -->
Pronto podrá usar Intune para administrar las reglas de firewall personalizadas en los clientes de Windows Defender. Las reglas pueden especificar un comportamiento entrante y saliente en las aplicaciones, las direcciones de red y los puertos. 


### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Los usuarios del dispositivo pueden ver todas las aplicaciones administradas que han instalado o han intentado instalar <!-- 2352913 -->
En Portal de empresa para Windows se mostrará una lista de todas las aplicaciones administradas, tanto las requeridas como las disponibles, que están instaladas en el dispositivo de un usuario. Los usuarios podrán ver las instalaciones de aplicaciones intentadas y pendientes, así como sus estados actuales. Si su organización no hace que las aplicaciones sean obligatorias o estén disponibles, los usuarios verán un mensaje en el que se explica que no se ha instalado ninguna aplicación de empresa. Los usuarios también podrán ordenar o filtrar sus aplicaciones por estado de instalación.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Uso de "reglas de aplicabilidad" al crear perfiles de configuración de dispositivo Windows 10 <!-- 2549910 -->
Puede crear perfiles de configuración de dispositivo Windows 10 (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10** como plataforma). Podrá crear una **regla de aplicabilidad** para que el perfil solo se aplique a una edición o una versión en concreto. Por ejemplo, cree un perfil que permita algunas opciones de configuración de BitLocker. Una vez que agregue el perfil, use una regla de aplicabilidad para que este solo se aplique a los dispositivos que ejecuten Windows 10 Enterprise.

Se aplica a: 
- Windows 10 y versiones posteriores

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Tareas de seguridad de Intune para ATP de Defender (en versión preliminar pública) <!-- 3208597 -->
Intune agregará pronto tareas de seguridad en forma de versión preliminar pública para el recién anunciado Microsoft Defender Threat & Vulnerability Management.  Con esta integración, los administradores de operaciones de seguridad de ATP de Windows Defender (WDATP) pueden comunicar de forma más eficaz las correcciones recomendadas para las amenazas emergentes a los administradores de Intune. Al incluir las tareas de seguridad, se agrega un enfoque basado en riesgos para detectar, priorizar y corregir los errores de configuración y las vulnerabilidades del punto de conexión.

Para obtener más información sobre las tareas de seguridad en Intune, consulte la entrada de blog sobre [cómo usar las tareas de seguridad de Intune para ampliar Threat and Vulnerability Management de ATP de Microsoft Defender](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Línea de base de Advanced Threat Protection de Windows Defender <!-- 3754134 -->
Vamos a agregar una nueva línea base para ayudarle a configurar las opciones de Protección contra amenazas avanzada de Windows Defender.



## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


