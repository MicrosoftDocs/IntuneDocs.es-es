---
title: "Introducción al SDK para aplicaciones de Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7f62c5ee18d8f69fa174f09a1c46b6925c7517c
ms.openlocfilehash: a042f0c6206e9aaf4ec0eb012a70930aa95ecc47


---

# Introducción al SDK para aplicaciones de Microsoft Intune

Esta guía de introducción le ayudará a habilitar rápidamente la aplicación móvil para la administración de aplicaciones móviles con Microsoft Intune. Quizá le resulte útil entender primero las ventajas del SDK para aplicaciones de Intune que figuran en la en la [Información general del SDK para aplicaciones de Intune](intune-app-sdk.md).

En esta guía se describen los pasos principales necesarios para habilitar la administración de aplicaciones móviles en su aplicación con Microsoft Intune. El SDK para aplicaciones de Intune admite escenarios similares en distintas plataformas y está pensado para crear una experiencia coherente en todas las plataformas para los administradores de TI. Sin embargo, hay pequeñas diferencias en la compatibilidad de determinadas características debido a las limitaciones de la plataforma.

# Introducción

## Registrarse en Microsoft Connect

Actualmente, se puede obtener acceso al SDK para aplicaciones de Intune a través de Microsoft Connect y se necesita inicio de sesión. Para ello, registre una [cuenta de Microsoft](https://connect.microsoft.com/ConfigurationManagervnext/InvitationUse.aspx?ProgramID=8967&InvitationID=8967-YJYJ-8G6X) con el correo de la empresa.

El registro estará en estado pendiente hasta que el equipo de Intune revise la solicitud. El tiempo de respuesta habitual es de entre 2 y 3 días laborables. Cuando se haya aprobado, recibirá una notificación de correo electrónico con los vínculos para descargar el SDK para aplicaciones de Intune para las plataformas y todas las guías relacionadas. También puede tener acceso a estas guías en el sitio de MSDN.

## Registrar la aplicación de la tienda con Microsoft Intune

**Si la aplicación habilitada es interna de su empresa y no estará disponible en la tienda de aplicaciones de Apple o Google**: no es necesario registrar la aplicación. Para esas aplicaciones internas, el administrador de TI las cargará directamente en la consola de Microsoft Intune para la implementación, Intune detectará que la aplicación se ha compilado con el SDK y presentará al administrador de TI la opción de aplicarle la directiva MAM. Puede ir a la sección titulada [Habilitar su aplicación móvil iOS o Android para MAM con el SDK](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk).

**Si es un ISV que desarrolla una aplicación que estará disponible para los clientes a través de las tiendas de aplicaciones de Apple o Google**: en primer lugar, debe registrar la aplicación con Microsoft Intune y aceptar los términos del registro. Puede ofrecer el vínculo profundo de la aplicación en este momento. Después, un administrador de TI puede aplicar directivas MAM de Intune a la aplicación. Hasta que no se complete el registro y no se confirme por el equipo de Microsoft Intune, el vínculo profundo de la aplicación no tendrá la opción de aplicar la directiva MAM en la consola de administración. Microsoft también mantiene un sitio web de socios de Microsoft Intune en el que se registrará la aplicación para que los clientes sepan que cumple la directiva MAM de Microsoft Intune.

Para comenzar el proceso de registro, **revise y firme** el [acuerdo de socio de Microsoft Intune](https://connect.microsoft.com/ConfigurationManagervnext/Survey/Survey.aspx?SurveyID=17806). En este contrato se describen los términos que su empresa debe aceptar para convertirse en socio de las aplicaciones de Microsoft Intune. Tiene que iniciar sesión para poder ver este documento. Puede encontrar el acuerdo en el sitio de Microsoft Connect del SDK para aplicaciones de Intune, en la pestaña Encuestas o aquí. También le pediremos que ofrezca el nombre de la aplicación, el nombre de la empresa y el vínculo profundo a la aplicación en la tienda de Google o iTunes.

![Microsoft Connect](../media/microsoft-connect.png)

Usaremos su dirección de correo electrónico de registro para confirmar y completar la recepción del proceso de registro. Además, usamos la dirección de correo electrónico del registro para ponernos en contacto con usted si surge cualquier problema.

**Qué esperar del proceso de registro**: una vez que ha enviado el formulario, Microsoft se pondrá en contacto con usted a través de la dirección de correo electrónico de registro, bien para confirmar la recepción correcta, bien para pedir información adicional para completar el registro. También nos pondremos en contacto con usted si la aplicación se registra correctamente con Microsoft Intune y si la aplicación aparece en el sitio del socio de Microsoft Intune. Una vez confirmada la recepción de la información, el vínculo profundo de la aplicación se incluirá en la siguiente actualización mensual del servicio de Intune. Por ejemplo, si la información de registro se ha completado en julio, el vínculo profundo de la aplicación se admitirá hacia mediados de agosto. Si el vínculo profundo de la aplicación de tienda cambia en el futuro, tendrá que volver a registrar la aplicación. Avísenos si actualiza la aplicación con una nueva versión del SDK de la aplicación de Intune.

**Nota**: toda la información recopilada en el formulario anterior y a través del correo electrónico cruzado con el equipo de Intune cumplirá la [declaración de privacidad de Microsoft](https://www.microsoft.com/en-us/privacystatement/default.aspx).

## Habilitar su aplicación móvil iOS o Android para MAM con el SDK

Para habilitar la aplicación móvil iOS, necesitará lo siguiente:

1. **[Guía para desarrolladores sobre el SDK para aplicaciones de Intune para iOS](intune-app-sdk-ios.md)**: este documento lo guiará paso a paso para habilitar la aplicación móvil iOS con el SDK para aplicaciones de Intune. Encontrará este documento en la carpeta de documentación que ha descargado como parte del paquete del SDK para aplicaciones de Intune.
2. **SDK para aplicaciones de Intune para iOS**: como parte del paquete SDK para aplicaciones de Intune descargado desde Microsoft Intune, encontrará una carpeta llamada "SDK para aplicaciones de Intune para iOS". Esta carpeta tiene todo el contenido del SDK para aplicaciones de Intune para iOS.

Para habilitar la aplicación móvil Android para el SDK para aplicaciones de Intune, necesitará lo siguiente:

1. **[Guía para desarrolladores sobre el SDK para aplicaciones de Intune para Android](intune-app-sdk-android.md)**: este documento lo guiará paso a paso para habilitar la aplicación móvil Android con el SDK para aplicaciones de Intune. Encontrará este documento en la carpeta de documentación que ha descargado como parte del paquete del SDK para aplicaciones de Intune.
2. **SDK para aplicaciones de Intune para Android**: como parte del paquete del SDK para aplicaciones de Intune descargado de Microsoft Intune, encontrará una carpeta llamada "SDK para aplicaciones de Intune para Android". Esta carpeta tiene todo el contenido del SDK para aplicaciones de Intune para Android.

## Desactivar la telemetría para la aplicación

**SDK para aplicaciones de Intune para iOS**: de forma predeterminada, el SDK registra los datos de telemetría del SDK en eventos de uso. Estos datos se envían a Microsoft Intune.

Si decide no enviar datos de telemetría del SDK a Microsoft Intune desde su aplicación, **debe deshabilitar** la transmisión de telemetría del SDK estableciendo la propiedad `MAMTelemetryDisabled` en "Sí" en `IntuneMAMSettings`.

**SDK para aplicaciones de Intune para Android**: los datos de telemetría del SDK no se registran a través del SDK.

## Probar la aplicación habilitada para MAM con Microsoft Intune

Una vez haya completado los pasos necesarios para habilitar (integrar el SDK para aplicaciones de Intune) el SDK para aplicaciones de Intune para iOS o Android, debe asegurarse de que todas las directivas de administración de la aplicación están habilitadas y funcionando para el usuario final y el administrador de TI. Para probar la aplicación habilitada, necesitará lo siguiente:

1. **Probar la aplicación habilitada para MAM con Microsoft Intune**: este documento lo guiará paso a paso en el proceso de prueba de sus aplicaciones Android o iOS habilitadas para administración de aplicaciones móviles (MAM) con Microsoft Intune. Encontrará este documento en la carpeta de documentación que ha descargado como parte del paquete del SDK para aplicaciones de Intune.
2. **Cuenta de Microsoft Intune**: para probar sus aplicaciones habilitadas para MAM con Microsoft Intune, necesita una cuenta de Microsoft Intune. Si es un ISV que quiere habilitar las aplicaciones de la tienda Android o iOS para MAM, recibirá un código de promoción una vez completado el registro con Microsoft Intune, como se describe en el paso de registro. El código de promoción le permite registrarse para obtener una versión de prueba de un año de uso extendido de Microsoft Intune. Si está desarrollando una línea de aplicaciones empresariales que no se enviarán a la tienda, se espera que tenga acceso a Microsoft Intune a través de la empresa. También puede registrarse en [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) para obtener la versión de prueba gratuita de un mes.




<!--HONumber=Jun16_HO4-->


