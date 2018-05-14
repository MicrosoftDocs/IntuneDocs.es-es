---
title: Eliminación de datos de la empresa de los dispositivos mediante Microsoft Intune - Azure | Microsoft Docs
description: Quite los datos de la empresa de un dispositivo o efectúe un restablecimiento de fábrica en un dispositivo Android, Android for Work, iOS, Mac OS o Windows con Microsoft Intune. Elimine también un dispositivo de Azure Active Directory.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f7d3e768e740866d69d675a962dfca6d98c85568
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="remove-devices-by-using-factory-reset-or-remove-company-data"></a>Eliminación de dispositivos mediante el restablecimiento de fábrica o de los datos de la compañía

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Puede eliminar de Intune los dispositivos que ya no son necesarios, que se van a reutilizar o que han desaparecido. Para ello, use las acciones **Eliminar datos de la compañía** o **Restablecimiento de fábrica**. Los usuarios también pueden emitir un comando remoto desde el Portal de empresa de Intune para los dispositivos de propiedad privada que están inscritos en Intune.

> [!NOTE]
> Antes de eliminar un usuario de Azure Active Directory (Azure AD), use la acción **Restablecimiento de fábrica** o **Eliminar datos de la compañía** para todos los dispositivos asociados a ese usuario. Si elimina usuarios que tienen dispositivos administrados desde Azure AD, Intune ya no podrá emitir ningún restablecimiento de fábrica ni eliminar los datos de la compañía de esos dispositivos.

## <a name="factory-reset"></a>Restablecimiento de fábrica

La acción **Restablecimiento de fábrica** restaura un dispositivo a su configuración de fábrica predeterminada. El restablecimiento de fábrica restablece todos los datos y opciones de configuración de la empresa y del usuario. El dispositivo se quita de la administración de Intune. El restablecimiento de fábrica es útil para restablecer un dispositivo antes de dárselo a otro usuario o en el caso de que el dispositivo se haya perdido o lo hayan robado. Tenga cuidado al seleccionar el **restablecimiento de fábrica**. Los datos del dispositivo no se pueden recuperar.

### <a name="factory-reset-a-device"></a>Realizar el restablecimiento de fábrica de un dispositivo

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Dispositivos** > **Todos los dispositivos**.
4. Seleccione el nombre del dispositivo al que quiere aplicar el restablecimiento de fábrica.
5. En el panel que muestra el nombre del dispositivo, seleccione **Restablecimiento de fábrica**.
6. Para Windows 10 versión 1709 y versiones posteriores, también tiene la opción **Conservar el estado de inscripción y la cuenta de usuario**. 
    
    |Conservado durante un restablecimiento de fábrica|No se conserva|
    | -------------|------------|
    |Cuentas de usuario asociadas con el dispositivo|Archivos de usuario|
    |Estado del equipo \(unión a un dominio, unido a Azure AD)| Aplicaciones instaladas por el usuario \(tienda y aplicaciones de Win32)|
    |Inscripción de la Administración de dispositivos móviles (MDM)|Configuración del dispositivo no predeterminada|
    |Aplicaciones instaladas por OEM \(tienda y aplicaciones de Win32)||
    |Perfil de usuario||
    |Datos de usuario que se encuentran fuera del perfil de usuario||
    |Inicio de sesión automático del usuario|| 
    
         
7. Para confirmar el restablecimiento de fábrica, seleccione **Sí**.

Si el dispositivo está encendido y conectado, la acción **Restablecimiento de fábrica** se propaga por todos los tipos de dispositivos en menos de 15 minutos.

## <a name="remove-company-data"></a>Eliminar datos de la compañía

La acción **Eliminar datos de la compañía** elimina los datos de las aplicaciones administradas (si procede), la configuración y los perfiles de correo electrónico asignados con Intune. El dispositivo se quita de la administración de Intune. Esto sucede la próxima vez que el dispositivo se registra y recibe la acción remota para **eliminar datos de la compañía**.

La acción **Eliminar datos de la compañía** deja los datos personales del usuario en el dispositivo.  

En las tablas siguientes se describen los datos que se eliminan y el efecto de la acción **Eliminar datos de la compañía** en los datos que permanecen en el dispositivo después de eliminar los datos de la compañía.

### <a name="ios"></a>iOS

|Tipo de datos|iOS|
|-------------|-------|
|Aplicaciones de empresa y datos asociados instalados por Intune.|Las aplicaciones se desinstalarán. Se quitarán los datos de la aplicación de empresa.<br /><br />Se eliminan los datos de las aplicaciones de Microsoft que usan la administración de aplicaciones móviles. La aplicación no se elimina.|
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

