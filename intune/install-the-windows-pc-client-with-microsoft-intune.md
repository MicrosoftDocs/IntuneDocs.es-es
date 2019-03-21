---
title: Instalación del software cliente del PC
description: Siga esta guía para administrar sus equipos Windows con el software cliente de Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
ms.date: 07/13/2017
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: d68f4151dc8b10ef716524f2422f532dec6693f9
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57461250"
---
# <a name="install-the-intune-software-client-on-windows-pcs"></a>Instalar el cliente de software de Intune en equipos con Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

> [!NOTE]
> Puede usar Microsoft Intune para administrar equipos con Windows [como dispositivos móviles con la administración de dispositivos móviles (MDM)](windows-enroll.md) o como equipos con el software cliente de Intune, tal y como se describe a continuación. Sin embargo, Microsoft recomienda que los clientes [usen la solución de administración de MDM](windows-enroll.md) siempre que sea posible. Para más información, consulte [Comparación de la administración de equipos con Windows como dispositivos móviles o equipos](pc-management-comparison.md). 


Los equipos con Windows se pueden inscribir instalando el software cliente de Intune. El software cliente de Intune se puede instalar siguiendo los métodos siguientes:

- Mediante el administrador de TI, con uno de estos métodos: instalación manual, directiva de grupo o instalación incluida en una imagen de disco

- Mediante los usuarios finales, que instalan manualmente el software cliente

El software cliente de Intune contiene el software mínimo necesario para inscribir el equipo en la administración de Intune. Después de inscribir un equipo, el software cliente de Intune descarga el software cliente completo que se necesita para la administración del equipo.

Esta serie de descargas reduce el impacto en el ancho de banda de la red y reduce al mínimo el tiempo necesario para inscribir inicialmente el equipo en Intune. También garantiza que el cliente tenga disponible el software más reciente una vez finalizada la segunda descarga.

Una licencia de Intune permite instalar el software cliente de Intune en un máximo de cinco equipos.

## <a name="download-the-intune-client-software"></a>Descargar el software cliente de Intune

