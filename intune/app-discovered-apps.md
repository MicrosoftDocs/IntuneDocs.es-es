---
title: Aplicaciones detectadas
titleSuffix: Microsoft Intune
description: Conozca los detalles sobre las aplicaciones detectadas que Intune ha encontrado en un dispositivo.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53555a01899cfec15c319e790620b2bfeaa302bc
ms.sourcegitcommit: 948ff8f56639e6dc7091134a0efd8d44efca63f2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2019
ms.locfileid: "68590915"
---
# <a name="intune-discovered-apps"></a>Aplicaciones descubiertas de Intune

Las **aplicaciones descubiertas** de Intune es una lista de aplicaciones detectadas en los dispositivos inscritos en Intune del inquilino. Actúa como un inventario de software para el inquilino. **Aplicaciones descubiertas** es un informe independiente de los informes de [instalación de aplicaciones](apps-monitor.md). En el caso de los dispositivos personales, Intune nunca recopila información sobre las aplicaciones que no están administradas. En los dispositivos corporativos, todas las aplicaciones, tanto si están administradas como si no, se recopilan para este informe. Debajo está la tabla que asigna el comportamiento esperado. En general, el informe se actualiza cada 7 días desde el momento de la inscripción (no una actualización semanal para todo el inquilino). La única excepción a este período de actualización es la información de la aplicación recopilada a través de la Extensión de administración de Intune para aplicaciones Win32, que se recopila cada 24 horas.

## <a name="monitor-discovered-apps-with-intune"></a>Supervisión de aplicaciones descubiertas con Intune

Intune proporciona una lista agregada de aplicaciones detectadas en los dispositivos inscritos en Intune del inquilino.

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. En el panel **Intune**, seleccione **Aplicaciones cliente** > **Aplicaciones descubiertas**.

>[!NOTE]
>Puede exportar la lista de aplicaciones descubiertas a un archivo .csv seleccionando **Exportar** en la hoja **Aplicaciones descubiertas**.
>
>Para las aplicaciones Win32 detectadas, no hay actualmente ningún recuento agregado. Este tipo de datos solo se puede ver en cada dispositivo.

Intune también proporciona la lista de aplicaciones detectadas de cada dispositivo del inquilino. 

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. En el panel de Intune, seleccione **Dispositivos** > **Todos los dispositivos**.
3. Seleccione un dispositivo.
4. Para ver las aplicaciones detectadas de este dispositivo , seleccione **Aplicaciones detectadas** en la sección **Supervisión**. 

## <a name="details-of-discovered-apps"></a>Detalles de las aplicaciones descubiertas

En la lista siguiente se proporciona el tipo de plataforma de aplicaciones, las aplicaciones que se supervisan para dispositivos personales, las aplicaciones que se supervisan para dispositivos propiedad de la empresa y el ciclo de actualización. Para obtener más información sobre los tipos de aplicaciones que admite Intune, consulte [Tipos de aplicaciones en Microsoft Intune](apps-add.md#app-types-in-microsoft-intune).

| Plataforma | Para dispositivos personales | Para dispositivos propiedad de la empresa | Ciclo de actualización |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Nota de Windows 10 (aplicaciones Win32): [Requiere la Extensión de administración de Intune](intune-management-extension.md) en el dispositivo | No aplicable | Todas las aplicaciones Win32 encontradas en la lista Agregar o quitar programas | Cada 24 horas a partir de la inscripción del dispositivo |
| Windows 10 (aplicaciones modernas) | Solo aplicaciones modernas administradas | Todas las aplicaciones modernas instaladas en el dispositivo | Cada 7 días a partir de la inscripción de dispositivos |
| Windows 8.1 | Solo aplicaciones administradas | Solo aplicaciones administradas | Cada 7 días a partir de la inscripción de dispositivos |
| Windows Phone 8 | Solo aplicaciones administradas | Solo aplicaciones administradas | Cada 7 días a partir de la inscripción de dispositivos |
| Windows RT | Solo aplicaciones administradas | Solo aplicaciones administradas | Cada 7 días a partir de la inscripción de dispositivos |
| iOS | Solo aplicaciones administradas | Todas las aplicaciones instaladas en el dispositivo | Cada 7 días a partir de la inscripción de dispositivos |
| macOS | Todas las aplicaciones instaladas en el dispositivo | Todas las aplicaciones instaladas en el dispositivo | Cada 7 días a partir de la inscripción de dispositivos |
| Android | Solo aplicaciones administradas | Todas las aplicaciones instaladas en el dispositivo | Cada 7 días a partir de la inscripción de dispositivos |
| Android Enterprise | Solo aplicaciones administradas | Solo aplicaciones instaladas en el perfil de trabajo | Cada 7 días a partir de la inscripción de dispositivos |

El número de aplicaciones detectadas puede no coincidir con el recuento del estado de instalación de la aplicación. Estas son las posibles incoherencias:
- Un cambio de orientación de una aplicación administrada instalada puede hacer que el recuento de instalación en la hoja de estado disminuya, pero se mantenga presente en las aplicaciones detectadas.
- Dirigir varias instancias de la misma aplicación a un inquilino dará lugar a recuentos diferentes debido a la posible superposición de usuarios o dispositivos. Cada instancia de la aplicación contará los usuarios que se superponen, pero las aplicaciones detectadas tendrán recuentos duplicados.
- Las aplicaciones detectadas y los estados de la aplicación se recopilan en intervalos de tiempo diferentes, lo que podría provocar una discrepancia en los recuentos de la aplicación.

## <a name="next-steps"></a>Pasos siguientes

- [Tipos de aplicaciones en Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Supervisión de información y asignaciones de aplicaciones con Microsoft Intune](apps-monitor.md)
