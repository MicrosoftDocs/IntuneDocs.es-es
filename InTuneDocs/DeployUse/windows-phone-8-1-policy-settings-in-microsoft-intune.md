---
title: "Configuración de directivas de Windows Phone 8.1 | Microsoft Intune"
description: "Intune proporciona una variedad de opciones generales integradas que puede configurar en los dispositivos Windows Phone 8.1. Además, puede especificar valores OMA-URI para crear una configuración personalizada que no esté disponible en Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 83f7469c-272e-43f2-8139-b0d7bc34f43f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e95db6d0ccbe350984f11ce08749b700c2f5ad01
ms.openlocfilehash: 3c9c75e5e9e19574a5b4525688103dc95e3d6b9b


---

# Configuración de directivas de Windows 8.1 en Microsoft Intune

Intune proporciona una variedad de opciones generales integradas que puede configurar en los dispositivos Windows Phone 8.1. Además, puede especificar valores Open Mobile Alliance Uniform Resource Identifier (OMA-URI, identificador uniforme de recursos de Open Mobile Alliance) para crear una configuración personalizada que no esté disponible en Intune.

## Opciones generales de configuración

Use la **directiva de configuración general de Windows Phone (Windows Phone 8.1 y posterior)** de Microsoft Intune para configurar las opciones siguientes para dispositivos Windows Phone 8.1:

-   **Configuración de seguridad de dispositivos móviles** : elija entre una lista de configuraciones predefinidas que permiten controlar una variedad de características y la funcionalidad en el dispositivo.

-   **Aplicaciones compatibles y no compatibles**: especifique una lista de las aplicaciones compatibles y no compatibles de su compañía. Los dispositivos Windows Phone pueden bloquear o permitir la instalación de estas aplicaciones.

### Configuración de aplicabilidad

|Nombre de la configuración|Detalles|
|----------------|----------------------------------|
|**Aplicar todas las configuraciones a Windows 10**|Permite aplicar la configuración de esta directiva en dispositivos Windows 10 Mobile y en dispositivos Windows Phone 8.1.|

### Configuración de contraseña

|Nombre de la configuración|Detalles|
|----------------|------|
|**Requerir una contraseña para desbloquear dispositivos móviles**|Especifica si los usuarios deben escribir una contraseña para obtener acceso a los dispositivos.|
|**Tipo de contraseña obligatoria**|Especifica el tipo de contraseña que será necesario, como solo numérica o alfanumérica.|
|**Tipo de contraseña requerida: número mínimo de conjuntos de caracteres**|Especifica cuántos juegos de caracteres diferentes deben incluirse en la contraseña. Hay cuatro juegos de caracteres: letras minúsculas, letras mayúsculas, símbolos y números. En cambio, para dispositivos iOS, especifica el número de símbolos que deben incluirse en la contraseña.|
|**Longitud mínima de la contraseña**|Especifica el número mínimo de caracteres que son necesarios en la contraseña.|
|**Permitir contraseñas sencillas**|Especifica que pueden usarse contraseñas sencillas como "0000" y "1234".|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Especifica el número de veces que se puede escribir una contraseña incorrecta antes de que se borre el dispositivo.|
|**Minutos de inactividad antes de que se apague la pantalla.**|Especifica la cantidad de tiempo que un dispositivo debe permanecer inactivo antes de que se bloquee automáticamente la pantalla.|
|**Caducidad de contraseña (días)**|Especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.|Sí|Sí|
|**Recordar el historial de contraseñas**|Especifica si se recuerdan las contraseñas usadas anteriormente para impedir que el usuario vuelva a usarlas.|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Especifica cuántas contraseñas usadas anteriormente se recuerdan.|

### Configuración de cifrado

|Nombre de la configuración|Detalles|
|----------------|------|
|**Requerir cifrado en dispositivo móvil**|Requiere que se cifren los datos en los dispositivos móviles compatibles.|

### Configuración del sistema

|Nombre de la configuración|Detalles|
|----------------|-----|
|**Permitir captura de pantalla**|Permite al usuario capturar el contenido de la pantalla como un archivo de imagen.|
|**Permitir el envío de datos de diagnóstico**|Permite que el dispositivo envíe información de diagnóstico a Microsoft.|

### Configuración de nube: cuentas y sincronización

|Nombre de la configuración|Detalles|
|----------------|------|
|**Permitir cuenta de Microsoft**|Permite vincular una cuenta Microsoft al dispositivo.|

### Configuración de correo electrónico

|Nombre de la configuración|Detalles|
|----------------|-----|
|**Permitir cuentas de correo electrónico personalizadas**|Permite que el dispositivo se conecte a cuentas de correo electrónico que no son de Microsoft.|

### Configuración de la aplicación: explorador

|Nombre de la configuración|Detalles|
|----------------|-----|
|**Permitir explorador web**|Permite o bloquea el explorador web integrado en los dispositivos.|

### Configuración de la aplicación: aplicaciones

