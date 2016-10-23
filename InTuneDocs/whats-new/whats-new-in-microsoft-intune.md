---
title: Novedades | Microsoft Intune
description: Conozca las novedades de las versiones anteriores y de este mes de Microsoft Intune
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 503719953031bf5079b2bf5bc84a0497d708f79a
ms.openlocfilehash: 730809e0841a248b90f5fe157f2c6338bfd32b2d


---
# Novedades de Microsoft Intune - Octubre 2016
Conozca las novedades de esta versión de Microsoft Intune. También podrá obtener información sobre los próximos cambios para los que debe prepararse y sobre las versiones anteriores.

Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## Novedades

### Acceso condicional para la administración de aplicaciones móviles
Podrá restringir el acceso a Exchange Online de forma que el acceso solo proceda de aplicaciones que admitan las directivas de administración de aplicaciones móviles de Intune, como Outlook. [Esta nueva característica](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) se adapta perfectamente a las directivas de administración de aplicaciones móviles (MAM) de Intune, ya que puede bloquear el acceso a los clientes de correo integrado u otras aplicaciones que no se hayan configurado con las directivas de MAM de Intune. Esto garantiza que los usuarios están teniendo acceso a los datos de su organización con aplicaciones que pueden estar protegidas mediante MAM de Intune. Puede comenzar a trabajar en la administración de aplicaciones móviles de Intune mediante Azure Portal. Busque la nueva sección de acceso condicional en la hoja "Configuración".

### Acceso condicional para equipos Windows
Ahora puede crear directivas de acceso condicional a través de la consola de administración de Intune para impedir que los equipos Windows tengan acceso a [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) y a [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune). También puede crear directivas de acceso condicional para bloquear el acceso a aplicaciones de escritorio y universales de Office.

### Compatibilidad de Android for Work
Intune ahora forma parte del programa de Android for Work. Empezaremos a implementar la compatibilidad de las características de Android for Work en Intune a partir de este mes.
[Lea el anuncio de Microsoft sobre la compatibilidad de Intune con Android for Work](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

Los temas de Intune siguientes son nuevos o actualizados con la información de Android for Work:

Para profesionales de TI:
- [Configurar Android for Work](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [Restringir el acceso de correo electrónico a Exchange Online y nuevo Exchange Online dedicado](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Restringir el acceso de correo electrónico a Exchange local y Exchange Online dedicado heredado con Intune](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Configuración de directivas de cumplimiento para dispositivos Android for Work](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [Implementación de aplicaciones Android for Work](/intune/deploy-use/android-for-work-apps)
- [Configuración de aplicaciones Android for Work con directivas de configuración de aplicaciones móviles](/intune/deploy-use/afw-app-configuration-policy)
- [Opciones de directivas de Android for Work](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

Para usuarios finales:
- [¿Qué ocurre cuando se crea un perfil de trabajo?](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [Creación de un perfil de trabajo e inscripción del dispositivo en Intune](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### Integración de Lookout para proteger los dispositivos iOS
En octubre, Microsoft se está integrando en la solución de protección de amenazas móviles de Lookout para proteger los dispositivos móviles iOS mediante la detección de malware y aplicaciones de riesgo, entre otros, en los dispositivos. La solución de Lookout le ayuda a determinar el nivel de amenaza, que es configurable. Puede crear una regla de directivas de cumplimiento en Intune para terminar el cumplimiento de dispositivo basándose en la evaluación de riesgos mediante Lookout. Con las directivas de acceso condicional, puede permitir o bloquear el acceso a los recursos empresariales basándose en el estado de cumplimiento del dispositivo.

A los usuarios finales de los dispositivos iOS no compatibles se les solicitará que se inscriban; necesitarán instalar la aplicación Lookout for Work en sus dispositivos, activar la aplicación y corregir las amenazas que se mencionan en la aplicación Lookout for Work para obtener acceso a los datos de la empresa. Obtenga información sobre cómo [Configurar e implementar aplicaciones Lookout for Work](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps).
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### Herramienta de ajuste de aplicaciones Intune para Android
Puede habilitar las aplicaciones para que usen directivas de administración de aplicaciones móviles (MAM) de Intune mediante la herramienta de ajuste de aplicaciones de Intune. La compatibilidad con directivas MAM de Intune sin requerir la inscripción de dispositivos ya está disponible.

### Administrar la impresión desde aplicaciones administradas mediante directivas MAM
Ahora puede evitar la impresión de datos empresariales desde aplicaciones que tengan directivas MAM. Esta configuración está disponible en [Azure Portal](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) y se admite tanto en dispositivos [iOS](/Intune/deploy-use/ios-mam-policy-settings) como [Android](/Intune/deploy-use/android-mam-policy-settings).
<!--TFS 1014328-->

## Notificaciones

### Compatibilidad de Android Samsung KNOX con Intune
Determinados modelos del teléfono Samsung Galaxy Ace no pueden administrarse con Intune como los dispositivos de Samsung KNOX. Cuando inscriba estos dispositivos con Intune, se administrarán en su lugar como dispositivos estándar de Android.

Los números de los modelos afectados son:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Sus usuarios finales y usted no necesitan realizar ninguna otra acción. Para obtener más información, visite el sitio web de [Samsung KNOX](https://www.samsungknox.com).

### La aplicación portal de empresa de Windows 8 está en desuso; el soporte para las plataformas de Windows Phone 8 y Windows RT está en desuso
A partir de octubre de 2016, Microsoft Intune dejará de ofrecer soporte para el portal de empresa de Windows 8. Microsoft Intune también dejará de ofrecer soporte para la plataforma Windows Phone 8 y Windows RT. Como consecuencia, no podrá inscribir ni actualizar ningún dispositivo Windows Phone 8 o Windows RT.

Puede seguir administrando los dispositivos Windows Phone 8, Windows RT y Windows 8 que ya estén inscritos. Actualice los dispositivos Windows Phone 8 y Windows 8 a Windows 8.1 y Windows Phone 8.1 y use las aplicaciones de portal de empresa de Windows 8.1 y Windows Phone 8.1 correspondientes para poder seguir con la distribución de aplicaciones en estos dispositivos sin interrupciones.

A partir de noviembre de 2016, dejaremos de ofrecer soporte para el portal de empresa de Windows Phone 8.
<!--TFS 1255391-->

## Próximas novedades

### El nuevo portal de empresa de Microsoft Intune está disponible para los dispositivos Windows 10
Microsoft está lanzando un nuevo portal de empresa de Microsoft Intune para los dispositivos Windows 10. Esta aplicación, que aprovecha el nuevo formato de Windows 10 Universal, proporcionará al usuario una experiencia de usuario actualizada dentro de la aplicación y experiencias idénticas en todos los dispositivos Windows 10, PC y móvil, mientras sigue permitiendo las mismas funcionalidades que usa hoy en día.

La nueva aplicación también permitirá a los usuarios aprovechar características de plataforma adicional como el inicio de sesión único (SSO) y la autenticación basada en certificados en dispositivos Windows 10. La aplicación estará disponible como una actualización del portal de empresa de Windows 8.1 existente y este se instala desde la Tienda Windows. Para más información, vaya a [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).
<!--TFS 1016502-->

### Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Versiones anteriores de Intune](previous-intune-releases.md)



<!--HONumber=Oct16_HO3-->


