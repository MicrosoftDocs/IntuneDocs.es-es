---
title: Retirada o borrado de los dispositivos mediante Microsoft Intune - Azure | Microsoft Docs
description: Retire o borre un dispositivo en un dispositivo Android, perfil de trabajo Android, iOS, macOS o Windows con Microsoft Intune. Elimine también un dispositivo de Azure Active Directory.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 44923d89647118268c7a55746599354ac88fbfd2
ms.sourcegitcommit: d3b1e3fffd3e0229292768c7ef634be71e4736ae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2018
ms.locfileid: "52861020"
---
# <a name="remove-devices-by-using-wipe-retire-or-manually-unenrolling-the-device"></a>Eliminación de dispositivos mediante el borrado, la retirada o la anulación manual de la inscripción del dispositivo

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mediante las acciones **Retirar** o **Borrar**, puede quitar de Intune los dispositivos que ya no son necesarios, que se van a reasignar o que han desaparecido. Los usuarios también pueden emitir un comando remoto desde el Portal de empresa de Intune para los dispositivos de propiedad privada que están inscritos en Intune.

> [!NOTE]
> Antes de eliminar un usuario de Azure Active Directory (Azure AD), use la acción **Borrar** o **Retirar** para todos los dispositivos asociados a ese usuario. Si elimina usuarios que tienen dispositivos administrados desde Azure AD, Intune ya no podrá borrar o retirar esos dispositivos.

## <a name="wipe"></a>Eliminación de datos

La acción **Borrar** restaura un dispositivo a su configuración de fábrica predeterminada. Los datos de usuario se conservan si decide activar la casilla **Conservar el estado de inscripción y la cuenta de usuario**. Si no, la unidad se borra de forma segura.

|Acción de borrado|**Conservar el estado de inscripción y la cuenta de usuario**|Quitado de la administración de Intune|Descripción|
|:-------------:|:------------:|:------------:|------------|
|**Eliminación de datos**| No activada | Sí | Borra todas las cuentas de usuario, los datos, las directivas de MDM y la configuración. Restablece el sistema operativo a su configuración y estado predeterminados.|
|**Eliminación de datos**| Activada | No | Borra todas las directivas de MDM. Conserva los datos y las cuentas de usuario. Restablece la configuración del usuario a los valores predeterminados. Restablece el sistema operativo a su configuración y estado predeterminados.|

La opción **Conservar el estado de inscripción y la cuenta de usuario** solo está disponible para Windows 10 versión 1709 o posterior.

Las directivas de MDM se volverán a aplicar la próxima vez que el dispositivo se conecte a Intune.

Un borrado es útil para restablecer un dispositivo antes de dárselo a otro usuario o en el caso de que el dispositivo se haya perdido o lo hayan robado. Tenga cuidado al seleccionar **Borrar**. Los datos del dispositivo no se pueden recuperar.

### <a name="wiping-a-device"></a>Borrado de un dispositivo

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** > **Todos los dispositivos**.
4. Seleccione el nombre del dispositivo que quiere borrar.
5. En el panel en el que se muestra el nombre del dispositivo, haga clic en **Borrar**.
6. Para Windows 10 versión 1709 y versiones posteriores, también tiene la opción **Conservar el estado de inscripción y la cuenta de usuario**. 
    
    |Se conserva durante un borrado |No se conserva|
    | -------------|------------|
    |Cuentas de usuario asociadas con el dispositivo|Archivos de usuario|
    |Estado del equipo \(unión a un dominio, unido a Azure AD)| Aplicaciones instaladas por el usuario \(tienda y aplicaciones de Win32)|
    |Inscripción de la Administración de dispositivos móviles (MDM)|Configuración del dispositivo no predeterminada|
    |Aplicaciones instaladas por OEM \(tienda y aplicaciones de Win32)||
    |Perfil de usuario||
    |Datos de usuario que se encuentran fuera del perfil de usuario||
    |Inicio de sesión automático del usuario|| 
    
         
7. Para confirmar el borrado, haga clic en **Sí**.

Si el dispositivo está encendido y conectado, la acción **Borrar** se propaga por todos los tipos de dispositivos en menos de 15 minutos.

