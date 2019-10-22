---
title: 'En desarrollo: Microsoft Intune'
titleSuffix: ''
description: Características de Microsoft Intune en desarrollo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea5fae72f6e2057ef0b03a7bd295085ed1ac3bbd
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601547"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>En desarrollo para Microsoft Intune: octubre de 2019

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

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>Aplicar el modo oscuro en iOS Portal de empresa <!-- 4911422  -->
El modo oscuro está planeado para iOS Portal de empresa. Podrá descargar aplicaciones de empresa, administrar sus dispositivos y obtener soporte técnico en la combinación de colores que prefiera. Para más información sobre el Portal de empresa de iOS, consulte [Configuración de la aplicación Portal de empresa de Microsoft Intune](../apps/company-portal-app.md).

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

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>Asignación de la versión beta de Microsoft Edge para macOS <!-- 4678761  -->
Podrá agregar y asignar la versión más reciente de la versión beta de Microsoft Edge a Intune para dispositivos macOS. 

Para asignar la versión beta de Microsoft Edge para dispositivos macOS:
1. En Intune, seleccione **aplicaciones cliente**  > **aplicaciones**  > **Agregar aplicación**  > **Microsoft Edge-MacOS**. 
1. Asigne la versión beta de Microsoft Edge a los grupos deseados. Microsoft AutoUpdate (MAU) mantiene actualizado Microsoft Edge. 
 
Para obtener más información sobre Microsoft Edge, consulte [Administración del acceso web con Microsoft Edge con Microsoft Intune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurar el contenido de notificación de aplicación para las cuentas de la organización <!-- 2576686 -->
La aplicación de Intune en dispositivos iOS y Android le permitirá controlar el contenido de las notificaciones de la aplicación para las cuentas de la organización. Esta característica requerirá la compatibilidad de las aplicaciones y es posible que no esté disponible para todas las aplicaciones habilitadas para la aplicación. Para más información sobre la aplicación, consulte [¿Qué son las directivas de protección de aplicaciones?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuración de los dispositivos

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>Nuevo perfil de interfaz de configuración de firmware de dispositivo para dispositivos que ejecutan Windows 10 y versiones posteriores <!-- 2266073  -->
En Windows 10 y versiones posteriores, puede crear un perfil de configuración de dispositivo para controlar la configuración y las características: 

1. Seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
1. En Plataforma, seleccione **Windows 10 y versiones posteriores**. 
 
Un nuevo tipo de Perfil de interfaz de configuración de firmware de dispositivos permitirá a Intune administrar la configuración de UEFI (BIOS).

Para obtener información sobre la configuración actual que se puede configurar, consulte [Aplicar características y configuraciones en los dispositivos con perfiles de dispositivo en Microsoft Intune](../configuration/device-profiles.md).

Esta característica se aplica a Windows 10 RS5 (1809) y versiones posteriores, en seleccionar dispositivos.
 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscripción de dispositivos

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>Para dispositivos iOS, personalice la ventana de privacidad de inscripción de Portal de empresa <!-- 4394993  -->
Con Markdown, podrá personalizar la ventana de privacidad del Portal de empresa que los usuarios finales ven durante la inscripción de iOS. En concreto, puede personalizar la lista de elementos que la organización no puede ver o realizar en el dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Administración de dispositivos


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Editar el valor de la etiqueta de grupo para dispositivos AutoPilot<!-- 4816775 -->
Podrá editar el valor de etiqueta de **Grupo** para dispositivos AutoPilot:

1. Seleccione **Intune**  > **inscripción de dispositivos**  >  la**inscripción de windows**  > **Windows AutoPilot**  > **dispositivos**.
1. Elija el dispositivo.
1. En el panel de la derecha, cambie el valor de **etiqueta de grupo** .
1. Seleccione **Guardar**.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Dirigirse a los grupos de usuarios de macOS para requerir la administración de Jamf <!-- 4061739 -->
Podrá dirigirse a grupos específicos de usuarios para que los dispositivos de macOS puedan ser administrados por Jamf. Este destino le permitirá aplicar la integración de cumplimiento de Jamf a un subconjunto de dispositivos macOS mientras que otros dispositivos siguen siendo administrados por Intune. Los destinatarios también le permitirán migrar gradualmente los dispositivos de los usuarios de un sistema de administración de dispositivos móviles (MDM) al otro.

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Implementar actualizaciones de software en dispositivos macOS <!-- 3194876 -->
Podrá implementar actualizaciones de software en grupos de dispositivos macOS. Esta característica incluye el archivo crítico, el firmware, el archivo de configuración y otras actualizaciones. Puede enviar actualizaciones en la siguiente protección del dispositivo. También puede seleccionar una programación semanal para implementar actualizaciones dentro o fuera de los períodos que establezca. 

Esta característica le ayuda cuando desea actualizar dispositivos fuera de horas de trabajo estándar o fuera de horas cuando el Departamento de soporte técnico está totalmente personal. También obtendrá un informe detallado de todos los dispositivos macOS que tienen actualizaciones implementadas. Puede profundizar en el informe por dispositivo para ver el estado de una actualización determinada.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Supervisión y solución de problemas

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>Informe de Android en la página de información general de dispositivos <!-- 2984353  -->
Agregaremos un nuevo informe a la página de **información general de dispositivos** . El informe muestra el número de dispositivos Android inscritos en cada solución de administración de dispositivos. El gráfico muestra los recuentos de dispositivos para el perfil de trabajo, totalmente administrado, dedicado y administrador de dispositivos inscritos. 

Para ver el informe, elija **Intune** > **dispositivos** > **Introducción**.

### <a name="updated-support-experience-------5012398------"></a>Experiencia de soporte actualizada   <!--  5012398    -->
Como parte de las mejoras continuas, actualizaremos la experiencia de soporte técnico en la consola de Intune.  Mejoraremos la búsqueda en la consola y los comentarios de los problemas comunes, y simplificaremos el flujo de trabajo para ponerse en contacto con el soporte técnico.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Notificaciones

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Consulte también
Consulte [Novedades de Microsoft Intune](whats-new.md) para obtener más información sobre los desarrollos recientes.
