---
title: "Tareas comunes de administración de PC Windows | Microsoft Intune"
description: Revise las tareas de este tema para aprender a administrar los equipos que ejecutan el software del equipo cliente de Intune.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb912c73-54d2-4d78-ac34-3cbe825804c7
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: dcfa3af374a7e64e931508e1a8022bf8a50c71a7
ms.openlocfilehash: 93d5718fcd9949945180434b0f89eea96e92bbc6


---

# Tareas comunes de administración de PC Windows con el cliente de equipo de Microsoft Intune
Revise las tareas de este tema para aprender a administrar los equipos que ejecutan el software del equipo cliente de Intune. Si aún no tiene instalado el cliente en los equipos, vea [Install the Windows PC client with Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md) (Instalar el cliente de PC Windows con Microsoft Intune).


## Usar directivas para simplificar la administración de equipos
### Administrar el Firewall de Windows
Las directivas simplifican la administración de la configuración del Firewall de Windows en los equipos administrados. Para más información, vea [Ayudar a proteger los equipos de Windows mediante directivas del Firewall de Windows en Microsoft Intune](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md).

### Administrar Microsoft Intune Center
Con Microsoft Intune Center se puede hacer lo siguiente:

-   Obtener aplicaciones desde el portal de empresa.

-   Comprobar si hay actualizaciones.

-   Administrar Microsoft Intune Endpoint Protection.

-  Solicitar asistencia remota.

Microsoft Intune Center se instala en todos los equipos administrados. En una directiva de Intune se pueden establecer las siguientes opciones de configuración, que se mostrarán a los usuarios en Microsoft Intune Center:

|Configuración de directiva|Detalles|
|------------------|--------------------|
|**Nombre**|El nombre del administrador del equipo.<br /><br />Longitud máxima: 40 caracteres|
|**Número de teléfono**|El número de teléfono del administrador del equipo.<br /><br />Longitud máxima: 20 caracteres|
|**Dirección de correo electrónico**|La dirección de correo electrónico del administrador del equipo.<br /><br />Longitud máxima: 40 caracteres|
|**Nombre del sitio web**|El nombre del sitio web de soporte para los usuarios.<br /><br />Longitud máxima: 40 caracteres|
|**Dirección URL del sitio web**|La dirección URL del sitio web de soporte.<br /><br />Longitud máxima: 150 caracteres|
|**Notas**|Una nota que se muestra a los usuarios.<br /><br />Longitud máxima: 120 caracteres|

### Administrar la configuración de actualizaciones de software
Use directivas para establecer la configuración que los equipos administrados utilizan para buscar y descargar actualizaciones de software de Microsoft y de otros fabricantes. Para más información, vea [Mantener los equipos Windows al día con las actualizaciones de software en Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).

### Administrar la configuración de Endpoint Protection
Use directivas para establecer la configuración de Endpoint Protection que luego implementará en los equipos administrados. Esto incluye, entre otras cosas, la programación de exámenes y las acciones que hay que realizar cuando se detecta malware. Para más información, vea [Ayudar a proteger los equipos de Windows con Endpoint Protection para Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).

## Ver el Inventario de hardware y software
Intune recopila información detallada sobre el hardware y el software de los equipos administrados. Use la información de los siguientes procedimientos para aprender a crear:

-   Un informe que muestra información acerca de las capacidades de hardware de los equipos.

-   Un informe que muestra la lista de software instalado en cada equipo.

-   Cómo actualizar un inventario de equipos para asegurarse de que los datos del informe estén al día.

### Para mostrar información acerca de los equipos

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Informes** &gt; **Informes de inventario de equipos**.

2.  En la página **Crear nuevo informe** , acepte los valores predeterminados o personalícelos para filtrar los resultados devueltos por el informe. Por ejemplo, puede seleccionar que en el informe sólo se muestren los equipos que ejecutan Windows 8.1.

3.  Elija **Ver informe** para abrir el **Informe de inventario de equipos** en otra ventana.

    Para ordenar el informe por cualquiera de las columnas, seleccione el encabezado de columna correspondiente, como **Nombre**, **Tipo de chasis** o **Fabricante**.

### Para mostrar el software instalado en sus equipos

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Informes** &gt; **Informes de software detectado**.

2.  En la página **Crear nuevo informe** , acepte los valores predeterminados o personalícelos para filtrar los resultados devueltos por el informe. Por ejemplo, puede seleccionar que en el informe sólo se muestre el software publicado por Microsoft.

