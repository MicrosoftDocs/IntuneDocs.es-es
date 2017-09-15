---
title: "Habilitación de Mobile Threat Defense de Skycure en Intune"
description: "Habilite Mobile Threat Defense de Skycure en el portal clásico de Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9fe3c59e52d9d7732267ecfb28eac3b5c7368ed9
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Habilitación de Mobile Threat Defense de Skycure en Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para habilitar la conexión de Mobile Threat Defense (MTD) de Skycure en Intune, ya debe haber configurado el [conector de Intune en la consola de Skycure] (/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune).

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>Para habilitar la conexión de MTD de Skycure en Intune

1.  Vaya al [portal clásico de Intune](https://manage.microsoft.com/) y, a continuación, escriba sus credenciales.

2.  Elija **Admin** &gt; **Integración de servicios de terceros** y, a continuación, elija **Skycure Status** (Estado de Skycure) y habilite **Synchronization with MTD** (Sincronización con MTD) mediante el botón de alternancia.

    ![Habilitación de la alternancia de Skycure en el portal clásico de Intune](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> Se debe configurar la aplicación de Skycure antes de crear reglas de directiva de cumplimiento y de configurar el acceso condicional. Esto garantiza que la aplicación esté lista y disponible para que los usuarios finales la instalen antes de poder acceder al correo electrónico u otros recursos de empresa.

Con esto se completa la configuración de la integración de Skycure e Intune en la consola de administración de Intune. Los siguientes pasos para implementar esta solución implican implementar las aplicaciones de Skycure for Work y configurar la directiva de cumplimiento.

## <a name="next-steps"></a>Pasos siguientes

[Creación de directiva de cumplimiento de Mobile Threat Defense de Skycure en Intune](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
