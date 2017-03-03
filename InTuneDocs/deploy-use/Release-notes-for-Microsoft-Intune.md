---
title: "Notas de la versión para Microsoft Intune | Microsoft Docs"
description: "Notas de la versión de Intune"
keywords: 
author: Staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: fd300a5dfe6d6976491988453ec69e99668889fb


---

# <a name="release-notes-for-microsoft-intune"></a>Notas de la versión para Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune es una solución de administración cliente integrada y basada en la nube que proporciona herramientas, informes y licencias de actualización para la versión más reciente de Windows. También ayuda a mantener sus equipos actualizados y seguros. Asimismo, Intune permite administrar dispositivos móviles en la red por medio de Exchange ActiveSync o directamente con Intune. En las siguientes notas de la versión se describen información importante y problemas conocidos de Microsoft Intune.


## <a name="android-users-cant-send-email-when-conditional-access-for-exchange-online-is-implemented"></a>Los usuarios de Android no pueden enviar correo electrónico cuando el acceso condicional para Exchange Online está implementado

**Problema**: Los usuarios que ejecutan Samsung Android 5.1.1 y versiones superiores en sus dispositivos no pueden enviar correo electrónico cuando se ha configurado el acceso condicional para Exchange Online. Samsung reconoce que el problema está en su cliente de correo electrónico integrado en Android 5.1.1 y versiones superiores, y que está buscando una solución.

**Solución alternativa 1:** aconseje a los usuarios finales que usen la aplicación Outlook para Android.

**Solución alternativa 2:** para permitir que los usuarios afectados envíen correo electrónico, puede seguir estos pasos:

1. Coloque cada usuario afectado en un grupo de seguridad de la sección "grupos exentos" de la directiva de acceso condicional para Exchange Online.
2. Deje que el usuario sincronice temporalmente el correo electrónico en el cliente de correo electrónico integrado.
3. Quite al usuario afectado del grupo exento y confirme que ya puede enviar correo electrónico.

Microsoft seguirá trabajando estrechamente con Samsung para corregir le problema o para encontrar otras soluciones.



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

**Solución:** vaya a la ubicación donde instaló la herramienta y elimine el directorio. La ubicación de instalación predeterminada es: **C:\Archivos de programa (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**. Para más información sobre la herramienta de ajuste de aplicaciones, consulte [Preparar aplicaciones Android para la administración de aplicaciones móviles con la Herramienta de ajuste de aplicaciones de Intune](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## <a name="remote-assistance-is-not-available-on-computers-that-run-windows-8-or-windows-81"></a>La asistencia remota no está disponible en equipos que ejecutan Windows 8 o Windows 8.1
**Problema:** en esta versión, la característica de asistencia remota no está disponible en equipos que ejecutan Windows 8 o Windows 8.1.

**Solución:** ninguna

## <a name="alert-notifications-for-recipients-that-are-automatically-added-might-not-work"></a>Es posible que las notificaciones de alerta para destinatarios que se han agregado automáticamente no funcionen.
**Problema:** Si un destinatario se agregó automáticamente a una notificación de alerta, es posible que no siempre reciba una notificación.

**Solución alternativa:** Para asegurarse de que los destinatarios reciban la notificación de mensaje, debe agregar manualmente los destinatarios a las notificaciones de alerta.

## <a name="language-support-in-the-azure-portal"></a>Compatibilidad de idioma en Azure Portal
Azure Portal admite los siguientes idiomas: alemán, checo, chino (simplificado), chino (tradicional), coreano, español, francés, húngaro, inglés, italiano, japonés, neerlandés, polaco, portugués (Brasil), portugués (Portugal), ruso, sueco y turco.

La consola de administración de Intune y las experiencias móviles de usuario admiten danés, finés, griego, noruego y rumano, además de todos los idiomas admitidos en Azure Portal.



<!--HONumber=Dec16_HO2-->


