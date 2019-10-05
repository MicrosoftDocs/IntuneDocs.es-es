---
title: Configuración de Windows Update for Business en Microsoft Intune (Azure) | Microsoft Docs
description: Configuración de WUfB para dispositivos Windows 10 que se pueden implementar mediante Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5aaa964151477896c236e504ec9b378cf580e838
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736382"
---
# <a name="windows-update-settings-for-intune"></a>Configuración de actualizaciones de Windows para Intune  

Vea la configuración de actualizaciones de Windows 10 que puede [realizar y administrar](windows-update-for-business-configure.md) con Microsoft Intune.  

Al realizar la configuración de anillos de actualización de Windows 10 en Intune, está configurando Windows Update. Si una opción de configuración de actualizaciones de Windows tiene una dependencia de versión de Windows 10, esta se anota en los detalles de configuración.  

## <a name="update-settings"></a>Configuración de actualizaciones  

La configuración de actualizaciones controla qué bits descargará un dispositivo y cuándo. Para obtener más información sobre el comportamiento de cada opción de configuración, vea la documentación de referencia de Windows.  

- **Canal de servicio**  
  **Valor predeterminado**: canal semianual  
  Windows Update CSP: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  

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
 
- **Actualizaciones de productos de Microsoft**  
  **Valor predeterminado**: Permitir  
  Windows Update CSP: [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

  - **Permitir** : seleccione *permitir* para buscar actualizaciones de aplicaciones desde Microsoft Update.  
  - **Bloquear** : seleccione Bloquear para impedir que se busquen actualizaciones de aplicaciones.  

- **Controladores de Windows**  
  **Valor predeterminado**: Permitir  
  Windows Update CSP: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)  

  - **Permitir** : seleccione *permitir* incluir controladores de Windows Update durante las actualizaciones.  
  - **Bloquear** : seleccione Bloquear para impedir que se busquen controladores.  

- **Período de aplazamiento de actualizaciones de calidad (días)**  
  **Valor predeterminado**: 0  
  Windows Update CSP: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

  Especifique el número de días, entre 0 y 30, que se aplazarán las actualizaciones de calidad. Este período se suma a cualquier período de aplazamiento que forme parte del canal de servicio seleccionado. El período de aplazamiento comienza cuando el dispositivo recibe la directiva.  

  Las actualizaciones de calidad suelen ser correcciones y mejoras de la funcionalidad de Windows existente.  

- **Período de aplazamiento de actualizaciones de características (días)**  
  **Valor predeterminado**: 0  
  Windows Update CSP: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

  Especifique el número de días que se aplazarán las actualizaciones de características. Este período se suma a cualquier período de aplazamiento que forme parte del canal de servicio seleccionado. El período de aplazamiento comienza cuando el dispositivo recibe la directiva.  

  Período de aplazamiento admitido:  

  - *Windows versión 1709 y versiones posteriores* : de 0 a 365 días  
  - *Versión 1703 de Windows*: de 0 a 180 días  

  Las actualizaciones de características suelen ser características nuevas de Windows.  

