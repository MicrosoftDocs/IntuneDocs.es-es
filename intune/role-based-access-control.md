---
title: RBAC con Microsoft Intune
description: Sepa cómo el control de acceso basado en roles (RBAC) le permite controlar quién puede realizar acciones y efectuar cambios en Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 745fd366520ba55e54a5b666d47469debb241ab9
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831537"
---
# <a name="role-based-administration-control-rbac-with-microsoft-intune"></a>Control de administración basada en roles (RBAC) con Microsoft Intune

RBAC ayuda a controlar quién puede realizar diversas tareas de Intune dentro de su organización y a quién se aplican dichas tareas. Puede usar los roles integrados que abarcan algunos escenarios de Intune comunes, o crear los suyos propios. Un rol se define mediante:

- **Definición de roles**: el nombre de un rol, los recursos que administra y los permisos concedidos para cada recurso.
- **Miembros**: los grupos de usuarios a los que se conceden los permisos.
- **Ámbito**: los grupos de usuarios o dispositivos que los miembros pueden administrar.
- **Asignación**: una vez configurados la definición, los miembros y el ámbito, se asigna el rol.

![Ejemplo de RBAC en Intune](./media/intune-rbac-1.PNG)

Con la nueva versión de Azure Portal, **Azure Active Directory (Azure AD)** ofrece dos roles de directorio que se pueden usar con Intune. A estos roles se les conceden permisos completos para realizar todas las actividades en Intune:

- **Administrador global:** los usuarios con este rol tienen acceso a todas las características administrativas de Azure AD, así como a los servicios que permiten la federación con Azure AD, como Exchange Online, SharePoint Online y Skype Empresarial Online. La persona que se suscribe al inquilino de Azure AD se convierte en administrador global. Solo los administradores globales pueden asignar otros roles de administrador de Azure AD. Puede haber más de un administrador global en tu organización. Los administradores globales pueden restablecer la contraseña de cualquier usuario y de todos los administradores.

- **Administrador del servicio de Intune:** los usuarios con este rol tienen permisos globales en Intune cuando el servicio está presente. Además de cualquier restricción reemplazada de Azure, este rol ofrece la posibilidad de administrar usuarios, dispositivos y de crear y administrar grupos de Intune.

- **Administrador de acceso condicional:** los usuarios con este rol solo tienen permisos para ver, crear, modificar y eliminar directivas de acceso condicional.

    > [!IMPORTANT]
    > El rol de administrador del servicio de Intune no proporciona la capacidad para administrar la configuración de acceso condicional de Azure AD.
    > Para asignar un rol de Intune a un usuario, este debe tener una licencia de Intune.

    > [!TIP]
    > Intune también muestra tres extensiones de Azure AD: **Usuarios**, **Grupos** y **Acceso condicional**, que se controlan mediante RBAC en Azure AD. Además, el **administrador de cuentas de usuario** solo realiza actividades de usuario o grupo de AAD y no tiene permisos completos para realizar todas las actividades en Intune. Para más información, vea [RBAC con Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).

## <a name="roles-created-in-the-intune-classic-portal"></a>Roles creados en el portal clásico de Intune

Solo los usuarios con roles de **administradores del servicio** de Intune con permisos "completos" pueden migrarse desde el portal clásico de Intune a Intune en Azure Portal. Debe reasignar a los usuarios con roles de **administradores del servicio** de Intune y con los permisos "Solo lectura" o "Departamento de soporte técnico" a los roles de Intune en Azure Portal y eliminarlos del portal clásico.

> [!IMPORTANT]
> Es posible que necesite mantener el acceso del administrador del servicio de Intune en el portal clásico en caso de que los administradores todavía necesiten acceder para administrar equipos con Intune.

## <a name="built-in-roles"></a>Roles integrados

Puede asignar roles integrados a los grupos sin ninguna configuración adicional. No se pueden eliminar ni editar los roles integrados.

