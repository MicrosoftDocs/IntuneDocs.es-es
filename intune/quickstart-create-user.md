---
title: 'Inicio rápido: Crear un usuario en Intune'
description: 'Inicio rápido: Crear un usuario en Intune.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 10/30/2018
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98c71bd4c93e869b429b7677b4fb7c442aa58643
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "57991077"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>Inicio rápido: Crear un usuario y asignarle una licencia

En este inicio rápido, creará un usuario y le asignará una licencia. Al usar Intune, toda persona que necesite tener acceso a los datos de la compañía deberá tener una cuenta de usuario. Los administradores de Intune pueden configurar estos usuarios más adelante para administrar el control de acceso.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como [administrador global o administrador de servicios de Intune](users-add.md#types-of-administrators). Si ha creado una suscripción de prueba de Intune, la cuenta con la que creó la suscripción es el administrador global.

## <a name="create-a-user"></a>Crear un usuario

Los usuarios deben tener una cuenta de usuario para poder inscribirse en la administración de dispositivos de Intune.

1. En Intune, elija **Usuarios** > **Todos los usuarios** > **Nuevo usuario**.
![Explorador](media/quickstart-create-user/create-user.png)
2. En el cuadro **Nombre**, escriba un nombre, como *Isabel Robledo*.
3. En el cuadro **Nombre de usuario**, escriba un identificador de usuario, como Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Si no ha configurado el nombre de dominio del cliente, use el nombre de dominio comprobado que usó para crear la suscripción de Intune (o [evaluación gratuita](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Elija **Mostrar contraseña** y tome nota de la contraseña generada automáticamente para que pueda iniciar sesión en un dispositivo de prueba.
5. Elija **Crear**.

## <a name="assign-a-license-to-the-user"></a>Asignar una licencia a un usuario

Después de crear un usuario, debe usar el [Centro de administración de Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para asignar una licencia de Intune a ese usuario. Si no le asigna una licencia, no podrá inscribir su dispositivo en Intune. 

1. Inicie sesión en el [Centro de administración de Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) con las mismas credenciales que ha usado para iniciar sesión en Intune.
2. Elija **Usuarios** > **Usuarios activos** > elija el usuario que acaba de crear.
3. Junto a **Licencias de productos**, seleccione **Editar**.
4. En **Ubicación**, elija una ubicación para el usuario.
5. Haga clic en **Activar** junto a la licencia de Intune (o en otra licencia que tenga que incluya Intune). El [nombre de producto](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** que se muestra se usa como plan de servicio en la administración de Azure 

   > [!NOTE]
   > Este valor usa una de las licencias de este usuario. Si usa un entorno de evaluación, es posible que más tarde quiera reasignar esta licencia a un usuario real en un entorno activo.
6. Elija **Guardar** > **Cerrar**.

El nuevo usuario activo de Intune ahora mostrará que está usando una licencia de **Intune**.

## <a name="clean-up-resources"></a>Limpieza de recursos

Si ya no necesita este usuario, puede eliminarlo desde el [Centro de administración de Microsoft 365](http://go.microsoft.com/fwlink/p/?LinkId=698854). Allí, elija **Usuarios** > **Usuarios activos** > *elija el usuario en la lista* > **Eliminar usuario** > **Eliminar usuario** > **Confirmar cambios** > **Cerrar**.

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, ha creado un usuario y le ha asignado una licencia. Para obtener más información sobre cómo agregar usuarios a Intune, consulte [Adición de usuarios y concesión de permiso administrativo a Intune](users-add.md).

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Crear un grupo para administrar usuarios](quickstart-create-group.md)
