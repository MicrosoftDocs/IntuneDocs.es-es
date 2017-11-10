---
title: "Edición anticipada"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 11/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d612f0e3ff3f38d51488818916479e8291c9e453
ms.sourcegitcommit: 0f877251e6adf4e45b918cc8dc9193626727f2d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2017
---
# <a name="the-early-edition-for-microsoft-intune---november-2017"></a>Edición anticipada para Microsoft Intune: noviembre de 2017

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


### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Asignación de aplicaciones móviles de Office 365 a dispositivos iOS y Android mediante el tipo de aplicación integrada <!-- 1332318 -->
El tipo de aplicación **integrada** facilita la creación y la asignación de aplicaciones de Office 365 a los dispositivos iOS y Android administrados. Entre estas aplicaciones están las de O365, como Word, Excel, PowerPoint y OneDrive. Puede asignar aplicaciones específicas al tipo de aplicación y, luego, editar la configuración de la información de la aplicación.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Compatibilidad del inicio de sesión único con iOS <!-- 1333645 -->  
Es posible usar el inicio de sesión único para los usuarios de iOS. Las aplicaciones de iOS que están codificadas para buscar las credenciales de usuario en la carga de inicio de sesión único funcionarán con esta actualización de la configuración de carga. También puede utilizar el UPN y el identificador de dispositivo de Intune para configurar el nombre de la entidad de seguridad y el dominio Kerberos.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API de inventario de aplicaciones iOS 11 para la detección de amenazas en dispositivos móviles <!-- 1391759 -->
Intune recopila la información de inventario de aplicaciones de los dispositivos personales y corporativos, y la pone a disposición de los proveedores de detección de amenazas en dispositivos móviles (MTD), como Lookout for Work. Podrá recopilar el inventario de aplicaciones de los usuarios de dispositivos iOS 11 y versiones posteriores.

**Inventario de aplicaciones**  
Los inventarios de los dispositivos iOS 11 y versiones posteriores, tanto de empresa como personales, se envían al proveedor de servicios MTD. El inventario de aplicaciones incluye los datos siguientes:

 - Identificador de la aplicación
 - Versión de la aplicación
 - Nombre corto de la versión
 - Nombre de la aplicación
 - Tamaño del lote de aplicaciones
 - Tamaño dinámico de la aplicación
 - Aplicación validada o no validada
 - Aplicación administrada o no administrada

### <a name="audit-updates----1412961---"></a>Actualizaciones de auditoría <!-- 1412961 -->  
La auditoría de Intune proporciona un registro de las operaciones que implican cambios en Intune.  Todas las operaciones de creación, actualización, eliminación y tareas remotas se registran y se conservan durante un año.  Azure Portal proporciona una vista filtrable de los datos auditados durante los últimos 30 días en cada carga de trabajo.  Con la correspondiente API Graph es posible recuperar los datos de auditoría almacenados durante el último año. 

La auditoría se encuentra en el grupo **MONITOR**. El elemento de menú **Registros de auditoría** está disponible para cada una de las carga de trabajo.   

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocolo de texto permitido en aplicaciones administradas <!-- 1414050  -->
Las aplicaciones administradas por Intune App SDK podrán enviar mensajes SMS.

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Reinicio remoto de dispositivos iOS (solo supervisado) <!-- 1424595 -->
Con una acción del dispositivo, podrá reiniciar un dispositivo supervisado iOS 10.3 y versiones posteriores. Para obtener más información sobre el uso de la acción de reinicio del dispositivo, consulte [Reinicio remoto de los dispositivos con Intune](device-restart.md).

> [!Note]  
> Para usar este comando es necesario que el dispositivo esté supervisado y disponer del derecho de acceso **Bloqueo del dispositivo**. El dispositivo se reinicia inmediatamente. Después de un reinicio, los dispositivos iOS bloqueados mediante código de acceso no volverán a unirse a una red Wi-Fi y es posible que no puedan comunicarse con el servidor.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloqueo remoto de los dispositivos macOS administrados con Intune <!-- 1437691 -->
Si pierde un dispositivo macOS, puede bloquearlo y establecer en él un PIN de recuperación de 6 dígitos. Una vez bloqueado, la hoja de **información general del dispositivo** muestra el PIN hasta que se envía otra acción de dispositivo.

