---
title: 'Configuración de restricciones de dispositivos para Windows 10 en Microsoft Intune: Azure | Microsoft Docs'
description: Descubra las opciones de configuración de Microsoft Intune que puede usar para controlar la funcionalidad y la configuración de los dispositivos que ejecutan Windows 10.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a4bbc89f66b49fe6a5c4ff8595c5913583288e0f
ms.sourcegitcommit: d1420a5d2d2c1da40cc4dac165ca9173c22323d3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2018
ms.locfileid: "34803846"
---
# <a name="device-restriction-for-windows-10-and-newer-settings-in-intune"></a>Restricciones de dispositivos para la configuración de Windows 10 (y versiones posteriores) en Intune
En este artículo, se muestran todas las opciones de configuración de restricciones de dispositivos de Microsoft Intune que puede configurar para los dispositivos que ejecutan Windows 10.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="general"></a>General
- **Captura de pantalla (solo móviles)**: permite que el usuario capture la pantalla del dispositivo como imagen.
- **Copiar y pegar (solo móviles)**: permite acciones de copiar y pegar entre aplicaciones del dispositivo.
- **Cancelación manual de la suscripción**: permite al usuario eliminar manualmente la cuenta del área de trabajo desde el dispositivo.
   - Esta configuración de directiva no se aplica si el equipo está unido a Azure Active Directory y la inscripción automática está habilitada. 
   - Esta configuración de directiva no se aplica a equipos que ejecuten Windows 10 Home.
- **Instalación manual del certificado raíz (solo móviles)**: impide que el usuario instale manualmente certificados raíz y certificados CAP intermedios.

- **Cámara**: permite o bloquea el uso de la cámara en el dispositivo.
- **Sincronización de archivos de OneDrive**: bloquea la sincronización de archivos de OneDrive en el dispositivo.
- **Almacenamiento extraíble**: especifica si se pueden usar dispositivos de almacenamiento externo, como tarjetas SD, con el dispositivo.
- **Geolocation** (Geolocalización): especifica si el dispositivo puede usar la información de servicios de ubicación.
- **Conexión compartida**: permite el uso compartido de una conexión a Internet en el dispositivo.
- **Restablecimiento del teléfono**: controla si el usuario puede restablecer su dispositivo a la configuración de fábrica.
- **Conexión USB (solo móviles)**: controla si los dispositivos pueden tener acceso a dispositivos de almacenamiento externo a mediante una conexión USB.
- **Modo antirrobo (solo móviles)**: permite habilitar el modo antirrobo de Windows.
- **Cortana**: habilita o deshabilita el asistente de voz de Cortana.
- **Grabación de voz (solo móviles)**: permite o bloquea el uso de la grabadora de voz del dispositivo.
- **Modificación del nombre del dispositivo**: evita que el usuario final cambie el nombre del dispositivo (solo para Windows 10 Mobile)
- **Agregar paquetes de aprovisionamiento**: bloquea el agente de configuración de tiempo de ejecución que instala paquetes de aprovisionamiento.
- **Quitar paquetes de aprovisionamiento**: bloquea el agente de configuración de tiempo de ejecución que quita paquetes de aprovisionamiento.
- **Detección de dispositivos**: bloquea la detección de un dispositivo por parte de otros dispositivos.
- **Conmutador de tareas (solo móviles)**: bloquea el conmutador de tareas en el dispositivo.
- **Cuadro de diálogo de error de tarjeta SIM (solo móviles)**: impide que un mensaje de error se muestre en el dispositivo si no se detecta una tarjeta SIM.
- **Área de trabajo de Ink**: impida que los usuarios accedan al área de trabajo de Ink. Cuando este valor no está configurado, se habilita el área de trabajo de Ink (se activa la característica) y el usuario puede usarla más allá de la pantalla de bloqueo.
- **Reimplementación automática**: permite a los usuarios con derechos administrativos eliminar todos los datos de usuario y las opciones de configuración con **Ctrl + Win + R** en la pantalla de bloqueo del dispositivo. En este caso, el dispositivo se vuelve a configurar e inscribir automáticamente para la administración.

## <a name="password"></a>Contraseña
-   **Contraseña**: exige que el usuario final escriba una contraseña para acceder al dispositivo.
    -   **Tipo de contraseña necesaria**: especifica si la contraseña debe ser solo numérica o alfanumérica.
    -   **Minimum password length** (Longitud mínima de contraseña): solo se aplica a Windows 10 Mobile.
    -   **Número de errores de inicio de sesión antes de borrar el dispositivo**: para dispositivos que ejecutan Windows 10: si el dispositivo tiene habilitado BitLocker, se pondrá en el modo de recuperación de BitLocker si el inicio de sesión produce error el número de veces especificado. Si el dispositivo no tiene habilitado BitLocker, no se aplica esta configuración.
