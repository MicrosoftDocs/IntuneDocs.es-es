---
title: Valores de configuración de dispositivo compartido de Microsoft Intune para iOS
titlesuffix: ''
description: Obtenga información sobre la configuración de Microsoft Intune que se puede usar para mostrar información en la pantalla de bloqueo del dispositivo iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7c735486ad93bd76350435861482505a1ab0d30a
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31834234"
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Valores de configuración de dispositivo compartido para mostrar mensajes en la pantalla de bloqueo del dispositivo iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo se muestra la configuración de Microsoft Intune que se puede usar para mostrar información en la pantalla de bloqueo del dispositivo iOS.

Los valores de configuración de dispositivo compartido le permiten especificar texto opcional que se muestra en la ventana de inicio de sesión y la pantalla de bloqueo. Por ejemplo, puede escribir un mensaje "En caso de pérdida, devolver a" e información de etiqueta de inventario. 

>[!IMPORTANT]
> Esta funcionalidad es compatible con dispositivos supervisados en los que se ejecutan iOS 9.3 y versiones posteriores.

## <a name="create-shared-device-settings"></a>Crear una configuración de dispositivo compartido

1. Desde [Intune en Azure Portal](https://portal.azure.com), vaya a [**Características del dispositivo** en el área de configuración de dispositivos](device-features-configure.md). 
1. En el panel **Características del dispositivo**, pulse **Configuración de dispositivo compartido (solo supervisado)**.
2. En el panel **Configuración de dispositivo compartido (solo supervisado)**, configure las opciones siguientes:
    - **Información de etiqueta del activo**: escriba información sobre la etiqueta del activo del dispositivo. Por ejemplo: **Propiedad de Contoso Corp**. La información que escriba se aplica a todos los dispositivos a los que asigne este perfil.
    - **Nota al pie de pantalla de bloqueo**: si el dispositivo se pierde o se lo roban, escriba una nota que pueda ayudar a que le devuelvan el dispositivo. Por ejemplo: **Si lo encuentra, llame al "número"**.
3. Cuando termine, haga clic en **Aceptar** hasta que vuelva al panel **Crear perfil** y, luego, haga clic en **Crear**. 


## <a name="next-steps"></a>Pasos siguientes

Ahora puede asignar el perfil de dispositivo a los grupos que elija. Para obtener más información, vea [Asignación de perfiles de dispositivo](device-profile-assign.md).
