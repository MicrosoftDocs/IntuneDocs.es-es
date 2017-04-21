---
title: Complemento Cordova del SDK para aplicaciones de Microsoft Intune | Microsoft Docs
description: 
keywords: sdk, Cordova, intune
author: oydang
manager: angrobe
ms.author: oydang
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: df54ac3a62b5ef21e8a32f3a282dd5299974a1b0
ms.openlocfilehash: 40c369bb0ff18bda30b221c461f75799e601c67c
ms.lasthandoff: 04/12/2017


---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Complemento Cordova del SDK para aplicaciones de Microsoft Intune

> [!NOTE]
> Puede que quiera leer primero el artículo [Introducción a Intune App SDK](intune-app-sdk-get-started.md), en el que se explica cómo preparar la integración en cada plataforma compatible.

## <a name="overview"></a>Información general

El [complemento Cordova del SDK para aplicaciones de Intune](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam) habilita la [directiva de protección de aplicaciones móviles de Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) en las aplicaciones para iOS y Android creadas con Cordova. El complemento permite a los desarrolladores integrar características de protección de datos y aplicaciones de Intune en la aplicación basada en Cordova.

Descubrirá que puede habilitar características del SDK sin necesidad de cambiar el comportamiento de la aplicación. Una vez que haya creado el complemento en su aplicación iOS o Android, el administrador de Microsoft Intune podrá implementar la directiva de protección de aplicaciones de Intune, que consta de una variedad de características de protección de datos. El complemento se ha creado de manera que la mayoría de los pasos se realizan automáticamente en el proceso de compilación de Cordova. Como resultado, debe poder obtener la aplicación habilitada para la protección de aplicaciones de Intune rápidamente. Para comenzar, siga los pasos que se indican a continuación en función de la plataforma de destino.

## <a name="supported-platforms"></a>Plataformas compatibles

* El complemento funciona en Windows, Mac y Linux OS
* El complemento funciona con aplicaciones Android con `minSdkVersion` >= 14 y `targetSdkVersion` <= 24
* El complemento funciona con aplicaciones de iOS destinadas a iOS 9.0 y versiones posteriores.

## <a name="intune-mobile-application-management-scenarios"></a>Escenarios de administración de aplicaciones móviles de Intune

* Dispositivos inscritos con MDM de Intune
* Dispositivos inscritos con EMM de terceros
* Dispositivos no administrados (es decir, no inscritos con cualquier MDM)

Ahora, las aplicaciones Cordova compiladas con el complemento Cordova del SDK pueden recibir directivas de protección de aplicaciones de Intune en dispositivos inscritos con la administración de dispositivos móviles (MDM) de Intune y en dispositivos no inscritos.

## <a name="prerequisites"></a>Requisitos previos

### <a name="android"></a>Android

* Siempre debe estar instalada en el dispositivo la aplicación de portal de empresa de Microsoft Intune más reciente.
* Debe aparecer Java 7 como mínimo en la ruta de acceso en la que vaya a ejecutar la compilación de Cordova cuando use el complemento.

### <a name="ios"></a>iOS

* La aplicación de portal de empresa de Microsoft Intune más reciente debe estar instalada en el dispositivo para las características de MDM. *No* es necesario para la directiva de protección de aplicaciones de Intune sin las características de inscripción de dispositivos.

### <a name="both-platforms"></a>Ambas plataformas