Para los dispositivos que ejecutan Windows 10 Mobile: si el inicio de sesión falla el número de veces especificado, el dispositivo se borrará.
    -   **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique la longitud de tiempo que un dispositivo debe estar inactivo antes de que se bloquee la pantalla.
    -   **Caducidad de la contraseña (días)**: especifica el período de tiempo transcurrido el cual debe cambiarse la contraseña del dispositivo.
    -   **Impedir la reutilización de contraseñas anteriores**: especifica el número de contraseñas usadas anteriormente que se recuerdan el dispositivo.
    -   **Requerir contraseña cuando el dispositivo vuelve de un estado de inactividad (solo móviles)**: especifica que el usuario debe escribir una contraseña para desbloquear el dispositivo (solo Windows 10 Mobile).
    -   **Contraseñas sencillas**: le permite el uso de contraseñas sencillas, como 1111 y 1234. Esta configuración también permite o bloquea el uso de contraseñas de imagen de Windows.
-   **Cifrado**: habilita el cifrado en dispositivos de destino.

## <a name="personalization"></a>Personalization

- **Dirección URL de imagen de fondo de escritorio (solo escritorio)**: especifica la dirección URL de una imagen en formato JPEG que quiere usar como fondo de escritorio de Windows. Los usuarios no pueden cambiar esto.

## <a name="privacy"></a>Privacidad

-   **Personalización de entrada**: no permite el uso de servicios de voz basados en la nube para Cortana, Dictado o aplicaciones de Microsoft Store. Si permite estos servicios, Microsoft puede recopilar datos de voz para mejorar el servicio.
-   **Aceptación automática de los mensajes de consentimiento del usuario sobre emparejamiento y privacidad**: permite que Windows acepte automáticamente los mensajes de consentimiento sobre emparejamiento y privacidad al ejecutar las aplicaciones.
- **Publicar las actividades del usuario**: establezca esta propiedad en **Bloquear** para evitar experiencias compartidas y la detección de recursos usados recientemente en el selector de tareas.
- **Solo actividades locales**: establezca esta propiedad en **Bloquear** para evitar experiencias compartidas y la detección de recursos usados recientemente en el selector de tareas según la actividad local únicamente.

Puede definir la información a la que pueden tener acceso todas las aplicaciones del dispositivo. Puede definir excepciones para cada aplicación mediante **excepciones de privacidad de cada aplicación**.

### <a name="exceptions"></a>Excepciones

- **Información de la cuenta**: define si esta aplicación puede tener acceso al nombre de usuario, las imágenes u otra información de contacto.
- **Aplicaciones en segundo plano**: define si esta aplicación puede ejecutarse en segundo plano.
- **Calendario**: define si esta aplicación puede tener acceso al calendario.
- **Historial de llamadas**: define si esta aplicación puede tener acceso al historial de llamadas.
- **Cámara**: define si esta aplicación puede tener acceso a la cámara.
- **Contactos**: define si esta aplicación puede tener acceso a los contactos.
- **Correo electrónico**: define si esta aplicación puede tener acceso al correo electrónico.
- **Ubicación**: define si esta aplicación puede tener acceso a información de ubicación.
- **Mensajería**: define si esta aplicación puede leer o enviar mensajes de texto o MMS.
- **Micrófono**: define si esta aplicación puede usar el micrófono.
- **Movimiento**: define si esta aplicación puede tener acceso a información de movimiento.
- **Notificaciones**: define si esta aplicación puede tener acceso a las notificaciones.
- **Teléfono**: define si esta aplicación puede tener acceso al teléfono.
- **Radios**: algunas aplicaciones usan radios (por ejemplo, Bluetooth) en el dispositivo para enviar y recibir datos y necesitan activar o desactivar estas radios. Define si esta aplicación puede controlar estas radios.
- **Tareas**: define si esta aplicación puede tener acceso a las tareas.
- **Dispositivos de confianza**: define si esta aplicación puede usar dispositivos de confianza (hardware ya conectado o que se proporciona con este PC, tableta o teléfono). Por ejemplo: televisores, proyectores, etc.
- **Comentarios y diagnóstico**: define si esta aplicación puede tener acceso a la información de diagnóstico.
- **Sincronización con dispositivos**: define si esta aplicación puede compartir y sincronizar información automáticamente con dispositivos inalámbricos que no se emparejan explícitamente con este PC, tableta o teléfono.

## <a name="per-app-privacy-exceptions"></a>Excepciones de privacidad para cada aplicación

Puede agregar aplicaciones que deben tener un comportamiento de privacidad diferente del definido en "Privacidad determinada".

- **Nombre del paquete**: nombre de la familia del paquete de aplicaciones.
- **Nombre de la aplicación**: el nombre de la aplicación.

### <a name="exceptions"></a>Excepciones

