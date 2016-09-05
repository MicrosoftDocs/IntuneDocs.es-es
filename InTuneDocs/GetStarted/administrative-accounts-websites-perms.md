---
title: Cuentas administrativas, sitios web y permisos | Microsoft Intune
description: cuentas administrativas permisos sitios web
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db3075e7-38fd-4dfe-b266-26aed10ac8ea
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6d1c7c670341692d4ea0c823e4a9a96746b83067
ms.openlocfilehash: 017de4d0cc65c00129a45f140eebea11a61154af


---

# Cuentas administrativas, sitios web y permisos en Microsoft Intune

Antes de configurar Microsoft Intune, repase este tema y los requisitos que aparecen en [What to know before you start Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md) (Información necesaria antes de iniciar Microsoft Intune).

Para administrar Intune, usará:
- Dos tipos de cuentas de administrador
- Cuentas de usuario con permisos adicionales
- Dos consolas o portales de administración basados en web para conceder a los administradores acceso a los elementos que deban administrar.

Las siguientes secciones explican estas cuentas y portales.

## Cuentas de administrador y cuentas de usuario con permisos especiales

Estas son las cuentas y los permisos que se usarán en Intune.

### Administrador de inquilinos
|Niveles de permisos|Más información|
|--------------------------|-------------------------|
|A los administradores de inquilinos se les asigna un rol de administrador que define el ámbito administrativo para ese usuario y las tareas que pueden administrar.<br /><br />Los roles de administrador son comunes entre los diferentes servicios en la nube de Microsoft, aunque es posible que algunos servicios no sean compatibles con determinados roles.<br /><br /> Microsoft Intune usa los siguientes roles:<br /><br />- Administrador global<br />- Administrador de facturación<br />- Administrador de contraseñas<br />- Administrador de soporte técnico de servicio<br />- Administrador de control de usuarios|La cuenta que se usa para crear la suscripción de Microsoft Intune es, de forma predeterminada, un administrador de inquilinos con el rol de administrador global.<br /></br>  Como administrador de inquilinos, usará la [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] para administrar la suscripción de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y para asignar administradores de inquilinos desde [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />Utilice un administrador de inquilinos con el rol de administración global para tener acceso a la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] y asignar así a su primer administrador de servicios. Como práctica recomendada, no utilice un administrador de inquilinos para tareas diarias de administración. Un administrador de inquilinos no requiere una licencia de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para tener acceso al [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />El administrador de inquilinos es un concepto común entre los servicios de nube de Microsoft. Cuando se suscribe a [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], el servicio es un inquilino de Microsoft Azure AD. Vea la sección del inquilino de Azure AD en [¿Qué es un directorio de Azure AD?](http://technet.microsoft.com/library/jj573650.aspx).|


### Administrador de servicios
|Niveles de permisos|Más información|
|--------------------------|-------------------------|
|A los administradores de servicios se les asigna uno de los siguientes permisos:<br /><br />**Acceso completo:** se otorga acceso a todas las áreas de la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)], sin restricciones. También puede agregar y administrar otros administradores de servicios.<br /><br />**Acceso de solo lectura:** se otorga permiso de lectura a todas las áreas de la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]. Un administrador de servicios de solo lectura no puede modificar los datos, pero puede ejecutar informes.<br /><br />**Departamento de soporte técnico - nodo Grupos:** se otorgan los permisos que permiten al administrador de servicios realizar solo un conjunto de tareas que suelen estar asociadas con escenarios del departamento de soporte técnico. Para obtener más información sobre este conjunto de permisos, vea [Personalizar vistas de consola de Intune según los roles de administración](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console).|De forma predeterminada, [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] no asigna un administrador de servicios. En su lugar, debe utilizar un administrador de inquilinos con el rol de administrador global para asignar el primer administrador de servicios de la suscripción. </br></br> Como administrador de servicios, debe usar la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] para administrar las tareas diarias de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].<br /><br />Los administradores de servicios se asignan desde la consola de administración. Un administrador de servicios requiere una licencia de [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] antes de que la cuenta pueda acceder a la consola de administración.|



### Administradores de inscripción de dispositivos
|Niveles de permisos|Más información|
|--------------------------|-------------------------|
|Los administradores de inscripción de dispositivos son cuentas de usuario estándar que tienen permisos adicionales para inscribir más de cinco dispositivos.|De forma predeterminada, cada usuario de [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] puede inscribir hasta cinco dispositivos. Sin embargo, puede conceder a una cuenta de usuario el permiso de administrador de inscripción de dispositivos y, después, utilizar esa cuenta para inscribir grandes grupos de dispositivos de empresa. Esto es útil cuando los dispositivos se pueden asignar a usuarios de forma temporal o servir en un modo de quiosco que no requiera una asociación de usuario a dispositivo.|


## Sitios web de administración de Intune
 Las diferentes tareas administrativas requieren que se use uno de los siguientes sitios web administrativos, a los que se puede tener acceso mediante un [explorador web compatible](supported-web-browsers.md).

- [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Consola de administrador de Microsoft Intune](https://admin.manage.microsoft.com/)

### [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**Como administrador de inquilinos, use este portal para administrar la suscripción**, incluidas las tareas siguientes, siempre y cuando se lo permita el rol de administrador:

- Administrar cuentas de usuario para la suscripción y configurar la sincronización de directorios desde el Active Directory local.
- Administrar grupos de usuarios, denominados grupos de seguridad.
- Asignar licencias a los usuarios para usar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].
- Configurar el nombre de dominio que se utiliza con la suscripción. El nombre de dominio define la cuenta con la que los usuarios inician sesión.
- Administrar los detalles de facturación y de compras de su suscripción, incluido el número de licencias que posee, o la cantidad de espacio de almacenamiento en nube que puede utilizar.
- Buscar vínculos para ver el estado del servicio [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].
- Como administrador de inquilinos, puede iniciar sesión en el portal de Office 365 para administrar la suscripción, aunque su cuenta no tenga asignada una licencia para usar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].
- Cualquier usuario que tenga una licencia de Intune, pero no sea un administrador, puede usar este portal para restablecer la contraseña de su cuenta y editar su perfil.
- Para tener acceso al portal de Office 365, el estado de inicio de sesión de su cuenta debe ser **Permitido**. Este estado es distinto a tener una licencia para la suscripción. De manera predeterminada, todas las cuentas de usuario tienen el estado **Permitido**.


### [Consola de administrador de Microsoft Intune](https://admin.manage.microsoft.com/)

**Como administrador de servicios, use este portal para administrar las operaciones diarias** como:

- Establecer directivas para equipos y dispositivos móviles.
- Cargar e implementar software como actualizaciones de software y aplicaciones.
- Administrar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Endpoint Protection en los equipos.
- Ver el estado del dispositivo y ejecutar informes.
- Inicie sesión en este portal. Para iniciar sesión en este portal, debe tener permisos de administrador de servicios o ser un administrador de inquilinos con el rol de administrador global.


Solo los usuarios con permisos de administrador de servicios o que sean administradores de inquilinos con el rol de administrador global pueden iniciar sesión en este portal. Para tener acceso a la consola de administración, su cuenta debe tener una licencia para usar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] y un estado de inicio de sesión de **Permitido**.

Obtenga más información sobre cómo [agregar usuarios para su suscripción](start-with-a-paid-subscription-to-microsoft-intune-step-3.md) y cómo [asignar licencias para su suscripción](start-with-a-paid-subscription-to-microsoft-intune-step-4.md).

 ### Consulte también
 [What to know before you start Microsoft Intune (Información necesaria antes de iniciar Microsoft Intune)](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Aug16_HO4-->


