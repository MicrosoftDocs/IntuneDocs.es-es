---
title: "Inscripción de dispositivos Windows"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: habilite la administración de dispositivos móviles (MDM) de Intune para dispositivos Windows."
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 02/15/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 7262093700dab3a7befd5b82ac9f8ee3dde22dcf
ms.lasthandoff: 02/18/2017


---

# <a name="enroll-windows-devices"></a>Inscripción de dispositivos Windows 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Use uno de los métodos siguientes para configurar la inscripción de dispositivos Windows:

- [**Inscripción automática de Windows 10 y Windows 10 Mobile con Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Este método solo es aplicable a dispositivos Windows 10 y Windows 10 Mobile.
 -  Debe tener Azure Active Directory Premium para usar este método. De lo contrario, use el método de inscripción para Windows 8.1 y Windows Phone 8.1.
 -  Si decide no habilitar la inscripción automática, use el método de inscripción para Windows 8.1 y Windows Phone 8.1.

- [**Inscripción de Windows 8.1 y Windows Phone 8.1 mediante la configuración de CNAME**](#set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname)
 - Debe usar este método para inscribir dispositivos Windows 8.1 y Windows Phone 8.1.


## <a name="prerequisites"></a>Requisitos previos

Si algunos de los siguientes requisitos previos no están aún en la versión preliminar de Intune Azure, debe realizarlos desde la consola de administración de Intune clásica.

- [Configurar un nombre de dominio personalizado](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Establecer la entidad de administración de dispositivos móviles (MDM) ](set-mdm-authority.md) como **Microsoft Intune**
- [Configurar la aplicación de portal de empresa](/intune-azure/manage-apps/company-portal-app.md)
- Asignar licencias a usuarios

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>Inscripción de dispositivos Windows 8.1 y Windows Phone 8.1 mediante la configuración de CNAME

Puede dejar que los usuarios instalen e inscriban sus dispositivos con la aplicación Portal de empresa de Intune. Al crear registros de recursos CNAME de DNS, los usuarios se conectan a Intune y se inscriben sin especificar un nombre de servidor.

1. **Crear CNAME** (opcional)<br>
 Debe crear registros de recursos DNS **CNAME** para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

    Aunque la creación de entradas DNS CNAME es opcional, los registros CNAME facilitan la inscripción para los usuarios. Si no se encuentra ningún registro CNAME de inscripción, los usuarios deberán escribir manualmente el nombre del servidor MDM, enrollment.manage.microsoft.com.

    Si hay más de un dominio comprobado, debe crear un registro CNAME para cada dominio. Los registros de recursos CNAME deben contener la siguiente información:

    Los registros de recursos CNAME deben tener la siguiente información:

  |TYPE|Nombre de host|Apunta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 hora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 hora|

  `EnterpriseEnrollment-s.manage.microsoft.com`: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

  `EnterpriseRegistration.windows.net`: admite dispositivos Windows 8.1 y Windows 10 Mobile que se registrarán en Azure Active Directory con su cuenta profesional o educativa.

  Si su organización usa varios dominios para las credenciales de usuario, cree registros CNAME para cada dominio.

  Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

2.  **Comprobar el CNAME**<br>En la [consola de administración de Intune](http://manage.microsoft.com), elija **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows Phone**. Escriba la dirección URL del dominio verificado del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y luego elija **Probar detección automática**.

3.  **Pasos opcionales**<br>El paso **Agregar claves de instalación de prueba** no es necesario para Windows 10. <br>El paso **Cargar certificado de firma de código** solo es necesario si va a distribuir a los dispositivos aplicaciones de línea de negocio (LOB) que no están disponibles en la Tienda Windows.

4.  **Indique a los usuarios cómo inscribir sus dispositivos y qué esperar cuando se hayan incorporado a la administración.**

    Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Windows en Intune](https://docs.microsoft.com/en-us/intune/enduser/enroll-your-device-in-intune-windows). También puede enviar a los usuarios a la página que trata sobre [lo que ven los administradores de TI en los dispositivos](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

    Para más información sobre las tareas del usuario final, vea [Recursos sobre la experiencia del usuario final con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune).

No es necesario ningún trabajo adicional a menos que vaya a implementar el portal de empresa en dispositivos.  Puede omitir sin ningún problema los pasos 2 y 3 de la consola de administración.