- **Información de la cuenta**: define si esta aplicación puede tener acceso al nombre de usuario, las imágenes u otra información de contacto.
- **Aplicaciones en segundo plano**: define si esta aplicación puede ejecutarse en segundo plano.
- **Calendario**: define si esta aplicación puede tener acceso al calendario.
- **Historial de llamadas**: define si esta aplicación puede tener acceso al historial de llamadas.
- **Cámara**: define si esta aplicación puede tener acceso a la cámara.
- **Contactos**: define si esta aplicación puede tener acceso a los contactos.
- **Correo electrónico**: define si esta aplicación puede tener acceso al correo electrónico.
- **Ubicación**: define si esta aplicación puede tener acceso a información de ubicación.
- **Mensajería**: define si esta aplicación puede leer o enviar mensajes de texto o MMS.
- **Micrófono**: define si esta aplicación puede usar el micrófono.
- **Movimiento**: define si esta aplicación puede tener acceso a información de movimiento.
- **Notificaciones**: define si esta aplicación puede tener acceso a las notificaciones.
- **Teléfono**: define si esta aplicación puede tener acceso al teléfono.
- **Radios**: algunas aplicaciones usan radios (por ejemplo, Bluetooth) en el dispositivo para enviar y recibir datos y necesitan activar o desactivar estas radios. Define si esta aplicación puede controlar estas radios.
- **Tareas**: define si esta aplicación puede tener acceso a las tareas.
- **Dispositivos de confianza**: define si esta aplicación puede usar dispositivos de confianza (hardware ya conectado o que se proporciona con este PC, tableta o teléfono). Por ejemplo: televisores, proyectores, etc.
- **Comentarios y diagnóstico**: define si esta aplicación puede tener acceso a la información de diagnóstico.
- **Sincronización con dispositivos**: define si esta aplicación puede compartir y sincronizar información automáticamente con dispositivos inalámbricos que no se emparejan explícitamente con este PC, tableta o teléfono.

## <a name="locked-screen-experience"></a>Experiencia de pantalla bloqueada

- **Notificaciones del centro de actividades (solo móviles)**: permite que las notificaciones del centro de actividades aparezcan en la pantalla de bloqueo del dispositivo (solo Windows 10 Mobile).
- **URL de imagen de pantalla de bloqueo (solo equipos de escritorio)**: especifica la URL de una imagen en formato JPEG que se usará como papel tapiz de la pantalla de bloqueo de Windows. Los usuarios no pueden cambiar esto.
-   **Tiempo de espera de la pantalla configurable por el usuario (solo dispositivos móviles)**: permite que los usuarios configuren la cantidad de tiempo 
-   **Cortana en pantalla bloqueada (solo escritorio)**: no permite que el usuario interactúe con Cortana cuando el dispositivo está en la pantalla de bloqueo (solo para equipos de escritorio de Windows 10).
-   **Notificaciones del sistema en pantalla bloqueada**: impide que los mensajes de alerta se muestren en la pantalla de bloqueo del dispositivo.
-   **Tiempo de espera de la pantalla (solo dispositivos móviles)**: especifica el tiempo en segundos después de que se bloquee la pantalla, cuando se apagará.

## <a name="app-store"></a>Tienda de aplicaciones

-   **Tienda de aplicaciones (solo móvil)**: permitir o bloquear el uso de la tienda de aplicaciones en dispositivos Windows 10 Mobile.
-   **Actualizar automáticamente las aplicaciones de la tienda**: permite que las aplicaciones instaladas de Microsoft Store se actualicen automáticamente.
-   **Instalación de aplicaciones de confianza**: permite realizar una instalación de prueba de las aplicaciones firmadas con un certificado de confianza.
-   **Desbloqueo de desarrollador**: permite que un usuario final modifique la configuración de desarrollador de Windows, como permitir las aplicaciones con instalación de prueba.
-   **Datos de aplicación compartidos entre usuarios**: permite que las aplicaciones compartan datos entre distintos usuarios en el mismo dispositivo.
-   **Usar solo una tienda privada**: habilite esta opción para permitir que los usuarios finales solo descarguen aplicaciones desde la tienda privada.
-   **Inicio de aplicaciones de la tienda**: se usa para deshabilitar todas las aplicaciones instaladas previamente en el dispositivo o que se descargaron de Microsoft Store.
-   **Instalar los datos de aplicación en el volumen del sistema**: esta opción hace que las aplicaciones dejen de almacenar datos en el volumen del sistema del dispositivo.
-   **Instalar las aplicaciones en la unidad del sistema**: esta opción hace que las aplicaciones dejen de almacenar datos en la unidad del sistema del dispositivo.
-   **Game DVR (solo escritorio)**: configura si se permite la grabación y difusión de los juegos.
-   **Aplicaciones solo de la tienda**: configura si los usuarios pueden instalar aplicaciones de otros lugares distintos de la tienda de aplicaciones.

## <a name="edge-browser"></a>Explorador Microsoft Edge

