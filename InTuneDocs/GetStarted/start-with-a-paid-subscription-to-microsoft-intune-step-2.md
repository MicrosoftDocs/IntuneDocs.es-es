---
title: Configurar un nombre de dominio personalizado | Microsoft Intune
description: "Se describe el proceso de agregar un nombre de dominio personalizado para su suscripción de Intune."
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6d1c7c670341692d4ea0c823e4a9a96746b83067
ms.openlocfilehash: 60f96b21f9e8f6ce610c24c6078906f51e327cb7


---


# Configuración de un nombre de dominio personalizado

De forma predeterminada, Intune usa el nombre de dominio **<domain>.onmicrosoft.com** que se creó al suscribirse por primera vez en el servicio. Si su organización posee un dominio personalizado, puede configurar la instancia de Intune para que use ese dominio en lugar del nombre de dominio proporcionado con la suscripción.

Le recomendamos encarecidamente que, antes de crear nuevas cuentas de usuario o sincronizar cuentas de su instancia de Active Directory, decida si va a usar únicamente el dominio .onmicrosoft.com o va a agregar uno o más nombres de dominios personalizados. Configurar un dominio personalizado antes de agregar usuarios puede ayudar a simplificar la administración de las identidades de usuario para la suscripción, ya que permite a los usuarios iniciar sesión con las credenciales que usan para acceder a otros recursos del dominio.

Al suscribirse a un servicio basado en la nube de Microsoft, la instancia de ese servicio se convierte en un [inquilino de Microsoft Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), que proporciona servicios de identidad y directorio al servicio basado en la nube. Además, como las tareas de configuración de Intune para que use el nombre de dominio personalizado de las organizaciones son las mismas que para otros inquilinos de Azure AD, puede usar la información y los procedimientos que se describen en [Agregar el dominio](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Para más información sobre el uso de un dominio personalizado con un servicio basado en la nube de Microsoft, consulte [Información general conceptual de nombres de dominio personalizado en Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

### Pasos siguientes
Enhorabuena. Acaba de completar el paso 2 de la *Guía de inicio rápido de Intune*.

>[!div class="step-by-step"]

>[&larr; **Iniciar sesión en Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Agregar usuarios a Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  



<!--HONumber=Aug16_HO4-->


