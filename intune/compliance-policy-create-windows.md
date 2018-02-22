---
title: "Creación de una directiva de cumplimiento para Windows"
titleSuffix: Azure portal
description: Aprenda a crear una directiva de cumplimiento para dispositivos Windows.
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 1/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 05fb016277f8645c661bc8dee213ed98b95c0198
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-windows-devices-in-intune"></a>Creación de una directiva de cumplimiento de dispositivos para dispositivos Windows en Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Las directivas de cumplimiento se crean para cada plataforma. Puede crear una directiva de cumplimiento en el portal de Azure. Para aprender más sobre lo que son las directivas de cumplimiento, consulte el tema [¿Qué es el cumplimiento de los dispositivos?](device-compliance.md). Para conocer los requisitos previos que deben satisfacerse antes de crear una directiva de cumplimiento, consulte el tema [Introducción al cumplimiento de dispositivos](device-compliance-get-started.md).

En la tabla siguiente se describe cómo administrar la configuración de no conformidad cuando se usa una directiva de cumplimiento con una directiva de acceso condicional.

---------------------------

| **Configuración de directiva** | **Windows 8.1 y versiones posteriores** | **Windows Phone 8.1 y versiones posteriores** |
|----| ----| --- |
| **Configuración de PIN o contraseña** | Corregido | Corregido |   
| **Cifrado del dispositivo** | No aplicable | Corregido |   
| **Dispositivo liberado o modificado** | No disponible | No disponible |  
| **Perfil de correo electrónico** | No disponible | No disponible |   
| **Versión de SO mínima** | En cuarentena | En cuarentena |   
| **Versión de SO máxima** | En cuarentena | En cuarentena |   
| **Atestación de estado de Windows** | Windows 10 y Windows 10 Mobile están en cuarentena|No aplicable: Windows 8.1 |

-------------------------------

**Corregido** = el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena** = el sistema operativo del sistema no exige compatibilidad. (Por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo). Si los dispositivos no son compatibles, se emprenden las acciones siguientes:

- El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
- El portal de empresa notifica al usuario acerca de los problemas de cumplimiento.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Creación de una directiva de cumplimiento en el portal de Azure

1. En la hoja **Intune**, elija **Establecer la compatibilidad con dispositivos**. En **Administrar**, elija **All device compliance policies** (Todas las directivas de cumplimiento de dispositivo) y elija **Crear**.
2. Escriba un nombre y una descripción y elija la plataforma a la que quiere que se aplique esta directiva.
3. Elija **Requisitos de cumplimiento** para abrir la hoja de requisitos de cumplimiento.  Puede especificar aquí los valores de configuración de **Seguridad**, **Mantenimiento de dispositivos** y **Propiedad del dispositivo**. Cuando haya terminado, elija **Aceptar**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Asignación de grupos de usuarios

Para asignar una directiva de cumplimiento a los usuarios, elija una directiva que haya configurado. Las directivas existentes se pueden encontrar en la hoja **Directivas de cumplimiento normativo**.

1. Seleccione la directiva que quiere asignar a los usuarios y elija **Asignaciones**. Se abre la hoja donde puede seleccionar **Grupos de seguridad de Azure Active Directory** y asignarlos a la directiva.
2. Elija **Seleccionar grupos** para abrir la hoja que muestra los grupos de seguridad de Azure AD.  Al elegir **Seleccionar** la directiva se implementa para los usuarios.

Ya ha aplicado la directiva a los usuarios. Ahora se evaluará el cumplimiento de los dispositivos usados por los usuarios a los que se aplique la directiva.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles:** establezca esta opción en **Sí** para exigir que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos.
- **Permitir contraseñas sencillas:** establezca esta opción en **Sí** para permitir a los usuarios crear contraseñas sencillas como "**1234**"; o "**1111**".
- **Minimum password length** (Longitud mínima de la contraseña): especifique el número mínimo de dígitos o caracteres que debe contener la contraseña del usuario.
- **Tipo de contraseña obligatoria:** Especifique si los usuarios deben crear una contraseña **Alfanumérica** o **Numérica**.

