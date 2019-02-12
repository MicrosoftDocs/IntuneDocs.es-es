---
title: Solucionar problemas de perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Problemas comunes con perfiles de dispositivo, como los cambios de perfil que no se aplican a determinados usuarios o dispositivos, cuánto tiempo tarda una directiva nueva en enviarse a los dispositivos, qué configuración se aplica cuando hay varias directivas, qué ocurre cuando se elimina o quita un perfil y más con Microsoft InTune en Azure Portal
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 1/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 528e26ddca1b3327fb0afa2f5cff6f2dbdca1660
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55846492"
---
# <a name="common-issues-and-resolutions-with-device-profiles-in-microsoft-intune"></a>Problemas comunes y resoluciones con perfiles de dispositivo en Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Solucione problemas comunes al usar perfiles de dispositivo de Intune.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>¿Por qué un usuario no obtiene un perfil nuevo cuando cambia una contraseña o una frase de contraseña en un perfil de Wi-Fi existente? 
Después de crear un perfil de Wi-Fi corporativo, implementar el perfil en un grupo, cambiar la contraseña y guardar el perfil, cuando este cambia, puede que algunos usuarios no obtengan el nuevo perfil.

Para mitigar este problema, configure una Wi-Fi de invitado. Si se produce un error en la Wi-Fi corporativa, los usuarios pueden conectarse a la Wi-Fi de invitado. Debe habilitar todas las opciones de configuración de conexión automáticamente. Implemente el perfil de Wi-Fi de invitado para todos los usuarios.

Algunas recomendaciones adicionales:  

- Como la red Wi-Fi a la que se está conectando usa una contraseña o frase de contraseña, asegúrese de que puede conectarse directamente al enrutador Wi-Fi. Esto lo puede comprobar con un dispositivo iOS.
- Después de conectarse correctamente al punto de conexión Wi-Fi (enrutador Wi-Fi), anote el SSID y las credenciales que se han usado (este valor es la contraseña o frase de contraseña).
- Escriba el SSID y la credencial (contraseña o frase de contraseña) en el campo Clave precompartida. 
- Realice la implementación en un grupo de prueba que tenga un número de usuarios limitado, preferiblemente solo del equipo de TI. 
- Sincronice el dispositivo iOS con Intune. Inscríbalo si aún no lo ha hecho. 
- Vuelva a probar la conexión al mismo punto de conexión Wi-Fi (mencionado en el primer paso).
- Realice la implementación en grupos más grandes y, finalmente, en todos los usuarios relevantes de la organización. 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>¿Cuánto tiempo tardan los dispositivos móviles en obtener directivas o aplicaciones una vez asignadas?
Cuando se asigna una directiva o aplicación, Intune empieza inmediatamente a notificar al dispositivo que se conecte con el servicio de Intune. Esta notificación suele tardar menos de cinco minutos.

Si un dispositivo no se conecta para recibir la directiva una vez enviada la primera notificación, Intune hace tres intentos más. Si el dispositivo está sin conexión (por ejemplo, está apagado o no está conectado a una red), puede que no reciba las notificaciones. En ese caso, el dispositivo obtiene la directiva en la próxima conexión programada con el servicio Intune, como se indica a continuación:

- iOS y macOS: cada seis horas.
- Android: cada ocho horas.
- Windows Phone: cada ocho horas.
- Equipos Windows 8.1 y Windows 10 inscritos como dispositivos: cada ocho horas.

Si el dispositivo se ha inscrito recientemente, la frecuencia de conexión es más frecuente, como se indica a continuación:

- iOS y macOS: cada 15 minutos durante seis horas y, después, cada seis horas.
- Android: cada tres minutos durante 15 minutos, cada 15 minutos durante dos horas y, después, cada ocho horas.
- Windows Phone: cada cinco minutos durante 15 minutos, cada 15 minutos durante dos horas y, después, cada ocho horas.
- Equipos Windows inscritos como dispositivos: cada tres minutos durante 30 minutos y, después, cada ocho horas.

