---
title: "Configuración de restricciones de dispositivo de Intune para Android"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: conozca los valores de configuración de Intune que puede usar para controlar la configuración y la funcionalidad de los dispositivos Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: a9748a0ad6b9bbe10e36ba133ba74edb6aa6e09a
ms.openlocfilehash: 0c3a5ef16da3e2c395cb71a0fc8a23d531cfa02c
ms.contentlocale: es-es
ms.lasthandoff: 05/05/2017


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos Android y Samsung KNOX en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>General

|||||
|-|-|-|-|
|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX Standard|
|**Cámara**|Permite el uso de la cámara del dispositivo.|Sí|Sí|
|**Copiar y pegar**|Permite copiar y pegar funciones en el dispositivo.|No|Sí|
|**Uso compartido del Portapapeles entre aplicaciones**|Permite usar el Portapapeles para copiar y pegar entre aplicaciones.|No|Sí|
|**Envío de datos de diagnóstico**|Impide que el usuario envíe datos de diagnóstico desde el dispositivo.|No|Sí|
|**Restablecimiento de la configuración de fábrica**|Permite que el usuario realice un restablecimiento de la configuración de fábrica en el dispositivo.|No|Sí|
|**Geolocalización**|Permite que el dispositivo use información de ubicación (solo Samsung KNOX Standard).|No|Sí|
|**Desconectar**|Permite al usuario desconectar el dispositivo.<br>Si se deshabilita esta opción, la opción **Número de errores de inicio de sesión antes de borrar el dispositivo** de los dispositivos Samsung KNOX Standard no funciona.|No|Sí|
|**Captura de pantalla**|Permite al usuario capturar el contenido en pantalla como una imagen.|No|Sí|
|**Asistente de voz**|Permite usar software de asistente de voz en el dispositivo.|No|Sí|
|**YouTube**|Permite el uso de la aplicación de YouTube en el dispositivo.|No|Sí|
|**Dispositivos compartidos**|Configure un dispositivo Samsung KNOX Standard como compartido. De este modo, los usuarios finales puede iniciar y cerrar sesión del dispositivo con sus credenciales de Azure AD, y el dispositivo se administra de forma central tanto si está en uso como si no.<br>Cuando los usuarios finales inician sesión, tienen acceso a aplicaciones, además de las directivas aplicadas a ellas. Cuando los usuarios cierran sesión, se borran todos los datos de la aplicación.|No|Sí|

## <a name="password"></a>Contraseña

|||||
|-|-|-|-|
|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX Standard|
|**Contraseña**|Exige que el usuario final escriba una contraseña para acceder al dispositivo.|Sí|Sí|
|**Longitud mínima de contraseña**|Escriba la longitud mínima de contraseña que un usuario debe configurar (entre 4 y 16 caracteres).|Sí|Sí|
|**Máximo de minutos de inactividad hasta que se bloquea la pantalla**|Especifica el número de minutos de inactividad antes de que el dispositivo se bloquee automáticamente.|Sí|Sí|
|**Número de errores de inicio de sesión antes de borrar el dispositivo**|Especifica el número de errores de inicio de sesión que se permite antes de que se borre el dispositivo.|Sí|Sí|
|**Expiración de contraseña (días)**|Especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.|Sí|Sí|
|**Tipo de contraseña obligatoria**|Especifica el nivel requerido de complejidad de la contraseña y si se pueden usar dispositivos biométricos. Elija de entre las siguientes opciones:<br><br>    -     **Valor predeterminado de dispositivo**<br>-     **Biométrica de seguridad baja**<br>    -     **Al menos numérica**<br>    -     **Complejo numérico** (no se permiten números consecutivos o de repetición, como "1111" o "1234")<sup>1</sup><br>    -     **Al menos alfabética**<br>    -     **Al menos alfanumérica**<br>    -     **Al menos alfanumérica con símbolos**|Sí|Sí|
|**Impedir la reutilización de contraseñas anteriores**|Impide que el usuario final cree una contraseña que ha usado anteriormente.|Sí|Sí|
|**Desbloqueo con huella digital**|Permite el uso de una huella digital para desbloquear dispositivos compatibles.|No|Sí|
|**Smart Lock y otros agentes de confianza**|Le permite controlar la característica de Smart Lock en dispositivos Android compatibles (Samsung KNOX Standard 5.0 y versiones posteriores). Esta funcionalidad del teléfono, conocida también en ocasiones como agentes de confianza, le permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si el dispositivo está en una ubicación de confianza (por ejemplo, cuando se conecta a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC). Puede usar esta opción para impedir que los usuarios configuren Smart Lock.|Sí (5.0 y versiones posteriores)|No|
|**Cifrado**|Requiere el cifrado de los archivos en el dispositivo.|Sí|Sí|

<sup>1</sup>Antes de asignar esta configuración a los dispositivos, asegúrese de que la aplicación Portal de empresa se actualizó a la versión más reciente en los dispositivos de destino.

