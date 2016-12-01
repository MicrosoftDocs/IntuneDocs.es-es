---
title: "Introducción al SDK para aplicaciones de Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.author: oydang
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ca4623db80d711f3543b6d688fb1bb1ef228c62c
ms.openlocfilehash: 2a65ae79a0bba21d555dbed9f1bc40e01452f08c


---

# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Introducción al SDK para aplicaciones de Microsoft Intune

Esta guía le ayudará a habilitar rápidamente la aplicación móvil para la administración de aplicaciones móviles (MAM) con Microsoft Intune. Quizá le resulte útil entender primero las ventajas del SDK para aplicaciones de Intune, tal como se explica en la [Información general del SDK para aplicaciones de Intune](intune-app-sdk.md).

En esta guía se describen los pasos principales para habilitar MAM en su aplicación con Microsoft Intune. El SDK para aplicaciones de Intune admite escenarios similares en distintas plataformas y está pensado para crear una experiencia coherente en todas las plataformas para los administradores de TI. Sin embargo, hay pequeñas diferencias en la compatibilidad de determinadas características debido a las limitaciones de la plataforma.

## <a name="register-your-store-app-with-microsoft"></a>Registrar la aplicación de la tienda con Microsoft

**Si la aplicación es interna de la empresa y no estará disponible en una tienda de aplicaciones pública**:

*No es necesario* que registre la aplicación. En el caso de las aplicaciones de línea de negocio internas, el administrador de TI implementará la aplicación internamente. Intune detectará que la aplicación se ha compilado con el SDK y permitirá que el administrador de TI le aplique la configuración de las directivas de MAM. Puede ir a la sección titulada [Habilitar su aplicación móvil iOS o Android para MAM con el SDK](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk).

**Si la aplicación se va a publicar en una tienda de aplicaciones pública, como App Store de Apple o Google Play**:

Primero *debe* registrar la aplicación con Microsoft Intune y aceptar las condiciones de registro. Los administradores de TI pueden entonces aplicar la configuración de las directivas de MAM de Intune a la aplicación habilitada, que se mostrará como un partner de las aplicaciones de Intune. Mientras no se complete el registro y no se confirme por parte del equipo de Microsoft Intune, los administradores de Intune no tendrán la opción de aplicar la directiva de MAM al vínculo profundo de la aplicación. Microsoft también agregará la aplicación a su [página de partners de Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps). Allí, el icono de la aplicación mostrará que admite la directiva MAM de Microsoft Intune.

Para comenzar el proceso de registro, rellene el [Cuestionario de partner de la aplicación de Microsoft Intune](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u).

Usaremos las direcciones de correo electrónico que se muestran en las respuestas del cuestionario para dirigirse al proceso de registro y continuarlo. Además, usamos la dirección de correo electrónico del registro para ponernos en contacto con usted si surge cualquier problema.

