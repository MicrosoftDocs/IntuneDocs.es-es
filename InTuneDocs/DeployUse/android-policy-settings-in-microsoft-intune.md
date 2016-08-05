---

title: "Configuración de directivas de Android y Samsung KNOX | Microsoft Intune"
description: "Cree directivas que controlen la configuración y las características en los dispositivos Android que administra con Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6e3e81f37e677a016ac49240cc70602a568afcd5
ms.openlocfilehash: 9385ca0e5aa9dd8fc2daf79c57b47951bcd5c0cb


---

# Configuración de directivas de Android y Samsung KNOX en Microsoft Intune

Intune proporciona una variedad de opciones generales integradas que puede configurar en los dispositivos Android. Además, puede especificar valores Open Mobile Alliance Uniform Resource Identifier (OMA-URI, identificador uniforme de recursos de Open Mobile Alliance) para crear una configuración personalizada que no esté disponible en Intune.

## Directiva de configuración general

Use la **directiva de configuración general de Android** de Intune para configurar las opciones de:

-   **Configuración de seguridad de dispositivos móviles**: Elija entre una lista de configuraciones predefinidas que permiten controlar una variedad de características y la funcionalidad en el dispositivo.

-   **Pantalla completa** (solo para dispositivos Samsung KNOX): permite bloquear un dispositivo para que solo funcionen determinadas características. Por ejemplo, puede permitir que un dispositivo ejecute solo una aplicación administrada que especifique, o puede deshabilitar los botones de volumen de un dispositivo. Esta configuración podría utilizarse para un modelo de demostración de un dispositivo o para un dispositivo que está dedicado a realizar solo una función, como un dispositivo de punto de venta.

-   **Aplicaciones compatibles y no compatibles**: Especifique una lista de las aplicaciones compatibles y no compatibles de su empresa. En los dispositivos iOS y Android, el **informe de aplicaciones no conformes** puede utilizarse para comparar la conformidad de las aplicaciones especificadas en la lista con las aplicaciones que los usuarios han instalado. En realidad no pueden impedir la instalación de la aplicación.

