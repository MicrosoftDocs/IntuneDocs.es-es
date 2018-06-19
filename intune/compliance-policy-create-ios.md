---
title: Creación de una directiva de cumplimiento de dispositivos iOS en Microsoft Intune - Azure | Microsoft Docs
description: Cree o configure una directiva de cumplimiento de dispositivos Microsoft Intune para dispositivos iOS para especificar una cuenta de correo electrónico, comprobar dispositivos con Jailbreak, comprobar la versión del sistema operativo mínima y máxima, así como establecer las restricciones de contraseñas, incluida la longitud de las contraseñas y la inactividad de los dispositivos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6f711a6bec9be0ac1fd94183931070f9988d49e3
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31442651"
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Agregación de una directiva de cumplimiento para dispositivos iOS en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Las directivas de cumplimiento de dispositivos iOS para Intune determinan las reglas y la configuración que deben cumplir los dispositivos iOS para que sean compatibles. Al usar directivas de cumplimiento de dispositivos con acceso condicional, puede permitir o bloquear el acceso a los recursos de la empresa. También puede obtener informes de dispositivos y realizar acciones en caso de incumplimiento. Las directivas de cumplimiento de dispositivos para cada plataforma se pueden crear en Azure Portal de Intune. Para más información sobre las directivas de cumplimiento, consulte [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).

En la tabla siguiente se describe cómo administrar la configuración de no conformidad cuando se usa una directiva de cumplimiento con una directiva de acceso condicional.

---------------------------

| **Configuración de directiva** | **iOS 8.0 y versiones posteriores** |
| --- | --- |
| **Configuración de PIN o contraseña** | Corregido |
| **Cifrado del dispositivo** | Corregido (estableciendo PIN) |
| **Dispositivo liberado o modificado** | En cuarentena (no es una configuración)
| **Perfil de correo electrónico** | En cuarentena |
|**Versión de SO mínima** | En cuarentena |
| **Versión de SO máxima** | En cuarentena |
| **Atestación de estado de Windows** | No disponible |

---------------------------

**Corregido** = el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena** = el sistema operativo del sistema no exige compatibilidad. (Por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo). Si los dispositivos no son compatibles, se emprenden las acciones siguientes:

- El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
- El portal de empresa notifica al usuario acerca de los problemas de cumplimiento.

## <a name="create-a-device-compliance-policy"></a>Crear una directiva de cumplimiento de dispositivos

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Para **Plataforma**, seleccione **iOS**. Seleccione **Definir configuración** y especifique las opciones **Correo electrónico**, **Estado de dispositivos**, **Propiedades de dispositivo** y **Seguridad del sistema**. Cuando termine, seleccione **Aceptar** y **Crear**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="email"></a>Correo electrónico

- **Requerir que los dispositivos móviles tengan un perfil de correo electrónico administrado**: si establece esta opción en Requerir, los dispositivos que no tengan un perfil de correo electrónico administrado por Intune se considerarán no compatibles. Un dispositivo puede no tener un perfil de correo electrónico administrado cuando no tenga definido correctamente el destino, o si el usuario configura manualmente la cuenta de correo electrónico en el dispositivo.

  El dispositivo se considera no conforme en las situaciones siguientes:
  - El perfil de correo electrónico se implementa en un grupo de usuarios distinto del grupo de usuarios al que se dirige la directiva de cumplimiento.
  - El usuario ya tiene configurada una cuenta de correo electrónico en el dispositivo que coincide con el perfil de correo electrónico de Intune implementado en dicho dispositivo. Intune no puede sobrescribir el perfil implementado por el usuario y, por tanto, no puede administrarlo. Para garantizar el cumplimiento, el usuario debe quitar la configuración de correo electrónico existente. De este modo, Intune puede instalar el perfil de correo electrónico administrado.

- **Seleccione el perfil de correo electrónico que Intune debe administrar**: si se selecciona la opción **Intune debe administrar la cuenta de correo electrónico**, elija **Seleccionar** para especificar el perfil de correo electrónico de Intune. El perfil de correo electrónico debe estar presente en el dispositivo.

