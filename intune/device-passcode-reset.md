---
title: 'Restablecimiento de códigos de acceso de dispositivos con Microsoft Intune: Azure | Microsoft Docs'
description: Quite o restablezca el código de acceso con la acción Quitar código de acceso en dispositivos que administre o supervise con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 83a231f41f5cf9d4488e86040c2d7e141f71d0a7
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2018
ms.locfileid: "49424924"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Restablecimiento o eliminación del código de acceso de un dispositivo en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este documento se describe el restablecimiento del código de acceso tanto en el nivel del dispositivo como en el perfil de trabajo en dispositivos Android Enterprise (anteriormente conocido como Android for Work o AfW). Es importante tener en cuenta esta distinción, ya que los requisitos de cada uno pueden variar. Un restablecimiento de código de acceso de nivel de dispositivo restablece el código de acceso en todo el dispositivo. Un restablecimiento de código de acceso del perfil de trabajo restablece el código de acceso, pero solo en el perfil de trabajo del usuario en dispositivos Android Enterprise.

## <a name="supported-platforms-for-device-level-passcode-reset"></a>Plataformas compatibles con el restablecimiento del código de acceso en el nivel de dispositivo

| Plataforma | ¿Compatible? |
| ---- | ---- |
| Dispositivos Android con la versión 6 o anteriores | Sí |
| Dispositivos Android Enterprise en modo de pantalla completa | Sí |
| Dispositivos iOS | Sí |
| Dispositivos Android inscritos con un perfil de trabajo, versión 7.0 y anteriores | No |
| Dispositivos Android en la versión 7.0 o posteriores | No |
| macOS | No |
| Windows | No |

Para dispositivos Android, esto significa que el restablecimiento del código de acceso en el nivel de dispositivo solo se admite en dispositivos que ejecutan la versión 6.x o anterior, o en dispositivos Android Enterprise que se ejecutan en modo de pantalla completa. El motivo es que Google ha quitado la posibilidad de restablecer el código de acceso o la contraseña de un dispositivo Android 7 desde una aplicación otorgada por un administrador de dispositivos, y esto es aplicable a todos los proveedores MDM.

## <a name="supported-platforms-for-android-enterprise-work-profile-passcode-reset"></a>Plataformas compatibles con el restablecimiento del código de acceso del perfil de trabajo en Android Enterprise

| Plataforma | ¿Compatible? |
| ---- | ---- |
| Dispositivos Android Enterprise inscritos con un perfil de trabajo que ejecutan la versión 8.0 y posteriores | Sí |
| Dispositivos Android Enterprise inscritos con un perfil de trabajo que ejecutan la versión 7.x y anteriores | No |
| Dispositivos Android que ejecutan la versión 7.x y anteriores | No |
| iOS | No |
| macOS | No |

Para crear un nuevo código de acceso del perfil de trabajo, use la acción Restablecer el código de acceso. Esta acción solicita un restablecimiento del código de acceso y crea uno nuevo y provisional, únicamente para el perfil de trabajo. 

## <a name="reset-a-passcode"></a>Restablecer un código de acceso

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos que administra, seleccione un dispositivo y seleccione **...Más**. Luego, elija la acción remota de dispositivo **Quitar código de acceso**.

## <a name="reset-android-work-profile-passcodes"></a>Restablecer códigos de acceso de perfil de trabajo Android

Los dispositivos compatibles Android Enterprise inscritos un con perfil de trabajo reciben una nueva contraseña de desbloqueo de perfil o un desafío de perfil administrado para el usuario final.

En los dispositivos Android Enterprise versión 8.x o posterior que están inscritos con un perfil de trabajo, los usuarios finales reciben una notificación para activar el restablecimiento de código de acceso una vez completada la inscripción. La notificación se muestra si hay establecida y se requiere una contraseña de perfil de trabajo. Una vez introducido el código de acceso, la notificación desaparece.


## <a name="remove-ios-passcodes"></a>Quitar códigos de acceso de iOS

En lugar de restablecerse, los códigos de acceso se quitan de los dispositivos iOS. Si hay establecida una directiva de cumplimiento de código de acceso, el dispositivo solicitará al usuario que establezca un código de acceso nuevo en Configuración.

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en **Dispositivos**, elija **Acciones de dispositivo**.
