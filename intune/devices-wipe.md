---
title: "Uso del restablecimiento de fábrica o eliminación de los datos de la compañía de dispositivos con Microsoft Intune"
titlesuffix: 
description: "Obtenga información sobre cómo eliminar datos de la compañía de un dispositivo o cómo realizar un restablecimiento de fábrica en el dispositivo."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b56f7d7bcf576a0b2342c7c5394c08661b6a45fd
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="remove-devices-by-using-factory-reset-or-remove-company-data"></a>Eliminación de dispositivos mediante el restablecimiento de fábrica o de los datos de la compañía

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Puede eliminar de Intune los dispositivos que ya no son necesarios, que se van a reutilizar o que han desaparecido. Para ello, emita un comando **Eliminar datos de la compañía** o **Restablecimiento de fábrica**. Los usuarios también pueden emitir un comando remoto desde el Portal de empresa de Intune para los dispositivos de propiedad privada inscritos en Intune.

> [!NOTE]
> Antes de eliminar un usuario de Azure Active Directory, emita un comando **Restablecimiento de fábrica** o **Eliminar datos de la compañía** a todos los dispositivos asociados a ese usuario. Si elimina usuarios con dispositivos administrados desde Azure Active Directory, Intune ya no podrá emitir el restablecimiento de fábrica o eliminar los datos de la compañía de esos dispositivos.

## <a name="factory-reset"></a>Restablecimiento de fábrica

La opción **Restablecimiento de fábrica** restaura la configuración predeterminada de fábrica del dispositivo y quita todos los datos y parámetros del usuario y la compañía. El dispositivo se quita de la administración de Intune. El restablecimiento de fábrica es útil para restablecer un dispositivo antes de proporcionárselo a un nuevo usuario o en caso de que el dispositivo se haya perdido o lo hayan robado. Tenga cuidado al seleccionar el restablecimiento de fábrica. Los datos del dispositivo no se pueden recuperar.

### <a name="to-factory-reset-a-device"></a>Para realizar el restablecimiento de fábrica de un dispositivo

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la hoja **Dispositivos**, pulse **Todos los dispositivos**.
4. Elija el nombre del dispositivo en el que quiere realizar el restablecimiento de fábrica.
5. En la hoja en la que se muestra el nombre del dispositivo, elija **Restablecimiento de fábrica**.
6. Para Windows 10 versión 1709 o versiones posteriores, hay una opción adicional para "Conservar el estado de inscripción y la cuenta de usuario". 
    
    |Se conserva a través de un restablecimiento de fábrica|No se conserva|
    | -------------|------------|
    |Cuentas de usuario asociadas con el dispositivo|Archivos de usuario|
    |Estado del equipo \(unión a un dominio, unido a Azure Active Directory)| Aplicaciones instaladas por el usuario \(aplicaciones de Win32 y tienda)|
    |Inscripción de MDM|Configuración del dispositivo no predeterminada|
    |Aplicaciones instaladas por OEM \(aplicaciones de Win32 y tienda)||
    |Perfil de usuario||
    |Datos de usuario fuera del perfil de usuario||
    |Inicio de sesión automático del usuario|| 
    
         
7. Haga clic en **Sí** para confirmar el restablecimiento de fábrica.

Si el dispositivo está encendido y conectado, un comando de restablecimiento de fábrica tarda menos de 15 minutos en propagarse por cualquier tipo de dispositivo.

## <a name="remove-company-data"></a>Eliminar datos de la compañía

El comando **Eliminar datos de la compañía** quita los datos de la aplicación administrada (si procede), la configuración y los perfiles de correo electrónico que se han asignado mediante Intune. El comando Eliminar datos de la compañía deja los datos personales del usuario en el dispositivo. El dispositivo se quita de la administración de Intune. En las tablas siguientes se describen los datos que se eliminan y el efecto en los datos que permanecen en el dispositivo después de eliminar los datos de la compañía.

### <a name="ios"></a>iOS

