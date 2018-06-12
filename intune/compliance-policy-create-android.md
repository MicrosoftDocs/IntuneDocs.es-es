---
title: Creación de una directiva de cumplimiento de dispositivos Android en Microsoft Intune - Azure | Microsoft Docs
description: Cree o configure una directiva de cumplimiento de dispositivos Microsoft Intune para dispositivos Android. Opte por permitir dispositivos con Jailbroken, establecer el nivel de amenaza aceptable, buscar Google Play, especificar la versión de sistema operativo mínima y máxima, elegir los requisitos de contraseña y permitir aplicaciones de instalación de prueba.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2277da45ad1404269571f36dec0c16443409b39f
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744710"
---
# <a name="add-a-device-compliance-policy-for-android-devices-in-intune"></a>Incorporación de una directiva de cumplimiento de dispositivos para dispositivos Android en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Una directiva de cumplimiento de dispositivos de Intune para Android especifica las reglas y la configuración que los dispositivos Android deben cumplir para que se consideren compatibles. Puede usar estas directivas con acceso condicional para permitir o bloquear el acceso a los recursos de la empresa. También puede obtener informes de dispositivos y realizar acciones en caso de incumplimiento. Las directivas de cumplimiento de dispositivos para cada plataforma se crean en Azure Portal de Intune. Para más información sobre las directivas de cumplimiento, consulte [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).

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

## <a name="create-a-device-compliance-policy"></a>Crear una directiva de cumplimiento de dispositivos

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Para **Plataforma**, seleccione **Android**. Seleccione **Definir configuración** y especifique las opciones **Estado de dispositivos**, **Propiedades de dispositivo** y **Seguridad del sistema**. Cuando haya terminado, seleccione **Aceptar** y **Crear**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.--->

<!---##  Compliance policy settings--->

## <a name="device-health"></a>Device health

- **Dispositivos raíz**: si habilita esta configuración, los dispositivos con Jailbreak se evaluarán como no compatibles.
- **Requerir que el dispositivo tenga el nivel de amenaza del dispositivo**: use esta opción para hacer que la evaluación del riesgo de la solución Lookout MTP sea una condición para el cumplimiento. Elija máximo nivel de amenaza permitido:
  - **Protegido**: esta opción es la más segura y el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.
  - **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  - **Medio:** el dispositivo se evalúa como compatible si las amenazas existentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
  - **Alto**: esta opción es la menos segura, ya que permite que todos los niveles de amenaza. Quizás sea útil si utiliza esta solución solo con fines informativos.
- **Google Play Services está configurado**: se requiere que la aplicación Google Play Services esté instalada y habilitada. Google Play Services permite actualizaciones de seguridad y es una dependencia de nivel base para muchas características de seguridad en los dispositivos de Google certificados.
- **Proveedor de seguridad actualizado**: se requiere que un proveedor de seguridad actualizado pueda proteger un dispositivo frente a vulnerabilidades conocidas.
- **Examen de amenazas en las aplicaciones**: se requiere que la característica **Verificar aplicaciones** de Android esté habilitada.

  > [!NOTE]
  > En la plataforma Android heredada, esta característica es una configuración de cumplimiento. Intune solo puede comprobar si esta configuración está habilitada en el nivel de dispositivo. En los dispositivos con perfiles de trabajo (Android for Work), esta configuración puede encontrarse como un ajuste de la directiva de configuración. Esto permite a los administradores habilitar la configuración para un dispositivo.

  Si su empresa utiliza perfiles de trabajo Android, puede habilitar **Examen de amenazas en las aplicaciones** en los dispositivos inscritos. Establezca un perfil de dispositivo y requiera la configuración de seguridad del sistema. Para más información, consulte [Configuración de las restricciones de dispositivos de trabajo en Intune](device-restrictions-android-for-work.md).

