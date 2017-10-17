---
title: "Creación de una directiva de acceso condicional basado en aplicación para SharePoint Online"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.openlocfilehash: 4183df8e8ed982e7aba2d55d82923564f215ad53
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="set-up-app-based-conditional-access-ca-policies-for-sharepoint-online"></a>Configuración de directivas de acceso condicional basado en aplicación para SharePoint Online

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

En este tema se proporcionan instrucciones sobre cómo configurar la directiva de acceso condicional basado en aplicación para SharePoint Online. El acceso condicional basado en aplicación ayuda a los administradores solo permitan las aplicaciones móviles a las que se aplican las directivas de protección de aplicación de Intune.

## <a name="to-create-the-app-based-ca-policy-for-sharepoint-online"></a>Para crear la directiva de acceso condicional basado en aplicación para SharePoint Online

1. Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales.

    > [!NOTE]
    > Si no está familiarizado con la experiencia de Azure Portal, consulte el tema [Azure Portal para directivas de protección de aplicaciones](azure-portal-for-microsoft-intune-mam-policies.md).

2. Elija **Más servicios** en el menú izquierdo y, luego, escriba **Intune** en el filtro del cuadro de texto.

3. Elija **Protección de aplicaciones de Intune** > **Administración de aplicaciones móviles de Intune** > **Toda la configuración**.

4. En la hoja Administración de aplicaciones móviles de Intune, elija el icono SharePoint Online.

5. En la hoja **Aplicaciones permitidas**, elija la opción que **permite las aplicaciones que admiten las directivas de aplicación de Intune** para admitir solo las aplicaciones que sean compatibles con las directivas de protección de aplicaciones de Intune.

    > [!NOTE] 
    > Cuando se selecciona la opción de solo permitir las aplicaciones que sean compatibles con las directivas de protección de aplicación de Intune, se muestra una lista que **solo** contiene las aplicaciones compatibles.

    ![Captura de pantalla de la hoja de aplicaciones permitidas que muestra la lista de aplicaciones](../media/mam-ca-spo-allowed-apps.png)

## <a name="to-assign-app-based-ca-policies-to-your-users"></a>Para asignar directivas de acceso condicional basado en aplicaciones a los usuarios

1. Abra la hoja **Grupos de usuarios restringidos** y, luego, elija **Agregar grupo de usuarios**.

2. Seleccione uno o más grupos de usuarios a los que se aplicará esta directiva.

    ![Captura de pantalla de la hoja de grupos de usuarios restringidos con la opción de agregar grupo de usuarios resaltada](../media/mam-ca-spo-restricted-groups.png)

    > [!IMPORTANT] 
    > Puede que algunos usuarios del grupo de usuarios seleccionado en el paso anterior no se vean afectados por esta directiva. En estos casos, agregue el grupo de usuarios a la lista de grupos de usuarios exentos. 

3. En la hoja **SharePoint Online**, elija **Grupos de usuarios exentos** y, luego, **Agregar grupo de usuarios** para abrir la lista de grupos de usuarios.

4. Seleccione los grupos que desea excluir de la directiva.  

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>Para modificar o eliminar grupos de usuario de una directiva de acceso condicional existente basada en aplicación

1. Abra la hoja **Grupos de usuarios restringidos** y resalte el grupo de usuarios que desea eliminar.
2. Haga clic en los puntos suspensivos para ver las opciones de eliminación.
3. Elija **Eliminar** para quitar el grupo de usuarios de la lista.

> [!NOTE] 
> Puede seguir los pasos del procedimiento para quitar un grupo de usuarios de la lista de **grupos de usuarios exentos**.

## <a name="next-steps"></a>Pasos siguientes

[Bloqueo de aplicaciones que no usan la autenticación moderna](block-apps-with-no-modern-authentication.md)

## <a name="see-also"></a>Consulte también

[Protección de datos de aplicaciones con directivas de protección de aplicaciones](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Configuración del acceso condicional basado en aplicación para Exchange Online](mam-ca-for-exchange-online.md)
