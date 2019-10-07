---
title: Configuración de dispositivo macOS en Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Agregue, configure o cree valores en dispositivos macOS para restringir características, lo que incluye establecer requisitos de contraseña, controlar la pantalla de bloqueo, usar aplicaciones integradas, agregar aplicaciones restringidas o aprobadas, controlar dispositivos Bluetooth, conectarse a la nube para realizar copias de seguridad y almacenar, habilitar la pantalla completa, agregar dominios y controlar la manera en que los usuarios interactúan con el explorador web Safari en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 675f98d952cb243b5aa43e94972b3ef42fbee463
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734822"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Configuración de dispositivos macOS para permitir o restringir características mediante Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En este artículo se enumeran y describen los diferentes valores de configuración que se pueden controlar en los dispositivos macOS. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores para habilitar o deshabilitar características, establecer reglas de contraseña, permitir o restringir determinadas aplicaciones, etc.

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos macOS.

## <a name="before-you-begin"></a>Antes de comenzar

[Crear un perfil de configuración de restricciones de dispositivos](../device-restrictions-configure.md).

> [!NOTE]
> Esta configuración se aplica a diferentes tipos de inscripción. Para obtener más información sobre los diferentes tipos de inscripción, consulte [inscripción de MacOS](../macos-enroll.md).

## <a name="general"></a>General

### <a name="settings-apply-to-device-enrollment"></a>La configuración se aplica a: inscripción de dispositivos

