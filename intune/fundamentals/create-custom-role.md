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
ms.openlocfilehash: bfa2758546595d1e6237d88e128958c50759eb04
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569190"
---
# <a name="create-a-custom-role-in-intune"></a>Creación de un rol personalizado en Intune

Puede crear un rol personalizado en Intune que incluya los permisos necesarios para una función de trabajo específica. Por ejemplo, si un grupo del departamento de TI administra las aplicaciones, las directivas y los perfiles de configuración, puede agregar todos los permisos juntos en un rol personalizado. Después de crear un rol personalizado, puede [asignarlo](assign-role.md) a todos los usuarios que necesiten esos permisos.

Para crear, editar o asignar roles, la cuenta debe tener uno de los siguientes permisos en Azure AD:
- **Administrador global**
- **Administrador del servicio de Intune**

## <a name="to-create-a-custom-role"></a>Para crear un rol personalizado

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Administración de inquilinos** > **Roles** > **Todos los roles** > **Crear**.

2. En la página **Datos básicos**, escriba un nombre y una descripción para el nuevo rol y, después, elija **Siguiente**.

3. En la página **Permisos**, elija los permisos que quiera usar con este rol.

4. En la página **Ámbito (etiquetas)**, seleccione las etiquetas para este rol. Este rol puede acceder a los recursos que también tengan estas etiquetas. Elija **Siguiente**.

5. Cuando haya terminado, elija **Crear** en la página **Revisar y crear**. El nuevo rol se muestra en la lista de la hoja **Roles de Intune: Todos los roles**.

## <a name="copy-a-role"></a>Copia de un rol

También puede copiar un rol existente.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Administración de inquilinos** > **Roles** > **Todos los roles** > active la casilla de un rol de la lista > **Duplicar**.

2. En la página **Datos básicos**, escriba un nombre. Asegúrese de usar un nombre único.

3. Todos los permisos y etiquetas de ámbito del rol original estarán ya seleccionados. Posteriormente, puede cambiar los valores de **Nombre**, **Descripción**, **Permisos** y **Ámbito (etiquetas)** del rol duplicado.

4. Una vez realizados todos los cambios que quiere, elija **Siguiente** para ir a la página **Revisar y crear**. Seleccione **Crear**. 

## <a name="next-steps"></a>Pasos siguientes
- [Asignación de un rol a un usuario](assign-role.md)
- [Más información sobre el control de acceso basado en rol en Intune](role-based-access-control.md)


