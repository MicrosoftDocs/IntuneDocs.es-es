---
title: Edición anticipada - Microsoft Intune
titlesuffix: ''
description: Edición anticipada de Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/3/2018
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
ms.openlocfilehash: 35298713738c666ca19d57e647412729a85bbc4a
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112840"
---
# <a name="the-early-edition-for-microsoft-intune---december-2018"></a>La edición anticipada para Microsoft Intune, diciembre de 2018

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

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Implementación de aplicaciones APP-WE de Android Enterprise <!-- 1171203 -->
Para los dispositivos Android en un escenario de implementación de directiva de protección de aplicaciones sin inscripción (APP-WE) no inscrito, podrá usar Google Play administrado para implementar aplicaciones de la tienda y aplicaciones LOB en los usuarios. En concreto, el departamento de TI puede brindar a los usuarios finales un catálogo de aplicaciones y experiencia de instalación que ya no requiere que los usuarios finales flexibilicen la posición de seguridad de sus dispositivos al permitir instalaciones de orígenes desconocidos. Además, este escenario de implementación proporcionará una mejor experiencia del usuario final.

### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nuevas opciones para conectarse automáticamente y conservar las reglas al usar la configuración DNS en dispositivos Windows 10 y posteriores <!-- 1333665, 2999078 -->
En dispositivos Windows 10 y posteriores, podrá crear un perfil de configuración de VPN que incluya una lista de servidores DNS para resolver dominios, como contoso.com. Esto incluirá una nueva configuración para la resolución de nombres (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > Elegir **Windows 10 y versiones posteriores** para la plataforma > Elegir **VPN** para el tipo de perfil > **Configuración DNS** >**Agregar**): 

- **Conectar automáticamente**: si esta opción está **Habilitada**, el dispositivo se conecta automáticamente a la VPN cuando se comunica con un dominio especificado, como contoso.com.
- **Persistente**: de manera predeterminada, todas las reglas de la tabla de directivas de resolución de nombres (NRPT) están activas siempre que el dispositivo esté conectado mediante este perfil de VPN. Si esta opción está **habilitada** en una regla de NRPT, la regla sigue activa en el dispositivo incluso si la VPN se desconecta o si se quita el perfil de VPN. La regla permanece hasta que se quita manualmente, lo que se puede hacer mediante PowerShell.

[Configuración de VPN de Windows 10](vpn-settings-windows-10.md) describe la lista actual de configuraciones. 

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642-eeready---"></a>Uso de S/MIME para cifrar y firmar varios dispositivos de un usuario <!-- 1333642 eeready -->
Se admite el cifrado de correo electrónico S/MIME mediante un nuevo perfil de certificado importado (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > seleccione la plataforma > tipo de perfil **Certificado PKCS importado**). En Intune, puede importar los certificados en formato PFX. Después, Intune puede entregar esos mismos certificados a varios dispositivos inscritos por un solo usuario. Esto también incluye lo siguiente:

- El perfil de correo electrónico de iOS nativo permite habilitar el cifrado S/MIME mediante certificados importados en formato PFX.
- La aplicación de correo nativo de los dispositivos Windows Phone 10 usa automáticamente el certificado S/MIME.
- Los certificados privados se pueden entregar en varias plataformas. Aun así, no todas las aplicaciones de correo electrónico son compatibles con S/MIME.
- En otras plataformas, podría tener que configurar manualmente la aplicación de correo electrónico para habilitar S/MIME.  
- Las aplicaciones de correo electrónico que admiten el cifrado S/MIME pueden controlar la recuperación de certificados para el cifrado de correo electrónico S/MIME de una manera que no es compatible con un servicio MDM, por ejemplo, si los lee desde el almacén de certificados del publicador.

Compatible con: Windows, Windows Phone 10, macOS, iOS, Android

### <a name="help-and-support-page-in-the-windows-company-portal-app----1488939---"></a>Página de Ayuda y soporte técnico en la aplicación Portal de empresa de Windows <!-- 1488939 -->
Se agregará una página nueva a la aplicación Portal de empresa de Windows. La página de ayuda y soporte técnico brindará la información de contacto del departamento de soporte técnico. Además, los usuarios finales podrán enviar registros de Portal de empresa en caso de tener errores. La página también proporciona una sección con las preguntas más frecuentes para ayudar a los usuarios finales.

### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Uso de la detección de redes de confianza para perfiles de VPN en dispositivos Windows 10 <!-- 1500165 -->
Al usar la detección de redes de confianza, podrá impedir que los perfiles de VPN creen automáticamente una conexión VPN cuando el usuario ya está en una red de confianza. Podrá agregar sufijos DNS para habilitar la detección de redes de confianza en dispositivos que ejecutan Windows 10 y versiones posteriores (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para la plataforma > **VPN** para el tipo de perfil).
[Configuración de VPN de Windows 10](vpn-settings-windows-10.md) muestra la configuración de VPN actual.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>El SDK de aplicaciones de Intune admitirá claves de cifrado de 256 bits <!-- 1832174 -->
El SDK de aplicaciones de Intune para iOS usará claves de cifrado de 256 bits cuando el cifrado esté habilitado mediante las directivas de protección de aplicaciones. El SDK seguirá siendo compatible con las claves de 128 bits para mantener la compatibilidad con el contenido y las aplicaciones que usen las versiones anteriores del SDK.

### <a name="enabled-shared-pc-settings-in-intune-profile----1907917---"></a>Configuración PC compartido habilitada en el perfil de Intune <!-- 1907917 -->
Actualmente, puede establecer la configuración PC compartido en dispositivos con Windows 10 Escritorio con una configuración de OMA-URI personalizada. Se agregará un nuevo perfil para ajustar la configuración PC compartido (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** > **Shared multi-user device** [Dispositivo multiusuario compartido]).
Se aplica a: Windows 10 y versiones posteriores, Windows Holographic for Business

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Método de autenticación de actualizaciones de directivas de Intune e instalación de aplicaciones de Portal de empresa <!-- 1927359 -->
En ciertos dispositivos, Intune dejará de admitir la aplicación Portal de empresa cuando se instale desde la tienda de aplicaciones. Este cambio solo es pertinente cuando se realiza la autenticación con el Asistente de configuración de Apple durante la inscripción. Este cambio solo afecta a los dispositivos iOS inscritos a través de:  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Programa de inscripción de dispositivos (DEP) de Apple

Si los usuarios instalan la aplicación Portal de empresa desde la tienda de aplicaciones y luego intentan inscribir estos dispositivos a través de ella, recibirán un error. Se espera que estos dispositivos solo usen Portal de empresa cuando Intune lo inserta, automáticamente, durante la inscripción. Se actualizarán los perfiles de inscripción de Intune en Azure Portal para que pueda especificar cómo los dispositivos se autentican y si reciben la aplicación Portal de empresa. Si quiere que los usuarios de dispositivos DEP tengan la aplicación Portal de empresa, deberá especificar sus preferencias en un perfil de inscripción. Además, pronto quedará obsoleta la pantalla **Identificar el dispositivo** de la aplicación Portal de empresa.  
Para instalar Portal de empresa en dispositivos DEP ya inscritos, deberá ir a Intune > Aplicaciones cliente e insertarla como aplicación administrada con las directivas de configuración de aplicaciones. En futuros documentos habrá disponible más información sobre cómo llevar a cabo estos pasos.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>Quienes no son administradores pueden habilitar BitLocker en dispositivos Windows 10 unidos a Azure AD<!-- 2147379 -->
Cuando se habilita la configuración de BitLocker en dispositivos Windows 10 (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para la plataforma > **Endpoint Protection** para el tipo de perfil > **Cifrado de Windows**), se agrega la configuración de BitLocker. Esta actualización incluye una configuración de BitLocker nueva para permitir que los usuarios estándar (no administradores) habiliten el cifrado. Para ver la configuración actual, consulte [Configuración de Endpoint Protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).

### <a name="intune-app-pin----2298397---"></a>PIN de aplicación de Intune <!-- 2298397 -->
Como administrador de TI, podrá configurar la cantidad de días que un usuario final puede esperar hasta que se deba cambiar el PIN de aplicación de Intune. La configuración nueva estará disponible en Azure Portal si selecciona **Intune** > **Aplicaciones cliente** > **Directivas de protección de aplicaciones** > **Crear directiva** > **Configuración** > **Requisitos de acceso**. Esta característica estará disponible en dispositivos iOS y Android. Esta configuración admite un valor entero positivo.

