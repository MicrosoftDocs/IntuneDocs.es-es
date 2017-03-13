---
title: "Configurar la administración de dispositivos Windows con Microsoft Intune | Microsoft Docs"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos Windows con Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 02/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 255c3e47464ac7670a971881cf399e8e2bb17044
ms.openlocfilehash: 4acbae2aba4cff21286d45cb7cb1691864c281dc
ms.lasthandoff: 02/28/2017


---

# <a name="set-up-windows-device-management"></a>Configurar la administración de dispositivos Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use uno de los métodos siguientes para configurar la inscripción de dispositivos Windows:

- [**Inscripción automática de Windows 10 y Windows 10 Mobile con Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Este método solo es aplicable a dispositivos Windows 10 y Windows 10 Mobile.
 -  Debe tener Azure Active Directory Premium para usar este método. De lo contrario, use el método de inscripción para Windows 8.1 y Windows Phone 8.1.
 -  Si decide no habilitar la inscripción automática, use el método de inscripción para Windows 8.1 y Windows Phone 8.1.


- [**Inscripción de Windows 8.1 y Windows Phone 8.1 mediante la configuración de CNAME**](#set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname)
 - Debe usar este método para inscribir dispositivos Windows 8.1 y Windows Phone 8.1.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>Inscripción de dispositivos Windows 8.1 y Windows Phone 8.1 mediante la configuración de CNAME
Puede dejar que los usuarios instalen e inscriban sus dispositivos con la aplicación Portal de empresa de Intune. Al crear registros de recursos CNAME de DNS, los usuarios se conectan a Intune y se inscriben sin especificar un nombre de servidor.

### <a name="step-1-set-up-intune"></a>Paso 1: Configurar Intune

Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles (MDM)](prerequisites-for-enrollment.md#step-2-set-mdm-authority) como **Microsoft Intune** y luego configure MDM.

### <a name="step-2-create-cnames-optional"></a>Paso 2: Crear CNAME (opcional)

Debe crear registros de recursos DNS **CNAME** para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.


   Aunque la creación de entradas DNS CNAME es opcional, los registros CNAME facilitan la inscripción para los usuarios. Si no se encuentra ningún registro CNAME de inscripción, los usuarios deberán escribir manualmente el nombre del servidor MDM, enrollment.manage.microsoft.com.

   Los registros de recursos CNAME deben tener la siguiente información:

  |TYPE|Nombre de host|Apunta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 hora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 hora|

  `EnterpriseEnrollment-s.manage.microsoft.com`: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

  `EnterpriseRegistration.windows.net`: admite dispositivos Windows 8.1 y Windows 10 Mobile que se registrarán en Azure Active Directory con su cuenta profesional o educativa.

  Si su organización usa varios dominios para las credenciales de usuario, cree registros CNAME para cada dominio.

  Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

### <a name="step-3-verify-cname"></a>Paso 3: Comprobar el CNAME

En la [consola de administración de Intune](http://manage.microsoft.com), elija **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows**. Escriba la dirección URL del dominio verificado del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y luego elija **Probar detección automática**.

### <a name="step-4-tell-your-users-how-to-enroll-their-devices-and-what-to-expect-after-theyre-brought-into-management"></a>Paso 4: Indicar a los usuarios cómo inscribir sus dispositivos y qué esperar cuando se hayan incorporado a la administración.

   Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Windows en Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows).

   Para obtener más información sobre las tareas del usuario final, consulte [Cómo presentar Microsoft Intune a los usuarios finales](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) y [Guía de usuario final para dispositivos Windows](../enduser/using-your-windows-device-with-intune.md).

### <a name="see-also"></a>Consulte también
[Requisitos previos para la inscripción de dispositivos en Microsoft Intune](prerequisites-for-enrollment.md)

