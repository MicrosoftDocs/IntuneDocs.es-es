---
title: 'Comprobación del cumplimiento en dispositivos Windows en Microsoft Intune: Azure | Microsoft Docs'
description: Cree o configure una directiva de cumplimiento de dispositivos de Microsoft Intune para Windows Phone 8.1, Windows 8.1 y versiones posteriores, y dispositivos con Windows 10 y versiones posteriores. Compruebe el cumplimiento respecto a la versión mínima y máxima del sistema operativo, establezca las restricciones y la longitud de las contraseñas, requiera BitLocker, busque soluciones de antivirus de terceros, establezca el nivel de amenaza aceptable y habilite el cifrado en el almacenamiento de datos, incluidos Surface Hub y Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 518bb2ab0f59b5692ff2c2391fe971abba0639c6
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2019
ms.locfileid: "55072531"
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>Incorporación de una directiva de cumplimiento de dispositivos para dispositivos Windows en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Una directiva de cumplimiento de dispositivos de Intune incluye reglas y configuraciones que los dispositivos deben cumplir para que se consideren compatibles. Use estas directivas con acceso condicional para permitir o bloquear el acceso a los recursos de la organización. También puede obtener informes de dispositivos y realizar acciones en caso de incumplimiento.

Para más información sobre las directivas de cumplimiento, consulte [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).

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
| **Atestación de estado de Windows** | En cuarentena: Windows 10 y Windows 10 Mobile|No aplicable: Windows 8.1 |

-------------------------------

**Corregido** = el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena** = el sistema operativo del sistema no exige compatibilidad. (Por ejemplo, los dispositivos Android no obligan al usuario a cifrar el dispositivo). Si los dispositivos no son compatibles, se emprenden las acciones siguientes:

- El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
- El portal de empresa notifica al usuario acerca de los problemas de cumplimiento.

## <a name="create-a-device-compliance-policy"></a>Crear una directiva de cumplimiento de dispositivos

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Para **Plataforma** , seleccione **Windows Phone 8.1**, **Windows 8.1 y posterior** o **Windows 10 y versiones posteriores**.
6. Elija **Definir configuración** y especifique las opciones **Estado de dispositivos**, **Propiedades de dispositivo** y **Seguridad del sistema**. Cuando termine, seleccione **Aceptar** y **Crear**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="windows-81-devices-policy-settings"></a>Configuración de directivas de dispositivos Windows 8.1

Esta configuración de directivas se aplica a dispositivos que ejecutan las siguientes plataformas:

- Windows Phone 8,1
- Windows 8.1 y posterior

### <a name="device-properties"></a>Propiedades del dispositivo

- **Sistema operativo mínimo requerido**: cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no conforme. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo y luego acceder a los recursos de la empresa.
- **Versión de sistema operativo máxima permitida**: cuando un dispositivo usa una versión de SO posterior a la de la especificada en la regla, se bloquea el acceso a los recursos de la empresa. Se solicita al usuario que se ponga en contacto con el administrador de TI. El dispositivo no puede acceder a recursos de la organización hasta que cambie la regla para permitir la versión del SO.

Los equipos con Windows 8.1 devuelven la versión **3**. Si la regla de la versión de sistema operativo se establece en Windows 8.1 para Windows, el dispositivo se notificará como no conforme aunque tenga Windows 8.1.

### <a name="system-security"></a>Seguridad del sistema

#### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: **exija** a los usuarios que escriban una contraseña para acceder al dispositivo.
- **Contraseñas sencillas**: establezca esta opción en **Bloquear** para que los usuarios no puedan crear contraseñas sencillas, como **1234** o **1111**. Establézcala en **No configurado** para permitir a los usuarios crear contraseñas como **1234** o **1111**.
- **Longitud mínima de la contraseña**: especifique el número mínimo de dígitos o caracteres que debe tener la contraseña.

  Para los dispositivos que ejecutan Windows y a los que se accede con una cuenta de Microsoft, la directiva de cumplimiento no se puede evaluar correctamente:
  - Si la longitud mínima de la contraseña es superior a ocho caracteres
  - O si el número mínimo de conjuntos de caracteres es superior a dos

