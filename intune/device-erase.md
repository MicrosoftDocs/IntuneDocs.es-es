---
title: Borrar el contenido de un dispositivo macOS
titlesuffix: Azure portal
description: "Obtenga información sobre cómo borrar todos los datos, incluido el sistema operativo, de un dispositivo macOS."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 81f328004863e812b706174e74a9b74d0bdf80b6
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="erase-all-data-from-a-macos-device"></a>Borrar todos los datos de un dispositivo macOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Puede borrar todos los datos de un dispositivo macOS, incluido el sistema operativo. El dispositivo también se eliminará de la administración de Intune. No se proporcionará ninguna advertencia al usuario final.

1. En [Azure Portal de Intune](https://aka.ms/intuneportal), elija **Dispositivos** > **Todos los dispositivos** > elija el dispositivo cuyo contenido desee borrar.
![Captura de pantalla](./media/device-erase/choosedevice.png)
2. Haga clic en **Más** > **Borrar** > proporcione un número de 6 dígitos para el **PIN de recuperación**. Este es el PIN que debe proporcionar al usuario para que pueda volver a instalar el sistema operativo en su dispositivo. No olvide anotar este PIN porque no podrá verlo una vez completada la acción de borrado.
![Captura de pantalla](./media/device-erase/providepin.png)
3. Haga clic en **Aceptar** para borrar el dispositivo.
