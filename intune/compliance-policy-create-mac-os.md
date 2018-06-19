---
title: Creación de una directiva de cumplimiento de dispositivos macOS en Microsoft Intune - Azure | Microsoft Docs
description: Cree o configure una directiva de cumplimiento de dispositivos de Microsoft Intune para dispositivos macOS para usar la protección de integridad del sistema, establezca la versión de sistema operativo mínima y máxima, elija los requisitos de contraseña y cifre el almacenamiento de datos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a797c68ca43a6173a4bac70e914d3f763ce5e6d0
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31442583"
---
# <a name="add-a-device-compliance-policy-for-macos-devices-with-intune"></a>Incorporación de una directiva de cumplimiento de dispositivos macOS con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Una directivas de cumplimiento de dispositivos macOS para Intune determina las reglas y la configuración que deben cumplir los dispositivos macOS para que sean compatibles. Al usar directivas de cumplimiento de dispositivos con acceso condicional, puede permitir o bloquear el acceso a los recursos de la empresa. También puede obtener informes de dispositivos y realizar acciones en caso de incumplimiento. Las directivas de cumplimiento de dispositivos para cada plataforma se pueden crear en Azure Portal de Intune. Para más información sobre las directivas de cumplimiento, consulte [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).

En la tabla siguiente se explica cómo se administran las configuraciones no conformes cuando se usa una directiva de cumplimiento con una directiva de acceso condicional:

---------------------------

| Configuración de directiva | macOS 10.11 y versiones posteriores |
| --- | --- |
| **Configuración de PIN o contraseña** | Corregido |   
| **Cifrado del dispositivo** | Corregido (estableciendo PIN) |
| **Perfil de correo electrónico** | En cuarentena |
|**Versión de SO mínima** | En cuarentena |
| **Versión de SO máxima** | En cuarentena |

---------------------------

**Corregido** = el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena** = el sistema operativo del sistema no exige compatibilidad. (Por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo). Si los dispositivos no son compatibles, se emprenden las acciones siguientes:

- El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
- El portal de empresa notifica al usuario acerca de los problemas de cumplimiento.

## <a name="create-a-device-compliance-policy"></a>Crear una directiva de cumplimiento de dispositivos

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Para **Plataforma**, seleccione **macOS**. Seleccione **Definir configuración** y especifique las opciones **Estado de dispositivos**, **Propiedades de dispositivo** y **Seguridad del sistema**. Cuando termine, seleccione **Aceptar** y **Crear**.

## <a name="device-health"></a>Estado de dispositivos

- **Requerir protección de integridad del sistema**: **requiere** que los dispositivos macOS tengan habilitada la [protección de integridad del sistema](https://support.apple.com/HT204899).

## <a name="device-properties"></a>Propiedades del dispositivo

- **Versión mínima del sistema operativo**: cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no conforme. Se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo y luego acceder a los recursos de la empresa.
- **Versión máxima de SO**: cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa. Se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, el dispositivo no podrá acceder a los recursos de la empresa.

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: **requiere** que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos.
- **Contraseñas sencillas**: establezca esta opción en **Bloquear** para que los usuarios no puedan crear contraseñas sencillas como **1234** o **1111**. Establézcala en **No configurado** para permitir a los usuarios crear contraseñas como **1234** o **1111**.
- **Longitud mínima de la contraseña**: indique el número mínimo de dígitos o caracteres que debe tener la contraseña.
- **Tipo de contraseña**: elija si una contraseña debe tener solo caracteres **numéricos** o si es necesario combinar números y otros caracteres (**alfanuméricos**).
- **Número de caracteres no alfanuméricos en la contraseña**: indique el número mínimo de caracteres especiales (&, #, %, !, etc.) que se deben incluir en la contraseña.

    Para establecer un número mayor, es necesario que el usuario cree una contraseña más compleja.

- **Máximo de minutos de inactividad antes de solicitar la contraseña**: indique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir la contraseña.
- **Expiración de la contraseña (días)**: seleccione el número de días que faltan para que la contraseña expire y se deba crear una nueva.
- **Número de contraseñas anteriores que no se pueden reutilizar**: indique el número de contraseñas usadas anteriormente que no se pueden usar.

    > [!IMPORTANT]
    > Cuando se modifica un requisito de contraseña en un dispositivo macOS, no se aplica hasta la siguiente vez que el usuario cambia la contraseña. Por ejemplo, si establece la restricción de longitud de contraseña en ocho dígitos y el dispositivo macOS actualmente tiene una contraseña de seis dígitos, el dispositivo sigue siendo conforme hasta la siguiente vez que el usuario actualiza la contraseña en él.

### <a name="encryption"></a>Cifrado

- **Cifrado de almacenamiento de datos en un dispositivo**: elija **Requerir** para cifrar el almacenamiento de datos en los dispositivos.

## <a name="assign-user-groups"></a>Asignación de grupos de usuarios

1. Elija una directiva que haya configurado. Las directivas existentes están en **Conformidad de dispositivos** > **Directivas**.
2. Elija la directiva y luego **Asignaciones**. Puede incluir o excluir grupos de seguridad de Azure Active Directory (AD).
3. Elija **Grupos seleccionados** para ver los grupos de seguridad de Azure AD. Seleccione los grupos de usuarios a los que quiera aplicar esta directiva y elija **Guardar** para implementar la directiva a los usuarios.

> [!TIP]
> De forma predeterminada, los dispositivos comprueban el cumplimiento cada ocho horas. Pero los usuarios pueden forzar este proceso a través de la aplicación Portal de empresa de Intune.

Ya ha aplicado la directiva a los usuarios. Se evalúa el cumplimiento por parte de los dispositivos usados por los usuarios a los que se aplique la directiva.

## <a name="next-steps"></a>Pasos siguientes
[Automatización del correo electrónico y adición de acciones para dispositivos no compatibles](actions-for-noncompliance.md)  
[Supervisión de las directivas de cumplimiento de dispositivos de Intune](compliance-policy-monitor.md)