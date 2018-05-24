---
title: Configurar una directiva de acceso condicional basado en aplicación con Intune
description: Obtenga información sobre cómo crear una directiva de acceso condicional basado en aplicación con Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 05/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c505e881fe06d6f4da217533d0507731ac22a29f
ms.sourcegitcommit: 698bd1488be3a269bb88c077eb8d99df6e552a9a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurar directivas de acceso condicional basado en aplicación con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se describe cómo configurar directivas de acceso condicional basado en aplicación para aplicaciones que forman parte de la lista de aplicaciones aprobadas. La lista de aplicaciones aprobadas consta de aplicaciones que Microsoft ha probado.

> [!IMPORTANT]
> En este artículo se indican los pasos necesarios para agregar una directiva de acceso condicional basado en aplicación. Tenga en cuenta que puede usar los mismos pasos al agregar aplicaciones como SharePoint Online, Microsoft Teams y Microsoft Exchange Online desde la lista de aplicaciones aprobadas.

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Crear directivas de acceso condicional basado en la aplicación en la carga de trabajo de Azure AD

Los administradores de TI pueden crear directivas de acceso condicional basado en aplicación a partir de la carga de trabajo de Azure AD. Esto resulta más cómodo, ya que no es necesario cambiar entre Azure y las cargas de trabajo de Intune.

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
