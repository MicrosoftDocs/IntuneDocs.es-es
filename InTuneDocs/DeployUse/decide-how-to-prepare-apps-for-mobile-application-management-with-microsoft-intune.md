---
title: "Preparación de aplicaciones para la administración de aplicaciones móviles | Microsoft Intune"
description: "La información de este tema le ayuda a decidir cuándo se debe usar la herramienta de ajuste de aplicaciones y el SDK de aplicaciones para permitir que las aplicaciones personalizadas de línea de negocio usen las directivas de administración de aplicaciones móviles."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 376c9bce811ffd986242678929469f3e28bfad4c
ms.openlocfilehash: e145baf0f7366f331e8d1df994a8fa40ec693227


---

# <a name="decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune"></a>Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune
Puede habilitar las aplicaciones para que usen directivas de administración de aplicaciones móviles (MAM) mediante la herramienta de ajuste de aplicaciones de Intune o el SDK para aplicaciones de Intune. Use esta información para conocer sobre estos dos métodos y cuándo usarlos.

## <a name="intune-app-wrapping-tool"></a>Herramienta de ajuste de aplicaciones de Intune
La herramienta de ajuste de aplicaciones se usa principalmente para aplicaciones internas línea de negocio (LOB). Esta herramienta es una aplicación de línea de comandos que crea un contenedor en torno a la aplicación que luego permite administrarla mediante una directiva de MAM de Intune.

No se necesita el código fuente para usar la herramienta, pero se necesitan credenciales de firma.  Para obtener más información sobre las credenciales de firma, vea el [blog de Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Para obtener documentación sobre la herramienta de ajuste de aplicaciones, consulte [Android App Wrapping Tool (Herramienta de ajuste de aplicaciones para Android)](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) e [iOS App Wrapping Tool (Herramienta de ajuste de aplicaciones para iOS)](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

La herramienta de ajuste de aplicaciones **no** admite aplicaciones de App Store de Apple ni de Google Play Store. Tampoco admite ciertas características que requieren la integración del desarrollador (consulte la siguiente tabla de comparación de características).

Se debe usar la herramienta de ajuste de aplicaciones en lugar del SDK, si la aplicación ya se ha escrito o si el código fuente no está disponible.

Para obtener más información sobre la herramienta de ajuste de aplicaciones para MAM en dispositivos que no están inscritos en Intune, consulte [Proteger aplicaciones y datos de línea de negocio en dispositivos no inscritos en Microsoft Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

### <a name="supported-app-development-platforms"></a>Plataformas de desarrollo de aplicaciones compatibles

|**Herramienta de ajuste de aplicaciones** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Sí|Sí|
|**Android**| No |Sí|

## <a name="intune-app-sdk"></a>SDK para aplicaciones de Intune
El SDK de aplicaciones está diseñado principalmente para clientes que tienen aplicaciones en App Store de Apple o Google Play Store y quieren administrar las aplicaciones con Intune. Pero cualquier aplicación puede aprovechar la integración del SDK, incluso las aplicaciones de línea de negocio.

Para obtener más información sobre el SDK, consulte la [Introducción](/intune/develop/intune-app-sdk). Para empezar a usar el SDK, consulte [Introducción al SDK para aplicaciones de Microsoft Intune](/intune/develop/intune-app-sdk-get-started).

### <a name="supported-app-development-platforms"></a>Plataformas de desarrollo de aplicaciones compatibles

|**SDK de aplicaciones de Intune** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Sí: usar el componente Xamarin del SDK de aplicaciones de Intune.|Sí: usar el complemento Cordova del SDK de aplicaciones de Intune.|
|**Android**| Sí: usar el componente Xamarin del SDK de aplicaciones de Intune.|Sí: usar el complemento Cordova del SDK de aplicaciones de Intune.|

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
|Requerir huella digital en lugar de PIN (solo iOS)<br></br>**Nota**: Únicamente disponible en entornos del tipo solo administración de aplicaciones móviles.|X||
|Requerir credenciales corporativas en acceso|X|X|
|Bloquear la ejecución de aplicaciones administradas en dispositivos liberados o modificados|X|X|
|Cifrar datos de aplicación|X|X|
|Volver a comprobar los requisitos de acceso tras un número especificado de minutos|X|X|
|Especificar el período de gracia sin conexión|X|X|
|Bloquear captura de pantalla (solo Android)|X|X|
|Eliminación completa|X|X|
|Eliminación selectiva <br></br>**Nota**: Para iOS, cuando se quita el perfil de administración, también se quita la aplicación.|X||
|Impedir "Guardar como" |X||
|Compatibilidad con aplicaciones de identidades múltiples|X||
|Compatibilidad con MAM sin la inscripción de dispositivos|X|X|
### <a name="see-also"></a>Consulte también

[Herramienta de ajuste de aplicaciones para Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Herramienta de ajuste de aplicaciones para iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Usar el SDK para habilitar aplicaciones para la administración de aplicaciones móviles](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Nov16_HO3-->


