---
title: Versiones anteriores | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d3305d9938244f0da769dc547cd7a42d7ef81ed
ms.openlocfilehash: 996198a2525dc830d229e7143afda3c71f4276b8


---

# Versiones anteriores de Intune
## Agosto de 2016
## Agosto de 2016
## Administración de aplicaciones
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

### Aplicaciones para iOS 9.3 ocultas y visibles
En dispositivos supervisados con iOS 9.3 o versiones posteriores, puede usar la lista de aplicaciones ocultas y visibles de la directiva de configuración general de iOS para:
- Especificar una lista de las aplicaciones ocultas para los usuarios. Los usuarios no pueden ver ni iniciar estas aplicaciones.
- Especificar una lista de las aplicaciones que los usuarios pueden ver e iniciar. No se puede ver ni iniciar ninguna otra aplicación.

En las aplicaciones que puede especificar, se incluyen las dos aplicaciones que ha implementado, así como las aplicaciones iOS integradas, como Mensajes y Notas. Para obtener más información, vea [Configuración de directivas de iOS en Microsoft Intune]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune).
<!---TFS 1279009 checked--->
### Directiva de aplicaciones permitidas y bloqueadas para dispositivos Samsung KNOX
Ahora puede configurar una directiva personalizada para dispositivos Samsung KNOX que permite crear una de las siguientes listas:
- Una lista de aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo. Aunque se instale, una aplicación incluida en esta lista no se puede activar en el dispositivo.
- Una lista de aplicaciones que los usuarios del dispositivo pueden instalar desde la tienda Google Play. Desde la tienda no se puede instalar ninguna otra aplicación.

Esta configuración solo se puede usar en dispositivos que ejecutan Samsung KNOX.
Para obtener más información, vea [Usar directivas personalizadas para permitir y bloquear aplicaciones en los dispositivos Samsung KNOX]( custom-policy-to-allow-and-block-samsung-knox-apps.md).
<!---TFS 1311629 checked --->
### Nuevas aplicaciones compatibles con las directivas de administración de aplicaciones móviles (MAM).
La aplicación Yammer para [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) y [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) es compatible ahora con las [directivas de administración de aplicaciones móviles (MAM) de Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), independientemente de si el dispositivo está inscrito o no.

