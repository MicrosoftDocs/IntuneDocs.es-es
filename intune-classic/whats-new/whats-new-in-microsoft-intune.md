---
title: Novedades | Microsoft Docs
description: Conozca las novedades de las versiones anteriores y de este mes de Microsoft Intune
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2e6452a066aa7eaeb295a3b531d83dc3b632bcf5
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---
# <a name="whats-new-in-microsoft-intune---april-2017"></a>Novedades de Microsoft Intune: abril de 2017
Conozca las novedades de esta versión de Microsoft Intune. También podrá obtener información sobre los próximos cambios para los que debe prepararse y sobre las versiones anteriores.

> [!Note]
> Todas estas características finalmente se admitirán para las implementaciones de clientes híbridos (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuevas funcionalidades

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps disponible para Managed Browser <!--822308, 822303-->

Microsoft MyApps tiene ahora mejor compatibilidad con Managed Browser. A los usuarios de Managed Browser que no estén destinados a la administración se les llevará directamente al servicio MyApps, donde podrán acceder a sus aplicaciones SaaS aprovisionadas por el administrador. Los usuarios que tengan como destino la administración de Intune seguirán teniendo acceso a MyApps desde el marcador integrado de Managed Browser.

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Nuevos iconos para Managed Browser y el Portal de empresa <!--918433, 918431, 971473-->

Managed Browser está recibiendo iconos actualizados para las versiones de iOS y Android de la aplicación. El nuevo icono contendrá el distintivo de Intune actualizado para que sea más coherente con otras aplicaciones de Enterprise Mobility + Security (EM+S). Puede ver el nuevo icono de Managed Browser en la página de [novedades de la interfaz de usuario de la aplicación de Intune](whats-new-in-intune-app-ui.md).

El Portal de empresa también está recibiendo iconos actualizados para las versiones de Windows, iOS y Android de la aplicación con el objetivo de mejorar la coherencia con otras aplicaciones de EM+S. Estos iconos se lanzarán gradualmente en las plataformas desde abril hasta finales de mayo.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicador de progreso de inicio de sesión en Portal de empresa de Android <!--953374-->

Una actualización de la aplicación Portal de empresa de Android muestra un indicador de progreso de inicio de sesión cuando el usuario inicia o reanuda la aplicación. El indicador avanza por nuevos estados en el siguiente orden: "Conectando...", "Iniciando sesión..." y "Checking for security requirements..." (Comprobando requisitos de seguridad) antes de permitir que el usuario acceda a la aplicación. Puede ver las nuevas pantallas de la aplicación Portal de empresa en la página de [novedades de la interfaz de usuario de la aplicación de Intune](whats-new-in-intune-app-ui.md).

### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>Bloquear el acceso de las aplicaciones a SharePoint Online <!-- 679339 -->

Ahora puede crear una directiva de acceso condicional basada en aplicaciones para bloquear el acceso a [SharePoint Online](/intune-classic/deploy-use/mam-ca-for-sharepoint-online) a aquellas aplicaciones a las que no se apliquen directivas de protección. En el escenario de acceso condicional basado en aplicaciones, puede especificar las aplicaciones que quiere que tengan acceso a SharePoint Online mediante Azure Portal.

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Compatibilidad del inicio de sesión único desde el Portal de empresa para iOS con Outlook para iOS <!--834012-->
Los usuarios ya no tienen que iniciar sesión en la aplicación de Outlook si ya lo han hecho en la aplicación Portal de empresa para iOS en el mismo dispositivo con la misma cuenta. Cuando los usuarios inicien la aplicación de Outlook, podrán seleccionar su cuenta e iniciar sesión automáticamente. También estamos trabajando para agregar esta funcionalidad en otras aplicaciones de Microsoft.

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Mejora de los mensajes de estado en la aplicación Portal de empresa para iOS <!--744866-->
Ahora se mostrarán nuevos mensajes de error más específicos en la aplicación Portal de empresa para iOS con el objetivo de ofrecer información más accesible sobre lo que ocurre en los dispositivos. Estos casos de error anteriormente se incluían en un mensaje de error general titulado "Portal de empresa no disponible temporalmente". Además, si un usuario inicia el Portal de empresa en iOS sin conexión a Internet, ahora aparecerá una barra de estado persistente en la página principal con el mensaje "No hay conexión a Internet".

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Mejora del estado de instalación de la aplicación para la aplicación Portal de empresa de Windows 10 <!--676495-->

A continuación se mencionan las nuevas mejoras para las instalaciones de aplicaciones iniciadas en la aplicación Portal de empresa de Windows 10:
-    Informe de progreso de instalación más rápido para paquetes MSI
-    Informe de progreso de instalación más rápido para aplicaciones modernas en dispositivos que ejecutan la Actualización de aniversario de Windows 10 o superior
-    Nueva barra de progreso para instalaciones de aplicaciones modernas en dispositivos que ejecutan la Actualización de aniversario de Windows 10 o superior

Puede ver la nueva barra de progreso en la [página de novedades de la interfaz de usuario de la aplicación de Intune](whats-new-in-intune-app-ui.md).

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscripción masiva de dispositivos Windows 10 <!-- 747607 -->

Ya puede unir a un gran número de dispositivos que ejecutan Windows 10 Creators Update con Azure Active Directory y Intune usando el Diseñador de configuración de Windows para su inquilino de Azure AD, crear un paquete de aprovisionamiento que una dispositivos a su inquilino de Azure AD mediante el Diseñador de configuración de Windows, y aplicar el paquete a los dispositivos empresariales que quiera administrar e inscribir en masa. Una vez que el paquete se aplica a los dispositivos, se unirán a Azure AD, se inscribirán en Intune y estarán listos para que los usuarios de Azure AD inicien sesión.  Los usuarios de Azure AD son usuarios estándar en estos dispositivos y reciben las aplicaciones requeridas y las directivas asignadas. En este momento, no se admiten los escenarios de autoservicio ni de portal de empresa.

## <a name="notices"></a>Notificaciones

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->

Para las cuentas de Intune creadas después de enero de 2017, Intune ha habilitado el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en el portal de vista previa de Azure. Anteriormente, la vista previa de inscripción de Apple solo era accesible desde los vínculos al portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requerirán una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero la información estará disponible tan pronto como sea posible. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta no tiene acceso a la versión preliminar.

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Novedades para Appx en Intune en Azure <!-- 1000270 -->

Como parte de la migración a Intune en Azure, estamos realizando tres cambios de appx:

1. Agregar un nuevo tipo de aplicación appx en la consola clásica de Intune que solo se puede implementar en dispositivos inscritos en MDM.
2. Reasignar el tipo de aplicación appx existente para que solo esté dirigido a equipos administrados mediante el agente de PC de Intune.
3. Convertir todos los appxs existentes en appxs de MDM con la migración.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?

Esto no afectará a ninguna de sus implementaciones existentes en dispositivos que estén administrados mediante el agente de PC de Intune. No obstante, tras la migración, no podrá implementar esos appxs migrados en ningún dispositivo nuevo administrado mediante el agente de PC de Intune que no estuviera seleccionado anteriormente.

#### <a name="what-action-do-i-need-to-take"></a>Acciones necesarias

Tras la migración, deberá volver a cargar el appx de nuevo como un appx de PC si quiere realizar nuevas implementaciones de PC. Para obtener más información, consulte [Appx changes in Intune on Azure](https://aka.ms/appxchange) (Cambios de appx en Intune en Azure) en el blog del equipo de soporte técnico de Intune.  

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novedades en la versión preliminar pública de la experiencia de administración en Azure <!--736542-->

A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API Graph.

Nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en el portal de Azure de este mes. Durante el estado de versión preliminar, se proporcionarán funcionalidades y paridad con la consola de Intune existente de manera iterativa.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si quiere probar o examinar alguna de las nuevas características hasta que se migre su inquilino, regístrese para obtener una nueva cuenta de prueba de Intune o revise la [nueva documentación](/intune/whats-new).

> [!Note]
> En cuanto a la versión preliminar de Azure Portal, estamos implementando las actualizaciones de este mes. Sin embargo, pueden que los cambios no estén disponibles inmediatamente debido a la forma en que se ha implementado el servicio de Intune.  Varios componentes del servicio deben actualizarse de manera secuencial antes de que estén disponibles las nuevas características del Portal. Busque los cambios de la versión preliminar de Azure Portal cuando se implementen este mes. Para obtener una lista completa de cambios, consulte [Novedades de la versión preliminar de Microsoft Intune](/intune/whats-new).

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Roles de administración que se reemplazan en el Portal de Azure

Los roles de administración de aplicaciones móviles (MAM) existentes (colaborador, propietario y de solo lectura) usados en el portal clásico de Intune (Silverlight) se reemplazan por un conjunto completo de nuevos controles de administración basada en roles (RBAC) en el Portal de Intune Azure. Cuando haya migrado al Portal de Azure, tendrá que reasignar estos nuevos roles de administración a los administradores. Para obtener más información sobre RBAC y los nuevos roles, vea [Roles de Intune (RBAC) para Microsoft Intune](/intune/role-based-access-control).

## <a name="whats-coming"></a>Próximas novedades

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Se mejoró la experiencia de inicio de sesión en todas las aplicaciones del Portal de empresa para todas las plataformas <!--User Story 1132123-->

Estamos anunciando un cambio que aparecerá en los próximos meses que mejorará la experiencia de inicio de sesión para las aplicaciones del Portal de empresa de Intune para Android, iOS y Windows. La nueva experiencia del usuario aparecerá automáticamente en todas las plataformas de la aplicación Portal de empresa cuando Azure AD haga este cambio. Además, los usuarios ahora pueden iniciar sesión en Portal de empresa desde otro dispositivo con un código generado de un solo uso. Esto resulta útil especialmente en casos en los que los usuarios necesitan iniciar sesión sin credenciales.

Puede encontrar capturas de pantalla de la experiencia de inicio de sesión anterior, la nueva experiencia de inicio de sesión con credenciales y la nueva experiencia de inicio de sesión desde otro dispositivo en la página [Novedades en la UI de la aplicación](whats-new-in-intune-app-ui.md).

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Plan de cambio: Intune está cambiando la experiencia del portal Partner de Intune<!-- 1050016 -->

Estamos quitando la página Partner de Intune de manage.microsoft.com a partir de la actualización de servicio de mediados de mayo de 2017.  

Si es un administrador de partners, ya no podrá ver y realizar acciones en nombre de sus clientes desde la página Partner de Intune pero, en su lugar, tendrá que iniciar sesión en uno de los dos portales de partners de Microsoft.

Tanto el [Centro de partners de Microsoft](https://partnercenter.microsoft.com/) como el [Centro de administración de partners de Microsoft Office 365](https://portal.office.com/) le permitirá iniciar sesión en las cuentas de cliente que administra. En adelante, como partner, use uno de estos sitios para administrar a sus clientes.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->

Apple ha anunciado que se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS.

Hay disponible una versión de la aplicación Portal de empresa para iOS a través del programa Apple TestFlight que aplica los nuevos requisitos de ATS. Si desea probarla para que pueda experimentar el cumplimiento de ATS, envíe un correo electrónico a <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> con su nombre, apellidos, dirección de correo electrónico y nombre de la empresa. Visite nuestro [blog de soporte técnico de Intune](https://aka.ms/compportalats) para obtener más información.

### <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades en la vista previa de Azure](https://docs.microsoft.com/intune/whats-new)
* [Novedades de la interfaz de usuario del portal de empresa](/intune-classic/whats-new/whats-new-in-company-portal-ui)
* [Archivo de novedades](whats-new-archive.md)

