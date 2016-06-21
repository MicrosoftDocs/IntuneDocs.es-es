---
# required metadata

title: Configuración de directivas de iOS | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configuración de directivas de iOS en Microsoft Intune

## Configuración general de directivas

Use la **directiva de configuración general de iOS** de Microsoft Intune para configurar las siguientes opciones:

-   **Configuración de seguridad de dispositivos móviles** : elija entre una lista de configuraciones predefinidas que permiten controlar una variedad de características y la funcionalidad en el dispositivo.

-   **Pantalla completa**: bloquee un dispositivo para permitir que solo funcionen determinadas características. Por ejemplo, puede permitir que un dispositivo ejecute solo una aplicación administrada que especifique, o puede deshabilitar los botones de volumen de un dispositivo. Esta configuración podría utilizarse para un modelo de demostración de un dispositivo o para un dispositivo que está dedicado a realizar solo una función, como un dispositivo de punto de venta.

-   **Aplicaciones compatibles y no compatibles**: especifique una lista de las aplicaciones compatibles y no compatibles de su empresa. En los dispositivos iOS y Android, el **informe de aplicaciones no conformes** puede utilizarse para comparar la conformidad de las aplicaciones especificadas en la lista con las aplicaciones que los usuarios han instalado (pero en realidad no pueden impedir la instalación de la aplicación).

