---
title: Autenticación multifactor para la inscripciones de dispositivos de Intune
description: Cómo requerir Multi-factor Authentication en Azure AD para la inscripción de dispositivos.
keywords: ''
author: dougeby
ms.author: angrobe
manager: angerobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: 62568a307b5e28c9543a8bb73271da2f55c44ae4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31014136"
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Autenticación multifactor para inscripciones de dispositivos de Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune integra Azure AD Multi-factor Authentication (MFA) para la inscripción de dispositivos para ayudar a proteger los recursos corporativos.

MFA funciona pidiendo dos o más de los métodos de verificación siguientes: 

- Algo que usted sabe (generalmente una contraseña o PIN).
- Algo que usted tiene (un dispositivo de confianza que no se puede duplicar fácilmente, como un teléfono).
- Algo que usted es (biométrica).

MFA se admite para iOS, Android, Windows 8.1 o versiones posteriores, o Windows Phone 8.1 o dispositivos posteriores.

> [!NOTE]
> En versiones anteriores de Configuration Manager (anteriores a la versión 1610), seguirán viendo la configuración de MFA en la consola de administración de Configuration Manager. No intente configurar MFA en la consola de administración de Configuration Manager, ya que no funcionará. Configure MFA como se describe en este tema.

### <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configurar Intune para requerir Multi-Factor Authentication en la inscripción de dispositivos
Para requerir MFA cuando se inscribe un dispositivo, siga estos pasos:

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
