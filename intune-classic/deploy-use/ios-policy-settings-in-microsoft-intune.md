---
title: "Configuración de directivas de iOS"
description: "Cree directivas que controlen la configuración y las características en los dispositivos iOS que administra con Intune."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 11/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e9d014eb504098ff4361add7a0f3715f33be9083
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="ios-policy-settings-in-microsoft-intune"></a>Configuración de directivas de iOS en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune proporciona una variedad de opciones generales integradas que puede configurar en los dispositivos iOS. Además, puede usar la herramienta Apple Configurator para crear una configuración personalizada que no esté disponible en Intune.

## <a name="general-configuration-policy-settings"></a>Configuración general de directivas

Use la **directiva de configuración general de iOS** de Microsoft Intune para configurar las siguientes opciones:

-   **Configuración general de dispositivos y seguridad**. Elija entre las opciones de una lista de configuraciones predefinidas que permiten controlar diversas características y funcionalidades en el dispositivo.

-   **Pantalla completa**. Bloquee un dispositivo para permitir que solo funcionen determinadas características. Por ejemplo, puede permitir que un dispositivo ejecute solo una aplicación administrada que especifique, o puede deshabilitar los botones de volumen de un dispositivo. Esta configuración podría usarse para un modelo de demostración de un dispositivo o para un dispositivo que está dedicado a realizar solo una función, como un dispositivo de punto de venta.

-   **Aplicaciones conformes y no conformes**. Especifique una lista de las aplicaciones conformes y no conformes en su empresa. En los dispositivos iOS y Android, el **Informe de aplicaciones no conformes** puede usarse para comparar la conformidad de las aplicaciones especificadas en la lista con las aplicaciones que los usuarios han instalado (pero en realidad no pueden bloquear la instalación de la aplicación).

