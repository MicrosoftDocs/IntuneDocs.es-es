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
ms.openlocfilehash: 5783558a768e1d58087168f81ad27e5acf9aae09
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34216316"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Restablecimiento o eliminación del código de acceso de un dispositivo en Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Para crear un código de acceso para un dispositivo, use la acción **Quitar código de acceso**.

## <a name="supported-platforms"></a>Plataformas compatibles

- Dispositivos Android inscritos con un perfil de trabajo, versión 7.0 y posteriores
- Dispositivos Android en la versión 6.0 o anteriores
- iOS 
     
## <a name="unsupported-platforms"></a>Plataformas incompatibles

- Dispositivos Android inscritos con un perfil de trabajo, versión 6.0 y anteriores
- Dispositivos Android en la versión 7.0 o posteriores
- macOS
- Windows

## <a name="reset-a-passcode"></a>Restablecer un código de acceso

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** y, después, **Todos los dispositivos**.
4. En la lista de dispositivos que administra, seleccione un dispositivo y seleccione **...Más**. Luego, elija la acción remota de dispositivo **Quitar código de acceso**.

## <a name="resetting-android-for-work-passcodes"></a>Restablecer códigos de acceso de Android for Work

Los dispositivos compatibles con Android for Work reciben una nueva contraseña de desbloqueo de perfil o un desafío de perfil administrado para el usuario final. Para dispositivos Android 7.0 o posteriores con perfiles de trabajo, los usuarios finales reciben una notificación para activar su token de restablecimiento de código de acceso inmediatamente después de completar la inscripción. La notificación se muestra si hay establecida y se requiere una contraseña de perfil de trabajo. Una vez introducido el código de acceso, la notificación desaparece.

## <a name="resetting-ios-passcodes"></a>Restablecer códigos de acceso de iOS

Los códigos de acceso se quitan de los dispositivos iOS. Si hay establecida una directiva de cumplimiento de código de acceso, el dispositivo le solicitará al usuario que establezca un código de acceso nuevo en los ajustes. 

## <a name="next-steps"></a>Pasos siguientes

Para ver el estado de la acción que acaba de realizar, en **Dispositivos**, elija **Acciones de dispositivo**.
