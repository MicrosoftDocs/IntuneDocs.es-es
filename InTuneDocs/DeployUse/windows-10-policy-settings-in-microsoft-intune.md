---
title: "Configuración de directivas de Windows 10 | Microsoft Intune"
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
ms.reviewer: heenamac
ms.suite: ems
ms.sourcegitcommit: 1cccafa5f740bad50779ae36c899fd23ee7dc5f3
ms.openlocfilehash: 70347776f72a3534a4c384957aef01a909767b99


---

# Configuración de directivas de Windows 10 en Microsoft Intune

Use la configuración de directiva indicada en este tema para configurar las opciones de los dispositivos inscritos de la versión de escritorio de Windows 10 y Windows 10 Mobile.

## Configuración general de directivas

Use la **directiva de configuración general** de Microsoft Intune para Windows 10 para configurar las opciones generales de los dispositivos Windows 10 Escritorio y Windows 10 Mobile inscritos. Esta directiva no se puede usar para administrar equipos con Windows 10 con el software cliente de Intune.


### Contraseña

|Nombre de la configuración|Detalles|
|----------------|----------------------|
|**Requerir contraseña para desbloquear dispositivos**|Se requiere una contraseña en dispositivos compatibles.|
|**Tipo de contraseña obligatoria**|Especifica el tipo de contraseña que será necesario, como solo numérica o alfanumérica.|
|**Tipo de contraseña requerida** - **Número mínimo de conjuntos de caracteres**|Hay cuatro conjuntos de caracteres: letras minúsculas, letras mayúsculas, símbolos y números. Esta configuración especifica cuántos conjuntos de caracteres diferentes deben incluirse en la contraseña.|
|**Longitud mínima de la contraseña**|Especifica el número mínimo de caracteres necesarios que debe contener la contraseña del dispositivo.<br>(Windows 10 Mobile solo)|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Borra el dispositivo si hay un error en este número de intentos de inicio de sesión.|
|**Minutos de inactividad antes de que se apague la pantalla**|Especifica el tiempo durante el que un dispositivo debe estar inactivo antes de que se bloquee la pantalla.|
|**Caducidad de contraseña (días)**|Especifica el período de tiempo tras el que debe cambiarse la contraseña del dispositivo.|
|**Recordar el historial de contraseñas**|Especifica si quiere impedir que el usuario final cree contraseñas usadas anteriormente.|
|**Recordar historial de contraseñas** - **Impedir la reutilización de contraseñas anteriores**|Especifica el número de contraseñas usadas previamente que el dispositivo recuerda.|
|**Permitir contraseña de imagen y PIN**|Le permite usar gestos simples en una imagen o un PIN sencillo para iniciar sesión.<br>(Windows 10 Escritorio solo)|
|**Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad**|Si está habilitado, el usuario debe escribir una contraseña para desbloquear el dispositivo en estado de inactividad.<br>(Windows 10 Mobile solo)|

### Cifrado

|Nombre de la configuración|Detalles|
|----------------|----------------------|
|**Requerir cifrado en dispositivo móvil**|Habilita el cifrado en dispositivos de destino.<br>(Windows 10 Mobile solo)|

### System (Sistema)

|Nombre de la configuración|Detalles|
|----------------|----------------------|
|**Permitir captura de pantalla**|Permite al usuario capturar la pantalla del dispositivo como una imagen.<br>(Windows 10 Mobile solo)|
|**Permitir cancelar suscripción manualmente**|Permite al usuario eliminar manualmente la cuenta del área de trabajo desde el dispositivo.|
|**Permitir la instalación de certificado raíz manualmente**|Especifica si el usuario puede instalar certificados raíz manualmente.<br>(Windows 10 Mobile solo)|
|**Permitir que datos de diagnóstico y uso se envíen a Microsoft**|Determina la cantidad de datos de diagnóstico y uso que se envían a Microsoft desde los dispositivos.<br><br>**No**: no se envían datos a Microsoft.<br>**Básico**: el dispositivo solo envía información limitada a Microsoft.<br>**Mejorado**: envía datos de diagnóstico mejorados a Microsoft.<br>**Completo (recomendado)**: envía los mismos datos que **Mejorado**, además de datos adicionales sobre el estado del dispositivo.|


