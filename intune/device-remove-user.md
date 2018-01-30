---
title: Quitar un usuario de un dispositivo iOS con Intune
titlesuffix: Azure portal
description: "Obtenga información sobre cómo quitar un usuario de un dispositivo iOS compartido con Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 979614aaa450493ea0b5cc2a1baaccc10a6dd028
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="remove-a-user-from-a-shared-ios-device-with-intune"></a>Quitar un usuario de un dispositivo iOS compartido con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción **Quitar usuario** elimina un usuario elegido de la memoria caché local en un dispositivo iPad compartido que se ha configurado para administrar la aplicación Classroom para iOS con un [perfil educativo de iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: no compatible
- Windows Phone: no compatible
- iOS: compatible en iOS 9.3 y versiones posteriores (solo dispositivos iPad compartidos)
- macOS: no compatible
- Android: no compatible

## <a name="how-to-remove-a-user"></a>Cómo quitar un usuario

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos**, pulse **Todos los dispositivos**.
5. De la lista de dispositivos que administra, seleccione un dispositivo iOS.
6. En la hoja de ese dispositivo, pulse **Usuarios**.
7. De la lista, haga clic con el botón derecho en el usuario que quiere quitar y, después, pulse **Quitar usuario**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.
