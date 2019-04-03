---
title: Filtrado de directivas con etiquetas de ámbito en Microsoft Intune - Azure | Microsoft Docs
description: Use las etiquetas de ámbito para filtrar los perfiles de configuración por roles específicos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb57ea2ef5c99c58968ee25b3a75b2165ece787a
ms.sourcegitcommit: 0adb41c0640743d5cb726e66ad2427e3ad6faf20
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658556"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Utilice el control de acceso basado en roles (RBAC) y las etiquetas de ámbito para la TI

Puede usar etiquetas de control y el ámbito de acceso basado en rol para asegurarse de que los administradores de la derecha tienen el derecho de acceso y la visibilidad a los objetos de Intune adecuados. Los roles determinan qué acceso a los administradores tienen a los objetos. Las etiquetas de ámbito determinan qué objetos de los administradores pueden ver.

Por ejemplo, supongamos que un administrador de la oficina de Seattle se asigna el rol Administrador de perfiles y directivas. Desea que este administrador para ver y administrar solo los perfiles y las directivas que se aplican solo a dispositivos de Seattle. Para ello, lo siguiente:

1. Cree una etiqueta de ámbito denominada a Seattle.
2. Crear una asignación de roles para el rol de administrador de perfiles y directivas con: 
    - Miembros (grupos) = un grupo de seguridad denominado Administradores de TI de Seattle. Todos los administradores de este grupo tendrá permiso para administrar las directivas y perfiles de usuarios o dispositivos en el ámbito (grupos).
    - Ámbito (grupos) = la seguridad de una grupo denominado usuarios de Seattle. Todos los usuarios o dispositivos de este grupo puede tener sus perfiles y directivas administrados por los administradores en los miembros (grupos). 
    - Ámbito (etiquetas) = Seattle. Los administradores en el miembro (grupos) pueden ver los dispositivos que tienen también la etiqueta de ámbito de Seattle.
3. Agregue la etiqueta de ámbito de Seattle con las directivas y perfiles que desee que los administradores de miembros (grupos) para tener acceso a.
4. Agregue la etiqueta de ámbito de Seattle a los dispositivos que desea que estén visibles para los administradores en los miembros (grupos). 


## <a name="to-create-a-scope-tag"></a>Para crear una etiqueta de ámbito

1. En Intune, elija **Roles** > **ámbito (etiquetas)** > **crear**.

    ![Captura de pantalla de creación de una etiqueta de ámbito.](./media/scope-tags/create-scope-tag.png)

2. Proporcione un **Nombre** y una **Descripción**.
3. Elija **Crear**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Para asignar una etiqueta de ámbito a un rol

1. En Intune, elija **Roles** > **todos los roles** > elija un rol > **asignaciones** > **asignar**.

    ![Captura de pantalla de asignación de ámbito a un rol.](./media/scope-tags/assign-scope-to-role.png)

2. Proporcione un **nombre de la asignación** y **descripción**.
3. Elija **miembros (grupos)** > **agregar** > elija los grupos que desee como parte de esta asignación > **seleccione**  >   **Aceptar**. mUsers en este grupo tendrán permisos para administrar las directivas y perfiles de usuarios o dispositivos en el ámbito (grupos).

    ![Captura de pantalla de grupos de selección de miembros.](./media/scope-tags/select-member-groups.png)

4. Si desea administrar usuarios o dispositivos en un conjunto específico de grupos, elija **ámbito (grupos)** > **grupos seleccionados** > **seleccionar grupos para incluir**> elija los grupos > **seleccione** > **Aceptar**. Todos los usuarios o dispositivos de este grupo puede tener sus perfiles y directivas administrados por los administradores en los miembros (grupo).

    ![Captura de pantalla de grupos de ámbitos de select.](./media/scope-tags/select-scope-groups.png)

    Como alternativa, puede elegir **todos los dispositivos**, **todos los usuarios**, o **todos los usuarios y todos los dispositivos**.

    ![Captura de pantalla de otras opciones para grupos de ámbitos de select.](./media/scope-tags/scope-group-other-options.png)
    
