---
title: Acceso condicional con Microsoft Intune
titlesuffix: ''
description: Obtenga más información sobre cómo definir las condiciones que deben cumplir los usuarios, los dispositivos y las aplicaciones para acceder a los recursos de la empresa en Microsoft Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/06/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a62166792570c5bb81391d05d1cbc3f8486543a4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022346"
---
# <a name="whats-conditional-access"></a>¿Qué es el acceso condicional?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

El acceso condicional hace referencia a las formas en que puede controlar los dispositivos y las aplicaciones que pueden conectarse a los recursos del correo electrónico y la empresa. En este tema, obtendrá información sobre el acceso condicional basado en dispositivos y aplicaciones, y encontrará escenarios comunes para usar el acceso condicional con Intune.

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
