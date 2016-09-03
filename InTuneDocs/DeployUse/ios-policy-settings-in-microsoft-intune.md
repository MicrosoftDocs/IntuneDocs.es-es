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
ms.sourcegitcommit: 65d2c9c1f5d81dae33422bd4bf7c0e2e21bb96e4
ms.openlocfilehash: 13b8bd8c3269be60d66c4e79551f662205afcea0


---

# Configuración de directivas de iOS en Microsoft Intune

Intune proporciona una variedad de opciones generales integradas que puede configurar en los dispositivos iOS. Además, puede usar la herramienta Apple Configurator para crear una configuración personalizada que no esté disponible en Intune.

## Configuración general de directivas

Use la **directiva de configuración general de iOS** de Microsoft Intune para configurar las siguientes opciones:

-   **Configuración general de dispositivos y seguridad**. Elija entre las opciones de una lista de configuraciones predefinidas que permiten controlar diversas características y funcionalidades en el dispositivo.

-   **Pantalla completa**. Bloquee un dispositivo para permitir que solo funcionen determinadas características. Por ejemplo, puede permitir que un dispositivo ejecute solo una aplicación administrada que especifique, o puede deshabilitar los botones de volumen de un dispositivo. Esta configuración podría usarse para un modelo de demostración de un dispositivo o para un dispositivo que está dedicado a realizar solo una función, como un dispositivo de punto de venta.

-   **Aplicaciones conformes y no conformes**. Especifique una lista de las aplicaciones conformes y no conformes en su empresa. En los dispositivos iOS y Android, el **Informe de aplicaciones no conformes** puede usarse para comparar la conformidad de las aplicaciones especificadas en la lista con las aplicaciones que los usuarios han instalado (pero en realidad no pueden bloquear la instalación de la aplicación).

