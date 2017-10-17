---
title: "Implementación de directivas y aplicaciones"
description: "Tan pronto como los dispositivos se inscriban en la administración, puede habilitar la configuración de directivas e implementar las aplicaciones a las que se aplicarán."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d0a0a3670388ec95cff86b09ea81661a0825ba83
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="create-policies-and-publish-apps"></a>Crear directivas y publicar aplicaciones

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

En este tema se explica a los administradores de Intune cómo crear directivas y publicar aplicaciones que luego pueden implementar en dispositivos administrados.

Antes de comenzar a inscribir aplicaciones en Intune, puede habilitar la configuración de directivas y las aplicaciones que se implementarán en cuanto dichos dispositivos se inscriban en la administración. Las directivas de Intune proporcionan una configuración con la que es más fácil: controlar la configuración de seguridad en dispositivos móviles, mantener la configuración de Firewall de Windows y Endpoint Protection de los equipos e implementar aplicaciones. Puede configurar directivas, agregar aplicaciones e implementar esas aplicaciones para que los dispositivos reciban la configuración y las aplicaciones en cuanto se inscriban en Intune.

Las directivas y las aplicaciones son específicas de la plataforma.

## <a name="manage-device-settings"></a>Administrar la configuración del dispositivo

 La configuración de las directivas de dispositivo se realiza y administra por plataforma. En los siguientes vínculos se proporcionan listas de opciones de configuración disponibles para sus respectivas plataformas:

- [iOS](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)
- [Android y Samsung KNOX Standard](/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune)
- [Android for Work](/intune-classic/deploy-use/android-for-work-policy-settings-in-microsoft-intune)
- [Windows 10 (PC y móvil)](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)
- [Windows 8.1](/intune-classic/deploy-use/windows-configuration-policy-settings-in-microsoft-intune)
- [Windows Phone 8.1](/intune-classic/deploy-use/windows-phone-8-1-policy-settings-in-microsoft-intune)
- [Equipo de Windows](/intune-classic/deploy-use/windows-team-configuration-policy-settings-in-microsoft-intune)
- [Equipos Windows que ejecutan el software cliente de Intune](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)

Puede aprender más sobre cómo [administrar la configuración y las características de sus dispositivos con directivas de Microsoft Intune](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).

## <a name="add-and-deploy-apps"></a>Agregar e implementar aplicaciones

Puede agregar aplicaciones a Intune y luego implementarlas en dispositivos administrados de dos maneras:
- **Instalación requerida**: las aplicaciones se instalan automáticamente en dispositivos administrados.
- **Instalación disponible**: las aplicaciones aparecen en el Portal de empresa de Intune para que los usuarios puedan elegir si instalarlas en sus dispositivos.

### <a name="add-apps"></a>Agregar aplicaciones

En primer lugar debe hacer que las aplicaciones estén disponibles en Intune mediante uno de los siguientes métodos:
- [Agregar aplicaciones a los dispositivos inscritos](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)
- [Agregar aplicaciones para equipos cliente de software Intune](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)

### <a name="deploy-apps"></a>Implementación de aplicaciones

Ahora que la aplicación está disponible en Intune, puede implementarla en dispositivos administrados:
- [Implementar aplicaciones en dispositivos](/intune-classic/deploy-use/deploy-use/deploy-apps-in-microsoft-intune)
- Implementar aplicaciones adquiridas por volumen:
    - [iOS: programa de adquisición por volumen](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)
    - [Tienda Microsoft para Empresas](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)
    - [Android for Work](/intune-classic/deploy-use/android-for-work-apps)

    Una vez configuradas las aplicaciones para la implementación, puede [configurar aplicaciones](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune).

>[!div class="step-by-step"]

>[&larr; **Organizar usuarios y dispositivos**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)      [**Personalizar el portal de empresa** &rarr;](/intune/company-portal-customize)  
