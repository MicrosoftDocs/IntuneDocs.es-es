---
title: Búsqueda de dispositivos iOS perdidos con Microsoft Intune - Azure | Microsoft Docs
description: Busque o localice dispositivos iOS perdidos o robados mediante la característica Buscar dispositivos de Microsoft Intune y obtenga detalles sobre la información de privacidad y seguridad al utilizar la acción Buscar dispositivos.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4bc51ef7f9af9cc97fd4c11408a1857679aee665
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Búsqueda de dispositivos iOS perdidos o robados con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Para descubrir la ubicación de un dispositivo iOS robado o perdido en un mapa, utilice la acción **Buscar dispositivos**. El dispositivo debe ser un dispositivo iOS de empresa, debe estar inscrito a través del programa de inscripción de dispositivos (DEP) y estar en modo supervisado. Antes de realizar esta acción, asegúrese de que el dispositivo esté en [modo perdido](device-lost-mode.md).

## <a name="supported-platforms"></a>Plataformas compatibles

- iOS 9.3 y versiones posteriores

Esta característica **no** se admite en los siguientes sistemas: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Búsqueda de un dispositivo perdido o robado

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos que administra, elija un dispositivo iOS, **Más** y luego la acción remota **Buscar dispositivo**.
5. Al encontrar el dispositivo, su ubicación se muestra en **Buscar dispositivos**.
    ![Búsqueda de un dispositivo con Intune en Azure](./media/locate-device.png)

>[!NOTE]
>Por motivos de privacidad, se limita la distancia con la que puede hacer zoom en el mapa.

## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Información de seguridad y privacidad de las acciones de modo perdido y buscar dispositivo
- No se envía ningún dato relacionado con la ubicación del dispositivo a Intune hasta que active esta acción.
- Cuando se usa la acción Buscar dispositivo, las coordenadas de latitud y longitud del dispositivo se envían a Intune y se muestran en Azure Portal.
- Los datos se almacenan durante 24 horas y, más adelante, se eliminan. No se puede quitar manualmente la información de ubicación.
- Los datos de ubicación permanecen cifrados mientras están almacenados y transmitiéndose.
- Al configurar el modo perdido, puede personalizar un mensaje para que se muestre en la pantalla de bloqueo. Para ayudar a la persona que encuentre el dispositivo, incluya en este mensaje detalles específicos para devolver el dispositivo perdido.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de habilitación de Localizar el dispositivo, abra **Dispositivos** y seleccione **Acciones de dispositivo**.
