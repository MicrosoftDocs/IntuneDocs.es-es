---
title: "Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune"
description: "La información de este tema le ayuda a decidir cuándo se debe usar la herramienta de ajuste de aplicaciones y el SDK de aplicaciones para permitir que las aplicaciones personalizadas de línea de negocio usen las directivas de administración de aplicaciones móviles."
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e8b218ce38a7e76135a62b1155dbf9060ba511cc
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="prepare-line-of-business-apps-for-mam"></a>Preparar aplicaciones de línea de negocio para MAM

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Puede habilitar las aplicaciones para que usen directivas de administración de aplicaciones móviles (MAM) mediante la herramienta de ajuste de aplicaciones de Intune o el SDK para aplicaciones de Intune. Use esta información para conocer sobre estos dos métodos y cuándo usarlos.

## <a name="intune-app-wrapping-tool"></a>Herramienta de ajuste de aplicaciones de Intune
La herramienta de ajuste de aplicaciones se usa principalmente para aplicaciones internas línea de negocio (LOB). Esta herramienta es una aplicación de línea de comandos que crea un contenedor en torno a la aplicación que luego permite administrarla mediante una directiva de MAM de Intune.

No se necesita el código fuente para usar la herramienta, pero se necesitan credenciales de firma.  Para obtener más información sobre las credenciales de firma, vea el [blog de Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Para obtener documentación sobre la herramienta de ajuste de aplicaciones, consulte [Android App Wrapping Tool (Herramienta de ajuste de aplicaciones para Android)](app-wrapper-prepare-android.md) e [iOS App Wrapping Tool (Herramienta de ajuste de aplicaciones para iOS)](app-wrapper-prepare-ios.md).

La herramienta de ajuste de aplicaciones **no** admite aplicaciones de App Store de Apple ni de Google Play Store. Tampoco admite ciertas características que requieren la integración del desarrollador (consulte la siguiente tabla de comparación de características).


Para obtener más información sobre la herramienta de ajuste de aplicaciones para MAM en dispositivos que no están inscritos en Intune, consulte [Proteger aplicaciones y datos de línea de negocio en dispositivos no inscritos en Microsoft Intune](/intune-classic/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune).

### <a name="reasons-to-use-the-app-wrapping-tool"></a>Razones para usar la herramienta de ajuste de aplicaciones:
* La aplicación no tiene funciones de protección de datos integradas.
* La aplicación es sencilla.
* La aplicación se implementa internamente.
* No tiene acceso al código fuente de la aplicación
* No desarrolló la aplicación.
* La aplicación tiene experiencias de autenticación de usuario mínimas.


### <a name="supported-app-development-platforms"></a>Plataformas de desarrollo de aplicaciones compatibles

|**Herramienta de ajuste de aplicaciones** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Sí|Sí|
|**Android**| No |Sí|

## <a name="intune-app-sdk"></a>SDK para aplicaciones de Intune
El SDK de aplicaciones está diseñado principalmente para clientes que tienen aplicaciones en App Store de Apple o Google Play Store y quieren administrar las aplicaciones con Intune. Pero cualquier aplicación puede aprovechar la integración del SDK, incluso las aplicaciones de línea de negocio.

Para obtener más información sobre el SDK, consulte la [Introducción](app-sdk.md). Para empezar a usar el SDK, consulte [Introducción al SDK para aplicaciones de Microsoft Intune](app-sdk-get-started.md).

### <a name="reasons-to-use-the-sdk"></a>Razones para usar el SDK
* La aplicación no tiene funciones de protección de datos integradas.
* La aplicación es compleja y contiene muchas experiencias.
* La aplicación se implementa en un almacén de aplicaciones público como Google Play o la App Store de Apple.
* Es un desarrollador de aplicaciones y tiene la experiencia técnica para usar el SDK.
* La aplicación tiene otras integraciones de SDK.
* La aplicación se actualiza con frecuencia.

### <a name="supported-app-development-platforms"></a>Plataformas de desarrollo de aplicaciones compatibles

|**SDK de aplicaciones de Intune** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Sí: usar el [componente Xamarin del SDK de aplicaciones de Intune](app-sdk-xamarin.md).|Sí: usar el [complemento Cordova del SDK de aplicaciones de Intune](app-sdk-cordova.md).|
|**Android**| Sí: usar el [componente Xamarin del SDK de aplicaciones de Intune](app-sdk-xamarin.md).|Sí: usar el [complemento Cordova del SDK de aplicaciones de Intune](app-sdk-cordova.md).|

## <a name="feature-comparison"></a>Comparación de características
En la siguiente tabla se enumeran los valores que puede usarse para el SDK para aplicaciones y la herramienta de ajuste de aplicaciones.

> [!NOTE]
> La herramienta de ajuste de aplicaciones se puede usar con Intune independiente o con Intune con Configuration Manager.

|Característica|SDK para aplicaciones|Herramienta de ajuste de aplicaciones|
|-----------|---------------------|-----------|
|Restringir contenido web para mostrar en un explorador administrado corporativo|X|X|
|Impedir copias de seguridad de Android, iTunes o iCloud|X|X|
|Permitir que la aplicación transfiera datos a otras aplicaciones|X|X|
|Permitir que la aplicación reciba datos de otras aplicaciones|X|X|
|Restringir cortar, copiar y pegar con otras aplicaciones|X|X|
|Requerir PIN simple en acceso|X|X|
|Reemplazar el PIN de aplicación integrado con PIN de Intune|X||
|Especificar el número de intentos antes de restablecer el PIN|X|X|
|Permitir desbloqueo mediante huellas digitales en lugar de mediante PIN |X|X|
|Requerir credenciales corporativas en acceso|X|X|
|Bloquear la ejecución de aplicaciones administradas en dispositivos liberados o modificados|X|X|
|Cifrar datos de aplicación|X|X|
|Volver a comprobar los requisitos de acceso tras un número especificado de minutos|X|X|
|Especificar el período de gracia sin conexión|X|X|
|Bloquear captura de pantalla (solo Android)|X|X|
|Compatibilidad con MAM sin la inscripción de dispositivos|X|X|
|Eliminación completa|X|X|
|Eliminación selectiva <br></br>**Nota**: Para iOS, cuando se quita el perfil de administración, también se quita la aplicación.|X||
|Impedir "Guardar como" |X||
|Configuración de aplicaciones de destino |X||
|Compatibilidad con aplicaciones de identidades múltiples|X||
|Estilo personalizable |X|||
### <a name="see-also"></a>Consulte también

[Herramienta de ajuste de aplicaciones para Android](app-wrapper-prepare-android.md)</br>
[Herramienta de ajuste de aplicaciones para iOS](app-wrapper-prepare-ios.md)</br>
[Usar el SDK para habilitar aplicaciones para la administración de aplicaciones móviles](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)
