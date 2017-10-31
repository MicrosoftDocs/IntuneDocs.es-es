---
title: "Sincronización de dispositivos con Intune"
titlesuffix: Azure portal
description: "Aprenda a sincronizar dispositivos con Intune para obtener las directivas y las acciones más recientes."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dadcd33f39827365fc3f22c46d4332f3ea3cbf09
ms.sourcegitcommit: a1c751959c9b3d5678bd9d67007e762df30eab59
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2017
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>Sincronización de dispositivos con Intune para obtener las directivas y las acciones más recientes


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La acción de dispositivo **Sincronizar** fuerza al dispositivo seleccionado a registrarse inmediatamente en Intune. Cuando un dispositivo se registra, recibe de inmediato las acciones o las directivas pendientes que se le han asignado.  Esta acción puede ayudarle a validar y a solucionar problemas de directivas que se le hayan asignado inmediatamente, sin tener que esperar al siguiente registro programado.

## <a name="supported-platforms"></a>Plataformas compatibles

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="how-to-sync-a-device"></a>Cómo sincronizar un dispositivo

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos y grupos**, elija **Todos los dispositivos**.
5. En la lista de dispositivos que administra, elija un dispositivo y seleccione la acción remota **Sincronizar**.
7. Haga clic en **Sí** para confirmar la acción.


## <a name="retriable-error-codes"></a>Códigos de error que admiten reintentos

Cuando un administrador ejecute la acción de dispositivo **Sincronización**, las aplicaciones de iOS y Android que han fallado pero han generado un código de error que admite reintentos estarán disponibles para el dispositivo. En cambio, las aplicaciones que han generado un código de error que no admite reintentos deberán esperar siete días antes de estar disponibles para el dispositivo.


| Código de error  | Sugerencia de descripción                                                                                                                  | Admite reintentos |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------|-----------|
| 2016330898 | Se produjo un error desconocido.                                                                                                             | No        |
| 2016330897 | La conexión a Intune ha agotado el tiempo de espera. Restablezca la conexión.                                                                             | Sí       |
| 2016330896 | Ha perdido la conexión a Internet. Restablezca la conexión.                                                                            | Sí       |
| 2016330895 | Ha perdido la conexión a Internet. Restablezca la conexión.                                                                            | Sí       |
| 2016330894 | Ha perdido la conexión a Internet. Restablezca la conexión.                                                                            | Sí       |
| 2016330893 | Ha perdido la conexión a Internet. Restablezca la conexión.                                                                            | Sí       |
| 2016330892 | La itinerancia internacional se ha deshabilitado.                                                                                                     | No        |
| 2016330891 | No se puede acceder a la conexión de datos móviles de este dispositivo mientras se realiza una llamada de teléfono. Espere a que la llamada de teléfono finalice. | Sí       |
| 2016330890 | La red de telefonía móvil para este dispositivo. Estos dispositivos no se pueden usar en este momento.                                                   | No        |
| 2016330889 | Error de conexión segura. Restablezca la conexión.                                                                                   | Sí       |
| 2016330888 | Error en la evaluación de confianza del servidor.                                                                                                | No        |

## <a name="next-steps"></a>Pasos siguientes

Seleccione **Acciones de dispositivo** para ver el estado de la acción de sincronización. 
