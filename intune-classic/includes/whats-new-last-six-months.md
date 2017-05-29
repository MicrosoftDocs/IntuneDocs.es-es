## <a name="march-2017"></a>Marzo de 2017

### <a name="new-capabilities"></a>Nuevas funcionalidades

#### <a name="support-for-skycure"></a>Compatibilidad con Skycure

Ahora puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Skycure, una solución de defensa contra amenazas móviles integrada con Microsoft Intune. El riesgo se evalúa según la telemetría recopilada de dispositivos que ejecutan Skycure, que incluye:

- Defensa física
- Defensa de red
- Defensa de aplicaciones
- Defensa de vulnerabilidades

Puede configurar directivas de acceso condicional de EMS basadas en la evaluación de riesgos de Skycure habilitada mediante las directivas de cumplimiento de dispositivos de Intune. Puede usar estas directivas para permitir o bloquear el acceso de dispositivos no compatibles a recursos corporativos en función de las amenazas detectadas. Para obtener más información, vea [Conector de Mobile Threat Defense de Skycure](/intune-classic/deploy-use/skycure-mobile-threat-defense-connector).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nueva experiencia del usuario en la aplicación del portal de empresa para Android <!--621622-->

La aplicación de Portal de empresa para Android va a actualizar su interfaz de usuario para un aspecto más moderno y una mejor experiencia de usuario. Las actualizaciones importantes son:

- Colores: los encabezados de la pestaña de Portal de empresa están coloreados según la información de la marca definida por TI.
- Aplicaciones: en la pestaña **Aplicaciones**, los botones **Aplicaciones destacadas** y **Todas las aplicaciones** se han actualizado.
- Buscar: en la pestaña **Aplicaciones**, el botón **Buscar** ahora es un botón de acción flotante.
- Aplicaciones de navegación: la vista **Todas las aplicaciones** muestra una vista con las pestañas **Destacadas**, **Todas** y **Categorías** para navegar más fácilmente.
- Soporte: las pestañas **Mis dispositivos** y **Contactar con TI** se actualizan para mejorar la legibilidad.

Para obtener más información sobre estos cambios, consulte [Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune](/intune-classic/whats-new/whats-new-in-intune-app-ui).

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Los dispositivos no administrados puedan acceder a aplicaciones asignadas <!--664691-->

Como parte de los cambios de diseño en el sitio web del portal de empresa, los usuarios de iOS y Android podrán instalar aplicaciones asignadas a ellos como "disponibles sin inscripción" en sus dispositivos no administrados. Con sus credenciales de Intune, los usuarios podrán iniciar sesión en el sitio web del portal de empresa y ver la lista de aplicaciones asignadas. Los paquetes de aplicación de las aplicaciones "disponibles sin inscripción" se encuentran disponibles para descargar a través del sitio web del portal de empresa. Las aplicaciones que requieren la inscripción para la instalación no se ven afectadas por este cambio, ya que se les pedirá a los usuarios que inscriban su dispositivo si quieren instalar esas aplicaciones.

#### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Script de firma para el Portal de empresa para Windows 10<!--941642-->

