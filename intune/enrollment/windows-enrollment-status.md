---
title: Configuración de una página de estado de inscripción
titleSuffix: Microsoft Intune
description: Configure una página de saludo para los usuarios que inscriban dispositivos Windows 10.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: ericor
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5e453002493e95bd5147cca115075a17a6e7a298
ms.sourcegitcommit: 556b7ea2049014c9027f0e44affd3f301fab55fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73709323"
---
# <a name="set-up-an-enrollment-status-page"></a>Configuración de una página de estado de inscripción
 
[!INCLUDE [azure_portal](../includes/azure_portal.md)]
 
La página de estado de la inscripción (ESP) muestra información de instalación sobre los dispositivos Windows 10 (versión 1803 y posteriores) durante la inscripción inicial de estos. Por ejemplo:
- cuando se usa [Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/), 
- o cada vez que se inicia un dispositivo administrado por primera vez después de haber aplicado una directiva de página de estado de la inscripción. 

La página de estado de la inscripción ayuda a los usuarios a comprender el estado de su dispositivo durante la instalación. Puede crear varios perfiles de la página de estado de inscripción y aplicarlos a diferentes grupos que contengan usuarios. Los perfiles se pueden establecer en:
- Mostrar progreso de la instalación.
- Bloquear el uso hasta que finalice la instalación.
- Especificar lo que puede hacer un usuario si se produce un error en la configuración del dispositivo.

También puede establecer el orden de prioridad de cada perfil para tener en cuenta las asignaciones de perfiles en conflicto al mismo usuario.

> [!NOTE]
> La página de estado de la inscripción solo se puede destinar a un usuario que pertenezca a un grupo asignado. La directiva se establece en el dispositivo durante la inscripción para todos los usuarios que lo usan.  

## <a name="available-settings"></a>Opciones de configuración disponibles

 Se pueden configurar los siguientes valores para personalizar el comportamiento de la página de estado de la inscripción:

<table>
<th align="left">Setting<th align="left">Sí<th align="left">No
<tr><td>Mostrar el progreso de la instalación de la aplicación y el perfil<td>Se muestra la página de estado de la inscripción.<td>No se muestra la página de estado de la inscripción.
<tr><td>Bloquear el uso del dispositivo hasta que todos los perfiles y aplicaciones estén instalados<td>La configuración de esta tabla está disponible para personalizar el comportamiento de la página de estado de la inscripción, de modo que el usuario pueda resolver posibles problemas de instalación.
<td>La página de estado de la inscripción se muestra sin opciones adicionales para solucionar los errores de instalación.
<tr><td>Permitir a los usuarios restablecer el dispositivo si se produce un error de instalación<td>Si se produce un error de instalación, se muestra un botón <b>Restablecer dispositivo</b>.<td>El botón <b>Restablecer dispositivo</b> no se muestra si se produce un error de instalación.
<tr><td>Permitir a los usuarios utilizar el dispositivo si se produce un error de instalación<td>Si se produce un error de instalación, se muestra un botón <b>Continuar de todos modos</b>.<td>El botón <b>Continuar de todos modos</b> no se muestra si se produce un error de instalación.
<tr><td>Show timeout error when installation takes longer than specified number of minutes (Mostrar error de tiempo de expiración cuando la instalación tarda más de un número especificado de minutos)<td colspan="2">Especifique el número de minutos de espera para finalizar la instalación. Se especifica un valor predeterminado de 60 minutos.
<tr><td>Mostrar un mensaje personalizado cuando se produce un error<td>Se proporciona un cuadro de texto en el que puede especificar un mensaje personalizado que se mostrará si se produce un error de instalación.<td>Se muestra el mensaje predeterminado: <br><b>La instalación superó el límite de tiempo establecido por su organización. Vuelva a intentarlo o póngase en contacto con la persona de soporte de TI para obtener ayuda.<b>
.<tr><td>Permitir a los usuarios recopilar los registros acerca de los errores de instalación<td>Si se produce un error de instalación, se muestra el botón registros <b>Recopilar registros</b>. <br>Si el usuario hace clic en este botón, se le pedirá que elija una ubicación para guardar el archivo de registro <b>MDMDiagReport.cab</b>.<td>El botón <b>Recopilar registros</b> no se muestra si hay un error de instalación.
<tr><td>Block device use until these required apps are installed if they are assigned to the user/device (Bloquear dispositivo hasta que las aplicaciones necesarias estén instaladas si están asignadas al usuario o dispositivo).<td colspan="2">Elija <b>Todo</b> o <b>Seleccionado</b>. <br><br>Si se elige <b>Seleccionado</b>, aparece un botón <b>Seleccionar aplicaciones</b> que permite elegir qué aplicaciones deben instalarse antes de habilitar el dispositivo.
</table>

## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Turn on default Enrollment Status Page for all users (Activar la página de estado de la inscripción predeterminada para todos los usuarios)

Para activar la página de estado de la inscripción, siga estos pasos.
 
1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Página de estado de la inscripción**.
2. En la hoja **Página de estado de inscripción**, elija **Predeterminado** > **Configuración**.
3. Para **Show app and profile installation progress** (Mostrar progreso de instalación de la aplicación y el perfil), elija **Sí**.
4. Elija las demás opciones de configuración que desee activar y seleccione **Guardar**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Creación de un perfil de la página de estado de la inscripción y asignación a un grupo

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Página de estado de la inscripción** > **Crear perfil**.
2. Proporcione un **Nombre** y una **Descripción**.
3. Elija **Crear**.
4. Elija el nuevo perfil en la lista **Página de estado de inscripción**.
5. Elija **Asignaciones** > **Seleccionar grupos** > elija los grupos que quiera que adopten este perfil > **Seleccionar** > **Guardar**.
6. Elija **Configuración** > elija la configuración que quiera aplicar a este perfil > **Guardar**.

## <a name="set-the-enrollment-status-page-priority"></a>Establecimiento de la prioridad de la página de estado de inscripción

Un usuario puede estar en muchos grupos y tener muchos perfiles de página de estado de la inscripción. Para resolver estos conflictos, puede establecer las prioridades de cada perfil. Durante la inscripción, si alguien tiene más de un perfil de página de estado de la inscripción, solo se aplica el perfil de prioridad más alta al dispositivo de inscripción.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Página de estado de la inscripción**.
2. Mantenga el mouse sobre el perfil en la lista.
3. Use los tres puntos verticales para arrastrar el perfil a la posición que quiera en la lista.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Bloqueo del acceso a un dispositivo a menos que haya instalada una aplicación específica

Puede especificar qué aplicaciones deben estar instaladas antes de que el usuario pueda acceder al escritorio.

1. En el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Inscripción de dispositivos** > **Inscripción de Windows** > **Página de estado de la inscripción**.
2. Elija un perfil > **Configuración**.
3. Elija **Sí** en **Show app and profile installation progress** (Mostrar progreso de instalación de la aplicación y el perfil).
4. Elija **Sí** en **Block device use until all apps and profiles are installed** (Bloquear dispositivo hasta que todas estas aplicaciones y perfiles estén instalados).
5. Elija **Seleccionado** en **Block device use until these required apps are installed if they are assigned to the user/device** (Bloquear dispositivo hasta que las aplicaciones necesarias estén instaladas si están asignadas al usuario o dispositivo).
6. Elija **Seleccionar aplicaciones** > elija las aplicaciones > **Seleccionar** > **Guardar**.

## <a name="enrollment-status-page-tracking-information"></a>Información de seguimiento de la página de estado de la inscripción

Hay tres fases en las que la página de estado de la inscripción realiza un seguimiento de la información: durante la preparación del dispositivo, la instalación del dispositivo y la configuración de la cuenta.

### <a name="device-preparation"></a>Preparación del dispositivo

Durante la preparación del dispositivo, la página de estado de la inscripción realiza un seguimiento de lo siguiente:
- Atestaciones de clave del Módulo de plataforma segura (TPM) (cuando proceda)
- Progreso de la unión a Azure Active Directory
- Inscripción en Intune
- Instalación de las extensiones de administración de Intune

### <a name="device-setup"></a>Configuración del dispositivo

La página de estado de la inscripción realiza un seguimiento de los siguientes elementos de configuración de los dispositivos (si están asignados a todos los dispositivos o a un grupo de dispositivos del que es miembro el dispositivo de inscripción):
- Directivas de seguridad
  - Un proveedor de servicios de configuración (CSP) para todas las inscripciones.
  - El seguimiento de los CSP reales configurados por Intune no se realiza aquí.
- Aplicaciones
  - Aplicaciones MSI de línea de negocio (LoB) por equipo.
  - Aplicaciones de almacén de LoB con contexto de instalación = Dispositivo.
  - Aplicaciones de almacén de LoB y almacén sin conexión con contexto de instalación = Dispositivo.
  - Aplicaciones Win32 (solo Windows 10 versión 1903 y versiones más recientes) 
