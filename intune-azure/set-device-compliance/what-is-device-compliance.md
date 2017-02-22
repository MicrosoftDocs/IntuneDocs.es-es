---
title: "Cumplimiento de dispositivos | Versión preliminar de Intune Azure | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: 7693d49e2f0fa6e4aa40b6bb71433a7eaab8dd15
ms.openlocfilehash: a4254503e4e6b86079f862966dee2727934f1ee6


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>¿Qué es el cumplimiento de dispositivos en la versión preliminar de Intune Azure?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Para ayudar a proteger los datos de empresa, debe asegurarse de que los dispositivos usados para acceder a datos y aplicaciones de empresa cumplan ciertas reglas. Estas reglas pueden incluir el uso de un PIN para acceder a los dispositivos y el cifrado de los datos almacenados en ellos. A un conjunto de tales reglas se le denomina una **directiva de cumplimiento**.

##  <a name="how-should-i-use-a-device-compliance-policy"></a>¿Cómo debo usar una directiva de cumplimiento de dispositivo?
Puede usar la directiva de cumplimiento con acceso condicional para permitir que solo los dispositivos que satisfacen las reglas de la directiva de cumplimiento accedan al correo electrónico y otros servicios.

También puede usar la directiva de cumplimiento con independencia del acceso condicional.
Cuando se usan directivas de cumplimiento de forma independiente, los dispositivos de destino se evalúan y su estado se cumplimiento se notifica. Por ejemplo, puede obtener un informe sobre cuántos dispositivos no están cifrados o qué dispositivos están descodificados o descifrados. Pero cuando se usan directivas de cumplimiento de manera independiente, no existen restricciones de acceso a los recursos de empresa.

Las directivas de cumplimiento se implementan para los usuarios. Cuando se implementa una directiva de cumplimiento para un usuario, se comprueba el cumplimiento de todos los dispositivos del usuario. Para más información sobre cuánto tiempo tardan los dispositivos móviles en obtener una directiva una vez que esta se ha implementado, consulte Administración de la configuración y las características de los dispositivos.

##  <a name="concepts"></a>Conceptos
Estos son algunos términos y conceptos que resultan útiles para comprender cómo usar las directivas de cumplimiento.

### <a name="compliance-requirements"></a>Requisitos de cumplimiento
Los requisitos de cumplimiento son básicamente reglas, como exigir el PIN de un dispositivo o especificar el cifrado como obligatorio o no obligatorio para una directiva de cumplimiento.

<!---### Actions for noncompliance

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

##  <a name="differences-between-the-classic-intune-admin-console-and-intune-in-the-azure-portal"></a>Diferencias entre la consola de administración clásica de Intune e Intune en el portal de Azure


Si anteriormente ha usado la consola de administración clásica de Intune, observe las siguientes diferencias para que le ayuden en la transición al nuevo flujo de trabajo de cumplimiento del dispositivo en el portal de Azure:


-   En el portal de Azure, las directivas de cumplimiento se crean por separado para cada plataforma compatible. En la consola de administración de Intune, una directiva de cumplimiento era común a todas las plataformas compatibles.


<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="next-steps"></a>Pasos siguientes

[Introducción a las directivas de cumplimiento](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->



<!--HONumber=Feb17_HO1-->


