---
title: Multi-factor Authentication con Azure AD | Microsoft Intune
description: "Cómo requerir Multi-factor Authentication en Azure AD para la inscripción de dispositivos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 09/22/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
translationtype: Human Translation
ms.sourcegitcommit: a7cced90c482498b5f5af424165f8dcf77b79b75
ms.openlocfilehash: ccd55cc8637ebccfdbddd05c4f6b182c7923a2ab


---

# <a name="multifactor-authentication-for-microsoft-intune"></a>Multi-factor Authentication para Windows | Microsoft Intune

Intune integra Azure AD Multi-factor Authentication (MFA) para la inscripción de dispositivos para ayudar a proteger los recursos corporativos. MFA necesita factores de autenticación como la autenticación de texto además de nombres de usuario y contraseñas. Esto se admite para iOS, Android, Windows 8.1 o posterior, o Windows Phone 8.1 o dispositivos posteriores.

> [!NOTE]
>
> En versiones anteriores de Configuration Manager (anteriores a la versión 1610), seguirán viendo la configuración de MFA en la consola de administración de Configuration Manager. No intente configurar MFA en la consola de administración de Configuration Manager, ya que no funcionará. Configure MFA como se describe en este tema.

### <a name="configuring-intune-to-require-multifactor-authentication-at-device-enrollment"></a>Configuración de Intune para requerir Multi-factor Authentication en la inscripción de dispositivos
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



<!--HONumber=Sep16_HO4-->


