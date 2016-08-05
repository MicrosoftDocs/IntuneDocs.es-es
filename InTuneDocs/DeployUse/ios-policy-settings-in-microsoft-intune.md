---
title: "Configuración de directivas de iOS | Microsoft Intune"
description: "Cree directivas que controlen la configuración y las características en los dispositivos iOS que administra con Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 947328a5c28839d8227a9e5ae0dd8b1fc5ad8e81
ms.openlocfilehash: 63bc2cedf8d81b050a384a947a0b43827de5c352


---

# Configuración de directivas de iOS en Microsoft Intune

Intune proporciona una variedad de opciones generales integradas que puede configurar en los dispositivos iOS. Además, puede usar la herramienta Apple Configurator para crear una configuración personalizada que no esté disponible en Intune.

## Configuración general de directivas

Use la **directiva de configuración general de iOS** de Microsoft Intune para configurar las siguientes opciones:

-   **Configuración de seguridad y de dispositivos generales**: elija entre una lista de configuraciones predefinidas que permiten controlar una variedad de características y funcionalidades en el dispositivo.

-   **Pantalla completa**: bloquee un dispositivo para permitir que solo funcionen determinadas características. Por ejemplo, puede permitir que un dispositivo ejecute solo una aplicación administrada que especifique, o puede deshabilitar los botones de volumen de un dispositivo. Esta configuración podría utilizarse para un modelo de demostración de un dispositivo o para un dispositivo que está dedicado a realizar solo una función, como un dispositivo de punto de venta.

-   **Aplicaciones compatibles y no compatibles**: especifique una lista de las aplicaciones compatibles y no compatibles de su empresa. En los dispositivos iOS y Android, el **informe de aplicaciones no conformes** puede utilizarse para comparar la conformidad de las aplicaciones especificadas en la lista con las aplicaciones que los usuarios han instalado (pero en realidad no pueden impedir la instalación de la aplicación).

