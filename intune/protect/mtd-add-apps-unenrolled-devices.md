---
title: Incorporación de aplicaciones de Mobile Threat Defense a dispositivos no inscritos
titleSuffix: Microsoft Intune
description: Agregue aplicaciones de Mobile Threat Defense a dispositivos no inscritos por usuarios del dispositivo.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8dd7127594a0e23c85b9f8141ce6d398d9a447a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72794464"
---
# <a name="add-mobile-threat-defense-apps-to-unenrolled-devices"></a>Incorporación de aplicaciones de Mobile Threat Defense a dispositivos no inscritos

De forma predeterminada, al usar las directivas de protección de aplicaciones de Intune con Mobile Threat Defense, Intune realiza el trabajo de guiar al usuario final en su dispositivo para instalar e iniciar sesión en todas las aplicaciones necesarias para habilitar las conexiones con los servicios pertinentes.

Los usuarios finales necesitan Microsoft Authenticator (iOS) para registrar su dispositivo y Mobile Threat Defense (iOS y Android) para recibir notificaciones cuando se identifica una amenaza en sus dispositivos móviles, así como instrucciones para corregir las amenazas.

Opcionalmente, se puede usar Intune para agregar e implementar Microsoft Authenticator y también aplicaciones de Mobile Threat Defense (MTD).

> [!NOTE] 
> Este artículo se aplica a todos los asociados de Mobile Threat Defense que admiten directivas de protección de aplicaciones: Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).
> 
> Para los dispositivos no inscritos, **no se necesita una directiva de configuración de aplicaciones de iOS** que configure la aplicación Mobile Threat Defense para iOS que se usa con Intune. Esta es una diferencia importante en comparación con los dispositivos inscritos en Intune. 

## <a name="configure-microsoft-authenticator-for-ios-via-intune-optional"></a>Configuración de Microsoft Authenticator para iOS a través de Intune (opcional)
Cuando se usan directivas de protección de aplicaciones de Intune con Mobile Threat Defense, Intune guiará al usuario final para que instale, inicie sesión y registre su dispositivo con Microsoft Authenticator (iOS).

Pero si quiere que la aplicación esté disponible para los usuarios finales a través del Portal de empresa de Intune, vea las instrucciones para [agregar aplicaciones de la tienda iOS a Microsoft Intune](../apps/store-apps-ios.md). Use esta [dirección URL de la tienda de aplicaciones iOS para Microsoft Authenticator](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) cuando vaya a completar la sección **Configuración de información de la aplicación**. Como paso final, no se olvide de [asignar la aplicación a grupos con Intune](../apps/apps-deploy.md).

> [!NOTE] 
> Para los dispositivos iOS, necesita [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) de manera que los usuarios puedan comprobar sus identidades con Azure AD. El Portal de empresa de Intune funciona como el agente de los dispositivos Android, de manera que los usuarios puedan comprobar sus identidades con Azure AD.

## <a name="making-mobile-threat-defense-apps-available-via-intune-optional"></a>Disponibilidad de las aplicaciones de Mobile Threat Defense a través de Intune (opcional)
Cuando se usan directivas de protección de aplicaciones de Intune con Mobile Threat Defense, Intune guiará al usuario final para que instale e inicie sesión en la aplicación cliente de Mobile Threat Defense adecuada. 

Pero si quiere que la aplicación esté disponible para los usuarios finales a través del Portal de empresa de Intune, puede seguir los pasos siguientes en [Azure Portal](https://portal.azure.com/). Asegúrese de estar familiarizado con los siguientes procesos:

- [Agregar una aplicación en Intune](../apps/apps-add.md)
- [Asignar una aplicación con Intune](../apps/apps-deploy.md).

### <a name="making-lookout-for-work-available-to-end-users"></a>Poner Lookout for Work a disposición de los usuarios finales
- **Android**  
  - Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](../apps/store-apps-android.md). Use esta [dirección URL de Play Store para Lookout for Work](https://play.google.com/store/apps/details?id=com.lookout.enterprise) cuando vaya a completar la sección **Configuración de información de la aplicación**.

- **iOS**
  - Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](../apps/store-apps-ios.md). Use esta [dirección URL de la tienda de aplicaciones iOS para Lookout for Work](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) cuando vaya a completar la sección **Configuración de información de la aplicación**.

<!-- ### Making Symantec Endpoint Protection Mobile available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). When completing the **Configure app information** section, use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure). For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [SEP Mobile - App Store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) when completing the **Configure app information** section.

### Making Check Point SandBlast Mobile available to end users
- **Android**  
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Check Point SandBlast Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) when completing the **Configure app information** section. 

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Check Point SandBlast Mobile - App Store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) when completing the **Configure app information** section. -->

### <a name="making-zimperium-available-to-end-users"></a>Poner Zimperium a disposición de los usuarios finales
<!-- - **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Zimperium - Play Store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) when completing the **Configure app information** section. -->
- **iOS**
  - Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](../apps/store-apps-ios.md). Use esta [dirección URL de la App Store para Zimperium](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) cuando vaya a completar la sección **Configuración de información de la aplicación**.
 
<!-- ### Making Pradeo available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Pradeo - Play Store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Pradeo - App Store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) when completing the **Configure app information** section. -->

### <a name="making-better-mobile-available-to-end-users"></a>Disponibilidad de Better Mobile para los usuarios finales 
- **Android**
  - Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](../apps/store-apps-android.md). Use esta [dirección URL de Play Store para Active Shield](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) cuando vaya a completar la sección **Configuración de información de la aplicación**.
<!-- - **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) when completing the **Configure app information** section. -->

<!-- ### Making Sophos available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Sophos - Play Store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) when completing the **Configure app information** section.

### Making Wandera available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Wandera Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.wandera.android) when completing the **Configure app information** section. For **Minimum operating system**, select **Android 5.0**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Wandera Mobile - - App Store URL](https://itunes.apple.com/app/wandera/id605469330) when completing the **Configure app information** section. -->

## <a name="next-steps"></a>Pasos siguientes  

- [Habilitación del conector Mobile Threat Defense en Intune para dispositivos no inscritos](~/protect/mtd-enable-unenrolled-devices.md)

