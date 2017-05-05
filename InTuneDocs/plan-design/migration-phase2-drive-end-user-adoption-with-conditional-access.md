---
title: "Impulsar la adopción de usuarios finales con acceso condicional | Microsoft Docs"
description: "El propósito de este artículo es ofrecer información sobre cómo aprovechar el acceso condicional para impulsar la inscripción de Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 12584743534a76d0b2ce92e5de6cb5f916453938
ms.lasthandoff: 04/25/2017


---

# <a name="phase-2-drive-end-user-adoption-with-conditional-access"></a>Fase 2: Impulsar la adopción de usuarios finales con acceso condicional

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

La habilitación de características de acceso condicional con Intune, como el bloqueo de correo electrónico para dispositivos no inscritos, puede contribuir a impulsar la inscripción y el cumplimiento pero no son necesarios para una correcta migración. Los requisitos de seguridad y los objetivos de adopción de la migración deben determinar el éxito.

## <a name="migration-campaign-with-conditional-access"></a>Campaña de migración con acceso condicional

Aquí tiene un método típico para mejorar una campaña de migración con acceso condicional:

1.  Establezca reglas de acceso condicional que se apliquen a todos los usuarios, pero excluya específicamente los usuarios que tengan que migrar desde el proveedor de MDM antiguo. Puede crear un grupo de usuarios de Azure AD con todos los usuarios excluidos del acceso condicional.

2.  A medida que se migren, quite los usuarios del grupo de exclusión de acceso condicional.

3.  Una vez finalizada la migración, configure todas las directivas de acceso condicional para que se bloqueen de forma predeterminada a menos que Intune permita el acceso.

### <a name="advantages"></a>Ventajas

-   Ofrece control de acceso para nuevas cuentas de usuario o cuentas de usuario que no se administraban mediante la solución anterior.

-   Ofrece un período de gracia para los usuarios de la solución anterior a la migración.

-   Minimiza la pérdida de productividad.

### <a name="disadvantages"></a>Desventajas

-   Los usuarios de la solución anterior posiblemente puedan acceder a recursos mediante dispositivos no administrados hasta que se habilite el acceso condicional para esos usuarios.

> [!TIP]
> Se trata de un método entre otros. Es posible elegir un proceso más sencillo que aplace todo el acceso condicional hasta después de que se dé orden de inscripción a cada fase o un proceso más estricto que exija el acceso condicional desde el mismo principio y requiera compatibilidad completa para todos los accesos.

-   Más información sobre el [acceso condicional](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access).

## <a name="task-list-for-conditional-access"></a>Lista de tareas para acceso condicional

### <a name="task-1-get-ready-for-intune-conditional-access"></a>Tarea 1: Prepararse para el acceso condicional de Intune

-   Aprenda a [configurar el acceso condicional](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

### <a name="task-2-set-up-intune-conditional-access"></a>Tarea 2: Configurar el acceso condicional de Intune

Elija uno de los tipos de directiva de acceso condicional siguientes para obtener más información:

-   [Proteger el acceso de correo electrónico a Exchange Online y nuevo Exchange Online dedicado](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)

-   [Proteger el acceso de correo electrónico a Exchange local y Exchange Online dedicado heredado con Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)

-   [SharePoint Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

-   [Skype Empresarial Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)

-   [Dynamics CRM Online](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

-   [Proteger el acceso al correo electrónico con Microsoft Intune: escenarios de ejemplo](https://docs.microsoft.com/intune/deploy-use/restrict-email-access-example-scenarios)

## <a name="next-steps"></a>Pasos siguientes

[Fase 2: Ciclo de migración típica](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle)

