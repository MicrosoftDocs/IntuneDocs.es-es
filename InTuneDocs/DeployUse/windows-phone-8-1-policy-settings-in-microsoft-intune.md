---
# required metadata

title: Configuración de directivas de Windows 8.1 en Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 83f7469c-272e-43f2-8139-b0d7bc34f43f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configuración de directivas de Windows 8.1 en Microsoft Intune

## Opciones generales de configuración

Use la **directiva de configuración general de Windows Phone** de Microsoft Intune para configurar las opciones siguientes para dispositivos con Windows Phone 8.1:

-   **Configuración de seguridad de dispositivos móviles** : elija entre una lista de configuraciones predefinidas que permiten controlar una variedad de características y la funcionalidad en el dispositivo.

-   **Aplicaciones compatibles y no compatibles**: especifique una lista de las aplicaciones compatibles y no compatibles de su empresa. Los dispositivos de Windows Phone pueden bloquear o permitir la instalación de estas aplicaciones.

### Configuración de contraseña

|Nombre de la configuración|Detalles|Windows Phone 8|Windows Phone 8,1|
|----------------|-----------------------------------------|
|**Requerir una contraseña para desbloquear dispositivos móviles**|Especifica si los usuarios deben escribir una contraseña para obtener acceso a los dispositivos.|Sí|Sí|
|**Tipo de contraseña obligatoria**|Especifica el tipo de contraseña que será necesario, como solo numérica o alfanumérica.|Sí|Sí|
|**Tipo de contraseña requerida: número mínimo de conjuntos de caracteres**|Hay cuatro conjuntos de caracteres: letras minúsculas, letras mayúsculas, símbolos y números. Esta configuración especifica cuántos conjuntos de caracteres diferentes deben incluirse en la contraseña. Sin embargo, para dispositivos iOS, especifica el número de caracteres de símbolos que deben incluirse en la contraseña.|Sí|Sí|
|**Longitud mínima de la contraseña**|Especifica el número mínimo de caracteres necesarios en la contraseña.|Sí|Sí|
|**Permitir contraseñas sencillas**|Contraseñas sencillas serían, por ejemplo, "0000" y "1234".|Sí|Sí|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Especifica el número de veces que se puede recordar una contraseña incorrecta antes de que se borre el dispositivo.|Sí|Sí|
|**Minutos de inactividad antes de que se apague la pantalla**|Especifica la cantidad de tiempo que un dispositivo debe permanecer inactivo antes de que se bloquee automáticamente la pantalla.|Sí|Sí|
|**Caducidad de contraseña (días)**|Especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.|Sí|Sí|
|**Recordar el historial de contraseñas**|Especifica si se recuerdan las contraseñas usadas anteriormente para impedir que el usuario vuelva a usarlas.|Sí|Sí|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Especifica cuántas contraseñas usadas anteriormente se recuerdan.|Sí|Sí|

### Configuración de cifrado

|Nombre de la configuración|Detalles|Windows Phone 8|Windows Phone 8,1|
|----------------|-----------------------------------------|
|**Requerir cifrado en dispositivo móvil**|Requiere que se cifren los datos en los dispositivos móviles compatibles.<br>Para dispositivos de Windows Phone 8, debe establecerse en **Sí**..|Sí|Sí|

### Configuración del sistema

|Nombre de la configuración|Detalles|Windows Phone 8|Windows Phone 8,1|
|----------------|-----------------------------------------|
|**Permitir captura de pantalla**|Permite al usuario capturar el contenido de la pantalla como un archivo de imagen.|No|Sí|
|**Permitir el envío de datos de diagnóstico**|Permite que el dispositivo envíe información de diagnóstico a Microsoft.|No|Sí|

### Configuración de nube: cuentas y sincronización

|Nombre de la configuración|Detalles|Windows Phone 8|Windows Phone 8,1|
|----------------|-----------------------------------------|
|**Permitir cuenta de Microsoft**|Permite vincular una cuenta de Microsoft al dispositivo.|No|Sí|

### Configuración de correo electrónico

|Nombre de la configuración|Detalles|Windows Phone 8|Windows Phone 8,1|
|----------------|-----------------------------------------|
|**Permitir cuentas de correo electrónico personalizadas**|Permite que el dispositivo se conecte a cuentas de correo electrónico que no son de Microsoft.|No|Sí|

### Configuración de la aplicación: explorador

|Nombre de la configuración|Detalles|Windows Phone 8|Windows Phone 8,1|
|----------------|-----------------------------------------|
|**Permitir explorador web**|Permite o bloquea el explorador web integrado en los dispositivos.|No|Sí|

### Configuración de la aplicación: aplicaciones

|Nombre de la configuración|Detalles|Windows Phone 8|Windows Phone 8,1|
|----------------|-----------------------------------------|
|**Permitir almacén de aplicaciones**|Permite a los usuarios conectarse a la tienda de aplicaciones desde el dispositivo.|No|Sí|

### Configuración de funcionalidades del dispositivo: hardware