-   **Explorador de Microsoft Edge (solo móvil)**: permite el uso del explorador web Edge en el dispositivo.
-   **Lista desplegable de la barra de direcciones (solo escritorio)**: use esto para impedir que Edge muestre una lista de sugerencias en una lista desplegable cuando escriba. Esto ayuda a minimizar el uso del ancho de banda de red entre Microsoft Edge y servicios Microsoft.
-   **Sincronizar favoritos entre exploradores de Microsoft (solo escritorio)**: permite que Windows sincronice los favoritos entre Internet Explorer y Microsoft Edge.
-   **Enviar encabezados de no seguimiento**: configura el explorador Edge para que envíe encabezados de no seguimiento a sitios web que visitan los usuarios.
-   **Cookies**: permite que el explorador guarde cookies de Internet en el dispositivo.
-   **JavaScript**: permite la ejecución de scripts, como JavaScript, en el explorador Edge.
-   **Ventanas emergentes**: bloquea las ventanas emergentes en el explorador (solo se aplica a Windows 10 Escritorio).
-   **Search suggestions** (Sugerencias de búsqueda): permite que el motor de búsqueda sugiera sitios a medida que se escriben las frases de búsqueda.
-   **Enviar el tráfico de la intranet a Internet Explorer**: permite a los usuarios abrir sitios web de intranet en Internet Explorer (solo Windows 10 Escritorio).
-   **Rellenar automáticamente**: permite a los usuarios cambiar la configuración de Autocompletar en el explorador (solo Windows 10 Escritorio).
-   **Administrador de contraseñas**: habilita o deshabilita la característica de Administrador de contraseñas de Microsoft Edge.
-   **Ubicación de la lista de sitios del modo de empresa**: especifica dónde encontrar la lista de sitios web que se abren en modo de empresa. Los usuarios no pueden editar esta lista.<br>(Solo Windows 10 Escritorio)
-   **Herramientas de desarrollo**: impiden que el usuario final abra las herramientas de desarrollo de Microsoft Edge.
-   **Extensiones**: permiten que el usuario final instale extensiones de Microsoft Edge en el dispositivo.
-   **Exploración de InPrivate**: impide que el usuario final abra sesiones de exploración de InPrivate.
-   **Mostrar la página de la primera ejecución**: impide que la página de introducción aparezca la primera vez que ejecuta Edge.
    -   **URL de primera ejecución**: especifica la URL de una página que se muestra la primera vez que un usuario ejecuta Microsoft Edge (solo Windows 10 Mobile).
-   **Páginas principales**: agrega una lista de sitios que quiere usar como páginas principales en el explorador Microsoft Edge (solo escritorio).
-   **Cambia a la página de inicio**: permite que los usuarios cambien las páginas de inicio que se muestran cuando se abre Microsoft Edge. Use la configuración de páginas principales para crear la página o enumerar las páginas que se abren cuando se inicia Microsoft Edge.
-   **Bloquear acceso a about:flags**: impide que el usuario final tenga acceso a la página about:flags de Microsoft Edge que contiene la configuración experimental y de desarrollador.
-   **Dirección IP de localhost para WebRtc**: impide que la dirección IP de localhost de los usuarios se muestre cuando se hacen llamadas telefónicas a través del protocolo WebRtc.
-   **Motor de búsqueda predeterminado**: especifica el motor de búsqueda predeterminado que se usará. Los usuarios finales pueden cambiar este valor en cualquier momento.
-   **Borrar datos de navegación al salir**: borra el historial y los datos de navegación cuando el usuario sale de Edge.
-   **Recopilación de datos para iconos dinámicos**: impide que Windows recopile información de iconos dinámicos cuando los usuarios anclan un sitio al menú de inicio de Microsoft Edge.
-  **Lista de favoritos**: define la ruta de acceso al archivo de favoritos. Por ejemplo, http://contoso.com/favorites.html.
-  **Restringir los cambios a Favoritos**: establezca este valor en **Bloquear** para impedir que los usuarios agreguen, importen, ordenen o modifiquen la lista de favoritos. 

## <a name="windows-defender-smart-screen"></a>SmartScreen de Windows Defender

- **SmartScreen para Microsoft Edge**: permite a SmartScreen de Edge el acceso al sitio y las descargas de archivos.
- **Acceso a sitio malintencionado**: impide que los usuarios omitan las advertencias del filtro SmartScreen de Windows Defender y no permite que vayan al sitio.
- **Descarga de archivos no comprobados**: impide que los usuarios omitan las advertencias del filtro SmartScreen de Windows Defender y no permite que descarguen los archivos no comprobados.

## <a name="search"></a>Buscar
- **Búsqueda segura (solo móviles)**: controla cómo Cortana filtra contenido para adultos en los resultados de la búsqueda. Puede seleccionar **Strict** (Estricto), **Moderate** (Moderado) o permitir que el usuario final elija su propia configuración.
- **Mostrar resultados web en la búsqueda**: permita o no que aparezcan resultados web en las búsquedas realizadas en el dispositivo.

## <a name="cloud-and-storage"></a>Nube y almacenamiento
-   **Cuenta Microsoft**: permite al usuario asociar una cuenta de Microsoft con el dispositivo.
-   **Cuenta que no es Microsoft**: permite al usuario agregar al dispositivo cuentas de correo electrónico que no estén asociadas a una cuenta de Microsoft.
-   **Sincronización de configuración de cuenta Microsoft**: permite sincronizar la configuración de dispositivos y aplicaciones que están asociados con una cuenta de Microsoft entre dispositivos.

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad

