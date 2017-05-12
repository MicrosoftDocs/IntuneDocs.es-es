---
title: "Novedades de la versión preliminar de Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Descubra las novedades de la versión preliminar de Intune Azure"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: f209429bbafe50530e90bbaf133f780f448a8c57
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017

---

# <a name="whats-new-in-the-microsoft-intune-preview"></a>Novedades de la versión preliminar de Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

A medida que avance la versión preliminar pública y se agreguen más características, proporcionaremos información sobre ellas aquí.

> [!Note]
> Estamos implementando los cambios incluidos en esta página para la versión preliminar de Azure Portal. Sin embargo, pueden que los cambios no estén disponibles inmediatamente debido a la forma en que se ha actualizado el servicio de Intune.  Varios componentes del servicio deben actualizarse de manera secuencial antes de que estén disponibles las nuevas características del Portal. Busque estos cambios cuando se implementen este mes.

## <a name="april-2017"></a>Abril de 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Compatibilidad para administrar la aplicación Classroom de Apple

Ahora puede administrar la aplicación Classroom de iOS en dispositivos iPad. Configure la aplicación Classroom en el iPad de los profesores con los datos correctos de la clase y los estudiantes y, a continuación, configure los iPad de los estudiantes registrados en la clase, de modo que pueda controlarlos mediante la aplicación.
Para obtener más detalles, vea [Configuración de dispositivos iOS para el entorno educativo](../configure-devices/how-to-configure-ios-edu-settings.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Compatibilidad con las opciones de configuración administradas para aplicaciones Android <!-- 621621 -->

Intune ahora puede configurar las aplicaciones Android de Play Store que admiten opciones de configuración administradas.  Esta característica permite al equipo de TI ver la lista de valores de configuración que admite una aplicación y proporciona una interfaz de usuario interactiva y de primera clase que les permite configurar dichos valores.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nueva directiva de Android para PIN complejos <!-- 722069 -->

Ahora puede establecer un tipo de [contraseña](../configure-devices/device-restrictions-for-android.md#password) obligatoria de complejo numérico en un perfil de dispositivo Android para dispositivos que ejecutan Android 5.0 y versiones posteriores.  Use esta opción para impedir que los usuarios de los dispositivos creen un PIN que contenga números repetidos o consecutivos, como 1111 o 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Soporte adicional para dispositivos Android for Work

- **Administrar la configuración del perfil de trabajo y la contraseña** <!-- 612808 -->

  Esta nueva directiva de restricción de dispositivos Android for Work ahora permite administrar la configuración del perfil de trabajo y la contraseña en los dispositivos Android for Work que administre.

- **Permitir el uso compartido de datos entre perfiles profesionales y personales** <!-- 1045102 -->

Este perfil de restricción de dispositivos Android for Work ahora tiene opciones nuevas que le ayudarán a configurar el uso compartido de datos entre el perfil profesional y el perfil personal.

- **Restringir las acciones de copiar y pegar entre perfiles profesionales y personales** <!-- 1046094 -->

  Un perfil de dispositivo personalizado para dispositivos Android for Work ahora permite restringir si se permiten las acciones de copiar y pegar entre aplicaciones profesionales y personales.

Para más información, consulte [Restricciones de dispositivos para Android for Work](../configure-devices/device-restrictions-for-afw.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Asignar aplicaciones de LOB a dispositivos iOS y Android <!-- 1057568 -->

Ahora puede asignar aplicaciones de línea de negocio para [iOS](../manage-apps/ios-lob-app.md) (archivos .ipa) y [Android](../manage-apps/android-lob-app.md) (archivos .apk) a usuarios o dispositivos.

###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Nuevas directivas de dispositivo para iOS <!-- 723774, 723815, 723826, 723830 -->

- **Aplicaciones en la pantalla principal**: controla qué aplicaciones ven los usuarios en la [pantalla principal de sus dispositivos iOS](../configure-devices/home-screen-settings-for-ios.md). Esta directiva cambia el diseño de la pantalla principal, pero no implementa ninguna aplicación que especifique y no esté instalada.

- **Conexiones con dispositivos AirPrint**: controla a qué [dispositivos AirPrint](../configure-devices/air-print-settings-for-ios-and-macos.md) (impresoras de red) se pueden conectar los usuarios finales de dispositivos iOS.

- **Conexiones con dispositivos AirPlay**: controla a qué [dispositivos AirPlay](../configure-devices/airplay-settings-for-ios-devices.md) (como Apple TV) se pueden conectar los usuarios finales de dispositivos iOS.

- **Mensaje personalizado de la pantalla de bloqueo**: configurar un mensaje personalizado que verán los usuarios en la pantalla de bloqueo de sus dispositivos iOS y que reemplaza al mensaje predeterminado de esa pantalla. Para más información, consulte las [acciones de dispositivo disponibles](../manage-devices/what-is.md#available-device-actions)


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Restringir las notificaciones de inserción para aplicaciones iOS <!-- 723767 -->

En un perfil de restricción de dispositivos de Intune, ahora puede configurar los siguientes [ajustes de notificación](../configure-devices/app-notification-settings-for-ios.md) para dispositivos iOS:

- Activar o desactivar completamente las notificaciones para una aplicación especificada.
- Activar o desactivar la notificación en el centro de notificaciones para una aplicación especificada.
- Especificar el tipo de alerta como **None** (Ninguna), **Banner** (Mensaje emergente) o **Modal Alert** (Alerta modal).
- Especificar si se permiten los distintivos para esta aplicación.
- Especificar si se permiten los sonidos de notificaciones.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurar aplicaciones iOS para que se ejecuten en el modo de aplicación única de forma autónoma <!-- 737837 -->

Puede usar un perfil de dispositivo de Intune para configurar dispositivos iOS de modo que ejecuten aplicaciones especificadas en [modo de aplicación única autónoma](../configure-devices/device-restrictions-for-ios.md#autonomous-single-app-mode-supervised-only). Cuando se configura este modo y se ejecuta la aplicación, el dispositivo se bloquea para que solo pueda ejecutar esa aplicación. Un ejemplo es cuando se configura una aplicación que permite a los usuarios hacer un examen en el dispositivo. Cuando se completan las acciones de la aplicación, o quita esta directiva, el dispositivo vuelve a su estado normal.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurar dominios de confianza para el correo electrónico y la exploración web en dispositivos iOS <!-- 723765 -->

Desde un perfil de restricción de dispositivos iOS, ahora puede configurar los [valores de dominio](../configure-devices/device-restrictions-for-ios.md#domains) siguientes:

- **Dominios de correo electrónico sin marcar**: los correos electrónicos que el usuario envía o recibe y no coinciden con los dominios que especifique aquí se marcarán como que no son de confianza.

- **Dominios web administrados**: los documentos que se descargan de las direcciones URL que especifique aquí se considerarán administrados (solo en Safari).  

- **Dominios de relleno automático de contraseña de Safari**: los usuarios pueden guardar en Safari las contraseñas solo de las direcciones URL que coincidan con los patrones que especifique aquí. Para usar esta opción, el dispositivo debe estar en modo supervisado y no estar configurado para varios usuarios. (iOS 9.3 y versiones posteriores)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>Aplicaciones de PCV disponibles en el Portal de empresa de iOS <!-- 748782 -->

Ahora puede asignar aplicaciones de compras por volumen (PCV) de iOS como instalaciones **Disponibles** para usuarios finales. Los usuarios finales necesitarán una cuenta de Apple Store para instalar la aplicación.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizar libros electrónicos de la tienda de compras por volumen de Apple <!-- 800878 -->

Ahora puede [sincronizar los libros](../manage-apps/ios-vpp-apps.md) que haya adquirido a través de la tienda del programa de compras por volumen de Apple con Intune y asignarlos a los usuarios.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Administración de varios usuarios para dispositivos Samsung KNOX Standard <!-- 971988 -->

Intune es compatible ahora con dispositivos que ejecutan Samsung KNOX Standard para la [administración de varios usuarios](../enroll-devices/enroll-android-and-knox-standard-devices.md). Esto significa que los usuarios finales pueden iniciar y cerrar sesión en el dispositivo con sus credenciales de Azure Active Directory, y que el dispositivo se administra centralmente tanto si está en uso como si no.  Cuando los usuarios finales inician sesión, tienen acceso a aplicaciones, además de las directivas aplicadas a ellas. Cuando los usuarios cierran sesión, se borran todos los datos de la aplicación.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Configuración adicional de restricción de dispositivos Windows <!-- 818566 -->

Hemos agregado compatibilidad con [opciones de configuración adicionales de restricción de dispositivos Windows](../configure-devices/device-restrictions-for-windows-10.md), como la compatibilidad adicional con el explorador Edge, la personalización de la pantalla de bloqueo del dispositivo, las personalizaciones del menú Inicio, el papel tapiz del conjunto de búsqueda de Contenido destacado de Windows y la configuración de proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Compatibilidad con varios usuarios para Windows 10 Creators Update <!-- 822547 -->

Hemos agregado compatibilidad para la [administración de varios usuarios](../enroll-devices/enroll-windows-devices.md) en dispositivos que ejecutan Windows 10 Creators Update y están unidos al dominio de Azure Active Directory. Esto significa que cuando varios usuarios estándar inicien sesión en el dispositivo con sus credenciales de Azure AD, recibirán las aplicaciones y las directivas que se hayan asignado a sus nombres de usuario. Actualmente, los usuarios no puede usar Portal de empresa para escenarios de autoservicio, como la instalación de aplicaciones.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start para equipos con Windows 10<!-- 1004830 -->

Ahora hay disponible una nueva [acción de dispositivo Fresh Start](../manage-devices/what-is.md#available-device-actions) para equipos Windows 10.  Cuando se lleva a cabo esta acción, se quitan las aplicaciones que hubiera instaladas en el equipo y este se actualiza automáticamente a la última versión de Windows. Esto puede servir para ayudar a quitar las aplicaciones de OEM preinstaladas que a menudo se entregan con los nuevos PC. Puede configurar si se conservan los datos de usuario cuando se lleva a cabo esta acción de dispositivo.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Rutas de actualización adicionales de Windows 10 <!-- 903672 -->

Ahora puede crear una [directiva de actualización de edición para actualizar los dispositivos](../configure-devices/how-to-configure-windows-10-edition-upgrade.md) a las siguientes ediciones adicionales de Windows 10:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Inscripción masiva de dispositivos Windows 10 <!-- 747607 -->

Ahora puede unir grandes cantidades de dispositivos que ejecutan Windows 10 Creator Update a Azure Active Directory e Intune con Windows Configuration Designer (WCD). Para habilitar la [inscripción masiva de MDM](../enroll-devices/bulk-enroll-windows.md) para el inquilino de Azure AD, cree un paquete de aprovisionamiento que una dispositivos al inquilino de Azure AD a través de Windows Configuration Designer y aplique el paquete a los dispositivos corporativos que desea inscribir y administrar de forma masiva. Una vez que el paquete se aplica a los dispositivos, se unirán a Azure AD, se inscribirán en Intune y estarán listos para que los usuarios de Azure AD inicien sesión.  Los usuarios de Azure AD son usuarios estándar en estos dispositivos y reciben las aplicaciones requeridas y las directivas asignadas. En este momento, no se admiten los escenarios de autoservicio ni de portal de empresa.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Nueva configuración de MAM para PIN y ubicaciones de almacenamiento administrado <!-- 581122, 736644 -->

Ahora hay disponibles dos nuevas opciones de configuración de aplicaciones que le ayudarán con los escenarios de administración de aplicaciones móviles (MAM):

- **Disable app PIN when device PIN is managed** (Deshabilitar el PIN de aplicación cuando se administra el PIN del dispositivo): detecta si hay un PIN de dispositivo en el dispositivo inscrito y, si es así, omite el PIN de aplicación desencadenado por las directivas de protección de aplicaciones. Esta configuración permitirá reducir el número de veces que se muestra una solicitud de PIN a los usuarios que abran una aplicación habilitada para MAM en un dispositivo inscrito. Esta característica está disponible para iOS y Android.

- **Seleccione en qué servicios de almacenamiento se puede guardar datos empresariales**: permite especificar en qué ubicaciones de almacenamiento quiere guardar los datos corporativos. Los usuarios pueden guardar en los servicios de ubicación de almacenamiento seleccionados, lo que implica que se bloquearán todos los demás servicios de ubicación de almacenamiento no indicados.

  Lista de servicios de ubicación de almacenamiento compatibles:

  - OneDrive
  - OneDrive para la Empresa/SharePoint Online
  - Almacenamiento local

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portal de solución de problemas del departamento de soporte técnico <!-- 907448 -->

El nuevo [portal de solución de problemas](../manage-users/help-desk.md) permite que los operadores del departamento de soporte técnico y los administradores de Intune vean a los usuarios y sus dispositivos y, además, realicen tareas para solucionar problemas técnicos de Intune.

## <a name="march-2017"></a>Marzo de 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Compatibilidad con Modo Perdido de iOS <!--431695-->

En iOS 9.3 y dispositivos posteriores, Intune agrega compatibilidad con **Modo Perdido**. Ahora puede bloquear un dispositivo para evitar su uso, así como mostrar un mensaje y llamar al número de teléfono de la pantalla de bloqueo del dispositivo.

El usuario final no podrá desbloquear el dispositivo hasta que un administrador deshabilite Modo Perdido. Cuando está activado el Modo Perdido, puede usar la acción **Buscar dispositivo** para ver la ubicación geográfica del dispositivo en un mapa en la consola de Intune.

El dispositivo debe ser un dispositivo iOS de la empresa, inscrito mediante DEP, que esté en modo supervisado.

Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](../manage-devices/what-is.md)

### <a name="improvements-to-device-actions-report---677150--"></a>Mejoras en los informes de las acciones del dispositivo <!--677150-->

Hemos realizado mejoras en el informe de las acciones del dispositivo para mejorar el rendimiento. Además, ahora puede filtrar el informe por estado. Por ejemplo, puede filtrar el informe para mostrar únicamente las acciones de dispositivo que se han completado".

### <a name="actions-for-non-compliance---730266--"></a>Acciones en caso de incumplimiento <!--730266-->

**Acciones en caso de incumplimiento** es una nueva característica de directivas de cumplimiento que le permite realizar acciones en dispositivos no compatibles. Puede especificar una o varias acciones y especificar el período de tiempo en el que se deben producir esas acciones. Por ejemplo, puede notificar a los usuarios de dispositivos no compatibles inmediatamente después de que el dispositivo se convierta en no compatible mediante el correo electrónico, o puede impedir que los dispositivos no compatibles tengan acceso a los recursos corporativos después de un período de gracia de 3 días mediante el acceso condicional.

### <a name="custom-app-categories---748805--"></a>Categorías de aplicaciones personalizadas <!--748805-->

Ahora puede crear, editar y asignar categorías a las aplicaciones que agregue a Intune. En estos momentos, las categorías solo pueden especificarse en inglés.
Consulte [How to add an app to Intune](../manage-apps/add-apps.md) (Cómo agregar una aplicación a Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Asignación de aplicaciones LOB a los usuarios con dispositivos no inscritos <!--748823-->

Ahora puede asignar aplicaciones de línea de negocio desde la tienda a usuarios tengan o no inscritos sus dispositivos con Intune. Si el dispositivo de los usuarios no está inscrito con Intune, deben ir al sitio web del Portal de empresa para instalarlo, en lugar de a la aplicación del Portal de empresa.

### <a name="new-compliance-reports---846671--"></a>Nuevos informes de cumplimiento <!--846671-->

Ahora dispone de informes de cumplimiento que proporcionan la posición de cumplimiento de los dispositivos de su empresa y le permiten solucionar rápidamente los problemas relacionados con el cumplimiento detectados por los usuarios. Puede ver información acerca de

- Estado de cumplimiento general de los dispositivos
- Estado de cumplimiento de una configuración individual
- Estado de cumplimiento de una directiva individual

También puede utilizar estos informes para profundizar en un dispositivo individual para ver la configuración específica y las directivas que afectan a dicho dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->

Para las cuentas de Intune creadas después de enero de 2017, Intune ha habilitado el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en el portal de vista previa de Azure. Anteriormente, la vista previa de inscripción de Apple solo era accesible desde los vínculos al portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requerirán una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero la información estará disponible tan pronto como sea posible. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta no tiene acceso a la versión preliminar.


## <a name="february-2017"></a>Febrero de 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Capacidad para restringir la inscripción de dispositivos móviles <!--747600, 795782-->
Intune está agregando nuevas restricciones de inscripción que controlan qué plataformas de dispositivos móviles pueden inscribir. Intune separa las plataformas de dispositivos móviles como iOS, Mac OS, Android, Windows y Windows Mobile.

* La restricción la inscripción de dispositivos móviles no restringe la inscripción del cliente de PC.  
* Solo para iOS y Android, hay una opción adicional para bloquear la inscripción de dispositivos de propiedad personal.

Intune marca todos los dispositivos nuevos como personal a menos que el administrador de TI tome la medida de marcarlos como propiedad de la empresa, como se explica en [este artículo](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Ver todas las acciones en los dispositivos administrados <!--677150-->
Un nuevo informe __Acciones de dispositivo__ muestra quién ha realizado acciones remotas como el restablecimiento de fábrica en dispositivos y, además, muestra el estado de esa acción. Vea [¿Qué es la administración de dispositivos?](https://docs.microsoft.com../manage-devices/what-is.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Los dispositivos no administrados puedan acceder a aplicaciones asignadas <!--664691-->
Como parte de los cambios de diseño en el sitio web del portal de empresa, los usuarios de iOS y Android podrán instalar aplicaciones asignadas a ellos como "disponibles sin inscripción" en sus dispositivos no administrados. Con sus credenciales de Intune, los usuarios podrán iniciar sesión en el sitio web del portal de empresa y ver la lista de aplicaciones asignadas. Los paquetes de aplicación de las aplicaciones "disponibles sin inscripción" se encuentran disponibles para descargar a través del sitio web del portal de empresa. Las aplicaciones que requieren la inscripción para la instalación no se ven afectadas por este cambio, ya que se les pedirá a los usuarios que inscriban su dispositivo si quieren instalar esas aplicaciones.

### <a name="custom-app-categories---748805--"></a>Categorías de aplicaciones personalizadas <!--748805-->
Ahora puede crear, editar y asignar categorías a las aplicaciones que agregue a Intune. En estos momentos, las categorías solo pueden especificarse en inglés.
Consulte [How to add an app to Intune](../manage-apps/add-apps.md) (Cómo agregar una aplicación a Intune).

### <a name="display-device-categories---814654--"></a>Mostrar categorías de dispositivos <!--814654-->
Ahora puede ver la categoría del dispositivo como una columna en la lista de dispositivos. También puede editar la categoría desde la sección de propiedades de la hoja de propiedades del dispositivo. Consulte [How to add an app to Intune](../manage-apps/add-apps.md) (Cómo agregar una aplicación a Intune).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configuración de Windows Update para empresas <!--776716-->

Windows como servicio es la nueva forma de proporcionar actualizaciones para Windows 10. A partir de Windows 10, todas las nuevas actualizaciones de calidad y características contienen las actualizaciones anteriores. Es decir, siempre que haya instalado la más reciente, sabrá que sus dispositivos Windows 10 están completamente actualizados. A diferencia de las versiones anteriores de Windows, ahora debe instalar la actualización completa en lugar de una parte.

Gracias a Windows Update para empresas, puede simplificar la administración de actualizaciones, ya que no tendrá que aprobar actualizaciones individuales para grupos de dispositivos. Todavía puede administrar los riesgos en sus entornos configurando una estrategia de implementación de actualizaciones; Windows Update se asegurará de que las actualizaciones se instalen en el momento oportuno. Microsoft Intune ofrece la posibilidad de configurar las actualizaciones en los dispositivos y de aplazar su instalación. Intune no almacena las actualizaciones, sino únicamente la asignación de las directivas de actualización. Los dispositivos acceden a Windows Update directamente para instalar las actualizaciones. Use Intune para configurar y administrar los **anillos de actualización de Windows 10**. Un anillo de actualización contiene un grupo de opciones que configuran cuándo y cómo se instalan las actualizaciones de Windows 10. Para obtener más información, consulte [Configuración de Windows Update para empresas](../configure-devices/how-to-configure-windows-update-for-business.md).

## <a name="january-2017"></a>Enero de 2017

### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748823--"></a>Asignar aplicaciones de línea de negocio en dispositivos inscritos y no inscritos <!--748823-->
Ahora puede asignar aplicaciones de línea de negocio desde la tienda a usuarios tengan o no inscritos sus dispositivos con Intune. Si el dispositivo de los usuarios no está inscrito con Intune, deben ir al sitio web del portal de empresa para instalarlo, en lugar de a la aplicación de portal de empresa. [¿Qué es la administración de aplicaciones?](../manage-apps/what-is-app-management.md)

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them"></a>Resolver el problema en el que los dispositivos iOS están inactivos o la consola de administración no puede comunicarse con ellos
Cuando los dispositivos de los usuarios pierden el contacto con Intune, puede proporcionarles nuevos pasos de solución de problemas para ayudarles a volver a obtener acceso a los recursos de la empresa. Vea [Los dispositivos están inactivos o la consola de administración no puede comunicarse con ellos](../enroll-devices/troubleshoot-device-enrollment.md#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="december-2016-initial-release"></a>Diciembre de 2016 (versión inicial)

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integración de la administración de gastos de telecomunicaciones en la versión preliminar pública del portal de Azure<!--747605-->
Ahora estamos comenzando a realizar la integración de la versión preliminar con los servicios de administración de gastos de telecomunicaciones (TEM) dentro del portal de Azure. Puede usar Intune para exigir límites sobre el uso de datos nacionales y móviles. Comenzaremos estas integraciones con [Saaswedo](http://www.saaswedo.com). Para habilitar esta característica en su inquilino de prueba, [póngase en contacto con el soporte técnico de Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

- Implementación y administración de aplicaciones de la tienda en dispositivos iOS, Android y Windows
- Implementación y administración de aplicaciones de línea de negocio (LOB) en dispositivos iOS, Android y Windows
- Implementación y administración de aplicaciones compradas por volumen en dispositivos iOS y Windows
- Implementación y administración de aplicaciones web para dispositivos Android, iOS y Windows
- Perfiles de configuración de aplicaciones administrados por iOS
- Configuración de directivas de protección de aplicaciones e implementación de aplicaciones de línea de negocio en dispositivos no inscritos en Intune
- Perfiles de VPN, VPN por aplicación, Wi-Fi, correo electrónico y perfiles de certificado
- Directivas de cumplimiento
- Acceso condicional para Azure AD
- Acceso condicional para Exchange local
- Inscripción de dispositivos
- Control de acceso basado en roles

## <a name="deprecated-features-in-the-azure-portal"></a>Características en desuso en el portal de Azure

### <a name="support-for-row-by-row-review-of-hardware-identifiers"></a>Compatibilidad con la revisión fila a fila de identificadores de hardware
El portal de Azure no admite la revisión fila a fila de identificadores de hardware para números IMEI y números de serie de Apple. En la consola de Intune clásica, puede importar detalles de un archivo de valores separados por comas (.csv) y sobrescribir los detalles existentes para identificadores de hardware individuales. El portal de Azure presenta una única opción optimizada que sobrescribe automáticamente los detalles de todos los identificadores de hardware u omite nuevos detalles de identificadores existentes.

#### <a name="how-this-affects-you"></a>Cómo afecta esto
En el portal de Azure, no podrá decidir, fila a fila, qué dispositivos de identidad de equipo móvil internacional (IMEI) se actualizarán. La consola de Intune clásica seguirá admitiendo esta funcionalidad.

#### <a name="how-to-get-ready-for-this-change"></a>Cómo prepararse para este cambio
Vamos a proporcionar esta información de antemano; así, en caso de que le afecte, pueda informar a sus administradores de soporte técnico de este cambio. Este cambio coincidirá con el paso al portal de Azure, previsto para la primera mitad de 2017.


### <a name="support-for-default-corporate-device-enrollment-profiles-in-apple-dep"></a>Compatibilidad con perfiles de Inscripción de dispositivos corporativos en DEP de Apple
El portal de Azure no admite el perfil de inscripción de dispositivos corporativos "predeterminado" para los números de serie de dispositivo del Programa de inscripción de dispositivos de Apple (DEP). Esta funcionalidad, disponible en la consola de Intune clásica, está en desuso para evitar que se asignen perfiles involuntariamente. En el portal de Azure, los números de serie sincronizados desde una cuenta de DEP de Apple inicialmente no tendrán asignado ningún perfil de inscripción de dispositivos corporativos.

#### <a name="how-this-affects-you"></a>Cómo afecta esto
En el portal de Azure, no podrá establecer una directiva de perfil predeterminada en todos los dispositivos Apple. La consola de Intune clásica seguirá admitiendo esta funcionalidad.

#### <a name="how-to-get-ready-for-this-change"></a>Cómo prepararse para este cambio
Vamos a proporcionar esta información de antemano; así, en caso de que le afecte, pueda informar a sus administradores de soporte técnico de este cambio. Este cambio coincidirá con el movimiento al portal de Azure, previsto para la primera mitad de 2017.