Para más información sobre los perfiles de correo electrónico, consulte [Configurar el acceso al correo electrónico corporativo mediante perfiles de correo electrónico con Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health"></a>Device health

- **Dispositivos con Jailbreak**: si habilita esta configuración, los dispositivos con Jailbreak no serán compatibles.
- **Requerir que el dispositivo tenga el nivel de amenaza del dispositivo** (iOS 8.0 y posterior): elija el nivel de amenaza máximo para marcar los dispositivos como no compatibles. Los dispositivos que superan este nivel de amenaza se marcan como no compatibles:
  - **Protegido**: esta opción es la más segura y el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.
  - **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  - **Medio:** el dispositivo se evalúa como compatible si las amenazas existentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
  - **Alto**: esta opción es la menos segura, ya que permite que todos los niveles de amenaza. Quizás sea útil si utiliza esta solución solo con fines informativos.

## <a name="device-properties"></a>Propiedades del dispositivo

- **SO mínimo requerido:** cuando un dispositivo no cumpla el requisito de versión de SO mínima, se notificará como no compatible. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario puede elegir actualizar su dispositivo. Después de eso, puede acceder a los recursos de la empresa.
- **Maximum OS version allowed** (Versión de SO máxima permitida): cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá obtener acceso a los recursos de la empresa.

## <a name="system-security"></a>Seguridad del sistema

### <a name="password"></a>Contraseña

> [!NOTE]
> Después de poner en marcha una directiva de configuración o cumplimiento en un dispositivo iOS, cada 15 minutos se pedirá al usuario que establezca un código de acceso y se le seguirá pidiendo hasta que se establezca un código de acceso.

- **Requerir una contraseña para desbloquear dispositivos móviles**: **requiere** que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos. Los dispositivos iOS que usan una contraseña están cifrados.
- **Contraseñas sencillas**: establezca esta opción en **Bloquear** para que los usuarios no puedan crear contraseñas sencillas como **1234** o **1111**. Establézcala en **No configurado** para permitir a los usuarios crear contraseñas como **1234** o **1111**.
- **Longitud mínima de la contraseña**: indique el número mínimo de dígitos o caracteres que debe tener la contraseña.
- **Tipo de contraseña requerida**: elija si una contraseña debe tener solo caracteres **numéricos** o si es necesario combinar números y otros caracteres (**alfanuméricos**).
- **Number of non-alphanumeric characters in password** (Número de caracteres no alfanuméricos de la contraseña): indique el número mínimo de caracteres especiales (&, #, %, !, etc.) que se deben incluir en la contraseña.

    Para establecer un número mayor, es necesario que el usuario cree una contraseña más compleja.

- **Máximo de minutos de inactividad antes de solicitar la contraseña**: indique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir la contraseña.
- **Expiración de la contraseña (días)**: seleccione el número de días que faltan para que la contraseña expire y se deba crear una nueva.
- **Número de contraseñas anteriores que no se pueden reutilizar**: indique el número de contraseñas usadas anteriormente que no se pueden usar.

## <a name="assign-user-groups"></a>Asignación de grupos de usuarios

1. Elija una directiva que haya configurado. Las directivas existentes están en **Conformidad de dispositivos** > **Directivas**.
2. Elija la directiva y luego **Asignaciones**. Puede incluir o excluir grupos de seguridad de Azure Active Directory (AD).
3. Elija **Grupos seleccionados** para ver los grupos de seguridad de Azure AD. Seleccione los grupos de usuarios a los que quiera aplicar esta directiva y elija **Guardar** para implementar la directiva a los usuarios.

Ya ha aplicado la directiva a los usuarios. Se evalúa el cumplimiento por parte de los dispositivos usados por los usuarios a los que se aplique la directiva.

## <a name="next-steps"></a>Pasos siguientes
[Automatización del correo electrónico y adición de acciones para dispositivos no compatibles](actions-for-noncompliance.md)  
[Supervisión de las directivas de cumplimiento de dispositivos de Intune](compliance-policy-monitor.md)