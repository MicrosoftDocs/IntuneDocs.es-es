---
title: Directivas de dispositivo, perfiles y preguntas y respuestas con Intune - Azure | Microsoft Docs
description: Obtenga información sobre las distintas directivas y perfiles que se pueden usar en Microsoft Intune, incluidas las directivas para configurar dispositivos, obtener acceso a recursos de la empresa, habilitar el acceso condicional e inscribir dispositivos corporativos. Además, obtenga respuestas a las preguntas frecuentes.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ROBOTS: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 3b1115a91707c639caba6410ace3c2e255e40a39
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185005"
---
# <a name="manage-settings-and-features-on-your-devices-with-intune-policies"></a>Administrar la configuración y las características de los dispositivos con directivas de Intune

Las *directivas* de Microsoft Intune son grupos de configuraciones que controlan características en equipos y dispositivos móviles. Las directivas se crean mediante plantillas que incluyen configuraciones recomendadas o personalizadas. Después, se implementan en grupos de usuarios o dispositivos.

## <a name="types-of-policies"></a>Tipos de directivas

Las directivas de Intune se dividen en las siguientes categorías. La categoría que se usa afecta a la manera de crear e implementar la directiva.

- **Directivas de configuración:** normalmente se usan para administrar las características y la configuración de seguridad en los dispositivos, incluido el acceso a los recursos de la empresa. Comience a usar los [perfiles de dispositivo de Intune](device-profiles.md).
- **Directivas de cumplimiento de los dispositivos**: definen las reglas y los valores de configuración que un dispositivo debe cumplir para que se considere conforme a las directivas de acceso condicional. Las directivas de cumplimiento también se pueden usar para supervisar y corregir problemas de compatibilidad con dispositivos independientes del acceso condicional. Introducción a [las directivas de cumplimiento de dispositivos](device-compliance-get-started.md).
- **Directivas de acceso condicional:** ayudan a proteger el correo electrónico y otros servicios, en función de las condiciones que escriba. [¿Qué es el acceso condicional?](conditional-access.md) y [¿Cuáles son las formas habituales de usar el acceso condicional con Intune?](conditional-access-intune-common-ways-use.md) son buenos recursos para empezar a trabajar.
- **Directivas de inscripción de dispositivos corporativos**: para obtener información sobre las directivas de inscripción de dispositivos corporativos, vea [Inscripción de dispositivos iOS en Intune](ios-enroll.md).

## <a name="frequently-asked-questions-about-intune-policies"></a>Preguntas más frecuentes sobre las directivas de Intune

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-being-deployed"></a>¿Cuánto tiempo tardan los dispositivos móviles en obtener directivas o aplicaciones una vez implementados?
Cuando se implementa una directiva o aplicación, Intune empieza inmediatamente a notificar al dispositivo que se conecte con el servicio de Intune. Este paso suele tardar menos de cinco minutos.

Si un dispositivo no se conecta para recibir la directiva una vez enviada la primera notificación, Intune hace tres intentos más.  Si el dispositivo está sin conexión (por ejemplo, está apagado o no está conectado a una red), es posible que no reciba las notificaciones. En ese caso, el dispositivo obtiene la directiva en la próxima conexión programada con el servicio Intune, como se indica a continuación:

| Plataforma | Frecuencia de inserción en el repositorio |
| --- | --- |
| iOS | Cada 6 horas | 
| Mac OS X | Cada 6 horas |
| Android | Cada 8 horas | 
| Windows Phone | Cada 8 horas | 
| Windows 8.1  | Cada 8 horas |  
| Equipos Windows 10 inscritos como dispositivos | Cada 8 horas | 

Si el dispositivo se ha inscrito recientemente, la frecuencia de inserción en el repositorio es más frecuente, como se indica a continuación:

| Plataforma | Frecuencia |
| --- | --- |
| iOS | Cada 15 minutos durante 6 horas y, después, cada 6 horas |  
| Mac OS X | Cada 15 minutos durante 6 horas y, después, cada 6 horas | 
| Android | Cada 3 minutos durante 15 minutos y, después, cada 15 minutos durante 2 horas y, después cada 8 horas | 
| Windows Phone | Cada 5 minutos durante 15 minutos y, después, cada 15 minutos durante 2 horas y, después cada 8 horas | 
| Equipos Windows inscritos como dispositivos | Cada 3 minutos durante 30 minutos y, después, cada 8 horas | 

Los usuarios también pueden abrir la aplicación del Portal de empresa y sincronizar el dispositivo para buscar la directiva inmediatamente en cualquier momento.

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>¿Qué acciones provocan que Intune envíe inmediatamente una notificación a un dispositivo?
Los dispositivos se insertan en el repositorio con Intune cuando reciben una notificación que se lo indica o durante la conexión programada periódicamente.  Cuando el destino es un dispositivo o usuario con una acción como un borrado, bloqueo, restablecimiento de código de acceso, implementación de aplicaciones, implementación de perfiles (Wi-Fi, VPN, correo electrónico) o implementación de directivas, Intune comienza inmediatamente a intentar notificar al dispositivo que debe conectarse al servicio Intune.