## <a name="retire"></a>Retirar

La acción **Retirar** elimina los datos de las aplicaciones administradas (si procede), la configuración y los perfiles de correo electrónico asignados con Intune. El dispositivo se quita de la administración de Intune. Esto sucede la próxima vez que el dispositivo se registra y recibe la acción remota **Retirar**.

**Retirar** deja los datos personales del usuario en el dispositivo.  

En las tablas siguientes se describen los datos que se eliminan y el efecto de la acción **Retirar** en los datos que permanecen en el dispositivo después de eliminar los datos de la empresa.

### <a name="ios"></a>iOS

|Tipo de datos|iOS|
|-------------|-------|
|Aplicaciones de empresa y datos asociados instalados por Intune.|**Aplicaciones instaladas mediante Portal de empresa:** se quitan todos los datos de aplicación y las aplicaciones. Entre estas aplicaciones se incluyen aquellas instaladas originalmente desde App Store y posteriormente administradas como aplicaciones de la empresa. <br /><br /> **Aplicaciones de Microsoft que usan la administración de aplicaciones móviles y se instalaron desde App Store:** Se quitarán los datos de la aplicación personal. No se quitarán las aplicaciones ni los datos de la aplicación de la empresa.|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado.|
|Configuración de perfil de certificado|Certificados eliminados y revocados.|
|Agente de administración|Se quitará el perfil de administración.|
|Correo electrónico|Se borran los perfiles de correo electrónico que se aprovisionan mediante Intune. Se elimina el correo electrónico almacenado en caché en el dispositivo.|
|Outlook|Se quita el correo electrónico recibido en la aplicación de Microsoft Outlook para iOS. Esto exige que la aplicación móvil de Outlook primero se implemente como una aplicación Requerida para los usuarios de iOS.|
|Separación de Azure AD|Se quita el registro de Azure AD.|
|Contactos |Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa. No se pueden quitar los contactos sincronizados desde la libreta de direcciones nativa a otro origen externo. <br /> <br />En este momento solo se admite la aplicación Outlook.

### <a name="android"></a>Android

|Tipo de datos|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Vínculos web|Quitado.|Quitado.|
|Aplicaciones no administradas de Google Play|Se mantendrán instalados los datos y las aplicaciones.|Se mantendrán instalados los datos y las aplicaciones.|
|Aplicaciones de línea de negocio no administradas|Se mantendrán instalados los datos y las aplicaciones.|Las aplicaciones se desinstalan y se quitan los datos locales de la aplicación. No se quitan los datos que se encuentran fuera de la aplicación (por ejemplo, en una tarjeta SD).|
|Aplicaciones administradas de Google Play|Se quitan los datos de la aplicación. La aplicación no se elimina. Los datos protegidos mediante el cifrado Administración de aplicaciones móviles (MAM) fuera de la aplicación (por ejemplo, las tarjetas SD) permanecen cifrados e inutilizables, pero no se quitan.|Se quitan los datos de la aplicación. La aplicación no se elimina. Los datos protegidos mediante el cifrado MAM fuera de la aplicación (por ejemplo, las tarjetas SD) permanecen cifrados, pero no se quitan.|
|Aplicaciones de línea de negocio administradas|Se quitan los datos de la aplicación. La aplicación no se elimina. Los datos protegidos mediante el cifrado MAM fuera de la aplicación (por ejemplo, las tarjetas SD) permanecen cifrados e inutilizables, pero no se quitan.|Se quitan los datos de la aplicación. La aplicación no se elimina. Los datos protegidos mediante el cifrado MAM fuera de la aplicación (por ejemplo, las tarjetas SD) permanecen cifrados e inutilizables, pero no se quitan.|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado.|Quitado.|
|Configuración de perfil de certificado|Los certificados se revocan, pero no se quitan.|Certificados eliminados y revocados.|
|Agente de administración|Se revocarán los privilegios del administrador de dispositivos.|Se revocarán los privilegios del administrador de dispositivos.|
|Correo electrónico|N/D (los dispositivos Android no admiten los perfiles de correo electrónico)|Se borran los perfiles de correo electrónico que se aprovisionan mediante Intune. Se elimina el correo electrónico almacenado en caché en el dispositivo.|
|Outlook|Se quita el correo electrónico recibido por la aplicación Outlook para Android, pero solo si Outlook está protegido con directivas MAM. De lo contrario, no se borra Outlook cuando se anula la inscripción del dispositivo.|Se quita el correo electrónico recibido por la aplicación Outlook para Android, pero solo si Outlook está protegido con directivas MAM. De lo contrario, no se borra Outlook cuando se anula la inscripción del dispositivo.|
|Separación de Azure AD|Se quita el registro de Azure AD.|Se quita el registro de Azure AD.|
|Contactos |Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa. No se pueden quitar los contactos sincronizados desde la libreta de direcciones nativa a otro origen externo. <br /> <br />En este momento solo se admite la aplicación Outlook.|Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa. No se pueden quitar los contactos sincronizados desde la libreta de direcciones nativa a otro origen externo. <br /> <br />En este momento solo se admite la aplicación Outlook.

