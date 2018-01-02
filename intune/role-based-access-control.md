---
title: RBAC con Intune
titleSuffix: Azure portal
description: "Versión preliminar de Intune Azure: aprenda cómo RBAC le permite controlar quién puede realizar acciones y efectuar cambios."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 791d93326ed1af173606d28639e92647ed7c1312
ms.sourcegitcommit: a7c1e10e615e5c975bb5d52eca986c5cf5287687
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2017
---
# <a name="role-based-administration-control-rbac-with-intune"></a>Control de administración basada en roles (RBAC) con Intune

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

    > [!TIP]
    > Intune también muestra tres extensiones de Azure AD: **usuarios**, **grupos** y **acceso condicional** que se controlan mediante RBAC en Azure AD. Además, el **administrador de cuentas de usuario** solo realiza actividades de usuario o grupo de AAD y no tiene permisos completos para realizar todas las actividades en Intune. Consulte [RBAC con Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) para obtener información más detallada.

## <a name="roles-created-in-the-intune-classic-portal"></a>Roles creados en el portal clásico de Intune

Solo los usuarios con roles de **administradores del servicio** de Intune con permisos "completos" pueden migrarse desde el portal clásico de Intune a Intune en Azure Portal. Debe reasignar a los usuarios con roles de **administradores del servicio** de Intune permisos de "Solo lectura" o "Departamento de soporte técnico" para acceder a los roles de Intune en Azure Portal y eliminarlos del portal clásico.

> [!IMPORTANT]
> Es posible que necesite mantener el acceso del administrador del servicio de Intune en el portal clásico en caso de que los administradores todavía necesiten acceder para administrar equipos con Intune.

## <a name="built-in-roles"></a>Roles integrados

Los siguientes roles están integrados en Intune y puede asignarlos a grupos sin necesidad de realizar ninguna configuración adicional:

- **Departamento de soporte técnico**: realiza tareas remotas relacionadas con usuarios y dispositivos y puede asignar aplicaciones o directivas a usuarios o dispositivos.
- **Administrador de directivas y perfiles**: administra la directiva de cumplimiento, los perfiles de configuración, la inscripción de Apple y los identificadores de dispositivos corporativos.
- **Operador de solo lectura**: ve información sobre usuarios, dispositivos, inscripciones, configuraciones y aplicaciones. No puede realizar ningún cambio en Intune.
- **Administrador de aplicaciones**: administra las aplicaciones móviles y administradas y puede leer la información del dispositivo.

### <a name="to-assign-a-built-in-role"></a>Para asignar un rol integrado

1. En **Roles de Intune**, elija el rol integrado que desea asignar.

2. En la hoja <*nombre del rol*> - **Propiedades**, elija **Administrar** y luego **Asignaciones**.

    > [!NOTE]
    > No se pueden eliminar ni editar los roles integrados

3. En la hoja de roles personalizados, elija **Asignar**.

4. En la hoja **Asignaciones de roles**, escriba un **nombre** y una **descripción** opcional para la asignación y luego elija lo siguiente:
    - **Miembros**: seleccione un grupo que contenga el usuario al que quiere conceder los permisos.
    - **Ámbito** seleccione un grupo que contenga los usuarios que tendrá permiso para administrar el miembro anterior.
<br></br>
5. Cuando haya terminado, haga clic en **Aceptar**. La nueva asignación se muestra en la lista de asignaciones.

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

2. Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Elija **Intune** y, cuando se abra el panel de Intune, seleccione **Roles de Intune**.

4. En la hoja **Roles de Intune**, elija **Roles de Intune** y después **Agregar personalizado**.

5. En la hoja **Agregar rol personalizado**, escriba un nombre y una descripción para el nuevo rol y luego haga clic en **Permisos**.

3. En la hoja **Permisos**, elija los permisos que quiere usar con este rol. Use la [tabla de RBAC en Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) para ayudarle a decidir qué permisos desea aplicar.

4. Cuando termine, elija **Aceptar**.

5. En la hoja **Agregar rol de personalizado**, haga clic en **Crear**. El nuevo rol se muestra en la lista de la hoja **Roles de Intune**.

### <a name="to-assign-a-custom-role"></a>Para asignar un rol personalizado

1. En **Roles de Intune**, elija el rol personalizado que desea asignar.

2. En la hoja <*nombre del rol*> - **Propiedades**, elija **Administrar** y luego **Asignaciones**. En esta hoja, también puede editar o eliminar roles existentes.

3. En la hoja de roles personalizados, elija **Asignar**.

4. En la hoja **Asignaciones de roles**, escriba un **nombre** y una **descripción** opcional para la asignación y luego elija lo siguiente:
    - **Miembros**: seleccione un grupo que contenga el usuario al que quiere conceder los permisos.
    - **Ámbito** seleccione un grupo que contenga los usuarios que tendrá permiso para administrar el miembro anterior.
<br></br>
5. Cuando haya terminado, haga clic en **Aceptar**. La nueva asignación se muestra en la lista de asignaciones.

## <a name="next-steps"></a>Pasos siguientes

[Use el rol Departamento de soporte técnico de Intune en el portal de solución de problemas](help-desk-operators.md)

## <a name="see-also"></a>Consulte también

[Asignación de roles mediante Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
