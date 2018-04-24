---
title: Administración de la configuración de dispositivos con directivas
description: Use Intune para crear e implementar directivas que controlen la configuración y las características en los dispositivos inscritos que administre.
keywords: ''
author: dougeby
ms.author: angrobe
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6e639dda2509ab51bfcf6d0976be517e220800e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="manage-settings-and-features-on-your-devices-with-microsoft-intune-policies"></a>Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Las *directivas* de Microsoft Intune son grupos de configuraciones que controlan características en equipos y dispositivos móviles. Las directivas se crean con plantillas que contienen configuraciones recomendadas o personalizadas, y se implementan en grupos de dispositivos o usuarios.

## <a name="types-of-policies"></a>Tipos de directivas

Las directivas de Intune se dividen en las siguientes categorías. La categoría que se usa afecta a la manera de crear e implementar la directiva.


- **Directivas de configuración:** normalmente se usan para administrar las características y la configuración de seguridad en los dispositivos. Use la información de este tema para ver cómo crear e implementar estas directivas y para explorar las opciones disponibles.
- **Directivas de cumplimiento de dispositivos:** definen las reglas y los valores de configuración que un dispositivo debe cumplir para que se considere conforme a las directivas de acceso condicional. Las directivas de cumplimiento también se pueden usar para supervisar y corregir problemas de compatibilidad con dispositivos independientes del acceso condicional.
Para obtener más información, consulte [Device compliance policies in Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md) (Directivas de cumplimiento de dispositivos de Microsoft Intune).
- **Directivas de acceso condicional:** estas directivas le ayudan a proteger el correo electrónico y otros servicios en función de las condiciones que especifique.
Para obtener más información, consulte [Restrict access to email and O365 services with Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (Restringir el acceso al correo electrónico y los servicios de O365 con Microsoft Intune).
- **Directivas de inscripción de dispositivos corporativos**: para obtener información sobre las directivas de inscripción de dispositivos corporativos, consulte [Configurar la administración de dispositivos iOS y Mac](set-up-ios-and-mac-management-with-microsoft-intune.md).
- **Directivas de acceso a recursos:** estas directivas funcionan juntas para ayudar a los usuarios a obtener acceso a los archivos y recursos que necesitan para hacer su trabajo correctamente, estén donde estén.
Para obtener más información, vea [Enable access to company resources with Microsoft Intune](enable-access-to-company-resources-with-microsoft-intune.md) (Habilitar el acceso a los recursos de la empresa con Microsoft Intune).


Para obtener una lista completa de las directivas de Intune, consulte [Microsoft Intune policy reference](microsoft-intune-policy-reference.md) (Referencia de directivas de Microsoft Intune).

## <a name="create-a-configuration-policy"></a>Crear una directiva de configuración

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), elija **Directiva** &gt; **Directivas de configuración** &gt; **Agregar**.

2.  Seleccione la directiva que quiera y elija usar la configuración recomendada para la directiva (si está disponible; puede cambiar esta configuración en otro momento) o crear una directiva personalizada con su propia configuración.

    > [!TIP]
    > Para obtener ayuda a la hora de elegir la directiva correcta, vea [Referencia de directivas de Microsoft Intune](microsoft-intune-policy-reference.md).

3.  Cuando esté listo, elija **Crear directiva**.

4.  En la página **Crear directiva** , configure un nombre y una descripción opcional para la directiva.

