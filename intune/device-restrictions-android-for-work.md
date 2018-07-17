---
title: Restricciones de dispositivos para perfiles de trabajo Android en Microsoft Intune - Azure | Microsoft Docs
description: En dispositivos de perfil de trabajo Android puede restringir algunas opciones, como las opciones de copiar y pegar; mostrar las notificaciones, los permisos de las aplicaciones, el uso compartido de datos, la longitud de la contraseña, errores de inicio de sesión; usar la huella digital para desbloquear el dispositivo; reutilizar contraseñas y habilitar el uso compartido de los contactos de trabajo mediante Bluetooth.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 34c66aabe8c094b67805bcf0eeae38dbbbbff627
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905944"
---
# <a name="work-device-restriction-settings-in-intune"></a>Configuración de las restricciones de dispositivos de trabajo en Intune

En este artículo se enumeran las opciones de configuración de restricciones de dispositivos de Microsoft Intune que se pueden configurar para dispositivos de perfil de trabajo Android.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Configuración de perfil de trabajo

### <a name="general-settings"></a>Configuración general

- **Copy and paste between work and personal profiles** (Copiar y pegar entre el perfil de trabajo y el personal): controla la acción de copiar y pegar entre aplicaciones de trabajo y las personales. Elija **Bloquear** para habilitar el bloqueo. Elija **Sin configurar** para deshabilitar el bloqueo.
- **Data sharing between work and personal profiles** (Uso compartido de datos entre el perfil de trabajo y el personal): con esta opción puede controlar si las aplicaciones del perfil de trabajo y las aplicaciones del perfil personal pueden compartir datos. Este valor controla las acciones de uso compartido dentro de las aplicaciones (por ejemplo, la opción **Compartir...** de la aplicación del navegador Chrome) y no se aplica al comportamiento del Portapapeles de copiar y pegar. A diferencia de la [configuración de las directivas de protección de aplicaciones](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), la configuración de las restricciones del dispositivo se administra desde el portal de Intune y se usa la partición del perfil de trabajo Android para aislar las aplicaciones administradas. Elija de entre las siguientes opciones:
  - **Restricciones de uso compartido predeterminadas**: el comportamiento predeterminado del uso compartido del dispositivo, que varía según la versión de Android. De manera predeterminada, se permite el uso compartido desde el perfil personal hasta el perfil de trabajo. También de manera predeterminada, el uso compartido desde el perfil de trabajo hasta el perfil personal está bloqueado. Esta opción evita que se compartan datos desde el perfil de trabajo hasta el perfil personal. Google no proporciona ninguna manera de bloquear el uso compartido desde el perfil personal hasta el perfil de trabajo en dispositivos que ejecutan las versiones 6.0 y posteriores.
  - **Apps in work profile can handle sharing request from personal profile** (Las aplicaciones de un perfil de trabajo pueden controlar la solicitud de uso compartido desde un perfil personal): habilita la característica de Android integrada que permite el uso compartido desde el perfil personal al perfil de trabajo. Cuando esta opción está habilitada, una solicitud de uso compartido que se inicia en una aplicación del perfil personal se podrá compartir con las aplicaciones del perfil de trabajo. Esta opción es el comportamiento predeterminado de los dispositivos Android que ejecutan versiones anteriores a 6.0.
  - **Permitir el uso compartido a través de límites**: permite el uso compartido a través del límite del perfil de trabajo en ambas direcciones. Cuando selecciona esta configuración, las aplicaciones del perfil de trabajo pueden compartir datos con aplicaciones no administradas del perfil personal. Use esta configuración con precaución, ya que permite que las aplicaciones administradas en el perfil de trabajo se compartan con aplicaciones del lado sin administrar del dispositivo.

