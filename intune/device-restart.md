---
title: Reinicio remoto de los dispositivos con Intune
titlesuffix: Azure portal
description: "Aprenda a reiniciar los dispositivos de forma remota mediante la acción de reinicio del dispositivo."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9afe804d2f9e48e27ced4bd92959cd065f6ec89a
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="remotely-restart-devices-with-intune"></a>Reinicio remoto de los dispositivos con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Reiniciar** permite que se reinicie el dispositivo elegido. Como al propietario del dispositivo no se le informa automáticamente del reinicio, podría perder trabajo.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: compatible con Windows 8.1 y versiones posteriores
- Windows Phone: compatible con Windows Phone 8.1 y versiones posteriores
- iOS: compatible

    > [!Note]  
    > Para usar este comando es necesario que el dispositivo esté supervisado y disponer del derecho de acceso **Bloqueo del dispositivo**. El dispositivo se reinicia inmediatamente. Después de un reinicio, los dispositivos iOS bloqueados mediante código de acceso no volverán a unirse a una red Wi-Fi y es posible que no puedan comunicarse con el servidor.
- macOS: no compatible
- Android: no compatible

## <a name="how-to-restart-a-device"></a>Cómo reiniciar un dispositivo

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo y luego elija la acción de dispositivo remoto **Reiniciar**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.
