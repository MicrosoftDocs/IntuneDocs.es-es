---
# required metadata

title: Guía para desarrolladores acerca del SDK de aplicaciones de Microsoft Intune para Android | Microsoft Intune
description:
keywords:
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune

> [!NOTE] Puede que quiera leer primero la [Información general del SDK para aplicaciones de Intune](intune-app-sdk.md), que cubre las características actuales del SDK y describe cómo preparar la integración en cada plataforma compatible. 

# Qué hay en el SDK 

El SDK para aplicaciones de Intune para Android es una biblioteca de Android estándar que no tiene dependencias externas. 
El SDK se compone de:  

* **`Microsoft.Intune MAM.SDK.jar`**: interfaces necesarias para habilitar MAM en una aplicación, así como la interoperabilidad con la aplicación Portal de empresa de Microsoft Intune. Las aplicaciones deben especificarla como una referencia a la biblioteca Android.

*  **`Microsoft.Intune.MAM.SDK.Support.v4.jar`**: interfaces necesarias para habilitar MAM en aplicaciones que aprovechan la biblioteca de compatibilidad de Android v4.  Aquellas aplicaciones que necesiten este tipo de compatibilidad deben hacer referencia al archivo jar directamente. 

* **`Microsoft.Intune.MAM.SDK.Support.v7.jar`**: interfaces necesarias para habilitar MAM en aplicaciones que aprovechan la biblioteca de compatibilidad de Android v7.   Aquellas aplicaciones que necesiten este tipo de compatibilidad deben hacer referencia al archivo jar directamente.

* **El directorio de recursos**: se compone de los recursos (como por ejemplo, las cadenas) en los que se basa el SDK. 

* **`Microsoft.Intune.MAM.SDK.aar`**: componentes del SDK, excepto los archivos .jar Support.V4 y Support.V7. Puede usar este archivo en lugar de los componentes individuales, si el sistema de compilación admite archivos AAR.

* **`AndroidManifest.xml`**: puntos de entrada adicionales y requisitos de la biblioteca. 

* **`THIRDPARTYNOTICES.TXT`**: aviso de atribución que reconoce el código de terceros o de OSS que se compilará en la aplicación. 

# Requisitos 

El SDK para aplicaciones de Intune es un proyecto de Android compilado. Como resultado, resulta ser un SDK extraordinariamente independiente de la versión de Android que usa la aplicación para sus versiones de API mínimas o de destino. El SDK admite las API de la 14 a la 24 de Android (Android 4.0 +). 

# Cómo funciona el SDK para aplicaciones de Intune 

Para que el SDK para aplicaciones de Intune pueda habilitar las directivas de administración de aplicaciones, es necesario realizar algunos cambios en el código de origen de una aplicación. Esto se puede llevar a cabo reemplazando las clases base de Android con las clases administradas equivalentes mencionadas en el documento y que tienen el prefijo `MAM`. Las clases del SDK son un término medio entre las clases base de Android y la versión derivada que la propia aplicación tiene de esas clases.  Si usamos una actividad a modo de ejemplo, terminará con una jerarquía de herencia que tendrá el siguiente aspecto: `Activity ->MAMActivity->AppSpecificActivity`.

Cuando `AppSpecificActivity` quiere interactuar con su elemento primario (por ejemplo, `super.onCreate())`), `MAMActivity` se considera la superclase a pesar de estar en la jerarquía de herencia y de reemplazar unos cuantos métodos. Las aplicaciones de Android tienen un modo único y acceso a todo el sistema a través de su objeto de contexto.  Por otro lado, las aplicaciones que tienen incorporado el SDK para aplicaciones de Intune tienen dos modos; tenga en cuenta que estas aplicaciones siguen teniendo acceso al sistema a través del objeto de contexto pero, dependiendo de la actividad base utilizada, es Android quien proporciona el objeto de contexto o este se divide inteligentemente entre una vista restringida del sistema y el contexto proporcionado por Android.

