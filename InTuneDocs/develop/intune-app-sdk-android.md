---
title: "Guía para desarrolladores acerca del SDK de aplicaciones de Microsoft Intune para Android | Microsoft Docs"
description: "El SDK de la aplicación Microsoft Intune para Android le permite incorporar la administración de aplicaciones móviles (MAM) de Intune en su aplicación Android."
keywords: SDK
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 905be6a926dc5bab8e9b1016ba82751ee47313e5
ms.openlocfilehash: 178fbaeb1d3235a81cb4da49b7a955f6999c49a2
ms.lasthandoff: 02/18/2017


---


# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune

> [!NOTE]
> Es posible que quiera leer primero la [Información general del SDK para aplicaciones de Intune](intune-app-sdk.md), que cubre las características actuales del SDK y describe cómo preparar la integración en cada plataforma compatible.

El SDK de la aplicación Microsoft Intune para Android le permite incorporar la administración de aplicaciones móviles (MAM) de Intune en su aplicación Android. Una aplicación con MAM es aquella que está integrada con Intune App SDK. Permite a los administradores de TI implementar directivas en la aplicación móvil cuando Intune administra activamente la aplicación.

## <a name="whats-in-the-sdk"></a>Qué hay en el SDK

El SDK para aplicaciones de Intune para Android es una biblioteca de Android estándar que no tiene dependencias externas. El SDK consta de:  

* **Microsoft.Intune.MAM.SDK.jar**: las interfaces necesarias para habilitar MAM y la interoperabilidad con la aplicación Portal de empresa de Intune. Las aplicaciones deben especificarla como una referencia a la biblioteca Android.

* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: las interfaces necesarias para habilitar MAM en aplicaciones que usan la biblioteca de compatibilidad de Android v4. Las aplicaciones que necesiten este tipo de compatibilidad deben hacer referencia al archivo JAR directamente.

* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: las interfaces necesarias para habilitar MAM en aplicaciones que usan la biblioteca de compatibilidad de Android v7. Las aplicaciones que necesiten este tipo de compatibilidad deben hacer referencia al archivo JAR directamente.

* **El directorio de recursos**: se compone de los recursos (como cadenas) en los que se basa el SDK.

* **Microsoft.Intune.MAM.SDK.aar**: los componentes del SDK, excepto los archivos JAR Support.V4 y Support.V7. Puede usar este archivo en lugar de los componentes individuales, si el sistema de compilación admite archivos AAR.

* **AndroidManifest.xml**: los puntos de entrada adicionales y los requisitos de la biblioteca.

* **THIRDPARTYNOTICES. TXT**: es un aviso de atribución que reconoce el código de terceros o de OSS que se compilará en la aplicación.

## <a name="requirements"></a>Requisitos

El SDK para aplicaciones de Intune es un proyecto de Android compilado. Como resultado, no se ve para nada afectado por la versión de Android que usa la aplicación para sus versiones de API mínima o de destino. El SDK admite las API de la 14 a la 24 de Android (Android 4.0 +).

La aplicación [Portal de empresa](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) debe estar presente en el dispositivo para que el SDK para aplicaciones de Intune para Android pueda habilitar las directivas MAM. En MAM sin inscripción de dispositivo, *no* es necesario que el usuario inscriba el dispositivo con la aplicación Portal de empresa.


## <a name="how-the-intune-app-sdk-works"></a>Cómo funciona el SDK para aplicaciones de Intune

###<a name="entry-points"></a>Puntos de entrada

Para que el SDK para aplicaciones de Intune pueda habilitar las directivas de administración de aplicaciones de Intune, es necesario realizar algunos cambios en el código fuente de una aplicación. Para ello, se reemplazan las clases base de Android por las clases base de Intune equivalentes, cuyos nombres tienen el prefijo `MAM`. Las clases del SDK son un término medio entre las clases base de Android y la versión derivada que la propia aplicación tiene de esas clases. Si usamos una actividad a modo de ejemplo, terminará con una jerarquía de herencia que tendrá el siguiente aspecto: `Activity` > `MAMActivity` > `AppSpecificActivity`.

Por ejemplo, cuando `AppSpecificActivity` interactúa con su elemento primario (por ejemplo, al llamar a `super.onCreate()`), `MAMActivity` es la superclase.

