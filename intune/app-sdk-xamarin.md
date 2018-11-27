---
title: Enlaces Xamarin del SDK para aplicaciones de Microsoft Intune
description: Los enlaces Xamarin del SDK para aplicaciones de Intune habilitan la directiva de protección de aplicaciones de Intune en las aplicaciones para iOS y Android creadas con Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: d8e9dd1e38fdc693bd30372f2961244e4e809771
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180347"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Enlaces Xamarin del SDK para aplicaciones de Microsoft Intune

> [!NOTE]
> Puede que quiera leer primero el artículo [Introducción a Intune App SDK](app-sdk-get-started.md), en el que se explica cómo preparar la integración en cada plataforma compatible.

## <a name="overview"></a>Introducción
Los [enlaces Xamarin del SDK para aplicaciones de Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) habilitan la [directiva de protección de aplicaciones de Intune](app-protection-policy.md) en las aplicaciones para iOS y Android creadas con Xamarin. Los enlaces permiten a los desarrolladores integrar fácilmente funciones de protección de la aplicación de Intune en su aplicación basada en Xamarin.

Los enlaces Xamarin del SDK para aplicaciones de Microsoft Intune permiten incorporar directivas de protección de aplicaciones de Intune, (también conocidas como directivas MAM o APP), a sus aplicaciones desarrolladas con Xamarin. Una aplicación MAM es aquella que está integrada con Intune App SDK. Los administradores de TI pueden implementar directivas de protección de aplicaciones en la aplicación móvil cuando Intune la administra activamente.

## <a name="whats-supported"></a>¿Qué se admite?

### <a name="developer-machines"></a>Equipos de desarrollador
* Windows (Visual Studio versión 15.7+)
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

