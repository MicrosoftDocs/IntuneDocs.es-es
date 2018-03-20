---
title: "Restablecimiento de códigos de acceso de dispositivos con Microsoft Intune: Azure | Microsoft Docs"
description: "Quite o restablezca el código de acceso con la acción Quitar código de acceso en dispositivos que administre o supervise con Intune."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f23a79bbe72d12750ef642226aefd1e11dcac24
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Restablecimiento o eliminación del código de acceso de un dispositivo en Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Para crear un código de acceso para un dispositivo, use la acción **Quitar código de acceso**.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows Phone 8.1 a Windows 10 Creators Update sin unir a Azure AD, Windows 10 Creators Update y versiones posteriores
- iOS
- Versiones de Android anteriores a Android 7

Esta característica **no** se admite en los siguientes sistemas:

- Windows
- macOS
- Android for Work

## <a name="reset-a-passcode"></a>Restablecer un código de acceso

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos que administra, elija un dispositivo, **…Más** y la acción de dispositivo remoto **Quitar código de acceso**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en **Dispositivos**, elija **Acciones de dispositivo**.