- **Tipo de contraseña**: elija si una contraseña debe tener solo caracteres **numéricos** o si es necesario combinar números y otros caracteres (**alfanuméricos**).
  
  - **Número de caracteres no alfanuméricos en la contraseña**: Si la opción **Tipo de contraseña requerida** está establecida en **Alfanumérica**, esta configuración especifica el número mínimo de caracteres que debe contener la contraseña. Los conjuntos de cuatro caracteres son los siguientes:
    - Letras minúsculas
    - Letras mayúsculas
    - Símbolos
    - Números

    Para establecer un número mayor, es necesario que el usuario cree una contraseña más compleja. Para los dispositivos a los que se accede con una cuenta de Microsoft, la directiva de cumplimiento no se puede evaluar correctamente:

    - Si la longitud mínima de la contraseña es superior a ocho caracteres
    - O si el número mínimo de conjuntos de caracteres es superior a dos

- **Máximo de minutos de inactividad antes de solicitar la contraseña**: especifique el tiempo de inactividad antes de que el usuario deba volver a escribir la contraseña.
- **Expiración de la contraseña (días)**: seleccione el número de días que faltan para que expire la contraseña y se deba crear una nueva.
- **Número de contraseñas anteriores que no se pueden reutilizar**: escriba el número de contraseñas usadas previamente que no se pueden volver a usar.

#### <a name="encryption"></a>Cifrado

- **Requerir cifrado en el dispositivo móvil**: **requerir** que el dispositivo se cifre para conectarse a recursos de almacenamiento de datos.

## <a name="windows-10-and-later-policy-settings"></a>Configuración de directivas en Windows 10 y versiones posteriores

### <a name="device-health"></a>Device health

- **Requerir BitLocker**: cuando BitLocker está activado, el dispositivo puede proteger los datos almacenados en la unidad frente al acceso no autorizado cuando el sistema está apagado o entra en estado de hibernación. La característica Cifrado de unidad BitLocker de Windows cifra todos los datos almacenados en el volumen del sistema operativo Windows. BitLocker usa el TPM para ayudar a proteger el sistema operativo Windows y los datos de usuario. También ayuda a confirmar que un equipo no se manipule, incluso si se deja desatendido, se pierde o se lo roban. Si el equipo incluye un TPM compatible, BitLocker lo usa para bloquear las claves de cifrado que protegen los datos. Como resultado, las claves no son accesibles hasta que el TPM comprueba el estado del equipo.
- **Debe estar habilitado el arranque seguro en el dispositivo**: Si el arranque seguro está habilitado, el sistema debe arrancar en un estado de confianza de fábrica. Además, si el arranque seguro está habilitado, los componentes principales que se usan para arrancar el equipo deben tener las firmas de cifrado correctas que son de confianza para la organización que fabricó el dispositivo. El firmware UEFI comprueba la firma antes de permitir iniciar el equipo. Si los archivos se manipulan, lo que rompe su firma, el sistema no arranca.

  > [!NOTE]
  > La configuración de **Debe estar habilitado el arranque seguro en el dispositivo** es compatible con dispositivos TPM 1.2 y 2.0. Para los dispositivos que no son compatibles con TPM 2.0 o versiones posteriores, el estado de la directiva en Intune se muestra como **No conforme**. Esta es una limitación del servicio [Atestación de estado de dispositivo](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation) en Windows 10.

- **Requiere integridad de código**: la integridad de código es una característica que valida la integridad de un archivo del sistema o controlador cada vez que se carga en la memoria. La integridad de código detecta si se está cargando en el kernel un archivo del sistema o controlador sin firmar. También detecta si se ha modificado un archivo del sistema mediante software malintencionado ejecutado por usuario con privilegios de administrador.

Consulte [Health Attestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) (CSP de atestación de mantenimiento) para detalles sobre cómo funciona el servicio HAS.

### <a name="device-properties"></a>Propiedades del dispositivo

- **Versión mínima del sistema operativo**: escriba la versión mínima permitida, con el formato numérico **major.minor.build.CU**. Para obtener el valor correcto, abra un símbolo del sistema y escriba `ver`. El comando `ver` devuelve la versión en este formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Cuando un dispositivo tiene una versión anterior a la versión del sistema operativo que especifica, se notifica como no conforme. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede elegir actualizar su dispositivo. Después de la actualización, puede acceder a los recursos de la empresa.

