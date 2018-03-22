---
title: Activación del modo perdido de iOS con Microsoft Intune - Azure | Microsoft Docs
description: Active o inicie el modo perdido para personalizar mediante Microsoft Intune un mensaje que se mostrará en la pantalla de bloqueo de un dispositivo iOS perdido o robado. Además, puede obtener detalles sobre la información de privacidad y seguridad al utilizar la acción de modo perdido.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 47d6314dfaed546e5b4cff7f93a5540ba512bde9
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>Habilitar el modo perdido en dispositivos iOS con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Modo perdido** le ayuda a habilitar el modo perdido en dispositivos iOS perdidos o robados. Este modo le permite introducir un mensaje y un número de teléfono para que se muestren en la pantalla de bloqueo del dispositivo. Para usar el modo Perdido, debe ser un dispositivo iOS de empresa con el modo supervisado.

## <a name="supported-platforms"></a>Plataformas compatibles

- iOS 9.3 y versiones posteriores

Esta característica **no** se admite en los siguientes sistemas operativos: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>Habilitar el modo perdido

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos que administra, elija un dispositivo iOS, **Más** y luego la acción remota **Modo Perdido**.
5. En **Modo perdido**, habilite esta característica. A continuación, escriba el mensaje que quiere que se muestre y un número de teléfono de contacto.
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