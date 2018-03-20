---
title: "Creación de una directiva de cumplimiento de dispositivos iOS en Microsoft Intune"
titleSuffix: 
description: Cree una directiva de cumplimiento de dispositivos de Microsoft Intune para dispositivos iOS para poder especificar los requisitos que debe cumplir un dispositivo para que sea compatible.
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b024c846f9fc79fe214e3e90b094384455f2b086
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-ios-devices-in-intune"></a>Creación de una directiva de cumplimiento para dispositivos iOS en Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Una directiva de cumplimiento de dispositivos de Intune para iOS especifica las reglas y la configuración que los dispositivos iOS deben cumplir para que se consideren compatibles. Al usar directivas de cumplimiento de dispositivos con acceso condicional, puede permitir o bloquear el acceso a los recursos de la empresa. También puede obtener informes de dispositivos y realizar acciones en caso de incumplimiento. Las directivas de cumplimiento de dispositivos para cada plataforma se pueden crear en Azure Portal de Intune. Para obtener más información sobre las directivas de cumplimiento y los requisitos previos que deben satisfacerse antes de crear una directiva de cumplimiento, consulte el tema [Introducción a las directivas de cumplimiento de dispositivos](device-compliance-get-started.md).

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
| **Atestación de estado de Windows** | No disponible |  
----------------------------


**Corregido** = el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena** = el sistema operativo del sistema no exige compatibilidad. (Por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo). Si los dispositivos no son compatibles, se emprenden las acciones siguientes:

- El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
- El portal de empresa notifica al usuario acerca de los problemas de cumplimiento.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Creación de una directiva de cumplimiento en el portal de Azure

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
1. En el panel **Intune**, elija **Cumplimiento del dispositivo**. En **Administrar**, elija **Directivas** y después **Crear directiva**.
2. Escriba un nombre y una descripción y elija la plataforma a la que quiere que se aplique esta directiva.
3. Elija **Requisitos de cumplimiento** para especificar los valores de **Seguridad del sistema**, **Mantenimiento de dispositivos** y **Propiedades del dispositivo**. Cuando haya terminado, elija **Aceptar**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Asignación de grupos de usuarios

Para asignar una directiva de cumplimiento a los usuarios, elija una directiva que haya configurado. Las directivas existentes se pueden encontrar en el panel **Conformidad del dispositivo: directivas**.

1. Seleccione la directiva que quiere asignar a los usuarios y elija **Asignaciones**. Se abre un panel donde puede seleccionar **grupos de seguridad de Azure Active Directory** y asignarlos a la directiva.
2. Elija **Grupos seleccionados** para abrir el panel en el que se muestran los grupos de seguridad de Azure AD.  Al elegir **Guardar** la directiva se implementa para los usuarios.

Ya ha aplicado la directiva a los usuarios.  Se evalúa el cumplimiento por parte de los dispositivos usados por los usuarios a los que se aplique la directiva.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles:** establezca esta opción en **Sí** para exigir que los usuarios escriban una contraseña para poder tener acceso a sus dispositivos. Los dispositivos iOS que usan una contraseña están cifrados.
- **Permitir contraseñas sencillas**: establezca esta opción en **Sí** para permitir al usuario crear una contraseña como **1234** o **1111**.
- **Longitud mínima de la contraseña**: especifique el número mínimo de dígitos o caracteres que debe tener la contraseña.
- **Tipo de contraseña obligatoria:** especifique si el usuario debe crear una contraseña **Alfanumérica** o **Numérica**.
- **Número mínimo de conjuntos de caracteres:** si establece la opción **Tipo de contraseña requerida** en **Alfanumérica**, use esta configuración para especificar el número mínimo de conjuntos de caracteres que debe contener la contraseña. Los conjuntos de cuatro caracteres son los siguientes:
  - Letras minúsculas
  - Letras mayúsculas
  - Símbolos
  - Números

Para establecer un número mayor, es necesario que el usuario cree una contraseña más compleja.

En dispositivos iOS, esta configuración hace referencia al número de caracteres especiales (por ejemplo, **!** **#** , **&amp;**) que deben incluirse en la contraseña.

- **Minutos de inactividad antes de que sea necesaria la contraseña**: especifique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir su contraseña.
- **Caducidad de contraseña (días)**: seleccione el número de días que faltan para que la contraseña expire y se deba crear una nueva.
- **Recordar historial de contraseñas:** use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para impedir que el usuario cree contraseñas que se han usado anteriormente.
- **Impedir la reutilización de contraseñas anteriores**: si ha seleccionado **Recordar historial de contraseñas**, especifique el número de contraseñas que se han usado previamente que no se pueden volver a usar.
- **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad**: use este valor junto con el de la opción **Minutos de inactividad antes de que sea necesaria la contraseña**. Se pedirá al usuario que escriba una contraseña para obtener acceso a un dispositivo que haya estado inactivo durante el tiempo especificado en la opción **Minutos de inactividad antes de que sea necesaria la contraseña**.

### <a name="email-profile"></a>Perfil de correo electrónico

- **Intune debe administrar la cuenta de correo electrónico:** cuando esta opción se establece en **Sí**, el dispositivo debe utilizar el perfil de correo electrónico que tenga implementado. El dispositivo se considera no conforme en las situaciones siguientes:
  - El perfil de correo electrónico se implementa en un grupo de usuarios distinto del grupo de usuarios al que se dirige la directiva de cumplimiento.
  - El usuario ya tiene configurada una cuenta de correo electrónico en el dispositivo que coincide con el perfil de correo electrónico de Intune implementado en dicho dispositivo. Intune no puede sobrescribir el perfil implementado por el usuario y, por tanto, no puede administrarlo. Para garantizar el cumplimiento, el usuario debe quitar la configuración de correo electrónico existente. De este modo, Intune puede instalar el perfil de correo electrónico administrado.
- **Seleccione el perfil de correo electrónico que Intune debe administrar**: si se selecciona la opción **Intune debe administrar la cuenta de correo electrónico**, elija **Seleccionar** para especificar el perfil de correo electrónico de Intune. El perfil de correo electrónico debe estar presente en el dispositivo.

Para más información sobre los perfiles de correo electrónico, consulte [Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico con Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health-settings"></a>Configuración de estado del dispositivo

- **El dispositivo no debe estar modificado por los métodos de acceso jailbreak o root:** si habilita esta opción, los dispositivos descodificados no serán compatibles.

## <a name="device-properties"></a>Propiedades del dispositivo

- **SO mínimo requerido:** cuando un dispositivo no cumpla el requisito de versión de SO mínima, se notificará como no compatible. Se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario puede elegir actualizar su dispositivo. Después de eso, puede acceder a los recursos de la empresa.
- **Versión de SO máxima permitida**: cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
