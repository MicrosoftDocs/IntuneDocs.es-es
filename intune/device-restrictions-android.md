---
title: "Configuración de restricciones de dispositivo de Intune para Android"
titlesuffix: Azure portal
description: "Conozca la configuración de Intune que puede usar para controlar los valores de configuración y la funcionalidad de los dispositivos Android."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ffddf9e5fcdf8359c729eb048a6f8052a1b3286f
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos Android y Samsung KNOX en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use esta configuración con una directiva de restricción de dispositivos Android para configurar los dispositivos de su organización.

>[!TIP]
>Si la configuración que quiere no está disponible, es posible que pueda configurar sus dispositivos con un [perfil personalizado](custom-settings-android.md). 

## <a name="general"></a>General

- **Cámara**: permite el uso de la cámara del dispositivo.
- **Copiar y pegar (solo Samsung KNOX)**: permite funciones de copiar y pegar en el dispositivo.
- **Uso compartido del Portapapeles entre aplicaciones (solo Samsung KNOX)**: permite el uso del Portapapeles para copiar y pegar entre aplicaciones.
- **Envío de datos de diagnóstico (solo Samsung KNOX)**: impide que el usuario envíe datos de diagnóstico desde el dispositivo.
- **Restablecimiento de fábrica (solo Samsung KNOX)**: permite que el usuario realice un restablecimiento de la configuración de fábrica en el dispositivo.
- **Geolocalización (solo Samsung KNOX)**: permite que el dispositivo use información de ubicación.
- **Desconectar (solo Samsung KNOX)**: permite que el usuario desconecte el dispositivo.<br>Si se deshabilita, no se puede establecer la opción **Número de errores de inicio de sesión antes de borrar el dispositivo**.
- **Captura de pantalla (solo Samsung KNOX)**: permite al usuario capturar el contenido de la pantalla como una imagen.
- **Asistente de voz (solo Samsung KNOX)**: permite el uso de software del asistente de voz en el dispositivo.
- **YouTube (solo Samsung KNOX)**: permite el uso de la aplicación YouTube en el dispositivo.
- **Dispositivos compartidos (solo Samsung KNOX)**: configure un dispositivo Samsung KNOX Standard administrado como compartido. En este modo, los usuarios finales pueden iniciar y cerrar sesión en el dispositivo con sus credenciales de Azure AD. El dispositivo permanece administrado tanto si se usa como si no.<br>Cuando se usa junto con un perfil de certificado SCEP, esta característica permite a los usuarios finales compartir un dispositivo con el mismo conjunto de aplicaciones para todos los usuarios, pero con su propio certificado de usuario SCEP.  Cuando los usuarios cierran sesión, se borran todos los datos de la aplicación.  Esta característica se limita a las aplicaciones LOB.

## <a name="password"></a>Contraseña

- **Contraseña**: exige que el usuario final escriba una contraseña para acceder al dispositivo.|Sí|Sí|
- **Minimum password length** (Longitud mínima de contraseña): escriba la longitud mínima de contraseña que debe configurar un usuario (entre 4 y 16 caracteres).
- **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique el número de minutos de inactividad antes de que el dispositivo se bloquee automáticamente.
- **Número de errores de inicio de sesión antes de borrar el dispositivo**: especifica el número de errores de inicio de sesión que se permiten antes de que se borre el dispositivo.
- **Caducidad de la contraseña (días)**: especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.
-  **Tipo de contraseña necesaria**: especifica el nivel requerido de complejidad de la contraseña y si se pueden usar dispositivos biométricos. Elija de entre las siguientes opciones:
    - **Valor predeterminado de dispositivo**
    - **Biométrico de seguridad baja**
    - **Al menos numérica**
    - **Complejo numérico**: no se permiten números consecutivos o de repetición, como "1111" o "1234"<sup>1</sup>
    - **Al menos alfabética**
    - **Al menos alfanumérica**
    - **Al menos alfanumérica con símbolos**
