---
title: Edición anticipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6cc33bc6e03d2e0370c9e2c2dd9d3462296710e6
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329691"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>La edición anticipada de Microsoft Intune: agosto de 2018

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

<!-- 1808 start -->



### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP de Apple usado por otro MDM <!-- 1488946 -->
Intune detectará y mostrará los detalles si un token de programa de compras por volumen (VPP) de Apple lo está usando Intune y otro MDM.

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>Se muestran el número de versión y el número de compilación de iOS <!-- 1892471 -->
En **Cumplimiento del dispositivo** > **Cumplimiento del dispositivo**, se muestra la versión del sistema operativo iOS. En una actualización futura, también se mostrará el número de compilación.
Cuando se publican las actualizaciones de seguridad, Apple normalmente deja el número de versión como está, pero actualiza el número de compilación. Al mostrar el número de compilación, puede comprobar fácilmente si se instala una actualización de vulnerabilidad.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos retirados en el panel de cumplimiento del dispositivos <!-- 1981119 -->
En una actualización futura, los dispositivos retirados se quitarán del panel de cumplimiento del dispositivo. Esto cambiará los números de cumplimiento.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Actualización de la experiencia de usuario en el sitio web de Portal de empresa <!--2000968 -->
Tras escuchar los comentarios de los clientes, se agregarán nuevas características al sitio web de Portal de empresa. Podrá comprobar una mejora considerable en las funciones y la facilidad de uso actual de los dispositivos Android, iOS y Windows. Se aplicará un diseño moderno y receptivo a las áreas del sitio, como los detalles del dispositivo, los comentarios, el soporte técnico y la descripción general del dispositivo. También verá:
- Flujos de trabajo simplificados en todas las plataformas del dispositivo
- Flujos mejorados para la identificación y la inscripción de dispositivos
- Mensajes de error más útiles
- Lenguaje más descriptivo con menos jerga técnica
- Posibilidad de compartir vínculos directos a aplicaciones
- Mejor rendimiento de los catálogos de aplicaciones de gran tamaño
- Mayor accesibilidad para todos los usuarios

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configuración del perfil para omitir algunas pantallas durante el Asistente para configuración <!-- 2276470 -->
Cuando cree un perfil de inscripción de macOS, podrá configurarlo para omitir cualquiera de las siguientes pantallas cuando un usuario recorra el Asistente para configuración:
- Migración de Android
- Tono de visualización
- Privacidad
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Cambio en el proceso de actualización para conectores locales <!-- 2277554 -->
Según los comentarios de clientes, se cambiará la manera en que se realizan las actualizaciones en los conectores locales. Después de instalar inicialmente un conector local, las actualizaciones se producirán automáticamente. Este cambio se iniciará con el nuevo conector de certificado PFX para Microsoft Intune y posteriormente se implementará en otros tipos de conectores locales. 



<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>Más oportunidades de sincronización en la aplicación Portal de empresa para Windows <!-- 2683177 -->
La aplicación Portal de empresa para Windows agrega una acción de sincronización de dispositivo a la barra de tareas de Windows y listas de salto al menú Inicio. Haga clic en cualquier ubicación para sincronizar rápidamente los dispositivos y obtener acceso a recursos corporativos.  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Códigos de acceso para restablecer el dispositivo desde la aplicación Portal de empresa para Windows 10 <!-- 2101282 --> 
Los empleados pronto podrán restablecer el PIN o el código de acceso de su dispositivo directamente desde la aplicación Portal de empresa para Windows 10. Esta funcionalidad estará disponible en los dispositivos remotos y locales administrados por Intune que admiten el restablecimiento de la contraseña. Según el tipo de dispositivo, una solicitud realizada para un dispositivo remoto eliminará el código de acceso actual del dispositivo o creará una contraseña temporal. Si un usuario solicita el restablecimiento para un dispositivo local, se le redirigirá a la aplicación de configuración del dispositivo.  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>Nuevas experiencias de navegación en la aplicación Portal de empresa para Windows <!-- 2317227 -->  
Al examinar o buscar aplicaciones en la aplicación Portal de empresa para Windows, podrá alternar entre la vista **Elementos** existente y la vista recién añadida **Detalles**. En la nueva vista se muestran detalles de la aplicación, como el nombre, el editor, la fecha de publicación y el estado de la instalación.  