El SDK se basa en la herramienta [Biblioteca de autenticación de Active Directory (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) para sus escenarios de inicio condicional y [autenticación](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/), que requieren que las aplicaciones se configuren con [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). 

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Habilitar directivas de protección de aplicaciones de Intune en su aplicación móvil iOS
1. Agregue el [paquete de NuGet Microsoft.Intune.MAM.Xamarin.iOS](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) a su proyecto Xamarin.iOS.
2.  Siga los pasos generales necesarios para integrar el SDK de aplicaciones de Intune en una aplicación móvil de iOS. Puede comenzar con el paso 3 de las instrucciones de integración de la [Guía para desarrolladores sobre el SDK de aplicaciones de Intune para iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). Puede omitir el paso final de esa sección consistente en ejecutar IntuneMAMConfigurator, ya que esta herramienta se incluye en el paquete Microsoft.Intune.MAM.Xamarin.iOS y se ejecutará automáticamente en tiempo de compilación.
    **Importante**: la habilitación del uso compartido de la cadena de claves para una aplicación es ligeramente diferente en Visual Studio en comparación con Xcode. Abra el plist de derechos de la aplicación y asegúrese de que está habilitada la opción "Habilitar cadena de claves" y de que se han agregado los grupos de uso compartido de la cadena de claves adecuados en esa sección. A continuación, asegúrese de que se especifica el plist de derechos en el campo "Derechos personalizados" de las opciones del proyecto "Firma de lote para iOS" para todas las combinaciones de configuración/plataforma adecuadas.
3.  Una vez que se agregan los enlaces y la aplicación está correctamente configurada, la aplicación puede empezar a usar las API del SDK de Intune. Para ello, debe incluir el espacio de nombres siguiente:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. Para empezar a recibir las directivas de protección de aplicaciones, la aplicación debe inscribirse en el servicio de MAM de Intune. Si su aplicación no usa la [Biblioteca de autenticación de Azure Active Directory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) o la [Biblioteca de autenticación de Microsoft](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) para autenticar a los usuarios y quiere que el SDK de Intune administre la autenticación, la aplicación deberá proporcionar el UPN del usuario al método LoginAndEnrollAccount de IntuneMAMEnrollmentManager:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      Las aplicaciones podrían pasar un valor nulo si el UPN del usuario es desconocido en el momento de hacer la llamada. En este caso, se pedirá a los usuarios que escriban su dirección de correo electrónico y su contraseña.
      
      Si su aplicación ya usa ADAL o MSAL para autenticar a los usuarios, puede configurar una experiencia de inicio de sesión único (SSO) entre la aplicación y el SDK de Intune. En primer lugar, deberá configurar ADAL/MSAL para almacenar los tokens en el mismo grupo de acceso de cadenas de claves que Intune Xamarin Bindings para iOS (com.microsoft.adalcache). Para ADAL, puede hacerlo [estableciendo la propiedad KeychainSecurityGroup de AuthenticationContext](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/Token-cache-serialization#enable-token-cache-sharing-across-ios-applications). En cuanto a MSAL, deberá [establecer la propiedad KeychainSecurityGroup de PublicClientApplication](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/msal-net-2-released#you-can-now-enable-sso-between-adal-and-msal-apps-on-xamarinios). Luego deberá reemplazar la configuración predeterminada de AAD que usa el SDK de Intune por la de la aplicación. Puede hacerlo mediante el diccionario IntuneMAMSettings de Info.plist de la aplicación, como se menciona en [Guía para desarrolladores acerca del SDK de aplicaciones de Microsoft Intune para iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk), o bien puede usar las propiedades de invalidación de AAD de la instancia de IntuneMAMPolicyManager. El enfoque de Info.plist se recomienda para las aplicaciones cuyos valores de ADAL son estáticos, aunque se recomienda utilizar las propiedades de invalidación para las aplicaciones que determinan esos valores en runtime. Cuando se hayan configurado todas las opciones del inicio de sesión único, su aplicación debe proporcionar el UPN del usuario al método RegisterAndEnrollAccount de IntuneMAMEnrollmentManager una vez que se haya autenticado correctamente:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      Las aplicaciones pueden determinar el resultado de un intento de inscripción implementando el método EnrollmentRequestWithStatus en una subclase de IntuneMAMEnrollmentDelegate y estableciendo la propiedad Delegate de IntuneMAMEnrollmentManager en una instancia de esa clase. Consulte nuestra [aplicación Xamarin.iOS de ejemplo](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) para ver un ejemplo.

      Una vez efectuada la inscripción correctamente, las aplicaciones pueden determinar el UPN de la cuenta inscrita (si antes era desconocido) consultando la siguiente propiedad: 
      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
> [!NOTE] 
> No hay ningún Remapper para iOS. La integración en una aplicación de Xamarin.Forms debería ser igual que para un proyecto normal de Xamarin.iOS. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Habilitación de directivas de protección de aplicaciones de Intune en la aplicación móvil Android

En el caso de las aplicaciones Android basadas en Xamarin que no usan un marco de interfaz de usuario, debe leer y seguir la [Guía para desarrolladores de Android sobre el SDK para aplicaciones de Intune](app-sdk-android.md). En la aplicación Android basada en Xamarin, debe reemplazar la clase, los métodos y las actividades por su equivalente MAM en función de la [tabla de reemplazos de clases y métodos](app-sdk-android.md#class-and-method-replacements) incluida en la guía. Si la aplicación no define una clase `android.app.Application`, deberá crear una y asegurarse de que se hereda de `MAMApplication`. Los valores de configuración de ADAL se comunican al SDK mediante los metadatos de AndroidManifest. Lea la documentación en [Configurar ADAL para la aplicación](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).

### <a name="xamarinandroid-integration"></a>Integración de Xamarin.Android

1. Agregue la última versión del [paquete NuGet Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) al proyecto de Xamarin.Android. Esto proporciona las referencias necesarias para que Intune habilite la aplicación.

2. Lea y siga la [Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune](app-sdk-android.md) en su totalidad, con especial atención a:

    1. La [sección completa de reemplazos de las clases y los métodos](app-sdk-android.md#class-and-method-replacements). 
    2. La [sección MAMApplication](app-sdk-android.md#mamapplication). Asegúrese de que la subclase esté correctamente representada con el atributo `[Application]` y de que invalide al constructor `(IntPtr, JniHandleOwnership)`.
    3. La [sección de integración ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) si la aplicación realiza la autenticación con AAD. 
    4. La [sección de inscripción MAM-WE](app-sdk-android.md#app-protection-policy-without-device-enrollment) si piensa obtener la directiva del servicio MAM en la aplicación.

> [!NOTE]
> Cuando intente buscar API equivalentes en la [Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune](app-sdk-android.md) en los enlaces de `Microsoft.Intune.MAM.Xamarin.Android` o cuando convierta los fragmentos de código de la guía, tenga en cuenta que ese generador de enlaces de Xamarin modifica las API de Android en los siguientes aspectos fundamentales:
> * Todos los identificadores se convierten en Pascal Case (com.foo.bar -> Com.Foo.Bar)
> * Todas las operaciones get/set se convierten en operaciones de propiedades (por ejemplo, Foo.getBar() -> Foo.Bar, Foo.setBar("zap") -> Foo.Bar = "zap")
> * Todas las interfaces tienen el carácter "I" antepuesto en el nombre (FooInterface -> IFooInterface).

### <a name="xamarinforms-integration"></a>Integración de Xamarin.Forms

**Además de realizar todos los pasos anteriores**, en las aplicaciones `Xamarin.Forms` se ha proporcionado el paquete `Microsoft.Intune.MAM.Remapper`. Este paquete realiza la sustitución de clases automáticamente al insertar clases `MAM` en la jerarquía de clases `Xamarin.Forms` de uso frecuente como `FormsAppCompatActivity` y `FormsApplicationActivity` para que pueda seguir usando esas clases mediante invalidaciones de funciones equivalentes MAM como `OnMAMCreate` y `OnMAMResume`. Para usarla, haga lo siguiente:

1.  Agregar el paquete de NuGet [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) al proyecto. Esto agrega automáticamente los enlaces de Xamarin del SDK para aplicaciones de Intune si aún no se han incluido.

2.  Agregue una llamada a `Xamarin.Forms.Forms.Init(Context, Bundle)` en la función `OnMAMCreate` de la clase `MAMApplication` creada en el paso anterior 2.2. Esto es necesario porque con la administración de Intune se puede iniciar la aplicación mientras se encuentra en segundo plano.

> [!NOTE]
> Dado que esta operación reescribe una dependencia que Visual Studio usa para la finalización automática de Intellisense, debe reiniciar Visual Studio después de la primera vez que se ejecuta Remapper para que Intellisense reconozca correctamente los cambios. 

Ha completado los pasos básicos para integrar el componente en la aplicación. Ahora puede seguir los pasos incluidos en la aplicación de ejemplo de Android de Xamarin. Se proporcionan dos ejemplos, uno para Xamarin.Forms y otro para Android.

## <a name="requiring-intune-app-protection-policies-in-order-to-use-your-xamarin-based-android-lob-app-optional"></a>Requerir directivas de protección de aplicaciones de Intune para usar la aplicación de LOB Android basada en Xamarin (opcional) 

Aquí encontrará instrucciones para garantizar que solo los usuarios protegidos de Intune pueden usar aplicaciones de LOB Android basadas en Xamarin en sus dispositivos. 

### <a name="general-requirements"></a>Requisitos generales
* Asegúrese de que se siguen los pasos para conceder los permisos de aplicación de Xamarin para el servicio Directiva de protección de aplicaciones (APP). Siga las instrucciones de la [guía de introducción al SDK de Intune](app-sdk-get-started.md#next-steps-after-integration) sobre cómo conceder acceso al servicio Intune App Protection (opcional). 
    
### <a name="working-with-the-intune-sdk"></a>Trabajar con el SDK de Intune
Estas instrucciones son específicas para todas las aplicaciones de Android y Xamarin que quieren solicitar directivas de protección de aplicaciones de Intune para su uso en un dispositivo de usuario final.

1. Configure ADAL siguiendo los pasos definidos en la [Guía para desarrolladores de Android acerca del SDK para aplicaciones de Microsoft Intune](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).
> [!NOTE] 
> El término "Id. de cliente" es el mismo que el término "Id. de aplicación" de Azure Portal vinculado a la aplicación. 
* Para habilitar el SSO, necesita el punto n.º 2 de la "Configuración de ADAL común".

2. Habilite la inscripción predeterminada indicando el siguiente valor en el manifiesto:```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
> [!NOTE] 
> Esta debe ser la única integración de MAM-WE en la aplicación. Podrían surgir conflictos si hay cualquier otro intento de llamada a las API de MAMEnrollmentManager.

3. Habilite la directiva de MAM necesaria indicando el siguiente valor en el manifiesto:```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
> [!NOTE] 
> Esto obliga a las aplicaciones a descargar el Portal de empresa en el dispositivo y completar el flujo de inscripción predeterminada antes de usarlo.

### <a name="working-with-adal"></a>Trabajar con ADAL
Estas instrucciones son un requisito de las aplicaciones .NET/Xamarin que quieren solicitar directivas de protección de aplicaciones de Intune para su uso en un dispositivo de usuario final.

1. Siga todos los pasos definidos en la documentación de ADAL en [Brokered Authentication for Android](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/tree/dev/adal#brokered-authentication-for-android) (Autenticación de intermediación para Android).
> [!NOTE] 
> Se espera que la próxima versión que ADAL .NET lance (3.17.4) contenga la corrección necesaria para que esto funcione.

## <a name="support"></a>Soporte técnico
Si su organización es cliente de Intune, consulte con su representante de soporte técnico de Microsoft para abrir un vale de soporte y crear una caso [en la página de incidencias de GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Le ayudaremos tan pronto como nos sea posible. 
