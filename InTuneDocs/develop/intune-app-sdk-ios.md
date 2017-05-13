---
title: "Guía para desarrolladores sobre el SDK para aplicaciones de Microsoft Intune para iOS | Microsoft Docs"
description: "El SDK para aplicaciones de Microsoft Intune para iOS permite incorporar directivas de protección de aplicaciones de Intune (en forma de administración de aplicaciones móviles (MAM)) a la aplicación iOS."
keywords: 
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df54ac3a62b5ef21e8a32f3a282dd5299974a1b0
ms.openlocfilehash: 1d2cb0d4b9442262c562e559a675f5a4a28ee572
ms.contentlocale: es-es
ms.lasthandoff: 05/03/2017


---

# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Guía para desarrolladores sobre el SDK para aplicaciones de Microsoft Intune para iOS

> [!NOTE]
> Puede que primero quiera leer el artículo [Introducción al SDK para aplicaciones de Microsoft Intune](intune-app-sdk-get-started.md), en el que se explica cómo preparar la integración en cada plataforma compatible.

El SDK para aplicaciones de Microsoft Intune para iOS permite incorporar directivas de protección de aplicaciones de Intune (también conocidas como directivas de **aplicación** o **MAM**) a la aplicación iOS nativa. Una aplicación habilitada para MAM es aquella que está integrada con el SDK para aplicaciones de Intune. Los administradores de TI pueden implementar directivas de protección de aplicaciones en la aplicación móvil si Intune administra activamente la aplicación.

## <a name="prerequisites"></a>Requisitos previos

* Necesitará un equipo Mac OS con OS X 10.8.5 o posterior y con Xcode 8 o posterior instalado.

* La aplicación debe ir dirigida a iOS 9 o superior.

* Revise los [términos de licencia del SDK para aplicaciones de Intune para iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS%20.pdf). Imprima y conserve una copia de los términos de licencia para sus registros. La descarga y el uso del SDK para aplicaciones de Intune para iOS supone la aceptación de dichos términos.  Si no los acepta, no use el software.

* Descargue los archivos del SDK para aplicaciones de Intune para iOS en [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios).

## <a name="whats-in-the-sdk"></a>Qué hay en el SDK

El SDK para aplicaciones de Intune para iOS incluye una biblioteca estática, archivos de recursos, encabezados de API, un archivo .plist de configuración de depuración y una herramienta de configuración. Las aplicaciones móviles pueden incluir simplemente los archivos de recursos y vincularse estáticamente a las bibliotecas para la mayor parte de la aplicación de las directivas. Las características avanzadas de MAM de Intune se aplican a través de las API.

Esta guía cubre el uso de los siguientes componentes del SDK para aplicaciones de Intune para iOS:

* **libIntuneMAM.a**: biblioteca estática del SDK para aplicaciones de Intune. Si la aplicación no usa extensiones, vincule esta biblioteca al proyecto para permitir la administración de aplicaciones móviles de Intune en la aplicación.

* **IntuneMAM.framework**: marco de trabajo del SDK para aplicaciones de Intune. Vincule este marco de trabajo al proyecto para permitir la administración de aplicaciones móviles de Intune en la aplicación. Si la aplicación emplea extensiones, use el marco de trabajo en lugar de la biblioteca estática para que el proyecto no cree varias copias de esta.

* **IntuneMAMResources.bundle**: lote de recursos que contiene recursos en los que se basa el SDK.

* **Encabezados**: expone las API del SDK para aplicaciones de Intune. Si usa una API, deberá incluir el archivo de encabezado que contiene la API. Los archivos de encabezado siguientes incluyen las llamadas a funciones API necesarias para habilitar la funcionalidad del SDK para aplicaciones de Intune:

    * IntuneMAMAsyncResult.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMLogger.h


## <a name="how-the-intune-app-sdk-works"></a>Cómo funciona el SDK para aplicaciones de Intune

El objetivo del SDK para aplicaciones de Intune para iOS es agregar capacidades de administración a las aplicaciones de iOS con mínimos cambios en el código. Cuantos menos cambios haya en el código, menos se tardará en comercializar, sin afectar a la coherencia y la estabilidad de la aplicación móvil.


## <a name="build-the-sdk-into-your-mobile-app"></a>Compilar el SDK en la aplicación móvil

Para habilitar el SDK para aplicaciones de Intune, siga estos pasos:

1. **Opción 1 (recomendada)**: vincule `IntuneMAM.framework` al proyecto. Arrastre `IntuneMAM.framework` a la lista **Marcos de trabajo y bibliotecas vinculados** del destino del proyecto.

    > [!NOTE]
    > Si usa el marco de trabajo, debe extraer manualmente las arquitecturas de simulador del marco de trabajo universal antes de enviar la aplicación al App Store. Vea [Enviar la aplicación al App Store](#Submit-your-app-to-the-App-Store) para obtener más detalles.

2. **Opción 2**: vincule a la biblioteca `libIntuneMAM.a`. Arrastre la biblioteca `libIntuneMAM.a` a la lista **Marcos de trabajo y bibliotecas vinculados** del destino del proyecto.

    ![SDK para aplicaciones de Intune para iOS: marcos de trabajo y bibliotecas vinculados](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    > [!NOTE]
    > Si planea publicar la aplicación en el App Store, use la versión de `libIntuneMAM.a` compilada para publicación y no la versión de depuración. La versión de lanzamiento estará en la carpeta **release**. La versión de depuración tiene un resultado detallado que ayuda a solucionar problemas relacionados con el SDK para aplicaciones de Intune.

    Agregue `-force_load {PATH_TO_LIB}/libIntuneMAM.a` a cualquiera de los siguientes y sustituya `{PATH_TO_LIB}` por la ubicación del SDK para aplicaciones de Intune:
      * La opción de configuración de compilación `OTHER_LDFLAGS` del proyecto
      * **Otras marcas del enlazador** de la interfaz de usuario

        > [!NOTE]
        > Para buscar `PATH_TO_LIB`, seleccione el archivo `libIntuneMAM.a` y elija **Obtener información** en el menú **Archivo**. Copie y pegue la información **Dónde** (la ruta de acceso) de la sección **General** de la ventana **Información**.

3. Agregue estos marcos de trabajo de iOS al proyecto:
    * MessageUI.framework
    * Security.framework
    * MobileCoreServices.framework
    * SystemConfiguration.framework
    * libsqlite3.tbd
    * libc++.tbd
    * ImageIO.framework
    * LocalAuthentication.framework
    * AudioToolbox.framework


4. Agregue el lote de recursos `IntuneMAMResources.bundle` al proyecto al arrastrarlo desde **Copiar recursos del lote**, en **Fases de compilación**.

    ![SDK para aplicaciones de Intune para iOS: copiar recursos del lote](../media/intune-app-sdk-ios-copy-bundle-resources.png)

5. Si la aplicación móvil define un archivo de guión gráfico o nib principal en su archivo Info.plist, corte los campos de **guión gráfico principal** o **nib principal**. En Info.plist, pegue estos campos y sus valores correspondientes en un diccionario nuevo llamado **IntuneMAMSettings** con los siguientes nombres de clave, según corresponda:
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile~ipad
    > [!NOTE]
  > Si la aplicación móvil no define un archivo de guión gráfico o nib principal en su archivo Info.plist, estos valores no son necesarios.

    Puede ver Info.plist en formato sin procesar (para ver los nombres de claves) si hace clic con el botón derecho en cualquier lugar del cuerpo del documento y cambia el tipo de vista a **Mostrar claves/valores sin procesar**.

6. Para habilitar el uso compartido de cadenas de claves (si aún no está habilitado), elija **Capacidades** en cada destino del proyecto y habilite el modificador de **uso compartido de cadenas de claves**. El uso compartido de cadenas de claves es necesario para continuar con el siguiente paso.

  > [!NOTE]
    > El perfil de aprovisionamiento debe admitir nuevos valores de uso compartido de cadenas de claves. Los grupos de acceso a cadena de claves deben admitir un carácter comodín. Para comprobarlo, abra el archivo .mobileprovision en un editor de texto, busque **keychain-access-groups** y asegúrese de que tiene un carácter comodín. Por ejemplo:
    ```xml
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```

7. Después de habilitar el uso compartido de cadenas de claves, siga estos pasos para crear un grupo de acceso independiente en el que almacenar los datos del SDK para aplicaciones de Intune. Puede crear un grupo de acceso a cadenas de claves mediante la interfaz de usuario o mediante el archivo de derechos. Si usa la interfaz de usuario para crear el grupo de acceso a cadenas de claves, asegúrese de seguir los pasos siguientes:

    1. Si la aplicación móvil no tiene definido ningún grupo de acceso a cadenas de claves, agregue el identificador de lote de la aplicación como primer grupo.

    2. Agregue el grupo de cadenas de claves compartido `com.microsoft.intune.mam` a los grupos de acceso existentes. El SDK para aplicaciones de Intune usa este grupo de acceso para almacenar datos.

    3. Agregue `com.microsoft.adalcache` a los grupos de acceso existentes.

        4. Agregue `com.microsoft.workplacejoin` a los grupos de acceso existentes.
            ![SDK para aplicaciones de Intune para IOS: uso compartido de cadenas de claves](../media/intune-app-sdk-ios-keychain-sharing.png)

      5. Si usa el archivo de derechos para crear el grupo de acceso a cadenas de claves, anteponga `$(AppIdentifierPrefix)` al grupo de acceso a cadenas de claves en el archivo de derechos. Por ejemplo:

            * `$(AppIdentifierPrefix)com.microsoft.intune.mam`
            * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    > [!NOTE]
    > Un archivo de derechos es un archivo XML exclusivo para la aplicación móvil. Se usa para especificar permisos y capacidades especiales en la aplicación iOS.

7. Si la aplicación define esquemas URL en su archivo Info.plist, agregue otro esquema con un sufijo `-intunemam` para cada esquema URL.

8. En el caso de las aplicaciones móviles desarrolladas en iOS 9+, incluya cada protocolo que la aplicación pase a `UIApplication canOpenURL` en la matriz `LSApplicationQueriesSchemes` del archivo Info.plist de la aplicación. Además, agregue un nuevo protocolo y anéxele `-intunemam` para cada protocolo enumerado. También debe incluir `http-intunemam`, `https-intunemam` y `ms-outlook-intunemam` en la matriz.

9. Si la aplicación tiene definidos grupos de aplicaciones en sus derechos, agregue estos grupos al diccionario **IntuneMAMSettings** en la clave `AppGroupIdentifiers` como una matriz de cadenas.



## <a name="configure-azure-active-directory-authentication-library-adal"></a>Configurar Azure Active Directory Authentication Library (ADAL)

El SDK para aplicaciones de Intune usa [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) para sus escenarios de autenticación y de inicio condicional. También se basa en ADAL para registrar la identidad del usuario en el servicio MAM para la administración sin escenarios de inscripción de dispositivos.

Normalmente, ADAL exige que las aplicaciones se registren en Azure Active Directory (AAD) y que obtengan un identificador único (Id. de cliente) y otros identificadores para garantizar la seguridad de los tokens concedidos a la aplicación. A menos que se especifique lo contrario, el SDK para aplicaciones de Intune usa valores de registro predeterminados al ponerse en contacto con Azure AD.  

Si la aplicación ya usa ADAL para autenticar a los usuarios, debe usar sus valores de registro existentes y reemplazar los valores predeterminados del SDK para aplicaciones de Intune. Esto garantiza que no se pida a los usuarios autenticarse dos veces (una por parte del SDK para aplicaciones de Intune y otra por parte de la aplicación).

### <a name="recommendations"></a>Recomendaciones

Se recomienda vincular la aplicación a la [versión más reciente de ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) en su rama principal. El SDK para aplicaciones de Intune usa actualmente la rama de agente de ADAL para admitir aplicaciones que requieren acceso condicional. (Por tanto, estas aplicaciones dependen de la aplicación Microsoft Authenticator). Pero el SDK sigue siendo compatible con la rama principal de ADAL. Use la rama que sea adecuada para la aplicación.

### <a name="link-to-adal-binaries"></a>Vincular a archivos binarios de ADAL

Siga estos pasos para vincular la aplicación a los archivos binarios de ADAL:

1. Descargue [Azure Active Directory Authentication Library (ADAL) para Objective-C](https://github.com/AzureAD/azure-activedirectory-library-for-objc) desde GitHub y siga las [instrucciones](https://github.com/AzureAD/azure-activedirectory-library-for-objc/blob/master/README.md) para descargar ADAL mediante submódulos Git o CocoaPods.

2. Incluya el lote de recursos `ADALiOSBundle.bundle` en el proyecto al arrastrarlo desde **Copiar recursos del lote**, en **Fases de compilación**.

3. Agregue `-force_load {PATH_TO_LIB}/libADALiOS.a` a la opción de configuración de compilación `OTHER_LDFLAGS` del proyecto o a **Otras marcas del enlazador** en la interfaz de usuario. `PATH_TO_LIB` debe reemplazarse por la ubicación de los archivos binarios de ADAL.



### <a name="share-the-adal-token-cache-with-other-apps-signed-with-the-same-provisioning-profile"></a>Compartir la caché de tokens de ADAL con otras aplicaciones firmadas con el mismo perfil de aprovisionamiento**

Siga las instrucciones siguientes si quiere compartir los tokens de ADAL entre aplicaciones firmadas con el mismo perfil de aprovisionamiento:

1. Si la aplicación no tiene definido ningún grupo de acceso a cadenas de claves, agregue el identificador de lote de la aplicación como primer grupo.

2. Habilite el inicio de sesión único (SSO) de ADAL mediante la adición de los grupos de acceso `com.microsoft.adalcache` y `com.microsoft.workplacejoin` a los derechos de cadenas de claves.

3. Si establece explícitamente el grupo de cadenas de claves de caché compartida de ADAL, asegúrese de que esté establecido en `<app_id_prefix>.com.microsoft.adalcache`. ADAL lo establecerá automáticamente a menos que lo reemplace. Si quiere especificar un grupo de cadenas de claves personalizado para reemplazar a `com.microsoft.adalcache`, hágalo en el archivo Info.plist en IntuneMAMSettings, mediante la clave `ADALCacheKeychainGroupOverride`.

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>Configurar ADAL para el SDK para aplicaciones de Intune

Si la aplicación ya usa ADAL para la autenticación y tiene su propia configuración de ADAL, puede hacer que el SDK para aplicaciones de Intune use la misma configuración durante la autenticación en Azure Active Directory. Esto garantiza que la aplicación no pida al usuario que se autentique dos veces. Vea [Configurar los valores para el SDK para aplicaciones de Intune](#configure-settings-for-the-intune-app-sdk) para obtener información sobre cómo rellenar los valores siguientes:  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Si la aplicación ya usa ADAL, se necesitan las siguientes configuraciones:

1. En el archivo Info.plist del proyecto, en el diccionario **IntuneMAMSettings** con el nombre de clave `ADALClientId`, especifique el Id. de cliente que se va a usar para las llamadas a ADAL.

2. También en el diccionario **IntuneMAMSettings** con el nombre de clave `ADALAuthority`, especifique la entidad de Azure AD.

3. También en el diccionario **IntuneMAMSettings** con el nombre de clave `ADALRedirectUri`, especifique el URI de redireccionamiento que se va a usar para las llamadas a ADAL. Es posible que también tenga que especificar `ADALRedirectScheme`, según el formato del URI de redireccionamiento de la aplicación.


Además, puede reemplazar la dirección URL de la entidad de Azure AD por una dirección URL específica del inquilino en tiempo de ejecución. Para ello, basta con establecer la propiedad `aadAuthorityUriOverride` en la instancia `IntuneMAMPolicyManager`.

> [!NOTE]
> El establecimiento de la dirección URL de la entidad de AAD es necesario para que la [aplicación sin inscripción de dispositivos](#App-protection-policy-without-device-enrollment) permita que el SDK vuelva a usar el token de actualización de ADAL capturado por la aplicación.

El SDK seguirá usando esta dirección URL de la entidad para la actualización de directivas y las solicitudes de inscripción siguientes, a menos que se borre o se cambie el valor.  Por lo tanto, es importante borrar el valor cuando un usuario administrado cierre la sesión en la aplicación y restablecer el valor cuando un nuevo usuario administrado inicie sesión.

### <a name="if-your-app-does-not-use-adal"></a>Si la aplicación no usa ADAL

Si la aplicación no usa ADAL, el SDK para aplicaciones de Intune proporcionará valores predeterminados para los parámetros de ADAL y controlará la autenticación en Azure AD. No es necesario especificar ningún valor para la configuración de ADAL mencionada arriba.

## <a name="app-protection-policy-without-device-enrollment"></a>Directiva de protección de aplicaciones sin inscripción de dispositivos

### <a name="overview"></a>Información general
La directiva de protección de aplicaciones sin inscripción de dispositivos de Intune, también conocida como **APP-WE** o MAM-WE, permite que Intune administre las aplicaciones sin necesidad de que el dispositivo esté inscrito en la administración de dispositivos móviles (MDM) de Intune. Para admitir esta nueva funcionalidad, la aplicación debe registrar las cuentas de usuario para la administración. Para usar las nuevas API, siga estos pasos:

1. Use la versión más reciente del SDK para aplicaciones de Intune, que admite la administración de aplicaciones con o sin inscripción de dispositivos.

2. Agregue IntuneMAMEnrollment.h a cualquier archivo que llame a las API.

### <a name="register-user-accounts"></a>Registrar cuentas de usuario

Una aplicación puede recibir la directiva de protección de aplicaciones del servicio Intune si se inscribe en el servicio APP-WE en nombre de una cuenta de usuario especificada. La aplicación es responsable de registrar cualquier usuario que acabe de iniciar sesión con el SDK. Después de autenticar la nueva cuenta de usuario, la aplicación debe llamar al método `registerAndEnrollAccount` en Headers/IntuneMAMEnrollment.h:

```objc
/**


 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;

```
Al llamar al método `registerAndEnrollAccount`, el SDK registrará la cuenta de usuario e intentará inscribir la aplicación en nombre de esta cuenta. Si se produce un error en la inscripción por algún motivo, el SDK reintentará automáticamente la inscripción 24 horas más tarde. Para la depuración, la aplicación puede recibir notificaciones, a través de un delegado, sobre los resultados de las solicitudes de inscripción.

Después de invocar a esta API, la aplicación puede seguir funcionando normalmente. Si la inscripción se realiza correctamente, el SDK avisará al usuario de que se requiere un reinicio de la aplicación. En ese momento el usuario puede reiniciar la aplicación.

### <a name="deregister-user-accounts"></a>Anular el registro de cuentas de usuario

Antes de que un usuario cierre la sesión en una aplicación, esta debe anular el registro de ese usuario desde el SDK. Esto garantizará que:

1. Ya no se realicen reintentos de inscripción para la cuenta del usuario.

2. Se quite la directiva de protección de aplicaciones.

3. Se eliminen todos los datos corporativos si la aplicación inicia un borrado selectivo (opcional).

Antes de cerrar la sesión del usuario, la aplicación debe llamar a la siguiente API en `Headers/IntuneMAMEnrollment.h`:

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune MAM AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */

(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

Debe llamarse a este método antes de eliminar los tokens de Azure AD de la cuenta de usuario. El SDK necesita que los tokens de AAD de la cuenta de usuario realicen solicitudes específicas al servicio APP-WE en nombre del usuario.

Si la aplicación elimina los datos corporativos del usuario automáticamente, la marca `doWipe` puede establecerse en false. De lo contrario, la aplicación puede hacer que el SDK inicie un borrado selectivo. Esto dará lugar a una llamada al delegado de borrado selectivo de la aplicación.

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

### <a name="apps-that-do-not-use-adal"></a>Aplicaciones que no usan ADAL

Las aplicaciones en las que el usuario no inicia sesión mediante ADAL pueden seguir recibiendo la directiva de protección de aplicaciones del servicio Intune si llaman a la API para que el SDK controle esa autenticación. Las aplicaciones deben usar esta técnica si no han autenticado a un usuario con Azure AD pero siguen necesitando recuperar la directiva de protección de aplicaciones para ayudar a proteger los datos. Un ejemplo es si se usa otro servicio de autenticación para iniciar sesión en la aplicación, o si la aplicación no admite el inicio de sesión en absoluto. Para ello, la aplicación debe llamar al método `loginAndEnrollAccount` en Headers/IntuneMAMEnrollment.h:

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;

```

Al llamar a este método, si no se encuentra ningún token existente, el SDK le pide al usuario las credenciales. Luego el SDK intenta inscribir la aplicación con el servicio APP-WE en nombre de la cuenta de usuario proporcionada. Se puede llamar al método con "nil" como identidad. En ese caso, el SDK se inscribirá con el usuario administrado existente en el dispositivo o pedirá al usuario un nombre de usuario si no encuentra uno existente.

Si se produce un error en la inscripción, la aplicación debe considerar una nueva llamada a esta API en el futuro, según los detalles del error. La aplicación puede recibir [notificaciones](#Status-result-and-debug-notifications), a través de un delegado, sobre los resultados de las solicitudes de inscripción.

Después de invocar a esta API, la aplicación puede seguir funcionando normalmente. Si la inscripción se realiza correctamente, el SDK avisará al usuario de que se requiere un reinicio de la aplicación.

## <a name="status-result-and-debug-notifications"></a>Notificaciones de estado, resultado y depuración

La aplicación puede recibir notificaciones de estado, resultado y depuración sobre las siguientes solicitudes al servicio de MAM de Intune:

 - Solicitudes de inscripción
 - Solicitudes de actualización de directivas
 - Solicitudes de anulación de inscripción

Las notificaciones se presentan a través de métodos delegados en `Headers/IntuneMAMEnrollmentDelegate.h`:

```objc
/**
 *  Called when an enrollment request operation is completed.
 * @param status status object containing debug information
 */

(void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a MAM policy request operation is completed.
 *  @param status status object containing debug information
 */
(void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a un-enroll request operation is completed.
 *  @Note: when a user is un-enrolled, the user is also de-registered with the SDK
 *  @param status status object containing debug information
 */

(void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

```

Estos métodos delegados devuelven un objeto `IntuneMAMEnrollmentStatus` que tiene la siguiente información:

- La identidad de la cuenta asociada a la solicitud
- Un código de estado que indica el resultado de la solicitud
- Una cadena de error con una descripción del código de estado
- Un objeto `NSError`

Este objeto se define en `IntuneMAMEnrollmentStatus.h`, junto con los códigos de estado específicos que se pueden devolver.


### <a name="sample-code"></a>Código de ejemplo

Estas son implementaciones de ejemplo de los métodos delegados:

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}


- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

```

## <a name="app-restart"></a>Reinicio de la aplicación

Cuando una aplicación recibe directivas de protección de aplicaciones por primera vez, debe reiniciarse para aplicar los enlaces necesarios. Para notificar a la aplicación que debe reiniciarse, el SDK proporciona un método delegado en Headers/IntuneMAMPolicyDelegate.h.

```objc
 - (BOOL) restartApplication
```
El valor devuelto de este método indica al SDK si la aplicación debe controlar el reinicio necesario:   

 - Si devuelve true, la aplicación debe controlar el reinicio.   

 - Si devuelve false, el SDK reiniciará la aplicación después de que se devuelva este método. El SDK mostrará inmediatamente un cuadro de diálogo que indica al usuario que reinicie la aplicación.

## <a name="customize-your-apps-behavior"></a>Personalizar el comportamiento de la aplicación

El SDK para aplicaciones de Intune tiene varias API a las que se puede llamar para obtener información sobre la directiva de protección de aplicaciones de Intune implementada en la aplicación. Puede usar estos datos para personalizar el comportamiento de la aplicación. Es el SDK, y no la aplicación, el que aplica automáticamente la mayoría de los valores de la directiva de protección de aplicaciones. El único valor que debe implementar la aplicación es el control Guardar como.

### <a name="get-app-protection-policy"></a>Obtener la directiva de protección de aplicaciones

#### <a name="intunemampolicymanagerh"></a>IntuneMAMPolicyManager.h
La clase IntuneMAMPolicyManager expone la directiva de protección de aplicaciones de Intune implementada en la aplicación. En particular, expone las API que son útiles para [Habilitar varias identidades](#-enable-multi-identity-optional).

#### <a name="intunemampolicyh"></a>IntuneMAMPolicy.h
La clase IntuneMAMPolicy expone la directiva de protección de aplicaciones de Intune implementada en la aplicación. El SDK aplica la mayoría de los valores de la directiva expuestos en esta clase, aunque siempre puede personalizar el comportamiento de la aplicación según cómo se apliquen los valores de la directiva.

Esta clase expone algunas API necesarias para implementar controles Guardar como, que se detallan en la sección siguiente.

### <a name="implement-save-as-controls"></a>Implementar controles Guardar como

Intune permite a los administradores de TI seleccionar las ubicaciones de almacenamiento en las que una aplicación administrada puede guardar datos. Las aplicaciones pueden consultar al SDK para aplicaciones de Intune sobre las ubicaciones de almacenamiento permitidas mediante la API **isSaveToAllowedForLocation**, definida en **IntuneMAMPolicy.h**.

Para que las aplicaciones puedan guardar datos administrados en una ubicación de almacenamiento local o en la nube, primero deben consultar a la API **isSaveToAllowedForLocation** para saber si los administradores de TI han permitido guardar datos allí.

Cuando las aplicaciones usan la API **isSaveToAllowedForLocation**, deben pasar el UPN de la ubicación de almacenamiento, si está disponible.

#### <a name="supported-save-locations"></a>Ubicaciones de almacenamiento admitidas

La API **isSaveToAllowedForLocation** proporciona constantes para comprobar si los administradores de TI permiten guardar datos en las siguientes ubicaciones definidas en IntuneMAMPolicy.h:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

Las aplicaciones deben usar las constantes de la API **isSaveToAllowedForLocation** para comprobar si se pueden guardar datos en ubicaciones consideradas "administradas", como OneDrive para la Empresa, o "personales". Además, debe usarse la API cuando la aplicación no puede comprobar si una ubicación es "administrada" o "personal".

Las ubicaciones que son "personales" están representadas por la constante `IntuneMAMSaveLocationOther`.

La constante `IntuneMAMSaveLocationLocalDrive` debe usarse cuando la aplicación está guardando datos en cualquier ubicación en el dispositivo local.

## <a name="configure-settings-for-the-intune-app-sdk"></a>Configurar los valores para el SDK para aplicaciones de Intune

Puede usar el diccionario **IntuneMAMSettings** del archivo Info.plist de la aplicación para configurar el SDK para aplicaciones de Intune. Si no se ve el diccionario IntuneMAMSettings en el archivo Info.plist, debe crear un diccionario en el archivo Info.plist de la aplicación con el nombre del campo "IntuneMAMSettings".

En el diccionario IntuneMAMSettings puede agregar filas de clave y valor de configuración para configurar el SDK. En la tabla siguiente se enumeran todas las configuraciones admitidas.

Es posible que algunas se hayan tratado en las secciones anteriores y que otras no se apliquen a todas las aplicaciones.

Configuración  | Tipo  | Definición | ¿Necesario?
--       |  --   |   --       |  --
ADALClientId  | String  | Identificador de cliente de Azure AD de la aplicación. | Necesario si la aplicación usa ADAL. |
ADALAuthority | String | Entidad de Azure AD de la aplicación en uso. Debe usar su propio entorno donde se hayan configurado cuentas de AAD. | Necesario si la aplicación usa ADAL. Si este valor está ausente, se usa un valor predeterminado de Intune.|
ADALRedirectUri  | String  | URI de redireccionamiento de Azure AD de la aplicación. | ADALRedirectUri o ADALRedirectScheme es necesario si la aplicación usa ADAL.  |
ADALRedirectScheme  | String  | Esquema de redireccionamiento de Azure AD de la aplicación. Puede usarse en lugar de ADALRedirectUri si el URI de redireccionamiento de la aplicación está en el formato `scheme://bundle_id`. | ADALRedirectUri o ADALRedirectScheme es necesario si la aplicación usa ADAL. |
ADALLogOverrideDisabled | Boolean  | Especifica si el SDK enrutará todos los registros de ADAL (incluidas las llamadas a ADAL desde la aplicación, de haberlas) a su propio archivo de registro. El valor predeterminado es NO. Establezca en YES si la aplicación establecerá su propia devolución de llamada de registros ADAL. | Opcional. |
ADALCacheKeychainGroupOverride | String  | Especifica el grupo de cadenas de claves que se va a usar para la caché de ADAL en lugar de "com.microsoft.adalcache". Tenga en cuenta que no tiene el prefijo de identificador de la aplicación. Ese se anexará a la cadena proporcionada en tiempo de ejecución. | Opcional. |
AppGroupIdentifiers | Matriz de cadena  | Matriz de grupos de aplicación de la sección de grupos de com.apple.security.application-groups de derechos de la aplicación. | Se requiere si la aplicación usa grupos de aplicaciones. |
ContainingAppBundleId | String | Especifica el identificador de lote de la aplicación que contiene la extensión. | Se requiere para las extensiones de iOS. |
DebugSettingsEnabled| Boolean | Si se establece en YES, se pueden aplicar directivas de prueba dentro del lote Configuración. Las aplicaciones *no* deben enviarse con este valor habilitado. | Opcional. |
MainNibFile<br>MainNibFile~ipad  | String  | Este valor debe tener el nombre de archivo nib principal de la aplicación.  | Necesario si la aplicación define MainNibFile en Info.plist. |
MainStoryboardFile<br>MainStoryboardFile~ipad  | String  | Este valor debe tener el nombre de archivo de guión gráfico principal de la aplicación. | Necesario si la aplicación define UIMainStoryboardFile en Info.plist. |
MAMPolicyRequired| Boolean| Especifica si se evitará que la aplicación se inicie si no tiene una directiva de protección de aplicaciones de Intune. El valor predeterminado es NO. <br><br> Nota: Las aplicaciones no se puede enviar al App Store con MAMPolicyRequired establecido en YES. | Opcional. |
MAMPolicyWarnAbsent | Boolean| Especifica si la aplicación advertirá al usuario durante el inicio si no tiene una directiva de protección de aplicaciones de Intune. Tenga en cuenta que las aplicaciones no se pueden enviar a la tienda con este valor establecido en YES. | Opcional. |
MultiIdentity | Boolean| Especifica si la aplicación reconoce varias identidades. | Opcional. |
SplashIconFile <br>SplashIconFile~ipad | String  | Especifica el archivo de icono de la pantalla de presentación de Intune (inicio). | Opcional. |
SplashDuration | Número | Cantidad mínima de tiempo, en segundos, que se mostrará la pantalla de inicio de Intune al iniciar la aplicación. El valor predeterminado es 1,5. | Opcional. |
BackgroundColor| String| Especifica el color de fondo de las pantallas de inicio y PIN. Acepta una cadena RGB hexadecimal en formato #XXXXXX, donde X puede estar comprendido entre 0 y 9 o A y F. Se puede omitir el signo de libra esterlina.   | Opcional. El valor predeterminado es gris claro. |
ForegroundColor| String| Especifica el color de primer plano de las pantallas de inicio y PIN, como el color de texto. Acepta una cadena RGB hexadecimal en formato #XXXXXX, donde X puede estar comprendido entre 0 y 9 o A y F. Se puede omitir el signo de libra esterlina.  | Opcional. El valor predeterminado es negro. |
AccentColor | String| Especifica el color de énfasis de la pantalla de PIN, como el color de texto de botón y el color de resaltado de cuadro. Acepta una cadena RGB hexadecimal en formato #XXXXXX, donde X puede estar comprendido entre 0 y 9 o A y F. Se puede omitir el signo de libra esterlina.| Opcional. El valor predeterminado es azul del sistema. |
MAMTelemetryDisabled| Boolean| Especifica si el SDK no enviará datos de telemetría a su back-end.| Opcional. |

> [!NOTE]
> Si la aplicación se va a publicar en el App Store, `MAMPolicyRequired` debe establecerse en "NO", según los estándares del App Store.

## <a name="telemetry"></a>Telemetría

De forma predeterminada, el SDK para aplicaciones de Intune para iOS registra los datos de telemetría en los siguientes eventos de uso. Estos datos se envían a Microsoft Intune.

* **Inicio de aplicación**: para ayudar a Microsoft Intune a obtener información sobre el uso de la aplicación habilitada para MAM por tipo de administración (MAM con MDM, MAM sin inscripción MDM, etc.).

* **Llamadas de inscripción**: para ayudar a Microsoft Intune a obtener información sobre la tasa de éxito y otras métricas de rendimiento de las llamadas de inscripción iniciadas desde el cliente.

> [!NOTE]
> Si decide no enviar datos de telemetría del SDK para aplicaciones de Intune a Microsoft Intune desde la aplicación móvil, debe deshabilitar la captura de telemetría del SDK para aplicaciones de Intune. Establezca la propiedad `MAMTelemetryDisabled` en YES en el diccionario IntuneMAMSettings.

## <a name="enable-multi-identity-optional"></a>Habilitar varias identidades (opcional)

De forma predeterminada, el SDK aplica una directiva a la aplicación como un todo. Varias identidades es una característica de MAM que puede habilitar para aplicar una directiva por identidad. Esto exige más participación de la aplicación que otras características de MAM.

La aplicación debe informar al SDK de la aplicación cuando intenta cambiar la identidad activa. El SDK además notifica a la aplicación cuando se requiere un cambio de identidad. Actualmente, solo se admite una identidad administrada. Una vez que el usuario inscribe el dispositivo o la aplicación, el SDK usa esta identidad y la considera la identidad administrada principal. Los demás usuarios de la aplicación se tratarán como usuarios no administrados con una configuración de directiva sin restricciones.

Tenga en cuenta que una identidad se define simplemente como una cadena. Las identidades no distinguen mayúsculas de minúsculas. Las solicitudes de identidades que se realizan al SDK podrían no devolverse con el mismo uso de mayúsculas y minúsculas que se empleó originalmente al establecer la identidad.

### <a name="identity-overview"></a>Información general sobre la identidad

Una identidad simplemente es el nombre de usuario de una cuenta (por ejemplo, user@contoso.com). Los desarrolladores pueden establecer la identidad de la aplicación en los siguientes niveles:

* **Identidad de proceso**: establece la identidad de todo el proceso y se usa principalmente para aplicaciones de identidad única. Esta identidad afecta a todas las tareas, los archivos y la interfaz de usuario.

* **Identidad de interfaz de usuario**: determina qué directivas se aplican a las tareas de la interfaz de usuario en el subproceso principal, como cortar, copiar y pegar; PIN; autenticación y uso compartido de datos. La identidad de interfaz de usuario no afecta a tareas de archivo como copia de seguridad y cifrado.

* **Identidad de subproceso**: afecta a qué directivas se aplican en el subproceso actual. Esta identidad afecta a todas las tareas, los archivos y la interfaz de usuario.

La aplicación es responsable de establecer las identidades de forma adecuada, tanto si el usuario está administrado como si no.

En cualquier momento, cada subproceso tiene una identidad efectiva para tareas de interfaz de usuario y tareas de archivo. Se trata de la identidad que se usa para comprobar qué directivas, si las hubiera, se deben aplicar. Si la identidad es "ninguna identidad" o el usuario no está administrado, no se aplica ninguna directiva. En los diagramas siguientes se muestra cómo se determinan las identidades efectivas.

  ![SDK para aplicaciones de Intune para iOS: marcos de trabajo y bibliotecas vinculados](../media/intune-app-sdk/ios-thread-identities.png)

### <a name="thread-queues"></a>Colas de subprocesos

Las aplicaciones a menudo envían tareas sincrónicas y asincrónicas a colas de subprocesos. El SDK intercepta las llamadas a Grand Central Dispatch (GCD) y asocia la identidad del subproceso actual a las tareas enviadas. Cuando las tareas terminan, el SDK cambia temporalmente la identidad del subproceso a la identidad asociada a las tareas, finaliza las tareas y restaura la identidad del subproceso original.


Dado que `NSOperationQueue` se basa en GCD, `NSOperations` se ejecutará en la identidad del subproceso en el momento de agregar las tareas a `NSOperationQueue`. `NSOperations` o las funciones enviadas directamente a través de GCD también pueden cambiar la identidad del subproceso actual mientras se ejecutan. Esta identidad invalidará la identidad heredada del subproceso que envía.

### <a name="file-owner"></a>Propietario del archivo

El SDK realiza un seguimiento de las identidades de los propietarios de archivos locales y aplica las directivas según corresponda. Un propietario de archivo se establece cuando se crea un archivo o cuando se abre en modo de truncamiento. El propietario se establece en la identidad de la tarea de archivo real del subproceso que está realizando la tarea.

Como alternativa, las aplicaciones pueden establecer la identidad del propietario del archivo explícitamente mediante `IntuneMAMFilePolicyManager`. Las aplicaciones pueden usar `IntuneMAMFilePolicyManager` para recuperar el propietario del archivo y establecer la identidad de la interfaz de usuario antes de mostrar el contenido del archivo.

### <a name="shared-data"></a>Datos compartidos

Si la aplicación crea archivos con datos de usuarios administrados y no administrados, la aplicación es responsable de cifrar los datos del usuario administrado. Puede cifrar los datos mediante las API `protect` y `unprotect` de `IntuneMAMDataProtectionManager`.

El método `protect` acepta una identidad que puede ser un usuario administrado o no administrado. Si el usuario está administrado, se cifrarán los datos. Si el usuario no está administrado, se agregará un encabezado a los datos que codifican la identidad, pero no se cifrarán los datos en sí. Puede usar el método `protectionInfo` para recuperar el propietario de los datos.

### <a name="share-extensions"></a>Extensiones compartidas

Si la aplicación tiene una extensión compartida, se puede recuperar el propietario del elemento que se comparte mediante el método `protectionInfoForItemProvider` de `IntuneMAMDataProtectionManager`. Si el elemento compartido es un archivo, el SDK controlará la configuración de propietario del archivo. Si el elemento compartido son datos, la aplicación es responsable de establecer el propietario del archivo si estos datos se guardan en un archivo y de llamar a la API `setUIPolicyIdentity` antes de mostrar estos datos en la interfaz de usuario.

### <a name="turning-on-multi-identity"></a>Activación de varias identidades

De forma predeterminada, las aplicaciones se consideran una identidad única. El SDK establece la identidad del proceso en el usuario inscrito. Para habilitar la compatibilidad con varias identidades, agregue un valor booleano con el nombre `MultiIdentity` y un valor YES al diccionario IntuneMAMSettings en el archivo Info.plist de la aplicación.

> [!NOTE]
> Cuando hay varias identidades habilitadas, la identidad del proceso, la identidad de la interfaz de usuario y las identidades del subproceso se establecen en nulo. La aplicación es responsable de configurarlas de forma adecuada.

### <a name="switching-identities"></a>Cambio de identidades

* **Cambio de identidad iniciado por la aplicación**:

    Durante el inicio, se considera que las aplicaciones de varias identidades se ejecutan en una cuenta desconocida no administrada. La interfaz de usuario de inicio condicional no se ejecutará ni se aplicará ninguna directiva en la aplicación. La aplicación es responsable de notificar al SDK siempre que haya que cambiar la identidad. Normalmente, esto ocurre cada vez que la aplicación está a punto de mostrar datos de una cuenta de usuario determinada.

    Un ejemplo es cuando el usuario intenta abrir un documento, un buzón o una pestaña de un bloc de notas. La aplicación debe notificar al SDK antes de que el archivo, el buzón o la pestaña se abra realmente. Esto se hace mediante la API `setUIPolicyIdentity` de `IntuneMAMPolicyManager`. Se debe llamar a esta API tanto si el usuario está administrado como si no. Si el usuario está administrado, el SDK llevará a cabo las comprobaciones de inicio condicional, como la detección de Jailbreak, el PIN y la autenticación.

    El resultado del cambio de identidad se devuelve a la aplicación de forma asincrónica a través de un controlador de finalización. La aplicación debe posponer la apertura del documento, el buzón o la pestaña hasta que se devuelva un código de resultado correcto. Si se produce un error en el cambio de identidad, la aplicación debe cancelar la tarea.

* **Cambio de identidad iniciado por el SDK**:

    A veces, el SDK tiene que pedir a la aplicación que cambie a una identidad concreta. Las aplicaciones de varias identidades deben implementar el método `identitySwitchRequired` en `IntuneMAMPolicyDelegate` para controlar esta solicitud.

    Cuando se llama a este método, si la aplicación puede controlar la solicitud de cambio a la identidad especificada, debe pasar `IntuneMAMAddIdentityResultSuccess` al controlador de finalización. Si no puede controlar el cambio de la identidad, la aplicación debe pasar `IntuneMAMAddIdentityResultFailed` al controlador de finalización.

    La aplicación no tiene que llamar a `setUIPolicyIdentity` en respuesta a esta llamada. Si el SDK necesita que la aplicación cambie a una cuenta de usuario no administrada, se pasará la cadena vacía a la llamada `identitySwitchRequired`.

* **Borrado selectivo**:

    Cuando la aplicación se borra de forma selectiva, el SDK llama al método `wipeDataForAccount` en `IntuneMAMPolicyDelegate`. La aplicación es responsable de quitar la cuenta de usuario especificada y cualquier dato asociado a ella. El SDK es capaz de quitar todos los archivos que pertenecen al usuario y así lo hará si la aplicación devuelve FALSE desde la llamada `wipeDataForAccount`.

    Tenga en cuenta que se llama a este método desde un subproceso en segundo plano. La aplicación no debe devolver un valor hasta que se hayan quitado todos los datos del usuario (a excepción de los archivos si la aplicación devuelve FALSE).

## <a name="test-app-protection-policy-settings-in-xcode"></a>Probar la configuración de las directivas de protección de aplicaciones en Xcode

Antes de probar la aplicación habilitada para Intune manualmente en producción, puede usar un archivo Settings.bundle en Xcode. Esto le permitirá establecer directivas de protección de aplicaciones para pruebas sin necesidad de una conexión a Intune.

### <a name="enable-policy-testing"></a>Habilitar pruebas de directivas

Siga los pasos siguientes para habilitar las pruebas de directivas en Xcode:

1. Asegúrese de estar en una compilación de depuración. Agregue un archivo Settings.bundle al hacer clic con el botón derecho en la carpeta de nivel superior del proyecto. Elija **Agregar** > **Nuevo archivo** en el menú. En **Recursos**, elija la plantilla **Lote de configuración**.

2.  Copie el siguiente bloque en el archivo Settings.bundle/**Root.plist** de la compilación de depuración:
    ```xml
    <key>PreferenceSpecifiers</key>
    <array>
        <dict>
            <key>Type</key>
            <string>PSChildPaneSpecifier</string>
            <key>Title</key>
            <string>MDM Debug Settings</string>
            <key>Key</key>
            <string>MAMDebugSettings</string>
            <key>File</key>
            <string>MAMDebugSettings</string>
        </dict>
    </array>
    ```

3. En el diccionario **IntuneMAMSettings** del archivo Info.plist de la aplicación, agregue un valor booleano denominado "DebugSettingsEnabled". Establezca el valor de DebugSettingsEnabled en "YES".



### <a name="app-protection-policy-settings"></a>Configuración de directivas de protección de aplicaciones

La siguiente tabla describe las configuraciones de directivas de protección de aplicaciones que se pueden probar con MAMDebugSettings.plist. Para activar una configuración, agréguela a MAMDebugSettings.plist.

| Nombre de la configuración de directiva | Descripción | Valores posibles |
| -- | -- | -- |
| AccessRecheckOfflineTimeout | Tiempo en minutos que la aplicación puede estar sin conexión antes de que Intune bloquee su inicio o reanudación si la autenticación está habilitada. | Cualquier entero mayor que 0 |
|    AccessRecheckOnlineTimeout | Tiempo en minutos que se puede ejecutar la aplicación antes de que se pida al usuario el PIN o la autenticación durante el inicio o la reanudación (si está habilitada la autenticación o el PIN para el acceso). | Cualquier entero mayor que 0 |
| AppSharingFromLevel | Especifica de qué aplicaciones puede aceptar datos esta aplicación. | 0 = |
## <a name="ios-best-practices"></a>Procedimientos recomendados de iOS

Aquí se explican algunos procedimientos recomendados para desarrollar para iOS:

* El sistema de archivos iOS distingue mayúsculas de minúsculas. Asegúrese de que la grafía sea correcta para los nombres de archivo como `libIntuneMAM.a` e `IntuneMAMResources.bundle`.

* Si Xcode tiene problemas para encontrar `libIntuneMAM.a`, puede solucionar el problema si agrega la ruta de acceso a esta biblioteca en las rutas de acceso de búsqueda del enlazador.

## <a name="faqs"></a>Preguntas más frecuentes


**¿Todas las API son direccionables a través de Swift nativo o la interoperabilidad de Objective-C y Swift?**

Las API del SDK para aplicaciones de Intune solo están en Objective-C y no admiten Swift **nativo**. Se necesita interoperabilidad de Swift con Objective-C.


**¿Todos los usuarios de mi aplicación deben estar registrados en el servicio APP-WE?**

No. De hecho, solo las cuentas educativas o profesionales se deben registrar en el SDK para aplicaciones de Intune. Las aplicaciones son responsables de determinar si una cuenta se usa en un contexto educativo o profesional.   

**¿Qué sucede con los usuarios que ya han iniciado sesión en la aplicación? ¿Tienen que inscribirse?**

La aplicación es responsable de inscribir a los usuarios después de que se hayan autenticado correctamente. La aplicación también es responsable de inscribir cualquier cuenta existente que pudiera estar presente antes de que la aplicación tuviera funcionalidad MAM sin MDM.   

Para ello, la aplicación debe usar el método `registeredAccounts:`. Este método devuelve un NSDictionary que tiene todas las cuentas registradas en el servicio de MAM de Intune. Si alguna cuenta existente en la aplicación no está en la lista, la aplicación debe registrarla e inscribirla mediante `registerAndEnrollAccount:`.

**¿Con qué frecuencia reintenta el SDK las inscripciones?**

El SDK volverá a intentar automáticamente todas las inscripciones previas erróneas en un intervalo de 24 horas. El SDK hace esto para asegurarse de que si la organización de un usuario ha habilitado MAM después de que el usuario iniciara sesión en la aplicación, este se inscriba correctamente y reciba las directivas.

El SDK dejará de reintentar cuando detecte que un usuario ha inscrito correctamente la aplicación. Esto se debe a que solo un usuario puede inscribir una aplicación en un momento determinado. Si se anula la inscripción del usuario, los reintentos comenzarán de nuevo en el mismo intervalo de 24 horas.

**¿Por qué hay que anular el registro del usuario?**

El SDK tomará periódicamente estas mediadas en segundo plano:

 - Si la aplicación aún no se ha inscrito, intentará inscribir todas las cuentas registradas cada 24 horas.
 - Si la aplicación está inscrita, el SDK comprobará las actualizaciones de la directiva de protección de aplicaciones cada 8 horas.

Al anular el registro de un usuario, se notifica al SDK que el usuario ya no va a usar la aplicación y el SDK puede detener cualquiera de los eventos periódicos de esa cuenta de usuario. También se desencadena la anulación de la inscripción de una aplicación y un borrado selectivo en caso necesario.

**¿Debo establecer la marca doWipe en true en el método de anulación del registro?**

Se debe llamar a este método antes de que el usuario cierre la sesión en la aplicación.  Si los datos del usuario se eliminan de la aplicación como parte del cierre de sesión, `doWipe` se puede establecer en false. Pero si la aplicación no quita los datos del usuario, `doWipe` debe establecerse en true para que el SDK pueda eliminarlos.

**¿Hay otras maneras de anular la inscripción de una aplicación?**

Sí, los administradores de TI pueden enviar un comando de borrado selectivo a la aplicación. Con esto se anula el registro y la inscripción del usuario y se borran sus datos. El SDK controla este escenario automáticamente y envía una notificación a través del método delegado de anulación del registro.



## <a name="submit-your-app-to-the-app-store"></a>Enviar la aplicación al App Store

Las compilaciones de la biblioteca estática y el marco de trabajo del SDK para aplicaciones de Intune son binarios universales. Esto significa que tienen código para todas las arquitecturas de dispositivo y simulador. Apple rechazará aquellas aplicaciones enviadas al App Store que tengan código de simulador. Al compilar con la biblioteca estática para las compilaciones de solo dispositivo, el enlazador eliminará automáticamente el código de simulador. Siga los pasos siguientes para asegurarse de que todo el código de simulador se quite antes de cargar la aplicación en el App Store.

1. Asegúrese de que `IntuneMAM.framework` esté en el escritorio.

2. Ejecute estos comandos:

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```
    El primer comando elimina las arquitecturas de simulador del archivo DYLIB del marco de trabajo. El segundo comando vuelve a copiar el archivo DYLIB de solo dispositivo en el directorio del marco de trabajo.

