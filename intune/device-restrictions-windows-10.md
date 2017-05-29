---
title: "Configuración de restricciones de dispositivo de Intune para Windows 10"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: conozca la configuración de Intune que puede usar para controlar la configuración y la funcionalidad de dispositivos Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89f2d806-2e97-430c-a9a1-70688269627f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 88910c6628bb356e4a757cbdb4cf63b0acf60040
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="windows-10-and-later-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos Windows 10 y versiones posteriores en Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="general"></a>General
-     **Captura de pantalla (solo móviles)**: permite que el usuario capture la pantalla del dispositivo como imagen.
-     **Copiar y pegar (solo móviles)**: permite acciones de copiar y pegar entre aplicaciones del dispositivo.
-     **Cancelación manual de la suscripción**: permite al usuario eliminar manualmente la cuenta del área de trabajo desde el dispositivo.
-     **Instalación manual del certificado raíz (solo móviles)**: impide que el usuario instale manualmente certificados raíz y certificados CAP intermedios.
-     **Envío de datos de diagnóstico**: los valores posibles son:
    -         **Ninguno**: no se envían datos a Microsoft.
    -         **Básico**: se envía información limitada a Microsoft.
    -         **Mejorado**: se envían datos de diagnóstico mejorados a Microsoft.
    -         **Completo** : envía los mismos datos que Mejorado, además de datos adicionales sobre el estado del dispositivo.
-     **Cámara**: permite o bloquea el uso de la cámara en el dispositivo.
-     **Sincronización de archivos de OneDrive**: bloquea la sincronización de archivos de OneDrive en el dispositivo.
-     **Almacenamiento extraíble**: especifica si se pueden usar dispositivos de almacenamiento externo, como una tarjeta SD, con el dispositivo.
-     **Geolocation** (Geolocalización): especifica si el dispositivo puede usar la información de servicios de ubicación.
-     **Conexión compartida**: permite el uso compartido de una conexión a Internet en el dispositivo.
-     **Restablecimiento del teléfono**: controla si el usuario puede restablecer su dispositivo a la configuración de fábrica.
-     **Conexión USB (solo móviles)**: controla si los dispositivos pueden tener acceso a dispositivos de almacenamiento externo a mediante una conexión USB.
-     **Modo antirrobo (solo móviles)**: permite habilitar el modo antirrobo de Windows.
-     **Notificaciones del centro de actividades (solo móviles)**: habilita o deshabilita las notificaciones del centro de actividades en la pantalla de bloqueo del dispositivo (solo Windows 10 Mobile).
-     **Cortana**: habilita o deshabilita el asistente de voz de Cortana.
-     **Grabación de voz (solo móviles)**: permite o bloquea el uso de la grabadora de voz del dispositivo.
-     **Modificación de la configuración de inicio/apagado y suspensión (solo escritorio)**: evita que el usuario final cambie la configuración de inicio/apagado y suspensión en el dispositivo.
-     **Modificación de la configuración regional (solo escritorio)**: evita que el usuario final cambie la configuración regional en el dispositivo.
-     **Modificación de la configuración de idioma (solo escritorio)**: evita que el usuario cambie la configuración de idioma en el dispositivo.
-     **Modificación de la hora del sistema**: evita que el usuario final cambie la fecha y hora del dispositivo.
-     **Modificación del nombre del dispositivo**: evita que el usuario final cambie el nombre del dispositivo.
-     **Agregar paquetes de aprovisionamiento**: bloquea el agente de configuración de tiempo de ejecución que instala paquetes de aprovisionamiento.
-     **Quitar paquetes de aprovisionamiento**: bloquea el agente de configuración de tiempo de ejecución que quita paquetes de aprovisionamiento.
-     **Detección de dispositivos**: bloquea la detección de un dispositivo por parte de otros dispositivos.
-     **Conmutador de tareas (solo móviles)**: bloquea el conmutador de tareas en el dispositivo.
-     **Cuadro de diálogo de error de tarjeta SIM (solo móviles)**: impide que un mensaje de error se muestre en el dispositivo si no se detecta una tarjeta SIM.


