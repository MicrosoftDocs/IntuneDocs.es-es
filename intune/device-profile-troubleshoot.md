---
title: "Solución de problemas de perfiles de dispositivo en Microsoft Intune"
titlesuffix: Azure portal
description: Si se queda atascado, use este tema para ayudarle a resolver problemas con perfiles de dispositivo de Intune.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 1/17/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0bc5ad6e0467fe8a8c98c1ad2d71b967c18b8233
ms.sourcegitcommit: 967a7c23b863123398c40b812e2eb02c921a0afe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2018
---
# <a name="troubleshooting-device-profiles-in-microsoft-intune"></a>Solución de problemas de perfiles de dispositivo en Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La información de este tema puede usarse para ayudarle a solucionar problemas comunes de perfiles de dispositivo de Intune.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>¿Por qué un usuario no obtiene un perfil nuevo cuando cambia una contraseña o una frase de contraseña en un perfil de Wi-Fi existente? 
Al crear un perfil de Wi-Fi corporativo, implementar el perfil en un grupo, cambiar la contraseña y guardar el perfil, es de esperar que el usuario obtenga el nuevo perfil. Pero existe la posibilidad de que el usuario no lo obtenga. 

Para acabar con este problema, asegúrese de que el Wi-Fi de invitado está configurado de forma que el usuario pase a Wi-Fi de invitado si se produce un error en el Wi-Fi corporativo. La opción de conexión automática debe estar habilitada. Este perfil de Wi-Fi de invitado debe estar implementado en todos los usuarios.

Existen otros procedimientos recomendados que se pueden llevar a cabo:
- Como la red Wi-Fi a la que se está conectando precisa de una contraseña o frase de contraseña, asegúrese de que puede conectarse directamente al router Wi-Fi. Esto lo puede comprobar con un dispositivo iOS.
- Después de conectarse correctamente al punto de conexión Wi-Fi (router Wi-Fi), anote el SSID y la credencial que se han usado (esto es, la contraseña o frase de contraseña).
- Escriba el SSID y la credencial (contraseña o frase de contraseña) en el campo Clave precompartida. 
- Realice la implementación en un grupo de prueba que tenga un número de usuarios limitado, preferiblemente del equipo de TI. 
- Sincronice el dispositivo iOS con Intune. Inscríbalo si aún no lo ha hecho. 
- Vuelva a probar la conexión al mismo punto de conexión Wi-Fi (mencionado en el primer paso).
- Realice la implementación en grupos más grandes y, finalmente, en todos los usuarios relevantes de la organización. 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>¿Cuánto tiempo tardan los dispositivos móviles en obtener directivas o aplicaciones una vez asignadas?
Cuando se asigna una directiva o aplicación, Intune empieza inmediatamente a intentar notificar al dispositivo que debe conectar con el servicio Intune. Este proceso suele tardar menos de cinco minutos.

Si un dispositivo no se conecta para recibir la directiva una vez enviada la primera notificación, Intune hace tres intentos más. Si el dispositivo está desconectado (por ejemplo, está desactivado o no está conectado a una red), puede que no reciba las notificaciones. En ese caso, el dispositivo obtiene la directiva en la próxima conexión programada con el servicio Intune, como se indica a continuación:

- iOS y macOS: cada seis horas.
- Android: cada ocho horas.
- Windows Phone: cada ocho horas.
- Equipos con Windows 8.1 y Windows 10 inscritos como dispositivos: cada ocho horas.

Si el dispositivo se acaba de inscribir, la frecuencia de conexión es más frecuente, como se indica a continuación:

- iOS y macOS: cada 15 minutos durante seis horas y, después, cada seis horas.
- Android: cada tres minutos durante 15 minutos, luego cada 15 minutos durante dos horas y, después, cada ocho horas.
- Windows Phone: cada cinco minutos durante 15 minutos, luego cada 15 minutos durante dos horas y, después, cada ocho horas.
- Equipos con Windows inscritos como dispositivos: cada tres minutos durante 30 minutos y, después, cada ocho horas.

Los usuarios también pueden abrir la aplicación del Portal de empresa y sincronizar el dispositivo para buscar la directiva inmediatamente en cualquier momento.

En los dispositivos sin afinidad de usuario, la frecuencia de sincronización inmediatamente después de la inscripción puede variar de horas a un día o más. Intune envía solicitudes a diferentes intervalos para que un dispositivo se conecte con el servicio. Sin embargo, la conexión depende del dispositivo. Después de la inscripción inicial, dependiendo del tipo de inscripción de dispositivos y las directivas y perfiles asignados a un dispositivo, no se puede predecir el tiempo que tarda un dispositivo en completar el registro. Con todo, una vez que el dispositivo esté inscrito y se hayan aplicado todas las directivas iniciales, el dispositivo debería comprobar si hay nuevas directivas aproximadamente cada seis horas.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>¿Qué acciones provocan que Intune envíe inmediatamente una notificación a un dispositivo?
Los dispositivos conectan con Intune cuando reciben una notificación que se lo indica o durante la conexión programada periódicamente. Cuando el destino es un dispositivo o usuario concreto con una acción como un borrado, bloqueo, restablecimiento de código de acceso, asignación de aplicaciones, asignación de perfiles (Wi-Fi, VPN, correo electrónico, etc.) o asignación de directivas, Intune comienza inmediatamente a intentar notificar al dispositivo que debe conectarse al servicio Intune para recibir estas actualizaciones.

