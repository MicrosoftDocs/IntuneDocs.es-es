---
title: Edición anticipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e37a45122ab4950e2a85cc1c6f6696759d429a3f
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828285"
---
# <a name="the-early-edition-for-microsoft-intune---october-2018"></a>La edición anticipada para Microsoft Intune: octubre de 2018

> [!Note]
> Notificación del acuerdo de confidencialidad: Los siguientes cambios están en fase de desarrollo para Intune. Esta información se comparte en el acuerdo de confidencialidad de forma muy limitada. No publique esta información en redes sociales ni sitios web públicos, como Twitter, UserVoice, Reddit, etc. 

La **edición anticipada** proporciona una lista de características, compartidas en el acuerdo de confidencialidad, que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No publique en un tweet, divulgue en UserVoice ni comparta de otra manera esta información fuera de su empresa. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Uso de la configuración recomendada por Microsoft con líneas de base de seguridad <!-- 2055484 -->
Intune se integra con otros servicios centrados en la seguridad, incluidos ATP de Windows Defender y Office 365 ATP. Los clientes solicitan una estrategia común y un conjunto coherente de flujos de trabajo de seguridad integrales entre los servicios de Microsoft 365. Nuestro objetivo es alinear las estrategias para crear soluciones que actúen de puente entre las operaciones de seguridad y las tareas de administración comunes. En Intune, este objetivo se pretende lograr mediante la publicación de un conjunto de "Líneas de base de seguridad" recomendadas de Microsoft (**Intune** > **Líneas de base de seguridad**).  Un administrador podrá crear directivas de seguridad directamente a partir de estas líneas de base y, después, implementarlas en sus usuarios. También se pueden personalizar los procedimientos recomendados para satisfacer las necesidades de la organización. Intune garantiza que los dispositivos cumplan estas líneas de base y notifica a los administradores los usuarios o dispositivos que no están en cumplimiento.

