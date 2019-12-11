---
title: Administrar versiones de sistemas operativos con Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo administrar versiones de sistemas operativos en plataformas con Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 361ef17b-1ee0-4879-b7b1-d678b0787f5a
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 681b4f690d03cd21c5a430e02cb0f3584d2e680e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72510121"
---
# <a name="manage-operating-system-versions-with-intune"></a>Administrar versiones de sistemas operativos con Intune
En las plataformas modernas de ordenadores y dispositivos móviles, podrá implementar rápidamente actualizaciones principales, revisiones y nuevas versiones. Tiene controles para administrar completamente las actualizaciones y revisiones en Windows, pero otras plataformas, como iOS y Android, requieren que los usuarios finales participen en el proceso.  Microsoft Intune tiene las capacidades para ayudarle a estructurar la administración de versiones del sistema operativo en diferentes plataformas.

Intune puede ayudarle a resolver estos escenarios comunes: 
- Determinar qué sistema operativo se ejecuta en los dispositivos de los usuarios finales
- Controlar el acceso a datos de la organización desde dispositivos mientras se valida una nueva versión del sistema operativo
- Inducir/requerir a los usuarios finales que actualicen la versión del sistema operativo a la más reciente aprobada por su organización
- Administrar el lanzamiento de una nueva versión del sistema operativo para toda la organización
  
## <a name="operating-system-version-control-using-intune-mobile-device-management-mdm-enrollment-restrictions"></a>Control de la versión del sistema operativo mediante las restricciones de inscripción de la administración de dispositivos móviles (MDM) de Intune
Las restricciones de inscripción de MDM de Intune le permiten definir los requisitos del dispositivo del cliente antes de permitir la inscripción del dispositivo. El objetivo es requerir que los usuarios finales inscriban solamente dispositivos compatibles para poder obtener acceso a los recursos de la organización. Los requisitos del dispositivo incluyen tanto las versiones del sistema operativo mínimas como las máximas admitidas para las plataformas compatibles.

![Hoja de restricciones en la configuración de la plataforma](./media/manage-os-versions/os-version-platform-configurations.png)

### <a name="in-practice"></a>A la práctica

Las organizaciones usan restricciones según el tipo de dispositivo para controlar el acceso a los recursos de la organización mediante las siguientes opciones de configuración:

1. Usar la versión mínima del sistema operativo para que los usuarios finales usen plataformas actuales y compatibles en su organización.
2. No especificar la versión máxima del sistema operativo (sin límite) o establecerlo en la última versión validada en su organización para dar tiempo a que se prueben internamente las nuevas versiones del sistema operativo.

