---
title: "Preparación de aplicaciones para la administración de aplicaciones móviles | Microsoft Intune"
description: "La información de este tema le ayuda a decidir cuándo se debe utilizar la herramienta de ajuste de aplicaciones y el SDK de aplicaciones para habilitar la línea personalizada de aplicaciones empresariales con el fin de utilizar las directivas de administración de aplicaciones móviles."
keywords: 
author: karthikaraman
manager: arob98
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2038ed6219a94dc4285891d71ce00fd51310f3e3
ms.openlocfilehash: a7aa32704a8eb33d20a3149941b3e6f2a91478a0


---

# Decidir cómo preparar las aplicaciones para la administración de aplicaciones móviles mediante Microsoft Intune
Puede habilitar las aplicaciones para que usen directivas de administración de aplicaciones móviles mediante la herramienta de ajuste de aplicaciones de Intune o el SDK para aplicaciones de Intune. Use esta información para conocer sobre estos dos métodos y cuándo usarlos.

## Herramienta de ajuste de aplicaciones de Intune
La herramienta de ajuste de aplicaciones se usa principalmente para aplicaciones internas línea de negocio (LOB). Esta herramienta es una aplicación de línea de comandos que crea un contenedor en torno a la aplicación, que permite administrarla mediante una directiva de administración de aplicaciones móviles de Intune. No se necesita el código fuente para usar la herramienta, pero se necesitan credenciales de firma.  Para obtener más información sobre las credenciales de firma, vea el [blog de Intune](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Para obtener documentación sobre la herramienta de ajuste de aplicaciones, consulte [Android App Wrapping Tool (Herramienta de ajuste de aplicaciones para Android)](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) e [iOS App Wrapping Tool (Herramienta de ajuste de aplicaciones para iOS)](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

La herramienta de ajuste de aplicaciones no admite las aplicaciones de App Store o Play Store ni las características que requieren la integración del tiempo de desarrollo (vea la siguiente tabla de comparación de características).

Se debe usar la herramienta de ajuste de aplicaciones en lugar del SDK, si la aplicación ya se ha escrito o si el código fuente no está disponible.

## SDK para aplicaciones de Intune
El SDK para aplicaciones está diseñado principalmente para clientes que tienen aplicaciones en App Store y Play Store y quieren administrar las aplicaciones con Intune. Sin embargo, cualquier aplicación puede aprovechar la integración del SDK, incluso si se trata de una aplicación de línea de negocio.

Para obtener más información sobre el SDK, consulte la [Introducción](/intune/develop/intune-app-sdk). Para empezar a usar el SDK, consulte [Introducción al SDK para aplicaciones de Microsoft Intune](/intune/develop/intune-app-sdk-get-started).

## Comparación de características
En la siguiente tabla se enumeran los valores que puede usarse para el SDK para aplicaciones y la herramienta de ajuste de aplicaciones.

> [!NOTE]
> La herramienta de ajuste de aplicaciones solo se puede usar con Intune independiente o con Intune con Configuration Manager.

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
|Impedir "Guardar como..." |X||
|Compatibilidad con aplicaciones de identidades múltiples|X||

### Consulte también
[Android app wrapping tool (Herramienta de ajuste de aplicaciones para Android)](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[iOS app wrapping tool (Herramienta de ajuste de aplicaciones para iOS)](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Use the SDK to enable apps for mobile application management (Usar el SDK para habilitar aplicaciones para la administración de aplicaciones móviles)](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Jul16_HO4-->


