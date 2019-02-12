---
title: Proteger dispositivos con Microsoft Intune
titleSuffix: Microsoft Intune
description: Obtenga información acerca de algunas de las maneras en que Intune puede ayudarle a proteger los dispositivos contra accesos no autorizados y otras amenazas.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5743e1d24e878a84413c23c8309cda2ab0dda90
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55844486"
---
# <a name="protect-devices-with-microsoft-intune"></a>Proteger dispositivos con Microsoft Intune

Microsoft Intune le ayuda a proteger los dispositivos que administra y los datos almacenados en dichos dispositivos.

## <a name="device-configuration"></a>Configuración de los dispositivos
Gracias a las [directivas de configuración](device-profiles.md) de Intune puede proteger y configurar dispositivos controlando una gran variedad de opciones y características. Por ejemplo:
- Puede restringir el uso de las características de hardware en el dispositivo, como la cámara o el Bluetooth.
- Puede configurar aplicaciones conformes y no conformes. Recibirá una alerta si se instala una aplicación no conforme (de hecho, algunas plataformas pueden bloquear la instalación).

## <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>Restablecer códigos de acceso cuando los usuarios quedan bloqueados fuera de sus dispositivos
Dado que el primer paso para proteger los datos empresariales en dispositivos móviles es exigir un código de acceso para usar el dispositivo, a veces será necesario [restablecer un código de acceso](device-passcode-reset.md) o ayudar a un empleado a hacerlo, ya sea quitando el código de acceso o estableciendo uno temporal de forma remota. También puede [bloquear un dispositivo de forma remota](device-remote-lock.md) si se pierde o lo roban.

## <a name="retire-devices-and-remove-data"></a>Retirar dispositivos y quitar datos
Cuando un dispositivo se debe [quitar de la administración de Intune](devices-wipe.md) (por ejemplo, porque un usuario se ha ido o se ha perdido o robado el dispositivo), es probable que quiera quitar los datos de dicho dispositivo. Intune proporciona una serie de métodos para garantizar que los datos de su empresa sigan estando protegidos.

## <a name="require-devices-to-be-compliant"></a>Requerir que los dispositivos sean conformes
Intune cuenta con [directivas de conformidad de dispositivos](device-compliance-get-started.md), que le permiten evaluar (y, en algunos casos, corregir) aquellos dispositivos que no se ajustan a las reglas especificadas. Por ejemplo, puede obtener informes sobre:
- dispositivos iOS JailBroken
- dispositivos cifrados o no cifrados
- el estado de los dispositivos Windows 10 (según lo determinado por el servicio de atestación de estado).

## <a name="protect-apps-and-the-data-they-use"></a>Proteger las aplicaciones y los datos que usan
Intune le ofrece una serie de características que le ayudan a proteger las aplicaciones y sus datos. Por ejemplo, las directivas de administración de aplicaciones móviles (MAM) pueden:
- evitar que se haga una copia de seguridad de los datos desde una aplicación protegida
- restringir copiar y pegar en otras aplicaciones
- requerir un PIN para tener acceso a una aplicación. Para obtener más información, consulte [Proteger aplicaciones y datos con Microsoft Intune](app-protection-policy.md)

## <a name="add-an-additional-layer-of-protection-to-devices"></a>Agregar una capa adicional de protección a dispositivos
La [autenticación multifactor (MFA)](multi-factor-authentication.md) es una forma más segura de autenticar a los usuarios de dispositivos en la red.  Con MFA, los usuarios deben confirmar su identidad, más allá del nombre de usuario y la contraseña, mediante una llamada de teléfono o un mensaje de texto.

## <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>Controlar la configuración de Windows Hello para empresas en los dispositivos Windows
Intune permite la integración con [Windows Hello para empresas](windows-hello.md), que es un método alternativo de inicio de sesión para Windows 10 y versiones posteriores que usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual.

## <a name="bypass-activation-lock-on-ios-devices"></a>Realizar el bypass del bloqueo de activación en dispositivos iOS
Bloqueo de activación es una característica que ayuda a proteger los dispositivos de los usuarios. La característica requiere que los usuarios escriban su identificador de Apple y su contraseña antes de que alguien pueda borrar o reactivar el dispositivo. Pero esta característica puede provocar problemas, por ejemplo, si el usuario deja la empresa sin quitar el bloqueo. El [bypass del bloqueo de activación de iOS]( device-activation-lock-bypass.md) sirve para quitar el bloqueo de los dispositivos iOS supervisados, de forma que pueda reasignarlos o borrarlos.

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre [Mobile Threat Defense](mobile-threat-defense.md)