### <a name="remove-ability-for-admins-to-wipe-personal-devices-and-reset-passcodes----2934699---"></a>Eliminación de la capacidad de los administradores de borrar los dispositivos personales y restablecer las contraseñas <!-- 2934699 -->
Para reducir el temor de los usuarios de que los administradores de la empresa puedan borrar sus dispositivos personales, las acciones remotas [Borrar](devices-wipe.md#wipe) y [Restablecer contraseña](device-passcode-reset.md) dejarán de aplicarse a los dispositivos personales. Cambie el tipo de propiedad de dispositivo a corporativo para habilitar estas acciones para los dispositivos propiedad de la organización.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices----1048100---"></a>Compatibilidad con AutoPilot para dispositivos híbridos unidos a Azure Active Directory <!-- 1048100 -->
Podrá configurar dispositivos híbridos unidos a Azure Active Directory mediante AutoPilot. Los dispositivos deben estar unidos a la red de la organización para usar la característica de AutoPilot híbrida.

### <a name="scope-tags-for-apps---1081941---"></a>Etiquetas de ámbito para las aplicaciones <!--1081941 -->
Podrá crear etiquetas de ámbito para limitar el acceso a los recursos de Intune. Agregue una etiqueta de ámbito a una asignación de roles y luego agregue dicha etiqueta a un perfil de configuración. El rol solo tendrá acceso a los recursos con perfiles de configuración que tengan etiquetas de ámbito coincidentes (o no tengan ninguna etiqueta de ámbito).
Para crear una etiqueta de ámbito, elija **Roles de Intune** > **Ámbito (etiquetas)** > **Crear**.
Para agregar una etiqueta de ámbito a una asignación de rol, elija **Roles de Intune** > **Todos los roles** > **Policy and profile manager (Administrador de directivas y perfiles)** > **Asignaciones** > **Ámbito (etiquetas)**.
Para agregar una etiqueta de ámbito a un perfil de configuración, elija **Configuración del dispositivo** > **Perfiles** > elija un perfil > **Propiedades** > **Ámbito (etiquetas)**.

## <a name="tenant-health-dashboard----1124854---"></a>Panel de estado del inquilino <!-- 1124854 -->
En la página Estado del inquilino de Intune se proporciona información de estado del inquilino en un solo lugar. La página se divide en cuatro secciones:  
- **Detalles del inquilino**: contiene información como la autoridad de MDM, el total de los dispositivos inscritos en el inquilino y el número de licencias. En esta sección también se proporciona la versión actual del servicio para el inquilino.
- **Estado del conector**: contiene información de los conectores configurados, como PCV de Apple, Microsoft Store para Empresas y los conectores de certificados. En función de su estado actual, los conectores se marcan como *Correcto*, *Advertencia* o *Incorrecto*.
- **Service Health para Intune**: contiene los incidentes activos o las interrupciones para el inquilino. La información de esta sección se recupera directamente del Centro de mensajes de Office ([https://portal.office.com](https://portal.office.com)).
- **Noticias de Intune**: contiene mensajes activos para el inquilino, que incluyen elementos como las notificaciones que el inquilino ha recibido sobre las características de Intune más recientes. La información de esta sección se recupera directamente del Centro de mensajes de Office ([https://portal.office.com](https://portal.office.com)).

### <a name="enrollment-abandonment-report----1382924---"></a>Informe de abandono de la inscripción <!-- 1382924 -->
Un nuevo informe en el que se proporciona información detallada sobre las inscripciones abandonadas estará disponible en **Inscripción de dispositivos** > **Supervisión**.

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Directivas de WIP implementadas sin la inscripción del usuario <!-- 1434452 -->
Las directivas de Windows Information Protection (WIP) se podrán implementar sin requerir que los usuarios de MDM inscriban sus dispositivos Windows 10. Esta configuración permite a las empresas proteger sus documentos corporativos en función de la configuración de WIP, mientras que permite a los usuarios mantener la administración de sus propios dispositivos Windows. Una vez que los documentos están protegidos con una directiva de WIP, un administrador de Intune puede borrar de forma selectiva los datos protegidos. Mediante la selección del usuario y dispositivo, y el envío de una solicitud de borrado, todos los datos protegidos mediante la directiva de WIP quedarán inservibles. En Intune en Azure Portal, seleccione **Aplicación móvil** > **Borrado selectivo de aplicaciones**.


### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Adición de una imagen de marca personalizada para la aplicación Portal de empresa <!-- 1916266 -->
Como administrador de Microsoft Intune, podrá cargar una imagen de marca personalizada que se mostrará como imagen de fondo en la página de perfil del usuario en la aplicación Portal de empresa. Para obtener más información sobre cómo configurar la aplicación Portal de empresa, vea [How to configure the Microsoft Intune Company Portal app](company-portal-app.md) (Cómo configurar la aplicación Portal de empresa de Microsoft Intune).

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Agrupación de dispositivos inscritos en Windows Autopilot por identificador de correlación <!-- 2075110 -->
Intune admitirá la agrupación de dispositivos Windows mediante un identificador de correlación cuando se inscriban mediante [AutoPilot para dispositivos existentes](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) a través de Configuration Manager. El identificador de correlación es un parámetro del archivo de configuración de AutoPilot. Intune establecerá de forma automática el [atributo enrollmentProfileName de dispositivo de Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) para que sea igual a "OfflineAutopilotprofile-\<Id. de correlación\>". Esto permite la creación de grupos dinámicos de Azure AD arbitrarios en función del identificador de correlación a través del atributo enrollmentprofileName para las inscripciones de AutoPilot sin conexión. 


### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Compatibilidad con OAuth de iOS 12 en perfiles de correo electrónico de iOS <!--2155106 -->
Los perfiles de correo electrónico de iOS de Intune serán compatible con OAuth de iOS 12. Para ver esta característica, seleccione **Intune** > **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **OAuth**. Si esta opción está activada, sucederán dos cosas:
1. Se emitirá un perfil nuevo para los dispositivos que ya estén seleccionados como destino.
2. A los usuarios finales se les volverá a solicitar sus credenciales.

### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nueva configuración predeterminada "Tipo de contraseña requerida" para Android, Android Enterprise <!-- 2649963 -->
Al crear una directiva de cumplimiento (**Intune** > **Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Android** o **Android Enterprise** para Plataforma > Seguridad del sistema), el valor predeterminado de **Tipo de contraseña requerida** cambiará: Valor predeterminado actual: Valor predeterminado del dispositivo Nuevo valor predeterminado: Al menos numérica Se aplica a: Android, Android Enterprise

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Asignación de perfiles de AutoPilot al grupo virtual Todos los dispositivos<!--2715522 -->
Podrá asignar perfiles de AutoPilot al grupo virtual Todos los dispositivos. Para ello, elija **Inscripción de dispositivos** > **Inscripción Windows** > **Perfiles de implementación** > elija un perfil > **Tareas** > bajo **Asignar a** elija **Todos los dispositivos**.

### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Nuevos característica de términos de uso de Azure Active Directory <!-- 2870393 -->
Azure Active Directory tendrá una característica de términos de uso que puede usar en lugar de los términos y condiciones existentes de Intune. La característica de términos de uso de Azure AD proporciona más flexibilidad sobre qué términos se van a mostrar y cuándo, mejor compatibilidad de localización, mayor control sobre cómo se representan los términos y creación de informes mejorada. La característica de términos de uso de Azure AD requiere Azure Active Directory Premium P1, que también forma parte del conjunto de aplicaciones Enterprise Mobility + Security E3.


### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune mantendrá el idioma de Office localizado al actualizar Office en los equipos de los usuarios finales <!-- 2971030 -->
Cuando Intune instala Office en los equipos de los usuarios finales, estos recibirán automáticamente los mismos paquetes de idioma que tenían con las instalaciones de Office .MSI anteriores. 

<!-- 1809 start -->  

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Configuración de transferencia de datos de la aplicación de Intune en dispositivos iOS inscritos en MDM <!-- 2244713 -->
Podrá controlar por separado la configuración de transferencia de datos de la aplicación de Intune en dispositivos iOS inscritos en MDM y la especificación de la identidad del usuario inscrito. Los administradores que no usen el IntuneMAMUPN no observarán un cambio de comportamiento. Cuando esta función esté disponible, los administradores que usan el IntuneMAMUPN para controlar el comportamiento de la transferencia de datos en los dispositivos inscritos deben revisar la nueva configuración y actualizar la configuración de APP según sea necesario.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Usar una clave precompartida en un perfil de Wi-Fi de Windows 10 <!-- 2662938 -->
Podrá usar una clave precompartida (PSK) con el protocolo de seguridad WPA o WPA2-Personal para autenticar un perfil de configuración de Wi-Fi para Windows 10.
Actualmente, debe importar un perfil de Wi-Fi o crear un perfil personalizado para usar una clave precompartida. [Configuración de Wi-Fi para Windows 10](wi-fi-settings-windows.md) muestra la configuración actual. 

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Configuración de directiva de protección de la aplicación (APP) de datos web <!-- 2662995 -->
La configuración de directiva APP de contenido web en dispositivos iOS y Android se actualizará para controlar mejor los vínculos web http y https, así como la transferencia de datos a través de vínculos universales de iOS y vínculos de aplicación de Android.  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>La frecuencia de sincronización de dispositivos Autopilot se aumenta a cada 12 horas <!-- 2753673 -->
Los dispositivos Autopilot se sincronizarán cada 12 horas en lugar de cada 24 horas.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Actualizaciones de la página de aterrizaje de Intune y cambio del nombre del nodo <!--2867309 -->
Las actualizaciones a la página de aterrizaje de Intune incluirán iconos de supervisión nuevos y modificados y gráficos para una mejor visualización de datos. El nodo **Aplicaciones móviles** cambiará a **Aplicaciones cliente**.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>Aumento de acceso de usuario final mediante la aplicación Portal de empresa <!-- 772203 -->
Los usuarios finales podrán acceder a las acciones de cuenta clave, como restablecer la contraseña y su perfil de Azure AD, desde la aplicación Portal de empresa.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP de Apple usado por otro MDM <!-- 1488946 -->
Intune detectará y mostrará los detalles si un token de programa de compras por volumen (VPP) de Apple lo está usando Intune y otro MDM.

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>Se muestran el número de versión y el número de compilación de iOS <!-- 1892471 -->
En **Cumplimiento del dispositivo** > **Cumplimiento del dispositivo**, se muestra la versión del sistema operativo iOS. En una actualización futura, también se mostrará el número de compilación.
Cuando se publican las actualizaciones de seguridad, Apple normalmente deja el número de versión como está, pero actualiza el número de compilación. Al mostrar el número de compilación, puede comprobar fácilmente si se instala una actualización de vulnerabilidad.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos retirados en el panel de cumplimiento del dispositivos <!-- 1981119 -->
En una actualización futura, los dispositivos retirados se quitarán del panel de cumplimiento del dispositivo. Esto cambiará los números de cumplimiento.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Cambio en el proceso de actualización para conectores locales <!-- 2277554 -->
Según los comentarios de clientes, se cambiará la manera en que se realizan las actualizaciones en los conectores locales. Después de instalar inicialmente un conector local, las actualizaciones se producirán automáticamente. Este cambio se iniciará con el nuevo conector de certificado PFX para Microsoft Intune y posteriormente se implementará en otros tipos de conectores locales. 

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Mejora de la experiencia en la aplicación Portal de empresa para usuarios administradores de inscripciones de dispositivos <!-- 675800 -->
Cuando un administrador de inscripciones de dispositivos (DEM) inicia sesión en la aplicación Portal de empresa para Windows, la aplicación solo mostrará el dispositivo actual en ejecución de DEM. Esta mejora reduce los tiempos de espera que se han producido anteriormente cuando la aplicación ha intentado cargar todos los dispositivos inscritos en DEM.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Comprobar cumplimiento de Configuration Manager <!-- 2192052 -->
Una actualización futura incluirá una nueva configuración de conformidad de System Center Configuration Manager (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Windows 10**). Configuration Manager envía señales a la conformidad de Intune. Mediante la configuración de Intune, puede exigir que todas las señales de Configuration Manager devuelvan “conforme”.

Por ejemplo, exige que todas las actualizaciones de software se instalen en los dispositivos. En Configuration Manager, este requisito tiene el estado “Instalado”. Si algún programa del dispositivo se encuentra en estado desconocido, el dispositivo no será conforme en Intune.

Se aplica a Windows 10 y versiones posteriores

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas sobre tokens de VPP que expiran próximamente o licencias del Portal de empresa a punto de agotarse <!-- 2237572 -->
Si usa el Programa de Compras por Volumen (VPP) para tener en servicio el Portal de empresa durante la inscripción de DEP, Intune le avisará cuando el token de VPP esté a punto de expirar y las licencias del Portal de empresa se estén agotando.

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Configuración de la directiva de protección de aplicaciones para el bloqueo de teclados de terceros en iOS <!-- 1248481 -->
En dispositivos iOS, los administradores de Intune podrán bloquear el uso de teclados de terceros al acceder a datos de la organización en aplicaciones protegidas mediante directiva. Cuando la directiva de protección de aplicación (APP) esté configurada para bloquear teclados de terceros, el usuario del dispositivo recibirá un mensaje la primera vez que interactúe con datos corporativos usando un teclado de terceros. Se bloquearán todas las demás opciones, que no afecten al teclado nativo, y los usuarios de los dispositivos no podrán verlas. Los usuarios de los dispositivos verán el mensaje del cuadro de diálogo una vez. 

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>Requerir identificación que no sea biométrica después de tiempo de espera especificado <!-- 1506985 --> 

Al exigir un número de identificación personal no biométrico después de transcurrir un tiempo de espera especificado por el administrador, Intune proporcionará una mayor seguridad para las aplicaciones compatibles con Administración de aplicaciones de móviles (MAM), ya que restringe el uso de identificación biométrica para el acceso a datos corporativos. La configuración afectará a los usuarios que dependen de Touch ID (iOS), Face ID (iOS), Android Biometric u otros métodos de autenticación biométrica futuros para tener acceso a aplicaciones compatibles con APP/MAM. Con esta configuración, los administradores de Intune tendrán un control más detallado sobre el acceso de los usuarios. De este modo, se evitan situaciones en las que un dispositivo con varias huellas digitales u otros métodos de acceso biométrico pueda revelar datos corporativos a un usuario incorrecto. En Azure Portal, abra **Microsoft Intune**. Seleccione **Aplicaciones móviles** > **Directivas de protección de aplicaciones** > **Agregar una directiva** > **Configuración**. En la **Acceso** encontrará ajustes específicos.

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Actualización de la experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android <!--1631531 -->

La experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android se actualizará de acuerdo con los procedimientos recomendados para las aplicaciones Android. En los próximos meses actualizaremos la aplicación Portal de empresa para Android para dividir el elemento de menú **Ayuda y comentarios** en los elementos de menú independientes **Ayuda** y **Enviar comentarios**. En la página **Ayuda** se incluirá una sección **Preguntas más frecuentes** y un botón **Soporte por correo electrónico** para permitir a los usuarios finales cargar registros a Microsoft y enviar al equipo de soporte técnico de la empresa un correo electrónico en el que se describa el problema. **Enviar comentarios** llevará al usuario a través de un proceso estándar de envío de comentarios de Microsoft, en el que se le pedirá elegir entre "Me gusta algo", "No me gusta algo" o "Tengo una idea".



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.

### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.



