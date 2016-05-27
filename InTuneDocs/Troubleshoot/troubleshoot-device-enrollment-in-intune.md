---
# required metadata

title: Solución de problemas con la inscripción de dispositivos | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Solución de problemas con la inscripción de dispositivos en Intune

Aquí se indican algunos problemas relacionados con la inscripción de dispositivos y cómo puede solucionarlos.

> [!NOTE]
> Los usuarios de dispositivos administrados pueden recopilar registros de inscripción y diagnóstico para que usted pueda revisarlos. Aquí se proporcionan instrucciones de usuario para recopilar registros:
>- [Send Android diagnostic data logs to your IT administrator using a USB cable (Enviar registros de datos de diagnóstico de Android al administrador de TI mediante un cable USB)](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
>- [Send Android diagnostic data logs to your IT administrator using email (Enviar registros de datos de diagnóstico de Android al administrador de TI mediante correo electrónico)](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
>- [Send Android enrollment errors to your IT administrator (Enviar errores de inscripción de Android al administrador de TI)](/intune/enduser/send-enrollment-errors-to-your-it-administrator-android)
>- [Send iOS enrollment errors to your IT administrator (Enviar errores de inscripción de iOS al administrador de TI)](/intune/enduser/send-errors-to-your-it-admin-ios)


Si esta información no soluciona el problema, vea [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico para Microsoft Intune) para conocer otras formas de obtener ayuda.

## Se alcanzó el límite de dispositivos
**Problema:** un usuario recibió un error en su dispositivo durante la inscripción (por ejemplo, el error **Portal de empresa no disponible temporalmente** en un dispositivo iOS) y el registro DMPdownloader.log que se encuentra en Configuration Manager contiene el error **DeviceCapReached**..

**Solución:** de forma predeterminada, los usuarios no pueden inscribir más de 5 dispositivos.

### Compruebe el número de dispositivos inscritos y permitidos

1.  Asegúrese de que el usuario no tiene más de 5 dispositivos asignados en el Portal de administración de Intune

2.  Compruebe en el Portal de administración de Intune, en Administrador\Dispositivo móvil\Reglas de inscripción, que el límite de inscripción de dispositivos está establecido en 5

Los usuarios de dispositivos móviles pueden eliminar dispositivos en la siguiente URL: [https://byodtestservice.azurewebsites.net/](https://byodtestservice.azurewebsites.net/)..

Los administradores pueden eliminar dispositivos en el portal de Azure Active Directory.

### Eliminar dispositivos en el portal de Azure Active Directory

1.  Vaya a [http://aka.ms/accessaad](http://aka.ms/accessaad) o haga clic en **Administrador** &gt; **Azure AD** en [https://portal.office.com](https://portal.office.com)..

2.  Inicie sesión con su identificador de organización mediante el vínculo que encontrará en el lado izquierdo de la página.

3.  Cree una suscripción de Azure si no tiene una. Si tiene una cuenta de pago, no necesitará una tarjeta de crédito o realizar ningún pago (haga clic en el vínculo de suscripción **Registre su suscripción gratuita de Azure Active Directory** ).

4.  Seleccione **Active Directory** y, a continuación, seleccione su empresa.

5.  Seleccione la pestaña **Usuarios** .

6.  Seleccione el usuario cuyos dispositivos desea eliminar.

7.  Haga clic en **Dispositivos**..

8.  Quite los dispositivos que crea oportunos, como por ejemplo aquellos que ya no estén en uso o que tienen definiciones inexactas.

> [!NOTE]

> Puede evitar llegar el límite de inscripciones de dispositivos mediante el uso de administradores de inscripción de dispositivos, tal como se describe en [Enroll corporate-owned devices with the Device Enrollment Manager in Microsoft Intune](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) (Inscribir dispositivos propiedad de la empresa con el Administrador de inscripción de dispositivos de Microsoft Intune)..
>
> Si agrega una cuenta de usuario al grupo de administradores de inscripción de dispositivos, esta no podrá realizar la inscripción al aplicarse la directiva de acceso condicional cuando ese usuario en cuestión inicie sesión.

## Error de instalación de perfil
**Problema:** un usuario recibió un **error en la instalación del perfil** en un dispositivo de iOS o Android.

### Pasos para solucionar problemas con la instalación del perfil

1.  Confirme que el usuario tiene asignada una licencia adecuada para la versión del servicio Intune que usa.

2.  Confirme que el dispositivo no esté inscrito en otro proveedor MDM o que no tenga ya instalado un perfil de administración.

3.  Si el dispositivo es iOS, vaya a [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) e intente instalar el perfil cuando se le solicite.

4.  Confirme que Safari y Chrome son los exploradores predeterminados de su dispositivo iOS o Android respectivamente, y que las cookies están habilitadas.

## El Portal de empresa no está disponible temporalmente
**Problema:** un usuario recibió en su dispositivo el error **El Portal de empresa no está disponible temporalmente**.

### Solucionar el error “El Portal de empresa no está disponible temporalmente”

1.  Quite la aplicación Portal de empresa de Intune del dispositivo.

2.  En el dispositivo, abra el explorador, vaya a [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com), e intente un inicio de sesión de usuario.

3.  Si el usuario no puede iniciar sesión, intente usar otra red.

4.  Si ello produce un error, compruebe que las credenciales del usuario se han sincronizado correctamente con Azure Active Directory.

5.  Si el usuario inicia sesión correctamente, el dispositivo iOS le pedirá que instale la aplicación Portal de empresa de Intune y que se inscriba. En un dispositivo Android, debe instalar manualmente la aplicación Portal de empresa de Intune y, a continuación, puede volver a intentar inscribirse.

## Entidad de MDM no definida
**Problema:** un usuario recibió el error **Entidad de MDM no definida**.

### Solucionar el error “Entidad de MDM no definida”

1.  Compruebe que la entidad de MDM se ha establecido correctamente para la versión del servicio Intune que usa; esto es, para Intune, MDM de Office 365 y System Center Configuration Manager con Intune. Para Intune, se establece la entidad de MDM en **Administrador** &gt; **Administración de dispositivos móviles**. Para Configuration Manager con Intune, deberá establecerla al configurar el conector de Intune. En O365 deberá acceder a una configuración denominada **Dispositivos móviles**..

    > [!NOTE]
    > Una vez establecida la entidad de MDM, solo podrá cambiarla si se pone en contacto con el soporte técnico, tal como se describe en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico para Microsoft Intune)..

2.  Compruebe que las credenciales del usuario se han sincronizado correctamente con Azure Active Directory; para ello, asegúrese de que sus UPN coinciden con la información de Active Directory en el Portal de cuentas.
    Si el UPN no coincide con la información de Active Directory:

    1.  Desactive DirSync en el servidor local.

    2.  Elimine el usuario que no coincida de la lista de usuarios **Portal de cuentas de Intune** .

    3.  Espere aproximadamente una hora para permitir que el servicio de Azure pueda quitar los datos incorrectos.

    4.  Vuelva a activar DirSync y compruebe si el usuario ya se ha sincronizado correctamente.

3.  Si usa System Center Configuration Manager con Intune, compruebe que el usuario tiene un identificador válido de usuario en la nube:

    1.  Abra SQL Management Studio.

    2.  Conéctese a la base de datos adecuada.

    3.  Abra la carpeta de bases de datos y busque y abra la carpeta **CM_DBName**, donde DBName es el nombre de la base de datos de cliente.

    4.  En la parte superior, haga clic en Nueva consulta y ejecute las siguientes consultas:

        -   Para ver todos los usuarios:
            `select * from [CM_ DBName].[dbo].[User_DISC]`

        -   Para ver usuarios específicos, use la siguiente consulta, donde %testuser1% representa el elemento username@domain.com referente al usuario que desea buscar:
            `select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        Una vez escrita la consulta, haga clic en **!Execute**..
        Cuando obtenga los resultados, busque el identificador clouduser.  Si no encuentra ningún identificador, esto quiere decir que el usuario no tiene licencia para usar Intune.

## Los dispositivos móviles desaparecen cuando se usa System Center Configuration Manager con Intune
**Problema:** después de inscribir correctamente un dispositivo móvil a Configuration Manager, este desaparece de la colección de dispositivos móviles, pero el dispositivo aún tiene el perfil de administración y aparece en la puerta de enlace de CSS.

**Solución:** esto puede ocurrir si tiene un proceso personalizado que quita dispositivos que no estén unidos al dominio o porque el usuario ha retirado la suscripción del dispositivo. Para validar y comprobar qué proceso o cuenta de usuario ha quitado el dispositivo de la consola de Configuration Manager, siga los pasos siguientes.

### Compruebe cómo se quitó el dispositivo

1.  En la consola de administración de Configuration Manager, seleccione **Supervisión** &gt; **Estado del sistema** &gt; **Consultas de mensaje de estado**..

2.  Haga clic con el botón derecho en **Recursos de miembro de la recopilación eliminados manualmente** y seleccione **Mostrar mensajes**..

3.  Seleccione la fecha y hora apropiadas o las últimas 12 horas.

4.  Busque el dispositivo en cuestión y compruebe cómo se quitó el dispositivo. En el ejemplo siguiente se muestra que la cuenta SCCMInstall eliminó el dispositivo a través de una aplicación desconocida.

    ![Captura de pantalla del diagnóstico de eliminación del dispositivo](./media/CM_With_Intune_Unknown_App_Deleted_Device.jpg)

5.  Compruebe que Configuration Manager no tenga ninguna tarea, script u otro proceso programado que pudiera estar purgando de forma automática dispositivos móviles que no pertenezcan al dominio u otros dispositivos relacionados.

## El dispositivo iOS inscrito no aparece en la consola cuando se usa System Center Configuration Manager con Intune
**Problema:** el usuario inscribe el dispositivo iOS, pero no aparece en la consola de administración de Configuration Manager. El dispositivo no indica que se ha inscrito. Posibles causas:

- Puede que haya inscrito el conector de Intune en una cuenta y que después lo haya inscrito en otra cuenta. 
- Puede que haya descargado el certificado MDM de una cuenta y que lo haya usado en otra cuenta.


**Solución:** lleve a cabo los pasos siguientes:

1. Deshabilite iOS en el conector de Windows Intune. 
    1. Haga clic con el botón derecho en la suscripción de Intune y seleccione "Propiedades".
    1. En la pestaña "iOS", desactive la opción "Habilitar inscripción de iOS".



1. En SQL, ejecute los pasos siguientes en la base de datos de CAS.
  
    1. update SC_ClientComponent_Property set Value2 = '' where Name like '%APNS%' 
    1. delete from MDMPolicy where PolicyType = 7 
    1. delete from MDMPolicyAssignment where PolicyType = 7
    1. update SC_ClientComponent_Property set Value2 = '' where Name like '%APNS%' 
    1. delete from MDMPolicy where PolicyType = 11 
    1. delete from MDMPolicyAssignment where PolicyType = 11 
    1. DELETE Drs_Signals
1. Reinicie el servicio SMS Executive o el servidor de CM. 



1. Obtenga un nuevo certificado de APNs y cárguelo. Haga clic con el botón derecho en la suscripción de Intune en el panel izquierdo de Configuration Manager. Seleccione **Crear solicitud de certificado APNs** y siga las instrucciones.


## El equipo ya está inscrito. Error hr 0x8007064c
**Problema:** la inscripción produce un error con el mensaje **The machine is already enrolled** (El equipo ya está inscrito). El registro de inscripción muestra el error **hr 0x8007064c**..
  
Esto puede deberse a que el equipo se inscribió anteriormente o a que tiene la imagen clonada de un equipo ya inscrito. El certificado de cuenta de la cuenta anterior sigue estando presente en el equipo.



**Solución:** 

1. En el menú **Inicio**, **Ejecutar** -> **MMC**.. 
1. **Archivo** -> **Add/ Remove Snap-ins** (Agregar o quitar complementos)..
1. Haga doble clic en **Certificados**, elija **Cuenta de equipo**, **Siguiente** y seleccione **Equipo local**..
1. Haga doble clic en **Certificados (equipo local)** y elija **Personal/ Certificates** (Personal / Certificados).. 
1. Busque el certificado de Intune emitido por Sc_Online_Issuing y elimínelo si está presente.
1. Elimine esta clave del Registro si existe: ** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey** y todas las subclaves.
1. Intente volver a realizar la inscripción. 
1. Si todavía no puede inscribir el equipo, busque y elimine esta clave, si existe: **KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**.. 
1. Intente volver a realizar la inscripción. 

    > [!IMPORTANT]
    > Esta sección, método o tarea contiene pasos que indican cómo modificar el Registro. Pero pueden producirse problemas graves si modifica incorrectamente el Registro. Por lo tanto, asegúrese de que sigue estos pasos cuidadosamente. Como protección adicional, haga una copia de seguridad del Registro antes de modificarlo. Y así, si se produce algún problema, puede restaurarlo.
    > Para más información sobre cómo realizar copias de seguridad del Registro y cómo restaurarlo, lea [Cómo hacer copia de seguridad y restaurar el registro de Windows](https://support.microsoft.com/en-us/kb/322756).

## No se puede crear la directiva o inscribir dispositivos si el nombre de la empresa contiene caracteres especiales
**Problema:** no se puede crear la directiva o inscribir dispositivos.

**Solución:** en el [Centro de administración de Office 365](https://portal.office.com/), quite los caracteres especiales del nombre de la empresa y guarde la información de la empresa.

## No se puede iniciar sesión o inscribir dispositivos cuando se tienen varios dominios comprobados
**Problema:** es posible que, al agregar un segundo dominio comprobado a AD FS, los usuarios con el sufijo del nombre principal de usuario (UPN) del segundo dominio no puedan iniciar sesión en los portales o inscribir dispositivos. 


**Solución:** los clientes de Microsoft Office 365 que usan el inicio de sesión único (SSO) a través de AD FS 2.0 y que tienen varios dominios de nivel superior para los sufijos UPN de los usuarios de su organización (por ejemplo, @contoso.com o @fabrikam.com) deben implementar una instancia independiente del servicio de federación de AD FS 2.0 para cada sufijo.  Ahora hay una [acumulación para AD FS 2.0](http://support.microsoft.com/kb/2607496) que funciona con el conmutador **SupportMultipleDomain** para permitir que el servidor de AD FS admita este escenario sin necesidad de servidores de AD FS 2.0 adicionales. Vea [este blog](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/) para más información.



## Códigos de error

|Código de error|Posible problema|Solución recomendada|
|--------------|--------------------|------------------------|
|0x80CF0437 |El reloj del equipo cliente no está configurado en la hora correcta.|Asegúrese de que el reloj y la zona horaria del equipo cliente se hayan configurado en la hora y la zona horaria correctas.
|
|0x80240438, 0x80CF0438, 0x80CF402C|No se puede conectar con el servicio de Intune. Compruebe la configuración del proxy del cliente.|Compruebe que la configuración del proxy del equipo cliente sea compatible con Intune y que el equipo cliente tenga acceso a Internet.|
|0x80240438, 0x80CF0438|La configuración del proxy en Internet Explorer y el sistema local no se ha establecido.|No se puede conectar con el servicio de Intune. Compruebe la configuración del proxy del cliente y confirme que la configuración del proxy en el equipo cliente sea compatible con Intune y que el equipo cliente tiene acceso a Internet.|
|0x80043001, 0x80CF3001, 0x80043004, 0x80CF3004|El paquete de inscripción no está actualizado.|Descargue e instale el paquete de software cliente actual del área de trabajo Administración.|
|0x80043002, 0x80CF3002|La cuenta está en modo de mantenimiento.|No es posible inscribir nuevos equipos cliente cuando la cuenta está en modo de mantenimiento. Para ver la configuración de la cuenta, inicie sesión en la cuenta.|
|0x80043003, 0x80CF3003|Se ha eliminado la cuenta.|Compruebe que su cuenta y la suscripción a Intune todavía están activas. Para ver la configuración de la cuenta, inicie sesión en la cuenta.|
|0x80043005, 0x80CF3005|El equipo cliente se ha retirado.|Espere unas pocas horas, quite cualquier versión anterior del software cliente del equipo y, a continuación, intente instalar de nuevo el software cliente.|
|0x80043006, 0x80CF3006|Se ha alcanzado el máximo número de puestos permitido para la cuenta.|Su organización debe adquirir puestos adicionales antes de inscribir más equipos cliente en el servicio.|
|0x80043007, 0x80CF3007|No se encontró el archivo de certificado en la misma carpeta que el programa de instalación.|Extraiga todos los archivos antes de iniciar la instalación. No cambie el nombre ni la ubicación de los archivos extraídos: todos los archivos deben existir en la misma carpeta o de lo contrario, la instalación será errónea.|
|0x8024D015, 0x00240005, 0x80070BC2, 0x80070BC9, 0x80CFD015|No se puede instalar el software porque el equipo cliente está pendiente de reiniciarse.|Reinicie el equipo y, a continuación, intente instalar de nuevo el software cliente.|
|0x80070032|No se encontró uno o más requisitos previos para instalar el software cliente en el equipo cliente.|Asegúrese de que las actualizaciones necesarias están instaladas en el equipo cliente y, a continuación, intente instalar de nuevo el software cliente.|
|0x80043008, 0x80CF3008|No se pudo iniciar el servicio de actualización de Microsoft Online Management.|Póngase en contacto con el soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune)..|
|0x80043009, 0x80CF3009|El equipo cliente ya está inscrito en el servicio.|Debe retirar el equipo cliente para poder volver a inscribirlo en el servicio.|
|0x8004300B, 0x80CF300B|No se puede ejecutar el paquete de instalación del software cliente porque no se admite la versión de Windows que se está ejecutando en el cliente.|Intune no es compatible con la versión de Windows que se está ejecutando en el equipo cliente.|
|0xAB2|Windows Installer no pudo tener acceso al tiempo de ejecución de VBScript para una acción personalizada.|Este error está causado por una acción personalizada basada en Bibliotecas de vínculos dinámicos (DLL). Cuando solucione problemas de DLL, quizás deba usar las herramientas que se describen en [Microsoft Support KB198038: Useful Tools for Package and Deployment Issues](https://support.microsoft.com/en-us/kb/198038) (Soporte técnico de Microsoft KB198038: Herramientas útiles para problemas de implementación y de paquete)..|
|0x80cf0440|Se terminó la conexión al extremo de servicio.|La cuenta de prueba o de pago está suspendida. Cree una nueva cuenta de prueba o de pago y vuelva a realizar la inscripción.|


## Errores de inscripción de iOS
Se proporciona una lista de otros errores de inscripción de iOS en la documentación de usuario del dispositivo, en [You see errors while trying to enroll your device in Intune](/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune) (Ve errores al intentar inscribir su dispositivo en Intune)..

### Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune)..


<!--HONumber=May16_HO1-->


