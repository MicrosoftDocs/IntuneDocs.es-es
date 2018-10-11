---
title: 'Inicio rápido: Crear un usuario en Intune'
description: 'Inicio rápido: Crear un usuario en Intune.'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 6a1d591e635dccd99551d9b8d40e099724a85d77
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581809"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>Inicio rápido: Crear un usuario y asignarle una licencia

En este inicio rápido, creará un usuario y le asignará una licencia. Al usar Intune, toda persona que necesite tener acceso a los datos de la compañía deberá tener una cuenta de usuario. Los administradores de Intune pueden configurar estos usuarios para administrar el control de acceso.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como administrador global o administrador de servicios de Intune.

## <a name="create-a-user"></a>Crear un usuario

Los usuarios deben tener una cuenta de usuario para poder inscribirse en la administración de dispositivos de Intune.

1. En Intune, elija **Usuarios** > **Todos los usuarios** > **Nuevo usuario**.
![Explorador](media/quickstart-create-user/create-user.png)
2. En el cuadro **Nombre**, escriba *Isabel Robledo*.
3. En el cuadro **Nombre de usuario**, escriba *Dewey@contoso.onmicrosoft.com*.
4. Elija **Grupos** > **Todos** > **Seleccionar**.
5. Elija **Mostrar contraseña** y tome nota de la contraseña generada automáticamente para que pueda iniciar sesión en un dispositivo de prueba.
6. Elija **Crear**.

## <a name="assign-a-license-to-the-user"></a>Asignar una licencia a un usuario

Después de crear un usuario, debe usar el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para asignar una licencia de Intune a ese usuario. Si no le asigna una licencia, no podrá inscribir su dispositivo en Intune. 

1. Inicie sesión en el [Portal de Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) con las mismas credenciales que ha usado para iniciar sesión en Intune.
2. Elija **Usuarios** > **Usuarios activos** > elija el usuario que acaba de crear.
3. En **Ubicación**, elija una ubicación para el usuario.
3. Elija **Licencias de producto** y establezca **Enterprise Mobility + Security E3** (u otra licencia que tenga que incluya Intune) en **Activado**.
   > [!NOTE]
   > Esto usa una de las licencias de este usuario. Si está usando un entorno dinámico, puede desactivarlo usando esta licencia más tarde para volver a asignarla a un usuario real.
5. Elija **Guardar**.

## <a name="clean-up-resources"></a>Limpieza de recursos

Si ya no necesita este usuario, puede eliminarlo desde **Usuarios** > **Todos los usuarios** > elija el usuario en la lista > **Eliminar usuario** > **Sí**.

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, ha creado un usuario y le ha asignado una licencia. Ya puede asignar ese usuario a un grupo.

> [!div class="nextstepaction"]
> [Crear un grupo](quickstart-create-group.md)
