---

title: Instalar el software cliente de PC | Microsoft Intune
description: "Siga esta guía para administrar sus equipos Windows con el software cliente de Microsoft Intune."
keywords: 
author: staciebarker
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 103e7065d1e2c3281f8f04808ee2546d3c7e2b53
ms.openlocfilehash: 32af8a615453b8c72e704f40dcdf0de6fbf10907


---

# <a name="install-the-intune-software-client-on-windows-pcs"></a>Instalar el cliente de software de Intune en equipos con Windows
Los equipos con Windows se pueden inscribir instalando el software cliente de Intune. El software cliente de Intune se puede instalar de las maneras siguientes:

- Instalado manualmente
- Instalado mediante directivas de grupo
- Incluido en una imagen de disco
- Instalado por parte de los usuarios

El software cliente de Intune que se descarga primero contiene el software mínimo necesario para inscribir el equipo en la administración de Intune. Después de inscribir un equipo, el software cliente de Intune descarga el software cliente completo que se necesita para la administración del equipo.

Esta serie de descargas minimiza el tiempo necesario para inscribir inicialmente su equipo en Intune. También garantiza que el cliente tenga disponible el software más reciente una vez finalizada la segunda descarga.

## <a name="download-the-intune-client-software"></a>Descargar el software cliente de Intune

Para todos los métodos, excepto en el que los usuarios mismos instalan el software cliente de Intune, debe descargar el software para poder implementarlo.

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), haga clic en **Administración** &gt; **Descargar software cliente**.

  ![Descargar el cliente de equipo de Intune](../media/pc-sa-client-download.png)

2.  En la página **Descarga de software cliente**, haga clic en **Descargar software cliente**. A continuación, guarde el paquete **Microsoft_Intune_Setup.zip** que contiene el software en una ubicación segura de la red.

    > [!NOTE]
    > El paquete de instalación del software cliente de Intune contiene información sobre su cuenta. Si usuarios no autorizados obtienen acceso al paquete de instalación, estos podrán inscribir los equipos en la cuenta representada por el certificado incrustado y acceder a los recursos de la empresa.

3.  Extraiga el contenido del paquete de instalación en la ubicación segura de la red.

    > [!IMPORTANT]
    > No cambie de nombre ni quite el archivo **ACCOUNTCERT** extraído; de lo contrario, la instalación del software cliente no funcionará.

## <a name="deploy-the-client-software-manually"></a>Implementar el software cliente manualmente

En un equipo, vaya a la carpeta donde se encuentran los archivos de instalación de software cliente. A continuación, ejecute **Microsoft_Intune_Setup.exe** para instalar el software cliente.

    > [!NOTE]
    > The status of the installation is displayed when you hover over the icon in the taskbar on the client computer.

## <a name="deploy-the-client-software-by-using-group-policy"></a>Implementar el software cliente mediante una directiva de grupo

1.  En la carpeta que contiene los archivos **Microsoft_Intune_Setup.exe** y **MicrosoftIntune.accountcert**, ejecute el siguiente comando para extraer los programas de instalación basados en Windows Installer para equipos de 32 bits y 64 bits:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  Copie los archivos **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** y **MicrosoftIntune.accountcert** en una ubicación de red a la que tengan acceso todos los equipos en los que se va a instalar el software cliente.

    > [!IMPORTANT]
    > No separe los archivos ni cambie sus nombres; de lo contrario, se producirá un error en la instalación del software cliente.

3.  Use la directiva de grupo para implementar el software en los equipos de la red.

    Para obtener más información acerca de cómo utilizar la directiva de grupo para implementar software automáticamente, consulte la documentación de Windows Server.

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

Los usuarios pueden instalar el software cliente de Intune desde el [sitio web del portal de empresa](http://portal.manage.microsoft.com). Si el portal web puede detectar que el dispositivo es un equipo con Windows, se solicitará a los usuarios que lo inscriban descargando el software cliente de Intune. Una vez descargado el software, los usuarios pueden instalarlo para incorporar sus equipos a la administración.

![El portal de Intune solicita descargar el cliente de software de Intune](../media/software-client-download.png)

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


### <a name="see-also"></a>Consulte también
[Administrar equipos Windows con Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
[Solucionar los problemas de configuración del cliente en Microsoft Intune](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune.md)



<!--HONumber=Nov16_HO5-->