## <a name="password"></a>Contraseña
-     **Contraseña**: exige que el usuario final escriba una contraseña para acceder al dispositivo.
    -     **Tipo de contraseña necesaria**: especifica si la contraseña debe ser solo numérica o alfanumérica.
    -     **Minimum password length** (Longitud mínima de contraseña): solo se aplica a Windows 10 Mobile.
    -     **Número de errores de inicio de sesión antes de borrar el dispositivo**: para dispositivos que ejecutan Windows 10: si el dispositivo tiene habilitado BitLocker, se pondrá en el modo de recuperación de BitLocker si el inicio de sesión produce un error el número de veces que ha especificado. Si el dispositivo no tiene habilitado BitLocker, no se aplica esta configuración.
Para los dispositivos que ejecutan Windows 10 Mobile: si el inicio de sesión falla el número de veces especificado, el dispositivo se borrará.
    -     **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique la longitud de tiempo que un dispositivo debe estar inactivo antes de que se bloquee la pantalla.
    -     **Caducidad de la contraseña (días)**: especifica el período de tiempo transcurrido el cual debe cambiarse la contraseña del dispositivo.
    -     **Impedir la reutilización de contraseñas anteriores**: especifica el número de contraseñas usadas anteriormente que se recuerdan el dispositivo.
    -     **Requerir contraseña cuando el dispositivo vuelve de un estado de inactividad**: especifica que el usuario debe escribir una contraseña para desbloquear el dispositivo (solo Windows 10 Mobile).
-     **Cifrado**: habilita el cifrado en los dispositivos de destino (solo Windows 10 Mobile).

## <a name="personalization"></a>Personalization

-     **Dirección URL de imagen de fondo de escritorio (solo escritorio)**: especifica la dirección URL de una imagen en formato PNG, JPG o JPEG que se usará como papel tapiz de escritorio de Windows. Los usuarios no podrán cambiar este valor.

## <a name="locked-screen-experience"></a>Experiencia de pantalla bloqueada

-     **Dirección URL de imagen de pantalla bloqueada (solo escritorio)**: especifica la dirección URL de una imagen en formato PNG, JPG o JPEG que se usará como papel tapiz de la pantalla de bloqueo de Windows. Los usuarios no podrán cambiar este valor.


## <a name="app-store"></a>Tienda de aplicaciones

-     **Tienda de aplicaciones (solo móvil)**: permitir o bloquear el uso de la tienda de aplicaciones en dispositivos Windows 10 Mobile.
-     **Actualización automática de aplicaciones desde la tienda**: permite que las aplicaciones instaladas de la Tienda Windows se actualicen automáticamente.
-     **Instalación de aplicaciones de confianza**: permite realizar una instalación de prueba de las aplicaciones firmadas con un certificado de confianza.
-     **Desbloqueo de desarrollador**: permite que un usuario final modifique la configuración de desarrollador de Windows, como permitir las aplicaciones con instalación de prueba.
-     **Datos de aplicación compartidos entre usuarios**: permite que las aplicaciones compartan datos entre distintos usuarios en el mismo dispositivo.
-     **Usar solo una tienda privada**: habilite esta opción para permitir que los usuarios finales solo descarguen aplicaciones desde la tienda privada.
-     **Inicio de aplicaciones de la tienda**: se usa para deshabilitar todas las aplicaciones instaladas previamente en el dispositivo o que se descargaron de la Tienda Windows.
-     **Instalar los datos de aplicación en el volumen del sistema**: esta opción hace que las aplicaciones dejen de almacenar datos en el volumen del sistema del dispositivo.
-     **Instalar las aplicaciones en la unidad del sistema**: esta opción hace que las aplicaciones dejen de almacenar datos en la unidad del sistema del dispositivo.
-     **Game DVR (solo escritorio)**: configura si se permite la grabación y difusión de los juegos.



