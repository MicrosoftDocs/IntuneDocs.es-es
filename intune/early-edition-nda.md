---
title: Edición anticipada - Microsoft Intune
titlesuffix: ''
description: Edición anticipada de Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 0efc84da6a9efb594600b9ca33aa5eb7622c8101
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203440"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>La edición anticipada de Microsoft Intune: enero de 2019

> [!Note]
> Notificación de acuerdo de confidencialidad: Los siguientes cambios están en fase de desarrollo de Intune. Esta información se comparte en el acuerdo de confidencialidad de forma muy limitada. No publique esta información en redes sociales ni sitios web públicos, como Twitter, UserVoice, Reddit, etc. 

La **edición anticipada** proporciona una lista de características, compartidas en el acuerdo de confidencialidad, que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No publique en un tweet, divulgue en UserVoice ni comparta de otra manera esta información fuera de su empresa. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure

<!-- 1901 start -->

### <a name="android-enterprise-apps----1352553----"></a>Aplicaciones de Android Enterprise <!-- 1352553  -->
Podrá eliminar aplicaciones de Google Play administradas desde Microsoft Intune. Para eliminar una aplicación administrada de Google Play, abra Microsoft Intune en Azure Portal y seleccione **Aplicaciones cliente** > **Aplicaciones**. En la lista de aplicaciones, seleccione la elipse (...) a la derecha de la aplicación de Google Play administrada y luego seleccione **Eliminar** en la lista que aparece. Cuando se elimina una aplicación de Google Play administrada de la lista de aplicaciones, automáticamente se desactiva la aprobación de la aplicación administrada de Google Play.