5. Elija **ámbito (etiquetas)** > **agregar** > elija las etiquetas que desea agregar a este rol > **seleccione** > **Aceptar**. Los usuarios de miembros (grupos) tendrá acceso a las directivas y perfiles que también tienen la misma etiqueta de ámbito.

    ![Captura de pantalla de las etiquetas de ámbito seleccione.](./media/scope-tags/select-scope-tags.png)

6. Elija **Aceptar**. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Para agregar una etiqueta de ámbito a un perfil de configuración
1. En Intune, elija **configuración del dispositivo** > **perfiles** > elija un perfil.

    ![Captura de pantalla de Seleccionar perfil.](./media/scope-tags/choose-profile.png)

2. Elija **propiedades** > **ámbito (etiquetas)** > **agregar**.

    ![Captura de pantalla de agregar etiquetas de ámbito.](./media/scope-tags/add-scope-tags.png)

3. En **seleccionar etiquetas**, elija las etiquetas que desea agregar al perfil.
4. Elija **seleccione** > **Aceptar** > **guardar**.

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>Para asignar una etiqueta de ámbito a una directiva de configuración de aplicación
Para dispositivos con **tipo de inscripción del dispositivo** establecido en **dispositivos administrados**:
1. Elija **las aplicaciones cliente** > **directivas de configuración** > elija una directiva de configuración de la aplicación.
2. Elija **propiedades** > **ámbito (etiquetas)** > elija las etiquetas que desea asignar a la directiva.

Para dispositivos con **tipo de inscripción del dispositivo** establecido en **aplicaciones administradas**:
1. Elija **las aplicaciones cliente** > **directivas de configuración** > elija una directiva de configuración de la aplicación.
2. Elija **ámbito (etiquetas)** > elija las etiquetas que desea asignar a la directiva.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>Para asignar una etiqueta de ámbito a un perfil de aprovisionamiento de aplicaciones de iOS
1. En Intune, elija **las aplicaciones cliente** > **perfiles de aprovisionamiento de aplicaciones iOS** > elija un perfil.
2. Elija **propiedades** > **ámbito (etiquetas)** > elija las etiquetas que desea asignar al perfil.
3. Elija **seleccione** > **Aceptar** > **guardar**.

## <a name="scope-tag-details"></a>Detalles de la etiqueta de ámbito
Cuando se trabaja con las etiquetas de ámbito, recuerde estos detalles:

- Ahora puede asignar a las etiquetas de ámbito:
    - Asignaciones de roles
    - Directivas de cumplimiento de dispositivos
    - Perfiles de configuración de dispositivos
    - Anillos de actualizaciones de Windows 10
    - Dispositivos administrados
    - Aplicaciones
    - Directivas de configuración: los dispositivos administrados
    - Scripts de PowerShell
    - Token de DEP
    - Perfil de aprovisionamiento de aplicaciones de iOS
- Cuando un administrador crea un objeto en Intune, todas las etiquetas de ámbito asignadas a dicho administrador se asignará automáticamente al nuevo objeto.
- RBAC en Intune no se aplica a los roles de Azure Active Directory. Por lo tanto, los roles de administradores de servicios de Intune y los administradores globales tienen acceso de administrador completo a Intune independientemente de qué etiquetas de ámbito que tienen.
- Los administradores en una asignación de roles con las etiquetas de ámbito también pueden ver los objetos de Intune sin etiquetas de ámbito.
- Solo se puede asignar una etiqueta de ámbito que tiene en las asignaciones de rol.
- Puede que solo los grupos de destino que se muestran en el ámbito (grupos) de la asignación de roles.
- Si tiene una etiqueta de ámbito asignada a su rol, no se puede eliminar todas las etiquetas de ámbito en un objeto de Intune. Etiqueta de al menos un ámbito es necesaria.

## <a name="next-steps"></a>Pasos siguientes

Administre sus [roles](role-based-access-control.md) y [perfiles](device-profile-assign.md).