## <a name="edge-browser"></a>Explorador Edge
-     **Explorador de Microsoft Edge (solo móvil)**: permite el uso del explorador web Edge en el dispositivo.
-     **SmartScreen**: habilita o deshabilita SmartScreen que bloquea los sitios web fraudulentos.
-     **Enviar encabezados de no seguimiento**: configura el explorador Edge para que envíe encabezados de no seguimiento a sitios web que visitan los usuarios.
-     **Cookies**: permite que el explorador guarde cookies de Internet en el dispositivo.
-     **JavaScript**: permite la ejecución de scripts, como JavaScript, en el explorador Edge.
-     **Ventanas emergentes**: bloquea las ventanas emergentes en el explorador (solo se aplica a Windows 10 Escritorio).
-     **Search suggestions** (Sugerencias de búsqueda): permite que el motor de búsqueda sugiera sitios a medida que se escriben las frases de búsqueda.
-     **Enviar el tráfico de la intranet a Internet Explorer**: permite a los usuarios abrir sitios web de intranet en Internet Explorer (solo Windows 10 Escritorio).
-     **Rellenar automáticamente**: permite a los usuarios cambiar la configuración de Autocompletar en el explorador (solo Windows 10 Escritorio).
-     **Administrador de contraseñas**: habilita o deshabilita la característica de Administrador de contraseñas de Edge.
-     **Ubicación de la lista de sitios del modo de empresa**: especifica dónde encontrar la lista de sitios web que se abren en modo de empresa. Los usuarios no pueden editar esta lista.<br>(Solo Windows 10 Escritorio)
-     **Herramientas de desarrollo**: impiden que el usuario final abra las herramientas de desarrollo de Edge.
-     **Extensiones**: permiten que el usuario final instale extensiones de Edge en el dispositivo.
-     **Exploración de InPrivate**: impide que el usuario final abra sesiones de exploración de InPrivate.
-     **Dirección URL de primera ejecución**: escriba la dirección URL que el explorador Edge abrirá la primera vez que se ejecute (solo móviles).
-     **Páginas principales**: agrega una lista de sitios que se usarán como páginas principales en el explorador Edge (solo escritorio).
-     **Bloquear acceso a about:flags**: impide que el usuario final tenga acceso a la página about:flags de Edge que contiene la configuración experimental y de desarrollador.
-     **Invalidación de avisos de SmartScreen**: permite que el usuario final omita las advertencias de filtro de SmartScreen sobre los sitios web potencialmente malintencionados.
-     **Invalidación de avisos de SmartScreen para archivos**: permite que el usuario final omita las advertencias de filtro de SmartScreen sobre la descarga de archivos potencialmente malintencionados.
-     **Dirección IP de localhost para WebRtc**: impide que la dirección IP de localhost de los usuarios se muestre cuando se hacen llamadas telefónicas a través del protocolo WebRtc.
-     **Motor de búsqueda predeterminado**: especifica el motor de búsqueda predeterminado que se usará. Los usuarios finales pueden cambiar este valor en cualquier momento.

## <a name="search"></a>Búsqueda
- **Búsqueda segura (solo móviles)**: controla cómo Cortana filtra contenido para adultos en los resultados de la búsqueda. Puede seleccionar **Strict** (Estricto), **Moderate** (Moderado) o permitir que el usuario final elija su propia configuración.

## <a name="cloud-and-storage"></a>Nube y almacenamiento
-     **Cuenta Microsoft**: permite al usuario asociar una cuenta de Microsoft con el dispositivo.
-     **Cuenta que no es Microsoft**: permite al usuario agregar al dispositivo cuentas de correo electrónico que no estén asociadas a una cuenta de Microsoft.
-     **Sincronización de configuración de cuenta Microsoft**: permite sincronizar la configuración de dispositivos y aplicaciones que están asociados con una cuenta de Microsoft entre dispositivos.

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad
-     **Itinerancia de datos**: permite la itinerancia entre redes al acceder a los datos.
-     **VPN a través de la red de telefonía móvil**: controla si el dispositivo puede acceder a las conexiones VPN cuando se conecta a una red móvil.
-     **Itinerancia de VPN a través de la red de telefonía móvil**: controla si el dispositivo puede acceder a conexiones VPN cuando está en itinerancia en una red móvil.
-     **Bluetooth**: controla si el usuario puede habilitar y configurar Bluetooth en el dispositivo.
-     **Detectabilidad de Bluetooth**: permite que otros dispositivos con Bluetooth habilitado detecten el dispositivo.
-     **Anuncios de Bluetooth**: permite que el dispositivo reciba anuncios a través de Bluetooth.
-     **Nombre de Bluetooth del dispositivo**: permite especificar el nombre de Bluetooth del dispositivo.
-     **NFC**: permite al usuario habilitar y configurar funciones de transmisión de datos en proximidad en el dispositivo.
-     **Wi-Fi**: permite al usuario habilitar y configurar Wi-Fi en el dispositivo (solo Windows 10 Mobile).
-     **Conectar automáticamente a zonas Wi-Fi**: permite que el dispositivo se conecte automáticamente a zonas Wi-Fi gratuitas y acepte automáticamente los términos y condiciones para la conexión.
-     **Configuración manual de Wi-Fi**: controla si el usuario puede configurar sus propias conexiones Wi-Fi o si solo puede usar conexiones configuradas mediante un perfil Wi-Fi (solo Windows 10 Mobile).
-     **Intervalo de detección de Wi-Fi**: especifica con qué frecuencia los dispositivos detectan redes Wi-Fi.

