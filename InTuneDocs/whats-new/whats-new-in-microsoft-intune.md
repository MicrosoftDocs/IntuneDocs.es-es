---
title: Novedades | Microsoft Docs
description: Conozca las novedades de las versiones anteriores y de este mes de Microsoft Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2fdf4086ccf4b4f256596b7d0f7192b70a4efd2a
ms.openlocfilehash: a2f3eab11f208c0260dc4dbc245801416dc36633


---
# <a name="whats-new-in-microsoft-intune---january-2017"></a>Novedades de Microsoft Intune - Enero de 2017
Conozca las novedades de esta versión de Microsoft Intune. También podrá obtener información sobre los próximos cambios para los que debe prepararse y sobre las versiones anteriores.

> [!Note]
> Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuevas funcionalidades

<!--### Actions for non-compliance <!--730266
_Actions for non-compliance_ is a new feature of compliance policies that lets you take action on devices that are out of compliance. You can specify single or multiple actions and specify the time period at which those actions must occur. For example, you can notify users of non-compliant devices immediately after the devices become non-compliant through email, or you can block non-compliant devices from accessing corporate resources after a 3-day grace period via Conditional Access.-->

### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Informes en la consola para MAM sin inscripción <!--677961-->
Se han agregado nuevos informes de protección de aplicaciones para los dispositivos inscritos y no inscritos. Obtenga más información sobre cómo puede [supervisar directivas de administración de aplicaciones móviles con Microsoft Intune aquí](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune).

<!--### Conditional access for MAM with SharePoint Online <!--679339
You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint Online.  You can get started using Intune mobile app management in the Azure portal. Look for the __Conditional Access__ section in the __Settings__ blade which will include the option for SharePoint Online. This feature will ship separately from the rest of the service release. <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="android-711-support---694397--"></a>Compatibilidad con Android 7.1.1 <!--694397-->
Ahora, Intune admite y administra completamente Android 7.1.1.

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Resolver el problema en el que los dispositivos iOS están inactivos o la consola de administración no puede comunicarse con ellos

Cuando los dispositivos de los usuarios pierden el contacto con Intune, puede proporcionarles nuevos pasos de solución de problemas para ayudarles a volver a obtener acceso a los recursos de la empresa. Vea [Los dispositivos están inactivos o la consola de administración no puede comunicarse con ellos](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="notices"></a>Notificaciones

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Restablecer la administración de dispositivos de escritorio Windows predeterminada mediante la configuración de Windows <!--663050-->
El comportamiento predeterminado para inscribir equipos de escritorio de Windows 10 está cambiando. Las nuevas inscripciones seguirán el típico flujo de inscripción del agente MDM en lugar del agente de PC.

El sitio web de portal de empresa proporcionará a los usuarios de escritorio de Windows 10 las instrucciones de inscripción que les guiarán a través del proceso de agregar equipos de escritorio de Windows 10 como dispositivos móviles. Esto no afectará a los PC inscritos en estos momentos, y su organización todavía puede administrar equipos de escritorio de Windows 10 con el agente de PC [si lo prefiere](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

<!--### Company Portal for iOS links open inside the app <!--665954
Links inside of the Company Portal app for iOS, including those to documentation and apps, will open directly in the Company Portal app using an in-app view of Safari. This update will ship separately from the service update in January.-->

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Mejorar la asistencia de la administración de aplicaciones móviles para el borrado selectivo <!--581242-->
A los usuarios finales se les proporcionarán instrucciones adicionales sobre cómo recuperar el acceso a los datos profesionales o educativos si estos se quitaron automáticamente debido a la directiva "Intervalo sin conexión antes de que se borren los datos de la aplicación".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="new-documentation-for-app-protection-policies---583398--"></a>Nueva documentación para las directivas de protección de aplicaciones <!--583398-->
Hemos actualizado nuestra documentación para administradores y desarrolladores de aplicaciones que quieran habilitar directivas de protección de aplicaciones (conocidas como directivas de MAM) en sus aplicaciones iOS y Android con la herramienta de ajuste de aplicaciones de Intune o con el SDK para aplicaciones de Intune.

Se han actualizado los siguientes artículos:

* [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Preparar aplicaciones iOS para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Introducción al SDK para aplicaciones de Microsoft Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Guía para desarrolladores sobre el SDK de aplicaciones de Intune para iOS](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

Se han agregado los siguientes artículos nuevos a la biblioteca de documentos:

* [Complemento Cordova del SDK para aplicaciones de Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Componente Xamarin del SDK para aplicaciones de Intune](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

<!--### Progress bar when launching the Company Portal on iOS <!--665978
The Company Portal for iOS is introducing a progress bar on the launch screen to provide the user with information about the loading processes that occur. There will be a phased rollout of the progress bar to replace the spinner. This means that some of your users will see the new progress bar while others will continue to see the spinner.-->

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novedades en la versión preliminar pública de la experiencia de administración en Azure <!--736542-->

A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API Graph.

Nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en el portal de Azure de este mes. Durante el estado de versión preliminar, se proporcionarán funcionalidades y paridad con la consola de Intune existente de manera iterativa.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si quiere probar o examinar alguna de las nuevas características hasta que se migre su inquilino, regístrese para obtener una nueva cuenta de prueba de Intune o revise la [nueva documentación](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

Si tiene alguna pregunta sobre la programación de la migración de su inquilino, póngase en contacto con nuestro equipo de migración en [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

Puede encontrar las novedades en la vista previa de Intune en Azure [aquí](https://docs.microsoft.com/intune-azure/introduction/whats-new).

### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades en la vista previa de Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Archivo de novedades](whats-new-archive.md)



<!--HONumber=Jan17_HO2-->


