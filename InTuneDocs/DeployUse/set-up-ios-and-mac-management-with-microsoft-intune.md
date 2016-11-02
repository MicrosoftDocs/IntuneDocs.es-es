---
title: "Configurar la administración de iOS y Mac | Microsoft Intune"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos iOS, como iPad e iPhone, así como para dispositivos de Mac OS X con Microsoft Intune."
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: b3f6323912707d56d23380217a07e6474593d83f
ms.openlocfilehash: f93f7bfe99e878691dccd24c124a781c8607e7c6


---

# Configurar la administración de dispositivos iOS y Mac
Para obtener ayuda para configurar el dispositivo Mac o iOS, vea [Uso de un dispositivo iOS o Mac OS X con Intune](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md).

Intune permite la administración de dispositivos móviles (MDM) de iPad, iPhone y dispositivos Mac OS X y concede acceso a los usuarios al correo electrónico y las aplicaciones de la empresa. El certificado del Servicio de notificaciones push de Apple (APNs) es necesario para que Intune pueda administrar dispositivos iOS y Mac. Una vez que el certificado se agrega a Intune, los usuarios pueden instalar la aplicación Portal de empresa para inscribir sus dispositivos o el administrador puede configurar la [administración de dispositivos iOS de la empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

1.  **Configurar Intune**<br>
    Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](prerequisites-for-enrollment.md#set-mobile-device-management-authority) como **Microsoft Intune** y configure MDM.

2.  **Obtener una solicitud de firma de certificado**<br>
    Como usuario administrativo, abra la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS y Mac OS X** &gt; **Cargar un certificado de APNs** y luego elija **Descargar la solicitud de certificado de APNs**. Guarde la solicitud de firma de certificado (.csr) en el equipo local. Se utiliza el archivo .csr para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.

    ![Cuadro de diálogo del certificado de APNs de carga](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Obtenga un certificado del servicio de notificaciones push de Apple**<br>
    Vaya al [Portal de certificados push de Apple](http://go.microsoft.com/fwlink/?LinkId=269844) e inicie sesión con el Id. de Apple de empresa para crear el certificado de APNs mediante el archivo .csr. Después de elegir **Cargar** en el portal de certificados push de Apple, recibirá un archivo .json que no se puede usar para APNs. Complete la descarga, vuelva al portal de certificados push de Apple para **Certificados para servidores de terceros** y elija **Descargar**.

    Descargue el certificado de APNs (.pem) y guarde el archivo localmente. Este Id. de Apple debe usarse en el futuro para renovar el certificado de APNs.

4.  **Agregar el certificado de APN a Intune**<br>
    En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS y Mac OS X** &gt; **Cargar un certificado de APNs** y luego elija **Cargar el certificado de APNs**. Vaya al archivo de certificado (.pem), elija **Abrir** y luego escriba su **Id. de Apple**. Con el certificado APNs, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos.

5.  **Indique a los usuarios cómo obtener acceso a los recursos de empresa con el Portal de empresa**<br>
    Los usuarios necesitan saber cómo inscribir sus dispositivos y qué esperar una vez que se incorporan a la administración.
    - [Qué decirles a los usuarios finales sobre el uso de Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Guía de usuario final para dispositivos iOS y Mac](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

Si la empresa u organización adquiere dispositivos iOS para los usuarios, estos dispositivos también se pueden inscribir en la administración como [dispositivos iOS propiedad de la empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### Consulte también
[Requisitos previos para la inscripción con Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Oct16_HO3-->


