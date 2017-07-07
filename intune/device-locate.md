---
title: "Búsqueda de dispositivos iOS perdidos con Intune"
titleSuffix: Intune on Azure
description: Aprenda a buscar dispositivos iOS perdidos o robados con Intune.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 80aa0e5afd1f8862b181d455ff6b545e462f90c9
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Búsqueda de dispositivos iOS perdidos o robados con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Buscar dispositivos** muestra la ubicación de un dispositivo iOS perdido o robado en un mapa. El dispositivo debe ser un dispositivo iOS de la empresa, inscrito mediante DEP, que esté en modo supervisado. Antes de usar esta acción, se debe haber colocado el dispositivo en [modo perdido](/intune-azure/manage-devices/lost-mode.md).

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
