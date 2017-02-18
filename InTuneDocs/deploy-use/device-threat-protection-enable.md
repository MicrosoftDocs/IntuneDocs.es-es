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
translationtype: Human Translation
ms.sourcegitcommit: 53862e49c922b75b414fd5aceec3bba2b10299a6
ms.openlocfilehash: 1297522d0f7b52ebe14eb7b938f3458e7308ae27


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Habilitar la conexión de Lookout MTP en la consola de administración de Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Para habilitar la conexión de la protección contra amenazas malintencionadas (MTP) de Lookout en Intune, ya debe haber configurado el conector de Intune en la consola de Lookout.  Si aún no lo ha hecho, debe [Configurar la suscripción con protección contra amenazas móviles de Lookout](set-up-your-subscription-with-lookout-mtp.md).

Para habilitar la conexión de Lookout MTP en Intune, en la página **Administración** de la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Integración de servicios de terceros**. Seleccione **Estado de Lookout** y habilite **Sincronización con MTP** mediante el botón de alternancia.

![captura de pantalla de la página de sincronización de Lookout con el botón de alternar Habilitar resaltado](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> Se **debe** configurar la aplicación Lookout for Work antes de crear reglas de directiva de cumplimiento y de configurar el acceso condicional. Esto garantiza que la aplicación esté lista y disponible para que los usuarios finales la instalen antes de poder acceder al correo electrónico u otros recursos de empresa.

Con esto se completa la configuración de la integración de Lookout e Intune en la consola de administración de Intune.  Los siguientes pasos para implementar esta solución implican implementar las [aplicaciones Lookout for Work](configure-and-deploy-lookout-for-work-apps.md) y configurar la directiva de [cumplimiento normativo](enable-device-threat-protection-rule-in-compliance-policy.md).


## <a name="next-steps"></a>Pasos siguientes
[Configurar la aplicación Lookout for Work ](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Jan17_HO2-->


