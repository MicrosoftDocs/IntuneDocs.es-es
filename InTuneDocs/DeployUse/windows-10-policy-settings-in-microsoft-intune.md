---
# required metadata

title: Configuración de directivas de Windows 10 en Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configuración de directivas de Windows 10 en Microsoft Intune

Use la configuración de directiva indicada en este tema para configurar las opciones de los dispositivos inscritos de la versión de escritorio de Windows 10 y Windows 10 Mobile.

## Configuración general de directivas

Use la **directiva de configuración general** de Microsoft de Windows 10 para configurar las opciones generales de los dispositivos inscritos de la versión de escritorio de Windows 10 y Windows 10 Mobile:


### Contraseña

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Móvil|
|----------------|----------------------|---------------------|
|**Requerir contraseña para desbloquear dispositivos**|Se requiere una contraseña en dispositivos compatibles.|Sí|Sí|
|**Tipo de contraseña obligatoria**|Especifica el tipo de contraseña que será necesario, como solo numérica o alfanumérica.|Sí|Sí|
|**Tipo de contraseña requerida** - **Número mínimo de conjuntos de caracteres**|Hay cuatro conjuntos de caracteres: letras minúsculas, letras mayúsculas, símbolos y números. Esta configuración especifica cuántos conjuntos de caracteres diferentes deben incluirse en la contraseña.|Sí|Sí|
|**Longitud mínima de la contraseña**|Especifica el número mínimo de caracteres necesarios que debe contener la contraseña del dispositivo.|No|Sí|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Borra el dispositivo si hay un error en este número de intentos de inicio de sesión.|Sí|Sí|
|**Minutos de inactividad antes de que se apague la pantalla**|Especifica el tiempo durante el que un dispositivo debe estar inactivo antes de que se bloquee la pantalla.|Sí|Sí|
|**Caducidad de contraseña (días)**|Especifica el período de tiempo tras el que debe cambiarse la contraseña del dispositivo.|Sí|Sí|
|**Recordar el historial de contraseñas**|Especifica si quiere impedir que el usuario final cree contraseñas usadas anteriormente.|Sí|Sí|
|**Recordar historial de contraseñas** - **Impedir la reutilización de contraseñas anteriores**|Especifica el número de contraseñas usadas previamente que el dispositivo recuerda.|Sí|Sí|
|**Permitir contraseña de imagen y PIN**|Le permite usar gestos simples en una imagen o un PIN sencillo para iniciar sesión.|Sí|No|
|**Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad**|Si está habilitado, el usuario debe escribir una contraseña para desbloquear el dispositivo en estado de inactividad.|No|Sí|

### Cifrado

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Móvil|
|----------------|----------------------|---------------------|
|**Requerir cifrado en dispositivo móvil**|Habilita el cifrado en dispositivos de destino.|No|Sí|

### System

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Móvil|
|----------------|----------------------|---------------------|
|**Permitir captura de pantalla**|Permite al usuario capturar la pantalla del dispositivo como una imagen.|No|Sí|
|**Permitir cancelar suscripción manualmente**|Permite al usuario eliminar manualmente la cuenta del área de trabajo desde el dispositivo.|Sí|Sí|
|**Permitir la instalación de certificado raíz manualmente**|Especifica si el usuario puede instalar certificados raíz manualmente.|No|Sí|
|**Permitir que datos de diagnóstico y uso se envíen a Microsoft**|Determina la cantidad de datos de diagnóstico y uso que se envían a Microsoft desde los dispositivos.<br>**No**: no se envían datos a Microsoft.<br>**Básico**: el dispositivo solo envía información limitada a Microsoft.<br>**Mejorado**: envía datos de diagnóstico mejorados a Microsoft.<br>**Completo (recomendado)**: envía los mismos datos que **Mejorado**, además de datos adicionales sobre el estado del dispositivo.|Sí|Sí|


### Cuenta y sincronización

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Móvil|
|----------------|----------------------|---------------------|
|**Permitir cuenta de Microsoft**|Permite al usuario asociar una cuenta de Microsoft con el dispositivo.|Sí|Sí|
|**Permitir añadir cuentas que no son de Microsoft de forma manual**|Permite al usuario agregar al dispositivo cuentas de correo electrónico que no estén asociadas a una cuenta de Microsoft.|Sí|Sí|
|**Permitir la sincronización de la configuración de las cuentas de Microsoft**|Permite que la configuración de dispositivo y aplicación asociada a una cuenta de Microsoft se sincronice entre los dispositivos.|Sí|Sí|

