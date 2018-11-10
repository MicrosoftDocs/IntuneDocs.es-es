---
title: 'Inicio rápido: Crear un grupo para administrar usuarios'
titlesuffix: Microsoft Intune
description: En este inicio rápido, usará Microsoft Intune para crear un grupo basado en usuarios existentes.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2b52265bb9b3df800c0e13450a2154e46098a933
ms.sourcegitcommit: 9d08545727543b434dd270371fa50233470f2bce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50410827"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Inicio rápido: Crear un grupo para administrar usuarios

En este inicio rápido, usará Intune para crear un grupo basado en un usuario existente. Los grupos se usan para administrar los usuarios y controlar el acceso de los empleados a los recursos de la empresa. Estos recursos pueden formar parte de la intranet de la empresa o ser recursos externos, como sitios de SharePoint, aplicaciones de SaaS o aplicaciones web.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

>[!NOTE]
>Intune ofrece los grupos creados previamente **Todos los usuarios** y **Todos los dispositivos** en la consola con las optimizaciones integradas para su comodidad.

## <a name="prerequisites"></a>Requisitos previos

- Para completar este inicio rápido, debe [crear un usuario](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como [administrador global o administrador de servicios de Intune](users-add.md#types-of-administrators). Si ha creado una suscripción de prueba de Intune, la cuenta con la que creó la suscripción es el administrador global.

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

En este inicio rápido, usó Intune para crear un grupo basado en un usuario existente.

> [!div class="nextstepaction"]
> [Crear una directiva de cumplimiento de dispositivos](quickstart-create-policy.md)
