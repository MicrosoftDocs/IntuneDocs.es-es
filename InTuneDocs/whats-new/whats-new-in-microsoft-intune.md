---
title: Novedades | Microsoft Intune
description: Conozca las novedades de las versiones anteriores y de este mes de Microsoft Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9fd309a10d9eb020795c5ce46df124b13dc1a006
ms.openlocfilehash: d117c929fbde4dd0a39503b8da695aa9c9ea91ad


---
# <a name="whats-new-in-microsoft-intune---december-2016"></a>Novedades de Microsoft Intune - Diciembre de 2016
Conozca las novedades de esta versión de Microsoft Intune. También podrá obtener información sobre los próximos cambios para los que debe prepararse y sobre las versiones anteriores.

> [!Note]
> Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure--736542--"></a>Versión preliminar pública de la nueva experiencia de administración de Intune en Azure<!--736542-->
A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API Graph. Antes de la disponibilidad general de este portal para todos los inquilinos de Intune, nos complace anunciar que comenzaremos a implementar una versión preliminar de esta nueva experiencia de administración dentro de este mes para seleccionar inquilinos.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, encuentre más información sobre lo que tenemos en Azure Portal para Microsoft Azure en nuestra [documentación nueva](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

Si tiene alguna pregunta sobre la programación de la migración de su inquilino, póngase en contacto con nuestro equipo de migración en [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integración de la administración de gastos de telecomunicaciones en la versión preliminar pública del portal de Azure<!--747605-->
Ahora estamos comenzando a realizar la integración de la versión preliminar con los servicios de administración de gastos de telecomunicaciones (TEM) dentro del portal de Azure. Puede usar Intune para exigir límites sobre el uso de datos nacionales y móviles. Comenzaremos estas integraciones con [Saaswedo](http://www.saaswedo.com).

## <a name="new-capabilities"></a>Nuevas funcionalidades

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>Autenticación multifactor en todas las plataformas <!--747590-->
Ahora puede exigir la autenticación multifactor (MFA) en un grupo de usuarios seleccionado cuando inscriben un dispositivo iOS, Android, Windows 8.1 + o Windows Phone 8.1 + desde el Portal de administración de Azure mediante la configuración de MFA en la aplicación de inscripción de Microsoft Intune en Azure Active Directory.

<!--VSO 679339, awaiting chrisgre for go-live--><!--### Conditional access for MAM with SharePoint Online
Puede impedir que las aplicaciones que no son compatibles con las directivas de administración de aplicaciones móviles (MAM) de Intune accedan a SharePoint Online.  Puede comenzar a usar la administración de aplicaciones móviles de Intune mediante el portal de Azure. Busque la sección __Acceso condicional__ en la hoja __Configuración__ que incluirá la opción para SharePoint Online. Esta característica se distribuirá aparte del resto de la versión del servicio. Encuentre más información sobre esta característica nueva [aquí](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="ability-to-restrict-mobile-device-enrollment--747596--"></a>Capacidad para restringir la inscripción de dispositivos móviles<!--747596-->
Intune está agregando nuevas restricciones de inscripción que controlan qué plataformas de dispositivos móviles pueden inscribir. Intune separa las plataformas de dispositivos móviles como iOS, Mac OS, Android, Windows y Windows Mobile.
* La restricción la inscripción de dispositivos móviles no restringe la inscripción del cliente de PC.
* Solo para iOS, hay una opción adicional para bloquear la inscripción de dispositivos de propiedad personal.

Intune marca todos los dispositivos nuevos como personal a menos que el administrador de TI tome la medida de marcarlos como propiedad de la empresa, como se explica en [este artículo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).


## <a name="notices"></a>Notificaciones

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>Multi-Factor Authentication para la inscripción se mueve al portal de Azure <!--VSO 750545-->
Anteriormente, los administradores iban a la consola de Intune o a la consola de Configuration Manager (antes de la versión de octubre de 2016) para establecer MFA para las inscripciones de Intune. Con esta característica actualizada, ahora iniciará sesión en el [portal de Microsoft Azure](https://manage.windowsazure.com) con sus credenciales de Intune y configurará MFA mediante Azure AD. Aprenda más al respecto [aquí](https://aka.ms/mfa_ad).

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>La aplicación del Portal de empresa para Android ahora disponible en China <!--VSO 658093-->
Publicaremos la aplicación del Portal de empresa para Android para su descarga en China. Debido a la ausencia de Google Play Store en China, los dispositivos Android deben obtener aplicaciones en los mercados de aplicaciones chinos. La aplicación Portal de empresa para Android estará disponible para su descarga en las siguientes tiendas:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

La aplicación del Portal de empresa para Android usa Google Play Services para comunicarse con el servicio de Microsoft Intune. Como Google Play Services no está todavía disponible en China, la realización de cualquiera de las siguientes tareas puede tardar hasta 8 horas en completarse. 

|Consola de administración de Intune| Aplicación del Portal de empresa de Intune para Android |Sitio web del Portal de empresa de Intune|   
|---|---|---|
|Borrar todos los datos| Quitar un dispositivo remoto| Quitar dispositivo (local y remoto)|
|La eliminación de datos selectiva| Restablecer dispositivo| Restablecer dispositivo|
|Implementaciones de aplicaciones nuevas o actualizadas| Instalar aplicaciones de línea de negocio disponibles| Restablecimiento de la contraseña del dispositivo|
|Bloqueo remoto|||
|Restablecimiento de la contraseña|||

## <a name="deprecations"></a>Elementos obsoletos

### <a name="firefox-to-no-longer-support-silverlight--vso-tba--"></a>Firefox ya no admite Silverlight<!--VSO TBA-->
Mozilla quitará la compatibilidad con Silverlight en la versión 52 del [explorador Firefox](https://www.mozilla.org/firefox), a partir de marzo de 2017. Como resultado de lo anterior, ya no podrá iniciar sesión en la consola de Intune existente con las versiones de Firefox superiores a la versión 51. Se recomienda usar Internet Explorer 10 u 11 para obtener acceso a la consola de administración, o bien una [versión de Firefox anterior a la versión 52](https://ftp.mozilla.org/pub/firefox/releases/). La transición de Intune a Azure Portal le permitirá admitir varios [exploradores modernos](https://docs.microsoft.com/en-us/azure/azure-preview-portal-supported-browsers-devices) sin depender de Silverlight.

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>Eliminación de directivas de bandeja de entrada móvil de Exchange Online <!--770687-->
A partir de diciembre, los administradores ya no podrán ver ni configurar directivas de buzón móvil de Exchange Online (EAS) en la consola de Intune. Este cambio se implementará en todos los inquilinos de Intune durante diciembre y enero. Todas las directivas existentes permanecerán como están configuradas; para configurar nuevas directivas, use el Shell de administración de Exchange. Puede encontrar más información [aquí](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx).

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>Ya no se admiten las aplicaciones AV Player, Image Viewer y PDF Viewer de Intune en Android <!--747553-->.
Desde mediados de diciembre de 2016 en adelante, los usuarios ya no podrán utilizar las aplicaciones AV Player, Image Viewer, y PDF Viewer de Intune. Estas aplicaciones se han reemplazado por la aplicación Azure Information Protection. Descubra más sobre la aplicación Azure Information Protection [aquí](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).

### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Versiones anteriores de Intune](whats-new-archive.md)



<!--HONumber=Dec16_HO2-->


