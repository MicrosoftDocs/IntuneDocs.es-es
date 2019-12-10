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
ms.openlocfilehash: 3ca83287c58f8d2fb7c8eec5f8cc793e2c67b77a
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390702"
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

5. En la hoja **Permisos**, elija los permisos que quiere usar con este rol.

6. En la hoja **Ámbito (etiquetas)** , seleccione las etiquetas para este rol. Este rol puede acceder a los recursos que también tengan estas etiquetas.

7. Cuando haya terminado, seleccione **Aceptar**.

8. En la hoja **Agregar rol de personalizado**, haga clic en **Crear**. El nuevo rol se muestra en la lista de la hoja **Roles de Intune: Todos los roles**.


## <a name="copy-a-role"></a>Copia de un rol

También puede copiar un rol existente.

1. Inicie sesión en [Azure Portal](https://portal.azure.com) con las credenciales de Intune y seleccione **Intune**.

2. Seleccione **Roles** > **Todos los roles**, seleccione un rol de la lista y haga clic en **Duplicar**.

3. En **Rol duplicado**, escriba un nombre. Asegúrese de usar un nombre único.

4. Todos los permisos y etiquetas de ámbito del rol original estarán ya seleccionados. Posteriormente, puede cambiar los valores de **Nombre**, **Descripción**, **Permisos** y **Ámbito (etiquetas)** del rol duplicado.

5. Seleccione **Crear**. 

## <a name="next-steps"></a>Pasos siguientes
- [Asignación de un rol a un usuario](assign-role.md)
- [Más información sobre el control de acceso basado en rol en Intune](role-based-access-control.md)
