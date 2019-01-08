---
title: Bloqueo de aplicaciones sin autenticación moderna en Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre el bloqueo de aplicaciones que no usan la autenticación moderna (ADAL) mediante Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: dc9318d46892eab21e81c7eb2992f3476720abd1
ms.sourcegitcommit: 4e69a8664c289263490daa4c02bc6b81c33196e5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53642462"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloqueo de aplicaciones que no usan la autenticación moderna (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

El acceso condicional basado en aplicación con directivas de protección de aplicaciones se basa en aplicaciones que usan la [autenticación moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) que es una implementación de OAuth2. Las aplicaciones de escritorio y móviles de Office más recientes usan la autenticación moderna. Sin embargo, hay aplicaciones de terceros y aplicaciones de Office más antiguas que usan otros métodos de autenticación, como la autenticación básica y la autenticación basada en formularios.

## <a name="block-apps"></a>Bloqueo de aplicaciones

Para bloquear el acceso a las aplicaciones que no usan la autenticación moderna, se recomiendan los métodos siguientes:

- Configure reglas de notificaciones de ADFS para bloquear protocolos de autenticación no moderna. Las instrucciones detalladas se describen en el escenario 3: [Bloquear todo el acceso a Office 365 excepto las aplicaciones basadas en explorador](https://technet.microsoft.com/library/dn592182.aspx).
- Para **Exchange y SharePoint Online**, use el acceso condicional de Azure Active Directory y el commandlet de PowerShell Set-SPOTenant para SharePoint Online. Para obtener instrucciones detalladas, consulte [Procedimientos para configurar SharePoint Online y Exchange Online para el acceso condicional de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols).


>[!IMPORTANT]
>La entidad de certificación basada en aplicaciones no debe usarse con la autenticación basada en certificados de Azure Active Directory (Azure AD). Solo puede tener uno de lo siguiente configurado a la vez.

## <a name="next-steps"></a>Pasos siguientes

- [Acceso condicional basado en aplicación con Intune](app-based-conditional-access-intune.md)
