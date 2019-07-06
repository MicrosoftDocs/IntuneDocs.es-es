---
ms.openlocfilehash: 448ec3aaa9bc9ad09e54d7dd78d4f08a4adae010
ms.sourcegitcommit: ede86a3cb094c12e3e218b956abb9935bec76902
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2019
ms.locfileid: "67571973"
---
## <a name="april-2017"></a>Abril de 2017

### <a name="new-capabilities"></a>Nuevas funcionalidades

#### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps disponible para Managed Browser <!--822308, 822303-->

Microsoft MyApps tiene ahora mejor compatibilidad con Managed Browser. A los usuarios de Managed Browser que no estén destinados a la administración se les llevará directamente al servicio MyApps, donde podrán acceder a sus aplicaciones SaaS aprovisionadas por el administrador. Los usuarios que tengan como destino la administración de Intune seguirán teniendo acceso a MyApps desde el marcador integrado de Managed Browser.

#### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Nuevos iconos para Managed Browser y el Portal de empresa <!--918433, 918431, 971473-->

Managed Browser está recibiendo iconos actualizados para las versiones de iOS y Android de la aplicación. El nuevo icono contendrá el distintivo de Intune actualizado para que sea más coherente con otras aplicaciones de Enterprise Mobility + Security (EM+S). Puede ver el nuevo icono de Managed Browser en la página de [novedades de la interfaz de usuario de la aplicación de Intune](/intune/whats-new-app-ui).

El Portal de empresa también está recibiendo iconos actualizados para las versiones de Windows, iOS y Android de la aplicación con el objetivo de mejorar la coherencia con otras aplicaciones de EM+S. Estos iconos se lanzarán gradualmente en las plataformas desde abril hasta finales de mayo.

#### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicador de progreso de inicio de sesión en Portal de empresa de Android <!--953374-->

Una actualización de la aplicación Portal de empresa de Android muestra un indicador de progreso de inicio de sesión cuando el usuario inicia o reanuda la aplicación. El indicador avanza por los nuevos estados, desde "Conectando..." e "Iniciando sesión..." hasta "Comprobando los requisitos de seguridad...", antes de permitir que el usuario acceda a la aplicación. Puede ver las nuevas pantallas de la aplicación Portal de empresa en la página de [novedades de la interfaz de usuario de la aplicación de Intune](/intune/whats-new-app-ui).

#### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>Bloqueo del acceso de las aplicaciones a SharePoint Online <!-- 679339 -->

Ahora puede crear una directiva de acceso condicional basada en aplicaciones para bloquear el acceso a [SharePoint Online](/intune-classic/deploy-use/mam-ca-for-sharepoint-online) a aquellas aplicaciones a las que no se apliquen directivas de protección. En el escenario de acceso condicional basado en aplicaciones, puede especificar las aplicaciones que quiere que tengan acceso a SharePoint Online mediante Azure Portal.

#### <a name="single-sign-in-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Compatibilidad del inicio de sesión único desde el Portal de empresa para iOS con Outlook para iOS <!--834012-->
Los usuarios ya no tienen que iniciar sesión en la aplicación de Outlook si ya lo han hecho en la aplicación Portal de empresa para iOS en el mismo dispositivo con la misma cuenta. Cuando los usuarios inicien la aplicación de Outlook, podrán seleccionar su cuenta e iniciar sesión automáticamente. También estamos trabajando para agregar esta funcionalidad en otras aplicaciones de Microsoft.

#### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Mejora de los mensajes de estado en la aplicación Portal de empresa para iOS <!--744866-->
Ahora se mostrarán nuevos mensajes de error más específicos en la aplicación Portal de empresa para iOS con el objetivo de ofrecer información más accesible sobre lo que ocurre en los dispositivos. Estos casos de error anteriormente se incluían en un mensaje de error general titulado "Portal de empresa no disponible temporalmente". Además, si un usuario inicia el Portal de empresa en iOS sin conexión a Internet, ahora aparecerá una barra de estado persistente en la página principal con el mensaje "No hay conexión a Internet".

#### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Mejora del estado de instalación de la aplicación para la aplicación Portal de empresa de Windows 10 <!--676495-->

A continuación se mencionan las nuevas mejoras para las instalaciones de aplicaciones iniciadas en la aplicación Portal de empresa de Windows 10:
- Informe de progreso de instalación más rápido para paquetes MSI
- Informe de progreso de instalación más rápido para aplicaciones modernas en dispositivos que ejecutan la Actualización de aniversario de Windows 10 o superior
- Nueva barra de progreso para instalaciones de aplicaciones modernas en dispositivos que ejecutan la Actualización de aniversario de Windows 10 o superior

