---
title: "Restauración de dispositivos iOS administrados en Intune desde una copia de seguridad | Microsoft Intune"
description: "Proporcione instrucciones a los usuarios finales acerca de cómo volver a inscribir sus dispositivos después de restaurar desde una copia de seguridad."
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 612b0954a81de1ee8d4a1e96c7440239437dec14
ms.openlocfilehash: 5fc4423f8fd0c5829be5fe6c96949e126991e430


---

# Restauración de dispositivos iOS administrados en Intune desde una copia de seguridad

Habrá casos cuando en los que usted o sus usuarios necesiten restaurar un dispositivo iOS desde una copia de seguridad, como cuando un usuario obtiene un nuevo dispositivo. En este tema se explican los pasos adicionales que debe realizar para configurar la administración de Intune después de restaurar el dispositivo.

## Restauración de copias de seguridad en el mismo dispositivo

Si se restaura la copia de seguridad en el mismo dispositivo, también se restaurará el estado de inscripción en dicho dispositivo. No es necesario hacer nada más.

## Restauración de copias de seguridad en dispositivos diferentes

Si se restaura la copia de seguridad en un dispositivo distinto, el estado de la inscripción no se restaura automáticamente en el nuevo dispositivo. Los usuarios tienen que seguir los pasos de inscripción estándar de la aplicación Portal de empresa versión 2.1.22 o posterior para [inscribir su dispositivo iOS en Intune](/Intune/EndUser/enroll-your-device-in-intune-ios).

> [!NOTE]
> Si se dirige a los usuarios finales con directivas de acceso condicional, no podrá tener acceso al correo electrónico corporativo hasta después de volver a inscribirse.

> [!TIP]
> Una comunicación de ejemplo para los usuarios podría ser la siguiente: para inscribirse en el nuevo dispositivo, asegúrese de que la versión de la aplicación Portal de empresa es la 2.1.22 o posterior. Para comprobar la versión, abra la aplicación Portal de empresa, pulse en el botón de menú en la esquina superior derecha y, después, pulse Acerca de. Si utiliza una versión anterior, salga de la aplicación Portal de empresa y abra la tienda App Store. Pulse el botón Actualizaciones, en la esquina inferior derecha, y después pulse el botón Actualizar junto al elemento de Portal de empresa en la lista. Una vez completada la actualización, inicie la aplicación Portal de empresa e [inscriba el dispositivo iOS en Intune](/Intune/EndUser/enroll-your-device-in-intune-ios).



<!--HONumber=Oct16_HO2-->


