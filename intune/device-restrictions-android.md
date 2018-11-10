---
title: 'Configuración de restricciones de dispositivos para Android en Microsoft Intune: Azure | Microsoft Docs'
description: Vea una lista de todas las configuraciones de dispositivos Android que puede controlar y restringir en Microsoft Intune. Use estos valores para controlar la contraseña, acceder a Google Play, permitir o prohibir aplicaciones, controlar la configuración del explorador, bloquear aplicaciones, hacer una copia de seguridad en la nube de Google y controlar las opciones de conexión de Bluetooth, Wi-Fi, itinerancia de datos, voz y mensaje.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2e3b356cc7c09b00916c24340dbbe1923540889b
ms.sourcegitcommit: 1134ecd733356277b40eb1c7f2b318b36d387e00
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2018
ms.locfileid: "50915740"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings---intune"></a>Configuración de restricciones de dispositivos Android y Samsung Knox: Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo, se muestran todas las opciones de configuración de restricciones de dispositivos de Microsoft Intune que puede configurar para los dispositivos que ejecutan Android.

>[!TIP]
>Si la configuración que quiere no está disponible, es posible que pueda configurar sus dispositivos con un [perfil personalizado](custom-settings-android.md).

## <a name="general"></a>General

- **Cámara**: permite el uso de la cámara del dispositivo.
- **Copiar y pegar (solo Samsung Knox)**: permite funciones de copiar y pegar en el dispositivo.
- **Uso compartido del Portapapeles entre aplicaciones (solo Samsung Knox)**: permite el uso del Portapapeles para copiar y pegar entre aplicaciones.
- **Envío de datos de diagnóstico (solo Samsung Knox)**: impide que el usuario envíe datos de diagnóstico desde el dispositivo.
- **Borrado (solo Samsung Knox)**: permite que el usuario realice un [borrado](devices-wipe.md) en el dispositivo.
- **Geolocalización (solo Samsung Knox)**: permite que el dispositivo use información de ubicación.
- **Desconectar (solo Samsung Knox)**: permite que el usuario desconecte el dispositivo.<br>Si se deshabilita, no se puede establecer la opción **Número de errores de inicio de sesión antes de borrar el dispositivo**.
- **Captura de pantalla (solo Samsung Knox)**: permite al usuario capturar el contenido de la pantalla como una imagen.
- **Asistente de voz (solo Samsung KNOX)**: permite el uso de la aplicación y el servicio S Voice en el dispositivo. Esto no se aplica a Bixby ni al asistente de voz de accesibilidad que lee el contenido de la pantalla en voz alta.
- **YouTube (solo Samsung Knox)**: permite el uso de la aplicación YouTube en el dispositivo.
- **Dispositivos compartidos (solo Samsung Knox)**: configure un dispositivo Samsung Knox Standard administrado como compartido. En este modo, los usuarios finales pueden iniciar y cerrar sesión en el dispositivo con sus credenciales de Azure AD. El dispositivo permanece administrado tanto si se usa como si no.<br>Cuando se usa junto con un perfil de certificado SCEP, esta característica permite a los usuarios finales compartir un dispositivo con el mismo conjunto de aplicaciones para todos los usuarios, pero con su propio certificado de usuario SCEP.  Cuando los usuarios cierran sesión, se borran todos los datos de la aplicación.  Esta característica se limita a las aplicaciones LOB.
- **Bloquear los cambios de fecha y hora (Samsung Knox)**: evite que el usuario cambie la fecha y hora de configuración del dispositivo. 

## <a name="password"></a>Contraseña

- **Contraseña**: exige que el usuario final escriba una contraseña para acceder al dispositivo.|Sí|Sí|

    > [!NOTE]
    > Los dispositivos Samsung Knox requieren automáticamente un PIN de 4 dígitos durante la inscripción de MDM. Es posible que los dispositivos nativos de Android requieran automáticamente un PIN para ser compatibles con el acceso condicional.

