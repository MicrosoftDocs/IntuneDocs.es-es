---
title: Directivas de cumplimiento de dispositivos Intune
titleSuffix: Azure portal
description: Use este tema para aprender sobre el cumplimiento de dispositivos en Microsoft Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aa78383233950e342c5ab0f83095bba3c8fda1f9
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="get-started-with-intune-device-compliance-policies"></a>Introducción a las directivas de cumplimiento de dispositivos de Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="what-is-device-compliance-in-intune"></a>¿Qué es el cumplimiento de dispositivos en Intune?

Las directivas de cumplimiento de dispositivos Intune definen las reglas y configuraciones con las que debe cumplir un dispositivo para que Intune lo considere compatible.

Estas son algunas de las reglas:

- Usar una contraseña para acceder a los dispositivos

- Cifrado

- Si el dispositivo está liberado

- Versión de SO mínima requerida

- Versión de SO máxima permitida

- Requerir que el dispositivo se encuentre en el nivel de Mobile Threat Defense

También puede usar directivas de cumplimiento de dispositivos para supervisar el estado de cumplimiento de los dispositivos.

### <a name="device-compliance-requirements"></a>Requisitos de cumplimiento del dispositivo

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

Cuando un dispositivo está inscrito en Intune, se produce el proceso de registro de Azure AD, el que actualiza los atributos del dispositivo con más información en Azure AD. Parte clave de la información de un dispositivo es el estado de cumplimiento del dispositivo, que las directivas de acceso condicional usan para bloquear o permitir el acceso al correo electrónico y otros recursos corporativos.

- Más información sobre el [proceso de registro de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-overview).

##  <a name="ways-to-use-device-compliance-policies"></a>Formas de usar las directivas de cumplimiento de dispositivos

### <a name="with-conditional-access"></a>Con acceso condicional
Puede usar la directiva de cumplimiento con acceso condicional para permitir que solo los dispositivos que satisfacen una o varias reglas de las directivas de cumplimiento de dispositivos accedan al correo electrónico y otros servicios corporativos.

### <a name="without-conditional-access"></a>Sin acceso condicional
También puede usar las directivas de cumplimiento de dispositivos con independencia del acceso condicional. Cuando se usan directivas de cumplimiento de forma independiente, los dispositivos de destino se evalúan y su estado se cumplimiento se notifica. Por ejemplo, puede obtener un informe sobre cuántos dispositivos no están cifrados o qué dispositivos están liberados. Pero cuando se usan directivas de cumplimiento de manera independiente, no existen restricciones de acceso a los recursos de empresa.

Las directivas de cumplimiento se implementan para los usuarios. Cuando se implementa una directiva de cumplimiento para un usuario, se comprueba el cumplimiento de todos los dispositivos del usuario. Para más información sobre cuánto tiempo tardan los dispositivos móviles en obtener una directiva una vez que esta se ha implementado, consulte Administración de la configuración y las características de los dispositivos.

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>Uso de directivas de cumplimiento de dispositivos en el portal de Intune clásico en comparación con Portal de Azure

Tenga en cuenta las principales diferencias que le permitirán realizar la transición al nuevo flujo de trabajo de las directivas de cumplimiento de dispositivos en Azure Portal.

- En el portal de Azure, las directivas de cumplimiento se crean por separado para cada plataforma compatible.
- En el portal de Intune clásico, había una directiva de cumplimiento de dispositivos común a todas las plataformas compatibles.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>Migración de las directivas de cumplimiento de dispositivos desde el portal de Intune clásico a Azure Portal

Las directivas de cumplimiento de dispositivos creadas en el [portal clásico de Intune](https://manage.microsoft.com) no aparecerán en [Azure Portal de Intune](https://portal.azure.com). Pero todavía se destinan a los usuarios y pueden administrarse mediante el portal de Intune clásico.

Si desea aprovechar las nuevas características relacionadas con el cumplimiento de dispositivos en Azure Portal, debe crear nuevas directivas de cumplimiento de dispositivos en el mismo Azure Portal. Si asigna una nueva directiva de cumplimiento de dispositivos de Azure Portal a un usuario al que también se ha asignado una directiva de cumplimiento de dispositivos en el portal clásico de Intune, las directivas de cumplimiento de dispositivos de Azure Portal de Intune tienen prioridad sobre las creadas en el portal de Intune clásico.

##  <a name="next-steps"></a>Pasos siguientes

Cree una directiva de cumplimiento de directivas para las plataformas siguientes:

- [Android](compliance-policy-create-android.md)
- [Android for work](compliance-policy-create-android-for-work.md)
- [iOS](compliance-policy-create-ios.md)
- [macOS](compliance-policy-create-mac-os.md)
- [Windows](compliance-policy-create-windows.md)
