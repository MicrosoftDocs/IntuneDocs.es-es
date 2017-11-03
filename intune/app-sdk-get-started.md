---
title: "Introducción al SDK para aplicaciones de Microsoft Intune"
description: "Habilite rápidamente la aplicación móvil para la administración de aplicaciones móviles (MAM) con Microsoft Intune."
keywords: 
author: mattbriggs
manager: angrobe
ms.author: mabriggs
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 65350c9a247c5820cb2080d8230d308a37e98d7c
ms.sourcegitcommit: 42a0e4c83e33c1a25506ca75d673e861e9206945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/26/2017
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Introducción al SDK para aplicaciones de Microsoft Intune

Esta guía le ayudará a habilitar rápidamente la aplicación móvil para las directivas de protección de aplicaciones con Microsoft Intune. Quizá le resulte útil entender primero las ventajas del SDK para aplicaciones de Intune, tal como se explica en la [Información general del SDK para aplicaciones de Intune](app-sdk.md).

El SDK para aplicaciones de Intune admite escenarios similares en iOS y Android, y está pensado para crear una experiencia coherente en todas las plataformas para los administradores de TI. Sin embargo, hay pequeñas diferencias en la compatibilidad de determinadas características debido a las limitaciones de la plataforma.

## <a name="register-your-store-app-with-microsoft"></a>Registrar la aplicación de la tienda con Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Si la aplicación es interna de su organización y no estará disponible públicamente:

*No es necesario* que registre la aplicación. En el caso de las aplicaciones de línea de negocio internas, el administrador de TI implementará la aplicación internamente. Intune detectará que la aplicación se ha compilado con el SDK y permitirá que el administrador de TI le aplique la directiva de protección de aplicaciones. Puede ir a la sección [Habilitar su aplicación iOS o Android para la directiva de protección de aplicaciones](#enable-your-iOS-or-Android-app-for-app-protection-policy).

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Si la aplicación se va a publicar en una tienda de aplicaciones pública, como App Store de Apple o Google Play:

Primero _**debe**_ registrar la aplicación con Microsoft Intune y aceptar las condiciones de registro. Los administradores de TI pueden entonces aplicar la directiva de protección de aplicaciones a la aplicación habilitada, que se mostrará como un partner de las aplicaciones de Intune.

Mientras no se complete el registro y no se confirme por parte del equipo de Microsoft Intune, los administradores de Intune no tendrán la opción de aplicar la directiva de protección de aplicaciones al vínculo profundo de la aplicación. Microsoft también agregará la aplicación a su [página de partners de Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps). Allí, el icono de la aplicación mostrará que admite las directivas de protección de aplicaciones de Intune.

Para comenzar el proceso de registro, rellene el [Cuestionario de partner de la aplicación de Microsoft Intune](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u).

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
> Avísenos si actualiza la aplicación con una nueva versión del SDK de la aplicación de Intune.



## <a name="download-the-sdk-files"></a>Descargar los archivos del SDK

Los SDK de aplicaciones de Intune para iOS y Android nativos están hospedados en una cuenta de GitHub de Microsoft. Estos repositorios públicos contienen los archivos del SDK para iOS y Android nativos, respectivamente:

* [SDK de aplicaciones de Intune para iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [SDK de aplicaciones de Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Si su aplicación es una aplicación Xamarin o Cordova, use estas variantes del SDK:

* [Componente Xamarin del SDK para aplicaciones de Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Complemento Cordova del SDK para aplicaciones de Intune](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Se recomienda que se suscriba a una cuenta de GitHub que pueda usar para bifurcar nuestros repositorios y extraer de ellos. GitHub permite que los desarrolladores se comuniquen con nuestro equipo de productos, notifiquen problemas y reciban respuestas rápidas, vean las notas de la versión y envíen comentarios a Microsoft. Para realizar preguntas sobre el SDK de aplicaciones de Intune en GitHub, póngase en contacto con msintuneappsdk@microsoft.com.





## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>Habilitar su aplicación iOS o Android para la directiva de protección de aplicaciones

Necesitará una de las siguientes guías para desarrolladores que le ayudará a integrar el SDK de aplicaciones de Intune en la aplicación:

* **[Guía para desarrolladores sobre el SDK para aplicaciones de Intune para iOS](app-sdk-ios.md)**: este documento le guiará paso a paso para habilitar la aplicación iOS nativa con el SDK para aplicaciones de Intune.

* **[Guía para desarrolladores sobre el SDK para aplicaciones de Intune para Android](app-sdk-android.md)**: este documento le guiará paso a paso para habilitar la aplicación Android nativa con el SDK para aplicaciones de Intune.

* **[Guía de complemento Cordova de SDK para aplicaciones de Intune](app-sdk-cordova.md)**: este documento le ayudará a crear aplicaciones iOS y Android con Cordova para las directivas de protección de aplicaciones de Intune.

* **[Guía de complemento Xamarin de SDK para aplicaciones de Intune](app-sdk-xamarin.md)**: este documento le ayudará a crear aplicaciones iOS y Android con Cordova para las directivas de protección de aplicaciones de Intune.



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>Habilitar su aplicación iOS o Android para un acceso condicional basado en aplicación
 
 Además de habilitar la aplicación para la directiva de protección de aplicaciones, se requiere lo siguiente para que la aplicación funcione correctamente con el acceso condicional basado en la aplicación Azure Active Directory (AAD):
 
 * La aplicación se compiló con la [Biblioteca de autenticación de Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-authentication-libraries) y está habilitada para la autenticación de agente AAD.
 
 * El [identificador de cliente de AAD](https://docs.microsoft.com/en-us/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application) de la aplicación debe ser único en las plataformas iOS y Android.
 
 
 

## <a name="configure-telemetry-for-your-app"></a>Configuración de la telemetría para la aplicación

Microsoft Intune recopila datos sobre las estadísticas de uso de la aplicación.

* **SDK para aplicaciones de Intune para iOS**: de forma predeterminada, el SDK registra los datos de telemetría del SDK en eventos de uso. Estos datos se envían a Microsoft Intune.

    * Si decide no enviar datos de telemetría del SDK a Microsoft Intune desde su aplicación, debe deshabilitar la transmisión de telemetría estableciendo la propiedad `MAMTelemetryDisabled` en "Sí" en el diccionario IntuneMAMSettings.


* **SDK de aplicaciones de Intune para Android**: los datos de telemetría no se registran a través del SDK.

## <a name="next-steps-after-integration"></a>Pasos siguientes después de la integración

### <a name="test-your-app"></a>Probar la aplicación
Cuando haya completado los pasos necesarios para integrar la aplicación iOS o Android con el SDK de aplicaciones de Intune, debe asegurarse de que todas las directivas de protección de aplicaciones están habilitadas y que funcionan para el usuario y el administrador de TI. Para probar la aplicación integrada, necesitará lo siguiente:

* **Cuenta de prueba de Microsoft Intune**: para probar la aplicación habilitada para Intune con las características de protección de aplicaciones de Intune, necesitará una cuenta de Microsoft Intune.

    * Si es un ISV que quiere habilitar las aplicaciones de la tienda Android o iOS para la directiva de protección de aplicaciones de Intune, recibirá un código de promoción una vez completado el registro con Microsoft Intune, como se describe en el paso de registro. El código de promoción le permite registrarse para obtener una versión de prueba de un año de uso extendido de Microsoft Intune.

    * Si está desarrollando una línea de aplicaciones empresariales que no se enviarán a la tienda, se espera que tenga acceso a Microsoft Intune a través de la empresa. También puede registrarse en [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) para obtener la versión de prueba gratuita de un mes.

* **Directivas de protección de aplicaciones de Intune**: para probar la aplicación con todas las directivas de protección de aplicaciones de Intune, debe saber que el comportamiento esperado es para cada configuración de directiva. Vea las descripciones para las [directivas de protección de aplicaciones iOS](/intune-classic/deploy-use/ios-mam-policy-settings) y las [directivas de protección de aplicaciones Android](/intune-classic/deploy-use/android-mam-policy-settings).

* **Solución de problemas**: si encuentra algún problema al probar manualmente la experiencia de usuario de la aplicación, vea la [Solución de problemas de MAM](/intune-classic/troubleshoot/troubleshoot-mam). En este artículo se ofrece ayuda para los problemas comunes, cuadros de diálogo y mensajes de error que pueden experimentarse en las aplicaciones habilitadas para Intune. 

### <a name="badge-your-app-optional"></a>Identificar la aplicación (opcional)

Después de validar que las directivas de protección de aplicaciones de Intune funcionan en su aplicación, puede identificar el icono de la aplicación con el logotipo de protección de aplicaciones de Intune.

Este distintivo indica a los administradores de TI, a los usuarios finales y a los clientes potenciales de Intune que su aplicación funciona con las directivas de protección de aplicaciones de Intune. Fomenta el uso y la adopción de su aplicación para los clientes de Intune.

Este distintivo es un icono de maletín y puede verse en los ejemplos siguientes:

![Ejemplo de distintivo 1](./media/badge-example-1.png) ![Ejemplo de distintivo 2](./media/badge-example-2.png)

**Lo que necesitará para identificar su aplicación**:

* Una aplicación de manipulación de imágenes que pueda leer archivos **.eps** o una aplicación de Adobe que pueda leer archivos **.ai**.

* Puede encontrar las [instrucciones y activos de distintivo de aplicaciones de Intune](https://github.com/msintuneappsdk/intune-app-partner-badge) en Microsoft Intune GitHub.