La página **Aplicaciones** presentará una vista **Instaladas** que le permite ver detalles sobre las instalaciones de aplicaciones completadas y en curso. ¿Quiere compartir comentarios y opiniones sobre los nuevos cambios? Envíenos sus comentarios en la aplicación Portal de empresa.

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Mejora de la experiencia en la aplicación Portal de empresa para usuarios administradores de inscripciones de dispositivos <!-- 675800 -->
Cuando un administrador de inscripciones de dispositivos (DEM) inicia sesión en la aplicación Portal de empresa para Windows, la aplicación solo mostrará el dispositivo actual en ejecución de DEM. Esta mejora reduce los tiempos de espera que se han producido anteriormente cuando la aplicación ha intentado cargar todos los dispositivos inscritos en DEM.  

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Use licencias de dispositivo de VPP para tener en servicio el Portal de empresa durante la inscripción de DEP <!-- 1608345 -->
Podrá usar licencias de dispositivo del Programa de Compras por Volumen (VPP) para tener en servicio el Portal de empresa durante las inscripciones en el Programa de inscripción de dispositivos (DEP). Para ello, al crear o editar un perfil de inscripción, especifique el token de VPP que quiera usar para instalar el Portal de empresa. Asegúrese de que el token no expire y que dispone de suficientes licencias para la aplicación de Portal de empresa. En los casos en los que el token expire o se agoten las licencias, Intune instalará el Portal de empresa del App Store (se solicitará un identificador de Apple).

### <a name="check-for-sccm-compliance----2192052---"></a>Comprobación de la conformidad de SCCM <!-- 2192052 -->
Una actualización futura incluirá una nueva configuración de conformidad de System Center Configuration Manager (SCCM) (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Windows 10**). SCCM envía señales a la conformidad de Intune. Mediante la configuración de Intune, puede exigir que todas las señales de SCCM devuelvan "conforme".

Por ejemplo, exige que todas las actualizaciones de software se instalen en los dispositivos. En SCCM, este requisito tiene el estado "Instalado". Si algún programa del dispositivo se encuentra en estado desconocido, el dispositivo no será conforme en Intune.

Se aplica a Windows 10 y versiones posteriores

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas sobre tokens de VPP que expiran próximamente o licencias del Portal de empresa a punto de agotarse <!-- 2237572 -->
Si usa el Programa de Compras por Volumen (VPP) para tener en servicio el Portal de empresa durante la inscripción de DEP, Intune le avisará cuando el token de VPP esté a punto de expirar y las licencias del Portal de empresa se estén agotando.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmación requerida para eliminar el token de VPP que se usa para tener en servicio el Portal de empresa <!-- 2237634 -->
Se solicitará confirmación para eliminar un token del Programa de Compras por Volumen (VPP) si se usa para tener en servicio el Portal de empresa durante la inscripción de DEP.

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Configuración de seguridad adicional de Windows Installer <!-- 2282430 -->
Podrá dejar que los usuarios controlen las instalaciones de aplicaciones. Si lo permite, las instalaciones que antes se detendrían debido a una infracción de seguridad podrán seguir funcionando. Podrá indicar a Windows Installer que use permisos elevados cuando instale un programa en un sistema. Además, podrá habilitar elementos protegidos por WIP (Windows Information Protection) para indexarlos y almacenar los metadatos relativos a estos elementos en una ubicación sin cifrar. Cuando la directiva está deshabilitada, los elementos protegidos por WIP no se indexarán ni se mostrarán en los resultados de Cortana o del explorador de archivos. La funcionalidad de estas opciones estará deshabilitada de forma predeterminada. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Configuración de la directiva de protección de aplicaciones para el bloqueo de teclados de terceros en iOS <!-- 1248481 -->
En dispositivos iOS, los administradores de Intune podrán bloquear el uso de teclados de terceros al acceder a datos de la organización en aplicaciones protegidas mediante directiva. Cuando la directiva de protección de aplicación (APP) esté configurada para bloquear teclados de terceros, el usuario del dispositivo recibirá un mensaje la primera vez que interactúe con datos corporativos usando un teclado de terceros. Se bloquearán todas las demás opciones, que no afecten al teclado nativo, y los usuarios de los dispositivos no podrán verlas. Los usuarios de los dispositivos verán el mensaje del cuadro de diálogo una vez. 

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Exigir código de acceso no biométrico al transcurrir tiempo de espera y al iniciar la aplicación <!-- 1506985 -->

