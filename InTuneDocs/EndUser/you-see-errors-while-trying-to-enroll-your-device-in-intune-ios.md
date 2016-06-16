---
# required metadata

title: Observa errores al intentar inscribir un dispositivo iOS en Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58

# optional metadata

ROBOTS: noindex
#audience:
#ms.devlang:
ms.reviewer: esmich
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Observa errores al intentar inscribir un dispositivo iOS en Intune

En la siguiente tabla se muestran los errores que puede encontrar durante la inscripción de un dispositivo iOS en Intune. Comparta este vínculo con el administrador de TI. Si no encuentra la información de contacto del administrador de la TI, vea si aparece en el [sitio web del portal de empresa](http://portal.manage.microsoft.com).

|Mensaje de error|Problema|Qué decirle al administrador de TI|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|DeviceCapReached|Ya hay demasiados dispositivos móviles inscritos.|El usuario debe quitar uno de los dispositivos móviles actualmente inscritos desde el Portal de empresa antes de inscribir otro.|
|APNSCertificateNotValid|Existe un problema con el certificado que permite al dispositivo móvil comunicarse con la red de empresa.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que recibió el mensaje **APNSCertificateNotValid** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|El servicio de notificaciones de inserción de Apple (APNS) proporciona un canal para llegar a dispositivos iOS inscritos. Si no se realizaron los pasos para obtener un certificado de APNS o ha expirado el certificado de APNS, los intentos de inscripción producirán un error y aparecerá este mensaje.<br /><br />Repase la información sobre cómo configurar usuarios en [Sync Active Directory and add users to Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) (Sincronizar Active Directory y agregar usuarios a Intune) y [Organizing users and devices](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5) (Organizar usuarios y dispositivos).|
|AccountNotOnboarded|Existe un problema con el certificado que permite al dispositivo móvil comunicarse con la red de empresa.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que recibió el mensaje **APNSNotOnboarded** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|El servicio de notificaciones de inserción de Apple (APNS) proporciona un canal para llegar a dispositivos iOS inscritos. Si no se realizaron los pasos para obtener un certificado de APNS o ha expirado el certificado de APNS, los intentos de inscripción producirán un error y aparecerá este mensaje.<br /><br />Para más información, vea [Set up iOS and Mac management with Microsoft Intune](/Intune/Deployuse/set-up-ios-and-mac-management-with-microsoft-intune) (Configurar la administración de iOS y Mac con Microsoft Intune).|
|DeviceTypeNotSupported|Es posible que haya intentado inscribirse con un dispositivo que no sea iOS. No se admite el tipo de dispositivo móvil que intenta inscribir.<br /><br />Compruebe que el dispositivo ejecute la versión 7.1 de iOS o una posterior.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que recibió el mensaje **DeviceTypeNotSupported** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|Compruebe que el dispositivo del usuario ejecute la versión 7.1 de iOS o una posterior.|
|UserLicenseTypeInvalid|No puede inscribir el dispositivo móvil porque la cuenta de usuario ya no pertenece a ningún grupo de usuarios requerido.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que recibió el mensaje **UserLicenseTypeInvalid** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|Antes de que los usuarios pueden inscribir los dispositivos, deben ser miembros del grupo de usuarios correcto. Este mensaje significa que tienen el tipo de licencia incorrecto para la entidad de administración de dispositivos móviles designada. Por ejemplo, si Intune se ha designado como la entidad de administración de dispositivos móviles y se usa una licencia de System Center 2012 R2 Configuration Manager, verá este error.<br /><br />Revise lo siguiente para más información:<br /><br />Vea [Set up iOS and Mac management with Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) (Configurar la administración de iOS y Mac con Microsoft Intune) e información sobre cómo configurar usuarios en [Sync Active Directory and add users to Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3 (Sincronizar Active Directory y agregar usuarios a Intune) y [Organizing users and devices](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5) (Organizar usuarios y dispositivos).|
|MdmAuthorityNotDefined|Es necesario que el administrador de TI configure la forma en que se administran los dispositivos móviles de la empresa.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que recibió el mensaje **MdmAuthorityNotDefined** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|La entidad de administración de dispositivos móviles no se ha designado en Intune.<br /><br />Revise el primer elemento de la sección "Paso 6: inscribir dispositivos móviles e instalar una aplicación" en [Empezar a trabajar con una versión de prueba de 30 días de Microsoft Intune](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune).|

### Consulte también
[Using your iOS or Mac OS X device with Intune](using-your-ios-or-mac-os-x-device-with-intune.md)

<!--HONumber=Jun16_HO1-->


