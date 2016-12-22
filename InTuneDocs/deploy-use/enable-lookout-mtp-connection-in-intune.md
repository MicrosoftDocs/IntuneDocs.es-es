---
title: Habilitar Lookout MTP en Intune | Microsoft Intune
description: "Habilite la protección contra amenazas móviles de Lookout en la consola de administración de Intune."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 1bef6c15387309e1b36bc85758ca699acd54fdd0


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Habilitar la conexión de Lookout MTP en la consola de administración de Intune
En este tema se muestra cómo habilitar la conexión de Lookout MTP en Intune. Para hacer este paso ya tiene que haber configurado el conector de Intune en la consola de Lookout.  Si aún no lo ha hecho, siga los pasos descritos en [Configurar la suscripción con protección contra amenazas móviles de Lookout](set-up-your-subscription-with-lookout-mtp.md).

Para habilitar la conexión de Lookout MTP en Intune, en la página **Administración** de la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Integración de servicios de terceros**. Seleccione **Estado de Lookout** y habilite **Sincronización con MTP** mediante el botón de alternancia.

![captura de pantalla de la página de sincronización de Lookout con el botón de alternar Habilitar resaltado](../media/mtp/lookout-intune-synchronization.png)

Con esto se completa la configuración de la integración de Lookout e Intune en la consola de administración de Intune.  Los siguientes pasos para implementar esta solución implican implementar las [aplicaciones Lookout for Work](configure-and-deploy-lookout-for-work-apps.md) y configurar la directiva de [cumplimiento normativo](enable-device-threat-protection-rule-in-compliance-policy.md).

>[!IMPORTANT]
> Se **debe** configurar la aplicación Lookout for Work antes de crear reglas de directiva de cumplimiento y de configurar el acceso condicional. Esto garantiza que la aplicación esté lista y disponible para que los usuarios finales la instalen antes de poder acceder al correo electrónico u otros recursos de empresa.
## <a name="next-steps"></a>Pasos siguientes
[Configurar la aplicación Lookout for Work ](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Dec16_HO2-->


