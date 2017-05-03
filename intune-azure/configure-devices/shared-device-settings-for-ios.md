---
title: "Valores de configuración de dispositivo compartido de Intune para iOS"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Azure de Intune: conozca la configuración de Intune que puede usar para mostrar información en la pantalla de bloqueo del dispositivo iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 4/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 2bc107054f438d5ed72de87dec85900f871c0acc
ms.lasthandoff: 04/19/2017


---

# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Valores de configuración de dispositivo compartido para mostrar mensajes en la pantalla de bloqueo del dispositivo iOS

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Los valores de configuración de dispositivo compartido le permiten especificar texto opcional que se muestra en la ventana de inicio de sesión y la pantalla de bloqueo (por ejemplo, un mensaje "Si está perdido, devolver a" y la información de etiqueta del activo). 

>[!IMPORTANT]
> Esta funcionalidad es compatible con dispositivos supervisados en los que se ejecutan iOS 9.3 y versiones posteriores.

1. En la hoja **Características del dispositivo**, elija **Configuración de dispositivo compartido (solo supervisado)**.
2. En la hoja **Configuración de dispositivo compartido (solo supervisado)**, configure lo siguiente:
    - **Información de etiqueta del activo**: escriba información sobre la etiqueta del activo del dispositivo. Por ejemplo: **Propiedad de Contoso Corp**. La información que escriba se aplicará a todos los dispositivos a los que asigne este perfil.
    - **Nota al pie de pantalla de bloqueo**: escriba una nota que pueda ayudar a que devuelvan el dispositivo si se pierde o se lo roban. Por ejemplo: **Si lo encuentra, llame al "número"**.
3. Cuando termine, elija **Aceptar** hasta que vuelva a la hoja **Crear perfil** y, luego, elija **Crear**. 

