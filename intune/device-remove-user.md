---
title: "Eliminación de un usuario de un dispositivo iOS con Microsoft Intune"
titlesuffix: 
description: "Descubra cómo quitar un usuario de un dispositivo iOS compartido con Intune."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ce1b6b439c287b67a7c9e776edf136e78e5ecf5b
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Eliminación de un usuario de un dispositivo iOS compartido


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción **Quitar usuario** elimina un usuario elegido de la memoria caché local en un dispositivo iPad compartido que se ha configurado para administrar la aplicación Classroom para iOS con un [perfil educativo de iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: no compatible
- Windows Phone: no compatible
- iOS: compatible en iOS 9.3 y versiones posteriores (solo dispositivos iPad compartidos)
- macOS: no compatible
- Android: no compatible

## <a name="how-to-remove-a-user"></a>Cómo quitar un usuario

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos**, pulse **Todos los dispositivos**.
5. De la lista de dispositivos que administra, seleccione un dispositivo iOS.
6. En la hoja de ese dispositivo, pulse **Usuarios**.
7. De la lista, haga clic con el botón derecho en el usuario que quiere quitar y, después, pulse **Quitar usuario**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos**, elija **Acciones de dispositivo**.
