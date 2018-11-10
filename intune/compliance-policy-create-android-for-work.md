---
title: 'Creación de una directiva de cumplimiento de Android Enterprise en Microsoft Intune: Azure | Microsoft Docs'
description: Cree o configure una directiva de cumplimiento de dispositivos Microsoft Intune para dispositivos de perfil de trabajo Android Enterprise. Opte por permitir dispositivos con Jailbroken, establecer el nivel de amenaza aceptable, buscar Google Play, especificar la versión de sistema operativo mínima y máxima, elegir los requisitos de contraseña y permitir aplicaciones de instalación de prueba.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ff1f4f6a728fc041241371a413ce9d2dfdf89605
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236465"
---
# <a name="add-a-device-compliance-policy-for-android-enterprise-devices-in-intune"></a>Incorporación de una directiva de cumplimiento de dispositivos para dispositivos Android Enterprise en Intune

Las directivas de cumplimiento de dispositivos son una característica clave cuando se usa Intune para proteger los recursos de su organización. En Intune, puede crear reglas y opciones de configuración que los dispositivos deben cumplir para que se consideren conformes, por ejemplo, una longitud de contraseña. Si el dispositivo no las cumple, puede bloquear el acceso a datos y recursos mediante el [acceso condicional](conditional-access.md). 

También puede obtener informes de dispositivos y realizar acciones en caso de incumplimiento, como enviar un correo electrónico de notificación al usuario. Para más información sobre las directivas de cumplimiento, consulte [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).

En este artículo se enumeran los valores que puede usar en una directiva de cumplimiento para dispositivos que ejecutan Android Enterprise.

## <a name="non-compliance-and-conditional-access"></a>Incumplimiento y acceso condicional

En la tabla siguiente se describe cómo administrar la configuración de no conformidad cuando se usa una directiva de cumplimiento con una directiva de acceso condicional.

--------------------------

|**Configuración de directiva**| **Perfil de Android Enterprise** |
| --- | --- |
| **Configuración de PIN o contraseña** |  En cuarentena |
| **Cifrado del dispositivo** |  En cuarentena |
| **Dispositivo liberado o modificado** | En cuarentena (no es una configuración) |
| **Perfil de correo electrónico** | No disponible |
| **Versión de SO mínima** | En cuarentena |
| **Versión de SO máxima** | En cuarentena |
| **Atestación de estado de Windows** |No disponible |

**Corregido** = el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena** = el sistema operativo del dispositivo no exige cumplimiento. Por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo. Si el dispositivo no es conforme, se emprenden las acciones siguientes:

  - El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
  - El portal de empresa notifica al usuario acerca de los problemas de cumplimiento.

## <a name="create-a-device-compliance-policy"></a>Crear una directiva de cumplimiento de dispositivos

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Para **Plataforma**, seleccione **Android Enterprise**. 
5. Elija **Settings Configure** (Definir configuración). Especifique las opciones **Estado de dispositivos**, **Propiedades de dispositivo** y **Seguridad del sistema**, tal y como se describe en este artículo.

## <a name="device-health"></a>Device health

- **Dispositivos raíz**: elija **Bloquear** para marcar los dispositivos raíz (con jailbreak) como no conformes. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Requerir que el dispositivo tenga el nivel de amenaza del dispositivo**: use esta opción para hacer que la evaluación del riesgo de la solución Lookout MTP sea una condición para el cumplimiento. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración. Para usar esta configuración, elija el nivel de amenaza permitido:
  - **Protegido**: esta opción es la más segura y significa que el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.
  - **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  - **Medio**: el dispositivo se evalúa como conforme si las amenazas presentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
  - **Alto**: esta opción es la menos segura, ya que permite que todos los niveles de amenaza. Quizás sea útil si utiliza esta solución solo con fines informativos.
