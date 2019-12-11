---
title: Bloqueo de aplicaciones sin autenticación moderna en Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre la autenticación moderna (ADAL) y de aplicaciones con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81c7746985bd3449ce4e5f2d90780bcd117069eb
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509662"
---
# <a name="block-apps-that-dont-use-modern-authentication-adal"></a>Bloqueo de aplicaciones que no usan la autenticación moderna (ADAL)

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

El acceso condicional basado en la aplicación con directivas de protección de aplicaciones depende de aplicaciones que usan la [autenticación moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) que es una implementación de OAuth2. Las aplicaciones de escritorio y móviles de Office más recientes usan la autenticación moderna. Si bien, hay aplicaciones de terceros y aplicaciones de Office más antiguas que usan otros métodos de autenticación, como la autenticación básica y la autenticación basada en formularios.

## <a name="block-access-to-apps"></a>Bloqueo del acceso a las aplicaciones

Para bloquear el acceso a las aplicaciones que no usan la autenticación moderna, use las directivas de protección de aplicación de Intune para implementar acceso condicional. Para más información, consulte [Acceso condicional basado en aplicación con Intune](app-based-conditional-access-intune.md).

## <a name="additional-information"></a>Información adicional

Para más información sobre el acceso condicional de Azure AD, consulte estos temas:
- [¿Qué es el acceso condicional en Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Funcionamiento del acceso condicional basado en aplicación](app-based-conditional-access-intune.md#how-app-based-conditional-access-works)
- [Procedimientos para configurar SharePoint Online y Exchange Online para el acceso condicional de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/conditional-access-for-exo-and-spo)

## <a name="next-steps"></a>Pasos siguientes

- [Acceso condicional basado en aplicación con Intune](app-based-conditional-access-intune.md)
