---
title: "Restauración de dispositivos iOS administrados en Intune desde una copia de seguridad"
description: "Proporcione instrucciones a los usuarios finales acerca de cómo volver a inscribir sus dispositivos después de restaurar desde una copia de seguridad."
keywords: "restauración, administrados, iOS"
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2270e19ab2f45d7f3636226709b8a0fbea075ed0
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="restore-intune-managed-ios-devices-from-backup"></a>Restauración de dispositivos iOS administrados en Intune desde una copia de seguridad

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Habrá casos cuando en los que usted o sus usuarios necesiten restaurar un dispositivo iOS desde una copia de seguridad, como cuando un usuario obtiene un nuevo dispositivo. En este tema se explican los pasos adicionales que debe realizar para configurar la administración de Intune después de restaurar el dispositivo.

## <a name="restoring-backups-onto-the-same-device"></a>Restauración de copias de seguridad en el mismo dispositivo

Si se restaura la copia de seguridad en el mismo dispositivo, también se restaurará el estado de inscripción en dicho dispositivo. No es necesario hacer nada más.

## <a name="restoring-backups-onto-different-devices"></a>Restauración de copias de seguridad en dispositivos diferentes

Si se restaura la copia de seguridad en un dispositivo distinto, el estado de la inscripción no se restaura automáticamente en el nuevo dispositivo. Los usuarios tienen que seguir los pasos de inscripción estándar de la aplicación Portal de empresa versión 2.1.22 o posterior para [inscribir su dispositivo iOS en Intune](/intune-user-help/enroll-your-device-in-intune-ios).

> [!NOTE]
> Si se dirige a los usuarios finales con directivas de acceso condicional, no podrá tener acceso al correo electrónico corporativo hasta después de volver a inscribirse.

> [!TIP]
> Una comunicación de ejemplo para los usuarios podría ser la siguiente: para inscribirse en el nuevo dispositivo, asegúrese de que la versión de la aplicación Portal de empresa es la 2.1.22 o posterior. Para comprobar la versión, abra la aplicación Portal de empresa, pulse en el botón de menú en la esquina superior derecha y, después, pulse Acerca de. Si utiliza una versión anterior, salga de la aplicación Portal de empresa y abra la tienda App Store. Pulse el botón Actualizaciones, en la esquina inferior derecha, y después pulse el botón Actualizar junto al elemento de Portal de empresa en la lista. Una vez completada la actualización, inicie la aplicación Portal de empresa e [inscriba el dispositivo iOS en Intune](/intune-user-help/enroll-your-device-in-intune-ios).

## <a name="resolving-known-issues-with-restores"></a>Solución de problemas conocidos mediante restauraciones

Es posible que los usuarios experimenten alguna dificultad si restauraron el dispositivo e iniciaron la aplicación Portal de empresa con la versión 2.1.21 o anterior de Portal de empresa aún instalada. Estos problemas pueden resolverse con los pasos adecuados para la situación del usuario.

### <a name="for-users-who-will-only-use-their-new-device"></a>Para usuarios que solo van a usar su nuevo dispositivo
Inicie la aplicación Portal de empresa, seleccione el icono del dispositivo actual y pulse en el botón __Quitar__ para anular la inscripción. Después de quitar, siga los pasos de inscripción estándar para [inscribir un dispositivo iOS en Intune](/intune-user-help/enroll-your-device-in-intune-ios).

### <a name="for-users-who-will-use-both-their-old-and-new-devices"></a>Para usuarios que van a usar el dispositivo antiguo y el nuevo
Pulse en __Configuración__ > __Safari__ > __Borrar historial y datos de sitios web__ para borrar las cookies de Safari. Después de borrar, desinstale y vuelva a instalar la aplicación Portal de empresa y siga los pasos de inscripción estándar para [inscribir un dispositivo iOS en Intune](/intune-user-help/enroll-your-device-in-intune-ios).
