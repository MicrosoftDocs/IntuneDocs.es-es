---
title: "Bloqueo de aplicaciones sin autenticación moderna | Microsoft Intune"
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
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 5c95cd8510faa437a33ac25d6602a2bcc57c05d5


---

# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloqueo de aplicaciones que no usan la autenticación moderna (ADAL)
El acceso condicional para aplicaciones con directivas MAM (MAM CA) se basa en aplicaciones que utilizan la [autenticación moderna](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) que es una implementación de OAuth2. Las aplicaciones de escritorio y móviles de Office más recientes usan la autenticación moderna; sin embargo, hay aplicaciones de terceros y aplicaciones Office más antiguas que usan otros métodos de autenticación como la autenticación básica y la autenticación basada en formularios.

Para bloquear el acceso a estas aplicaciones, se recomienda lo siguiente:

* Configure reglas de notificaciones de ADFS para bloquear protocolos de autenticación no moderna. Se proporcionan instrucciones detalladas en el Escenario 3: [Bloquear todo el acceso externo a O365 excepto las aplicaciones basadas en explorador](https://technet.microsoft.com/library/dn592182.aspx).

>[!IMPORTANT]
>El acceso condicional de MAM no debe utilizarse con autenticación basada en certificados de Azure Active Directory (Azure AD). Solo puede tener uno de lo siguiente configurado a la vez.



### <a name="see-also"></a>Consulte también
[Permitir solo las aplicaciones compatibles con Intune para obtener acceso a servicios de O365](allow-policy-managed-apps-access-to-o365.md)



<!--HONumber=Dec16_HO2-->