### Cuenta y sincronización

|Nombre de la configuración|Detalles|
|----------------|----------------------|---------------------|
|**Permitir cuenta de Microsoft**|Permite al usuario asociar una cuenta de Microsoft con el dispositivo.|
|**Permitir añadir cuentas que no son de Microsoft de forma manual**|Permite al usuario agregar al dispositivo cuentas de correo electrónico que no estén asociadas a una cuenta de Microsoft.|
|**Permitir la sincronización de la configuración de las cuentas de Microsoft**|Permite que la configuración de dispositivo y aplicación asociada a una cuenta de Microsoft se sincronice entre los dispositivos.|

### Configuración de correo electrónico

|Nombre de la configuración|Detalles|
|----------------|----------------------|---------------------|
|**Hacer que la cuenta Microsoft sea opcional en la aplicación Windows Mail**|Configure esta opción para quitar el requisito de una cuenta de Microsoft en Correo de Windows.<br>Windows 10 Escritorio solo|



### Microsoft Edge

|Nombre de la configuración|Detalles|
|----------------|----------------------|
|**Permitir explorador web**|Permite el uso del explorador web de Edge en el dispositivo.<br>(Windows 10 Mobile solo)|
|**Permitir sugerencias de búsqueda en la barra de direcciones**|Permite que el motor de búsqueda sugiera sitios a medida que se escriben las frases de búsqueda.|
|**Permitir enviar tráfico de intranet a Internet Explorer**|Permite a los usuarios abrir sitios web de intranet en Internet Explorer.<br>(Windows 10 Escritorio solo)|
|**Permitir no rastrear**|Configura el explorador Edge para que envíe encabezados Do Not Track a los sitios web que visitan los usuarios.|
|**Habilitar SmartScreen**|Habilita la configuración del explorador SmartScreen en dispositivos.|
|**Permitir Active scripting**|Permite que se ejecuten en el explorador Edge scripts como JavaScript.|
|**Permitir elementos emergentes**|Habilita o deshabilita el bloqueador de elementos emergentes del explorador.<br>(Windows 10 Escritorio solo)|
|**Permitir cookies**|Permite o deshabilita las cookies.|
|**Permitir autorrellenar**|Permite a los usuarios cambiar la configuración de Autocompletar en el explorador.<br>(Windows 10 Escritorio solo)|
|**Permitir administrador de contraseñas**|Habilita o deshabilita la característica Administrador de contraseñas de Edge.|
|**Ubicación de la lista de sitios de Modo de empresa**|Especifica dónde se encuentra la lista de sitios web que se abrirá en modo de empresa. Los usuarios no pueden editar esta lista.<br>(Windows 10 Escritorio solo)|

### Aplicaciones

|Nombre de la configuración|Detalles|
|----------------|----------------------|---------------------|
|**Permitir almacén de aplicaciones**|Permite al usuario tener acceso a la tienda de aplicaciones en el dispositivo.<br>(Windows 10 Mobile solo)|



### Móvil

|Nombre de la configuración|Detalles|
|----------------|----------------------|---------------------|
|**Permitir itinerancia de datos**|Permite movilidad entre redes al obtener acceso a datos.|
|**Permitir VPN sobre móvil**|Controla si el dispositivo puede tener acceso a las conexiones VPN cuando se conecta a una red móvil.|
|**Permitir itinerancia de VPN sobre móvil**|Controla si el dispositivo puede tener acceso a las conexiones VPN cuando hay itinerancia a una red móvil.|

### Hardware