-   **Canal de datos móviles**: impide que los usuarios usen datos, como la navegación por la web, cuando están conectados a una red móvil. 
-   **Itinerancia de datos**: permite la itinerancia entre redes al acceder a los datos.
-   **VPN a través de la red de telefonía móvil**: controla si el dispositivo puede acceder a las conexiones VPN cuando se conecta a una red móvil.
-   **Itinerancia de VPN a través de la red de telefonía móvil**: controla si el dispositivo puede acceder a conexiones VPN cuando está en itinerancia en una red móvil.
-   **Bluetooth**: controla si el usuario puede habilitar y configurar Bluetooth en el dispositivo.
-   **Detectabilidad de Bluetooth**: permite que otros dispositivos con Bluetooth habilitado detecten el dispositivo.
-   **Emparejamiento previo Bluetooth**: permite que configure dispositivos Bluetooth específicos para emparejarse automáticamente con un dispositivo de host.
-   **Anuncios de Bluetooth**: permite que el dispositivo reciba anuncios a través de Bluetooth.
-   **Servicio de dispositivos conectados**: permite decidir si permitir el servicio de dispositivos conectados, que habilita la detección y la conexión a otros dispositivos Bluetooth.
-   **NFC**: permite al usuario habilitar y configurar funcionalidades de transmisión de datos en proximidad en el dispositivo.
-   **Wi-Fi**: permite al usuario habilitar y configurar Wi-Fi en el dispositivo (solo Windows 10 Mobile).
-   **Conectar automáticamente a zonas Wi-Fi**: permite que el dispositivo se conecte automáticamente a zonas Wi-Fi gratuitas y acepte automáticamente los términos y condiciones para la conexión.
-   **Configuración manual de Wi-Fi**: controla si el usuario puede configurar sus propias conexiones Wi-Fi o si solo puede usar conexiones configuradas mediante un perfil Wi-Fi (solo Windows 10 Mobile).
-   **Intervalo de detección de Wi-Fi**: especifica con qué frecuencia los dispositivos detectan redes Wi-Fi. Especifique un valor de 1 (más frecuente) a 500 (menos frecuente).
-   **Servicios Bluetooth permitidos**: especifica como cadenas hexadecimales una lista de perfiles y servicios Bluetooth permitidos.

## <a name="control-panel-and-settings"></a>Panel de control y configuración

-   **Aplicación de configuración**: bloquea el acceso a la aplicación de configuración de Windows.
    -   **Sistema**: bloquea el acceso al área de sistema de la aplicación de configuración.
        -   **Modificación de la configuración de inicio/apagado y suspensión (solo escritorio)**: evita que el usuario final cambie la configuración de inicio/apagado y suspensión en el dispositivo.
    -   **Dispositivos**: bloquea el acceso al área de dispositivos de la aplicación de configuración.
    -   **Red e Internet**: bloquea el acceso al área de la red e Internet de la aplicación de configuración.
    -   **Personalización**: bloquea el acceso al área de personalización de la aplicación de configuración.
    -   **Cuentas**: bloquea el acceso al área de cuentas de la aplicación de configuración.
    -   **Hora e idioma**: bloquea el acceso al área de hora e idioma de la aplicación de configuración.
        -   **Modificación de la hora del sistema**: evita que el usuario final cambie la fecha y hora del dispositivo.
        -   **Modificación de la configuración regional (solo escritorio)**: evita que el usuario final cambie la configuración regional en el dispositivo.
        -   **Modificación de la configuración de idioma (solo escritorio)**: evita que el usuario cambie la configuración de idioma en el dispositivo.
    -   **Juegos**: bloquea el acceso a la aplicación Juegos en la configuración.
    -   **Accesibilidad**: bloquea el acceso al área de accesibilidad de la aplicación de configuración.
    -   **Privacidad**: bloquea el acceso al área de privacidad de la aplicación de configuración.
    -   **Actualización y seguridad**: bloquea el acceso al área de actualizaciones y seguridad de la aplicación de configuración.

## <a name="start"></a>Start

- **Desanclar aplicaciones de la barra de tareas**: impide que el usuario desancle aplicaciones del menú Inicio.
- **Documentos en Inicio**: oculta o muestra la carpeta Documentos en el menú Inicio de Windows.
- **Descargas en Inicio**: oculta o muestra la carpeta Descargas en el menú Inicio de Windows.
- **Explorador de archivos en Inicio**: oculta o muestra la aplicación Explorador de archivos en el menú Inicio de Windows.
- **Grupo Hogar en Inicio**: oculta o muestra la carpeta Grupo Hogar en el menú Inicio de Windows.
- **Música en Inicio**: oculta o muestra la carpeta Música en el menú Inicio de Windows.
- **Red en Inicio**: oculta o muestra la carpeta Red en el menú Inicio de Windows.
- **Carpeta Personal en Inicio**: oculta o muestra la carpeta Personal en el menú Inicio de Windows.
- **Imágenes en Inicio**: oculta o muestra la carpeta de imágenes en el menú Inicio de Windows.
- **Configuración en Inicio**: oculta o muestra la aplicación Configuración en el menú Inicio de Windows.
- **Vídeos en Inicio**: oculta o muestra la carpeta de vídeos en el menú Inicio de Windows.

## <a name="display"></a>Pantalla

- **Activar el ajuste de GDI para las aplicaciones**
- **Desactivar el ajuste de GDI para las aplicaciones**

  El ajuste de escala de PPP de GDI permite a las aplicaciones que no tienen en cuenta los PPP empezar a tenerlos en cuenta para cada monitor. Especifique las aplicaciones heredadas que tienen activado el ajuste de escala de PPP de GDI. Si el ajuste de escala de PPP de GDI está configurado para activarse y desactivarse en una aplicación, el ajuste de escala estará desactivado para la aplicación.