### <a name="managed-google-play-app-type----1352580---"></a>Aplicación administrada de Google Play tipo <!-- 1352580 -->
El tipo de aplicación **administrada de Google Play** le permitirá agregar específicamente [aplicaciones de Google Play administradas](https://play.google.com/work/search?q=microsoft&c=apps) a Intune. Como administrador de Intune, ahora podrá examinar, buscar, aprobar, sincronizar y asignar aplicaciones de Google Play administradas aprobadas en Intune. Ya no necesitará ir a la consola de Google Play administrada por separado ni tendrá que volver a autenticarlas. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. En la lista **Tipo de aplicación**, seleccione **Google Play administrada** como tipo de aplicación.

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Versión preliminar de la compatibilidad para dispositivos Android totalmente administrados de propiedad corporativa <!-- 1574342  -->
Intune admitirá dispositivos Android totalmente administrados, un escenario de "propietario de dispositivo" de propiedad corporativa en el departamento de TI administra de manera rigurosa los dispositivos y estos están asociados a usuarios individuales. Esto permite que los administradores administren todo el dispositivo, apliquen una amplia variedad de controles de directivas no disponibles para los perfiles de trabajo y restrinjan las instalaciones de aplicaciones por parte de los usuarios solo a Google Play administrado. Para configurar dispositivos Android totalmente administrados, vaya a **Dispositivo administrado** > **Inscripción de Android** > **Corporate-owned, fully managed user devices** (Dispositivos de usuario totalmente administrados de propiedad corporativa). Tenga en cuenta que esta característica está en versión preliminar. Algunas funcionalidades de Intune, como certificados, cumplimiento y acceso condicional, no están disponibles actualmente con dispositivos Android totalmente administrados.

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Implementación de aplicaciones de Microsoft Store para Empresas con licencias en línea <!-- 1672660  -->
Podrá asignar las aplicaciones de Microsoft Store para Empresas con licencias en línea necesarias en el contexto del dispositivo. Implementar una aplicación de Microsoft Store para Empresas de esta forma permitirá que la aplicación se instale para todos los usuarios en el dispositivo. Esto solo es aplicable para dispositivos de escritorio de Windows 10 RS4+. La opción para instalar en el contexto del dispositivo está disponible en la página de asignación de aplicaciones del cliente para las aplicaciones con licencia en línea de MSFB.

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Configuración del perfil para omitir algunas pantallas durante el Asistente para configuración <!-- 2276470  -->
Cuando cree un perfil de inscripción de macOS, podrá configurarlo para omitir cualquiera de las siguientes pantallas cuando un usuario utilice el Asistente para la configuración:
- Migración de Android
- Tono de visualización
- Privacidad
- iCloudStorage

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522----"></a>Asignación de perfiles de AutoPilot al grupo virtual Todos los dispositivos<!--2715522  -->
Podrá asignar perfiles de AutoPilot al grupo virtual Todos los dispositivos. Para ello, elija **Inscripción de dispositivos** > **Inscripción Windows** > **Perfiles de implementación** > elija un perfil > **Tareas** > bajo **Asignar a** elija **Todos los dispositivos**. Para más información sobre los perfiles de Autopilot, vea [Inscribir dispositivos Windows con Windows Autopilot](enrollment-autopilot.md).

### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324----"></a>Personalice el papel tapiz en dispositivos iOS supervisados mediante un perfil de configuración de dispositivo <!-- 2809324  -->
Cuando cree un perfil de configuración de dispositivos para dispositivos iOS, podrá permitir o restringir algunas opciones en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **Restricciones del dispositivo** para el tipo de perfil. Esta actualización incluye una nueva configuración de **Papel tapiz** que permite a un administrador usar una imagen .png, .jpg o .jpeg como fondo de pantalla, ver la versión preliminar de la imagen e impedir que los usuarios cambien el papel tapiz. Esta configuración de papel tapiz solo se aplicará a los dispositivos supervisados. Para obtener una lista de las configuraciones actuales, vea la [Configuración de restricción de dispositivos iOS](device-restrictions-ios.md).

### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notificaciones del sistema para aplicaciones Win32 <!-- 3136566   -->
Podrá suprimir notificaciones del sistema para el usuario final por asignación de aplicaciones. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > seleccione la aplicación > **Asignaciones** > **Incluir grupos**. 

### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396---"></a>Se eliminó la opción para compartir contacto a través de Bluetooth en Restricciones del dispositivo > Propietario del dispositivo para Android Enterprise <!-- 3598396 -->
Cuando se crea un perfil de restricciones de dispositivos para dispositivos de Android Enterprise, hay una configuración para **Compartir contacto a través de Bluetooth**. En esta actualización, se eliminará la configuración **Compartir contacto a través de Bluetooth** (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **Restricciones de dispositivos > Propietario del dispositivo** para el tipo de perfil > **General**). 

La configuración **Compartir contacto a través de Bluetooth** no es compatible con la administración de Propietario del dispositivo Android Enterprise. Por lo que cuando se quite esta configuración, no afectará a ningún dispositivo ni inquilino, incluso si esta opción está habilitada y configurada en su entorno.

Para ver la lista actual de configuraciones, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características](device-restrictions-android-for-work.md).

Se aplica a: Propietario del dispositivo Android Enterprise

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Implementación de aplicaciones APP-WE de Android Enterprise <!-- 1171203 -->
Para los dispositivos Android en un escenario de implementación de directiva de protección de aplicaciones sin inscripción (APP-WE) no inscrito, podrá usar Google Play administrado para implementar aplicaciones de la tienda y aplicaciones LOB en los usuarios. En concreto, el departamento de TI puede brindar a los usuarios finales un catálogo de aplicaciones y experiencia de instalación que ya no requiere que los usuarios finales flexibilicen la posición de seguridad de sus dispositivos al permitir instalaciones de orígenes desconocidos. Además, este escenario de implementación proporcionará una mejor experiencia del usuario final.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>El SDK de aplicaciones de Intune admitirá claves de cifrado de 256 bits <!-- 1832174 -->
El SDK de aplicaciones de Intune para Android usará claves de cifrado de 256 bits cuando el cifrado esté habilitado mediante las directivas de protección de aplicaciones. El SDK seguirá siendo compatible con las claves de 128 bits para mantener la compatibilidad con el contenido y las aplicaciones que usen las versiones anteriores del SDK.


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Método de autenticación de actualizaciones de directivas de Intune e instalación de aplicaciones de Portal de empresa <!-- 1927359 -->
En los dispositivos ya inscritos mediante el Asistente de configuración a través de uno de los métodos de inscripción de dispositivos corporativos de Apple, Intune ya no será compatible con el Portal de empresa cuando los usuarios finales de la tienda de aplicaciones lo instalen manualmente. Este cambio solo es pertinente cuando se realiza la autenticación con el Asistente de configuración de Apple durante la inscripción. Este cambio solo afecta a los dispositivos iOS inscritos a través de:  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Programa de inscripción de dispositivos (DEP) de Apple

