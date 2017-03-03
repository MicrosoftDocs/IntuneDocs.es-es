---
title: Versiones anteriores | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6bc3afe58d5e0f1f12c8b6c6fc62e37d01cd5132
ms.openlocfilehash: cab9833a1e1b92c156a2eb77411436289c70ad71


---

# <a name="previous-intune-releases"></a>Versiones anteriores de Intune

Esta página es una lista de los anuncios hechos en [Novedades de Microsoft Intune](whats-new-in-microsoft-intune.md).

[!INCLUDE[wit_nextref](../includes/whats-new-last-six-months.md)]

## <a name="july-2016"></a>Julio de 2016

### <a name="app-management"></a>Administración de aplicaciones

__Mejorar la aplicación aprovisionando una experiencia de actualización de perfil__ La línea de aplicaciones móviles empresariales de Apple iOS se crea con un perfil de aprovisionamiento incluido y código firmado con un certificado. Cuando la aplicación se ejecuta en un dispositivo iOS, iOS confirma la integridad de la aplicación de iOS y exige el cumplimiento de las directivas definidas por el perfil de aprovisionamiento.

El certificado de firma empresarial que se usa para firmar aplicaciones normalmente tiene una validez de 3 años. Sin embargo, el perfil de aprovisionamiento expira después de 1 año. Con esta actualización, Intune proporciona las herramientas para implementar proactivamente una nueva directiva de perfil de aprovisionamiento a dispositivos que tengan aplicaciones cuya expiración esté próxima mientras siga siendo válido el certificado. Para más información, consulte [Use iOS mobile provisioning profile policies to keep your line of business apps up to date (Usar directivas de perfil de aprovisionamiento móvil iOS para mantener al día sus aplicaciones de línea de negocio)](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->

__Xamarin SDK para aplicaciones de Intune está disponible__ El componente Intune App SDK Xamarin permite habilitar las características de administración de aplicaciones móviles de Intune en las aplicaciones móviles para iOS y Android creadas con Xamarin. Puede encontrar el componente en la [tienda de Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) o en la [página de Github de Microsoft Intune](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### <a name="device-management"></a>Administración de dispositivos
__Aumento de los límites de inscripción de dispositivos__ Intune ha aumentado el límite máximo de inscripción de dispositivos configurables de 5 a 15 dispositivos por usuario.
<!---TFS 1289896 --->

__Integración de TeamViewer para equipos Windows que ejecutan el software cliente de Intune__
La integración de [TeamViewer](https://www.teamviewer.com) para equipos Windows que ejecutan el software cliente de Intune permite establecer sesiones de asistencia remota en equipos Windows como apoyo para departamentos de soporte técnico para usuarios finales. Esto incluye Windows 7, 8, 8.1 y Windows 10. Para obtener más información, vea [Tareas comunes de administración de PC Windows con el cliente de equipo de Microsoft Intune](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>Actualizaciones del portal de empresa

__Sitio web del Portal de empresa__
- **Experiencia de usuario final mejorada al inscribir dispositivos de Windows**<br/>
Cuando usa acceso condicional, los pasos de inscripción para Windows 8.1, Windows 10 Escritorio y Windows 10 Mobile se han clarificado en el sitio web del Portal de empresa. Los usuarios ahora verán pasos "Inscripción de dispositivos" y "Unión al lugar de trabajo" independientes, lo que les facilita ver el estado de su dispositivo y completar el proceso si experimentan un error en Unión al lugar de trabajo (WPJ). También se espera que los pasos independientes simplifiquen el proceso de solución de problemas para los administradores de TI. Anteriormente, cuando los usuarios finales intentaban inscribirse y todos los pasos de la inscripción se llevaban a cabo correctamente excepto para WPJ, el dispositivo inscrito no aparecería en la lista de dispositivos para los usuarios para identificar, provocando confusión para los usuarios.

__Android__
- **Aplicación de portal de empresa de Android**<br/>
Si los usuarios finales Android ven un mensaje de error que dice que el dispositivo no tiene un certificado necesario, pueden pulsar un botón "Cómo resolver esto" para obtener [pasos](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) para instalar el certificado que falta. Si los usuarios completan los pasos, pero ven un mensaje de error adicional que indica que "falta el certificado", se les solicita que se pongan en contacto con su administrador de TI y proporcionen este [vínculo](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), que contiene pasos que los administradores de TI pueden usar para solucionar el problema del certificado.

- **Restringir instalaciones de aplicaciones de transferencia local a dispositivos inscritos**<br/>
Los dispositivos Android ya no pueden instalar aplicaciones a través del sitio web de Portal de empresa a menos que los dispositivos se hayan inscrito en Intune mediante la aplicación de Portal de empresa de Intune para Android.
<!---TFS 1299082--->

__iOS__
- **Cambios en las cuentas de administradores de inscripción de dispositivos en la aplicación de portal de empresa de iOS**<br/>
Para mejorar el rendimiento y la escalabilidad, Intune ya no mostrará todos los dispositivos de Administradores de inscripción de dispositivos (DEM) en el panel **Mis dispositivos** de la aplicación de Portal de empresa para iOS. Solo se muestra el dispositivo local que está ejecutando la aplicación y solo si está inscrito a través de la aplicación Portal de empresa.

El usuario de DEM puede realizar acciones en el dispositivo local, pero la administración remota de los demás dispositivos inscritos solo puede realizarse desde la consola de administración de Intune. Además, Intune está dejando de usar las cuentas de DEM con el Programa de inscripción de dispositivos de Apple o con la herramienta Apple Configurator. Estos métodos de inscripción ya admiten la inscripción sin usuarios para los dispositivos iOS compartidos.

Use las cuentas de DEM solo cuando no esté disponible la inscripción sin usuarios para los dispositivos compartidos. Para más información, consulte [Inscribir dispositivos propiedad de la empresa con el Administrador de inscripción de dispositivos de Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>Cambio de nombres de características de Windows
- [Microsoft Passport para Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) ahora se conoce como **Windows Hello para empresas**.
- [Protección de datos de empresa](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) ahora se conoce como **Windows Information Protection**.


## <a name="june-2016"></a>Junio de 2016
### <a name="intune-service-health"></a>Mantenimiento del servicio de Intune
La información de mantenimiento del servicio de Intune se ha movido a una ubicación central con otros servicios de Microsoft. Ahora encontrará esta información en el portal de administración de Office 365, en Estado del servicio. Para más información, consulte [esta entrada de blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Administración de aplicaciones
- **Mejoras en la experiencia de configuración de la directiva de datos de empresa de Windows 10.** Se han realizado mejoras en la experiencia de configuración de directivas de protección de datos de empresa de Windows 10 en relación con la creación de reglas de aplicaciones, la especificación de la definición de límite de red y otras opciones de protección de datos de empresa. Para más información, consulte [Create an enterprise data protection (EDP) policy using Microsoft Intune (Crear una directiva de protección de datos de empresa (EDP) con Microsoft Intune)](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### <a name="device-management"></a>Administración de dispositivos
- **Configuración de directiva de Windows Defender para la protección ante aplicaciones potencialmente no deseadas.** Se ha agregado una nueva configuración de Windows Defender denominada **Detección de aplicaciones potencialmente no deseadas** a la directiva de configuración general para Windows 10 Escritorio y Mobile. Puede usar esta configuración para proteger los equipos de escritorio de Windows inscritos ante la ejecución de software que Windows Defender ha clasificado como potencialmente no deseado. Puede protegerse contra la ejecución de estas aplicaciones o puede usar el modo auditoría para informar cuando se instale una aplicación potencialmente no deseada. Para más información, consulte [Configuración de directivas de Windows 10 en Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### <a name="conditional-access"></a>Acceso condicional
- **Directiva de control de acceso de red de Cisco ISE para Intune.**  Los clientes que usen Cisco Identity Service Engine (ISE) 2.1 y también usen Microsoft Intune pueden establecer una directiva de control de acceso de red en ISE.

    Al usar esta directiva, los dispositivos que necesiten conectarse a la red mediante WiFi o VPN deben cumplir las siguientes condiciones antes de que se les permita el acceso:

    * Deben administrarse mediante Intune
    * Deben cumplir todas las directivas de cumplimiento de Intune implementadas

 A los usuarios finales de los dispositivos no conformes se les solicitará que se inscriban y que solucionen cualquier problema de cumplimiento para obtener acceso.
- **Acceso condicional para el explorador.** Puede establecer una directiva de acceso condicional para [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) y [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) de modo que solo se pueda obtener acceso a ellos desde exploradores web compatibles en dispositivos administrados y compatibles con iOS y Android. A los usuarios finales que intenten iniciar sesión en Outlook Web Access (OWA) y en los sitios de SharePoint con dispositivos iOS y Android, se les solicitará que inscriban su dispositivo con Intune así como que solucionen cualquier problema de incumplimiento antes de completar el inicio de sesión.
<!---TFS 1175844--->

- **Dynamics CRM Online admite el acceso condicional.** Puede establecer una directiva de acceso condicional para [Dynamics CRM Online](/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) de modo que solo se pueda tener acceso a este con dispositivos administrados y compatibles con iOS y Android. Los usuarios finales que intenten iniciar sesión en la aplicación móvil de Dynamics CRM en iOS y Android tendrán que inscribirse en Intune y corregir cualquier problema de cumplimiento para poder iniciar sesión.
<!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Actualizaciones del portal de empresa de Intune

__Aplicación de portal de empresa de Android__

- Cuando los administradores de TI apliquen la nueva directiva "Los dispositivos deben impedir la instalación de aplicaciones de orígenes desconocidos (Android 4.0+)", los usuarios finales con dispositivos de Android 4.0 o posterior verán el mensaje "Debe deshabilitarse la instalación desde orígenes desconocidos". Los usuarios tendrán que ir a **Configuración** > **Seguridad** y desactivar **Orígenes desconocidos**. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener más [información](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) sobre el mensaje y el porqué de desactivar el valor.

- Cuando los administradores de TI apliquen la nueva directiva "Los dispositivos deben tener habilitada la opción "Buscar amenazas de seguridad en el dispositivo" (Android 4.0+)", los usuarios finales con dispositivos de Android 4.0 o posterior verán el mensaje "Buscar amenazas de seguridad en el dispositivo". Los usuarios tendrán que ir a **Configuración** > **Google** > **Seguridad** y activar **Buscar amenazas de seguridad en el dispositivo**. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener más [información](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre el mensaje y el porqué de activar el valor.

- Cuando los administradores de TI apliquen la nueva directiva "La depuración USB debe estar deshabilitada (Android 4.2+)", los usuarios finales con dispositivos de Android 4.2 o posterior verán el mensaje "La depuración USB debe deshabilitarse". Los usuarios tendrán que ir a **Configuración** > **Opciones del desarrollador** y desactivar **Depuración USB**. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener más [información](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) sobre el mensaje y el porqué de desactivar el valor.

- Cuando los administradores de TI apliquen la nueva directiva "Nivel mínimo de revisión de seguridad de Android (Android 6.0+)", los usuarios finales con dispositivos de Android 6.0 o posterior verán el mensaje "Este dispositivo no cumple el nivel mínimo de revisión de seguridad de Android". Los usuarios tendrán que instalar la revisión de seguridad necesaria. Un vínculo en el mensaje de compatibilidad permite a los usuarios obtener [información](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre cómo instalar la revisión de seguridad necesaria y ver qué revisión de seguridad tienen instalada en ese momento.

__Aplicación de portal de empresa de iOS__

- Cuando los usuarios finales instalen aplicaciones de línea empresarial, ahora podrán disfrutar una experiencia mejorada de instalación de la aplicación. Si la instalación de la aplicación tarda mucho, los usuarios pueden sincronizar manualmente el dispositivo para forzar que se reanude el proceso de sincronización. Para leer las instrucciones del usuario final, consulte [Sincronizar el dispositivo iOS manualmente](/Intune/EndUser/sync-your-device-manually-ios).

- La aplicación Portal de empresa de Microsoft Intune para iOS se ha actualizado y ahora admite la versión de iOS 8.0 y posteriores. Con esta actualización, los usuarios finales pueden instalar la aplicación Portal de empresa de Microsoft Intune e inscribir nuevos dispositivos en Intune solo si el dispositivo ejecuta la versión de iOS 8.0 o posterior. Los usuarios que ya han inscrito dispositivos que se ejecutan con una versión no compatible de iOS pueden seguir utilizando la aplicación Portal de empresa que está en su dispositivo.

## <a name="may-2016"></a>Mayo de 2016
Todas estas características también son compatibles en las implementaciones híbridas (Configuration Manager con Intune). Para más información sobre las nuevas características híbridas, vea la página sobre las [novedades de implementaciones híbridas](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### <a name="documentation"></a>Documentación
Le damos la bienvenida a la versión preliminar de [docs.microsoft.com](https://docs.microsoft.com/en-us/intune).
Se trata de una plataforma de contenido completamente nueva y moderna diseñada para facilitarles a los usuarios la comprensión y el uso de Intune.
Para más información sobre todas las características nuevas, vea [Introducing docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/) (Introducción a docs.microsoft.com).

### <a name="intune-service-health"></a>Mantenimiento del servicio de Intune
La información de mantenimiento del servicio de Intune se ha movido a una ubicación central con otros servicios de Microsoft. Ahora encontrará esta información en el [portal de administración de Office 365](https://portal.office.com/Admin/Default.aspx) en **Mantenimiento del servicio**.
Para más información, vea [esta entrada de blog](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>Administración de aplicaciones
- **SDK de MAM: admite la configuración de longitud de PIN.** Podrá especificar la longitud del PIN para las aplicaciones de MAM como si fuera el PIN de un dispositivo. Esto requerirá que los usuarios finales cumplan con las nuevas restricciones que establezca. Verán una pantalla de PIN ligeramente modificada para tener en cuenta la entrada más larga. Para obtener más información, vea [Opciones de configuración de directiva de administración de aplicaciones móviles de Android en Microsoft Intune](/intune/deploy-use/android-mam-policy-settings) y [Configuración de directiva de administración de aplicaciones móviles iOS](/intune/deploy-use/ios-mam-policy-settings).

- **Skype Empresarial para iOS y Android.** Ahora puede abordar Skype Empresarial con [MAM sin las directivas de inscripción](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Cuando los usuarios inician sesión, se aplican las directivas de MAM.

- **Nuevas aplicaciones disponibles para la administración con directivas de MAM.** Las aplicaciones de Microsoft Word, Excel y PowerPoint para Android ahora pueden asociarse con directivas de MAM en los dispositivos que no están inscritos con Intune. Para ver una lista completa de las aplicaciones compatibles, vaya a la galería de aplicaciones móviles de Microsoft Intune de la página [Microsoft Intune application partners](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) (Socios de aplicaciones de Microsoft Intune).


### <a name="company-portal-updates"></a>Actualizaciones del portal de empresa

#### <a name="android-company-portal-app"></a>Aplicación Portal de empresa de Android
- **Notificaciones del sistema para el usuario final:** los usuarios finales ahora verán notificaciones del sistema de la aplicación de portal de empresa de Android cuando inscriban o quiten sus dispositivos desde el portal de empresa.

- **Cambios en las cuentas de administradores de inscripción de dispositivos en la aplicación de portal de empresa de Android.** Para mejorar el rendimiento y la escalabilidad, Intune ya no mostrará todos los dispositivos de administradores de inscripción de dispositivos (DEM) en el panel Mis dispositivos de la aplicación de portal de empresa de Android. Solo se muestra el dispositivo local que está ejecutando la aplicación y solo si está inscrito a través de la aplicación Portal de empresa. El usuario de DEM puede realizar acciones en el dispositivo local, pero la administración remota de los demás dispositivos inscritos solo puede realizarse desde la consola de administración de Intune.

#### <a name="company-portal-website"></a>Sitio web del Portal de empresa
- **Sitio web del portal de empresa: el banner de identificación de dispositivos proporcionará más información a los usuarios finales.** Los usuarios finales ahora pueden identificar más fácilmente el dispositivo que han seleccionado cuando están usando el sitio web del portal de empresa. Si hay seleccionado un dispositivo incorrecto, podrán seleccionar el dispositivo correcto pulsando en el vínculo **Pulsar aquí** en el banner de la página principal.

### <a name="service-deprecation"></a>Degradación del servicio
- **Aplicaciones de visor de Intune.** Con el lanzamiento de la nueva aplicación RMS sharing, quitaremos las siguientes aplicaciones de visor de Intune a partir de agosto de 2016:
    - Visor de AV de Intune
    - Visor de PDF de Intune
    - Visor de imágenes de Intune para Android de Google Play

  En lugar de usar las aplicaciones de visor de Intune, se recomienda usar la nueva aplicación Rights Management (RMS sharing) para Android, que permite implementar una aplicación en lugar de tres aplicaciones independientes para ver archivos corporativos de forma segura en dispositivos Android. Obtenga más información sobre la aplicación RMS sharing (con un vínculo a documentación).

- **Eliminación del grupo personalizado de destinatarios de reglas de notificación.**
Las reglas de notificación de Intune definen a quién se enviará una alerta de correo electrónico a través de Intune. Actualmente, puede configurar reglas de notificación para enviar mensajes de correo electrónico a todos los usuarios de dispositivos de un grupo de dispositivos de Intune que haya creado. Aproximadamente a partir del 1 de junio de 2016, ya no se admitirán los grupos creados por el usuario de destino.

    A día de hoy, para que una regla de notificación esté destinada a un grupo creado desde la consola de administración de Microsoft Intune, debe seguir los pasos siguientes:

    En el área de trabajo **Administración**, haga clic en **Reglas de notificación** > **Crear nueva regla**.

    En el paso&2; del Asistente para crear reglas de notificación, se seleccionan los grupos de dispositivos a los que se destinará la regla. Este paso ("Seleccionar grupos de dispositivos") se va a quitar de la consola de Intune.

    La escala de tiempo preliminar de este cambio es la siguiente:
    - En junio de 2016, los nuevos inquilinos no verán el paso 2 del Asistente para crear reglas de notificación. Los inquilinos existentes no se verán afectados.
    - Alrededor de agosto de 2016, algunos inquilinos existentes no verán la opción "Seleccionar grupos de dispositivos" en el asistente.
    - Alrededor de octubre de 2016, se espera que ningún inquilino vea la opción "Seleccionar grupos de dispositivos" en el asistente.


- **Cambios en la compatibilidad de la aplicación de portal de empresa de iOS.**. En los próximos meses, habrá una actualización para la aplicación de portal de empresa de Microsoft Intune para iOS que solo admitirá dispositivos que ejecuten iOS 8.0 o posterior. Los usuarios no podrán inscribir dispositivos nuevos que ejecuten versiones anteriores a iOS 8.0. Los dispositivos inscritos que ejecuten versiones anteriores a iOS 8.0 seguirán administrándose y, durante un tiempo limitado, podrá seguir usando la aplicación de portal de empresa. Pero los dispositivos deben tener iOS 8.0 o posterior para tener acceso a las últimas versiones de la aplicación de portal de empresa. Le recomendamos que notifique a los usuarios que actualicen a iOS 8.0 o posterior para aprovechar las nuevas características de Intune.  


## <a name="april-2016"></a>Abril de 2016
Todas estas características también son compatibles con los clientes híbridos (Configuration Manager integrado con Intune).

### <a name="app-management"></a>Administración de aplicaciones
- **Compatibilidad de usuario de MAM.**
Ahora puede ver el [estado](/intune/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune) de sus directivas de administración de aplicaciones para cualquier usuario en el inquilino de Azure Active Directory (AAD). Esto incluye:
   - Dispositivos
   - Aplicaciones del dispositivo

   Valores de estado:

   **Checked in (Comprobado)**: indica que la directiva se implementó para el usuario, y la aplicación se usó en un contexto profesional y recibió correctamente la directiva.

    **Not checked in (No comprobado)**: indica que la directiva se implementó para el usuario, pero la aplicación no se ha usado en un contexto profesional desde entonces.


- **Controles de MAM para evitar la sincronización de contactos de Outlook (Android).**
Hay una nueva opción de configuración disponible para la [administración de aplicaciones móviles](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) sin inscripción de dispositivos. Esta opción permite evitar que una aplicación sincronice contactos con la libreta de direcciones nativa en dispositivos Android. Si esta opción está habilitada, las aplicaciones de destino ya no podrán guardar contactos en la libreta de direcciones nativa. Si esta opción está deshabilitada, las aplicaciones de destino podrán guardar contactos en la libreta de direcciones nativa. Al [borrar un dispositivo o aplicación de forma remota](/intune/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune), se quitarán todos los contactos que ya se hayan guardado en la libreta de direcciones nativa. Esta nueva opción es compatible inicialmente con la aplicación Outlook en dispositivos Android.

### <a name="device-management"></a>Administración de dispositivos
- **Identificación de número de teléfono para dispositivos propiedad de la empresa.** Los teléfonos que están clasificados como "Corporativos" se identifican ahora con el número de teléfono completo, por ejemplo, al ejecutar un informe de inventario de dispositivos móviles. Los números de teléfono BYOD se seguirán enmascarando con ****; y solo se mostrarán los últimos 4 dígitos.


### <a name="company-portal-updates"></a>Actualizaciones de Portal de empresa
**Aplicación de portal de empresa de Android** Los usuarios que no han inscrito su dispositivo en Intune y que no tienen el certificado correcto instalado, no podrán iniciar sesión en la aplicación de portal de empresa de Android y verán el mensaje "No puede iniciar sesión porque falta un certificado necesario en su dispositivo". El mensaje incluye un vínculo "Cómo resolver esto" que los usuarios pueden pulsar para ver instrucciones para instalar el certificado. Para ver los pasos que los usuarios finales siguen para solucionar el problema, vea [Uso de un dispositivo Android con Intune](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**Aplicación de portal de empresa de iOS** Se ha agregado soporte técnico para que la acción de deslizar para actualizar actualice el contenido en la pantalla principal, que incluye aplicaciones y dispositivos enumerados e información de contacto de TI. Las acciones de deslizar para actualizar no comprueban el cumplimiento ni la información de la directiva, que puede realizarse al seleccionar el icono de su dispositivo actual y pulsar el botón **Sincronizar**.

**La aplicación de portal de empresa de Windows 10 Mobile y Windows Phone 8.1** Cuando los usuarios finales instalen aplicaciones de línea empresarial, ahora podrán disfrutar de una experiencia mejorada de instalación de la aplicación. Si la instalación de la aplicación tarda mucho, los usuarios pueden sincronizar manualmente el dispositivo para forzar que se reanude el proceso de sincronización. Para revisar las instrucciones del usuario final, vea [Usar un dispositivo Windows con Intune](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Sitio web de portal de empresa** Cuando los usuarios de Windows 10 Mobile y Windows Phone 8.1 instalen aplicaciones de línea empresarial, ahora podrán disfrutar de los siguientes estados nuevos, que les proporcionan más información sobre el estado de su instalación:

* **Esperando a que se sincronice el dispositivo**: el usuario ha pulsado "Instalar" y el dispositivo ahora se intenta sincronizar mediante la infraestructura de Intune. La sincronización es necesaria antes de que se complete la instalación. El mensaje "Esperando a que se sincronice el dispositivo" también es un vínculo que los usuarios pueden pulsar para ver [instrucciones](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) sobre cómo sincronizar manualmente su dispositivo con Intune si el proceso de sincronización tarda mucho o se detiene.
* **Descargando**: la solicitud de descarga del usuario se está procesando y el dispositivo está descargando e instalando la aplicación.

Antes de que se agregaran estos estados, los usuarios se confundían si una instalación de aplicación tardaba mucho, porque solo veían el estando "Instalando", que puede permanecer en la pantalla durante horas. Al agregar los nuevos estados, en vez de llamar al soporte técnico, los usuarios ahora pueden pulsar el vínculo "Esperando a que se sincronice el dispositivo" y seguir las instrucciones para forzar que se reanude el proceso de sincronización.

>[!div class="step-by-step"]

>[&larr; **Novedades de Intune**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Feb17_HO3-->