En los dispositivos a los que se obtiene acceso con una cuenta de Microsoft y que ejecutan Windows, la directiva de cumplimiento no puede evaluarse correctamente si la longitud mínima de la contraseña es superior a 8 caracteres o si el número mínimo de conjuntos de caracteres es superior a 2.

- **Número mínimo de conjuntos de caracteres**: si la opción **Tipo de contraseña necesaria** está establecida en **Alfanumérica**, esta configuración especifica el número mínimo de caracteres que debe contener la contraseña. Los conjuntos de cuatro caracteres son los siguientes:
  - Letras minúsculas
  - Letras mayúsculas
  - Símbolos
  - Números

Si se establece un número superior para este valor de configuración, los usuarios deberán crear contraseñas más complejas. En los dispositivos a los que se obtiene acceso con una cuenta de Microsoft y que ejecutan Windows, la directiva de cumplimiento no puede evaluarse correctamente si la longitud mínima de la contraseña es superior a 8 caracteres o si el número mínimo de conjuntos de caracteres es superior a 2.

- **Minutos de inactividad antes de que sea necesaria la contraseña**: especifica el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir su contraseña.
- **Caducidad de contraseña (días)**: seleccione el número de días que faltan para que la contraseña expire y se deba crear una nueva.
- **Recordar historial de contraseñas:** use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para impedir que el usuario cree contraseñas que se han usado anteriormente.
- **Impedir la reutilización de contraseñas anteriores:** si la opción **Recordar historial de contraseñas** está seleccionada, especifique el número de contraseñas usadas previamente que no se pueden volver a usar.
- **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad:** este valor debe usarse junto con el de la opción **Minutos de inactividad antes de que sea necesaria la contraseña**. Se pedirá a los usuarios que escriban una contraseña para acceder a un dispositivo que haya estado inactivo durante el tiempo especificado en la opción **Minutos de inactividad antes de que sea necesaria la contraseña**.

**Esta configuración solo se aplica a dispositivos Windows 10 Mobile.**

### <a name="encryption"></a>Cifrado

- **Requerir cifrado en el dispositivo móvil:** establezca esta opción en **Sí** para requerir que el dispositivo esté cifrado para poder conectarse a los recursos.



## <a name="device-health-settings"></a>Configuración de estado del dispositivo

- **Requerir que se informe del mantenimiento correcto de los dispositivos:** puede establecer una regla para requerir que se informe del mantenimiento correcto de los dispositivos con **Windows 10 Mobile** en las directivas de cumplimiento nuevas o existentes. Si se habilita esta opción de configuración, se evaluarán los puntos de datos siguientes de los dispositivos Windows 10 a través del servicio de atestación de mantenimiento (HAS):
  - **BitLocker is enabled** (BitLocker está habilitado): cuando Bitlocker está activado, el dispositivo puede proteger los datos almacenados en la unidad del acceso no autorizado cuando el sistema está apagado o entra en estado de hibernación. La característica Cifrado de unidad BitLocker de Windows cifra todos los datos almacenados en el volumen del sistema operativo Windows. BitLocker usa TPM para ayudar a proteger el sistema operativo Windows y los datos de usuario, y contribuye a evitar la manipulación de un equipo, incluso si se deja desatendido, se pierde o lo roban. Si el equipo incluye un TPM compatible, BitLocker lo usa para bloquear las claves de cifrado que protegen los datos. Como resultado, las claves no son accesibles hasta que TPM termina la comprobación del estado del equipo.
  - **Code integrity is enabled** (La integridad de código está habilitada): la integridad de código es una característica que valida la integridad de un archivo del sistema o controlador cada vez que se carga en la memoria. Integridad de código detecta si se está cargando un archivo del sistema o controlador sin firmar en el kernel, o si software malintencionado que se ejecuta mediante una cuenta de usuario con privilegios de administrador ha modificado un archivo del sistema.
  - **Secure Boot is enabled** (El arranque seguro está habilitado): si el arranque seguro está habilitado, el sistema debe arrancar en un estado de confianza de fábrica. Además, si el arranque seguro está habilitado, los componentes principales que se usan para arrancar el equipo deben tener las firmas de cifrado correctas que son de confianza para la organización que fabricó el dispositivo. El firmware UEFI lo comprueba antes de permitir iniciar el equipo. Si los archivos se han manipulado e interrumpido su firma, el sistema no arrancará.

