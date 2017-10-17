---
title: Endpoint Protection para equipos Windows
description: "Proteja los equipos administrados con Endpoint Protection, que ofrece protección en tiempo real contra las amenazas de malware."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: arob98
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 002241bf-6cd0-4c75-a4f0-891ac7e6721a
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8b903d5b1ae66b7ce022480864fb08e7107ff4b0
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2017
---
# <a name="help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune"></a>Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune puede ayudarle a proteger los equipos administrados con Endpoint Protection, que proporciona protección en tiempo real contra amenazas de malware, mantiene las definiciones de malware actualizadas y examina automáticamente los equipos. Endpoint Protection también proporciona herramientas que ayudan a administrar y supervisar los ataques de malware.

Si aún no ha instalado el cliente Intune en sus equipos, vea [Instalar el cliente de equipos Windows con Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Use la información de las secciones siguientes como ayuda para configurar, implementar y supervisar Endpoint Protection.

## <a name="choose-when-to-use-endpoint-protection"></a>Elegir cuándo usar Endpoint Protection
Una de las principales prioridades de un administrador de TI es proteger los equipos administrados contra virus y malware. Antes de implementar Intune en los equipos Windows de su organización, debe decidir la manera de proteger los equipos seleccionando una de las siguientes opciones y configurando las opciones de la directiva asociada:

|Quiere:|Configuración de directivas de Endpoint Protection|Más información|
|--------------|---------------------------------------|--------------------|
|Usar Microsoft Intune Endpoint Protection únicamente si no hay ninguna aplicación de protección de extremos de otro fabricante instalada.<br /><br />Puede usar Microsoft Intune Endpoint Protection en todos los equipos en los que no haya instalada una aplicación de protección de puntos de conexión de terceros.|Instalar Endpoint Protection = **Sí**<br /><br />Habilitar Endpoint Protection = **Sí**<br /><br />Instalar Endpoint Protection incluso si hay una aplicación de protección de puntos de conexión de terceros instalada = **No**|Si se detecta una aplicación de protección de puntos de conexión de terceros, Microsoft Intune Endpoint Protection no se instala y se desinstala si ya estaba instalado.|
|Usar Microsoft Intune Endpoint Protection incluso si hay una aplicación de protección de puntos de conexión de otro fabricante instalada.<br /><br />Con este enfoque, se ejecutarán simultáneamente Microsoft Intune Endpoint Protection y la aplicación de protección de puntos de conexión de otro fabricante. No se recomienda esta configuración porque puede provocar problemas de rendimiento. |Instalar Endpoint Protection = **Sí**<br /><br />Habilitar Endpoint Protection = **Sí**<br /><br />Instalar Endpoint Protection incluso si hay una aplicación de protección de puntos de conexión de terceros instalada = **Sí**|Se debe usar cuando:<br /><br />– Desea pasar a usar Microsoft Intune Endpoint Protection.<br />- Se implementa un cliente nuevo que va a usar Microsoft Intune Endpoint Protection.<br />– Se actualiza un cliente que va a usar Microsoft Intune Endpoint Protection.|
|Usar Intune sin Microsoft Intune Endpoint Protection. En lugar de ello va a utilizar una aplicación de protección de extremos de otro fabricante.|Instalar Endpoint Protection = **No**|Si no usa una aplicación de protección de puntos de conexión de otro fabricante, no se recomienda esta configuración, ya que podría exponer los equipos de la organización a malware u otros ataques.<br /><br />Microsoft Intune Endpoint Protection no se instala y, si estaba instalado, se desinstala.|
Para cambiar de su aplicación de protección de extremos actual a Microsoft Intune Endpoint Protection, haga lo siguiente:

1.  Deje que su aplicación actual de protección de extremos se siga ejecutando mientras implementa el software cliente de Intune en esos equipos.

2.  Compruebe que Microsoft Intune Endpoint Protection está instalado y ayuda a proteger los equipos cliente.

3.  Quite el software de protección de extremos de un tercero de la manera siguiente:

    -   Use la distribución de software de Intune para implementar una herramienta de eliminación de software proporcionada por el fabricante de la otra aplicación de protección de puntos de conexión. Para obtener más información, vea [Implementar aplicaciones con Microsoft Intune](deploy-apps.md).

    -   Quitar manualmente la aplicación de protección de extremos de otro fabricante.

> [!NOTE]
> Intune no desinstala automáticamente aplicaciones de protección de extremos de otro fabricante.

## <a name="configure-microsoft-intune-endpoint-protection"></a>Configurar Microsoft Intune Endpoint Protection
Siga estos pasos como guía para la configuración de Endpoint Protection para Microsoft Intune.

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Directiva** > **Agregar directiva**.

2.  Expanda **Administración de equipos** y luego elija **Configuración de agente de Microsoft Intune**. Elija **Crear e implementar una directiva personalizada** para especificar una directiva de configuración de Endpoint Protection. Luego, elija el botón **Crear directiva**.

Puede usar la configuración recomendada o personalizar la configuración. Si necesita más información sobre cómo crear e implementar directivas, vea el tema [Tareas comunes de administración de equipos Windows con el cliente de software de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

  ![Configuración de Endpoint Protection](./media/pol-sa-pc-endpoint-policy.png)

Puede ver la directiva Endpoint Protection implementada en la página **Todas las directivas** del área de trabajo **Directiva**.

## <a name="specify-endpoint-protection-service-settings"></a>Especificar la configuración del servicio Endpoint Protection

|Configuración de directiva|Detalles|
|------------------|--------------------|
|**Instalar Endpoint Protection**|Debe establecerse en **Sí** para instalar Endpoint Protection en equipos administrados. Si durante la instalación se detecta una aplicación de protección de puntos de conexión de terceros, Endpoint Protection no se instalará, a menos que el valor **Instalar Endpoint Protection incluso si hay una aplicación de protección de extremos de otro fabricante instalada** esté establecido en **Sí**. **Nota**: Intune Endpoint Protection se instala de manera predeterminada en equipos administrados. Si no quiere instalar Endpoint Protection en los equipos administrados, debe establecer explícitamente esta directiva en **No**. Si Endpoint Protection se instaló previamente y la directiva se actualiza a **No**, el cliente de Endpoint Protection se desinstalará.<br />Valor recomendado: **Sí**|
|**Instalar Endpoint Protection incluso si hay una aplicación de protección de extremos de otro fabricante instalada**|Debe establecerse en **Sí** para instalar Microsoft Intune Endpoint Protection incluso si se detecta una aplicación de protección de extremos de otro fabricante.<br /><br />Valor recomendado: **Sí**|
|**Habilitar Endpoint Protection**|Debe establecerse en **Sí** para habilitar Microsoft Intune Endpoint Protection en los equipos que tienen el cliente de Endpoint Protection.<br /><br />Si se establece en **No** y Microsoft Intune Endpoint Protection está instalado, la interfaz de usuario cliente de Endpoint Protection no se mostrará a los usuarios y se desactivarán todas las características de protección.<br /><br />Valor recomendado: **Sí**|
|**Deshabilitar UI cliente**|Debe establecerse en **Sí** para ocultar la interfaz de usuario cliente de Microsoft Intune Endpoint Protection a los usuarios (para que surta efecto hay que reiniciar el equipo cliente).<br /><br />Valor recomendado: **No**|
|**Instalar Endpoint Protection incluso si hay una aplicación de protección de extremos de otro fabricante instalada**|Debe establecerse en **Sí** para forzar la instalación de Microsoft Intune Endpoint Protection incluso si se detecta una aplicación de protección de extremos de otro fabricante.<br /><br />Valor recomendado: **No**|
|**Crear un punto de restauración del sistema antes de eliminar malware**|Debe establecerse en **Sí** para crear un punto de restauración del sistema de Windows antes de que comience cualquier corrección de software malintencionado.<br /><br />Valor recomendado: **Sí**|
|**Realizar seguimiento de malware resuelto (días)**|Permite que Endpoint Protection haga un seguimiento de malware resuelto durante un tiempo especificado para que pueda comprobar manualmente los equipos infectados anteriormente.<br /><br />Puede especificar un valor comprendido entre 0 y 30 días.<br /><br />Valor recomendado: **7 días**|
Si ha establecido los valores de directivas de **Instalar Endpoint Protection** y **Habilitar Endpoint Protection** en **Sí** y de **Instalar Endpoint Protection incluso si hay una aplicación de protección de extremos de otro fabricante instalada** en **No**, Microsoft Intune Endpoint Protection detectará que hay otra aplicación de protección de puntos de conexión instalada. Esto significa que Endpoint Protection no se instalará o se desinstalará si ya estaba instalado. Pero Microsoft Intune Endpoint Protection informa sobre el estado de la otra aplicación de protección de puntos de conexión en Intune.

  Microsoft Security Essentials le avisa con la protección en tiempo real si hay amenazas potenciales, como virus y spyware, que intentan instalarse o ejecutarse en el equipo. Si sucede, verá un mensaje en el área de notificación, en el lado derecho de la barra de tareas.

### <a name="specify-real-time-protection-settings"></a>Especificar la configuración de protección en tiempo real

|Configuración de directiva|Detalles|
|------------------|--------------------|
|**Habilitar protección en tiempo real**|Habilita la supervisión y el examen de todos los archivos y aplicaciones a los que se accede. También bloquea las aplicaciones y los archivos malintencionados antes de que puedan ejecutarse en los equipos.<br /><br />Valor recomendado: **Sí**|
|**Examinar todas las descargas**|Habilita el examen de todos los archivos y datos adjuntos que se descargan de Internet a los equipos.<br /><br />Valor recomendado: **Sí**|
|**Supervisar la actividad de archivos y programas en los equipos**|Habilita la supervisión de los archivos entrantes y los archivos salientes, así como la actividad de los programas en los equipos. Con esta opción de configuración, Endpoint Protection puede supervisar cuándo empieza la ejecución de archivos y programas, y le envía alertas sobre las acciones que realizan o las acciones que se realizan con ellos.<br /><br />Valor recomendado: **Sí**|
|**Archivos supervisados**|Permite decidir si se supervisan solo los archivos entrantes, los salientes o todos.<br /><br />Valor recomendado: **Supervisar todos los archivos**|
|**Habilitar supervisión del comportamiento**|Permite a Microsoft Intune Endpoint Protection buscar determinados patrones de actividad sospechosa en equipos cliente.<br /><br />Valor recomendado: **Sí**|
|**Habilitar Sistema de inspección de red**|Habilita el Sistema de inspección de red (NIS) en los equipos cliente. NIS usa firmas de vulnerabilidades conocidas del [Microsoft Malware Protection Center (Centro de protección contra malware de Microsoft)](https://go.microsoft.com/fwlink/?LinkId=234249) para ayudar a detectar y bloquear tráfico de red malintencionado.<br /><br />Valor recomendado: **Sí**|

  ![Configuración en tiempo real para Endpoint Protection](./media/pol-sa-pc-policy-realtime.png)

### <a name="specify-scan-schedule-settings"></a>Especificar la configuración de programación de examen

|Configuración de directiva|Más información|
|------------------|--------------------|
|**Programar un examen rápido diario**|Programa un examen rápido diario de los archivos de uso frecuente y los archivos importantes del sistema en los equipos. Este examen rápido tiene un efecto mínimo sobre el rendimiento.<br /><br />Valor recomendado: **Sí**|
|**Ejecutar un examen rápido si no se han ejecutado dos exámenes rápidos consecutivos**|Configura Endpoint Protection para que ejecute automáticamente un examen rápido en los equipos en caso de que no se hayan realizado dos exámenes rápidos consecutivos.<br /><br />Valor recomendado: **Sí**|
|**Programar un examen completo**|Configura un examen completo de todos los archivos y recursos de los discos duros locales de los equipos. Este examen puede tardar y puede afectar al rendimiento de los equipos (el tiempo depende del número de archivos y recursos examinados).<br /><br />Valor recomendado: **No**|
|**Ejecutar un examen completo si no se han ejecutado dos exámenes completos consecutivos**|Configura Endpoint Protection para que ejecute automáticamente un examen completo en los equipos en caso de que no se hayan realizado dos exámenes consecutivos.<br /><br />Valor recomendado: No configurado|

### <a name="specify-scan-options-settings"></a>Especificar la configuración de opciones de examen

|Configuración de directiva|Detalles|
|------------------|--------------------|
|**Ejecutar un examen completo tras la instalación de Endpoint Protection**|Se establece en **Sí** para que Endpoint Protection ejecute automáticamente un examen completo del sistema después de instalarse en los equipos. Este examen se ejecuta únicamente cuando los equipos están inactivos para minimizar así el efecto en la productividad de los usuarios.<br /><br />Valor recomendado: **Sí**|
|**Ejecutar un examen completo automáticamente cuando es necesario hacer un seguimiento después de quitar malware**|Debe establecerse en **Sí** para permitir a Endpoint Protection ejecutar automáticamente un examen completo del sistema en los equipos tras eliminar malware, para comprobar que no haya otros archivos afectados.<br /><br />Valor recomendado: **Sí**|
|**Iniciar un examen programado solo cuando el equipo está inactivo**|Debe establecerse en **Sí** para impedir que se inicien exámenes programados cuando los equipos se están usando a fin de no mermar la productividad de los usuarios.<br /><br />Valor recomendado: **Sí**|
|**Buscar las últimas definiciones de malware antes de iniciar un examen**|Debe establecerse en **Sí** para permitir que Endpoint Protection compruebe automáticamente las definiciones de malware más recientes antes de empezar a examinar los equipos.<br /><br />Valor recomendado: **Sí**|
|**Examinar archivos de almacenamiento**|Debe establecerse en **Sí** para configurar Endpoint Protection de forma que examine los archivos de almacenamiento (como los archivos .zip o .cab) de los equipos en busca de malware.<br /><br />Valor recomendado: **No**|
|**Analizar mensajes de correo electrónico**|Debe establecerse en **Sí** para configurar Endpoint Protection de forma que examine los mensajes entrantes cuando llegan a los equipos.<br /><br />Valor recomendado: **Sí**|
|**Examinar archivos abiertos desde carpetas compartidas de red**|Debe establecerse en **Sí** para configurar Endpoint Protection de forma que examine los archivos abiertos desde carpetas compartidas en la red. Normalmente se trata de archivos a los que se accede mediante una ruta de acceso UNC (convención de nomenclatura universal). Si se habilita esta función, los usuarios que tienen acceso de solo lectura pueden tener problemas, ya que no pueden eliminar el malware.<br /><br />Valor recomendado: **No**|
|**Examinar unidades de red asignadas**|Debe establecerse en **Sí** para que Endpoint Protection analice los archivos ubicados en unidades de red asignadas. Si se habilita esta función, los usuarios que tienen acceso de solo lectura pueden tener problemas, ya que no pueden eliminar el malware.<br /><br />Valor recomendado: **No**|
|**Examinar unidades extraíbles**|Debe establecerse en **Sí** para configurar Endpoint Protection de forma que examine las unidades extraíbles (como las unidades flash USB) en busca de malware al realizar un examen completo en los equipos.<br /><br />Valor recomendado: **Sí**|
|**Limitar el uso de CPU durante un examen**|Establece el porcentaje máximo de uso de la CPU que se puede usar durante los exámenes programados en los equipos. Puede establecer este valor entre el 1 y el 100 por ciento.<br /><br />Valor recomendado: **50%**|

### <a name="choose-default-actions-settings"></a>Seleccionar la configuración de acciones predeterminadas

La opción **Elegir cómo actúa Endpoint Protection sobre malware de los siguientes niveles de alerta** especifica la acción predeterminada que efectuará Endpoint Protection si se detecta malware de diversos niveles de alerta. Para cada nivel de la alerta puede quitar el malware, ponerlo en cuarentena o realizar la acción recomendada por Microsoft.

Valor recomendado: **Acción recomendada**, que permite a Endpoint Protection recomendar la acción.   

### <a name="decide-whether-to-choose-the-excluded-files-and-folders-settings"></a>Decidir si se selecciona la configuración de archivos y carpetas excluidos

La opción **Archivos y carpetas que se excluirán al ejecutar un examen o al usar la protección en tiempo real** excluye archivos o carpetas específicos cuando se ejecuta un examen o cuando se usa la protección en tiempo real en los equipos.

### <a name="decide-whether-to-choose-the-excluded-processes-settings"></a>Decidir si se selecciona la configuración de procesos excluidos

La opción **Procesos que se excluirán al ejecutar un examen o al usar protección en tiempo real** permite excluir procesos específicos cuando se ejecuta un examen o cuando se usa la protección en tiempo real en los equipos. Solo se pueden excluir los archivos con las siguientes extensiones: **.exe**, **.com** o **.scr**.

### <a name="decide-whether-to-choose-the-excluded-file-types-settings"></a>Decidir si se selecciona la configuración de tipos de archivo excluidos

La opción **Extensiones de archivos que se excluirán al ejecutar un examen o al usar protección en tiempo real** permite excluir extensiones de archivo específicas cuando se ejecuta un examen o cuando se usa la protección en tiempo real en los equipos.

### <a name="specify-microsoft-active-protection-service-settings"></a>Especificar la configuración de Microsoft Active Protection Service
Microsoft Active Protection Service es una comunidad en línea que ayuda a decidir cómo responder a amenazas potenciales. La comunidad también ayuda a detener la propagación de nuevas infecciones de malware. Para **Unirse a Microsoft Active Protection Service**, seleccione **Sí** y, después, especifique el **Nivel de pertenencia**:
  - **Básica**: envía a Microsoft información básica sobre el malware detectado. Esta información incluye de dónde procede el software, las acciones que el usuario aplica o que Endpoint Protection aplica automáticamente y si las acciones obtuvieron resultados satisfactorios.
  - **Avanzada**: envía más información a Microsoft acerca de malware, spyware y software potencialmente no deseado. Esto incluye información sobre la ubicación del software, los nombres de archivo, cómo funciona el software y cómo ha afectado al equipo.

También puede **Recibir definiciones dinámicas en función de los informes de Microsoft Active Protection Service**.

## <a name="choose-management-tasks-for-endpoint-protection"></a>Seleccionar tareas de administración para Endpoint Protection
Las siguientes tareas ayudan a realizar diversas tareas de administración en equipos administrados que ejecutan Endpoint Protection:
 - Actualizar definiciones de malware
  - Consola de Intune: en el área de trabajo **Grupos**, seleccione los equipos que quiere actualizar. Seleccione **Tareas remotas** &gt; **Actualizar definiciones de malware**.
  - Equipo administrado: inicie el software cliente de Endpoint Protection desde el área de notificación de Windows. Seleccione la pestaña **Actualizar** y, luego, **Actualizar**.
 - Ejecutar un examen de malware:
  - Consola de Intune: en el área de trabajo **Grupos**, seleccione los equipos que quiere examinar. Seleccione **Ejecutar un examen completo de malware** o **Ejecutar un examen rápido de malware**.
  - Equipo administrado: inicie el software cliente de Endpoint Protection desde el área de notificación de Windows. Seleccione **Rápido**, **Completo** o **Personalizado** y, luego, **Examinar ahora**.

Para ver el estado de una tarea remota, seleccione el vínculo **Tareas remotas** situado en la esquina inferior derecha de la consola de Intune. El cuadro de diálogo **Estado de la tarea remota** muestra las tareas remotas actuales, el estado de la tarea, el nombre del dispositivo y los errores notificados. También proporciona un vínculo a la información de solución de problemas, si procediera.

## <a name="monitor-endpoint-protection"></a>Supervisar Endpoint Protection
Puede supervisar el estado de infección con malware en sus equipos a través del área de trabajo **Protección** de la [consola de administración de Microsoft Intune](https://manage.microsoft.com/). Esta área de trabajo contiene dos páginas:
 - **Información general de Endpoint Protection**: muestra problemas importantes como vínculos que se pueden seleccionar para obtener más información. Algunos problemas que podrían aparecer son:
  - **Instancias de malware que requieren seguimiento**: haga clic en el vínculo para ver una lista de problemas de malware y las acciones de seguimiento correspondientes que hay que realizar para solucionar el problema. Puede profundizar en la lista para ver qué equipos están afectados.
  - **Equipos con malware que requieren seguimiento**: haga clic en el vínculo para ver todos los equipos con problemas de malware sin solucionar, así como las acciones de seguimiento correspondientes que hay que realizar para solucionar el problema.
  - **Dispositivos que no están protegidos**: haga clic en el vínculo para ver los equipos que no están protegidos por ningún software de protección de puntos de conexión, ya sea porque no hay ningún software instalado o porque hay un error. Seleccione un equipo para ver más detalles.
  - **Dispositivos con otra aplicación de Endpoint Protection en ejecución**: haga clic en el vínculo para ver los equipos que ejecutan una aplicación de protección de puntos de conexión de terceros.
 - **Todo el malware**: muestra una lista de todo el malware activo detectado en los equipos. Puede examinar la lista para ver todos los equipos afectados por un elemento de malware determinado o puede seleccionar una de las siguientes tareas:
  - **Ver propiedades**: abre una página con más información sobre el malware seleccionado.
  - **Más información sobre este malware**: abre un tema desde el Centro de protección contra malware de Microsoft con más información sobre el malware.

> [!IMPORTANT]
> El área de trabajo **Protección** solo se muestra en la consola de administración si el cliente está instalado y se está administrando al menos un equipo cliente.

  ![Supervisar Endpoint Protection](./media/pol-sa-ep-monitor.png)

### <a name="how-to-view-recent-detection-paths-for-malware-on-computers"></a>Cómo ver las rutas de acceso de detección recientes de malware en equipos
Intune puede mostrar las rutas de acceso de hasta 10 de las instancias de malware detectadas más recientemente en un dispositivo. La opción **Rutas de acceso de detección recientes** está deshabilitada de forma predeterminada. Para habilitar esta vista:

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), elija **Grupos** > **Todos los dispositivos** > **Todos los equipos**.
2. Haga clic en el equipo cuyas rutas de acceso de detección recientes desea ver y seleccione **Propiedades**.
3. Seleccione **Malware** desde las pestañas de la parte superior.

   ![Seleccione la pestaña Malware y después haga clic en la casilla Rutas de acceso de detección recientes.](../media/malware-path-column.png)
4. Haga clic con el botón derecho en un encabezado de columna. Aparece una lista de las columnas disponibles. Active la casilla **Rutas de acceso de detección recientes** de la lista. La columna **Rutas de acceso de detección recientes** aparece y muestra hasta 10 de las instancias de malware supervisadas más recientemente en el dispositivo.

## <a name="run-a-malware-scan-or-update-malware-definitions-on-a-computer"></a>Ejecutar un examen de malware o actualizar las definiciones de malware en un equipo
Intune puede ejecutar un examen rápido o completo de malware mediante Endpoint Protection o Windows Defender en un equipo administrado de forma remota que tenga instalado el cliente de Intune.

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), vaya a **Grupos** > **Información general** > **Todos los dispositivos** > **Todos los equipos** y seleccione el equipo de destino.

2. Seleccione la lista desplegable **Tareas remotas** y, después, la tarea que se va a ejecutar en el equipo remoto.

## <a name="need-more-help"></a>¿Necesita más ayuda?
Para obtener más ayuda y soporte técnico, vea [Solucionar problemas de Endpoint Protection en Microsoft Intune](/intune-classic/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune).

### <a name="see-also"></a>Consulte también
[Directivas para proteger equipos de Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