### <a name="new-windows-10-update-settings----2626030-2512994---"></a>Nueva configuración de actualizaciones de Windows 10 <!-- 2626030 2512994 -->
Para los círculos de actualizaciones de Windows 10, podrá:
- restaurar la configuración de actualización automática original de una máquina con Windows 10 en máquinas que ejecuten la *actualización de octubre de 2018*
- establecer una nueva configuración de actualizaciones de software que le permita bloquear o autorizar que los usuarios pausen la instalación de aplicaciones en los *Ajustes* de sus máquinas. 



### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>Los perfiles de correo electrónico de iOS pueden usar cifrado y firma de S/MIME <!-- 2662949 -->
Podrá crear un perfil de correo electrónico que incluya otra configuración. Esto incluye la configuración de S/MIME que se puede usar para firmar y cifrar las comunicaciones de correo electrónico de dispositivos iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > Elegir **iOS** para la plataforma > **Correo electrónico** para el tipo de perfil).

[Opciones de configuración de correo electrónico iOS](email-settings-ios.md) muestra la configuración actual.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509---"></a>Omisión de más pantallas del Asistente de configuración de un dispositivo DEP iOS <!-- 2687509 -->
Además de las pantallas que actualmente se pueden omitir, podrá establecer dispositivos DEP de iOS para omitir las pantallas siguientes en el Asistente de configuración cuando un usuario inscribe el dispositivo: Tono de pantalla, Privacidad, Migración de Android, botón Inicio, iMessage y FaceTime, Incorporación, Migración de Watch, Apariencia, Tiempo de uso, Actualización de software, Configuración de SIM.
Para elegir qué pantallas omitir, vaya a **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > elija un token > **Perfiles** > elija un perfil > **Propiedades** > **Personalización del Asistente de configuración** > elija **Ocultar** en todas las pantallas que quiera omitir > **Aceptar**.

### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Algunas opciones de configuración de BitLocker admiten Windows 10 Pro Edition<!-- 2727036 -->
Podrá crear un perfil de configuración que establezca los ajustes de Endpoint Protection en dispositivos Windows 10, incluido BitLocker. Esto agrega compatibilidad con Windows 10 Professional Edition en algunas configuraciones de BitLocker. Para ver la configuración de la edición de Windows 10 actual, consulte [Configuración de Endpoint Protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).
Intune proporcionará campos adicionales con información sobre el dispositivo, incluido el fabricante de Android, el modelo, la versión de la revisión de seguridad y el modelo de iOS. En Intune, estos campos estarán disponibles si selecciona **Aplicaciones cliente** > **Estado de protección de aplicaciones** y elige **Informe de protección de aplicaciones: iOS, Android**. Además, estos parámetros lo ayudarán a configurar la lista de **admitidos** correspondiente al fabricante de dispositivo (Android), la lista de **admitidos** del modelo de dispositivo (iOS y Android) y la configuración de versión de la revisión de seguridad mínima de Android. 

### <a name="intune-device-reporting-fields----2748738---"></a>Campos de informes de dispositivo de Intune <!-- 2748738 -->
Intune proporcionará campos adicionales con información sobre el dispositivo, incluido el fabricante de Android, el modelo, la versión de la revisión de seguridad y el modelo de iOS. En Intune, estos campos estarán disponibles si selecciona **Aplicaciones cliente** > **Estado de protección de aplicaciones** y elige **Informe de protección de aplicaciones: iOS, Android**. Además, estos parámetros lo ayudarán a configurar la lista de **admitidos** correspondiente al fabricante de dispositivo (Android), la lista de **admitidos** del modelo de dispositivo (iOS y Android) y la configuración de versión de la revisión de seguridad mínima de Android. 

### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal----2809362---"></a>El nombre de Configuración de un dispositivo compartido se cambia a Mensaje de la pantalla de bloqueo para dispositivos iOS en Azure Portal <!-- 2809362 -->
Cuando cree un perfil de configuración de dispositivos iOS, podrá agregar la opción **Configuración de un dispositivo compartido** para mostrar texto específico en la pantalla de bloqueo. Esto incluye los siguientes cambios: 

