---
title: Bloqueo de aplicaciones sin autenticación moderna
description: ''
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 10/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a8e9ec3d5a8aaea266dff8be8c1c71ad19e74d2b
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloqueo de aplicaciones que no usan autenticación moderna (ADAL)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

El acceso condicional basado en aplicación con directivas de protección de aplicaciones se basa en aplicaciones que usan la [autenticación moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) que es una implementación de OAuth2. Las aplicaciones de escritorio y móviles de Office más recientes usan la autenticación moderna; sin embargo, hay aplicaciones de terceros y aplicaciones Office más antiguas que usan otros métodos de autenticación como la autenticación básica y la autenticación basada en formularios.

Para bloquear el acceso a estas aplicaciones, se recomienda lo siguiente:

* Configure reglas de notificaciones de ADFS para bloquear protocolos de autenticación no moderna. Las instrucciones detalladas se describen en el escenario 3: [Bloquear todo el acceso a Office 365 excepto las aplicaciones basadas en explorador](https://technet.microsoft.com/library/dn592182.aspx).
* Para **SharePoint Online**, deshabilite la autenticación no moderna en el servicio SharePoint Online con el commandlet [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) para establecer la propiedad de protocolos de autenticación heredados en false:

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false

```


>[!IMPORTANT]
>La CA basada en aplicación no debe utilizarse con autenticación basada en certificados de Azure Active Directory (Azure AD). Solo puede tener una de ellas configurada en cada momento.

### <a name="see-also"></a>Consulte también
[Permitir solo las aplicaciones compatibles con Intune para obtener acceso a servicios de O365](allow-policy-managed-apps-access-to-o365.md)
