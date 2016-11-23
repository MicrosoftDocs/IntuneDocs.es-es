---
title: "Configurar la administración de Windows 10 Mobile y Windows Phone | Microsoft Intune"
description: "Habilite la administración de dispositivos móviles (MDM) para dispositivos Windows 10 Mobile o Windows Phone con Microsoft Intune."
keywords: 
author: staciebarker
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d44a6494bed0758b9768045bd204ea0eb481636
ms.openlocfilehash: 66d533d094a12239ca4ed1a30f9ce3a06e5cece1


---


# <a name="set-up-windows-phone-and-windows-10-mobile-management-with-microsoft-intune"></a>Configurar la administración de Windows Phone y Windows 10 Mobile con Microsoft Intune

Como administrador de Intune, puede habilitar la inscripción y administración de los dispositivos Windows 10 Mobile y Windows Phone de dos maneras:

- **[Inscripción automática con Azure Active Directory](#azure-active-directory-enrollment)**: los usuarios de Windows 10 y Windows 10 Mobile inscriben sus dispositivos agregando al dispositivo una cuenta profesional o educativa
- **[Inscripción de Portal de empresa](#company-portal-app-enrollment)**: los usuarios de Windows Phone 8.1 y versiones posteriores inscriben sus dispositivos descargando e instalando la aplicación Portal de empresa y escribiendo en la aplicación las credenciales de su cuenta profesional o educativa.


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="company-portal-app-enrollment"></a>Inscripción de la aplicación de Portal de empresa
Puede permitir que los usuarios instalen e inscriban sus dispositivos con la aplicación Portal de empresa de Intune. Al crear registros de recursos CNAME de DNS, los usuarios se conectan a Intune y se inscriben sin especificar un nombre de servidor.

1.  **Configurar Intune**<br>Si aún no lo ha hecho, prepárese para la administración de dispositivos móviles. Para ello, [defina la entidad de administración de dispositivos móviles (MDM)](prerequisites-for-enrollment.md#set-mobile-device-management-authority) como **Microsoft Intune** y luego configure MDM.

2.  **Crear CNAME** (opcional)<br>Debe crear registros de recursos DNS **CNAME** para el dominio de su empresa. Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com. 

    Si tiene ahora un CNAME en el DNS que redirija EnterpriseEnrollment.contoso.com a manage.microsoft.com, sugerimos que lo reemplace por un CNAME en el DNS que redirija EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com. Se recomienda este cambio, porque en una versión futura el punto de conexión manage.microsoft.com estará en desuso para las inscripciones.

    Si hay más de un dominio comprobado, debe crear un registro CNAME para cada dominio. Los registros de recursos CNAME deben contener la siguiente información:

  |TYPE|Nombre de host|Apunta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 hora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 hora|

  `EnterpriseEnrollment-s.manage.microsoft.com`: admite un redireccionamiento al servicio Intune con reconocimiento de dominio del nombre de dominio del correo electrónico.

  `EnterpriseRegistration.windows.net`: admite dispositivos Windows 8.1 y Windows 10 Mobile que se registrarán en Azure Active Directory con su cuenta profesional o educativa.

  Si su organización usa varios dominios para las credenciales de usuario, cree registros CNAME para cada dominio.

  Por ejemplo, si el sitio web de la empresa es contoso.com, debe crear un CNAME en DNS que redirija EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. Los cambios en los registros DNS pueden tardar hasta 72 horas en propagarse. No se puede comprobar el cambio DNS en Intune hasta que el registro DNS se propague.

3.  **Comprobar el CNAME**<br>En la [consola de administración de Intune](http://manage.microsoft.com), elija **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows Phone**. Escriba la dirección URL del dominio verificado del sitio web de empresa en el cuadro **Especificar un nombre de dominio verificado** y luego elija **Probar detección automática**.

    ![Configurar la administración de dispositivos móviles para el cuadro de diálogo de Windows](../media/windows-phone-enrollment.png)

4.  **Pasos opcionales**<br>El paso **Agregar claves de instalación de prueba** no es necesario para Windows 10. El paso **Cargar certificado de firma de código** solo es necesario si va a distribuir aplicaciones de línea de negocio (LOB) que no están disponibles en la Tienda Windows a dispositivos.

5.  **Indique a los usuarios cómo inscribir sus dispositivos para acceder a recursos de la empresa.**

    Para obtener instrucciones de inscripción del usuario final, consulte [Inscribir el dispositivo Windows en Intune](../enduser/enroll-your-device-in-intune-windows.md). También puede enviar a los usuarios a [¿Qué puede ver el administrador de TI cuando inscribe el dispositivo en Intune?](../enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)

    Para más información acerca de otras tareas de usuario final, consulte estos artículos:
    - [Qué decirles a los usuarios finales sobre el uso de Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Guía de usuario final para dispositivos Windows](../enduser/using-your-windows-device-with-intune.md)

No es necesario ningún trabajo adicional a menos que vaya a implementar el portal de empresa en dispositivos.  Puede omitir sin ningún problema los pasos 2 y 3 de la consola de administración.



<!--HONumber=Nov16_HO2-->