- **Búsqueda de definiciones**: **Bloquear** evita que el usuario resalte una palabra y luego busque su definición en el dispositivo. **No configurado** (valor predeterminado) permite el acceso a la característica de búsqueda de definiciones.
- **Dictado**: **Bloquear** evita que el usuario use la entrada de voz para escribir texto. **No configurado** (valor predeterminado) permite que el usuario use la entrada de dictado.
- **Almacenamiento en caché de contenido**: elija **Sin configurar** (valor predeterminado) para habilitar el almacenamiento en caché de contenido. El almacenamiento en caché de contenido almacena localmente en el dispositivo datos de aplicaciones, datos del explorador web, descargas y mucho más. Seleccione **Bloquear** para evitar que estos datos se almacenen en la memoria caché.

  Para más información sobre el almacenamiento en caché de contenido en macOS, vea [Gestionar el almacenamiento en caché de contenido en el Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (abre otro sitio web).

  Esta característica se aplica a:  
  - macOS 10.13 y versiones más recientes

- **Aplazar actualizaciones de software**: cuando se establece en **Sin configurar** (valor predeterminado), las actualizaciones de software se muestran en el dispositivo a medida que Apple las va publicando. Por ejemplo, si Apple publica una actualización de macOS en una fecha concreta, dicha actualización naturalmente se mostrará en el dispositivo en torno a la fecha de publicación. Se permiten las actualizaciones de compilación de inicialización sin retraso.

  **Habilitar** permite retrasar la visualización de las actualizaciones en el dispositivo, entre 0 y 90 días. Esta configuración no controla cuándo se instalan las actualizaciones. 

  - **Retrasar la visibilidad de las actualizaciones de software**: escriba un valor comprendido entre 0 y 90 días. Cuando el retraso expira, los usuarios reciben una notificación para actualizar a la versión más antigua del sistema operativo que estaba disponible cuando se desencadenó el retraso.

    Por ejemplo, si hay una actualización de macOS disponible **el 1 de enero** y **Retrasar la visibilidad** está establecido en **5 días**, la actualización no se muestra como una actualización disponible. Al **sexto día** después de la publicación, esta actualización estará disponible y los usuarios finales podrán instalarla.

    Esta característica se aplica a:  
    - macOS 10.13.4 y versiones más recientes

- **Capturas de pantallas**: el dispositivo debe inscribirse en la inscripción automática de dispositivos (DEP) de Apple. Cuando se establece en **bloquear**, los usuarios no pueden guardar una captura de pantalla de la pantalla. También evita que la aplicación Classroom Observe pantallas remotas. **No configurado** (valor predeterminado) permite a los usuarios capturar capturas de pantalla y permite que la aplicación Classroom vea pantallas remotas.

### <a name="settings-apply-to-automated-device-enrollment"></a>La configuración se aplica a: inscripción de dispositivos automatizada

- **Observación de pantalla remota a través de la aplicación Classroom**: **deshabilitar** evita que los profesores usen la aplicación Classroom para ver las pantallas de los estudiantes. **No configurado** (valor predeterminado) permite a los profesores ver las pantallas de los estudiantes.

  Para usar esta opción, establezca el valor de **capturas de pantallas** en **no configurado** (se permiten capturas de pantallas).

- **Observación de pantalla sin preguntar por aplicación de aula**: **permitir** a los profesores ver las pantallas de los estudiantes sin necesidad de que el estudiante lo acepte. **No configurado** (valor predeterminado) requiere que el estudiante acepte antes de que el profesor pueda ver las pantallas.

  Para usar esta opción, establezca el valor de **capturas de pantallas** en **no configurado** (se permiten capturas de pantallas).

- **Los estudiantes deben solicitar permiso para dejar clase Classroom**: **requerir** fuerza a los estudiantes inscritos en un curso de la sala no administrada para obtener la aprobación del profesor para salir del curso. **No configurado** (valor predeterminado) permite que el estudiante deje el curso cada vez que el estudiante decida.

- **Los profesores pueden bloquear automáticamente dispositivos o aplicaciones en la aplicación Classroom**: **permitir que** los profesores bloqueen el dispositivo o la aplicación de un estudiante sin la aprobación del estudiante. **No configurado** (valor predeterminado) requiere que el estudiante acepte antes de que el profesor pueda bloquear el dispositivo o la aplicación.

- **Los estudiantes pueden unirse automáticamente a la clase Classroom**: **Allow** permite a los estudiantes unirse a una clase sin preguntar al profesor. **No configurado** (valor predeterminado) requiere la aprobación del profesor para unirse a una clase.

## <a name="password"></a>Contraseña

### <a name="settings-apply-to-device-enrollment"></a>La configuración se aplica a: inscripción de dispositivos

- **Contraseña**: **Requerir** que el usuario final escriba una contraseña para acceder al dispositivo. **No configurado** (valor predeterminado) no requiere una contraseña. Tampoco fuerza ninguna restricción, como el bloqueo de contraseñas simples o la configuración de una longitud mínima.
  - **Tipo de contraseña necesaria**: especifique si la contraseña solo puede ser numérica o si debe ser alfanumérica (contener letras y números).

    Esta característica se aplica a:  
    - macOS 10.10.3 y versiones más recientes

  - **Número de caracteres no alfanuméricos en la contraseña**: especifique el número de caracteres complejos necesarios en la contraseña (de **0** a **4**).<br>Un carácter complejo es un símbolo, por ejemplo, "**?**".
  - **Longitud mínima de la contraseña**: escriba la longitud mínima de contraseña que un usuario debe configurar (entre **4** y **16** caracteres).
  - **Contraseñas sencillas**: permita el uso de contraseñas sencillas, como **0000** o **1234**.
  - **Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña**: especifique cuánto tiempo debe estar inactivo el equipo antes de que se requiera una contraseña para desbloquearlo.
  - **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique el período de tiempo que el equipo debe estar inactivo antes de la pantalla se bloquee.
  - **Caducidad de la contraseña (días)**: especifique cuántos días deben transcurrir antes de que el usuario tenga que cambiar la contraseña (de **1** a **255** días).
  - **Impedir la reutilización de contraseñas anteriores**: especifique el número de contraseñas de usuario usadas anteriormente que no se pueden volver a utilizar, de **1** a **24**.

- **Block User from Modifying Passcode** (Bloquear modificación del código de acceso): elija **Bloquear** para evitar que se cambie, se agregue o se quite el código de acceso. **No configurado** (valor predeterminado) permite agregar, cambiar o quitar códigos de acceso.
- **Bloquear desbloqueo con huella digital**: elija **Bloquear** para impedir el uso de la huella digital para desbloquear el dispositivo. **No configurado** (valor predeterminado) permite que el usuario desbloquee el dispositivo con la huella digital.

- **Bloquear la característica Autorrellenar contraseñas**: elija **Bloquear** para evitar el uso de la característica Autorrellenar contraseñas en macOS. Si elige **Bloquear** tendrá también este impacto:

  - No se les pide a los usuarios que usen una contraseña guardada en Safari ni en ninguna aplicación.
  - Se deshabilitan las contraseñas seguras automáticas y no se sugieren contraseñas seguras a los usuarios.

  **No configurado** (valor predeterminado) permite estas características.

- **Bloquear solicitudes de proximidad de contraseñas**: elija **Bloquear** para que el dispositivo de un usuario no solicite contraseñas de los dispositivos cercanos. **No configurado** (valor predeterminado) permite estas solicitudes de contraseña.

- **Bloquear el uso compartido de contraseñas**: **Bloquear** impide el uso compartido de contraseñas entre dispositivos mediante AirDrop. **No configurado** (valor predeterminado) permite compartir las contraseñas.

## <a name="built-in-apps"></a>Aplicaciones integradas

### <a name="settings-apply-to-device-enrollment"></a>La configuración se aplica a: inscripción de dispositivos

- **Bloquear Autorrellenar de Safari**: **Bloquear** deshabilita la característica Autorrellenar de Safari en el dispositivo. **No configurado** (valor predeterminado) permite que los usuarios cambien la configuración de Autorrellenar del explorador web.
- **Bloquear Cámara**: elija **Bloquear** para impedir el acceso a la cámara del dispositivo. **No configurado** (valor predeterminado) permite el acceso a la cámara del dispositivo.
- **Bloquear Apple Music**: **Bloquear** revierte la aplicación Música al modo clásico y deshabilita el servicio Música. **No configurado** (valor predeterminado) permite usar la aplicación Apple Music.
- **Block Spotlight Internet Search Results** (Bloquear resultados de búsqueda de Internet de Spotlight): **Bloquear** impide que Spotlight devuelva resultados de cualquier búsqueda de Internet. **No configurado** (valor predeterminado) permite que la búsqueda de Spotlight se conecte a Internet para proporcionar resultados de la búsqueda.
- **Bloquear transferencia de archivos mediante iTunes**: **Bloquear** deshabilita los servicios de uso compartido de archivos de aplicaciones. **Sin configurar** (valor predeterminado) permite servicios de uso compartido de archivos de aplicaciones.

  Esta característica se aplica a:  
  - macOS 10.13 y versiones más recientes

## <a name="restricted-apps"></a>Aplicaciones restringidas

### <a name="settings-apply-to-device-enrollment"></a>La configuración se aplica a: inscripción de dispositivos

- **Tipo de lista de aplicaciones restringidas**: cree una lista de aplicaciones que los usuarios no pueden instalar ni usar. Las opciones son:

  - **No configurado** (valor predeterminado): no hay restricciones en Intune. Los usuarios tienen acceso a las aplicaciones que asigne y a las aplicaciones integradas.
  - **Aplicaciones prohibidas**: aplicaciones no administradas por Intune que no quiere que se instalen en el dispositivo. No se impide que los usuarios instalen una aplicación prohibida. Pero si un usuario instala una aplicación a partir de esta lista, se muestra en Intune.
  - **Aplicaciones aprobadas**: aplicaciones que los usuarios pueden instalar. Los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente. No se impide a los usuarios que instalen una aplicación que no se encuentra en la lista aprobada, Pero si lo hacen, se muestra en Intune.
- **Identificador de lote de aplicaciones**: escriba el [identificador de lote](bundle-ids-built-in-ios-apps.md) de aplicaciones de la aplicación que quiere. Puede mostrar u ocultar las aplicaciones integradas y las aplicaciones de línea de negocio. El sitio web de Apple tiene una lista de [aplicaciones de Apple integradas](https://support.apple.com/HT208094).
- **Nombre de la aplicación**: escriba el nombre de la aplicación que quiere. Puede mostrar u ocultar las aplicaciones integradas y las aplicaciones de línea de negocio. El sitio web de Apple tiene una lista de [aplicaciones de Apple integradas](https://support.apple.com/HT208094).
- **Publicador**: escriba el publicador de la aplicación que quiere.

Para agregar aplicaciones a estas listas, puede:

- **Agregar**: Seleccione esta aplicación para crear la lista de aplicaciones.
- **Importe** un archivo .csv con detalles sobre la aplicación, incluida la dirección URL. Use el formato `<app bundle ID>, <app name>, <app publisher>`. O bien, **exporte** para crear una lista de las aplicaciones que ha agregado en el mismo formato.

## <a name="connected-devices"></a>Dispositivos conectados

### <a name="settings-apply-to-device-enrollment"></a>La configuración se aplica a: inscripción de dispositivos

- **Bloquear AirDrop**: **Bloquear** evita el uso de AirDrop en el dispositivo. **No configurado** (valor predeterminado) permite usar la característica AirDrop para intercambiar contenido con dispositivos cercanos.
- **Block Apple Watch Auto Unlock** (Bloquear desbloqueo automático de Apple Watch): **Bloquear** impide que los usuarios desbloqueen su dispositivo macOS mediante Apple Watch. **Sin configurar** (valor predeterminado) permite a los usuarios desbloquear su dispositivo macOS mediante Apple Watch.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

### <a name="settings-apply-to-device-enrollment"></a>La configuración se aplica a: inscripción de dispositivos

- **Bloquear la sincronización de Keychain en iCloud**: elija **Bloquear** para deshabilitar la sincronización de las credenciales almacenadas en Keychain en iCloud. **No configurado** (valor predeterminado) permite que los usuarios sincronicen estas credenciales.
- **Block iCloud Document Sync** (Bloquear sincronización de documentos de iCloud): **Bloquear** impide que iCloud sincronice documentos y datos. **No configurado** (valor predeterminado) permite la sincronización de clave-valor y documentos en el espacio de almacenamiento de iCloud.
- **Block iCloud Mail Backup** (Bloquear copia de seguridad de Correo de iCloud): **Bloquear** impide que iCloud se sincronice en la aplicación Correo de macOS. **Sin configurar** (valor predeterminado) permite la sincronización de Correo en iCloud.
- **Block iCloud Contact Backup** (Bloquear copia de seguridad de Contacto de iCloud): **Bloquear** impide que iCloud sincronice los contactos de los dispositivos. **Sin configurar** (valor predeterminado) permite la sincronización de contactos con iCloud.
- **Block iCloud Calendar Backup** (Bloquear copia de seguridad de Calendario de iCloud): **Bloquear** impide que iCloud se sincronice en la aplicación Calendario de macOS. **Sin configurar** (valor predeterminado) permite la sincronización de Calendario en iCloud.
- **Block iCloud Reminder Backup** (Bloquear copia de seguridad de Recordatorios de iCloud): **Bloquear** impide que iCloud se sincronice en la aplicación Recordatorios de macOS. **Sin configurar** (valor predeterminado) permite la sincronización de Recordatorios en iCloud.
- **Block iCloud Bookmark Backup** (Bloquear copia de seguridad de marcadores de iCloud): **Bloquear** impide que iCloud sincronice Marcadores de los dispositivos. **Sin configurar** (valor predeterminado) permite la sincronización de Marcadores en iCloud.
- **Block iCloud Notes Backup** (Bloquear copia de seguridad de Notas de iCloud): **Bloquear** impide que iCloud sincronice Notas de los dispositivos. **Sin configurar** (valor predeterminado) permite la sincronización de Notas en iCloud.
- **Bloquear la biblioteca de fotografías de icloud**: **bloquear** deshabilita la biblioteca de fotos de iCloud y evita que iCloud Sincronice las fotos de los dispositivos. Las fotos que no se hayan descargado de la Fototeca de iCloud se quitarán del almacenamiento local del dispositivo. **No configurado** (valor predeterminado) permite sincronizar fotos entre el dispositivo y la biblioteca de fotografías de iCloud.
- **Entrega**: **no configurado** (valor predeterminado) permite a los usuarios iniciar el trabajo en un dispositivo MacOS y, a continuación, continuar el trabajo que han iniciado en otro dispositivo iOS o MacOS. **Bloquear** impide la característica de entrega en el dispositivo. 

  Esta característica se aplica a:  
  - macOS 10.15 y versiones más recientes

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment"></a>La configuración se aplica a: inscripción de dispositivos

- **Dirección URL de dominio de correo electrónico**: **agregue** una o varias direcciones URL a la lista. Cuando los usuarios reciben un correo electrónico de un dominio distinto del que ha configurado, este se marca como correo electrónico de no confianza en la aplicación Mail de macOS.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](../device-profile-assign.md) y [supervise el estado](../device-profile-monitor.md).

También puede restringir la configuración y las características en dispositivos [iOS](../device-restrictions-ios.md).
