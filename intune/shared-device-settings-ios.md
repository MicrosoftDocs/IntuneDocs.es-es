---
title: "Valores de configuración de dispositivo compartido de Intune para iOS"
titleSuffix: Intune on Azure
description: "Obtenga información sobre la configuración de Intune que puede usar para mostrar información en la pantalla de bloqueo del dispositivo iOS\"."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61bb1f8c7a9b6c92c128f32910f2ad8d390b6c64
ms.sourcegitcommit: c9b3a95bf529b6cb2a2bdacbc49127dfa0c233e5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2017
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Valores de configuración de dispositivo compartido para mostrar mensajes en la pantalla de bloqueo del dispositivo iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Los valores de configuración de dispositivo compartido le permiten especificar texto opcional que se muestra en la ventana de inicio de sesión y la pantalla de bloqueo. Por ejemplo, puede escribir un mensaje "En caso de pérdida, devolver a" e información de etiqueta de inventario. 

>[!IMPORTANT]
> Esta funcionalidad es compatible con dispositivos supervisados en los que se ejecutan iOS 9.3 y versiones posteriores.

## <a name="create-shared-device-settings"></a>Crear una configuración de dispositivo compartido

1. En la hoja **Características del dispositivo**, pulse **Configuración de dispositivo compartido (solo supervisado)**.
2. En la hoja **Configuración de dispositivo compartido (solo supervisado)**, configure las siguientes opciones:
    - **Información de etiqueta del activo**: escriba información sobre la etiqueta del activo del dispositivo. Por ejemplo: **Propiedad de Contoso Corp**. La información que escriba se aplica a todos los dispositivos a los que asigne este perfil.
    - **Nota al pie de pantalla de bloqueo**: si el dispositivo se pierde o se lo roban, escriba una nota que pueda ayudar a que le devuelvan el dispositivo. Por ejemplo: **Si lo encuentra, llame al "número"**.
3. Cuando termine, elija **Aceptar** hasta que vuelva a la hoja **Crear perfil** y, luego, elija **Crear**. 


## <a name="next-steps"></a>Pasos siguientes

Ahora puede asignar el perfil de dispositivo a los grupos que elija. Para obtener más información, vea [Asignación de perfiles de dispositivo](device-profile-assign.md).
