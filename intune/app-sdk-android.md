---
title: Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune
description: El SDK de la aplicación Microsoft Intune para Android le permite incorporar la administración de aplicaciones móviles (MAM) de Intune en su aplicación Android.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2cad30b0cf446d6591cba2997261f049ad6ae983
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735636"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune

> [!NOTE]
> Es posible que quiera leer primero la [Información general del SDK para aplicaciones de Intune](app-sdk.md), que cubre las características actuales del SDK y describe cómo preparar la integración en cada plataforma compatible.

El SDK para aplicaciones de Microsoft Intune para Android permite incorporar directivas de aplicaciones de Intune (también conocidas como directivas MAM o **APP**) a la aplicación Android nativa. Una aplicación administrada por Intune es aquella que está integrada con el SDK para aplicaciones de Intune. Los administradores de Intune pueden implementar fácilmente directivas de protección de aplicaciones en la aplicación administrada por Intune cuando Intune la administra de manera activa.


## <a name="whats-in-the-sdk"></a>Qué hay en el SDK

El SDK para aplicaciones de Intune consta de los siguientes archivos:

* **Microsoft.Intune.MAM.SDK.aar**: los componentes del SDK, excepto los archivos JAR de la biblioteca de compatibilidad.
* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: las clases necesarias para habilitar MAM en aplicaciones que usan la biblioteca de compatibilidad de Android v4.
* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: las clases necesarias para habilitar MAM en aplicaciones que usan la biblioteca de compatibilidad de Android v7.
* **Microsoft.Intune.MAM.SDK.Support.v17.jar**: las clases necesarias para habilitar MAM en aplicaciones que usan la biblioteca de compatibilidad de Android v17. 
* **Microsoft.Intune.MAM.SDK.Support.Text.jar**: las clases necesarias para habilitar MAM en aplicaciones que usan clases de la biblioteca de compatibilidad de Android en el paquete `android.support.text`.
* **Microsoft.Intune.MDM.SDK.DownlevelStubs.jar**: este archivo jar contiene códigos auxiliares para las clases del sistema de Android que solo están presentes en los dispositivos nuevos, pero a las que se hace referencia mediante métodos en MAMActivity. Los dispositivos más recientes ignorarán estas clases de código auxiliar. Este archivo jar solo es necesario si la aplicación realiza la reflexión en clases derivadas de MAMActivity y en la mayoría de las aplicaciones no es necesario incluirlo. Si usa este archivo jar, debe excluir todas las clases de ProGuard. Todas estarán en el paquete de raíz "android"
* **com.microsoft.intune.mam.build.jar**: un complemento de Gradle que [ayuda a integrar el SDK](#build-tooling).
* **CHANGELOG.txt**: proporciona un registro de los cambios hechos en cada versión del SDK.
* **THIRDPARTYNOTICES. TXT**: es un aviso de atribución que reconoce el código de terceros o de OSS que se compilará en la aplicación.

## <a name="requirements"></a>Requisitos

### <a name="android-versions"></a>Versiones de Android
El SDK admite desde la API 19 (Android 4.4 y versiones posteriores) a la API 28 (Android 9.0) de Android.

### <a name="company-portal-app"></a>Aplicación de portal de empresa
La aplicación [Portal de empresa](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) debe estar presente en el dispositivo para que el SDK para aplicaciones de Intune para Android pueda habilitar las directivas de protección. El Portal de empresa recupera las directivas de protección de aplicaciones del servicio Intune. Cuando se inicializa la aplicación, carga la directiva y el código para aplicar dicha directiva desde el Portal de empresa.

> [!NOTE]
> Si la aplicación Portal de empresa no está en el dispositivo, una aplicación administrada por Intune tiene el mismo comportamiento que una aplicación normal que no admite las directivas de protección de aplicaciones de Intune.

Para la protección de aplicaciones sin inscripción de dispositivo, _**no**_ es necesario que el usuario inscriba el dispositivo con la aplicación Portal de empresa.

## <a name="sdk-integration"></a>Integración del SDK

### <a name="sample-app"></a>Aplicación de ejemplo
En [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) hay un ejemplo de cómo integrar Intune App SDK correctamente. En este ejemplo se usa el [complemento de compilación de Gradle](#gradle-build-plugin).

### <a name="referencing-intune-app-libraries"></a>Referencia a bibliotecas de aplicaciones de Intune

El SDK para aplicaciones de Intune es una biblioteca de Android estándar que no tiene dependencias externas. **Microsoft.Intune.MAM.SDK.aar** contiene tanto las interfaces necesarias para la habilitación de una directiva de protección de aplicaciones como el código necesario para interoperar con la aplicación Portal de empresa de Microsoft Intune.

**Microsoft.Intune.MAM.SDK.aar** se debe especificar como una referencia a la biblioteca de Android. Para hacerlo, abra el proyecto de aplicación en Android Studio y vaya a **Archivo > Nuevo > Nuevo módulo** y seleccione **Importar paquete .JAR/.AAR**. Luego, seleccione nuestro paquete de archivos de Android Microsoft.Intune.MAM.SDK.aar para crear un módulo para nuestro .AAR. Haga clic con el botón derecho en el módulo o los módulos que contienen el código de la aplicación y vaya a **Configuración de módulo** > **pestaña Dependencias** > **icono +**  > **Module dependency** (Dependencia de módulo) > seleccione el módulo AAR de SDK de MAM que acaba de crear > **Aceptar**. Esto garantizará que el módulo se compila con el SDK de MAM al crear el proyecto.

Además, las bibliotecas de **Microsoft.Intune.MAM.SDK.Support.XXX.jar** contienen variantes de Intune de las bibliotecas `android.support.XXX` correspondientes. No están integradas en Microsoft.Intune.MAM.SDK.aar en caso de que una aplicación no tenga que depender de las bibliotecas de compatibilidad.

#### <a name="proguard"></a>ProGuard

Si se usa [ProGuard](http://proguard.sourceforge.net/) (o cualquier otro mecanismo de reducción u ofuscación) como paso de compilación, el SDK tiene reglas de configuración adicionales que se deben incluirse. Cuando se incluye el paquete .AAR en la compilación, nuestras reglas se integran de forma automática en el paso de ProGuard y se mantienen los archivos de clase necesarios.

Las bibliotecas de autenticación de Azure Active Directory (ADAL) pueden tener sus propias restricciones de ProGuard. Si la aplicación integra ADAL, debe seguir la documentación de ADAL sobre estas restricciones.

### <a name="build-tooling"></a>Herramientas de compilación
Intune App SDK es una biblioteca de Android que permite a la aplicación admitir el cumplimiento de directivas de Intune y participar en él. Algunas directivas exigen que [la aplicación participe de forma explícita para poder aplicarlas](#enable-features-that-require-app-participation), pero la mayoría se aplican casi automáticamente. Para que se apliquen automáticamente hace falta que las aplicaciones reemplacen la herencia de varias clases base de Android con la herencia de equivalentes de MAM y, del mismo modo, reemplacen llamadas a ciertas clases de servicio de sistema de Android con llamadas a equivalentes de MAM. Estos reemplazos específicos que se necesitan se detallan más [abajo](#class-and-method-replacements).

Realizar manualmente estos reemplazos puede ser un proceso largo. Es mejor usar las herramientas de compilación que ofrece el SDK (un complemento para compilaciones de Gradle y una herramienta de línea de comandos para compilaciones que no son de Gradle) que realizan los reemplazos automáticamente. Estas herramientas transforman los archivos de clase generados por la compilación de Java y no modifican el código fuente original.

Las herramientas solo realizan [reemplazos directos](#class-and-method-replacements). No realizan integraciones de SDK más complejas, como [guardar como directiva](#enable-features-that-require-app-participation), [trabajar con varias identidades](#multi-identity-optional), [registrar con APP-WE](#app-protection-policy-without-device-enrollment), [realizar modificaciones en AndroidManifest](#manifest-replacements) o [configurar ADAL](#configure-azure-active-directory-authentication-library-adal) por lo que estas deberán hacerse antes de que la aplicación esté totalmente habilitada para Intune. Revise detenidamente el resto de esta documentación para los puntos de integración correspondiente a la aplicación.

> [!NOTE]
> Se pueden ejecutar las herramientas en un proyecto donde ya se ha realizado la integración de origen completa o parcial del SDK de MAM a través de reemplazos manuales. El proyecto debe seguir enumerando el SDK de MAM como una dependencia.

### <a name="gradle-build-plugin"></a>Complemento de compilación de Gradle
Si la aplicación no se compila con Gradle, vaya directamente a la [integración con la herramienta de línea de comandos](#command-line-build-tool). 

El complemento de SDK de aplicaciones que se distribuye como parte del SDK como **GradlePlugin/com.microsoft.intune.mam.build.jar**. Para que Gradle pueda encontrar el complemento, debe agregarse a la ruta de clase buildscript. El complemento depende [Javassist](https://jboss-javassist.github.io/javassist/), que también se debe agregar. Para agregarlos a la ruta de clase, agregue lo siguiente a la raíz `build.gradle`

```groovy
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath "org.javassist:javassist:3.22.0-GA"
        classpath files("$PATH_TO_MAM_SDK/GradlePlugin/com.microsoft.intune.mam.build.jar")
    }
}
```

Después, en el archivo `build.gradle` del proyecto APK, basta con aplicar el complemento como

```groovy
apply plugin: 'com.microsoft.intune.mam'
```

De forma predeterminada, el complemento funcionará **solo** en dependencias `project`.
La compilación de prueba no se ve afectada. Puede que se proporcione configuración a la lista
* Proyectos que se excluyen
* [Dependencias externas que se incluyen](#usage-of-includeexternallibraries) 
* Clases específicas que se excluyen del procesamiento
* Variantes que se excluyen del procesamiento. Pueden hacer referencia a un nombre de variante completo o un sabor único. Por ejemplo,
     * si la aplicación tiene los tipos de compilación `debug` y `release` con sabores {`savory`, `sweet`} y {`vanilla`, `chocolate`}, puede especificar
     * `savory` para excluir todas las variantes con el sabor savory o `savoryVanillaRelease` para excluir solo esa variante exacta.

#### <a name="example-partial-buildgradle"></a>Ejemplo de build.gradle parcial

```groovy

apply plugin: 'com.microsoft.intune.mam'

dependencies {
    implementation project(':product:FooLib')
    implementation project(':product:foo-project')
    implementation fileTree(dir: "libs", include: ["bar.jar"])
    implementation fileTree(dir: "libs", include: ["zap.jar"])
    implementation "com.contoso.foo:zap-artifact:1.0.0"
    implementation "com.microsoft.bar:baz:1.0.0"

    // Include the MAM SDK
    implementation files("$PATH_TO_MAM_SDK/Microsoft.Intune.MAM.SDK.aar")
}
intunemam {
    excludeProjects = [':product:FooLib']
    includeExternalLibraries = ['bar.jar', "com.contoso.foo:zap-artifact", "com.microsoft.*", "!com.microsoft.qux*"]
    excludeClasses = ['com.contoso.SplashActivity']
    excludeVariants=['savory']
}
```

Esto tendría los siguientes efectos:
* `:product:FooLib` no se reescribe porque está incluido en `excludeProjects`
* `:product:foo-project` se reescribe, excepto para `com.contoso.SplashActivity`, que se omite porque se encuentra en `excludeClasses`
* `bar.jar` se reescribe porque está incluido en `includeExternalLibraries`
* `zap.jar` **no** se reescribe porque no es un proyecto y no se incluye en `includeExternalLibraries`
* `com.contoso.foo:zap-artifact:1.0.0` se reescribe porque está incluido en `includeExternalLibraries`
* `com.microsoft.bar:baz:1.0.0` se reescribe porque está incluido en `includeExternalLibraries` mediante un carácter comodín (`com.microsoft.*`).
* `com.microsoft.qux:foo:2.0` no se reescribe aunque coincida con el mismo carácter comodín que el elemento anterior porque se excluye explícitamente mediante un patrón de negación.

#### <a name="usage-of-includeexternallibraries"></a>Uso de includeExternalLibraries

Puesto que el complemento solo funciona en dependencias del proyecto (normalmente proporcionado por la función `project()`) de forma predeterminada, todas las dependencias especificadas por `fileTree(...)` u obtenidas de maven u otros orígenes de paquetes (por ejemplo, "`com.contoso.bar:baz:1.2.0`") deben proporcionarse a la propiedad `includeExternalLibraries` si se necesita que MAM las procese según los criterios que se explican más abajo. Se admiten caracteres comodín ("*"). Un elemento que comienza por `!` es una negación y se puede utilizar para excluir bibliotecas que en caso contrario se incluirían con un carácter comodín.

Al especificar las dependencias externas con notación de artefacto, se recomienda omitir el componente de versión en el valor `includeExternalLibraries`. Si incluye la versión, debe ser una versión exacta. Las especificaciones de la versión dinámica (por ejemplo, `1.+`) no se admiten.

La regla general que debe usar para determinar si necesita incluir bibliotecas en `includeExternalLibraries` se basa en dos preguntas:
1. ¿La biblioteca tiene clases para los que hay equivalentes de MAM? Ejemplos: `Activity`, `Fragment`, `ContentProvider`, `Service`, etcétera.
2. ¿En caso afirmativo, la aplicación usa esas clases?

Si la respuesta es "Sí" a ambas preguntas, debe incluir esa biblioteca en `includeExternalLibraries`. 

| Escenario | ¿Debe incluirse? |
|--|--|
| Se incluye una biblioteca de visor PDF en la aplicación y se usa `Activity` del visor en la aplicación cuando los usuarios intentan ver archivos PDF | Sí |
| Se incluye una biblioteca HTTP en la aplicación para obtener un rendimiento web mejorado | No |
| Se incluye una biblioteca como React Native que contiene clases derivadas de `Activity`, `Application` y `Fragment`, las cuales se usan o se derivan aún más en la aplicación | Sí |
| Se incluye una biblioteca como React Native que contiene clases derivadas de `Activity`, `Application` y `Fragment`, pero solo se usan clases auxiliares estáticas o clases de utilidades | No |
| Se incluye que contiene clases de vista derivadas de `TextView` y se usan esas clases o se derivan aún más en la aplicación | Sí |

#### <a name="reporting"></a>Generación de informes
El complemento de compilación puede generar un informe HTML de los cambios que realiza. Para solicitar la generación de este informe, especifique `report = true` en el bloque de configuración `intunemam`. Si se genera, el informe se escribirá en el directorio de compilación, en `outputs/logs`.

```groovy
intunemam {
    report = true
}
```

#### <a name="dependencies"></a>Dependencias

El complemento Gradle tiene una dependencia en [Javassist](https://jboss-javassist.github.io/javassist/), que debe estar disponible para la resolución de dependencias de Gradle (como se describió antes). Javassist se usa únicamente en tiempo de compilación cuando se ejecuta el complemento. No se agregará ningún código Javassist a la aplicación.

> [!NOTE] 
> Debe usar la versión 3.0 o posterior del complemento Gradle de Android y Gradle 4.1 o posterior.

### <a name="command-line-build-tool"></a>Herramienta de compilación de línea de comandos
Si la compilación usa Gradle, vaya directamente a la [siguiente sección](#class-and-method-replacements).

La herramienta de compilación de línea de comandos está disponible en la carpeta `BuildTool` del SDK. Realiza la misma función que el complemento de Gradle explicado anteriormente, pero se puede integrar en sistemas de compilación personalizada o que no sean de Gradle. Como es más genérico, es más complejo de invocar, por lo que debe usarse el complemento de Gradle cuando sea posible.

#### <a name="using-the-command-line-tool"></a>Mediante la herramienta de línea de comandos

La herramienta de línea de comandos se puede invocar mediante los scripts auxiliares que se encuentran en el directorio `BuildTool\bin`.

La herramienta espera estos parámetros:

| Parámetro | Descripción |
| -- | -- |
| `--input` | Una lista delimitada por puntos y coma de archivos jar y directorios de archivos de clase que se van a modificar. Debe incluir todos los directorios y archivos jar que quiere escribir. |
| `--output` | Una lista delimitada por puntos y coma de archivos jar y directorios donde se van a almacenar las clases modificadas. Debe haber una entrada de salida por cada entrada de entrada y deben aparecer en orden. |
| `--classpath` | La ruta de clase de la compilación. Puede contener tanto archivos jar como directorios de clase. |
| `--excludeClasses`| Una lista delimitada por puntos y coma que contiene los nombres de las clases que se deben excluir de la reescritura. |

Todos los parámetros son necesarios, excepto `--excludeClasses` que es opcional.

> [!NOTE] 
> En sistemas similares a Unix, el punto y coma es un separador de comandos. Para evitar que el shell divida los comandos, asegúrese de escapar de cada punto y coma con '\' o bien escriba el parámetro completo entre comillas.

#### <a name="example-command-line-tool-invocation"></a>Ejemplo de invocación de la herramienta de línea de comandos

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

Esto tendría los siguientes efectos:

* el directorio `product-foo-project` se reescribe como `mam-build\product-foo-project`
* `bar.jar` se reescribe como `mam-build\libs\bar.jar`
* `zap.jar` **no** se reescribe porque solo está incluido en `--classpath`
* La clase `com.contoso.SplashActivity` **no** se reescribe aunque esté en `--input`

> [!NOTE] 
> La herramienta de compilación no admite archivos aar actualmente. Si el sistema de compilación ya no extrae `classes.jar` cuando trabaja con archivos aar, deberá hacerlo antes de invocar la herramienta de compilación.


## <a name="class-and-method-replacements"></a>Reemplazos de clases y métodos

Las clases base de Android se deben reemplazar por sus equivalentes MAM respectivos para permitir la administración de Intune. Las clases del SDK son un término medio entre las clases base de Android y la versión derivada que la propia aplicación tiene de esas clases. Por ejemplo, una actividad de aplicación podría terminar con una jerarquía de herencia que tendrá este aspecto: `Activity` > `MAMActivity` >
`AppSpecificActivity`. La capa MAM filtra las llamadas a las operaciones del sistema a fin de proporcionar una vista administrada sin complicaciones para la aplicación.

Además de las clases base, algunas clases que la aplicación podría usar sin tener que derivar (por ejemplo, `MediaPlayer`) también tienen los equivalentes de MAM necesarios y [también se deben reemplazar algunas llamadas a métodos](#wrapped-system-services). Los detalles concretos se proporcionan más abajo.

Todos los reemplazos que se detallan en esta sección pueden realizarse automáticamente mediante las [herramientas de compilación](#build-tooling) del SDK. 



| Clase base Android | Sustitución del SDK para aplicaciones de Intune |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.Dialog | MAMDialog |
| android.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.ListFragment | MAMListFragment |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent (vea [PendingIntent](#pendingintent)) |
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
| android.media.MediaPlayer | MAMMediaPlayer |
| android.media.MediaMetadataRetriever | MAMMediaMetadataRetriever |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |
| android.support.multidex.MultiDexApplication | MAMMultiDexApplication |
| android.widget.TextView | MAMTextView |
| android.widget.AutoCompleteTextView | MAMAutoCompleteTextView |
| android.widget.CheckedTextView | MAMCheckedTextView |
| android.widget.EditText | MAMEditText |
| android.inputmethodservice.ExtractEditText | MAMExtractEditText |
| android.widget.MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> Incluso si la aplicación no necesita su propia clase `Application` derivada, [vea `MAMApplication` a continuación](#mamapplication)

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar:

| Clase de Android | Sustitución del SDK para aplicaciones de Intune |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.JobIntentService | MAMJobIntentService
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider
| android.support.v4.content.WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar:

|Clase de Android | Sustitución del SDK para aplicaciones de Intune |
|--|--|
| android.support.v7.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.support.v7.app.AppCompatActivity | MAMAppCompatActivity |
| android.support.v7.widget.AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| android.support.v7.widget.AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| android.support.v7.widget.AppCompatEditText | MAMAppCompatEditText |
| android.support.v7.widget.AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| android.support.v7.widget.AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft.Intune.MAM.SDK.Support.v17.jar:
|Clase de Android | Sustitución del SDK para aplicaciones de Intune |
|--|--|
| android.support.v17.leanback.widget.SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft.Intune.MAM.SDK.Support.Text.jar:
|Clase de Android | Sustitución del SDK para aplicaciones de Intune |
|--|--|
| android.support.text.emoji.widget.EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| android.support.text.emoji.widget.EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| android.support.text.emoji.widget.EmojiEditText | MAMEmojiEditText |
| android.support.text.emoji.widget.EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>Métodos renombrados
En muchos casos, un método que se encuentra en la clase Android se marca como final de la clase de reemplazo MAM. En este caso, la clase de reemplazo MAM proporciona un método con un nombre similar (generalmente lleva el sufijo `MAM`) que se debería reemplazar en su lugar. Por ejemplo, al derivar desde `MAMActivity`, en lugar de reemplazar `onCreate()` y llamar a `super.onCreate()`, `Activity` debe reemplazar a `onMAMCreate()` y llamar a `super.onMAMCreate()`. El compilador de Java debe encargarse de aplicar las restricciones necesarias para evitar que se reemplace por accidente el método original en lugar del equivalente MAM.

### <a name="mamapplication"></a>MAMApplication
Si la aplicación crea una subclase de `android.app.Application`, **debe** crear una subclase de `com.microsoft.intune.mam.client.app.MAMApplication` en su lugar. Si la aplicación no tiene la subclase `android.app.Application`, **debe** establecer `"com.microsoft.intune.mam.client.app.MAMApplication"` como el atributo `"android:name"` en su etiqueta `<application>` de AndroidManifest.xml.

### <a name="pendingintent"></a>PendingIntent
En lugar de `PendingIntent.get*`, debe usar el método `MAMPendingIntent.get*`. Después de esto, puede usar la clase `PendingIntent` del modo habitual.

### <a name="wrapped-system-services"></a>Servicios del sistema encapsulados
Para algunas clases de servicios del sistema, es necesario llamar a un método estático en una clase contenedora de MAM en lugar de invocar directamente el método que quiera en la instancia de servicio. Por ejemplo, una llamada a `getSystemService(ClipboardManager.class).getPrimaryClip()` debe convertirse en una llamada a `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)`. No se recomienda realizar estos reemplazos manualmente. En su lugar, deje que BuildPlugin lo haga.

| Clase de Android | Sustitución del SDK para aplicaciones de Intune |
|--|--|
| android.content.ClipboardManager | MAMClipboard |
| android.content.ContentProviderClient | MAMContentProviderClientManagement |
| android.content.ContentResolver | MAMContentResolverManagement |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
| android.print.PrintManager | MAMPrintManagement |
| android.support.v4.print.PrintHelper | MAMPrintHelperManagement |
| android.view.View | MAMViewManagement |
| android.view.DragEvent | MAMDragEventManagement |

Algunas clases tienen la mayoría de sus métodos encapsulados (por ejemplo, `ClipboardManager`, `ContentProviderClient`, `ContentResolver` y `PackageManager`) mientras que otras solo tienen uno o dos métodos encapsulados (por ejemplo, `DownloadManager`, `PrintManager`, `PrintHelper`, `View` y `DragEvent`). Consulte las API expuestas por las clases equivalentes de MAM para conocer el método exacto si no utiliza BuildPlugin. 

### <a name="manifest-replacements"></a>Reemplazos de manifiestos
Puede que sea necesario realizar algunos de los reemplazos de clase anteriores en el manifiesto así como también en el código Java. De especial interés:
* Las referencias de manifiesto a `android.support.v4.content.FileProvider` se deben reemplazar por `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`.

## <a name="androidx-libraries"></a>Bibliotecas de AndroidX
Con Android P, Google anunció un nuevo conjunto (cuyo nombre ha cambiado) de bibliotecas de compatibilidad llamado AndroidX, y la versión 28 es la última versión principal de las bibliotecas de compatibilidad de Android existentes.

A diferencia de las bibliotecas de compatibilidad de Android, no se proporciona variantes de MAM de las bibliotecas de AndroidX. En su lugar, AndroidX debe tratar como cualquier otra biblioteca externa y debe estar configurada para el complemento o la herramienta de compilación la reescriba. Para las compilaciones de Gradle, esto puede hacerse si se incluye `androidx.*` en el campo `includeExternalLibraries` de la configuración del complemento. Las invocaciones de la herramienta de línea de comandos deben incluir explícitamente todos los archivos jar.
## <a name="sdk-permissions"></a>Permisos de SDK

El SDK para aplicaciones de Intune requiere tres [permisos del sistema de Android](https://developer.android.com/guide/topics/security/permissions.html) sobre las aplicaciones que lo integran:

* `android.permission.GET_ACCOUNTS` (solicitado en tiempo de ejecución si es necesario)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

La biblioteca de autenticación de Azure Active Directory ([ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/)) requiere estos permisos para realizar autenticación negociada. Si estos permisos no se conceden a la aplicación o el usuario los revoca, se deshabilitará el flujo de autenticación que necesita el agente (la aplicación de Portal de empresa).

## <a name="logging"></a>Registro

El registro se debe inicializar antes para aprovechar al máximo los datos registrados. `Application.onMAMCreate()` es típicamente el mejor lugar para inicializar el registro.

Para recibir registros MAM en la aplicación, cree un [controlador Java](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) y agréguelo a `MAMLogHandlerWrapper`. Esto invocará a `publish()` en el controlador de aplicación para cada mensaje de registro.

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
 * Checks whether any activities which could handle the given intent are allowed by policy. Returns false only if all
 * activities which could otherwise handle the intent are blocked. If there are no activities which could handle the intent
 * regardless of policy, returns true. If some activities are allowed and others blocked, returns true. Note that it is not
 * necessary to use this method for policy enforcement. If your app attempts to launch an intent for which there are no
 * allowed activities, MAM will display a dialog explaining the situation to the user.
 *
 * @param intent
 *         intent to check
 *
 * @return whether any activities which could handle this intent are allowed.
*/
boolean areIntentActivitiesAllowed(Intent intent);

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
 * This method is intended for diagnostic/telemetry purposes only. It can be used to discover whether
 * file encryption is in use. File encryption is transparent to the app, and the app should not need
 * to make any business logic decisions based on this.
 * 
 * @return True if file encryption is in use.
 */
boolean diagnosticIsFileEncryptionInUse();

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

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
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
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

El parámetro `service` debe ser uno de los siguientes valores `SaveLocation`:


- `SaveLocation.ONEDRIVE_FOR_BUSINESS`
- `SaveLocation.SHAREPOINT`
- `SaveLocation.LOCAL`
- `SaveLocation.OTHER`

`username` debe ser el UPN/nombre de usuario/correo electrónico asociado al servicio en la nube en donde se guarda (*no* necesariamente igual al usuario propietario del documento que se guarda). Use NULL si no existe una asignación entre el UPN de AAD y el nombre de usuario del servicio en la nube o si no se conoce el nombre de usuario.

El método anterior para determinar si la directiva de un usuario le permite guardar datos en diversas ubicaciones era `getIsSaveToPersonalAllowed()` dentro de la misma **AppPolicy**. Esta función está **en desuso** y no se debe usar; la invocación siguiente equivale a `getIsSaveToPersonalAllowed()`:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, userNameInQuestion);
```

>[!NOTE]
> Use `SaveLocation.OTHER` si la ubicación en cuestión no aparece en la enumeración **SaveLocations**.


## <a name="register-for-notifications-from-the-sdk"></a>Registrarse para recibir notificaciones del SDK

### <a name="overview"></a>Introducción
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

* **WIPE_USER_AUXILIARY_DATA**: las aplicaciones pueden registrarse para esta notificación si quieren que el SDK para aplicaciones de Intune realice el comportamiento predeterminado de eliminación selectiva, pero les gustaría quitar algunos datos auxiliares cuando se produzca la eliminación. Esta notificación no está disponible para aplicaciones de identidad única; solo se enviará a las aplicaciones de varias identidades.

* **REFRESH_POLICY**: esta notificación se envía en `MAMUserNotification`. Cuando se recibe esta notificación, se deben invalidar y actualizar las decisiones de directiva de Intune almacenadas en caché. Si la aplicación no almacena supuestos de directiva, no tiene que registrarse para recibir esta notificación.

* **REFRESH_APP_CONFIG**: esta notificación se envía en `MAMUserNotification`. Cuando se recibe esta notificación, se deben invalidar y actualizar los datos de configuración de la aplicación almacenados en caché.

* **MANAGEMENT_REMOVED**: esta notificación se envía en `MAMUserNotification` e informa a la aplicación que está a punto de dejar de estar administrada. Cuando deja de estar administrada, ya no podrá leer archivos cifrados, leer datos cifrados con MAMDataProtectionManager, interactuar con el portapapeles cifrado o participar de cualquier otro modo en el ecosistema de aplicaciones administradas. Ver más detalles a continuación.

* **MAM_ENROLLMENT_RESULT**: esta notificación se envía en `MAMEnrollmentNotification` para informar a la aplicación de que se ha completado un intento de inscripción APP-WE y proporcionar el estado del intento.

* **COMPLIANCE_STATUS**: esta notificación se envía en `MAMComplianceNotification` para informar a la aplicación del resultado de un intento de corrección de cumplimiento.

> [!NOTE]
> Una aplicación nunca debe registrarse para recibir notificaciones `WIPE_USER_DATA` y `WIPE_USER_AUXILIARY_DATA`.

### <a name="managementremoved"></a>MANAGEMENT_REMOVED

La notificación `MANAGEMENT_REMOVED` indica que un usuario previamente administrado por directivas ya no será administrado por la directiva de MAM de Intune. Esto no requiere que se borren los datos del usuario ni que el usuario cierre la sesión (si fuera necesario un borrado, se enviaría una notificación `WIPE_USER_DATA`). Es posible que muchas aplicaciones no tengan que controlar esta notificación en absoluto, pero las aplicaciones que utilizan `MAMDataProtectionManager` deben [prestar especial atención a esta notificación](#data-protection).

Cuando MAM llame al receptor `MANAGEMENT_REMOVED` de la aplicación, se cumplirá lo siguiente:
* MAM ya ha descifrado archivos previamente cifrados (pero no búferes de datos protegidos) pertenecientes a la aplicación. No se descifran los archivos de ubicaciones públicas en sdcard que no pertenecen directamente a la aplicación (por ejemplo, las carpetas de descarga o de documentos).
* No se cifrarán los nuevos archivos ni los búferes de datos protegidos que haya creado el método receptor (o cualquier otro código que se ejecute después de que se inicie el receptor).
* La aplicación todavía tiene acceso a las claves de cifrado, por lo que operaciones tales como los búferes de datos de descifrado se realizarán correctamente.

Una vez que se devuelve el receptor de la aplicación, ya no tendrá acceso a las claves de cifrado.

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

* **Authority** es la autoridad de AAD en uso. Si este valor está ausente, se usa el entorno público de AAD.
    > [!NOTE]
    > No establezca este campo si la aplicación tiene reconocimiento de nube soberana.

* **ClientID** es el ClientID de AAD (también conocido como identificador de aplicación) que se usará. Debe usar el ClientID de su propia aplicación si se registró con Azure AD. Si este valor está ausente, se usa un valor predeterminado de Intune.

* **NonBrokerRedirectURI** es el URI de direccionamiento de AAD para usar en casos sin agente. Si no se especifica ninguno, se usa el valor predeterminado de `urn:ietf:wg:oauth:2.0:oob`. Este valor predeterminado es adecuado para la mayoría de las aplicaciones.

    * Solo se usa NonBrokerRedirectURI cuando SkipBroker es "true".

* **SkipBroker** se usa para invalidar el comportamiento de participación predeterminado de SSO de ADAL. SkipBroker debe especificarse solo para las aplicaciones que especifican un ClientID **y** no admiten autenticación asincrónica/SSO en todos los dispositivos. En este caso debe establecerse en "true". En la mayoría de las aplicaciones no debe establecerse el parámetro SkipBroker.

    * Se **debe** especificar un ClientID en el manifiesto para especificar un valor de SkipBroker.

    * Cuando se especifica un ClientID, el valor predeterminado es "false".

    * Cuando SkipBroker es "true", se utilizará NonBrokerRedirectURI. Las aplicaciones que no integran ADAL (y, por lo tanto, no tienen ningún ClientID) también serán "true" de forma predeterminada.

### <a name="common-adal-configurations"></a>Opciones de configuración comunes de ADAL

A continuación se describen las maneras comunes en que se puede configurar una aplicación con ADAL. Busque la configuración de la aplicación y asegúrese de establecer los parámetros de metadatos de ADAL (que se explicaron anteriormente) en los valores necesarios. En todos los casos, la autoridad se puede especificar si se desea para entornos no predeterminados. Si no se especifica, se usará la autoridad de AAD de producción pública.

#### <a name="1-app-does-not-integrate-adal"></a>1. La aplicación no integra ADAL
**No debe** haber metadatos de ADAL en el manifiesto.

#### <a name="2-app-integrates-adal"></a>2. La aplicación integra ADAL

|Parámetro obligatorio de ADAL| Valor |
|--|--|
| ClientID | ClientID de la aplicación (que Azure AD genera cuando se registra la aplicación) |

En caso necesario, puede especificarse la autoridad.

Debe registrar su aplicación en Azure AD y darle acceso al servicio de directiva de protección de aplicaciones:
* Consulte [este artículo](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) para obtener información sobre cómo registrar una aplicación con Azure AD.
* Asegúrese de que se siguen los pasos para conceder los permisos de aplicación de Android para el servicio Directiva de protección de aplicaciones (APP). Siga las instrucciones de la [guía de introducción al SDK de Intune](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) sobre cómo conceder acceso al servicio Intune App Protection (opcional). 

Consulte también más adelante los requisitos para el [acceso condicional](#conditional-access).


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3. La aplicación integra ADAL pero no admite la autenticación intermediada o SSO en todo el dispositivo.

|Parámetro obligatorio de ADAL| Valor |
|--|--|
| ClientID | ClientID de la aplicación (que Azure AD genera cuando se registra la aplicación) |
| SkipBroker | **True** |

Se pueden especificar los valores de Authority y NonBrokerRedirectURI si resulta necesario.

### <a name="conditional-access"></a>Acceso condicional

El acceso condicional (CA) es una [característica](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer) de Azure Active Directory que puede usarse para controlar el acceso a recursos de AAD. [Los administradores de Intune pueden definir reglas de CA](https://docs.microsoft.com/intune/conditional-access) que permiten el acceso a los recursos únicamente desde dispositivos o aplicaciones administrados por Intune. Para asegurarse de que la aplicación sea capaz de acceder a los recursos cuando proceda, debe seguir los pasos que se incluyen más adelante. Si la aplicación no adquiere ningún token de acceso de AAD o accede solo a recursos que no se pueden proteger con CA, puede saltarse estos pasos.

1. Siga las [directrices de integración de ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library). 
   Vea especialmente el paso 11 para el uso del agente.
2. [Registre la aplicación con Azure Active Directory] (https://docs.microsoft.com/azure/active-directory/active-directory-app-registration). 
   El URI de redirección se puede encontrar en las directrices de integración de ADAL anteriores.
3. Establezca los parámetros de los metadatos del manifiesto de acuerdo con las [configuraciones comunes de ADAL](#common-adal-configurations) del punto 2 anterior.
4. Compruebe que todo esté configurado correctamente habilitando el [CA basado en dispositivos](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use) desde [Azure Portal](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2) y confirme lo siguiente:
    - El inicio de sesión en la aplicación solicita la instalación y la inscripción del Portal de empresa de Intune.
    - Tras la inscripción, el inicio de sesión en la aplicación se completa correctamente.
5. Una vez que la aplicación haya enviado la integración con el SDK para aplicaciones de Intune, póngase en contacto con msintuneappsdk@microsoft.com para que se agregue a la lista de aplicaciones aprobadas para el [acceso condicional basado en aplicación](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access).
6. Cuando la aplicación se haya agregado a la lista aprobada, realice la validación [configurando el CA basado en aplicación](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create) y asegurándose de que el inicio de sesión en la aplicación se completa correctamente.

## <a name="app-protection-policy-without-device-enrollment"></a>Directiva de protección de aplicaciones sin la inscripción de dispositivos

### <a name="overview"></a>Introducción
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

3. Cuando una cuenta de usuario se quita, la aplicación debe llamar a `unregisterAccountForMAM()` para quitar la cuenta de la administración de Intune.

    > [!NOTE]
    > Si un usuario cierra temporalmente la sesión de la aplicación, esta no necesita llamar a `unregisterAccountForMAM()`. La llamada puede iniciar una eliminación para quitar completamente los datos corporativos del usuario.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

Todas las API de autenticación y registro necesarias se pueden encontrar en la interfaz `MAMEnrollmentManager`. Se puede obtener una referencia a `MAMEnrollmentManager` de la manera siguiente:

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

Se garantiza que la instancia `MAMEnrollmentManager` devuelta no será nula. Los métodos de API se dividen en dos categorías: **autenticación** y **registro de cuenta**.

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
    void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
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

1. La aplicación debe implementar la interfaz `MAMServiceAuthenticationCallback` para permitir que el SDK solicite un token ADAL para el identificador de recurso y usuario determinado. La instancia de devolución de llamada se debe proporcionar a `MAMEnrollmentManager` llamando a su método `registerAuthenticationCallback()`. Puede que se necesite un token en una etapa temprana del ciclo de vida de la aplicación para reintentar la inscripción o para las inserciones en el repositorio de las actualizaciones de la directivas de protección de aplicaciones, de modo que el lugar perfecto para registrar la devolución de llamada es en el método `onMAMCreate()` de la subclase `MAMApplication` de la aplicación.

2. El método `acquireToken()` debe adquirir el token de acceso para el identificador de recurso solicitado del usuario determinado. Si no puede adquirir el token solicitado, debe devolver un valor nulo.

    > [!NOTE]
    > Asegúrese de que la aplicación utiliza los parámetros `resourceId` y `aadId` que se pasaron a `acquireToken()` para que se obtenga el token correcto.

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
            return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. En aso de que la aplicación no pueda proporcionar un token cuando el SDK llama a `acquireToken()`, por ejemplo, si la autenticación silenciosa genera un error y no es un momento adecuado para mostrar una interfaz e usuario, la aplicación puede proporcionar un token más adelante llamando al método `updateToken()`. El mismo identificador de recurso, identificador de AAD y UPN que solicitó la llamada anterior a `acquireToken()` se deben transmitir a `updateToken()`, junto con el token que se adquirió al final. La aplicación debe llamar a este método tan pronto como sea posible después de devolver un valor nulo a partir de la devolución de llamada proporcionada.

    > [!NOTE]
    > El SDK llamará a `acquireToken()` de forma periódica para obtener el token, por lo que no es estrictamente necesario llamar a `updateToken()`. Pero es muy recomendable, ya que puede ayudar a que los registros de las directivas de protección de aplicaciones y las inscripciones se completen de manera puntual.


### <a name="account-registration"></a>Registro de la cuenta

En esta sección se describen los métodos de API para el registro de la cuenta en `MAMEnrollmentManager` y cómo usarlos.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. Para registrar una cuenta para administración, la aplicación debe llamar a `registerAccountForMAM()`. Una cuenta de usuario se identifica mediante su UPN y su identificador de usuario de AAD. El identificador de inquilino también es obligatorio para asociar los datos de inscripción con el inquilino de AAD del usuario. También se puede proporcionar la entidad del usuario para permitir la inscripción en nubes soberanas específicas; para más información, vea [Registro de nube soberana](#sovereign-cloud-registration).  El SDK puede intentar inscribir la aplicación del usuario en cuestión en el servicio MAM; si se produce un error en la inscripción, se reintentará periódicamente hasta que se anule el registro de la cuenta. El período de reintento suele ser de 12 a 24 horas. El SDK proporciona el estado de los intentos de inscripción de manera asincrónica a través de las notificaciones.

2. Como se requiere autenticación de AAD, el mejor momento para registrar la cuenta de usuario es después de que el usuario haya iniciado sesión en la aplicación y se haya autenticado satisfactoriamente con ADAL. El identificador de inquilino y el identificador de AAD del usuario se devuelven con la llamada de autenticación de ADAL como parte del objeto [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android).
    * El identificador de inquilino proviene del método `AuthenticationResult.getTenantID()`.
    * La información sobre el usuario se encuentra en un objeto secundario de tipo `UserInfo` que proviene de `AuthenticationResult.getUserInfo()`, mientras que el identificador de usuario de AAD se recupera desde ese objeto llamando a `UserInfo.getUserId()`.

3. Para anular el registro de una cuenta desde la administración de Intune, la aplicación debe llamar a `unregisterAccountForMAM()`. Si la cuenta se registró correctamente y está administrada, el SDK anulará la inscripción de la cuenta y borrará sus datos. Se detendrán los reintentos de inscripción periódicos de la cuenta. El SDK proporciona el estado de la solicitud no inscrita de manera asincrónica a través de notificaciones.

### <a name="sovereign-cloud-registration"></a>Registro de nube soberana

Las aplicaciones con [reconocimiento de nube soberana](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud) **deben** proporcionar el elemento `authority` a `registerAccountForMAM()`.  Esto puede obtenerse proporcionando `instance_aware=true` en acquireToken extraQueryParameters de ADAL [1.14.0+](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) e invocando luego `getAuthority()` en AuthenticationCallback AuthenticationResult.

```java
mAuthContext.acquireToken(this, RESOURCE_ID, CLIENT_ID, REDIRECT_URI, PromptBehavior.FORCE_PROMPT, "instance_aware=true",
        new AuthenticationCallback<AuthenticationResult>() {
            @Override
            public void onError(final Exception exc) {
                // authentication failed
            }

            @Override
            public void onSuccess(final AuthenticationResult result) {
                mAuthority = result.getAuthority();
                // handle other parts of the result
            }
        });
```

> [!NOTE]
> No establezca el elemento de metadatos `com.microsoft.intune.mam.aad.Authority` en AndroidManifest.xml.

> [!NOTE]
> Asegúrese de que la autoridad se haya configurado correctamente el método `MAMServiceAuthenticationCallback::acquireToken()`.

#### <a name="currently-supported-sovereign-clouds"></a>Nubes soberanas admitidas actualmente

1. Arlington

### <a name="important-implementation-notes"></a>Notas de implementación importantes

#### <a name="authentication"></a>Autenticación

* Cuando la aplicación llama a `registerAccountForMAM()`, puede recibir una devolución de llamada en su interfaz `MAMServiceAuthenticationCallback` poco después, en un subproceso distinto. Idealmente, la aplicación ha adquirido su propio token desde ADAL antes de registrar la cuenta para acelerar la adquisición del token solicitado. Si la aplicación devuelve un token válido desde la devolución de llamada, la inscripción seguirá y la aplicación obtendrá el resultado final a través de una notificación.

* Si la aplicación no devuelve un token AAD válido, el resultado final del intento de inscripción será `AUTHENTICATION_NEEDED`. Si la aplicación recibe este resultado a través de una notificación, se recomienda encarecidamente acelerar el proceso de inscripción adquiriendo el token para el usuario y el recurso previamente solicitado de `acquireToken()` y llamando al método `updateToken()` para iniciar de nuevo el proceso de inscripción.

* También se llamará al elemento `MAMServiceAuthenticationCallback` registrado de la aplicación para adquirir un token para los registros periódicos de actualizaciones de las directivas de protección de aplicaciones. Si la aplicación no puede proporcionar un token cuando se solicita, no recibirá una notificación sino que tendrá que intentar adquirir un token y llamar a `updateToken()` en el próximo momento conveniente para acelerar el proceso de registro. Si no se proporciona un token, de todos modos se realizará la devolución de llamada en el próximo intento de registro.

* Para la compatibilidad con nubes soberanas, se debe proporcionar la autoridad.

#### <a name="registration"></a>Registro

* Para mayor comodidad, los métodos de registro son idempotentes; por ejemplo, `registerAccountForMAM()` solo registrará una cuenta e intentará inscribir la aplicación si la cuenta todavía no está registrada y `unregisterAccountForMAM()` solo anulará el registro de una cuenta si está registrada actualmente. Las llamadas subsiguientes no son operativas, por lo que no afecta llamar a estos métodos más de una vez. Adicionalmente, no se garantiza la correspondencia entre las llamadas a estos métodos y las notificaciones de los resultados; es decir, si se llama a `registerAccountForMAM` para una identidad que ya está registrada, es posible que no se envíe nuevamente la notificación para esa identidad. Es posible que las notificaciones que se envíen no correspondan a ninguna llamada a estos métodos, dado que el SDK puede intentar inscripciones de forma periódica en segundo plano, y las anulaciones de las inscripciones se puede desencadenar debido a las solicitudes de eliminación que se reciben desde el servicio Intune.

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

Se llama a este método antes de que el SDK muestre la interfaz de usuario de bloqueo predeterminada. Si la aplicación cambia la identidad de la actividad o anula el registro del usuario que intentó la inscripción, el SDK no bloqueará la actividad. En esta situación, es tarea de la aplicación evitar la pérdida de los datos corporativos. Solo las aplicaciones de varias identidades (que se describirán más adelante) podrán cambiar la identidad de la actividad.

Si no se hereda explícitamente `MAMActivity` (porque las herramientas de compilación harán ese cambio), pero aun así necesita controlar esta notificación, puede implementar `MAMActivityBlockingListener` en su lugar.

### <a name="notifications"></a>Notificaciones

Si la aplicación se registra para recibir notificaciones de tipo **MAM_ENROLLMENT_RESULT**, se enviará una `MAMEnrollmentNotification` para informar a la aplicación de que se ha completado la solicitud de inscripción. `MAMEnrollmentNotification` se recibirá a través de la interfaz `MAMNotificationReceiver`, tal como se describe en la sección [Registrarse para recibir notificaciones del SDK](#register-for-notifications-from-the-sdk).

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

El método `getEnrollmentResult()` devuelve el resultado de la solicitud de inscripción.  Como `MAMEnrollmentNotification` extiende `MAMUserNotification`, también está disponible la identidad del usuario para quien se intentó la inscripción. La aplicación debe implementar la interfaz `MAMNotificationReceiver` para recibir estas notificaciones, lo que se detalla en la sección [Registrarse para recibir notificaciones del SDK](#register-for-notifications-from-the-sdk).

El estado de la cuenta de usuario registrado puede cambiar cuando se recibe una notificación de inscripción, pero no se modificará en todos los casos (por ejemplo, si la notificación `AUTHORIZATION_NEEDED` se recibe después de un resultado mucho más informativo como `WRONG_USER`, el resultado más informativo se conservará como estado de la cuenta).  Cuando la cuenta se haya inscrito correctamente, el estado permanecerá como `ENROLLMENT_SUCCEEDED` hasta que la cuenta se anule o se borre.

El estado de la cuenta de usuario registrado puede cambiar cuando se recibe una notificación de inscripción, pero no se modificará en todos los casos (por ejemplo, si la notificación `AUTHORIZATION_NEEDED` se recibe después de un resultado mucho más informativo como `WRONG_USER`, el resultado más informativo se conservará como estado de la cuenta).  Cuando la cuenta se haya inscrito correctamente, el estado permanecerá como `ENROLLMENT_SUCCEEDED` hasta que la cuenta se anule o se borre.

## <a name="app-ca-with-policy-assurance"></a>CA de APP con control de directivas

### <a name="overview"></a>Introducción
Con CA (acceso condicional) de APP con control de directivas, el acceso a los recursos está condicionado a la aplicación de directivas de Intune App Protection.  Para aplicarlo, AAD requiere que APP inscriba y administre la aplicación antes de conceder un token para acceder a un recurso protegido de CA de APP con control de directivas.  La aplicación debe usar el agente de ADAL para la adquisición de tokens y la instalación es igual a la descrita anteriormente en [Acceso condicional](#conditional-access)

### <a name="adal-changes"></a>Cambios en ADAL
La biblioteca ADAL tiene un nuevo código de error que informa a la aplicación de que la imposibilidad de adquirir un token se debe al incumplimiento con la administración de aplicaciones.  Si la aplicación recibe este código de error, debe llamar al SDK para intentar corregir el problema de cumplimiento inscribiendo la aplicación y la directiva de aplicación. El método `onError()` del `AuthenticationCallback` de ADAL recibirá una excepción que tendrá el código de error `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`.  En este caso, la excepción se puede convertir en un `IntuneAppProtectionPolicyRequiredException`, del que se pueden extraer parámetros adicionales para su uso en la corrección de cumplimiento (vea el ejemplo de código siguiente). Una vez que la corrección se realiza, la aplicación puede volver a intentar la adquisición del token mediante ADAL.

> [!NOTE]
> Este nuevo código de error y otra compatibilidad con CA de APP con control de directivas requieren la versión 1.15.0 (o superior) de la biblioteca ADAL.

### <a name="mamcompliancemanager"></a>MAMComplianceManager

La interfaz `MAMComplianceManager` se utiliza cuando se recibe el error de directiva obligatoria de ADAL.  Contiene el método `remediateCompliance()` al que hay que llamar para intentar poner la aplicación en un estado de cumplimiento. Se puede obtener una referencia a `MAMComplianceManager` de la manera siguiente:

```java
MAMComplianceManager mgr = MAMComponents.get(MAMComplianceManager.class);

// make use of mgr
```

Se garantiza que la instancia `MAMComplianceManager` devuelta no será nula.

```java
package com.microsoft.intune.mam.policy;

public interface MAMComplianceManager {
    void remediateCompliance(String upn, String aadId, String tenantId, String authority, boolean showUX);
}
```

Se llama al método `remediateCompliance()` para intentar poner la aplicación en administración a fin de cumplir las condiciones para que AAD conceda el token solicitado.  Se pueden extraer los cuatro primeros parámetros de la excepción recibida por el método `AuthenticationCallback.onError()` de ADAL (vea el ejemplo de código siguiente).  El último parámetro es un valor booleano que controla si se muestra una experiencia de usuario durante el intento de cumplimiento.  Se trata de una sencilla interfaz de tipo de bloqueo de progreso que se ofrece de forma predeterminada para aplicaciones que no tienen que mostrar una experiencia de usuario personalizada durante esta operación.  Solo se bloqueará mientras se esté realizando la corrección de cumplimiento y no mostrará el resultado final.  La aplicación debe registrar un receptor de notificación para controlar el éxito o error del intento de corrección de cumplimiento (ver más adelante).

El método `remediateCompliance()` puede realizar una inscripción de MAM como parte del establecimiento del cumplimiento.  La aplicación puede recibir una notificación de inscripción si ha registrado un receptor de notificación para las notificaciones de inscripción.  El `MAMServiceAuthenticationCallback` registrado de la aplicación hará que se llame a su método `acquireToken()` para obtener un token para la inscripción de MAM. Se llamará a `acquireToken()` antes de que la aplicación haya adquirido su propio token, por lo que es posible que las tareas de creación de cuentas o contabilidad que la aplicación realice después de una adquisición correcta de token no se hayan realizado todavía.  La devolución de llamada debe poder adquirir un token en este caso.  Si no se puede devolver un token de `acquireToken()`, se producirá un error en el intento de corrección de cumplimiento.  Si se llama a `updateToken()` más adelante con un token válido para el recurso solicitado, la corrección de cumplimiento se volverá a intentar inmediatamente con el token especificado.

> [!NOTE]
> La adquisición silenciosa del token todavía será posible en `acquireToken()` porque ya se habrá indicado al usuario que instale el agente y registre el dispositivo antes de que se reciba el error `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`.  Esto hace que el agente tenga un token de actualización válido en su caché, lo que permite realizar correctamente la adquisición silenciosa del token solicitado.

Este es un ejemplo de recepción del error de directiva obligatoria en el método `AuthenticationCallback.onError()` y llamada a la `MAMComplianceManager` para controlar el error.

```java
public void onError(@Nullable Exception exc) {
    if (exc instanceof AuthenticationException && 
        ((AuthenticationException) exc).getCode() == ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED) {

        final IntuneAppProtectionPolicyRequiredException policyRequiredException = 
            (IntuneAppProtectionPolicyRequiredException) ex;

        final String upn = policyRequiredException.getAccountUpn();
        final String aadId = policyRequiredException.getAccountUserId();
        final String tenantId = policyRequiredException.getTenantId();
        final String authority = policyRequiredException.getAuthorityURL();

        MAMComplianceManager complianceManager = MAMComponents.get(MAMComplianceManager.class);
        complianceManager.remediateCompliance(upn, aadId, tenantId, authority, showUX);
    }
}
```

### <a name="status-notifications"></a>Notificaciones de estado

Si la aplicación se registra para recibir notificaciones de tipo **COMPLIANCE_STATUS**, se enviará una `MAMComplianceNotification` para informar a la aplicación del estado final del intento de corrección de cumplimiento. `MAMComplianceNotification` se recibirá a través de la interfaz `MAMNotificationReceiver`, tal como se describe en la sección [Registrarse para recibir notificaciones del SDK](#register-for-notifications-from-the-sdk).

```java
public interface MAMComplianceNotification extends MAMUserNotification {
    MAMCAComplianceStatus getComplianceStatus();
    String getComplianceErrorTitle();
    String getComplianceErrorMessage();
}
```

El método `getComplianceStatus()` devuelve el resultado del intento de corrección de cumplimiento como valor de la enumeración `MAMCAComplianceStatus`.

|Código de estado | Explicación |
| -- | -- |
| UNKNOWN | Se desconoce el estado de conexión. Esto podría indicar un motivo de error inesperado. Puede encontrar información adicional en los registros del Portal de empresa. |
| COMPLIANT | La corrección de cumplimiento se ha realizado correctamente y la aplicación ya es compatible con la directiva. Debe reintentarse la adquisición de tokens ADAL. |
| NOT_COMPLIANT | El intento de corrección de cumplimiento no se ha realizado.  La aplicación no es compatible y no se debe reintentar la adquisición de tokens ADAL hasta que se corrija la condición de error.  Se envía información de error adicional con MAMComplianceNotification. |
| SERVICE_FAILURE | Se produjo un error al intentar recuperar datos de cumplimiento del servicio Intune. Puede encontrar información adicional en los registros del Portal de empresa. |
| NETWORK_FAILURE | Se produjo un error al conectarse al servicio Intune. La aplicación debería intentar la adquisición de tokens de nuevo cuando se restaure la conexión de red. |
| CLIENT_ERROR | El intento de corrección de cumplimiento no se ha realizado por algún motivo relacionado con el cliente.  Por ejemplo, ningún token o usuario incorrecto. Se envía información de error adicional con MAMComplianceNotification. |
| PENDING | El intento de corrección de cumplimiento no se ha realizado porque aún no se había recibido la respuesta de estado del servicio cuando se superó el límite de tiempo. La aplicación debería volver a intentar la adquisición de tokens más tarde. |
| COMPANY_PORTAL_REQUIRED | El Portal de empresa debe estar instalado en el dispositivo para que la corrección de cumplimiento se realice correctamente.  Si el Portal de empresa ya está instalado en el dispositivo, debe reiniciarse la aplicación.  En este caso, se mostrará un cuadro de diálogo que pide al usuario que reinicie la aplicación. |

Si el estado de cumplimiento es `MAMCAComplianceStatus.COMPLIANT`, la aplicación debe volver a iniciar la adquisición de tokens original (para su propio recurso). Si el intento de corrección de cumplimiento no se ha realizado, los métodos `getComplianceErrorTitle()` y `getComplianceErrorMessage()` devolverán las cadenas localizadas que la aplicación puede mostrar al usuario final, si así lo decide.  La mayoría de los casos de error no los puede solucionar la aplicación, por lo que en general puede ser mejor no crear la cuenta o no iniciar sesión y permitir que el usuario vuelva a intentarlo más tarde.  Si un error persiste, los registros MAM pueden ayudar a determinar la causa.  El usuario final puede enviar los registros siguiendo las instrucciones que se indican [aquí](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "Enviar registros al equipo de soporte técnico de su empresa por correo electrónico").

Como `MAMComplianceNotification` extiende `MAMUserNotification`, también está disponible la identidad del usuario para el que se ha intentado la inscripción.

Este es un ejemplo de registro de un receptor con una clase anónima para implementar la interfaz MAMNotificationReceiver:

```java
final MAMNotificationReceiverRegistry notificationRegistry = MAMComponents.get(MAMNotificationReceiverRegistry.class);
// create a receiver
final MAMNotificationReceiver receiver = new MAMNotificationReceiver() {
    public boolean onReceive(MAMNotification notification) {
        if (notification.getType() == MAMNotificationType.COMPLIANCE_STATUS) {
            MAMComplianceNotification complianceNotification = (MAMComplianceNotification) notification;
            
            // take appropriate action based on complianceNotification.getComplianceStatus()
            
            // unregister this receiver if no longer needed
            notificationRegistry.unregisterReceiver(this, MAMNotificationType.COMPLIANCE_STATUS);
        }
        return true;
    }
};
// register the receiver
notificationRegistry.registerReceiver(receiver, MAMNotificationType.COMPLIANCE_STATUS);
```

> [!NOTE]
> El receptor de la notificación debe registrarse antes de llamar a `remediateCompliance()` para evitar una condición de carrera que pueda hacer que no se reciba la notificación.

### <a name="implementation-notes"></a>Notas de implementación

> [!NOTE]
> El método `MAMServiceAuthenticationCallback.acquireToken()` de la aplicación debe pasar *true* con la nueva marca `forceRefresh` a `acquireTokenSilentSync()` para forzar una actualización del agente.  Esto sirve para solucionar un problema de almacenamiento en caché con tokens en ADAL que puede afectar a tokens del servicio MAM. En general, tendrá este aspecto:
>
> ```java
> AuthenticationResult result = acquireTokenSilentSync(resourceId, clientId, userId, /* forceRefresh */ true);
> ```

> [!NOTE]
> Si quiere mostrar una experiencia de usuario de bloqueo personalizada durante el intento de corrección, debería pasar *false* con el parámetro showUX a `remediateCompliance()`. Debe asegurarse de que se muestra la experiencia de usuario y se registra el cliente de escucha de notificaciones antes de llamar a `remediateCompliance()`.  Esto evitará una condición de carrera en la que podría faltar la notificación si `remediateCompliance()` no se realiza muy rápidamente.  Por ejemplo, el método `onCreate()` o `onMAMCreate()` de una subclase Activity es el lugar ideal para registrar el cliente de escucha de notificaciones y luego llamara a `remediateCompliance()`.  Los parámetros de `remediateCompliance()` pueden pasarse a la experiencia de usuario como extras de intención.  Cuando se recibe la notificación de estado de cumplimiento, se puede mostrar el resultado o simplemente finalizar la actividad.

> [!NOTE]
> `remediateCompliance()` registrará la cuenta e intentará la inscripción.  Una vez adquirido el token principal, no es necesario llamar a `registerAccountForMAM()`, pero no hay ningún inconveniente en hacerlo. Por otro lado, si la aplicación no puede adquirir el token y quiere quitar la cuenta de usuario, debe llamar a `unregisterAccountForMAM()` para quitar la cuenta y evitar que se produzcan reintentos de inscripción en segundo plano.

## <a name="protecting-backup-data"></a>Proteger los datos de copia de seguridad

En lo referente a la versión Android Marshmallow (API 23), el sistema Android tiene dos formas para que una aplicación pueda hacer una copia de seguridad de sus datos. Cada opción está disponible para la aplicación y requiere pasos diferentes para garantizar que la protección de datos de Intune está correctamente implementada. Puede revisar la siguiente tabla sobre las acciones correspondientes necesarias para el comportamiento de protección de datos correcto.  Lea más acerca de los métodos de copia de seguridad en la [guía de API de Android](https://developer.android.com/guide/topics/data/backup.html).

### <a name="auto-backup-for-apps"></a>Copia de seguridad automática de aplicaciones

Android comenzó a ofrecer [copias de seguridad completas automática](https://developer.android.com/guide/topics/data/autobackup.html) a Google Drive para aplicaciones en dispositivos Android Marshmallow, con independencia de la API de destino de la aplicación. En el archivo AndroidManifest.xml, si establece explícitamente `android:allowBackup` a **false**, la aplicación nunca se pondrán en cola para las copias de seguridad de Android y los datos "corporativos" permanecerán dentro de la aplicación. En este caso, no se necesita ninguna acción.

Sin embargo, de forma predeterminada el atributo `android:allowBackup` se establece en true, incluso si `android:allowBackup` no se especifica en el archivo de manifiesto. Esto significa que todos los datos de la aplicación se copian automáticamente en la cuenta de Google Drive del usuario, un comportamiento predeterminado que plantea un **riesgo de pérdida de datos**. Por lo tanto, el SDK requiere los cambios que se describen a continuación para tener la seguridad de que se aplica la protección de datos.  Si quiere que su aplicación se ejecute en dispositivos de Android Marshmallow, es importante seguir las directrices que se indican a continuación para proteger los datos del cliente de la manera adecuada.  

Intune le permite utilizar todas las [características de copia de seguridad automática](https://developer.android.com/guide/topics/data/autobackup.html) disponibles en Android, como la posibilidad de definir reglas personalizadas en XML, pero debe seguir los pasos siguientes para proteger los datos:

1. Si la aplicación **no** usa su propio BackupAgent, use el valor predeterminado de MAMBackupAgent para permitir copias de seguridad completas automáticas que sean compatibles con la directiva de Intune. Coloque lo siguiente en el manifiesto de aplicación:

    ```xml
    android:fullBackupOnly="true"
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

1. Lea detenidamente la sección [Key/Value Backup](https://developer.android.com/guide/topics/data/keyvaluebackup.html) (Copia de seguridad de clave-valor) y en concreto [Extending BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) (Extensión de BackupAgent) de la guía de Android para garantizar que la implementación de BackupAgent sigue las instrucciones de Android.

2. Haga que la clase extienda `MAMBackupAgent`.

**Copia de seguridad de varias identidades:**

1. Antes de comenzar la copia de seguridad, compruebe que los búferes de datos o archivos de los que planea realizar una copia de seguridad están permitidos por **el administrador de TI para crear copias de seguridad** en escenario con varias identidades. Le proporcionamos la función `isBackupAllowed` en `MAMFileProtectionManager` y `MAMDataProtectionManager` para determinar esto. Si no puede hacer la copia de seguridad del búfer de datos o de archivos, no debe seguir incluyéndolos en la copia de seguridad.

2. Si quiere realizar una copia de seguridad de las identidades de los archivos que registró en el paso 1 mientras realiza la copia de seguridad, debe llamar a `backupMAMFileIdentity(BackupDataOutput data, File … files)` con los archivos de los que planea extraer datos. Esto creará automáticamente nuevas entidades de copia de seguridad y las escribirá en `BackupDataOutput` . Estas entidades se consumirán automáticamente durante la restauración.

**Restauración de varias identidades:**

La guía sobre la copia de seguridad de datos especifica un algoritmo general para restaurar los datos de la aplicación y proporciona un ejemplo de código en la sección [Extensión de BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent). Para realizar una restauración correcta de varias identidades, debe seguir la estructura general que se proporciona en este ejemplo de código y prestar especial atención a lo siguiente:

1. Debe utilizar un bucle `while(data.readNextHeader())`* para avanzar por las entidades de la copia de seguridad.

2. Debe llamar a `data.skipEntityData()`* si `data.getKey()`* no coincide con la clave que escribió en `onBackup`. Si no realiza este paso, las restauraciones podrían no realizarse correctamente.

3. Evite la devolución cuando se están usando las entidades de copia de seguridad en la construcción `while(data.readNextHeader())`*, puesto que se perderán las entidades que se escriben automáticamente.

* Donde `data` es el nombre de variable local para **BackupDataInput** que se pasa a la aplicación tras la restauración.

## <a name="multi-identity-optional"></a>Varias identidades (opcional)

### <a name="overview"></a>Introducción
De forma predeterminada, el SDK para aplicaciones de Intune aplicará la directiva a la aplicación en su conjunto. Varias identidades es una característica de protección de aplicaciones de Intune opcional que se puede habilitar para permitir que se aplique una directiva en un nivel por identidad. Para ello es necesaria más participación en la aplicación que otras características de la protección de la aplicación.

> [!NOTE]
> Si la participación de la aplicación correcta no se da, puede haber fugas de datos y otros problemas de seguridad.

Una vez que el usuario inscriba el dispositivo o la aplicación, el SDK registra esta identidad y la considera la identidad administrada principal de Intune. Los demás usuarios de la aplicación se tratarán como usuarios no administrados con una configuración de directiva sin restricciones.

> [!NOTE]
> Actualmente, solo se admite una identidad administrada de Intune por dispositivo.

Una identidad se define como una cadena. Las identidades **no distinguen mayúsculas de minúsculas** y las solicitudes de identidades que se realizan al SDK podrían no devolverse con el mismo uso de mayúsculas y minúsculas que se empleó originalmente al establecer la identidad.

La aplicación *debe* informar al SDK cuando intente cambiar la identidad activa. En algunos casos, el SDK también notificará a la aplicación cuando se requiera un cambio de identidad. Sin embargo, en la mayoría de los casos, MAM no puede saber cuáles son los datos que se muestran en la UI ni los que se usan en un subproceso en un momento determinado y confía en que la aplicación establezca la identidad correcta a fin de evitar fugas de datos. En las secciones siguientes se detallarán algunos escenarios determinados que requieren acción de la aplicación.

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
  2. Nivel `Context` (generalmente `Activity`)
  3. Nivel de proceso

Una identidad que se establece en el nivel de subproceso sustituye a una identidad que se establece en el nivel `Context`, la cual reemplaza a una identidad que se establece en el nivel de proceso. Una identidad que se establece en un elemento `Context` solo se usa en escenarios asociados adecuados. Las operaciones de E/S de archivos, por ejemplo, no tienen un elemento `Context` asociado. Habitualmente, las aplicaciones establecerán la identidad `Context` en un objeto `Activity`. Una aplicación *no debe* mostrar los datos de una identidad administrada a menos que la identidad de `Activity` se establezca en la misma identidad. En general, la identidad de nivel de proceso resulta útil solo si la aplicación funciona con un usuario a la vez en todos los subprocesos. Es posible que muchas aplicaciones no necesiten usar esto.

Si la aplicación usa el contexto `Application` para adquirir servicios del sistema, asegúrese de que se haya establecido la identidad del proceso o subproceso, o bien de que ha establecido la identidad de la interfaz de usuario en el contexto `Application` de la aplicación.

Para controlar casos especiales al actualizar la identidad de la interfaz de usuario con `setUIPolicyIdentity` o `switchMAMIdentity`, se puede pasar un conjunto de valores `IdentitySwitchOption` a ambos métodos.

* `IGNORE_INTENT`: se usa si se solicita un cambio de identidad que debe ignorar la intención asociada a la actividad actual.
  Por ejemplo:

  1. La aplicación recibe una intención de una identidad administrada que contiene un documento administrado, y la aplicación muestra el documento.
  2. El usuario cambia a su identidad personal, por lo que la aplicación solicita un cambio de identidad de la interfaz de usuario. En la identidad personal, la aplicación ya no muestra el documento, por lo que se usa `IGNORE_INTENT` al solicitar el cambio de identidad.

  Si no se establece, el SDK supondrá que aún se utiliza la intención más reciente en la aplicación. Esto hará que la directiva de recepción de la nueva identidad trate la intención como datos entrantes y utilice su identidad.

>[!NOTE]
> Dado que el `CLIPBOARD_SERVICE` se usa en las operaciones de interfaz de usuario, el SDK usa la identidad de la interfaz de usuario de la actividad de primer plano en las operaciones `ClipboardManager`.
> Se pueden usar los métodos siguientes en `MAMPolicyManager` para establecer la identidad y recuperar los valores de identidad previamente establecidos.

```java
  public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

/**
   * Get the current app policy. This does NOT take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use the overload below.
   */
  public static AppPolicy getPolicy();

  /**
  * Get the current app policy. This DOES take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use this function.
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
| NOT_ALLOWED  | No se permite el cambio de identidad. Esto sucede si se intenta establecer la identidad de la interfaz de usuario (contexto) cuando hay una identidad diferente establecida en el subproceso actual. |
| CANCELLED | El usuario canceló el cambio de identidad, por lo general presionando el botón Atrás en un mensaje de autenticación o solicitud del PIN. |
| FAILED | No se pudo realizar el cambio de identidad por una razón específica.|

La aplicación debe garantizar que un cambio de identidad se realice correctamente antes de mostrar o usar datos corporativos. Actualmente, los cambios de identidad de proceso y subproceso siempre se realizarán correctamente para una aplicación compatible con varias identidades. Sin embargo, nos reservamos el derecho a agregar condiciones de error. El cambio de identidad de UI podría presentar un error si los argumentos no son válidos, si entrara en conflicto con la identidad de subproceso o si el usuario cancelara los requisitos de inicio condicional (por ejemplo, si presiona el botón Atrás en la pantalla del PIN).


En el caso de establecer una identidad de contexto, el resultado se notifica de forma asincrónica. Si el contexto es una actividad, el SDK no sabe si el cambio de identidad se realizó correctamente hasta después de realizar el inicio condicional, lo que puede requerir que el usuario escriba un PIN o sus credenciales corporativas. Se espera que la aplicación implemente un elemento `MAMSetUIIdentityCallback` para recibir este resultado; además, puede pasar un valor null para este parámetro.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

También puede establecer la identidad de una actividad directamente a través de un método en `MAMActivity` en lugar de llamar a `MAMPolicyManager.setUIPolicyIdentity`. Para hacerlo, use el método siguiente:

```java
     public final void switchMAMIdentity(final String newIdentity, final EnumSet<IdentitySwitchOption> options);
```

También puede reemplazar un método en `MAMActivity` si desea que la aplicación reciba una notificación del resultado de los intentos de cambiar la identidad de esa actividad.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

Si no invalida `onSwitchMAMIdentityComplete` (o llama al método `super`), un cambio de identidad con errores en una actividad se traducirá en que la actividad finalice. Si invalida el método, debe tener cuidado de que los datos corporativos no se muestren después de un cambio de identidad con errores.

>[!NOTE]
> Puede que cambiar la identidad requiera volver a crear la actividad. En este caso, la devolución de llamada `onSwitchMAMIdentityComplete` se entregará a la nueva instancia de la actividad.


### <a name="implicit-identity-changes"></a>Cambios de identidad implícitos

Además de la posibilidad de que la aplicación establezca la identidad, un subproceso o la identidad de un contexto pueden cambiar en función de la entrada de datos desde otra aplicación administrada por Intune que tenga la directiva de protección de la aplicación.

#### <a name="examples"></a>Ejemplos

  1. Si una actividad se inicia desde un `Intent` enviado desde otra aplicación MAM, la identidad de la actividad se establecerá en función de la identidad efectiva de la otra aplicación en el punto en que se envió el `Intent`.

  2. En el caso de los servicios, la identidad del subproceso se establecerá de forma similar para la duración de una llamada `onStart` o `onBind`. Las llamadas a `Binder` devueltas por `onBind` también establecerán temporalmente la identidad del subproceso.

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

    Donde ```AppIdentitySwitchResult``` es `SUCCESS` o `FAILURE`.

Al método `onMAMIdentitySwitchRequired` se le llama para todos los cambios de identidad implícitos, excepto aquellos realizados a través de un enlazador devueltos por `MAMService.onMAMBind`. Las implementaciones predeterminadas de `onMAMIdentitySwitchRequired` llaman inmediatamente a:

* `reportIdentitySwitchResult(FAILURE)` cuando el motivo es `RESUME_CANCELLED`.

* `reportIdentitySwitchResult(SUCCESS)` en todos los demás casos.

  Lo normal es que la mayoría de las aplicaciones no tengan que bloquear o retrasar un cambio de identidad de una manera diferente, pero en caso de hacerlo, se deben tener en cuenta los siguientes puntos:

  * Si se bloquea un cambio de identidad, el resultado es el mismo que si la configuración de uso compartido `Receive` hubiera prohibido la entrada de datos.

  * Si un servicio se ejecuta en el subproceso principal, se **debe** llamar a `reportIdentitySwitchResult` de forma sincrónica o se bloqueará el subproceso de IU.

  * Para la creación de **`Activity`** , se llamará a `onMAMIdentitySwitchRequired` antes que a `onMAMCreate`. Si la aplicación debe mostrar la interfaz de usuario para determinar si se permite el cambio de identidad, esa interfaz de usuario se debe mostrar mediante una actividad *diferente*.

  * En un elemento **`Activity`** , cuando se solicita un cambio a la identidad vacía con el motivo `RESUME_CANCELLED`, la aplicación debe modificar la actividad reanudada para mostrar datos coherentes con ese cambio de identidad.  Si esto no es posible, la aplicación debe rechazar el cambio y se pedirá al usuario que cumpla de nuevo la directiva de reanudar la identidad (por ejemplo, con la presentación de la pantalla de entrada del PIN de la aplicación).

    > [!NOTE]
    > Una aplicación de varias identidades siempre recibirá datos de entrada de aplicaciones tanto administradas como sin administrar. Es responsabilidad de la aplicación tratar los datos de identidades administradas de forma administrada.

  Si una identidad solicitada es administrada (use `MAMPolicyManager.getIsIdentityManaged` para comprobarlo), pero la aplicación no puede usar esa cuenta (por ejemplo, porque las cuentas, como las de correo electrónico, deben configurarse primero en la aplicación), el cambio de identidad se debe rechazar.

#### <a name="build-plugin--tool-considerations"></a>Consideraciones sobre las herramientas o el complemento de compilación
Si no hereda explícitamente de `MAMActivity`, `MAMService` o `MAMContentProvider` (porque permite que las herramientas de compilación realicen ese cambio), pero aun así necesita procesar cambios de identidad, en su lugar puede implementar `MAMActivityIdentityRequirementListener` (para un elemento `Activity`) o `MAMIdentityRequirementListener` (para `Service` o `ContentProviders`).
Se puede acceder al comportamiento predeterminado para `MAMActivity.onMAMIdentitySwitchRequired` mediante una llamada al método estático `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)`.

De forma similar, si tiene que invalidar `MAMActivity.onSwitchMAMIdentityComplete`, puede implementar `MAMActivityIdentitySwitchListener` sin heredar explícitamente de `MAMActivity`.

### <a name="preserving-identity-in-async-operations"></a>Conservar la identidad en operaciones asincrónicas
Es habitual que las operaciones en el subproceso de interfaz de usuario envíen tareas en segundo plano a otro subproceso. Una aplicación de varias identidades querrá asegurarse de que estas tareas en segundo plano funcionen con la identidad adecuada, que suele ser la misma que usa la actividad que las envió. El SDK de MAM proporciona `MAMAsyncTask` y `MAMIdentityExecutors` como una forma cómoda de conservar la identidad.
Deben usarse si la operación asincrónica puede escribir datos corporativos en un archivo o puede comunicarse con otras aplicaciones.

#### <a name="mamasynctask"></a>MAMAsyncTask

Para usar `MAMAsyncTask`, simplemente herede de ella en lugar de `AsyncTask` y reemplace las invalidaciones de `doInBackground` y `onPreExecute` con `doInBackgroundMAM` y `onPreExecuteMAM` respectivamente. El constructor `MAMAsyncTask` toma un contexto de actividad. Por ejemplo:

```java
  AsyncTask<Object, Object, Object> task = new MAMAsyncTask<Object, Object, Object>(thisActivity) {

    @Override
    protected Object doInBackgroundMAM(final Object[] params) {
        // Do operations.
    }

    @Override
    protected void onPreExecuteMAM() {
        // Do setup.
    };
```

### <a name="mamidentityexecutors"></a>MAMIdentityExecutors
`MAMIdentityExecutors` permite encapsular una instancia existente de `Executor` o `ExecutorService` como un `Executor`/`ExecutorService` de conservación de la identidad con métodos `wrapExecutor` y `wrapExecutorService`. Por ejemplo,

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```

### <a name="file-protection"></a>Protección de archivos

Cada archivo tiene una identidad asociada en el momento de creación basada en la identidad del proceso y del subproceso. Esta identidad se utilizará para el cifrado de archivos y la eliminación selectiva. Solo se cifrarán los archivos cuya identidad está administrada y tiene una directiva que exige cifrado. La eliminación de funcionalidad selectiva predeterminada del SDK solo eliminará los archivos asociados con la identidad administrada para la que se ha solicitado una eliminación. La aplicación puede consultar o cambiar la identidad de un archivo con la clase `MAMFileProtectionManager`.

```java
public final class MAMFileProtectionManager {

   /**
    * Protect a file or directory. This will synchronously trigger whatever protection is required for the file, and will tag the
    * file for future protection changes. If an identity is set on a directory, it is set recursively on all files and
    * subdirectories. New files or directories will inherit their parent directory's identity. If MAM is operating in offline mode,
    * this method will silently do nothing.
    *
    * @param identity
    *        Identity to set.
    * @param file
    *        File to protect.
    *
    * @throws IOException
    *         If the file cannot be protected.
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
     *            Identity to set.
     * @param file
     *            File to protect.
     *
     * @throws IOException
     *             If the file cannot be protected.
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
    public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;

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
  * El usuario selecciona un documento para abrirlo en la aplicación.
  * Durante el flujo de apertura, antes de leer los datos del disco, la aplicación confirma la identidad que se debe usar para mostrar el contenido
    * Información de MAMFileProtectionInfo = MAMFileProtectionManager.getProtectionInfo(docPath)
    * if(info)   MAMPolicyManager.setUIPolicyIdentity(activity, info.getIdentity(), callback)
    * La aplicación espera hasta que se informa un resultado para devolución de llamada
    * Si el resultado informado es un error, la aplicación no muestra el documento.
  * La aplicación abre y representa el archivo.
  
#### <a name="single-identity-to-multi-identity-transition"></a>Transición de identidad única a varias identidades
Si una aplicación que anteriormente se publicó con la integración de identidad única de Intune más adelante integra varias identidades, las aplicaciones instaladas previamente experimentarán una transición (no es visible para el usuario, no hay ninguna experiencia de usuario asociada). No se *requiere* que la aplicación haga nada explícito para controlar esta transición. Todos los archivos creados antes de la transición se seguirán considerando administrados (por lo que permanecerán cifrados si la directiva de cifrado está activa). Si quiere, puede detectar la actualización y usar `MAMFileProtectionManager.protect` para etiquetar determinados archivos o directorios con la identidad vacía (lo que eliminará el cifrado si estaban cifrados).

#### <a name="offline-scenarios"></a>Escenarios sin conexión

El etiquetado de identidad de archivo es sensible al modo sin conexión. Se deben tener en cuenta los siguientes puntos:

  * Si no está instalado el Portal de empresa, no se puede etiquetar la identidad de los archivos.

  * Si está instalado el Portal de empresa, pero la aplicación no tiene una directiva MAM de Intune, no se puede etiquetar la identidad de los archivos de forma confiable.

  * Cuando esté disponible el etiquetado de identidad de los archivos, todos los archivos creados anteriormente se tratan como personales o no administrados (que pertenecen a la identidad de cadena vacía), a menos que la aplicación se instalara anteriormente como una aplicación administrada de una única identidad, en cuyo caso se tratan como pertenecientes al usuario inscrito.

### <a name="directory-protection"></a>Protección de los directorios

Los directorios se pueden proteger con el mismo método `protect` que se usa para proteger los archivos. La protección de los directorios se aplica de forma recursiva a todos los archivos y subdirectorios contenidos en el directorio y a los archivos nuevos creados dentro del directorio. Como la protección de directorios se aplica de forma recursiva, la llamada de `protect` puede tardar un poco en completarse en el caso de directorios muy grandes. Por este motivo, las aplicaciones que aplican protección a un directorio que contiene una gran cantidad de archivos puede querer ejecutar `protect` de manera asincrónica en un subproceso en segundo plano.

### <a name="data-protection"></a>Protección de datos

No es posible etiquetar un archivo como perteneciente a varias identidades. Las aplicaciones que deben almacenar datos que pertenecen a distintos usuarios en el mismo archivo pueden hacerlo manualmente mediante las características proporcionadas por `MAMDataProtectionManager`. Esto permite que la aplicación cifre los datos y los asocie a un usuario determinado. Los datos cifrados son adecuados para almacenarse en disco en un archivo. Puede consultar los datos asociados con la identidad y descifrarlos más tarde.

Las aplicaciones que usan `MAMDataProtectionManager` deben implementar un receptor para la notificación `MANAGEMENT_REMOVED`. Una vez que se complete esta notificación, los búferes que se protegieron con esta clase ya no serán legibles si se habilitó el cifrado de archivos cuando los búferes estaban protegidos. Una aplicación puede corregir esta situación con una llamada a `MAMDataProtectionManager.unprotect` en todos los búferes durante esta notificación. También es seguro llamar a la protección durante esta notificación si se quiere conservar la información de identidad; se garantiza que el cifrado estará deshabilitado durante la notificación.


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

Si la aplicación proporciona datos corporativos distintos de `ParcelFileDescriptor` a través de un elemento `ContentProvider`, la aplicación debe llamar al método `isProvideContentAllowed(String)` de `MAMContentProvider` y transmitir el UPN (nombre principal de usuario) de la identidad del propietario para el contenido. Si esta función devuelve false, el contenido *no* se tiene que devolver al autor de la llamada. Los descriptores de archivo devueltos a través de un proveedor de contenido se administran automáticamente en función de la identidad del archivo.

Si no hereda `MAMContentProvider` explícitamente y en su lugar permite que la herramienta de compilación realice ese cambio, puede llamar a una versión estática del mismo método: `MAMContentProvider.isProvideContentAllowed(provider, contentIdentity)`.

### <a name="selective-wipe"></a>Eliminación selectiva

Si una aplicación de varias identidades se registra para la notificación `WIPE_USER_DATA`, es responsabilidad de la aplicación quitar todos los datos del usuario que se va a eliminar, incluidos todos los archivos con etiquetas de identidad que indiquen su pertenencia a dicho usuario. Si la aplicación quita datos de usuario de un archivo, pero desea dejar otros datos en el archivo, *debe* cambiar la identidad del archivo (mediante `MAMFileProtectionManager.protect` a un usuario personal o la identidad vacía). Si la directiva de cifrado está en uso, los archivos restantes que pertenezcan al usuario que se vaya a borrar no se descifrarán y la aplicación no podrá acceder a ellos tras el borrado.

Las aplicaciones que se registren para `WIPE_USER_DATA` no recibirán la ventaja del comportamiento de borrado selectivo predeterminado del SDK. En el caso de aplicaciones compatibles con varias identidades, esta pérdida puede tener un impacto más considerable dado que la eliminación selectiva predeterminada de MAM solo eliminará los archivos cuya identidad sea el destino de una eliminación. Si una aplicación compatible con varias identidades desea que se realice una eliminación selectiva predeterminada de MAM _**y**_ también desea realizar sus propias acciones en la eliminación, se debe registrar para recibir notificaciones `WIPE_USER_AUXILIARY_DATA`. El SDK enviará inmediatamente esta notificación antes de que realice la eliminación selectiva predeterminada de MAM. Una aplicación nunca debe registrarse para `WIPE_USER_DATA` y `WIPE_USER_AUXILIARY_DATA`.

El borrado selectivo predeterminado cerrará la aplicación correctamente, finalizando las actividades y terminando el proceso de aplicación. Si la aplicación invalida el borrado selectivo predeterminado, es posible que convenga cerrar la aplicación manualmente para evitar que el usuario acceda a datos en memoria después de que se produzca un borrado.


## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Habilitación de la configuración de destino de MAM para las aplicaciones Android (opcional)
Los pares clave-valor específicos de la aplicación se pueden configurar en la consola de Intune para [MAM-WE](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) y [aplicaciones del perfil de trabajo Android](https://docs.microsoft.com/intune/app-configuration-policies-use-android).
Intune no interpreta en absoluto los pares clave-valor, sino que se pasan a la aplicación. Las aplicaciones que desean recibir dicha configuración pueden usar las clases `MAMAppConfigManager` y `MAMAppConfig` para hacerlo. Si hay varias directivas dirigidas a la misma aplicación, puede haber varios valores en conflicto disponibles para la misma clave.

> [!NOTE] 
> Las configuraciones establecidas para la entrega a través de MAM-WE no se pueden entregar en `offline`.  En este caso, solo se entregará Android Enterprise AppRestrictions a través de un `MAMUserNotification` en una identidad vacía.

### <a name="example"></a>Ejemplo

```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
LOGGER.info("App Config Data = " + appConfig.getFullData());
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

### <a name="notification"></a>Notificación
La configuración de aplicación agrega un nuevo tipo de notificación:
* **REFRESH_APP_CONFIG**: esta notificación se envía en `MAMUserNotification` e informa a la aplicación que los datos de configuración de aplicación nuevos están disponibles.

### <a name="further-reading"></a>Lectura adicional
Para más información sobre las capacidades de Graph API, vea la [referencia de Graph API](https://developer.microsoft.com/graph/docs/concepts/overview). <br>

Para más información sobre cómo crear una directiva de configuración de aplicaciones de destino de MAM en Android, vea la sección de la configuración de aplicaciones de destino de MAM en [How to use Microsoft Intune app configuration policies for Android](https://docs.microsoft.com/intune/app-configuration-policies-use-android) (Uso de las directivas de configuración de aplicaciones de Microsoft Intune para Android).

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

## <a name="default-enrollment-optional"></a>Inscripción predeterminada (opcional)

La siguiente es una guía para el mensaje de Requerir usuario al iniciar la aplicación para una inscripción automática del servicio APP-WE (denominada**inscripción predeterminada** en esta sección), que requiere directivas de protección de aplicaciones de Intune para permitir que solo los usuarios protegidos de Intune usen la aplicación de LOB de Android con SDK integrado. También se describe cómo habilitar el SSO para la aplicación de LOB de Android con SDK integrado. **No** se admite para las aplicaciones de la tienda que pueden usar los usuarios que no son de Intune.

> [!NOTE] 
> Las ventajas de la **inscripción predeterminada** incluyen un método simplificado de obtención de la directiva del servicio APP-WE para una aplicación en el dispositivo.

> [!NOTE] 
> La **inscripción predeterminada** es compatible con la nube soberana.

Habilite la inscripción predeterminada con los pasos siguientes:

1. Si la aplicación integra ADAL o hay que habilitar SSO, [configure ADAL](#configure-azure-active-directory-authentication-library-adal) según la [configuración común de ADAL](#common-adal-configurations) #2. Si no es así, puede omitir este paso.
   
2. Habilite la inscripción predeterminada indicando el siguiente valor en el manifiesto:

   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```

   > [!NOTE] 
   > Esta debe ser la única integración de MAM-WE en la aplicación. Surgirán conflictos si hay cualquier otro intento de llamada a las API de MAMEnrollmentManager.

3. Habilite la directiva de MAM necesaria indicando el siguiente valor en el manifiesto:

   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
   ```

   > [!NOTE] 
   > Esto obliga al usuario a descargar el Portal de empresa en el dispositivo y completar el flujo de inscripción predeterminada antes de usarlo.


## <a name="limitations"></a>Limitaciones

### <a name="file-size-limitations"></a>Limitaciones del tamaño de archivo

En el caso de las bases de código de gran tamaño que se ejecutan sin [ProGuard](http://proguard.sourceforge.net/), las limitaciones del formato de archivo ejecutable Dalvik se convierten en un problema. En concreto, pueden producirse las siguientes limitaciones:

1. Límite de 65 000 en campos.
2. Límite de 65 000 en métodos.

### <a name="policy-enforcement-limitations"></a>Limitaciones de cumplimiento de directivas

* **Uso de solucionadores de contenido**: la directiva de "transferencia o recepción" de Intune puede bloquear (o bloquear parcialmente) el uso de un solucionador de contenido para acceder al proveedor de contenido de otra aplicación. Esto hará que los métodos `ContentResolver` devuelvan un valor nulo o generen un valor de error (por ejemplo, `openOutputStream` generará `FileNotFoundException` si se bloquea). La aplicación puede determinar si fue la directiva quien produjo un error al escribir los datos a través de un solucionador de contenido, cuando realizó la siguiente llamada:

    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```

    o si no hay ninguna actividad asociada

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    En el segundo caso, las aplicaciones de varias identidades deben encargarse de establecer adecuadamente la identidad de los subprocesos (o pasar una identidad explícita a la llamada de `getPolicy`).

### <a name="exported-services"></a>Servicios exportados

 El archivo AndroidManifest.xml que se incluye en el SDK para aplicaciones de Intune contiene el elemento **MAMNotificationReceiverService**; este elemento debe ser un servicio exportado para permitir que el Portal de empresa envíe notificaciones a una aplicación administrada. El servicio comprueba quién fue el autor de la llamada para asegurarse de que solo el Portal de empresa tiene permiso para enviar notificaciones.

### <a name="reflection-limitations"></a>Limitaciones de la reflexión
Algunas de las clases base de MAM (como MAMActivity y MAMDocumentsProvider) contienen métodos (basados en las clases base de Android originales) que usan tipos de parámetro o de valor devuelto que solo están presentes por encima de determinados niveles de API. Por esta razón, es posible que no siempre se pueda usar la reflexión para enumerar todos los métodos de los componentes de la aplicación. Esta restricción no se limita a MAM; es la misma que se aplicaría si la propia aplicación implementara estos métodos desde las clases base de Android.

### <a name="robolectric"></a>Robolectric
No se admiten pruebas del comportamiento del SDK de MAM en Robolectric. Existen problemas conocidos relacionados con la ejecución del SDK de MAM en Robolectric debido a comportamientos en Robolectric que no imitan de forma precisa aquellos de emuladores o dispositivos reales.

Si necesita probar la aplicación en Robolectric, se recomienda mover la lógica de clase de la aplicación a un asistente para producir el apk de pruebas unitarias con una clase de aplicación que no se herede de MAMApplication.
## <a name="expectations-of-the-sdk-consumer"></a>Expectativas del consumidor del SDK

El SDK de Intune mantiene el contrato proporcionado por la API de Android, aunque se pueden desencadenar condiciones de error con más frecuencia como resultado de la aplicación de directivas. Gracias a estas prácticas recomendadas, Android reducirá la probabilidad de que se produzcan errores:

* Las funciones del SDK de Android que podrían devolver el valor "null" tienen una mayor probabilidad de ser nulas.  Para minimizar los problemas, asegúrese de los valores que pueden ser “null” se encuentran en los lugares adecuados.

* Todas aquellas características que se pueden comprobar deben, por supuesto, comprobarse a través de sus API de reemplazo de MAM.

* Las funciones derivadas deben llamar a través de sus versiones de superclase.

* Evite usar cualquier API de manera ambigua. Por ejemplo, usar `Activity.startActivityForResult` sin comprobar antes si requestCode creará un comportamiento extraño.

## <a name="telemetry"></a>Telemetría

El SDK para aplicaciones de Intune para Android no controla la recopilación de datos de su aplicación. La aplicación Portal de empresa registra de forma predeterminada los datos generados por el sistema. Estos datos se envían a Microsoft Intune. Según la Directiva de Microsoft, no se recopilan datos personales.

> [!NOTE]
> Si los usuarios finales deciden no enviar estos datos, deberán desactivar la telemetría en la sección Configuración de la aplicación Portal de empresa. Para obtener más información, consulte [Desactivar la recopilación de datos de uso de Microsoft](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="recommended-android-best-practices"></a>Procedimientos recomendados de Android

* Todos los proyectos de biblioteca deberían compartir el mismo paquete de Android siempre que sea posible. Esta solución no generará errores esporádicos en el entorno de tiempo de ejecución; este es únicamente un problema de tiempo de compilación. Las versiones más recientes del SDK para aplicaciones de Intune quitarán parte de esta redundancia.

* Use las herramientas de la compilación del SDK de Android más reciente.

* Quite todas las bibliotecas innecesarias y que no use (por ejemplo, android.support.v4).
