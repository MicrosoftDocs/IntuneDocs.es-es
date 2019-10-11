---
title: Creación de perfiles de dispositivos iOS o Mac OS con Microsoft Intune - Azure |Microsoft Docs
description: Agregue o cree un perfil de dispositivo para iOS o macOS y después configure los valores de AirPrint, diseño de la pantalla principal, notificaciones de aplicaciones, dispositivo compartido, inicio de sesión único y configuración de filtro de contenido web en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83328652c366eea6e1a3cbb81ea4979d8844a96b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724196"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Agregar la configuración de características de dispositivos iOS o Mac OS en Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune incluye muchas características y configuraciones que ayudan a los administradores a controlar dispositivos iOS y macOS. Por ejemplo, los administradores pueden:

- Permitir a los usuarios acceder a impresoras AirPrint en la red
- Agregar aplicaciones y carpetas a la pantalla principal, incluida la incorporación de nuevas páginas
- Elegir si se muestran las notificaciones de aplicación y cómo se muestran
- Configurar la pantalla de bloqueo para mostrar un mensaje o la etiqueta de recurso, especialmente para los dispositivos compartidos
- Proporcionar a los usuarios una experiencia de inicio de sesión único para compartir las credenciales entre aplicaciones
- Filtrar los sitios web que usan el lenguaje para adultos y permitir o bloquear sitios web específicos

Intune usa "perfiles de configuración" para crear y personalizar estas configuraciones para las necesidades de su organización. Después de agregar estas características en un perfil, inserte o implemente el perfil en dispositivos iOS y macOS de la organización.

En este artículo se describen las distintas características que se pueden configurar y se muestra cómo crear un perfil de configuración de dispositivo. También puede ver todas las configuraciones disponibles para dispositivos [iOS](ios-device-features-settings.md) y [macOS](macos-device-features-settings.md).

## <a name="airprint"></a>AirPrint

AirPrint es una característica de Apple que permite a los dispositivos imprimir archivos mediante una red inalámbrica. En Intune, puede agregar información de AirPrint a los dispositivos.