|Nombre de la configuración|Detalles|
|----------------|----------------------|
|**Permitir cámara**|Especifica si se puede usar la cámara del dispositivo.|
|**Permitir almacenamiento extraíble**|Especifica si se pueden usar dispositivos de almacenamiento externo, como una tarjeta SD, con el dispositivo.|
|**Permitir Wi-Fi**|Permite usar la funcionalidad de Wi-Fi del dispositivo.<br>(Windows 10 Mobile solo)|
|**Permitir compartir Internet**|Permite el uso compartido de una conexión de Internet en el dispositivo.|
|**Permitir la configuración Wi-Fi manual**|Controla si el usuario puede configurar sus propias conexiones Wi-Fi o si solo puede usar conexiones configuradas mediante un perfil Wi-Fi.<br>(Windows 10 Mobile solo)|
|**Permitir la conexión automática a zonas Wi-Fi gratuitas**|Permite que el dispositivo se conecte automáticamente a zonas Wi-Fi gratuitas y acepte automáticamente los términos y condiciones para la conexión.|
|**Permitir geolocalización**|Especifica si el dispositivo puede usar información de servicios de ubicación.|
|**Permitir NFC**|Permite que el dispositivo use las funcionalidades de transmisión de datos en proximidad.|
|**Permitir Bluetooth**|Habilita el uso de funcionalidades de Bluetooth en el dispositivo.|
|**Permitir modo visible de Bluetooth **|Permite que otros dispositivos habilitados para Bluetooth detecten este dispositivo.|
|**Permitir anuncios de Bluetooth**|Permite que los dispositivos reciban anuncios a través de Bluetooth.|
|**Permitir modo conectable de Bluetooth **|**Importante:** esta configuración ya no es compatible con Windows 10 y se eliminará en el futuro.|
|**Permitir restablecer teléfono**|Controla si el usuario puede restablecer su dispositivo a la configuración de fábrica.|
|**Permitir conexión USB**|Controla si los dispositivos pueden tener acceso a dispositivos de almacenamiento externo a través de una conexión USB.|
|**Permitir modo antirrobo**|Permite habilitar el modo antirrobo de Windows.|

### Funciones

|Nombre de la configuración|Detalles|
|----------------|----------------------|---------------------|
|**Permitir copiar y pegar**|Habilita o deshabilita el uso de copiar y pegar en el dispositivo.<br>(Windows 10 Mobile solo)|
|**Permitir grabación de voz**|Habilita o deshabilita las características de grabación de voz en el dispositivo.<br>(Windows 10 Mobile solo)|
|**Permitir a Cortana**|Habilita o deshabilita el asistente de voz de Cortana.|
|**Permitir notificaciones del centro de actividades**|Habilita o deshabilita notificaciones del centro de actividades en la pantalla de bloqueo del dispositivo.<br>(Windows 10 Mobile solo)|

### Defender

Todos los valores son solo válidos para Windows 10 Escritorio.

