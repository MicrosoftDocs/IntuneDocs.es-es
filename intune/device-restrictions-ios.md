---
title: Configuración de dispositivo iOS en Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Agregue, configure o cree valores en dispositivos iOS para restringir características, lo que incluye establecer requisitos de contraseña, controlar la pantalla de bloqueo, usar aplicaciones integradas, agregar aplicaciones restringidas o aprobadas, controlar dispositivos Bluetooth, conectarse a la nube para realizar copias de seguridad y almacenar, habilitar la pantalla completa, agregar dominios y controlar la manera en que los usuarios interactúan con el explorador web Safari en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a92d18615f6be7c1e0ce931d443d2ac986db991e
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566716"
---
# <a name="ios-device-settings-to-allow-or-restrict-features-using-intune"></a>Configuración de dispositivos iOS para permitir o restringir características mediante Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo se enumeran y describen los diferentes valores de configuración que se pueden controlar en los dispositivos iOS. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores para habilitar o deshabilitar características, establecer reglas de contraseña, permitir o restringir determinadas aplicaciones, etc.

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos iOS.

## <a name="before-you-begin"></a>Antes de comenzar

[Crear un perfil de configuración de restricciones de dispositivos](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>General

- **Compartir datos de uso**: elija **Bloquear** para evitar que el dispositivo envíe a Apple datos de diagnóstico y uso. **No configurado** (valor predeterminado) permite que se envíen estos datos.
  - **Modificación de configuración de envío de diagnósticos (solo supervisado)**: **bloque** evita que el usuario cambie la configuración de análisis de presentación y aplicación de diagnóstico en **deusoydiagnóstico**(configuración del dispositivo). **No configurado** (valor predeterminado) permite que el usuario cambie esta configuración del dispositivo.

    Esta característica se aplica a:  
    - iOS 9.3.2 y versiones posteriores

- **Captura de pantalla**: elija **Bloquear** para evitar que se hagan capturas de pantalla en el dispositivo. **No configurado** (valor predeterminado) permite que el usuario capture el contenido de la pantalla como imagen.
  - **Observación de pantalla remota mediante la aplicación Aula (solo con supervisión)**: elija **Bloquear** para evitar que la aplicación Aula vea de manera remota la pantalla en el dispositivo. **No configurado** (valor predeterminado) permite que la aplicación Aula de Apple vea la pantalla.

    Esta característica se aplica a:  
    - iOS 9.3 y versiones posteriores

  - **Observación de pantalla sin mensajes desde la aplicación Aula (solo con supervisión)**: si está establecido en **Permitir**, los profesores pueden observar de manera silenciosa la pantalla de los dispositivos iOS de los alumnos con la aplicación Aula sin que estos lo sepan. Los dispositivos de alumnos inscritos en una clase con la aplicación Aula automáticamente dan permiso al profesor de ese curso. **No configurado** (valor predeterminado) impide que esta característica.
- **Certificados TLS que no son de confianza**: elija **Bloquear** para evitar en el dispositivo los certificados de Seguridad de la capa de transporte (TLS) que no son de confianza. **No configurado** (valor predeterminado) permite que los certificados TLS.
- **Confianza de aplicaciones empresariales**: elija **Bloquear** para quitar el botón **Trust Enterprise Developer** en Configuración > General > Administración de perfiles y dispositivos del dispositivo. **No configurado** (valor predeterminado) permite que el usuario elija confiar en aplicaciones no descargadas de la tienda de aplicaciones.
- **Modificación de la cuenta (solo con supervisión)**: cuando se establece en **Bloquear**, el usuario no puede actualizar la configuración específica del dispositivo en la aplicación de configuración de iOS. Por ejemplo, el usuario no puede crear nuevas cuentas de dispositivo ni modificar el nombre de usuario o la contraseña. **No configurado** (valor predeterminado) permite que los usuarios cambien esta configuración.

  Esta característica también se aplica a la configuración accesible desde la aplicación de configuración de iOS, como Mail, Contacts, Calendar, Twitter, etc. Esta característica no se aplica a las aplicaciones con la configuración de la cuenta que no se pueden configurar desde la aplicación de configuración de iOS, como la aplicación Microsoft Outlook.
- **Pantalla de tiempo (solo supervisado)**: elija **bloque** para impedir que los usuarios establecer sus propias restricciones en tiempo de la pantalla (configuración de dispositivo). **No configurado** permite al usuario configurar restricciones de dispositivos (por ejemplo, controles parentales o contenido y restricciones de privacidad) en el dispositivo.

  Esta configuración se ha cambiado desde **habilitación de restricciones en la configuración del dispositivo**. Impacto de este cambio:  
  
  - iOS 11.4.1 y versiones anteriores: **Bloquear** impide que los usuarios finales establezcan sus propias restricciones en la configuración del dispositivo. Este es el mismo; y no hay ningún cambio para los usuarios finales.
  - iOS 12.0 y versiones posteriores: **bloque** impide que los usuarios finales establezcan sus propias **tiempo pantalla** en la configuración del dispositivo (configuración > General > tiempo de pantalla), incluidas las restricciones de contenido y la privacidad. Dispositivos actualizados a iOS 12.0 no aparecerá la ficha restricciones en la configuración del dispositivo ya (configuración > General > Administración de dispositivos > perfil de administración > restricciones). Estas opciones se encuentran en **Tiempo de uso**.
  
- **Uso de la opción de borrar todo el contenido y la configuración del dispositivo (solo con supervisión)**: elija **Bloquear** para que los usuarios no puedan usar la opción de borrar todo el contenido y la configuración del dispositivo (solo con supervisión). **No configurado** (valor predeterminado) permite que los usuarios accedan a esta configuración.
- **Modificación del nombre del dispositivo (solo con supervisión)**: elija **Bloquear** para que no se pueda cambiar el nombre del dispositivo. **No configurado** (valor predeterminado) permite que el usuario cambie el nombre del dispositivo.
- **Modificación de la configuración de notificaciones (solo con supervisión)**: elija **Bloquear** para que no se pueda cambiar la configuración de notificaciones. **No configurado** (valor predeterminado) permite que el usuario cambie la configuración de las notificaciones del dispositivo.
- **Modificación del fondo de pantalla (solo con supervisión)**: **Bloquear** impide que se cambie el fondo de pantalla. **No configurado** (valor predeterminado) permite que el usuario cambie el fondo de pantalla del dispositivo.
- **Modificación de la configuración de confianza de aplicaciones empresariales (solo con supervisión)**: **Bloquear** impide que el usuario cambie la configuración de confianza de aplicaciones empresariales en dispositivos supervisados. **No configurado** (valor predeterminado) permite que el usuario confíe en aplicaciones no descargadas de la tienda de aplicaciones.
- **Cambios en el perfil de configuración (solo con supervisión)**: **Bloquear** impide los cambios en el perfil de configuración del dispositivo. **No configurado** (valor predeterminado) permite que el usuario instale perfiles de configuración.
- **Bloqueo de activación (solo con supervisión)**: elija **Permitir** para permitir el bloqueo de activación en dispositivos iOS supervisados. Bloqueo de activación dificulta que un dispositivo robado o perdido pueda reactivarse.
- **Bloqueo de la eliminación de aplicaciones (solo con supervisión)**: elija **Bloquear** para impedir que los usuarios quiten aplicaciones. **No configurado** (valor predeterminado) permite que los usuarios quiten aplicaciones del dispositivo.
- **Bloqueo del modo restringido de USB (solo con supervisión)**: elija **Bloquear** para deshabilitar el modo restringido de USB en los dispositivos supervisados. El modo restringido de USB impide que los accesorios USB intercambien datos con un dispositivo bloqueado durante más de una hora. **No configurado** (valor predeterminado) permite el modo restringido de USB.
- **Forzar fecha y hora automática (solo con supervisión)**: **Requerir** fuerza los dispositivos supervisados para que establezcan fecha y hora automáticamente. La zona horaria del dispositivo se actualiza cuando el dispositivo tiene conexiones móviles o tiene Wi-Fi con servicios de ubicación habilitados.
- **Requerir que los alumnos pidan permiso para dejar un curso de Aula (solo con supervisión)**: **Requerir** obliga a los alumnos inscritos en un curso no administrado con la aplicación Aula a pedir permiso al profesor para dejar el curso. **No configurado** (valor predeterminado) no obliga al alumno a pedir permiso.

  Esta característica se aplica a:  
  - iOS 11.3 y versiones posteriores

- **Permitir aula bloquear a una aplicación y bloquear el dispositivo sin pedir confirmación (solo supervisado)**: **habilitar** permite profesor bloquear las aplicaciones o bloquear el dispositivo con la aplicación aula sin preguntar al alumno. Bloqueo significa que las aplicaciones del dispositivo solo puede profesor de acceso a las aplicaciones especificadas. **No configurado** (valor predeterminado) impide que los profesores bloqueen aplicaciones o dispositivos con la aplicación aula sin preguntar al alumno. 

  Esta característica se aplica a:  
  - iOS 11.0 y versiones posteriores

- **Clases de Classroom se unen automáticamente sin preguntar (solo supervisado)**: **habilitar** automáticamente permite a los alumnos para unirse a una clase que se encuentra en la aplicación aula sin preguntar al profesor. **No configurado** (valor predeterminado) solicita el profesor que los estudiantes van a unirse a una clase que se encuentra en la aplicación Classroom.

  Esta característica se aplica a:  
  - iOS 11.0 y versiones posteriores

- **Permitir actualizaciones de PKI de manera inalámbrica**: con la opción **Permitir**, los usuarios reciben actualizaciones de software sin tener que conectar los dispositivos a un equipo.
- **Limitar el seguimiento de publicidad**: elija **Limitar** para deshabilitar el identificador de publicidad del dispositivo. **No configurado** (valor predeterminado) mantiene habilitado.
- **Bloquear la creación de VPN (solo con supervisión)**: **Bloquear** impide que los usuarios creen una configuración de VPN. **No configurado** (valor predeterminado) permite que los usuarios creen VPN en el dispositivo.
- **Modificar la configuración de eSIM (solo supervisado)**: **bloque** impide que los usuarios quitar o agregar un plan de telefonía móvil para el eSIM en el dispositivo. **No configurado** (valor predeterminado) permite que los usuarios cambien esta configuración.

  Esta característica se aplica a:  
  - iOS 12.1 y versiones posteriores

- **Aplazar actualizaciones de software (solo supervisadas)**: cuando se establece en **no configurado** (valor predeterminado), las actualizaciones de software se muestran en el dispositivo con Apple vaya lanzando. Por ejemplo, si obtiene publica una actualización de iOS de Apple en una fecha concreta, a continuación, esa actualización naturalmente aparecerá en el dispositivo en torno a la fecha de lanzamiento.

  **Habilitar** permite retrasar cuando se muestran las actualizaciones de software en dispositivos, desde 0 a 90 días. Esta configuración no controla cuando las actualizaciones están o no están instaladas. 

  - **Retrasar la visibilidad de las actualizaciones de software**: escriba un valor comprendido entre 0 y 90 días. Cuando el retraso expira, los usuarios reciben una notificación para actualizar a la versión más antigua del sistema operativo que estaba disponible cuando se desencadenó el retraso.

    Por ejemplo, si iOS 12.a está disponible en **el 1 de enero**, y **retrasar visibilidad** está establecido en **5 días**, iOS, a continuación, 12.a no se muestra como una actualización disponible en dispositivos de usuario final. En el **sexto día** posteriores al lanzamiento, que está disponible la actualización y los usuarios finales pueden instalarlo.

    Esta configuración se aplica a:  
    - iOS 11.3 y versiones posteriores

## <a name="password"></a>Contraseña

- **Contraseña**: **Requerir** que el usuario final escriba una contraseña para acceder al dispositivo. **No configurado** permite que los usuarios accedan al dispositivo sin tener que escribir una contraseña.
  - **Contraseñas sencillas**: elija **Bloquear** para exigir contraseñas más complejas. **No configurado** permite contraseñas sencillas, como `0000` y `1234`.
  - **Tipo de contraseña requerida**: elija el tipo de contraseña que requiere la organización. Las opciones son:
    - **Valor predeterminado de dispositivo**
    - **Numérico**
    - **Alfanumérico**
  - **Número de caracteres no alfanuméricos en la contraseña**: escriba el número de caracteres de símbolos, como `#` o `@`, que se deben incluir en la contraseña.
  - **Longitud mínima de la contraseña**: escriba la longitud mínima que un usuario debe escribir (entre 4 y 14 caracteres).
  - **Número de errores de inicio de sesión antes de borrar el contenido del dispositivo**: escriba el número permitido de errores de inicio de sesión antes de borrar el contenido del dispositivo (entre 1 y 11).
  - **Máximo de minutos tras el bloqueo de la pantalla antes de solicitar la contraseña**<sup>1</sup>: escriba cuánto tiempo el dispositivo permanece inactivo antes de que el usuario deba volver a escribir la contraseña. Si escribe un tiempo mayor al que está establecido actualmente en el dispositivo, este pasará por alto el tiempo que escribió. Compatible en dispositivos iOS 8.0 y más recientes.
  - **Máximo de minutos de inactividad hasta que se bloquea la pantalla**<sup>1</sup>: escriba el número máximo de minutos de inactividad que se permiten en el dispositivo hasta que se bloquea la pantalla. Si escribe un tiempo mayor al que está establecido actualmente en el dispositivo, este pasará por alto el tiempo que escribió.
  - **Caducidad de la contraseña (días)**: escriba el número de días antes de que se deba cambiar la contraseña del dispositivo.
  - **Impedir la reutilización de contraseñas anteriores**: escriba el número de contraseñas nuevas que se deben usar antes de poder reutilizar una antigua.
  - **Desbloqueo con huella digital**: elija **Bloquear** para impedir el uso de la huella digital para desbloquear el dispositivo. **No configurado** permite que el usuario desbloquee el dispositivo con la huella digital.
- **Modificación del código de acceso (solo con supervisión)**: elija **Bloquear** para evitar que se cambie, se agregue o se quite el código de acceso. En los dispositivos supervisados, los cambios en las restricciones del código de acceso se pasan por alto después de bloquear esta característica. **No configurado** (valor predeterminado) permite agregar, cambiar o quitar códigos de acceso.

  - **Modificación de huella digital (solo con supervisión)**: **Bloquear** impide que el usuario cambie, agregue o quite las huellas digitales de TouchID. **No configurado** (valor predeterminado) permite que el usuario actualice las huellas digitales de TouchID del dispositivo.

- **Bloquear la característica Autorrellenar contraseñas (solo con supervisión)**: elija **Bloquear** para evitar el uso de la característica Autorrellenar contraseñas en iOS. Al elegir **Bloquear**, también ocurre lo siguiente:

  - No se les pide a los usuarios que usen una contraseña guardada en Safari ni en ninguna aplicación.
  - Se deshabilitan las contraseñas seguras automáticas y no se sugieren contraseñas seguras a los usuarios.

  **No configurado** (valor predeterminado) permite estas características.

- **Bloquear solicitudes de proximidad de contraseñas (solo con supervisión)**: elija **Bloquear** para que el dispositivo de un usuario no solicite contraseñas de los dispositivos cercanos. **No configurado** (valor predeterminado) permite estas solicitudes de contraseña.
- **Bloquear el uso compartido de contraseñas (solo con supervisión)**: **Bloquear** impide el uso compartido de contraseñas entre dispositivos mediante AirDrop. **No configurado** (valor predeterminado) permite compartir las contraseñas.
- **Requerir la autenticación de Touch ID o Face ID para obtener información de contraseña o tarjeta de crédito Autorrellenar (solo supervisado)**: cuando se establece en **requieren**, los usuarios deben autenticarse utilizando TouchID o FaceID antes de la tarjeta de crédito o contraseñas información puede ser automática rellenada Safari y otras aplicaciones. **No configurado** (valor predeterminado) permite a los usuarios controlar esta característica en la configuración del dispositivo.

  Esta característica se aplica a:  
  - iOS 11.0 y versiones posteriores

<sup>1</sup>Al configurar los valores **Máximo de minutos de inactividad hasta que se bloquea la pantalla** y **Máximo de minutos tras el bloqueo de la pantalla antes de solicitar la contraseña**, se aplican en secuencia. Por ejemplo, si establece el valor para ambas opciones en **5** minutos, a pantalla se apaga automáticamente transcurridos cinco minutos y el dispositivo se bloquea después de cinco minutos más. Sin embargo, si el usuario apaga la pantalla manualmente, la segunda opción se aplica inmediatamente. En el mismo ejemplo, una vez que el usuario apaga la pantalla, el dispositivo se bloquea cinco minutos más tarde.

## <a name="locked-screen-experience"></a>Experiencia de pantalla bloqueada

- **Acceso a Centro de control con dispositivo bloqueado**: elija **Bloquear** para impedir el acceso a la aplicación Centro de control cuando el dispositivo está bloqueado. **No configurado** permite que los usuarios accedan a la aplicación Centro de control cuando el dispositivo está bloqueado.
- **Notificaciones con dispositivo bloqueado**: **Bloquear** impide el acceso a las notificaciones cuando el dispositivo está bloqueado. **No configurado** permite que el usuario acceda a las notificaciones sin que sea necesario desbloquear el dispositivo.
- **Notificaciones de Wallet con dispositivo bloqueado**: **Bloquear** impide el acceso a las notificaciones cuando el dispositivo está bloqueado. **No configurado** permite que el usuario acceda a la aplicación Wallet mientras el dispositivo está bloqueado.
- **Vista Hoy con dispositivo bloqueado**: **Bloquear** impide el acceso a la vista Hoy cuando el dispositivo está bloqueado. **No configurado** permite que el usuario vea la vista Hoy cuando el dispositivo está bloqueado.

## <a name="app-store-doc-viewing-gaming"></a>Tienda de aplicaciones, presentación de documentos, juegos

- **Tienda de aplicaciones**: **Bloquear** impide el acceso a la tienda de aplicaciones en dispositivos supervisados. **No configurado** permite el acceso.
  - **Instalación de aplicaciones de App Store (solo con supervisión)**: elija **Bloquear** para bloquear la tienda de aplicaciones en la pantalla principal del dispositivo. Los usuarios finales pueden seguir usando iTunes o Apple Configurator para instalar aplicaciones. **No configurado** permite la tienda de aplicaciones en la pantalla principal.
  - **Descargas de aplicaciones automáticas (solo con supervisión)**: elija **Bloquear** para impedir la descarga automática de las aplicaciones compradas en otros dispositivos. No afecta las actualizaciones de las aplicaciones existentes. **No configurado** permite descargar en el dispositivo las aplicaciones compradas en otros dispositivos iOS.
- **Contraseña para acceder a la tienda de aplicaciones**: **Requerir**  que el usuario escriba una contraseña antes de que pueda visitar la tienda de aplicaciones. **No configurado** permite el acceso a la tienda de aplicaciones sin que sea necesario escribir una contraseña.
- **Compras desde la aplicación**: elija **Bloquear** para impedir las compras en la tienda desde la aplicación. **No configurado** permite las compras en la tienda dentro de una aplicación en ejecución.
- **Música, podcasts o contenido de noticias explícitos de iTunes (solo con supervisión)**: elija **Bloquear** para evitar música, podcasts o contenido de noticias explícitos de iTunes. **No configurado** permite que el dispositivo acceda a contenido clasificado para adultos en la tienda.
- **Descargar contenido marcado como "Erótico" en iBooks Store**: elija **Bloquear** para impedir que los usuarios descarguen archivos multimedia de iBooks Store marcados como eróticos. **No configurado** permite que el usuario descargue libros con la categoría "Erotismo".
- **Visualización de documentos corporativos en aplicaciones no administradas**: **Bloquear** impide la visualización de documentos no corporativos en aplicaciones no administradas. **No configurado** permite ver los documentos corporativos en cualquier aplicación. Por ejemplo, se quiere evitar que los usuarios guarden archivos de la aplicación OneDrive en Dropbox. Configure este valor como **Bloquear**. Después de que el dispositivo recibe la directiva (por ejemplo, después de un reinicio), ya no le permite guardar.
  - **Permitir que las aplicaciones administradas escribir contactos en cuentas de contactos no administrado**: cuando se establece en **permitir**, los usuarios pueden agregar o sincronizar la información de contacto de Outlook de cualquier persona, incluidos empresariales y contactos corporativos, a la aplicación contactos integrada en el dispositivo. Cuando se establece en **Sin configurar**, los usuarios no pueden agregar contactos de Outlook a la aplicación de contactos integrada en el dispositivo.
  
    Para usar este valor, establezca la opción **Visualización de documentos corporativos en aplicaciones no administradas** en **Bloquear**.
  
- **Visualización de documentos no corporativos en aplicaciones corporativas**: **Bloquear** impide la visualización de documentos no corporativos en aplicaciones corporativas. **No configurado** permite ver cualquier documento en aplicaciones administradas corporativas.
  - **Permitir que las aplicaciones no administradas leer desde las cuentas de contactos administrado**: cuando se establece en **permitir**, los usuarios pueden agregar a iContacts póngase en contacto con información de la aplicación cualquier persona en Outlook. **Sin configurar** evita la lectura, incluso la eliminación de duplicados, en la aplicación de contactos integrada en el dispositivo.
  
    Para usar este valor, establezca la opción **Visualización de documentos no corporativos en aplicaciones corporativas** en **Bloquear**.
  
- **Tratar AirDrop como destino no administrado**: **Requerir** obliga a considerar a AirDrop como destino para colocar no administrado. Impide que las aplicaciones administradas envíen datos mediante AirDrop. 
- **Agregar amigos a Game Center (solo con supervisión)**: **Bloquear** impide que los usuarios agreguen amigos a Game Center. **No configurado** permite que el usuario agregue amigos en Game Center.
- **Game Center (solo con supervisión)**: **Bloquear** el uso de la aplicación Game Center. **No configurado** permite usar la aplicación Game Center en el dispositivo.
- **Juegos multijugador (solo con supervisión)**: elija **Bloquear** para impedir los juegos multijugador. **No configurado** permite que el usuario disfrute juegos multijugador en el dispositivo.
- **Región de clasificaciones**: elija la región de clasificaciones que quiere usar para las descargas permitidas. y luego elija las clasificaciones permitidas para **Películas** y **Programas de TV**.
- **Aplicaciones**: elija la clasificación por edades permitida de las aplicaciones que los usuarios pueden descargar. También puede elegir **Permitir todas las aplicaciones**.

## <a name="built-in-apps"></a>Aplicaciones integradas

- **Cámara**: elija **Bloquear** para impedir el acceso a la cámara del dispositivo. **No configurado** permite el acceso a la cámara del dispositivo.
  - **FaceTime**: **Bloquear** impide el acceso a la aplicación FaceTime. **No configurado** permite el acceso a la aplicación FaceTime en el dispositivo.
- **Siri**: **Bloquear** impide el acceso a Siri. **No configurado** permite usar el asistente de voz Siri en el dispositivo.
  - **Siri con dispositivo bloqueado**: elija **Bloquear** para impedir el acceso a Siri cuando el dispositivo está bloqueado. **No configurado** permite usar el asistente de voz Siri en el dispositivo cuando está bloqueado.
  - **Filtro de obscenidad de Siri (solo con supervisión)**: **Requerir** evita que Siri dicte o hable con un lenguaje obsceno.
  - **Consulta de Siri de contenido generado por usuarios de Internet (solo con supervisión)**: **Bloquear** impide que Siri acceda a sitios web para responder preguntas. **No configurado** permite que Siri acceda al contenido generado por usuarios de Internet.
- **Apple News (solo con supervisión)**: Elija **Bloquear** para impedir el acceso a la aplicación Apple News en el dispositivo. **No configurado** permite usar la aplicación Apple News.
- **iBooks Store (solo con supervisión)**: **Bloquear** impide el acceso a iBooks Store. **No configurado** permite que los usuarios examinen y compren libros en iBooks Store.
- **Aplicaciones Mensajes del dispositivo (solo con supervisión)**: elija **Bloquear** para que los usuarios no puedan usar la aplicación Mensajes en el dispositivo. **No configurado** permite usar la aplicación Mensajes para enviar y leer mensajes de texto.
- **Podcasts (solo con supervisión)**: **Bloquear** impide que los usuarios usen la aplicación Podcasts. **No configurado** permite usar la aplicación Podcasts.
- **Servicio Música (solo con supervisión)**: **Bloquear** revierte la aplicación Música al modo clásico y deshabilita el servicio Música. **No configurado** permite usar la aplicación Apple Music.
- **Servicio iTunes Radio (solo con supervisión)**: **Bloquear** impide que los usuarios usen la aplicación iTunes Radio. **No configurado** permite usar la aplicación iTunes Radio.
- **Cambios en la configuración de la aplicación Buscar a mis amigos (solo con supervisión)**: **Bloquear** impide cambios en la configuración de la aplicación Buscar a mis amigos. **No configurado** permite que el usuario cambie la configuración de la aplicación Buscar a mis amigos.
- **Búsqueda de Spotlight para devolver resultados de Internet (solo con supervisión)**: **Bloquear** impide que Spotlight devuelva resultados de cualquier búsqueda de Internet. **No configurado** permite que la búsqueda de Spotlight se conecte a Internet para proporcionar resultados de la búsqueda.
- **Bloquear la eliminación de aplicaciones de sistema del dispositivo (solo con supervisión)**: elegir **Bloquear** deshabilita la capacidad de quitar aplicaciones de sistema del dispositivo. **No configurado** permite que los usuarios quiten aplicaciones de sistema.

#### <a name="safari"></a>Safari

- **Safari**: **Bloquear** el uso del explorador Safari en el dispositivo. **No configurado** permite que los usuarios utilicen el explorador Safari.
- **Autorrellenar**: **Bloquear** deshabilita la característica Autorrellenar de Safari en el dispositivo. **No configurado** permite que los usuarios cambien la configuración de Autorrellenar del explorador web.
- **Cookies**: elija cómo se administran las cookies en el dispositivo. Las opciones son:
  - Allow
  - Bloquear todas las cookies
  - Permitir cookies de sitios web visitados
  - Permitir cookies del sitio web actual
- **JavaScript**: **Bloquear** impide que los scripts de Java del explorador se ejecuten en el dispositivo. **No configurado** permite los scripts de Java.
- **Advertencias de fraude**: **Requerir** que las advertencias de fraude se muestren en el explorador web del dispositivo. **No configurado** deshabilita esta característica.
- **Elementos emergentes**: **Bloquear** para deshabilitar el bloqueador de elementos emergentes del explorador web. **No configurado** permite el bloqueador de elementos emergentes.

## <a name="restricted-apps"></a>Aplicaciones restringidas

En la lista de aplicaciones restringidas, puede configurar una de las listas siguientes:

- **Aplicaciones prohibidas**: lista de aplicaciones no administradas por Intune que no quiere que se instalen en el dispositivo. Si un usuario instala una aplicación de esta lista, recibirá una notificación a través de Intune.
- **Aplicaciones aprobadas**: lista de aplicaciones que los usuarios pueden instalar. Para mantener el cumplimiento, los usuarios no deben instalar otras aplicaciones. Las aplicaciones que se administran mediante Intune están permitidas automáticamente. Si un usuario instala una aplicación de esta lista, recibirá una notificación a través de Intune.

Para agregar aplicaciones a estas listas, puede:

- **Agregar** la dirección URL de la tienda de aplicaciones de iTunes de la aplicación que quiere instalar. Por ejemplo, para agregar la aplicación Carpetas de trabajo de Microsoft, escriba `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para buscar la dirección URL de una aplicación, abra la tienda de aplicaciones de iTunes y busque la aplicación. Por ejemplo, busque `Microsoft Remote Desktop` o `Microsoft Word`. Seleccione la aplicación y copie la dirección URL.

  También puede usar iTunes para buscar la aplicación y luego usar la tarea **Copiar vínculo** para obtener la dirección URL de la aplicación.

- Importe un archivo .csv con detalles sobre la aplicación, incluida la dirección URL. Use el formato `<app url>, <app name>, <app publisher>`. O bien exporte una lista existente que incluye la lista de aplicaciones restringidas en el mismo formato.

> [!IMPORTANT]
> Se deben asignar perfiles de dispositivo que usen configuración de aplicaciones restringidas para grupos de usuarios.

## <a name="show-or-hide-apps-supervised-only"></a>Mostrar u ocultar aplicaciones (solo con supervisión)

En la lista de aplicaciones visibles u ocultas, puede configurar una de las siguientes listas en dispositivos supervisados que ejecuten iOS 9.3 o posteriores.

- **Aplicaciones ocultas**: escriba una lista de las aplicaciones ocultas a los usuarios. Los usuarios no pueden ver ni abrir estas aplicaciones.
- **Aplicaciones visibles**: escriba una lista de aplicaciones que los usuarios pueden ver e iniciar. No se puede ver ni iniciar ninguna otra aplicación.

Para agregar aplicaciones a estas listas, puede:

- **Agregar** la dirección URL de la tienda de aplicaciones de iTunes de la aplicación que quiere instalar. Por ejemplo, para agregar la aplicación Carpetas de trabajo de Microsoft, escriba `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`.

  Para buscar la dirección URL de una aplicación, abra la tienda de aplicaciones de iTunes y busque la aplicación. Por ejemplo, busque `Microsoft Remote Desktop` o `Microsoft Word`. Seleccione la aplicación y copie la dirección URL.

  También puede usar iTunes para buscar la aplicación y luego usar la tarea **Copiar vínculo** para obtener la dirección URL de la aplicación.

- Importe un archivo .csv con detalles sobre la aplicación, incluida la dirección URL. Use el formato `<app url>, <app name>, <app publisher>`. O bien exporte una lista existente que incluye la lista de aplicaciones restringidas en el mismo formato.

## <a name="wireless"></a>Inalámbrico

- **Itinerancia de datos**: elija **Bloquear** para evitar la itinerancia de datos a través de la red de telefonía móvil. **No configurado** (valor predeterminado) permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.
- **Captura de fondo global durante la itinerancia**: **Bloquear** impide usar la característica de captura de fondo global durante la itinerancia a través de la red de telefonía móvil. **No configurado** (valor predeterminado) permite que el dispositivo capture datos, como el correo electrónico, durante la itinerancia en una red de telefonía móvil.
- **Marcación por voz**: elija **Bloquear** para impedir que los usuarios usen la característica de marcación por voz en el dispositivo. **No configurado** (valor predeterminado) permite la marcación por voz en el dispositivo.
- **Itinerancia de voz**: elija **Bloquear** para evitar la itinerancia de voz a través de la red de telefonía móvil. **No configurado** (valor predeterminado) permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.
- **Cambios en la configuración de uso de datos móviles de la aplicación (solo con supervisión)**: elija **Bloquear** para evitar los cambios en la configuración de uso de datos móviles de la aplicación. **No configurado** (valor predeterminado) permite que el usuario controle qué aplicaciones pueden usar datos móviles.
- **Los cambios de configuración del plan de telefonía móvil (solo supervisada)**: **bloque** impide que los usuarios cambiar la configuración en el plan de telefonía móvil. **No configurado** (valor predeterminado) permite a los usuarios realizar cambios.

  Esta característica se aplica a:  
  - iOS 11.0 y versiones posteriores

- **Zona de cobertura personal**: **Bloquear** impide que el dispositivo se use como una zona de cobertura personal. Esta opción puede que no sea compatible con algunos operadores. **No configurado** (valor predeterminado) permite que esta característica.
- **Conexión a redes Wi-Fi con perfiles de configuración (solo con supervisión)**: **Requerir** obliga al dispositivo a usar solo redes Wi-Fi configuradas a través de perfiles de configuración de Intune. **No configurado** (valor predeterminado) permite que el dispositivo use otras redes Wi-Fi.
- **Reglas de uso de datos móviles (solo aplicaciones )**: defina los tipos de datos que las aplicaciones administradas pueden usar cuando están en redes de telefonía móvil. Las opciones son:
  - **Bloquear el uso de datos móviles**: bloquee el uso de los datos móviles en **Todas las aplicaciones administradas** o **Elegir aplicaciones específicas**.
  - **Bloquear el uso de datos móviles en itinerancia**: bloquee el uso de datos móviles en itinerancia en **Todas las aplicaciones administradas** o **Elegir aplicaciones específicas**.

## <a name="connected-devices"></a>Dispositivos conectados

- **AirDrop (solo con supervisión)**: **Bloquear** impide usar AirDrop en el dispositivo. **No configurado** (valor predeterminado) permite usar la característica AirDrop para intercambiar contenido con dispositivos cercanos.
- **Emparejamiento con Apple Watch (solo con supervisión)**: **Bloquear** impide el emparejamiento con un dispositivo Apple Watch. **No configurado** (valor predeterminado) permite el emparejamiento del dispositivo con Apple Watch.
- **Detección de muñeca para Apple Watch enlazado**: **Requerir** obliga a que un dispositivo Apple Watch use la detección de muñeca. Cuando se requiere, el dispositivo Apple Watch no mostrará notificaciones si no se lleva puesto. 
- **Modificación de Bluetooth (solo con supervisión)**: **Bloquear** impide que el usuario final cambie la configuración de Bluetooth del dispositivo. **No configurado** (valor predeterminado) permite que el usuario cambie esta configuración.
- **Emparejamiento de host para controlar los dispositivos con los que se puede emparejar un dispositivo iOS (solo con supervisión)**: **No configurado** (valor predeterminado) permite el emparejamiento de host para que el administrador controle con qué dispositivos se puede emparejar un dispositivo iOS. **Bloquear** impide el emparejamiento de host.
- **Requerir contraseña de emparejamiento para solicitudes salientes de AirPlay**: **Requerir** solicita una contraseña de emparejamiento cuando el usuario usa AirPlay para transmitir contenido a otros dispositivos Apple. **No configurado** (valor predeterminado) permite que el usuario transmita contenido mediante AirPlay sin tener que escribir una contraseña.
- **Bloquear AirPrint (solo con supervisión)**: elija **Bloquear** para impedir usar la característica AirPrint en el dispositivo. **No configurado** (valor predeterminado) permite que el usuario use AirPrint.
  - **Bloquear almacenamiento de credenciales de AirPrint en Keychain (solo con supervisión)**: **Bloquear** impide usar el almacenamiento Keychain para el nombre de usuario y la contraseña en el dispositivo. **No configurado** (valor predeterminado) permite almacenar el nombre de usuario y la contraseña de AirPrint en la aplicación Keychain.
  - **Requerir un certificado TLS de confianza para AirPrint (solo con supervisión)**: **Requerir** obliga al dispositivo a usar certificados de confianza para la comunicación de impresión de TLS.
  - **Bloquear la detección de iBeacon de impresoras AirPrint (solo con supervisión)**: **Bloquear** impide que señales Bluetooth de AirPrint malintencionadas realicen suplantación de identidad (phishing) para el tráfico de red. **No configurado** (valor predeterminado) permite anunciar impresoras AirPrint en el dispositivo.
- **Bloquear configuración de seguridad nuevo (solo supervisados) de dispositivos cercanos**: **bloque** deshabilita el símbolo del sistema para configurar nuevos dispositivos que están cercanos. **No configurado** (valor predeterminado) permite solicitudes para los usuarios para conectarse a otros dispositivos cercanos de Apple.

  Esta característica se aplica a:  
  - iOS 11.0 y versiones posteriores

## <a name="keyboard-and-dictionary"></a>Teclado y diccionario

- **Búsqueda de definiciones de palabras (solo con supervisión)**: **Bloquear** evita que el usuario resalte una palabra y luego busque su definición en el dispositivo. **No configurado** permite el acceso a la característica de búsqueda de definiciones.
- **Teclados predictivos (solo con supervisión)**: **No configurado** permite usar teclados predictivos para sugerir las palabras que es posible que el usuario quiera. **Bloquear** impide esta característica.
- **Autocorrección (solo con supervisión)**: **No configurado** permite que el dispositivo corrija automáticamente las palabras mal escritas. **Bloquear** impide usar la autocorrección.
- **Revisión ortográfica de teclado (solo con supervisión)**: **No configurado** permite usar el corrector ortográfico del dispositivo. **Bloquear** permite el corrector ortográfico.
- **Métodos abreviados de teclado (solo con supervisión)**: **No configurado** permite usar los métodos abreviados de teclado del dispositivo. **Bloquear** impide que el usuario use los métodos abreviados de teclado.
- **Dictado (solo con supervisión)**: **Bloquear** impide que el usuario use la entrada de voz para escribir texto. **No configurado** permite que el usuario use la entrada de dictado.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

- **Copia de seguridad en iCloud**: **No configurado** permite que el usuario cree una copia de seguridad del dispositivo en iCloud. **Bloquear** impide que el usuario cree una copia de seguridad del dispositivo en iCloud.
- **Bloquear la sincronización de documentos en iCloud**: **No configurado** permite la sincronización de documentos y pares clave-valor con el espacio de almacenamiento de iCloud. **Bloquear** impide que iCloud sincronice documentos y datos.
- **Sincronización de Photo Stream en iCloud**: **No configurado** permite que los usuarios habiliten **My Photo Stream** en su dispositivo para sincronizar en iCloud y que las fotos estén disponibles en todos los dispositivos del usuario. **Bloquear** impide la sincronización de Photo Stream en iCloud.
- **Copia de seguridad cifrada**: **Requerir** que las copias de seguridad del dispositivos sean cifradas.
- **Fototeca de iCloud**: establezca en **Bloquear** para deshabilitar el uso de la Fototeca de iCloud para almacenar fotos y vídeos en la nube. Las fotos que no se hayan descargado de la Fototeca de iCloud en el dispositivo se quitarán del dispositivo. **No configurado** permite usar la Fototeca de iCloud.
- **Sincronización de aplicaciones administradas con la nube**: **No configurado** permite que Intune administre las aplicaciones para sincronizar los datos con la cuenta de iCloud del usuario. **Bloquear** impide que estos datos se sincronicen con iCloud.
- **Uso compartido de Photo Stream**: elija **Bloquear** para deshabilitar **Fotos compartidas en iCloud** en el dispositivo. **No configurado** permite las fotos compartidas.
- **Continuación de la actividad**: **No configurado** permite que los usuarios continúen el trabajo que inició en un dispositivo iOS en otro dispositivo iOS o macOS (entrega). **Bloquear** impide esta entrega.
- **Bloquear la sincronización de Keychain en iCloud**: elija **Bloquear** para deshabilitar la sincronización de las credenciales almacenadas en Keychain en iCloud. **No configurado** permite que los usuarios sincronicen estas credenciales.
- **Bloquear la copia de seguridad de libros empresariales**: elija **Bloquear** para impedir que los usuarios hagan una copia de seguridad de libros empresariales. **No configurado** permite que los usuarios hagan una copia de seguridad de estos libros.
- **Bloquear la sincronización de metadatos de libros empresariales (notas y eventos destacados)**: **Bloquear** impide la sincronización de notas y eventos destacados en los libros empresariales. **No configurado** permite la sincronización.

## <a name="autonomous-single-app-mode-supervised-only"></a>Modo de aplicación única autónoma (solo supervisado)

Use estos valores para configurar los dispositivos iOS de modo que ejecuten aplicaciones específicas en modo de aplicación única autónoma. Cuando se configura este modo y se ejecuta la aplicación, el dispositivo se bloquea. Solo puede ejecutar esa aplicación. Por ejemplo, agregue una aplicación que permita que los usuarios hagan una prueba en el dispositivo. Cuando se completan las acciones de la aplicación o quita esta directiva, el dispositivo vuelve a su estado normal.

Para agregar aplicaciones, puede:

- Escribir el **nombre de la aplicación** y el **identificador del lote de aplicaciones** y seleccionar **Agregar**. En la sección [Identificadores de lote para aplicaciones iOS integradas](#bundle-ids-for-built-in-ios-apps) (en este artículo) se incluyen algunas aplicaciones con sus identificadores.
- **Importar** un archivo .csv con la lista de nombres de aplicaciones y sus identificadores de lote. O bien puede **Exportar** una lista existente que incluya las aplicaciones.

## <a name="kiosk-supervised-only"></a>Pantalla completa (solo supervisado)

- **Aplicación para ejecutar en pantalla completa**: elija el tipo de aplicaciones que quiere que se ejecuten en pantalla completa. Las opciones son:
  - **No configurado**: no se aplican las opciones de pantalla. El dispositivo no se ejecuta en modo de quiosco.
  - **Aplicación de la tienda**: escriba la dirección URL de una aplicación de la tienda de aplicaciones de iTunes.
  - **Aplicación administrada**: elija una aplicación que haya agregado a Intune.
  - **Aplicación integrada**: escriba el [Id. de lote](#bundle-ids-for-built-in-ios-apps) (en este artículo) de la aplicación integrada.

- **AssistiveTouch**: **Requerir** que la configuración de accesibilidad AssistiveTouch se establezca en el dispositivo. Esta característica ayuda a los usuarios con gestos en pantalla que podrían ser difíciles para ellos. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Invertir colores**: **Requerir** la configuración de accesibilidad Invertir colores para que los usuarios con discapacidades visuales puedan cambiar la pantalla. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Audio mono**: **Requerir** que la configuración de accesibilidad Audio mono esté establecida en el dispositivo. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **VoiceOver**: **Requerir** la configuración de accesibilidad VoiceOver esté establecida en el dispositivo para leer en voz alta el texto en pantalla. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Zoom**: **Requerir** que la configuración de Zoom esté establecida en el dispositivo para que los usuarios usen un toque para acercar en la pantalla. **No configurado** no ejecuta ni permite esta característica en pantalla completa.
- **Bloqueo automático**: **Permitir** el bloqueo automático del dispositivo. **No configurado** deshabilita esta característica.
- **Cambio de timbre**: **Permitir** el cambio de timbre (silencio) en el dispositivo. **No configurado** deshabilita esta característica.
- **Rotación de pantalla**: **Permitir** cambia la orientación de la pantalla cuando el usuario gira el dispositivo. **No configurado** deshabilita esta característica.
- **Botón de suspensión de pantalla**: elija **Permitir** para deshabilitar el botón de reactivación de suspensión de pantalla del dispositivo. **No configurado** habilita esta característica.
- **Toque**: **Bloquear** deshabilita la pantalla táctil del dispositivo **No configurado** permite que el usuario use la pantalla táctil.
- **Botones de volumen**: **Permitir** el uso de los botones de volumen del dispositivo. **No configurado** deshabilita los botones de volumen.
- **Control de AssistiveTouch**: **Permitir** deja que los usuarios usen la función AssistiveTouch. **No configurado** deshabilita esta característica.
- **Control Invertir colores**: **Permitir** invierte los cambios de colores para que los usuarios puedan ajustar la función Invertir colores. **No configurado** deshabilita esta característica.
- **Leer el texto seleccionado**: **Permitir** que la configuración de accesibilidad Reproducir selección esté establecida en el dispositivo. Esta característica lee en voz alta el texto seleccionado por el usuario. **No configurado** deshabilita esta característica.
- **Control de VoiceOver**: **Permitir** cambios en VoiceOver para que los usuarios puedan actualizar la función VoiceOver, por ejemplo, la velocidad con que el texto en pantalla se lee en voz alta. **No configurado** impide los cambios en VoiceOver.
- **Control de zoom**: **Permitir** que el usuario haga cambios en el zoom. **No configurado** impide cambios en el zoom.

> [!NOTE]
> Antes de configurar un dispositivo iOS para pantalla completa, debe usar la herramienta Apple Configurator o el Programa de inscripción de dispositivos de Apple para pasar el dispositivo al modo supervisado. Consulte la guía de Apple sobre cómo usar la herramienta Apple Configurator.
> Si la aplicación iOS que escriba se instala después de asignar el perfil, el dispositivo no ingresará en el modo de pantalla completa hasta que se reinicie el dispositivo.

## <a name="domains"></a>Domains

- **Dominios de correo electrónico sin marcar** > **dirección URL del dominio de correo electrónico**: agregar una o más direcciones URL a la lista. Cuando los usuarios finales reciben un correo electrónico de un dominio distinto de los dominios que especifica, el correo electrónico se marca como correo electrónico no de confianza en la aplicación Mail de iOS.

- **Dominios web administrados** > **dirección URL del dominio Web**; Agregar una o más direcciones URL a la lista. Los documentos que se descargan de los dominios que especifica se consideran administrados. Esta configuración solo se aplica a los documentos que se descargan con el explorador Safari.

- **Dominios de relleno automático de contraseña de Safari** > **dirección URL del dominio**: agregar una o más direcciones URL a la lista. Los usuarios solo pueden guardar contraseñas web de las direcciones URL que aparecen en esta lista. Esta configuración solo se aplica al explorador Safari y a dispositivos iOS 9.3 y versiones posteriores en modo supervisado. Si no especifica ninguna dirección URL, se podrán guardar contraseñas de todos los sitios web.

## <a name="bundle-ids-for-built-in-ios-apps"></a>Identificadores de lote para aplicaciones iOS integradas

En la lista siguiente se muestra el identificador de lote de algunas aplicaciones iOS integradas comunes. Póngase en contacto con el proveedor de software para encontrar el identificador de lote de otras aplicaciones.

| Identificador de lote                   | Nombre de la aplicación     | Publicador |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | Tienda de aplicaciones    | Apple     |
| com.apple.calculator        | Calculadora   | Apple     |
| com.apple.mobilecal         | Calendario     | Apple     |
| com.apple.camera            | Cámara       | Apple     |
| com.apple.mobiletimer       | Reloj        | Apple     |
| com.apple.compass           | Compass      | Apple     |
| com.apple.MobileAddressBook | Contactos     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | Archivos        | Apple     |
| com.apple.mobileme.fmf1     | Buscar amigos | Apple     |
| com.apple.mobileme.fmip1    | Buscar mi iPhone  | Apple     |
| com.apple.gamecenter        | Centro de juegos  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Mantenimiento       | Apple     |
| com.apple.Home              | Inicio         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | Asignaciones         | Apple     |
| com.apple.MobileSMS         | Mensajes     | Apple     |
| com.apple.Music             | Música        | Apple     |
| com.apple.news              | Noticias         | Apple     |
| com.apple.mobilenotes       | Notas        | Apple     |
| com.apple.Numbers           | Números      | Apple     |
| com.apple.Pages             | Páginas        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Fotos       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | Recordatorios    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Configuración     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Acciones       | Apple     |
| com.apple.tips              | Sugerencias         | Apple     |
| com.apple.TV                | TV           | Apple     |
| com.apple.videos            | Vídeos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Inspección        | Apple     |
| com.apple.weather           | Clima      | Apple     |

## <a name="settings-that-require-supervised-mode"></a>Configuración que requieren el modo supervisado

El modo supervisado de iOS solo se puede habilitar durante la configuración inicial del dispositivo a través del Programa de inscripción de dispositivos de Apple o con Apple Configurator. Una vez activado el modo supervisado, Intune puede configurar un dispositivo con la funcionalidad siguiente:

- Bloqueo de aplicaciones (modo de aplicación única) 
- Proxy HTTP global 
- Bypass del bloqueo de activación 
- Modo de aplicación única autónoma 
- Filtro de contenido web 
- Establecer la pantalla de fondo y la pantalla de bloqueo 
- Inserción de aplicación silenciosa 
- VPN Always-On 
- Permitir la instalación de aplicaciones administradas de forma exclusiva 
- iBookstore 
- iMessages 
- Centro de juegos 
- AirDrop 
- AirPlay 
- Emparejamiento de host 
- Sincronización en la nube 
- Búsqueda en Spotlight 
- Handoff 
- Borrar dispositivo 
- Interfaz de usuario de restricciones 
- Instalación de perfiles de configuración por interfaz de usuario 
- Noticias 
- Accesos directos del teclado 
- Modificaciones de código de acceso 
- Cambios en los nombres de dispositivos 
- Descargas de aplicaciones automáticas 
- Cambios en la confianza de las aplicaciones empresariales 
- Apple Music 
- Mail Drop 
- Emparejamiento con Apple Watch 

> [!NOTE]
> Apple ha confirmado que ciertas opciones de configuración se trasladan al modo de solo supervisión en 2019. Le recomendamos que lo tenga en cuenta a la hora de usar estas opciones, en lugar de esperar a que Apple las migre al modo de solo supervisión:
> - Instalación de la aplicación por los usuarios finales
> - Eliminación de aplicaciones
> - FaceTime
> - Safari
> - iTunes
> - Contenido explícito
> - Documentos y datos de iCloud
> - Juego multijugador
> - Agregar amigos del centro de juegos
> - Siri

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede restringir la configuración y características de dispositivos en [macOS](device-restrictions-macos.md) dispositivos.