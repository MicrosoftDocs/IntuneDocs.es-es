---
title: "Introducción a los grupos"
titleSuffix: Azure portal
description: "Organice a los usuarios en grupos para administrar las directivas y las aplicaciones a las que pueden acceder con más facilidad."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 964732be680273c62f341086ce23f0e40d981479
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2017
---
# <a name="get-started-with-groups"></a>Introducción a los grupos

Los grupos se usan para administrar a los usuarios y controlar el acceso de los empleados a los recursos de la empresa. Estos recursos pueden formar parte de su directorio. También pueden ser recursos externos, como las aplicaciones de SaaS o los sitios de SharePoint.

Microsoft Intune usa Azure Active Directory (Azure AD) para administrar el acceso a los recursos de la empresa. Este acceso está controlado mediante roles en el directorio. Entonces Intune administra este acceso para los dispositivos móviles, que permite a los miembros de ese grupo tener acceso a los recursos.

## <a name="how-do-i-create-a-group"></a>¿Cómo se crea un grupo?

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Con **Buscar recursos**, busque **Intune**.
3. Después de abrir la hoja **Microsoft Intune**, seleccione **Grupos**.
4. En la hoja **Usuarios y grupos: todos los grupos**, seleccione el comando **Nuevo grupo**.
5. En la hoja **Grupo**, agregue un **nombre** y una **descripción** para el grupo.
6. Establezca el **Tipo de pertenencia** como **Asignado**. No **habilite las características de Office** para el grupo de prueba.
7. Haga clic en **Crear**.

Si ha creado correctamente un grupo, debe aparecer en la lista de **Todos los grupos**. Si no aparece ahí, pruebe a crear otro grupo.

## <a name="next-steps"></a>Pasos siguientes

[Introducción a las directivas](get-started-policies.md): cree directivas para evitar que los usuarios usen sus dispositivos de forma no autorizada.

## <a name="learn-more"></a>Obtener más información

* [Establecer restricciones de inscripción mediante grupos en Intune](groups-add.md)
* [Administrar el acceso a los recursos de la empresa mediante grupos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