> [!TIP]
> Puede configurar los términos y condiciones de los usuarios para asegurarse de que saben que las aplicaciones de su dispositivo, incluidas las aplicaciones personales, se evaluarán y que las aplicaciones no conformes se bloquearán o se notificarán como no conformes. Los usuarios deben aceptar estos términos y condiciones para poder inscribir su dispositivo y utilizar el portal de empresa para obtener aplicaciones. Para obtener más información sobre el uso de los términos y condiciones, consulte [Configuración de la directiva de términos y condiciones en Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Si el valor que busca no aparece en este tema, puede crearlo mediante una directiva personalizada de iOS que le permita importar la configuración creada con [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Para obtener más información, consulte **Configuración de directivas personalizadas**.

### Configuración de seguridad
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Requerir una contraseña para desbloquear dispositivos móviles**|Especifica si los usuarios tienen que escribir una contraseña para obtener acceso al dispositivo.|
|**Tipo de contraseña obligatoria**|Especifica el tipo de contraseña que será necesario, como solo numérica o alfanumérica.|
|**Número de caracteres complejos requeridos en la contraseña**|Especifica el número de caracteres de símbolos (como **#** o **@**) que deben incluirse en la contraseña.|
|**Longitud mínima de la contraseña**|Especifica el número mínimo de caracteres de la contraseña.|
|**Permitir contraseñas sencillas**|Permitir contraseñas sencillas como ‘0000’ y ‘1234’.|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Borra el dispositivo si hay un error en este número de intentos de inicio de sesión.|
|**Minutos de inactividad antes de que sea necesaria la contraseña**<sup>1</sup>|Especifica cuánto tiempo puede permanecer inactivo el dispositivo antes de que el usuario deba volver a escribir su contraseña.|
|**Caducidad de contraseña (días)**|Especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.|
|**Recordar el historial de contraseñas**|Especifica si el usuario puede utilizar las contraseñas que ha usado anteriormente.|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Especifica el número de contraseñas usadas anteriormente que recuerda el dispositivo.|
|**Minutos de inactividad antes de que se apague la pantalla**<sup>1</sup>|Especifique el número de minutos antes de que la pantalla del dispositivo se apague.|
|**Permitir desbloqueo mediante huellas digitales**|Permite desbloquear el dispositivo mediante las huellas digitales.|
<sup>1</sup> En los dispositivos iOS, cuando configura las opciones **Minutos de inactividad antes de que se apague la pantalla** y **Minutos de inactividad antes de que sea necesaria la contraseña**, estas se aplican en secuencia. Por ejemplo, si establece el valor para ambas opciones en **5** minutos, la pantalla se apagará automáticamente transcurridos 5 minutos y el dispositivo se bloqueará pasados 5 minutos más. Sin embargo, si el usuario apaga la pantalla manualmente, la segunda opción se aplica inmediatamente. En el mismo ejemplo, una vez que el usuario apague la pantalla, el dispositivo se bloqueará 5 minutos más tarde.

### Configuración del sistema
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir capturas de pantalla**|Permite al usuario capturar el contenido de la pantalla como una imagen.|
|**Permitir centro de control en la pantalla de bloqueo**|Controla si se puede tener acceso a la aplicación de centro de control cuando el dispositivo está bloqueado.|
|**Permitir vista de notificaciones en la pantalla de bloqueo**|Permite el acceso del usuario a la vista de notificaciones sin que sea necesario desbloquear el dispositivo.|
|**Permitir vista de hoy en la pantalla de bloqueo**|Controla si se pueden ver notificaciones cuando el dispositivo está bloqueado.|
|**Permitir certificados TLS que no son de confianza**|Permite el uso en el dispositivo de certificados de seguridad de la capa de transporte que no son de confianza.|
|**Permitir el envío de datos de diagnóstico**|Permite o impide que el dispositivo envíe datos de diagnóstico a Apple.|
|**Permitir libreta con dispositivo bloqueado**|Permite al usuario tener acceso a la aplicación Libreta mientras el dispositivo está bloqueado.|

### Configuración de nube: documentos y datos
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir copias de seguridad en iCloud**|Permite al usuario hacer copias de seguridad del dispositivo en iCloud.|
|**Permitir sincronización de documentos en iCloud**|Permite la sincronización de clave-valor y documentos en el espacio de almacenamiento de iCloud.|
|**Permitir sincronización de Photo Stream en iCloud**|Permite que las fotos del dispositivo se sincronicen con iCloud.|
|**Requerir copia de seguridad cifrada**|Requiere que las copias de seguridad del dispositivo se cifren.|
|**Permitir que las aplicaciones administradas sincronicen datos en iCloud**|Permitir las aplicaciones que se administran con Intune para sincronizar los datos con la cuenta de usuarios iCloud.|
|**Permitir la entrega para continuar las actividades en otro dispositivo**|La entrega permite continuar el trabajo iniciado en un dispositivo iOS en otro dispositivo iOS o MAC OS X.|

### Configuración de la aplicación: explorador
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir Safari**|Especifica si se puede usar el explorador Safari en el dispositivo.|
|**Permitir el autorrelleno**|El usuario puede cambiar la configuración de Autocompletar en el explorador.|
|**Permitir bloqueador de elementos emergentes**|Habilita o deshabilita el bloqueador de elementos emergentes del explorador.|
|**Permitir cookies**|Permite que el explorador web del dispositivo use cookies.|
|**Permitir scripting de Java**|Permite que los scripts de Java se ejecuten en el explorador.|
|**Permitir advertencias de fraude**|Permite mostrar advertencias de fraude en el explorador del dispositivo.|

### Configuración de la aplicación: aplicaciones
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir almacén de aplicaciones**|Permite que el dispositivo tenga acceso a la tienda de aplicaciones.|
|**Requerir una contraseña para tener acceso al almacén de aplicaciones**|Es necesario que el usuario escriba una contraseña antes de que pueda visitar la tienda de aplicaciones.|
|**Permitir compras dentro de la aplicación**|Permite realizar compras en la tienda desde una aplicación en ejecución.|
|**Permitir documentos administrados en otras aplicaciones no administradas**|Permite la visualización de documentos corporativos en cualquier aplicación.<br>**Ejemplo:** quiere evitar que los usuarios guarden archivos de la aplicación de OneDrive en Dropbox. Configure este ajuste en no. Después de que el dispositivo reciba la directiva (por ejemplo, después de un reinicio), ya no le permitirá guardar.|
|**Permitir documentos no administrados en otras aplicaciones administradas**|Permite la visualización de cualquier documento en aplicaciones administradas corporativas.|
|**Permitir videoconferencias**|Permite el uso de aplicaciones de videoconferencia como Facetime en el dispositivo.|
|**Permitir contenido para adultos en el almacén multimedia**|Permite que el dispositivo tenga acceso a contenido clasificado para adultos en la tienda.|
|**Permite al usuario descargar contenido desde la tienda de iBooks marcada como 'Erótico'**|Permite al usuario descargar libros con la categoría 'Erótico'.|

### Configuración de aplicaciones: juegos
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir agregar amigos al centro de juegos**|Permite al usuario agregar a amigos del centro de juegos.|
|**Permitir juegos multijugador**|Permite al usuario jugar a juegos multijugador en el dispositivo.|

### Configuración de funcionalidades del dispositivo: hardware
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir cámara**|Especifica si se puede usar la cámara del dispositivo.|
|**Requerir una contraseña de emparejamiento para las solicitudes salientes de AirPlay**|Airplay le permite transmitir contenido a otros dispositivos de Apple. Utilice esta opción para requerir una contraseña de emparejamiento para conectarse a otros dispositivos.|

### Configuración de funcionalidades del dispositivo: datos móviles
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir itinerancia de voz**|Permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.|
|**Permitir itinerancia de datos**|Permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.|
|**Permitir captura de fondo global durante la itinerancia**|Permite al dispositivo capturar datos (por ejemplo, correo electrónico) mientras está en itinerancia en una red de telefonía móvil.|

### Configuración de funcionalidades del dispositivo: características
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir Siri**|Permite el uso del asistente de voz Siri en el dispositivo.|
|**Permitir Siri con el dispositivo bloqueado**|Permite el uso del asistente de voz Siri en el dispositivo aunque esté bloqueado.|
|**Permitir la marcación por voz**|Permite el uso de la característica de marcación por voz en el dispositivo.|


### Configuración de aplicaciones conformes y no conformes
En la lista de **aplicaciones compatibles&amp; y no compatibles**, especifique las aplicaciones que son compatibles y no compatibles con la siguiente información:

> [!NOTE]
> Una única directiva solo puede contener una lista de aplicaciones conformes o una lista de aplicaciones no conformes. No se pueden especificar ambas en la misma directiva.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Notificar la no compatibilidad cuando los usuarios instalan las aplicaciones de la lista**|Enumera las aplicaciones que no se administran mediante Intune y que los usuarios no pueden instalar ni ejecutar.|
|**Informar sobre la incompatibilidad cuando los usuarios instalen aplicaciones no enumeradas**|Enumera las aplicaciones que los usuarios pueden instalar. Para mantener la conformidad, los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.|
|**Agregar**|Agrega una aplicación a la lista seleccionada. Especifique un nombre de su elección, opcionalmente el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones. Lea **Cómo especificar las direcciones URL de tiendas de aplicaciones** más adelante en este tema para obtener más ayuda.|
|**Importar aplicaciones**|Importa la lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. Utilice el formato, nombre de la aplicación, editor, dirección URL de la aplicación en el archivo.|
|**Editar**|Permite editar el nombre, el editor y la dirección URL de la aplicación seleccionada.|
|**Eliminar**|Elimina la aplicación seleccionada de la lista.|

### Configuración del modo de pantalla completa

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Seleccione una aplicación administrada que se permitirá ejecutar cuando el dispositivo esté en modo de quiosco**|Elija **Examinar**y luego especifique la aplicación administrada, o una aplicación de una tienda que se podrá ejecutar cuando el dispositivo esté en pantalla completa. Ninguna otra aplicación se podrá ejecutar en el dispositivo. Para obtener más información, vea **Cómo especificar las direcciones URL de tiendas de aplicaciones** más adelante en este tema.|
|**Permitir la interacción táctil**|Habilita o deshabilita la pantalla táctil en el dispositivo.|
|**Permitir la rotación de pantalla**|Habilita o deshabilita el cambio de orientación de la pantalla cuando el dispositivo gira.|
|**Permitir los botones de volumen**|Habilita o deshabilita el uso de los botones de volumen en el dispositivo.|
|**Permite el conmutador de timbre**|Habilita o deshabilita el conmutador de timbre (silencio) en el dispositivo.|
|**Permitir el botón de reactivación de suspensión de pantalla**|Habilita o deshabilita el botón de reactivación de la suspensión de pantalla en el dispositivo.|
|**Permitir el bloqueo automático**|Habilita o deshabilita el bloqueo automático del dispositivo.|
|**Habilitar audio mono**|Habilita o deshabilita la configuración de accesibilidad **Audio mono**.|
|**Habilitar VoiceOver**|Habilita o deshabilita la opción de accesibilidad **VoiceOver** , que lee en voz alta el texto de la pantalla del dispositivo.|
|**Habilitar los ajustes de VoiceOver**|Habilita o deshabilita los ajustes de VoiceOver, que permiten ajustar la función VoiceOver (por ejemplo, la rapidez con la que se lee el texto en pantalla en voz alta).|
|**Habilitar zoom**|Habilita o deshabilita la configuración de accesibilidad de **Zoom** , que permite usar un toque para hacer zoom en la pantalla del dispositivo.|
|**Habilitar los ajustes de zoom**|Habilita o deshabilita los ajustes de zoom que permiten ajustar la función de zoom.|
|**Habilitar invertir colores**|Habilita o deshabilita la configuración de accesibilidad **Invertir colores** , que ajusta la pantalla para ayudar a los usuarios con discapacidades visuales.|
|**Habilitar los ajustes de invertir colores**|Habilita o deshabilita los ajustes de invertir colores que permiten ajustar la función de invertir colores.|
|**Habilitar la interacción táctil de asistencia**|Habilita o deshabilita la configuración de accesibilidad **Interacción táctil de asistencia** que ayuda a los usuarios a realizar gestos en pantalla que podrían resultarles difíciles.|
|**Habilitar los ajustes de la interacción táctil de asistencia**|Habilita o deshabilita los ajustes de la interacción táctil de asistencia que le permiten ajustar la función de interacción táctil de asistencia.|
|**Habilitar la selección de voz**|Habilita o deshabilita la configuración de accesibilidad **Reproducir selección** que lee en voz alta el texto que seleccione.|
> [!NOTE]
> Las siguientes notas se aplican a la configuración del modo de quiosco para dispositivos iOS:
> 
> -   Antes de configurar un dispositivo iOS para el modo de quiosco, debe usar la [herramienta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) o el administrador de inscripción de dispositivos para ajustar el dispositivo en el modo de supervisión. Para obtener más información acerca de la herramienta Apple Configurator, consulte la documentación de Apple.
> -   Si la aplicación de iOS que especifique se instala después de implementar la directiva de configuración, el dispositivo no pasará al modo de quiosco hasta que se reinicie.

### Información de referencia para las aplicaciones conformes y no conformes

#### Supervisar las aplicaciones conformes y no conformes
Utilice el **Informe de aplicaciones no conformes** para ver la conformidad de las aplicaciones permitidas y bloqueadas.

##### Para ejecutar el informe de aplicaciones no conformes

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Informes** &gt; **Informe de aplicaciones no conformes**.

2.  Seleccione los grupos de dispositivos que quiere comprobar, si quiere comprobar las aplicaciones conformes, las aplicaciones no conformes o ambas y, después, elija **Ver informe**.

#### Cómo especificar las direcciones URL de tiendas de aplicaciones
Para especificar una dirección URL de aplicación en la lista de aplicaciones conformes y no conformes o en la opción **Seleccione una aplicación administrada que se podrá ejecutar cuando el dispositivo esté en modo de pantalla completa** (solo iOS), use el siguiente formato:

Con la ayuda de un motor de búsqueda, busque la aplicación que desea usar en iTunes App Store y abra la página de la aplicación.

Copie la dirección URL de la página y úsela como dirección URL para configurar la lista de aplicaciones conformes y no conformes o la aplicación que desea ejecutar en modo de quiosco.

**Ejemplo:** Busque **Microsoft Word para iPad**. La dirección URL que use será **https://itunes.apple.com/es/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> También puede utilizar el software de iTunes para encontrar la aplicación y, a continuación, utilizar el comando **Copiar vínculo** para obtener la dirección URL de la aplicación.

### Configuración de la inscripción
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Permitir bloqueo de activación cuando el dispositivo está en modo supervisado**|Permite el bloqueo de activación en dispositivos iOS supervisados.|

### Supervisión
Las siguientes opciones se pueden configurar en dispositivos que ejecuten iOS 7.1 y posterior que estén en modo supervisado.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Permitir la modificación de la cuenta**|Permite al usuario cambiar la configuración de la cuenta, como las configuraciones de correo electrónico.|
|**Permitir AirDrop**|Permite el uso de la característica Airdrop para intercambiar el contenido con dispositivos cercanos.|
|**Permitir cambios en la configuración de uso de datos móviles de la aplicación**|Permite al usuario controlar qué aplicaciones pueden utilizar datos móviles.|
|**Permitir Siri para consultar el contenido generado por el usuario de Internet**|Permite Siri para tener acceso a sitios web para responder a preguntas.|
|**Permitir el acceso a la tienda de iBooks**|Permite al usuario examinar y comprar libros desde la tienda de iBooks.|
|**Permitir cambios en la configuración de la aplicación para buscar a sus amigos**|Permite al usuario cambiar la configuración de la aplicación para buscar a sus amigos.|
|**Permitir el uso de la opción de borrado de todo el contenido y configuración en el dispositivo**|Permite al usuario usar la opción de borrado de todo el contenido y la configuración del dispositivo.|
|**Permitir al usuario habilitar las restricciones en la configuración del dispositivo**|Permitir al usuario configurar restricciones de dispositivos (controles parentales) en el dispositivo|
|**Permitir la búsqueda de Spotlight para devolver resultados de Internet**|Vamos a conectar la búsqueda de Spotlight a Internet para proporcionar más resultados.|
|**Permitir el uso de la aplicación Centro de juegos**|Permite el uso de la aplicación Centro de juegos.|
|**Permitir el emparejamiento de host para controlar los dispositivos que puede emparejar un dispositivo iOS**|El emparejamiento de host permite al administrador controlar qué dispositivos puede emparejar con un dispositivo iOS 7.|
|**Permitir al usuario que instale certificados y perfiles de configuración**|Permite al usuario que instale certificados y perfiles de configuración.|
|**Permitir el uso de la aplicación de mensajes en el dispositivo**|Permite el uso de la aplicación de mensajes en el dispositivo.|


## Configuración de directivas personalizadas

Use la **Directiva personalizada para iOS** de Microsoft Intune para implementar la configuración que creó mediante la [herramienta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) en dispositivos iOS. Esta herramienta permite crear muchas configuraciones para controlar el funcionamiento de estos dispositivos y exportarlas a un perfil de configuración. A continuación, puede importar este perfil de configuración en una directiva personalizada de iOS de Intune e implementar la configuración para los usuarios y dispositivos de su organización.

Esta funcionalidad está destinada a permitirle implementar la configuración de iOS que no se puede configurar con una directiva de configuración general de Intune.

### Requisitos previos
Antes de empezar, debe tener instalado Apple Configurator y haber creado un archivo de configuración que contenga la configuración que desea implementar en usuarios o dispositivos. Puede descargar Apple Configurator y obtener información sobre esta aplicación en el [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)

> [!NOTE]
> Intune no notifica el cumplimiento de opciones de configuración individuales de una directiva personalizada de iOS. Sin embargo, se notifica el cumplimiento general de la directiva.

### Configuración general

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre**|Escriba un nombre único para la directiva personalizada de iOS que le ayude a identificarla en la consola de Intune.|
    |**Descripción**|Proporcione una descripción que ofrezca una visión general de la directiva personalizada de iOS y otra información relevante que le ayude a encontrarla.|

### Configuración personalizada

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
|**Nombre del perfil de configuración personalizada (que se muestra a los usuarios)**|Proporcione el nombre de la directiva que se mostrará en el dispositivo y en los informes de directivas de Intune.|
|**Archivo del perfil de configuración**|Elija **Importar** y luego examine el perfil de configuración que ha creado con Apple Configurator. **Nota:** Asegúrese de que la configuración que exporta de la herramienta Apple Configurator sea compatible con la versión de iOS en los dispositivos en los que implementa la directiva personalizada de iOS. Para obtener información sobre la resolución de las opciones de configuración incompatibles, busque la **referencia de perfiles de configuración** y la **referencia del protocolo de administración de dispositivos móviles** en el sitio web para [desarrolladores de Apple](https://developer.apple.com/).|
    |**Detalles del perfil de configuración**|Muestra el código XML del perfil de configuración que ha importado.|

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jul16_HO4-->


