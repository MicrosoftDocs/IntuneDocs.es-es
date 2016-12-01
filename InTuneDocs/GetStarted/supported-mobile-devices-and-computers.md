---
title: "Exploradores y dispositivos móviles compatibles | Microsoft Intune"
description: "Dispositivos móviles y equipos que admite Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aeeccfa4-0f14-447e-a3df-c8435c8a4bb2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 149f3a3310907d131affeaad4bd372aa60be9206
ms.openlocfilehash: 80541567c535cfeb7fca3eda3c9143f4b11d7abb


---

# <a name="supported-mobile-devices-and-computers"></a>Equipos y dispositivos móviles compatibles

Puede inscribir y administrar los siguientes tipos de dispositivo:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

La inscripción de dispositivos proporciona [estas capacidades](/Intune/get-started/choose-how-to-manage-devices).

Como alternativa, puede administrar equipos con Windows con el software cliente de Intune PC. El software de cliente de Intune PC es compatible con Windows 7 y versiones posteriores, excepto Windows 10 Home. La administración de equipos con el software cliente proporciona [estas capacidades](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

Los clientes con el conjunto de aplicaciones de administración empresarial también pueden usar Azure Active Directory (Azure AD) para registrar dispositivos Windows 10.

## <a name="microsoft-intune-supported-web-browsers"></a>Exploradores web compatibles de Microsoft Intune

Las diferentes tareas administrativas requieren el uso de uno de los siguientes sitios web de administración.

- [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Consola de administrador de Microsoft Intune](https://admin.manage.microsoft.com/)

> [!Note]
> Microsoft Edge y los exploradores móviles no son compatibles con la consola de administración porque no admiten [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). La migración de la consola de Intune desde la experiencia de Silverlight se realizará a lo largo de un período de tiempo; al final, todos los dispositivos móviles y las características de administración de aplicaciones de Intune estarán [disponibles en el nuevo portal de Microsoft Azure](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).

|Característica de Intune |Exploradores admitidos|
|---------|---------|
|Consola de administración de Intune     |  Internet Explorer 10 o posterior<br /><br />Google Chrome (las versiones anteriores a la 42)<br /><br />Mozilla Firefox con Silverlight habilitado<br /><br />**Nota:** La consola de administración no admite Microsoft Edge ni los exploradores móviles.                      
|Portal de administración de Office 365     |Todos los exploradores, incluidos los exploradores móviles y los exploradores administrados  |
|Sitio web del Portal de empresa     |**En dispositivos móviles:** use el explorador web predeterminado para cada plataforma compatible   <br /><br />**En equipos de Windows:** Internet Explorer 10 o posterior, o Microsoft Edge<br /><br />**En Mac OS X 10.9 o posterior:** Apple Safari    |

> [!Note]
> Microsoft Edge y los exploradores móviles no son compatibles con la consola de administración porque no admiten [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). La migración de la consola de Intune desde la experiencia de Silverlight se realizará a lo largo de un período de tiempo; al final, todos los dispositivos móviles y las características de administración de aplicaciones de Intune estarán [disponibles en el nuevo portal de Microsoft Azure](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).

### <a name="office-365-portalhttpgomicrosoftcomfwlinkplinkid698854"></a>[Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**Como administrador de inquilinos, use este portal para administrar la suscripción**, incluidas las tareas siguientes, siempre y cuando se lo permita el rol de administrador:

- Administrar cuentas de usuario para la suscripción y configurar la sincronización de directorios desde el Active Directory local.
- Administrar grupos de usuarios, denominados grupos de seguridad.
- Asignar licencias a los usuarios para usar Intune.
- Configurar el nombre de dominio que se utiliza con la suscripción. El nombre de dominio define la cuenta con la que los usuarios inician sesión.
- Administrar los detalles de facturación y de compras de su suscripción, incluido el número de licencias que posee, o la cantidad de espacio de almacenamiento en nube que puede utilizar.
- Buscar vínculos para ver el estado del servicio de Intune.
- Como administrador de inquilinos, puede iniciar sesión en el portal de Office 365 para administrar la suscripción, aunque su cuenta no tenga asignada una licencia para usar Intune.
- Cualquier usuario que tenga una licencia de Intune, pero no sea un administrador, puede usar este portal para restablecer la contraseña de su cuenta y editar su perfil.
- Para tener acceso al portal de Office 365, el estado de inicio de sesión de su cuenta debe ser **Permitido**. Este estado es distinto a tener una licencia para la suscripción. De manera predeterminada, todas las cuentas de usuario tienen el estado **Permitido**.


### <a name="microsoft-intune-administrator-consolehttpsmanagemicrosoftcom"></a>[Consola de administrador de Microsoft Intune](https://manage.microsoft.com/)

**Como administrador de servicios, use este portal para administrar las operaciones diarias** como:

- Establecer directivas para equipos y dispositivos móviles.
- Cargar e implementar software como actualizaciones de software y aplicaciones.
- Administrar Endpoint Protection en los equipos.
- Ver el estado del dispositivo y ejecutar informes.
- Inicie sesión en este portal. Para iniciar sesión en este portal, debe tener permisos de administrador de servicios o ser un administrador de inquilinos con el rol de administrador global.


Solo los usuarios con permisos de administrador de servicios o que sean administradores de inquilinos con el rol de administrador global pueden iniciar sesión en este portal. Para acceder a la consola de administración, su cuenta debe tener una licencia para usar Intune y un estado de inicio de sesión de **Permitido**.



<!--HONumber=Nov16_HO4-->


