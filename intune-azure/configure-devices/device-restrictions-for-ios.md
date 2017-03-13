---
title: "Configuración de restricciones de dispositivos de Intune para iOS"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: conozca los valores de configuración de Intune que puede usar para controlar la configuración y la funcionalidad de los dispositivos iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73590192-54ca-4833-9f1d-83e1b654399f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: a062b92cba0042153ffe22b949ce8a3b7b740b3f
ms.lasthandoff: 02/18/2017


---

# <a name="ios-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos iOS en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>General
-     **Cámara**: seleccione si se puede usar la cámara del dispositivo.     
-     **Envío de datos de diagnóstico**: permite o impide que el dispositivo envíe datos de diagnóstico a Apple.
-     **FaceTime**: permite el uso de la aplicación FaceTime en el dispositivo.
-     **Captura de pantalla**: permite que el usuario capture el contenido de la pantalla como una imagen.
-     **Siri**: permite el uso del asistente de voz Siri en el dispositivo.
    -     **Siri con dispositivo bloqueado**: permite el uso del asistente de voz Siri en el dispositivo aunque esté bloqueado.
    -     **Filtro de obscenidad de Siri (solo supervisado)**: evita que Siri dicte o hable con un lenguaje obsceno.
    -     **Consulta de Siri de contenido generado por usuarios de Internet (solo supervisada)**: permite que Siri acceda a sitios web para responder a preguntas.
-     **Certificados TLS que no son de confianza**: permite certificados de Seguridad de capa de transporte en los que no se confía en el dispositivo.
-     **Acceso al centro de control con dispositivo bloqueado**: permite al usuario acceder a la aplicación del centro de control cuando el dispositivo está bloqueado.
-     **Notificaciones con dispositivo bloqueado**: permite al usuario acceder a la vista de notificaciones sin desbloquear el dispositivo.
-     **Permitir libreta con dispositivo bloqueado**: permite al usuario acceder a la aplicación Libreta mientras el dispositivo está bloqueado.
-     **Vista de hoy con dispositivo bloqueado**: permite al usuario ver la vista del día de hoy cuando el dispositivo está bloqueado.
-     **Confianza de aplicaciones empresariales**: permite que el usuario confíe en aplicaciones que no se descargaron de la tienda de aplicaciones.
-     **AirDrop (solo supervisado)**: permite que el usuario de la característica AirDrop intercambie contenido con dispositivos cercanos.
-     **Búsqueda de Spotlight para devolver resultados de Internet (solo supervisada)**: permite que la búsqueda de Spotlight se conecte a Internet para obtener más resultados.
-     **Búsqueda de definiciones de palabras (solo supervisada)**: permite la característica de iOS que le deja resaltar una palabra y buscar su definición.
-     **Teclados predictivos (solo supervisados)**: permite el uso de teclados predictivos que sugieren palabras que el usuario podría buscar.
-     **Autocorrección (solo supervisada)**: permite que el dispositivo corrija automáticamente las palabras mal escritas.
-     **Revisión ortográfica de teclado (solo supervisada)**: permite el corrector ortográfico del dispositivo.
-     **Métodos abreviados de teclado (solo supervisados)**: permite el uso de métodos abreviados de teclado.
-     **Detección de muñeca para Apple Watch enlazado**: cuando se habilita, Apple Watch no muestra notificaciones si no se lleva puesto.
- **Requerir contraseña de emparejamiento para solicitudes salientes de AirPlay**: solicita una contraseña de emparejamiento cuando el usuario usa AirPlay para transmitir contenido a otros dispositivos Apple.
- **Modificación de la cuenta (solo supervisado)**: permite al usuario cambiar la configuración de la cuenta, como las configuraciones del correo electrónico.
- **Emparejamiento con Apple Watch (solo supervisado)**: permite al dispositivo emparejarse con un dispositivo Apple Watch.
- **Modificación de Bluetooth (solo supervisado)**: impide al usuario cambiar la configuración de Bluetooth del dispositivo.
- **Observación de pantalla remota mediante la aplicación Classroom (solo supervisado)**: permite o impide que la aplicación Classroom observe la pantalla en dispositivos remotos.
- **Habilitación de restricciones en la configuración del dispositivo (solo supervisado)**: permite al usuario configurar restricciones (controles parentales) en el dispositivo.
- **Uso de la opción de borrar todo el contenido y la configuración del dispositivo (solo supervisado)**: permite que el usuario use la opción de borrar todo el contenido y la configuración del dispositivo.
- **Modificación del nombre del dispositivo (solo supervisado)**: permite que el usuario cambie el nombre del dispositivo.
- **Modificación de la configuración de envío de diagnósticos (solo supervisado)**: permite o impide que el dispositivo envíe datos de diagnóstico a Apple.
- **Emparejamiento de host para controlar los dispositivos con los que se puede emparejar un dispositivo iOS (solo supervisado)**: permite el emparejamiento de host para dejar que el administrador controle con qué dispositivos se puede emparejar un dispositivo iOS.
- **Modificación de la configuración de notificaciones (solo supervisado)**: permitir al usuario cambiar la configuración de notificación del dispositivo.
- **Modificación del código de acceso (solo supervisado)**: permite agregar, cambiar o quitar la contraseña del dispositivo.
- **Modificación del fondo de pantalla (solo supervisado)**: permite al usuario cambiar el fondo de pantalla del dispositivo.
- **Modificación de la configuración de confianza de aplicaciones empresariales (solo supervisado)**: permite que el usuario confíe en aplicaciones que no se descargaron de la tienda de aplicaciones.
- **Instalación de aplicaciones de App Store (solo supervisado)**: permite que el dispositivo acceda a la tienda de aplicaciones e instale aplicaciones.
- **Cambios en la configuración de la aplicación Buscar a mis amigos (solo supervisado)**: permite que el usuario cambiar la configuración de la aplicación Buscar a mis amigos.
- **Tienda iBooks (solo supervisado)**: permite que el usuario explore y compre libros de la tienda iBooks.
- **Aplicación Mensajes del dispositivo (solo supervisado)**: permite el uso de la aplicación Mensajes para enviar y leer mensajes de texto.
- **Podcasts (solo supervisado)**: permite el uso de la aplicación Podcasts.
- **Servicio Música (solo supervisado)**: permite el uso de la aplicación Música.
- **Servicio Radio de iTunes (solo supervisado)**: permite el uso de la aplicación Radio de iTunes.
- **Apple News (solo supervisado)**: permite el uso de la aplicación Apple News.
- **Cambios en el perfil de configuración**: permite al usuario instalar perfiles de configuración.