La aplicación Portal de empresa debe estar presente en el dispositivo para que el SDK para aplicaciones de Intune para Android pueda habilitar las directivas de MAM. Cuando la aplicación Portal de empresa no está presente, el comportamiento de la aplicación habilitada por MAM no se modificará y esta actuará como cualquier otra aplicación móvil. Cuando el Portal de empresa se instala y tiene una directiva para el usuario, los puntos de entrada del SDK se inicializan de forma asincrónica. Solo es necesario realizar la inicialización cuando es Android quien crea inicialmente el proceso. Durante la inicialización, se establece una conexión con la aplicación Portal de empresa y se descarga la directiva de restricción de la aplicación.  

# Cómo realizar integraciones con el SDK para aplicaciones de Intune
 
Tal como se indicó antes, para que el SDK pueda habilitar las directivas de administración de aplicaciones, es necesario realizar algunos cambios en el código de origen de la aplicación. Estos son los pasos necesarios para habilitar MAM en la aplicación: 

## Reemplace las clases, los métodos y las actividades con su equivalente MAM (obligatorio) 

* Las clases base de Android deben sustituirse por su equivalente MAM. Para ello, busque todas las instancias de las clases enumeradas en la tabla siguiente y reemplácelas con el SDK para aplicaciones de Intune equivalente.  

    | Clase de Android | Reemplazar por estos SDK para aplicaciones de Intune  |
    |--|--|
    | android.app.Activity | MAMActivity |
    | android.app.ActivityGroup | MAMActivityGroup |
    | android.app.AliasActivity | MAMAliasActivity |
    | android.app.Application | MAMApplication |
    | android.app.DialogFragment | MAMDialogFragment |
    | android.app.ExpandableListActivity | MAMExpandableListActivity |
    | android.app.Fragment | MAMFragment |
    | android.app.IntentService | MAMIntentService |
    | android.app.LauncherActivity | MAMLauncherActivity |
    | android.app.ListActivity | MAMListActivity |
    | android.app.NativeActivity | MAMNativeActivity |
    | android.app.PendingIntent | MAMPendingIntent |
    | android.app.Service | MAMService |
    | android.app.TabActivity | MAMTabActivity |
    | android.app.TaskStackBuilder | MAMTaskStackBuilder |
    | android.app.backup.BackupAgent | MAMBackupAgent |
    | android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
    | android.app.backup.FileBackupHelper | MAMFileBackupHelper |
    | android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
    | android.content.BroadcastReceiver | MAMBroadcastReceiver |
    | android.content.ContentProvider | MAMContentProvider |
    | android.os.Binder | MAMBinder* |
    | android.provider.DocumentsProvider | MAMDocumentsProvider |
    | android.preference.PreferenceActivity | MAMPreferenceActivity |

    * Solo es necesario reemplazar el enlazador con MAMBinder si este no se genera desde una interfaz AIDL.

    **Microsoft.Intune.MAM.SDK.Suppot.v4.jar**:

    | MAM de Intune de clase Android | Reemplazar por estos SDK |
    |--|--|
    | android.support.v4.app.DialogFragment | MAMDialogFragment
    | android.support.v4.app.FragmentActivity | MAMFragmentActivity
    | android.support.v4.app.Fragment | MAMFragment
    | android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
    | android.support.v4.content.FileProvider | MAMFileProvider
    
    **Microsoft.Intune.MAM.SDK.Suppot.v7.jar**:

    |Clase de Android | Reemplazar por estos SDK de MAM de Intune |
    |--|--|
    |android.support.v7.app.ActionBarActivity | MAMActionBarActivity |


* Cuando se usa un punto de entrada de Android que se ha reemplazado por su equivalente MAM, se debe usar una versión alternativa del ciclo de vida del punto de entrada (a excepción de la clase `MAMApplication`).

    Por ejemplo, al derivar desde la clase `MAMActivity`, en lugar de reemplazar `onCreate` y llamar a `super.onCreate`, la actividad debe reemplazar `onMAMCreate` y llamar a`uper.onMAMCreate`. Esto permite que, en ciertos casos, se restrinja el inicio de la actividad (entre otras cosas). 