- **Work profile notifications while device locked** (Notificaciones del perfil de trabajo con el dispositivo bloqueado): controla si las aplicaciones del perfil de trabajo pueden mostrar datos en las notificaciones cuando el dispositivo está bloqueado.
- **Permisos de aplicación predeterminados**: establece la directiva de permisos predeterminada para todas las aplicaciones del perfil de trabajo. A partir de Android 6, se solicita al usuario que conceda determinados permisos que requieren las aplicaciones cuando se inician. Esta configuración de directiva permite decidir si se pedirá a los usuarios que concedan permisos para todas las aplicaciones del perfil de trabajo. Por ejemplo, suponga que asigna una aplicación al perfil de trabajo que requiere acceso mediante la ubicación. Normalmente, esa aplicación pide al usuario que apruebe o deniegue el acceso a la aplicación mediante la ubicación. Esta directiva le permite decidir si todos los permisos deben concederse automáticamente sin preguntar al usuario, denegarse automáticamente sin preguntar al usuario o dejar que el usuario final decida. Elija de entre las siguientes opciones:
  - **Valor predeterminado de dispositivo**
  - **Aviso**
  - **Concesión automática**
  - **Denegación automática**

    El estado de concesión de los permisos se puede definir aún más para aplicaciones específicas usando una directiva de configuración de aplicaciones (en **Aplicaciones móviles** > **Directivas de configuración de aplicaciones**).

- **Agregar y quitar cuentas**

   Impide que los usuarios finales agreguen o quiten cuentas manualmente en el perfil de trabajo.

   Por ejemplo, cuando implemente la aplicación de Gmail en un perfil de trabajo Android, podrá impedir que los usuarios finales agreguen o quiten cuentas en este perfil de trabajo.

- **Uso compartido de contactos a través de Bluetooth**: permite el acceso a los contactos de trabajo desde otro dispositivo (por ejemplo, un automóvil) que se empareja con Bluetooth. De forma predeterminada, esta opción no está configurada y los contactos de perfil de trabajo no se muestran. Seleccione **Habilitar** para permitir este uso compartido y para que se muestren los contactos de perfil de trabajo. Esta configuración se aplica a dispositivos de perfil de trabajo Android con la versión de SO Android 6.0 y versiones más recientes. Si se habilita, puede permitir que ciertos dispositivos Bluetooth almacenen en caché los contactos de trabajo en la primera conexión. Si se deshabilita esta directiva después de un emparejamiento o una sincronización inicial no puede eliminar los contactos de trabajo desde un dispositivo Bluetooth.

- **Captura de pantalla**: bloquea la captura de pantalla del dispositivo en el perfil de trabajo. Además evita que el contenido se muestre en los dispositivos de pantalla que no tengan una salida de vídeo segura.

- **Mostrar el identificador de llamada de contacto profesional en el perfil personal**: cuando se habilita (sin configurar), se muestran los detalles del autor de la llamada del contacto en el perfil personal. Cuando se bloquea, no se muestra el número del autor de la llamada del contacto en el perfil personal. Se aplica a las versiones del sistema operativo Android v6.0 y posteriores.

- **Cámara**: bloquea la cámara del dispositivo en el perfil de trabajo. La configuración no afecta a la cámara en el perfil personal.

### <a name="work-profile-password"></a>Contraseña del perfil de trabajo

- **Requerir contraseña del perfil de trabajo**: se aplica a Android 7.0 y versiones posteriores que tengan habilitado el perfil de trabajo. Defina una directiva de código de acceso que se aplique únicamente a las aplicaciones del perfil del trabajo. De forma predeterminada, el usuario final puede usar los dos PIN definidos por separado o bien puede optar por combinarlos en el más seguro de ellos.
- **Longitud mínima de la contraseña**: escriba el número mínimo de caracteres que debe contener la contraseña del usuario (de **4**-**16**)
- **Maximum minutes of inactivity until work profile locks** (Máximo de minutos de inactividad hasta que se bloquea el perfil de trabajo): seleccione la cantidad de tiempo antes de que se bloquee el perfil de trabajo. El usuario deberá especificar sus credenciales para volver a obtener acceso.
- **Number of sign-in failures before wiping device** (Número de errores de inicio de sesión antes de borrar el dispositivo): escriba la cantidad de veces que se puede escribir una contraseña incorrecta antes de que se borre el perfil de trabajo del dispositivo.
- **Expiración de la contraseña (días)**: escriba el número de días hasta que se deba cambiar la contraseña de un usuario final (de **1**-**255**).
- **Tipo de contraseña requerida**: seleccione el tipo de contraseña que se debe establecer en el dispositivo. Elija de entre las siguientes opciones:
  - **Valor predeterminado del dispositivo**
  - **Biométrico de seguridad baja**
  - **Requerido**
  - **Al menos numérica**
  - **Numérica compleja**: no se permiten números consecutivos ni repetidos, como "1111" o "1234"
  - **Al menos alfabética**
  - **Al menos alfanumérica**
  - **Al menos alfanumérica con símbolos**