- **Minimum password length** (Longitud mínima de contraseña): escriba la longitud mínima de contraseña que debe configurar un usuario (entre 4 y 16 caracteres).
- **Maximum minutes of inactivity until screen locks** (Máximo de minutos de inactividad hasta que se bloquea la pantalla): escriba el número máximo de minutos de inactividad que se permiten en el dispositivo hasta que se bloquea la pantalla. En un dispositivo, un usuario final no puede establecer un valor de tiempo mayor que el tiempo configurado en el perfil. Un usuario final puede establecer un valor de tiempo menor. Por ejemplo, si el perfil está establecido en 15 minutos, un usuario final puede establecer el valor en 5 minutos. Un usuario final no puede establecer el valor en 30 minutos. 
- **Número de errores de inicio de sesión antes de borrar el dispositivo**: especifica el número de errores de inicio de sesión que se permiten antes de que se borre el dispositivo.
- **Caducidad de la contraseña (días)**: especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.
-  **Tipo de contraseña necesaria**: especifica el nivel requerido de complejidad de la contraseña y si se pueden usar dispositivos biométricos. Elija de entre las siguientes opciones:
    - **Valor predeterminado del dispositivo**
    - **Biométrico de seguridad baja**
    - **Al menos numérica**
    - **Complejo numérico**: no se permiten números consecutivos ni repetidos (como "1111" o "1234").<sup>1</sup>
    - **Al menos alfabética**
    - **Al menos alfanumérica**
    - **Al menos alfanumérica con símbolos**
- **Impedir la reutilización de contraseñas anteriores**: impide que el usuario final cree una contraseña que ha usado anteriormente.
- **Desbloqueo con huella digital (solo Samsung Knox)**: permite el uso de una huella digital para desbloquear dispositivos compatibles.
- **Smart Lock y otros agentes de confianza**: le permite controlar la característica de Smart Lock en dispositivos Android compatibles (Samsung Knox Standard 5.0 y versiones posteriores). Esta funcionalidad del teléfono, conocida en ocasiones como "agente de confianza", le permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si el dispositivo está en una ubicación de confianza. Por ejemplo, se puede usar cuando el dispositivo está conectado a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC. Puede usar esta opción para impedir que los usuarios configuren Smart Lock.
- **Cifrado**: requiere el cifrado de los archivos en el dispositivo.

    > [!NOTE]
    > Si se aplica una directiva de cifrado, los dispositivos Samsung Knox requieren que los usuarios establezcan una contraseña compleja de 6 caracteres como el código de acceso del dispositivo.

<sup>1</sup> Antes de asignar esta configuración a los dispositivos, asegúrese de actualizar la aplicación del Portal de empresa a la versión más reciente en esos dispositivos.

Si configura el valor de **Complejo numérico** y luego lo asigna a un dispositivo que ejecuta una versión de Android anterior a la versión 5.0, se aplica el comportamiento siguiente.
- Si la aplicación de Portal de empresa se ejecuta en una versión anterior a 1704, no se aplica ninguna directiva de PIN al dispositivo y se muestra un error en Azure Portal.
- Si la aplicación del Portal de empresa ejecuta la versión 1704 o una versión posterior, solo se puede aplicar un PIN sencillo. Las versiones de Android anteriores a 5.0 no admiten esta configuración. No se muestra ningún error en Azure Portal.


## <a name="google-play-store"></a>Google Play Store

- **Google Play Store (solo Samsung Knox)**: permite al usuario acceder a la tienda de Google Play en el dispositivo.

## <a name="restricted-apps"></a>Aplicaciones restringidas

En la lista de aplicaciones restringidas, puede configurar una de las listas siguientes para dispositivos Android y dispositivos Samsung Knox Standard:

Lista **Aplicaciones prohibidas**: enumera las aplicaciones (no administradas por Intune) por las que recibe una notificación en caso de que los usuarios las instalen y ejecuten.
**Aplicaciones aprobadas**: aplicaciones que los usuarios pueden instalar. Para mantener el cumplimiento, los usuarios no deben instalar otras aplicaciones. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.
Se deben asignar perfiles de dispositivo que contengan configuración de aplicaciones restringidas para grupos de usuarios.

Para configurar la lista, haga clic en **Agregar** y especifique un nombre de su elección. Opcionalmente, puede indicar el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Especificación de la dirección URL para una aplicación de la tienda

Para especificar una dirección URL de la aplicación en la lista de aplicaciones compatibles y no compatibles, realice los siguientes pasos:

