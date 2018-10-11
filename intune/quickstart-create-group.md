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
ms.openlocfilehash: 3a4468f2e6919349095d934790740afc8c347282
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581797"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Inicio rápido: Crear un grupo para administrar usuarios

En este inicio rápido, usará Intune para crear un grupo basado en un usuario existente. Los grupos se usan para administrar los usuarios y controlar el acceso de los empleados a los recursos de la empresa. Estos recursos pueden formar parte de la intranet de la empresa o ser recursos externos, como sitios de SharePoint, aplicaciones de SaaS o aplicaciones web.

Si no tiene una suscripción a Intune, [regístrese para obtener una cuenta de prueba gratuita](free-trial-sign-up.md).

>[!NOTE]
>Intune ofrece los grupos creados previamente **Todos los usuarios** y **Todos los dispositivos** en la consola con las optimizaciones integradas para su comodidad.

## <a name="prerequisites"></a>Requisitos previos

- Para completar este inicio rápido, debe [crear un usuario](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Iniciar sesión en Intune

Inicie sesión en [Intune](https://aka.ms/intuneportal) como administrador global o administrador de servicios de Intune. Intune se encuentra en Azure Portal, si selecciona **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.

## <a name="create-a-group"></a>Crear un grupo
1. Después de abrir el panel **Microsoft Intune**, seleccione **Grupos** > **Nuevo grupo**.
2. En el panel **Grupo**, seleccione **Tipo de grupo** > **Seguridad**.
3. Establezca el **Nombre** en "Contoso Testers" (Evaluadores de Contoso) y agregue una **Descripción** al grupo.
4. Establezca el **Tipo de pertenencia** como **Asignado**. 
5. Haga clic en **Miembros** y seleccione **Miembros** para el grupo en la lista existente.

    ![Captura de pantalla de creación de un grupo en Microsoft Intune](./media/quickstart-use-groups-01.png)

6. Haga clic en **Seleccionar**.
7. Haga clic en **Crear**.

Si ha creado correctamente el grupo, aparecerá en la lista **Todos los grupos**. 

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, usó Intune para crear un grupo basado en un usuario existente.

> [!div class="nextstepaction"]
> [Crear una directiva de cumplimiento de dispositivos](quickstart-create-policy.md)
