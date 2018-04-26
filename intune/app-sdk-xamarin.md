---
title: Enlaces Xamarin del SDK para aplicaciones de Microsoft Intune
description: Los enlaces Xamarin del SDK para aplicaciones de Intune habilitan la directiva de protección de aplicaciones de Intune en las aplicaciones para iOS y Android creadas con Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9f9cc117925f59c9fb7c55d0ff10aedf09d26f93
ms.sourcegitcommit: b727b6bd6f138c5def7ac7bf1658068db30a0ec3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Enlaces Xamarin del SDK para aplicaciones de Microsoft Intune

> [!NOTE]
> Puede que quiera leer primero el artículo [Introducción a Intune App SDK](app-sdk-get-started.md), en el que se explica cómo preparar la integración en cada plataforma compatible.

## <a name="overview"></a>Introducción
Los [enlaces Xamarin del SDK para aplicaciones de Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) habilitan la [directiva de protección de aplicaciones de Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) en las aplicaciones para iOS y Android creadas con Xamarin. Los enlaces permiten a los desarrolladores integrar fácilmente funciones de protección de la aplicación de Intune en su aplicación basada en Xamarin.

Los enlaces Xamarin del SDK para aplicaciones de Microsoft Intune permiten incorporar directivas de protección de aplicaciones de Intune, (también conocidas como directivas MAM o APP), a sus aplicaciones desarrolladas con Xamarin. Una aplicación MAM es aquella que está integrada con Intune App SDK. Los administradores de TI pueden implementar directivas de protección de aplicaciones en la aplicación móvil cuando Intune la administra activamente.

## <a name="whats-supported"></a>¿Qué se admite?

### <a name="developer-machines"></a>Equipos de desarrollador
* Windows
* macOS


### <a name="mobile-app-platforms"></a>Plataformas de aplicaciones móviles
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Escenarios de administración de aplicaciones móviles de Intune

* Intune APP-WE (sin inscripción de dispositivos)
* Dispositivos inscritos con MDM de Intune
* Dispositivos inscritos con EMM de terceros

Ahora, las aplicaciones Xamarin compiladas con los enlaces Xamarin del SDK para aplicaciones de Intune pueden recibir directivas de protección de aplicaciones de Intune en dispositivos inscritos con la administración de dispositivos móviles (MDM) de Intune y en dispositivos no inscritos.

## <a name="prerequisites"></a>Requisitos previos