> [!TIP]
> Puede configurar los términos y condiciones de los usuarios para asegurarse de que saben que las aplicaciones de su dispositivo, incluidas las aplicaciones personales, se evaluarán y que las aplicaciones no conformes se bloquearán o se notificarán como no conformes. Los usuarios deben aceptar estos términos y condiciones para poder inscribir su dispositivo y utilizar el portal de empresa para obtener aplicaciones. Para obtener más información sobre el uso de los términos y condiciones, consulte [Configuración de la directiva de términos y condiciones en Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Si el valor que busca no aparece en este tema, puede crearlo mediante una directiva personalizada de iOS que le permita importar la configuración creada con [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Para obtener más información, consulte **Configuración de directivas personalizadas**.

### Configuración de seguridad

|Nombre de la configuración|Detalles|iOS|
|----------------|-------|
|**Requerir una contraseña para desbloquear dispositivos móviles**|Especifica si los usuarios tienen que escribir una contraseña para obtener acceso al dispositivo.|Sí|
|**Tipo de contraseña obligatoria**|Especifica el tipo de contraseña obligatoria (solo numérica o alfanumérica).|Sí|
|**Tipo de contraseña requerida: número mínimo de conjuntos de caracteres**|Hay cuatro conjuntos de caracteres: letras minúsculas, letras mayúsculas, símbolos y números. Esta configuración especifica cuántos conjuntos de caracteres diferentes deben incluirse en la contraseña. Sin embargo, para dispositivos iOS, especifica el número de caracteres de símbolos que deben incluirse en la contraseña.|Sí|
|**Longitud mínima de la contraseña**|Especifica el número mínimo de caracteres de la contraseña.|Sí|
|**Permitir contraseñas sencillas**|Permitir contraseñas sencillas como ‘0000’ y ‘1234’.|Sí|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Borra el dispositivo si hay un error en este número de intentos de inicio de sesión.|Sí|
|**Minutos de inactividad antes de que se apague la pantalla**<sup>1</sup>|Especifique el número de minutos antes de que la pantalla del dispositivo se apague.|Sí|
|**Caducidad de contraseña (días)**|Especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.|Sí|
|**Recordar el historial de contraseñas**|Especifica si el usuario puede utilizar las contraseñas que ha usado anteriormente.|Sí|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Especifica el número de contraseñas usadas anteriormente que recuerda el dispositivo.|Sí|
|**Minutos de inactividad antes de que sea necesaria la contraseña**<sup>1</sup>|Especifica cuánto tiempo puede permanecer inactivo el dispositivo antes de que el usuario deba volver a escribir su contraseña.|Sí|
|**Permitir desbloqueo mediante huellas digitales**|Permite desbloquear el dispositivo mediante las huellas digitales.|iOS 7.1 y versiones posteriores|
<sup>1</sup> En los dispositivos iOS, cuando configura las opciones **Minutos de inactividad antes de que se apague la pantalla** y **Minutos de inactividad antes de que sea necesaria la contraseña**, estas se aplican en secuencia. Por ejemplo, si establece el valor para ambas opciones en **5** minutos, la pantalla se apagará automáticamente transcurridos 5 minutos y el dispositivo se bloqueará pasados 5 minutos más. Sin embargo, si el usuario apaga la pantalla manualmente, la segunda opción se aplica inmediatamente. En el mismo ejemplo, una vez que el usuario apague la pantalla, el dispositivo se bloqueará 5 minutos más tarde.

### Configuración del sistema

|Nombre de la configuración|Detalles|iOS|
|----------------|-------|
|**Permitir capturas de pantalla**|Permite al usuario capturar el contenido de la pantalla como una imagen.|Sí|
|**Permitir centro de control en la pantalla de bloqueo**|Controla si se puede tener acceso a la aplicación de centro de control cuando el dispositivo está bloqueado.|iOS 7.1 y versiones posteriores|
|**Permitir vista de notificaciones en la pantalla de bloqueo**|Permite el acceso del usuario a la vista de notificaciones sin que sea necesario desbloquear el dispositivo.|iOS 7.1 y versiones posteriores|
|**Permitir vista de hoy en la pantalla de bloqueo**|Controla si se pueden ver notificaciones cuando el dispositivo está bloqueado.|iOS 7.1 y versiones posteriores|
|**Permitir el envío de datos de diagnóstico**|Permite o impide que el dispositivo envíe datos de diagnóstico a Apple.|Sí|
|**Permitir certificados TLS que no son de confianza**|Permite el uso en el dispositivo de certificados de seguridad de la capa de transporte que no son de confianza.|Sí|
|**Permitir libreta con dispositivo bloqueado**|Permite al usuario tener acceso a la aplicación Libreta mientras el dispositivo está bloqueado.|Sí|

### Configuración de nube: documentos y datos

|Nombre de la configuración|Detalles|iOS|
|----------------|-------|
|**Permitir copias de seguridad en iCloud**|Permite al usuario hacer copias de seguridad del dispositivo en iCloud.|Sí|
|**Permitir sincronización de documentos en iCloud**|Permite la sincronización de clave-valor y documentos en el espacio de almacenamiento de iCloud. Sí|
|**Permitir sincronización de Photo Stream en iCloud**|Permite que las fotos del dispositivo se sincronicen con iCloud.|Sí|
|**Requerir copia de seguridad cifrada**|Requiere que las copias de seguridad del dispositivo se cifren.|Sí|

### Configuración de la aplicación: explorador

|Nombre de la configuración|Detalles|iOS|
|----------------|-------|
|**Permitir Safari**|Especifica si se puede usar el explorador Safari en el dispositivo.|Sí|
|**Permitir el autorrelleno**|El usuario puede cambiar la configuración de Autocompletar en el explorador.|Sí|
|**Permitir bloqueador de elementos emergentes**|Habilita o deshabilita el bloqueador de elementos emergentes del explorador.|Sí|
|**Permitir cookies**|Permite que el explorador web del dispositivo use cookies.|Sí|
|**Permitir scripting de Java**|Permite que los scripts de Java se ejecuten en el explorador.|Sí|
|**Permitir advertencias de fraude**|Permite mostrar advertencias de fraude en el explorador del dispositivo.|Sí|

### Configuración de la aplicación: aplicaciones

|Nombre de la configuración|Detalles|iOS|
|----------------|-------|
|**Permitir almacén de aplicaciones**|Permite que el dispositivo tenga acceso a la tienda de aplicaciones.|Sí|
|**Requerir una contraseña para tener acceso al almacén de aplicaciones**|Sí|
|**Permitir compras dentro de la aplicación**|Permite realizar compras en la tienda desde una aplicación en ejecución.|Sí|
|**Permitir documentos administrados en otras aplicaciones no administradas**|Permite la visualización de documentos corporativos en cualquier aplicación.|iOS 7.1 y versiones posteriores|
|**Permitir documentos no administrados en otras aplicaciones administradas**|Permite la visualización de cualquier documento en aplicaciones administradas corporativas.|iOS 7.1 y versiones posteriores|
|**Permitir videoconferencias**|Permite el uso de aplicaciones de videoconferencia como Facetime en el dispositivo.|Sí|
|**Permitir contenido para adultos en el almacén multimedia**|Permite que el dispositivo tenga acceso a contenido clasificado para adultos en la tienda.|Sí|

### Configuración de aplicaciones: juegos

|Nombre de la configuración|Detalles|iOS|
|----------------|-------|
|**Permitir agregar amigos al centro de juegos**|Permite al usuario agregar a amigos del centro de juegos.|Sí|
|**Permitir juegos multijugador**|Permite al usuario jugar a juegos multijugador en el dispositivo.|Sí|

### Configuración de funcionalidades del dispositivo: hardware

|Nombre de la configuración|Detalles|iOS|
|----------------|-------|
|**Permitir cámara**|Especifica si se puede usar la cámara del dispositivo.|Sí|

### Configuración de funcionalidades del dispositivo: datos móviles

|Nombre de la configuración|Detalles|iOS|
|----------------|-------|
|**Permitir itinerancia de voz**|Permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.|Sí|
|**Permitir itinerancia de datos**|Permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.|Sí|
|**Permitir captura de fondo global durante la itinerancia**|Permite al dispositivo capturar datos (por ejemplo, correo electrónico) mientras está en itinerancia en una red de telefonía móvil.|Sí|

### Configuración de funcionalidades del dispositivo: características

|Nombre de la configuración|Detalles|iOS|
|----------------|-------|
|**Permitir Siri**|Permite el uso del asistente de voz Siri en el dispositivo.|Sí|
|**Permitir Siri con el dispositivo bloqueado**|Permite el uso del asistente de voz Siri en el dispositivo aunque esté bloqueado.|Sí|
|**Permitir la marcación por voz**|Permite el uso de la característica de marcación por voz en el dispositivo.|Sí|


### Configuración de aplicaciones conformes y no conformes
En la lista de **aplicaciones compatibles&amp; y no compatibles**, especifique las aplicaciones que son compatibles y no compatibles con la siguiente información:

> [!NOTE]
> Una única directiva solo puede contener una lista de aplicaciones conformes o una lista de aplicaciones no conformes. No se pueden especificar ambas en la misma directiva.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Notificar la no compatibilidad cuando los usuarios instalan las aplicaciones de la lista**|Enumera las aplicaciones que no se administran mediante Intune y que los usuarios no pueden instalar ni ejecutar.|
|**No informar de incompatibilidad cuando los usuarios instalan las aplicaciones enumeradas.**|Enumera las aplicaciones que los usuarios pueden instalar. Para mantener la conformidad, los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.|
|**Agregar**|Agrega una aplicación a la lista seleccionada. Especifique un nombre de su elección, opcionalmente el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones. Lea **Cómo especificar las direcciones URL de tiendas de aplicaciones** más adelante en este tema para obtener más ayuda.|
|**Importar aplicaciones**|Importa la lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. Utilice el formato, nombre de la aplicación, editor, dirección URL de la aplicación en el archivo.|
|**Editar**|Permite editar el nombre, el editor y la dirección URL de la aplicación seleccionada.|
|**Eliminar**|Elimina la aplicación seleccionada de la lista.|

### Configuración del modo de pantalla completa

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Seleccione una aplicación administrada que se permitirá ejecutar cuando el dispositivo esté en modo de quiosco**|Haga clic en **Examinar**y, a continuación, especifique la aplicación administrada, o una aplicación de una tienda que se podrá ejecutar cuando el dispositivo esté en modo de quiosco. Ninguna otra aplicación se podrá ejecutar en el dispositivo. Para obtener más información, vea **Cómo especificar las direcciones URL de tiendas de aplicaciones** más adelante en este tema.|
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
> [!NOTE] Las siguientes notas se aplican a la configuración del modo de quiosco para dispositivos iOS:
> 
> -   Antes de configurar un dispositivo iOS para el modo de quiosco, debe usar la [herramienta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) o el administrador de inscripción de dispositivos para ajustar el dispositivo en el modo de supervisión. Para obtener más información acerca de la herramienta Apple Configurator, consulte la documentación de Apple.
> -   Si la aplicación de iOS que especifique se instala después de implementar la directiva de configuración, el dispositivo no pasará al modo de quiosco hasta que se reinicie.

### Información de referencia para las aplicaciones conformes y no conformes

#### Supervisar las aplicaciones conformes y no conformes
Utilice el **Informe de aplicaciones no conformes** para ver la conformidad de las aplicaciones permitidas y bloqueadas.

##### Para ejecutar el informe de aplicaciones no conformes

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Informes** &gt; **Informe de aplicaciones no conformes**.

2.  Seleccione los grupos de dispositivos que quiere comprobar, si quiere comprobar las aplicaciones conformes, las aplicaciones no conformes o ambas y, a continuación, haga clic en **Ver informe**.

#### Cómo especificar las direcciones URL de tiendas de aplicaciones
Para especificar una dirección URL de aplicación en la lista de aplicaciones conformes y no conformes o en la opción **Seleccione una aplicación administrada que se podrá ejecutar cuando el dispositivo esté en modo de pantalla completa** (solo iOS), use el siguiente formato:

Con la ayuda de un motor de búsqueda, busque la aplicación que desea usar en iTunes App Store y abra la página de la aplicación.

Copie la dirección URL de la página y úsela como dirección URL para configurar la lista de aplicaciones conformes y no conformes o la aplicación que desea ejecutar en modo de quiosco.

**Ejemplo:** Busque **Microsoft Word para iPad**. La dirección URL que use será **https://itunes.apple.com/es/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE] También puede usar el software de iTunes para encontrar la aplicación y, después, usar el comando **Copiar vínculo** para obtener la dirección URL de la aplicación.


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
|**Archivo del perfil de configuración**|Haga clic en **Importar**y luego examine el perfil de configuración que ha creado con Apple Configurator. **Nota:** Asegúrese de que la configuración que exporta de la herramienta Apple Configurator sea compatible con la versión de iOS en los dispositivos en los que implementa la directiva personalizada de iOS. Para obtener información sobre la resolución de las opciones de configuración incompatibles, busque la **referencia de perfiles de configuración** y la **referencia del protocolo de administración de dispositivos móviles** en el sitio web para [desarrolladores de Apple](https://developer.apple.com/).|
    |**Detalles del perfil de configuración**|Muestra el código XML del perfil de configuración que ha importado.|

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO2-->


