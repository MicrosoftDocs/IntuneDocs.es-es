---
title: Administrar dispositivos con Intune
titleSuffix: Intune on Azure
description: Aprenda a ver los dispositivos que administra con Intune y a realizar varias operaciones en ellos.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f066e62e323fffb7c6954d83b2b55ee63f4be46
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>¿Qué es la administración de dispositivos de Microsoft Intune?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La carga de trabajo de **Dispositivos**ofrece información sobre los dispositivos que administra y permite realizar tareas remotas en esos dispositivos. Para acceder a la carga de trabajo:

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.

Ahora puede realizar las siguientes acciones:

- [Visualización del inventario de dispositivos](device-inventory.md)
- Realice acciones de dispositivo remoto:
    - [Eliminar datos de la compañía](device-company-data-remove.md) 
    - [Restablecimiento de la configuración de fábrica](device-factory-reset.md)
    - [Bloqueo remoto](device-remote-lock.md)
    - [Restablecer el código de acceso](device-passcode-reset.md)
    - [Omitir bloqueo de activación](device-activation-lock-bypass.md)
    - [Fresh Start](device-fresh-start.md)
    - [Modo Perdido](device-lost-mode.md)
    - [Buscar dispositivo](device-locate.md)
    - [Reiniciar](device-restart.md)
    - [Restablecimiento del PIN de Windows 10](device-windows-pin-reset.md)
    - [Control remoto en Android](device-profile-android-teamviewer.md)


## <a name="support-for-each-device-action"></a>Compatibilidad con cada acción de dispositivo

Use la tabla siguiente para conocer las plataformas de dispositivos que son compatibles con cada acción.

|||||||
|-|-|-|-|-|-|
|Acción de dispositivo|Windows|Windows Phone|iOS|macOS|Android|
|**Eliminar datos de la compañía**|Sí|Sí|Sí|Sí|Sí|
|**Restablecimiento de la configuración de fábrica**|Windows 8.1 y versiones posteriores (dispositivos administrados no EAS)|Sí|Sí|No|Android for Work no compatible|
|**Eliminar**|Sí|Sí|Sí|Sí|Sí|
|**Bloqueo remoto**|No|Windows Phone 8.1 y versiones posteriores|Sí|No|Sí|
|**Restablecer el código de acceso**|No|Windows Phone 8.1 a Windows 10 Creators Update no unido a Azure AD, Windows 10 Creators Update y versiones posteriores, todos|Sí|No|Anteriores a Android 7, Android for Work no compatible|
|**Nuevo código de acceso** (para dispositivos Windows 10)|No|Windows 10 Creators Update y versiones posteriores (unido a Azure AD)|No|No|Android for Work no compatible|
|**Omitir bloqueo de activación**|No|No|Solo dispositivos de propiedad corporativa|No|No|
|**Modo Perdido**|No|No|iOS 9.3 y versiones posteriores, supervisado y de propiedad corporativa|No|No|
|**Buscar dispositivo**|No|No|iOS 9.3 y versiones posteriores de modo Perdido, supervisado y de propiedad corporativa|No|No|
|**Cierre de sesión del usuario actual**|No|No|iOS 9.3 y versiones posteriores (solo dispositivos iPad compartidos)|No|No|
|**Reiniciar**|Windows 8.1 y posterior|Windows Phone 8.1 y versiones posteriores|No|No|No|
|**Fresh Start**|Windows 10 Creators Update y versiones posteriores|No|No|No|No|
|**Nueva sesión de Asistencia remota**|No|No|No|No|Sí|
|**Quitar usuario**|No|No|iOS 9.3 y versiones posteriores (solo dispositivos iPad compartidos)|No|No|

## <a name="next-steps"></a>Pasos siguientes

- Elija **Acciones de dispositivo** para ver el estado de las acciones realizadas en los dispositivos que administra. 
![Supervisión de acciones de dispositivo](./media/monitor-device-actions.png)