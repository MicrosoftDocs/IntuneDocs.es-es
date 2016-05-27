---
# required metadata

title: Notas de la versión para Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Notas de la versión para Microsoft Intune
Microsoft Intune es una solución de administración cliente integrada y basada en la nube que proporciona herramientas, informes y licencias de actualización para la versión más reciente de Windows. Además, ayuda a mantener los equipos actualizados y seguros. Asimismo, Intune permite administrar dispositivos móviles en la red por medio de Exchange ActiveSync o directamente con Intune. En las siguientes notas de la versión se describen información importante y problemas conocidos de Microsoft Intune.


## Los usuarios de Android no pueden enviar correo electrónico cuando el acceso condicional para Exchange Online está implementado

Los usuarios que ejecutan Samsung Android 5.1.1 y superior en sus dispositivos no pueden enviar correo electrónico cuando se ha configurado el acceso condicional para Exchange Online. Samsung reconoce que el problema está en su cliente de correo integrado en Android 5.1.1 y superior y que está buscando una solución.

**Solución 1:** aconseje a los usuarios finales que usen la aplicación Outlook para Android.

**Solución 2:** para permitir que los usuarios afectados envíen correo electrónico, puede seguir estos pasos:

1. Coloque al usuario afectado en un grupo de seguridad de la sección "grupos exentos" de la directiva de acceso condicional para Exchange Online.
2. Permita que el usuario sincronice temporalmente el correo electrónico en el cliente de correo electrónico integrado.
3. Quite al usuario afectado del grupo exento y confirme que ya puede enviar correo electrónico.

Microsoft seguirá trabajando estrechamente con Samsung para corregir le problema o para encontrar otras soluciones.



## Se puede producir un error al cambiar los perfiles de acceso de recursos entre grupos para iOS y Android
**Problema:** cuando se cambian los perfiles de acceso de recursos de correo electrónico o de Protocolo de inscripción de certificados Simple (SCEP) entre grupos, los perfiles pueden entrar en conflicto y producirse un error. Por ejemplo, digamos que dispone de un perfil de correo electrónico existente que apunta al servidor de Exchange local, dirigido al grupo A, y que entonces crea un nuevo perfil de correo electrónico que apunta a Exchange Online, dirigido al grupo B. Al mover usuarios del grupo A al B, los dispositivos conservarán el perfil de correo electrónico de Exchange local e intentarán instalar el perfil de correo electrónico de Exchange Online destinado al grupo B.

En este punto se produce uno de los siguientes casos: 
* Si los perfiles de correo electrónico A y B son idénticos, el dispositivo rechaza el perfil de correo electrónico B porque ya contiene el perfil de correo electrónico A.
* Si el perfil de correo electrónico A es diferente al perfil de correo electrónico B, como se menciona en el ejemplo anterior, el dispositivo termina con dos perfiles de correo electrónico.

**Nota:** El nombre de host y el atributo usados para el nombre de usuario se comprueban para distinguir un perfil de correo electrónico del otro.

En ambos casos, el perfil de acceso de recursos (perfil de correo electrónico) no se ha quitado del dispositivo para evitar la eliminación accidental del acceso de un usuario al correo electrónico o al certificado SCEP del cliente.

**Solución:** ninguna

## Cuando inscribe un dispositivo Windows 8.1 que debe autenticarse en un servidor proxy, el proceso de inscripción produce un error sin ninguna indicación visible sobre la causa del error
**Problema:** cuando se inscribe un dispositivo de Windows 8.1 y este se debe autenticar en un servidor proxy durante el proceso de inscripción, se produce un error en la inscripción si el dispositivo no ha almacenado en caché las credenciales del servidor proxy. Cuando las credenciales del servidor proxy no están almacenadas en la caché del dispositivo, el proceso de inscripción debe esperar a que el usuario escriba las credenciales. Sin embargo, no se muestra ningún mensaje para proporcionar las credenciales del servidor proxy durante el proceso de inscripción. El resultado es que el proceso de inscripción no se puede autenticar en el servidor proxy y no se envía ninguna indicación visible de este error al usuario.

**Solución:** en los dispositivos de Windows 8.1 que deban inscribirse en una red que exija el uso de un servidor proxy autenticado, configure y guarde las credenciales del servidor proxy antes de inscribir el dispositivo. Para configurar y guardar las credenciales en un dispositivo con Windows 8.1:

1.  En el dispositivo con Windows 8.1 , abra **Internet Explorer**..

2.  Cuando se le pidan las credenciales del servidor proxy, escríbalas y seleccione la opción **Recordar mis credenciales**..

3.  Inscriba el dispositivo.

## Los dispositivos Windows Phone 8.1 no podrán inscribirse en Microsoft Intune cuando la autenticación de dispositivo está habilitada en AD FS
**Problema:** si inscribe un dispositivo de Windows Phone 8.1, la inscripción generará un error si la configuración opcional de autenticación de dispositivos está habilitada como parte de la directiva de autenticación global en los Servicios de federación de Active Directory (AD FS).

**Solución:** deshabilite la autenticación de dispositivos en el servidor de AD FS; para ello, desactive **Habilitar autenticación de dispositivos** en **Editar directiva de autenticación global**. Para obtener más información, consulte [Configuración de directivas de autenticación](http://technet.microsoft.com/library/dn486781.aspx)


## La herramienta de ajuste de aplicaciones de Microsoft Intune para Android no presenta ninguna capacidad de desinstalación integrada
**Problema:** la **Herramienta de ajuste de aplicaciones de Microsoft para Android** no tiene funciones integradas para desinstalar la herramienta.

**Solución:** vaya a la ubicación donde instaló la herramienta y elimine el directorio. La ubicación de instalación predeterminada es: **C:\Archivos de programa (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**. Para obtener más información sobre la herramienta de ajuste de aplicaciones, consulte [Prepare Android apps for management with App Wrapping Tool](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool) (Preparar aplicaciones de Android para la administración con la Herramienta de ajuste de aplicaciones)..

## La asistencia remota no está disponible en equipos que ejecutan Windows 8 o Windows 8.1
**Problema:** en esta versión, la característica de asistencia remota no está disponible en equipos que ejecutan Windows 8 o Windows 8.1.

**Solución:** ninguna

## Es posible que las notificaciones de alerta para destinatarios que se han agregado automáticamente no funcionen
**Problema:** Si un destinatario se agregó automáticamente a una notificación de alerta, es posible que no siempre reciba una notificación.

**Solución alternativa:** Para asegurarse de que los destinatarios reciban la notificación de mensaje, debe agregar manualmente los destinatarios a las notificaciones de alerta.

## Compatibilidad de idioma en el Portal de vista previa de Azure
El Portal de vista previa de Azure se basa en una nueva plataforma y admite los siguientes idiomas: alemán, checo, chino (simplificado), chino (tradicional), coreano, español, francés, húngaro, inglés, italiano, japonés, neerlandés, polaco, portugués (Brasil), portugués (Portugal), ruso, sueco y turco.

La consola de administración de Intune y las experiencias móviles de usuario admiten danés, finés, griego, noruego y rumano, además de todos los idiomas admitidos en el Portal de vista previa de Azure.


<!--HONumber=May16_HO1-->


