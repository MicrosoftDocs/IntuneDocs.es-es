---
title: "Inscripción de dispositivos Windows"
titleSuffix: Intune on Azure
description: "Habilite la administración de dispositivos móviles (MDM) de Intune para dispositivos Windows\"."
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 06/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b873e72e39c5c6f1d96ddac138f920be9dc673dd
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
# <a name="enroll-windows-devices"></a>Inscripción de dispositivos Windows

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tema ayuda a los administradores de TI a simplificar la inscripción de Windows para sus usuarios. Una vez que haya [configurado Intune](setup-steps.md), los usuarios inscriben los dispositivos Windows [iniciando sesión](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows) con su cuenta profesional o educativa.  

Como administrador de Intune, puede simplificar la inscripción de las siguientes maneras:
- Habilitar la inscripción automática (se necesita Azure AD Premium)
- Registro CNAME
- Habilitar la inscripción masiva (se necesita Azure AD Premium y Diseñador de configuración de Windows)

Hay dos factores que determinan cómo puede simplificar la inscripción de dispositivos Windows:

- **¿Usa Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) se incluye con Enterprise Mobility + Security y otros planes de licencias.
- **¿A qué versiones de los clientes de Windows se inscribirán los usuarios?** <br>Los dispositivos Windows 10 pueden inscribirse automáticamente al agregar una cuenta profesional o educativa. Las versiones anteriores deben inscribirse mediante la aplicación de Portal de empresa.

||**Azure AD Premium**|**Otro AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Inscripción automática](#enable-windows-10-automatic-enrollment) |[Inscripción de usuarios](#enable-windows-enrollment-without-azure-ad-premium)|
|**Versiones anteriores de Windows**|[Inscripción de usuarios](#enable-windows-enrollment-without-azure-ad-premium)|[Inscripción de usuarios](#enable-windows-enrollment-without-azure-ad-premium)|

Las organizaciones que pueden usar la inscripción automática también pueden configurar los [dispositivos de inscripción masiva](windows-bulk-enroll.md) mediante la aplicación Diseñador de configuración de Windows.

**Compatibilidad con varios usuarios**<br>
Los dispositivos que ejecutan Windows 10 Creators Update y que están unidos al dominio de Azure Active Directory ahora admiten la administración de varios usuarios de Intune. Cuando los usuarios estándar inician sesión con sus credenciales de Azure AD, reciben aplicaciones y directivas asignadas a su nombre de usuario. Actualmente, los usuarios no puede usar Portal de empresa para escenarios de autoservicio, como la instalación de aplicaciones.

[!INCLUDE[AAD-enrollment](./includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Habilitación de la inscripción de Windows sin Azure AD Premium
Puede simplificar la inscripción para sus usuarios creando un alias DNS (tipo de registro CNAME) que redirige automáticamente las solicitudes de inscripción a los servidores de Intune. Si no crea un registro de recurso DNS CNAME, los usuarios que intentan conectarse a Intune deben especificar el nombre del servidor de Intune durante la inscripción.

**Paso 1: Crear CNAME** (opcional)<br>
Cree registros de recursos DNS CNAME para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

Aunque la creación de entradas DNS CNAME es opcional, los registros CNAME facilitan la inscripción para los usuarios. Si no se encuentra ningún registro CNAME de inscripción, se pedirá a los usuarios que escriban de forma manual el nombre del servidor MDM (enrollment.manage.microsoft.com).

|Tipo|Nombre de host|Apunta a|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|

Si tiene más de un sufijo UPN, debe crear un CNAME para cada nombre de dominio y apuntar todos a EnterpriseEnrollment-s.manage.microsoft.com. Si los usuarios de Contoso usan name@contoso.com, pero también usan name@us.contoso.com y name@eu.constoso.com como su correo electrónico o UPN, el administrador de DNS de Contoso debe crear los CNAME siguientes:

|Tipo|Nombre de host|Apunta a|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|

`EnterpriseEnrollment-s.manage.microsoft.com`: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

**Paso 2: Comprobar CNAME** (opcional)<br>
En el portal de Azure Intune, elija **Más servicios** > **Supervisión y administración** > **Intune**. En la hoja Intune, elija **Inscribir dispositivos** > **Windows Enrollment** (Inscripción de Windows). Escriba la dirección URL del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y luego pulse **Probar detección automática**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Indicar a los usuarios cómo inscribir dispositivos Windows
Indique a los usuarios cómo inscribir sus dispositivos Windows y qué esperar cuando se hayan incorporado a la administración. Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Windows en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). También puede indicar a los usuarios que revisen [¿Qué información puede ver mi administrador de TI cuando inscribo mi dispositivo en Intune?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

Para más información sobre las tareas del usuario final, vea [Recursos sobre la experiencia del usuario final con Microsoft Intune](end-user-educate.md).
