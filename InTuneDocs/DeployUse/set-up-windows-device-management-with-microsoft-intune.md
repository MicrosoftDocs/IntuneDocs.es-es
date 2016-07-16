---
title: "Configurar la administración de dispositivos Windows con Microsoft Intune | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6951ccdb0e37489217ef939f0cbf6fc1133a6d3c
ms.openlocfilehash: c18445385e8361cf01948b583f08e992658a8762


---

# Configurar la administración de dispositivos Windows
Con Intune, puede habilitar la inscripción BYOD (Bring Your Own Device) de dispositivos de equipos Windows para proporcionar acceso al correo electrónico y a las aplicaciones de la empresa. Usado con Azure Active Directory, proporciona una forma rápida y sin intervención del usuario para mostrar los nuevos dispositivos Windows 10 en la administración y tener acceso a los recursos de la empresa sin necesidad de restablecer la imagen inicial del equipo. Una vez inscritos, los usuarios pueden iniciar sesión y se pueden aplicar a sus dispositivos directivas, aplicaciones y opciones de configuración mediante la consola de administración de Intune. También podría interesarle [Set up Windows Phone management with Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md) (Configurar la administración de Windows Phone con Microsoft Intune) o [Manage computers with Intune client software](manage-windows-pcs-with-microsoft-intune.md) (Administrar equipos con software cliente de Intune) mediante el cliente de Intune.

Al crear un CNAME de DNS, los usuarios pueden conectarse e inscribirse en Intune sin especificar un nombre de servidor.

### Configurar la administración de dispositivos Windows

  1.  Debe crear un registro de recursos DNS **CNAME** para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. Si hay más de un dominio comprobado, debe crear un registro CNAME para cada dominio. Los registros de recursos CNAME deben contener la siguiente información:

  |TYPE|Nombre de host|Apunta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 hora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 hora|

    Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

    **EnterpriseEnrollment-s.manage.microsoft.com**: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

    **EnterpriseRegistration.windows.net**: admite dispositivos Windows 8.1 y Windows 10 Mobile que se registrarán con Azure Active Directory con su cuenta profesional o educativa.

  2.  En la [consola de administración de Intune](http://manage.microsoft.com), haga clic en **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows**.
  ![Cuadro de diálogo de administración de dispositivos Windows](../media/enroll-intune-winenr.png)
  3.  Escriba la dirección URL del dominio verificado del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y luego haga clic en **Probar detección automática**.

### Consulte también
[Preparar la inscripción de dispositivos en Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