Para buscar la directiva inmediatamente en cualquier momento, los usuarios pueden abrir la aplicación del Portal de empresa y sincronizar el dispositivo.

En los dispositivos sin afinidad de usuario, la frecuencia de sincronización inmediatamente después de la inscripción puede variar de horas a un día o más. Intune envía solicitudes a diferentes intervalos para que un dispositivo se conecte con el servicio. En cambio, la conexión depende del dispositivo. Después de la inscripción inicial, en función del tipo de inscripción de dispositivos y las directivas y perfiles asignados a un dispositivo, no se puede predecir el tiempo que tarda un dispositivo en completar el registro. Aun así, una vez que el dispositivo esté inscrito y se hayan aplicado todas las directivas iniciales, el dispositivo debería comprobar si hay nuevas directivas aproximadamente cada seis horas.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>¿Qué acciones provocan que Intune envíe inmediatamente una notificación a un dispositivo?
Los dispositivos se conectan con Intune cuando reciben una notificación que se lo indica o durante la conexión programada periódicamente. Cuando el destino es un dispositivo o usuario con una acción (por ejemplo, borrado, bloqueo, restablecimiento de código de acceso, asignación de aplicaciones, asignación de perfiles o asignación de directivas), Intune notifica inmediatamente al dispositivo que se conecte al servicio de Intune para recibir estas actualizaciones.

Otros cambios, como la revisión de la información de contacto del Portal de empresa, no provocan una notificación inmediata a los dispositivos.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Si varias directivas se asignan al mismo usuario o dispositivo, ¿cómo puedo saber qué configuración se aplica?
Si dos o más directivas se asignan al mismo usuario o dispositivo, la configuración que se aplica se produce a nivel individual del valor:

- La configuración de directivas de cumplimiento siempre tiene prioridad respecto a la configuración de directivas de configuración

- Si se evalúa una directiva de cumplimiento con el mismo valor en otra directiva de cumplimiento, se aplica el valor de directiva de cumplimiento más restrictivo.

- Si un valor de directiva de configuración entra en conflicto con un valor de otra directiva de configuración, este conflicto se muestra en Azure Portal. En este escenario, debe resolver estos conflictos de forma manual.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>¿Qué sucede cuando las directivas de protección de aplicaciones entran en conflicto entre sí? ¿Cuál se aplica a la aplicación?
Los valores en conflicto son la configuración más restrictiva disponible en una directiva de protección de aplicaciones, excepto para los campos de entrada de números (como intentos de PIN antes del restablecimiento). Los campos de entrada de números se definen con los mismos valores que si crease una directiva de MAM en la consola con la opción de configuración recomendada.

Se producen conflictos cuando dos configuraciones de perfil son iguales. Por ejemplo, si configura dos directivas MAM que son idénticas, salvo por la configuración de copiar y pegar. En este escenario, la configuración de copiar y pegar se define con el valor más restrictivo, pero el resto de parámetros se aplican según la configuración.

Si un perfil se asigna a la aplicación y se aplica, y después se asigna un segundo, el primero tiene precedencia y se aplicará, mientras que el segundo presentará un conflicto. Si se aplican al mismo tiempo, lo que significa que no hay ningún perfil anterior, ambos están en conflicto. Cualquier configuración en conflicto se establece en los valores más restrictivos.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>¿Qué sucede cuando hay un conflicto de directivas personalizadas de iOS?
Intune no evalúa la carga de archivos de configuración de Apple ni perfiles personalizados de identificador uniforme de recursos de Open Mobile Alliance (OMA-URI). Sencillamente, se usa como mecanismo de entrega.

Al asignar un perfil personalizado, asegúrese de que los valores configurados no entran en conflicto con las directivas de cumplimiento, de configuración o con directivas personalizadas de otro tipo. Si un perfil personalizado y su configuración entran en conflicto, la configuración se aplicará de forma aleatoria.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>¿Qué ocurre cuando se elimina un perfil o deja de ser aplicable?
Al eliminar un perfil o quitar un dispositivo de un grupo que tiene el perfil, se quitan el perfil y la configuración del dispositivo según las siguientes listas:

