---
title: 'Configuración de restricciones de dispositivos para Android en Microsoft Intune: Azure | Microsoft Docs'
description: Vea una lista de todas las configuraciones de dispositivos Android que puede controlar y restringir en Microsoft Intune. Use estos valores para controlar la contraseña, acceder a Google Play, permitir o prohibir aplicaciones, controlar la configuración del explorador, bloquear aplicaciones, hacer una copia de seguridad en la nube de Google y controlar las opciones de conexión de Bluetooth, Wi-Fi, itinerancia de datos, voz y mensaje.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: f546fc66f7c602705289493eb2f5c96555ab7603
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728946"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Listas de configuraciones de restricciones de dispositivos Android y Samsung Knox en Intune

En este artículo, se muestran todas las opciones de configuración de restricciones de dispositivos de Microsoft Intune que puede configurar para los dispositivos que ejecutan Android.

>[!TIP]
>Si la configuración que quiere no está disponible, es posible que pueda configurar sus dispositivos con un [perfil personalizado](custom-settings-android.md).

## <a name="general"></a>General

- **Cámara**: elija **Bloquear** para impedir el acceso a la cámara. **No configurado** permite el acceso a la cámara del dispositivo.
- **Copiar y pegar (solo Samsung Knox)**: elija **Bloquear** para impedir la característica Copiar y pegar. **No configurado** permite las funciones de copiar y pegar en el dispositivo.
- **Uso compartido del Portapapeles entre aplicaciones (solo Samsung Knox)**: elija**Bloquear** para impedir el uso del Portapapeles para copiar y pegar entre aplicaciones. **No configurado** permite usar el Portapapeles para copiar y pegar entre aplicaciones.
- **Envío de datos de diagnóstico (solo Samsung Knox)**: elija **Bloquear** para impedir que el usuario envíe datos de diagnóstico desde el dispositivo. **No configurado** permite que el usuario envíe los datos.
- **Borrado (solo Samsung Knox)**: permite que el usuario ejecute una acción de [borrado](devices-wipe.md) en el dispositivo.
- **Geolocalización (solo Samsung Knox)**: elija **Bloquear** para impedir que el dispositivo use información de ubicación. **No configurado** permite que el dispositivo use la información de ubicación.
- **Desconectar (solo Samsung Knox)**: elija **Bloquear** para impedir que el usuario desconecte el dispositivo. Si esta opción está deshabilitada, la configuración **Número de errores de inicio de sesión antes de borrar el dispositivo** no se puede establecer ni tampoco funciona. **No configurado** permite que el usuario desconecte el dispositivo.
- **Captura de pantalla (solo Samsung Knox)**: elija **Bloquear** para impedir las capturas de pantalla. **No configurado** permite que el usuario capture el contenido de la pantalla como imagen.
- **Asistente de voz (solo Samsung Knox)**: elija **Bloquear** para deshabilitar el servicio S Voice. **No configurado** permite usar el servicio y la aplicación S Voice en el dispositivo. Esta configuración no se aplica a Bixby ni al asistente de voz de accesibilidad que lee el contenido de la pantalla en voz alta.
- **YouTube (solo Samsung Knox)**: elija **Bloquear** para impedir que los usuarios utilicen la aplicación de YouTube. **No configurado** permite usar la aplicación de YouTube en el dispositivo.
- **Dispositivos compartidos (solo Samsung Knox)**: configure un dispositivo Samsung Knox Standard administrado como compartido. Si se establece en **Permitir**, los usuarios finales pueden iniciar y cerrar sesión en el dispositivo con sus credenciales de Azure AD. El dispositivo permanece administrado tanto si se usa como si no.</br>Cuando se usa con un perfil de certificado SCEP, esta característica permite que los usuarios finales compartan un dispositivo con las mismas aplicaciones para todos los usuarios. Sin embargo, cada usuario tiene su propio certificado de usuario SCEP. Cuando los usuarios cierran sesión, se borran todos los datos de la aplicación. Esta característica se limita a las aplicaciones LOB. </br>**No configurado** impide que varios usuarios finales inicien sesión en la aplicación Portal de empresa en el dispositivo con sus credenciales de Azure AD.
- **Bloquear los cambios de fecha y hora (Samsung Knox)**: elija **Bloquear** para impedir que el usuario cambie la configuración de fecha y hora del dispositivo. **No configurado** permite que los usuarios cambien la configuración de fecha y hora.