> [!TIP]
> Puede configurar los términos y condiciones de los usuarios para asegurarse de que saben que todas las aplicaciones de su dispositivo, incluidas las aplicaciones personales, se evaluarán y que las aplicaciones no conformes se bloquearán o se notificarán como no conformes. Los usuarios deben aceptar estos términos y condiciones para poder inscribir su dispositivo y utilizar el portal de empresa para obtener aplicaciones. Para obtener más información sobre cómo usar los términos y condiciones, vea [Configuración de la directiva de términos y condiciones en Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Si el valor que busca no aparece en este tema, puede crearlo mediante una directiva personalizada de Android que le permita usar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance) para controlar el dispositivo. Para obtener más información, vaya a [Configuración de directivas personalizadas](#custom-policy-settings).

### Configuración de contraseña

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|-|----------------|----------------|
|**Requerir una contraseña para desbloquear dispositivos móviles**|Especifica si se requiere una contraseña en dispositivos compatibles.|Sí|Sí|
|**Longitud mínima de la contraseña**|Especifica la longitud mínima de la contraseña.|Sí|Sí|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Especifica el número de errores de inicio de sesión que se permite antes de que se borre el dispositivo.|Sí|Sí|
|**Minutos de inactividad antes de que se apague la pantalla**|Especifica el número de minutos de inactividad antes de que el dispositivo se bloquee automáticamente.|Sí|Sí|
|**Caducidad de contraseña (días)**|Especifica el número de días antes de que se deba cambiar una contraseña.|Sí|Sí|
|**Recordar el historial de contraseñas**|Especifica el número de contraseñas usadas previamente que recordar.|Sí|Sí|
|**Recordar historial de contraseñas** - **Impedir la reutilización de contraseñas anteriores**|Impide la reutilización de contraseñas anteriores.|Sí|Sí|
|**Calidad de contraseña**|Especifica el nivel requerido de complejidad de la contraseña y si se pueden usar dispositivos biométricos.|Sí|Sí|
|**Permitir desbloqueo mediante huellas digitales**|Permite usar una huella digital para desbloquear el dispositivo.|No|Sí|
|**Permitir Smart Lock y otros agentes de confianza**<br>(Android 5 y versiones posteriores)|Vamos a controlar la característica Smart Lock en dispositivos Android compatibles. Esta funcionalidad del teléfono, conocida también en ocasiones como agentes de confianza, le permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si el dispositivo está en una ubicación de confianza (por ejemplo, cuando se conecta a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC). Puede usar esta opción para impedir que los usuarios configuren Smart Lock.|Sí|No|

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

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------------------|----------------|
|**Permitir copia de seguridad de Google**|Permite el uso de la copia de seguridad de Google.|No|Sí|

### Configuración de nube: cuentas y sincronización

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir la sincronización automática de la cuenta de Google**|Permite que la configuración de la cuenta de Google se sincronice automáticamente.|No|Sí|

### Configuración de la aplicación: explorador

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir explorador web**|Especifica si se puede usar el explorador web predeterminado del dispositivo.|No|Sí|
|**Permitir el autorrelleno**|Permite usar la función Autorrellenar del explorador web.|No|Sí|
|**Permitir bloqueador de elementos emergentes**|Permite usar el bloqueador de elementos emergentes en el explorador web.|No|Sí|
|**Permitir cookies**|Permite que el explorador web del dispositivo use cookies.|No|Sí|
|**Permitir Active scripting**|Permite que el explorador web del dispositivo use Active scripting.|No|Sí|

### Configuración de la aplicación: aplicaciones

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir Google Play Store**|Permite al usuario tener acceso a Google Play Store en el dispositivo.|No|Sí|

### Configuración de funcionalidades del dispositivo: hardware

|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Permitir cámara**|Permite el uso de la cámara del dispositivo.|Sí|Sí|
|**Permitir almacenamiento extraíble**|Permite usar un almacenamiento extraíble (como una tarjeta SD) en el dispositivo.|No|Sí|
|**Permitir Wi-Fi**|Permite usar las capacidades de Wi-Fi del dispositivo.|No|Sí|
|**Permitir Wi-Fi Tethering**|Permite usar tethering Wi-Fi en el dispositivo.|No|Sí|
|**Permitir geolocalización**|Permite que el dispositivo use información de ubicación.|No|Sí|
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
|**Permitir el uso compartido del Portapapeles entre aplicaciones**|Permite usar el Portapapeles para copiar y pegar entre aplicaciones.|No|Sí|
|**Permitir YouTube**|Permite usar YouTube en el dispositivo.|No|Sí|

### Configuración de aplicaciones conformes y no conformes
En la lista de **aplicaciones compatibles&amp; y no compatibles**, especifique las aplicaciones que son compatibles y no compatibles con la siguiente información:

> [!NOTE]
> Una única directiva solo puede contener una lista de aplicaciones conformes o una lista de aplicaciones no conformes. No se pueden especificar ambas en la misma directiva.

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Notificar la no compatibilidad cuando los usuarios instalan las aplicaciones de la lista**|Enumera las aplicaciones que no se administran mediante Intune y que no quiere que instalen ni ejecuten los usuarios. Si los usuarios instalan una de estas aplicaciones, aparecerá en el informe de aplicaciones no compatibles.|
|**No informar de incompatibilidad cuando los usuarios instalan las aplicaciones enumeradas.**|Enumera las aplicaciones que quiere permitir. Para mantener la conformidad, los usuarios no deben instalar ninguna aplicación que no se muestre en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.|
|**Agregar**|Agrega una aplicación a la lista seleccionada. Especifique un nombre de la aplicación, el publicador de la aplicación (opcional) y la dirección URL de la aplicación en la tienda de aplicaciones.<br /><br />Para obtener más información, vea [Especificar direcciones URL en tiendas de aplicaciones](#specify-urls-to-app-stores) después en este tema.|
|**Importar aplicaciones**|Importa la lista de las aplicaciones que ha especificado en un archivo de valores separados por comas. Utilice el formato, nombre de la aplicación, editor, dirección URL de la aplicación en el archivo.|
|**Editar**|Permite editar el nombre, el editor y la dirección URL de la aplicación seleccionada.|
|**Eliminar**|Elimina la aplicación seleccionada de la lista.|

### Configuración del modo de pantalla completa
Especifique la siguiente configuración para los **dispositivos Samsung KNOX**:

|Nombre de la configuración|Detalles|
|----------------|--------------------|
|**Seleccione una aplicación administrada que se puede ejecutar cuando el dispositivo esté en modo de quiosco**|Elija **Examinar** y después seleccione la aplicación administrada que se pueda ejecutar cuando el dispositivo está en pantalla completa (actualmente no se admiten aplicaciones especificadas como un vínculo a la tienda). No se podrá ejecutar ninguna otra aplicación en el dispositivo.|
|**Permitir los botones de volumen**|Habilita o deshabilita el uso de los botones de volumen en el dispositivo.|
|**Permitir el botón de reactivación de suspensión de pantalla**|Habilita o deshabilita el botón de reactivación de la suspensión de pantalla en el dispositivo.|

### Información de referencia para las aplicaciones conformes y no conformes

#### Supervisar las aplicaciones conformes y no conformes
Utilice el **Informe de aplicaciones no conformes** para ver la conformidad de las aplicaciones permitidas y bloqueadas.

###### Para ejecutar el informe de aplicaciones no conformes

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), elija **Informes** &gt; **Informe de aplicaciones no conformes**.

2.  Seleccione los grupos de dispositivos que desee comprobar. A continuación, elija si desea buscar aplicaciones conformes, aplicaciones no conformes o ambas. Por último, elija **Ver informe**.

#### Especificar las direcciones URL de tiendas de aplicaciones
Para especificar una dirección URL de la aplicación en la lista de aplicaciones compatibles y no compatibles, realice los siguientes pasos:

En la [sección Aplicaciones de Google Play](https://play.google.com/store/apps), busque la aplicación que quiere usar.

Abra la página de instalación de la aplicación y, a continuación, copie la dirección URL en el Portapapeles. Ya puede utilizarla como dirección URL en una la lista de aplicaciones conformes o no conformes.

Ejemplo: Busque Microsoft Office Mobile en Google Play. Usará la dirección URL **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

## Configuración de directivas personalizadas
Use la **directiva de configuración personalizada de Android** de Microsoft Intune para implementar las opciones de configuración de OMA-URI, que sirve para controlar características en dispositivos Android. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta capacidad está pensada para que se puedan implementar las opciones de configuración de Android que no se pueden definir con directivas de Intune.

> [!NOTE]
> Actualmente, las directivas personalizadas de Android solo admiten la configuración de Wi-Fi para dispositivos Android que incluyen una clave precompartida.

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
    |**Tipo de datos**|Seleccione el tipo de fecha en que especificará este valor OMA-URI. Elija entre las siguientes opciones **Cadena, Cadena (XML), Fecha y hora, Entero, Punto flotante** o **Booleano**.|
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
|**Tipo de datos**|Seleccione **Cadena (XML)**.|
|**OMA-URI**|Escriba lo siguiente: ./Vendor/MSFT/WiFi/Profile/*&lt;su perfil de Wi-Fi&gt;*/Settings|

3.  Para **Valor**, copie y pegue el siguiente código XML:

    ```
    <!--
    WEP Wifi Profile
                    <Name of wifi profile> = Name of profile
                    <SSID of wifi profile> = Plain text version of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
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



<!--HONumber=Jul16_HO4-->