- **Google Play Services está configurado**: se **requiere** que la aplicación Google Play Services esté instalada y habilitada. Google Play Services permite actualizaciones de seguridad y es una dependencia de nivel base para muchas características de seguridad en los dispositivos de Google certificados. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Proveedor de seguridad actualizada**: se **requiere** que un proveedor de seguridad actualizado pueda proteger un dispositivo frente a vulnerabilidades conocidas. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Atestación de dispositivo SafetyNet**: especifique el nivel de [atestación de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que se debe cumplir. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se evalúa el cumplimiento o incumplimiento de esta configuración.
  - **Comprobar integridad básica**
  - **Comprobar integridad básica y dispositivos certificados**

#### <a name="threat-scan-on-apps"></a>Examen de amenazas en las aplicaciones

En los dispositivos Android Enterprise, la configuración **Examen de amenazas en las aplicaciones** es una directiva de configuración. Vea [Configuración de las restricciones de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

## <a name="device-properties-settings"></a>Configuración de las propiedades del dispositivo

- **Versión mínima del sistema operativo**: cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no conforme. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo y luego acceder a los recursos de la empresa.
- **Versión máxima de SO**: cuando un dispositivo usa una versión de SO posterior a la de la regla, se bloquea el acceso a los recursos de la empresa. Además, se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, el dispositivo no podrá acceder a los recursos de la empresa.

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: **requiere** que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Longitud mínima de la contraseña**: indique el número mínimo de dígitos o caracteres que debe tener la contraseña del usuario.
- **Tipo de contraseña requerida**: elija si una contraseña debe incluir solo caracteres numéricos o una combinación de números y otros caracteres. Las opciones son:
  - **Valor predeterminado del dispositivo**
  - **Biométrico de seguridad baja**
  - **Al menos numérica** (valor predeterminado)
  - **Numérica compleja**
  - **Al menos alfabética**
  - **Al menos alfanumérica**
  - **Al menos alfanumérica con símbolos**

- **Máximo de minutos de inactividad antes de solicitar la contraseña**: indique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir la contraseña. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Expiración de la contraseña (días)**: seleccione el número de días que faltan para que la contraseña expire y se deba crear una nueva.
- **Número de contraseñas anteriores que no se pueden reutilizar**: indique el número de contraseñas recientes que no se pueden volver a usar. Utilice esta configuración para impedir que el usuario cree contraseñas usadas anteriormente.

### <a name="encryption"></a>Cifrado

- **Cifrado de almacenamiento de datos en el dispositivo**: elija **Requerir** para cifrar el almacenamiento de datos en los dispositivos. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración. 

  No tiene que configurar este valor ya que los dispositivos de perfil de trabajo Android fuerzan el cifrado.

### <a name="device-security"></a>Seguridad de dispositivos

- **Bloquear aplicaciones de orígenes desconocidos**: elija **bloquear** los dispositivos con la opción "Seguridad > Orígenes desconocidos" habilitada (se admite de Android 4.0 a Android 7.x; no se admite en Android 8.0 ni versiones posteriores). Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

  Para realizar instalaciones de prueba de las aplicaciones, se deben permitir los orígenes desconocidos. Si no realiza instalaciones de prueba de las aplicaciones Android, establezca esta característica en **Bloquear** para habilitar esta directiva de cumplimiento. 

  > [!IMPORTANT]
  > Las aplicaciones de instalación de prueba requieren que se habilite la opción **Bloquear aplicaciones de orígenes desconocidos**. Aplique esta directiva de cumplimiento solo si no realiza instalaciones de prueba de las aplicaciones Android en dispositivos.

  No tiene que configurar este valor ya que los dispositivos de perfil de trabajo Android siempre restringen la instalación desde orígenes desconocidos.

- **Integridad en tiempo de ejecución de la aplicación Portal de empresa**: elija **Requerir** para confirmar que la aplicación Portal de empresa cumple los siguientes requisitos:

  - Tiene instalado el entorno de tiempo de ejecución predeterminado.
  - Está firmada correctamente.
  - No se encuentra en modo de depuración.
  - Se ha instalado desde un origen conocido.

  Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

- **Bloquear depuración USB en el dispositivo**: elija **Bloquear** para evitar que los dispositivos usen la característica de depuración USB. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

  No es necesario configurar este valor porque la depuración USB ya está deshabilitada en los dispositivos de perfil de trabajo Android.

- **Nivel mínimo de revisión de seguridad**: seleccione el nivel de revisión de seguridad más antiguo que puede tener un dispositivo. Los dispositivos que no estén al menos en este nivel de revisión se consideran no conformes. La fecha debe especificarse en el formato *AAAA-MM-DD*.

Cuando termine, seleccione **Aceptar** > **Aceptar** para guardar los cambios.

## <a name="actions-for-noncompliance"></a>Acciones en caso de incumplimiento

Seleccione **Actions for noncompliance** (Acciones en caso no conformidad). La acción predeterminada marca inmediatamente el dispositivo como no conforme.

Puede cambiar la programación cuando el dispositivo se marca como no conforme, por ejemplo, después de un día. También puede configurar una segunda acción que envía un correo electrónico al usuario cuando el dispositivo es no conforme.

En [Adición de acciones en caso de incumplimiento](actions-for-noncompliance.md) se proporciona más información, por ejemplo, cómo crear un correo electrónico para notificar a los usuarios.

## <a name="scope-tags"></a>Etiquetas de ámbito

Las etiquetas de ámbito son una excelente manera de asignar directivas a grupos específicos, como Ventas, Ingeniería, RR. HH., etc. Puede agregar etiquetas de ámbito a las directivas de cumplimiento. Vea [Uso de etiquetas de ámbito para filtrar directivas](scope-tags.md). 

## <a name="assign-user-groups"></a>Asignación de grupos de usuarios

Una vez que se crea una directiva, no hace nada hasta que se asigna. Para asignar la directiva: 

1. Elija una directiva que haya configurado. Las directivas existentes están en **Conformidad de dispositivos** > **Directivas**.
2. Elija la directiva y luego **Asignaciones**. Puede incluir o excluir grupos de seguridad de Azure Active Directory (AD).
3. Elija **Grupos seleccionados** para ver los grupos de seguridad de Azure AD. Seleccione los grupos de usuarios a los que quiera aplicar esta directiva y elija **Guardar** para implementar la directiva a los usuarios.

Ya ha aplicado la directiva a los usuarios. Se evalúa el cumplimiento de los dispositivos que utilizan los usuarios a los que se destina la directiva.

## <a name="next-steps"></a>Pasos siguientes
[Automatización del correo electrónico y adición de acciones para dispositivos no compatibles: Intune](actions-for-noncompliance.md)  
[Supervisión de las directivas de cumplimiento de dispositivos de Intune](compliance-policy-monitor.md)  
[Configuración de directivas de cumplimiento para Android](compliance-policy-create-android.md)