- Perfiles de conectividad
  - Perfiles de Wi-Fi o VPN que están asignados a **Todos los dispositivos** o a un grupo de dispositivos en el que el dispositivo de inscripción es un miembro, pero solo para dispositivos Autopilot
- Perfiles de certificado que están asignados a **Todos los dispositivos** o a un grupo de dispositivos en el que el dispositivo de inscripción es un miembro, pero solo para dispositivos Autopilot

### <a name="account-setup"></a>Configuración de la cuenta
Para la configuración de la cuenta, la página de estado de la inscripción realiza un seguimiento de estos elementos si están asignados al usuario con sesión iniciada en ese momento:
- Directivas de seguridad
  - Un CSP para todas las inscripciones.
  - El seguimiento de los CSP reales configurados por Intune no se realiza aquí.
- Aplicaciones
  - Aplicaciones de MSI de LoB por usuario que están asignadas a todos los dispositivos, a todos los usuarios a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.
  - Aplicaciones de MSI de LoB por equipo que están asignadas a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.
  - Aplicaciones LoB de la tienda, aplicaciones de la tienda en línea y aplicaciones de la tienda sin conexión que se asignan a cualquiera de los siguientes objetos:
    - Todos los dispositivos
    - Todos los usuarios
    - Un grupo de usuarios del que es miembro el usuario que inscribe el dispositivo con el contexto de instalación establecido en Usuario.
  - Aplicaciones Win32 (solo Windows 10 versión 1903 y versiones más recientes) 
- Perfiles de conectividad
  - Perfiles de VPN o Wi-Fi que están asignados a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.
- Certificados
  - Perfiles de certificado que están asignados a todos los usuarios o a un grupo de usuarios del que es miembro el usuario que está inscribiendo el dispositivo.

### <a name="troubleshooting"></a>Solucionar problemas
Principales preguntas de solución de problemas.

- ¿Por qué mis aplicaciones no se instalaron durante la fase de instalación del dispositivo en el transcurso de la implementación de Autopilot mediante la página de estado de la inscripción?
  - Para garantizar que las aplicaciones se instalen durante la fase de instalación de un dispositivo Autopilot, compruebe lo siguiente: 
        1. La aplicación está seleccionada para bloquear el acceso en la lista de aplicaciones seleccionadas.
        2. El destino de las aplicaciones es el mismo grupo de dispositivos de Azure AD al que está asignado el perfil de Autopilot. 

- ¿Por qué se muestra la página de estado de la inscripción en las implementaciones que no son de Autopilot, por ejemplo, cuando un usuario inicia sesión por primera vez en un dispositivo inscrito en la administración conjunta de Configuration Manager?  
  - En la página de estado de la inscripción se muestra el estado de instalación de todos los métodos de inscripción. Por ejemplo:
      - Autopilot
      - Configuration Manager y administración conjunta
      - Cuando un usuario nuevo inicia sesión por primera vez en el dispositivo que tiene aplicada la directiva de página de estado de la inscripción

- ¿Cómo se puede deshabilitar la página de estado de la inscripción si se ha configurado en el dispositivo?
  - La directiva de página de estado de la inscripción se establece en un dispositivo en el momento de la inscripción. Para deshabilitar esta página, debe deshabilitar las secciones de la página de estado de la inscripción de dispositivos y usuarios. Para ello, cree valores personalizados de OMA-URI con las siguientes configuraciones.

      Deshabilitar la página de estado de la inscripción de usuario:

      ```
      Name:  Disable User ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipUserStatusPage
      Data type:  Boolean
      Value:  True 
      ```
      Deshabilitar la página de estado de la inscripción de dispositivo:

      ```
      Name:  Disable Device ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipDeviceStatusPage
      Data type:  Boolean
      Value:  True 
      ```
- ¿Cómo puedo recopilar los archivos de registro?
  - Hay dos maneras de recopilar los archivos de registro de la página de estado de la inscripción:
      - Permitir la posibilidad de que los usuarios recopilen registros en la directiva ESP. Cuando se agota el tiempo de expiración en la página de estado de la inscripción, el usuario final puede elegir la opción **Recopilar registros**. Al insertar una unidad USB, los archivos de registro se pueden copiar en ella.
      - Abra un símbolo del sistema con la secuencia de teclas Mayús + F10 y, luego, escriba la siguiente línea de comandos para generar los archivos de registro: 

      ```
      mdmdiagnosticstool.exe -area Autopilot -cab <pathToOutputCabFile>.cab 
      ```

