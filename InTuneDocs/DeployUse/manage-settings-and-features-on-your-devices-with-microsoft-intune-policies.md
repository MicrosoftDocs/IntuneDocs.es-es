---
# required metadata

title: Administrar la configuración y las características de los dispositivos con directivas | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune
Las **directivas** de Microsoft Intune son grupos de configuraciones que controlan características en equipos y dispositivos móviles. Las directivas se crean con plantillas que contienen configuraciones recomendadas o personalizadas, y se implementan en grupos de dispositivos o usuarios.

## ¿Qué tipos de directiva se pueden usar?

Las directivas de Intune se dividen en las siguientes categorías. La directiva que use afectará a la forma de crear e implementar la directiva.


- **Directivas de configuración:** normalmente se utilizan para administrar las características y la configuración de seguridad en los dispositivos. Use la información de este tema para ver cómo crear e implementar estas directivas y para explorar las opciones disponibles.
- **Directivas de cumplimiento de dispositivos:** definen las reglas y los valores de configuración que un dispositivo debe cumplir para que se considere conforme a las directivas de acceso condicional. Las directivas de cumplimiento también se pueden usar para supervisar y corregir problemas de compatibilidad con dispositivos independientemente del acceso condicional.
Para obtener más información, consulte [Device compliance policies in Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md) (Directivas de cumplimiento de dispositivos de Microsoft Intune).
- **Directivas de acceso condicional:** estas directivas le ayudan a proteger el correo electrónico y otros servicios en función de las condiciones que especifique.
Para obtener más información, consulte [Restrict access to email and O365 services with Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (Restringir el acceso al correo electrónico y los servicios de O365 con Microsoft Intune).
- **Directivas de inscripción de dispositivos corporativos:** para obtener información sobre las directivas de inscripción de dispositivos corporativos, consulte [Set up iOS and Mac management with Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md) (Configurar la administración de iOS y Mac con Microsoft Intune).
- **Directivas de acceso a recursos:** este grupo de directivas funcionan juntas para ayudar a los usuarios a obtener acceso a los archivos y recursos que necesitan para hacer su trabajo correctamente, estén donde estén.
Para obtener más información, vea [Enable access to company resources with Microsoft Intune](enable-access-to-company-resources-with-microsoft-intune.md) (Habilitar el acceso a los recursos de la empresa con Microsoft Intune).


Para obtener una lista completa de las directivas de Intune, consulte [Microsoft Intune policy reference](microsoft-intune-policy-reference.md) (Referencia de directivas de Microsoft Intune).




## Crear una directiva de configuración

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), haga clic en **Directiva** &gt; **Directivas de configuración** &gt; **Agregar**.

2.  Seleccione la directiva que quiera, elija usar la configuración recomendada para la directiva (si está disponible; puede cambiar esta configuración en otro momento), o crear una directiva personalizada con su propia configuración.

    > [!TIP] Para obtener ayuda a la hora de elegir la directiva correcta, consulte [Microsoft Intune policy reference](microsoft-intune-policy-reference.md) (Referencia de directivas de Microsoft Intune).

3.  Cuando esté listo, haga clic en **Crear directiva**.

4.  En la pantalla **Crear directiva** , configure un nombre y una descripción opcional para la directiva.