Todos los métodos, excepto aquellos en los que los usuarios instalan el software cliente de Intune, requieren que los administradores de TI descarguen el software primero para que pueda implementarse posteriormente en los usuarios finales.

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), haga clic en **Administración** &gt; **Descargar software cliente**.

   ![Descargar el cliente de equipo de Intune](./media/https://docs.microsoft.com/intune/media/install-the-windows-pc-client/pc-sa-client-download.png)

2. En la página **Descarga de software cliente**, haga clic en **Descargar software cliente**. A continuación, guarde el paquete **Microsoft_Intune_Setup.zip** que contiene el software en una ubicación segura de la red.

   El paquete de instalación del software cliente de Intune contiene información exclusiva y específica, que está disponible a través de un certificado insertado, sobre su cuenta. Si usuarios no autorizados obtienen acceso al paquete de instalación, estos podrán inscribir los equipos en la cuenta representada por el certificado insertado y acceder a los recursos de la empresa.

3. Extraiga el contenido del paquete de instalación en la ubicación segura de la red.

    > [!IMPORTANT]
    > No cambie de nombre ni quite el archivo **ACCOUNTCERT** extraído; de lo contrario, la instalación del software cliente no funcionará.

## <a name="deploy-the-client-software-manually"></a>Implementar el software cliente manualmente

En los equipos en los que el software cliente se va a instalar, vaya a la carpeta donde se encuentran los archivos de instalación del software cliente. A continuación, ejecute **Microsoft_Intune_Setup.exe** para instalar el software cliente.

> [!NOTE]
> El estado de la instalación se muestra al colocar el puntero sobre el icono de la barra de tareas en el equipo cliente.

## <a name="deploy-the-client-software-by-using-group-policy"></a>Implementar el software cliente mediante una directiva de grupo

1.  En la carpeta que contiene los archivos **Microsoft_Intune_Setup.exe** y **MicrosoftIntune.accountcert**, ejecute el siguiente comando para extraer los programas de instalación basados en Windows Installer para equipos de 32 bits y 64 bits:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  Copie los archivos **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** y **MicrosoftIntune.accountcert** en una ubicación de red a la que tengan acceso todos los equipos en los que se va a instalar el software cliente.

    > [!IMPORTANT]
    > No separe los archivos ni cambie sus nombres; de lo contrario, se producirá un error en la instalación del software cliente.

3.  Use la directiva de grupo para implementar el software en los equipos de la red.

    Para más información sobre cómo usar la directiva de grupo para implementar software automáticamente, consulte [Directiva de grupo para principiantes](https://technet.microsoft.com/library/hh147307.aspx).

## <a name="deploy-the-client-software-as-part-of-an-image"></a>Implementar el software cliente como parte de una imagen
El software cliente de Intune se puede implementar en equipos como parte de una imagen de sistema operativo. Para ello, puede usar el siguiente procedimiento como guía:

1.  Copie los archivos de instalación del cliente, **Microsoft_Intune_Setup.exe** y **MicrosoftIntune.accountcert**, en la carpeta **%Systemdrive%\Temp\Microsoft_Intune_Setup** del equipo de referencia.

2.  Cree la entrada **WindowsIntuneEnrollPending** en el Registro agregando el siguiente comando al script **SetupComplete.cmd** :

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3.  Agregue el siguiente comando a **setupcomplete.cmd** para ejecutar el paquete de inscripción con el argumento de línea de comandos /PrepareEnroll:

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > El script **SetupComplete.cmd** permite que el programa de instalación de Windows realice modificaciones en el sistema antes de que un usuario inicie sesión. El argumento de línea de comandos **/PrepareEnroll** prepara un equipo de destino para inscribirse automáticamente en Intune cuando haya finalizado la instalación de Windows.

4.  Coloque **SetupComplete.cmd** en la carpeta **%Windir%\Setup\Scripts** del equipo de referencia.

5.  Capture una imagen del equipo de referencia y, a continuación, impleméntela en los equipos de destino.

    Cuando se reinicie el equipo de destino al finalizar la instalación de Windows, se creará la clave **WindowsIntuneEnrollPending** en el Registro. El paquete de inscripción comprueba si el equipo está inscrito. Si el equipo está inscrito, no se realiza ninguna otra acción. Si el equipo no está inscrito, el paquete de inscripción crea una tarea de inscripción automática de Microsoft Intune.

    Cuando se ejecuta la tarea de inscripción automática a la siguiente hora programada, se comprueba la existencia del valor **WindowsIntuneEnrollPending** en el Registro y se intenta inscribir el equipo de destino en Intune. Si por algún motivo se produjera un error en la inscripción, se reintentará la inscripción la próxima vez que se ejecute la tarea. Los reintentos continuarán durante un mes.

    La tarea de inscripción automática de Intune, el valor **WindowsIntuneEnrollPending** del Registro y el certificado de cuenta se eliminarán del equipo de destino cuando se haya inscrito correctamente o al cabo de un mes, lo que suceda primero.

## <a name="instruct-users-to-self-enroll"></a>Indicar a los usuarios que efectúen una inscripción automática

Los usuarios instalan el software cliente de Intune desde el [sitio web del portal de empresa](https://portal.manage.microsoft.com). La información exacta que ven los usuarios en el portal web varía, dependiendo de la entidad de MDM de la cuenta y la plataforma y la versión de sistema operativo del equipo del usuario.

Si a los usuarios no se les ha asignado una licencia de Intune o si la entidad de MDM de la organización no se ha establecido en Intune, los usuarios no ven ninguna opción para inscribirse.

Si a los usuarios se les ha asignado una licencia de Intune y la entidad de MDM de la organización se ha establecido en Intune:

- Los usuarios de equipos con Windows 7 o Windows 8 ven SOLO la opción de inscribirse a Intune mediante la descarga e instalación del software cliente de PC que es única para su organización.

- A los usuarios de equipos con Windows 10 o Windows 8.1 se les muestran dos opciones de inscripción:

  -  **Inscribir el equipo como un dispositivo móvil**: los usuarios pulsan el botón **Cómo inscribirse** y se les dirige a las instrucciones sobre cómo inscribir sus equipos como un dispositivo móvil. Este botón se muestra claramente, ya que la inscripción de MDM se considera la opción de inscripción preferida y predeterminada. En cambio, la opción de MDM no se aplica a este tema, que trata solo la instalación del software cliente.
  - **Inscribir el equipo con el software cliente de Intune**: necesitará indicar a los usuarios que seleccionen el vínculo **Haga clic aquí para descargar**, que les guía a través de la instalación del software cliente.

En la siguiente tabla se resumen las opciones.

  ![Opciones de inscripción predeterminadas por plataforma](./media/install-the-windows-pc-client/default-enrollment-options-table.png)

En las siguientes capturas de pantalla se muestra lo que ven los usuarios a medida que inscriben sus dispositivos con el software cliente.

Primero, a los usuarios se les pide que identifiquen o inscriban su dispositivo.

  ![identificar o inscribir el dispositivo](./media/install-the-windows-pc-client/identify-device-or-enroll.png)

Para que los usuarios instalen el software cliente del equipo, necesitará indicarles que seleccionen el vínculo **Haga clic aquí para descargar**, que permite a los usuarios descargar el software cliente del equipo y guiarles a través del proceso de instalación. El botón **Cómo inscribirse** dirige a los usuarios a la documentación sobre cómo inscribirse con la inscripción de MDM, que no es relevante a esas instrucciones del software cliente.

  ![pulsar el vínculo Haga clic aquí para descargar](./media/install-the-windows-pc-client/enroll-your-windows-device.png)

Cuando los usuarios hacen clic en el vínculo, ven un botón **Descargar software**, que seleccionan para iniciar la instalación del software cliente del equipo.

  ![pulsar el botón Descargar software](./media/install-the-windows-pc-client/download-pc-client-software.png)

Después, a los usuarios se les pide que inicien sesión con sus credenciales corporativas.

  ![Iniciar sesión con sus credenciales](./media/install-the-windows-pc-client/sign-in-to-intune.png)

Se dirige a los usuarios a la página principal de la instalación.

  ![Página principal de la instalación cliente del equipo](./media/install-the-windows-pc-client/welcome-to-pc-agent-install-wizard.png)

Los usuarios pulsan **Siguiente** y la instalación se inicia.

  ![Página principal de la instalación cliente del equipo](./media/install-the-windows-pc-client/welcome-to-pc-agent-install-wizard.png)

Cuando se completa la instalación, los usuarios pulsan **Finalizar**.

  ![Finalizar la instalación cliente del equipo](./media/install-the-windows-pc-client/completed-the-setup-wizard.png)

Si los usuarios intentan inscribir su equipo como un dispositivo móvil después de que ya esté inscrito con el software cliente de equipo de Intune, verán la siguiente pantalla de error.

  ![Pantalla que se muestra si el equipo ya está inscrito](./media/install-the-windows-pc-client/page-shown-if-pc-already-enrolled.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>Supervisión y validación de una implementación correcta del cliente
Use uno de los procedimientos siguientes como ayuda para supervisar y validar una implementación correcta del cliente.

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>Para comprobar la instalación del software cliente mediante la consola de administrador de Microsoft Intune

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), haga clic en **Grupos** &gt; **Todos los dispositivos** &gt; **Todos los equipos**.

2.  En la lista, busque los equipos que se estén comunicando con Intune o busque un equipo administrado específico escribiendo el nombre del equipo (o una parte de él) en el cuadro **Buscar dispositivos**.

3.  Examine el estado del equipo en el panel inferior de la consola. Resuelva los errores.

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>Para crear un informe de inventario de equipo que muestre todos los equipos inscritos

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), haga clic en **Informes** &gt; **Informes de inventario de equipos**.

2.  En la página **Crear nuevo informe** , deje los valores predeterminados en todos los campos (a menos que desee aplicar filtros) y haga clic en **Ver informe**.

3.  Se abre la página de **Informe de inventario de equipos** en una nueva ventana que muestra todos los equipos que están inscritos correctamente en Intune.

    > [!TIP]
    > Para ordenar la lista del informe por el contenido de una columna, haga clic en el encabezado de esa columna.

## <a name="uninstall-the-windows-client-software"></a>Desinstalar el software de cliente de Windows

Hay dos formas de anular la inscripción del software de cliente de Windows:

- Desde la consola de administración de Intune (método recomendado)
- Desde un símbolo del sistema en el cliente

### <a name="unenroll-by-using-the-intune-admin-console"></a>Anular la inscripción mediante la consola de administración de Intune

Para anular la inscripción del software cliente mediante la consola de administración de Intune, vaya a **Grupos** > **Todos los equipos** > **Dispositivos**. Haga clic con el botón derecho en el cliente y seleccione **Retirar/Eliminar datos**.

### <a name="unenroll-by-using-a-command-prompt-on-the-client"></a>Anular la inscripción mediante un símbolo del sistema en el cliente

Desde un símbolo del sistema con privilegios elevados, ejecute uno de los siguientes comandos.

**Método 1**:

    "C:\Program Files\Microsoft\OnlineManagement\Common\ProvisioningUtil.exe" /UninstallAgents /MicrosoftIntune

**Método 2** Tenga en cuenta que todos los agentes están instalados en cada SKU de Windows:

    wmic product where name="Microsoft Endpoint Protection Management Components" call uninstall
    wmic product where name="Microsoft Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Microsoft Online Management Policy Agent" call uninstall
    wmic product where name="Microsoft Policy Platform" call uninstall
    wmic product where name="Microsoft Security Client" call uninstall
    wmic product where name="Microsoft Online Management Client" call uninstall
    wmic product where name="Microsoft Online Management Client Service" call uninstall
    wmic product where name="Microsoft Easy Assist v2" call uninstall
    wmic product where name="Microsoft Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Microsoft Intune Center" call uninstall
    wmic product where name="Microsoft Online Management Update Manager" call uninstall
    wmic product where name="Microsoft Online Management Agent Installer" call uninstall
    wmic product where name="Microsoft Intune" call uninstall
    wmic product where name="Windows Endpoint Protection Management Components" call uninstall
    wmic product where name="Windows Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Windows Online Management Policy Agent" call uninstall
    wmic product where name="Windows Policy Platform" call uninstall
    wmic product where name="Windows Security Client" call uninstall
    wmic product where name="Windows Online Management Client" call uninstall
    wmic product where name="Windows Online Management Client Service" call uninstall
    wmic product where name="Windows Easy Assist v2" call uninstall
    wmic product where name="Windows Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Windows Intune Center" call uninstall
    wmic product where name="Windows Online Management Update Manager" call uninstall
    wmic product where name="Windows Online Management Agent Installer" call uninstall
    wmic product where name="Windows Intune" call uninstall

> [!TIP]
> La anulación de la suscripción del cliente dejará un registro obsoleto del lado del servidor para el cliente afectado. El proceso de anulación de la suscripción es asincrónico y hay nueve agentes que desinstalar, por lo que puede tardar hasta 30 minutos en completarse.

### <a name="check-the-unenrollment-status"></a>Comprobar el estado de la anulación de la suscripción

Compruebe "%ProgramFiles%\Microsoft\OnlineManagement" y asegúrese de que solo se muestran los siguientes directorios a la izquierda:

- AgentInstaller
- Registros
- Updates
- Común

### <a name="remove-the-onlinemanagement-folder"></a>Quitar la carpeta OnlineManagement

El proceso de anulación de la suscripción no elimina la carpeta OnlineManagement. Espere 30 minutos después de la desinstalación y luego ejecute este comando. Si se ejecuta demasiado pronto, la desinstalación podría quedar en un estado desconocido. Para quitar la carpeta, abra una ventana de símbolo del sistema con privilegios elevados y ejecute:

    "rd /s /q %ProgramFiles%\Microsoft\OnlineManagement".

### <a name="next-steps"></a>Pasos siguientes
[Tareas comunes de administración de equipos Windows con el cliente de software de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
