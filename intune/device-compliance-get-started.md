---
title: Directivas de cumplimiento de dispositivos en Microsoft Intune - Azure | Microsoft Docs
description: Requisitos para usar directivas de cumplimiento de dispositivos, información general de los estados y los niveles de gravedad, uso del estado En período de gracia, trabajar con el acceso condicional, control de los dispositivos sin una directiva asignada y diferencias de cumplimiento en Azure Portal y el portal clásico en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 806df8077045a4ad81cb7e221bd053059461a2fd
ms.sourcegitcommit: 6f2f2fa70f4e47fa5ad2f3c536ba7116e1bd1d05
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2019
ms.locfileid: "55199411"
---
# <a name="get-started-with-device-compliance-policies-in-intune"></a>Introducción a las directivas de cumplimiento de dispositivos de Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Muchas soluciones de administración de dispositivos móviles (MDM) ayudan a proteger los datos de la organización exigiendo a los usuarios y dispositivos que cumplan algunos requisitos. En Intune, esta característica se denomina "directivas de cumplimiento". Las directivas de cumplimiento definen las reglas y la configuración que los usuarios y los dispositivos deben cumplir para ser conformes. Cuando se combina con el acceso condicional, los administradores pueden bloquear a los usuarios y dispositivos que no cumplan las reglas. Por ejemplo, un administrador de Intune puede exigir:

- Que los usuarios finales usen una contraseña para acceder a los datos de la organización en dispositivos móviles

- Que el dispositivo no esté descodificado o descifrado

- Una versión máxima o mínima del sistema operativo en el dispositivo

- Que el dispositivo esté en un nivel de amenaza o bajo el mismo

También puede usar directivas de cumplimiento de dispositivos para supervisar el estado de cumplimiento en los dispositivos.