## <a name="control-panel-and-settings"></a>Panel de control y configuración

-     **Aplicación de configuración**: bloquea el acceso a la aplicación de configuración de Windows.
    -     **Sistema**: bloquea el acceso al área de sistema de la aplicación de configuración.
    -     **Dispositivos**: bloquea el acceso al área de dispositivos de la aplicación de configuración.
    -     **Red e Internet**: bloquea el acceso al área de la red e Internet de la aplicación de configuración.
    -     **Personalización**: bloquea el acceso al área de personalización de la aplicación de configuración.
    -     **Cuentas**: bloquea el acceso al área de cuentas de la aplicación de configuración.
    -     **Hora e idioma**: bloquea el acceso al área de hora e idioma de la aplicación de configuración.
    -     **Accesibilidad**: bloquea el acceso al área de accesibilidad de la aplicación de configuración.
    -     **Privacidad**: bloquea el acceso al área de privacidad de la aplicación de configuración.
    -     **Actualización y seguridad**: bloquea el acceso al área de actualizaciones y seguridad de la aplicación de configuración.

## <a name="defender"></a>Defender

-     **Supervisión en tiempo real**: habilita el análisis en tiempo real de malware, spyware y otro software no deseado.
-     **Supervisión de comportamiento**: permite a Defender comprobar determinados patrones conocidos de actividad sospechosa en los dispositivos.
-     **Sistema de inspección de red (NIS)**: el Sistema de inspección de red (NIS) ayuda a proteger los dispositivos contra ataques basados en red mediante el uso de firmas de vulnerabilidades conocidas de Microsoft Endpoint Protection Center para detectar y bloquear el tráfico malintencionado.
-     **Analizar todas las descargas**: controla si Defender examina todos los archivos descargados de Internet.
-     **Examinar scripts cargados en exploradores web de Microsoft**: permite a Defender examinar scripts que se usan en Internet Explorer.
-     **Acceso de usuario final a Defender**: controla si la interfaz de usuario de Windows Defender se oculta a los usuarios finales.
Cuando se cambia esta configuración, surtirá efecto la próxima vez que se reinicie el equipo del usuario final.
-     **Intervalo de actualización de firma (en horas)**: especifique el intervalo dentro del cual Defender buscará nuevos archivos de firmas.
-     **Supervisar la actividad de archivos y programas**: permite que Defender supervise la actividad de archivos y programas en los dispositivos.
-     **Días antes de eliminar el malware en cuarentena**: permite que Defender continúe realizando el seguimiento de malware resuelto durante el número de días especificado para que pueda comprobar de forma manual los dispositivos previamente afectados. Si establece el número de días en **0**, el malware permanece en la carpeta de cuarentena y no se quita automáticamente.
-     **Límite de uso de la CPU durante un examen**: le permite limitar la cantidad de CPU que pueden usar los exámenes (de **1** a **100**).
-     **Examinar archivos de almacenamiento**: permite que Defender examine archivos almacenados, como archivos .zip o .cab.
-     **Examinar mensajes de correo entrante**: permite que Defender examine mensajes de correo electrónico cuando llegan al dispositivo.
-     **Examinar unidades extraíbles durante un examen completo**: permite que Defender examine unidades extraíbles, como llaves USB.
-     **Examinar unidades de red asignadas durante un examen completo**: permite que Defender examine archivos en unidades de red asignadas.<br>Si los archivos de la unidad son de solo lectura, Defender no podrá quitar el malware que se encuentre en ellos.
-     **Examinar archivos abiertos desde carpetas de red**: permite que Defender examine archivos en unidades de red compartidas (por ejemplo, aquellas a las que se tiene acceso desde una ruta de acceso UNC).
Si los archivos de la unidad son de solo lectura, Defender no podrá quitar el malware que se encuentre en ellos.
-     **Protección de la nube**: permite o bloquea la recepción por parte de Microsoft Active Protection Service de información relativa a la actividad de malware de los dispositivos que administra. Esta información se usa para mejorar el servicio en el futuro.
-     **Preguntar a los usuarios antes de enviar muestras**: controla si los archivos que podrían requerir un análisis posterior por parte de Microsoft para determinar si son malintencionados se envían automáticamente a Microsoft.
-     **Hora a la que se realizará un examen rápido diario**: permite programar un examen rápido que se produce diariamente en el momento seleccionado.
-     **Tipo de examen del sistema para realizar**: le permite especificar el nivel de examen que se realizará cuando se programe un examen del sistema.

