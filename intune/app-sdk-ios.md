---
title: "Guía para desarrolladores acerca del SDK de aplicaciones de Microsoft Intune para iOS"
description: "El SDK de la aplicación Microsoft Intune para iOS permite incorporar directivas de protección de aplicaciones de Intune, en forma de administración de aplicaciones móviles (MAM), en su aplicación iOS."
keywords: 
author: erikre
manager: angrobe
ms.author: erikre
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 031ae18fb88a04cd02ca3ced5c39a33e49610bef
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Guía para desarrolladores sobre el SDK para aplicaciones de Microsoft Intune para iOS

> [!NOTE]
> Puede que primero quiera leer el artículo [Introducción al SDK para aplicaciones de Microsoft Intune](app-sdk-get-started.md), en el que se explica cómo preparar la integración en cada plataforma compatible.

Microsoft Intune App SDK para iOS permite incorporar directivas de protección de aplicaciones de Intune, también conocidas como **APP** o **directivas MAM**, a la aplicación iOS nativa. Una aplicación habilitada para MAM es aquella que está integrada con el SDK para aplicaciones de Intune. Los administradores de TI pueden implementar directivas de protección de aplicaciones en la aplicación móvil cuando Intune la administra activamente.

## <a name="prerequisites"></a>Requisitos previos

* Necesita un equipo Mac OS que ejecute OS X 10.8.5 o posterior y que tenga instalada XCode 8 o posterior.

* Debe elegir la aplicación para iOS 9 o posterior.

* Revise los [términos de licencia del SDK de aplicaciones de Intune para iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS%20.pdf). Imprima y conserve una copia de los términos de licencia para sus registros. Al descargar y usar el SDK de aplicaciones de Intune para iOS, acepta dichos términos.  Si no los acepta, no use el software.

* Descargue los archivos del SDK de aplicaciones de Intune para iOS en [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios).

## <a name="whats-in-the-sdk"></a>Qué hay en el SDK

El SDK para aplicaciones de Intune para iOS incluye una biblioteca estática, archivos de recursos, encabezados de API, un archivo .plist de configuración de depuración y una herramienta de configuración. Las aplicaciones móviles pueden incluir simplemente los archivos de recursos y vincularse estáticamente para la mayor parte de la aplicación de las directivas. Las características avanzadas de MAM de Intune se aplican a través de las API.

En esta guía se tratará el uso de los siguientes componentes del SDK de aplicaciones de Intune para iOS:

* **libIntuneMAM.a**: biblioteca estática del SDK de aplicaciones de Intune. Si su aplicación no usa extensiones, vincule esta biblioteca al proyecto para habilitar la aplicación para la administración de aplicaciones móviles de Intune.

* **IntuneMAM.framework**: marco del SDK de aplicaciones Intune. Vincule este marco al proyecto para habilitar la aplicación para la administración de aplicaciones móviles de Intune. Si la aplicación emplea extensiones, use el marco de trabajo en lugar de la biblioteca estática para que el proyecto no cree varias copias de esta.

* **IntuneMAMResources.Bundle**: lote de recursos que contiene los recursos en los que se basa el SDK.

* **Encabezados**: expone las API del SDK para aplicaciones de Intune. Si usa una API, deberá incluir el archivo de encabezado que contiene la API. Los siguientes archivos de encabezado incluyen las API, los tipos de datos y los protocolos que Intune App SDK pone a disposición de los desarrolladores:

    * IntuneMAMAppConfig.h
    * IntuneMAMAppConfigManager.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMDefs.h
    * IntuneMAMEnrollmentDelegate.h
    * IntuneMAMEnrollmentManager.h
    * IntuneMAMEnrollmentStatus.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMLogger.h
    * IntuneMAMPolicy.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMPolicyManager.h
    * IntuneMAMVersionInfo.h
    
Los desarrolladores pueden hacer que el contenido de todos los encabezados anteriores esté disponible importando solamente IntuneMAM.h.


## <a name="how-the-intune-app-sdk-works"></a>Cómo funciona el SDK para aplicaciones de Intune

El objetivo del SDK para aplicaciones de Intune para iOS es agregar capacidades de administración a las aplicaciones de iOS con mínimos cambios en el código. Cuantos menos cambios se hagan en el código, menor será el tiempo de comercialización; sin afectar a la coherencia y la estabilidad de la aplicación móvil seguirán estando garantizadas.


## <a name="build-the-sdk-into-your-mobile-app"></a>Integrar el SDK en la aplicación móvil

Para habilitar el SDK para aplicaciones de Intune, siga estos pasos:

1. **Opción 1 (recomendada)**: vínculo `IntuneMAM.framework` al proyecto. Arrastre `IntuneMAM.framework` a la lista **Embedded Binaries** (Binarios insertados) del destino del proyecto.

    > [!NOTE]
    > Si usa el marco, debe quitar manualmente las arquitecturas de simulador del marco universal antes de enviar la aplicación a la Tienda de aplicaciones. Vea [Enviar la aplicación a la Tienda de aplicaciones](#Submit-your-app-to-the-App-Store) para más información.

2. **Opción 2**: vincular a la biblioteca `libIntuneMAM.a`. Arrastre la bibloteca `libIntuneMAM.a` en la lista de **Linked Frameworks and Libraries** (Marcos y bibliotecas vinculados) del destino del proyecto.

    ![Intune App SDK para iOS: marcos y bibliotecas vinculados](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    Agregue `-force_load {PATH_TO_LIB}/libIntuneMAM.a` a cualquiera de lo siguiente, reemplazando `{PATH_TO_LIB}` por la ubicación del SDK para aplicaciones de Intune:
      * Ajuste de la configuración de compilación `OTHER_LDFLAGS` del proyecto
      * **Otras marcas del enlazador** de la interfaz de usuario de Xcode

        > [!NOTE]
        > Para encontrar `PATH_TO_LIB`, seleccione el archivo `libIntuneMAM.a` y elija **Obtener información** en el menú **Archivo**. Copie y pegue la información **Dónde** (la ruta de acceso) de la sección **General** de la ventana **Información**.

    Agregue el lote de recursos `IntuneMAMResources.bundle` al proyecto arrastrando el lote de recursos de **Copy Bundle Resources** (Copiar recursos del lote) en **Build Phases** (Fases de compilación).

    ![SDK de aplicaciones de Intune para iOS: copiar recursos del lote](./media/intune-app-sdk-ios-copy-bundle-resources.png)

    Agregue estos marcos de iOS al proyecto:          * MessageUI.framework          * Security.framework          * MobileCoreServices.framework          * SystemConfiguration.framework          * libsqlite3.tbd          * libc++.tbd          * ImageIO.framework          * LocalAuthentication.framework          * AudioToolbox.framework          * QuartzCore.framework          * WebKit.framework

3. Para habilitar el uso compartido de la cadena de claves (si aún no está habilitado), elija **Capacidades** en cada destino del proyecto y habilite el modificador del **uso compartido de cadena de claves**. El uso compartido de cadena de claves es necesario para que continúe con el siguiente paso.

  > [!NOTE]
    > El perfil de aprovisionamiento debe admitir nuevos valores de uso compartido de cadena de claves. Los grupos de acceso a cadena de claves deben admitir un carácter comodín. Para comprobar esto, abra el archivo .mobileprovision en un editor de texto, busque **keychain-access-groups** y asegúrese de que tiene un carácter comodín. Por ejemplo:
    ```xml
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```

4. Después de habilitar el uso compartido de cadena de claves, siga estos pasos para crear un grupo de acceso independiente en el que se almacenarán los datos del SDK para aplicaciones de Intune. Puede crear un grupo de acceso a cadenas de claves mediante la interfaz de usuario o mediante el archivo de derechos. Si utiliza la interfaz de usuario para crear el grupo de acceso de la cadena de claves, asegúrese de seguir los pasos siguientes:

    1. Si la aplicación móvil no tiene ningún grupo de acceso a cadena de claves definido, agregue el id. del lote de la aplicación como el primer grupo.

    2. Agregue el grupo de cadena de claves compartido `com.microsoft.intune.mam` a los grupos de acceso existentes. El SDK para aplicaciones de Intune usa este grupo de acceso para almacenar datos.

    3. Agregue `com.microsoft.adalcache` a los grupos de acceso existentes.

        ![Intune App SDK iOS: uso compartido de cadena de claves](./media/intune-app-sdk-ios-keychain-sharing.png)

    4. Si edita el archivo de derechos directamente, en lugar de usar la interfaz de usuario de Xcode mostrada anteriormente para crear los grupos de acceso a cadena de claves, anteponga `$(AppIdentifierPrefix)` a dichos grupos (Xcode lo hace automáticamente). Por ejemplo:

            * `$(AppIdentifierPrefix)com.microsoft.intune.mam`
            * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    > [!NOTE]
    > Un archivo de derechos es un archivo XML exclusivo para la aplicación móvil. Se utiliza para especificar permisos especiales y capacidades en su aplicación iOS. Si la aplicación no disponía anteriormente de un archivo de títulos, Xcode generará uno para la aplicación después de habilitar el uso compartido de la cadena claves (paso 3).

5. Incluya cada protocolo que la aplicación pasa a `UIApplication canOpenURL` en la matriz `LSApplicationQueriesSchemes` del archivo Info.plist de la aplicación. Asegúrese de guardar los cambios antes de continuar con el paso siguiente.

6. Use la herramienta IntuneMAMConfigurator que se incluye en el [repositorio de SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) para finalizar la configuración de Info.plist de la aplicación. La herramienta tiene 3 parámetros:
|Propiedad|Cómo usarla|
|---------------|--------------------------------|
|- i |  `<Path to the input plist>` |
|- e | `<Path to the entitlements file>` |
|- o |  (Opcional) `<Path to the output plist>`. |

Si el parámetro "-o" no se especifica, el archivo de entrada se modificará en contexto. La herramienta es idempotente y debe volver a ejecutarse cada vez que se realicen cambios en Info.plist o los derechos de la aplicación. También debe descargar y ejecutar la versión más reciente de la herramienta al actualizar el SDK de Intune, en caso de que los requisitos de configuración de Info.plist hayan cambiado en la versión más reciente.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Configurar Azure Active Directory Authentication Library (ADAL)

Intune App SDK usa [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) para sus escenarios de inicio condicional y de autenticación. También se basa en ADAL para registrar la identidad del usuario en el servicio MAM para la administración sin escenarios de inscripción de dispositivos.

Normalmente, ADAL requiere que las aplicaciones se registren con Azure Active Directory (AAD) y que obtengan un identificador único (ClientID), y otros identificadores para garantizar la seguridad de los tokens concedidos a la aplicación. A menos que se especifique lo contrario, Intune App SDK usa valores de registro predeterminados al ponerse en contacto con Azure AD.  

Si su aplicación ya usa ADAL para la autenticación de usuarios, la aplicación debe utilizar los valores de registro existentes y reemplazar los valores predeterminados de Intune App SDK. Esto garantiza que no se pida a los usuarios autenticarse dos veces (una por parte del SDK para aplicaciones de Intune y otra por parte de la aplicación).

### <a name="recommendations"></a>Recomendaciones

Se recomienda que la aplicación se vincule a la [versión más reciente de ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) en la bifurcación principal. Intune App SDK usa actualmente la bifurcación del agente de ADAL para admitir aplicaciones que requieren acceso condicional. (Por tanto, estas aplicaciones dependen de la aplicación Microsoft Authenticator). Sin embargo, el SDK sigue siendo compatible con la bifurcación principal de ADAL. Use la rama que sea adecuada para la aplicación.

### <a name="link-to-adal-binaries"></a>Vincular a archivos binarios de ADAL

Siga los pasos siguientes para vincular la aplicación a los archivos binarios de ADAL:

1. Descargue [Azure Active Directory Authentication Library (ADAL) para Objective-C](https://github.com/AzureAD/azure-activedirectory-library-for-objc) desde GitHub y luego siga las [instrucciones](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download) sobre cómo descargar ADAL mediante submódulos de Git o CocoaPods.

2. Agregue el marco ADAL (opción 1) o una biblioteca estática (opción 2) al proyecto:
    
    **Opción 1 (recomendada)**: arrastre `ADAL.framework` a la lista **Embedded Binaries** (Binarios insertados) del destino del proyecto.
    
    **Opción 2**: arrastre la biblioteca `libADALiOS.a` a la lista de **Linked Frameworks and Libraries** (Marcos y bibliotecas vinculados) del destino del proyecto. Agregue `-force_load {PATH_TO_LIB}/libADALiOS.a` al ajuste de la configuración de compilación `OTHER_LDFLAGS` del proyecto u **Other Linker Flags** (Otras marcas del enlazador) en la interfaz de usuario de Xcode. `PATH_TO_LIB` debe reemplazarse por la ubicación de archivos binarios de ADAL.



### <a name="share-the-adal-token-cache-with-other-apps-signed-with-the-same-provisioning-profile"></a>¿Cómo se puede compartir la caché de token de ADAL con otras aplicaciones firmadas con el mismo perfil de aprovisionamiento?**

Si desea compartir tokens de ADAL entre aplicaciones firmadas con el mismo perfil de aprovisionamiento, siga las instrucciones siguientes:

1. Si la aplicación no tiene definido ningún grupo de acceso a cadena de claves, agregue el identificador del lote de la aplicación como el primer grupo.

2. Habilite el inicio de sesión único (SSO) de ADAL agregando `com.microsoft.adalcache` a los grupos de acceso de la cadena de claves.

3. Si quiere especificar un grupo de cadenas de claves personalizado para reemplazar `com.microsoft.adalcache`, especifíquelo en el archivo Info.plist, en "IntuneMAMSettings", mediante la clave `ADALCacheKeychainGroupOverride`.

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>Establecer la configuración de ADAL para Intune App SDK

Si la aplicación ya usa ADAL para la autenticación y tiene su propia configuración de ADAL, puede hacer que Intune App SDK use la misma configuración durante la autenticación en Azure Active Directory. Esto garantiza que la aplicación no vuelva a solicitar la autenticación al usuario. Vea [Configurar Intune App SDK](#configure-settings-for-the-intune-app-sdk) para obtener información sobre cómo rellenar las opciones siguientes:  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Si su aplicación ya usa ADAL, son necesarias las siguientes configuraciones:

1. En el archivo Info.plist del proyecto, en el diccionario **IntuneMAMSettings** con el nombre de clave `ADALClientId`, especifique el ClientID que se usará para llamadas de ADAL.

2. Además, en el diccionario **IntuneMAMSettings** con el nombre de clave `ADALAuthority`, especifique la entidad de Azure AD.

3. En el diccionario **IntuneMAMSettings** con el nombre de clave `ADALRedirectUri`, especifique el URI de redireccionamiento que se usará para llamadas de ADAL. También puede especificar `ADALRedirectScheme` en su lugar, si el URI de redireccionamiento de la aplicación está en el formato `scheme://bundle_id`.


Además, las aplicaciones pueden invalidar esta configuración de Azure AD en runtime. Para ello, basta con establecer las propiedades `aadAuthorityUriOverride`, `aadClientIdOverride` y `aadRedirectUriOverride` en la instancia `IntuneMAMPolicyManager`.

> [!NOTE]
    > El enfoque de Info.plist se recomienda para todos los valores que sean estáticos y no tengan que determinarse en runtime. Los valores asignados a las propiedades de `IntuneMAMPolicyManager` tienen prioridad sobre los valores correspondientes especificados en Info.plist y se conservarán incluso después de reiniciar la aplicación. El SDK continuará usándolos para las protecciones de directivas hasta que se anule la inscripción del usuario o los valores se borren o cambien.

### <a name="if-your-app-does-not-use-adal"></a>Si su aplicación no usa ADAL

Si la aplicación no usa ADAL, el SDK para aplicaciones de Intune proporcionará valores predeterminados para los parámetros de ADAL y controlará la autenticación en Azure AD. No es necesario especificar los valores de configuración de ADAL mencionados anteriormente.

## <a name="receiving-app-protection-policy"></a>Recepción de la directiva de protección de aplicaciones

### <a name="overview"></a>Introducción
Para recibir la directiva de protección de aplicaciones de Intune, las aplicaciones deben iniciar una solicitud de inscripción en el servicio Intune. Las aplicaciones pueden configurarse en la consola de Intune para recibir la directiva de protección de aplicaciones con o sin inscripción de dispositivos. La directiva de protección de aplicaciones sin inscripción, también conocida como **APP-WE** o MAM-WE, permite administrar las aplicaciones mediante Intune sin necesidad de que el dispositivo esté inscrito en la administración de dispositivos móviles (MDM) de Intune. En ambos casos, se requiere la inscripción en el servicio Intune para recibir la directiva.

### <a name="apps-that-use-adal"></a>Aplicaciones que usan ADAL

Las aplicaciones que ya usan ADAL deben llamar al método `registerAndEnrollAccount` en la instancia `IntuneMAMEnrollmentManager` una vez que el usuario se haya autenticado correctamente:

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;

```

Al llamar al método `registerAndEnrollAccount`, el SDK registrará la cuenta de usuario e intentará inscribir la aplicación en nombre de esta cuenta. Si, por cualquier motivo, se produce un error en la inscripción, el SDK intentará volver a realizar la inscripción automáticamente 24 horas más tarde. Con fines de depuración, la aplicación puede recibir [notificaciones](#Status-result-and-debug-notifications) a través de un delegado sobre los resultados de las solicitudes de inscripción.

Una vez que se haya invocado esta API, la aplicación puede seguir funcionando de la manera habitual. Si la inscripción se realiza correctamente, el SDK le notificará al usuario que se debe reiniciar la aplicación. En ese momento, el usuario puede reiniciar inmediatamente la aplicación.

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal"></a>Aplicaciones que no usan ADAL

Las aplicaciones que no inician la sesión del usuario con ADAL pueden recibir directivas de protección de aplicaciones del servicio de Intune mediante una llamada a la API para que el SDK controle la autenticación. Las aplicaciones deben usar esta técnica si no han autenticado a un usuario con Azure AD pero siguen necesitando recuperar la directiva de protección de aplicaciones para ayudar a proteger los datos. Un ejemplo es si otro servicio de autenticación se utiliza para iniciar sesión en la aplicación, o si la aplicación no admite el inicio de sesión en absoluto. Para ello, la aplicación debe llamar al método `loginAndEnrollAccount` en la instancia `IntuneMAMEnrollmentManager`:

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;

```

Al llamar a este método, el SDK pedirá al usuario las credenciales si no se encuentra ningún token existente. El SDK intentará inscribir la aplicación con el servicio Intune en nombre de la cuenta de usuario proporcionado. Se puede llamar al método con "nulo" como identidad. En este caso, el SDK se inscribirá con el usuario administrado existente en el dispositivo (en el caso de MDM), o bien le pedirá al usuario un nombre de usuario si no encuentra ninguno.

Si se produce un error en la inscripción, la aplicación debe considerar la posibilidad de llamar a esta API de nuevo en el futuro, en función de los detalles del error. La aplicación puede recibir [notificaciones](#Status-result-and-debug-notifications) a través de un delegado sobre los resultados de las solicitudes de inscripción.

Una vez que se haya invocado esta API, la aplicación puede seguir funcionando de la manera habitual. Si la inscripción se realiza correctamente, el SDK le notificará al usuario que se debe reiniciar la aplicación.

Ejemplo:
```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="deregister-user-accounts"></a>Anulación del registro de cuentas de usuario

Antes de que un usuario cierre sesión en una aplicación, la aplicación debe eliminar el registro del usuario del SDK. Esto garantizará que:

1. Ya no se realizarán reintentos de inscripción para la cuenta del usuario.

2. Se quitará la directiva de protección de la aplicación.

3. Si la aplicación inicia un borrado selectivo (opcional), se eliminan todos los datos corporativos.

Antes de que el usuario cierre sesión, la aplicación debe llamar al siguiente método en la instancia de `IntuneMAMEnrollmentManager`:

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

Es necesario llamar a este método antes de eliminar los tokens de Azure AD de la cuenta de usuario. El SDK necesita que los tokens AAD de la cuenta del usuario realicen solicitudes específicas en el servicio de Intune en nombre del usuario.

Si la aplicación va a eliminar por sí misma los datos corporativos, la marca `doWipe` se puede establecer en False. De lo contrario, la aplicación puede hacer que el SDK inicie un borrado selectivo. Esto provocará una llamada al delegado de borrado selectivo de la aplicación.

Ejemplo:
```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

## <a name="status-result-and-debug-notifications"></a>Notificaciones de estado, resultados y depuración

La aplicación puede recibir notificaciones de estado, resultados y depuración sobre las solicitudes siguientes en el servicio de MAM de Intune:

 - Solicitudes de inscripción
 - Solicitudes de actualización de directivas
 - Solicitudes de anulación de inscripción

Las notificaciones se presentan a través de métodos de delegado en `Headers/IntuneMAMEnrollmentDelegate.h`:

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

Estos métodos delegados devuelven un objeto `IntuneMAMEnrollmentStatus` que contiene la información siguiente:

- La identidad de la cuenta asociada a la solicitud
- El código de estado que indica el resultado de la solicitud
- Una cadena de error con una descripción del código de estado
- Objeto `NSError`

Este objeto está definido en `IntuneMAMEnrollmentStatus.h` junto con los códigos de estado específicos que se pueden devolver.


### <a name="sample-code"></a>Código de ejemplo

A continuación se muestran implementaciones de ejemplo de los métodos delegados:

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
El valor devuelto por este método le indicará al SDK si la aplicación debe controlar el reinicio necesario:   

 - Si se devuelve True, la aplicación debe controlar el reinicio.   

 - Si devuelve false, el SDK reiniciará la aplicación después de que se devuelva este método. El SDK mostrará inmediatamente un cuadro de diálogo que indica al usuario que reinicie la aplicación.

## <a name="customize-your-apps-behavior"></a>Personalizar el comportamiento de la aplicación

Intune App SDK tiene varias API a las que se puede llamar para obtener información sobre la directiva de protección de aplicaciones de Intune implementada en la aplicación. Puede usar estos datos para personalizar el comportamiento de la aplicación. La mayoría de los valores de la directiva de protección de aplicaciones son aplicados automáticamente por el SDK y no por la aplicación. El único valor que debe implementar la aplicación es el control Guardar como.

### <a name="get-app-protection-policy"></a>Obtención de la directiva de protección de aplicaciones

#### <a name="intunemampolicymanagerh"></a>IntuneMAMPolicyManager.h
La clase IntuneMAMPolicyManager expone la directiva de protección de aplicaciones de Intune implementada en la aplicación. En particular, expone las API que son útiles para [Habilitar varias identidades](#-enable-multi-identity-optional).

#### <a name="intunemampolicyh"></a>IntuneMAMPolicy.h
La clase IntuneMAMPolicy expone la directiva de protección de aplicaciones de Intune implementada en la aplicación. La mayoría de los valores de la directiva expuestos en esta clase son aplicados por el SDK, pero siempre se puede personalizar el comportamiento de la aplicación en función de cómo se apliquen los valores de la directiva.

Esta clase expone algunas API necesarias para implementar controles Guardar como, que se detallan en la sección siguiente.

### <a name="implement-save-as-controls"></a>Implementar controles Guardar como

Intune permite a los administradores de TI seleccionen las ubicaciones de almacenamiento en las que puede guardar datos una aplicación administrada. Las aplicaciones pueden consultar a Intune App SDK sobre las ubicaciones de almacenamiento permitidas mediante la API **isSaveToAllowedForLocation**, definida en **IntuneMAMPolicy.h**.

Antes de que las aplicaciones puedan guardar datos administrados en ubicaciones locales o de almacenamiento en la nube, deben realizar una comprobación con la API **isSaveToAllowedForLocation** para saber si el administrador de TI permite que se guarden datos ahí.

Cuando las aplicaciones usen la API **isSaveToAllowedForLocation**, deben pasar el UPN para la ubicación de almacenamiento, si está disponible.

#### <a name="supported-save-locations"></a>Ubicaciones de almacenamiento admitidas

La API **isSaveToAllowedForLocation** proporciona constantes para comprobar si el administrador de TI permite que los datos se guarden en las ubicaciones siguientes definidas en IntuneMAMPolicy.h:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

Las aplicaciones deben usar las constantes de la API **isSaveToAllowedForLocation** para comprobar si los datos se pueden guardar en ubicaciones que se consideran "administradas", como OneDrive para la Empresa, o "personales". Además, la API debe usarse cuando la aplicación no puede determinar si una ubicación es "administrada" o "personal".

Las ubicaciones conocidas como "personales" se representan mediante la constante `IntuneMAMSaveLocationOther`.

La constante `IntuneMAMSaveLocationLocalDrive` debe usarse cuando la aplicación guarda datos en cualquier ubicación del dispositivo local.

## <a name="configure-settings-for-the-intune-app-sdk"></a>Establecer la configuración de Intune App SDK

Puede usar el diccionario **IntuneMAMSettings** del archivo Info.plist de la aplicación para instalar y configurar Intune App SDK. Si no se ve el diccionario IntuneMAMSettings en el archivo Info.plist, debe crear un diccionario en el archivo Info.plist de la aplicación con el nombre de campo "IntuneMAMSettings".

En el diccionario IntuneMAMSettings, puede agregar las filas de clave y valor de configuración para configurar el SDK. En la tabla siguiente se enumeran todas las configuraciones compatibles.

Es posible que se hayan tratado algunos de estos valores en las secciones anteriores y que otros no se apliquen a todas las aplicaciones.

Setting  | Tipo  | Definición | ¿Necesario?
--       |  --   |   --       |  --
ADALClientId  | String  | Identificador de cliente de Azure AD de la aplicación. | Se requiere si la aplicación usa ADAL. |
ADALAuthority | String | Entidad de Azure AD de la aplicación en uso. Debe usar su propio entorno donde se hayan configurado cuentas de AAD. | Se requiere si la aplicación usa ADAL. Si este valor está ausente, se usa un valor predeterminado de Intune.|
ADALRedirectUri  | String  | URI de redireccionamiento de Azure AD de la aplicación. | ADALRedirectUri o ADALRedirectScheme es necesario si la aplicación usa ADAL.  |
ADALRedirectScheme  | String  | Esquema de redireccionamiento de Azure AD de la aplicación. Puede usarse en lugar de ADALRedirectUri si el URI de redireccionamiento de la aplicación está en el formato `scheme://bundle_id`. | Se requiere ADALRedirectUri o ADALRedirectScheme si la aplicación usa ADAL. |
ADALLogOverrideDisabled | Boolean  | Especifica si el SDK enrutará todos los registros de ADAL (incluidas las llamadas de ADAL desde la aplicación de haberlas) a su propio archivo de registro. El valor predeterminado es NO. Establezca la opción en SÍ si la aplicación establecerá su propia devolución de llamada de registros ADAL. | Opcional. |
ADALCacheKeychainGroupOverride | String  | Especifica el grupo de cadena de claves que se usará para la caché de ADAL en lugar de "com.microsoft.adalcache". Tenga en cuenta que no contiene el prefijo de identificador de la aplicación. Ese se anexará a la cadena proporcionada en tiempo de ejecución. | Opcional. |
AppGroupIdentifiers | Matriz de cadena  | Matriz de grupos de aplicación de la sección de grupos de com.apple.security.application-groups de derechos de la aplicación. | Se requiere si la aplicación usa grupos de aplicaciones. |
ContainingAppBundleId | String | Especifica el id. del lote de la aplicación contenedora de la extensión. | Se requiere para las extensiones de iOS. |
DebugSettingsEnabled| Boolean | Si se establece en Sí, se pueden aplicar directivas de prueba en el lote de configuración. Las aplicaciones *no* se deben proporcionar con esta opción habilitada. | Opcional. |
MainNibFile<br>MainNibFile~ipad  | String  | Esta configuración debe contener el nombre de archivo nib principal de la aplicación.  | Obligatorio si la aplicación define MainNibFile en Info.plist. |
MainStoryboardFile<br>MainStoryboardFile~ipad  | String  | Esta configuración debe contener el nombre de archivo de guion gráfico principal de la aplicación. | Se requiere si la aplicación define UIMainStoryboardFile en Info.plist. |
AutoEnrollOnLaunch| Boolean| Especifica si la aplicación debe intentar inscribir automáticamente al ejecutarse, o en caso de que se haya detectado una identidad administrada existente que aún no lo haya hecho. El valor predeterminado es NO. <br><br> Nota: Si no se encuentra ninguna identidad administrada, o bien si ningún símbolo (token) válido para la identidad está disponible en la caché de AAL, el intento de inscripción devolverá un error silenciosamente sin pedir las credenciales, a menos que la aplicación tenga en valor MAMPolicyRequired establecido en SÍ. | Opcional. |
MAMPolicyRequired| Boolean| Especifica si se bloqueará el inicio de la aplicación en caso de que no tenga una directiva de protección de aplicaciones de Intune. El valor predeterminado es NO. <br><br> Nota: Las aplicaciones no se pueden enviar a la Tienda de aplicaciones con MAMPolicyRequired establecido en SÍ. Al establecer MAMPolicyRequired en SÍ, AutoEnrollOnLaunch también debe establecerse en SÍ. | Opcional. |
MAMPolicyWarnAbsent | Boolean| Especifica si la aplicación avisará al usuario durante el inicio en caso de que no tenga una directiva de protección de aplicaciones de Intune. <br><br> Nota: Los usuarios podrán seguir usando la aplicación sin directiva después de descartar la advertencia. | Opcional. |
MultiIdentity | Boolean| Especifica si la aplicación es compatible con varias identidades. | Opcional. |
SplashIconFile <br>SplashIconFile~ipad | String  | Especifica el archivo del icono de la pantalla de presentación (inicio) de Intune. | Opcional. |
SplashDuration | Número | Cantidad mínima de tiempo en segundos en que se mostrará la pantalla de presentación de Intune al iniciar la aplicación. El valor predeterminado es 1,5. | Opcional. |
BackgroundColor| String| Especifica el color de fondo para los paneles de PIN e inicio. Acepta una cadena RGB hexadecimal con el formato #XXXXXX, donde las X pueden ir de 0 a 9 o de A a F. Se puede omitir la almohadilla.   | Opcional. El valor predeterminado es gris claro. |
ForegroundColor| String| Especifica el color de primer plano para los paneles de PIN e inicio, como el color del texto. Acepta una cadena RGB hexadecimal en formato #XXXXXX, donde X puede estar comprendido entre 0 y 9 o A y F. Se puede omitir la almohadilla.  | Opcional. El valor predeterminado es negro. |
AccentColor | String| Especifica el color de énfasis de la pantalla de PIN, como el color del texto de botón y el color de resaltado del cuadro. Acepta una cadena RGB hexadecimal con el formato #XXXXXX, donde las X pueden ir de 0 a 9 o de A a F. Se puede omitir la almohadilla.| Opcional. El valor predeterminado es el azul del sistema. |
MAMTelemetryDisabled| Boolean| Especifica si el SDK no enviará los datos de telemetría a su back-end.| Opcional. |
WebViewHandledURLSchemes | Matriz de cadenas | Especifica los esquemas de dirección URL que controla WebView de la aplicación. | Se requiere si la aplicación usa WebView para controlar direcciones URL a través de vínculos o JavaScript. |  

> [!NOTE]
> Si la aplicación se va a publicar en la Tienda de aplicaciones, `MAMPolicyRequired` debe establecerse en "NO", según los estándares de la Tienda de aplicaciones.

## <a name="enabling-mam-targeted-configuration-for-your-ios-applications"></a>Habilitar la configuración de destino de MAM para las aplicaciones iOS
La configuración de destino de MAM permite que una aplicación reciba datos de configuración mediante Intune App SDK. El formato y las variantes de estos datos deben definirse y comunicarse a los clientes de Intune mediante el desarrollador o el propietario de la aplicación. Los administradores de Intune pueden dirigirse e implementar los datos de configuración mediante Azure Portal de Intune. A partir de Intune App SDK para iOS (v 7.0.1), a las aplicaciones que estén participando en la configuración de destino de MAM se les pueden proporcionar datos de la configuración de destino de MAM mediante el servicio MAM. Los datos de configuración de la aplicación se insertan a través del servicio MAM directamente en la aplicación, y no a través del canal de MDM. Intune App SDK proporciona una clase para tener acceso a los datos recuperados de estas consolas. Considere lo siguiente como requisitos previos: <br>
* La aplicación necesita inscribirse en MAM-WE antes de que tenga acceso a la interfaz de usuario de la configuración de destino de MAM. Para obtener más información sobre MAM-WE, vea [Directiva de protección de aplicaciones sin la inscripción de dispositivos en la guía de Intune App SDK](https://docs.microsoft.com/en-us/intune/app-sdk-ios#app-protection-policy-without-device-enrollment).
* Incluya ```IntuneMAMAppConfigManager.h``` en el archivo de origen de la aplicación.
* Llame a ```[[IntuneMAMAppConfig instance] appConfigForIdentity:]``` para obtener el objeto de configuración de la aplicación.
* Llame al selector adecuado en el objeto ```IntuneMAMAppConfig```. Por ejemplo, si la clave de la aplicación es una cadena, querrá usar ```stringValueForKey``` o ```allStringsForKey```. El archivo ```IntuneMAMAppConfig.h header``` trata sobre condiciones de error o valores devueltos.

Para obtener más información sobre las funciones de Graph API en relación con los valores de configuración de destino de MAM, vea la [referencia sobre Graph API para la configuración de destino de MAM](https://graph.microsoft.io/en-us/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create). <br>

Para obtener más información sobre cómo crear una directiva de configuración de aplicaciones de destino de MAM en iOS, vea la sección de la configuración de aplicaciones de destino de MAM en [How to use Microsoft Intune app configuration policies for iOS](https://docs.microsoft.com/en-us/intune/app-configuration-policies-use-ios) (Cómo usar las directivas de configuración de aplicaciones de Microsoft Intune para iOS).

## <a name="telemetry"></a>Telemetría

De manera predeterminada, el SDK de aplicaciones de Intune para iOS registra los datos de telemetría en los siguientes eventos de uso. Estos datos se envían a Microsoft Intune.

* **Inicio de la aplicación**: para ayudar a Microsoft Intune a obtener información sobre el uso de la aplicación habilitada para MAM por tipo de administración (inscripción de MAM con MDM, de MAM sin MDM, etc.).

* **Llamadas de inscripción**: para ayudar a Microsoft Intune a obtener información sobre la tasa de éxito y otras métricas de rendimiento de las llamadas de inscripción desde el cliente.

> [!NOTE]
> Si decide no enviar datos de telemetría del SDK para aplicaciones de Intune a Microsoft desde su aplicación móvil, debe deshabilitar la transmisión de telemetría de Intune App SDK. Establezca la propiedad `MAMTelemetryDisabled` en SÍ en el diccionario IntuneMAMSettings.

## <a name="enable-multi-identity-optional"></a>Habilitar varias identidades (opcional)

De forma predeterminada, el SDK aplicará una directiva a la aplicación en su conjunto. La característica de varias identidades es una característica MAM que puede habilitar para aplicar una directiva en un nivel por identidad. Esto requiere más participación en la aplicación que otras características de MAM.

La aplicación debe informar al SDK de la aplicación cuando intente cambiar la identidad activa. El SDK también notificará a la aplicación cuando se requiera un cambio de identidad. Actualmente, solo se admite una identidad administrada. Una vez que el usuario inscriba el dispositivo o la aplicación, el SDK usa esta identidad y la considera la identidad administrada principal. Los demás usuarios de la aplicación se tratarán como usuarios no administrados con una configuración de directiva sin restricciones.

Tenga en cuenta que una identidad se define simplemente como una cadena. Las identidades no distinguen mayúsculas de minúsculas. Las solicitudes al SDK podrían no devolverse con el mismo uso de mayúsculas y minúsculas que se empleó originalmente al establecer la identidad.

### <a name="identity-overview"></a>Información general sobre la identidad

Una identidad es simplemente el nombre de usuario de una cuenta (por ejemplo, user@contoso.com). Los desarrolladores pueden establecer la identidad de la aplicación en los siguientes niveles:

* **Identidad de proceso**: establece la identidad de todo el proceso y se usa principalmente para aplicaciones de una sola identidad. Esta identidad afecta a todas las tareas, los archivos y la interfaz de usuario.

* **Identidad de la interfaz de usuario**: determina qué directivas se aplican a las tareas de la interfaz de usuario en el subproceso principal, como cortar/copiar/pegar, PIN, autenticación y uso compartido de datos. La identidad de la interfaz de usuario no afecta a las tareas de archivos como el cifrado y la copia de seguridad.

* **Identidad de subproceso**: afecta a qué directivas se aplican en el subproceso actual. Esta identidad afecta a todas las tareas, los archivos y la interfaz de usuario.

La aplicación es responsable de establecer las identidades correctamente, tanto si el usuario está administrado como si no.

En todo momento, los subprocesos tienen una identidad eficaz para las tareas de la interfaz de usuario y las tareas de archivos. Esta es la identidad que se usa para comprobar qué directivas se deben aplicar, en caso de que las haya. Si la identidad es "Ninguna identidad" o si el usuario no está administrado, no se aplica ninguna directiva. Los diagramas siguientes muestran cómo se determinan las identidades reales.

  ![Intune App SDK para iOS: marcos y bibliotecas vinculados](./media/ios-thread-identities.png)

### <a name="thread-queues"></a>Colas de subprocesos

Las aplicaciones a menudo envían tareas sincrónicas y asincrónicas a colas de subprocesos. El SDK intercepta las llamadas a Grand Central Dispatch (GCD) y asocia la identidad del subproceso actual a las tareas enviadas. Cuando finalizan las tareas, el SDK cambia temporalmente la identidad del subproceso a la identidad asociada con la tarea, finaliza las tareas y restaura la identidad del subproceso original.


Dado que `NSOperationQueue` se basa en GCD, `NSOperations` se ejecutará en la identidad del subproceso en el momento en que las tareas se agreguen a `NSOperationQueue`. `NSOperations` o las funciones que se envían usando GCD directamente también pueden cambiar la identidad del subproceso actual cuando se ejecutan. Esta identidad invalidará la identidad heredada del subproceso que envía.

### <a name="file-owner"></a>Propietario del archivo

El SDK hace un seguimiento de las identidades de los propietarios del archivo local y aplica las directivas según corresponda. El propietario del archivo se establece cuando el archivo se crea o se abre en modo de truncamiento. El propietario se establece en la identidad de la tarea de archivo efectiva del subproceso que realiza la tarea.

Las aplicaciones también pueden establecer la identidad del propietario del archivo explícitamente mediante `IntuneMAMFilePolicyManager`. Las aplicaciones pueden usar `IntuneMAMFilePolicyManager` para recuperar el propietario del archivo y establecer la identidad de la interfaz de usuario antes de mostrar el contenido del archivo.

### <a name="shared-data"></a>Datos compartidos

Si la aplicación crea archivos que contienen datos de los usuarios administrados y no administrados, la aplicación es responsable de cifrar los datos del usuario administrado. Puede cifrar los datos mediante el uso de las API `protect` y `unprotect` en `IntuneMAMDataProtectionManager`.

El método `protect` acepta una identidad que puede ser un usuario administrado o no administrado. Si el usuario está administrado, se cifrarán los datos. Si el usuario no está administrado, se agregará un encabezado a los datos para cifrar la identidad, pero los datos no se cifrarán. Puede usar el método `protectionInfo` para recuperar el propietario de los datos.

### <a name="share-extensions"></a>Extensiones de recurso compartido

Si la aplicación contiene una extensión de recurso compartido, el propietario del elemento que se comparte se puede recuperar mediante el método `protectionInfoForItemProvider` en `IntuneMAMDataProtectionManager`. Si el elemento compartido es un archivo, el SDK controlará la configuración de propietario del archivo. Si el elemento compartido son datos, la aplicación es responsable de establecer el propietario del archivo si estos datos se almacenan en un archivo, y de la llamada a la API de `setUIPolicyIdentity` antes de mostrar estos datos en la interfaz de usuario.

### <a name="turning-on-multi-identity"></a>Activar varias identidades

De forma predeterminada, se considera que las aplicaciones son de una única identidad. El SDK establece la identidad del proceso en el usuario inscrito. Para habilitar la compatibilidad con varias identidades, agregue un valor booleano denominado `MultiIdentity` y un valor SÍ al diccionario IntuneMAMSettings en el archivo Info.plist de la aplicación.

> [!NOTE]
> Cuando se habilita la característica de varias identidades, la identidad del proceso, la identidad de la interfaz de usuario y las identidades de subproceso se establecerán en "nulo". La aplicación es responsable de la configuración de forma adecuada.

### <a name="switching-identities"></a>Cambio de identidades

* **Cambio de identidad iniciado por la aplicación**:

    Cuando se inicia una aplicación con varias identidades, se considera que se ejecuta en una cuenta desconocida no administrada. La interfaz de usuario de inicio condicional no se ejecutará ni se aplicará ninguna directiva en la aplicación. La aplicación es responsable de notificarle al SDK si debe cambiarse la identidad. Normalmente, esto ocurre cada vez que la aplicación va a mostrar los datos de una cuenta de usuario específica.

    Un ejemplo es cuando el usuario intenta abrir un documento, un buzón o una pestaña en un portátil. La aplicación debe notificar al SDK antes de que el archivo, el buzón o la pestaña se abra realmente. Esto se hace mediante la API `setUIPolicyIdentity` en `IntuneMAMPolicyManager`. Se debe llamar a esta API tanto si el usuario está administrado como si no. Si el usuario está administrado, el SDK llevará a cabo las comprobaciones de inicio condicional (como la detección de jailbreak, PIN y autenticación).

    El resultado del cambio de identidad se devuelve a la aplicación de forma asincrónica a través de un controlador de finalización. La aplicación debe posponer la apertura del documento, el buzón de correo o la ficha hasta que se devuelva un código de resultado correcto. Si se produce un error en el cambio de identidad, la aplicación debe cancelar la tarea.

* **Cambio de identidad iniciado por el SDK**:

    A veces, el SDK debe pedirle a la aplicación que cambie a una identidad específica. Las aplicaciones de varias identidades deben implementar el método `identitySwitchRequired` en `IntuneMAMPolicyDelegate` para controlar esta solicitud.

    Cuando se llama a este método, si la aplicación puede atender la solicitud para cambiar a la identidad especificada, debe pasar `IntuneMAMAddIdentityResultSuccess` al controlador de finalización. Si no puede atender el cambio de identidad, la aplicación debe pasar `IntuneMAMAddIdentityResultFailed` al controlador de finalización.

    La aplicación no tiene que llamar a `setUIPolicyIdentity` en respuesta a esta llamada. Si el SDK necesita que la aplicación cambie a una cuenta de usuario no administrado, se pasará la cadena vacía en la llamada a `identitySwitchRequired`.

* **Borrado selectivo**:

    Cuando la aplicación se borra de forma selectiva, el SDK llama al método `wipeDataForAccount` en `IntuneMAMPolicyDelegate`. La aplicación es responsable de quitar la cuenta del usuario especificado y todos los datos asociados. El SDK puede quitar todos los archivos que pertenecen al usuario, y lo hará si la aplicación devuelve FALSE tras la llamada a `wipeDataForAccount`.

    Tenga en cuenta que este método se llama desde un subproceso en segundo plano. La aplicación no debe devolver un valor hasta que se hayan quitado todos los datos del usuario (a excepción de los archivos si la aplicación devuelve el valor FALSE).

## <a name="ios-best-practices"></a>Prácticas recomendadas de iOS

Aquí hay algunas prácticas recomendadas para el desarrollo de iOS:

* El sistema de archivos iOS distingue mayúsculas de minúsculas. Asegúrese de que el caso sea correcto para los nombres de archivo como `libIntuneMAM.a` y `IntuneMAMResources.bundle`.

* Si Xcode tiene problemas para encontrar `libIntuneMAM.a`, puede corregir el problema agregando la ruta de acceso a esta biblioteca en las rutas de acceso de búsqueda del enlazador.

## <a name="faqs"></a>Preguntas más frecuentes


**¿Todas las API son direccionables a través de Swift nativo o la interoperabilidad de Objective-C y Swift?**

Las API de Intune App SDK solo están en Objective-C y no admiten Swift **nativo**. Se requiere la interoperabilidad de Swift con Objective-C.


**¿Es necesario registrar todos los usuarios de mi aplicación con el servicio de APP-WE?**

No. De hecho, solo se deben registrar las cuentas profesionales o educativas con el SDK de aplicaciones de Intune. Las aplicaciones son responsables de determinar si una cuenta se usa en un contexto profesional o educativo.   

**¿Qué ocurre con los usuarios que ya han iniciado sesión en la aplicación? ¿Es necesario inscribirlos?**

La aplicación es responsable de inscribir a los usuarios después de que se han autenticado correctamente. La aplicación también es responsable de la inscripción de cualquier cuenta existente que se presente antes de que la aplicación tuviera una funcionalidad MAM sin MDM.   

Para ello, la aplicación debe usar el método `registeredAccounts:`. Este método devuelve un NSDictionary que contiene todas las cuentas registradas en el servicio de MAM de Intune. Si algunas de las cuentas existentes en la aplicación no están en la lista, la aplicación debe registrar e inscribir dichas cuentas mediante `registerAndEnrollAccount:`.

**¿Con qué frecuencia debe el SDK volver a intentar las inscripciones?**

El SDK volverá a intentar automáticamente todas las inscripciones en las que se produjo un error transcurrido un intervalo de 24 horas. El SDK lo hace para asegurarse de que, en caso de que la organización de un usuario habilitara MAM después de que el usuario hubiese iniciado sesión en la aplicación, el usuario se inscriba correctamente y reciba las directivas.

El SDK dejará de intentarlo cuando detecte que el usuario ha inscrito correctamente en la aplicación. Esto se debe a que solo un usuario puede inscribir una aplicación en un momento dado. Si el usuario ha anulado la inscripción, los reintentos comenzarán de nuevo transcurrido dicho intervalo de 24 horas.

**¿Por qué es necesario anular el registro del usuario?**

El SDK realizará periódicamente estas acciones en segundo plano:

 - Si la aplicación aún no se ha inscrito, intentará inscribir todas las cuentas registradas cada 24 horas.
 - Si la aplicación está inscrita, el SDK comprobará si hay actualizaciones de la directiva de protección de aplicaciones cada 8 horas.

Al anular el registro de un usuario, se notifica al SDK que el usuario ya no va a usar la aplicación y el SDK puede detener cualquiera de los eventos periódicos de esa cuenta de usuario. También se desencadena la anulación de la inscripción de la aplicación y un borrado selectivo si es necesario.

**¿Debo establecer la marca doWipe en true en el método de anulación del registro?**

Se debe llamar a este método antes de que el usuario cierre la sesión en la aplicación.  Si los datos del usuario se eliminan de la aplicación como parte del cierre de sesión, `doWipe` se puede establecer en False. Sin embargo, si la aplicación no elimina los datos del usuario, `doWipe` se debe establecer en True para que el SDK pueda eliminar los datos.

**¿Hay otras maneras de anular la inscripción de una aplicación?**

Sí, el administrador de TI puede enviar un comando de borrado selectivo a la aplicación. Así podrá cancelar el registro y cancelar la inscripción del usuario, y borrará los datos del usuario. El SDK se encarga automáticamente de esta situación y envía una notificación a través del método delegado de anulación de inscripción.



## <a name="submit-your-app-to-the-app-store"></a>Enviar la aplicación a la Tienda de aplicaciones

Las compilaciones de marco y biblioteca estáticas de Intune App SDK son archivos binarios universales. Esto significa que tienen código para todas las arquitecturas de simulador y dispositivo. Apple rechazará las aplicaciones enviadas a la Tienda de aplicaciones si contienen código de simulador. Al compilar con la biblioteca estática para las compilaciones de solo dispositivo, el enlazador eliminará automáticamente el código de simulador. Siga los pasos siguientes para asegurarse de que se quite todo el código de simulador antes de cargar la aplicación a la Tienda de aplicaciones.

1. Asegúrese de que `IntuneMAM.framework` está en el escritorio.

2. Ejecute estos comandos:

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```
    El primer comando elimina las arquitecturas de simulador del archivo DYLIB del marco. El segundo comando copia el archivo DYLIB solo de dispositivos de nuevo en el directorio del marco.