En la [sección Aplicaciones de Google Play](https://play.google.com/store/apps), busque la aplicación que quiere usar.

Abra la página de instalación de la aplicación y, a continuación, copie la dirección URL en el Portapapeles. Ahora puede usar esta dirección URL en la lista de aplicaciones conformes o no conformes.

Por ejemplo, busque **Microsoft Planner** en la [sección Aplicaciones de Google Play](https://play.google.com/store/apps). Use la dirección URL: **https://play.google.com/store/apps/details?id=com.microsoft.planner**.

### <a name="additional-options"></a>Opciones adicionales

También puede hacer clic en **Importar** para obtener la lista de un archivo csv. Use el formato <*url de la aplicación*>, <*nombre de la aplicación*>, <*publicador de la aplicación*> o haga clic en **Exportar** en el archivo csv que contiene la lista de aplicaciones restringidas en el mismo formato.      

## <a name="browser"></a>Explorador

- **Explorador web (solo Samsung Knox)**: especifica si se puede usar el explorador web predeterminado del dispositivo.
- **Autorrellenar (solo Samsung Knox)**: permite la función de relleno automático del explorador web que se va a usar.
- **Cookies (solo Samsung Knox)**: permite que el explorador web del dispositivo use cookies.
- **Javascript (solo Samsung Knox)**: permite que el explorador web del dispositivo ejecute scripts de Java.
- **Elementos emergentes (solo Samsung Knox)**: permite el uso del bloqueador de elementos emergentes en el explorador web.

## <a name="allow-or-block-apps"></a>Permiso o bloqueo para aplicaciones

Esta configuración puede utilizarse para especificar las aplicaciones que se pueden instalar o iniciar en dispositivos que ejecutan solo Samsung Knox Standard.
Además, también puede especificar las aplicaciones instaladas que se ocultan al usuario del dispositivo. Los usuarios no pueden ejecutar estas aplicaciones.

- **Aplicaciones cuya instalación se permite (solo Samsung Knox Standard)**
- **Aplicaciones cuyo inicio está bloqueado (solo Samsung Knox Standard)**
- **Aplicaciones ocultas para el usuario (solo Samsung Knox Standard)**

Para cada ajuste, configure una lista de aplicaciones con uno de los siguientes valores:

- **Agregar aplicaciones por nombre de paquete**: se usa principalmente para aplicaciones de línea de negocio. Escriba el nombre de la aplicación y el nombre del paquete de la aplicación.
- **Agregar aplicaciones por URL**: especifique el nombre de la aplicación y su dirección URL en Google Play Store.
- **Agregar aplicaciones administradas**: en la lista de aplicaciones que administra con Intune, seleccione la aplicación que necesita.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

- **Copia de seguridad de Google (solo Samsung Knox)**: permite el uso de la característica de copia de seguridad de Google.
- **Sincronización automática de cuenta de Google (solo Samsung Knox)**: permite la sincronización automática de la cuenta de Google.
- **Almacenamiento extraíble (solo Samsung Knox)**: permite que el dispositivo use almacenamiento extraíble, como una tarjeta SD.
- **Cifrado en tarjetas de almacenamiento (solo Samsung Knox)**: especifica si se debe cifrar la tarjeta de almacenamiento del dispositivo.

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad

- **Itinerancia de datos (solo Samsung Knox)**: permite la itinerancia de los datos cuando el dispositivo está en una red de telefonía móvil.
- **Mensajería SMS/MMS (solo Samsung Knox)**: permite el uso de mensajería SMS y MMS en el dispositivo.
- **Marcación por voz (solo Samsung Knox)**: habilita o deshabilita la característica de marcación por voz en el dispositivo.
- **Itinerancia de voz (solo Samsung Knox)**: permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.
- **Bluetooth (solo Samsung Knox)**: permite el uso de Bluetooth en el dispositivo.
- **NFC (solo Samsung Knox)**: permite operaciones que usan la transmisión de datos en proximidad en los dispositivos admitidos.
- **Wi-Fi (solo Samsung Knox)**: permite el uso de las funciones Wi-Fi del dispositivo.
- **Tethering Wi-Fi (solo Samsung Knox)**: permite el uso de tethering Wi-Fi en el dispositivo.

## <a name="kiosk"></a>Pantalla completa

La configuración de pantalla completa solo se aplica a dispositivos Samsung Knox Standard y exclusivamente a las aplicaciones que administra mediante Intune.

- **Seleccionar una aplicación administrada**: seleccione una de las siguientes opciones para agregar una o varias aplicaciones administradas que se pueden ejecutar cuando el dispositivo esté en pantalla completa. Ninguna otra aplicación puede ejecutarse en el dispositivo. Los exploradores instalados previamente no se pueden considerar aplicaciones que pueden ejecutarse mientras el dispositivo está en pantalla completa. Si se necesita un explorador, puede utilizar [Managed Browser](app-configuration-managed-browser.md).
    - **Agregar aplicaciones por nombre de paquete**
    - **Agregar aplicaciones por dirección URL**
    - **Agregar aplicaciones administradas**.
- **Botón de suspensión de pantalla**: habilita o deshabilita el botón de reactivación de la suspensión de pantalla en el dispositivo.
- **Botones de volumen**: habilita o deshabilita el uso de los botones de volumen en el dispositivo.


## <a name="next-steps"></a>Pasos siguientes

Siga usando las instrucciones del artículo [Configuración de restricciones de dispositivos](device-restrictions-configure.md) para crear y, después, asignar el perfil de restricción de dispositivo.
