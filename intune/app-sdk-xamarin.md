---
title: Componente Xamarin del SDK para aplicaciones de Microsoft Intune
description: 
keywords: sdk, Xamarin, intune
author: erikre
manager: angrobe
ms.author: erikre
ms.date: 11/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ae53ced489542ba7e675e547740f1858d761c7ab
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Componente Xamarin del SDK para aplicaciones de Microsoft Intune

> [!NOTE]
> Puede que quiera leer primero el artículo [Introducción a Intune App SDK](app-sdk-get-started.md), en el que se explica cómo preparar la integración en cada plataforma compatible.



## <a name="overview"></a>Introducción
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
1.  Siga los pasos generales necesarios para integrar el SDK de aplicaciones de Intune en una aplicación móvil de iOS. Puede comenzar con el paso 3 de las instrucciones de integración de la [Guía para desarrolladores sobre el SDK de aplicaciones de Intune para iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app).
    **Importante**: la habilitación del uso compartido de la cadena de claves para una aplicación es ligeramente diferente en Visual Studio en comparación con Xcode. Abra el plist de derechos de la aplicación y asegúrese de que está habilitada la opción "Habilitar cadena de claves" y de que se han agregado los grupos de uso compartido de la cadena de claves adecuados en esa sección. A continuación, asegúrese de que se especifica el plist de derechos en el campo "Derechos personalizados" de las opciones del proyecto "Firma de lote para iOS" para todas las combinaciones de configuración/plataforma adecuadas.
2.  Una vez que se agrega el componente y la aplicación está correctamente configurada, la aplicación puede empezar a usar las API de SDK de Intune. Para ello, debe incluir el espacio de nombres siguiente:
      ```csharp
      using Microsoft.Intune.MAM;
      ```
3.    Para empezar a recibir las directivas de protección de aplicaciones, la aplicación debe inscribirse en el servicio de MAM de Intune. Si su aplicación ya usa Microsoft Azure Active Directory Authentication Library (ADAL) para autenticar a los usuarios, la aplicación debe proporcionar el UPN del usuario al método registerAndEnrollAccount de IntuneMAMEnrollmentManager una vez que se ha autenticado correctamente:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **Importante**: Asegúrese de reemplazar la configuración de ADAL pretedeterminada del SDK de aplicaciones de Intune por la de la aplicación. Puede hacerlo mediante el diccionario IntuneMAMSettings de Info.plist de la aplicación, como se menciona en [Guía para desarrolladores acerca del SDK de aplicaciones de Microsoft Intune para iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), o bien puede usar las propiedades de invalidación de AAD de la instancia de IntuneMAMPolicyManager. El enfoque de Info.plist se recomienda para las aplicaciones cuyos valores de ADAL son estáticos, aunque se recomienda utilizar las propiedades de invalidación para las aplicaciones que determinan esos valores en runtime. 
      
      Si la aplicación no usa ADAL y desea que el SDK de Intune controle la autenticación, la aplicación debe llamar al método loginAndEnrollAccount de IntuneMAMEnrollmentManager:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

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
