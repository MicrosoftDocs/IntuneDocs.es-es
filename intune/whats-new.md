---
title: Novedades de Microsoft Intune (Azure) | Microsoft Docs
titleSuffix: ''
description: Descubra las novedades del portal de Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/31/2019
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
ms.openlocfilehash: 72b96714e8740fe4077583cfa5d9f148c2ee0908
ms.sourcegitcommit: f41b22f65286a64a8002e2cbe80debfdd6692278
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66469588"
---
# <a name="whats-new-in-microsoft-intune"></a>Novedades de Microsoft Intune

Conozca las novedades semanales de Microsoft Intune. También encontrará información sobre [próximos cambios](in-development.md), [notificaciones importantes](#notices) e información sobre [versiones anteriores](whats-new-archive.md). 

> [!Note]
> Algunas características pueden lanzarse a lo largo de varias semanas y pueden no estar disponibles para todos los clientes durante la primera semana.

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

<!-- ########################## -->

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

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359-idready-wnready--"></a>Método de autenticación de actualizaciones de directivas de Intune e instalación de aplicaciones de Portal de empresa  <!-- 1927359 idready wnready-->
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

#### <a name="intune-management-extension-powershell-scripts-----3734186-idready---"></a>Scripts de PowerShell de extensión de administración de Intune  <!-- 3734186 idready -->
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

####  <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Tareas de seguridad de Intune para ATP de Defender (en versión preliminar pública)     <!-- 3208597 -->
En la versión preliminar pública, puede usar Intune para administrar las tareas de seguridad para Protección contra amenazas avanzada (ATP) de Microsoft Defender. Esta integración con ATP agrega un enfoque basado en riesgos para detectar vulnerabilidades y errores de configuración de puntos de conexión, establecer su prioridad y corregirlos, a la vez que reduce el tiempo entre la detección y la mitigación.

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

####  <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Línea de base de Protección contra amenazas avanzada de Microsoft Defender (versión preliminar)  <!--  3754134 -->
Agregamos una versión preliminar de línea de base de seguridad para la configuración [Protección contra amenazas avanzada de Microsoft Defender](security-baseline-settings-defender-atp.md). Esta línea de base está disponible cuando el entorno cumple con los requisitos previos para usar [Protección contra amenazas avanzada de Windows Defender](advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Inscripción de dispositivos

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>La página Estado de inscripción (ESP) de Windows ya está disponible con carácter general <!-- 3605348 -->
La página Estado de inscripción dejó de estar en versión preliminar. Para más información, consulte [Configurar una página de estado de inscripción](windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Actualización de la interfaz de usuario de Intune: creación de un perfil de inscripción de Autopilot  <!-- 4593669 -->
La interfaz de usuario para crear un perfil de inscripción de Autopilot se actualizó para alinearla con los estilos de interfaz de usuario de Azure. Para más información, consulte cómo [crear un perfil de inscripción de Autopilot](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile). Más adelante, se actualizarán más escenarios de Intune a este nuevo estilo de interfaz de usuario.

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
- Integre BIG-IP con Intune para NAC. Los pasos se describen en [Overview: Configuring APM for device posture checks with endpoint management systems](https://support.f5.com/kb/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) (Información general: Configuración de APM para comprobaciones de posición del dispositivo con sistemas de administración de puntos de conexión).
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

#### <a name="device-overview-shows-primary-user---794259----"></a>Usuario primario mostrado en Resumen del dispositivo <!--794259  -->
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
- Bloquear o permitir que los usuarios [busquen actualizaciones de Windows](windows-update-settings.md#block-user-from-scanning-for-windows-updates).
- Administrar el [nivel de notificación de Windows Update](windows-update-settings.md#windows-update-notification-level) que los usuarios pueden ver.

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

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470--wnstaged--"></a>Configuración del perfil para omitir algunas pantallas durante el Asistente para configuración <!-- 2276470  wnstaged-->
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

> [!Note]
> Esta característica aún no se ha implementado por completo para todos los clientes. Si no puede usar el Portal de empresa en dispositivos inscritos de forma masiva, tendrá que esperar a que este cambio se implemente en su cuenta.

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

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>Asignar certificados SCEP en un dispositivo macOS sin usuarios  <!-- 2340521  -->
Puede asignar los certificados del Protocolo de inscripción de certificados simple (SCEP) mediante los atributos del dispositivo para dispositivos macOS, incluidos los dispositivos sin afinidad de usuario y asociar el perfil de certificado con perfiles de Wi-Fi o VPN. Esto amplía la compatibilidad que ya tenemos para [asignar certificados del SCEP a dispositivos con y sin afinidad de usuario](certificates-scep-configure.md#create-a-scep-certificate-profile) que tienen instalado Windows, iOS y Android.  Esta actualización agrega la opción de seleccionar un tipo de certificado de *Dispositivo* al configurar un perfil de certificado SCEP para macOS.

Se aplica a: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Actualización de la interfaz de usuario de acceso condicional de Intune   <!-- 2432313   -->
Hemos realizado mejoras en la interfaz de usuario para el acceso condicional en la consola de Intune. Entre ellos se incluyen los siguientes:
-  Hemos reemplazado la hoja *Acceso condicional* de Intune con la hoja de Azure Active Directory. Esto garantiza que tendrá acceso a toda la gama de opciones y configuraciones para el [acceso condicional](conditional-access.md) (que sigue siendo una tecnología de Azure AD) desde la consola de Intune. 
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

Estas son algunas de las nuevas características: 

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
-  **Estado del servicio Intune**: muestra detalles sobre incidentes activos o interrupciones del inquilino. La información de esta sección se obtiene directamente del Centro de mensajes de Office.
-  **Noticias de Intune**: muestra mensajes activos para el inquilino. En estos mensajes, se incluyen notificaciones cuando el inquilino recibe las características de Intune más recientes.  La información de esta sección se obtiene directamente del Centro de mensajes de Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Nueva experiencia de ayuda y soporte técnico en el Portal de empresa para Windows 10 <!-- 1488939-->
La nueva página de ayuda y soporte técnico del Portal de empresa ayuda a los usuarios a solucionar problemas y solicitar ayuda para problemas de acceso y de aplicaciones. Desde la nueva página, puede enviar por correo electrónico detalles de registros de diagnóstico y errores, así como obtener los detalles del departamento de soporte técnico de su organización. También encontrará una sección de preguntas más frecuentes con vínculos a la documentación de Intune relevante. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Nueva experiencia de ayuda y soporte técnico para Intune   <!-- #3307080 -->
Implementaremos la nueva experiencia de ayuda y soporte técnico a todos los inquilinos en los próximos días. Esta experiencia está disponible para Intune y puede accederse al usar las hojas de Intune en [Azure Portal](https://portal.azure.com/).
La nueva experiencia le permite describir el problema con sus propias palabras y recibir información sobre solución de problemas y contenido de corrección basado en la Web. Estas soluciones se ofrecen mediante un algoritmo de aprendizaje automático con reglas, basado en las consultas de los usuarios. Además de instrucciones específicas del problema, también puede usar el nuevo flujo de trabajo de creación de casos para abrir una incidencia de soporte técnico por teléfono o correo electrónico. Esta nueva experiencia reemplaza a la experiencia de ayuda y soporte técnico anterior de un conjunto estático de opciones seleccionadas previamente que se basan en el área de la consola en la que se encuentra cuando abre la sección Ayuda y soporte técnico. Para obtener más información, vea [Cómo obtener asistencia para Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Control de acceso basado en roles

#### <a name="scope-tags-for-apps----1081941---"></a>Etiquetas de ámbito para las aplicaciones <!-- 1081941 -->
Puede crear etiquetas de ámbito para limitar el acceso a roles y aplicaciones. Puede agregar una etiqueta de ámbito a una aplicación para que solo los usuarios con roles que también tengan asignada esa etiqueta de ámbito puedan acceder a la aplicación. Actualmente, no es posible asignar etiquetas de ámbito a las aplicaciones que se agregan a Intune desde Google Play administrado o a aquellas que se compran mediante el Programa de Compras por Volumen de Apple (VPP), si bien será posible en el futuro. Para obtener más información, vea [Uso de etiquetas de ámbito para filtrar directivas](scope-tags.md).

<!-- ########################## -->
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

<!-- ########################## -->
## <a name="week-of-november-26-2018"></a>Semana del 26 de noviembre de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Desinstalación de aplicaciones en dispositivos iOS supervisados corporativos <!-- 1281677 -->

Puede quitar cualquier aplicación en dispositivos iOS corporativos supervisados. Puede quitar cualquier aplicación estableciendo como destino grupos de usuarios o dispositivos con un tipo de asignación **Desinstalar**. Para dispositivos iOS personales o no supervisados, podrá quitar solo las aplicaciones que se instalaron mediante Intune.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Descarga de contenido de aplicaciones Win32 de Intune <!-- 2617320 -->
Los clientes Windows 10 RS3 y versiones posterior descargarán contenido de aplicaciones Win32 de Intune mediante un componente de Optimización de distribución del cliente Windows 10. La Optimización de distribución proporciona la funcionalidad punto a punto está activada de manera predeterminada. Actualmente, la Optimización de distribución se puede configurar según la directiva de grupo. Para más información, consulte el artículo sobre la [Optimización de distribución para Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menú de contenido de aplicaciones y dispositivos del usuario final <!-- 2771453 -->
Los usuarios finales ahora pueden usar el menú contextual del dispositivo y las aplicaciones para desencadenar acciones comunes, como cambiar el nombre de un dispositivo o comprobar el cumplimiento.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Establecer un fondo personalizado en la aplicación Managed Home Screen  <!-- 3041945 -->
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

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Seleccionar las aplicaciones de las que se realiza un seguimiento en la página de estado de la inscripción<!-- 2531007 -->
Puede elegir de qué aplicaciones se realiza un seguimiento en la página de estado de la inscripción. El usuario no puede usar el dispositivo hasta que se instalen estas aplicaciones. Para más información, consulte [Configurar una página de estado de inscripción](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Búsqueda del dispositivo Autopilot por número de serie <!--2595788 -->
Ahora puede buscar dispositivos Autopilot por número de serie. Para hacerlo, elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos** > escriba un número de serie en el cuadro **Buscar por número de serie** > presione ENTRAR.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Seguimiento de la instalación de Office Pro Plus <!--2620217 -->
Los usuarios pueden realizar un seguimiento del progreso de instalación de [Office ProPlus](apps-add-office365.md) en la [página de estado de la inscripción](windows-enrollment-status.md). Para más información, consulte [Configurar una página de estado de inscripción](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas sobre tokens de VPP que expiran próximamente o licencias del Portal de empresa a punto de agotarse <!-- 2237572 -->
Si usa el Programa de Compras por Volumen (VPP) para tener en servicio el Portal de empresa durante la inscripción de DEP, Intune le avisará cuando el token de VPP esté a punto de expirar y las licencias del Portal de empresa se estén agotando.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Compatibilidad del Programa de inscripción de dispositivos macOS para cuentas de Apple School Manager <!--3006133 -->
Intune permite usar el Programa de inscripción de dispositivos en dispositivos macOS para las cuentas de Apple School Manager.  Para más información, consulte el artículo sobre la [inscripción automática de dispositivos macOS con el Programa de inscripción de dispositivos de Apple o Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="new-intune-device-subscription-sku---3312071--"></a>Nueva SKU de suscripción a dispositivos de Intune <!--3312071-->
Para ayudar a reducir el costo de administración de dispositivos en las empresas, ahora tiene a su disposición una nueva SKU de suscripción basada en dispositivos. Las licencias de esta SKU de dispositivos de Intune se conceden mensualmente por dispositivo. El precio varía según el programa de licencias. Está disponible directamente mediante el centro de administración de Microsoft 365 y el [Contrato Enterprise](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), el [contrato de productos y servicios de Microsoft](https://www.microsoft.com/licensing/mpsa/default) (MPSA), los [contratos abiertos de Microsoft ](https://partner.microsoft.com/licensing/licensing-agreements) y los [proveedores de soluciones en la nube](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### <a name="device-management"></a>Administración de dispositivos

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Detener temporalmente el modo de pantalla completa en dispositivos Android para realizar cambios <!-- 3041935 -->
Al usar dispositivos Android en modo quiosco con varias aplicaciones, puede que un administrador de TI deba realizar cambios en el dispositivo. Esta actualización incluye una configuración nueva de pantalla completa con varias aplicaciones que permite que un administrador de TI pause de manera temporal la pantalla completa con un PIN y obtener acceso a todo el dispositivo.
Para ver la configuración de pantalla completa, consulte las [restricciones de los dispositivos Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Habilitar el botón de inicio virtual en dispositivos Android Enterprise en pantalla completa  <!-- 3042021 -->
Una nueva configuración permitirá a los usuarios pulsar un botón de tecla programable en su dispositivo para cambiar entre la aplicación Managed Home Screen y otras aplicaciones asignadas en su dispositivo de quiosco con varias aplicaciones asignadas. Esta configuración es especialmente útil en escenarios donde una aplicación de quiosco del usuario no responde correctamente al botón "Atrás". Podrá configurar esta opción para dispositivos Android corporativos de un solo uso. Para habilitar o deshabilitar el **botón de inicio virtual**, vaya a Intune en Azure Portal > Configuración del dispositivo. Seleccione un perfil de configuración del dispositivo actual o cree uno para editar su configuración de quiosco.
Para ver la configuración de pantalla completa, consulte las [restricciones de los dispositivos Android Enterprise](device-restrictions-android-for-work.md).

<!-- ########################## -->
## <a name="week-of-november-12-2018"></a>Semana del 12 de noviembre de 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Compatibilidad del control de acceso de red (NAC) con Citrix SSO para iOS <!-- 3259404 -->

Citrix lanzó una actualización para Citrix Gateway para permitir el control de acceso de red (NAC) para Citrix SSO para iOS en Intune. Puede optar por incluir un identificador de dispositivo en un perfil de VPN en Intune y luego insertar este perfil en los dispositivos iOS. Deberá instalar la actualización más reciente de Citrix Gateway para usar esta funcionalidad.

[Configuración de VPN en dispositivos iOS](vpn-settings-ios.md#base-vpn-settings) proporciona más información sobre el uso de NAC, incluidos algunos requisitos adicionales. 

<!-- ########################## -->
## <a name="week-of-november-5-2018"></a>Semana del 5 de noviembre de 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Compatibilidad con OAuth de iOS 12 en perfiles de correo electrónico de iOS <!--2155106 -->

Los perfiles de correo electrónico iOS de Intune son compatibles con Open Authorization (OAuth) para iOS 12. Para ver esta característica, cree un perfil (**Configuración del dispositivo** > **Perfiles** > **Crear perfil** > **iOS** como plataforma > **Correo electrónico** como tipo de perfil) o actualice un perfil de correo electrónico iOS existente. Si habilita OAuth en un perfil que ya se ha implementado en los usuarios, se les pedirá que se vuelvan a autenticar y que vuelvan a descargar su correo electrónico.

En [Perfiles de correo electrónico iOS](email-settings-ios.md) hay más información sobre cómo usar OAuth en un perfil de correo electrónico.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Compatibilidad con Autopilot para dispositivos híbridos unidos a Azure Active Directory (versión preliminar) <!-- 1048100-->
Ahora puede configurar dispositivos híbridos unidos a Azure Active Directory mediante AutoPilot. Los dispositivos deben estar unidos a la red de la organización para usar la característica de AutoPilot híbrida. Para más información, vea [Implementar dispositivos unidos a Azure AD híbrido mediante Intune y Windows Autopilot (versión preliminar)](windows-autopilot-hybrid.md).
Esta característica se implementará en toda la base de usuarios durante los próximos días. Por tanto, es posible que no pueda seguir estos pasos hasta que se implemente en su cuenta.

<!-- ########################## -->
## <a name="week-of-october-29-2018"></a>Semana del 29 de octubre de 2018

### <a name="app-management"></a>Administración de aplicaciones

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Solicitar PIN que no sea biométrico después de un tiempo de expiración especificado <!-- 1506985 -->
Al exigir un número de identificación personal no biométrico después de transcurrir un tiempo de expiración especificado por el administrador, Intune proporcionará una mayor seguridad para las aplicaciones compatibles con Administración de aplicaciones de móviles (MAM), ya que restringe el uso de identificación biométrica para el acceso a datos corporativos. La configuración afectará a los usuarios que dependen de Touch ID (iOS), Face ID (iOS), Android Biometric u otros métodos de autenticación biométrica futuros para tener acceso a aplicaciones compatibles con APP/MAM. Con esta configuración, los administradores de Intune tendrán un control más exhaustivo del acceso de los usuarios. De este modo, se evitan situaciones en las que un dispositivo con varias huellas digitales u otros métodos de acceso biométrico pueda revelar datos corporativos a un usuario incorrecto. En Azure Portal, abra **Microsoft Intune**. Seleccione **Aplicaciones cliente** > **Directivas de protección de aplicaciones** > **Agregar una directiva** > **Configuración**. En la **Acceso** encontrará ajustes específicos. Para obtener información sobre la configuración del acceso, vea la [configuración para iOS](app-protection-policy-settings-ios.md#access-requirements) y la [configuración para Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Configuración de transferencia de datos de APP de Intune en dispositivos iOS inscritos en MDM <!-- 2244713 -->
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

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Eliminación de un perfil de correo electrónico de un dispositivo, incluso cuando solo hay un perfil <!-- 1818139 -->
Antes no se podía quitar un perfil de correo electrónico de un dispositivo *si* era el único perfil de correo electrónico. Con esta actualización, se ha cambiado este comportamiento y ahora se puede quitar un perfil de correo electrónico aunque sea el único perfil de este tipo del dispositivo. Vea [Configuración del correo electrónico en Microsoft Intune](email-settings-configure.md) para obtener más información.

#### <a name="powershell-scripts-and-aad----2309469---"></a>Scripts de PowerShell y AAD <!-- 2309469 -->
Los scripts de PowerShell en Intune pueden estar dirigidos a grupos de seguridad de dispositivos de AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nueva configuración predeterminada "Tipo de contraseña requerida" para Android, Android Enterprise<!-- 2649963 -->
Al crear una directiva de cumplimiento (**Intune** > **Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Android** o **Android Enterprise** para Plataforma > Seguridad del sistema), el valor predeterminado de **Tipo de contraseña requerida** cambiará:

Desde: Valor predeterminado del dispositivo Hasta: Al menos numérica

Se aplica a: Android, Android Enterprise

Para ver esta configuración, vaya a [Android](compliance-policy-create-android.md) y [Android Enterprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Usar una clave precompartida en un perfil de Wi-Fi de Windows 10 <!-- 2662938 -->
Con esta actualización, puede usar una clave precompartida (PSK) con el protocolo de seguridad WPA o WPA2-Personal para autenticar un perfil de configuración de Wi-Fi para Windows 10. También puede especificar la configuración de costo para una red de uso medido para la actualización del 10 de octubre de 2018 en dispositivos Windows 10.

Actualmente, debe importar un perfil de Wi-Fi o crear un perfil personalizado para usar una clave precompartida. [Configuración de Wi-Fi para Windows 10](wi-fi-settings-windows.md) muestra la configuración actual. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Eliminación de certificados PKCS y SCEP de los dispositivos <!-- 3218390 -->
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
#### <a name="new-settings-for-software-updates------1907869---"></a>Nuevas configuraciones para actualizaciones de software   <!-- 1907869 -->  
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


<!-- ########################## -->
## <a name="week-of-october-15-2018"></a>Semana del 15 de octubre de 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Solicitud de PIN al cambiar las huellas digitales o Face ID en un dispositivo iOS  <!-- 2637704  -->
Ahora se solicitará a los usuarios un PIN después de realizar cambios biométricos en su dispositivo iOS. Esto incluye cambios en las huellas digitales o los identificadores de cara registrados. El tiempo de la solicitud depende de la configuración del tiempo de espera de *Recheck access requirements after (minutes)* (Volver a comprobar los requisitos de acceso después de [minutos]).  Cuando no se establece ningún PIN, se solicita al usuario que establezca uno. 
 
Esta característica solo está disponible para iOS y requiere la participación de aplicaciones que integran Intune APP SDK para iOS, versión 9.0.1 o posterior. La integración del SDK es necesaria para que se pueda aplicar el comportamiento en las aplicaciones de destino. Esta integración ocurre de manera gradual y depende de los equipos de la aplicación específica. Algunas de las aplicaciones que participan son WXP, Outlook, Managed Browser y Yammer.


<!-- ########################## -->
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

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Implementación de aplicaciones Windows 10 con Intune <!-- 2309001 -->
Aprovechando la compatibilidad actual con aplicaciones de línea de negocio (LOB) y Microsoft Store para aplicaciones empresariales, los administradores pueden usar Intune para implementar la mayoría de las aplicaciones existentes de su organización a los usuarios finales en dispositivos Windows 10. Los administradores pueden agregar, instalar y desinstalar aplicaciones para los usuarios de Windows 10 en una variedad de formatos, como archivos MSI, Setup.exe o MSP. Intune evaluará las reglas de requisitos antes de realizar la descarga y la instalación, y notificará a los usuarios finales del estado o los requisitos de reinicio a través del Centro de actividades de Windows 10. Esta función desbloqueará de manera eficaz las organizaciones interesadas en el desplazamiento de esta carga de trabajo a Intune y la nube. Esta característica está actualmente en versión preliminar pública y esperamos poder agregarle nuevas funciones importantes en los próximos meses. 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Configuración de directiva de protección de la aplicación (APP) de datos web <!-- 2662995 -->
La configuración de directiva APP de contenido web en dispositivos iOS y Android se actualizará para controlar mejor los vínculos web http y https, así como la transferencia de datos a través de vínculos universales de iOS y vínculos de aplicación de Android. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menú de contenido de aplicaciones y dispositivos del usuario final <!-- 2771453 -->
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
Apple Business Manager (ABM) funciona en Intune, así que puede actualizar su cuenta desde el Programa de inscripción de dispositivos (DEP) a ABM. El proceso en Intune es el mismo. Para actualizar la cuenta de Apple de DEP a ABN, vaya a [ https://support.apple.com/HT208817]( https://support.apple.com/HT208817).

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Pestañas de estado de alerta e inscripción en la página de información general de inscripción de dispositivos <!--2748656-->
Ahora, las alertas y los errores de inscripción aparecen en pestañas distintas en la página de información general de inscripción de dispositivos.

### <a name="device-management"></a>Administración de dispositivos

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Restricción de aplicaciones y bloqueo del acceso a los recursos de la compañía dispositivos Android <!-- 2451462  -->  
En **Conformidad de dispositivos** > **Directivas** > **Crear directiva** > **Android**  >  **Seguridad del sistema**, hay un nuevo valor en la sección *Seguridad del dispositivo* que se llama **Aplicaciones restringidas**. El valor **Aplicaciones restringidas** usa una directiva de cumplimiento para bloquear el acceso a recursos de la compañía si ciertas aplicaciones están instaladas en el dispositivo. El dispositivo se considera no compatible hasta que las aplicaciones restringidas se quitan del dispositivo.
Se aplica a: 
- Android

<!-- ########################### -->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