3.  Elija **Ver informe** para abrir el **Informe de software detectado** en otra ventana.

    Para ordenar el informe por cualquiera de las columnas, seleccione el encabezado de columna correspondiente, como **Nombre**, **Editor** o **Categoría**. Puede seleccionar la flecha situada junto al elemento de lista para expandir las actualizaciones de la lista a fin de mostrar más detalles (como los equipos en los que están instaladas).

### Para actualizar el inventario de equipos a fin de asegurarse de que está al día

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos ** (u otro grupo que contenga el equipo para el que quiera actualizar el inventario).

2.  Seleccione un equipo o mantenga presionada la tecla **Ctrl** para seleccionar varios equipos.

3.  En la barra de tareas, seleccione **Tareas remotas** &gt; **Actualizar inventario**.

4.  Para ver el estado de la tarea, seleccione **Tareas remotas** en la esquina inferior derecha de la página.

    Se abre el cuadro de diálogo **Estado de la tarea** , que muestra las tareas remotas actuales, el estado de la tarea, el nombre del dispositivo y los errores notificados, y proporciona un vínculo a información de solución de problemas, si es necesario.


## Reiniciar un PC Windows de forma remota

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** (u otro grupo que contenga el equipo que quiera reiniciar).

2.  Seleccione uno o más equipos y, después, seleccione **Tareas remotas** &gt; **Reiniciar el equipo**.

3.  Para ver el estado de la tarea, seleccione **Tareas remotas** en la esquina inferior derecha de la página.

4.  En el cuadro de diálogo **Estado de la tarea** , revise las tareas remotas actuales, el estado de la tarea, el nombre del dispositivo y los errores notificados.

## Retirar un equipo

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** (u otro grupo que contenga el equipo que quiera retirar).

2.  Seleccione los dispositivos que quiera retirar y, después, elija **Retirar/Eliminar datos**.

Para volver a inscribir un equipo en Intune, reinstale el software cliente en el equipo según se indica en el tema [Install the Windows PC client with Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md) (Instalar el cliente de PC Windows con Microsoft Intune).

Si un equipo no se puede conectar a Intune, verá un mensaje en el área de trabajo **Panel**.

Cuando retira un equipo:

-   Se quita del inventario y la administración de Intune y la licencia asociada al equipo queda disponible para poder reutilizarla. La opción de retirar o borrar un equipo quita el cliente del software de Intune, pero no elimina las aplicaciones o los datos del equipo.

-   Su estado deja de aparecer en la consola de Intune.

-   Intune quita el software cliente del equipo. Si el equipo no está conectado al servicio de Intune, se quitará el software cliente la próxima vez que se conecte.

-   Microsoft Intune Endpoint Protection se quita del equipo. Si el equipo tiene instalada otra aplicación de extremos que está deshabilitada, esa aplicación se puede volver a habilitar después de quitar Microsoft Intune Endpoint Protection y, así, garantizar la protección del equipo.

-   Se quitan las directivas del equipo y se cambian los valores establecidos por las directivas.

-   El equipo deja de recibir actualizaciones de software o de definiciones de malware procedentes del servicio de Intune.

-   Según como estén configurados, los equipos retirados pueden seguir recibiendo actualizaciones mediante Windows Server Update Services, Windows Update o Microsoft Update.

    > [!IMPORTANT]
    > Si el software cliente se instaló con un objeto de directiva de grupo (GPO), debe quitar dicho objeto para poder quitar el software cliente, a fin de evitar que el software se reinstale.

    Si el cliente no se puede desinstalar, lea [Solucionar problemas de Endpoint Protection en Microsoft Intune](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) para obtener más ayuda.

## Administrar la vinculación de dispositivos de usuario
Antes de implementar software en un usuario, debe vincular el usuario a un equipo. Puede vincular un usuario a varios equipos, pero cada equipo puede vincularse sólo a un usuario. Los usuarios se vinculan automáticamente a los equipos que tengan inscritos en Intune a través del portal de la empresa.

### Para vincular un usuario a un equipo

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** (u otro grupo que contenga el equipo que quiera vincular a un usuario).

2.  Seleccione el equipo que quiera vincular a un usuario y, después, elija **Vincular usuario**.

    El cuadro de diálogo **Vincular usuario** muestra una lista de usuarios disponibles con su nombre para mostrar, Id. de usuario, y el número de equipos a los que cada usuario que está vinculado. Si un usuario ya está vinculado al equipo seleccionado, el nombre del usuario y su Id. se muestran en **Usuario actual**. Si el equipo no está vinculado a ningún usuario, aparece **Ningún usuario** bajo el **Usuario actual**.

