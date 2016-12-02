---
title: Archivo de novedades | Microsoft Intune
description: Anuncios de novedades archivados de Microsoft Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aa8fe81b6a9f6b11bba9c15ede36d9df9cd2e0da
ms.openlocfilehash: 72a2f8026d1a67a3a49111daa9a7b8380b0cb088


---
# <a name="whats-new---archive"></a>Archivo de novedades

Esta página es un archivo de anuncios recientes realizados en [Novedades de Microsoft Intune](whats-new-in-microsoft-intune.md).

## <a name="october-2016"></a>Octubre de 2016

### <a name="conditional-access-for-mobile-application-management"></a>Acceso condicional para la administración de aplicaciones móviles
Podrá restringir el acceso a Exchange Online de forma que el acceso solo proceda de aplicaciones que admitan las directivas de administración de aplicaciones móviles de Intune, como Outlook. [Esta nueva característica](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) se adapta perfectamente a las directivas de administración de aplicaciones móviles (MAM) de Intune, ya que puede bloquear el acceso a los clientes de correo integrado u otras aplicaciones que no se hayan configurado con las directivas de MAM de Intune. Esto garantiza que los usuarios están teniendo acceso a los datos de su organización con aplicaciones que pueden estar protegidas mediante MAM de Intune. Puede comenzar a trabajar en la administración de aplicaciones móviles de Intune mediante Azure Portal. Busque la nueva sección de acceso condicional en la hoja "Configuración".

### <a name="conditional-access-for-windows-pcs"></a>Acceso condicional para equipos Windows
Ahora puede crear directivas de acceso condicional a través de la consola de administración de Intune para impedir que los equipos Windows tengan acceso a [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) y a [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune). También puede crear directivas de acceso condicional para bloquear el acceso a aplicaciones de escritorio y universales de Office.

### <a name="android-for-work-support"></a>Compatibilidad de Android for Work

> [!IMPORTANT]

> Aunque se pueden implementar aplicaciones Android for Work con una acción __Requerido__, solo se pueden implementar aplicaciones como __Disponible__ si los grupos de Intune se han migrado a la nueva experiencia de grupos de Azure AD.

Intune ahora forma parte del programa de Android for Work (AfW). Comenzaremos este mes por implementar la compatibilidad con las características de AfW y continuaremos en los próximos meses. Tenga en cuenta que la implementación de aplicaciones disponibles de AfW aprovecha la nueva experiencia de agrupación y selección de destino. Las cuentas de servicio de Intune aprovisionadas recientemente podrán usar esta característica cuando AfW esté disponible para ellas.

<!--Existing Intune customers can use this feature in production once their tenant has been migrated. Existing customers are welcome to create a trial Intune account to plan for and test this feature until their tenant has been migrated. Any questions on grouping and targeting timelines, please contact our [migration team](mailto:intunegrps@microsoft.com).-->