- **Versión máxima de SO**: escriba la versión máxima permitida, con el formato numérico **major.minor.build.revision**. Para obtener el valor correcto, abra un símbolo del sistema y escriba `ver`. El comando `ver` devuelve la versión en este formato:

  `Microsoft Windows [Version 10.0.17134.1]`

  Cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. El dispositivo no podrá acceder a los recursos de la empresa mientras no se cambie la regla para permitir la versión de SO.

- **Versión mínima del SO requerida para dispositivos móviles**: escriba la versión mínima permitida, con el formato numérico major.minor.build.

  Cuando un dispositivo tiene una versión anterior a la versión del sistema operativo que especifica, se notifica como no conforme. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede elegir actualizar su dispositivo. Después de la actualización, puede acceder a los recursos de la empresa.

- **Versión máxima del SO requerida para dispositivos móviles**: escriba la versión máxima permitida, con el formato numérico major.minor.build.

  Cuando un dispositivo usa una versión de SO posterior a la especificada, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. El dispositivo no podrá acceder a los recursos de la empresa mientras no se cambie la regla para permitir la versión de SO.

- **Compilaciones válidas del sistema operativo**: escriba un intervalo para las versiones de sistema operativo aceptables, incluida la mínima y la máxima. También puede **exportar** una lista de archivos de valores separados por comas (CSV) de estos números de compilación aceptables del sistema operativo.

### <a name="configuration-manager-compliance"></a>Comprobación del cumplimiento de Configuration Manager

Solo se aplica a dispositivos administrados conjuntamente en los que se ejecuta Windows 10 y versiones posteriores. Los dispositivos solo de Intune devuelven un estado de no disponible.

- **Requerir cumplimiento del dispositivo de System Center Configuration Manager**: elija **Requerir** para exigir a todos las configuraciones (elementos de configuración) de System Center Configuration Manager que sean compatibles. 

  Por ejemplo, exige que todas las actualizaciones de software se instalen en los dispositivos. En Configuration Manager, este requisito tiene el estado “Instalado”. Si algún programa del dispositivo se encuentra en un estado desconocido, dicho dispositivo no será conforme en Intune.
  
  Si la opción es **No configurada**, Intune no comprueba ninguna configuración de Configuration Manager para el cumplimiento.

### <a name="system-security-settings"></a>Configuración de seguridad del sistema

#### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: **exija** a los usuarios que escriban una contraseña para acceder al dispositivo.
- **Contraseñas sencillas**: establezca esta opción en **Bloquear** para que los usuarios no puedan crear contraseñas sencillas, como **1234** o **1111**. Establézcala en **No configurado** para permitir a los usuarios crear contraseñas como **1234** o **1111**.
- **Tipo de contraseña**: elija si una contraseña debe tener solo caracteres **numéricos** o si es necesario combinar números y otros caracteres (**alfanuméricos**).

  - **Número de caracteres no alfanuméricos en la contraseña**: Si la opción **Tipo de contraseña requerida** está establecida en **Alfanumérica**, esta configuración especifica el número mínimo de caracteres que debe contener la contraseña. Los conjuntos de cuatro caracteres son los siguientes:
    - Letras minúsculas
    - Letras mayúsculas
    - Símbolos
    - Números

    Para establecer un número mayor, es necesario que el usuario cree una contraseña más compleja.

- **Longitud mínima de la contraseña**: especifique el número mínimo de dígitos o caracteres que debe tener la contraseña.
- **Máximo de minutos de inactividad antes de solicitar la contraseña**: especifique el tiempo de inactividad antes de que el usuario deba volver a escribir la contraseña.
- **Expiración de la contraseña (días)**: seleccione el número de días que faltan para que expire la contraseña y se deba crear una nueva.
- **Número de contraseñas anteriores que no se pueden reutilizar**: escriba el número de contraseñas usadas previamente que no se pueden volver a usar.
- **Requerir contraseña cuando el dispositivo vuelve de un estado de inactividad (Mobile y Holographic)** : esta opción exige a los usuarios que introduzcan la contraseña cada vez que el dispositivo vuelve de un estado de inactividad.

