---
title: Agregar y asignar aplicaciones MTD a Microsoft Intune
titleSuffix: Microsoft Intune
description: Use Intune para agregar aplicaciones de Mobile Threat Defense (MTD), la aplicación de Microsoft Authenticator y la directiva de configuración de iOS en Azure Portal.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f5ca8b7c94569861ccc5c4235315a7a57de9d838
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504412"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Agregar y asignar aplicaciones de Mobile Threat Defense (MTD) con Intune  

> [!NOTE] 
> Este tema se aplica a todos los asociados de Mobile Threat Defense.

Puede usar Intune para agregar e implementar las aplicaciones de Mobile Threat Defense (MTD) para que los usuarios finales puedan recibir notificaciones al identificar una amenaza en sus dispositivos móviles y para recibir orientación con el objetivo de solucionarlas.

## <a name="before-you-begin"></a>Antes de comenzar    
Los pasos que se indican a continuación deben completarse en [Azure Portal](https://portal.azure.com/). Asegúrese de estar familiarizado con los siguientes procesos:

- [Agregar una aplicación en Intune](../apps/apps-add.md)
- [Descargar una directiva de configuración de aplicación de iOS en Intune](../apps/app-configuration-policies-use-ios.md)
- [Asignar una aplicación con Intune](../apps/apps-deploy.md).

> [!TIP]
> El Portal de empresa de Intune funciona como el agente de los dispositivos Android, de manera que los usuarios puedan comprobar sus identidades con Azure AD.

## <a name="configure-microsoft-authenticator-for-ios"></a>Configuración de Microsoft Authenticator para iOS  
Para los dispositivos iOS, necesita [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) de manera que los usuarios puedan comprobar sus identidades con Azure AD. Además, necesita una directiva de configuración de aplicaciones para iOS que establezca la aplicación iOS de MTD para usarla con Intune.

Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](../apps/store-apps-ios.md). Use esta [dirección URL de la tienda de aplicaciones de Microsoft Authenticator](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) en el **paso 12** en la sección **Configuración de información de la aplicación**.

## <a name="configure-mtd-applications"></a>Configuración de aplicaciones de MTD  
Elija la sección que corresponda, según su proveedor MTD:

- [Lookout for Work](#configure-lookout-for-work-apps)
- [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
- [SandBlast Mobile de Check Point](#configure-check-point-sandblast-mobile-apps)
- [Zimperium](#configure-zimperium-apps)
- [Pradeo](#configure-pradeo-apps)
- [Better Mobile](#configure-better-mobile-apps)
- [Sophos Mobile](#configure-sophos-apps)
- [Wandera](#configure-wandera-apps)

### <a name="configure-lookout-for-work-apps"></a>Configuración de aplicaciones Lookout for Work  
- **Android**  
  - Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](../apps/store-apps-android.md). Use esta [dirección URL de la tienda de aplicaciones de Lookout for Work para Google](https://play.google.com/store/apps/details?id=com.lookout.enterprise) en el **paso 7**.

- **iOS**
  - Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](../apps/store-apps-ios.md). Use la [dirección URL de Lookout for Work en la tienda App Store de iOS](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) que aparece en el **paso 11** como la **dirección URL de la tienda App Store**.

- **Aplicación Lookout for Work fuera de la tienda de Apple**  
  - Necesita volver a firmar la aplicación Lookout for Work para iOS. Lookout distribuye su aplicación Lookout for Work de iOS fuera de la tienda App Store de iOS. Antes de distribuir la aplicación, deberá volver a firmar la aplicación con su certificado de desarrollador empresarial de iOS.  
  - Para obtener información sobre cómo volver a firmar las aplicaciones Lookout for Work de iOS, vea [el proceso de volver a firmar la aplicación Lookout for Work de iOS](https://personal.support.lookout.com/hc/articles/114094038714) en el sitio web de Lookout.

  - **Habilite la autenticación de Azure AD para los usuarios de la aplicación Lookout for Work para iOS**.

    1. Vaya a [Azure Portal](https://portal.azure.com), inicie sesión con sus credenciales y, después, vaya a la página de la aplicación.

    2. Agregue la **aplicación Lookout for Work de iOS** como una **aplicación de cliente nativ**.

    3. Reemplace **com.lookout.enterprise.yourcompanyname** por el ID de agrupación del cliente que ha seleccionado cuando se registró el IPA.

    4. Agregue un URI de redireccionamiento adicional: **&lt;companyportal://code/>** seguido de una versión codificada por URL del URI de redireccionamiento original.

    5. Agregue los **permisos delegados** a la aplicación.

    > [!NOTE] 
    > Para obtener más información, vea [Configurar una aplicación de cliente nativo con Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

  - **Agregue el archivo IPA de Lookout for Work**.

    - Cargue el archivo .ipa que se ha vuelto a firmar como se describe en el artículo [Agregar aplicaciones LOB para iOS con Intune](../apps/lob-apps-ios.md). También necesita establecer la versión mínima del sistema operativo en iOS 8.0 o posterior.

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>Configuración de aplicaciones Symantec Endpoint Protection Mobile  
- **Android**
  - Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](../apps/store-apps-android.md). En el **paso 7**, use esta [dirección URL de la tienda de aplicaciones de SEP Mobile](https://play.google.com/store/apps/details?id=com.skycure.skycure).  En **Versión mínima del sistema operativo**, seleccione **Android 4.0 (Ice Cream Sandwich)** .

- **iOS**
  - Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](../apps/store-apps-ios.md). Use la [dirección URL de SEP Mobile en la tienda App Store](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) que aparece en el **paso 11** como la **dirección URL de la tienda App Store**.

### <a name="configure-check-point-sandblast-mobile-apps"></a>Configuración de aplicaciones SandBlast Mobile de Check Point  
- **Android**  
  - Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](../apps/store-apps-android.md). Utilice esta [URL de la tienda de aplicaciones móviles de SandBlast Mobile de Check Point](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) en el **paso 7**.

- **iOS**
  - Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](../apps/store-apps-ios.md). Use la [dirección URL de SandBlast Mobile de Check Point en la tienda App Store](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) que aparece en el **paso 11** como la **dirección URL de la tienda App Store**.  

### <a name="configure-zimperium-apps"></a>Configuración de aplicaciones Zimperium  
- **Android**
  - Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](../apps/store-apps-android.md). Use esta [dirección URL de la tienda de aplicaciones de Zimperium](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) en el **paso 7**.

- **iOS**
  - Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](../apps/store-apps-ios.md). Use la [dirección URL de Zimperium en la tienda App Store](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) que aparece en el **paso 11** como la **dirección URL de la tienda App Store**.  
 
### <a name="configure-pradeo-apps"></a>Configuración de aplicaciones Pradeo  
- **Android**
  - Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](../apps/store-apps-android.md). Use esta [dirección URL de la tienda de aplicaciones de Pradeo](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) en el **paso 7**.

- **iOS**
  - Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](../apps/store-apps-ios.md). Use la [dirección URL de Pradeo en la tienda App Store](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) que aparece en el **paso 11** como la **dirección URL de la tienda App Store**.

### <a name="configure-better-mobile-apps"></a>Configuración de aplicaciones de Better Mobile  
- **Android**
  - Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](../apps/store-apps-android.md). Use esta [dirección URL de la tienda de aplicaciones de Active Shield](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) en el **paso 7**.

- **iOS**
  - Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](../apps/store-apps-ios.md). Use la [dirección URL de ActiveShield en la tienda App Store](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) que aparece en el **paso 11** como la **dirección URL de la tienda App Store**.

### <a name="configure-sophos-apps"></a>Configuración de aplicaciones de Sophos  
- **Android**
  - Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](../apps/store-apps-android.md). Use esta [dirección URL de la tienda de aplicaciones de Sophos](https://play.google.com/store/apps/details?id=com.sophos.smsec) en el **paso 7**.

- **iOS**
  - Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](../apps/store-apps-ios.md). Use la [dirección URL de ActiveShield en la tienda App Store](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) que aparece en el **paso 11** como la **dirección URL de la tienda App Store**.

### <a name="configure-wandera-apps"></a>Configuración de aplicaciones de Wandera  
 