## <a name="defender-exclusions"></a>Exclusiones de Defender

-     **Archivos y carpetas para excluir de exámenes y protección en tiempo real**: agrega uno o varios archivos y carpetas, como **C:\Path** o **%ProgramFiles%\Path\filename.exe** a la lista de exclusiones. Estos archivos y carpetas no se incluyen en los exámenes en tiempo real ni programados.
-     **Extensiones de archivo para excluir de exámenes y protección en tiempo real**: agrega una o varias extensiones de archivo, como **jpg** o **txt** a la lista de exclusiones. Los archivos con estas extensiones no se incluyen en los exámenes en tiempo real ni programados.
-     **Procesos para excluir de exámenes y protección en tiempo real**: agregar uno o varios procesos del tipo **.exe**, **.com** o **.scr** a la lista de exclusiones. Estos procesos no se incluirán en los análisis en tiempo real ni programados.


## <a name="network-proxy"></a>Proxy de red

-     **Detectar automáticamente configuración de proxy**: cuando esta opción está habilitada, el dispositivo intentará encontrar la ruta de acceso a un script de configuración automática del proxy.
-     **Usar script de proxy**: seleccione esta opción si desea especificar una ruta de acceso a un script de configuración automática para configurar el servidor proxy.
    -     **URL del script de configuración**: escriba la dirección URL de un script de configuración automática que desee usar para configurar el servidor proxy.
-     **Usar servidor proxy manual**: seleccione esta opción si desea proporcionar manualmente información sobre el servidor proxy.
    -     **Dirección**: escriba el nombre o la dirección IP del servidor proxy.
    -     **Número de puerto**: escriba el número de puerto del servidor proxy.
    -     **Excepciones de proxy**: escriba las direcciones URL que no deben usar el servidor proxy. Use un punto y coma para separar cada elemento.
    -     **Omitir el servidor proxy para direcciones locales**: habilite esta opción si no desea usar el servidor proxy para direcciones locales de la intranet.


## <a name="windows-spotlight"></a>Contenido destacado de Windows

-     **Contenido destacado de Windows**: permita o bloquee Contenido destacado de Windows que proporciona características como sugerencias y trucos, mensajes en la pantalla de bloqueo de Windows, etc.
    -     **Sugerencias de Windows**: permite impedir que las sugerencias emergentes se muestren en Windows.
    -     **Características de consumidor**: permite bloquear las características de consumidor, como sugerencias del menú Inicio y notificaciones de pertenencia.

## <a name="display"></a>Pantalla

- **Entrada de usuario desde receptores de pantalla inalámbricos**: bloquea la entrada de usuario desde receptores de pantalla inalámbricos.
- **Proyección en este equipo**: impide que otros dispositivos detecten el equipo para proyección.
- **Requerir PIN para emparejamiento**: se requiere un PIN cuando se conecta a un dispositivo de proyección.

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