Puede ver la nueva barra de progreso en la [página de novedades de la interfaz de usuario de la aplicación de Intune](/intune/whats-new-app-ui).

#### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscripción masiva de dispositivos Windows 10 <!-- 747607 -->

Ahora puede unir grandes cantidades de dispositivos que ejecutan Windows 10 Creator Update a Azure Active Directory e Intune con Windows Configuration Designer (WCD). Para habilitar la [inscripción masiva de MDM](/intune-classic/deploy-use/bulk-enroll-windows) para el inquilino de Azure AD, cree un paquete de aprovisionamiento que una dispositivos al inquilino de Azure AD a través de Windows Configuration Designer y aplique el paquete a los dispositivos corporativos que desea inscribir y administrar de forma masiva. Una vez que el paquete se haya aplicado a los dispositivos, se unirán a Azure AD, se inscribirán en Intune y estarán listos para que los usuarios de Azure AD inicien sesión.  Los usuarios de Azure AD son usuarios estándar en estos dispositivos y reciben las aplicaciones requeridas y las directivas asignadas. En este momento, no se admiten los escenarios de autoservicio ni de portal de empresa.

### <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novedades en la versión preliminar pública de la experiencia de administración de Intune en Azure <!--736542-->

A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante API de Graph.

Nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en el portal de Azure de este mes. Durante el estado de versión preliminar, se proporcionarán funcionalidades y paridad con la consola de Intune existente de manera iterativa.

La experiencia de administración de Azure Portal usará la nueva funcionalidad de agrupación y destino ya anunciadas; cuando el inquilino existente se migra a la nueva experiencia de agrupación, también se migra a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si quiere probar o examinar alguna de las nuevas características hasta que se migre su inquilino, regístrese para obtener una nueva cuenta de prueba de Intune o revise la [nueva documentación](/intune/whats-new).

Puede encontrar las novedades en la vista previa de Intune en Azure [aquí](/intune/whats-new).

### <a name="notices"></a>Notificaciones

#### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->

Para las cuentas de Intune creadas después de enero de 2017, Intune ha habilitado el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en el portal de vista previa de Azure. Anteriormente, solo se podía acceder a la versión preliminar de inscripción de Apple desde los vínculos del portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requerirán una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero pronto habrá detalles disponibles. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta no tiene acceso a la versión preliminar.

#### <a name="whats-coming-for-appx-in-intune-in-the-azure-portal----1000270---"></a>Novedades para Appx en Intune en Azure Portal <!-- 1000270 -->

Como parte de la migración a Intune en Azure Portal, estamos realizando tres cambios de appx:

1. Agregar un nuevo tipo de aplicación appx en la consola clásica de Intune que solo se puede implementar en dispositivos inscritos en MDM.
2. Reasignar el tipo de aplicación appx existente para que solo esté dirigido a equipos administrados mediante el agente de PC de Intune.
3. Convertir todos los appxs existentes en appxs de MDM con la migración.

##### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?

Esto no afectará a ninguna de sus implementaciones actuales en dispositivos administrados a través del agente de PC de Intune. No obstante, tras la migración, no podrá implementar esos appxs migrados en ningún dispositivo nuevo administrado mediante el agente de PC de Intune que no estuviera seleccionado anteriormente.

##### <a name="what-action-do-i-need-to-take"></a>Acciones necesarias

