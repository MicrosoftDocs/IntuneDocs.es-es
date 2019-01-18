---
title: 'Inscripción para dispositivos unidos a Active Directory híbrido: Windows Autopilot'
titleSuffix: ''
description: Use Windows Autopilot para inscribir dispositivos unidos a Active Directory híbrido en Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: f6a78c6612f98903fcbaa9d33b8037c5ea4a3960
ms.sourcegitcommit: 2ff19c09a43c63556d082966727674120b516d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149668"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-using-intune-and-windows-autopilot-preview"></a>Implementación de dispositivos unidos a Azure AD híbrido mediante Intune y Windows Autopilot (versión preliminar)
Puede usar Intune y Windows Autopilot para configurar dispositivos unidos a Azure Active Directory híbrido. Para ello, siga estos pasos.

## <a name="prerequisites"></a>Requisitos previos

- Los [dispositivos unidos a Azure Active Directory híbrido](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan) deben estar configurados correctamente.
    - No olvide [comprobar el registro mediante el cmdlet Get-MsolDevice]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration).

Los dispositivos que se inscriban también deben:
- Ejecutar Windows 10 con la [actualización de octubre de 2018](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/).
- Tener acceso a Internet.
- Tener acceso a Active Directory (no se admite la conexión VPN).
- Realizar la configuración rápida (OOBE).

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurar la inscripción automática de Windows 10

