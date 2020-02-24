---
title: Sincronizar dispositivos con Microsoft Intune - Azure | Microsoft Docs
description: Sincronice los dispositivos registrados o administrados con Microsoft Intune para obtener las directivas y acciones más recientes. Incluye los pasos necesarios para efectuar la sincronización con Azure Portal y se enumeran los códigos de error que se pueden recuperar.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21167b226556100e7e9920f31f859d6d6ce2a7bb
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415530"
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>Sincronización de dispositivos para obtener las directivas y las acciones más recientes con Intune


La acción del dispositivo **Sincronizar** obliga al dispositivo seleccionado a registrarse inmediatamente con Intune. Cuando un dispositivo se registra, recibe de inmediato las acciones o las directivas pendientes que se le han asignado. Esta característica puede ayudarle a validar y a solucionar problemas de directivas que se le hayan asignado inmediatamente, sin tener que esperar al siguiente registro programado.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>Sincronizar un dispositivo

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431). 
3. Seleccione **Dispositivos** > **Todos los dispositivos**.
4. En la lista de dispositivos que administra, seleccione un dispositivo para abrir su panel de *información general* y, luego, seleccione **Sincronizar**.
5. Para confirmar, seleccione **Sí**.

Seleccione **Dispositivos** > **Acciones de dispositivo** para ver el estado de la acción de sincronización.

Puede encontrar las frecuencias de sincronización de directivas de Intune estándar en [Tiempos de ciclo de actualización](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

## <a name="retryable-error-codes"></a>Códigos de error que admiten reintentos

Cuando un administrador ejecute la acción de dispositivo **Sincronizar**, las aplicaciones iOS/iPadOS y Android que han generado un código de error que admite reintentos siguen estando disponibles para el dispositivo. En cambio, las aplicaciones que han generado un código de error que no admite reintentos deberán esperar siete días antes de estar disponibles en el dispositivo.


| Código de error  | Descripción sugerida | Admite reintentos |
|---|---|---|
| 2016330898 | Se produjo un error desconocido. | No |
| 2016330897 | La conexión a Intune ha agotado el tiempo de espera. Restablezca la conexión. | Sí |
| 2016330896 | Ha perdido la conexión a Internet. Restablezca la conexión. | Sí |
| 2016330895 | Ha perdido la conexión a Internet. Restablezca la conexión. | Sí |
| 2016330894 | Ha perdido la conexión a Internet. Restablezca la conexión. | Sí |
| 2016330893 | Ha perdido la conexión a Internet. Restablezca la conexión. | Sí|
| 2016330892 | La itinerancia internacional se ha deshabilitado. | No|
| 2016330891 | No se puede acceder a la conexión de datos móviles de este dispositivo mientras se realiza una llamada de teléfono. Espere a que la llamada de teléfono finalice. | Sí|
| 2016330890 | La red de telefonía móvil para este dispositivo. Estos dispositivos no se pueden usar en este momento. | No|
| 2016330889 | Error de conexión segura. Restablezca la conexión. | Sí|
| 2016330888 | Error en la evaluación de confianza del servidor. | No|

## <a name="next-steps"></a>Pasos siguientes

Puede [consultar los detalles](device-inventory.md) del dispositivo.
 
