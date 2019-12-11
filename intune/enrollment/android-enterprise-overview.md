---
title: Administrar dispositivos de perfil de trabajo Android Enterprise en Microsoft Intune
titleSuffix: ''
description: Microsoft Intune administra dispositivos de perfil de trabajo Android Enterprise para proporcionar funciones de administración adicionales y privacidad cuando las personas usan sus dispositivos personales Android para trabajar.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a5c980b3f9ababaf94aa7b279e533679ed74b0e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503364"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>Administrar dispositivos de perfil de trabajo Android con Intune

Android Enterprise ofrece un conjunto de opciones de inscripción que proporcionan a los usuarios las características más actualizadas y seguras. La inscripción con el perfil de trabajo Android Enterprise ofrece un conjunto de características y servicios que permite separar aplicaciones y datos personales de aplicaciones y datos de trabajo. También proporciona funciones de administración adicionales y privacidad cuando las personas usan sus dispositivos personales Android para trabajar. 

## <a name="supported-devices"></a>Dispositivos compatibles

Las funciones de administración de Android Enterprise dependen de las características que forman parte del sistema operativo Android más reciente. En el caso de los dispositivos que no sean compatibles con Android Enterprise, la administración de Android convencional sigue estando disponible. Para más información, vea [Requisitos de Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Incorporación

Antes de inscribir dispositivos de perfil de trabajo Android Enterprise, debe llevar a cabo algunos pasos de incorporación. Estos pasos establecen una conexión entre su inquilino de Intune y Google Play administrado. Para más información, vea [Configure la inscripción de dispositivos de perfil de trabajo Android](android-work-profile-enroll.md).

## <a name="work-profile-management"></a>Administración de perfiles de trabajo

Cuando administra un dispositivo de perfil de trabajo Android Enterprise con Intune, no administra todo el dispositivo. Las funcionalidades de administración solo afectan al perfil de trabajo que se crea en el dispositivo durante la inscripción. Las aplicaciones implementadas en el dispositivo con Intune se instalan en el perfil de trabajo. Los iconos de aplicación en el perfil de trabajo se diferencian de las aplicaciones personales del dispositivo. Todas las aplicaciones y los datos de Android que están fuera de la parte Android Enterprise del dispositivo permanecen como personales y bajo el control del usuario final. Los usuarios pueden instalar la aplicación que quieran en el lado personal del dispositivo. Los administradores pueden administrar y supervisar aplicaciones y acciones en el perfil de trabajo.

Intune proporciona una variedad de opciones generales integradas que puede configurar en los dispositivos de perfil de trabajo Android. Para obtener más información, consulte [Android work profile device policy settings](../protect/compliance-policy-create-android-for-work.md) (Configuración de las directiva para dispositivos de perfil de trabajo Android).

## <a name="app-publishing-and-distribution"></a>Distribución y publicación de aplicaciones

Google Play administrado es una parte integral de la distribución y la administración de aplicaciones de Android Enterprise. Todas las aplicaciones implementadas en dispositivos de perfil de trabajo Android Enterprise en el perfil de trabajo proceden del servicio Google Play administrado. Para administrar e implementar aplicaciones en Play Store, inicie sesión en el sitio web de Google Play con las credenciales de administrador de su empresa para administrar Google. Puede aprobar aplicaciones para la implementación de Android Enterprise para que aparezcan en los perfiles de trabajo de los dispositivos. Estas aplicaciones se sincronizan con la consola de Intune, donde se pueden implementar y administrar mediante Intune. Las aplicaciones de línea de negocio (LOB) desarrolladas por su organización se deben publicar en Google Play administrado mediante la consola de publicación de aplicaciones de Android de Google. Este tipo de aplicaciones se deben configurar en la consola de publicación de aplicaciones de Android para restringir el acceso a su organización.

Las aplicaciones se pueden instalar sin interacción del usuario y sin necesidad de que el usuario tenga que permitir la **instalación desde orígenes desconocidos**. Para buscar e instalar aplicaciones opcionales o disponibles, el usuario puede examinar la tienda Play for Work en su dispositivo. Para más información, vea [Asignación de aplicaciones para dispositivos de perfil de trabajo Android Enterprise con Intune](../apps/apps-add-android-for-work.md).

## <a name="app-configuration"></a>Configuración de aplicaciones

Android Enterprise proporciona una infraestructura para implementar valores de configuración de aplicaciones en aplicaciones que los admiten. Al especificar valores de configuración para aplicaciones de trabajo, se asegura de que están configuradas correctamente cuando los usuarios inician la aplicación por primera vez. Para permitir la compatibilidad con la configuración de aplicaciones, es necesario que los desarrolladores de aplicaciones creen sus aplicaciones Android específicamente para admitir valores de configuración administrados. Si lo hacen, podrá usar Intune para especificar y aplicar estos valores de configuración. Para obtener más información, vea [Agregar directivas de configuración de aplicaciones para dispositivos Android administrados](../apps/app-configuration-policies-use-android.md).

## <a name="email-configuration"></a>Configuración del correo electrónico

Android Enterprise no proporciona una aplicación de correo electrónico predeterminada o un perfil de correo electrónico nativo como los que proporciona iOS. En su lugar, las configuraciones de correo electrónico se pueden establecer aplicando los valores de configuración a las aplicaciones de correo electrónico que los admitan. Gmail y Nine Work son dos aplicaciones cliente de Exchange ActiveSync (EAS) de Play Store que admiten la configuración con aplicaciones de Android Enterprise.

Intune proporciona plantillas de configuración para aplicaciones de Gmail y Nine Work cuando se administran como aplicaciones de trabajo. Otras aplicaciones de correo electrónico que admiten perfiles de configuración de aplicaciones pueden configurarse con las directivas de configuración de aplicaciones móviles.

Si va a usar el acceso condicional de Exchange ActiveSync en un dispositivo de perfil de trabajo Android Enterprise, puede usar la aplicación de correo electrónico Gmail o Nine Work. También se admite la aplicación Microsoft Outlook para Android o cualquier otra aplicación de correo electrónico que utilice autenticación moderna mediante ADAL. Para obtener más información, consulte [Configuración del correo electrónico en Microsoft Intune](../configuration/email-settings-configure.md).

## <a name="app-protection-policies"></a>Directivas de protección de aplicaciones

Las directivas de protección de aplicaciones que se aplican son totalmente compatibles con el perfil del trabajo y el perfil personal. Puede publicar aplicaciones de línea de negocio en la consola de publicación de aplicaciones de Android en https://play.google.com/apps/publish. Esta consola incluye una opción para convertir las aplicaciones en privadas para su organización. Para más información, vea [Incorporación de una directiva de cumplimiento de dispositivos de perfil de trabajo Android Enterprise en Intune](../protect/compliance-policy-create-android-for-work.md). Para obtener información general sobre las directivas de protección de aplicaciones, consulte [¿Qué son las directivas de protección de aplicaciones?](../apps/app-protection-policy.md).

## <a name="vpn-profiles"></a>Perfiles de VPN

La compatibilidad con VPN es similar a los perfiles de VPN de Android. Android Enterprise dispone de las mismas opciones de configuración básicas y de los mismos proveedores de VPN, aunque con dos diferencias:

- **VPN con ámbito de perfiles de trabajo**: las conexiones VPN se limitan solo a las aplicaciones implementadas en el perfil de trabajo. Solo las aplicaciones administradas con Android Enterprise pueden usar la conexión VPN. Las aplicaciones personales del dispositivo no pueden usar una conexión VPN administrada. Para más información, vea [Configuración de VPN en Android Enterprise](../configuration/vpn-settings-android-enterprise.md).

- **VPN específica de la aplicación**: la VPN específica de la aplicación puede configurarse en Intune si el proveedor VPN admite:
  - la configuración para una VPN específica de la aplicación,
  - la capacidad de configurar la VPN por aplicación mediante el perfil de configuración de la aplicación Android Enterprise.
  Para obtener más información, consulte [Use un perfil personalizado de Microsoft Intune para crear un perfil de VPN por aplicación para dispositivos Android](../configuration/android-pulse-secure-per-app-vpn.md).

## <a name="certificate-profiles"></a>Perfiles de certificado

Las mismas opciones de configuración de perfiles de certificado que están disponibles para la administración de Android están disponibles en dispositivos de perfil de trabajo Android Enterprise. Android Enterprise proporciona API mejoradas de administración de certificados. La administración mejorada de certificados proporciona la funcionalidad siguiente:

- Garantiza la implementación silenciosa y transparente para el usuario.
- Garantiza que los certificados implementados se quitan cuando se retira un dispositivo de Intune y se quita el perfil de trabajo.
- Proporciona mensajería mejorada que informa a los usuarios que el departamento de TI ha implementado y configurado el certificado mediante su servicio de administración.

Para obtener más información, consulte [Configuración de un perfil de certificado para sus dispositivos en Microsoft Intune](../protect/certificates-configure.md).

## <a name="wi-fi-profiles"></a>Perfiles de Wi-Fi

Los perfiles de Wi-Fi administrados con Android Enterprise se quitan cuando el dispositivo se retira de Intune y se elimina el perfil de trabajo. Para obtener más información, consulta [Configuración de Wi-Fi en Microsoft Intune](../configuration/wi-fi-settings-configure.md).

## <a name="next-steps"></a>Pasos siguientes
- [Inscribir dispositivos Android](android-enroll.md)
- [Asignación de aplicaciones para dispositivos de perfil de trabajo Android Enterprise con Intune](../apps/apps-add-android-for-work.md)
