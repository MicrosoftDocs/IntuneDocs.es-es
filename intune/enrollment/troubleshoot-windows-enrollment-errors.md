---
title: Solución de problemas con la inscripción de dispositivos Windows en Microsoft Intune
titleSuffix: Microsoft Intune
description: Sugerencias para solucionar algunos de los problemas más comunes al inscribir dispositivos Windows en Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dae8e92209a8640ab3254e073d3043d390c3791b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514258"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Solución de problemas con la inscripción de dispositivos Windows en Microsoft Intune

Este artículo ayuda a los administradores de Intune a comprender y solucionar problemas relacionados con la inscripción de dispositivos Windows en Intune.

## <a name="prerequisites"></a>Requisitos previos
Antes de empezar a solucionar problemas, es importante recopilar alguna información básica. Esta información puede ayudarle a entender mejor el problema y reducir el tiempo para encontrar una solución.

Recopile la siguiente información sobre el problema:
- ¿Se ha asignado al usuario una licencia de Intune válida? Antes de que los usuarios puedan inscribir los dispositivos, deben tener la licencia necesaria asignada.
- ¿Está instalada la actualización más reciente en el dispositivo Windows? Algunas características de Intune solo funcionan con la última versión de Windows. Hay muchas correcciones disponibles en Windows Update para los problemas conocidos. Al aplicar todas las actualizaciones más recientes, a menudo se corrige un problema de inscripción de dispositivos Windows. 
- ¿Cuál es el mensaje de error exacto?
- ¿Dónde ve el mensaje de error?
- ¿Cuándo empezó el problema? ¿Alguna vez ha funcionado la inscripción? 
- ¿Qué plataforma (Android, iOS/iPadOS o Windows) tiene el problema?
- ¿Cuántos usuarios están afectados? ¿Todos los usuarios están afectados o solo algunos?
- ¿Cuántos dispositivos se ven afectados? ¿Todos los dispositivos se ven afectados o solo algunos?
- ¿Qué es la entidad de MDM?
- ¿Cómo se realiza la inscripción? ¿Se trata de la opción "Bring Your Own Device" (BYOD) o del Programa de inscripción de dispositivos (DEP) de Apple con perfiles de inscripción?

## <a name="error-messages"></a>Mensajes de error

### <a name="this-user-is-not-authorized-to-enroll"></a>Este usuario no está autorizado para inscribirse.

Error 0x801c003: "Este usuario no está autorizado para inscribirse. Puede intentarlo de nuevo o ponerse en contacto con el administrador del sistema con el código de error (0x801c0003)".
Error 80180003: "Se ha producido un problema. Este usuario no está autorizado para inscribirse. Puede intentarlo de nuevo o ponerse en contacto con el administrador del sistema con el código de error 80180003".

**Causa:** Cualquiera de las siguientes condiciones: 

- El usuario ya ha inscrito el número máximo de dispositivos permitidos en Intune.    
- El dispositivo está bloqueado por las restricciones de tipo de dispositivo.    
- El equipo ejecuta Windows 10 Home. Sin embargo, la inscripción en Intune o la unión a Azure AD solo se admiten en Windows 10 Pro y versiones posteriores.

#### <a name="resolution"></a>Solución
Hay varias posibles soluciones a este problema:

##### <a name="remove-devices-that-were-enrolled"></a>Quitar los dispositivos inscritos
1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).    
2. Vaya a **Usuarios** > **Todos los usuarios**.    
3. Seleccione la cuenta de usuario afectada y, después, haga clic en **Dispositivos**.    
4. Seleccione los dispositivos no usados o no deseados y, después, haga clic en **Eliminar**. 

##### <a name="increase-the-device-enrollment-limit"></a>Aumentar el límite de inscripción de dispositivos

> [!NOTE]
> Este método aumenta el límite de inscripción de dispositivos para todos los usuarios, no solo para el usuario afectado.

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Vaya a **Dispositivos** > **Restricciones de inscripción** > **Valores predeterminados** (en **Restricciones de límite de dispositivos**) > **Propiedades** > **Editar** (junto a **Límite de dispositivos**) > aumente el **Límite de dispositivos** (máximo 15) > **Revisar y guardar**.    
 

