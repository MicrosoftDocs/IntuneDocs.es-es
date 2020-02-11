---
title: Reiniciar dispositivos con Microsoft Intune - Azure | Microsoft Docs
description: Reinicie dispositivos Windows e iOS con Microsoft Intune en Azure Portal con la acción de reinicio remoto.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 82ebf35d0eb435f2df4e6cf55274808e6fa690f4
ms.sourcegitcommit: af384c46ec8d8def6aa32c3b89947748dc6fd28f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2020
ms.locfileid: "76517548"
---
# <a name="remotely-restart-devices-with-intune"></a>Reinicio remoto de los dispositivos con Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

La acción de dispositivo **Reiniciar** permite que se reinicie el dispositivo elegido (dentro de 5 minutos). Como al propietario del dispositivo no se le notifica automáticamente del reinicio, podría perder trabajo.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: compatible con Windows 8.1 y versiones posteriores
- Windows Phone: compatible con Windows Phone 8.1 y versiones posteriores
- Dispositivos de quiosco de Android: compatibles con Android 7.0 y versiones posteriores
- iOS: compatible

    > [!Note]  
    > Para usar este comando es necesario que el dispositivo esté supervisado y disponer del derecho de acceso **Bloqueo del dispositivo**. El dispositivo se reinicia inmediatamente. Los dispositivos iOS bloqueados con un código de acceso no se vuelven a unir a una red Wi-Fi después del reinicio. Después del reinicio, el dispositivo podría no comunicarse con el servidor.
- macOS: no compatible
- Dispositivos Android y del perfil de trabajo Android: no compatibles

## <a name="restart-a-device"></a>Reiniciar un dispositivo

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Seleccione **Dispositivos** > **Todos los dispositivos**.
4. En la lista de dispositivos que administra, seleccione un dispositivo > **Reiniciar** > **Sí**.

## <a name="next-steps"></a>Pasos siguientes

- Para ver el estado de la acción de dispositivo **Reiniciar**, seleccione **Dispositivos** > **Acciones de dispositivo**.
