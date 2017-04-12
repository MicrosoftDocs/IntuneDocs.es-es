---
title: Novedades | Microsoft Docs
description: Conozca las novedades de las versiones anteriores y de este mes de Microsoft Intune
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: c473a1f05b0a7b0ce5205598b2b9a9b86bfe6c1d
ms.openlocfilehash: bddd8c0dc74835f74a71af1d900d43d84aab894c
ms.lasthandoff: 03/29/2017


---
# <a name="whats-new-in-microsoft-intune---march-2017"></a>Novedades de Microsoft Intune: marzo de 2017
Conozca las novedades de esta versión de Microsoft Intune. También podrá obtener información sobre los próximos cambios para los que debe prepararse y sobre las versiones anteriores.

> [!Note]
> Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuevas funcionalidades

### <a name="support-for-skycure"></a>Compatibilidad con Skycure

Ahora puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Skycure, una solución de defensa contra amenazas móviles integrada con Microsoft Intune. El riesgo se evalúa según la telemetría recopilada de dispositivos que ejecutan Skycure, que incluye:

- Defensa física
- Defensa de red
- Defensa de aplicaciones
- Defensa de vulnerabilidades

Puede configurar directivas de acceso condicional de EMS basadas en la evaluación de riesgos de Skycure habilitada mediante las directivas de cumplimiento de dispositivos de Intune. Puede usar estas directivas para permitir o bloquear el acceso de dispositivos no compatibles a recursos corporativos en función de las amenazas detectadas. Para obtener más información, vea [Conector de Mobile Threat Defense de Skycure](/intune/deploy-use/skycure-mobile-threat-defense-connector).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nueva experiencia del usuario en la aplicación del portal de empresa para Android <!--621622-->

La aplicación de Portal de empresa para Android va a actualizar su interfaz de usuario para un aspecto más moderno y una mejor experiencia de usuario. Las actualizaciones importantes son:

- Colores: los encabezados de la pestaña de Portal de empresa están coloreados según la información de la marca definida por TI.
- Aplicaciones: en la pestaña **Aplicaciones**, los botones **Aplicaciones destacadas** y **Todas las aplicaciones** se han actualizado.
- Buscar: en la pestaña **Aplicaciones**, el botón **Buscar** ahora es un botón de acción flotante.
- Aplicaciones de navegación: la vista **Todas las aplicaciones** muestra una vista con las pestañas **Destacadas**, **Todas** y **Categorías** para navegar más fácilmente.
- Soporte: las pestañas **Mis dispositivos** y **Contactar con TI** se actualizan para mejorar la legibilidad.

