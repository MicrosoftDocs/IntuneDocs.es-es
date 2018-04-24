---
title: Cierre de la sesión del usuario de un dispositivo iOS
titlesuffix: Microsoft Intune
description: Obtenga información sobre cómo cerrar la sesión del usuario actual de un dispositivo iOS con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 223906d37159ba4081f5a5c055392321ac02e0ab
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Cerrar la sesión del usuario actual en dispositivos iOS administrados con Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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
