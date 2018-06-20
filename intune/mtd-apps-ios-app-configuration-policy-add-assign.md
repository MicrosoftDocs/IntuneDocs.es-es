---
title: Agregar y asignar aplicaciones MTD a Microsoft Intune
titleSuffix: ''
description: Use Intune para agregar aplicaciones de Mobile Threat Defense (MTD), la aplicación de Microsoft Authenticator y la directiva de configuración de iOS en Azure Portal.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 10502f82d94246f7a70af6b88c0704a4daa0372b
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32046390"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Agregar y asignar aplicaciones de Mobile Threat Defense (MTD) con Intune

> [!NOTE] 
> La información de este tema se aplica a todos los asociados de Mobile Threat Defense.

Puede usar Intune para agregar e implementar las aplicaciones de MTD para que los usuarios finales puedan recibir notificaciones cuando se identifique una amenaza en sus dispositivos móviles y para recibir orientación para solucionar tales amenazas.

Para los dispositivos iOS, necesita [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) de manera que los usuarios puedan comprobar sus identidades con Azure AD. Además, necesita la directiva de configuración de aplicaciones para iOS que indica la aplicación iOS de MTD para usarla con Intune.

> [!TIP]
> El portal de empresa de Intune funciona como el agente de los dispositivos Android, de manera que los usuarios puedan comprobar sus identidades con Azure AD.

## <a name="before-you-begin"></a>Antes de comenzar

-   Los pasos que se indican a continuación deben completarse en [Azure Portal](https://portal.azure.com/).

-   Asegúrese de estar familiarizado con los siguientes procesos:

    -   [Agregar una aplicación en Intune](apps-add.md)

    -   [Descargar una directiva de configuración de aplicación de iOS en Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)

    -   [Asignar una aplicación con Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).

    -   [Agregar una directiva de configuración de aplicaciones iOS](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-add-apps"></a>Para agregar aplicaciones

### <a name="all-mtd-partners"></a>Todos los asociados de MTD

#### <a name="microsoft-authenticator-app-for-ios"></a>Aplicación de Microsoft Authenticator para iOS

- Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](store-apps-ios.md). Use esta [dirección URL de la tienda de aplicaciones de Microsoft Authenticator](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) en el **paso 12** en la sección **Configuración de información de la aplicación**.

### <a name="lookout"></a>Lookout

#### <a name="android"></a>Android
- Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](store-apps-android.md). Use esta [dirección URL de la tienda de aplicaciones de Lookout for Work para Google](https://play.google.com/store/apps/details?id=com.lookout.enterprise) en el **paso 7**.

#### <a name="ios"></a>iOS

- Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](store-apps-ios.md). Use esta [dirección URL de la tienda de aplicaciones iOS para Lookout for Work](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) en el **paso 12** en la sección **Configuración de información de la aplicación**.

#### <a name="lookout-for-work-app-outside-the-apple-store"></a>Aplicación Lookout for Work fuera de la tienda de Apple

Necesita volver a firmar la aplicación Lookout for Work para iOS. Lookout distribuye su aplicación Lookout for Work de iOS fuera de la tienda App Store de iOS. Antes de distribuir la aplicación, deberá volver a firmar la aplicación con su certificado de desarrollador empresarial de iOS.

