---
title: "Configuración del acceso de aplicación de SharePoint Online"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 992273f88e4bbe234f11f936d6416dbaf0d394e9
ms.lasthandoff: 04/19/2017


---

# <a name="create-a-sharepoint-online-conditional-access-policy-to-only-allow-apps-supported-by-mam"></a>Creación de una directiva de acceso condicional de SharePoint Online para permitir solo las aplicaciones compatibles con MAM
En este tema se indican instrucciones paso a paso sobre cómo configurar el acceso condicional para que Exchange Online solo permita aplicaciones móviles que admiten las directivas de administración de aplicaciones móviles (MAM) de Intune.

## <a name="configure-a-sharepoint-online-policy"></a>Configuración de una directiva de SharePoint Online
**Paso 1**: inicie sesión en [Azure Portal](https://portal.azure.com) que incluye la característica de acceso de la aplicación. Si no está familiarizado con la experiencia de Azure Portal, consulte el tema [Azure Portal para directivas de MAM](azure-portal-for-microsoft-intune-mam-policies.md).

**Paso 2**: vaya a **Examinar >Intune > hoja Administración de aplicaciones móviles de Intune > Configuración** y, en la sección de **acceso condicional**, elija **SharePoint Online**.

![Captura de pantalla de la hoja de configuración que muestra la sección de acceso condicional y la hoja SharePoint Online abierta](../media/mam-ca-settings-spo.png)

**Paso 3**: en la hoja **Aplicaciones permitidas**, elija la opción que **permite las aplicaciones que admiten las directivas de aplicación de Intune** para que solo las aplicaciones que sean compatibles con las directivas MAM de Intune tengan la capacidad de acceder a SharePoint Online. Cuando se selecciona la opción de solo permitir las aplicaciones que sean compatibles con las directivas MAM de Intune, se muestra la lista con las aplicaciones compatibles.

![Captura de pantalla de la hoja de aplicaciones permitidas que muestra la lista de aplicaciones](../media/mam-ca-spo-allowed-apps.png)

**Paso 4**: para aplicar esta directiva a los usuarios, abra la hoja **Grupos de usuarios restringidos** y elija **Agregar grupo de usuarios**. Seleccione uno o más grupos de usuarios a los que se aplicará esta directiva.

![Captura de pantalla de la hoja de grupos de usuarios restringidos con la opción de agregar grupo de usuarios resaltada](../media/mam-ca-spo-restricted-groups.png)


**Paso 5**: puede que algunos usuarios del grupo de usuarios seleccionado en el paso anterior no se vean afectados por esta directiva. En estos casos, agregue el grupo de usuarios a la lista de grupos de usuarios exentos. En la hoja **SharePoint Online**, elija **Grupos de usuarios exentos**. Elija **Agregar grupo de usuarios** para abrir la lista de grupos de usuarios. Seleccione los grupos que desea excluir de la directiva.  

## <a name="modifying-an-existing-policy"></a>Modificación de una directiva existente
### <a name="adding-or-deleting-user-groups"></a>Incorporación o eliminación de grupos de usuarios
Para **eliminar un grupo de usuarios** de la lista de **grupos de usuarios restringidos**, abra la hoja Grupos de usuarios restringidos, resalte el grupo de usuarios que desea eliminar y haga clic en los puntos suspensivos (...) para ver la opción de eliminación. Elija **Eliminar** para quitar el grupo de usuarios de la lista. Puede seguir el mismo procedimiento para quitar un grupo de usuarios de la lista de **grupos de usuarios exentos**.


## <a name="next-steps"></a>Pasos siguientes
[Configuración del acceso de aplicaciones a Exchange Online](mam-ca-for-exchange-online.md)

[Bloqueo de aplicaciones que no usan la autenticación moderna](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Consulte también

[Proteger datos de aplicaciones mediante las directivas de MAM](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