# Habilitar características que requieren la participación de la aplicación 

Existen algunas directivas que el SDK no puede implementar por sí mismo. Para hacer que la aplicación pueda controlar su comportamiento en lo que se refiere a estas características, le planteamos varias API que puede encontrar en la interfaz `AppPolicy` que encontrará un poco más abajo.  

    /**
     * External facing app policies.
     */
    public interface AppPolicy {
        /**
         * Restrict where an app can save personal data.
         * 
         * @return True if the app is allowed to save to personal data stores;
         *         false otherwise.
         */
        boolean getIsSaveToPersonalAllowed();
    
        /**
         * Check if policy prohibits saving to a content provider location.
         * 
         * @param location
         *            a content URI to check
         * @return True if location is not a content URI or if policy does not 
         *         prohibit saving to the content location.
         */
        boolean getIsSaveToLocationAllowed(android.net.Uri location); 
    
        /**
         * Whether the SDK PIN prompt is enlightened for the app.
         * 
         * @return True if the PIN is enabled. False otherwise.
         */
        boolean getIsPinRequired();
        /**
         * Whether the Intune Managed Browser is required to open web links.
         *
         * @return True if the Managed Browser is required, false otherwise
         */
        boolean getIsManagedBrowserRequired();
    }

## Habilitar el control de administración de TI en el comportamiento de guardado de una aplicación

Muchas aplicaciones implementan características que permiten al usuario final guardar archivos de forma local o en otro servicio. El SDK para aplicaciones de Intune permite a los administradores de TI evitar que se filtren los datos aplicando restricciones de directivas en su organización, según lo consideren oportuno.  Una de las directivas que un administrador puede controlar, es permitir si el usuario final puede guardar elementos en un almacén de datos personales. Esto incluye guardar datos en una ubicación local, en una tarjeta SD o en servicios de copia de seguridad. Para poder habilitar esta característica, es necesaria la participación de la aplicación. Si la aplicación permite guardar datos directamente en ubicaciones personales o en la nube, debe implementar esta característica para garantizar que los administradores de TI puedan controlar los permisos para guardar datos en una ubicación. La siguiente API permite a la aplicación saber si está permitido guardar datos en un almacén personal, según la directiva de administración actual. Gracias a ello, la aplicación puede aplicar la directiva ya que “sabe” que el usuario final puede guardar datos personales a través de ella.  

Para determinar si debe aplicar la directiva, la aplicación puede realizar la siguiente llamada: 

    MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();

**Nota**: el elemento MAMComponents.get(AppPolicy.class) devolverá siempre una directiva de aplicación que no es nula, incluso si no se está administrando el dispositivo o la aplicación. 

## Permitir que la aplicación detecte si es necesaria la directiva de PIN
 
 Existen directivas adicionales de las cuales la aplicación puede desactivar algunas funciones, con el fin de no duplicar las características del SDK para aplicaciones de Intune. Por ejemplo, si la aplicación tiene su propia experiencia de usuario de PIN, puede deshabilitarla si el SDK está configurado para solicitar al usuario final que escriba un PIN. 

Para determinar si la directiva de PIN está configurada para solicitar que se escriba el PIN periódicamente, la aplicación puede realizar la siguiente llamada: 

    MAMComponents.get(AppPolicy.class).getIsPinRequired();

## Registrarse para recibir notificaciones del SDK  