- Perfiles de correo electrónico, certificado, VPN y Wi-Fi: estos perfiles se quitan de todos los dispositivos inscritos admitidos.
- Todos los demás tipos de perfiles:  

  - **Dispositivos Android y Windows**: la configuración no se quita del dispositivo.
  - **Dispositivos Windows Phone 8.1**: Se han eliminado las siguientes configuraciones:  
  
    - Requerir una contraseña para desbloquear dispositivos móviles
    - Permitir contraseñas sencillas
    - Longitud mínima de la contraseña
    - Tipo de contraseña obligatoria
    - Expiración de contraseña (días)
    - Recordar el historial de contraseñas
    - Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo
    - Minutos de inactividad antes de que se pida la contraseña
    - Tipo de contraseña requerida: número mínimo de conjuntos de caracteres
    - Permitir cámara
    - Requerir cifrado en dispositivo móvil
    - Permitir almacenamiento extraíble
    - Permitir explorador web
    - Permitir almacén de aplicaciones
    - Permitir captura de pantalla
    - Permitir geolocalización
    - Permitir cuenta de Microsoft
    - Permitir copiar y pegar
    - Permitir Wi-Fi Tethering
    - Permitir la conexión automática a zonas Wi-Fi gratuitas
    - Permitir informar de zonas Wi-Fi
    - Permitir borrado
    - Permitir Bluetooth
    - Permitir NFC
    - Permitir Wi-Fi

  - **iOS**: se quitan todas las opciones de configuración, excepto las siguientes:
  
    - Permitir itinerancia de voz
    - Permitir itinerancia de datos
    - Permitir la sincronización automática en itinerancia

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>He cambiado un perfil de restricción de dispositivos, pero los cambios no han surtido efecto
Una vez establecidas las directivas de seguridad a través de MDM o EAS, los dispositivos Windows Phone no permiten que se reduzca el nivel de seguridad de estas. Por ejemplo, si establece una **contraseña con un número mínimo de 8 caracteres**, no podrá reducirla a 4. Esto se debe a que ya se ha aplicado el perfil más restrictivo en el dispositivo.

Si quiere cambiar el perfil a un valor menos seguro, debe restablecer las directivas de seguridad. Por ejemplo, en el escritorio de Windows 8.1, deslice el dedo desde la derecha y seleccione **Configuración** > **Panel de control**. Seleccione el applet **Cuentas de usuario** . En el menú de navegación izquierdo, hay un vínculo denominado **Restablecer las directivas de seguridad** (hacia la parte inferior). Selecciónelo y, después, elija **Restablecer directivas**.

En otros dispositivos MDM, como Android, Windows Phone 8.1 y versiones posteriores, iOS y Windows 10, es posible que tenga que eliminar la inscripción al servicio y volver a hacerla para poder aplicar un perfil menos restrictivo.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Algunas opciones de configuración de un perfil de Windows 10 devuelven "No aplicable"
Algunas opciones de configuración de los dispositivos Windows 10 pueden mostrarse como "No aplicable". Esto indica que esa configuración concreta no se admite en la versión o edición de Windows que se esté ejecutando en el dispositivo. Este mensaje puede aparecer por las siguientes razones:

- La configuración solo está disponible para versiones más recientes de Windows, pero no para la versión actual del sistema operativo (SO) del dispositivo.
- La configuración solo está disponible para ediciones de Windows o SKU específicas, como Home, Professional, Enterprise o Education.

Para obtener más información sobre los requisitos de versión y de SKU para las distintas opciones de configuración, vea [Configuration Service Provider (CSP) reference](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (Referencia del proveedor de servicios de configuración).

## <a name="next-steps"></a>Pasos siguientes
¿Necesita más ayuda? Consulte [Cómo obtener asistencia para Microsoft Intune](get-support.md).
