---
title: Bloquear dispositivos con Microsoft Intune - Azure | Microsoft Docs
description: Use la acción de bloqueo remoto de Microsoft Intune para bloquear un dispositivo protegido por un PIN o contraseña.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 59a55de54a5a18f5fd1080fefa15c0e4801a1456
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/09/2018
---
# <a name="remotely-lock-devices-with-intune"></a>Bloqueo remoto de dispositivos con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Bloqueo remoto** bloquea el dispositivo. Para desbloquearlo, el propietario del dispositivo debe introducir su código de acceso. Puede bloquear de forma remota los dispositivos que dispongan de PIN o contraseña. Los dispositivos que no tienen PIN o contraseña no se pueden bloquear de forma remota.

## <a name="supported-platforms"></a>Plataformas compatibles

Bloqueo remoto es compatible con las siguientes plataformas:

- Android
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 y versiones posteriores

**No** se admite en:
- Windows 10 Escritorio

> [!NOTE]
> Para los dispositivos MacOS, establezca un PIN de recuperación de 6 dígitos. Una vez bloqueado, en **Información general del dispositivo** se muestra el PIN hasta que se envía otra acción de dispositivo.

## <a name="remote-lock-a-device"></a>Bloquear de forma remota un dispositivo

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos, seleccione un dispositivo y, a continuación, seleccione la acción **Bloqueo remoto**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de esta acción, abra **Acciones de dispositivo** (Microsoft Intune > Dispositivos). Consulte [Acciones disponibles](device-management.md) para ver más acciones para administrar dispositivos.