### Configuración de correo electrónico

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Móvil|
|----------------|----------------------|---------------------|
|**Hacer que la cuenta Microsoft sea opcional en la aplicación Windows Mail**|Configure esta opción para quitar el requisito de una cuenta de Microsoft en Correo de Windows.|Sí|No|



### Microsoft Edge

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Móvil|
|----------------|----------------------|---------------------|
|**Permitir explorador web**|Permite el uso del explorador web de Edge en el dispositivo.|No|Sí|
|**Permitir sugerencias de búsqueda en la barra de direcciones**|Permite que el motor de búsqueda sugiera sitios a medida que se escriben las frases de búsqueda.|Sí|Sí|
|**Permitir enviar tráfico de intranet a Internet Explorer**|Permite a los usuarios abrir sitios web de intranet en Internet Explorer.|Sí|No|
|**Permitir no rastrear**|Configura el explorador Edge para que envíe encabezados Do Not Track a los sitios web que visitan los usuarios.|Sí|Sí|
|**Habilitar SmartScreen**|Habilita la configuración del explorador SmartScreen en dispositivos.|Sí|Sí|
|**Permitir Active scripting**|Permite que se ejecuten en el explorador Edge scripts como JavaScript.|Sí|Sí|
|**Permitir elementos emergentes**|Habilita o deshabilita el bloqueador de elementos emergentes del explorador.|Sí|No|
|**Permitir cookies**|Permite o deshabilita las cookies.|Sí|Sí|
|**Permitir autorrellenar**|Permite a los usuarios cambiar la configuración de Autocompletar en el explorador.|Sí|No|
|**Permitir administrador de contraseñas**|Habilita o deshabilita la característica Administrador de contraseñas de Edge.|Sí|Sí|
|**Ubicación de la lista de sitios de Modo de empresa**|Especifica dónde se encuentra la lista de sitios web que se abrirá en modo de empresa. Los usuarios no pueden editar esta lista.|Sí|No|

### Aplicaciones

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Móvil|
|----------------|----------------------|---------------------|
|**Permitir almacén de aplicaciones**|Permite al usuario tener acceso a la tienda de aplicaciones en el dispositivo.|No|Sí|



### Móvil

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Móvil|
|----------------|----------------------|---------------------|
|**Permitir itinerancia de datos**|Permite movilidad entre redes al obtener acceso a datos.|Sí|Sí|
|**Permitir VPN sobre móvil**|Controla si el dispositivo puede tener acceso a las conexiones VPN cuando se conecta a una red móvil.|Sí|Sí|
|**Permitir itinerancia de VPN sobre móvil**|Controla si el dispositivo puede tener acceso a las conexiones VPN cuando hay itinerancia a una red móvil.|Sí|Sí|

### Hardware

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Móvil|
|----------------|----------------------|---------------------|
|**Permitir cámara**|Especifica si se puede usar la cámara del dispositivo.|Sí|Sí|
|**Permitir almacenamiento extraíble**|Especifica si se pueden usar dispositivos de almacenamiento externo, como una tarjeta SD, con el dispositivo.|Sí|Sí|
|**Permitir Wi-Fi**|Permite usar la funcionalidad de Wi-Fi del dispositivo.|No|Sí|
|**Permitir compartir Internet**|Permite el uso compartido de una conexión de Internet en el dispositivo.|Sí|Sí|
|**Permitir la configuración Wi-Fi manual**|Controla si el usuario puede configurar sus propias conexiones Wi-Fi o si solo puede usar conexiones configuradas mediante un perfil Wi-Fi.|No|Sí|
|**Permitir la conexión automática a zonas Wi-Fi gratuitas**|Permite que el dispositivo se conecte automáticamente a zonas Wi-Fi gratuitas y acepte automáticamente los términos y condiciones para la conexión.|Sí|Sí|
|**Permitir geolocalización**|Especifica si el dispositivo puede usar información de servicios de ubicación.|Sí|Sí|
|**Permitir NFC**|Permite que el dispositivo use las funcionalidades de transmisión de datos en proximidad.|Sí|Sí|
|**Permitir Bluetooth**|Habilita el uso de funcionalidades de Bluetooth en el dispositivo.|Sí|Sí|
|**Permitir modo visible de Bluetooth **|Permite que otros dispositivos habilitados para Bluetooth detecten este dispositivo.|Sí|Sí|
|**Permitir anuncios de Bluetooth**|Permite que los dispositivos reciban anuncios a través de Bluetooth.|Sí|Sí|
|**Permite el modo conectable de Bluetooth.** **Importante:** |Esta configuración ya no es compatible con Windows 10 y se eliminará en el futuro.|Sí|Sí|
|**Permitir restablecer teléfono**|Controla si el usuario puede restablecer su dispositivo a la configuración de fábrica.|Sí|Sí|
|**Permitir conexión USB**|Controla si los dispositivos pueden tener acceso a dispositivos de almacenamiento externo a través de una conexión USB.|Sí|Sí|
|**Permitir modo antirrobo**|Permite habilitar el modo antirrobo de Windows.|Sí|Sí|

