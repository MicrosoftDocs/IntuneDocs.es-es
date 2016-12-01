---
title: Complemento Cordova del SDK para aplicaciones de Microsoft Intune | Microsoft Intune
description: 
keywords: sdk, Cordova, intune
author: oydang
manager: angrobe
ms.author: oydang
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: karthikaraman
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ca4623db80d711f3543b6d688fb1bb1ef228c62c
ms.openlocfilehash: 5583c496a10d93d041d3387b7b10931bf87c73d6


---
# ﻿<a name="microsoft-intune-app-sdk-cordova-plugin"></a>Complemento Cordova del SDK para aplicaciones de Microsoft Intune

## <a name="overview"></a>Información general

El [complemento Cordova del SDK para aplicaciones de Intune](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam) habilita las [características de administración de aplicaciones móviles de Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) en las aplicaciones para iOS y Android creadas con Cordova. El complemento permite a los desarrolladores integrar características de protección de datos y aplicaciones de Intune en la aplicación basada en Cordova.

Descubrirá que puede habilitar características del SDK sin necesidad de cambiar el comportamiento de la aplicación. Una vez que haya integrado el complemento en la aplicación móvil iOS o Android, los administradores de TI podrán implementar directivas a través de Microsoft Intune compatibles con diversas características que permiten la protección de datos. Hemos creado el complemento de modo que la mayoría de los pasos se realizan automáticamente en el proceso de compilación de Cordova. Como resultado, podrá habilitar la aplicación para la administración rápidamente. Para comenzar, siga los pasos que se indican a continuación en función de la plataforma de destino.

Para poder instalar y usar el complemento Cordova del SDK para aplicaciones de Microsoft Intune **debe**:

* Revisar los [términos de licencia del complemento Cordova del SDK para aplicaciones de Intune](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam/blob/master/Intune_App_SDK_Cordova_plugin_RTM_license.pdf).
* Imprimir y conservar una copia de los términos de licencia para sus archivos. Al descargar y usar el complemento Cordova del SDK para aplicaciones de Intune, acepta dichos términos.  Si no los acepta, no use el software.

Consulte la [documentación oficial](/intune/develop/intune-app-sdk) para obtener una descripción más detallada del SDK para aplicaciones de Intune.

## <a name="supported-scenarios"></a>Escenarios admitidos

### <a name="platforms"></a>Plataformas
* Android
* iOS


### <a name="emm-scenarios"></a>Escenarios de EMM

* MAM de Intune en dispositivos inscritos con MDM de Intune
* MAM de Intune en dispositivos inscritos con EMM de terceros
* MAM de Intune en dispositivos no administrados y no inscritos

Ahora, las aplicaciones Cordova compiladas con el complemento Cordova del SDK para aplicaciones de Intune pueden recibir directivas de administración de aplicaciones móviles (MAM) de Intune en dispositivos inscritos con la administración de dispositivos móviles (MDM) de Intune y en dispositivos no inscritos.



## <a name="prerequisites"></a>Requisitos previos

* **[Solo para Android]** Siempre debe estar instalada en el dispositivo la aplicación de portal de empresa de Microsoft Intune más reciente.


