---
title: Usar el control de acceso basado en rol (RBAC) y las etiquetas de ámbito para distribuirlo en Intune | Microsoft Docs
description: Use las etiquetas de ámbito para filtrar los perfiles de configuración por roles específicos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.assetid: a21d3039-f2ed-4f43-b6fa-d00c071edbc4
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b92dca399afeb035bf58d998efdd469318de389
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504947"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Usar control de acceso basado en rol (RBAC) y etiquetas de ámbito para TI distribuida

Puede usar control de acceso basado en rol y etiquetas de ámbito para asegurarse de que los administradores adecuados tengan el acceso y la visibilidad correctos para los objetos de Intune apropiados. Los roles determinan qué acceso tienen los administradores a qué objetos. Las etiquetas de ámbito determinan qué objetos pueden ver los administradores.

Por ejemplo, imagine que un administrador de la sucursal regional de Seattle tiene el rol Administrador de perfiles y directivas. Quiere que este administrador solo vea y administre los perfiles y las directivas que se aplican exclusivamente a los dispositivos de Seattle. Para configurar este acceso, debería:

1. Crear una etiqueta de ámbito denominada Seattle.
2. Crear una asignación de roles para el rol Administrador de perfiles y directivas con: 
    - Miembros (grupos) = un grupo de seguridad denominado Administradores de TI de Seattle. Todos los administradores de este grupo tienen permiso para administrar las directivas y los perfiles de los usuarios o los dispositivos de Ámbito (grupos).
    - Ámbito (grupos) = un grupo de seguridad denominado Usuarios de Seattle. Todos los usuarios o dispositivos de este grupo pueden tener sus perfiles y directivas administrados por los administradores de Miembros (grupos). 
    - Ámbito (etiquetas) = Seattle. Los administradores de Miembros (grupos) pueden ver los objetos de Intune que tienen también la etiqueta de ámbito Seattle.
3. Agregue la etiqueta de ámbito Seattle a las directivas y los perfiles a los que quiera que puedan tener acceso los administradores de Miembros (grupos).
4. Agregar la etiqueta de ámbito Seattle a los dispositivos que quiere que sean visibles para los administradores de Miembros (grupos). 

## <a name="default-scope-tag"></a>Etiquetas de ámbito predeterminadas
La etiqueta de ámbito predeterminada se agrega automáticamente a todos los objetos sin etiqueta que admiten etiquetas de ámbito.

Esta característica es similar a la característica de ámbitos de seguridad de System Center Configuration Manager. 

## <a name="to-create-a-scope-tag"></a>Para crear una etiqueta de ámbito

1. En Intune, seleccione **Roles** > **Ámbito (etiquetas)**  > **Crear**.

    ![Captura de pantalla de la creación de una etiqueta de ámbito.](./media/scope-tags/create-scope-tag.png)

3. Si quiere que todos los dispositivos estén en grupos específicos, elija **asignar etiqueta de ámbito a todos los dispositivos de los grupos seleccionados**.
    1. En la página **seleccionar grupos que se van a incluir** , elija los grupos que contengan los dispositivos a los que desea asignar esta etiqueta de ámbito.
    2. Elija **Seleccionar**.
4. Elija **Crear**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Para asignar una etiqueta de ámbito a un rol

1. En Intune, seleccione **Roles** > **Todos los roles** > elija un rol > **Asignaciones** > **Asignar**.

    ![Captura de pantalla de la asignación de un ámbito a un rol.](./media/scope-tags/assign-scope-to-role.png)

2. Proporcione un **Nombre de asignación** y una **Descripción**.
3. Seleccione **Miembros (grupos)**  > **Agregar** > elija los grupos que quiera como parte de esta asignación > **Seleccionar** > **Aceptar**. Los usuarios de este grupo tendrán permisos para administrar usuarios y dispositivos en el ámbito (grupos).

    ![Captura de pantalla de la selección de grupos de miembros.](./media/scope-tags/select-member-groups.png)

