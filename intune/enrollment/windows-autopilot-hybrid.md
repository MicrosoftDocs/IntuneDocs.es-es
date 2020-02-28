---
title: 'Inscripción para dispositivos unidos a Azure AD híbrido: Windows Autopilot'
titleSuffix: ''
description: Use Windows Autopilot para inscribir dispositivos unidos a Azure AD híbrido en Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d87a4b5d46a5f0d40cebe3dbcaff211ff508d667
ms.sourcegitcommit: 822a70c61f5d644216ccc401b8e8949bc39e8d4a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76125317"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot"></a>Implementación de dispositivos unidos a Azure AD híbrido mediante Intune y Windows Autopilot
Puede usar Intune y Windows Autopilot para configurar dispositivos unidos a Azure Active Directory (Azure AD) híbrido. Para ello, siga los pasos de este artículo.

## <a name="prerequisites"></a>Requisitos previos

Configure correctamente los [dispositivos unidos a Azure AD híbrido](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan). Asegúrese de [comprobar el registro del dispositivo](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration) mediante el cmdlet Get-MsolDevice.

Los dispositivos que se inscriban también deben:
- Ejecutar la versión 1809 o superiores de Windows 10.
- Tener acceso a Internet [siguiendo los requisitos de red documentados de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements#networking-requirements).
- Tener acceso a un controlador de dominio de Active Directory, por lo que debe estar conectado a la red de la organización (donde puede resolver los registros DNS para el dominio de AD y el controlador de dominio de AD, y comunicarse con el controlador de dominio para autenticar al usuario). La conexión VPN no se admite en este momento.
- Ser capaces de hacer ping al controlador de dominio del dominio al que está intentando unirse.
- Si utiliza el proxy, la opción de configuración del proxy WPAD debe estar activada y configurada.
- Realizar la configuración rápida (OOBE).

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurar la inscripción automática de Windows 10

1. Inicie sesión en Azure y, en el panel de la izquierda, seleccione **Azure Active Directory**.

   ![Azure Portal](./media/windows-autopilot-hybrid/auto-enroll-azure-main.png)

1. Seleccione **Movilidad (MDM y MAM)** .

   ![El panel Azure Active Directory](./media/windows-autopilot-hybrid/auto-enroll-mdm.png)

1. Seleccione **Microsoft Intune**.

   ![El panel Movilidad (MDM y MAM)](./media/windows-autopilot-hybrid/auto-enroll-intune.png)

1. Asegúrese de que los usuarios que implementan dispositivos unidos a Azure AD mediante Intune y Windows son miembros de un grupo incluido en el **ámbito de usuario de MDM**.

   ![El panel de configuración de Movilidad (MDM y MAM)](./media/windows-autopilot-hybrid/auto-enroll-scope.png)

1. Use los valores predeterminados de los cuadros **URL de las condiciones de uso de MDM**, **Dirección URL de descubrimiento de MDM** y **Dirección URL de cumplimiento de MDM**, y después haga clic en **Guardar**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Aumento del límite de la cuenta de equipo en la unidad organizativa

El conector de Intune para Active Directory crea equipos inscritos con Autopilot en el dominio local de Active Directory. El equipo que hospeda el conector de Intune debe tener los derechos para crear los objetos de equipo dentro del dominio. 

En algunos dominios, no se concede a los equipos derechos para crear equipos. Además, los dominios tienen un límite integrado (valor predeterminado de 10) que se aplica a todos los usuarios y equipos en los que no se delegan derechos para crear objetos de equipo. Por tanto, los derechos se deben delegar en equipos que hospedan el conector de Intune en la unidad organizativa donde se crean los dispositivos unidos a Azure AD híbrido.

La unidad organizativa a la que se conceden los derechos para crear equipos debe coincidir con:
- la unidad organizativa especificada en el perfil Unión a dominio.
- Si no se ha seleccionado ningún perfil, el nombre de dominio del equipo para el dominio.

1. Abra **Usuarios y equipos de Active Directory (DSA.msc)** .

1. Haga clic con el botón derecho en la unidad organizativa que se va a usar para crear equipos unidos a Azure AD híbrido y, después, seleccione **Delegar control**.

    ![El comando Delegar control](./media/windows-autopilot-hybrid/delegate-control.png)

1. En el asistente **Delegación de control**, haga clic en **Siguiente** > **Agregar** > **Tipos de objeto**.

1. En el cuadro de diálogo **Tipos de objeto**, active la casilla **Equipos** y, después, haga clic en **Aceptar**.

    ![El panel Tipos de objeto](./media/windows-autopilot-hybrid/object-types-computers.png)

1. En el cuadro de diálogo **Seleccionar usuarios, equipos o grupos**, en el cuadro **Escriba los nombres de objeto que desea seleccionar**, escriba el nombre del equipo donde está instalado el conector.

    ![El panel Seleccionar usuarios, equipos o grupos](./media/windows-autopilot-hybrid/enter-object-names.png)

1. Haga clic en **Comprobar nombres** para validar la entrada, haga clic en **Aceptar** y después en **Siguiente**.

1. Haga clic en **Crear una tarea personalizada para delegar** > **Siguiente**.

1. Active la casilla **Solo los siguientes objetos en la carpeta** y, después, active las casillas **Objetos de equipo**, **Crear los objetos seleccionados en esta carpeta** y **Eliminar los objetos seleccionados en esta carpeta**.

    ![El panel Tipo de objeto de Active Directory](./media/windows-autopilot-hybrid/only-following-objects.png)
    
1. Seleccione **Siguiente**.

1. En **Permisos**, active la casilla **Control total**.  
    Esta acción selecciona todas las demás opciones.

    ![El panel Permisos](./media/windows-autopilot-hybrid/full-control.png)

1. Haga clic en **Siguiente** y después en **Finalizar**.

## <a name="install-the-intune-connector"></a>Instalación del conector de Intune

El conector de Intune para Active Directory se debe instalar en un equipo que ejecute Windows Server 2016 o una versión posterior. El equipo también debe tener acceso a Internet y a Active Directory. Para aumentar la escalabilidad y disponibilidad, o para admitir varios dominios de Active Directory, puede instalar varios conectores en el entorno. Se recomienda instalar el conector en un servidor en el que no se ejecute ningún otro conector de Intune.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Dispositivos** > **Windows** > **Inscripción de Windows** > **Conector de Intune para Active Directory** > **Agregar**. 
2. Siga las instrucciones para descargar el conector.
3. Abra el archivo de instalación del conector que ha descargado, *ODJConnectorBootstrapper.exe*, para instalar el conector.
4. Al final del programa de instalación, haga clic en **Configurar**.
5. Haga clic en **Iniciar sesión**.
6. Escriba las credenciales del rol de usuario Administrador global o Administrador de Intune.  
   La cuenta de usuario debe tener una licencia de Intune asignada.
7. Vaya a **Dispositivos** > **Windows** > **Inscripción de Windows** > **Conector de Intune para Active Directory** y confirme que el estado de la conexión es **Activo**.

> [!NOTE]
> Después de iniciar sesión en el conector, es posible que tarde un par de minutos en aparecer en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431). Solo aparece si se puede comunicar correctamente con el servicio Intune.

