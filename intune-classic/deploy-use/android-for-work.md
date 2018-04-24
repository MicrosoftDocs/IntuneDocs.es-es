---
title: Acerca de Android for Work
description: Intune administra Android for Work para proporcionar funcionalidades de administración adicionales y privacidad cuando las personas usan sus dispositivos Android para trabajar.
keywords: ''
author: nathbarn
manager: dougeby
ms.date: 03/22/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: aa0002d9-f5a0-466e-98ac-3970cb77e3a2
ROBOTS: NOINDEX,NOFOLLOW
ms.custom: intune-classic
ms.openlocfilehash: ac83eb71b04e034023d008fa4cdbb960f2c4bedb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="manage-android-for-work-devices-with-intune"></a>Administración de dispositivos Android for Work con Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Android for Work es un conjunto de características y servicios para dispositivos Android que permite separar las aplicaciones y los datos personales de un perfil de trabajo que contenga aplicaciones y datos laborales. Android for Work proporciona funcionalidades de administración adicionales y privacidad cuando las personas usan sus dispositivos Android para trabajar. Intune le ayuda a implementar aplicaciones y recursos de empresa para dispositivos Android for Work a fin de garantizar que funcionen y que la información personal se mantenga aparte. Cuando se implementan correctamente, las aplicaciones y los datos a los que acceden permanecen exclusivamente en el entorno de Android for Work del dispositivo.

## <a name="supported-devices"></a>Dispositivos compatibles

