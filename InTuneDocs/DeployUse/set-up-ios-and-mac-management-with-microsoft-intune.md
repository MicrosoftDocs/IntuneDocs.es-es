---
title: "Configurar la administración de iOS y Mac | Microsoft Intune"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos iOS, como iPad e iPhone, así como para dispositivos de Mac OS X con Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 06d6c8ce97ba6a259055e94f0eba87f7c5a96531
ms.openlocfilehash: e61e764f4761ab83500ff6f0febe253d427729d9


---

# Configurar la administración de dispositivos iOS y Mac
[Aquí](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md) puede encontrar ayuda para configurar su dispositivo iOS o Mac.

Aplique la administración de dispositivos móviles de Intune de iPad, iPhone y dispositivos Mac OS X y conceda acceso al correo electrónico y las aplicaciones de la empresa. El certificado del Servicio de notificaciones push de Apple (APNs) es necesario para que Intune pueda administrar dispositivos iOS y Mac. Una vez que el certificado se agrega a Intune, los usuarios pueden instalar la aplicación Portal de empresa para inscribir sus dispositivos o el administrador puede configurar la [administración de dispositivos iOS de la empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

1.  **Configurar Intune**<br>
    Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) como **Microsoft Intune** y configure MDM.

2.  **Obtener una solicitud de firma de certificado**<br>
    Como usuario administrativo, abra la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS y Mac OS X** &gt; **Cargar un certificado de APNs** y haga clic en **Descargar la solicitud de certificado de APN**. Guarde la solicitud de firma de certificado (.csr) en el equipo local. Se utiliza el archivo .csr para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.

    ![Cuadro de diálogo del certificado de APNs de carga](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Obtenga un certificado del servicio de notificaciones push de Apple**<br>
    Vaya al [Portal de certificados push de Apple](http://go.microsoft.com/fwlink/?LinkId=269844) e inicie sesión con el Id. de Apple de empresa para crear el certificado de APN mediante el archivo .csr. Después de hacer clic en **Cargar** en el portal de certificados push de Apple, recibirá un archivo .json que no se puede usar para APNs. Complete la descarga y vuelva al portal de certificados de inserción de Apple para **certificados para servidores de terceros** y haga clic en **Descargar**.

    Descargue el certificado de APNs (.pem) y guarde el archivo localmente. Este ID de Apple debe utilizarse en el futuro para renovar el certificado APNs.

4.  **Agregar el certificado de APN a Intune**<br>
    En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS y Mac OS X** &gt; **Cargar un certificado de APNs** y haga clic en **Cargar el certificado de APNs**. **Busque** el archivo de certificado (.pem), haga clic en **Abrir** y, a continuación, escriba su **ID de Apple**. Con el certificado APNs, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos.

5.  **Indique a los usuarios cómo obtener acceso a los recursos de empresa con el Portal de empresa**<br>
    Los usuarios necesitan saber cómo inscribir sus dispositivos y qué esperar una vez que se incorporan a la administración.
    - [Qué decirles a los usuarios finales sobre el uso de Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Guía de usuario final para dispositivos iOS y Mac](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

Si la empresa u organización adquiere dispositivos iOS para los usuarios, estos dispositivos también se pueden inscribir en la administración como [dispositivos iOS propiedad de la empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### Véase también
[Preparar la inscripción de dispositivos en Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