|Tipo de datos|iOS|
|-------------|-------|
|Aplicaciones de empresa y datos asociados instalados por Intune.|Las aplicaciones se desinstalarán. Se quitarán los datos de la aplicación de empresa.<br /><br />Se eliminan los datos de las aplicaciones de Microsoft que usan la administración de aplicaciones móviles. La aplicación no se elimina.|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado.|
|Configuración de perfil de certificado|Certificados eliminados y revocados.|
|Agente de administración|Se quitará el perfil de administración.|
|Correo electrónico|Los perfiles de correo electrónico que se aprovisionan mediante Intune se quitan y el correo electrónico almacenado en caché en el dispositivo se elimina.|
|Outlook|Se quita el correo electrónico recibido en la aplicación de Microsoft Outlook para iOS.|
|Separación de Azure Active Directory (AD)|Se quita el registro de Azure AD.|
|Contactos | Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa.  No se pueden eliminar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. <br /> <br />Actualmente, se admite solo la aplicación Outlook.

### <a name="android"></a>Android

|Tipo de datos|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Vínculos web|Quitado.|Quitado.|
|Aplicaciones no administradas de Google Play|Se mantendrán instalados los datos y las aplicaciones.|Se mantendrán instalados los datos y las aplicaciones.|
|Aplicaciones de línea de negocio no administradas|Se mantendrán instalados los datos y las aplicaciones.|Las aplicaciones se desinstalan y, como consecuencia, se quitan los datos locales de la aplicación. Ningún dato de fuera de la aplicación (por ejemplo, en una tarjeta SD) se quita.|
|Aplicaciones administradas de Google Play|Se quitan los datos de la aplicación. La aplicación no se quita. Los datos protegidos mediante cifrado MAM fuera de la aplicación (por ejemplo, tarjeta SD, etc.) permanecen cifrados e inutilizables, pero no se quitan.|Se quitan los datos de la aplicación. La aplicación no se quita. Los datos protegidos mediante cifrado MAM fuera de la aplicación (por ejemplo, tarjeta SD, etc.) permanecen cifrados, pero no se quitan.|
|Aplicaciones de línea de negocio administradas|Se quitan los datos de la aplicación. La aplicación no se quita. Los datos protegidos mediante cifrado MAM fuera de la aplicación (por ejemplo, tarjeta SD, etc.) permanecen cifrados e inutilizables, pero no se quitan.|Se quitan los datos de la aplicación. La aplicación no se quita. Los datos protegidos mediante cifrado MAM fuera de la aplicación (por ejemplo, tarjeta SD, etc.) permanecen cifrados e inutilizables, pero no se quitan.|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado.|Quitado.|
|Configuración de perfil de certificado|Certificados revocados, pero no eliminados.|Certificados eliminados y revocados.|
|Agente de administración|Se revocarán los privilegios del administrador de dispositivos.|Se revocarán los privilegios del administrador de dispositivos.|
|Correo electrónico|n/a (los dispositivos Android no admiten perfiles de correo electrónico)|Los perfiles de correo electrónico que se aprovisionan mediante Intune se quitan y el correo electrónico almacenado en caché en el dispositivo se elimina.|
|Outlook|Se quita el correo electrónico recibido por la aplicación Microsoft Outlook para Android, pero solo si Outlook está protegido con directivas MAM. De lo contrario, Outlook no se borra en la anulación de la inscripción.|Se quita el correo electrónico recibido por la aplicación Microsoft Outlook para Android, pero solo si Outlook está protegido con directivas MAM. De lo contrario, Outlook no se borra en la anulación de la inscripción.|
|Separación de Azure Active Directory (AD)|Registro de Azure AD eliminado.|Registro de Azure AD eliminado.|
|Contactos | Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa.  No se pueden eliminar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. <br /> <br />Actualmente, se admite solo la aplicación Outlook.|Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa.  No se pueden eliminar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. <br /> <br />Actualmente, se admite solo la aplicación Outlook.

### <a name="android-for-work"></a>Android for Work

Al eliminar los datos de la compañía de un dispositivo de Android for Work, se eliminan todos los datos, las aplicaciones y las configuraciones del perfil de trabajo en dicho dispositivo. Esto retira el dispositivo de la administración con Intune. No se admite el restablecimiento de fábrica en Android for Work.