> [!TIP]
> Puede configurar los términos y condiciones de los usuarios para asegurarse de que saben que las aplicaciones de su dispositivo (incluidas las aplicaciones personales) se evaluarán y que las aplicaciones no conformes se bloquearán o se notificarán como no conformes. Los usuarios deben aceptar estos términos y condiciones para poder inscribir su dispositivo y utilizar el portal de empresa para obtener aplicaciones. Para obtener más información sobre el uso de los términos y condiciones, consulte [Configuración de la directiva de términos y condiciones en Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Si el valor que busca no aparece en este tema, puede crearlo mediante una directiva personalizada de iOS que le permita importar la configuración creada con la [herramienta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Para obtener más información, consulte "Configuración de directivas personalizadas" más adelante en este tema.

### <a name="security-settings"></a>Configuración de seguridad
Todas las configuraciones se aplican a iOS 8.0 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Requerir una contraseña para desbloquear dispositivos móviles**|Especificar si el usuario tiene que escribir una contraseña para obtener acceso al dispositivo.|
|**Tipo de contraseña obligatoria**|Especificar el tipo de contraseña que será necesario, como solo numérica o alfanumérica.|
|**Número de caracteres complejos necesarios en la contraseña**|Especificar el número de caracteres de símbolos (como **#** o **@**) que deben incluirse en la contraseña.|
|**Longitud mínima de contraseña**|Especificar el número mínimo de caracteres de la contraseña.|
|**Permitir contraseñas sencillas**|Permitir contraseñas sencillas como **0000** y **1234**.|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Especificar el número de intentos de inicio de sesión con error antes de que esta configuración borre el dispositivo.|
|**Minutos de inactividad antes de que sea necesaria la contraseña**<sup>1</sup>|Especificar cuánto tiempo puede permanecer inactivo el dispositivo antes de que el usuario deba volver a escribir su contraseña.|
|**Expiración de contraseña (días)**|Especificar el número de días antes de que se deba cambiar la contraseña del dispositivo.|
|**Recordar el historial de contraseñas**|Especificar si el usuario puede usar las contraseñas que ha usado anteriormente.|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Especificar el número de contraseñas usadas anteriormente que el dispositivo recuerda.|
|**Minutos de inactividad antes de que se apague la pantalla**<sup>1</sup>|Especifique el número de minutos antes de que la pantalla del dispositivo se apague.|
|**Permitir desbloqueo mediante huellas digitales**|Permite desbloquear el dispositivo mediante las huellas digitales.|
<sup>1</sup> En los dispositivos iOS, cuando configura las opciones **Minutos de inactividad antes de que se apague la pantalla** y **Minutos de inactividad antes de que sea necesaria la contraseña**, se aplican en secuencia. Por ejemplo, si establece el valor para ambas opciones en **5** minutos, la pantalla se apagará automáticamente transcurridos 5 minutos y el dispositivo se bloqueará pasados 5 minutos más. Sin embargo, si el usuario apaga la pantalla manualmente, la segunda opción se aplica inmediatamente. En el mismo ejemplo, una vez que el usuario apague la pantalla, el dispositivo se bloqueará 5 minutos más tarde.

### <a name="system-settings"></a>Configuración del sistema
Todas las configuraciones se aplican a iOS 8.0 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir capturas de pantalla**|Permitir al usuario capturar el contenido de la pantalla como una imagen.|
|**Permitir centro de control en la pantalla de bloqueo**|Permitir al usuario tener acceso a la aplicación Centro de control mientras el dispositivo está bloqueado.|
|**Permitir vista de notificaciones en la pantalla de bloqueo**|Permite el acceso del usuario a la vista de notificaciones sin que sea necesario desbloquear el dispositivo.|
|**Permitir vista de hoy en la pantalla de bloqueo**|Permitir al usuario ver las notificaciones cuando el dispositivo está bloqueado.|
|**Permitir certificados TLS que no son de confianza**|Permite el uso en el dispositivo de certificados de seguridad de la capa de transporte que no son de confianza.|
|**Permitir el envío de datos de diagnóstico**|Permite o impide que el dispositivo envíe datos de diagnóstico a Apple.|
|**Permitir libreta con dispositivo bloqueado**|Permite al usuario tener acceso a la aplicación Libreta mientras el dispositivo está bloqueado.|

### <a name="cloud-settings-for-documents-and-data"></a>Configuración de nube para documentos y datos
Todas las configuraciones se aplican a iOS 8.0 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir copias de seguridad en iCloud**|Permitir al usuario hacer copias de seguridad del dispositivo en iCloud.|
|**Permitir sincronización de documentos en iCloud**|Permite la sincronización de clave-valor y documentos en el espacio de almacenamiento de iCloud.|
|**Permitir sincronización de Photo Stream en iCloud**|Permita que los usuarios habiliten **My Photo Stream** en su dispositivo que permite que las fotos se sincronicen en iCloud y estén disponibles para todos los dispositivos de usuario.|
|**Requerir copia de seguridad cifrada**|Requiere que las copias de seguridad del dispositivo se cifren.|
|**Permitir que las aplicaciones administradas sincronicen datos en iCloud**|Permitir que las aplicaciones que se administran con Intune sincronicen los datos con la cuenta de iCloud del usuario.|
|**Permitir la entrega para continuar las actividades en otro dispositivo**|Permitir al usuario continuar el trabajo iniciado en un dispositivo iOS en otro dispositivo iOS o MAC OS X.|
|**Permitir el uso compartido de fotografías de iCloud**|Establezca **No** para deshabilitar **Fotos compartidas en iCloud** en el dispositivo.|
|**Permitir la biblioteca de fotografías de iCloud**|Si se establece en **No**, deshabilita el uso de la Fototeca de iCloud que permite a los usuarios almacenar fotos y vídeos en la nube.   Las fotos que no se hayan descargado completamente de la Fototeca de iCloud al dispositivo se quitarán de este si esta opción se establece en **No**.|

### <a name="application-settings-for-the-browser"></a>Configuración de la aplicación para el explorador
Todas las configuraciones se aplican a iOS 8.0 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir Safari**|Especifica si se puede usar el explorador Safari en el dispositivo.|
|**Permitir el autorrelleno**|Permitir al usuario cambiar la configuración de Autocompletar en el explorador.|
|**Permitir bloqueador de elementos emergentes**|Habilita o deshabilita el bloqueador de elementos emergentes del explorador.|
|**Permitir cookies**|Permitir que el explorador use cookies.|
|**Permitir scripting de Java**|Permite que los scripts de Java se ejecuten en el explorador.|
|**Permitir advertencias de fraude**|Permitir mostrar advertencias de fraude en el explorador.|

### <a name="application-settings-for-apps"></a>Configuración de la aplicación para aplicaciones
Todas las configuraciones se aplican a iOS 8.0 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir la instalación de aplicaciones**|Permitir que el dispositivo tenga acceso a la tienda de aplicaciones y que instale aplicaciones.|
|**Requerir una contraseña para tener acceso al almacén de aplicaciones**|Requerir al usuario que escriba una contraseña antes de que pueda visitar la tienda de aplicaciones.|
|**Permitir compras dentro de la aplicación**|Permite realizar compras en la tienda desde una aplicación en ejecución.|
|**Permitir documentos administrados en otras aplicaciones no administradas**|Esta opción permite la visualización de documentos corporativos en cualquier aplicación.<br>**Ejemplo:** Quiere evitar que los usuarios guarden archivos de la aplicación OneDrive en Dropbox. Configure este ajuste en no. Después de que el dispositivo reciba la directiva (por ejemplo, después de un reinicio), ya no le permitirá guardar.|
|**Permitir documentos no administrados en otras aplicaciones administradas**|Permite la visualización de cualquier documento en aplicaciones administradas corporativas.|
|**Permitir videoconferencias**|Permitir el uso de aplicaciones de videoconferencia como FaceTime en el dispositivo.|
|**Permitir que el usuario confíe en nuevos autores de aplicaciones empresariales**|Permite que el usuario confíe en aplicaciones que no se han descargado en la tienda de aplicaciones.|


### <a name="application-settings-for-games"></a>Configuración de la aplicación para juegos
Todas las configuraciones se aplican a iOS 8.0 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir agregar amigos al centro de juegos**|Permite al usuario agregar a amigos del centro de juegos.|
|**Permitir juegos multijugador**|Permite al usuario jugar a juegos multijugador en el dispositivo.|

### <a name="application-settings-for-media-content"></a>Configuración de aplicación para el contenido multimedia
Todas las configuraciones se aplican a iOS 8.0 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Región de clasificación**|Seleccione una región y, luego, la clasificación máxima que los usuarios pueden descargar para **Películas**, **Programas de TV** y **Aplicaciones**.|
|**Permitir contenido para adultos en el almacén multimedia**|Permite que el dispositivo tenga acceso a contenido clasificado para adultos en la tienda.|
|**Permite al usuario descargar contenido desde la tienda de iBooks marcada como "Erótico"**|Permitir al usuario descargar libros con la categoría "Erotismo".|


### <a name="device-capabilities-settings-for-hardware"></a>Configuración de funcionalidades del dispositivo para hardware
Todas las configuraciones se aplican a iOS 8.0 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir cámara**|Especificar si se puede usar la cámara del dispositivo.|
|**Forzar a los dispositivos Apple Watch enlazados a usar la detección de muñeca**|Si se habilita, el dispositivo Apple Watch no mostrará notificaciones si no se lleva puesto.|
|**Requerir una contraseña de emparejamiento para las solicitudes salientes de AirPlay**|Requerir una contraseña de emparejamiento cuando el usuario usa AirPlay para transmitir contenido a otros dispositivos de Apple.|

### <a name="device-capabilities-settings-for-cellular"></a>Configuración de funcionalidades del dispositivo para red de telefonía móvil
Todas las configuraciones se aplican a iOS 8.0 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir itinerancia de voz**|Permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.|
|**Permitir itinerancia de datos**|Permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.|
|**Permitir captura de fondo global durante la itinerancia**|Permite al dispositivo capturar datos (por ejemplo, correo electrónico) mientras está en itinerancia en una red de telefonía móvil.|

### <a name="device-capabilities-settings-for-features"></a>Configuración de funcionalidades del dispositivo para características
Todas las configuraciones se aplican a iOS 8.0 y posterior.

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Permitir Siri**|Permite el uso del asistente de voz Siri en el dispositivo.|
|**Permitir Siri con el dispositivo bloqueado**|Permite el uso del asistente de voz Siri en el dispositivo aunque esté bloqueado.|
|**Permitir la marcación por voz**|Permite el uso de la característica de marcación por voz en el dispositivo.|
|**No permitir Airdrop con aplicaciones administradas**|Las aplicaciones administradas ya no pueden enviar datos a través de Airdrop.|


### <a name="settings-for-compliant-and-noncompliant-apps"></a>Configuración de aplicaciones conformes y no conformes
En la lista de **Aplicaciones conformes y no conformes**, especifique las aplicaciones que son conformes y no conformes con la siguiente información.

> [!NOTE]
> Una única directiva solo puede contener una lista de aplicaciones conformes o una lista de aplicaciones no conformes. No se pueden especificar ambas en la misma directiva.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Notificar la no compatibilidad cuando los usuarios instalan las aplicaciones de la lista**|Enumerar las aplicaciones (que no se administran mediante Intune) que los usuarios no pueden instalar ni ejecutar.|
|**Informar sobre la incompatibilidad cuando los usuarios instalen aplicaciones no enumeradas**|Enumerar las aplicaciones que los usuarios pueden instalar. Para mantener la conformidad, los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.|
|**Agregar**|Agregar una aplicación a la lista seleccionada. Especifique un nombre de su elección, opcionalmente el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones. Lea "Cómo especificar las direcciones URL de tiendas de aplicaciones" más adelante en este tema para obtener más ayuda.|
|**Importar aplicaciones**|Importar una lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. En el archivo, use este formato: nombre de la aplicación, editor, dirección URL de la aplicación.|
|**Editarar**|Editar el nombre, el editor y la dirección URL de la aplicación seleccionada.|
|**Eliminar**|Eliminar la aplicación seleccionada de la lista.|

Las directivas que contienen ajustes de aplicaciones compatibles y no compatibles se deben implementar en los grupos de usuarios.

### <a name="kiosk-mode-settings"></a>Configuración del modo de pantalla completa

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
> -   Antes de configurar un dispositivo iOS para pantalla completa, debe usar la [herramienta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) o el [Programa de Inscripción de Dispositivos de Apple](ios-device-enrollment-program-in-microsoft-intune.md) para pasar el dispositivo al modo supervisado. Para obtener más información sobre la herramienta Apple Configurator, consulte la documentación de Apple.
> -   Si la aplicación de iOS que especifique se instala después de implementar la directiva de configuración, el dispositivo no pasará a pantalla completa hasta que se reinicie.

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>Información de referencia para las aplicaciones conformes y no conformes

Utilice el **Informe de aplicaciones no conformes** para ver la conformidad de las aplicaciones permitidas y bloqueadas.

##### <a name="to-run-the-noncompliant-apps-report"></a>Para ejecutar el informe de aplicaciones no conformes

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Informes** &gt; **Informe de aplicaciones no conformes**.

2.  Seleccione los grupos de dispositivos que quiere comprobar, si quiere comprobar las aplicaciones conformes, las aplicaciones no conformes o ambas y, después, elija **Ver informe**.

#### <a name="how-to-specify-urls-to-app-stores"></a>Cómo especificar las direcciones URL de tiendas de aplicaciones
Para especificar una dirección URL de aplicación en la lista de aplicaciones conformes y no conformes o en la opción **Seleccione una aplicación administrada que se podrá ejecutar cuando el dispositivo esté en modo de pantalla completa** (solo iOS), use el siguiente formato:

1. Con la ayuda de un motor de búsqueda, busque la aplicación que quiere usar en iTunes App Store y abra la página de la aplicación.

2. Copie la dirección URL de la página y úsela como dirección URL para configurar la lista de aplicaciones conformes y no conformes o la aplicación que quiere ejecutar en pantalla completa.

**Ejemplo:** Busque **Microsoft Word para iPad**. La dirección URL que debe usar es **https://itunes.apple.com/es/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> También puede utilizar el software de iTunes para encontrar la aplicación y, a continuación, utilizar el comando **Copiar vínculo** para obtener la dirección URL de la aplicación.

### <a name="enrollment-settings"></a>Configuración de la inscripción
Todas las configuraciones se aplican a iOS 8.0 y posterior.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Permitir bloqueo de activación cuando el dispositivo está en modo supervisado**|Permitir bloqueo de activación en dispositivos iOS supervisados.|

### <a name="supervised-mode-settings"></a>Configuración del modo supervisado
Puede configurar las siguientes opciones en dispositivos con iOS 8.0 y posterior que estén en modo supervisado.

### <a name="supervised-mode-settings-for-device-restrictions"></a>Configuración del modo supervisado para las restricciones de dispositivos

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Permitir la modificación de la cuenta**|Permite al usuario cambiar la configuración de la cuenta, como las configuraciones de correo electrónico.|
|**Permitir cambios en la configuración de uso de datos móviles de la aplicación**|Permite al usuario controlar qué aplicaciones pueden utilizar datos móviles.|
|**Permitir el uso de la opción de borrado de todo el contenido y configuración en el dispositivo**|Permitir al usuario usar la opción de borrar todo el contenido y la configuración del dispositivo.|
|**Permitir al usuario habilitar las restricciones en la configuración del dispositivo**|Permitir al usuario configurar restricciones de dispositivos (controles parentales) en el dispositivo.|
|**Permitir el emparejamiento de host para controlar los dispositivos que puede emparejar un dispositivo iOS**|Permitir que el emparejamiento de host permita al administrador controlar con qué dispositivos se puede emparejar un dispositivo iOS.|
|**Permitir al usuario que instale certificados y perfiles de configuración**|Permite al usuario que instale certificados y perfiles de configuración.|
|**Permitir modificar el nombre del dispositivo**|Permitir que el usuario cambie el nombre del dispositivo.|
|**Permitir cambiar código de acceso**|Permitir que se agregue, se cambie o se quite la contraseña del dispositivo.|
|**Permitir enlace con Apple Watch**|Permitir que el dispositivo se empareje con un dispositivo Apple Watch.|
|**Permitir modificar la configuración de notificaciones**|Permitir que el usuario cambie la configuración de las notificaciones del dispositivo.|
|**Permitir modificar fondo de pantalla**|Permitir que el usuario cambie el fondo de pantalla del dispositivo.|

### <a name="supervised-mode-settings-for-feature-restrictions"></a>Configuración del modo supervisado para las restricciones de características

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Permitir AirDrop**|Permitir el uso de la característica AirDrop para intercambiar el contenido con dispositivos cercanos.|
|**Permitir Siri para consultar el contenido generado por el usuario de Internet**|Permitir que Siri tenga acceso a sitios web para responder a preguntas.|
|**Usar filtro de obscenidad de Siri**|Evita que Siri dicte o hable con un lenguaje malsonante.|
|**Permitir la búsqueda de Spotlight para devolver resultados de Internet**|Permitir que la búsqueda de Spotlight se conecte a Internet para proporcionar más resultados.|
|**Permitir búsqueda de definiciones de palabras**|Permitir la característica de iOS que le permite resaltar una palabra y buscar su definición.|
|**Permitir teclados predictivos**|Permitir el uso de teclados predictivos que sugieren posibles palabras que el usuario podría buscar.|
|**Permitir corrección automática**|Permite que el dispositivo corrija automáticamente palabras mal escritas.|
|**Permitir revisión ortográfica de teclado**|Permite el uso del corrector ortográfico del dispositivo.|
|**Permitir métodos abreviados de teclado**|Permite el uso de métodos abreviados de teclado.|

### <a name="supervised-mode-settings-for-app-restrictions"></a>Configuración del modo supervisado para las restricciones de aplicaciones

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Permitir modificar la configuración de confianza de aplicaciones empresariales**|Permite a los usuarios cambiar la configuración de confianza de las aplicaciones empresariales.|
|**Permitir la instalación de aplicaciones solo con Apple Configurator y iTunes**|Habilita o deshabilita la Tienda de aplicaciones desde la pantalla de inicio del dispositivo. Los usuarios pueden seguir usando iTunes o la herramienta Apple Configurator para instalar y actualizar aplicaciones.|
|**Permitir descargas de aplicaciones automáticas**|Permite descargar automáticamente aplicaciones adquiridas en otros dispositivos en este. Esta opción no afecta a las actualizaciones de las aplicaciones.|
|**Permitir cambios en la configuración de la aplicación para buscar a sus amigos**|Permite al usuario cambiar la configuración de la aplicación para buscar a sus amigos.|
|**Permitir el acceso a la tienda de iBooks**|Permite al usuario examinar y comprar libros desde la tienda de iBooks.|
|**Permitir el uso de la aplicación de mensajes en el dispositivo**|Permite el uso de la aplicación de mensajes en el dispositivo.|
|**Permitir el uso de Podcasts**|Permitir el uso de la aplicación Podcasts.|
|**Permitir el uso del servicio Music**|Permitir el uso de la aplicación Apple Music.|
|**Permitir el servicio Radio de iTunes**|Permitir el uso de la aplicación Radio de iTunes.|
|**Permitir Apple News**|Permitir el uso de la aplicación Apple News.|
|**Permitir Game Center**|Permite el uso de la aplicación Centro de juegos.|


### <a name="show-or-hide-apps"></a>Mostrar u ocultar aplicaciones

Use la **Lista de aplicaciones ocultas y visibles** para controlar las siguientes opciones en los dispositivos supervisados que ejecutan iOS 9.3 o versiones posteriores:

- Especificar una lista de las aplicaciones ocultas para los usuarios. Los usuarios no pueden ver ni iniciar estas aplicaciones.
- Especificar una lista de las aplicaciones que los usuarios pueden ver e iniciar. No se puede ver ni iniciar ninguna otra aplicación.


#### <a name="how-to-create-a-hidden-or-shown-app-list"></a>Cómo crear una lista de aplicaciones ocultas y visibles

Especifique las siguientes opciones:

|Nombre de la configuración|Detalles|
|-|-|
|**Lista de aplicaciones ocultas y visibles**|Habilite esta opción si quiere crear una lista de aplicaciones ocultas o visibles.|
|**Ocultar las aplicaciones de la lista a los usuarios**|Seleccione esta opción si quiere crear una lista de aplicaciones que permanecerán ocultas para los usuarios.<br>Cuando cree este tipo de lista, todas las demás aplicaciones pueden estar ocultas; excepto para las aplicaciones **Configuración** y **Teléfono** (para iPhone) de iOS.|
|**Mostrar solo las aplicaciones de la lista a los usuarios**|Seleccione esta opción si quiere crear una lista de aplicaciones que se muestre a los usuarios.<br>Cuando cree este tipo de lista, todas las demás aplicaciones están ocultas; excepto para las aplicaciones **Configuración** y **Teléfono** (para iPhone) de iOS.<br>Además, debe agregar el Portal de empresa, y cualquier aplicación que haya implementado, y administrarlo con Intune para la lista.|
|**Agregar**|Agrega una aplicación a la lista seleccionada.<br>Para la lista oculta, debe especificar el **Nombre**, **Publicador** y **Dirección URL de aplicación o id. de lote de aplicaciones** de cada aplicación que quiera ocultar.<br>Para la lista que se muestra, puede **Seleccionar una aplicación administrada** que le proporciona una lista de las aplicaciones que administra con Intune para seleccionarlas, o bien Seleccionar aplicación de tienda, donde debe especificar el **Nombre**, **Publicador** y **Dirección URL de aplicación o id. de lote de aplicaciones** de cada aplicación que quiere mostrar.|
|**Importar aplicaciones**|Importa la lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. Utilice el formato, nombre de la aplicación, editor, dirección URL de la aplicación en el archivo.|
|**Editarar**|Permite editar el nombre, el editor y la dirección URL de la aplicación seleccionada.|
|**Eliminar**|Elimina la aplicación seleccionada de la lista.|

#### <a name="app-information-for-built-in-ios-apps"></a>Información de aplicaciones para las aplicaciones integradas de iOS

Use la información de esta lista para identificar el nombre, el publicador y el identificador de lote de aplicaciones de las aplicaciones integradas de iOS que quiere mostrar u ocultar. Si quiere mostrar u ocultar todas las aplicaciones de la lista, puede copiar los datos siguientes en un archivo de texto con la extensión **.csv** y, después, usar la opción **Importar aplicaciones** para importar todas las aplicaciones a la vez.

```
,com.apple.AppStore,App Store,Apple
,com.apple.calculator,Calculator,Apple
,com.apple.mobilecal,Calendar,Apple
,com.apple.camera,Camera,Apple
,com.apple.mobiletimer,Clock,Apple
,com.apple.compass,Compass,Apple
,com.apple.MobileAddressBook,Contacts,Apple
,com.apple.facetime,FaceTime,Apple
,com.apple.mobileme.fmf1,Find Friends,Apple
,com.apple.mobileme.fmip1,Find iPhone,Apple
,com.apple.gamecenter,Game Center,Apple
,com.apple.mobilegarageband,GarageBand,Apple
,com.apple.Health,Health,Apple
,com.apple.iBooks,iBooks,Apple
,com.apple.MobileStore,iTunes Store,Apple
,com.apple.itunesu,iTunes U,Apple
,com.apple.Keynote,Keynote,Apple
,com.apple.mobilemail,Mail,Apple
,com.apple.MapsMaps,Apple
,com.apple.MobileSMS,Messages,Apple
,com.apple.Music,Music,Apple
,com.apple.news,News,Apple
,com.apple.mobilenotes,Notes,Apple
,com.apple.Numbers,Numbers,Apple
,com.apple.Pages,Pages,Apple
,com.apple.Photo-Booth,Photo Booth,Apple
,com.apple.mobileslideshow,Photos,Apple
,com.apple.podcasts,Podcasts,Apple
,com.apple.reminders,Reminders,Apple
,com.apple.MobileSafari,Safari,Apple
,com.apple.Preferences,Settings,Apple
,com.apple.stocks,Stocks,Apple
,com.apple.tips,Tips,Apple
,com.apple.videos,Videos,Apple
,com.apple.VoiceMemos,VoiceMemos,Apple
,com.apple.Passbook,Wallet,Apple
,com.apple.Bridge,Watch,Apple
,com.apple.weather,Weather,Apple


```




## <a name="custom-policy-settings"></a>Configuración de directivas personalizadas

Use la **Directiva personalizada para iOS** de Microsoft Intune para implementar la configuración que ha creado mediante la [herramienta Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) en dispositivos iOS. Esta herramienta permite crear muchas configuraciones para controlar el funcionamiento de estos dispositivos y exportarlas a un perfil de configuración. A continuación, puede importar este perfil de configuración en una directiva personalizada de iOS de Intune e implementar la configuración para los usuarios y dispositivos de su organización.

Esta funcionalidad permite implementar la configuración de iOS que no se puede configurar con directivas de configuración general de Intune.

### <a name="prerequisites"></a>Requisitos previos
Antes de empezar, debe tener instalado Apple Configurator y haber creado un archivo de configuración que contenga la configuración que quiere implementar en usuarios o dispositivos. Puede descargar Apple Configurator y obtener información sobre esta aplicación en [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12).

> [!NOTE]
> Intune no notifica el cumplimiento de opciones de configuración individuales de una directiva personalizada de iOS. Sin embargo, se notifica el cumplimiento general de la directiva.

### <a name="general-settings"></a>Configuración general

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre**|Escriba un nombre único para la directiva personalizada de iOS que le ayude a identificarla en la consola de Intune.|
    |**Descripción**|Proporcione una descripción que ofrezca una visión general de la directiva personalizada de iOS y otra información relevante que le ayude a encontrarla.|

### <a name="custom-settings"></a>Configuración personalizada

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
|**Nombre del perfil de configuración personalizada (que se muestra a los usuarios)**|Proporcione el nombre de la directiva que se mostrará en el dispositivo y en los informes de directivas de Intune.|
|**Archivo del perfil de configuración**|Elija **Importar** y, luego, examine el perfil de configuración que ha creado con Apple Configurator. **Nota:** Asegúrese de que la configuración que exporta de la herramienta Apple Configurator sea compatible con la versión de iOS en los dispositivos en los que implementa la directiva personalizada de iOS. Para obtener información sobre la resolución de las opciones de configuración incompatibles, busque la **Referencia de perfiles de configuración** y la **Referencia del protocolo de administración de dispositivos móviles** en el sitio web de [Apple Developer](https://developer.apple.com/).|
    |**Detalles del perfil de configuración**|Mostrar el código XML del perfil de configuración que ha importado.|

### <a name="see-also"></a>Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
