---
# required metadata

title: Opciones de configuración de directiva de configuración de Android en Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Opciones de configuración de directiva de configuración de Android en Microsoft Intune

## Directiva de configuración general

Use la **directiva de configuración general de Android** de Microsoft Intune para establecer las siguientes opciones:

-   **Configuración de seguridad de dispositivos móviles** : elija entre una lista de configuraciones predefinidas que permiten controlar una variedad de características y la funcionalidad en el dispositivo.

-   **Pantalla completa** (solo para dispositivos Samsung KNOX): permite bloquear un dispositivo para que solo funcionen determinadas características. Por ejemplo, puede permitir que un dispositivo ejecute solo una aplicación administrada que especifique, o puede deshabilitar los botones de volumen de un dispositivo. Esta configuración podría utilizarse para un modelo de demostración de un dispositivo o para un dispositivo que está dedicado a realizar solo una función, como un dispositivo de punto de venta.

-   **Aplicaciones compatibles y no compatibles**: especifique una lista de las aplicaciones compatibles y no compatibles de su empresa. En los dispositivos iOS y Android, el **informe de aplicaciones no conformes** puede utilizarse para comparar la conformidad de las aplicaciones especificadas en la lista con las aplicaciones que los usuarios han instalado (pero en realidad no pueden impedir la instalación de la aplicación).

> [!TIP]
> Puede configurar los términos y condiciones de los usuarios para asegurarse de que saben que las aplicaciones de su dispositivo, incluidas las aplicaciones personales, se evaluarán y que las aplicaciones no conformes se bloquearán o se notificarán como no conformes. Los usuarios deben aceptar estos términos y condiciones para poder inscribir su dispositivo y utilizar el portal de empresa para obtener aplicaciones. Para obtener más información sobre cómo usar los términos y condiciones, vea [Configuración de la directiva de términos y condiciones en Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md)..

Si el valor que busca no aparece en este tema, puede crearlo mediante una directiva personalizada de Android que le permita usar la configuración de OMA-URI para controlar el dispositivo. Para obtener más información, vea **Opciones de configuración de directiva personalizadas** más adelante en este tema.

### Configuración de contraseña

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|-|----------------|----------------|
|**Requerir una contraseña para desbloquear dispositivos móviles**|Se requiere una contraseña en dispositivos compatibles.|Sí|Sí|
|**Longitud mínima de la contraseña**|La longitud mínima de la contraseña.|Sí|Sí|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Borra el dispositivo si hay un error en este número de intentos de inicio de sesión.|Sí|Sí|
|**Minutos de inactividad antes de que se apague la pantalla**|Especifique el número de minutos antes de que el dispositivo se bloquee automáticamente.|Sí|Sí|
|**Caducidad de contraseña (días)**|El número de días antes de que se deba cambiar una contraseña.|Sí|Sí|
|**Recordar el historial de contraseñas**|Se recuerdan las contraseñas usadas anteriormente.|Sí|Sí|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Impide que se vuelvan a usar contraseñas ya utilizadas.|Sí|Sí|
|**Calidad de contraseña**|Seleccione el nivel requerido de complejidad de la contraseña y también si se pueden usar dispositivos biométricos.|Sí|Sí|
|**Permitir desbloqueo mediante huellas digitales**|Permite usar una huella digital para desbloquear el dispositivo.|No|Sí|

### Configuración de cifrado

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Requerir cifrado en dispositivo móvil**|Requiere el cifrado de los archivos en el dispositivo móvil.|Sí|Sí|
|**Requerir cifrado en tarjetas de almacenamiento**|Especifica si se debe cifrar la tarjeta de almacenamiento del dispositivo.|No|Sí|

### Configuración del sistema

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir captura de pantalla**|Permite al usuario capturar el contenido en pantalla como una imagen.|No|Sí|
|**Permitir el envío de datos de diagnóstico**|Permite enviar información de diagnóstico a Google desde el dispositivo.|No|Sí|
|**Permitir el restablecimiento de la configuración de fábrica**|Permite que el usuario realice un restablecimiento de la configuración de fábrica en el dispositivo.|No|Sí|

### Configuración de nube: documentos y datos

|Nombre de la configuración|Detalles|Android y Samsung KNOX|Android 4.0+|
|----------------|----------------------------|----------------|
|**Permitir copia de seguridad de Google**|Permite el uso de la copia de seguridad de Google.|No|Sí|

### Configuración de nube: cuentas y sincronización

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir la sincronización automática de la cuenta de Google**|Permite que la configuración de la cuenta de Google se sincronice automáticamente.|No|Sí|

### Configuración de la aplicación: explorador

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir explorador web**|Especifica si se puede usar el explorador web del dispositivo.|No|Sí|
|**Permitir el autorrelleno**|Permite usar la función Autorrellenar del explorador web.|No|Sí|
|**Permitir bloqueador de elementos emergentes**|Permite usar el bloqueador de elementos emergentes en el explorador web.|No|Sí|
|**Permitir cookies**|Permite que el explorador web del dispositivo use cookies.|No|Sí|
|**Permitir Active scripting**|Permite que el explorador web del dispositivo use Active scripting.|No|Sí|

