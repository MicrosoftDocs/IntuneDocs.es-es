---
title: 'Restablecimiento de códigos de acceso de dispositivos con Microsoft Intune: Azure | Microsoft Docs'
description: Quite o restablezca el código de acceso con la acción Quitar código de acceso en dispositivos que administre o supervise con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dd743bdb0eaf2e00c50aab85c497dd00aac773ed
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905162"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Restablecimiento o eliminación del código de acceso de un dispositivo en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para crear un código de acceso para un dispositivo, use la acción **Quitar código de acceso**.

## <a name="supported-platforms"></a>Plataformas compatibles

- Dispositivos Android inscritos con un perfil de trabajo, versión 8.0 y posteriores
- Dispositivos Android en la versión 6.0 o anteriores
- Dispositivos de quiosco de Android Enterprise
- iOS 
     
## <a name="unsupported-platforms"></a>Plataformas incompatibles

- Dispositivos Android inscritos con un perfil de trabajo, versión 7.0 y anteriores
- Dispositivos Android en la versión 7.0 o posteriores
- macOS
- Windows

## <a name="reset-a-passcode"></a>Restablecer un código de acceso

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos que administra, seleccione un dispositivo y seleccione **...Más**. Luego, elija la acción remota de dispositivo **Quitar código de acceso**.

## <a name="resetting-android-work-profile-passcodes"></a>Restablecer códigos de acceso de perfil de trabajo Android

Los dispositivos compatibles con perfiles de trabajo Android reciben una nueva contraseña de desbloqueo de perfil o un desafío de perfil administrado para el usuario final. En dispositivos de perfil de trabajo Android 8.0, los usuarios finales reciben una notificación para activar su token de restablecimiento de código de acceso justo después de que la inscripción finalice. La notificación se muestra si hay establecida y se requiere una contraseña de perfil de trabajo. Una vez introducido el código de acceso, la notificación desaparece.

## <a name="resetting-ios-passcodes"></a>Restablecer códigos de acceso de iOS

Los códigos de acceso se quitan de los dispositivos iOS. Si hay establecida una directiva de cumplimiento de código de acceso, el dispositivo solicita al usuario que establezca un código de acceso nuevo en los ajustes. 

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en **Dispositivos**, elija **Acciones de dispositivo**.
