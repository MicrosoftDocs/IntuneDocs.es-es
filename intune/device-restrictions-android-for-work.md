---
title: Configuración de dispositivos de Android Enterprise en Microsoft Intune (Azure) | Microsoft Docs
description: En dispositivos Android Enterprise o Android for Work, restrinja opciones de configuración en el dispositivo, como copiar y pegar; mostrar notificaciones; permisos de aplicación; uso compartido de datos; longitud de contraseña; errores de inicio de sesión; usar huella digital para desbloquear; reutilizar contraseñas y habilitar el uso compartido de los contactos de trabajo mediante Bluetooth. Configure los dispositivos en modo de pantalla completa para ejecutar una o varias aplicaciones.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.openlocfilehash: c9e2e0df79625329310171c509327395989f3a7c
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032544"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune

En este artículo se enumeran y describen los diferentes valores de configuración que puede controlar en los dispositivos Android y Android Enterprise. Como parte de su solución de administración de dispositivos móviles (MDM), use estos valores de configuración para habilitar o deshabilitar características, ejecutar aplicaciones en modo de pantalla completa, controlar la seguridad, y mucho más.

## <a name="before-you-begin"></a>Antes de comenzar

[Cree un perfil de configuración de dispositivo](device-restrictions-configure.md).

## <a name="device-owner-only"></a>Solo el propietario del dispositivo

### <a name="general-settings"></a>Configuración general

- **Captura de pantalla**: elija **Bloquear** para impedir que se hagan capturas de pantalla en el dispositivo. Además evita que el contenido se muestre en los dispositivos de pantalla que no tengan una salida de vídeo segura. **No configurado** permite que el usuario capture el contenido de la pantalla como imagen.
- **Cámara**: elija **Bloquear** para impedir el acceso a la cámara del dispositivo. **No requerido** permite el acceso a la cámara del dispositivo.
- **Directiva de permisos predeterminada**: con esta opción se define la directiva de permisos predeterminada para las solicitudes de permisos en tiempo de ejecución. Los valores posibles incluyen:
  - **Valor predeterminado del dispositivo**: use la configuración predeterminada del dispositivo.
  - **Símbolo del sistema**: se solicita al usuario que apruebe el permiso.
  - **Concesión automática**: los permisos se conceden automáticamente.
  - **Denegación automática**: los permisos se deniegan automáticamente.