Las aplicaciones Android habituales tienen un modo único y pueden acceder al sistema mediante su [contexto](https://developer.android.com/reference/android/content/Context.html). Por otro lado, las aplicaciones que han incorporado el SDK para aplicaciones de Intune tienen dos modos. Estas aplicaciones siguen teniendo acceso al sistema a través del objeto `Context`. En función de la `Activity` usada, es Android quien proporciona el objeto `Context` o este se dividirá de manera inteligente entre una vista restringida del sistema y el `Context` proporcionado por Android.

Cuando un [punto de entrada](https://developer.android.com/guide/components/fundamentals.html) se reemplaza por su equivalente MAM, se debe usar la versión MAM del ciclo de vida del punto de entrada (a excepción de la clase `MAMApplication`).

Por ejemplo, al derivar desde `MAMActivity`, en lugar de reemplazar `onCreate` y llamar a `super.onCreate`, `Activity` debe reemplazar a `onMAMCreate` y llamar a `super.onMAMCreate`. Esto permite que Intune restringa el lanzamiento de `Activity` (entre otros) en ciertos casos.


###<a name="sdk-permissions"></a>Permisos de SDK

El SDK para aplicaciones de Intune requiere tres [permisos del sistema de Android](https://developer.android.com/guide/topics/security/permissions.html) sobre las aplicaciones que lo integran:

* `android.permission.GET_ACCOUNTS` (solicitada en tiempo de ejecución si es necesario)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

La biblioteca de autenticación de Azure Active Directory ([ADAL](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/)) requiere estos permisos para realizar autenticación negociada. Si estos permisos no se conceden a la aplicación o el usuario los revoca, se deshabilitará el flujo de autenticación que necesita el agente (la aplicación de Portal de empresa).


###<a name="company-portal-app"></a>Aplicación de portal de empresa

¿Por qué es necesaria la aplicación de Portal de empresa? Cuando la aplicación Portal de empresa está instalada en el dispositivo y ha recuperado una directiva de restricción de aplicaciones para el usuario del servicio de Intune, los puntos de entrada del SDK se inicializan de forma asincrónica. La inicialización solo se requiere cuando Android crea inicialmente el proceso. Durante la inicialización, se establece una conexión con la aplicación Portal de empresa y se recupera la directiva desde la aplicación.  

> [!NOTE]
> Cuando la aplicación de Portal de empresa no está en el dispositivo, no se alterará el comportamiento de la aplicación habilitada para Intune, sino que se comportará como una aplicación normal.


## <a name="how-to-integrate-with-the-intune-app-sdk"></a>Cómo realizar integraciones con el SDK para aplicaciones de Intune

Tal como se indicó antes, para que el SDK pueda habilitar las directivas de administración de aplicaciones, es necesario realizar algunos cambios en el código fuente de la aplicación. Estos son los pasos necesarios para habilitar MAM en la aplicación.

### <a name="replace-classes-methods-and-activities-with-their-mam-equivalent-required"></a>Reemplace las clases, los métodos y las actividades por su equivalente MAM (obligatorio)

Las clases base de Android se deben reemplazar por sus equivalentes MAM. Para ello, busque todas las instancias de las clases enumeradas en la tabla siguiente y reemplácelas por el SDK para aplicaciones de Intune equivalente.

| Clase base Android | Sustitución del SDK para aplicaciones de Intune |
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
| android.app.PendingIntent | MAMPendingIntent* |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | MAMBinder (solo es necesario si el enlazador no se genera desde una interfaz de lenguaje de definición de interfaz Android [AIDL]) |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |


**Microsoft.Intune.MAM.SDK.Suppot.v4.jar**:

| MAM de Intune de clase Android | Sustitución del SDK para aplicaciones de Intune |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider

**Microsoft.Intune.MAM.SDK.Suppot.v7.jar**:

|Clase de Android | Sustitución del SDK para aplicaciones de Intune |
|--|--|
|android.support.v7.app.ActionBarActivity | MAMActionBarActivity |

>[!NOTE]
>Recuerde que cuando un [punto de entrada](https://developer.android.com/guide/components/fundamentals.html) se reemplaza por su equivalente MAM, se debe usar la versión MAM del ciclo de vida del punto de entrada (a excepción de la clase `MAMApplication`).
>
>Por ejemplo, al derivar desde `MAMActivity`, en lugar de reemplazar `onCreate` y llamar a `super.onCreate`, `Activity` debe reemplazar a `onMAMCreate` y llamar a `super.onMAMCreate`. Esto permite que Intune restringa el lanzamiento de `Activity` (entre otros) en ciertos casos.

#### <a name="pendingintent-classes-and-renamed-methods"></a>Clases PendingIntent y métodos renombrados

Una vez que hace una derivación desde uno de los puntos de entrada de MAM, es seguro usar `Context` como lo haría habitualmente; por ejemplo, iniciando las clases `Activity` y usando `PackageManager`.  

Las clases `PendingIntent` son una excepción a esta regla. Cuando llame a este tipo de clases, debe cambiar el nombre de la clase. Por ejemplo, en lugar de `PendingIntent.get*`, debe usar el método `MAMPendingIntent.get*`. Después de esto, puede usar la clase `PendingIntent` del modo habitual.

En algunos casos, un método que se encuentra en la clase Android se marca como final de la clase de reemplazo MAM. En este caso, la clase de reemplazo MAM proporciona un método con un nombre similar (generalmente lleva el sufijo `MAM`) que se debería reemplazar en su lugar. Por ejemplo, en lugar de reemplazar `ContentProvider.query`, debe reemplazar `MAMContentProvider.queryMAM`. El compilador de Java debe encargarse de aplicar las restricciones necesarias para evitar que se reemplace por accidente el método original en lugar del equivalente MAM.

###<a name="enable-features-that-require-app-participation"></a>Habilitar características que requieren la participación de la aplicación

El SDK no puede implementar algunas directivas por sí mismo. La aplicación puede controlar su comportamiento para lograr estas características mediante el uso de varias API que puede encontrar en la siguiente interfaz `AppPolicy`.

```
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * <strong>This function is now deprecated. Please use {@link #getIsSaveToLocationAllowed(SaveLocation, String)} instead</strong>
 * @return True if the app is allowed to save to personal data stores; false otherwise.
 */
@Deprecated
boolean getIsSaveToPersonalAllowed();

/**
 * Check if policy prohibits saving to a content provider location.
 *
 * @param location
 *            a content URI to check
 * @return True if location is not a content URI or if policy does not prohibit saving to the content location.
 */
boolean getIsSaveToLocationAllowed(Uri location);

/**
 * Determines if the SaveLocation passed in can be saved to by the username associated with the cloud service.
 *
 * @param service
 *           see {@link SaveLocation}.
 * @param username
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Whether the SDK PIN prompt is enabled for the app.
 *
 * @return True if the PIN is enabled. False otherwise.
 */
boolean getIsPinRequired();

/**
 * Whether the Intune Managed Browser is required to open web links.
 * @return True if the Managed Browser is required, false otherwise
 */
boolean getIsManagedBrowserRequired();

/**
 * Check if policy allows Contact sync to local contact list.
 *
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();


}

```

### <a name="enable-it-control-over-app-saving-behavior"></a>Habilitación del control de TI sobre el comportamiento de guardado de aplicaciones

Muchas aplicaciones implementan características que le permiten al usuario guardar archivos de forma local o en un servicio de almacenamiento en la nube. El SDK para aplicaciones de Intune ayuda a los administradores de TI a proteger los datos de filtraciones con restricciones de directivas en su organización, según lo consideren oportuno.  Una de las directivas que la TI puede controlar es si el usuario puede guardar en un almacén de datos "personal" no administrado. Esto incluye guardar datos en una ubicación local, en una tarjeta SD o en servicios de copia de seguridad de terceros.

Para poder habilitar esta característica, es necesaria la participación de la aplicación. Si la aplicación permite guardar datos directamente en ubicaciones personales o en la nube, debe implementar esta característica para garantizar que los administradores de TI puedan controlar los permisos para guardar datos en una ubicación.   

Para determinar si debe aplicar la directiva, la aplicación puede realizar la siguiente llamada. Esto permite que la aplicación sepa si la directiva de administración actual de Intune permite guardar en un almacén personal. Gracias a ello, la aplicación puede aplicar la directiva ya que sabe que el usuario puede guardar datos personales a través de ella.

```
MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();
```

> [!NOTE]
> `MAMComponents.get(AppPolicy.class)` siempre devolverá una directiva de aplicaciones no nula, aunque el dispositivo o la aplicación no estén dentro de una directiva de administración de Intune.

### <a name="let-the-app-detect-if-a-pin-policy-is-required"></a>Permitir que la aplicación detecte si se necesita una directiva de PIN

En el caso de algunas restricciones de aplicaciones de Intune, puede que desee inhabilitar algunas funciones con el fin de no duplicar la funcionalidad del SDK para aplicaciones de Intune. Por ejemplo, si la aplicación tiene su propia experiencia de usuario de PIN, puede inhabilitarla si el SDK está configurado para solicitar al usuario final que escriba un PIN.

Para determinar si una directiva de PIN de Intune está configurada para solicitar un PIN de aplicación al inicio, la aplicación puede realizar esta llamada:

```
MAMComponents.get(AppPolicy.class).getIsPinRequired();
```

### <a name="register-for-notifications-from-the-sdk"></a>Registrarse para recibir notificaciones del SDK  

El SDK para aplicaciones de Intune permite que la aplicación controle el comportamiento de determinadas directivas, como la eliminación selectiva, cuando las implemente el administrador de TI. Cuando un administrador de TI implementa esta directiva, el servicio de Intune envía una notificación al SDK.

La aplicación debe registrarse para recibir notificaciones del SDK mediante la creación de una clase `MAMNotificationReceiver` y su registro mediante `MAMNotificationReceiverRegistry`. Para ello, se proporcionan el receptor y el tipo de notificación deseada en `App.onCreate`, como se ilustra en el ejemplo:

```
@Override
public void onCreate() {
    super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class)
.registerReceiver(
                new ToastNotificationReceiver(),
MAMNotificationType.WIPE_USER_DATA);
    }
```

`MAMNotificationReceiver` simplemente recibe notificaciones del servicio de Intune. El SDK controla directamente algunas notificaciones. Otras notificaciones requieren la participación de la aplicación.

Una aplicación *debe* devolver los valores “true” o “false” desde una notificación. Recuerde que siempre debe devolver el valor "true" a menos que falle alguna acción realizada como consecuencia de la notificación. Este error se puede notificar al servicio de Intune. Un ejemplo de un escenario de notificación es si la aplicación no puede eliminar los datos de usuario después de que el administrador de TI inicia una eliminación.

Puede bloquear con seguridad el elemento `MAMNotificationReceiver.onReceive` porque su devolución de llamada no se ejecuta en el subproceso de la interfaz de usuario.

La siguiente interfaz `MAMNotificationReceiver` se define en el SDK:

```
/**
 * The SDK is signaling that a WG event has occurred.
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

```

###<a name="types-of-notifications"></a>Tipos de notificaciones

Las siguientes notificaciones se envían a la aplicación. Algunas de ellas podrían requerir participación de la aplicación.

* **`WIPE_USER_DATA`**: esta notificación se envía en una clase `MAMUserNotification`. Cuando se recibe esta notificación, se espera que la aplicación elimine todos los datos asociados con la identidad "corporativa" que pasa con la clase `MAMUserNotification`. Actualmente, esta notificación se envía durante la anulación de la inscripción del servicio de Intune. Normalmente, se especifica el nombre del usuario principal durante el proceso de inscripción. Si se registra para esta notificación, la aplicación debe asegurarse de que todos los datos de usuario se han eliminado. Si no se registra, la aplicación llevará a cabo de forma predeterminada el proceso de eliminación selectiva.

* **`WIPE_USER_AUXILIARY_DATA`**: las aplicaciones pueden registrarse para esta notificación si quieren que el SDK para aplicaciones de Intune realice el comportamiento predeterminado de eliminación selectiva, pero de todos modos les gustaría quitar algunos datos auxiliares cuando se produzca la eliminación.  

* **`REFRESH_POLICY`**: esta notificación se envía en una clase `MAMUserNotification`. Cuando se recibe esta notificación, cualquier directiva de Intune en caché debe ser invalidada y actualizada. Generalmente, es el SDK el que controla esta tarea. Pero la aplicación deberá controlar esta tarea si la directiva se usa de manera persistente.



### <a name="protection-of-backup-data"></a>Protección de datos de copia de seguridad

En lo referente a la versión Android Marshmallow (API 23), el sistema Android tiene dos formas para que una aplicación pueda hacer una copia de seguridad de sus datos. Cada opción está disponible para la aplicación y requiere pasos diferentes para garantizar que la protección de datos de Intune está correctamente implementada. Lea más acerca de los métodos de copia de seguridad en la [guía de API de Android](http://developer.android.com/guide/topics/data/backup.html).

#### <a name="automatic-backup-for-apps"></a>Copia de seguridad automática de aplicaciones

Android comenzó a ofrecer [copias de seguridad completas automática](https://developer.android.com/guide/topics/data/autobackup.html) a aplicaciones de dispositivos Android Marshmallow, con independencia de la API de destino de la aplicación. Si establece explícitamente `android:allowBackup` en "false" en el archivo AndroidManifest.xml, Android nunca podrá en cola la aplicación para realizar copias de seguridad y los datos "corporativos" permanecerán dentro de la aplicación. En este caso, no se necesita ninguna acción.

De manera predeterminada, el atributo `android:allowBackup` se establece en true, incluso si `android:allowBackup` no se especifica en el archivo de manifiesto. Esto significa que todos los datos de la aplicación se copian automáticamente en la cuenta de Google Drive del usuario, un comportamiento predeterminado que plantea un *riesgo de pérdida de datos*. El SDK requiere los cambios siguientes para garantizar que se aplique la protección de datos. Si quiere que su aplicación se ejecute en dispositivos de Android Marshmallow, es importante seguir estas directrices para proteger los datos del cliente de la manera adecuada.  

Si no ha escrito un agente de copia de seguridad para crear una copia de seguridad de la aplicación con `MAMBackupAgent` o `MAMBackupAgentHelper`, debe tener en cuenta y controlar cómo se cargarán los datos de la aplicación mediante la copia de seguridad automática. Intune le permite usar todas las [características de copia de seguridad automática](https://developer.android.com/guide/topics/data/autobackup.html) disponibles en Android, como la posibilidad de definir reglas personalizadas en XML. Sin embargo, debe seguir estos pasos para ayudar a proteger los datos:

1. Use el valor predeterminado de `MAMBackupAgent` para permitir copias de seguridad completas automáticas que sean compatibles con la directiva de Intune. Coloque `android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"` en el manifiesto de aplicación.

2. Cuando decida qué tipo de copia de seguridad completa debe recibir la aplicación (sin filtrar, filtrada o ninguna), establezca el atributo `android:fullBackupContent` en true, en false o en un recurso XML de la aplicación. Copie todo lo que se pone en `android:fullBackupContent` en una etiqueta de metadatos denominada `com.microsoft.intune.mam.FullBackupContent`.

    Por ejemplo, si desea que la aplicación tenga copias de seguridad completas de acuerdo con sus reglas personalizadas en un archivo XML, proporcione un recurso en la etiqueta de metadatos `com.microsoft.intune.mam.FullBackupContent` en su manifiesto, similar a lo siguiente:
    ```
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```



#### <a name="keyvalue-backup"></a>Copia de seguridad de tipo clave-valor

La opción de copia de seguridad de tipo clave-valor está disponible para todas las API y usa los elementos `BackupAgentHelper` y `BackupAgent`.

##### <a name="backupagenthelper"></a>BackupAgentHelper

`BackupAgentHelper` es mucho más fácil de implementar que `BackupAgent`, tanto en términos de funcionalidad nativa de Android como en cuanto a la integración de MAM. `BackupAgentHelper` le permite registrar archivos completos y preferencias compartidas en `FileBackupHelper` o `SharedPreferencesBackupHelper`, respectivamente. Luego se pueden agregar a `BackupAgentHelper` después de la creación.

##### <a name="backupagent"></a>BackupAgent

`BackupAgent` le permite ser mucho más explícito acerca de los datos sobre los cuales desea hacer una copia de seguridad. Sin embargo, con esta opción no podrá aprovechar el marco de trabajo de copia de seguridad que le ofrece Android. Como realizar una implementación supone un grado de responsabilidad, deberá dar más pasos para garantizar la protección de datos de MAM. Como la mayoría del trabajo lo realizará usted como desarrollador, la integración de MAM le puede resultar ligeramente más complicada.

###### <a name="app-does-not-have-a-backup-agent"></a>La aplicación no tiene un agente de copia de seguridad

Estas son las opciones que encontrará el desarrollador cuando se establece `android:allowBackup =true`.

####### <a name="full-backup-according-to-a-configuration-file"></a>Copia de seguridad completa según un archivo de configuración

Proporcione un recurso en la etiqueta de metadatos `com.microsoft.intune.mam.FullBackupContent` del manifiesto. Por ejemplo:     `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

Agregue el siguiente atributo en la etiqueta `<application>` : `android:fullBackupContent="@xml/my_scheme"`, donde `my_scheme` es un recurso XML de su aplicación.

####### <a name="full-backup-without-exclusions"></a>Copia de seguridad completa sin exclusiones

Proporcione una etiqueta en el manifiesto, como `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />`.

Agregue el siguiente atributo en la etiqueta `<application>`: `android:fullBackupContent="true"`.

###### <a name="app-has-a-backup-agent"></a>La aplicación tiene un agente de copia de seguridad

Siga las recomendaciones mencionadas anteriormente en esta guía para `BackupAgent` y `BackupAgentHelper`.

Considere la posibilidad de usar `MAMDefaultFullBackupAgent`, que proporciona copias de seguridad sencillas en Android Marshmallow.

##### <a name="before-your-backup"></a>Antes de hacer la copia de seguridad

Antes de comenzar con la copia de seguridad, debe comprobar de que realmente puede realizar copias de seguridad de los búferes de archivos o de datos. Le dimos una función `isBackupAllowed` en `MAMFileProtectionManager` y `MAMDataProtectionManager` para comprobar esto. Si no puede hacer la copia de seguridad del búfer de datos o de archivos, no debe intentar seguir usándolo en la copia de seguridad.

Si quiere realizar una copia de seguridad de las identidades de los archivos que registró en el paso 1 mientras realiza la copia de seguridad, debe llamar a `backupMAMFileIdentity(BackupDataOutput data, File … files)` con los archivos de los que planea extraer datos. Esto creará automáticamente nuevas entidades de copia de seguridad y las escribirá en `BackupDataOutput`. Estas entidades se consumirán automáticamente durante la restauración.

#### <a name="azure-directory-authentication-library-setup"></a>Configuración de la Biblioteca de autenticación de Azure Directory  

El SDK se basa en ADAL para sus escenarios de inicio condicional y de autenticación. Estos escenarios requieren que las aplicaciones tengan ciertos elementos de configuración de Azure Active Directory (Azure AD). Los valores de configuración se comunican con el SDK mediante los metadatos de `AndroidManifest` .

Para configurar la aplicación y habilitar la autenticación correcta, agregue los datos siguientes en el nodo de la aplicación en `AndroidManifest`. Algunas de estas configuraciones se requieren solo si la aplicación usar ADAL para la autenticación en general. En ese caso, necesitará los valores específicos que la aplicación usó para registrarse en Azure AD. Esto asegura que no se le solicitará al usuario la autenticación por duplicado, debido a que Azure AD reconoce dos valores de registro independientes: uno de la aplicación y otro del SDK.

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

##### <a name="common-adal-configurations"></a>Opciones de configuración comunes de ADAL

La siguiente configuración detalla opciones comunes referentes a los valores que se explicaron anteriormente.

###### <a name="app-does-not-integrate-adal"></a>La aplicación no integra ADAL

* La autoridad se debe establecer en el entorno deseado donde se configuraron las cuentas de Azure AD.

* SkipBroker debe establecerse en “true”.

###### <a name="app-integrates-adal"></a>La aplicación integra ADAL

* La autoridad se debe establecer en el entorno deseado donde se configuraron las cuentas de Azure AD.

* El Id. de cliente se debe establecer en el identificador de cliente de la aplicación.

* `NonBrokerRedirectURI` debería establecerse como un URI de redirección válido de la aplicación. O bien, `urn:ietf:wg:oauth:2.0:oob` debe establecerse como un URI de redireccionamiento de Azure AD válido.

* SkipBroker debe establecerse con el valor "false" (o estar ausente).

* Azure AD debe configurarse para que acepte el URI de redireccionamiento del agente.

###### <a name="app-integrates-adal-but-does-not-support-the-azure-ad-authenticator-app"></a>La aplicación se integra con ADAL, pero no admite la aplicación Azure AD Authenticator

* La autoridad se debe establecer en el entorno deseado donde se configuraron las cuentas de Azure AD.

* El Id. de cliente se debe establecer en el identificador de cliente de la aplicación.

* `NonBrokerRedirectURI` debe establecerse como un URI de redirección válido de la aplicación. O bien, `urn:ietf:wg:oauth:2.0:oob` debe establecerse como un URI de redireccionamiento de Azure AD válido.

#### <a name="logging-in-the-sdk"></a>Registro en el SDK

El registro se realiza a través del marco `java.util.logging` . Para recibir los registros, debe configurar el registro global tal como se describe en la [Guía técnica de Java](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html). Dependiendo de la aplicación, el elemento `App.onCreate` suele ser el mejor lugar para iniciar el registro. Tenga en cuenta que los mensajes de registro están organizados según el nombre de clase, el cual puede estar oculto.

###<a name="multi-identity"></a>Varias identidades

De forma predeterminada, el SDK para aplicaciones de Intune aplicará una directiva a la aplicación en su conjunto. La característica de varias identidades es una característica MAM que puede habilitar para aplicar una directiva en un nivel por identidad. Para ello es necesaria más participación en la aplicación que otras características de MAM. La aplicación debe informar al SDK de la aplicación cuando intente cambiar la identidad activa. El SDK también deberá notificar a la aplicación cuando se requiera un cambio de identidad.

Actualmente, solo se admite una identidad administrada. Una vez que el usuario inscriba el dispositivo o la aplicación, el SDK usa esta identidad y la considera la identidad administrada principal. Los demás usuarios de la aplicación se tratan como usuarios no administrados con una configuración de directiva sin restricciones.

Tenga en cuenta que una identidad se define simplemente como una cadena. Las identidades no distinguen mayúsculas de minúsculas. Las solicitudes al SDK podrían no devolverse con el mismo uso de mayúsculas y minúsculas que se empleó originalmente al establecer la identidad.

####<a name="enabling-multi-identity"></a>Habilitar varias identidades

De forma predeterminada, se considera que todas las aplicaciones son de una única identidad. Una aplicación declara que es compatible con varias identidades colocando los siguientes metadatos en el manifiesto de Android.

```
<meta-data
            android:name="com.microsoft.intune.mam.MAMMultiIdentity"
            android:value="true" />
```
####<a name="setting-the-identity"></a>Definición de la identidad

Puede establecer la identidad de la aplicación en los niveles siguientes:

1. Nivel de proceso

2. Nivel de contexto (generalmente `Activity`)

3. Nivel de subproceso

Una identidad que se establece en el nivel de subproceso sustituye a una identidad que se establece en el nivel `Context`, la cual reemplaza a una identidad que se establece en el nivel de proceso. Una identidad establecida en `Context` solo se usa cuando corresponde. Las tareas de E/S de archivos, por ejemplo, no tienen un `Context` asociado. Puede usar los métodos siguientes en `MAMPolicyManager` para establecer la identidad y recuperar los valores de identidad previamente establecidos.

```
public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

public static String getUIPolicyIdentity(final Context context);

public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

public static String getProcessIdentity();

public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

public static String getCurrentThreadIdentity();

/**
 * Get the currently applicable app policy. Same as MAMComponents.get(AppPolicy.class). This method does
    not take the context identity into account.
 */
public static AppPolicy getPolicy();

/**
 * Get the currently applicable app policy, taking the context
 * identity into account.
 */
public static AppPolicy getPolicy(final Context context);


public static AppPolicy getPolicyForIdentity(final String identity);

public static boolean getIsIdentityManaged(final String identity);

```
También puede borrar la identidad de la aplicación si la establece en null. La cadena vacía se puede usar como una identidad que nunca tendrá restricciones. Todos los métodos para establecer la identidad devuelven valores de resultado mediante ``` MAMIdentitySwitchResult```. Pueden devolverse cuatro valores:

* **SUCCEEDED**: el cambio de la identidad se realizó correctamente.

* **NOT_ALLOWED**: no se permite el cambio de identidad. Esto sucederá si se intenta cambiar a otro usuario corporativo que pertenece a la misma empresa que el usuario inscrito. También sucederá si se intenta establecer la identidad de la interfaz de usuario (`Context`) cuando hay una identidad diferente establecida en el subproceso actual.

* **CANCELLED**: el usuario canceló el cambio de identidad, por lo general eligiendo el botón Atrás en un mensaje de autenticación o solicitud del PIN.

* **FAILED**: no se pudo realizar el cambio de identidad por una razón específica.

En el caso de establecer una identidad `Context`, el resultado se notifica de forma asincrónica. Si `Context` es una clase `Activity`, no se sabrá si el cambio de identidad se realizó correctamente hasta después de realizar el inicio condicional. Un inicio condicional puede requerir que el usuario escriba un PIN o sus credenciales corporativas completas. Se espera que la aplicación implemente ```MAMSetUIIdentityCallback``` para recibir este resultado, aunque es admisible pasar null para este parámetro.

```
public interface MAMSetUIIdentityCallback {
    void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
}
```

También puede establecer la identidad de una actividad directamente a través de un método en `MAMActivity` en lugar de llamar a ```MAMPolicyManager.setUIPolicyIdentity```. Para ello, use el método siguiente:

 ```public final void switchMAMIdentity(final String newIdentity);```

Las aplicaciones también pueden reemplazar un método en `MAMActivity` para que se les notifique el resultado de los intentos de cambiar la identidad de esa actividad.

```public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);```

> [!NOTE]
> Puede que cambiar la identidad requiera volver a crear la actividad. En este caso, la devolución de llamada ```onSwitchMAMIdentityComplete``` se entregará a la nueva instancia de la actividad.


####<a name="implicit-identity-changes"></a>Cambios de identidad implícitos

Además de la posibilidad de que la aplicación establezca la identidad, un subproceso o la identidad de un contexto pueden cambiar en función de la entrada de datos desde otra aplicación habilitada para MAM. Por ejemplo, si una actividad se inicia desde una clase `Intent` enviado desde otra aplicación MAM, la identidad de la actividad se establecerá en función de la identidad efectiva de la otra aplicación en el punto en que se envió la clase `Intent`.

En el caso de los servicios, la identidad del subproceso se establecerá de forma similar para la duración de una llamada `onStart` o `onBind`. Las llamadas a `Binder` devueltas por `onBind` también establecerán temporalmente la identidad del subproceso. Las llamadas a ```ContentProvider``` establecerán de forma similar la identidad del subproceso a lo largo de su duración.

Además, la interacción del usuario con una actividad puede provocar un cambio de identidad implícita. Por ejemplo, la cancelación por un usuario de un mensaje de autorización durante ```Resume``` dará como resultado un cambio implícito a una identidad vacía.
La aplicación tiene la oportunidad de enterarse de esos cambios y, en algunos casos, de prohibirlos si es necesario. ```MAMService``` y ```MAMContentProvider``` exponen el siguiente método cuyas subclases pueden reemplazar:

```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
```
En el caso de ```MAMActivity```, existe un parámetro adicional en el método:
```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
```
La parte ```AppIdentitySwitchReason``` captura el origen del cambio implícito. Puede aceptar los valores ```CREATE```, ```RESUME_CANCELLED``` y ```NEW_INTENT```.  La razón de ```RESUME_CANCELLED``` se usa cuando la reanudación de la actividad provoca que se muestren el PIN, la autenticación u otra IU compatible y el usuario intenta cancelar esa IU, por lo general mediante el uso del botón Atrás.
```AppIdentitySwitchResultCallback``` es así:
```
public interface AppIdentitySwitchResultCallback {
    /**
     * @param result
     *            whether the identity switch can proceed.
     */
    void reportIdentitySwitchResult(AppIdentitySwitchResult result);
}
```
```AppIdentitySwitchResult``` es ```SUCCESS``` o ```FAILURE```.

Al método ```onMAMIdentitySwitchRequired``` se le llama para todos los cambios de identidad implícitos, excepto aquellos realizados a través de una clase `Binder` devuelta desde ```MAMService.onMAMBind```. La implementación predeterminada de ```onMAMIdentitySwitchRequired``` llama inmediatamente a ```reportIdentitySwitchResult(FAILURE)``` cuando la razón es ```RESUME_CANCELLED``` y ```reportIdentitySwitchResult(SUCCESS)``` en todos los demás casos.

La mayoría de las aplicaciones probablemente no tendrán que bloquear ni retrasar un cambio de identidad de una manera diferente. Sin embargo, en caso de que una aplicación necesite hacerlo, debe considerar los siguientes puntos:

* Si se bloquea un cambio de identidad, el resultado es el mismo que si la configuración de uso compartido ```Receive``` hubiera prohibido la entrada de datos.

* Si un servicio se ejecuta en el subproceso principal, se *debe* llamar a ```reportIdentitySwitchResult``` de forma sincrónica o se bloqueará el subproceso de IU.

* Para la creación de ```Activity```, se llamará a ```onMAMIdentitySwitchRequired``` antes que a ```onMAMCreate```. Si la aplicación debe mostrar IU para comprobar si se permite el cambio de identidad, esa IU se debe mostrar mediante una actividad diferente.

* En ```Activity```, cuando se solicita un cambio a la identidad vacía con el motivo ```RESUME_CANCELLED```, la aplicación debe cambiar la actividad reanudada para mostrar datos coherentes con ese cambio de identidad. Si esto no es posible, la aplicación debe rechazar el cambio. Además, se volverá a pedir al usuario que cumpla con la directiva de reanudar la identidad (por ejemplo, con la presentación de la pantalla de entrada del PIN).

> [!NOTE]
> Una aplicación de varias identidades siempre recibirá datos de entrada de aplicaciones tanto administradas como sin administrar. La aplicación es responsable de tratar los datos de identidades administradas de forma administrada. Si una identidad solicitada es administrada por ```(MAMPolicyManager.getIsIdentityManaged)```, pero la aplicación no puede usar esa cuenta (por ejemplo, porque las cuentas, como las de correo electrónico, deben configurarse primero en la aplicación), se debe rechazar el cambio de identidad.

###<a name="file-protection"></a>Protección de archivos

Cada archivo tiene una identidad asociada en el momento de creación basada en la identidad del proceso y del subproceso. Esta identidad se usa para el cifrado de archivos y la eliminación selectiva. Solo se cifrarán los archivos cuya identidad tenga una directiva que requiera cifrado. La eliminación selectiva predeterminada del SDK solo eliminará los archivos asociados con la identidad para la que se ha solicitado una eliminación. La aplicación puede consultar o cambiar la identidad de un archivo mediante el uso de ```MAMFileProtectionManager```.
```
public final class MAMFileProtectionManager {

    /**
     * Protect a file. This will synchronously trigger whatever protection is required for the file, and will tag the file for
     * future protection changes.
     *
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     * @throws IOException
     *             If the file cannot be changed.
     */
    public static void protect(final File file, final String identity) throws IOException;

    /**
     * Get the protection info on a file.
     *
     * @param file
     *            File or directory to get information on.
     * @return File protection info, or null if there is no protection info.
     * @throws IOException
     *             If the file cannot be read or opened.
     */
    public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;
}

public interface MAMFileProtectionInfo {
String getIdentity();
}
```

> [!NOTE]
> El etiquetado de identidad de archivo es sensible al modo sin conexión. Debe tomar en cuenta los siguientes puntos:
> * Si no está instalada la aplicación Portal de empresa, no se puede etiquetar la identidad de los archivos.
>
> * Si la aplicación Portal de empresa está instalada, pero no tiene una directiva, no se puede etiquetar la identidad de los archivos de forma confiable.
>
> * Cuando esté disponible el etiquetado de identidad de los archivos, todos los archivos creados anteriormente se tratan como personales (que pertenecen a la identidad de cadena vacía), a menos que la aplicación se instalara anteriormente como una aplicación administrada de una única identidad. En ese caso, se tratan como pertenecientes al usuario inscrito.

####<a name="data-protection"></a>Protección de datos

No es posible etiquetar un archivo como perteneciente a varias identidades. Las aplicaciones que deben almacenar datos que pertenecen a distintos usuarios en el mismo archivo pueden hacerlo manualmente mediante las características que ```MAMDataProtectionManager``` proporciona. Esto permite que la aplicación cifre los datos y los asocie a un usuario determinado. Los datos cifrados son adecuados para almacenarse en disco en un archivo. Puede consultar los datos asociados con la identidad y descifrarlos más tarde.

```
public final class MAMDataProtectionManager {
    /**
     * Protect a stream. This will return a stream containing the protected
 * input.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect, read sequentially. This function
 *            will change the position of the stream but may not have
     *            read the entire stream by the time it returns. The
 *            returned stream will wrap this one. Calls to read on the
     *            returned stream may cause further reads on the original
 *            input stream. Callers should not expect to read directly
     *            from the input stream after passing it to this method.
 *            Calling close on the returned stream will close this one.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static InputStream protect(final InputStream input, final String identity);

    /**
     * Protect a byte array. This will return protected bytes.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static byte[] protect(final byte[] input, final String identity) throws IOException;

    /**
     * Unprotect a stream. This will return a stream containing the
 * unprotected input.
     *
     * @param input
     *            Input data to protect, read sequentially.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static InputStream unprotect(final InputStream input) throws IOException;

    /**
     * Unprotect a byte array. This will return unprotected bytes.
     *
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static byte[] unprotect(final byte[] input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input stream to get information on. Either this input
 *            stream must have been returned by a previous call to
      *            protect OR input.markSupported() must return true.
 *            Otherwise it will be impossible to get protection info
 *            without advancing the stream position. The stream must be
 *            positioned at the beginning of the protected data.
     * @return Data protection info, or null if there is no protection
 *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final InputStream input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input bytes to get information on. These must be bytes
 *            returned by a previous call to protect() or a copy of
 *            such bytes.
     * @return Data protection info, or null if there is no protection
 *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final byte[] input) throws IOException;
}
```
###<a name="content-providers"></a>Proveedores de contenido

Si la aplicación proporciona en potencia datos corporativos distintos de ```ParcelFileDescriptor``` a través de ```ContentProvider```, la aplicación debe llamar al método ```MAMContentProvider``` ```isProvideContentAllowed(String)``` pasando el propietario ```UPN``` del contenido. Si esta función devuelve false, puede que el contenido no se devuelva al autor de la llamada. Los descriptores de archivo devueltos a través de un proveedor de contenido se administran automáticamente en función de la identidad del archivo.

###<a name="selective-wipe"></a>La eliminación de datos selectiva

Si una aplicación se registra para recibir la notificación ```WIPE_USER_DATA```, no obtendrá el beneficio del comportamiento de eliminación selectiva predeterminada del SDK. En el caso de aplicaciones compatibles con varias identidades, esto puede tener un impacto más considerable dado que la eliminación selectiva predeterminada de MAM solo elimina los archivos que coinciden con la identidad que se va a eliminar.

Si compila una aplicación compatible con varias identidades, puede registrarse para ```WIPE_USER_AUXILIARY_DATA```. Esta notificación le permite aprovechar el comportamiento de eliminación predeterminada del SDK. Esta notificación se enviará inmediatamente antes de que realice la eliminación selectiva predeterminada del SDK. Tenga en cuenta que una aplicación nunca debe registrarse para ```WIPE_USER_DATA``` y ```WIPE_USER_AUXILIARY_DATA```.

### <a name="known-platform-limitations"></a>Limitaciones conocidas de la plataforma

#### <a name="file-size-limitations"></a>Limitaciones del tamaño de archivo

En Android, las limitaciones del formato de archivo ejecutable Dalvik podrían ser un problema para grandes bases de códigos que se ejecutan sin ProGuard. En concreto, podrían producirse las siguientes limitaciones:

* Límite de 65.000 en campos.

* Límite de 65.000 en métodos.

Cuando incluye muchos proyectos, cada `android:package` recibirá una copia de R. Esto aumentará considerablemente el número de campos a medida que se agregan bibliotecas. Las recomendaciones siguientes podrían ayudarle a suavizar esta limitación:

* Todos los proyectos de biblioteca deberían compartir el mismo `android:package` siempre que sea posible. Esta solución no presentará errores de forma esporádica en el campo, ya que este es básicamente un problema de tiempo de compilación. Asimismo, las versiones más recientes del SDK de Android procesarán de antemano los archivos DEX para eliminar parte de la redundancia. Gracias a ello, reducirá la distancia de los campos aún más.

* Use las herramientas que tiene disponibles en la compilación del SDK de Android más reciente.

* Quite todas las bibliotecas innecesarias y que no use (por ejemplo, `android.support.v4`).

#### <a name="policy-enforcement-limitations"></a>Limitaciones de cumplimiento de directivas

**Captura de pantalla**: el SDK no puede aplicar un nuevo valor de configuración de la captura de pantalla en las clases `Activity` que ya hayan pasado por `Activity.onCreate`. Esto puede dar lugar a un período de tiempo en el cual la aplicación se configuró para deshabilitar las capturas de pantalla, pero aún así, todavía se pueden tomar capturas de pantalla.

**Solucionadores de contenido**: la directiva de transferencia o recepción podría bloquear (o bloquear parcialmente) el uso de un solucionador de contenido para acceder al proveedor de contenido de otra aplicación. Esto hará que los métodos de `ContentResolver` devuelvan un valor nulo o creen un valor de error. (Por ejemplo, `openOutputStream` creará el valor `FileNotFoundException` si se bloquea). La aplicación puede hacer esta llamada para comprobar si una directiva provocó (o podría provocar) un error al escribir datos a través de un solucionador de contenido:

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**Servicios exportados**: el archivo `AndroidManifest.xml` que se incluye en el SDK para aplicaciones de Intune tiene el elemento `MAMNotificationReceiverService`. Este elemento debe ser un servicio exportado para permitir que la aplicación Portal de empresa envíe notificaciones a una aplicación habilitada. El servicio comprueba quién fue el autor de la llamada para asegurarse de que solo la aplicación Portal de empresa tiene permiso para enviar notificaciones.

### <a name="android-best-practices"></a>Procedimientos recomendados para contraseñas

El SDK de Intune mantiene el contrato proporcionado por la API de Android, aunque se podrían desencadenar condiciones de error con más frecuencia como resultado de la aplicación de directivas. Gracias a estas prácticas recomendadas, Android reducirá la probabilidad de que se produzcan errores:

* Las funciones del SDK de Android que podrían devolver el valor "null" tienen una mayor probabilidad de ser nulas. Para minimizar los problemas, asegúrese de los valores que pueden ser "null" se encuentran en los lugares adecuados.

* Si desea saber cuáles características puede comprobar, use sus API de SDK para hacerlo.

* Las funciones derivadas deben llamar a través de sus versiones de superclase.

* Evite usar cualquier API de manera ambigua. Por ejemplo, si usa `Activity.startActivityForResult/onActivityResult` sin comprobar `requestCode` se provocará un comportamiento extraño.

