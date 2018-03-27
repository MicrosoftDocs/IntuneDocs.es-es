---
title: Acceso de aplicaciones a Exchange Online
description: En este tema se describe cómo puede configurar una directiva de acceso condicional para las aplicaciones con MAM.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 10/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f2cd1a1f-fd29-4081-8dfa-c40993a107d5
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d582421ed842f1e5b87419e25c5d03ad7a138e99
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="create-an-exchange-online-conditional-access-to-only-allow-apps-supported-by-mam"></a>Creación de un acceso condicional de Exchange Online para permitir solo las aplicaciones compatibles con MAM

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

En este tema se indican instrucciones paso a paso sobre cómo configurar el acceso condicional para que Exchange Online solo permita aplicaciones móviles compatibles con las directivas de protección de aplicaciones de Intune.


## <a name="create-an-exchange-online-policy"></a>Creación de una directiva de Exchange Online
1.  Inicie sesión en [Azure Portal](https://portal.azure.com) que incluye la característica de acceso de la aplicación. Si no está familiarizado con la experiencia de Azure Portal, consulte el tema [Azure Portal para directivas de protección de aplicaciones](azure-portal-for-microsoft-intune-mam-policies.md).

2.  Seleccione **Más servicios** y escriba "Intune".

3.  Elija **Protección de aplicaciones de Intune**.

4.  En la hoja **Administración de aplicaciones móviles de Intune**, elija **Toda la configuración**.

5.  En la sección **Acceso condicional**, elija **Exchange Online**.

    ![Captura de pantalla de la hoja de configuración que se muestra la sección de acceso condicional con la opción Exchange Online resaltada](../media/MAM-conditional-access-1.png)

6. En la hoja **Aplicaciones permitidas**, elija la opción que **permite las aplicaciones que admiten las directivas de aplicación de Intune** para que solo las aplicaciones que sean compatibles con las directivas de protección de aplicaciones de Intune puedan acceder a Exchange Online. Cuando se selecciona esta opción, se muestra la lista de aplicaciones admitidas.

    >[!NOTE]
    >Ningún cliente de correo de Exchange Active Sync, incluidos los clientes de correo electrónico integrados en iOS y Android que se conectan a Exchange Online, podrá enviar o recibir correo electrónico. En su lugar, los usuarios recibirán un solo correo electrónico que les informa de que necesitan usar la aplicación de correo de Outlook.

7. Para aplicar esta directiva a los usuarios, abra la hoja **Grupos de usuarios restringidos** y elija **Agregar grupo de usuarios**. Seleccione uno o más grupos de usuarios a los que se aplicará esta directiva.

    ![Captura de pantalla de la hoja de grupos de usuarios restringidos con la opción de agregar grupo de usuarios resaltada](../media/mam-ca-add-user-group.png)

8. Puede que algunos usuarios del grupo de usuarios seleccionado en el paso anterior no se vean afectados por esta directiva. En estos casos, agregue el grupo de usuarios a la lista de grupos de usuarios exentos. En la hoja **Exchange Online**, elija **Grupos de usuarios exentos**. Elija **Agregar grupo de usuarios** para abrir la lista de grupos de usuarios. Seleccione los grupos que desea excluir de la directiva.  

## <a name="modify-an-existing-policy"></a>Modificación de una directiva existente
### <a name="add-or-delete-user-groups"></a>Adición o eliminación de grupos de usuarios

Para **eliminar un grupo de usuarios** de la lista **grupos de usuarios restringidos**, abra la hoja **Grupos de usuarios restringidos**, resalte el grupo de usuarios que desea eliminar y haga clic en el signo de **puntos suspensivos (...)** para ver la opción **Eliminar**. Elija **Eliminar** para quitar el grupo de usuarios de la lista. Puede seguir el mismo procedimiento para quitar un grupo de usuarios de la lista de **grupos de usuarios exentos**.


## <a name="next-steps"></a>Pasos siguientes
[Bloqueo de aplicaciones que no usan la autenticación moderna](block-apps-with-no-modern-authentication.md)
### <a name="see-also"></a>Vea también
[Protección de datos de aplicaciones con directivas de protección de aplicaciones](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