- **Impedir la reutilización de contraseñas anteriores**: impide que el usuario final cree una contraseña que ha usado anteriormente.
- **Desbloqueo con huella digital (solo Samsung KNOX)**: permite el uso de una huella digital para desbloquear dispositivos compatibles.
- **Smart Lock y otros agentes de confianza**: le permite controlar la característica de Smart Lock en dispositivos Android compatibles (Samsung KNOX Standard 5.0 y versiones posteriores). Esta funcionalidad del teléfono, conocida en ocasiones como "agente de confianza", le permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si el dispositivo está en una ubicación de confianza. Por ejemplo, se puede usar cuando el dispositivo está conectado a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC. Puede usar esta opción para impedir que los usuarios configuren Smart Lock.
- **Cifrado**: requiere el cifrado de los archivos en el dispositivo.

<sup>1</sup> Antes de asignar esta configuración a los dispositivos, asegúrese de actualizar la aplicación del Portal de empresa a la versión más reciente en esos dispositivos.

Si configura el valor de **Complejo numérico** y luego lo asigna a un dispositivo que ejecuta una versión de Android anterior a la versión 5.0, se aplica el comportamiento siguiente.
- Si la aplicación de Portal de empresa se ejecuta en una versión anterior a 1704, no se aplica ninguna directiva de PIN al dispositivo y se muestra un error en Azure Portal.
- Si la aplicación del Portal de empresa ejecuta la versión 1704 o una versión posterior, solo se puede aplicar un PIN sencillo. Las versiones de Android anteriores a 5.0 no admiten esta configuración. No se muestra ningún error en Azure Portal.


## <a name="google-play-store"></a>Google Play Store

- **Google Play Store (solo Samsung KNOX)**: permite al usuario acceder a la tienda de Google Play en el dispositivo.

## <a name="restricted-apps"></a>Aplicaciones restringidas

En la lista de aplicaciones restringidas, puede configurar una de las listas siguientes para dispositivos Android y dispositivos Samsung KNOX Standard:

Lista de **Aplicaciones prohibidas**: enumera las aplicaciones (no administradas por Intune) por las que recibirá una notificación en caso de que el usuario las instale y ejecute.
**Aplicaciones aprobadas**: aplicaciones que los usuarios pueden instalar. Para mantener el cumplimiento, los usuarios no deben instalar otras aplicaciones. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.
Se deben asignar perfiles de dispositivo que contengan configuración de aplicaciones restringidas para grupos de usuarios.

Para configurar la lista, haga clic en **Agregar** y especifique un nombre de su elección. Opcionalmente, puede indicar el editor de la aplicación y la dirección URL de la aplicación en la tienda de aplicaciones.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Especificación de la dirección URL para una aplicación de la tienda

Para especificar una dirección URL de la aplicación en la lista de aplicaciones compatibles y no compatibles, realice los siguientes pasos:

En la [sección Aplicaciones de Google Play](https://play.google.com/store/apps), busque la aplicación que quiere usar.

Abra la página de instalación de la aplicación y, a continuación, copie la dirección URL en el Portapapeles. Ahora puede usar esta dirección URL en la lista de aplicaciones conformes o no conformes.

Ejemplo: Busque Microsoft Office Mobile en Google Play. Usará la dirección URL: **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

### <a name="additional-options"></a>Opciones adicionales

También puede hacer clic en **Importar** para obtener la lista de un archivo csv. Use el formato <*url de la aplicación*>, <*nombre de la aplicación*>, <*publicador de la aplicación*> o haga clic en **Exportar** en el archivo csv que contiene la lista de aplicaciones restringidas en el mismo formato.      

## <a name="browser"></a>Explorador

- **Explorador web (solo Samsung KNOX)**: especifica si se puede usar el explorador web predeterminado del dispositivo.
- **Autorrellenar (solo Samsung KNOX)**: permite la función de relleno automático del explorador web que se va a usar.
- **Cookies (solo Samsung KNOX)**: permite que el explorador web del dispositivo use cookies.
- **Javascript (solo Samsung KNOX)**: permite que el explorador web del dispositivo ejecute scripts de Java.
- **Elementos emergentes (solo Samsung KNOX)**: permite el uso del bloqueador de elementos emergentes en el explorador web.

## <a name="allow-or-block-apps"></a>Permiso o bloqueo para aplicaciones

Esta configuración puede utilizarse para especificar las aplicaciones que se pueden instalar o iniciar en dispositivos que ejecutan solo Samsung KNOX Standard.
Además, también puede especificar las aplicaciones instaladas que se ocultarán en el usuario del dispositivo. Los usuarios no pueden ejecutar estas aplicaciones.

- **Aplicaciones cuya instalación se permite (solo Samsung KNOX Standard)**
- **Aplicaciones cuyo inicio está bloqueado (solo Samsung KNOX Standard)**
- **Aplicaciones ocultas para el usuario (solo Samsung KNOX Standard)**

Para cada ajuste, configure una lista de aplicaciones con uno de los siguientes valores:

- **Agregar aplicaciones por nombre de paquete**: se usa principalmente para aplicaciones de línea de negocio. Escriba el nombre de la aplicación y el nombre del paquete de la aplicación. 
- **Agregar aplicaciones por URL**: especifique el nombre de la aplicación y su dirección URL en Google Play Store.
- **Agregar aplicaciones administradas**: en la lista de aplicaciones que administra con Intune, seleccione la aplicación que necesita.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

- **Copia de seguridad de Google (solo Samsung KNOX)**: permite el uso de la característica de copia de seguridad de Google.
- **Sincronización automática de cuenta de Google (solo Samsung KNOX)**: permite la sincronización automática de la cuenta de Google.
- **Almacenamiento extraíble (solo Samsung KNOX)**: permite que el dispositivo use almacenamiento extraíble, como una tarjeta SD.
- **Cifrado en tarjetas de almacenamiento (solo Samsung KNOX)**: especifica si se debe cifrar la tarjeta de almacenamiento del dispositivo.

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad

- **Itinerancia de datos (solo Samsung KNOX)**: permite la itinerancia de los datos cuando el dispositivo está en una red de telefonía móvil.
- **Mensajería SMS/MMS (solo Samsung KNOX)**: permite el uso de mensajería SMS y MMS en el dispositivo.
- **Marcación por voz (solo Samsung KNOX)**: habilita o deshabilita la característica de marcación por voz en el dispositivo.
- **Itinerancia de voz (solo Samsung KNOX)**: permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.
- **Bluetooth (solo Samsung KNOX)**: permite el uso de Bluetooth en el dispositivo.
- **NFC (solo Samsung KNOX)**: permite operaciones que usan la transmisión de datos en proximidad en los dispositivos admitidos.
- **Wi-Fi (solo Samsung KNOX)**: permite el uso de las funciones Wi-Fi del dispositivo.
- **Tethering Wi-Fi (solo Samsung KNOX)**: permite el uso de tethering Wi-Fi en el dispositivo.

## <a name="kiosk"></a>Pantalla completa

La configuración de pantalla completa solo se aplica a dispositivos Samsung KNOX Standard y exclusivamente a las aplicaciones que administra mediante Intune.

- **Seleccionar una aplicación administrada**: seleccione una de las siguientes opciones para agregar una o varias aplicaciones administradas que se pueden ejecutar cuando el dispositivo esté en pantalla completa. Ninguna otra aplicación puede ejecutarse en el dispositivo.
    - **Agregar aplicaciones por nombre de paquete**
    - **Agregar aplicaciones por dirección URL**
    - **Agregar aplicaciones administradas**.
- **Botón de suspensión de pantalla**: habilita o deshabilita el botón de reactivación de la suspensión de pantalla en el dispositivo.
- **Botones de volumen**: habilita o deshabilita el uso de los botones de volumen en el dispositivo.


## <a name="next-steps"></a>Pasos siguientes

Siga usando las instrucciones del artículo [Configuración de restricciones de dispositivos](device-restrictions-configure.md) para crear y, después, asignar el perfil de restricción de dispositivo.
