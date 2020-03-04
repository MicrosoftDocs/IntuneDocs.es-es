---
title: Búsqueda de dispositivos iOS/iPadOS perdidos con Microsoft Intune - Azure | Microsoft Docs
description: Busque dispositivos iOS/iPadOS perdidos o robados mediante la característica de búsqueda de dispositivos de Microsoft Intune. Puede obtener detalles sobre la información de privacidad y seguridad usando la acción de búsqueda de dispositivos.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7285ba1d8df5b53411bf6462fc165beeee66172f
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782216"
---
# <a name="locate-lost-or-stolen-iosipados-devices-with-intune"></a>Búsqueda de dispositivos iOS/iPadOS perdidos o robados con Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Para descubrir la ubicación de un dispositivo iOS/iPadOS robado o perdido en un mapa, use la acción **Buscar dispositivo**. El dispositivo debe estar en modo supervisado. Antes de realizar esta acción, asegúrese de que el dispositivo esté en [modo perdido](device-lost-mode.md).

## <a name="supported-platforms"></a>Plataformas compatibles

- iOS/iPadOS 9.3 y versiones posteriores

Esta característica no se admite en los siguientes sistemas: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Búsqueda de un dispositivo perdido o robado

1. Inicie sesión en el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos que administra, seleccione un dispositivo iOS/iPadOS y seleccione **Más...** . Luego, elija la acción remota **Buscar dispositivo**.
5. Al encontrar el dispositivo, su ubicación se mostrará en **Buscar dispositivo**.
    ![Captura de pantalla de Buscar dispositivo con Intune en Azure](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>Activación de la alerta sonora de modo perdido en un dispositivo iOS

Si alguien ha perdido su dispositivo iOS/iPadOS 9.3 o versiones posteriores, puede desencadenar de forma remota una alerta sonora en el dispositivo para que el usuario pueda encontrarlo. El dispositivo debe estar en [modo perdido](device-lost-mode.md).

En [Intune en Azure Portal](https://aka.ms/intuneportal), elija **Dispositivos** > **Todos los dispositivos** > seleccione un dispositivo iOS/iPadOS > **Información general** > **Más** > **Reproducir un sonido para el modo Perdido (solo supervisado)** .

El sonido sigue reproduciéndose hasta que el usuario lo deshabilita en el dispositivo o este se quita del modo perdido.


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Información de seguridad y privacidad de las acciones de modo perdido y buscar dispositivo
- No se envía ningún dato relacionado con la ubicación del dispositivo a Intune hasta que active esta acción.
- Cuando se usa la acción Buscar dispositivo, las coordenadas de latitud y longitud del dispositivo se puede recuperar mediante Graph API.
- Los datos se almacenan durante 24 horas y, más adelante, se eliminan. No se puede quitar manualmente la información de ubicación.
- Los datos de ubicación permanecen cifrados mientras están almacenados y transmitiéndose.
- Al configurar el modo perdido, puede personalizar un mensaje para que se muestre en la pantalla de bloqueo. Para ayudar a la persona que encuentre el dispositivo, incluya en este mensaje detalles específicos para devolver el dispositivo perdido.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de habilitación de Buscar dispositivo, abra **Dispositivos** y seleccione **Acciones de dispositivo**.