- El nombre de la opción **Configuración de un dispositivo compartido** en Azure Portal se cambia a "Mensaje de la pantalla de bloqueo (solo con supervisión)" (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > Elegir **iOS** para la plataforma > Elegir **Características del dispositivo** para el tipo de perfil > **Mensaje de la pantalla de bloqueo**).
- Al agregar mensajes de la pantalla de bloqueo, puede insertar un número de serie, un nombre de dispositivo u otro valor específico para el dispositivo como variable en **Información de etiqueta del activo**. Por ejemplo, puede escribir `Device name: {{device name}}` o `Serial number is {{serial number}}` entre llaves. [Tokens de iOS](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) muestra los tokens disponibles que se pueden usar.

[Settings to display messages on the lock screen](shared-device-settings-ios.md) (Configuración para mostrar mensaje en la pantalla de bloqueo) muestra la configuración actual.

### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564--"></a>Mensajes de error de restricción de inscripción más detallados <!-- 3111564-->
Los mensajes de error más detallados estarán disponibles cuando no se cumplan las restricciones de inscripción. Para ver estos mensajes, vaya a **Intune** > **Solucionar problemas** > y revise la tabla Errores de inscripción.

### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Nueva configuración de notificaciones, sugerencias y bloqueo del teclado para dispositivos propietarios del dispositivo Android Enterprise <!-- 3201839 3201843 -->
Esta actualización incluye varias características de los dispositivos Android Enterprise cuando se ejecutan como propietario del dispositivo. Para usar estas características, vaya a **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > en **Plataforma**, elija **Android Enterprise** > en **Tipo de perfil**, elija **Solo el propietario del dispositivo** > **Restricciones de dispositivos**.
Entre las nuevas características se incluyen: 
- Deshabilitar la visualización de las notificaciones del sistema, incluidas las llamadas entrantes, las alertas del sistema, los errores del sistema, etc.
- Sugerir omitir los tutoriales de inicio y las sugerencias para las aplicaciones que se abren por primera vez.
- Deshabilitar la configuración avanzada del bloqueo del teclado, como la cámara, las notificaciones, el desbloqueo con huella digital, etc.

