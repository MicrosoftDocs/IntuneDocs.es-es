---
title: Personalización de la pantalla de bloqueo en dispositivos iOS con Microsoft Intune (Azure) | Microsoft Docs
titlesuffix: ''
description: Obtenga más información sobre la configuración de Microsoft Intune que se puede usar para mostrar información en la pantalla de bloqueo del dispositivo iOS con la configuración de dispositivo compartido para iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f4d75d795421c761398f349c324b498fd21ca01
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203083"
---
# <a name="add-custom-messages-to-lock-screen-and-login-window-on-ios-devices-using-microsoft-intune"></a>Agregue mensajes personalizados a la pantalla de bloqueo y a la ventana de inicio de sesión de dispositivos iOS con Microsoft Intune.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo se muestra la configuración de Microsoft Intune que se puede usar para mostrar información en la pantalla de bloqueo y en la ventana de inicio de sesión de dispositivo iOS. 

Use esta configuración para mostrar un mensaje o un texto personalizado en la ventana de inicio de sesión y la pantalla de bloqueo. Por ejemplo, puede escribir el mensaje "En caso de pérdida, devolver a..." y agregar información sobre la etiqueta de activo.

Esta configuración admite dispositivos supervisados que ejecuten iOS 9.3 y versiones posteriores.

## <a name="create-the-profile"></a>Creación del perfil

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los dispositivos**, filtre por **Intune** y seleccione **Intune**.
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba un **Nombre** y una **Descripción** para el perfil.
4. En **Plataforma**, seleccione **iOS**. En **Tipo de perfil**, seleccione **Características del dispositivo**.
5. En **Configuración**, seleccione **Mensaje de pantalla de bloqueo (solo supervisado)**. Configure las siguientes opciones:

    - **Información de etiqueta de activo**: escriba información sobre la etiqueta de activo del dispositivo. Por ejemplo, escriba `123xyz`.

        El texto que escriba se mostrará en la pantalla de bloqueo y de inicio de sesión del dispositivo.

    - **Nota al pie de pantalla de bloqueo**: si pierde el dispositivo o se lo roban, escriba una nota que pueda ayudar a que se lo devuelvan. En este campo puede escribir el texto que quiera. Por ejemplo, escriba algo parecido a `If found, call Contoso at ...`.

    Los tokens de dispositivo también se pueden usar para agregar información específica sobre el dispositivo a estos campos. Por ejemplo, para que se muestre el número de serie, escriba `Serial Number: {{serialnumber}}`. En la pantalla de bloqueo, el texto tendrá un aspecto similar a este: `Serial Number 123456789ABC`. Al especificar variables, no olvide usar llaves: `{{ }}`. En los [tokens de configuración de aplicación](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) podrá ver una lista de las variables que puede usar. También puede usar `deviceName` o cualquier otro valor específico del dispositivo.

6. Cuando haya terminado, seleccione **Aceptar** > **Aceptar** > **Crear**. Seguidamente, su perfil se mostrará en la lista.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
