---
title: Habilitar Lookout MTP en Intune | Microsoft Docs
description: "Habilite la protección contra amenazas móviles de Lookout en la consola de administración de Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2a99839ece16c56c7bfaacb295796525903f9464
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="enable-lookout-mtd-connection-in-the-intune-classic-console"></a>Habilitación de la conexión de Lookout MTD en la consola clásica de Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para habilitar la conexión de Mobile Threat Defense (MTD) de Lookout en Intune, ya debe haber configurado el conector de Intune en la consola de Lookout.  Si aún no lo ha hecho, debe [configurar la suscripción a Mobile Threat Defense de Lookout](setup-your-lookout-mtd-subscription.md).

Para habilitar la conexión de Lookout MTP en Intune, en la página **Administración** de la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Integración de servicios de terceros**. Seleccione **Estado de Lookout** y habilite **Sincronización con MTP** mediante el botón de alternancia.

![captura de pantalla de la página de sincronización de Lookout con el botón de alternar Habilitar resaltado](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> Se **debe** configurar la aplicación Lookout for Work antes de crear reglas de directiva de cumplimiento y de configurar el acceso condicional. Esto garantiza que la aplicación esté lista y disponible para que los usuarios finales la instalen antes de poder acceder al correo electrónico u otros recursos de empresa.

Con esto se completa la configuración de la integración de Lookout e Intune en la consola de administración de Intune.  Los siguientes pasos para implementar esta solución implican implementar la directiva [Aplicaciones de Lookout for Work](/intune-classic/deploy-use/device-threat-protection-policy).


## <a name="next-steps"></a>Pasos siguientes
[Configurar la aplicación Lookout for Work ](/intune-classic/deploy-use/device-threat-protection-apps)