[Lea el anuncio de Microsoft sobre la compatibilidad de Intune con Android for Work](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

Los temas de Intune siguientes son nuevos o actualizados con la información de Android for Work:

Para profesionales de TI:
- [Configurar Android for Work](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [Restringir el acceso de correo electrónico a Exchange Online y nuevo Exchange Online dedicado](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Restringir el acceso de correo electrónico a Exchange local y Exchange Online dedicado heredado con Intune](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Configuración de directivas de cumplimiento para dispositivos Android for Work](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [Implementación de aplicaciones Android for Work](/intune/deploy-use/android-for-work-apps)
- [Configuración de aplicaciones Android for Work con directivas de configuración de aplicaciones móviles](/intune/deploy-use/afw-app-configuration-policy)
- [Opciones de directivas de Android for Work](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

Para usuarios finales:
- [¿Qué ocurre cuando se crea un perfil de trabajo?](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [Creación de un perfil de trabajo e inscripción del dispositivo en Intune](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### <a name="lookout-integration-to-protect-ios-devices"></a>Integración de Lookout para proteger los dispositivos iOS
En octubre, Microsoft se está integrando en la solución de protección de amenazas móviles de Lookout para proteger los dispositivos móviles iOS mediante la detección de malware y aplicaciones de riesgo, entre otros, en los dispositivos. La solución de Lookout le ayuda a determinar el nivel de amenaza, que es configurable. Puede crear una regla de directivas de cumplimiento en Intune para terminar el cumplimiento de dispositivo basándose en la evaluación de riesgos mediante Lookout. Con las directivas de acceso condicional, puede permitir o bloquear el acceso a los recursos empresariales basándose en el estado de cumplimiento del dispositivo.

A los usuarios finales de los dispositivos iOS no compatibles se les solicitará que se inscriban; necesitarán instalar la aplicación Lookout for Work en sus dispositivos, activar la aplicación y corregir las amenazas que se mencionan en la aplicación Lookout for Work para obtener acceso a los datos de la empresa. Obtenga información sobre cómo [Configurar e implementar aplicaciones Lookout for Work](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps).
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### <a name="intune-app-wrapping-tool-for-android"></a>Herramienta de ajuste de aplicaciones Intune para Android
Puede habilitar las aplicaciones para que usen directivas de administración de aplicaciones móviles (MAM) de Intune mediante la herramienta de ajuste de aplicaciones de Intune. La compatibilidad con directivas MAM de Intune sin requerir la inscripción de dispositivos ya está disponible.

### <a name="manage-printing-from-apps-managed-using-mam-policies"></a>Administrar la impresión desde aplicaciones administradas mediante directivas MAM
Ahora puede evitar la impresión de datos empresariales desde aplicaciones que tengan directivas MAM. Esta configuración está disponible en [Azure Portal](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) y se admite tanto en dispositivos [iOS](/Intune/deploy-use/ios-mam-policy-settings) como [Android](/Intune/deploy-use/android-mam-policy-settings).
<!--TFS 1014328-->

### <a name="support-for-fingerprints-on-android-devices"></a>Compatibilidad con huellas digitales en dispositivos Android
Las directivas de administración de aplicaciones móviles (MAM) de Android permiten ahora a los usuarios acceder a una aplicación con su huella digital en lugar de la entrada del PIN. Consulte [aquí esta y otras configuraciones de directiva de administración de aplicaciones móviles](/Intune/deploy-use/android-mam-policy-settings).

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

A los usuarios finales de los dispositivos no compatibles se les solicitará que se inscriban; necesitarán instalar la aplicación Lookout for Work en los dispositivos Android, activar la aplicación y corregir las amenazas que se mencionan en la aplicación Lookout for Work para obtener acceso. Para obtener más información, vea [Restrict access based on device, network, and application risk](restrict-access-based-on-device-network-app-risk.md) (Restringir el acceso basándose en el riesgo del dispositivo, de la red y de la aplicación).


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
Hemos agregado un nuevo [tema de glosario](https://docs.microsoft.com/intune/understand-explore/intune-glossary) a la biblioteca para que entienda algunos de los términos usados en el producto de Intune.

## <a name="august-2016"></a>Agosto de 2016
### <a name="app-management"></a>Administración de aplicaciones
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

__Aplicaciones ocultas y visibles para iOS 9.3__ En dispositivos con iOS 9.3 o versiones posteriores, puede usar la lista de aplicaciones ocultas y visibles de la directiva de configuración general de iOS para:
- Especificar una lista de las aplicaciones ocultas para los usuarios. Los usuarios no pueden ver ni iniciar estas aplicaciones.
- Especificar una lista de las aplicaciones que los usuarios pueden ver e iniciar. No se puede ver ni iniciar ninguna otra aplicación.

En las aplicaciones que puede especificar, se incluyen las dos aplicaciones que ha implementado, así como las aplicaciones iOS integradas, como Mensajes y Notas. Para obtener más información, vea [Configuración de directivas de iOS en Microsoft Intune]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune).
<!---TFS 1279009 checked--->
__Directiva de aplicaciones permitidas y bloqueadas para dispositivos Samsung KNOX__ Ahora puede configurar una directiva personalizada para dispositivos Samsung KNOX que permite crear una de las siguientes:
- Una lista de aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo. Aunque se instale, una aplicación incluida en esta lista no se puede activar en el dispositivo.
- Una lista de aplicaciones que los usuarios del dispositivo pueden instalar desde la tienda Google Play. Desde la tienda no se puede instalar ninguna otra aplicación.

Esta configuración solo se puede usar en dispositivos que ejecutan Samsung KNOX.
Para obtener más información, vea [Usar directivas personalizadas para permitir y bloquear aplicaciones en los dispositivos Samsung KNOX]( custom-policy-to-allow-and-block-samsung-knox-apps.md).
<!---TFS 1311629 checked --->
__Nuevas aplicaciones compatibles con las directivas de administración de aplicaciones móviles (MAM)__ La aplicación Yammer para [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) y [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) es compatible ahora con las [directivas de administración de aplicaciones móviles (MAM) de Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), independientemente de si el dispositivo está inscrito o no.

Para ver una lista completa de aplicaciones compatibles con MAM, consulte el sitio de los [asociados de aplicaciones de Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

__Aplicaciones de visor de Intune__ Con el lanzamiento de la nueva aplicación RMS sharing, quitaremos las siguientes aplicaciones de visor de Intune a partir de agosto de 2016:
- Visor de AV de Intune
- Visor de PDF de Intune
- Visor de imágenes de Intune para Android de Google Play

En lugar de usar las aplicaciones de visor de Intune, se recomienda usar la nueva aplicación [Rights Management (RMS sharing) para Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app), que permite implementar una aplicación en lugar de tres aplicaciones independientes para ver archivos corporativos de forma segura en dispositivos Android. Cuando ya no se admita la aplicación de visor de Intune, se quitará de Google Store y no estará disponible para su uso futuro.

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
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Cambios en la compatibilidad de la aplicación de portal de empresa de iOS**<br/>
En septiembre, todos los usuarios de la aplicación Portal de empresa de Microsoft Intune para iOS deberán usar la versión más reciente. Los nuevos usuarios solo podrán descargar la versión más reciente y se pedirá a los usuarios actuales que la actualicen. La versión más reciente requiere iOS 8.0 o posterior, de modo que los dispositivos que ejecuten versiones anteriores de iOS no podrán usar el portal de empresa ni inscribirse hasta que se actualicen a iOS 8.0 o posterior y, luego, se actualice la aplicación de portal de empresa a la versión más reciente. Los dispositivos inscritos que ejecuten versiones anteriores a iOS 8.0 seguirán administrándose y apareciendo en la consola de administración de Intune.  

- **Versión mínima de Managed Browser para iOS actualizada a 8.0**<br/>
En agosto, Intune publicará una aplicación Microsoft Intune Managed Browser actualizada para iOS que solo admitirá los dispositivos que ejecuten iOS 8.0 o posterior. Aunque que los dispositivos con iOS 7.1 todavía podrán usar la aplicación Managed Browser existente, anime a sus usuarios a actualizar a iOS 8.0 o posterior para tener acceso y aprovechar las nuevas características de Managed Browser.  
<!---TFS 1313253--->

- **Las aplicaciones de portal de empresa para Windows 8 y Windows Phone 8 se dejarán de usar a partir de septiembre de 2016** <br/>
A partir de septiembre de 2016, Microsoft Intune dejará de proporcionar soporte para las aplicaciones de Portal de empresa de Microsoft Intune para las plataformas Windows Phone 8 y Windows 8. Actualice los dispositivos a Windows 8.1 y Windows Phone 8.1 y use las aplicaciones de portal de empresa de Windows 8.1 y Windows Phone 8.1 correspondientes para poder seguir con la distribución de aplicaciones en estos dispositivos.
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->

## <a name="july-2016"></a>Julio de 2016
### <a name="app-management"></a>Administración de aplicaciones

__Mejorar la aplicación aprovisionando una experiencia de actualización de perfil__ La línea de aplicaciones móviles empresariales de Apple iOS se crea con un perfil de aprovisionamiento incluido y código firmado con un certificado. Cuando la aplicación se ejecuta en un dispositivo iOS, iOS confirma la integridad de la aplicación de iOS y exige el cumplimiento de las directivas definidas por el perfil de aprovisionamiento.

El certificado de firma empresarial que se usa para firmar aplicaciones normalmente tiene una validez de 3 años. Sin embargo, el perfil de aprovisionamiento expira después de 1 año. Con esta actualización, Intune proporciona las herramientas para implementar proactivamente una nueva directiva de perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima mientras siga siendo válido el certificado. Para más información, consulte [Use iOS mobile provisioning profile policies to keep your line of business apps up to date (Usar directivas de perfil de aprovisionamiento móvil iOS para mantener al día sus aplicaciones de línea de negocio)](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->

__Xamarin SDK para aplicaciones de Intune está disponible__ El componente Intune App SDK Xamarin permite habilitar las características de administración de aplicaciones móviles de Intune en las aplicaciones móviles para iOS y Android creadas con Xamarin. Puede encontrar el componente en la [tienda de Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) o en la [página de Github de Microsoft Intune](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### <a name="device-management"></a>Administración de dispositivos
__Aumento de los límites de inscripción de dispositivos__ Intune ha aumentado el límite máximo de inscripción de dispositivos configurables de 5 a 15 dispositivos por usuario.
<!---TFS 1289896 --->

__Integración de TeamViewer para equipos Windows que ejecutan el software cliente de Intune__
La integración de [TeamViewer](https://www.teamviewer.com) para equipos Windows que ejecutan el software cliente de Intune permite establecer sesiones de asistencia remota en equipos Windows como apoyo para departamentos de soporte técnico para usuarios finales. Esto incluye Windows 7, 8, 8.1 y Windows 10. Para obtener más información, vea [Tareas comunes de administración de PC Windows con el cliente de equipo de Microsoft Intune](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>Actualizaciones del portal de empresa

__Sitio web del Portal de empresa__
- **Experiencia de usuario final mejorada al inscribir dispositivos de Windows**<br/>
Cuando usa acceso condicional, los pasos de inscripción para Windows 8.1, Windows 10 Escritorio y Windows 10 Mobile se han clarificado en el sitio web del Portal de empresa. Los usuarios ahora verán pasos "Inscripción de dispositivos" y "Unión al lugar de trabajo" independientes, lo que les facilita ver el estado de su dispositivo y completar el proceso si experimentan un error en Unión al lugar de trabajo (WPJ). También se espera que los pasos independientes simplifiquen el proceso de solución de problemas para los administradores de TI. Anteriormente, cuando los usuarios finales intentaban inscribirse y todos los pasos de la inscripción se llevaban a cabo correctamente excepto para WPJ, el dispositivo inscrito no aparecería en la lista de dispositivos para los usuarios para identificar, provocando confusión para los usuarios.

__Android__
- **Aplicación de portal de empresa de Android**<br/>
Si los usuarios finales Android ven un mensaje de error que dice que el dispositivo no tiene un certificado necesario, pueden pulsar un botón "Cómo resolver esto" para obtener [pasos](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) para instalar el certificado que falta. Si los usuarios completan los pasos, pero ven un mensaje de error adicional que indica que "falta el certificado", se les solicita que se pongan en contacto con su administrador de TI y proporcionen este [vínculo](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), que contiene pasos que los administradores de TI pueden usar para solucionar el problema del certificado.

- **Restringir instalaciones de aplicaciones de transferencia local a dispositivos inscritos**<br/>
Los dispositivos Android ya no pueden instalar aplicaciones a través del sitio web de Portal de empresa a menos que los dispositivos se hayan inscrito en Intune mediante la aplicación de Portal de empresa de Intune para Android.
<!---TFS 1299082--->

__iOS__
- **Cambios en las cuentas de administradores de inscripción de dispositivos en la aplicación de portal de empresa de iOS**<br/>
Para mejorar el rendimiento y la escalabilidad, Intune ya no mostrará todos los dispositivos de Administradores de inscripción de dispositivos (DEM) en el panel **Mis dispositivos** de la aplicación de Portal de empresa para iOS. Solo se muestra el dispositivo local que está ejecutando la aplicación y solo si está inscrito a través de la aplicación Portal de empresa.

El usuario de DEM puede realizar acciones en el dispositivo local, pero la administración remota de los demás dispositivos inscritos solo puede realizarse desde la consola de administración de Intune. Además, Intune está dejando de usar las cuentas de DEM con el Programa de inscripción de dispositivos de Apple o con la herramienta Apple Configurator. Estos métodos de inscripción ya admiten la inscripción sin usuarios para los dispositivos iOS compartidos.

Use las cuentas de DEM solo cuando no esté disponible la inscripción sin usuarios para los dispositivos compartidos. Para más información, consulte [Inscribir dispositivos propiedad de la empresa con el Administrador de inscripción de dispositivos de Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>Cambio de nombres de características de Windows
- [Microsoft Passport para Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) ahora se conoce como **Windows Hello para empresas**.
- [Protección de datos de empresa](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) ahora se conoce como **Windows Information Protection**.

## <a name="june-2016"></a>Junio de 2016
### <a name="intune-service-health"></a>Mantenimiento del servicio de Intune
La información de mantenimiento del servicio de Intune se ha movido a una ubicación central con otros servicios de Microsoft. Ahora encontrará esta información en el portal de administración de Office 365, en Estado del servicio. Para más información, consulte [esta entrada de blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Administración de aplicaciones
- **Mejoras en la experiencia de configuración de la directiva de datos de empresa de Windows 10.** Se han realizado mejoras en la experiencia de configuración de directivas de protección de datos de empresa de Windows 10 en relación con la creación de reglas de aplicaciones, la especificación de la definición de límite de red y otras opciones de protección de datos de empresa. Para más información, consulte [Create an enterprise data protection (EDP) policy using Microsoft Intune (Crear una directiva de protección de datos de empresa (EDP) con Microsoft Intune)](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### <a name="device-management"></a>Administración de dispositivos
- **Configuración de directiva de Windows Defender para la protección ante aplicaciones potencialmente no deseadas.** Se ha agregado una nueva configuración de Windows Defender denominada **Detección de aplicaciones potencialmente no deseadas** a la directiva de configuración general para Windows 10 Escritorio y Mobile. Puede usar esta configuración para proteger los equipos de escritorio de Windows inscritos ante la ejecución de software que Windows Defender ha clasificado como potencialmente no deseado. Puede protegerse contra la ejecución de estas aplicaciones o puede usar el modo auditoría para informar cuando se instale una aplicación potencialmente no deseada. Para más información, consulte [Configuración de directivas de Windows 10 en Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### <a name="conditional-access"></a>Acceso condicional
- **Directiva de control de acceso de red de Cisco ISE para Intune.**  Los clientes que usen Cisco Identity Service Engine (ISE) 2.1 y también usen Microsoft Intune pueden establecer una directiva de control de acceso de red en ISE.

    Al usar esta directiva, los dispositivos que necesiten conectarse a la red mediante WiFi o VPN deben cumplir las siguientes condiciones antes de que se les permita el acceso:

    * Deben administrarse mediante Intune
    * Deben cumplir todas las directivas de cumplimiento de Intune implementadas

 A los usuarios finales de los dispositivos no conformes se les solicitará que se inscriban y que solucionen cualquier problema de cumplimiento para obtener acceso.
- **Acceso condicional para el explorador.** Puede establecer una directiva de acceso condicional para [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) y [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) de modo que solo se pueda obtener acceso a ellos desde exploradores web compatibles en dispositivos administrados y compatibles con iOS y Android. A los usuarios finales que intenten iniciar sesión en Outlook Web Access (OWA) y en los sitios de SharePoint con dispositivos iOS y Android, se les solicitará que inscriban su dispositivo con Intune así como que solucionen cualquier problema de incumplimiento antes de completar el inicio de sesión.
<!---TFS 1175844--->

- **Dynamics CRM Online admite el acceso condicional.** Puede establecer una directiva de acceso condicional para [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) de modo que solo se pueda tener acceso a este con dispositivos administrados y compatibles con iOS y Android. Los usuarios finales que intenten iniciar sesión en la aplicación móvil de Dynamics CRM en iOS y Android tendrán que inscribirse en Intune y corregir cualquier problema de cumplimiento para poder iniciar sesión.
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Actualizaciones del portal de empresa de Intune

__Aplicación de portal de empresa de Android__

- Cuando los administradores de TI apliquen la nueva directiva "Los dispositivos deben impedir la instalación de aplicaciones de orígenes desconocidos (Android 4.0+)", los usuarios finales con dispositivos de Android 4.0 o posterior verán el mensaje "Debe deshabilitarse la instalación desde orígenes desconocidos". Los usuarios tendrán que ir a **Configuración** > **Seguridad** y desactivar **Orígenes desconocidos**. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener más [información](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) sobre el mensaje y el porqué de desactivar el valor.

- Cuando los administradores de TI apliquen la nueva directiva "Los dispositivos deben tener habilitada la opción "Buscar amenazas de seguridad en el dispositivo" (Android 4.0+)", los usuarios finales con dispositivos de Android 4.0 o posterior verán el mensaje "Buscar amenazas de seguridad en el dispositivo". Los usuarios tendrán que ir a **Configuración** > **Google** > **Seguridad** y activar **Buscar amenazas de seguridad en el dispositivo**. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener más [información](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre el mensaje y el porqué de activar el valor.

- Cuando los administradores de TI apliquen la nueva directiva "La depuración USB debe estar deshabilitada (Android 4.2+)", los usuarios finales con dispositivos de Android 4.2 o posterior verán el mensaje "La depuración USB debe deshabilitarse". Los usuarios tendrán que ir a **Configuración** > **Opciones del desarrollador** y desactivar **Depuración USB**. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener más [información](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) sobre el mensaje y el porqué de desactivar el valor.

- Cuando los administradores de TI apliquen la nueva directiva "Nivel mínimo de revisión de seguridad de Android (Android 6.0+)", los usuarios finales con dispositivos de Android 6.0 o posterior verán el mensaje "Este dispositivo no cumple el nivel mínimo de revisión de seguridad de Android". Los usuarios tendrán que instalar la revisión de seguridad necesaria. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener [información](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre cómo instalar la revisión de seguridad necesaria y ver qué revisión de seguridad tienen instalada en ese momento.

__Aplicación de portal de empresa de iOS__

- Cuando los usuarios finales instalen aplicaciones de línea empresarial, ahora podrán disfrutar una experiencia mejorada de instalación de la aplicación. Si la instalación de la aplicación tarda mucho, los usuarios pueden sincronizar manualmente el dispositivo para forzar que se reanude el proceso de sincronización. Para leer las instrucciones del usuario final, consulte [Sincronizar el dispositivo iOS manualmente](/Intune/EndUser/sync-your-device-manually-ios).

- La aplicación Portal de empresa de Microsoft Intune para iOS se ha actualizado y ahora admite la versión de iOS 8.0 y posteriores. Con esta actualización, los usuarios finales pueden instalar la aplicación Portal de empresa de Microsoft Intune e inscribir nuevos dispositivos en Intune solo si el dispositivo ejecuta la versión de iOS 8.0 o posterior. Los usuarios que ya han inscrito dispositivos que se ejecutan con una versión no compatible de iOS pueden seguir utilizando la aplicación Portal de empresa que está en su dispositivo.


## <a name="may-2016"></a>Mayo de 2016
Todas estas características también son compatibles en las implementaciones híbridas (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea la página sobre las [novedades de implementaciones híbridas](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### <a name="documentation"></a>Documentación
Le damos la bienvenida a la versión preliminar de [docs.microsoft.com](https://docs.microsoft.com/en-us/intune).
Se trata de una plataforma de contenido completamente nueva y moderna diseñada para facilitarles a los usuarios la comprensión y el uso de Intune.
Para más información sobre todas las características nuevas, vea [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/) (Introducción a docs.microsoft.com).

### <a name="intune-service-health"></a>Mantenimiento del servicio de Intune
La información de mantenimiento del servicio de Intune se ha movido a una ubicación central con otros servicios de Microsoft. Ahora encontrará esta información en el [portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx) en **Mantenimiento del servicio**.
Para más información, vea [esta entrada de blog](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### <a name="app-management"></a>Administración de aplicaciones
- **SDK de MAM: admite la configuración de longitud de PIN.** Podrá especificar la longitud del PIN para las aplicaciones de MAM como si fuera el PIN de un dispositivo. Esto requerirá que los usuarios finales cumplan con las nuevas restricciones que establezca. Verán una pantalla de PIN ligeramente modificada para tener en cuenta la entrada más larga. Para obtener más información, vea [Opciones de configuración de directiva de administración de aplicaciones móviles de Android en Microsoft Intune](/intune/deploy-use/android-mam-policy-settings) y [Configuración de directiva de administración de aplicaciones móviles iOS](/intune/deploy-use/ios-mam-policy-settings).

- **Skype Empresarial para iOS y Android.** Ahora puede abordar Skype Empresarial con [MAM sin las directivas de inscripción](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Cuando los usuarios inician sesión, se aplican las directivas de MAM.

- **Nuevas aplicaciones disponibles para la administración con directivas de MAM.** Las aplicaciones de Microsoft Word, Excel y PowerPoint para Android ahora pueden asociarse con directivas de MAM en los dispositivos que no están inscritos con Intune. Para ver una lista completa de las aplicaciones compatibles, vaya a la galería de aplicaciones móviles de Microsoft Intune de la página [Microsoft Intune application partners](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) (Socios de aplicaciones de Microsoft Intune).


### <a name="company-portal-updates"></a>Actualizaciones del portal de empresa

#### <a name="android-company-portal-app"></a>Aplicación Portal de empresa de Android
- **Notificaciones del sistema para el usuario final:** los usuarios finales ahora verán notificaciones del sistema de la aplicación de portal de empresa de Android cuando inscriban o quiten sus dispositivos desde el portal de empresa.

- **Cambios en las cuentas de administradores de inscripción de dispositivos en la aplicación de portal de empresa de Android.** Para mejorar el rendimiento y la escalabilidad, Intune ya no mostrará todos los dispositivos de administradores de inscripción de dispositivos (DEM) en el panel Mis dispositivos de la aplicación de portal de empresa de Android. Solo se muestra el dispositivo local que está ejecutando la aplicación y solo si está inscrito a través de la aplicación Portal de empresa. El usuario de DEM puede realizar acciones en el dispositivo local, pero la administración remota de los demás dispositivos inscritos solo puede realizarse desde la consola de administración de Intune.

#### <a name="company-portal-website"></a>Sitio web del Portal de empresa
- **Sitio web del portal de empresa: el banner de identificación de dispositivos proporcionará más información a los usuarios finales.** Los usuarios finales ahora pueden identificar más fácilmente el dispositivo que han seleccionado cuando están usando el sitio web del portal de empresa. Si hay seleccionado un dispositivo incorrecto, podrán seleccionar el dispositivo correcto pulsando en el vínculo **Pulsar aquí** en el banner de la página principal.

### <a name="service-deprecation"></a>Degradación del servicio
- **Aplicaciones de visor de Intune.** Con el lanzamiento de la nueva aplicación RMS sharing, quitaremos las siguientes aplicaciones de visor de Intune a partir de agosto de 2016:
    - Visor de AV de Intune
    - Visor de PDF de Intune
    - Visor de imágenes de Intune para Android de Google Play

  En lugar de usar las aplicaciones de visor de Intune, se recomienda usar la nueva aplicación Rights Management (RMS sharing) para Android, que permite implementar una aplicación en lugar de tres aplicaciones independientes para ver archivos corporativos de forma segura en dispositivos Android. Obtenga más información sobre la aplicación RMS sharing (con un vínculo a documentación).

- **Eliminación del grupo personalizado de destinatarios de reglas de notificación.**
Las reglas de notificación de Intune definen a quién se enviará una alerta de correo electrónico a través de Intune. Actualmente, puede configurar reglas de notificación para enviar mensajes de correo electrónico a todos los usuarios de dispositivos de un grupo de dispositivos de Intune que haya creado. Aproximadamente a partir del 1 de junio de 2016, ya no se admitirán los grupos creados por el usuario de destino.

    A día de hoy, para que una regla de notificación esté destinada a un grupo creado desde la consola de administración de Microsoft Intune, debe seguir los pasos siguientes:

    En el área de trabajo **Administración**, haga clic en **Reglas de notificación** > **Crear nueva regla**.

    En el paso 2 del Asistente para crear reglas de notificación, se seleccionan los grupos de dispositivos a los que se destinará la regla. Este paso ("Seleccionar grupos de dispositivos") se va a quitar de la consola de Intune.

    La escala de tiempo preliminar de este cambio es la siguiente:
    - En junio de 2016, los nuevos inquilinos no verán el paso 2 del Asistente para crear reglas de notificación. Los inquilinos existentes no se verán afectados.
    - Alrededor de agosto de 2016, algunos inquilinos existentes no verán la opción "Seleccionar grupos de dispositivos" en el asistente.
    - Alrededor de octubre de 2016, se espera que ningún inquilino vea la opción "Seleccionar grupos de dispositivos" en el asistente.


- **Cambios en la compatibilidad de la aplicación de portal de empresa de iOS.**. En los próximos meses, habrá una actualización para la aplicación de portal de empresa de Microsoft Intune para iOS que solo admitirá dispositivos que ejecuten iOS 8.0 o posterior. Los usuarios no podrán inscribir dispositivos nuevos que ejecuten versiones anteriores a iOS 8.0. Los dispositivos inscritos que ejecuten versiones anteriores a iOS 8.0 seguirán administrándose y, durante un tiempo limitado, podrá seguir usando la aplicación de portal de empresa. Pero los dispositivos deben tener iOS 8.0 o posterior para tener acceso a las últimas versiones de la aplicación de portal de empresa. Le recomendamos que notifique a los usuarios que actualicen a iOS 8.0 o posterior para aprovechar las nuevas características de Intune.  


## <a name="april-2016"></a>Abril de 2016
Todas estas características también son compatibles con los clientes híbridos (Configuration Manager integrado con Intune).

### <a name="app-management"></a>Administración de aplicaciones
- **Compatibilidad de usuario de MAM.**
Ahora puede ver el [estado](/intune/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune) de sus directivas de administración de aplicaciones para cualquier usuario en el inquilino de Azure Active Directory (AAD). Esto incluye:
   - Dispositivos
   - Aplicaciones del dispositivo

   Valores de estado:

   **Checked in (Comprobado)**: indica que la directiva se implementó para el usuario, y la aplicación se usó en un contexto profesional y recibió correctamente la directiva.

    **Not checked in (No comprobado)**: indica que la directiva se implementó para el usuario, pero la aplicación no se ha usado en un contexto profesional desde entonces.


- **Controles de MAM para evitar la sincronización de contactos de Outlook (Android).**
Hay una nueva opción de configuración disponible para la [administración de aplicaciones móviles](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) sin inscripción de dispositivos. Esta opción permite evitar que una aplicación sincronice contactos con la libreta de direcciones nativa en dispositivos Android. Si esta opción está habilitada, las aplicaciones de destino ya no podrán guardar contactos en la libreta de direcciones nativa. Si esta opción está deshabilitada, las aplicaciones de destino podrán guardar contactos en la libreta de direcciones nativa. Al [borrar un dispositivo o aplicación de forma remota](/intune/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune), se quitarán todos los contactos que ya se hayan guardado en la libreta de direcciones nativa. Esta nueva opción es compatible inicialmente con la aplicación Outlook en dispositivos Android.

### <a name="device-management"></a>Administración de dispositivos
- **Identificación de número de teléfono para dispositivos propiedad de la empresa.** Los teléfonos que están clasificados como "Corporativos" se identifican ahora con el número de teléfono completo, por ejemplo, al ejecutar un informe de inventario de dispositivos móviles. Los números de teléfono BYOD se seguirán enmascarando con ****; y solo se mostrarán los últimos 4 dígitos.


### <a name="company-portal-updates"></a>Actualizaciones de Portal de empresa
**Aplicación de portal de empresa de Android** Los usuarios que no han inscrito su dispositivo en Intune y que no tienen el certificado correcto instalado, no podrán iniciar sesión en la aplicación de portal de empresa de Android y verán el mensaje "No puede iniciar sesión porque falta un certificado necesario en su dispositivo". El mensaje incluye un vínculo "Cómo resolver esto" que los usuarios pueden pulsar para ver instrucciones para instalar el certificado. Para ver los pasos que los usuarios finales siguen para solucionar el problema, vea [Uso de un dispositivo Android con Intune](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**Aplicación de portal de empresa de iOS** Se ha agregado soporte técnico para que la acción de deslizar para actualizar actualice el contenido en la pantalla principal, que incluye aplicaciones y dispositivos enumerados e información de contacto de TI. Las acciones de deslizar para actualizar no comprueban el cumplimiento ni la información de la directiva, que puede realizarse al seleccionar el icono de su dispositivo actual y pulsar el botón **Sincronizar**.

**La aplicación de portal de empresa de Windows 10 Mobile y Windows Phone 8.1** Cuando los usuarios finales instalen aplicaciones de línea empresarial, ahora podrán disfrutar de una experiencia mejorada de instalación de la aplicación. Si la instalación de la aplicación tarda mucho, los usuarios pueden sincronizar manualmente el dispositivo para forzar que se reanude el proceso de sincronización. Para revisar las instrucciones del usuario final, vea [Usar un dispositivo Windows con Intune](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Sitio web de portal de empresa** Cuando los usuarios de Windows 10 Mobile y Windows Phone 8.1 instalen aplicaciones de línea empresarial, ahora podrán disfrutar de los siguientes estados nuevos, que les proporcionan más información sobre el estado de su instalación:

* **Esperando a que se sincronice el dispositivo**: el usuario ha pulsado "Instalar" y el dispositivo ahora se intenta sincronizar mediante la infraestructura de Intune. La sincronización es necesaria antes de que se complete la instalación. El mensaje "Esperando a que se sincronice el dispositivo" también es un vínculo que los usuarios pueden pulsar para ver [instrucciones](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) sobre cómo sincronizar manualmente su dispositivo con Intune si el proceso de sincronización tarda mucho o se detiene.
* **Descargando**: la solicitud de descarga del usuario se está procesando y el dispositivo está descargando e instalando la aplicación.

Antes de que se agregaran estos estados, los usuarios se confundían si una instalación de aplicación tardaba mucho, porque solo veían el estando "Instalando", que puede permanecer en la pantalla durante horas. Al agregar los nuevos estados, en vez de llamar al soporte técnico, los usuarios ahora pueden pulsar el vínculo "Esperando a que se sincronice el dispositivo" y seguir las instrucciones para forzar que se reanude el proceso de sincronización.



### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new-in-microsoft-intune.md) para obtener más información sobre los desarrollos recientes.



<!--HONumber=Nov16_HO3-->