- **Cambios de fecha y hora**: elija **Bloquear** para evitar que los usuarios configuren manualmente la fecha y hora. **No configurado** permite que los usuarios configuren la fecha y hora del dispositivo.
- **Cambios de volumen**: elija **Bloquear** para impedir que los usuarios cambien el volumen del dispositivo. **No configurado** permite usar la configuración de volumen del dispositivo.
- **Restablecimiento de la configuración de fábrica**: elija **Bloquear** para impedir que los usuarios usen la opción de restablecimiento de fábrica en la configuración del dispositivo. **No configurado** permite que los usuarios utilice esta configuración en el dispositivo.
- **Arranque seguro**: elija **Bloquear** para impedir que los usuarios reinicien el dispositivo en modo seguro. **No configurado** permite que los usuarios reinicie el dispositivo en modo seguro.
- **Barra de estado**: elija **Bloquear** para impedir el acceso a la barra de estado, incluidas las notificaciones y las opciones de configuración rápida. **No configurado** permite que los usuarios accedan a la barra de estado.
- **Servicios de datos de itinerancia**: elija **Bloquear** para impedir la itinerancia de datos a través de la red de telefonía móvil. **No configurado** permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.
- **Cambios en la configuración de Wi-Fi**: elija **Bloquear** para impedir que los usuarios cambien la configuración de Wi-Fi creada por el propietario del dispositivo. Los usuarios pueden crear sus propias configuraciones de Wi-Fi. **No configurado** permite a los usuarios cambiar la configuración de Wi-Fi del dispositivo.
- **Configuración de punto de acceso Wi-Fi**: elija **Bloquear** para impedir que los usuarios creen o cambien las configuraciones de Wi-Fi. **No configurado** permite a los usuarios cambiar la configuración de Wi-Fi del dispositivo.
- **Configuración de Bluetooth**: elija **Bloquear** para impedir que los usuarios configuren Bluetooth en el dispositivo. **No configurado** permite usar Bluetooth en el dispositivo.
- **Uso compartido de contactos a través de Bluetooth**: elija **Bloquear** para impedir el acceso a los contactos del trabajo desde otro dispositivo, como un sistema de automóvil, cuando un dispositivo Android se empareja mediante Bluetooth. **No configurado** permite acceder a los contactos de trabajo en otro dispositivo Bluetooth emparejado con el dispositivo Android.
- **Tethering and access to hotspots** (Acceso a zonas y tethering): elija **Bloquear** para impedir tethering y acceso a zonas portátiles. **No configurado** permite tethering y acceso a zonas activas portátiles.
- **Almacenamiento USB**: elija **Permitir** para acceder al almacenamiento USB en el dispositivo. **No configurado** impide el acceso al almacenamiento USB.
- **USB file transfer** (Transferencia de archivos USB): elija **Bloquear** para impedir la transferencia de archivos a través de USB. **No configurado** permite la transferencia de archivos.
- **External media** (Medios externos): elija **Bloquear** para impedir usar o conectar cualquier medio externo en el dispositivo. **No configurado** permite los medios externos en el dispositivo.
- **Beam data using NFC** (Transferir datos mediante NFC): elija **Bloquear** para impedir el uso de la tecnología Transmisión de datos en proximidad (NFC) para transferir datos desde las aplicaciones. **No configurado** permite usar NFC para compartir datos entre los dispositivos.
- **Características de depuración**: elija **Permitir** para permitir que los usuarios usen las características de depuración en el dispositivo. **No configurado** impide que los usuarios utilicen las características de depuración en el dispositivo.
- **Ajuste del micrófono**: elija **Bloquear** para impedir que los usuarios silencien el micrófono y ajusten su volumen. **No configurado** permite que el usuario utilice y ajuste el volumen del micrófono en el dispositivo.
- **Correos electrónicos de protección frente al restablecimiento de fábrica**: elija **Direcciones de correo electrónico de la cuenta de Google**. Escriba las direcciones de correo electrónico del dispositivo que los administradores pueden desbloquear una vez que se eliminan los datos del dispositivo. Asegúrese de separar las direcciones de correo electrónico con punto y coma, como en `admin1@gmail.com;admin2@gmail.com`. Si no se especificó ningún correo electrónico, cualquier usuario puede desbloquear el dispositivo una vez que se restaura la configuración de fábrica.
- **Trampilla de escape de red**: elija **Habilitar** para permitir que los usuarios activen la característica de trampilla de escape de red. Si no se realiza una conexión de red cuando se inicia el dispositivo, la ruta de escape pide conectarse de manera temporal a una red y actualizar la directiva del dispositivo. Después de aplicar la directiva, la red temporal se olvida y el dispositivo sigue arrancando. Esta característica conecta dispositivos a una red si:
  - No hay ninguna red adecuada en la última directiva.
  - El dispositivo se inicia en una aplicación en modo de bloqueo de tareas.
  - El usuario no puede llegar a la configuración del dispositivo.

  **No configurado** impide que los usuarios activen la característica de ruta de escape de red.

- **Permitir la instalación desde orígenes desconocidos**: elija **Permitir** para que los usuarios puedan activar los **orígenes desconocidos**. Esta configuración permite la instalación de aplicaciones de orígenes desconocidos. **No configurado** impide que los usuarios activen los **orígenes desconocidos**.
- **Actualización del sistema**: elija una opción para definir de qué forma funciona el dispositivo a través de las actualizaciones inalámbricas:
  - **Valor predeterminado del dispositivo**: use la configuración predeterminada del dispositivo.
  - **Automática**: las actualizaciones se instalan automáticamente sin intervención del usuario. Si se configura esta directiva se instalarán inmediatamente las actualizaciones pendientes.
  - **Pospuesta**: las actualizaciones se posponen durante 30 días. Cuando termine el período de 30 días, Android le pedirá al usuario que instale la actualización. Es posible que los fabricantes de dispositivos o los transportistas impidan que se pospongan actualizaciones de seguridad importantes (es decir, que las declaren como exentas). Una actualización exenta muestra al usuario una notificación en el dispositivo. 
  - **Ventana de mantenimiento**: instala las actualizaciones automáticamente durante una ventana de mantenimiento diario configurada en Intune. La instalación se intenta diariamente durante 30 días y pueden producirse errores si los niveles de batería o espacio no son suficientes. Después del período de 30 días, Android le solicitará al usuario que realice la instalación. La ventana también se usa para instalar actualizaciones de aplicaciones de Google Play. Use esta opción para dispositivos dedicados, como pantallas completas, ya que se pueden actualizar las aplicaciones de primer plano de pantalla completa con una única aplicación.