|Nombre de la configuración|Detalles|
|----------------|-----|
|**Permitir almacén de aplicaciones**|Permite a los usuarios conectarse a la tienda de aplicaciones desde el dispositivo.|

### Configuración de funcionalidades del dispositivo: hardware

|Nombre de la configuración|Detalles|
|----------------|-----|
|**Permitir cámara**|Permite o bloquea la cámara del dispositivo.|
|**Permitir almacenamiento extraíble**|Permite que el dispositivo use un almacenamiento extraíble, como las tarjetas SD.|
|**Permitir Wi-Fi**|Habilita o deshabilita la funcionalidad de Wi-Fi del dispositivo.|
|**Permitir Wi-Fi Tethering**|Permite el uso de Tethering Wi-Fi en el dispositivo.|
|**Permitir la conexión automática a zonas Wi-Fi gratuitas**|Permite que el dispositivo se conecte automáticamente a zonas Wi-Fi gratuitas y acepte automáticamente las condiciones de uso.|
|**Permitir informar de zonas Wi-Fi**|Envía información sobre las conexiones Wi-Fi para ayudar al usuario a detectar conexiones cercanas.|
|**Permitir geolocalización**|Permite que el dispositivo use información de ubicación.|
|**Permitir NFC**|Permite las operaciones que usan la transmisión de datos en proximidad.|
|**Permitir Bluetooth**|Habilita o deshabilita la funcionalidad de Bluetooth del dispositivo.|

### Configuración de funcionalidades del dispositivo: características

|Nombre de la configuración|Detalles|
|----------------|----|
|**Permitir copiar y pegar**|Permite la funcionalidad de copiar y pegar en los dispositivos.|

### Configuración de aplicaciones permitidas y bloqueadas
En la lista **Aplicaciones permitidas y bloqueadas**, especifique una lista de aplicaciones que quiera permitir o bloquear mediante la siguiente información:

> [!NOTE]
> Una sola directiva únicamente puede contener una lista de aplicaciones permitidas o bloqueadas. No se pueden especificar ambas en la misma directiva.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Bloquear dispositivos para que no abran las aplicaciones de la lista**|Enumera las aplicaciones que no se administran mediante Intune y que los usuarios no pueden instalar ni ejecutar.|
|**Permitir que los dispositivos instalen solo las aplicaciones de la lista**|Enumera las aplicaciones que los usuarios pueden instalar. Los usuarios no pueden instalar ninguna otra aplicación. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.|
|**Agregar**|Agrega una aplicación a la lista seleccionada. Especifique un nombre de su elección, la dirección URL de la aplicación en la tienda de aplicaciones y el publicador de la aplicación (opcional). Consulte Cómo especificar las direcciones URL de tiendas de aplicaciones más adelante en este tema para obtener más ayuda.
|**Importar aplicaciones**|Importa la lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. Utilice el formato, nombre de la aplicación, editor, dirección URL de la aplicación en el archivo.|
|**Editar**|Permite editar el nombre, el editor y la dirección URL de la aplicación seleccionada.|
|**Eliminar**|Elimina la aplicación seleccionada de la lista.|
> [!IMPORTANT]
> Si especifica una lista de aplicaciones permitidas para dispositivos de Windows Phone 8.1, debe agregar la aplicación Portal de empresa a esta lista o se bloqueará.


### Información de referencia para aplicaciones permitidas y bloqueadas

#### Cómo especificar las direcciones URL de tiendas de aplicaciones
Para especificar la dirección URL de una aplicación en la lista de aplicaciones permitidas y bloqueadas, use el siguiente formato:

Desde la página de [aplicaciones y juegos para Windows Phone](http://www.windowsphone.com/en-us/store/overview), busque la aplicación que quiere usar.

Abra la página de la aplicación y copie la dirección URL en el Portapapeles. Ya puede usarla como dirección URL en una la lista de aplicaciones permitidas o bloqueadas.

**Ejemplo:** Busque la aplicación Skype en la Tienda. La dirección URL que use será **http://www.windowsphone.com/es-es/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.

## Configuración de directivas personalizadas
Use la **directiva de configuración personalizada de Windows Phone** de Microsoft Intune para implementar las opciones de configuración de OMA-URI, que pueden usarse para controlar características en **dispositivos Windows Phone 8.1**. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad le permite implementar la configuración de Windows Phone que no se puede configurar con una directiva de configuración general de Intune. Para obtener más información sobre las opciones que se pueden configurar con estas directivas, vea [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Para obtener ayuda acerca de cómo crear la configuración de OMA-URI para dispositivos Windows Phone, consulte [Windows Phone 8.1 MDM protocol documentation](http://technet.microsoft.com/library/dn499787.aspx).

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
    |**OMA-URI (distingue mayúsculas de minúsculas)**|Especifique el OMA-URI para el que quiere proporcionar un valor.|
    |**Valor**|Especifique el valor asociado con el OMA-URI especificado anteriormente.|

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Oct16_HO2-->