### Funciones

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Móvil|
|----------------|----------------------|---------------------|
|**Permitir copiar y pegar**|Habilita o deshabilita el uso de copiar y pegar en el dispositivo.|No|Sí|
|**Permitir grabación de voz**|Habilita o deshabilita las características de grabación de voz en el dispositivo.|No|Sí|
|**Permitir a Cortana**|Habilita o deshabilita el asistente de voz de Cortana.|Sí|Sí|
|**Permitir notificaciones del centro de actividades**|Habilita o deshabilita notificaciones del centro de actividades en la pantalla de bloqueo del dispositivo.|No|Sí|

### Defender

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Mobile|
|-|-|
|**Permitir supervisión en tiempo real**|Habilita el análisis en tiempo real de malware, spyware y otro software no deseado.|Sí|No|
|**Permitir supervisión del comportamiento**|Permite a Defender comprobar determinados patrones conocidos de actividad sospechosa en los dispositivos.|Sí|No
|**Habilitar Sistema de inspección de red**|El Sistema de inspección de red (NIS) ayuda a proteger los dispositivos contra ataques basados en red mediante el uso de firmas de vulnerabilidades conocidas de Microsoft Endpoint Protection Center para detectar y bloquear el tráfico malintencionado.|Sí|No
|**Analizar todas las descargas**|Controla si Defender analiza todos los archivos descargados de Internet.|Sí|No
|**Permitir análisis de scripts**|Permite que Defender examine scripts que se usan en Internet Explorer.|Sí|No
|**Supervisar actividad de archivos y programas**|Habilite esta opción para permitir que Defender supervise la actividad de archivos y programas en los dispositivos.|Sí|No
|**Días que hay que hacer seguimiento de malware resuelto**|Permite que Defender continúe realizando el seguimiento de malware resuelto durante el número de días especificado para que pueda comprobar de forma manual los dispositivos previamente afectados. Si establece el número de días en **0**, el malware permanece en la carpeta de cuarentena y no se quita automáticamente. |Sí|No
|**Permitir acceso a la interfaz de usuario de cliente**|Controla si la interfaz de usuario de Windows Defender se oculta a los usuarios finales.<br>Cuando se cambia esta configuración, surtirá efecto la próxima vez que se reinicie el equipo del usuario final.|Sí|No
|**Programar un examen rápido diario**|Permite programar un examen rápido que se lleva a cabo diariamente a la hora que seleccione.|Sí|No
|**Programar un examen del sistema**|Permite programar un examen completo o rápido del sistema que se lleva a cabo periódicamente en el día y la hora seleccionados.|Sí|No
|**Limitar el uso de la CPU durante un análisis a**|Permite limitar la cantidad de CPU que pueden usar los exámenes (de **1** a **100**).)|Sí|No
|**Examinar archivos de almacenamiento**|Permite que Defender examine archivos almacenados, como archivos Zip o Cab.|Sí|No
|**Analizar mensajes de correo electrónico**|Permite que Defender analice los mensajes de correo electrónico cuando llegan al dispositivo.|Sí|No
|**Analizar unidades extraíbles**|Permite que Defender analice unidades extraíbles, como sticks USB.|Sí|No
|**Examinar unidades de red asignadas**|Permite que Defender examine archivos en unidades de red asignadas.<br>Si los archivos de la unidad son de solo lectura, Defender no podrá quitar el malware que se encuentre en ellos.|Sí|No
|**Examinar archivos abiertos desde carpetas compartidas de red**|Permite que Defender examine archivos en unidades de red compartidas (por ejemplo, aquellas a las que se tiene acceso desde una ruta de acceso UNC).<br>Si los archivos de la unidad son de solo lectura, Defender no podrá quitar el malware que se encuentre en ellos.|Sí|No
|**Intervalo de actualización de firma**|Especifica el intervalo en el que Defender buscará nuevos archivos de firma.|Sí|No
|**Permitir la protección en la nube**|Permite o bloquea la recepción por parte de Microsoft Active Protection Service de información sobre la actividad de malware de los dispositivos que administra. Esta información se usa para mejorar el servicio en el futuro.|Sí|No
|**Pedir a los usuarios el envío de muestras**|Controla si los archivos que podrían requerir un análisis posterior por parte de Microsoft para determinar si son malintencionados se envían automáticamente a Microsoft.|Sí|No
|**Archivos y carpetas que se van a excluir al ejecutar un análisis o al usar la protección en tiempo real**|Agrega uno o varios archivos y carpetas como **C:\Path** o **%ProgramFiles%\Path\filename.exe** a la lista de exclusiones. Estos archivos y carpetas no se incluirán en los análisis en tiempo real ni programados.|Sí|No
|**Extensiones de archivo que se deben excluir al ejecutar un análisis o al utilizar protección en tiempo real**|Agrega una o varias extensiones de archivo como **jpg** o **txt** a la lista de exclusiones. Los archivos con estas extensiones no se incluirán en los análisis en tiempo real ni programados.|Sí|No
|**Procesos que se deben excluir al ejecutar un análisis o al utilizar protección en tiempo real**|Agrega uno o varios procesos del tipo **.exe**, **.com** o **.scr** a la lista de exclusiones. Estos procesos no se incluirán en los análisis en tiempo real ni programados.|Sí|No| 


