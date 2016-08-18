---
title: Proteger dispositivos | Microsoft Intune
description: "Obtenga información acerca de algunas de las maneras en que Intune puede ayudarle a proteger los dispositivos contra accesos no autorizados y otras amenazas."
keywords: 
author: Robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c999a852b68762002ac94269e27ecbf46c8f9999
ms.openlocfilehash: 3318590eaedc6f0e96fb463dc016d5786eeb38fb


---

# Proteger dispositivos con Microsoft Intune
Una vez que los dispositivos estén administrados por Intune, querrá asegurarse de que están protegidos frente al acceso no autorizado y otras amenazas. Estas son algunas de las funcionalidades de Intune que ayudan a lograr estos objetivos.

> [!TIP]
> Este tema no contiene todas las formas en que Intune puede ayudar a proteger los dispositivos. Por ejemplo, puede usar directivas de Intune para configurar muchas opciones de seguridad para los dispositivos, como la configuración de contraseñas y cifrado, así como características de hardware, como Bluetooth y la cámara del dispositivo. Consulte [Manage settings and features on your devices with Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) (Administrar la configuración y las características de los dispositivos con Microsoft Intune) para obtener más información sobre estas opciones.

## Restablecer códigos de acceso cuando los usuarios quedan bloqueados fuera de sus dispositivos
El primer paso para proteger los datos corporativos en dispositivos móviles consiste en solicitar una contraseña para usar el dispositivo. En ocasiones tendrá que [restablecer una contraseña](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) o ayudar a un empleado a hacerlo, ya sea eliminando la contraseña o estableciendo un código de acceso temporal de forma remota. También puede [bloquear un dispositivo de forma remota](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) si se pierde o es robado.

## Agregar una capa adicional de protección en dispositivos Windows
[Multi-Factor Authentication (MFA)](protect-windows-devices-with-multi-factor-authentication.md) es una forma más segura de autenticar a los usuarios de dispositivos Windows y Windows Phone en la red. Con MFA, los usuarios deben confirmar su identidad, más allá del nombre de usuario y la contraseña, a través de una llamada de teléfono o un mensaje de texto.

## Controlar la configuración de Microsoft Passport en dispositivos Windows
Intune permite la integración con [Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), que es un método alternativo de inicio de sesión para Windows 10 y versiones posteriores. Microsoft Passport for Work usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual.

## Realizar el bypass del bloqueo de activación en dispositivos iOS
El bloqueo de activación es una característica que sirve para proteger los dispositivos de los usuarios, para lo cual se requiere que especifiquen su identificador de Apple y la contraseña antes de poder borrar o volver a activar el dispositivo. Pero esto puede provocar problemas, por ejemplo, si el usuario deja la empresa sin quitar el bloqueo. El [bypass del bloqueo de activación de iOS](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) sirve para quitar el bloqueo de los dispositivos iOS supervisados, de forma que pueda reasignarlos o borrarlos.

## Proteger equipos Windows administrados con el cliente de Intune
Intune sigue siendo compatible con las directivas de seguridad para equipos Windows que no se inscriben, sino que se administran con el software cliente de equipo de Intune. Para averiguar cómo pueden ayudar estas directivas a proteger los equipos Windows, consulte [Use policies to help protect Windows PCs that run the Intune client software](policies-to-protect-windows-pcs-in-microsoft-intune.md) (Usar directivas para ayudar a proteger equipos Windows que ejecutan el software cliente de Intune).



<!--HONumber=Aug16_HO2-->