## <a name="password"></a>Contraseña
-     **Contraseña necesaria**: exige que el usuario final escriba una contraseña para acceder al dispositivo.
-     **Contraseñas sencillas**: permite contraseñas sencillas, como 0000 y 1234.
-     **Tipo de contraseña necesaria**: especifica el tipo de contraseña que es necesaria, como solo numérica o alfanumérica.
-     **Número de caracteres no alfanuméricos en la contraseña**: especifica el número de caracteres de símbolos (como **#** o **@**) que se deben incluir en la contraseña.
-     **Minimum password length** (Longitud mínima de contraseña): especifica el número mínimo de caracteres en la contraseña.
-     **Número de errores de inicio de sesión antes de borrar el dispositivo**: especifique el número de intentos de inicios de sesión erróneos antes de que esta configuración borre el dispositivo.
-     **Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña**<sup>1</sup>: especifique cuánto tiempo puede permanecer inactivo el dispositivo antes de que el usuario deba volver a escribir su contraseña.
-     **Máximo de minutos de inactividad hasta que se bloquea la pantalla**<sup>1</sup>: especifique el número de minutos antes de que la pantalla del dispositivo se apague.
-     **Caducidad de la contraseña (días)**: especifique el número de días antes de que deba cambiarse la contraseña del dispositivo.
-     **Impedir la reutilización de contraseñas anteriores**: especifique el número de contraseñas usadas anteriormente que el dispositivo puede recordar.
-     **Desbloqueo con huella digital**: permite el uso de una huella digital para desbloquear dispositivos compatibles.

<sup>1</sup>Al configurar los valores **Máximo de minutos de inactividad hasta que se bloquea la pantalla** y **Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña**, se aplican en secuencia. Por ejemplo, si establece el valor para ambas opciones en **5** minutos, la pantalla se apagará automáticamente transcurridos 5 minutos y el dispositivo se bloqueará pasados 5 minutos más. Sin embargo, si el usuario apaga la pantalla manualmente, la segunda opción se aplica inmediatamente. En el mismo ejemplo, una vez que el usuario apague la pantalla, el dispositivo se bloqueará 5 minutos más tarde.

## <a name="app-store-doc-viewing-gaming"></a>Tienda de aplicaciones, presentación de documentos, juegos


-   **Tienda de aplicaciones (solo supervisado)**: bloquea el acceso a la tienda de aplicaciones en dispositivos supervisados.
-     **Contraseña para acceder a la tienda de aplicaciones**: exige al usuario que escriba una contraseña antes de que pueda visitar la tienda de aplicaciones.
-     **Compras desde la aplicación**: permite realizar compras en la tienda desde una aplicación en ejecución.
-     **Descargas de aplicaciones automáticas (solo supervisado)** -
-     **Música, podcasts o contenido de noticias explícitos de iTunes (solo supervisado)**: permite que el dispositivo acceda a contenido clasificado como adulto en la tienda.
-     **Descargar contenido marcado como " Erótico" de la tienda iBooks**: permite que el usuario descargue libros de la categoría "Erótica".
-     **Visualización de documentos corporativos en aplicaciones no administradas**: permite la visualización de documentos corporativos en cualquier aplicación.<br>**Ejemplo:** Quiere evitar que los usuarios guarden archivos de la aplicación OneDrive en Dropbox. Configure este ajuste en no. Después de que el dispositivo reciba la directiva (por ejemplo, después de un reinicio), ya no le permitirá guardar.
-     **Visualización de documentos no corporativos en aplicaciones corporativas**: permite la visualización de cualquier documento en las aplicaciones administradas corporativas.
-     **Tratar AirDrop como destino no administrado**: impide que las aplicaciones administradas puedan enviar datos mediante Airdrop.
-     **Agregando amigos del Game Center (solo supervisado)**: permite que el usuario agregue amigos en Game Center.
-     **Game Center (solo supervisado)**: impide o permite el uso de la aplicación Game Center.
-     **Juegos multijugador (solo supervisado)**: permite al usuario jugar a juegos multijugador en el dispositivo.
-     **Región de clasificación**: elija la región de clasificación para la que quiere configurar descargas permitidas y luego elija la clasificación permitida para **Películas** y **Programas de TV**.
-     **Aplicaciones**: elija la clasificación por edades permitida de las aplicaciones que los usuarios podrán descargar. También puede elegir **Permitir todas las aplicaciones**.

## <a name="restricted-apps"></a>Aplicaciones restringidas

En la lista de aplicaciones restringidas, puede configurar una de las listas siguientes:

**Aplicaciones prohibidas**: aplicaciones (no administradas por Intune) que los usuarios no pueden instalar ni ejecutar.
**Aplicaciones aprobadas**: aplicaciones que los usuarios pueden instalar. Para mantener la conformidad, los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.

Para configurar la lista, haga clic en **Agregar** y especifique un nombre de su elección. Opcionalmente, puede indicar el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Especificación de la dirección URL para una aplicación de la tienda

Para especificar una dirección URL en la lista de aplicaciones, use el siguiente formato:

Con la ayuda de un motor de búsqueda, busque la aplicación que quiere usar en iTunes App Store y abra la página de la aplicación.
Copie la dirección URL de la página y úsela para configurar la lista de aplicaciones permitidas y prohibidas o una aplicación que quiera ejecutar en pantalla completa.
Se deben implementar perfiles de dispositivo que contengan configuración de aplicaciones restringidas para grupos de usuarios.

Ejemplo: busque Microsoft Word para iPad. La dirección URL que debe usar es https://itunes.apple.com/es/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> También puede utilizar el software de iTunes para encontrar la aplicación y, a continuación, utilizar el comando **Copiar vínculo** para obtener la dirección URL de la aplicación.



### <a name="additional-options"></a>Opciones adicionales

También puede hacer clic en **Importar** para rellenar la lista a partir de un archivo csv con el formato <*url de aplicación*>, <*nombre de aplicación*>, <*editor de aplicación*> o en **Exportar** para crear un archivo csv que contenga la lista de aplicaciones restringidas en el mismo formato.

## <a name="show-or-hide-apps"></a>Aplicaciones visibles u ocultas

En la lista de aplicaciones visibles u ocultas, puede configurar una de las siguientes listas (requiere dispositivos supervisados que ejecuten iOS 9.3 o posterior).

**Aplicaciones ocultas** especifique una lista de aplicaciones que estarán ocultas para los usuarios. Los usuarios no pueden ver ni iniciar estas aplicaciones.
**Aplicaciones visibles**: especifique una lista de aplicaciones que los usuarios puedan ver e iniciar. No se puede ver ni iniciar ninguna otra aplicación.

Para configurar la lista, haga clic en **Agregar** y especifique un nombre de su elección. Opcionalmente, puede indicar el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Especificación de la dirección URL para una aplicación de la tienda

Para especificar una dirección URL en la lista de aplicaciones, use el siguiente formato:

Con la ayuda de un motor de búsqueda, busque la aplicación que quiere usar en iTunes App Store y abra la página de la aplicación.
Copie la dirección URL de la página y úsela para configurar la lista de aplicaciones permitidas y prohibidas o una aplicación que quiera ejecutar en pantalla completa.

Ejemplo: busque Microsoft Word para iPad. La dirección URL que debe usar es https://itunes.apple.com/es/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> También puede utilizar el software de iTunes para encontrar la aplicación y, a continuación, utilizar el comando **Copiar vínculo** para obtener la dirección URL de la aplicación.

### <a name="additional-options"></a>Opciones adicionales

También puede hacer clic en **Importar** para rellenar la lista a partir de un archivo csv con el formato <*url de aplicación*>, <*nombre de aplicación*>, <*editor de aplicación*> o en **Exportar** para crear un archivo csv que contenga la lista de aplicaciones visibles u ocultas en el mismo formato.

### <a name="app-information-for-built-in-ios-apps"></a>Información de aplicaciones para las aplicaciones integradas de iOS
Use la información de esta lista para identificar el nombre, el publicador y el identificador de lote de aplicaciones de las aplicaciones integradas de iOS que quiere mostrar u ocultar. Si quiere mostrar u ocultar todas las aplicaciones de la lista, puede copiar los datos siguientes en un archivo de texto con la extensión **.csv** y, después, usar la opción **Importar** para importar todas las aplicaciones a la vez.


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





## <a name="cellular"></a>Móvil
-     **Itinerancia de datos**: permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.
-     **Captura de fondo global en itinerancia**: permite que el dispositivo capture datos, como el correo electrónico, mientras está en itinerancia en una red de telefonía móvil.
-     **Marcación por voz**: permite el uso de la característica de marcación por voz en el dispositivo.
-     **Itinerancia de voz**: permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.
-     **Cambios en la configuración de uso de datos móviles de la aplicación (solo supervisado)**: permite al usuario controlar qué aplicaciones pueden usar datos móviles.

## <a name="cloud-and-storage"></a>Nube y almacenamiento
-     **Copia de seguridad en iCloud**: permite al usuario realizar una copia de seguridad del dispositivo en iCloud.
-     **Sincronización del documento con iCloud (solo supervisado)**: permite la sincronización de documentos y de clave-valor con el espacio de almacenamiento de iCloud.
-     **Sincronización de Photo Stream en iCloud**: permite que los usuarios habiliten **Mis fotos en streaming** en su dispositivo para que las fotos se sincronicen con iCloud y está disponible en todos los dispositivos de usuario.
-     **Copia de seguridad cifrada**: exige el cifrado de cualquier copia de seguridad del dispositivo.
-     **Fototeca de iCloud**: si se establece en **No**, deshabilita el uso de la Fototeca de iCloud, que permite a los usuarios almacenar fotos y vídeos en la nube.    Las fotos que no se hayan descargado completamente de la Fototeca de iCloud al dispositivo se quitarán de este si esta opción se establece en **No**.
-     **Sincronización de aplicaciones administradas con la nube**: permite que las aplicaciones que se administran con Intune sincronicen los datos con la cuenta de iCloud del usuario.
-     **Fotos en streaming compartidas**: establezca en **No** para deshabilitar **fotos compartidas en iCloud** en el dispositivo.
-     **Continuación de la actividad**: permite que el usuario continúe el trabajo que inició en un dispositivo iOS en otro dispositivo iOS o Mac OS X (Handoff).

## <a name="kiosk"></a>Pantalla completa
-     **Bloqueo de activación**: permite el bloqueo de activación en dispositivos iOS supervisados.
-     **Aplicación que se ejecuta en modo de pantalla completa**: elija **Aplicación administrada** para seleccionar una aplicación que haya agregado a Intune, o **Aplicación de la Tienda** para especificar la dirección URL a una aplicación de la tienda. No se podrá ejecutar ninguna otra aplicación en el dispositivo. Lea "Cómo especificar las direcciones URL de tiendas de aplicaciones" más adelante en este tema para obtener más ayuda.
-     **Assistive touch**: habilita o deshabilita la configuración de accesibilidad **Assistive Touch**, que ayuda al usuario a realizar gestos en pantalla que podrían resultarle difíciles.
-     **Invertir colores**: habilita o deshabilita la configuración de accesibilidad Invertir colores, que ajusta la pantalla para ayudar a los usuarios con discapacidades visuales.
-     **Audio mono**: habilita o deshabilita la configuración de accesibilidad Audio mono.
-     **VoiceOver**: habilita o deshabilita la configuración de accesibilidad **VoiceOver**, que lee en voz alta el texto de la pantalla del dispositivo.
-     **Zoom**: habilita o deshabilita la configuración de accesibilidad **Zoom**, que permite al usuario usar un toque para acercar la pantalla del dispositivo.
-     **Bloqueo automático**: habilita o deshabilita el bloqueo automático del dispositivo.
-     **Cambio de timbre**: habilita o deshabilita el conmutador de timbre (silencio) en el dispositivo.
-     **Rotación de pantalla**: habilita o deshabilita el cambio de orientación de la pantalla cuando el usuario gira el dispositivo.
-     **Botón de suspensión de pantalla**: habilita o deshabilita el botón de reposo o activación de pantalla en el dispositivo.
-     **Táctil**: habilita o deshabilita la pantalla táctil en el dispositivo.
-     **Botones de volumen**: habilita o deshabilita el uso de los botones de volumen en el dispositivo.
-     **Control de AssistiveTouch**: habilita o deshabilita los ajustes de Assistive Touch, que permiten al usuario ajustar la función de Assistive Touch.
-     **Control Invertir colores**: habilita o deshabilita los ajustes de invertir colores, que permiten al usuario ajustar la función de invertir colores.
-     **Speak on selected text** (Leer el texto seleccionado) habilita o deshabilita la configuración de accesibilidad Reproducir selección, que puede leer en voz alta el texto que selecciona el usuario.
-     **Control de VoiceOver**: habilita o deshabilita los ajustes de VoiceOver, que permiten al usuario ajustar la función VoiceOver (por ejemplo, la rapidez con la que se lee el texto en pantalla en voz alta).
-     **Control de zoom**: habilita o deshabilita los ajustes de zoom, que permiten al usuario ajustar la función de zoom.

>[!NOTE]
> Antes de configurar un dispositivo iOS para pantalla completa, debe usar la herramienta Apple Configurator o el Programa de inscripción de dispositivos de Apple para pasar el dispositivo al modo supervisado. Para obtener más información sobre la herramienta Apple Configurator, consulte la documentación de Apple.
>Si la aplicación de iOS que especifique se instala después de implementar la directiva de configuración, el dispositivo no pasará a pantalla completa hasta que se reinicie.

## <a name="safari"></a>Safari
-     **Safari (solo supervisado)**: especifique si el explorador Safari se puede usar en el dispositivo.
-     **Autofill** (Rellenar automáticamente): permite al usuario cambiar la configuración de Autocompletar en el explorador.
-     **Cookies**: permite que el explorador use cookies.
-     **JavaScript**: permite la ejecución de scripts de Java en el explorador.
-     **Advertencias de fraude**: permite advertencias de fraude en el explorador.
-     **Elementos emergentes**: habilita o deshabilita el bloqueador de elementos emergentes del explorador.

