---
title: Bloqueo de aplicaciones sin autenticación moderna en Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre la autenticación moderna (ADAL) y de aplicaciones con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/03/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ca96f36f8813d80c7ebb07bfb3bd65f8aa0b392
ms.sourcegitcommit: 71314481e644025c005019b478b4cbeaf2390ea9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59569108"
---
# <a name="block-apps-that-dont-use-modern-authentication-adal"></a>Bloqueo de aplicaciones que no usan la autenticación moderna (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

El acceso condicional basado en aplicación con directivas de protección de aplicaciones se basa en aplicaciones que usan la [autenticación moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) que es una implementación de OAuth2. Las aplicaciones de escritorio y móviles de Office más recientes usan la autenticación moderna. Sin embargo, hay aplicaciones de terceros y aplicaciones de Office más antiguas que usan otros métodos de autenticación, como la autenticación básica y la autenticación basada en formularios.

## <a name="block-access-to-apps"></a>Bloqueo del acceso a las aplicaciones

Para bloquear el acceso a las aplicaciones que no usan la autenticación moderna, use las directivas de protección de aplicación de Intune para implementar acceso condicional. Para más información, [Acceso condicional basado en aplicación con Intune](app-based-conditional-access-intune.md).

## <a name="additional-information"></a>Información adicional

Para más información sobre el acceso condicional de Azure AD, consulte estos temas:
- [¿Qué es el acceso condicional en Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Funcionamiento del acceso condicional basado en aplicación](app-based-conditional-access-intune.md#how-app-based-conditional-access-works)
- [Procedimientos para configurar SharePoint Online y Exchange Online para el acceso condicional de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/conditional-access-for-exo-and-spo)

## <a name="next-steps"></a>Pasos siguientes

- [Acceso condicional basado en aplicación con Intune](app-based-conditional-access-intune.md)