Si necesita descargar y transferir localmente la aplicación del Portal de empresa para Windows 10, ahora puede usar un script para simplificar y agilizar el proceso de firma de aplicaciones en su organización.   Para descargar el script y las instrucciones de uso, consulte el artículo [Microsoft Intune Signing Script for Windows 10 Company Portal](https://aka.ms/win10cpscript) (Script de firma de Microsoft Intune para el Portal de empresa para Windows 10) de la Galería de TechNet. Para obtener más información sobre este anuncio, consulte [Updating your Windows 10 Company Portal app](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) (Actualización de la aplicación del Portal de empresa para Windows 10) en el blog del equipo de asistencia técnica de Intune.


### <a name="notices"></a>Notificaciones

#### <a name="support-for-ios-103"></a>Compatibilidad con iOS 10.3

La versión de iOS 10.3 empezó a implementarse el 27 de marzo de 2017 a los usuarios de iOS. Todos los escenarios MDM y MAM existentes de Intune son compatibles con la versión más reciente del sistema operativo de Apple. Se prevé que todas las características existentes de Intune actualmente disponibles para administrar dispositivos iOS seguirán funcionando cuando los usuarios actualicen sus dispositivos a iOS 10.3.

Actualmente no hay ningún problema conocido que compartir. Si tiene algún problema con iOS 10.3, póngase en contacto con el [equipo de soporte técnico de Intune](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune).

#### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Compatibilidad mejorada para usuarios de Android radicados en China<!--720444-->

Debido a la ausencia de Google Play Store en China, los dispositivos Android deben obtener aplicaciones en los mercados chinos. El Portal de empresa admitirá este flujo de trabajo al redirigir a los usuarios de Android de China para que descarguen las aplicaciones de Portal de empresa y de Outlook desde tiendas de aplicaciones locales. Esto mejorará la experiencia del usuario cuando se habiliten las directivas de acceso condicional, tanto para administración de dispositivos móviles como para la administración de aplicaciones móviles. Las aplicaciones de Portal de empresa y Outlook para Android están disponibles en los siguientes tiendas de aplicaciones chinas:

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

#### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>Procedimiento recomendado: asegúrese de que las aplicaciones del Portal de empresa están actualizadas.<!--879465-->

En diciembre de 2016, se publicó una actualización que permitía aplicar la autenticación multifactor (MFA) en un grupo de usuarios cuando registraban un dispositivo iOS, Android, Windows 8.1 + o Windows Phone 8.1 +. Esta característica no puede funcionar sin determinadas versiones de línea de base de la aplicación del Portal de empresa para iOS (2.1.17 y posteriores) y Android (5.0.3419.0 y posteriores).

Microsoft mejora continuamente Intune agregando nuevas funciones en la consola y las aplicaciones del Portal de empresa en todas las plataformas compatibles. Como resultado, solo lanza correcciones para problemas detectados en la versión actual de la aplicación del Portal de empresa. Por lo tanto, se recomienda utilizar las versiones más recientes de las aplicaciones del Portal de empresa para mejorar la experiencia de usuario.

>[!Tip]
> Pida a los usuarios que configuren sus dispositivos para actualizar automáticamente las aplicaciones de la tienda de aplicaciones correspondiente. Si ha publicado la aplicación del Portal de empresa para Android en un recurso compartido de red, puede descargar la versión más reciente desde el [Centro de descarga de Microsoft](https://www.microsoft.com/download/details.aspx?id=49140).

#### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>Microsoft Teams ahora está habilitado para MAM en iOS y Android

Microsoft ha anunciado la disponibilidad general de Microsoft Teams. Las aplicaciones de Microsoft Teams actualizadas para iOS y Android están habilitadas con las funcionalidades de administración de aplicaciones móviles (MAM) de Intune, por lo que sus equipos podrán trabajar con libertad en todos los dispositivos. De esta forma, se asegurará de que las conversaciones y datos corporativos estén protegidos en todo momento. Para obtener más información, consulte el [anuncio de Microsoft Teams](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) en el blog de seguridad y la movilidad empresarial.


## <a name="february-2017"></a>Febrero de 2017

### <a name="new-capabilities"></a>Nuevas funcionalidades

### <a name="modernizing-the-company-portal-website---753980--"></a>Renovación del sitio web del portal de empresa<!--753980-->
El sitio web del portal de empresa admitirá aplicaciones destinadas a aquellos usuarios que no tienen dispositivos administrados. El sitio web se asemejará a otros productos y servicios de Microsoft gracias a una nueva combinación de colores de contraste, ilustraciones dinámicas y un “menú hamburguesa”, ![Pequeña imagen del menú hamburguesa que se ha agregado en la esquina superior izquierda del sitio web del portal de empresa](/intune-classic/whats-new/whats-new-in-intune-app-ui).

### <a name="notices"></a>Notificaciones

#### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>La migración de grupo no requiere actualizaciones a grupos ni directivas para dispositivos iOS <!--898837-->
Para cada grupo de dispositivos de Intune previamente asignado mediante un perfil de inscripción de dispositivos corporativos, se creará un grupo de dispositivos dinámico correspondiente en AAD según el nombre del perfil de inscripción de dispositivos corporativos, durante la migración a grupos de dispositivos de Azure Active Directory. Esto garantizará que, según se inscriban dispositivos, estos se agrupen de manera automática y reciban las mismas directivas y aplicaciones que el grupo de Intune original.

Una vez que un inquilino empieza el proceso de migración para agrupar y seleccionar el destino, Intune creará de forma automática un grupo dinámico de AAD para que se corresponda con un grupo de Intune destinado mediante un perfil de inscripción de dispositivos corporativos. Si el administrador de Intune elimina el grupo de destino de Intune, no se eliminará el grupo de AAD dinámico correspondiente. Se borrarán los miembros del grupo y la consulta dinámica, pero el propio grupo permanecerá hasta que el administrador de TI lo quite a través del portal de AAD.

De forma similar, si el administrador de TI cambia qué grupo de Intune es el destino de un perfil de inscripción de dispositivos corporativos, Intune crea un nuevo grupo dinámico que refleje la nueva asignación de perfil, pero no quitará el grupo dinámico creado para la asignación anterior.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Restablecer la administración de dispositivos de escritorio Windows predeterminada mediante la configuración de Windows <!--663050-->
El comportamiento predeterminado para inscribir equipos de escritorio de Windows 10 está cambiando. Las nuevas inscripciones seguirán el típico flujo de inscripción del agente MDM en lugar del agente de PC. El sitio web de portal de empresa proporcionará a los usuarios de escritorio de Windows 10 las instrucciones de inscripción que les guiarán a través del proceso de agregar equipos de escritorio de Windows 10 como dispositivos móviles. Esto no afectará a los PC inscritos en estos momentos, y su organización todavía puede administrar equipos de escritorio de Windows 10 con el agente de PC [si lo prefiere](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Mejorar la asistencia de la administración de aplicaciones móviles para el borrado selectivo <!--581242-->
A los usuarios finales se les proporcionarán instrucciones adicionales sobre cómo recuperar el acceso a los datos profesionales o educativos si estos se quitaron automáticamente debido a la directiva "Intervalo sin conexión antes de que se borren los datos de la aplicación".<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Los vínculos de portal de empresa para iOS se abren dentro de la aplicación <!--665954-->
Los vínculos dentro de la aplicación de portal de empresa para iOS, incluidos los de documentación y aplicaciones, se abrirán directamente en la aplicación de portal de empresa con una vista desde la aplicación de Safari. Esta actualización se enviará por separado desde la actualización del servicio en enero.

#### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Nueva dirección del servidor MDM para dispositivos Windows <!--893007-->
Se producirá un error en la inscripción del dispositivo si los usuarios de Windows y Windows Phone especifican __manage.microsoft.com__ como la dirección del servidor MDM (si se le pide). La dirección del servidor MDM cambia de __manage.microsoft.com__ a __enrollment.manage.microsoft.com__. Notifique al usuario que use __enrollment.manage.microsoft.com__ como la dirección del servidor MDM si se le pide durante la inscripción de un dispositivo Windows o Windows Phone. No se requieren cambios para la configuración de CNAME. Para obtener información adicional sobre este cambio, visite [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nueva experiencia del usuario en la aplicación del portal de empresa para Android <!--621622-->
A partir de marzo, la aplicación del portal de empresa para Android seguirá las [directrices de Material Design](https://material.io/guidelines/material-design/introduction.html) para crear una apariencia más moderna. Esta experiencia del usuario mejorada incluye:

* __Colores__: los encabezados de pestaña pueden colorearse según la paleta de colores personalizada.
* __Interfaz__: los botones Aplicaciones destacadas y Todas las aplicaciones se han actualizado en la pestaña Aplicaciones. El botón Buscar ahora es un botón de acción flotante.
* __Navegación__: Todas las aplicaciones muestra una vista con pestañas de Destacadas, Todas y Categorías para navegar más fácilmente.
* __Servicio__: las pestañas Mis dispositivos y Contactar con TI han mejorado la legibilidad.

Puede encontrar imágenes de antes y después en la [página de actualizaciones de la interfaz de usuario](/intune-classic/whats-new/whats-new-in-intune-app-ui).

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>Asociación de varias herramientas de administración con la Tienda Windows para empresas<!--926135-->
Si usa más de una herramienta de administración para implementar las aplicaciones de la Tienda Windows para empresas, anteriormente solo podía asociar una de ellas con la Tienda Windows para empresas. Ahora puede asociar varias herramientas de administración con la tienda, por ejemplo, Intune y Configuration Manager. Para más información, consulte [Administrar las aplicaciones adquiridas a través de la Tienda Windows para empresas con Microsoft Intune](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novedades en la versión preliminar pública de la experiencia de administración en Azure <!--736542-->

A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API Graph.

Nuevos inquilinos de prueba comenzarán a ver la versión preliminar pública de la nueva experiencia de administración en el portal de Azure de este mes. Durante el estado de versión preliminar, se proporcionarán funcionalidades y paridad con la consola de Intune existente de manera iterativa.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, si quiere probar o examinar alguna de las nuevas características hasta que se migre su inquilino, regístrese para obtener una nueva cuenta de prueba de Intune o revise la [nueva documentación](/intune/whats-new).

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

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Restablecer la administración de dispositivos de escritorio Windows predeterminada mediante la configuración de Windows <!--663050-->
El comportamiento predeterminado para inscribir equipos de escritorio de Windows 10 está cambiando. Las nuevas inscripciones seguirán el típico flujo de inscripción del agente MDM en lugar del agente de PC.

El sitio web de portal de empresa proporcionará a los usuarios de escritorio de Windows 10 las instrucciones de inscripción que les guiarán a través del proceso de agregar equipos de escritorio de Windows 10 como dispositivos móviles. Esto no afectará a los PC inscritos en estos momentos, y su organización todavía puede administrar equipos de escritorio de Windows 10 con el agente de PC [si lo prefiere](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Mejorar la asistencia de la administración de aplicaciones móviles para el borrado selectivo <!--581242-->
A los usuarios finales se les proporcionarán instrucciones adicionales sobre cómo recuperar el acceso a los datos profesionales o educativos si estos se quitaron automáticamente debido a la directiva "Intervalo sin conexión antes de que se borren los datos de la aplicación".<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Los vínculos de portal de empresa para iOS se abren dentro de la aplicación <!--665954-->
Los vínculos dentro de la aplicación de portal de empresa para iOS, incluidos los de documentación y aplicaciones, se abrirán directamente en la aplicación de portal de empresa con una vista desde la aplicación de Safari. Esta actualización se enviará por separado desde la actualización del servicio en enero.

#### <a name="modernizing-the-company-portal-website---753980--"></a>Renovación del sitio web del portal de empresa<!--753980-->
A partir de febrero, el sitio web del portal de empresa admitirá aplicaciones destinadas a aquellos usuarios que no tienen dispositivos administrados. El sitio web se asemejará a otros productos y servicios de Microsoft gracias a una nueva combinación de colores de contraste, ilustraciones dinámicas y un “menú hamburguesa”, ![Menú de hamburguesa del sitio web de Portal de empresa](/intune-classic/whats-new/whats-new-in-intune-app-ui).

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>Nueva documentación para las directivas de protección de aplicaciones <!--583398-->
Hemos actualizado nuestra documentación para administradores y desarrolladores de aplicaciones que quieran habilitar directivas de protección de aplicaciones (conocidas como directivas de MAM) en sus aplicaciones iOS y Android con la herramienta de ajuste de aplicaciones de Intune o con el SDK para aplicaciones de Intune.

Se han actualizado los siguientes artículos:

* [Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune](/intune-classic/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Preparar aplicaciones iOS para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune](/intune-classic/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Introducción al SDK para aplicaciones de Microsoft Intune](/intune-classic/develop/intune-app-sdk-get-started)
* [Guía para desarrolladores sobre el SDK de aplicaciones de Intune para iOS](/intune-classic/develop/intune-app-sdk-ios)

Se han agregado los siguientes artículos nuevos a la biblioteca de documentos:

* [Complemento Cordova del SDK para aplicaciones de Intune](/intune-classic/develop/intune-app-sdk-cordova)
* [Componente Xamarin del SDK para aplicaciones de Intune](/intune-classic/develop/intune-app-sdk-xamarin)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Barra de progreso cuando se inicia el portal de empresa en iOS <!--665978-->
El portal de empresa para iOS presenta una barra de progreso en la pantalla de inicio para proporcionar información al usuario sobre los procesos de carga que se producen. Habrá una implementación por fases de la barra de progreso para reemplazar el control de número. Esto significa que algunos usuarios verán la nueva barra de progreso y otros seguirán viendo el control de número.

## <a name="december-2016"></a>Diciembre de 2016

### <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Versión preliminar pública de la nueva experiencia de administración de Intune en Azure <!--736542-->
A principios de 2017 migraremos nuestra experiencia de administración completa a Azure, lo que permitirá una administración eficaz e integrada de los flujos de trabajo principales de EMS en una moderna plataforma de servicios que es extensible mediante las API Graph. Antes de la disponibilidad general de este portal para todos los inquilinos de Intune, nos complace anunciar que comenzaremos a implementar una versión preliminar de esta nueva experiencia de administración dentro de este mes para seleccionar inquilinos.

La experiencia de administración del portal de Azure usará la nueva funcionalidad de agrupación y selección de destino ya anunciada; cuando se migre su inquilino existente a la nueva experiencia de agrupación también se migrará a la versión preliminar la nueva experiencia de administración en el inquilino. Mientras tanto, encuentre más información sobre lo que tenemos en Azure Portal para Microsoft Azure en nuestra [documentación nueva](/intune/what-is-intune).

__Integración de la administración de gastos de Telecom en la versión preliminar pública de Azure Portal__ <!--747605--> Se ha empezado a integrar la administración de gastos de Telecom, un tercero, en la versión preliminar.

### <a name="new-capabilities"></a>Nuevas funcionalidades

__Multi-factor Authentication en todas las plataformas__ <!--747590--> Ahora puede exigir la autenticación multifactor (MFA) en un grupo de usuarios seleccionado cuando inscriben un dispositivo iOS, Android, Windows 8.1 + o Windows Phone 8.1 + desde el Portal de administración de Azure mediante la configuración de MFA en la aplicación de inscripción de Microsoft Intune en Azure Active Directory.

__Capacidad de restringir la inscripción de dispositivos móviles__ <!--747596--> Intune está agregando nuevas restricciones de inscripción que controlan qué plataformas de dispositivos móviles pueden inscribir. Intune separa las plataformas de dispositivos móviles como iOS, Mac OS, Android, Windows y Windows Mobile.
* La restricción la inscripción de dispositivos móviles no restringe la inscripción del cliente de PC.
* Solo para iOS, hay una opción adicional para bloquear la inscripción de dispositivos de propiedad personal.

Intune marca todos los dispositivos nuevos como personal a menos que el administrador de TI tome la medida de marcarlos como propiedad de la empresa, como se explica en [este artículo](/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="notices"></a>Notificaciones

__Multi-Factor Authentication en inscripción hacia Azure Portal__ <!--VSO 750545-->Anteriormente, los administradores iban a la consola de Intune o a la consola de Configuration Manager (antes de la versión de octubre de 2016) para establecer MFA para las inscripciones de Intune. Con esta característica actualizada, ahora iniciará sesión en el [portal de Microsoft Azure](https://manage.windowsazure.com) con sus credenciales de Intune y configurará MFA mediante Azure AD. Aprenda más al respecto [aquí](https://aka.ms/mfa_ad).

__Aplicación de Portal de empresa para Android ahora disponible en China__  <!--VSO 658093--> Publicaremos la aplicación del Portal de empresa para Android para su descarga en China. Debido a la ausencia de Google Play Store en China, los dispositivos Android deben obtener aplicaciones en los mercados de aplicaciones chinos. La aplicación Portal de empresa para Android estará disponible para su descarga en las siguientes tiendas:
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

__Firefox dejará de ser compatible con Silverlight__ <!--VSO TBA-->Mozilla quitará la compatibilidad con Silverlight en la versión 52 del [explorador Firefox](https://www.mozilla.org/firefox), a partir de marzo de 2017. Como resultado de lo anterior, ya no podrá iniciar sesión en la consola de Intune existente con las versiones de Firefox superiores a la versión 51. Se recomienda usar Internet Explorer 10 u 11 para obtener acceso a la consola de administración, o bien una [versión de Firefox anterior a la versión 52](https://ftp.mozilla.org/pub/firefox/releases/). La transición de Intune a Azure Portal le permitirá admitir varios [exploradores modernos](/azure/azure-preview-portal-supported-browsers-devices) sin depender de Silverlight.

__Eliminación de directivas de buzón móvil de Exchange Online__ <!--770687-->A partir de diciembre, los administradores ya no podrán ver ni configurar directivas de buzón móvil de Exchange Online (EAS) en la consola de Intune. Este cambio se implementará en todos los inquilinos de Intune durante diciembre y enero. Todas las directivas existentes permanecerán como están configuradas; para configurar nuevas directivas, use el Shell de administración de Exchange. Puede encontrar más información [aquí](https://technet.microsoft.com/library/bb123783%28v=exchg.150%29.aspx).

__Las aplicaciones AV Player, Image Viewer y PDF Viewer de Intune ya no son compatibles con Android__ <!--747553--> Desde mediados de diciembre de 2016 en adelante, los usuarios ya no podrán utilizar las aplicaciones AV Player, Image Viewer, y PDF Viewer de Intune. Estas aplicaciones se han reemplazado por la aplicación Azure Information Protection. Descubra más sobre la aplicación Azure Information Protection [aquí](/information-protection/rms-client/mobile-app-faq).

## <a name="november-2016"></a>Noviembre de 2016

### <a name="new-capabilities"></a>Nuevas funcionalidades

__Nuevo portal de empresa de Microsoft Intune disponible para los dispositivos Windows 10__ Microsoft ha lanzado una nueva aplicación de portal de empresa de [Microsoft Intune para los dispositivos Windows 10](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Esta aplicación, que aprovecha el nuevo formato de Windows 10 Universal, proporcionará al usuario una experiencia de usuario actualizada dentro de la aplicación y experiencias idénticas en todos los dispositivos Windows 10, PC y móvil, mientras sigue permitiendo las mismas funcionalidades que usa hoy en día.

La nueva aplicación también permitirá a los usuarios aprovechar características de plataforma adicional como el inicio de sesión único (SSO) y la autenticación basada en certificados en dispositivos Windows 10. La aplicación estará disponible como una actualización del portal de empresa de Windows 8.1 existente y este se instala desde la Tienda Windows. Para más información, vaya a [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).

> [!IMPORTANT]
> __Actualización de Intune y Android for Work__ Aunque se pueden implementar aplicaciones de Android for Work con una acción __Requerido__, solo puede implementar aplicaciones como __Disponible__ si los grupos de Intune se han migrado a la nueva experiencia de grupos de Azure AD.

__El complemento Cordova del SDK para aplicaciones de Intune ahora admite MAM sin inscripción__Los desarrolladores de aplicaciones ahora pueden usar el complemento Cordova del SDK para aplicaciones de Intune para habilitar la funcionalidad MAM sin inscribir el dispositivo en sus aplicaciones de Cordova para Android e iOS. El complemento Cordova del SDK para aplicaciones de Intune se puede encontrar [aquí](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

__El componente Xamarin del SDK para aplicaciones de Intune ahora admite MAM sin suscripción__ Los desarrolladores de aplicaciones ahora pueden usar el componente Xamarin del SDK para aplicaciones de Intune para habilitar la funcionalidad MAM sin inscripción de dispositivos en sus aplicaciones basadas en Xamarin para Android e iOS. El componente Xamarin del SDK para aplicaciones de Intune se puede encontrar [aquí](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

### <a name="notices"></a>Notificaciones

__El certificado de firma de Symantec ya no requiere el portal de empresa firmado de Windows Phone 8 para la carga__ La carga del certificado de firma de Symantec ya no requiere una aplicación firmada del portal de empresa de Windows Phone 8. El certificado se puede cargar de forma independiente.

###<a name="deprecations"></a>Elementos obsoletos

__Compatibilidad con el portal de empresa de Windows Phone 8__ La compatibilidad con el portal de empresa de Windows Phone 8 ahora está en desuso. La compatibilidad con las plataformas Windows Phone 8 y WinRT ha quedado en desuso en octubre de 2016. La compatibilidad con el portal de empresa de Windows 8 ha quedado en desuso en octubre de 2016.

## <a name="october-2016"></a>Octubre de 2016

### <a name="conditional-access-for-mobile-application-management"></a>Acceso condicional para la administración de aplicaciones móviles
Podrá restringir el acceso a Exchange Online de forma que el acceso solo proceda de aplicaciones que admitan las directivas de administración de aplicaciones móviles de Intune, como Outlook. [Esta nueva característica](/intune-classic/deploy-use/allow-policy-managed-apps-access-to-o365) se adapta perfectamente a las directivas de administración de aplicaciones móviles (MAM) de Intune, ya que puede bloquear el acceso a los clientes de correo integrado u otras aplicaciones que no se hayan configurado con las directivas de MAM de Intune. Esto garantiza que los usuarios están teniendo acceso a los datos de su organización con aplicaciones que pueden estar protegidas mediante MAM de Intune. Puede comenzar a trabajar en la administración de aplicaciones móviles de Intune mediante Azure Portal. Busque la nueva sección de acceso condicional en la hoja "Configuración".

### <a name="conditional-access-for-windows-pcs"></a>Acceso condicional para equipos Windows
Ahora puede crear directivas de acceso condicional a través de la consola de administración de Intune para impedir que los equipos que ejecuten Windows tengan acceso a [Exchange Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune). También puede crear directivas de acceso condicional para bloquear el acceso a aplicaciones de escritorio y universales de Office.

### <a name="android-for-work-support"></a>Compatibilidad de Android for Work

> [!IMPORTANT]

> Aunque se pueden implementar aplicaciones Android for Work con una acción __Requerido__, solo se pueden implementar aplicaciones como __Disponible__ si los grupos de Intune se han migrado a la nueva experiencia de grupos de Azure AD.

Intune ahora forma parte del programa de Android for Work (AfW). Comenzaremos este mes por implementar la compatibilidad con las características de AfW y continuaremos en los próximos meses. Tenga en cuenta que la implementación de aplicaciones disponibles de AfW aprovecha la nueva experiencia de agrupación y selección de destino. Las cuentas de servicio de Intune aprovisionadas recientemente podrán usar esta característica cuando AfW esté disponible para ellas.

[Lea el anuncio de Microsoft sobre la compatibilidad de Intune con Android for Work](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

Los temas de Intune siguientes son nuevos o actualizados con la información de Android for Work:

Para profesionales de TI:
- [Configurar Android for Work](/intune-classic/deploy-use/set-up-android-for-work)
- [Restringir el acceso de correo electrónico a Exchange Online y nuevo Exchange Online dedicado](/intune-classic/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Restringir el acceso de correo electrónico a Exchange local y Exchange Online dedicado heredado con Intune](/intune-classic/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Configuración de directivas de cumplimiento para dispositivos Android for Work](/intune-classic/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [Implementación de aplicaciones Android for Work](/intune-classic/deploy-use/android-for-work-apps)
- [Configuración de aplicaciones Android for Work con directivas de configuración de aplicaciones móviles](/intune-classic/deploy-use/afw-app-configuration-policy)
- [Opciones de directivas de Android for Work](/intune-classic/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

Para usuarios finales:
- [¿Qué ocurre cuando se crea un perfil de trabajo?](/intune-user-help/what-happens-when-you-create-a-work-profile-android)
- [Creación de un perfil de trabajo e inscripción del dispositivo en Intune](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android)

### <a name="lookout-integration-to-protect-ios-devices"></a>Integración de Lookout para proteger los dispositivos iOS
En octubre, Microsoft se está integrando en la solución de protección de amenazas móviles de Lookout para proteger los dispositivos móviles iOS mediante la detección de malware y aplicaciones de riesgo, entre otros, en los dispositivos. La solución de Lookout le ayuda a determinar el nivel de amenaza, que es configurable. Puede crear una regla de directivas de cumplimiento en Intune para terminar el cumplimiento de dispositivo basándose en la evaluación de riesgos mediante Lookout. Con las directivas de acceso condicional, puede permitir o bloquear el acceso a los recursos empresariales basándose en el estado de cumplimiento del dispositivo.

A los usuarios finales de los dispositivos iOS no compatibles se les solicitará que se inscriban; necesitarán instalar la aplicación Lookout for Work en sus dispositivos, activar la aplicación y corregir las amenazas que se mencionan en la aplicación Lookout for Work para obtener acceso a los datos de la empresa. Obtenga información sobre cómo [Configurar e implementar aplicaciones Lookout for Work](/intune-classic/deploy-use/configure-and-deploy-lookout-for-work-apps).
<!--TFS 1319493-->

### <a name="intune-app-wrapping-tool-for-android"></a>Herramienta de ajuste de aplicaciones Intune para Android
Puede habilitar las aplicaciones para que usen directivas de administración de aplicaciones móviles (MAM) de Intune mediante la herramienta de ajuste de aplicaciones de Intune. La compatibilidad con directivas MAM de Intune sin requerir la inscripción de dispositivos ya está disponible.

### <a name="manage-printing-from-apps-managed-using-mam-policies"></a>Administrar la impresión desde aplicaciones administradas mediante directivas MAM
Ahora puede evitar la impresión de datos empresariales desde aplicaciones que tengan directivas MAM. Esta opción está disponible en los dispositivos de [Azure Portal](/intune-classic/deploy-use/android-mam-policy-settings).
<!--TFS 1014328-->

### <a name="support-for-fingerprints-on-android-devices"></a>Compatibilidad con huellas digitales en dispositivos Android
Administración de aplicaciones móviles Android

### <a name="notices"></a>Notificaciones

__Compatibilidad de Android Samsung KNOX con Intune__ Determinados modelos del teléfono Samsung Galaxy Ace no pueden administrarse con Intune, como los dispositivos Samsung KNOX. Cuando inscriba estos dispositivos con Intune, se administrarán en su lugar como dispositivos estándar de Android.

Los números de los modelos afectados son:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Sus usuarios finales y usted no necesitan realizar ninguna otra acción. Para obtener más información, visite el sitio web de [Samsung KNOX](https://www.samsungknox.com).

__La aplicación portal de empresa de Windows 8 está en desuso; el soporte para las plataformas de Windows Phone 8 y Windows RT está en desuso__ A partir de octubre de 2016, Microsoft Intune dejará de ofrecer soporte para el portal de empresa de Windows 8. Microsoft Intune también dejará de ofrecer soporte para la plataforma Windows Phone 8 y Windows RT. Como consecuencia, no podrá inscribir ni actualizar ningún dispositivo Windows Phone 8 o Windows RT.

Puede seguir administrando los dispositivos Windows Phone 8, Windows RT y Windows 8 que ya estén inscritos. Actualice los dispositivos Windows Phone 8 y Windows 8 a Windows 8.1 y Windows Phone 8.1 y use las aplicaciones de portal de empresa de Windows 8.1 y Windows Phone 8.1 correspondientes para poder seguir con la distribución de aplicaciones en estos dispositivos sin interrupciones.

A partir de noviembre de 2016, dejaremos de ofrecer soporte para el portal de empresa de Windows Phone 8.
<!--TFS 1255391-->

### <a name="whats-coming"></a>Próximas novedades

__Nuevo portal de empresa de Microsoft Intune disponible para los dispositivos Windows 10__ Microsoft está lanzando un nuevo portal de empresa de Microsoft Intune para los dispositivos Windows 10. Esta aplicación, que aprovecha el nuevo formato de Windows 10 Universal, proporcionará al usuario una experiencia de usuario actualizada dentro de la aplicación y experiencias idénticas en todos los dispositivos Windows 10, PC y móvil, mientras sigue permitiendo las mismas funcionalidades que usa hoy en día.

La nueva aplicación también permitirá a los usuarios aprovechar características de plataforma adicional como el inicio de sesión único (SSO) y la autenticación basada en certificados en dispositivos Windows 10. La aplicación estará disponible como una actualización del portal de empresa de Windows 8.1 existente y este se instala desde la Tienda Windows. Para más información, vaya a [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).
<!--TFS 1016502-->

## <a name="september-2016"></a>Septiembre de 2016
### <a name="new-features-announcements-and-information"></a>Nuevas características, anuncios e Información
* [Acceso condicional de Windows](#windows-conditional-access)
* [Compatibilidad con iOS 10](#ios-10-support)
* [La herramienta de ajuste de aplicaciones es compatible con MAM sin la inscripción de dispositivos para Android e iOS](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [Los grupos de Intune comienzan la transición a Azure Active Directory en septiembre](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Integración de Lookout para proteger los dispositivos Android](#lookout-integration-to-protect-android-devices)
* [Actualizaciones del portal de empresa para Android, iOS y Windows](#company-portal-updates)
* [Glosario de Intune](#intune-glossary)
* [Próximas novedades](#whats-coming)

### <a name="windows-conditional-access"></a>Acceso condicional de Windows
Ahora puede crear directivas de acceso condicional a través de la consola de administración de Intune para impedir que los equipos Windows tengan acceso a Exchange Online y SharePoint Online. También puede crear directivas de acceso condicional para bloquear el acceso a aplicaciones de escritorio y universales de Office.

### <a name="ios-10-support"></a>Compatibilidad con iOS 10
Los escenarios MDM y MAM existentes de Intune son compatibles con iOS 10. Para obtener sugerencias, consulte el [log del equipo de soporte técnico de Intune](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>La herramienta de ajuste de aplicaciones es compatible con MAM sin la inscripción de dispositivos para Android e iOS
La herramienta de ajuste de aplicaciones de Intune es una herramienta de línea de comandos que se usa para habilitar MAM de Intune en las aplicaciones de línea de negocio (LOB) para iOS y Android. Esta es la manera más sencilla de incorporar el SKU de MAM de Intune en su aplicación, de forma que su aplicación pueda aplicar directivas de MAM que se han implementado mediante Intune. Con las directivas de MAM puede:

1. Cifrar los datos de la aplicación.
2. Requerir que el trabajador de la información escriba un PIN al iniciar la aplicación.
3. Permitir que la aplicación transfiera datos solo a otras aplicaciones administradas.
4. Evitar que la aplicación realice una copia de seguridad de los datos en Android, iTunes e iCloud.
5. Permitir solo las opciones Cortar, Copiar y Pegar dentro y fuera de otras aplicaciones administradas.

La versión preliminar pública y actualizada de la herramienta de ajuste de aplicaciones de Intune ahora admite MAM sin inscripción de dispositivos en aplicaciones de LOB internas en iOS y Android. Esto significa que los usuarios finales no necesitan inscribir sus dispositivos con Intune para usar aplicaciones de LOB habilitadas para MAM.

Cualquier usuario puede probar el software de la versión preliminar pública y leer la documentación útil, situada en GitHub de msintuneappsdk:

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Antes de que instale y use la versión preliminar de Microsoft Intune App Wrapper para Android y iOS, debe:

* Revisar los Términos de licencia de Microsoft para la versión preliminar de la herramienta de ajuste de aplicaciones de Microsoft Intune para Android e iOS
* Imprimir y conservar una copia de los términos de licencia para sus archivos. Al descargar y usar la versión preliminar de la herramienta de ajuste de aplicaciones de Microsoft Intune para Android, acepta dichos términos de licencia. Si no los acepta, no use el software.
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>Los grupos de Intune comienzan la transición a Azure Active Directory en septiembre
Algunas cuentas nuevas de Intune usarán los grupos de seguridad de Azure Active Directory en lugar de los grupos de usuarios de Intune. Sabrá que está trabajando con grupos de seguridad, ya que la página de grupos del portal de Intune tendrá un vínculo que le dirigirá al Portal de administración de Azure.

### <a name="lookout-integration-to-protect-android-devices"></a>Integración de Lookout para proteger los dispositivos Android
Microsoft se está integrando en la solución de protección de amenazas móviles de Lookout para proteger los dispositivos móviles Android mediante la detección de malware y aplicaciones de riesgo, entre otros, en los dispositivos. La solución de Lookout le ayuda a determinar el nivel de amenaza, que es configurable. Puede crear una regla de directivas de cumplimiento en Intune para terminar el cumplimiento de dispositivo basándose en la evaluación de riesgos mediante Lookout. Con las directivas de acceso condicional, puede permitir o bloquear el acceso a los recursos empresariales basándose en el estado de cumplimiento del dispositivo.

A los usuarios finales de los dispositivos no compatibles se les solicitará que se inscriban; necesitarán instalar la aplicación Lookout for Work en los dispositivos Android, activar la aplicación y corregir las amenazas que se mencionan en la aplicación Lookout for Work para obtener acceso. Para obtener más información, vea [Restrict access based on device, network, and application risk](/intune-classic/deploy-use/device-threat-protection) (Restringir el acceso basándose en el riesgo del dispositivo, de la red y de la aplicación).


### <a name="company-portal-updates"></a>Actualizaciones del portal de empresa

__Android__

<p style="margin-left: 40px">**Adición de "Notificaciones" al portal de empresa para Android**<br/>
<p style="margin-left: 40px">Se ha agregado un nuevo icono Notificaciones al portal de empresa para Android en la página principal. Al pulsar este icono, tendrá acceso a la página Notificaciones, que mostrará al usuario final todos los elementos que requieren atención en la aplicación de portal de empresa, como el no cumplimiento de dispositivos, la actualización de inscripciones y la activación de inscripciones. La aplicación de portal de empresa para iOS ya tiene esta experiencia de notificaciones. Tener la nueva página Notificaciones significa que el usuario no verá la página Configuración de acceso a la empresa cada vez que inicie o reanude el portal de empresa, siempre que el dispositivo ya esté inscrito. Si crea sus propias instrucciones de usuario final, puede que quiera actualizar su documentación para reflejar este cambio. Puede encontrar capturas de pantalla actualizadas [aquí](https://aka.ms/androidcpupdate).  

__iOS__
<p style="margin-left: 40px">**Cambios en la compatibilidad de la aplicación de portal de empresa de iOS**<br/>
<p style="margin-left: 40px">Todos los usuarios de la aplicación de portal de empresa de Microsoft Intune ahora necesitan usar la última versión. Los usuarios nuevos pueden descargar solo la última versión, y los usuarios actuales necesitan actualizarla. La versión más reciente requiere iOS 8.0 o posterior, de modo que los dispositivos que ejecuten versiones anteriores de iOS no pueden usar el portal de empresa ni inscribirse hasta que se actualicen a iOS 8.0 o posterior y, luego, se actualice la aplicación de portal de empresa a la versión más reciente. Los dispositivos inscritos que ejecuten versiones anteriores a iOS 8.0 seguirán administrándose y apareciendo en la consola de administración de Intune.
<!---TFS 1283165--->

<p style="margin-left: 40px">**Mejoras en cómo los usuarios finales de iOS obtienen sus aplicaciones**<br/>
<p style="margin-left: 40px">Los siguientes cambios se han realizado en los iconos de aplicaciones en la aplicación de portal de empresa para iOS para que apunte a los usuarios a distintas vistas en una única ubicación, el sitio web de portal de empresa, para todas sus aplicaciones. Las restricciones de Apple prohíben que se muestren la línea de negocio y las aplicaciones de la tienda de aplicaciones administrada en la aplicación de portal de empresa de la tienda y requieren a los usuarios visitar vistas diferentes para encontrar todas sus aplicaciones.

<p style="margin-left: 40px">El icono **Aplicaciones de la empresa** anteriormente apuntaba a una lista de todas las aplicaciones de la pestaña TODAS del sitio web de Portal de empresa, y seguirá funcionando del mismo modo. El nombre del icono ha cambiado a **Todas las aplicaciones**.

<p style="margin-left: 40px">El icono **Otras aplicaciones** antes apuntaba a una vista, dentro de la aplicación de portal de empresa, que enumera todas las aplicaciones que Apple permite mostrar a la aplicación de portal de empresa. El nombre del icono ha cambiado a **Aplicaciones destacadas** y, si pulsa en él, se le dirigirá a la pestaña Destacadas del sitio web de portal de empresa.

<p style="margin-left: 40px">El icono **Categorías** anteriormente apuntaba a una vista, dentro de la aplicación de portal de empresa, que enumera las categorías de aplicaciones. El nombre del icono no ha cambiado, pero ahora apunta a la pestaña Categorías del sitio web de portal de empresa. Puede encontrar las capturas de pantalla actualizadas [aquí](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
  <!---TFS 1317133--->

<p style="margin-left: 40px">**Preguntar para instalar la aplicación del explorador administrado de iOS si el profesional de TI establece ese requisito para una aplicación**<br/>
<p style="margin-left: 40px">Si ha configurado un clip de web para abrirlo solo en el explorador administrado y este no está instalado en un dispositivo, la aplicación de portal de empresa en el dispositivo le solicitará al usuario que instale el explorador administrado para poder instalar el clip web.
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**Botón Comentarios agregado a la aplicación de portal de empresa para Windows Phone 8.1**<br/>
<p style="margin-left: 40px">La aplicación de portal de empresa para Windows Phone 8.1 permite que los usuarios finales envíen comentarios sobre la aplicación mediante un nuevo botón "Enviar comentarios". Para encontrar el botón, los usuarios pulsan el menú "tres puntos" en la parte inferior derecha de la pantalla de la aplicación de portal de empresa y, después, **Enviar comentarios**. Los comentarios recopilados y anónimos ayudan a Microsoft a mejorar la experiencia de los usuarios en la aplicación de portal de empresa.
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Glosario de Intune</br>
Hemos agregado un nuevo [tema de glosario](/intune-classic/understand-explore/intune-glossary) a la biblioteca para que entienda algunos de los términos usados en el producto de Intune.

## <a name="august-2016"></a>Agosto de 2016
### <a name="app-management"></a>Administración de aplicaciones

__Aplicaciones ocultas y visibles para iOS 9.3__ En dispositivos con iOS 9.3 o versiones posteriores, puede usar la lista de aplicaciones ocultas y visibles de la directiva de configuración general de iOS para:
- Especificar una lista de las aplicaciones ocultas para los usuarios. Los usuarios no pueden ver ni iniciar estas aplicaciones.
- Especificar una lista de las aplicaciones que los usuarios pueden ver e iniciar. No se puede ver ni iniciar ninguna otra aplicación.

En las aplicaciones que puede especificar, se incluyen las dos aplicaciones que ha implementado, así como las aplicaciones iOS integradas, como Mensajes y Notas. Para obtener más información, vea [Configuración de directivas de iOS en Microsoft Intune](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune).
<!---TFS 1279009 checked--->
__Directiva de aplicaciones permitidas y bloqueadas para dispositivos Samsung KNOX__ Ahora puede configurar una directiva personalizada para dispositivos Samsung KNOX que permite crear una de las siguientes:
- Una lista de aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo. Aunque se instale, una aplicación incluida en esta lista no se puede activar en el dispositivo.
- Una lista de aplicaciones que los usuarios del dispositivo pueden instalar desde la tienda Google Play. Desde la tienda no se puede instalar ninguna otra aplicación.

Esta configuración solo se puede usar en dispositivos que ejecutan Samsung KNOX.
Para obtener más información, vea [Usar directivas personalizadas para permitir y bloquear aplicaciones en los dispositivos Samsung KNOX](/intune-classic/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps).
<!---TFS 1311629 checked --->

__Nuevas aplicaciones compatibles con las directivas de administración de aplicaciones móviles (MAM)__ La aplicación Yammer para [iOS](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), aunque el dispositivo no esté inscrito.

Para ver una lista completa de aplicaciones compatibles con MAM, consulte el sitio de los [asociados de aplicaciones de Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336 checked--->

__Aplicaciones de visor de Intune__ Con el lanzamiento de la nueva aplicación RMS sharing, quitaremos las siguientes aplicaciones de visor de Intune a partir de agosto de 2016:
- Visor de AV de Intune
- Visor de PDF de Intune
- Visor de imágenes de Intune para Android de Google Play

En lugar de usar las aplicaciones del Visor de Intune, le recomendamos que use la nueva aplicación Rights Management, que le permite implementar una aplicación en lugar de tres aplicaciones independientes, de modo que pueda consultar los archivos de la empresa de forma segura en dispositivos en Android. Cuando ya no se admita la aplicación de visor de Intune, se quitará de Google Store y no estará disponible para su uso futuro.

### <a name="device-management"></a>Administración de dispositivos
__Soporte técnico para Android 7.0__ Intune proporciona soporte "desde el primer momento" para el próximo sistema operativo Android 7.0 para dispositivos móviles.
<!---TFS 1262053--->
### <a name="google-removal-of-remote-passcode-reset-capability-on-android-70-devices"></a>Eliminación por parte de Google de la capacidad de restablecimiento de la contraseña remota en dispositivos Android 7.0
Google ha decidido eliminar la capacidad de los administradores de TI y los usuarios finales para restablecer la contraseña de dispositivos Android 7.0 de forma remota. Anteriormente, los administradores de TI podían restablecer de forma remota la contraseña de un usuario y los usuarios finales podían restablecer sus contraseñas desde el sitio web de Portal de empresa.



### <a name="company-portal-updates"></a>Actualizaciones del portal de empresa
__Sitio web del Portal de empresa__
- **Vínculo de comentarios del portal de empresa a Microsoft** <br/>
El sitio web de Portal de empresa permite a los usuarios finales pulsar un nuevo vínculo "Comentarios", situado en la parte inferior de la página, para enviar comentarios a Microsoft sobre su experiencia en el sitio. Los comentarios recopilados y anónimos ayudan a Microsoft a mejorar la experiencia de los usuarios en el sitio web de Portal de empresa.
<!--- TFS 1313657 checked--->

__iOS__
- **Versión mínima de Managed Browser para iOS actualizada a 8.0**<br/>
La aplicación Microsoft Intune Managed Browser para iOS se ha actualizado para admitir los dispositivos que ejecutan iOS 8.0 o versiones posteriores. Aunque que los dispositivos con iOS 7.1 todavía podrán usar la aplicación Managed Browser existente, anime a sus usuarios a actualizar a iOS 8.0 o versiones posteriores para tener acceso y aprovechar las nuevas características de Managed Browser.  
<!---TFS 1313253 checked--->

### <a name="whats-coming"></a>Próximas novedades
__La transición de grupos de Intune a grupos de Azure Active Directory comienza en septiembre de 2016__ Intune está creando una nueva experiencia de administración de grupos que usa grupos de seguridad de Azure Active Directory (AAD) como grupos de usuarios y dispositivos en Intune. Estos grupos se usarán para toda las administración de grupos, implementación de directivas e implementación de perfil **cuando presentemos el nuevo portal de administración de Intune basado en Azure**.

Esta nueva experiencia evitará tener que duplicar grupos entre servicios, **permitirá el acceso a algunas nuevas características de grupo de Azure Active Directory Premium (AADP)** y proporcionará extensibilidad con PowerShell y Graph. Esto también unificará la experiencia de administración de grupo a través de la administración de movilidad empresarial.

Para habilitar el movimiento a grupos de seguridad, la experiencia en la **consola de administración actual** sufrirá algunas modificaciones. **Estos cambios, y el uso de grupos de seguridad AAD, se registrarán en la documentación de Intune**.

Los clientes que son nuevos en Intune verán **algunos de los cambios de grupos de seguridad antes que los inquilinos actuales**.

Además de los cambios en la administración de grupos, **la siguiente funcionalidad dejará de utilizarse**:
- Excluir miembros o grupos al crear un nuevo grupo
- Grupos **Usuarios desagrupados** y **Dispositivos desagrupados**
- **Administrar grupos** en el rol de administrador de servicios
- Alertas personalizadas basadas en grupos para reglas de notificación
- Dinamizar con grupos en informes
<!--- TFS 1295329--->

__Adición de "Notificaciones" al portal de empresa para Android__ Vamos a lanzar una actualización en el portal de empresa para Android en septiembre que presentará un nuevo icono de **Notificaciones** en la página principal. Pulse este icono para acceder a la página **Notificaciones** que mostrará al usuario final todos los elementos que requieren atención en la aplicación Portal de empresa, como no cumplimiento de dispositivos, actualización de inscripciones y activación de inscripciones. Si también usa la aplicación de Portal de la compañía de iOS, ya verá la experiencia de notificaciones. Con la introducción de la página **Notificaciones**, no verá la página **Configuración de acceso a la empresa** cada vez que inicia o reanuda el Portal de empresa para Android, siempre que el dispositivo ya esté inscrito. Tenemos conocimiento de que muchos usuarios han creado una guía para el usuario final y agradecemos que nos avisen por adelantado cuando la guía y las capturas de pantalla necesiten actualizarse. Actualice la documentación para reflejar el próximo cambio en la experiencia. Busque las capturas de pantalla actualizadas en https://aka.ms/androidcpupdate.  

### <a name="service-deprecation"></a>Degradación del servicio

- **Cambios en la compatibilidad de la aplicación de portal de empresa de iOS**<br/>
En septiembre, todos los usuarios de la aplicación Portal de empresa de Microsoft Intune para iOS deberán usar la versión más reciente. Los nuevos usuarios solo podrán descargar la versión más reciente y se pedirá a los usuarios actuales que la actualicen. La versión más reciente requiere iOS 8.0 o posterior, de modo que los dispositivos que ejecuten versiones anteriores de iOS no podrán usar el portal de empresa ni inscribirse hasta que se actualicen a iOS 8.0 o posterior y, luego, se actualice la aplicación de portal de empresa a la versión más reciente. Los dispositivos inscritos que ejecuten versiones anteriores a iOS 8.0 seguirán administrándose y apareciendo en la consola de administración de Intune.  

- **Versión mínima de Managed Browser para iOS actualizada a 8.0**<br/>
En agosto, Intune publicará una aplicación Microsoft Intune Managed Browser actualizada para iOS que solo admitirá los dispositivos que ejecuten iOS 8.0 o posterior. Aunque que los dispositivos con iOS 7.1 todavía podrán usar la aplicación Managed Browser existente, anime a sus usuarios a actualizar a iOS 8.0 o posterior para tener acceso y aprovechar las nuevas características de Managed Browser.  
<!---TFS 1313253--->

- **Las aplicaciones de portal de empresa para Windows 8 y Windows Phone 8 se dejarán de usar a partir de septiembre de 2016** <br/>
A partir de septiembre de 2016, Microsoft Intune dejará de proporcionar soporte para las aplicaciones de Portal de empresa de Microsoft Intune para las plataformas Windows Phone 8 y Windows 8. Actualice los dispositivos a Windows 8.1 y Windows Phone 8.1 y use las aplicaciones de portal de empresa de Windows 8.1 y Windows Phone 8.1 correspondientes para poder seguir con la distribución de aplicaciones en estos dispositivos.
<!---TFS 1255391--->
