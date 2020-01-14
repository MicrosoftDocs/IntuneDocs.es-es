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
ms.openlocfilehash: c82805bf70259d43d738644e5663b93533bcb56a
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207169"
---
# <a name="assign-a-role-to-an-intune-user"></a>Asignación de un rol a un usuario de Intune

Puede asignar un rol [integrado](role-based-access-control.md#built-in-roles) o [personalizado](create-custom-role.md) a un usuario de Intune.

Para crear, editar o asignar roles, la cuenta debe tener uno de los siguientes permisos en Azure AD:
- **Administrador global**
- **Administrador del servicio de Intune**

1. En el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Roles** > **Todos los roles**.

2. En la hoja **Roles de Intune: Todos los roles**, elija el rol integrado que quiera asignar.

3. En la hoja <*nombre del rol*> - **Información general**, elija **Administrar** > **Asignaciones**.

4. En la hoja de roles personalizados, elija **Asignar**.

5. En la hoja **Asignaciones de roles**, escriba un **nombre de asignación** y una **descripción** opcional para la asignación.

6. En **Miembros (grupos)** , elija un grupo que contenga el usuario al que quiere conceder los permisos.

7. En **Ámbito (grupos)** , elija un grupo que contenga los usuarios o los dispositivos que el miembro anterior tendrá permiso para administrar.

8. En **Ámbito (etiquetas)** , elija las etiquetas donde se aplicará esta asignación de roles.

9. Cuando haya terminado, seleccione **Aceptar**. La nueva asignación se muestra en la lista de asignaciones.


## <a name="next-steps"></a>Pasos siguientes
- [Más información sobre el control de acceso basado en rol en Intune](role-based-access-control.md)
- [Creación de un rol personalizado](create-custom-role.md)
