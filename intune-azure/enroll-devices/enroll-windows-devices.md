---
title: "Inscripción de dispositivos Windows"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: habilite la administración de dispositivos móviles (MDM) de Intune para dispositivos Windows."
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 03/21/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 771aed4e1c57171183b9a9ea7d9e0f702dc1859c
ms.openlocfilehash: b62a5704605f5cf89efb4052180f09f88eb788e1
ms.lasthandoff: 04/06/2017


---

# <a name="enroll-windows-devices"></a>Inscripción de dispositivos Windows

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Este tema ayuda a los administradores de TI a simplificar la inscripción de Windows para sus usuarios.  Los dispositivos Windows se pueden inscribir sin pasos adicionales, pero puede facilitar la inscripción para los usuarios.

Hay dos factores que determinan cómo inscribirá dispositivos Windows:
- **¿Usa Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) se incluye con Enterprise Mobility + Security y otros planes de licencias.
- **¿Qué versiones de los clientes de Windows se inscribirán?** <br>Los dispositivos Windows 10 pueden inscribirse automáticamente al agregar una cuenta profesional o educativa. Las versiones anteriores deben inscribirse mediante la aplicación de Portal de empresa.

||**Azure AD Premium**|**Otro AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Inscripción automática](#enable-windows-10-automatic-enrollment) |[Inscripción de usuarios](#enable-windows-enrollment-without-azure-ad-premium)|
|**Versiones anteriores de Windows**|[Inscripción de usuarios](#enable-windows-enrollment-without-azure-ad-premium)|[Inscripción de usuarios](#enable-windows-enrollment-without-azure-ad-premium)|

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Habilitación de la inscripción de Windows sin Azure AD Premium
Puede permitir a los usuarios inscribir sus dispositivos sin la inscripción automática de Azure AD Premium. Una vez que asigne licencias a las cuentas de los usuarios, estos pueden agregar esa cuenta a un dispositivo Windows y aceptar inscribir el dispositivo en administración. La creación de un alias DNS (tipo de registro CNAME) facilita a los usuarios la inscripción de sus dispositivos. Al crear registros de recursos DNS CNAME, los usuarios se conectan a Intune y se inscriben sin necesidad de escribir el nombre del servidor de Intune.

**Paso 1: Crear CNAME** (opcional)<br>
Cree registros de recursos DNS CNAME para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

Aunque la creación de entradas DNS CNAME es opcional, los registros CNAME facilitan la inscripción para los usuarios. Si no se encuentra ningún registro CNAME de inscripción, se pedirá a los usuarios que escriban de forma manual el nombre del servidor MDM (enrollment.manage.microsoft.com).

|Tipo|Nombre de host|Apunta a|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|

Si tiene más de un sufijo UPN, debe crear un CNAME para cada nombre de dominio y apuntar todos a EnterpriseEnrollment-s.manage.microsoft.com. Por ejemplo, si los usuarios de Contoso usan name@contoso.com, pero también usan name@us.contoso.com y name@eu.constoso.com como su correo electrónico o UPN, el administrador de DNS de Contoso necesitaría crear los CNAME siguientes.

|Tipo|Nombre de host|Apunta a|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|

`EnterpriseEnrollment-s.manage.microsoft.com`: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

**Paso 2: Comprobar CNAME** (opcional)<br>
En el portal de Azure Intune, elija **Más servicios** > **Supervisión y administración** > **Intune**. En la hoja Intune, elija **Inscribir dispositivos** > **Windows Enrollment** (Inscripción de Windows). Escriba la dirección URL del dominio verificado del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y luego elija **Probar detección automática**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Indicar a los usuarios cómo inscribir dispositivos Windows
Indique a los usuarios cómo inscribir sus dispositivos Windows y qué esperar cuando se hayan incorporado a la administración. Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Windows en Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). También puede indicar a los usuarios que consulten la página [¿Qué información puede ver mi empresa cuando inscribo mi dispositivo en Intune?](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)

Para más información sobre las tareas del usuario final, vea [Recursos sobre la experiencia del usuario final con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune).