- **App auto-updates** (Actualizaciones automáticas de las aplicaciones): elija el momento de instalar las actualizaciones automáticas. Las opciones son:
  - **No configurado**.
  - **Elección del usuario**
  - **Nunca**
  - **Solo Wi-Fi**
  - **Siempre**

### <a name="system-security-settings"></a>Configuración de seguridad del sistema

- **Examen de amenazas en las aplicaciones**: **Requerir** exige que la configuración **Verificar aplicaciones** esté habilitada para los perfiles personales y profesionales.

### <a name="kiosk-settings"></a>Configuración de quiosco

Puede configurar un dispositivo para ejecutar una o muchas aplicaciones. Cuando un dispositivo está en pantalla completa, solo están disponibles las aplicaciones que usted agregue.

**Pantalla completa**: elija si el dispositivo ejecutará una o varias aplicaciones.

- **Pantalla completa con una sola aplicación**: los usuarios solo pueden acceder a una aplicación. Cuando se inicia el dispositivo, solo se inicia la aplicación específica. los usuarios no pueden abrir nuevas aplicaciones ni modificar la aplicación en ejecución.

  **Pasos**
  1. Elija **Seleccionar una aplicación administrada** y seleccione la aplicación de Google Play administrada en la lista. 

      Si no aparece ninguna aplicación, [agregue algunas aplicaciones Android](apps-add-android-for-work.md) al dispositivo. No olvide [asignar la aplicación al grupo de dispositivos creado para los dispositivos con pantalla completa](apps-deploy.md).

  2. Elija **Aceptar** > **Aceptar** para agregar la aplicación.

- **Pantalla completa con varias operaciones**: los usuarios pueden acceder a un conjunto limitado de aplicaciones en el dispositivo. Cuando se inicia el dispositivo, solo se inician las aplicaciones que agrega. También puede agregar algunos vínculos web que los usuarios pueden abrir. Al aplicar la directiva, los usuarios ven los iconos de las aplicaciones permitidas en la pantalla principal.

  > [IMPORTANTE] En los dispositivos con pantalla completa con varias aplicaciones, la [aplicación Managed Home Screen](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) de Google Play **debe estar**:
  >   - [Agregada como aplicación cliente](apps-add-android-for-work.md) en Intune
  >   - [Asignada al grupo de dispositivos](apps-deploy.md) creado para los dispositivos con pantalla completa
  > 
  > No es necesario que la aplicación **Managed Home Screen** esté en el perfil de configuración, pero sí se debe agregar como aplicación cliente. Cuando la aplicación **Managed Home Screen** se agrega como aplicación cliente, cualquier otra aplicación que se agregue en el perfil de configuración aparece como icono en la aplicación **Managed Home Screen**. 

  - Elija **Agregar** y seleccione las aplicaciones de la lista.

    Si la aplicación **Managed Home Screen** no aparece en la lista, [agréguela desde Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). No olvide [asignar la aplicación al grupo de dispositivos creado para los dispositivos con pantalla completa](apps-deploy.md).

    También puede agregar al dispositivo otras [aplicaciones Android](apps-add-android-for-work.md) y [aplicaciones web](web-app.md) creadas por la organización. No olvide [asignar la aplicación al grupo de dispositivos creado para los dispositivos con pantalla completa](apps-deploy.md).

  - **Botón de inicio virtual**: elija **Habilitar** para mostrar un botón de inicio en el dispositivo con pantalla completa. Cuando se selecciona, devuelve al usuario a la pantalla principal del dispositivo para que los usuarios puedan cambiar de manera sencilla entre las aplicaciones. En algunos dispositivos Android, es posible que los usuarios deban deslizarse hacia arriba de la pantalla para ver el botón de inicio. **Deshabilitar** no muestra un botón de inicio, por lo que los usuarios deben utilizar el botón de retroceso para cambiar entre las aplicaciones.
  - **Salir del modo de pantalla completa**: elija **Habilitar** para permitir que los administradores pausen temporalmente el modo de pantalla completa para actualizar el dispositivo. Para usar esta característica, el administrador debe hacer lo siguiente: 
  
    1. Seleccionar el botón de retroceso hasta que aparezca el botón "Exit Kiosk" (Salir de pantalla completa). 
    2. Seleccionar el botón y escriba el PIN **Leave kiosk mode code** (Código para salir de pantalla completa).
    3. Al terminar de hacer cambios, seleccionar la aplicación **Managed Home Screen**. Este paso vuelve a bloquear el dispositivo para pantalla completa con varias aplicaciones. 
    
    **Deshabilitar** no permite pausar la pantalla completa. Si el administrador sigue seleccionando el botón de retroceso y selecciona el botón "Exit Kiosk" (Salir de pantalla completa), aparece un mensaje que indica que se requiere un código de acceso.
    
    - **Código para salir del modo de pantalla completa**: escriba un PIN numérico que tenga entre 4 y 6 dígitos. El administrador usa este PIN para pausar de manera temporal la pantalla completa.
 
  - **Establecer fondo personalizado de la dirección URL**: escriba una dirección URL para personalizar la pantalla de fondo del dispositivo con pantalla completa.