Para obtener información, consulte [Establecer restricciones de tipo de dispositivo](../enrollment/enrollment-restrictions-set.md#create-a-device-type-restriction).

## <a name="operating-system-version-reporting-and-compliance-with-intune-mdm-device-compliance-policies"></a>Informes de la versión del sistema operativo y cumplimiento de las directivas de cumplimiento de dispositivos de MDM de Intune

Las directivas de cumplimiento de dispositivos MDM de Intune proporcionan las siguientes herramientas:

- Especificar reglas de cumplimiento
- Ver el estado de cumplimiento mediante informes
- Actuar sobre los dispositivos no compatibles poniendo el dispositivo en cuarentena y ofreciéndole un acceso condicional

Igual que las restricciones de inscripción, las directivas de cumplimiento de dispositivos incluyen tanto la versión mínima como la máxima del sistema operativo. Las directivas también tienen una escala de tiempo de cumplimiento para ofrecer a los usuarios un período de gracia para cumplir con la directiva. Las directivas de cumplimiento del dispositivo hacen que los dispositivos de los usuarios finales inscritos cumplan con la directiva de la organización.

![Cumplimiento de dispositivos: acciones para dispositivos no compatibles](./media/manage-os-versions/os-version-actions-noncompliance.png)

### <a name="in-practice"></a>A la práctica
Las organizaciones usan las directivas de cumplimiento de dispositivos en los mismos escenarios que las restricciones de inscripción. Estas directivas hacen que los usuarios usen versiones actuales y validadas del sistema operativo en su organización. Si los dispositivos de los usuarios finales no cumplen las directivas, se puede bloquear el acceso a recursos de la organización mediante un acceso condicional hasta que los usuarios finales estén dentro del rango del sistema operativo compatible para su organización. A los usuarios finales se les informa de que no están cumpliendo con la directiva y se les explican los pasos para volver a obtener acceso.   

Para obtener información, consulte [Introducción a las directivas de cumplimiento de dispositivos](../protect/device-compliance-get-started.md).
 
## <a name="operating-system-version-controls-using-intune-app-protection-policies"></a>Controles de la versión del sistema operativo mediante directivas de protección de aplicaciones de Intune    
Las directivas de protección de aplicaciones de Intune y la configuración de acceso a la administración de aplicaciones móviles (MAM) le permiten especificar la versión mínima del sistema operativo en el nivel de aplicación. Esto le permite informar a los usuarios finales de que pueden actualizar su sistema operativo a una versión mínima especificada y fomentar o requerirles que lo hagan.
 
Tiene dos opciones: 
- **Advertencia**: con la advertencia, se informa al usuario final de que debería actualizar la versión si abre una aplicación con una directiva de protección de aplicaciones o una configuración de acceso de MAM en un dispositivo con una versión de sistema operativo inferior a la especificada. Se permite el acceso a la aplicación y a los datos de la organización.
  ![Imagen del cuadro de diálogo de advertencia de actualización de Android](./media/manage-os-versions/os-version-update-warning.png) 

- **Bloqueo**: con el bloqueo, se informa al usuario final de que debe actualizar la versión si abre una aplicación con una directiva de protección de aplicaciones o una configuración de acceso de MAM en un dispositivo con una versión de sistema operativo inferior a la especificada. No se permite el acceso a la aplicación ni a los datos de la organización.
  ![Imagen del cuadro de diálogo de bloqueo del acceso a la aplicación](./media/manage-os-versions/os-version-access-blocked.png)

### <a name="in-practice"></a>A la práctica
Al abrir o reanudar aplicaciones, las organizaciones usan la configuración de la directiva de protección de aplicaciones para explicar a los usuarios finales la necesidad de mantener las aplicaciones actualizadas. Por ejemplo, se podría establecer una configuración en la que a los usuarios finales se les advirtiera cuando estuvieran usando la versión actual menos uno y se les bloqueara cuando usaran la versión actual menos dos.
 
Para obtener información, consulte [Creación y asignación de directivas de protección de aplicaciones](../apps/app-protection-policies.md).

## <a name="managing-a-new-operating-system-version-rollout"></a>Administrar el lanzamiento de una versión de sistema operativo
Puede usar las capacidades de Intune que se describen en este artículo para implementar una nueva versión de sistema operativo en su organización en la escala de tiempo que defina. En los pasos siguientes se ofrece un modelo de implementación de muestra para hacer que los usuarios de la versión 1 del sistema operativo pasen a la versión 2 en un plazo de siete días.
- **Paso 1**: use las restricciones de lanzamiento para requerir la versión 2 del sistema operativo como versión mínima para inscribir el dispositivo. Esto garantiza que los dispositivos de los usuarios finales nuevos cumplan los requisitos a la hora de realizar la inscripción.
- **Paso 2a**: use las directivas de protección de aplicaciones de Intune para advertir a los usuarios de que se requiere la versión 2 del sistema operativo cuando la aplicación se abra o reanude.
- **Paso 2b**: use las directivas de cumplimiento de dispositivos para requerir la versión 2 del sistema operativo como versión mínima para que un dispositivo cumpla los requisitos. En los casos en que no se cumplan los requisitos, use **Acciones** para conceder un período de gracia de siete días y enviar una notificación por correo electrónico a los usuarios finales con la escala de tiempo y los requisitos.
  - En estas directivas se informará a los usuarios finales de que los dispositivos existentes deben actualizarse por correo electrónico, a través del Portal de empresa de Intune y, si la aplicación está abierta y tiene la función habilitada, con una directiva de protección de aplicaciones.
  - Puede ejecutar un informe de cumplimiento para identificar a los usuarios que no cumplan los requisitos. 
- **Paso 3a**: use las directivas de protección de aplicaciones de Intune para bloquear a los usuarios que usen un dispositivo en el que no se esté ejecutando la versión 2 del sistema operativo cuando se abra o reanude una aplicación.
- **Paso 3b**: use las directivas de cumplimiento de dispositivos para requerir la versión 2 del sistema operativo como versión mínima para que un dispositivo cumpla los requisitos.
  - Estas directivas requieren que los dispositivos estén actualizados para seguir teniendo acceso a datos de la organización. Los servicios protegidos se bloquean cuando se usan con acceso condicional al dispositivo. Las aplicaciones que disponen de una directiva de protección de aplicaciones se bloquean cuando se abren o cuando acceden a datos de la organización.

## <a name="next-steps"></a>Pasos siguientes

Use los siguientes recursos para administrar las versiones del sistema operativo en su organización:

- [Establecer restricciones de tipo de dispositivo](../enrollment/enrollment-restrictions-set.md#create-a-device-type-restriction)
- [Introducción al cumplimiento de dispositivos](../protect/device-compliance-get-started.md)
- [Creación y asignación de directivas de protección de aplicaciones](../apps/app-protection-policies.md)
