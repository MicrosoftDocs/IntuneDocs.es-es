---
title: Configuración de la inscripción de dispositivos Windows con Microsoft Intune
titleSuffix: ''
description: Configure la inscripción para dispositivos Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f12feca6d43a4194e7c60639a93747c7f389f93
ms.sourcegitcommit: fc4b38660129d615068f34ad4b96b900d73f7b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2019
ms.locfileid: "74558210"
---
# <a name="set-up-enrollment-for-windows-devices"></a>Configuración de la inscripción de dispositivos Windows

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artículo ayuda a los administradores de TI a simplificar la inscripción de Windows para sus usuarios. Una vez que haya [configurado Intune](../fundamentals/setup-steps.md), los usuarios inscriben los dispositivos Windows [iniciando sesión](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows) con su cuenta profesional o educativa.  

Como administrador de Intune, puede simplificar la inscripción de las siguientes maneras:

- [Habilitar la inscripción automática](#enable-windows-10-automatic-enrollment) (se necesita Azure AD Premium)
- [Registro CNAME](#simplify-windows-enrollment-without-azure-ad-premium)
- [Habilitar la inscripción masiva](../windows-bulk-enroll.md) (se necesita Azure AD Premium y Diseñador de configuración de Windows)

Hay dos factores que determinan cómo puede simplificar la inscripción de dispositivos Windows:

- **¿Usa Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) se incluye con Enterprise Mobility + Security y otros planes de licencias.
- **¿A qué versiones de los clientes de Windows se inscribirán los usuarios?** <br>Los dispositivos Windows 10 pueden inscribirse automáticamente al agregar una cuenta profesional o educativa. Las versiones anteriores deben inscribirse mediante la aplicación de Portal de empresa.

||**Azure AD Premium**|**Otro AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Inscripción automática](#enable-windows-10-automatic-enrollment) |Inscripción de usuarios|
|**Versiones anteriores de Windows**|Inscripción de usuarios|Inscripción de usuarios|

Las organizaciones que pueden usar la inscripción automática también pueden configurar los [dispositivos de inscripción masiva](../windows-bulk-enroll.md) mediante la aplicación Diseñador de configuración de Windows.

## <a name="device-enrollment-prerequisites"></a>Requisitos previos para la inscripción de dispositivos

Para que un administrador pueda inscribir dispositivos en Intune para su administración, ya se deben haber asignado licencias a la cuenta del administrador. [Más información sobre la asignación de licencias para la inscripción de dispositivos](../fundamentals/licenses-assign.md)

## <a name="multi-user-support"></a>Compatibilidad con varios usuarios

Intune admite varios usuarios en dispositivos que:

- Ejecuten la actualización Windows 10 Creators Update
- Estén unidos a un dominio de Azure Active Directory.

Cuando los usuarios estándar inician sesión con sus credenciales de Azure AD, reciben aplicaciones y directivas asignadas a su nombre de usuario. Solo el [usuario primario](../remote-actions/find-primary-user.md) del dispositivo puede usar el Portal de empresa en escenarios de autoservicio, como la instalación de aplicaciones y la realización de acciones de dispositivo (quitar, restablecer). En el caso de dispositivos compartidos de Windows 10 que no tienen asignado un usuario primario, puede seguir utilizándose el Portal de empresa para instalar aplicaciones disponibles.

[!INCLUDE [AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Simplificación de la inscripción de Windows sin Azure AD Premium
Para simplificar la inscripción, cree un alias de servidor de nombres de dominio (DNS, tipo de registro CNAME) que redirija las solicitudes de inscripción a los servidores de Intune. De lo contrario, los usuarios que intenten conectarse a Intune deberán escribir el nombre del servidor de Intune durante la inscripción.

**Paso 1: Creación de CNAME** (opcional)<br>
Cree registros de recursos DNS CNAME para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un registro CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com.

Aunque la creación de entradas DNS CNAME es opcional, los registros CNAME facilitan la inscripción para los usuarios. Si no se encuentra ningún registro CNAME de inscripción, se pedirá a los usuarios que escriban de forma manual el nombre del servidor MDM (enrollment.manage.microsoft.com).

|Tipo|Nombre de host|Apunta a|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 hora|

Si la compañía usa más de un sufijo UPN, debe crear un CNAME para cada nombre de dominio y apuntar todos a EnterpriseEnrollment-s.manage.microsoft.com. Por ejemplo, los usuarios de Contoso usan los siguientes formatos como su correo electrónico o UPN:

- name@contoso.com
- name@us.contoso.com
- name@eu.contoso.com

El administrador de DNS de Contoso debe crear los CNAME siguientes:

|Tipo|Nombre de host|Apunta a|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 hora|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 hora|

`EnterpriseEnrollment-s.manage.microsoft.com`: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio de DNS en Intune hasta que el registro DNS se propague.

## <a name="additional-endpoints-are-supported-but-not-recommended"></a>Se admiten puntos de conexión adicionales, pero no se recomiendan
EnterpriseEnrollment-s.manage.microsoft.com es el FQDN preferido para la inscripción, pero hay otros dos puntos de conexión que han usado los clientes en el pasado y que se admiten. EnterpriseEnrollment.manage.microsoft.com (sin -s) y manage.microsoft.com funcionan como el destino del servidor de detección automática, pero el usuario tendrá que pulsar Aceptar en un mensaje de confirmación. Si apunta a EnterpriseEnrollment-s.manage.microsoft.com, el usuario no tendrá que seguir el paso de confirmación adicional, por lo que esta es la configuración recomendada.

## <a name="alternate-methods-of-redirection-are-not-supported"></a>No se admiten métodos alternativos de redireccionamiento
No se admite el uso de un método que no sea la configuración de CNAME. Por ejemplo, no se admite el uso de un servidor proxy para redirigir enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc a enterpriseenrollment-s.manage.microsoft.com/EnrollmentServer/Discovery.svc o manage.microsoft.com/EnrollmentServer/Discovery.svc.

**Paso 2: Comprobación de CNAME** (opcional)<br>
1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **Windows** > **Inscripción de Windows** > **Validación de CNAME**.
2. En el cuadro **Dominio**, escriba el sitio web de empresa y, a continuación, haga clic en **Probar**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Indicar a los usuarios cómo inscribir dispositivos Windows
Indique a los usuarios cómo inscribir sus dispositivos Windows y qué esperar cuando se hayan incorporado a la administración.

> [!NOTE]
> Los usuarios finales deben tener acceso al sitio web Portal de empresa a través de Microsoft Edge para ver las aplicaciones de Windows que haya asignado para versiones específicas de Windows. Otros exploradores (incluidos Google Chrome, Mozilla Firefox e Internet Explorer) no admiten este tipo de filtrado.

Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Windows en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). También puede indicar a los usuarios que revisen [¿Qué información puede ver mi administrador de TI cuando inscribo mi dispositivo en Intune?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

>[!IMPORTANT]
> Si no tiene habilitada la inscripción de MDM automática, pero tiene dispositivos Windows 10 unidos a Azure AD, verá dos registros en la consola de Intune tras la inscripción. Esto se puede evitar; para ello, asegúrese de que los usuarios con dispositivos unidos a Azure AD se dirigen a **Cuentas** > **Obtener acceso a trabajo o escuela** y usan **Conectar** para conectarse con la misma cuenta. 

Para más información sobre las tareas del usuario final, vea [Recursos sobre la experiencia del usuario final con Microsoft Intune](../fundamentals/end-user-educate.md).

## <a name="registration-and-enrollment-cnames"></a>CNAME de registro e inscripción
Azure Active Directory tiene un CNAME diferente que usa para el registro de dispositivos iOS, Android y Windows. El acceso condicional de Intune requiere el registro de dispositivos, en una acción denominada también "unirse al área de trabajo". Si piensa usar el acceso condicional, también debe configurar el CNAME EnterpriseRegistration para cada nombre de empresa que tenga.

| Tipo | Nombre de host | Apunta a | TTL |
| --- | --- | --- | --- |
| NOMBRE | EnterpriseRegistration. company_domain.com | EnterpriseRegistration.windows.net | 1 hora|

Para obtener más información sobre el registro de dispositivos, consulte [Administración de identidades de dispositivos con Azure Portal](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal).

## <a name="next-steps"></a>Pasos siguientes

- [Consideraciones al administrar dispositivos Windows con Intune en Azure](../fundamentals/intune-legacy-pc-client.md).