* Se requiere la versión 0.8.0 o superior del [complemento de bibliotecas de autenticación de Azure Active Directory (ADAL) para Cordova](https://github.com/AzureAD/azure-activedirectory-library-for-cordova).
  * **Nota:** Debido a un error de Apache Cordova archivado [aquí](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22), las aplicaciones que ya tienen la dependencia del complemento no actualizarán automáticamente el complemento a la versión solicitada.

## <a name="quick-start"></a>Inicio rápido

1. Actualice su versión de ADAL:

    ```
    cordova plugin remove cordova-plugin-ms-adal
    cordova plugin add cordova-plugin-ms-adal@0.8.x
    ```

2. Agregue el complemento Cordova del SDK para aplicaciones de Intune:

    ```
    cordova plugin add cordova-plugin-ms-intune-mam
    ```

## <a name="how-to-build-the-plugin-into-your-ios-app"></a>Cómo integrar el complemento en la aplicación iOS

Debe llevar a cabo ciertos pasos a fin de habilitar la aplicación para MAM de Intune. Para mayor comodidad, estos pasos se realizan automáticamente en el proceso de compilación de Cordova como enlace anterior a la compilación. Como resultado, los pasos automatizados modificarán los archivos `*.pbxproj`, `*-Info.plist` y `*.entitlements` que están asociados a una configuración de proyecto. Si el proyecto no contiene un archivo de derechos, el complemento creará uno automáticamente.

Esta configuración admite un solo destino y llevará a cabo la configuración en el primer destino encontrado en caso de que existan varios. Si se produce un error en el proceso, compruebe que:

1. El proyecto Xcode de la aplicación es `[name].xcodeproj`, donde `[name]` es el valor definido en `config.xml`
2. El proyecto usa la [estructura de directorios estándar de una aplicación Cordova](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure).

## <a name="how-to-build-the-plugin-into-your-android-app"></a>Cómo integrar el complemento en la aplicación Android

1. Importe este complemento con las herramientas de Cordova más recientes. El complemento se invocará automáticamente como un paso `after_compile`.

2. El complemento creará una versión habilitada para MAM de un archivo apk integrado (API de Android 14 o superior) al final del proceso de compilación. La salida de compilación contendrá un archivo `[Project]-intunewrapped-[Build_Configuration].apk` (por ejemplo, `helloWorld-intunewrapped-debug.apk`).

El complemento solo admite compilaciones Gradle.

Debido a un error de Cordova archivado [aquí](https://issues.apache.org/jira/browse/CB-9434) que hace que ciertos enlaces de Cordova se omitan en `cordova run`, para ejecutar la aplicación ajustada desde la línea de comandos debe hacer lo siguiente:

```
$ cordova build
$ cordova run --nobuild
```


### <a name="signing-your-android-app"></a>Firmar la aplicación Android
Para agregar información de firma al archivo apk ajustado, modifique `build.json` como lo haría normalmente para agregar información de firma. Por ejemplo:
```json
{
  "android": {
    "release": {
      "keystore": "your.keystore",
      "storePassword": "yourpassword",
      "alias": "youralias",
      "password" : "yourpassword",
      "keystoreType": ""
    }
  }
}
```

### <a name="build-for-android-test-only"></a>Compilar solo para prueba de Android

1. Agregue `android:testOnly="true"` al nodo de aplicación del archivo `AndroidManifest.xml`.


2. **Cordova 6.x.x:** en `[PROJECT_ROOT]/platforms/android/cordova/lib/Adb.js`, cambie la línea 60 de

    ```
    var args = ['-s', target, 'install'];
    ```
    en
    ```
    var args = ['-s', target, 'install', '-t'];
    ```

Como resultado, se ejecuta `adb install` con la marca "-t", ya que las aplicaciones `testOnly` no se pueden instalar sin dicha marca.

### <a name="debugging-from-visual-studio"></a>Depurar desde Visual Studio
Después de iniciar la aplicación por primera vez, debería ver un cuadro de diálogo que le notifica que la aplicación se administra mediante Intune. Pulse "No volver a mostrar" y haga clic de nuevo en el botón para depurar o ejecutar en VS para encontrar los puntos de interrupción.

## <a name="known-limitations"></a>Limitaciones conocidas
### <a name="android"></a>Android
* La compatibilidad con Multi-Dex está incompleta.
* La aplicación debe tener como destino Android 4.0 (API de Android 14) o superior.

### <a name="ios"></a>iOS
* Cada vez que modifique la lista de UTI en el nodo **CFBundleDocumentTypes** del archivo **Info.plist**, debe borrar el UTI de Intune en la sección de UTI importados del mismo archivo plist (nodo **UTImportedTypeDeclarations**) antes de volver a compilar. Todos los UTI de Intune empezarán con el prefijo `com.microsoft.intune.mam`.

* Si quiere quitar del proyecto Cordova el complemento de Intune, también debe quitar la plataforma iOS y volver a agregarla para deshacer parte de la configuración de Intune en los archivos .xcodeproj y .plist.



<!--HONumber=Nov16_HO3-->


