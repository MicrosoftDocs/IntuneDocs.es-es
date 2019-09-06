---
title: Novedades de Microsoft Intune (Azure) | Microsoft Docs
titleSuffix: ''
description: Descubra las novedades del portal de Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09d80964a417772b1f011478db59398ceede5c5e
ms.sourcegitcommit: cf40f641af4746a1e34edd980dc6ec96fd040126
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122136"
---
# <a name="whats-new-in-microsoft-intune"></a>Novedades de Microsoft Intune

Conozca las novedades semanales de Microsoft Intune. También puede encontrar [notificaciones importantes](#notices), [versiones anteriores](whats-new-archive.md) e información sobre [cómo se publican las actualizaciones del servicio de Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> El lanzamiento de cada [actualización mensual](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) puede tardar hasta tres días y se realizará en el orden siguiente:
> - Día 1: Asia Pacífico (APAC)
> - Día 2: Europa, Oriente Medio y África (EMEA)
> - Día 3: América del Norte
> 
> Algunas características pueden lanzarse a lo largo de varias semanas y pueden no estar disponibles para todos los clientes durante la primera semana.
>
> Revise la [página En desarrollo](in-development.md) para ver una lista de las características que aparecerán en una versión próxima.

**Fuente RSS**: reciba notificaciones cuando esta página se actualice copiando y pegando la siguiente dirección URL en su lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-august-26-2019"></a>Semana del 26 de agosto de 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer----5228061---"></a>Configuración de Microsoft Edge mediante plantillas administrativas para Windows 10 y versiones más recientes <!-- 5228061 -->

En los dispositivos Windows 10 y más recientes, puede crear plantillas administrativas para configurar las opciones de directiva de grupo en Intune. En esta actualización, puede configurar las opciones que se aplican a la versión 77 y posteriores de Microsoft Edge.

Para más información sobre las plantillas administrativas, vea [Usar plantillas de Windows 10 para configurar opciones de directiva de grupo en Intune](administrative-templates-windows.md).

Se aplica a:

- Windows 10 y versiones más recientes (Windows RS4+)

## <a name="week-of-august-12-2019"></a>Semana del 12 de agosto de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144-----"></a>Control del comportamiento de desinstalación de aplicaciones iOS en anulación de la inscripción de dispositivos <!-- 3504144   -->
Los administradores pueden administrar si una aplicación se quita de un dispositivo o se conserva en este cuando se anula la inscripción de dicho dispositivo en el nivel de grupo de usuarios o dispositivos. 

#### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Categorización de aplicaciones de Microsoft Store para Empresas <!-- 3926922 -->
Puede categorizar las aplicaciones de la Tienda Microsoft para Empresas. Para ello, elija aplicaciones  > **cliente** > de **Intune** **aplicaciones** > seleccione una aplicación de Microsoft Store para empresas  > **categoría**de **información**de la aplicación. En el menú desplegable, asigne una categoría.

#### <a name="customized-notifications-for-microsoft-intune-app-users----4843354----"></a>Notificaciones personalizadas para usuarios de aplicaciones de Microsoft Intune <!-- 4843354  -->
La aplicación de Microsoft Intune para Android ahora admite la visualización de notificaciones de envío personalizadas y se alinea con la compatibilidad agregada recientemente en las aplicaciones de Portal de empresa para iOS y Android. Para más información, consulte [Envío de notificaciones personalizadas en Intune](custom-notifications.md).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946-----"></a>Nuevas características para dispositivos dedicados de Android Enterprise en el modo de varias aplicaciones <!-- 3755304 3041943 3041946   -->
En Intune, puede controlar las características y las configuraciones en una experiencia de estilo de quiosco en dispositivos dedicados (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **Solo el propietario del dispositivo, Restricciones de dispositivos** para el tipo de perfil).

En esta actualización, se agregan las siguientes características:

- **Dispositivos dedicados** > **Varias aplicaciones:** el **botón Inicio virtual** se puede mostrar al avanzar en el dispositivo o flotar en la pantalla para que los usuarios puedan moverla.
- **Dispositivos dedicados** > **Varias aplicaciones:** **Acceso a la linterna** permite a los usuarios usar la linterna. 
- **Dispositivos dedicados** > **Varias aplicaciones:** **Control del volumen de elementos multimedia**  permite a los usuarios controlar el volumen multimedia del dispositivo con un control deslizante. 
- **Dispositivos dedicados** > **Varias aplicaciones:**  **habilite un protector de pantalla**, cargue una imagen personalizada y controle cuándo se muestra el protector.

Para ver la configuración actual, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](device-restrictions-android-for-work.md#dedicated-device-settings).

Se aplica a:  
- Dispositivos Android Enterprise dedicados

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215-3574238-3574235-3574232-----"></a>Nueva aplicación y perfiles de configuración para dispositivos Android Enterprise totalmente administrados <!-- 3574215 3574238 3574235 3574232   -->
Mediante el uso de perfiles, puede configurar las opciones que aplican la configuración de VPN, correo electrónico y Wi-Fi al propietario de dispositivos (totalmente administrados) Android Enterprise. En esta actualización, puede:

- Use las [directivas de configuración de aplicaciones](app-configuration-policies-use-android.md) para implementar la configuración de correo electrónico de Outlook, Gmail y Nine Work.
- Use los perfiles de configuración de dispositivos para implementar la [configuración de certificados raíz de confianza](certificates-configure.md).
- Use los perfiles de configuración de dispositivos para implementar la configuración de [VPN](vpn-settings-android-enterprise.md) y [Wi-Fi](wi-fi-settings-android-enterprise.md).

> [!IMPORTANT]
> Con esta característica, los usuarios se autentican con su nombre de usuario y contraseña para los perfiles de VPN, Wi-Fi y correo electrónico. Actualmente, la autenticación basada en certificados no está disponible. 

Se aplica a:  
- Propietario del dispositivo Android Enterprise (totalmente administrado)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices---3914202-----"></a>Control de las aplicaciones, los archivos, los documentos y las carpetas que se abren cuando los usuarios inician sesión en dispositivos macOS <!--3914202   -->
Puede habilitar y configurar características de dispositivos macOS (**Configuración del dispositivos** > **Perfiles** > **Crear perfil** > **macOS** para la plataforma >**Características del dispositivo**  para el tipo de perfil). 

En esta actualización, hay una nueva configuración de elementos de inicio de sesión para controlar qué aplicaciones, archivos, documentos y carpetas se abren cuando un usuario inicia sesión en el dispositivo inscrito. 

Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](macos-device-features-settings.md).

Se aplica a:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings------4464404----------"></a>Las fechas límite reemplazan la configuración del reinicio establecido de los anillos de Windows Update   <!-- 4464404        -->
Para estar en consonancia con [los cambios recientes en el servicio de Windows](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing), los anillos de actualización de Windows 10 de Intune ahora [admiten la configuración de fechas límite](windows-update-settings.md). Las *fechas límite* determinan cuándo un dispositivo instala las actualizaciones de características y seguridad.  En los dispositivos que ejecutan Windows 10 1903 o una versión posterior, las *fechas límite* sustituyen a las configuraciones del *reinicio establecido*.  En el futuro, las *fechas límite* reemplazarán también al *reinicio establecido* de las versiones anteriores de Windows 10.  

Cuando no configure las *fechas límite*, los dispositivos seguirán usando la configuración de *reinicio establecido*, pero [Intune dejará de admitir la configuración de reinicio establecido](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-) en una actualización futura.  

Planee el uso de *fechas límite* para todos los dispositivos Windows 10. Una vez que haya establecido la configuración de las *fechas límite*, puede cambiar las configuraciones de Intune para que el *reinicio establecido* sea Sin configurar. Cuando se establece en Sin configurar, Intune deja de administrar esa configuración en los dispositivos, pero no quita las últimas configuraciones de la configuración del dispositivo. Por lo tanto, las últimas configuraciones que se establecieron para el *reinicio establecido* permanecen activas y en uso en los dispositivos hasta que dichas configuraciones se modifican mediante un método distinto de Intune. Más adelante, cuando la versión de los dispositivos de Windows cambia o cuando la compatibilidad de Intune con las *fechas límite* se expande a la versión de Windows de los dispositivos, el dispositivo comenzará a usar la nueva configuración, que ya está en su lugar.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors--------4704642--------"></a>Compatibilidad con varias instancias de Microsoft Intune Certificate Connector   <!--   4704642      -->
Intune ahora admite la instalación y el uso de varias instancias de [Microsoft Intune Certificate Connectors para operaciones PKCS](certficates-pfx-configure.md). Este cambio admite el equilibrio de carga y la alta disponibilidad del conector. Cada instancia de conector puede procesar solicitudes de certificado desde Intune.  Si un conector no está disponible, otros conectores continúan procesando las solicitudes. 

Para usar varios conectores, no es necesario actualizar a la versión más reciente del software del conector.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709-----"></a>Nuevas configuraciones y cambios en la configuración existente para restringir características en dispositivos iOS y macOS <!-- 4867699 4867709   -->
Puede crear perfiles para restringir configuraciones en dispositivos que ejecutan iOS y macOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** o **macOS** para el tipo de plataforma > **Restricciones de dispositivos**). En esta actualización se incluyen las características siguientes:

- En**macOS** > **Restricciones de dispositivos** > **Nube y almacenamiento** use la nueva configuración **Handoff** para impedir que los usuarios empiecen a trabajar en un dispositivo macOS y sigan trabajando en otro dispositivo macOS o iOS.

  Para ver la configuración actual, vaya a [Configuración de dispositivos macOS para permitir o restringir características mediante Intune](device-restrictions-macos.md).

- En **iOS** > **Restricciones de dispositivos**, hay algunos cambios:

  - **Aplicaciones integradas** > **Buscar mi iPhone (solo supervisado)** : nueva configuración que bloquea esta característica en la característica Buscar mi aplicación. 
  - **Aplicaciones integradas** > **Find My Friends (solo supervisado)** : nueva configuración que bloquea esta característica en la característica Buscar mi aplicación. 
  - **Inalámbrica** > **Modificación del estado de Wi-Fi (solo supervisado)** : nueva configuración que impide que los usuarios activen o desactiven la conexión Wi-Fi en el dispositivo.
  - **Teclado y diccionario** > **QuickPath (solo supervisado)** : nueva configuración que bloquea la característica QuickPath.
  - **Nube y almacenamiento**: **Continuación de la actividad** pasa a llamarse **Handoff**.

  Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](device-restrictions-ios.md).

Se aplica a:  
- macOS 10.15 y versiones más recientes
- iOS 13 y versiones más recientes

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809-----"></a>Algunas restricciones de dispositivos iOS no supervisadas se supervisarán solo con la versión iOS 13.0 <!-- 4867809   -->
En esta actualización, algunas configuraciones se aplican a los dispositivos solo supervisados con la versión iOS 13.0. Si esta configuración se definen y asignan a dispositivos no supervisados antes de la versión de iOS 13.0, dicha configuración se seguirá aplicando a esos dispositivos no supervisados. También se aplican después de que los dispositivos se actualicen a iOS 13.0. Estas restricciones se quitan de los dispositivos no supervisados de los que se realiza una copia de seguridad y se restauran. 

Estas opciones incluyen:

- Tienda de aplicaciones, presentación de documentos, juegos
  - Tienda de aplicaciones
  - Música, podcasts o contenido de noticias explícitos de iTunes
  - Incorporación de amigos a Game Center
  - Juego multijugador
- Aplicaciones integradas
  - Cámara
    - FaceTime
  - Safari
    - Autorrellenar
- Nube y almacenamiento
  - Copia de seguridad en iCloud
  - Bloquear la sincronización de documentos de iCloud
  - Bloquear la sincronización de Keychain en iCloud

Para ver la configuración actual, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](device-restrictions-ios.md).

Se aplica a:  
- iOS 13.0 y versiones más recientes

