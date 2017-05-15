---
title: "Bloqueo de aplicaciones con autenticación no moderna"
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
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 0f192c0e41cf3b639cbfdac3f8c4fc3b8167266d
ms.contentlocale: es-es
ms.lasthandoff: 04/25/2017


---

# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloqueo de aplicaciones que no usan autenticación moderna (ADAL)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Acceso condicional basado en aplicación con directivas de protección de aplicaciones que se basan en aplicaciones que utilizan [autenticación moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), que es una implementación de OAuth2. Las aplicaciones de escritorio y móviles de Office más recientes usan autenticación moderna; sin embargo, hay aplicaciones de terceros y aplicaciones de Office más antiguas que usan otros métodos de autenticación como autenticación básica y autenticación basada en formularios.

Para bloquear el acceso a estas aplicaciones, se recomienda lo siguiente:

* Configure reglas de notificaciones de ADFS para bloquear protocolos de autenticación no moderna. Las instrucciones detalladas se describen en el escenario 3: [Bloquear todo el acceso a Office 365 excepto las aplicaciones basadas en explorador](https://technet.microsoft.com/library/dn592182.aspx).
* Para **SharePoint Online**, deshabilite la autenticación no moderna en el servicio de SharePoint Online mediante el cmdlet de PowerShell [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) para establecer la propiedad de protocolos de autenticación heredada en false:

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false

```


>[!IMPORTANT]
>La CA basada en aplicación no debe utilizarse con autenticación basada en certificados de Azure Active Directory (Azure AD). Solo puede tener una de ellas configurada en cada momento.

### <a name="see-also"></a>Consulte también
[Permitir solo aplicaciones admitidas por Intune para acceder a servicios de Office 365](allow-policy-managed-apps-access-to-o365.md)

