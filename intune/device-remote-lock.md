---
title: Bloqueo remoto de los dispositivos administrados con Intune
titleSuffix: Intune on Azure
description: Aprenda a usar Intune para bloquear los dispositivos administrados de forma remota.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ab885fa6f693e65295986c182353f4918024281f
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2017
---
# <a name="remotely-lock-managed-devices-with-intune"></a>Bloqueo remoto de los dispositivos administrados con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Bloqueo remoto** bloquea el dispositivo seleccionado. El propietario del dispositivo debe usar su contraseña para desbloquearlo. Solo puede bloquear de forma remota un dispositivo que tenga definidos un PIN o una contraseña.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: no compatible
- Windows Phone: compatible con Windows Phone 8.1 y versiones posteriores
- iOS: compatible
- macOS: no compatible
- Android: compatible

## <a name="how-to-remote-lock-a-device"></a>Cómo bloquear de forma remota un dispositivo

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo y luego elija la acción de dispositivo remoto **Bloqueo remoto**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.