> [!TIP]
> Puede configurar los términos y condiciones de los usuarios para asegurarse de que saben que las aplicaciones de su dispositivo (incluidas las aplicaciones personales) se evaluarán y que las aplicaciones no conformes se bloquearán o se notificarán como no conformes. Los usuarios deben aceptar estos términos y condiciones para poder inscribir su dispositivo y utilizar el portal de empresa para obtener aplicaciones. Para obtener más información sobre el uso de los términos y condiciones, consulte [Configuración de la directiva de términos y condiciones en Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Si el valor que busca no aparece en este tema, puede crearlo mediante una directiva personalizada de iOS que le permita importar la configuración creada con la [herramienta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Para obtener más información, consulte "Configuración de directivas personalizadas" más adelante en este tema.

### Configuración de seguridad
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Requerir una contraseña para desbloquear dispositivos móviles**|Especificar si el usuario tiene que escribir una contraseña para obtener acceso al dispositivo.|
|**Tipo de contraseña obligatoria**|Especificar el tipo de contraseña que será necesario, como solo numérica o alfanumérica.|
|**Número de caracteres complejos requeridos en la contraseña**|Especificar el número de caracteres de símbolos (como **#** o **@**) que deben incluirse en la contraseña.|
|**Longitud mínima de la contraseña**|Especificar el número mínimo de caracteres de la contraseña.|
|**Permitir contraseñas sencillas**|Permitir contraseñas sencillas como **0000** y **1234**.|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Especificar el número de intentos de inicio de sesión con error antes de que esta configuración borre el dispositivo.|
|**Minutos de inactividad antes de que sea necesaria la contraseña**<sup>1</sup>|Especificar cuánto tiempo puede permanecer inactivo el dispositivo antes de que el usuario deba volver a escribir su contraseña.|
|**Caducidad de contraseña (días)**|Especificar el número de días antes de que se deba cambiar la contraseña del dispositivo.|
|**Recordar el historial de contraseñas**|Especificar si el usuario puede usar las contraseñas que ha usado anteriormente.|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Especificar el número de contraseñas usadas anteriormente que el dispositivo recuerda.|
|**Minutos de inactividad antes de que se apague la pantalla**<sup>1</sup>|Especifique el número de minutos antes de que la pantalla del dispositivo se apague.|
|**Permitir desbloqueo mediante huellas digitales**|Permite desbloquear el dispositivo mediante las huellas digitales.|
<sup>1</sup> En los dispositivos iOS, cuando configura las opciones **Minutos de inactividad antes de que se apague la pantalla** y **Minutos de inactividad antes de que sea necesaria la contraseña**, estas se aplican en secuencia. Por ejemplo, si establece el valor para ambas opciones en **5** minutos, la pantalla se apagará automáticamente transcurridos 5 minutos y el dispositivo se bloqueará pasados 5 minutos más. Sin embargo, si el usuario apaga la pantalla manualmente, la segunda opción se aplica inmediatamente. En el mismo ejemplo, una vez que el usuario apague la pantalla, el dispositivo se bloqueará 5 minutos más tarde.

### Configuración del sistema
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir capturas de pantalla**|Permitir al usuario capturar el contenido de la pantalla como una imagen.|
|**Permitir centro de control en la pantalla de bloqueo**|Permitir al usuario tener acceso a la aplicación Centro de control mientras el dispositivo está bloqueado.|
|**Permitir vista de notificaciones en la pantalla de bloqueo**|Permite el acceso del usuario a la vista de notificaciones sin que sea necesario desbloquear el dispositivo.|
|**Permitir vista de hoy en la pantalla de bloqueo**|Permitir al usuario ver las notificaciones cuando el dispositivo está bloqueado.|
|**Permitir certificados TLS que no son de confianza**|Permite el uso en el dispositivo de certificados de seguridad de la capa de transporte que no son de confianza.|
|**Permitir el envío de datos de diagnóstico**|Permite o impide que el dispositivo envíe datos de diagnóstico a Apple.|
|**Permitir libreta con dispositivo bloqueado**|Permite al usuario tener acceso a la aplicación Libreta mientras el dispositivo está bloqueado.|

### Configuración de nube para documentos y datos
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir copias de seguridad en iCloud**|Permitir al usuario hacer copias de seguridad del dispositivo en iCloud.|
|**Permitir sincronización de documentos en iCloud**|Permite la sincronización de clave-valor y documentos en el espacio de almacenamiento de iCloud.|
|**Permitir sincronización de Photo Stream en iCloud**|Permite que las fotos del dispositivo se sincronicen con iCloud.|
|**Requerir copia de seguridad cifrada**|Requiere que las copias de seguridad del dispositivo se cifren.|
|**Permitir que las aplicaciones administradas sincronicen datos en iCloud**|Permitir que las aplicaciones que se administran con Intune sincronicen los datos con la cuenta de iCloud del usuario.|
|**Permitir la entrega para continuar las actividades en otro dispositivo**|Permitir al usuario continuar el trabajo iniciado en un dispositivo iOS en otro dispositivo iOS o MAC OS X.|

### Configuración de la aplicación para el explorador
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir Safari**|Especifica si se puede usar el explorador Safari en el dispositivo.|
|**Permitir el autorrelleno**|Permitir al usuario cambiar la configuración de Autocompletar en el explorador.|
|**Permitir bloqueador de elementos emergentes**|Habilita o deshabilita el bloqueador de elementos emergentes del explorador.|
|**Permitir cookies**|Permitir que el explorador use cookies.|
|**Permitir scripting de Java**|Permite que los scripts de Java se ejecuten en el explorador.|
|**Permitir advertencias de fraude**|Permitir mostrar advertencias de fraude en el explorador.|

### Configuración de la aplicación para aplicaciones
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir almacén de aplicaciones**|Permitir que el dispositivo tenga acceso a la tienda de aplicaciones.|
|**Requerir una contraseña para tener acceso al almacén de aplicaciones**|Requerir al usuario que escriba una contraseña antes de que pueda visitar la tienda de aplicaciones.|
|**Permitir compras dentro de la aplicación**|Permite realizar compras en la tienda desde una aplicación en ejecución.|
|**Permitir documentos administrados en otras aplicaciones no administradas**|Esta opción permite la visualización de documentos corporativos en cualquier aplicación.<br>**Ejemplo:** Quiere evitar que los usuarios guarden archivos de la aplicación OneDrive en Dropbox. Configure este ajuste en no. Después de que el dispositivo reciba la directiva (por ejemplo, después de un reinicio), ya no le permitirá guardar.|
|**Permitir documentos no administrados en otras aplicaciones administradas**|Permite la visualización de cualquier documento en aplicaciones administradas corporativas.|
|**Permitir videoconferencias**|Permitir el uso de aplicaciones de videoconferencia como FaceTime en el dispositivo.|
|**Permitir contenido para adultos en el almacén multimedia**|Permite que el dispositivo tenga acceso a contenido clasificado para adultos en la tienda.|
|**Permite al usuario descargar contenido desde la tienda de iBooks marcada como 'Erótico'**|Permitir al usuario descargar libros con la categoría "Erotismo".|

### Configuración de la aplicación para juegos
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir agregar amigos al centro de juegos**|Permite al usuario agregar a amigos del centro de juegos.|
|**Permitir juegos multijugador**|Permite al usuario jugar a juegos multijugador en el dispositivo.|

### Configuración de funcionalidades del dispositivo para hardware
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir cámara**|Especificar si se puede usar la cámara del dispositivo.|
|**Requerir una contraseña de emparejamiento para las solicitudes salientes de AirPlay**|Requerir una contraseña de emparejamiento cuando el usuario usa AirPlay para transmitir contenido a otros dispositivos de Apple.|

### Configuración de funcionalidades del dispositivo para red de telefonía móvil
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir itinerancia de voz**|Permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.|
|**Permitir itinerancia de datos**|Permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.|
|**Permitir captura de fondo global durante la itinerancia**|Permite al dispositivo capturar datos (por ejemplo, correo electrónico) mientras está en itinerancia en una red de telefonía móvil.|

### Configuración de funcionalidades del dispositivo para características
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir Siri**|Permite el uso del asistente de voz Siri en el dispositivo.|
|**Permitir Siri con el dispositivo bloqueado**|Permite el uso del asistente de voz Siri en el dispositivo aunque esté bloqueado.|
|**Permitir la marcación por voz**|Permite el uso de la característica de marcación por voz en el dispositivo.|


### Configuración de aplicaciones conformes y no conformes
En la lista de **Aplicaciones conformes y no conformes**, especifique las aplicaciones que son conformes y no conformes con la siguiente información.

> [!NOTE]
> Una única directiva solo puede contener una lista de aplicaciones conformes o una lista de aplicaciones no conformes. No se pueden especificar ambas en la misma directiva.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Notificar la no compatibilidad cuando los usuarios instalan las aplicaciones de la lista**|Enumerar las aplicaciones (que no se administran mediante Intune) que los usuarios no pueden instalar ni ejecutar.|
|**Informar sobre la incompatibilidad cuando los usuarios instalen aplicaciones no enumeradas**|Enumerar las aplicaciones que los usuarios pueden instalar. Para mantener la conformidad, los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.|
|**Agregar**|Agregar una aplicación a la lista seleccionada. Especifique un nombre de su elección, opcionalmente el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones. Lea "Cómo especificar las direcciones URL de tiendas de aplicaciones" más adelante en este tema para obtener más ayuda.|
|**Importar aplicaciones**|Importar una lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. En el archivo, use este formato: nombre de la aplicación, editor, dirección URL de la aplicación.|
|**Editar**|Editar el nombre, el editor y la dirección URL de la aplicación seleccionada.|
|**Eliminar**|Eliminar la aplicación seleccionada de la lista.|

### Configuración del modo de pantalla completa

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Seleccione una aplicación administrada que se permitirá ejecutar cuando el dispositivo esté en modo de quiosco**|Elija **Examinar** y, luego, especifique la aplicación administrada, o una aplicación de una tienda, que se podrá ejecutar cuando el dispositivo esté en pantalla completa. No se podrá ejecutar ninguna otra aplicación en el dispositivo. Lea "Cómo especificar las direcciones URL de tiendas de aplicaciones" más adelante en este tema para obtener más ayuda.|
|**Permitir la interacción táctil**|Habilitar o deshabilitar la pantalla táctil en el dispositivo.|
|**Permitir la rotación de pantalla**|Habilitar o deshabilitar el cambio de orientación de la pantalla cuando el usuario gira el dispositivo.|
|**Permitir los botones de volumen**|Habilitar o deshabilitar el uso de los botones de volumen en el dispositivo.|
|**Permite el conmutador de timbre**|Habilitar o deshabilitar el conmutador de timbre (silencio) en el dispositivo.|
|**Permitir el botón de reactivación de suspensión de pantalla**|Habilitar o deshabilitar el botón de reposo o activación de pantalla en el dispositivo.|
|**Permitir el bloqueo automático**|Habilitar o deshabilitar el bloqueo automático del dispositivo.|
|**Habilitar audio mono**|Habilitar o deshabilitar la configuración de accesibilidad **Audio mono**.|
|**Habilitar VoiceOver**|Habilitar o deshabilitar la configuración de accesibilidad **VoiceOver**, que lee en voz alta el texto de la pantalla del dispositivo.|
|**Habilitar los ajustes de VoiceOver**|Habilitar o deshabilitar los ajustes de VoiceOver, que permiten al usuario ajustar la función VoiceOver (por ejemplo, la rapidez con la que se lee el texto en pantalla en voz alta).|
|**Habilitar zoom**|Habilitar o deshabilitar la configuración de accesibilidad **Zoom**, que permite al usuario usar un toque para acercar la pantalla del dispositivo.|
|**Habilitar los ajustes de zoom**|Habilitar o deshabilitar los ajustes de zoom, que permiten al usuario ajustar la función de zoom.|
|**Habilitar invertir colores**|Habilitar o deshabilitar la configuración de accesibilidad **Invertir colores**, que ajusta la pantalla para ayudar a los usuarios con discapacidades visuales.|
|**Habilitar los ajustes de invertir colores**|Habilitar o deshabilitar los ajustes de invertir colores, que permiten al usuario ajustar la función de invertir colores.|
|**Habilitar la interacción táctil de asistencia**|Habilitar o deshabilitar la configuración de accesibilidad **Assistive Touch**, que ayuda al usuario a realizar gestos en pantalla que podrían resultarle difíciles.|
|**Habilitar los ajustes de la interacción táctil de asistencia**|Habilitar o deshabilitar los ajustes de Assistive Touch, que permiten al usuario ajustar la función de Assistive Touch.|
|**Habilitar la selección de voz**|Habilitar o deshabilitar la configuración de accesibilidad **Reproducir selección**, que puede leer en voz alta el texto que el usuario seleccione.|
> [!NOTE]
> Las siguientes notas se aplican a la configuración del modo de quiosco para dispositivos iOS:
>
> -   Antes de configurar un dispositivo iOS para pantalla completa, debe usar la [herramienta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) o el administrador de inscripción de dispositivos para ajustar el dispositivo en modo supervisado. Para obtener más información sobre la herramienta Apple Configurator, consulte la documentación de Apple.
> -   Si la aplicación de iOS que especifique se instala después de implementar la directiva de configuración, el dispositivo no pasará a pantalla completa hasta que se reinicie.

### Información de referencia para las aplicaciones conformes y no conformes

Utilice el **Informe de aplicaciones no conformes** para ver la conformidad de las aplicaciones permitidas y bloqueadas.

##### Para ejecutar el informe de aplicaciones no conformes

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Informes** &gt; **Informe de aplicaciones no conformes**.

2.  Seleccione los grupos de dispositivos que quiere comprobar, si quiere comprobar las aplicaciones conformes, las aplicaciones no conformes o ambas y, después, elija **Ver informe**.

#### Cómo especificar las direcciones URL de tiendas de aplicaciones
Para especificar una dirección URL de aplicación en la lista de aplicaciones conformes y no conformes o en la opción **Seleccione una aplicación administrada que se podrá ejecutar cuando el dispositivo esté en modo de pantalla completa** (solo iOS), use el siguiente formato:

1. Con la ayuda de un motor de búsqueda, busque la aplicación que quiere usar en iTunes App Store y abra la página de la aplicación.

2. Copie la dirección URL de la página y úsela como dirección URL para configurar la lista de aplicaciones conformes y no conformes o la aplicación que quiere ejecutar en pantalla completa.

**Ejemplo:** Busque **Microsoft Word para iPad**. La dirección URL que debe usar es **https://itunes.apple.com/es/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> También puede utilizar el software de iTunes para encontrar la aplicación y, a continuación, utilizar el comando **Copiar vínculo** para obtener la dirección URL de la aplicación.

### Configuración de la inscripción
Todas las configuraciones se aplican a iOS 7.1 y posterior.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Permitir bloqueo de activación cuando el dispositivo está en modo supervisado**|Permitir bloqueo de activación en dispositivos iOS supervisados.|

### Supervisión
Puede configurar las siguientes opciones en dispositivos que ejecuten iOS 7.1 y posterior que estén en modo supervisado.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Permitir la modificación de la cuenta**|Permite al usuario cambiar la configuración de la cuenta, como las configuraciones de correo electrónico.|
|**Permitir AirDrop**|Permitir el uso de la característica AirDrop para intercambiar el contenido con dispositivos cercanos.|
|**Permitir cambios en la configuración de uso de datos móviles de la aplicación**|Permite al usuario controlar qué aplicaciones pueden utilizar datos móviles.|
|**Permitir Siri para consultar el contenido generado por el usuario de Internet**|Permitir que Siri tenga acceso a sitios web para responder a preguntas.|
|**Permitir el acceso a la tienda de iBooks**|Permite al usuario examinar y comprar libros desde la tienda de iBooks.|
|**Permitir cambios en la configuración de la aplicación para buscar a sus amigos**|Permite al usuario cambiar la configuración de la aplicación para buscar a sus amigos.|
|**Permitir el uso de la opción de borrado de todo el contenido y configuración en el dispositivo**|Permitir al usuario usar la opción de borrar todo el contenido y la configuración del dispositivo.|
|**Permitir al usuario habilitar las restricciones en la configuración del dispositivo**|Permitir al usuario configurar restricciones de dispositivos (controles parentales) en el dispositivo.|
|**Permitir la búsqueda de Spotlight para devolver resultados de Internet**|Permitir que la búsqueda de Spotlight se conecte a Internet para proporcionar más resultados.|
|**Permitir el uso de la aplicación Centro de juegos**|Permite el uso de la aplicación Centro de juegos.|
|**Permitir el emparejamiento de host para controlar los dispositivos que puede emparejar un dispositivo iOS**|Permitir que el emparejamiento de host permita al administrador controlar con qué dispositivos se puede emparejar un dispositivo iOS 7.|
|**Permitir al usuario que instale certificados y perfiles de configuración**|Permite al usuario que instale certificados y perfiles de configuración.|
|**Permitir el uso de la aplicación de mensajes en el dispositivo**|Permite el uso de la aplicación de mensajes en el dispositivo.|

### Mostrar u ocultar aplicaciones

Use la **Lista de aplicaciones ocultas y visibles** para controlar las siguientes opciones en los dispositivos supervisados que ejecutan iOS 9.3 o versiones posteriores:

- Especificar una lista de las aplicaciones ocultas para los usuarios. Los usuarios no pueden ver ni iniciar estas aplicaciones.
- Especificar una lista de las aplicaciones que los usuarios pueden ver e iniciar. No se puede ver ni iniciar ninguna otra aplicación.


#### Cómo crear una lista de aplicaciones ocultas y visibles

Especifique las siguientes opciones:

|Nombre de la configuración|Detalles|
|-|-|
|**Lista de aplicaciones ocultas y visibles**|Habilite esta opción si quiere crear una lista de aplicaciones ocultas o visibles.|
|**Ocultar las aplicaciones de la lista a los usuarios**|Seleccione esta opción si quiere crear una lista de aplicaciones que permanecerán ocultas para los usuarios.|
|**Mostrar solo las aplicaciones de la lista a los usuarios**|Seleccione esta opción si quiere crear una lista de aplicaciones que se muestre a los usuarios.<br>Cuando cree este tipo de lista, todas las demás aplicaciones están ocultas; excepto para las aplicaciones **Configuración** y **Teléfono** (para iPhone) de iOS.<br>Además, debe agregar el Portal de empresa, y cualquier aplicación que haya implementado, y administrarlo con Intune para la lista.|
|**Agregar**|Agrega una aplicación a la lista seleccionada.<br>Para la lista oculta, debe especificar el **Nombre**, **Publicador** y **Dirección URL de aplicación o id. de lote de aplicaciones** de cada aplicación que quiera ocultar.<br>Para la lista que se muestra, puede **Seleccionar una aplicación administrada** que le proporciona una lista de las aplicaciones que administra con Intune para seleccionarlas, o bien Seleccionar aplicación de tienda, donde debe especificar el **Nombre**, **Publicador** y **Dirección URL de aplicación o id. de lote de aplicaciones** de cada aplicación que quiere mostrar.|
|**Importar aplicaciones**|Importa la lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. Utilice el formato, nombre de la aplicación, editor, dirección URL de la aplicación en el archivo.|
|**Editar**|Permite editar el nombre, el editor y la dirección URL de la aplicación seleccionada.|
|**Eliminar**|Elimina la aplicación seleccionada de la lista.|

#### Información de aplicaciones para las aplicaciones integradas de iOS

Use la información de esta lista para identificar el nombre, el publicador y el identificador de lote de aplicaciones de las aplicaciones integradas de iOS que quiere mostrar u ocultar. Si quiere mostrar u ocultar todas las aplicaciones de la lista, puede copiar los datos siguientes en un archivo de texto con la extensión **.csv** y, después, usar la opción **Importar aplicaciones** para importar todas las aplicaciones a la vez.

```
App Store,Apple,com.apple.AppStore
Calculator,Apple,com.apple.calculator
Calendar,Apple,com.apple.mobilecal
Camera,Apple,com.apple.camera
Clock,Apple,com.apple.mobiletimer
Compass,Apple,com.apple.compass
Contacts,Apple,com.apple.MobileAddressBook
FaceTime,Apple,com.apple.facetime
Find Friends,Apple,com.apple.mobileme.fmf1
Find iPhone,Apple,com.apple.mobileme.fmip1
Game Center,Apple,com.apple.gamecenter
GarageBand,Apple,com.apple.mobilegarageband
Health,Apple,com.apple.Health
iBooks,Apple,com.apple.iBooks
iTunes Store,Apple,com.apple.MobileStore
iTunes U,Apple,com.apple.itunesu
Keynote,Apple,com.apple.Keynote
Mail,Apple,com.apple.mobilemail
Maps,Apple,com.apple.Maps
Messages,Apple,com.apple.MobileSMS
Music,Apple,com.apple.Music
News,Apple,com.apple.news
Notes,Apple,com.apple.mobilenotes
Numbers,Apple,com.apple.Numbers
Pages,Apple,com.apple.Pages
Photo Booth,Apple,com.apple.Photo-Booth
Photos,Apple,com.apple.mobileslideshow
Podcasts,Apple,com.apple.podcasts
Reminders,Apple,com.apple.reminders
Safari,Apple,com.apple.mobilesafari
Settings,Apple,com.apple.Preferences
Stocks,Apple,com.apple.stocks
Tips,Apple,com.apple.tips
Videos,Apple,com.apple.videos
VoiceMemos,Apple,com.apple.VoiceMemos
Wallet,Apple,com.apple.Passbook
Watch,Apple,com.apple.Bridge
Weather,Apple,com.apple.weather


```




## Configuración de directivas personalizadas

Use la **Directiva personalizada para iOS** de Microsoft Intune para implementar la configuración que ha creado mediante la [herramienta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) en dispositivos iOS. Esta herramienta permite crear muchas configuraciones para controlar el funcionamiento de estos dispositivos y exportarlas a un perfil de configuración. A continuación, puede importar este perfil de configuración en una directiva personalizada de iOS de Intune e implementar la configuración para los usuarios y dispositivos de su organización.

Esta funcionalidad permite implementar la configuración de iOS que no se puede configurar con directivas de configuración general de Intune.

### Requisitos previos
Antes de empezar, debe tener instalado Apple Configurator y haber creado un archivo de configuración que contenga la configuración que quiere implementar en usuarios o dispositivos. Puede descargar Apple Configurator y obtener información sobre esta aplicación en [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12).

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
|**Archivo del perfil de configuración**|Elija **Importar** y, luego, examine el perfil de configuración que ha creado con Apple Configurator. **Nota:** Asegúrese de que la configuración que exporta de la herramienta Apple Configurator sea compatible con la versión de iOS en los dispositivos en los que implementa la directiva personalizada de iOS. Para obtener información sobre la resolución de las opciones de configuración incompatibles, busque la **Referencia de perfiles de configuración** y la **Referencia del protocolo de administración de dispositivos móviles** en el sitio web de [Apple Developer](https://developer.apple.com/).|
    |**Detalles del perfil de configuración**|Mostrar el código XML del perfil de configuración que ha importado.|

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Aug16_HO3-->


