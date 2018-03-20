---
title: "Creación de una directiva de cumplimiento de Android for Work"
titleSuffix: Microsoft Intune
description: Cree una directiva de cumplimiento de dispositivos de Intune para dispositivos Android for Work para poder especificar los requisitos que debe cumplir un dispositivo para que sea compatible.
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8ca31d4c83ccc6b786933080b96f66953cf1a108
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Creación de una directiva de cumplimiento para dispositivos Android for Work en Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Una directiva de cumplimiento de dispositivos de Intune para Android for Work especifica las reglas y la configuración que los dispositivos Android for Work deben cumplir para que se consideren compatibles. Estas directivas se pueden usar con el acceso condicional para permitir o bloquear el acceso a recursos de la empresa, y se pueden obtener informes de dispositivos y realizar acciones en caso de incumplimiento. Las directivas de cumplimiento de dispositivos para cada plataforma se crean en Azure Portal de Intune. Para obtener más información sobre las directivas de cumplimiento y los requisitos previos que deben satisfacerse antes de crear una directiva de cumplimiento, consulte [Introducción a las directivas de cumplimiento de dispositivos](device-compliance-get-started.md).

En la tabla siguiente se describe cómo administrar la configuración de no conformidad cuando se usa una directiva de cumplimiento con una directiva de acceso condicional.

--------------------------

|**Configuración de directiva**| **Android for Work** |
| --- | --- |
| **Configuración de PIN o contraseña** |  En cuarentena |
| **Cifrado del dispositivo** |  En cuarentena |
| **Dispositivo liberado o modificado** | En cuarentena (no es una configuración) |
| **Perfil de correo electrónico** | No disponible |
| **Versión de SO mínima** | En cuarentena |
| **Versión de SO máxima** | En cuarentena |
| **Atestación de estado de Windows** |No disponible |

**Corregido** = el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena** = el sistema operativo del sistema no exige compatibilidad. (Por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo). Si los dispositivos no son compatibles, se emprenden las acciones siguientes:

- El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
- El portal de empresa notifica al usuario acerca de los problemas de cumplimiento.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Creación de una directiva de cumplimiento en el portal de Azure

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
1. En el panel **Intune**, elija **Cumplimiento del dispositivo**. En **Administrar**, elija **Directivas** y después **Crear directiva**.
2. Escriba un nombre y una descripción y elija la plataforma a la que quiere que se aplique esta directiva.
3. Elija **Configuración de valores** para especificar aquí las opciones de **Seguridad del sistema**, **Estado de dispositivos** y **Propiedades del dispositivo**. Cuando termine, elija **Aceptar**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Asignación de grupos de usuarios

Para asignar una directiva de cumplimiento a los usuarios, elija una directiva que haya configurado. Las directivas existentes se pueden encontrar en el panel **Conformidad del dispositivo: directivas**.

1. Seleccione la directiva que quiere asignar a los usuarios y elija **Asignaciones**. Se abre el panel donde puede seleccionar **grupos de seguridad de Azure Active Directory** y asignarlos a la directiva.
2. Elija **Grupos seleccionados** para abrir el panel en el que se muestran los grupos de seguridad de Azure AD.  Al elegir **Guardar** la directiva se implementa para los usuarios.

Ya ha aplicado la directiva a los usuarios.  Ahora se evaluará el cumplimiento de los dispositivos usados por los usuarios a los que se aplique la directiva.

<!--- ##  Compliance policy settings--->

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: establezca esta opción en **Sí** para exigir que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos.
- **Longitud mínima de la contraseña**: especifique el número mínimo de dígitos o caracteres que debe contener la contraseña del usuario.
- **Calidad de contraseña**: esta opción detecta si los requisitos de contraseña que especifique están configurados en el dispositivo. Habilite esta opción para requerir a los usuarios configurar determinados requisitos de contraseña para dispositivos Android. Elija de entre las siguientes opciones:
  - **Biométrico de seguridad baja**
  - **Requerido**
  - **Al menos numérica**
  - **Al menos alfabética**
  - **Al menos alfanumérica**
  - **Alfanumérica con símbolos**
- **Minutos de inactividad antes de que sea necesaria la contraseña**: especifica el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir su contraseña.
- **Caducidad de contraseña (días)**: seleccione el número de días que faltan para que la contraseña expire y se deba crear una nueva.
- **Recordar historial de contraseñas:** use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para impedir que el usuario cree contraseñas que se han usado anteriormente.
- **Impedir la reutilización de contraseñas anteriores:** si la opción **Recordar historial de contraseñas** está seleccionada, especifique el número de contraseñas usadas previamente que no se pueden volver a usar.
- **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad:** este valor debe usarse con el de la opción **Minutos de inactividad antes de que sea necesaria la contraseña**. Se pedirá a los usuarios finales que escriban una contraseña para obtener acceso a un dispositivo que haya estado inactivo durante el tiempo especificado en la opción **Minutos de inactividad antes de que sea necesaria la contraseña**.


### <a name="encryption"></a>Cifrado

- **Requerir cifrado en el dispositivo móvil**: no tiene que configurar este valor ya que los dispositivos Android for Work fuerzan el cifrado.


## <a name="device-health-and-security-settings"></a>Configuración de estado y la seguridad de dispositivos

- **El dispositivo no debe estar descodificado o liberado**: si habilita esta opción, los dispositivos descodificados se consideran no conformes.
- **Los dispositivos deben impedir la instalación de aplicaciones de orígenes desconocidos**: no es necesario configurar este valor ya que los dispositivos Android for Work siempre restringen la instalación de orígenes desconocidos.
- **La depuración USB debe estar deshabilitada**: no es necesario configurar esta opción, dado que la depuración USB ya está deshabilitada en los dispositivos Android for Work.
- **Nivel mínimo de revisión de seguridad de Android**: use esta opción para especificar el nivel mínimo de revisión de Android. No serán compatibles los dispositivos que no están al menos en este nivel de revisión. La fecha debe estar especificada en el formato: aaaa-MM-DD.
- **Requerir la habilitación de la protección frente a amenazas de dispositivo**: utilice esta opción para hacer que la evaluación del riesgo de la solución Lookout MTP sea una condición para el cumplimiento. Seleccione el nivel de amenaza máximo permitido, que es uno de los siguientes:
  - **Ninguno (protegido)** es la más segura. Esto significa que el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.
  - **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  - **Medio**: el dispositivo se evalúa como conforme si las amenazas presentes en él son de nivel bajo o medio. Si se detecta que el dispositivo presenta amenazas de nivel alto, se clasificará como no conforme.
  - **Alto**: esta opción es la menos segura. Básicamente, permite todos los niveles de amenaza y quizás solo sea útil si usa esta solución únicamente para fines informativos.

## <a name="device-property-settings"></a>Configuración de propiedades de dispositivo

- **SO mínimo requerido:** cuando un dispositivo no cumpla el requisito de versión de SO mínima, se notificará como no compatible. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo, tras lo cual podrá tener acceso a los recursos de la empresa.
- **Versión de SO máxima permitida**: cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
