---
title: Introducción al SDK para aplicaciones de Microsoft Intune
description: Habilite rápidamente la aplicación móvil para la administración de aplicaciones móviles (MAM) con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 428da4581e9946b62bd6ee7c5f7d17d69f93ad9b
ms.sourcegitcommit: ae6f2e7812e7fd36f2393b8f4b6cd8de63777b2c
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73592020"
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Introducción al SDK para aplicaciones de Microsoft Intune

Esta guía le ayudará a habilitar rápidamente la aplicación móvil para que admita las directivas de protección de aplicaciones con Microsoft Intune. Quizá le resulte útil entender primero las ventajas del SDK para aplicaciones de Intune, tal como se explica en la [Información general del SDK para aplicaciones de Intune](app-sdk.md).

El SDK para aplicaciones de Intune admite escenarios similares en iOS y Android, y está pensado para crear una experiencia coherente en todas las plataformas para los administradores de TI. Pero hay pequeñas diferencias en la compatibilidad de determinadas características, debido a las limitaciones y diferencias de las plataformas.

## <a name="register-your-store-app-with-microsoft"></a>Registrar la aplicación de la tienda con Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Si la aplicación es interna de su organización y no estará disponible públicamente:

_**No es necesario**_ que registre la aplicación. En el caso de las [aplicaciones de línea de negocio internas](../apps/apps-add.md#app-types-in-microsoft-intune) que se escribieron para la empresa, el administrador de TI implementará la aplicación internamente. Intune detectará que la aplicación se ha compilado con el SDK y permitirá que el administrador de TI le aplique directivas de protección de aplicaciones. Puede ir a la sección [Habilitar su aplicación iOS o Android para la directiva de protección de aplicaciones](#enable-your-ios-or-android-app-for-app-protection-policy).

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Si la aplicación se va a publicar en una tienda de aplicaciones pública, como App Store de Apple o Google Play:

Primero _**debe**_ registrar la aplicación con Microsoft Intune y aceptar las condiciones de registro. Después, los administradores de TI pueden aplicar una directiva de protección de aplicaciones a la aplicación administrada, que se mostrará como una [aplicación asociada protegida de Intune](../apps/apps-supported-intune-apps.md#partner-apps).

Mientras no se complete el registro y no se confirme por parte del equipo de Microsoft Intune, los administradores de Intune no tendrán la opción de aplicar la directiva de protección de aplicaciones al vínculo profundo de la aplicación. Microsoft también agregará la aplicación a su [página de partners de Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). Allí, el icono de la aplicación mostrará que admite las directivas de protección de aplicaciones de Intune.

### <a name="the-registration-process"></a>El proceso de registro
Para comenzar el proceso de registro (y si aún no está trabajando con un contacto de Microsoft), rellene el cuestionario [Microsoft Intune App Partner Questionnaire](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR80SNPjnVA1KsGiZ89UxSdVUMEpZNUFEUzdENENOVEdRMjM5UEpWWjJFVi4u) (Cuestionario de asociado de la aplicación de Microsoft Intune).

Usaremos las direcciones de correo que se muestran en la respuesta del cuestionario para dirigirse al proceso de registro y continuarlo. Además, usamos la dirección de correo electrónico del registro para ponernos en contacto con usted si surge cualquier problema.

> [!NOTE]
> Toda la información recopilada en el cuestionario y a través de la correspondencia por correo electrónico con el equipo de Microsoft Intune cumplirá la [declaración de privacidad de Microsoft](https://www.microsoft.com/privacystatement/default.aspx).

**Qué esperar durante el proceso de registro**:

1. Una vez que ha enviado el cuestionario, nos pondremos en contacto con usted a través de la dirección de correo electrónico de registro, bien para confirmar la recepción correcta, bien para pedir información adicional para completar el registro.

2. Después de que recibamos la información necesaria, le enviaremos el Acuerdo de partner de la aplicación de Microsoft Intune para que lo firme. En este contrato se describen los términos que su empresa debe aceptar para convertirse en partner de las aplicaciones de Microsoft Intune.

3. También le notificaremos si la aplicación se registra correctamente con el servicio de Microsoft Intune y si la aplicación aparece en el sitio de [partners de Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

4. Por último, el vínculo profundo se agregará a la actualización del próximo mes del servicio de Intune. Por ejemplo, si la información de registro se ha completado en julio, el vínculo profundo se admitirá hacia mediados de agosto.

Si el vínculo profundo de la aplicación cambia en el futuro, tendrá que volver a registrar la aplicación.

> [!NOTE]
> Debe informarnos si actualiza la aplicación con una nueva versión del SDK para aplicaciones de Intune.

## <a name="download-the-sdk-files"></a>Descargar los archivos del SDK

Los SDK de aplicaciones de Intune para iOS y Android nativos están hospedados en una cuenta de GitHub de Microsoft. Estos repositorios públicos contienen los archivos del SDK para iOS y Android nativos, respectivamente:

* [SDK de aplicaciones de Intune para iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [SDK de aplicaciones de Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Si la aplicación es una aplicación Xamarin, use esta variante del SDK:

* [Xamarin Bindings del SDK para aplicaciones de Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)

Se recomienda que se suscriba a una cuenta de GitHub que pueda usar para bifurcar nuestros repositorios y extraer de ellos. GitHub permite que los desarrolladores se comuniquen con nuestro equipo de productos, notifiquen problemas y reciban respuestas rápidas, vean las notas de la versión y envíen comentarios a Microsoft. Para realizar preguntas sobre el SDK de aplicaciones de Intune en GitHub, póngase en contacto con msintuneappsdk@microsoft.com.

## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>Habilitar su aplicación iOS o Android para la directiva de protección de aplicaciones

Necesitará una de las siguientes guías para desarrolladores que le ayudará a integrar el SDK de aplicaciones de Intune en la aplicación:

* **[Guía para desarrolladores sobre el SDK para aplicaciones de Intune para iOS](app-sdk-ios.md)** : este documento le guiará paso a paso para habilitar la aplicación iOS nativa con el SDK para aplicaciones de Intune.

* **[Guía para desarrolladores sobre el SDK para aplicaciones de Intune para Android](app-sdk-android.md)** : este documento le guiará paso a paso para habilitar la aplicación Android nativa con el SDK para aplicaciones de Intune.

* **[Guía de Xamarin Bindings del SDK para aplicaciones de Intune](app-sdk-xamarin.md)** : este documento le ayudará a crear aplicaciones iOS y Android con Xamarin para las directivas de protección de aplicaciones de Intune.



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>Habilitar su aplicación iOS o Android para un acceso condicional basado en aplicación

Además de habilitar la aplicación para la directiva de protección de aplicaciones, se requiere lo siguiente para que la aplicación funcione correctamente con el acceso condicional basado en la aplicación Azure Active Directory (AAD):

* La aplicación se compiló con la [Biblioteca de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) y está habilitada para la autenticación de agente AAD.

* El [identificador de cliente de AAD](https://docs.microsoft.com/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#configure-a-native-client-application) de la aplicación debe ser único en las plataformas iOS y Android.

## <a name="configure-telemetry-for-your-app"></a>Configuración de la telemetría para la aplicación

Microsoft Intune recopila datos sobre las estadísticas de uso de la aplicación.

* **SDK para aplicaciones de Intune para iOS**: de forma predeterminada, el SDK registra los datos de telemetría del SDK en eventos de uso. Estos datos se envían a Microsoft Intune.

  * Si decide no enviar datos de telemetría del SDK a Microsoft Intune desde su aplicación, debe deshabilitar la transmisión de telemetría estableciendo la propiedad `MAMTelemetryDisabled` en "Sí" en el diccionario IntuneMAMSettings.

* **SDK de aplicaciones de Intune para Android**: el SDK para aplicaciones de Intune para Android no controla la recopilación de datos de su aplicación. La aplicación de Portal de empresa registra los datos de telemetría de manera predeterminada. Estos datos se envían a Microsoft Intune. Según las directivas de Microsoft, no se recopila información de identificación personal (PII por sus siglas en inglés). 

  * Si los usuarios finales deciden no enviar estos datos, deberán desactivar la telemetría en la sección Configuración de la aplicación Portal de empresa. Para obtener más información, consulte [Desactivar la recopilación de datos de uso de Microsoft](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="line-of-business-app-version-numbers"></a>Números de versión de las aplicaciones de línea de negocio

Las aplicaciones de línea de negocio de Intune ahora muestran el número de versión para iOS y Android. El número se muestra en la lista de aplicaciones de Azure Portal y en la hoja de información general de la aplicación. Los usuarios finales pueden ver este número en la aplicación Portal de empresa y en el portal web.

### <a name="full-version-number"></a>Número de versión completo

El número de versión completo identifica una versión específica de la aplicación. El número aparece como _versión_(_compilación_). Por ejemplo, 2.2(2.2.17560800). 

El número de versión completo consta de dos componentes:

- **Versión**  
  El número de versión es el número que pueden ver los usuarios. Sirve para que los usuarios finales distingan las diferentes versiones de la aplicación.

- **Número de compilación**  
  El número de compilación es un número interno que puede usarse para la detección de la aplicación y para administrar la aplicación mediante programación. El número de compilación alude a una iteración de la aplicación que hace referencia a los cambios en el código.

### <a name="version-and-build-number-in-android-and-ios"></a>Números de versión y compilación en Android y iOS

Android y iOS usan números de versión y de compilación para hacer referencia a las aplicaciones. Sin embargo, ambos sistemas operativos tienen significados específicos de cada uno. En la tabla siguiente se explica cómo se relacionan estos términos.

Cuando desarrolle una aplicación de línea de negocio para su uso en Intune, recuerde que debe usar tanto el número de versión como el de compilación. Las características de administración de aplicaciones de Intune se basan en unos valores significativos de **CFBundleVersion** (para iOS) y **PackageVersionCode** (para Android). Estos números se incluyen en el manifiesto de aplicación. 

Intune|iOS|Android|Descripción|
|---|---|---|---|
Número de versión|CFBundleShortVersionString|PackageVersionName |Este número indica una versión específica de la aplicación para los usuarios finales.|
Número de compilación|CFBundleVersion|PackageVersionCode |Este número se usa para indicar una iteración en el código de la aplicación.|

#### <a name="ios"></a>iOS

- **CFBundleShortVersionString**  
  Especifica el número de versión de lanzamiento del conjunto. Este número identifica una versión publicada de la aplicación y lo utilizan los usuarios finales para hacer referencia a ella.
- **CFBundleVersion**  
  Se trata de la versión de compilación del conjunto que identifica una iteración de dicho conjunto. El número permite identificar una versión o un conjunto sin publicar y se usa para fines de detección de la aplicación.

#### <a name="android"></a>Android

- **PackageVersionName**  
  Es el número de versión que se muestra a los usuarios. Este atributo puede establecerse como una cadena sin formato o como una referencia a un recurso de la cadena. La cadena no tiene ningún otro propósito que mostrarse a los usuarios.
- **PackageVersionCode**  
  Se trata de un número de versión interno. Este número se usa únicamente para determinar si una versión es más reciente que otra. Los números más altos indican versiones más recientes. No es la versión. 

## <a name="next-steps-after-integration"></a>Pasos siguientes después de la integración

### <a name="test-your-app"></a>Probar la aplicación
Cuando haya completado los pasos necesarios para integrar la aplicación iOS o Android con el SDK de aplicaciones de Intune, debe asegurarse de que todas las directivas de protección de aplicaciones están habilitadas y que funcionan para el usuario y el administrador de TI. Para probar la aplicación integrada, necesitará lo siguiente:

* **Cuenta de prueba de Microsoft Intune**: para probar la aplicación administrada por Intune con las características de protección de aplicaciones de Intune, necesitará una cuenta de Microsoft Intune.

  * Si es un ISV que quiere habilitar las aplicaciones de la tienda Android o iOS para la directiva de protección de aplicaciones de Intune, recibirá un código de promoción una vez completado el registro con Microsoft Intune, como se describe en el paso de registro. El código de promoción le permite registrarse para obtener una versión de prueba de un año de uso extendido de Microsoft Intune.

  * Si está desarrollando una línea de aplicaciones empresariales que no se enviarán a la tienda, se espera que tenga acceso a Microsoft Intune a través de la empresa. También puede registrarse en [Microsoft Intune](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) para obtener la versión de prueba gratuita de un mes.

  * Si quiere probar la aplicación en un dispositivo móvil con una cuenta de usuario final, asegúrese de haber iniciado sesión con una cuenta de administrador y concedido a dicha cuenta una licencia de Intune en el sitio web del Centro de administración de Microsoft 365. Para más información, vea [Asignar licencias a los usuarios para que puedan inscribir dispositivos en Intune](../fundamentals/licenses-assign.md).

* **Directivas de protección de aplicaciones de Intune**: para probar la aplicación con todas las directivas de protección de aplicaciones de Intune, debe saber que el comportamiento esperado es para cada configuración de directiva. Vea las descripciones para las [directivas de protección de aplicaciones iOS](../apps/app-protection-policy-settings-ios.md) y las [directivas de protección de aplicaciones Android](../apps/app-protection-policy-settings-android.md). Si su aplicación ha integrado el SDK de Intune, pero aún no figura en Azure Portal como una aplicación específica, puede orientarla con una directiva seleccionando la opción "+ Más aplicaciones" y proporcionando el id. del paquete (iOS) o el nombre del paquete. (Android) en el cuadro de texto.

* **Solución de problemas**: si encuentra algún problema al probar manualmente la experiencia de usuario de instalación de la aplicación, vea la [solución de problemas de instalación de aplicaciones](../apps/troubleshoot-app-install.md). 

### <a name="give-your-app-access-to-the-intune-app-protection-service-optional"></a>Proporcione a la aplicación acceso al servicio Intune App Protection (opcional)

Si la aplicación usa su propia configuración personalizada de Azure Active Directory (AAD) para la autenticación, se deben realizar los siguientes pasos tanto para aplicaciones de la tienda pública como para aplicaciones de línea de negocio. **No es necesario realizar los pasos si la aplicación usa el identificador de cliente predeterminado del SDK de Intune**. 

Una vez que haya registrado la aplicación dentro de un inquilino de Azure y se muestre en **Todas las aplicaciones**, debe asignar a la aplicación acceso al servicio Intune App Protection (anteriormente conocido como servicio MAM). En Azure Portal:

1. Vaya a la hoja **Azure Active Directory**.
2. En **Registros de aplicaciones**, vaya a la lista configurada para la aplicación.
3. Haga clic en **+ Agregar un permiso**.
4. Haga clic en **API usadas en mi organización**. 
5. En el cuadro de búsqueda, escriba **Microsoft Mobile Application Management**.
6. En **Permisos delegados**, active la casilla **DeviceManagementManagedApps.ReadWrite: Read and Write the User's App Management Data** (DeviceManagementManagedApps.ReadWrite: Leer y escribir los datos de administración de aplicaciones del usuario)*.
7. Haga clic en **Agregar permisos**.

> [!NOTE]
> Si su aplicación le impide iniciar sesión debido a un error al acceder a este recurso: https://intunemam.microsoftonline.com, debe enviar una nota a msintuneappsdk@microsoft.com con el identificador de cliente de la aplicación. Este es un proceso de aprobación manual hoy en día.

### <a name="badge-your-app-optional"></a>Identificar la aplicación (opcional)

Después de validar que las directivas de protección de aplicaciones de Intune funcionan en su aplicación, puede identificar el icono de la aplicación con el logotipo de protección de aplicaciones de Intune.

Este distintivo indica a los administradores de TI, a los usuarios finales y a los clientes potenciales de Intune que su aplicación funciona con las directivas de protección de aplicaciones de Intune. Fomenta el uso y la adopción de su aplicación para los clientes de Intune.

Este distintivo es un icono de maletín y puede verse en los ejemplos siguientes:

![Directivas de protección de aplicaciones de Intune: ejemplo de distintivo 1](./media/app-sdk-get-started/badge-example-1.png) ![Directivas de protección de aplicaciones de Intune: ejemplo de distintivo 2](./media/app-sdk-get-started/badge-example-2.png)

**Lo que necesitará para identificar su aplicación**:

* Una aplicación de manipulación de imágenes que pueda leer archivos **.eps** o una aplicación de Adobe que pueda leer archivos **.ai**.

* Puede encontrar las [instrucciones y activos de distintivo de aplicaciones de Intune](https://github.com/msintuneappsdk/intune-app-partner-badge) en Microsoft Intune GitHub.
