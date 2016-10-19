---
title: "La edición anticipada | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5c4b0f15456a9f24c95954d669a17c63f96a459
ms.openlocfilehash: 273016d4fe114bbe60e9cebc06e89584c8f91f0b


---

# Próximas novedades en Microsoft Intune - Octubre
La **edición anticipada** proporciona una lista de características que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme al NDA en una base extremadamente limitada y está vinculada a cambios. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Póngase en contacto con su persona conocida de Intune/PM si tiene alguna pregunta o problema.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones nuevas en Próximas novedades.

Los siguientes cambios están en fase de desarrollo de Intune. Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

### Administrar la impresión desde aplicaciones administradas mediante directivas MAM
Ahora puede evitar la impresión de datos empresariales desde aplicaciones que tengan directivas MAM. Esta configuración está disponible en [Azure Portal](..deployuse/create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) y se admite tanto en dispositivos [iOS](..deployuse/ios-mam-policy-settings) como [Android](..deployuse/android-mam-policy-settings).
<!--TFS 1014328-->

### El nuevo portal de empresa de Microsoft Intune está disponible para los dispositivos Windows 10
Microsoft está lanzando un nuevo portal de empresa de Microsoft Intune para los dispositivos Windows 10. Esta aplicación, que aprovecha el nuevo formato de Windows 10 Universal, proporcionará al usuario una experiencia de usuario actualizada dentro de la aplicación y experiencias idénticas en todos los dispositivos Windows 10, PC y móvil, mientras sigue permitiendo las mismas funcionalidades que usa hoy en día.

La nueva aplicación también permitirá a los usuarios aprovechar características de plataforma adicional como el inicio de sesión único (SSO) y la autenticación basada en certificados en dispositivos Windows 10. La aplicación estará disponible como una actualización del portal de empresa de Windows 8.1 existente y este se instala desde la Tienda Windows.
<!--TFS 1016502-->

### Compatibilidad de Android for Work

