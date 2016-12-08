---
title: "La edición anticipada | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6dd584397451d38be86fa0780efff435ffb9b2af
ms.openlocfilehash: d70ebf87bc930f853741ddc0d572d2174c636dac


---

# <a name="the-early-edition-for-microsoft-intune---december"></a>La edición anticipada para Microsoft Intune, diciembre

La **edición anticipada** proporciona una lista de características que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme al NDA en una base extremadamente limitada y está vinculada a cambios. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Póngase en contacto con su persona conocida de Intune/PM si tiene alguna pregunta o problema.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

Los siguientes cambios están en fase de desarrollo de Intune. Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

<!--736542-->
## <a name="public-preview-of-the-new-intune-admin-experience-on-azure"></a>Versión preliminar pública de la nueva experiencia de administración de Intune en Azure

A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API Graph.

Nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en el portal de Azure de este mes. Durante el estado de versión preliminar, se proporcionarán funcionalidades y paridad con la consola de Intune existente de manera iterativa.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si quiere probar o examinar alguna de las nuevas funcionalidades hasta que se migre su inquilino, regístrese para obtener una nueva cuenta de prueba de Intune o revise la nueva documentación.

Si tiene alguna pregunta sobre la programación de la migración de su inquilino, póngase en contacto con nuestro equipo de migración en [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integración de la administración de gastos de telecomunicaciones en la versión preliminar pública del portal de Azure<!--747605-->
Ahora estamos comenzando a realizar la integración de la versión preliminar con los servicios de administración de gastos de telecomunicaciones (TEM) dentro del portal de Azure. Puede usar Intune para exigir límites sobre el uso de datos nacionales y móviles. Comenzaremos estas integraciones con [Saaswedo](http://www.saaswedo.com).

## <a name="new-capabilities"></a>Nuevas funcionalidades

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>Autenticación multifactor en todas las plataformas <!--747590-->
Ahora puede exigir la autenticación multifactor (MFA) en un grupo de usuarios seleccionado cuando inscriben un dispositivo iOS, Android, Windows 8.1 + o Windows Phone 8.1 + desde el Portal de administración de Azure mediante la configuración de MFA en la aplicación de inscripción de Microsoft Intune en Azure Active Directory.

### <a name="conditional-access-for-mam-with-sharepoint-online---vso-679339--"></a>Acceso condicional para MAM con SharePoint Online<!--VSO 679339-->
Puede impedir que las aplicaciones que no son compatibles con las directivas de administración de aplicaciones móviles (MAM) de Intune accedan a SharePoint Online.  Puede comenzar a usar la administración de aplicaciones móviles de Intune mediante el portal de Azure. Busque la sección __Acceso condicional__ en la hoja __Configuración__ que incluirá la opción para SharePoint Online. Esta característica se distribuirá aparte del resto de la versión del servicio.

### <a name="ability-to-restrict-intune-mobile-device-enrollment"></a>Capacidad para restringir la inscripción de dispositivos móviles de Intune
Intune está agregando nuevas restricciones de inscripción que controlan qué plataformas de dispositivos móviles pueden inscribir. Intune separa las plataformas de dispositivos móviles como iOS, Mac OS, Android, Windows y Windows Mobile. 
* macOS y Windows 8.1 o posterior puede restringirse de la inscripción como plataformas de dispositivos móviles. 
* La restricción la inscripción de dispositivos móviles no restringe la inscripción del agente de PC. 
* Solo para iOS, hay una opción adicional para bloquear la inscripción de dispositivos de propiedad personal. Intune marca todos los dispositivos nuevos como personal a menos que el administrador de TI tome la medida de marcarlos como propiedad de la empresa, como se explica en [este artículo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).


## <a name="notices"></a>Notificaciones

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>Multi-Factor Authentication para la inscripción se mueve al portal de Azure <!--VSO 750545-->
Anteriormente, los administradores iban a la consola de Intune o a la consola de Configuration Manager (antes de la versión 1610) para establecer MFA para las inscripciones de Intune. Con esta característica actualizada, ahora iniciará sesión en el [portal de Microsoft Azure](https://manage.windowsazure.com) con sus credenciales de Intune y configurará MFA mediante Azure AD. Aprenda más al respecto [aquí](https://aka.ms/mfa_ad).

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>La aplicación del Portal de empresa para Android ahora disponible en China <!--VSO 658093-->
Publicaremos la aplicación del Portal de empresa para Android para su descarga en China. Debido a la ausencia de Google Play Store en China, los dispositivos Android deben obtener aplicaciones en los mercados de aplicaciones chinos. La aplicación del Portal de empresa para Android estará disponible para su descarga en 360, Tencent, Xiaomi, Wandoujia y Huawei. 

La aplicación del Portal de empresa para Android usa Google Play Services para comunicarse con el servicio de Microsoft Intune. Como Google Play Services no está todavía disponible en China, la realización de cualquiera de las siguientes tareas puede tardar hasta 8 horas en completarse. 

|Consola de administración de Intune| Aplicación del Portal de empresa de Intune para Android |Sitio web del Portal de empresa de Intune|   
|---|---|---|
|Borrar todos los datos| Quitar un dispositivo remoto| Quitar dispositivo (local y remoto)|
|La eliminación de datos selectiva| Restablecer dispositivo| Restablecer dispositivo|
|Implementaciones de aplicaciones nuevas o actualizadas| Instalar aplicaciones de línea de negocio disponibles| Restablecimiento de la contraseña del dispositivo|
|Bloqueo remoto|||
|Restablecimiento de la contraseña|||

## <a name="deprecations"></a>Elementos obsoletos

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>Eliminación de directivas de bandeja de entrada móvil de Exchange Online <!--770687-->
A partir de diciembre, los administradores ya no podrán ver ni configurar directivas de buzón móvil de Exchange Online (EAS) en la consola de Intune. Este cambio se implementará en todos los inquilinos de Intune durante diciembre y enero. Todas las directivas existentes permanecerán como están configuradas; para configurar nuevas directivas, use el Shell de administración de Exchange. Puede encontrar más información [aquí](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx).

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>Ya no se admiten las aplicaciones AV Player, Image Viewer y PDF Viewer de Intune en Android <!--747553-->.
Desde mediados de diciembre de 2016 en adelante, los usuarios ya no podrán utilizar las aplicaciones AV Player, Image Viewer, y PDF Viewer de Intune. Estas aplicaciones se han reemplazado por la aplicación Azure Information Protection. Descubra más sobre la aplicación Azure Information Protection [aquí](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new-in-microsoft-intune.md) para obtener más información sobre los desarrollos recientes.



<!--HONumber=Nov16_HO5-->


