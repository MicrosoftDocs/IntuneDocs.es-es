---
title: Usar el borrado remoto para ayudar a proteger los datos | Microsoft Intune
description: Intune ofrece capacidades de borrado completo y selectivo para quitar los datos corporativos confidenciales y el acceso a muchos recursos corporativos.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8519e411-3d48-44eb-9b41-3e4fd6a93112
ms.reviewer: lancecra
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: c61fd1070f84f359ac6abe9ff48e51d2787c4eb4


---

# Ayudar a proteger los datos con el borrado selectivo o completo mediante Microsoft Intune
Al igual que con los dispositivos, en algún momento, quiere o necesita [quitar aplicaciones](retire-apps-using-microsoft-intune.md) que ha implementado en equipos y dispositivos móviles porque ya no los necesita. También es posible que quiera quitar datos de la empresa del dispositivo. Para hacer esto, Intune proporciona funcionalidades de borrado completo y de borrado selectivo. Dado que los dispositivos móviles pueden almacenar datos corporativos confidenciales y proporcionar acceso a muchos recursos corporativos, es posible emitir un comando de borrado remoto de dispositivos desde Intune para borrar un dispositivo perdido o robado. Además, los usuarios pueden emitir un comando de borrado remoto de dispositivos desde Intune en dispositivos de propiedad privada inscritos en Intune.

  > [!NOTE]
  > En este tema se trata únicamente la eliminación de dispositivos administrados por Intune. También puede usar [el Portal de vista previa de Azure](https://portal.azure.com) para [borrar datos corporativos de las aplicaciones](wipe-managed-company-app-data-with-microsoft-intune.md).

## Borrar todos los datos


La opción **Borrar todos los datos** restaura la configuración predeterminada de fábrica del dispositivo y quita todos los datos y parámetros del usuario y la empresa. El dispositivo se quita de Intune. El borrado completo es útil para restablecer un dispositivo antes de proporcionárselo a un nuevo usuario o en caso de que el dispositivo se haya perdido o robado.  **Tenga cuidado al seleccionar el borrado completo. Los datos del dispositivo no se pueden recuperar**.

> [!Warning]
> Los dispositivos Windows 10 RTM (es decir, los dispositivos anteriores a la versión 1511 de Windows 10) con menos de 4 GB de RAM podrían dejar de estar accesibles si se borran. Para acceder a un dispositivo Windows 10 que ha dejado de responder, puede arrancarlo desde una unidad USB o puede llevar a cabo una solución alternativa similar.

## La eliminación de datos selectiva

El **borrado selectivo** quita los datos de la empresa incluidos los datos de administración de aplicaciones móviles (MAM) si procede, las configuraciones y los perfiles de correo electrónico de un dispositivo. El borrado selectivo deja los datos personales del usuario en el dispositivo. El dispositivo se quita de Intune. Las tablas siguientes describen para cada plataforma los datos que se eliminan y el efecto en los datos que permanecen en el dispositivo después de una eliminación selectiva.

**iOS**

|Tipo de datos|iOS|
|-------------|-------|
|Aplicaciones de empresa y datos asociados instalados por Intune.|Las aplicaciones se desinstalarán. Se quitarán los datos de la aplicación de empresa.<br /><br />Se eliminan los datos de las aplicaciones de Microsoft que usan la administración de aplicaciones móviles. La aplicación no se elimina.|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado|
|Configuración de perfil de certificado|Certificados eliminados y revocados.|
|Agente de administración|Se quitará el perfil de administración.|
|Correo electrónico|Los perfiles de correo electrónico que se aprovisionan mediante Intune se quitan y el correo electrónico almacenado en caché en el dispositivo se elimina.|
|Separación de Azure Active Directory (AAD)|Registro de AAD eliminado|
|Contactos | Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa.  No se pueden borrar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. <br /> <br />Actualmente, se admite solo la aplicación Outlook.

**Android**

|Tipo de datos|Android|Android Samsung KNOX|
|-------------|-----------|------------------------|
|Vínculos web|Quitado.|Quitado|
|Aplicaciones no administradas de Google Play|Se mantendrán instalados los datos y las aplicaciones.|Se mantendrán instalados los datos y las aplicaciones.|
|Línea de aplicaciones empresariales no administradas|Se mantendrán instalados los datos y las aplicaciones.|Las aplicaciones se desinstalan y, como consecuencia, se quitan los datos locales de la aplicación. No se quita ningún datos fuera de la aplicación (tarjeta SD, etc.).|
|Aplicaciones administradas de Google Play|Se quitan los datos de la aplicación. La aplicación no se quita. Los datos protegidos por cifrado MAM fuera de la aplicación (tarjeta SD, etc.) permanecen cifrados e inutilizables, pero no se quitan.|Se quitan los datos de la aplicación. La aplicación no se quita. Los datos protegidos por cifrado MAM fuera de la aplicación (tarjeta SD, etc.) permanecen cifrados, pero no se quitan.|
|Línea administrada de aplicaciones empresariales|Se quitan los datos de la aplicación. La aplicación no se quita. Los datos protegidos por cifrado MAM fuera de la aplicación (tarjeta SD, etc.) permanecen cifrados e inutilizables, pero no se quitan.|Se quitan los datos de la aplicación. La aplicación no se quita. Los datos protegidos por cifrado MAM fuera de la aplicación (tarjeta SD, etc.) permanecen cifrados e inutilizables, pero no se quitan.|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado|Quitado|
|Configuración de perfil de certificado|Certificados revocados, pero no eliminados.|Certificados eliminados y revocados.|
|Agente de administración|Se revocarán los privilegios del administrador de dispositivos.|Se revocarán los privilegios del administrador de dispositivos.|
|Correo electrónico|Se quita el correo electrónico recibido en la aplicación de Microsoft Outlook para Android.|Los perfiles de correo electrónico que se aprovisionan mediante Intune se quitan y el correo electrónico almacenado en caché en el dispositivo se elimina.|
|Separación de Azure Active Directory (AAD)|Registro de AAD eliminado|Registro de AAD eliminado|
|Contactos | Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa.  No se pueden borrar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. <br /> <br />Actualmente, se admite solo la aplicación Outlook.|Se quitan los contactos sincronizados directamente desde la aplicación en la libreta de direcciones nativa.  No se pueden borrar los contactos sincronizados desde la libreta de direcciones nativa en otro origen externo. <br /> <br />Actualmente, se admite solo la aplicación Outlook.

**Windows**

|Tipo de datos|Windows 8.1 (MDM) y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Aplicaciones de empresa y datos asociados instalados por Intune.|Los archivos protegidos por EFS tendrán su clave revocada y el usuario no podrá abrir los archivos.|No se quitarán las aplicaciones de empresa.|Se desinstalarán las aplicaciones instaladas originalmente a través del portal de empresa. Se quitarán los datos de la aplicación de empresa.|Se desinstalan las aplicaciones y se quitan las claves de instalación de prueba.|
|Configuración|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|Las configuraciones que estableció la directiva de Intune ya no se aplican y los usuarios pueden cambiar la configuración.|
|Configuración de perfil de Wi-Fi y VPN|Quitado|Quitado|No compatible|Quitado|
|Configuración de perfil de certificado|Certificados eliminados y revocados.|Certificados eliminados y revocados.|No compatible|Certificados eliminados y revocados.|
|Correo electrónico|Quita el correo electrónico habilitado para EFS que incluye la aplicación de correo electrónico y datos adjuntos de Windows.|No compatible|Los perfiles de correo electrónico que se aprovisionan mediante Intune se quitan y el correo electrónico almacenado en caché en el dispositivo se elimina.|Quita el correo electrónico habilitado para EFS que incluye la aplicación de correo electrónico y datos adjuntos de Windows. Se quitan las cuentas de correo aprovisionadas por Intune.|
|Separación de Azure Active Directory (AAD)|No|No|Registro de AAD eliminado|No aplicable. Windows 10 no admite el borrado selectivo en los dispositivos unidos a Azure Active Directory|

### Cómo borrar de forma remota un dispositivo desde la consola de administrador de Intune

1.  Seleccione los dispositivos que se borrarán. Puede encontrarlos por usuario o por dispositivo.

    -   **Por usuario:**

        1.  En la [consola de administrador de Intune](https://manage.microsoft.com/), elija **Grupos** &gt; **Todos los usuarios**.

        2.  Elija el nombre del usuario cuyo dispositivo móvil quiere borrar. Elija **Ver propiedades**.

        3.  En la página **Propiedades** del usuario, elija **Dispositivos** y luego elija el nombre del dispositivo móvil que quiere borrar. Utilice Ctrl + clic para seleccionar varios dispositivos.

    -   **Por dispositivo:**

        1.  En la [consola de administrador de Intune](https://manage.microsoft.com/), elija **Grupos** &gt; **Todos los dispositivos móviles**.

      ![Iniciar una operación de borrado o retirada](../media/dev-sa-wipe.png)

        2.  Elija **Dispositivos** y después elija el nombre del dispositivo móvil que quiere borrar. Utilice Ctrl + clic para seleccionar varios dispositivos.

2.  Elija **Retirar/Eliminar datos**.

3.  Aparecerá un mensaje que le pedirá que confirme que desea retirar el equipo.

    -   Para realizar un **Borrado selectivo** que solo quite las aplicaciones y los datos de la empresa, elija **Sí**.

    -   Para realizar un **Borrado completo** que borre todas las aplicaciones y datos y restablezca la configuración predeterminada de fábrica del dispositivo, seleccione **Eliminar datos del dispositivo antes de retirarlo**. Esta acción se aplica a todas las plataformas excepto Windows 8.1. **No se pueden recuperar los datos quitados mediante un borrado completo**.

Se tarda menos de 15 minutos para que una eliminación de datos se propague a través de todos los tipos de dispositivos.

## Borrar el contenido habilitado para el sistema de archivos de cifrado (EFS)
El borrado selectivo de contenido cifrado de EFS es compatible con Windows 8.1 y Windows RT 8.1. La información siguiente es aplicable a un borrado selectivo de contenido habilitado para EFS:

-   Solo se borran de forma selectiva las aplicaciones y los datos protegidos por EFS que usen el mismo dominio de Internet que la cuenta de Intune. Para obtener más información, consulte [Borrado selectivo de Windows para la administración de datos del dispositivo](http://technet.microsoft.com/library/dn486874.aspx).

-   Si se producen cambios en el dominio asociado con EFS, esos cambios pueden tardar hasta 48 horas antes de que las aplicaciones y los datos que usen el nuevo dominio se puedan borrar de forma selectiva.

-   Todos los dominios registrados con Intune se borrarán.

Los datos y las aplicaciones que son compatibles actualmente con el borrado selectivo de EFS son:

-   Aplicación de correo para Windows

-   Carpetas de trabajo

-   Archivos y carpetas cifrados con EFS. Para obtener más información, consulte [Procedimientos recomendados para el Sistema de archivos de cifrado](http://support.microsoft.com/kb/223316).

-   Si su organización mantiene su identidad en Active Directory, debe utilizar la herramienta de sincronización de directorios (DirSync) para sincronizar la información en AAD para que la eliminación selectiva de EFS funcione correctamente.  Para obtener más información sobre DirSync, consulte el [escenario de sincronización de directorios](http://technet.microsoft.com/library/dn441212.aspx) en la documentación de Azure Active Directory.

## Supervisar acciones de retirada, borrado y eliminación
Para obtener un informe de los dispositivos que se han retirado, borrado o eliminado, y saber quién realizó la acción:

1.  En la [consola de administrador de Intune](https://manage.microsoft.com/), elija **Informes** &gt; **Informes de historial de dispositivos**.

2.  Proporcione las fechas de inicio y finalización del informe y después elija **Ver informe**.


### Consulte también
[Retirar dispositivos](retire-devices-from-microsoft-intune-management.md)

[Windows Selective Wipe for Device Data Management (Eliminación selectiva de Windows para administración de datos de dispositivos)](http://technet.microsoft.com/library/dn486874.aspx)



<!--HONumber=Jul16_HO4-->