- **Android**
  - Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](../apps/store-apps-android.md). Use esta [dirección URL de la tienda de aplicaciones de Wandera Mobile](https://play.google.com/store/apps/details?id=com.wandera.android) en el **paso 7**. En **Versión mínima del sistema operativo**, seleccione **Android 5.0**.

- **iOS**
  - Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](../apps/store-apps-ios.md). Use la [dirección URL de Wandera Mobile en la tienda App Store](https://itunes.apple.com/app/wandera/id605469330) que aparece en el **paso 11** como la **dirección URL de la tienda App Store**.

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>Configuración de aplicaciones de MTD con una directiva de configuración de aplicaciones iOS  

### <a name="lookout-for-work-app-configuration-policy"></a>Directiva de configuración de aplicaciones Lookout for Work  
- Cree la directiva de configuración de aplicaciones para iOS como se describe en el artículo [Usar la directiva de configuración de aplicaciones para iOS](../apps/app-configuration-policies-use-ios.md).

### <a name="sep-mobile-app-configuration-policy"></a>Directiva de configuración de aplicaciones de SEP Mobile  
- Use la misma cuenta de Azure AD configurada anteriormente en la [consola de administración de Symantec Endpoint Protection](https://aad.skycure.com), que debe ser la misma que se usó para iniciar sesión en el portal clásico de Intune.

- **Descargue** el archivo de la directiva de configuración de la aplicación de iOS: 
  - Vaya a la [consola de administración de Symantec Endpoint Protection](https://aad.skycure.com) e inicie sesión con sus credenciales de administrador.

  - Vaya a **Settings** (Configuración) y, en **Integrations** (Integraciones), elija **Intune**. Elija **EMM Integration Selection** (Selección de la integración de EMM). Elija **Microsoft** y guarde la selección.

  - Haga clic en el vínculo **Integration setup files** (Archivos de configuración de la integración) y guarde el archivo \*.zip generado. El archivo .zip contiene el archivo * **.plist**, que se usará para crear la directiva de configuración de aplicaciones iOS en Intune.

  - Para agregar la directiva de configuración de aplicaciones de SEP Mobile, consulte las instrucciones para [usar directivas de configuración de aplicaciones de Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md).

  - En el **paso 8**, use la opción **Especificar datos XML**, copie el contenido del archivo * **.plist** y péguelo en el cuerpo de la directiva de configuración.

> [!NOTE]  
> Si no puede recuperar los archivos, póngase en contacto con el [soporte técnico de Symantec Endpoint Protection Mobile Enterprise](https://support.symantec.com/en_US/contact-support.html).

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Directiva de configuración de aplicaciones SandBlast Mobile de Check Point  
- Consulte las instrucciones para [usar las directivas de configuración de aplicaciones de Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md) con el fin de agregar la directiva de configuración de aplicaciones de SandBlast Mobile de Check Point para iOS.
  - En el **paso 8**, use la opción **Especificar datos XML**, copie el contenido siguiente y péguelo en el cuerpo de la directiva de configuración.

        <dict><key>MDM</key><string>INTUNE</string></dict>


### <a name="zimperium-app-configuration-policy"></a>Directiva de configuración de aplicaciones de Zimperium  
- Vea las instrucciones para [usar las directivas de configuración de aplicaciones de Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md) para agregar la directiva de configuración de aplicaciones de Zimperium para iOS.
  - En el **paso 8**, use la opción **Especificar datos XML**, copie el contenido siguiente y péguelo en el cuerpo de la directiva de configuración.
 
        <dict>
        <key>provider</key><string>Intune</string>
        <key>userprincipalname</key><string>{{userprincipalname}}</string>
        <key>deviceid</key>
        <string>{{deviceid}}</string>
        <key>serialnumber</key>
        <string>{{serialnumber}}</string>
        <key>udidlast4digits</key>
        <string>{{udidlast4digits}}</string>
        </dict>

### <a name="pradeo-app-configuration-policy"></a>Directiva de configuración de aplicaciones de Pradeo  
Pradeo no es compatible con la directiva de configuración de aplicaciones en iOS.  En su lugar, para configurar una aplicación, trabaje con Pradeo para implementar archivos IPA o APK personalizados que estén preconfigurados con la configuración que quiera.

### <a name="better-mobile-app-configuration-policy"></a>Directiva de configuración de aplicaciones de Better Mobile  
- Para agregar la directiva de configuración de aplicaciones de Better Mobile, consulte las instrucciones para [usar directivas de configuración de aplicaciones de Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md).
  - En el **paso 8**, use la opción **Especificar datos XML**, copie el contenido siguiente y péguelo en el cuerpo de la directiva de configuración. Reemplace la dirección URL `https://client.bmobi.net` por la dirección URL de consola apropiada.

        <dict>
        <key>better_server_url</key>
        <string>https://client.bmobi.net</string>
        <key>better_udid</key>
        <string>{{aaddeviceid}}</string>
        <key>better_user</key>
        <string>{{userprincipalname}}</string>
        </dict>


### <a name="sophos-mobile-app-configuration-policy"></a>Directiva de configuración de aplicaciones de Sophos Mobile  
Cree la directiva de configuración de aplicaciones para iOS como se describe en el artículo [Usar la directiva de configuración de aplicaciones para iOS](../apps/app-configuration-policies-use-ios.md).

### <a name="wandera-app-configuration-policy"></a>Directiva de configuración de aplicaciones de Wandera  
Consulte las instrucciones para [usar las directivas de configuración de aplicaciones de Microsoft Intune para iOS](../apps/app-configuration-policies-use-ios.md) para agregar la directiva de configuración de aplicaciones de Wandera para iOS.
- En el **paso 8**, use la opción **Especificar datos XML**. Inicie sesión en el portal RADAR de Wandera y vaya a **Configuración** > **Integración de EMM** > **App Push** (Inserción de aplicación). Seleccione **Intune** y, luego, copie el contenido siguiente y péguelo en el cuerpo de la directiva de configuración.  

      <dict><key>secretKey</key>
       <string>SeeRADAR</string>
       <key>apiKey</key>
       <string> SeeRADAR </string>
       <key>customerId</key>
       <string> SeeRADAR </string>
       <key>email</key>
       <string>{{mail}}</string>
       <key>firstName</key>
       <string>{{username}}</string>
       <key>lastName</key>
       <string></string>
       <key>activationType</key>
       <string>PROVISION_THEN_AWP</string></dict>  

## <a name="assign-apps-to-groups"></a>Asignación de aplicaciones a grupos  
- Este paso se aplica a todos los asociados de MTD. Consulte las instrucciones para [asignar aplicaciones a grupos con Intune](../apps/apps-deploy.md).

## <a name="next-steps"></a>Pasos siguientes  
- [Configuración de la directiva de cumplimiento de dispositivos para MTD](mtd-device-compliance-policy-create.md)
