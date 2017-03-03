---
title: "Configuración de restricciones de dispositivos de Intune para Android | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: conozca los valores de configuración de Intune que puede usar para controlar la configuración y la funcionalidad de los dispositivos Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: a003b2b16e05c2d071bb7dbaaf564e24d0cf5823
ms.lasthandoff: 02/16/2017


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos Android y Samsung KNOX en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>General
-     **Cámara**: permite el uso de la cámara del dispositivo.
-     **Copiar y pegar**: permite funciones de copiar y pegar en el dispositivo.
-     **Uso compartido del Portapapeles entre aplicaciones**: permite el uso del Portapapeles para copiar y pegar entre aplicaciones (solo Samsung KNOX Standard).
-     **Envío de datos de diagnóstico**: impide que el usuario envíe datos de diagnóstico desde el dispositivo.    
-     **Restablecimiento de fábrica**: permite que el usuario realice un restablecimiento de la configuración de fábrica en el dispositivo.
-     **Geolocation** (Geolocalización): permite que el dispositivo use información de ubicación (solo Samsung KNOX Standard).
-     **Power off** (Desconectar): permite que el usuario desconecte el dispositivo.<br>Si se deshabilita esta opción, la opción **Número de errores de inicio de sesión antes de borrar el dispositivo** de los dispositivos Samsung KNOX Standard no funciona.
-     **Captura de pantalla**: permite al usuario capturar el contenido de la pantalla como una imagen.
-     **Asistente de voz**: permite el uso de software del asistente de voz en el dispositivo (solo Samsung KNOX Standard).
-     **YouTube**: permite el uso de la aplicación YouTube en el dispositivo (solo Samsung KNOX Standard).

## <a name="password"></a>Contraseña
-     **Contraseña necesaria**: exige que el usuario final escriba una contraseña para acceder al dispositivo.
-     **Longitud mínima de contraseña**: escriba la longitud mínima de contraseña que debe configurar un usuario (entre 4 y 16 caracteres).
-     **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique el número de minutos de inactividad antes de que el dispositivo se bloquee automáticamente.
-     **Número de errores de inicio de sesión antes de borrar el dispositivo**: especifica el número de errores de inicio de sesión que se permiten antes de que se borre el dispositivo.
-     **Caducidad de la contraseña (días)**: especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.
-     **Tipo de contraseña obligatoria**: especifica el nivel requerido de complejidad de la contraseña y si se pueden usar dispositivos biométricos.
-     **Impedir la reutilización de contraseñas anteriores**: impide que el usuario final cree una contraseña que ha usado anteriormente.
-     **Desbloqueo con huella digital**: permite el uso de una huella digital para desbloquear dispositivos compatibles.
-     **Smart Lock y otros agentes de confianza**: le permite controlar la característica de Smart Lock en dispositivos Android compatibles (Samsung KNOX Standard 5.0 y versiones posteriores). Esta funcionalidad del teléfono, conocida también en ocasiones como agentes de confianza, le permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si el dispositivo está en una ubicación de confianza (por ejemplo, cuando se conecta a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC). Puede usar esta opción para impedir que los usuarios configuren Smart Lock.
-     **Cifrado**: requiere el cifrado de los archivos en el dispositivo.

## <a name="google-play-store"></a>Google Play Store

-     **Google Play Store**: permite al usuario acceder a la tienda de Google Play en el dispositivo (solo Samsung KNOX Standard).

## <a name="restricted-apps"></a>Aplicaciones restringidas

En la lista de aplicaciones restringidas, puede configurar una de las listas siguientes:

**Aplicaciones prohibidas**: aplicaciones (no administradas por Intune) que los usuarios no pueden instalar ni ejecutar.
**Aplicaciones aprobadas**: aplicaciones que los usuarios pueden instalar. Para mantener la conformidad, los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.
Se deben implementar perfiles de dispositivo que contengan configuración de aplicaciones restringidas para grupos de usuarios.

Para configurar la lista, haga clic en **Agregar** y especifique un nombre de su elección. Opcionalmente, puede indicar el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Especificación de la dirección URL para una aplicación de la tienda

Para especificar una dirección URL de la aplicación en la lista de aplicaciones compatibles y no compatibles, realice los siguientes pasos:

En la [sección Aplicaciones de Google Play](https://play.google.com/store/apps), busque la aplicación que quiere usar.

Abra la página de instalación de la aplicación y, a continuación, copie la dirección URL en el Portapapeles. Ya puede utilizarla como dirección URL en una la lista de aplicaciones conformes o no conformes.

Ejemplo: Busque Microsoft Office Mobile en Google Play. Usará la dirección URL **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

### <a name="additional-options"></a>Opciones adicionales

También puede hacer clic en **Importar** para rellenar la lista a partir de un archivo csv con el formato <*url de aplicación*>, <*nombre de aplicación*>, <*editor de aplicación*> o en **Exportar** para crear un archivo csv que contenga la lista de aplicaciones restringidas en el mismo formato.        

## <a name="browser"></a>Explorador
-     **Explorador web**: especifica si se puede usar el explorador web predeterminado del dispositivo.
-     **Autofill** (Rellenar automáticamente): permite la función de relleno automático del explorador web que se va a usar.
-     **Cookies**: permite que el explorador web del dispositivo use cookies.
-     **Javascript**: permite que el explorador web del dispositivo ejecute scripts de Java.
-     **Elementos emergentes**: permite el uso del bloqueador de elementos emergentes en el explorador web.

## <a name="cloud-and-storage"></a>Nube y almacenamiento
-     **Copia de seguridad de Google**: permite el uso de la característica de copia de seguridad de Google.
-     **Sincronización automática de cuenta de Google**: permite la sincronización automática de la cuenta de Google.
-     **Almacenamiento extraíble**: permite que el dispositivo use almacenamiento extraíble, como una tarjeta SD (solo Samsung KNOX Standard).
-     **Cifrado en tarjetas de almacenamiento**: especifica si se debe cifrar la tarjeta de almacenamiento del dispositivo.

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad
-     **Itinerancia de datos**: permite la itinerancia de los datos cuando el dispositivo está en una red de telefonía móvil (solo Samsung KNOX Standard).
-     **Mensajería SMS/MMS**: permite el uso de mensajería SMS y MMS en el dispositivo (solo Samsung KNOX Standard).
-     **Marcación por voz**: habilita o deshabilita la característica de marcación por voz en el dispositivo (solo Samsung KNOX Standard).
-     **Itinerancia de voz**: permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil (solo Samsung KNOX Standard).
-     **Bluetooth**: permite el uso de Bluetooth en el dispositivo (solo Samsung KNOX Standard).
-     **NFC**: permite operaciones que usan la transmisión de datos en proximidad si el dispositivo lo admite (solo Samsung KNOX Standard).
-     **Wi-Fi**: permite el uso de las funcionalidades Wi-Fi del dispositivo (solo Samsung KNOX Standard).
-     **Tethering Wi-Fi**: permite el uso de tethering Wi-Fi en el dispositivo (solo Samsung KNOX Standard).

## <a name="kiosk"></a>Pantalla completa
-     **Seleccionar una aplicación administrada**: elija Examinar y después seleccione la aplicación administrada que se pueda ejecutar cuando el dispositivo está en pantalla completa (actualmente no se admiten aplicaciones especificadas como un vínculo a la tienda). No se podrá ejecutar ninguna otra aplicación en el dispositivo.
-     **Botón de suspensión de pantalla**: habilita o deshabilita el botón de reactivación de la suspensión de pantalla en el dispositivo.
-     **Botones de volumen**: habilita o deshabilita el uso de los botones de volumen en el dispositivo.