Revise los [términos de licencia](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Imprimir y conservar una copia de los términos de licencia para sus archivos. Al descargar y usar los enlaces Xamarin del SDK de aplicaciones de Intune, acepta dichos términos. Si no los acepta, no use el software.

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Habilitar directivas de protección de aplicaciones de Intune en su aplicación móvil iOS
1. Agregue el [paquete de NuGet Microsoft.Intune.MAM.Xamarin.iOS](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) a su proyecto Xamarin.iOS.
2.  Siga los pasos generales necesarios para integrar el SDK de aplicaciones de Intune en una aplicación móvil de iOS. Puede comenzar con el paso 3 de las instrucciones de integración de la [Guía para desarrolladores sobre el SDK de aplicaciones de Intune para iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Puede omitir el paso final de esa sección consistente en ejecutar IntuneMAMConfigurator, ya que esta herramienta se incluye en el paquete Microsoft.Intune.MAM.Xamarin.iOS y se ejecutará automáticamente en tiempo de compilación.
    **Importante**: la habilitación del uso compartido de la cadena de claves para una aplicación es ligeramente diferente en Visual Studio en comparación con Xcode. Abra el plist de derechos de la aplicación y asegúrese de que está habilitada la opción "Habilitar cadena de claves" y de que se han agregado los grupos de uso compartido de la cadena de claves adecuados en esa sección. A continuación, asegúrese de que se especifica el plist de derechos en el campo "Derechos personalizados" de las opciones del proyecto "Firma de lote para iOS" para todas las combinaciones de configuración/plataforma adecuadas.
3.  Una vez que se agregan los enlaces y la aplicación está correctamente configurada, la aplicación puede empezar a usar las API del SDK de Intune. Para ello, debe incluir el espacio de nombres siguiente:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. Para empezar a recibir las directivas de protección de aplicaciones, la aplicación debe inscribirse en el servicio de MAM de Intune. Si su aplicación ya usa Microsoft Azure Active Directory Authentication Library (ADAL) para autenticar a los usuarios, la aplicación debe proporcionar el UPN del usuario al método registerAndEnrollAccount de IntuneMAMEnrollmentManager una vez que se ha autenticado correctamente:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **Importante**: Asegúrese de reemplazar la configuración de ADAL pretedeterminada del SDK de aplicaciones de Intune por la de la aplicación. Puede hacerlo mediante el diccionario IntuneMAMSettings de Info.plist de la aplicación, como se menciona en [Guía para desarrolladores acerca del SDK de aplicaciones de Microsoft Intune para iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), o bien puede usar las propiedades de invalidación de AAD de la instancia de IntuneMAMPolicyManager. El enfoque de Info.plist se recomienda para las aplicaciones cuyos valores de ADAL son estáticos, aunque se recomienda utilizar las propiedades de invalidación para las aplicaciones que determinan esos valores en runtime. 
      
      Si la aplicación no usa ADAL y desea que el SDK de Intune controle la autenticación, la aplicación debe llamar al método loginAndEnrollAccount de IntuneMAMEnrollmentManager:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>Habilitar directivas de protección de aplicaciones en su aplicación móvil Android
Agregue el [paquete de NuGet Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) a su proyecto Xamarin.Android.

Para las aplicaciones de Xamarin.Android, debe leer por completo y seguir la [Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune](app-sdk-android.md), incluido el reemplazo de las clases, los métodos y las actividades por su equivalente MAM siguiendo la [tabla](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) que aparece en la guía. 

> [!NOTE]
> Si la aplicación no define una clase `android.app.Application`, deberá crear una y asegurarse de que se hereda de `MAMApplication`.

> [!NOTE]
> Al intentar buscar una API equivalente en la [Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune](app-sdk-android.md) en los enlaces de `Microsoft.Intune.MAM.Xamarin.Android` o convertir los fragmentos de código de la guía, tenga en cuenta que ese generador de enlaces de Xamarin modifica las API de Android en los siguientes aspectos fundamentales:
> * Todos los identificadores se convierten en mayúsculas y minúsculas Pascal (com.microsoft.foo -> Com.Microsoft.Foo).
> * Todas las operaciones get/set se convierten en operaciones de propiedad (por ejemplo, Foo.getBar() -> Foo.Bar, Foo.setBar("zap") -> Foo.Bar = "zap").
> * Todas las interfaces tienen el carácter "I" antepuesto en el nombre (FooInterface -> IFooInterface).

En el caso de aplicaciones que usan Xamarin.Forms u otros marcos de interfaz de usuario, hemos proporcionado una herramienta denominada `Microsoft.Intune.MAM.Remapper`. La herramienta llevará a cabo automáticamente el reemplazo de la clase, Para usarla, haga lo siguiente:

1.  Agregar el paquete de NuGet [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) al proyecto.

2.  Establezca la acción de compilación del archivo `remapping-config.json` que se incluye con el paquete de NuGet en **RemappingConfigFile**. El archivo `remapping-config.json` incluido solo funciona con Xamarin.Forms. En el caso de otros marcos de interfaz de usuario, consulte el archivo Léame incluido con el paquete NuGet de Remapper.

3.  Agregue una llamada a Xamarin.Forms.Forms.Init(Context, Bundle) en la función OnMAMCreate de MAMApplication porque, con la administración de Intune, se puede iniciar la aplicación mientras se encuentra en segundo plano.

4.  Realice el resto de los pasos descritos en la [Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune](app-sdk-android.md) que sean adecuados a su aplicación.

> [!NOTE]
> A veces se puede restablecer la acción de remapping-config.json al actualizar el paquete de Microsoft.Intune.MAM.Remapper.Tasks, lo que haría que las compilaciones generasen un error.

## <a name="next-steps"></a>Pasos siguientes

Ha completado la configuración básica de la aplicación para la administración de Intune. Ahora puede seguir los pasos que se incluyen en las guías de integración para cada una de las plataformas mencionadas anteriormente.

Si su organización es cliente de Intune, consulte con su representante de soporte técnico de Microsoft para abrir un vale de soporte y crear una caso [en la página de incidencias de GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Le ayudaremos tan pronto como nos sea posible. 