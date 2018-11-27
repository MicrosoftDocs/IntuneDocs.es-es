---
title: Configuración de la inscripción de dispositivos Windows con Microsoft Intune
titlesuffix: ''
description: Configure la inscripción para dispositivos Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: efb850e0f08c94cfee7948f50411220216eb8418
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188082"
---
# <a name="set-up-enrollment-for-windows-devices"></a>Configuración de la inscripción de dispositivos Windows

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artículo ayuda a los administradores de TI a simplificar la inscripción de Windows para sus usuarios. Una vez que haya [configurado Intune](setup-steps.md), los usuarios inscriben los dispositivos Windows [iniciando sesión](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows) con su cuenta profesional o educativa.  

Como administrador de Intune, puede simplificar la inscripción de las siguientes maneras:
- [Habilitar la inscripción automática](#enable-windows-10-automatic-enrollment) (se necesita Azure AD Premium)
- [Registro CNAME](#simplify-windows-enrollment-without-azure-ad-premium)
- [Habilitar la inscripción masiva](windows-bulk-enroll.md) (se necesita Azure AD Premium y Diseñador de configuración de Windows)

Hay dos factores que determinan cómo puede simplificar la inscripción de dispositivos Windows:

- **¿Usa Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) se incluye con Enterprise Mobility + Security y otros planes de licencias.
- **¿A qué versiones de los clientes de Windows se inscribirán los usuarios?** <br>Los dispositivos Windows 10 pueden inscribirse automáticamente al agregar una cuenta profesional o educativa. Las versiones anteriores deben inscribirse mediante la aplicación de Portal de empresa.

||**Azure AD Premium**|**Otro AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Inscripción automática](#enable-windows-10-automatic-enrollment) |[Inscripción de usuarios](#enable-windows-enrollment-without-azure-ad-premium)|
|**Versiones anteriores de Windows**|[Inscripción de usuarios](#enable-windows-enrollment-without-azure-ad-premium)|[Inscripción de usuarios](#enable-windows-enrollment-without-azure-ad-premium)|

Las organizaciones que pueden usar la inscripción automática también pueden configurar los [dispositivos de inscripción masiva](windows-bulk-enroll.md) mediante la aplicación Diseñador de configuración de Windows.

## <a name="multi-user-support"></a>Compatibilidad con varios usuarios

Intune admite administración de varios usuarios en dispositivos que ejecutan Windows 10 Creators Update y están unidos al dominio de Azure Active Directory. Cuando los usuarios estándar inician sesión con sus credenciales de Azure AD, reciben aplicaciones y directivas asignadas a su nombre de usuario. Actualmente, los usuarios no pueden usar el Portal de empresa para escenarios de autoservicio, como la instalación de aplicaciones.

[!INCLUDE [AAD-enrollment](./includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Simplificación de la inscripción de Windows sin Azure AD Premium
Para simplificar la inscripción, cree un alias de servidor de nombres de dominio (DNS, tipo de registro CNAME) que redirija las solicitudes de inscripción a los servidores de Intune. De lo contrario, los usuarios que intenten conectarse a Intune deberán escribir el nombre del servidor de Intune durante la inscripción.

**Paso 1: Crear CNAME** (opcional)<br>
Cree registros de recursos DNS CNAME para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un registro CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com.

Aunque la creación de entradas DNS CNAME es opcional, los registros CNAME facilitan la inscripción para los usuarios. Si no se encuentra ningún registro CNAME de inscripción, se pedirá a los usuarios que escriban de forma manual el nombre del servidor MDM (enrollment.manage.microsoft.com).

|Tipo|Nombre de host|Apunta a|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 hora|

Si la compañía usa más de un sufijo UPN, debe crear un CNAME para cada nombre de dominio y apuntar todos a EnterpriseEnrollment-s.manage.microsoft.com. Por ejemplo, los usuarios de Contoso usan los siguientes formatos como su correo electrónico o UPN:

- name@contoso.com
- name@us.contoso.com
- name@eu.constoso.com\

El administrador de DNS de Contoso debe crear los CNAME siguientes:

|Tipo|Nombre de host|Apunta a|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|

`EnterpriseEnrollment-s.manage.microsoft.com`: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio de DNS en Intune hasta que el registro DNS se propague.

**Paso 2: Comprobar CNAME** (opcional)<br>
1. En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Validación de CNAME**.
2. En el cuadro **Dominio**, escriba el sitio web de empresa y, a continuación, haga clic en **Probar**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Indicar a los usuarios cómo inscribir dispositivos Windows
Indique a los usuarios cómo inscribir sus dispositivos Windows y qué esperar cuando se hayan incorporado a la administración.

> [!NOTE]
> Los usuarios finales deben tener acceso al sitio web Portal de empresa a través de Microsoft Edge para ver las aplicaciones de Windows que haya asignado para versiones específicas de Windows. Otros exploradores (incluidos Google Chrome, Mozilla Firefox e Internet Explorer) no admiten este tipo de filtrado.

Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Windows en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). También puede indicar a los usuarios que revisen [¿Qué información puede ver mi administrador de TI cuando inscribo mi dispositivo en Intune?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

>[!IMPORTANT]
> Si no tiene habilitada la inscripción de MDM automática, pero tiene dispositivos Windows 10 unidos a Azure AD, verá dos registros en la consola de Intune tras la inscripción. Esto se puede evitar; para ello, asegúrese de que los usuarios con dispositivos unidos a Azure AD se dirigen a **Cuentas** > **Obtener acceso a trabajo o escuela** y usan **Conectar** para conectarse con la misma cuenta. 

Para más información sobre las tareas del usuario final, vea [Recursos sobre la experiencia del usuario final con Microsoft Intune](end-user-educate.md).

## <a name="next-steps"></a>Pasos siguientes

- [Consideraciones al administrar dispositivos Windows con Intune en Azure](/intune-classic/deploy-use/intune-on-azure).