Al exigir un código de acceso no biométrico al iniciar la aplicación y después de transcurrir un tiempo de espera especificado por el administrador, Intune proporcionará una mayor seguridad para las aplicaciones compatibles con Administración de aplicaciones de móviles (MAM), ya que restringe el uso de identificación biométrica para el acceso a datos corporativos. La configuración afectará a los usuarios que dependen de Touch ID (iOS), Face ID (iOS), Android Biometric u otros métodos de autenticación biométrica futuros para tener acceso a aplicaciones compatibles con APP/MAM. Con esta configuración, los administradores de Intune tendrán un control más detallado sobre el acceso de los usuarios. De este modo, se evitan situaciones en las que un dispositivo con varias huellas digitales u otros métodos de acceso biométrico pueda revelar datos corporativos a un usuario incorrecto. En Azure Portal, abra **Microsoft Intune**. Seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones** > **Agregar una directiva** > **Configuración**. En la **Acceso** encontrará ajustes específicos.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Paquetes de idioma de Office 365 Pro Plus <!-- 1833450 -->
Como administrador de Intune, podrá implementar idiomas adicionales para las aplicaciones Office 365 Pro Plus administradas mediante Intune. La lista de idiomas disponibles incluye el **Tipo** de paquete de idioma (núcleo, parcial y corrección). En Azure Portal, seleccione **Microsoft Intune** > **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. En la lista **Tipo de aplicación** de la hoja **Agregar aplicación**, seleccione **Windows 10** en **Conjunto de aplicaciones de Office 365**. Seleccione **Idiomas** en la hoja **Configuración del conjunto de aplicaciones**.

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Obtener una versión preliminar de una actualización de la experiencia de usuario en el sitio web de Portal de empresa <!--2000968 -->
Tras escuchar las opiniones de los clientes, estamos agregando nuevas características al sitio web de Portal de empresa y al catálogo de aplicaciones de iOS. Podrá comprobar una mejora considerable en las funciones y la facilidad de uso actual de los dispositivos Android, iOS y Windows. Se aplicará un diseño moderno y receptivo a las áreas del sitio, como los detalles del dispositivo, los comentarios, el soporte técnico y la descripción general del dispositivo. También verá:

- Flujos de trabajo simplificados en todas las plataformas del dispositivo
- Flujos mejorados para la identificación y la inscripción de dispositivos
- Mensajes de error más útiles
- Lenguaje más descriptivo con menos jerga técnica
- Posibilidad de compartir vínculos directos a aplicaciones
- Mejor rendimiento de los catálogos de aplicaciones de gran tamaño
- Mayor accesibilidad para todos los usuarios

Actualmente, la actualización está disponible en versión preliminar. Puede registrarse para unirse a la versión preliminar en http://aka.ms/webcpflighting.

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Exigir código de acceso no biométrico al transcurrir tiempo de espera y al iniciar la aplicación en frío<!-- 1506985 --> 

Al exigir un código de acceso no biométrico al iniciar la aplicación en frío y después de transcurrir un tiempo de espera especificado por el administrador, Intune proporcionará una mayor seguridad para las aplicaciones compatibles con Administración de aplicaciones de móviles (MAM), ya que restringe el uso de identificación biométrica para el acceso a datos corporativos. La configuración afectará a los usuarios que dependen de Touch ID (iOS), Face ID (iOS), Android Biometric u otros métodos de autenticación biométrica futuros para tener acceso a aplicaciones compatibles con APP/MAM. Con esta configuración, los administradores de Intune tendrán un control más detallado sobre el acceso de los usuarios. De este modo, se evitan situaciones en las que un dispositivo con varias huellas digitales u otros métodos de acceso biométrico pueda revelar datos corporativos a un usuario incorrecto. En Azure Portal, abra **Microsoft Intune**. Seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones** > **Agregar una directiva** > **Configuración**. En la **Acceso** encontrará ajustes específicos.

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidad de implementar aplicaciones de línea de negocio (LOB) requeridas en todos los usuarios en dispositivos Windows 10 Escritorio <!-- 1627835 RS4 -->
Los clientes podrán implementar aplicaciones de Windows 10 de línea de negocio requeridas para instalarlas en contextos de dispositivo. Esto permitirá que estas aplicaciones estén disponibles para todos los usuarios del dispositivo. Esto solo es aplicable a dispositivos Windows 10 Escritorio.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Actualización de la experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android <!--1631531 -->

La experiencia de ayuda y comentarios en la aplicación Portal de empresa para Android se actualizará de acuerdo con los procedimientos recomendados para las aplicaciones Android. En los próximos meses actualizaremos la aplicación Portal de empresa para Android para dividir el elemento de menú **Ayuda y comentarios** en los elementos de menú independientes **Ayuda** y **Enviar comentarios**. En la página **Ayuda** se incluirá una sección **Preguntas más frecuentes** y un botón **Soporte por correo electrónico** para permitir a los usuarios finales cargar registros a Microsoft y enviar al equipo de soporte técnico de la empresa un correo electrónico en el que se describa el problema. **Enviar comentarios** llevará al usuario a través de un proceso estándar de envío de comentarios de Microsoft, en el que se le pedirá elegir entre "Me gusta algo", "No me gusta algo" o "Tengo una idea".

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Directivas de protección de aplicaciones  <!-- 679615 -->
Las directivas de Intune App Protection ofrecerán la capacidad de crear directivas predeterminadas globales para habilitar rápidamente la protección en todos los usuarios de todo el inquilino.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.

### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.



