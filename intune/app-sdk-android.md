---
title: "Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune"
description: "El SDK de la aplicación Microsoft Intune para Android le permite incorporar la administración de aplicaciones móviles (MAM) de Intune en su aplicación Android."
keywords: SDK
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a6e0ea5edc5a174e0400ccca3931323712f3cbbe
ms.sourcegitcommit: ce8a1f0f4e95444949556600d1837937b6efd769
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2017
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune

> [!NOTE]
> Es posible que quiera leer primero la [Información general del SDK para aplicaciones de Intune](app-sdk.md), que cubre las características actuales del SDK y describe cómo preparar la integración en cada plataforma compatible.

El SDK para aplicaciones de Microsoft Intune para Android permite incorporar directivas de aplicaciones de Intune (también conocidas como directivas MAM o **APP**) a la aplicación Android nativa. Una aplicación habilitada para Intune es aquella que está integrada con el SDK para aplicaciones de Intune. Los administradores de Intune pueden implementar fácilmente directivas de protección de aplicaciones en la aplicación habilitada para Intune cuando Intune la administra de manera activa.


## <a name="whats-in-the-sdk"></a>Qué hay en el SDK

El SDK para aplicaciones de Intune consta de los siguientes archivos:  

* **Microsoft.Intune.MAM.SDK.aar**: los componentes del SDK, excepto los archivos JAR Support.V4 y Support.V7. Puede usar este archivo en lugar de los componentes individuales, si el sistema de compilación admite archivos AAR.
* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: las interfaces necesarias para habilitar MAM en aplicaciones que usan la biblioteca de compatibilidad de Android v4. Las aplicaciones que necesiten este tipo de compatibilidad deben hacer referencia al archivo JAR directamente.
* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: las interfaces necesarias para habilitar MAM en aplicaciones que usan la biblioteca de compatibilidad de Android v7. Las aplicaciones que necesiten este tipo de compatibilidad deben hacer referencia al archivo JAR directamente.
* **proguard.txt**: contiene reglas de ProGuard que se debe aplicar si se compila con ProGuard.
* **CHANGELOG.txt**: proporciona un registro de los cambios hechos en cada versión del SDK.
* **THIRDPARTYNOTICES. TXT**: es un aviso de atribución que reconoce el código de terceros o de OSS que se compilará en la aplicación.

Si el sistema de compilación no admite archivos AAR, puede usar los archivos siguientes en lugar de Microsoft.Intune.MAM.SDK.aar.
* **Microsoft.Intune.MAM.SDK.jar**: las interfaces necesarias para habilitar MAM y la interoperabilidad con la aplicación Portal de empresa de Intune. Las aplicaciones deben especificarla como una referencia a la biblioteca Android.
* **El directorio res**: se compone de los recursos (como cadenas) en los que se basa el SDK.
* **AndroidManifest.xml**: los requisitos de biblioteca y los puntos de entrada.


## <a name="requirements"></a>Requisitos

El SDK para aplicaciones de Intune es un proyecto de Android compilado. Como resultado, no se ve para nada afectado por la versión de Android que usa la aplicación para sus versiones de API mínima o de destino. El SDK admite desde la API 14 (Android 4.0+) a la API 25 (Android 7.1) de Android.



### <a name="company-portal-app"></a>Aplicación de portal de empresa
La aplicación [Portal de empresa](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) debe estar presente en el dispositivo para que el SDK para aplicaciones de Intune para Android pueda habilitar las directivas de protección. El Portal de empresa recupera las directivas de protección de aplicaciones del servicio Intune. Cuando se inicializa la aplicación, carga la directiva y el código para aplicar dicha directiva desde el Portal de empresa.

> [!NOTE]
> Si la aplicación Portal de empresa no está en el dispositivo, una aplicación habilitada para Intune tiene el mismo comportamiento que una aplicación normal que no admite las directivas de protección de aplicaciones de Intune.

Para la protección de aplicaciones sin inscripción de dispositivo, _**no**_ es necesario que el usuario inscriba el dispositivo con la aplicación Portal de empresa.

## <a name="sdk-integration"></a>Integración del SDK

### <a name="build-integration"></a>Integración de compilación

El SDK para aplicaciones de Intune es una biblioteca de Android estándar que no tiene dependencias externas. **Microsoft.Intune.MAM.SDK.jar** contiene tanto las interfaces necesarias para la habilitación de una directiva de protección de aplicaciones como el código necesario para interoperar con la aplicación Portal de empresa de Microsoft Intune.

**Microsoft.Intune.MAM.SDK.jar** se debe especificar como una referencia a la biblioteca de Android. Para hacerlo, abra el proyecto de aplicación en Android Studio y vaya a **Archivo > Nuevo > Nuevo módulo** y seleccione **Importar paquete .JAR/.AAR**. Seleccione el paquete de archivos Android Microsoft.Intune.MAM.SDK.aar.

Además, **Microsoft.Intune.MAM.SDK.Support.v4** y **Microsoft.Intune.MAM.SDK.Support.v7** contienen variantes de Intune de `android.support.v4` y `android.support.v7`, respectivamente. No están integradas en Microsoft.Intune.MAM.SDK.aar en caso de que una aplicación no desee incluir las bibliotecas de compatibilidad. Son archivos JAR estándar en lugar de proyecto de biblioteca Android.

#### <a name="proguard"></a>ProGuard

Si [ProGuard](http://proguard.sourceforge.net/) (o cualquier otro mecanismo de reducción u ofuscación) se usa como paso de compilación, se deben excluir las clases del SDK de Intune. Para ProGuard, esto se puede lograr si se incluyen las reglas contenidas en el archivo proguard.txt que se distribuye con el SDK.

Las bibliotecas de autenticación de Azure Active Directory (ADAL) pueden tener sus propias restricciones de ProGuard. Si la aplicación integra ADAL, debe seguir la documentación de ADAL sobre estas restricciones.

### <a name="entry-points"></a>Puntos de entrada

La biblioteca de autenticación de Azure Active Directory ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) requiere estos permisos para realizar autenticación negociada. Si estos permisos no se conceden a la aplicación o el usuario los revoca, se deshabilitará el flujo de autenticación que necesita el agente (la aplicación de Portal de empresa).

Para que el SDK para aplicaciones de Intune pueda habilitar las directivas de protección de aplicaciones de Intune, es necesario realizar algunos cambios en el código fuente de una aplicación. Para ello, se reemplazan las clases base de Android por las clases base de Intune equivalentes, cuyos nombres tienen el prefijo **MAM**. Las clases del SDK son un término medio entre las clases base de Android y la versión derivada que la propia aplicación tiene de esas clases. Si usamos una actividad a modo de ejemplo, terminará con una jerarquía de herencia que tendrá el siguiente aspecto: `Activity` > `MAMActivity` > `AppSpecificActivity`.

Por ejemplo, cuando `AppSpecificActivity` interactúa con su elemento primario (por ejemplo, al llamar a `super.onCreate()`), `MAMActivity` es la superclase.