Para obtener más información, consulte [Bloqueo remoto de los dispositivos administrados con Intune](device-remote-lock.md).

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings------1455974-----"></a>Configuración de la frecuencia de informes de Protección contra amenazas avanzada de Windows Defender <!--- 1455974  --->
El servicio Protección contra amenazas avanzada de Windows Defender (WDATP) permite a los administradores gestionar la frecuencia con la que se generan informes relativos a los dispositivos administrados. Con la nueva opción **Frecuencia de informes de telemetría urgentes**, WDATP recopila datos y evalúa los riesgos con una frecuencia mayor. El valor predeterminado para los informes optimiza el rendimiento y la velocidad. Aumentar la frecuencia de los informes puede ser muy útil para dispositivos de alto riesgo. Esta configuración puede encontrarse en el perfil **ATP de Windows Defender** en **Configuraciones de dispositivos**.

### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>Modificación de la resolución de conflictos de asignación para aplicaciones de la tienda iOS <!-- 1480316 -->
Los usuarios finales pueden experimentar un cambio en la disponibilidad de las aplicaciones de la tienda iOS. Actualmente, una aplicación que se ha asignado a dos grupos con un conflicto entre **Requerido y Disponible** y **No aplicable** se resuelve como **Requerido y Disponible**. Con el cambio, una aplicación que experimente este conflicto se resuelve como **No aplicable**.

El cambio soluciona la confusión que se produce cuando una aplicación se asigna a varios grupos con propósitos de aplicación distintos.

Si quiere que la aplicación esté disponible en el portal de trabajo de la información y en el Portal de empresa antes de la publicación de la versión de noviembre, tiene dos opciones:

1. Quitar la asignación **No aplicable** para su grupo.
2. Crear un nuevo grupo que no incluya miembros con el propósito **Requerido y Disponible** asignado, y asignar ese grupo como **No aplicable**.

Para obtener más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).

> [!Note]
> Después del lanzamiento, la versión ya no podrá ver ni modificar las asignaciones de aplicación de administración de dispositivos móviles (MDM) en la consola de Intune clásica. No obstante, puede usar la consola de Azure o la API Graph de Intune para asignar las aplicaciones.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>Administración independiente de dispositivos Android for Work y dispositivos Android <!-- 1490731 -->
Intune admitirá la administración de inscripciones de dispositivos Android for Work independientemente de la plataforma Android. Esta configuración se administra en **Inscripción de dispositivos** > **Restricciones de inscripción** > **Restricciones de tipo de dispositivo**. (Anteriormente se encontraban bajo **Inscripción de dispositivos** > **Inscripción en Android for Work** > **Configuración de la inscripción de Android for Work**).

De forma predeterminada, la configuración de los dispositivos Android for Work será igual que la configuración de los dispositivos Android. Sin embargo, dejará de ser así tras modificar la configuración de Android for Work.
 
Si bloquea la inscripción de Android for Work personal, tan solo los dispositivos Android corporativos podrán inscribirse como Android for Work.

Cuando trabaje con la nueva configuración, tenga en cuenta lo siguiente:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Si es la primera vez que incorpora inscripciones de Android for Work
La nueva plataforma Android for Work está bloqueada de manera predeterminada en Restricciones de tipo de dispositivo. Después de incorporar la característica, puede permitir que los dispositivos se inscriban con Android for Work. Para ello, cambie el valor predeterminado o cree una nueva restricción de tipo de dispositivo que sustituya a la predeterminada.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Si ya ha incorporado inscripciones de Android for Work
Si no es la primera que realiza una incorporación, su situación depende de la configuración elegida:

| Configuración | Estado de Android for Work en el valor predeterminado de Restricción de tipo de dispositivo | Notas |
| --- | --- | --- |
| **Administrar todos los dispositivos como Android** | Bloqueado | Todos los dispositivos Android deben inscribirse sin Android for Work. |
| **Administrar los dispositivos compatibles como Android for Work** | Permitido | Todos los dispositivos que admiten Android for Work deben inscribirse con Android for Work. |
| **Administrar los dispositivos compatibles para usuarios solo en estos grupos como Android for Work** | Bloqueado | Para invalidar el valor predeterminado, se creó una directiva de restricción de tipo de dispositivo independiente. Esta directiva define los grupos que se seleccionaron previamente para permitir la inscripción de Android for Work. Los usuarios de los grupos seleccionados seguirán teniendo permiso para inscribir sus dispositivos Android for Work. Todos los demás usuarios tienen restringida la inscripción con Android for Work. |