## <a name="password"></a>Contraseña

- **Contraseña**: **Requerir** que el usuario final escriba una contraseña para acceder al dispositivo. **No configurado** permite que los usuarios accedan al dispositivo sin tener que escribir una contraseña.

    > [!NOTE]
    > Los dispositivos Samsung Knox requieren automáticamente un PIN de 4 dígitos durante la inscripción de MDM. Es posible que los dispositivos nativos de Android requieran automáticamente un PIN para ser compatibles con el acceso condicional.

- **Longitud mínima de contraseña**: escriba la longitud mínima de contraseña que debe escribir un usuario (entre 4 y 16 caracteres).
- **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: escriba el número máximo de minutos de inactividad que se permiten en el dispositivo hasta que se bloquea la pantalla. En un dispositivo, un usuario final no puede establecer un valor de tiempo mayor que el tiempo configurado en el perfil. Un usuario final puede establecer un valor de tiempo menor. Por ejemplo, si el perfil está establecido en 15 minutos, un usuario final puede establecer el valor en 5 minutos. Un usuario final no puede establecer el valor en 30 minutos. 
- **Número de errores de inicio de sesión antes de borrar el dispositivo**: escriba el número de errores de inicio de sesión que se permiten antes de que se borre el dispositivo.
- **Caducidad de la contraseña (días)**: escriba el número de días antes de que se deba cambiar la contraseña del dispositivo.
- **Tipo de contraseña necesaria**: escriba el nivel requerido de complejidad de la contraseña y si se pueden usar dispositivos biométricos. Las opciones son:
  - **Valor predeterminado de dispositivo**
  - **Biométrico de seguridad baja**
  - **Al menos numérica**
  - **Complejo numérico**: no se permiten números repetidos ni consecutivos, como "1111" o "1234".<sup>1</sup>
  - **Al menos alfabética**
  - **Al menos alfanumérica**
  - **Al menos alfanumérica con símbolos**
- **Impedir la reutilización de contraseñas anteriores**: impide que el usuario final cree una contraseña que ha usado anteriormente.
- **Desbloqueo con huella digital (solo Samsung Knox)**: elija **Bloquear** para impedir el uso de la huella digital para desbloquear el dispositivo. **No configurado** permite que el usuario desbloquee el dispositivo con la huella digital.
- **Smart Lock y otros agentes de confianza**: elija **Bloquear** para impedir que Smart Lock u otros agentes de confianza ajusten la configuración de la pantalla de bloqueo (Samsung KNOX Standard 5.0 y versiones posteriores). Esta característica del teléfono, conocida a veces como agente de confianza, permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si el dispositivo está en una ubicación de confianza. Por ejemplo, esta característica se puede usar cuando el dispositivo está conectado a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC. Puede usar esta opción para impedir que los usuarios configuren Smart Lock.
- **Cifrado**: elija **Requerir** para que se cifren los archivos del dispositivo. No todos los dispositivos admiten el cifrado. Para usar esta característica, también: 
  1. Establezca **Contraseña** en **Requerir**.
  2. Establezca **Tipo de contraseña requerida** en **Al menos numérica**.
  3. Establezca **Longitud mínima de la contraseña** en al menos 4 para que esta configuración cumpla correctamente con los requisitos.

  > [!NOTE]
  > Si se aplica una directiva de cifrado, los dispositivos Samsung Knox requieren que los usuarios establezcan una contraseña compleja de 6 caracteres como el código de acceso del dispositivo.

<sup>1</sup> Antes de asignar esta configuración a los dispositivos, asegúrese de actualizar la aplicación Portal de empresa a la versión más reciente en esos dispositivos.

Si establece **Tipo de contraseña requerida** en **Numérica compleja** y luego lo asigna a un dispositivo que ejecuta una versión de Android anterior a la versión 5.0, se aplica el comportamiento siguiente:

- Si la aplicación de Portal de empresa se ejecuta en una versión anterior a 1704, no se aplica ninguna directiva de PIN al dispositivo y se muestra un error en Azure Portal.
- Si la aplicación del Portal de empresa ejecuta la versión 1704 o una versión posterior, solo se puede aplicar un PIN sencillo. Las versiones de Android anteriores a 5.0 no admiten esta configuración. No se muestra ningún error en Azure Portal.

