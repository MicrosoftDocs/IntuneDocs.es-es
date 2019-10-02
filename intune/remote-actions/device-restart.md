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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d1e13801e3235831081be76ddfe5c8f5872e2077
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728525"
---
# <a name="remotely-restart-devices-with-intune"></a>Reinicio remoto de los dispositivos con Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

La acción de dispositivo **Reiniciar** permite que se reinicie el dispositivo elegido. Como al propietario del dispositivo no se le notifica automáticamente del reinicio, podría perder trabajo.

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

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Seleccione **Dispositivos** > **Todos los dispositivos**.
4. En la lista de dispositivos que administra, seleccione un dispositivo, seleccione **Más** y, luego, seleccione la acción remota de dispositivo **Reiniciar**.

## <a name="next-steps"></a>Pasos siguientes

- Para ver el estado de la acción de dispositivo **Reiniciar**, seleccione **Dispositivos** > **Acciones de dispositivo**.