##### <a name="check-device-type-restrictions"></a>Comprobar las restricciones de tipo de dispositivo
1. Inicie sesión en el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) con una cuenta de administrador global.
2. Vaya a **Dispositivos** > **Restricciones de inscripción** y, después, seleccione la restricción **Valores predeterminados** en **Restricciones de tipo de dispositivo**.    
3. Seleccione **Plataformas** y, después, seleccione **Permitir** para **Windows (MDM)** .

    > [!IMPORTANT]
    > Si la configuración actual ya es **Permitir**, cámbiela a **Bloquear**, guarde la configuración y, después, vuelva a cambiarla a **Permitir** y guarde la configuración de nuevo. De esta forma, se restablece la configuración de la inscripción.

4. Espere aproximadamente 15 minutos y, después, vuelva a inscribir el dispositivo afectado.    

##### <a name="upgrade-windows-10-home"></a>Actualizar Windows 10 Home
[Actualice Windows 10 Home a Windows 10 Pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) o una versión posterior. 



### <a name="this-user-is-not-allowed-to-enroll"></a>No se permite la inscripción de este usuario.

Error 0x801c0003: "No se permite la inscripción de este usuario. Puede intentarlo de nuevo o ponerse en contacto con el administrador del sistema con el código de error 801c0003".

**Causa**: La opción **Los usuarios pueden inscribir dispositivos en Azure AD** está establecida en **Ninguno**. Esto impide que los nuevos usuarios unan sus dispositivos a Azure AD. Por lo tanto, la inscripción de Intune produce un error.

