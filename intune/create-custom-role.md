---
title: Creación de un rol personalizado en Intune
description: Obtenga información sobre cómo crear un rol personalizado en Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7e1e67f617c0a345b17aa731fd193e611eba71e
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508248"
---
# <a name="create-a-custom-role-in-intune"></a>Creación de un rol personalizado en Intune

Puede crear un rol personalizado en Intune que incluya los permisos necesarios para una función de trabajo específica. Por ejemplo, si un grupo del departamento de TI administra las aplicaciones, las directivas y los perfiles de configuración, puede agregar todos los permisos juntos en un rol personalizado. Después de crear un rol personalizado, puede [asignarlo](assign-role.md) a todos los usuarios que necesiten esos permisos.

Para crear, editar o asignar roles, la cuenta debe tener uno de los siguientes permisos en Azure AD:
- **Administrador global**
- **Administrador del servicio de Intune**

## <a name="to-create-a-custom-role"></a>Para crear un rol personalizado

1. Inicie sesión en [Azure Portal](https://portal.azure.com) con las credenciales de Intune.

2. Elija **Todos los servicios** en el menú de la izquierda y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Seleccione **Intune** > **Roles** > **Todos los roles** > **Agregar**.

4. En la hoja **Agregar rol personalizado**, escriba un nombre y una descripción para el nuevo rol y luego haga clic en **Permisos**.

5. En la hoja **Permisos**, elija los permisos que quiere usar con este rol. Use la [tabla de RBAC en Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) para ayudarle a decidir qué permisos desea aplicar.

6. En la hoja **Ámbito (etiquetas)**, seleccione las etiquetas para este rol. Este rol puede acceder a los recursos que también tengan estas etiquetas.

7. Cuando haya terminado, seleccione **Aceptar**.

8. En la hoja **Agregar rol de personalizado**, haga clic en **Crear**. El nuevo rol se muestra en la lista de la hoja **Roles de Intune: Todos los roles**.

## <a name="next-steps"></a>Pasos siguientes
- [Asignación de un rol a un usuario](assign-role.md)
- [Más información sobre el control de acceso basado en rol en Intune](role-based-access-control.md)
