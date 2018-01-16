---
title: "Búsqueda de dispositivos iOS perdidos con Intune"
titlesuffix: Azure portal
description: Aprenda a buscar dispositivos iOS perdidos o robados con Intune.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 036ef508467e811b689393a157ada541fea70bcc
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Búsqueda de dispositivos iOS perdidos o robados con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Buscar dispositivos** muestra la ubicación de un dispositivo iOS perdido o robado en un mapa. El dispositivo debe ser un dispositivo iOS de la empresa, inscrito mediante DEP, que esté en modo supervisado. Antes de usar esta acción, se debe haber colocado el dispositivo en [modo perdido](/intune-azure/manage-devices/lost-mode.md).

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows: no compatible
- Windows Phone: no compatible
- iOS: compatible en iOS 9.3 y versiones posteriores (en modo Perdido), supervisado y de propiedad corporativa
- macOS: no compatible
- Android: no compatible

## <a name="how-to-locate-a-lost-or-stolen-device"></a>Cómo buscar un dispositivo extraviado o robado

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo iOS y luego elija la acción remota **Buscar dispositivo**.
6. Cuando se haya localizado el dispositivo, se muestra su ubicación en la hoja **Buscar dispositivo**.
    ![Hoja Buscar dispositivo](./media/locate-device.png)

>[!NOTE]
>Por motivos de privacidad, se limita la distancia con la que puede hacer zoom en el mapa.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Información de seguridad y privacidad de las acciones Modo Perdido y Buscar dispositivo
- No se envía ningún dato relacionado con la ubicación del dispositivo a Intune hasta que active esta acción.
- Cuando se usa la acción Buscar dispositivo, las coordenadas de latitud y longitud del dispositivo se envían a Intune y se muestran en Azure Portal.
- Los datos se almacenan durante 24 horas y, más adelante, se eliminan. No se puede quitar manualmente la información de ubicación.
- Los datos de ubicación permanecen cifrados mientras están almacenados y transmitiéndose.
- Al configurar el modo perdido, se recomienda que el mensaje que especifique para mostrarse en la pantalla de bloqueo incluya información que sirva para que la persona que se encuentra el dispositivo pueda devolverlo.


## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en la hoja **Dispositivos y grupos**, elija **Acciones de dispositivo**.