### <a name="turn-off-ie-enhanced-security-configuration"></a>Desactivación de la configuración de seguridad mejorada de Internet Explorer
De manera predeterminada, Windows Server tiene activada la configuración de seguridad mejorada de Internet Explorer. Si no puede iniciar sesión en el conector de Intune para Active Directory, deshabilite la configuración de seguridad mejorada de Internet Explorer para el administrador. [Desactivación de la configuración de seguridad mejorada de Internet Explorer](https://blogs.technet.microsoft.com/chenley/2011/03/10/how-to-turn-off-internet-explorer-enhanced-security-configuration)

### <a name="configure-web-proxy-settings"></a>Establecer la configuración del proxy web

Si tiene un proxy web en el entorno de red, asegúrese de que el conector de Intune para Active Directory funcione correctamente; para ello, vea [Trabajo con servidores proxy locales existentes](autopilot-hybrid-connector-proxy.md).


## <a name="create-a-device-group"></a>Creación de un grupo de dispositivos
1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Grupos** > **Nuevo grupo**.

1. En el panel **Grupo**, siga estos pasos:

    a. En **Tipo de grupo**, seleccione **Seguridad**.

    b. Escriba un **Nombre de grupo** y una **Descripción del grupo**.

    c. Seleccione un **Tipo de pertenencia**.

1. Si ha seleccionado **Dispositivos dinámicos** para el tipo de pertenencia, seleccione **Miembros del dispositivo dinámico** en el panel **Grupo** y, después, en el cuadro **Regla avanzada**, siga estos pasos:
    - Para crear un grupo que incluya todos los dispositivos Autopilot, escriba `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`.
    - El campo Etiqueta de grupo de Intune se asigna al atributo OrderID en los dispositivos de Azure AD. Si quiere crear un grupo que incluya todos los dispositivos Autopilot con una etiqueta de grupo específica (OrderID), debe escribir: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Para crear un grupo que incluya todos los dispositivos Autopilot con un identificador de pedido de compra específico, escriba `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`.
    
1. Seleccione **Guardar**.

1. Seleccione **Crear**.  

## <a name="register-your-autopilot-devices"></a>Registro de los dispositivos Autopilot

Seleccione una de las formas siguientes de inscribir los dispositivos Autopilot.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registro de dispositivos Autopilot ya inscritos

1. Cree un perfil de implementación de Autopilot con **Convertir todos los dispositivos de destino a Autopilot** establecido en **Sí**. 
2. Asigne el perfil a un grupo que contenga los miembros que quiere registrar de forma automática en Autopilot.

Para más información, vea [Crear un perfil de implementación de Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registro de dispositivos Autopilot no inscritos

Si los dispositivos aún no están inscritos, puede registrarlos manualmente. Para más información, vea [Agregar dispositivos](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registro de dispositivos de un OEM

Si va a comprar nuevos dispositivos, algunos OEM pueden encargarse de registrar los dispositivos. Para más información, vea la [página de Windows Autopilot](https://aka.ms/WindowsAutopilot).

Cuando los dispositivos Autopilot están *registrados*, antes de que se inscriban en Intune, se muestran en tres lugares (con los nombres establecidos en sus números de serie):
- El panel **Dispositivos Autopilot** de Intune en Azure Portal. Seleccione **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos**.
- El panel **Dispositivos de Azure AD** de Intune en Azure Portal. Seleccione **Dispositivos** > **Dispositivos de Azure AD**.
- El panel **Todos los dispositivos de Azure AD** en Azure Active Directory en Azure Portal al seleccionar **Dispositivos** > **Todos los dispositivos**.

Después de *inscribir* los dispositivos Autopilot, se muestran en cuatro lugares:
- El panel **Dispositivos Autopilot** de Intune en Azure Portal. Seleccione **Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos**.
- El panel **Dispositivos de Azure AD** de Intune en Azure Portal. Seleccione **Dispositivos** > **Dispositivos de Azure AD**.
- El panel **Todos los dispositivos de Azure AD** en Azure Active Directory en Azure Portal. Seleccione **Dispositivos** > **Todos los dispositivos**.
- El panel **Todos los dispositivos** de Intune en Azure Portal. Seleccione **Dispositivos** > **Todos los dispositivos**.

Una vez que se hayan inscrito los dispositivos Autopilot, sus nombres se convierten en el nombre de host del dispositivo. De forma predeterminada, el nombre de host comienza con *DESKTOP-* .


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Creación y asignación de un perfil de implementación de Autopilot
Los perfiles de implementación de Autopilot sirven para configurar los dispositivos Autopilot.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Dispositivos** > **Windows** > **Inscripción de Windows** > **Perfiles de implementación** > **Crear perfil**.
2. En la página de los **datos básicos**, escriba un **nombre** y, opcionalmente, una **descripción**.
3. Si quiere que todos los dispositivos en los grupos asignados se conviertan automáticamente en Autopilot, establezca **Convertir todos los dispositivos de destino a Autopilot** en **Sí**. Todos los dispositivos propiedad de la empresa que no sean Autopilot en grupos asignados se registrarán con el servicio de implementación de Autopilot. Los dispositivos de propiedad personal no se convertirán en Autopilot. Permita un plazo de 48 horas para que se procese el registro. Cuando se anule la inscripción del dispositivo y este se restablezca, Autopilot lo inscribirá. Una vez registrado un dispositivo de este modo, si deshabilita esta opción o quitar la asignación de perfil, el dispositivo no se quitará desde el servicio de implementación de Autopilot, sino que deberá [quitar el dispositivo directamente](enrollment-autopilot.md#delete-autopilot-devices).
4. Seleccione **Siguiente**.
5. En la página **Configuración rápida (OOBE)** , para **Modo de implementación**, seleccione **Controlado por el usuario**.
6. En el cuadro **Unirse a Azure AD como**, seleccione **Unidos a Azure AD híbrido**.
7. Configure las opciones restantes en la página **Configuración rápida (OOBE)** , según sea necesario.
8. Seleccione **Siguiente**.
9. En la página **Etiquetas de ámbito**, seleccione las [etiquetas de ámbito](../fundamentals/scope-tags.md) para este perfil.
10. Seleccione **Siguiente**.
11. En la página **Asignaciones**, seleccione **Seleccionar grupos para incluir** > busque y seleccione el grupo de dispositivos > **Seleccionar**.
12. Seleccione **Siguiente** > **Crear**.

El cambio de estado del perfil de dispositivo de *No asignado* a *Asignando* y, por último, a *Asignado*, tarda unos 15 minutos.

## <a name="optional-turn-on-the-enrollment-status-page"></a>(Opcional) Activación de la página de estado de inscripción

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Dispositivos** > **Windows** > **Inscripción de Windows** > **Página de estado de la inscripción**.
1. En el panel **Página de estado de inscripción**, seleccione **Predeterminado** > **Configuración**.
1. En el cuadro **Mostrar el progreso de la instalación de la aplicación y el perfil**, haga clic en **Sí**.
1. Configure las demás opciones según sea necesario.
1. Seleccione **Guardar**.

## <a name="create-and-assign-a-domain-join-profile"></a>Creación y asignación de un perfil Unión a un dominio

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
2. Escriba las propiedades siguientes:
   - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
   - **Descripción**: escriba una descripción para el perfil.
   - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
   - **Tipo de perfil**: seleccione **Unión a un dominio (vista previa)** .
3. Seleccione **Configuración** y, luego, proporcione valores para **Prefijo del nombre de equipo** y **Nombre de dominio**.
4. (Opcional) Proporcione una **unidad organizativa** (OU) en [Formato de DN](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name). Existen varias opciones:
   - Proporcionar una unidad organizativa en la que haya delegado el control en el dispositivo de Windows 2016 que ejecuta el conector de Intune.
   - Proporcionar una unidad organizativa en la que haya delegado el control a los equipos raíz de Active Directory local.
   - Si deja este valor en blanco, el objeto de equipo se creará en el contenedor predeterminado de Active Directory (CN=Computers si nunca [lo ha cambiado](https://support.microsoft.com/en-us/help/324949/redirecting-the-users-and-computers-containers-in-active-directory-dom)).
   
   Estos son algunos ejemplos válidos:
   - OU=Level 1,OU=Level2,DC=contoso,DC=com
   - OU=Mine,DC=contoso,DC=com
   
   Estos son algunos ejemplos que no son válidos:
   - CN=Computers,DC=contoso,DC=com (no puede especificar un contenedor, en su lugar deje el valor en blanco para usar el predeterminado para el dominio)
   - OU=Mine (debe especificar el dominio mediante los atributos DC=)
     
   > [!NOTE]
   > No utilice comillas alrededor del valor de **Unidad organizativa**.
5. Haga clic en **Aceptar** > **Crear**.  
    El perfil se crea y se muestra en la lista.
6. Para asignar el perfil, siga los pasos descritos en [Asignación de un perfil de dispositivo](../configuration/device-profile-assign.md#assign-a-device-profile) y asigne el perfil al mismo grupo que se usa en este paso [Creación de un grupo de dispositivos](windows-autopilot-hybrid.md#create-a-device-group)
   - Implementación de varios perfiles Unión a un dominio
   
     a. Cree un grupo dinámico que incluya todos los dispositivos Autopilot con un perfil de implementación de Autopilot específico, escriba (device.enrollmentProfileName -eq "Nombre de perfil de Autopilot"). 
     
     b. Reemplace "Nombre de perfil de Autopilot" con el nombre para mostrar del perfil que ha creado en [Creación y asignación de un perfil de implementación de Autopilot](windows-autopilot-hybrid.md#create-and-assign-an-autopilot-deployment-profile). 
     
     c. Cree varios perfiles de implementación de Autopilot y asigne ese dispositivo al perfil especificado en este grupo dinámico.

> [!NOTE]
> Las funcionalidades de nomenclatura de Windows Autopilot para la unión a Azure AD híbrido no son compatibles con variables como %SERIAL% y solo admiten prefijos para el nombre del equipo.

## <a name="next-steps"></a>Pasos siguientes

Después de configurar Windows Autopilot, infórmese sobre cómo administrar esos dispositivos. Para más información, vea [¿Qué es la administración de dispositivos de Microsoft Intune?](../remote-actions/device-management.md).
