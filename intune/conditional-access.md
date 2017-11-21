---
title: Acceso condicional con Intune
titlesuffix: Azure portal
description: Aprenda a definir las condiciones que deben cumplir los usuarios y los dispositivos para acceder a los recursos de la empresa en Microsoft Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1cd12a105142d5e537da487e3bd9297ef83ddcb3
ms.sourcegitcommit: 82088d297eef629e3da6011681ead442ae7e25f7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2017
---
# <a name="whats-conditional-access"></a>¿Qué es el acceso condicional?

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En este tema se describe el acceso condicional tal y como se aplica a Enterprise Mobility + Security (EMS). A continuación, se analizan los escenarios comunes de acceso condicional cuando se usa Intune.

El acceso condicional de Enterprise Mobility + Security (EMS) no es un producto independiente; es una solución que forma parte de todos los servicios y productos que constituyen EMS. Ofrece un control de acceso granular para mantener seguros los datos corporativos y proporciona a los usuarios una experiencia que les permite trabajar desde cualquier dispositivo en cualquier parte.

Puede definir las condiciones que regulan el acceso a los datos corporativos en función de la ubicación, el dispositivo, el estado del usuario y la confidencialidad de la aplicación.

> [!NOTE] 
> El acceso condicional también extiende sus funcionalidades a los [servicios de Office 365](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/).

![Diagrama de la arquitectura del acceso condicional](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>Acceso condicional con Intune

Intune incorpora directivas de cumplimiento de dispositivos móviles y administración de aplicaciones para admitir la solución de acceso condicional de EMS.

![Intune y el acceso condicional cuando se usa EMS](./media/intune-with-ca-1.png)

Formas de usar el acceso condicional con Intune:

-   **Acceso condicional basado en dispositivos**

    -   Acceso condicional para Exchange local

    -   Acceso condicional basado en el control de acceso a redes

    -   Acceso condicional basado en el riesgo del dispositivo

    -   Acceso condicional para equipos Windows

        -   Propiedad corporativa

        -   Bring your own device (BYOD)

-   **Acceso condicional basado en la aplicación**

## <a name="next-steps"></a>Pasos siguientes

[Formas habituales de usar el acceso condicional con Intune](conditional-access-intune-common-ways-use.md)
