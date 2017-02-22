---
title: "Configurar la administración de dispositivos Windows con Microsoft Intune | Microsoft Docs"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos Windows con Microsoft Intune."
keywords: 
author: staciebarker
manager: stabar
ms.date: 02/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 45c32cf08e4d6fd570af287ed64411edc9d9b394
ms.openlocfilehash: e020ac2a4f600a94e7409e04c4c48f0c405c56cf


---

# <a name="set-up-windows-device-management"></a>Configurar la administración de dispositivos Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use uno de los métodos siguientes para configurar la inscripción de dispositivos Windows:

- **[Inscripción automática de Windows 10 y Windows 10 Mobile con Azure Active Directory Premium](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)** 
 -  Este método solo es aplicable a dispositivos Windows 10 y Windows 10 Mobile.
 -  Debe tener Azure Active Directory Premium para usar este método. De lo contrario, use el método de inscripción para Windows 8.1 y Windows Phone 8.1.
 -  Si decide no habilitar la inscripción automática, use el método de inscripción para Windows 8.1 y Windows Phone 8.1.


- **[Inscripción de Windows 8.1 y Windows Phone 8.1 mediante la configuración de CNAME](#set-up-windows-8--1-and-windows-phone-8--1-enrollment-by-configuring-cname)** 
 - Debe usar este método para inscribir dispositivos Windows 8.1 y Windows Phone 8.1.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>Inscripción de dispositivos Windows 8.1 y Windows Phone 8.1 mediante la configuración de CNAME
Puede dejar que los usuarios instalen e inscriban sus dispositivos con la aplicación Portal de empresa de Intune. Al crear registros de recursos CNAME de DNS, los usuarios se conectan a Intune y se inscriben sin especificar un nombre de servidor.

1. **Configurar Intune**<br>
Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles (MDM)](prerequisites-for-enrollment.md#step-2-set-mdm-authority) como **Microsoft Intune** y luego configure MDM.

2. **Crear CNAME** (opcional)<br>
Debe crear registros de recursos DNS **CNAME** para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

    Aunque la creación de entradas DNS CNAME es opcional, los registros CNAME facilitan la inscripción para los usuarios. Si no se encuentra ningún registro CNAME de inscripción, los usuarios deberán escribir manualmente el nombre del servidor MDM, enrollment.manage.microsoft.com.    

    Si tiene ahora un CNAME en el DNS que redirija EnterpriseEnrollment.contoso.com a manage.microsoft.com, sugerimos que lo reemplace por un CNAME en el DNS que redirija EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com. Se recomienda este cambio, porque en una versión futura el punto de conexión manage.microsoft.com estará en desuso para las inscripciones.

    Los registros de recursos CNAME deben tener la siguiente información:

  |TYPE|Nombre de host|Apunta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 hora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 hora|

  `EnterpriseEnrollment-s.manage.microsoft.com`: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

  `EnterpriseRegistration.windows.net`: admite dispositivos Windows 8.1 y Windows 10 Mobile que se registrarán en Azure Active Directory con su cuenta profesional o educativa.

  Si su organización usa varios dominios para las credenciales de usuario, cree registros CNAME para cada dominio.

  Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

3.  **Comprobar el CNAME**<br>En la [consola de administración de Intune](http://manage.microsoft.com), elija **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows**. Escriba la dirección URL del dominio verificado del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y luego elija **Probar detección automática**.

4.  **Indique a los usuarios cómo inscribir sus dispositivos y qué esperar cuando se hayan incorporado a la administración.**

    Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Windows en Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows).

    Para más información sobre las tareas del usuario final, vea [Recursos sobre la experiencia del usuario final con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune).


### <a name="see-also"></a>Consulte también
[Requisitos previos para la inscripción de dispositivos en Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Feb17_HO2-->