Para ver la configuración actual, vaya a [Configuración de las restricciones de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Los dispositivos propietarios del dispositivo Android Enterprise pueden usar conexiones VPN siempre activas <!-- 3202194 -->
En esta actualización, puede usar conexiones VPN siempre activas en dispositivos propietarios del dispositivo Android Enterprise. Las conexiones VPN siempre activas permanecen conectadas o se vuelven a conectar inmediatamente cuando el usuario desbloquea el dispositivo, cuando se reinicia el dispositivo o cuando cambia la red inalámbrica. También puede poner la conexión en modo “bloqueo”, que bloquea todo el tráfico de red hasta que la conexión VPN esté activa.
Puede habilitar la VPN siempre activa en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **Restricciones de dispositivos** solo para el propietario del dispositivo > **Conectividad**. Para ver la configuración actual, vaya a [Configuración de las restricciones de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nueva configuración para terminar los procesos en el Administrador de tareas de dispositivos Windows 10 <!-- 3285177 --> 
Esta actualización incluye una configuración nueva para terminar los procesos con el Administrador de tareas en dispositivos Windows 10. Con un perfil de configuración de dispositivo (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > en **Plataforma**, elija **Windows 10** > en **Tipo de perfil**, elija **Restricciones de dispositivos** > **Configuración general**), elige si permitir o impedir esta configuración.
Para ver la configuración actual, vaya a la [configuración de restricciones de dispositivos Windows 10](device-restrictions-windows-10.md).
Se aplica a: Windows 10 y versiones posteriores

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Las plantillas administrativas están en versión preliminar pública y se movieron a su propio perfil de configuración <!-- 3322847 -->
Las plantillas administrativas de Intune (**Configuración del dispositivo** > **Plantillas administrativas**) están actualmente en versión preliminar privada. Con esta actualización: las plantillas administrativas incluyen cerca de 300 valores de configuración que se pueden administrar en Intune. Anteriormente, estas configuraciones solo existían en el editor de directivas de grupo.
Las plantillas administrativas están disponibles en versión preliminar pública y se mueven desde **Configuración del dispositivo** > **Plantillas administrativas** a **Configuración del dispositivo** > **Perfiles** >**Crear perfil** > en **Plataforma**, elija **Windows 10 y versiones posteriores**, en **Tipo de perfil**, elija **Plantillas administrativas**.
Se habilita el informe; se aplica a: Windows 10 y versiones posteriores


<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Uso de la configuración recomendada por Microsoft con líneas de base de seguridad <!-- 2055484 -->
Intune se integra con otros servicios centrados en la seguridad, incluidos ATP de Windows Defender y Office 365 ATP. Los clientes solicitan una estrategia común y un conjunto coherente de flujos de trabajo de seguridad integrales entre los servicios de Microsoft 365. Nuestro objetivo es alinear las estrategias para crear soluciones que actúen de puente entre las operaciones de seguridad y las tareas de administración comunes. En Intune, este objetivo se pretende lograr mediante la publicación de un conjunto de "Líneas de base de seguridad" recomendadas de Microsoft (**Intune** > **Líneas de base de seguridad**).  Un administrador podrá crear directivas de seguridad directamente a partir de estas líneas de base y, después, implementarlas en sus usuarios. También se pueden personalizar los procedimientos recomendados para satisfacer las necesidades de la organización. Intune garantiza que los dispositivos cumplan estas líneas de base y notifica a los administradores los usuarios o dispositivos que no están en cumplimiento.

### <a name="scope-tags-for-apps---1081941---"></a>Etiquetas de ámbito para las aplicaciones <!--1081941 -->
Podrá crear etiquetas de ámbito para limitar el acceso a los recursos de Intune. Agregue una etiqueta de ámbito a una asignación de roles y luego agregue dicha etiqueta a un perfil de configuración. El rol solo tendrá acceso a los recursos con perfiles de configuración que tengan etiquetas de ámbito coincidentes (o no tengan ninguna etiqueta de ámbito).
Para crear una etiqueta de ámbito, elija **Roles de Intune** > **Ámbito (etiquetas)** > **Crear**.
Para agregar una etiqueta de ámbito a una asignación de rol, elija **Roles de Intune** > **Todos los roles** > **Policy and profile manager (Administrador de directivas y perfiles)** > **Asignaciones** > **Ámbito (etiquetas)**.
Para agregar una etiqueta de ámbito a un perfil de configuración, elija **Configuración del dispositivo** > **Perfiles** > elija un perfil > **Propiedades** > **Ámbito (etiquetas)**.

### <a name="tenant-health-dashboard----1124854---"></a>Panel de estado del inquilino <!-- 1124854 -->
En la página Estado del inquilino de Intune se proporciona información de estado del inquilino en un solo lugar. La página se divide en cuatro secciones:  
- **Detalles del inquilino**: contiene información, como la autoridad de MDM, el número total de dispositivos inscritos en el inquilino y el recuento de licencias. En esta sección también se proporciona la versión actual del servicio para el inquilino.
- **Estado del conector**: contiene información de los conectores configurados, como PCV de Apple, Microsoft Store para Empresas y los conectores de certificados. En función de su estado actual, los conectores se marcan como *Correcto*, *Advertencia* o *Incorrecto*.
- **Service Health para Intune**: contiene los incidentes activos o las interrupciones del inquilino. La información de esta sección se recupera directamente del Centro de mensajes de Office ([https://portal.office.com](https://portal.office.com)).
- **Noticias de Intune**: contiene mensajes activos para el inquilino, que incluyen elementos como las notificaciones que el inquilino ha recibido sobre las características de Intune más recientes. La información de esta sección se recupera directamente del Centro de mensajes de Office ([https://portal.office.com](https://portal.office.com)).


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


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Cambio en el proceso de actualización para conectores locales <!-- 2277554 -->
Según los comentarios de clientes, se cambiará la manera en que se realizan las actualizaciones en los conectores locales. Después de instalar inicialmente un conector local, las actualizaciones se producirán automáticamente. Este cambio se iniciará con el nuevo conector de certificado PFX para Microsoft Intune y posteriormente se implementará en otros tipos de conectores locales. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Comprobar cumplimiento de Configuration Manager <!-- 2192052 -->
Una actualización futura incluirá una nueva configuración de conformidad de System Center Configuration Manager (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Windows 10**). Configuration Manager envía señales a la conformidad de Intune. Mediante la configuración de Intune, puede exigir que todas las señales de Configuration Manager devuelvan “conforme”.

Por ejemplo, exige que todas las actualizaciones de software se instalen en los dispositivos. En Configuration Manager, este requisito tiene el estado “Instalado”. Si algún programa del dispositivo se encuentra en estado desconocido, el dispositivo no será conforme en Intune.

Se aplica a Windows 10 y versiones posteriores



## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.

### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.



