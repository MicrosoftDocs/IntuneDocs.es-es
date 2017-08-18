---
title: "Cerrar la sesión del usuario de un dispositivo iOS con Intune"
titleSuffix: Intune on Azure
description: "Obtenga información sobre cómo cerrar la sesión del usuario actual de un dispositivo iOS con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1de2069b7b25ee5e5c21a8e4caa7512f13d4ca0e
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2017
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Cerrar la sesión del usuario actual en dispositivos iOS administrados con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


La acción **Cerrar sesión del usuario actual** cierra la sesión del usuario actual en un dispositivo iPad compartido que está configurado para administrar la aplicación Classroom para iOS con un [perfil educativo de iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: no compatible
- Windows Phone: no compatible
- iOS: compatible en iOS 9.3 y versiones posteriores (solo dispositivos iPad compartidos)
- macOS: no compatible
- Android: no compatible

## <a name="how-to-logout-the-current-user"></a>Cómo cerrar la sesión del usuario actual

1.  Inicie sesión en el portal de Azure.
2.  Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3.  En la hoja **Intune**, elija **Dispositivos**.
4.  En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5.  En la lista de dispositivos que administra, seleccione un dispositivo iOS y, luego, seleccione la acción remota del dispositivo **Cerrar sesión del usuario actual**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.