Si configura el valor de **Complejo numérico** y luego lo asigna a un dispositivo que ejecuta una versión de Android anterior a la versión 5.0, se aplica el comportamiento siguiente.
- Si la aplicación Portal de empresa se ejecuta en una versión anterior a 1704, no se aplicará ninguna directiva de PIN en el dispositivo y se mostrará un error en el portal de Intune.
- Si la aplicación Portal de empresa se actualizó a la versión 1704, solo aparecerá un PIN simple. Las versiones de Android anteriores a 5.0 no admiten esta configuración. No se muestra ningún error en el portal de Intune.


## <a name="google-play-store"></a>Google Play Store

|||||
|-|-|-|-|
|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX Standard|
|**Google Play Store**|Permite al usuario acceder a Google Play Store en el dispositivo.|No|Sí|

## <a name="restricted-apps"></a>Aplicaciones restringidas

En la lista de aplicaciones restringidas, puede configurar una de las listas siguientes:

**Aplicaciones prohibidas**: aplicaciones (no administradas por Intune) que los usuarios no pueden instalar ni ejecutar.
**Aplicaciones aprobadas**: aplicaciones que los usuarios pueden instalar. Para mantener la conformidad, los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.
Se deben asignar perfiles de dispositivo que contengan configuración de aplicaciones restringidas para grupos de usuarios.

Para configurar la lista, haga clic en **Agregar** y especifique un nombre de su elección. Opcionalmente, puede indicar el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Especificación de la dirección URL para una aplicación de la tienda

Para especificar una dirección URL de la aplicación en la lista de aplicaciones compatibles y no compatibles, realice los siguientes pasos:

En la [sección Aplicaciones de Google Play](https://play.google.com/store/apps), busque la aplicación que quiere usar.

Abra la página de instalación de la aplicación y, a continuación, copie la dirección URL en el Portapapeles. Ya puede utilizarla como dirección URL en una la lista de aplicaciones conformes o no conformes.

Ejemplo: Busque Microsoft Office Mobile en Google Play. Usará la dirección URL **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

### <a name="additional-options"></a>Opciones adicionales

También puede hacer clic en **Importar** para rellenar la lista a partir de un archivo csv con el formato <*url de aplicación*>, <*nombre de aplicación*>, <*editor de aplicación*> o en **Exportar** para crear un archivo csv que contenga la lista de aplicaciones restringidas en el mismo formato.        

## <a name="browser"></a>Explorador
|||||
|-|-|-|-|
|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX Standard|
|**Explorador web**|Especifica si se puede usar el explorador web predeterminado del dispositivo.|No|Sí|
|**Autorrellenar**|Permite usar la función Autorrellenar del explorador web.|No|Sí|
|**Cookies**|Permite que el explorador web del dispositivo use cookies.|No|Sí|
|**Javascript**|Permite que el explorador web del dispositivo ejecute scripts de Java.|No|Sí|
|**Elementos emergentes**|Permite usar el bloqueador de elementos emergentes en el explorador web.|No|Sí|

## <a name="cloud-and-storage"></a>Nube y almacenamiento
|||||
|-|-|-|-|
|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX Standard|
|**Copia de seguridad de Google**|Permite el uso de la copia de seguridad de Google.|No|Sí|
|**Sincronización automática de la cuenta de Google**|Permite que la configuración de la cuenta de Google se sincronice automáticamente.|No|Sí|
|**Almacenamiento extraíble**|Permite usar un almacenamiento extraíble (como una tarjeta SD) en el dispositivo.|No|Sí|
|**Cifrado en tarjetas de almacenamiento**|Especifica si se debe cifrar la tarjeta de almacenamiento del dispositivo.|No|Sí|

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad
|||||
|-|-|-|-|
|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX Standard|
|**Itinerancia de datos**|Permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.|No|Sí|
|**Mensajería SMS y MMS**|Permite usar mensajes SMS y MMS en el dispositivo.|No|Sí|
|**Marcación por voz**|Habilita o deshabilita la característica de marcación por voz en el dispositivo.|No|Sí|
|**Itinerancia de voz**|Permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.|No|Sí|
|**Bluetooth**|Permite usar Bluetooth en el dispositivo.|No|Sí|
|**NFC**|Permite operaciones que usan la transmisión de datos en proximidad (si es posible en el dispositivo).|No|Sí|
|**Wi-Fi**|Permite usar las capacidades de Wi-Fi del dispositivo.|No|Sí|
|**Tethering Wi-Fi**|Permite usar tethering Wi-Fi en el dispositivo.|No|Sí|

## <a name="kiosk"></a>Pantalla completa
|||||
|-|-|-|-|
|Nombre de la configuración|Detalles|Android 4.0+|Samsung KNOX Standard|
|**Seleccionar una aplicación administrada**|Elija Examinar y seleccione una aplicación administrada que se pueda ejecutar cuando el dispositivo esté en pantalla completa (actualmente no se admiten aplicaciones especificadas como vínculo a la tienda). No se podrá ejecutar ninguna otra aplicación en el dispositivo.|No|Sí|
|**Botón de suspensión de pantalla**|Habilita o deshabilita el botón de reactivación de la suspensión de pantalla en el dispositivo.|No|Sí|
|**Botones de volumen**|Habilita o deshabilita el uso de los botones de volumen en el dispositivo.|No|Sí|

