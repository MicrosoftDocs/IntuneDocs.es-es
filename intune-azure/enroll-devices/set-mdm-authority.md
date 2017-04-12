---
title: "Establecer la entidad de administración de dispositivos móviles"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: aprenda a configurar la entidad de administración de dispositivos móviles en Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 9d7a1a934188f0a40553d3c6b8b567ba8f6af034
ms.lasthandoff: 02/18/2017

---

# <a name="set-the-mobile-device-management-authority"></a>Establecer la entidad de administración de dispositivos móviles 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

La configuración de la entidad de administración de dispositivos móviles determina cómo se administran los dispositivos. Las configuraciones posibles son:

- **Intune independiente**: administración solo en la nube, que se configura mediante el portal de Azure. Incluye el conjunto completo de funcionalidades que ofrece Intune.

- **Intune híbrido**: integración de la solución de nube de Intune con System Center Configuration Manager. Intune se configura mediante la consola de Configuration Manager.

- **Administración de dispositivos móviles para Office 365**: integración de Office 365 con la solución de nube de Intune. Intune se configura desde el Centro de administración de Office 365. Incluye un subconjunto de las funcionalidades que están disponibles con la versión independiente de Intune.

>[!IMPORTANT]
>Una vez establecida la entidad de administración de dispositivos móviles, tendrá que ponerse en contacto con el [soporte técnico de Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) para cambiarla, así que tenga cuidado cuando haga su elección.

**Para establecer la entidad de administración de dispositivos móviles**

1. En Azure Portal, elija **Más servicios** > **Supervisión y administración** > **Intune**.

2. En la hoja de Intune, elija **Inscribir dispositivos** y luego elija **Overview** (Información general).

3. En la hoja **Empezar a administrar dispositivos**, elija **Establecer Intune como entidad de MDM**. Un mensaje indica que ha configurado correctamente su entidad de MDM en Intune.