Para obtener información sobre cómo volver a firmar las aplicaciones Lookout for Work de iOS, vea [el proceso de volver a firmar la aplicación Lookout for Work de iOS](https://personal.support.lookout.com/hc/articles/114094038714) en el sitio web de Lookout.

##### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>Habilitar la autenticación de Azure AD para la aplicación Lookout for Work para iOS

Habilite la autenticación de Azure Active Directory para los usuarios de iOS haciendo lo siguiente:

1. Vaya a [Azure Portal](https://portal.azure.com), inicie sesión con sus credenciales y, después, vaya a la página de la aplicación.

2. Agregue la **aplicación Lookout for Work de iOS** como una **aplicación de cliente nativ**.

3. Reemplace **com.lookout.enterprise.yourcompanyname** por el ID de agrupación del cliente que ha seleccionado cuando se registró el IPA.

4.  Agregue un URI de redireccionamiento adicional: **&lt;companyportal://code/>** seguido de una versión codificada por URL del URI de redireccionamiento original.

5.  Agregue los **permisos delegados** a la aplicación.

    > [!NOTE] 
    > Para obtener más información, vea [Configurar una aplicación de cliente nativo con Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

##### <a name="add-the-lookout-for-work-ipa-file"></a>Agregar el archivo IPA de Lookout for Work

- Cargue el archivo .ipa que se ha vuelto a firmar como se describe en el tema [Agregar aplicaciones LOB para iOS con Intune](lob-apps-ios.md). También necesita establecer la versión mínima del sistema operativo en iOS 8.0 o posterior.

### <a name="symantec-endpoint-protection-mobile-sep-mobile"></a>Symantec Endpoint Protection Mobile (SEP Mobile)

#### <a name="android"></a>Android

- Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](store-apps-android.md). En el **paso 7**, use esta [dirección URL de la tienda de aplicaciones de SEP Mobile](https://play.google.com/store/apps/details?id=com.skycure.skycure).  En **Versión mínima del sistema operativo**, seleccione **Android 4.0 (Ice Cream Sandwich)**.

#### <a name="ios"></a>iOS

- Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](store-apps-ios.md). En el **paso 12**, use esta [dirección URL de la tienda de aplicaciones de SEP Mobile](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) en la sección **Configuración de información de la aplicación**.

### <a name="check-point-sandblast-mobile"></a>SandBlast Mobile de Check Point

#### <a name="android"></a>Android

- Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](store-apps-android.md). Utilice esta [URL de la tienda de aplicaciones móviles de SandBlast Mobile de Check Point](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) en el **paso 7**.

#### <a name="ios"></a>iOS

- Póngase en contacto con el equipo de [SandBlast Mobile de Check Point](https://www.checkpoint.com/products/sandblast-mobile/) para obtener la aplicación para iOS. Consulte las instrucciones para [agregar aplicaciones de App Store a Microsoft Intune](store-apps-ios.md); después, use la dirección URL de la tienda de Apple en el **paso 12** de la sección **Configuración de información de la aplicación**.

### <a name="zimperium"></a>Zimperium

#### <a name="android"></a>Android

- Vea las instrucciones para [agregar aplicaciones de la tienda Android en Microsoft Intune](store-apps-android.md). Use esta [dirección URL de la tienda de aplicaciones de Zimperium](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) en el **paso 7**.

#### <a name="ios"></a>iOS

- Vea las instrucciones para [agregar aplicaciones de la tienda iOS en Microsoft Intune](store-apps-ios.md). Use esta [dirección URL de la tienda de aplicaciones de Zimperium](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) en el **paso 12** de la sección **Configuración de información de la aplicación**.

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>Para asociar la aplicación de MTD con una directiva de configuración de aplicaciones iOS

### <a name="for-lookout"></a>Para Lookout

- Cree la directiva de configuración de aplicaciones para iOS como se describe en el tema [Usar la directiva de configuración de aplicaciones para iOS](app-configuration-policies-use-ios.md).

### <a name="for-sep-mobile"></a>Para SEP Mobile

-   Use la misma cuenta de Azure AD configurada anteriormente en la [consola de administración de Symantec Endpoint Protection](https://aad.skycure.com), que debe ser la misma que se usó para iniciar sesión en el portal clásico de Intune.

-   Debe **descargar** el archivo de directiva de configuración de aplicaciones para iOS: 
    -   Vaya a la [consola de administración de Symantec Endpoint Protection](https://aad.skycure.com) e inicie sesión con sus credenciales de administrador.

    -   Vaya a **Settings** (Configuración) y, en **Integrations** (Integraciones), elija **Intune**. Elija **EMM Integration Selection** (Selección de la integración de EMM). Elija **Microsoft** y guarde la selección.

    -   Haga clic en el vínculo **Integration setup files** (Archivos de configuración de la integración) y guarde el archivo \*.zip generado. El archivo .zip contiene el archivo ***.plist**, que se usará para crear la directiva de configuración de aplicaciones iOS en Intune.

    -   Para agregar la directiva de configuración de aplicaciones de SEP Mobile, consulte las instrucciones para [usar directivas de configuración de aplicaciones de Microsoft Intune para iOS](app-configuration-policies-use-ios.md).

    - En el **paso 8**, use la opción **Especificar datos XML**, copie el contenido del archivo ***.plist** y péguelo en el cuerpo de la directiva de configuración.

> [!NOTE]
> Si no puede recuperar los archivos, póngase en contacto con el [soporte técnico de Symantec Endpoint Protection Mobile Enterprise](https://support.symantec.com/en_US/contact-support.html).

### <a name="for-check-point-sandblast-mobile"></a>Para SandBlast Mobile de Check Point

- Consulte las instrucciones para [usar las directivas de configuración de aplicaciones de Microsoft Intune para iOS](app-configuration-policies-use-ios.md) con el fin de agregar la directiva de configuración de aplicaciones de SandBlast Mobile de Check Point para iOS.
    - En el **paso 8**, use la opción **Especificar datos XML**, copie el contenido siguiente y péguelo en el cuerpo de la directiva de configuración.

```
<dict><key>MDM</key><string>INTUNE</string></dict>
```

### <a name="for-zimperium"></a>Para Zimperium

- Vea las instrucciones para [usar las directivas de configuración de aplicaciones de Microsoft Intune para iOS](app-configuration-policies-use-ios.md) para agregar la directiva de configuración de aplicaciones de Zimperium para iOS.
    - En el **paso 8**, use la opción **Especificar datos XML**, copie el contenido siguiente y péguelo en el cuerpo de la directiva de configuración.

```
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
```

## <a name="to-assign-apps-all-mtd-partners"></a>Para asignar aplicaciones (todos los asociados de MTD)

- Consulte las instrucciones para [asignar aplicaciones a grupos con Intune](apps-deploy.md).

## <a name="next-steps"></a>Pasos siguientes

- [Agregar una directiva de cumplimiento de dispositivos para MTD](mtd-device-compliance-policy-create.md)
