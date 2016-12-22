---
title: Versiones anteriores | Microsoft Intune
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4dab832da4490c3df045d2c627b231028c92b25
ms.openlocfilehash: 3de5e57589a24600301e54a3b60eecb5321ff838


---

# <a name="previous-intune-releases"></a>Versiones anteriores de Intune

Esta página es una lista de los anuncios hechos en [Novedades de Microsoft Intune](whats-new-in-microsoft-intune.md).

[!INCLUDE[wit_nextref](../includes/whats-new-last-six-months.md)]

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

    En el paso 2 del Asistente para crear reglas de notificación, se seleccionan los grupos de dispositivos a los que se destinará la regla. Este paso ("Seleccionar grupos de dispositivos") se va a quitar de la consola de Intune.

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



<!--HONumber=Dec16_HO1-->