### <a name="device-password-settings"></a>Configuración de la contraseña del dispositivo

- **Bloqueo del teclado**: elija **Deshabilitar** para impedir que los usuarios usen la característica de bloqueo del teclado en el dispositivo. **No configurado** permite que el usuario utilice las características Keyguard.
- **Tipo de contraseña requerida**: defina el tipo de contraseña necesaria para el dispositivo. Las opciones son:
  - **Al menos numérica**
  - **Numérica compleja**: no se permiten números repetidos ni consecutivos, como "1111" o "1234".
  - **Al menos alfabética**
  - **Al menos alfanumérica**
  - **Al menos alfanumérica con símbolos**
- **Longitud mínima de la contraseña**: escriba la longitud mínima de contraseña que un usuario debe escribir (entre 4 y 16 caracteres).
- **Número de errores de inicio de sesión antes de borrar el dispositivo**: escriba el número de errores de inicio de sesión que se permiten antes de que se borre el dispositivo (entre 1 y 11).

### <a name="power-settings"></a>Configuración de energía

- **Tiempo antes de que se bloquee la pantalla**: establece la cantidad de tiempo de inactividad requerido antes de que el dispositivo se bloquee.
- **Pantalla activada mientras el dispositivo está conectado**: elija qué fuentes de alimentación hacen que la pantalla del dispositivo permanezca encendida cuando está conectado a la corriente alterna.

### <a name="users-and-accounts-settings"></a>Configuración de cuentas y usuarios

- **Agregar nuevos usuarios**: elija **Bloquear** para impedir que los usuarios agreguen nuevos usuarios. Cada usuario tiene un espacio personal en el dispositivo para pantallas principales, cuentas, aplicaciones y configuraciones personalizadas. **No configurado** permite que los usuarios agreguen a otros usuarios al dispositivo.
- **Eliminación de usuario**: elija **Bloquear** para impedir que los usuarios quiten usuarios. **No configurado** permite que los usuarios quiten a otros usuarios del dispositivos.
- **Cambios de la cuenta**: elija **Bloquear** para impedir que los usuarios modifiquen las cuentas. **No configurado** permite que los usuarios actualicen las cuentas de usuario del dispositivo.

## <a name="work-profile-only"></a>Solo perfil de trabajo 

### <a name="work-profile-settings"></a>Configuración de perfil de trabajo

#### <a name="general"></a>General

