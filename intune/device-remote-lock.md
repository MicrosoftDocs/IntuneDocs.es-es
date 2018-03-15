---
title: Bloqueo remoto de los dispositivos administrados con Intune
titlesuffix: Azure portal
description: Aprenda a usar Intune para bloquear los dispositivos administrados de forma remota.
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 01/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a8f3c93507cde4363570a9a39f8b3b1f69c07df
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="remotely-lock-managed-devices-with-intune"></a>Bloqueo remoto de los dispositivos administrados con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Bloqueo remoto** bloquea el dispositivo seleccionado. El propietario del dispositivo debe usar su contraseña para desbloquearlo. Solo puede bloquear de forma remota un dispositivo que tenga definidos un PIN o una contraseña.

## <a name="supported-platforms"></a>Plataformas compatibles

Bloqueo remoto es compatible con las siguientes plataformas:

|Plataforma|Estado de compatibilidad|
|---|---|
|Android|Sí|
|iOS|Sí|
|macOS|Sí|
|Windows 10 Escritorio|No|
|Windows 10 Mobile|Sí|
|Windows Phone|Sí, para Windows Phone 8.1 y versiones posteriores|

> [!NOTE]  
> Para los dispositivos MacOS, establezca un PIN de recuperación de 6 dígitos. Una vez bloqueado, la hoja de **información general del dispositivo** muestra el PIN hasta que se envía otra acción de dispositivo.

## <a name="how-to-remote-lock-a-device"></a>Cómo bloquear de forma remota un dispositivo

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services (Todos los servicios)** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos**, pulse **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo y luego elija la acción de dispositivo remoto **Bloqueo remoto**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos**, elija **Acciones de dispositivo**.