> [!IMPORTANT]
> Intune sigue el programa de inserción en el repositorio del dispositivo para todas las evaluaciones de cumplimiento del dispositivo. [Obtenga más información sobre el programa de inserción en el repositorio del dispositivo](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

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

## <a name="prerequisites"></a>Requisitos previos

Para usar las directivas de cumplimiento de dispositivos, asegúrese de lo siguiente:

- Use las siguientes suscripciones:

  - Intune
  - Azure Active Directory (AD) Premium

- Use una plataforma compatible:

  - Android
  - iOS
  - macOS (versión preliminar)
  - Windows 8.1
  - Windows Phone 8,1
  - Windows 10

- Inscriba dispositivos en Intune para ver el estado de cumplimiento

- Inscriba dispositivos en un usuario o realice la inscripción sin un usuario primario. Los dispositivos inscritos en varios usuarios no se admiten.

## <a name="how-device-compliance-policies-work-with-azure-ad"></a>Funcionamiento de las directivas de cumplimiento de dispositivos con Azure AD

Cuando un dispositivo se inscribe en Intune, se inicia el proceso de registro de Azure AD y se actualizan los atributos del dispositivo en Azure AD. Una parte clave de la información es el estado de cumplimiento del dispositivo. Este estado de cumplimiento lo usan las directivas de acceso condicional para bloquear o permitir el acceso al correo electrónico y otros recursos corporativos.

En [Proceso de registro de Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction) se proporciona más información.

## <a name="refresh-cycle-times"></a>Tiempos de ciclo de actualización

Durante la comprobación de cumplimiento, Intune usa el mismo ciclo de actualización que los perfiles de configuración. En general, los tiempos son:

- iOS: cada seis horas.
- macOS: cada seis horas.
- Android: cada ocho horas.
- Equipos con Windows 10 inscritos como dispositivos: cada ocho horas.
- Windows Phone: cada ocho horas.
- Windows 8.1: cada ocho horas.

Una comprobación de cumplimiento se produce con más frecuencia inmediatamente después de que se inscribe un dispositivo.

### <a name="assign-an-ingraceperiod-status"></a>Asignar un estado En período de gracia

El estado En período de gracia de una directiva de cumplimiento es un valor. Este valor se determina mediante la combinación del período de gracia de un dispositivo y el estado real del dispositivo para esa directiva de cumplimiento.

En concreto, si un dispositivo tiene un estado No conforme para una directiva de cumplimiento asignada y si se dan los casos siguientes:

- El dispositivo no tiene asignado ningún período de gracia, de modo que el valor asignado para la directiva de cumplimiento es No conforme
- El dispositivo tiene un período de gracia que ha expirado, de modo que el valor asignado para la directiva de cumplimiento es No conforme
- El dispositivo tiene un período de gracia futuro, de modo que el valor asignado para la directiva de cumplimiento es En período de gracia.

En la siguiente tabla se resumen estos aspectos:

|Estado de cumplimiento real|Valor del período de gracia asignado|Estado de cumplimiento efectivo|
|---------|---------|---------|
|No conforme |Ningún periodo de gracia asignado |No conforme |
|No conforme |Fecha de ayer|No conforme|
|No conforme |Fecha de mañana|En período de gracia|

Para obtener más información sobre la supervisión de las directivas de cumplimiento de dispositivos, vea [Supervisión de las directivas de cumplimiento de dispositivos Intune](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Asignar un estado de directiva de cumplimiento resultante

Si un dispositivo tiene varias directivas de cumplimiento y distintos estados de cumplimiento para dos o más de dichas directivas, se asigna un único estado de cumplimiento resultante. Esta asignación se basa en un nivel de gravedad conceptual que se asigna a cada estado de cumplimiento. Cada estado de cumplimiento tiene el nivel de gravedad siguiente:

|Estado  |Gravedad  |
|---------|---------|
|Unknown     |1|
|No aplicable     |2|
|Conforme|3|
|En período de gracia|4|
|No conforme|5|
|Error|6|

Si un dispositivo tiene varias directivas de cumplimiento, se le asignará el nivel de gravedad más alto de todas las directivas.

Por ejemplo, pongamos que un dispositivo tiene 3 directivas de cumplimiento asignadas: la primera, con el estado Desconocido (gravedad 1); la segunda, con el estado Conforme (gravedad 3) y, la tercera, con el estado En período de gracia (gravedad 4). El estado En período de gracia tiene el nivel de gravedad más alto, de manera que las tres directivas tienen el estado de cumplimiento En período de gracia.

## <a name="ways-to-use-device-compliance-policies"></a>Formas de usar las directivas de cumplimiento de dispositivos

#### <a name="with-conditional-access"></a>Con acceso condicional
Para los dispositivos que cumplan las reglas de directiva, puede concederles acceso al correo electrónico y a otros recursos corporativos. Si los dispositivos no cumplen las reglas de directiva, no obtendrán acceso a los recursos corporativos. Se trata del acceso condicional.

#### <a name="without-conditional-access"></a>Sin acceso condicional
También puede usar las directivas de cumplimiento de dispositivos sin ningún acceso condicional. Cuando se usan directivas de cumplimiento de forma independiente, los dispositivos de destino se evalúan y su estado se cumplimiento se notifica. Por ejemplo, puede obtener un informe sobre cuántos dispositivos no están cifrados o qué dispositivos están descodificados o descifrados. Cuando usa directivas de cumplimiento sin acceso condicional, no hay ninguna restricción de acceso a los recursos de la organización.

## <a name="ways-to-deploy-device-compliance-policies"></a>Formas de implementar las directivas de cumplimiento de dispositivos
Puede implementar directivas de cumplimiento en los usuarios de grupos de usuarios o en dispositivos de grupos de dispositivos. Cuando se implementa una directiva de cumplimiento en un usuario, se comprueba el cumplimiento de todos los dispositivos del usuario. En Windows 10 versión 1803 y dispositivos más recientes, se recomienda realizar la implementación en grupos de dispositivos *si* el usuario primario no ha inscrito el dispositivo. El uso de grupos de dispositivos en este escenario ayuda con los informes de cumplimiento.

Un conjunto de configuración de directivas de cumplimiento integrada (**Intune** > **Conformidad de dispositivos**) se evalúa en todos los dispositivos inscritos en Intune. Entre ellos se incluyen los siguientes:

- **Marcar los dispositivos que no tienen asignada una directiva de cumplimiento como**: esta propiedad tiene dos valores:

  - **Compatible**: característica de seguridad desactivada
  - **No compatible** (valor predeterminado): característica de seguridad activada

  Si un dispositivo no tiene asignada una directiva de cumplimiento, se considerará no compatible. De forma predeterminada, los dispositivos están marcados como **No compatible**. Si usa el acceso condicional, se recomienda cambiar la configuración a **No compatible**. Si un usuario final no es compatible porque no se ha asignado una directiva, en el Portal de empresa se muestra `No compliance policies have been assigned`.

- **Detección de jailbreak mejorada**: cuando se habilita este valor de configuración, hace que los dispositivos iOS se registren en Intune con mayor frecuencia. Para habilitar esta propiedad se usan los servicios de ubicación del dispositivo, que afectan al uso de la batería. Intune no almacena los datos de ubicación del usuario.

  Para habilitar esta configuración, los dispositivos deben:
  - Habilitar los servicios de ubicación en el nivel de sistema operativo
  - Permitir que el Portal de empresa use los servicios de ubicación
  - Evaluar y notificar su estado de jailbreak a Intune al menos una vez cada 72 horas. En caso contrario, el dispositivo se marcará como no compatible. La evaluación se desencadena al abrir la aplicación Portal de empresa o al mover físicamente los 500 medidores o más del dispositivo. Si el dispositivo no se mueve 500 metros en 72 horas, el usuario tiene que abrir la aplicación Portal de empresa para la evaluación de jailbreak mejorada.

- **Período de validez del estado de cumplimiento (días)**: especifique el período en que los dispositivos informan del estado de todas las directivas de cumplimiento recibidas. Los dispositivos que no proporcionen el estado dentro de este período se tratarán como no conformes. El valor predeterminado es 30 días.

Todos los dispositivos tienen una **Directiva de cumplimiento de dispositivos integrada** (Azure Portal > Conformidad de dispositivos > Cumplimiento de directiva). Use esta directiva integrada para supervisar estas opciones.

Para obtener información sobre el tiempo que tardan los dispositivos móviles en obtener una directiva una vez que esta se ha implementado, vea [Solución de problemas de perfiles de dispositivo](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

Los informes de cumplimiento son una excelente manera de comprobar el estado de los dispositivos. Vea [Supervisión de las directivas de cumplimiento](compliance-policy-monitor.md) para obtener instrucciones.

### <a name="actions-for-noncompliance"></a>Acciones en caso de incumplimiento
Puede configurar una secuencia de acciones ordenadas en el tiempo que se aplican a dispositivos que no cumplen los criterios de la directiva de cumplimiento. Estas acciones en caso de incumplimiento se pueden automatizar, tal y como se describe en [Automatización de acciones en caso de incumplimiento](actions-for-noncompliance.md).

## <a name="azure-classic-portal-vs-azure-portal"></a>Portal clásico de Azure y Portal de Azure

La diferencia principal al usar las directivas de cumplimiento de dispositivos en Azure Portal es la siguiente:

- En Azure Portal, las directivas de cumplimiento se crean por separado para cada plataforma compatible
- En el portal clásico de Azure hay una directiva de cumplimiento de dispositivos común a todas las plataformas compatibles

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

## <a name="device-compliance-policies-in-the-classic-portal-and-azure-portal"></a>Directivas de cumplimiento de dispositivos en el portal clásico y en Azure Portal

Las directivas de cumplimiento de dispositivos creadas en el [portal clásico](https://manage.microsoft.com) no aparecen en [Azure Portal](https://portal.azure.com). Pero todavía se destinan a los usuarios y pueden administrarse mediante el portal clásico.

Para usar las características relacionadas con el cumplimiento de dispositivos en Azure Portal, debe crear directivas de cumplimiento de dispositivos en Azure Portal. Si asigna una directiva de cumplimiento de dispositivos en Azure Portal a un usuario al que también se ha asignado una directiva de cumplimiento de dispositivos desde el portal clásico, las directivas de cumplimiento de dispositivos de Azure Portal tendrán prioridad sobre las directivas creadas en el portal clásico.

## <a name="next-steps"></a>Pasos siguientes

- Cree una directiva de cumplimiento de directivas para las plataformas siguientes:

  - [Android](compliance-policy-create-android.md)
  - [Perfil de trabajo Android](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Para obtener información sobre las entidades de directivas de almacenamiento de datos de Intune, vea [Referencia de entidades de directivas](reports-ref-policy.md).
