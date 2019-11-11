---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3720b0b9a67f0c3462993feef4162ef35f7f3f92
ms.sourcegitcommit: d1b36501186e867355843ddd67c795ade800b76a
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182926"
---
# <a name="in-development-for-microsoft-intune---november-2019"></a>En desarrollo para Microsoft Intune: noviembre de 2019

Para ayudarle con la preparación y planeación, en esta página se enumeran las actualizaciones y características de la interfaz de usuario de Intune que están en desarrollo, pero que aún no se han publicado. Además de la información de esta página:

- Si prevemos que tendrá que tomar medidas antes de realizar un cambio, haremos una publicación complementaria en el Centro de mensajes de Office.
- Cuando una característica [entra en producción](whats-new.md), ya sea una vista previa o disponible con carácter general, la descripción de la característica pasará de esta página a las novedades.
- Esta página y la página [Novedades](whats-new.md) se actualizan periódicamente. Compruebe si hay actualizaciones adicionales.
- Consulte el [plan de desarrollo de Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para conocer los plazos de tiempo y los productos estratégicos.

> [!NOTE]
> Esta página refleja nuestras expectativas actuales sobre las funcionalidades de Intune en una versión futura. Las fechas y las características individuales pueden cambiar. En esta página no se describen todas las características de desarrollo.

**Fuente RSS**: para recibir notificaciones cuando esta página se actualice, copie y pegue la dirección URL siguiente en el lector de fuentes: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Administración de aplicaciones

### <a name="smime-support-for-microsoft-outlook-mobile----2669398----"></a>Compatibilidad con S/MIME para Microsoft Outlook Mobile <!-- 2669398  -->
Intune admitirá la entrega de certificados de cifrado y firma S/MIME que se pueden usar con Outlook Mobile en iOS y Android. Para obtener información relacionada, consulte [configuración de correo electrónico para dispositivos iOS](~/configuration/email-settings-ios.md) y [configuración de correo electrónico para dispositivos Android](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications----4736278----"></a>Compatibilidad con la configuración personalizada para aplicaciones macOS <!-- 4736278  -->
Intune será compatible con la configuración personalizada, lo que le permite agregar claves y valores específicos a un archivo de lista de propiedades de preferencias (. plist) existente para configurar las aplicaciones de macOS y el dispositivo. No todas las aplicaciones admiten preferencias administradas y, en algunos casos, solo se puede administrar la configuración específica. La configuración se implementa solo a través del canal de dispositivo. Solo debe cargar los archivos de lista de propiedades o los archivos. XML que tienen como destino la configuración de canal de dispositivo.

### <a name="assignment-type-value-in-windows-company-portal----5459950----"></a>Valor de tipo de asignación en Windows Portal de empresa <!-- 5459950  -->
Se actualizará la página **aplicaciones instaladas** de la aplicación de portal de empresa de Windows. La columna **tipo de asignación** de la página **aplicaciones instaladas** se ha actualizado para que se llame "requerido por su organización". Los valores posibles son **sí** o **no** para designar las aplicaciones necesarias y las disponibles. Este cambio se realiza en respuesta a alguna confusión del usuario final. Para obtener más información sobre el Portal de empresa de Windows, vea [Configuración de la aplicación Portal de empresa de Microsoft Intune](~/apps/company-portal-app.md).

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Ejecutar aplicaciones Win32 en dispositivos Windows 10 en modo S <!-- 3747604  --> 
Podrá instalar y ejecutar aplicaciones de Win32 en dispositivos administrados en modo Windows 10 S. Cree una o varias directivas complementarias para el modo S mediante las herramientas de PowerShell de Windows Defender Application control (WDAC). Use el portal de firma de Device Guard para firmar las directivas complementarias. Después, cargue y distribuya las directivas a través de Intune. 

En Intune, encontrará esta funcionalidad seleccionando **aplicaciones cliente**  > **directivas complementarias de Windows 10 S**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Establecer la disponibilidad de la aplicación en función de una fecha y hora <!-- 3510685  -->
Como administrador, podrá configurar la hora de inicio y la fecha límite para una aplicación requerida. A la hora de inicio, la extensión de administración de Intune descargará el contenido de la aplicación y lo almacenará en la memoria caché. La aplicación se instalará en el momento de la fecha límite. En el caso de las aplicaciones disponibles, la hora de inicio se determinará cuando la aplicación esté visible en Portal de empresa. 

Para establecer la disponibilidad de la aplicación en función de la fecha y la hora:

1. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones**. 
1. Seleccione una aplicación de la lista o agregue una nueva seleccionando **Agregar**. 
1. En la hoja de la aplicación, seleccione **asignaciones** > **Agregar grupo**. 
1. Establezca el **tipo de asignación** en **requerido** y, a continuación, seleccione **grupos incluidos**. 
1. Establezca **que esta aplicación sea necesaria para todos los usuarios** como **sí**. 
1. Seleccione **Editar** para modificar las opciones de **experiencia del usuario final** . 
1. En la hoja **experiencia del usuario final** , establezca la **hora disponible del software** según sea necesario. 

Para más información, vea [Agregar aplicaciones a Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Requerir que las aplicaciones Win32 se reinicien <!-- 3136567  -->
Podrá solicitar una aplicación Win32 para que se reinicie después de una instalación correcta. Puede elegir la cantidad de tiempo (el período de gracia) antes del reinicio.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Mostrar notificaciones para la aplicación Portal de empresa en Windows <!-- 1808082  -->
Actualizaremos la aplicación Portal de empresa en dispositivos Windows para mostrar las notificaciones del sistema a los usuarios, incluso cuando la aplicación está cerrada. La actualización mostrará las notificaciones de las aplicaciones disponibles solo cuando el estado de la instalación sea completado o erróneo. La aplicación Portal de empresa no mostrará notificaciones de las aplicaciones necesarias.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>Mostrar mensajes de estado de instalación de la aplicación Portal de empresa <!-- 2514416  -->
La aplicación Portal de empresa mostrará mensajes de estado de instalación de aplicaciones adicionales a los usuarios finales. Las condiciones siguientes se aplicarán a las nuevas características de dependencia de Win32:
- No se pudo instalar la aplicación. No se cumplieron las dependencias definidas por el administrador.
- La aplicación se instaló correctamente, pero requiere un reinicio.
- La aplicación está en proceso de instalación, pero requiere un reinicio para continuar.

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar el contenido de notificación de aplicación para las cuentas de la organización <!-- 2576686 -->
La aplicación de Intune en dispositivos iOS y Android le permitirá controlar el contenido de las notificaciones de la aplicación para las cuentas de la organización. Esta característica requerirá la compatibilidad de las aplicaciones y es posible que no esté disponible para todas las aplicaciones habilitadas para la aplicación. Para más información sobre la aplicación, consulte [¿Qué son las directivas de protección de aplicaciones?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración de los dispositivos

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices----3246388----"></a>Uso de certificados PKCS con perfiles de Wi-Fi en dispositivos Windows 10 y versiones posteriores <!-- 3246388  -->
Actualmente, puede autenticar los perfiles de Wi-Fi de Windows con certificados SCEP (**configuración de dispositivos** > **perfiles** > **crear un perfil** > **Windows 10 y versiones posteriores** para la plataforma > **Wi-Fi** para tipo de perfil > **tipo de EAP**de > **empresarial** ). Podrá usar certificados PKCS con los perfiles de Wi-Fi de Windows. Esta característica permite a los usuarios autenticar perfiles de Wi-Fi mediante perfiles de certificado PKCS nuevos o existentes en el inquilino. 

Para obtener más información sobre los perfiles de Wi-Fi, consulte [Agregar configuración de Wi-Fi para dispositivos Windows 10 y versiones posteriores en Intune](../configuration/wi-fi-settings-windows.md).

Se aplica a:
- Windows 10 y versiones posteriores

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices----4892824----"></a>Nueva configuración de ExchangeActiveSync al crear un perfil de configuración de dispositivo de correo electrónico en dispositivos iOS <!-- 4892824  --> 
En dispositivos iOS/iPados, puede configurar la conectividad de correo electrónico en un perfil de configuración de dispositivo (**configuración de dispositivo** > **perfiles** > **crear perfil** > **iOS/ipad** para el **correo electrónico** de plataforma > para el tipo de perfil). 

Habrá nuevas opciones de configuración de ExchangeActiveSync disponibles, entre las que se incluyen:
- Elija los servicios que desea sincronizar (o bloquear la sincronización), como correo electrónico, calendario y contactos.
- Permita (o bloquee) a los usuarios cambiar la configuración de sincronización para estos servicios en sus dispositivos. 

Para ver la configuración actual, vaya a [configuración de Perfil de correo electrónico para dispositivos iOS en Intune](../configuration/email-settings-ios.md).

Se aplica a:
- iOS 13.0 y versiones más recientes
- IPadOS 13.0 y versiones más recientes

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices----5353228----"></a>Impedir que los usuarios agreguen cuentas personales de Google al propietario del dispositivo de Android y a los dispositivos dedicados <!-- 5353228  -->
Podrá evitar que los usuarios creen cuentas personales de Google en el propietario del dispositivo de Android Enterprise y en los dispositivos dedicados (**configuración del dispositivo** > **perfiles** > **crear un perfil** > **Android Enterprise** para la plataforma > **propietario del dispositivo solo > restricciones de dispositivo** para el tipo de perfil > la configuración de **usuarios y cuentas**).

Para ver los valores actuales que puede configurar, vaya a [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](../configuration/device-restrictions-android-for-work.md).

Se aplica a:
- Propietario del dispositivo Android Enterprise
- Dispositivos Android Enterprise dedicados

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile----5468501----"></a>Se ha quitado el valor de registro del lado servidor para comandos Siri en el perfil de restricciones de dispositivos iOS <!-- 5468501  -->
En los dispositivos iOS, puede crear perfiles de restricciones de dispositivo que configure el registro del lado servidor para los comandos de Siri (**configuración del dispositivo** > **perfiles** > **crear perfil** > **iOS/ipados** para la plataforma > **Restricciones de dispositivo** para el tipo de perfil > **aplicaciones integradas**). Se quitará el valor **de configuración de registro del lado servidor para comandos Siri** .

Esta configuración se quitará de la consola de administración de Intune. Esta configuración no tiene ningún efecto en el dispositivo, aunque las directivas existentes que tienen configurada esta configuración seguirán mostrando el valor. Si desea quitar la configuración de las directivas existentes, vaya a la Directiva, haga una edición menor, guárdela y la Directiva se actualizará.

Para ver los valores que puede configurar, vea [Configuración de dispositivos iOS e iPadOS para permitir o restringir características mediante Intune](../configuration/device-restrictions-ios.md).

Se aplica a:
- iOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Administración de dispositivos

### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>Editar el valor de nombre de dispositivo para dispositivos AutoPilot<!-- 2640074  -->
Podrá editar el valor de nombre de dispositivo para los dispositivos AutoPilot Azure AD Unidos. Para ello, vaya a **Intune** > **inscripción de dispositivos** > la **inscripción de windows** > **Windows AutoPilot** > **dispositivos** > elija el dispositivo > cambiar el valor del **nombre del dispositivo** en el panel derecho. > **Guardar**.


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Editar el valor de la etiqueta de grupo para dispositivos AutoPilot<!-- 4816775 -->
Podrá editar el valor de etiqueta de **Grupo** para dispositivos AutoPilot:

1. Seleccione **Intune**  > **inscripción de dispositivos**  >  la**inscripción de windows**  > **Windows AutoPilot**  > **dispositivos**.
1. Elija el dispositivo.
1. En el panel de la derecha, cambie el valor de **etiqueta de grupo** .
1. Seleccione **Guardar**.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Dirigirse a los grupos de usuarios de macOS para requerir la administración de Jamf <!-- 4061739 -->
Podrá dirigirse a grupos específicos de usuarios para que los dispositivos de macOS puedan ser administrados por Jamf. Este destino le permitirá aplicar la integración de cumplimiento de Jamf a un subconjunto de dispositivos macOS mientras que otros dispositivos siguen siendo administrados por Intune. Los destinatarios también le permitirán migrar gradualmente los dispositivos de los usuarios de un sistema de administración de dispositivos móviles (MDM) al otro.

<!-- ***********************************************-->
## <a name="intune-apps"></a>Aplicaciones de Intune

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Experiencia mejorada de inscripción de macOS en Portal de empresa <!-- 5074349  -->
La experiencia de inscripción de Portal de empresa para macOS tendrá un proceso de inscripción más sencillo que se alineará más estrechamente con la Portal de empresa para la experiencia de inscripción de iOS. Los usuarios del dispositivo verán:  

* Una interfaz de usuario más elegante.  
* Una lista de comprobación de inscripción mejorada.  
* Instrucciones más claras sobre cómo inscribir sus dispositivos.  
* Opciones de solución de problemas mejoradas.  

### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857----"></a>Mejor diseño de la lista de comprobación en Portal de empresa aplicación para Android<!-- 5550857  -->
La lista de comprobación de configuración de la aplicación Portal de empresa para Android se actualizará con un diseño ligero y nuevos iconos. Los cambios se alinearán con las actualizaciones recientes realizadas en la aplicación Portal de empresa para iOS.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Supervisión y solución de problemas

### <a name="updated-support-experience-------5012398------"></a>Experiencia de soporte actualizada   <!--  5012398    -->
Como parte de las mejoras continuas, actualizaremos la experiencia de soporte técnico en la consola de Intune.  Mejoraremos la búsqueda en la consola y los comentarios de los problemas comunes, y simplificaremos el flujo de trabajo para ponerse en contacto con el soporte técnico.     

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Control de acceso basado en roles

### <a name="duplicate-custom-or-built-in-roles----1081938---"></a>Duplicar roles personalizados o integrados <!-- 1081938 -->
Podrá copiar los roles integrados y personalizados. Para ello, vaya a **Intune** > **roles** > **todos los roles** > elija un rol en la lista > **duplicar**. Asegúrese de escribir un nuevo nombre que sea único.

<!-- ***********************************************-->

## <a name="security"></a>Seguridad

### <a name="bitlocker-key-rotation--------2564951--------"></a>Rotación de claves de BitLocker     <!-- 2564951      -->
Podrá usar Intune para rotar las claves de recuperación de BitLocker para los dispositivos administrados que ejecutan Windows versión 1909 o posterior. 

<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.