## <a name="kiosk-preview---obsolete"></a>Quiosco (versión preliminar): obsoleto

Esta configuración se está moviendo y se quitará en una próxima versión. Para usar la nueva configuración, consulte [Configuración de quiosco para Windows 10 (y versiones posteriores) en Intune](kiosk-settings.md).

Un dispositivo de pantalla completa normalmente ejecuta una aplicación o un conjunto determinado de aplicaciones. A los usuarios no se les permite el acceso a características o funciones del dispositivo que está fuera de la aplicación de pantalla completa.

- **Pantalla completa**: identifica el tipo de pantalla completa admitido por la directiva. Las opciones son:

  - **No configurado** (valor predeterminado): la directiva no habilita una pantalla completa. 
  - **Pantalla completa con una sola aplicación**: el perfil permite que el dispositivo solo ejecute una aplicación. Cuando el usuario inicia sesión, se inicia una aplicación concreta. Este modo también evita que el usuario abra nuevas aplicaciones o modifique la aplicación en ejecución.
  - **Pantalla completa con varias aplicaciones**: el perfil permite que el dispositivo ejecute varias aplicaciones. Solo las aplicaciones que agregue están disponibles para el usuario. La ventaja de una pantalla completa con varias aplicaciones, o un dispositivo de propósito fijo, es proporcionar una experiencia fácil de entender para los usuarios gracias al acceso únicamente a las aplicaciones que necesitan y la retirada de la vista de las aplicaciones que no necesitan.

#### <a name="single-app-kiosks"></a>Pantallas completas con una sola aplicación
Escriba los valores siguientes:

- **Cuenta de usuario**: especifique la cuenta de usuario local (en el dispositivo), una cuenta de dominio de AD o el inicio de sesión de cuenta de Azure AD asociado a la aplicación de pantalla completa.
  - Cuenta local: escríbala como `devicename\accountname`, `.\accountname` o `accountname`.
  - Cuenta de dominio: escríbala como `domain\accountname`.
  - Cuenta de Azure AD: escríbala como `AzureAD\emailaddress`. Asegúrese de escribir "AzureAD", ya que es un nombre de dominio fijo. Después, siga con la dirección de correo electrónico de Azure AD. Por ejemplo, escriba `AzureAD\user@contoso.onmicrosoft.com`.

    En el caso de las pantallas completas en entornos de uso público con inicio de sesión automático habilitado, se debe usar un tipo de usuario con los privilegios mínimos (por ejemplo, la cuenta de usuario estándar local). Si usa una cuenta de Azure AD para el modo de pantalla completa, asegúrese de especificar `AzureAD\user@yourorganization.com`.

- **Identificador de modelo de usuario de la aplicación (AUMID)**: especifique el AUMID de la aplicación de pantalla completa. Para más información, vea [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Buscar el identificador de modelo de usuario de aplicación de una aplicación instalada).

#### <a name="multi-app-kiosks"></a>Pantallas completas con varias aplicaciones
Las [pantallas completas con varias aplicaciones](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) usan una configuración de pantalla completa que muestra las aplicaciones permitidas y otras opciones. 

Use el botón **Agregar** para crear una configuración de pantalla completa (o seleccionar una existente). Luego, escriba los valores siguientes:

- **Nombre de la configuración de quiosco**: escriba un nombre descriptivo que se use para identificar la configuración.

