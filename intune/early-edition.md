---
title: "Edición anticipada"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d7c2ec47a163c16de91d3004a6204c1c00feb801
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="the-early-edition-for-microsoft-intune---february-2018"></a>La edición anticipada de Microsoft Intune: febrero de 2018

La **edición anticipada** proporciona una lista de características que se incluirán en las próximas versiones de Microsoft Intune. Esta información se proporciona conforme a una base limitada y está sujeta a cambios. No comparta esta información fuera de la compañía. Algunas de las características enumeradas aquí corren el riesgo de no cumplir las fechas límite y pueden retrasarse hasta una versión futura. Otras características se están probando en una prueba piloto (distribución de paquetes piloto) para asegurarse de que están preparadas para el cliente. Si tiene alguna pregunta o problema, póngase en contacto con su contacto del grupo de productos de Microsoft.

Esta página se actualiza periódicamente. Compruebe si hay actualizaciones adicionales.

> [!Note]
>Los siguientes cambios están en fase de desarrollo de Intune. Para obtener más información sobre las nuevas características híbridas, vea la [página sobre las novedades de implementaciones híbridas](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->

## <a name="intune-in-the-azure-portal"></a>Intune en el portal de Azure


<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nuevo gráfico de tendencias sobre errores de inscripción y tabla de motivos de error <!-- 1471783 -->

En la página de información general de inscripción, verá la tendencia de los errores de inscripción y los cinco motivos de error principales. Al hacer clic en un gráfico o una tabla, podrá explorar los detalles para obtener consejos de resolución de problemas y sugerencias de corrección.

### <a name="prevent-end-users-from-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Impedir que los usuarios finales agreguen cuentas al perfil del trabajo o las quiten<!-- 1728700 -->    
Al implementar la aplicación Gmail en un perfil de Android for Work, puede impedir que los usuarios finales agreguen o quiten cuentas en el perfil de trabajo mediante la opción de configuración **Agregar y quitar cuentas** del perfil de restricciones del dispositivo Android for Work.

### <a name="app-protection-policies-----679615---"></a>Directivas de protección de aplicaciones  <!-- 679615 -->
Las directivas de Intune App Protection ofrecerán la capacidad de crear directivas predeterminadas globales para habilitar rápidamente la protección en todos los usuarios de todo el inquilino.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Compatibilidad de Intune con varias cuentas del programa del Programa de inscripción de dispositivos (DEP) de Apple o de Apple School Manager (ASM) <!-- 747685 -->

Intune admitirá la inscripción de dispositivos de hasta 100 cuentas distintas del Programa de inscripción de dispositivos de Apple o de Apple School Manager. Cada token cargado puede administrarse por separado para los perfiles y los dispositivos de inscripción. Es posible asignar un perfil de inscripción diferente para cada token de DEP/School Manager. Si se cargan varios tokens de School Manager, solo pueden compartirse de uno en uno con Microsoft School Data Sync.

Tras la migración, la versión beta de las API Graph y los scripts publicados para la administración de Apple DEP o ASM en Graph ya no funcionará. Las nuevas versiones beta de las API Graph están en desarrollo y se publicarán después de la migración.

### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Informes de estado de mantenimiento y de estado de amenazas de Windows defender <!--854704 -->

Conocer el estado de mantenimiento de Windows Defender es clave para la administración de equipos de Windows.  Intune la agregará nuevos informes y acciones para el estado y el mantenimiento del agente de Windows Defender. Con un informe de resumen de estado en la carga de trabajo de conformidad de los dispositivos, podrá ver los dispositivos que necesitan alguna de las siguientes acciones:

- actualización de la firma
- reiniciar
- intervención manual
- examen completo
- otros estados del agente que requieren intervención

En algunos casos, se pueden realizar acciones de corrección remotas, como desencadenar una actualización de la firma.  El informe también indica el número de equipos identificados como **limpios**.

Un informe de obtención de detalles para cada categoría de estado muestra los equipos individuales que requieren atención o identificados como **limpios**.

### <a name="protocol-exceptions-for-applications---1035509-eeready--"></a>Excepciones de protocolo para las aplicaciones <!--1035509 eeready-->

Podrá crear excepciones a la directiva de transferencia de datos de la administración de aplicaciones móviles (MAM) de Intune para abrir determinadas aplicaciones no administradas. Dichas aplicaciones deben ser de confianza para el departamento de TI. Aparte de las excepciones que cree, la transferencia de datos seguirá estando limitada a las aplicaciones que se administran mediante Intune cuando la directiva de transferencia de datos se establece en **solo aplicaciones administradas**. Puede crear las restricciones mediante protocolos (iOS) o paquetes (Android).

Por ejemplo, puede agregar el paquete de WebEx como una excepción a la directiva de transferencia de datos de MAM. Esto permitirá que los vínculos de WebEx en un mensaje de correo electrónico de Outlook administrado se abran directamente en la aplicación de WebEx. Se seguirá restringiendo la transferencia de datos en otras aplicaciones no administradas.

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561-eeready--"></a>Personalice los temas del Portal de empresa con códigos hexadecimales <!--1049561 eeready-->

Podrá personalizar el color del tema en las aplicaciones del Portal de empresa mediante los códigos hexadecimales. Cuando se escriba el código hexadecimal, Intune determinará el color del texto que proporciona el nivel más alto de contraste entre el color del texto y el color de fondo según los [estándares de WCAG 2.0](http://www.w3.org/TR/WCAG20). Puede ver el color del texto y el logotipo de su empresa con el color en **Aplicaciones móviles** > **Portal de empresa**. 

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Nueva configuración de protección de credenciales de Windows Defender agregada a la configuración de endpoint protection<!--1102252 --> 

Se agregará una nueva configuración [Credential Guard de Windows Defender] (https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard] a **Configuración del dispositivo** > **Perfiles** > **Endpoint protection**. Se agregará la configuración siguiente: 

- Nivel de seguridad de la plataforma: especifique si el nivel de seguridad de plataforma está habilitado en el siguiente reinicio. La seguridad basada en la virtualización requiere el arranque seguro. Opcionalmente, la seguridad basada en la virtualización se puede habilitar con el uso de protecciones de acceso directo a memoria (DMA). Las protecciones de DMA requieren compatibilidad con el hardware y solo se habilitarán en dispositivos configurados correctamente.
- Seguridad basada en la virtualización: especifique si está habilitada la seguridad basada en la virtualización en el siguiente reinicio. 
- Credential Guard de Windows Defender: active Credential Guard con seguridad basada en la virtualización para ayudar a proteger las credenciales en el siguiente reinicio cuando están activados tanto el nivel de seguridad de la plataforma con arranque seguro como la seguridad basada en la virtualización. Las opciones disponibles son **Deshabilitado**, **Habilitado con el bloqueo UEFI**, **Habilitado sin bloqueo** y **No configurado**. 
  - La opción "Deshabilitado" desactiva Credential Guard remotamente si previamente se ha activado con la opción "Habilitado sin bloqueo".

  - La opción "Habilitado con el bloqueo UEFI" garantiza que no se puede deshabilitar Credential Guard con la clave del registro o mediante la directiva de grupo. Para deshabilitar Credential Guard después de usar esta opción, debe establecer la directiva de grupo en "Deshabilitado" y eliminar la funcionalidad de seguridad de cada equipo, con un usuario presente de forma física, para poder borrar la configuración persistente en UEFI. Mientras persista la configuración de UEFI, Credential Guard estará habilitado.

  - La opción "Habilitado sin bloqueo" permite que se deshabilite de forma remota Credential Guard mediante una directiva de grupo. Los dispositivos que usen esta configuración deben ejecutar al menos Windows 10 (versión 1511).

  - La opción "No configurado" deja la configuración de la directiva sin definir. La directiva de grupo no escribe la configuración de directiva en el Registro, por lo que no existe un impacto en los equipos o los usuarios. Si hay una configuración actual en el registro, esta no se modificará.

### <a name="synchronize-and-deploy-sparsely-bundled-windows-store-for-business-apps---1222672---"></a>Sincronizar e implementar aplicaciones de Windows Store para Empresas poco agrupadas <!--1222672 -->
Las aplicaciones sin conexión adquiridas en Windows Store para Empresas se sincronizarán con el portal de Intune. Así, puede implementar estas aplicaciones en grupos de usuarios o grupos de dispositivos. Las aplicaciones sin conexión se instalan mediante Intune, en lugar de desde la tienda.

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Restablecer contraseñas para dispositivos Android O <!-- 1238299 -->
Podrá restablecer las contraseñas para los dispositivos Android O inscritos. Cuando se envía una solicitud de "Restablecer contraseña" en un dispositivo Android O, se establece un nueva contraseña de desbloqueo de dispositivo o un desafío de perfil administrado al usuario actual. La contraseña o el desafío se envía en función de si el dispositivo tiene un propietario del perfil o un propietario de dispositivo y surte efecto de inmediato.

### <a name="local-device-security-option-settings----1251887---"></a>Configuración de opciones de seguridad del dispositivo local <!-- 1251887 -->
Podrá habilitar la configuración de seguridad en dispositivos Windows 10 con los nuevos valores de opción de seguridad del dispositivo local. Encuentre estos valores en la categoría de Endpoint Protection cuando cree una directiva de configuración de dispositivo de Windows 10.

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nueva configuración de impresora para perfiles de educación <!-- 1308900 -->

Para los perfiles de educación, habrá nueva configuración disponible en la categoría **Impresoras**: **Impresoras**, **Impresora predeterminada**, **Agregar nuevas impresoras**. 

### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Nueva configuración de privacidad para las restricciones de dispositivos <!--1308926 -->

Habrá dos nuevas opciones de privacidad disponibles para los dispositivos:

- **Publicar las actividades del usuario**: establezca esta propiedad en **Bloquear** para evitar experiencias compartidas y la detección de recursos usados recientemente en el selector de tareas.

- **Solo actividades locales**: establezca esta propiedad en **Bloquear** para evitar experiencias compartidas y la detección de recursos usados recientemente en el selector de tareas según la actividad local únicamente.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>compatibilidad del Portal de empresa de macOS para las inscripciones que usen el administrador de inscripciones de dispositivos <!-- 1352411 -->

Los usuarios podrán usar el administrador de inscripciones de dispositivos cuando se inscriban con el Portal de empresa de macOS.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Nueva configuración para el explorador Edge <!--1469166 -->

Habrá dos nuevas opciones disponibles para dispositivos con el explorador Microsoft Edge: **Ruta de acceso al archivo de favoritos** y **Cambios a Favoritos**. 

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Datos cifrados de Windows Information Protection (WIP) en los resultados de la búsqueda de Windows <!-- 1469193 -->

Un nuevo parámetro de configuración de la directiva de Windows Information Protection (WIP) permitirá controlar si los datos cifrados por WIP se incluyen en los resultados de la búsqueda de Windows.

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Compatibilidad con aplicaciones de línea de negocio (LOB) para macOS <!-- 1473977 -->
Intune proporcionará la capacidad para instalar aplicaciones LOB de macOS. Las aplicaciones LOB son aplicaciones en las que el usuario proporciona el archivo de instalación y usa Intune para instalar la aplicación en el dispositivo. Como parte de la compatibilidad con aplicaciones LOB de macOS, debe usar la herramienta de ajuste de aplicaciones de Microsoft Intune para macOS para preprocesar las aplicaciones de línea de negocio (LOB) de macOS.

### <a name="configure-resource-account-settings-for-surface-hubs----1475674---"></a>Configurar las opciones de la cuenta del recurso para Surface Hubs <!-- 1475674 -->

Podrá configurar las opciones de la cuenta del recurso para Surface Hubs de forma remota.

Una instancia de Surface Hub usa la cuenta del recurso para autenticarse en Skype o Exchange y así poder unirse a una reunión. Deberá crear una cuenta del recurso única para que Surface Hub pueda aparecer en la reunión como la sala de conferencias. Por ejemplo, una cuenta del recurso como **Sala de conferencias B41/6233**.

> [!NOTE]
> - Si deja campos en blanco invalidará los atributos configurados previamente en el dispositivo.
>
> - Las propiedades de la cuenta del recurso pueden cambiar dinámicamente en Surface Hub. Por ejemplo, si el cambio de contraseñas está activado. Por lo tanto, es posible que los valores de la consola de Azure tarden algún tiempo en reflejar la realidad en el dispositivo. 
>
>   Para entender lo que está configurado actualmente en Surface Hub, se puede incluir la información de la cuenta del recurso en el inventario de hardware (que ya tiene un intervalo de 7 días) o como propiedades de solo lectura. Para mejorar la precisión después de llevar a cabo la acción remota, puede obtener el estado de los parámetros inmediatamente después de ejecutar la acción para actualizar la cuenta o los parámetros en Surface Hub.

### <a name="ios-app-provisioning-configuration----1581650---"></a>configuración de aprovisionamiento de aplicaciones de iOS <!-- 1581650 -->
Podrá asignar perfiles de aprovisionamiento de aplicaciones de iOS para evitar que las aplicaciones expiren mediante la inclusión o exclusión de grupos de seguridad.

### <a name="new-windows-defender-exploit-guard-settings----631893---"></a>Nueva configuración de protección contra vulnerabilidades de seguridad de Windows Defender <!-- 631893 -->

Habrá disponibles seis nuevas opciones de **reducción de la superficie expuesta a ataques** y funcionalidades ampliadas de **acceso controlado a carpetas: protección de carpetas**. Puede encontrar estas opciones en: Configuración de dispositivo\Perfiles\
Crear perfil\Endpoint protection\Protección contra vulnerabilidades de seguridad de Windows Defender.

#### <a name="attack-surface-reduction"></a>Reducción de la superficie expuesta a ataques

|Nombre de la configuración  |Opciones de configuración  |Descripción  |
|---------|---------|---------|
|Protección de ransomware avanzada|Habilitado, Auditoría, No configurado|Usar protección ransomware intensa.|
|Marcar el robo de credenciales desde el subsistema de autoridad de seguridad local de Windows|Habilitado, Auditoría, No configurado|Marcar el robo de credenciales desde el subsistema de autoridad de seguridad local de Windows (lsass.exe).|
|Creación del proceso desde comandos PSExec y WMI|Bloquear, Auditoría, No configurado|Bloquear creaciones del proceso que se originan desde comandos PSExec y WMI.|
|Procesos que no son de confianza y sin firma que se ejecutan desde una unidad USB|Bloquear, Auditoría, No configurado|Bloquear los procesos que no son de confianza y sin firma que se ejecutan desde una unidad USB.|
|Archivos ejecutables que no cumplen unos criterios de uso habitual, edad o lista de confianza|Bloquear, Auditoría, No configurado|Bloquear la ejecución de los archivos ejecutables a menos que cumplan unos criterios de uso habitual, edad o lista de confianza.|

#### <a name="controlled-folder-access"></a>Acceso controlado a carpetas

|Nombre de la configuración  |Opciones de configuración  |Descripción  |
|---------|---------|---------|
|Protección de carpetas (ya implementado)|No configurado, Habilitar, Solo auditoría (ya implementado)<br><br> **Nuevo**<br>Impedir la modificación del disco, Auditar la modificación del disco|
Proteger los archivos y carpetas frente a cambios no autorizados de aplicaciones hostiles.<br><br>**Habilitar**: impedir que las aplicaciones que no son de confianza modifiquen o eliminen archivos en carpetas protegidas y que escriban en los sectores de disco.<br><br>
**Solo impedir la modificación del disco**:<br>Impedir que las aplicaciones que no son de confianza escriban en los sectores de disco. Las aplicaciones que no son de confianza todavía podrán modificar o eliminar archivos en las carpetas protegidas.|

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nueva configuración de Protección de aplicaciones de Windows Defender <!-- 1631890 -->

- **Habilitar la aceleración gráfica**

Los administradores pueden habilitar un procesador de gráficos virtuales para la Protección de aplicaciones de Windows Defender. Esta configuración permite que la CPU descargue el procesamiento de gráficos a la vGPU. Esto puede mejorar el rendimiento cuando se trabaja con sitios web con gran cantidad de datos gráficos o se ve un vídeo dentro del contenedor.

- **SaveFilestoHost**

Los administradores podrán habilitar que los archivos pasen de Microsoft Edge ejecutándose en el contenedor al sistema de archivos de host. Al activarlo, permitirá que los usuarios descarguen los archivos de Microsoft Edge en el contenedor al sistema de archivos de host.

### <a name="see-enrollment-restrictions-per-user----1634444---"></a>Vea las restricciones de inscripción por usuario <!-- 1634444 -->
En la hoja de solución de problemas, podrá ver las restricciones de inscripción que están en vigor para cada usuario.

### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configurar una aplicación MSI móvil de auto-actualización <!-- 1740840 -->
Podrá configurar una aplicación MSI móvil de auto-actualización conocida para que pase por alto el proceso de comprobación de versión. Esta capacidad es útil para evitar encontrarse en una condición de carrera. Por ejemplo, esto puede ocurrir cuando el desarrollador de aplicaciones va a auto-actualizar la aplicación y también se está actualizando mediante Intune. Ambos podrían tratar de aplicar una versión de la aplicación en el cliente de Windows, lo que podría crear un conflicto.

### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133---"></a>Adiciones a la configuración de seguridad del sistema para las directivas de cumplimiento de Windows 10 y posteriores <!--1704133 -->

Estarán disponibles las adiciones a la configuración de cumplimiento de Windows 10, incluida la necesidad del Firewall y el Antivirus de Windows Defender.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusión o exclusión de la asignación de aplicaciones con base en grupos para Android Enterprise <!-- 1813081 -->
Durante la asignación de aplicaciones y después de seleccionar un tipo de asignación, Android Enterprise (anteriormente conocido como Android for Work) es compatible con la funcionalidad de exclusión.


### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Conjuntos de licencias de aplicaciones relacionadas admitidas en Intune <!-- 1864117 -->
Intune en Azure Portal admitirán conjuntos de licencias de aplicaciones relacionadas como un elemento de aplicación único en la interfaz de usuario. Además, las aplicaciones con licencia sin conexión sincronizadas desde Microsoft Store para Empresas se consolidarán en una entrada de aplicación única y los detalles de implementación de los paquetes individuales se migrarán a la entrada única. Para ver los conjuntos de licencias de aplicaciones relacionadas en Azure Portal, seleccione **Licencias de aplicaciones** desde la hoja **Aplicaciones móviles**.

<!-- the following are present prior to 1802 -->

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>Nueva opción para la autenticación de usuario para la inscripción masiva de Apple <!-- 747625 -->
Intune le ofrecerá la opción de autenticar los dispositivos mediante la aplicación Portal de empresa para los siguientes métodos de inscripción:

- Programa de inscripción de dispositivos de Apple
- Apple School Manager
- Inscripción de Apple Configurator

Al usar la opción Portal de empresa, se puede aplicar la autenticación multifactor de Azure Active Directory sin bloquear estos métodos de inscripción.

Al usar la opción Portal de empresa, Intune omite la autenticación de usuario en el Asistente de configuración de iOS para la inscripción de afinidad del usuario. Esto significa que el dispositivo se inscribe inicialmente como un dispositivo sin usuario, por lo que no recibirá las configuraciones ni las directivas de grupos de usuarios. Solo recibirá las configuraciones y las directivas de grupos de dispositivos. Sin embargo, Intune instalará automáticamente la aplicación Portal de empresa en el dispositivo. El primer usuario que inicie la aplicación Portal de empresa e inicie sesión en ella se asociará con el dispositivo en Intune. En este momento, el usuario recibirá las configuraciones y las directivas de sus grupos de usuarios. No se puede cambiar la asociación del usuario sin volver a realizar la inscripción.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Compatibilidad de Intune con varias cuentas del programa del Programa de inscripción de dispositivos (DEP) de Apple o de Apple School Manager (ASM) <!-- 747685 -->
Intune admitirá la inscripción de dispositivos de hasta 100 cuentas distintas del Programa de inscripción de dispositivos de Apple o de Apple School Manager. Cada token cargado puede administrarse por separado para los perfiles y los dispositivos de inscripción. Es posible asignar un perfil de inscripción diferente para cada token de DEP/School Manager. Si se cargan varios tokens de School Manager, solo pueden compartirse de uno en uno con Microsoft School Data Sync.

Tras la migración, la versión beta de las API Graph y los scripts publicados para la administración de Apple DEP o ASM en Graph ya no funcionará. Las nuevas versiones beta de las API Graph están en desarrollo y se publicarán después de la migración.

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Destinación de las directivas de cumplimiento a dispositivos en grupos de dispositivos <!--1307012 -->

Podrá destinar las directivas de cumplimiento a usuarios en los grupos de usuarios. Podrá destinar las directivas de cumplimiento a dispositivos en los grupos de dispositivos.

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Datos cifrados de Windows Information Protection (WIP) en los resultados de la búsqueda de Windows <!-- 1469193 -->

Un nuevo parámetro de configuración de la directiva de Windows Information Protection (WIP) permitirá controlar si los datos cifrados por WIP se incluyen en los resultados de la búsqueda de Windows.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Impresión remota a través de una red segura <!-- 1709994  -->
Las soluciones de impresión móvil inalámbricas de PrinterOn permitirán a los usuarios imprimir remotamente desde cualquier lugar en cualquier momento a través de una red segura. PrinterOn se integrará con el SDK de aplicaciones de Intune para iOS y Android. Podrá destinar las directivas de protección de aplicaciones a esta aplicación a través de la hoja **Directivas de protección de aplicaciones** de Intune de la consola de administración. Los usuarios finales podrán descargar la aplicación "PrinterOn for Microsoft" a través de Play Store o iTunes para usarla dentro de su ecosistema de Intune.



### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>API Graph de Microsoft para Intune - Disponibilidad General<!-- 1833289 -->
Las API de Intune en Microsoft Graph proporcionarán acceso mediante programación a los datos y métodos para automatizar acciones administrativas para el servicio de Intune.  Con la **disponibilidad general** de estas API, los clientes, asociados y desarrolladores podrán aprovechar las API para integrarlas con soluciones internas o comerciales que guarden relación o tengan que ser compatibles con Intune u otros servicios de Microsoft disponibles en Microsoft Graph.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Directivas de protección de aplicaciones  <!-- 679615 -->
Las directivas de Intune App Protection ofrecerán la capacidad de crear directivas predeterminadas globales para habilitar rápidamente la protección en todos los usuarios de todo el inquilino.

### <a name="new-ios-device-action------1244701---"></a>Nueva acción de dispositivo iOS   <!-- 1244701 -->
Puede apagar los dispositivos iOS 10.3 supervisados. Esta acción apaga inmediatamente el dispositivo sin enviar una advertencia al usuario final. La acción **Shut down (supervised only)** [Apagar (solo con supervisión)] se puede encontrar en las propiedades de dispositivos cuando se selecciona un dispositivo en la carga de trabajo del **dispositivo**.

### <a name="intune-provides-the-account-move-operation-----1573558-1579830---"></a>Intune proporciona la operación Movimiento de cuenta <!-- 1573558, 1579830 -->
El **Movimiento de cuenta** migra un inquilino de una unidad de escalado de Azure (ASU) a otra. El **Movimiento de cuenta** se puede usar para ambos escenarios iniciados por el cliente, cuando se llama al equipo de soporte técnico de Intune para solicitarlo, y también puede tratarse de un escenario de Microsoft donde este necesita hacer ajustes al servicio en el back-end. Durante el **Movimiento de cuenta**, el inquilino entra en el modo de solo lectura (ROM). Las operaciones de servicio, como la inscripción, el cambio de nombre de los dispositivos, la actualización del estado de cumplimiento, presentarán errores durante el período de ROM.

El cambio soluciona la confusión que se produce cuando una aplicación se asigna a varios grupos con propósitos de aplicación distintos.

Si quiere que la aplicación esté disponible en el portal de trabajo de la información y en el Portal de empresa antes de la publicación de la versión de noviembre, tiene dos opciones:

1. Quitar la asignación **No aplicable** para su grupo.
2. Crear un nuevo grupo que no incluya miembros con el propósito **Requerido y Disponible** asignado, y asignar ese grupo como **No aplicable**.

Para más información, consulte [Asignación de aplicaciones a grupos con Microsoft Intune](apps-deploy.md).

> [!Note]
> Después del lanzamiento, la versión ya no podrá ver ni modificar las asignaciones de aplicación de administración de dispositivos móviles (MDM) en la consola de Intune clásica. No obstante, puede usar la consola de Azure o Graph API de Intune para asignar las aplicaciones.

### <a name="configure-an-ios-app-pin----1586774---"></a>Configurar un PIN de aplicación iOS <!-- 1586774 -->
Pronto podrá solicitar un PIN para las aplicaciones iOS de destino. En Azure Portal puede configurar el requisito de PIN y la fecha de expiración en días. Para obtener acceso a una aplicación de iOS, se le pedirá al usuario que establezca y use un nuevo PIN. Solo las aplicaciones iOS que tienen habilitada la protección aplicaciones con Intune App SDK serán compatibles con esta característica.

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Actualización de la experiencia del usuario en la aplicación del Portal de empresa para iOS <!--1412866-->

Lanzaremos una actualización importante de la experiencia de usuario para la aplicación del Portal de empresa para iOS. La actualización contará con un cambio de diseño visual completo, que incluye una apariencia y aspecto modernizados con mayor facilidad de uso y accesibilidad. Se mantendrán todas las funcionalidades del Portal de empresa de iOS actuales.

Ofrecemos una versión preliminar de la aplicación del Portal de empresa actualizada para iOS a través del programa TestFlight de Apple para que la use y nos envíe sus comentarios. Regístrese en https://aka.ms/intune_ios_cp_testflight para obtener acceso a TestFlight. 

![imágenes de avance para la nueva aplicación del Portal de empresa de iOS](./media/ios-cp-app-redesign-1801-teaser.png)

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Los sitios web de Azure Active Directory pueden requerir la aplicación Intune Managed Browser y compatibilidad con el inicio de sesión único para Managed Browser (versión preliminar pública) <!-- 710595 -->   
Con Azure Active Directory (Azure AD), podrá restringir el acceso a sitios web en dispositivos móviles a la aplicación Intune Managed Browser. En Managed Browser, los datos del sitio web permanecen seguros y separados de los datos personales del usuario final. Además, Managed Browser admite funciones de inicio de sesión único para sitios protegidos por Azure AD. Al iniciar sesión en Managed Browser, o al usarlo en un dispositivo con otra aplicación administrada por Intune, se permite que Managed Browser tenga acceso a sitios corporativos protegidos por Azure AD sin necesidad de que el usuario escriba sus credenciales. Esta funcionalidad se aplica a sitios como Outlook Web Access (OWA) y SharePoint Online, así como a otros sitios corporativos, como los recursos de intranet a los que se tiene acceso a través de Azure App Proxy.

<!-- the following are present prior to 1709 -->
### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune App Protection y Herramientas de desarrollo de Citrix MDX <!-- 709185 -->
Puede administrar dispositivos y aplicaciones con una combinación de Citrix XenMobile MDX y Microsoft Intune. Esto le permite administrar aplicaciones con la directiva de protección de aplicaciones de Intune mientras usa tecnología mVPN de Citrix.

Puede buscar un repositorio de código que contiene la herramienta de ajuste de aplicaciones de Intune e Intune App SDK para iOS y Android, que se integra con la tecnología mVPN de Citrix MDX.

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>Redireccionamiento de los usuarios de macOS a la nueva aplicación Portal de empresa <!--1380728-->   
Cuando un usuario final inicia sesión en el sitio web del Portal de empresa para inscribir su dispositivo macOS, se le dirigirá a la descarga de la nueva aplicación Portal de empresa para macOS a fin de que complete el proceso. Esto ocurre con los dispositivos macOS que usan OS X El Capitan 10.11 o una versión posterior. 

<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Compatibilidad de Intune Managed Browser con iOS y Android <!-- 1374196 -->
A partir de octubre de 2017, la aplicación Intune Managed Browser en dispositivos Android admitirá solo los dispositivos con Android 4.4 y versiones posteriores. La aplicación Intune Managed Browser en iOS solo admitirá dispositivos con iOS 9.0 y versiones posteriores. Las versiones anteriores de iOS y Android podrán seguir usando Intune Managed Browser, pero no podrán instalar nuevas versiones de la aplicación y es posible que no puedan tener acceso a todas las funcionalidades de la aplicación. Le recomendamos que actualice la versión del sistema operativo de estos dispositivos a una que sea compatible.

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Mensaje de error mejorado cuando un usuario alcanza el número máximo de dispositivos permitidos para la inscripción <!-- 1270370 -->
En lugar de un mensaje de error genérico, los usuarios finales con dispositivos Android ven un mensaje de error descriptivo que requiere acción: "Ya ha inscrito el máximo número de dispositivos permitidos por su administrador de TI. Quite un dispositivo inscrito o reciba ayuda de su administrador de TI".



## <a name="notices"></a>Notificaciones

No hay ningún aviso activo en este momento.



### <a name="see-also"></a>Vea también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.


