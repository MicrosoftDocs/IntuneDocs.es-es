---
title: Configuración de Windows Update for Business en Microsoft Intune (Azure) | Microsoft Docs
description: Configuración de WUfB para dispositivos Windows 10 que se pueden implementar mediante Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c5a0ee88a24804294346888facef523f89fee816
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046646"
---
# <a name="windows-update-settings-for-intune"></a>Configuración de actualizaciones de Windows para Intune  

Vea la configuración de actualizaciones de Windows 10 que puede [realizar y administrar](windows-update-for-business-configure.md) con Microsoft Intune.  

Al realizar la configuración de anillos de actualización de Windows 10 en Intune, está configurando Windows Update. Si una opción de configuración de actualizaciones de Windows tiene una dependencia de versión de Windows 10, esta se anota en los detalles de configuración.  

## <a name="update-settings"></a>Configuración de actualizaciones  

La configuración de actualizaciones controla qué bits descargará un dispositivo y cuándo. Para obtener más información sobre el comportamiento de cada opción de configuración, vea la documentación de referencia de Windows.  

### <a name="servicing-channel"></a>Canal de servicio  

- **Valor predeterminado**: Canal semianual (dirigido)  
- **Documentación de referencia de Windows**: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  
Establezca el canal (rama) del que el dispositivo recibe las actualizaciones de Windows. Distintos canales pueden usar períodos de aplazamiento diferente antes de que se entreguen las actualizaciones.  

Por ejemplo, el *Canal semianual* tiene un aplazamiento de seis meses. Si usa este canal sin otros aplazamientos desde este cuerpo de configuración, el dispositivo instala la actualización seis meses después de su lanzamiento.  

Canales de actualización admitidos:  

- Canal semianual  
- Canal semianual (dirigido)  
- Windows Insider: rápido  
- Windows Insider: lento  
- Lanzamiento de Windows Insider  

Si selecciona un canal de Insider, Intune configura automáticamente el valor de actualización de Windows [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) para que funcione la compilación de Insider.  


> [!IMPORTANT]  
> A partir de la versión 1903 de Windows, se retira el uso del *Canal semianual (dirigido)* (SAC-T). Con este cambio, SAC-T se combina con el *Canal semianual*. Para más información sobre este cambio y cómo afecta a Windows Update for Business, consulte la entrada de Blog de Windows IT Pro sobre [Windows Update for Business y la retirada de SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523).
 


### <a name="microsoft-product-updates"></a>Actualizaciones de productos de Microsoft  

- **Valor predeterminado**: Permitir
- **Documentación de referencia de Windows**: [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

Elija *Permitir* si quiere buscar actualizaciones de aplicaciones en Microsoft Update.    

### <a name="windows-drivers"></a>Controladores de Windows  

- **Valor predeterminado**: Permitir
- **Documentación de referencia de Windows**: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)

Elija *Permitir* para incluir los controladores de Windows Update durante las actualizaciones.

### <a name="quality-update-deferral-period-days"></a>Período de aplazamiento de actualizaciones de calidad (días)  

- **Valor predeterminado**: 0  
- **Documentación de referencia de Windows**: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

Especifique el número de días, entre 0 y 30, que se aplazarán las actualizaciones de calidad. Este período se suma a cualquier período de aplazamiento que forme parte del canal de servicio seleccionado. El período de aplazamiento comienza cuando el dispositivo recibe la directiva.  

Las actualizaciones de calidad suelen ser correcciones y mejoras de la funcionalidad de Windows existente.  

### <a name="feature-update-deferral-period-days"></a>Período de aplazamiento de actualizaciones de características (días)  

- **Valor predeterminado**: 0  
- **Documentación de referencia de Windows**: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

Especifique el número de días que se aplazarán las actualizaciones de características. Este período se suma a cualquier período de aplazamiento que forme parte del canal de servicio seleccionado. El período de aplazamiento comienza cuando el dispositivo recibe la directiva.  
Período de aplazamiento admitido:  

- *Versión 1709 o posteriores de Windows*: de 0 a 365 días  
- *Versión 1703 de Windows*: de 0 a 180 días  

Las actualizaciones de características suelen ser características nuevas de Windows.  

