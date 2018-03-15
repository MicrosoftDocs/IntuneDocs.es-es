---
title: Directivas de cumplimiento de dispositivos de Microsoft Intune
titleSuffix: 
description: "Obtenga información sobre el cumplimiento de dispositivos en Microsoft Intune"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9e3a7bdf3ddf6ad77a82ac6dc7075d696fbe6497
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2018
---
# <a name="get-started-with-microsoft-intune-device-compliance-policies"></a>Introducción a las directivas de cumplimiento de dispositivos de Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Las directivas de cumplimiento de dispositivos de Intune definen las reglas y configuraciones con las que debe cumplir un dispositivo para que Intune lo considere compatible.

Estas son algunas de las reglas:

- Usar una contraseña para acceder a los dispositivos

- Cifrado

- Si el dispositivo está liberado

- Versión de SO mínima requerida

- Versión de SO máxima permitida

- Requerir que el dispositivo se encuentre en el nivel de Mobile Threat Defense

También puede usar directivas de cumplimiento de dispositivos para supervisar el estado de cumplimiento de los dispositivos.

## <a name="device-compliance-requirements"></a>Requisitos de cumplimiento del dispositivo

Los requisitos de cumplimiento son básicamente reglas, como exigir el PIN de un dispositivo o especificar el cifrado como obligatorio o no obligatorio para una directiva de cumplimiento.

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

##  <a name="pre-requisites"></a>Requisitos previos

Debe tener las siguientes suscripciones para usar las directivas de cumplimiento de dispositivos con Intune:

- Intune EMS

- Azure AD Premium

###  <a name="supported-platforms"></a>Plataformas compatibles:

-   Android

-   iOS

-   macOS (versión preliminar)

-   Windows 8.1

-   Windows Phone 8,1

-   Windows 10

> [!IMPORTANT]
> Los dispositivos se deben inscribir en Intune para informar sus estados de cumplimiento.

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>Funcionamiento de las directivas de cumplimiento de dispositivos Intune con Azure AD

Cuando un dispositivo está inscrito en Intune, se produce el proceso de registro de Azure AD, cosa que actualiza los atributos del dispositivo con más información en Azure AD. Una parte clave de la información de un dispositivo es el estado de cumplimiento del dispositivo, que las directivas de acceso condicional usan para bloquear o permitir el acceso al correo electrónico y otros recursos corporativos.

- Más información sobre el [proceso de registro de Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction).

### <a name="assigning-a-resulting-device-configuration-profile-status"></a>Asignación de un estado del perfil de configuración del dispositivo resultante

Si un dispositivo tiene varios perfiles de configuración asignados y distintos estados de cumplimiento para dos o más de dichos perfiles, se debe asignar un único estado de cumplimiento resultante. Esta asignación se basa en un nivel de gravedad conceptual que se asigna a cada estado de cumplimiento. Cada estado de cumplimiento tiene el nivel de gravedad siguiente:


|Estado  |Gravedad  |
|---------|---------|
|Pending     |1|
|Correcto     |2|
|Failed     |3|
|Error     |4|

A continuación, se asigna un estado resultante de dos o más perfiles de configuración seleccionando el nivel de gravedad más alto de todos los perfiles asignados a un dispositivo.

Por ejemplo, pongamos que un dispositivo tiene 3 perfiles asignados: el primero, con el estado Pendiente (gravedad 1); el segundo, con el estado Correcto (gravedad 2) y, el tercero, con el estado Error (gravedad 4). El estado Error tiene el nivel de gravedad más alto, de forma que se asigna como estado de cumplimiento resultante para los 3 perfiles.

### <a name="assigning-an-ingraceperiod-status-for-an-assigned-compliance-policy"></a>Asignación de un estado En período de gracia para una directiva de cumplimiento asignada

El estado En período de gracia de una directiva de cumplimiento es un valor que se determina a partir de la combinación del período de gracia y el estado real de un dispositivo para la directiva de cumplimiento asignada. 

En concreto, si un dispositivo tiene un estado No conforme para una directiva de cumplimiento asignada y si se dan los casos siguientes:

- El dispositivo no tiene asignado ningún período de gracia, de modo que el valor asignado para la directiva de cumplimiento es No conforme.
- El dispositivo tiene un período de gracia que ha expirado, de modo que el valor asignado para la directiva de cumplimiento es No conforme.
- El dispositivo tiene un período de gracia futuro, de modo que el valor asignado para la directiva de cumplimiento es En período de gracia.

En la tabla siguiente se resumen los puntos anteriores:


|Estado de cumplimiento real|Valor del período de gracia asignado|Estado de cumplimiento efectivo|
|---------|---------|---------|
|No conforme |Ningún periodo de gracia asignado |No conforme |
|No conforme |Fecha de ayer|No conforme|
|No conforme |Fecha de mañana|En período de gracia|

Para obtener más información sobre la supervisión de las directivas de cumplimiento de dispositivos, vea [Supervisión de las directivas de cumplimiento de dispositivos Intune](compliance-policy-monitor.md).