Para ver una lista completa de aplicaciones compatibles con MAM, consulte el sitio de los [asociados de aplicaciones de Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

### Aplicaciones de visor de Intune
Con el lanzamiento de la nueva aplicación RMS sharing, quitaremos las siguientes aplicaciones de visor de Intune a partir de agosto de 2016:
- Visor de AV de Intune
- Visor de PDF de Intune
- Visor de imágenes de Intune para Android de Google Play

En lugar de usar las aplicaciones de visor de Intune, se recomienda usar la nueva aplicación [Rights Management (RMS sharing) para Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app), que permite implementar una aplicación en lugar de tres aplicaciones independientes para ver archivos corporativos de forma segura en dispositivos Android. Cuando ya no se admita la aplicación de visor de Intune, se quitará de Google Store y no estará disponible para su uso futuro.

## Administración de dispositivos
### Compatibilidad con Android 7.0
Intune proporciona soporte desde el primer momento para el próximo sistema operativo Android 7.0 para dispositivos móviles.
<!---TFS 1262053--->
### Eliminación por parte de Google de la capacidad de restablecimiento de la contraseña remota en dispositivos Android 7.0
Google ha decidido eliminar la capacidad de los administradores de TI y los usuarios finales para restablecer la contraseña de dispositivos Android 7.0 de forma remota. Anteriormente, los administradores de TI podían restablecer de forma remota la contraseña de un usuario y los usuarios finales podían restablecer sus contraseñas desde el sitio web de Portal de empresa.



## Actualizaciones del portal de empresa
### Sitio web del Portal de empresa
- **Vínculo de comentarios del Portal de empresa a Microsoft** <br/>
El sitio web de Portal de empresa permite a los usuarios finales pulsar un nuevo vínculo "Comentarios", situado en la parte inferior de la página, para enviar comentarios a Microsoft sobre su experiencia en el sitio. Los comentarios recopilados y anónimos ayudan a Microsoft a mejorar la experiencia de los usuarios en el sitio web de Portal de empresa.
<!--- TFS 1313657 checked--->

### iOS
- **Versión mínima de Managed Browser para iOS actualizada a 8.0**<br/>
La aplicación Microsoft Intune Managed Browser para iOS se ha actualizado para admitir los dispositivos que ejecutan iOS 8.0 o versiones posteriores. Aunque que los dispositivos con iOS 7.1 todavía podrán usar la aplicación Managed Browser existente, anime a sus usuarios a actualizar a iOS 8.0 o versiones posteriores para tener acceso y aprovechar las nuevas características de Managed Browser.  
<!---TFS 1313253 checked--->

## Próximas novedades

### Compatibilidad con iOS 10
Intune será totalmente compatible con iOS 10. Tras el lanzamiento de iOS 10 se proporcionará más información.

### Transición de grupos de Intune a grupos de Azure Active Directory a partir de septiembre de 2016
Intune está creando una nueva experiencia de administración de grupos que usa grupos de seguridad de Azure Active Directory (AAD) como grupos de usuarios y dispositivos en Intune. Estos grupos se usarán para toda las administración de grupos, implementación de directivas e implementación de perfil **cuando presentemos el nuevo portal de administración de Intune basado en Azure**.

Esta nueva experiencia evitará tener que duplicar grupos entre servicios, **permitirá el acceso a algunas nuevas características de grupo de Azure Active Directory Premium (AADP)** y proporcionará extensibilidad con PowerShell y Graph. Esto también unificará la experiencia de administración de grupo a través de la administración de movilidad empresarial.

Para habilitar el movimiento a grupos de seguridad, la experiencia en la **consola de administración actual** sufrirá algunas modificaciones. **Estos cambios, y el uso de grupos de seguridad AAD, se registrarán en la documentación de Intune**.

Los clientes que son nuevos en Intune verán **algunos de los cambios de grupos de seguridad antes que los inquilinos actuales**.

Además de los cambios en la administración de grupos, **la siguiente funcionalidad dejará de utilizarse**:
- Excluir miembros o grupos al crear un nuevo grupo
- Grupos **Usuarios desagrupados** y **Dispositivos desagrupados**
- **Administrar grupos** en el rol de administrador de servicios
- Alertas personalizadas basadas en grupos para reglas de notificación
- Dinamizar con grupos en informes
<!--- TFS 1295329--->

### Adición de 'Notificaciones' al Portal de empresa para Android
Vamos a lanzar una actualización en el Portal de empresa para Android en septiembre que presentará un nuevo icono de **Notificaciones** en la página principal. Pulse este icono para acceder a la página **Notificaciones** que mostrará al usuario final todos los elementos que requieren atención en la aplicación Portal de empresa, como no cumplimiento de dispositivos, actualización de inscripciones y activación de inscripciones. Si también usa la aplicación de Portal de la compañía de iOS, ya verá la experiencia de notificaciones. Con la introducción de la página **Notificaciones**, no verá la página **Configuración de acceso a la empresa** cada vez que inicia o reanuda el Portal de empresa para Android, siempre que el dispositivo ya esté inscrito. Tenemos conocimiento de que muchos usuarios han creado una guía para el usuario final y agradecemos que nos avisen por adelantado cuando la guía y las capturas de pantalla necesiten actualizarse. Actualice la documentación para reflejar el próximo cambio en la experiencia. Busque las capturas de pantalla actualizadas en https://aka.ms/androidcpupdate.  

### Mejoras en cómo los usuarios finales de iOS obtienen sus aplicaciones
Los siguientes cambios se realizarán en septiembre en los iconos de aplicaciones en la aplicación de portal de empresa para iOS para que apunte a los usuarios a distintas vistas en una única ubicación, el sitio web de portal de empresa, para todas sus aplicaciones. Actualmente, las restricciones de Apple prohíben que se muestren la línea de negocio y las aplicaciones de la tienda de aplicaciones administrada en la aplicación de portal de empresa de la tienda y requieren a los usuarios visitar vistas diferentes para encontrar todas sus aplicaciones.

- El icono de **aplicaciones de empresa** actualmente apunta a una lista de todas las aplicaciones en la pestaña TODO del sitio web del portal de empresa y seguirá funcionando del mismo modo. El nombre de icono cambiará a **Todas las aplicaciones**.
- El icono **Otras aplicaciones** apunta actualmente a una vista, dentro de la aplicación de portal de empresa, que enumera todas las aplicaciones que Apple permite mostrar a la aplicación de portal de empresa. El nombre de icono cambiará a **Aplicaciones destacadas**, y si pulsa en el icono, se le dirigirá a la pestaña DESTACADOS del sitio web del portal de empresa.
-  El icono **Categorías** apunta actualmente a una vista, dentro del portal de empresa, que enumera las categorías de aplicaciones. No se cambiará el nombre del icono, pero ahora apuntará a la pestaña CATEGORÍAS del sitio web del portal de empresa. Puede encontrar las capturas de pantalla actualizadas [aquí](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

### Guía básica de la nube
Manténgase informado sobre los próximos desarrollos para Intune con la [Guía básica de Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Degradación del servicio
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Cambios en la compatibilidad de la aplicación de Portal de empresa de iOS**<br/>
En septiembre, todos los usuarios de la aplicación Portal de empresa de Microsoft Intune para iOS deberán usar la versión más reciente. Los nuevos usuarios solo podrán descargar la versión más reciente y se pedirá a los usuarios actuales que la actualicen. La versión más reciente requiere iOS 8.0 o posterior, de modo que los dispositivos que ejecuten versiones anteriores de iOS no podrán usar el portal de empresa ni inscribirse hasta que se actualicen a iOS 8.0 o posterior y, luego, se actualice la aplicación de portal de empresa a la versión más reciente. Los dispositivos inscritos que ejecuten versiones anteriores a iOS 8.0 seguirán administrándose y apareciendo en la consola de administración de Intune.  

- **Versión mínima de Managed Browser para iOS actualizada a 8.0**<br/>
En agosto, Intune publicará una aplicación Microsoft Intune Managed Browser actualizada para iOS que solo admitirá los dispositivos que ejecuten iOS 8.0 o posterior. Aunque que los dispositivos con iOS 7.1 todavía podrán usar la aplicación Managed Browser existente, anime a sus usuarios a actualizar a iOS 8.0 o posterior para tener acceso y aprovechar las nuevas características de Managed Browser.  
<!---TFS 1313253--->

- **Las aplicaciones de Portal de la compañía para Windows 8 y Windows Phone 8 se dejarán de usar** <br/>
A partir de octubre de 2016, Microsoft Intune dejará de ofrecer soporte para las aplicaciones de Portal de empresa de Windows 8 y Windows Phone 8. Microsoft Intune también dejará de ofrecer soporte para la plataforma Windows Phone 8. Como consecuencia, no podrá inscribir ni actualizar ningún dispositivo Windows Phone 8. Puede seguir administrando los dispositivos Windows Phone 8 y Windows 8 que ya estén inscritos. Actualice los dispositivos Windows Phone 8 y Windows 8 a Windows 8.1 y Windows Phone 8.1 y use las aplicaciones de portal de empresa de Windows 8.1 y Windows Phone 8.1 correspondientes para poder seguir con la distribución de aplicaciones en estos dispositivos sin interrupciones.
<!---TFS 1255391--->

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->

## Julio de 2016
### Administración de aplicaciones
#### Mejorar la experiencia de actualización de perfil de aprovisionamiento de aplicación
La línea de aplicaciones móviles empresariales de Apple iOS se crea con un perfil de aprovisionamiento incluido y código firmado con un certificado. Cuando la aplicación se ejecuta en un dispositivo iOS, iOS confirma la integridad de la aplicación de iOS y exige el cumplimiento de las directivas definidas por el perfil de aprovisionamiento.

El certificado de firma empresarial que se usa para firmar aplicaciones normalmente tiene una validez de 3 años. Sin embargo, el perfil de aprovisionamiento expira después de 1 año. Con esta actualización, Intune proporciona las herramientas para implementar proactivamente una nueva directiva de perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima mientras siga siendo válido el certificado. Para más información, consulte [Use iOS mobile provisioning profile policies to keep your line of business apps up to date (Usar directivas de perfil de aprovisionamiento móvil iOS para mantener al día sus aplicaciones de línea de negocio)](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->
#### Está disponible el SDK de Xamarin para aplicaciones de Intune
El componente Intune App SDK Xamarin permite habilitar las características de administración de aplicaciones móviles de Intune en las aplicaciones móviles para iOS y Android creadas con Xamarin. Puede encontrar el componente en la [tienda de Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) o en la [página de Github de Microsoft Intune](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### Administración de dispositivos
#### Mayores límites de inscripción de dispositivos
Intune aumentó el límite máximo de inscripción de dispositivos configurables de 5 a 15 dispositivos por usuario.
<!---TFS 1289896 --->

#### Integración de TeamViewer para equipos Windows que ejecutan el software cliente de Intune
La integración de [TeamViewer](https://www.teamviewer.com) para equipos Windows que ejecutan el software cliente de Intune permite establecer sesiones de asistencia remota en equipos Windows como apoyo para departamentos de soporte técnico para usuarios finales. Esto incluye Windows 7, 8, 8.1 y Windows 10. Para obtener más información, vea [Tareas comunes de administración de PC Windows con el cliente de equipo de Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).
<!---TFS 1284856--->

### Actualizaciones del portal de empresa
#### Sitio web del Portal de empresa
- **Experiencia de usuario final mejorada al inscribir dispositivos de Windows**<br/>
Cuando usa acceso condicional, los pasos de inscripción para Windows 8.1, Windows 10 Escritorio y Windows 10 Mobile se han clarificado en el sitio web del Portal de empresa. Los usuarios ahora verán pasos "Inscripción de dispositivos" y "Unión al lugar de trabajo" independientes, lo que les facilita ver el estado de su dispositivo y completar el proceso si experimentan un error en Unión al lugar de trabajo (WPJ). También se espera que los pasos independientes simplifiquen el proceso de solución de problemas para los administradores de TI. Anteriormente, cuando los usuarios finales intentaban inscribirse y todos los pasos de la inscripción se llevaban a cabo correctamente excepto para WPJ, el dispositivo inscrito no aparecería en la lista de dispositivos para los usuarios para identificar, provocando confusión para los usuarios.

#### Android
- **Aplicación Portal de empresa de Android**<br/>
Si los usuarios finales Android ven un mensaje de error que dice que el dispositivo no tiene un certificado necesario, pueden pulsar un botón "Cómo resolver esto" para obtener [pasos](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) para instalar el certificado que falta. Si los usuarios completan los pasos, pero ven un mensaje de error adicional que indica que "falta el certificado", se les solicita que se pongan en contacto con su administrador de TI y proporcionen este [vínculo](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), que contiene pasos que los administradores de TI pueden usar para solucionar el problema del certificado.

- **Restringir instalaciones de aplicaciones de transferencia local a dispositivos inscritos**<br/>
Los dispositivos Android ya no pueden instalar aplicaciones a través del sitio web de Portal de empresa a menos que los dispositivos se hayan inscrito en Intune mediante la aplicación de Portal de empresa de Intune para Android.
<!---TFS 1299082--->

#### iOS
- **Cambios en las cuentas de administradores de inscripción de dispositivos en la aplicación de Portal de empresa de iOS**<br/>
Para mejorar el rendimiento y la escalabilidad, Intune ya no mostrará todos los dispositivos de Administradores de inscripción de dispositivos (DEM) en el panel **Mis dispositivos** de la aplicación de Portal de empresa para iOS. Solo se muestra el dispositivo local que está ejecutando la aplicación y solo si está inscrito a través de la aplicación Portal de empresa.

El usuario de DEM puede realizar acciones en el dispositivo local, pero la administración remota de los demás dispositivos inscritos solo puede realizarse desde la consola de administración de Intune. Además, Intune está dejando de usar las cuentas de DEM con el Programa de inscripción de dispositivos de Apple o con la herramienta Apple Configurator. Estos métodos de inscripción ya admiten la inscripción sin usuarios para los dispositivos iOS compartidos.

Use las cuentas de DEM solo cuando no esté disponible la inscripción sin usuarios para los dispositivos compartidos. Para más información, consulte [Inscribir dispositivos propiedad de la empresa con el Administrador de inscripción de dispositivos de Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### Cambio de nombres de características de Windows
- [Microsoft Passport para Windows](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) ahora se conoce como **Windows Hello para empresas**.
- [Protección de datos de empresa](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) ahora se conoce como **Windows Information Protection**.

## Junio de 2016
### Mantenimiento del servicio de Intune
La información de mantenimiento del servicio de Intune se ha movido a una ubicación central con otros servicios de Microsoft. Ahora encontrará esta información en el portal de administración de Office 365, en Estado del servicio. Para más información, consulte [esta entrada de blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### Administración de aplicaciones
- **Mejoras en la experiencia de configuración de la política de datos de empresa de Windows 10.** Se han realizado mejoras en la experiencia de configuración de directivas de protección de datos de empresa de Windows 10 en relación con la creación de reglas de aplicaciones, la especificación de la definición de límite de red y otras opciones de protección de datos de empresa. Para más información, consulte [Create an enterprise data protection (EDP) policy using Microsoft Intune (Crear una directiva de protección de datos de empresa (EDP) con Microsoft Intune)](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### Administración de dispositivos
- **Configuración de directiva de Windows Defender para la protección ante aplicaciones potencialmente no deseadas.** Se ha agregado una nueva configuración de Windows Defender denominada **Detección de aplicaciones potencialmente no deseadas** a la directiva de configuración general para Windows 10 Escritorio y Mobile. Puede usar esta configuración para proteger los equipos de escritorio de Windows inscritos ante la ejecución de software que Windows Defender ha clasificado como potencialmente no deseado. Puede protegerse contra la ejecución de estas aplicaciones o puede usar el modo auditoría para informar cuando se instale una aplicación potencialmente no deseada. Para más información, consulte [Configuración de directivas de Windows 10 en Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### Acceso condicional
- **Directiva de control de acceso de red de Cisco ISE.**  Los clientes que usen Cisco Identity Service Engine (ISE) 2.1 y también usen Microsoft Intune pueden establecer una directiva de control de acceso de red en ISE.

    Al usar esta directiva, los dispositivos que necesiten conectarse a la red mediante WiFi o VPN deben cumplir las siguientes condiciones antes de que se les permita el acceso:

    * Deben administrarse mediante Intune
    * Deben cumplir todas las directivas de cumplimiento de Intune implementadas

 A los usuarios finales de los dispositivos no conformes se les solicitará que se inscriban y que solucionen cualquier problema de cumplimiento para obtener acceso.
- **Acceso condicional para el explorador.** Puede establecer una directiva de acceso condicional para [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) y [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) de modo que solo se pueda obtener acceso a ellos desde exploradores web compatibles en dispositivos administrados y compatibles con iOS y Android. A los usuarios finales que intenten iniciar sesión en Outlook Web Access (OWA) y en los sitios de SharePoint con dispositivos iOS y Android, se les solicitará que inscriban su dispositivo con Intune así como que solucionen cualquier problema de incumplimiento antes de completar el inicio de sesión.
<!---TFS 1175844--->

- **Dynamics CRM Online admite el acceso condicional.** Puede establecer una directiva de acceso condicional para [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) de modo que solo se pueda tener acceso a este con dispositivos administrados y compatibles con iOS y Android. Los usuarios finales que intenten iniciar sesión en la aplicación móvil de Dynamics CRM en iOS y Android tendrán que inscribirse en Intune y corregir cualquier problema de cumplimiento para poder iniciar sesión.
<!---TFS1295358--->

##Actualizaciones del Portal de empresa

#### Aplicación Portal de empresa de Android

- Cuando los administradores de TI apliquen la nueva directiva "Los dispositivos deben impedir la instalación de aplicaciones de orígenes desconocidos (Android 4.0+)", los usuarios finales con dispositivos de Android 4.0 o posterior verán el mensaje "Debe deshabilitarse la instalación desde orígenes desconocidos". Los usuarios tendrán que ir a **Configuración** > **Seguridad** y desactivar **Orígenes desconocidos**. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener más [información](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) sobre el mensaje y el porqué de desactivar el valor.

- Cuando los administradores de TI apliquen la nueva directiva "Los dispositivos deben tener habilitada la opción "Buscar amenazas de seguridad en el dispositivo" (Android 4.0+)", los usuarios finales con dispositivos de Android 4.0 o posterior verán el mensaje "Buscar amenazas de seguridad en el dispositivo". Los usuarios tendrán que ir a **Configuración** > **Google** > **Seguridad** y activar **Buscar amenazas de seguridad en el dispositivo**. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener más [información](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre el mensaje y el porqué de activar el valor.

- Cuando los administradores de TI apliquen la nueva directiva "La depuración USB debe estar deshabilitada (Android 4.2+)", los usuarios finales con dispositivos de Android 4.2 o posterior verán el mensaje "La depuración USB debe deshabilitarse". Los usuarios tendrán que ir a **Configuración** > **Opciones del desarrollador** y desactivar **Depuración USB**. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener más [información](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) sobre el mensaje y el porqué de desactivar el valor.

- Cuando los administradores de TI apliquen la nueva directiva "Nivel mínimo de revisión de seguridad de Android (Android 6.0+)", los usuarios finales con dispositivos de Android 6.0 o posterior verán el mensaje "Este dispositivo no cumple el nivel mínimo de revisión de seguridad de Android". Los usuarios tendrán que instalar la revisión de seguridad necesaria. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener [información](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre cómo instalar la revisión de seguridad necesaria y ver qué revisión de seguridad tienen instalada en ese momento.

#### Aplicación Portal de empresa de iOS

- Cuando los usuarios finales instalen aplicaciones de línea empresarial, ahora podrán disfrutar una experiencia mejorada de instalación de la aplicación. Si la instalación de la aplicación tarda mucho, los usuarios pueden sincronizar manualmente el dispositivo para forzar que se reanude el proceso de sincronización. Para leer las instrucciones del usuario final, consulte [Sincronizar el dispositivo iOS manualmente](/Intune/EndUser/sync-your-device-manually-ios).

- La aplicación Portal de empresa de Microsoft Intune para iOS se ha actualizado y ahora admite la versión de iOS 8.0 y posteriores. Con esta actualización, los usuarios finales pueden instalar la aplicación Portal de empresa de Microsoft Intune e inscribir nuevos dispositivos en Intune solo si el dispositivo ejecuta la versión de iOS 8.0 o posterior. Los usuarios que ya han inscrito dispositivos que se ejecutan con una versión no compatible de iOS pueden seguir utilizando la aplicación Portal de empresa que está en su dispositivo.


## Mayo de 2016

Todas estas características también son compatibles en las implementaciones híbridas (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea la página sobre las [novedades de implementaciones híbridas](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### Documentación
Le damos la bienvenida a la versión preliminar de [docs.microsoft.com](https://docs.microsoft.com/en-us/intune).
Se trata de una plataforma de contenido completamente nueva y moderna diseñada para facilitarles a los usuarios la comprensión y el uso de Intune.
Para más información sobre todas las características nuevas, vea [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/) (Introducción a docs.microsoft.com).

### Mantenimiento del servicio de Intune
La información de mantenimiento del servicio de Intune se ha movido a una ubicación central con otros servicios de Microsoft. Ahora encontrará esta información en el [portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx) en **Mantenimiento del servicio**.
Para más información, vea [esta entrada de blog](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### Administración de aplicaciones
- **SDK de MAM: Admite la configuración de longitud de PIN.** Podrá especificar la longitud del PIN para las aplicaciones de MAM como si fuera el PIN de un dispositivo. Esto requerirá que los usuarios finales cumplan con las nuevas restricciones que establezca. Verán una pantalla de PIN ligeramente modificada para tener en cuenta la entrada más larga. Para obtener más información, vea [Opciones de configuración de directiva de administración de aplicaciones móviles de Android en Microsoft Intune](android-mam-policy-settings.md) y [Configuración de directiva de administración de aplicaciones móviles iOS](ios-mam-policy-settings.md).

- **Skype Empresarial para iOS y Android.** Ahora puede abordar Skype Empresarial con [MAM sin las directivas de inscripción](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md). Cuando los usuarios inician sesión, se aplican las directivas de MAM.

- **Nuevas aplicaciones disponibles para la administración con directivas de MAM.** Las aplicaciones de Microsoft Word, Excel y PowerPoint para Android ahora pueden asociarse con directivas de MAM en los dispositivos que no están inscritos con Intune. Para ver una lista completa de las aplicaciones compatibles, vaya a la galería de aplicaciones móviles de Microsoft Intune de la página [Microsoft Intune application partners](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) (Socios de aplicaciones de Microsoft Intune).


### Actualizaciones del portal de empresa

#### Aplicación Portal de empresa de Android
- **Notificaciones del sistema para el usuario final:** los usuarios finales ahora verán notificaciones del sistema de la aplicación de portal de empresa de Android cuando inscriban o quiten sus dispositivos desde el portal de empresa.

- **Cambios en las cuentas de administradores de inscripción de dispositivos en la aplicación de portal de empresa Android.** Para mejorar el rendimiento y la escalabilidad, Intune ya no mostrará todos los dispositivos de administradores de inscripción de dispositivos (DEM) en el panel Mis dispositivos de la aplicación de portal de empresa de Android. Solo se muestra el dispositivo local que está ejecutando la aplicación y solo si está inscrito a través de la aplicación Portal de empresa. El usuario de DEM puede realizar acciones en el dispositivo local, pero la administración remota de los demás dispositivos inscritos solo puede realizarse desde la consola de administración de Intune.

#### Sitio web del Portal de empresa
- **Sitio web del portal de empresa: el banner de identificación de dispositivos proporcionará más información a los usuarios finales.** Los usuarios finales ahora pueden identificar más fácilmente el dispositivo que han seleccionado cuando están usando el sitio web del portal de empresa. Si hay seleccionado un dispositivo incorrecto, podrán seleccionar el dispositivo correcto pulsando en el vínculo **Pulsar aquí** en el banner de la página principal.

## Próximas novedades
- **Incorporación de la interfaz de usuario del Centro de mensajes.**. Como parte de la migración de Intune al [Portal de administración de Office 365](https://portal.office.com/), nos aprovecharemos de su Centro de mensajes para comunicar las características nuevas y otras notificaciones. Además, al instalar la aplicación móvil complementaria de administración de Office 365, puede recibir notificaciones en su teléfono móvil y reenviar fácilmente cualquier mensaje a los usuarios o a un alias de distribución.
Empezaremos a usar el Centro de Mensajes con nuestro lanzamiento de mayo para notificarle cuándo se completan las actualizaciones e incluiremos información sobre las características nuevas y mejoradas de Intune. Consulte hoy el Centro de mensajes iniciando sesión en el [portal de administración de Office 365](https://portal.office.com/) y elija la opción CENTRO DE MENSAJES en el panel de navegación izquierdo.

- **Cambios en las cuentas de administradores de inscripción de dispositivos.**. Para mejorar el rendimiento y la escalabilidad, Intune ya no mostrará **todos** los dispositivos de administradores de inscripción de dispositivos (DEM) en el panel **Mis dispositivos** de la aplicación de portal de empresa de iOS. Solo se muestra el dispositivo local que está ejecutando la aplicación y solo si está inscrito a través de la aplicación Portal de empresa. El usuario de DEM puede realizar acciones en el dispositivo local, pero la administración remota de los demás dispositivos inscritos solo puede realizarse desde la consola de administración de Intune. Además, Intune está dejando de usar las cuentas de DEM con el Programa de inscripción de dispositivos de Apple o con la herramienta Apple Configurator. Estos métodos de inscripción ya admiten la inscripción sin usuarios para los dispositivos iOS compartidos. Use las cuentas de DEM solo cuando no esté disponible la inscripción sin usuarios para los dispositivos compartidos.

### Guía básica de la nube
Manténgase informado sobre los próximos desarrollos para Intune con la [Guía básica de Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Degradación del servicio
- **Aplicaciones de visor de Intune.** Con el lanzamiento de la nueva aplicación RMS sharing, quitaremos las siguientes aplicaciones de visor de Intune a partir de agosto de 2016:
    - Visor de AV de Intune
    - Visor de PDF de Intune
    - Visor de imágenes de Intune para Android de Google Play

  En lugar de usar las aplicaciones de visor de Intune, se recomienda usar la nueva aplicación Rights Management (RMS sharing) para Android, que permite implementar una aplicación en lugar de tres aplicaciones independientes para ver archivos corporativos de forma segura en dispositivos Android. Obtenga más información sobre la aplicación RMS sharing (con un vínculo a documentación).

- **Grupo personalizado de destino de retirada de reglas de notificación.**
Las reglas de notificación de Intune definen a quién se enviará una alerta de correo electrónico a través de Intune. Actualmente, puede configurar reglas de notificación para enviar mensajes de correo electrónico a todos los usuarios de dispositivos de un grupo de dispositivos de Intune que haya creado. Aproximadamente a partir del 1 de junio de 2016, ya no se admitirán los grupos creados por el usuario de destino.

    A día de hoy, para que una regla de notificación esté destinada a un grupo creado desde la consola de administración de Microsoft Intune, debe seguir los pasos siguientes:

    En el área de trabajo **Administración**, haga clic en **Reglas de notificación** > **Crear nueva regla**.

    En el paso 2 del Asistente para crear reglas de notificación, se seleccionan los grupos de dispositivos a los que se destinará la regla. Este paso ("Seleccionar grupos de dispositivos") se va a quitar de la consola de Intune.

    La escala de tiempo preliminar de este cambio es la siguiente:
    - En junio de 2016, los nuevos inquilinos no verán el paso 2 del Asistente para crear reglas de notificación. Los inquilinos existentes no se verán afectados.
    - Alrededor de agosto de 2016, algunos inquilinos existentes no verán la opción "Seleccionar grupos de dispositivos" en el asistente.
    - Alrededor de octubre de 2016, se espera que ningún inquilino vea la opción "Seleccionar grupos de dispositivos" en el asistente.


- **Cambios en la compatibilidad de la aplicación de portal de empresa de iOS.**. En los próximos meses, habrá una actualización para la aplicación de portal de empresa de Microsoft Intune para iOS que solo admitirá dispositivos que ejecuten iOS 8.0 o posterior. Los usuarios no podrán inscribir dispositivos nuevos que ejecuten versiones anteriores a iOS 8.0. Los dispositivos inscritos que ejecuten versiones anteriores a iOS 8.0 seguirán administrándose y, durante un tiempo limitado, podrá seguir usando la aplicación de portal de empresa. Pero los dispositivos deben tener iOS 8.0 o posterior para tener acceso a las últimas versiones de la aplicación de portal de empresa. Le recomendamos que notifique a los usuarios que actualicen a iOS 8.0 o posterior para aprovechar las nuevas características de Intune.  


## Abril de 2016
Todas estas características también son compatibles con los clientes híbridos (Configuration Manager integrado con Intune).
### Administración de aplicaciones
- **Compatibilidad de usuario de MAM.**
Ahora puede ver el [estado](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) de sus directivas de administración de aplicaciones para cualquier usuario en el inquilino de Azure Active Directory (AAD). Esto incluye:
   - Dispositivos
   - Aplicaciones del dispositivo

   Valores de estado:

   **Checked in (Comprobado)**: indica que la directiva se implementó para el usuario, y la aplicación se usó en un contexto profesional y recibió correctamente la directiva.

    **Not checked in (No comprobado)**: indica que la directiva se implementó para el usuario, pero la aplicación no se ha usado en un contexto profesional desde entonces.


- **Controles de MAM para evitar la sincronización de contactos de Outlook (Android).**
Hay una nueva opción de configuración disponible para la [administración de aplicaciones móviles](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) sin inscripción de dispositivos. Esta opción permite evitar que una aplicación sincronice contactos con la libreta de direcciones nativa en dispositivos Android. Si esta opción está habilitada, las aplicaciones de destino ya no podrán guardar contactos en la libreta de direcciones nativa. Si esta opción está deshabilitada, las aplicaciones de destino podrán guardar contactos en la libreta de direcciones nativa. Al [borrar un dispositivo o aplicación de forma remota](wipe-managed-company-app-data-with-Microsoft-Intune.md), se quitarán todos los contactos que ya se hayan guardado en la libreta de direcciones nativa. Esta nueva opción es compatible inicialmente con la aplicación Outlook en dispositivos Android.

### Administración de dispositivos
- **Identificación de número de teléfono para dispositivos propiedad de la empresa.** Los teléfonos que están clasificados como "Corporativos" se identifican ahora con el número de teléfono completo, por ejemplo, al ejecutar un informe de inventario de dispositivos móviles. Los números de teléfono BYOD se seguirán enmascarando con ****; y solo se mostrarán los últimos 4 dígitos.


### Actualizaciones de Portal de empresa
**Aplicación de portal de empresa de Android** Los usuarios que no han inscrito su dispositivo en Intune y que no tienen el certificado correcto instalado, no podrán iniciar sesión en la aplicación de portal de empresa de Android y verán el mensaje "No puede iniciar sesión porque falta un certificado necesario en su dispositivo". El mensaje incluye un vínculo "Cómo resolver esto" que los usuarios pueden pulsar para ver instrucciones para instalar el certificado. Para ver los pasos que los usuarios finales siguen para solucionar el problema, vea [Uso de un dispositivo Android con Intune](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**Aplicación de portal de empresa de iOS** Se ha agregado soporte técnico para que la acción de deslizar para actualizar actualice el contenido en la pantalla principal, que incluye aplicaciones y dispositivos enumerados e información de contacto de TI. Las acciones de deslizar para actualizar no comprueban el cumplimiento ni la información de la directiva, que puede realizarse al seleccionar el icono de su dispositivo actual y pulsar el botón **Sincronizar**.

**La aplicación de portal de empresa de Windows 10 Mobile y Windows Phone 8.1** Cuando los usuarios finales instalen aplicaciones de línea empresarial, ahora podrán disfrutar de una experiencia mejorada de instalación de la aplicación. Si la instalación de la aplicación tarda mucho, los usuarios pueden sincronizar manualmente el dispositivo para forzar que se reanude el proceso de sincronización. Para revisar las instrucciones del usuario final, vea [Usar un dispositivo Windows con Intune](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Sitio web de portal de empresa** Cuando los usuarios de Windows 10 Mobile y Windows Phone 8.1 instalen aplicaciones de línea empresarial, ahora podrán disfrutar de los siguientes estados nuevos, que les proporcionan más información sobre el estado de su instalación:

* **Esperando a que se sincronice el dispositivo**: el usuario ha pulsado "Instalar" y el dispositivo ahora se intenta sincronizar mediante la infraestructura de Intune. La sincronización es necesaria antes de que se complete la instalación. El mensaje "Esperando a que se sincronice el dispositivo" también es un vínculo que los usuarios pueden pulsar para ver [instrucciones](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) sobre cómo sincronizar manualmente su dispositivo con Intune si el proceso de sincronización tarda mucho o se detiene.
* **Descargando**: la solicitud de descarga del usuario se está procesando y el dispositivo está descargando e instalando la aplicación.

Antes de que se agregaran estos estados, los usuarios se confundían si una instalación de aplicación tardaba mucho, porque solo veían el estando "Instalando", que puede permanecer en la pantalla durante horas. Al agregar los nuevos estados, en vez de llamar al soporte técnico, los usuarios ahora pueden pulsar el vínculo "Esperando a que se sincronice el dispositivo" y seguir las instrucciones para forzar que se reanude el proceso de sincronización.


## Marzo de 2016
### Novedades a día 29 de marzo de 2016
A excepción de la actualización de la directiva de configuración general de Windows 10, todas las características publicadas el 29 de marzo de 2016 son compatibles con los clientes híbridos (Configuration Manager integrado con Intune). La compatibilidad híbrida con la actualización de la directiva de configuración general de Windows 10 estará disponible próximamente. Tenga en cuenta que algunas de estas características pueden exigir la versión más reciente de Configuration Manager.

### Administración de aplicaciones
- **Controles de administración de aplicaciones móviles (MAM) para evitar la sincronización de contactos de Outlook (iOS).** Hay una nueva opción de configuración disponible para la administración de aplicaciones móviles sin inscripción de dispositivos. Esta opción permite evitar que una aplicación sincronice contactos con la libreta de direcciones nativa en dispositivos iOS. Si esta opción está habilitada, la aplicación ya no podrá guardar contactos en la libreta de direcciones nativa. Si esta opción está deshabilitada, la aplicación podrá guardar contactos en la libreta de direcciones nativa. Al borrar el contenido de un dispositivo de forma selectiva, se quitarán todos los contactos que ya se hayan guardado en la libreta de direcciones nativa. Esta nueva opción es compatible con la aplicación Outlook en dispositivos iOS. Para obtener más detalles sobre esta opción y otras, vea [Crear e implementar directivas MAM](https://technet.microsoft.com/en-us/library/dn292747.aspx).

### Control de acceso
- **Skype Empresarial Online admite el acceso condicional.** Puede definir una directiva de acceso condicional para Skype Empresarial Online de modo que solo se pueda acceder a él mediante dispositivos administrados y compatibles con iOS y Android. A los usuarios finales que intenten iniciar sesión en la aplicación móvil de Skype Empresarial en iOS y Android se les pedirá que se inscriban en Intune y que corrijan los problemas de cumplimiento para poder iniciar sesión. Para obtener detalles, vea [Manage access to Skype for Business Online (Administrar el acceso a Skype Empresarial Online)](https://technet.microsoft.com/en-us/library/mt695297.aspx).

### Administración de dispositivos
- **Soporte técnico de Intune para iOS 9.3.** El lunes 21 de marzo, Apple anunció que iOS 9.3 ya estaba disponible. Hemos estado trabajando sin descanso para garantizar que Microsoft Intune sea compatible con la versión más reciente del sistema operativo para móviles de Apple y [nos complace anunciar que Intune permite la administración de dispositivos con iOS 9.3](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/).

  Todas las características existentes de Intune actualmente disponibles para administrar dispositivos iOS seguirán funcionando sin problemas cuando los usuarios actualicen sus dispositivos a iOS 9.3. Además, iOS 9.3 también es compatible en este momento con los clientes híbridos (Configuration Manager integrado con Intune).

- **La directiva de configuración general de Windows 10 ahora contiene opciones de configuración para administrar Windows Defender en equipos con Windows 10 inscritos.** Para obtener detalles, vea [Windows 10 configuration policy settings in Microsoft Intune (Configuración de directivas de configuración de Windows 10 en Microsoft Intune)](https://technet.microsoft.com/en-us/library/mt404697.aspx).


### Portal de empresa

- **Paquetes de aplicaciones de Windows disponibles directamente desde el sitio web del Portal de empresa.** Los usuarios de equipos con Windows 8, Windows 8.1 y Windows RT ya pueden instalar paquetes de aplicaciones de Windows (con la extensión .appx) directamente desde el sitio web del Portal de empresa. Anteriormente, tenía que implementar (o los usuarios tenían que instalar) la aplicación Portal de empresa en sus dispositivos para instalar aplicaciones.

- **Los usuarios pueden bloquear de forma remota su dispositivo desde el sitio web del Portal de empresa.** Se ha agregado una nueva opción de bloqueo remoto al sitio web del Portal de empresa para permitir que los usuarios bloqueen de forma remota su dispositivo desde el Portal en caso de pérdida o robo. Consulte las [instrucciones para el usuario final](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock). En la tabla siguiente se muestra la compatibilidad de plataforma con el bloqueo remoto para la versión independiente de Intune y para Intune con Configuration Manager.

|Plataforma | Detalles sobre compatibilidad|
|---------|----------------|
|Android |Compatible.|
|iOS |Compatible.|
|Windows 10 Mobile |Compatible únicamente si el teléfono tiene establecido un código de acceso|
|Windows 10 Escritorio |No compatible|
|Windows Phone 8,1 |Compatible únicamente si el teléfono tiene establecido un código de acceso|
|Windows Phone 8.0 |No compatible|
|PC (Windows 8.0 y anteriores) |No compatible|
|PC (Windows 8.1) |No compatible|

### Novedades a día 10 de marzo de 2016

### Administración de aplicaciones

- **Aprovecharse de la administración "Open-in" de iOS para los dispositivos que están inscritos en una solución de MDM de terceros** Puede usar su proveedor de administración de dispositivos móviles (MDM) de terceros para aprovecharse de la administración "Open-in" de iOS. Puede establecer las restricciones en los ajustes del perfil de configuración e implementar la aplicación con [Administrar la transferencia de datos entre aplicaciones iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

     Este enfoque tiene dos ventajas principales:

     1. Los usuarios deben iniciar sesión con su cuenta profesional antes de obtener acceso a los datos corporativos desde otras aplicaciones u otros servicios en la nube. Esto garantiza que las directivas de administración de aplicaciones móviles (MAM) están en vigor cuando se accede a los datos.

     2. Los perfiles de correo electrónico administrados y otras aplicaciones administradas que se han implementado a través de una solución MDM de terceros pueden compartir archivos y datos con las aplicaciones que tengan directivas de MAM de Intune.

- **Administrar la aplicación de Microsoft Outlook con directivas de MAM para los dispositivos que no están inscritos en Intune** Ahora puede administrar la aplicación Microsoft Outlook en dispositivos que no estén inscritos en Intune con la directiva de administración de aplicaciones móviles de Intune. La aplicación Microsoft Outlook actualizada con las funcionalidades MAM está disponible para dispositivos [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) y [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook). Siga las instrucciones del tema [Crear e implementar directivas de administración de aplicaciones móviles](https://technet.microsoft.com/library/mt627829.aspx) para crear una directiva MAM.  


- **Las directivas de configuración de aplicaciones móviles le proporcionan más flexibilidad para especificar los detalles de usuario en las aplicaciones iOS** Puede proporcionar la configuración de usuario que una aplicación iOS necesite al abrirse. Por ejemplo, puede proporcionar un puerto de red o un nombre de usuario. Para obtener más información, vea [Configurar aplicaciones de iOS con directivas de configuración de aplicaciones móviles en Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).


- **Implementar Adobe Reader para Microsoft Intune para los dispositivos iOS administrados por Intune en su empresa** La aplicación de Adobe Reader para iOS ahora puede administrarse en los dispositivos inscritos con la directiva de administración de la aplicación móvil de Intune.

- **Garantizar que las imágenes de web que se han implementado están abiertas en el explorador administrado** Puede implementar imágenes de web de destino que solo se pueden abrir con el explorador administrado en dispositivos iOS y Android. Por ejemplo, puede implementar vínculos a recursos corporativos a través del Portal de empresa y, cuando los usuarios naveguen a los vínculos, se abrirán directamente en el explorador administrado donde se pueden proteger mediante directivas MAM. Para obtener detalles, vea [Implementación de aplicaciones](deploy-apps.md).


- **Encontrar, administrar y distribuir las aplicaciones Tienda Windows para empresas para dispositivos Windows 10 desde la consola de administrador de Intune** El soporte técnico para la Tienda Windows para empresas está disponible en Intune para ayudarle a encontrar, administrar y distribuir aplicaciones en los dispositivos Windows 10 que está administrando. La Tienda Windows para empresas permite administrar el proceso de implementación y supervisión de estas aplicaciones desde la consola de administrador de Intune (la misma consola que se utiliza para administrar el resto de aplicaciones). En concreto, la Tienda Windows para empresas administra el contenido y las licencias de las "aplicaciones con licencia en línea". Para obtener detalles, vea [Administrar las aplicaciones adquiridas a través de la Tienda Windows para empresas con Microsoft Intune](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).


### Administración de dispositivos
- **Distribución de certificados PFX para dispositivos iOS** Los administradores de Intune pueden crear e implementar certificados PFX de iOS para la autenticación de VPN, correo electrónico y Wi-Fi en dispositivos iOS. Esta característica ya está disponible para los dispositivos Android y Windows 10. Para obtener detalles, vea [Enable access to company resources using certificate profiles (Habilitar el acceso a los recursos de empresa mediante perfiles de certificados)](secure-resource-access-with-certificate-profiles.md).


- **Aplicar aplicaciones y directivas a los diferentes grupos de dispositivos basándose en la selección de la categoría de usuario** Los administradores de Intune ahora pueden definir las categorías de dispositivos personalizadas para que los usuarios las seleccionen durante la inscripción. Por ejemplo, los administradores pueden querer que los usuarios especifiquen si están inscribiendo un dispositivo utilizado para la "Caja registradora", el "Camión de reparto" o el "Almacén de productos". La categoría seleccionada hará que el dispositivo se convierta en miembro de un grupo de dispositivos de Intune, que puede utilizarse para implementar diferentes aplicaciones y directivas en el dispositivo inscrito. Para obtener detalles, vea [Clasificar los dispositivos con la asignación de grupos de dispositivos en Microsoft Intune](categorize-devices-with-device-group-mapping-in-microsoft-intune.md).

### Cambios y actualizaciones del Portal de empresa de Microsoft
Los siguientes cambios se realizaron en el Portal de empresa en esta versión.

**Aplicación Portal de empresa de Android**

* Cuando los usuarios inicien una aplicación administrada mediante la administración de aplicaciones móviles (MAM), verán un mensaje que les informa de que su empresa administra la aplicación. Ahora, los usuarios podrán pulsar un vínculo de "Más información" para obtener [más información](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) sobre lo que significa "aplicaciones administradas". También puede pulsar "No volver a mostrar" para que el mensaje deje de aparecer al iniciar la aplicación.
* Se han agregado nuevas pantallas para guiar a los usuarios a través del proceso de inscripción y ofrecer más información sobre por qué deberían inscribirse los usuarios, y lo que los administradores de TI pueden y no pueden ver sobre los dispositivos inscritos. Consulte las [instrucciones de inscripción](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) para obtener detalles.
* Los mensajes de error de inscripción ahora se muestran ahora en la aplicación Portal de empresa. Anteriormente, estos mensajes aparecían en el sitio web del Portal de empresa. Al realizar el cambio, todos los mensajes de error aparecerán ahora en un solo sitio, en lugar de en dos sitios distintos.


**Aplicación Portal de empresa de iOS**
* Cuando los usuarios inicien una aplicación administrada mediante la administración de aplicaciones móviles (MAM), verán un mensaje que les informa de que su empresa administra la aplicación. Ahora, los usuarios podrán pulsar un vínculo de "Más información" para obtener [más información](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) sobre lo que significa "aplicaciones administradas". También puede pulsar "No volver a mostrar" para que el mensaje deje de aparecer al iniciar la aplicación.
* Se han agregado nuevas pantallas para guiar a los usuarios a través del proceso de inscripción y ofrecer más información sobre por qué deberían inscribirse los usuarios, y lo que los administradores de TI pueden y no pueden ver sobre los dispositivos inscritos. Consulte las [instrucciones de inscripción](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) para obtener detalles.
* Los mensajes de error de inscripción ahora se muestran ahora en la aplicación Portal de empresa. Anteriormente, estos mensajes aparecían en el sitio web del Portal de empresa. Al realizar el cambio, todos los mensajes de error aparecerán ahora en un solo sitio, en lugar de en dos sitios distintos.




## Febrero de 2016
### Cambios y actualizaciones del Portal de empresa de Microsoft

Los siguientes cambios se realizaron en el Portal de empresa en esta versión.

#### Aplicación Portal de empresa de Android
- Se han agregado nuevas pantallas para guiar a los usuarios a través del proceso de inscripción y ofrecer más información sobre por qué deberían inscribirse los usuarios, y lo que los administradores de TI pueden y no pueden ver sobre los dispositivos inscritos. Consulte las [instrucciones de inscripción](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) para obtener detalles.
- Los mensajes de error de inscripción ahora se muestran ahora en la aplicación Portal de empresa. Anteriormente, estos mensajes aparecían en el sitio web del Portal de empresa. Al realizar el cambio, todos los mensajes de error aparecerán ahora en un solo sitio, en lugar de en dos sitios distintos.

#### Aplicación Portal de empresa de iOS
 - Se han agregado nuevas pantallas para guiar a los usuarios a través del proceso de inscripción y ofrecer más información sobre por qué deberían inscribirse los usuarios, y lo que los administradores de TI pueden y no pueden ver sobre los dispositivos inscritos. Consulte las [instrucciones de inscripción](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) para obtener detalles.

 - Los mensajes de error de inscripción ahora se muestran ahora en la aplicación Portal de empresa. Anteriormente, estos mensajes aparecían en el sitio web del Portal de empresa. Al realizar el cambio, todos los mensajes de error aparecerán ahora en un solo sitio, en lugar de en dos sitios distintos.


## Enero de 2016

### Aprovechar las características de Windows 10
* **Acceso condicional con el servicio de atestación de estado local** Los administradores de Intune ahora pueden ver el estado de la atestación de estado de los dispositivos de Windows 10 en la consola de administración de Intune. La atestación de estado del dispositivo permite al administrador garantizar que los equipos cliente tienen configuraciones BIOS, TPM y de arranque de software de confianza. Para admitir la atestación de estado de los dispositivos, los dispositivos cliente deben ejecutar Windows 10 con TPM 2 habilitado. La atestación de estado del dispositivo muestra el número de dispositivos habilitados para cada una de las siguientes acciones:
    * Antimalware de inicio temprano
    * BitLocker
    * Arranque seguro
    * Integridad de código

    Lea [Introduction to device compliance policies for Microsoft Intune ](introduction-to-device-compliance-policies-in-microsoft-intune.md) (Introducción a las directivas de cumplimiento de dispositivos para Microsoft Intune) para obtener detalles sobre la configuración de estado de los dispositivos, los puntos de datos recopilados y el informe de certificación de estado. En los [detalles del servicio HAS](https://msdn.microsoft.com/en-us/library/dn934876.aspx) se explica el servicio en profundidad.

* **Administración de certificados y directiva de Windows 10 Passport for Work** Con Intune, es posible la [integración con Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), que es un método alternativo de inicio de sesión para Windows 10 que usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual. Passport permite usar un gesto de usuario para iniciar sesión, en lugar de una contraseña. Un gesto de usuario podría ser una autenticación biométrica de PIN simple, como Windows Hello, o un dispositivo externo como un lector de huellas digitales.

* **VPN para aplicaciones específicas** Puede seleccionar aplicaciones que se conecten automáticamente a la red corporativa a través de VPN. Cree la lista de aplicaciones al configurar el perfil de VPN, como se describe en Ayudar a los usuarios a conectarse a su trabajo con perfiles de VPN con Microsoft Intune.

* **Soporte técnico de Windows 10 Full Wipe** Ahora puede emitir un borrado completo remoto de los dispositivos de escritorio de Windows 10 inscritos en Intune a través de la consola de administración de Intune. El borrado completo de Windows 10 realiza un restablecimiento de fábrica del dispositivo.


### Actualización del Programa de Compras por Volumen (PCV) de Apple
Intune puede ayudarle a [administrar aplicaciones adquiridas a través del Programa de compras por volumen (PCV) para empresas de Apple](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md). Esto incluye la sincronización de la información de licencias entre Apple e Intune, y el seguimiento del número de copias de cada aplicación que haya implementado.

### Utilice números IMEI para identificar los dispositivos corporativos
Ahora puede [importar los números de identidad internacional de equipo móvil (IMEI)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) de las plataformas de dispositivos móviles que tengan un número IMEI para ayudar a identificar los dispositivos móviles corporativos. Cuando se inscriben en Intune, los dispositivos con números IMEI importados se etiquetan como corporativos, que se puede utilizar para aplicar las directivas que son diferentes a las que se aplican a dispositivos personales.

### Ahora, hay más aplicaciones compatibles con las directivas MAM de Intune
Ahora, un mayor número de aplicaciones de socios de Microsoft son compatibles con directivas de administración de aplicaciones móviles (MAM) de Intune (para dispositivos administrados por Intune):
* Box for EMM (de Box Inc), solo iOS.
* Adobe Reader (de Adobe), solo Android.
* Foxit PDF Reader (de Foxit Corporation), iOS y Android.


### Finalización de la compatibilidad con IE9 en enero
A partir de febrero de 2016, Internet Explorer 9 dejará de admitirse como explorador oficial para obtener acceso al sitio web del Portal de empresa de Microsoft Intune, el portal de cuentas de Intune y la consola de administración de Intune. Debe migrar a Internet Explorer 10 o posterior.


>[!div class="step-by-step"]

>[&larr; **Novedades de Intune**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Sep16_HO2-->