5.  Configure la directiva necesaria y después elija **Guardar directiva**.

    Si necesita ayuda con la configuración de alguna directiva, elija el tipo de directiva en la lista siguiente:

    - [Configuración de dispositivos iOS](ios-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Android](android-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Windows 8 y Windows 8.1](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Windows Phone 8.1](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Windows 10 Desktop y Mobile](windows-10-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Windows Team](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Configuración de la actualización de la edición de Windows](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Mac OS X](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Configuración de Exchange ActiveSync](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [Configuración de la directiva de términos y condiciones](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [Configuración general para dispositivos móviles (heredado)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  En el cuadro de diálogo de confirmación, elija **Sí** para implementar la directiva ahora o elija **No** para crear la directiva sin implementarla.

Puede ver y editar la nueva directiva examinando las secciones de cada tipo de directiva en el área de trabajo **Directiva** .

Cuando se crea una directiva que usa la configuración recomendada, el nombre de la nueva directiva es una combinación del nombre de la plantilla, la fecha y la hora. Al modificar la directiva, el nombre se actualiza con la fecha y la hora de la edición.

Después de crear una directiva, probablemente querrá implementarla en uno o varios grupos de usuarios o dispositivos.

> [!TIP]
> No implemente todos los tipos de directiva. Por ejemplo, no se implementa la directiva de administración de aplicaciones (MAM) móviles. Este tipo de directiva se asocia con una aplicación, que, a continuación, se implementa.

## <a name="deploy-a-configuration-policy"></a>Implementar una directiva de configuración

1.  En el área de trabajo **Directiva**, seleccione la directiva que quiera implementar y, después, haga clic en **Administrar implementación**.

2.  En el cuadro de diálogo **Administrar la implementación** :

    -   Para implementar la directiva, seleccione uno o más grupos en los que quiera implementarla y luego elija **Add** (Agregar) &gt; **OK** (Aceptar).

    -   Para cerrar el cuadro de diálogo sin implementar la directiva, elija **Cancel** (Cancelar).

Cuando se selecciona una directiva implementada, puede ver más información acerca de la implementación en la parte inferior de la lista de directivas.

## <a name="manage-policies"></a>Administrar directivas

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), elija **Directiva**y, después, busque y seleccione la directiva que quiera administrar.

2.  Seleccione una de las siguientes acciones:

- **Editar**: abra las propiedades de la directiva seleccionada para poder hacer cambios.
- **Delete** (Eliminar): elimine la directiva seleccionada.<br>Al eliminar una directiva, se quita de todos los grupos en los que se ha implementado.
- **Administrar implementación**: seleccione el grupo en el que quiera implementar la directiva y elija **Add** (Agregar).


## <a name="frequently-asked-questions-about-intune-policies"></a>Preguntas más frecuentes sobre las directivas de Intune

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-deployed"></a>¿Cuánto tiempo tardan los dispositivos móviles en obtener directivas o aplicaciones una vez implementados?
Cuando se implementa una directiva o aplicación, Intune empieza inmediatamente a intentar notificar al dispositivo que debe conectar con el servicio Intune. Este proceso suele tardar menos de cinco minutos.

Si un dispositivo no se conecta para recibir la directiva una vez enviada la primera notificación, Intune hace tres intentos más.  Si el dispositivo está desconectado (por ejemplo, está desactivado o no está conectado a una red), puede que no reciba las notificaciones. En ese caso, el dispositivo obtendrá la directiva en la próxima conexión programada con el servicio Intune, como se indica a continuación:

- iOS y Mac OS X: cada 6 horas.
- Android: cada 8 horas.
- Windows Phone: cada 8 horas.
- Equipos con Windows 8.1 y Windows 10 inscritos como dispositivos: cada 8 horas.

Si el dispositivo se acaba de inscribir, la frecuencia de conexión será más frecuente, como se indica a continuación:

- iOS y Mac OS X: cada 15 minutos durante 6 horas y, después, cada 6 horas.
- Android: cada 3 minutos durante 15 minutos y, después, cada 15 minutos durante 2 horas y, después, cada 8 horas.
- Windows Phone: cada 5 minutos durante 15 minutos y, después, cada 15 minutos durante 2 horas y, después, cada 8 horas.
- Equipos con Windows inscritos como dispositivos: cada 3 minutos durante 30 minutos y, después, cada 8 horas.

Los usuarios también pueden abrir la aplicación del Portal de empresa y sincronizar el dispositivo para buscar la directiva inmediatamente en cualquier momento.

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>¿Qué acciones provocan que Intune envíe inmediatamente una notificación a un dispositivo?
Los dispositivos conectan con Intune cuando reciben una notificación que se lo indica o durante la conexión programada periódicamente.  Cuando el destino es un dispositivo o usuario concreto con una acción como un borrado, bloqueo, restablecimiento de código de acceso, implementación de aplicaciones, implementación de perfiles (Wi-Fi, VPN, correo electrónico, etc.) o implementación de directivas, Intune comenzará inmediatamente a intentar notificar al dispositivo que debe conectarse al servicio Intune para recibir estas actualizaciones.

Otros cambios, como la revisión de la información de contacto del Portal de empresa, no provocan una notificación inmediata a los dispositivos.

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-will-get-applied"></a>Si varias directivas se implementan en el mismo usuario o dispositivo, ¿cómo puedo saber qué configuración se aplicará?
Cuando se aplican dos o más directivas al mismo usuario o dispositivo, la evaluación de la configuración aplicada se hace a nivel de parámetro individual:

-   La configuración de directivas de cumplimiento siempre tiene prioridad respecto a la configuración de directivas de configuración.

-   La configuración de directivas de cumplimiento más restrictiva se aplica si se evalúa con la misma configuración en otra directiva de cumplimiento.

-   Si una opción de la directiva de configuración entra en conflicto con una opción de una directiva de configuración diferente, este conflicto se mostrará en la consola de Intune. Debe resolver manualmente dichos conflictos.

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-will-be-applied-to-the-app"></a>¿Qué sucede cuando las directivas de administración de aplicaciones móviles entran en conflicto entre sí? ¿Cuál se aplicará a la aplicación?
Los valores en conflicto son la configuración más restrictiva disponible en una directiva de MAM, excepto para los campos de entrada de números (como intentos de PIN antes del restablecimiento).  Los campos de entrada de números se definirán con los mismos valores que si crease una directiva de MAM en la consola con la opción de configuración recomendada.

Se producen conflictos cuando dos configuraciones de directiva son iguales.  Por ejemplo, si configura dos directivas MAM que son idénticas, salvo por la configuración de copiar y pegar.  En este escenario, la configuración de copiar y pegar se definirá con el valor más restrictivo, pero el resto de parámetros se aplicará según la configuración.

Si una directiva se implementa en la aplicación y se aplica y, a continuación, se implementa una segunda, la primera tendrá precedencia y se aplicará, mientras que la segunda presentará un conflicto. Si se aplican al mismo tiempo, lo que significa que no hay ninguna directiva anterior, ambas estarán en conflicto. Cualquier configuración en conflicto se establecerá en los valores más restrictivos.

### <a name="what-happens-when-ios-custom-policies-conflict"></a>¿Qué sucede cuando hay un conflicto de directivas personalizadas de iOS?
Intune no evalúa la carga de archivos de configuración de Apple ni directivas personalizadas de identificador uniforme de recursos de Open Mobile Alliance (OMA-URI). Sencillamente, se usa como mecanismo de entrega.

Al implementar una directiva personalizada, asegúrese de que los valores configurados no entran en conflicto con las directivas de cumplimiento, configuración o de otro tipo. En el caso de una directiva personalizada con conflictos de parámetros, el orden en que se aplican los conflictos es aleatorio.

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>¿Qué ocurre cuando se elimina una directiva o deja de ser aplicable?
Al eliminar una directiva o quitar un dispositivo de un grupo al que se le aplica una directiva, se quitará la directiva y la configuración del dispositivo según las siguientes listas.

#### <a name="enrolled-devices"></a>Dispositivos inscritos

- Perfiles de correo electrónico, certificado, VPN y Wi-Fi: estos perfiles se quitan de todos los dispositivos inscritos admitidos.
- Todos los demás tipos de directivas:
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

#### <a name="windows-pcs-running-the-intune-client-software"></a>Equipos Windows que ejecutan el software cliente de Intune

- **Configuración de Endpoint Protection**: se restablecen los valores recomendados de la configuración. La única excepción es la opción de configuración **Unirse a Microsoft Active Protection Service**, cuyo valor predeterminado es **No**. Para obtener más información, consulte [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) (Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune).
- **Configuración de actualizaciones de software**: se restablece la configuración al estado predeterminado para el sistema operativo. Para obtener más información, consulte [Mantener los equipos Windows al día con las actualizaciones de software de Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).
- **Configuración de Microsoft Intune Center**: cualquier información de contacto de soporte configurada por la directiva se elimina de los equipos.
- **Configuración del Firewall de Windows**: se restablece la configuración predeterminada para el sistema operativo del equipo. Para obtener más información, consulte [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) (Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune).


### <a name="how-can-i-refresh-the-policies-on-a-device-to-ensure-that-they-are-current-applies-to-windows-pcs-running-the-intune-client-software-only"></a>¿Cómo puedo actualizar las directivas en un dispositivo para asegurarme de que están actualizadas (solo se aplica a los equipos con Windows que ejecutan el software cliente de Intune)?

1.  En un grupo de dispositivos, seleccione los dispositivos en los que quiere actualizar las directivas y luego elija **Tareas remotas** &gt; **Actualizar directivas**.
2.  Elija **Tareas remotas** en la esquina inferior derecha de la ventana de la consola de administración de Intune para comprobar el estado de la tarea.

### <a name="where-can-i-find-help-troubleshooting-policies"></a>¿Dónde puedo encontrar ayuda para solucionar problemas en las directivas?

Vea [Directivas de solución de problemas en Microsoft Intune](/intune-classic/troubleshoot/troubleshoot-policies-in-microsoft-intune).