En todos los casos, se conserva la normativa que haya previsto. No se requiere ninguna acción por su parte para seguir permitiendo Android for Work en su entorno, tanto de forma global como por grupo.

El lanzamiento de estos cambios se iniciará con la actualización de noviembre, pero pueden tardar un tiempo en ejecutarse en su cuenta. Cuando estos cambios entren en vigor en su cuenta, recibirá una notificación de confirmación en el portal de Office 365.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Compatibilidad con varios conectores de Servicio de inscripción de dispositivos de red (NDES) <!-- 1528104 -->
NDES permite que los dispositivos móviles que se ejecutan sin credenciales de dominio puedan obtener certificados a través del Protocolo de inscripción de certificados simple (SCEP). Con esta actualización, se admitirán varios conectores NDES.

### <a name="new-scep-profile-details-supported----1559808---"></a>Nuevos detalles admitidos del perfil SCEP <!-- 1559808 -->
Los administradores podrán establecer configuraciones adicionales al crear un perfil de SCEP en plataformas Android, iOS, macOS y Windows.  Los administradores pueden establecer el IMEI, el número de serie o el nombre común, incluido el correo electrónico en el formato de nombre de sujeto.

### <a name="configure-an-ios-app-pin----1586774---"></a>Configurar un PIN de aplicación iOS <!-- 1586774 -->
Pronto podrá solicitar un PIN para las aplicaciones iOS de destino. En Azure Portal puede configurar el requisito de PIN y la fecha de expiración en días. Para obtener acceso a una aplicación de iOS, se le pedirá al usuario que establezca y use un nuevo PIN. Solo las aplicaciones iOS que tienen habilitada la protección aplicaciones con Intune App SDK serán compatibles con esta característica.

### <a name="retain-data-during-a-factory-reset-----1588489---"></a>Conservar los datos durante un restablecimiento de fábrica <!-- 1588489 -->
Se agrega una nueva funcionalidad al restablecimiento de fábrica de Windows. Ahora, los administradores pueden especificar si la inscripción de dispositivos y otros datos de aprovisionamiento se conservan en un dispositivo tras un restablecimiento de fábrica. 
 
Los siguientes datos se conservan tras un restablecimiento de fábrica:
- Cuentas de usuario asociadas con el dispositivo
- Estado de la máquina (unión a un dominio, AADJ)
- Inscripción de MDM
- Aplicaciones instaladas por OEM (aplicaciones de Win32 y tienda)
- Perfil de usuario
- Datos de usuario fuera del perfil de usuario
- Inicio de sesión automático del usuario
 
Los siguientes datos no se conservan:
- Archivos de usuario
- Aplicaciones instaladas por el usuario (aplicaciones de Win32 y tienda)
- Configuración del dispositivo no predeterminada 

### <a name="app-install-status-report-now-a-bar-chart----1249446---"></a>El informe Estado de instalación de la aplicación es ahora un gráfico de barras <!-- 1249446 -->  
El informe **Estado de la instalación de la aplicación**, al que se puede tener acceso a través de la lista **Aplicación** de la carga de trabajo **Aplicaciones móviles**, pronto estará disponible como gráfico de barras.

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Agregar "Buscar mi iPhone" para dispositivos personales <!--1427287-->
Podrá ver si los dispositivos iOS tienen activado el bloqueo de activación. Esta característica se encontraba anteriormente en Intune, en el portal clásico.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restricciones de inscripción asignada a grupos <!-- 747598 -->
Como administrador de Intune, podrá crear restricciones de inscripción personalizadas de tipo de dispositivo y de límite de dispositivos para grupos de usuarios.
 
Azure Portal de Intune permite crear un máximo de 25 instancias de cada tipo de restricción que pueden asignarse luego a grupos de usuarios. Las restricciones asignadas por grupo invalidan las restricciones predeterminadas.
 
Todas las instancias de un tipo de restricción se mantienen en una lista ordenada de forma estricta. Este orden define un valor de prioridad para la resolución de conflictos. Un usuario afectado por más de una instancia de la restricción solo está limitado por la instancia con el valor de prioridad más alto. Para cambiar la prioridad de una determinada instancia, arrástrela a una posición diferente en la lista. 
 