Las funcionalidades de administración de Android for Work dependen de las características que forman parte del nuevo sistema operativo Android. Actualmente, Android for Work es compatible con dispositivos con Android 5.0 Lollipop y versiones posteriores que admitan un perfil de trabajo. En el caso de los dispositivos que no sean compatibles con Android for Work, la administración de Android convencional sigue estando disponible. Más información sobre los [requisitos de Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Incorporación

Antes de inscribir dispositivos Android for Work, debe llevar a cabo algunos pasos de incorporación. Estos pasos establecen una conexión entre el inquilino de Intune y el servicio Play for Work de Google, que es parte integral de la distribución de aplicaciones y el proceso de administración de Android for Work. Más información sobre [cómo habilitar la inscripción de Android for Work](/intune-classic/deploy-use/set-up-android-for-work).

## <a name="work-profile-management"></a>Administración de perfiles de trabajo

Cuando administra un dispositivo Android for Work con Intune, no administra todo el dispositivo. Las funcionalidades de administración solo afectan al perfil de trabajo que se crea en el dispositivo durante la inscripción. Las aplicaciones implementadas en el dispositivo con Intune se instalan en el perfil de trabajo. Los iconos de las aplicaciones del perfil de trabajo muestran un maletín naranja para diferenciar las laborales de las personales en el dispositivo. Todas las aplicaciones y los datos de Android que están fuera de la parte Android for Work del dispositivo permanecen como personales y bajo el control del usuario final. Los usuarios pueden instalar cualquier aplicación que elijan en el lado personal del dispositivo, mientras que los administradores pueden administrar y supervisar las aplicaciones y las acciones que tengan el perfil de trabajo como ámbito.

Intune proporciona una variedad de opciones generales integradas que puede configurar en los dispositivos Android for Work. Más información sobre la [configuración de directivas de Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="app-publishing-and-distribution"></a>Distribución y publicación de aplicaciones

El servicio Google Play for Work es una parte integral de la distribución y la administración de aplicaciones de Android for Work. Todas las aplicaciones implementadas en dispositivos Android for Work en el perfil de trabajo proceden del servicio Play for Work. Para administrar e implementar aplicaciones en Play Store, inicia sesión en el sitio web de Google Play con las credenciales de administrador de tu empresa para administrar Google. Puede aprobar aplicaciones para la implementación de Android for Work para que aparezcan en los perfiles de trabajo de los dispositivos. Estas aplicaciones se sincronizan con la consola de Intune, donde se pueden implementar y administrar mediante Intune. Las aplicaciones de línea de negocio (LOB) desarrolladas por su organización se deben publicar en Play for Work mediante la consola de publicación de aplicaciones de Android de Google. Este tipo de aplicaciones se deben configurar en la consola de publicación de aplicaciones de Android para restringir el acceso a su organización.

Las aplicaciones se pueden instalar sin interacción del usuario y sin necesidad de que el usuario tenga que permitir la **instalación desde orígenes desconocidos**. Para buscar e instalar aplicaciones opcionales o disponibles, el usuario puede examinar la tienda Play for Work en su dispositivo. Más información sobre [la implementación de aplicaciones de Android for Work](/intune-classic/deploy-use/android-for-work-apps).

## <a name="app-configuration"></a>Configuración de aplicaciones

Android for Work proporciona una infraestructura para implementar valores de configuración de aplicaciones en aplicaciones que los admiten. Al especificar valores de configuración para aplicaciones de trabajo, se asegura de que están configuradas correctamente cuando los usuarios inician la aplicación por primera vez. Para permitir la compatibilidad con la configuración de aplicaciones, es necesario que los desarrolladores de aplicaciones creen sus aplicaciones Android específicamente para admitir valores de configuración administrados. Si lo hacen, podrá usar Intune para especificar y aplicar estos valores de configuración. Más información sobre [los valores de configuración de aplicaciones de Android for Work](afw-app-configuration-policy.md).

## <a name="email-configuration"></a>Configuración del correo electrónico

Android for Work no proporciona una aplicación de correo electrónico predeterminada o un perfil de correo electrónico nativo como el que proporciona iOS. En su lugar, las configuraciones de correo electrónico se pueden establecer aplicando los valores de configuración a las aplicaciones de correo electrónico que los admitan. Gmail y Nine Work son dos aplicaciones cliente de Exchange ActiveSync (EAS) de Play Store que admiten la configuración con aplicaciones de Android for Work.

Intune proporciona plantillas de configuración para aplicaciones de Gmail y Nine Work cuando se administran como aplicaciones de trabajo. Otras aplicaciones de correo electrónico que admiten perfiles de configuración de aplicaciones pueden configurarse con las directivas de configuración de aplicaciones móviles.

Si va a usar el acceso condicional de Exchange ActiveSync en dispositivos Android for Work, debe utilizar la aplicación de correo electrónico de Gmail o de Nine Work. También se admite la aplicación Microsoft Outlook para Android o cualquier otra aplicación de correo electrónico que utilice autenticación moderna mediante ADAL. Más información sobre los [perfiles de correo electrónico para el correo electrónico de empresa](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## <a name="app-protection-policies"></a>Directivas de protección de aplicaciones

Las directivas de protección de aplicaciones que se aplican son totalmente compatibles con el perfil del trabajo y el perfil personal. Puede publicar aplicaciones de línea de negocio en la consola de publicación de aplicaciones de Android en https://play.google.com/apps/publish. Esta consola incluye una opción para convertir las aplicaciones en privadas para su organización. Obtenga más información sobre la [configuración de directivas de cumplimiento de Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md). Para obtener información general sobre las directivas de protección de aplicaciones, consulte las [directivas de aplicaciones](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

## <a name="vpn-profiles"></a>Perfiles de VPN

La compatibilidad con VPN es similar a los perfiles de VPN de Android. Android for Work dispone de las mismas opciones de configuración básicas y de los mismos proveedores de VPN, aunque con dos diferencias:

-  **VPN con ámbito de perfiles de trabajo**: las conexiones VPN se limitan solo a las aplicaciones implementadas en el perfil de trabajo. Solo las aplicaciones administradas con Android for Work pueden utilizar la conexión VPN. Las aplicaciones personales del dispositivo no pueden usar una conexión VPN administrada.

-  **VPN específica de la aplicación**: si un proveedor de VPN admite la configuración de una VPN específica de la aplicación y proporciona la funcionalidad para configurar una VPN por cada aplicación mediante el perfil de configuración de aplicaciones de Android for Work, se pueden configurar VPN específicas de la aplicación en Intune. Consulte al proveedor de VPN para ver si se admite esta funcionalidad. Más información sobre los [perfiles de conexión VPN](vpn-connections-in-microsoft-intune.md).

## <a name="certificate-profiles"></a>Perfiles de certificado

Las mismas opciones de configuración de perfiles de certificado que están disponibles para la administración de Android están disponibles en dispositivos Android for Work. Android for Work proporciona API mejoradas de administración de certificados. La administración mejorada de certificados proporciona la funcionalidad siguiente:

- Garantiza la implementación silenciosa y transparente para el usuario.
-  Garantiza que los certificados implementados se quitan completamente cuando se retira un dispositivo de Intune y se quita el perfil de trabajo.
-  Proporciona mensajería mejorada que informa a los usuarios que el departamento de TI ha implementado y configurado el certificado mediante su servicio de administración.

Más información sobre los [perfiles de certificado](secure-resource-access-with-certificate-profiles.md)

## <a name="wi-fi-profiles"></a>Perfiles de Wi-Fi

Los perfiles de Wi-Fi administrados con Android for Work se quitan cuando el dispositivo se retira de Intune y se elimina el perfil de trabajo. Más información sobre los [perfiles Wi-Fi](wi-fi-connections-in-microsoft-intune.md).

## <a name="next-steps"></a>Pasos siguientes
[Habilitación de la inscripción de Android for Work](/intune-classic/deploy-use/set-up-android-for-work)

[Implementación de aplicaciones para Android for Work](/intune-classic/deploy-use/android-for-work-apps)
