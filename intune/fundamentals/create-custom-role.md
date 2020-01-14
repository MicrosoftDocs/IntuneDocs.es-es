---
title: Creación de un rol personalizado en Intune
description: Obtenga información sobre cómo crear un rol personalizado en Microsoft Intune.
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
ms.openlocfilehash: 68c2dc7df123593513c14e16e2626c7426f50b01
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207424"
---
# <a name="create-a-custom-role-in-intune"></a>Creación de un rol personalizado en Intune

Puede crear un rol personalizado en Intune que incluya los permisos necesarios para una función de trabajo específica. Por ejemplo, si un grupo del departamento de TI administra las aplicaciones, las directivas y los perfiles de configuración, puede agregar todos los permisos juntos en un rol personalizado. Después de crear un rol personalizado, puede [asignarlo](assign-role.md) a todos los usuarios que necesiten esos permisos.

Para crear, editar o asignar roles, la cuenta debe tener uno de los siguientes permisos en Azure AD:
- **Administrador global**
- **Administrador del servicio de Intune**

## <a name="to-create-a-custom-role"></a>Para crear un rol personalizado

1. En el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Roles** > **Todos los roles** > **Agregar**.

2. En la hoja **Agregar rol personalizado**, escriba un nombre y una descripción para el nuevo rol y luego haga clic en **Permisos**.

3. En la hoja **Permisos**, elija los permisos que quiere usar con este rol.

4. En la hoja **Ámbito (etiquetas)** , seleccione las etiquetas para este rol. Este rol puede acceder a los recursos que también tengan estas etiquetas.

5. Cuando haya terminado, seleccione **Aceptar**.

6. En la hoja **Agregar rol de personalizado**, haga clic en **Crear**. El nuevo rol se muestra en la lista de la hoja **Roles de Intune: Todos los roles**.


## <a name="copy-a-role"></a>Copia de un rol

También puede copiar un rol existente.

1. En el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Roles** > **Todos los roles** > seleccione un rol en la lista > **Duplicar**.

2. En **Rol duplicado**, escriba un nombre. Asegúrese de usar un nombre único.

3. Todos los permisos y etiquetas de ámbito del rol original estarán ya seleccionados. Posteriormente, puede cambiar los valores de **Nombre**, **Descripción**, **Permisos** y **Ámbito (etiquetas)** del rol duplicado.

4. Seleccione **Crear**. 

## <a name="next-steps"></a>Pasos siguientes
- [Asignación de un rol a un usuario](assign-role.md)
- [Más información sobre el control de acceso basado en rol en Intune](role-based-access-control.md)
