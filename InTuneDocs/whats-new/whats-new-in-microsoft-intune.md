---
title: Novedades | Microsoft Intune
description: Conozca las novedades de este mes y las versiones anteriores de Microsoft Intune
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 0dc3fd3b4cc355bc95677ca648efdee07d1066b2
ms.contentlocale: es-es
ms.lasthandoff: 04/24/2017


---
# <a name="whats-new-in-microsoft-intune---april-2017"></a>Novedades de Microsoft Intune - Abril de 2017
Novedades en esta versión de Microsoft Intune. También puede comprobar los próximos cambios que pueda planear, así como información sobre las versiones anteriores.

> [!Note]
> Todas estas funciones se admitirán finalmente para las implementaciones de los clientes híbridos (Configuration Manager con Intune). Para obtener más información sobre las nuevas funciones híbridas, consulte nuestra [página Novedades](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuevas funcionalidades

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Se mejoró la experiencia de inicio de sesión en todas las aplicaciones del Portal de empresa para todas las plataformas <!--User Story 1132123-->

Estamos mejorando la experiencia de inicio de sesión de las aplicaciones del Portal de empresa de Intune para Android, iOS y Windows. La nueva experiencia del usuario aparecerá automáticamente en todas las plataformas de la aplicación Portal de empresa cuando Azure AD haga este cambio. Además, los usuarios ahora pueden iniciar sesión en el Portal de empresa desde otro dispositivo con un código generado de un solo uso. Esto resulta útil especialmente en casos en los que los usuarios necesitan iniciar sesión sin credenciales.

Puede encontrar las capturas de pantalla de la experiencia de inicio de sesión anterior, la nueva experiencia de inicio de sesión con credenciales y la nueva experiencia de inicio de sesión desde otro dispositivo en la página [Novedades en la interfaz de usuario de la aplicación](whats-new-in-intune-app-ui.md).

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps está disponible para Managed Browser <!--822308, 822303-->

Ahora, Microsoft MyApps ofrece una mejor compatibilidad con Managed Browser. Los usuarios de Managed Browser que no estén destinados a la administración se redirigirán directamente al servicio MyApps, donde podrán acceder a sus aplicaciones de SaaS aprovisionadas por el administrador. Los usuarios destinados a la administración de Intune seguirán teniendo acceso a MyApps desde el marcador de Managed Browser integrado.

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Nuevos iconos para Managed Browser y Portal de empresa <!--918433, 918431, 971473-->

Managed Browser recibirá iconos actualizados para la versión de la aplicación de Android y la de iOS. El nuevo icono contendrá la notificación de Intune actualizada para que sea más coherente con otras aplicaciones de Enterprise Mobility + Security (EM+S). Puede ver el icono nuevo de Managed Browser en la [página de novedades de la UI de la aplicación de Intune](whats-new-in-intune-app-ui.md).

Portal de empresa también recibirá iconos actualizados para las versiones de Windows, iOS y Android de la aplicación a fin de mejorar la coherencia con otras aplicaciones de EM+S. Estos iconos se lanzarán gradualmente en las distintas plataformas desde abril hasta finales de mayo.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicador de progreso de inicio de sesión en Portal de empresa para Android <!--953374-->

Una actualización de la aplicación Portal de empresa para Android muestra un indicador de progreso de inicio de sesión cuando el usuario inicia o reanuda la aplicación. El indicador avanza por los nuevos estados, desde "Conectando..." e "Iniciando sesión..." hasta "Comprobando los requisitos de seguridad...", antes de permitir que el usuario acceda a la aplicación. Puede ver las nuevas pantallas de la aplicación Portal de empresa para Android en la [página de novedades de la UI de la aplicación Intune](whats-new-in-intune-app-ui.md).

### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>Bloquear el acceso de las aplicaciones a SharePoint Online <!-- 679339 -->

Ahora puede crear una directiva de acceso condicional basada en aplicaciones para bloquear el acceso a [SharePoint Online](/InTune/deploy-use/mam-ca-for-sharepoint-online) a aquellas aplicaciones a las que no se apliquen directivas de protección. En el escenario de acceso condicional basado en aplicaciones, puede especificar las aplicaciones que quiere que tengan acceso a SharePoint Online mediante Azure Portal.

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscripción masiva de dispositivos Windows 10 <!-- 747607 -->

Puede unir grandes cantidades de dispositivos que ejecutan Windows 10 Creator Update a Azure Active Directory e Intune con el Diseñador de configuración de Windows (WCD). Para habilitar la [inscripción masiva de MDM](/intune/deploy-use/bulk-enroll-windows) para el inquilino de Azure AD, cree un paquete de aprovisionamiento que una dispositivos al inquilino de Azure AD a través del Diseñador de configuración de Windows y aplique el paquete a los dispositivos corporativos que desea inscribir y administrar de forma masiva. Una vez que el paquete se aplica a los dispositivos, se unirán a Azure AD, se inscribirán en Intune y estarán listos para que los usuarios de Azure AD inicien sesión.  Los usuarios de Azure AD son usuarios estándar en estos dispositivos y reciben las aplicaciones requeridas y las directivas asignadas. En este momento, no se admiten los escenarios de autoservicio ni de Portal de empresa.

## <a name="notices"></a>Notificaciones

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a escenarios de inscripción de Apple <!--951869-->

Para las cuentas de Intune creadas después de enero de 2017, Intune ha habilitado el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo Inscribir los dispositivos en el Portal de vista previa de Azure. Anteriormente, solo se podía acceder a la versión preliminar de inscripción de Apple desde los vínculos del portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requerirán una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero pronto habrá detalles disponibles. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta existente no puede acceder a la versión preliminar.

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Novedades para Appx en Intune en Azure<!-- 1000270 -->

Como parte de la migración a Intune en Azure, vamos a llevar a cabo tres cambios en appx:

1. Incorporación de un nuevo tipo de aplicación appx en la consola clásica de Intune que solo se puede implementar en dispositivos inscritos en MDM.
2. Reutilización del tipo de aplicación appx existente para que solo se dirija a equipos administrados a través del agente de PC de Intune.
3. Conversión de todos los appx existentes en appx MDM con la migración.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto ahora?

Esto no afectará a ninguna de sus implementaciones actuales en dispositivos administrados a través del agente de PC de Intune. Sin embargo, tras la migración, no podrá implementar esos appx migrados a ningún dispositivo nuevo que se administre a través del agente de PC de Intune que estuviera establecido como destino previamente.

#### <a name="what-action-do-i-need-to-take"></a>Qué acción necesito realizar

Tras la migración, debe volver a cargar el appx de nuevo como un appx de PC si desea hacer nuevas implementaciones de PC. Para más información, consulte [Appx changes in Intune on Azure](https://aka.ms/appxchange) (Cambios de appx en Intune en Azure) en el blog del equipo de soporte técnico de Intune.  


## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novedades de la versión preliminar pública de la experiencia de administración de Intune en Azure <!--736542-->

A principios de 2017, migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración versátil e integrada de los flujos de trabajo de EMS principales en una plataforma de servicio moderna extensible mediante API Graph.

Los nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en Azure Portal este mes. Mientras se esté en el estado de versión preliminar, las funcionalidades y la paridad con la consola de Intune existente se entregarán de forma iterativa.

La experiencia de administración de Azure Portal usará la nueva funcionalidad de agrupación y destino ya anunciadas; cuando el inquilino existente se migra a la nueva experiencia de agrupación, también se migra a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si desea probar o consultar cualquiera de las nuevas funcionalidades hasta que se migre el inquilino, regístrese para una nueva cuenta de prueba de Intune o consulte la [nueva documentación](/intune-azure/introduction/whats-new).

> [!Note]
> En cuanto a la versión preliminar de Azure Portal, estamos implementando las actualizaciones de este mes. Sin embargo, puede que los cambios no estén disponibles inmediatamente debido a la forma en que se ha implementado el servicio de Intune.  Varios componentes del servicio deben actualizarse de manera secuencial antes de que estén disponibles las nuevas características del portal. Busque los cambios de la versión preliminar de Azure Portal cuando se implementen este mes. Para obtener una lista completa de cambios, consulte [Novedades de la versión preliminar de Microsoft Intune](/intune-azure/introduction/whats-new).

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Roles de administración que se reemplazan en Azure Portal

Los roles de administración de aplicaciones móviles (MAM) existentes (Colaborador, Propietario y Solo lectura) usados en el portal clásico de Intune (Silverlight) se reemplazan por un conjunto completo de nuevos controles de administración basada en roles (RBAC) en el portal de Intune Azure. Cuando haya migrado a Azure Portal, tendrá que reasignar estos nuevos roles de administración a los administradores. Para más información sobre RBAC y los nuevos roles, consulte [Roles de Intune (RBAC) para Microsoft Intune](/intune-azure/access-control/role-based-access-control).


## <a name="whats-coming"></a>Próximas novedades

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Plan de cambio: Intune está cambiando la experiencia del portal Partner de Intune<!-- 1050016 -->

Estamos quitando la página Partner de Intune de manage.microsoft.com a partir de la actualización de servicio de mediados de mayo de 2017.  

Si es un administrador de partners, ya no podrá ver y realizar acciones en nombre de sus clientes desde la página Partner de Intune pero, en su lugar, tendrá que iniciar sesión en uno de los dos portales de partners de Microsoft.

Tanto el [Centro de partners de Microsoft](https://partnercenter.microsoft.com/) como el [Centro de administración de partners de Microsoft Office 365](https://portal.office.com/) le permitirá iniciar sesión en las cuentas de cliente que administra. En adelante, como partner, use uno de estos sitios para administrar a sus clientes. 


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requiere actualizaciones para su funcionalidad de seguridad de transporte de aplicaciones <!--748318-->

A partir de la primavera de 2017, Apple ha anunciado que exigirán requisitos específicos para la seguridad de transporte de aplicaciones (ATS). ATS se utiliza para exigir una seguridad más estricta en todas las comunicaciones de aplicación a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones de Portal de empresa para iOS. Revise nuestro [blog de soporte técnico de Intune](https://aka.ms/compportalats) para más detalles.

### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de la plataforma en la nube](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades de la versión preliminar de Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Novedades de la interfaz de usuario de Portal de empresa](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [Archivo de novedades](whats-new-archive.md)