3.  Realice una de las siguientes acciones:

    -   Para dejar el equipo vinculado a su usuario actual (si lo hay), seleccione **Cancelar**.

    -   Para quitar el vínculo al usuario actual (si lo hay), seleccione **Quitar vínculo** &gt; **Aceptar**.

    -   Para vincular el equipo a un usuario nuevo, en la lista **Todos los usuarios** , seleccione un usuario. Confirme que los datos de usuario son correctos y, luego, seleccione **Aceptar**.

> [!TIP]
> Si desea restringir la capacidad de los usuarios finales para vincularse a equipos, habilite la opción **Restringir la capacidad de los usuarios de vincularse a equipos** en la directiva de **Configuración de agente de Microsoft Intune**.

## Solicitar y ofrecer asistencia remota a los equipos de Windows que usan el software cliente de Intune

Microsoft Intune puede usar el software [TeamViewer](https://www.teamviewer.com) para que usted pueda ofrecer asistencia remota a los usuarios de equipos que ejecutan el software cliente de Intune. Cuando un usuario solicita ayuda a Microsoft Intune Center, usted recibe una alerta, puede aceptar la solicitud y, luego, proporcionar asistencia.
Esta funcionalidad reemplaza la funcionalidad de asistencia remota de Windows existente en Intune.


### Antes de empezar

Antes de empezar a establecer las solicitudes de asistencia remota y responderlas, debe asegurarse de haber cumplido los requisitos previos siguientes:

- Debe haber [registrado una cuenta de TeamViewer](https://login.teamviewer.com/LogOn#register) para iniciar sesión en el sitio web de TeamViewer.
- Debe administrar los equipos Windows mediante [el cliente de equipos Windows](manage-windows-pcs-with-microsoft-intune.md)
- Se pueden administrar todos los sistemas operativos de equipos Windows que Intune admite.

### Configurar el conector de TeamViewer

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Administración**.
2. En el área de trabajo **Administración**, elija **TeamViewer**.
3. En la página **TeamViewer**, en **Conector de TeamViewer**, elija **Habilitar**.
4. En el cuadro de diálogo **Habilitar TeamViewer**, lea los términos de licencia y, después, haga clic en **Aceptar**. Si aún no tiene una licencia de TeamViewer, elija **Comprar una licencia de TeamViewer**.
5. Una vez abierta la ventana del explorador de TeamViewer, inicie sesión en el sitio con sus credenciales de TeamViewer.
6. En el sitio de TeamViewer, lea y acepte las opciones para permitir que Intune se conecte con TeamViewer.
7. En la consola de Intune, compruebe que el elemento **Conector de TeamViewer** aparece como **Habilitado**.


### Abrir una solicitud de asistencia remota (usuario final)

1. En un equipo Windows de cliente, abra **Microsoft Intune Center**.
2. En **Asistencia remota**, elija **Solicitar asistencia remota**.
3. Después de aprobar la solicitud (ver abajo), TeamViewer se abre en el cliente. El usuario debe aceptar los mensajes en los que se indique que el explorador web está intentando abrir la aplicación TeamViewer.
4. El usuario ve un mensaje en el que se le pregunta si usted puede controlar el equipo de dicho usuario. Él debe aceptar este mensaje para continuar.
5. Durante la sesión de asistencia remota, el usuario ve una ventana que muestra que usted está conectado. Si el usuario cierra esta ventana, la sesión remota finaliza.

### Responder a una solicitud de asistencia remota

1. Cuando un usuario envía una solicitud de asistencia remota, usted puede verlo en el área de trabajo **Alertas**, en **Supervisión** > **Asistencia remota**. Por ejemplo:
> ![Captura de pantalla de una solicitud de asistencia remota](./media/team-viewer.png)

<br>Si no contesta a una solicitud pasadas 4 horas, se quita.
2. Para aceptar la solicitud, elija **Aprobar solicitud e iniciar asistencia remota**.
3. En el cuadro de diálogo **Hay una nueva solicitud de asistencia remota pendiente**, elija **Aceptar la solicitud de asistencia remota**. Si aún no están instaladas, TeamViewer instalará las aplicaciones necesarias en el equipo.
4. Después, TeamViewer notifica al usuario final que usted quiere tomar el control de su equipo. Después de que el usuario ha aceptado la solicitud, la ventana de TeamViewer se abre y usted puede controlar el equipo.

Durante una sesión de asistencia remota, puede usar todos los comandos de TeamViewer disponibles para controlar el equipo remoto. Para obtener ayuda con estos comandos, descargue el [Manual de control remoto](http://www.teamviewer.com/en/support/documents/) desde el sitio web de TeamViewer.

### Cerrar la sesión de asistencia remota

En el menú **Acciones** de la ventana **TeamViewer**, elija **Finalizar sesión**.



<!--HONumber=Aug16_HO1-->


