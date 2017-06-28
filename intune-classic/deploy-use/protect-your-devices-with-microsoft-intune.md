---
title: Proteger dispositivos con Microsoft Intune
description: "Obtenga información acerca de algunas de las maneras en que Intune puede ayudarle a proteger los dispositivos contra accesos no autorizados y otras amenazas."
keywords: 
author: Robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 8acde93c1c0c0d3bf443daf61d5f8d75b3d061df
ms.contentlocale: es-es
ms.lasthandoff: 06/08/2017


---

# <a name="protect-devices-with-microsoft-intune"></a>Proteger dispositivos con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune le ofrece un conjunto de capacidades para que pueda proteger los dispositivos que administra y los datos almacenados en dichos dispositivos. Lea este tema para aprender los conceptos básicos de estas capacidades y descubrir cómo obtener más información.

## <a name="general-ways-to-protect-all-devices"></a>Métodos generales para proteger todos los dispositivos

### <a name="device-configuration"></a>Configuración de los dispositivos
Gracias a las [directivas de configuración](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) de Intune puede proteger y configurar dispositivos controlando una gran variedad de opciones y características. Por ejemplo:
- Puede restringir el uso de las características de hardware en el dispositivo, como la cámara o el Bluetooth.
- Puede configurar aplicaciones conformes y no conformes. Se le avisará si se instala una aplicación no conforme (de hecho, algunas plataformas pueden bloquear la instalación).

### <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>Restablecer códigos de acceso cuando los usuarios quedan bloqueados fuera de sus dispositivos
Dado que el primer paso para proteger los datos empresariales en dispositivos móviles es exigir un código de acceso para usar el dispositivo, a veces será necesario [restablecer un código de acceso](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) o ayudar a un empleado a hacerlo, ya sea quitando el código de acceso o estableciendo uno temporal de forma remota. También puede [bloquear un dispositivo de forma remota](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) si se pierde o es robado.

### <a name="retire-devices-and-remove-data"></a>Retirar dispositivos y quitar datos
Cuando un dispositivo se debe [quitar de la administración de Intune](retire-devices-from-microsoft-intune-management.md) (por ejemplo, porque un usuario se ha ido o se ha perdido o robado el dispositivo), es probable que quiera quitar los datos de dicho dispositivo. Intune proporciona una serie de métodos para garantizar que los datos de su empresa siguen estando protegidos.

### <a name="require-devices-to-be-compliant"></a>Requerir que los dispositivos sean conformes
Intune cuenta con [directivas de conformidad de dispositivos](introduction-to-device-compliance-policies-in-microsoft-intune.md), que le permiten evaluar (y, en algunos casos, corregir) aquellos dispositivos que no se ajustan a las reglas especificadas. Por ejemplo, puede notificar la existencia de dispositivos iOS con Jailbreak, si los dispositivos están cifrados o si el servicio de atestación de mantenimiento ha notificado que el estado de los dispositivos con Windows 10 es correcto.

### <a name="protect-apps-and-the-data-they-use"></a>Proteger las aplicaciones y los datos que usan
Intune le ofrece una serie de características que le ayudan a proteger las aplicaciones y sus datos. Por ejemplo, las directivas de administración de aplicaciones móviles (MAM) pueden impedir que se haga una copia de seguridad de los datos desde una aplicación protegida, restringir la acción de copiar y pegar a otras aplicaciones, pedir un PIN para obtener acceso a una aplicación, etc. Para obtener más información sobre cómo proteger las aplicaciones, consulte [Proteger aplicaciones y datos con Microsoft Intune](protect-apps-and-data-with-microsoft-intune.md)

### <a name="add-an-additional-layer-of-protection-to-devices"></a>Agregar una capa adicional de protección a dispositivos
La [autenticación multifactor (MFA)](multi-factor-authentication-azure-active-directory.md) es una forma más segura de autenticar a los usuarios de dispositivos en la red.  Con MFA, los usuarios deben confirmar su identidad, más allá del nombre de usuario y la contraseña, mediante una llamada de teléfono o un mensaje de texto.

## <a name="further-capabilities-for-windows-devices"></a>Otras capacidades para dispositivos Windows

### <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>Controlar la configuración de Windows Hello para empresas en los dispositivos Windows
Intune permite la integración con [Windows Hello para empresas](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) (anteriormente denominado Microsoft Passport), que es un método alternativo de inicio de sesión para Windows 10 y versiones posteriores que usa Active Directory o una cuenta de Azure Active Directory para reemplazar una contraseña, una tarjeta inteligente o una tarjeta inteligente virtual.

## <a name="further-capabilities-for-ios-devices"></a>Otras capacidades para dispositivos iOS

### <a name="bypass-activation-lock-on-ios-devices"></a>Realizar el bypass del bloqueo de activación en dispositivos iOS
El bloqueo de activación es una característica que sirve para proteger los dispositivos de los usuarios, para lo cual deben especificar su identificador de Apple y la contraseña antes de poder borrar o volver a activar el dispositivo. Pero esto puede provocar problemas, por ejemplo, si el usuario deja la empresa sin quitar el bloqueo. El [bypass del bloqueo de activación de iOS](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) sirve para quitar el bloqueo de los dispositivos iOS supervisados, de forma que pueda reasignarlos o borrarlos.



## <a name="protect-windows-pcs-managed-with-the-intune-client"></a>Proteger equipos Windows administrados con el cliente de Intune
Intune sigue siendo compatible con las directivas de seguridad para equipos Windows que no se inscriben, sino que se administran con el software cliente de equipo de Intune. Para averiguar cómo pueden ayudar estas directivas a proteger los equipos Windows, consulte [Use policies to help protect Windows PCs that run the Intune client software](policies-to-protect-windows-pcs-in-microsoft-intune.md) (Usar directivas para ayudar a proteger equipos Windows que ejecutan el software cliente de Intune).

