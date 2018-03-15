---
title: "Configurar una directiva de acceso condicional basado en aplicación con Intune"
description: "Obtenga información sobre cómo crear una directiva de acceso condicional basado en aplicación con Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5ab442f49e0eabc4162bd2f56865ed42d96ae5db
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurar directivas de acceso condicional basado en aplicación con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En este artículo, se describe cómo configurar directivas de acceso condicional basado en aplicación para aplicaciones que forman parte de la lista de aplicaciones aprobadas. La lista de aplicaciones aprobadas consta de aplicaciones que Microsoft ha probado.

> [!IMPORTANT]
> Este artículo le guía a través de los pasos para agregar una directiva de acceso condicional basado en aplicación con Exchange Online, pero puede usar los mismos pasos al agregar otras aplicaciones como SharePoint Online, Microsoft Teams, etc. desde la lista de aplicaciones aprobadas.

## <a name="to-create-an-app-based-conditional-access-policy"></a>Para crear una directiva de acceso condicional basado en aplicación
1.  Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con sus credenciales.

2.  Elija **All services** (Todos los servicios) y escriba "Intune".

3.  Elija **Protección de aplicaciones de Intune**.

4.  En **Protección de aplicaciones de Intune** en la sección **Acceso condicional**, elija **Exchange Online**.

    ![Captura de pantalla del panel de configuración que muestra la sección de acceso condicional con la opción Exchange Online resaltada](./media/MAM-conditional-access-1.png)

6. En el panel **Aplicaciones permitidas**, elija la opción **Permitir aplicaciones que admiten las directivas de aplicación de Intune** para que solo las aplicaciones que sean compatibles con las directivas de protección de aplicaciones de Intune puedan acceder a Exchange Online. Cuando se selecciona esta opción, se muestra la lista de aplicaciones admitidas.

    > [!NOTE]
    > Ningún cliente de correo de Exchange Active Sync, incluidos los clientes de correo electrónico integrados en iOS y Android que se conectan a Exchange Online, puede enviar o recibir correo electrónico. En su lugar, los usuarios recibirán un solo correo electrónico que les informa que necesitan usar la aplicación de correo de Outlook.

7. Para aplicar esta directiva a los usuarios, abra el panel **Grupos de usuarios restringidos** y elija **Agregar grupo de usuarios**. Seleccione uno o más grupos de usuarios a los que se aplicará esta directiva.

    ![Captura de pantalla del panel Grupos de usuarios restringidos con la opción Agregar grupo de usuarios resaltada](./media/mam-ca-add-user-group.png)

8. Puede que algunos usuarios del grupo de usuarios seleccionado en el paso anterior no se vean afectados por esta directiva. En estos casos, agregue el grupo de usuarios a la lista de grupos de usuarios exentos. En el panel **Exchange Online**, elija **Grupos de usuarios exentos**. Elija **Agregar grupo de usuarios** para abrir la lista de grupos de usuarios. Seleccione los grupos que desea excluir de la directiva.

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>Para modificar o eliminar grupos de usuario de una directiva de acceso condicional existente basada en aplicación

1. Abra el panel **Grupos de usuarios restringidos** y resalte el grupo de usuarios que quiera eliminar.
2. Haga clic en los puntos suspensivos para ver las opciones de eliminación.
3. Elija **Eliminar** para quitar el grupo de usuarios de la lista.

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Crear directivas de acceso condicional basado en la aplicación en la carga de trabajo de Azure AD

A partir de la versión 1708 de Intune, los administradores de TI pueden crear directivas de acceso condicional basado en la aplicación a partir de la carga de trabajo de Azure AD. Esto resulta más cómodo, ya que no es necesario cambiar entre Azure y las cargas de trabajo de Intune.

> [!IMPORTANT]
> Para crear directivas de acceso condicional de Azure AD desde el portal de Azure de Intune, debe disponer de una licencia de Azure AD Premium.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Para crear una directiva de acceso condicional basado en aplicación

> [!IMPORTANT]
> Debe aplicar [directivas de protección de aplicaciones de Intune](app-protection-policies.md) a sus aplicaciones antes de usar las directivas de acceso condicional basado en la aplicación.

1. En el **panel de Intune**, elija **Acceso condicional**.

2. En el panel **Directivas**, elija **Nueva directiva** para crear la directiva de acceso condicional basado en aplicación.

4. Tras escribir un nombre de directiva y configurar las opciones disponibles en la sección **Asignaciones**, elija **Conceder** en **Controles de acceso**.

5. Elija **Requerir aplicación cliente aprobada**, **Seleccionar** y **Crear** para guardar la directiva nueva.

## <a name="next-steps"></a>Pasos siguientes
[Bloqueo de aplicaciones que no usan la autenticación moderna](app-modern-authentication-block.md)

### <a name="see-also"></a>Vea también

[Proteger datos de aplicaciones mediante directivas de protección de aplicaciones](app-protection-policies.md)
[Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
