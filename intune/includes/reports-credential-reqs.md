---
ms.openlocfilehash: 76706fb39c3c5a69cba4fbf3f57c0b58d92e4a27
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2019
ms.locfileid: "67560021"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisitos de credenciales de Azure AD e Intune

La autenticación y la autorización se basan en las credenciales de Azure AD y en el control de acceso basado en roles (RBAC) de Intune. Todos los administradores globales y los administradores de servicios de Intune del inquilino tienen acceso al Almacén de datos de forma predeterminada. Use roles de Intune para proporcionar acceso a más usuarios. Para ello, concédales acceso al recurso **Almacenamiento de datos de Intune**.

Los requisitos para acceder al Almacén de datos de Intune (incluida la API) son:

  - El usuario debe ser uno de los siguientes:
      - Un administrador global de Azure AD.
      - Un administrador del servicio de Intune.
      - Usuario con acceso basado en roles al recurso **Almacenamiento de datos de Intune**.
      - Autenticación sin usuario mediante [autenticación de solo aplicación](../data-warehouse-app-only-auth.md). 
