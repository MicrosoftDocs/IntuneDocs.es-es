---
# required metadata

title: Actualizaciones de software para equipos Windows | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 48e9c41a-d2de-424e-9610-cfd1ad514210

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Mantener los equipos Windows al día con las actualizaciones de software de Microsoft Intune
Microsoft Intune le ayuda a proteger los equipos administrados de varias formas. Por ejemplo, Intune puede administrar e instalar rápidamente las actualizaciones de software que mantienen los equipos actualizados con las últimas revisiones y mejoras de software.

Si aún no ha instalado el cliente Intune en sus equipos, consulte [Instalar al cliente de equipos Windows con Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md)..

Cuando estén disponibles nuevas actualizaciones de Microsoft Update o se haya creado una actualización de otro fabricante, y se puedan aplicar a los equipos administrados, se mostrará una notificación en la página **Introducción** del área de trabajo **Actualizaciones**. Tras seleccionar este vínculo de notificación, puede realizar varias operaciones, como ver más información sobre la actualización, aprobar o rechazar la actualización, y ver los equipos en los que se instalará la actualización si se aprueba.

> [!IMPORTANT]
> El área de trabajo **Actualizaciones** no se muestra en la consola de administrador hasta que se ha instalado el cliente y está administrando correctamente al menos un equipo cliente.

A medida que se aprueban e instalan las actualizaciones, puede examinar el resultado de la instalación en el área de trabajo **Actualizaciones** de la consola de Intune.

Las siguientes secciones le ayudarán a mantener el software actualizado en los equipos administrados.

## Antes de empezar
Antes de empezar a crear y aprobar actualizaciones de software, configure e implemente directivas en los equipos para controlar cuándo y cómo se instalan las actualizaciones.

### Para configurar la directiva de actualización

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Directiva** &gt; **Información general** &gt; **Agregar directiva**..

2.  Configure e implemente una directiva de **Configuración de agente de Microsoft Intune** para la configuración de las actualizaciones. Puede usar la configuración recomendada o personalizar la configuración. Si necesita más información sobre cómo crear e implementar directivas, consulte [Tareas comunes de administración de PC Windows con el cliente de equipo de Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)..