### Configuración de actualizaciones

|Nombre de la configuración|Detalles|Windows 10 Escritorio|Windows 10 Móvil|
|----------------|---------------|----------------------|---------------------|
|**Permitir actualizaciones automáticas**|Habilite esta configuración para permitir las actualizaciones automáticas. Luego, configure una de las opciones siguientes para controlar el comportamiento de las actualizaciones:<br /><br />**Notificar descarga**<br /><br />**Instalar automáticamente en tiempo de mantenimiento**<br /><br />**Instalar y reiniciar automáticamente en tiempo de mantenimiento**<br /><br />**Instalar y reiniciar automáticamente a la hora programada** **Nota:** Cuando esta opción está seleccionada, también puede configurar los valores siguientes: **Suprimir notificación para el usuario final** y **Definir el día de instalación para las actualizaciones programadas**..|Sí|No|

## Opciones de configuración de directiva personalizadas
Use la **directiva de configuración personalizada** de Microsoft Intune para Windows 10 y Windows 10 Mobile para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance) que puede usarse para controlar características en dispositivos con Windows 10 y Windows 10 Mobile. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad está destinada a permitirle implementar la configuración de Windows 10 que no se puede configurar con una directiva de configuración general de Intune. Para obtener información sobre las opciones que puede configurar con estas directivas, consulte [Manage settings and features on your devices with Microsoft Intune policies](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) (Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune)..

Para obtener una lista de opciones de OMA-URI que se pueden configurar en los dispositivos Windows 10 inscritos, consulte Configuración de URI personalizada para dispositivos de Windows 10 más adelante en este tema.

### Configuración general

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre**|Escriba un nombre único para la directiva que le ayude a identificarla en la consola de Intune.|
    |**Descripción**|Proporcione una descripción general de la directiva y otra información relevante que le ayude a encontrarla.|

### Configuración de OMA-URI

|Nombre de la configuración|Detalles|
    |--------|--------------------|
    |**Nombre de la configuración**|Escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.|
    |**Descripción del valor**|Proporcione una descripción que ofrezca una visión general del valor y otra información relevante que le ayude a encontrarlo.|
    |**Tipo de datos**|Seleccione el tipo de fecha en que especificará este valor OMA-URI. Elija de entre las siguientes opciones:<br /><br />-   **String**<br />-   **Cadena (XML)**<br />-   **Fecha y hora**<br />-   **Integer**<br />-   **Punto flotante**<br />-   **Boolean**|
    |**OMA-URI (distingue mayúsculas de minúsculas)**|Especifique el OMA-URI para el que desee suministrar un valor.|
    |**Valor**|Especifique el valor asociado con el OMA-URI especificado anteriormente.|


## Configuración de URI personalizada para dispositivos de Windows 10
En este tema se enumeran los valores que puede configurar para dispositivos de Windows 10 y Windows 10 Mobile en una **directiva personalizada de Windows 10** de Microsoft Intune..