## <a name="google-play-store"></a>Google Play Store

- **Google Play Store (solo Samsung Knox)**: elija **Bloquear** para impedir que los usuarios usen Google Play Store. **No configurado** permite que el usuario acceda a Google Play Store en el dispositivo.

## <a name="restricted-apps"></a>Aplicaciones restringidas

Use esta configuración para permitir o impedir aplicaciones específicas en el dispositivo. Esta característica es compatible con dispositivos Android y Samsung Knox Standard:

- **Aplicaciones prohibidas**: lista de aplicaciones no administradas por Intune que no quiere que se instalen en el dispositivo. Si un usuario instala una aplicación de esta lista, recibirá una notificación a través de Intune.
- **Aplicaciones aprobadas**: lista de aplicaciones que los usuarios pueden instalar. Para mantener el cumplimiento, los usuarios no deben instalar otras aplicaciones. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.

Para agregar una aplicación a estas listas, puede:

- **Agregar** la dirección URL de Google Play Store de la aplicación que quiere. Por ejemplo, para agregar la aplicación Escritorio remoto de Microsoft para Android, escriba `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android`. Para buscar la dirección URL	 de una aplicación, abra [Google Play Store](https://play.google.com/store/apps) y busque la aplicación. Por ejemplo, busque `Microsoft Remote Desktop Play Store` o `Microsoft Planner`. Seleccione la aplicación y copie la dirección URL.
- Importe un archivo .csv con detalles sobre la aplicación, incluida la dirección URL. Use el formato <*dirección URL de la aplicación*>, <*nombre de la aplicación*>, <*editor de la aplicación*>. O bien **exporte** una lista existente que incluye la lista de aplicaciones restringidas en el mismo formato.

> [!IMPORTANT]
> Se deben asignar perfiles de dispositivo que usen configuración de aplicaciones restringidas para grupos de usuarios.

## <a name="browser"></a>Explorador

- **Explorador web (solo Samsung Knox)**: elija **Bloquear** para impedir que se use el explorador web predeterminado en el dispositivo. **No configurado** permite que se use el explorador web predeterminado del dispositivo.
- **Autorrellenar (solo Samsung Knox)**: elija **Bloquear** para evitar autorrellenar el texto en el explorador. **No configurado** permite usar la función Autorrellenar del explorador web.
- **Cookies (solo Samsung Knox)**: elija cómo quiere administrar las cookies de los sitios web en el dispositivo. Las opciones son:
  - Permitir
  - Bloquear todas las cookies
  - Permitir cookies de sitios web visitados
  - Permitir cookies del sitio web actual
- **Javascript (solo Samsung Knox)**: elija **Bloquear** para impedir que el explorador web ejecute scripts de Java. **No configurado** permite que el explorador web del dispositivo ejecute scripts de Java.
- **Elementos emergentes (solo Samsung Knox)**: elija**Bloquear** para impedir los elementos emergentes en el explorador web. **No configurado** permite los elementos emergentes en el explorador web.

## <a name="allow-or-block-apps"></a>Permiso o bloqueo para aplicaciones

Use esta configuración para permitir, bloquear u ocultar aplicaciones específicas en dispositivos Samsung Knox Standard. El usuario no puede abrir ni ejecutar las aplicaciones ocultas.

Las opciones son:

- **Aplicaciones cuya instalación se permite (solo Samsung Knox Standard)**
- **Aplicaciones cuyo inicio está bloqueado (solo Samsung Knox Standard)**
- **Aplicaciones ocultas para el usuario (solo Samsung Knox Standard)**

Agregue una lista de aplicaciones para cada configuración. Las opciones son:

- **Agregar aplicaciones por nombre de paquete**: se usa principalmente para aplicaciones de línea de negocio. Escriba el nombre de la aplicación y el nombre del paquete de la aplicación.
- **Agregar aplicaciones por URL**: especifique el nombre de la aplicación y su dirección URL en Google Play Store.
- **Agregar aplicación de la tienda**: seleccione una aplicación de la lista de aplicaciones existentes que administra en Intune.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

- **Copia de seguridad de Google (solo Samsung Knox)**: elija **Bloquear** para impedir que el dispositivo se sincronice con la copia de seguridad de Google. **No configurado** permite usar la copia de seguridad de Google.
- **Sincronización automática de la cuenta de Google (solo Samsung Knox)**: elija **Bloquear** para impedir la característica de sincronización automática de la cuenta de Google en el dispositivo. **No configurado** permite sincronizar automáticamente la configuración de la cuenta de Google.
- **Almacenamiento extraíble (solo Samsung Knox)**: elija **Bloquear** para impedir que el dispositivo use el almacenamiento extraíble. **No configurado** permite que el dispositivo use almacenamiento extraíble, como una tarjeta SD.
- **Cifrado en tarjetas de almacenamiento (solo Samsung Knox)**: **Requerir** exige que las tarjetas de almacenamiento estén cifradas. **No configurado** permite que se usen tarjetas de almacenamiento no cifradas. No todos los dispositivos admiten el cifrado de tarjetas de almacenamiento. Para confirmar, consulte con el fabricante del dispositivo.

## <a name="cellular-and-connectivity"></a>Red de telefonía móvil y conectividad

- **Itinerancia de datos (solo Samsung Knox)**: elija **Bloquear** para evitar la itinerancia de datos a través de la red de telefonía móvil. **No configurado** permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.
- **Mensajería SMS y MMS (solo Samsung Knox)**: elija **Bloquear** para impedir la mensajería de texto en el dispositivo. **No configurado** permite usar la mensajería SMS y MMS en el dispositivo.
- **Marcación por voz (solo Samsung Knox)**: elija **Bloquear** para impedir que los usuarios usen la característica de marcación por voz en el dispositivo. **No configurado** permite la marcación por voz en el dispositivo.
- **Itinerancia de voz (solo Samsung Knox)**: elija **Bloquear** para evitar la itinerancia de voz a través de la red de telefonía móvil. **No configurado** permite la itinerancia de voz cuando el dispositivo está en una red de telefonía móvil.
- **Bluetooth (solo Samsung Knox)**: elija **Bloquear** para impedir el uso de Bluetooth en el dispositivo. **No configurado** permite usar Bluetooth en el dispositivo.
- **NFC (solo Samsung Knox)**: elija **Bloquear** para detener la tecnología Transmisión de datos en proximidad (NFC). **No configurado** permite operaciones que usan la transmisión de datos en proximidad en dispositivos compatibles.
- **Wi-Fi (solo Samsung Knox)**: elija **Bloquear** para impedir el uso de Wi-Fi en el dispositivo. **No configurado** permite usar las características de Wi-Fi del dispositivo.
- **Tethering Wi-Fi (solo Samsung Knox)**: elija **Bloquear** para impedir el uso de tethering Wi-Fi en el dispositivo. **No configurado** permite usar tethering Wi-Fi en el dispositivo.

## <a name="kiosk"></a>Pantalla completa

La configuración de pantalla completa solo se aplica a dispositivos Samsung Knox Standard y exclusivamente a las aplicaciones que administra mediante Intune.

- Agregue las aplicaciones que quiere ejecutar cuando el dispositivo está en pantalla completa. En pantalla completa, solo se ejecutan las aplicaciones que se agregan; las que no se agregan no se ejecutan. Los exploradores instalados previamente no se ejecutan como aplicación cuando el dispositivo está en modo de pantalla completa. Si se necesita un explorador, puede utilizar [Managed Browser](app-configuration-managed-browser.md).

  Las opciones de la aplicación:

  - **Agregar aplicaciones por nombre de paquete**: se usa principalmente para aplicaciones de línea de negocio. Escriba el nombre de la aplicación y el nombre del paquete de la aplicación.
  - **Agregar aplicaciones por URL**: especifique el nombre de la aplicación y su dirección URL en Google Play Store.
  - **Agregar aplicación de la tienda**: seleccione una aplicación de la lista de aplicaciones existentes que administra en Intune.

- **Botón de suspensión de pantalla**: elija **Bloquear** para impedir u ocultar el botón de suspensión de pantalla. **No configurado** permite el botón de reactivación de suspensión de pantalla en el dispositivo.
- **Botones de volumen**: elija **Bloquear** para impedir que el usuario ajuste el volumen al deshabilitar los botones de volumen. **No configurado** permite usar los botones de volumen del dispositivo.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede crear perfiles de pantalla completa para dispositivos [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings) y [Windows 10](kiosk-settings.md).