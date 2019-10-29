---
title: Configuración de cumplimiento de dispositivos macOS en Microsoft Intune - Azure | Microsoft Docs
description: Vea una lista de todas las opciones que puede usar al configurar el cumplimiento de dispositivos macOS en Microsoft Intune. Se necesitan las opciones de Apple de protección de integridad del sistema, establecer restricciones de contraseña, requerir un firewall, permitir el equipo selector y mucho más.
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
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 518f0b825b71a9773ed66dd480b329e998f919c4
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813507"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Configuración de macOS para marcar dispositivos como compatibles o no compatibles con Intune

En este artículo se enumeran y describen las distintas opciones de configuración de cumplimiento que se pueden establecer en dispositivos con macOS y versiones posteriores en Intune. Como parte de la solución de administración de dispositivos móviles (MDM), use esta configuración para establecer un requisito mínimo o máximo de versión de sistema operativo, establecer la expiración de contraseñas y mucho más.

Esta característica se aplica a:

- macOS

Como administrador del servicio Intune, use esta configuración de cumplimiento para proteger mejor los recursos de la organización. Para más información sobre las directivas de cumplimiento y lo que hacen, vea [Introducción a las directivas de cumplimiento](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Crear una directiva de cumplimiento](create-compliance-policy.md#create-the-policy). Para **Plataforma**, seleccione **macOS**.

## <a name="device-health"></a>Estado de dispositivos

- **Requerir protección de integridad del sistema**:  
  - **Sin configurar** (*valor predeterminado*): no se evalúa el cumplimiento o incumplimiento de esta opción de configuración.
  - **Requerir** : requerir que los dispositivos MacOS tengan habilitada la [protección de integridad del sistema](https://support.apple.com/HT204899) (abre el sitio web de Apple).  

## <a name="device-properties"></a>Propiedades de dispositivos

- **Sistema operativo mínimo requerido**:  
  Cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no compatible. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario del dispositivo puede elegir actualizar su dispositivo. Después, puede acceder a los recursos de la empresa.

- **Versión de sistema operativo máxima permitida**:  
  Cuando un dispositivo usa una versión de sistema operativo posterior a la de la regla, se bloquea el acceso a los recursos de la empresa. Se pide al usuario del dispositivo que se ponga en contacto con el administrador de TI. El dispositivo no podrá acceder a los recursos de la empresa mientras no cambie una regla para permitir la versión de sistema operativo.

- **Versión de compilación mínima del sistema operativo**:  
  cuando Apple publica actualizaciones de seguridad, habitualmente se actualiza el número de compilación, no la versión del sistema operativo. Use esta característica para escribir un número de compilación mínimo permitido en el dispositivo.

- **Versión de compilación máxima del sistema operativo**:  
  cuando Apple publica actualizaciones de seguridad, habitualmente se actualiza el número de compilación, no la versión del sistema operativo. Use esta característica para escribir un número de compilación máximo permitido en el dispositivo.

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**:  
  - **Sin configurar** (*valor predeterminado*).
  - **Requerir**: los usuarios deben introducir una contraseña para poder acceder al dispositivo.

- **Contraseñas sencillas**:  
  - **No configurado** (*valor predeterminado*): los usuarios pueden crear contraseñas sencillas, como **1234** o **1111**.
  - **Bloquear**: los usuarios no puedan crear contraseñas sencillas, como **1234** o **1111**.

- **Longitud mínima de la contraseña**:  
  especifique el número mínimo de dígitos o caracteres que debe tener la contraseña.

- **Tipo de contraseña**: elija si una contraseña debe tener solo caracteres **numéricos** o si es necesario combinar números y otros caracteres (**alfanuméricos**).

- **Número de caracteres no alfanuméricos en la contraseña**:  
  escriba el número mínimo de caracteres especiales, como `&`, `#`, `%`, `!`, etc., que se deben incluir en la contraseña.

  Para establecer un número mayor, es necesario que el usuario cree una contraseña más compleja.

- **Máximo de minutos de inactividad antes de solicitar la contraseña**:  
  especifique el tiempo de inactividad antes de que el usuario deba volver a escribir la contraseña.

- **Expiración de la contraseña (días)** :  
  seleccione el número de días que faltan para que expire la contraseña y se deba crear una nueva.

- **Número de contraseñas anteriores que no se pueden reutilizar**:  
  escriba el número de contraseñas usadas previamente que no se pueden volver a usar.
> [!IMPORTANT]
> Cuando se modifica un requisito de contraseña en un dispositivo macOS, no se aplica hasta la siguiente vez que el usuario cambia la contraseña. Por ejemplo, si establece la restricción de longitud de contraseña en ocho dígitos y el dispositivo macOS actualmente tiene una contraseña de seis dígitos, el dispositivo sigue siendo conforme hasta la siguiente vez que el usuario actualiza la contraseña en él.

### <a name="encryption"></a>Cifrado

- **Cifrado de almacenamiento de datos en un dispositivo**:  
  - **Sin configurar** (*valor predeterminado*).
  - **Requerir**: use *Requerir* para cifrar el almacenamiento de datos en los dispositivos.

### <a name="device-security"></a>Seguridad de dispositivos

Firewall protege los dispositivos frente al acceso de red no autorizado. Puede usar Firewall para controlar las conexiones por cada aplicación. 

- **Firewall**:  
  - **Sin configurar** (*valor predeterminado*): esta opción de configuración deja el firewall desactivado y se permite el tráfico de red (no se bloquea).
  - **Habilitar**: use *Habilitar* para ayudar a proteger los dispositivos frente al acceso no autorizado. Habilitar esta característica permite controlar las conexiones entrantes de Internet y usar el modo sigiloso. 

- **Conexiones entrantes**:  
  - **Sin configurar** (*valor predeterminado*): permite las conexiones entrantes y los servicios de uso compartido.
  - **Bloquear**: bloquee todas las conexiones de red entrantes excepto las necesarias para los servicios básicos de Internet, como DHCP, Bonjour e IPSec. Esta opción también bloquea todos los servicios de uso compartido, incluido el uso compartido de pantalla, acceso remoto, uso compartido de música de iTunes y mucho más.  

- **Modo sigiloso**:  
  - **No configurado** (*valor predeterminado*): esta opción deja el modo oculto desactivado.
  - **Habilitar**: active el modo sigiloso para evitar que el dispositivo responda a solicitudes de sondeo, que pueden provenir de usuarios malintencionados. Cuando se habilita, el dispositivo sigue respondiendo a las solicitudes entrantes de las aplicaciones autorizadas.  

### <a name="gatekeeper"></a>Equipo selector

Para más información, vea [Gatekeeper en macOS](https://support.apple.com/HT202491) (abre el sitio web de Apple).

**Permitir aplicaciones descargadas desde estas ubicaciones**: permite que las aplicaciones admitidas se instalen en los dispositivos desde diferentes ubicaciones. Opciones de ubicación:

- **No configurado** (*valor predeterminado*): la opción de equipo selector no tiene ningún impacto en el cumplimiento o no cumplimiento.  
- **Mac App Store**: solo instala aplicaciones para Mac App Store. No se pueden instalar aplicaciones de terceros ni de desarrolladores identificados. Si un usuario selecciona Gatekeeper para instalar aplicaciones fuera de Mac App Store, el dispositivo se considera no compatible.
- **Mac App Store y desarrolladores identificados**: instala aplicaciones para Mac App Store y desarrolladores identificados. macOS comprueba la identidad de los desarrolladores y realiza otras comprobaciones relacionadas con la integridad de la aplicación. Si un usuario selecciona Gatekeeper para instalar aplicaciones fuera de estas opciones, el dispositivo se considera no compatible.
- **Cualquier ubicación**: las aplicaciones pueden instalarse desde cualquier lugar y por parte de cualquier desarrollador. Esta opción es la menos segura.
 

## <a name="next-steps"></a>Pasos siguientes

- [Agregar acciones para dispositivos no compatibles](actions-for-noncompliance.md) y [usar etiquetas de ámbito para filtrar directivas](../fundamentals/scope-tags.md).
- [Supervisar las directivas de cumplimiento](compliance-policy-monitor.md).
- Vea [Configuración de directivas de cumplimiento para dispositivos iOS](compliance-policy-create-ios.md).