#### <a name="resolution"></a>Solución
1. Inicie sesión en [Azure Portal](https://portal.azure.com/) como administrador.    
2. Vaya a **Azure Active Directory** > **Dispositivos** > **Configuración del dispositivo**.    
3. Establezca **Los usuarios pueden inscribir dispositivos en Azure AD** en **Todos**.    
4. Vuelva a inscribir el dispositivo.   

### <a name="the-device-is-already-enrolled"></a>El dispositivo ya está inscrito.

Error 8018000a: "Se ha producido un problema. El dispositivo ya está inscrito.  Puede ponerse en contacto con el administrador del sistema con el código de error 8018000a".

**Causa:** Se cumple alguna de las siguientes condiciones:
- Otro usuario ya ha inscrito el dispositivo en Intune o lo ha unido a Azure AD. Para determinar si este es el caso, vaya a **Configuración** > **Cuentas** > **Acceso al trabajo**. Busque un mensaje similar al siguiente: "Otro usuario del sistema ya tiene una conexión profesional o educativa. Quite esa conexión profesional o educativa e inténtelo de nuevo".    

#### <a name="resolution"></a>Solución

Utilice uno de los métodos siguientes para resolver el error:

##### <a name="remove-the-other-work-or-school-account"></a>Quitar la otra cuenta profesional o educativa
1. Cierre la sesión de Windows y, después, inicie sesión con la otra cuenta que ha inscrito o unido al dispositivo.    
2. Vaya a **Configuración** > **Cuentas** > **Acceso al trabajo** y, después, quite la cuenta profesional o educativa.
3. Cierre la sesión de Windows y, después, inicie sesión con su cuenta.    
4. Inscriba el dispositivo en Intune o una el dispositivo a Azure AD. 



### <a name="this-account-is-not-allowed-on-this-phone"></a>Esta cuenta no está permitida en este teléfono.

Error: "Esta cuenta no está permitida en este teléfono. Asegúrese de que la información proporcionada es correcta y vuelva a intentarlo o solicite soporte técnico a su empresa".

**Causa**: El usuario que intentó inscribir el dispositivo no tiene una licencia válida de Intune.

#### <a name="resolution"></a>Solución
Asigne una licencia válida de Intune al usuario y, después, inscriba el dispositivo.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>Parece que el punto de conexión de las condiciones de uso de MDM no está configurado correctamente.

**Causa:** Se cumple alguna de las siguientes condiciones: 
 - Usa la administración de dispositivos móviles (MDM) para Office 365 e Intune en el inquilino, y el usuario que intenta inscribir el dispositivo no tiene una licencia válida de Intune o una licencia de Office 365.     
- Los términos y condiciones de MDM en Azure AD están en blanco o no contienen la dirección URL correcta.    

#### <a name="resolution"></a>Solución

Para solucionar este problema, use alguno de los métodos siguientes: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Asignar una licencia válida al usuario
Vaya al [Centro de administración de Microsoft 365](https://portal.office.com/adminportal/home) y, después, asigne una licencia de Intune u Office 365 al usuario.

##### <a name="correct-the-mdm-terms-of-use-url"></a>Corregir la dirección URL de las condiciones de uso de MDM
  1. Inicie sesión en [Azure Portal](https://portal.azure.com/) y seleccione **Azure Active Directory**.    
  2. Seleccione **Mobility (MDM y MAM)** y, después, haga clic en **Microsoft Intune**.    
  3. Seleccione **Restaurar las URL de MDM predeterminadas**, compruebe que la **Dirección URL de las condiciones de uso de MDM** está establecida en **https://portal.manage.microsoft.com/TermsofUse.aspx** .    
  4. Elija **Guardar**.    


### <a name="something-went-wrong"></a>Se ha producido un problema.

Error 80180026: "Se ha producido un problema. Confirme que está usando la información de inicio de sesión correcta y que su organización usa esta característica. Puede intentarlo de nuevo o ponerse en contacto con el administrador del sistema con el código de error 80180026".

**Causa**: Este error puede producirse al intentar unir un equipo Windows 10 a Azure AD y si se cumplen las dos condiciones siguientes: 
- La inscripción automática de MDM está habilitada en Azure.    
- El cliente de PC de Intune (agente de PC de Intune) está instalado en el equipo Windows 10.

#### <a name="resolution"></a>Solución
Utilice uno de los métodos siguientes para resolver esta incidencia:

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Deshabilite la inscripción automática de MDM en Azure.
1. Inicie sesión en [Azure Portal](https://portal.azure.com/).    
2. Vaya a **Azure Active Directory** > **Mobility (MDM y MAM)**  > **Microsoft Intune**.    
3. Establezca el **Ámbito de usuario de MDM** en **Ninguno** y, después, haga clic en **Guardar**.    
     
##### <a name="uninstall"></a>Desinstalar
Desinstale el agente cliente de PC de Intune del equipo.    

### <a name="the-software-cannot-be-installed"></a>El software no se puede instalar.

Error: "No se puede instalar el software, 0x80cf4017".

**Causa**: El software cliente no está actualizado.

#### <a name="resolution"></a>Solución
1. Inicie sesión en [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Vaya a **Administración** > **Descargar software cliente** y, después, haga clic en **Descargar software cliente**.    
3. Guarde el paquete de instalación y, después, instale el software cliente. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>El certificado de cuenta no es válido y puede que haya expirado.

Error: "El certificado de cuenta no es válido, puede que haya expirado, 0x80cf4017".

**Causa**: El software cliente no está actualizado.

#### <a name="resolution"></a>Solución
1. Inicie sesión en [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Vaya a **Administración** > **Descargar software cliente** y, después, haga clic en **Descargar software cliente**.    
3. Guarde el paquete de instalación y, después, instale el software cliente.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>Su organización no es compatible con esta versión de Windows. 

Error: "Hubo un problema. Su organización no es compatible con esta versión de Windows  (0x80180014)".

**Causa**: La inscripción de MDM de Windows está deshabilitada en el inquilino de Intune.

#### <a name="resolution"></a>Solución
Para corregir este problema en un entorno de Intune independiente, siga estos pasos: 
 
1. En el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), elija **Dispositivos** > **Restricciones de inscripción** y seleccione una restricción de tipo de dispositivo.    
2. Elija **Propiedades** > **Editar** (junto a **Configuración de plataforma**) > **Permitir** para **Windows (MDM)** .    
3. Haga clic en **Revisar y guardar**.    

### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Error de instalación durante la inscripción masiva.

**Causa**: Las cuentas de usuario de Azure AD del paquete de la cuenta (Package_GUID) para el paquete de aprovisionamiento correspondiente no pueden unir dispositivos a Azure AD. Estas cuentas de Azure AD se crean automáticamente al configurar un paquete de aprovisionamiento con el Diseñador de configuraciones de Windows (WCD) o la aplicación Configurar equipos académicos, y estas cuentas se usan después para unir los dispositivos a Azure AD.

#### <a name="resolution"></a>Solución
1. Inicie sesión en [Azure Portal](https://portal.azure.com/) como administrador.    
2. Vaya a **Azure Active Directory > Dispositivos > Configuración del dispositivo**.    
3. Establezca **Los usuarios pueden inscribir dispositivos en Azure AD** en **Todos** o **Seleccionado**.

   Si elige **Seleccionado**, haga clic en **Seleccionado** y, después, haga clic en **Agregar miembros** para agregar todos los usuarios que pueden unir sus dispositivos a Azure AD. Asegúrese de que se han agregado todas las cuentas de Azure AD del paquete de aprovisionamiento.
 
Para más información sobre cómo crear un paquete de aprovisionamiento para el Diseñador de configuraciones de Windows, vea [Crear un paquete de aprovisionamiento para Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package).

Para más información sobre la aplicación Configurar equipos académicos, vea [Usar la aplicación Configurar equipos académicos](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Inscripción automática de MDM: error 

Al intentar inscribir automáticamente un dispositivo Windows 10 mediante la directiva de grupo, se producen los siguientes problemas: 
- En el Programador de tareas, en **Microsoft** > **Windows** > **EnterpriseMgmt**, el resultado de la última ejecución de la tarea **Programación creada por el cliente de inscripción para inscribirse automáticamente en MDM desde AAD** es el siguiente: **Evento 76, error de inscripción automática (código de error de Win32 desconocido: 0x8018002b)** .       
- En el Visor de eventos, se registra el siguiente evento en **Registros de aplicaciones y servicios/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/Admin**:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**Causa:** Se cumple alguna de las siguientes condiciones: 
- El UPN contiene un dominio no verificado o no enrutable, como. .local (tipo joe@contoso.local).    
- El **ámbito de usuario de MDM** está establecido en **Ninguno**. 

#### <a name="resolution"></a>Solución
Si el UPN contiene un dominio no verificado o no enrutable, siga estos pasos: 

1. En el servidor en el que se ejecuta Active Directory Domain Services (AD DS), abra **Usuarios y equipos de Active Directory**; para ello, escriba **dsa.msc** en el cuadro de diálogo **Ejecutar** y, después, haga clic en **Aceptar**.    
2. Haga clic en **Usuarios** en el dominio y, después, haga lo siguiente:  
    - Si solo hay un usuario afectado, haga clic con el botón derecho en el usuario y, después, haga clic en **Propiedades**. En la pestaña **Cuenta**, en la lista desplegable Sufijo UPN, en **Nombre de inicio de sesión del usuario**, seleccione un sufijo UPN válido como contoso.com y, después, haga clic en **Aceptar**.    
    - Si hay varios usuarios afectados, seleccione los usuarios y, en el menú **Acción**, haga clic en **Propiedades**. En la pestaña **Cuenta**, active la casilla **Sufijo UPN**, seleccione un sufijo UPN válido como contoso.com en la lista desplegable y, después, haga clic en **Aceptar**.
3. Espere a la siguiente sincronización o fuerce una sincronización diferencial desde el servidor de sincronización mediante la ejecución de los siguientes comandos en un símbolo del sistema de PowerShell con privilegios elevados:
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Si **Ámbito de usuario de MDM** se establece en **Ninguno**, siga estos pasos: 
 
1. Inicie sesión en [Azure Portal](https://portal.azure.com/) y seleccione **Azure Active Directory**.
2. Seleccione **Mobility (MDM y MAM)** y, después, seleccione **Microsoft Intune**.    
3. Establezca **Ámbito de usuario de MDM** en **Todos**. O bien, establezca **Ámbito de usuario de MDM** en **Algunos** y seleccione los grupos que pueden inscribir automáticamente sus dispositivos Windows 10.    
4. Establezca **Ámbito de usuario de MAM** en **Ninguno**.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Se produjo un error al crear el perfil de Autopilot.

**Causa**: El formato de nombre especificado de la plantilla de nombre de dispositivo no cumple los requisitos. Por ejemplo, usa minúsculas para la macro de serie, como %serial% en lugar de %SERIAL%.

#### <a name="resolution"></a>Solución

Asegúrese de que el formato de nombre cumple los requisitos siguientes:

- Cree un nombre único para los dispositivos. Los nombres deben tener 15 caracteres o menos, y pueden contener letras (a-z, A-Z), números (0-9) y guiones (‐).
- Los nombres no pueden estar formados solo por números.
- Los nombres no pueden contener espacios en blanco.
- Use la macro %SERIAL% para agregar el número de serie de hardware específico. O bien, utilice la macro %RAND:<n.º de dígitos>% para agregar una cadena aleatoria de números; la cadena contiene <n.º de dígitos> dígitos. Por ejemplo, MYPC-%RAND:6% genera un nombre como MYPC-123456.

### <a name="something-went-wrong-oobeidps"></a>Se ha producido un problema. OOBEIDPS.

**Causa**: Este problema se produce si hay un proxy, un firewall u otro dispositivo de red que está bloqueando el acceso al proveedor de identidades (IdP).

#### <a name="resolution"></a>Solución
Asegúrese de que el acceso necesario a los servicios basados en Internet para Autopilot no está bloqueado. Para más información, vea [Requisitos de red de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network).


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>Registrando el dispositivo para la administración móvil (Error: 3, 0x801C03EA).

**Causa**: El dispositivo tiene un chip TPM que admite la versión 2.0, pero aún no se ha actualizado a la versión 2.0.

#### <a name="resolution"></a>Solución
Actualice el chip TPM a la versión 2.0.

Si el problema persiste, compruebe si el mismo dispositivo está en dos grupos asignados, de tal forma que cada grupo esté asignado a un perfil de Autopilot distinto. Si se encuentra en dos grupos, determine qué perfil de Autopilot debe aplicarse al dispositivo y, después, quite la asignación del otro perfil.

Para más información sobre cómo implementar un dispositivo Windows en modo de pantalla completa con Autopilot, vea [Implementación del modo de pantalla completa con Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="securing-your-hardware-failed-0x800705b4"></a>Protección del hardware (error: 0x800705b4).

Error 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**Causa**: El dispositivo Windows de destino no cumple ninguno de los siguientes requisitos:

- El dispositivo debe tener un chip TPM 2.0 físico. Los dispositivos con TPM virtuales (por ejemplo, máquinas virtuales Hyper-V) o los chips TPM 1.2 no funcionan con el modo de implementación automática.
- El dispositivo debe ejecutar una de las siguientes versiones de Windows:
    - Compilación 1703 de Windows 10 o una versión posterior.
    - Si se usa Unión a Azure AD híbrido, la compilación 1809 de Windows 10 o una versión posterior.


#### <a name="resolution"></a>Solución
Asegúrese de que el dispositivo de destino cumple los dos requisitos que se describen en la sección **Causa**.

Para más información sobre cómo implementar un dispositivo Windows en modo de pantalla completa con Autopilot, vea [Implementación del modo de pantalla completa con Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="something-went-wrong-error-code-80070774"></a>Se ha producido un problema. Código de error 80070774.

Error 0x80070774: Hubo un problema. Confirme que está usando la información de inicio de sesión correcta y que su organización usa esta característica. Puede intentarlo de nuevo o ponerse en contacto con el administrador del sistema con el código de error 80070774.

Este problema se produce normalmente antes de que el dispositivo se reinicie en un escenario de Azure AD híbrido en Autopilot, cuando el dispositivo agota el tiempo de espera durante la pantalla de inicio de sesión inicial. Significa que el controlador de dominio no se puede encontrar o no se puede acceder a él correctamente debido a problemas de conectividad. O bien, que el dispositivo ha entrado en un estado que no se puede unir al dominio.

**Causa**: La causa más común es que se está usando Unión a Azure AD híbrido y que la característica de asignación de usuario está configurada en el perfil de Autopilot. El uso de la característica de asignación de usuarios realiza una unión a Azure AD en el dispositivo durante la pantalla de inicio de sesión inicial, que pone el dispositivo en un estado en el que no se puede unir al dominio local. Por lo tanto, la característica de asignación de usuarios solo se debe usar en escenarios de Unión a Azure AD estándar en Autopilot.  La característica no debe usarse en escenarios de Unión a Azure AD híbrido.

#### <a name="resolution"></a>Solución

1. En el [Centro de administración de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), elija > **Dispositivos** > **Windows** > **Dispositivos Windows**.
2. Seleccione el dispositivo que está experimentando el problema y haga clic en los puntos suspensivos (...) del lado derecho.
3. Seleccione **Desasignar usuario** y espere a que finalice el proceso.
4. Compruebe que se ha asignado el perfil de Azure AD híbrido en Autopilot antes de volver a intentarlo con OOBE.

#### <a name="second-resolution"></a>Segunda resolución
Si el problema persiste, en el servidor que hospeda el conector de Intune Unión a dominio sin conexión, compruebe si el identificador de evento 30312 está registrado en el registro del servicio ODJ Connector. El evento 30312 es similar al siguiente:

```
Log Name:      ODJ Connector Service
Source:        ODJ Connector Service Source
Event ID:      30132
Level:         Error
Description:
{
          "Metric":{
                   "Dimensions":{
                             "RequestId":"<RequestId>",
                             "DeviceId":"<DeviceId>",
                             "DomainName":"contoso.com",
                             "ErrorCode":"5",
                             "RetryCount":"1",
                              "ErrorDescription":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation",
                              "InstanceId":"<InstanceId>",
                              "DiagnosticCode":"0x00000800",
                              "DiagnosticText":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation [Exception Message: \"DiagnosticException: 0x00000800. Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation\"] [Exception Message: \"Failed to call NetProvisionComputerAccount machineName=<ComputerName>\"]"
                   },
                   "Name":"RequestOfflineDomainJoinBlob_Failure",
                   "Value":0
          }
}
```

Este problema se debe normalmente a la delegación incorrecta de los permisos en la unidad organizativa en la que se crean los dispositivos Windows Autopilot. Para más información, vea [Aumento del límite de la cuenta de equipo en la unidad organizativa](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit).

1. Abra **Usuarios y equipos de Active Directory (DSA.msc)** .
2. Haga clic con el botón derecho en la unidad organizativa que usará para crear equipos unidos a Azure AD híbrido > **Delegar control**.
3. En el asistente **Delegación de control**, haga clic en **Siguiente** > **Agregar** > **Tipos de objeto**.
4. En panel **Tipos de objeto**, seleccione la casilla **Equipos** > **Aceptar**.
5. En el panel **Seleccionar usuarios**, **Equipos** o **Grupos**, en el cuadro **Escriba los nombres de objeto que desea seleccionar**, escriba el nombre del equipo donde está instalado el conector.
6. Seleccione **Comprobar nombres** para validar la entrada > **Aceptar** > **Siguiente**.
7. Haga clic en **Crear una tarea personalizada para delegar** > **Siguiente**.
8. Active la casilla **Solo los siguientes objetos en la carpeta** y, después, active las casillas **Objetos de equipo**, **Crear los objetos seleccionados en esta carpeta** y **Eliminar los objetos seleccionados en esta carpeta**.
9. Seleccione **Siguiente**.
10. En **Permisos**, active la casilla **Control total**. Esta acción selecciona todas las demás opciones.
11. Seleccione **Siguiente** > **Finalizar**.

### <a name="the-enrollment-status-page-times-out-before-the-sign-in-screen"></a>Se agota el tiempo de espera de la página de estado de inscripción antes de la pantalla de inicio de sesión

**Causa**: Este problema puede producirse si se cumplen todas las condiciones siguientes:
- Usa la página estado de inscripción para realizar un seguimiento de Microsoft Store para aplicaciones empresariales.
- Tiene una directiva de acceso condicional de Azure AD que usa el control para requerir que un dispositivo se marque como compatible.
- La directiva se aplica a todas las aplicaciones y ventanas en la nube.

#### <a name="resolution"></a>Solución:
Intente realizar una de las siguientes acciones:
- Destine las directivas de cumplimiento de Intune a los dispositivos. Asegúrese de que se puede determinar el cumplimiento antes de que el usuario inicie sesión.
- Use las licencias sin conexión para las aplicaciones de la tienda. De este modo, el cliente de Windows no tiene que comprobar Microsoft Store antes de determinar el cumplimiento del dispositivo.



## <a name="next-steps"></a>Pasos siguientes

- [Solucionar problemas con la inscripción de dispositivos en Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Formule una pregunta en el foro de Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Revise el blog del equipo de soporte técnico de Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Revise el blog de Enterprise Mobility and Security de Microsoft](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Cómo obtener asistencia para Microsoft Intune](../fundamentals/get-support.md)
- [Buscar errores de inscripción de administración conjunta](https://docs.microsoft.com/configmgr/comanage/how-to-monitor#enrollment-errors)
