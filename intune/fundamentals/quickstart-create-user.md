---
title: 'Inicio rápido: Crear un usuario en Intune'
description: 'Inicio rápido: Crear un usuario en Intune.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6aa57b71e052e3fc8566fcdff8bdd9ef5d1c39e
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754497"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-the-user-a-license"></a>Inicio rápido: Creación de un usuario en Intune y asignación de una licencia

En este inicio rápido, creará un usuario y le asignará una licencia de Intune. Al usar Intune, toda persona que necesite tener acceso a los datos de la empresa deberá tener su propia cuenta de usuario. Los administradores de Intune pueden configurar a los usuarios más adelante para administrar el control de acceso.

## <a name="prerequisites"></a>Requisitos previos

- Suscripción a Microsoft Intune. [Suscríbase para disfrutar de una cuenta de prueba gratuita](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune-in-microsoft-endpoint-manager"></a>Inicio de sesión en Intune en el Administrador de puntos de conexión de Microsoft

Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) como [administrador global o administrador de servicios de Intune](users-add.md#types-of-administrators). Si ha creado una suscripción de prueba de Intune, la cuenta con la que la haya creado es el administrador global.

## <a name="create-a-user"></a>Creación de un usuario

Un usuario debe tener una cuenta de usuario para poder inscribirse en la administración de dispositivos de Intune. Para crear un usuario:

1. En el Administrador de puntos de conexión de Microsoft, seleccione **Usuarios** > **Todos los usuarios** > **Nuevo usuario**:  ![En el Administrador de puntos de conexión de Microsoft, seleccione Nuevo usuario](./media/quickstart-create-user/create-user.png)
2. En el cuadro **Nombre**, escriba un nombre, como *Isabel Robledo*:  ![Agregar detalles del usuario](./media/quickstart-create-user/create-user-02.png)
3. En el cuadro **Nombre de usuario**, escriba un identificador de usuario, como Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Si no ha configurado el nombre de dominio del cliente, use el nombre de dominio comprobado que usó para crear la suscripción de Intune (o [evaluación gratuita](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)). 

4. Seleccione **Mostrar contraseña** y asegúrese de recordar la contraseña generada automáticamente para que pueda iniciar sesión en un dispositivo de prueba.
5. Seleccione **Crear**.

## <a name="assign-a-license-to-the-user"></a>Asignar una licencia a un usuario

Después de crear un usuario, debe usar el [Centro de administración de Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) para asignarle una licencia de Intune. Si no se le asigna una licencia al usuario, no podrá inscribir su dispositivo en Intune.

Para asignar una licencia de Intune a un usuario:

1. Inicie sesión en el [Centro de administración de Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854) con las mismas credenciales que ha usado para iniciar sesión en Intune.
2. Seleccione **Usuarios** > **Usuarios activos** y, luego, seleccione el usuario que acaba de crear.
3. Seleccione la pestaña **Licencias y aplicaciones**.
4. En **Seleccionar ubicación**, seleccione una ubicación para el usuario, si todavía no se establece.
2. Active la casilla **Intune** en la sección **Licencias**. Si otra licencia incluye Intune, puede seleccionar esa licencia. El [nombre de producto](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference) que se muestra se usa como plan de servicio en la administración de Azure.

    ![Selección de la ubicación y la licencia de Intune](./media/quickstart-create-user/create-user-03.png)

   > [!NOTE]
   > Este valor usa una de las licencias del usuario. Si usa un entorno de evaluación, más tarde reasignará esta licencia a un usuario real en un entorno activo.

6. Seleccione **Guardar cambios**.

Ahora el nuevo usuario activo de Intune mostrará que está usando una licencia de **Intune**.

## <a name="clean-up-resources"></a>Limpieza de recursos

Si ya no necesita ese usuario, puede eliminarlo en el [Centro de administración de Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854). Ahí, seleccione **Usuarios** > *el usuario* > *el icono de eliminación del usuario* > **Eliminar usuario** > **Cerrar**.

   ![Seleccione el icono de eliminación](./media/quickstart-create-user/create-user-04.png)

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, creó un usuario y le asignó una licencia de Intune. Para obtener más información sobre cómo agregar usuarios a Intune, consulte [Adición de usuarios y concesión de permiso administrativo a Intune](users-add.md).

Para seguir esta serie de inicios rápidos de Intune, vaya al siguiente:

> [!div class="nextstepaction"]
> [Inicio rápido: Crear un grupo para administrar usuarios](../quickstart-create-group.md)
