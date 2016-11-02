---
title: Observa errores al intentar inscribir un dispositivo iOS en Intune | Microsoft Intune
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 92a8d06d-0ecb-4912-898b-993e8eaf4e58
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 016449720f6e77b8862fcaa232d252eefa8b20b3
ms.openlocfilehash: 5b00e171bf7f4fb8401c77b9409c1747f08a158c


---


# <a name="you-see-errors-while-trying-to-enroll-your-ios-device-in-intune"></a>Observa errores al intentar inscribir un dispositivo iOS en Intune

En la siguiente tabla se muestran los errores que puede encontrar durante la inscripción de un dispositivo iOS en Intune. Comparta este vínculo con el administrador de TI. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).

|Mensaje de error|Problema|Qué decirle al administrador de TI|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|Ninguna directiva de inscripción|Compruebe que todos los requisitos previos de inscripción, como el certificado Apple Push Notification Service (APNs), se han configurado y que "iOS como plataforma" está habilitado. Para obtener instrucciones, consulte [Configurar la administración de dispositivos iOS y Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceCapReached|Ya hay demasiados dispositivos móviles inscritos.|El usuario debe quitar uno de los dispositivos móviles actualmente inscritos desde el Portal de empresa antes de inscribir otro. Consulte las instrucciones del tipo de dispositivo que usa: [Android](unenroll-your-device-from-intune-android.md), [iOS](unenroll-your-device-from-intune-ios.md), [Windows](unenroll-your-device-from-intune-windows.md).|
|APNSCertificateNotValid|Existe un problema con el certificado que permite al dispositivo móvil comunicarse con la red de empresa.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que ha recibido el mensaje **APNSCertificateNotValid** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|Apple Push Notification Service (APNs) proporciona un canal para llegar a dispositivos iOS inscritos. Si no se han realizado los pasos para obtener un certificado de APNs o este ha expirado, los intentos de inscripción producirán un error y aparecerá este mensaje.<br /><br />Consulte la información sobre cómo configurar usuarios en [Sincronizar Active Directory y agregar usuarios a Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) y [Organizar usuarios y dispositivos](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|AccountNotOnboarded|Existe un problema con el certificado que permite al dispositivo móvil comunicarse con la red de empresa.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que ha recibido el mensaje **APNSNotOnboarded** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|Apple Push Notification Service (APNs) proporciona un canal para llegar a dispositivos iOS inscritos. Si no se han realizado los pasos para obtener un certificado de APNs o este ha expirado, los intentos de inscripción producirán un error y aparecerá este mensaje.<br /><br />Para más información, consulte [Configurar la administración de dispositivos iOS y Mac con Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceTypeNotSupported|Es posible que haya intentado inscribirse con un dispositivo que no sea iOS. No se admite el tipo de dispositivo móvil que intenta inscribir.<br /><br />Compruebe que el dispositivo ejecute la versión 8.0 de iOS o una posterior.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que ha recibido el mensaje **DeviceTypeNotSupported** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|Compruebe que el dispositivo del usuario ejecute la versión 8.0 de iOS o una posterior.|
|UserLicenseTypeInvalid|No puede inscribir el dispositivo móvil porque la cuenta de usuario ya no pertenece a ningún grupo de usuarios requerido.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que ha recibido el mensaje **UserLicenseTypeInvalid** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|Antes de que los usuarios puedan inscribir los dispositivos, deben ser miembros del grupo de usuarios correcto. Este mensaje significa que tienen el tipo de licencia incorrecto para la entidad de administración de dispositivos móviles designada. Por ejemplo, si Intune se ha designado como la entidad de administración de dispositivos móviles y se usa una licencia de System Center 2012 R2 Configuration Manager, verá este error.<br /><br />Revise lo siguiente para más información:<br /><br />Consulte [Configurar la administración de iOS y Mac con Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) y la información sobre cómo configurar usuarios en [Sincronizar Active Directory y agregar usuarios a Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) y [Organizar usuarios y dispositivos](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|MdmAuthorityNotDefined|Es necesario que el administrador de TI configure la forma en que se administran los dispositivos móviles de la empresa.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que ha recibido el mensaje **MdmAuthorityNotDefined** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|La entidad de administración de dispositivos móviles no se ha designado en Intune.<br /><br />Revise el primer elemento de la sección "Paso 6: inscribir dispositivos móviles e instalar una aplicación" en [Empezar a trabajar con una versión de prueba de 30 días de Microsoft Intune](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune).|



<!--HONumber=Oct16_HO2-->


