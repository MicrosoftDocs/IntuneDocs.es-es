---
title: Cumplimiento de dispositivos
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: use este tema para aprender sobre el cumplimiento de dispositivos en Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: cddeb6bf854b9ffbbc1744d5d164c8ceea34ff49
ms.openlocfilehash: 7d5a1859ef1a373ce424dd4f351fc137c6052fb7
ms.lasthandoff: 03/10/2017


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>¿Qué es el cumplimiento de dispositivos en la versión preliminar de Intune Azure?

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Las directivas de cumplimiento de dispositivos definen las reglas y los valores de configuración que un dispositivo debe cumplir para que se considere conforme a las directivas de acceso condicional de EMS y de Intune. También se pueden usar para supervisar y corregir problemas de cumplimiento con dispositivos. 

Estas son algunas de las reglas:

- Usar una contraseña para acceder a los dispositivos
- Cifrado
- Si el dispositivo está liberado
- Versión de SO mínima requerida
- Versión de SO máxima permitida
- Requerir que el dispositivo se encuentre en el nivel de Mobile Threat Defense

<!---##  Concepts
Following are some terms and concepts that are useful to understanding how to use compliance policies.

### Device compliance requirements
Compliance requirements are essentially rules like requiring a device PIN or encryption that you can specify as required or not required for a compliance policy.

### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be non-compliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

##  <a name="how-should-i-use-a-device-compliance-policy"></a>¿Cómo debo usar una directiva de cumplimiento de dispositivo?

### <a name="using-ems-conditional-access"></a>Usar el acceso condicional de EMS
Puede usar la directiva de cumplimiento con acceso condicional de EMS para permitir que solo los dispositivos que satisfacen una o varias reglas de las directivas de cumplimiento de dispositivos accedan al correo electrónico y otros servicios corporativos.

### <a name="not-using-ems-conditional-access"></a>No usar el acceso condicional de EMS
También puede usar las directivas de cumplimiento de dispositivos con independencia del acceso condicional de EMS.
Cuando se usan directivas de cumplimiento de forma independiente, los dispositivos de destino se evalúan y su estado se cumplimiento se notifica. Por ejemplo, puede obtener un informe sobre cuántos dispositivos no están cifrados o qué dispositivos están liberados. Pero cuando se usan directivas de cumplimiento de manera independiente, no existen restricciones de acceso a los recursos de empresa.

Las directivas de cumplimiento se implementan para los usuarios. Cuando se implementa una directiva de cumplimiento para un usuario, se comprueba el cumplimiento de todos los dispositivos del usuario. Para más información sobre cuánto tiempo tardan los dispositivos móviles en obtener una directiva una vez que esta se ha implementado, consulte Administración de la configuración y las características de los dispositivos.

##  <a name="intune-classic-admin-console-vs-intune-azure-preview-portal"></a>Comparación entre la consola de administración clásica de Intune y el portal de la versión preliminar de Intune Azure

Si ha usado la consola de administración clásica de Intune, observe las siguientes diferencias para que le ayuden en la transición al nuevo flujo de trabajo de las directivas de cumplimiento de dispositivos en Azure Portal:

-   En el portal de Azure, las directivas de cumplimiento se crean por separado para cada plataforma compatible. En la consola de administración de Intune, una directiva de cumplimiento era común a todas las plataformas compatibles.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="next-steps"></a>Pasos siguientes

[Introducción a las directivas de cumplimiento de dispositivos](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->

