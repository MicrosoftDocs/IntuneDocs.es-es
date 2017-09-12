---
title: "Creación de una directiva de cumplimiento para macOS"
titleSuffix: Azure portal
description: "Obtenga información sobre cómo crear una directiva de cumplimiento para dispositivos macOS.\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0444183e-f924-4605-96a8-48fdfbc58fd1
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0c6e3c3f8e31d9ac6d42c3a2c519836dee186f0b
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="create-a-device-compliance-policy-for-macos-devices-preview-with-intune"></a>Creación de una directiva de cumplimiento para dispositivos macOS (versión preliminar) con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="before-you-begin"></a>Antes de comenzar

Antes de crear y asignar una directiva de cumplimiento de dispositivos, revise los conceptos de la directiva de cumplimiento de dispositivos Intune.

- Para más información sobre las directivas de cumplimiento de dispositivos, consulte la [introducción a las directivas de cumplimiento de dispositivos](device-compliance.md).

> [!IMPORTANT]
> Necesita crear directivas de cumplimiento de dispositivos para cada plataforma. La configuración de la directiva de cumplimiento de dispositivos Intune depende de las funcionalidades de la plataforma, que es la configuración expuesta a través del protocolo MDM.

En la tabla siguiente se describe cómo administrar la configuración de no conformidad cuando se usa una directiva de cumplimiento con una directiva de acceso condicional.

-------------------------------


| **Configuración de directiva** | **macOS 10.11 y versiones posteriores** |
| --- | --- |
| **Configuración de PIN o contraseña** | Corregido |   
| **Cifrado del dispositivo** | Corregido (estableciendo PIN) |
| **Perfil de correo electrónico** | En cuarentena |
|**Versión de SO mínima** | En cuarentena |
| **Versión de SO máxima** | En cuarentena |  
| **Atestación de estado de Windows** | No aplicable |  
----------------------------


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

- **Require a system integrity protection** (Requerir protección de integridad del sistema): establezca esta opción en **Require** (Requerir) para comprobar si los dispositivos macOS tienen habilitada la protección de integridad del sistema.

### <a name="device-properties"></a>Propiedades del dispositivo

- **Minimum OS version** (Versión mínima de SO): cuando un dispositivo no cumpla el requisito de versión de SO mínima, se notificará como no conforme. Se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario puede elegir actualizar su dispositivo. Después de eso, puede acceder a los recursos de la empresa.

- **Maximum OS version allowed** (Versión máxima de SO máxima permitida): cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.

### <a name="system-security-settings"></a>Configuración de seguridad del sistema

#### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: establezca esta opción en **Requerir** para que los usuarios tengan que escribir una contraseña antes de poder acceder al dispositivo.

- **Simple passwords** (Contraseñas sencillas): establezca esta opción en **Block** (Bloquear) para que los usuarios no puedan crear una contraseña sencilla como **1234** o **1111**.

- **Minimum password length** (Longitud mínima de la contraseña): especifique el número mínimo de dígitos o caracteres que debe tener la contraseña del usuario.

- **Tipo de contraseña**: especifique si el usuario debe crear una contraseña **alfanumérica** o una contraseña **numérica**.

- **Number of non-alphanumeric character in password** (Número de caracteres no alfanuméricos en la contraseña): si establece **Tipo de contraseña obligatoria** en **Alfanumérico**, use esta configuración para especificar el número mínimo de juegos de caracteres que debe tener la contraseña. 

    > [!NOTE]
    > Para establecer un número mayor será necesario que el usuario cree una contraseña más compleja.

    > [!IMPORTANT]
    > En dispositivos macOS, esta configuración hace referencia al número de caracteres especiales (por ejemplo, **!** **#** , **&amp;**) que deben incluirse en la contraseña.

- **Maximum minutes of inactivity before password is required** (Minutos máximos de inactividad antes de que sea necesaria la contraseña): especifique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir su contraseña.

- **Expiración de la contraseña (días)**: seleccione el número de días (entre 1 y 250) que faltan para que la contraseña expire y se deba crear una nueva.

- **Number of previous passwords to prevent reuse** (Número de contraseñas anteriores para impedir que se vuelvan a usar): especifique el número de contraseñas usadas anteriormente que no se pueden volver a usar.

    > [!IMPORTANT]
    > Cuando se cambia el requisito de contraseña en un dispositivo macOS, no entra en vigor hasta la próxima vez que el usuario cambie su contraseña. Por ejemplo, si establece la restricción de longitud de contraseña en ocho dígitos y el dispositivo macOS actualmente tiene una contraseña de 6 dígitos, el dispositivo sigue siendo compatible hasta la próxima vez que el usuario actualice su contraseña en el dispositivo.

## <a name="to-create-a-device-compliance-policy"></a>Pasos para crear una directiva de cumplimiento de dispositivos

1. Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales de Intune.

2. Después de iniciar sesión correctamente, podrá ver el **panel de Azure**.

3. Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.

4. Elija **Intune**, podrá ver el **panel de Intune**.

5. Elija **Cumplimiento de dispositivos** y, luego, elija **Directivas** en **Administrar**.

6. Elija **Crear directiva**.

7. Escriba un nombre y una descripción y elija la plataforma a la que quiere que se aplique esta directiva.

8. La hoja **macOS compliance policy** (Directiva de cumplimiento de macOS), elija las categorías de configuración de cumplimiento de dispositivos **Seguridad**, **Estado del dispositivo** y **Propiedad del dispositivo** para especificar la configuración.

10. Una vez que haya elegido la configuración, seleccione **Aceptar** en cada categoría de configuración de cumplimiento de dispositivos.

11. Elija **Aceptar** y, luego, **Crear**.

## <a name="assign-user-groups"></a>Asignación de grupos de usuarios

Para asignar una directiva de cumplimiento a los usuarios, elija una directiva que haya configurado. Las directivas existentes se pueden encontrar en la hoja **Directivas de cumplimiento**.

1. Elija la directiva de cumplimiento de dispositivos que desea asignar a los usuarios y elija **Asignaciones**. Se abre la hoja donde puede seleccionar **Grupos de seguridad de Azure Active Directory** y asignarlos a la directiva.

2. Elija **Seleccionar grupos** para abrir la hoja que muestra los grupos de seguridad de Azure AD.

3. Elija **Seleccionar** y, luego, **Guardar** para asignar la directiva de cumplimiento de dispositivos a los grupos de seguridad de Azure AD.

4. Una vez que asigne la directiva de cumplimiento de dispositivos a los grupos, puede cerrar la hoja **Asignaciones**.

    > [!TIP]
    > De manera predeterminada, los dispositivos comprueban el cumplimiento cada ocho horas, pero los usuarios pueden forzar este proceso a través de la aplicación Portal de empresa de Intune.

## <a name="next-steps"></a>Pasos siguientes

[Supervisión de las directivas de cumplimiento de dispositivos](compliance-policy-monitor.md)
