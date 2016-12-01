---
title: Novedades | Microsoft Intune
description: Conozca las novedades de las versiones anteriores y de este mes de Microsoft Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8e88c14ad77d8fe1b4c0fe2e7676d126e6288146
ms.openlocfilehash: bcd77b751c2059131558e1cbfeebd4d3f71086e5


---
# <a name="whats-new-in-microsoft-intune---november-2016"></a>Novedades de Microsoft Intune - Noviembre de 2016
Conozca las novedades de esta versión de Microsoft Intune. También podrá obtener información sobre los próximos cambios para los que debe prepararse y sobre las versiones anteriores.

Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## <a name="new-capabilities"></a>Nuevas funcionalidades

<!--### View App States for All Platforms in Real Time
App installation status is now shown in real-time in the console. When you previously deployed an app, you had to wait for a targeted device to report back before the app install status was displayed in the Intune console.

### Streamline iOS App Management for your End Users
Intune can now automatically take over management of the previously installed app and no end user action is required.

Previously, if the end user of an enrolled iOS device installed an app from the App Store before you deployed that same app with a deployment action of __Available__, then the end user had to:

1. Open the __Company Portal__.
2. Select the app.
3. Tap __Install__ to enable Intune to take over management of the app.-->

<!--### New Microsoft Intune Company Portal App for Windows 10 Devices
Microsoft is releasing a new Intune Company Portal for Windows 10 devices. This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike - while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store. It will also be available for sideloading.-->

<!--### Support for Windows Store for Business Apps Being Deployed as Available
You can now deploy apps you synchronized from the Windows Store for Business (WSfB) with a deployment action of __Available__ or __Required__. After syncing WSfB apps into Intune, administrators will be able to target those apps as available installs to groups of users. End users will see the deployed WSfB apps as available for install in the Universal Company Portal, where they can choose whether they would like to acquire the apps.

### Conditional Access for MAM with SharePoint Online

You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint online.  You can get started in Intune mobile app management via the Azure portal. Look for the  Conditional Access section in the “Settings” blade which now includes the option for SharePoint online.-->

> [!IMPORTANT]

> __Actualización de Intune y Android for Work__

> Aunque se pueden implementar aplicaciones Android for Work con una acción __Requerido__, solo se pueden implementar aplicaciones como __Disponible__ si los grupos de Intune se han migrado a la nueva experiencia de grupos de Azure AD.

### <a name="intune-app-sdk-for-cordova-plugin-now-supports-mam-without-enrollment"></a>El complemento Cordova del SDK para aplicaciones de Intune ahora admite MAM sin inscripción
Los desarrolladores de aplicaciones ahora pueden usar el complemento Cordova del SDK para aplicaciones de Intune para habilitar la funcionalidad MAM sin inscribir el dispositivo en sus aplicaciones de Cordova para iOS y Android. El complemento Cordova del SDK para aplicaciones de Intune se puede encontrar [aquí](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

### <a name="intune-app-sdk-xamarin-component-now-supports-mam-without-enrollment"></a>El componente Xamarin del SDK para aplicaciones de Intune ahora admite MAM sin inscripción
Los desarrolladores de aplicaciones ahora pueden usar el componente Xamarin del SDK para aplicaciones de Intune para habilitar la funcionalidad MAM sin inscripción de dispositivos en sus aplicaciones basadas en Xamarin para iOS y Android. El componente Xamarin del SDK para aplicaciones de Intune se puede encontrar [aquí](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

## <a name="notices"></a>Notificaciones

### <a name="symantec-signing-certificate-no-longer-requires-signed-windows-phone-8-company-portal-for-upload"></a>El certificado de firma de Symantec ya no requiere el portal de empresa firmado de Windows Phone 8 para la carga
La carga del certificado de firma de Symantec ya no requiere una aplicación firmada del portal de empresa de Windows Phone 8. El certificado se puede cargar de forma independiente.

## <a name="deprecations"></a>Elementos obsoletos

### <a name="support-for-the-windows-phone-8-company-portal"></a>Compatibilidad con el portal de empresa de Windows Phone 8
La compatibilidad con el portal de empresa de Windows Phone 8 ahora está en desuso. La compatibilidad con las plataformas Windows Phone 8 y WinRT ha quedado en desuso en octubre de 2016. La compatibilidad con el portal de empresa de Windows 8 ha quedado en desuso en octubre de 2016.


### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Versiones anteriores de Intune](whats-new-archive.md)



<!--HONumber=Nov16_HO3-->


