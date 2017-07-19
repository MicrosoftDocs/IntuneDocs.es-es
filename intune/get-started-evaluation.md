---
title: "Introducción a Intune"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bfab644-c1e2-4154-a254-e95b9a1d75f2
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ef58e46118a0a44609abba5de4986b5a1526a151
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2017
---
# <a name="what-is-microsoft-intune"></a>¿Qué es Microsoft Intune?

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

![Microsoft Intune en Azure Portal](./media/generic-intune-azure.png)

Microsoft Intune es uno de los servicios más nuevos de Azure. Ofrece herramientas para administrar los dispositivos móviles, equipos y aplicaciones de la organización que se [actualizan regularmente](whats-new.md). Además de la moderna consola de Azure, Intune también le permite usar la consola clásica. La consola clásica es la primera versión de Intune y el lugar donde todavía se dirige para [administrar los equipos Windows con el cliente de software de Intune](/intune-classic/deploy-use/pc-management-comparison.md). El portal clásico, que está integrado en Silverlight, se usa para un número reducido de tareas. Todo lo demás, incluida la administración de aplicaciones y dispositivos móviles, se realiza en Azure Portal. La guía de introducción le guía a través de las tareas básicas que necesita realizar para usar correctamente Intune en Azure Portal.

![La hoja de ayuda y soporte técnico, disponible en la parte inferior de la lista de acciones en la barra lateral izquierda de Intune.](./media/intune-azure-help-support-closeup.png)

## <a name="what-does-intune-in-the-azure-portal-provide"></a>¿Qué proporciona Intune en Azure Portal?

Intune en Azure Portal le proporciona:

* Consola integrada para todos los [componentes de Enterprise Mobility + Security (EMS)](https://docs.microsoft.com/enterprise-mobility-security)
* Una consola basada en HTML creada en estándares web que admite los [exploradores web modernos](supported-devices-browsers.md)
* [Grupos de Azure Active Directory](groups-get-started.md) para proporcionar compatibilidad entre todas las aplicaciones de Azure
* Automatización a través de la [API de Microsoft Graph](intune-graph-apis.md)

## <a name="prerequisites"></a>Requisitos previos

Antes de comenzar, debe tener una cuenta de inquilino y administrador de Intune activada. Puede registrarse para obtener estas cuentas [aquí](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20). Los suscriptores actuales también pueden completar estas actividades en su inquilino dinámico. Asegúrese de que solo está trabajando en dispositivos de prueba.

También necesita asegurarse de que es el administrador global de su organización para completar todas las tareas de la guía.