Tras la migración, deberá volver a cargar el appx de nuevo como un appx de PC si quiere realizar nuevas implementaciones de PC. Para obtener más información, consulte [Appx changes in Intune in the Azure portal](https://aka.ms/appxchange) (Cambios de appx en Intune en Azure Portal) en el blog del equipo de soporte técnico de Intune.  

#### <a name="administration-roles-being-replaced-in-azure-portal"></a>Roles de administración que se reemplazan en el Portal de Azure

Los roles de administración de aplicaciones móviles (MAM) existentes (colaborador, propietario y de solo lectura) usados en el portal clásico de Intune (Silverlight) se reemplazan por un conjunto completo de nuevos controles de administración basada en roles (RBAC) en el Portal de Intune Azure. Cuando haya migrado al Portal de Azure, tendrá que reasignar estos nuevos roles de administración a los administradores. Para más información sobre RBAC y los nuevos roles, consulte [Roles de Intune (RBAC) para Microsoft Intune](/intune/role-based-access-control).

### <a name="whats-coming"></a>Próximas novedades

#### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Mejora de la experiencia de inicio de sesión en todas las aplicaciones de Portal de empresa para todas las plataformas <!--User Story 1132123-->

Estamos anunciando un cambio que aparecerá en los próximos meses que mejorará la experiencia de inicio de sesión para las aplicaciones de Portal de empresa de Intune para Android, iOS y Windows. La nueva experiencia del usuario aparecerá automáticamente en todas las plataformas de la aplicación Portal de empresa cuando Azure AD haga este cambio. Además, los usuarios ahora pueden iniciar sesión en Portal de empresa desde otro dispositivo con un código generado de un solo uso. Esto resulta útil especialmente en casos en los que los usuarios necesitan iniciar sesión sin credenciales.

Puede encontrar capturas de pantalla de la experiencia de inicio de sesión anterior, la nueva experiencia de inicio de sesión con credenciales y la nueva experiencia de inicio de sesión desde otro dispositivo en la página [Novedades en la UI de la aplicación](/intune/whats-new-app-ui).

#### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Plan de cambio: Intune está cambiando la experiencia del portal Partner de Intune <!-- 1050016 -->

Estamos quitando la página Partner de Intune de manage.microsoft.com a partir de la actualización de servicio de mediados de mayo de 2017.  

Si es un administrador de partners, ya no podrá ver y realizar acciones en nombre de sus clientes desde la página Partner de Intune pero, en su lugar, tendrá que iniciar sesión en uno de los dos portales de partners de Microsoft.

Tanto el [Centro de partners de Microsoft](https://partnercenter.microsoft.com/) como el [Centro de administración de Microsoft 365](https://admin.microsoft.com/) le permitirán iniciar sesión en las cuentas de cliente que administre. En adelante, como partner, use uno de estos sitios para administrar a sus clientes.


#### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->

Apple ha anunciado que se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS.

Hay disponible una versión de la aplicación Portal de empresa para iOS a través del programa Apple TestFlight que aplica los nuevos requisitos de ATS. Si desea probarla para que pueda experimentar el cumplimiento de ATS, envíe un correo electrónico a <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> con su nombre, apellidos, dirección de correo electrónico y nombre de la empresa. Visite nuestro [blog de soporte técnico de Intune](https://aka.ms/compportalats) para obtener más información.

## <a name="march-2017"></a>Marzo de 2017

### <a name="new-capabilities"></a>Nuevas funcionalidades

#### <a name="support-for-skycure"></a>Compatibilidad con Skycure

Ahora puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Skycure, una solución de defensa contra amenazas móviles integrada con Microsoft Intune. El riesgo se evalúa según la telemetría recopilada de dispositivos que ejecutan Skycure, que incluye:

- Defensa física
- Defensa de red
- Defensa de aplicaciones
- Defensa de vulnerabilidades

Puede configurar directivas de acceso condicional de EMS basadas en la evaluación de riesgos de Skycure habilitada mediante las directivas de cumplimiento de dispositivos de Intune. Puede usar estas directivas para permitir o bloquear el acceso de dispositivos no compatibles a recursos corporativos en función de las amenazas detectadas. Para obtener más información, vea [Conector de Mobile Threat Defense de Skycure](/intune-classic/deploy-use/skycure-mobile-threat-defense-connector).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nueva experiencia del usuario en la aplicación Portal de empresa para Android <!--621622-->

La aplicación de Portal de empresa para Android va a actualizar su interfaz de usuario para un aspecto más moderno y una mejor experiencia de usuario. Las actualizaciones importantes son:

- Colores: los encabezados de la pestaña de Portal de empresa están coloreados según la información de la marca definida por TI.
- Aplicaciones: en la pestaña **Aplicaciones**, los botones **Aplicaciones destacadas** y **Todas las aplicaciones** se han actualizado.
- Buscar: en la pestaña **Aplicaciones**, el botón **Buscar** ahora es un botón de acción flotante.
- Aplicaciones de navegación: la vista **Todas las aplicaciones** muestra una vista con las pestañas **Destacadas**, **Todas** y **Categorías** para navegar más fácilmente.
- Soporte: las pestañas **Mis dispositivos** y **Contactar con TI** se actualizan para mejorar la legibilidad.

Para obtener más información sobre estos cambios, consulte [Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune](/intune/whats-new-app-ui).

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Los dispositivos no administrados pueden acceder a aplicaciones asignadas <!--664691-->

Como parte de los cambios de diseño en el sitio web del portal de empresa, los usuarios de iOS y Android podrán instalar aplicaciones asignadas a ellos como "disponibles sin inscripción" en sus dispositivos no administrados. Con sus credenciales de Intune, los usuarios podrán iniciar sesión en el sitio web del Portal de empresa y ver la lista de aplicaciones asignadas. Los paquetes de aplicación de las aplicaciones "disponibles sin inscripción" se encuentran disponibles para descargar a través del sitio web del portal de empresa. Las aplicaciones que requieren la inscripción para la instalación no se ven afectadas por este cambio, ya que se les pedirá a los usuarios que inscriban su dispositivo si quieren instalar esas aplicaciones.

#### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Script de firma para Portal de empresa para Windows 10 <!--941642-->

Si necesita descargar y transferir localmente la aplicación del Portal de empresa para Windows 10, ahora puede usar un script para simplificar y agilizar el proceso de firma de aplicaciones en su organización.   Para descargar el script y las instrucciones de uso, consulte el artículo [Microsoft Intune Signing Script for Windows 10 Company Portal](https://aka.ms/win10cpscript) (Script de firma de Microsoft Intune para el Portal de empresa para Windows 10) de la Galería de TechNet. Para obtener más información sobre este anuncio, consulte [Updating your Windows 10 Company Portal app](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) (Actualización de la aplicación del Portal de empresa para Windows 10) en el blog del equipo de asistencia técnica de Intune.


### <a name="notices"></a>Notificaciones

#### <a name="support-for-ios-103"></a>Compatibilidad con iOS 10.3

La versión de iOS 10.3 empezó a implementarse el 27 de marzo de 2017 a los usuarios de iOS. Todos los escenarios MDM y MAM existentes de Intune son compatibles con la versión más reciente del sistema operativo de Apple. Se prevé que todas las características existentes de Intune actualmente disponibles para administrar dispositivos iOS seguirán funcionando cuando los usuarios actualicen sus dispositivos a iOS 10.3.

Actualmente no hay ningún problema conocido que compartir. Si tiene algún problema con iOS 10.3, póngase en contacto con el [equipo de soporte técnico de Intune](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune).

#### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Compatibilidad mejorada para usuarios de Android radicados en China <!--720444-->

Debido a la ausencia de Google Play Store en China, los dispositivos Android deben obtener aplicaciones en los mercados chinos. El Portal de empresa admitirá este flujo de trabajo al redirigir a los usuarios de Android de China para que descarguen las aplicaciones de Portal de empresa y de Outlook desde tiendas de aplicaciones locales. Esto mejorará la experiencia del usuario cuando se habiliten las directivas de acceso condicional, tanto para administración de dispositivos móviles como para la administración de aplicaciones móviles. Las aplicaciones de Portal de empresa y Outlook para Android están disponibles en los siguientes tiendas de aplicaciones chinas:

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

#### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>Procedimiento recomendado: asegurarse de que las aplicaciones de Portal de empresa están actualizadas <!--879465-->

En diciembre de 2016, se publicó una actualización que permitía aplicar la autenticación multifactor (MFA) en un grupo de usuarios cuando registraban un dispositivo iOS, Android, Windows 8.1 + o Windows Phone 8.1 +. Esta característica no puede funcionar sin determinadas versiones de línea de base de la aplicación del Portal de empresa para iOS (2.1.17 y posteriores) y Android (5.0.3419.0 y posteriores).

Microsoft mejora continuamente Intune agregando nuevas funciones en la consola y las aplicaciones del Portal de empresa en todas las plataformas compatibles. Como resultado, solo lanza correcciones para problemas detectados en la versión actual de la aplicación del Portal de empresa. Por lo tanto, se recomienda utilizar las versiones más recientes de las aplicaciones del Portal de empresa para mejorar la experiencia de usuario.

>[!Tip]
> Pida a los usuarios que configuren sus dispositivos para actualizar automáticamente las aplicaciones de la tienda de aplicaciones correspondiente. Si ha publicado la aplicación del Portal de empresa para Android en un recurso compartido de red, puede descargar la versión más reciente desde el [Centro de descarga de Microsoft](https://www.microsoft.com/download/details.aspx?id=49140).

#### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>Microsoft Teams ahora está habilitado para MAM en iOS y Android

Microsoft ha anunciado la disponibilidad general de Microsoft Teams. Las aplicaciones de Microsoft Teams actualizadas para iOS y Android están habilitadas con las funcionalidades de administración de aplicaciones móviles (MAM) de Intune, por lo que sus equipos podrán trabajar con libertad en todos los dispositivos. De esta forma, se asegurará de que las conversaciones y datos corporativos estén protegidos en todo momento. Para obtener más información, consulte el [anuncio de Microsoft Teams](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) en el blog de seguridad y la movilidad empresarial.


## <a name="february-2017"></a>Febrero de 2017

### <a name="new-capabilities"></a>Nuevas funcionalidades

### <a name="modernizing-the-company-portal-website---753980--"></a>Renovación del sitio web del portal de empresa <!--753980-->
El sitio web del portal de empresa admitirá aplicaciones destinadas a aquellos usuarios que no tienen dispositivos administrados. El sitio web se asemejará a otros productos y servicios de Microsoft gracias a una nueva combinación de colores de contraste, ilustraciones dinámicas y un “menú hamburguesa”, ![Pequeña imagen del menú hamburguesa que se ha agregado en la esquina superior izquierda del sitio web del portal de empresa](/intune/whats-new-app-ui).

### <a name="notices"></a>Notificaciones

#### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>La migración de grupo no requiere actualizaciones a grupos ni directivas para dispositivos iOS <!--898837-->
Para cada grupo de dispositivos de Intune previamente asignado mediante un perfil de inscripción de dispositivos corporativos, se creará un grupo de dispositivos dinámico correspondiente en AAD según el nombre del perfil de inscripción de dispositivos corporativos, durante la migración a grupos de dispositivos de Azure Active Directory. Esto garantizará que, según se inscriban dispositivos, estos se agrupen de manera automática y reciban las mismas directivas y aplicaciones que el grupo de Intune original.

Una vez que un inquilino empieza el proceso de migración para agrupar y seleccionar el destino, Intune creará de forma automática un grupo dinámico de AAD para que se corresponda con un grupo de Intune destinado mediante un perfil de inscripción de dispositivos corporativos. Si el administrador de Intune elimina el grupo de destino de Intune, no se eliminará el grupo de AAD dinámico correspondiente. Se borrarán los miembros del grupo y la consulta dinámica, pero el propio grupo permanecerá hasta que el administrador de TI lo quite a través del portal de AAD.

De forma similar, si el administrador de TI cambia qué grupo de Intune es el destino de un perfil de inscripción de dispositivos corporativos, Intune crea un nuevo grupo dinámico que refleje la nueva asignación de perfil, pero no quitará el grupo dinámico creado para la asignación anterior.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Administración predeterminada de los dispositivos de escritorio Windows mediante la configuración de Windows <!--663050-->
El comportamiento predeterminado para inscribir equipos de escritorio de Windows 10 está cambiando. Las nuevas inscripciones seguirán el típico flujo de inscripción del agente MDM en lugar del agente de PC. El sitio web de portal de empresa proporcionará a los usuarios de escritorio de Windows 10 las instrucciones de inscripción que les guiarán a través del proceso de agregar equipos de escritorio de Windows 10 como dispositivos móviles. Esto no afectará a los PC inscritos en estos momentos, y su organización todavía puede administrar equipos de escritorio de Windows 10 con el agente de PC [si lo prefiere](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Mejora de la asistencia de la administración de aplicaciones móviles para el borrado selectivo <!--581242-->
A los usuarios finales se les proporcionarán instrucciones adicionales sobre cómo recuperar el acceso a los datos profesionales o educativos si estos se quitaron automáticamente debido a la directiva "Intervalo sin conexión antes de que se borren los datos de la aplicación".<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Los vínculos de Portal de empresa para iOS se abren dentro de la aplicación <!--665954-->
Los vínculos dentro de la aplicación de portal de empresa para iOS, incluidos los de documentación y aplicaciones, se abrirán directamente en la aplicación de portal de empresa con una vista desde la aplicación de Safari. Esta actualización se enviará por separado desde la actualización del servicio en enero.

#### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Nueva dirección del servidor MDM para dispositivos Windows <!--893007-->
Se producirá un error en la inscripción del dispositivo si los usuarios de Windows y Windows Phone especifican __manage.microsoft.com__ como la dirección del servidor MDM (si se le pide). La dirección del servidor MDM cambia de __manage.microsoft.com__ a __enrollment.manage.microsoft.com__. Notifique al usuario que use __enrollment.manage.microsoft.com__ como la dirección del servidor MDM si se le pide durante la inscripción de un dispositivo Windows o Windows Phone. No se requieren cambios para la configuración de CNAME. Para obtener información adicional sobre este cambio, visite [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nueva experiencia del usuario en la aplicación Portal de empresa para Android <!--621622-->
A partir de marzo, la aplicación del portal de empresa para Android seguirá las [directrices de Material Design](https://material.io/guidelines/material-design/introduction.html) para crear una apariencia más moderna. Esta experiencia del usuario mejorada incluye:

* __Colores__: los encabezados de pestaña pueden colorearse según la paleta de colores personalizada.
* __Interfaz__: los botones Aplicaciones destacadas y Todas las aplicaciones se han actualizado en la pestaña Aplicaciones. El botón Buscar ahora es un botón de acción flotante.
* __Navegación__: Todas las aplicaciones muestra una vista con pestañas de Destacadas, Todas y Categorías para navegar más fácilmente.
* __Servicio__: las pestañas Mis dispositivos y Contactar con TI han mejorado la legibilidad.

Puede encontrar imágenes de antes y después en la [página de actualizaciones de la interfaz de usuario](/intune/whats-new-app-ui).

### <a name="associate-multiple-management-tools-with-the-microsoft-store-for-business---926135--"></a>Asociación de varias herramientas de administración con Microsoft Store para Empresas <!--926135-->
Si usa más de una herramienta de administración para implementar las aplicaciones de la Tienda Microsoft para Empresas, anteriormente solo podía asociar una de ellas con la Tienda Microsoft para Empresas. Ahora puede asociar varias herramientas de administración con la tienda, por ejemplo, Intune y Configuration Manager. Para obtener más información, vea [Administrar las aplicaciones adquiridas a través de la Tienda Microsoft para Empresas con Microsoft Intune](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novedades en la versión preliminar pública de la experiencia de administración de Intune en Azure <!--736542-->

A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante API de Graph.

Nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en el portal de Azure de este mes. Durante el estado de versión preliminar, se proporcionarán funcionalidades y paridad con la consola de Intune existente de manera iterativa.

La experiencia de administración de Azure Portal usará la nueva funcionalidad de agrupación y destino ya anunciadas; cuando el inquilino existente se migra a la nueva experiencia de agrupación, también se migra a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si quiere probar o examinar alguna de las nuevas características hasta que se migre su inquilino, regístrese para obtener una nueva cuenta de prueba de Intune o revise la [nueva documentación](/intune/whats-new).

Puede encontrar las novedades en la vista previa de Intune en Azure [aquí](/intune/whats-new).

## <a name="january-2017"></a>Enero de 2017

### <a name="new-capabilities"></a>Nuevas funcionalidades

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Informes en la consola para MAM sin inscripción <!--677961-->
Se han agregado nuevos informes de protección de aplicaciones para los dispositivos inscritos y no inscritos. Obtenga más información sobre cómo puede [supervisar directivas de administración de aplicaciones móviles con Microsoft Intune aquí](/intune-classic/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune).

#### <a name="android-711-support---694397--"></a>Compatibilidad con Android 7.1.1 <!--694397-->
Ahora, Intune admite y administra completamente Android 7.1.1.

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>Resolver el problema en el que los dispositivos iOS están inactivos o la consola de administración no puede comunicarse con ellos <!--unknown-->
Cuando los dispositivos de los usuarios pierden el contacto con Intune, puede proporcionarles nuevos pasos de solución de problemas para ayudarles a volver a obtener acceso a los recursos de la empresa. Vea [Los dispositivos están inactivos o la consola de administración no puede comunicarse con ellos](/intune-classic/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

### <a name="notices"></a>Notificaciones

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Administración predeterminada de los dispositivos de escritorio Windows mediante la configuración de Windows <!--663050-->
El comportamiento predeterminado para inscribir equipos de escritorio de Windows 10 está cambiando. Las nuevas inscripciones seguirán el típico flujo de inscripción del agente MDM en lugar del agente de PC.

El sitio web de portal de empresa proporcionará a los usuarios de escritorio de Windows 10 las instrucciones de inscripción que les guiarán a través del proceso de agregar equipos de escritorio de Windows 10 como dispositivos móviles. Esto no afectará a los PC inscritos en estos momentos, y su organización todavía puede administrar equipos de escritorio de Windows 10 con el agente de PC [si lo prefiere](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Mejora de la asistencia de la administración de aplicaciones móviles para el borrado selectivo <!--581242-->
A los usuarios finales se les proporcionarán instrucciones adicionales sobre cómo recuperar el acceso a los datos profesionales o educativos si estos se quitaron automáticamente debido a la directiva "Intervalo sin conexión antes de que se borren los datos de la aplicación".<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Los vínculos de Portal de empresa para iOS se abren dentro de la aplicación <!--665954-->
Los vínculos dentro de la aplicación de portal de empresa para iOS, incluidos los de documentación y aplicaciones, se abrirán directamente en la aplicación de portal de empresa con una vista desde la aplicación de Safari. Esta actualización se enviará por separado desde la actualización del servicio en enero.

#### <a name="modernizing-the-company-portal-website---753980--"></a>Renovación del sitio web del portal de empresa <!--753980-->
A partir de febrero, el sitio web del portal de empresa admitirá aplicaciones destinadas a aquellos usuarios que no tienen dispositivos administrados. El sitio web se asemejará a otros productos y servicios de Microsoft gracias a una nueva combinación de colores de contraste, ilustraciones dinámicas y un “menú hamburguesa”, ![Menú de hamburguesa del sitio web de Portal de empresa](/intune/whats-new-app-ui).

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>Nueva documentación para las directivas de protección de aplicaciones <!--583398-->
Hemos actualizado nuestra documentación para administradores y desarrolladores de aplicaciones que quieran habilitar directivas de protección de aplicaciones (conocidas como directivas de MAM) en sus aplicaciones iOS y Android con la herramienta de ajuste de aplicaciones de Intune o con el SDK para aplicaciones de Intune.

Se han actualizado los siguientes artículos:

* [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](/intune/apps-prepare-mobile-application-management)
* [Preparar aplicaciones iOS para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune](/intune/app-wrapper-prepare-ios)
* [Introducción al SDK para aplicaciones de Microsoft Intune](/intune/app-sdk-get-started)
* [Guía para desarrolladores sobre el SDK de aplicaciones de Intune para iOS](/intune/app-sdk-ios)

Se han agregado los siguientes artículos nuevos a la biblioteca de documentos:

* [Complemento Cordova del SDK para aplicaciones de Intune](/intune/app-sdk-cordova)
* [Componente Xamarin del SDK para aplicaciones de Intune](/intune/app-sdk-xamarin)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Barra de progreso cuando se inicia el portal de empresa en iOS <!--665978-->
El portal de empresa para iOS presenta una barra de progreso en la pantalla de inicio para proporcionar información al usuario sobre los procesos de carga que se producen. Habrá una implementación por fases de la barra de progreso para reemplazar el control de número. Esto significa que algunos usuarios verán la nueva barra de progreso y otros seguirán viendo el control de número.

## <a name="december-2016"></a>Diciembre de 2016

### <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Versión preliminar pública de la nueva experiencia de administración de Intune en Azure <!--736542-->
A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API de Graph. Antes de la disponibilidad general de este portal para todos los inquilinos de Intune, nos complace anunciar que comenzaremos a implementar una versión preliminar de esta nueva experiencia de administración dentro de este mes para seleccionar inquilinos.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, encuentre más información sobre lo que tenemos en Azure Portal para Microsoft Azure en nuestra [documentación nueva](/intune/what-is-intune).

__Integración de la administración de gastos de telecomunicaciones en la versión preliminar pública de Azure Portal__ <!--747605-->
Ahora estamos comenzando a realizar la integración de la versión preliminar con los servicios de administración de gastos de telecomunicaciones (TEM) dentro del portal de Azure. Puede usar Intune para exigir límites sobre el uso de datos nacionales y móviles. Comenzaremos estas integraciones con [Saaswedo](http://www.saaswedo.com/). Para habilitar esta característica en su inquilino de prueba, [póngase en contacto con el soporte técnico de Microsoft](/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune).

### <a name="new-capabilities"></a>Nuevas funcionalidades

__Autenticación multifactor en todas las plataformas__ <!--747590-->
Ahora puede exigir la autenticación multifactor (MFA) en un grupo de usuarios seleccionado cuando inscriben un dispositivo iOS, Android, Windows 8.1 + o Windows Phone 8.1 + desde el Portal de administración de Azure mediante la configuración de MFA en la aplicación de inscripción de Microsoft Intune en Azure Active Directory.

__Capacidad para restringir la inscripción de dispositivos móviles__ <!--747596-->
Intune está agregando nuevas restricciones de inscripción que controlan qué plataformas de dispositivos móviles pueden inscribir. Intune separa las plataformas de dispositivos móviles como iOS, Mac OS, Android, Windows y Windows Mobile.
* La restricción la inscripción de dispositivos móviles no restringe la inscripción del cliente de PC.
* Solo para iOS, hay una opción adicional para bloquear la inscripción de dispositivos de propiedad personal.

Intune marca todos los dispositivos nuevos como personal a menos que el administrador de TI tome la medida de marcarlos como propiedad de la empresa, como se explica en [este artículo](/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="notices"></a>Notificaciones

__Multi-Factor Authentication para la inscripción se mueve a Azure Portal__ <!--VSO 750545-->
Anteriormente, los administradores iban a la consola de Intune o a la consola de Configuration Manager (antes de la versión de octubre de 2016) para establecer MFA para las inscripciones de Intune. Con esta característica actualizada, ahora iniciará sesión en [Microsoft Azure Portal](https://manage.windowsazure.com) con sus credenciales de Intune y configurará MFA mediante Azure AD. Aprenda más al respecto [aquí](https://aka.ms/mfa_ad).

__La aplicación del Portal de empresa para Android ahora disponible en China__ <!--VSO 658093-->
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

### <a name="deprecations"></a>Elementos obsoletos

__Firefox ya no admitirá Silverlight__ <!--VSO TBA-->
Mozilla quitará la compatibilidad con Silverlight en la versión 52 del [explorador Firefox](https://www.mozilla.org/firefox), a partir de marzo de 2017. Como resultado de lo anterior, ya no podrá iniciar sesión en la consola de Intune existente con las versiones de Firefox superiores a la versión 51. Se recomienda usar Internet Explorer 10 u 11 para obtener acceso a la consola de administración, o bien una [versión de Firefox anterior a la versión 52](https://ftp.mozilla.org/pub/firefox/releases/). La transición de Intune a Azure Portal le permitirá admitir varios [exploradores modernos](/azure/azure-preview-portal-supported-browsers-devices) sin depender de Silverlight.

__Eliminación de directivas de bandeja de entrada móvil de Exchange Online__ <!--770687-->
A partir de diciembre, los administradores ya no podrán ver ni configurar directivas de buzón móvil de Exchange Online (EAS) en la consola de Intune. Este cambio se implementará en todos los inquilinos de Intune durante diciembre y enero. Todas las directivas existentes permanecerán como están configuradas; para configurar nuevas directivas, use el Shell de administración de Exchange. Puede encontrar más información [aquí](https://technet.microsoft.com/library/bb123783%28v=exchg.150%29.aspx).

__Ya no se admiten las aplicaciones AV Player, Image Viewer y PDF Viewer de Intune en Android__ <!--747553-->
Desde mediados de diciembre de 2016 en adelante, los usuarios ya no podrán utilizar las aplicaciones AV Player, Image Viewer, y PDF Viewer de Intune. Estas aplicaciones se han reemplazado por la aplicación Azure Information Protection. Descubra más sobre la aplicación Azure Information Protection [aquí](/information-protection/rms-client/mobile-app-faq).

## <a name="november-2016"></a>Noviembre de 2016

### <a name="new-capabilities"></a>Nuevas funcionalidades

__Nuevo portal de empresa de Microsoft Intune disponible para los dispositivos Windows 10__ Microsoft ha lanzado una nueva aplicación de portal de empresa de [Microsoft Intune para los dispositivos Windows 10](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Esta aplicación, que aprovecha el nuevo formato de Windows 10 Universal, proporcionará al usuario una experiencia de usuario actualizada dentro de la aplicación y experiencias idénticas en todos los dispositivos Windows 10, PC y móvil, mientras sigue permitiendo las mismas funcionalidades que usa hoy en día.

La nueva aplicación también permitirá a los usuarios aprovechar características de plataforma adicional como el inicio de sesión único (SSO) y la autenticación basada en certificados en dispositivos Windows 10. La aplicación estará disponible como una actualización del Portal de empresa de Windows 8.1 existente. El Portal de empresa de Windows Phone 8.1 se instala desde la Microsoft Store. Para más información, vaya a [aka.ms/intunecp_universalapp](https://aka.ms/intunecp_universalapp).

> [!IMPORTANT]
> __Actualización de Intune y Android for Work__ Aunque se pueden implementar aplicaciones de Android for Work con una acción __Requerido__, solo puede implementar aplicaciones como __Disponible__ si los grupos de Intune se han migrado a la nueva experiencia de grupos de Azure AD.

__El complemento Cordova del SDK para aplicaciones de Intune ahora admite MAM sin inscripción__Los desarrolladores de aplicaciones ahora pueden usar el complemento Cordova del SDK para aplicaciones de Intune para habilitar la funcionalidad MAM sin inscribir el dispositivo en sus aplicaciones de Cordova para Android e iOS. El complemento Cordova del SDK para aplicaciones de Intune se puede encontrar [aquí](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

__El componente Xamarin del SDK para aplicaciones de Intune ahora admite MAM sin suscripción__ Los desarrolladores de aplicaciones ahora pueden usar el componente Xamarin del SDK para aplicaciones de Intune para habilitar la funcionalidad MAM sin inscripción de dispositivos en sus aplicaciones basadas en Xamarin para Android e iOS. El componente Xamarin del SDK para aplicaciones de Intune se puede encontrar [aquí](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

### <a name="notices"></a>Notificaciones

__El certificado de firma de Symantec ya no requiere el portal de empresa firmado de Windows Phone 8 para la carga__ La carga del certificado de firma de Symantec ya no requiere una aplicación firmada del portal de empresa de Windows Phone 8. El certificado se puede cargar de forma independiente.

### <a name="deprecations"></a>Elementos obsoletos

__Compatibilidad con el portal de empresa de Windows Phone 8__ La compatibilidad con el portal de empresa de Windows Phone 8 ahora está en desuso. La compatibilidad con las plataformas Windows Phone 8 y WinRT ha quedado en desuso en octubre de 2016. La compatibilidad con el portal de empresa de Windows 8 ha quedado en desuso en octubre de 2016.