- **Atestación de dispositivo SafetyNet**: especifique el nivel de [atestación de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que se debe cumplir. Las opciones son:
  - **No configurado**.
  - **Comprobar integridad básica**
  - **Comprobar integridad básica y dispositivos certificados**

## <a name="device-property-settings"></a>Configuración de propiedades de dispositivo

- **Versión mínima del sistema operativo**: cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no conforme. Se muestra un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo y luego acceder a los recursos de la empresa.
- **Versión máxima de SO**: cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa. Se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, el dispositivo no podrá acceder a los recursos de la empresa.

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: **requiere** que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos.
- **Longitud mínima de la contraseña**: indique el número mínimo de dígitos o caracteres que debe tener la contraseña del usuario.
- **Tipo de contraseña requerida**: seleccione si una contraseña debe tener solo caracteres numéricos o es necesario combinar números y otros caracteres. Elija de entre las siguientes opciones:
  - **Valor predeterminado del dispositivo**
  - **Biométrico de seguridad baja**
  - **Al menos numérica**
  - **Complejo numérico**: no se permiten números consecutivos ni repetidos(como "1111" o "1234").
  - **Al menos alfabética**
  - **Al menos alfanumérica**
  - **Al menos alfanumérica con símbolos**
- **Máximo de minutos de inactividad antes de solicitar la contraseña**: indique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir la contraseña.
- **Expiración de la contraseña (días)**: seleccione el número de días que faltan para que expire la contraseña y durante los cuales el usuario debe crear otra.
- **Número de contraseñas anteriores que no se pueden reutilizar**: indique el número de contraseñas recientes que no se pueden volver a usar. Utilice esta configuración para impedir que el usuario cree contraseñas usadas anteriormente.

### <a name="encryption"></a>Cifrado

- **Cifrado de almacenamiento de datos en un dispositivo** (Android 4.0 y versiones posteriores, o KNOX 4.0 y versiones posteriores): elija **Requerir** para cifrar el almacenamiento de datos en los dispositivos. Los dispositivos se cifran al elegir la opción **Requerir una contraseña para desbloquear dispositivos móviles**.

### <a name="device-security"></a>Seguridad de dispositivos

- **Bloquear aplicaciones de orígenes desconocidos**: elija bloquear los dispositivos con la opción "Seguridad > Orígenes desconocidos" habilitada (desde Android 4.0 hasta Android 7.x. No se admite en Android 8.0 y versiones posteriores). Para realizar instalaciones de prueba de las aplicaciones, se deben permitir los orígenes desconocidos. Si no realiza instalaciones de prueba de las aplicaciones Android, habilite esta directiva de cumplimiento.

  > [!IMPORTANT]
  > Las aplicaciones de instalación de prueba requieren que se habilite la opción **Bloquear aplicaciones de orígenes desconocidos**. Aplique esta directiva de cumplimiento solo si no tiene aplicaciones Android de instalación de prueba en dispositivos.

- **Integridad en tiempo de ejecución de la aplicación Portal de empresa**: comprueba si la aplicación Portal de empresa tiene el entorno de tiempo de ejecución predeterminado instalado, está firmada correctamente, no está en modo de depuración y se instala desde un origen conocido.
- **Bloquear depuración USB en el dispositivo** (Android 4.2 o posterior): elija evitar que los dispositivos usen la característica de depuración USB.
- **Nivel mínimo de revisión de seguridad** (Android 6.0 o posterior): seleccione el nivel de revisión de seguridad más antiguo que puede tener un dispositivo. No son compatibles los dispositivos que no están al menos en este nivel de revisión. La fecha debe especificarse en el formato `YYYY-MM-DD`.

## <a name="locations"></a>Ubicaciones

En la directiva, realice una elección entre las ubicaciones existentes. ¿Aún no tiene una ubicación? En el apartado [Usar ubicaciones (límite de red) en Intune](use-network-locations.md) se proporcionan algunas instrucciones.

1. Elija **Seleccionar ubicaciones**.
2. En la lista, compruebe la ubicación y elija **Seleccionar**.
3. Haga clic en **Guardar** la directiva.
4. Seleccione **Actions for noncompliance** (Acciones en caso no conformidad). La acción predeterminada marca inmediatamente el dispositivo como no conforme. Esta acción se aplica cuando se selecciona al menos una ubicación y si el dispositivo no está conectado a las ubicaciones seleccionadas.

  Puede cambiar esta acción para actualizar la programación cuando el dispositivo esté marcado como no conforme, por ejemplo, después de un día. También puede configurar una segunda acción que envía un correo electrónico al usuario cuando el dispositivo ya no cumple con los requisitos de ubicación.

## <a name="assign-user-groups"></a>Asignación de grupos de usuarios

1. Elija una directiva que haya configurado. Las directivas existentes están en **Conformidad de dispositivos** > **Directivas**.
2. Elija la directiva y luego **Asignaciones**. Puede incluir o excluir grupos de seguridad de Azure Active Directory (AD).
3. Elija **Grupos seleccionados** para ver los grupos de seguridad de Azure AD. Seleccione los grupos de usuarios a los que quiera aplicar esta directiva y elija **Guardar** para implementar la directiva a los usuarios.

Ya ha aplicado la directiva a los usuarios. Se evalúa el cumplimiento por parte de los dispositivos usados por los usuarios a los que se aplique la directiva.

## <a name="next-steps"></a>Pasos siguientes
[Automatización del correo electrónico y adición de acciones para dispositivos no compatibles: Intune](actions-for-noncompliance.md)  
[Supervisión de las directivas de cumplimiento de dispositivos de Intune](compliance-policy-monitor.md)