### <a name="assigning-a-resulting-compliance-policy-status"></a>Asignación de un estado de directiva de cumplimiento resultante

Si un dispositivo tiene varias directivas de cumplimiento asignadas y distintos estados de cumplimiento para dos o más de dichas directivas, se debe asignar un único estado de cumplimiento resultante. Esta asignación se basa en un nivel de gravedad conceptual que se asigna a cada estado de cumplimiento. Cada estado de cumplimiento tiene el nivel de gravedad siguiente: 

|Estado  |Gravedad  |
|---------|---------|
|Unknown     |1|
|No aplicable     |2|
|Conforme|3|
|En período de gracia|4|
|No conforme|5|
|Error|6|

A continuación, se determina un estado resultante de dos o más directivas de cumplimiento seleccionando el nivel de gravedad más alto de todas las directivas asignadas a un dispositivo.
 
Por ejemplo, pongamos que un dispositivo tiene 3 directivas de cumplimiento asignadas: la primera, con el estado Desconocido (gravedad 1); la segunda, con el estado Conforme (gravedad 3) y, la tercera, con el estado En período de gracia (gravedad 4). El estado En período de gracia tiene el nivel de gravedad más alto, de forma que se asigna como estado de cumplimiento resultante para los 3 perfiles.  

##  <a name="ways-to-use-device-compliance-policies"></a>Formas de usar las directivas de cumplimiento de dispositivos

### <a name="with-conditional-access"></a>Con acceso condicional
Puede usar la directiva de cumplimiento con acceso condicional para permitir que solo los dispositivos que satisfacen una o varias reglas de las directivas de cumplimiento de dispositivos accedan al correo electrónico y otros servicios corporativos.

### <a name="without-conditional-access"></a>Sin acceso condicional
También puede usar las directivas de cumplimiento de dispositivos con independencia del acceso condicional. Cuando se usan directivas de cumplimiento de forma independiente, los dispositivos de destino se evalúan y su estado se cumplimiento se notifica. Por ejemplo, puede obtener un informe sobre cuántos dispositivos no están cifrados o qué dispositivos están liberados. Pero cuando se usan directivas de cumplimiento de manera independiente, no existen restricciones de acceso a los recursos de empresa.

Las directivas de cumplimiento se implementan para los usuarios. Cuando se implementa una directiva de cumplimiento para un usuario, se comprueba el cumplimiento de todos los dispositivos del usuario. Para obtener más información sobre cuánto tiempo tardan los dispositivos móviles en obtener una directiva una vez que esta se ha implementado, consulte [Solución de problemas de perfiles de dispositivo en Microsoft Intune](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

#### <a name="actions-for-non-compliance"></a>Acciones de no cumplimiento

Las acciones en caso de no conformidad permiten configurar una secuencia de acciones ordenadas en el tiempo que se aplican a dispositivos que no cumplen los criterios de la directiva de cumplimiento. Para obtener más información, vea [Acciones automáticas en caso de incumplimiento](actions-for-noncompliance.md).

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>Uso de directivas de cumplimiento de dispositivos en el portal de Intune clásico en comparación con Portal de Azure

Tenga en cuenta las principales diferencias que le permitirán realizar la transición al nuevo flujo de trabajo de las directivas de cumplimiento de dispositivos en Azure Portal.

- En el portal de Azure, las directivas de cumplimiento se crean por separado para cada plataforma compatible.
- En el portal de Intune clásico, había una directiva de cumplimiento de dispositivos común a todas las plataformas compatibles.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>Migración de las directivas de cumplimiento de dispositivos desde el portal de Intune clásico a Azure Portal

Las directivas de cumplimiento de dispositivos creadas en el [portal clásico de Intune](https://manage.microsoft.com) no aparecen en el nuevo [Azure Portal de Intune](https://portal.azure.com). Pero todavía se destinan a los usuarios y pueden administrarse mediante el portal de Intune clásico.

Si quiere aprovechar las nuevas características relacionadas con el cumplimiento de dispositivos en Azure Portal, debe crear directivas de cumplimiento de dispositivos en el mismo Azure Portal. Si asigna una nueva directiva de cumplimiento de dispositivos de Azure Portal a un usuario al que también se ha asignado una directiva de cumplimiento de dispositivos en el portal clásico de Intune, las directivas de cumplimiento de dispositivos de Azure Portal de Intune tienen prioridad sobre las creadas en el portal de Intune clásico.

##  <a name="next-steps"></a>Pasos siguientes

- Cree una directiva de cumplimiento de directivas para las plataformas siguientes:

   - [Android](compliance-policy-create-android.md)
   - [Android for work](compliance-policy-create-android-for-work.md)
   - [iOS](compliance-policy-create-ios.md)
   - [macOS](compliance-policy-create-mac-os.md)
   - [Windows](compliance-policy-create-windows.md)

- Para obtener información sobre las entidades de directivas de almacenamiento de datos de Intune, vea [Referencia de entidades de directivas](reports-ref-policy.md).
