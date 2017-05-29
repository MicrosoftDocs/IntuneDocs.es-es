---
title: "Configuración de directivas de Windows 10 | Microsoft Docs"
description: "Use la configuración de directiva indicada en este tema para configurar las opciones integradas y personalizadas de los dispositivos Windows 10 Escritorio y Windows 10 Mobile inscritos."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/03/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: dd81102eb768ab8ad5f9ee1d2f122f15a8e17b89
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="intune-policy-settings-for-windows-10-devices-in-microsoft-intune"></a>Configuración de directivas de Intune para dispositivos Windows 10 en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Este tema contiene información que le ayudará a entender la configuración de directivas de Intune que puede usar para administrar dispositivos Windows 10. Lea este tema y los procedimientos que se describen en [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](/intune-classic/get-started/windows-pc-management-capabilities-in-microsoft-intune).

Puede elegir entre dos tipos de directivas:

- **Directiva personalizada**: use la **directiva personalizada** de Microsoft Intune para Windows 10 y Windows 10 Mobile para implementar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance), que se puede usar para controlar las características en los dispositivos. Windows 10 tiene disponibles muchas opciones de configuración de CSP, por ejemplo, el [proveedor de servicios de configuración de directivas (CSP de directivas)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Directiva de configuración general**: use este tipo de directiva si quiere seleccionar una configuración de la lista integrada que se proporciona con Microsoft Intune.

## <a name="custom-policy-settings"></a>Configuración de directivas personalizadas

Proporcione las siguientes opciones en una directiva personalizada.

### <a name="general-settings"></a>Configuración general

Escriba un nombre y, si quiere, una descripción para esta directiva que le ayude a identificarla en la consola de Intune.

### <a name="oma-uri-settings"></a>Configuración de OMA-URI

Para cada configuración de OMA-URI que quiera agregar, escriba la siguiente información. Use la [referencia de configuración de URI de Windows 10](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings) de este tema para obtener información sobre la configuración que puede usar:

- **Nombre de la configuración**: escriba un nombre único para la configuración de OMA-URI que le ayude a identificarla en la lista de valores de configuración.
- **Descripción de la configuración**: si lo desea, escriba una descripción para la configuración.
- **Tipo de datos**: elija entre los siguientes tipos de datos:
    - **Cadena**
    - **Cadena (XML)**
    - **Fecha y hora**
    - **Entero**
    - **Punto flotante**
    - **Booleano**
- **OMA-URI (distingue mayúsculas de minúsculas)**: especifique el OMA-URI para el que quiere proporcionar un valor de configuración.
- **Valor**: especifique el valor que quiere asociar al OMA-URI especificado.

### <a name="example"></a>Ejemplo
En la siguiente captura de pantalla, se ha habilitado el valor **Connectivity/AllowVPNOverCellular**. De esta forma, un dispositivo Windows 10 puede abrir una conexión VPN cuando se encuentra en una red de telefonía móvil.

> ![Ejemplo de una directiva personalizada que contiene opciones de VPN](./media/custom-policy-example.png)

### <a name="how-to-find-the-policies-you-can-configure"></a>Búsqueda de las directivas que puede configurar

Encontrará una lista completa de todos los proveedores de servicio de configuración (CSP) que Windows 10 admite en la [referencia del proveedor de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) en la biblioteca de documentación de Windows.

No todas las configuraciones son compatibles con todas las versiones de Windows 10. La tabla en el tema sobre Windows indica las versiones compatibles con cada CSP.

Además, Intune no admite todas las configuraciones que aparecen en el tema. Para saber si Intune admite la configuración que desea, abra el tema correspondiente a dicha configuración. La página de cada configuración muestra una operación compatible. Para trabajar con Intune, la configuración debe ser compatible con las operaciones **Add** o **Replace**.

## <a name="general-configuration-policy-settings"></a>Configuración general de directivas

Use la **directiva de configuración general** de Microsoft Intune para Windows 10 para configurar las opciones integradas de los dispositivos Windows 10 Escritorio y Windows 10 Mobile inscritos.

### <a name="password"></a>Contraseña

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|
|**Requerir contraseña para desbloquear dispositivos**|-|
|**Tipo de contraseña obligatoria**|Especifica si la contraseña debe ser alfanumérica o solo numérica|
|**Tipo de contraseña requerida** - **Número mínimo de conjuntos de caracteres**| Especifica la cantidad de conjuntos de caracteres (letras minúsculas, letras mayúsculas, números y símbolos) debe incluirse en la contraseña|
|**Longitud mínima de contraseña**|Solo se aplica a Windows 10 Mobile|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Para los dispositivos que ejecutan Windows 10: si el dispositivo tiene habilitado BitLocker, se pondrá en el modo de recuperación de BitLocker si el inicio de sesión falla el número de veces especificado. Si el dispositivo no tiene habilitado BitLocker, no se aplica esta configuración.<br>Para los dispositivos que ejecutan Windows 10 Mobile: si el inicio de sesión falla el número de veces especificado, el dispositivo se borrará.|
|**Minutos de inactividad antes de que se apague la pantalla**|Especifica el tiempo durante el que un dispositivo debe estar inactivo antes de que se bloquee la pantalla|
|**Expiración de contraseña (días)**|Especifica el período tras el que debe cambiarse la contraseña del dispositivo|
|**Recordar el historial de contraseñas**|Especifica si se impide que el usuario cree contraseñas usadas anteriormente|
|**Recordar historial de contraseñas** - **Impedir la reutilización de contraseñas anteriores**|Especifica el número de contraseñas usadas anteriormente que recuerda el dispositivo|
|**Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad**|Especifica que el usuario debe escribir una contraseña para desbloquear el dispositivo (solo Windows 10 Mobile)|

### <a name="encryption"></a>Cifrado

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|
|**Requerir cifrado en dispositivo móvil**|Habilita el cifrado en dispositivos de destino<br>(Windows 10 Mobile solo)|

### <a name="system"></a>System (Sistema)

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|
|**Permitir captura de pantalla**|Permite al usuario capturar la pantalla del dispositivo como una imagen (solo Windows 10 Mobile)|
|**Permitir cancelar suscripción manualmente**|Permite al usuario eliminar manualmente la cuenta del área de trabajo desde el dispositivo|
|**Permitir la instalación de certificado raíz manualmente**|Se aplica a Windows 10 Mobile|
|**Permitir que datos de diagnóstico y uso se envíen a Microsoft**|Los valores posibles son:<br><br>**No**: no se envían datos a Microsoft.<br>**Básico**: se envía información limitada a Microsoft<br>**Mejorado**: se envían datos de diagnóstico mejorados a Microsoft<br>**Completo (recomendado)**: envía los mismos datos que **Mejorado**, además de datos adicionales sobre el estado del dispositivo.|


### <a name="account-and-synchronization"></a>Cuenta y sincronización

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|---------------------|
|**Permitir cuenta de Microsoft**|Permite al usuario asociar una cuenta de Microsoft con el dispositivo|
|**Permitir añadir cuentas que no son de Microsoft de forma manual**|Permite al usuario agregar al dispositivo cuentas de correo electrónico que no estén asociadas a una cuenta de Microsoft|
|**Permitir la sincronización de la configuración de las cuentas de Microsoft**|Permite que la configuración de dispositivo y aplicación asociada a una cuenta de Microsoft se sincronice entre los dispositivos|

### <a name="microsoft-edge"></a>Microsoft Edge

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|
|**Permitir explorador web**|Permite el uso del explorador web de Edge en el dispositivo<br>(Windows 10 Mobile solo)|
|**Permitir sugerencias de búsqueda en la barra de direcciones**|Permite que el motor de búsqueda sugiera sitios a medida que se escriben las frases de búsqueda|
|**Permitir enviar tráfico de intranet a Internet Explorer**|Permite a los usuarios abrir sitios web de intranet en Internet Explorer<br>(Windows 10 Escritorio solo)|
|**Permitir No realizar seguimiento**|Configura el explorador Edge para que envíe encabezados Do Not Track a los sitios web que visitan los usuarios|
|**Habilitar SmartScreen**||
|**Permitir Active scripting**|Permite que scripts, como JavaScript, se ejecuten en el explorador Edge|
|**Permitir elementos emergentes**|Solo se aplica a Windows 10 Escritorio|
|**Permitir cookies**||
|**Permitir el autorrelleno**|Permite a los usuarios cambiar la configuración de Autocompletar en el explorador<br>(Windows 10 Escritorio solo)|
|**Permitir administrador de contraseñas**|Habilita o deshabilita la característica Administrador de contraseñas de Edge|
|**Ubicación de la lista de sitios de Modo de empresa**|Especifica dónde se encuentra la lista de sitios web que se abren en modo de empresa. Los usuarios no pueden editar esta lista.<br>(Windows 10 Escritorio solo)|

### <a name="apps"></a>Aplicaciones

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|---------------------|
|**Permitir almacén de aplicaciones**|Solo se aplica a Windows 10 Mobile|



### <a name="cellular"></a>Móvil

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|---------------------|
|**Permitir itinerancia de datos**|Permite itinerancia entre redes al obtener acceso a datos.|
|**Permitir VPN sobre móvil**|Controla si el dispositivo puede tener acceso a las conexiones VPN cuando se conecta a una red móvil.|
|**Permitir itinerancia de VPN sobre móvil**|Controla si el dispositivo puede tener acceso a las conexiones VPN cuando hay itinerancia a una red móvil.|

### <a name="hardware"></a>Hardware

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|
|**Permitir cámara**|-|
|**Permitir almacenamiento extraíble**|Especifica si se pueden usar dispositivos de almacenamiento externo, como una tarjeta SD, con el dispositivo.|
|**Permitir Wi-Fi**|Solo se aplica a Windows 10 Mobile|
|**Permitir compartir Internet**|Permite el uso compartido de una conexión de Internet en el dispositivo|
|**Permitir la configuración Wi-Fi manual**|Controla si el usuario puede configurar sus propias conexiones Wi-Fi o si solo puede usar conexiones configuradas mediante un perfil Wi-Fi.<br>(Windows 10 Mobile solo)|
|**Permitir la conexión automática a zonas Wi-Fi gratuitas**|Permite que el dispositivo se conecte automáticamente a zonas Wi-Fi gratuitas y acepte automáticamente los términos y condiciones para la conexión.|
|**Permitir geolocalización**|Especifica si el dispositivo puede usar información de servicios de ubicación.|
|**Permitir NFC**|Permite que el dispositivo use las funcionalidades de transmisión de datos en proximidad.|
|**Permitir Bluetooth**|-|
|**Permitir modo visible de Bluetooth**|Permite que otros dispositivos habilitados para Bluetooth detecten este dispositivo.|
|**Permitir anuncios de Bluetooth**|Permite que los dispositivos reciban anuncios a través de Bluetooth.|
|**Permitir restablecer teléfono**|Controla si el usuario puede restablecer su dispositivo a la configuración de fábrica|
|**Permitir conexión USB**|Controla si los dispositivos pueden tener acceso a dispositivos de almacenamiento externo a través de una conexión USB.|
|**Permitir modo antirrobo**|Permite habilitar el modo antirrobo de Windows|

### <a name="features"></a>Funciones

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|---------------------|
|**Permitir copiar y pegar**|Solo se aplica a Windows 10 Mobile|
|**Permitir grabación de voz**|Solo se aplica a Windows 10 Mobile|
|**Permitir a Cortana**|Habilita o deshabilita el asistente de voz de Cortana.|
|**Permitir notificaciones del centro de actividades**|Habilita o deshabilita las notificaciones del centro de actividades en la pantalla de bloqueo del dispositivo.<br>(Windows 10 Mobile solo)|

### <a name="windows-defender"></a>Windows Defender

Todos los valores son solo válidos para Windows 10 Escritorio.

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|----------------------|---------------------|
|**Permitir supervisión en tiempo real**|Habilita el análisis en tiempo real de malware, spyware y otro software no deseado|
|**Permitir supervisión del comportamiento**|Permite a Defender comprobar determinados patrones conocidos de actividad sospechosa en los dispositivos|
|**Habilitar Sistema de inspección de red**|El Sistema de inspección de red (NIS) ayuda a proteger los dispositivos contra ataques basados en red mediante el uso de firmas de vulnerabilidades conocidas de Microsoft Endpoint Protection Center para detectar y bloquear el tráfico malintencionado|
|**Examinar todas las descargas**|Controla si Defender examina todos los archivos descargados de Internet|
|**Permitir el examen de scripts**|Permite que Defender examine scripts que se usan en Internet Explorer|
|**Supervisar la actividad de archivos y programas**|Permite que Defender supervise la actividad de archivos y programas en los dispositivos|
|**Días que hay que hacer seguimiento de malware resuelto**|Permite que Defender continúe realizando el seguimiento de malware resuelto durante el número de días especificado para que pueda comprobar de forma manual los dispositivos previamente afectados. Si establece el número de días en **0**, el malware permanece en la carpeta de cuarentena y no se quita automáticamente. |
|**Permitir acceso a la interfaz de usuario de cliente**|Controla si la interfaz de usuario de Windows Defender se oculta a los usuarios.<br>Cuando se cambia esta configuración, surtirá efecto la próxima vez que se reinicie el equipo del usuario.|
|**Programar un examen rápido diario**|Permite programar un examen rápido que se lleva a cabo diariamente a la hora que seleccione|
|**Programar un examen del sistema**|Permite programar un examen completo o rápido del sistema que se lleva a cabo periódicamente en el día y la hora seleccionados|
|**Limitar el uso de CPU durante un examen**|Permite limitar la cantidad de CPU que pueden usar los exámenes (de **1** a **100**)|
|**Examinar archivos de almacenamiento**|Permite que Defender examine archivos almacenados, como archivos .zip o .cab.|
|**Analizar mensajes de correo electrónico**|Permite que Defender analice los mensajes de correo electrónico cuando llegan al dispositivo|
|**Examinar unidades extraíbles**|Permite que Defender analice unidades extraíbles, como sticks USB|
|**Examinar unidades de red asignadas**|Permite que Defender examine archivos en unidades de red asignadas.<br>Si los archivos de la unidad son de solo lectura, Defender no podrá quitar el malware que se encuentre en ellos.|
|**Examinar archivos abiertos desde carpetas compartidas de red**|Permite que Defender examine archivos en unidades de red compartidas (por ejemplo, aquellas a las que se tiene acceso desde una ruta de acceso UNC).<br>Si los archivos de la unidad son de solo lectura, Defender no podrá quitar el malware que se encuentre en ellos.|
|**Intervalo de actualización de firma**|Especifica el intervalo en el que Defender buscará nuevos archivos de firma.|
|**Permitir la protección en la nube**|Permite o bloquea la recepción por parte de Microsoft Active Protection Service de información relativa a la actividad de malware de los dispositivos que administra. Esta información se usa para mejorar el servicio en el futuro.|
|**Pedir a los usuarios el envío de muestras**|Controla si los archivos que podrían requerir un análisis posterior por parte de Microsoft para determinar si son malintencionados se envían automáticamente a Microsoft|
|**Detección de aplicaciones potencialmente no deseadas**|Protege los dispositivos de escritorio de Windows inscritos frente a la ejecución de software que Windows Defender ha clasificado como potencialmente no deseado. Puede protegerse contra la ejecución de estas aplicaciones o puede usar el modo auditoría para informar cuando se instale una aplicación potencialmente no deseada.|
|**Archivos y carpetas que se excluirán al ejecutar un examen o al usar la protección en tiempo real**|Agrega uno o varios archivos y carpetas como **C:\Path** o **%ProgramFiles%\Path\filename.exe** a la lista de exclusiones. Estos archivos y carpetas no se incluyen en los exámenes en tiempo real ni programados.|
|**Extensiones de archivos que se excluirán al ejecutar un examen o al usar protección en tiempo real**|Agrega una o varias extensiones de archivo como **jpg** o **txt** a la lista de exclusiones. Los archivos con estas extensiones no se incluyen en los exámenes en tiempo real ni programados.|
|**Procesos que se excluirán al ejecutar un examen o al utilizar protección en tiempo real**|Agrega uno o varios procesos del tipo **.exe**, **.com** o **.scr** a la lista de exclusiones. Estos procesos no se incluyen en los exámenes en tiempo real ni programados.|


### <a name="updates"></a>Updates

|Nombre de la configuración|Información adicional (si es necesario)|
|----------------|---------------|
|**Permitir actualizaciones automáticas**|Permite las actualizaciones automáticas. Configure una de las opciones siguientes para controlar el comportamiento de las actualizaciones:<br />**Notificar descarga**<br />**Instalar automáticamente en tiempo de mantenimiento**<br />**Instalar y reiniciar automáticamente en tiempo de mantenimiento**<br />**Instalar y reiniciar automáticamente a la hora programada**: tenga en cuenta que, cuando esta opción está seleccionada, también puede configurar los valores **Suprimir la notificación para el usuario final** y **Definir el día de instalación para las actualizaciones programadas**.<br>(Windows 10 Escritorio solo)|
|**Permitir características de evaluación**|Permite a Microsoft implementar características y configuraciones de la versión preliminar en dispositivos Windows 10. Puede seleccionar permitir que se instale únicamente la configuración o todas las configuraciones y características de la versión preliminar.|

### <a name="see-also"></a>Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