### <a name="known-issues"></a>Problemas conocidos
A continuación se muestran los problemas conocidos. 
- Al deshabilitar el perfil de ESP no se quita la directiva de ESP de los dispositivos, y los usuarios siguen viendo la ESP cuando inician sesión en el dispositivo por primera vez. La directiva no se quita cuando se deshabilita el perfil de ESP. Debe implementar OMA-URI para deshabilitar la ESP. Consulte anteriormente las instrucciones para deshabilitar ESP mediante OMA-URI. 
- Un reinicio pendiente siempre producirá un tiempo de expiración. El tiempo de expiración se agota porque el dispositivo debe reiniciarse. El reinicio es necesario para dar tiempo a que finalice el elemento cuyo seguimiento se realiza en la página de estado de la inscripción. Un reinicio provocará que se cierre la página de estado de la inscripción y, tras el reinicio, el dispositivo no accederá a ella mientras se configura la cuenta.  Considere la posibilidad de no exigir un reinicio durante la instalación de la aplicación, 
- ya que obligará al usuario a escribir sus credenciales antes de pasar a la fase de configuración de la cuenta. Las credenciales de usuario no se conservan durante el reinicio. Haga que el usuario escriba sus credenciales; de este modo, la página de estado de la inscripción puede continuar. 
- La página de estado de la inscripción siempre agotará el tiempo de expiración durante una inscripción mediante la opción para agregar una cuenta profesional o educativa en versiones de Windows 10 inferiores a la 1903. La página de estado de la inscripción espera a que finalice el registro de Azure AD. El problema se corrigió en Windows 10 versión 1903 y posteriores.  
- La implementación de Autopilot de Azure AD híbrido con ESP tarda más tiempo que la duración del tiempo de expiración definida en el perfil de ESP. En implementaciones de Autopilot de Azure AD híbrido, ESP tardará 40 minutos más que el valor establecido en el perfil de ESP. Este retraso proporciona tiempo para que el conector de AD local cree el registro del dispositivo en Azure AD. 
- La página de inicio de sesión de Windows no se rellena previamente con el nombre de usuario en el modo controlado por el usuario de Autopilot. Si se ha producido un reinicio durante la fase de instalación del dispositivo de ESP:
    - No se conservan las credenciales de usuario.
    - El usuario debe volver a escribir las credenciales antes de pasar de la fase de instalación del dispositivo a la fase de configuración de la cuenta.
- ESP se queda bloqueado durante mucho tiempo o nunca completa la fase de identificación. Intune calcula las directivas de ESP durante la fase de identificación. Puede que un dispositivo no complete nunca las directivas de ESP si el usuario actual no tiene asignada una licencia de Intune.  
- La configuración de Windows Defender Application Control provoca que se reinicie el sistema durante la fase de Autopilot. La configuración de Windows Defender Application Control (CSP de AppLocker) requiere un reinicio. Cuando se configura esta directiva, es posible que el dispositivo se reinicie durante la fase de Autopilot. Actualmente, no hay ninguna manera de suprimir o posponer el reinicio.
- Cuando la directiva DeviceLock (https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) ) está habilitada como parte de un perfil de ESP, la configuración rápida del sistema (OOBE) o el inicio de sesión automático en el escritorio del usuario podrían producir un error inesperado por dos motivos.
  - Si el dispositivo no se reinició antes de salir de la fase de instalación del dispositivo de ESP, es posible que se le pida al usuario que escriba sus credenciales de Azure AD. Este mensaje se muestra en lugar de un inicio de sesión automático correcto en el que el usuario ve la animación del primer inicio de sesión de Windows.
  - El inicio de sesión automático no se realizará correctamente si el dispositivo se reinicia después de que el usuario haya escrito sus credenciales de Azure AD, pero antes de salir de la fase de instalación del dispositivo de ESP. Este error se produce porque la fase de instalación del dispositivo de ESP nunca se ha completado. La solución alternativa es restablecer el dispositivo.

## <a name="next-steps"></a>Pasos siguientes
Tras configurar las páginas de inscripción de Windows, descubra cómo administrar dispositivos Windows. Para obtener más información, consulte [¿Qué es la administración de dispositivos de Microsoft Intune?](../remote-actions/device-management.md)
