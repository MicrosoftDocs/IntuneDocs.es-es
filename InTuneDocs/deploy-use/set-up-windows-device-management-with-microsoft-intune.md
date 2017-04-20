---
title: "Configurar la administración de dispositivos Windows con Microsoft Intune | Microsoft Docs"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos Windows con Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 771aed4e1c57171183b9a9ea7d9e0f702dc1859c
ms.openlocfilehash: f6014c5500b05762d123b2285ef859d67382e402
ms.lasthandoff: 04/06/2017


---

# <a name="set-up-windows-device-management"></a>Configurar la administración de dispositivos Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use uno de los métodos siguientes para configurar la inscripción de dispositivos Windows:

- [**Inscripción automática de Windows 10 con Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Este método solo está disponible para dispositivos Windows 10.
 -  Debe tener Azure Active Directory Premium para usar este método.
 -  Si decide no habilitar la inscripción automática, use el método de inscripción para Windows 8.1 y Windows Phone 8.1.

- [**Inscripción sin la inscripción automática de Azure AD Premium**](#enable-windows-enrollment-without-azure-ad-premium)
 - Debe usar este método para inscribir dispositivos Windows 8.1 y Windows Phone 8.1.
 - También puede utilizar este método para dispositivos Windows 8.1 y posteriores si no desea usar Azure Active Directory (AD) Premium.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>Habilitar la inscripción de Windows sin la inscripción automática
Puede permitir a los usuarios instalar e inscribir sus dispositivos sin la inscripción automática de Azure AD Premium. Una vez que asigne una licencia a la cuenta de los usuarios, estos pueden agregar esa cuenta a un dispositivo Windows y aceptar inscribir el dispositivo en administración. Al crear registros de recursos CNAME de DNS, los usuarios se conectan a Intune y se inscriben sin especificar un nombre de servidor.

**Paso 1: Crear CNAME** (opcional)<br>
Cree registros de recursos DNS CNAME para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

Aunque la creación de entradas DNS CNAME es opcional, los registros CNAME facilitan la inscripción para los usuarios. Si no se encuentra ningún registro CNAME de inscripción, los usuarios deberán escribir manualmente el nombre del servidor MDM, enrollment.manage.microsoft.com.

Si hay más de un dominio comprobado, debe crear un registro CNAME para cada dominio. Los registros de recursos CNAME deben contener la siguiente información:

Los registros de recursos CNAME deben tener la siguiente información:

|TYPE|Nombre de host|Apunta a|TTL|
|--------|-------------|-------------|-------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 hora|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 hora|

`EnterpriseEnrollment-s.manage.microsoft.com`: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

Si su organización usa varios dominios para las credenciales de usuario, cree registros CNAME para cada dominio.

Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

**Paso 2: Comprobar CNAME** (opcional)<br>
En la [consola de administración de Intune](http://manage.microsoft.com), elija **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows**. Escriba la dirección URL del dominio verificado del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y luego elija **Probar detección automática**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Indicar a los usuarios cómo inscribir dispositivos Windows
Indique a los usuarios cómo inscribir sus dispositivos Windows y qué esperar cuando se hayan incorporado a la administración.
Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Windows en Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). También puede enviar a los usuarios a la página [¿Qué información puede ver mi empresa cuando inscribo mi dispositivo en Intune?](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)

Para más información sobre las tareas del usuario final, vea [Recursos sobre la experiencia del usuario final con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune).

### <a name="see-also"></a>Consulte también
[Requisitos previos para la inscripción de dispositivos en Microsoft Intune](prerequisites-for-enrollment.md)