### Configuración de la aplicación: aplicaciones

|Nombre de la configuración|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir Google Play Store**|Permite al usuario tener acceso a Google Play Store en el dispositivo.|No|Sí|

### Configuración de funcionalidades del dispositivo: hardware

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir cámara**|Permite el uso de la cámara del dispositivo.|Sí|Sí|
|**Permitir almacenamiento extraíble**|Permite usar un almacenamiento extraíble (como una tarjeta SD) en el dispositivo.|No|Sí|
|**Permitir Wi-Fi**|Permite usar las capacidades de Wi-Fi del dispositivo.|No|Sí|
|**Permitir Wi-Fi Tethering**|Permite usar tethering Wi-Fi en el dispositivo.|No|Sí|
|**Permitir geolocalización**|Permite usar información de ubicación en el dispositivo.|No|Sí|
|**Permitir NFC**|Permite operaciones que usan la transmisión de datos en proximidad (si es posible en el dispositivo).|No|Sí|
|**Permitir Bluetooth**|Permite usar Bluetooth en el dispositivo.|No|Sí|
|**Permitir desconectar**|Permite al usuario desconectar el dispositivo.<br /><br />Si se deshabilita esta opción, la opción **Número de errores de inicio de sesión repetidos que se permiten antes de que se eliminen los datos del dispositivo** de los dispositivos Samsung KNOX no funciona.|No|Sí|

### Configuración de funcionalidades del dispositivo: datos móviles

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir itinerancia de voz**|Permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.|No|Sí|
|**Permitir itinerancia de datos**|Permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.|No|Sí|
|**Permitir mensajería SMS y MMS**|Permite usar mensajes SMS y MMS en el dispositivo.|No|Sí|

### Configuración de funcionalidades del dispositivo: características

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir asistente de voz**|Permite usar software de asistente de voz en el dispositivo.|No|Sí|
|**Permitir la marcación por voz**|Habilita o deshabilita la característica de marcación por voz en el dispositivo.|No|Sí|
|**Permitir copiar y pegar**|Permite copiar y pegar funciones en el dispositivo.|No|Sí|
|**Permitir el uso compartido del Portapapeles entre aplicaciones**|Use el Portapapeles para copiar y pegar entre aplicaciones.|No|Sí|
|**Permitir YouTube**|Permite usar YouTube en el dispositivo.|No|Sí|

### Configuración de aplicaciones conformes y no conformes
En la lista de **aplicaciones compatibles&amp; y no compatibles**, especifique las aplicaciones que son compatibles y no compatibles con la siguiente información:

> [!NOTE]
> Una única directiva solo puede contener una lista de aplicaciones conformes o una lista de aplicaciones no conformes. No se pueden especificar ambas en la misma directiva.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Notificar la no compatibilidad cuando los usuarios instalan las aplicaciones de la lista**|Enumera las aplicaciones que no se administran mediante Intune y que los usuarios no pueden instalar ni ejecutar.|
|**No informar de incompatibilidad cuando los usuarios instalan las aplicaciones enumeradas.**|Enumera las aplicaciones que los usuarios pueden instalar. Para mantener la conformidad, los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.|
|**Agregar**|Agrega una aplicación a la lista seleccionada. Especifique un nombre de su elección, opcionalmente el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones.<br /><br />Consulte Cómo especificar las direcciones URL de tiendas de aplicaciones más adelante en este tema para obtener más ayuda.|
|**Importar aplicaciones**|Importa la lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. Utilice el formato, nombre de la aplicación, editor, dirección URL de la aplicación en el archivo.|
|**Editar**|Permite editar el nombre, el editor y la dirección URL de la aplicación seleccionada.|
|**Eliminar**|Elimina la aplicación seleccionada de la lista.|

### Configuración del modo de pantalla completa
Especifique la siguiente configuración para los **dispositivos Samsung KNOX**:

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Seleccione una aplicación administrada que se permitirá ejecutar cuando el dispositivo esté en modo de quiosco**|Haga clic en **Examinar**, seleccione la aplicación administrada, o una aplicación de una tienda, que se permitirá ejecutar cuando el dispositivo esté en modo de pantalla completa. No se podrá ejecutar ninguna otra aplicación en el dispositivo.<br /><br />Consulte Cómo especificar las direcciones URL de tiendas de aplicaciones más adelante en este tema para obtener más ayuda.|
|**Permitir los botones de volumen**|Habilita o deshabilita el uso de los botones de volumen en el dispositivo.|
|**Permitir el botón de reactivación de suspensión de pantalla**|Habilita o deshabilita el botón de reactivación de la suspensión de pantalla en el dispositivo.|

### Información de referencia para las aplicaciones conformes y no conformes

#### Supervisar las aplicaciones conformes y no conformes
Utilice el **Informe de aplicaciones no conformes** para ver la conformidad de las aplicaciones permitidas y bloqueadas.