- **Copiar y pegar entre perfiles personales y de trabajo**: elija **Bloquear** para impedir copiar y pegar entre aplicaciones personales y de trabajo. **No configurado** permite que los usuarios compartan datos mediante copiar y pegar con aplicaciones en el perfil personal. 
- **Uso compartido de datos entre el perfil profesional y el personal**: elija si las aplicaciones del perfil de trabajo pueden compartirse con aplicaciones del perfil personal. Por ejemplo, puede controlar las acciones de uso compartido dentro de las aplicaciones, como la opción **Compartir…** en la aplicación del explorador Chrome. Esta configuración no se aplica al comportamiento del Portapapeles de copiar y pegar. Las opciones de uso compartido son:
  - **Restricciones de uso compartido predeterminadas**: el comportamiento predeterminado del uso compartido del dispositivo, que varía según la versión de Android. De manera predeterminada, se permite el uso compartido desde el perfil personal hasta el perfil de trabajo. También de manera predeterminada, el uso compartido desde el perfil de trabajo hasta el perfil personal está bloqueado. Esta opción evita que se compartan datos desde el perfil de trabajo hasta el perfil personal. En dispositivos que ejecutan versiones 6.0 y posteriores, Google no bloquea el uso compartido desde el perfil personal hacia el perfil de trabajo.
  - **Las aplicaciones del perfil profesional pueden controlar una solicitud de uso compartido del perfil personal**: habilita la característica de Android integrada que permite el uso compartido del perfil personal al perfil de trabajo. Cuando esta opción está habilitada, una solicitud de uso compartido que se inicia en una aplicación del perfil personal se podrá compartir con las aplicaciones del perfil de trabajo. Esta opción es el comportamiento predeterminado de los dispositivos Android que ejecutan versiones anteriores a 6.0.
  - **Permitir el uso compartido a través de límites**: permite el uso compartido a través del límite del perfil de trabajo en ambas direcciones. Cuando selecciona esta configuración, las aplicaciones del perfil de trabajo pueden compartir datos con aplicaciones no administradas del perfil personal. Esta configuración permite administrar aplicaciones en el perfil de trabajo para compartirlas con aplicaciones del lado sin administrar del dispositivo. Por lo tanto, use esta configuración con precaución.

- **Notificaciones del perfil profesional con dispositivo bloqueado**: controla si las aplicaciones del perfil de trabajo pueden mostrar datos en las notificaciones cuando el dispositivo está bloqueado. **Bloquear** no muestra los datos. **No configurado** muestra los datos.
- **Permisos de aplicación predeterminados**: Establece la directiva de permisos predeterminada para todas las aplicaciones del perfil de trabajo. A partir de Android 6, se solicita al usuario que conceda determinados permisos que requieren las aplicaciones cuando se inician. Esta configuración de directiva permite decidir si se pedirá a los usuarios que concedan permisos para todas las aplicaciones del perfil de trabajo. Por ejemplo, suponga que asigna una aplicación al perfil de trabajo que requiere acceso mediante la ubicación. Normalmente, esa aplicación pide al usuario que apruebe o deniegue el acceso a la aplicación mediante la ubicación. Use esta directiva para conceder permisos y denegar permisos automáticamente sin preguntar al usuario o dejar que el usuario final decida. Elija de entre las siguientes opciones:
  - **Valor predeterminado de dispositivo**
  - **Aviso**
  - **Concesión automática**
  - **Denegación automática**

  También puede usar una directiva de configuración de aplicaciones para conceder permisos para aplicaciones individuales (**Aplicaciones cliente** > **Directivas de configuración de aplicaciones**).

- **Agregar y quitar cuentas**: elija **Bloquear** para impedir que los usuarios finales agreguen o quiten manualmente cuentas del perfil de trabajo. Por ejemplo, cuando implemente la aplicación de Gmail en un perfil de trabajo Android, podrá impedir que los usuarios finales agreguen o quiten cuentas en este perfil de trabajo. **No configurado** permite agregar cuentas en el perfil de trabajo.  

- **Uso compartido de contactos a través de Bluetooth**: permite el acceso a los contactos de trabajo desde otro dispositivo (por ejemplo, un automóvil) que está emparejado con Bluetooth. De forma predeterminada, esta opción no está configurada y los contactos de perfil de trabajo no se muestran. Seleccione **Habilitar** para permitir este uso compartido y para que se muestren los contactos de perfil de trabajo. Esta configuración se aplica a dispositivos de perfil de trabajo Android con la versión de SO Android 6.0 y versiones más recientes. Si se habilita, puede permitir que ciertos dispositivos Bluetooth almacenen en caché los contactos de trabajo en la primera conexión. Si se deshabilita esta directiva después de un emparejamiento o una sincronización inicial no puede eliminar los contactos de trabajo desde un dispositivo Bluetooth.