Para obtener información sobre cómo funciona el servicio HAS, consulte [HealthAttestation CSP](https://msdn.microsoft.com/library/dn934876.aspx).

## <a name="device-property-settings"></a>Configuración de propiedades de dispositivo

- **SO mínimo requerido:** cuando un dispositivo no cumpla el requisito de versión de SO mínima, se notificará como no compatible. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo, tras lo cual podrá tener acceso a los recursos de la empresa.
- **Versión de SO máxima permitida:** cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.

<!---## Compliance policy settings for Windows PCs--->

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Longitud mínima de la contraseña:** se admite en Windows 8.1.

Especifique el número mínimo de dígitos o caracteres que debe contener la contraseña del usuario.

En los dispositivos a los que se obtiene acceso con una cuenta de Microsoft, la directiva de cumplimiento no puede evaluarse correctamente si el valor de **Longitud mínima de la contraseña** es superior a ocho caracteres o el de **Número mínimo de conjuntos de caracteres** es superior a dos.

- **Tipo de contraseña necesaria**: se admite en Windows RT, Windows RT 8.1 y Windows 8.1.

Especifique si los usuarios deben crear una contraseña **Alfanumérica** o **Numérica**.

- **Número mínimo de conjuntos de caracteres:**: se admite en Windows RT, Windows RT 8.1 y Windows 8.1. Si la opción **Tipo de contraseña requerida** está establecida en **Alfanumérica**, esta configuración especifica el número mínimo de caracteres que debe contener la contraseña. Los conjuntos de cuatro caracteres son los siguientes:
  - Letras minúsculas
  - Letras mayúsculas
  - Símbolos
  - Números: si se establece un número superior para este valor de configuración, los usuarios deberán crear contraseñas más complejas.

En los dispositivos a los que se obtiene acceso con una cuenta de Microsoft, la directiva de cumplimiento no puede evaluarse correctamente si el valor de **Longitud mínima de la contraseña** es superior a ocho caracteres o el de **Número mínimo de conjuntos de caracteres** es superior a dos.

- **Minutos de inactividad antes de que sea necesaria la contraseña:** se admite en Windows RT, Windows RT 8.1 y Windows 8.1.

Especifique el tiempo de inactividad antes de que el usuario deba volver a escribir la contraseña.

- **Expiración de la contraseña (días)**: se admite en Windows RT, Windows RT 8.1 y Windows 8.1.

Seleccione el número de días que faltan para que la contraseña expire y sea necesario crear una nueva.

- **Recordar historial de contraseñas:** se admite en Windows RT, Windows RT 8.1 y Windows 8.1.

Use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para impedir que el usuario cree contraseñas que se han usado anteriormente.

- **Impedir la reutilización de contraseñas anteriores:** se admite en Windows RT, Windows RT 8.1 y Windows 8.1.

Si la opción **Recordar historial de contraseñas** está seleccionada, especifique el número de contraseñas usadas previamente que no se pueden volver a usar.


## <a name="device-health-settings"></a>Configuración de estado del dispositivo

- **Requerir que se informe del mantenimiento correcto de los dispositivos:** se admite en dispositivos Windows 10. Puede establecer una regla para requerir que se informe del mantenimiento correcto de los dispositivos con Windows 10 en las directivas de cumplimiento nuevas o existentes. Si se habilita esta opción de configuración, se evaluarán los puntos de datos siguientes de los dispositivos Windows 10 a través del servicio de atestación de mantenimiento (HAS):
  - **BitLocker is enabled** (BitLocker está habilitado): cuando Bitlocker está activado, el dispositivo puede proteger los datos almacenados en la unidad del acceso no autorizado cuando el sistema está apagado o entra en estado de hibernación. La característica Cifrado de unidad BitLocker de Windows cifra todos los datos almacenados en el volumen del sistema operativo Windows. BitLocker usa TPM para ayudar a proteger el sistema operativo Windows y los datos de usuario, y contribuye a evitar la manipulación de un equipo, incluso si se deja desatendido, se pierde o lo roban. Si el equipo incluye un TPM compatible, BitLocker lo usa para bloquear las claves de cifrado que protegen los datos. Como resultado, las claves no son accesibles hasta que TPM termina la comprobación del estado del equipo.
  - **Code integrity is enabled** (La integridad de código está habilitada): la integridad de código es una característica que valida la integridad de un archivo del sistema o controlador cada vez que se carga en la memoria. Integridad de código detecta si se está cargando un archivo del sistema o controlador sin firmar en el kernel, o si software malintencionado que se ejecuta mediante una cuenta de usuario con privilegios de administrador ha modificado un archivo del sistema.
  - **Secure Boot is enabled** (El arranque seguro está habilitado): si el arranque seguro está habilitado, el sistema debe arrancar en un estado de confianza de fábrica. Además, si el arranque seguro está habilitado, los componentes principales que se usan para arrancar el equipo deben tener las firmas de cifrado correctas que son de confianza para la organización que fabricó el dispositivo. El firmware UEFI lo comprueba antes de permitir iniciar el equipo. Si los archivos se han manipulado e interrumpido su firma, el sistema no arrancará.
  - **Early-launch antimalware is enabled** (El antimalware de inicio temprano está habilitado): el antimalware de inicio temprano (ELAM) proporciona protección para los equipos de la red cuando se inician y antes de que se inicialicen los controladores de terceros.

Para obtener información sobre cómo funciona el servicio HAS, consulte [HealthAttestation CSP](https://msdn.microsoft.com/library/dn934876.aspx).

## <a name="device-property-settings"></a>Configuración de propiedades de dispositivo

- **Minimum OS required:** (Versión mínima de sistema operativo): se admite en Windows 8.1 y Windows 10.

Especifique aquí el número de major.minor.build. El número de versión debe coincidir con la versión devuelta por el comando ```winver```.

Cuando un dispositivo tiene una versión anterior a la versión de sistema operativo especificada, se notifica como no conforme. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo, tras lo cual podrá tener acceso a los recursos de la empresa.

- **Maximum OS version allowed** (Versión máxima de sistema operativo permitida): se admite en Windows 8.1 y Windows 10.

Cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.

Para buscar la versión de sistema operativo que se usará para las opciones **Minimum OS required** (Versión mínima de sistema operativo) y **Maximum OS version allowed** (Versión máxima de sistema operativo permitida), ejecute el comando **winver** desde el símbolo del sistema. El comando winver devuelve la versión de sistema operativo notificada.

- Los equipos con Windows 8.1 devuelven la versión **3**. Si la regla de la versión de sistema operativo se establece en Windows 8.1 para Windows, el dispositivo se notificará como no conforme aunque tenga Windows 8.1.
- En los equipos que ejecutan Windows 10, la versión debe establecerse en &quot;10.0&quot;+ el número de compilación del sistema operativo devuelto por el comando winver.

## <a name="windows-holographic-for-business-support"></a>Compatibilidad con Windows Holographic for Business

Windows Holographic for Business es compatible con las siguientes opciones de configuración:

- Cifrado/seguridad del sistema

  **Cifrado de los datos almacenados en el dispositivo**.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