4. Si quiere administrar los usuarios o dispositivos de un conjunto determinado de grupos, seleccione **Ámbito (grupos)**  > **Grupos seleccionados** > **Seleccionar grupos para incluir**> elija los grupos > **Seleccionar** > **Aceptar**. Todos los usuarios o dispositivos de este grupo serán administrados por los administradores de los miembros (grupo).

    ![Captura de pantalla de la selección de grupos de ámbito.](./media/scope-tags/select-scope-groups.png)

    También puede seleccionar **Todos los dispositivos**, **Todos los usuarios** o **Todos los usuarios y todos los dispositivos**.

    ![Captura de pantalla de otras opciones para seleccionar grupos de ámbito.](./media/scope-tags/scope-group-other-options.png)
    
5. Seleccione **Ámbito (etiquetas)**  > **Agregar** > elija las etiquetas que quiera agregar a este rol > **Seleccionar** > **Aceptar**. Los usuarios de miembros (grupos) tendrán acceso a los objetos de Intune que también tienen la misma etiqueta de ámbito.

    ![Captura de pantalla de la selección de etiquetas de ámbito.](./media/scope-tags/select-scope-tags.png)

6. Elija **Aceptar**. 

## <a name="assign-scope-tags-to-other-objects"></a>Asignar etiquetas de ámbito a otros objetos

En el caso de los objetos que admiten etiquetas de ámbito, las etiquetas de ámbito suelen aparecer en **propiedades**. Por ejemplo, para asignar una etiqueta de ámbito a un perfil de configuración, siga estos pasos:

1. En Intune, seleccione **Configuración del dispositivo** > **Perfiles** > elija un perfil.

    ![Captura de pantalla de la selección de perfil.](./media/scope-tags/choose-profile.png)

2. Seleccione **Propiedades** > **Ámbito (etiquetas)**  > **Agregar**.

    ![Captura de pantalla de la adición de etiquetas de ámbito.](./media/scope-tags/add-scope-tags.png)

3. En **Seleccionar etiquetas**, seleccione las etiquetas que quiera agregar al perfil.
4. Seleccione **Seleccionar** > **Aceptar** > **Guardar**.


## <a name="scope-tag-details"></a>Detalles de las etiquetas de ámbito
Al trabajar con etiquetas de ámbito, recuerde estos detalles: 

- Puede asignar etiquetas de ámbito a un tipo de objeto de Intune si el inquilino puede tener varias versiones de ese objeto (como asignaciones de roles o aplicaciones).
  Los siguientes objetos de Intune son excepciones a esta regla y actualmente no admiten etiquetas de ámbito:
    - Perfiles ESP de Windows
    - Categorías de dispositivos
    - Restricciones de inscripción
    - Identificadores de dispositivo Corp
    - Dispositivos AutoPilot
    - Ubicaciones de cumplimiento de dispositivos
    - Dispositivos Jamf
- Las aplicaciones de PCV y los libros electrónicos asociados al token de PCV heredan las etiquetas de ámbito asignadas al token de PCV asociado.
- Los dispositivos Programa de inscripción de dispositivos (DEP) y los perfiles de DEP asociados al token de DEP heredan las etiquetas de ámbito asignadas al token de DEP asociado.
- Cuando un administrador crea un objeto en Intune, todas las etiquetas de ámbito asignadas a ese administrador se asignan automáticamente al nuevo objeto.
- El RBAC de Intune no se aplica a los roles de Azure Active Directory. Por lo tanto, los roles Administradores de servicios de Intune y Administradores globales tienen acceso de administrador completo a Intune independientemente de las etiquetas de ámbito que tengan.
- Si una asignación de roles no tiene etiqueta de ámbito, el administrador de ti puede ver todos los objetos en función de los permisos de los administradores de ti. Los administradores que no tienen etiquetas de ámbito esencialmente tienen etiquetas de ámbito.
- Solo puede asignar una etiqueta de ámbito que tenga en las asignaciones de roles.
- Solo puede dirigirse a grupos que aparezcan en el Ámbito (grupos) de la asignación de roles.
- Si tiene una etiqueta de ámbito asignada a su rol, no puede eliminar todas las etiquetas de ámbito en un objeto de Intune. Se necesita al menos una etiqueta de ámbito.

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre cómo se comportan las etiquetas de ámbito cuando hay [varias asignaciones de roles](role-based-access-control.md#multiple-role-assignments).
Administre sus [roles](role-based-access-control.md) y [perfiles](../configuration/device-profile-assign.md).