- **Prevent reuse of previous passwords** (Impedir la reutilización de contraseñas anteriores): escriba la cantidad de contraseñas nuevas que se deben usar antes de que se pueda reutilizar una antigua (de **1**-**24**).
- **Desbloqueo con huella digital**: impide que un usuario final use el escáner de huella digital del dispositivo para desbloquearlo
- **Smart Lock y otros agentes de confianza**: controle la característica de Smart Lock en dispositivos compatibles. Esta funcionalidad del teléfono, conocida en ocasiones como "agente de confianza", le permite deshabilitar u omitir la contraseña del perfil de trabajo si el dispositivo está en una ubicación de confianza. Por ejemplo, cuando está conectado a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC. Use esta opción para impedir que los usuarios configuren Smart Lock.

## <a name="device-password"></a>Contraseña del dispositivo

- **Longitud mínima de la contraseña**: escriba el número mínimo de caracteres que debe contener la contraseña del usuario (de **4**-**14**)
- **Maximum minutes of inactivity until screen locks** (Máximo de minutos de inactividad hasta que se bloquea la pantalla): seleccione el tiempo antes de que un dispositivo inactivo se bloquee de forma automática.
- **Number of sign-in failures before wiping device** (Número de errores de inicio de sesión antes de borrar el dispositivo): escriba la cantidad de veces que se puede escribir una contraseña incorrecta antes de que se borren todos los datos del dispositivo
- **Expiración de la contraseña (días)**: escriba el número de días hasta que se deba cambiar la contraseña de un usuario final (de **1**-**255**)
- **Tipo de contraseña requerida**: seleccione el tipo de contraseña que se debe establecer en el dispositivo. Elija de entre las siguientes opciones:
  - **Valor predeterminado del dispositivo**
  - **Biométrico de seguridad baja**
  - **Requerido**
  - **Al menos numérica**
  - **Numérica compleja**: no se permiten números consecutivos ni repetidos, como "1111" o "1234"
  - **Al menos alfabética**
  - **Al menos alfanumérica**
  - **Al menos alfanumérica con símbolos**
- **Prevent reuse of previous passwords** (Impedir la reutilización de contraseñas anteriores): escriba la cantidad de contraseñas nuevas que se deben usar antes de que se pueda reutilizar una antigua (de **1**-**24**).
- **Desbloqueo con huella digital**: impide que un usuario final use el escáner de huella digital del dispositivo para desbloquearlo
- **Smart Lock y otros agentes de confianza**: controle la característica de Smart Lock en dispositivos compatibles. Esta funcionalidad del teléfono, conocida en ocasiones como "agente de confianza", le permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si el dispositivo está en una ubicación de confianza. Por ejemplo, cuando está conectado a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC. Use esta opción para impedir que los usuarios configuren Smart Lock.

## <a name="system-security"></a>Seguridad del sistema

- **Examen de amenazas en las aplicaciones**: exija que la opción **Verificar aplicaciones** esté activada para el perfil personal y el perfil de trabajo.

   > [!Note]
   > Esta configuración solo sirve para dispositivos Android O y posteriores.

## <a name="next-step"></a>Paso siguiente

Vea [Configuración de restricciones de dispositivo](device-restrictions-configure.md) para guardar y asignar el perfil a los usuarios y dispositivos.