Si los usuarios instalan la aplicación Portal de empresa desde la tienda de aplicaciones y luego intentan inscribir estos dispositivos a través de ella, recibirán un error. Se espera que estos dispositivos solo usen Portal de empresa cuando Intune lo inserta, automáticamente, durante la inscripción. Se actualizarán los perfiles de inscripción de Intune en Azure Portal para que pueda especificar cómo los dispositivos se autentican y si reciben la aplicación Portal de empresa. Si quiere que los usuarios de dispositivos DEP tengan la aplicación Portal de empresa, deberá especificar sus preferencias en un perfil de inscripción. Además, pronto quedará obsoleta la pantalla **Identificar el dispositivo** de la aplicación Portal de empresa.  
Para instalar Portal de empresa en dispositivos DEP ya inscritos, deberá ir a Intune > Aplicaciones cliente e insertarla como aplicación administrada con las directivas de configuración de aplicaciones. En futuros documentos habrá disponible más información sobre cómo llevar a cabo estos pasos.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>Quienes no son administradores pueden habilitar BitLocker en dispositivos Windows 10 unidos a Azure AD<!-- 2147379 -->
Cuando se habilita la configuración de BitLocker en dispositivos Windows 10 (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para la plataforma > **Endpoint Protection** para el tipo de perfil > **Cifrado de Windows**), se agrega la configuración de BitLocker. Esta actualización incluye una configuración de BitLocker nueva para permitir que los usuarios estándar (no administradores) habiliten el cifrado. Para ver la configuración actual, consulte [Configuración de Endpoint Protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).


### <a name="additional-settings-for-outlook----3301182---"></a>Configuración adicional para Outlook <!-- 3301182 -->
Ahora puede cambiar más opciones de configuración para Outlook para iOS y Android con Intune.  Estas opciones de configuración incluyen las siguientes:
- Permitir que solo se usen cuentas profesionales o educativas en iOS y Android.
- Implementar la autenticación moderna para Office 365 y la autenticación moderna híbrida para cuentas locales.
- Usar `SAMAccountName` para el campo de nombre de usuario en el perfil de correo electrónico al tener seleccionada la autenticación básica.
- Permitir que se guarden contactos.
- Configurar información sobre el correo electrónico de destinatarios externos.
- Configurar la **Bandeja de entrada Prioritarios**.
- Requerir autenticación biométrica para acceder a Outlook para iOS. 
- Bloquear las imágenes externas.