Otros cambios, como la revisión de la información de contacto del Portal de empresa, no provocan una notificación inmediata a los dispositivos.

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-are-applied"></a>Si se implementan varias directivas en el mismo usuario o dispositivo, ¿cómo puedo saber qué configuración se aplica?
Cuando se aplican dos o más directivas al mismo usuario o dispositivo, la evaluación de la configuración que se aplica se hace por cada parámetro:

- La configuración de directivas de cumplimiento siempre tiene prioridad respecto a la configuración de directivas de configuración.

- La configuración de directivas de cumplimiento más restrictivas se aplica si se evalúan con la misma configuración en otra directiva de cumplimiento.

- Si una opción de la directiva de configuración entra en conflicto con una opción de otra directiva de configuración, este conflicto se muestra en Intune. Resuelva estos conflictos de forma manual.

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-applies-to-the-app"></a>¿Qué sucede cuando las directivas de administración de aplicaciones móviles entran en conflicto entre sí? ¿Cuál se aplica a la aplicación?
Los valores en conflicto son la configuración más restrictiva disponible en una directiva de MAM, excepto para los campos de entrada de números (como intentos de PIN antes del restablecimiento).  Los campos de entrada de números se definen con los mismos valores que si crease una directiva de MAM en la consola con la opción de configuración recomendada.

Se producen conflictos cuando dos configuraciones de directiva son iguales.  Por ejemplo, si configura dos directivas MAM que son idénticas, salvo por la configuración de copiar y pegar.  En este escenario, la configuración de copiar y pegar se define con el valor más restrictivo, pero el resto de los parámetros se aplican según la configuración.

Si una directiva se implementa en la aplicación y surte efecto, y después se implementa una segunda, la primera tiene precedencia y se aplica. La segunda directiva presentará un conflicto. Si se aplican al mismo tiempo, lo que significa que no hay ninguna directiva anterior, ambas están en conflicto. Cualquier configuración en conflicto se establece en los valores más restrictivos.

### <a name="what-happens-when-ios-custom-policies-conflict"></a>¿Qué sucede cuando hay un conflicto de directivas personalizadas de iOS?
Intune no evalúa la carga de archivos de configuración de Apple ni directivas personalizadas de identificador uniforme de recursos de Open Mobile Alliance (OMA-URI). Sencillamente, se usa como mecanismo de entrega.

Al implementar una directiva personalizada, confirme que los valores configurados no entran en conflicto con las directivas de cumplimiento, configuración o personalizadas. Si una directiva personalizada con parámetros entra en conflicto, el orden en que se aplican es aleatorio.

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>¿Qué ocurre cuando se elimina una directiva o deja de ser aplicable?
Al eliminar una directiva, o bien al quitar un dispositivo de un grupo que tiene una directiva implementada, se quitan la directiva y la configuración del dispositivo según las listas siguientes.

#### <a name="enrolled-devices"></a>Dispositivos inscritos

- Perfiles de correo electrónico, certificado, VPN y Wi-Fi: estos perfiles se quitan de todos los dispositivos inscritos admitidos.
- Todos los demás tipos de directivas:
  - **Dispositivos Windows y Android**: la configuración no se quita del dispositivo.
  - **Dispositivos Windows Phone 8.1**: se quitan las opciones siguientes:
    - Requerir una contraseña para desbloquear dispositivos móviles
    - Permitir contraseñas sencillas
    - Longitud mínima de la contraseña
    - Tipo de contraseña obligatoria
    - Expiración de contraseña (días)
    - Recordar el historial de contraseñas
    - Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo
    - Minutos de inactividad antes de que se pida la contraseña
    - Tipo de contraseña requerida: número mínimo de conjuntos de caracteres
    - Permitir cámara
    - Requerir cifrado en dispositivo móvil
    - Permitir almacenamiento extraíble
    - Permitir explorador web
    - Permitir almacén de aplicaciones
    - Permitir captura de pantalla
    - Permitir geolocalización
    - Permitir cuenta de Microsoft
    - Permitir copiar y pegar
    - Permitir Wi-Fi Tethering
    - Permitir la conexión automática a zonas Wi-Fi gratuitas
    - Permitir informar de zonas Wi-Fi
    - Permitir borrado
    - Permitir Bluetooth
    - Permitir NFC
    - Permitir Wi-Fi

  - **iOS**: se quitan todas las configuraciones, excepto:
    - Permitir itinerancia de voz
    - Permitir itinerancia de datos
    - Permitir la sincronización automática en itinerancia

### <a name="where-can-i-find-help-troubleshooting-policies"></a>¿Dónde puedo encontrar ayuda para solucionar problemas en las directivas?

Vea [Solucionar problemas de directivas](troubleshoot-policies-in-microsoft-intune.md).
