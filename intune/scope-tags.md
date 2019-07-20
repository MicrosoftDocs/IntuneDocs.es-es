---
title: Filtrado de directivas con etiquetas de ámbito en Microsoft Intune - Azure | Microsoft Docs
description: Use las etiquetas de ámbito para filtrar los perfiles de configuración por roles específicos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 627899eafb2175b2d3034045bd765a10f4a203d6
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882506"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Usar control de acceso basado en rol (RBAC) y etiquetas de ámbito para TI distribuida

Puede usar control de acceso basado en rol y etiquetas de ámbito para asegurarse de que los administradores adecuados tengan el acceso y la visibilidad correctos para los objetos de Intune apropiados. Los roles determinan qué acceso tienen los administradores a qué objetos. Las etiquetas de ámbito determinan qué objetos pueden ver los administradores.

Por ejemplo, imagine que a un administrador de la sucursal regional de Seattle se le asigna el rol Administrador de perfiles y directivas. Quiere que este administrador solo vea y administre los perfiles y las directivas que se aplican exclusivamente a los dispositivos de Seattle. Para ello, haría lo siguiente:

1. Crear una etiqueta de ámbito denominada Seattle.
2. Crear una asignación de roles para el rol Administrador de perfiles y directivas con: 
    - Miembros (grupos) = un grupo de seguridad denominado Administradores de TI de Seattle. Todos los administradores de este grupo tienen permiso para administrar las directivas y los perfiles de los usuarios o los dispositivos de Ámbito (grupos).
    - Ámbito (grupos) = un grupo de seguridad denominado Usuarios de Seattle. Todos los usuarios o dispositivos de este grupo pueden tener sus perfiles y directivas administrados por los administradores de Miembros (grupos). 
    - Ámbito (etiquetas) = Seattle. Los administradores de Miembros (grupos) pueden ver los dispositivos que tienen también la etiqueta de ámbito Seattle.
3. Agregar la etiqueta de ámbito Seattle a las directivas y los perfiles a los que quiere que puedan acceder los administradores de Miembros (grupos).
4. Agregar la etiqueta de ámbito Seattle a los dispositivos que quiere que sean visibles para los administradores de Miembros (grupos). 


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
3. Seleccione **Miembros (grupos)**  > **Agregar** > elija los grupos que quiera como parte de esta asignación > **Seleccionar** > **Aceptar**. Los usuarios de este grupo tienen permiso para administrar las directivas y los perfiles de los usuarios o los dispositivos de Ámbito (grupos).

    ![Captura de pantalla de la selección de grupos de miembros.](./media/scope-tags/select-member-groups.png)

4. Si quiere administrar los usuarios o dispositivos de un conjunto determinado de grupos, seleccione **Ámbito (grupos)**  > **Grupos seleccionados** > **Seleccionar grupos para incluir**> elija los grupos > **Seleccionar** > **Aceptar**. Todos los usuarios o dispositivos de este grupo pueden tener sus perfiles y directivas administrados por los administradores de Miembros (grupos).

    ![Captura de pantalla de la selección de grupos de ámbito.](./media/scope-tags/select-scope-groups.png)

    También puede seleccionar **Todos los dispositivos**, **Todos los usuarios** o **Todos los usuarios y todos los dispositivos**.

    ![Captura de pantalla de otras opciones para seleccionar grupos de ámbito.](./media/scope-tags/scope-group-other-options.png)
    
5. Seleccione **Ámbito (etiquetas)**  > **Agregar** > elija las etiquetas que quiera agregar a este rol > **Seleccionar** > **Aceptar**. Los usuarios de Miembros (grupos) tienen acceso a las directivas y los perfiles que además tienen la misma etiqueta de ámbito.

    ![Captura de pantalla de la selección de etiquetas de ámbito.](./media/scope-tags/select-scope-tags.png)

6. Elija **Aceptar**. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Para agregar una etiqueta de ámbito a un perfil de configuración
1. En Intune, seleccione **Configuración del dispositivo** > **Perfiles** > elija un perfil.

    ![Captura de pantalla de la selección de perfil.](./media/scope-tags/choose-profile.png)