#### <a name="encryption"></a>Cifrado

- **Cifrado de almacenamiento de datos en un dispositivo**: elija **Requerir** para cifrar el almacenamiento de datos en los dispositivos.

  > [!NOTE]
  > La configuración **Cifrado de almacenamiento de datos en el dispositivo** comprueba de manera genérica la presencia de cifrado en el dispositivo. Para conseguir una configuración de cifrado más sólida, considere la posibilidad de usar **Requerir BitLocker**, que aprovecha la Atestación de estado de dispositivo de Windows para validar el estado de Bitlocker en el nivel de TPM.

#### <a name="device-security"></a>Seguridad de dispositivos

- **Antivirus**: cuando se establece en **Requerir**, puede comprobar el cumplimiento mediante soluciones antivirus registradas con Windows Security Center, como Symantec y Windows Defender. Si se establece en **Sin configurar**, Intune no busca soluciones antivirus instaladas en el dispositivo.
- **Antispyware**: cuando se establece en **Requerir**, puede comprobar el cumplimiento mediante soluciones antispyware registradas con Windows Security Center, como Symantec y Windows Defender. Si se establece en **Sin configurar**, Intune no busca soluciones antispyware instaladas en el dispositivo.

### <a name="windows-defender-atp"></a>ATP de Windows Defender

- **Require the device to be at or under the machine risk score**: (Requerir que el dispositivo tenga la misma puntuación de riesgo de la máquina o inferior): use este valor de configuración para hacer que la evaluación del riesgo de los servicios de amenazas de defensa sea una condición para el cumplimiento. Elija el máximo nivel de amenaza permitido:
  - **Borrar**: esta opción es la más segura, ya que el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.
  - **Baja**: el dispositivo se evalúa como compatible si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  - **Media**: el dispositivo se evalúa como compatible si las amenazas existentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
  - **Alta**: esta opción es la menos segura y permite que todos los niveles de amenaza. Quizás sea útil si utiliza esta solución solo con fines informativos.
  
  Para configurar ATP (protección contra amenazas avanzada) de Windows Defender como servicio de defensa contra amenazas, consulte [Habilitación de ATP de Windows Defender con acceso condicional](advanced-threat-protection.md).

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business usa la plataforma **Windows 10 y versiones posteriores**. Windows Holographic for Business es compatible con las siguientes opciones de configuración:

- **Seguridad del sistema** > **Cifrado** > **Cifrado de almacenamiento de datos en el dispositivo**.

Para verificar el cifrado de dispositivo en Microsoft HoloLens, vea [Verificar el cifrado de dispositivo](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub
Surface Hub usa la plataforma **Windows 10 y versiones posteriores**. Las instancias de Surface Hub son compatibles tanto con el cumplimiento como con el acceso condicional. Para habilitar estas características en Surface Hubs, le recomendamos que [habilite la inscripción automática de Windows 10 ](windows-enroll.md) en Intune (también requiere Azure Active Directory [Azure AD]) y dirija los dispositivos de Surface Hub como grupos de dispositivos. Se requiere que Surface Hub se una a Azure AD para que el cumplimiento y el acceso condicional funcionen.

Consulte [Configuración de la inscripción de dispositivos Windows](windows-enroll.md) para instrucciones.

## <a name="assign-user-or-device-groups"></a>Asignación de grupos de usuarios o dispositivos

1. Elija una directiva que haya configurado. Las directivas existentes están en **Conformidad de dispositivos** > **Directivas**.
2. Elija la directiva y luego **Asignaciones**. Puede incluir o excluir grupos de seguridad de Azure AD.
3. Elija **Grupos seleccionados** para ver los grupos de seguridad de Azure AD. Seleccione los grupos de usuarios o dispositivos a los que quiera aplicar esta directiva y elija **Guardar** para implementar la directiva.

Ya ha aplicado la directiva. Se evalúa el cumplimiento de los dispositivos que utilizan los usuarios a los que se destina la directiva.

## <a name="next-steps"></a>Pasos siguientes
[Automatización del correo electrónico y adición de acciones para dispositivos no compatibles: Intune](actions-for-noncompliance.md)  
[Supervisión de las directivas de cumplimiento de dispositivos de Intune](compliance-policy-monitor.md)