El SDK de aplicaciones de Intune permite a la aplicación controlar el comportamiento que se llevará a cabo cuando el administrador de TI usa determinadas directivas, como por ejemplo, una directiva de borrado remoto. Para ello, debe registrarse para recibir notificaciones del SDK mediante la creación de una clase `MAMNotificationReceiver` y registrarla mediante `MAMNotificationReceiverRegistry`. Esto se hace proporcionando el receptor y el tipo de notificación que el receptor desea recibir en  `App.onCreate`, tal como se muestra en el ejemplo siguiente:
 
    @Override
      public void onCreate() {
            super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class).registerReceiver(
    new ToastNotificationReceiver(), MAMNotificationType.WIPE_USER_DATA);
    }

`MAMNotificationReceiver` simplemente recibe notificaciones. Algunas notificaciones se administran directamente mediante el SDK y otras requieren que la aplicación participe. Una aplicación debe devolver los valores “true” o “false” desde una notificación. Recuerde que siempre debe devolver el valor “true” a menos que falle alguna acción realizada como consecuencia de la notificación. Errores como que la aplicación indique que no se pudieron borrar los datos de usuario, se notifican al servicio de Intune. Puede bloquear con seguridad el elemento `MAMNotificationReceiver.onReceive`; su devolución de llamada no se ejecuta en el subproceso de la interfaz de usuario. 

