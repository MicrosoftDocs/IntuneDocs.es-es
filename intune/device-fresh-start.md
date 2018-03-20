---
title: 'Restablecimiento de dispositivos Windows 10 con Microsoft Intune: Azure | Microsoft Docs'
description: "Use Empezar de cero para quitar o desinstalar aplicaciones en equipos con Windows 10 mediante Microsoft Intune, incluidas las aplicaciones preinstaladas de los OEM. También puede mantener el contenido de la carpeta Inicio mediante la configuración que indica si se conservan los datos del usuario."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d17c9dc11791f32f0c2c1e7faa88966c112fc6a5
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/09/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Uso de Empezar de cero para restablecer dispositivos Windows 10 con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Empezar de cero** permite quitar las aplicaciones que están instaladas en un equipo que ejecuta Windows 10 Creators Update. Después, actualiza automáticamente el equipo a la versión más reciente de Windows.

Esta acción ayuda a eliminar aplicaciones preinstaladas (OEM) que normalmente se instalan con un nuevo equipo. Para mantener el contenido de la carpeta Inicio del usuario y quitar solo las aplicaciones y la configuración, use el valor `if user data is retained`.

> [!IMPORTANT]
> La característica Empezar de cero anula la inscripción del dispositivo de Intune, pero este sigue unido en Azure Active Directory.

## <a name="use-fresh-start"></a>Uso de Empezar de cero

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Elija **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos que administra, elija un dispositivo de Windows 10 Desktop y, luego, seleccione **Empezar de cero**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de esta acción, seleccione **Acciones de dispositivo** (**Microsoft Intune** > **Dispositivos**).