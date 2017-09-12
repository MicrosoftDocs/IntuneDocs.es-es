---
title: Restablecimiento de dispositivos Windows 10 con Intune
titlesuffix: Azure portal
description: Aprenda a usar Empezar de cero para restablecer equipos con Windows 10 que ejecutan Intune.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1b59db6f876e1a7353acda63b6b5acdbb5961cb0
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Uso de Empezar de cero para restablecer dispositivos Windows 10 con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción del dispositivo **Empezar de cero** elimina las aplicaciones que se instalaron en un equipo Windows 10 mediante la ejecución de Creators Update y luego actualiza automáticamente el equipo a la versión más reciente de Windows.
Esto puede servir para ayudar a quitar las aplicaciones de OEM preinstaladas que a menudo se entregan con los nuevos equipos. Puede configurar si se conservan los datos de usuario cuando se lleva a cabo esta acción de dispositivo. En este caso, se quitan las aplicaciones y la configuración, pero se conserva el contenido de la carpeta de inicio de los usuarios.

## <a name="how-to-use-fresh-start"></a>Cómo usar Empezar de cero

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo de Windows 10 Escritorio y luego elija la acción de dispositivo remoto **Empezar de cero**.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.

