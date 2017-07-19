---
title: "Introducción a los grupos"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 04843a918a3c661ab69dfa711f4d22a8feedf5f3
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
# <a name="get-started-with-groups"></a>Introducción a los grupos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[](./media/generic-users-groups.png)

Microsoft Intune usa Azure Active Directory (Azure AD) para [administrar el acceso a los recursos de la empresa](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups). Este acceso está controlado mediante roles en el directorio. Entonces Intune administra este acceso para los dispositivos móviles, que permite a los miembros de ese grupo tener acceso a los recursos.

__¿Cómo se crea un grupo?__

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Con **Buscar recursos**, busque **Usuarios y grupos**.
3. Una vez que haya abierto la hoja **Usuarios y grupos**, seleccione **Todos los grupos**.
4. En la hoja **Usuarios y grupos: todos los grupos**, seleccione el comando **Nuevo grupo**.
5. En la hoja **Grupo**, agregue un **nombre** y una **descripción** para el grupo.
6. Establezca el **Tipo de pertenencia** como **Asignado**. No **habilite las características de Office** para el grupo de prueba.
7. Haga clic en **Crear**.

Si ha creado correctamente un grupo, debe aparecer en la lista de **Todos los grupos**. Si no aparece ahí, pruebe a crear otro grupo.
