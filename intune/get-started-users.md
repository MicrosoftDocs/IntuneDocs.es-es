---
title: Introducción a la administración de usuarios
titlesuffix: Microsoft Intune
description: Agregue un usuario a Intune y asígnele una licencia para que pueda acceder a recursos de la empresa en dispositivos móviles.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 646a72eaa3837b48b4af718904064fddaeb98955
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55840389"
---
# <a name="get-started-managing-users"></a>Introducción a la administración de usuarios

Tenga en cuenta a todas las personas de su organización. Cada una de ellas que use los datos de la empresa necesitará disponer de un usuario para administrar el acceso a ellos en Intune.

## <a name="how-do-i-create-a-user"></a>¿Cómo se crea un usuario?

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Después de abrir el panel **Microsoft Intune**, seleccione **Usuarios**. En la página **Todos los usuarios**, seleccione **+ Usuario nuevo**.
4. Escriba la información del usuario, como el **nombre** y el **nombre de usuario**. La parte del nombre de dominio del nombre de usuario debe ser uno de los siguientes dominios:
    - el nombre de dominio predeterminado inicial "contoso.onmicrosoft.com", o
    - un nombre de dominio verificado no federado como "contoso.com".
5. En **Grupos**, elija [un grupo](get-started-groups.md) al que agregar el usuario.
6. Guarde la contraseña de usuario que se ha generado automáticamente de manera que pueda usarla para iniciar sesión en un dispositivo de prueba. Debe proporcionar esta contraseña a los usuarios para que puedan cambiarla a una contraseña normal que puedan recordar.
7. En el panel **Usuario**, seleccione **Crear**.

## <a name="assigning-licenses-to-users"></a>Asignar licencias a usuarios

Después de que haya creado un usuario, necesita usar el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para asignar una licencia de Intune a ese usuario. Sin asignarles una licencia, no pueden inscribir su dispositivo en la administración.

1. Inicie sesión en el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) con las mismas credenciales que ha usado para iniciar sesión en Intune.
2. Seleccione **Usuarios** > **Usuarios activos**, después seleccione el usuario que ha creado anteriormente.
3. Puede que necesite esperar un momento a que se cargue toda la información del usuario. Una vez que se cargue, seleccione **Editar** para las **Licencias de productos** del usuario.
4. Asigne al usuario una **Ubicación** y, después, cambie Intune a **Activado**.

   > [!NOTE]
   > Esto usa una de las licencias de este usuario. Si está usando un entorno dinámico, puede desactivarlo usando esta licencia más tarde para volver a asignarla a un usuario real.

5. Seleccione **Guardar**.

## <a name="next-steps"></a>Pasos siguientes

[Introducción a los grupos](get-started-groups.md): organice a los usuarios en grupos para administrar las directivas y las aplicaciones a las que pueden acceder con más facilidad.