En la tabla siguiente se muestran los valores que puede configurar en la directiva y también los valores recomendados que se utilizarán si no se personaliza la directiva. Puede encontrar estos valores en la sección **Actualizaciones** .

  |Configuración de directiva|Detalles|
    |------------------|--------------------|
    |**Frecuencia de detección de la aplicación y la actualización (horas)** |Especifica la frecuencia (de 8 a 22 horas) con que Intune comprueba si hay nuevas actualizaciones y aplicaciones.<br /><br />Valor recomendado: **8** horas.|
    |**Instalación de actualizaciones y aplicaciones automatizada o con confirmación** |Especifica si las actualizaciones se instalan automáticamente o si se pregunta al usuario antes de la instalación. Además, esta configuración permite programar la instalación de actualizaciones y aplicaciones.<br /><br />La opción **Instalar actualizaciones y aplicaciones automáticamente según la programación** instala las actualizaciones y aplicaciones mediante la programación especificada.<br /><br />Como configuración de directiva dependiente, **Usar mantenimiento automático para equipos Windows**  especifica que se instalan las actualizaciones y aplicaciones con la ventana de mantenimiento automático de Windows.<br /><br />La opción **Solicitar al usuario la instalación** solicita al usuario que instale las actualizaciones cuando están listas.<br /><br />Valores recomendados:<br /><br />Seleccionar **Instalar actualizaciones y aplicaciones automáticamente según la programación**<br /><br />**Día programado: todos los días**<br /><br />**Tiempo programado: 15:00**<br /><br />Seleccionar **Usar mantenimiento automático para equipos Windows**|
    |**Permitir la instalación inmediata de actualizaciones que no interrumpan Windows** |La opción **Permitir** instala inmediatamente las actualizaciones tras su descarga, excepto las actualizaciones que interrumpan o reinicien Windows. Esas actualizaciones se instalan según el valor configurado en **Instalación automática o solicitada de actualizaciones** .<br /><br />La opción **No permitir** instala las actualizaciones según el valor configurado en **Instalación automática o solicitada de actualizaciones**.<br /><br />Valor recomendado: **Permitir** |
    |**Retraso de reinicio de Windows tras la instalación de aplicaciones y actualizaciones programadas (minutos)** |Especifica el tiempo de espera (de 1 a 30 minutos) para reiniciar Windows después de la instalación programada de actualizaciones y aplicaciones.<br /><br />Valor recomendado: **15 minutos** |
    |**Retraso después del reinicio de Windows para iniciar la instalación de aplicaciones y actualizaciones programadas que faltan (minutos)** |Especifica el tiempo que se esperará (de 1 a 60 minutos) para iniciar la instalación de actualizaciones y aplicaciones tras el reinicio de Windows cuando no se realiza una actualización programada.<br /><br />Valor recomendado: **5 minutos**|
    |**Permitir que el usuario que ha iniciado sesión controle el reinicio de Windows tras la instalación de aplicaciones y actualizaciones programadas** |Especifica si el usuario que ha iniciado sesión puede retrasar el reinicio de Windows (si está establecido en **Sí**) o solo recibir una notificación del reinicio automático de Windows (si está establecido en **No**). Si ningún usuario ha iniciado sesión cuando se completa la instalación de actualizaciones o aplicaciones programadas, Windows se reiniciará automáticamente cuando sea necesario. Si se establece en **No**, de manera predeterminada el tiempo que transcurre antes de que se reinicie Windows es 5 minutos.<br /><br />Valor recomendado: **Sí**|
    |**Solicitar al usuario que reinicie Windows durante las actualizaciones obligatorias del agente cliente de Microsoft Intune** |Especifica si se pide a los usuarios conectados que reinicien Windows cuando una actualización obligatoria del cliente de Intune requiere que se reinicie Windows.<br /><br />Valor recomendado: **Sí**|
    |**Programación de instalación de actualizaciones obligatorias del agente cliente de Microsoft Intune** |Programa cuándo se debe realizar la instalación de las actualizaciones del cliente.<br /><br />Valor recomendado: no configurado|
    |**Retraso entre solicitudes para reiniciar Windows tras la instalación de actualizaciones y aplicaciones programadas (minutos)** |Especifica la frecuencia (entre 1 y 1440 minutos) con la que se solicita al usuario que reinicie Windows cuando se instala una actualización o aplicación que requiera el reinicio de Windows y el usuario retrase el reinicio.<br /><br />Valor recomendado: **30 minutos** |

## Actualización de software de Microsoft
La actualización del software de Microsoft no requiere mucho trabajo por parte del usuario. Sin embargo, antes de empezar hay dos cosas que debe configurar:

-   **Categorías de productos y clasificaciones de actualización** : define las categorías y las clasificaciones de las actualizaciones que desea poner a disposición de los equipos. Por ejemplo, podría decidir que sólo desea que se instalen las actualizaciones críticas para Microsoft Office.

-   **Reglas de aprobación automática** : estas reglas aprueban automáticamente determinados tipos de actualizaciones para reducir la sobrecarga de administración. Por ejemplo, es posible que desee aprobar automáticamente todas las actualizaciones de software críticas.

Utilice los dos procedimientos siguientes como ayuda para preparar el uso de las actualizaciones de software:

### Configure las categorías de productos y las clasificaciones de actualización que desee poner a disposición de los equipos administrados

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Administrador** &gt; **Actualizaciones**..

2.  En la página **Configuración del servicio: Actualizaciones** , en la lista **Categoría de productos** , seleccione las categorías de actualización que quiera que estén disponibles para los equipos. Tenga en cuenta que las actualizaciones más comunes están seleccionadas de forma predeterminada.

    > [!IMPORTANT]
    > Para asegurarse de que los equipos reciben las actualizaciones aprobadas por el administrador, la configuración de directiva de grupo de Windows Server Update Services (WSUS) **Especificar la ubicación del servicio Microsoft Update en la intranet** no se debe aplicar a los equipos inscritos con Intune.

3.  En la lista **Clasificación de actualizaciones** , seleccione las clases de actualización que desee poner a disposición de los equipos administrados. De nuevo, se seleccionan las opciones más comunes de forma predeterminada.

4.  Haga clic en **Guardar** para almacenar sus selecciones.

### Para configurar las reglas de aprobación automática de las actualizaciones de software

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Administrador** &gt; **Actualizaciones**..

