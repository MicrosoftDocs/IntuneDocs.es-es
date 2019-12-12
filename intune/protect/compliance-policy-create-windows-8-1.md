---
title: 'Configuración de cumplimiento de Windows 8.1 en Microsoft Intune: Azure | Microsoft Docs'
description: Vea una lista de todas las opciones que puede usar al configurar el cumplimiento de dispositivos Windows 8.1 y Windows Phone 8.1 en Microsoft Intune. Compruebe el cumplimiento de los requisitos mínimo y máximo de sistema operativo, establezca restricciones de contraseña y longitud, habilite el cifrado en almacenamiento de datos y mucho más.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e074d922078a9772ca67a6ebd99948bc3e64601
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72813216"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Configuración de Windows 8.1 para marcar dispositivos como compatibles o no compatibles con Intune

En este artículo se enumeran y describen las distintas opciones de cumplimiento que se pueden configurar en dispositivos con Windows 8.1 en Intune. Como parte de la solución de administración de dispositivos móviles (MDM), use esta configuración para bloquear contraseñas sencillas, establecer un requisito mínimo o máximo de versión de sistema operativo y mucho más.

Esta característica se aplica a:

- Windows Phone 8,1
- Windows 8.1 y posterior

Como administrador del servicio Intune, use esta configuración de cumplimiento para proteger mejor los recursos de la organización. Para más información sobre las directivas de cumplimiento y lo que hacen, vea [Introducción a las directivas de cumplimiento](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Crear una directiva de cumplimiento](create-compliance-policy.md#create-the-policy). Para **Plataforma**, seleccione **Windows Phone 8.1** o **Windows 8.1 y posterior**.

## <a name="device-properties"></a>Propiedades de dispositivos

### <a name="operating-system-version"></a>Versión de sistema operativo

**Windows Phone 8.1 y versiones posteriores**
- **Versión mínima del sistema operativo para dispositivos móviles**:  
  Escriba la versión mínima permitida. Cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no compatible. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario del dispositivo puede optar por actualizar este y luego acceder a los recursos de la empresa.

- **Versión máxima del sistema operativo para dispositivos móviles**:  
  Escriba la versión máxima permitida. Cuando un dispositivo usa una versión de sistema operativo posterior a la de la regla, se bloquea el acceso a los recursos de la empresa. Se pide al usuario del dispositivo que se ponga en contacto con el administrador de TI. El dispositivo no podrá acceder a los recursos de la empresa mientras no cambie una regla para permitir la versión de sistema operativo.

**Windows 8.1 y versiones posteriores**
- **Versión mínima del sistema operativo**:  
  Escriba la versión mínima permitida. Cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no compatible. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario del dispositivo puede optar por actualizar este y luego acceder a los recursos de la empresa.

- **Versión máxima de SO**:  
  Escriba la versión máxima permitida. Cuando un dispositivo usa una versión de sistema operativo posterior a la de la regla, se bloquea el acceso a los recursos de la empresa. Se pide al usuario del dispositivo que se ponga en contacto con el administrador de TI. El dispositivo no podrá acceder a los recursos de la empresa mientras no cambie una regla para permitir la versión de sistema operativo.

Los equipos con Windows 8.1 devuelven la versión **3**. Si la regla de la versión de sistema operativo se establece en Windows 8.1 para Windows, el dispositivo se notificará como no compatible, aunque tenga Windows 8.1.

## <a name="system-security"></a>Seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**:  
  - **Sin configurar** (*valor predeterminado*): no se evalúa el cumplimiento o incumplimiento de esta opción de configuración.
  - **Requerir**: los usuarios deben introducir una contraseña para poder acceder al dispositivo.

- **Contraseñas sencillas**:  
  - **No configurado** (*valor predeterminado*): los usuarios pueden crear contraseñas sencillas como **1234** o **1111**.
  - **Bloquear**: los usuarios no puedan crear contraseñas sencillas, como **1234** o **1111**.  

- **Longitud mínima de la contraseña**:  
  especifique el número mínimo de dígitos o caracteres que debe tener la contraseña.

  En el caso de los dispositivos que ejecutan Windows y a los que se tiene acceso con un cuenta de Microsoft, la Directiva de cumplimiento no puede evaluarse correctamente si se cumple alguna de las siguientes condiciones:  
  - La longitud mínima de la contraseña es superior a ocho caracteres
  - El número mínimo de conjuntos de caracteres es superior a dos

- **Tipo de contraseña**:  
  elija si una contraseña debe tener solo caracteres **numéricos** o si es necesario combinar números y otros caracteres (alfanuméricos).

  Cuando se establece en *alfanumérico*, está disponible la siguiente configuración.  

  - **Número de caracteres no alfanuméricos en la contraseña**:  
    Cuando el *tipo de contraseña* está establecido en **alfanumérico**, especifique el número mínimo de conjuntos de caracteres que debe contener la contraseña. Las opciones incluyen de **0** a **4** conjuntos, con un valor predeterminado de **1**.
    
    Los conjuntos de cuatro caracteres son los siguientes:
    - Letras minúsculas
    - Letras mayúsculas
    - Símbolos
    - Números

    Para establecer un número mayor, es necesario que el usuario cree una contraseña más compleja. En el caso de los dispositivos a los que se tiene acceso con un cuenta de Microsoft, la Directiva de cumplimiento no puede evaluarse correctamente si se cumple alguna de las siguientes condiciones:

    - La longitud mínima de la contraseña es superior a ocho caracteres
    - El número mínimo de conjuntos de caracteres es superior a dos

- **Máximo de minutos de inactividad antes de solicitar la contraseña**:  
  especifique el tiempo de inactividad antes de que el usuario deba volver a escribir la contraseña.

- **Expiración de la contraseña (días)** :  
  seleccione el número de días que faltan para que expire la contraseña y los usuarios deban crear una nueva.

- **Número de contraseñas anteriores que no se pueden reutilizar**:  
  escriba el número de contraseñas usadas previamente que no se pueden volver a usar.

### <a name="encryption"></a>Cifrado

- **Cifrado de almacenamiento de datos en el dispositivo**:  
  - **Sin configurar** (*valor predeterminado*).
  - **Requerir**: use *Requerir* para cifrar el almacenamiento de datos en los dispositivos.


<!-- not on phone   
- **Require encryption on mobile device**: **Require** the device to be encrypted to connect to data storage resources.
--> 

## <a name="next-steps"></a>Pasos siguientes

- [Agregar acciones para dispositivos no compatibles](actions-for-noncompliance.md) y [usar etiquetas de ámbito para filtrar directivas](../fundamentals/scope-tags.md).
- [Supervisar las directivas de cumplimiento](compliance-policy-monitor.md).
- Vea la [configuración de directivas de cumplimiento para dispositivos Windows 10 y versiones posteriores](compliance-policy-create-windows.md).