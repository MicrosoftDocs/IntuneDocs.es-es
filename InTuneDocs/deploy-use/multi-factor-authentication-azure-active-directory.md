---
title: Multi-factor Authentication con Azure AD | Microsoft Docs
description: "Cómo requerir Multi-factor Authentication en Azure AD para la inscripción de dispositivos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 12/12/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: 
translationtype: Human Translation
ms.sourcegitcommit: 85462d6cb5e3dc6ce8e94fe8fd1bc1c1c2b6e4f3
ms.openlocfilehash: 6e20eca60886781ae884107a224245639c5f107c


---

# <a name="multi-factor-authentication-for-microsoft-intune"></a>Multi-factor Authentication para Windows | Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune integra Azure AD Multi-factor Authentication (MFA) para la inscripción de dispositivos para ayudar a proteger los recursos corporativos. MFA necesita factores de autenticación como la autenticación de texto además de nombres de usuario y contraseñas. Esto se admite para iOS, Android, Windows 8.1 o posterior, o Windows Phone 8.1 o dispositivos posteriores.

> [!NOTE]
>
> Esta es la nueva experiencia de MFA en Intune. La experiencia anterior, desde la que se migran los clientes, se describe en [Proteger dispositivos Windows con Multi-factor Authentication](protect-windows-devices-with-multi-factor-authentication.md).
>
> En versiones anteriores de Configuration Manager (anteriores a la versión 1610), seguirán viendo la configuración de MFA en la consola de administración de Configuration Manager. No intente configurar MFA en la consola de administración de Configuration Manager, ya que no funcionará. Configure MFA como se describe en este tema.

### <a name="configuring-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configuración de Intune para requerir Multi-factor Authentication en la inscripción de dispositivos
Para requerir MFA en la inscripción de dispositivos, siga estos pasos:

1. Inicie sesión en el [portal de Microsoft Azure](https://manage.windowsazure.com) con sus credenciales de administrador.
2. Elija el inquilino.
2. Seleccione la pestaña **Aplicaciones**. Verá una lista de servicios para los que puede configurar las funciones de seguridad de Azure AD.
3. Elija **Inscripción a Microsoft Intune**.
4. Elija **Configurar**. 
5. En **Multi-factor Authentication y las reglas de acceso basado en la ubicación**, puede:
    
    -  Habilitar las reglas de acceso
    -  Elegir si desea aplicar las reglas a todos los usuarios o a grupos de seguridad de Azure AD específicos.
    -  Requerir Multi-factor Authentication para la inscripción de todos los dispositivos.
    -  Requerir Multi-factor Authentication para la inscripción cuando el dispositivo no esté en el trabajo.
    -  Seleccione **Bloquear el acceso a los recursos corporativos** para evitar la inscripción de un dispositivo cuando no está conectado a la red corporativa. 
4. También puede hacer clic en el vínculo para **definir o modificar la ubicación de red de trabajo**, para configurar los requisitos de conectividad de red para la inscripción del dispositivo.

> [!IMPORTANT]
> 
> No configure **Dispositivo según las reglas de acceso** para la inscripción de Intune de Microsoft.



<!--HONumber=Dec16_HO3-->