> [!NOTE]
> Toda la información recopilada en el cuestionario y a través de la correspondencia por correo electrónico con el equipo de Microsoft Intune cumplirá la [declaración de privacidad de Microsoft](https://www.microsoft.com/en-us/privacystatement/default.aspx).

**Qué esperar durante el proceso de registro**:

1. Una vez que ha enviado el cuestionario, nos pondremos en contacto con usted a través de la dirección de correo electrónico de registro, bien para confirmar la recepción correcta, bien para pedir información adicional para completar el registro.
2. Después de que recibamos la información necesaria, le enviaremos el Acuerdo de partner de la aplicación de Microsoft Intune para que lo firme. En este contrato se describen los términos que su empresa debe aceptar para convertirse en partner de las aplicaciones de Microsoft Intune.
3. También le notificaremos si la aplicación se registra correctamente con el servicio de Microsoft Intune y si la aplicación aparece en el sitio de [partners de Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps).
4. Por último, el vínculo profundo se agregará a la actualización del próximo mes del servicio de Intune. Por ejemplo, si la información de registro se ha completado en julio, el vínculo profundo se admitirá hacia mediados de agosto.

Si el vínculo profundo de la aplicación cambia en el futuro, tendrá que volver a registrar la aplicación. Además, avísenos si actualiza la aplicación con una nueva versión del SDK de la aplicación de Intune.



## <a name="download-the-sdk-files"></a>Descargar los archivos del SDK

Los SDK de aplicaciones de Intune para iOS y Android nativos están hospedados en una cuenta de GitHub de Microsoft. Estos repositorios públicos contienen los archivos del SDK para iOS y Android, respectivamente:

* [SDK de aplicaciones de Intune para iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [SDK de aplicaciones de Intune para Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Si su aplicación es una aplicación Xamarin o Cordova, use las siguientes herramientas de desarrollador:

* [Componente Xamarin del SDK para aplicaciones de Intune](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Complemento Cordova del SDK para aplicaciones de Intune](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Se recomienda que se suscriba a una cuenta de GitHub que pueda usar para bifurcar nuestros repositorios y extraer de ellos. GitHub permite que los desarrolladores se comuniquen con nuestro equipo de productos, notifiquen problemas y reciban respuestas rápidas, vean las notas de la versión y envíen comentarios a Microsoft. Para formular preguntas sobre la cuenta y los repositorios de GitHub, póngase en contacto con msintuneappsdk@microsoft.com.





## <a name="enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk"></a>Habilitar su aplicación móvil iOS o Android para MAM con el SDK

Para integrar el SDK de aplicaciones de Intune en la aplicación de iOS nativo, necesitará lo siguiente:

* **[Guía para desarrolladores sobre el SDK para aplicaciones de Intune para iOS](intune-app-sdk-ios.md)**: este documento lo guiará paso a paso para habilitar la aplicación móvil iOS con el SDK para aplicaciones de Intune.


Para integrar el SDK de aplicaciones de Intune en la aplicación de Android nativo, necesitará lo siguiente:

* **[Guía para desarrolladores sobre el SDK para aplicaciones de Intune para Android](intune-app-sdk-android.md)**: este documento lo guiará paso a paso para habilitar la aplicación móvil Android con el SDK para aplicaciones de Intune.

Para compilar aplicaciones de Cordova con el complemento Cordova del SDK para aplicaciones de Intune, necesitará lo siguiente:

* **[Guía de complemento Cordova de SDK para aplicaciones de Intune](intune-app-sdk-cordova)**: este documento le ayudará a crear aplicaciones iOS y Android con Cordova para la administración de aplicaciones móviles de Intune.

Para compilar aplicaciones de Xamarin con el complemento Xamarin del SDK para aplicaciones de Intune, necesitará lo siguiente:

* **[Guía de complemento Xamarin de SDK para aplicaciones de Intune](intune-app-sdk-xamarin)**: este documento le ayudará a crear aplicaciones iOS y Android con Cordova para la administración de aplicaciones móviles de Intune.




## <a name="configure-telemetry-for-your-app"></a>Configuración de la telemetría para la aplicación

Microsoft Intune recopila datos sobre las estadísticas de uso de la aplicación.

* **SDK para aplicaciones de Intune para iOS**: de forma predeterminada, el SDK registra los datos de telemetría del SDK en eventos de uso. Estos datos se envían a Microsoft Intune.

    * Si decide no enviar datos de telemetría del SDK a Microsoft Intune desde su aplicación, debe deshabilitar la transmisión de telemetría estableciendo la propiedad `MAMTelemetryDisabled` en "Sí" en el diccionario IntuneMAMSettings.

* **SDK de aplicaciones de Intune para Android**: los datos de telemetría no se registran a través del SDK.

## <a name="test-your-mam-enabled-app-with-microsoft-intune"></a>Probar la aplicación habilitada para MAM con Microsoft Intune

Cuando haya completado los pasos necesarios para integrar la aplicación iOS o Android con el SDK de aplicaciones de Intune, debe asegurarse de que todas las directivas de administración de aplicaciones están habilitadas y que funcionan para el usuario y el administrador de TI. Para probar la aplicación integrada, necesitará lo siguiente:

<!--TODO-->

* **Probar la aplicación habilitada para MAM con Microsoft Intune**: este documento lo guiará paso a paso a lo largo del proceso para probar las aplicaciones Android o iOS habilitadas para MAM con Microsoft Intune. Encontrará este documento en los repositorios de GitHub de los SDK.

* **Cuenta de Microsoft Intune**: para probar sus aplicaciones habilitadas para MAM con Microsoft Intune, necesita una cuenta de Microsoft Intune.
    * Si es un ISV que quiere habilitar las aplicaciones de la tienda Android o iOS para MAM de Intune, recibirá un código de promoción una vez completado el registro con Microsoft Intune, como se describe en el paso de registro. El código de promoción le permite registrarse para obtener una versión de prueba de un año de uso extendido de Microsoft Intune.
    * Si está desarrollando una línea de aplicaciones empresariales que no se enviarán a la tienda, se espera que tenga acceso a Microsoft Intune a través de la empresa. También puede registrarse en [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) para obtener la versión de prueba gratuita de un mes.



<!--HONumber=Nov16_HO3-->


