---
title: 'Configuración de dispositivo iOS/iPadOS en Microsoft Intune: Azure | Microsoft Docs'
titleSuffix: ''
description: Agregue, configure o cree valores en dispositivos iOS/iPadOS para restringir características, lo que incluye establecer requisitos de contraseña, controlar la pantalla de bloqueo, usar aplicaciones integradas, agregar aplicaciones restringidas o aprobadas, controlar dispositivos Bluetooth, conectarse a la nube para realizar copias de seguridad y almacenamiento, habilitar la pantalla completa, agregar dominios y controlar la manera en que los usuarios interactúan con el explorador web Safari en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1e352ca0c0100ebe1756d621feb725e040521901
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513082"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>Configuración de dispositivos iOS e iPadOS para permitir o restringir características mediante Intune

En este artículo se enumeran y describen los diferentes valores de configuración que se pueden controlar en los dispositivos iOS e iPadOS. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores para habilitar o deshabilitar características, establecer reglas de contraseña, permitir o restringir determinadas aplicaciones, etc.

Estos valores se agregan a un perfil de configuración del dispositivo en Intune y luego se asignan o implementan en los dispositivos iOS/iPadOS.

> [!TIP]
> Esta configuración usa las opciones de MDM de Apple. Para obtener más información sobre esta configuración, vea [Configuración de administración de dispositivos móviles de Apple](https://support.apple.com/guide/mdm/welcome/web) (abre el sitio web de Apple).

## <a name="before-you-begin"></a>Antes de comenzar

[Crear un perfil de configuración de restricciones de dispositivos](../device-restrictions-configure.md).

> [!NOTE]
> Esta configuración se aplica a diferentes tipos de inscripción, mientras que algunas opciones se aplican a todas las opciones de inscripción. Para más información sobre los diferentes tipos de inscripción, consulte [Inscripción en iOS/iPadOS](../ios-enroll.md).

## <a name="general"></a>General

### <a name="settings-apply-to-all-enrollment-types"></a>Las opciones se aplican a: Todos los tipos de inscripción

- **Compartir los datos de uso**: Elija **Bloquear** para evitar que el dispositivo envíe a Apple datos de diagnóstico y uso. **No configurado** (valor predeterminado) permite que se envíen estos datos.

- **Captura de pantalla**: elija **Bloquear** para impedir que se hagan capturas de pantalla en el dispositivo. En iOS/iPadOS 9.0 y versiones más recientes, también se bloquean las grabaciones de pantalla. **No configurado** (valor predeterminado) permite que el usuario capture el contenido de la pantalla como imagen o como vídeo.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivos, también en el caso de la inscripción automatizada (con supervisión)

- **Certificados TLS que no son de confianza**: Elija **Bloquear** para evitar en el dispositivo los certificados de Seguridad de la capa de transporte (TLS) que no son de confianza. **Sin configurar** (valor predeterminado) permite certificados TLS.
- **Bloquear actualizaciones móviles de PKI**: **Bloquear** impide que los usuarios reciban actualizaciones de software, a menos que el dispositivo esté conectado a un equipo. **No configurado** (valor predeterminado): permite que un dispositivo reciba actualizaciones de software sin estar conectado a un equipo.
- **Limitar el seguimiento de publicidad**: Elija **Limitar** para deshabilitar el identificador de publicidad del dispositivo. **Sin configurar** (valor predeterminado) lo mantiene habilitado.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **Modificación de la configuración del envío de diagnósticos**: **Bloquear** evita que el usuario cambie la configuración de análisis de aplicación y envío de diagnóstico en **Datos de diagnóstico y uso** (configuración del dispositivo). **No configurado** (valor predeterminado) permite que el usuario cambie esta configuración del dispositivo.

  Para usar esta opción, establezca **Compartir datos de uso** en **Bloquear**.

  Esta característica se aplica a:  
  - iOS 9.3.2 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Observación de pantalla remota mediante la aplicación Classroom**: Elija **Bloquear** para evitar que la aplicación Classroom vea de forma remota la pantalla en el dispositivo. **No configurado** (valor predeterminado) permite que la aplicación Aula de Apple vea la pantalla.

  Para usar esta opción, establezca **Captura de pantalla** en **Bloquear**.

  Esta característica se aplica a:  
  - iOS 9.3 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Observación de pantalla sin mensajes por la aplicación Classroom**: Si está establecido en **Permitir**, los profesores pueden observar de manera silenciosa la pantalla de los dispositivos iOS/iPadOS de los alumnos con la aplicación Classroom sin que estos lo sepan. Los dispositivos de alumnos inscritos en una clase con la aplicación Aula automáticamente dan permiso al profesor de ese curso. **Sin configurar** (valor predeterminado) deshabilita esta característica.

  Para usar esta opción, establezca **Captura de pantalla** en **Bloquear**.

- **Confianza de aplicaciones empresariales**: Elija **Bloquear** para quitar el botón **Trust Enterprise Developer** en Configuración > General > Administración de perfiles y dispositivos del dispositivo. **No configurado** (valor predeterminado) permite que el usuario elija confiar en aplicaciones no descargadas de la tienda de aplicaciones.
- **Modificación de la cuenta**: Cuando se establece en **Bloquear**, el usuario no puede actualizar la configuración específica del dispositivo en la aplicación de configuración de iOS/iPadOS. Por ejemplo, el usuario no puede crear nuevas cuentas de dispositivo ni modificar el nombre de usuario o la contraseña. **No configurado** (valor predeterminado) permite que los usuarios cambien esta configuración.

  Esta característica también se aplica a la configuración accesible desde la aplicación de configuración de iOS/iPadOS, como Correo, Contactos, Calendario, Twitter, etc. Esta característica no se aplica a las aplicaciones con la configuración de la cuenta que no se pueden configurar desde la aplicación de configuración de iOS/iPadOS, como la aplicación Microsoft Outlook.

- **Tiempo de uso**: seleccione **Bloquear** para evitar que los usuarios establezcan sus propias restricciones en Tiempo de uso (configuración de dispositivo). **No configurado** permite que el usuario configure las restricciones de dispositivo (como las restricciones de privacidad y contenido o el control parental) en el dispositivo.

  Este es el nuevo nombre de que se ha cambiado de la configuración **Habilitación de restricciones en la configuración del dispositivo**. Impacto de este cambio:  
  
  - iOS 11.4.1 y superior: **Bloquear** impide que los usuarios finales establezcan sus propias restricciones en la configuración del dispositivo. El comportamiento es el mismo y no hay ningún cambio para los usuarios finales.
  - iOS 12.0 y versiones más recientes: **Bloquear** evita que los usuarios finales establezcan su propio **Tiempo de uso** en la configuración del dispositivo (Configuración > General > Tiempo de uso), incluidas restricciones de contenido y privacidad. En los dispositivos actualizados a iOS 12.0 ya no aparecerá la pestaña de restricciones en la configuración del dispositivo (Configuración > General > Administración de dispositivos > Perfil de administración > Restricciones). Estas opciones se encuentran en **Tiempo de uso**.
  
- **Usar la opción de borrar todo el contenido y la configuración del dispositivo**: seleccione **Bloquear** para que los usuarios no puedan usar la opción de borrar todo el contenido y la configuración del dispositivo. **No configurado** (valor predeterminado) permite que los usuarios accedan a esta configuración.
- **Modificación del nombre del dispositivo**: Elija **Bloquear** para que no se pueda cambiar el nombre del dispositivo. **No configurado** (valor predeterminado) permite que el usuario cambie el nombre del dispositivo.
- **Modificación de la configuración de notificaciones**: Elija **Bloquear** para que no se pueda cambiar la configuración de notificaciones. **No configurado** (valor predeterminado) permite que el usuario cambie la configuración de las notificaciones del dispositivo.
- **Modificación del fondo de pantalla**: **Bloquear** evita que se cambie el fondo de pantalla. **No configurado** (valor predeterminado) permite que el usuario cambie el fondo de pantalla del dispositivo.
- **Modificación de la configuración de confianza de aplicaciones empresariales**: **Bloquear** evita que el usuario cambie la configuración de confianza de aplicaciones empresariales en dispositivos supervisados. **No configurado** (valor predeterminado) permite que el usuario confíe en aplicaciones no descargadas de la tienda de aplicaciones.
- **Cambios en el perfil de configuración**: **Bloquear** evita los cambios del perfil de configuración en el dispositivo. **No configurado** (valor predeterminado) permite que el usuario instale perfiles de configuración.
- **Bloqueo de activación**: Elija **Permitir** para habilitar el bloqueo de activación en dispositivos iOS/iPadOS supervisados. Bloqueo de activación dificulta que un dispositivo robado o perdido pueda reactivarse.
- **Bloquear la eliminación de aplicaciones**: Elija **Bloquear** para evitar que los usuarios quiten aplicaciones. **No configurado** (valor predeterminado) permite que los usuarios quiten aplicaciones del dispositivo.
- **Permitir accesorios USB con el dispositivo bloqueado**: **Permitir** permite que los accesorios USB intercambien datos con un dispositivo que ha estado bloqueado durante más de una hora. **No configurado** (valor predeterminado) no actualiza el modo restringido de USB en el dispositivo y los accesorios USB no podrán transferir datos del dispositivo si están bloqueados durante más de una hora.
- **Forzar fecha y hora automáticas**: **Requerir** obliga a los dispositivos supervisados a establecer la fecha y la hora automáticamente. La zona horaria del dispositivo se actualiza cuando el dispositivo tiene conexiones móviles o tiene Wi-Fi con servicios de ubicación habilitados.
- **Requerir que los estudiantes soliciten permiso para dejar el curso de Classroom**: **Requerir** obliga a los alumnos inscritos en un curso no administrado con la aplicación Aula a pedir permiso al profesor para dejar el curso. **No configurado** (valor predeterminado) no obliga al alumno a pedir permiso.

  Esta característica se aplica a:  
  - iOS 11.3 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Permitir a Classroom bloquearse en una aplicación y bloquear el dispositivo sin preguntar**: **Habilitar** permite que el profesor bloquee aplicaciones o el dispositivo mediante la aplicación Classroom sin preguntar al alumno. Al bloquear las aplicaciones, los dispositivos solo pueden acceder a las aplicaciones especificadas por el profesor. **Sin configurar** (valor predeterminado) impide que los profesores bloqueen aplicaciones o dispositivos que usan la aplicación Aula sin preguntar al alumno.

  Esta característica se aplica a:  
  - iOS 11.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Unirse a las clases de Classroom automáticamente sin preguntar**: **Habilitar** permite automáticamente a los alumnos unirse a una clase de la aplicación Classroom sin preguntar al profesor. **Sin configurar** (valor predeterminado) notifica al profesor que hay alumnos que quieren unirse a una clase que se encuentra en la aplicación Aula.

  Esta característica se aplica a:  
  - iOS 11.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Bloquear creación de VPN**: **Bloquear** evita que los usuarios creen una configuración de VPN. **No configurado** (valor predeterminado) permite que los usuarios creen VPN en el dispositivo.
- **Modificar la configuración de eSIM**: **Bloquear** evita que los usuarios quiten o agreguen un plan de telefonía móvil para el eSIM en el dispositivo. **No configurado** (valor predeterminado) permite que los usuarios cambien esta configuración.

  Esta característica se aplica a:  
  - iOS 12.1 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Aplazar las actualizaciones de software**: cuando se establece en **Sin configurar** (valor predeterminado), las actualizaciones de software se muestran en el dispositivo a medida que Apple las publica. Por ejemplo, si Apple publica una actualización de iOS/iPadOS en una fecha concreta, dicha actualización se mostrará de forma natural en el dispositivo en torno a la fecha de publicación.

  **Habilitar** permite retrasar la visualización de las actualizaciones en el dispositivo, entre 0 y 90 días. Esta configuración no controla cuándo se instalan las actualizaciones. 

  - **Retrasar la visibilidad de las actualizaciones de software**: especifique un valor entre 0 y 90 días. Cuando el retraso expira, los usuarios reciben una notificación para actualizar a la versión más antigua del sistema operativo que estaba disponible cuando se desencadenó el retraso.

    Por ejemplo, si iOS 12.a está disponible **el 1 de enero** y **Retrasar la visibilidad** está establecido en **5 días**, iOS 12.a no se muestra como una actualización disponible en los dispositivos de usuario final. Al **sexto día** después de la publicación, esta actualización estará disponible y los usuarios finales podrán instalarla.

    Esta configuración solo es aplicable a:  
    - iOS 11.3 y versiones más recientes
    - IPadOS 13.0 y versiones más recientes

## <a name="password"></a>Contraseña

### <a name="settings-apply-to-all-enrollment-types"></a>Las opciones se aplican a: Todos los tipos de inscripción

- **Contraseña**: **Requerir** que el usuario final escriba una contraseña para acceder al dispositivo. **No configurado** (valor predeterminado) permite que los usuarios accedan al dispositivo sin tener que escribir una contraseña.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivos, también en el caso de la inscripción automatizada (con supervisión)

> [!IMPORTANT]
> En los dispositivos inscritos por usuarios, si configura cualquier opción de contraseña, la configuración de **Contraseñas sencillas** se establece automáticamente en **Bloquear** y se aplica un PIN de 6 dígitos.
>
> Por ejemplo, configura el valor **Caducidad de la contraseña** e inserta esta directiva en dispositivos con usuarios inscritos. En los dispositivos, ocurre lo siguiente:
>
> - Se omite el valor de **Caducidad de la contraseña**.
> - No se permiten contraseñas sencillas, como `1111` o `1234`.
> - Se aplica un PIN de 6 dígitos.

- **Contraseñas sencillas**: Elija **Bloquear** para exigir contraseñas más complejas. **No configurado** permite contraseñas sencillas, como `0000` y `1234`.

- **Tipo de contraseña requerida**: Elija el tipo de contraseña que requiere la organización. Las opciones son:
  - **Valor predeterminado de dispositivo**
  - **Numérico**
  - **Alfanumérico**
- **Número de caracteres no alfanuméricos en la contraseña**: Especifique el número de caracteres de símbolo, como `#` o `@`, que deben incluirse en la contraseña.

- **Longitud mínima de la contraseña**: especifique la longitud mínima que un usuario debe escribir, entre 4 y 14 caracteres. En dispositivos inscritos por el usuario, especifique una longitud de entre 4 y 6 caracteres.
  
  > [!NOTE]
  > En el caso de los dispositivos inscritos por el usuario, los usuarios pueden establecer un PIN de más de 6 dígitos. Pero en el dispositivo no se exigen más de 6 dígitos. Por ejemplo, un administrador establece la longitud mínima en `8`. En los dispositivos inscritos por el usuario, solo se exige a los usuarios establecer un PIN de 6 dígitos. Intune no exige un PIN de más de 6 dígitos en los dispositivos inscritos por el usuario.

- **Número de errores de inicio de sesión antes de borrar el dispositivo**: escriba el número de errores de inicio de sesión que se permiten antes de que se borre el dispositivo (entre 4 y 11).
  
  iOS/iPadOS cuenta con seguridad integrada que puede afectar a esta configuración. Por ejemplo, iOS/iPadOS puede retrasar la activación de la directiva en función del número de errores de inicio de sesión. También puede considerar la especificación repetida del mismo código de acceso como un intento. La [guía de seguridad de iOS/iPadOS](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) de Apple (abre el sitio web de Apple) es un buen recurso y proporciona detalles más concretos sobre los códigos de acceso.
  
- **Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña**<sup>1</sup>: Especifique cuánto tiempo puede permanecer inactivo el dispositivo antes de que el usuario deba volver a escribir la contraseña. Si escribe un tiempo mayor al que está establecido actualmente en el dispositivo, este pasará por alto el tiempo que escribió. Compatible con dispositivos que ejecutan iOS 8.0 + y iPadOS 13.0+.

- **Máximo de minutos de inactividad hasta que se bloquea la pantalla**<sup>1</sup>: Escriba el número máximo de minutos de inactividad que se permiten en el dispositivo hasta que se bloquea la pantalla.

  **Opciones de iOS/iPadOS**:  

  - **Sin configurar** (valor predeterminado): Intune no modifica este valor.
  - **Inmediatamente**: la pantalla se bloquea tras 30 segundos de inactividad.
  - **1**: la pantalla se bloquea tras 1 minuto de inactividad.
  - **2**: la pantalla se bloquea tras 2 minutos de inactividad.
  - **3**: la pantalla se bloquea tras 3 minutos de inactividad.
  - **4**: la pantalla se bloquea tras 4 minutos de inactividad.
  - **5**: la pantalla se bloquea tras 5 minutos de inactividad.

  **Opciones de iPadOS**:  

  - **Sin configurar** (valor predeterminado): Intune no modifica este valor.
  - **Inmediatamente**: la pantalla se bloquea tras 2 minutos de inactividad.
  - **2**: la pantalla se bloquea tras 2 minutos de inactividad.
  - **5**: la pantalla se bloquea tras 5 minutos de inactividad.
  - **10**: la pantalla se bloquea tras 10 minutos de inactividad.
  - **15**: la pantalla se bloquea tras 15 minutos de inactividad.

  Si un valor no se aplica a iOS ni iPadOS, Apple usa el valor *inferior* más cercano. Por ejemplo, si especifica `4` minutos, los dispositivos iPadOS usan `2` minutos. Si especifica `10` minutos, los dispositivos iOS usan `5` minutos. Se trata de una limitación de Apple.
  
  > [!NOTE]
  > La interfaz de usuario de Intune para esta configuración no separa los valores admitidos de iOS e iPadOS. La interfaz de usuario podría actualizarse en una versión futura.

- **Expiración de la contraseña (días)** : Especifique el número de días antes de que se deba cambiar la contraseña del dispositivo.
- **Impedir la reutilización de contraseñas anteriores**: Escriba el número de contraseñas nuevas que se deben usar antes de poder reutilizar una antigua.
- **Desbloqueo de Touch ID y Face ID**: elija **Bloquear** para impedir el uso de una huella digital o una cara para desbloquear el dispositivo. **No configurado** permite que el usuario desbloquee el dispositivo con estos métodos.

  El bloqueo de esta configuración también evita el uso de la autenticación de FaceID para desbloquear el dispositivo.

  Face ID se aplica a:  
  - iOS 11.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **Modificación del código de acceso**: Elija **Bloquear** para evitar que se cambie, se agregue o se quite el código de acceso. En los dispositivos supervisados, los cambios en las restricciones del código de acceso se pasan por alto después de bloquear esta característica. **No configurado** (valor predeterminado) permite agregar, cambiar o quitar códigos de acceso.

  - **Modificación de Touch ID y Face ID**: la opción **Bloquear** impide que el usuario cambie, agregue o quite huellas digitales de Touch ID y Face ID. **No configurado** (valor predeterminado) permite que el usuario actualice las huellas digitales de TouchID y de Face ID del dispositivo.

    El bloqueo de esta configuración también evita que el usuario cambie, agregue o quite la autenticación de FaceID.

    Face ID se aplica a:  
    - iOS 11.0 y versiones más recientes
    - IPadOS 13.0 y versiones más recientes

- **Impedir el relleno automático de contraseñas**: Elija **Bloquear** para evitar el uso de la característica Autorrellenar contraseñas en iOS/iPadOS. Si elige **Bloquear** tendrá también este impacto:

  - No se les pide a los usuarios que usen una contraseña guardada en Safari ni en ninguna aplicación.
  - Se deshabilitan las contraseñas seguras automáticas y no se sugieren contraseñas seguras a los usuarios.

  **No configurado** (valor predeterminado) permite estas características.

- **Impedir las solicitudes de proximidad de contraseñas**: Elija **Bloquear** para que el dispositivo de un usuario no solicite contraseñas de los dispositivos cercanos. **No configurado** (valor predeterminado) permite estas solicitudes de contraseña.
- **Impedir el uso compartido de contraseñas**: **Bloquear** evita el uso compartido de contraseñas entre dispositivos mediante AirDrop. **No configurado** (valor predeterminado) permite compartir las contraseñas.
- **Requerir autenticación con Touch ID o Face ID para el relleno automático de datos de tarjetas de crédito o contraseñas**: cuando se establece en **Requerir**, los usuarios deben autenticarse mediante TouchID o FaceID para que los datos de la tarjeta de crédito o las contraseñas puedan rellenarse automáticamente en Safari y otras aplicaciones. **Sin configurar** (valor predeterminado) permite a los usuarios controlar esta característica en la configuración del dispositivo.

  Esta característica se aplica a:  
  - iOS 11.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes
  
<sup>1</sup> Al configurar los valores **Máximo de minutos de inactividad hasta que se bloquea la pantalla** y **Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña**, se aplican en secuencia. Por ejemplo, si establece el valor para ambas opciones en **5** minutos, a pantalla se apaga automáticamente transcurridos cinco minutos y el dispositivo se bloquea después de cinco minutos más. Sin embargo, si el usuario apaga la pantalla manualmente, la segunda opción se aplica inmediatamente. En el mismo ejemplo, una vez que el usuario apaga la pantalla, el dispositivo se bloquea cinco minutos más tarde.

## <a name="locked-screen-experience"></a>Experiencia de pantalla bloqueada

### <a name="settings-apply-to-all-enrollment-types"></a>Las opciones se aplican a: Todos los tipos de inscripción

- **Acceso a Centro de control con dispositivo bloqueado**: Elija **Bloquear** para evitar el acceso a la aplicación Centro de control cuando el dispositivo está bloqueado. **No configurado** (valor predeterminado) permite que los usuarios accedan a la aplicación Centro de control cuando el dispositivo está bloqueado.
- **Notificaciones con dispositivo bloqueado**: **Bloquear** evita el acceso a las notificaciones cuando el dispositivo está bloqueado. **No configurado** (valor predeterminado) permite que el usuario acceda a las notificaciones sin que sea necesario desbloquear el dispositivo.
- **Vista Hoy con dispositivo bloqueado**: **Bloquear** evita el acceso a la vista Hoy cuando el dispositivo está bloqueado. **No configurado** (valor predeterminado) permite que el usuario vea la vista Hoy cuando el dispositivo está bloqueado.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivos, también en el caso de la inscripción automatizada (con supervisión)

- **Notificaciones de Wallet con dispositivo bloqueado**: **Bloquear** evita el acceso a la aplicación Wallet cuando el dispositivo está bloqueado. **No configurado** (valor predeterminado) permite que el usuario acceda a la aplicación Wallet mientras el dispositivo está bloqueado.

## <a name="app-store-doc-viewing-gaming"></a>Tienda de aplicaciones, presentación de documentos, juegos

### <a name="settings-apply-to-all-enrollment-types"></a>Las opciones se aplican a: Todos los tipos de inscripción

- **Visualización de documentos corporativos en aplicaciones no administradas**: **Bloquear** evita la visualización de documentos corporativos en aplicaciones no administradas. **No configurado** (valor predeterminado) permite ver los documentos corporativos en cualquier aplicación. Por ejemplo, se quiere evitar que los usuarios guarden archivos de la aplicación OneDrive en Dropbox. Configure este valor como **Bloquear**. Después de que el dispositivo recibe la directiva (por ejemplo, después de un reinicio), ya no le permite guardar.


  > [!NOTE]
  > Cuando esta configuración está bloqueada, también se bloquean los teclados de terceros instalados desde App Store.

  - **Permitir que las aplicaciones no administradas lean en cuentas de contactos administradas**: cuando se establece en **Permitir**, las aplicaciones no administradas, como la aplicación integrada Contactos de iOS/iPadOS, pueden leer información de contacto y acceder a ella desde aplicaciones administradas, incluida la aplicación móvil Outlook. **Sin configurar** (valor predeterminado) evita la lectura, incluso la eliminación de duplicados, en la aplicación de contactos integrada en el dispositivo.  
  
    Esta configuración permite o evita la lectura de información de contacto. No controla la sincronización de contactos entre las aplicaciones.
  
    Para usar este valor, establezca la opción **Visualización de documentos corporativos en aplicaciones no administradas** en **Bloquear**.

  Para más información sobre estos dos valores y cómo afecta a Outlook para la sincronización de exportación de contactos de iOS/iPadOS, consulte [Sugerencia de soporte técnico: uso de la configuración de perfil personalizada de Intune con la aplicación Contactos nativa de iOS/iPadOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).

- **Tratar AirDrop como destino no administrado**: **Requerir** obliga a que se considere a Airdrop un destino para colocar no administrado. Impide que las aplicaciones administradas envíen datos mediante AirDrop. 
- **Visualización de documentos no corporativos en aplicaciones corporativas**: **Bloquear** evita la visualización de documentos no corporativos en aplicaciones corporativas. **No configurado** (valor predeterminado) permite ver cualquier documento en aplicaciones administradas corporativas.

  Si se establece en **Bloquear** también se evita la sincronización de la exportación de contactos en Outlook para iOS/iPadOS. Para obtener más información, vea [Sugerencia de soporte técnico: habilitación de la sincronización de contactos entre Outlook e iOS/iPadOS con controles de MDM de iOS12](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453).

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivos, también en el caso de la inscripción automatizada (con supervisión)

- **Requerir contraseña de iTunes Store para todas las compras**: **Requerir** exige al usuario escribir la contraseña del id. de Apple para cada compra en la aplicación o iTunes. **Sin configurar** (valor predeterminado) permite compras sin pedir una contraseña cada vez.
- **Compras desde la aplicación**: Elija **Bloquear** para evitar las compras en la tienda desde la aplicación. **No configurado** (valor predeterminado) permite las compras en la tienda dentro de una aplicación en ejecución.
- **Descargar contenido marcado como "Erótico" en iBooks Store**: Elija **Bloquear** para evitar que los usuarios descarguen archivos multimedia de iBooks Store marcados como eróticos. **No configurado** (valor predeterminado) permite que el usuario descargue libros con la categoría "Erotismo".
- **Permitir que las aplicaciones administradas escriban contactos en cuentas de contactos no administradas**: cuando se establece en **Permitir**, las aplicaciones administradas, como la aplicación móvil Outlook, pueden guardar o sincronizar la información de contacto, como los contactos corporativos y empresariales, en la aplicación Contactos integrada de iOS/iPadOS. Cuando se establece en **No configurado** (valor predeterminado), las aplicaciones administradas no pueden guardar ni sincronizar la información de contacto con la aplicación Contactos integrada de iOS/iPadOS en el dispositivo.
  
  Para usar este valor, establezca la opción **Visualización de documentos corporativos en aplicaciones no administradas** en **Bloquear**.

- **Región de clasificaciones**: Elija la región de clasificaciones que quiere usar para las descargas permitidas. Luego elija las clasificaciones permitidas para **Películas**, **Programas de TV** y **Aplicaciones**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **Tienda de aplicaciones**: **Bloquear** evita el acceso a la tienda de aplicaciones en dispositivos supervisados. **Sin configurar** (valor predeterminado) permite el acceso.

  A partir de iOS/iPadOS 13.0, esta configuración requiere dispositivos supervisados.

  - **Instalación de aplicaciones de App Store**: Elija **Bloquear** para bloquear la Tienda de aplicaciones en la pantalla de inicio del dispositivo. Los usuarios finales pueden seguir usando iTunes o Apple Configurator para instalar aplicaciones. **No configurado** (valor predeterminado) permite la tienda de aplicaciones en la pantalla principal.
  - **Descargas de aplicaciones automáticas**: Elija **Bloquear** para evitar la descarga automática de las aplicaciones compradas en otros dispositivos. No afecta las actualizaciones de las aplicaciones existentes. **No configurado** (valor predeterminado) permite descargar en el dispositivo las aplicaciones compradas en otros dispositivos iOS/iPadOS.

- **Música, podcasts o contenido de noticias explícitos de iTunes**: Elija **Bloquear** para evitar el contenido de música, podcasts o noticias explícito de iTunes. **No configurado** (valor predeterminado) permite que el dispositivo acceda a contenido clasificado para adultos en la tienda.

  A partir de iOS/iPadOS 13.0, esta configuración requiere dispositivos supervisados.

- **Agregando amigos de Game Center**: **Bloquear** evita que los usuarios agreguen amigos de Game Center. **No configurado** (valor predeterminado) permite que el usuario agregue amigos en Game Center.

  A partir de iOS/iPadOS 13.0, esta configuración requiere dispositivos supervisados.

- **Game Center**: **Bloquear** evita el uso de la aplicación Game Center. **No configurado** (valor predeterminado) permite usar la aplicación Game Center en el dispositivo.
- **Juegos multijugador**: Elija **Bloquear** para evitar los juegos multijugador. **No configurado** (valor predeterminado) permite que el usuario disfrute juegos multijugador en el dispositivo.

  A partir de iOS/iPadOS 13.0, esta configuración requiere dispositivos supervisados.

- **Acceso a la unidad de red en la aplicación Files**: mediante el protocolo Bloque de mensajes del servidor (SMB), los dispositivos pueden acceder a archivos u otros recursos de un servidor de red. **Deshabilitar** evita el acceso a archivos de una unidad SMB de red. **Sin configurar** (valor predeterminado) permite el acceso.

  Esta característica se aplica a:  
  - iOS 13.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

## <a name="built-in-apps"></a>Aplicaciones integradas

### <a name="settings-apply-to-all-enrollment-types"></a>Las opciones se aplican a: Todos los tipos de inscripción

- **Siri**: **Bloquear** evita el acceso a Siri. **No configurado** (valor predeterminado) permite usar el asistente de voz Siri en el dispositivo.
  - **Siri con dispositivo bloqueado**: Elija **Bloquear** para evitar el acceso a Siri cuando el dispositivo está bloqueado. **No configurado** (valor predeterminado) permite usar el asistente de voz Siri en el dispositivo cuando está bloqueado.

- **Advertencias de fraude de Safari**: **Requerir** que las advertencias de fraude se muestren en el explorador web en el dispositivo. **No configurado** (valor predeterminado) deshabilita esta característica.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivos, también en el caso de la inscripción automatizada (con supervisión)

- **Búsqueda de Spotlight para devolver resultados de Internet**: **Bloquear** evita que Spotlight devuelva resultados de una búsqueda en Internet. **No configurado** (valor predeterminado) permite que la búsqueda de Spotlight se conecte a Internet para proporcionar resultados de la búsqueda.

- **Cookies de Safari**: Elija cómo se administran las cookies en el dispositivo. Las opciones son:
  - Allow
  - Bloquear todas las cookies
  - Permitir cookies de sitios web visitados
  - Permitir cookies del sitio web actual

- **JavaScript de Safari**: **Bloquear** evita que los scripts de Java del explorador se ejecuten en el dispositivo. **Sin configurar** (valor predeterminado) permite scripts de Java.

- **Ventanas emergentes de Safari**: **Bloquear** para deshabilitar el bloqueador de elementos emergentes del explorador web. **Sin configurar** (valor predeterminado) permite el bloqueador de elementos emergentes.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **Cámara**: elija **Bloquear** para impedir el acceso a la cámara del dispositivo. **No configurado** (valor predeterminado) permite el acceso a la cámara del dispositivo.

  A partir de iOS/iPadOS 13.0, esta configuración requiere dispositivos supervisados.

  - **FaceTime**: **Bloquear** evita el acceso a la aplicación FaceTime. **Sin configurar** (valor predeterminado) permite el acceso a la aplicación FaceTime en el dispositivo.

    A partir de iOS/iPadOS 13.0, esta configuración requiere dispositivos supervisados.

- **Filtro de obscenidad de Siri**: **Requerir** evita que Siri dicte o hable con un lenguaje malsonante.

  Para usar esta opción, establezca **Siri** en **Bloquear**.

- **Siri para consultar contenido generado por usuarios de Internet**: **Bloquear** evita que Siri acceda a sitios web para responder preguntas. **Sin configurar** (valor predeterminado) permite que Siri acceda al contenido generado por usuarios de Internet.

  Para usar esta opción, establezca **Siri** en **Bloquear**.

- **Apple News**: Elija **Bloquear** para evitar el acceso a la aplicación Apple News en el dispositivo. **Sin configurar** (valor predeterminado) permite usar la aplicación Apple News.
- **iBooks Store**: **Bloquear** evita el acceso a la tienda de iBooks. **Sin configurar** (valor predeterminado) permite que los usuarios examinen y compren libros en iBooks Store.
- **Aplicación Mensajes del dispositivo**: **Bloquear** impide que los usuarios usen la aplicación Mensajes para iMessage. Si el dispositivo admite la mensajería de texto, el usuario puede seguir enviando y recibiendo mensajes de texto mediante SMS. **Sin configurar** (valor predeterminado) permite el uso de la aplicación Mensajes para enviar y leer mensajes mediante Internet.
- **Podcasts**: **Bloquear** evita que los usuarios usen la aplicación Podcasts. **Sin configurar** (valor predeterminado) permite usar la aplicación Podcasts.
- **Servicio de música**: **Bloquear** revierte la aplicación Música al modo clásico y deshabilita el servicio Música. **No configurado** (valor predeterminado) permite usar la aplicación Apple Music.
- **Servicio Radio de iTunes**: **Bloquear** evita que los usuarios usen la aplicación iTunes Radio. **Sin configurar** (valor predeterminado) permite usar la aplicación iTunes Radio.
- **iTunes Store**: **Sin configurar** (valor predeterminado) permite iTunes en los dispositivos. **Bloquear** evita que los usuarios usen iTunes en el dispositivo. 

  Esta característica se aplica a:  
  - iOS 4.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Buscar mi iPhone**: **Sin configurar** (valor predeterminado) permite usar esta característica de la aplicación Buscar mi para obtener la ubicación aproximada del dispositivo. **Bloquear** evita esta característica de la aplicación Buscar mi. 

  Esta característica se aplica a:  
  - iOS 13.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Buscar a mis amigos**: **Sin configurar** (valor predeterminado) permite usar esta característica de la aplicación Buscar mi para encontrar familiares y amigos desde un dispositivo Apple o iCloud.com. **Bloquear** evita esta característica de la aplicación Buscar mi.

  Esta característica se aplica a:  
  - iOS 13.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Cambios en la configuración de la aplicación Buscar a mis amigos**: **Bloquear** evita los cambios en la configuración de la aplicación Buscar a mis amigos. **Sin configurar** (valor predeterminado) permite que el usuario cambie la configuración de la aplicación Buscar a mis amigos.

- **Búsqueda de Spotlight para devolver resultados de Internet**: **Bloquear** evita que Spotlight devuelva resultados de una búsqueda en Internet. **No configurado** (valor predeterminado) permite que la búsqueda de Spotlight se conecte a Internet para proporcionar resultados de la búsqueda.

- **Bloquear la eliminación de aplicaciones del sistema del dispositivo**: Elija **Bloquear** para deshabilitar la posibilidad de quitar aplicaciones del sistema del dispositivo. **Sin configuración** (valor predeterminado) permite que los usuarios quiten aplicaciones de sistema.

- **Safari**: **Bloquear** el uso del explorador Safari en el dispositivo. **Sin configurar** (valor predeterminado) permite que los usuarios utilicen el explorador Safari.

  A partir de iOS/iPadOS 13.0, esta configuración requiere dispositivos supervisados.

- **Autorelleno de Safari**: **Bloquear** deshabilita la característica Autorrellenar de Safari en el dispositivo. **No configurado** (valor predeterminado) permite que los usuarios cambien la configuración de Autorrellenar del explorador web.

  A partir de iOS/iPadOS 13.0, esta configuración requiere dispositivos supervisados.

## <a name="restricted-apps"></a>Aplicaciones restringidas

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivos, también en el caso de la inscripción automatizada (con supervisión)

- **Tipo de lista de aplicaciones restringidas**: cree una lista de aplicaciones que los usuarios no pueden instalar ni usar. Las opciones son:

  - **Sin configurar** (valor predeterminado): no hay restricciones en Intune. Los usuarios tienen acceso a las aplicaciones que asigne y a las aplicaciones integradas.
  - **Aplicaciones prohibidas**: aplicaciones no administradas por Intune que no se quieren instalar en el dispositivo. No se evita que los usuarios instalen una aplicación prohibida. Pero si un usuario instala una aplicación de esta lista, se notifica en Intune.
  - **Aplicaciones aprobadas**: aplicaciones que los usuarios pueden instalar. Los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente. No se impide a los usuarios que instalen una aplicación que no se encuentra en la lista aprobada, Pero si lo hacen, se notifica en Intune.

Para agregar aplicaciones a estas listas, puede:

- **Agregar** la dirección URL de la tienda de aplicaciones de iTunes de la aplicación que quiere instalar. Por ejemplo, para agregar la aplicación Carpetas de trabajo de Microsoft, escriba `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` o `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para buscar la dirección URL de una aplicación, abra la tienda de aplicaciones de iTunes y busque la aplicación. Por ejemplo, busque `Microsoft Remote Desktop` o `Microsoft Word`. Seleccione la aplicación y copie la dirección URL.

  También puede usar iTunes para buscar la aplicación y luego usar la tarea **Copiar vínculo** para obtener la dirección URL de la aplicación.

- **Importe** un archivo .csv con detalles sobre la aplicación, incluida la dirección URL. Use el formato `<app url>, <app name>, <app publisher>`. O bien **exporte** una lista existente que incluye la lista de aplicaciones restringidas en el mismo formato.

> [!IMPORTANT]
> Se deben asignar perfiles de dispositivo que usen configuración de aplicaciones restringidas para grupos de usuarios.

## <a name="show-or-hide-apps"></a>Aplicaciones visibles u ocultas

Se aplica a dispositivos que ejecutan iOS 9.3+ y iPadOS 13.0+.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **Tipo de lista de aplicaciones**: cree una lista de aplicaciones para mostrar u ocultar. Puede mostrar u ocultar aplicaciones integradas y aplicaciones de línea de negocio. El sitio web de Apple tiene una lista de [aplicaciones de Apple integradas](https://support.apple.com/HT208094). Las opciones son:

  - **Aplicaciones ocultas**: Escriba una lista de las aplicaciones ocultas a los usuarios. Los usuarios no pueden ver ni abrir estas aplicaciones.
  
    Apple evita ocultar algunas aplicaciones nativas. Por ejemplo, no puede ocultar las aplicaciones **Configuración** o **Wallet** en el dispositivo. [Delete built-in Apple apps](https://support.apple.com/HT208094) (Eliminar aplicaciones integradas de Apple) muestra las aplicaciones que se pueden ocultar.
  
  - **Aplicaciones visibles**: Especifique una lista de las aplicaciones que los usuarios pueden ver e iniciar. No se puede ver ni iniciar ninguna otra aplicación.

- **Dirección URL de la aplicación**: escriba la dirección URL de la aplicación de la tienda que quiere mostrar u ocultar. Por ejemplo:

  - Para agregar la aplicación Carpetas de trabajo de Microsoft, escriba `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` o `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`. 

  - Para agregar la aplicación Microsoft Word, escriba `https://itunes.apple.com/de/app/microsoft-word/id586447913` o `https://apps.apple.com/de/app/microsoft-word/id586447913`.

  Para buscar la dirección URL de una aplicación, abra la tienda de aplicaciones de iTunes y busque la aplicación. Por ejemplo, busque `Microsoft Remote Desktop` o `Microsoft Word`. Seleccione la aplicación y copie la dirección URL.

  También puede usar iTunes para buscar la aplicación y luego usar la tarea **Copiar vínculo** para obtener la dirección URL de la aplicación.

- **Identificador de lote de aplicaciones**: escriba el [identificador del lote](bundle-ids-built-in-ios-apps.md) de aplicaciones de la aplicación que quiere. Puede mostrar u ocultar aplicaciones integradas y aplicaciones de línea de negocio. El sitio web de Apple tiene una lista de [aplicaciones de Apple integradas](https://support.apple.com/HT208094).
- **Nombre de la aplicación**: escriba el nombre de la aplicación que quiere. Puede mostrar u ocultar aplicaciones integradas y aplicaciones de línea de negocio. El sitio web de Apple tiene una lista de [aplicaciones de Apple integradas](https://support.apple.com/HT208094).
- **Publicador**: escriba el publicador de la aplicación que quiere.

Para agregar aplicaciones, puede:

- **Agregar**: seleccione para crear la lista de aplicaciones.
- **Importe** un archivo .csv con detalles sobre la aplicación, incluida la dirección URL. Use el formato `<app url>, <app name>, <app publisher>`. O bien, **Exportar** para crear una lista de las aplicaciones restringidas que ha agregado, en el mismo formato.

## <a name="wireless"></a>Inalámbrico

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivos, también en el caso de la inscripción automatizada (con supervisión)

Nota necesaria para la itinerancia de datos (sugerencia o nota importante para ayudar a aclarar la confusión del cliente): Este valor no se muestra en el perfil de administración del dispositivo de destino. Esto se debe a que esta configuración se trata como una acción de dispositivo remoto y cada vez que se cambia el estado de la itinerancia de datos en el dispositivo, el servicio Intune vuelve a bloquearla. Aunque no esté en el perfil de administración, funciona si aparece como correcto en las notificaciones de la consola de administración. 
- **Itinerancia de datos**: elija **Bloquear** para impedir la itinerancia de datos a través de la red de telefonía móvil. **No configurado** (valor predeterminado) permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.

  > [!IMPORTANT]
  > Esta configuración se trata como una acción de dispositivo remoto. Por lo tanto, no se muestra en el perfil de administración del dispositivo. Cada vez que cambia el estado de itinerancia de datos en el dispositivo, el servicio Intune bloquea **Itinerancia de datos**. En Intune, si el estado de las notificaciones muestra que todo es correcto, sepa que funciona, aunque la configuración no se muestre en el perfil de administración del dispositivo.

- **Captura de fondo global durante la itinerancia**: **Bloquear** evita el uso de la característica de captura de fondo global durante la itinerancia a través de la red de telefonía móvil. **No configurado** (valor predeterminado) permite que el dispositivo capture datos, como el correo electrónico, durante la itinerancia en una red de telefonía móvil.
- **Marcación por voz**: Elija **Bloquear** para evitar que los usuarios usen la característica de marcación por voz en el dispositivo. **No configurado** (valor predeterminado) permite la marcación por voz en el dispositivo.
- **Itinerancia de voz**: Elija **Bloquear** para evitar la itinerancia de datos a través de la red de telefonía móvil. **No configurado** (valor predeterminado) permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.
- **Punto de acceso personal**: **Bloquear** desactiva el punto de acceso personal en el dispositivo del usuario con la sincronización de cada dispositivo. Esta opción puede que no sea compatible con algunos operadores. **Sin configurar** (valor predeterminado) mantiene la configuración de punto de acceso personal como el valor predeterminado establecido por el usuario.

  > [!IMPORTANT]
  > Esta configuración se trata como una acción de dispositivo remoto. Por lo tanto, no se muestra en el perfil de administración del dispositivo. Cada vez que cambia el estado del punto de acceso personal en el dispositivo, el servicio Intune bloquea **Punto de acceso personal**. En Intune, si el estado de las notificaciones muestra que todo es correcto, significa que funciona, aunque la configuración no se muestre en el perfil de administración del dispositivo.

- **Reglas de uso de datos móviles (solo aplicaciones administradas)** : Defina los tipos de datos que las aplicaciones administradas pueden usar cuando están en redes de telefonía móvil. Las opciones son:
  - **Bloquear el uso de datos móviles**: Bloquee el uso de los datos móviles en **Todas las aplicaciones administradas** o **Elegir aplicaciones específicas**.
  - **Bloquear uso de datos móviles en itinerancia**: Bloquee el uso de los datos móviles en itinerancia en **Todas las aplicaciones administradas** o **Elegir aplicaciones específicas**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **Cambios en la configuración de uso de datos móviles de la aplicación**: Elija **Bloquear** para evitar los cambios en la configuración de uso de datos móviles de la aplicación. **No configurado** (valor predeterminado) permite que el usuario controle qué aplicaciones pueden usar datos móviles.
- **Cambios en la configuración del plan de red de telefonía móvil**: **Bloquear** evita que los usuarios cambien cualquier configuración en el plan de telefonía móvil. **Sin configurar** (valor predeterminado) permite que los usuarios realicen cambios.

  Esta característica se aplica a:  
  - iOS 11.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Modificación por el usuario del punto de acceso personal**: cuando se establece en **Bloquear**, el usuario no puede cambiar el valor del punto de acceso personal. **Sin configurar** (valor predeterminado) permite a los usuarios finales habilitar o deshabilitar su punto de acceso personal.

  Si bloquea esta configuración y también **Punto de acceso personal**, se desactiva el punto de acceso personal.

  Esta característica se aplica a:  
  - iOS 12.2 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Conexión a redes Wi-Fi solo con perfiles de configuración**: **Requerir** fuerza al dispositivo a usar solo las redes Wi-Fi configuradas mediante perfiles de configuración de Intune. **No configurado** (valor predeterminado) permite que el dispositivo use otras redes Wi-Fi.

  Si se establece en **Requerir**, asegúrese de que el dispositivo tiene un perfil de Wi-Fi. Si no asigna un perfil de Wi-Fi, este valor podría evitar que el dispositivo se conectara a Internet. Es decir, si este perfil de restricciones de dispositivos se asigna antes que un perfil de Wi-Fi, es posible que el dispositivo no pueda conectarse a Internet.
  
  Si no se puede conectar, anule la inscripción del dispositivo y vuelva a inscribirlo con un perfil de Wi-Fi. Luego establezca esta opción en **Requerir** en un perfil de restricciones de dispositivos y asigne el perfil al dispositivo.

- **Conexión Wi-Fi siempre activada**: cuando se establece en **Requerir**, la conexión Wi-Fi está activada en la aplicación Configuración. No se puede desactivar en Configuración ni en el centro de control, aun cuando el dispositivo esté en modo avión. **Sin configurar** (valor predeterminado) permite al usuario controlar la activación o desactivación de la conexión Wi-Fi.

  La configuración de esta opción no evita que los usuarios seleccionen una red Wi-Fi.

  Esta característica se aplica a:  
  - iOS 13.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

## <a name="connected-devices"></a>Dispositivos conectados

### <a name="settings-apply-to-all-enrollment-types"></a>Las opciones se aplican a: Todos los tipos de inscripción

- **Detección de muñeca para Apple Watch enlazados**: **Requerir** fuerza a los dispositivos Apple Watch emparejados a usar la detección de muñeca. Cuando se requiere, el dispositivo Apple Watch no mostrará notificaciones si no se lleva puesto. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivos, también en el caso de la inscripción automatizada (con supervisión)

- **Requerir contraseña de emparejamiento para solicitudes salientes de AirPlay**: **Requerir** exige una contraseña de emparejamiento cuando el usuario usa AirPlay para transmitir contenido a otros dispositivos de Apple. **No configurado** (valor predeterminado) permite que el usuario transmita contenido mediante AirPlay sin tener que escribir una contraseña.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **AirDrop**: **Bloquear** evita el uso de AirDrop en el dispositivo. **No configurado** (valor predeterminado) permite usar la característica AirDrop para intercambiar contenido con dispositivos cercanos.
- **Enlace con Apple Watch**: **Bloquear** evita el emparejamiento con Apple Watch. **No configurado** (valor predeterminado) permite el emparejamiento del dispositivo con Apple Watch.
- **Modificación de Bluetooth**: **Bloquear** evita que el usuario final cambie la configuración de Bluetooth en el dispositivo. **No configurado** (valor predeterminado) permite que el usuario cambie esta configuración.
- **Emparejamiento de host para controlar los dispositivos con los que se puede emparejar un dispositivo iOS/iPadOS**: **No configurado** (valor predeterminado) permite que el emparejamiento de host deje al administrador controlar con qué dispositivos se puede emparejar un dispositivo iOS/iPadOS. **Bloquear** impide el emparejamiento de host.
- **Bloquear AirPrint**: Elija **Bloquear** para evitar el uso de la característica AirPrint en el dispositivo. **No configurado** (valor predeterminado) permite que el usuario use AirPrint.
  - **Bloquear el almacenamiento de credenciales de AirPrint en Keychain**: **Bloquear** evita el uso del almacenamiento de Keychain para nombres de usuario y contraseñas en el dispositivo. **No configurado** (valor predeterminado) permite almacenar el nombre de usuario y la contraseña de AirPrint en la aplicación Keychain.
  - **Requerir un certificado de confianza TLS para AirPrint**: **Requerir** fuerza al dispositivo a usar certificados de confianza para la comunicación de impresión de TLS.
  - **Bloquear la detección de iBeacon de impresoras AirPrint**: **Bloquear** evita que balizas Bluetooth de AirPrint malintencionadas suplanten la identidad en el tráfico de red. **No configurado** (valor predeterminado) permite anunciar impresoras AirPrint en el dispositivo.
- **Bloquear la configuración de nuevos dispositivos cercanos**: **Bloquear** deshabilita el símbolo del sistema para configurar nuevos dispositivos cercanos. **Sin configurar** (valor predeterminado) permite solicitudes de los usuarios para conectarse a otros dispositivos Apple cercanos.

  Esta característica se aplica a:  
  - iOS 11.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Acceso a los archivos de la unidad USB**: los dispositivos pueden conectarse a una unidad USB y abrir los archivos que contiene. **Deshabilitar** evita el acceso del dispositivo a la unidad USB en la aplicación Files cuando hay un USB conectado al dispositivo. Al deshabilitar esta característica también se evita que los usuarios finales transfieran archivos a una unidad USB conectada a un dispositivo iPad. **Sin configurar** (valor predeterminado) permite el acceso a una unidad USB en la aplicación Files.

  Esta característica se aplica a:  
  - iOS 13.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

## <a name="keyboard-and-dictionary"></a>Teclado y diccionario

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **Búsqueda de definiciones de palabras**: **Bloquear** evita que el usuario resalte una palabra y luego busque su definición en el dispositivo. **No configurado** (valor predeterminado) permite el acceso a la característica de búsqueda de definiciones.
- **Teclados predictivos**: **No configurado** (valor predeterminado) permite usar teclados predictivos para sugerir las palabras que pueda querer el usuario. **Bloquear** impide esta característica.
- **Autocorrección**: **No configurado** (valor predeterminado) permite que el dispositivo corrija automáticamente las palabras mal escritas. **Bloquear** impide usar la autocorrección.
- **Revisión ortográfica de teclado**: **Sin configurar** (valor predeterminado) permite usar el corrector ortográfico en el dispositivo. **Bloquear** permite el corrector ortográfico.
- **Métodos abreviados de teclado**: **Sin configurar** (valor predeterminado) permite usar métodos abreviados de teclado en el dispositivo. **Bloquear** impide que el usuario use los métodos abreviados de teclado.
- **Dictado**: **Bloquear** evita que el usuario use la entrada de voz para escribir texto. **No configurado** (valor predeterminado) permite que el usuario use la entrada de dictado.
- **QuickPath**: **Sin configurar** (valor predeterminado) deja a los usuarios usar QuickPath, que permite una entrada continua en el teclado del dispositivo. Los usuarios pueden escribir al deslizar el dedo por las teclas para crear palabras. **Bloquear** evita que los usuarios usen QuickPath. 

  Esta característica se aplica a:  
  - iOS 13.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

## <a name="cloud-and-storage"></a>Nube y almacenamiento

### <a name="settings-apply-to-all-enrollment-types"></a>Las opciones se aplican a: Todos los tipos de inscripción

- **Copia de seguridad cifrada**: **Requerir** obliga a que las copias de seguridad del dispositivo se cifren.
- **Sincronización de aplicaciones administradas con la nube**: **No configurado** (valor predeterminado) permite que Intune administre las aplicaciones para sincronizar los datos con la cuenta de iCloud del usuario. **Bloquear** impide que estos datos se sincronicen con iCloud.
- **Bloquear la copia de seguridad de libros empresariales**: Elija **Bloquear** para evitar que los usuarios hagan copias de seguridad de libros empresariales. **No configurado** (valor predeterminado) permite que los usuarios hagan una copia de seguridad de estos libros.
- **Bloquear la sincronización de metadatos de libros empresariales (notas y eventos destacados)** : **Bloquear** evita la sincronización de notas y eventos destacados de libros empresariales. **Sin configurar** (valor predeterminado) permite la sincronización.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivos, también en el caso de la inscripción automatizada (con supervisión)

- **Sincronización de Photo Stream en iCloud**: **No configurado** (valor predeterminado) permite que los usuarios habiliten **My Photo Stream** en su dispositivo para sincronizar en iCloud y que las fotos estén disponibles en todos los dispositivos del usuario. **Bloquear** impide la sincronización de Photo Stream en iCloud. El bloqueo de esta característica puede provocar una pérdida de datos. 
- **Fototeca de iCloud**: Establezca en **Bloquear** para deshabilitar el uso de la Fototeca de iCloud para almacenar fotos y vídeos en la nube. Las fotos que no se hayan descargado de la Fototeca de iCloud en el dispositivo se quitarán del dispositivo. **No configurado** (valor predeterminado) permite usar la Fototeca de iCloud.
- **Fotos en streaming compartidas**: Elija **Bloquear** para deshabilitar **Fotos compartidas en iCloud** en el dispositivo. **No configurado** (valor predeterminado) permite las fotos compartidas.
- **Handoff**: **No configurado** (valor predeterminado) permite a los usuarios empezar a trabajar en un dispositivo iOS/iPadOS y, luego, seguir con el trabajo iniciado en otro dispositivo iOS/iPadOS. **Bloquear** impide esta entrega.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **Copia de seguridad en iCloud**: **No configurado** (valor predeterminado) permite que el usuario realice una copia de seguridad del dispositivo en iCloud. **Bloquear** impide que el usuario cree una copia de seguridad del dispositivo en iCloud.

  A partir de iOS/iPadOS 13.0, esta configuración requiere dispositivos supervisados.

- **Bloquear la sincronización de documentos en iCloud**: **No configurado** (valor predeterminado) permite la sincronización de clave-valor y documentos en el espacio de almacenamiento de iCloud. **Bloquear** impide que iCloud sincronice documentos y datos.

  A partir de iOS/iPadOS 13.0, esta configuración requiere dispositivos supervisados.

- **Bloquear la sincronización de Keychain en iCloud**: Elija **Bloquear** para deshabilitar la sincronización de las credenciales almacenadas en Keychain en iCloud. **No configurado** (valor predeterminado) permite que los usuarios sincronicen estas credenciales.

  A partir de iOS/iPadOS 13.0, esta configuración requiere dispositivos supervisados.

## <a name="autonomous-single-app-mode"></a>Modo de aplicación única autónoma

Use estos valores para configurar los dispositivos iOS/iPadOS de modo que ejecuten aplicaciones específicas en modo de aplicación única autónoma. Si se configura este modo y el usuario inicia una de las aplicaciones configuradas, el dispositivo se bloqueará para esa aplicación. La conmutación de tareas y aplicaciones se deshabilitará hasta que el usuario salga de la aplicación permitida.

Por ejemplo, en un entorno educativo o universitario, agregue una aplicación que permita que los usuarios realicen una prueba en el dispositivo. Otra opción es bloquear el dispositivo en la aplicación Portal de empresa hasta que el usuario final se autentique. Cuando el usuario complete las acciones de la aplicación o quite esta directiva, el dispositivo volverá a su estado normal.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **Nombre de la aplicación**: escriba el nombre de la aplicación que quiere.
- **Identificador de lote de aplicaciones**: escriba el [identificador del lote](bundle-ids-built-in-ios-apps.md) de la aplicación que quiere.
- **Agregar**: seleccione para crear la lista de aplicaciones.

También puede **importar** un archivo .csv con la lista de nombres de aplicaciones y sus identificadores de lote. O bien puede **Exportar** una lista existente que incluya las aplicaciones.

## <a name="kiosk"></a>Pantalla completa

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **Aplicación para ejecutar en modo de pantalla completa**: Elija el tipo de aplicaciones que quiere que se ejecuten en pantalla completa. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se aplica la configuración de pantalla completa. El dispositivo no se ejecuta en modo de pantalla completa.
  - **Aplicación de la Tienda**: escriba la dirección URL de una aplicación de la tienda de aplicaciones de iTunes.
  - **Aplicación administrada**: elija una aplicación que haya agregado a Intune.
  - **Aplicación integrada**: escriba el [identificador del lote](bundle-ids-built-in-ios-apps.md) de la aplicación integrada.

- **AssistiveTouch**: **Requerir** que la configuración de accesibilidad AssistiveTouch se establezca en el dispositivo. Esta característica ayuda a los usuarios con gestos en pantalla que podrían ser difíciles para ellos. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Invertir colores**: **Requerir** la configuración de accesibilidad Invertir colores para que los usuarios con discapacidades visuales puedan cambiar la pantalla. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Audio mono**: **Requerir** que la configuración de accesibilidad Audio mono esté establecida en el dispositivo. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Control de voz**: **Requerir** habilita el control de voz en el dispositivo y permite a los usuarios controlar por completo el sistema operativo mediante los comandos de Siri. **Sin configurar** deshabilita el control de voz en el dispositivo.

  Esta configuración solo es aplicable a:  
  - iOS 13.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes
  
  > [!TIP]
  > Si tiene aplicaciones de LOB disponibles para la organización y no están preparadas para el **Control de voz** en el día 0 cuando se publique iOS 13.0, se recomienda dejar este valor como **Sin configurar**.

- **VoiceOver**: **Requerir** que la configuración de accesibilidad VoiceOver esté establecida en el dispositivo para leer en voz alta el texto en pantalla. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Zoom**: **Requerir** que la configuración Zoom esté establecida en el dispositivo para que los usuarios usen un toque para acercar en la pantalla. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Bloqueo automático**: **Bloquear** impide el bloqueo automático del dispositivo. **No configurado** permite esta característica Administrador de contraseñas de Microsoft Edge.
- **Cambio de timbre**: **Bloquear** deshabilita el conmutador de timbre (silencio) en el dispositivo. **No configurado** permite esta característica Administrador de contraseñas de Microsoft Edge.
- **Rotación de pantalla**: **Bloquear** evita cambiar la orientación de la pantalla cuando el usuario gira el dispositivo. **No configurado** permite esta característica Administrador de contraseñas de Microsoft Edge.
- **Botón de suspensión de pantalla**: seleccione **Bloquear** para deshabilitar el botón de reactivación de suspensión de pantalla en el dispositivo. **No configurado** permite esta característica Administrador de contraseñas de Microsoft Edge.
- **Toque**: **Bloquear** deshabilita la pantalla táctil en el dispositivo. **No configurado** permite que el usuario use la pantalla táctil.
- **Botones de volumen**: **Bloquear** impide el uso de los botones de volumen en el dispositivo. **Sin configurar** permite los botones de volumen.
- **Control de AssistiveTouch**: **Permitir** permite que los usuarios usen la función AssistiveTouch. **No configurado** deshabilita esta característica.
- **Control Invertir colores**: **Permitir** invierte los cambios de color para que los usuarios puedan ajustar la función Invertir colores. **No configurado** deshabilita esta característica.
- **Leer el texto seleccionado**: **Permitir** que la configuración de accesibilidad Reproducir selección esté establecida en el dispositivo. Esta característica lee en voz alta el texto seleccionado por el usuario. **No configurado** deshabilita esta característica.
- **Modificación del control de voz**: **Permitir** deja a los usuarios cambiar el estado del control de voz en los dispositivos. **Sin configurar** evita que los usuarios cambien el estado del control de voz en sus dispositivos.

  Esta configuración solo es aplicable a:  
  - iOS 13.0 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

- **Control de VoiceOver**: **Permitir** cambios de VoiceOver para que los usuarios puedan actualizar la función VoiceOver, por ejemplo, la velocidad con que el texto en pantalla se lee en voz alta. **No configurado** impide los cambios en VoiceOver.
- **Control de zoom**: **Permitir** que el usuario haga cambios en el zoom. **No configurado** impide cambios en el zoom.

> [!NOTE]
> Antes de configurar un dispositivo iOS/iPadOS para el modo de pantalla completa, debe usar la herramienta Apple Configurator o el Programa de inscripción de dispositivos de Apple para poner el dispositivo en modo supervisado. Consulte la guía de Apple sobre cómo usar la herramienta Apple Configurator.
> Si la aplicación iOS/iPadOS que escriba se instala después de asignar el perfil, el dispositivo no entrará en el modo de pantalla completa hasta que se lo reinicie.

## <a name="domains"></a>Dominios

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivos, también en el caso de la inscripción automatizada (con supervisión)

- **Dominios de correo electrónico no marcados** > **URL de dominio de correo electrónico**: agregue una o más direcciones URL a la lista. Cuando los usuarios finales reciben un correo electrónico de un dominio distinto al especificado, el correo electrónico se marca como correo electrónico no de confianza en la aplicación Correo de iOS/iPadOS.

- **Dominios web administrados** > **URL de dominio web**: agregue una o varias URL a la lista. Los documentos que se descargan de los dominios que especifica se consideran administrados. Esta configuración solo se aplica a los documentos que se descargan con el explorador Safari.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada (supervisado)

- **Dominios de relleno automático de contraseña de Safari** > **URL de dominio**: agregue una o más direcciones URL a la lista. Los usuarios solo pueden guardar contraseñas web de las direcciones URL que aparecen en esta lista. Esta configuración solo se aplica al explorador Safari y a dispositivos en modo supervisado. Si no escribe ninguna dirección URL, se podrán guardar contraseñas de todos los sitios web.

  Esta configuración solo es aplicable a:  
  - iOS 9.3 y versiones más recientes
  - IPadOS 13.0 y versiones más recientes

## <a name="settings-that-require-supervised-mode"></a>Configuraciones que necesitan el modo supervisado

El modo supervisado de iOS/iPadOS solo se puede habilitar durante la configuración inicial del dispositivo a través del Programa de inscripción de dispositivos de Apple o con Apple Configurator. Una vez activado el modo supervisado, Intune puede configurar un dispositivo con la funcionalidad siguiente:

- Bloqueo de aplicaciones (modo de aplicación única) 
- Proxy HTTP global 
- Deshabilitación del bloqueo de activación 
- Modo de aplicación única autónoma 
- Filtro de contenido web 
- Establecer la pantalla de fondo y la pantalla de bloqueo 
- Inserción de aplicación silenciosa 
- VPN Always-On 
- Permitir la instalación de aplicaciones administradas de forma exclusiva 
- iBookstore 
- iMessages 
- Centro de juegos 
- AirDrop 
- AirPlay 
- Emparejamiento de host 
- Sincronización en la nube 
- Búsqueda en Spotlight 
- Handoff 
- Borrar dispositivo 
- Interfaz de usuario de restricciones 
- Instalación de perfiles de configuración por interfaz de usuario 
- Noticias 
- Métodos abreviados de teclado 
- Modificaciones de código de acceso 
- Cambios en los nombres de dispositivos 
- Descargas de aplicaciones automáticas 
- Cambios en la confianza de las aplicaciones empresariales 
- Apple Music 
- Mail Drop 
- Emparejamiento con Apple Watch 

> [!NOTE]
> Apple ha confirmado que ciertas opciones de configuración se trasladan al modo de solo supervisión en 2019. Le recomendamos que lo tenga en cuenta a la hora de usar estas opciones, en lugar de esperar a que Apple las migre al modo de solo supervisión:
>
> - Instalación de la aplicación por los usuarios finales
> - Eliminación de aplicaciones
> - FaceTime
> - Safari
> - iTunes
> - Contenido explícito
> - Documentos y datos de iCloud
> - Juego multijugador
> - Agregar amigos de Game Center
> - Siri

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](../device-profile-assign.md) y [supervise el estado](../device-profile-monitor.md).

También puede restringir la configuración y las características de los dispositivos en dispositivos [macOS](device-restrictions-macos.md).