###### Para ejecutar el informe de aplicaciones no conformes

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), haga clic en **Informes** &gt; **Informe de aplicaciones no compatibles**..

2.  Seleccione los grupos de dispositivos que quiere comprobar, si quiere buscar las aplicaciones compatibles, las no compatibles o ambas y, después, haga clic en **Ver informe**..

#### Cómo especificar las direcciones URL de tiendas de aplicaciones
Para especificar una dirección URL de aplicación en la lista de aplicaciones conformes y no conformes o en la opción **Seleccione una aplicación administrada que se podrá ejecutar cuando el dispositivo esté en modo de pantalla completa** (solo iOS), use el siguiente formato:

En la [sección Aplicaciones de Google Play](https://play.google.com/store/apps), busque la aplicación que quiere usar.

Abra la página de instalación de la aplicación y copie la dirección URL en el Portapapeles. Ya puede utilizarla como dirección URL en una la lista de aplicaciones conformes o no conformes.

**Ejemplo:** busque Microsoft Office Mobile en Google Play. Usará la dirección URL **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**..

## Opciones de configuración de directiva personalizadas
Use la **directiva de configuración personalizada de Android** de Microsoft Intune para implementar las opciones de configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance), que sirve para controlar características en dispositivos Android. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta capacidad está pensada para que se puedan implementar las opciones de configuración de Android que no se pueden definir con directivas de Intune. Para obtener más información sobre las opciones que se pueden configurar con estas directivas, vea [Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)..

> [!NOTE]
> Actualmente, las directivas personalizadas de Android solo admiten la configuración de Wi-Fi para dispositivos Android que incluyen una clave precompartida. Para obtener más información, vea Configurar un perfil de Wi-Fi personalizado con una clave precompartida más adelante en este tema.

### Configuración general

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre**|Escriba un nombre único para la directiva personalizada de Android que permita identificarla en la consola de Intune.|
    |**Descripción**|Proporcione una descripción que ofrezca una visión general de la directiva personalizada de Android y otra información relevante que le ayude a encontrarla.|

### Configuración de OMA-URI

   |Nombre de la configuración|Detalles|
    |--------|--------------------|
    |**Nombre de la configuración**|Escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.|
    |**Descripción del valor**|Proporcione una descripción que ofrezca una visión general del valor y otra información relevante que le ayude a encontrarlo.|
    |**Tipo de datos**|Seleccione el tipo de fecha en que especificará este valor OMA-URI. Elija entre las opciones **Cadena, Cadena (XML), Fecha y hora, Entero, Punto flotante** o **Booleano**..|
    |**OMA-URI (distingue mayúsculas de minúsculas)**|Especifique el OMA-URI para el que desee suministrar un valor.|
    |**Valor**|Especifique el valor asociado con el OMA-URI especificado anteriormente.|

### Ejemplo: configurar un perfil de Wi-Fi personalizado con una clave precompartida
Aunque Intune admite perfiles de Wi-Fi para dispositivos Android, actualmente esta característica no admite la inclusión de una clave precompartida en la configuración. En este ejemplo, aprenderá a crear una directiva personalizada de Android que cree un perfil de Wi-Fi con una clave precompartida en el dispositivo Android.

#### Para crear un perfil de Wi-Fi con una clave precompartida

1.  Asegúrese de que los usuarios usen la versión más reciente de la aplicación [Portal de empresa de Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) para Android.

2.  Cree una directiva personalizada de Android y agregue los siguientes valores:

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Nombre de la configuración**|Especifique un nombre de su elección para el valor.|
|**Descripción del valor**|Especifique una descripción para el valor.|
|**Tipo de datos**|Seleccione **Cadena (XML)**..|
|**OMA-URI**|Escriba lo siguiente: ./Vendor/MSFT/WiFi/Profile/*&lt;su perfil de Wi-Fi&gt;*/Settings|

3.  Para **Valor**, copie y pegue el siguiente código XML:

    ```
    <!--
    WEP Wifi Profile
                    <Name of wifi profile> = Name of profile 
                    <SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
                    <WEP password> = Password to connect to the network
    -->
    <WLANProfile 
    xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name><Name of wifi profile></name>
      <SSIDConfig>
        <SSID>
          <name><SSID of wifi profile></name>
        </SSID>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <MSM>
        <security>
          <authEncryption>
            <authentication>open</authentication>
            <encryption>WEP</encryption>
            <useOneX>false</useOneX>
          </authEncryption>
          <sharedKey>
            <keyType>networkKey</keyType>
            <protected>false</protected>
            <keyMaterial><WEP password></keyMaterial>
          </sharedKey>
          <keyIndex>0</keyIndex>
        </security>
      </MSM>
    </WLANProfile>
    ```

4.  Cuando haya terminado, guarde la directiva e impleméntela en los dispositivos Android necesarios. El nuevo perfil de Wi-Fi aparecerá en la lista de conexiones del dispositivo.

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


