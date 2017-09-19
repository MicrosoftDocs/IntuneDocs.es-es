---
title: "Sincronización de dispositivos con Intune"
titlesuffix: Azure portal
description: "Aprenda a sincronizar dispositivos con Intune para obtener las directivas y las acciones más recientes."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ab24b147b32c94ba51728c0c223de3e6c92dd215
ms.sourcegitcommit: cf7f7e7c9e9cde5b030cf5fae26a5e8f4d269b0d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2017
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>Sincronización de dispositivos con Intune para obtener las directivas y las acciones más recientes


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Sincronizar** fuerza al dispositivo seleccionado a registrarse inmediatamente en Intune. Cuando un dispositivo se registra, recibe de inmediato las acciones o las directivas pendientes que se le han asignado.  Esta acción puede ayudarle a validar y a solucionar problemas de directivas que se le hayan asignado inmediatamente, sin tener que esperar al siguiente registro programado.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: compatible
- Windows Phone: compatible
- iOS: compatible
- macOS: compatible
- Android: compatible

## <a name="how-to-sync-a-device"></a>Cómo sincronizar un dispositivo

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo y seleccione la acción remota **Sincronizar**.
7. Haga clic en **Sí** para confirmar la acción.

## <a name="next-steps"></a>Pasos siguientes

Seleccione **Acciones de dispositivo** para ver el estado de la acción de sincronización. 
