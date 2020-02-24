---
title: Activación del modo perdido de iOS/iPadOS con Microsoft Intune - Azure | Microsoft Docs
description: Active o inicie el modo perdido para personalizar un mensaje que se mostrará en la pantalla de bloqueo de un dispositivo iOS/iPadOS perdido o robado mediante Microsoft Intune. Además, puede obtener detalles sobre la información de privacidad y seguridad al usar la acción de modo perdido.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a4103c819c0d4bd377b9c6ab2359cb7465cdd9c
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415595"
---
# <a name="enable-lost-mode-on-iosipados-devices-with-intune"></a>Habilitar el modo perdido en dispositivos iOS/iPadOS con Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

La acción de dispositivo **Modo perdido** le ayuda a habilitar el modo perdido en dispositivos iOS/iPadOS perdidos o robados. Este modo le permite introducir un mensaje y un número de teléfono para que se muestren en la pantalla de bloqueo del dispositivo. Para usar el modo perdido, debe ser un dispositivo iOS/iPadOS de empresa con el modo supervisado.

## <a name="supported-platforms"></a>Plataformas compatibles

- iOS/iPadOS 9.3 y versiones posteriores

Esta característica no se admite en los siguientes sistemas operativos: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>Habilitar el modo perdido

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos que administra, elija un dispositivo iOS/iPadOS y luego elija **Modo Perdido (solo supervisado)** .
5. En **Modo Perdido**, seleccione **Habilitar**.
6. En el **mensaje para mostrar en la pantalla de bloqueo**, escriba el mensaje que se mostrará en dicha pantalla del dispositivo.
7. Opcionalmente, escriba un número de teléfono en el cuadro **Número de teléfono que se muestra**.
6. Haga clic en **Aceptar** para guardar los cambios.

Al habilitar el modo perdido, se bloquea totalmente el uso del dispositivo. El usuario final no puede acceder al dispositivo hasta que deshabilite Modo Perdido. Mientras el modo perdido está habilitado, use la acción [Buscar dispositivo](device-locate.md) para encontrar el dispositivo.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Información de seguridad y privacidad de las acciones Modo Perdido y Buscar dispositivo
- No se envía ningún dato relacionado con la ubicación del dispositivo a Intune hasta que active esta acción.
- Cuando se usa la acción Buscar dispositivo, las coordenadas de latitud y longitud del dispositivo se envían a Intune y se muestran en Azure Portal.
- Los datos se almacenan durante 24 horas y, más adelante, se eliminan. No se puede quitar manualmente la información de ubicación.
- Los datos de ubicación permanecen cifrados mientras están almacenados y transmitiéndose.
- En el mensaje que introduzca para que se muestre en la pantalla de bloqueo, no olvide incluir detalles específicos para devolver el dispositivo perdido.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de habilitación del Modo perdido, abra **Dispositivos** y seleccione **Acciones de dispositivo**.