5.  Configure la directiva necesaria y, a continuación, haga clic en **Guardar directiva**.

    Si necesita ayuda con la configuración de alguna directiva, elija el tipo de directiva en la lista siguiente:

    - [Configuración para dispositivos iOS](ios-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Android](android-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Windows 8 y Windows 8.1](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Windows Phone 8.1](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Configuración de escritorios y dispositivos móviles Windows 10](windows-10-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Windows Team](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Configuración de la actualización de la edición de Windows](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Configuración de dispositivos Mac OS X](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Configuración de Exchange ActiveSync](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [Configuración de la directiva de términos y condiciones](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [Configuración general para dispositivos móviles (heredado)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  En el cuadro de diálogo de confirmación, haga clic en **Sí** para implementar la directiva ahora o haga clic en **No** para crear la directiva sin implementarla.

Puede ver y editar la nueva directiva examinando las secciones de cada tipo de directiva en el área de trabajo **Directiva** .

Cuando se crea una directiva que usa la configuración recomendada, el nombre de la nueva directiva es una combinación del nombre de la plantilla, la fecha y la hora. Al modificar la directiva, el nombre se actualiza con la fecha y la hora de la edición.

Ahora que ha creado una directiva, probablemente querrá implementarla en uno o varios grupos de usuarios o dispositivos.

> [!TIP]
> No implemente todos los tipos de directiva. Por ejemplo, no se implementa la directiva de administración de aplicaciones móviles. Este tipo de directiva se asocia con una aplicación, que, a continuación, se implementa.

## Implementar una directiva de configuración

1.  En el área de trabajo **Directiva** , seleccione la directiva que quiera implementar y, a continuación, haga clic en **Administrar implementación**.

2.  En el cuadro de diálogo **Administrar la implementación** :

    -   **Para implementar la directiva**: seleccione uno o más grupos en los que quiera implementar la directiva y haga clic en **Agregar** &gt; **Aceptar**.

    -   **Para cerrar el cuadro de diálogo sin implementarla**: haga clic en **Cancelar**.

Cuando se selecciona una directiva implementada, puede ver más información acerca de la implementación en la parte inferior de la lista de directivas.

## Administrar directivas

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), haga clic en **Directiva**y, a continuación, busque y seleccione la directiva que desee administrar.

2.  Seleccione una de las siguientes acciones:

- **Editar**: abre las propiedades de la directiva seleccionada para que pueda realizar cambios.
- **Eliminar**: elimina la directiva seleccionada.<br>Al eliminar una directiva, se quita de todos los grupos en los que se ha implementado.
- **Administrar implementación**: seleccione el grupo en el que quiere implementar la directiva y haga clic en **Agregar**.

## Tareas para las directivas de Intune

### Para actualizar las directivas en un dispositivo y asegurarse de que están actualizadas (solo se aplica a los equipos con Windows que ejecutan el software cliente de Intune)

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), haga clic en **Grupos**y seleccione un grupo de dispositivos.

2.  Seleccione los dispositivos en los que quiere actualizar las directivas y haga clic en **Tareas remotas** &gt; **Actualizar directivas**.

3.  Haga clic en **Tareas remotas** en la esquina inferior derecha de la ventana de la consola de administración de Intune para comprobar el estado de la tarea.

## Preguntas más frecuentes sobre las directivas de Intune

### ¿Cuánto tiempo tardan los dispositivos móviles en obtener directivas o aplicaciones una vez implementados?
Cuando se implementa una directiva o aplicación, Intune empieza inmediatamente a intentar notificar al dispositivo que debe conectar con el servicio Intune. Este proceso suele tardar menos de 5 minutos.

Si un dispositivo no se conecta para recibir la directiva una vez enviada la primera notificación, se realizan 3 intentos más.  Si el dispositivo está desconectado (por ejemplo, está desactivado o no está conectado a una red), puede que no reciba las notificaciones.

En ese caso, el dispositivo obtendrá la directiva en la próxima conexión programada con el servicio Intune, como se indica a continuación:

- iOS: cada 6 horas
- Android: cada 8 horas
- Windows Phone: cada 8 horas
- Dispositivos Windows RT inscritos: cada 24 horas
- Equipos con Windows 8.1 y Windows 10 inscritos como dispositivos: cada 8 horas

Si el dispositivo se acaba de inscribir, la frecuencia de conexión será más frecuente, como se indica a continuación:

- iOS: cada 15 minutos durante 6 horas y, después, cada 6 horas
- Android: cada 3 minutos durante 15 minutos y, después, cada 15 minutos durante 2 horas y, después cada 8 horas
- Windows Phone: cada 5 minutos durante 15 minutos y, después, cada 15 minutos durante 2 horas y, después cada 8 horas
- Equipos con Windows inscritos como dispositivos: cada 3 minutos durante 30 minutos y, después, cada 24 horas

Los usuarios también pueden iniciar la aplicación del Portal de empresa y sincronizar el dispositivo para buscar la directiva inmediatamente en cualquier momento.

### ¿Qué acciones provocan que Intune envíe inmediatamente una notificación a un dispositivo?
Los dispositivos conectan con Intune cuando reciben una notificación que se lo indica o durante la conexión programada periódicamente que se muestra en las tablas superiores.  Cuando el destino es un dispositivo o usuario concreto con una acción como un borrado, bloqueo, restablecimiento de contraseña, implementación de aplicaciones, implementación de perfiles (Wi-Fi, VPN, correo electrónico, etc.) o implementación de directivas, Intune comenzará inmediatamente a intentar notificar al dispositivo que debe conectarse al servicio Intune para recibir estas actualizaciones.

Otros cambios, como la revisión de la información de contacto del portal de empresa, no provocan una notificación inmediata a los dispositivos.

> [!TIP]
> Cuando se implementa una directiva que contiene la configuración en un dispositivo Android, se indica al usuario que debe tomar medidas para cumplir con la directiva. Hasta que los usuarios realicen esta acción o se reinicie el dispositivo, la nueva configuración de directiva no surtirá efecto.

### Si varias directivas se implementan en el mismo usuario o dispositivo, ¿cómo puedo saber qué configuración se aplicará?
Es importante saber que, cuando se aplican dos o más directivas al mismo usuario o dispositivo, la evaluación de la configuración aplicada se hace a nivel de parámetro individual.

-   La configuración de directivas de cumplimiento siempre tiene prioridad respecto a la configuración de directivas de configuración

-   La configuración de directivas de cumplimiento más restrictiva se aplica si se evalúa con la misma configuración en otra directiva de cumplimiento

-   La configuración de directivas de configuración más restrictiva se aplica si se evalúa con la misma configuración en otra directiva de configuración

### ¿Qué sucede cuando las directivas de administración de aplicaciones móviles (MAM) entran en conflicto entre sí? ¿Cuál se aplicará a la aplicación?
Los valores en conflicto son la configuración más restrictiva disponible en una directiva de administración de aplicaciones móviles, excepto para los campos de entrada de números (como intentos de PIN antes del restablecimiento).  Los campos de entrada de números se definirán con los mismos valores que si crea una directiva MAM en la consola con la opción de configuración recomendada.

Se producen conflictos cuando dos configuraciones de directiva son iguales.  Por ejemplo, si configura dos directivas MAM que son idénticas, salvo por la configuración de copiar y pegar.  En este escenario, la configuración de copiar y pegar se definirá con el valor más restrictivo, pero el resto de parámetros se aplicará según la configuración.

Si una directiva se implementa en la aplicación y se aplica y, a continuación, se implementa una segunda, la primera tendrá precedencia y se aplicará, mientras que la segunda presentará un conflicto. Sin embargo, si se aplican al mismo tiempo, lo que significa que no hay ninguna directiva anterior, ambas estarán en conflicto y los parámetros en conflicto se definirán con los valores más restrictivos.

### ¿Qué sucede cuando hay un conflicto de directivas personalizadas de iOS?
Intune no evalúa la carga de archivos de configuración de Apple ni directivas personalizadas de OMA-URI; sencillamente, se usa como mecanismo de entrega.

Por lo tanto, al implementar una directiva personalizada, asegúrese de que los valores configurados no entran en conflicto con las directivas de cumplimiento, configuración o de otro tipo. En el caso de una directiva personalizada con conflictos de parámetros, el orden en que se aplican los conflictos es aleatorio.

### ¿Qué ocurre cuando se elimina una directiva o deja de ser aplicable?
Al eliminar una directiva o quitar un dispositivo de un grupo al que se le aplica una directiva, se quitará la directiva y la configuración del dispositivo según las siguientes tablas:

#### Dispositivos inscritos

- Perfiles de correo electrónico, certificado, VPN y Wi-Fi: estos perfiles se quitan de todos los dispositivos inscritos admitidos.
- Todos los demás tipos de directivas
    - **Dispositivos Windows y Android**: la configuración no se quita del dispositivo.
    - **Dispositivos Windows Phone 8.1**: se quitan las opciones siguientes:
        - Requerir una contraseña para desbloquear dispositivos móviles
        - Permitir contraseñas sencillas
        - Longitud mínima de contraseña
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

#### Equipos Windows que ejecutan el software cliente de Intune

- **Configuración de Endpoint Protection**: se restablecen los valores recomendados de la configuración. La única excepción es la opción de configuración **Unirse a Microsoft Active Protection Service** , para la que el valor predeterminado es **No**. Para obtener más información, consulte [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) (Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune).
- **Configuración de actualizaciones de software**: se restablece la configuración al estado predeterminado para el sistema operativo. Para obtener más información, consulte [Keep Windows PCs up to date with software updates in Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) (Mantener los equipos de Windows al día con las actualizaciones de software de Microsoft Intune).
- **Configuración de Microsoft Intune Center**: cualquier información de contacto de soporte configurada por la directiva se elimina de los equipos.
- **Configuración del Firewall de Windows**: se restablece la configuración predeterminada para el sistema operativo del equipo. Para obtener más información, consulte [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) (Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune).





<!--HONumber=May16_HO3-->


