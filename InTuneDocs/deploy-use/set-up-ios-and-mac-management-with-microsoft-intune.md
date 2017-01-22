---
title: "Configurar la administración de iOS y Mac | Microsoft Docs"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos iOS, como iPad e iPhone, así como para dispositivos de Mac OS X con Microsoft Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/17/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d2ed7b2e713f5efd4161eb8015ab43c8f97a017b
ms.openlocfilehash: 594b6b66a4c756155e958815b926674e63f07bb5


---

# <a name="set-up-ios-and-mac-device-management"></a>Configurar la administración de dispositivos iOS y Mac

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune permite la administración de dispositivos móviles (MDM) de iPad, iPhone y dispositivos Mac OS X y concede acceso a los usuarios al correo electrónico y las aplicaciones de la empresa. El certificado del Servicio de notificaciones push de Apple (APNs) es necesario para que Intune pueda administrar dispositivos iOS y Mac. Una vez que el certificado se agrega a Intune, los usuarios pueden instalar la aplicación Portal de empresa para inscribir sus dispositivos o el administrador puede configurar la [administración de dispositivos iOS de la empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

1.  **Configurar Intune**<br>
    Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](prerequisites-for-enrollment.md#step-2-set-mdm-authority) como **Microsoft Intune** y configure MDM.

2.  **Obtener una solicitud de firma de certificado**<br>
    Como usuario administrativo, abra la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS y Mac OS X** &gt; **Cargar un certificado de APNs** y luego elija **Descargar la solicitud de certificado de APNs**. Guarde la solicitud de firma de certificado (.csr) en el equipo local. Se utiliza el archivo .csr para solicitar un certificado de relación de confianza desde el portal de certificados push de Apple.

    ![Cuadro de diálogo del certificado de APNs de carga](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Obtener un certificado de servicio de notificaciones de inserción de Apple**<br>
    Vaya al [Portal de certificados push de Apple](http://go.microsoft.com/fwlink/?LinkId=269844) e inicie sesión con el Id. de Apple de empresa para crear el certificado de APNs mediante el archivo .csr. Después de elegir **Cargar** en el portal de certificados push de Apple, recibirá un archivo .json que no se puede usar para APNs. Complete la descarga, vuelva al portal de certificados push de Apple para **Certificados para servidores de terceros** y elija **Descargar**.

    Descargue el certificado de APNs (.pem) y guarde el archivo localmente.

    > [!NOTE]
    > Cada año, necesita renovar (no reemplazar) este certificado de APN. Utilice ese mismo identificador de Apple para iniciar sesión en el portal de certificados push de Apple para renovar el certificado, después, utilizar las mismas instrucciones de este tema para descargar el certificado y, finalmente, cargarlo en Intune.

4.  **Agregar el certificado de APN a Intune**<br>
    En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **iOS y Mac OS X** &gt; **Cargar un certificado de APNs** y luego elija **Cargar el certificado de APNs**. Vaya al archivo de certificado (.pem), elija **Abrir** y luego escriba su **Id. de Apple**. Con el certificado APNs, Intune puede inscribir y administrar dispositivos iOS insertando la directiva en los dispositivos móviles inscritos.

5.  **Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.**

    Para instrucciones sobre la inscripción del usuario final, consulte [Inscribir un dispositivo iOS en Intune](../enduser/enroll-your-device-in-intune-ios.md) o [Inscribir un dispositivo Mac OS X en Intune](../enduser/enroll-your-device-in-intune-macos.md). El proceso de inscripción indica a los usuarios lo que pueden esperar y qué pueden o no ver los administradores de TI en sus dispositivos.

    Para más información acerca de otras tareas de usuario final, consulte estos artículos:
    - [Recursos sobre la experiencia del usuario final con Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Guía de usuario final para dispositivos iOS y Mac](../enduser/using-your-ios-or-macOS-device-with-intune.md)

Si la empresa u organización adquiere dispositivos iOS para los usuarios, estos dispositivos también se pueden inscribir en la administración como [dispositivos iOS propiedad de la empresa](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### <a name="see-also"></a>Véase también
[Requisitos previos para la inscripción con Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Jan17_HO1-->