Intune ahora forma parte del [programa de Android for Work](https://enterprise.google.com/android/partners/). Empezaremos a implementar la compatibilidad de las características de Android for Work en Intune a partir de este mes.

[Lea el anuncio de Microsoft sobre la compatibilidad de Intune con Android for Work](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

<!---This month, some newly provisioned Intune tenants will start seeing the Android for Work features. We will announce later when existing tenants will begin to see this feature.--->
<!--TFS 1043303-->

### Compatibilidad de Android Samsung KNOX con Intune

Determinados modelos del teléfono Samsung Galaxy Ace no pueden administrarse con Intune como los dispositivos de Samsung KNOX. Cuando inscriba estos dispositivos con Intune, se administrarán en su lugar como dispositivos estándar de Android.
Los números de los modelos afectados son:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Sus usuarios finales y usted no necesitan realizar ninguna otra acción.
Para obtener más información, visite el sitio web de [Samsung KNOX](https://www.samsungknox.com).

<!--TFS 1173566 iX blurb provided by Barry; requires PM signoff

### Multi-factor authentication for Android and iOS enrollment

In addition to Windows 8.1 and later, administrators can now enable multi-factor authentication for Android and iOS devices in the Microsoft Intune Enrollment application. -->    

### La aplicación portal de empresa de Windows 8 está en desuso; el soporte para las plataformas de Windows Phone 8 y Windows RT está en desuso
A partir de octubre de 2016, Microsoft Intune dejará de ofrecer soporte para el portal de empresa de Windows 8. Microsoft Intune también dejará de ofrecer soporte para la plataforma Windows Phone 8 y Windows RT. Como consecuencia, no podrá inscribir ni actualizar ningún dispositivo Windows Phone 8 o Windows RT.

Puede seguir administrando los dispositivos Windows Phone 8, Windows RT y Windows 8 que ya estén inscritos. Actualice los dispositivos Windows Phone 8 y Windows 8 a Windows 8.1 y Windows Phone 8.1 y use las aplicaciones de portal de empresa de Windows 8.1 y Windows Phone 8.1 correspondientes para poder seguir con la distribución de aplicaciones en estos dispositivos sin interrupciones.

A partir de noviembre de 2016, dejaremos de ofrecer soporte para el portal de empresa de Windows Phone 8.
<!--TFS 1255391-->

### Acceso condicional para la administración de aplicaciones móviles
Ahora puede crear directivas de acceso condicional para impedir que las aplicaciones móviles sin administrar tengan acceso a [Exchange Online](..deployuse/restrict-access-to-exchange-online-with-microsoft-intune.md) y [SharePoint Online](..deployuse/restrict-access-to-sharepoint-online-with-microsoft-intune.md). Puede bloquear las aplicaciones y los clientes de correo integrados que no están habilitados mediante MAM con el SDK de la aplicación de Intune.  Esto puede realizarse al crear una directiva de acceso condicional y especificar las aplicaciones que quiere que tengan acceso a Exchange Online y SharePoint Online mediante Azure Portal.
<!--TFS 1317673-->

<!--TFS 1318014; awaiting approval in notes as to whether to proceed

### "Default" policy is deprecated

To minimize unintentionally assigned profiles, Intune is removing support for the "default" Corporate Device Enrollment profile for Apple Device Enrollment Program (DEP) device serial numbers in the new Azure console. Serial numbers synchronized from an Apple DEP account will initially have no Corporate Device Enrollment profile assigned.  A profile must be assigned manually after synchronization. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

<!--TFS 1318023; awaiting approval in notes as to whether to proceed

### Deprecation of row-by-row iOS Details review for iOS device CSV uploads

In order to streamline uploading IMEI numbers for Corporate devices and Apple serial numbers for Configurator enrollment, Intune is removing the row by row review of hardware identifiers already found in the system. This review allows the IT Pro to accept associated Details from the CSV to overwrite the existing details for a hardware identifier already in the system. The review will be replaced by a single option to automatically overwrite Details for all hardware identifiers or ignore new details for existing identifiers. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

### Integración de Lookout para proteger los dispositivos iOS
En octubre, Microsoft se está integrando en la solución de protección de amenazas móviles de Lookout para proteger los dispositivos móviles iOS mediante la detección de malware y aplicaciones de riesgo, entre otros, en los dispositivos. La solución de Lookout le ayuda a determinar el nivel de amenaza, que es configurable. Puede crear una regla de directivas de cumplimiento en Intune para terminar el cumplimiento de dispositivo basándose en la evaluación de riesgos mediante Lookout. Con las directivas de acceso condicional, puede permitir o bloquear el acceso a los recursos empresariales basándose en el estado de cumplimiento del dispositivo.

A los usuarios finales de los dispositivos iOS no compatibles se les solicitará que se inscriban; necesitarán instalar la aplicación Lookout for Work en sus dispositivos, activar la aplicación y corregir las amenazas que se mencionan en la aplicación Lookout for Work para obtener acceso a los datos de la empresa.
<!--TFS 1319493-->

### SDK de la aplicación de Intune y herramienta de ajuste de aplicaciones para Android
Puede habilitar las aplicaciones para que usen directivas de administración de aplicaciones móviles (MAM) de Intune mediante la herramienta de ajuste de aplicaciones de Intune o el SDK para aplicaciones de Intune. Las nuevas actualizaciones para el SDK y la herramienta de ajuste de aplicaciones incluirán:

* Compatibilidad con Android N
* Compatibilidad con directivas MAM de Intune sin requerir la inscripción de dispositivos
* Compatibilidad con aplicaciones de Android basadas en Xamarin

Puede probar MAM sin la inscripción de dispositivos y la compatibilidad de Xamarin en la versión preliminar pública de la herramienta de ajuste de aplicaciones de Android aquí: [https://github.com/msintuneappsdk/intune-app-wrapper-android-preview](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview).
<!--TFS 1319511; please create new TFS entry for WN text associated with this TFS item-->

<!--TFS 1319613; no iX review on PM text blurb

### Private preview customers using MAM Conditional Access will have their policies reset

Due to changes in the policy structure for Conditional Access for Mobile App Management, any existing policies that were set by customers through the private preview will be removed. Customers will need to set new policies once the change is made. The timing will coincide with the October service update.
-->

### Consulte también
Consulte [Novedades de Microsoft Intune](whats-new-in-microsoft-intune.md) para obtener más información sobre los desarrollos recientes.



<!--HONumber=Oct16_HO1-->