|Nombre de la configuración|Detalles|
|-|-|
|**Permitir supervisión en tiempo real**|Habilita el análisis en tiempo real de malware, spyware y otro software no deseado.|
|**Permitir supervisión del comportamiento**|Permite a Defender comprobar determinados patrones conocidos de actividad sospechosa en los dispositivos.|
|**Habilitar Sistema de inspección de red**|El Sistema de inspección de red (NIS) ayuda a proteger los dispositivos contra ataques basados en red mediante el uso de firmas de vulnerabilidades conocidas de Microsoft Endpoint Protection Center para detectar y bloquear el tráfico malintencionado.|
|**Analizar todas las descargas**|Controla si Defender analiza todos los archivos descargados de Internet.|
|**Permitir análisis de scripts**|Permite que Defender examine scripts que se usan en Internet Explorer.|
|**Supervisar actividad de archivos y programas**|Habilite esta opción para permitir que Defender supervise la actividad de archivos y programas en los dispositivos.|
|**Días que hay que hacer seguimiento de malware resuelto**|Permite que Defender continúe realizando el seguimiento de malware resuelto durante el número de días especificado para que pueda comprobar de forma manual los dispositivos previamente afectados. Si establece el número de días en **0**, el malware permanece en la carpeta de cuarentena y no se quita automáticamente. |
|**Permitir acceso a la interfaz de usuario de cliente**|Controla si la interfaz de usuario de Windows Defender se oculta a los usuarios finales.<br>Cuando se cambia esta configuración, surtirá efecto la próxima vez que se reinicie el equipo del usuario final.|
|**Programar un examen rápido diario**|Permite programar un examen rápido que se lleva a cabo diariamente a la hora que seleccione.|
|**Programar un examen del sistema**|Permite programar un examen completo o rápido del sistema que se lleva a cabo periódicamente en el día y la hora seleccionados.|
|**Limitar el uso de la CPU durante un análisis a**|Permite limitar la cantidad de CPU que pueden usar los exámenes (de **1** a **100**)|
|**Examinar archivos de almacenamiento**|Permite que Defender examine archivos almacenados, como archivos Zip o Cab.|
|**Analizar mensajes de correo electrónico**|Permite que Defender analice los mensajes de correo electrónico cuando llegan al dispositivo.|
|**Analizar unidades extraíbles**|Permite que Defender analice unidades extraíbles, como sticks USB.|
|**Examinar unidades de red asignadas**|Permite que Defender examine archivos en unidades de red asignadas.<br>Si los archivos de la unidad son de solo lectura, Defender no podrá quitar el malware que se encuentre en ellos.|
|**Examinar archivos abiertos desde carpetas compartidas de red**|Permite que Defender examine archivos en unidades de red compartidas (por ejemplo, aquellas a las que se tiene acceso desde una ruta de acceso UNC).<br>Si los archivos de la unidad son de solo lectura, Defender no podrá quitar el malware que se encuentre en ellos.|
|**Intervalo de actualización de firma**|Especifica el intervalo en el que Defender buscará nuevos archivos de firma.|
|**Permitir la protección en la nube**|Permite o bloquea la recepción por parte de Microsoft Active Protection Service de información sobre la actividad de malware de los dispositivos que administra. Esta información se usa para mejorar el servicio en el futuro.|
|**Pedir a los usuarios el envío de muestras**|Controla si los archivos que podrían requerir un análisis posterior por parte de Microsoft para determinar si son malintencionados se envían automáticamente a Microsoft.|
|**Detección de aplicaciones potencialmente no deseadas**|Esta configuración se puede usar para proteger los equipos de escritorio de Windows inscritos frente a la ejecución de software que Windows Defender ha clasificado como potencialmente no deseado. Puede protegerse contra la ejecución de estas aplicaciones o puede usar el modo auditoría para informar cuando se instale una aplicación potencialmente no deseada.|
|**Archivos y carpetas que se van a excluir al ejecutar un análisis o al usar la protección en tiempo real**|Agrega uno o varios archivos y carpetas como **C:\Path** o **%ProgramFiles%\Path\filename.exe** a la lista de exclusiones. Estos archivos y carpetas no se incluirán en los análisis en tiempo real ni programados.|
|**Extensiones de archivo que se deben excluir al ejecutar un análisis o al utilizar protección en tiempo real**|Agrega una o varias extensiones de archivo como **jpg** o **txt** a la lista de exclusiones. Los archivos con estas extensiones no se incluirán en los análisis en tiempo real ni programados.|
|**Procesos que se deben excluir al ejecutar un análisis o al utilizar protección en tiempo real**|Agrega uno o varios procesos del tipo **.exe**, **.com** o **.scr** a la lista de exclusiones. Estos procesos no se incluirán en los análisis en tiempo real ni programados.| 


### Configuración de actualizaciones

|Nombre de la configuración|Detalles|
|----------------|---------------|
|**Permitir actualizaciones automáticas**|Habilite esta configuración para permitir las actualizaciones automáticas. Luego, configure una de las opciones siguientes para controlar el comportamiento de las actualizaciones:<br /><br />**Notificar descarga**<br /><br />**Instalar automáticamente en tiempo de mantenimiento**<br /><br />**Instalar y reiniciar automáticamente en tiempo de mantenimiento**<br /><br />**Instalar y reiniciar automáticamente a la hora programada** **Nota:** cuando esta opción está seleccionada, también puede configurar los valores siguientes: **Eliminar la notificación para el usuario final** y **Definir el día de instalación para las actualizaciones programadas**.<br>(Windows 10 Escritorio solo)|

## Configuración de directivas personalizadas
Use la **directiva de configuración personalizada** de Microsoft Intune para Windows 10 y Windows 10 Mobile para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance) que puede usarse para controlar características en dispositivos con Windows 10 y Windows 10 Mobile. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad está destinada a permitirle implementar la configuración de Windows 10 que no se puede configurar con una directiva de configuración general de Intune.



### Configuración general de directiva personalizada

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre**|Escriba un nombre único para la directiva que le ayude a identificarla en la consola de Intune.|
    |**Descripción**|Proporcione una descripción general de la directiva y otra información relevante que le ayude a encontrarla.|

