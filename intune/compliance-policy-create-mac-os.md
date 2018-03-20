---
title: "Creación de una directiva de cumplimiento para dispositivos macOS en Microsoft Intune"
titleSuffix: 
description: Cree una directiva de cumplimiento de dispositivos de Microsoft Intune para dispositivos macOS para poder especificar los requisitos que debe cumplir un dispositivo para que sea compatible.
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e7703b8ea26d6ce53b82e806a78c788d14ae05b4
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="create-a-device-compliance-policy-for-macos-devices-with-intune"></a>Creación de una directiva de cumplimiento para dispositivos macOS con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Una directiva de cumplimiento de dispositivos de Intune para macOS especifica las reglas y la configuración que los dispositivos macOS deben cumplir para que se consideren compatibles. Estas directivas se pueden usar con el acceso condicional para permitir o bloquear el acceso a recursos de la empresa, y se pueden obtener informes de dispositivos y realizar acciones en caso de incumplimiento. Las directivas de cumplimiento de dispositivos para cada plataforma se crean en el portal de Azure de Intune.

## <a name="before-you-begin"></a>Antes de comenzar

Antes de crear y asignar una directiva de cumplimiento de dispositivos, revise los conceptos de la directiva de cumplimiento de dispositivos Intune.

- Para más información sobre las directivas de cumplimiento de dispositivos, consulte la [introducción a las directivas de cumplimiento de dispositivos](device-compliance.md).

> [!IMPORTANT]
> Necesita crear directivas de cumplimiento de dispositivos para cada plataforma. La configuración de las directivas de cumplimiento de dispositivos de Intune depende de las capacidades de la plataforma, que es la configuración expuesta a través del protocolo MDM.

En la tabla siguiente se explica cómo se administran las configuraciones no conformes cuando se usa una directiva de cumplimiento con una directiva de acceso condicional:


| Configuración de directiva | macOS 10.11 y versiones posteriores |
| --- | --- |
| **Configuración de PIN o contraseña** | Corregido |   
| **Cifrado del dispositivo** | Corregido (estableciendo PIN) |
| **Perfil de correo electrónico** | En cuarentena |
|**Versión de SO mínima** | En cuarentena |
| **Versión de SO máxima** | En cuarentena |  


**Corregido** = el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena** = el sistema operativo del sistema no exige compatibilidad. (Por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo). Si los dispositivos no son compatibles, se emprenden las acciones siguientes:

- El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
- El portal de empresa notifica al usuario acerca de los problemas de cumplimiento.

## <a name="macos-compliance-policy-settings"></a>Configuración de directiva de cumplimiento de macOS

Tiene distintas categorías con valores distintos entre los cuales elegir cuando se cree un nuevo cumplimiento de dispositivos con Intune:

- Estado de dispositivos

- Propiedades de dispositivos

- Seguridad del sistema

### <a name="device-health"></a>Estado de dispositivos

- **Requerir protección de integridad del sistema**: establezca en **Requerir** para comprobar si los dispositivos macOS tienen habilitada la protección de integridad del sistema.

### <a name="device-properties"></a>Propiedades del dispositivo

- **Versión mínima del sistema operativo**: cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no conforme. Se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario puede elegir actualizar su dispositivo. Después de eso, puede acceder a los recursos de la empresa.

- **Versión máxima del sistema operativo**: cuando un dispositivo usa una versión del sistema operativo posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se pide al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.

### <a name="system-security-settings"></a>Configuración de seguridad del sistema

#### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: establezca esta opción en **Requerir** para que los usuarios tengan que escribir una contraseña para poder acceder al dispositivo.

- **Contraseñas sencillas**: establezca esta opción en **Bloquear** para que los usuarios no puedan crear una contraseña sencilla como **1234** o **1111**.

- **Longitud mínima de la contraseña**: especifique el número mínimo de dígitos o caracteres que debe tener la contraseña.

