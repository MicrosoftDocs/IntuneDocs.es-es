---
title: "Edición anticipada"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 09/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0ac0d1fd2f618339f847201f333d3f32561ca6b1
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2017
---
# <a name="the-early-edition-for-microsoft-intune---september-2017"></a>La edición anticipada de Microsoft Intune: septiembre de 2017

La **edición anticipada** proporciona una lista de características que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No comparta esta información fuera de la compañía. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

> [!Note]
>Los siguientes cambios están en fase de desarrollo de Intune. Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--

## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
   
-->

  

## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure


### <a name="google-play-protect-support-on-android----908720----"></a>Compatibilidad con Google Play Protect en Android <!-- 908720  -->  
Con el lanzamiento de Android Oreo, Google presenta un conjunto de características de seguridad denominado Google Play Protect que permite a los usuarios y las organizaciones ejecutar aplicaciones e imágenes de Android seguras. Intune admite las características de Google Play Protect, incluida la atestación remota de SafetyNet.  Los administradores pueden establecer requisitos para directivas de cumplimiento que exijan que Google Play Protect esté configurado y en buen estado. La opción **SafetyNet device attestation** (Atestación de dispositivo SafetyNet)* requiere que el dispositivo se conecte con un servicio de Google para comprobar que se encuentra en buen estado y no está en riesgo. Los administradores también pueden establecer una opción en el perfil de configuración de Android for Work para requerir que se comprueben las aplicaciones instaladas por los servicios de Google Play.  El acceso condicional puede impedir que los usuarios tengan acceso a los recursos corporativos si un dispositivo no es compatible con los requisitos de Google Play Protect. 

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Restricción para impedir que los usuarios de dispositivos Android puedan cambiar la fecha y la hora de sus dispositivos <!-- 1333292 -->
Puede usar una [directiva de dispositivo personalizada de Android](custom-settings-android.md) para impedir que los usuarios de dispositivos Android cambien la fecha y la hora del dispositivo.
Para ello, configure una directiva personalizada de Android con el URI de configuración ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange. Establezca este parámetro en **TRUE** y luego asígnelo a los grupos requeridos.

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Visualización de las asignaciones de directivas de protección de aplicaciones para la solución de problemas <!--  1475003 -->
En la próxima versión, la opción **Directiva de protección de aplicaciones** se agregará a la lista desplegable **Asignaciones** disponible en la hoja de la solución de problemas. Ahora puede seleccionar las directivas de protección de aplicaciones para ver las directivas de protección de aplicaciones asignadas a los usuarios seleccionados.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Creación de aplicaciones iOS limitadas a determinadas instancias regionales de App Store de Apple <!-- 1281692 -->
Podrá especificar la configuración regional del país durante la creación de una aplicación administrada de App Store de Apple.

> [!NOTE]  
> Actualmente, solo puede crear aplicaciones administradas de App Store de Apple que se encuentren en la instancia de Estados Unidos.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selección de la instancia de App Store de Apple del país para la sincronización de aplicaciones de VPP  <!-- 1332311 -->  
Puede configurar la instancia de App Store del país para el Programa de Compras por Volumen de Apple (VPP) al cargar el token de VPP. Intune sincroniza las aplicaciones de VPP para todas las configuraciones regionales desde la instancia de App Store del país de VPP especificada.

> [!NOTE]  
> En la actualidad, Intune solo sincroniza las aplicaciones de VPP de la instancia de App Store del país de VPP que coinciden con la configuración regional de Intune en la que se creó el inquilino de Intune.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Actualización de aplicaciones con licencia para dispositivos y usuarios de VPP de iOS  <!-- 1305564 -->  
Podrá configurar el token de VPP de iOS para actualizar todas las aplicaciones adquiridas para ese token a través del servicio de Intune. Intune detectará las actualizaciones de la aplicación de VPP dentro de la App Store y las insertará automáticamente en el dispositivo cuando este se registra.