Para obtener más información sobre estos cambios, consulte [Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune](whats-new-in-intune-app-ui.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Los dispositivos no administrados puedan acceder a aplicaciones asignadas <!--664691-->

Como parte de los cambios de diseño en el sitio web del portal de empresa, los usuarios de iOS y Android podrán instalar aplicaciones asignadas a ellos como "disponibles sin inscripción" en sus dispositivos no administrados. Con sus credenciales de Intune, los usuarios podrán iniciar sesión en el sitio web del portal de empresa y ver la lista de aplicaciones asignadas. Los paquetes de aplicación de las aplicaciones "disponibles sin inscripción" se encuentran disponibles para descargar a través del sitio web del portal de empresa. Las aplicaciones que requieren la inscripción para la instalación no se ven afectadas por este cambio, ya que se les pedirá a los usuarios que inscriban su dispositivo si quieren instalar esas aplicaciones.

### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Script de firma para el Portal de empresa para Windows 10<!--941642-->

Si necesita descargar y transferir localmente la aplicación del Portal de empresa para Windows 10, ahora puede usar un script para simplificar y agilizar el proceso de firma de aplicaciones en su organización.   Para descargar el script y las instrucciones de uso, consulte el artículo [Microsoft Intune Signing Script for Windows 10 Company Portal](https://aka.ms/win10cpscript) (Script de firma de Microsoft Intune para el Portal de empresa para Windows 10) de la Galería de TechNet. Para obtener más información sobre este anuncio, consulte [Updating your Windows 10 Company Portal app](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) (Actualización de la aplicación del Portal de empresa para Windows 10) en el blog del equipo de asistencia técnica de Intune.


## <a name="notices"></a>Notificaciones

### <a name="support-for-ios-103"></a>Compatibilidad con iOS 10.3

La versión de iOS 10.3 empezó a implementarse el 27 de marzo de 2017 a los usuarios de iOS. Todos los escenarios MDM y MAM existentes de Intune son compatibles con la versión más reciente del sistema operativo de Apple. Se prevé que todas las características existentes de Intune actualmente disponibles para administrar dispositivos iOS seguirán funcionando cuando los usuarios actualicen sus dispositivos a iOS 10.3.

Actualmente no hay ningún problema conocido que compartir. Si tiene algún problema con iOS 10.3, póngase en contacto con el [equipo de soporte técnico de Intune](/intune/troubleshoot/contact-assisted-phone-support-for-microsoft-intune).

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Compatibilidad mejorada para usuarios de Android radicados en China<!--720444-->

Debido a la ausencia de Google Play Store en China, los dispositivos Android deben obtener aplicaciones en los mercados chinos. El Portal de empresa admitirá este flujo de trabajo al redirigir a los usuarios de Android de China para que descarguen las aplicaciones de Portal de empresa y de Outlook desde tiendas de aplicaciones locales. Esto mejorará la experiencia del usuario cuando se habiliten las directivas de acceso condicional, tanto para administración de dispositivos móviles como para la administración de aplicaciones móviles. Las aplicaciones de Portal de empresa y Outlook para Android están disponibles en los siguientes tiendas de aplicaciones chinas:

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>Procedimiento recomendado: asegúrese de que las aplicaciones del Portal de empresa están actualizadas.<!--879465-->

En diciembre de 2016, se publicó una actualización que permitía aplicar la autenticación multifactor (MFA) en un grupo de usuarios cuando registraban un dispositivo iOS, Android, Windows 8.1 + o Windows Phone 8.1 +. Esta característica no puede funcionar sin determinadas versiones de línea de base de la aplicación del Portal de empresa para iOS (2.1.17 y posteriores) y Android (5.0.3419.0 y posteriores).

Microsoft mejora continuamente Intune agregando nuevas funciones en la consola y las aplicaciones del Portal de empresa en todas las plataformas compatibles. Como resultado, solo lanza correcciones para problemas detectados en la versión actual de la aplicación del Portal de empresa. Por lo tanto, se recomienda utilizar las versiones más recientes de las aplicaciones del Portal de empresa para mejorar la experiencia de usuario.

>[!Tip]
> Pida a los usuarios que configuren sus dispositivos para actualizar automáticamente las aplicaciones de la tienda de aplicaciones correspondiente. Si ha publicado la aplicación del Portal de empresa para Android en un recurso compartido de red, puede descargar la versión más reciente desde el [Centro de descarga de Microsoft](https://www.microsoft.com/download/details.aspx?id=49140).

### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>Microsoft Teams ahora está habilitado para MAM en iOS y Android

Microsoft ha anunciado la disponibilidad general de Microsoft Teams. Las aplicaciones de Microsoft Teams actualizadas para iOS y Android están habilitadas con las funcionalidades de administración de aplicaciones móviles (MAM) de Intune, por lo que sus equipos podrán trabajar con libertad en todos los dispositivos. De esta forma, se asegurará de que las conversaciones y datos corporativos estén protegidos en todo momento. Para obtener más información, consulte el [anuncio de Microsoft Teams](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) en el blog de seguridad y la movilidad empresarial.


## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novedades en la versión preliminar pública de la experiencia de administración en Azure <!--736542-->

A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API Graph.

Nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en el portal de Azure de este mes. Durante el estado de versión preliminar, se proporcionarán funcionalidades y paridad con la consola de Intune existente de manera iterativa.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si quiere probar o examinar alguna de las nuevas características hasta que se migre su inquilino, regístrese para obtener una nueva cuenta de prueba de Intune o revise la [nueva documentación](/intune-azure/introduction/whats-new).

> [!Note]
> En cuanto a la versión preliminar de Azure Portal, estamos implementando las actualizaciones de este mes. Sin embargo, pueden que los cambios no estén disponibles inmediatamente debido a la forma en que se ha implementado el servicio de Intune.  Varios componentes del servicio deben actualizarse de manera secuencial antes de que estén disponibles las nuevas características del Portal. Busque los cambios de la versión preliminar de Azure Portal cuando se implementen este mes. Para obtener una lista completa de cambios, consulte [Novedades de la versión preliminar de Microsoft Intune](/intune-azure/introduction/whats-new).

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Roles de administración que se reemplazan en el Portal de Azure

Los roles de administración de aplicaciones móviles (MAM) existentes (colaborador, propietario y de solo lectura) usados en el portal clásico de Intune (Silverlight) se reemplazan por un conjunto completo de nuevos controles de administración basada en roles (RBAC) en el Portal de Intune Azure. Cuando haya migrado al Portal de Azure, tendrá que reasignar estos nuevos roles de administración a los administradores. Para obtener más información sobre RBAC y los nuevos roles, vea [Roles de Intune (RBAC) para Microsoft Intune](/intune-azure/access-control/role-based-access-control).


## <a name="whats-coming"></a>Próximas novedades

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->

Apple ha anunciado que, a partir de la primavera de 2017, se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS. Visite nuestro [blog de soporte técnico de Intune](https://aka.ms/compportalats) para obtener más información.

### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades en la vista previa de Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Novedades de la interfaz de usuario del portal de empresa](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [Archivo de novedades](whats-new-archive.md)