La interfaz `MAMNotificationReceiver se incluye a continuación, tal como se define en el SDK: 

    /**
     * The SDK is signaling that a MAM event has occurred. 
     * 
     */
    public interface MAMNotificationReceiver {
      /**
      * A notification was received.
      * 
      * @param notification
      *            The notification that was received.
    * @return The receiver should return true if it handled the
    *   notification without error (or if it decided to ignore the
    *   notification). If the receiver tried to take some action in 
    *   response to the notification but failed to complete that
      *   action it should return false.
      */
      boolean onReceive(MAMNotification notification);
    }

Las siguientes notificaciones se envían a la aplicación y es posible que algunas de ellas necesiten que participe la aplicación: 

* **Notificación `WIPE_USER_DATA`**: esta notificación se envía en una clase `MAMUserNotification`. Cuando se recibe esta notificación, la aplicación debe eliminar todos los datos asociados con la identidad que pasa con la clase `MAMUserNotification`. Actualmente, esta notificación se envía durante la anulación de la inscripción del servicio de Intune. Normalmente, se especifica el nombre del usuario principal durante el proceso de inscripción. Si se registra para esta notificación, la aplicación debe asegurarse de que todos los datos de usuario se han eliminado. Si no se registra, se llevará a cabo de forma predeterminada el proceso de eliminación selectiva. 

* **Notificación `WIPE_USER_AUXILIARY_DATA`**: las aplicaciones pueden registrarse para esta notificación si quieren que el SDK para aplicaciones de Intune realice el borrado predeterminado a la vez que quita algunos datos auxiliares.  

* **Notificación `REFRESH_POLICY`**: esta notificación se envía en un elemento MAMNotification sin ninguna información adicional. Cuando se recibe esta notificación, cualquier directiva almacenada en caché debe considerarse como válida y, por lo tanto, debería tener en cuenta qué tipo de directiva es. Esto generalmente se controla mediante el SDK, sin embargo debería gestionarse con la aplicación si se utiliza la directiva habitualmente. 

## Propósitos y métodos pendientes 

Después de realizar la derivación desde uno de los puntos de entrada MAM, puede usar el contexto tal como lo haría normalmente para acciones como iniciar las actividades, usar `PackageManager`, etc.  Las clases  `PendingIntents` son una excepción a esta regla. Al llamar a este tipo de clases, debe cambiar el nombre de la clase. Por ejemplo, en lugar de usar `PendingIntent.get*`, se debe usar `MAMPendingIntents.get*`. 

En algunos casos, un método que se encuentra en la clase Android se marca como final de la clase de reemplazo MAM. En este caso, la clase de reemplazo MAM proporciona un método con un nombre similar (generalmente lleva el sufijo "MAM") y se debe reemplazar. Por ejemplo, en lugar de reemplazar `ContentProvider.query`, debe reemplazar `MAMContentProvider.queryMAM`. El compilador de Java debe encargarse de aplicar las restricciones necesarias para evitar que se reemplace por accidente el método original en lugar del equivalente MAM. 

# Proteger los datos de copia de seguridad 

En lo referente a la versión Android Marshmallow (API 23), el sistema Android tiene ahora dos formas para que una aplicación pueda hacer una copia de seguridad de sus datos. Estas opciones están disponibles en la aplicación y requieren que se lleven a cabo distintos pasos para asegurarse de que la protección de datos MAM se aplica correctamente. Puede revisar la siguiente tabla para obtener información general acerca de las acciones necesarias para que la protección de datos funcione correctamente.  Asimismo, también puede encontrar más información sobre la copia de seguridad de Android en la [Guía sobre la copia de seguridad de datos para el desarrollador de Android](http://developer.android.com/guide/topics/data/backup.html.). 

## Realizar una copia de seguridad completa de forma automática

En Android M, el sistema Android comenzó a ofrecer a las aplicaciones copias de seguridad completas de forma automática, independientemente de la API de destino cuando esta se ejecutaba en un dispositivo Android M. Siempre que el atributo `android:allowBackup` no tenga el valor “false”, la aplicación obtendrá sus propias copias de seguridad de forma completa y sin filtrar. Esto supone un riesgo de pérdida de datos, por lo tanto, es necesario que realicen en el SDK los cambios que se indican en la tabla que tiene a continuación, para que pueda asegurarse de que se aplica la protección de datos.  Es importante que siga las instrucciones descritas a continuación para proteger los datos del cliente correctamente.  Si establece `android:allowBackup=false` , la aplicación nunca se pondrá en cola para obtener las copias de seguridad realizadas por el sistema operativo, y no podrá realizar ninguna acción adicional de MAM, puesto que no habrá ninguna copia de seguridad para ello
 
 ## Copias de seguridad de tipo "key/value"

Esta opción está disponible para todas las API y usa los elementos `BackupAgent` y `BackupAgentHelper`. 

### Uso de BackupAgentHelper

`BackupAgentHelper` es mucho más fácil de implementar que `BackupAgent` tanto en términos de funcionalidad nativa de Android como en cuanto a la integración de MAM. `BackupAgentHelper` permite al desarrollador registrar archivos completos y preferencias compartidas en `FileBackupHelper` o `SharedPreferencesBackupHelper` respectivamente, los cuales se agregan posteriormente al elemento `BackupAgentHelper` tras su creación. 

### Uso de BackupAgent

`BackupAgent` le permite ser mucho más explícito acerca de los datos sobre los cuales quiere hacer una copia de seguridad. Sin embargo, tenga en cuenta que con esta opción no podrá aprovechar el marco de trabajo de copia de seguridad que le ofrece Android.  Como realizar una implementación supone un grado bastante alto de responsabilidad, deberá dar más pasos para garantizar la protección de datos de MAM. Puesto que la mayoría del trabajo lo realizará usted como desarrollador, la integración de MAM le puede resultar ligeramente más complicada. 

#### La aplicación no tiene un agente de copia de seguridad
  
Estas son las opciones que encontrará el desarrollador cuando se establece `Android:allowbBackup =true`:

##### Copia de seguridad completa según un archivo de configuración: 

Proporcione un recurso en la etiqueta de metadatos `com.microsoft.intune.mam.FullBackupContent` del manifiesto. Por ejemplo:
    `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

Agregue el siguiente atributo en la etiqueta `<application>` : `android:fullBackupContent="@xml/my_scheme"`, donde `my_scheme` es un recurso XML de su aplicación. 

##### Copia de seguridad completa sin exclusiones 

Proporcione una etiqueta en el manifiesto, como `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />` 
 
Agregue el siguiente atributo en la etiqueta `<application>`: `android:fullBackupContent="true"`.

#### La aplicación tiene un agente de copia de seguridad