### <a name="ios-11-support----1428975---"></a>Compatibilidad con iOS 11 <!-- 1428975 -->
Cuando Apple lo publique, Intune admitirá el sistema operativo iOS 11.

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838----"></a>Nueva configuración del perfil de restricción de dispositivo Windows 10 Team  <!--- 1308838  -->
En esta versión, agregamos muchas configuraciones nuevas al perfil de restricción de dispositivo de Windows 10 Team para ayudarle a controlar los dispositivos de Surface Hub.
Para obtener más información sobre este perfil, vea [Configuración de restricciones de dispositivos Windows 10 Team en Microsoft Intune](device-restrictions-windows-10-teams.md).

### <a name="support-for-windows-10-edition-upgrade-policy------903672-1119689---"></a>Compatibilidad con una directiva de actualización de la edición de Windows 10   <!-- 903672, 1119689 -->  
Podrá crear una directiva de actualización de la edición de Windows 10 que actualice los dispositivos con Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education y Windows 10 Professional Education N. Para obtener más información acerca de las actualizaciones de la edición de Windows 10, consulte [Configuración de actualizaciones de la edición de Windows 10 en Microsoft Intune](edition-upgrade-configure-windows-10.md).

### <a name="review-policy-compliance-for-windows-10-update-rings----1352223---"></a>Revisión del cumplimiento de directivas para los anillos de actualizaciones de Windows 10 <!-- 1352223 -->  
Podrá revisar un informe de directiva para los anillos de actualizaciones de Windows 10 desde **Actualizaciones de software** > **Estado de implementación por anillo de actualización**. El informe de directiva incluye el estado de implementación para los anillos de actualización que ha configurado. 

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Adición de la aplicación de Portal de empresa de Windows 10 a la directiva de permiso de Windows Information Protection <!-- 677129 -->  
La aplicación de Portal de empresa de Windows 10 se actualizará para admitir Windows Information Protection (WIP). La aplicación puede agregarse a la directiva de permiso de WIP. Con este cambio, la aplicación ya no tiene que agregarse a la lista **Excluir**. 

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Soporte remoto para Windows y dispositivos Windows Mobile  <!-- 1070473 -->    
Intune podrá utilizar el software [TeamViewer](https://www.teamviewer.com), comprado por separado, para que pueda ofrecer asistencia remota a los usuarios que estén ejecutando Windows y dispositivos Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Examen de dispositivos con Windows Defender <!-- 1280988  1280990   -->
Podrá ejecutar un **Examen rápido** y un **Examen completo**, además de **Actualizar firmas**, con el antivirus Windows Defender en los dispositivos Windows 10 administrados. En la hoja de información general del dispositivo, elija la acción que desea ejecutar en el dispositivo. Se le pide que confirme la acción antes de que el comando se envíe al dispositivo. 

**Examen rápido**: un examen rápido examina ubicaciones donde el malware se registra para iniciarse, como las claves del registro y las carpetas de inicio de Windows conocidas. Un examen rápido tarda de media cinco minutos. Al combinarlo con la opción **Always-on real-time protection** (Protección en tiempo real siempre activa), que examina los archivos cuando están abiertos o cerrados y siempre que un usuario navega a una carpeta, el examen rápido ayuda a proporcionar protección frente a malware que podría estar en el sistema o el kernel. Los usuarios ven los resultados del examen en sus dispositivos cuando termina. 

**Examen completo**: un examen completo puede resultar útil en los dispositivos que han encontrado una amenaza de malware para identificar si existe algún componente inactivo que requiera una limpieza más exhaustiva, además de para ejecutar exámenes a petición. El examen completo puede tardar una hora en ejecutarse. Los usuarios ven los resultados del examen en sus dispositivos cuando termina. 

**Actualizar firmas**: el comando de actualización de firmas actualiza las definiciones y las firmas de malware del antivirus de Windows Defender. Esto le ayuda a asegurarse de que el antivirus de Windows Defender es eficaz en la detección de malware. Esta característica es para dispositivos Windows 10 únicamente, está pendiente la conectividad a Internet de los dispositivos. 

### <a name="bitlocker-device-configuration----1397398---"></a>Configuración del dispositivo de BitLocker <!-- 1397398 -->  
La opción **Cifrado de Windows > Configuración base ** incluirá el nuevo ajuste **Warning for another disk encryption** (Advertencia para otro cifrado de disco)* que le permite deshabilitar el [mensaje de advertencia](https://docs.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) para otro cifrado de disco que podría estar en uso en el dispositivo del usuario.  El mensaje de advertencia requiere el consentimiento del usuario final antes de configurar BitLocker en el dispositivo y bloquea la instalación de BitLocker hasta que este la confirme.  La nueva configuración deshabilita la advertencia del usuario final.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Puesta en modo de mantenimiento del Portal de empresa para Windows 8.1 y Windows Phone 8.1 <!--1428681-->
A partir de octubre de 2017, las aplicaciones de Portal de empresa para Windows 8.1 y Windows Phone 8.1 pasarán a modo de mantenimiento. Esto significa que las aplicaciones y los escenarios existentes, como la inscripción y el cumplimiento, seguirán siendo compatibles para estas plataformas. Estas aplicaciones seguirán estando disponibles para su descarga a través de los canales de lanzamiento existentes, como Microsoft Store. 

Una vez que se encuentre en modo de mantenimiento, estas aplicaciones solo recibirán actualizaciones de seguridad críticas. No se publicarán actualizaciones ni características para estas aplicaciones. Para las nuevas características, se recomienda que actualice los dispositivos a Windows 10 o Windows 10 Mobile. 

###  <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloqueo de las acciones de copiar y pegar entre perfiles profesionales y personales en Android for Work <!-- 1098994 -->   
Con esta versión, es posible configurar el perfil del trabajo para Android for Work a fin de bloquear las acciones de copiar y pegar entre aplicaciones profesionales y personales. Puede encontrar esta nueva opción de configuración en el perfil **Restricciones de dispositivos** para la plataforma **Android for Work** en **Configuración del perfil de trabajo**.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nuevos comportamientos para la aplicación de Portal de empresa para Android con perfiles de trabajo <!---1485783--->
Cuando inscribe un dispositivo de Android for Work con un perfil de trabajo, la aplicación de Portal de empresa del perfil de trabajo es quien realiza las tareas de administración en el dispositivo. A menos que utilice una aplicación habilitada para MAM en el perfil personal, la aplicación de Portal de empresa para Android ya no tiene ninguna utilidad. Para mejorar la experiencia de perfil de trabajo, Intune ocultará automáticamente la aplicación de Portal de empresa personal una vez que se complete correctamente la inscripción del perfil de trabajo.

La aplicación Portal de empresa para Android se puede habilitar en cualquier momento en el perfil personal; para ello, vaya a [Portal de empresa de en Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) y pulse en **Habilitar**.

### <a name="intune-mam--outlook-for-android-add-ins-----1450688---"></a>Complementos MAM de Intune y Outlook para Android  <!-- 1450688 -->
En unas cuantas semanas, el equipo de Office anunciará complementos para Outlook en Android. Este conjunto de características de los complementos ya existe en Outlook en Windows, iOS, la Web y Mac. Dado que los complementos se administran mediante Exchange, los usuarios podrán copiar y compartir datos y mensajes entre Outlook y aplicaciones de complementos sin administrar, a no ser que el acceso a los complementos se desactive por parte del administrador de Exchange. 

Para administrar permisos de acceso de usuario para complementos, trabaje con el administrador de Exchange para asegurarse de que las directivas de protección de datos de MAM se aplican a los complementos.

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Si las directivas de Exchange ya están configuradas para evitar la transferencia local o la instalación de complementos, no hace falta que siga leyendo. Las directivas de MAM se aplicarán según lo previsto. Sin embargo, si ha configurado las directivas de MAM para restringir las operaciones de cortar, copiar y pegar dentro de Outlook en Android y no ha configurado la directiva de complementos en Exchange, debe saber que, de manera predeterminada, los usuarios podrán instalar complementos para Outlook. Estos complementos pueden tener acceso al cuerpo y al asunto del mensaje y a otras propiedades de este. Puede desactivar la capacidad del usuario final de instalar complementos; para ello, pida al Administrador de Exchange que quite los roles "My Marketplace Apps" (Mis aplicaciones de Marketplace) y "My Custom Apps". (Mis aplicaciones personalizadas). Para obtener más información, consulte el vínculo de información adicional compartido abajo.

Tenga en cuenta que el cambio de configuración de Exchange se aplicará a Outlook en Windows, iOS, la Web, Mac y los móviles. 

#### <a name="what-do-i-need-to-do"></a>¿Qué tengo que hacer?
Revise las directivas de Exchange hoy mimo. Informe al departamento de TI y al personal de soporte técnico. Póngase en contacto con nuestro equipo de soporte técnico para consultar cualquier pregunta o duda. 

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Adición de colección de entidad de asociación de dispositivo de usuario al modelo de datos de almacenamiento de datos de Intune <!-- 1187917 -->
Podrá generar informes y visualizaciones de datos con la información de asociación de dispositivo de usuario que asocia las colecciones de la entidad de dispositivo y de usuario. Es posible tener acceso al modelo de datos a través del archivo de Power BI (PBIX) recuperado de la página de almacenamiento de datos de Intune, a través del punto de conexión de OData o mediante el desarrollo de un cliente personalizado.


<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--"></a>Acciones en caso de incumplimiento <!--730266-->     
*Acciones en caso de incumplimiento* es una nueva característica de directivas de cumplimiento que le permite realizar acciones en dispositivos no compatibles. Puede especificar una o varias acciones y especificar el período de tiempo en el que se deben producir esas acciones. Por ejemplo, puede notificar a los usuarios de dispositivos no compatibles inmediatamente después de que el dispositivo se convierta en no compatible mediante el correo electrónico, o puede impedir que los dispositivos no compatibles tengan acceso a los recursos corporativos después de un período de gracia de 3 días mediante el acceso condicional.

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Nuevo informe que muestra los dispositivos iOS con versiones anteriores de iOS <!-- 1352223 -->
El informe **Dispositivos iOS obsoletos** estará disponible desde el área de trabajo **Actualizaciones de software**. En el informe, puede ver una lista de dispositivos iOS supervisados destinados mediante una directiva de actualización iOS y que tienen actualizaciones disponibles. Para cada dispositivo, puede ver un estado por el que el dispositivo no se ha actualizado automáticamente. 

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Nueva configuración del perfil de restricción de dispositivos Windows 10
<!--- 978575, 1308849, -->
Estamos agregando nuevas configuraciones al perfil de restricción de dispositivos Windows 10 en la categoría de SmartScreen de Windows Defender.

Para obtener información sobre el perfil de restricción de dispositivos Windows 10, vea [Configuración de restricciones de dispositivos Windows 10 y versiones posteriores]( device-restrictions-windows-10.md).

### <a name="android-for-work-support-for-lookout----1087312---"></a>Compatibilidad de Android for Work con Lookout <!-- 1087312 -->   
El conector de Intune con Lookout admitirá dispositivos de Android for Work cuando se use la aplicación Lookout for Work. Puede implementar la aplicación Lookout dentro o fuera del contenedor.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune App Protection y Herramientas de desarrollo de Citrix MDX <!-- 709185 -->
Puede administrar dispositivos y aplicaciones con una combinación de Citrix XenMobile MDX y Microsoft Intune. Esto le permite administrar aplicaciones con la directiva de protección de aplicaciones de Intune mientras usa tecnología mVPN de Citrix.

Puede buscar un repositorio de código que contiene la herramienta de ajuste de aplicaciones de Intune e Intune App SDK para iOS y Android, que se integra con la tecnología mVPN de Citrix MDX.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium: nuevo socio de defensa contra amenazas móviles <!-- 954681 -->
Puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Zimperium, una solución de defensa contra amenazas móviles integrada en Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funcionamiento de la integración con Intune
El riesgo se evalúa según la telemetría recopilada de dispositivos con Zimperium. Se pueden configurar directivas de acceso condicional de EMS según la evaluación de riesgos de Zimperium habilitada mediante las directivas de cumplimiento de los dispositivos de Intune, que puede usar para permitir o bloquear el acceso de los dispositivos no compatibles a los recursos corporativos en función de las amenazas detectadas.

### <a name="new-azure-ad-conditional-access-policy-ui-link-from-intune-----1016201---"></a>Nuevo vínculo de interfaz de usuario de la directiva de acceso condicional de Azure AD desde Intune <!-- 1016201 -->
Los administradores de TI pueden establecer directivas condicionales basadas en aplicaciones mediante la nueva interfaz de usuario de directivas de acceso condicional en la carga de trabajo de Azure AD. Las directivas de acceso condicional basadas en aplicaciones que están en la sección de Intune App Protection en Azure permanecen allí por el momento y se aplican en paralelo. También existirá un vínculo cómodo a la nueva interfaz de usuario de la directiva de acceso condicional en Azure AD desde la carga de trabajo de Intune.

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Compatibilidad de alta disponibilidad de On-premises Exchange Connector <!-- 676614 -->   
Puede tener varios roles de servidor de acceso de cliente (CAS) para el conector de Exchange local. Por ejemplo, si se produce un error en el CAS principal, Exchange Connector recibe una consulta para recurrir a otros CAS. Esta característica garantiza que no se interrumpa el servicio.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Módulo de administración de System Center Operations Manager para Exchange Connector <!-- 885457 -->   
El módulo de administración de System Center Operations Manager para Exchange Connector está disponible para ayudarle a analizar los registros de Exchange Connector. Este módulo de administración le proporciona distintas maneras de supervisar Intune cuando tenga que resolver problemas.

### <a name="end-of-support-for-ios-80----1164477---"></a>Fin de la compatibilidad con iOS 8.0 <!---1164477--->
Las aplicaciones administradas y la aplicación Portal de empresa para iOS exigirán iOS 9.0 y versiones posteriores para acceder a recursos de empresa. Los dispositivos que no estén actualizados antes de septiembre de este año ya no podrán acceder a esas aplicaciones ni al Portal de empresa.  

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fin de la compatibilidad con Android 4.3 y anterior <!---1171127, 1326920 --->
Las aplicaciones administradas y la aplicación Portal de empresa para Android exigirán Android 4.4 y versiones posteriores para acceder a recursos de empresa. Los dispositivos que no estén actualizados antes del comienzo de octubre ya no podrán acceder a esas aplicaciones ni al Portal de empresa. En diciembre, todos los dispositivos inscritos serán eliminados, lo que provocará su pérdida de acceso a los recursos de empresa. Si está usando directivas de protección de aplicaciones sin MDM, las aplicaciones no recibirán actualizaciones y la calidad de su experiencia empeorará con el tiempo.

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>Recordatorio de compatibilidad de plataforma: la compatibilidad estándar de Windows Phone 8.1 finalizará el 11 de julio de 2017 <!-- 1327781 -->  
El 11 de julio de 2017 terminará la compatibilidad estándar de la plataforma Windows Phone 8.1. La compatibilidad de los equipos Windows 8.1 no se verá afectada.

No hay ningún impacto inmediato en ningún dispositivo Windows Phone 8.1 administrado por el servicio Intune. Los dispositivos inscritos siguen funcionando y todas las directivas, configuraciones y aplicaciones seguirán funcionando según lo previsto. Tenga en cuenta que no hay mejoras destinadas a la plataforma Windows Phone 8.1 en el servicio Intune ni para la aplicación Portal de empresa de Windows Phone 8.1.

Se recomienda actualizar los dispositivos Windows Phone 8.1 aptos a Windows 10 Mobile en cuanto se pueda. 





## <a name="intune-apps"></a>Aplicaciones de Intune
### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Adición de acción de actualización a la aplicación de Portal de empresa para Windows 10 <!--1132468-->
La aplicación de Portal de empresa para Windows 10 permitirá a los usuarios actualizar los datos de la aplicación tirando para actualizar o, en equipos de escritorio, presionando F5.


### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Las aplicaciones que están disponibles con o sin inscripción ahora se pueden instalar sin que se les solicite la inscripción. <!-- 1334712 -->
Las aplicaciones de empresa que se han puesto a disposición de los usuarios con o sin inscripción en la aplicación de Portal de empresa de Android pueden instalarse sin necesidad de una solicitud de inscripción.

### <a name="ios-company-portal-display-large-icons----1454593---"></a>Visualización de iconos de gran tamaño en el Portal de empresa para iOS <!-- 1454593 -->
Estamos solucionando un problema conocido en relación con el modo en que el Portal de empresa de iOS muestra los iconos en el icono de la aplicación. Si carga iconos de aplicación de 120x120 píxeles o más, ahora se muestran en el [sitio web del Portal de empresa] (https://portal.manage.microsoft.com) y las páginas de aplicaciones del Portal de empresa de iOS al tamaño completo del icono de aplicaciones.

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android------1396349---"></a>Fraseado más fácil de entender para la aplicación de Portal de empresa para Android   <!---1396349--->    
El proceso de inscripción para la aplicación de Portal de empresa para Android se ha simplificado con nuevo texto para que resulte más sencillo para los usuarios finales. 


<!-- the following are present prior to 1709 -->


### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Compatibilidad de Intune Managed Browser con iOS y Android <!---1374196--->
A partir de octubre de 2017, la aplicación Intune Managed Browser en dispositivos Android admitirá solo los dispositivos con Android 4.4 y versiones posteriores. La aplicación Intune Managed Browser en iOS solo admitirá dispositivos con iOS 9.0 y versiones posteriores. Las versiones anteriores de iOS y Android podrán seguir usando Intune Managed Browser, pero no podrán instalar nuevas versiones de la aplicación y es posible que no puedan tener acceso a todas las funcionalidades de la aplicación. Le recomendamos que actualice estos dispositivos a una versión compatible del sistema operativo.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Permitir que los usuarios finales accedan a la aplicación Portal de empresa para Android sin inscripción <!---1169910--->  
Pronto los usuarios finales no tendrán que inscribir sus dispositivos para acceder a la aplicación Portal de empresa para Android. Los usuarios finales de las organizaciones que usen directivas de protección de aplicaciones dejarán de recibir mensajes para inscribir sus dispositivos cuando abran la aplicación Portal de empresa. Los usuarios finales también podrán instalar aplicaciones desde el Portal de empresa sin inscribir el dispositivo. 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensaje de error mejorado cuando un usuario alcanza el número máximo de dispositivos permitidos para la inscripción <!-- 1270370 -->
En lugar de un mensaje de error genérico, los usuarios finales ven un mensaje de error descriptivo que requiere acción: "Ya ha inscrito el máximo número de dispositivos permitidos por su administrador de TI. Quite un dispositivo inscrito o reciba ayuda de su administrador de TI".

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informar a los usuarios finales de la información de dispositivo que puede verse para iOS <!--739894-->
Estamos agregando **Tipo de propiedad** a la pantalla Detalles del dispositivo en la aplicación del portal de empresa para iOS. Esto permite a los usuarios obtener más información sobre privacidad directamente desde esta página de los documentos de usuario final de Intune. También podrán encontrar esta información en la pantalla Acerca de.

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>Las páginas de información de aplicaciones muestran información nueva para los dispositivos Android <!--1287476-->
La página de información de aplicaciones de la aplicación de portal de empresa para Android mostrará las categorías de aplicaciones que el administrador de TI ha definido para esa aplicación.

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>Ahora los cuadros de diálogo de administración de aplicaciones móviles (MAM) de Intune tienen una interfaz moderna <!-- 1199015 -->
Se han actualizado los cuadros de diálogo de administración de aplicaciones móviles (MAM) de Intune para tener una apariencia moderna. Los cuadros de diálogo funcionan de la misma manera que con el estilo anterior.

En los dispositivos Android modernos, los cuadros de diálogo de notificación o error que muestra Intune ahora tendrán una apariencia actualizada.



## <a name="notices"></a>Notificaciones
### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->   
Apple ha anunciado que, a partir de la primavera de 2017, se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS. Visite nuestro [blog de soporte técnico de Intune](https://aka.ms/compportalats) para obtener más información.

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Plan de cambio: Intune está cambiando la experiencia del portal Partner de Intune<!-- 1050016 -->
Estamos quitando la página Partner de Intune de manage.microsoft.com a partir de la actualización de servicio de mediados de mayo de 2017.  

Si es un administrador de partners, ya no podrá ver y realizar acciones en nombre de sus clientes desde la página Partner de Intune pero, en su lugar, tendrá que iniciar sesión en uno de los dos portales de partners de Microsoft.

Tanto el [Centro de partners de Microsoft](https://partnercenter.microsoft.com/) como el [Centro de administración de partners de Microsoft Office 365](https://portal.office.com/) le permitirá iniciar sesión en las cuentas de cliente que administra. En adelante, como partner, use uno de estos sitios para administrar a sus clientes.



### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.