> [!NOTE]
> Si usa directivas de Intune App Protection para administrar el acceso de las identidades corporativas, le recomendamos que no habilite el **requisito de autenticación biométrica**. Para obtener más información, vea **Requerir credenciales corporativas en acceso**, en los artículos relativos a los [requisitos de acceso de iOS](app-protection-policy-settings-ios.md#access-settings) y los [requisitos de acceso de Android](app-protection-policy-settings-android.md#access-settings), respectivamente.

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Las plantillas administrativas están en versión preliminar pública y se movieron a su propio perfil de configuración <!-- 3322847 -->
Las plantillas administrativas de Intune (**Configuración del dispositivo** > **Plantillas administrativas**) están actualmente en versión preliminar privada. Con esta actualización: las plantillas administrativas incluyen cerca de 300 valores de configuración que se pueden administrar en Intune. Anteriormente, estas configuraciones solo existían en el editor de directivas de grupo.
Las plantillas administrativas están disponibles en versión preliminar pública y se mueven desde **Configuración del dispositivo** > **Plantillas administrativas** a **Configuración del dispositivo** > **Perfiles** >**Crear perfil** > en **Plataforma**, elija **Windows 10 y versiones posteriores**, en **Tipo de perfil**, elija **Plantillas administrativas**.
Se habilita el informe; se aplica a: Windows 10 y versiones posteriores

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Modo oscuro del Portal de empresa de macOS para Intune <!-- 3300524 -->
El Portal de empresa de macOS para Intune ahora admite el Modo oscuro para macOS. Cuando habilita el Modo oscuro en un dispositivo macOS 10.14 o una versión posterior, el Portal de empresa ajustará su apariencia para que los colores reflejen ese modo.

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Uso de la configuración recomendada por Microsoft con líneas de base de seguridad <!-- 2055484 -->
Intune se integra con otros servicios centrados en la seguridad, incluidos ATP de Windows Defender y Office 365 ATP. Los clientes solicitan una estrategia común y un conjunto coherente de flujos de trabajo de seguridad integrales entre los servicios de Microsoft 365. Nuestro objetivo es alinear las estrategias para crear soluciones que actúen de puente entre las operaciones de seguridad y las tareas de administración comunes. En Intune, este objetivo se pretende lograr mediante la publicación de un conjunto de "Líneas de base de seguridad" recomendadas de Microsoft (**Intune** > **Líneas de base de seguridad**).  Un administrador podrá crear directivas de seguridad directamente a partir de estas líneas de base y, después, implementarlas en sus usuarios. También se pueden personalizar los procedimientos recomendados para satisfacer las necesidades de la organización. Intune garantiza que los dispositivos cumplan estas líneas de base y notifica a los administradores los usuarios o dispositivos que no están en cumplimiento.

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Directivas de WIP implementadas sin la inscripción del usuario <!-- 1434452 -->
Las directivas de Windows Information Protection (WIP) se podrán implementar sin requerir que los usuarios de MDM inscriban sus dispositivos Windows 10. Esta configuración permite a las empresas proteger sus documentos corporativos en función de la configuración de WIP, mientras que permite a los usuarios mantener la administración de sus propios dispositivos Windows. Una vez que los documentos están protegidos con una directiva de WIP, un administrador de Intune puede borrar de forma selectiva los datos protegidos. Mediante la selección del usuario y dispositivo, y el envío de una solicitud de borrado, todos los datos protegidos mediante la directiva de WIP quedarán inservibles. En Intune en Azure Portal, seleccione **Aplicación móvil** > **Borrado selectivo de aplicaciones**.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Configuración de directiva de protección de la aplicación (APP) de datos web <!-- 2662995 -->
La configuración de directiva APP de contenido web en dispositivos iOS y Android se actualizará para controlar mejor los vínculos web http y https, así como la transferencia de datos a través de vínculos universales de iOS y vínculos de aplicación de Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP de Apple usado por otro MDM <!-- 1488946 -->
Intune detectará y mostrará los detalles si un token de programa de compras por volumen (VPP) de Apple lo está usando Intune y otro MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos retirados en el panel de cumplimiento del dispositivos <!-- 1981119 -->
En una actualización futura, los dispositivos retirados se quitarán del panel de cumplimiento del dispositivo. Esto cambiará los números de cumplimiento.



<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Comprobar cumplimiento de Configuration Manager <!-- 2192052 -->
Una actualización futura incluirá una nueva configuración de conformidad de System Center Configuration Manager (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Windows 10**). Configuration Manager envía señales a la conformidad de Intune. Mediante la configuración de Intune, puede exigir que todas las señales de Configuration Manager devuelvan “conforme”.

Por ejemplo, exige que todas las actualizaciones de software se instalen en los dispositivos. En Configuration Manager, este requisito tiene el estado “Instalado”. Si algún programa del dispositivo se encuentra en estado desconocido, el dispositivo no será conforme en Intune.

Se aplica a Windows 10 y versiones posteriores



## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.

### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.



