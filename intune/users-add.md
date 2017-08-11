---
title: Agregar usuarios y conceder permisos
description: "Sincronización de usuarios locales con Azure AD y concesión de permisos de administrador para la suscripción de Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7873481ccd33d2eaf4ec1a4c7fadf30c61b8d42e
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="add-users-and-give-administrative-permission-to-intune"></a>Agregar usuarios y conceder permiso administrativo a Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

En este tema se explica a los administradores cómo pueden agregar usuarios a Intune y qué permisos administrativos están disponibles en el servicio Intune.

Como administrador, puede agregar usuarios directamente o sincronizarlos desde la instancia local de Active Directory. Una vez agregados, los usuarios pueden inscribir dispositivos y obtener acceso a los recursos de la empresa. También puede conceder a los usuarios permisos adicionales, incluidos permisos de *administrador global* y de *administrador de servicios*.

## <a name="add-users-to-intune"></a>Agregar usuarios a Intune
Puede agregar usuarios manualmente a la suscripción de Intune mediante el [portal de Office 365](https://www.office.com/signin) o el [portal de Azure Intune](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview). Un administrador puede editar cuentas de usuario para asignar licencias de Intune. Puede asignar licencias en el portal de Office 365 o en el portal de Intune Azure. Para obtener más información sobre cómo usar el Portal de Office 365, vea [Agregar usuarios individualmente o de forma masiva al Portal de Office 365](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

### <a name="add-intune-users-in-the-office-365-admin-center"></a>Agregar usuarios de Intune en el Centro de administración de Office 365
1. Inicie sesión en el [Portal de Office 365](https://www.office.com/signin) con una cuenta de administrador de administración de usuarios o de administrador global.
2. En el menú de Office 365, seleccione **Administración**.
3. En el Centro de administración, seleccione **Agregar un usuario**.

  ![Captura de pantalla del Centro de administración de Office 365](media/office-add-user.png)

4. Especifique los siguientes detalles de usuario:
  - **Nombre**
  - **Apellido**
  - **Nombre para mostrar**
  - **Nombre de usuario**: nombre principal de usuario (UPN) almacenado en Azure Active Directory que se ha usado para tener acceso al servicio
  - **Ubicación**
  - **Información de contacto** (opcional)
  - **Contraseña**: generada automáticamente o especificar una

     ![Captura de pantalla del Centro de administración de Office 365](media/office-add-user-details.png)

5. Asigne una licencia de Intune. Seleccione **Licencias de productos** y seleccione la licencia de producto. Se necesita una licencia que incluya Intune.
6. Seleccione **Agregar** para crear el nuevo usuario.

### <a name="add-intune-users-in-the-azure-intune-portal"></a>Agregar usuarios de Intune en el portal de Azure Intune
1. Inicie sesión en [Azure Portal](https://portal.azure.com) y vaya a **Más servicios** > **Supervisión y administración** > **Intune**. También puede *buscar recursos* para **Intune**.
2. Seleccione **Usuarios**.
3. En el Centro de administración, seleccione **Nuevo usuario**.
  ![Captura de pantalla del Centro de administración de Office 365](media/intune-add-user.png)
4. Especifique los siguientes detalles de usuario:
  - **Nombre**
  - **Nombre de usuario**: el nuevo nombre en el portal de Azure Active Directory ![Captura de pantalla del Centro de administración de Office 365](media/intune-add-user-info.png) Seleccione **Aceptar** para continuar.
5. Opcionalmente, puede especificar las siguientes propiedades de usuario:
  - **Perfil**: información de trabajo, que incluye el **puesto** y el **departamento**.
  -  **Grupos**: seleccione los grupos que se van a agregar al usuario.
  - **Rol de directorio**: proporciona permisos administrativos al usuario incluido un rol de administrador de servicios de Intune.

  Seleccione **Crear** para agregar el nuevo usuario a Intune.
6. Seleccione **Perfil** y, después, elija una **Ubicación de uso** para el usuario nuevo. Es necesario especificar la ubicación de uso para poder asignar una licencia de Intune al nuevo usuario. Elija **Guardar** para continuar.
    ![Captura de pantalla del Centro de administración de Office 365](media/intune-add-user-loc.png)
7. Seleccione **Licencias** y, después, elija **Asignar** para asignar una licencia de Intune a este usuario. Se necesita una licencia de Intune para inscribir dispositivos o tener acceso a los recursos de la empresa. Seleccione **Productos**, pulse el tipo de licencia, pulse **Seleccionar** y, después, seleccione **Asignar**.

## <a name="grant-admin-permissions"></a>Conceder permisos de administrador

Tras agregar usuarios adicionales a la suscripción de Intune, le recomendamos que conceda permiso administrativo a algunos usuarios.  Para conceder permisos administrativos, siga estos pasos:

### <a name="give-admin-permissions-in-office-365"></a>Proporcionar permisos administrativos en Office 365
1. Inicie sesión en el [Portal de Office 365](https://www.office.com/signin) con una cuenta de administrador global.
2. En el menú de Office 365, seleccione **Administración**.
3. En el Centro de administración, pulse **Usuarios activos** y, después, elija el usuario al que se le van a proporcionar los permisos de administración.
4. En la columna **Roles**, pulse **Editar**.
  ![Captura de pantalla de la pantalla de asignación de roles en Office 365](./media/office-assign-roles-open.png)
5. Seleccione el permiso de administración que se va a conceder de la lista de roles disponibles.
![Imagen de la asignación de roles en el portal de Office 365.](./media/office-assign-roles.png)
6. Elija **Guardar**.

### <a name="give-admin-permissions-in-the-intune-portal"></a>Proporcionar permisos de administración en el portal de Intune
1. Inicie sesión en el [Portal de Intune](https://www.office.com/signin) con una cuenta de administrador global.
2. En el portal de Intune, seleccione **Usuario** y, después, elija el usuario al que quiere proporcionar los permisos administrativos.
3. Seleccione **Rol de directorio** y, después, seleccione el permiso.
  ![Captura de pantalla](./media/add-intune-directory-role.png)
4. Elija **Guardar**.

### <a name="types-of-administrators"></a>Tipos de administradores

Asigne a los usuarios uno o varios permisos de administrador. Estos permisos definen el ámbito administrativo de los usuarios y las tareas que pueden administrar. Los permisos de administrador son comunes entre los diferentes servicios en la nube de Microsoft, y es posible que algunos servicios no sean compatibles con determinados permisos. El portal de Intune y el portal de Office 365 muestran roles de administrador limitados que no usa Intune. Los permisos de administrador de Intune incluyen las opciones siguientes:

- **Administrador global**: (Office 365 e Intune) tiene acceso a todas las características administrativas de Intune. De manera predeterminada, la persona que se suscriba a Intune se convertirá en un administrador global. Los administradores globales son los únicos administradores que pueden asignar otros roles de administrador. Puede tener más de un administrador global en la organización. Como procedimiento recomendado, se recomienda que solo unas pocas personas de la empresa tengan este rol, a fin de disminuir el riesgo para la empresa.
- **Administrador de contraseñas**: (Office 365 e Intune) restablece contraseñas, administra solicitudes del servicio y supervisa el estado de dicho servicio. Los administradores de contraseñas están limitados a restablecer las contraseñas de los usuarios.
- **Administrador de servicio**: (Office 365 e Intune) abre solicitudes de soporte técnico con Microsoft y puede ver el panel de servicio y el centro de mensajes. Tienen permisos de "solo para visualización", excepto para abrir incidencias de soporte técnico y leerlas.
- **Administrador de facturación**: (Office 365 e Intune) hace compras, administra suscripciones e incidencias de soporte técnico, y supervisa el estado del servicio.
- **Administrador de usuarios**: (Office 365 e Intune) restablece contraseñas, supervisa el estado del servicio, agrega y elimina cuentas de usuario y, además, administra solicitudes de servicio. El administrador de control de usuarios no puede eliminar a un administrador global, crear otros roles de administrador ni restablecer las contraseñas de otros administradores.
- **Administrador de servicios de Intune**: todos los permisos de administrador global de Intune excepto el permiso para crear administradores con las opciones **Rol de directorio**.

La cuenta que se usa para crear la suscripción a Microsoft Intune es un administrador global. Como procedimiento recomendado, no use un administrador global para las tareas de administración cotidianas. Un administrador no requiere una licencia de Intune para acceder al portal de Intune. 

Para tener acceso al portal de Office 365, su cuenta debe tener establecido un **inicio de sesión permitido**. En el portal de Intune, en **Perfil**, establezca **Bloquear inicio de sesión** en **No** para permitir el acceso. Este estado es distinto a tener una licencia para la suscripción. De manera predeterminada, todas las cuentas de usuario tienen el estado **Permitido**. Los usuarios que no tienen permisos de administrador pueden usar el portal de Office 365 para restablecer las contraseñas de Intune.

## <a name="sync-active-directory-and-add-users-to-intune"></a>Sincronizar Active Directory y agregar usuarios a Intune
Puede configurar la sincronización de directorios para importar las cuentas de usuario desde la instancia local de Active Directory a Microsoft Azure Active Directory (Azure AD), que incluye los usuarios de Intune. Tener el servicio local de Active Directory conectado con todos los servicios basados en Azure Active Directory facilita la administración de identidades de usuario en gran medida. También puede configurar características de inicio de sesión único para que la experiencia de autenticación resulte fácil y familiar a los usuarios. Al vincular el mismo [inquilino de Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) con varios servicios, las cuentas de usuario que sincronizó previamente están disponibles para todos los servicios basados en la nube.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Sincronización de usuarios locales con Azure AD
La única herramienta que necesita para sincronizar las cuentas de usuario con Azure AD es el [Asistente de Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). El Asistente de Azure AD Connect proporciona una experiencia guiada y simplificada que conectará su infraestructura de identidad local con la nube.  Elija su topología y sus necesidades (uno o varios directorios, sincronización de contraseñas o federación). El asistente implementa y configura todos los componentes necesarios para preparar la conexión. Esto incluye los servicios de sincronización, los servicios de federación de Active Directory (AD FS) y el módulo de PowerShell de Azure AD.

> [!TIP]
> Azure AD Connect abarca funciones que se publicaron anteriormente, como la Sincronización de directorios y la Sincronización de Azure AD. Obtenga más información sobre la [integración de directorios](http://technet.microsoft.com/library/jj573653.aspx). Para obtener información sobre la sincronización de cuentas de usuario desde un directorio local con Azure AD, consulte [Similitudes entre Active Directory y Azure AD](http://technet.microsoft.com/library/dn518177.aspx).
