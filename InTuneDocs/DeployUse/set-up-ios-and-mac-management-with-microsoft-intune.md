---
# required metadata

title: Configurar la administración de iOS y Mac con Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configurar la administración de dispositivos iOS y Mac
Con Microsoft Intune, puede habilitar la inscripción BYOD (Bring Your Own Device) de dispositivos iOS y Mac OS X para proporcionar acceso al correo electrónico y a las aplicaciones de la empresa a los usuarios de iPhone, iPad y Mac. Una vez inscritos, los usuarios pueden instalar la aplicación de portal de empresa de Intune y se pueden aplicar a sus dispositivos directivas mediante la consola de administración de Intune.

Para poder administrar dispositivos iOS con Intune, los dispositivos deben poder comunicarse con Intune. Apple pide que se establezca una relación de confianza con Intune mediante la importación de un certificado de servicio de notificaciones push de Apple (APNs).

1.  **Configurar Intune**<br>
    Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) como **Microsoft Intune** y configure MDM.

2.  **Obtener una solicitud de firma de certificado**<br>
    Como usuario administrativo, abra la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS y Mac OS X** &gt; **Cargar un certificado de APNs** y haga clic en **Descargar la solicitud de certificado de APNs**. Guarde la solicitud de firma de certificado (.csr) en el equipo local. Se utiliza el archivo .csr para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.

    ![Cuadro de diálogo del certificado de APNs de carga](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Obtenga un certificado del servicio de notificaciones push de Apple**<br>
    Vaya al [Portal de certificados push de Apple](http://go.microsoft.com/fwlink/?LinkId=269844) e inicie sesión con el Id. de Apple de empresa para crear el certificado de APN mediante el archivo .csr. Después de hacer clic en **Cargar** en el portal de certificados push de Apple, recibirá un archivo .json que no se puede usar para APNs. Complete la descarga y vuelva al portal de certificados push de Apple para **Certificates for Third-Party Servers** (Certificados para servidores de terceros) y haga clic en **Descargar**..

    Descargue el certificado de APNs (.pem) y guarde el archivo localmente. Este ID de Apple debe utilizarse en el futuro para renovar el certificado APNs.

4.  **Agregar el certificado de APN a Intune**<br>
    En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS y Mac OS X** &gt; **Cargar un certificado de APNs** y haga clic en **Cargar el certificado de APNs**. **Busque** el archivo de certificado (.pem), haga clic en **Abrir** y escriba su **ID de Apple**. Con el certificado APNs, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos.

5.  **Indique a los usuarios cómo obtener acceso a los recursos de empresa con el Portal de empresa**<br>
    Los usuarios necesitan saber cómo inscribir sus dispositivos y qué esperar una vez que se incorporan a la administración. [Qué decirles a los usuarios finales sobre el uso de Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)

Si su empresa u organización adquiere dispositivos iOS para los usuarios, estos dispositivos también se pueden inscribir en la administración como [dispositivos iOS propiedad de la empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)..

### Véase también
[Preparar la inscripción de dispositivos en Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