### <a name="set-feature-update-uninstall-period-2--60-days"></a>Establecimiento del período de desinstalación de actualizaciones de características (de 2 a 60 días)  

- **Valor predeterminado**: 10  
- **Documentación de referencia de Windows**: [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

Configure un tiempo transcurrido el cual las actualizaciones de características no se pueden desinstalar.  

Finalizado este período, se quitan los bits de actualizaciones anteriores del dispositivo y ya no se puede desinstalar una versión anterior de la actualización.  

Por ejemplo, imagine un anillo de actualización con un período de desinstalación de actualizaciones de características de 20 días. A los 25 días decide revertir la última actualización de características y usar la opción Desinstalar.  Los dispositivos que instalaron la actualización de características hace más de 20 días no pueden desinstalarla ya que quitaron los bits necesarios como parte de su mantenimiento. Pero los dispositivos que solo han instalado la actualización de características hace un máximo de 19 días pueden desinstalarla si se registran correctamente para recibir el comando de desinstalación antes de superar el período de desinstalación de 20 días.  


## <a name="user-experience-settings"></a>Configuración de la experiencia de usuario  

La configuración de la experiencia de usuario controla la experiencia del usuario final con el reinicio del dispositivo y los avisos. Para obtener más información sobre el comportamiento de cada opción de configuración, vea la documentación de referencia de Windows.  

### <a name="automatic-update-behavior"></a>Comportamiento de actualizaciones automáticas  

- **Valor predeterminado**: instalación y reinicio automáticos a una hora programada.  
- **Documentación de referencia de Windows**: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

Elija cómo se instalan las actualizaciones automáticas y, si es necesario, cuándo se debe reiniciar el dispositivo.  

Vea la documentación de referencia de Windows para conocer las siguientes opciones admitidas:  

- **Notificar descarga**: se notifica al usuario antes de descargar la actualización. Los usuarios eligen descargar e instalar las actualizaciones.  

- **Instalación automática a la hora del mantenimiento**: las actualizaciones se descargan automáticamente y luego se instalan durante el mantenimiento automático cuando el dispositivo no está en uso ni funciona con batería. Cuando es necesario reiniciar, se pide a los usuarios que reinicien durante siete días y luego se fuerza el reinicio.  

  Esta opción puede reiniciar un dispositivo automáticamente después de que se instala la actualización. Use el valor **Horas activas** para definir un período durante el cual se bloquean los reinicios automáticos:  

  - **Inicio de horas activas**: especifique una hora de inicio para suprimir los reinicios debido a las instalaciones de actualizaciones.  
    **Documentación de referencia de Windows**: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Valor predeterminado**: 8 a.m.  
  
  - **Fin de horas activas**: especifique una hora de finalización para suprimir los reinicios debido a las instalaciones de actualizaciones.  
    **Documentación de referencia de Windows**: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Valor predeterminado**: 5 a.m.  

- **Instalar y reiniciar automáticamente a la hora del mantenimiento**: las actualizaciones se descargan automáticamente y, luego, se instalan durante el mantenimiento automático cuando el dispositivo no está en uso o funcionando con batería. Cuando es necesario reiniciar, el dispositivo se reinicia cuando no se está usando. (Este es el valor predeterminado para los dispositivos no administrados).  

  Esta opción puede reiniciar un dispositivo automáticamente después de que se instala la actualización. El uso de la opción **Horas activas** no se describe en la configuración de Windows Update, pero se usa en Intune para definir un período durante el cual los reinicios automáticos están bloqueados:  

  - **Inicio de horas activas**: especifique una hora de inicio para suprimir los reinicios debido a las instalaciones de actualizaciones.  
    **Documentación de referencia de Windows**: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Valor predeterminado**: 8 a.m.  

  - **Fin de horas activas**: especifique una hora de finalización para suprimir los reinicios debido a las instalaciones de actualizaciones.  
    **Documentación de referencia de Windows**: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Valor predeterminado**: 5 a.m.  

- **Instalar y reiniciar automáticamente a la hora programada**: especifique un día y una hora de instalación. Si no se especifica, la instalación se ejecuta a las 3 a.m. todos los días, seguida de una cuenta atrás de 15 minutos para un reinicio. El usuario que ha iniciado sesión puede retrasar la cuenta atrás y reiniciar.  
  
  Esta opción admite valores de configuración adicionales.  
  **Documentación de referencia de Windows**: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  - **Frecuencia de comportamiento automático**: use esta opción para programar cuándo se instalarán las actualizaciones (semana, día y hora).  
    **Valor predeterminado**: Cada semana

  - **Día de instalación programado**: especifique qué día de la semana quiere que se instalen las actualizaciones.  
    **Valor predeterminado**: Cualquier día  

  - **Hora de instalación programada**: especifique a qué hora del día quiere que se instalen las actualizaciones.  
    **Valor predeterminado**: 3 a.m.  

- **Instalar y reiniciar automáticamente sin control del usuario final**: las actualizaciones se descargan automáticamente y, luego, se instalan durante el mantenimiento automático cuando el dispositivo no está en uso o funcionando con batería. Cuando es necesario reiniciar, el dispositivo se reinicia cuando no se está usando. Esta opción establece el panel de control de los usuarios finales como de solo lectura.  

- **Restablecer valores predeterminados**: se restaurará la configuración original de actualizaciones automáticas en máquinas Windows 10 que ejecuten la actualización de octubre de 2018 o versiones posteriores.  


### <a name="restart-checks"></a>Comprobaciones de reinicio  

- **Valor predeterminado**: Permitir  
- **Documentación de referencia de Windows**: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

Este valor tiene resultados diferentes según la versión de Windows de los dispositivos:  

- Windows, versión 1703 y anteriores: al reiniciar un dispositivo se efectúan algunas comprobaciones, como la de los usuarios activos, los niveles de batería, los juegos en ejecución, etc. Para omitir estas comprobaciones al reiniciar un dispositivo, seleccione **Omitir**.  
- A partir de la versión 1709 de Windows: durante las horas activas no se ejecutan los procesos siguientes para las actualizaciones: examen, descarga, instalación y reinicio. Después de las horas activas, se ejecutan los procesos de actualización y se puede reactivar el dispositivo tras la suspensión, y examinar, descargar, instalar y reiniciar el dispositivo, siempre y cuando se hayan pasado las comprobaciones de batería y energía. Para más información, consulte [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart).  

### <a name="block-user-from-pausing-windows-updates"></a>Impedir al usuario pausar las actualizaciones de Windows  

- **Valor predeterminado**: Permitir  
- **Documentación de referencia de Windows**: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

Permita o impida que el usuario de un dispositivo pause la instalación de una actualización. 

### <a name="block-user-from-scanning-for-windows-updates"></a>Evitar que los usuarios examinen las actualizaciones de Windows  
 - **Valor predeterminado**: Permitir
 - **Documentación de referencia de Windows**: [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

Especifica si se permite o no que un usuario examine Windows Update. Por ejemplo, si configura un *bloqueo*, los usuarios no pueden acceder a las características de examen, descarga e instalación de Windows Update.  

### <a name="require-users-approval-to-restart-outside-of-work-hours"></a>Solicitar la aprobación del usuario para reiniciar fuera del horario de trabajo  

- **Valor predeterminado**: Sin configurar  
- **Documentación de referencia de Windows**: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
Seleccione *Requerido* para exigir que un usuario apruebe el reinicio de un dispositivo fuera del horario de trabajo.  
   
### <a name="remind-user-prior-to-required-auto-restart-with-dismissible-reminder-hours"></a>Recordar al usuario antes del reinicio automático necesario con aviso que se pueda descartar (horas)  

- **Valor predeterminado**: *esta opción no está configurada de forma predeterminada ni se presenta un recordatorio a los usuarios*.  
- **Documentación de referencia de Windows**: [Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

Especifique cuánto tiempo antes de un reinicio automático se mostrará una notificación sobre ese reinicio en el dispositivo de un usuario. Esa notificación se puede descartar. Se admiten los valores de **2**, **4**, **8**, **12** o **24** horas.  

### <a name="remind-user-prior-to-required-auto-restart-with-permanent-reminder-minutes"></a>Recordar al usuario antes del reinicio automático necesario con aviso permanente (minutos)  

- **Valor predeterminado**: *esta opción no está configurada de forma predeterminada ni se presenta un recordatorio a los usuarios*.  
- **Documentación de referencia de Windows**: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning) 

Especifique cuánto tiempo antes de un reinicio automático se mostrará una advertencia sobre ese reinicio en el dispositivo de un usuario. Esa advertencia no se puede descartar. Se admiten los valores de **15**, **30** o **60** minutos.  

### <a name="windows-update-notification-level"></a>Nivel de notificación de Windows Update  
- **Valor predeterminado**: use las notificaciones predeterminadas de Windows Update 
- **Documentación de referencia de Windows**: [Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)

Especifique qué nivel de notificaciones de Windows Update ven los usuarios. Esta opción no controla cómo y cuándo se descargan e instalan las actualizaciones.

### <a name="allow-user-to-restart-engaged-restart"></a>Permitir al usuario que reinicie (reinicio establecido)  

- **Valor predeterminado**: Sin configurar  
- **Documentación de referencia de Windows**: *No aplicable*  
- **Versión de Windows**: compatible con la versión 1803 y posteriores de Windows 10  

  > [!NOTE]  
  > La versión 1809 de Windows 10 presenta valores de configuración adicionales de reinicio establecido que permiten aplicar distintos valores a actualizaciones de características y de calidad. Sin embargo, la configuración administrada por Intune no se aplica de forma diferente a los distintos tipos de actualizaciones. En cambio, Intune aplica los mismos valores a las actualizaciones de características y de calidad.  

Cuando se establece en **Requerido**, se permite el uso de las opciones de reinicio establecido para las actualizaciones de Windows 10. Estas opciones hacen partícipe al usuario de un dispositivo para que ayude a administrar cuándo reiniciarlo tras la instalación de una actualización que requiere un reinicio.  

Para más información sobre esta opción, consulte [Reinicio establecido](https://docs.microsoft.com/windows/deployment/update/waas-restart#engaged-restart) en la documentación de Windows 10 para la implementación de actualizaciones.  

Los siguientes valores de configuración se usan para controlar cuándo se producirán las acciones de reinicio establecido.  

- **Hacer la transición de los usuarios al reinicio comprometido después de un reinicio automático (días)**  
  - **Valor predeterminado**: de forma predeterminada, esta opción no está configurada, aunque admite un valor de **2** a **30**.  
  - **Documentación de referencia de Windows**: [Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
  Especifique cuánto tiempo transcurre desde que se instala la actualización hasta que el dispositivo entra en el comportamiento de reinicio establecido. Después de obtener el número de días configurado, los usuarios reciben un aviso para reiniciar el dispositivo.  

- **Posponer el recordatorio de reinicio establecido (días)**  
  - **Valor predeterminado**: de forma predeterminada, esta opción no está configurada, aunque admite un valor de **1** a **3**.  
  - **Documentación de referencia de Windows**: [Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
  Especifique cuánto tiempo se puede posponer un aviso de reinicio.  Tras el período de aplazamiento, se vuelve a ofrecer el aviso de reinicio. El usuario puede seguir posponiendo el aviso hasta que se alcance la fecha límite de instalación.  

- **Establecer fecha límite para reinicios pendientes (días)**  
  - **Valor predeterminado**: de forma predeterminada, esta opción no está configurada, aunque admite un valor de **2** a **30**.  
  - **Documentación de referencia de Windows**: [Update/EngagedRestartDeadline](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  Especifique un número máximo de días de espera después de que comience el comportamiento de reinicio establecido antes de que un dispositivo aplique un reinicio obligatorio. Este reinicio solicita a los usuarios que guarden su trabajo.

### <a name="delivery-optimization-download-mode"></a>Modo de descarga de optimización de entrega  

la optimización de entrega ya no se configura como parte del Círculo de actualizaciones de Windows 10 en Actualizaciones de software. Ahora, la optimización de entrega se establece mediante la configuración del dispositivo. Sin embargo, las opciones de configuración anteriores seguirán estando disponibles en la consola. Puede quitar estas configuraciones previas si las edita para que se muestren como *Sin configurar*, pero no se pueden modificar de otra forma. 

Para evitar conflictos entre la directiva nueva y la anterior, vea [Cambiar desde círculos de actualizaciones existentes a la optimización de entrega](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization) y, después, migre su configuración a un perfil de optimización de entrega.
