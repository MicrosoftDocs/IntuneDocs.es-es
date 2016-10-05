---
title: "Configurar la administración de Windows 10 Mobile y Windows Phone | Microsoft Intune"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos Windows 10 Mobile o Windows Phone con Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: d88405e913fe61cef2c297f9d50408e10674cf3f


---


# Configurar la administración de Windows Phone y Windows 10 Mobile con Microsoft Intune

Como administrador de Intune, puede habilitar la inscripción y administración de los dispositivos Windows 10 Mobile y Windows Phone de dos maneras:

- **[Inscripción automática con Azure AD](#azure-active-directory-enrollment)**: los usuarios de Windows 10 y Windows 10 Mobile inscriben sus dispositivos agregando al dispositivo una cuenta profesional o educativa
- **[Inscripción de Portal de empresa](#company-portal-app-enrollment)**: los dispositivos que ejecutan Windows Phone 8.1 y versiones posteriores se inscriben descargando e instalando la aplicación de Portal de empresa y escribiendo en la aplicación las credenciales de su cuenta profesional o educativa.


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## Inscripción de la aplicación de Portal de empresa
Puede permitir que los usuarios inscriban sus dispositivos instalándolos e inscribiéndolos con la aplicación de Portal de empresa. Al crear un CNAME de DNS, los usuarios pueden conectarse e inscribirse en Intune sin especificar un nombre de servidor. Si administra dispositivos Windows Phone 8.0 o necesita implementar el portal de empresa en dispositivos Windows Phone, también debe descargar y firmar la aplicación de portal de empresa. Consulte [Set up Windows Phone 8.0 management (Configurar la administración de Windows Phone 8.0)](set-up-windows-phone-8.0-management-with-microsoft-intune.md).

1.  **Configurar Intune**<br>Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles](prerequisites-for-enrollment.md#set-mobile-device-management-authority) como **Microsoft Intune** y configure MDM.

2.  **Crear CNAME** (opcional)<br>Debe crear registros de recursos DNS **CNAME** para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a manage.microsoft.com. Si hay más de un dominio comprobado, debe crear un registro CNAME para cada dominio. Los registros de recursos CNAME deben contener la siguiente información:

  |TYPE|Nombre de host|Apunta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 hora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 hora|
  Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

  `EnterpriseEnrollment-s.manage.microsoft.com` – Admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

  `EnterpriseRegistration.windows.net` – Admite dispositivos Windows 8.1 y Windows 10 Mobile que se registrarán en Azure Active Directory con su cuenta profesional o educativa.

  Si su organización usa varios dominios para las credenciales de usuario, cree registros CNAME para cada dominio.

  Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

3.  **Comprobar el CNAME**<br>En la [consola de administración de Intune](http://manage.microsoft.com), haga clic en **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows Phone**. Escriba la dirección URL del dominio verificado del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y luego haga clic en **Probar detección automática**.

    ![Configurar la administración de dispositivos móviles para el cuadro de diálogo de Windows](../media/windows-phone-enrollment.png)

4.  **Pasos opcionales**<br>El paso **Agregar claves de instalación de prueba** no es necesario para Windows 10. El paso **Cargar certificado de firma de código** solo es necesario si va a distribuir aplicaciones de línea de negocio (LOB) a dispositivos que no están disponibles en la Tienda Windows. [Obtener más información](set-up-windows-phone-8.0-management-with-microsoft-intune.md)

5.  **Informar a los usuarios**<br>Los usuarios necesitan saber cómo inscribir sus dispositivos y qué esperar una vez que se incorporan a la administración.
    - [Qué decirles a los usuarios finales sobre el uso de Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Guía de usuario final para dispositivos Windows](../enduser/using-your-windows-device-with-intune.md)

No es necesario ningún trabajo adicional a menos que vaya a implementar el portal de empresa en dispositivos.  Puede omitir sin ningún problema los pasos 2 y 3 de la consola de administración.



<!--HONumber=Sep16_HO4-->