Esta funcionalidad se publicará con la migración de la configuración de Android for Work desde el menú de inscripción de Android for Work al menú de restricciones de inscripción. Puesto que esta migración puede tardar varios días, la versión de noviembre puede afectar primero a otras partes de su cuenta antes de habilitar la asignación de grupo para las restricciones de inscripción.

### <a name="windows-10-update-ring-assignments-are-displayed----1621837---"></a>Se muestran las asignaciones del círculo de actualizaciones de Windows 10 <!-- 1621837 -->
Cuando esté **solucionando problemas**, y en relación al usuario que está visualizando, podrá observar las asignaciones de círculos de actualizaciones de Windows 10.  



<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Los sitios web de Azure Active Directory pueden requerir la aplicación Intune Managed Browser y compatibilidad con el inicio de sesión único para Managed Browser (versión preliminar pública) <!-- 710595 -->   
Con Azure Active Directory (Azure AD), podrá restringir el acceso a sitios web en dispositivos móviles a la aplicación Intune Managed Browser. En Managed Browser, los datos del sitio web permanecen seguros y separados de los datos personales del usuario final. Además, Managed Browser admite funciones de inicio de sesión único para sitios protegidos por Azure AD. Al iniciar sesión en Managed Browser, o al usarlo en un dispositivo con otra aplicación administrada por Intune, se permite que Managed Browser tenga acceso a sitios corporativos protegidos por Azure AD sin necesidad de que el usuario escriba sus credenciales. Esta funcionalidad se aplica a sitios como Outlook Web Access (OWA) y SharePoint Online, así como a otros sitios corporativos, como los recursos de intranet a los que se tiene acceso a través de Azure App Proxy.

### <a name="troubleshoot-enrollment-issues------746324----"></a>Solución de problemas de inscripción <!--- 746324 --->  
El área de trabajo de solución de problemas mostrará al usuario los problemas de inscripción. Los detalles del problema y los pasos de corrección sugeridos pueden ayudar a los administradores y a los operadores del departamento de soporte técnico a solucionar los problemas. Ciertos problemas de inscripción no se capturan, y es posible que no se sugieran correcciones para algunos errores.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Los administradores ya pueden configurar las opciones del firewall en un dispositivo mediante un perfil de configuración de dispositivo <!-- 951708 -->   
Los administradores pueden activar el firewall para los dispositivos y, además, configurar varios protocolos para redes públicas, privadas y de dominio.  Esta configuración del firewall se encuentra en el perfil "Endpoint Protection".

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>La Protección de aplicaciones de Windows Defender ayuda a proteger los dispositivos de sitios web que no son de confianza, en función de la definición de la organización <!-- 958257 -->   
Los administradores pueden definir sitios como "de confianza" o "corporativos" mediante un flujo de trabajo de Windows Information Protection o el nuevo perfil de "límite de red" en las configuraciones del dispositivo. Todos los sitios que no aparezcan en un límite de red de confianza de un dispositivo de Windows 10 de 64 bits, si se visualizan con Microsoft Edge, se abrirán en su lugar en un explorador en un equipo virtual de Hyper-V.

La Protección de aplicaciones se encuentra en los perfiles de configuración del dispositivo, en el perfil "Endpoint Protection". Desde allí, los administradores pueden configurar la interacción entre el explorador virtualizado y el equipo host, los sitios que son y que no son de confianza, y el almacenamiento de datos generado en el explorador virtualizado. Para usar la Protección de aplicaciones en un dispositivo, debe configurarse primero un límite de red. Es importante definir un solo límite de red para un dispositivo.  

### <a name="windows-defender-application-guard-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>La Protección de aplicaciones de Windows Defender en Windows 10 Enterprise ofrece el modo de confiar solo en aplicaciones autorizadas <!-- 1031096 -->    
Teniendo en cuenta que cada día se crean miles de archivos malintencionados, el uso de la detección antivirus basada en firma para luchar contra el malware podría ser insuficiente para proporcionar una defensa adecuada contra nuevos ataques. Mediante la Protección de aplicaciones de Windows Defender en Windows 10 Enterprise, puede cambiar la configuración del dispositivo y dejar de usar el modo mediante el que se establece que las aplicaciones son de confianza a menos que las bloquee un antivirus u otra solución de seguridad. Asimismo, esto permite pasar al modo mediante el que se establce que el sistema operativo solo confía en las aplicaciones autorizadas por la empresa. La confianza se asigna a las aplicaciones en la Protección de aplicaciones de Windows Defender.

