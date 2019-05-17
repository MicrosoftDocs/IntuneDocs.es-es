---
title: Directivas de cumplimiento de dispositivos en Microsoft Intune - Azure | Microsoft Docs
description: Empiece a usar directivas de cumplimiento de dispositivos, información general de los estados y los niveles de gravedad, uso del estado En período de gracia, trabajar con el acceso condicional, control de los dispositivos sin una directiva asignada y diferencias de cumplimiento en Azure Portal y el portal clásico en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fbed6185abe7656c3269805d1d5ed09eccbaf05e
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570434"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>Establecimiento de reglas en los dispositivos para permitir el acceso a recursos de su organización con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Muchas soluciones de administración de dispositivos móviles (MDM) ayudan a proteger los datos de la organización exigiendo a los usuarios y dispositivos que cumplan algunos requisitos. En Intune, esta característica se denomina "directivas de cumplimiento". Las directivas de cumplimiento definen las reglas y la configuración que los usuarios y los dispositivos deben cumplir para ser conformes. Cuando se combina con el acceso condicional, los administradores pueden bloquear a los usuarios y dispositivos que no cumplan las reglas.

Por ejemplo, un administrador de Intune puede exigir:

- Que los usuarios finales usen una contraseña para acceder a los datos de la organización en dispositivos móviles
- Que el dispositivo no esté descodificado o descifrado
- Una versión máxima o mínima del sistema operativo en el dispositivo
- Que el dispositivo esté en un nivel de amenaza o bajo el mismo

También puede usar esta característica para supervisar el estado del cumplimiento de los dispositivos de su organización.

