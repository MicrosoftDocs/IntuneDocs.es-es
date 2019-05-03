---
title: Configuración de dispositivo macOS en Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Agregue, configure o cree valores en dispositivos macOS para restringir características, lo que incluye establecer requisitos de contraseña, controlar la pantalla de bloqueo, usar aplicaciones integradas, agregar aplicaciones restringidas o aprobadas, controlar dispositivos Bluetooth, conectarse a la nube para realizar copias de seguridad y almacenar, habilitar la pantalla completa, agregar dominios y controlar la manera en que los usuarios interactúan con el explorador web Safari en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5feec66e791da4038bd069cdad69a7ba573f27f3
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798384"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Configuración de dispositivos macOS para permitir o restringir características mediante Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo se enumeran y describen los diferentes valores de configuración que se pueden controlar en los dispositivos macOS. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores para habilitar o deshabilitar características, establecer reglas de contraseña, permitir o restringir determinadas aplicaciones, etc.

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos macOS.

## <a name="before-you-begin"></a>Antes de comenzar

[Crear un perfil de configuración de restricciones de dispositivos](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>General

- **Block Definition Lookup** (Bloquear búsqueda de definiciones): **Bloquear** evita que el usuario resalte una palabra y luego busque su definición en el dispositivo. **No configurado** (valor predeterminado) permite el acceso a la característica de búsqueda de definiciones.
- **Bloquear dictado**: **Bloquear** evita que el usuario use la entrada de voz para escribir texto. **No configurado** (valor predeterminado) permite que el usuario use la entrada de dictado.
- **Bloquear el almacenamiento en caché contenido**: elija **no configurado** (valor predeterminado) para habilitar el almacenamiento en caché contenido. Almacenamiento en caché contenido almacena datos de la aplicación, datos del explorador web, descargas y más localmente en el dispositivo. Seleccione **bloque** para evitar que estos datos se almacenen en la memoria caché.

  Para obtener más información sobre el almacenamiento en caché contenido en macOS, consulte [administrar el almacenamiento en caché contenido en Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (abre otro sitio Web).

  Esta característica se aplica a:  
  - macOS 10.13 y versiones posteriores

- **Aplazar actualizaciones de software**: cuando se establece en **no configurado** (valor predeterminado), las actualizaciones de software se muestran en el dispositivo con Apple vaya lanzando. Por ejemplo, si obtiene publica una actualización de macOS de Apple en una fecha concreta, a continuación, esa actualización naturalmente aparecerá en el dispositivo en torno a la fecha de lanzamiento. Se permiten las actualizaciones de compilación de inicialización sin retraso.

  **Habilitar** permite retrasar cuando se muestran las actualizaciones de software en dispositivos, desde 0 a 90 días. Esta configuración no controla cuando las actualizaciones están o no están instaladas. 

  - **Retrasar la visibilidad de las actualizaciones de software**: escriba un valor comprendido entre 0 y 90 días. Cuando el retraso expira, los usuarios reciben una notificación para actualizar a la versión más antigua del sistema operativo que estaba disponible cuando se desencadenó el retraso.

    Por ejemplo, si está disponible en una actualización de macOS **el 1 de enero**, y **retrasar visibilidad** está establecido en **5 días**, a continuación, la actualización no se muestra como una actualización disponible en dispositivos. En el **sexto día** posteriores al lanzamiento, que está disponible la actualización y los usuarios finales pueden instalarlo.

    Esta característica se aplica a:  
    - macOS 10.13.4 y versiones posteriores

## <a name="password"></a>Contraseña

- **Contraseña**: **Requerir** que el usuario final escriba una contraseña para acceder al dispositivo. **No configurado** (valor predeterminado) no requiere una contraseña y no obliga a las restricciones, como bloquear contraseñas simples o establecer una longitud mínima.
  - **Tipo de contraseña necesaria**: especifique si la contraseña solo puede ser numérica o si debe ser alfanumérica (contener letras y números). Esta configuración solo es compatible con Mac OS X versión 10.10.3 y posteriores.
  - **Número de caracteres no alfanuméricos en la contraseña**: especifique el número de caracteres complejos necesarios en la contraseña (de **0** a **4**).<br>Un carácter complejo es un símbolo, por ejemplo, "**?**".
  - **Longitud mínima de la contraseña**: escriba la longitud mínima de contraseña que un usuario debe configurar (entre **4** y **16** caracteres).
  - **Contraseñas sencillas**: permita el uso de contraseñas sencillas, como **0000** o **1234**.
  - **Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña**: especifique cuánto tiempo debe estar inactivo el equipo antes de que se requiera una contraseña para desbloquearlo.
  - **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique el período de tiempo que el equipo debe estar inactivo antes de la pantalla se bloquee.
  - **Caducidad de la contraseña (días)**: especifique cuántos días deben transcurrir antes de que el usuario tenga que cambiar la contraseña (de **1** a **255** días).
  - **Impedir la reutilización de contraseñas anteriores**: especifique el número de contraseñas de usuario usadas anteriormente que no se pueden volver a utilizar, de **1** a **24**.

- **Bloquea al usuario modificar el código de acceso**: elija **bloque** para detener el código de acceso se cambie, agregado o quitado. **No configurado** (valor predeterminado) permite agregar, cambiar o quitar códigos de acceso.
- **Bloquear desbloqueo con huella digital**: elija **Bloquear** para impedir el uso de la huella digital para desbloquear el dispositivo. **No configurado** (valor predeterminado) permite que el usuario desbloquee el dispositivo con la huella digital.

- **Bloquear la característica Autorrellenar contraseñas**: elija **Bloquear** para evitar el uso de la característica Autorrellenar contraseñas en macOS. Elegir **bloque** también tiene las siguientes consecuencias:

  - No se les pide a los usuarios que usen una contraseña guardada en Safari ni en ninguna aplicación.
  - Se deshabilitan las contraseñas seguras automáticas y no se sugieren contraseñas seguras a los usuarios.

  **No configurado** (valor predeterminado) permite estas características.

- **Bloquear solicitudes de proximidad de contraseñas**: elija **Bloquear** para que el dispositivo de un usuario no solicite contraseñas de los dispositivos cercanos. **No configurado** (valor predeterminado) permite estas solicitudes de contraseña.

- **Bloquear el uso compartido de contraseñas**: **Bloquear** impide el uso compartido de contraseñas entre dispositivos mediante AirDrop. **No configurado** (valor predeterminado) permite compartir las contraseñas.

## <a name="built-in-apps"></a>Aplicaciones integradas

- **Bloquear Autorrellenar de Safari**: **Bloquear** deshabilita la característica Autorrellenar de Safari en el dispositivo. **No configurado** (valor predeterminado) permite que los usuarios cambien la configuración de Autorrellenar del explorador web.
- **Bloquear Cámara**: elija **Bloquear** para impedir el acceso a la cámara del dispositivo. **No configurado** (valor predeterminado) permite el acceso a la cámara del dispositivo.
- **Bloquear Apple Music**: **Bloquear** revierte la aplicación Música al modo clásico y deshabilita el servicio Música. **No configurado** (valor predeterminado) permite usar la aplicación Apple Music.
- **Resultados de búsqueda de Internet de Spotlight bloque**: **bloque** impide que contenido destacado de devolver los resultados de una búsqueda en Internet. **No configurado** (valor predeterminado) permite que la búsqueda de Spotlight se conecte a Internet para proporcionar resultados de la búsqueda.
- **Transferencia de archivos de bloque mediante iTunes**: **bloque** deshabilita servicios de uso compartido de archivos de aplicación. Disponible en Mac OS 10.13 y versiones posteriores. **No configurado** (valor predeterminado) permite el uso compartido de servicios de archivos de aplicación.

## <a name="restricted-apps"></a>Aplicaciones restringidas

En la lista de aplicaciones restringidas, puede configurar una de las listas siguientes:

- Una lista de **Aplicaciones prohibidas**: se enumeran las aplicaciones no administradas por Intune que los usuarios no pueden instalar ni ejecutar. No se impide que los usuarios instalar una aplicación prohibida, pero si lo hacen, se notifica al administrador.
- Una lista de **aplicaciones aprobadas**: se enumeran aplicaciones que los usuarios pueden instalar. Los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente. No se impide que los usuarios instalen una aplicación que no se encuentra en la lista aprobada. Sin embargo, si es así, se notifica al administrador.

Para configurar la lista, haga clic en **Agregar**, especifique un nombre de su elección (puede ser el publicador de la aplicación) y el identificador de paquete de la aplicación (por ejemplo *com.apple.calculator*).

## <a name="connected-devices"></a>Dispositivos conectados

- **Bloquear AirDrop**: **Bloquear** evita el uso de AirDrop en el dispositivo. **No configurado** (valor predeterminado) permite usar la característica AirDrop para intercambiar contenido con dispositivos cercanos.
- **Bloque de Apple Watch automática desbloquear**: **bloque** impide que los usuarios desbloquear su dispositivo macOS con su Apple Watch. **No configurado** (valor predeterminado) permite a los usuarios desbloquear el dispositivo macOS con su Apple Watch.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

- **Bloquear la sincronización de Keychain en iCloud**: elija **Bloquear** para deshabilitar la sincronización de las credenciales almacenadas en Keychain en iCloud. **No configurado** (valor predeterminado) permite que los usuarios sincronicen estas credenciales.
- **Bloquear la sincronización de documentos de iCloud**: **bloque** impide que la sincronización de documentos y datos iCloud. **No configurado** (valor predeterminado) permite la sincronización de clave-valor y documentos en el espacio de almacenamiento de iCloud.
- **Bloquear el correo electrónico de copia de seguridad de iCloud**: **bloque** impide que iCloud de sincronización en la aplicación de correo de macOS. **No configurado** (valor predeterminado) permite la sincronización de correo electrónico en iCloud.
- **Bloquear póngase en contacto con copia de seguridad de iCloud**: **bloque** impide que sincronice los contactos de los dispositivos de iCloud. **No configurado** (valor predeterminado) permite la sincronización de contactos con iCloud.
- **Bloquear el calendario de copia de seguridad de iCloud**: **bloque** impide que iCloud de sincronización en la aplicación de calendario de macOS. **No configurado** (valor predeterminado) permite la sincronización de calendario en iCloud.
- **Bloquear el aviso de copia de seguridad de iCloud**: **bloque** impide que iCloud de sincronización en la aplicación de avisos de macOS. **No configurado** (valor predeterminado) permite la sincronización de avisos en iCloud.
- **Bloquear la copia de seguridad de marcador de iCloud**: **bloque** impide a iCloud sincronizando los marcadores de dispositivos. **No configurado** (valor predeterminado) permite la sincronización de marcador en iCloud.
- **Bloque de notas de la copia de seguridad de iCloud**: **bloque** impide iCloud sincronice los dispositivos de notas. **No configurado** (valor predeterminado) permite la sincronización de notas en iCloud.

## <a name="domains"></a>Domains

- **Dirección URL de dominio de correo electrónico**: agregue una o varias direcciones URL a la lista. Cuando los usuarios reciben un correo electrónico de un dominio distinto del que ha configurado, este se marca como correo electrónico de no confianza en la aplicación Mail de MacOS.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).

También puede restringir la configuración y características de dispositivos en [iOS](device-restrictions-ios.md) dispositivos.
