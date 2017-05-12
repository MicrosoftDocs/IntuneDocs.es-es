---
title: "Creación de una directiva de cumplimiento para iOS"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a crear una directiva de cumplimiento para dispositivos iOS."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 6fb4b81e11ae8c66341922898d9ecc4cce3a002d
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017


---

# <a name="how-to-create-a-device-compliance-policy-for-ios-devices-in-intune-azure-preview"></a>Creación de una directiva de cumplimiento de dispositivos para dispositivos iOS en la versión preliminar de Intune Azure


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Las directivas de cumplimiento se crean para cada plataforma.  Puede crear una directiva de cumplimiento en el portal de Azure. Para aprender más sobre lo que son las directivas de cumplimiento, consulte el tema [¿Qué es el cumplimiento de los dispositivos?](what-is-device-compliance.md). Para conocer los requisitos previos que deben satisfacerse antes de crear una directiva de cumplimiento, consulte el tema [Introducción al cumplimiento de dispositivos](get-started-with-device-compliance.md).

En la tabla siguiente se describe cómo administrar la configuración de no conformidad cuando se usa una directiva de cumplimiento con una directiva de acceso condicional.

-------------------------------


| **Configuración de directiva** | **iOS 8.0 y versiones posteriores** |
| --- | --- |
| **Configuración de PIN o contraseña** | Corregido |   
| **Cifrado del dispositivo** | Corregido (estableciendo PIN) |
| **Dispositivo liberado o modificado** | En cuarentena (no es una configuración)
| **Perfil de correo electrónico** | En cuarentena |
|**Versión de SO mínima** | En cuarentena |
| **Versión de SO máxima** | En cuarentena |  
| **Atestación de estado de Windows** | No aplicable |  
----------------------------


**Corregido** = el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena** = el sistema operativo del sistema no exige compatibilidad. (Por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo). Si los dispositivos no son compatibles, se emprenden las acciones siguientes:

- El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
- El portal de empresa notifica al usuario acerca de los problemas de cumplimiento.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Creación de una directiva de cumplimiento en el portal de Azure

1. En la hoja **Intune**, elija **Establecer la compatibilidad con dispositivos**. En **Administrar**, elija **All device compliance policies** (Todas las directivas de cumplimiento de dispositivo) y elija **Crear**.
2. Escriba un nombre y una descripción y elija la plataforma a la que quiere que se aplique esta directiva.
3. Elija **Requisitos de cumplimiento** para especificar los valores de **Seguridad**, **Mantenimiento de dispositivos** y **Propiedad del dispositivo**. Cuando haya terminado, elija **Aceptar**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Asignación de grupos de usuarios

Para asignar una directiva de cumplimiento a los usuarios, elija una directiva que haya configurado. Las directivas existentes se pueden encontrar en la hoja **Directivas de cumplimiento normativo**.

1. Seleccione la directiva que quiere asignar a los usuarios y elija **Asignaciones**. Se abre la hoja donde puede seleccionar **Grupos de seguridad de Azure Active Directory** y asignarlos a la directiva.
2. Elija **Seleccionar grupos** para abrir la hoja que muestra los grupos de seguridad de Azure AD.  Al elegir **Seleccionar** la directiva se implementa para los usuarios.

Ya ha aplicado la directiva a los usuarios.  Ahora se evaluará el cumplimiento de los dispositivos usados por los usuarios a los que se aplique la directiva.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: establezca esta opción en **Sí** para exigir que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos. Los dispositivos iOS que usan una contraseña están cifrados.
- **Permitir contraseñas sencillas**: establezca esta opción en **Sí** para permitir al usuario crear una contraseña sencilla como **1234** o **1111**.
- **Minimum password length** (Longitud mínima de la contraseña): especifique el número mínimo de dígitos o caracteres que debe tener la contraseña del usuario.
- **Tipo de contraseña necesaria:** especifique si el usuario debe crear una contraseña **Alfanumérica** o **Numérica**.
- **Número mínimo de conjuntos de caracteres:** si establece la opción **Tipo de contraseña necesaria** en **Alfanumérica**, use esta configuración para especificar el número mínimo de conjuntos de caracteres que debe contener la contraseña. Los conjuntos de cuatro caracteres son los siguientes:
  - Letras minúsculas
  - Letras mayúsculas
  - Símbolos
  - Números

Para establecer un número mayor será necesario que el usuario cree una contraseña más compleja.

En dispositivos iOS, esta configuración hace referencia al número de caracteres especiales (por ejemplo, **!** **#** , **&amp;**) que deben incluirse en la contraseña.

- **Minutos de inactividad antes de que sea necesaria la contraseña**: especifique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir su contraseña.
- **Caducidad de contraseña (días)**: seleccione el número de días que faltan para que la contraseña expire y se deba crear una nueva.
- **Recordar historial de contraseñas:** use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para impedir que el usuario cree contraseñas que se hayan usado anteriormente.
- **Impedir la reutilización de contraseñas anteriores**: si ha seleccionado **Recordar historial de contraseñas**, especifique el número de contraseñas que se han usado anteriormente que no se pueden volver a usar.
- **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad**: use este valor junto con el de la opción **Minutos de inactividad antes de que sea necesaria la contraseña**. Se pedirá al usuario que escriba una contraseña para obtener acceso a un dispositivo que haya estado inactivo durante el tiempo especificado en la opción **Minutos de inactividad antes de que sea necesaria la contraseña**.

### <a name="email-profile"></a>Perfil de correo electrónico

- **Intune debe administrar la cuenta de correo electrónico**: cuando esta opción se establece en **Sí**, el dispositivo debe usar el perfil de correo electrónico que tenga implementado. El dispositivo se considera no conforme en las situaciones siguientes:
  - El perfil de correo electrónico se implementa en un grupo de usuarios distinto del grupo de usuarios al que se dirige la directiva de cumplimiento.
  - El usuario ya tiene configurada una cuenta de correo electrónico en el dispositivo que coincide con el perfil de correo electrónico de Intune implementado en dicho dispositivo. Intune no puede sobrescribir el perfil implementado por el usuario y, por tanto, no puede administrarlo. Para garantizar el cumplimiento, el usuario debe quitar la configuración de correo electrónico existente. De este modo, Intune puede instalar el perfil de correo electrónico administrado.
- **Seleccione el perfil de correo electrónico que Intune debe administrar**: si se selecciona la opción **Intune debe administrar la cuenta de correo electrónico**, elija **Seleccionar** para especificar el perfil de correo electrónico de Intune. El perfil de correo electrónico debe estar presente en el dispositivo.

Para más información sobre los perfiles de correo electrónico, consulte [Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health-settings"></a>Configuración de estado del dispositivo

- **El dispositivo no debe estar modificado por los métodos de acceso jailbreak o root**: si habilita esta opción, los dispositivos descodificados no serán compatibles.

## <a name="device-properties"></a>Propiedades del dispositivo

- **Minimum OS required** (SO mínimo necesario): cuando un dispositivo no cumpla el requisito de versión de SO mínima, se notificará como no conforme. Se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario puede elegir actualizar su dispositivo. Después de eso, puede acceder a los recursos de la empresa.
- **Maximum OS version allowed** (Versión de SO máxima permitida): cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.

<!--- ## Next steps

[How to monitor device compliance](monitor-device-compliance.md)--->

