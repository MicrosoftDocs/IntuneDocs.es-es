---
title: "Creación de una directiva de cumplimiento de dispositivos en Microsoft Intune"
titleSuffix: 
description: Cree una directiva de cumplimiento de dispositivos de Microsoft Intune para dispositivos Android para poder especificar los requisitos que debe cumplir un dispositivo para que sea compatible.
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 283685629ac1e268a66d82250273a17f9baa5d17
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-android-devices-in-intune"></a>Creación de una directiva de cumplimiento de dispositivos para dispositivos Android en Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Una directiva de cumplimiento de dispositivos de Intune para Android especifica las reglas y la configuración que los dispositivos Android deben cumplir para que se consideren compatibles. Estas directivas se pueden usar con el acceso condicional para permitir o bloquear el acceso a recursos de la empresa, y se pueden obtener informes de dispositivos y realizar acciones en caso de incumplimiento. Las directivas de cumplimiento de dispositivos para cada plataforma se crean en Azure Portal de Intune. Para obtener más información sobre las directivas de cumplimiento y los requisitos previos que deben satisfacerse antes de crear una, consulte [Introducción a las directivas de cumplimiento de dispositivos](device-compliance-get-started.md).

## <a name="to-create-a-device-compliance-policy"></a>Pasos para crear una directiva de cumplimiento de dispositivos

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
1. En el panel **Intune**, elija **Cumplimiento del dispositivo**. En **Administrar**, elija **Directivas** y después **Crear directiva**.
3. Elija **Configuración de valores** para especificar aquí las opciones de **Seguridad del sistema**, **Estado de dispositivos** y **Propiedades del dispositivo**. Cuando termine, elija **Aceptar**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.--->

## <a name="to-assign-user-groups"></a>Pasos para asignar grupos de usuarios

Para asignar una directiva de cumplimiento a los usuarios, elija una directiva que haya configurado. Las directivas existentes se pueden encontrar en el panel **Conformidad del dispositivo: directivas**.

1. Elija la directiva y luego **Asignaciones**. Se abre el panel donde puede seleccionar **grupos de seguridad de Azure Active Directory** y asignarlos a la directiva.
2. Elija **Grupos seleccionados** para abrir el panel en el que se muestran los grupos de seguridad de Azure AD. Aquí puede encontrar los grupos de seguridad de su instancia de Azure Active Directory.  Puede seleccionar los grupos de usuarios a los que quiera aplicar esta directiva y elegir **Guardar** para implementarla a los usuarios.

Ya ha aplicado la directiva a los usuarios.  Ahora se evaluará el cumplimiento de los dispositivos usados por los usuarios a los que se aplique la directiva.

<!---##  Compliance policy settings--->

## <a name="device-health-and-security-settings"></a>Configuración de estado y la seguridad de dispositivos

- **El dispositivo no debe estar descodificado o descifrado**: si habilita esta opción, los dispositivos descodificados se considerarán como no compatibles.
- **Requerir que los dispositivos impidan la instalación de aplicaciones desde orígenes desconocidos (Android 4.0 o posterior)**: para bloquear los dispositivos que tienen **Seguridad** > **Orígenes desconocidos** habilitado en el dispositivo, habilite esta configuración y establézcala en **Sí**.

### <a name="important"></a>Importante

Las aplicaciones de instalación de prueba requieren que se habilite la opción **Orígenes desconocidos**. Aplique esta directiva de cumplimiento solo si no tiene aplicaciones Android de instalación de prueba en dispositivos.

- **Requerir que se deshabilite la depuración USB (Android 4.2 o posterior)**: esta opción especifica si está habilitada la opción para detectar la opción de depuración USB en el dispositivo.
- **Requerir que los dispositivos habiliten el dispositivo de análisis de amenazas de seguridad (Android 4.4 4.2)**: Esta opción especifica que la característica **Comprobar aplicaciones** está habilitada en el dispositivo.
- **Nivel de revisión de seguridad mínimos de Android (Android 6.0 o posterior)**: Utilice esta opción para especificar el nivel de revisión mínima de Android. No serán compatibles los dispositivos que no están al menos en este nivel de revisión. La fecha debe especificarse en el formato: AAAA-MM-DD.
- **Requerir la habilitación de la protección frente a amenazas de dispositivo**: utilice esta opción para hacer que la evaluación del riesgo de la solución Lookout MTP sea una condición para el cumplimiento. Elija el nivel de amenaza máximo permitido, que es uno de los siguientes:
  - **Ninguno (protegido)**: es la más segura. Esto significa que el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.
  - **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  - **Medio**: el dispositivo se evalúa como conforme si las amenazas presentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
  - **Alto**: esta opción es la menos segura. Básicamente, esto permite todos los niveles de amenaza. Quizás sea útil si está usando esta solución solo con fines informativos.

