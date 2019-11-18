---
title: Configuración de una directiva de acceso condicional basada en la aplicación con Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo crear una directiva de acceso condicional basado en la aplicación con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 465f8b0001e5e2a049a3ffe12469bdb5057854ec
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712832"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configuración de directivas de acceso condicional basado en la aplicación con Intune

Configure directivas de acceso condicional basado en la aplicación para aplicaciones que forman parte de la lista de aplicaciones aprobadas. La lista de aplicaciones aprobadas consta de aplicaciones que Microsoft ha probado.

Antes de usar directivas de acceso condicional basadas en la aplicación, debe haber aplicado [directivas de protección de aplicaciones de Intune](../apps/app-protection-policies.md) a las aplicaciones.

> [!IMPORTANT]
> En este artículo se describen los pasos necesarios para agregar una directiva de acceso condicional basado en la aplicación. Puede usar los mismos pasos al agregar aplicaciones como SharePoint Online, Microsoft Teams y Microsoft Exchange Online desde la lista de aplicaciones aprobadas.

## <a name="create-app-based-conditional-access-policies"></a>Creación de directivas de acceso condicional basado en la aplicación

Acceso condicional es una tecnología de Azure Active Directory (Azure AD). El nodo de acceso condicional al que se accede desde *Intune* es el mismo nodo al que se accede desde *Azure AD*. Por lo tanto, no es necesario cambiar entre Intune y Azure AD para configurar las directivas.

Para poder crear directivas de acceso condicional desde el Centro de administración del Administrador de puntos de conexión de Microsoft, debe tener una licencia de Azure AD Premium.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Para crear una directiva de acceso condicional basado en la aplicación

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Endpoint security** (Seguridad del punto de conexión)  > **Acceso condicional** > **Nueva directiva**.

3. En **Nombre**, escriba un nombre de directiva y, en *Asignaciones*, seleccione **Usuarios y grupos**. Utilice las opciones Incluir o Excluir para agregar los grupos para la directiva y seleccione **Listo**.

4. Seleccione **Aplicaciones en la nube o acciones** y elija las aplicaciones que quiere proteger. Por ejemplo, elija **Seleccionar aplicaciones** y seleccione **Office 365 SharePoint Online** y **Office 365 Exchange Online**.

   Haga clic en **Listo** para guardar los cambios.

5. Seleccione **Condiciones** > **Aplicaciones cliente** para aplicar la directiva a las aplicaciones y los exploradores. Por ejemplo, seleccione **Sí** y habilite **Explorador** y **Aplicaciones móviles y aplicaciones de escritorio**.

   Haga clic en **Listo** para guardar los cambios.

6. En *Controles de acceso*, seleccione **Conceder** para aplicar el acceso condicional según el cumplimiento del dispositivo. Por ejemplo, seleccione **Conceder acceso** > **requieren que el dispositivo se marquen como compatibles**.

   Elija **Seleccionar** para guardar los cambios.

7. En **Habilitar directiva**, seleccione **Activar** y, luego, seleccione **Crear** para guardar los cambios.





## <a name="next-steps"></a>Pasos siguientes
[Bloqueo de aplicaciones que no usan la autenticación moderna](app-modern-authentication-block.md)

## <a name="see-also"></a>Consulte también

[Proteger datos de aplicaciones mediante directivas de protección de aplicaciones](../apps/app-protection-policies.md)
[Acceso condicional en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
