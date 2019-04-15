---
title: Cierre de la sesión del usuario de un dispositivo iOS
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo cerrar la sesión del usuario actual de un dispositivo iOS con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 23af88f4d595669589b8f7104cbac0c5b695602f
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567626"
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Cerrar la sesión del usuario actual en dispositivos iOS administrados con Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La acción **Cerrar sesión del usuario actual** cierra la sesión del usuario actual de un dispositivo iPad compartido. 

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: no compatible
- Windows Phone: no compatible
- iOS: compatible en iOS 9.3 y versiones posteriores (solo dispositivos iPad compartidos)
- macOS: no compatible
- Android: no compatible

## <a name="how-to-log-out-the-current-user"></a>Cómo cerrar la sesión del usuario actual

1.  Inicie sesión en el portal de Azure.
2.  Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3.  En la hoja **Intune**, elija **Dispositivos**.
4.  En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5.  En la lista de dispositivos que administra, seleccione un dispositivo iOS y, luego, seleccione la acción remota del dispositivo **Cerrar sesión del usuario actual**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.