* Se requiere la versión 0.8.0 o superior del [complemento de bibliotecas de autenticación de Azure Active Directory (ADAL) para Cordova](https://github.com/AzureAD/azure-activedirectory-library-for-cordova).

> [!NOTE]
> Debido a un error de Apache Cordova archivado [aquí](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22), las aplicaciones que ya tienen la dependencia del complemento no actualizarán automáticamente el complemento a la versión solicitada.



## <a name="quick-start"></a>Inicio rápido

1. Actualice su versión de ADAL:

  ```shell
  cordova plugin remove cordova-plugin-ms-adal
  cordova plugin add cordova-plugin-ms-adal@0.8.x
  ```

2. Agregue el complemento Cordova del SDK para aplicaciones de Intune:

  ```shell
  cordova plugin add cordova-plugin-ms-intune-mam
  ```

## <a name="build-the-plugin-into-your-ios-app"></a>Integrar el complemento en la aplicación iOS

Tendrá que completar estos pasos para que se habilite la aplicación para la directiva de protección de aplicaciones de Intune. Para mayor comodidad, estos pasos se realizan automáticamente en el proceso de compilación de Cordova como enlace anterior a la compilación. Como resultado, los pasos automatizados modificarán los archivos `*.pbxproj`, `*-Info.plist` y `*.entitlements` que están asociados a una configuración de proyecto. Si el proyecto no contiene un archivo de derechos, el complemento creará uno automáticamente.

Esta configuración admite un solo destino y llevará a cabo la configuración en el primer destino encontrado en caso de que existan varios. Si se produce un error en el proceso, compruebe que:

1. El proyecto Xcode de la aplicación es `[name].xcodeproj`, donde `[name]` es el valor definido en `config.xml`
2. El proyecto usa la [estructura de directorios estándar de una aplicación Cordova](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure).

## <a name="build-the-plugin-into-your-android-app"></a>Integrar el complemento en la aplicación Android

1. Importe este complemento con las herramientas de Cordova más recientes. El complemento se invocará automáticamente como un paso `after_compile`.

2. El complemento creará una versión habilitada para Intune de un archivo apk integrado (API de Android 14 o superior) al final del proceso de compilación. La salida de compilación contendrá un archivo `[Project]-intunewrapped-[Build_Configuration].apk` (por ejemplo, `helloWorld-intunewrapped-debug.apk`).

> [!NOTE]
> El complemento solo admite compilaciones Gradle.

Debido a un error de Cordova archivado [aquí](https://issues.apache.org/jira/browse/CB-9434) que hace que ciertos enlaces de Cordova se omitan en `cordova run`, para ejecutar la aplicación ajustada desde la línea de comandos debe hacer lo siguiente:

```shell
$ cordova build
$ cordova run --nobuild
```

## <a name="sign-your-android-app"></a>Firmar la aplicación Android

El complemento reconoce automáticamente la información de firma que ha proporcionado a Cordova en las siguientes ubicaciones:

* platforms/android/debug-signing.properties
* platforms/android/release-signing.properties
* res/native/android/ant.properties

Consulte la [información de firma de gradle de Cordova](https://cordova.apache.org/docs/en/latest/guide/platforms/android/#using-gradle) para obtener más información sobre el formato esperado.

Actualmente no se admite la capacidad de proporcionar información de firma en `build.json` o ubicaciones arbitrarias proporcionadas a través de parámetros en la compilación de Cordova.

## <a name="debugging-from-visual-studio"></a>Depurar desde Visual Studio

Después de iniciar la aplicación por primera vez, debería ver un cuadro de diálogo que le notifica que la aplicación se administra mediante Intune. Pulse "No volver a mostrar" y haga clic de nuevo en el botón para depurar o ejecutar en VS para encontrar los puntos de interrupción.

## <a name="known-limitations"></a>Limitaciones conocidas

### <a name="android"></a>Android

* La compatibilidad con Multi-Dex está incompleta.
* La aplicación debe tener `minSdkVersion` de 14 y `targetSdkVersion` de 24 o lo siguiente. Actualmente no se admiten aplicaciones destinadas a API 25.
* No se pueden volver a firmar aplicaciones firmadas con el esquema de firma V2. Cuando las aplicaciones firmadas V2 se ajustan mediante el complemento, el .apk de salida ajustado estará sin firmar.
*
  * Puede deshabilitar la firma V2 predeterminada de Cordova agregando lo siguiente al archivo `build-extras.gradle`:

  ```gradle
  android {
      signingConfigs {
          release {
              v2SigningEnabled false
          }
          debug {
              v2SigningEnabled false
          }
      }
      buildTypes {
          release {
              signingConfig signingConfigs.release
          }
          debug {
              signingConfig signingConfigs.debug
          }
      }
  }
  ```

### <a name="ios"></a>iOS

* Cada vez que modifique la lista de UTI en el nodo **CFBundleDocumentTypes** del archivo **Info.plist**, debe borrar el UTI de Intune en la sección de UTI importados del mismo archivo plist (nodo **UTImportedTypeDeclarations**) antes de volver a compilar. Todos los UTI de Intune empezarán con el prefijo `com.microsoft.intune.mam`.

* Si quiere quitar el complemento de Intune App SDK para Cordova del proyecto de Cordova, también debe quitar la plataforma iOS y volver a agregarla para deshacer parte de la configuración de Intune en los archivos .xcodeproj y .plist.

