---
title: "Restablecimiento y eliminación de códigos de acceso de dispositivo con Intune"
titlesuffix: Azure portal
description: "Aprenda a restablecer y a quitar el código de acceso en los dispositivos que administra con Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3fdbb2fe6d52eaff8844ccfe14cef6c15a31cdff
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
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

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo y seleccione la acción remota de dispositivo **Quitar código de acceso**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.
