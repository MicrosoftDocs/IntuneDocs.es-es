---
title: Eliminación de un usuario de un dispositivo iOS/iPadOS con Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo quitar un usuario de un dispositivo iOS/iPadOS compartido con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b6b2b3492b9edece6b69e4b302741c0443c0a3e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415568"
---
# <a name="remove-a-user-from-a-shared-iosipados-device"></a>Eliminación de un usuario de un dispositivo iOS/iPadOS compartido


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

La acción **Quitar usuario** elimina un usuario que seleccione de la memoria caché local en un dispositivo iPad compartido. El dispositivo iPad debe estar configurado para administrar la aplicación de Classroom de iOS/iPadOS mediante un [perfil educativo de iOS/iPadOS](../fundamentals/education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: no compatible
- Windows Phone: no compatible
- iOS/iPadOS: compatible con iOS/iPadOS 9.3 y versiones posteriores (solo dispositivos iPad compartidos)
- macOS: no compatible
- Android: no compatible

## <a name="remove-a-user"></a>Quitar un usuario

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Todos los dispositivos**.
3. En la lista de dispositivos que administra, seleccione un dispositivo iOS/iPadOS.
4. En el panel del dispositivo, seleccione **Usuarios**.
5. En la lista, haga clic con el botón derecho en el usuario que quiere quitar y, después, seleccione **Quitar usuario**.

## <a name="next-steps"></a>Pasos siguientes

- Para ver el estado de la acción **Quitar usuario**, seleccione **Dispositivos** > **Acciones de dispositivo**.