2.  En la sección **Reglas de aprobación automática** de la página **Configuración del servidor: Actualizaciones**, seleccione **Nuevo**..

3.  En la página **General** del asistente para Crear regla de aprobación automática, escriba un nombre y, opcionalmente, una descripción para la regla.

4.  En la página **Categorías de productos** , seleccione los productos para los que desea la aprobación automática de las actualizaciones.

5.  En la página **Clasificaciones de actualizaciones** , especifique las clasificaciones de actualizaciones que desea que se aprueben automáticamente.

6.  En la página **Implementación** , realice la acción siguiente:

    -   Seleccione los grupos de equipos en los que desea implementar la nueva regla y, después, haga clic en **Agregar**..

    -   Para especificar una fecha límite de instalación para las actualizaciones, active la casilla **Aplique una fecha límite de instalación para estas aplicaciones** y, a continuación, en la lista **Fecha límite para la instalación** , seleccione la fecha límite para la instalación.

        > [!NOTE]
        > Si especifica una fecha límite de instalación, podría ser necesario reiniciar el equipo administrado una o varias veces después de que haya transcurrido el intervalo de fecha límite.

    -   Cuando termine, seleccione **Siguiente**..

7.  En la página **Resumen**, revise los valores de configuración de la nueva regla y, después, seleccione **Finalizar**..

La nueva regla se muestra en la sección **Reglas de aprobación automática** de la página **Configuración de servicio: Actualizaciones** .

> [!NOTE]
> Cuando se crea una regla de aprobación automática, la regla solo aprueba futuras actualizaciones, no las actualizaciones previas que ya existan en Intune. Para aprobar estas actualizaciones debe ejecutar la regla de aprobación automática.


### Para editar, ejecutar o eliminar una regla de actualización aprobada automáticamente

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Administrador** &gt; **Actualizaciones**..

2.  En la sección **Reglas de aprobación automática** , seleccione una regla y, a continuación, realice una de las acciones siguientes:

    -   Para editar la regla, seleccione **Editar** y, después, cambie los parámetros de la regla en el **Asistente para reglas de aprobación de actualización automática**..

    -   Para ejecutar la regla, seleccione **Ejecutar seleccionado**..

    -   Para eliminar la regla, seleccione **Eliminar**..

        > [!NOTE]
        > Eliminar una regla no afecta a las actualizaciones anteriores que se aprobaron mediante la regla eliminada.

## Actualizar software de otros fabricantes
Puede implementar actualizaciones de software que no sea de Microsoft. Para ello debe usar el asistente para **Cargar actualización** , a fin de colocar la actualización en su espacio de almacenamiento en nube. Una vez hecho esto, se puede aprobar o rechazar la actualización, igual que en el caso del software de Microsoft.

### Para cargar y configurar una actualización de otro fabricante

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Actualizaciones** &gt; **Información general** &gt; **Cargar**..

2.  En la página **Archivos de actualización**, seleccione **Examinar** para seleccionar los archivos de instalación necesarios para instalar el paquete de actualización. Puede ser un archivo de Windows Installer (.msi), un archivo de revisión de Windows Installer (.msp) o un archivo de programa .exe. También puede incluir archivos o carpetas adicionales que se encuentren en la misma carpeta que el archivo de instalación.

    Se muestra el tamaño total de los archivos seleccionados para cargar. Tenga en cuenta que este tamaño no incluye los tamaños sin comprimir o expandidos de los archivos de instalación.

3.  Después de especificar los archivos de instalación, la página **Descripción de la actualización** muestra el nombre, la descripción y la clasificación de la información de software que Intune extrajo de los archivos de instalación del software. Puede seleccionar una clasificación para etiquetar el tipo de actualización va a implementar (actualizaciones, actualizaciones críticas, paquetes acumulativos, actualizaciones de seguridad o Service Packs). Seleccione **Siguiente** cuando haya terminado.

4.  En la página **Requisitos** del asistente, elija la arquitectura (32 bits, 64 bits, o ambas) y los sistemas operativos de los equipos administrados a los que se podrá aplicar esta actualización.