#### <a name="improved-device-status-for-macos-filevault-encryption-----4944983-----------"></a>Estado de dispositivo mejorado para el cifrado de FileVault de macOS  <!-- 4944983         -->
Hemos actualizado varios [mensajes de estado de dispositivo](encryption-monitor.md#device-encryption-status) para el cifrado de FileVault en dispositivos macOS.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status----5119229---"></a>Algunas configuraciones de examen del Antivirus de Windows Defender en el informe muestran un estado de error <!-- 5119229 -->
En Intune, puede crear directivas para usar el Antivirus de Windows Defender para examinar los dispositivos Windows 10 (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para la plataforma > **Restricciones del dispositivo** para el tipo de perfil > **Antivirus de Windows Defender**). Los informes **Hora a la que se realizará un examen rápido diario** y **Tipo de examen del sistema para realizar** muestran un estado de error, cuando es realmente un estado correcto. 

En esta actualización se ha corregido este comportamiento. Por lo tanto las configuraciones **Hora a la que se realizará un examen rápido diario** y **Tipo de examen del sistema para realizar** muestran un estado correcto cuando los exámenes se completan correctamente y muestran un estado de error cuando la configuración no se puede aplicar. 

Para más información sobre la configuración de Windows Defender Antivirus consulte [Configuración de dispositivos con Windows 10 y versiones posteriores para permitir o restringir características mediante Intune](device-restrictions-windows-10.md#windows-defender-antivirus). 

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="default-scope-tags----3702875----"></a>Etiquetas de ámbito predeterminadas <!-- 3702875  -->
Ahora hay disponible una nueva etiqueta de ámbito predeterminada integrada. Todos los objetos de Intune no etiquetados que admiten etiquetas de ámbito se asignan automáticamente a la etiqueta de ámbito predeterminada. La etiqueta de ámbito **predeterminada** se agrega a todas las asignaciones de roles existentes para mantener la paridad con la experiencia de administración hoy en día. Si no desea que un administrador vea los objetos de Intune con la etiqueta de ámbito predeterminada, quítela de la asignación de roles. Esta característica es similar a la característica de ámbitos de seguridad de System Center Configuration Manager. Para más información, consulte [Usar control de acceso basado en rol (RBAC) y etiquetas de ámbito para TI distribuida](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support----4869749-----"></a>Soporte técnico del administrador de dispositivos de inscripción de Android <!-- 4869749   -->
La opción de inscripción del administrador de dispositivos Android se ha agregado a la página Inscripción de Android (**Intune** > **Inscripción de dispositivos** > **Inscripción de Android** ). El administrador de dispositivos Android seguirá estando habilitado de forma predeterminada para todos los inquilinos.  Para más información, consulte [Inscripción del administrador de dispositivos Android](android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Omisión de más pantallas en el Asistente de configuración <!--4877451  -->
Puede establecer perfiles de Programa de inscripción de dispositivos para omitir las siguientes pantallas del Asistente de configuración:
- Para iOS
    - Aspecto
    - Express Language (Idioma rápido)
    - Idioma preferido
    - Device to Device Migration (Migración entre dispositivos)
- Para macOS
    - Tiempo de pantalla
    - Configuración de Touch ID

Para más información sobre la personalización del Asistente de configuración, consulte [Creación de un perfil de inscripción de Apple](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) y [Creación de un perfil de inscripción de Apple para macOS](device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process----3823054---"></a>Incorporación de una columna de usuario al proceso de carga de CSV del dispositivo AutoPilot <!-- 3823054 -->
Ahora puede agregar una columna de usuario a la carga CSV para Dispositivos Autopilot. Esto le permite asignar usuarios en masa en el momento de importar el archivo CSV. El nuevo formato de las filas en el archivo CSV es similar al siguiente: número-de-serie, id.-del-producto-windows, hash-de-hardware, etiqueta-de-grupo-opcional, usuario-asignado-opcional. Para más información, consulte [Inscripción de dispositivos Windows en Intune con Windows Autopilot](enrollment-autopilot.md).


### <a name="device-management"></a>Administración de dispositivos

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configuración del límite de tiempo de limpieza automática de dispositivos en treinta días <!--4231059  -->
Puede establecer el límite de tiempo de limpieza automática de dispositivos en un plazo de 30 días (en lugar del límite anterior de noventa días) después del último inicio de sesión. Para ello, vaya a **Intune** > **configuración** > de**dispositivos** > **limpiar reglas**.

#### <a name="build-number-included-on-android-device-hardware-page----4461910-----"></a>Número de compilación incluido en la página Hardware del dispositivo Android <!-- 4461910   -->
Una nueva entrada en la página Hardware de cada dispositivo Android incluye el número de compilación del sistema operativo del dispositivo. Para más información, consulte [Ver detalles del dispositivo en Intune](device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Semana del 5 de agosto de 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices-----4843713---"></a>Zebra Technologies es un OEM admitido para OEMConfig en dispositivos Android Enterprise  <!-- 4843713 -->

En Intune, puede crear perfiles de configuración de dispositivo y aplicar la configuración a los dispositivos Android Enterprise mediante OEMConfig (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **OEMConfig** para el tipo de perfil).

En esta actualización, Zebra Technologies es un fabricante de equipos originales (OEM) admitido para OEMConfig. Para obtener más información sobre OEMConfig, consulte [Uso y administración de dispositivos Android Enterprise con OEMConfig](android-oem-configuration-overview.md).

Se aplica a:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>Semana del 22 de julio de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="customized-notifications-for-users-and-groups-------16766574------------"></a>Notificaciones personalizadas para usuarios y grupos    <!-- 16766574          -->
Envíe notificaciones de inserción personalizadas desde la aplicación del Portal de empresa a los usuarios en dispositivos iOS y Android que administra con Intune. Estas notificaciones de inserción móviles son altamente personalizables con texto libre y se pueden usar con cualquier fin. Puede dirigirlas a diferentes grupos de usuarios de su organización. Para obtener más información, consulte [Notificaciones personalizadas](custom-notifications.md).

#### <a name="googles-device-policy-controller-app----3041950----"></a>Aplicación de controlador de directiva de dispositivo de Google <!-- 3041950  -->
La aplicación de Pantalla principal administrada ahora proporciona acceso a la aplicación de directiva de dispositivo Android de Google. La aplicación de Pantalla principal administrada es un iniciador personalizado que se usa para dispositivos inscritos en Intune, como dispositivos dedicados de Android Enterprise (AE) que usan el modo de pantalla completa de varias aplicaciones. Puede acceder a la aplicación de directiva de dispositivo Android o guiar a los usuarios a esta aplicación, con fines de soporte técnico y depuración. Esta capacidad de inicio está disponible en el momento en que el dispositivo se inscribe y se bloquea en la Pantalla principal administrada. No se necesitan instalaciones adicionales para usar esta funcionalidad.

#### <a name="outlook-protection-settings-for-ios-and-android-devices----3212619---"></a>Configuración de protección de Outlook para dispositivos iOS y Android <!-- 3212619 -->
Ahora puede configurar los valores de configuración de protección generales de datos y aplicaciones para Outlook para iOS y Android mediante controles de administración de Intune simples sin inscripción de dispositivos. Los valores de configuración generales de aplicaciones proporcionan paridad con la configuración que pueden habilitar los administradores al administrar Outlook para iOS y Android en dispositivos inscritos. Para obtener más información sobre la configuración de Outlook, consulte [Implementación de Outlook para iOS y opciones de configuración de aplicación de Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Uso de "reglas de aplicabilidad" al crear perfiles de configuración de dispositivo Windows 10 <!-- 2549910 eeready   idstaged -->

Puede crear perfiles de configuración de dispositivo Windows 10 (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **Windows 10** para la plataforma > **Reglas de aplicabilidad**). En esta actualización, puede crear una **regla de aplicabilidad** para que el perfil solo se aplique a una edición o una versión en concreto. Por ejemplo, cree un perfil que permita algunas opciones de configuración de BitLocker. Una vez que agregue el perfil, use una regla de aplicabilidad para que este solo se aplique a los dispositivos que ejecuten Windows 10 Enterprise.

Para agregar una regla de aplicabilidad, consulte [Reglas de aplicabilidad](device-profile-create.md#applicability-rules).

Se aplica a: Windows 10 y versiones posteriores

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices----3330008----"></a>Uso de tokens para agregar información específica del dispositivo en perfiles personalizados para dispositivos iOS y macOS <!-- 3330008  -->
Puede usar perfiles personalizados en dispositivos iOS y macOS para configurar opciones y características no integradas en Intune (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** o **macOS** para la plataforma > **Personalizado** para el tipo de perfil). En esta actualización, puede agregar tokens a sus archivos `.mobileconfig` para agregar información específica del dispositivo. Por ejemplo, puede agregar `Serial Number: {{serialnumber}}` a su archivo de configuración para mostrar el número de serie del dispositivo.

Para crear un perfil personalizado, consulte [Configuración personalizada de iOS](custom-settings-ios.md) o [Configuración personalizada de macOS](custom-settings-macos.md).

Se aplica a:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769-----"></a>Nuevo diseñador de configuraciones al crear un perfil OEMConfig para Android Enterprise <!-- 3712769   -->
En Intune, puede crear un perfil de configuración de dispositivo que use una aplicación OEMConfig (Configuración del dispositivo > Perfiles > Crear perfil > Android Enterprise para la plataforma > OEMConfig para el tipo de perfil). Al hacerlo, se abre un editor JSON con una plantilla y valores que debe cambiar. 

Esta actualización incluye un diseñador de configuraciones con una experiencia de usuario mejorada que muestra detalles insertados en la aplicación entre los que se incluyen títulos, descripciones, etc. El editor JSON sigue estando disponible y muestra cualquier cambio que realiza en el diseñador de aplicaciones.

Para ver la configuración actual, vaya a [Uso y administración de dispositivos Android Enterprise con OEMConfig](android-oem-configuration-overview.md).

Se aplica a: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello-----4089576--------------"></a>Interfaz de usuario actualizada para configurar Windows Hello  <!-- 4089576            -->
Hemos actualizado la consola donde [configura Intune para usar Windows Hello para empresas](windows-hello.md). Ya están disponibles todas las opciones de configuración en el mismo panel de la consola donde habilita compatibilidad con Windows Hello. 


#### <a name="intune-powershell-sdk----4924113---"></a>SDK de PowerShell de Intune <!-- 4924113 --> 
El SDK de PowerShell de Intune, que proporciona compatibilidad con la API de Intune a través de Microsoft Graph, se ha actualizado a la versión 6.1907.1.0. Ahora, el SDK admite lo siguiente:
- Funciona con Azure Automation.
- Admite operaciones de lectura de autenticación de solo aplicación. 
- Admite nombres abreviados descriptivos como alias.
- Se ajusta a las convenciones de nomenclatura de PowerShell. De forma específica, se ha cambiado el nombre del parámetro `PSCredential` (en el cmdlet `Connect-MSGraph`) por `Credential`.
- Admite la especificación manual del valor del encabezado `Content-Type` al usar el cmdlet `Invoke-MSGraphRequest`.

Para obtener más información, consulte [SDK de PowerShell para Graph API de Microsoft Intune](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="updates-for-enrollment-restrictions-----2871968---"></a>Actualizaciones de las restricciones de inscripción  <!-- 2871968 -->
Las restricciones de inscripción para nuevos inquilinos se han actualizado para que se permitan los perfiles de trabajo de Android Enterprise de forma predeterminada. Los inquilinos existentes no experimentarán cambio alguno. Para usar los perfiles de trabajo de Android Enterprise, aún deberá [conectar su cuenta de Intune a su cuenta de Google Play administrada](https://docs.microsoft.com/intune/connect-intune-android-enterprise).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions---4089575-4089579----"></a>Actualizaciones de interfaz de usuario de las restricciones de inscripción y la inscripción de Apple <!--4089575, 4089579  -->
Los dos procesos siguientes usan una interfaz de usuario de estilo de asistente:
- Inscripción de dispositivos de Apple. Para obtener más información, consulte [Inscripción automática de dispositivos iOS con el Programa de inscripción de dispositivos de Apple](device-enrollment-program-enroll-ios.md).
- Creación de restricciones de inscripción. Para obtener más información, consulte [Establecer restricciones de inscripción](enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices----4711509--idmiss---"></a>Control de la configuración previa de identificadores de dispositivos corporativos para dispositivos Android Q <!-- 4711509  idmiss -->
En Android Q (v10), Google no permitirá a los agentes MDM de dispositivos Android (administrador de dispositivos) administrados heredados recopilar información del identificador de dispositivo.  Intune tiene una característica que permite a los administradores de TI [configurar de forma previa una lista de números de serie del dispositivo](https://docs.microsoft.com/intune/corporate-identifiers-add#identify-corporate-owned-devices-with-imei-or-serial-number) para etiquetar automáticamente estos dispositivos como propiedad corporativa. Esta característica no funcionará para los dispositivos Android Q que administre el administrador de dispositivos.  Independientemente de si se carga el número de serie o IMEI del dispositivo, siempre se considerará personal durante la inscripción de Intune.  Puede cambiar manualmente la propiedad a corporativa tras la inscripción.  Esto solo afecta a las nuevas inscripciones, no a los dispositivos inscritos existentes.  Los dispositivos Android administrados con perfiles de trabajo no se ven afectados por este cambio y continuarán funcionando como lo hacen en la actualidad.  Además, los dispositivos Android Q inscritos como administrador de dispositivos ya no podrán informar sobre el número de serie o IMEI en la consola de Intune como propiedades del dispositivo.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices----4977730---"></a>Los iconos han cambiado para las inscripciones de Android Enterprise (perfil de trabajo, dispositivos dedicados y dispositivos completamente administrados) <!-- 4977730 -->
Los iconos de los perfiles de inscripción de Android Enterprise han cambiado. Para ver los nuevos iconos, vaya a **Intune** > **Inscripción** > **Inscripción de Android** > busque en **Perfiles de inscripción**.


#### <a name="windows-diagnostic-data-collection-change----4113859---"></a>Cambio en la recopilación de datos de diagnóstico de Windows <!-- 4113859 -->
El valor predeterminado de la recopilación de datos de diagnóstico ha cambiado para los dispositivos con la versión 1903 de Windows 10 y posteriores. A partir de Windows 10 1903, la recopilación de datos de diagnóstico se habilita de forma predeterminada. Los datos de diagnóstico de Windows son datos técnicos vitales de dispositivos Windows sobre el dispositivo y el rendimiento de Windows y el software relacionado. Para obtener más información, consulte [Configurar los datos de diagnóstico de Windows en la organización](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Los dispositivos Autopilot también participan en la telemetría "completa" a menos que se establezca lo contrario en el perfil de Autopilot con [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Administración de dispositivos

#### <a name="improve-device-location---3855417----"></a>Mejora de la ubicación del dispositivo<!-- 3855417  -->
Puede acercar las coordenadas exactas de un dispositivo mediante la acción **Buscar dispositivo**. Para obtener más información sobre cómo buscar dispositivos iOS perdidos, consulte [Búsqueda de dispositivos iOS perdidos](device-locate.md).


### <a name="device-security"></a>Seguridad de dispositivos

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview------1311949-------"></a>Configuración avanzada del Firewall de Windows Defender (versión preliminar pública)  <!--  1311949     -->  
Use Intune para administrar las [reglas de firewall personalizadas como parte de un perfil de configuración de dispositivo](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) para Endpoint Protection en Windows 10. Las reglas pueden especificar un comportamiento entrante y saliente en las aplicaciones, las direcciones de red y los puertos. 

#### <a name="updated-ui-for-managing-security-baselines------4091125-------"></a>Interfaz de usuario actualizada para administrar líneas de base de seguridad   <!-- 4091125     -->
Hemos actualizado la [experiencia de creación y edición](security-baselines.md#create-the-profile) en la consola de Intune para nuestras líneas de base de seguridad. Los cambios son:

Un formato de estilo de asistente que se ha comprimido en una sola hoja. en una hoja. Este nuevo diseño elimina la expansión de la hoja que requiere que los profesionales de TI exploren en profundidad varios paneles independientes.  
Ahora puede crear asignaciones como parte de la experiencia de creación y edición, en lugar de tener que volver posteriormente para asignar líneas de base. Hemos agregado un resumen de la configuración que puede ver antes de crear una nueva línea de base y al editar una existente. Al editar, en el resumen solo se muestra la lista de elementos establecidos en la primera categoría de propiedades editadas.



<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Semana del 15 de julio de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="managed-home-screen-and-managed-settings-icons----4918107---"></a>Iconos Managed Home Screen y Configuración administrada <!-- 4918107 -->
El icono de la aplicación Managed Home Screen y el icono **Configuración administrada** se han actualizado. La aplicación Managed Home Screen solo la usan dispositivos inscritos en Intune, como dispositivos dedicados de Android Enterprise (AE) y que se ejecutan en modo de pantalla completa con varias aplicaciones. Para obtener más información sobre la aplicación de Pantalla principal administrada, consulte [Configuración de la aplicación Managed Home Screen de Microsoft para Android Enterprise](app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices----4918136---"></a>Directiva de dispositivos Android en dispositivos dedicados de Android Enterprise <!-- 4918136 -->
Puede obtener acceso a la aplicación Directiva de dispositivos Android en la pantalla de depuración de la aplicación Managed Home Screen. La aplicación Managed Home Screen solo la usan dispositivos inscritos en Intune, como dispositivos dedicados de Android Enterprise (AE) y que se ejecutan en modo de pantalla completa con varias aplicaciones. Para obtener más información, consulte [Configuración de la aplicación Managed Home Screen de Microsoft para Android Enterprise](app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates----3902931---"></a>Actualizaciones del Portal de empresa de iOS <!-- 3902931 -->
El nombre de la empresa reemplazará el texto "i.manage.microsoft.com" actual en los mensajes de administración de aplicaciones iOS. Por ejemplo, los usuarios verán el nombre de la empresa en lugar de "i.manage.microsoft.com" cuando intenten instalar una aplicación iOS desde el portal de empresa o cuando permitan la administración de la aplicación. Esto se implantará para todos los clientes en los próximos días.

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="manage-filevault-for-macos-------3858502--4557986--1210104----"></a>Administración de FileVault para macOS   <!--  3858502 + 4557986 + 1210104  -->
Puede usar Intune para [administrar el cifrado de claves de FileVault para dispositivos macOS](encrypt-devices.md). Para cifrar los dispositivos, debe usar un perfil de configuración de dispositivos de Endpoint Protection.

Nuestra compatibilidad con FileVault incluye el cifrado de dispositivos descifrados, la custodia de la clave de recuperación personal de un dispositivo, la rotación automática o manual de claves de cifrado personales y la recuperación de clave para sus dispositivos corporativos. Los usuarios finales también pueden utilizar el sitio web del Portal de empresa para obtener la clave de recuperación personal para sus dispositivos cifrados. 

También hemos expandido el informe de cifrado para incluir [información sobre FileVault](encryption-monitor.md) con información para BitLocker, de modo que puede ver todos los detalles del cifrado del dispositivo en un solo lugar. 

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>El restablecimiento de Windows Autopilot quita el usuario primario del dispositivo <!-- 4156123 -->
Al usarse el restablecimiento de Autopilot en un dispositivo, se quitará el usuario primario del dispositivo. El próximo usuario que inicie sesión tras el restablecimiento se establecerá como usuario primario. Esta característica se implantará para todos los clientes en los próximos días.

## <a name="week-of-july-8-2019"></a>Semana del 8 de julio de 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Nueva configuración de Office, Windows y OneDrive en las plantillas administrativas de Windows 10 <!-- 3510695 -->

Puede crear plantillas administrativas en Intune que imiten la administración de directivas de grupo locales (**Administración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y posterior** para la plataforma > **Plantilla administrativa** para el tipo de perfil).

En esta actualización se incluyen más opciones de configuración de Office, Windows y OneDrive que pueden agregar a sus plantillas. Con esta nueva configuración, ahora puede configurar más de 2500 opciones totalmente basadas en la nube.

Para obtener más información sobre esta característica, consulte [Usar plantillas de Windows 10 para configurar opciones de directiva de grupo en Intune](administrative-templates-windows.md).

Se aplica a: Windows 10 y versiones posteriores

## <a name="week-of-july-1-2019"></a>Semana del 1 de julio de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="aad-and-app-on-android-enterprise-devices----3574267---"></a>AAD y APP en los dispositivos Android Enterprise <!-- 3574267 -->
Ahora, al incorporar dispositivos Android Enterprise totalmente administrados, los usuarios se registrarán en Azure Active Directory (AAD) durante la configuración inicial de su nuevo dispositivo o el restablecimiento de fábrica del dispositivo. Anteriormente, en el caso de un dispositivo totalmente administrado, una vez completada la configuración, el usuario tenía que iniciar manualmente la aplicación de Microsoft Intune para iniciar el registro de AAD. Ahora, cuando el usuario tiene acceso a la página principal del dispositivo tras la configuración inicial, el dispositivo se inscribe y registra.

Además de las actualizaciones de AAD, las directivas de protección de aplicaciones (APP) de Intune se admiten ahora en dispositivos Android Enterprise totalmente administrados. Esta funcionalidad estará disponible a medida que la implementemos. Para obtener más información, consulte [Incorporación de aplicaciones de Google Play administrado a dispositivos Android Enterprise con Intune](apps-add-android-for-work.md).

## <a name="week-of-june-24-2019"></a>Semana del 24 de junio de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Configuración del explorador que se puede vincular a datos organizativos <!-- 3145939 -->
Ahora, las directivas de protección de aplicaciones (APP) de Intune en dispositivos iOS y Android permiten transferir vínculos web Org a un explorador determinado más allá de Intune Managed Browser o Microsoft Edge.  Consulte [¿Qué son las directivas de protección de aplicaciones?](app-protection-policy.md) para obtener más información sobre APP.

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>En la página Todas las aplicaciones se identifican las aplicaciones de Microsoft Store para Empresas en línea o sin conexión<!--4089647 -->
En la página **Todas las aplicaciones** ahora se incluye el etiquetado para identificar las aplicaciones de Microsoft Store para Empresas (MSFB) como aplicaciones en línea o sin conexión. Ahora, en cada aplicación MSFB se incluye un sufijo para **En línea** o **Sin conexión**. En la página de detalles de la aplicación también se incluye información sobre **Tipo de licencia** y **Supports device context installation** (Admite la instalación de contexto de dispositivo) (solo aplicaciones con licencia sin conexión).

#### <a name="company-portal-app-on-windows-shared-devices---4393553---"></a>Aplicación del Portal de empresa en los dispositivos compartidos de Windows <!--4393553 -->
Ahora, los usuarios pueden tener acceso a la aplicación del Portal de empresa en los dispositivos compartidos de Windows. Los usuarios finales verán una etiqueta **Compartida** en el icono de dispositivo. Esto se aplica a la versión 10.3.45609.0 y posteriores de la aplicación del Portal de empresa de Windows.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>Ver todas las aplicaciones instaladas desde la página web del Portal de empresa <!-- 4224326 -->
La nueva página **Aplicaciones instaladas** del sitio web del Portal de empresa muestra todas las aplicaciones administradas (requeridas y disponibles) que están instaladas en los dispositivos de un usuario. Además del tipo de asignación, los usuarios pueden ver el editor de la aplicación, la fecha de publicación y el estado de instalación actual. Si todavía no hay ninguna aplicación requerida o disponible para los usuarios, estos verán un mensaje en el que se explica que no hay ninguna aplicación de la empresa instalada. Para ver la página nueva en la Web, vaya al [sitio web del Portal de empresa](https://portal.manage.microsoft.com) y haga clic en **Aplicaciones instaladas**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>La vista nueva permite que los usuarios de las aplicaciones vean todas las aplicaciones administradas instaladas en el dispositivo <!-- 2352913 -->  
La aplicación Portal de empresa para Windows ahora muestra todas las aplicaciones administradas (tanto las requeridas como las disponibles) que están instaladas en el dispositivo de un usuario. Los usuarios también pueden ver las instalaciones de aplicaciones intentadas y pendientes, además de sus estados actuales. Si todavía no hay ninguna aplicación requerida o disponible para los usuarios, estos verán un mensaje en el que se explica que no hay ninguna aplicación de la empresa instalada. Para ver la vista nueva, vaya al panel de navegación del Portal de empresa y seleccione **Aplicaciones** > **Aplicaciones instaladas**.    

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Configuración de las extensiones de kernel en dispositivos macOS <!-- 2043024 -->
En dispositivos macOS, puede crear un perfil de configuración de dispositivos (**Configuración de dispositivo** > **Perfiles** > **Crear perfil** > elija **macOS** como plataforma). Esta actualización incluye un nuevo grupo de opciones de configuración que permite configurar y usar las extensiones de kernel en los dispositivos. Puede agregar extensiones específicas o permitir todas las extensiones de un asociado o desarrollador específico.

Para obtener más información sobre esta característica, consulte los artículos sobre [información general de las extensiones de kernel](kernel-extensions-overview-macos.md) y la [configuración de las extensiones de kernel](kernel-extensions-settings-macos.md).

Se aplica a: macOS 10.13.2 y versiones posteriores

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002---"></a>La opción Permitir solo aplicaciones de la Tienda para dispositivos Windows 10 incluye más opciones de configuración <!-- 2697002 -->
Al crear un perfil de restricciones de dispositivos para dispositivos Windows, se puede usar la opción **Permitir solo aplicaciones de la Tienda** de modo que los usuarios solo instalen aplicaciones de la Tienda Windows (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **Restricciones de dispositivos** para tipo de perfil). En esta actualización, este valor se amplía para admitir más opciones. 

Para ver la nueva configuración, vaya al artículo sobre la [configuración de dispositivos con Windows 10 y versiones posteriores para permitir o restringir características](device-restrictions-windows-10.md#app-store).

Se aplica a: Windows 10 y versiones posteriores

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Implementación de varios perfiles de dispositivo de extensiones de movilidad de Zebra en un dispositivo, el mismo grupo de usuarios o el mismo grupo de dispositivos <!-- 4089955 -->
En Intune, puede usar extensiones de movilidad (MX) de Zebra en un perfil de configuración de dispositivo para personalizar la configuración de dispositivos Zebra que no se integran en Intune. Actualmente, puede implementar un perfil en un único dispositivo. En esta actualización, puede implementar varios perfiles en:
- Mismo grupo de usuarios
- Mismo grupo de dispositivos
- Dispositivo único

En [Usar y administrar dispositivos Zebra con extensiones de movilidad de Zebra en Microsoft Intune](android-zebra-mx-overview.md) se muestra cómo usar MX en Intune.

Se aplica a: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Algunas opciones de configuración de pantalla completa en dispositivos iOS se establecen mediante "Bloquear", en sustitución de "Permitir" <!-- 4404075  -->
Al crear un perfil de restricciones de dispositivos en dispositivos iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **Pantalla completa**), se establecen el **Bloqueo automático**, el **Cambio de timbre**, la **Rotación de pantalla**, el **Botón de suspensión de pantalla** y los **Botones de volumen**. 

En esta actualización, los valores son **Bloquear** (bloquea la característica) o **Sin configurar** (permite la característica). Para ver la configuración, vaya a [Configuración de dispositivos iOS para permitir o restringir características ](device-restrictions-ios.md#kiosk-supervised-only). 

Se aplica a iOS.

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704---"></a>Uso de Face ID para la autenticación de contraseña en dispositivos iOS <!-- 4490704 -->
Al crear un perfil de restricciones de dispositivos para dispositivos iOS, puede usar una huella digital para una contraseña. En esta actualización, la configuración de contraseña de huella digital también permite el reconocimiento facial (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para la plataforma > **Restricciones de dispositivos** para el tipo de perfil > **Contraseña**). Como resultado, han cambiado las opciones de configuración siguientes:

- **Desbloqueo con huella digital** es ahora **Desbloqueo de Touch ID y Face ID**.
- **Modificación de huella digital (solo con supervisión)** es ahora **Modificación de Touch ID y Face ID (solo con supervisión)** .

Face ID está disponible en iOS 11.0 y versiones posteriores. Para ver la configuración, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](device-restrictions-ios.md#password).

Se aplica a iOS.

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region----4593948---"></a>La restricción de características de juegos y aplicaciones de la tienda en dispositivos iOS depende ahora de la región de clasificación <!-- 4593948 -->
En dispositivos iOS, puede permitir o restringir características relacionadas con los juegos, la tienda de aplicaciones y la visualización de documentos (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **App Store, presentación de documentos, juegos**). También puede elegir la región de clasificación, por ejemplo, Estados Unidos. 

En esta actualización, la característica **Aplicaciones** pasa a ser un elemento secundario de **Región de clasificación** y a depender de **Región de clasificación**. Para ver la configuración, vaya a [Configuración de dispositivos iOS para permitir o restringir características mediante Intune](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Se aplica a iOS.

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join----4809146--"></a>Compatibilidad de Windows Autopilot con Unión a Azure AD híbrido <!-- 4809146-->
Ahora, Windows Autopilot para los dispositivos existentes admite Unión a Azure AD híbrido (además de la compatibilidad con Unión a Azure AD existente). Se aplica a dispositivos con la versión 1809 de Windows 10 y posteriores. Para obtener más información, consulte [Windows Autopilot para dispositivos existentes](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).



### <a name="device-management"></a>Administración de dispositivos

#### <a name="see-the-security-patch-level-for-android-devices----4461911---"></a>Consulta del nivel de revisión de seguridad para dispositivos Android <!-- 4461911 -->
Ahora puede consultar el nivel de revisión de seguridad para dispositivos Android. Para ello, seleccione **Intune** > **Dispositivos** > **Todos los dispositivos** > seleccione un dispositivo > **Hardware**.
El nivel de revisión se muestra en la sección **Sistema operativo**.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Asignación de etiquetas de ámbito a todos los dispositivos administrados de un grupo de seguridad <!-- 3173810 -->
Ahora puede asignar etiquetas de ámbito a un grupo de seguridad y todos los dispositivos del grupo de seguridad también se asociarán a esas etiquetas de ámbito. La etiqueta de ámbito también se asigna a todos los dispositivos de estos grupos. Las etiquetas de ámbito establecidas con esta característica sobrescriben a las establecidas con el flujo de etiquetas de ámbito de dispositivo actual. Para obtener más información, consulte el artículo sobre el [uso de RBAC y las etiquetas de ámbito para TI distribuida](scope-tags.md).

### <a name="device-security"></a>Seguridad de dispositivos

#### <a name="use-keyword-search-with-security-baselines-------"></a>Uso de la búsqueda de palabras clave con Líneas de base de seguridad <!--  -->
Al crear o editar [perfiles de línea de base de seguridad](security-baselines.md#create-the-profile), puede especificar las palabras clave en la nueva barra de *búsqueda* para filtrar los grupos disponibles de opciones de configuración a aquellos que incluyen sus criterios de búsqueda. 

#### <a name="the-security-baselines-feature-is-now-generally-available-----3785395---"></a>La característica Líneas de base de seguridad ya está disponible con carácter general  <!-- 3785395 -->
La característica **Líneas de base de seguridad** está fuera de la versión preliminar y ya está disponible con carácter general (GA).  Esto significa que la característica está lista para usarse en producción. Sin embargo, las plantillas de línea de base individuales pueden permanecer en versión preliminar y se evalúan y publican con carácter general según su propia programación.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available------3794072-4217151--3534649---"></a>La plantilla Línea de base de seguridad MDM ya está disponible con carácter general   <!-- 3794072, 4217151,  3534649 -->
La plantilla Línea de base de seguridad MDM se ha sacado de la versión preliminar y ya está disponible con carácter general (GA). La plantilla con disponibilidad general se identifica como **Línea de base de seguridad MDM de mayo de 2019**.  Se trata de una nueva plantilla y no de una actualización de la versión preliminar.  Como nueva plantilla, deberá revisar la [configuración que contiene](security-baseline-settings-windows.md) y, a continuación, crear nuevos perfiles para implementar la plantilla en su dispositivo. Otras plantillas de línea de base de seguridad pueden permanecer en versión preliminar. Para ver una lista de líneas de base disponibles, consulte [Líneas de base de seguridad disponibles](security-baselines.md#available-security-baselines).  

Además de ser una nueva plantilla, *Línea de base de seguridad MDM de mayo de 2019* incluye las dos opciones de configuración que hemos anunciado recientemente en nuestro artículo En desarrollo:  
- Above Lock (Por encima de la pantalla de bloqueo): la voz activa las aplicaciones de una pantalla bloqueada  
- DeviceGuard: use la seguridad basada en la virtualización (VBS) la próxima vez que reinicie los dispositivos.  

*Línea de base de seguridad MDM de mayo de 2019* también incluye la incorporación de varias opciones de configuración nuevas, la eliminación de otras y una revisión del valor predeterminado de una configuración. Para ver una lista detallada de los cambios realizados de la versión preliminar a la disponibilidad general, consulte los **cambios en la nueva plantilla**.

#### <a name="security-baseline-versioning-----3194322---"></a>Control de versiones de líneas de base de seguridad  <!-- 3194322 -->
Líneas de base de seguridad para el control de versiones del soporte técnico de Intune. Con este soporte técnico, a medida que se publican nuevas versiones de cada línea de base de seguridad, puede actualizar sus perfiles de línea de base de seguridad para usar la versión de línea de base más reciente sin tener que volver a crear e implementar una nueva línea de base desde cero. Además, en la consola de Intune puede ver información sobre cada una de las líneas de base, como, por ejemplo, el número de perfiles individuales que tiene y que usan la línea de base, cuántas de las diferentes versiones de línea de base usan sus perfiles y de qué fecha data la versión más reciente de una línea de base de seguridad específica.  Para obtener más información, consulte **Líneas de base de seguridad**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved-----4501151---"></a>Se ha movido la opción Utilice las claves de seguridad para el inicio de sesión  <!-- 4501151 -->
La opción de configuración del dispositivo para la protección de identidad llamada **Utilice las claves de seguridad para el inicio de sesión** ya no se encuentra como configuración secundaria de *Configurar Windows Hello para empresas*. Ahora se trata de una opción de nivel superior que está siempre disponible, incluso si no habilita el uso de Windows Hello para empresas. Para obtener más información, consulte [Protección de identidad](identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="new-permissions-for-assigned-group-admins------4504437-----"></a>Nuevos permisos para administradores de grupos asignados   <!-- 4504437   -->
Ahora, el rol de administrador de la escuela integrado de Intune tiene permisos de creación, lectura, actualización y eliminación (CRUD) para Aplicaciones administradas. Esta actualización significa que si se le asigna como administrador de grupos en Intune for Education, ahora puede crear, ver, actualizar y eliminar el certificado push MDM de iOS, los tokens de servidor de MDM de iOS y los tokens de VPP de iOS, junto con [todos los permisos existentes que tenga](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Para tomar alguna de estas medidas, vaya a **Configuración de inquilinos** > **Administración de dispositivos iOS**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials----4655885---"></a>Las aplicaciones pueden usar Graph API para llamar a operaciones de lectura sin credenciales de usuario <!-- 4655885 -->
Las aplicaciones pueden llamar a operaciones de lectura de Graph API de Intune con la identidad de la aplicación y sin credenciales de usuario. Para obtener más información sobre cómo obtener acceso a Microsoft Graph API para Intune, consulte [Trabajar con Intune en Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps----4392555---"></a>Aplicación de etiquetas de ámbito a las aplicaciones de Microsoft Store para Empresas <!-- 4392555 -->
Ahora puede aplicar etiquetas de ámbito a las aplicaciones de Microsoft Store para Empresas. Para obtener más información sobre las etiquetas de ámbito, consulte [Uso del control de acceso basado en roles y de las etiquetas de ámbito para la TI distribuida](scope-tags.md).

## <a name="week-of-june-17-2019"></a>Semana del 17 de junio de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="new-features-in-microsoft-intune-app"></a>Características nuevas de la aplicación Microsoft Intune
Agregamos características nuevas a la aplicación Microsoft Intune (versión preliminar) para Android. Los usuarios de dispositivos Android totalmente administrados ahora pueden:  

* Ver y administrar los dispositivos inscritos mediante la aplicación Portal de empresa de Intune o Microsoft Intune.    
* Ponerse en contacto con su organización para obtener soporte técnico.    
* Enviar comentarios a Microsoft.    
* Consultar los términos y condiciones, si la organización los estableció.    

## <a name="week-of-june-10-2019"></a>Semana del 10 de junio de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>Aplicaciones de ejemplo nuevas que muestran la integración del SDK de Intune disponible en GitHub <!-- 2653471 -->
La cuenta de GitHub msintuneappsdk agregó aplicaciones de ejemplo nuevas para iOS (Swift), Android, Xamarin.iOS, Xamarin Forms y Xamarin.Android. Estas aplicaciones están pensadas para complementar la documentación existente y ofrecen demostraciones sobre cómo integrar el SDK de la aplicación Intune en sus propias aplicaciones móviles. Si es desarrollador de aplicaciones y necesita más orientación sobre el SDK de Intune, consulte estos ejemplos vinculados:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App): una aplicación de mensajería instantánea nativa de iOS (Swift) que usa la Biblioteca de autenticación de Azure Active Directory (ADAL) para la autenticación intermediada.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App): una aplicación de listas de tareas pendientes nativa de Android que usa ADAL para la autenticación intermediada.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps): una aplicación de listas de tareas pendientes de Xamarin.Android que usa ADAL para la autenticación intermediada. Este repositorio también tiene la aplicación Xamarin.Forms.
- [Aplicación de ejemplo de Xamarin.iOS](https://github.com/msintuneappsdk/sample-intune-xamarin-ios): una aplicación de ejemplo esencial de Xamarin.iOS.

## <a name="week-of-may-27-2019"></a>Semana del 27 de mayo de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Informes de aplicaciones potencialmente peligrosas en dispositivos Android <!-- 4223162 -->
Intune ahora proporciona más datos sobre informes de aplicaciones potencialmente peligrosas en dispositivos Android. 

## <a name="week-of-may-20-2019"></a>Semana del 20 de mayo de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="windows-company-portal-app----3316993---"></a>Aplicación Portal de empresa de Windows <!-- 3316993 -->
La aplicación Portal de empresa de Windows ahora tiene una nueva página denominada **Dispositivos**. La página **Dispositivos** ahora mostrará a los usuarios finales los dispositivos inscritos. Los usuarios verán este cambio en Portal de empresa cuando usen la versión 10.3.4291.0 o una posterior. Para obtener información sobre cómo configurar Portal de empresa, vea [Configuración de la aplicación Portal de empresa de Microsoft Intune](company-portal-app.md).

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Nombre del atributo OrderID del dispositivo de Autopilot cambiado a Etiqueta de grupo <!-- 4659453 -->

Para hacer que sea más intuitivo, el nombre del atributo **OrderID** en los dispositivos de Autopilot se ha cambiado a **Etiqueta de grupo**. Al usar archivos CSV para cargar información de dispositivos de Autopilot, debe usar Etiqueta de grupo como encabezado de columna, en lugar de OrderID.  

## <a name="week-of-may-13-2019"></a>Semana del 13 de mayo de 2019 

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359----"></a>Método de autenticación de actualizaciones de directivas de Intune e instalación de aplicaciones de Portal de empresa  <!-- 1927359  -->
En los dispositivos ya inscritos mediante el Asistente de configuración a través de uno de los métodos de inscripción de dispositivos corporativos de Apple, Intune ya no será compatible con el Portal de empresa cuando los usuarios finales de la tienda de aplicaciones lo instalen manualmente. Este cambio solo es pertinente cuando se realiza la autenticación con el Asistente de configuración de Apple durante la inscripción. Este cambio solo afecta a los dispositivos iOS inscritos a través de:  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Programa de inscripción de dispositivos (DEP) de Apple

Si los usuarios instalan la aplicación Portal de empresa desde la tienda de aplicaciones y luego intentan inscribir estos dispositivos a través de ella, recibirán un error. Se espera que estos dispositivos solo usen la aplicación Portal de empresa cuando Intune lo inserta, automáticamente, durante la inscripción. Se actualizarán los perfiles de inscripción de Intune en Azure Portal para que pueda especificar cómo los dispositivos se autentican y si reciben la aplicación Portal de empresa. Si quiere que los usuarios de dispositivos DEP tengan la aplicación Portal de empresa, deberá especificar sus preferencias en un perfil de inscripción. 

Además, se va a quitar la pantalla **Identificar el dispositivo** de la aplicación Portal de empresa de iOS. Por lo tanto, los administradores que quieren habilitar el acceso condicional o implementar aplicaciones de la empresa deben actualizar el perfil de inscripción de DEP. Este requisito solo se aplica si la inscripción de DEP se autentica con el Asistente para la configuración. En ese caso, debe insertar la aplicación Portal de empresa en el dispositivo. Para ello, elija **Intune** > **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > elija un token > **Perfiles** > elija un perfil > **Propiedades** > establezca **Instalar Portal de empresa** en **Sí**.

Para instalar la aplicación Portal de empresa en dispositivos DEP ya inscritos, deberá ir a Intune > Aplicaciones cliente e insertarla como una aplicación administrada con directivas de configuración de aplicación. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>Configurar cómo los usuarios finales actualizan una aplicación de línea de negocio (LOB) con una directiva de protección de aplicaciones <!-- 3568384 -->
Ahora puede configurar dónde los usuarios finales pueden obtener una versión actualizada de una aplicación de línea de negocio (LOB). Los usuarios finales verán esta característica en el cuadro de diálogo de inicio condicional **Versión mínima de la aplicación**, que le pedirá a los usuarios finales que actualicen a una versión mínima de la aplicación de LOB. Debe proporcionar estos detalles de actualización como parte de la directiva de protección de aplicaciones (APP) de LOB. Esta característica está disponible en iOS y en Android. En iOS, esta característica requiere que la aplicación esté integrada (o encapsulada con la herramienta de encapsulado) con el SDK de Intune para iOS v. 10.0.7 o superior. En Android, esta característica requeriría la versión más reciente de la aplicación Portal de empresa. Para configurar cómo un usuario final actualiza una aplicación de LOB, la aplicación necesita que se le envíe una directiva de configuración de aplicación administrada con la clave `com.microsoft.intune.myappstore`. El valor enviado definirá desde qué tienda descargará la aplicación el usuario final. Si la aplicación se implementa a través de Portal de empresa, el valor debe ser `CompanyPortal`. En el caso de cualquier otra tienda, debe escribir una dirección URL completa.

#### <a name="intune-management-extension-powershell-scripts-----3734186----"></a>Scripts de PowerShell de extensión de administración de Intune  <!-- 3734186  -->
Puede configurar los scripts de PowerShell para que se ejecuten con los privilegios de administración del usuario en el dispositivo. Para más información, consulte [Uso de scripts de PowerShell para dispositivos Windows 10 en Intune](intune-management-extension.md) y [Administración de aplicaciones Win32](apps-win32-app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Administración de aplicaciones de Android Enterprise <!-- 4459905 -->
Para facilitar a los administradores de TI la configuración y el uso de la administración de Android Enterprise, Intune agregará automáticamente cuatro aplicaciones comunes relacionadas con Android Enterprise a la consola de administración de Intune. Las cuatro aplicaciones de Android Enterprise son las siguientes:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : se usa para escenarios totalmente administrados de Android Enterprise.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : ayuda a iniciar sesión en las cuentas si se usa la verificación de dos fases.
- **[Portal de empresa de Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : se usa para las directivas de protección de aplicación y escenarios de perfil de trabajo de Android Enterprise.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise): se usa para los escenarios de pantalla completa o dedicados de Android Enterprise.

Anteriormente, los administradores de TI tenían que buscar y aprobar manualmente estas aplicaciones en la [Tienda de Google Play administrada](https://play.google.com/store/apps) como parte de la configuración. Este cambio elimina los pasos que antes eran manuales para facilitar y agilizar el uso de la administración de Android Enterprise por parte de los clientes.

Los administradores verán que estas cuatro aplicaciones se agregan automáticamente a la lista de aplicaciones de Intune en el momento en que conecten por primera vez a su inquilino de Intune con Google Play administrado. Para más información, consulte [Conexión de una cuenta de Intune a una cuenta de Google Play administrado](connect-intune-android-enterprise.md). Para los inquilinos que ya han conectado a su inquilino o que ya utilizan Android Enterprise, no hay nada que los administradores tengan que hacer. Estas cuatro aplicaciones aparecerán automáticamente dentro de los siete días siguientes a la finalización de la implementación del servicio en mayo de 2019.

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>Conector de certificados PFX actualizado para Microsoft Intune  <!-- 1533038 -->
Hemos publicado una actualización del [Conector de certificado PFX para Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) que resuelve un problema por el que los certificados PFX existentes se siguen reprocesando, lo que provoca que el conector deje de procesar nuevas solicitudes.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Tareas de seguridad de Intune para ATP de Defender (en versión preliminar pública)     <!-- 3208597 -->
En la versión preliminar pública, puede usar Intune para administrar las [tareas de seguridad para Protección contra amenazas avanzada (ATP) de Microsoft Defender](atp-manage-vulnerabilities.md). Esta integración con ATP agrega un enfoque basado en riesgos para detectar vulnerabilidades y errores de configuración de puntos de conexión, establecer su prioridad y corregirlos, a la vez que reduce el tiempo entre la detección y la mitigación.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Buscar un conjunto de chips TPM en una directiva de cumplimiento de dispositivos Windows 10 <!-- 3617671   idstaged-->
Muchos dispositivos Windows 10 y posteriores tienen conjuntos de chips del Módulo de plataforma segura (TPM). Esta actualización incluye una nueva configuración de cumplimiento que comprueba la versión del chip TPM en el dispositivo. 

[La configuración de directivas de cumplimiento de Windows 10 y versiones posteriores](compliance-policy-create-windows.md#device-security) describe esta configuración.

Se aplica a: Windows 10 y versiones posteriores

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Impedir que los usuarios finales modifiquen su punto de acceso personal y deshabilitar el registro del servidor Siri en dispositivos iOS <!-- 4097904   -->  
Crear un perfil de restricciones de dispositivo en el dispositivo iOS (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para la plataforma y **Restricciones de dispositivo** para el tipo de perfil). Esta actualización incluye nuevas opciones que puede configurar:

- **Aplicaciones integradas**: registro del servidor para los comandos de Siri
- **Inalámbrica**: modificación por el usuario del punto de acceso personal (solo con supervisión)

Para ver esta configuración, vaya a la [configuración de aplicaciones integradas para iOS](device-restrictions-ios.md#built-in-apps) y [configuración inalámbrica para iOS](device-restrictions-ios.md#wireless).

Se aplica a iOS 12.2 y versiones más recientes.

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Nueva configuración de restricción de dispositivos de aplicaciones en el aula para dispositivos macOS <!-- 4097905   --> 
Puede crear un perfil de configuración de dispositivos para dispositivos MacOS (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **macOS** como plataforma >**Restricciones del dispositivo** para tipo de perfil). Esta actualización incluye una nueva configuración de aplicaciones en el aula, la opción para bloquear capturas de pantalla y la opción para deshabilitar la Fototeca de iCloud.

Para ver la configuración actual, vaya a [Configuración de dispositivos macOS para permitir o restringir características mediante Intune](device-restrictions-macos.md).

Se aplica a: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>Se cambia el nombre de la configuración Contraseña para acceder a la tienda de aplicaciones de iOS<!-- 4557891  -->
El nombre de la configuración **Contraseña para acceder a la tienda de aplicaciones** se cambia a **Require iTunes Store password for all purchases** (Requerir contraseña de iTunes Store para todas las compras) (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > **iOS** para la plataforma > **Restricciones de dispositivos** para el tipo de perfil > **Tienda de aplicaciones, presentación de documentos y juegos**).

Para ver la configuración disponible, vaya a [Tienda de aplicaciones, presentación de documentos, juegos de iOS](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Se aplica a iOS.

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Línea de base de Protección contra amenazas avanzada de Microsoft Defender (versión preliminar)  <!--  3754134 -->
Agregamos una versión preliminar de línea de base de seguridad para la configuración [Protección contra amenazas avanzada de Microsoft Defender](security-baseline-settings-defender-atp.md). Esta línea de base está disponible cuando el entorno cumple con los requisitos previos para usar [Protección contra amenazas avanzada de Windows Defender](advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>La página Estado de inscripción (ESP) de Windows ya está disponible con carácter general <!-- 3605348 -->
La página Estado de inscripción dejó de estar en versión preliminar. Para más información, consulte [Configurar una página de estado de inscripción](windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Actualización de la interfaz de usuario de Intune: creación de un perfil de inscripción de Autopilot  <!-- 4593669 -->
La interfaz de usuario para crear un perfil de inscripción de Autopilot se actualizó para alinearla con los estilos de interfaz de usuario de Azure. Para obtener más información, consulte cómo [crear un perfil de inscripción de Autopilot](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile). Más adelante, se actualizarán más escenarios de Intune a este nuevo estilo de interfaz de usuario.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>Habilitar Restablecimiento de Autopilot para todos los dispositivos Windows <!-- 4225665 -->
Restablecimiento de Autopilot ahora funciona para todos los dispositivos Windows, incluso para los que no están configurados para usar la página Estado de inscripción. Si no se configuró una página de estado de inscripción para el dispositivo durante la inscripción de dispositivo inicial, el dispositivo irá directamente al escritorio después de iniciar sesión. Puede tardar hasta ocho horas en sincronizar y aparecer como compatible en Intune. Para más información, consulte el artículo sobre cómo [restablecer dispositivos con Restablecimiento de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>No se requiere un formato IMEI exacto al buscar en todos los dispositivos <!--30407680 -->
No será necesario que incluya espacios en los números IMEI cuando busca en **Todos los dispositivos**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Reflejo de la eliminación de un dispositivo del portal de Apple en el portal de Intune <!--2489996 -->
Si se elimina un dispositivo de los portales del Programa de inscripción de dispositivos de Apple o de Apple Business Manager, el dispositivo se eliminará automáticamente de Intune durante la siguiente sincronización.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>La página de estado de inscripción ahora realiza un seguimiento de las aplicaciones de Win32 <!-- 2714451 -->
Esto solo se aplica a dispositivos que ejecutan Windows 10 versión 1903 y posteriores. Para más información, consulte [Configurar una página de estado de inscripción](windows-enrollment-status.md).

### <a name="device-management"></a>Administración de dispositivos

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Restablecimiento y borrado de dispositivos de forma masiva mediante Graph API <!-- 3295288 -->
Ahora podrá restablecer y borrar hasta 100 dispositivos de forma masiva mediante Graph API.


### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>El informe de cifrado dejó de estar en versión preliminar pública   <!-- 4587546      -->
El [informe sobre BitLocker y el cifrado de dispositivo](encryption-monitor.md) está disponible con carácter general y ya no forma parte de la versión preliminar pública. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>Configuración de biometría y firma de Outlook para dispositivos iOS y Android <!-- 4050557 -->
Ahora puede especificar si la firma predeterminada está habilitada en Outlook en dispositivos iOS y Android. Además, puede elegir permitir que los usuarios cambien la configuración de biometría en Outlook en iOS.

## <a name="week-of-may-6-2019"></a>Semana del 6 de mayo de 2019 

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>Compatibilidad del control de acceso de red (NAC) con F5 Access para dispositivos iOS <!-- 4500808 -->

F5 ha publicado una actualización para BIG-IP 13 que permite la funcionalidad NAC para F5 Access para iOS en Intune. Para usar esta característica,:

- Actualice BIG-IP a 13.1.1.5. No se admite BIG-IP 14.
- Integre BIG-IP con Intune para NAC. Los pasos se describen en [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html) (Información general: Configuración de APM para comprobaciones de posición del dispositivo con sistemas de administración de puntos de conexión).
- Active la opción **Habilitar el control de acceso a la red (NAC)** del perfil de VPN en Intune.

Para ver las opciones disponibles, vaya a [Configuración de VPN en dispositivos iOS](vpn-settings-ios.md).

Se aplica a iOS.

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>Conector de certificados PFX actualizado para Microsoft Intune <!-- doc-vso 1521237  -->  
Se ha publicado una actualización para el [Conector de certificados PFX para Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) que reduce el intervalo de sondeo de 5 minutos a 30 segundos.

## <a name="week-of-april-22-2019"></a>Semana del 22 de abril de 2019

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Usar el Administrador de cumplimiento para crear evaluaciones para Microsoft Intune<!-- 4404750 -->

El [Administrador de cumplimiento](https://servicetrust.microsoft.com/ComplianceManager) (abre otro sitio de Microsoft) es una herramienta de evaluación de riesgos según el flujo de trabajo que se encuentra en el Portal de confianza de servicios de Microsoft. Permite asignar y comprobar las actividades de cumplimiento normativo de la organización relacionadas con los servicios de Microsoft, y realizar un seguimiento de dichas actividades. Puede crear su propia evaluación de cumplimiento con Office 365, Azure, Dynamics, Servicios profesionales e Intune. Intune tiene dos evaluaciones disponibles: FFIEC y RGPD.

Con el Administrador de cumplimiento es más fácil centrarse en las actividades, ya que divide los controles en controles administrados por Microsoft y controles administrados por la organización. Permite completar las evaluaciones y, después, exportarlas e imprimirlas.

El cumplimiento normativo del [Consejo federal de examen de instituciones financieras (FFIEC, del inglés Federal Financial Institutions Examination Council)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (abre otro sitio de Microsoft) es un conjunto de estándares para la banca electrónica emitido por el FFIEC. Es la evaluación para instituciones financieras más solicitada que se usa en Intune. Interpreta cómo Intune le permite cumplir las directrices de ciberseguridad del FFIEC relacionadas con cargas de trabajo en la nube pública. La evaluación del FFIEC de Intune es la segunda evaluación del FFIEC en el Administrador de cumplimiento.

En este ejemplo puede ver el desglose de los controles del FFIEC. Microsoft abarca 64 controles. El usuario se encarga de los 12 controles restantes.

![Vea un ejemplo de la evaluación de Intune para el FFIEC, incluidas las acciones de cliente y las acciones de Microsoft.](./media/intune-ffiec-assessment-status.png)

El [Reglamento general de protección de datos (RGPD)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (abre otro sitio de Microsoft) es una ley de la Unión Europea (UE) que permite proteger los derechos de los usuarios y sus datos. El RGPD es la evaluación más solicitada para cumplir con las normas de privacidad. 

En este ejemplo puede ver el desglose de los controles del RGPD. Microsoft abarca 49 controles. El usuario se encarga de los 66 controles restantes.

![Vea un ejemplo de la evaluación de Intune para el RGPD, incluidas las acciones de cliente y las acciones de Microsoft.](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>Semana del 15 de abril de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Cifrado de OpenSSL para las directivas de protección de aplicaciones Android <!-- 3747362 -->
Las directivas de protección de aplicaciones (APP) de Intune en dispositivos Android ahora usan una biblioteca de cifrado de OpenSSL que es compatible con FIPS 140-2. Para más información, vea la sección sobre [cifrado](app-protection-policy-settings-android.md#encryption) de [Configuración de directivas de protección de aplicaciones Android en Microsoft Intune](app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies----2617348----"></a>Habilitar dependencias de la aplicación Win32 <!-- 2617348  -->
Como administrador, puede exigir que otras aplicaciones se instalen como dependencias antes de instalar la aplicación Win32. En concreto, el dispositivo debe instalar las aplicaciones dependientes antes de que se instale la aplicación Win32. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar** para mostrar la hoja **Agregar aplicación**. Seleccione **Aplicación de Windows (Win32)** como **Tipo de aplicación**. Después de agregar la aplicación, puede seleccionar **Dependencias** para agregar las aplicaciones dependientes que se deben instalar antes de poder instalar la aplicación Win32. Para más información, vea [Intune independiente: administración de aplicaciones Win32](apps-win32-app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Información de instalación de la versión para aplicaciones de Microsoft Store para Empresas <!-- 3537391   -->
Los informes de instalación de aplicaciones incluyen información de la versión de la aplicación para aplicaciones de Microsoft Store para Empresas. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones**. Elija una **Aplicación de Microsoft Store para Empresas** y luego seleccione **Estado de instalación del dispositivo** en la sección **Supervisión**.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Adiciones a las reglas de requisitos de las aplicaciones Win32 <!-- 3676883   -->
Puede crear reglas de requisitos basadas en los scripts de PowerShell, los valores del Registro y la información del sistema de archivos. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. Después, seleccione **Aplicación de Windows (Win32)** como **Tipo de aplicación** en la hoja **Agregar aplicación**.  Seleccione **Requisitos** > **Agregar** para configurar más reglas de requisitos. Después, seleccione **Tipo de archivo**, **Registro** o **Script** como **Tipo de requisito**. Para más información, vea [Administración de aplicaciones Win32](apps-win32-app-management.md).

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Configurar las aplicaciones Win32 para instalarlas en dispositivos unidos a Azure AD inscritos en Intune <!-- 3695227  -->
Puede asignar las aplicaciones Win32 para instalarlas en dispositivos unidos a Azure AD inscritos en Intune. Para más información sobre las aplicaciones Win32 en Intune, vea [Administración de aplicaciones Win32](apps-win32-app-management.md).

#### <a name="device-overview-shows-primary-user---3794259----"></a>Usuario primario mostrado en Resumen del dispositivo <!--3794259  -->
La página Resumen del dispositivo mostrará el usuario primario, también denominado el usuario de afinidad de dispositivo de usuario (UDA). Para ver el usuario primario de un dispositivo, seleccione **Intune** > **Dispositivos** > **Todos los dispositivos** y elija un dispositivo. El usuario primario se muestra cerca de la parte superior de la página **Resumen**.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Otros informes de aplicaciones de Google Play administrado para dispositivos de perfil de trabajo de Android Enterprise <!-- 4105925  -->
Para aplicaciones de Google Play administrado implementadas en dispositivos de perfil de trabajo de Android Enterprise, puede ver el número de versión específica de la aplicación instalada en un dispositivo. Esto se aplica solo a las aplicaciones necesarias.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>Teclados de terceros de iOS <!-- 4111843   -->
La compatibilidad de la directiva de protección de aplicaciones (APP) de Intune con la configuración **Teclados de terceros** para iOS ya no se admite debido a un cambio de la plataforma iOS. No podrá configurar esta opción en la consola de administración de Intune y no se aplicará en el cliente en el SDK de aplicaciones de Intune.

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>Establecer configuración de inicio de sesión y opciones de reinicio de control en dispositivos macOS <!-- 1210083  -->
En dispositivos macOS, puede crear un perfil de configuración de dispositivos (**Configuración de dispositivos** > **Perfiles** > **Crear perfil** > elija **macOS** como plataforma > **Características del dispositivo** para tipo de perfil). Esta actualización incluye una nueva configuración de la ventana de inicio de sesión, como mostrar un encabezado personalizado, elegir cómo inician sesión los usuarios, mostrar u ocultar la configuración de energía y mucho más.

Para ver esta configuración, vaya a [macOS device feature settings](macos-device-features-settings.md) (Configuración de características de dispositivos macOS).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>Configurar Wi-Fi en Android Enterprise para dispositivos dedicados de propietario del dispositivo que se ejecutan en pantalla completa con varias aplicaciones <!--3041940  -->
Puede habilitar la configuración de propietario del dispositivo en Android Enterprise cuando se ejecuta como un dispositivo dedicado en pantalla completa con varias aplicaciones. En esta actualización, puede permitir que los usuarios configuren y se conecten a Wi-Fi (**Intune** > **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **Solo el propietario del dispositivo, Restricciones de dispositivo** para el tipo de perfil >  **Dispositivos dedicados** > **Pantalla completa**: **Varias aplicaciones** > **Configuración de Wi-Fi**). 

Para ver todos los valores que puede configurar, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características](device-restrictions-android-for-work.md).

Se aplica a: Dispositivos dedicados de Android Enterprise que se ejecutan en pantalla completa con varias aplicaciones


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>Configurar Bluetooth y emparejamiento en Android Enterprise para dispositivos dedicados de propietario del dispositivo que se ejecutan en pantalla completa con varias aplicaciones <!-- 3041941  -->
Puede habilitar la configuración de propietario del dispositivo en Android Enterprise cuando se ejecuta como un dispositivo dedicado en pantalla completa con varias aplicaciones. En esta actualización, puede permitir que los usuarios finales habiliten Bluetooth y emparejen sus dispositivos mediante Bluetooth (**Intune** > **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **Solo el propietario del dispositivo, Restricciones de dispositivo** para el tipo de perfil >  **Dispositivos dedicados** > **Pantalla completa**: **Varias aplicaciones** > **Configuración de Bluetooth**). 

Para ver todos los valores que puede configurar, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características](device-restrictions-android-for-work.md).

Se aplica a: Dispositivos dedicados de Android Enterprise que se ejecutan en pantalla completa con varias aplicaciones

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Crear y usar perfiles de configuración de dispositivos OEMConfig en Intune <!-- 3305883  -->
En esta actualización, Intune admite la configuración de dispositivos Android Enterprise con OEMConfig. En concreto, puede crear un perfil de configuración de dispositivo y aplicar la configuración a los dispositivos Android Enterprise mediante OEMConfig (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma).

Actualmente, la compatibilidad con fabricantes de equipos originales depende del fabricante. Si quiere una aplicación OEMConfig que no está disponible en la lista de aplicaciones OEMConfig, póngase en contacto con `IntuneOEMConfig@microsoft.com`.

Para más información sobre esta característica, vaya a [Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune](android-oem-configuration-overview.md) (Uso y administración de dispositivos Android Enterprise con OEMConfig en Microsoft Intune).

Se aplica a: Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Notificaciones de Windows Update  <!-- 3316758, 3316782  -->
Se han agregado dos valores de *Configuración de la experiencia de usuario* a las configuraciones de anillo de Windows Update que puede administrar desde la consola de Intune. Ahora puede:
- Bloquear o permitir que los usuarios [busquen actualizaciones de Windows](windows-update-settings.md).
- Administrar el [nivel de notificación de Windows Update](windows-update-settings.md) que los usuarios pueden ver.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Nueva configuración de restricción de dispositivos para Propietario del dispositivo en Android Enterprise <!-- 3574254  -->
En dispositivos Android Enterprise, puede crear un perfil de restricción de dispositivos para permitir o restringir características, establecer reglas de contraseña y mucho más (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > elija **Android Enterprise** para plataforma > **Solo el propietario del dispositivo > Restricciones de dispositivos** para el tipo de perfil). 

Esta actualización incluye nuevas opciones de contraseña, permite el acceso completo a las aplicaciones en Google Play Store para dispositivos totalmente administrados y mucho más. Para ver la lista actual de configuraciones, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características](device-restrictions-android-for-work.md). 

Se aplica a: Dispositivos totalmente administrados de Android Enterprise

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Buscar un conjunto de chips TPM en una directiva de cumplimiento de dispositivos Windows 10 <!-- 3617671 -->

El lanzamiento de esta característica se ha retrasado y está previsto que sea más adelante.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Cambios de la interfaz de usuario actualizada para el explorador Microsoft Edge en dispositivos con Windows 10 y versiones posteriores <!-- 3775833   -->
Cuando se crea un perfil de configuración de dispositivo, puede permitir o restringir las características de Microsoft Edge en dispositivos con Windows 10 y versiones posteriores (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para la plataforma > **Restricciones de dispositivos** para el tipo de perfil > **Explorador Microsoft Edge**). En esta actualización, la configuración de Microsoft Edge es más descriptiva y fácil de entender. 

Para ver estas características, vaya a [Configuración de restricción de dispositivos del explorador Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

Se aplica a: Windows 10 y versiones posteriores

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Compatibilidad ampliada para dispositivos totalmente administrados de Android Enterprise (versión preliminar)  <!--   3903241, 3903244, 3903246   -->
Aún en versión preliminar pública, hemos ampliado la compatibilidad de dispositivos totalmente administrados de Android Enterprise ([se anunció por primera vez en enero de 2019](whats-new.md#week-of-january-14-2019) para incluir lo siguiente: 

- En dispositivos totalmente administrados y dedicados, puede crear [directivas de cumplimiento](compliance-policy-create-android-for-work.md) para incluir las reglas de contraseña y requisitos del sistema operativo (**Cumplimiento del dispositivo** > **Directivas** > **Crear directiva** > **Android Enterprise** para plataforma > **Propietario del dispositivo** para tipo de perfil). 

  En dispositivos dedicados, el dispositivo puede aparecer como **No compatible**. El acceso condicional no está disponible en dispositivos dedicados. Asegúrese de completar las tareas o acciones para obtener dispositivos dedicados compatibles con las directivas asignadas.

- [Acceso condicional](conditional-access.md): las directivas de acceso condicional que se aplican a Android también se aplican a dispositivos totalmente administrados de Android Enterprise. Los usuarios ahora pueden registrar su dispositivo totalmente administrado en Azure Active Directory mediante la **aplicación Microsoft Intune**. Después, pueden ver y resolver los problemas de cumplimiento para acceder a recursos de la organización.

- Nueva aplicación de usuario final (aplicación Microsoft Intune): hay una nueva aplicación de usuario final para dispositivos Android totalmente administrados denominada **Microsoft Intune**. Esta nueva aplicación, ligera y moderna, ofrece funciones similares a las de la aplicación Portal de empresa, pero para dispositivos totalmente administrados. Para más información, vea la [aplicación Microsoft Intune en Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Para configurar dispositivos Android totalmente administrados, vaya a **Dispositivo administrado** > **Inscripción de Android** > **Corporate-owned, fully managed user devices** (Dispositivos de usuario totalmente administrados de propiedad corporativa). La compatibilidad con dispositivos Android totalmente administrados sigue en versión preliminar y algunas características de Intune podrían no ser totalmente funcionales.  

Para más información sobre esta versión preliminar, lea nuestro blog [Microsoft Intune - Versión preliminar 2 para dispositivos totalmente administrados de Android Enterprise](https://aka.ms/preview2_AE_fullymanaged).


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Configuración del perfil para omitir algunas pantallas durante el Asistente para configuración <!-- 2276470  -->
Cuando se crea un perfil de inscripción de macOS, se puede configurar para que omita cualquiera de las siguientes pantallas cuando un usuario realiza los pasos del Asistente para configuración:
- Aspecto
- Tono de visualización
- iCloudStorage: si crea un nuevo perfil o edita uno, las pantallas de omisión seleccionadas deben sincronizarse con el servidor MDM de Apple.  Los usuarios pueden emitir una sincronización manual de los dispositivos para que no haya ningún retraso en la recogida de los cambios de perfil.
Para más información, consulte el artículo [Inscripción automática de dispositivos macOS con el Programa de inscripción de dispositivos o Apple School Manager](device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Asignar nombres en masa a dispositivos al inscribir dispositivos iOS corporativos<!--3566569  -->
Al usar uno de los métodos de inscripción corporativa de Apple (DEP/ABN/ASM), puede establecer un formato de nombre de dispositivo para que asigne un nombre automáticamente a los dispositivos iOS entrantes. Puede especificar un formato que incluya el tipo de dispositivo y el número de serie en la plantilla. Para hacerlo, elija **Intune** > **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > **Seleccione un token** >**Crear perfil** > **Formato de nomenclatura de dispositivo**. Puede editar los perfiles existentes, pero el nombre se aplicará solamente a los dispositivos que acaba de sincronizar.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Actualizado el mensaje de tiempo de espera predeterminado en la página de estado de inscripción <!-- 3959331 -->
Hemos actualizado el mensaje de tiempo de espera predeterminado que se muestra a los usuarios cuando la página de estado de inscripción (ESP) supera el valor de tiempo de espera especificado en el perfil de ESP. El nuevo mensaje predeterminado es lo que los usuarios ven y les permite comprender las siguientes acciones que deben realizar con su implementación de ESP.  

### <a name="device-management"></a>Administración de dispositivos

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Retirar dispositivos no compatibles  <!-- 1827291   -->
Esta característica se ha retrasado y se incluirá en una versión futura.


### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Cambios de Intune Data Warehouse V1.0 reflejados hasta la versión beta <!-- 4403765 -->
Cuando V1.0 apareció por primera vez en agosto de 2018, difería en algunos aspectos importantes de la versión beta de API. En marzo de 2019 esos cambios se reflejan en la versión beta de la API. Si tiene informes importantes que usan la versión beta de API, se recomienda encarecidamente cambiar dichos informes a V1.0 para evitar cambios bruscos. Para más información, vea [Registro de cambios en la API Almacenamiento de datos de Intune](reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Supervisar el estado de las líneas bases de seguridad (versión preliminar) <!-- 3082047 --> 
Hemos agregado una [vista por categorías](security-baselines-monitor.md#per-category-view) para la supervisión de las líneas bases de seguridad. (Las líneas base de seguridad siguen en versión preliminar). La vista por categorías muestra cada categoría desde la línea base junto con el porcentaje de dispositivos que pertenecen a cada grupo de estado para esa categoría. Ahora puede ver cuántos dispositivos no coinciden con las categorías individuales, están mal configurados o no son aplicables.

### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Etiquetas de ámbito para los tokens del Programa de compras por volumen (VPP) de Apple <!--2371886  -->
Ahora puede agregar etiquetas de ámbito a los tokens de VPP de Apple. Solo los usuarios que tienen asignada la misma etiqueta de ámbito tendrán acceso al token de VPP de Apple con esa etiqueta. Las aplicaciones y libros electrónicos de VPP comprados con ese token heredan sus etiquetas de ámbito. Para más información sobre las etiquetas de ámbito, vea [Use RBAC and scope tags](scope-tags.md) (Usar RBAC y etiquetas de ámbito).







## <a name="week-of-april-1-2019"></a>Semana del 1 de abril de 2019

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Conectores de certificado actualizados  <!-- ICM 113304612 -->
Se han publicado actualizaciones para [Intune Certificate Connector y el conector de certificados PFX para Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors). Las nuevas versiones corrigen varios problemas conocidos.  

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Actualización de la experiencia de usuario para la aplicación Portal de empresa para iOS <!-- 2536024 -->
Se ha rediseñado la página principal de la aplicación Portal de empresa para dispositivos iOS. Con este cambio, la página principal seguirá mejor los patrones de la interfaz de usuario de iOS y ofrecerá una función de detección mejorada para aplicaciones y libros electrónicos.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Cambios en la inscripción del Portal de empresa para los usuarios de dispositivos iOS 12 <!--3448635 -->  
Se han actualizado los pasos y las pantallas de inscripción del Portal de empresa para iOS con el fin de ajustarlos a los cambios en la inscripción de MDM que se introdujeron en Apple iOS 12.2. En el nuevo flujo de trabajo, se pide a los usuarios que hagan esto:  

* Permitir que Safari abra el sitio web del Portal de empresa y descargue el perfil de administración antes de volver a la aplicación Portal de empresa.  
* Abrir la aplicación Ajustes para instalar el perfil de administración en el dispositivo.
* Volver a la aplicación Portal de empresa para completar la inscripción.  

Para conocer los pasos y las pantallas de inscripción actualizados, vea [Enroll iOS device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) (Inscripción de dispositivos iOS en Intune).  

## <a name="week-of-march-25-2019"></a>Semana del 25 de marzo de 2019

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Compatibilidad con la aplicación de cumplimiento de Power BI en la hoja Almacenamiento de datos en Microsoft Intune <!-- 4260871 -->
Antes, el vínculo **Descargar archivo de Power BI** en la hoja **Almacenamiento de datos de Intune** descargaba un informe de Almacenamiento de datos de Intune (archivo .pbix). Este informe se ha reemplazado por la aplicación de cumplimiento de Power BI. Para la aplicación de cumplimiento de Power BI no se necesitará ninguna configuración o carga especial. Se abrirá directamente en el portal en línea de Power BI y mostrará datos específicamente para el inquilino de Intune según sus credenciales. En Intune, seleccione el vínculo **Configurar el almacenamiento de datos de Intune**  en el lado derecho de la hoja de Intune. Después, haga clic en **Obtener aplicación de Power BI**. Para más información, vea [Connect to the Data Warehouse with Power BI](reports-proc-get-a-link-powerbi.md) (Conectarse al almacenamiento de datos con Power BI).

## <a name="week-of-march-18-2019"></a>Semana del 18 de marzo de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Implementar Microsoft Visio y Microsoft Project <!-- 3725386  -->
Ahora puede implementar Microsoft Visio Pro para Office 365 y Microsoft Project Online Desktop Client como aplicaciones independientes para dispositivos Windows 10 con Microsoft Intune, si dispone de licencias para estas aplicaciones. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar** para mostrar la hoja **Agregar aplicación**. En la hoja **Agregar aplicación**, seleccione **Windows 10** como **Tipo de aplicación**. Después, elija **Configurar conjunto de aplicaciones** para seleccionar las aplicaciones que instalará. Para más información sobre cómo las aplicaciones de Office 365 para dispositivos Windows 10, vea [Asignación de aplicaciones de Office 365 a dispositivos Windows 10 con Microsoft Intune](apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Cambio de nombre de producto de Microsoft Visio Pro para Office 365 <!-- 3593653  -->
**Microsoft Visio Pro para Office 365** ahora se conocerá como **Microsoft Visio Online Plan 2**.  Para más información sobre Microsoft Visio, vea [Visio Online Plan 2](https://products.office.com/visio/visio-online-plan-2). Para más información sobre cómo las aplicaciones de Office 365 para dispositivos Windows 10, vea [Asignación de aplicaciones de Office 365 a dispositivos Windows 10 con Microsoft Intune](apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Configuración de límite de caracteres de la directiva de protección de aplicaciones (APP) de Intune <!-- 3291302  -->
Los administradores de Intune pueden especificar una excepción en la configuración de la directiva **Restringir cortar, copiar y pegar con otras aplicaciones** de la APP de Intune.  También pueden especificar el número de caracteres que se pueden cortar o copiar de una aplicación administrada. Esto permitirá compartir el número especificado de caracteres en cualquier aplicación, independientemente de la opción "Restringir cortar, copiar y pegar con otras aplicaciones". Tenga en cuenta que para la aplicación Portal de empresa de Intune para Android se necesita la versión 5.0.4364.0 o posterior. Para más información, vea [Configuración de directivas de protección de aplicaciones de iOS](app-protection-policy-settings-ios.md#data-protection), [Configuración de directivas de protección de aplicaciones Android en Microsoft Intune](app-protection-policy-settings-android.md#data-protection) y [Revisión de los registros de protección de aplicaciones cliente](app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>XML de la Herramienta de implementación de Office (ODT) para la implementación de Office Pro Plus <!-- 3192477   -->
Será capaz de proporcionar el XML de la Herramienta de implementación de Office (ODT) al crear una instancia de Office Pro Plus en la consola de administración de Intune. Esto permite mayor capacidad de personalización si las opciones actuales de la interfaz de usuario de Intune no satisfacen sus necesidades. Para más información, vea [Asignación de aplicaciones de Office 365 a dispositivos Windows 10 con Microsoft Intune](https://docs.microsoft.com/intune/apps-add-office365) y [Opciones de configuración de la Herramienta de implementación de Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>Los iconos de aplicación se mostrarán con un fondo generado automáticamente <!-- 1429026  -->
En la aplicación Portal de empresa, ahora los iconos de aplicación se muestran con un fondo generado automáticamente según el color dominante del icono (si se puede detectar). Si procede, este fondo reemplaza el borde gris que antes se veía en los iconos de aplicación. Los usuarios verán este cambio en las versiones posteriores de Portal de empresa posteriores a 10.3.3451.0.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Instalar aplicaciones disponibles mediante la aplicación Portal de empresa después de la inscripción masiva de dispositivos Windows <!-- 2751523   -->
Los dispositivos Windows inscritos en Intune mediante [Inscripción masiva de Windows](windows-bulk-enroll.md) (paquetes de aprovisionamiento) podrán usar la aplicación Portal de empresa para instalar aplicaciones disponibles. Para más información sobre cómo configurar la aplicación Portal de empresa, vea [Adición manual de la aplicación Portal de empresa para Windows 10 con Microsoft Intune](store-apps-company-portal-app.md) y [Configuración de la aplicación Portal de empresa de Microsoft Intune](company-portal-app.md).

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>Posibilidad de seleccionar la aplicación Microsoft Teams como parte del conjunto de aplicaciones de Office <!-- 3828932  -->
La aplicación Microsoft Teams se puede incluir o excluir como parte de la instalación del conjunto de aplicaciones de Office Pro Plus. Esta característica funciona para Office Pro Plus con número de compilación 16.0.11328.20116+. El usuario debe cerrar sesión y después iniciar sesión en el dispositivo para que se complete la instalación. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**. Seleccione uno de los tipos de aplicación del **Conjunto de aplicaciones Office 365** y elija **Configurar conjunto de aplicaciones**.

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Iniciar automáticamente una aplicación cuando se ejecutan varias aplicaciones en modo de pantalla completa en dispositivos con Windows 10 y versiones posteriores <!-- 2351390 -->

En dispositivos con Windows 10 y versiones posteriores, puede ejecutar un dispositivo en modo de pantalla completa y ejecutar muchas aplicaciones. En esta actualización, hay un valor **Ejecución automática** configuración (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Windows 10 y versiones posteriores** para plataforma > **Pantalla completa** para el tipo de perfil > **Pantalla completa con varias aplicaciones**). Con este valor se puede iniciar automáticamente una aplicación cuando el usuario inicia sesión en el dispositivo.

Para ver una lista y una descripción de todos los valores de pantalla completa, vea [Windows 10 and later device settings to run as a kiosk in Intune](kiosk-settings-windows.md) (Configuración de dispositivos con Windows 10 y versiones posteriores para ejecutarlos en pantalla completa en Intune).

Se aplica a: Windows 10 y versiones posteriores

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>Registros operativos también muestran detalles en dispositivos no compatibles <!-- 4063755  -->
Al enrutar registros de Intune a características de supervisión de Azure, también puede enrutar los registros operativos. En esta actualización, los registros operativos también proporcionan información sobre los dispositivos no compatibles. 

Para más información sobre esta característica, vea [Envío de datos de registro al almacenamiento, a Event Hubs o a Log Analytics en Intune (versión preliminar)](review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Enrutar registros a Azure Monitor en más cargas de trabajo de Intune <!-- 3804627 -->
En Intune, puede enrutar los registros operativos y de auditoría a centros de eventos, almacenamiento y análisis de registros en Azure Monitor (**Intune** > **Supervisión** > **Configuración de diagnósticos**). En esta actualización, puede enrutar estos registros en más cargas de trabajo de Intune, incluido el cumplimiento, las configuraciones, las aplicaciones cliente y mucho más. 

Para más información sobre el enrutamiento de registros a Azure Monitor, vea [Envío de datos de registro al almacenamiento, a Event Hubs o a Log Analytics en Intune (versión preliminar)](review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Crear y usar extensiones de movilidad en dispositivos Android Zebra en Intune <!-- 3305880   -->
En esta actualización, Intune admite la configuración de dispositivos Android Zebra. En concreto, puede crear un perfil de configuración de dispositivo y aplicar la configuración a dispositivos Android Zebra mediante perfiles de movilidad extensiones (MX) generados por StageNow (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android** para plataforma > **Perfil de MX (solo Zebra)** para tipo de perfil).

Para más información sobre esta característica, vea [Use and manage Zebra devices with mobility extensions in Intune](android-zebra-mx-overview.md) (Uso y administración de dispositivos Zebra con extensiones de movilidad en Intune).

Se aplica a: Android

### <a name="device-management"></a>Administración de dispositivos

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Informe de cifrado para dispositivos Windows 10 (en versión preliminar pública)<!-- 2351538 -->  
Use la nueva opción [Informe de cifrado (vista previa)](encryption-monitor.md) para ver los detalles sobre el estado de cifrado de los dispositivos Windows 10. Entre los detalles disponibles se incluye una versión de TPM de los dispositivos, el estado y la preparación para cifrado, informes de errores y mucho más.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Acceder a claves de recuperación de BitLocker desde el portal de Intune (en versión preliminar pública) <!-- 2351547   -->  
Ahora puede usar Intune para [ver detalles](encryption-monitor.md) sobre el identificador de clave de BitLocker y las claves de recuperación de BitLocker, desde Azure Active Directory.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Compatibilidad de Microsoft Edge con escenarios de Intune en dispositivos iOS y Android <!-- 3411007 -->
Microsoft Edge será compatible con los mismos escenarios de administración que Intune Managed Browser con la adición de mejoras en la experiencia del usuario final. Entre las características para empresas de Microsoft Edge que se habilitan mediante las directivas de Intune se incluyen la identidad dual, la integración de la directiva de protección de aplicaciones, la integración del proxy de aplicación de Azure, favoritos administrados y accesos directos a la página principal. Para más información, vea [Compatibilidad con Microsoft Edge](app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Exchange Online y Conector de Intune retiran su compatibilidad para dispositivos EAS solamente <!--3105122  -->
La consola de Intune ya no admite la visualización y la administración de dispositivos de EAS solamente conectados a Exchange Online con el Conector de Intune. Dispone de estas otras opciones:
- Inscribir dispositivos en Administración de dispositivos móviles (MDM)
- Usar las directivas de Intune App Protection para administrar los dispositivos
- Usar controles de Exchange como se describe en [Clients and mobile in Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online) (Clientes y dispositivos móviles en Exchange Online)

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>Buscar la página Todos los dispositivos para un dispositivo concreto mediante el uso de [nombre] <!--4254930 -->
Ahora puede buscar un nombre de dispositivo exacto. Vaya a **Intune** > **Dispositivos** > **Todos los dispositivos** > en el cuadro de búsqueda, escriba el nombre de dispositivo entre {} para buscar una coincidencia exacta. Por ejemplo, **{Device12345}** .

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>Compatibilidad con conectores adicionales en la página Estado del inquilino <!-- 3617202  -->
La [página Estado del inquilino](tenant-status.md) ahora muestra información de estado de los conectores adicionales, incluidos *Protección contra amenazas avanzada de Windows Defender* (ATP) y otros conectores de Mobile Threat Defense.

### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Concedido el acceso de solo lectura a Intune a algunos roles de Azure Active Directory <!-- 3637917  -->
Se ha concedido acceso de solo lectura de Intune a estos roles de Azure AD. Los permisos concedidos con roles de Azure AD sustituyen a los permisos concedidos con control de acceso basado en roles (RBAC) de Intune.

Acceso de solo lectura a los datos de auditoría de Intune:

- Administrador de cumplimiento
- Administrador de datos de cumplimiento

Acceso de solo lectura a todos los datos de Intune:

- Administrador de seguridad
- Operador de seguridad
- Lector de seguridad

Para más información, vea [Control de acceso basado en roles](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>Etiquetas de ámbito para perfiles de aprovisionamiento de aplicaciones iOS <!--2934430   -->
Puede agregar una etiqueta de ámbito a un perfil de aprovisionamiento de aplicaciones iOS para que solo los usuarios con roles que también tengan asignada esa etiqueta de ámbito puedan acceder al perfil de aprovisionamiento de aplicaciones iOS. Para más información, vea [Use RBAC and scope tags](scope-tags.md) (Usar RBAC y etiquetas de ámbito).

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>Etiquetas de ámbito para directivas de configuración de aplicaciones <!--2371891   -->
Puede agregar una etiqueta de ámbito a una directiva de configuración de aplicaciones para que solo los usuarios con roles que también tengan asignada esa etiqueta de ámbito puedan acceder a la directiva de configuración de aplicaciones. La directiva de configuración de aplicaciones solo puede asociarse a aplicaciones que tengan asignada la misma etiqueta de ámbito. Para más información, vea [Use RBAC and scope tags](scope-tags.md) (Usar RBAC y etiquetas de ámbito).

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Compatibilidad de Microsoft Edge con escenarios de Intune en dispositivos iOS y Android <!-- 3411007 -->
Microsoft Edge será compatible con los mismos escenarios de administración que Intune Managed Browser con la adición de mejoras en la experiencia del usuario final. Entre las características para empresas de Microsoft Edge que se habilitan mediante las directivas de Intune se incluyen la identidad dual, la integración de la directiva de protección de aplicaciones, la integración del proxy de aplicación de Azure, favoritos administrados y accesos directos a la página principal. Para más información, vea [Compatibilidad con Microsoft Edge](app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>Semana del 25 de febrero de 2019

### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="intune-powershell-module----951068----"></a>Módulo de PowerShell de Intune <!-- 951068  -->
El módulo de PowerShell de Intune, que proporciona compatibilidad con la API de Intune a través de Microsoft Graph, ya está disponible en la [Galería de Microsoft PowerShell](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Detalles sobre cómo usar este módulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Ejemplos de escenarios de uso de este módulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Compatibilidad mejorada para la optimización de entrega  <!--3183757  -->
Hemos ampliado la compatibilidad de Intune para configurar la optimización de entrega. Ahora puede configurar una lista expandida de [Configuración de optimización de entrega](delivery-optimization-settings.md) y aplicarla a los dispositivos directamente desde la consola de Intune.


## <a name="week-of-february-18-2019"></a>Semana del 18 de febrero de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune aprovechará las API de Google Play Protect en dispositivos Android <!-- 2577355   -->
Algunos administradores de TI se enfrentan a un panorama BYOD donde los usuarios finales pueden acabar por obtener privilegios de usuario root o realizar jailbreaking en sus teléfonos móviles. Este comportamiento, aunque en ocasiones no sea malintencionado, tiene como resultado la omisión de muchas directivas de Intune que se establecen con el fin de proteger los datos de la organización en los dispositivos de los usuarios finales. Por tanto, Intune proporciona la detección de jailbreak y de obtención de permisos de usuario root para los dispositivos inscritos y no inscritos. Con esta versión, ahora Intune aprovechará las API de Google Play Protect para agregarlas a nuestras comprobaciones de detección de modificaciones existentes para los dispositivos no inscritos. Aunque Google no comparte la totalidad de las comprobaciones de detección de modificaciones que se producen, esperamos que estas API detecten los usuarios que han modificado sus dispositivos por cualquier motivo, desde la personalización del dispositivo a la obtención de las actualizaciones más recientes del sistema operativo en dispositivos más antiguos. Después, se puede bloquear el acceso de estos usuarios a los datos corporativos, o bien se pueden eliminar sus cuentas de empresa desde sus aplicaciones habilitadas para la directiva. Para obtener valor adicional, ahora los administradores de TI tendrán varias actualizaciones de informes en la hoja Protección de aplicaciones de Intune: en el informe "Usuarios marcados" se mostrarán los usuarios que se han detectado mediante el examen de la API SafetyNet de Google Play Protect, y en el informe "Aplicaciones potencialmente peligrosas" se mostrarán las aplicaciones que se hayan detectado mediante el examen de la API Verify Apps de Google. Esta característica está disponible en Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Información de aplicaciones Win32 disponible en la hoja Solución de problemas <!-- 2617342   -->
Ya puede recopilar archivos de registro de errores de la instalación de una aplicación Win32 desde la hoja **Solución de problemas** de la aplicación Intune. Para más información sobre la solución de problemas de instalación de aplicaciones, vea [Troubleshoot app installation issue](troubleshoot-app-install.md) (Solución de problemas de instalación de aplicaciones) y [Solucionar los problemas de aplicaciones Win32](apps-win32-app-management.md#troubleshoot-win32-app-issues).

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Detalles del estado de la aplicación para aplicaciones iOS <!-- 3761235   -->
Hay nuevos mensajes de error de instalación de aplicaciones relacionados con lo siguiente:
- Error de las aplicaciones VPP cuando se instalan en un iPad compartido
- Error cuando la tienda de aplicaciones está deshabilitada
- No se puede encontrar la licencia VPP de la aplicación
- No se pueden instalar las aplicaciones del sistema con el proveedor de MDM
- No se pueden instalar aplicaciones cuando el dispositivo está en modo de pantalla completa o modo perdido
- No se puede instalar la aplicación cuando el usuario no ha iniciado sesión en la App Store

En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > "Nombre de la aplicación" > **Estado de instalación del dispositivo**. Los mensajes de error nuevos estarán disponibles en el estado **Detalles del estado**.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Nuevas pantalla de categorías de aplicaciones en la aplicación Portal de empresa para Windows 10<!-- 3834780  -->
Se ha agregado una nueva pantalla denominada **Categorías de aplicaciones** para mejorar la experiencia de exploración y selección en la aplicación Portal de empresa para Windows 10. Los usuarios ahora verán sus aplicaciones ordenadas en categorías como **Destacadas**, **Educación** y **Productividad**. Este cambio aparece en las versiones 10.3.3451.0 y posteriores de Portal de empresa. Para ver la nueva pantalla, vea [Actualizaciones de la interfaz de usuario para las aplicaciones de usuario final de Intune](https://docs.microsoft.com/intune/whats-new-app-ui). Para más información sobre las aplicaciones del Portal de empresa, vea [Instalar y compartir aplicaciones en el dispositivo](/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Aplicación de cumplimiento de Power BI <!-- 1455231 doc-work-item -->
Acceda al almacenamiento de datos de Intune en Power BI Online mediante la aplicación [Cumplimiento de Intune (Almacenamiento de datos)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp). Con esta aplicación de Power BI, ahora puede acceder y compartir informes creados previamente sin necesidad de configuración y sin salir de su explorador web. Para más información, vea el [registro de cambios en la aplicación del cumplimiento de Power BI](reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>Los scripts de PowerShell se pueden ejecutar en un host de 64 bits en dispositivos de 64 bits <!-- 1862675   -->
Al agregar un script de PowerShell a un perfil de configuración de dispositivo, el script siempre se ejecuta en 32 bits, incluso en sistemas operativos de 64 bits. Con esta actualización, un administrador puede ejecutar el script en un host de PowerShell de 64 bits en dispositivos de 64 bits (**Configuración del dispositivo** > **Scripts de PowerShell** >  **Agregar** > **Configurar** > **Ejecutar script en el host de PowerShell de 64 bits**).

Para obtener más detalles sobre el uso de PowerShell, vea [Scripts de PowerShell en Intune](intune-management-extension.md).

Se aplica a: Windows 10 y versiones posteriores

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>Se pide a los usuarios de macOS que actualicen su contraseña <!-- 1873216 -->
Intune está exigiendo el valor **ChangeAtNextAuth** en los dispositivos macOS. Esta opción afecta a los usuarios finales y los dispositivos que tienen directivas de contraseña de cumplimiento o perfiles de contraseña de restricción de dispositivo. Se pide a los usuarios finales que actualicen su contraseña una vez. Este mensaje se produce cada vez que un usuario realiza por primera vez una tarea que necesita autenticación, como iniciar sesión en el dispositivo. También se pide a los usuarios que actualicen su contraseña cuando hagan algo que necesite privilegios administrativos, como por ejemplo, pedir acceso a cadenas de llaves. 

Cuando el administrador cambia la directiva de contraseña nueva o existente, se pide a los usuarios finales que vuelan a actualizar su contraseña.

Se aplica a:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521------"></a>Asignar certificados SCEP en un dispositivo macOS sin usuarios    <!-- 2340521    -->
Puede asignar los certificados del Protocolo de inscripción de certificados simple (SCEP) mediante los atributos del dispositivo para dispositivos macOS, incluidos los dispositivos sin afinidad de usuario y asociar el perfil de certificado con perfiles de Wi-Fi o VPN. Esto amplía la compatibilidad que ya tenemos para [asignar certificados del SCEP a dispositivos con y sin afinidad de usuario](certificates-profile-scep.md) que tienen instalado Windows, iOS y Android.  Esta actualización agrega la opción de seleccionar un tipo de certificado de *Dispositivo* al configurar un perfil de certificado SCEP para macOS.

Se aplica a: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Actualización de la interfaz de usuario del acceso condicional de Intune   <!-- 2432313   -->
Hemos realizado mejoras en la interfaz de usuario para el acceso condicional en la consola de Intune. Entre ellos se incluyen los siguientes:
- Hemos reemplazado la hoja *Acceso condicional* de Intune con la hoja de Azure Active Directory. Esto garantiza que tendrá acceso a toda la gama de opciones y configuraciones para el [acceso condicional](conditional-access.md) (que sigue siendo una tecnología de Azure AD) desde la consola de Intune. 
- Hemos cambiado el nombre de la hoja *Acceso local* a *Acceso de Exchange* y hemos cambiado de sitio el programa de instalación del *Conector de servicio de Exchange* a esta hoja con el nuevo nombre.  Este cambio consolida donde se puede [configurar y supervisar los detalles relacionados con Exchange en línea y local](exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Las aplicaciones de explorador del Quiosco y Microsoft Edge se pueden ejecutar en dispositivos Windows 10 en modo de pantalla completa <!-- 2935135   -->
Puede usar dispositivos Windows 10 en modo de pantalla completa para ejecutar una o varias aplicaciones. En esta actualización se incluyen varios cambios en el uso de las aplicaciones de explorador en modo de pantalla completa, incluidos los siguientes:

- Se agrega el explorador Microsoft Edge o Kiosk Browser para que se ejecuten como aplicaciones en el dispositivo de pantalla completa (**Configuración del dispositivo** > **Perfiles** > **Nuevo perfil**  >  **Windows 10 y versiones posteriores** para plataforma > **Pantalla completa** para el tipo de perfil).
- Hay disponibles nuevas características y configuraciones para permitir o restringir (**Configuración del dispositivo** > **Perfiles** > **Nuevo perfil** > **Windows 10 y versiones posteriores** para la plataforma > **Restricciones de dispositivos** para el tipo de perfil), incluidos:

- Explorador Microsoft Edge:
  - Usar el modo de pantalla completa de Microsoft Edge
  - Actualizar el explorador después del tiempo de inactividad

- Favoritos y búsqueda:
  - Permitir cambios en el motor de búsqueda

Para obtener una lista de estos valores, vea:

- [Configuración de dispositivos con Windows 10 y versiones posteriores para ejecutarse como una pantalla completa](kiosk-settings-windows.md)
- [Restricciones de dispositivos del explorador Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser)
- [Favoritos y restricciones de búsqueda de dispositivos](device-restrictions-windows-10.md##favorites-and-search)

Se aplica a: Windows 10 y versiones posteriores

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Nueva configuración de restricción de dispositivos para dispositivos iOS y macOS <!-- 3448774   -->
Puede restringir algunas opciones y características de los dispositivos que ejecutan iOS y macOS (**Configuración del dispositivo** > **Perfiles** > **Nuevo perfil**  >  **iOS** o **macOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil). En esta actualización se agregan más características y valores de configuración que puede controlar, incluida la configuración del tiempo de pantalla, el cambio de la configuración eSIM, planes de telefonía móvil y mucho más en dispositivos iOS. También la opción de retrasar la visibilidad para el usuario de las actualizaciones de software y el bloqueo de almacenamiento en caché de contenido en dispositivos macOS. 

Para ver las características y la configuración que se pueden restringir, vea:

- [Configuración de restricciones de dispositivos iOS](device-restrictions-ios.md)
- [Configuración de restricciones de dispositivos macOS](device-restrictions-macos.md)

Se aplica a:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>Los dispositivos de "Pantalla completa" ahora se denominan "Dispositivos dedicados" en dispositivos Android Enterprise <!-- 3598402   -->
Para alinear con la terminología de Android, **Pantalla completa** cambia a **Dispositivos dedicados** para dispositivos Android Enterprise (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > ** Android Enterprise para la plataforma > **Solo el propietario del dispositivo** > **Restricciones de dispositivos** > **Dispositivos dedicados**).

Para ver los valores disponibles, vaya a [Android Enterprise device settings to allow or restrict features using Intune](device-restrictions-android-for-work.md#dedicated-device-settings) (Configuración de dispositivos Android Enterprise para permitir o restringir características con Intune).

Se aplica a:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Las opciones de Safari y Retrasar la visibilidad de las actualizaciones de software iOS se cambian a la interfaz de usuario de Intune <!-- 3640850, 3803313   -->
Para los dispositivos iOS, puede establecer la configuración de Safari y configurar actualizaciones de software. En esta actualización, estas opciones se van a cambiar a otra partes de la interfaz de usuario de Intune:

- La configuración de Safari cambia de **Safari** (**Configuración del dispositivo** > **Perfiles** > **Nuevo perfil** > **iOS** para la plataforma > **Restricciones de dispositivos** para el tipo de perfil) a **[Aplicaciones integradas](device-restrictions-ios.md#built-in-apps)** .
- La opción **Delaying user software update visibility for supervised iOS devices** (Retrasar la visibilidad de las actualizaciones de software para los dispositivos iOS supervisados) (**Actualizaciones de software** > **Directivas de actualización para iOS**) se va a cambiar a **Restricciones de dispositivos** >  **[General](device-restrictions-ios.md#general)** .  Para más información sobre el impacto en las directivas existentes, vea [Configuración de directivas de actualización de iOS en Intune](software-updates-ios.md#configure-the-policy). 

Para obtener una lista de estos valores, vea:

- [Restricciones de dispositivos iOS](device-restrictions-ios.md) 
- [Actualizaciones del software iOS](software-updates-ios.md)

Esta característica se aplica a: 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>En los dispositivos iOS se ha cambiado el nombre de Habilitar restricciones en la configuración del dispositivo por Tiempo de uso <!-- 3699164   -->
Puede configurar **Habilitar restricciones en la configuración del dispositivo**  en dispositivos iOS supervisados (**Configuración del dispositivo** > **Perfiles** > **Nuevo perfil** > **iOS** para plataforma > **Restricciones de dispositivos** para tipo de perfil > **General**). En esta actualización, se ha cambiado el nombre de esta opción por **Tiempo de uso (solo con supervisión)** . 

El comportamiento es el mismo. De manera específica: 

- iOS 11.4.1 y versiones anteriores: **Bloquear** impide que los usuarios finales establezcan sus propias restricciones en la configuración del dispositivo. 
- iOS 12.0 y versiones posteriores: **Bloquear** impide que los usuarios finales establezcan su propio **Tiempo de uso** en la configuración del dispositivo, incluidas las restricciones de contenido y privacidad. En los dispositivos actualizados a iOS 12.0 ya no aparecerá la pestaña Restricciones en la configuración del dispositivo. Estas opciones se encuentran en **Tiempo de uso**. 

Para obtener una lista de los valores, vea [Restricciones de dispositivos iOS](device-restrictions-ios.md#general).

Se aplica a: 
- iOS


### <a name="device-management"></a>Administración de dispositivos

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Cambio del nombre de un dispositivo Windows inscrito <!-- 1911112  -->
Ahora puede cambiar el nombre de un dispositivo Windows 10 inscrito (RS4 o posterior). Para ello, seleccione **Intune** > **Dispositivos** > **Todos los dispositivos** > elija un dispositivo > **Cambiar el nombre del dispositivo**. Esta característica no es compatible actualmente con el cambio de nombre de dispositivos Windows híbridos con Azure AD.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Asignación automática de etiquetas de ámbito a los recursos creados por un administrador con ese ámbito <!-- 3173823  -->
Cuando un administrador crea un recurso, las etiquetas de ámbito asignadas al administrador se asignarán de forma automática a esos recursos nuevos.

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>El informe Errores de inscripción se mueve a la hoja Inscripción de dispositivos <!-- 3560202  -->
El informe **Errores de inscripción** se ha movido a la sección **Supervisar** de la hoja **Inscripción de dispositivos**. Se han agregado dos columnas nuevas (Método de inscripción y Versión del sistema operativo).

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Se ha cambiado el nombre del informe Abandono del Portal de empresa a Inscripciones de usuario incompletas <!--3815076 eemiss -->
Se ha cambiado el nombre del informe **Abandono del Portal de empresa** a **Inscripciones de usuario incompletas**.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>Semana del 4 de febrero de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Modo oscuro del Portal de empresa de macOS para Intune <!-- 3300524  -->
El Portal de empresa de macOS para Intune ahora admite el Modo oscuro para macOS. Cuando habilita el Modo oscuro en un dispositivo macOS 10.14 o una versión posterior, el Portal de empresa ajustará su apariencia para que los colores reflejen ese modo.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>Semana del 21 de enero de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notificaciones del sistema para aplicaciones Win32 <!-- 3136566   -->
Puede suprimir notificaciones del sistema para el usuario final por asignación de aplicaciones. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > seleccione la aplicación > **Asignaciones** > **Incluir grupos**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Actualización de la interfaz de usuario de las directivas de protección de aplicaciones de Intune <!-- 3251427  -->
Hemos cambiado las etiquetas para las opciones y los botones de la protección de aplicaciones de Intune para que sean más fáciles de entender. Algunos de los cambios son:  
- Los controles han cambiado de **sí** / **no** a principalmente **bloquear** / **permitir** y **deshabilitar** / **habilitar**. Las etiquetas también se actualizaron.  
- Se cambió el formato de las opciones, de tal forma que la opción y su etiqueta aparezcan una al lado de la otra en el control, para así facilitar la navegación.   

La configuración predeterminada y el número de opciones se conservan, pero este cambio permite al usuario entender, navegar y utilizar la configuración con más facilidad para aplicar las directivas de protección de aplicaciones seleccionadas. Para información, consulte la [configuración para iOS](app-protection-policy-settings-ios.md) y la [configuración para Android](app-protection-policy-settings-android.md).

### <a name="additional-settings-for-outlook----3301182----"></a>Configuración adicional para Outlook <!-- 3301182  -->
Ahora puede cambiar estos otros valores de configuración de Outlook para iOS y Android mediante Intune:

- Permitir que solo se usen cuentas profesionales o educativas en iOS y Android.
- Implementar la autenticación moderna para Office 365 y la autenticación moderna híbrida para cuentas locales.
- Usar `SAMAccountName` para el campo de nombre de usuario en el perfil de correo electrónico al tener seleccionada la autenticación básica.
- Permitir que se guarden contactos.
- Configurar información sobre el correo electrónico de destinatarios externos.
- Configurar la **Bandeja de entrada Prioritarios**.
- Requerir autenticación biométrica para acceder a Outlook para iOS.
- Bloquear las imágenes externas.

> [!NOTE]
> Si usa directivas de Intune App Protection para administrar el acceso de las identidades corporativas, le recomendamos que no habilite el **requisito de autenticación biométrica**. Para más información, vea **Requerir credenciales corporativas en acceso**, en los artículos relativos a la [configuración de acceso de iOS](app-protection-policy-settings-ios.md#access-requirements) y la [configuración de acceso de Android](app-protection-policy-settings-android.md#access-requirements), respectivamente.

Para más información, vea [Opciones de configuración de Microsoft Outlook](app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Eliminación de aplicaciones de Android Enterprise <!-- 1352553 -->
Puede eliminar aplicaciones de Google Play administrado desde Microsoft Intune. Para eliminar una aplicación de Google Play administrado, abra Microsoft Intune en Azure Portal y seleccione **Aplicaciones cliente** > **Aplicaciones**. En la lista de aplicaciones, seleccione los puntos suspensivos (...) a la derecha de la aplicación de Google Play administrado y luego seleccione **Eliminar** en la lista que aparece. Cuando se elimina una aplicación de Google Play administrada de la lista de aplicaciones, automáticamente se desactiva la aprobación de la aplicación administrada de Google Play.

#### <a name="managed-google-play-app-type----1352580---"></a>Tipo de aplicaicón de Google Play administrado <!-- 1352580 -->
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

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Comprobación de cumplimiento de Configuration Manager <!-- 2192052  eepublished  -->
Esta actualización incluirá una nueva configuración de conformidad de System Center Configuration Manager (**Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Windows 10 y versiones posteriores** > **Cumplimiento de Configuration Manager**). Configuration Manager envía señales a la conformidad de Intune. Mediante esta configuración, puede exigir que todas las señales de Configuration Manager devuelvan “conforme”.

Por ejemplo, exige que todas las actualizaciones de software se instalen en los dispositivos. En Configuration Manager, este requisito tiene el estado “Instalado”. Si algún programa del dispositivo se encuentra en un estado desconocido, dicho dispositivo no será conforme en Intune.

[Cumplimiento de Configuration Manager](compliance-policy-create-windows.md#configuration-manager-compliance) describe esta configuración.

Se aplica a: Windows 10 y versiones posteriores

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Personalización del papel tapiz en dispositivos iOS supervisados mediante un perfil de configuración de dispositivo <!-- 2809324   -->
Cuando cree un perfil de configuración de dispositivos para dispositivos iOS, podrá personalizar algunas características (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para la plataforma > **Características del dispositivo** para el tipo de perfil). Esta actualización incluye nuevas configuraciones **Fondo de pantalla** que permiten a un administrador usar una imagen .png, .jpg o .jpeg en la pantalla de inicio o en la pantalla de bloqueo. Esta configuración de fondo de pantalla solo se aplica a los dispositivos supervisados. 

Para una lista de esta configuración, consulte [iOS device feature settings](ios-device-features-settings.md) (Configuración de características de dispositivos iOS).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Pantalla completa de Windows 10 disponible con carácter general <!-- 3594661  -->
En esta actualización, la característica Pantalla completa en dispositivos con Windows 10 y versiones posteriores está disponible con carácter general (GA). Para ver todas las configuraciones que puede agregar y definir, consulte [Configuración de dispositivos con Windows 10 y versiones posteriores para ejecutarse como una pantalla completa dedicada con Intune](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Se eliminó la opción para compartir contacto a través de Bluetooth en Restricciones del dispositivo > Propietario del dispositivo para Android Enterprise <!-- 3598396   -->
Cuando se crea un perfil de restricciones de dispositivos para dispositivos de Android Enterprise, hay una configuración para **Compartir contacto a través de Bluetooth**. En esta actualización, se elimina la configuración **Compartir contacto a través de Bluetooth** (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **Restricciones de dispositivos > Propietario del dispositivo** para el tipo de perfil > **General**). 

La configuración **Compartir contacto a través de Bluetooth** no es compatible con la administración de Propietario del dispositivo Android Enterprise. Por lo que cuando se quite esta configuración, no afectará a ningún dispositivo ni inquilino, incluso si esta opción está habilitada y configurada en su entorno.

Para ver la lista actual de configuraciones, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características](device-restrictions-android-for-work.md).

Se aplica a: Propietario del dispositivo Android Enterprise

### <a name="device-management"></a>Administración de dispositivos

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Compatibilidad con el borrado selectivo para dispositivos con trabajos en curso sin inscripción <!-- 1434452 -->
Windows Information Protection Without Enrollment (WIP-WE) permite a los clientes proteger sus datos corporativos en dispositivos con Windows 10 sin necesidad de realizar una inscripción de MDM completa. Una vez que los documentos están protegidos con una directiva de WIP-WE, un administrador de Intune puede borrar de forma selectiva los datos protegidos. Mediante la selección del usuario y dispositivo, y el envío de una solicitud de borrado, todos los datos protegidos mediante la directiva de WIP-WE quedarán inservibles. En Intune en Azure Portal, seleccione **Aplicación móvil** > **Borrado selectivo de aplicaciones**.

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Nuevos registros operativos y posibilidad de enviar registros a los servicios de Azure Monitor <!-- 3762211  -->
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

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Semana del 14 de enero de 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Versión preliminar de la compatibilidad con dispositivos Android totalmente administrados de propiedad corporativa <!-- 1574342  -->
Intune ya admite dispositivos Android totalmente administrados; un escenario de "propietario de dispositivo" de propiedad corporativa en el que el departamento de TI administra de manera rigurosa los dispositivos y estos se asocian a usuarios individuales. Esto permite que los administradores administren todo el dispositivo, apliquen una amplia variedad de controles de directivas no disponibles para los perfiles de trabajo y restrinjan las instalaciones de aplicaciones por parte de los usuarios solo a Google Play administrado. Para obtener más información, vea [Set up Intune enrollment of Android fully managed devices](android-fully-managed-enroll.md) (Configuración de la inscripción en Intune de dispositivos Android totalmente administrados) y [Enroll your dedicated devices or fully managed devices](android-dedicated-devices-fully-managed-enroll.md) (Inscripción de dispositivos dedicados o dispositivos totalmente administrados).  Tenga en cuenta que esta característica está en versión preliminar. Algunas funcionalidades de Intune, como certificados, cumplimiento y acceso condicional, no están disponibles actualmente con dispositivos Android totalmente administrados.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Semana del 7 de enero de 2019

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="intune-app-pin----2298397---"></a>PIN de aplicación de Intune <!-- 2298397 -->
Como administrador de TI, podrá configurar el número de días que un usuario final puede esperar hasta que se tenga que cambiar el PIN de aplicación de Intune. La nueva configuración es *Restablecimiento del PIN después de un número de días* y está disponible en Azure Portal; para acceder a esta configuración, seleccione **Intune** > **Aplicaciones cliente** > **Directivas de protección de aplicaciones** > **Crear directiva** > **Configuración** > **Requisitos de acceso**. Esta característica está disponible para dispositivos [iOS](app-protection-policy-settings-ios.md) y [Android](app-protection-policy-settings-android.md), y admite un valor entero positivo.


#### <a name="intune-device-reporting-fields----2748738---"></a>Campos de informes de dispositivo de Intune <!-- 2748738 -->
Intune proporciona campos adicionales con información sobre el dispositivo, como el identificador de registro de aplicación, el fabricante de Android, el modelo, la versión de la revisión de seguridad y el modelo de iOS. En Intune, estos campos estarán disponibles en **Aplicaciones cliente** > **Estado de protección de aplicaciones** y **Informe de protección de aplicaciones: iOS, Android**. Además, estos parámetros lo ayudarán a configurar la lista de **admitidos** correspondiente al fabricante de dispositivo (Android), la lista de **admitidos** del modelo de dispositivo (iOS y Android) y la configuración de versión de la revisión de seguridad mínima de Android. 


### <a name="device-configuration"></a>Configuración de los dispositivos

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Las plantillas administrativas están en versión preliminar pública y se movieron a su propio perfil de configuración <!-- 3322847 -->

Las plantillas administrativas de Intune (**Configuración del dispositivo** > **Plantillas administrativas**) están actualmente en versión preliminar pública. Con esta actualización:

- Las plantillas administrativas contienen unos 300 valores de configuración que se pueden administrar en Intune. Anteriormente, estas configuraciones solo existían en el editor de directivas de grupo.
- Las plantillas administrativas están disponibles en versión preliminar pública.
- Las plantillas administrativas están disponibles en versión preliminar pública y se han migrado desde **Configuración del dispositivo** > **Plantillas administrativas** a **Configuración del dispositivo** > **Perfiles** > **Crear perfil**. Luego, en **Plataforma**, seleccione **Windows 10 y versiones posteriores**, en **Tipo de perfil**, y haga clic en **Plantillas administrativas**.
- Se han habilitado los informes.

Para obtener más información sobre esta característica, vaya a [Plantillas de Windows 10 para configurar opciones de directiva de grupo](administrative-templates-windows.md).

Se aplica a: Windows 10 y versiones posteriores

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Uso de S/MIME para cifrar y firmar varios dispositivos para un usuario  <!-- 1333642 -->
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

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Algunos valores de configuración de BitLocker admiten Windows 10 Pro Edition<!-- 2727036 -->
Podrá crear un perfil de configuración que establezca los ajustes de Endpoint Protection en dispositivos con Windows 10, incluido BitLocker. En esta actualización se agrega la compatibilidad con Windows 10 Professional Edition en algunas opciones de configuración de BitLocker. Para ver estos ajustes de protección, vaya a [Configuración de Endpoint Protection para Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Cambio del nombre de Configuración de dispositivo compartido a Mensaje de la pantalla de bloqueo para dispositivos iOS en Azure Portal<!-- 2809362 -->
Al crear un perfil de configuración de dispositivos iOS, puede agregar la opción **Configuración de dispositivo compartido** para mostrar texto específico en la pantalla de bloqueo. En esta actualización se incluyen los cambios siguientes: 
- El nombre de la opción **Configuración de un dispositivo compartido** en Azure Portal se cambia a "Mensaje de la pantalla de bloqueo (solo con supervisión)" (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > Elegir **iOS** para la plataforma > Elegir **Características del dispositivo** para el tipo de perfil > **Mensaje de la pantalla de bloqueo**).
- Al agregar mensajes de la pantalla de bloqueo, puede insertar un número de serie, un nombre de dispositivo u otro valor específico del dispositivo como una variable en **Información de etiqueta del activo** y **Nota al pie en la pantalla de bloqueo**. Por ejemplo, puede escribir `Device name: {{devicename}}` o `Serial number is {{serialnumber}}` entre llaves. [Tokens de iOS](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) muestra los tokens disponibles que se pueden usar.
En [Configuración para mostrar mensaje en la pantalla de bloqueo](shared-device-settings-ios.md), se muestra la configuración actual.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Adición en dispositivos iOS de nuevo App Store, visualización de documentos y configuración de restricción de dispositivos de juego <!-- 2827760-->
En **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** para la plataforma y **Restricciones de dispositivo** para el tipo de perfil, en **App Store, visualización de documentos y juegos**, se han agregado las siguientes opciones de configuración: Permitir a las aplicaciones administradas escribir contactos en cuentas de contactos no administradas y Permitir a las aplicaciones no administradas leer en cuentas de contactos administradas. Para ver estas opciones de configuración, vaya a [Restricciones de dispositivos iOS](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Nueva configuración de notificaciones, sugerencias y bloqueo del teclado para dispositivos de propietarios de dispositivos Android Enterprise <!-- 3201839 3201843 -->
Esta actualización incluye varias características de los dispositivos Android Enterprise cuando se ejecutan como propietario del dispositivo. Para usar estas características, vaya a **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > en **Plataforma**, elija **Android Enterprise** > en **Tipo de perfil**, elija **Solo el propietario del dispositivo** > **Restricciones de dispositivos**.

Nuevas características: 

- Deshabilitar la visualización de las notificaciones del sistema, incluidas las llamadas entrantes, las alertas del sistema, los errores del sistema, etc.
- Sugerir omitir los tutoriales de inicio y las sugerencias para las aplicaciones que se abren por primera vez.
- Deshabilitar la configuración avanzada del bloqueo del teclado, como la cámara, las notificaciones, el desbloqueo con huella digital, etc.


Para ver la configuración actual, vaya a [Configuración de restricciones de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Los dispositivos de propietarios de dispositivos Android Enterprise pueden usar conexiones VPN siempre activas <!-- 3202194 -->
En esta actualización, puede usar conexiones VPN siempre activas en dispositivos propietarios del dispositivo Android Enterprise. Las conexiones VPN siempre activas permanecen conectadas o se vuelven a conectar inmediatamente cuando el usuario desbloquea el dispositivo, cuando se reinicia el dispositivo o cuando cambia la red inalámbrica. También puede poner la conexión en modo “bloqueo”, que bloquea todo el tráfico de red hasta que la conexión VPN esté activa.
Puede habilitar la VPN siempre activa en **Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **Android Enterprise** para la plataforma > **Restricciones de dispositivos** solo para el propietario del dispositivo > **Conectividad**. Para ver la configuración actual, vaya a [Configuración de restricciones de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nueva configuración para terminar procesos en el Administrador de tareas de dispositivos Windows 10 <!-- 3285177 --> 
Esta actualización incluye una configuración nueva para terminar los procesos con el Administrador de tareas en dispositivos Windows 10. Con un perfil de configuración de dispositivo (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > en **Plataforma**, elija **Windows 10** > en **Tipo de perfil**, elija **Restricciones de dispositivos** > **Configuración general**), elige si permitir o impedir esta configuración.
Para ver la configuración actual, vaya a [Configuración de restricciones de dispositivos Windows 10](device-restrictions-windows-10.md).
Se aplica a: Windows 10 y versiones posteriores


### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Mensajes de error de restricción de inscripción más detallados <!-- 3111564 -->
Los mensajes de error más detallados estarán disponibles cuando no se cumplan las restricciones de inscripción. Para ver estos mensajes, vaya a **Intune** > **Solucionar problemas** > y revise la tabla Errores de inscripción. Para obtener más información, vea la [lista de errores de inscripción](help-desk-operators.md#enrollment-failure-reference).

### <a name="monitor-and-troubleshoot"></a>Supervisión y solución de problemas

#### <a name="tenant-status-dashboard-----1124854---"></a>Panel Estado del inquilino  <!-- 1124854 -->
En la nueva [página Estado del inquilino](tenant-status.md) se proporciona una ubicación única donde puede ver el estado del inquilino y los detalles relacionados.  El panel se divide en cuatro áreas:
- **Detalles del inquilino**: se muestra información como el nombre del inquilino y la ubicación, la entidad de MDM, el número total de dispositivos inscritos en el inquilino y el número de licencias. En esta sección también se indica la versión de mantenimiento actual del inquilino.
- **Estado del conector**: muestra información sobre conectores disponibles que ha configurado y, además, se puede mostrar una lista de los que aún no ha habilitado.  
   Basándose en el estado actual de cada conector, se marcan como Correcto, Advertencia o Incorrecto. Seleccione un conector para explorarlo en profundidad y ver sus detalles, o bien para configurar información adicional sobre este.
- **Estado del servicio Intune**: muestra detalles sobre incidentes activos o interrupciones del inquilino. La información de esta sección se obtiene directamente del Centro de mensajes de Office.
- **Noticias de Intune**: muestra mensajes activos para el inquilino. En estos mensajes, se incluyen notificaciones cuando el inquilino recibe las características de Intune más recientes.  La información de esta sección se obtiene directamente del Centro de mensajes de Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Nueva experiencia de ayuda y soporte técnico en el Portal de empresa para Windows 10 <!-- 1488939-->
La nueva página de ayuda y soporte técnico del Portal de empresa ayuda a los usuarios a solucionar problemas y solicitar ayuda para problemas de acceso y de aplicaciones. Desde la nueva página, puede enviar por correo electrónico detalles de registros de diagnóstico y errores, así como obtener los detalles del departamento de soporte técnico de su organización. También encontrará una sección de preguntas más frecuentes con vínculos a la documentación de Intune relevante. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Nueva experiencia de ayuda y soporte técnico para Intune   <!-- #3307080 -->
Implementaremos la nueva experiencia de ayuda y soporte técnico a todos los inquilinos en los próximos días. Esta experiencia está disponible para Intune y puede accederse al usar las hojas de Intune en [Azure Portal](https://portal.azure.com/).
La nueva experiencia le permite describir el problema con sus propias palabras y recibir información sobre solución de problemas y contenido de corrección basado en la Web. Estas soluciones se ofrecen mediante un algoritmo de aprendizaje automático con reglas, basado en las consultas de los usuarios. Además de instrucciones específicas del problema, también puede usar el nuevo flujo de trabajo de creación de casos para abrir una incidencia de soporte técnico por teléfono o correo electrónico. Esta nueva experiencia reemplaza a la experiencia de ayuda y soporte técnico anterior de un conjunto estático de opciones seleccionadas previamente que se basan en el área de la consola en la que se encuentra cuando abre la sección Ayuda y soporte técnico. Para obtener más información, vea [Cómo obtener asistencia para Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="scope-tags-for-apps----1081941---"></a>Etiquetas de ámbito para las aplicaciones <!-- 1081941 -->
Puede crear etiquetas de ámbito para limitar el acceso a roles y aplicaciones. Puede agregar una etiqueta de ámbito a una aplicación para que solo los usuarios con roles que también tengan asignada esa etiqueta de ámbito puedan acceder a la aplicación. Actualmente, no es posible asignar etiquetas de ámbito a las aplicaciones que se agregan a Intune desde Google Play administrado o a aquellas que se compran mediante el Programa de Compras por Volumen de Apple (VPP), si bien será posible en el futuro. Para obtener más información, vea [Uso de etiquetas de ámbito para filtrar directivas](scope-tags.md).

## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
