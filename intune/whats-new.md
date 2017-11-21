---
title: Novedades de Microsoft Intune
titlesuffix: Azure portal
description: Descubra las novedades del portal de Intune Azure
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 11/8/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f42410c0df0492f57c7c1f33beed1d2f082ff285
ms.sourcegitcommit: 5b5744aed73384e1df864f8d3f9f739e17607c2c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/14/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Novedades de Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Conozca las novedades semanales de Microsoft Intune. También podrá obtener información sobre los [próximos cambios](#whats-coming), [notificaciones importantes](#notices) sobre el servicio e información sobre las [versiones anteriores](whats-new-archive.md).

> [!Note]
> Muchas de estas características finalmente serán compatibles con las implementaciones híbridas con Configuration Manager. Para más información sobre las nuevas características híbridas, vea nuestra [página sobre novedades de las implementaciones híbridas](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   
## <a name="week-of-november-6-2017"></a>Semana del 6 de noviembre de 2017


### <a name="device-enrollment"></a>Inscripción de dispositivos
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Administración conjunta para dispositivos de Windows 10 <!-- 1243445 -->
La administración conjunta es una solución que sirve para ofrecer un vínculo entre la administración tradicional y la administración moderna. Además, le proporciona una guía para llevar a cabo la transición con un enfoque por fases. Básicamente, la administración conjunta es una solución en la que los dispositivos de Windows 10 se administran de forma simultánea mediante Configuration Manager y Microsoft Intune. También se unen a Active Directory (AD) y a Azure Active Directory (Azure AD).  Esta configuración proporciona un método para poder modernizar la administración con el tiempo, a la velocidad que sea adecuada para su organización si no puede moverlo todo a la vez.  


#### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Nueva página de estado de inscripción para las inscripciones de Windows 10 <!--1063201-->    
Ahora puede configurar un saludo que aparecerá cuando los usuarios inscriban dispositivos Windows 10. Use la pantalla **Estado de inscripción** para configurar un mensaje personalizado y un hipervínculo que se mostrarán a los usuarios finales cuando inscriban sus dispositivos Windows 10.  La pantalla **Estado de inscripción** también proporcionará a los usuarios finales una vista del progreso de las opciones de configuración de directivas que se aplican a su dispositivo.  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Restricción de la inscripción de Windows según la versión del sistema operativo <!-- 245498 -->
Como administrador de Intune, ahora puede especificar una versión mínima y máxima de Windows 10 para poder inscribir dispositivos. Estas restricciones se pueden establecer en la hoja **Configuraciones de plataforma**.

Intune seguirá permitiendo la inscripción de teléfonos y equipos con Windows 8.1, pero solo se pueden establecer los límites mínimo y máximo de las versiones de Windows 10. Para permitir la inscripción de dispositivos 8.1, deje vacío el límite mínimo.

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Alertas de dispositivos sin asignar de Windows AutoPilot <!-- 1631236 -->
Hay una nueva alerta disponible relativa a los dispositivos sin asignar de Windows AutoPilot en la página **Microsoft Intune** > **Inscripción de dispositivos** > **Información general**. Esta alerta indica cuántos dispositivos del programa AutoPilot no tienen asignados perfiles de implementación de AutoPilot. Use la información provista en la alerta para crear perfiles y asignarlos a los dispositivos sin asignar. Al hacer clic en la alerta, verá una lista completa de dispositivos de Windows AutoPilot e información detallada sobre ellos. Para obtener más información, vea [Inscribir dispositivos mediante el programa Windows AutoPilot Deployment](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="device-management"></a>Administración de dispositivos
#### <a name="refresh-button-for-devices-list-------1333581---"></a>Botón Actualizar de la lista de dispositivos    <!-- 1333581 -->
La lista de dispositivos no se actualiza automáticamente, de modo que puede usar el nuevo botón Actualizar para actualizar los dispositivos que figuran en esa lista.

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Compatibilidad con la entidad de certificación (CA) en la nube de Symantec <!-- 1333638 -->    
Intune ahora admite la entidad de certificación en la nube de Symantec que permite que Intune Certificate Connector emita certificados PKCS desde la entidad de certificación en la nube de Symantec para dispositivos administrados por Intune. Si ya usa Intune Certificate Connector con la entidad de certificación de Microsoft, puede aprovechar la configuración existente de Intune Certificate Connector para agregar compatibilidad con la entidad de certificación de Symantec.

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>Nuevos elementos agregados al inventario de dispositivos   <!--1404455 -->
En esta versión, hemos agregado los siguientes elementos nuevos al [inventario de los dispositivos inscritos](device-inventory.md):

- Dirección MAC de Wi-Fi
- Espacio de almacenamiento total
- Espacio disponible total
- MEID
- Operador del suscriptor


### <a name="app-management"></a>Administración de aplicaciones
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Establecimiento del acceso para las aplicaciones mediante una revisión de seguridad mínima de Android en el dispositivo <!-- 1278463 -->   
Un administrador podrá definir la revisión de seguridad mínima de Android que debe estar instalada en el dispositivo para poder obtener acceso a una aplicación administrada en una cuenta administrada.

> [!Note]  
> Esta característica solamente restringe las revisiones de seguridad publicadas por Google en dispositivos Android 6.0 y versiones posteriores.

#### <a name="app-conditional-launch-support----1193313---"></a>Compatibilidad con inicio condicional de aplicación <!-- 1193313 -->
Los administradores de TI ahora pueden establecer un requisito a través del portal de administración de Azure para exigir un código de acceso en lugar de un PIN numérico mediante la administración de aplicaciones móviles (MAM) cuando se inicia la aplicación. Si se configura, se le pedirá al usuario que establezca y use un código de acceso cuando se le solicite antes de obtener acceso a aplicaciones habilitadas para MAM. Un código de acceso se define como un PIN numérico con al menos un carácter especial o un carácter alfabético en mayúsculas/minúsculas. Esta versión de Intune habilitará esta característica **solo en iOS**. Intune admite un código de acceso de forma similar al PIN numérico. Establece una longitud mínima y permite la repetición de caracteres y secuencias. Esta característica requiere la participación de las aplicaciones (es decir, WXP, Outlook, Managed Browser, Yammer) para integrar el SDK para aplicaciones de Intune con el código de esta característica para que se aplique la configuración del código de acceso en las aplicaciones de destino.

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Número de versión de la aplicación para línea de negocio en el informe de estado de instalación del dispositivo <!-- 1233999 -->
Con esta versión, el informe de estado de instalación del dispositivo mostrará el número de versión de aplicación de las aplicaciones de línea de negocio para iOS y Android. Puede usar esta información para solucionar problemas de las aplicaciones o buscar los dispositivos que ejecuten versiones obsoletas de la aplicación.


### <a name="device-configuration"></a>Configuración de los dispositivos
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Los administradores ya pueden configurar las opciones del firewall en un dispositivo mediante un perfil de configuración de dispositivo <!-- 951708 -->   
Los administradores pueden activar el firewall para los dispositivos y, además, configurar varios protocolos para redes públicas, privadas y de dominio.  Esta configuración del firewall se encuentra en el perfil "Endpoint Protection".

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>La Protección de aplicaciones de Windows Defender ayuda a proteger los dispositivos de sitios web que no son de confianza, en función de la definición de la organización <!-- 958257 -->   
Los administradores pueden definir sitios como "de confianza" o "corporativos" mediante un flujo de trabajo de Windows Information Protection o el nuevo perfil de "límite de red" en las configuraciones del dispositivo. Todos los sitios que no aparezcan en un límite de red de confianza de un dispositivo de Windows 10 de 64 bits, si se visualizan con Microsoft Edge, se abrirán en su lugar en un explorador en un equipo virtual de Hyper-V.

La Protección de aplicaciones se encuentra en los perfiles de configuración del dispositivo, en el perfil "Endpoint Protection". Desde allí, los administradores pueden configurar la interacción entre el explorador virtualizado y el equipo host, los sitios que son y que no son de confianza, y el almacenamiento de datos generado en el explorador virtualizado. Para usar la Protección de aplicaciones en un dispositivo, debe configurarse primero un límite de red. Es importante definir un solo límite de red para un dispositivo.  

#### <a name="windows-defender-application-guard-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>La Protección de aplicaciones de Windows Defender en Windows 10 Enterprise ofrece el modo de confiar solo en aplicaciones autorizadas <!-- 1031096 -->    
Teniendo en cuenta que cada día se crean miles de archivos malintencionados, el uso de la detección antivirus basada en firma para luchar contra el malware podría ser insuficiente para proporcionar una defensa adecuada contra nuevos ataques. Mediante la Protección de aplicaciones de Windows Defender en Windows 10 Enterprise, puede cambiar la configuración del dispositivo y dejar de usar el modo mediante el que se establece que las aplicaciones son de confianza a menos que las bloquee un antivirus u otra solución de seguridad. Asimismo, esto permite pasar al modo mediante el que se establce que el sistema operativo solo confía en las aplicaciones autorizadas por la empresa. La confianza se asigna a las aplicaciones en la Protección de aplicaciones de Windows Defender.

Mediante Intune, puede configurar las directivas de control de aplicaciones en modo de "solo auditoría" o en el modo de uso forzoso. Las aplicaciones no se bloquearán cuando se ejecuten en modo de "solo auditoría". El modo de "solo auditoría" registra todos los eventos en registros del cliente local. También puede configurar si solo se pueden ejecutar componentes de Windows y aplicaciones de la Tienda Windows, o si también se podrán ejecutar otras aplicaciones con buena reputación de acuerdo con la definición de Intelligent Security Graph.

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>La Protección contra vulnerabilidades de seguridad de Windows Defender es un nuevo conjunto de funciones de prevención de intrusiones para Windows 10 <!-- 1063615 -->   
La Protección contra vulnerabilidades de seguridad de Windows Defender incluye reglas personalizadas para reducir la explotabilidad de las aplicaciones. También impide las amenazas de macros y scripts, bloquea automáticamente las conexiones de red a direcciones IP de mala reputación y puede proteger los datos contra el ransomware y amenazas desconocidas. La Protección contra vulnerabilidades de seguridad de Windows Defender consta de los componentes siguientes:

- La **reducción de la superficie expuesta a ataques (ASR)** proporciona reglas que permiten impedir las amenazas de macros, scripts y correos electrónicos.
- El **acceso controlado a carpetas** bloquea automáticamente el acceso a contenido en las carpetas protegidas.
- El **filtro de red** bloquea las conexiones salientes desde cualquier aplicación a IP o dominios de mala reputación.
- La **protección contra vulnerabilidades** proporciona restricciones de memoria, flujo de control y directivas que pueden usarse para proteger una aplicación contra las vulnerabilidades.


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Administrar scripts de PowerShell en Intune para dispositivos Windows 10 <!-- 790537 -->
La extensión de administración de Intune permite cargar los scripts de PowerShell en Intune para ejecutarse en dispositivos Windows 10. Esta extensión complementa las capacidades de administración de dispositivos móviles (MDM) de Windows 10 y facilita la transición a una administración moderna. Para conocer más detalles, vea [Administrar scripts de PowerShell en Intune para dispositivos Windows 10](intune-management-extension.md).

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Nueva configuración de restricciones de dispositivos para Windows 10 <!-- 1308850 -->
-    Mensajería (solo móvil): deshabilitar pruebas o mensajes MMS
-    Contraseña: configuración para habilitar FIPS y el uso de dispositivos secundarios Windows Hello para la autenticación 
-    Pantalla: configuración para activar o desactivar el ajuste de escala de GDI para las aplicaciones heredadas

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Restricciones de dispositivos Windows 10 a pantalla completa <!-- 1308872 -->   
Puede restringir usuarios de dispositivos Windows 10 a pantalla completa, lo que les limita a un conjunto de aplicaciones predefinidas.  Para ello, cree un perfil de restricción de dispositivo Windows 10 y defina la configuración de pantalla completa.

La pantalla completa admite dos modos: **aplicación única**, que permite que un usuario ejecute una sola aplicación, o **varias aplicaciones**, que permite el acceso a un conjunto de aplicaciones.  Para determinar las aplicaciones compatibles, debe definir la cuenta de usuario y el nombre del dispositivo.  Cuando el usuario ha iniciado sesión, verá únicamente las aplicaciones definidas.  Para obtener más información, vea [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) (CSP AssignedAccess). 

La pantalla completa requiere lo siguiente:

- Intune debe ser la entidad de MDM.
- Las aplicaciones deben estar ya instaladas en el dispositivo de destino.
- El dispositivo debe estar [aprovisionado correctamente](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Nuevo perfil de configuración de dispositivo para crear límites de red <!-- 1311967 -->   
Hemos creado un perfil de configuración de dispositivo denominado **Límite de red** que encontrará junto con los demás perfiles de configuración de dispositivo. Use este perfil para definir los recursos en línea que quiere que se consideren corporativos y de confianza. Debe definir un límite de red para un dispositivo *antes* de que en el dispositivo se puedan usar características como la Protección de aplicaciones de Windows Defender y Windows Information Protection. Es importante definir un solo límite de red para cada dispositivo.

Puede definir los recursos de empresa en la nube, los intervalos de direcciones IP y los servidores proxy internos que quiere que se consideren de confianza. Una vez definidos, pueden usar el límite de red otras características como la Protección de aplicaciones de Windows Defender y Windows Information Protection.

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Dos opciones de configuración adicionales para Antivirus de Windows Defender <!-- 1338409 -->  
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

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Adición de la VPN de Citrix a dispositivos Windows 10 <!-- 1512457 -->  
Puede configurar la VPN de Citrix para sus dispositivos Windows 10. Puede elegir la VPN de Citrix en la lista *Seleccione un tipo de conexión* en la hoja **VPN base** al configurar una VPN para Windows 10 y versiones posteriores.

> [!Note]
> La configuración de Citrix ya existía para iOS y Android.

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Las conexiones Wi-Fi admiten claves precompartidas en iOS <!-- 1550823 -->
Los clientes pueden configurar perfiles de Wi-Fi para usar claves precompartidas (PSK) en las conexiones WPA o WPA2 Personal en dispositivos iOS. Estos perfiles se insertan en el dispositivo del usuario al inscribirlo en Intune.

Cuando el perfil se haya insertado en el dispositivo, el siguiente paso dependerá de la configuración del perfil.  Si está establecido para conectarse automáticamente, lo hace cuando la red se necesite.  Cuando el perfil se conecta de forma manual, el usuario deberá activar manualmente la conexión.  

### <a name="intune-apps"></a>Aplicaciones de Intune
#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Acceso a los registros de aplicación administrada de iOS <!-- 1469920 -->
Ahora, los usuarios finales que tengan Managed Browser instalado pueden ver el estado de administración de todas las aplicaciones publicadas de Microsoft, así como enviar registros para solucionar problemas con sus aplicaciones iOS administradas.

Para más información sobre cómo habilitar el modo de solución de problemas en Managed Browser en un dispositivo iOS, vea [Cómo tener acceso a los registros de aplicación administrada con Managed Browser en iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).


### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas
#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>La entidad de usuario contiene los datos de usuario más recientes en el modelo de datos de Almacenamiento de datos <!-- 1544273 -->
La primera versión del modelo de datos del Almacenamiento de datos de Intune solo contenía datos de Intune recientes e históricos. Los creadores de informes no podían capturar el estado actual de un usuario. En esta actualización, la **entidad de usuario** se rellenará con los datos más recientes del usuario.






## <a name="week-of-october-30-2017"></a>Semana del 30 de octubre de 2017
### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>El número de versión de la aplicación de línea de negocio de Android y iOS es visible <!-- 1380712 -->

Las aplicaciones de Intune ahora muestran el número de versión para las aplicaciones de línea de negocio de iOS y Android. El número se muestra en la lista de aplicaciones de Azure Portal y en la hoja de información general de la aplicación. Los usuarios finales pueden ver este número en la aplicación Portal de empresa y en el portal web.

#### <a name="full-version-number"></a>Número de versión completo
El número de versión completo identifica una versión específica de la aplicación. El número aparece como _versión_(_compilación_). Por ejemplo, 2.2(2.2.17560800).

El número de versión completo consta de dos componentes:

 - **Versión**  
   El número de versión es el número que pueden ver los usuarios. Sirve para que los usuarios finales distingan las diferentes versiones de la aplicación.

 - **Número de compilación**  
    El número de compilación es un número interno que puede usarse para la detección de la aplicación y para administrar la aplicación mediante programación. El número de compilación alude a una iteración de la aplicación que hace referencia a los cambios en el código.

Obtenga más información sobre los números de versión y el desarrollo de aplicaciones de línea de negocio en [Introducción al SDK para aplicaciones de Microsoft Intune](app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration----677972---"></a>Integración de la administración de dispositivos y aplicaciones <!-- 677972 -->   
Ahora que se puede tener acceso a la administración de dispositivos móviles (MDM) y a la administración de aplicaciones móviles (MAM) de Intune desde Azure Portal, Intune ha empezado a integrar la experiencia de administración de TI en torno a la administración de aplicaciones y dispositivos. Estos cambios están pensados para simplificar la experiencia de administración de dispositivos y aplicaciones.

Obtenga más información sobre los cambios anunciados en MDM y MAM en el [blog del equipo de soporte técnico de Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Nuevas alertas de inscripción de dispositivos de Apple <!-- 1471790 -->
En la página de información general de la inscripción se mostrarán alertas relacionadas con la administración de dispositivos de Apple que resultarán útiles para los administradores de TI. Las alertas se mostrarán en la página de información general cuando el certificado de inserción MDM de Apple esté a punto de expirar o ya lo haya hecho; cuando el token del Programa de inscripción de dispositivos vaya a expirar o ya lo haya hecho; y cuando haya dispositivos sin asignar en el Programa de inscripción de dispositivos.


### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Reemplazo de tokens en la configuración de aplicaciones sin inscripción de dispositivos <!-- 1080364 -->

Puede usar tokens para valores dinámicos de la configuración de las aplicaciones en dispositivos que no están inscritos. Para obtener más información, consulte [Agregar directivas de configuración para aplicaciones administradas sin inscripción de dispositivos](app-configuration-policies-managed-app.md).

## <a name="week-of-october-23-2017"></a>Semana del 23 de octubre de 2017
### <a name="intune-apps"></a>Aplicaciones de Intune
#### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Compatibilidad con la autenticación basada en certificados en el Portal de empresa para iOS <!--1029830-->
Hemos agregado compatibilidad con la autenticación basada en certificados (CBA) en la aplicación Portal de empresa para iOS. Los usuarios con CBA deben escribir su nombre de usuario y, después, pulsar el vínculo para iniciar sesión con un certificado. CBA ya se admite en las aplicaciones Portal de empresa para Android y Windows. Puede obtener más información en la página [Sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) (Iniciar sesión en la aplicación Portal de empresa).

#### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Las aplicaciones que están disponibles con o sin inscripción ahora se pueden instalar sin que se les solicite la inscripción. <!-- 1334712 -->

Ahora, las aplicaciones de empresa que se han puesto a disposición de los usuarios con o sin inscripción en la aplicación de Portal de empresa de Android pueden instalarse sin necesidad de una solicitud de inscripción.

## <a name="week-of-october-16-2017"></a>Semana del 16 de octubre de 2017
### <a name="device-enrollment"></a>Inscripción de dispositivos
#### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Compatibilidad del programa Windows AutoPilot Deployment en Microsoft Intune<!-- 747617  -->
Ahora puede usar Microsoft Intune con el programa Windows AutoPilot Deployment para que los usuarios puedan aprovisionar sus dispositivos de empresa sin necesidad de recurrir al departamento de TI. Puede personalizar la experiencia de configuración rápida y guiar a los usuarios durante la combinación de sus dispositivos con Azure AD y la inscripción en Intune. Al usar conjuntamente Microsoft Intune y Windows AutoPilot, se acaba con la necesidad de implementar, mantener y administrar imágenes del sistema operativo. Para obtener información, consulte [Inscribir dispositivos mediante el programa Windows AutoPilot Deployment](https://docs.microsoft.com/intune/enrollment-autopilot).

#### <a name="quick-start-for-device-enrollment-----1425655---"></a>Inicio rápido para la inscripción de dispositivos <!-- 1425655 --> 
Ahora el inicio rápido está disponible en **Inscripción de dispositivos** y proporciona una tabla de referencias para administrar plataformas y configurar el proceso de inscripción. Para simplificar la iniciación, se ofrece documentación útil en forma de una breve descripción de cada elemento y enlaces a documentación con instrucciones paso a paso.

#### <a name="device-categorization----1427491---"></a>Categorización de dispositivos <!-- 1427491 -->
En el gráfico de la plataforma de dispositivos inscritos de la hoja **Dispositivos > Información general** se organizan los dispositivos por plataforma, incluidos Android, iOS, macOS, Windows y Windows Mobile.  Los dispositivos que ejecutan otros sistemas operativos se agrupan en "Otros",  por ejemplo, dispositivos fabricados por Blackberry, NOKIA u otros fabricantes.  

Para obtener información sobre los dispositivos que se ven afectados en el inquilino, elija **Administrar > Todos los dispositivos** y después use **Filtrar** para limitar el campo **Sistema operativo**.

### <a name="device-management"></a>Administración de dispositivos
#### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium: nuevo socio de defensa contra amenazas móviles <!-- 954681 -->  
Puede controlar el acceso desde dispositivos móviles a recursos corporativos mediante el acceso condicional basado en la evaluación de riesgos efectuada por Zimperium, una solución de defensa contra amenazas móviles integrada en Microsoft Intune.

##### <a name="how-integration-with-intune-works"></a>Funcionamiento de la integración con Intune
El riesgo se evalúa según la telemetría recopilada de dispositivos con Zimperium. Se pueden configurar directivas de acceso condicional de EMS según la evaluación de riesgos de Zimperium habilitada mediante las directivas de cumplimiento de los dispositivos de Intune, que puede usar para permitir o bloquear el acceso de los dispositivos no compatibles a los recursos corporativos en función de las amenazas detectadas.

#### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Nueva configuración del perfil de restricción de dispositivo Windows 10 <!--- 978575, 1308849, -->  
Estamos agregando nuevas configuraciones al perfil de restricción de dispositivos Windows 10 en la categoría de SmartScreen de Windows Defender.

Para obtener información sobre el perfil de restricción de dispositivos Windows 10, vea [Configuración de restricciones de dispositivos Windows 10 y versiones posteriores]( device-restrictions-windows-10.md).

#### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Soporte remoto para Windows y dispositivos Windows Mobile  <!-- 1070473 -->  
Ahora Intune puede usar el software [TeamViewer](https://www.teamviewer.com), que se compra por separado, para que pueda ofrecer asistencia remota a los usuarios que estén ejecutando Windows y dispositivos Windows Mobile.

#### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Examen de dispositivos con Windows Defender <!-- 1280988  1280990   -->
Ahora puede ejecutar un **Examen rápido** y un **Examen completo**, además de **Actualizar firmas**, con el antivirus Windows Defender en los dispositivos Windows 10 administrados. En la hoja de información general del dispositivo, elija la acción que desea ejecutar en el dispositivo. Se le pide que confirme la acción antes de que el comando se envíe al dispositivo. 

**Examen rápido**: un examen rápido examina ubicaciones donde el malware se registra para iniciarse, como las claves del registro y las carpetas de inicio de Windows conocidas. Un examen rápido tarda de media cinco minutos. Al combinarlo con la opción **Always-on real-time protection** (Protección en tiempo real siempre activa), que examina los archivos cuando están abiertos o cerrados y siempre que un usuario navega a una carpeta, el examen rápido ayuda a proporcionar protección frente a malware que podría estar en el sistema o el kernel. Los usuarios ven los resultados del examen en sus dispositivos cuando termina. 

**Examen completo**: un examen completo puede resultar útil en los dispositivos que han encontrado una amenaza de malware para identificar si existe algún componente inactivo que requiera una limpieza más exhaustiva, además de para ejecutar exámenes a petición. El examen completo puede tardar una hora en ejecutarse. Los usuarios ven los resultados del examen en sus dispositivos cuando termina. 

**Actualizar firmas**: el comando de actualización de firmas actualiza las definiciones y las firmas de malware del antivirus de Windows Defender. Esto le ayuda a asegurarse de que el antivirus de Windows Defender es eficaz en la detección de malware. Esta característica es para dispositivos Windows 10 únicamente, está pendiente la conectividad a Internet de los dispositivos. 

#### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Se ha quitado el botón Habilitar/Deshabilitar de la página de la entidad emisora de certificados de Azure Portal de Intune <!-- 1400455 -->
 Se está eliminando un paso adicional para configurar el conector de certificados en Intune. Actualmente, descarga el conector del certificado y después lo habilita en la consola de Intune. En cambio, si deshabilita el conector en la consola de Intune, el conector sigue emitiendo certificados.

##### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
A partir de octubre, el botón Habilitar/Deshabilitar ya no aparecerá en la página de la entidad emisora de certificados en Azure Portal. La funcionalidad del conector sigue siendo la misma. Los certificados todavía se implementan en dispositivos inscritos en Intune. Puede continuar descargando e instalando el conector del certificado. Para detener la emisión de certificados, ahora deberá desinstalar el conector del certificado en vez de deshabilitarlo.

##### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Si actualmente tiene el conector del certificado deshabilitado, primero debe desinstalarlo.

### <a name="device-configuration"></a>Configuración de los dispositivos
#### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Nueva configuración del perfil de restricción de dispositivo Windows 10 Team  <!--- 1308838 -->
En esta versión, hemos agregado muchas configuraciones nuevas al perfil de restricción de dispositivo de Windows 10 Team para ayudarle a controlar los dispositivos de Surface Hub.

Para obtener más información sobre este perfil, vea [Configuración de restricciones de dispositivos Windows 10 Team en Microsoft Intune](device-restrictions-windows-10-teams.md).

#### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Restricción para impedir que los usuarios de dispositivos Android puedan cambiar la fecha y la hora de sus dispositivos <!-- 1333292 -->
Puede usar una [directiva de dispositivo personalizada de Android](custom-settings-android.md) para impedir que los usuarios de dispositivos Android cambien la fecha y la hora del dispositivo.

Para ello, configure una directiva personalizada de Android con el URI de configuración ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange. Establezca este parámetro en **TRUE** y luego asígnelo a los grupos requeridos.

#### <a name="bitlocker-device-configuration----1397398---"></a>Configuración del dispositivo de BitLocker <!-- 1397398 -->
La opción **Cifrado de Windows > Configuración base**  incluye el nuevo ajuste **Advertencia para otro cifrado de disco** que le permite deshabilitar el [mensaje de advertencia](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) para otro cifrado de disco que podría estar en uso en el dispositivo del usuario.  El mensaje de advertencia requiere el consentimiento del usuario final antes de configurar BitLocker en el dispositivo y bloquea la instalación de BitLocker hasta que este la confirme.  La nueva configuración deshabilita la advertencia del usuario final.


### <a name="app-management"></a>Administración de aplicaciones
#### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Ahora el programa de compras por volumen para las aplicaciones de empresa se sincronizará con su inquilino de Intune <!-- 800882 -->  
Los desarrolladores de terceros también pueden distribuir aplicaciones de forma privada a miembros autorizados del Programa de compras por volumen (VPP) para Empresas, especificados en iTunes Connect. Estos miembros pueden iniciar sesión en la tienda de aplicaciones del Programa de Compras por Volumen y comprar aplicaciones.

Con esta versión, el VPP para aplicaciones de empresa que haya comprado el usuario final se sincronizarán con sus inquilinos de Intune.

#### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selección de la instancia de App Store de Apple del país para la sincronización de aplicaciones de VPP  <!-- 1332311 -->  
Puede configurar la instancia de App Store del país para el Programa de Compras por Volumen de Apple (VPP) al cargar el token de VPP. Intune sincroniza las aplicaciones de VPP para todas las configuraciones regionales desde la instancia de App Store del país de VPP especificada.

> [!NOTE]  
> En la actualidad, Intune solo sincroniza las aplicaciones de VPP de la instancia de App Store del país de VPP que coinciden con la configuración regional de Intune en la que se creó el inquilino de Intune.


### <a name="intune-apps"></a>Aplicaciones de Intune
#### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloqueo de las acciones de copiar y pegar entre perfiles profesionales y personales en Android for Work <!-- 1098994 -->
Con esta versión, es posible configurar el perfil del trabajo para Android for Work a fin de bloquear las acciones de copiar y pegar entre aplicaciones profesionales y personales. Puede encontrar esta nueva opción de configuración en el perfil **Restricciones de dispositivos** para la plataforma **Android for Work** en **Configuración del perfil de trabajo**.

#### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Creación de aplicaciones iOS limitadas a determinadas instancias regionales de App Store de Apple <!-- 1281692 -->
Podrá especificar la configuración regional del país durante la creación de una aplicación administrada de App Store de Apple.

> [!Note]  
> Actualmente, solo puede crear aplicaciones administradas del App Store de Apple que se encuentren en tiendas de Estados Unidos.

####  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Actualización de aplicaciones con licencia para dispositivos y usuarios de VPP de iOS  <!-- 1305564 -->  
Podrá configurar el token de VPP de iOS para actualizar todas las aplicaciones adquiridas para ese token a través del servicio de Intune. Intune detectará las actualizaciones de la aplicación de VPP dentro de la App Store y las insertará automáticamente en el dispositivo cuando este se registra.

Para consultar los pasos necesarios para establecer un token de VPP y habilitar las actualizaciones automáticas, consulte [Administrar aplicaciones de iOS compradas a través de un programa de compras por volumen con Microsoft Intune] (/intune/vpp-apps-ios).


### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas
#### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Adición de colección de entidad de asociación de dispositivo de usuario al modelo de datos de almacenamiento de datos de Intune <!-- 1187917 -->
Ahora puede generar informes y visualizaciones de datos con la información de asociación de dispositivo de usuario que asocia las colecciones de la entidad de dispositivo y de usuario. Es posible tener acceso al modelo de datos a través del archivo de Power BI (PBIX) recuperado de la página de almacenamiento de datos de Intune, a través del punto de conexión de OData o mediante el desarrollo de un cliente personalizado.

#### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Revisión del cumplimiento de directivas para los anillos de actualizaciones de Windows 10 <!-- 1067886 -->
Podrá revisar un informe de directiva para los círculos de actualizaciones de Windows 10 desde Actualizaciones de software > Estado de implementación por anillo de actualización. El informe de directiva incluye el estado de implementación para los anillos de actualización que ha configurado. 

#### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Nuevo informe que muestra los dispositivos iOS con versiones anteriores de iOS <!-- 1352223 -->
El informe **Dispositivos iOS obsoletos** está disponible desde el área de trabajo **Actualizaciones de software**. En el informe, puede ver una lista de dispositivos iOS supervisados destinados mediante una directiva de actualización iOS y que tienen actualizaciones disponibles. Para cada dispositivo, puede ver un estado por el que el dispositivo no se ha actualizado automáticamente. 

#### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Visualización de las asignaciones de directivas de protección de aplicaciones para la solución de problemas <!--  1475003 -->
En la próxima versión, la opción **Directiva de protección de aplicaciones** se agregará a la lista desplegable **Asignaciones** disponible en la hoja de la solución de problemas. Ahora puede seleccionar las directivas de protección de aplicaciones para ver las directivas de protección de aplicaciones asignadas a los usuarios seleccionados.



## <a name="week-of-october-2-2017"></a>Semana del 2 de octubre de 2017
### <a name="intune-apps"></a>Aplicaciones de Intune
#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Mejoras en el flujo de trabajo de configuración de dispositivos en el Portal de empresa <!--1490692-->
Hemos mejorado el flujo de trabajo de configuración de dispositivos en la aplicación Portal de empresa para Android. El lenguaje es más fácil de usar y es específico de su empresa. Además, hemos combinado pantallas siempre que hemos podido. Puede verlas en la página [Novedades de la interfaz de usuario de aplicaciones](whats-new-app-ui.md#week-of-october-2-2017).

#### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Se ha mejorado la guía sobre la solicitud de acceso a los contactos en dispositivos Android <!--1484985-->

La aplicación Portal de empresa para Android suele pedir al usuario final que acepte el permiso de los contactos. Si un usuario final no acepta este acceso, ahora verá una notificación en la aplicación en la que se le alerta de concederlo para el acceso condicional. 

#### <a name="secure-startup-remediation-for-android---1490712--"></a>Corrección del inicio seguro para Android <!--1490712-->

Los usuarios finales que tienen dispositivos Android podrán seleccionar el motivo de no compatibilidad en la aplicación del Portal de empresa. Cuando sea posible, se les llevará directamente a la ubicación correcta de la aplicación de configuración para poder resolver el problema. 

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Notificaciones de inserción adicionales para los usuarios finales en la aplicación Portal de empresa para Android Oreo <!--1475932-->

Los usuarios finales verán notificaciones adicionales que les indicarán cuándo la aplicación Portal de empresa para Android Oreo está realizando tareas en segundo plano, como la recuperación de directivas desde el servicio Intune. Con esto se aumenta la transparencia para los usuarios finales con respecto a cuando Portal de empresa realiza tareas administrativas en el dispositivo. Esto forma parte de la [optimización de la interfaz de usuario de Portal de empresa](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) general para la aplicación Portal de empresa para Android Oreo. 

Existen más optimizaciones para nuevos elementos de la IU que ya están habilitados para Android Oreo.  Los usuarios finales verán notificaciones adicionales en las que se les indicará el momento en el que la aplicación Portal de empresa esté realizando tareas en segundo plano, como la recuperación de directivas desde el servicio Intune.  Esto aumenta la transparencia para los usuarios finales sobre cuándo el Portal de empresa está realizando tareas administrativas en el dispositivo.

#### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nuevos comportamientos para la aplicación de Portal de empresa para Android con perfiles de trabajo <!---1485783--->

Cuando inscribe un dispositivo de Android for Work con un perfil de trabajo, la aplicación de Portal de empresa del perfil de trabajo es quien realiza las tareas de administración en el dispositivo. 

A menos que utilice una aplicación habilitada para MAM en el perfil personal, la aplicación de Portal de empresa para Android ya no tiene ninguna utilidad. Para mejorar la experiencia de perfil de trabajo, Intune ocultará automáticamente la aplicación de Portal de empresa personal una vez que se complete correctamente la inscripción del perfil de trabajo.

La aplicación Portal de empresa para Android se puede habilitar en cualquier momento en el perfil personal; para ello, vaya a [Portal de empresa de en Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) y pulse en **Habilitar**.

#### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Puesta en modo de mantenimiento del Portal de empresa para Windows 8.1 y Windows Phone 8.1 <!--1428681-->

A partir de octubre de 2017, las aplicaciones de Portal de empresa para Windows 8.1 y Windows Phone 8.1 pasarán a modo de mantenimiento. Esto significa que las aplicaciones y los escenarios existentes, como la inscripción y el cumplimiento, seguirán siendo compatibles para estas plataformas. Estas aplicaciones seguirán estando disponibles para su descarga a través de los canales de lanzamiento existentes, como Microsoft Store. 

Una vez que se encuentre en modo de mantenimiento, estas aplicaciones solo recibirán actualizaciones de seguridad críticas. No se publicarán actualizaciones ni características para estas aplicaciones. Para las nuevas características, se recomienda que actualice los dispositivos a Windows 10 o Windows 10 Mobile. 


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="block-unsupported-samsung-knox-device-enrollment------1490695----"></a>Bloqueo de la inscripción de dispositivos Samsung KNOX no compatible <!--- 1490695 --->

La aplicación del Portal de empresa solo intenta inscribir dispositivos Samsung KNOX compatibles. Para evitar errores de activación de KNOX que impidan la inscripción de MDM, la inscripción de dispositivos solo se intenta si el dispositivo aparece en la [lista de dispositivos publicados por Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Los dispositivos Samsung pueden tener números de modelo que admitan KNOX, mientras que otros no. Compruebe la compatibilidad de KNOX con el distribuidor de su dispositivo antes de la compra y la implementación. Encontrará la lista completa de dispositivos comprobados en la [configuración de directivas de Android y Samsung KNOX Standard](/intune/supported-devices-browsers.md#intune-supported-devices).

#### <a name="end-of-support-for-android-43-and-lower----1171126-1326920----"></a>Fin de la compatibilidad con Android 4.3 y anterior <!---1171126, 1326920 --->
Las aplicaciones administradas y la aplicación Portal de empresa para Android exigirán Android 4.4 y versiones posteriores para acceder a recursos de empresa. En diciembre, todos los dispositivos inscritos serán eliminados, lo que provocará su pérdida de acceso a los recursos de empresa. Si está usando directivas de protección de aplicaciones sin MDM, las aplicaciones no recibirán actualizaciones y la calidad de su experiencia empeorará con el tiempo.

#### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Informar a los usuarios finales de la información de dispositivo que puede verse en los dispositivos inscritos <!--1165314-->
Estamos agregando **Tipo de propiedad** a la pantalla Detalles del dispositivo en todas las aplicaciones del Portal de empresa. Esto permitirá que los usuarios obtengan más información sobre la privacidad directamente en el artículo [¿Qué información puede ver mi empresa cuando inscribo mi dispositivo en Intune?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) Se irá implementando en todas las aplicaciones del Portal de empresa en un futuro próximo (se anunció para iOS en [septiembre](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)).


## <a name="week-of-september-25-2017"></a>Semana del 25 de septiembre de 2017

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="intune-supports-ios-11---1428975--"></a>Intune es compatible con iOS 11 <!--1428975-->
Intune es compatible con iOS 11. Ya se anunció anteriormente en el [blog de soporte técnico de Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

#### <a name="end-of-support-for-ios-80----1164477---"></a>Fin de la compatibilidad con iOS 8.0 <!---1164477--->
Las aplicaciones administradas y la aplicación Portal de empresa para iOS exigirán iOS 9.0 y versiones posteriores para acceder a recursos de empresa. Los dispositivos que no estén actualizados antes de septiembre de este año ya no podrán acceder a esas aplicaciones ni al Portal de empresa. 

### <a name="intune-apps"></a>Aplicaciones de Intune

#### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Adición de acción de actualización a la aplicación de Portal de empresa para Windows 10 <!--1132468-->
La aplicación de Portal de empresa para Windows 10 permite a los usuarios actualizar los datos de la aplicación tirando para actualizar o, en equipos de escritorio, presionando F5.



## <a name="notices"></a>Notificaciones

### <a name="deprecating-support-for-os-x-mavericks-1010-and-previous-versions-of-macos---1489263-plan-for-change-for-1802--"></a>Se está poniendo en desuso el soporte técnico de OS X Mavericks 10.10 y versiones anteriores de macOS <!--1489263, plan for change for 1802-->

Anunciamos que, en febrero de 2018, empezaremos a poner en desuso la inscripción de dispositivos con OS X Mavericks 10.10 y versiones anteriores de macOS. Intune es totalmente compatible con OS X Yosemite 10.11 y versiones más recientes.

### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Nueva ruta de acceso para los dispositivos administrados en API Graph <!-- 1586728 -->
Hemos realizado un cambio en la ruta de acceso que se usa para obtener acceso a los dispositivos administrados en la versión beta de API Graph. 

| | |
|--|--|
| Ruta de acceso actual |  https://graph.microsoft.com/beta/managedDevices |
| Nueva ruta de acceso | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

Ambas rutas de acceso funcionarán durante el mes de octubre. Después de la versión del servicio de octubre, solo funcionará la nueva ruta de acceso.  Si usa API Graph para tener acceso a los dispositivos administrados, actualice y compruebe los scripts y las aplicaciones con la nueva ruta de acceso. Para conocer otros cambios, consulte el [registro de cambios mensual de API Graph](https://developer.microsoft.com/graph/docs/concepts/changelog).


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Acceso directo a los escenarios de inscripción de Apple <!--951869-->
Para las cuentas de Intune creadas después de enero de 2017, Intune habilitó el acceso directo a los escenarios de inscripción de Apple mediante la carga de trabajo de inscripción de dispositivos en Azure Portal. Anteriormente, la vista preliminar de inscripción de Apple solo era accesible desde los vínculos del portal clásico de Intune. Las cuentas de Intune creadas antes de enero de 2017 requieren una migración única antes de que estas características estén disponibles en Azure. Aún no se ha anunciado la programación para la migración, pero la información estará disponible tan pronto como sea posible. Se recomienda encarecidamente crear una cuenta de prueba para probar la nueva experiencia si su cuenta no tiene acceso a Azure Portal.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Roles de administración que se reemplazan en el Portal de Azure
Los roles de administración de aplicaciones móviles (MAM) existentes (colaborador, propietario y de solo lectura) usados en el portal clásico de Intune (Silverlight) se reemplazan por un conjunto completo de nuevos controles de administración basada en roles (RBAC) en el Portal de Intune Azure. Cuando haya migrado a Azure Portal, tendrá que reasignar estos nuevos roles de administración a los administradores. Para obtener más información sobre RBAC y los nuevos roles, vea [Roles de Intune (RBAC) para Microsoft Intune](/intune/role-based-access-control).



## <a name="whats-coming"></a>Próximas novedades

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Cambios en la compatibilidad de la aplicación de portal de empresa de iOS de Intune <!-- 1164474  -->
Próximamente, habrá una nueva versión de la aplicación de portal de empresa de Microsoft Intune para iOS que solo admitirá dispositivos que ejecuten iOS 9.0 o posterior. La versión del portal de empresa que admite iOS 8 todavía estará disponible durante un período de tiempo muy breve. En cambio, tenga en cuenta que si también usa aplicaciones iOS habilitadas para MAM, se admiten iOS 9.0 y versiones posteriores, por lo que querrá asegurarse de que sus usuarios finales actualicen al sistema operativo más reciente. 

#### <a name="how-does-this-affect-me"></a>¿Cómo me afecta esto?
Le informamos de esto con antelación, incluso cuando no tenemos fechas específicas, para que tenga tiempo para planear. Asegúrese de que sus usuarios hayan actualizado a iOS 9 o versiones posteriores y, cuando se publique la aplicación Portal de empresa, solicite a sus usuarios finales que la actualicen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>¿Qué necesito hacer para prepararme para este cambio?
Anime a los usuarios a que actualicen a iOS 9.0 o posterior para aprovechar las nuevas características de Intune.  Anime a los usuarios a que instalen la última versión del portal de empresa y se aprovechen de las nuevas características que ofrecerá.

Vaya a Intune en Azure Portal y vea Dispositivos > Todos los dispositivos y filtre por la versión de iOS para ver cualquier dispositivo actual con sistemas operativos anteriores a iOS 9.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple requerirá actualizaciones para la Seguridad de transporte de aplicaciones <!--748318-->
Apple ha anunciado que se aplicarán requisitos específicos para la Seguridad de transporte de aplicaciones (ATS). ATS se usa para aplicar una seguridad más estricta en todas las comunicaciones de aplicaciones a través de HTTPS. Este cambio afecta a los clientes de Intune que usan aplicaciones del portal de empresa de iOS.

Hay disponible una versión de la aplicación Portal de empresa para iOS a través del programa Apple TestFlight que aplica los nuevos requisitos de ATS. Si desea probarla para que pueda experimentar el cumplimiento de ATS, envíe un correo electrónico a <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> con su nombre, apellidos, dirección de correo electrónico y nombre de la empresa. Visite nuestro [blog de soporte técnico de Intune](https://aka.ms/compportalats) para obtener más información.

## <a name="see-also"></a>Consulte también
* [Blog de Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guía básica de Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novedades de la interfaz de usuario del portal de empresa](whats-new-app-ui.md)
* [Novedades de los meses anteriores](whats-new-archive.md)