> [!IMPORTANT]
> Intune sigue el programa de inserción en el repositorio del dispositivo para todas las evaluaciones de cumplimiento del dispositivo. [Obtenga más información sobre el programa de inserción en el repositorio del dispositivo](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>Funcionamiento de las directivas de cumplimiento de dispositivos con Azure AD

Intune usa el [acceso condicional](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) de Azure Active Directory (AD) (abre otro sitio web de documentación) para ayudar a aplicar el cumplimiento. Cuando un dispositivo se inscribe en Intune, se inicia el proceso de registro de Azure AD y la información del dispositivo se actualiza en Azure AD. Una parte clave de la información es el estado de cumplimiento del dispositivo. Este estado de cumplimiento lo usan las directivas de acceso condicional para bloquear o permitir el acceso al correo electrónico y otros recursos de la organización.

- [¿Qué es la administración de dispositivos en Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/device-management-introduction) es un recurso excelente que explica por qué y cómo se registran los dispositivos en Azure AD.

- En [Acceso condicional](conditional-access.md) y las [formas habituales de usar el acceso condicional](conditional-access-intune-common-ways-use.md) se describe esta característica en relación con Intune.

## <a name="ways-to-use-device-compliance-policies"></a>Formas de usar las directivas de cumplimiento de dispositivos

#### <a name="with-conditional-access"></a>Con acceso condicional

Para los dispositivos que cumplan las reglas de directiva, puede concederles acceso al correo electrónico y a otros recursos de la organización. Si los dispositivos no cumplen las reglas de directiva, no obtendrán acceso a los recursos de la organización. Se trata del acceso condicional.

#### <a name="without-conditional-access"></a>Sin acceso condicional

También puede usar las directivas de cumplimiento de dispositivos sin ningún acceso condicional. Cuando se usan directivas de cumplimiento de forma independiente, los dispositivos de destino se evalúan y su estado se cumplimiento se notifica. Por ejemplo, puede obtener un informe sobre cuántos dispositivos no están cifrados o qué dispositivos están descodificados o descifrados. Cuando usa directivas de cumplimiento sin acceso condicional, no hay ninguna restricción de acceso a los recursos de la organización.

## <a name="ways-to-deploy-device-compliance-policies"></a>Formas de implementar las directivas de cumplimiento de dispositivos

Puede implementar directivas de cumplimiento en los usuarios de grupos de usuarios o en dispositivos de grupos de dispositivos. Cuando se implementa una directiva de cumplimiento en un usuario, se comprueba el cumplimiento de todos los dispositivos del usuario. En Windows 10 versión 1803 y dispositivos más recientes, se recomienda realizar la implementación en grupos de dispositivos *si* el usuario primario no ha inscrito el dispositivo. El uso de grupos de dispositivos en este escenario ayuda con los informes de cumplimiento.

Intune también incluye un conjunto de configuraciones de directivas de cumplimiento integradas. Las directivas integradas siguientes se evalúan en todos los dispositivos inscritos en Intune:

- **Marcar los dispositivos que no tienen asignada una directiva de cumplimiento como**: esta propiedad tiene dos valores:

  - **Compatible**: característica de seguridad desactivada
  - **No compatible** (valor predeterminado): característica de seguridad activada

  Si un dispositivo no tiene asignada una directiva de cumplimiento, se considerará no compatible. De forma predeterminada, los dispositivos están marcados como **No compatible**. Si usa el acceso condicional, se recomienda cambiar la configuración a **No compatible**. Si un usuario final no es compatible porque no se asignó ninguna directiva, en la [aplicación Portal de empresa de Intune](company-portal-app.md) se muestra `No compliance policies have been assigned`.

- **Detección de jailbreak mejorada**: cuando se habilita este valor de configuración, hace que los dispositivos iOS se registren en Intune con mayor frecuencia. Para habilitar esta propiedad se usan los servicios de ubicación del dispositivo, que afectan al uso de la batería. Intune no almacena los datos de ubicación del usuario.

  Para habilitar esta configuración, los dispositivos deben:
  - Habilitar los servicios de ubicación en el nivel de sistema operativo.
  - Permitir que el Portal de empresa use los servicios de ubicación.
  - Evaluar y notificar su estado de jailbreak a Intune al menos una vez cada 72 horas. En caso contrario, el dispositivo se marcará como no compatible. La evaluación se desencadena al abrir la aplicación Portal de empresa de Intune o al mover físicamente los 500 medidores o más del dispositivo. Si el dispositivo no se mueve 500 metros en 72 horas, el usuario tiene que abrir la aplicación Portal de empresa para la evaluación de jailbreak mejorada.

- **Período de validez del estado de cumplimiento (días)**: especifique el período en que los dispositivos informan del estado de todas las directivas de cumplimiento recibidas. Los dispositivos que no proporcionen el estado dentro de este período se tratarán como no conformes. El valor predeterminado es 30 días.

Puede usar estas directivas integradas para supervisar estas configuraciones. Intune también [se actualiza o comprueba si hay actualizaciones](create-compliance-policy.md#refresh-cycle-times) en distintos intervalos, dependiendo de la plataforma del dispositivo. [Preguntas comunes, problemas y su solución con perfiles y directivas de dispositivos en Microsoft Intune](device-profile-troubleshoot.md) es un recurso útil.

Los informes de cumplimiento son una excelente manera de comprobar el estado de los dispositivos. [Supervisión de las directivas de cumplimiento](compliance-policy-monitor.md) incluye algunas instrucciones.

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>Incumplimiento y acceso condicional en las distintas plataformas

En la tabla siguiente se describe cómo administrar la configuración de no conformidad cuando se usa una directiva de cumplimiento con una directiva de acceso condicional.

---------------------------

|**Configuración de directiva**| **Plataforma** |
| --- | ----|
| **Configuración de PIN o contraseña** | - **Android 4.0 y versiones posteriores**: En cuarentena</br>- **Samsung Knox Standard 4.0 y versiones posteriores**: En cuarentena</br>- **Android Enterprise**: En cuarentena</br></br>- **iOS 8.0 y versiones posteriores**: Corregido</br>- **macOS 10.11 y versiones posteriores**: Corregido</br></br>- **Windows 8.1 y versiones posteriores**: Corregido</br>- **Windows Phone 8.1 y versiones posteriores**: Corregido|
| **Cifrado del dispositivo** | - **Android 4.0 y versiones posteriores**: En cuarentena</br>- **Samsung Knox Standard 4.0 y versiones posteriores**: En cuarentena</br>- **Android Enterprise**: En cuarentena</br></br>- **iOS 8.0 y versiones posteriores**: Corregido (estableciendo PIN)</br>- **macOS 10.11 y versiones posteriores**: Corregido (estableciendo PIN)</br></br>- **Windows 8.1 y versiones posteriores**: No disponible</br>- **Windows Phone 8.1 y versiones posteriores**: Corregido |
| **Dispositivo liberado o modificado** | - **Android 4.0 y versiones posteriores**: En cuarentena (no es una configuración)</br>- **Samsung Knox Standard 4.0 y versiones posteriores**: En cuarentena (no es una configuración)</br>- **Android Enterprise**: En cuarentena (no es una configuración)</br></br>- **iOS 8.0 y versiones posteriores**: En cuarentena (no es una configuración)</br>- **macOS 10.11 y versiones posteriores**: No disponible</br></br>- **Windows 8.1 y versiones posteriores**: No disponible</br>- **Windows Phone 8.1 y versiones posteriores**: No disponible |
| **Perfil de correo electrónico** | - **Android 4.0 y versiones posteriores**: No disponible</br>- **Samsung Knox Standard 4.0 y versiones posteriores**: No disponible</br>- **Android Enterprise**: No disponible</br></br>- **iOS 8.0 y versiones posteriores**: En cuarentena</br>- **macOS 10.11 y versiones posteriores**: En cuarentena</br></br>- **Windows 8.1 y versiones posteriores**: No disponible</br>- **Windows Phone 8.1 y versiones posteriores**: No disponible |
| **Versión de SO mínima** | - **Android 4.0 y versiones posteriores**: En cuarentena</br>- **Samsung Knox Standard 4.0 y versiones posteriores**: En cuarentena</br>- **Android Enterprise**: En cuarentena</br></br>- **iOS 8.0 y versiones posteriores**: En cuarentena</br>- **macOS 10.11 y versiones posteriores**: En cuarentena</br></br>- **Windows 8.1 y versiones posteriores**: En cuarentena</br>- **Windows Phone 8.1 y versiones posteriores**: En cuarentena |
| **Versión de SO máxima** | - **Android 4.0 y versiones posteriores**: En cuarentena</br>- **Samsung Knox Standard 4.0 y versiones posteriores**: En cuarentena</br>- **Android Enterprise**: En cuarentena</br></br>- **iOS 8.0 y versiones posteriores**: En cuarentena</br>- **macOS 10.11 y versiones posteriores**: En cuarentena</br></br>- **Windows 8.1 y versiones posteriores**: En cuarentena</br>- **Windows Phone 8.1 y versiones posteriores**: En cuarentena |
| **Atestación de estado de Windows** | - **Android 4.0 y versiones posteriores**: No disponible</br>- **Samsung Knox Standard 4.0 y versiones posteriores**: No disponible</br>- **Android Enterprise**: No disponible</br></br>- **iOS 8.0 y versiones posteriores**: No disponible</br>- **macOS 10.11 y versiones posteriores**: No disponible</br></br>- **Windows 10 y Windows 10 Mobile**: En cuarentena</br>- **Windows 8.1 y versiones posteriores**: En cuarentena</br>- **Windows Phone 8.1 y versiones posteriores**: No disponible |

---------------------------

**Corregido**: el sistema operativo del dispositivo exige compatibilidad. (Por ejemplo, se obliga al usuario a configurar un PIN).

**En cuarentena**: el sistema operativo del dispositivo no exige cumplimiento. Por ejemplo, los dispositivos Android y Android Enterprise no obligan al usuario a cifrar el dispositivo. Si el dispositivo no es conforme, se emprenden las acciones siguientes:

  - El dispositivo se bloquea si se aplica una directiva de acceso condicional al usuario.
  - La aplicación Portal de empresa de Intune notifica al usuario sobre cualquier problema de cumplimiento.

## <a name="azure-classic-portal-vs-azure-portal"></a>Portal clásico de Azure y Portal de Azure

La diferencia principal al usar las directivas de cumplimiento de dispositivos en Azure Portal es la siguiente:

- En Azure Portal, las directivas de cumplimiento se crean por separado para cada plataforma compatible
- En el portal clásico de Azure hay una directiva de cumplimiento de dispositivos común a todas las plataformas compatibles

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are initiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

Las directivas de cumplimiento de dispositivos creadas en el [portal clásico](https://manage.microsoft.com) no aparecen en [Azure Portal](https://portal.azure.com). Pero todavía se destinan a los usuarios y pueden administrarse mediante el portal clásico.

Para usar las características relacionadas con el cumplimiento de dispositivos en Azure Portal, debe crear directivas de cumplimiento de dispositivos en Azure Portal. Si asigna una directiva de cumplimiento de dispositivos en Azure Portal a un usuario al que también se ha asignado una directiva de cumplimiento de dispositivos desde el portal clásico, las directivas de cumplimiento de dispositivos de Azure Portal tendrán prioridad sobre las directivas creadas en el portal clásico.

## <a name="next-steps"></a>Pasos siguientes

- [Cree una directiva](create-compliance-policy.md) y vea los requisitos previos.
- Consulte la configuración de cumplimiento para las distintas plataformas de dispositivos:

  - [Android](compliance-policy-create-android.md)
  - [Android Enterprise](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows 10 y versiones posteriores](compliance-policy-create-windows.md)
  - [Windows 8.1 y Windows Phone 8.1](compliance-policy-create-windows-8-1.md)

- En [Referencia de entidades de directivas](reports-ref-policy.md) se brinda información sobre las entidades de directivas de almacenamiento de datos de Intune.