Siga las recomendaciones de las secciones `BackupAgent` y `BackupAgentHelper` descritas anteriormente 

Considere la posibilidad de usar nuestro elemento `MAMDefaultFullBackupAgent`, ya que proporciona copias de seguridad sencillas en Android M. 

### Antes de hacer la copia de seguridad

Antes de comenzar con la copia de seguridad, debe comprobar de que realmente puede realizar copias de seguridad de los búferes de archivos o de datos. Para averiguar si puede hacer estas copias, le ofrecemos la función `isBackupAllowed` en `MAMFileProtectionManager` y `MAMDataProtectionManager` . Si no puede hacer la copia de seguridad del búfer de datos o de archivos, le recomendamos que no lo use en la copia.

Si quiere realizar una copia de seguridad de las identidades de los archivos que registró en el paso 1 mientras realiza la copia de seguridad, debe llamar a `backupMAMFileIdentity(BackupDataOutput data, File … files)` con los archivos de los que planea extraer datos. Esto creará automáticamente nuevas entidades de copia de seguridad y las escribirá en `BackupDataOutput` . Estas entidades se consumirán automáticamente durante la restauración. 

## Configurar la Biblioteca de autenticación de Azure Directory (ADAL)  

El SDK se basa en ADAL para realizar su autenticación y para los escenarios de inicio condicional, lo cual requiere que las aplicaciones tengan ciertos elementos de configuración de Azure Active Directory. Los valores de configuración se comunican con el SDK mediante los metadatos de `AndroidManifest` . Para configurar la aplicación y habilitar la autenticación correcta, agregue los datos siguientes en el nodo de la aplicación en el elemento `AndroidManifest`. Algunas de estas opciones de configuración solo son necesarias si la aplicación usa ADAL para la autenticación en general; en ese caso, necesitará los valores específicos que su aplicación usa para registrarse con AAD. Esto se hace para garantizar de que no se le solicita la autenticación por duplicado al usuario final, ya que tenga en cuenta que AAD debe reconocer dos valores de registro independientes: uno de la aplicación y otro del SDK. 

        <meta-data
            android:name="com.microsoft.intune.mam.aad.Authority"
            android:value="https://AAD authority/" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.ClientID"
            android:value="your-client-ID-GUID" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.NonBrokerRedirectURI"
            android:value="your-redirect-URI" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.SkipBroker"
            android:value="[true | false]" />

No se espera que los GUID tengan el símbolo de llave de apertura o de cierre.

### Opciones de configuración comunes de ADAL 

La siguiente configuración detalla opciones comunes referentes a los valores que se explicaron anteriormente: 

#### La aplicación no integra ADAL

* La autoridad debe establecerse en el entorno deseado donde se han configurado las cuentas de AAD.

* SkipBroker debe establecerse en “true”.

#### La aplicación integra ADAL

* La autoridad debe establecerse en el entorno deseado donde se han configurado las cuentas de AAD.

* El Id. de cliente se debe establecer en el identificador de cliente de la aplicación.

* `NonBrokerRedirectURI` debería establecerse en un URI de redireccionamiento válido de la aplicación.
    * Or `urn:ietf:wg:oauth:2.0:oob` debe configurarse como un URI de redirección de AAD válido.

* SkipBroker debe establecerse con el valor “false” (o estar ausente)

* AAD debe configurarse para que acepte el URI de redirección del agente.

#### La aplicación integra ADAL, pero no admite la aplicación AAD Authenticator.

* La autoridad debe establecerse en el entorno deseado donde se han configurado las cuentas de AAD.

* El Id. de cliente se debe establecer en el identificador de cliente de la aplicación.

* `NonBrokerRedirectURI` debe establecerse en un URI de redireccionamiento válido de la aplicación.

    * Or `urn:ietf:wg:oauth:2.0:oob` debería configurarse como un URI de redirección de AAD válido.

## Cómo habilitar el registro en el SDK 