- **Establecer el período de desinstalación de la actualización de características (de 2 a 60 días)**  
  **Valor predeterminado**: 10  
  Windows Update CSP: [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

  Configure un tiempo transcurrido el cual las actualizaciones de características no se pueden desinstalar.  

  Finalizado este período, se quitan los bits de actualizaciones anteriores del dispositivo y ya no se puede desinstalar una versión anterior de la actualización.  

  Por ejemplo, imagine un anillo de actualización con un período de desinstalación de actualizaciones de características de 20 días. A los 25 días decide revertir la última actualización de características y usar la opción Desinstalar.  Los dispositivos que instalaron la actualización de características hace más de 20 días no pueden desinstalarla ya que quitaron los bits necesarios como parte de su mantenimiento. Pero los dispositivos que solo han instalado la actualización de características hace un máximo de 19 días pueden desinstalarla si se registran correctamente para recibir el comando de desinstalación antes de superar el período de desinstalación de 20 días.  

## <a name="user-experience-settings"></a>Configuración de la experiencia de usuario  

La configuración de la experiencia de usuario controla la experiencia del usuario final con el reinicio del dispositivo y los avisos. Para más información sobre el comportamiento de cada opción de configuración, consulte la documentación de CSP sobre Windows Update.  

- **Comportamiento de las actualizaciones automáticas**  
  **Valor predeterminado**: instalar automáticamente a la hora del mantenimiento  
  Windows Update CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  Elija cómo se instalan las actualizaciones automáticas y, si es necesario, cuándo se debe reiniciar el dispositivo.  

  Opciones admitidas:  

  - **Notificar descarga**: se notifica al usuario antes de descargar la actualización. Los usuarios eligen descargar e instalar las actualizaciones.  

  - **Instalar automáticamente a la hora del mantenimiento**: las actualizaciones se descargan automáticamente y luego se instalan durante el mantenimiento automático cuando el dispositivo no está en uso ni funciona con batería. Cuando es necesario reiniciar, se pide a los usuarios que reinicien durante siete días y luego se fuerza el reinicio.  

    Esta opción puede reiniciar un dispositivo automáticamente después de que se instala la actualización. Use el valor **Horas activas** para definir un período durante el cual se bloquean los reinicios automáticos:  

    - **Inicio de horas activas**: especifique una hora de inicio para suprimir los reinicios debido a las instalaciones de actualizaciones.  
      **Valor predeterminado**: 8 a.m.  
      Windows Update CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Fin de horas activas**: especifique una hora de finalización para suprimir los reinicios debido a las instalaciones de actualizaciones.  
      **Valor predeterminado**: 5 a.m.  
      Windows Update CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Instalar y reiniciar automáticamente a la hora del mantenimiento**: las actualizaciones se descargan automáticamente y, luego, se instalan durante el mantenimiento automático cuando el dispositivo no está en uso o funcionando con batería. Cuando es necesario reiniciar, el dispositivo se reinicia cuando no se está usando. (Este es el valor predeterminado para los dispositivos no administrados).  

    Esta opción puede reiniciar un dispositivo automáticamente después de que se instala la actualización. El uso de la opción **Horas activas** no se describe en la configuración de Windows Update, pero se usa en Intune para definir un período durante el cual los reinicios automáticos están bloqueados:  

    - **Inicio de horas activas**: especifique una hora de inicio para suprimir los reinicios debido a las instalaciones de actualizaciones.  
      **Valor predeterminado**: 8 a.m.  
      Windows Update CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Fin de horas activas**: especifique una hora de finalización para suprimir los reinicios debido a las instalaciones de actualizaciones.  
      **Valor predeterminado**: 5 a.m.  
      Windows Update CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Instalar y reiniciar automáticamente a la hora programada**: especifique un día y una hora de instalación. Si no se especifica, la instalación se ejecuta a las 3 a.m. todos los días, seguida de una cuenta atrás de 15 minutos para un reinicio. El usuario que ha iniciado sesión puede retrasar la cuenta atrás y reiniciar.   
  Windows Update CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

    Esta opción admite valores de configuración adicionales.  

    - **Frecuencia de comportamiento automático**: use esta opción para programar cuándo se instalarán las actualizaciones (semana, día y hora).  
      **Valor predeterminado**: Cada semana

    - **Día de la instalación programada**: especifique qué día de la semana quiere que se instalen las actualizaciones.  
      **Valor predeterminado**: Cualquier día  

    - **Hora de instalación programada**: especifique a qué hora del día quiere que se instalen las actualizaciones.  
      **Valor predeterminado**: 3 a.m.  

  - **Instalar y reiniciar automáticamente sin control del usuario final**: las actualizaciones se descargan automáticamente y, luego, se instalan durante el mantenimiento automático cuando el dispositivo no está en uso o funcionando con batería. Cuando es necesario reiniciar, el dispositivo se reinicia cuando no se está usando. Esta opción establece el panel de control de los usuarios finales como de solo lectura.  

  - **Restablecer valores predeterminados**: se restaurará la configuración original de actualizaciones automáticas en máquinas Windows 10 que ejecuten la actualización de octubre de 2018 o versiones posteriores.  


- **Comprobaciones de reinicio**  
  **Valor predeterminado**: Permitir  
  Windows Update CSP: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

  Para omitir estas comprobaciones al reiniciar un dispositivo, seleccione **Omitir**. 
  
  Este valor tiene resultados diferentes según la versión de Windows de los dispositivos:  
 
  - *Windows, versión 1703 y anteriores*: al reiniciar un dispositivo se efectúan algunas comprobaciones, como la de los usuarios activos, los niveles de batería, los juegos en ejecución, etc.  
  
  - *Windows, versión 1709 y posteriores*: durante las horas activas no se ejecutan los procesos siguientes para las actualizaciones: examen, descarga, instalación y reinicio. Después de las horas activas, se ejecutan los procesos de actualización y se puede reactivar el dispositivo tras la suspensión, y examinar, descargar, instalar y reiniciar el dispositivo, siempre y cuando se hayan pasado las comprobaciones de batería y energía. 

- **Impedir que los usuarios pausen las actualizaciones de Windows**  
  **Valor predeterminado**: Permitir  
  Windows Update CSP: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

  - **Permitir** : permite a los usuarios del dispositivo pausar la instalación de una actualización.  
  - **Bloquear** : impide que los usuarios del dispositivo pausen la instalación de una actualización.  

- **Impedir que los usuarios examinen las actualizaciones de Windows**  
  **Valor predeterminado**: Permitir  
  Windows Update CSP: [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

  - **Permitir** : permite a los usuarios del dispositivo usar el análisis de Windows Update para buscar y descargar actualizaciones e instalar características.
  - **Bloquear** : impedir que los usuarios del dispositivo tengan acceso a la Windows Update examinar, descargar actualizaciones e instalar características.  

- **Solicitar la aprobación del usuario para reiniciar fuera del horario de trabajo**  
  **Valor predeterminado**: No configurado  
  Windows Update CSP: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
  - **No configurado**.  
  - **Requerido**: exigir que un usuario apruebe el reinicio de un dispositivo fuera del horario de trabajo.  
   
- **Recordar al usuario antes del reinicio automático necesario con aviso que se pueda descartar (horas)**  
  **Valor predeterminado**: 4  
  Windows Update CSP: [Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

  Especifique cuánto tiempo antes de un reinicio automático se mostrará una notificación sobre ese reinicio en el dispositivo de un usuario. Esa notificación se puede descartar. Se admiten los valores de **2**, **4**, **8**, **12** o **24** horas.  
  
  Al borrar el valor predeterminado, esta configuración no se *configura*.  

- **Recordar al usuario antes del reinicio automático necesario con aviso permanente (minutos)**  
  **Valor predeterminado**: 15  
  Windows Update CSP: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)  

  Especifique cuánto tiempo antes de un reinicio automático se mostrará una advertencia sobre ese reinicio en el dispositivo de un usuario. Esa advertencia no se puede descartar. Se admiten los valores de **15**, **30** o **60** minutos.  

  Al borrar el valor predeterminado, esta configuración no se *configura*.  

- **Cambiar el nivel de notificación de Windows Update**  
  **Valor predeterminado**: use las notificaciones predeterminadas de Windows Update  
  Windows Update CSP: [Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)
  
  Especifique qué nivel de notificaciones de Windows Update ven los usuarios. Esta opción no controla cómo y cuándo se descargan e instalan las actualizaciones.  

  Opciones admitidas:
  - **No configurado**.
  - **Usar las notificaciones predeterminadas de Windows Update**
  - **Desactivar todas las notificaciones, excluidas las advertencias de reinicio**
  - **Desactivar todas las notificaciones, incluidas las advertencias de reinicio**  

- **Permitir al usuario que reinicie (reinicio establecido)**  
  **Valor predeterminado**: No configurado  
  > [!IMPORTANT]  
  > Ya no se recomienda usar la configuración de *reinicio de embragado* . En su lugar, use la nueva configuración de *fecha límite* que sustituye a la configuración de *reinicio de embragado* . Intune dejará de admitir la configuración de [ *reinicio* ](../fundamentals/whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-) de la opción en una actualización futura.

  El reinicio comprometido es compatible con Windows 10 versión 1803 y versiones posteriores. 

  > [!NOTE]  
  > La versión 1809 de Windows 10 presenta valores de configuración adicionales de reinicio establecido que permiten aplicar distintos valores a actualizaciones de características y de calidad. Sin embargo, la configuración administrada por Intune no se aplica de forma diferente a los distintos tipos de actualizaciones. En cambio, Intune aplica los mismos valores a las actualizaciones de características y de calidad.  
  
  - **No configurado**.  
  - **Requerido**: esta opción se establece en *Requerido* para permitir el uso de las opciones de reinicio establecido para las actualizaciones de Windows 10. Estas opciones hacen partícipe al usuario de un dispositivo para que ayude a administrar cuándo reiniciarlo tras la instalación de una actualización que requiere un reinicio.  

  Para más información sobre esta opción, consulte [Reinicio establecido](https://docs.microsoft.com/windows/deployment/update/waas-restart#engaged-restart) en la documentación de Windows 10 para la implementación de actualizaciones.  

  Los siguientes valores de configuración se usan para controlar cuándo se producirán las acciones de reinicio establecido.  

  - **Hacer la transición de los usuarios al reinicio comprometido después de un reinicio automático (días)**  
    **Valor predeterminado**: no configurado Windows Update CSP: [Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
    
    Especifique un valor entre **2** y **30** días para indicar cuánto tiempo transcurre desde que se instala la actualización hasta que el dispositivo entra en el comportamiento de reinicio establecido. Después de obtener el número de días configurado, los usuarios reciben un aviso para reiniciar el dispositivo.  

  - **Posponer el recordatorio de reinicio establecido (días)**  
    **Valor predeterminado**: No configurado    
    Windows Update CSP: [Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
    
    Especifique un valor entre **1** y **3** para el tiempo que se puede posponer una solicitud de reinicio.  Tras el período de aplazamiento, se vuelve a ofrecer el aviso de reinicio. El usuario puede seguir posponiendo el aviso hasta que se alcance la fecha límite de instalación.  

  - **Establecer fecha límite para reinicios pendientes (días)**  
    **Valor predeterminado**: No configurado  
    Windows Update CSP: [Update/EngagedRestartDeadline](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  
    Especifique un valor entre **2** y **30** como el número máximo de días de espera después de que comience el comportamiento de reinicio establecido antes de que un dispositivo aplique un reinicio obligatorio. Este reinicio solicita a los usuarios que guarden su trabajo.

- **Usar configuración de fecha límite**  
  **Valor predeterminado**: No configurado  
  > [!IMPORTANT]  
  > A partir de la actualización de agosto de Intune, se recomienda usar la siguiente configuración de fecha límite que sustituye a la configuración de reinicio de la opción activada. Intune dejará de admitir la configuración de [ *reinicio* ](../fundamentals/whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-) de la actividad en una actualización futura de Intune.  

  Permite al usuario usar la configuración de fecha límite.  

  - **No configurado**.
  - **Permitir**

  Cuando se establece en *permitir*, puede configurar las siguientes opciones para las fechas límite:

  - **Fecha límite para las actualizaciones de características**  
    **Valor predeterminado**: 7  
    Windows Update CSP: [Update/ConfigureDeadlineForFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)  

    Especifica el número de días que un usuario tiene antes de que se instalen automáticamente las actualizaciones de características en sus dispositivos (2-30).

  - **Fecha límite para las actualizaciones de calidad**  
    **Valor predeterminado**: 7  
    Windows Update CSP: [Update/ConfigureDeadlineForQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)

    Especifica el número de días que un usuario tiene antes de que se instalen automáticamente las actualizaciones de calidad en sus dispositivos (2-30).

  - **Período de gracia**  
    **Valor predeterminado**: 2 Windows Update CSP: [Update/ConfigureDeadlineGracePeriod]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)

    Especifica un número mínimo de días después de la fecha límite hasta que los reinicios se producen automáticamente (0-7).

  - **Reinicio automático antes de la fecha límite**  
    **Valor predeterminado**: sí Windows Update CSP: [Update/ConfigureDeadlineNoAutoReboot](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)

    Especifica si el dispositivo debe reiniciarse automáticamente antes de la fecha límite.
    - **Sí**
    - **No**




### <a name="delivery-optimization-download-mode"></a>Modo de descarga de optimización de entrega  

la optimización de entrega ya no se configura como parte del Círculo de actualizaciones de Windows 10 en Actualizaciones de software. Ahora, la optimización de entrega se establece mediante la configuración del dispositivo. Sin embargo, las opciones de configuración anteriores seguirán estando disponibles en la consola. Puede quitar estas configuraciones previas si las edita para que se muestren como *Sin configurar*, pero no se pueden modificar de otra forma. 

Para evitar conflictos entre la directiva nueva y la anterior, vea [Cambiar desde círculos de actualizaciones existentes a la optimización de entrega](../configuration/delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization) y, después, migre su configuración a un perfil de optimización de entrega.
