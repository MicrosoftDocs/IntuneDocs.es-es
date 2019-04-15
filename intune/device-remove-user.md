---
title: Eliminación de un usuario de un dispositivo iOS con Microsoft Intune
titleSuffix: ''
description: Descubra cómo quitar un usuario de un dispositivo iOS compartido con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53c4e02f32fa421c745f5bfa15e97023f47ece88
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568588"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Eliminación de un usuario de un dispositivo iOS compartido


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La acción **Quitar usuario** elimina un usuario que seleccione de la memoria caché local en un dispositivo iPad compartido. El dispositivo iPad debe estar configurado para administrar la aplicación de Classroom de iOS mediante un [perfil educativo de iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: no compatible
- Windows Phone: no compatible
- iOS: compatible en iOS 9.3 y versiones posteriores (solo dispositivos iPad compartidos)
- macOS: no compatible
- Android: no compatible

## <a name="remove-a-user"></a>Quitar un usuario

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, seleccione **Dispositivos**.
4. En el panel **Dispositivos**, seleccione **Todos los dispositivos**.
5. En la lista de dispositivos que administra, seleccione un dispositivo iOS.
6. En el panel del dispositivo, seleccione **Usuarios**.
7. En la lista, haga clic con el botón derecho en el usuario que quiere quitar y, después, seleccione **Quitar usuario**.

## <a name="next-steps"></a>Pasos siguientes

- Para ver el estado de la acción **Quitar usuario**, seleccione **Dispositivos** > **Acciones de dispositivo**.
