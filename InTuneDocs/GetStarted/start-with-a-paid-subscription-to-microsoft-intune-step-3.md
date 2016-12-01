---
title: Sincronizar Active Directory y agregar usuarios a Intune | Microsoft Intune
description: "Sincronización de usuarios locales con Azure AD y concesión de permisos de administrador para la suscripción de Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 33534c685ad3a4ddfd4b605e088132f2b8ff2c36


---


# <a name="sync-active-directory-and-add-users-to-intune"></a>Sincronizar Active Directory y agregar usuarios a Intune
Puede configurar la sincronización de directorios para importar las cuentas de usuario desde su instancia local de Active Directory a Microsoft Azure Active Directory (Azure AD). Tener el servicio local de Active Directory conectado con todos los servicios basados en Azure Active Directory facilita la administración de identidades de usuario en gran medida. También puede configurar características de inicio de sesión único para que la experiencia de autenticación resulte fácil y familiar a los usuarios.

Para facilitar todavía más las cosas, al usar varios servicios con el mismo [inquilino de Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/), las cuentas de usuario que se sincronizaron previamente están disponibles para todos los servicios basados en la nube que comparten la misma suscripción de inquilino de Azure AD.

## <a name="synchronize-on-premises-users-with-azure-ad"></a>Sincronizar usuarios locales con Azure AD
La única herramienta que necesita para sincronizar las cuentas de usuario con Azure AD es el [Asistente de Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). El Asistente de Azure AD Connect proporciona una experiencia guiada y simplificada que conectará su infraestructura de identidad local con la nube.  Elija la topología según sus necesidades (directorio único o varios directorios, sincronización de contraseñas o federación) y el Asistente implementará y configurará todos los componentes necesarios para preparar la conexión y ejecutarla. Esto incluye los servicios de sincronización, los servicios de federación de Active Directory (AD FS) y el módulo de PowerShell de Azure AD.

> [!TIP]
> Azure AD Connect abarca funciones que se publicaron anteriormente, como la Sincronización de directorios y la Sincronización de Azure AD. Obtenga más información sobre la [integración de directorios](http://technet.microsoft.com/library/jj573653.aspx). Para más información sobre las ventajas de sincronizar cuentas de usuario del directorio local con Azure AD, consulte [Similitudes entre Active Directory y Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## <a name="grant-administrator-permissions"></a>Conceder permisos de administrador

Para administrar Intune, usará:
- Dos tipos de cuentas de administrador
- Cuentas de usuario con permisos adicionales
- Dos consolas o portales de administración basados en web para conceder a los administradores acceso a los elementos que deban administrar.

Tras agregar usuarios adicionales a la suscripción de Intune, es recomendable conceder credenciales administrativas a algunas cuentas de usuario. La consola que debe usar para asignar credenciales administrativas depende del tipo de administrador que quiera asignar:

-   **Administrador de inquilinos**: use el **portal de la cuenta de Microsoft Intune** para asignar este tipo de administrador para administrar su suscripción, como la facturación, el almacenamiento en nube y la administración de los usuarios que pueden usar Intune.

-   **Administrador de servicios**: use la **consola de administrador de Microsoft Intune** para asignar este tipo de administrador para las tareas habituales, como la administración de dispositivos móviles o equipos, la implementación de directivas o software y la ejecución de informes.

Las siguientes secciones explican estas cuentas y portales.

## <a name="administrator-accounts-and-user-accounts-with-special-permissions"></a>Cuentas de administrador y cuentas de usuario con permisos especiales

Estas son las cuentas y los permisos que se usarán en Intune.

### <a name="tenant-administrator"></a>Administrador de inquilinos
|Niveles de permisos|Más información|
|--------------------------|-------------------------|
|A los administradores de inquilinos se les asigna un rol de administrador que define el ámbito administrativo para ese usuario y las tareas que pueden administrar.<br /><br />Los roles de administrador son comunes entre los diferentes servicios en la nube de Microsoft, aunque es posible que algunos servicios no sean compatibles con determinados roles.<br /><br /> Microsoft Intune usa los siguientes roles:<br /><br />- Administrador global<br />- Administrador de facturación<br />- Administrador de contraseñas<br />- Administrador de soporte técnico de servicio<br />- Administrador de control de usuarios|La cuenta que se usa para crear la suscripción de Microsoft Intune es, de forma predeterminada, un administrador de inquilinos con el rol de administrador global.<br /></br>  Como administrador de inquilinos, usará [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] para administrar la suscripción de Intune y para asignar administradores de inquilinos desde [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />Utilice un administrador de inquilinos con el rol de administración global para tener acceso a la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] y asignar así a su primer administrador de servicios. Como práctica recomendada, no utilice un administrador de inquilinos para tareas diarias de administración. Un administrador de inquilinos no requiere una licencia de Intune para acceder a [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />El administrador de inquilinos es un concepto común entre los servicios de nube de Microsoft. Cuando se suscribe a Intune, el servicio es un inquilino de Microsoft Azure AD. Vea la sección del inquilino de Azure AD en [¿Qué es un directorio de Azure AD?](http://technet.microsoft.com/library/jj573650.aspx).|


### <a name="service-administrator"></a>Administrador de servicios
|Niveles de permisos|Más información|
|--------------------------|-------------------------|
|A los administradores de servicios se les asigna uno de los siguientes permisos:<br /><br />**Acceso completo:** se otorga acceso a todas las áreas de la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)], sin restricciones. También puede agregar y administrar otros administradores de servicios.<br /><br />**Acceso de solo lectura:** se otorga permiso de lectura a todas las áreas de la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]. Un administrador de servicios de solo lectura no puede modificar los datos, pero puede ejecutar informes.<br /><br />**Departamento de soporte técnico - nodo Grupos:** se otorgan los permisos que permiten al administrador de servicios realizar solo un conjunto de tareas que suelen estar asociadas con escenarios del departamento de soporte técnico. Para obtener más información sobre este conjunto de permisos, vea [Personalizar vistas de consola de Intune según los roles de administración](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console).|De forma predeterminada, Intune no asigna un administrador de servicios. En su lugar, debe utilizar un administrador de inquilinos con el rol de administrador global para asignar el primer administrador de servicios de la suscripción. </br></br> Como administrador de servicios, debe usar la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] para administrar las tareas diarias de Intune.<br /><br />Los administradores de servicios se asignan desde la consola de administración. Un administrador de servicios requiere una licencia de Intune antes de que la cuenta pueda acceder a la consola de administración.|



### <a name="device-enrollment-managers"></a>Administradores de inscripción de dispositivos
|Niveles de permisos|Más información|
|--------------------------|-------------------------|
|Los administradores de inscripción de dispositivos son cuentas de usuario estándar que tienen permisos adicionales para inscribir más de cinco dispositivos.|De forma predeterminada, cada usuario de [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] puede inscribir hasta cinco dispositivos. Sin embargo, puede conceder a una cuenta de usuario el permiso de administrador de inscripción de dispositivos y, después, utilizar esa cuenta para inscribir grandes grupos de dispositivos de empresa. Esto es útil cuando los dispositivos se pueden asignar a usuarios de forma temporal o servir en un modo de quiosco que no requiera una asociación de usuario a dispositivo.|




>[!div class="step-by-step"]

>[&larr; **Configuración del dominio**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md) [**Administrar licencias de Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Nov16_HO4-->


