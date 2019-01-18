---
title: 'Inicio rápido: Crear un grupo para administrar usuarios'
titlesuffix: Microsoft Intune
description: En este inicio rápido, usará Microsoft Intune para crear un grupo basado en usuarios existentes.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/11/2019
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 6f7d7ccb4c94300d00f02dcace5c3a089cd9f2a2
ms.sourcegitcommit: d54a12a836503f7e8b90346f16b7ad2d83b710dc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2019
ms.locfileid: "54270578"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Inicio rápido: Crear un grupo para administrar usuarios

En este inicio rápido, usará Intune para crear un grupo basado en un usuario existente. Los grupos se usan para administrar los usuarios y controlar el acceso de los empleados a los recursos de la empresa. Estos recursos pueden formar parte de la intranet de la empresa o ser recursos externos, como sitios de SharePoint, aplicaciones de SaaS o aplicaciones web.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

>[!NOTE]
>Intune ofrece los grupos creados previamente **Todos los usuarios** y **Todos los dispositivos** en la consola con las optimizaciones integradas para su comodidad.

## <a name="prerequisites"></a>Requisitos previos

- Para completar este inicio rápido, debe [crear un usuario](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en el [portal de Intune](https://aka.ms/intuneportal) como [administrador global o como administrador de servicios de Intune](users-add.md#types-of-administrators). Si ha creado una suscripción de prueba de Intune, la cuenta con la que creó la suscripción es el administrador global.

## <a name="create-a-group"></a>Crear un grupo

Creará un grupo que se usará más adelante en esta serie de inicio rápido.

1. Después de abrir el panel **Microsoft Intune**, seleccione **Grupos** > **Nuevo grupo**.
2. En el cuadro desplegable **Tipo de grupo**, seleccione **Seguridad**.
3. Establezca el **Nombre** en "Contoso Testers" (Evaluadores de Contoso) y agregue una **Descripción** al grupo.
4. Establezca **Tipo de miembro** en **Asignado**. 
5. Haga clic en **Miembros** y seleccione uno o varios miembros para el grupo a partir de la lista existente.

    ![Captura de pantalla de creación de un grupo en Microsoft Intune](./media/quickstart-use-groups-01.png)

6. Haga clic en **Seleccionar** > **Crear**.

Cuando haya creado correctamente el grupo, aparecerá en la lista **Todos los grupos**. 

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, usó Intune para crear un grupo basado en un usuario existente. Para obtener más información sobre cómo agregar grupos a Intune, consulte [Agregar grupos para organizar usuarios y dispositivos](groups-add.md).

Para seguir esta serie de tutoriales de inicio rápido de Intune, pase al siguiente tutorial de inicio rápido.

> [!div class="nextstepaction"]
> [Inicio rápido: Configurar la inscripción automática para dispositivos Windows 10](quickstart-setup-auto-enrollment.md)