### Configuración de OMA-URI de directiva personalizada

|Nombre de la configuración|Detalles|
    |--------|--------------------|
    |**Nombre de la configuración**|Escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.|
    |**Descripción del valor**|Proporcione una descripción que ofrezca una visión general del valor y otra información relevante que le ayude a encontrarlo.|
    |**Tipo de datos**|Seleccione el tipo de fecha en que especificará este valor OMA-URI. Elija de entre las siguientes opciones:<br /><br />-   **String**<br />-   **Cadena (XML)**<br />-   **Fecha y hora**<br />-   **Integer**<br />-   **Punto flotante**<br />-   **Boolean**|
    |**OMA-URI (distingue mayúsculas de minúsculas)**|Especifique el OMA-URI para el que desee suministrar un valor.|
    |**Valor**|Especifique el valor asociado con el OMA-URI especificado anteriormente.|


## Configuración de URI personalizada para dispositivos de Windows 10
En este tema se enumeran los valores que puede configurar para dispositivos Windows 10 y Windows 10 Mobile en una **directiva personalizada de Windows 10** de Microsoft Intune.

Todos los dispositivos deben estar inscritos con Intune si quiere usar la directiva de URI de Windows personalizada.

### Configuración URI de directiva

|Nombre de la directiva|Detalles|
|---------------|------------|-----------|
|**​Permitir la actualización automática**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** - **5** (valor predeterminado: **1**)|
|**Programa el día de la instalación**<br>(solo Mobile)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: todos los días (valor predeterminado)<br>**1**: domingo<br>**2**: lunes<br>**3**: martes<br>**4**: miércoles<br>**5**: jueves<br>**6**: viernes<br>**7**: sábado|
|**Programar la hora de la instalación**<br>(Escritorio y Mobile)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: **23** horas (**0** es medianoche) (valor predeterminado: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: el usuario no puede establecer el temporizador de período de gracia de la contraseña y el valor se establece como "siempre"<br>**1**: el usuario puede establecer el temporizador de período de gracia de la contraseña (valor predeterminado)|
|**WiFi/AllowWiFi**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no se permite **usar la conexión Wi-Fi**.<br>**1**: **se permite usar la conexión Wi-Fi** (valor predeterminado)|
|**Wi-Fi/AllowInternetSharing**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitir el uso compartido de Internet.<br>**1**: se permite el uso compartido de Internet (valor predeterminado).|
|**Wi-Fi/AllowAutoConnectToWiFiSenseHotspots**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Wi-Fi/AllowManualWiFiConfiguration**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no se permite la conexión Wi-Fi fuera de la MDM aprovisionada.<br>**1**: se permite agregar nuevos SSID de red más allá de los de la MDM aprovisionada (valor predeterminado).|
|**System/AllowLocation**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**System/AllowTelemetry**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido (valor de Enterprise solo)<br>**1** : limitado<br>**2**: completo (valor predeterminado)<br>**3**: completo e información de diagnóstico|
|**Sistema/AllowExperimentation**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: solo configuración (valor predeterminado)<br>**2**: configuración y experimentación|
|**Security/AntiTheftMode**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no permitir el modo antirrobo<br>**1**: preferencia del usuario (valor predeterminado)|
|**Connectivity/AllowUSBConnection**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**System/AllowUserToResetPhone**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Connectivity/AllowCellularDataRoaming**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Connectivity/AllowVPNOverCellular**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no se permite la VPN a través de la red de telefonía móvil<br>**1**: la VPN puede usar cualquier conexión, incluida la de la red de telefonía móvil (valor predeterminado)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Connectivity/AllowBluetooth**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no se permite al usuario activar el Bluetooth.<br>**1**: reservado. El usuario puede activar y configurar el Bluetooth (no admitido en Windows Phone 8.1 para MDM, EAS, Windows 10 Escritorio o Windows 10 Mobile)<br>**2**: permitido El usuario puede activar y configurar el Bluetooth (valor predeterminado)|
|**Experience/AllowScreenCapture**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Experience/AllowTaskSwitcher**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Experience/AllowVoiceRecording**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Experience/AllowSyncMySettings**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitir itinerancia<br>**1**: permitir itinerancia (valor predeterminado)|
|**Experience/AllowManualMDMUnenrollment**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Accounts/AllowMicrosoftAccountConnection**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Security/AllowManualRootCertificateInstallation**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Security/AllowAddProvisioningPackages**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Search/DisableBackoff**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** (valor predeterminado)<br>**1**|
|**Search/PreventRemoteQueries**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**<br>**1** (valor predeterminado)|
|**Search/AllowUsingDiacritics**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br> **0** (valor predeterminado)<br>**1**|
|**Search/AlwaysUseAutoLangDetection**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** (valor predeterminado)<br>**1**|
|**Search/DisableRemovableDriveIndexing**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** (valor predeterminado)<br>**1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**<br>**1** (valor predeterminado)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** (valor predeterminado)<br>**1**|
|**Security/AllowRemoveProvisioningPackage**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Security/RequireProvisioningPackageSignature**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** (valor predeterminado)<br>**1**|
|**AboveLock/AllowActionCenterNotifications**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**TextInput/AllowIMENetworkAccess**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitir<br>El diccionario extendido abierto está desactivado.<br>Un usuario no puede:<br>Agregar un nuevo diccionario extendido abierto<br /><br />Agregar un nuevo archivo de configuración de integración de búsqueda<br>Usar la característica de candidato en la nube<br>Enviar la palabra registrada del usuario<br>Además:<br>Un diccionario extendido abierto que se ha agregado antes de habilitar esta configuración de directiva no se usa para la conversión.<br>Un archivo de configuración de integración de búsqueda que se ha instalado antes de habilitar esta configuración de directiva no se usa.<br>**1**: permitir<br>El diccionario extendido abierto se puede agregar y usar de forma predeterminada. La función de integración de búsqueda también se puede usar de forma predeterminada.<br>Un usuario puede:<br>Usar la característica de candidato en la nube<br>Enviar la palabra registrada del usuario.|
|**TextInput/AllowIMELogging**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: el registro de conversión incorrecta está desactivado. Los datos ajustados automáticamente y los datos del historial de entrada no se guardan en un archivo.<br>**1**: el registro de conversión incorrecta está activado. Los datos ajustados automáticamente y los datos del historial de entrada se guardan en un archivo (valor predeterminado).|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**TextInput/AllowJapaneseIVSCharacters**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**TextInput/AllowJapaneseUserDictionary**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no se filtra ningún carácter (valor predeterminado).<br>**1**: se filtra todo excepto los caracteres Shift JIS.|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br /><br />**0**: no se filtra ningún carácter (valor predeterminado).<br>**1**: se filtra todo excepto los caracteres JIS0208.|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no se filtra ningún carácter (valor predeterminado).<br>**1**: se filtra todo excepto los caracteres JIS0208 o EUDC.|
|**TextInput/AllowInputPanel**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Bluetooth/AllowDiscoverableMode**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Bluetooth/AllowAdvertising**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Settings/AllowDataSense**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Settings/AllowVPN**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Settings/AllowWorkplace**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Settings/AllowDateTime**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Settings/AllowLanguage**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Settings/AllowRegion**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Settings/AllowSignInOptions**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Settings/AllowYourAccount**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Settings/AllowPowerSleep**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Settings/AllowAutoPlay**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Experience/AllowCortana**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Search/SafeSearchPermissions**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : filtrado estricto más alto del contenido para adultos<br>**1**: filtrado moderado del contenido para adultos (no se filtrarán los resultados de búsqueda válidos, valor predeterminado)|
|**Experience/AllowCopyPaste**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**Forzar tamaño inicial**<br>(solo Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: permitir al usuario cambiar el tamaño (valor predeterminado)<br>**1**: forzar la pantalla no completa<br>**2**: forzar la pantalla completa|
|**Update/RequireDeferUpgrade**<br>(Escritorio y Mobile)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no aplazar la actualización (permanecer en la rama actual, CB, valor predeterminado)<br>**1**: habilitar que las actualizaciones se aplacen (el dispositivo sigue la rama actual para negocios, CBB y reglas)<br /><br />Para obtener más información, vea:<br>[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>(Escritorio y Mobile)|**Descripción:** directiva para aplazar actualizaciones de software durante un máximo de 4 semanas<br /><br />**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br> **0**: aplicar actualizaciones inmediatamente (valor predeterminado)<br>**1**-**4**: número de semanas durante las que aplazar las actualizaciones de software.<br /><br />Para obtener más información, vea:<br>[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>(Escritorio y Mobile)|**Descripción:** directiva para aplazar actualizaciones de funciones durante un máximo de 8 meses<br /><br />**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: aplicar actualizaciones inmediatamente (valor predeterminado)<br>**1**-**8**: número de meses durante los que aplazar actualizaciones de características.<br /><br />Para obtener más información, vea:<br>[Introducción al mantenimiento de Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Plan de implementación de Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>(Escritorio y Mobile)|**Descripción:** permite que una máquina CBB deje de recibir actualizaciones durante 5 semanas. Debería usarse en caso de que haya un problema con una actualización.<br /><br />**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: aplicar actualizaciones inmediatamente (valor predeterminado)<br>**1**: pausar las actualizaciones (expira transcurridas 5 semanas)|

### Configuración URI de Windows Defender

|Nombre de la directiva|Detalles|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**AllowBehaviorMonitoring**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**AllowIntrusionPreventionSystem**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**AllowIOAVProtection**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**AllowScriptScanning**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**AllowOnAccessProtection**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**RealTimeScanDirection**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: supervisar todos los archivos (bidireccional, valor predeterminado)<br>**1** : supervisar los archivos entrantes<br>**2** : supervisar los archivos salientes|
|**DaysToRetainCleanedMalware**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** - **90**: representa la cantidad de tiempo que se conservará el malware.<br>**Valor predeterminado:** **0:** se guarda en la carpeta de cuarentena para siempre y no se quita automáticamente.|
|**AllowUserUIAccess**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**ScanParameter**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**1**: examen rápido (valor predeterminado)<br>**2**: examen completo|
|**ScheduleScanDay**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** -todos los días (valor predeterminado)<br>**1**: lunes<br>**2**: martes<br>**3**: miércoles<br>**4**: jueves<br>**5**: viernes<br>**6**: sábado<br>**7**: domingo<br>**8** : ningún examen programado|
|**ScheduleScanTime**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: 12:00<br>**60** : 1:00<br>**120**: 2:00 (valor predeterminado)<br>**180** : 3:00<br>**240** : 4:00<br>**300** : 5:00<br>**360** : 6:00<br>**420** : 7:00<br>**480** : 8:00<br>**540** : 9:00<br>**600** : 10:00<br>**660** : 11:00<br>**720** : 12:00<br>**780** : 13:00<br>**840** : 14:00<br>**900** : 15:00<br>**960** : 16:00<br>**1020** : 17:00<br>**1080** : 18:00<br>**1140** : 19:00<br>**1200** : 20:00<br>**1260** : 21:00<br>**1320** : 22:00<br>**1381** : ventana de mantenimiento|
|**ScheduleQuickScanTime**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br>**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: 12:00<br>**60** : 1:00<br>**120**: 2:00 (valor predeterminado)<br>**180** : 3:00<br>**240** : 4:00<br>**300** : 5:00<br>**360** : 6:00<br>**420** : 7:00<br>**480** : 8:00<br>**540** : 9:00<br>**600** : 10:00<br>**660** : 11:00<br>**720** : 12:00<br>**780** : 13:00<br>**840** : 14:00<br>**900** : 15:00<br>**960** : 16:00<br>**1020** : 17:00<br>**1080** : 18:00<br>**1140** : 19:00<br>**1200** : 20:00<br>**1260** : 21:00<br>**1320** : 22:00<br>**1380** : 23:00|
|**AVGCPULoadFactor**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos: 0** - **100** (valor predeterminado: **50**)|
|**AllowArchiveScanning**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**AllowEmailScanning**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />**Tipo de datos:** entero<br>**Valores permitidos:**<br>**0**: no permitido (valor predeterminado)<br>**1** : permitido|
|**AllowFullScanRemovableDriveScanning**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no permitido (valor predeterminado)<br>**1** : permitido|
|**AllowFullScanOnMappedNetworkDrives**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**AllowScanningNetworkFiles**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1** permitido (valor predeterminado): también se ejecuta cuando RTP está activado y se establece como permitido|
|**SignatureUpdateInterval**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no comprobar las firmas en un intervalo<br>**1**: comprobar las firmas cada hora<br>**2** : comprobar las firmas cada 2 horas, etc.<br>**24** : comprobar las firmas cada día<br>**Valor predeterminado:** 8: comprobar las firmas cada 8 horas|
|**AllowCloudProtection**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0** : no permitido<br>**1**: permitido (valor predeterminado)|
|**SubmitSamplesConsent**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: preguntar siempre (valor predeterminado)<br>**1** : enviar muestras seguras automáticamente<br>**2** : no enviar nunca<br>**3** : enviar todas las muestras automáticamente|
|**ExcludedExtensions**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />**Tipo de datos:** cadena<br /><br />**Valores permitidos:**<br>*&lt;lista de extensiones separadas por punto y coma&gt;* p. ej. **obj;lib**<br>**Valor predeterminado**: no se excluye ninguna extensión|
|**ExcludedPaths**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />**Tipo de datos:** cadena<br /><br />**Valores permitidos:**<br /><br />*&lt;lista de rutas de acceso separadas por punto y coma&gt;*<br /><br />Ejemplo: **c:\test;c:\test1.exe**<br /><br />**Valor predeterminado:** no se excluye ninguna ruta de acceso|
|**ExcludedProcesses**<br>(solo Escritorio)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />**Tipo de datos:** cadena<br /><br />**Valores permitidos:**<br>*&lt;lista de rutas de acceso separadas por punto y coma&gt;*<br>Ejemplo: **c:\test.exe;c:\test1.exe**<br>**Valor predeterminado:** no se excluye ningún proceso|

### Configuración URI de explorador Edge

|Nombre de la directiva|Detalles|
|---------------|------------|-----------|
|**Permitir explorador**<br>(solo Mobile)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: exploración desactivada<br>**1**: exploración activada (valor predeterminado)|
|**AllowSearchSuggestionsinAddressBar**<br>(Escritorio y Mobile)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no mostrar sugerencias de búsqueda<br>**1**: mostrar sugerencias (valor predeterminado)|
|**SendIntranetTraffictoInternetExplorer**<br>(solo Escritorio)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: deshabilitado (abrir sitios de intranet en el explorador Edge, valor predeterminado).<br>**1**: habilitado (abrir sitios de intranet en Internet Explorer).|
|**Permitir No realizar seguimiento**<br>(Escritorio y Mobile)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: deshabilitado (DNT no enviado, valor predeterminado)<br>**1**: habilitado (enviar DNT)|
|**Configurar SmartScreen**<br>(Escritorio y Mobile)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no permitir<br>**1**: permitir (valor predeterminado)|
|**Permitir elementos emergentes**<br>(solo Escritorio)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: bloquear elementos emergentes (valor predeterminado)<br>**1**: permitir elementos emergentes|
|**Permitir cookies**<br>(Escritorio y Mobile)|**Ruta de acceso completa de URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowCookies<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: no bloquear. Permitir cookies de todos los sitios web (valor predeterminado)<br>**1**: bloquear solo cookies de terceros<br>**2**: bloquear todas las cookies|
|**Permitir guardar contraseña**<br>(Escritorio y Mobile)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: el administrador de contraseñas está deshabilitado <br>**1**: el administrador de contraseñas está habilitado (valor predeterminado)|
|**Permitir autorrellenar**<br>(solo Escritorio)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />**Tipo de datos:** entero<br /><br />**Valores permitidos:**<br>**0**: deshabilitado (valor predeterminado)<br>**1**: habilitado|
|**Configurar la lista de sitios de empresa**<br>(solo Escritorio)|**Ruta de acceso completa del URI:** ./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />**Tipo de datos:** cadena<br /><br />**Valores permitidos:<br>0**: no configurado<br>**1** usar la lista de sitios del modo de empresa de IE si está configurada (valor predeterminado)<br>**2**: especificar la ubicación de la lista de sitios de la empresa|

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO3-->