5.  En la página **Reglas de detección** especifique cómo Intune determinará si la actualización ya existe en equipos administrados. Si usa la opción predeterminada, **Usar las reglas de detección predeterminadas**, Intune siempre instalará el paquete de actualización una vez en cada equipo de destino.

    > [!NOTE]
    > Si el archivo de instalación de la actualización que especificó es un archivo de Windows Installer o un archivo .msp, no se mostrará la página **Reglas de detección** del asistente. Esto se debe a que los archivos de Windows Installer y .msp contienen sus propias instrucciones para detectar instalaciones de actualización anteriores.

    Seleccione uno o varias de las siguientes reglas para determinar si la actualización ya está instalada en los equipos administrados:

    -   **El archivo existe**

    -   **Existe un código de producto MSI**

    -   **Existe la clave del registro**

6.  Especifique la información adicional necesaria para configurar la regla de detección, como la ruta y el nombre del archivo, el código de producto Windows Installer o una clave del Registro y, después, seleccione **Siguiente**..

7.  En la página **Requisitos previos** del asistente se especifica el software que ya debe estar instalado para poder instalar esta actualización. Puede especificar **Ninguno**, seleccionar un paquete de software que ya se le haya agregado y esté administrado por Intune, o puede especificar una de las reglas siguientes para describir el software:

    -   **El archivo existe**

    -   **Existe un código de producto MSI**

    -   **Existe la clave del registro**

8.  Especifique la información adicional necesaria para configurar la regla de detección, como la ruta y el nombre del archivo, el código de producto Windows Installer o una clave del Registro y, después, seleccione **Siguiente**..

9. En la página **Argumentos de línea de comandos** del asistente puede agregar las propiedades de instalación necesarias a la línea de comandos de instalación para modificar el comportamiento del archivo de instalación. Por ejemplo, algunos programas de software admiten la propiedad **/q** para habilitar la instalación silenciosa. Consulte la documentación de su paquete de software para obtener información sobre los argumentos de línea de comandos disponibles. Especifique los argumentos de línea de comandos que necesita y, después, seleccione **Siguiente**..

    > [!NOTE]
    > Si la actualización no admite la instalación silenciosa, no se puede instalar con Intune.

10. En la página **Códigos de retorno** del asistente puede especificar cómo deben interpretarse los códigos de retorno de la instalación de la actualización. De forma predeterminada, Intune usa códigos de retorno estándares de la industria para informar de una instalación correcta o incorrecta de un paquete de actualización. Los códigos de retorno proporcionados son:

|Código de retorno|Detalles|
|---------------|------------------|
|**0**|Correcto|
|**3010**|Correcto con reinicio|

11. Los códigos de retorno que no figuran en la lista se consideran como un error.
Algunas actualizaciones usan interpretaciones no estándares para códigos de retorno. En este caso, puede especificar sus propias interpretaciones de los códigos de retorno.

12. Especifique o edite los códigos de retorno necesarios y, después, seleccione **Siguiente**..

13. En la página **Resumen** del asistente, revise las acciones que se van a realizar y, después, seleccione **Cargar** para completar el asistente.

La actualización cargada se almacena en el almacenamiento en nube de Intune. Si no dispone de espacio libre suficiente para cargar el paquete de actualización, recibirá notificación de ello durante el proceso de carga. Intune no puede determinar si hay espacio libre suficiente hasta después de que se inicie la carga de la actualización, ya que los archivos comprimidos de instalación y configuración requieren más espacio cuando se descomprimen.

Después de haberse cargado en Intune, una actualización de terceros se muestra en el área de trabajo **Actualizaciones** del panel **Todas las actualizaciones**. Ahora puede aprobar e implementar la actualización. Para obtener más información, consulte la sección “Aprobar y rechazar actualizaciones”.

## Aprobar y rechazar actualizaciones
Cuando las actualizaciones están listas para su instalación, se muestra un mensaje en la página **Información general de actualizaciones** del área de trabajo **Actualizaciones** , en **Estado de actualización**. Seleccione este mensaje para abrir la página **Todas las actualizaciones** y ver qué actualizaciones están listas para su aprobación.

Puede utilizar la lista **Filtros** para facilitar la búsqueda de actualizaciones. Por ejemplo, puede mostrar sólo las actualizaciones que no se pudieron aplicar o las que han quedado obsoletas.

Al seleccionar una actualización de la lista estarán disponibles otros comandos con los que podrá administrar las actualizaciones, como se indica en la tabla siguiente:

|Tarea|Detalles|
|--------|--------------------|
|**Ver propiedades**|Muestra información detallada de la actualización, como el número de equipos a los que se puede aplicar.|
|**Editar**|Sólo para actualizaciones de otros fabricantes. Permite editar las propiedades de la actualización.|
|**Aprobar**|Aprueba la actualización seleccionada y permite configurar los grupos en los que se va a implementar. Para obtener más información, consulte el procedimiento [Para aprobar actualizaciones](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md#BKMK_Approve) de este tema.|
|**Rechazar**|Quita las aprobaciones anteriores de la actualización y oculta la actualización en las vistas predeterminadas. Además, se eliminarán los datos de informe de la actualización.<br /><br />Si posteriormente desea localizar una actualización rechazada, en la página **Todas las actualizaciones** establezca el filtro en **Rechazada**. Puede aprobar esta actualización si es necesario.<br /><br />Si una actualización ha sido rechazada porque la actualización había caducado en Microsoft Update, no se podrá aprobar esa actualización en la consola de administración de Intune.<br /><br />Si elimina una directiva de actualizaciones implementada en los equipos, los valores de esa configuración de directiva de actualizaciones se restablecen a los valores del estado predeterminado del sistema operativo instalado en los equipos.|
|**Eliminar**|Sólo para actualizaciones de otros fabricantes. Elimina la actualización seleccionada.|
|**Cargar**|Inicia el asistente para **Cargar actualización**, que permite cargar las actualizaciones que no son de Microsoft que quiera implementar.|

### Para aprobar actualizaciones

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Actualizaciones** &gt; **Información general** &gt; **Nuevas actualizaciones para aprobar**..

    En el área de trabajo **Actualizaciones**, seleccione **Introducción** &gt; **Nuevas actualizaciones para aprobar**..

    > [!NOTE]
    > El vínculo **Nuevas actualizaciones para aprobar** aparece en el área **Estado de actualización** solo cuando hay, al menos, un equipo administrado que necesita la autorización de una actualización.

2.  Seleccione una actualización, revise las propiedades de la actualización en la parte inferior de la página para asegurarse de que desea aprobar la actualización y, después, seleccione **Aprobar**. Para seleccionar varias actualizaciones, mantenga presionada la tecla **CTRL** mientras selecciona cada elemento.

3.  En la página **Seleccionar grupos**, seleccione un grupo en el que desee implementar las actualizaciones y, después, seleccione **Agregar**. Cuando haya terminado de especificar los grupos, seleccione **Siguiente**..

4.  En la página **Acción de implementación** , realice lo siguiente para cada grupo de la lista:

    -   En la lista **Aprobación** , seleccione una de las siguientes opciones:

        -   **Instalación requerida**: instala la actualización en los equipos del grupo especificado.

        -   **No instalar**: solo informa de que se puede aplicar, pero no instala la actualización.

        -   **Instalación disponible** : el usuario puede instalar la aplicación a petición desde el portal de empresa.

        -   **Desinstalar**: quita las actualizaciones de los equipos del grupo de destino.

            > [!IMPORTANT]
            > La actualización se quita aunque no se haya instalado mediante Intune.

    -   En la lista **Fecha límite** , seleccione una de las siguientes opciones:

        -   **Ninguna**: indica que no hay fecha límite para la instalación de la actualización y los usuarios podrán rechazar la actualización continuamente.

        -   **Lo antes posible**: instala la actualización a la primera oportunidad en todos los equipos de destino.

        -   **Personalizada**: especifica la fecha y hora en que las actualizaciones aprobadas se instalarán.

        -   **Una semana**, **Dos semanas**, **Un mes** – Instala la actualización en el período de tiempo especificado.

5.  Seleccione **Finalizar** para guardar la configuración o **Cancelar** para descartar la configuración y volver a la lista de actualizaciones.

    > [!IMPORTANT]
    > A menos que se configurase explícitamente la acción **No instalar**, **Instalación requerida**o **Desinstalar** para un grupo secundario, una acción configurada para un grupo principal es heredada por todos sus grupos secundarios.

6.  Puede comprobar los mensajes recordatorios acerca de la actualización en el panel de detalles de la parte inferior de la página **Todas las actualizaciones** .


### Consulte también
[Directivas para proteger equipos de Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