- **Aplicaciones de quiosco**: especifique las aplicaciones disponibles en el menú Inicio. Las aplicaciones que agregue son las únicas que el usuario puede abrir.

  - **Tipo de aplicación**: elija el tipo de la aplicación de pantalla completa:
    - **Aplicación Win32**: una aplicación de escritorio tradicional Necesita el nombre/ruta de acceso completo del archivo ejecutable correspondiente al dispositivo.
    - **Aplicación para UWP**: una aplicación Windows universal. Necesita el [AUMID de la aplicación](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

  - **Identificador**: especifique el nombre o ruta de acceso completo del archivo ejecutable (aplicaciones Win32) o el [AUMID de aplicación](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (aplicaciones para UWP).

- **Barra de tareas**: elija **Habilitar** (mostrar) la barra de tareas o mantenerla **No configurada** (oculta) en la pantalla completa.

- **Diseño del menú Inicio**: especifique un archivo XML que describa el modo en que las aplicaciones aparecen en el menú Inicio. [Personalizar y exportar el diseño de la pantalla Inicio](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) proporciona algunas instrucciones y XML de ejemplo.


  [Crear un quiosco de Windows 10 que ejecute varias aplicaciones](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file) proporciona más detalles sobre cómo usar y crear archivos XML.

- **Usuarios asignados**: agregue una o varias cuentas de usuario que puedan usar las aplicaciones agregadas. Cuando la cuenta inicia sesión, solo están disponibles las aplicaciones definidas en la configuración. La cuenta de usuario puede ser local en el dispositivo o un inicio de sesión de cuenta de Azure AD asociada a la aplicación de pantalla completa.

    En el caso de las pantallas completas en entornos de uso público con inicio de sesión automático habilitado, se debe usar un tipo de usuario con los privilegios mínimos (por ejemplo, la cuenta de usuario estándar local). Para configurar una cuenta de Azure Active Directory (AD) para el modo de pantalla completa, use el formato `domain\user@tenant.com`.

## <a name="windows-defender-antivirus"></a>Antivirus de Windows Defender

-   **Supervisión en tiempo real**: habilita el análisis en tiempo real de malware, spyware y otro software no deseado.
-   **Supervisión de comportamiento**: permite a Defender comprobar determinados patrones conocidos de actividad sospechosa en los dispositivos.
-   **Sistema de inspección de red (NIS)**: NIS ayuda a proteger los dispositivos contra las vulnerabilidades de seguridad basadas en red. Usa las firmas de vulnerabilidades conocidas de Microsoft Endpoint Protection Center para ayudar a detectar y bloquear el tráfico malintencionado.
-   **Analizar todas las descargas**: controla si Defender examina todos los archivos descargados de Internet.
-   **Examinar scripts cargados en exploradores web de Microsoft**: permite a Defender examinar scripts que se usan en Internet Explorer.
-   **Acceso de usuario final a Defender**: controla si la interfaz de usuario de Windows Defender se oculta a los usuarios finales.
Cuando se cambia esta configuración, surtirá efecto la próxima vez que se reinicie el equipo del usuario final.
-   **Intervalo de actualización de firma (en horas)**: especifica el intervalo dentro del cual Defender comprobará nuevos archivos de firmas.
-   **Supervisar la actividad de archivos y programas**: permite que Defender supervise la actividad de archivos y programas en los dispositivos.
-   **Días antes de eliminar el malware en cuarentena**: permite que Defender continúe realizando el seguimiento de malware resuelto durante el número de días especificado para que pueda comprobar de forma manual los dispositivos previamente afectados. Si establece el número de días en **0**, el malware permanece en la carpeta de cuarentena y no se quita automáticamente.
-   **Límite de uso de la CPU durante un examen**: le permite limitar la cantidad de CPU que pueden usar los exámenes (de **1** a **100**).
-   **Examinar archivos de almacenamiento**: permite que Defender examine archivos almacenados, como archivos .zip o .cab.
-   **Examinar mensajes de correo entrante**: permite que Defender examine mensajes de correo electrónico cuando llegan al dispositivo.
-   **Examinar unidades extraíbles durante un examen completo**: permite que Defender examine unidades extraíbles, como llaves USB.
-   **Examinar unidades de red asignadas durante un examen completo**: permite que Defender examine archivos en unidades de red asignadas.<br>Si los archivos de la unidad son de solo lectura, Defender no puede quitar el malware que se encuentre en ellos.
-   **Examinar archivos abiertos desde carpetas de red**: permite que Defender examine archivos en unidades de red compartidas (por ejemplo, los archivos a los que se tiene acceso desde una ruta de acceso UNC).
Si los archivos de la unidad son de solo lectura, Defender no puede quitar el malware que se encuentre en ellos.
-   **Protección de la nube**: permite o bloquea la recepción por parte de Microsoft Active Protection Service de información relativa a la actividad de malware de los dispositivos que administra. Esta información se usa para mejorar el servicio en el futuro.
-   **Preguntar a los usuarios antes de enviar muestras**: controla si los archivos potencialmente malintencionados que podrían requerir un análisis posterior se envían automáticamente a Microsoft.
-   **Hora a la que se realizará un examen rápido diario**: permite programar un examen rápido que se produce diariamente en el momento seleccionado.
-   **Tipo de examen del sistema para realizar**: le permite especificar el nivel de examen que se realiza cuando se programe un examen del sistema.
-   **Detectar aplicaciones potencialmente no deseadas**: elija el nivel de protección cuando Windows detecte aplicaciones potencialmente no deseadas entre:
        - **Bloquear**
        - **Auditar** Para obtener más información sobre las aplicaciones potencialmente no deseadas, vea [este tema](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
-   **Acciones para amenazas de malware detectadas**: habilite esta opción para especificar las acciones que quiere que Defender realice para cada nivel de amenaza que detecte (Bajo, Moderado, Alto y Grave). Las acciones que puede realizar son:
    -   **Limpiar**
    -   **Cuarentena**
    -   **Quitar**
    -   **Permitir**
    -   **Definido por el usuario**
    -   **Bloquear**

### <a name="windows-defender-antivirus-exclusions"></a>Exclusiones del antivirus de Windows Defender

-   **Archivos y carpetas para excluir de exámenes y protección en tiempo real**: agrega uno o varios archivos y carpetas, como **C:\Path** o **%ProgramFiles%\Path\filename.exe** a la lista de exclusiones. Estos archivos y carpetas no se incluyen en los exámenes en tiempo real ni programados.
-   **Extensiones de archivo para excluir de exámenes y protección en tiempo real**: agrega una o varias extensiones de archivo, como **jpg** o **txt** a la lista de exclusiones. Los archivos con estas extensiones no se incluyen en los exámenes en tiempo real ni programados.
-   **Procesos para excluir de exámenes y protección en tiempo real**: agregar uno o varios procesos del tipo **.exe**, **.com** o **.scr** a la lista de exclusiones. Estos procesos no se incluyen en los exámenes en tiempo real ni programados.

## <a name="network-proxy"></a>Proxy de red

-   **Detectar automáticamente configuración de proxy**: cuando esta opción está habilitada, el dispositivo intenta encontrar la ruta de acceso a un script de configuración automática del proxy.
-   **Usar script de proxy**: seleccione esta opción si desea especificar una ruta de acceso a un script de configuración automática para configurar el servidor proxy.
    -   **URL del script de configuración**: escriba la dirección URL de un script de configuración automática que desee usar para configurar el servidor proxy.
-   **Usar servidor proxy manual**: seleccione esta opción si desea proporcionar manualmente información sobre el servidor proxy.
    -   **Dirección**: escriba el nombre o la dirección IP del servidor proxy.
    -   **Número de puerto**: escriba el número de puerto del servidor proxy.
    -   **Excepciones de proxy**: escriba las direcciones URL que no deben usar el servidor proxy. Use un punto y coma para separar cada elemento.
    -   **Omitir el servidor proxy para direcciones locales**: si no quiere usar el servidor proxy para direcciones locales de la intranet, habilite esta opción.

## <a name="windows-spotlight"></a>Contenido destacado de Windows

- **Contenido destacado de Windows**: use esta opción para bloquear todas las funciones de Contenido destacado de Windows en los dispositivos de Windows 10. Si bloquea esta configuración, las siguientes opciones no estarán disponibles.
    - **Contenido destacado de Windows en la pantalla de bloqueo**: impide que Contenido destacado de Windows muestre información en la pantalla de bloqueo del dispositivo.
    - **Sugerencias de terceros en Contenido destacado de Windows**: impide que Contenido destacado de Windows sugiera contenido que no ha sido publicado por Microsoft.
    - **Características de consumidor**: permite bloquear las características de consumidor, como sugerencias del menú Inicio y notificaciones de pertenencia.
    - **Sugerencias de Windows**: permite impedir que las sugerencias emergentes se muestren en Windows.
    - **Contenido destacado de Windows en el centro de actividades**: impide que las sugerencias de Contenido destacado de Windows como una nueva aplicación o contenido de seguridad aparezcan en el centro de actividades de Windows.
    - **Personalización de Contenido destacado de Windows**: impide que Contenido destacado de Windows personalice los resultados basándose en el uso de un dispositivo.
    - **Experiencia de bienvenida de Windows**: bloquea la experiencia de bienvenida de Windows que muestra la información de usuario sobre características nuevas o actualizadas.

## <a name="projection"></a>Proyección

- **Entrada de usuario desde receptores de pantalla inalámbricos**: bloquea la entrada de usuario desde receptores de pantalla inalámbricos.
- **Proyección en este equipo**: impide que otros dispositivos detecten el equipo para proyección.
- **Requerir PIN para emparejamiento**: se requiere un PIN cuando se conecta a un dispositivo de proyección.

## <a name="cloud-printer"></a>Impresora en la nube

- **Dirección URL de detección de la impresora**: punto de conexión para detectar impresoras en la nube.
- **Dirección URL de autoridad de acceso a la impresora**: punto de conexión de autenticación para la adquisición de tokens de OAuth.
- **GUID de aplicación cliente nativa de Azure**: una GUID de una aplicación cliente autorizada para recuperar los tokens de OAuth desde OAuthAuthority.
- **URI de recurso de servicio de impresión**: URI de recurso de OAuth para el servicio de impresión tal y como está configurado en Azure Portal.
- **Máximo de impresoras para consultar (solo móvil)**: número máximo de impresoras que se deben consultar desde un punto de conexión de detección.
- **URI de recurso de servicio de detección de impresora**: URI de recurso de OAuth para el servicio de detección de impresora tal y como está configurado en Azure Portal.

## <a name="local-printer"></a>Impresora local
- **Impresoras**: lista de impresoras locales que se han agregado.
- **Impresora predeterminada**: establezca la impresora predeterminada.
- **Acceso de usuario para agregar nuevas impresoras**: permita o bloquee el uso de las impresoras locales.

## <a name="reporting-and-telemetry"></a>Informes y telemetría

- **Compartir datos de uso**: seleccione el nivel de envío de datos de diagnóstico.
- **Servidor proxy de telemetría**

  Especifique el nombre de dominio completo (FQDN) o la dirección IP de un servidor proxy para las solicitudes de Telemetría y experiencias del usuario conectado mediante una conexión de Capa de sockets seguros. El formato de esta configuración es *servidor*:*puerto*. Si se produce un error en el proxy con nombre, o si no hay ningún proxy especificado cuando esta directiva está habilitada, los datos de Telemetría y experiencias del usuario conectado no se transmiten y permanecen en el dispositivo local.

   Formatos de ejemplo:

   IPv4: 192.246.246.106:100<br>
 IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100<br> FQDN: www.contoso.com:345

## <a name="messaging"></a>Mensajería

- **Sincronización de mensajes (solo móvil)**: deshabilita Mensajes en cualquier dispositivo y la copia de seguridad y restauración de los mensajes de texto.
- **MMS (solo móvil)**: deshabilita la funcionalidad de envío y recepción de MMS en el dispositivo.
- **RCS (solo móvil)**: deshabilita la funcionalidad de envío o recepción de Rich Communication Services en el dispositivo.