### <a name="macos"></a>macOS

|Tipo de datos|macOS|
|-------------|-------|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado.|
|Configuración de perfil de certificado|Se han eliminado y revocado los certificados implementados a través de MDM.|
|Agente de administración|Se quitará el perfil de administración.|
|Outlook|Si el acceso condicional está habilitado, el dispositivo no recibirá ningún correo nuevo.|
|Separación de Azure Active Directory (AD)|Se quita el registro de Azure AD.|

### <a name="windows"></a>Windows

|Tipo de datos|Windows 8.1 (MDM) y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Aplicaciones de empresa y datos asociados instalados por Intune.|Los archivos protegidos por EFS tendrán su clave revocada y el usuario no podrá abrir los archivos.|No se quitarán las aplicaciones de empresa.|Se desinstalarán las aplicaciones instaladas originalmente a través del portal de empresa. Se quitarán los datos de la aplicación de empresa.|Se desinstalan las aplicaciones y se quitan las claves de instalación de prueba.<br>Para Windows 10 versión 1703 (Creator Update) y posteriores, no se eliminan las aplicaciones de Office 365 ProPlus.|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado.|Quitado.|No compatible.|Quitado.|
|Configuración de perfil de certificado|Certificados eliminados y revocados.|Certificados eliminados y revocados.|No compatible.|Certificados eliminados y revocados.|
|Correo electrónico|Quita el correo electrónico habilitado para EFS que incluye la aplicación de correo electrónico y datos adjuntos de Windows.|No compatible.|Los perfiles de correo electrónico que se aprovisionan mediante Intune se quitan y el correo electrónico almacenado en caché en el dispositivo se elimina.|Quita el correo electrónico habilitado para EFS que incluye la aplicación de correo electrónico y datos adjuntos de Windows. Se quitan las cuentas de correo aprovisionadas por Intune.|
|Separación de Azure Active Directory (AD)|No.|No.|Registro de Azure AD eliminado.|No aplicable. Windows 10 no admite la eliminación de datos de la compañía en los dispositivos unidos a Azure Active Directory.|

### <a name="to-remove-company-data"></a>Para eliminar los datos de la compañía

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En la hoja **Dispositivos**, pulse **Todos los dispositivos**.
4. Elija el nombre del dispositivo del que quiere eliminar los datos de la compañía.
5. En la hoja que muestra el nombre del dispositivo, elija **Eliminar datos de la compañía** y seleccione **Sí** para confirmar.

Si el dispositivo está encendido y conectado, un comando de eliminación de datos tarda menos de 15 minutos en propagarse por cualquier tipo de dispositivo.

## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Eliminación de dispositivos en el portal de Azure Active Directory

Si se producen problemas de comunicación o faltan dispositivos, es posible que deba eliminar dispositivos de Azure Active Directory (AD). El comando de eliminación no quita un dispositivo de la administración, pero puede usar **Eliminar** para quitar de Azure Portal los registros de dispositivos que sabe que no son accesibles y que es poco probable que vuelvan a comunicarse con Azure.

1.  Inicie sesión en [Azure Active Directory en Azure Portal](http://aka.ms/accessaad) con sus credenciales de administrador. También puede iniciar sesión en el [Portal de Office 365](https://portal.office.com) y, después, elegir **Centros de administración** &gt; **Azure AD** mediante el vínculo situado en el lado izquierdo de la página.
3.  Si no tiene ninguna, cree una suscripción de Azure. Si tiene una cuenta de pago, no necesitará una tarjeta de crédito ni realizar ningún pago (seleccione el vínculo de suscripción **Registre su suscripción gratuita de Azure Active Directory**).
4.  Seleccione **Azure Active Directory** y, después, su organización.
5.  Seleccione la pestaña **Usuarios** .
6.  Seleccione el usuario cuyos dispositivos desea eliminar.
7.  Seleccione **Dispositivos**.
8.  Quite los dispositivos que crea oportunos, como por ejemplo aquellos que ya no estén en uso o que tienen definiciones inexactas.