### <a name="android-for-work"></a>Android for Work

Al eliminar los datos de la compañía de un dispositivo de Android for Work, se eliminan todos los datos, las aplicaciones y las configuraciones del perfil de trabajo en dicho dispositivo. El dispositivo se retira de la administración con Intune. No se admite el restablecimiento de fábrica en Android for Work.


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

|Tipo de datos|Windows 8.1 (MDM) y Windows RT 8.1|Windows RT|Windows Phone 8.1 y Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Aplicaciones de empresa y datos asociados instalados por Intune.|Se revocan las claves de los archivos protegidos con EFS. El usuario no puede abrir los archivos.|No se quitan las aplicaciones de empresa.|Se desinstalan las aplicaciones instaladas originalmente a través del Portal de empresa. Se quitarán los datos de la aplicación de empresa.|Las aplicaciones se desinstalarán. Se quitan las claves de instalación de prueba.<br>Para Windows 10 versión 1703 (Creator Update) y versiones posteriores, no se quitan las aplicaciones de Office 365 ProPlus.|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado.|Quitado.|No compatible.|Quitado.|
|Configuración de perfil de certificado|Certificados eliminados y revocados.|Certificados eliminados y revocados.|No compatible.|Certificados eliminados y revocados.|
|Correo electrónico|Quita el correo electrónico habilitado para EFS. Se incluyen los mensajes de correo electrónico y los datos adjuntos de la aplicación de correo para Windows.|No compatible.|Se borran los perfiles de correo electrónico que se aprovisionan mediante Intune. Se elimina el correo electrónico almacenado en caché en el dispositivo.|Quita el correo electrónico habilitado para EFS. Se incluyen los mensajes de correo electrónico y los datos adjuntos de la aplicación de correo para Windows. Se quitan las cuentas de correo aprovisionadas por Intune.|
|Separación de Azure AD|No.|No.|Se quita el registro de Azure AD.|No aplicable. En Windows 10 no puede quitar los datos de la compañía de dispositivos unidos a Azure AD.|

### <a name="remove-company-data"></a>Eliminar datos de la compañía

1. Inicie sesión en [Intune en Azure Portal](https://aka.ms/intuneportal).
2. En el panel **Dispositivos**, seleccione **Todos los dispositivos**.
3. Seleccione el nombre del dispositivo del que quiere quitar los datos de la empresa.
4. En el panel que muestra el nombre del dispositivo, seleccione **Eliminar datos de la compañía**. Para confirmar, seleccione **Sí**.

Si el dispositivo está encendido y conectado, la acción **Eliminar datos de la compañía** se propaga por todos los tipos de dispositivos en menos de 15 minutos.

## <a name="delete-devices-from-the-intune-portal"></a>Eliminación de dispositivos del portal de Intune

Si quiere quitar dispositivos del portal de Intune, puede eliminarlos desde el panel de dispositivos específico. La próxima vez que el dispositivo se registra, se quitan los datos de la compañía que contiene.

1. Inicie sesión en [Intune en Azure Portal](https://aka.ms/intuneportal).
2. Elija **Dispositivos** > **Todos los dispositivos** > elija los dispositivos que quiere eliminar > **Eliminar**.

## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Eliminación de dispositivos en el portal de Azure Active Directory

Es posible que deba eliminar dispositivos de Azure AD si se producen problemas de comunicación o si faltan dispositivos. Puede usar la acción **Eliminar** para quitar registros de dispositivo de Azure Portal de los dispositivos que sabe que son inaccesibles y que es poco probable que vuelvan a comunicarse con Azure. La acción **Eliminar** no quita ningún dispositivo de la administración.

1.  Inicie sesión en [Azure Active Directory en Azure Portal](http://aka.ms/accessaad) con sus credenciales de administrador. También puede iniciar sesión en el [portal de Office 365](https://portal.office.com). En el menú, seleccione **Centros de administración** > **Azure AD**.
2.  Si no tiene ninguna, cree una suscripción de Azure. Si tiene una cuenta de pago, no necesitará ninguna tarjeta de crédito ni deberá efectuar ningún pago (seleccione el vínculo de suscripción **Registre su suscripción gratuita de Azure Active Directory**).
3.  Seleccione **Azure Active Directory** y, después, seleccione su organización.
4.  Seleccione la pestaña **Usuarios** .
5. Seleccione el usuario que está asociado al dispositivo que quiere eliminar.
6.  Seleccione **Dispositivos**.
7.  Quite los dispositivos según corresponda. Por ejemplo, puede quitar los dispositivos que ya no están en uso o los dispositivos que tienen definiciones inexactas.
