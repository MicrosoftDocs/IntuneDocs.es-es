---
title: Administrar dispositivos con Intune
titleSuffix: Intune on Azure
description: Aprenda a ver los dispositivos que administra con Intune y a realizar varias operaciones en ellos.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5d78b4a87eaa366b7bb00356c4b98d609620dcf3
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>¿Qué es la administración de dispositivos de Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La carga de trabajo de **Dispositivos**ofrece información sobre los dispositivos que administra y permite realizar tareas remotas en esos dispositivos. Para acceder a la carga de trabajo:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. Puede consultar la información sobre los dispositivos y realizar las acciones de dispositivo remoto que se muestran a continuación.

## <a name="available-device-actions"></a>Acciones de dispositivo disponibles
Las acciones disponibles dependen de la plataforma y la configuración del dispositivo.

- [Visualización del inventario de dispositivos](device-inventory.md)
- Realice acciones de dispositivo remoto:
    - [Eliminar datos de la compañía](devices-wipe.md#remove-company-data)
    - [Restablecimiento de la configuración de fábrica](devices-wipe.md#factory-reset)
    - [Bloqueo remoto](device-remote-lock.md) 
    - [Restablecer el código de acceso](device-passcode-reset.md)
    - [Omitir Bloqueo de activación](device-activation-lock-bypass.md) (solo para iOS)
    - [Comienzo de cero](device-fresh-start.md) (solo para Windows)
    - [Modo perdido](device-lost-mode.md) (solo para iOS)
    - [Buscar dispositivo](device-locate.md) (solo para iOS)
    - [Reiniciar](device-restart.md) (solo para Windows)
    - [Restablecimiento del PIN de Windows 10](device-windows-pin-reset.md)
    - [Control remoto en Android](device-profile-android-teamviewer.md)
    - [Sincronización del dispositivo](device-sync.md)


## <a name="next-steps"></a>Pasos siguientes

- Elija **Acciones de dispositivo** para ver el estado de las acciones realizadas en los dispositivos que administra.
![Supervisión de acciones de dispositivo](./media/monitor-device-actions.png)
