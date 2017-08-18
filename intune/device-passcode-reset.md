---
title: "Restablecimiento de un código de acceso de dispositivo con Intune"
titleSuffix: Intune on Azure
description: "Aprenda a restablecer el código de acceso en los dispositivos que administra con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 30fac990d8b4a0a088180598e7787e23b1f708b7
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2017
---
# <a name="reset-the-passcode-on-intune-managed-devices"></a>Restablecimiento del código de acceso en los dispositivos administrados con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción **Restablecer el código de acceso** genera un nuevo código de acceso para el dispositivo que se muestra en la hoja <*nombre del dispositivo*> **Introducción**.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: no compatible
- Windows Phone: compatible en Windows Phone 8.1 a Windows 10 Creators Update no unido a Azure AD, Windows 10 Creators Update y versiones posteriores
- iOS: compatible
- macOS: no compatible
- Android: compatible en versiones Android anteriores a Android 7. Android for Work no es compatible.

## <a name="how-to-reset-a-passcode"></a>Cómo restablecer un código de acceso

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo y luego elija la acción de dispositivo remoto **Restablecer el código de acceso**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.
