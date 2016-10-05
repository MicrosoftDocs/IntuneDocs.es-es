---
title: Se ven errores al intentar inscribir el dispositivo iOS en Intune | Microsoft Intune
description: 
keywords: 
author: Staciebarker
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
ms.sourcegitcommit: f3ca61178e64feea30e8783f9a2471303dd68378
ms.openlocfilehash: 191ff1347d31c9361a80d8a581ee90a03d02061c


---


# Se ven errores al intentar inscribir el dispositivo iOS en Intune

En la tabla siguiente se muestran los errores que se pueden ver durante la inscripción de un dispositivo iOS en Intune. Comparta este vínculo con el administrador de TI. Para obtener información de contacto, consulte el [sitio web del portal de empresa](http://portal.manage.microsoft.com).

|Mensaje de error|Problema|Qué decirle al administrador de TI|
|-----------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|NoEnrollmentPolicy|No hay ninguna directiva de inscripción.|Compruebe que se han configurado todos los requisitos previos de inscripción, como el certificado de APNs, y que está habilitado "iOS as a platform" (iOS como plataforma). Para obtener instrucciones, consulte [Configurar la administración de dispositivos iOS y Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceCapReached|Ya hay demasiados dispositivos móviles inscritos.|El usuario debe quitar uno de los dispositivos móviles inscritos actualmente desde el portal de empresa para poder inscribir otro. Consulte las instrucciones para el tipo de dispositivo que está usando: [Android](unenroll-your-device-from-intune-android.md), [iOS](unenroll-your-device-from-intune-ios.md) o [Windows](unenroll-your-device-from-intune-windows.md).|
|APNSCertificateNotValid|Hay un problema con el certificado que permite al dispositivo móvil comunicarse con la red de la empresa.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que ha recibido el mensaje **APNSCertificateNotValid** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|El servicio de notificaciones de inserción de Apple (APNS) proporciona un canal para llegar a dispositivos iOS inscritos. Si no se realizaron los pasos para obtener un certificado de APNs o si el certificado de APNs ha expirado, los intentos de inscripción producirán un error y aparecerá este mensaje.<br /><br />Revise la información sobre cómo configurar los usuarios incluida en [Sincronizar Active Directory y agregar usuarios a Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) y [organizar usuarios y dispositivos](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|AccountNotOnboarded|Hay un problema con el certificado que permite al dispositivo móvil comunicarse con la red de la empresa.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que ha recibido el mensaje **APNSNotOnboarded** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|El servicio de notificaciones de inserción de Apple (APNS) proporciona un canal para llegar a dispositivos iOS inscritos. Si no se realizaron los pasos para obtener un certificado de APNs o si el certificado de APNs ha expirado, los intentos de inscripción producirán un error y aparecerá este mensaje.<br /><br />Para obtener más información, consulte [Configurar la administración de dispositivos iOS y Mac con Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).|
|DeviceTypeNotSupported|Es posible que haya intentado realizar la inscripción con un dispositivo que no es iOS. No se admite el tipo de dispositivo móvil que intenta inscribir.<br /><br />Compruebe que el dispositivo ejecuta iOS versión 7.1 o posterior.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que ha recibido el mensaje **DeviceTypeNotSupported** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|Compruebe que el dispositivo de usuario ejecuta iOS versión 7.1 o posterior.|
|UserLicenseTypeInvalid|No puede inscribir su dispositivo móvil porque su cuenta de usuario ya no pertenece a ningún grupo de usuarios requerido.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que ha recibido el mensaje **UserLicenseTypeInvalid** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|Para que un usuario pueda inscribir su dispositivo, debe pertenecer al grupo de usuarios correcto. Este mensaje significa que tiene el tipo de licencia incorrecto para la entidad de administración de dispositivos móviles designada. Por ejemplo, si se ha designado Intune como entidad de administración de dispositivos móviles y el usuario usa una licencia de System Center 2012 R2 Configuration Manager, recibirá este error.<br /><br />Para obtener más información, consulte lo siguiente:<br /><br />Revise [Configurar la administración de dispositivos iOS y Mac con Microsoft Intune](/Intune/Deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) y la información sobre cómo configurar los usuarios incluida en [Sincronizar Active Directory y agregar usuarios a Intune](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-3) y [organizar usuarios y dispositivos](/Intune/Get-Started/start-with-a-paid-subscription-to-microsoft-intune-step-5).|
|MdmAuthorityNotDefined|El administrador de TI necesita configurar la forma en que se administran los dispositivos móviles de la empresa.<br /><br />Póngase en contacto con los administradores de TI, indíqueles que ha recibido el mensaje **MdmAuthorityNotDefined** mientras intentaba inscribir el dispositivo móvil y dígales que consulten la solución de esta tabla.|La entidad de administración de dispositivos móviles no se designó en Intune.<br /><br />Revise el elemento número 1 de la sección "Paso 6: inscribir dispositivos móviles e instalar una aplicación" en [Empezar a trabajar con una versión de prueba de 30 días de Microsoft Intune](/Intune/Understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune).|





<!--HONumber=Sep16_HO1-->


