---
title: "Configurar la administración de dispositivos Windows con Microsoft Intune | Microsoft Intune"
description: "Habilite la administración de dispositivos móviles (MDM) para PC con Windows, incluidos dispositivos Windows 10 con Microsoft Intune."
keywords: 
author: staciebarker
manager: stabar
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d51f34dea3463bec83ea39cdfb79c7bedf9e3926
ms.openlocfilehash: 78137299b1c4e18fe68e1f9720a2111d1794e177


---

# <a name="set-up-windows-device-management"></a>Configurar la administración de dispositivos Windows

Como administrador de Intune, puede habilitar la inscripción y administración de los equipos Windows de dos maneras:

- **[Inscripción automática con Azure Active Directory](#azure-active-directory-enrollment)**: los usuarios de Windows 10 y Windows 10 Mobile inscriben sus dispositivos agregando al dispositivo una cuenta profesional o educativa
- **[Inscripción de Portal de empresa](#company-portal-app-enrollment)**: los usuarios de Windows 8.1 y versiones posteriores inscriben sus dispositivos descargando e instalando la aplicación Portal de empresa y escribiendo en la aplicación las credenciales de su cuenta profesional o educativa.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-company-portal-app-enrollment"></a>Configurar la inscripción de la aplicación Portal de empresa
Puede permitir que los usuarios instalen e inscriban sus dispositivos con la aplicación Portal de empresa de Intune. Al crear registros de recursos CNAME de DNS, los usuarios se conectan a Intune y se inscriben sin especificar un nombre de servidor.

1. **Configurar Intune**<br>
Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles (MDM)](prerequisites-for-enrollment.md#set-mobile-device-management-authority) como **Microsoft Intune** y luego configure MDM.

2. **Crear CNAME** (opcional)<br>Cree registros de recursos DNS **CNAME** para el dominio de su empresa para simplificar la inscripción. Aunque la creación de entradas DNS CNAME es opcional, los registros CNAME facilitan la inscripción para los usuarios. Si no se encuentra ningún registro CNAME de inscripción, los usuarios deberán escribir manualmente el nombre del servidor MDM, `https://manage.microsoft.com`. Los registros de recursos CNAME deben tener la siguiente información:

  |TYPE|Nombre de host|Apunta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 hora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 hora|

  `EnterpriseEnrollment-s.manage.microsoft.com`: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

  `EnterpriseRegistration.windows.net`: admite dispositivos Windows 8.1 y Windows 10 Mobile que se registrarán en Azure Active Directory con su cuenta profesional o educativa.

  Si su organización usa varios dominios para las credenciales de usuario, cree registros CNAME para cada dominio.

  Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

3.  **Comprobar el CNAME**<br>En la [consola de administración de Intune](http://manage.microsoft.com), elija **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows**. Escriba la dirección URL del dominio verificado del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y luego elija **Probar detección automática**.

  ![Cuadro de diálogo de administración de dispositivos Windows](../media/enroll-intune-winenr.png)

4.  **Pasos opcionales**<br>El paso **Agregar claves de instalación de prueba** no es necesario para Windows 10. El paso **Cargar certificado de firma de código** solo es necesario si va a distribuir aplicaciones de línea de negocio (LOB) que no están disponibles en la Tienda Windows a dispositivos.

6.  **Indique a los usuarios cómo inscribir sus dispositivos y qué esperar cuando se hayan incorporado a la administración.**

    Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Windows en Intune](../enduser/enroll-your-device-in-intune-windows.md).

    Para más información sobre las tareas del usuario final, consulte estos artículos:
      - [Recursos sobre la experiencia del usuario final con Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Guía de usuario final para dispositivos Windows](../enduser/using-your-windows-device-with-intune.md)

### <a name="see-also"></a>Consulte también
[Requisitos previos para la inscripción de dispositivos en Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Nov16_HO2-->