Mediante Intune, puede configurar las directivas de control de aplicaciones en modo de "solo auditoría" o en el modo de uso forzoso. Las aplicaciones no se bloquearán cuando se ejecuten en modo de "solo auditoría". El modo de "solo auditoría" registra todos los eventos en registros del cliente local. También puede configurar si solo se pueden ejecutar componentes de Windows y aplicaciones de la Tienda Windows, o si también se podrán ejecutar otras aplicaciones con buena reputación de acuerdo con la definición de Intelligent Security Graph.

### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Nueva página de estado de inscripción para las inscripciones de Windows 10 <!--1063201-->    
Ahora puede configurar un saludo que aparecerá cuando los usuarios inscriban dispositivos Windows 10. Use la pantalla **Estado de inscripción** para configurar un mensaje personalizado y un hipervínculo que se mostrarán a los usuarios finales cuando inscriban sus dispositivos Windows 10.  La pantalla **Estado de inscripción** también proporcionará a los usuarios finales una vista del progreso de las opciones de configuración de directivas que se aplican a su dispositivo.  

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>La Protección contra vulnerabilidades de seguridad de Windows Defender es un nuevo conjunto de funciones de prevención de intrusiones para Windows 10 <!-- 1063615 -->   
La Protección contra vulnerabilidades de seguridad de Windows Defender incluye reglas personalizadas para reducir la explotabilidad de las aplicaciones. También impide las amenazas de macros y scripts, bloquea automáticamente las conexiones de red a direcciones IP de mala reputación y puede proteger los datos contra el ransomware y amenazas desconocidas. La Protección contra vulnerabilidades de seguridad de Windows Defender consta de los componentes siguientes:

- La **reducción de la superficie expuesta a ataques (ASR)** proporciona reglas que permiten impedir las amenazas de macros, scripts y correos electrónicos.
- El **acceso controlado a carpetas** bloquea automáticamente el acceso a contenido en las carpetas protegidas.
- El **filtro de red** bloquea las conexiones salientes desde cualquier aplicación a IP o dominios de mala reputación.
- La **protección contra vulnerabilidades** proporciona restricciones de memoria, flujo de control y directivas que pueden usarse para proteger una aplicación contra las vulnerabilidades.

### <a name="app-conditional-launch-support----1193313---"></a>Compatibilidad con inicio condicional de aplicación <!-- 1193313 -->
Los administradores de TI ahora pueden establecer un requisito a través del portal de administración de Azure para exigir un código de acceso en lugar de un PIN numérico mediante la administración de aplicaciones móviles (MAM) cuando se inicia la aplicación. Si se configura, se le pedirá al usuario que establezca y use un código de acceso cuando se le solicite antes de obtener acceso a aplicaciones habilitadas para MAM. Un código de acceso se define como un PIN numérico con al menos un carácter especial o un carácter alfabético en mayúsculas/minúsculas. Esta versión de Intune habilitará esta característica **solo en iOS**. Intune admite un código de acceso de forma similar al PIN numérico. Establece una longitud mínima y permite la repetición de caracteres y secuencias. Esta característica requiere la participación de las aplicaciones (es decir, WXP, Outlook, Managed Browser, Yammer) para integrar el SDK para aplicaciones de Intune con el código de esta característica para que se aplique la configuración del código de acceso en las aplicaciones de destino.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Número de versión de la aplicación para línea de negocio en el informe de estado de instalación del dispositivo <!-- 1233999 -->  
El informe de estado de instalación del dispositivo mostrará el número de versión de la aplicación para las aplicaciones de línea de negocio para iOS y Android. Puede usar esta información para solucionar problemas de las aplicaciones o buscar los dispositivos que ejecuten versiones obsoletas de la aplicación.

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Administración conjunta para dispositivos de Windows 10 <!-- 1243445 -->
La administración conjunta es una solución que sirve para ofrecer un vínculo entre la administración tradicional y la administración moderna. Además, le proporciona una guía para llevar a cabo la transición con un enfoque por fases. Básicamente, la administración conjunta es una solución en la que los dispositivos de Windows 10 se administran de forma simultánea mediante Configuration Manager y Microsoft Intune. También se unen a Active Directory (AD) y a Azure Active Directory (Azure AD).  Esta configuración proporciona un método para poder modernizar la administración con el tiempo, a la velocidad que sea adecuada para su organización si no puede moverlo todo a la vez.  

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Establecimiento del acceso para las aplicaciones mediante una revisión de seguridad mínima de Android en el dispositivo <!-- 1278463 -->   
Un administrador podrá definir la revisión de seguridad mínima de Android que debe estar instalada en el dispositivo para poder obtener acceso a una aplicación administrada en una cuenta administrada.