2. Seleccione **Propiedades** > **Ámbito (etiquetas)**  > **Agregar**.

    ![Captura de pantalla de la adición de etiquetas de ámbito.](./media/scope-tags/add-scope-tags.png)

3. En **Seleccionar etiquetas**, seleccione las etiquetas que quiera agregar al perfil.
4. Seleccione **Seleccionar** > **Aceptar** > **Guardar**.

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>Para asignar una etiqueta de ámbito a una directiva de configuración de aplicación
En el caso de los dispositivos con **Tipo de inscripción del dispositivo** establecido en **Dispositivos administrados**:
1. Seleccione **Aplicaciones cliente** > **Directivas de configuración de aplicaciones** > elija una directiva de configuración de aplicación.
2. Seleccione **Propiedades** > **Ámbito (etiquetas)** > elija las etiquetas que quiera asignar a la directiva.

En el caso de los dispositivos con **Tipo de inscripción del dispositivo** establecido en **Aplicaciones administradas**:
1. Seleccione **Aplicaciones cliente** > **Directivas de configuración de aplicaciones** > elija una directiva de configuración de aplicación.
2. Seleccione **Ámbito (etiquetas)** > elija las etiquetas que quiera asignar a la directiva.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>Para asignar una etiqueta de ámbito a un perfil de aprovisionamiento de aplicación iOS
1. En Intune, seleccione **Aplicaciones cliente** > **Perfiles de aprovisionamiento de aplicaciones de iOS** > elija un perfil.
2. Seleccione **Propiedades** > **Ámbito (etiquetas)** > elija las etiquetas que quiera asignar al perfil.
3. Seleccione **Seleccionar** > **Aceptar** > **Guardar**.

## <a name="to-assign-a-scope-tag-to-an-apple-volume-purchase-program-vpp-token"></a>Para asignar una etiqueta de ámbito a un token del Programa de Compras por Volumen de Apple (VPP)
1. En Intune, seleccione **Aplicaciones cliente** > **Tokens de VPP de Apple** > elija un token de VPP.
2. Seleccione **Ámbito (etiquetas)** > elija las etiquetas que quiera asignar al perfil. Las aplicaciones y los libros electrónicos de VPP asociados al token de VPP heredan las etiquetas asignadas.
3. Seleccione **Seleccionar** > **Aceptar** > **Guardar**.

## <a name="scope-tag-details"></a>Detalles de las etiquetas de ámbito
Al trabajar con etiquetas de ámbito, recuerde estos detalles:

- De momento, puede asignar etiquetas de ámbito a:
  - Asignaciones de roles
  - Directivas de cumplimiento de dispositivos
  - Perfiles de configuración de dispositivos
  - Anillos de actualización de Windows 10
  - Dispositivos administrados
  - Aplicaciones
  - Directivas de configuración de aplicaciones: dispositivos administrados
  - Scripts de PowerShell
  - Token de DEP
  - Perfil de aprovisionamiento de aplicaciones de iOS
  - Tokens del Programa de Compras por Volumen (VPP)
- Cuando un administrador crea un objeto en Intune, todas las etiquetas de ámbito asignadas a ese administrador se asignan automáticamente al nuevo objeto.
- El RBAC de Intune no se aplica a los roles de Azure Active Directory. Por lo tanto, los roles Administradores de servicios de Intune y Administradores globales tienen acceso de administrador completo a Intune independientemente de las etiquetas de ámbito que tengan.
- Los administradores de una asignación de roles con etiquetas de ámbito también pueden ver objetos de Intune sin etiquetas de ámbito.
- Solo puede asignar una etiqueta de ámbito que tenga en las asignaciones de roles.
- Solo puede dirigirse a grupos que aparezcan en el Ámbito (grupos) de la asignación de roles.
- Si tiene una etiqueta de ámbito asignada a su rol, no puede eliminar todas las etiquetas de ámbito en un objeto de Intune. Se necesita al menos una etiqueta de ámbito.

## <a name="next-steps"></a>Pasos siguientes

Administre sus [roles](role-based-access-control.md) y [perfiles](device-profile-assign.md).
