---
title: "Restablecer los dispositivos a la configuración de fábrica con Intune"
titleSuffix: Intune on Azure
description: "Aprenda a restablecer la configuración de fábrica de los dispositivos que administra con Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8eff9b53-eef2-4c50-8aee-556bc49d69f2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fd7273d6c5f75a675d7b01df4225a96fd3a5f821
ms.sourcegitcommit: 10e3ab2aeb79a1fb2243bef2748ccc003fdd4cc7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2017
---
# <a name="reset-intune-managed-devices-to-factory-settings"></a>Restablecimiento de la configuración de fábrica de los dispositivos administrados con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

El **restablecimiento de fábrica** devuelve el dispositivo a su configuración predeterminada. Intune ya no administra el dispositivo y se quitan tanto los datos de la compañía como los personales. No se puede deshacer esta acción.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: compatible en Windows 8.1 y versiones posteriores (dispositivos administrados no EAS)
- Windows Phone: compatible
- iOS: compatible
- macOS: no compatible
- Android: compatible (Android for Work no es compatible)

## <a name="how-to-reset-a-device-to-factory-settings"></a>Cómo restablecer la configuración de fábrica de un dispositivo

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo y luego elija la acción de dispositivos remotos **Restablecimiento de fábrica**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.