> [!NOTE]
> En la columna **Soportes** de la tabla siguiente, se utilizan los valores siguientes:
> 
> -   **Escritorio**: el valor es compatible con los equipos de Windows 10 Professional y Enterprise que están inscritos solo con Intune.
> -   **Móvil** : el valor solo es compatible con dispositivos de Windows 10 Mobile.
> -   **Ambos** : el valor es compatible con dispositivos móviles y de escritorio.
> 
> Todos los dispositivos deben estar inscritos con Intune si quiere usar la directiva de URI de Windows personalizada.

### Directiva

|Nombre de la directiva|Soportes|Detalles|
|---------------|------------|-----------|
|**​Permitir la actualización automática**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:0** - **5**<br /><br />**Valor predeterminado** : 1|
|**Programa el día de la instalación**|Ambos|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: cada día<br /><br />**1**: domingo<br /><br />**2**: lunes<br /><br />**3**: martes<br /><br />**4**: miércoles<br /><br />**5**: jueves<br /><br />**6**: viernes<br /><br />**7**: sábado<br /><br />**Valor predeterminado:** 0|
|**Programar la hora de la instalación**|Ambos|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos: 0**-**23** horas (0 es medianoche)<br /><br />**Valor predeterminado:** 3|
|**DeviceLock/AllowIdleReturnWithoutPassword**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: el usuario no puede establecer el temporizador de período de gracia de la contraseña y el valor se establece como "siempre"<br /><br />**1**: el usuario puede establecer el temporizador de período de gracia de la contraseña<br /><br />**Valor predeterminado** : 1|
|**WiFi/AllowWiFi**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: no se permite **usar la conexión Wi-Fi**.<br /><br />**1**: **se permite usar la conexión Wi-Fi**.<br /><br />**Valor predeterminado** : 1|
|**Wi-Fi/AllowInternetSharing**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitir el uso compartido de Internet.<br /><br />**1** : permitir el uso compartido de Internet.<br /><br />**Valor predeterminado** : 1|
|**Wi-Fi/AllowAutoConnectToWiFiSenseHotspots**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Wi-Fi/AllowManualWiFiConfiguration**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: no se permite la conexión Wi-Fi fuera de la MDM aprovisionada.<br /><br />**1** : se permite agregar nuevos SSID de red más allá de los de la MDM aprovisionada.<br /><br />**Valor predeterminado** : 1|
|**System/AllowLocation**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**System/AllowTelemetry**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido (valor de Enterprise solo)<br /><br />**1** : limitado<br /><br />**2** : completo<br /><br />**3**: completo e información de diagnóstico<br /><br />**Valor predeterminado:** 2|
|**Sistema/AllowExperimentation**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1**: solo configuración<br /><br />**2**: configuración y experimentación<br /><br />**Valor predeterminado** : 1|
|**Security/AntiTheftMode**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: no permitir el modo antirrobo<br /><br />**1** : preferencia del usuario<br /><br />**Valor predeterminado** : 1|
|**Connectivity/AllowUSBConnection**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**System/AllowUserToResetPhone**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Connectivity/AllowCellularDataRoaming**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Connectivity/AllowVPNOverCellular**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: no se permite la VPN a través de la red de telefonía móvil<br /><br />**1** : la VPN puede usar cualquier conexión, incluida la de la red de telefonía móvil.<br /><br />**Valor predeterminado** : 1|
|**Connectivity/AllowVPNRoamingOverCellular**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Connectivity/AllowVPNRoamingOverCellular**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Connectivity/AllowBluetooth**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: no se permite al usuario activar el Bluetooth.<br /><br />**1**: reservado. El usuario puede activar y configurar el Bluetooth (no admitido en Windows Phone 8.1 para MDM, EAS, Windows 10 Escritorio o Windows 10 Mobile)<br /><br />**2**: permitido El usuario puede activar y configurar el Bluetooth.<br /><br />**Valor predeterminado:** 2|
|**Experience/AllowScreenCapture**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Experience/AllowTaskSwitcher**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Experience/AllowVoiceRecording**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Experience/AllowSyncMySettings**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitir itinerancia<br /><br />**1** : permitir itinerancia<br /><br />**Valor predeterminado** : 1|
|**Experience/AllowManualMDMUnenrollment**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Accounts/AllowMicrosoftAccountConnection**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Security/AllowManualRootCertificateInstallation**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Security/AllowAddProvisioningPackages**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Search/DisableBackoff**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predeterminado:** 0|
|**Search/PreventRemoteQueries**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predeterminado** : 1|
|**Search/AllowUsingDiacritics**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predeterminado:** 0|
|**Search/AlwaysUseAutoLangDetection**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predeterminado:** 0|
|**Search/DisableRemovableDriveIndexing**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predeterminado:** 0|
|**Search/PreventIndexingLowDiskSpaceMB**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predeterminado** : 1|
|**Search/AllowIndexingEncryptedStoresOrItems**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predeterminado:** 0|
|**Security/AllowRemoveProvisioningPackage**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Security/RequireProvisioningPackageSignature**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**<br /><br />**1**<br /><br />**Valor predeterminado:** 0|
|**AboveLock/AllowActionCenterNotifications**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**TextInput/AllowIMENetworkAccess**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitir<br /><br />El diccionario extendido abierto está desactivado.<br /><br />Un usuario no puede:<br /><br />Agregar un nuevo diccionario extendido abierto<br /><br />Agregar un nuevo archivo de configuración de integración de búsqueda<br /><br />Usar la característica de candidato en la nube<br /><br />Enviar la palabra registrada del usuario<br /><br />Además:<br /><br />Un diccionario extendido abierto que se ha agregado antes de habilitar esta configuración de directiva no se usa para la conversión.<br /><br />Un archivo de configuración de integración de búsqueda que se ha instalado antes de habilitar esta configuración de directiva no se usa.<br /><br />**1**: permitir<br /><br />El diccionario extendido abierto se puede agregar y usar de forma predeterminada. La función de integración de búsqueda también se puede usar de forma predeterminada.<br /><br />Un usuario puede:<br /><br />Usar la característica de candidato en la nube<br /><br />Enviar la palabra registrada del usuario<br /><br />**Valor predeterminado:**|
|**TextInput/AllowKoreanExtendedHanja**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowKoreanExtendedHanja<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**TextInput/AllowIMELogging**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: el registro de conversión incorrecta está desactivado. Los datos ajustados automáticamente y los datos del historial de entrada no se guardan en un archivo.<br /><br />**1**: el registro de conversión incorrecta está activado. Los datos ajustados automáticamente y los datos del historial de entrada se guardan en un archivo.<br /><br />**Valor predeterminado** : 1|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**TextInput/AllowJapaneseIVSCharacters**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**TextInput/AllowJapaneseUserDictionary**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: se filtra todo excepto los caracteres JIS.<br /><br />**1**: no se filtra ningún carácter.<br /><br />**Valor predeterminado** : 1|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: se filtra todo excepto los caracteres JIS0208.<br /><br />**1**: no se filtra ningún carácter.<br /><br />**Valor predeterminado** : 1|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: se filtra todo excepto los caracteres JIS0208 o EUDC.<br /><br />**1**: no se filtra ningún carácter.<br /><br />**Valor predeterminado** : 1|
|**TextInput/AllowInputPanel**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Bluetooth/AllowDiscoverableMode**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Bluetooth/AllowAdvertising**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Settings/AllowDataSense**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Settings/AllowVPN**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Settings/AllowWorkplace**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Settings/AllowDateTime**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Settings/AllowLanguage**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Settings/AllowRegion**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Settings/AllowSignInOptions**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Settings/AllowYourAccount**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Settings/AllowPowerSleep**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Settings/AllowAutoPlay**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Experience/AllowCortana**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Search/SafeSearchPermissions**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : filtrado estricto más alto del contenido para adultos<br /><br />**1** : filtrado moderado del contenido para adultos (no se filtrarán los resultados de búsqueda válidos)<br /><br />**Valor predeterminado** : 1|
|**Experience/AllowCopyPaste**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**Forzar tamaño inicial**|Móvil|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: permitir al usuario cambiar el tamaño<br /><br />**1**: forzar la pantalla no completa<br /><br />**2**: forzar la pantalla completa<br /><br />**Valor predeterminado:** 0|
|**Update/RequireDeferUpgrade**|Ambos|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: no aplazar la actualización (permanecer en la rama actual, CB)<br /><br />**1**: habilitar que las actualizaciones se aplacen (el dispositivo sigue la rama actual para negocios, CBB y reglas)<br /><br />**Valor predeterminado: 0**<br /><br />Para obtener más información, vea:<br /><br />[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/DeferUpdatePeriod**|Ambos|**Descripción:** directiva para aplazar actualizaciones de software durante un máximo de 4 semanas<br /><br />**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:** 0: aplicar actualizaciones inmediatamente; 1-4: número de semanas durante las que aplazar las actualizaciones de software.<br /><br />**Valor predeterminado: 0**<br /><br /><br />Para obtener más información, vea:<br /><br />[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/DeferUpgradePeriod**|Ambos|**Descripción:** directiva para aplazar actualizaciones de funciones durante un máximo de 8 meses<br /><br />**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:** 0: aplicar actualizaciones inmediatamente; 1-8: número de meses durante los que aplazar las actualizaciones de funciones.<br /><br />**Valor predeterminado: 0**<br /><br />Para obtener más información, vea:<br /><br />[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/PauseDeferrals**|Ambos|**Descripción:** permite que una máquina CBB deje de recibir actualizaciones durante 5 semanas. Debería usarse en caso de que haya un problema con una actualización.<br /><br />**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: aplicar actualizaciones inmediatamente (valor predeterminado)<br /><br />**1**: pausar las actualizaciones (expira transcurridas 5 semanas)<br /><br />**Valor predeterminado: 0**|

### Windows Defender

|Nombre de la directiva|Soportes|Detalles|
|---------------|------------|-----------|
|**AllowRealtimeMonitoring**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**AllowBehaviorMonitoring**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**AllowIntrusionPreventionSystem**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**AllowIOAVProtection**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**AllowScriptScanning**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**AllowOnAccessProtection**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**RealTimeScanDirection**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: supervisar todos los archivos (bidireccional)<br /><br />**1** : supervisar los archivos entrantes<br /><br />**2** : supervisar los archivos salientes<br /><br />**Valor predeterminado:** 0|
|**DaysToRetainCleanedMalware**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:0** - **90**: representa la cantidad de tiempo que se conservará el malware<br /><br />**Valor predeterminado** 0: se guarda en la carpeta de cuarentena para siempre y no se quita automáticamente|
|**AllowUserUIAccess**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**ScanParameter**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**1** : examen rápido<br /><br />**2**: examen completo<br /><br />**Valor predeterminado** : 1|
|**ScheduleScanDay**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: todos los días<br /><br />**1**: lunes<br /><br />**2**: martes<br /><br />**3**: miércoles<br /><br />**4**: jueves<br /><br />**5**: viernes<br /><br />**6**: sábado<br /><br />**7**: domingo<br /><br />**8** : ningún examen programado<br /><br />**Valor predeterminado:** 0|
|**ScheduleScanTime**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: 12:00<br /><br />**60** : 1:00<br /><br />**120** : 2:00<br /><br />**180** : 3:00<br /><br />**240** : 4:00<br /><br />**300** : 5:00<br /><br />**360** : 6:00<br /><br />**420** : 7:00<br /><br />**480** : 8:00<br /><br />**540** : 9:00<br /><br />**600** : 10:00<br /><br />**660** : 11:00<br /><br />**720** : 12:00<br /><br />**780** : 13:00<br /><br />**840** : 14:00<br /><br />**900** : 15:00<br /><br />**960** : 16:00<br /><br />**1020** : 17:00<br /><br />**1080** : 18:00<br /><br />**1140** : 19:00<br /><br />**1200** : 20:00<br /><br />**1260** : 21:00<br /><br />**1320** : 22:00<br /><br />**1381** : ventana de mantenimiento<br /><br />**Valor predeterminado:** 120|
|**ScheduleQuickScanTime**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: 12:00<br /><br />**60** : 1:00<br /><br />**120** : 2:00<br /><br />**180** : 3:00<br /><br />**240** : 4:00<br /><br />**300** : 5:00<br /><br />**360** : 6:00<br /><br />**420** : 7:00<br /><br />**480** : 8:00<br /><br />**540** : 9:00<br /><br />**600** : 10:00<br /><br />**660** : 11:00<br /><br />**720** : 12:00<br /><br />**780** : 13:00<br /><br />**840** : 14:00<br /><br />**900** : 15:00<br /><br />**960** : 16:00<br /><br />**1020** : 17:00<br /><br />**1080** : 18:00<br /><br />**1140** : 19:00<br /><br />**1200** : 20:00<br /><br />**1260** : 21:00<br /><br />**1320** : 22:00<br /><br />**1380** : 23:00<br /><br />**Valor predeterminado:** 120|
|**AVGCPULoadFactor**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:0** - **100**<br /><br />**Valor predeterminado:** 50|
|**AllowArchiveScanning**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**AllowEmailScanning**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado:** 0|
|**AllowFullScanRemovableDriveScanning**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado:** 0|
|**AllowFullScanOnMappedNetworkDrives**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**AllowScanningNetworkFiles**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1: también se ejecuta cuando RTP está activado y se establece como permitido|
|**SignatureUpdateInterval**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no comprobar las firmas en un intervalo<br /><br />**1**: comprobar las firmas cada hora<br /><br />**2** : comprobar las firmas cada 2 horas, etc.<br /><br />**24** : comprobar las firmas cada día<br /><br />**Valor predeterminado:** 8: comprobar las firmas cada 8 horas|
|**AllowCloudProtection**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : no permitido<br /><br />**1** : permitido<br /><br />**Valor predeterminado** : 1|
|**SubmitSamplesConsent**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0** : preguntar siempre<br /><br />**1** : enviar muestras seguras automáticamente<br /><br />**2** : no enviar nunca<br /><br />**3** : enviar todas las muestras automáticamente<br /><br />**Valor predeterminado:** 0|
|**ExcludedExtensions**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />**Tipo de datos:** cadena<br /><br />**Valores permitidos:**<br /><br />*&lt;lista de extensiones separadas por punto y coma&gt;* p. ej. **obj;lib**<br /><br />**Valor predeterminado:** sin extensiones excluidas|
|**ExcludedPaths**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />**Tipo de datos:** cadena<br /><br />**Valores permitidos:**<br /><br />*&lt;lista de rutas de acceso separadas por punto y coma&gt;*<br /><br />Ejemplo: **c:\test;c:\test1.exe**<br /><br />**Valor predeterminado:** no se excluye ninguna ruta de acceso|
|**ExcludedProcesses**|Escritorio|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />**Tipo de datos:** cadena<br /><br />**Valores permitidos:**<br /><br />*&lt;lista de rutas de acceso separadas por punto y coma&gt;*<br /><br />Ejemplo: **c:\test.exe;c:\test1.exe**<br /><br />**Valor predeterminado:** no se excluye ningún proceso|

### Explorador Edge

|Nombre de la directiva|Soportes|Detalles|
|---------------|------------|-----------|
|**Permitir explorador**|Móvil|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos: 0**: exploración desactivada; **1**: exploración activada.<br /><br />**Valor predeterminado** : 1|
|**AllowSearchSuggestionsinAddressBar**|Ambos|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos: 0**: no mostrar sugerencias de búsqueda; **1**: mostrar sugerencias de búsqueda.<br /><br />**Valor predeterminado** : 1|
|**SendIntranetTraffictoInternetExplorer**|Escritorio|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos: 0**: deshabilitado (abrir sitios de intranet en el explorador Edge); **1**: habilitado (abrir sitios de intranet en Internet Explorer).<br /><br />**Valor predeterminado:** 0|
|**Permitir No realizar seguimiento**|Ambos|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos: 0**: deshabilitado (DNT no enviado); **1**: habilitado (enviar DNT)<br /><br />**Valor predeterminado:** 0|
|**Configurar SmartScreen**|Ambos|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos: 0**: no permitir; **1**: permitir<br /><br />**Valor predeterminado** : 1|
|**Permitir elementos emergentes**|Escritorio|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos: 0**: bloquear elementos emergentes; **1**: permitir elementos emergentes<br /><br />**Valor predeterminado:** 0|
|**Permitir cookies**|Ambos|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowCookies<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos: 0**: no bloquear. Permitir cookies de todos los sitios web; **1**: bloquear solo las cookies de terceros; **2**: bloquear todas las cookies<br /><br />**Valor predeterminado:** 0|
|**Permitir guardar contraseña**|Ambos|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos: 0**: el administrador de contraseñas está deshabilitado; <br />                        **1**: el administrador de contraseñas está habilitado<br /><br />**Valor predeterminado** : 1|
|**Permitir autorrellenar**|Escritorio|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos: 0**: deshabilitado; **1**: habilitado<br /><br />**Valor predeterminado:** 0|
|**Configurar la lista de sitios de empresa**|Escritorio|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />**Tipo de datos:** cadena<br /><br />**Valores permitidos: 0**: no configurado; **1**: usar la lista de sitios del modo de empresa de IE si está configurada; **2**: especificar la ubicación de la lista de sitios de empresa<br /><br />**Valor predeterminado** : 1|

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


