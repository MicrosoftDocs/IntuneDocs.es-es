---
title: Configurar la administración de dispositivos Windows con Microsoft Intune
description: Habilite la administración de dispositivos móviles (MDM) para dispositivos Windows con Microsoft Intune.
keywords: ''
author: NathBarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fb2d724cc87ffdc506eda8d5ea2330ab9aacd3e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-windows-device-management"></a>Configurar la administración de dispositivos Windows

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Este tema ayuda a los administradores de TI a simplificar la inscripción de Windows para sus usuarios.  Los dispositivos Windows se pueden inscribir sin pasos adicionales, pero puede facilitar la inscripción para los usuarios.

Hay dos factores que determinan cómo puede simplificar la inscripción de dispositivos Windows:
- **¿Usa Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) se incluye con Enterprise Mobility + Security y otros planes de licencias.
- **¿Qué versiones de los clientes de Windows se inscribirán?** <br>Los dispositivos Windows 10 pueden inscribirse automáticamente al agregar una cuenta profesional o educativa. Las versiones anteriores deben inscribirse mediante la aplicación de Portal de empresa.

||**Azure AD Premium**|**Otro AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Inscripción automática](#enable-windows-10-automatic-enrollment) |[Inscripción de usuarios](#enable-windows-enrollment-without-automatic-enrollment)|
|**Versiones anteriores de Windows**|[Inscripción de usuarios](#enable-windows-enrollment-without-automatic-enrollment)|[Inscripción de usuarios](#enable-windows-enrollment-without-automatic-enrollment)|

[!INCLUDE [AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>Habilitación de la inscripción de Windows sin inscripción automática Premium
Puede permitir a los usuarios inscribir sus dispositivos sin la inscripción automática de Azure AD Premium. Una vez que asigne licencias, los usuarios pueden realizar la inscripción después de agregar la cuenta profesional a sus dispositivos personales o unir sus dispositivos corporativos a Azure AD. La creación de un alias DNS (tipo de registro CNAME) permite que los usuarios puedan inscribir sus dispositivos fácilmente. Al crear registros de recursos DNS CNAME, los usuarios se conectan a Intune y se inscriben sin necesidad de escribir el nombre del servidor de Intune.

**Paso 1: Crear CNAME** (opcional)<br>
Cree registros de recursos DNS CNAME para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un registro CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com.

Aunque la creación de entradas DNS CNAME es opcional, los registros CNAME facilitan la inscripción para los usuarios. Si no se encuentra ningún registro CNAME de inscripción, se pedirá a los usuarios que escriban de forma manual el nombre del servidor MDM (enrollment.manage.microsoft.com).

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
En la [consola de administración de Intune](https://manage.microsoft.com), elija **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows**. Escriba la dirección URL del dominio comprobado del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y luego elija **Probar detección automática**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Indicación a los usuarios de cómo inscribir dispositivos Windows
Indique a los usuarios cómo inscribir sus dispositivos Windows y qué esperar cuando se hayan incorporado a la administración.
Para instrucciones sobre inscripción del usuario final, consulte [Inscriba el dispositivo Windows en Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). También puede enviar a los usuarios a la página [¿Qué información puede ver mi empresa cuando inscribo mi dispositivo en Intune?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)

Para más información sobre las tareas del usuario final, consulte [Cómo presentar Microsoft Intune a los usuarios finales](/intune/end-user-educate).

### <a name="see-also"></a>Vea también
[Requisitos previos para la inscripción de dispositivos en Microsoft Intune](prerequisites-for-enrollment.md)