Otros cambios, como la revisión de la información de contacto del Portal de empresa, no provocan una notificación inmediata a los dispositivos.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Si varias directivas se asignan al mismo usuario o dispositivo, ¿cómo puedo saber qué configuración se aplica?
Cuando se aplican dos o más directivas se asignen al mismo usuario o dispositivo, la evaluación de la configuración aplicada se hace a nivel de parámetro individual:

-   La configuración de directivas de cumplimiento siempre tiene prioridad respecto a la configuración de directivas de configuración.

-   La configuración de directivas de cumplimiento más restrictiva se aplica si se evalúa con la misma configuración en otra directiva de cumplimiento.

-   Si una opción de la directiva de configuración entra en conflicto con una opción de otra directiva de configuración, este conflicto se muestra en Azure Portal. Debe resolver manualmente dichos conflictos.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>¿Qué sucede cuando las directivas de protección de aplicaciones entran en conflicto entre sí? ¿Cuál se aplica a la aplicación?
Los valores en conflicto son la configuración más restrictiva disponible en una directiva de protección de aplicaciones, excepto para los campos de entrada de números (como intentos de PIN antes del restablecimiento). Los campos de entrada de números se definen con los mismos valores que si crease una directiva de MAM en la consola con la opción de configuración recomendada.

Se producen conflictos cuando dos configuraciones de perfil son iguales. Por ejemplo, si configura dos directivas MAM que son idénticas, salvo por la configuración de copiar y pegar. En este escenario, la configuración de copiar y pegar se define con el valor más restrictivo, pero el resto de parámetros se aplican según la configuración.

Si un perfil se asigna a la aplicación y se aplica y, a continuación, se asigna un segundo, el primero tiene precedencia y se aplicará, mientras que el segundo presentará un conflicto. Si se aplican al mismo tiempo, lo que significa que no hay ningún perfil anterior, ambos están en conflicto. Cualquier configuración en conflicto se establece en los valores más restrictivos.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>¿Qué sucede cuando hay un conflicto de directivas personalizadas de iOS?
Intune no evalúa la carga de archivos de configuración de Apple ni perfiles personalizados de identificador uniforme de recursos de Open Mobile Alliance (OMA-URI). Sencillamente, se usa como mecanismo de entrega.

Al asignar un perfil personalizado, asegúrese de que los valores configurados no entran en conflicto con las directivas de cumplimiento, de configuración o con directivas personalizadas de otro tipo. En el caso de un perfil personalizado con conflictos de parámetros, el orden en que se aplican los conflictos es aleatorio.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>What happens when a profile is deleted or no longer applicable?
Al eliminar un perfil o quitar un dispositivo de un grupo al que se le asigna un perfil, se quita el perfil y la configuración del dispositivo según las siguientes listas.

### <a name="enrolled-devices"></a>Dispositivos inscritos

- Perfiles de correo electrónico, certificado, VPN y Wi-Fi: estos perfiles se quitan de todos los dispositivos inscritos admitidos.
- Todos los demás tipos de perfiles:
    - **Dispositivos Windows y Android**: la configuración no se quita del dispositivo.
    - **Dispositivos Windows Phone 8.1**: se quitan las opciones siguientes:
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
        - Permitir el restablecimiento de la configuración de fábrica
        - Permitir Bluetooth
        - Permitir NFC
        - Permitir Wi-Fi

    - **iOS**: se quitan todas las configuraciones, excepto:
        - Permitir itinerancia de voz
        - Permitir itinerancia de datos
        - Permitir la sincronización automática en itinerancia

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>He cambiado un perfil de restricción de dispositivos, pero los cambios no han surtido efecto
Una vez establecidas las directivas de seguridad a través de MSM o EAS, los dispositivos Windows Phone no permiten que se reduzca el nivel de seguridad de las mismas. Por ejemplo, si establece una **contraseña con un número mínimo de 8 caracteres** no podrá reducirla a 4. Esto se debe a que ya se ha aplicado el perfil más restrictivo en el dispositivo.

Dependiendo de la plataforma del dispositivo, si desea cambiar el perfil a un valor menos seguro, debe restablecer las directivas de seguridad.
Por ejemplo, en el escritorio de Windows, deslice el dedo desde la derecha para abrir la barra de **Botones de acceso** y seleccione **Configuración** &gt; **Panel de Control**. Seleccione el applet **Cuentas de usuario** .
En el menú de navegación izquierdo, hay un vínculo denominado **Restablecer las directivas de seguridad** en la parte inferior. Selecciónelo y luego elija el botón **Restablecer directivas**.
En otros dispositivos MDM como Android, Windows Phone 8.1 y posteriores y iOS, es posible que tenga que eliminar la inscripción y volver a hacerla para que pueda aplicar un perfil menos restrictivo.


### <a name="next-steps"></a>Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el servicio de soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](get-support.md) (Cómo obtener soporte técnico de Microsoft Intune).