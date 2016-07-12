---
title: Versiones anteriores | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.reviewer: mamoriss
ms.suite: ems
ms.sourcegitcommit: 3080d23f464e96315ed9e5fd59774ba9f1b2dd86
ms.openlocfilehash: 65d582958d77150091880cce72e079b87308209f


---

# Versiones anteriores de Intune
## Mayo de 2016

Todas estas características también son compatibles en las implementaciones híbridas (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea la página sobre las [novedades de implementaciones híbridas](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### Documentación
Le damos la bienvenida a la versión preliminar de [docs.microsoft.com](https://docs.microsoft.com/en-us/intune).
Se trata de una plataforma de contenido completamente nueva y moderna diseñada para facilitarles a los usuarios la comprensión y el uso de Intune.
Para más información sobre todas las características nuevas, vea [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/) (Introducción a docs.microsoft.com).

### Mantenimiento del servicio de Intune
La información de mantenimiento del servicio de Intune se ha movido a una ubicación central con otros servicios de Microsoft. Ahora encontrará esta información en el [portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx) en **Mantenimiento del servicio**.
Para más información, vea [esta entrada de blog](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### Administración de aplicaciones
- **SDK de MAM: Admite la configuración de longitud de PIN.** Podrá especificar la longitud del PIN para las aplicaciones de MAM como si fuera el PIN de un dispositivo. Esto requerirá que los usuarios finales cumplan con las nuevas restricciones que establezca. Verán una pantalla de PIN ligeramente modificada para tener en cuenta la entrada más larga. Para más información, vea [MAM policy settings for Android](/intune/deploy-use/android-mam-policy-settings) (Configuración de directivas de MAM para Android) y [MAM policy settings for iOS](/intune/deploy-use/ios-mam-policy-settings) (Configuración de directivas de MAM para iOS).

- **Skype Empresarial para iOS y Android.** Ahora puede abordar Skype Empresarial con [MAM sin las directivas de inscripción](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Cuando los usuarios inician sesión, se aplican las directivas de MAM.

- **Nuevas aplicaciones disponibles para la administración con directivas de MAM.** Las aplicaciones de Microsoft Word, Excel y PowerPoint para Android ahora pueden asociarse con directivas de MAM en los dispositivos que no están inscritos con Intune. Para ver una lista completa de las aplicaciones compatibles, vaya a la galería de aplicaciones móviles de Microsoft Intune de la página [Microsoft Intune application partners](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) (Socios de aplicaciones de Microsoft Intune).


### Actualizaciones del portal de empresa

#### Aplicación Portal de empresa de Android
- **Notificaciones del sistema para el usuario final:** los usuarios finales ahora verán notificaciones del sistema de la aplicación de portal de empresa de Android cuando inscriban o quiten sus dispositivos desde el portal de empresa.

- **Cambios en las cuentas de administradores de inscripción de dispositivos en la aplicación de portal de empresa Android.** Para mejorar el rendimiento y la escalabilidad, Intune ya no mostrará todos los dispositivos de administradores de inscripción de dispositivos (DEM) en el panel Mis dispositivos de la aplicación de portal de empresa de Android. Solo se muestra el dispositivo local que está ejecutando la aplicación y solo si está inscrito a través de la aplicación Portal de empresa. El usuario de DEM puede realizar acciones en el dispositivo local, pero la administración remota de los demás dispositivos inscritos solo puede realizarse desde la consola de administración de Intune.

#### Sitio web del Portal de empresa
- **Sitio web del portal de empresa: el banner de identificación de dispositivos proporcionará más información a los usuarios finales.** Los usuarios finales ahora pueden identificar más fácilmente el dispositivo que han seleccionado cuando están usando el sitio web del portal de empresa. Si hay seleccionado un dispositivo incorrecto, podrán seleccionar el dispositivo correcto pulsando en el vínculo **Pulsar aquí** en el banner de la página principal.

## Próximas novedades
- **Incorporación de la interfaz de usuario del Centro de mensajes.**. Como parte de la migración de Intune al [Portal de administración de Office 365](https://portal.office.com/), nos aprovecharemos de su Centro de mensajes para comunicar las características nuevas y otras notificaciones. Además, al instalar la aplicación móvil complementaria de administración de Office 365, puede recibir notificaciones en su teléfono móvil y reenviar fácilmente cualquier mensaje a los usuarios o a un alias de distribución.
Empezaremos a usar el Centro de Mensajes con nuestro lanzamiento de mayo para notificarle cuándo se completan las actualizaciones e incluiremos información sobre las características nuevas y mejoradas de Intune. Consulte hoy el Centro de mensajes iniciando sesión en el [portal de administración de Office 365](https://portal.office.com/) y elija la opción CENTRO DE MENSAJES en el panel de navegación izquierdo.

- **Cambios en las cuentas de administradores de inscripción de dispositivos.**. Para mejorar el rendimiento y la escalabilidad, Intune ya no mostrará **todos** los dispositivos de administradores de inscripción de dispositivos (DEM) en el panel **Mis dispositivos** de la aplicación de portal de empresa de iOS. Solo se muestra el dispositivo local que está ejecutando la aplicación y solo si está inscrito a través de la aplicación Portal de empresa. El usuario de DEM puede realizar acciones en el dispositivo local, pero la administración remota de los demás dispositivos inscritos solo puede realizarse desde la consola de administración de Intune. Además, Intune está dejando de usar las cuentas de DEM con el Programa de inscripción de dispositivos de Apple o con la herramienta Apple Configurator. Estos métodos de inscripción ya admiten la inscripción sin usuarios para los dispositivos iOS compartidos. Use las cuentas de DEM solo cuando no esté disponible la inscripción sin usuarios para los dispositivos compartidos.

### Guía básica de la nube
Manténgase informado sobre los próximos desarrollos para Intune con la [Guía básica de Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Degradación del servicio
- **Aplicaciones de visor de Intune.** Con el lanzamiento de la nueva aplicación RMS sharing, quitaremos las siguientes aplicaciones de visor de Intune a partir de agosto de 2016:
    - Visor de AV de Intune
    - Visor de PDF de Intune
    - Visor de imágenes de Intune para Android de Google Play

  En lugar de usar las aplicaciones de visor de Intune, se recomienda usar la nueva aplicación Rights Management (RMS sharing) para Android, que permite implementar una aplicación en lugar de tres aplicaciones independientes para ver archivos corporativos de forma segura en dispositivos Android. Obtenga más información sobre la aplicación RMS sharing (con un vínculo a documentación).

- **Grupo personalizado de destino de retirada de reglas de notificación.**
Las reglas de notificación de Intune definen a quién se enviará una alerta de correo electrónico a través de Intune. Actualmente, puede configurar reglas de notificación para enviar mensajes de correo electrónico a todos los usuarios de dispositivos de un grupo de dispositivos de Intune que haya creado. Aproximadamente a partir del 1 de junio de 2016, ya no se admitirán los grupos creados por el usuario de destino.

    A día de hoy, para que una regla de notificación esté destinada a un grupo creado desde la consola de administración de Microsoft Intune, debe seguir los pasos siguientes:

    En el área de trabajo **Administración**, haga clic en **Reglas de notificación** > **Crear nueva regla**.

    En el paso 2 del Asistente para crear reglas de notificación, se seleccionan los grupos de dispositivos a los que se destinará la regla. Este paso ("Seleccionar grupos de dispositivos") se va a quitar de la consola de Intune.

    La escala de tiempo preliminar de este cambio es la siguiente:
    - En junio de 2016, los nuevos inquilinos no verán el paso 2 del Asistente para crear reglas de notificación. Los inquilinos existentes no se verán afectados.
    - Alrededor de agosto de 2016, algunos inquilinos existentes no verán la opción "Seleccionar grupos de dispositivos" en el asistente.
    - Alrededor de octubre de 2016, se espera que ningún inquilino vea la opción "Seleccionar grupos de dispositivos" en el asistente.


- **Cambios en la compatibilidad de la aplicación de portal de empresa de iOS.**. En los próximos meses, habrá una actualización para la aplicación de portal de empresa de Microsoft Intune para iOS que solo admitirá dispositivos que ejecuten iOS 8.0 o posterior. Los usuarios no podrán inscribir dispositivos nuevos que ejecuten versiones anteriores a iOS 8.0. Los dispositivos inscritos que ejecuten versiones anteriores a iOS 8.0 seguirán administrándose y, durante un tiempo limitado, podrá seguir usando la aplicación de portal de empresa. Pero los dispositivos deben tener iOS 8.0 o posterior para tener acceso a las últimas versiones de la aplicación de portal de empresa. Le recomendamos que notifique a los usuarios que actualicen a iOS 8.0 o posterior para aprovechar las nuevas características de Intune.  


## Abril de 2016
Todas estas características también son compatibles con los clientes híbridos (Configuration Manager integrado con Intune).
### Administración de aplicaciones
- **Compatibilidad de usuario de MAM.**
Ahora puede ver el [estado](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) de sus directivas de administración de aplicaciones para cualquier usuario en el inquilino de Azure Active Directory (AAD). Esto incluye:
   - Dispositivos
   - Aplicaciones del dispositivo

   Valores de estado:

   **Checked in (Comprobado)**: indica que la directiva se implementó para el usuario, y la aplicación se usó en un contexto profesional y recibió correctamente la directiva.

    **Not checked in (No comprobado)**: indica que la directiva se implementó para el usuario, pero la aplicación no se ha usado en un contexto profesional desde entonces.


- **Controles de MAM para evitar la sincronización de contactos de Outlook (Android).**
Hay una nueva opción de configuración disponible para la [administración de aplicaciones móviles](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) sin inscripción de dispositivos. Esta opción permite evitar que una aplicación sincronice contactos con la libreta de direcciones nativa en dispositivos Android. Si esta opción está habilitada, las aplicaciones de destino ya no podrán guardar contactos en la libreta de direcciones nativa. Si esta opción está deshabilitada, las aplicaciones de destino podrán guardar contactos en la libreta de direcciones nativa. Al [borrar un dispositivo o aplicación de forma remota](wipe-managed-company-app-data-with-Microsoft-Intune.md), se quitarán todos los contactos que ya se hayan guardado en la libreta de direcciones nativa. Esta nueva opción es compatible inicialmente con la aplicación Outlook en dispositivos Android.

### Administración de dispositivos
- **Identificación de número de teléfono para dispositivos propiedad de la empresa.** Los teléfonos que están clasificados como "Corporativos" se identifican ahora con el número de teléfono completo, por ejemplo, al ejecutar un informe de inventario de dispositivos móviles. Los números de teléfono BYOD se seguirán enmascarando con ****; y solo se mostrarán los últimos 4 dígitos.


### Actualizaciones de Portal de empresa
**Aplicación de portal de empresa de Android** Los usuarios que no han inscrito su dispositivo en Intune y que no tienen el certificado correcto instalado, no podrán iniciar sesión en la aplicación de portal de empresa de Android y verán el mensaje "No puede iniciar sesión porque falta un certificado necesario en su dispositivo". El mensaje incluye un vínculo "Cómo resolver esto" que los usuarios pueden pulsar para ver instrucciones para instalar el certificado. Para ver los pasos que los usuarios finales siguen para solucionar el problema, vea [Uso de un dispositivo Android con Intune](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**Aplicación de portal de empresa de iOS** Se ha agregado soporte técnico para que la acción de deslizar para actualizar actualice el contenido en la pantalla principal, que incluye aplicaciones y dispositivos enumerados e información de contacto de TI. Las acciones de deslizar para actualizar no comprueban el cumplimiento ni la información de la directiva, que puede realizarse al seleccionar el icono de su dispositivo actual y pulsar el botón **Sincronizar**.

**La aplicación de portal de empresa de Windows 10 Mobile y Windows Phone 8.1** Cuando los usuarios finales instalen aplicaciones de línea empresarial, ahora podrán disfrutar de una experiencia mejorada de instalación de la aplicación. Si la instalación de la aplicación tarda mucho, los usuarios pueden sincronizar manualmente el dispositivo para forzar que se reanude el proceso de sincronización. Para revisar las instrucciones del usuario final, vea [Usar un dispositivo Windows con Intune](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Sitio web de portal de empresa** Cuando los usuarios de Windows 10 Mobile y Windows Phone 8.1 instalen aplicaciones de línea empresarial, ahora podrán disfrutar de los siguientes estados nuevos, que les proporcionan más información sobre el estado de su instalación:

* **Esperando a que se sincronice el dispositivo**: el usuario ha pulsado "Instalar" y el dispositivo ahora se intenta sincronizar mediante la infraestructura de Intune. La sincronización es necesaria antes de que se complete la instalación. El mensaje "Esperando a que se sincronice el dispositivo" también es un vínculo que los usuarios pueden pulsar para ver [instrucciones](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) sobre cómo sincronizar manualmente su dispositivo con Intune si el proceso de sincronización tarda mucho o se detiene.
* **Descargando**: la solicitud de descarga del usuario se está procesando y el dispositivo está descargando e instalando la aplicación.

Antes de que se agregaran estos estados, los usuarios se confundían si una instalación de aplicación tardaba mucho, porque solo veían el estando "Instalando", que puede permanecer en la pantalla durante horas. Al agregar los nuevos estados, en vez de llamar al soporte técnico, los usuarios ahora pueden pulsar el vínculo "Esperando a que se sincronice el dispositivo" y seguir las instrucciones para forzar que se reanude el proceso de sincronización.


## Marzo de 2016
### Novedades a día 29 de marzo de 2016
A excepción de la actualización de la directiva de configuración general de Windows 10, todas las características publicadas el 29 de marzo de 2016 son compatibles con los clientes híbridos (Configuration Manager integrado con Intune). La compatibilidad híbrida con la actualización de la directiva de configuración general de Windows 10 estará disponible próximamente. Tenga en cuenta que algunas de estas características pueden exigir la versión más reciente de Configuration Manager.

### Administración de aplicaciones
- **Controles de administración de aplicaciones móviles (MAM) para evitar la sincronización de contactos de Outlook (iOS).** Hay una nueva opción de configuración disponible para la administración de aplicaciones móviles sin inscripción de dispositivos. Esta opción permite evitar que una aplicación sincronice contactos con la libreta de direcciones nativa en dispositivos iOS. Si esta opción está habilitada, la aplicación ya no podrá guardar contactos en la libreta de direcciones nativa. Si esta opción está deshabilitada, la aplicación podrá guardar contactos en la libreta de direcciones nativa. Al borrar el contenido de un dispositivo de forma selectiva, se quitarán todos los contactos que ya se hayan guardado en la libreta de direcciones nativa. Esta nueva opción es compatible con la aplicación Outlook en dispositivos iOS. Para obtener más detalles sobre esta opción y otras, vea [Crear e implementar directivas MAM](https://technet.microsoft.com/en-us/library/dn292747.aspx).

### Control de acceso
- **Skype Empresarial Online admite el acceso condicional.** Puede definir una directiva de acceso condicional para Skype Empresarial Online de modo que solo se pueda acceder a él mediante dispositivos administrados y compatibles con iOS y Android. A los usuarios finales que intenten iniciar sesión en la aplicación móvil de Skype Empresarial en iOS y Android se les pedirá que se inscriban en Intune y que corrijan los problemas de cumplimiento para poder iniciar sesión. Para obtener detalles, vea [Manage access to Skype for Business Online (Administrar el acceso a Skype Empresarial Online)](https://technet.microsoft.com/en-us/library/mt695297.aspx).

### Administración de dispositivos
- **Soporte técnico de Intune para iOS 9.3.** El lunes 21 de marzo, Apple anunció que iOS 9.3 ya estaba disponible. Hemos estado trabajando sin descanso para garantizar que Microsoft Intune sea compatible con la versión más reciente del sistema operativo para móviles de Apple y [nos complace anunciar que Intune permite la administración de dispositivos con iOS 9.3](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/).

  Todas las características existentes de Intune actualmente disponibles para administrar dispositivos iOS seguirán funcionando sin problemas cuando los usuarios actualicen sus dispositivos a iOS 9.3. Además, iOS 9.3 también es compatible en este momento con los clientes híbridos (Configuration Manager integrado con Intune).

- **La directiva de configuración general de Windows 10 ahora contiene opciones de configuración para administrar Windows Defender en equipos con Windows 10 inscritos.** Para obtener detalles, vea [Windows 10 configuration policy settings in Microsoft Intune (Configuración de directivas de configuración de Windows 10 en Microsoft Intune)](https://technet.microsoft.com/en-us/library/mt404697.aspx).


### Portal de empresa

- **Paquetes de aplicaciones de Windows disponibles directamente desde el sitio web del Portal de empresa.** Los usuarios de equipos con Windows 8, Windows 8.1 y Windows RT ya pueden instalar paquetes de aplicaciones de Windows (con la extensión .appx) directamente desde el sitio web del Portal de empresa. Anteriormente, tenía que implementar (o los usuarios tenían que instalar) la aplicación Portal de empresa en sus dispositivos para instalar aplicaciones.

- **Los usuarios pueden bloquear de forma remota su dispositivo desde el sitio web del Portal de empresa.** Se ha agregado una nueva opción de bloqueo remoto al sitio web del Portal de empresa para permitir que los usuarios bloqueen de forma remota su dispositivo desde el Portal en caso de pérdida o robo. Consulte las [instrucciones para el usuario final](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock). En la tabla siguiente se muestra la compatibilidad de plataforma con el bloqueo remoto para la versión independiente de Intune y para Intune con Configuration Manager.

|Plataforma | Detalles sobre compatibilidad|
|---------|----------------|
|Android |Compatible.|
|iOS |Compatible.|
|Windows 10 Mobile |Compatible únicamente si el teléfono tiene establecido un código de acceso|
|Windows 10 Escritorio |No compatible|
|Windows Phone 8,1 |Compatible únicamente si el teléfono tiene establecido un código de acceso|
|Windows Phone 8.0 |No compatible|
|PC (Windows 8.0 y anteriores) |No compatible|
|PC (Windows 8.1) |No compatible|

### Novedades a día 10 de marzo de 2016

### Administración de aplicaciones

- **Aprovecharse de la administración "Open-in" de iOS para los dispositivos que están inscritos en una solución de MDM de terceros** Puede usar su proveedor de administración de dispositivos móviles (MDM) de terceros para aprovecharse de la administración "Open-in" de iOS. Puede establecer las restricciones en los ajustes del perfil de configuración e implementar la aplicación con [Administrar la transferencia de datos entre aplicaciones iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

     Este enfoque tiene dos ventajas principales:

     1. Los usuarios deben iniciar sesión con su cuenta profesional antes de obtener acceso a los datos corporativos desde otras aplicaciones u otros servicios en la nube. Esto garantiza que las directivas de administración de aplicaciones móviles (MAM) están en vigor cuando se accede a los datos.

     2. Los perfiles de correo electrónico administrados y otras aplicaciones administradas que se han implementado a través de una solución MDM de terceros pueden compartir archivos y datos con las aplicaciones que tengan directivas de MAM de Intune.

- **Administrar la aplicación de Microsoft Outlook con directivas de MAM para los dispositivos que no están inscritos en Intune** Ahora puede administrar la aplicación Microsoft Outlook en dispositivos que no estén inscritos en Intune con la directiva de administración de aplicaciones móviles de Intune. La aplicación Microsoft Outlook actualizada con las funcionalidades MAM está disponible para dispositivos [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) y [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook). Siga las instrucciones del tema [Crear e implementar directivas de administración de aplicaciones móviles](https://technet.microsoft.com/library/mt627829.aspx) para crear una directiva MAM.  


- **Las directivas de configuración de aplicaciones móviles le proporcionan más flexibilidad para especificar los detalles de usuario en las aplicaciones iOS** Puede proporcionar la configuración de usuario que una aplicación iOS necesite al abrirse. Por ejemplo, puede proporcionar un puerto de red o un nombre de usuario. Para obtener más información, vea [Configurar aplicaciones de iOS con directivas de configuración de aplicaciones móviles en Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).


- **Implementar Adobe Reader para Microsoft Intune para los dispositivos iOS administrados por Intune en su empresa** La aplicación de Adobe Reader para iOS ahora puede administrarse en los dispositivos inscritos con la directiva de administración de la aplicación móvil de Intune.

- **Garantizar que las imágenes de web que se han implementado están abiertas en el explorador administrado** Puede implementar imágenes de web de destino que solo se pueden abrir con el explorador administrado en dispositivos iOS y Android. Por ejemplo, puede implementar vínculos a recursos corporativos a través del Portal de empresa y, cuando los usuarios naveguen a los vínculos, se abrirán directamente en el explorador administrado donde se pueden proteger mediante directivas MAM. Para obtener detalles, vea [Implementación de aplicaciones](deploy-apps.md).


- **Encontrar, administrar y distribuir las aplicaciones Tienda Windows para empresas para dispositivos Windows 10 desde la consola de administrador de Intune** El soporte técnico para la Tienda Windows para empresas está disponible en Intune para ayudarle a encontrar, administrar y distribuir aplicaciones en los dispositivos Windows 10 que está administrando. La Tienda Windows para empresas permite administrar el proceso de implementación y supervisión de estas aplicaciones desde la consola de administrador de Intune (la misma consola que se utiliza para administrar el resto de aplicaciones). En concreto, la Tienda Windows para empresas administra el contenido y las licencias de las "aplicaciones con licencia en línea". Para obtener detalles, vea [Administrar las aplicaciones adquiridas a través de la Tienda Windows para empresas con Microsoft Intune](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).


### Administración de dispositivos
- **Distribución de certificados PFX para dispositivos iOS** Los administradores de Intune pueden crear e implementar certificados PFX de iOS para la autenticación de VPN, correo electrónico y Wi-Fi en dispositivos iOS. Esta característica ya está disponible para los dispositivos Android y Windows 10. Para obtener detalles, vea [Enable access to company resources using certificate profiles (Habilitar el acceso a los recursos de empresa mediante perfiles de certificados)](secure-resource-access-with-certificate-profiles.md).


- **Aplicar aplicaciones y directivas a los diferentes grupos de dispositivos basándose en la selección de la categoría de usuario** Los administradores de Intune ahora pueden definir las categorías de dispositivos personalizadas para que los usuarios las seleccionen durante la inscripción. Por ejemplo, los administradores pueden querer que los usuarios especifiquen si están inscribiendo un dispositivo utilizado para la "Caja registradora", el "Camión de reparto" o el "Almacén de productos". La categoría seleccionada hará que el dispositivo se convierta en miembro de un grupo de dispositivos de Intune, que puede utilizarse para implementar diferentes aplicaciones y directivas en el dispositivo inscrito. Para obtener detalles, vea [Clasificar los dispositivos con la asignación de grupos de dispositivos en Microsoft Intune](categorize-devices-with-device-group-mapping-in-microsoft-intune.md).

### Cambios y actualizaciones del Portal de empresa de Microsoft
Los siguientes cambios se realizaron en el Portal de empresa en esta versión.

**Aplicación Portal de empresa de Android**

* Cuando los usuarios inicien una aplicación administrada mediante la administración de aplicaciones móviles (MAM), verán un mensaje que les informa de que su empresa administra la aplicación. Ahora, los usuarios podrán pulsar un vínculo de "Más información" para obtener [más información](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) sobre lo que significa "aplicaciones administradas". También puede pulsar "No volver a mostrar" para que el mensaje deje de aparecer al iniciar la aplicación.
* Se han agregado nuevas pantallas para guiar a los usuarios a través del proceso de inscripción y ofrecer más información sobre por qué deberían inscribirse los usuarios, y lo que los administradores de TI pueden y no pueden ver sobre los dispositivos inscritos. Consulte las [instrucciones de inscripción](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) para obtener detalles.
* Los mensajes de error de inscripción ahora se muestran ahora en la aplicación Portal de empresa. Anteriormente, estos mensajes aparecían en el sitio web del Portal de empresa. Al realizar el cambio, todos los mensajes de error aparecerán ahora en un solo sitio, en lugar de en dos sitios distintos.


**Aplicación Portal de empresa de iOS**
* Cuando los usuarios inicien una aplicación administrada mediante la administración de aplicaciones móviles (MAM), verán un mensaje que les informa de que su empresa administra la aplicación. Ahora, los usuarios podrán pulsar un vínculo de "Más información" para obtener [más información](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) sobre lo que significa "aplicaciones administradas". También puede pulsar "No volver a mostrar" para que el mensaje deje de aparecer al iniciar la aplicación.
* Se han agregado nuevas pantallas para guiar a los usuarios a través del proceso de inscripción y ofrecer más información sobre por qué deberían inscribirse los usuarios, y lo que los administradores de TI pueden y no pueden ver sobre los dispositivos inscritos. Consulte las [instrucciones de inscripción](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) para obtener detalles.
* Los mensajes de error de inscripción ahora se muestran ahora en la aplicación Portal de empresa. Anteriormente, estos mensajes aparecían en el sitio web del Portal de empresa. Al realizar el cambio, todos los mensajes de error aparecerán ahora en un solo sitio, en lugar de en dos sitios distintos.




## Febrero de 2016
### Cambios y actualizaciones del Portal de empresa de Microsoft

Los siguientes cambios se realizaron en el Portal de empresa en esta versión.

#### Aplicación Portal de empresa de Android
- Se han agregado nuevas pantallas para guiar a los usuarios a través del proceso de inscripción y ofrecer más información sobre por qué deberían inscribirse los usuarios, y lo que los administradores de TI pueden y no pueden ver sobre los dispositivos inscritos. Consulte las [instrucciones de inscripción](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) para obtener detalles.
- Los mensajes de error de inscripción ahora se muestran ahora en la aplicación Portal de empresa. Anteriormente, estos mensajes aparecían en el sitio web del Portal de empresa. Al realizar el cambio, todos los mensajes de error aparecerán ahora en un solo sitio, en lugar de en dos sitios distintos.

#### Aplicación Portal de empresa de iOS
 - Se han agregado nuevas pantallas para guiar a los usuarios a través del proceso de inscripción y ofrecer más información sobre por qué deberían inscribirse los usuarios, y lo que los administradores de TI pueden y no pueden ver sobre los dispositivos inscritos. Consulte las [instrucciones de inscripción](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) para obtener detalles.

 - Los mensajes de error de inscripción ahora se muestran ahora en la aplicación Portal de empresa. Anteriormente, estos mensajes aparecían en el sitio web del Portal de empresa. Al realizar el cambio, todos los mensajes de error aparecerán ahora en un solo sitio, en lugar de en dos sitios distintos.


## Enero de 2016

### Aprovechar las características de Windows 10
* **Acceso condicional con el servicio de atestación de estado local** Los administradores de Intune ahora pueden ver el estado de la atestación de estado de los dispositivos de Windows 10 en la consola de administración de Intune. La atestación de estado del dispositivo permite al administrador garantizar que los equipos cliente tienen configuraciones BIOS, TPM y de arranque de software de confianza. Para admitir la atestación de estado de los dispositivos, los dispositivos cliente deben ejecutar Windows 10 con TPM 2 habilitado. La atestación de estado del dispositivo muestra el número de dispositivos habilitados para cada una de las siguientes acciones:
    * Antimalware de inicio temprano
    * BitLocker
    * Arranque seguro
    * Integridad de código

    Lea [Introduction to device compliance policies for Microsoft Intune ](introduction-to-device-compliance-policies-in-microsoft-intune.md) (Introducción a las directivas de cumplimiento de dispositivos para Microsoft Intune) para obtener detalles sobre la configuración de estado de los dispositivos, los puntos de datos recopilados y el informe de certificación de estado. En los [detalles del servicio HAS](https://msdn.microsoft.com/en-us/library/dn934876.aspx) se explica el servicio en profundidad.

* **Administración de certificados y directiva de Windows 10 Passport for Work** Con Intune, es posible la [integración con Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), que es un método alternativo de inicio de sesión para Windows 10 que usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual. Passport permite usar un gesto de usuario para iniciar sesión, en lugar de una contraseña. Un gesto de usuario podría ser una autenticación biométrica de PIN simple, como Windows Hello, o un dispositivo externo como un lector de huellas digitales.

* **VPN para aplicaciones específicas** Puede seleccionar aplicaciones que se conecten automáticamente a la red corporativa a través de VPN. Cree la lista de aplicaciones al configurar el perfil de VPN, como se describe en Ayudar a los usuarios a conectarse a su trabajo con perfiles de VPN con Microsoft Intune.

* **Soporte técnico de Windows 10 Full Wipe** Ahora puede emitir un borrado completo remoto de los dispositivos de escritorio de Windows 10 inscritos en Intune a través de la consola de administración de Intune. El borrado completo de Windows 10 realiza un restablecimiento de fábrica del dispositivo.


### Actualización del Programa de Compras por Volumen (PCV) de Apple
Intune puede ayudarle a [administrar aplicaciones adquiridas a través del Programa de compras por volumen (PCV) para empresas de Apple](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md). Esto incluye la sincronización de la información de licencias entre Apple e Intune, y el seguimiento del número de copias de cada aplicación que haya implementado.

### Utilice números IMEI para identificar los dispositivos corporativos
Ahora puede [importar los números de identidad internacional de equipo móvil (IMEI)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) de las plataformas de dispositivos móviles que tengan un número IMEI para ayudar a identificar los dispositivos móviles corporativos. Cuando se inscriben en Intune, los dispositivos con números IMEI importados se etiquetan como corporativos, que se puede utilizar para aplicar las directivas que son diferentes a las que se aplican a dispositivos personales.

### Ahora, hay más aplicaciones compatibles con las directivas MAM de Intune
Ahora, un mayor número de aplicaciones de socios de Microsoft son compatibles con directivas de administración de aplicaciones móviles (MAM) de Intune (para dispositivos administrados por Intune):
* Box for EMM (de Box Inc), solo iOS.
* Adobe Reader (de Adobe), solo Android.
* Foxit PDF Reader (de Foxit Corporation), iOS y Android.


### Finalización de la compatibilidad con IE9 en enero
A partir de febrero de 2016, Internet Explorer 9 dejará de admitirse como explorador oficial para obtener acceso al sitio web del Portal de empresa de Microsoft Intune, el portal de cuentas de Intune y la consola de administración de Intune. Debe migrar a Internet Explorer 10 o posterior.

## Diciembre de 2015
### Cambios y actualizaciones del Portal de empresa de Microsoft
Los siguientes cambios se realizaron en el Portal de empresa en esta versión.

**Aplicación Portal de empresa de Android**

Los siguientes cambios se realizaron para cumplir con los nuevos requisitos de Google. En dispositivos con Android 6.0 y versiones posteriores, se muestran dos nuevos mensajes a los usuarios:
* ¿Permitir que Portal de empresa realice y administre llamadas telefónicas?
* ¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?

Consulte la tabla siguiente para conocer los detalles sobre estos dos mensajes.



Texto del mensaje  |¿Permitir que Portal de empresa realice y administre llamadas telefónicas?  
---------|---------
Significado del mensaje     |  Permite que el número de teléfono y el IMEI del dispositivo del usuario se envíen al servicio Intune y que aparezcan en la consola de administración de la página de hardware.   </br></br>**NOTA: La aplicación Portal de empresa nunca hace ni administra llamadas telefónicas.** Google controla el texto del mensaje y no se puede cambiar. </br></br>Para ver la página **Hardware**, vaya a **Grupos** > **Todos los dispositivos móviles** > **Dispositivos**. Seleccione el dispositivo del usuario y vaya a **Ver propiedades** > **Hardware**.    
Cuándo y dónde aparece el mensaje  | El mensaje aparece cuando los usuarios inician sesión en la aplicación Portal de empresa por primera vez para inscribir su dispositivo.|         
Qué sucede si los usuarios permiten el acceso  |  El número de teléfono y el IMEI del dispositivo aparecerán en la página de hardware de la consola de administración. |         
Qué sucede si los usuarios deniegan el acceso     | Podrán seguir usando la aplicación Portal de empresa e inscribir sus dispositivos, pero el número de teléfono y el IMEI de los dispositivos de los usuarios aparecerán en blanco en la página de hardware de la consola de administración.       </br></br> La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla **No volver a preguntar** que los usuarios pueden seleccionar para que el mensaje no se vuelva a mostrar.</br></br>Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparece la próxima vez que los usuarios inicien sesión en la aplicación Portal de empresa después de la inscripción.</br></br>Si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración**  >  **Aplicaciones**  >  **Portal de empresa**  >  **Permisos**  >  **Teléfono** y activar el permiso.
Más información     |  Para los usuarios: [Iniciar sesión en el Portal de empresa](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp).  </br></br>Para los profesionales de TI: La información de esta tabla también está disponible en [Qué decirles a los usuarios finales sobre el uso de Microsoft Intune](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs).   

Texto del mensaje  |¿Permitir que Portal de empresa tenga acceso a fotos, elementos multimedia y archivos del dispositivo?  
---------|---------
Significado del mensaje     |  Habilita el dispositivo para escribir registros de datos en la tarjeta SD del dispositivo, que permite mover los registros con un cable USB.   </br></br>**NOTA: La aplicación Portal de empresa nunca accede a las fotos, a los elementos multimedia ni a los archivos de los usuarios.** Google controla el texto del mensaje y no se puede cambiar.     
Cuándo y dónde aparece el mensaje  | El mensaje aparece cuando los usuarios pulsan en **Enviar datos** para enviar registros de datos a su administrador de TI.|         
Qué sucede si los usuarios permiten el acceso  |  Los registros se copiarán en la tarjeta SD. |         
Qué sucede si los usuarios deniegan el acceso     | Aun así pueden enviar registros de datos, pero los registros no se copiarán en la tarjeta SD del dispositivo.       </br></br> La segunda vez que los usuarios inician sesión en la aplicación Portal de empresa después de denegar el acceso, el mensaje muestra una casilla **No volver a preguntar** que los usuarios pueden seleccionar para que el mensaje no se vuelva a mostrar.</br></br>Si los usuarios permiten el acceso, pero luego lo deniegan, el mensaje aparece la próxima vez que los usuarios intenten enviar registros.</br></br>Si los usuarios más adelante deciden permitir el acceso, pueden ir a **Configuración**  >  **Aplicaciones**  >  **Portal de empresa**  >  **Permisos**  >  **Almacenamiento** y activar el permiso.
Más información     |  Para los usuarios: [Enviar los registros de datos de diagnóstico al administrador de TI mediante correo electrónico](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs).  </br></br>Para los profesionales de TI: La información de esta tabla también está disponible en [Qué decirles a los usuarios finales sobre el uso de Microsoft Intune](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs).   


**Aplicación Portal de empresa de iOS**
* Los usuarios ahora pueden usar Microsoft Outlook u otras aplicaciones de correo electrónico para enviar registros de diagnóstico al administrador de TI. Anteriormente, se puede usar solo la aplicación nativa.
* Se mejoró la compatibilidad para dispositivos de empresa y el programa de inscripción de dispositivos (DEP) de Apple. Para conocer más detalles, consulte [Usar un dispositivo iOS con Intune](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device).
* En la lista de dispositivos inscritos del usuario, aparece una marca de verificación verde junto al dispositivo que está usando actualmente el usuario. Antes de que se añadiera esta marca de verificación, los usuarios no podrían saber qué dispositivo inscrito estaban usando.

**Aplicación Portal de empresa de Windows**

Microsoft recopila automáticamente datos anónimos sobre el rendimiento y el uso del portal de empresa para mejorar sus productos y servicios. Los usuarios finales pueden desactivar la recopilación de datos mediante la opción Datos de uso en su dispositivo, pero los administradores no tienen ningún control sobre la recopilación de datos y no pueden cambiar la configuración que el usuario final seleccione.



## Noviembre de 2015
### Administración de aplicaciones
Intune admite directivas de administración de aplicaciones móviles (MAM) que ayudan a evitar que los datos corporativos se filtren a las aplicaciones o los servicios de los consumidores. Históricamente, estas directivas solo se aplicarían en aplicaciones móviles que se ejecuten en dispositivos que también se inscribieron para la administración de dispositivos móviles (MDM) en Intune.

Con la actualización de este mes, Intune está ampliando sus funcionalidades MAM a nuevas clases de dispositivos. Además de los dispositivos inscritos en Intune, ahora puede aplicar directivas MAM en:
* dispositivos administrados por alguna otra solución de administración de dispositivos móviles (MDM);
* dispositivos que no estén inscritos en ningún sistema de administración de dispositivos, normalmente dispositivos bring your own device (BYO).

Puede encontrar más información sobre estas nuevas funcionalidades MAM en las siguientes entradas de blog:
* [Mejorar la productividad móvil administrada](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [Anuncio de nuevas funcionalidades de movilidad empresarial de Microsoft](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

Además, a continuación se muestran algunos aspectos destacados e información adicional sobre las características MAM de Intune:
* Los datos corporativos se aíslan de los datos del consumidor en las aplicaciones habilitadas para Intune, incluidas las aplicaciones de Office Mobile, las aplicaciones de terceros que han adoptado el SDK de Intune o las aplicaciones de línea de negocio encapsuladas por Intune.
* Los datos de la empresa se pueden compartir (**cortar, copiar y pegar**) entre las aplicaciones de empresa, a la vez que se evita el uso compartido de datos de empresa en aplicaciones personales. Lea [Cómo protegen las directivas MAM los datos de las aplicaciones](https://technet.microsoft.com/library/mt627825.aspx) para conocer más detalles. Este escenario de ejemplo, [Experiencia del usuario final para aplicaciones asociadas con directivas de administración de aplicaciones móviles de Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx), se muestra cómo se evita el uso compartido de los datos de empresa en aplicaciones personales.
* Directivas de prevención de pérdida de datos clave como PIN por aplicación, controles guardar como y uso compartido de datos administrados entre aplicaciones. Lea [Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx) para ver una lista con todas las directivas.
* Word, Excel, PowerPoint, Outlook, OneNote y OneDrive para la Empresa tienen estas nuevas funcionalidades y se pueden administrar con y sin inscripción de dispositivos. Las funcionalidades de protección de pérdida de datos están integradas de forma nativa en las aplicaciones de Office estándares de Apple Store o Google Play Store, y no requieren instalación de prueba ni ajuste de la aplicación.
* Para conocer los primeros pasos, consulte [Introducción a las directivas de administración de aplicaciones móviles en el portal de Azure](https://technet.microsoft.com/library/mt627830.aspx). Para conocer cómo configurar e implementar directivas de administración de aplicaciones móviles, consulte [Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx).
* Cuando los usuarios finales se autentican en la aplicación con sus credenciales corporativas, las funcionalidades de protección de la pérdida de datos se configuran automáticamente. El tema [Experiencia del usuario final para aplicaciones asociadas con directivas de administración de aplicaciones móviles de Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx) tiene algunos escenarios de ejemplo para acceder a OneDrive en dispositivos iOS y Android.
* Funciona en dispositivos iOS y Android.

La lista de [Aplicaciones de Microsoft que puede utilizar con las directivas de administración de aplicaciones móviles de Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx) se ha actualizado para se muestren las aplicaciones más recientes.

### Administración de dispositivos
 **Administración de dispositivos Mac OS X** Con Intune, ahora puede inscribir y administrar dispositivos Mac OS X. Puede hacer lo siguiente con los dispositivos Mac OS X:
* Inscribir dispositivos para que los administre Intune. Consulte [Configurar la administración de iOS con Microsoft Intune](https://technet.microsoft.com/library/dn408185.aspx).
* Controlar la configuración de dispositivo mediante una directiva de configuración general. Consulte [Configuración de directivas de configuración de Mac OS X en Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx).
* Implementar la configuración de Mac OS X que ha creado con Apple Configurator. Consulte [Configuración de directivas personalizadas de Mac OS X en Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx).
* Recopilar el inventario de hardware y de software de los dispositivos Mac OS X. Consulte [Comprender el funcionamiento de sus dispositivos mediante el inventario en Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx).
* Ejecutar nuevos informes donde se muestren los detalles sobre los dispositivos de Mac OS X que administre. Consulte [Comprender las operaciones de Microsoft Intune mediante informes](https://technet.microsoft.com/library/dn646977.aspx).

**Nueva configuración del explorador Edge para dispositivos de Windows 10** Se ha agregado una nueva configuración a la directiva de configuración general de Windows 10 que permite administrar la configuración y las características del explorador Microsoft Edge. Consulte [Configuración de directivas de configuración de Windows 10 en Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx).

**Perfiles de correo electrónico** Se ha agregado una nueva directiva de perfiles de correo electrónico a los dispositivos de escritorio de Windows 10 y móviles de Windows 10. Consulte [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](https://technet.microsoft.com/library/dn646984.aspx).

**Nueva configuración de directivas de cumplimiento** La nueva configuración de directivas de sistema y seguridad siguiente se ha agregado a la lista de directivas de cumplimiento:
* Para asegurarse de que los dispositivos con Windows 8.1 o versiones posteriores que acceden a los recursos de empresa tengan instaladas las actualizaciones más recientes, use la configuración **Requerir actualizaciones automáticas**. También puede especificar el tipo de actualizaciones que se instalarán automáticamente: todas las actualizaciones marcadas como importantes o todas las marcadas como importantes o recomendadas. Para obtener la lista completa de configuraciones de directivas de cumplimiento, consulte [Administrar directivas de cumplimiento del dispositivo de Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx).
* La nueva configuración **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad** combinada con la configuración existente **Minutos de inactividad antes de que sea necesaria la contraseña** permite crear una configuración de cumplimiento que requiera que el usuario final escriba una contraseña para utilizar un dispositivo que ha estado inactivo durante un tiempo determinado.

**Nuevas opciones de directivas de acceso condicional** Puede aplicar directivas de acceso condicional a **todos los usuarios** en directivas de acceso condicional nuevas o existentes. Todos los usuarios con licencia para Intune y Office 365 deberán inscribir sus dispositivos y, si la plataforma de dispositivo no es compatible con Intune, el acceso se bloqueará para las aplicaciones de cliente que usen [inicio de sesión basado en la autenticación de Active Directory (autenticación moderna)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/).

También puede especificar que la directiva de acceso condicional se aplique a **todas las plataformas**.  Cualquier aplicación cliente que use el [inicio de sesión basado en la autenticación de Active Directory (autenticación moderna)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) está sujeta a la directiva de acceso condicional y, si la plataforma no es compatible con Intune, se bloqueará.

### Cambios y actualizaciones del Portal de empresa de Microsoft
Los siguientes cambios se realizaron en las aplicaciones de portal de empresa en esta versión:

* **Android**: una pantalla de inicio de sesión se ha agregado a la aplicación Portal de empresa de Android para ayudar a los usuarios a entender el propósito de la aplicación Portal de empresa. Esta pantalla está diseñada para reducir las descargas de la aplicación por parte de los usuarios cuyas empresas no son suscriptores de Intune.

* **iOS**: Intune ahora admite la inscripción de dispositivos Mac OS X mediante el [sitio web del Portal de empresa](https://portal.manage.microsoft.com). Para obtener instrucciones, consulte [Usar un dispositivo iOS con Intune](https://technet.microsoft.com/library/mt598622.aspx).

* **Sitio web del Portal de empresa**: Los usuarios que inscribieron su dispositivo en Intune ahora pueden restablecer su código de acceso mediante la opción **Restablecer código de acceso** del sitio web del Portal de empresa. Anteriormente, solo los administradores de TI podían restablecer los códigos de acceso de los usuarios. La opción Restablecer código de acceso no se admite en dispositivos Windows 8.1 y Windows RT, y la opción solo aparece cuando se inscriben los dispositivos en administración de dispositivos móviles (MDM) o en MDM con Exchange ActiveSync. Para obtener instrucciones de usuario, consulte [Restablecer el código de acceso](https://technet.microsoft.com/library/mt590895.aspx).

### Cambios en las licencias de administradores globales
En octubre, publicamos que los administradores globales (también denominados administradores de inquilinos) podrían seguir realizando tareas de administración cotidianas sin una licencia independiente de Intune o Enterprise Mobility Suite (EMS). Sin embargo, si los administradores globales quieren usar el servicio, por ejemplo para inscribir sus dispositivos, un dispositivo de la empresa o para usar el Portal de empresa de Intune, necesitarán una licencia de Intune o EMS igual que cualquier otro usuario. A continuación se muestran algunos detalles adicionales.
* El Portal de empresa de Intune es donde los usuarios finales pueden:
    * inscribir su dispositivo;
    * ver el estado de su dispositivo;
    * descargar el software que un administrador global ha implementado para la organización;
    * encontrar vínculos publicados por el administrador global sobre cómo ponerse en contacto con su departamento de TI.

    [Obtenga información sobre el Portal de empresa](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal) y sobre las distintas [maneras de personalizar el Portal de empresa](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal).
* La persona que se registre para comprar Intune o EMS en nombre de una organización se convierte automáticamente en el primer administrador global de su inquilino. Este otoño, Intune comenzó a asignar automáticamente una licencia Intune o EMS a ese primer administrador global como parte de la transición al [Portal de Office 365](http://portal.office.com/) y la retirada del [Portal de cuentas de Intune](http://account.manage.microsoft.com/). Los administradores globales adicionales que se hayan agregado pueden seguir con la administración diaria sin una licencia independiente de Intune o EMS. Si se actúa como un usuario final e inscribe su dispositivo propio (o corporativo) o descarga software del Portal de empresa, se provocaría la necesidad de una licencia, como cualquier otro usuario.
* El cambio se introducirá progresivamente y comenzará en enero de 2016.
* Para los partners de Microsoft, este cambio no debería afectar a su capacidad para administrar el servicio en nombre de los clientes. Para los usuarios finales, un usuario deberá tener una licencia de Intune o EMS para inscribir un dispositivo y acceder o descargar software desde el Portal de empresa.

Si tiene alguna pregunta sobre este cambio, no dude en ponerse en contacto con el equipo de soporte técnico de Intune:
* [Canales de soporte técnico de Microsoft Intune](https://technet.microsoft.com/library/jj839713.aspx)
* [Soporte técnico de la Comunidad](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

Hay comentarios generales sobre Microsoft Intune, incluidos el envío de solicitudes de cambios de diseño (DCR) o errores, en la página de [Intune user voice](https://microsoftintune.uservoice.com/).


### Novedades de la documentación de Intune: noviembre de 2015
**Contenido nuevo**
* [Configuración de directivas de configuración de Mac OS X en Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx): cómo controlar la configuración de dispositivo y las características de dispositivos Mac OS X.
* [Configuración de directivas personalizadas de Mac OS X en Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx): cómo implementar configuraciones de dispositivos Mac OS X que creó mediante la herramienta Apple Configurator.
* [Configurar directivas de aplicaciones de prevención de pérdida de datos con Microsoft Intune](https://technet.microsoft.com/library/mt627825.aspx): contiene información sobre los escenarios que admiten las directivas de administración de aplicaciones móviles y cómo funciona la directiva a fin de proteger los datos.
* [Introducción a las directivas de administración de aplicaciones móviles en el portal de Azure](https://technet.microsoft.com/library/mt627830.aspx): lo que necesita para empezar a usar el Portal de vista previa de Azure para las directivas de administración de aplicaciones móviles.
* [Crear e implementar directivas de administración de aplicaciones móviles con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx): contiene un tutorial paso a paso donde se explica cómo crear directivas de administración de aplicaciones móviles en el Portal de vista previa de Azure.
* [Supervisión de directivas de administración de aplicaciones móviles con Microsoft Intune](https://technet.microsoft.com/library/mt627824.aspx): se incluye información sobre cómo puede supervisar las directivas de administración de aplicaciones móviles mediante el Portal de vista previa de Azure.
* [Directivas de administración de aplicaciones móviles de Microsoft Intune y característica Open In de iOS](https://technet.microsoft.com/library/mt627821.aspx): información sobre cómo funcionan las directivas de administración de aplicaciones móviles con la característica Open In de iOS.
* [Experiencia del usuario final para aplicaciones asociadas con directivas de administración de aplicaciones móviles de Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx): se describe la experiencia del usuario final cuando se usan aplicaciones asociadas con directivas de administración de aplicaciones móviles.
* [Borrar los datos administrados de la aplicación de la empresa con Microsoft Intune](https://technet.microsoft.com/library/mt627826.aspx): cómo se pueden quitar datos de la aplicación de empresa.

**Contenido actualizado**
* [Configuración de directivas de configuración de Windows 10 en Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx): se han agregado nuevas características del explorador Edge.
* [Configurar la administración de iOS con Microsoft Intune](http://technet.microsoft.com/library/dn408185.aspx): se ha agregado información sobre cómo inscribir dispositivos Mac OS X.
* [Supervisar dispositivos móviles con Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx): se ha agregado información sobre el inventario recopilado a partir de dispositivos Mac OS X. Además, se ha actualizado el tema con la información más reciente de todas las plataformas de dispositivo.
* [Comprender las operaciones de Microsoft Intune mediante informes](https://technet.microsoft.com/library/dn646977.aspx): se ha agregado información sobre los dos nuevos informes que se usan para mostrar información sobre los dispositivos de Mac OS X administrados.
* [Administrar directivas de cumplimiento del dispositivo de Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx): se ha agregado información sobre las nuevas directivas de cumplimiento para requerir actualizaciones automáticas y el requisito de contraseña cuando un dispositivo vuelve de estado de inactividad.
* [Administrar acceso al correo electrónico con Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx): se ha agregado información sobre la capacidad de aplicar la directiva de acceso condicional a todos los usuarios y plataformas.
* [Administrar el acceso a SharePoint Online con Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx): se ha agregado información sobre la capacidad de aplicar la directiva de acceso condicional a todos los usuarios y plataformas.

## Octubre de 2015

### Actualizaciones para el acceso condicional de Exchange local
**Ahora puede permitir el acceso al correo electrónico de Exchange Active Sync para dispositivos compatibles inscritos en Intune cuando la regla de Exchange global está establecida en bloquear o poner en cuarentena** Hasta ahora, para permitir el acceso al correo electrónico en dispositivos inscritos y compatibles, era necesario establecer la regla de Exchange global predeterminada en **Permitir**.

Con esta actualización de servicio, esta configuración ya no es un requisito necesario para el acceso condicional. Si su entorno de Exchange requiere que la regla global predeterminada se establezca en **Bloqueo/cuarentena**, solo debe marcar la casilla **Invalidación de la regla predeterminada** en la página de directivas de acceso condicional de Exchange local. En el tema [Administrar acceso al correo electrónico con Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) se incluyen más detalles sobre las reglas y las notificaciones del usuario final resultantes.

**Nueva experiencia de cuarentena de un clic** Se ha simplificado la experiencia de cuarentena del correo electrónico para que pueda realizar la inscripción con un solo clic. Con esta actualización de servicio, los usuarios finales pueden hacer clic en un solo vínculo del correo electrónico de cuarentena para completar el proceso de inscripción dentro de la aplicación Portal de empresa.
### Actualizaciones de administración de dispositivos y aplicaciones móviles
**Android** Todas las características de administración de Intune ahora admiten Android 6.0 (Marshmallow) tal y como se describe en esta entrada de blog: [Microsoft Intune Provides Day 0 Support for Android Marshmallow](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx) (Microsoft Intune ofrece compatibilidad de día 0 para Android Marshmallow).

**iOS** Ya no podrá crear nuevas implementaciones de aplicaciones para dispositivos que ejecuten versiones anteriores a iOS 7.1. Cualquier implementación de aplicaciones que se realice en dispositivos que ejecuten una versión anterior a iOS 7.1, seguirá funcionando e Intune se encargará de administrarlas.

**Windows 10** Intune ahora admite la implementación de aplicaciones universales de Windows 10 mediante el tipo de instalador de software de **paquete de aplicaciones de Windows**. Para conocer los detalles y requisitos, vea [Get started with app deployment in Microsoft Intune (Introducción a la implementación de aplicaciones en Microsoft Intune)](http://technet.microsoft.com/en-US/library/dn646955.aspx).


### Cambios y actualizaciones para las aplicaciones del Portal de empresa de Microsoft
Los siguientes cambios se han realizado en las aplicaciones de portal de empresa en esta versión: **iOS** Los nuevos botones se han agregado a la aplicación de portal de empresa para facilitar a los usuarios el envío de registros de diagnóstico a sus administradores de TI:

|Nombre del botón|Dónde aparece|
|------------|---------------|
|Informe|Mensajes de alerta de error|
|Enviar informe de diagnóstico|Acerca de la pantalla de la aplicación Portal de empresa|


>[!div class="step-by-step"]

>[&larr; **Novedades de Intune**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Jun16_HO3-->


