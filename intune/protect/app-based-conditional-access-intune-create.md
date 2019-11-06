---
title: Configuración de una directiva de acceso condicional basado en aplicación con Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo crear una directiva de acceso condicional basado en la aplicación con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94e9fcc77f8260c4a63150b5d0aef033677c524a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509679"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configuración de directivas de acceso condicional basado en la aplicación con Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Configure directivas de acceso condicional basado en la aplicación para aplicaciones que forman parte de la lista de aplicaciones aprobadas. La lista de aplicaciones aprobadas consta de aplicaciones que Microsoft ha probado.

> [!IMPORTANT]
> En este artículo se describen los pasos necesarios para agregar una directiva de acceso condicional basado en la aplicación. Puede usar los mismos pasos al agregar aplicaciones como SharePoint Online, Microsoft Teams y Microsoft Exchange Online desde la lista de aplicaciones aprobadas.

## <a name="create-app-based-conditional-access-policies"></a>Creación de directivas de acceso condicional basado en la aplicación
Acceso condicional es una tecnología de Azure Active Directory (Azure AD). El nodo de acceso condicional al que se accede desde *Intune* es el mismo nodo al que se accede desde *Azure AD*. Esto significa que no es necesario cambiar entre Intune y Azure AD para configurar las directivas.

> [!IMPORTANT]
> Para crear directivas de acceso condicional desde el portal de Intune, debe disponer de una licencia de Azure AD Premium.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Para crear una directiva de acceso condicional basado en la aplicación

> [!IMPORTANT]
> Tiene que haber aplicado [directivas de protección de aplicaciones de Intune](../apps/app-protection-policies.md) a sus aplicaciones antes de usar las directivas de acceso condicional basado en la aplicación.

1. En el **panel de Intune**, seleccione **Acceso condicional**.

2. En el panel **Directivas**, elija **Nueva directiva** para crear la directiva de acceso condicional basado en la aplicación.

4. Tras escribir un nombre de directiva y configurar las opciones disponibles en la sección **Asignaciones**, elija **Conceder** en **Controles de acceso**.

5. Elija **Requerir aplicación cliente aprobada**, **Seleccionar** y **Crear** para guardar la directiva nueva.

## <a name="next-steps"></a>Pasos siguientes
[Bloqueo de aplicaciones que no usan la autenticación moderna](app-modern-authentication-block.md)

## <a name="see-also"></a>Consulte también

[Proteger datos de aplicaciones mediante directivas de protección de aplicaciones](../apps/app-protection-policies.md)
[Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)