---
title: "Eliminación de datos de la compañía de los dispositivos con Intune"
titleSuffix: Intune on Azure
description: "Aprenda a quitar únicamente los datos de la compañía de los dispositivos que administra con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 39acd12333e9685f94d23416fb1a61ce93f45476
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>Eliminación de datos de la compañía de los dispositivos administrados con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción **Eliminar datos de la compañía** quita únicamente los datos de la compañía de los dispositivos administrados por Intune. No se quitan datos personales del dispositivo. Intune ya no administra el dispositivo y este dejará de poder acceder a recursos corporativos (no aplicable a dispositivos Windows unidos a Azure Active Directory).

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo y luego elija la acción de dispositivo remoto **Eliminar datos de la compañía**.

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.
