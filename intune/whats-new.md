---
title: Novedades de Microsoft Intune (Azure) | Microsoft Docs
titlesuffix: ''
description: Descubra las novedades del portal de Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6d346d7f060b5e997577b09c3ee8b006843ab7b
ms.sourcegitcommit: 8e503c1b350f7b29a045b7daf3eece64be4ca3c4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56302241"
---
# <a name="whats-new-in-microsoft-intune"></a>Novedades de Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Conozca las novedades semanales de Microsoft Intune. También podrá buscar próximos cambios, [notificaciones importantes](#notices) e información sobre [versiones anteriores](whats-new-archive.md). 

> [!Note]
> Algunas características pueden lanzarse a lo largo de varias semanas y pueden no estar disponibles para todos los clientes durante la primera semana.
>
> Para obtener más información sobre la nueva funcionalidad de administración híbrida de dispositivos móviles (MDM), consulte la [página Novedades de MDM híbrida](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

**Fuente RSS**: reciba notificaciones cuando esta página se actualice copiando y pegando la siguiente dirección URL en su lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->     
## <a name="week-of-february-4-2019"></a>Semana del 4 de febrero de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="intune-macos-company-portal-dark-mode----3300524-eeready---"></a>Modo oscuro del Portal de empresa de macOS para Intune <!-- 3300524 eeready -->
El Portal de empresa de macOS para Intune ahora admite el Modo oscuro para macOS. Cuando habilita el Modo oscuro en un dispositivo macOS 10.14 o una versión posterior, el Portal de empresa ajustará su apariencia para que los colores reflejen ese modo.

## <a name="week-of-january-21-2019"></a>Semana del 21 de enero de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notificaciones del sistema para aplicaciones Win32 <!-- 3136566   -->
Puede suprimir notificaciones del sistema para el usuario final por asignación de aplicaciones. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > seleccione la aplicación > **Asignaciones** > **Incluir grupos**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Actualización de la interfaz de usuario de las directivas de protección de aplicaciones de Intune <!-- 3251427  -->
Hemos cambiado las etiquetas para las opciones y los botones de la protección de aplicaciones de Intune para que sean más fáciles de entender. Algunos de los cambios son:  
- Los controles han cambiado de **sí** / **no** a principalmente **bloquear** / **permitir** y **deshabilitar** / **habilitar**. Las etiquetas también se actualizaron.  
- Se cambió el formato de las opciones, de tal forma que la opción y su etiqueta aparezcan una al lado de la otra en el control, para así facilitar la navegación.   

La configuración predeterminada y el número de opciones se conservan, pero este cambio permite al usuario entender, navegar y utilizar la configuración con más facilidad para aplicar las directivas de protección de aplicaciones seleccionadas. Para información, consulte la [configuración para iOS](app-protection-policy-settings-ios.md) y la [configuración para Android](app-protection-policy-settings-android.md).

#### <a name="additional-settings-for-outlook----3301182----"></a>Configuración adicional para Outlook <!-- 3301182  -->
Ahora puede cambiar las siguientes opciones de configuración adicionales para Outlook para iOS y Android mediante Intune:
- Permitir que solo se usen cuentas profesionales o educativas en iOS y Android.
- Implementar la autenticación moderna para Office 365 y la autenticación moderna híbrida para cuentas locales.
- Usar `SAMAccountName` para el campo de nombre de usuario en el perfil de correo electrónico al tener seleccionada la autenticación básica.

Las siguientes opciones de configuración aún se están implantando gradualmente y pronto estarán disponibles en la consola:
- Permitir que se guarden contactos.
- Configurar información sobre el correo electrónico de destinatarios externos.
- Configurar la **Bandeja de entrada Prioritarios**.
- Requerir autenticación biométrica para acceder a Outlook para iOS.

La siguiente configuración aparece en la consola de Intune, pero, si se configura, no funcionará según lo previsto. Este problema se corregirá pronto:
- Bloquear las imágenes externas.

> [!NOTE]
> Si usa directivas de Intune App Protection para administrar el acceso de las identidades corporativas, le recomendamos que no habilite el **requisito de autenticación biométrica**. Para más información, vea **Requerir credenciales corporativas en acceso**, en los artículos relativos a la [configuración de acceso de iOS](app-protection-policy-settings-ios.md#access-requirements) y la [configuración de acceso de Android](app-protection-policy-settings-android.md#access-requirements), respectivamente.

#### <a name="delete-android-enterprise-apps----1352553---"></a>Eliminación de aplicaciones de Android Enterprise <!-- 1352553 -->
Puede eliminar aplicaciones de Google Play administrado desde Microsoft Intune. Para eliminar una aplicación de Google Play administrado, abra Microsoft Intune en Azure Portal y seleccione **Aplicaciones cliente** > **Aplicaciones**. En la lista de aplicaciones, seleccione los puntos suspensivos (...) a la derecha de la aplicación de Google Play administrado y luego seleccione **Eliminar** en la lista que aparece. Cuando se elimina una aplicación de Google Play administrada de la lista de aplicaciones, automáticamente se desactiva la aprobación de la aplicación administrada de Google Play.

#### <a name="managed-google-play-app-type----1352580---"></a>Aplicación administrada de Google Play tipo <!-- 1352580 -->
El tipo de aplicación **administrada de Google Play** le permitirá agregar específicamente [aplicaciones de Google Play administradas](https://play.google.com/work/search?q=microsoft&c=apps) a Intune. Como administrador de Intune, ahora podrá examinar, buscar, aprobar, sincronizar y asignar aplicaciones de Google Play administrado aprobadas dentro de Intune.  Ya no necesita ir a la consola de Google Play administrado por separado ni tiene que volver a autenticarse.  En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. En la lista **Tipo de aplicación**, seleccione **Google Play administrada** como tipo de aplicación.

### <a name="default-android-pin-keyboard----3802457---"></a>Teclado de PIN de Android predeterminado <!-- 3802457 -->
Los usuarios finales que hayan establecido un PIN de directiva de Intune App Protection (APP) en sus dispositivos Android con el tipo de PIN “Numérico” ahora verán el teclado de Android predeterminado en lugar de la interfaz de usuario de teclado de Android que se había diseñado anteriormente. Este cambio se ha llevado a cabo para que sea coherente al usar los teclados predeterminados en Android e iOS, para ambos tipos de PIN “Numérico” o “Código de acceso”. Para obtener más información sobre la configuración de acceso de los usuarios finales en Android, como el PIN de APP, consulte [Requisitos de acceso de Android](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Uso de la configuración recomendada por Microsoft con líneas de base de seguridad (versión preliminar pública) <!-- 2055484   -->

Intune se integra con otros servicios centrados en la seguridad, incluidos ATP de Windows Defender y Office 365 ATP. Los clientes solicitan una estrategia común y un conjunto coherente de flujos de trabajo de seguridad integrales entre los servicios de Microsoft 365. Nuestro objetivo es alinear las estrategias para crear soluciones que actúen de puente entre las operaciones de seguridad y las tareas de administración comunes. En Intune, este objetivo se pretende lograr mediante la publicación de un conjunto de "Líneas de base de seguridad" recomendadas de Microsoft (**Intune** > **Líneas de base de seguridad**).  Un administrador puede crear directivas de seguridad directamente a partir de estas líneas de base y, después, implementarlas en sus usuarios. También puede personalizar los procedimientos recomendados para satisfacer las necesidades de su organización. Intune garantiza que los dispositivos cumplan estas líneas de base y notifica a los administradores los usuarios o dispositivos que no están en cumplimiento.

Esta característica está en versión preliminar pública, por lo que los perfiles creados ahora no se moverán a las plantillas de líneas base de seguridad que están disponibles con carácter general (GA). No debería planear usar estas plantillas de versión preliminar en el entorno de producción.

Para más información sobre las líneas de base de seguridad, vea [Create a Windows 10 security baseline in Intune](security-baselines-monitor.md) (Crear una línea de base de seguridad de Windows 10 en Intune).

Esta característica se aplica a: Windows 10 y versiones posteriores

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Quienes no son administradores pueden habilitar BitLocker en dispositivos Windows 10 unidos a Azure AD<!-- 2147379   -->
Cuando se habilita la configuración de BitLocker en dispositivos Windows 10 (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para la plataforma > **Endpoint Protection** para el tipo de perfil > **Cifrado de Windows**), se agrega la configuración de BitLocker. 

Esta actualización incluye una configuración de BitLocker nueva para permitir que los usuarios estándar (no administradores) habiliten el cifrado. 

Para ver esta configuración, vaya a [Configuración de Windows 10 (y versiones posteriores) para proteger dispositivos mediante Intune](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Comprobar cumplimiento de Configuration Manager <!-- 2192052  eepublished  -->
Esta actualización incluirá una nueva configuración de conformidad de System Center Configuration Manager (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Windows 10 y versiones posteriores** > **Cumplimiento de Configuration Manager**). Configuration Manager envía señales a la conformidad de Intune. Mediante esta configuración, puede exigir que todas las señales de Configuration Manager devuelvan “conforme”.

Por ejemplo, exige que todas las actualizaciones de software se instalen en los dispositivos. En Configuration Manager, este requisito tiene el estado “Instalado”. Si algún programa del dispositivo se encuentra en un estado desconocido, dicho dispositivo no será conforme en Intune.

[Cumplimiento de Configuration Manager](compliance-policy-create-windows.md#configuration-manager-compliance) describe esta configuración.

Se aplica a: Windows 10 y versiones posteriores

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Personalice el papel tapiz en dispositivos iOS supervisados mediante un perfil de configuración de dispositivo <!-- 2809324   -->
Cuando cree un perfil de configuración de dispositivos para dispositivos iOS, podrá personalizar algunas características (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para la plataforma > **Características del dispositivo** para el tipo de perfil). Esta actualización incluye nuevas configuraciones **Fondo de pantalla** que permiten a un administrador usar una imagen .png, .jpg o .jpeg en la pantalla de inicio o en la pantalla de bloqueo. Esta configuración de fondo de pantalla solo se aplica a los dispositivos supervisados. 

Para una lista de esta configuración, consulte [iOS device feature settings](ios-device-features-settings.md) (Configuración de características de dispositivos iOS).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>La pantalla completa de Windows 10 está disponible con carácter general <!-- 3594661  -->
En esta actualización, la característica Pantalla completa en dispositivos con Windows 10 y versiones posteriores está disponible con carácter general (GA). Para ver todas las configuraciones que puede agregar y definir, consulte [Configuración de dispositivos con Windows 10 y versiones posteriores para ejecutarse como una pantalla completa dedicada con Intune](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Se eliminó la opción para compartir contacto a través de Bluetooth en Restricciones del dispositivo > Propietario del dispositivo para Android Enterprise <!-- 3598396   -->
Cuando se crea un perfil de restricciones de dispositivos para dispositivos de Android Enterprise, hay una configuración para **Compartir contacto a través de Bluetooth**. En esta actualización, se elimina la configuración **Compartir contacto a través de Bluetooth** (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **Restricciones de dispositivos > Propietario del dispositivo** para el tipo de perfil > **General**). 

La configuración **Compartir contacto a través de Bluetooth** no es compatible con la administración de Propietario del dispositivo Android Enterprise. Por lo que cuando se quite esta configuración, no afectará a ningún dispositivo ni inquilino, incluso si esta opción está habilitada y configurada en su entorno.

Para ver la lista actual de configuraciones, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características](device-restrictions-android-for-work.md).

Se aplica a: Propietario del dispositivo Android Enterprise

### <a name="device-management"></a>Administración de dispositivos

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Compatibilidad con el borrado selectivo para dispositivos de WIP Without Enrollment <!-- 1434452 -->
Windows Information Protection Without Enrollment (WIP-WE) permite a los clientes proteger sus datos corporativos en dispositivos con Windows 10 sin necesidad de realizar una inscripción de MDM completa. Una vez que los documentos están protegidos con una directiva de WIP-WE, un administrador de Intune puede borrar de forma selectiva los datos protegidos. Mediante la selección del usuario y dispositivo, y el envío de una solicitud de borrado, todos los datos protegidos mediante la directiva de WIP-WE quedarán inservibles. En Intune en Azure Portal, seleccione **Aplicación móvil** > **Borrado selectivo de aplicaciones**.

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Nuevos registros operativos y capacidad para enviar registros a los servicios de Azure Monitor <!-- 3762211  -->
Intune tiene el registro de auditoría integrado que realiza el seguimiento de eventos cuando se realizan cambios. Esta actualización incluye nuevas características de registro, como las siguientes: 
- Registros operativos (versión preliminar) que se muestran detalles sobre los usuarios y dispositivos que se inscribieron, incluidos los intentos correctos y erróneos.
- Los registros de auditoría y los registros operativos también se pueden enviar a Azure Monitor, incluidas las cuentas de almacenamiento, Event Hubs y Log Analytics. Estos servicios permiten almacenar, usar análisis como Splunk y QRadar y obtener visualizaciones de los datos de registro.

En [Send log data to storage, event hubs, or log analytics in Intune](review-logs-using-azure-monitor.md) (Envío de datos de registro al almacenamiento, Event Hubs o Log Analytics en Intune) se proporciona más información sobre esta característica.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Omisión de más pantallas del Asistente de configuración de un dispositivo DEP iOS <!-- 2687509  -->
Además de las pantallas que actualmente se pueden omitir, podrá establecer dispositivos DEP de iOS para omitir las pantallas siguientes en el Asistente para la configuración cuando un usuario inscribe el dispositivo: Tono de pantalla, Privacidad, Migración de Android, botón Inicio, iMessage y FaceTime, Incorporación, Migración de Watch, Apariencia, Tiempo de uso, Actualización de software, Configuración de SIM.
Para elegir qué pantallas omitir, vaya a **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > elija un token > **Perfiles** > elija un perfil > **Propiedades** > **Personalización del Asistente de configuración** > elija **Ocultar** en todas las pantallas que quiera omitir > **Aceptar**.
Si crea un nuevo perfil o edita uno, las pantallas de omisión seleccionadas deben sincronizarse con el servidor MDM de Apple. Los usuarios pueden emitir una sincronización manual de los dispositivos para que no haya ningún retraso en la recogida de los cambios de perfil.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Implementación de aplicaciones APP-WE de Android Enterprise <!-- 1171203 -->
En el caso de los dispositivos Android en un escenario de implementación de directiva de protección de aplicaciones sin inscripción (APP-WE) no inscrito, ahora puede usar Google Play administrado para implementar aplicaciones de la tienda y aplicaciones de LOB en los usuarios. En concreto, puede brindar a los usuarios finales un catálogo de aplicaciones y experiencia de instalación que ya no requiere que los usuarios finales flexibilicen la posición de seguridad de sus dispositivos al permitir instalaciones de orígenes desconocidos. Además, este escenario de implementación proporcionará una mejor experiencia del usuario final.

## <a name="week-of-january-14-2019"></a>Semana del 14 de enero de 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Versión preliminar de la compatibilidad para dispositivos Android totalmente administrados de propiedad corporativa <!-- 1574342  -->
Intune ya admite dispositivos Android totalmente administrados; un escenario de "propietario de dispositivo" de propiedad corporativa en el que el departamento de TI administra de manera rigurosa los dispositivos y estos se asocian a usuarios individuales. Esto permite que los administradores administren todo el dispositivo, apliquen una amplia variedad de controles de directivas no disponibles para los perfiles de trabajo y restrinjan las instalaciones de aplicaciones por parte de los usuarios solo a Google Play administrado. Para obtener más información, vea [Set up Intune enrollment of Android fully managed devices](android-fully-managed-enroll.md) (Configuración de la inscripción en Intune de dispositivos Android totalmente administrados) y [Enroll your dedicated devices or fully managed devices](android-dedicated-devices-fully-managed-enroll.md) (Inscripción de dispositivos dedicados o dispositivos totalmente administrados).  Tenga en cuenta que esta característica está en versión preliminar. Algunas funcionalidades de Intune, como certificados, cumplimiento y acceso condicional, no están disponibles actualmente con dispositivos Android totalmente administrados.

## <a name="week-of-january-7-2019"></a>Semana del 7 de enero de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="intune-app-pin----2298397---"></a>PIN de aplicación de Intune <!-- 2298397 -->
Como administrador de TI, podrá configurar el número de días que un usuario final puede esperar hasta que se tenga que cambiar el PIN de aplicación de Intune. La nueva configuración es *Restablecimiento del PIN después de un número de días* y está disponible en Azure Portal; para acceder a esta configuración, seleccione **Intune** > **Aplicaciones cliente** > **Directivas de protección de aplicaciones** > **Crear directiva** > **Configuración** > **Requisitos de acceso**. Esta característica está disponible para dispositivos [iOS](app-protection-policy-settings-ios.md) y [Android](app-protection-policy-settings-android.md), y admite un valor entero positivo.


#### <a name="intune-device-reporting-fields----2748738---"></a>Campos de informes de dispositivo de Intune <!-- 2748738 -->
Intune proporcionará campos adicionales con información sobre el dispositivo, como el identificador de registro de aplicación, el fabricante de Android, el modelo, la versión de la revisión de seguridad y el modelo de iOS. En Intune, estos campos estarán disponibles en **Aplicaciones cliente** > **Estado de protección de aplicaciones** y **Informe de protección de aplicaciones: iOS, Android**. Además, estos parámetros lo ayudarán a configurar la lista de **admitidos** correspondiente al fabricante de dispositivo (Android), la lista de **admitidos** del modelo de dispositivo (iOS y Android) y la configuración de versión de la revisión de seguridad mínima de Android. 


### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Las plantillas administrativas están en versión preliminar pública y se movieron a su propio perfil de configuración <!-- 3322847 -->

Las plantillas administrativas de Intune (**Configuración del dispositivo** > **Plantillas administrativas**) están actualmente en versión preliminar privada. Con esta actualización:

- Las plantillas administrativas contienen unos 300 valores de configuración que se pueden administrar en Intune. Anteriormente, estas configuraciones solo existían en el editor de directivas de grupo.
- Las plantillas administrativas están disponibles en versión preliminar pública.
- Las plantillas administrativas están disponibles en versión preliminar pública y se han migrado desde **Configuración del dispositivo** > **Plantillas administrativas** a **Configuración del dispositivo** > **Perfiles** > **Crear perfil**. Luego, en **Plataforma**, seleccione **Windows 10 y versiones posteriores**, en **Tipo de perfil**, y haga clic en **Plantillas administrativas**.
- Se han habilitado los informes.

Para obtener más información sobre esta característica, vaya a [Plantillas de Windows 10 para configurar opciones de directiva de grupo](administrative-templates-windows.md).

Se aplica a: Windows 10 y versiones posteriores

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Uso de S/MIME para cifrar y firmar varios dispositivos para un usuario <!-- 1333642 -->
Esta actualización incluye cifrado de correo electrónico S/MIME mediante un nuevo perfil de certificado importado (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > seleccione la plataforma > tipo de perfil **Certificado PKCS importado**). En Intune, puede importar los certificados en formato PFX. Después, Intune puede entregar esos mismos certificados a varios dispositivos inscritos por un solo usuario. Esto también incluye lo siguiente:
- El perfil de correo electrónico de iOS nativo permite habilitar el cifrado S/MIME mediante certificados importados en formato PFX.
- La aplicación de correo nativo de los dispositivos Windows Phone 10 usa automáticamente el certificado S/MIME.
- Los certificados privados se pueden entregar en varias plataformas. Aun así, no todas las aplicaciones de correo electrónico son compatibles con S/MIME.
- En otras plataformas, podría tener que configurar manualmente la aplicación de correo electrónico para habilitar S/MIME.  
- Las aplicaciones de correo electrónico que admiten el cifrado S/MIME pueden controlar la recuperación de certificados para el cifrado de correo electrónico S/MIME de una manera que no es compatible con un servicio MDM, por ejemplo, si los lee desde el almacén de certificados del publicador.
Para obtener más información sobre esta característica, vea [Información general sobre S/MIME para firmar y cifrar correos electrónicos](certificates-s-mime-encryption-sign.md).
Compatible con: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nuevas opciones para conectarse automáticamente y conservar las reglas al usar la configuración DNS en dispositivos Windows 10 y posteriores <!-- 1333665, 2999078 -->
En dispositivos Windows 10 y versiones posteriores, podrá crear un perfil de configuración de VPN que incluya una lista de servidores DNS para resolver dominios, como contoso.com. En esta actualización se incluirá una nueva configuración para la resolución de nombres (**Configuración del dispositivo** > **Perfiles** > **Crear perfil**; seleccione **Windows 10 y versiones posteriores** como la plataforma, **VPN** como el tipo de perfil, y **Configuración DNS** >**Agregar**): 
- **Conectar automáticamente**: si esta opción está **Habilitada**, el dispositivo se conecta automáticamente a la VPN cuando se comunica con un dominio especificado, como contoso.com.
- **Persistente**: de manera predeterminada, todas las reglas de la tabla de directivas de resolución de nombres (NRPT) están activas siempre que el dispositivo esté conectado mediante este perfil de VPN. Si esta opción está **habilitada** en una regla de NRPT, la regla sigue activa en el dispositivo incluso si la VPN se desconecta. La regla se mantiene hasta que se el perfil de VPN se quita o hasta que la regla se quita manualmente, lo cual puede hacerse mediante PowerShell.
En [Configuración de VPN de Windows 10](vpn-settings-windows-10.md), se describe la configuración. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Uso de la detección de redes de confianza para perfiles de VPN en dispositivos Windows 10 <!-- 1500165 -->
Al usar la detección de redes de confianza, podrá impedir que los perfiles VPN creen automáticamente una conexión VPN cuando el usuario ya esté en una red de confianza. Con esta actualización, podrá agregar sufijos DNS para habilitar la detección de redes de confianza en dispositivos que ejecuten Windows 10 y versiones posteriores (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para la plataforma > **VPN** para el tipo de perfil).
[Configuración de VPN de Windows 10](vpn-settings-windows-10.md) muestra la configuración de VPN actual.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Administración de dispositivos con Windows Holographic for Business empleados por varios usuarios <!-- 1907917, 1063203 -->
Actualmente, puede configurar parámetros de equipos compartidos en Windows 10 y dispositivos Windows Holographic for Business mediante una configuración personalizada de OMA-URI. En esta actualización se agregará un nuevo perfil para configurar las opciones de dispositivos compartidos (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** > **Dispositivo multiusuario compartido**).
Para obtener más información sobre esta característica, vaya a [Configuración de Intune para administrar dispositivos compartidos](shared-user-device-settings.md).
Se aplica a: Windows 10 y versiones posteriores, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Nueva configuración de actualizaciones de Windows 10 <!--2626030  2512994  -->
Para sus [Círculos de actualizaciones de Windows 10](windows-update-for-business-configure.md), puede configurar lo siguiente:
- **Comportamiento de actualizaciones automáticas**: use una nueva opción (*Restablecer valores predeterminados*) para restaurar la configuración de actualizaciones automáticas original en equipos con Windows 10 que ejecuten la *actualización de octubre de 2018*.
- **Impedir al usuario pausar las actualizaciones de Windows**: establezca una nueva configuración de actualizaciones de software que impida o permita que los usuarios pausen la instalación de actualizaciones en el menú *Configuración* de sus equipos. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>Los perfiles de correo electrónico de iOS pueden usar cifrado y firma de S/MIME <!-- 2662949 -->
Podrá crear un perfil de correo electrónico que incluya otra configuración. En esta actualización, se incluye la configuración de S/MIME que se puede usar para firmar y cifrar las comunicaciones por correo electrónico de dispositivos iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil**; elija **iOS** para la plataforma y **Correo electrónico** para el tipo de perfil).
La configuración actual se muestra en [Opciones de configuración de correo electrónico de iOS](email-settings-ios.md).

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Algunas opciones de configuración de BitLocker admiten Windows 10 Pro Edition<!-- 2727036 -->
Podrá crear un perfil de configuración que establezca los ajustes de Endpoint Protection en dispositivos con Windows 10, incluido BitLocker. En esta actualización se agrega la compatibilidad con Windows 10 Professional Edition en algunas opciones de configuración de BitLocker. Para ver estos ajustes de protección, vaya a [Configuración de Endpoint Protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Cambio del nombre de Configuración de dispositivo compartido a Mensaje de la pantalla de bloqueo para dispositivos iOS en Azure Portal<!-- 2809362 -->
Al crear un perfil de configuración de dispositivos iOS, puede agregar la opción **Configuración de dispositivo compartido** para mostrar texto específico en la pantalla de bloqueo. En esta actualización se incluyen los cambios siguientes: 
- El nombre de la opción **Configuración de un dispositivo compartido** en Azure Portal se cambia a "Mensaje de la pantalla de bloqueo (solo con supervisión)" (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > Elegir **iOS** para la plataforma > Elegir **Características del dispositivo** para el tipo de perfil > **Mensaje de la pantalla de bloqueo**).
- Al agregar mensajes de la pantalla de bloqueo, puede insertar un número de serie, un nombre de dispositivo u otro valor específico del dispositivo como una variable en **Información de etiqueta del activo** y **Nota al pie en la pantalla de bloqueo**. Por ejemplo, puede escribir `Device name: {{devicename}}` o `Serial number is {{serialnumber}}` entre llaves. [Tokens de iOS](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) muestra los tokens disponibles que se pueden usar.
En [Configuración para mostrar mensaje en la pantalla de bloqueo](shared-device-settings-ios.md), se muestra la configuración actual.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Adición en dispositivos iOS de nuevo App Store, visualización de documentos y configuración de restricción de dispositivos de juego <!-- 2827760-->
En **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para la plataforma y **Restricciones de dispositivo** para el tipo de perfil, en **App Store, visualización de documentos y juegos**, se han agregado las siguientes opciones de configuración: Permitir a las aplicaciones administradas escribir contactos en cuentas de contactos no administradas y Permitir a las aplicaciones no administradas leer en cuentas de contactos administradas. Para ver estas opciones de configuración, vaya a [Restricciones de dispositivos iOS](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Nueva configuración de notificaciones, sugerencias y bloqueo del teclado para dispositivos propietarios del dispositivo Android Enterprise <!-- 3201839 3201843 -->
Esta actualización incluye varias características de los dispositivos Android Enterprise cuando se ejecutan como propietario del dispositivo. Para usar estas características, vaya a **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > en **Plataforma**, elija **Android Enterprise** > en **Tipo de perfil**, elija **Solo el propietario del dispositivo** > **Restricciones de dispositivos**.

Estas son algunas de las nuevas características: 

- Deshabilitar la visualización de las notificaciones del sistema, incluidas las llamadas entrantes, las alertas del sistema, los errores del sistema, etc.
- Sugerir omitir los tutoriales de inicio y las sugerencias para las aplicaciones que se abren por primera vez.
- Deshabilitar la configuración avanzada del bloqueo del teclado, como la cámara, las notificaciones, el desbloqueo con huella digital, etc.


Para ver la configuración actual, vaya a [Configuración de restricciones de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Los dispositivos propietarios del dispositivo Android Enterprise pueden usar conexiones VPN siempre activas <!-- 3202194 -->
En esta actualización, puede usar conexiones VPN siempre activas en dispositivos propietarios del dispositivo Android Enterprise. Las conexiones VPN siempre activas permanecen conectadas o se vuelven a conectar inmediatamente cuando el usuario desbloquea el dispositivo, cuando se reinicia el dispositivo o cuando cambia la red inalámbrica. También puede poner la conexión en modo “bloqueo”, que bloquea todo el tráfico de red hasta que la conexión VPN esté activa.
Puede habilitar la VPN siempre activa en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **Restricciones de dispositivos** solo para el propietario del dispositivo > **Conectividad**. Para ver la configuración actual, vaya a [Configuración de restricciones de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nueva configuración para terminar los procesos en el Administrador de tareas de dispositivos Windows 10 <!-- 3285177 --> 
Esta actualización incluye una configuración nueva para terminar los procesos con el Administrador de tareas en dispositivos Windows 10. Con un perfil de configuración de dispositivo (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > en **Plataforma**, elija **Windows 10** > en **Tipo de perfil**, elija **Restricciones de dispositivos** > **Configuración general**), elige si permitir o impedir esta configuración.
Para ver la configuración actual, vaya a [Configuración de restricciones de dispositivos Windows 10](device-restrictions-windows-10.md).
Se aplica a: Windows 10 y versiones posteriores


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Mensajes de error de restricción de inscripción más detallados <!-- 3111564 -->
Los mensajes de error más detallados estarán disponibles cuando no se cumplan las restricciones de inscripción. Para ver estos mensajes, vaya a **Intune** > **Solucionar problemas** > y revise la tabla Errores de inscripción. Para obtener más información, vea la [lista de errores de inscripción](help-desk-operators.md#configuration-policies-reference).



### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="tenant-status-dashboard-----1124854---"></a>Panel Estado del inquilino <!-- 1124854 -->
En la nueva [página Estado del inquilino](tenant-status.md) se proporciona una ubicación única donde puede ver el estado del inquilino y los detalles relacionados.  El panel se divide en cuatro áreas:
- **Detalles del inquilino**: se muestra información como el nombre del inquilino y la ubicación, la entidad de MDM, el número total de dispositivos inscritos en el inquilino y el número de licencias. En esta sección también se indica la versión de mantenimiento actual del inquilino.
- **Estado del conector**: muestra información sobre conectores disponibles que ha configurado y, además, se puede mostrar una lista de los que aún no ha habilitado.  
   Basándose en el estado actual de cada conector, se marcan como Correcto, Advertencia o Incorrecto. Seleccione un conector para explorarlo en profundidad y ver sus detalles, o bien para configurar información adicional sobre este.
-  **Estado del servicio Intune**: muestra detalles sobre incidentes activos o interrupciones del inquilino. La información de esta sección se obtiene directamente del Centro de mensajes de Office.
-  **Noticias de Intune**: muestra mensajes activos para el inquilino. En estos mensajes, se incluyen notificaciones cuando el inquilino recibe las características de Intune más recientes.  La información de esta sección se obtiene directamente del Centro de mensajes de Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Nueva experiencia de ayuda y soporte técnico en el Portal de empresa para Windows 10 <!-- 1488939-->
La nueva página de ayuda y soporte técnico del Portal de empresa ayuda a los usuarios a solucionar problemas y solicitar ayuda para problemas de acceso y de aplicaciones. Desde la nueva página, puede enviar por correo electrónico detalles de registros de diagnóstico y errores, así como obtener los detalles del departamento de soporte técnico de su organización. También encontrará una sección de preguntas más frecuentes con vínculos a la documentación de Intune relevante. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Nueva experiencia de ayuda y soporte técnico para Intune <!-- #3307080 -->
Implementaremos la nueva experiencia de ayuda y soporte técnico a todos los inquilinos en los próximos días. Esta experiencia está disponible para Intune y puede accederse al usar las hojas de Intune en [Azure Portal](https://portal.azure.com/).
La nueva experiencia le permite describir el problema con sus propias palabras y recibir información sobre solución de problemas y contenido de corrección basado en la Web. Estas soluciones se ofrecen mediante un algoritmo de aprendizaje automático con reglas, basado en las consultas de los usuarios. Además de instrucciones específicas del problema, también puede usar el nuevo flujo de trabajo de creación de casos para abrir una incidencia de soporte técnico por teléfono o correo electrónico. Esta nueva experiencia reemplaza a la experiencia de ayuda y soporte técnico anterior de un conjunto estático de opciones seleccionadas previamente que se basan en el área de la consola en la que se encuentra cuando abre la sección Ayuda y soporte técnico. Para obtener más información, vea [Cómo obtener asistencia para Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="scope-tags-for-apps----1081941---"></a>Etiquetas de ámbito para las aplicaciones <!-- 1081941 -->
Puede crear etiquetas de ámbito para limitar el acceso a roles y aplicaciones. Puede agregar una etiqueta de ámbito a una aplicación para que solo los usuarios con roles que también tengan asignada esa etiqueta de ámbito puedan acceder a la aplicación. Actualmente, no es posible asignar etiquetas de ámbito a las aplicaciones que se agregan a Intune desde Google Play administrado o a aquellas que se compran mediante el Programa de Compras por Volumen de Apple (VPP), si bien será posible en el futuro. Para obtener más información, vea [Uso de etiquetas de ámbito para filtrar directivas](scope-tags.md).



## <a name="week-of-december-10-2018"></a>Semana del 10 de diciembre de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="updates-for-application-transport-security----748318---"></a>Actualizaciones para Seguridad de transporte de aplicaciones <!-- 748318 -->

Microsoft Intune admite la versión 1.2+ del protocolo Seguridad de la capa de transporte (TLS) para proporcionar el mejor cifrado en su clase, a fin de garantizar que Intune sea más seguro de forma predeterminada, y alinearlo con otros servicios de Microsoft, como Microsoft Office 365. Con el fin de satisfacer este requisito, en los portales de empresa de iOS y macOS se exigirán los requisitos de Seguridad de transporte de aplicaciones (ATS) actualizados de Apple que también requieren TLS 1.2+. ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan las aplicaciones Portal de empresa para iOS y macOS. Para más información, vea el [blog de soporte técnico de Intune](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>El SDK de aplicaciones de Intune admitirá claves de cifrado de 256 bits <!-- 1832174 -->
El SDK de aplicaciones de Intune para Android ahora usa claves de cifrado de 256 bits cuando el cifrado esté habilitado mediante las directivas de protección de aplicaciones. El SDK seguirá siendo compatible con las claves de 128 bits para mantener la compatibilidad con el contenido y las aplicaciones que usen las versiones anteriores del SDK.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>Versión de actualización automática 4.5.0 de Microsoft necesaria para dispositivos macOS <!-- 3503442 -->
Para seguir recibiendo actualizaciones del Portal de empresa y otras aplicaciones de Office, los dispositivos macOS administrados por Intune se deben actualizar a la actualización automática 4.5.0 de Microsoft. Es posible que los usuarios ya tengan esta versión para sus aplicaciones de Office.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune requiere macOS 10.12 o versiones posteriores <!-- 2827778 -->
Intune ahora requiere macOS versión 10.12 o posterior. Los dispositivos con versiones anteriores de macOS no pueden usar el Portal de empresa para inscribirse en Intune. Para recibir asistencia de soporte técnico y nuevas características, los usuarios deben actualizar su dispositivo a macOS 10.12 o posterior y actualizar el Portal de empresa a la versión más reciente.

## <a name="week-of-november-26-2018"></a>Semana del 26 de noviembre de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Desinstalación de aplicaciones en dispositivos iOS supervisados corporativos <!-- 1281677 -->

Puede quitar cualquier aplicación en dispositivos iOS corporativos supervisados. Puede quitar cualquier aplicación estableciendo como destino grupos de usuarios o dispositivos con un tipo de asignación **Desinstalar**. Para dispositivos iOS personales o no supervisados, podrá quitar solo las aplicaciones que se instalaron mediante Intune.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Descarga de contenido de aplicaciones Win32 de Intune <!-- 2617320 -->
Los clientes Windows 10 RS3 y versiones posterior descargarán contenido de aplicaciones Win32 de Intune mediante un componente de Optimización de distribución del cliente Windows 10. La Optimización de distribución proporciona la funcionalidad punto a punto está activada de manera predeterminada. La Optimización de distribución se puede configurar según la directiva de grupo y, en el futuro, a través de MDM de Intune. Para más información, consulte el artículo sobre la [Optimización de distribución para Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menú de contenido de aplicaciones y dispositivos de usuario final <!-- 2771453 -->
Los usuarios finales ahora pueden usar el menú contextual del dispositivo y las aplicaciones para desencadenar acciones comunes, como cambiar el nombre de un dispositivo o comprobar el cumplimiento.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Establecer un fondo personalizado en la aplicación Managed Home Screen <!-- 3041945 -->
Se está agregando una configuración que permitirá personalizar la apariencia del fondo de la aplicación Managed Home Screen en dispositivos Android Enterprise en pantalla completa con varias aplicaciones.  Para configurar el **fondo de dirección URL personalizado**, vaya a Intune en Azure Portal > Configuración del dispositivo. Seleccione un perfil de configuración del dispositivo actual o cree uno para editar su configuración de quiosco.
Para ver la configuración de pantalla completa, consulte las [restricciones de los dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Guardar y aplicar asignaciones de la directiva de protección de la aplicación <!-- 3104570 -->
Ahora puede controlar mejor las [asignaciones de la directiva de protección de la aplicación](app-protection-policies.md#deploy-a-policy-to-users). Cuando selecciona *Asignaciones* para establecer o editar las asignaciones de una directiva, debe **guardar** la configuración antes de que se aplique el cambio. Use **Descartar** para borrar todos los cambios que haga sin guardar ningún cambio en las listas de inclusión o exclusión.  Como se requiere guardar o descartar, solo los usuarios deseados tienen asignada una directiva de protección de la aplicación.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nueva configuración del explorador Microsoft Edge en Windows 10 y versiones posteriores <!-- 3174639 -->
Esta actualización incluye una nueva configuración para ayudar a controlar y administrar el explorador Microsoft Edge en los dispositivos. Para ver una lista de estas configuraciones, consulte[Restricciones de dispositivos para Windows 10 (y versiones posteriores)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Las nuevas aplicaciones son compatibles con las directivas de protección de aplicaciones <!-- 3330037 -->
Ahora puede administrar las aplicaciones siguientes con las [directivas de protección de aplicaciones de Intune](app-protection-policies.md):
- Stream (iOS)
- To DO (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Use las directivas de protección de aplicaciones para proteger los datos corporativos y controlar la transferencia de datos de estas aplicaciones, como otras aplicaciones administradas por las directivas de Intune. Nota: Si Flow todavía no aparece en la consola, lo agregará al crear o editar directivas de protección de aplicaciones. Para hacerlo, use la opción **+ Más aplicaciones** y especifique el *id. de la aplicación* para Flow en el campo de entrada. Para Android use *com.microsoft.flow* y para iOS, *com.microsoft.procsimo*.


### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Se muestran los números de versión y los números de compilación de iOS y macOS <!-- 1892471 -->
En **Conformidad de dispositivos** > **Conformidad de dispositivos** se muestran las versiones de los sistemas operativos iOS y macOS, que se pueden usar en las directivas de cumplimiento. Esta actualización incluye el número de compilación, que se puede configurar para ambas plataformas.
Cuando se publican las actualizaciones de seguridad, Apple normalmente deja el número de versión como está, pero actualiza el número de compilación. Si usa el número de compilación en una directiva de cumplimiento, puede comprobar fácilmente si hay instalada una actualización de vulnerabilidad.
Para usar esta característica, consulte las directivas de cumplimiento de [iOS](compliance-policy-create-ios.md#device-health) y [macOS](compliance-policy-create-mac-os.md#device-properties).

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Los círculos de actualizaciones se reemplazan por la configuración Optimización de distribución para Windows 10 y versiones posteriores <!-- 2753807 -->
Optimización de distribución es un perfil de configuración nuevo para Windows 10 y versiones posteriores. Esta característica proporciona una experiencia más simplificada para brindar actualizaciones de software a los dispositivos de la organización. Esta actualización también ayuda a entregar la configuración en círculos de actualizaciones nuevos y existentes con un perfil de configuración.
Para configurar un perfil de configuración de optimización de distribución, consulte la [configuración de Optimización de distribución de Windows 10 (y versiones posteriores)](delivery-optimization-windows.md).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Nueva configuración de restricción de dispositivos agregada a dispositivos iOS y macOS <!-- 2827760 -->
Esta actualización incluye nuevas configuraciones para los dispositivos iOS y Mac OS que se lanzan con iOS 12:

**Configuración de iOS**: 
- General: bloquear la eliminación de aplicaciones (solo supervisado)
- General: bloquear el modo restringido USB (solo supervisado)
- General: exigir fecha y hora automáticas (solo supervisado)
- Contraseña: bloquear el relleno automático de contraseñas (solo supervisado)
- Contraseña: bloquear las solicitudes de proximidad de contraseñas (solo supervisadas)
- Contraseña: bloquear el uso compartido de contraseñas (solo supervisado)

**Configuración de macOS**: 
- Contraseña: bloquear el relleno automático de contraseñas
- Contraseña: bloquear las solicitudes de proximidad de contraseñas
- Contraseña: bloquear el uso compartido de contraseñas

Para más información sobre estas configuraciones, consulte la configuración de restricciones de dispositivos [iOS](device-restrictions-ios.md) y [macOS](device-restrictions-macos.md).

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Seleccionar las aplicaciones de las que se realiza un seguimiento en la página de estado de la inscripción <!-- 2531007 -->
Puede elegir de qué aplicaciones se realiza un seguimiento en la página de estado de la inscripción. El usuario no puede usar el dispositivo hasta que se instalen estas aplicaciones. Para más información, consulte [Configurar una página de estado de inscripción](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Búsqueda del dispositivo Autopilot por número de serie <!--2595788 -->
Ahora puede buscar dispositivos Autopilot por número de serie. Para hacerlo, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos** > escriba un número de serie en el cuadro **Buscar por número de serie** > presione ENTRAR.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Seguimiento de la instalación de Office ProPlus <!--2620217 -->
Los usuarios pueden realizar un seguimiento del progreso de instalación de [Office ProPlus](apps-add-office365.md) en la [página de estado de la inscripción](windows-enrollment-status.md). Para más información, consulte [Configurar una página de estado de inscripción](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas sobre tokens de VPP que expiran próximamente o licencias del Portal de empresa a punto de agotarse <!-- 2237572 -->
Si usa el Programa de Compras por Volumen (VPP) para tener en servicio el Portal de empresa durante la inscripción de DEP, Intune le avisará cuando el token de VPP esté a punto de expirar y las licencias del Portal de empresa se estén agotando.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Compatibilidad del programa de inscripción de dispositivos macOS para cuentas de Apple School Manager <!--3006133 -->
Intune permite usar el Programa de inscripción de dispositivos en dispositivos macOS para las cuentas de Apple School Manager.  Para más información, consulte el artículo sobre la [inscripción automática de dispositivos macOS con el Programa de inscripción de dispositivos de Apple o Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="new-intune-device-subscription-sku---3312071--"></a>Nueva SKU de suscripción a dispositivos de Intune <!--3312071-->
Para ayudar a reducir el costo de administración de dispositivos en las empresas, ahora tiene a su disposición una nueva SKU de suscripción basada en dispositivos. Las licencias de esta SKU de dispositivos de Intune se conceden mensualmente por dispositivo. El precio varía según el programa de licencias. Está disponible directamente mediante el portal de administración de Office y el [Contrato Enterprise](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), el [contrato de productos y servicios de Microsoft](https://www.microsoft.com/licensing/mpsa/default) (MPSA), los [contratos abiertos de Microsoft ](https://partner.microsoft.com/licensing/licensing-agreements) y los [proveedores de soluciones en la nube](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### <a name="device-management"></a>Administración de dispositivos

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Detener temporalmente el modo quiosco en dispositivos Android para realizar cambios <!-- 3041935 -->
Al usar dispositivos Android en modo quiosco con varias aplicaciones, puede que un administrador de TI deba realizar cambios en el dispositivo. Esta actualización incluye una configuración nueva de pantalla completa con varias aplicaciones que permite que un administrador de TI pause de manera temporal la pantalla completa con un PIN y obtener acceso a todo el dispositivo.
Para ver la configuración de pantalla completa, consulte las [restricciones de los dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Habilitar el botón de inicio virtual en dispositivos de quiosco de Android Enterprise  <!-- 3042021 -->
Una nueva configuración permitirá a los usuarios pulsar un botón de tecla programable en su dispositivo para cambiar entre la aplicación Managed Home Screen y otras aplicaciones asignadas en su dispositivo de quiosco con varias aplicaciones asignadas. Esta configuración es especialmente útil en escenarios donde una aplicación de quiosco del usuario no responde correctamente al botón "Atrás". Podrá configurar esta opción para dispositivos Android corporativos de un solo uso. Para habilitar o deshabilitar el **botón de inicio virtual**, vaya a Intune en Azure Portal > Configuración del dispositivo. Seleccione un perfil de configuración del dispositivo actual o cree uno para editar su configuración de quiosco.
Para ver la configuración de pantalla completa, consulte las [restricciones de los dispositivos Android Enterprise](device-restrictions-android-for-work.md).

## <a name="week-of-november-12-2018"></a>Semana del 12 de noviembre de 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Compatibilidad del control de acceso de red (NAC) con Citrix SSO para iOS <!-- 3259404 -->

Citrix lanzó una actualización para Citrix Gateway para permitir el control de acceso de red (NAC) para Citrix SSO para iOS en Intune. Puede optar por incluir un identificador de dispositivo en un perfil de VPN en Intune y luego insertar este perfil en los dispositivos iOS. Deberá instalar la actualización más reciente de Citrix Gateway para usar esta funcionalidad.

[Configuración de VPN en dispositivos iOS](vpn-settings-ios.md#base-vpn-settings) proporciona más información sobre el uso de NAC, incluidos algunos requisitos adicionales. 

## <a name="week-of-november-5-2018"></a>Semana del 5 de noviembre de 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Compatibilidad con OAuth de iOS 12 en perfiles de correo electrónico de iOS <!--2155106 -->

Los perfiles de correo electrónico iOS de Intune son compatibles con Open Authorization (OAuth) para iOS 12. Para ver esta característica, cree un perfil (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** como plataforma > **Correo electrónico** como tipo de perfil) o actualice un perfil de correo electrónico iOS existente. Si habilita OAuth en un perfil que ya se ha implementado en los usuarios, se les pedirá que se vuelvan a autenticar y que vuelvan a descargar su correo electrónico.

En [Perfiles de correo electrónico iOS](email-settings-ios.md) hay más información sobre cómo usar OAuth en un perfil de correo electrónico.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Compatibilidad con AutoPilot para dispositivos híbridos unidos a Azure Active Directory (versión preliminar) <!-- 1048100-->
Ahora puede configurar dispositivos híbridos unidos a Azure Active Directory mediante AutoPilot. Los dispositivos deben estar unidos a la red de la organización para usar la característica de AutoPilot híbrida. Para más información, vea [Implementar dispositivos unidos a Azure AD híbrido mediante Intune y Windows Autopilot (versión preliminar)](windows-autopilot-hybrid.md).
Esta característica se implementará en toda la base de usuarios durante los próximos días. Por tanto, es posible que no pueda seguir estos pasos hasta que se implemente en su cuenta.

## <a name="week-of-october-29-2018"></a>Semana del 29 de octubre de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Requerir PIN que no sea biométrico después de un tiempo de expiración especificado <!-- 1506985 -->
Al exigir un número de identificación personal no biométrico después de transcurrir un tiempo de expiración especificado por el administrador, Intune proporcionará una mayor seguridad para las aplicaciones compatibles con Administración de aplicaciones de móviles (MAM), ya que restringe el uso de identificación biométrica para el acceso a datos corporativos. La configuración afectará a los usuarios que dependen de Touch ID (iOS), Face ID (iOS), Android Biometric u otros métodos de autenticación biométrica futuros para tener acceso a aplicaciones compatibles con APP/MAM. Con esta configuración, los administradores de Intune tendrán un control más exhaustivo del acceso de los usuarios. De este modo, se evitan situaciones en las que un dispositivo con varias huellas digitales u otros métodos de acceso biométrico pueda revelar datos corporativos a un usuario incorrecto. En Azure Portal, abra **Microsoft Intune**. Seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones** > **Agregar una directiva** > **Configuración**. En la **Acceso** encontrará ajustes específicos. Para obtener información sobre la configuración del acceso, vea la [configuración para iOS](app-protection-policy-settings-ios.md#access-requirements) y la [configuración para Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Configuración de transferencia de datos de la aplicación de Intune en dispositivos iOS inscritos en MDM <!-- 2244713 -->
Podrá controlar por separado la configuración de la transferencia de datos de la aplicación de Intune en dispositivos iOS inscritos en MDM y la especificación de la identidad del usuario inscrito, que se conoce también como nombre principal de usuario (UPN). Los administradores que no usen el IntuneMAMUPN no observarán un cambio de comportamiento. Cuando esta función esté disponible, los administradores que usan el IntuneMAMUPN para controlar el comportamiento de la transferencia de datos en los dispositivos inscritos deben revisar la nueva configuración y actualizar la configuración de APP según sea necesario.

#### <a name="windows-10-win32-apps----2617325---"></a>Aplicaciones Win32 de Windows 10 <!-- 2617325 -->
Puede configurar las aplicaciones Win32 para instalarlas en el contexto de usuario para usuarios individuales, en comparación con la instalación de la aplicación para todos los usuarios del dispositivo.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Aplicaciones Win32 de Windows y scripts de PowerShell <!-- 2617330 -->
Los usuarios finales ya no tienen que iniciar sesión en el dispositivo para instalar las aplicaciones Win32 o ejecutar scripts de PowerShell. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Solución de problemas de instalación de la aplicación cliente <!-- 1363711 -->
Puede solucionar los problemas para que las aplicaciones cliente se instalen correctamente si consulta la columna etiquetada como **Instalación de la aplicación** en la hoja **Solución de problemas**. Para ver la hoja **Solución de problemas**, en el portal de Intune, seleccione **Solución de problemas** en **Ayuda y soporte técnico**.

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Compatibilidad del control de acceso a la red en clientes VPN de iOS <!-- 1333693 -->
Con esta actualización, hay una nueva configuración para habilitar el control de acceso de red (NAC) al crear un perfil de configuración de VPN de Cisco AnyConnect, F5 Access y Citrix SSO para iOS. Esta configuración permite que el identificador de NAC del dispositivo se incluya en el perfil de VPN. Actualmente, no existe ningún cliente de VPN ni solución de asociados de NAC que admita este nuevo identificador de NAC, pero le mantendremos informado en nuestra [entrada de blog de soporte técnico](ttps://aka.ms/iOS12_and_vpn) cuando estén disponibles.

Para usar NAC, deberá:
1. Optar por permitir que Intune incluya los identificadores de dispositivo en perfiles de VPN
2. Actualizar el software/firmware del proveedor de NAC con instrucciones directas de dicho proveedor

Para obtener información sobre esta configuración en un perfil de VPN para iOS, vea [Configuración de VPN en Microsoft Intune para dispositivos que ejecutan iOS](vpn-settings-ios.md). Para obtener más información sobre el control de acceso de red, vea [Integración del control de acceso de red (NAC) con Intune](network-access-control-integrate.md). 

Se aplica a iOS.

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Eliminar un perfil de correo electrónico de un dispositivo, incluso cuando hay un solo perfil de este tipo <!-- 1818139 -->
Antes no se podía quitar un perfil de correo electrónico de un dispositivo *si* era el único perfil de correo electrónico. Con esta actualización, se ha cambiado este comportamiento y ahora se puede quitar un perfil de correo electrónico aunque sea el único perfil de este tipo del dispositivo. Vea [Configuración del correo electrónico en Microsoft Intune](email-settings-configure.md) para obtener más información.

#### <a name="powershell-scripts-and-aad----2309469---"></a>Scripts de PowerShell y AAD <!-- 2309469 -->
Los scripts de PowerShell en Intune pueden estar dirigidos a grupos de seguridad de dispositivos de AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nueva configuración predeterminada "Tipo de contraseña requerida" para Android, Android Enterprise <!-- 2649963 -->
Al crear una directiva de cumplimiento (**Intune** > **Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Android** o **Android Enterprise** para Plataforma > Seguridad del sistema), el valor predeterminado de **Tipo de contraseña requerida** cambiará:

Desde: Valor predeterminado del dispositivo Hasta: Al menos numérica

Se aplica a: Android, Android Enterprise

Para ver esta configuración, vaya a [Android](compliance-policy-create-android.md) y [Android Enterprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Usar una clave precompartida en un perfil de Wi-Fi de Windows 10 <!-- 2662938 -->
Con esta actualización, puede usar una clave precompartida (PSK) con el protocolo de seguridad WPA o WPA2-Personal para autenticar un perfil de configuración de Wi-Fi para Windows 10. También puede especificar la configuración de costo para una red de uso medido para la actualización del 10 de octubre de 2018 en dispositivos Windows 10.

Actualmente, debe importar un perfil de Wi-Fi o crear un perfil personalizado para usar una clave precompartida. [Configuración de Wi-Fi para Windows 10](wi-fi-settings-windows.md) muestra la configuración actual. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Eliminar certificados PKCS y SCEP de los dispositivos <!-- 3218390 -->
En algunos casos, los certificados PKCS y SCEP se conservaban en los dispositivos incluso si se quitaba una directiva de un grupo, se eliminaba una configuración o una implementación de cumplimiento, o bien un administrador actualizaba un perfil SCEP o PKCS existente. Esta actualización cambia el comportamiento. Hay algunos casos en los que los certificados PKCS y SCEP se quitan de los dispositivos y otros casos en los que dichos certificados se conservan. Vea [Eliminación de certificados SCEP y PKCS en Microsoft Intune](remove-certificates.md) para conocer estos casos.

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Usar un equipo selector para cumplimiento en dispositivos macOS <!-- 2504381 -->
Esta actualización incluye el equipo selector de macOS para evaluar el cumplimiento de los dispositivos. Para configurar la directiva del equipo selector, vea [Incorporación de una directiva de cumplimiento de dispositivos macOS con Intune](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="enrollment-abandonment-report----1382924---"></a>Informe de abandono de la inscripción <!-- 1382924 -->
Un nuevo informe en el que se proporciona información detallada sobre las inscripciones abandonadas está disponible en **Inscripción de dispositivos** > **Supervisión**. Para obtener más información, vea [Company portal abandonment report](enrollment-report-company-portal-abandon.md) (Informe de abandono del portal de empresa).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Nuevos característica de términos de uso de Azure Active Directory <!-- 2870393 -->
Azure Active Directory tiene una característica de términos de uso que puede usar en lugar de los términos y condiciones existentes de Intune. La característica de términos de uso de Azure AD proporciona más flexibilidad sobre qué términos se van a mostrar y cuándo, mejor compatibilidad de localización, mayor control sobre cómo se representan los términos y creación de informes mejorada. La característica de términos de uso de Azure AD requiere Azure Active Directory Premium P1, que también forma parte del conjunto de aplicaciones Enterprise Mobility + Security E3. Para más información, vea el artículo [Administrar los términos y condiciones de acceso de los usuarios de su empresa](terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support---3188762--"></a>Compatibilidad con el modo de propietario del dispositivo Android <!--3188762-->
Para Samsung Knox Mobile Enrollment, Intune ahora admite la inscripción de dispositivos en el modo de administración de propietario del dispositivo Android. Los usuarios en redes Wi-Fi o de telefonía móvil se pueden inscribir con unas pocas pulsaciones al encender sus dispositivos por primera vez. Para más información, vea [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Inscripción automática de dispositivos Android mediante Samsung Knox Mobile Enrollment).

### <a name="device-management"></a>Administración de dispositivos
#### <a name="new-settings-for-software-updates------1907869---"></a>Nuevas configuraciones para actualizaciones de software <!-- 1907869 -->  
- Ahora puede configurar algunas notificaciones para avisar a los usuarios finales sobre los reinicios necesarios para finalizar la instalación de las actualizaciones de software más recientes.   
- Ahora puede configurar un mensaje de advertencia de reinicio para los reinicios que se producen fuera de las horas de trabajo. Estos mensajes admiten escenarios BYOD.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Agrupación de dispositivos inscritos en Windows Autopilot por identificador de correlación <!-- 2075110 -->
Intune ahora admite la agrupación de dispositivos Windows mediante un identificador de correlación cuando se inscriban mediante [AutoPilot para dispositivos existentes](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) con Configuration Manager. El identificador de correlación es un parámetro del archivo de configuración de AutoPilot. Intune establecerá de forma automática el [atributo enrollmentProfileName de dispositivo de Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) para que sea igual a "OfflineAutopilotprofile-<correlator ID>". Esto permite la creación de grupos dinámicos de Azure AD arbitrarios en función del identificador de correlación a través del atributo enrollmentprofileName para las inscripciones de AutoPilot sin conexión. Para más información vea [Windows Autopilot para dispositivos existentes](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies----2984657---"></a>Directivas de protección de aplicaciones de Intune <!-- 2984657 -->
Las directivas de protección de aplicaciones de Intune permiten configurar varias opciones de protección de datos para aplicaciones protegidas de Intune, como Microsoft Outlook y Microsoft Word. Se ha cambiado la apariencia de estas opciones para [iOS](app-protection-policy-settings-ios.md) y [Android](app-protection-policy-settings-android.md) a fin de facilitar su detección de forma individual. Hay tres categorías de configuraciones de directiva:
- **Reubicación de datos** : este grupo incluye los controles de prevención de pérdida de datos (DLP), como restricciones para cortar, copiar, pegar y guardar como. Esta configuración determina cómo los usuarios interactúan con los datos en las aplicaciones.
- **Requisitos de acceso**: este grupo contiene las opciones de PIN por aplicación que determinan cómo el usuario final tiene acceso a las aplicaciones en un contexto de trabajo.  
- **Inicio condicional** : este grupo contiene configuraciones como la configuración mínima del sistema operativo, la detección de dispositivos liberados o modificados y períodos de gracia sin conexión.  
  
No cambia la funcionalidad de la configuración, pero será más fácil encontrarla cuando se trabaja en el flujo de creación de la directiva.

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune admitirá un tamaño de paquete máximo de 8 GB para las aplicaciones de línea de negocio <!-- 1727158 -->
Intune aumentó el tamaño de paquete máximo a 8 GB para las aplicaciones de línea de negocio (LOB). Para más información, vea [Agregar aplicaciones a Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Adición de una imagen de marca personalizada para la aplicación Portal de empresa <!-- 1916266 -->
Como administrador de Microsoft Intune, puede cargar una imagen de marca personalizada que se mostrará como imagen de fondo en la página de perfil del usuario en la aplicación Portal de empresa de iOS. Para obtener más información sobre cómo configurar la aplicación Portal de empresa, vea [How to configure the Microsoft Intune Company Portal app](company-portal-app.md) (Cómo configurar la aplicación Portal de empresa de Microsoft Intune).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune mantendrá el idioma de Office localizado al actualizar Office en los equipos de los usuarios finales <!-- 2971030 -->
Cuando Intune instala Office en los equipos de los usuarios finales, estos recibirán automáticamente los mismos paquetes de idioma que tenían con las instalaciones de Office .MSI anteriores. Para más información, vea [Asignación de aplicaciones de Office 365 a dispositivos Windows 10 con Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Nueva experiencia de soporte técnico de Intune en el portal de administración de dispositivos de Microsoft 365 <!-- 3076965 -->
Se va a lanzar una nueva experiencia de ayuda y soporte técnico para Intune en el [portal de administración de dispositivos de Microsoft 365]( http://devicemanagement.microsoft.com). La nueva experiencia le permite describir el problema con sus propias palabras y recibir información sobre solución de problemas y contenido de corrección basado en la Web. Estas soluciones se ofrecen mediante un algoritmo de aprendizaje automático con reglas, basado en las consultas de los usuarios.  

Además de instrucciones específicas del problema, también puede utilizar el nuevo flujo de trabajo de creación de casos para abrir una incidencia de soporte técnico por teléfono o correo electrónico.  

Los clientes que forman parte del lanzamiento, esta nueva experiencia reemplaza la actual experiencia de ayuda y soporte técnico de un conjunto estático de opciones previamente seleccionadas que se basan en el área de la consola en la que se encuentra cuando abre la sección Ayuda y soporte técnico.  

*Esta nueva experiencia de ayuda y soporte técnico se va a lanzar para algunos pero no todos los inquilinos y está disponible en el portal de administración de dispositivos. Los participantes de esta nueva experiencia se seleccionan aleatoriamente entre los inquilinos de Intune disponibles. Se agregarán nuevos inquilinos a medida que se expanda el lanzamiento.*  

Para obtener más información, vea [Nueva experiencia de Ayuda y soporte técnico](get-support.md#help-and-support-experience) en Cómo obtener asistencia para Microsoft Intune.  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Módulo de PowerShell para Intune: versión preliminar disponible <!-- 951068 -->
Ya hay disponible en [GitHub]( https://aka.ms/intunepowershell) una versión preliminar de un nuevo módulo de PowerShell, que proporciona compatibilidad con la API de Intune a través de Microsoft Graph. Para obtener más información sobre cómo usar este módulo, consulte el archivo Léame en esa ubicación. 


## <a name="week-of-october-15-2018"></a>Semana del 15 de octubre de 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Solicitud de PIN al cambiar los identificadores de huella digital o cara en un dispositivo <!-- 2637704  -->
Se pide un PIN a los usuarios después de realizar cambios biométricos en su dispositivo iOS. Esto incluye cambios en las huellas digitales o los identificadores de cara registrados. El tiempo de la solicitud depende de la configuración del tiempo de espera de *Recheck access requirements after (minutes)* (Volver a comprobar los requisitos de acceso después de [minutos]).  Cuando no se establece ningún PIN, se solicita al usuario que establezca uno. 
 
Esta característica solo está disponible para iOS y requiere la participación de aplicaciones que integran Intune APP SDK para iOS, versión 9.0.1 o posterior. La integración del SDK es necesaria para que se pueda aplicar el comportamiento en las aplicaciones de destino. Esta integración ocurre de manera gradual y depende de los equipos de la aplicación específica. Algunas de las aplicaciones que participan son WXP, Outlook, Managed Browser y Yammer.


## <a name="week-of-october-1-2018"></a>Semana del 1 de octubre de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Acceso a las propiedades de perfil principales mediante la aplicación del Portal de empresa <!-- 772203 -->
Los usuarios finales pueden acceder ahora a las propiedades y acciones de cuenta principales, como el restablecimiento de contraseña, desde la aplicación del Portal de empresa. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Configuración de la directiva de protección de aplicaciones para el bloqueo de teclados de terceros en iOS <!-- 1248481 -->
En dispositivos iOS, los administradores de Intune pueden bloquear el uso de teclados de terceros al acceder a datos de la organización en aplicaciones protegidas mediante directivas. Cuando la directiva de protección de aplicaciones (APP) está configurada para bloquear teclados de terceros, el usuario del dispositivo recibe un mensaje la primera vez que interactúa con los datos corporativos al usar un teclado de terceros. Todas las demás opciones, que no afecten al teclado nativo, se bloquean y los usuarios de los dispositivos no podrán verlas. Los usuarios de los dispositivos verán el mensaje del cuadro de diálogo una vez. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Acceso a la cuenta de usuario de aplicaciones de Intune en dispositivos iOS y Android administrados <!-- 1248496 -->
Como administrador de Microsoft Intune, puede controlar qué cuentas de usuario se agregan a las aplicaciones de Microsoft Office en dispositivos administrados. Puede limitar el acceso solo a las cuentas de usuario de la organización permitidas y bloquear las cuentas personales en los dispositivos inscritos. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Directiva de configuración de aplicaciones iOS y Android para Outlook <!--1828527 -->
Ahora, puede crear una directiva de configuración de aplicaciones de Outlook iOS y Android para usuarios locales que aprovechan la autenticación básica con el protocolo ActiveSync. Se agregarán opciones de configuración adicionales a medida que se habiliten en Outlook para iOS y Android.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Paquetes de idioma de Office 365 Pro Plus <!-- 1833450 -->
Como administrador de Intune, podrá implementar idiomas adicionales para las aplicaciones Office 365 Pro Plus administradas mediante Intune. La lista de idiomas disponibles incluye el **Tipo** de paquete de idioma (núcleo, parcial y corrección). En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. En la lista **Tipo de aplicación** de la hoja **Agregar aplicación**, seleccione **Windows 10** en **Conjunto de aplicaciones de Office 365**. Seleccione **Idiomas** en la hoja **Configuración del conjunto de aplicaciones**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Extensiones de los archivos de aplicaciones de línea de negocio (LOB) de Windows <!-- 1884873 -->
Ahora, las extensiones de archivo de las aplicaciones de LOB de Windows incluirán las extensiones *.msi*, *.appx*, *.appxbundle*, *.msix* y *.msixbundle*. Puede agregar una aplicación en Microsoft Intune seleccionando **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. Se mostrará el panel **Agregar aplicación**, que permite seleccionar el **tipo de aplicación**. En el caso de las aplicaciones de LOB de Windows, seleccione la aplicación de **línea de negocio** como el tipo de aplicación, elija el **archivo de paquete de aplicación** y, después, especifique un archivo de instalación con la extensión adecuada.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Implementación de aplicaciones Windows 10 con Intune<!-- 2309001 -->
Aprovechando la compatibilidad actual con aplicaciones de línea de negocio (LOB) y Microsoft Store para aplicaciones empresariales, los administradores pueden usar Intune para implementar la mayoría de las aplicaciones existentes de su organización a los usuarios finales en dispositivos Windows 10. Los administradores pueden agregar, instalar y desinstalar aplicaciones para los usuarios de Windows 10 en una variedad de formatos, como archivos MSI, Setup.exe o MSP. Intune evaluará las reglas de requisitos antes de realizar la descarga y la instalación, y notificará a los usuarios finales del estado o los requisitos de reinicio a través del Centro de actividades de Windows 10. Esta función desbloqueará de manera eficaz las organizaciones interesadas en el desplazamiento de esta carga de trabajo a Intune y la nube. Esta característica está actualmente en versión preliminar pública y esperamos poder agregarle nuevas funciones importantes en los próximos meses. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menú de contenido de aplicaciones y dispositivos de usuario final <!-- 2771453 -->
Los usuarios finales ahora pueden usar el menú contextual de aplicaciones y dispositivos para desencadenar acciones comunes, como cambiar el nombre de un dispositivo o comprobar su cumplimiento. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Métodos abreviados de teclado del Portal de empresa de Windows <!-- 2771518 -->
Ahora, los usuarios finales podrán desencadenar acciones de aplicación y dispositivo en el Portal de empresa de Windows mediante métodos abreviados de teclado (aceleradores).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Creación de sufijos DNS en los perfiles de configuración de VPN en dispositivos que ejecutan Windows 10<!-- 1333668 -->
Cuando se crea un perfil de configuración del dispositivo VPN (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **VPN** para tipo de perfil), se escriben algunos valores de DNS. Con esta actualización, también puede especificar varios **sufijos DNS** en Intune. Al usar los sufijos DNS, puede buscar un recurso de red mediante su nombre corto, en lugar del nombre de dominio completo (FQDN). Esta actualización también le permite cambiar el orden de los sufijos DNS en Intune.
[Configuración de VPN de Windows 10](vpn-settings-windows-10.md#dns-settings) muestra la configuración de DNS actual.
Se aplica a: Dispositivos Windows 10

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Compatibilidad con VPN siempre activa para perfiles de trabajo empresarial de Android <!-- 1333705 -->
En esta actualización, puede usar conexiones VPN siempre activas en dispositivos empresariales Android con perfiles de trabajo administrados. Las conexiones VPN siempre activas permanecen conectadas o se vuelven a conectar inmediatamente cuando el usuario desbloquea el dispositivo, cuando se reinicia el dispositivo o cuando cambia la red inalámbrica. También puede poner la conexión en modo “bloqueo”, que bloquea todo el tráfico de red hasta que la conexión VPN esté activa.
Puede habilitar la VPN siempre activa en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android empresarial** para plataforma > **Restricciones de dispositivo** > **Conectividad**.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Emitir certificados SCEP para los dispositivos sin usuario <!-- 1744554 -->
Actualmente, los certificados se emiten a los usuarios. Con esta actualización, se pueden emitir certificados SCEP para los dispositivos, incluidos los dispositivos sin usuario, como los quioscos multimedia (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **Certificado SCEP** para perfil). Otras actualizaciones incluyen:
- La propiedad **Asunto** en un perfil SCEP pasará a ser un cuadro de texto personalizado y puede incluir nuevas variables. 
- La propiedad **Nombre alternativo del firmante (SAN)** en un perfil SCEP ahora es un formato de tabla y puede incluir nuevas variables. En la tabla un administrador puede agregar un atributo y rellenar el valor en un cuadro de texto personalizado. La SAN será compatible con los siguientes atributos: 
  - DNS
  - Dirección de correo electrónico
  - UPN

  Estas nuevas variables se pueden agregar con texto estático en un cuadro de texto de valor personalizado. Por ejemplo, el atributo DNS puede agregarse como `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > Las llaves, los puntos y coma y los símbolos de barra vertical “ { } ; | ” no funcionará en el texto estático de la SAN. Las llaves solo deben rodear una de las nuevas variables de certificado de dispositivo que debe aceptar `Subject` o `Subject alternative name`. 

Nuevas variables de certificado de dispositivo:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` solo funciona para Windows y dispositivos unidos a dominios. 
>  -  Al especificar las propiedades del dispositivo como el IMEI, el número de serie y el nombre de dominio completo en el asunto o SAN para un certificado de dispositivo, tenga en cuenta que una persona con acceso al dispositivo podría suplantar estas propiedades. 

[Crear un perfil de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile) enumera las variables actuales al crear un perfil de configuración de SCEP. 

Se aplica a: Windows 10 y posterior e iOS, compatible con Wi-Fi

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Bloquear dispositivos no compatibles de forma remota <!-- 2064495 -->
Cuando un dispositivo no cumple los requisitos, puede crear una acción en la directiva de cumplimiento que bloquee el dispositivo de forma remota. En Intune > **Cumplimiento del dispositivo**, cree una nueva directiva o seleccione una directiva existente > **Propiedades**. Seleccione **Acciones en caso de incumplimiento** > **Agregar** y elija bloquear de forma remota el dispositivo.
Compatible con: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 y versiones posteriores 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Mejoras de perfil de quiosco multimedia de Windows 10 y versiones posteriores en Azure Portal <!-- 2748224 -->
Esta actualización incluye las siguientes mejoras para el perfil de configuración de dispositivo de quiosco multimedia de Windows 10 (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **Versión preliminar de quiosco** para tipo de perfil): 
- Actualmente, puede crear varios perfiles de quiosco multimedia en el mismo dispositivo. Con esta actualización, Intune admitirá un solo perfil de quiosco multimedia por dispositivo. Si necesita varios perfiles de quiosco multimedia en un único dispositivo, puede usar un URI personalizado.
- En un perfil de **Quiosco con varias aplicaciones**, puede seleccionar el tamaño del icono de la aplicación y el orden del **Diseño del menú inicio** en la cuadrícula de la aplicación. Si prefiere una mayor personalización, puede cargar un archivo XML.
- La configuración del explorador de quiosco multimedia pasará a estar en la configuración de **Quiosco**. Actualmente, la configuración **Explorador web del quiosco** tiene su propia categoría en Azure Portal.
Se aplica a: Windows 10 y versiones posteriores




### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Aplicar perfil de Autopilot para dispositivos Windows 10 inscritos que aún no están registrados para Autopilot <!-- 1558983 -->
Puede aplicar perfiles de Autopilot para dispositivos Windows 10 inscritos que aún no se han registrado para Autopilot. En el perfil de Autopilot, elija la opción **Convertir todos los dispositivos de destino a Autopilot** para registrar automáticamente los dispositivos que no se han registrado para Autopilot con los servicios de implementación de Autopilot. Permita un plazo de 48 horas para que se procese el registro. Cuando se anule la inscripción del dispositivo y este se restablezca, Autopilot lo aprovisionará.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Crear y asignar varios perfiles de la página Estado de inscripción a grupos de Azure AD <!-- 2526564 -->
Ya puede [crear y asignar](windows-enrollment-status.md) varios perfiles de la página Estado de inscripción a grupos de Azure AD.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migración desde el Programa de inscripción de dispositivos a Apple Business Manager en Intune <!--2748613-->
Apple Business Manager (ABM) funciona en Intune, así que puede actualizar su cuenta desde el Programa de inscripción de dispositivos (DEP) a ABM. El proceso en Intune es el mismo. Para actualizar la cuenta de Apple de DEP a ABN, vaya a [ https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817).

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Pestañas de estado de alerta e inscripción en la página de información general de inscripción de dispositivos <!--2748656-->
Ahora, las alertas y los errores de inscripción aparecen en pestañas distintas en la página de información general de inscripción de dispositivos.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Restricción de aplicaciones y bloqueo del acceso a los recursos de la compañía dispositivos Android <!-- 2451462  -->  
En **Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Android**  >  **Seguridad del sistema**, hay un nuevo valor en la sección *Seguridad del dispositivo* que se llama **Aplicaciones restringidas**. El valor **Aplicaciones restringidas** usa una directiva de cumplimiento para bloquear el acceso a recursos de la compañía si ciertas aplicaciones están instaladas en el dispositivo. El dispositivo se considera no compatible hasta que las aplicaciones restringidas se quitan del dispositivo.
Se aplica a: 
- Android




## <a name="week-of-september-24-2018"></a>Semana del 24 de septiembre de 2018

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Centro de Administración de dispositivos de Microsoft 365 <!-- 3078424 -->
Una de las promesas de Microsoft 365 es la simplificación de la administración. Con los años, hemos ido integrando servicios de Microsoft 365 back-end para entregar escenarios de extremo a extremo, como el acceso condicional de Intune y Azure AD. El nuevo [Centro de administración de Microsoft 365](http://devicemanagement.microsoft.com) consolida, simplifica e integra la experiencia de administración. El área de trabajo especialista en administración de dispositivos proporciona fácil acceso a todas las tareas y la información relacionadas con la administración de dispositivos y aplicaciones que necesita su organización. Esperamos que esto se convierta en el área de trabajo principal en la nube para los equipos informáticos de usuario final de empresa.

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>Compatibilidad con más entidades de certificación de terceros (CA) <!-- 3093107 -->
Si usa el protocolo de inscripción de certificados Simple (SCEP), ya puede emitir nuevos certificados y renovarlos en dispositivos móviles con Windows, iOS, Android y macOS.

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Intune cambia a compatibilidad con iOS 10 y versiones posteriores <!-- 2454656 -->  
Ahora la inscripción de Intune, el Portal de empresa y el explorador administrado incluyen dispositivos iOS que tengan solo la versión iOS 10 y posteriores. Para comprobar si hay dispositivos o usuarios que se vean afectados en la organización, vaya a Intune en Azure Portal > **Dispositivos** > **Todos los dispositivos**. Filtre por sistema operativo y, después, haga clic en **Columnas** para mostrar los detalles de la versión de sistema operativo. Pida a los usuarios que actualicen sus dispositivos a una versión del sistema operativo que sea compatible.  

Si posee o quiere inscribir alguno de los siguientes dispositivos, debe estar al tanto de que solo admiten iOS 9 y versiones anteriores.  Para seguir accediendo al Portal de empresa de Intune, debe actualizar estos dispositivos a dispositivos compatibles con iOS 10 o versiones posteriores:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (3ª generación) 
* iPad (1ª generación)  

## <a name="week-of-september-17-2018"></a>Semana del 17 de septiembre de 2018

### <a name="app-management"></a>Administración de aplicaciones

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>Quitar la duplicación de los iconos de estado de protección de la aplicación <!-- 3083391 -->
Los iconos **Estado del usuario para iOS** y **Estado del usuario para Android** estaban presentes en las páginas **Aplicaciones cliente: Información general** y **Aplicaciones cliente: Estado de protección de la aplicación**. Se han quitado los iconos de estado de la página **Aplicaciones cliente: Información general** para evitar la duplicación. 

## <a name="week-of-august-27-2018"></a>Semana del 27 de agosto de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Compatibilidad de túnel de paquete para perfiles de VPN por aplicación de iOS para los tipos de conexión Pulse Secure y personalizados <!-- 1520957 -->
Al usar perfiles de VPN por aplicación de iOS, puede elegir entre usar tunelización de capa de aplicación (app-proxy) o tunelización de nivel de paquete (packet-tunnel). Estas opciones están disponibles con los tipos de conexión siguientes:
- VPN personalizada
- Pulse Secure. Si no está seguro de qué valor usar, consulte la documentación de su proveedor de VPN.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Retraso cuando las actualizaciones de software de iOS se muestran en el dispositivo <!-- 1949583 -->
En Intune > **Actualizaciones de software** > **Directivas de actualización para iOS**, puede configurar los días y las horas en los que no desea que los dispositivos instalen ninguna actualización. En una actualización futura, podrá retrasar entre 1 y 90 días el momento en el que una actualización de software se muestra de forma visible en el dispositivo. 
[Configurar directivas de actualización de iOS en Microsoft Intune](software-updates-ios.md) enumera la configuración actual.

#### <a name="office-365-proplus-version----2213968---"></a>Versión de Office 365 ProPlus <!-- 2213968 -->
Al asignar las aplicaciones de Office 365 ProPlus a dispositivos Windows 10 mediante Intune, podrá seleccionar la versión de Office. En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones** > **Agregar aplicación**. Después, seleccione **Conjunto de aplicaciones Office 365 ProPlus (Windows 10)** en la lista desplegable **Tipo**. Seleccione **Configuración del conjunto de aplicaciones** para mostrar la hoja asociada. Establezca **Canal de actualización** en un valor, como **Mensualmente**. Si lo desea, quite otra versión de Office (msi) de los dispositivos del usuario final seleccionando **Sí**. Seleccione **Específico** para instalar una versión específica de Office del canal seleccionado en los dispositivos del usuario final. En este momento, en **Versión específica**, puede seleccionar la versión de Office que desee usar. Las versiones disponibles cambiarán con el tiempo. Por lo tanto, al crear una nueva implementación, las versiones disponibles pueden ser más recientes y no tener determinadas versiones anteriores disponibles. Las implementaciones actuales seguirán implementando la versión anterior, pero la lista de versiones se actualizará continuamente por canal. Para más información, vea [Información general de los canales de actualización para Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Compatibilidad con la configuración de DNS de registro para VPN de Windows 10 <!-- 2282852 -->
Con esta actualización, puede configurar perfiles de VPN de Windows 10 para registrar dinámicamente las direcciones IP asignadas a la interfaz VPN con el DNS interno, sin necesidad de usar perfiles personalizados.
Para obtener información sobre la configuración de perfil de VPN actual disponible, vea [Configuración de VPN de Windows 10](vpn-settings-windows-10.md). 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>El instalador de Portal de empresa para macOS ahora incluye el número de versión en el nombre de archivo del instalador <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759---"></a>Actualizaciones de aplicaciones automáticas de iOS <!-- 2729759 -->
Las actualizaciones de aplicaciones automáticas funcionan para las aplicaciones con licencia de dispositivo y usuario para la versión 11.0 de iOS y versiones posteriores.




### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello está dirigido a usuarios y dispositivos <!-- 1106609 -->
Cuando crea una directiva [Windows Hello para empresas](windows-hello.md), se aplica a todos los usuarios dentro de la organización (inquilinos). Con esta actualización, la directiva también se puede aplicar a determinados usuarios o específicos mediante una directiva de configuración de dispositivo (**Configuración del dispositivo** > **Perfiles**  >  **Crear perfil** > **Identity Protection** > **Windows Hello para empresas**).
En Intune en Azure Portal, la configuración de Windows Hello ahora existe tanto en **Inscripción del dispositivo** como en **Configuración del dispositivo**. **Inscripción del dispositivo** tiene como destino toda la organización (inquilinos) y es compatible con Windows AutoPilot (OOBE). **Configuración del dispositivo** tiene como destino los dispositivos y usuarios mediante una directiva que se aplica durante la inserción en el repositorio.
Esta característica se aplica a:  
- Windows 10 y versiones posteriores
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler es una conexión disponible para los perfiles VPN en iOS <!-- 1769858 -->
Cuando crea un perfil de configuración de dispositivo de VPN para iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > plataforma **iOS** > tipo de perfil **VPN**), hay varios tipos de conexión, incluidos Cisco, Citrix, etc. Esta actualización agrega Zscaler como un tipo de conexión. 
[Configuración de VPN para dispositivos que ejecutan iOS](vpn-settings-ios.md) enumera los tipos de conexión disponibles.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>Modo FIPS para perfiles de Wi-Fi de empresa para Windows 10 <!-- 1879077 -->
Ahora puede habilitar el modo Estándar federal de procesamiento de información (FIPS) para los perfiles de Wi-Fi de empresa para Windows 10 en Intune en Azure Portal. Asegúrese de que el modo FIPS está habilitado en la infraestructura de Wi-Fi si lo habilita en los perfiles de Wi-Fi.
En [Configuración de Wi-Fi para dispositivos Windows 10 y versiones posteriores en Intune](wi-fi-settings-windows.md) se muestra cómo crear un perfil de Wi-Fi.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Control del modo S en Windows 10 y dispositivos posteriores: versión preliminar pública <!-- 1958649 -->
Con esta actualización de características, puede crear un perfil de configuración de dispositivo que haga cambiar el modo S de un dispositivo Windows 10 o evitar que los usuarios cambien el modo S del dispositivo. Esta característica está en Intune > **Configuración del dispositivo** > **Perfiles** >  **Windows 10 y versiones posteriores** > **Edition upgrade and mode switch (Actualización de edición y conmutación de modo)**.
En [Presentamos Windows 10 en modo S](https://www.microsoft.com/windows/s-mode) se proporciona más información sobre el modo S.
Se aplica a: la compilación más reciente de [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (todavía en versión preliminar).


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Paquete de configuración de ATP de Windows Defender agregado automáticamente al perfil de configuración <!-- 2144658 -->
Cuando se usa la [Protección contra amenazas avanzada y la incorporación](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) de dispositivos en Intune, antes era necesario descargar un paquete de configuración y agregarlo al perfil de configuración. Con esta actualización, Intune obtiene de forma automática el paquete del Centro de seguridad avanzada de Windows Defender y lo agrega al perfil.
Se aplica a Windows 10 y versiones posteriores.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Requerir que los usuarios se conecten durante la instalación del dispositivo <!--2311457-->
Ahora puede establecer los perfiles de dispositivo para requerir que el dispositivo se conecte a una red antes de continuar más allá de la página Red durante la instalación de Windows 10. Aunque esta característica está en versión preliminar, se requiere una compilación 1809 de Windows Insider o una versión posterior para usar esta configuración.
Se aplica a: la compilación más reciente de [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (todavía en versión preliminar).


#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Restricción de aplicaciones y bloqueo del acceso a los recursos de la empresa en dispositivos iOS y Android Enterprise <!-- 2451462 -->
En **Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **iOS** > **Seguridad del sistema**, hay una nueva opción **Aplicaciones restringidas**. Esta nueva opción usa una directiva de cumplimiento para bloquear el acceso a recursos de la compañía si ciertas aplicaciones están instaladas en el dispositivo. El dispositivo se considera no compatible hasta que las aplicaciones restringidas se quitan del dispositivo.
Se aplica a iOS.

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Actualizaciones de compatibilidad con VPN moderna para iOS <!-- 2459928, 1819876, and 2650856 -->
Esta actualización agrega compatibilidad con los siguientes clientes VPN de iOS: 
- F5 Access (versión 3.0.1 y versiones posteriores)
- SSO de Citrix
- GlobalProtect de Palo Alto Networks versión 5.0 y versiones posteriores. También en esta actualización:
- El nombre del tipo de conexión de **F5 Access** existente se cambia a **F5 Access Legacy** para iOS.
- El nombre del tipo de conexión de **GlobalProtect de Palo Alto Networks** existente se cambia a **GlobalProtect de Palo Alto Networks (legacy)** para iOS.
Los perfiles existentes con estos tipos de conexión siguen funcionando con su correspondiente cliente heredado de VPN. Si usa Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN o GlobalProtect de Legacy Palo Alto Networks versión 4.1 y versiones anteriores con iOS, debe cambiar a las nuevas aplicaciones. Hágalo tan pronto como sea posible para garantizar que el acceso VPN esté disponible para dispositivos iOS a medida que se actualicen a iOS 12.
Para obtener más información sobre iOS 12 y los perfiles de VPN, vea el [blog del equipo de soporte técnico de Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Exportación de las directivas de cumplimiento del Portal de Azure clásico para volver a crearlas en Intune en Azure Portal <!-- 2469637 -->
Las directivas de cumplimiento creadas en el Portal de Azure clásico dejarán de utilizarse. Puede revisar y eliminar todas las directivas de cumplimiento existentes, pero no podrá actualizarlas. Si tiene que migrar las directivas de cumplimiento a Intune en Azure Portal, puede exportarlas como un archivo separado por comas (archivo *.csv*). Después, use los detalles del archivo para volver a crear estas directivas en Intune en Azure Portal.

> [!IMPORTANT]
> Cuando se retire el Portal de Azure clásico, ya no podrá acceder ni ver las directivas de cumplimiento. Por tanto, asegúrese de exportar las directivas y volverlas a crear en Azure Portal antes de la retirada del Portal de Azure clásico.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile: nuevo socio de Mobile Threat Defense <!-- 22662717 -->
Puede controlar el acceso desde dispositivos móviles a los recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Better Mobile, una solución de Mobile Threat Defense integrada en Microsoft Intune.

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Bloqueo del Portal de empresa en el modo de aplicación única hasta el inicio de sesión del usuario <!--1067692 --> 
Ahora tiene la opción de ejecutar Portal de empresa en el modo de aplicación única si autentica un usuario a través de Portal de empresa en lugar del Asistente para configuración durante la inscripción de DEP. Esta opción bloquea el dispositivo inmediatamente después de completar el Asistente para configuración, de manera que un usuario debe iniciar sesión para acceder al dispositivo. Este proceso garantiza que el dispositivo completa la incorporación y no está huérfano en un estado sin ningún usuario asociado.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Asignación de un usuario y un nombre descriptivo a un dispositivo AutoPilot <!--1346521 -->
Ahora puede [asignar un usuario a un único dispositivo Autopilot ](enrollment-autopilot.md). Los administradores también podrán proporcionar nombres descriptivos para saludar a los usuarios al configurar sus dispositivos con AutoPilot.
Se aplica a: la compilación más reciente de [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (todavía en versión preliminar).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Use licencias de dispositivo de VPP para tener en servicio el Portal de empresa durante la inscripción de DEP <!-- 1608345 -->
Ahora puede usar licencias de dispositivo del Programa de compras por volumen (VPP) para aprovisionar previamente Portal de empresa durante las inscripciones en el Programa de inscripción de dispositivos (DEP). Para ello, al [crear o editar un perfil de inscripción](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), especifique el token de VPP que quiera usar para instalar Portal de empresa. Asegúrese de que el token no expire y que dispone de suficientes licencias para la aplicación de Portal de empresa. En los casos en los que el token expire o se agoten las licencias, Intune instalará el Portal de empresa del App Store (se solicitará un identificador de Apple).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmación requerida para eliminar el token de VPP que se usa para tener en servicio el Portal de empresa <!-- 2237634 -->
Ahora se solicita confirmación para eliminar un token del Programa de Compras por Volumen (VPP) si se usa para preaprovisionar el Portal de empresa durante la inscripción de DEP.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloqueo de inscripciones de dispositivos personales Windows <!-- 1849498 -->
Puede [bloquear la inscripción de dispositivos personales Windows](enrollment-restrictions-set.md#set-device-type-restrictions) con la [administración de dispositivos móviles](windows-enroll.md) en Intune. Los dispositivos inscritos con el [agente de PC de Intune](manage-windows-pcs-with-microsoft-intune.md) no se puede bloquear con esta característica. Esta característica se desplegará gradualmente durante las próximas semanas, por lo que quizá no la vea de inmediato en la interfaz de usuario.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Especificación de patrones de nombre de equipo en un perfil de AutoPilot <!--1849855-->
Puede [especificar una plantilla de nombre de equipo](enrollment-autopilot.md#create-an-autopilot-deployment-profile) para generar y establecer el [nombre de equipo](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) durante la inscripción de AutoPilot. Se aplica a: la compilación más reciente de [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (todavía en versión preliminar).


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Para los perfiles de Windows AutoPilot, oculte las opciones de cambio de cuenta en las páginas de inicio de sesión de la compañía y de error de dominio <!--1901669 -->
Hay [nuevas opciones de perfil de Windows AutoPilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile) para que los administradores oculten las opciones de cambio de cuenta en las páginas de inicio de sesión de la empresa y de error de dominio. La ocultación de estas opciones requiere que se configure la personalización de marca de empresa en Azure Active Directory. Se aplica a: la compilación más reciente de [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) (todavía en versión preliminar).



### <a name="device-management"></a>Administración de dispositivos

#### <a name="delete-jamf-devices----2653306--"></a>Eliminación de dispositivos Jamf <!-- 2653306-->
Puede eliminar los dispositivos administrados por JAMF desde **Dispositivos** > seleccione el dispositivo de Jamf > **Eliminar**.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Cambio de terminología a "retirar" y "borrar" <!-- 2175759 -->
Para mantener la coherencia con Graph API, en la documentación y la interfaz de usuario de Intune se han cambiado los términos siguientes:
- **Eliminar datos de la compañía** se cambiará por "retirar".
- **Restablecimiento de fábrica** cambiará a **borrar**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>Cuadro de diálogo de confirmación si el administrador intenta eliminar el certificado push MDM <!-- 297909500-->
Si alguien intenta eliminar un certificado push MDM de Apple, en un cuadro de diálogo de confirmación se muestra el número de dispositivos iOS y macOS relacionados. Si se elimina el certificado, será necesario volver a inscribir estos dispositivos.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Configuración de seguridad adicional de Windows Installer <!-- 2282430 -->
Puede dejar que los usuarios controlen las instalaciones de aplicaciones. Si lo permite, las instalaciones que antes se detendrían debido a una infracción de seguridad podrán seguir funcionando. Puede indicar a Windows Installer que use permisos elevados cuando instale un programa en un sistema. Además, los elementos protegidos por WIP (Windows Information Protection) se pueden indexar y los metadatos relativos a estos elementos se pueden almacenar en una ubicación sin cifrar. Cuando la directiva está deshabilitada, los elementos protegidos por WIP no se indexan y no se muestran en los resultados de Cortana o del explorador de archivos. La funcionalidad de estas opciones está deshabilitada de forma predeterminada. 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Actualización de la experiencia de usuario en el sitio web de Portal de empresa <!--2000968 -->
Tras escuchar las opiniones de los clientes, se han agregado características nuevas al sitio web de Portal de empresa. Experimentará una mejora considerable en las funciones y la facilidad de uso actual de los dispositivos. Se ha aplicado un nuevo diseño moderno y dinámico a las áreas del sitio, como los detalles del dispositivo, los comentarios, el soporte técnico y la descripción general del dispositivo. También verá:

- Flujos de trabajo simplificados en todas las plataformas del dispositivo
- Flujos mejorados para la identificación y la inscripción de dispositivos
- Mensajes de error más útiles
- Lenguaje más descriptivo y menos terminología técnica
- Capacidad de compartir vínculos directos a aplicaciones
- Rendimiento mejorado de los catálogos de aplicaciones de gran tamaño
- Mayor accesibilidad para todos los usuarios  

Se ha actualizado la [documentación del sitio web de Portal de empresa de Intune](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) para reflejar estos cambios. Para ver un ejemplo de las mejoras de la aplicación, vea [Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Detección de jailbreak mejorada en informes de cumplimiento<!-- 2198738 -->
Ahora la configuración de detección de jailbreak mejorada aparece en todos los informes de cumplimiento en la consola de administración.

### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="scope-tags-for-policies---1081974---"></a>Etiquetas de ámbito para las directivas <!--1081974 -->
Puede crear [etiquetas de ámbito](scope-tags.md) para limitar el acceso a los recursos de Intune. Agregue una etiqueta de ámbito a una asignación de roles y luego agregue dicha etiqueta a un perfil de configuración. El rol solo tendrá acceso a los recursos con perfiles de configuración que tengan etiquetas de ámbito coincidentes (o no tengan ninguna etiqueta de ámbito).

## <a name="week-of-august-14-2018"></a>Semana del 14 de agosto de 2018

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Compatibilidad de macOS para el Programa de inscripción de dispositivos de Apple <!-- 747651 -->
Intune ahora admite la inscripción de dispositivos macOS el Programa de inscripción de dispositivos de Apple (DEP). Para obtener más información, vea [Inscripción automática de dispositivos macOS con el Programa de inscripción de dispositivos de Apple](device-enrollment-program-enroll-macos.md).

## <a name="week-of-july-23-2018"></a>Semana del 23 de julio de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Compatibilidad con aplicaciones de línea de negocio (LOB) para macOS <!-- 1895847 -->
Microsoft Intune permite implementar aplicaciones de LOB macOS como **Required** (Obligatoria) o como **Available with enrollment** (Disponible con inscripción). Los usuarios finales pueden obtener las aplicaciones implementadas como **Available** (Disponible) a través del Portal de empresa para macOS o del [sitio web del Portal de empresa](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Compatibilidad con aplicaciones integradas de iOS para pantalla completa <!-- 2051098 -->
Además de las aplicaciones de la Tienda y las aplicaciones administradas, ahora puede seleccionar una aplicación integrada (como Safari) que se ejecuta en pantalla completa en un dispositivo iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Editar implementaciones de aplicaciones de Office 365 Pro Plus <!-- 2150145 -->
Como administrador de Microsoft Intune, tiene más capacidad para editar las implementaciones de aplicaciones de Office 365 Pro Plus. Además, ya no tiene que eliminar las implementaciones para cambiar las propiedades del conjunto. En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones cliente** > **Aplicaciones**. En la lista de aplicaciones, seleccione su conjunto de aplicaciones Office 365 ProPlus.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>El SDK para aplicaciones de Intune para Android actualizado ya está disponible <!-- 2744271-->

Hay disponible una versión actualizada del SDK para aplicaciones de Intune para Android compatible con la versión de Android P. Si es desarrollador de aplicaciones y usa el SDK de Intune para Android, debe instalar la versión actualizada del SDK para aplicaciones de Intune a fin de garantizar que la funcionalidad de Intune dentro de las aplicaciones Android seguirá funcionando según lo esperado en dispositivos de Android P. En esta versión del SDK para aplicaciones de Intune se proporciona un complemento integrado que lleva a cabo las actualizaciones del SDK. No es necesario que reescriba ningún código existente que ya esté integrado. Para detalles, consulte el artículo sobre el [SDK de Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Si usa el anterior estilo de distintivo para Intune, se recomienda usar el icono de maletín. Para detalles de personalización de la marca, consulte [este repositorio de GitHub](https://github.com/msintuneappsdk/intune-app-partner-badge).


### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Crear directiva de cumplimiento de dispositivos usando la configuración de firewall en dispositivos macOS <!-- 1497640 -->
Cuando se crea una directiva de cumplimiento de macOS (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Plataforma: macOS** > **Seguridad del sistema**), hay nuevas opciones de **Firewall** disponibles: 

- **Firewall**: configure cómo se administran las conexiones entrantes en el entorno.
- **Conexiones entrantes**: **bloquee** todas las conexiones entrantes excepto las necesarias para los servicios básicos de Internet, como DHCP, Bonjour e IPSec. Esta opción también bloquea todos los servicios de uso compartido.
- **Modo sigiloso**: **habilite** el modo sigiloso para evitar que el dispositivo responda a solicitudes de sondeo. El dispositivo sigue respondiendo a las solicitudes entrantes de las aplicaciones autorizadas.

Se aplica a: macOS 10.12 y versiones posteriores

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Nuevo perfil de configuración de dispositivos Wi-Fi para Windows 10 y versiones posteriores <!-- 1879077 -->
Actualmente, puede importar y exportar perfiles de Wi-Fi mediante archivos XML. Con esta actualización, puede crear un perfil de configuración de dispositivo Wi-Fi directamente en Intune, igual que en otras plataformas.

Para crear el perfil, abra **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** > **Wi-Fi**. 

Se aplica a Windows 10 y versiones posteriores.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>La característica Quiosco (obsoleto) aparece atenuada y no se puede cambiar <!-- 2149998 -->
La [característica Quiosco](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** > **Restricciones de dispositivos**) está obsoleta y se sustituye por la [configuración de Quiosco para Windows 10 y versiones posteriores](kiosk-settings.md). Con esta actualización, la característica **Quiosco (obsoleto)** está atenuada y la interfaz de usuario no se puede modificar ni actualizar. 

Para habilitar el modo quiosco, vea [Configuración de quiosco para Windows 10 (y versiones posteriores)](kiosk-settings.md).

Se aplica a Windows 10 y versiones posteriores, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>API para usar entidades de certificación de terceros <!-- 2184013 -->
En esta actualización, hay una API de Java que permite que las entidades de certificación de terceros se integren con Intune y SCEP. Después, los usuarios pueden agregar el certificado SCEP a un perfil y aplicarlo a los dispositivos mediante MDM.

Actualmente, Intune admite [solicitudes SCEP mediante Servicios de certificados de Active Directory](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Alternar para mostrar u ocultar el botón Finalizar sesión en un explorador de Quiosco <!-- 2455253 -->
Ahora puede configurar si los exploradores de Quiosco muestran o no el botón Finalizar sesión. Puede ver el control en **Configuración del dispositivo** > **Quiosco (versión preliminar)** > **Kiosk Web Browser**. Si está activado, cuando un usuario hace clic en el botón, la aplicación solicita confirmación para finalizar la sesión. Cuando se confirma, el explorador borra todos los datos de exploración y vuelve a la dirección URL predeterminada.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Creación de un perfil de configuración de red de telefonía móvil eSIM <!-- 2564077 -->
En **Configuración del dispositivo**, puede crear un perfil de red de telefonía móvil eSIM. Puede importar un archivo que contenga códigos de activación de red de telefonía móvil proporcionados por el operador de telefonía móvil. Después, puede implementar estos perfiles en sus dispositivos Windows 10 habilitados para eSIM LTE, como Surface Pro LTE y otros dispositivos compatibles con eSIM.

Compruebe si sus [dispositivos admiten perfiles de eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Se aplica a Windows 10 y versiones posteriores. 




### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Marcado automático de dispositivos Android inscritos mediante Samsung Knox Mobile Enrollment como "corporativos". <!-- 2404851 -->
De forma predeterminada, los dispositivos Android inscritos mediante Samsung Knox Mobile Enrollment ahora se marcan como **corporativos** en **Propiedad del dispositivo**. No es necesario identificar manualmente los dispositivos corporativos mediante IMEI o números de serie antes de realizar la inscripción mediante Knox Mobile Enrollment.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Eliminación en masa de dispositivos en la hoja de dispositivos <!-- 1793693 -->

Ahora puede eliminar varios dispositivos a la vez en la hoja de dispositivos. Elija **Dispositivos** > **Todos los dispositivos** > seleccione los dispositivos que quiere eliminar > **Eliminar**. En el caso de los dispositivos que no se puedan eliminar, se mostrará una alerta.

## <a name="week-of-july-16-2018"></a>Semana del 16 de julio de 2018  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Más oportunidades de sincronización en la aplicación Portal de empresa para Windows  
La aplicación Portal de empresa para Windows ahora permite iniciar una sincronización directamente desde la barra de tareas de Windows y el menú Inicio. Esta característica es especialmente útil si la única tarea es sincronizar los dispositivos y obtener acceso a los recursos corporativos. Para acceder a la nueva característica, haga clic con el botón derecho en el icono de Portal de empresa que está anclado a la barra de tareas o el menú Inicio. En las opciones de menú (también denominada lista de accesos directos), seleccione **Sincronizar este dispositivo**. El Portal de empresa se abrirá en la página **Configuración** e iniciará la sincronización. Para comprobar la nueva funcionalidad, vea [Novedades de la interfaz de usuario](whats-new-app-ui.md).   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Nuevas experiencias de navegación en la aplicación Portal de empresa para Windows  

Ahora al examinar o buscar aplicaciones en la aplicación Portal de empresa para Windows, puede alternar entre la vista **Iconos** existente y la vista **Detalles** recién agregada. En la nueva vista se muestran detalles de la aplicación, como el nombre, el editor, la fecha de publicación y el estado de la instalación.  

La vista **Instaladas** de la página **Aplicaciones** permite ver detalles sobre las instalaciones de aplicaciones completadas y en curso. Para ver el aspecto de la vista nueva, vea [Novedades de la interfaz de usuario](whats-new-app-ui.md).  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Mejora de la experiencia en la aplicación Portal de empresa para administradores de inscripciones de dispositivos  
Cuando un administrador de inscripciones de dispositivos (DEM) inicia sesión en la aplicación Portal de empresa para Windows, ahora la aplicación solo mostrará el dispositivo en ejecución actual de DEM. Esta mejora reducirá los tiempos de espera que se producían anteriormente cuando la aplicación intentaba mostrar todos los dispositivos inscritos en DEM.  


## <a name="week-of-july-9-2018"></a>Semana del 9 de julio de 2018

### <a name="app-management"></a>Administración de aplicaciones

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloqueo del acceso a aplicaciones según proveedores y modelos de dispositivos no aprobados <!-- 1425689 ! -->
El administrador de TI de Intune puede aplicar una lista específica de fabricantes de dispositivos Android o modelos de iOS a través de las directivas de Intune App Protection. El administrador de TI puede brindar una lista de fabricantes separados por punto y coma para las directivas Android y los modelos de dispositivo para las directivas iOS. Las directivas de Intune App Protection solo son para Android e iOS. Se pueden realizar dos acciones independientes en esta lista especificada:
- Bloquear el acceso a la aplicación en dispositivos no especificados.
- O bien, borrar de manera selectiva los datos corporativos en dispositivos no especificados. 

El usuario no podrá acceder a la aplicación de destino si no se cumplen los requisitos que establece la directiva. En función de la configuración, se podrá bloquear al usuario o borrar de manera selectiva sus datos corporativos dentro de la aplicación. En dispositivos iOS, esta característica requiere el uso de ciertas aplicaciones (como WXP, Outlook, Managed Browser o Yammer) para integrar Intune APP SDK para que esta característica se aplique en las aplicaciones de destino. Esta integración se produce de manera gradual y depende de los equipos de la aplicación específica. En Android, esta característica requiere la versión más reciente de Portal de empresa. 

En dispositivos de usuario final, el cliente de Intune actúa en función de una coincidencia simple de las cadenas especificadas en la hoja de Intune para directivas de protección de aplicaciones. Esto depende por completo del valor que informa el dispositivo. Por lo tanto, se recomienda que el administrador de TI se asegure de que el comportamiento previsto sea preciso. Para ello, pruebe esta configuración en función de una variedad de fabricantes de dispositivos y de modelos dirigidos a un grupo de usuarios pequeño. En Microsoft Intune, seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones** para ver y agregar directivas de protección de aplicaciones. Para obtener más información sobre las directivas de protección de aplicaciones, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) y [Borrar los datos de forma selectiva mediante acciones de acceso de la directiva de protección de aplicaciones en Intune](app-protection-policies-access-actions.md).

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Acceso a la compilación de versión preliminar del Portal de empresa de macOS <!-- 1734766 -->
Con Microsoft AutoUpdate, puede registrarse para recibir antes las compilaciones si se une al programa Insider. El registro le permite usar el Portal de empresa actualizado antes de que esté disponible para los usuarios finales. Para obtener más información, vea el [blog de Microsoft Intune](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

## <a name="week-of-july-2-2018"></a>Semana del 2 de julio de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>Supervisar el estado de configuración de aplicaciones iOS por dispositivo <!-- 880037 -->
Como administrador de Microsoft Intune, puede supervisar el estado de configuración de aplicaciones iOS para cada dispositivo administrado. Desde **Microsoft Intune** en Azure Portal, seleccione **Dispositivos** > **Todos los dispositivos**. En la lista de dispositivos administrados, seleccione un dispositivo específico para mostrar una hoja para el dispositivo. En la hoja del dispositivo, seleccione **Configuración de aplicaciones**.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>Acceso a acciones para las directivas de protección de aplicaciones <!-- 1483510 -->
Puede configurar directivas de protección de aplicaciones para borrar, bloquear o advertir de forma expresa los dispositivos que no cumplan directivas. La acción *borrado* quita los datos corporativos de su empresa de un dispositivo. Si se lleva a cabo esta acción, el usuario del dispositivo recibe una notificación sobre el motivo del borrado y los pasos para corregirlo. En el caso de algunas configuraciones, como la versión mínima de SO, podrá aplicar varias acciones, como el bloqueo o el borrado. Cabe reseñar que estas acciones se desencadenan cuando la aplicación se inicia.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Borrado selectivo de datos de aplicaciones de la organización <!-- 1507030 -->
Ahora, los administradores pueden configurar un borrado selectivo de los datos de la organización como una nueva acción cuando no se cumplan las condiciones de Configuración de acceso de las Directivas de protección de aplicaciones (APP).  Mediante esta característica, los administradores podrán proteger y eliminar automáticamente datos confidenciales de la organización en las aplicaciones, en función de criterios configurados previamente.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Revocar una aplicación iOS adquirida a través de PCV <!-- 1777384 -->
Como administrador de Microsoft Intune, puede revocar todas las licencias de una determinada aplicación iOS adquirida a través del Programa de Compras por Volumen de Apple (VPP). Puede notificar a los usuarios cuando una aplicación con licencia de usuario ya no esté asignada a ellos. Revocar una licencia de aplicación no desinstalará la aplicación VPP desde el dispositivo. Para desinstalar una aplicación VPP, debe cambiar la acción de asignación a **Desinstalar**. El número de licencias reclamadas se indicará en el nodo **Aplicaciones con licencia** en la carga de trabajo **Aplicación** de Intune. Para más información relacionada con las aplicaciones iOS de PCV, vea [How to manage iOS apps purchased through a volume-purchase program with Microsoft Intune](vpp-apps-ios.md) (Administración de aplicaciones iOS adquiridas a través de un Programa de Compra de Licencias por Volumen con Microsoft Intune).

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Actualizaciones en los mensajes de no conformidad en la aplicación Portal de empresa <!-- 1832222 -->
Hemos revisado los mensajes que ven los usuarios cuando un dispositivo no es conforme. Estos mensajes conservan su significado original, pero se han actualizado con un lenguaje más descriptivo y menos jerga técnica. También se han actualizado los vínculos a la documentación y los pasos de corrección para mantenerlos actualizados.
Los textos siguientes son un ejemplo de las mejoras que verá en los mensajes:
- **Antes**: *este dispositivo no ha contactado con el servicio de Intune en el período de tiempo especificado que requiere el administrador de TI. Para resolver este problema, abra la aplicación de Portal de empresa en el dispositivo y haga clic en el botón Comprobar cumplimiento.*
- **Después**: *hace tiempo que el dispositivo no se registra en la organización. Para volver a establecer una conexión, abra la aplicación de Portal de empresa en el dispositivo y pulse en Comprobar configuración del dispositivo.*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>Revocar licencias de aplicaciones iOS de PCV<!-- 1863797 -->
Como administrador, puede recuperar la licencia de una aplicación iOS de VPP asignada a un usuario o un dispositivo. Al desinstalar una aplicación iOS de PCV, también podrá recuperar la licencia de la aplicación. Antes de desinstalar la aplicación, hay que quitar el usuario o el dispositivo del grupo al que se destina la aplicación. Al quitarlos, se evita que la aplicación vuelva a instalarse. Tras completar estos pasos, puede optar por asignar la licencia de la aplicación a otro usuario o dispositivo. Para más información sobre las licencias de aplicaciones iOS de PCV, vea [Manage iOS volume-purchased apps in Microsoft Intune](vpp-apps-ios.md) (Administración de aplicaciones iOS compradas por volumen en Microsoft Intune).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Selección de las categorías de dispositivos mediante el valor de configuración Obtener acceso a trabajo o escuela <!-- 1058963 eenotready --> 
Si ha habilitado la [asignación de grupos de dispositivos](https://docs.microsoft.com/intune/device-group-mapping), ahora se pedirá a los usuarios de Windows 10 que seleccionen una categoría de dispositivo después de la inscripción a través del botón **Conectar** en **Configuración** > **Cuentas** > **Obtener acceso a trabajo o escuela**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Usar sAMAccountName como nombre de usuario de cuenta para perfiles de correo electrónico <!-- 1500307 -->
Puede usar el nombre local **sAMAccountName** como nombre de usuario de cuenta de los perfiles de correo electrónico para Android, iOS y Windows 10. También puede obtener el dominio de los atributos `domain` o `ntdomain` en Azure Active Directory (Azure AD). O si lo prefiere, podrá especificar un dominio estático personalizado.

Para usar esta característica, debe sincronizar el atributo `sAMAccountName` desde el entorno de Active Directory local con Azure AD.

Se aplica a [Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 y versiones posteriores](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Ver perfiles de configuración de dispositivos en conflicto <!-- 1556983 -->
En **Configuración del dispositivo**, se muestra una lista de los perfiles existentes. Con esta actualización, se agrega una nueva columna que proporciona información detallada sobre los perfiles que tienen un conflicto. Puede seleccionar una fila en conflicto para ver la configuración y el perfil que tiene el conflicto. 

Obtenga más información sobre cómo [administrar perfiles de configuración](device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Nuevo estado para dispositivos en la conformidad de dispositivos <!-- 2308882 -->
En **Conformidad de dispositivos** > **Directivas** > seleccione una directiva > **Información general**, se han agregado los estados nuevos siguientes:
- Correcto
- error
- Conflicto
- pendiente
- No aplicable: una imagen que también muestra el número de dispositivos de una plataforma diferente. Por ejemplo, si está buscando un perfil de iOS, el nuevo icono muestra el número de dispositivos que no son de iOS que también están asignados a este perfil. Vea [Directivas de cumplimiento de dispositivos](compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Conformidad de dispositivos compatible con soluciones antivirus de terceros <!-- 2325484 -->
Cuando se crea una directiva de cumplimiento del dispositivo (**Cumplimiento del dispositivo** > **Directivas** > **Crear directiva** > **Plataforma: Windows 10 y versiones posteriores** > **Configuración** > **Seguridad del sistema**), hay nuevas opciones de **[Seguridad del dispositivo](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)**: 
- **Antivirus**: cuando se establece en **Requerir**, puede comprobar el cumplimiento mediante soluciones antivirus registradas con Windows Security Center, como Symantec y Windows Defender. 
- **Antispyware**: cuando se establece en **Requerir**, puede comprobar el cumplimiento mediante soluciones antispyware registradas con Windows Security Center, como Symantec y Windows Defender. 

Se aplica a: Windows 10 y versiones posteriores 

### <a name="device-enrollment"></a>Inscripción de dispositivos

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Dispositivos sin columna de perfiles en la lista de tokens del programa de inscripción <!-- 1853904 -->
En la lista de tokens del programa de inscripción hay una nueva columna que muestra el número de dispositivos sin un perfil asignado. Esto ayuda a los administradores a asignar perfiles a estos dispositivos antes de entregarlos a los usuarios. Para ver la nueva columna, vaya a **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción**.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Cambio de nombre en Google para Android for Work y Play for Work <!--842873 -->
Intune ha actualizado el término "Android for Work" para reflejar los cambios de personalización de marca de Google. Ya no se usan los términos "Android for Work" ni "Play for Work". Se usa otra terminología en función del contexto:
- "Android Enterprise" hace referencia a la pila de administración general de Android moderna.
- "Perfil de trabajo" o "Propietario de perfil" hacen referencia a dispositivos BYOD administrados con perfiles de trabajo.
- "Google Play administrada" hace referencia a la tienda de aplicaciones de Google.

#### <a name="rules-for-removing-devices----1609459---"></a>Reglas para quitar dispositivos <!-- 1609459 -->
Hay disponibles nuevas reglas que permiten quitar automáticamente dispositivos que no se hayan protegido durante un número de días que establezca. Para ver la nueva regla, vaya al panel **Intune**, seleccione **Dispositivos** y, luego, **Reglas de limpieza de dispositivos**.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Compatibilidad con dispositivos Android de un solo uso y propiedad corporativa <!-- 1630973 -->

Ahora, Intune admite dispositivos Android de estilo quiosco, que estén bloqueados y con una elevada administración. De este modo, los administradores pueden bloquear aún más el uso de un dispositivo para restringir su uso a una sola aplicación o un pequeño conjunto de aplicaciones, impidiendo así que los usuarios habiliten otras aplicaciones o realicen otras acciones en el dispositivo. Para configurar el quiosco de Android, vaya a Intune > **Inscripción de dispositivos** > **Inscripción de Android** > **Inscripciones de dispositivos de tareas y quiosco**. Para obtener más información, vea [Set up enrollment of Android enterprise kiosk devices](android-kiosk-enroll.md) (Configurar la inscripción de dispositivos de quiosco de Android Enterprise).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Revisión por fila de los identificadores de dispositivos corporativos duplicados cargados <!-- 2203794-->
Ahora, al cargar identificadores corporativos, Intune facilita una lista de cualquier dispositivo duplicado y ofrece la posibilidad de reemplazar o conservar la información existente. El informe se mostrará si hay duplicados después de elegir **Inscripción de dispositivos** > **Identificadores de dispositivos corporativos** > **Agregar identificadores**. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Agregar manualmente identificadores de dispositivos corporativos <!-- 2203803 -->
Ahora puede agregar manualmente identificadores de dispositivos corporativos. Elija **Inscripción de dispositivos** > **Identificadores de dispositivos corporativos** > **Agregar**. 

## <a name="week-of-june-25-2018"></a>Semana del 25 de junio de 2018

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo, nuevo colaborador de Mobile Threat Defense <!-- 1169249 -->

Puede controlar el acceso desde dispositivos móviles a recursos corporativos en función de la evaluación de riesgos efectuada por Pradeo, una solución de Mobile Threat Defense integrada con Microsoft Intune.

## <a name="week-of-june-18-2018"></a>Semana del 18 de junio de 2018

### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Compatibilidad móvil de Microsoft Edge para directivas de Intune App Protection <!-- 1817882 -->

El navegador Microsoft Edge para dispositivos móviles ahora admite las directivas de protección de aplicaciones definidas en Intune.

## <a name="week-of-june-11-2018"></a>Semana del 11 de junio de 2018

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Uso del modo FIPS con el conector de certificado NDES <!-- 1333688 -->
Al instalar el conector de certificado NDES en un equipo con el modo Estándar federal de procesamiento de información (FIPS) habilitado, la emisión y revocación de certificados no funciona según lo previsto. Con esta actualización, con el conector de certificado NDES se incluye la compatibilidad con FIPS. 

Esta actualización también incluye:

- El conector de certificado NDES requiere .NET 4.5 Framework, que se incluye automáticamente con Windows Server 2016 y Windows Server 2012 R2. Anteriormente, .NET 3.5 Framework era la versión mínima requerida.
- Con el conector de certificado NDES se incluye la compatibilidad con TLS 1.2. Por tanto, si el servidor con el conector de certificado NDES instalado es compatible con TLS 1.2, entonces se usará TLS 1.2. Si el servidor no admite TLS 1.2, entonces se usará TLS 1.1. Actualmente, se usa TLS 1.1 para la autenticación entre los dispositivos y el servidor.

Para obtener más información, vea [Configuración y uso de certificados SCEP](certificates-scep-configure.md) y [Configuración y uso de certificados PKCS](certficates-pfx-configure.md).

## <a name="week-of-june-4-2018"></a>Semana del 4 de junio de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Recuperación del identificador de modelo de usuario de la aplicación (AUMID) asociado para aplicaciones de Microsoft Store para Empresas en pantalla completa <!-- 1560077 ! -->
Intune ya puede recuperar los identificadores de modelo de usuario de la aplicación (AUMID) para aplicaciones de Microsoft Store para Empresas (WSfB) con el fin de mejorar la configuración del perfil de quiosco.

Para más información sobre las aplicaciones de Microsoft Store para Empresas, consulte el artículo sobre la [administración de aplicaciones de Microsoft Store para Empresas](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Nueva página de personalización de marca del Portal de empresa <!-- 1916370 -->
La página de personalización de marca del Portal de empresa tiene un nuevo diseño, mensajes e información sobre herramientas.


### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Compatibilidad con perfiles de VPN de Palo Alto Networks GlobalProtect <!-- 1333680 ! -->
Con esta actualización, puede elegir Palo Alto Networks GlobalProtect como un tipo de conexión VPN para perfiles de VPN en Intune (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Tipo de perfil** > **VPN**). En esta versión, se admiten las siguientes plataformas: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Adiciones a la configuración de opciones de seguridad del dispositivo local <!-- 1403702 -->
Ya puede configurar opciones adicionales de seguridad del dispositivo local para dispositivos con Windows 10. Las opciones adicionales están disponibles en las áreas Cliente de redes de Microsoft, Servidor de red Microsoft, Acceso y seguridad de red e Inicio de sesión interactivo. Encuentre estos valores en la categoría de Endpoint Protection cuando cree una directiva de configuración de dispositivo de Windows 10.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Habilitación de la pantalla completa en dispositivos Windows 10 <!-- 1560072 ! -->
En los dispositivos Windows 10, puede crear un perfil de configuración y habilitar la pantalla completa (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Windows 10** > **Restricciones de dispositivos** > **Quiosco**). En esta actualización, la configuración **Quiosco (versión preliminar)** cambia de nombre a **Quiosco (obsoleto)**. Ya no se recomienda usar **Quiosco (obsoleto)**, pero seguirá funcionando hasta la actualización de julio. El nuevo tipo de perfil **Quiosco** reemplaza a **Quiosco (obsoleto)** (**Crear perfil** > **Windows 10** > **Quiosco (versión preliminar)**), que contendrá los valores para configurar Quioscos en Windows 10 RS4 y versiones posteriores.

Se aplica a Windows 10 y versiones posteriores.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Vuelve el gráfico de usuario del perfil del dispositivo <!-- 2160133 -->
Si bien mejoraba el valor numérico que aparece en el gráfico del perfil del dispositivo (**Configuración de dispositivos** > **Perfiles** > seleccione un perfil existente > **Información general**), el gráfico de usuario se quitó de manera temporal.

Con esta actualización, dicho gráfico vuelve y aparece en Azure Portal.

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>Compatibilidad con la inscripción de Windows Autopilot sin autenticación de usuario <!-- 1165118 -->
Intune admite la inscripción de Windows Autopilot sin autenticación de usuario. Se trata de una nueva opción en el perfil de implementación de Windows Autopilot "Modo de implementación Autopilot" establecido en "Self-Deploying" (Autoimplementable).  El dispositivo debe ejecutar Windows 10 Insider Preview, compilación 17672 o posterior, y poseer un chip de TPM 2.0 para completar correctamente este tipo de inscripción. Puesto que no se requiere ninguna autenticación de usuario, solo puede asignar esta opción a dispositivos sobre los que tenga control físico.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Nueva configuración de idioma y región al realizar la configuración rápida de Autopilot <!-- 1821766 -->
Hay disponible una nueva configuración para establecer el idioma y la región de los perfiles de Autopilot durante la configuración rápida. Para ver la nueva configuración, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Implementación perfiles** > **Crear perfil** > **Modo de implementación** = **Self-deploying (Autoimplementable)** > **Valores predeterminados configurados**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nuevo valor para configurar el teclado del dispositivo <!-- 1821768 -->
Habrá disponible un valor nuevo para configurar el teclado de los perfiles de Autopilot durante la configuración rápida. Para ver la nueva configuración, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Implementación perfiles** > **Crear perfil** > **Modo de implementación** = **Self-deploying (Autoimplementable)** > **Valores predeterminados configurados**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Los perfiles AutoPilot se migran a un destinatario de grupo <!-- 1877935 -->
Se pueden asignar perfiles de implementación de AutoPilot a grupos de Azure AD que contengan dispositivos AutoPilot.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="set-compliance-by-device-location----851881----"></a>Establecimiento del cumplimiento por ubicación del dispositivo <!-- 851881 ! -->
En algunas situaciones, es posible que desee restringir el acceso a los recursos corporativos a una ubicación específica, definida por una conexión de red. Ya puede crear una directiva de cumplimiento (**Cumplimiento de dispositivos** > **Ubicaciones**) en función de la dirección IP del dispositivo. Si el dispositivo sale del intervalo IP, no podrá acceder a los recursos corporativos.

Se aplica a: Solo para dispositivos Android 6.0 y versiones posteriores, con la aplicación Portal de empresa actualizada.

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Evitar aplicaciones y experiencias de consumidor en dispositivos Windows 10 Enterprise RS4 Autopilot<!-- 1621980 -->
Puede evitar la instalación de aplicaciones y experiencias de consumidor en los dispositivos Windows 10 Enterprise RS4 Autopilot. Para ver esta característica, vaya a **Intune** > **Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Plataforma** = **Windows 10 o versiones posteriores** > **Tipo de perfil** = **Restricciones de dispositivo** > **Configurar** > **Windows Spotlight** > **Características de consumidor**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Desinstalar las últimas actualizaciones de software de Windows 10 <!-- 1732948 -->
En caso de que detecte un problema importante en las máquinas con Windows 10, puede optar por desinstalar (revertir) la última actualización de características o la última actualización de calidad. La desinstalación de una actualización de característica o de calidad solo está disponible para el canal de servicio en el que se encuentra el dispositivo. La desinstalación desencadenará una directiva para restaurar la actualización anterior en las máquinas con Windows 10. Para las actualizaciones de características concretamente, puede limitar el tiempo de 2 a 60 días durante el cual se puede aplicar una desinstalación de la versión más reciente. Para configurar las opciones de desinstalación de actualización de software, seleccione **Actualizaciones de software** en la hoja **Microsoft Intune** en el portal de Azure. Después, seleccione **Anillos de actualización de Windows 10** en la hoja **Actualizaciones de software**. Elija después la opción **Desinstalar** en la sección **Información general**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Buscar IMEI y número de serie en todos los dispositivos <!-- 1793685 -->
Ya puede buscar IMEI y los números de serie en la hoja Todos los dispositivos (correo electrónico, UPN, nombre de dispositivo y nombre de la administración siguen estando disponibles). En Intune, elija **Dispositivos** > **Todos los dispositivos** y escriba la búsqueda en el cuadro de búsqueda.

#### <a name="management-name-field-will-be-editable----1875989---"></a>El campo de nombre de administración se podrá editar <!-- 1875989 -->
Ya puede editar el campo de nombre de administración en la hoja **Propiedades** de un dispositivo. Para editar este campo, elija **Dispositivos** > **Todos los dispositivos** > elija el dispositivo > **Propiedades**. Puede usar el campo de nombre de administración para identificar un dispositivo de manera única.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Nuevo filtro Todos los dispositivos: Categoría de dispositivo <!-- 1878520 -->
Ya puede filtrar la lista **Todos los dispositivos** por categoría de dispositivo. Para ello, elija **Dispositivos** > **Todos los dispositivos** > **Filtro** > **Categoría de dispositivo**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Use TeamViewer para compartir la pantalla de dispositivos iOS y MacOS <!-- 1985547 -->
Los administradores podrán conectarse a [TeamViewer](device-profile-android-teamviewer.md) e iniciar una sesión de uso compartido de pantalla con dispositivos iOS y macOS. Los usuarios de iPhone, iPad y macOS pueden compartir sus pantallas en vivo con cualquier otro dispositivo móvil o de escritorio. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Compatibilidad con múltiples instancias de Exchange Connector <!-- 2070451 -->
Ya no estará limitado a una instancia de Microsoft Intune Exchange Connector por inquilino. Intune admite varias instancias de Exchange Connector para que pueda configurar el acceso condicional de Intune con varias organizaciones de Exchange local.

Con un conector de Exchange local de Intune, se puede controlar el acceso de los dispositivos a los buzones de Exchange locales en función de si un dispositivo está inscrito en Intune y cumple con las directivas de cumplimiento de dispositivos de Intune. Para configurar un conector, descargue el conector de Exchange local de Intune desde Azure Portal e instálelo en un servidor en la organización de Exchange. En el panel de Microsoft Intune, elija **Acceso local** y, después, en **Instalación**, elija **Conector de Exchange ActiveSync**. Descargue el conector de Exchange local e instálelo en un servidor en la organización de Exchange. Ahora que ya no está limitado a un conector de Exchange por inquilino, si tiene otras organizaciones de Exchange, puede seguir el mismo proceso para descargar e instalar un conector para cada organización de Exchange adicional.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Nuevos detalles de hardware de dispositivo: CCID <!-- 2156657 -->
La información de dispositivo de interfaz de tarjeta de chip (CCID) ya se incluye para cada dispositivo. Para verla, elija **Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Hardware**> compruebe en **Detalles de red**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Asignación de todos los usuarios y dispositivos como grupos de ámbito <!-- 2196803 -->
Podrá asignar todos los usuarios, todos los dispositivos y todos los usuarios y dispositivos en los grupos de ámbito. Para ello, elija **Roles de Intune** > **Todos los roles** > **Policy and profile manager (Administrador de directivas y perfiles)** > **Asignaciones**  > elija una asignación > **Ámbito (grupos)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>La información de UDID ahora se incluye para dispositivos iOS y macOS <!-- 2219806 -->
Para ver el identificador único de dispositivo (UDID) para dispositivos iOS y macOS, vaya a **Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Hardware**. UDID solo está disponible para dispositivos corporativos, tal y como se configura en **Dispositivos** > **Todos los dispositivos** > dispositivo > **Propiedades** > **Propiedad del dispositivo**.

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Solución de problemas mejorada para la instalación de aplicaciones <!-- 928990 -->
En algunas ocasiones, las instalaciones de aplicaciones en los dispositivos administrados por MDM de Microsoft Intune pueden presentar errores. Cuando esto ocurre, puede ser complicado entender el motivo del error o cómo solucionarlo. Incluimos una Versión preliminar pública de las características de solución de problemas de las aplicaciones. Verá un nodo nuevo bajo cada dispositivo individual denominado **Aplicaciones administradas**. En él aparecen las aplicaciones que se han entregado a través de MDM de Intune. Dentro del nodo, verá una lista de los estados de instalación de las aplicaciones. Si selecciona una aplicación individual, aparecerá la vista de solución de problemas de esa aplicación específica. En la vista de solución de problemas, verá el ciclo de vida completo de la aplicación, como cuándo se creó y modificó la aplicación, el momento en que se estableció su destino y cuándo se entregó a un dispositivo. Además, si la instalación de la aplicación no se realizó correctamente, verá el código de error y un mensaje útil sobre la causa del mismo. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Directivas de protección de aplicaciones de Intune y Microsoft Edge <!-- 1818968 -->
El explorador Microsoft Edge para dispositivos móviles (iOS y Android) ahora admite las directivas de protección de aplicaciones Microsoft Intune. Intune protegerá a los usuarios de dispositivos iOS y Android que inicien sesión con sus cuentas corporativas de Azure AD en la aplicación Edge. En dispositivos iOS, la directiva **Require managed browser for web content** (Requerir explorador administrado para contenido web) permitirá a los usuarios abrir vínculos en Microsoft Edge cuando esté administrado.

## <a name="week-of-may-14-2018"></a>Semana del 14 de mayo de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Exigencia de instalación de perfiles de directivas, aplicaciones, certificados y red <!-- 1553555 -->

Los administradores pueden evitar que los usuarios finales accedan al escritorio de Windows 10 RS4 hasta que Intune instale los perfiles de red y certificado, las aplicaciones y las directivas durante el aprovisionamiento de dispositivos AutoPilot. Para obtener más información, consulte [Configurar una página de estado de inscripción](windows-enrollment-status.md).

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Configurar las directivas de protección de aplicaciones <!-- 2144597 Part 2 -->

En Azure Portal, en lugar de dirigirse a la hoja del servicio Intune App Protection, solo tiene que ir a Intune. Ahora hay una única ubicación para las directivas de protección de aplicaciones en Intune. Tenga en cuenta que todas las directivas de protección de aplicaciones se encuentran en la hoja **Aplicación móvil** de Intune, en **Directivas de protección de aplicaciones**. Esta integración ayuda a simplificar la administración en la nube. Recuerde que todas las directivas de protección de aplicaciones ya están en Intune y que puede modificar cualquiera de las directivas configuradas anteriormente. Las directivas de protección de aplicaciones (APP) y acceso condicional (CA) de Intune se encuentran ahora en **Acceso condicional**, que se encuentra en la sección **Administrar** de la hoja **Microsoft Intune** o en la sección **Seguridad** de la hoja **Azure Active Directory**. Para obtener más información sobre cómo modificar directivas de acceso condicional, vea [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Para obtener más información, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>Semana del 7 de mayo de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Compatibilidad con Samsung Knox Mobile Enrollment <!--1112863-->

Al usar Intune con Samsung Knox Mobile Enrollment (KME), puede inscribir un gran número de dispositivos Android propiedad de la empresa. Los usuarios en redes Wi-Fi o de telefonía móvil se pueden inscribir con unas pocas pulsaciones al encender sus dispositivos por primera vez. Con la aplicación de implementación Knox, los dispositivos se pueden inscribir mediante Bluetooth o NFC. Para más información, vea [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Inscripción automática de dispositivos Android mediante Samsung Knox Mobile Enrollment).

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Solicitar ayuda en el Portal de empresa para Windows 10 <!-- 1874137 -->

El Portal de empresa para Windows 10 ahora enviará registros de aplicaciones directamente a Microsoft cuando el usuario inicie el flujo de trabajo para obtener ayuda con un problema. Esto permitirá que sea más fácil solucionar los problemas que se envían a Microsoft.

## <a name="week-of-april-23-2018"></a>Semana del 23 de abril de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Compatibilidad de código de acceso con el PIN de MAM en Android<!-- 1438086 -->

Los administradores de Intune pueden establecer un requisito de inicio de aplicación para exigir un código de acceso en lugar de un PIN numérico de MAM. Si se configura, se le pide al usuario que establezca y use un código de acceso cuando se le solicite antes de obtener acceso a aplicaciones habilitadas para MAM. Un código de acceso se define como un PIN numérico con al menos un carácter especial o un carácter alfabético en mayúsculas/minúsculas. Intune admite un código de acceso de forma similar al PIN numérico existente... puede establecer una longitud mínima y permite la repetición de caracteres y secuencias en la consola de administración. Esta característica requiere la versión más reciente del Portal de empresa en Android. Esta característica ya está disponible para iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Compatibilidad con aplicaciones de línea de negocio (LOB) para macOS <!-- 1473977 -->
Microsoft Intune proporciona la capacidad de instalar aplicaciones LOB de macOS desde Azure Portal. Se puede agregar una aplicación LOB de macOS a Intune una vez procesada por la herramienta disponible en GitHub. En Azure Portal, seleccione **Aplicaciones cliente** en la hoja **Intune**. En la hoja **Aplicaciones cliente**, elija **Aplicaciones** > **Agregar**. En la hoja **Agregar aplicación**, seleccione **Aplicación de línea de negocio**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>Todos los usuarios y todos los grupos de dispositivos integrados para la asignación de aplicaciones de perfil de trabajo de Android Enterprise <!-- 1813073 -->
Puede aprovechar los grupos integrados **Todos los usuarios** y **Todos los dispositivos** para la asignación de aplicaciones de perfil de trabajo de Android Enterprise. Para obtener más información, vea [Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune volverá a instalar las aplicaciones necesarias desinstaladas por los usuarios <!-- 1947010 -->
Si un usuario final desinstala una aplicación requerida, Intune la reinstala de forma automática antes de que transcurran 24 horas en lugar de esperar al ciclo de reevaluación de siete días.

### <a name="device-configuration"></a>Configuración de los dispositivos

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>El gráfico de perfiles de dispositivos y la lista de estado muestran todos los dispositivos de un grupo <!-- 1449153 -->
Al configurar un perfil de dispositivo (**Configuración del dispositivo** > **Perfiles**), elija el perfil del dispositivo, por ejemplo, iOS. Este perfil se asigna a un grupo que incluye los dispositivos iOS y los dispositivos que no son iOS. El recuento del gráfico muestra que el perfil se aplica a dispositivos iOS *y* no iOS (**Configuración del dispositivo** > **Perfiles** > seleccionar un perfil existente > **Información general**). Cuando se selecciona el gráfico en la pestaña **Información general**, el **Estado del dispositivo** enumera todos los dispositivos del grupo, en lugar de solo los dispositivos iOS. 

Con esta actualización, el gráfico (**Configuración del dispositivo** > **Perfiles** > seleccionar un perfil existente > **Información general**) solo muestra el recuento del perfil de dispositivo determinado. Por ejemplo, si el perfil de dispositivo de configuración se aplica a dispositivos iOS, el gráfico muestra solo el número de dispositivos iOS. Al seleccionar el gráfico y abrir **Estado del dispositivo**, solo se muestran los dispositivos iOS.

Mientras se realiza esta actualización, se quita temporalmente el gráfico de usuario. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>VPN de Always On para Windows 10 <!--1333666 -->

Actualmente, [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) puede usarse en dispositivos Windows 10 mediante un perfil de red privada virtual (VPN) personalizado creado con OMA-URI.

Con esta actualización, los administradores pueden habilitar Always On para perfiles de VPN de Windows 10 directamente en Intune en Azure Portal. Los perfiles VPN de Always On se conectarán automáticamente cuando:

- Los usuarios inicien sesión en sus dispositivos
- La red del dispositivo cambie
- La pantalla del dispositivo se vuelva a activar después de haberse desactivado

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nueva configuración de impresora para perfiles de educación <!-- 1308900 -->

Para los perfiles de educación, hay nuevos valores de configuración disponibles en la categoría **Impresoras**: **Impresoras**, **Impresora predeterminada**, **Agregar nuevas impresoras**.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>Mostrar el identificador de llamada en el perfil personal: perfil de trabajo de Android Enterprise <!--1098984 -->
Al usar un perfil personal en un dispositivo, es posible que los usuarios finales no vean los detalles del identificador del autor de la llamada de un contacto de trabajo. 

Con esta actualización, hay una nueva opción en **Android Enterprise** > **Restricciones de dispositivos** > **Configuración del perfil de trabajo**:
- Mostrar el identificador de llamada de contacto profesional en el perfil personal

Cuando se habilita (sin configurar), se muestran los detalles del autor de la llamada del contacto en el perfil personal. Cuando se bloquea, no se muestra el número del autor de la llamada del contacto en el perfil personal. 

Se aplica a: Dispositivos de perfil de trabajo Android con la versión del sistema operativo Android 6.0 y versiones más recientes

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nueva configuración de Credential Guard de Windows Defender agregada a la configuración de Endpoint Protection <!--1102252 --><!--from 1802 and 1804-->

Con esta actualización, [Credential Guard de Windows Defender](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configuración de dispositivos** > **Perfiles** > **Endpoint Protection**) incluye la siguiente configuración: 

- **Credential Guard de Windows Defender**: activa Credential Guard con seguridad basada en virtualización. Habilitar esta característica ayuda a proteger las credenciales en el siguiente reinicio cuando las opciones **///Platform Security Level with Secure Boot** (Nivel de seguridad de plataforma con arranque seguro) y **///Virtualization Based Security** (Seguridad basada en virtualización) are están ambas habilitadas. Las opciones son:
  - **Deshabilitado**: si Credential Guard se activó anteriormente con la opción **Habilitar sin bloqueo**", entonces Credential Guard se desactiva de forma remota.

  - **Habilitado con el bloqueo UEFI**: garantiza que Credential Guard no se puede deshabilitar mediante una clave de Registro o por medio de la directiva de grupo. Para deshabilitar Credential Guard después de usar esta opción, debe establecer la directiva de grupo en "Deshabilitado". A continuación, quite la funcionalidad de seguridad de cada equipo, con un usuario físicamente presente. Estos pasos borrar la configuración almacenada en UEFI. Mientras se conserve la configuración de UEFI, Credential Guard estará habilitado.

  - **Habilitar sin bloqueo**: permite deshabilitar Credential Guard de forma remota mediante la directiva de grupo. Los dispositivos que usen esta configuración deben ejecutar al menos Windows 10 (versión 1511).

Las siguientes tecnologías dependientes se habilitan automáticamente al configurar Credential Guard: 

  - **Enable Virtualization-based Security (VBS)** (Habilitar la seguridad basada en la virtualización [VBS]): activa la seguridad basada en la virtualización (VBS) en el siguiente reinicio. La seguridad basada en la virtualización emplea el hipervisor de Windows para proporcionar compatibilidad con servicios de seguridad, y requiere arranque seguro.
  - **Secure Boot with Direct Memory Access (DMA)** (Arranque seguro con acceso directo a memoria [DMA]): activa VBS con arranque seguro y acceso directo a memoria. La protección de DMA requiere compatibilidad con el hardware y solo se habilita en los dispositivos configurados correctamente. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Usar un nombre de firmante personalizado en certificado SCEP <!-- 2064190 -->
Puede usar el nombre común **OnPremisesSamAccountName** de un sujeto personalizado en un perfil de certificado SCEP. Por ejemplo, puede usar `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Bloqueo de la cámara y capturas de pantalla en los perfiles de trabajo de Android Enterprise <!-- 1098977 -->
Hay dos nuevas propiedades disponibles para bloquear al configurar restricciones de dispositivo para dispositivos Android: 
- Cámara: bloquea el acceso a todas las cámaras en el dispositivo.
- Captura de pantalla: bloquea la captura de pantalla y además evita que el contenido se muestre en los dispositivos de pantalla que no tengan una salida de vídeo segura.

Se aplica a los perfiles de trabajo de Android Enterprise.


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nuevos pasos de inscripción para los usuarios en dispositivos con macOS High Sierra 10.13.2+ <!--1734567 -->
macOS high Sierra 10.13.2 presentó el concepto de inscripción de inscripción de MDM "aprobada por el usuario". Las inscripciones aprobadas permiten a Intune administrar algunas configuraciones dependientes de la seguridad. Para obtener más información, vea la documentación de soporte técnico de Apple aquí: https://support.apple.com/HT208019.

Los dispositivos inscritos mediante el Portal de empresa de macOS se consideran "No aprobados por el usuario", a menos que el usuario final abra las preferencias del sistema y los apruebe de forma manual. Así, el Portal de empresa de macOS ahora insta a los usuarios de macOS 10.13.2 y versiones posteriores a aprobar manualmente su inscripción al final del proceso de inscripción. La consola de administración de Intune indicará si un dispositivo inscrito está aprobado por el usuario.



### <a name="device-management"></a>Administración de dispositivos

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>Protección contra amenazas avanzada (ATP) e Intune están totalmente integrados <!-- 1629303 -->

[Protección contra amenazas avanzada (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) muestra el nivel de riesgo de los dispositivos Windows 10. En el Centro de seguridad de Windows Defender (portal de ATP), puede crear una conexión a Microsoft Intune. Una vez creada, se usa una directiva de cumplimiento de Intune para determinar un nivel de amenaza aceptable. Si se supera el nivel de amenaza, una directiva de acceso condicional de Azure Active Directory (AD) puede bloquear el acceso a diferentes aplicaciones dentro de su organización.

Esta característica permite que ATP examine archivos, detecte amenazas y notifique cualquier riesgo en los dispositivos Windows 10.

Consulte [Habilitación de ATP con acceso condicional en Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Compatibilidad con dispositivos sin usuario <!-- 1637553 -->
Intune ofrece la posibilidad de evaluar el cumplimiento en dispositivos sin usuario, como Microsoft Surface Hub. La directiva de cumplimiento puede tener como destino dispositivos concretos. Así, es posible determinar el cumplimiento (y no cumplimiento) de dispositivos sin un usuario asociado.

#### <a name="delete-autopilot-devices----1713650---"></a>Eliminar dispositivos Autopilot <!-- 1713650 -->
Los administradores de Intune pueden [eliminar dispositivos Autopilot](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Experiencia de eliminación de dispositivos mejorada <!--1832333 -->
Ya no se le pide que quite los datos de la empresa o que restablezca el dispositivo a los valores de fábrica para [eliminar un dispositivo de Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Para ver la nueva experiencia, inicie sesión en Intune y seleccione **Dispositivos** > **Todos los dispositivos** > el nombre del dispositivo > **Eliminar**.

Si todavía quiere confirmar el borrado o eliminación, puede usar la ruta de ciclo de vida de dispositivo estándar al usar **Eliminar datos de la compañía** y **Restablecimiento de fábrica** antes de **Eliminar**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Reproducir sonidos en iOS en modo Perdido <!-- 1947769 -->
Cuando los dispositivos iOS supervisados están en el [modo perdido](device-lost-mode.md) de administración de dispositivos móviles (MDM), puede [reproducir un sonido](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Dispositivos** > **Todos los dispositivos** > seleccionar un dispositivo iOS > **Información general** > **Más**). El sonido sigue reproduciéndose hasta que el dispositivo se quita del modo Perdido o un usuario deshabilita el sonido en el dispositivo. Se aplica a dispositivos iOS 9.3 y versiones más recientes.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Bloquear o permitir resultados web en búsquedas realizadas en un dispositivo de Intune <!--1972804-->

Ahora, los administradores pueden bloquear los resultados web en las búsquedas realizadas en un dispositivo.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Mensajes de error mejorados para errores de carga del certificado push MDM de Apple <!-- 2172331 -->

El mensaje de error explica que se debe usar el mismo identificador de Apple al renovar un certificado MDM existente.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Probar el Portal de empresa para macOS en máquinas virtuales <!-- 2216679 -->

Se han publicado instrucciones para ayudar a los administradores de TI a probar la aplicación de Portal de empresa para macOS en máquinas virtuales en Parallels Desktop y VMware Fusion. Encuentre más información en [Inscribir máquinas virtuales macOS para realizar pruebas](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Interfaz de usuario

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Mejora de iconos de dispositivos en el Portal de empresa de Windows 10 <!--2213364 -->

Se han actualizado los iconos para hacerlos más accesibles para los usuarios con deficiencia visual y para que funcionen mejor con las herramientas de lectura de pantalla.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Enviar informes de diagnóstico en la aplicación Portal de empresa para macOS <!-- 2216677 -->
La aplicación Portal de empresa para dispositivos macOS se actualizó para mejorar la forma en que los usuarios notifican errores relacionados con Intune. Desde la aplicación Portal de empresa, los empleados pueden:

- Cargar informes de diagnóstico directamente para el equipo de desarrollo de Microsoft.
- Enviar por correo electrónico un Id. de incidente al equipo de soporte técnico de TI de la empresa.

Para más información, consulte [Envío de errores de macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>Intune se adapta al sistema de diseño fluido de la aplicación Portal de empresa de Windows 10 <!-- 1195010 -->
La aplicación Portal de empresa de Windows 10 se ha actualizado con la [vista de navegación del sistema de diseño fluido](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). En la parte lateral de la aplicación, verá una lista estática vertical de todas las páginas de nivel superior. Haga clic en cualquier vínculo para ver y cambiar entre páginas rápidamente. Esta es la primera de varias actualizaciones que verá como parte de nuestros esfuerzos para crear una experiencia más adaptable, empática y familiar en Intune. Para ver el aspecto actualizado, vaya a [Novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Semana del 16 de abril de 2018

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>Usar el cliente de Cisco AnyConnect para iOS <!-- 1333708 -->

Al crear un nuevo perfil de VPN para iOS, ahora hay dos opciones: **Cisco AnyConnect** y **Cisco Legacy AnyConnect**. Los perfiles de Cisco AnyConnect admiten las versiones 4.0.7x y más recientes. Los perfiles de VPN existentes de Cisco AnyConnect para iOS se etiquetan como **Cisco Legacy AnyConnect**, y siguen funcionando con Cisco AnyConnect 4.0.5x y versiones posteriores, como lo hacen en la actualidad.

> [!NOTE]
> Este cambio sólo se aplica a iOS. Sigue habiendo una única opción de Cisco AnyConnect para perfiles de trabajo de Android y Android Enterprise y las plataformas macOS.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Ahora, los dispositivos macOS inscritos en Jamf se pueden registrar en Intune <!-- 2370684 -->

Las versiones 1.3 y 1.4 del portal de empresa de macOS no registraban correctamente los dispositivos Jamf en Intune. La versión 1.4.2 del portal de macOS corrige este problema.


## <a name="week-of-april-9-2018"></a>Semana del 9 de abril de 2018  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Experiencia de ayuda actualizada en la aplicación Portal de empresa para Android <!-- 1631531 -->

Se ha actualizado la experiencia de ayuda en la aplicación Portal de empresa para Android de acuerdo con los procedimientos recomendados para la plataforma Android. Ahora, cuando los usuarios detectan un problema en la aplicación, pueden pulsar en **Menú** > **Ayuda** y:
- Cargar registros de diagnóstico en Microsoft.
- Enviar un mensaje de correo electrónico que describe el problema y un Id. de incidente a un miembro del equipo de soporte técnico de la empresa.  

Para ver la experiencia de ayuda actualizada, vaya a [Send logs using email](/intune-user-help/send-logs-to-your-it-admin-by-email-android) (Enviar registros por correo electrónico) y [Send errors to Microsoft](/intune-user-help/send-logs-to-microsoft-android) (Enviar errores a Microsoft).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nuevo gráfico de tendencias sobre errores de inscripción y tabla de motivos de error <!-- 1471783 -->

En la página de información general de inscripción, puede ver la tendencia de los errores de inscripción y los cinco motivos de error principales. Al hacer clic en el gráfico o la tabla, puede explorar los detalles para obtener consejos de resolución de problemas y sugerencias de corrección.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Actualización de la ubicación en la que se configuran las directivas de protección de aplicaciones <!-- 2144597 -->

En Azure Portal, dentro del servicio Microsoft Intune, se le va a redirigir de forma temporal desde la hoja del servicio **Intune App Protection** a la hoja **Aplicación móvil**. Tenga en cuenta que todas las directivas de protección de aplicaciones ya se encuentran en la hoja **Aplicación móvil** de Intune, en Configuración de aplicaciones. En lugar de ir a Intune App Protection, simplemente irá a Intune. En abril de 2018, se suspenderá el redireccionamiento y se quitará por completo la hoja del servicio **Intune App Protection**, para que haya una sola ubicación para las directivas de protección de aplicaciones en Intune. 

**¿Cómo me afecta esto a mí?**
Este cambio afectará tanto a los clientes de Intune independientes como a los clientes híbridos (Intune con Configuration Manager). Esta integración le ayudará a simplificar la administración en la nube.

**¿Qué he de hacer para prepararme para este cambio?**
Etiquete **Intune** como favorito en lugar de la hoja del servicio **Intune App Protection** y familiarícese con el flujo de trabajo de directivas de protección de aplicaciones de la hoja **Aplicación móvil** de Intune. Se proporciona el redireccionamiento durante un breve período de tiempo y, después, se elimina la hoja **Intune App Protection**. Recuerde que todas las directivas de protección de aplicaciones ya están en Intune y que puede modificar las directivas de acceso condicional. Para obtener más información sobre cómo modificar directivas de acceso condicional, vea [Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Para obtener más información, vea [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Semana del 2 de abril de 2018

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Actualización de la experiencia del usuario en la aplicación del Portal de empresa para iOS <!--1412866 -->
Se ha lanzado una actualización importante de la experiencia de usuario para la aplicación Portal de empresa para iOS. La actualización incorpora un rediseño visual completo con una apariencia modernizada. Se ha mantenido la funcionalidad de la aplicación, pero se han mejorado la facilidad de uso y la accesibilidad.  

También verá:
- Compatibilidad con iPhone X.
- Inicio de la aplicación y carga de respuestas más rápidos, para ahorrar tiempo a los usuarios.
- Barras de progreso adicionales para proporcionar a los usuarios la información de estado más reciente.
- Mejoras en la forma en que los usuarios cargan registros, de modo que, si hay algún problema, resulte más fácil informar.  

Para ver el aspecto actualizado, vaya a [Novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Protección de los datos locales de Exchange mediante APP y CA de Intune <!-- 1056954 -->
Ahora puede usar directivas de protección de aplicaciones (APP) y acceso condicional (CA) de Intune para proteger el acceso a datos locales de Exchange con Outlook Mobile. Para agregar o modificar una directiva de protección de aplicaciones en Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones cliente** > **Directivas de protección de aplicaciones**. Antes de usar esta característica, asegúrese de cumplir los [requisitos de Outlook para iOS y Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="notices"></a>Notificaciones

### <a name="upcoming-password-enforcement-change-for-macos-10142-in-intune---1873216--"></a>Próximo cambio de aplicación de contraseña para macOS 10.14.2 en Intune <!--1873216-->
El pasado mes de julio compartimos en MC145129 la noticia de que Intune tiene previsto integrar la opción de configuración recién publicada “Cambiar contraseña en el siguiente Auth” de Apple para dispositivos que ejecutan macOS 10.13 y versiones posteriores. Actualmente tenemos previsto implementar esta opción de configuración en febrero para macOS 10.14.2 y versiones posteriores. 

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Esto afecta a si tiene o va a tener dispositivos que ejecutan macOS 10.14.2 y versiones posteriores. Tras la introducción de Apple de la opción "Cambiar contraseña en el siguiente Auth", al insertar una directiva de contraseña, Intune puede exigir a los usuarios que actualicen su contraseña a una que sea compatible. Los usuarios de macOS recibirán una solicitud para actualizar su contraseña cuando se integre esta nueva característica de Apple, incluso si su contraseña ya es compatible. Tenga en cuenta que si la contraseña ya es compatible y no tiene un requisito para contraseñas de repetición, los usuarios finales podrán actualizar a su contraseña existente. Los usuarios finales solo verán una solicitud para actualizar su contraseña cuando intenten autenticar o iniciar sesión en su dispositivo. Si bloquea los recursos de la empresa hasta que el dispositivo se marque como compatible, debe tener en cuenta que los usuarios finales de dispositivos con macOS 10.14.2 podrían tener bloqueado el acceso a recursos de la empresa, como el correo electrónico o los sitios de SharePoint, hasta que restablezcan su contraseña. En el futuro, todas las actualizaciones de las directivas de contraseñas de configuración y cumplimiento obligarán a los usuarios de destino a actualizar sus contraseñas. Nuestro estudio de los clientes antes de implementar este cambio demostró que la mayoría de los clientes no se verán afectados por este cambio, puesto que los usuarios finales normalmente actualizarán su contraseña después de recibir una solicitud para inscribirse con una contraseña o restablecer su contraseña para seguir siendo compatible.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
Es posible que quiera informar a su departamento de soporte técnico. Actualizaremos esta página de novedades cuando se implante este cambio. Si no quiere que se aplique esta directiva de contraseña de dispositivos macOS, se recomienda eliminar o anular la asignación de la directiva de macOS existente.

###<a name="plan-for-change-update-to-ios-setting-for-supervised-devices-in-the-intune-console"></a>Plan de cambio: actualización de la configuración de iOS en dispositivos supervisados en la consola de Intune  
Con la actualización de febrero al servicio de Intune, se cambia el nombre de la configuración "Habilitación de restricciones en la configuración del dispositivo" para dispositivos iOS supervisados por "Tiempo de uso (solo con supervisión)". Después de este cambio, la experiencia del usuario final cambiará en función de la versión de iOS.

####<a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Después de que la configuración "Habilitación de restricciones en la configuración del dispositivo (solo supervisado)" haya cambiado de nombre por "Tiempo de uso (solo con supervisión)", esta será la experiencia de los dispositivos supervisados (dispositivos inscritos en los programas de inscripción de Apple): 

Para dispositivos con iOS 11.4 y versiones anteriores: esta configuración puede usarse para impedir que los usuarios modifiquen las restricciones de dispositivos como antes. Los usuarios finales no verán cambios en la experiencia.
 
Para dispositivos con iOS 12 y versiones posteriores: los usuarios finales ya no verán la pestaña Restricciones en Ajustes > General > Administración de dispositivos > Management Profile (Perfil de administración) > Restricciones.
En su lugar, este elemento formará parte de Ajustes > General > Tiempo de uso. Si configura este valor como "Bloquear", impedirá que los usuarios cambien la configuración de Tiempo de uso en sus dispositivos, lo que también incluye las restricciones de contenido y privacidad.

####<a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
Actualice la guía de usuario final para que tenga en cuenta el cambio en la experiencia para los dispositivos que se actualicen a iOS 12 y versiones posteriores.


###<a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>Plan de cambio: cambios de flujo de trabajo para la inscripción de iOS 12 en Intune
Apple ha anunciado algunos cambios relacionados con los dispositivos iOS que se inscriben en los servicios de administración de dispositivos móviles (MDM). Es probable que este cambio se vea en la versión de iOS de primavera de 2019, así como en todas las futuras versiones de iOS.

####<a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Si los usuarios finales actualizan sus dispositivos a esta nueva versión de iOS 12 en primavera, tienen que saber que hay un flujo de trabajo modificado y que tendrán que seguir pasos adicionales para completar la inscripción en Intune. Cuando Apple presente estos cambios, los usuarios finales tendrán que hacer lo siguiente: •            Empezar el proceso de inscripción en la aplicación Portal de empresa para descargar un perfil de administración. •            Ir a Ajustes > General > Perfiles. •            Seleccionar el perfil correcto y hacer clic en Instalar. •            Volver al Portal de empresa para completar la inscripción. 

Los dispositivos que ya estén inscritos y actualizados a la nueva versión de iOS no deberían verse afectados, salvo que se anule su inscripción y tengan que volver a inscribirse.
La experiencia de inscripción en dispositivos que ejecuten iOS 12.1 o versiones anteriores no cambiará con esta nueva versión de Apple.

####<a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
Debe planear actualizar la documentación y la guía de usuario final. También puede que quiera informar a su departamento de soporte técnico sobre estos cambios. Le mantendremos informado a través del Centro de mensajes y nuestra página de novedades cuando se produzca este cambio.

Haga clic en el vínculo de Información adicional para consultar una entrada de blog de soporte técnico con capturas de pantalla y un vídeo del flujo de inscripción esperado.

####<a name="additional-information"></a>Información adicional
https://aka.ms/iOS_enrollment_changes

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Plan de cambio: Actualización de la experiencia del usuario a la aplicación de Portal de empresa de Intune para iOS
Nos complace compartir que Intune pronto lanzará una actualización importante de la experiencia de usuario para la aplicación de Portal de empresa de iOS. La actualización contará con un cambio de diseño visual de la página principal con filtros avanzados y un acceso más rápido a las aplicaciones y los libros electrónicos.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Esta experiencia mantendrá las funciones actuales de Portal de empresa de iOS y también incluirá:
- Una página principal con aspecto de iOS nativo 
- Capacidades de filtrado en listas de contenido y búsqueda, incluida la capacidad de filtrar por tipo de contenido (aplicaciones o libros electrónicos) y disponibilidad (administración de dispositivos necesaria o disponible sin inscripción)
- Capacidad de buscar libros electrónicos
- Historial de búsquedas para aplicaciones y libros electrónicos si forma parte del programa TestFlight de Apple; se le notificará sobre la versión preliminar de la aplicación de Portal de empresa de Intune de iOS actualizada cuando esté disponible. Si no forma parte del programa TestFlight de Apple, aún está a tiempo de registrarse. Al registrarse podrá usar la aplicación de Portal de empresa actualizada antes de que esté disponible para los usuarios finales. También tendrá la oportunidad de proporcionar comentarios directamente al equipo de Intune.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?
No es necesario realizar ninguna acción; estos cambios se publicarán en una próxima versión de la aplicación de Portal de empresa de iOS. 

#### <a name="additional-information"></a>Información adicional
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="plan-for-change-exchange-online-to-intune-connector-will-not-be-available-in-intune----3105122---"></a>Plan de cambio: el conector de Exchange Online a Intune no estará disponible en Intune <!-- 3105122 -->
Para simplificar su experiencia con Exchange Online y Acceso condicional, deshabilitaremos el conector de "servicio a servicio" Exchange Online a Intune.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Ha recibido este mensaje porque en nuestros registros se indica que es posible que esté usando la funcionalidad del conector "Servicio a servicio" en el entorno. El conector "Servicio a servicio" admite la administración de Intune de los dispositivos de Exchange Active Sync Only para Exchange Online y no admite la infraestructura local. Este conector, debido a la manera en que se muestra en la consola, parece ser necesario para el Acceso condicional cuando, en realidad, no lo es. Con la actualización de febrero del servicio de Intune, para dejar esto en claro en la consola, deshabilitaremos el botón para configurar conectores nuevos. Luego, en marzo de 2019, se deshabilitarán todos los conectores existentes de Exchange Online a Intune.

Si usa estos conectores en el entorno, no podrá supervisar ni borrar los dispositivos Exchange Active Sync Only en Intune una vez que los conectores se deshabiliten en marzo. No se prevé ningún impacto en los usuarios finales durante este cambio.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>¿Qué puedo hacer para prepararme para este cambio?

Si tiene configurado el conector Servicio a servicio y tiene dispositivos de Exchange Active Sync, cambie a otros métodos para administrar los dispositivos. Dispone de las siguientes opciones:

- Inscribir dispositivos en Administración de dispositivos móviles (MDM)
- Usar las directivas de Intune App Protection para administrar los dispositivos
- Usar controles de Exchange tal como se describe en esta documentación. 

#### <a name="additional-information"></a>Información adicional
[Configuración de Exchange Service Connector para Intune y Exchange Online](https://docs.microsoft.com/intune/exchange-service-connector-configure)



### <a name="plan-for-change-performance-updates-to-intune-for-education---1750215--"></a>Plan de cambio: actualizaciones de rendimiento en Intune for Education <!--1750215-->.
Vamos a incorporar algunas actualizaciones en Intune for Education para aumentar la velocidad y la confiabilidad al asignar valores a los usuarios o dispositivos. Como parte de este cambio, a finales de noviembre trasladaremos sus directivas o sus asignaciones de directivas a grupos nuevos.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?

Como cliente de Intune for Education, tiene dos grupos dinámicos de Azure Active Directory (Azure AD): "Todos los usuarios" y "Todos los dispositivos". Con estas actualizaciones, los grupos de Azure AD "Todos los usuarios" y "Todos los dispositivos" no serán visibles en la consola de Intune for Education. Pero seguirán estando visibles en la consola de Intune en Azure y pasarán a llamarse "Todos los usuarios (obsoleto, no usar)" y "Todos los dispositivos (obsoleto, no usar)".

Cuando se implementen las actualizaciones, ya no necesitará usar los grupos de Azure AD para asignar aplicaciones y valores en Intune. Trasladaremos sus asignaciones de configuración a grupos nuevos en la consola de Intune for Education que le vamos a crear, que seguirán figurando como "Todos los usuarios" y "Todos los dispositivos". Estos cambios se efectuarán en segundo plano, por lo que no notará nada diferente en la consola de Intune for Education. No se prevé ningún impacto para los usuarios finales ni para los dispositivos inscritos. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
No es necesario hacer nada mientras trasladamos sus asignaciones de directivas. Si está asignando directivas en la consola de Intune for Education, siga haciéndolo.

Si está asignando directivas a los grupos de Azure AD mencionados en Intune en Azure, empiece por asignarlas a los grupos "Todos los usuarios" y "Todos los dispositivos" en la consola de Intune for Education. Cuando vea en la consola que los grupos de Azure AD han quedado obsoletos, deje de asignar directivas en Azure AD. Si no está usando los grupos cuyo nombre ha cambiado para ningún otro fin, debería eliminarlos.


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Realizar acción: actualice la configuración de restricción o contraseña de directiva de cumplimiento de dispositivos Android en Intune.
Intune ya no dispondrá del tipo de contraseña "predeterminada del dispositivo" para dispositivos Android 4.4 y versiones superiores. Debido a las diferencias entre las plataformas de Android y la configuración predeterminada del dispositivo, este suele tratar esta directiva como opcional. Para que no se produzcan confusiones al aplicar esta configuración en Android, se eliminará de la interfaz de usuario en una versión posterior. 
#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
- Si quiere que sea obligatorio indicar una contraseña en los dispositivos, le recomendamos que edite los perfiles de plataforma de Android para definir el tipo de contraseña necesario, en vez de usar la opción predeterminada del dispositivo.
- Si quiere que el usuario final decida si crear una contraseña o no, seleccione el botón "Sin configurar". Cuando se quite esta opción de la interfaz de usuario, si todavía está activada, recibirá una solicitud para elegir una opción distinta a la predeterminada del dispositivo al editar el perfil.
¿Qué necesito hacer para prepararme para este cambio?
Revise la configuración de contraseña en las directivas de cumplimiento y restricción de dispositivos Android y dispositivos empresariales Android. Figuran en las directivas Seguridad del sistema para cumplimiento y en las restricciones Contraseña de dispositivo o Configuración de perfil de trabajo para el dispositivo. En la información adicional encontrará un vínculo para obtener más información y capturas de pantalla sobre cómo configurar dichas opciones.
#### <a name="additional-information"></a>Información adicional
https://aka.ms/PasswordSettings 

