---
title: Asignación de un rol a un usuario de Intune
description: Obtenga información sobre cómo asignar un rol integrado o personalizado a un usuario de Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9e337d47757e3c5507c94433f90d5c2863bc1b0
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503014"
---
# <a name="assign-a-role-to-an-intune-user"></a>Asignación de un rol a un usuario de Intune

Puede asignar un rol [integrado](role-based-access-control.md#built-in-roles) o [personalizado](create-custom-role.md) a un usuario de Intune.

Para crear, editar o asignar roles, la cuenta debe tener uno de los siguientes permisos en Azure AD:
- **Administrador global**
- **Administrador del servicio de Intune**

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.

3. En la hoja **Intune**, seleccione **Roles** > **Todos los roles**.

4. En la hoja **Roles de Intune: Todos los roles**, elija el rol integrado que quiera asignar.

5. En la hoja <*nombre del rol*> - **Información general**, elija **Administrar** > **Asignaciones**.

6. En la hoja de roles personalizados, elija **Asignar**.

7. En la hoja **Asignaciones de roles**, escriba un **nombre de asignación** y una **descripción** opcional para la asignación.

8. En **Miembros (grupos)** , elija un grupo que contenga el usuario al que quiere conceder los permisos.

9. En **Ámbito (grupos)** , elija un grupo que contenga los usuarios o los dispositivos que el miembro anterior tendrá permiso para administrar.

10. En **Ámbito (etiquetas)** , elija las etiquetas donde se aplicará esta asignación de roles.

11. Cuando haya terminado, seleccione **Aceptar**. La nueva asignación se muestra en la lista de asignaciones.


## <a name="next-steps"></a>Pasos siguientes
- [Más información sobre el control de acceso basado en rol en Intune](role-based-access-control.md)
- [Creación de un rol personalizado](create-custom-role.md)