|Nombre de la configuración|Detalles|Windows Phone 8|Windows Phone 8,1|
|----------------|-----------------------------------------|
|**Permitir cámara**|Permite o bloquea la cámara del dispositivo.|No|Sí|
|**Permitir almacenamiento extraíble**|Permite que el dispositivo use un almacenamiento extraíble, como una tarjeta SD.|Sí|Sí|
|**Permitir Wi-Fi**|Habilita o deshabilita la funcionalidad de Wi-Fi del dispositivo.|No|Sí|
|**Permitir Wi-Fi Tethering**|Permite usar tethering Wi-Fi en el dispositivo.|No|Sí
|**Permitir la conexión automática a zonas Wi-Fi gratuitas**|Permite que el dispositivo se conecte automáticamente a zonas Wi-Fi gratuitas y acepte automáticamente los términos de uso.|No|Sí|
|**Permitir informar de zonas Wi-Fi**|Envía información sobre las conexiones Wi-Fi para ayudar a detectar conexiones cercanas.|No|Sí|
|**Permitir geolocalización**|Permite que el dispositivo use información de ubicación.|No|Sí|
|**Permitir NFC**|Permite las operaciones que usan la transmisión de datos en proximidad.|No|Sí|
|**Permitir Bluetooth**|Habilita o deshabilita la funcionalidad de Bluetooth del dispositivo.|No|Sí|

### Configuración de funcionalidades del dispositivo: características

|Nombre de la configuración|Detalles|Windows Phone 8|Windows Phone 8,1|
|----------------|-----------------------------------------|
|**Permitir copiar y pegar**|Permite la función de copiar y pegar en los dispositivos.|No|Sí|

### Configuración de aplicaciones conformes y no conformes
En la lista de **aplicaciones compatibles &amp; no compatibles**, especifique las aplicaciones que son compatibles y no compatibles con la siguiente información:

> [!NOTE]
> Una única directiva solo puede contener una lista de aplicaciones conformes o una lista de aplicaciones no conformes. No se pueden especificar ambas en la misma directiva.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Bloquear dispositivos para que no abran las aplicaciones de la lista**|Enumera las aplicaciones que no se administran mediante Intune y que los usuarios no pueden instalar ni ejecutar.|
|**Permitir que los dispositivos instalen solo las aplicaciones de la lista**|Enumera las aplicaciones que los usuarios pueden instalar. Los usuarios no pueden instalar ninguna otra aplicación. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.|
|**Agregar**|Agrega una aplicación a la lista seleccionada. Especifique un nombre de su elección, opcionalmente el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones. Consulte Cómo especificar las direcciones URL de tiendas de aplicaciones más adelante en este tema para obtener más ayuda.
|**Importar aplicaciones**|Importa la lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. Utilice el formato, nombre de la aplicación, editor, dirección URL de la aplicación en el archivo.|
|**Editar**|Permite editar el nombre, el editor y la dirección URL de la aplicación seleccionada.|
|**Eliminar**|Elimina la aplicación seleccionada de la lista.|
> [!IMPORTANT]
> Si especifica una lista de aplicaciones permitidas para dispositivos de Windows Phone 8.1, debe agregar la aplicación Portal de empresa a esta lista o se bloqueará.


### Información de referencia para las aplicaciones conformes y no conformes

#### Cómo especificar las direcciones URL de tiendas de aplicaciones
Para especificar una dirección URL de la aplicación en la lista de aplicaciones compatibles y no compatibles, utilice el siguiente formato:

Desde la página de [aplicaciones y juegos para Windows Phone](http://www.windowsphone.com/en-us/store/overview) , busque la aplicación que desea usar.

Abra la página de la aplicación y copie la dirección URL en el Portapapeles. Ya puede utilizarla como dirección URL en una la lista de aplicaciones conformes o no conformes.

**Ejemplo:** Busque la aplicación Skype en la Tienda. La dirección URL que use será **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.

## Opciones de configuración de directiva personalizadas 
Use la **Directiva de configuración personalizada de Windows Phone** de Microsoft Intune para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance), que puede usarse para controlar las características de los **dispositivos de Windows Phone 8.1**. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad está destinada a permitirle implementar la configuración de Windows Phone que no se puede configurar con una directiva de configuración general de Intune. Para obtener información sobre las opciones que puede configurar con estas directivas, consulte [Manage settings and features on your devices with Microsoft Intune policies](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) (Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune)..

Para obtener ayuda sobre cómo crear la configuración de OMA-URI para dispositivos Windows Phone, consulte [Windows Phone 8.1 MDM protocol documentation](http://technet.microsoft.com/library/dn499787.aspx) (Documentación del protocolo MDM de Windows Phone 8.1)..

### Configuración general

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Nombre**|Escriba un nombre único para la directiva que le ayude a identificarla en la consola de Intune.|
|**Descripción**|Proporcione una descripción general de la directiva y otra información relevante que le ayude a encontrarla.|

### Configuración de OMA-URI

En la sección **Configuración OMA-URI**, haga clic en **Agregar** para agregar un valor. También puede editar o eliminar un valor existente.

En el cuadro de diálogo **Agregar o editar configuración OMA-URI**, especifique la siguiente información:

|Nombre de la configuración|Detalles|
    |--------|--------------------|
    |**Nombre de la configuración**|Escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.|
    |**Descripción del valor**|Proporcione una descripción que ofrezca una visión general del valor y otra información relevante que le ayude a encontrarlo.|
    |**Tipo de datos**|Seleccione el tipo de fecha en que especificará este valor OMA-URI. Elija de entre las siguientes opciones:<br /><br />-   **String**<br />-   **Cadena (XML)**<br />-   **Fecha y hora**<br />-   **Integer**<br />-   **Punto flotante**<br />-   **Boolean**|
    |**OMA-URI (distingue mayúsculas de minúsculas)**|Especifique el OMA-URI para el que desee suministrar un valor.|
    |**Valor**|Especifique el valor asociado con el OMA-URI especificado anteriormente.|

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