Para ver más detalles, consulte [Habilitar la regla de protección contra amenazas móviles en la directiva de cumplimiento normativo](https://docs.microsoft.com/intune-classic/deploy-use/enable-device-threat-protection-rule-in-compliance-policy).

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: establezca esta opción en **Sí** para exigir que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos.
- **Longitud mínima de la contraseña**: especifique el número mínimo de dígitos o caracteres que debe tener la contraseña de usuario.
- **Calidad de contraseña**: esta opción detecta si los requisitos de contraseña que especifique se configuran en el dispositivo. Habilite esta opción para requerir a los usuarios que cumplan determinados requisitos de contraseña para dispositivos Android. Elija de entre las siguientes opciones:
  - **Biométrico de seguridad baja**
  - **Requerido**
  - **Al menos numérica**
  - **Al menos alfabética**
  - **Al menos alfanumérica**
  - **Alfanumérica con símbolos**
- **Minutos de inactividad antes de que sea necesaria la contraseña**: especifique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir su contraseña.
- **Caducidad de contraseña (días)**: seleccione el número de días que faltan para que la contraseña expire y se deba crear una nueva.
- **Recordar historial de contraseñas**: use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para impedir que el usuario cree contraseñas que se han usado anteriormente.
- **Impedir la reutilización de contraseñas anteriores**: si ha seleccionado **Recordar historial de contraseñas**, especifique el número de contraseñas que se han usado previamente que no se pueden volver a usar.
- **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad**: use este valor junto con el de la opción **Minutos de inactividad antes de que sea necesaria la contraseña**. Se pedirá al usuario que escriba una contraseña para obtener acceso a un dispositivo que haya estado inactivo durante el tiempo especificado en la opción **Minutos de inactividad antes de que sea necesaria la contraseña**.

### <a name="encryption"></a>Cifrado

- **Requerir cifrado en el dispositivo móvil**: establezca esta opción en **Sí** para requerir que los dispositivos estén cifrados para poder conectarse a los recursos. Los dispositivos se cifran al elegir la opción **Requerir una contraseña para desbloquear dispositivos móviles**.

## <a name="device-property-settings"></a>Configuración de propiedades de dispositivo

- **SO mínimo requerido:** cuando un dispositivo no cumpla el requisito de versión de SO mínima, se notificará como no compatible. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario puede optar por actualizar el dispositivo, tras lo cual podrá tener acceso a los recursos de la empresa.
- **Versión de SO máxima permitida**: cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambien las reglas para permitir la versión de SO, este dispositivo no podrá usarse para tener acceso a los recursos de la empresa.

## <a name="how-noncompliant-settings-work-with-conditional-access-policies"></a>¿Cómo funciona la configuración de no conformidad con las directivas de acceso condicional?

En la tabla siguiente se describe cómo administrar la configuración de no conformidad cuando se usa una directiva de cumplimiento con una directiva de acceso condicional.

--------------------

|**Configuración de directiva**| **Android 4.0 y versiones posteriores, Samsung Knox Standard 4.0 y versiones posteriores** |
| --- | ----|
| **Configuración de PIN o contraseña** |  En cuarentena |
| **Cifrado del dispositivo** | En cuarentena |
| **Dispositivo liberado o modificado** | En cuarentena (no es una configuración) |
| **Perfil de correo electrónico** | No disponible |
| **Versión de SO mínima** | En cuarentena |
| **Versión de SO máxima** |   En cuarentena |
| **Atestación de estado de Windows** | No disponible |

--------------------------

**Corregido** = el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena** = el sistema operativo del sistema no exige compatibilidad. (Por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo). Si los dispositivos no son compatibles, se emprenden las acciones siguientes:

- El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
- El portal de empresa notifica al usuario acerca de los problemas de cumplimiento.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
