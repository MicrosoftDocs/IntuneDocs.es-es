---
title: "Bloqueo de aplicaciones sin autenticación moderna en Intune"
description: 
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6a7cf3b73f4be195b4e07c8c72edeae9fbc9073
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2017
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloqueo de aplicaciones que no usan la autenticación moderna (ADAL)

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

El acceso condicional basado en aplicación con directivas de protección de aplicaciones se basa en aplicaciones que usan la [autenticación moderna](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) que es una implementación de OAuth2. Las aplicaciones de escritorio y móviles de Office más recientes usan la autenticación moderna; sin embargo, hay aplicaciones de terceros y aplicaciones Office más antiguas que usan otros métodos de autenticación como la autenticación básica y la autenticación basada en formularios.

Para bloquear el acceso a estas aplicaciones, se recomienda lo siguiente:

* Configure reglas de notificaciones de ADFS para bloquear protocolos de autenticación no moderna. Las instrucciones detalladas se describen en el escenario 3: [Bloquear todo el acceso a Office 365 excepto las aplicaciones basadas en explorador](https://technet.microsoft.com/library/dn592182.aspx).
* Para **SharePoint Online**, deshabilite la autenticación no moderna en el servicio SharePoint Online con el commandlet [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) para establecer la propiedad de protocolos de autenticación heredados en false:

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false

```


>[!IMPORTANT]
>La entidad de certificación basada en aplicaciones no debe usarse con la autenticación basada en certificados de Azure Active Directory (Azure AD). Solo puede tener uno de lo siguiente configurado a la vez.

### <a name="see-also"></a>Consulte también
[Acceso condicional basado en aplicación con Intune](app-based-conditional-access-intune.md)