Las aplicaciones Android habituales tienen un modo único y pueden acceder al sistema mediante su objeto [**Context**](https://developer.android.com/reference/android/content/Context.html). Por otro lado, las aplicaciones que han integrado el SDK para aplicaciones de Intune tienen dos modos. Estas aplicaciones siguen teniendo acceso al sistema a través del objeto `Context`. En función de la `Activity` usada, es Android quien proporciona el objeto `Context` o este se dividirá de manera inteligente entre una vista restringida del sistema y el `Context` proporcionado por Android. Una vez que hace una derivación desde uno de los puntos de entrada de MAM, es seguro usar `Context` como lo haría habitualmente; por ejemplo, iniciando las clases `Activity` y usando `PackageManager`.


## <a name="replace-classes-methods-and-activities-with-their-mam-equivalent"></a>Reemplazo de las clases, los métodos y las actividades por su equivalente MAM

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
| android.app.PendingIntent | MAMPendingIntent (consulte las notas siguientes) |
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


### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar:

| MAM de Intune de clase Android | Sustitución del SDK para aplicaciones de Intune |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar:

|Clase de Android | Sustitución del SDK para aplicaciones de Intune |
|--|--|
|android.support.v7.app.ActionBarActivity | MAMActionBarActivity |


### <a name="renamed-methods"></a>Métodos renombrados


En muchos casos, un método que se encuentra en la clase Android se marca como final de la clase de reemplazo MAM. En este caso, la clase de reemplazo MAM proporciona un método con un nombre similar (generalmente lleva el sufijo `MAM`) que se debería reemplazar en su lugar. Por ejemplo, al derivar desde `MAMActivity`, en lugar de reemplazar `onCreate()` y llamar a `super.onCreate()`, `Activity` debe reemplazar a `onMAMCreate()` y llamar a `super.onMAMCreate()`. El compilador de Java debe encargarse de aplicar las restricciones necesarias para evitar que se reemplace por accidente el método original en lugar del equivalente MAM.

### <a name="pendingintent"></a>PendingIntent
En lugar de `PendingIntent.get*`, debe usar el método `MAMPendingIntent.get*`. Después de esto, puede usar la clase `PendingIntent` del modo habitual.

### <a name="manifest-replacements"></a>Reemplazos de manifiestos
Tenga en cuenta que es posible que sea necesario realizar algunos de los reemplazos de clases anteriores en el manifiesto así como también en el código Java. De especial interés:
* Las referencias de manifiesto a `android.support.v4.content.FileProvider` se deben reemplazar por `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`.
* Si la aplicación no necesita su propia clase Application derivada, se debe establecer `com.microsoft.intune.mam.client.app.MAMApplication` como el nombre de la clase Application que se usa en el manifiesto.

## <a name="sdk-permissions"></a>Permisos de SDK

El SDK para aplicaciones de Intune requiere tres [permisos del sistema de Android](https://developer.android.com/guide/topics/security/permissions.html) sobre las aplicaciones que lo integran:

* `android.permission.GET_ACCOUNTS` (solicitada en tiempo de ejecución si es necesario)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

La biblioteca de autenticación de Azure Active Directory ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) requiere estos permisos para realizar autenticación negociada. Si estos permisos no se conceden a la aplicación o el usuario los revoca, se deshabilitará el flujo de autenticación que necesita el agente (la aplicación de Portal de empresa).

## <a name="logging"></a>Registro

El registro se debe inicializar antes para aprovechar al máximo los datos registrados. `Application.onMAMCreate()` es típicamente el mejor lugar para inicializar el registro.

Para recibir registros MAM en la aplicación, cree un [controlador Java](http://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) y agréguelo a `MAMLogHandlerWrapper`. Esto invocará a `publish()` en el controlador de aplicación para cada mensaje de registro.

```java
/**
 * Global log handler that enables fine grained PII filtering within MAM logs.  
 *
 * To start using this you should build your own log handler and add it via
 * MAMComponents.get(MAMLogHandlerWrapper.class).addHandler(myHandler, false);  
 *
 * You may also remove the handler entirely via
 * MAMComponents.get(MAMLogHandlerWrapper.class).removeHandler(myHandler);
 */
public interface MAMLogHandlerWrapper {
    /**
     * Add a handler, PII can be toggled.
     *
     * @param handler handler to add.
     * @param wantsPII if PII is desired in the logs.    
     */
    void addHandler(final Handler handler, final boolean wantsPII);

    /**
     * Remove a handler.
     *
     * @param handler handler to remove.
     */
    void removeHandler(final Handler handler);
}
```



## <a name="enable-features-that-require-app-participation"></a>Habilitar características que requieren la participación de la aplicación

Existen varias directivas de protección de la aplicación que el SDK no puede implementar por sí mismo. La aplicación puede controlar su comportamiento para lograr estas características mediante el uso de varias API que puede encontrar en la siguiente interfaz `AppPolicy`. Para recuperar una instancia de `AppPolicy`, use `MAMPolicyManager.getPolicy`.

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * This function is now deprecated. Please use getIsSaveToLocationAllowed(SaveLocation, String) instead
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
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between
 *           the AAD username and the cloud service username does not exist or the username is not known.
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

> [!NOTE]
> `MAMPolicyManager.getPolicy` siempre devolverá una directiva de aplicaciones no nula, aunque el dispositivo o la aplicación no estén dentro de una directiva de administración de Intune.

### <a name="example-determine-if-pin-is-required-for-the-app"></a>Ejemplo: determine si se requiere un PIN para la aplicación

Si la aplicación tiene su propia experiencia de usuario de PIN, es posible que desee deshabilitarla si el administrador de TI configuró el SDK para solicitar un PIN de aplicación. Con el fin de determinar si el administrador de TI implementó la directiva de PIN de esta aplicación para el usuario final actual, llame al método siguiente:

```java
MAMComponents.get(AppPolicy.class).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>Ejemplo: determine el usuario primario de Intune

Además de las API expuestas en AppPolicy, el nombre principal de usuario (**UPN**) también lo expone la API `getPrimaryUser()` definida dentro de la interfaz `MAMUserInfo`. Para obtener el UPN, llame a lo siguiente:

```java
MAMUserInfo info = MAMComponents.get(MAMUserInfo.class);
if (info != null) return info.getPrimaryUser();
```

La definición completa de la interfaz MAMUserInfo es la siguiente:

```java
/**
 * External facing user informations.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if the device is not enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>Ejemplo: determine si se permite guardar en un dispositivo o en almacenamiento en nube

Muchas aplicaciones implementan características que permiten al usuario final guardar archivos de forma local o en un servicio de almacenamiento en la nube. El SDK para aplicaciones de Intune permite a los administradores de TI proteger contra la pérdida de datos mediante la aplicación de restricciones de directivas en su organización, según lo consideren oportuno.  Una de las directivas que pueden controlar es si el usuario final puede guardar en un almacén de datos personal no administrado. Esto incluye guardar datos en una ubicación local, en una tarjeta SD o en servicios de copia de seguridad de terceros.

**Para poder habilitar esta característica, es necesaria la participación de la aplicación.** Si la aplicación permite guardar datos directamente en ubicaciones personales o en la nube, debe implementar esta característica para garantizar que los administradores de TI puedan controlar los permisos para guardar datos en una ubicación. La siguiente API permite a la aplicación saber si está permitido guardar datos en un almacén personal, según la directiva del administrador de Intune actual. Gracias a ello, la aplicación puede aplicar la directiva ya que “sabe” que el usuario final puede guardar datos personales a través de ella.  

Para determinar si se debe aplicar la directiva, haga la siguiente llamada:

```java
MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

... donde `service` es uno de los siguientes valores SaveLocations:


    * SaveLocation.ONEDRIVE_FOR_BUSINESS
    * SaveLocation.LOCAL
    * SaveLocation.SHAREPOINT

El método anterior para determinar si la directiva de un usuario le permite guardar datos en diversas ubicaciones era `getIsSaveToPersonalAllowed()` dentro de la misma **AppPolicy**. Esta función está **en desuso** y no se debe usar; la invocación siguiente equivale a `getIsSaveToPersonalAllowed()`:

```java

MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, userNameInQuestion);
```

>[!NOTE]
> Use `SaveLocation.OTHER` si la ubicación en cuestión no aparece en la enumeración **SaveLocations**.


## <a name="register-for-notifications-from-the-sdk"></a>Registrarse para recibir notificaciones del SDK

### <a name="overview"></a>Información general
El SDK para aplicaciones de Intune permite que la aplicación controle el comportamiento de determinadas directivas, como la eliminación selectiva, cuando las implemente el administrador de TI. Cuando un administrador de TI implementa esta directiva, el servicio de Intune envía una notificación al SDK.

La aplicación debe registrarse para recibir notificaciones del SDK mediante la creación de `MAMNotificationReceiver` y su registro mediante `MAMNotificationReceiverRegistry`. Para ello, se proporcionan el receptor y el tipo de notificación deseada en `App.onCreate`, como se ilustra en el ejemplo siguiente:

```java
@Override
public void onCreate() {
    super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class)
        .registerReceiver(
            new ToastNotificationReceiver(),
            MAMNotificationType.WIPE_USER_DATA);
    }
```

### <a name="mamnotificationreceiver"></a>MAMNotificationReceiver

La interfaz `MAMNotificationReceiver` simplemente recibe notificaciones del servicio de Intune. Algunas notificaciones se administran directamente mediante el SDK y otras requieren la participación de la aplicación. Una aplicación **debe** devolver los valores “true” o “false” desde una notificación. Recuerde que siempre debe devolver el valor “true” a menos que falle alguna acción realizada como consecuencia de la notificación.

* Este error se puede notificar al servicio de Intune. Un ejemplo de un escenario de notificación es si la aplicación no puede eliminar los datos de usuario después de que el administrador de TI inicia una eliminación.

>[!NOTE]
> Puede bloquear con seguridad el elemento `MAMNotificationReceiver.onReceive` porque su devolución de llamada no se ejecuta en el subproceso de la interfaz de usuario.

La interfaz `MAMNotificationReceiver` tal como se define en el SDK se incluye a continuación:

```java
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

```

### <a name="types-of-notifications"></a>Tipos de notificaciones

Las siguientes notificaciones se envían a la aplicación y es posible que algunas de ellas necesiten que participe la aplicación:

* **WIPE_USER_DATA**: esta notificación se envía en una clase `MAMUserNotification`. Cuando se recibe esta notificación, se espera que la aplicación elimine todos los datos asociados con la identidad "corporativa" que pasa con `MAMUserNotification`. Actualmente, esta notificación se envía durante la anulación de la inscripción del servicio APP-WE. Normalmente, se especifica el nombre del usuario principal durante el proceso de inscripción. Si se registra para esta notificación, la aplicación debe asegurarse de que todos los datos de usuario se han eliminado. Si no se registra, se llevará a cabo de forma predeterminada el proceso de eliminación selectiva.

* **WIPE_USER_AUXILIARY_DATA**: las aplicaciones pueden registrarse para esta notificación si quieren que el SDK para aplicaciones de Intune realice el comportamiento predeterminado de eliminación selectiva, pero les gustaría quitar algunos datos auxiliares cuando se produzca la eliminación.

* **REFRESH_POLICY**: esta notificación se envía en `MAMUserNotification`. Cuando se recibe esta notificación, cualquier directiva de Intune en caché debe ser invalidada y actualizada. Para ello normalmente se utiliza el SDK; sin embargo, debería gestionarse con la aplicación si la directiva se utiliza de forma constante.

* **MANAGEMENT_REMOVED**: esta notificación se envía en `MAMUserNotification` e informa a la aplicación que está a punto de dejar de estar administrada. Cuando deja de estar administrada, ya no podrá leer archivos cifrados, leer datos cifrados con MAMDataProtectionManager, interactuar con el portapapeles cifrado o participar de cualquier otro modo en el ecosistema de aplicaciones administradas.


> [!NOTE]
> Una aplicación nunca debe registrarse para recibir notificaciones `WIPE_USER_DATA` y `WIPE_USER_AUXILIARY_DATA`.


## <a name="configure-azure-active-directory-authentication-library-adal"></a>Configurar Azure Active Directory Authentication Library (ADAL)

En primer lugar, lea las guías de integración de ADAL que se encuentran en el [repositorio de ADAL en GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-android).

El SDK se basa en [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) para sus escenarios de inicio condicional y [autenticación](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/), que requieren que las aplicaciones se configuren con [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). Los valores de configuración se comunican con el SDK mediante los metadatos de AndroidManifest.

Para configurar la aplicación y habilitar la autenticación correcta, agregue los datos siguientes en el nodo de la aplicación en el elemento AndroidManifest.xml. Algunas de estas opciones de configuración solo son necesarias si la aplicación usa ADAL para la autenticación en general; en ese caso, necesitará los valores específicos que su aplicación usa para registrarse con AAD. Esto se hace para garantizar de que no se le solicita la autenticación por duplicado al usuario final, ya que tenga en cuenta que AAD debe reconocer dos valores de registro independientes: uno de la aplicación y otro del SDK.

```xml
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
```

### <a name="adal-metadata"></a>Metadatos de ADAL

* **Authority** es la autoridad de AAD actual en uso. Si está presente, debe usar su propio entorno donde se hayan configurado cuentas de AAD. Si este valor está ausente, se usa un valor predeterminado de Intune.

* **ClientID** es el identificador de cliente de AAD que se usará. Debe usar el ClientID de su propia aplicación si se registró con Azure AD. Si este valor está ausente, se usa un valor predeterminado de Intune.

* **NonBrokerRedirectURI** es el URI de direccionamiento de AAD para usar en casos sin agente. Si no se especifica ninguno, se usa el valor predeterminado de `urn:ietf:wg:oauth:2.0:oob`. Este valor predeterminado es adecuado para la mayoría de las aplicaciones.

* **SkipBroker** se usa si ClientID no está configurado para usar el URI de redireccionamiento del agente. El valor predeterminado es "false".
    * En el caso de las aplicaciones que **no integran ADAL** y **no quieren participar en SSO/autenticación intermediada en todo el dispositivo**, el valor debe estar establecido en "true". Si este valor está establecido en "true", el único URI de redireccionamiento que se usará es NonBrokerRedirectURI.

    * Para las aplicaciones que sí admiten la intermediación de SSO en todo el dispositivo, el valor debe ser "false". Cuando el valor es "false", el SDK seleccionará un agente entre el resultado de [`com.microsoft.aad.adal.AuthenticationContext.getRedirectUriForBroker()`](https://github.com/AzureAD/azure-activedirectory-library-for-android) y NonBrokerRedirectURI, según la disponibilidad del agente en el sistema. En general, el agente estará disponible en la aplicación Portal de empresa o en la aplicación Azure Authenticator.

### <a name="common-adal-configurations"></a>Opciones de configuración comunes de ADAL

A continuación se describen las maneras comunes en que se puede configurar una aplicación con ADAL. Busque la configuración de la aplicación y asegúrese de establecer los parámetros de metadatos de ADAL (que se explicaron anteriormente) en los valores necesarios.

1. **La aplicación no integra ADAL:**

    | Parámetro obligatorio de ADAL | Valor |
    |--|--|
    | Autoridad | Entorno deseado donde se configuraron las cuentas de AAD |
    | SkipBroker | True |

2. **La aplicación integra ADAL:**

    |Parámetro obligatorio de ADAL| Valor |
    |--|--|
    | Autoridad | Entorno deseado donde se configuraron las cuentas de AAD |
    | ClientID | ClientID de la aplicación (que Azure AD genera cuando se registra la aplicación) |
    | NonBrokerRedirectURI | Identificador URI de redireccionamiento válido para la aplicación o `urn:ietf:wg:oauth:2.0:oob` de manera predeterminada. <br><br> Asegúrese de configurar el valor como un identificador URI de redireccionamiento aceptable para ClientID de la aplicación.
    | SkipBroker | False |


3. **La aplicación integra ADAL pero no admite la autenticación intermediada/SSO en todo el dispositivo:**

    |Parámetro obligatorio de ADAL| Valor |
    |--|--|
    | Autoridad | Entorno deseado donde se configuraron las cuentas de AAD |
    | ClientID | ClientID de la aplicación (que Azure AD genera cuando se registra la aplicación) |
    | NonBrokerRedirectURI | Identificador URI de redireccionamiento válido para la aplicación o `urn:ietf:wg:oauth:2.0:oob` de manera predeterminada. <br><br> Asegúrese de configurar el valor como un identificador URI de redireccionamiento aceptable para ClientID de la aplicación.
    | SkipBroker | **True** |

## <a name="app-protection-policy-without-device-enrollment"></a>Directiva de protección de aplicaciones sin la inscripción de dispositivos

### <a name="overview"></a>Información general
La directiva de protección de aplicaciones de Intune sin inscripción de dispositivos, también conocida como APP-WE o MAM-WE, permite a las aplicaciones ser administradas mediante Intune sin necesidad de que el dispositivo esté inscrito en MDM de Intune. APP-WE funciona con o sin inscripción de dispositivos. De todos modos, es necesario que Portal de empresa esté instalado en el dispositivo, pero no es necesario que el usuario inicie sesión en él e inscriba el dispositivo.

> [!NOTE]
> Todas las aplicaciones deben admitir la directiva de protección de aplicaciones sin la inscripción de dispositivos.

### <a name="workflow"></a>Flujo de trabajo

Cuando una aplicación crea una cuenta de usuario, debe registrarla su administración con el SDK para aplicaciones de Intune. El SDK controlará los detalles de la inscripción de la aplicación en el servicio APP-WE; si es necesario, reintente las inscripciones a intervalos adecuados si se producen errores.

La aplicación también puede consultar el SDK para aplicaciones de Intune para conocer el estado de un usuario registrado a fin de determinar si se le debe bloquear el acceso a contenido corporativo. Puede haber varias cuentas registradas para administración, pero actualmente solo puede haber una cuenta activamente inscrita con el servicio APP-WE a la vez. Esto significa que solo una cuenta en la aplicación puede recibir la dirección de protección de aplicaciones a la vez.

La aplicación debe proporcionar una devolución de llamada para adquirir el token de acceso adecuado desde la biblioteca de autenticación de Azure Active Directory (ADAL) en nombre del SDK. Se da por supuesto que la aplicación ya usa ADAL para la autenticación del usuario y adquirir sus propios tokens de acceso.

Cuando la aplicación quita completamente una cuenta, debe anular el registro de esa cuenta para indicar que la aplicación ya no aplica la directiva en ese usuario. Si el usuario estaba inscrito en el servicio MAM, se anulará su inscripción y se borrará la aplicación.


### <a name="overview-of-app-requirements"></a>Información general sobre los requisitos de la aplicación

Para implementar la integración de APP-WE, la aplicación debe registrar la cuenta de usuario con el SDK de MAM:

1. La aplicación _debe_ implementar y registrar una instancia de la interfaz `MAMServiceAuthenticationCallback`. La instancia de devolución de llamada se debe registrar tan pronto como sea posible en el ciclo de vida la aplicación (habitualmente en el método `onMAMCreate()` de la clase de aplicación).

2. Cuando se crea una cuenta de usuario y el usuario inicia sesión correctamente con ADAL, la aplicación _debe_ llamar a `registerAccountForMAM()`.

3. Cuando una cuenta de usuario se quita completamente, la aplicación debe llamar a `unregisterAccountForMAM()` para quitar la cuenta de la administración de Intune.

    > [!NOTE]
    > Si un usuario cierra temporalmente la sesión de la aplicación, esta no necesita llamar a `unregisterAccountForMAM()`. La llamada puede iniciar una eliminación para quitar completamente los datos corporativos del usuario.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

Todas las API de autenticación y registro necesarias se pueden encontrar en la interfaz `MAMEnrollmentManager`. Se puede obtener una referencia a `MAMEnrollmentManager` de la manera siguiente:

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr

```

Se garantiza que la instancia `MAMEnrollmentManager` devuelta no será nula. Los métodos de API se dividen en dos categorías: **autenticación** y **registro de cuenta**.

> [!NOTE]
> `MAMEnrollmentManager` contiene algunos métodos de API que pronto quedarán en desuso. Para mayor claridad, en el bloque de código siguiente solo se muestran los códigos de resultado y los métodos pertinentes.

```java
package com.microsoft.intune.mam.policy;

public interface MAMEnrollmentManager {
    public enum Result {
        AUTHORIZATION_NEEDED,
        NOT_LICENSED,
        ENROLLMENT_SUCCEEDED,
        ENROLLMENT_FAILED,
        WRONG_USER,
        MDM_ENROLLED,
        UNENROLLMENT_SUCCEEDED,
        UNENROLLMENT_FAILED,
        PENDING,
        COMPANY_PORTAL_REQUIRED;
    }

    //Authentication methods
    interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
    }
    void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
    void updateToken(String upn, String aadId, String resourceId, String token);

    //Registration methods
    void registerAccountForMAM(String upn, String aadId, String tenantId);
    void unregisterAccountForMAM(String upn);
    Result getRegisteredAccountStatus(String upn);
}
```

### <a name="account-authentication"></a>Autenticación de cuenta

En esta sección se describen los métodos de API de autenticación en `MAMEnrollmentManager` y cómo usarlos.

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. La aplicación debe implementar la interfaz `MAMServiceAuthenticationCallback` para permitir que el SDK solicite un token ADAL para el identificador de recurso y usuario determinado. La instancia de devolución de llamada se debe proporcionar a `MAMEnrollmentManager` llamando a su método `registerAuthenticationCallback()`. Es posible que se necesite un token en una etapa muy temprana del ciclo de vida de la aplicación para reintentar la inscripción o para las protecciones de actualización de las directivas de protección de aplicaciones, por lo que el lugar ideal para registrar la devolución de llamada está en el método `onMAMCreate()` de la subclase `MAMApplication` de la aplicación.

2. El método `acquireToken()` debe adquirir el token de acceso para el identificador de recurso solicitado del usuario determinado. Si no puede adquirir el token solicitado, debe devolver un valor nulo.

3. En aso de que la aplicación no pueda proporcionar un token cuando el SDK llama a `acquireToken()`, por ejemplo, si la autenticación silenciosa genera un error y no es un momento adecuado para mostrar una interfaz e usuario, la aplicación puede proporcionar un token más adelante llamando al método `updateToken()`. El mismo identificador de recurso, identificador de AAD y UPN que solicitó la llamada anterior a `acquireToken()` se deben transmitir a `updateToken()`, junto con el token que se adquirió al final. La aplicación debe llamar a este método tan pronto como sea posible después de devolver un valor nulo a partir de la devolución de llamada proporcionada.

> [!NOTE]
> El SDK llamará a `acquireToken()` de forma periódica para obtener el token, por lo que no es estrictamente necesario llamar a `updateToken()`. Sin embargo, se recomienda ya que puede ayudar a que los registros de las directivas de protección de aplicaciones y las inscripciones se completen de manera oportuna.


### <a name="account-registration"></a>Registro de la cuenta

En esta sección se describen los métodos de API para el registro de la cuenta en `MAMEnrollmentManager` y cómo usarlos.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. Para registrar una cuenta para administración, la aplicación debe llamar a `registerAccountForMAM()`. Una cuenta de usuario se identifica mediante su UPN y su identificador de usuario de AAD. El identificador de inquilino también es obligatorio para asociar los datos de inscripción con el inquilino de AAD del usuario. El SDK puede intentar inscribir la aplicación del usuario en cuestión en el servicio MAM; si se produce un error en la inscripción, se reintentará periódicamente hasta que se anule el registro de la cuenta. El período de reintento suele ser de 12 a 24 horas. El SDK proporciona el estado de los intentos de inscripción de manera asincrónica a través de las notificaciones.

2. Como se requiere la autenticación de AAD, el mejor momento para registrar la cuenta de usuario es después de que el usuario inició sesión en la aplicación y se autenticó correctamente con ADAL.
    * El identificador de inquilino y el inquilino de AAD del usuario se devuelven de la llamada de autenticación de ADAL como parte del objeto [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android). El identificador de inquilino proviene del método `AuthenticationResult.getTenantID()`.
    * La información sobre el usuario se encuentra en un objeto secundario de tipo `UserInfo` que proviene de `AuthenticationResult.getUserInfo()`, mientras que el identificador de usuario de AAD se recupera desde ese objeto llamando a `UserInfo.getUserId()`.

3. Para anular el registro de una cuenta desde la administración de Intune, la aplicación debe llamar a `unregisterAccountForMAM()`. Si la cuenta se registró correctamente y está administrada, el SDK anulará la inscripción de la cuenta y borrará sus datos. Se detendrán los reintentos de inscripción periódicos de la cuenta. El SDK proporciona el estado de la solicitud no inscrita de manera asincrónica a través de las notificaciones.

### <a name="important-implementation-notes"></a>Notas de implementación importantes

#### <a name="authentication"></a>Autenticación

* Cuando la aplicación llama a `registerAccountForMAM()`, puede recibir una devolución de llamada en su interfaz `MAMServiceAuthenticationCallback` poco después, en un subproceso distinto. Idealmente, la aplicación adquirió su propio token desde ADAL antes de registrar la cuenta para acelerar la adquisición del **token MAMService**. Si la aplicación devuelve un token válido desde la devolución de llamada, la inscripción seguirá y la aplicación obtendrá el resultado final a través de una notificación.

* Si la aplicación no devuelve un token AAD válido, el resultado final del intento de inscripción será `AUTHENTICATION_NEEDED`. Si la aplicación recibe este resultado a través de una notificación, puede acelerar el proceso de inscripción mediante la adquisición del **token MAMService** y llamando al método `updateToken()` para volver a iniciar el proceso de inscripción. Sin embargo, este _no_ es un requisito firme, dado que el SDK reintenta periódicamente la inscripción e invoca la devolución de llamada para adquirir el token.

* También se llamará al elemento `MAMServiceAuthenticationCallback` registrado de la aplicación para adquirir un token para los registros periódicos de actualizaciones de las directivas de protección de aplicaciones. Si la aplicación no puede proporcionar un token cuando se solicita, no recibirá una notificación sino que tendrá que intentar adquirir un token y llamar a `updateToken()` en el próximo momento conveniente para acelerar el proceso de registro. Si no se proporciona un token, de todos modos se realizará la devolución de llamada en el próximo intento de registro.

#### <a name="registration"></a>Registro

* Para mayor comodidad, los métodos de registro son idempotentes; por ejemplo, `registerAccountForMAM()` solo registrará una cuenta e intentará inscribir la aplicación si la cuenta todavía no está registrada y `unregisterAccountForMAM()` solo anulará el registro de una cuenta si está registrada actualmente. Las llamadas subsiguientes no son operativas, por lo que no afecta llamar a estos métodos más de una vez. Adicionalmente, la correspondencia entre las llamadas a estos métodos y las notificaciones de los resultados no se garantizan; es decir, si se llama a `registerAccountForMAM` para una identidad que ya está registrada, es posible que no se envíe nuevamente la notificación para esa identidad. Es posible que las notificaciones que se envíen no correspondan a ninguna llamada a estos métodos, dado que el SDK puede intentar inscripciones de forma periódica en segundo plano, y las anulaciones de las inscripciones se puede desencadenar debido a las solicitudes de eliminación que se reciben desde el servicio Intune.

* Los métodos de registro se pueden llamar para cualquier número de identidades distintas, pero actualmente solo se puede inscribir correctamente una cuenta de usuario. Si varias cuentas de usuario con licencia de Intune a las que se aplica la directiva de protección de aplicaciones se registran casi al mismo tiempo, no hay garantía de cuál será la primera.

* Por último, puede consultar `MAMEnrollmentManager` para ver si una cuenta determinada esta registrada y para obtener su estado actual con el método `getRegisteredAccountStatus`. Si la cuenta proporcionada no está registrada, este método devolverá un valor **nulo**. Si la cuenta está registrada, este método devolverá el estado de la cuenta como uno de los miembros de la enumeración `MAMEnrollmentManager.Result`.

### <a name="result-and-status-codes"></a>Códigos de estado y resultado

La primera vez que se registra una cuenta, comienza con el estado `PENDING`, lo que indica que el intento de inscripción del servicio MAM inicial no está completo. Cuando finaliza el intento de inscripción, se enviará una notificación con uno de los códigos de resultado de la tabla a continuación. Además, el método `getRegisteredAccountStatus()` devolverá el estado de la cuenta para que la aplicación pueda determinar siempre si el acceso a contenido corporativo está bloqueado para ese usuario. Si hay un error en el intento de inscripción, el estado de la cuenta podría cambiar en el tiempo a medida que el SDK reintenta la inscripción en segundo plano.

|Código de resultado | Explicación |
| -- | -- |
|AUTHORIZATION_NEEDED | Este resultado indica que la instancia `MAMServiceAuthenticationCallback` registrada de la aplicación no proporcionó ningún token, o bien que el token que se proporcionó no era válido.  La aplicación debe adquirir un token válido y llamar a `updateToken()` si es posible. |
| NOT_LICENSED | El usuario no cuenta con licencia para Intune, o bien se produjo un error al intentar ponerse en contacto con el servicio MAM de Intune.  La aplicación debe continuar con un estado no administrado (normal) y no se debe bloquear el usuario.  Las inscripciones se reintentarán periódicamente ante la eventualidad de que el usuario obtenga una licencia en el futuro. |
| ENROLLMENT_SUCCEEDED | El intento de inscripción se completó con éxito, o bien el usuario ya está inscrito.  En caso de que se trate de una inscripción correcta, se enviará una notificación de actualización de política antes de esta notificación.  Se debe permitir el acceso a los datos corporativos. |
| ENROLLMENT_FAILED | Error al intentar la inscripción.  Puede encontrar más detalles en los registros del dispositivo.  En este estado, la aplicación no debe permitir el acceso a los datos corporativos, ya que anteriormente se determinó que el usuario no tiene licencia para Intune.|
| WRONG_USER | Solo un usuario por dispositivo puede inscribir una aplicación con el servicio MAM.  Con el fin de inscribirse correctamente como un usuario distinto, las aplicaciones inscritas primero tienen que anular su inscripción.  De lo contrario, esta aplicación se debe inscribir como el usuario primario.  Esta comprobación se realiza después de la comprobación de la licencia, con el fin de bloquear el acceso del usuario a los datos corporativos hasta que la aplicación se inscriba correctamente.|
| UNENROLLMENT_SUCCEEDED | La anulación de inscripción se realizó correctamente.|
| UNENROLLMENT_FAILED | Error en la solicitud de anulación de inscripción.  Puede encontrar más detalles en los registros del dispositivo. |
| PENDING | El intento de inscripción inicial para el usuario está en curso.  La aplicación puede bloquear el acceso a los datos corporativos hasta que se conozca el resultado de la inscripción, pero no es necesario que lo haga. |
| COMPANY_PORTAL_REQUIRED | El usuario cuenta con una licencia para Intune, pero no se puede inscribir la aplicación hasta que se instale Portal de empresa en el dispositivo. El SDK para aplicaciones de Intune intentará bloquear el acceso del usuario en cuestión a la aplicación e indicarle que instale la aplicación Portal de empresa (consulte los detalles a continuación). |


### <a name="company-portal-requirement-prompt-override-optional"></a>Invalidación de avisos del requisito de Portal de empresa (opcional)

Si se recibe el resultado `COMPANY_PORTAL_REQUIRED`, el SDK bloqueará el uso de las actividades que usan la identidad para la que se solicitó la inscripción. En su lugar, el SDK hará que esas actividades muestren un aviso para descargar Portal de empresa. Si desea evitar este comportamiento en la aplicación, las actividades pueden implementar `MAMActivity.onMAMCompanyPortalRequired`.

Se llama a este método antes de que el SDK muestre la interfaz de usuario de bloqueo predeterminada. Si la aplicación cambia la identidad de la actividad o anula el registro del usuario que intentó la inscripción, el SDK no bloqueará la actividad. En esta situación, es tarea de la aplicación evitar la pérdida de los datos corporativos.

### <a name="notifications"></a>Notificaciones

Se agregó un nuevo tipo de `MAMNotification` para informar a la aplicación que se completó la solicitud de inscripción.  `MAMEnrollmentNotification` se recibirá a través de la interfaz `MAMNotificationReceiver`, tal como se describe en la sección [Registrarse para recibir notificaciones del SDK](#register-for-notifications-from-the-sdk).

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}

```

El método `getEnrollmentResult()` devuelve el resultado de la solicitud de inscripción.  Como `MAMEnrollmentNotification` extiende `MAMUserNotification`, también está disponible la identidad del usuario para quien se intentó la inscripción. La aplicación debe implementar la interfaz `MAMNotificationReceiver` para recibir estas notificaciones, lo que se detalla en la sección [Registrarse para recibir notificaciones del SDK](#Register-for-notifications-from-the-SDK).

El estado de la cuenta de usuario registrada puede cambiar cuando se recibe una notificación de inscripción, pero no se modificará en algunos casos (por ejemplo, si la notificación `AUTHORIZATION_NEEDED` se recibe después de un resultado mucho más informativo como `WRONG_USER`, el resultado más informativo se conservará como el estado de la cuenta)


## <a name="protecting-backup-data"></a>Proteger los datos de copia de seguridad

En lo referente a la versión Android Marshmallow (API 23), el sistema Android tiene dos formas para que una aplicación pueda hacer una copia de seguridad de sus datos. Cada opción está disponible para la aplicación y requiere pasos diferentes para garantizar que la protección de datos de Intune está correctamente implementada. Puede revisar la siguiente tabla sobre las acciones correspondientes necesarias para el comportamiento de protección de datos correcto.  Lea más acerca de los métodos de copia de seguridad en la [guía de API de Android](http://developer.android.com/guide/topics/data/backup.html).

### <a name="auto-backup-for-apps"></a>Copia de seguridad automática de aplicaciones

Android comenzó a ofrecer [copias de seguridad completas automática](https://developer.android.com/guide/topics/data/autobackup.html) a Google Drive para aplicaciones en dispositivos Android Marshmallow, con independencia de la API de destino de la aplicación. En el archivo AndroidManifest.xml, si establece explícitamente `android:allowBackup` a **false**, la aplicación nunca se pondrán en cola para las copias de seguridad de Android y los datos "corporativos" permanecerán dentro de la aplicación. En este caso, no se necesita ninguna acción.

Sin embargo, de forma predeterminada el atributo `android:allowBackup` se establece en true, incluso si `android:allowBackup` no se especifica en el archivo de manifiesto. Esto significa que todos los datos de la aplicación se copian automáticamente en la cuenta de Google Drive del usuario, un comportamiento predeterminado que plantea un **riesgo de pérdida de datos**. Por lo tanto, el SDK requiere los cambios que se describen a continuación para tener la seguridad de que se aplica la protección de datos.  Si quiere que su aplicación se ejecute en dispositivos de Android Marshmallow, es importante seguir las directrices que se indican a continuación para proteger los datos del cliente de la manera adecuada.  

Intune le permite utilizar todas las [características de copia de seguridad automática](https://developer.android.com/guide/topics/data/autobackup.html) disponibles en Android, como la posibilidad de definir reglas personalizadas en XML, pero debe seguir los pasos siguientes para proteger los datos:

1. Si la aplicación **no** usa su propio BackupAgent, use el valor predeterminado de MAMBackupAgent para permitir copias de seguridad completas automáticas que sean compatibles con la directiva de Intune. Si lo hace, puede omitir el atributo de manifiesto `android:fullBackupOnly`, puesto que no se aplica al agente de copia de seguridad. Coloque lo siguiente en el manifiesto de aplicación:

    ```xml
android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```


2. **[Opcional]** Si implementó un BackupAgent personalizado opcional, debe asegurarse de usar MAMBackupAgent o MAMBackupAgentHelper. Consulte las secciones siguientes. Considere la posibilidad de usar el elemento **MAMDefaultFullBackupAgent** de Intune (que se describe en el paso 1), que proporciona copias de seguridad sencillas en Android M y versiones superiores.

3. Cuando decida qué tipo de copia de seguridad completa debe recibir la aplicación (sin filtrar, filtrada o ninguna), deberá establecer el atributo `android:fullBackupContent`  en true, en false o en un recurso XML de la aplicación.

4. Luego, _**debe**_ copiar todo lo que se pone en `android:fullBackupContent` en una etiqueta de metadatos denominada `com.microsoft.intune.mam.FullBackupContent` en el manifiesto.

    **Ejemplo 1**: si desea que la aplicación tenga copias de seguridad completas sin exclusiones, establezca el atributo `android:fullBackupContent` y la etiqueta de metadatos `com.microsoft.intune.mam.FullBackupContent` en **true**:

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **Ejemplo 2**: si desea que la aplicación use su propio BackupAgent personalizado y no haga copias de seguridad automáticas completas que sean compatibles con la directiva de Intune, debe establecer el atributo y la etiqueta de metadatos en **false**:

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    **Ejemplo 3**: si desea que la aplicación tenga copias de seguridad completas según las reglas personalizadas definidas en un archivo XML, establezca el atributo y la etiqueta de metadatos en el mismo recurso XML:

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```


### <a name="keyvalue-backup"></a>Copia de seguridad de tipo "key/value"

La opción [Copia de seguridad de tipo clave-valor](https://developer.android.com/guide/topics/data/keyvaluebackup.html) está disponible para las más de 8 API y carga los datos de aplicación en el [Servicio de copia de seguridad de Android](https://developer.android.com/google/backup/index.html). La cantidad de datos por usuario de la aplicación está limitada a 5 MB. Si usa Copia de seguridad de tipo clave-valor, debe usar **BackupAgentHelper** o **BackupAgent**.

### <a name="backupagenthelper"></a>BackupAgentHelper

BackupAgentHelper es más fácil de implementar que BackupAgent tanto en términos de funcionalidad nativa de Android como en cuanto a la integración de MAM de Intune. BackupAgentHelper permite al desarrollar registrar archivos enteros y preferencias compartidas en **FileBackupHelper** y **SharedPreferencesBackupHelper** (respectivamente), los cuales se agregan posteriormente a BackupAgentHelper tras su creación. Siga los pasos siguientes para usar BackupAgentHelper con MAM de Intune:

1. Para usar la copia de seguridad de varias entidades con BackupAgentHelper, siga la guía de Android para saber cómo [extender BackupAgentHelper](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper).

2. Haga que la clase extienda el equivalente de MAM de BackupAgentHelper, FileBackupHelper y SharedPreferencesBackupHelper.

|Clase de Android | Equivalente de MAM |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

Seguir estas instrucciones llevará a que se realice correctamente una copia de seguridad y restauración de varias identidades.

### <a name="backupagent"></a>BackupAgent

BackupAgent le permite ser mucho más explícito acerca de los datos sobre los cuales desea hacer una copia de seguridad. Como el desarrollador es en gran medida responsable de la implementación, se deben dar más pasos para garantizar la protección de datos adecuada de Intune. Puesto que la mayoría del trabajo lo realizará usted como desarrollador, la integración de Intune le puede resultar ligeramente más complicada.

**Integración de MAM:**

1. Lea detenidamente la guía de Android para [Copia de tipo clave-valor](https://developer.android.com/guide/topics/data/keyvaluebackup.html) y específicamente para [extender BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) a fin de garantizar que la implementación de BackupAgent sigue las instrucciones de Android.

2. Haga que la clase extienda `MAMBackupAgent`.

**Copia de seguridad de varias identidades:**

1. Antes de comenzar la copia de seguridad, compruebe que los búferes de datos o archivos de los que planea realizar una copia de seguridad están permitidos por **el administrador de TI para crear copias de seguridad** en escenario con varias identidades. Le proporcionamos la función `isBackupAllowed` en `MAMFileProtectionManager` y `MAMDataProtectionManager` para determinar esto. Si no puede hacer la copia de seguridad del búfer de datos o de archivos, no debe seguir incluyéndolos en la copia de seguridad.

2. Si quiere realizar una copia de seguridad de las identidades de los archivos que registró en el paso 1 mientras realiza la copia de seguridad, debe llamar a `backupMAMFileIdentity(BackupDataOutput data, File … files)` con los archivos de los que planea extraer datos. Esto creará automáticamente nuevas entidades de copia de seguridad y las escribirá en `BackupDataOutput` . Estas entidades se consumirán automáticamente durante la restauración.

**Restauración de varias identidades:**

La guía sobre la copia de seguridad de datos especifica un algoritmo general para restaurar los datos de la aplicación y proporciona un ejemplo de código en la sección [Extensión de BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent). Para realizar una restauración correcta de varias identidades, debe seguir la estructura general que se proporciona en este ejemplo de código y prestar especial atención a lo siguiente:

1.  Debe utilizar un bucle `while(data.readNextHeader())`* para avanzar por las entidades de la copia de seguridad.

2.  Debe llamar a `data.skipEntityData()`* si `data.getKey()`* no coincide con la clave que escribió en `onBackup`. Si no realiza este paso, las restauraciones podrían no realizarse correctamente.

3.  Evite la devolución cuando se están usando las entidades de copia de seguridad en la construcción `while(data.readNextHeader())`*, puesto que se perderán las entidades que se escriben automáticamente.

* Donde `data` es el nombre de variable local para **BackupDataInput** que se transmite a la aplicación una vez que se restaura.

## <a name="multi-identity-optional"></a>Varias identidades (opcional)

### <a name="overview"></a>Información general
De forma predeterminada, el SDK de Intune App aplicará la directiva a la aplicación en su conjunto. La característica Varias identidades es una característica de protección de aplicación de Intune opcional que se puede habilitar para permitir que se aplique una directiva en un nivel por identidad. Para ello es necesaria más participación en la aplicación que otras características de la protección de la aplicación.

La aplicación *debe* informar al SDK cuando intente cambiar la identidad activa. En algunos casos, el SDK también notificará a la aplicación cuando se requiera un cambio de identidad. Sin embargo, en la mayoría de los casos, MAM no puede saber cuáles son los datos que se muestran en la UI ni los que se usan en un subproceso en un momento determinado y confía en que la aplicación establezca la identidad correcta a fin de evitar fugas de datos. En las secciones siguientes se detallarán algunos escenarios determinados que requieren acción de la aplicación.

> [!NOTE]
>  Si la participación de la aplicación correcta no se da, puede haber fugas de datos y otros problemas de seguridad.

Una vez que el usuario inscriba el dispositivo o la aplicación, el SDK registra esta identidad y la considera la identidad administrada principal de Intune. Los demás usuarios de la aplicación se tratarán como usuarios no administrados con una configuración de directiva sin restricciones.

> [!NOTE]
> Actualmente, solo se admite una identidad administrada de Intune por dispositivo.

Tenga en cuenta que una identidad se define simplemente como una cadena. Las identidades **no distinguen mayúsculas de minúsculas** y las solicitudes de identidades que se realizan al SDK podrían no devolverse con el mismo uso de mayúsculas y minúsculas que se empleó originalmente al establecer la identidad.

### <a name="enabling-multi-identity"></a>Habilitación de varias identidades

De forma predeterminada, se considera que todas las aplicaciones son de una única identidad. Puede declarar que una aplicación es compatible con varias identidades si coloca los metadatos siguientes en AndroidManifest.xml.

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>Definición de la identidad

Los desarrolladores pueden establecer la identidad del usuario de la aplicación en los niveles siguientes, en orden descendente según su prioridad:

  1. Nivel de subproceso
  2. Nivel de contexto (generalmente actividad)
  3. Nivel de proceso

Una identidad que se establece en el nivel de subproceso sustituye a una identidad que se establece en el nivel de contexto, la cual reemplaza a una identidad que se establece en el nivel de proceso. Una identidad que se establece en un contexto solo se usa en escenarios asociados adecuados. Las operaciones de E/S de archivos, por ejemplo, no tienen un contexto asociado. Habitualmente, las aplicaciones establecerán la identidad de contexto en una actividad. Una aplicación *no debe* mostrar los datos de una identidad administrada a menos que la identidad de la actividad esté establecida en la misma identidad. En general, la identidad de nivel de proceso resulta útil solo si la aplicación funciona con un usuario a la vez en todos los subprocesos. Es posible que muchas aplicaciones no necesiten usar esto.

Se pueden usar los métodos siguientes en `MAMPolicyManager` para establecer la identidad y recuperar los valores de identidad previamente establecidos.

```java
  public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

  /**
   * Get the currently applicable app policy. Same as
   * MAMComponents.get(AppPolicy.class). This method does
   * not take the context identity into account.
   */
  public static AppPolicy getPolicy();

  /**
  * Get the current app policy. This does NOT take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use the overload below.
   */
  public static AppPolicy getPolicy(final Context context);


  public static AppPolicy getPolicyForIdentity(final String identity);

  public static boolean getIsIdentityManaged(final String identity);

  ```

>[!NOTE]
> Puede borrar la identidad de la aplicación si la establece en null.
>
> La cadena vacía se puede usar como una identidad que nunca tendrá una directiva de protección de la aplicación.

#### <a name="results"></a>Resultados
Todos los métodos usados para establecer la identidad devuelven valores de resultado mediante `MAMIdentitySwitchResult`. Hay cuatro valores que se pueden devolver:

| Valor devuelto | Escenario |
|--|--|
| SUCCEEDED | El cambio de la identidad se realizó correctamente. |
| NOT_ALLOWED | No se permite el cambio de identidad. No se permite el cambio de identidad. Esto sucede si se intenta establecer la identidad de la interfaz de usuario (contexto) cuando hay una identidad diferente establecida en el subproceso actual. |
| CANCELLED | El usuario canceló el cambio de identidad, por lo general presionando el botón Atrás en un mensaje de autenticación o solicitud del PIN. |
| FAILED | No se pudo realizar el cambio de identidad por una razón específica.|

La aplicación *debe* garantizar que un cambio de identidad se realice correctamente antes de mostrar o usar datos corporativos. Actualmente, los cambios de identidad de proceso y subproceso siempre se realizarán correctamente para una aplicación compatible con varias identidades. Sin embargo, nos reservamos el derecho a agregar condiciones de error. El cambio de identidad de UI puede presentar un error si los argumentos no son válidos, si pudiera entrar en conflicto con la identidad de subproceso o si el usuario cancela los requisitos de inicio condicional (por ejemplo, si presiona el botón Atrás en la pantalla del PIN).


En el caso de establecer una identidad de contexto, el resultado se notifica de forma asincrónica. Si el contexto es una actividad, el SDK no sabe si el cambio de identidad se realizó correctamente hasta después de realizar el inicio condicional, lo que puede requerir que el usuario escriba un PIN o sus credenciales corporativas. Se espera que la aplicación implemente un elemento `MAMSetUIIdentityCallback` para recibir este resultado; además, puede pasar un valor null para este parámetro.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

También puede establecer la identidad de una actividad directamente a través de un método en `MAMActivity` en lugar de llamar a `MAMPolicyManager.setUIPolicyIdentity`. Para hacerlo, use el método siguiente:

```java
     public final void switchMAMIdentity(final String newIdentity);
```

También puede reemplazar un método en `MAMActivity` si desea que la aplicación reciba una notificación del resultado de los intentos de cambiar la identidad de esa actividad.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

>[!NOTE]
> Puede que cambiar la identidad requiera volver a crear la actividad. En este caso, la devolución de llamada `onSwitchMAMIdentityComplete` se entregará a la nueva instancia de la actividad.


### <a name="implicit-identity-changes"></a>Cambios de identidad implícitos

Además de la posibilidad de que la aplicación establezca la identidad, un subproceso o la identidad de un contexto pueden cambiar en función de la entrada de datos desde otra aplicación habilitada para Intune que tenga la directiva de protección de la aplicación.

#### <a name="examples"></a>Ejemplos

  1. Si una actividad se inicia desde un `Intent` enviado desde otra aplicación MAM, la identidad de la actividad se establecerá en función de la identidad efectiva de la otra aplicación en el punto en que se envió el `Intent`.

  2.  En el caso de los servicios, la identidad del subproceso se establecerá de forma similar para la duración de una llamada `onStart` o `onBind`. Las llamadas a `Binder` devueltas por `onBind` también establecerán temporalmente la identidad del subproceso.

  3. Las llamadas a `ContentProvider` establecerán de forma similar la identidad del subproceso a lo largo de su duración.


  Además, la interacción del usuario con una actividad puede provocar un cambio de identidad implícita.

  **Ejemplo**: la cancelación por un usuario de un mensaje de autorización durante `Resume` dará como resultado un cambio implícito a una identidad vacía.

  La aplicación tiene la oportunidad de enterarse de esos cambios y puede prohibirlos, si debe hacerlo. `MAMService` y `MAMContentProvider` exponen el siguiente método que las subclases pueden reemplazar:

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
  ```

  En la clase `MAMActivity`, existe un parámetro adicional en el método:

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
  ```

  * `AppIdentitySwitchReason` captura el origen del cambio implícito y puede aceptar los valores `CREATE`, `RESUME_CANCELLED` y `NEW_INTENT`.  La razón de `RESUME_CANCELLED` se usa cuando la reanudación de la actividad provoca que se muestren el PIN, la autenticación u otra IU compatible y el usuario intenta cancelar esa IU, por lo general mediante el uso del botón Atrás.


  * `AppIdentitySwitchResultCallback` es así:

    ```java
    public interface AppIdentitySwitchResultCallback {
        /**
         * @param result
         *            whether the identity switch can proceed.
         */
        void reportIdentitySwitchResult(AppIdentitySwitchResult result);
    }
    ```

    Donde ```AppIdentitySwitchResult``` es SUCCESS o FAILURE.

Al método `onMAMIdentitySwitchRequired` se le llama para todos los cambios de identidad implícitos, excepto aquellos realizados a través de un enlazador devueltos por `MAMService.onMAMBind`. Las implementaciones predeterminadas de `onMAMIdentitySwitchRequired` llaman inmediatamente a:

*  `reportIdentitySwitchResult(FAILURE)` cuando el motivo es RESUME_CANCELLED.

*  `reportIdentitySwitchResult(SUCCESS)` en todos los demás casos.

  Lo normal es que la mayoría de las aplicaciones no tengan que bloquear o retrasar un cambio de identidad de una manera diferente, pero en caso de hacerlo, se deben tener en cuenta los siguientes puntos:

  * Si se bloquea un cambio de identidad, el resultado es el mismo que si la configuración de uso compartido `Receive` hubiera prohibido la entrada de datos.

  * Si un servicio se ejecuta en el subproceso principal, se **debe** llamar a `reportIdentitySwitchResult` de forma sincrónica o se bloqueará el subproceso de IU.

  * Para la creación de la **actividad**, se llamará a `onMAMIdentitySwitchRequired` antes que a `onMAMCreate`. Si la aplicación debe mostrar la interfaz de usuario para determinar si se permite el cambio de identidad, esa interfaz de usuario se debe mostrar mediante una actividad *diferente*.

  * En una **actividad**, cuando se solicita un cambio a la identidad vacía con el motivo RESUME_CANCELLED, la aplicación debe modificar la actividad reanudada para mostrar datos coherentes con ese cambio de identidad.  Si esto no es posible, la aplicación debe rechazar el cambio y se pedirá al usuario que cumpla de nuevo la directiva de reanudar la identidad (por ejemplo, con la presentación de la pantalla de entrada del PIN de la aplicación).

    > [!NOTE]
    > Una aplicación de varias identidades siempre recibirá datos de entrada de aplicaciones tanto administradas como sin administrar. Es responsabilidad de la aplicación tratar los datos de identidades administradas de forma administrada.

  Si una identidad solicitada es administrada (use `MAMPolicyManager.getIsIdentityManaged` para comprobarlo), pero la aplicación no puede usar esa cuenta (por ejemplo, porque las cuentas, como las de correo electrónico, deben configurarse primero en la aplicación), el cambio de identidad se debe rechazar.



  ### <a name="file-protection"></a>Protección de archivos

  Cada archivo tiene una identidad asociada en el momento de creación basada en la identidad del proceso y del subproceso. Esta identidad se utilizará para el cifrado de archivos y la eliminación selectiva. Solo se cifrarán los archivos cuya identidad está administrada y tiene una directiva que exige cifrado. La eliminación de funcionalidad selectiva predeterminada del SDK solo eliminará los archivos asociados con la identidad administrada para la que se ha solicitado una eliminación. La aplicación puede consultar o cambiar la identidad de un archivo con la clase `MAMFileProtectionManager`.

  ```java
    public final class MAMFileProtectionManager {
    /**
         * Protect a file. This will synchronously trigger whatever protection is required for the 
           file, and will tag the file for future protection changes.

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
        * Protect a file obtained from a content provider. This is intended to be used for
        * sdcard (whether internal or removable) files accessed through the Storage Access Framework.
        * It may also be used with descriptors referring to private files owned by this app.
        * It is not intended to be used for files owned by other apps and such usage will fail. If
        * creating a new file via a content provider exposed by another MAM-integrated app, the new
        * file identity will automatically be set correctly if the ContentResolver in use was
        * obtained via a Context with an identity or if the thread identity is set.
        *
        * This will synchronously trigger whatever protection is required for the file, and will tag
        * the file for future protection changes. If an identity is set on a directory, it is set
        * recursively on all files and subdirectories. If MAM is operating in offline mode, this
        * method will silently do nothing.
        *
        * @param identity
        *       Identity to set.
        * @param file
        *       File to protect.
        *
        * @throws IOException
        *       If the file cannot be protected.

        */
        public static void protect(final ParcelFileDescriptor file, final String identity) throws IOException;

        /**
         * Get the protection info on a file.
         *
         * @param file
         *            File or directory to get information on.
         * @return File protection info, or null if there is no protection info.
         * @throws IOException
         *             If the file cannot be read or opened.
         */
        public static MAMFileProtectionInfo getProtectionInfo(final ParcelFileDescriptor file) throws IOException;

    }

    public interface MAMFileProtectionInfo {
        String getIdentity();
    }

  ```
#### <a name="app-responsibility"></a>Responsabilidad de la aplicación
MAM no puede inferior automáticamente una relación entre los archivos que se leen y los datos que se muestran en una `Activity`. Las aplicaciones *deben* establecer la identidad de UI de manera adecuada antes de mostrar los datos corporativos. Esto incluye los datos leídos de los archivos. Si un archivo proviene de fuera de la aplicación (ya sea de un `ContentProvider` o se lee de una ubicación grabable de manera pública), la aplicación *debe* intentar determinar la identidad de archivo (con `MAMFileProtectionManager.getProtectionInfo`) antes de mostrar la información leída desde el archivo. Si `getProtectionInfo` informa una identidad no nula y no vacía, la identidad de UI se *debe* establecer para que coincida con esta identidad (con `MAMActivity.switchMAMIdentity` o `MAMPolicyManager.setUIPolicyIdentity`). Si el cambio de identidad presenta un error, los datos del archivo *no se deben* mostrar.

Un flujo de ejemplo debería ser similar al siguiente:
  * El usuario selecciona un documento para abrir en la aplicación
  * Durante el flujo de apertura, antes de leer los datos del disco, la aplicación confirma la identidad que se debe usar para mostrar el contenido
    * Información de MAMFileProtectionInfo = MAMFileProtectionManager.getProtectionInfo(docPath)
    * if(info)   MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback)
    * La aplicación espera hasta que se informa un resultado para devolución de llamada
    * Si el resultado informado es un error, la aplicación no muestra el documento.
  * La aplicación abre y representa el archivo

## <a name="offline-scenarios"></a>Escenarios sin conexión

El etiquetado de identidad de archivo es sensible al modo sin conexión. Se deben tener en cuenta los siguientes puntos:

  * Si no está instalado el Portal de empresa, no se puede etiquetar la identidad de los archivos.

  * Si está instalado el Portal de empresa, pero la aplicación no tiene una directiva MAM de Intune, no se puede etiquetar la identidad de los archivos de forma confiable.

  * Cuando esté disponible el etiquetado de identidad de los archivos, todos los archivos creados anteriormente se tratan como personales o no administrados (que pertenecen a la identidad de cadena vacía), a menos que la aplicación se instalara anteriormente como una aplicación administrada de una única identidad, en cuyo caso se tratan como pertenecientes al usuario inscrito.

### <a name="directory-protection"></a>Protección de los directorios

Los directorios se pueden proteger con el mismo método `protect` que se usa para proteger los archivos. Tenga en cuenta que la protección de los directorios se aplica de forma recursiva a todos los archivos y subdirectorios contenidos en el directorio y a los archivos nuevos creados dentro del directorio. Como la protección de directorios se aplica de forma recursiva, la llamada de `protect` puede tardar un poco en completarse en el caso de directorios muy grandes. Por este motivo, las aplicaciones que aplican protección a un directorio que contiene una gran cantidad de archivos puede querer ejecutar `protect` de manera asincrónica en un subproceso en segundo plano.

### <a name="data-protection"></a>Protección de datos

No es posible etiquetar un archivo como perteneciente a varias identidades. Las aplicaciones que deben almacenar datos que pertenecen a distintos usuarios en el mismo archivo pueden hacerlo manualmente mediante las características proporcionadas por `MAMDataProtectionManager`. Esto permite que la aplicación cifre los datos y los asocie a un usuario determinado. Los datos cifrados son adecuados para almacenarse en disco en un archivo. Puede consultar los datos asociados con la identidad y descifrarlos más tarde.

Las aplicaciones que usan `MAMDataProtectionManager` deben implementar un receptor para la notificación `MANAGEMENT_REMOVED`. Una vez que se complete esta notificación, los búferes que se protegieron con esta clase ya no serán legibles si se habilitó el cifrado de archivos cuando los búferes estaban protegidos. Una aplicación puede corregir esta situación con una llamada a MAMDataProtectionManager.unprotect en todos los búferes durante esta notificación. Tenga en cuenta que también es seguro llamar a la protección durante esta notificación si se quiere conservar la información de identidad; se garantiza que el cifrado estará deshabilitado durante la notificación.

```java

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

### <a name="content-providers"></a>Proveedores de contenido

Si la aplicación proporciona datos corporativos distintos de un **ParcelFileDescriptor** a través de un **ContentProvider**, la aplicación debe llamar al método `isProvideContentAllowed(String)` en `MAMContentProvider` y transmitir el UPN (nombre principal de usuario) de la identidad del propietario para el contenido. Si esta función devuelve false, puede que el contenido *no* se devuelva al autor de la llamada. Los descriptores de archivo devueltos a través de un proveedor de contenido se administran automáticamente en función de la identidad del archivo.

### <a name="selective-wipe"></a>Eliminación selectiva

Si una aplicación se registra para recibir la notificación `WIPE_USER_DATA`, no obtendrá el beneficio del comportamiento de eliminación selectiva predeterminada del SDK. En el caso de aplicaciones compatibles con varias identidades, esta pérdida puede tener un impacto más considerable dado que la eliminación selectiva predeterminada de MAM solo eliminará los archivos cuya identidad sea el destino de una eliminación.

Si una aplicación compatible con varias identidades desea que se realice una eliminación selectiva predeterminada de MAM _**y**_ también desea realizar sus propias acciones en la eliminación, se debe registrar para recibir notificaciones `WIPE_USER_AUXILIARY_DATA`. El SDK enviará inmediatamente esta notificación antes de que realice la eliminación selectiva predeterminada de MAM. Una aplicación nunca se debe registrar para WIPE_USER_DATA y WIPE_USER_AUXILIARY_DATA.

## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Habilitación de la configuración de destino de MAM para las aplicaciones Android (opcional)
Los pares clave-valor específicos de la aplicación se pueden configurar en la consola de Intune. Intune no interpreta en absoluto los pares clave-valor, sino que simplemente se pasan a la aplicación. Las aplicaciones que desean recibir dicha configuración pueden usar las clases `MAMAppConfigManager` y `MAMAppConfig` para hacerlo. Si hay varias directivas dirigidas a la misma aplicación, puede haber varios valores en conflicto disponibles para la misma clave.

### <a name="example"></a>Ejemplo
```
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
LOGGER.info("App Config Data = " + (appConfig == null ? "null" : appConfig.getFullData()));
String valueToUse = null;
if (appConfig.hasConflict("foo")) {
    List<String> values = appConfig.getAllStringsForKey("foo");
    for (String value : values) {
        if (isCorrectValue(value)) {
            valueToUse = value;
        }
    }
} else {
    valueToUse = appConfig.getStringForKey("foo", MAMAppConfig.StringQueryType.Any);
}
LOGGER.info("Found value " + valueToUse);
```

### <a name="mamappconfig-reference"></a>Referencia de MAMAppConfig

```
public interface MAMAppConfig {
    /**
     * Conflict resolution types for Boolean values.
     */
    enum BooleanQueryType {
        /**
         * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
         */
        Any,
        /**
         * In case of conflict, returns true if any of the values are true.
         */
        Or,
        /**
         * In case of conflict, returns false if any of the values are false.
         */
        And
    }

    /**
     * Conflict resolution types for integer and double values.
     */
    enum NumberQueryType {
        /**
         * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
         */
        Any,
        /**
         * In case of conflict, returns the minimum Integer.
         */
        Min,
        /**
         * In case of conflict, returns the maximum Integer.
         */
        Max
    }

    /**
     * Conflict resolution types for Strings.
     */
    enum StringQueryType {
        /**
         * In case of conflict, arbitrarily picks one. This is not guaranteed to return the same value every time.
         */
        Any,
        /**
         * In case of conflict, returns the first result ordered alphabetically.
         */
        Min,
        /**
         * In case of conflict, returns the last result ordered alphabetically.
         */
        Max
    }

    /**
     * Retrieve the List of Dictionaries containing all the custom
     *  config data sent by the MAMService. This will return every
     * Application Configuration setting available for this user, one
     *  mapping for each policy applied to the user.
     */
    List<Map<String, String>> getFullData();

    /**
     * Returns true if there is more than one targeted custom config setting for the key provided. 
     */
    boolean hasConflict(String key);

    /**
     * @return a Boolean value for the given key if it can be coerced into a Boolean, or 
     * null if none exists or it cannot be coerced.
     */
    Boolean getBooleanForKey(String key, BooleanQueryType queryType);

    /**
     * @return a Long value for the given key if it can be coerced into a Long, or null if none exists or it cannot be coerced.
     */
    Long getIntegerForKey(String key, NumberQueryType queryType);

    /**
     * @return a Double value for the given key if it can be coerced into a Double, or null if none exists or it cannot be coerced.
     */
    Double getDoubleForKey(String key, NumberQueryType queryType);

    /**
     * @return a String value for the given key, or null if none exists.
     */
    String getStringForKey(String key, StringQueryType queryType);

    /**
     * Like getBooleanForKey except returns all values if multiple are present.
     */
    List<Boolean> getAllBooleansForKey(String key);

    /**
     * Like getIntegerForKey except returns all values if multiple are present.
     */
    List<Long> getAllIntegersForKey(String key);

    /**
     * Like getDoubleForKey except returns all values if multiple are present.
     */
    List<Double> getAllDoublesForKey(String key);

    /**
     * Like getStringForKey except returns all values if multiple are present.
     */
    List<String> getAllStringsForKey(String key);
}
```

### <a name="notification"></a>Notificación
La configuración de aplicación agrega un nuevo tipo de notificación:
* **REFRESH_APP_CONFIG**: esta notificación se envía en `MAMUserNotification` e informa a la aplicación que los datos de configuración de aplicación nuevos están disponibles.

Para obtener más información sobre las funciones de Graph API en relación con los valores de configuración de destino de MAM, vea la [referencia sobre Graph API para la configuración de destino de MAM](https://graph.microsoft.io/en-us/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create). <br>

Para más información sobre cómo crear una directiva de configuración de aplicaciones de destino de MAM en Android, vea la sección de la configuración de aplicaciones de destino de MAM en [How to use Microsoft Intune app configuration policies for Android](https://docs.microsoft.com/en-us/intune/app-configuration-policies-use-android) (Uso de las directivas de configuración de aplicaciones de Microsoft Intune para Android).

## <a name="style-customization-optional"></a>Personalización del estilo (opcional)

Las vistas que el SDK de MAM genera se pueden personalizar visualmente para que coincidan con la aplicación en que está integrada. Puede personalizar el color principal, el color secundario y el color de fondo, además del tamaño del logotipo de la aplicación. Esta personalización de estilo es opcional y se usarán los valores predeterminados si no hay ningún estilo personalizado configurado.


### <a name="how-to-customize"></a>Cómo realizar la personalización
Para aplicar cambios de estilo a las vistas de MAM de Intune, primero debe crear un archivo XML de invalidación de estilo. Este archivo se debe colocar en el directorio "/res/xml" de la aplicación y puede ponerle el nombre que desee. A continuación se muestra un ejemplo del formato que debe tener este archivo.

```xml
<?xml version="1.0" encoding="utf-8"?>
<styleOverrides>
    <item
        name="foreground_color"
        resource="@color/red"/>
    <item
        name="accent_color"
        resource="@color/blue"/>
    <item
        name="background_color"
        resource="@color/green"/>
    <item
        name="logo_image"
        resource="@drawable/app_logo"/>
</styleOverrides>

```

Debe volver a usar recursos que ya existen en la aplicación. Por ejemplo, debe definir el color verde en el archivo colors.xml y hacer referencia a él aquí. No puede usar el código de color hexadecimal "#0000ff". El tamaño máximo del logotipo de la aplicación es de 110 dip (dp). Puede usar una imagen de logotipo más pequeña, pero obtendrá mejores resultados si cumple con el requisito de tamaño máximo. Si supera el límite de 110 dip, la imagen se reducirá y puede verse borrosa.

A continuación se muestra la lista completa de los atributos de estilo permitidos, los elementos de interfaz de usuario que controlan, los nombres de elemento de los atributos XML y el tipo de recurso que se espera para cada uno.

|Estilo de atributo | Elementos de interfaz de usuario afectados | Nombre de elemento del atributo | Tipo de recurso esperado |
| -- | -- | -- | -- |
| Color de fondo | Color de fondo de la pantalla de PIN <Br>Color de relleno del cuadro de PIN | background_color | Color |
| Color de primer plano | Color del texto de primer plano <br> Borde del cuadro de PIN en estado predeterminado <br> Caracteres (incluidos caracteres ofuscados) en el cuadro de PIN cuando un usuario escribe un PIN| foreground_color | Color|
| Color de énfasis | Borde del cuadro de PIN cuando está resaltado <br> Hipervínculos |accent_color | Color |
| Logotipo de la aplicación | Icono grande que aparece en la pantalla de PIN de la aplicación Intune | logo_image | Drawable |

## <a name="limitations"></a>Limitaciones

### <a name="file-size-limitations"></a>Limitaciones del tamaño de archivo

En el caso de las bases de código de gran tamaño que se ejecutan sin [ProGuard](http://proguard.sourceforge.net/), las limitaciones del formato de archivo ejecutable Dalvik se convierten en un problema. En concreto, pueden producirse las siguientes limitaciones:

1.  Límite de 65.000 en campos.
2.  Límite de 65.000 en métodos.

### <a name="policy-enforcement-limitations"></a>Limitaciones de cumplimiento de directivas

* **Captura de pantalla**: el SDK no puede aplicar un nuevo valor de configuración de la captura de pantalla en aquellas actividades que ya hayan pasado por Activity.onCreate. Esto puede dar lugar a un período de tiempo en el cual la aplicación se configuró para deshabilitar las capturas de pantalla, pero aún así, todavía se pueden tomar capturas de pantalla.

* **Uso de solucionadores de contenido**: la directiva de "transferencia o recepción" de Intune puede bloquear (o bloquear parcialmente) el uso de un solucionador de contenido para acceder al proveedor de contenido de otra aplicación. Esto hará que los métodos de ContentResolver devuelvan un valor nulo o creen un valor de error (por ejemplo, `openOutputStream` creará el valor `FileNotFoundException` si se bloquea). La aplicación puede determinar si fue la directiva quien produjo un error al escribir los datos a través de un solucionador de contenido, cuando realizó la siguiente llamada:
    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```
    o si no hay ninguna actividad asociada

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    En el segundo caso, las aplicaciones de varias identidades deben encargarse de establecer adecuadamente la identidad de los subprocesos (o pasar una identidad explícita a la llamada de `getPolicy`).
    
### <a name="exported-services"></a>Servicios exportados

 El archivo AndroidManifest.xml que se incluye en el SDK para aplicaciones de Intune contiene el elemento **MAMNotificationReceiverService**; este elemento debe ser un servicio exportado para permitir que el Portal de empresa envíe notificaciones a una aplicación habilitada. El servicio comprueba quién fue el autor de la llamada para asegurarse de que solo el Portal de empresa tiene permiso para enviar notificaciones.

## <a name="expectations-of-the-sdk-consumer"></a>Expectativas del consumidor del SDK

El SDK de Intune mantiene el contrato proporcionado por la API de Android, aunque se pueden desencadenar condiciones de error con más frecuencia como resultado de la aplicación de directivas. Gracias a estas prácticas recomendadas, Android reducirá la probabilidad de que se produzcan errores:

* Las funciones del SDK de Android que podrían devolver el valor "null" tienen una mayor probabilidad de ser nulas.  Para minimizar los problemas, asegúrese de los valores que pueden ser “null” se encuentran en los lugares adecuados.

* Todas aquellas características que se pueden comprobar deben, por supuesto, comprobarse a través de sus API de reemplazo de MAM.

* Las funciones derivadas deben llamar a través de sus versiones de superclase.

* Evite usar cualquier API de manera ambigua. Por ejemplo, usar `Activity.startActivityForResult` sin comprobar antes si requestCode creará un comportamiento extraño.

## <a name="telemetry"></a>Telemetría

El SDK para aplicaciones de Intune para Android no controla la recopilación de datos de su aplicación. De manera predeterminada, la aplicación Portal de empresa registra los datos de telemetría en los siguientes eventos de uso. Estos datos se envían a Microsoft Intune. Según las directivas de Microsoft, no se recopila información de identificación personal (PII por sus siglas en inglés).

> [!NOTE]
> Si los usuarios finales deciden no enviar estos datos, deberán desactivar la telemetría en la sección Configuración de la aplicación Portal de empresa. Para obtener más información, consulte [Desactivar la recopilación de datos de uso de Microsoft](https://docs.microsoft.com/en-us/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="recommended-android-best-practices"></a>Procedimientos recomendados de Android

* Todos los proyectos de biblioteca deberían compartir el mismo paquete de Android siempre que sea posible. Esta solución no generará errores esporádicos en el entorno de tiempo de ejecución; este es únicamente un problema de tiempo de compilación. Las versiones más recientes del SDK para aplicaciones de Intune quitarán parte de esta redundancia.

* Use las herramientas de la compilación del SDK de Android más reciente.

* Quite todas las bibliotecas innecesarias y que no use (por ejemplo, android.support.v4)
