---
title: Componente Xamarin del SDK para aplicaciones de Microsoft Intune
description: 
keywords: sdk, Xamarin, intune
author: mattbriggs
manager: angrobe
ms.author: mabriggs
ms.date: 11/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f50ecfbf5a0ac0b05de38e0ad29b27a729ab824b
ms.sourcegitcommit: 0f877251e6adf4e45b918cc8dc9193626727f2d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2017
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Componente Xamarin del SDK para aplicaciones de Microsoft Intune

> [!NOTE]
> Puede que quiera leer primero el artículo [Introducción a Intune App SDK](app-sdk-get-started.md), en el que se explica cómo preparar la integración en cada plataforma compatible.



## <a name="overview"></a>Información general
El [componente Xamarin del SDK para aplicaciones de Intune](https://components.xamarin.com/view/microsoft.intune.mam) habilita la [directiva de protección de aplicaciones de Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) en las aplicaciones para iOS y Android creadas con Xamarin. El componente permite a los desarrolladores integrar fácilmente funciones de protección de la aplicación de Intune en su aplicación basada en Xamarin.

> [!NOTE]
> La compatibilidad con Intune SDK para Xamarin está disponible actualmente en versión preliminar. 

El componente Xamarin del SDK para aplicaciones de Microsoft Intune permite incorporar directivas de protección de aplicaciones de Intune, (también conocidas como APP o directivas MAM), a sus aplicaciones desarrolladas con Xamarin. Una aplicación MAM es aquella que está integrada con Intune App SDK. Los administradores de TI pueden implementar directivas de protección de aplicaciones en la aplicación móvil cuando Intune la administra activamente.

## <a name="whats-supported"></a>¿Qué se admite?

### <a name="developer-machines"></a>Equipos de desarrollador
* macOS


### <a name="mobile-app-platforms"></a>Plataformas de aplicaciones móviles
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Escenarios de administración de aplicaciones móviles de Intune

* Dispositivos inscritos con MDM de Intune
* Dispositivos inscritos con EMM de terceros
* Dispositivos no administrados (es decir, no inscritos con cualquier MDM)

Ahora, las aplicaciones Xamarin compiladas con el componente Xamarin del SDK para aplicaciones de Intune pueden recibir directivas de protección de aplicaciones de Intune en dispositivos inscritos con la administración de dispositivos móviles (MDM) de Intune y en dispositivos no inscritos.

## <a name="prerequisites"></a>Requisitos previos

* **[Solo para Android]** Debe estar instalada en el dispositivo la aplicación Portal de empresa de Microsoft Intune más reciente.

## <a name="get-started"></a>Introducción

1.  Descargue **Xamarin-component.exe** desde [aquí](https://components.xamarin.com/submit/xpkg) y extráigalo.

2. Lea los [términos de licencia](https://components.xamarin.com/license/microsoft.intune.mam) del componente Xamarin de MAM de Microsoft Intune.

3.  Descargue la carpeta del componente Xamarin del SDK para aplicaciones de Intune desde [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) o [Xamarin](https://components.xamarin.com/license/microsoft.intune.mam) y extráigalo. Los dos archivos descargados en los pasos 1 y 3 deben estar en el mismo nivel de directorio.

4.  En la línea de comandos, ejecute como administrador `Xamarin.Component.exe install <.xam> file`.

5.  En Visual Studio, haga clic con el botón derecho en **Componentes** en el proyecto de Xamarin creado anteriormente.

6.  Seleccione **Editar componentes** y agregue el componente del SDK para aplicaciones de Intune que descargó localmente en el equipo.



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Habilitar directivas de protección de aplicaciones de Intune en su aplicación móvil iOS
1.  Para inicializar el SDK para aplicaciones de Intune, debe realizar una llamada a cualquier API de la clase `AppDelegate.cs`. Por ejemplo:

      ```csharp
      public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
      {
            Console.WriteLine ("Is Managed: {0}", IntuneMAMPolicyManager.Instance.PrimaryUser != null);
            return true;
      }

      ```

2.  Ahora que el componente se ha agregado e inicializado, puede seguir los pasos generales necesarios para integrar el SDK para aplicaciones en una aplicación móvil iOS. Encontrará la documentación completa para habilitar aplicaciones iOS nativas en la [Guía para desarrolladores sobre el SDK de aplicaciones de Microsoft Intune para iOS](app-sdk-ios.md).
3. **Importante**: Hay varias modificaciones específicas de las aplicaciones iOS basadas en Xamarin. Por ejemplo, al habilitar grupos de cadenas de claves, debe agregar lo siguiente para integrar la aplicación de ejemplo de Xamarin que se incluye en el componente. A continuación se muestra un ejemplo de los grupos que debe tener en los grupos de acceso a cadenas de claves:

      ```xml
      <?xml version="1.0" encoding="UTF-8"?>
      <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
      <plist version="1.0">
            <dict>
                  <key>keychain-access-groups</key>
                  <array>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample</string>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample.intunemam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.intune.mam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.adalcache</string>
                  </array>
            </dict>
      </plist>
      ```

Ya ha completado los pasos necesarios para integrar el componente en la aplicación iOS basada en Xamarin. Si emplea Xcode para compilar el proyecto, puede usar `Intune App SDK Settings.bundle`. Esto le permite activar y desactivar la configuración de directiva de Intune al compilar el proyecto para probarlo y depurarlo. Para sacar partido de este paquete, siga los pasos que se indican en la [Guía para desarrolladores sobre el SDK de aplicaciones de Microsoft Intune para iOS](app-sdk-ios.md) y lea la sección sobre la [depuración en Xcode](app-sdk-ios.md#status-result-and-debug-notifications).

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>Habilitar directivas de protección de aplicaciones en su aplicación móvil Android
En el caso de las aplicaciones Android basadas en Xamarin que no usan un marco de interfaz de usuario, debe leer y seguir la [Guía para desarrolladores de Android sobre el SDK para aplicaciones de Intune](app-sdk-android.md). En la aplicación Android basada en Xamarin, debe reemplazar la clase, los métodos y las actividades por su equivalente MAM en función de la [tabla](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) incluida en la guía. Si la aplicación no define una clase `android.app.Application`, deberá crear una y asegurarse de que se hereda de `MAMApplication`.

En el caso de Xamarin.Forms y otros marcos de interfaz de usuario, hemos proporcionado una herramienta denominada `MAM.Remapper`. La herramienta llevará a cabo automáticamente el reemplazo de la clase, pero deberá llevar a cabo los pasos siguientes:

1.  Agregar una referencia al paquete NuGet `Microsoft.Intune.MAM.Remapper.Tasks` versión 0.1.0.0 o superior.

2.  Agregar la línea siguiente al archivo csproj de Android:
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  Establecer la acción de compilación del archivo agregado `remapping-config.json` en **RemappingConfigFile**. El archivo `remapping-config.json` incluido solo funciona con Xamarin.Forms. En el caso de otros marcos de interfaz de usuario, consulte el archivo Léame incluido con el paquete NuGet de Remapper.

## <a name="next-steps"></a>Pasos siguientes

Ha completado los pasos básicos para integrar el componente en la aplicación. Ahora puede seguir los pasos incluidos en la aplicación de ejemplo de Android de Xamarin. Se proporcionan dos ejemplos, uno para Xamarin.Forms y otro para Android.