### <a name="android-work-profile"></a>Perfil de trabajo Android

Al eliminar los datos de la compañía de un dispositivo de perfil de trabajo Android, se eliminan todos los datos, las aplicaciones y las configuraciones del perfil de trabajo en dicho dispositivo. El dispositivo se retira de la administración con Intune. No se admite el borrado en los perfiles de trabajo Android.

### <a name="android-enterprise-kiosk-devices"></a>Dispositivos de quiosco de Android Enterprise

Solo se pueden borrar dispositivos de quiosco. Los dispositivos de quiosco de Android no se pueden retirar.


### <a name="macos"></a>macOS

|Tipo de datos|macOS|
|-------------|-------|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado.|
|Configuración de perfil de certificado|Se han eliminado y revocado los certificados implementados a través de MDM.|
|Agente de administración|Se quitará el perfil de administración.|
|Outlook|Si el acceso condicional está habilitado, el dispositivo no recibirá ningún correo nuevo.|
|Separación de Azure AD|Se quita el registro de Azure AD.|

### <a name="windows"></a>Windows

|Tipo de datos|Windows 8.1 (MDM) y Windows RT 8.1|Windows RT|Windows Phone 8.1 y Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Aplicaciones de empresa y datos asociados instalados por Intune.|Se revocan las claves de los archivos protegidos con EFS. El usuario no puede abrir los archivos.|No se quitan las aplicaciones de empresa.|Se desinstalan las aplicaciones instaladas originalmente a través del Portal de empresa. Se quitarán los datos de la aplicación de empresa.|Las aplicaciones se desinstalarán. Se quitan las claves de instalación de prueba.<br>Para Windows 10 versión 1703 (Creator Update) y versiones posteriores, no se quitan las aplicaciones de Office 365 ProPlus.|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado.|Quitado.|No compatible.|Quitado.|
|Configuración de perfil de certificado|Certificados eliminados y revocados.|Certificados eliminados y revocados.|No compatible.|Certificados eliminados y revocados.|
|Correo electrónico|Quita el correo electrónico habilitado para EFS. Se incluyen los mensajes de correo electrónico y los datos adjuntos de la aplicación de correo para Windows.|No compatible.|Se borran los perfiles de correo electrónico que se aprovisionan mediante Intune. Se elimina el correo electrónico almacenado en caché en el dispositivo.|Quita el correo electrónico habilitado para EFS. Se incluyen los mensajes de correo electrónico y los datos adjuntos de la aplicación de correo para Windows. Se quitan las cuentas de correo aprovisionadas por Intune.|
|Separación de Azure AD|No.|No.|Se quita el registro de Azure AD.|No aplicable. En Windows 10, no se pueden retirar los dispositivos unidos a Azure AD.|

### <a name="retire"></a>Retirar