- **Operador del departamento de soporte técnico**: realiza tareas remotas relacionadas con usuarios y dispositivos y puede asignar aplicaciones o directivas a usuarios o dispositivos.
- **Administrador de directivas y perfiles**: administra la directiva de cumplimiento, los perfiles de configuración, la inscripción de Apple y los identificadores de dispositivos corporativos.
- **Operador de solo lectura**: ve información sobre usuarios, dispositivos, inscripciones, configuraciones y aplicaciones. No puede realizar cambios en Intune.
- **Administrador de aplicaciones**: permite administrar las aplicaciones móviles y administradas, leer la información del dispositivo y ver los perfiles de configuración del dispositivo.
- **Administrador de roles de Intune**: permite administrar los roles de Intune personalizados y agregar las asignaciones de roles de Intune integrados. Esta es la única función de Intune que permite asignar permisos a los administradores.
- **Administrador de la escuela**: administra dispositivos de Windows 10 en [Intune for Education](introduction-intune-education.md) y puede realizar las acciones siguientes: 

    |Permission|Operación|
    |---|---|
    |Datos de auditoría|Lectura|
    |DeviceConfigurations|Asignar, Crear, Eliminar, Leer, Actualizar|
    |Administradores de inscripción de dispositivos|Leer, Actualizar|
    |Dispositivos administrados|Leer, Actualizar<!--, Delete [To be added in 1803]-->|
    |Aplicaciones móviles|Asignar, Crear, Eliminar, Leer, Actualizar|
    |Reports|Lectura|
    |Acciones remotas|Limpiar PC, Reiniciar, Bloqueo remoto, Retirar, Sincronizar dispositivos, Borrar|
    |Organización|Lectura|

### <a name="to-assign-a-built-in-role"></a>Para asignar un rol integrado

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, seleccione **Roles** > **Todos los roles**.
4. En el panel **Roles de Intune: todos los roles**, elija el rol integrado que quiera asignar.

5. En el panel <*nombre del rol*> - **Introducción**, elija **Administrar** y luego **Asignaciones**.

6. En el panel de roles personalizados, elija **Asignar**.

7. En el panel **Asignaciones de rol**, escriba un **Nombre** y una **Descripción** opcional para la asignación.

8. Para **Miembros**, elija un grupo que contenga el usuario al que quiere conceder los permisos.

9. Para **Ámbito**, elija un grupo que contenga los usuarios que el miembro anterior tendrá permiso para administrar.
<br></br>
10. Cuando haya terminado, seleccione **Aceptar**. La nueva asignación se muestra en la lista de asignaciones.

### <a name="intune-rbac-table"></a>Tabla de RBAC en Intune

- Descargue la [tabla de RBAC en Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) para ver más detalles sobre lo que puede hacer cada rol.

## <a name="custom-roles"></a>Roles personalizados

Puede crear un rol personalizado que incluye los permisos necesarios para una función de trabajo específica. Por ejemplo, si un grupo del departamento de TI administra las aplicaciones, las directivas y los perfiles de configuración, puede agregar todos los permisos juntos en un rol personalizado.

> [!IMPORTANT]
> Para crear, editar o asignar roles, la cuenta debe tener uno de los siguientes permisos en Azure AD:
> - **Administrador global**
> - **Administrador del servicio de Intune**

### <a name="to-create-a-custom-role"></a>Para crear un rol personalizado

1. Inicie sesión en [Azure Portal](https://portal.azure.com) con las credenciales de Intune.

2. Elija **Todos los servicios** en el menú de la izquierda y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Seleccione **Intune** > **Roles** > **Todos los roles** > **Agregar personalizado**.

4. En el panel **Agregar rol personalizado**, escriba un nombre y una descripción para el nuevo rol y luego haga clic en **Permisos**.

5. En el panel **Permisos**, elija los permisos que quiere usar con este rol. Use la [tabla de RBAC en Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) para ayudarle a decidir qué permisos desea aplicar.

6. Cuando haya terminado, seleccione **Aceptar**.

7. En el panel **Agregar rol personalizado**, haga clic en **Crear**. El nuevo rol se muestra en la lista del panel **Roles de Intune: todos los roles**.

### <a name="to-assign-a-custom-role"></a>Para asignar un rol personalizado

1. En el panel **Roles de Intune: todos los roles**, elija el rol personalizado que quiera asignar.

2. En el panel <*nombre del rol*> - **Introducción**, elija **Administrar** y luego **Asignaciones**. En este panel, también puede editar o eliminar roles existentes.

3. En el panel de roles personalizados, elija **Asignar**.

4. En el panel **Asignaciones de rol**, escriba un **Nombre** y una **Descripción** opcional para la asignación.

5. Para **Miembros**, elija un grupo que contenga el usuario al que quiere conceder los permisos.

6. Para **Ámbito**, elija un grupo que contenga los usuarios que el miembro anterior tendrá permiso para administrar.

7. Cuando haya terminado, seleccione **Aceptar**. La nueva asignación se muestra en la lista de asignaciones.

## <a name="next-steps"></a>Pasos siguientes

[Use el rol Departamento de soporte técnico de Intune en el portal de solución de problemas](help-desk-operators.md)

## <a name="see-also"></a>Consulte también

[Asignación de roles mediante Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
