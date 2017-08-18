---
title: "Eliminación de datos de la compañía de los dispositivos con Intune"
titleSuffix: Intune on Azure
description: "Aprenda a quitar únicamente los datos de la compañía de los dispositivos que administra con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b0cc7d62770057ff9df5a36e6e5df58b29430534
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>Eliminación de datos de la compañía de los dispositivos administrados con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Eliminar datos de la compañía** quita únicamente los datos de la compañía de los dispositivos administrados por Intune. No se quitan datos personales del dispositivo. Después de la eliminación, el dispositivo ya no se administra mediante Intune y ya no tiene acceso a recursos corporativos.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: compatible (no compatible en dispositivos Windows unidos a Azure Active Directory)
- Windows Phone: compatible
- iOS: compatible
- macOS: compatible
- Android: compatible

## <a name="how-to-remove-company-data"></a>Cómo eliminar datos de la compañía

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo y luego elija la acción de dispositivo remoto **Eliminar datos de la compañía**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.
