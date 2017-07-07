---
title: "Notas de la versión para Microsoft Intune"
description: "Notas de la versión de Intune"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 751bd0bc90b762c5b51b85fae2129e53773b54fe
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="release-notes-for-microsoft-intune"></a>Notas de la versión para Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune es una solución de administración cliente integrada y basada en la nube que proporciona herramientas, informes y licencias de actualización para la versión más reciente de Windows. También ayuda a mantener sus equipos actualizados y seguros. Asimismo, Intune permite administrar dispositivos móviles en la red por medio de Exchange ActiveSync o directamente con Intune. En las siguientes notas de la versión se describen información importante y problemas conocidos de Microsoft Intune.

<!-- 3-6-17: customer asked if this is still current; Stacie asked Chris Baldwin about it. Chris said it's a Samsung issue, but that he hasn't heard any reports about it for months, so he suggested that I share that with the customer and remove this item from the release notes. I'm only going to comment it out in case it resurfaces.
## Android users can’t send email when conditional access for Exchange Online is implemented

**Issue:** Users running Samsung Android 5.1.1 and later on their devices can't send email when conditional access for Exchange Online has been set up. Samsung acknowledges that the issue is in its built-in email client in Android 5.1.1 and later, and is investigating a fix.

**Workaround 1:** Advise users to use the Outlook app for Android.

**Workaround 2:** To let affected users send email, you can follow these steps:

1. Put each affected user in a security group in the “exempted groups” section of the conditional access policy for Exchange Online.
2. Let the user temporarily sync email on the built-in email client.
3. Remove the affected user from the exempted group, and confirm that the user can now send email.

Microsoft will continue to work closely with Samsung on a fix or additional workarounds.
-->


## <a name="changing-resource-access-profiles-between-groups-for-ios-and-android-might-fail"></a>Se puede producir un error al cambiar los perfiles de acceso de recursos entre grupos para iOS y Android
**Problema:** cuando se cambian los perfiles de acceso de recursos de correo electrónico o de Protocolo de inscripción de certificados Simple (SCEP) entre grupos, los perfiles pueden entrar en conflicto y producirse un error. Por ejemplo, digamos que dispone de un perfil de correo electrónico existente que apunta al servidor de Exchange local, dirigido al grupo A. Entonces crea un nuevo perfil de correo electrónico que apunta a Exchange Online, dirigido al grupo B. Al mover usuarios del grupo A al B, los dispositivos conservarán el perfil de correo electrónico de Exchange local e intentarán instalar el perfil de correo electrónico de Exchange Online destinado al grupo B.

En este punto se produce uno de los siguientes casos: 
* Si los perfiles de correo electrónico A y B son idénticos, el dispositivo rechaza el perfil de correo electrónico B porque ya contiene el perfil de correo electrónico A.
* Si el perfil de correo electrónico A es diferente al perfil de correo electrónico B, como se menciona en el ejemplo, el dispositivo termina con dos perfiles de correo electrónico.

> [!NOTE]
> El nombre de host y el atributo usados para el nombre de usuario se comprueban para distinguir un perfil de correo electrónico del otro.

En ambos casos, el perfil de acceso de recursos (perfil de correo electrónico) no se ha quitado del dispositivo para evitar la eliminación accidental del acceso de un usuario al correo electrónico o al certificado SCEP del cliente.

**Solución:** ninguna

## <a name="when-you-enroll-a-windows-81-device-that-must-authenticate-to-a-proxy-server-the-enrollment-process-fails-with-no-visible-cause"></a>Cuando inscribe un dispositivo Windows 8.1 que debe autenticarse en un servidor proxy, el proceso de inscripción produce un error sin ninguna causa visible
**Problema:** cuando se inscribe un dispositivo de Windows 8.1 y este se debe autenticar en un servidor proxy durante el proceso de inscripción, se produce un error en la inscripción si el dispositivo no ha almacenado en caché las credenciales del servidor proxy. Cuando las credenciales del servidor proxy no están almacenadas en la caché del dispositivo, el proceso de inscripción debe esperar a que el usuario escriba las credenciales. Sin embargo, no se muestra ningún mensaje para proporcionar las credenciales del servidor proxy durante el proceso de inscripción. El resultado es que el proceso de inscripción no puede autenticarse en el servidor proxy. Ninguna indicación visible de este error se presenta al usuario.