- **Captura de pantalla**: elija **Bloquear** para impedir capturas de pantalla en el dispositivo en el perfil de trabajo. Además evita que el contenido se muestre en los dispositivos de pantalla que no tengan una salida de vídeo segura. **No configurado** permite obtener capturas de pantalla.

- **Mostrar el identificador de llamada de contacto profesional en el perfil personal**: cuando se habilita (**sin configurar**), se muestran los detalles del autor de la llamada del contacto en el perfil personal. Cuando se establece en **Bloquear**, no se muestra el número del autor de la llamada del contacto en el perfil personal. Se aplica a las versiones del sistema operativo Android v6.0 y posteriores.

- **Buscar contactos profesionales del perfil personal**: elija **Bloquear** para impedir que los usuarios busquen contactos de trabajo en las aplicaciones del perfil personal. **No requerido** permite buscar contactos de trabajo en el perfil personal.

- **Cámara**: elija **Bloquear** para impedir el acceso a la cámara del dispositivo en el perfil de trabajo. La configuración no afecta a la cámara en el perfil personal. **No requerido** permite el acceso a la cámara en el perfil de trabajo.

#### <a name="work-profile-password"></a>Contraseña del perfil de trabajo

- **Requerir contraseña del perfil de trabajo**: se aplica a Android 7.0 y versiones posteriores con el perfil de trabajo habilitado. Elija **Requerir** para escribir una directiva de código de acceso que se aplique únicamente a las aplicaciones del perfil de trabajo. De forma predeterminada, el usuario final puede usar los dos PIN definidos por separado o bien puede optar por combinarlos en el más seguro de ellos. **No configurado** permite que el usuario use aplicaciones de trabajo, sin escribir ninguna contraseña.
- **Longitud mínima de la contraseña**: escriba el número mínimo de caracteres que debe tener la contraseña del usuario (**4**-**16**).
- **Cantidad máxima de minutos de inactividad hasta que el perfil de trabajo se bloquea**: seleccione la cantidad de tiempo antes de que se bloquee el perfil de trabajo. El usuario deberá especificar sus credenciales para volver a obtener acceso.
- **Número de errores de inicio de sesión antes de borrar el dispositivo**: especifique el número de veces que se puede escribir una contraseña incorrecta antes de que el perfil de trabajo se borre del dispositivo.
- **Expiración de la contraseña (días)**: escriba el número de días hasta que se deba cambiar la contraseña de un usuario final (**1**-**255**).
- **Tipo de contraseña requerida**: seleccione el tipo de contraseña que se debe establecer en el dispositivo. Elija de entre las siguientes opciones:
  - **Valor predeterminado del dispositivo**
  - **Biométrico de seguridad baja**
  - **Requerido**
  - **Al menos numérica**
  - **Numérica compleja**: no se permiten números consecutivos ni repetidos, como "1111" o "1234".
  - **Al menos alfabética**
  - **Al menos alfanumérica**
  - **Al menos alfanumérica con símbolos**
- **Impedir la reutilización de contraseñas anteriores**: escriba la cantidad de contraseñas nuevas que se deben usar antes de que se pueda reutilizar una antigua (**1**-**24**).
- **Desbloqueo con huella digital**: elija **Bloquear** para impedir que los usuarios finales usen el escáner de huella digital del dispositivo para desbloquearlo. **No configurado** permite que los usuarios desbloqueen los dispositivos con una huella digital en el perfil de trabajo.
- **Smart Lock y otros agentes de confianza**: elija **Bloquear** para impedir que Smart Lock u otros agentes de confianza ajusten la configuración de la pantalla de bloqueo en dispositivos compatibles. Esta característica, conocida a veces como agente de confianza, permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si el dispositivo está en una ubicación de confianza. Por ejemplo, se puede omitir la contraseña de perfil de trabajo cuando el dispositivo está conectado a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC. Use esta opción para impedir que los usuarios configuren Smart Lock.

### <a name="device-password"></a>Contraseña del dispositivo

Esta configuración de contraseña se aplica a los perfiles personales de los dispositivos que usan un perfil de trabajo.