Para una lista de los valores que puede configurar en Intune, consulte [AirPrint en iOS](ios-device-features-settings.md#airprint) y [AirPrint en macOS](macos-device-features-settings.md#airprint).

Para más información sobre AirPrint, consulte [Acerca de AirPrint](https://support.apple.com/HT201311) en el sitio web de Apple.

Se aplica a:

- iOS 7.0 y versiones más recientes
- IPadOS 13.0 y versiones más recientes
- macOS 10.10 y versiones más recientes

## <a name="app-notifications"></a>Notificaciones de la aplicación

Elija cómo las aplicaciones de los dispositivos iOS y iPad reciben notificaciones. Por ejemplo, desde Intune, envíe notificaciones de aplicación para que se muestren en el centro de notificaciones, se muestren en la pantalla de bloqueo o reproduzcan un sonido.

Para una lista de las opciones que puede configurar en Intune, consulte [Notificaciones de la aplicación en iOS](ios-device-features-settings.md#app-notifications).

Para más información sobre esta característica, consulte [Notificaciones](https://developer.apple.com/notifications/) en el sitio web de Apple.

Se aplica a:

- iOS 9.3 y versiones más recientes
- IPadOS 13.0 y versiones más recientes

## <a name="associated-domains"></a>Dominios asociados

Los dominios asociados permiten crear una relación entre los dominios, como `contoso.com` y las aplicaciones. Esta característica permite:

- Compartir datos y credenciales de inicio de sesión entre las aplicaciones y los sitios web de la organización.
- Usar las características de aplicaciones basadas en su sitio web, como la extensión de aplicación de inicio de sesión único, vínculos universales y el relleno automático de contraseñas.

  Por ejemplo, cree un dominio asociado para permitir que el relleno automático de contraseñas recomiende credenciales, como una contraseña, para los sitios web asociados a la aplicación.

Para una lista de los valores que puede configurar en Intune, consulte [Dominios asociados en macOS](macos-device-features-settings.md#associated-domains).

Para más información sobre esta característica, consulte [Configuración de los dominios asociados de una aplicación](https://developer.apple.com/documentation/security/password_autofill/setting_up_an_app_s_associated_domains) en el sitio web de Apple.

Se aplica a:

- macOS 10.15 y versiones más recientes

## <a name="home-screen-layout"></a>Diseño de la pantalla principal

Estas configuraciones definen el diseño de aplicaciones y carpetas en la base y las pantallas principales de los dispositivos iOS e iPadOS. Puede:

- Usar la configuración del **Dock** para agregar aplicaciones o carpetas a la pantalla. Por ejemplo, muestre Safari y la aplicación Mail en el Dock del dispositivo.
- Agregar las **páginas** que quiera que aparezcan en la pantalla principal y las aplicaciones que desee que se muestren en cada página. Por ejemplo, agregue una página **Contoso** y agregue la aplicación de configuración en esta página.

Para una lista de los valores que puede configurar en Intune, consulte [Diseño de la pantalla de inicio en iOS](ios-device-features-settings.md#home-screen-layout).

Se aplica a:

- iOS 9.3 y versiones más recientes
- IPadOS 13.0 y versiones más recientes

## <a name="lock-screen-message"></a>Mensaje de la pantalla de bloqueo

Use esta configuración para mostrar un mensaje o un texto personalizado en la ventana de inicio de sesión y la pantalla de bloqueo. Por ejemplo, puede escribir el mensaje "En caso de pérdida, devolver a..." y mostrar la información sobre la etiqueta del recurso.

Para una lista de los valores que puede configurar en Intune, consulte [Bloqueo de la configuración de mensajes de pantalla en iOS](ios-device-features-settings.md#lock-screen-message).

Para más información sobre el mensaje de la pantalla de bloqueo, consulte [LockScreenMessage](https://developer.apple.com/documentation/devicemanagement/lockscreenmessage) en el sitio web de Apple.

Se aplica a:

- iOS 9.3 y versiones más recientes
- IPadOS 13.0 y versiones más recientes

## <a name="login-items"></a>Elementos de inicio de sesión

Use esta característica para elegir las aplicaciones, las aplicaciones personalizadas, los archivos y las carpetas que se abren cuando los usuarios inician sesión en los dispositivos. 

Para una lista de los valores que puede configurar en Intune, consulte [Elementos de inicio de sesión en macOS](macos-device-features-settings.md#login-items).

Se aplica a:

- macOS 10.13 y versiones más recientes

## <a name="login-window"></a>Ventana de inicio de sesión

Controle la apariencia de la pantalla de inicio de sesión y las funciones disponibles para los usuarios antes de que inicien sesión. Por ejemplo, agregue un banner con un mensaje personalizado, elija si se muestra el botón de suspensión, etc.

Para una lista de los valores que puede configurar en Intune, consulte [Ventana de inicio de sesión en macOS](macos-device-features-settings.md#login-window).

Se aplica a:

- macOS 10.7 y versiones más recientes

## <a name="single-sign-on"></a>Inicio de sesión único

La mayoría de las aplicaciones de línea de negocio (LOB) necesita cierto nivel de autenticación de usuario para ofrecer seguridad. En muchos casos, esta autenticación exige que el usuario escriba las mismas credenciales repetidamente. Para mejorar la experiencia del usuario, los desarrolladores pueden crear aplicaciones que usen el inicio de sesión único (SSO). El uso del inicio de sesión único reduce el número de veces que un usuario debe escribir las credenciales.

Para usar el inicio de sesión único, asegúrese de que tiene:

- Una aplicación programada para buscar el almacén de credenciales del usuario en el inicio de sesión único en el dispositivo.
- Intune configurado para el inicio de sesión único para dispositivos iOS.

![Panel Inicio de sesión único](./media/device-features-configure/sso-blade.png)

Para una lista de los valores que puede configurar en Intune, consulte [Inicio de sesión único en iOS](ios-device-features-settings.md#single-sign-on).

Se aplica a:

- iOS 7.0 y versiones más recientes
- IPadOS 13.0 y versiones más recientes

## <a name="single-sign-on-app-extension"></a>Extensión de aplicación de inicio de sesión único

Estas opciones configuran una extensión de aplicación que habilita el inicio de sesión único (SSO) para los dispositivos iOS, iPados y macOS. La mayoría de las aplicaciones de línea de negocio (LOB) y sitios web de la organización necesitan cierto nivel de autenticación de usuario segura. En muchos casos, la autenticación requiere que los usuarios escriban las mismas credenciales varias veces. El inicio de sesión único proporciona a los usuarios acceso a las aplicaciones y los sitios web después de escribir sus credenciales una vez. Después de iniciar sesión, los usuarios pueden acceder a aplicaciones y sitios web de forma automática, o bien usar Face ID, Touch ID o el código de acceso de Apple para obtener acceso.

En Intune, use esta configuración para definir la extensión de Kerberos integrada de Apple o para configurar una extensión de aplicación de inicio de sesión único creada por su organización. La extensión de la aplicación de inicio de sesión único controla la autenticación de los usuarios. Estas opciones configuran las extensiones de aplicación de inicio de sesión único de tipo credencial, que están diseñadas para flujos de autenticación de desafío y respuesta. Puede elegir entre una extensión de credenciales específicas de Kerberos proporcionada por Apple y una extensión de credenciales genérica.

Para una lista de las opciones que puede configurar en Intune, consulte la [extensión de la aplicación de inicio de sesión único de iOS](ios-device-features-settings.md#single-sign-on-app-extension) y la [extensión de la aplicación de inicio de sesión único de macOS](macos-device-features-settings.md#single-sign-on-app-extension).

Para más información sobre cómo desarrollar una extensión de aplicación de inicio de sesión único, consulte [Extensible Enterprise SSO](https://developer.apple.com/videos/play/tech-talks/301) en el sitio web de Apple.

> [!NOTE]
> La característica de **extensión de la aplicación de inicio de sesión único** es diferente de la característica **Inicio de sesión único**:
>
> - La configuración de la **extensión de la aplicación de inicio de sesión único** se aplica a los dispositivos iPad 13.0 (y versiones más recientes) e iOS 13.0 (y versiones más recientes). La configuración del **inicio de sesión único** se aplica a los dispositivos iPad 13.0 (y versiones más recientes) e iOS 7.0 y versiones más recientes.
> - Una **extensión de la aplicación de inicio de sesión única** controla la autenticación con el sistema operativo. En el **inicio de sesión único**, una aplicación específica controla la autenticación.
> - Al usar la **extensión de la aplicación de inicio de sesión único**, los usuarios inician sesión en aplicaciones y sitios web de forma silenciosa, o con Face ID, Touch ID o el código PIN o el código de acceso de Apple. Cuando se usa el **inicio de sesión único**, los usuarios inician sesión en aplicaciones y sitios web con otra aplicación.
>
>    La **extensión de la aplicación de inicio de sesión único** usa el sistema operativo Apple para autenticarse. Por lo tanto, puede proporcionar una mejor experiencia de usuario final.
>
> - Desde la perspectiva del desarrollo, la **extensión de la aplicación de inicio de sesión única** puede usar cualquier tipo de autenticación de inicio de sesión único de credenciales. Con el **inicio de sesión único**, solo puede usar la autenticación de inicio de sesión único de Kerberos.  

Se aplica a:

- iOS 13.0 y versiones más recientes
- IPadOS 13.0 y versiones más recientes
- macOS 10.15 y versiones más recientes

## <a name="wallpaper"></a>Fondo de pantalla

Agregue una imagen .png, .jpg o .jpeg personalizada a los dispositivos iOS supervisados. Por ejemplo, use Intune para agregar un logotipo de empresa a la pantalla de bloqueo de los dispositivos.

Para una lista de los valores que puede configurar en Intune, consulte [Papeles en iOS](ios-device-features-settings.md#wallpaper).

Se aplica a:

- iOS
- IPadOS 13.0 y versiones más recientes

## <a name="web-content-filter"></a>Filtro de contenido web

Esta configuración puede usar el algoritmo de Autofiltro integrado de Apple para evaluar páginas web y bloquear el contenido para adultos y el idioma para adultos. También puede crear una lista de vínculos web permitidos y vínculos web restringidos. Por ejemplo, puede permitir que se abran solo los sitios web de `contoso`.

Para una lista de los valores que puede configurar en Intune, consulte [Filtro de contenido web en iOS](ios-device-features-settings.md#web-content-filter).

Se aplica a:

- iOS 7.0 y versiones más recientes
- IPadOS 13.0 y versiones más recientes

## <a name="create-a-device-profile"></a>Creación del perfil de un dispositivo

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre descriptivo para la directiva. Asígnele un nombre a las directivas para que pueda identificarlas de manera sencilla más adelante. Por ejemplo, un nombre de directiva válido es **macOS: Configura la pantalla de inicio de sesión**.
    - **Descripción**: escriba una descripción para el perfil. Esta configuración es opcional pero recomendada.
    - **Plataforma**: seleccione la plataforma de los dispositivos. Las opciones son:  
        - **iOS/iPadOS**
        - **macOS**
    - **Tipo de perfil**: seleccione **Características del dispositivo**.

4. Dependiendo de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. Elija la plataforma para la configuración detallada:

    - [iOS/iPadOS](ios-device-features-settings.md)
    - [macOS](macos-device-features-settings.md)

5. Cuando haya terminado, seleccione **Aceptar** > **Crear** para guardar los cambios.

El perfil se crea y se muestra en la lista de perfiles. Asegúrese de [asignar el perfil](device-profile-assign.md) y [supervise su estado](device-profile-monitor.md).

## <a name="next-steps"></a>Pasos siguientes

Una vez creado el perfil, está listo para asignarlo. Después, [asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

Ver todas las configuraciones de características de dispositivo para dispositivos [iOS](ios-device-features-settings.md) y [macOS](macos-device-features-settings.md).
