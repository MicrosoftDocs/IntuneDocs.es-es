---
# required metadata

title: Directivas de cumplimiento de dispositivos | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Directivas de cumplimiento de dispositivos en Microsoft Intune
## ¿Qué es una directiva de cumplimiento?
Para proteger los datos de la compañía, debe asegurarse de que los dispositivos usados para tener acceso a las aplicaciones y a los datos de la empresa cumplan ciertas reglas como, por ejemplo, usar un PIN para el acceso al dispositivo y que los datos almacenados en el dispositivo estén cifrados. A un conjunto de estas reglas se le denomina directiva de cumplimiento.

## ¿Cómo se deben usar las directivas de cumplimiento?
Las directivas de cumplimiento se pueden usar con directivas de acceso condicional para restringir el acceso a los dispositivos que cumplen con las reglas de directivas de cumplimiento. Lea el artículo [Restrict access to email and O365 services](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) (Restringir el acceso al correo electrónico y los servicios de O365) para entender cómo se pueden usar las dos directivas conjuntamente.

También puede usar las directivas de cumplimiento con independencia del acceso condicional. Cuando se usan de forma independiente, los dispositivos de destino se evalúan y se notifica su estado de cumplimiento. Por ejemplo, si quiere informar sobre el número de dispositivos que no están cifrados o sobre qué dispositivos están liberados o modificados. Sin embargo, cuando se usa de forma independiente, no se aplican restricciones de acceso a los recursos de empresa.

Usted se encarga de implementar las directivas de cumplimiento para los usuarios. Cuando se implementa una directiva de cumplimiento para un usuario, se comprueba el cumplimiento de todos los dispositivos del usuario.

En la siguiente tabla se enumeran los tipos de dispositivos compatibles con las directivas de cumplimiento y se indica cómo se administran los valores de configuración no compatibles cuando se usa la directiva con una directiva de acceso condicional.

--------------

|Configuración de directiva| Windows 8.1 y posterior| Windows Phone 8.1 y versiones posteriores| iOS 6.0 y versiones posteriores|Android 4.0 y versiones posteriores<br/>Samsung KNOX Standard 4.0 y posterior|
|-----|----|----|----|
|**Configuración de PIN o contraseña** |Corregido|Corregido|Corregido|En cuarentena|
|**Cifrado del dispositivo**|No aplicable|Corregido|Corregido (estableciendo PIN)|En cuarentena|
|**Dispositivo liberado o modificado**|No aplicable|No aplicable|En cuarentena (no es una configuración)|En cuarentena (no es una configuración)|
|**Perfil de correo electrónico**|No aplicable|No aplicable|En cuarentena|No aplicable|
|**Versión de SO mínima**|En cuarentena|En cuarentena|En cuarentena|En cuarentena|
|**Versión de SO máxima**|En cuarentena| En cuarentena| En cuarentena| En cuarentena|
|**Atestación de estado de Windows**|Windows 10 y Windows 10 Mobile están en cuarentena.<br /><br />La opción de configuración no es aplicable a Windows 8.1.|No aplicable|No aplicable|No aplicable|
--------------
**Corregido** = el sistema operativo del dispositivo exige el cumplimiento (por ejemplo, el usuario debe establecer un PIN).  La configuración nunca será no compatible.

**En cuarentena** = el sistema operativo del dispositivo no exige el cumplimiento (por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo). Si los dispositivos no son compatibles, se emprenden las acciones siguientes:

-   El dispositivo se bloqueará si el usuario se rige por una directiva de acceso condicional.

-   El portal de empresa notificará al usuario los problemas de cumplimiento que se produzcan.

## Pasos siguientes
[Crear una directiva de cumplimiento de dispositivos](create-a-device-compliance-policy-in-microsoft-intune.md)

[Implementar y supervisar una directiva de cumplimiento de dispositivos](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### Consulte también
[Restrict access to email and O365 services (Restringir el acceso al correo electrónico y los servicios de O365)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


<!--HONumber=May16_HO1-->


