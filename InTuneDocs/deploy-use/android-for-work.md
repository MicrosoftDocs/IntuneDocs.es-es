---
title: Acerca de Android for Work | Microsoft Docs
description: "Intune administra Android for Work para proporcionar funcionalidades de administración adicionales y privacidad cuando las personas usan sus dispositivos Android para trabajar."
keywords: 
author: nathbarn
manager: angrobe
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa0002d9-f5a0-466e-98ac-3970cb77e3a2
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: e9a99868e7bd4c3aa45de4d221f28c1d2f3efb74


---

# <a name="manage-android-for-work-devices-with-intune"></a>Administración de dispositivos Android for Work con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Android for Work es un conjunto de características y servicios para dispositivos Android. Tales características y servicios proporcionan funcionalidades de administración adicionales y privacidad cuando las personas usan sus dispositivos Android para trabajar. Intune puede ayudarle a implementar aplicaciones y recursos de empresa para dispositivos Android for Work a fin de garantizar que funcionan y que la información personal se mantiene aparte. Cuando se implementan correctamente, las aplicaciones y los datos a los que acceden permanecen exclusivamente en el entorno de Android for Work del dispositivo.

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

## <a name="supported-devices"></a>Dispositivos compatibles

Android for Work necesita hardware de Android más reciente porque muchas funcionalidades de administración dependen de características que son parte del sistema operativo Android más nuevo. Android for Work se admite actualmente en dispositivos que ejecutan Android 5.0 Lollipop y versiones posteriores, y que son compatibles con perfiles de trabajo. En dispositivos que no tienen compatibilidad nativa con Android for Work, sigue estando disponible la administración de Android convencional. Más información sobre los [requisitos de Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Incorporación

Antes de inscribir dispositivos Android for Work, debe llevar a cabo algunos pasos de incorporación. Estos pasos establecen una conexión entre el inquilino de Intune y el servicio Play for Work de Google, que es parte integral de la distribución de aplicaciones y el proceso de administración de Android for Work. Más información sobre [cómo habilitar la inscripción de Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-android-for-work).

## <a name="work-profile-management"></a>Administración de perfiles de trabajo

Cuando administra un dispositivo Android for Work con Intune, no administra todo el dispositivo. Las funciones de administración solo afectan a un perfil de trabajo que se crea durante la inscripción. Las aplicaciones que se implementan en el dispositivo con Intune forman parte del perfil de trabajo. Los iconos de aplicaciones en el perfil de trabajo mostrarán un maletín naranja. Esta marca diferencia las aplicaciones de empresa de las personales en el dispositivo. Todas las aplicaciones y los datos de Android que están fuera de la parte Android for Work del dispositivo permanecen como personales y bajo el control del usuario final. Los usuarios pueden instalar cualquier aplicación que elijan en el lado personal del dispositivo, mientras que los administradores pueden administrar y supervisar las acciones que tienen como ámbito el perfil de trabajo.

## <a name="app-publishing-and-distribution"></a>Distribución y publicación de aplicaciones

El servicio Google Play for Work es una parte integral de la distribución y la administración de aplicaciones. Todas las aplicaciones implementadas en dispositivos Android for Work en el perfil de trabajo proceden de Play for Work. Para administrar e implementar aplicaciones en Play Store, inicie sesión como administrador de Intune en el sitio web de Play for Work y apruebe las aplicaciones de su inquilino de Intune. Estas aplicaciones se sincronizan con la consola de Intune donde se pueden implementar y administran mediante Intune. Las aplicaciones de línea de negocio (LOB) desarrolladas por su organización se deben publicar en Play for Work mediante la consola de publicación de aplicaciones de Android de Google. Este tipo de aplicaciones se deben configurar en la consola de publicación de aplicaciones de Android para restringir el acceso a su organización.

Las aplicaciones se instalan sin interacción del usuario y sin necesidad de que el usuario permita la **instalación desde orígenes desconocidos**. Para examinar e instalar aplicaciones opcionales o disponibles, el usuario coloca el distintivo de trabajo a la aplicación de Play Store en su dispositivo. Más información sobre [la implementación de aplicaciones de Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/android-for-work-apps).

## <a name="app-configuration"></a>Configuración de aplicaciones

Android for Work proporciona una infraestructura para implementar valores de configuración de aplicaciones en aplicaciones que los admiten. Al especificar valores de configuración para aplicaciones de trabajo, se asegura de que están configuradas correctamente cuando los usuarios inician la aplicación por primera vez. Para permitir la compatibilidad con la configuración de aplicaciones, es necesario que los desarrolladores de aplicaciones creen sus aplicaciones Android específicamente para admitir valores de configuración administrados. Si lo hacen, podrá usar Intune para especificar y aplicar estos valores de configuración. Más información sobre [los valores de configuración de aplicaciones de Android for Work](afw-app-configuration-policy.md).

## <a name="email-configuration"></a>Configuración del correo electrónico

Android for Work no proporciona una aplicación de correo electrónico predeterminada o un perfil de correo electrónico nativo como el que proporciona iOS. En su lugar, las configuraciones de correo electrónico se pueden establecer aplicando los valores de configuración a las aplicaciones de correo electrónico que los admitan. Gmail y Nine Work son dos aplicaciones cliente de Exchange ActiveSync (EAS) de Play Store que admiten la configuración con aplicaciones de Android for Work.

Intune proporciona plantillas de configuración para aplicaciones de Gmail y Nine Work. Otras aplicaciones de correo electrónico que admiten perfiles de configuración de aplicaciones pueden configurarse con las directivas de configuración de aplicaciones móviles.

Si va a usar acceso condicional EAS en dispositivos Android for Work, debe utilizar la aplicación de correo electrónico Gmail o Nine Work. También se admite la aplicación Microsoft Outlook para Android o cualquier otra aplicación de correo electrónico que utilice autenticación moderna mediante ADAL. Más información sobre los [perfiles de correo electrónico para el correo electrónico de empresa](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## <a name="mobile-app-management-policies"></a>Directivas de administración de aplicaciones móviles

Las directivas de restricción que se aplican a aplicaciones habilitadas para la administración de aplicaciones móviles (MAM) son totalmente compatibles con el perfil del trabajo y el perfil personal. Puede publicar aplicaciones de línea de negocio en la consola de publicación de aplicaciones de Android en https://play.google.com/apps/publish. Esta consola incluye una opción para convertir las aplicaciones en privadas para su organización. Más información sobre la [configuración de directivas de cumplimiento](afw-compliance-policy-settings-in-microsoft-intune.md). Para obtener más información, consulte las [directivas de administración de aplicaciones móviles](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

## <a name="vpn-profiles"></a>Perfiles de VPN

La compatibilidad con VPN es similar a los perfiles de VPN de Android. Están disponibles los mismos proveedores de VPN y las mismas opciones de configuración básica. Hay dos diferencias principales:

1.  **VPN con ámbito de perfiles de trabajo**: las conexiones VPN se limitan solo a las aplicaciones implementadas en el perfil de trabajo. Solo las aplicaciones administradas por Android for Work pueden utilizar la conexión VPN. Las aplicaciones personales del dispositivo no pueden usar una conexión VPN administrada.

2.  **VPN específica de la aplicación**: si un proveedor de VPN admite la configuración de VPN específica de la aplicación y proporciona la funcionalidad para configurar VPN por aplicación mediante el perfil de configuración de aplicaciones de Android for Work, se pueden configurar VPN específicas de la aplicación en Intune. Consulte al proveedor de VPN para ver si se admite esta funcionalidad. Más información sobre los [perfiles de conexión VPN](vpn-connections-in-microsoft-intune.md).

## <a name="certificate-profiles"></a>Perfiles de certificado

Las mismas opciones de configuración de perfiles de certificado que están disponibles para la administración tradicional de Android están disponibles en dispositivos Android for Work. Android for Work proporciona API mejoradas de administración de certificados. La administración mejorada de certificados proporciona la funcionalidad siguiente:

1.  Garantiza la implementación silenciosa y transparente para el usuario.

2.  Garantiza que los certificados implementados se quitan completamente cuando se retira un dispositivo de Intune y se quita el perfil de trabajo.

3.  Proporciona mensajería mejorada que informa a los usuarios que el departamento de TI ha implementado y configurado el certificado mediante su servicio de administración.

Más información sobre los [perfiles de certificado](secure-resource-access-with-certificate-profiles.md)

## <a name="wi-fi-profiles"></a>Perfiles de Wi-Fi

Se garantiza que los perfiles Wi-Fi administrados por Android for Work se quitan cuando el dispositivo se retira de Intune y se elimina el perfil de trabajo. Más información sobre los [perfiles Wi-Fi](wi-fi-connections-in-microsoft-intune.md).

## <a name="next-steps"></a>Pasos siguientes
[Habilitación de la inscripción en Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-android-for-work)
[Implementación de aplicaciones para Android for Work](https://docs.microsoft.com/en-us/intune/deploy-use/android-for-work-apps)



<!--HONumber=Dec16_HO2-->