- **Longitud mínima de la contraseña**: escriba el número mínimo de caracteres que debe tener la contraseña del usuario (**4**-**14**).
- **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: seleccione la cantidad de tiempo antes de que un dispositivo inactivo se bloquee automáticamente.
- **Número de errores de inicio de sesión antes de borrar el dispositivo**: especifica el número de veces que se puede escribir una contraseña incorrecta antes de que todos los datos se borren del dispositivo.
- **Expiración de la contraseña (días)**: escriba el número de días hasta que se deba cambiar la contraseña de un usuario final (**1**-**255**).
- **Tipo de contraseña requerida**: seleccione el tipo de contraseña que se debe establecer en el dispositivo. Elija de entre las siguientes opciones:
  - **Valor predeterminado del dispositivo**
  - **Biométrico de seguridad baja**
  - **Requerido**
  - **Al menos numérica**
  - **Numérica compleja**: no se permiten números consecutivos ni repetidos, como "1111" o "1234".
  - **Al menos alfabética**
  - **Al menos alfanumérica**
  - **Al menos alfanumérica con símbolos**
- **Impedir la reutilización de contraseñas anteriores**: escriba la cantidad de contraseñas nuevas que se deben usar antes de que se pueda reutilizar una antigua (**1**-**24**).
- **Desbloqueo con huella digital**: elija **Bloquear** para impedir que el usuario final use el escáner de huella digital del dispositivo para desbloquearlo. **No configurado** permite que el usuario desbloquee el dispositivo con la huella digital.
- **Smart Lock y otros agentes de confianza**: elija **Bloquear** para impedir que Smart Lock u otros agentes de confianza ajusten la configuración de la pantalla de bloqueo en dispositivos compatibles. Esta característica, conocida a veces como agente de confianza, permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si el dispositivo está en una ubicación de confianza. Por ejemplo, se puede omitir la contraseña de perfil de trabajo cuando el dispositivo está conectado a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC. Use esta opción para impedir que los usuarios configuren Smart Lock.

### <a name="system-security"></a>Seguridad del sistema

- **Examen de amenazas en las aplicaciones**: **Requerir** exige que la configuración **Verificar aplicaciones** esté habilitada para los perfiles personales y profesionales.

   > [!Note]
   > Esta configuración solo sirve para dispositivos Android O y posteriores.

### <a name="connectivity"></a>Conectividad

- **VPN siempre activa**: elija **Habilitar** para establecer que un cliente VPN se conecte automáticamente y vuelva a conectarse a la VPN. Las conexiones VPN siempre activas permanecen conectadas o se vuelven a conectar inmediatamente cuando el usuario desbloquea su dispositivo, se reinicia el dispositivo o cambia la red inalámbrica. 

  Elija **No configurado** para deshabilitar la VPN siempre activa para todos los clientes VPN.

  > [!IMPORTANT]
  > Asegúrese de implementar una sola directiva de VPN siempre activa en un único dispositivo. No se admite la implementación de varias directivas de VPN siempre activa en un único dispositivo.

- **Cliente VPN**: elija un cliente VPN que admita Always On. Las opciones son:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Personalizada
    - **Id. de paquete**: escriba el identificador de paquete de la aplicación en Google Play Store. Por ejemplo, si la dirección URL de la aplicación en Play Store es `https://play.google.com/store/details?id=com.contosovpn.android.prod`, el identificador del paquete es `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  >  - El cliente VPN que elija debe instalarse en el dispositivo y debe admitir VPN por aplicación en los perfiles de trabajo. De lo contrario, se producirá un error. 
  >  - Necesita aprobar la aplicación de cliente VPN en **Google Play Store administrado**, sincronizar la aplicación en Intune e implementar la aplicación en el dispositivo. Una vez hecho esto, la aplicación queda instalada en el perfil de trabajo del usuario.
  >  - Existen problemas conocidos al usar VPN por aplicación con F5 Access para Android 3.0.4. Para más información, consulte las [notas de la versión de F5 Access para Android 3.0.4](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android).

- **Modo de bloqueo**: use **Habilitar** para forzar que todo el tráfico de red use el túnel VPN. Si no se establece una conexión a la VPN, el dispositivo no tendrá acceso a la red.

  Elija **No configurado** para permitir que el tráfico fluya a través del túnel VPN o a través de la red móvil.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede crear perfiles de pantalla completa para dispositivos [Android](device-restrictions-android.md#kiosk) y [Windows 10](kiosk-settings.md).
