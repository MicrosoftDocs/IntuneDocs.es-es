---
title: 'Adición de scripts de PowerShell en Microsoft Intune para dispositivos con Windows 10: Azure | Microsoft Docs'
description: Agregue scripts de PowerShell, asigne la directiva de script a grupos de Active Directory de Azure, use informes para supervisar los scripts y vea los pasos para eliminar scripts que se agregan en dispositivos con Windows 10 en Microsoft Intune. Vea también algunos problemas comunes y sus soluciones.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 573ca3aa10094e61165d297730d556e2ef559767
ms.sourcegitcommit: 8e503c1b350f7b29a045b7daf3eece64be4ca3c4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56302190"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Administrar scripts de PowerShell en Intune para dispositivos Windows 10

Use la extensión de administración de Intune para cargar los scripts de PowerShell en Intune y ejecutarlos en dispositivos Windows 10. La extensión de administración mejora la administración de dispositivos móviles (MDM) de Windows 10 y facilita el paso a una administración moderna.

## <a name="moving-to-modern-management"></a>Transición hacia una administración moderna

La informática de usuario final está experimentando una transformación digital. La TI clásica y tradicional se centra en una plataforma de dispositivo único, en dispositivos propiedad de la empresa, en usuarios que trabajan desde la oficina y en diversos procesos de TI manuales y reactivos. En el área de trabajo moderno se usan muchas plataformas que son propiedad del usuario o la empresa, permite a los usuarios trabajar desde cualquier lugar y proporciona procesos de TI automatizados y proactivos.

Los servicios MDM, como Microsoft Intune, pueden administrar dispositivos móviles y de escritorio que ejecutan Windows 10. El cliente de administración integrado de Windows 10 se comunica con Intune para realizar tareas de administración empresariales. Hay algunas tareas que puede necesitar, como configuración avanzada de dispositivos y solución de problemas. Para la administración de aplicaciones Win32, puede usar la característica de [administración de aplicaciones Win32](apps-win32-app-management.md) en sus dispositivos Windows 10.

La extensión de administración de Intune complementa las características de administración de dispositivos móviles (MDM) que Windows 10 incluye de fábrica. Puede crear scripts de PowerShell para ejecutar en los dispositivos Windows 10. Por ejemplo, puede crear un script de PowerShell que realice configuraciones avanzadas de dispositivos, cargue el script en Intune, asigne el script a un grupo de Azure Active Directory (AD) y ejecute el script. Luego, puede supervisar de principio a fin el estado de ejecución del script.

## <a name="prerequisites"></a>Requisitos previos

La extensión de administración de Intune tiene los siguientes requisitos previos:

- Los dispositivos deben estar unidos o registrados en Azure AD y Azure AD debe estar configurado para la [inscripción automática en Intune](windows-enroll.md#enable-windows-10-automatic-enrollment). La extensión de administración de Intune admite dispositivos Windows inscritos unidos a Azure AD, unidos a dominios híbridos y administrados conjuntamente.
- Los dispositivos deben ejecutar Windows 10, versión 1607 o posterior.
- El agente de la extensión de administración de Intune se instala cuando se implementa un script de PowerShell o una aplicación Win32 en un grupo de seguridad de dispositivos o usuarios.

## <a name="create-a-powershell-script-policy"></a>Crear una directiva de un script de PowerShell 

1. En [Azure Portal](https://portal.azure.com), seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
2. Seleccione **Configuración del dispositivo** > **Scripts de PowerShell** > **Agregar**.
3. Escriba un valor para **Nombre** y **Descripción** para el script de PowerShell. Para **Ubicación del script**, busque el script de PowerShell. El script no debe superar los 200 KB de tamaño.
4. Elija **Configurar**. Después, decida si quiere ejecutar el script con las credenciales del usuario en el dispositivo (**Sí**) o en el contexto del sistema (**No**). De forma predeterminada, el script se ejecuta en el contexto del sistema. Seleccione **Sí** a menos que el script se deba ejecutar en el contexto del sistema. 
  ![Panel Agregar script de PowerShell](./media/mgmt-extension-add-script.png)
5. Elija si el script debe estar firmado por un editor de confianza (**Sí**). De forma predeterminada, no se exige que el script esté firmado. 
6. Seleccione **Aceptar** y, luego, **Crear** para guardar el script.

## <a name="assign-a-powershell-script-policy"></a>Asignar una directiva de script de PowerShell

1. En **Scripts de PowerShell**, seleccione el script que se va a asignar y luego elija **Administrar** > **Asignaciones**.

    ![Panel Agregar script de PowerShell](./media/mgmt-extension-assignments.png)

2. Elija **Seleccionar grupos** para obtener una lista de los grupos de Azure AD disponibles. 
3. Seleccione uno o varios grupos que incluyan los usuarios cuyos dispositivos reciben el script. Haga clic en **Seleccionar** para asignar la directiva a los grupos seleccionados.

> [!NOTE]
> - No es necesario que los usuarios finales inicien sesión en el dispositivo para ejecutar scripts de PowerShell.
> - Los scripts de PowerShell en Intune pueden estar dirigidos a grupos de seguridad de dispositivos de Azure AD.
> - Los scripts de PowerShell en Intune pueden estar dirigidos a grupos de seguridad de usuarios de Azure AD.

El cliente de la extensión de administración de Intune consulta con Intune una vez cada hora. Después de asignar la directiva a los grupos de Azure AD, se ejecuta el script de PowerShell y se notifican los resultados de la ejecución.

## <a name="monitor-run-status-for-powershell-scripts"></a>Supervisar el estado de ejecución de scripts de PowerShell

Puede supervisar el estado de ejecución de scripts de PowerShell para usuarios y dispositivos en Azure Portal.

En **Scripts de PowerShell**, seleccione el script que quiere supervisar y, después, elija **Supervisar** y uno de estos informes:

- **Estado del dispositivo**
- **Estado del usuario**

## <a name="troubleshoot-powershell-scripts"></a>Solución de problemas de scripts de PowerShell

Habitualmente, los registros de agente en la máquina cliente se encuentran en `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Puede usar [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) para ver estos archivos de registro. 

![Captura de pantalla de los registros de agente](./media/apps-win32-app-10.png)  

## <a name="delete-a-powershell-script"></a>Eliminar un script de PowerShell

En **Scripts de PowerShell**, haga clic con el botón derecho en el script y seleccione **Eliminar**.

## <a name="common-issues-and-resolutions"></a>Problemas comunes y sus soluciones

Los scripts de PowerShell no se ejecutan en cada inicio de sesión. Solo lo hacen después de reiniciar el dispositivo, o si el servicio de **extensión de administración de Microsoft Intune**. El cliente de la extensión de administración de Intune comprueba con Intune cada hora si se han producido cambios en el script o la directiva.

#### <a name="issue-intune-management-extension-doesnt-download"></a>Problema: La extensión de administración de Intune no se descarga

**Soluciones posibles**:

- Asegúrese de que los dispositivos estén inscritos automáticamente en Azure AD. Para confirmarlo, en el dispositivo: 

  1. Vaya a **Configuración** > **Cuentas** > **Obtener acceso a trabajo o escuela**.
  2. Seleccione la cuenta combinada > **Información**.
  3. En **Advanced Diagnostic Report** (Informe de diagnóstico avanzado), seleccione **Crear informe**.
  4. Abra el archivo `MDMDiagReport` en un explorador web y vaya a la sección **Enrolled configuration sources** (Orígenes de configuración inscritos).
  5. Busque la propiedad **MDMDeviceWithAAD**. Si esta propiedad no existe, el dispositivo no está inscrito automáticamente.

    En [Habilitar la inscripción automática de Windows 10](windows-enroll.md#enable-windows-10-automatic-enrollment) se incluyen los pasos.

#### <a name="issue-the-powershell-scripts-do-not-run"></a>Problema: Los scripts de PowerShell no se ejecutan

**Soluciones posibles**:

- Confirme que la extensión de administración de Intune se ha descargado en `%ProgramFiles(x86)%\Microsoft Intune Management Extension`.
- Los scripts no se ejecutan en instancias de Surface Hub.
- Compruebe los registros de `\ProgramData\Microsoft\IntuneManagementExtension\Logs` en busca de errores.
- Para comprobar si existen problemas de permisos, asegúrese de que las propiedades del script de PowerShell estén establecidas en `Run this script using the logged on credentials`. Compruebe también que el usuario que ha iniciado sesión tenga los permisos adecuados para ejecutar el script.
- Para aislar los problemas de script, ejecute un script de ejemplo. Por ejemplo, cree el directorio `C:\Scripts` y proporcione a todos control total. Ejecute el siguiente script:

  ```powershell
  write-output "Script worked" | out-file c:\Scripts\output.txt
  ```

  Si se ejecuta correctamente, se creará un archivo output.txt e incluirá el texto "Script Worked" (El script funcionó).

- Para probar la ejecución del script sin Intune, ejecute los scripts que aparecen en el contexto del sistema mediante el uso local de la [herramienta psexec](https://docs.microsoft.com/sysinternals/downloads/psexec):

  `psexec -i -s`

## <a name="next-steps"></a>Pasos siguientes

[Supervise](device-profile-monitor.md) y [solucione los problemas](device-profile-troubleshoot.md) de sus perfiles.