El registro se realiza a través del marco `java.util.logging` . Para recibir los registros, debe configurar el registro global tal como se describe en la [Guía técnica de Java](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html). Dependiendo de la aplicación, el elemento `App.onCreate` suele ser el mejor lugar para iniciar el registro. Tenga en cuenta que los mensajes de registro están organizados según el nombre de clase, el cual puede estar protegido.

# Limitaciones conocidas de la plataforma 

## Limitaciones del tamaño de archivo 

En Android, las limitaciones del formato de archivo ejecutable Dalvik pueden ser un problema para grandes bases de códigos que se ejecutan sin ProGuard. En concreto, pueden producirse las siguientes limitaciones: 

* Límite de 65.000 en campos.

* Límite de 65.000 en métodos.

Cuando se incluyen muchos proyectos, cada paquete de Android recibirá una copia de “R” que aumentará considerablemente el número de campos a medida que se agregan bibliotecas. Las recomendaciones siguientes pueden ayudarle a suavizar esta limitación:
 
* Todos los proyectos de biblioteca deberían compartir el mismo paquete de Android siempre que sea posible. Esta solución no le fallará de forma esporádica en el campo, ya que este es básicamente un problema de tiempo de compilación.   Asimismo, las versiones más recientes del SDK de Android procesarán de antemano los archivos DEX para eliminar parte de la redundancia. Gracias a ello, reducirá la distancia de los campos aún más.

* Use las herramientas que tiene disponibles en la compilación del SDK de Android más reciente.

* Quite todas las bibliotecas innecesarias y que no use (por ejemplo, `android.support.v4`)

## Limitaciones de cumplimiento de directivas

**Captura de pantalla**: el SDK no puede aplicar un nuevo valor de configuración de la captura de pantalla en aquellas actividades que ya hayan pasado por Activity.onCreate. Esto puede dar lugar a un período de tiempo en el cual la aplicación se configuró para deshabilitar las capturas de pantalla, pero aún así, todavía se pueden tomar capturas de pantalla.

**Usar solucionadores de contenido*: la directiva de transferencia o recepción puede bloquear (o bloquear parcialmente) el uso de un solucionador de contenido para acceder al proveedor de contenido de otra aplicación. Esto hará que los métodos de ContentResolver devuelvan un valor nulo o creen un valor de error (por ejemplo, `openOutputStream` creará el valor `FileNotFoundException` si se bloquea). La aplicación puede determinar si fue la directiva quien produjo un error al escribir los datos a través de un solucionador de contenido, cuando realizó la siguiente llamada:

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**Servicios exportados**: el archivo `AndroidManifest.xml` que se incluye en el SDK para aplicaciones de Intune contiene el elemento `MAMNotificationReceiverService`; este elemento debe ser un servicio exportado para permitir que el Portal de empresa envíe notificaciones a una aplicación habilitada. El servicio comprueba quién fue el autor de la llamada para asegurarse de que solo el Portal de empresa tiene permiso para enviar notificaciones. 

# Procedimientos recomendados de Android 

El SDK de Intune mantiene el contrato proporcionado por la API de Android, aunque se pueden desencadenar condiciones de error con más frecuencia como resultado de la aplicación de directivas. Gracias a estas prácticas recomendadas, Android reducirá la probabilidad de que se produzcan errores: 

* Las funciones del SDK de Android que podrían devolver el valor “null” tienen una mayor probabilidad de ser nulas.  Para minimizar los problemas, asegúrese de los valores que pueden ser “null” se encuentran en los lugares adecuados.

* Todas aquellas características que se pueden comprobar deben, por supuesto, comprobarse a través de sus API del SDK.

* Las funciones derivadas deben llamar a través de sus versiones de superclase.

* Evite usar cualquier API de manera ambigua. Por ejemplo, no use `Activity.startActivityForResult/onActivityResult` sin comprobar antes si requestCode creará un comportamiento extraño.


<!--HONumber=May16_HO2-->


