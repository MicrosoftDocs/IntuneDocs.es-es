---
title: Implementar directivas y aplicaciones | Microsoft Intune
description: "Tan pronto como los dispositivos se inscriban en la administración, puede habilitar la configuración de directivas e implementar las aplicaciones a las que se aplicarán."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 56f7d1578ba6b193c6547686675e0fd4fde5f378


---

# <a name="create-policies-and-publish-apps"></a>Crear directivas y publicar aplicaciones
Antes de comenzar a inscribir aplicaciones en Intune, puede habilitar la configuración de directivas y las aplicaciones que se implementarán en cuanto dichos dispositivos se inscriban en la administración. Las directivas de Intune proporcionan una configuración con la que es más fácil: controlar la configuración de seguridad en dispositivos móviles, mantener la configuración de Firewall de Windows y Endpoint Protection de los equipos e implementar aplicaciones. Puede configurar directivas, agregar aplicaciones e implementar esas aplicaciones para que los dispositivos reciban la configuración y las aplicaciones en cuanto se inscriban en Intune.

Las directivas y las aplicaciones son específicas de la plataforma.

## <a name="manage-device-settings"></a>Administrar la configuración del dispositivo

 La configuración de las directivas de dispositivo se realiza y administra por plataforma. Puede configurar directivas para las siguientes plataformas:

- [iOS](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
- [Android y Samsung KNOX Standard](https://docs.microsoft.com/intune/deploy-use/android-policy-settings-in-microsoft-intune)
- [Android for Work](https://docs.microsoft.com/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)
- [Windows 10 (PC y móvil)](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)
- [Windows 8.1](https://docs.microsoft.com/intune/deploy-use/windows-configuration-policy-settings-in-microsoft-intune)
- [Windows Phone 8.1](https://docs.microsoft.com/intune/deploy-use/windows-phone-8-1-policy-settings-in-microsoft-intune)
- [Equipo de Windows](https://docs.microsoft.com/intune/deploy-use/windows-team-configuration-policy-settings-in-microsoft-intune)
- [Equipos Windows que ejecutan el software cliente de Intune](https://docs.microsoft.com/intune/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)

Puede aprender más sobre cómo [administrar la configuración y las características de sus dispositivos con directivas de Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).

## <a name="add-and-deploy-apps"></a>Agregar e implementar aplicaciones

Puede agregar aplicaciones a Intune y luego implementarlas en dispositivos administrados de dos maneras:
- **Instalación requerida**: las aplicaciones se instalan automáticamente en dispositivos administrados.
- **Instalación disponible**: las aplicaciones aparecen en el Portal de empresa de Intune para que los usuarios puedan elegir si instalarlas en sus dispositivos.

### <a name="add-apps"></a>Agregar aplicaciones

En primer lugar debe hacer que las aplicaciones estén disponibles en Intune mediante uno de los siguientes métodos:
- [Agregar aplicaciones a los dispositivos inscritos](https://docs.microsoft.com/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)
- [Agregar aplicaciones para equipos cliente de software Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)

### <a name="deploy-apps"></a>Implementación de aplicaciones

Ahora que la aplicación está disponible en Intune, puede implementarla en dispositivos administrados:
- [Implementar aplicaciones en dispositivos](https://docs.microsoft.com/intune/deploy-use/deploy-use/deploy-apps-in-microsoft-intune)
- Implementar aplicaciones adquiridas por volumen:
    - [iOS: programa de adquisición por volumen](https://docs.microsoft.com/intune/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)
    - [Tienda Windows para la Empresa](https://docs.microsoft.com/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)
    - [Android for Work](https://docs.microsoft.com/en-us/Intune/deploy-use/android-for-work-apps)

    Una vez configuradas las aplicaciones para la implementación, puede [configurar aplicaciones](https://docs.microsoft.com/intune/deploy-use/update-apps-using-microsoft-intune) y [supervisar aplicaciones](https://docs.microsoft.com/intune/deploy-use/monitor-apps-in-microsoft-intune).

>[!div class="step-by-step"]

>[&larr; **Organizar usuarios y dispositivos**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)      [**Personalizar el portal de empresa** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  



<!--HONumber=Dec16_HO2-->


