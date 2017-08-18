---
title: "Activación del modo perdido de iOS con Intune"
titleSuffix: Intune on Azure
description: Aprenda a usar Intune para activar el modo perdido en dispositivos iOS perdidos o robados.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5ed792011de9109dd415ba2fac3c9428e955e5e7
ms.sourcegitcommit: 2ed8d1c39d4b3e3282111f1d758afb3a50f19f8f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2017
---
# <a name="activate-lost-mode-on-ios-devices"></a>Activación del modo perdido en dispositivos iOS


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Modo perdido** le ayuda a habilitar el modo perdido en dispositivos iOS perdidos o robados. Este modo le permite especificar un mensaje y un número de teléfono que se mostrarán en la pantalla de bloqueo del dispositivo.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: no compatible
- Windows Phone: no compatible
- iOS: compatible en iOS 9.3 y versiones posteriores, supervisado y de propiedad corporativa
- macOS: no compatible
- Android: no compatible

## <a name="how-to-activate-lost-mode"></a>Cómo activar el modo Perdido

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo iOS y luego elija la acción remota **Modo perdido**.
6. En la hoja **Modo Perdido**, habilite el modo Perdido. Después, escriba el mensaje que se mostrará y, opcionalmente, un número de teléfono de contacto.
7. Haga clic en **Aceptar**.

Al habilitar Modo Perdido, se bloquea el uso del dispositivo al completo. El usuario final no puede acceder al dispositivo hasta que deshabilite Modo Perdido. Mientras Modo Perdido esté habilitado, puede utilizar la acción **Buscar dispositivo** para averiguar dónde está el dispositivo.
Para usar el modo Perdido, debe ser un dispositivo iOS de empresa con el modo supervisado.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Información de seguridad y privacidad de las acciones Modo Perdido y Buscar dispositivo
- No se envía ningún dato relacionado con la ubicación del dispositivo a Intune hasta que active esta acción.
- Cuando se usa la acción Buscar dispositivo, las coordenadas de latitud y longitud del dispositivo se envían a Intune y se muestran en Azure Portal.
- Los datos se almacenan durante 24 horas y, más adelante, se eliminan. No se puede quitar manualmente la información de ubicación.
- Los datos de ubicación permanecen cifrados mientras están almacenados y transmitiéndose.
- Se recomienda que el mensaje que especifique para mostrarse en la pantalla de bloqueo incluya información que sirva para que la persona que encuentre el dispositivo pueda devolverlo.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.