- **Tipo de contraseña**: especifique si el usuario debe crear una contraseña **alfanumérica** o **numérica**.

- **Número de caracteres no alfanuméricos en la contraseña**: si establece **Tipo de contraseña requerida** en **Alfanumérico**, use esta opción para especificar el número mínimo de juegos de caracteres que debe tener la contraseña. 

    > [!NOTE]
    > Para establecer un número mayor, es necesario que el usuario cree una contraseña más compleja.

    > [!IMPORTANT]
    > En dispositivos macOS, esta configuración hace referencia al número de caracteres especiales (por ejemplo, **!** **#** , **&amp;**) que deben incluirse en la contraseña.

- **Máximo de minutos de inactividad antes de solicitar la contraseña**: especifique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir la contraseña.

- **Expiración de la contraseña (días)**: seleccione el número de días (entre 1 y 250) que faltan para que la contraseña expire y se deba crear una nueva.

- **Número de contraseñas anteriores que no se pueden reutilizar**: especifique el número de contraseñas usadas anteriormente que no se pueden volver a usar.

    > [!IMPORTANT]
    > Cuando se modifica un requisito de contraseña en un dispositivo macOS, no se aplica hasta la siguiente vez que el usuario cambia la contraseña. Por ejemplo, si establece la restricción de longitud de contraseña en ocho dígitos y el dispositivo macOS actualmente tiene una contraseña de seis dígitos, el dispositivo sigue siendo conforme hasta la siguiente vez que el usuario actualiza la contraseña en él.

## <a name="to-create-a-device-compliance-policy"></a>Pasos para crear una directiva de cumplimiento de dispositivos

1. Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de Intune.

2. Después de iniciar sesión correctamente, podrá ver el **panel de Azure**.

3. Elija **Todos los servicios** en el menú de la izquierda y, luego, escriba **Intune** en el filtro del cuadro de texto.

4. Elija **Intune**, podrá ver el **panel de Intune**.

5. Elija **Cumplimiento de dispositivos** y, luego, elija **Directivas** en **Administrar**.

6. Haga clic en **Crear directiva**.

7. Escriba un nombre y una descripción y elija la plataforma a la que quiere que se aplique esta directiva.

8. En el panel **Directiva de cumplimiento de Mac** que se abre, elija las categorías de configuración de cumplimiento de dispositivos **Seguridad del sistema**, **Estado del dispositivo** y **Propiedades de dispositivo** para especificar la configuración.

10. Una vez que haya elegido la configuración, seleccione **Aceptar** en cada categoría de configuración de cumplimiento de dispositivos.

11. Elija **Aceptar** y, luego, **Crear**.

## <a name="assign-user-groups"></a>Asignación de grupos de usuarios

Para asignar una directiva de cumplimiento a los usuarios, elija una directiva que haya configurado. Las directivas existentes se pueden encontrar en el panel **Conformidad del dispositivo: directivas**.

1. Elija la directiva de cumplimiento de dispositivos que desea asignar a los usuarios y elija **Asignaciones**. Se abre el panel donde puede seleccionar **grupos de seguridad de Azure Active Directory** y asignarlos a la directiva.

2. Elija **Grupos seleccionados** para abrir el panel en el que se muestran los grupos de seguridad de Azure AD.

3. Haga clic en **Guardar** para asignar la directiva de cumplimiento de dispositivos a los grupos de seguridad de Azure AD.

4. Una vez que asigne la directiva de cumplimiento de dispositivos a los grupos, puede cerrar el panel **Asignaciones**.

    > [!TIP]
    > De manera predeterminada, los dispositivos comprueban el cumplimiento cada ocho horas, aunque los usuarios pueden forzar este proceso a través de la aplicación Portal de empresa de Intune.

## <a name="next-steps"></a>Pasos siguientes

[Supervisión de las directivas de cumplimiento de dispositivos](compliance-policy-monitor.md)