1. Inicie sesión en [Azure Portal](https://portal.azure.com) y seleccione **Azure Active Directory**.

   ![Captura de pantalla de Azure Portal](./media/auto-enroll-azure-main.png)

2. Seleccione **Movilidad (MDM y MAM)**.

   ![Captura de pantalla de Azure Portal](./media/auto-enroll-mdm.png)

3. Seleccione **Microsoft Intune**.

   ![Captura de pantalla de Azure Portal](./media/auto-enroll-intune.png)

4. Asegúrese de que los usuarios que implementan dispositivos unidos a Azure Active Directory mediante Intune y Windows son miembros de un grupo incluido en el **ámbito de usuario de MDM**.

   ![Captura de pantalla de Azure Portal](./media/auto-enroll-scope.png)

5. Use los valores predeterminados para las siguientes direcciones URL:
    - **URL de los términos de uso de MDM**
    - **URL de detección de MDM**
    - **URL de cumplimiento de MDM**
6. Elija **Guardar**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Aumento del límite de la cuenta de equipo en la unidad organizativa

El conector de Intune para Active Directory crea equipos inscritos con Autopilot en el dominio local de Active Directory. El equipo que hospeda el conector de Intune debe tener los derechos para crear objetos de equipo dentro del dominio. 

En algunos dominios, los equipos no tienen derechos para crear equipos. Además, los dominios tienen un límite integrado (valor predeterminado de 10) que se aplica a todos los usuarios y equipos que no son derechos delegados para crear Objetos de equipo. Por tanto, los derechos deben delegarse en equipos que hospedan el conector de Intune en la unidad organizativa donde se crean los dispositivos unidos a Hybrid Azure AD.

La unidad organizativa que concedió el derecho a crear equipos debe coincidir con:
- la unidad organizativa especificada en el perfil Unión a dominio
- o bien, si no se ha seleccionado ningún perfil, el nombre del dominio del equipo para el dominio.

1. Abra **Usuarios y equipos de Active Directory** (DSA.msc).

2. Haga clic con el botón derecho en la unidad organizativa que se usará para crear equipos unidos a Azure AD híbrido > **Delegar control**.

    ![Captura de pantalla de Delegar control](media/windows-autopilot-hybrid/delegate-control.png)

3. En el asistente **Delegación de control**, elija **Siguiente** > **Agregar...** > **Tipos de objeto**.

4. En el cuadro de diálogo **Tipos de objeto**, seleccione **Equipos** y, después, haga clic en **Aceptar**.

    ![Captura de pantalla de Delegar control](media/windows-autopilot-hybrid/object-types-computers.png)

5. En el cuadro de diálogo **Select Users, Computers, or Groups** (Seleccionar usuarios, equipos o grupos), en el cuadro **Enter the object names to select** (Escriba los nombres de objeto que se van a seleccionar), escriba el nombre del equipo donde está instalado el conector.

    ![Captura de pantalla de Delegar control](media/windows-autopilot-hybrid/enter-object-names.png)

6. Elija **Comprobar nombres** para validar la entrada y seleccione **Aceptar** > **Siguiente**.

7. Elija **Crear una tarea personalizada para delegar** > **Siguiente**.

8. Elija **Solo los siguientes objetos en la carpeta** y, luego, compruebe las siguientes opciones:
    - **Objetos de equipo**
    - **Crear los objetos seleccionados en esta carpeta**
    - **Eliminar los objetos seleccionados en esta carpeta**

    ![Captura de pantalla de Delegar control](media/windows-autopilot-hybrid/only-following-objects.png)
    
9. Seleccione **Siguiente**.

10. En **Permisos**, active **Control total** (se activarán también las demás opciones) > **Siguiente** > **Finalizar**.

    ![Captura de pantalla de Delegar control](media/windows-autopilot-hybrid/full-control.png)

## <a name="install-the-intune-connector"></a>Instalación del conector de Intune

Es necesario instalar el conector de Intune para Active Directory en un equipo en el que se ejecute Windows Server 2016 y que tenga acceso a Internet y a Active Directory. Para aumentar la escalabilidad y disponibilidad, o para admitir varios dominios de Active Directory, puede instalar varios conectores en el entorno. Se recomienda instalar el conector en un servidor en el que no se esté ejecutando ningún otro conector de Intune.

1. Asegúrese de que tiene un paquete de idioma instalado y configurado tal y como se describe en [Requisitos de idioma del conector de Intune (versión preliminar)](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector).
2. En [Intune](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos** > **Inscripción de Windows** > **Conector de Intune para Active Directory (versión preliminar)** > **Agregar conector**. 
3. Siga las instrucciones para descargar el conector.
4. Abra el archivo de instalación del conector que ha descargado para instalar el conector (ODJConnectorBootstrapper.exe).
5. Al final del proceso de instalación, elija **Configurar**.
6. Seleccione **Iniciar sesión**.
7. Escriba las credenciales del rol de usuario Administrador global o Administrador de Intune.
8. Vaya a **Inscripción de dispositivos** > **Inscripción de Windows** > **Intune Connector para Active Directory (versión preliminar)** y confirme que el estado de conexión es **Activo**.

### <a name="configure-web-proxy-settings"></a>Establecer la configuración del proxy web

Si tiene un proxy web en el entorno de red, siga estas instrucciones para que el conector de Intune para Active Directory funcione correctamente: [Trabaje con servidores proxy locales existentes](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers).


## <a name="create-a-device-group"></a>Creación de un grupo de dispositivos
1. En [Intune](https://aka.ms/intuneportal), elija **Grupos** > **Nuevo grupo**.
2. En la hoja **Grupo**:
    1. En **Tipo de grupo**, elija **Seguridad**.
    2. Escriba un **Nombre de grupo** y una **Descripción del grupo**.
    3. Elija **Tipo de pertenencia**.
3. Si ha elegido **Dispositivos dinámicos** en **Tipo de pertenencia** anteriormente, elija **Miembros del dispositivo dinámico** en la hoja **Grupo** y escriba cualquiera de los siguientes códigos en el cuadro **Regla avanzada**.
    - Si quiere crear un grupo que incluya todos los dispositivos Autopilot, escriba `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Si quiere crear un grupo que incluya todos los dispositivos Autopilot con un identificador de pedido específico, escriba `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Si quiere crear un grupo que incluya todos los dispositivos Autopilot con un identificador de pedido de compra específico, escriba `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Después de agregar el código de **Regla avanzada**, elija **Guardar**.
5. Elija **Crear**.  

## <a name="register-your-autopilot-devices"></a>Registro de los dispositivos Autopilot

Elija uno de los siguientes métodos para inscribir los dispositivos Autopilot:

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registro de dispositivos Autopilot ya inscritos

1. Cree un perfil de implementación de Autopilot con **Convertir todos los dispositivos de destino a Autopilot** establecido en **Sí**. 
2. Asigne el perfil a un grupo que contenga los miembros que quiere registrar automáticamente en Autopilot.

Para más información, vea [Crear un perfil de implementación de Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registro de dispositivos Autopilot no inscritos

Si los dispositivos aún no están inscritos, puede registrarlos manualmente. Para más información, vea [Agregar dispositivos](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registro de dispositivos de un OEM

Si va a comprar nuevos dispositivos, algunos OEM pueden encargarse de registrar los dispositivos. Para más información, vea la [página de Windows Autopilot](http://aka.ms/WindowsAutopilot).

Cuando los dispositivos Autopilot están registrados (y previamente están inscritos en Intune), podrá verlos en tres lugares (con nombres establecidos en sus números de serie):
- Hoja Dispositivos Autopilot en Intune en Azure Portal (**Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos**).
- Hoja Dispositivos de Azure AD en Intune en Azure Portal (**Dispositivos** > **Dispositivos de Azure AD**).
- Hoja Todos los dispositivos en Azure Active Directory en Azure Portal (**Dispositivos** > **Todos los dispositivos**).

Una vez que se hayan inscrito los dispositivos Autopilot, los verá en cuatro lugares:
- Hoja Dispositivos Autopilot en Intune en Azure Portal (**Inscripción de dispositivos** > **Inscripción de Windows** > **Dispositivos**).
- Hoja Dispositivos de Azure AD en Intune en Azure Portal (**Dispositivos** > **Dispositivos de Azure AD**).
- Hoja Todos los dispositivos en Azure Active Directory en Azure Portal (**Dispositivos** > **Todos los dispositivos**).
- Hoja Todos los dispositivos en Intune en Azure Portal (**Dispositivos** > **Todos los dispositivos**).

Una vez que se hayan inscrito los dispositivos Autopilot, sus nombres de dispositivo cambiarán al nombre de host del dispositivo. De forma predeterminada, empieza por "DESKTOP-".




## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Creación y asignación de un perfil de implementación de Autopilot
Los perfiles de implementación de Autopilot sirven para configurar los dispositivos Autopilot.

1. En [Intune](https://aka.ms/intuneportal), seleccione **Inscripción de dispositivos** > **Inscripción de Windows** > **Perfiles de implementación** > **Crear perfil**.
2. Escriba un **Nombre** y una **Descripción** opcional.
3. En **Modo de implementación**, elija **Controlado por el usuario**.
4. En el cuadro **Unirse a Azure AD como**, elija **Unidos a Azure AD híbrido (versión preliminar)**.
5. Elija **Configuración rápida (OOBE)**, configure las opciones necesarias y elija **Guardar**.
6. Elija **Crear** para crear el perfil. 
7. En la hoja del perfil, elija **Asignaciones**.
8. Elija **Seleccionar grupos** > en la hoja **Seleccionar grupos**, elija el grupo de dispositivos > **Seleccionar**.

El proceso para cambiar el estado del perfil de dispositivo de **No asignado** a **Asignando** y, por último, **Asignado**, tardará unos 15 minutos.

## <a name="turn-on-the-enrollment-status-page-optional"></a>Activación de la página de estado de inscripción (opcional)

1. En [Intune](https://aka.ms/intuneportal), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Página de estado de inscripción (vista previa)**.
2. En la hoja **Página de estado de inscripción**, elija **Predeterminado** > **Configuración**.
3. Para **Show app and profile installation progress** (Mostrar progreso de instalación de la aplicación y el perfil), elija **Sí**.
4. Configure las demás opciones según sea necesario.
5. Elija **Guardar**.

## <a name="create-and-assign-a-domain-join-profile"></a>Creación y asignación de un perfil Unión a un dominio

1. En [Intune](https://aka.ms/intuneportal), seleccione **Configuración del dispositivo** > **Perfiles** > **Crear perfil**.
2. Complete las siguientes propiedades:
   - **Nombre**: escriba un nombre descriptivo para el nuevo perfil.
   - **Descripción**: escriba una descripción para el perfil.
   - **Plataforma**: seleccione **Windows 10 y versiones posteriores**.
   - **Tipo de perfil**: elija **Unión a un dominio (vista previa)**.
3. Elija **Configuración** y proporcione un **Prefijo de nombre de equipo**, un **Nombre de dominio** y, opcionalmente, una **Unidad organizativa** en [formato DN](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name). 
4. Elija **Aceptar** > **Crear**. Se creará el perfil y aparecerá en la lista.
5. Para asignar el perfil, siga los pasos descritos en [Asignar un perfil de dispositivo](device-profile-assign.md#assign-a-device-profile). 

## <a name="next-steps"></a>Pasos siguientes

Después de configurar Windows Autopilot, infórmese sobre cómo administrar esos dispositivos. Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](device-management.md)