> [!Note]  
> Esta característica solamente restringe las revisiones de seguridad publicadas por Google en dispositivos Android 6.0 y versiones posteriores.

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Nueva configuración de restricciones de dispositivos para Windows 10 <!-- 1308850 -->
-    Mensajería (solo móvil): deshabilitar pruebas o mensajes MMS
-    Contraseña: configuración para habilitar FIPS y el uso de dispositivos secundarios Windows Hello para la autenticación 
-    Pantalla: configuración para activar o desactivar el ajuste de escala de GDI para las aplicaciones heredadas


### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Restricciones de dispositivos Windows 10 a pantalla completa <!-- 1308872 -->   
Podrá restringir a los usuarios de dispositivos Windows 10 a pantalla completa, lo que limita a los usuarios a un conjunto de aplicaciones predefinidas.  Para ello, cree un perfil de restricción de dispositivo Windows 10 y defina la configuración de pantalla completa.

La pantalla completa admite dos modos: **aplicación única**, que permite que un usuario ejecute una sola aplicación, o **varias aplicaciones**, que permite el acceso a un conjunto de aplicaciones.  Para determinar las aplicaciones compatibles, debe definir la cuenta de usuario y el nombre del dispositivo.  Cuando el usuario ha iniciado sesión, verá únicamente las aplicaciones definidas.  Para obtener más información, vea [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) (CSP AssignedAccess). 

La pantalla completa requiere lo siguiente:

- Intune debe ser la entidad de MDM.
- Las aplicaciones deben estar ya instaladas en el dispositivo de destino.
- El dispositivo debe estar [aprovisionado correctamente](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Nuevo perfil de configuración de dispositivo para crear límites de red <!-- 1311967 -->   
Hemos creado un perfil de configuración de dispositivo denominado **Límite de red** que encontrará junto con los demás perfiles de configuración de dispositivo. Use este perfil para definir los recursos en línea que quiere que se consideren corporativos y de confianza. Debe definir un límite de red para un dispositivo *antes* de que en el dispositivo se puedan usar características como la Protección de aplicaciones de Windows Defender y Windows Information Protection. Es importante definir un solo límite de red para cada dispositivo.

Puede definir los recursos de empresa en la nube, los intervalos de direcciones IP y los servidores proxy internos que quiere que se consideren de confianza. Una vez definidos, pueden usar el límite de red otras características como la Protección de aplicaciones de Windows Defender y Windows Information Protection.

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Dos opciones de configuración adicionales para Antivirus de Windows Defender <!-- 1338409 -->  
**Nivel de bloqueo de archivos**

| | |
|---|---|
| No configurado | **No configurado** usa el nivel de bloqueo predeterminado de Antivirus de Windows Defender y proporciona una detección segura sin aumentar el riesgo de detectar archivos legítimos. |
| Alto | **Alto** se aplica a un alto nivel de detección.
| Alto +  | **Alto +** proporciona el nivel Alto con medidas de protección adicionales que podrían afectar al rendimiento del cliente.
| Tolerancia cero  | **Tolerancia cero** bloquea todos los ejecutables desconocidos. |

Aunque es improbable, si se establece en **Alto** puede hacer que se detecten algunos archivos legítimos.
Se recomienda establecer el nivel de bloqueo de archivos en el valor predeterminado (**No configurado**).

**Ampliación del tiempo de espera para la detección de archivos por la nube**  

| | |
|--|--|
| Número de segundos (0-50) | Especifique el tiempo máximo durante el que Antivirus de Windows Defender debe bloquear un archivo mientras espera un resultado de la nube. El valor predeterminado es de 10 segundos. El tiempo adicional que se especifique aquí (hasta 50 segundos) se agregará a los 10 segundos. En la mayoría de los casos, la detección tarda mucho menos que el tiempo máximo. Si amplía el tiempo, permitirá que la nube investigue a fondo los archivos sospechosos. Se recomienda que habilite esta opción y que especifique al menos 20 segundos adicionales. |


### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Compatibilidad con la entidad de certificación (CA) en la nube de Symantec <!-- 1333638 -->    
Intune ahora admite la entidad de certificación en la nube de Symantec que permite que Intune Certificate Connector emita certificados PKCS desde la entidad de certificación en la nube de Symantec para dispositivos administrados por Intune. Si ya usa Intune Certificate Connector con la entidad de certificación de Microsoft, puede aprovechar la configuración existente de Intune Certificate Connector para agregar compatibilidad con la entidad de certificación de Symantec.



### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Adición de la VPN de Citrix a dispositivos Windows 10 <!-- 1512457 -->  
El cliente podrá configurar la VPN de Citrix para sus dispositivos Windows 10. Puede elegir la VPN de Citrix en la lista *Seleccione un tipo de conexión* en la hoja **VPN base** al configurar una VPN para Windows 10 y versiones posteriores.

> [!Note]
> La configuración de Citrix ya existía para iOS y Android.



<!-- the following are present prior to 1710 -->

### <a name="google-play-protect-support-on-android----908720----"></a>Compatibilidad con Google Play Protect en Android <!-- 908720  -->  
Con el lanzamiento de Android Oreo, Google presenta un conjunto de características de seguridad denominado Google Play Protect que permite a los usuarios y las organizaciones ejecutar aplicaciones e imágenes de Android seguras. Intune admite las características de Google Play Protect, incluida la atestación remota de SafetyNet.  Los administradores pueden establecer requisitos para directivas de cumplimiento que exijan que Google Play Protect esté configurado y en buen estado. La opción **SafetyNet device attestation** (Atestación de dispositivo SafetyNet)* requiere que el dispositivo se conecte con un servicio de Google para comprobar que se encuentra en buen estado y no está en riesgo. Los administradores también pueden establecer una opción en el perfil de configuración de Android for Work para requerir que se comprueben las aplicaciones instaladas por los servicios de Google Play.  El acceso condicional puede impedir que los usuarios tengan acceso a los recursos corporativos si un dispositivo no es compatible con los requisitos de Google Play Protect. 


### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Compatibilidad con una directiva de actualización de la edición de Windows 10   <!-- 903672(archived), 1119689 -->  
Podrá crear una directiva de actualización de la edición de Windows 10 que actualice los dispositivos con Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education y Windows 10 Professional Education N. Para obtener más información sobre las actualizaciones de la edición de Windows 10, vea [Configuración de actualizaciones de la edición de Windows 10](edition-upgrade-configure-windows-10.md).




<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--846515---"></a>Acciones en caso de incumplimiento <!--730266  846515 -->     
*Acciones en caso de incumplimiento* es una nueva característica de las directivas de cumplimiento que permite realizar acciones en dispositivos no compatibles. Puede especificar una o varias acciones y especificar el período de tiempo en el que se deben producir esas acciones. Por ejemplo, puede notificar a los usuarios de dispositivos no compatibles inmediatamente después de que el dispositivo se convierta en no compatible mediante el correo electrónico, o puede impedir que los dispositivos no compatibles tengan acceso a los recursos corporativos después de un período de gracia de 3 días mediante el acceso condicional.

### <a name="android-for-work-support-for-lookout----1087312---"></a>Compatibilidad de Android for Work con Lookout <!-- 1087312 -->   
El conector de Intune con Lookout admitirá dispositivos de Android for Work cuando se use la aplicación Lookout for Work. Puede implementar la aplicación Lookout dentro o fuera del contenedor.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune App Protection y Herramientas de desarrollo de Citrix MDX <!-- 709185 -->
Puede administrar dispositivos y aplicaciones con una combinación de Citrix XenMobile MDX y Microsoft Intune. Esto le permite administrar aplicaciones con la directiva de protección de aplicaciones de Intune mientras usa tecnología mVPN de Citrix.

Puede buscar un repositorio de código que contiene la herramienta de ajuste de aplicaciones de Intune e Intune App SDK para iOS y Android, que se integra con la tecnología mVPN de Citrix MDX.


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Compatibilidad de alta disponibilidad de On-premises Exchange Connector <!-- 676614 -->   
Puede tener varios roles de servidor de acceso de cliente (CAS) para el conector de Exchange local. Por ejemplo, si se produce un error en el CAS principal, Exchange Connector recibe una consulta para recurrir a otros CAS. Esta característica garantiza que no se interrumpa el servicio.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Módulo de administración de System Center Operations Manager para Exchange Connector <!-- 885457 -->   
El módulo de administración de System Center Operations Manager para Exchange Connector está disponible para ayudarle a analizar los registros de Exchange Connector. Este módulo de administración le proporciona distintas maneras de supervisar Intune cuando tenga que resolver problemas.





## <a name="intune-apps"></a>Aplicaciones de Intune

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Ayudar a los usuarios con la aplicación Portal de empresa para Android <!---1573324, 1573150, 1558616, 1564878--->
La aplicación de Portal de empresa para Android incorpora instrucciones dirigidas a los usuarios finales con la finalidad de ayudarles a comprender y, siempre que sea posible, resolver por ellos mismos los nuevos casos de uso. 

- Se mostrará un nuevo mensaje de error que explica que se ha implementado una directiva de cumplimiento para el cifrado, pero que el [fabricante no cifra el dispositivo](/intune-user-help/your-device-appears-encrypted-but-cp-says-otherwise-android) de acuerdo con las [recomendaciones de Google](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setStorageEncryption(android.content.ComponentName, boolean).
- Los usuarios finales serán guiados al (portal de Azure Active Directory)[https://account.activedirectory.windowsazure.com/r/#/profile] para quitar un dispositivo en caso de que hayan alcanzado el número máximo de dispositivos que se permite agregar. 
- Los usuarios finales tienen a su disposición una serie de instrucciones que pueden seguir para [corregir errores de activación en dispositivos Samsung KNOX](https://go.microsoft.com/fwlink/?linkid=859718) o [desactivar el modo de ahorro de energía](/intune-user-help/power-saving-mode-android). Si ninguna de esas soluciones resuelve su problema, se les proporcionará una explicación de cómo [enviar registros a Microsoft](/intune-user-help/send-logs-to-microsoft-ios). 


### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nueva acción “Resolver” disponible para dispositivos Android <!---1583480--->
La aplicación Portal de empresa para Android presenta la acción “Resolve” en la página _Actualizar configuración del dispositivo_. Si selecciona esta opción, el usuario final irá directamente a la configuración que causa la no conformidad de su dispositivo. La aplicación Portal de empresa para Android admite actualmente esta acción para las opciones de configuración [código de acceso de dispositivo](/intune-user-help/set-your-pin-or-password-android), [cifrado de dispositivo](/intune-user-help/encrypt-your-device-android), [depuración USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) y [orígenes desconocidos](/intune-user-help/you-need-to-turn-off-unknown-sources-android). 




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Redireccionamiento a los usuarios de macOS a nuestra nueva aplicación Portal de empresa <!--1380728-->   
Cuando un usuario final inicia sesión en el sitio web del Portal de empresa para inscribir su dispositivo macOS, se le dirigirá a la descarga de la nueva aplicación Portal de empresa para macOS a fin de que complete el proceso. Esto ocurre con los dispositivos macOS que usan OS X El Capitan 10.11 o una versión posterior. 


<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Las aplicaciones que están disponibles con o sin inscripción ahora se pueden instalar sin que se les solicite la inscripción. <!-- 1334712 -->
Las aplicaciones de empresa que se han puesto a disposición de los usuarios con o sin inscripción en la aplicación de Portal de empresa de Android pueden instalarse sin necesidad de una solicitud de inscripción.


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Compatibilidad de Intune Managed Browser con iOS y Android <!-- 1374196 -->
A partir de octubre de 2017, la aplicación Intune Managed Browser en dispositivos Android admitirá solo los dispositivos con Android 4.4 y versiones posteriores. La aplicación Intune Managed Browser en iOS solo admitirá dispositivos con iOS 9.0 y versiones posteriores. Las versiones anteriores de iOS y Android podrán seguir usando Intune Managed Browser, pero no podrán instalar nuevas versiones de la aplicación y es posible que no puedan tener acceso a todas las funcionalidades de la aplicación. Le recomendamos que actualice la versión del sistema operativo de estos dispositivos a una que sea compatible.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensaje de error mejorado cuando un usuario alcanza el número máximo de dispositivos permitidos para la inscripción <!-- 1270370 -->
En lugar de un mensaje de error genérico, los usuarios finales ven un mensaje de error descriptivo que requiere acción: "Ya ha inscrito el máximo número de dispositivos permitidos por su administrador de TI. Quite un dispositivo inscrito o reciba ayuda de su administrador de TI".




## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.




### <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.
