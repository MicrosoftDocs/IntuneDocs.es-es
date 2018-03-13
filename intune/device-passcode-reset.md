---
title: "Restablecimiento y eliminación de códigos de acceso de dispositivo con Intune"
titlesuffix: Azure portal
description: "Aprenda a restablecer y a quitar el código de acceso en los dispositivos que administra con Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e1496d24fd9d3bb636a4eab00c254b753210f63
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="reset-and-remove-the-passcode-on-intune-managed-devices"></a>Restablecimiento y eliminación del código de acceso en los dispositivos administrados con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Los términos *quitar* y *restablecer* se usan indistintamente en este artículo.

La acción **Quitar código de acceso** genera un nuevo código de acceso para el dispositivo que se muestra en la hoja **Información general** de <*nombre del dispositivo*> .

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: no compatible
- Windows Phone: compatible en Windows Phone 8.1 a Windows 10 Creators Update no unido a Azure AD, Windows 10 Creators Update y versiones posteriores
- iOS: compatible
- macOS: no compatible
- Android: compatible en versiones Android anteriores a Android 7. Android for Work no es compatible.

## <a name="how-to-reset-a-passcode"></a>Cómo restablecer un código de acceso

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos**, pulse **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo, **…Más** y la acción de dispositivo remoto **Quitar código de acceso**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos**, elija **Acciones de dispositivo**.