1. Inicie sesión en [Intune en Azure Portal](https://aka.ms/intuneportal).
2. En el panel **Dispositivos**, seleccione **Todos los dispositivos**.
3. Seleccione el nombre del dispositivo que quiere retirar.
4. En el panel en el que se muestra el nombre del dispositivo, haga clic en **Retirar**. Para confirmar, seleccione **Sí**.

Si el dispositivo está encendido y conectado, la acción **Retirar** se propaga por todos los tipos de dispositivos en menos de 15 minutos.

## <a name="delete-devices-from-the-intune-portal"></a>Eliminación de dispositivos del portal de Intune

Si quiere quitar dispositivos del portal de Intune, puede eliminarlos desde el panel de dispositivos específico. La próxima vez que el dispositivo se registra, se quitan los datos de la compañía que contiene.

1. Inicie sesión en [Intune en Azure Portal](https://aka.ms/intuneportal).
2. Elija **Dispositivos** > **Todos los dispositivos** > elija los dispositivos que quiere eliminar > **Eliminar**.

### <a name="automatically-delete-devices-with-cleanup-rules"></a>Eliminar dispositivos automáticamente con reglas de limpieza
Puede configurar Intune para eliminar automáticamente los dispositivos que parecen estar inactivos, obsoletos o que no responden. Estas reglas de limpieza supervisan constantemente el inventario de dispositivos para que los registros de dispositivos se mantengan al día. Los dispositivos eliminados de esta forma se quitan de la administración de Intune.
1. Inicie sesión en [Intune en Azure Portal](https://aka.ms/intuneportal).
2. Elija **Dispositivos** > **Reglas de limpieza de dispositivos** > **Sí**.
3. En el cuadro **Delete devices that haven’t checked in for this many days** (Eliminar dispositivos que no se han protegido durante este número de días), escriba un número entre 90 y 270.
4. Elija **Guardar**.



## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Eliminación de dispositivos en el portal de Azure Active Directory

Es posible que deba eliminar dispositivos de Azure AD si se producen problemas de comunicación o si faltan dispositivos. Puede usar la acción **Eliminar** para quitar registros de dispositivo de Azure Portal de los dispositivos que sabe que son inaccesibles y que es poco probable que vuelvan a comunicarse con Azure. La acción **Eliminar** no quita ningún dispositivo de la administración.

1.  Inicie sesión en [Azure Active Directory en Azure Portal](http://aka.ms/accessaad) con sus credenciales de administrador. También puede iniciar sesión en el [portal de Office 365](https://portal.office.com). En el menú, seleccione **Centros de administración** > **Azure AD**.
2.  Si no tiene ninguna, cree una suscripción de Azure. Si tiene una cuenta de pago, no necesitará ninguna tarjeta de crédito ni deberá efectuar ningún pago (seleccione el vínculo de suscripción **Registre su suscripción gratuita de Azure Active Directory**).
3.  Seleccione **Azure Active Directory** y, después, seleccione su organización.
4.  Seleccione la pestaña **Usuarios** .
5. Seleccione el usuario que está asociado al dispositivo que quiere eliminar.
6.  Seleccione **Dispositivos**.
7.  Quite los dispositivos según corresponda. Por ejemplo, puede quitar los dispositivos que ya no están en uso o los dispositivos que tienen definiciones inexactas.

## <a name="retire-an-apple-dep-device-from-intune"></a>Retirar un dispositivo DEP de Apple de Intune

Si quiere quitar completamente un dispositivo DEP de Apple de la administración mediante Intune, siga estos pasos:

1. Inicie sesión en [Intune en Azure Portal](https://aka.ms/intuneportal).
2. Elija **Dispositivos** > **Todos los dispositivos** > elija el dispositivo > **Retirar**.
![Captura de pantalla de Retirar](./media/devices-wipe/retire.png)
3. Elija **Inscripción de dispositivos** > **Inscripción de Apple** > **Tokens del programa de inscripción** > elija el token > **Dispositivos** > active la casilla del dispositivo > **Eliminar** > **Sí**.
![Captura de pantalla de eliminación de dispositivo](./media/devices-wipe/delete-device.png)
4. Visite [deploy.apple.com](http://deploy.apple.com) y busque el dispositivo por su número de serie.
5. En el menú **Asignado a**, elija **Sin asignar**.

6. Elija **Reasignar**.

    ![Captura de pantalla de reasignación de Apple](./media/devices-wipe/apple-reassign.png)

## <a name="next-steps"></a>Pasos siguientes

Si quiere volver a inscribir un dispositivo eliminado, vea [Opciones de inscripción](enrollment-options.md).