**Solución alternativa:** en los dispositivos de Windows 8.1 que deban inscribirse en una red que exija el uso de un servidor proxy autenticado, configure y guarde las credenciales del servidor proxy antes de inscribir el dispositivo. Para configurar y guardar las credenciales en un dispositivo con Windows 8.1:

1.  En el dispositivo con Windows 8.1, abra Internet Explorer.
2.  Cuando se le pidan las credenciales del servidor proxy, escríbalas y, a continuación, elija la opción **Recordar mis credenciales**.
3.  Inscriba el dispositivo.

## <a name="windows-phone-81-devices-fail-to-enroll-with-microsoft-intune-when-device-authentication-is-enabled-in-ad-fs"></a>Los dispositivos Windows Phone 8.1 no podrán inscribirse en Microsoft Intune cuando la autenticación de dispositivo está habilitada en AD FS
**Problema:** si inscribe un dispositivo de Windows Phone 8.1, la inscripción generará un error si la configuración opcional de autenticación de dispositivos está habilitada como parte de la directiva de autenticación global en los Servicios de federación de Active Directory (AD FS).

**Solución:** deshabilite la autenticación de dispositivos en el servidor de AD FS; para ello, desactive **Habilitar autenticación de dispositivos** en **Editar directiva de autenticación global**. Para más información, consulte [Configuración de directivas de autenticación](http://technet.microsoft.com/library/dn486781.aspx).


## <a name="microsoft-intune-app-wrapping-tool-for-android-has-no-built-in-uninstall-capability"></a>La herramienta de ajuste de aplicaciones de Microsoft Intune para Android no presenta ninguna capacidad de desinstalación integrada
**Problema:** la **Herramienta de ajuste de aplicaciones de Microsoft para Android** no tiene funciones integradas para desinstalar la herramienta.

**Solución:** vaya a la ubicación donde instaló la herramienta y elimine el directorio. La ubicación de instalación predeterminada es: **C:\Archivos de programa\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool. Para más información sobre la herramienta de ajuste de aplicaciones, consulte [Preparar aplicaciones Android para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune](/intune/app-wrapper-prepare-android).

## <a name="remote-assistance-is-not-available-on-computers-that-run-windows-8-or-windows-81"></a>La asistencia remota no está disponible en equipos que ejecutan Windows 8 o Windows 8.1
**Problema:** en esta versión, la característica de asistencia remota no está disponible en equipos que ejecutan Windows 8 o Windows 8.1.

**Solución:** ninguna

## <a name="alert-notifications-for-recipients-that-are-automatically-added-might-not-work"></a>Es posible que las notificaciones de alerta para destinatarios que se han agregado automáticamente no funcionen.
**Problema:** Si un destinatario se agregó automáticamente a una notificación de alerta, es posible que no siempre reciba una notificación.

**Solución alternativa:** Para asegurarse de que los destinatarios reciban la notificación de mensaje, debe agregar manualmente los destinatarios a las notificaciones de alerta.

## <a name="language-support-in-the-azure-portal"></a>Compatibilidad de idioma en Azure Portal
Azure Portal admite los siguientes idiomas: alemán, checo, chino (simplificado), chino (tradicional), coreano, español, francés, húngaro, inglés, italiano, japonés, neerlandés, polaco, portugués (Brasil), portugués (Portugal), ruso, sueco y turco.

La consola de administración de Intune y las experiencias móviles de usuario admiten danés, finés, griego, noruego y rumano, además de todos los idiomas admitidos en Azure Portal.
