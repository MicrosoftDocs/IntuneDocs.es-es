---
title: Agregar usuarios y conceder permisos | Microsoft Docs
description: "Sincronización de usuarios locales con Azure AD y concesión de permisos de administrador para la suscripción de Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ad13897fe7bbe4fe13167bb4ce7f558b436a7a90
ms.openlocfilehash: b1f16df329c01aeb45885f3981e2d9d7ef854e8b


---

# <a name="add-users-and-give-administrative-permission-to-intune"></a>Agregar usuarios y conceder permiso administrativo a Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

En este tema se explica a los administradores cómo pueden agregar usuarios a Intune y qué permisos administrativos están disponibles en el servicio Intune.

Como administrador, puede agregar usuarios directamente o sincronizarlos desde la instancia local de Active Directory. Una vez agregados, los usuarios pueden inscribir dispositivos y obtener acceso a los recursos de la empresa. También puede conceder a los usuarios permisos adicionales, incluidos permisos de *administrador de inquilinos*, permisos de *administrador de servicios* y permisos de *administrador de inscripción de dispositivos*.

Este tema le permite:

- [Agregar usuarios a Intune](#add-users-to-intune)
- [Conceder permisos adicionales de Intune](#grant-intune-permissions), como los permisos siguientes:
  - [Administrador de inquilinos](#tenant-administrator)
  - [Administrador de servicios](#service-administrator)
  - [Administradores de inscripción de dispositivos](#device-enrollment-managers)

## <a name="add-users-to-intune"></a>Agregar usuarios a Intune
Puede agregar manualmente usuarios a la suscripción de Intune mediante el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), pero no se les asigna ninguna licencia de Intune automáticamente. En vez de ello, un administrador de inquilinos de Intune deberá editar posteriormente la cuenta de usuario para asignar una licencia al usuario desde el portal de Office 365. Para instrucciones, consulte [Agregar usuarios individualmente o de forma masiva al portal de Office 365](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

### <a name="sync-active-directory-and-add-users-to-intune"></a>Sincronizar Active Directory y agregar usuarios a Intune
Puede configurar la sincronización de directorios para importar las cuentas de usuario desde la instancia local de Active Directory a Microsoft Azure Active Directory (Azure AD), que incluye los usuarios de Intune. Tener el servicio local de Active Directory conectado con todos los servicios basados en Azure Active Directory facilita la administración de identidades de usuario en gran medida. También puede configurar características de inicio de sesión único para que la experiencia de autenticación resulte fácil y familiar a los usuarios. Al vincular el mismo [inquilino de Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) con varios servicios, las cuentas de usuario que sincronizó previamente están disponibles para todos los servicios basados en la nube.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Sincronización de usuarios locales con Azure AD
La única herramienta que necesita para sincronizar las cuentas de usuario con Azure AD es el [Asistente de Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). El Asistente de Azure AD Connect proporciona una experiencia guiada y simplificada que conectará su infraestructura de identidad local con la nube.  Elija la topología según sus necesidades (directorio único o varios directorios, sincronización de contraseñas o federación) y el Asistente implementará y configurará todos los componentes necesarios para preparar la conexión y ejecutarla. Esto incluye los servicios de sincronización, los servicios de federación de Active Directory (AD FS) y el módulo de PowerShell de Azure AD.

> [!TIP]
> Azure AD Connect abarca funciones que se publicaron anteriormente, como la Sincronización de directorios y la Sincronización de Azure AD. Obtenga más información sobre la [integración de directorios](http://technet.microsoft.com/library/jj573653.aspx). Para más información sobre las ventajas de sincronizar cuentas de usuario del directorio local con Azure AD, consulte [Similitudes entre Active Directory y Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## <a name="grant-intune-permissions"></a>Conceder permisos de Intune

Tras agregar usuarios adicionales a la suscripción de Intune, es recomendable conceder permiso administrativo a algunas cuentas de usuario. Para administrar Intune, puede conceder tres tipos de permisos de Intune a los usuarios
-   **Administrador de inquilinos**: para asignar este tipo de administrador y administrar la suscripción, incluida la facturación, el almacenamiento en la nube y la administración de los usuarios que pueden usar Intune, use el portal de Office 365.
-   **Administrador de servicios**: use la consola de administrador de Microsoft Intune para asignar este tipo de administrador para las tareas habituales, como la administración de dispositivos o equipos, la implementación de directivas y aplicaciones, además de la ejecución de informes.
-   **Administrador de inscripción de dispositivos**: use la consola de administrador de Microsoft Intune para asignar este tipo de administrador para las tareas habituales, como la administración de dispositivos o equipos, la implementación de directivas y aplicaciones, además de la ejecución de informes.


### <a name="tenant-administrator"></a>Administrador de inquilinos


A los administradores de inquilinos se les asigna un rol de administrador que define el ámbito administrativo para ese usuario y las tareas que pueden administrar. Los roles de administrador son comunes entre los diferentes servicios en la nube de Microsoft, aunque es posible que algunos servicios no sean compatibles con determinados roles. Intune usa los roles siguientes:
- **Administrador global**: tiene acceso a todas las características administrativas de Intune. De manera predeterminada, la persona que se suscriba a Intune se convertirá en un administrador global. Los administradores globales son los únicos administradores que pueden asignar otros roles de administrador. Puede tener más de un administrador global en la organización. Como procedimiento recomendado, se recomienda que solo unas pocas personas de la empresa tengan este rol, a fin de disminuir el riesgo para la empresa.
- **Administrador de facturación**: realiza compras, administra suscripciones e incidencias de soporte técnico, y supervisa el estado del servicio.
- **Administrador de contraseñas**: restablece contraseñas, administra solicitudes del servicio y supervisa el estado de dicho servicio. Los administradores de contraseñas están limitados a restablecer las contraseñas de los usuarios.
- **Administrador de soporte de servicio**: abre solicitudes de soporte técnico con Microsoft y puede ver el panel de servicio y el centro de mensajes. Tienen permisos de "solo para visualización", excepto para abrir incidencias de soporte técnico y leerlas.
- **Administrador de control de usuarios**: restablece contraseñas, supervisa el estado del servicio, agrega y elimina cuentas de usuario y, además, administra solicitudes de servicio. El administrador de control de usuarios no puede eliminar a un administrador global, crear otros roles de administrador ni restablecer las contraseñas de administradores de facturación, global ni de servicios.

La cuenta que se usa para crear la suscripción de Microsoft Intune es, de forma predeterminada, un administrador de inquilinos con el rol de administrador global. Como administrador de inquilinos, usa la consola de administrador de Intune para administrar la suscripción de Intune y asignar administradores de inquilinos desde el [portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854). Use un administrador de inquilinos con el rol de administración global para obtener acceso al portal y asignar así su primer administrador de servicios. Como práctica recomendada, no utilice un administrador de inquilinos para tareas diarias de administración. Un administrador de inquilinos no requiere una licencia de Intune para obtener acceso a la consola de administrador de Intune. El administrador de inquilinos es un concepto común entre los servicios de nube de Microsoft. Cuando se suscribe a Intune, el servicio es un inquilino de Azure AD. Consulte la sección sobre el inquilino de Azure AD en [¿Qué es un directorio de Azure AD?](http://technet.microsoft.com/library/jj573650.aspx) para más información.

Como administrador de inquilinos, use el [portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para administrar la suscripción, incluidas las tareas siguientes, siempre y cuando se lo permita el rol de administrador:

- Administrar cuentas de usuario y configurar la sincronización de directorios desde la instancia local de Active Directory.
- Administrar grupos de usuarios, denominados grupos de seguridad.
- Asignar licencias de Intune a los usuarios.
- Configurar el nombre de dominio de la suscripción que se usa cuando los usuarios inician sesión (como contoso.com).
- Administrar la facturación y las compras, incluidas las licencias y el espacio de almacenamiento en la nube.
- Buscar vínculos para ver el estado del servicio de Intune.

Para tener acceso al portal de Office 365, el estado de inicio de sesión de su cuenta debe ser **Permitido**. Este estado es distinto a tener una licencia para la suscripción. De manera predeterminada, todas las cuentas de usuario tienen el estado **Permitido**. Los usuarios que no tienen permisos de administrador pueden usar el portal de Office 365 para restablecer las contraseñas de Intune.

### <a name="service-administrator"></a>Administrador de servicios

De forma predeterminada, Intune no asigna un administrador de servicios. En su lugar, debe utilizar un administrador de inquilinos con el rol de administrador global para asignar el primer administrador de servicios de la suscripción. Como administrador de servicios, debe usar la [consola de administrador de Intune](https://manage.microsoft.com/) para administrar las tareas habituales de Intune. Los administradores de servicios se asignan desde la consola de administración. Un administrador de servicios requiere una licencia de Intune para obtener acceso a la consola de administración.

A los administradores de servicios se les asigna uno de los siguientes permisos:
- **Acceso total**: acceso sin restricciones a todas las áreas de la consola de administrador de Intune; agregar y administrar a otros administradores de servicios.
- **Acceso de solo lectura**: permiso de lectura a todas las áreas de la consola de administrador de Intune; no se pueden modificar datos, pero sí ejecutar informes.
- **Departamento de soporte técnico - nodo de grupos**: permite que el administrador de servicios solo realice las tareas asociadas con los escenarios de departamento de soporte técnico; consulte [Personalizar vistas de consola de Intune según los roles de administración](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console).

Como administrador de servicios, use este portal para administrar las operaciones diarias como:

- Crear y administrar directivas para equipos y dispositivos móviles.
- Cargar e implementar aplicaciones y actualizaciones de software.
- Administrar Endpoint Protection en los equipos.
- Ver el estado del dispositivo y ejecutar informes.

### <a name="device-enrollment-managers"></a>Administradores de inscripción de dispositivos

Los administradores de inscripción de dispositivos son cuentas de usuario estándar con permisos adicionales para inscribir muchos más dispositivos sin usuarios. De manera predeterminada, cada usuario de Intune puede inscribir hasta quince dispositivos. Como administrador, puede conceder a una cuenta de usuario el permiso de administrador de inscripción de dispositivos. Esa cuenta puede inscribir grandes cantidades de dispositivos de propiedad de la empresa. Esto es útil cuando los dispositivos se pueden asignar a usuarios de forma temporal o servir en un modo de quiosco que no requiera una asociación de usuario a dispositivo. Para más información, consulte [Administrador de inscripción de dispositivos](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

>[!div class="step-by-step"]

>[&larr; **Configuración del dominio**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md) [**Administrar licencias de Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Feb17_HO3-->


