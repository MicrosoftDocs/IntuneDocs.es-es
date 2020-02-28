---
title: Configuración de dispositivo macOS en Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Agregue, configure o cree valores en dispositivos macOS para restringir características, lo que incluye establecer requisitos de contraseña, controlar la pantalla de bloqueo, usar aplicaciones integradas, agregar aplicaciones restringidas o aprobadas, controlar dispositivos Bluetooth, conectarse a la nube para realizar copias de seguridad y almacenar, habilitar la pantalla completa, agregar dominios y controlar la manera en que los usuarios interactúan con el explorador web Safari en Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3d26c4c6cd05a411555f7824ad21b72431eb569c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511179"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Configuración de dispositivos macOS para permitir o restringir características mediante Intune



En este artículo se enumeran y describen los diferentes valores de configuración que se pueden controlar en los dispositivos macOS. Como parte de la solución de administración de dispositivos móviles (MDM), use estos valores para habilitar o deshabilitar características, establecer reglas de contraseña, permitir o restringir determinadas aplicaciones, etc.

Estos valores se agregan a un perfil de configuración de dispositivo en Intune y luego se asignan o implementan en los dispositivos macOS.

## <a name="before-you-begin"></a>Antes de comenzar

[Crear un perfil de configuración de restricciones de dispositivos](../device-restrictions-configure.md).

> [!NOTE]
> Esta configuración se aplica a diferentes tipos de inscripción. Para más información sobre los diferentes tipos de inscripción, consulte [Inscripción en macOS](../macos-enroll.md).

## <a name="general"></a>General

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Las opciones se aplican a: Inscripción de dispositivos e inscripción de dispositivos automatizada

- **Búsqueda de definiciones**: **Bloquear** evita que el usuario resalte una palabra y luego busque su definición en el dispositivo. **No configurado** (valor predeterminado) permite el acceso a la característica de búsqueda de definiciones.
- **Dictado**: **Bloquear** evita que el usuario use la entrada de voz para escribir texto. **No configurado** (valor predeterminado) permite que el usuario use la entrada de dictado.
- **Almacenamiento en caché de contenido**: seleccione **Sin configurar** (valor predeterminado) para habilitar el almacenamiento en caché de contenido. El almacenamiento en caché de contenido almacena localmente en el dispositivo datos de aplicaciones, datos del explorador web, descargas y mucho más. Seleccione **Bloquear** para evitar que estos datos se almacenen en la memoria caché.

  Para más información sobre el almacenamiento en caché de contenido en macOS, vea [Gestionar el almacenamiento en caché de contenido en el Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (abre otro sitio web).

  Esta característica se aplica a:  
  - macOS 10.13 y versiones más recientes

- **Aplazar las actualizaciones de software**: cuando se establece en **Sin configurar** (valor predeterminado), las actualizaciones de software se muestran en el dispositivo a medida que Apple las publica. Por ejemplo, si Apple publica una actualización de macOS en una fecha concreta, dicha actualización naturalmente se mostrará en el dispositivo en torno a la fecha de publicación. Se permiten las actualizaciones de compilación de inicialización sin retraso.

  **Habilitar** permite retrasar la visualización de las actualizaciones en el dispositivo, entre 0 y 90 días. Esta configuración no controla cuándo se instalan las actualizaciones. 

  - **Retrasar la visibilidad de las actualizaciones de software**: especifique un valor entre 0 y 90 días. Cuando el retraso expira, los usuarios reciben una notificación para actualizar a la versión más antigua del sistema operativo que estaba disponible cuando se desencadenó el retraso.

    Por ejemplo, si hay una actualización de macOS disponible **el 1 de enero** y **Retrasar la visibilidad** está establecido en **5 días**, la actualización no se muestra como una actualización disponible. Al **sexto día** después de la publicación, esta actualización estará disponible y los usuarios finales podrán instalarla.

    Esta característica se aplica a:  
    - macOS 10.13.4 y versiones más recientes

- **Capturas de pantallas**: el dispositivo debe inscribirse en la inscripción automática de dispositivos (DEP) de Apple. Cuando se establece en **Bloquear**, los usuarios no pueden guardar una captura de la pantalla. También evita que la aplicación Classroom observe pantallas remotas. **No configurado** (valor predeterminado) permite a los usuarios realizar capturas de pantalla y hace posible que la aplicación Classroom vea pantallas remotas.

### <a name="settings-apply-to-automated-device-enrollment"></a>Las opciones se aplican a: Inscripción de dispositivo automatizada

- **Observación de pantalla remota mediante la aplicación Classroom**: **Deshabilitar** evita que los profesores usen la aplicación Classroom para ver las pantallas de sus alumnos. **No configurado** (valor predeterminado) permite que los profesores vean las pantallas de sus alumnos.

  Para usar esta opción, establezca el valor **Capturas de pantallas** en **No configurado** (se permiten capturas de pantallas).

- **Observación de pantalla sin mensajes por la aplicación Classroom**: **Permitir** deja que los profesores vean las pantallas de sus alumnos sin que el alumno esté de acuerdo. **No configurado** (valor predeterminado) requiere que el alumno esté de acuerdo antes de que el profesor pueda ver las pantallas.

  Para usar esta opción, establezca el valor **Capturas de pantallas** en **No configurado** (se permiten capturas de pantallas).

- **Los alumnos deben solicitar permiso para abandonar la clase de Classroom**: **Requerir** obliga a los alumnos inscritos en un curso de Classroom sin administrar a obtener la aprobación del profesor para abandonar el curso. **No configurado** (valor predeterminado) permite que el alumno abandone el curso siempre que así lo decida.

- **Los profesores pueden bloquear automáticamente dispositivos o aplicaciones en la aplicación Classroom**: **Permitir** deja que los profesores bloqueen el dispositivo o la aplicación de un alumno sin su aprobación. **No configurado** (valor predeterminado) requiere que el alumno esté de acuerdo antes de que el profesor pueda bloquear el dispositivo o la aplicación.

- **Los alumnos pueden unirse automáticamente a la clase de Classroom**: **Permitir** deja que los alumnos se unan a una clase sin preguntar al profesor. **No configurado** (valor predeterminado) requiere la aprobación del profesor para unirse a una clase.

## <a name="password"></a>Contraseña

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Las opciones se aplican a: Inscripción de dispositivos e inscripción de dispositivos automatizada

- **Contraseña**: **Requerir** que el usuario final escriba una contraseña para acceder al dispositivo. **No configurado** (valor predeterminado) no requiere una contraseña. Tampoco obliga a ninguna restricción, como el bloqueo de contraseñas sencillas o la configuración de una longitud mínima.
  - **Tipo de contraseña requerida**: especifique si la contraseña puede ser Numérica únicamente o si debe ser Alfanumérica (contiene letras y números).

    Esta característica se aplica a:  
    - macOS 10.10.3 y versiones más recientes

  - **Número de caracteres no alfanuméricos en la contraseña**: Especificar el número de caracteres complejos que requiere la contraseña (entre **0** y **4**).<br>Un carácter complejo es un símbolo, por ejemplo, " **?** ".
  - **Longitud mínima de la contraseña**: escriba la longitud mínima de contraseña que un usuario debe configurar (entre **4** y **16** caracteres).
  - **Contraseñas sencillas**: Permitir el uso de contraseñas sencillas, como **0000** o **1234**.
  - **Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña**: Especificar el tiempo que el equipo debe estar inactivo antes de que se solicite una contraseña para desbloquearlo.
  - **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique el período de tiempo que el equipo debe estar inactivo antes de que la pantalla se bloquee.
  - **Expiración de la contraseña (días)** : Especificar cuántos días deben transcurrir para que el usuario deba cambiar la contraseña (entre **1** y **255** días).
  - **Impedir la reutilización de contraseñas anteriores**: escriba el número de contraseñas usadas previamente que no se pueden volver a usar, entre **1** y **24**.

- **Impedir al usuario modificar el código de acceso**: Elija **Bloquear** para evitar que se cambie, se agregue o se quite el código de acceso. **No configurado** (valor predeterminado) permite agregar, cambiar o quitar códigos de acceso.
- **Impedir el desbloqueo mediante huella digital**: Elija **Bloquear** para evitar el uso de la huella digital para desbloquear el dispositivo. **No configurado** (valor predeterminado) permite que el usuario desbloquee el dispositivo con la huella digital.

- **Impedir el relleno automático de contraseñas**: seleccione **Bloquear** para evitar el uso de la característica Autorrellenar contraseñas en macOS. Si elige **Bloquear** tendrá también este impacto:

  - No se les pide a los usuarios que usen una contraseña guardada en Safari ni en ninguna aplicación.
  - Se deshabilitan las contraseñas seguras automáticas y no se sugieren contraseñas seguras a los usuarios.

  **No configurado** (valor predeterminado) permite estas características.

- **Impedir las solicitudes de proximidad de contraseñas**: Elija **Bloquear** para que el dispositivo de un usuario no solicite contraseñas de los dispositivos cercanos. **No configurado** (valor predeterminado) permite estas solicitudes de contraseña.

- **Impedir el uso compartido de contraseñas**: **Bloquear** evita el uso compartido de contraseñas entre dispositivos mediante AirDrop. **No configurado** (valor predeterminado) permite compartir las contraseñas.

## <a name="built-in-apps"></a>Aplicaciones integradas

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Las opciones se aplican a: Inscripción de dispositivos e inscripción de dispositivos automatizada

- **Bloquear Autorrelleno en Safari**: **Bloquear** deshabilita la característica Autorrellenar de Safari en el dispositivo. **No configurado** (valor predeterminado) permite que los usuarios cambien la configuración de Autorrellenar del explorador web.
- **Bloquear la cámara**: elija **Bloquear** para impedir el acceso a la cámara del dispositivo. **No configurado** (valor predeterminado) permite el acceso a la cámara del dispositivo.
- **Bloquear Apple Music**: **Bloquear** revierte la aplicación Música al modo clásico y deshabilita el servicio Música. **No configurado** (valor predeterminado) permite usar la aplicación Apple Music.
- **Bloquear resultados de búsquedas de Internet de Spotlight**: **Bloquear** evita que Spotlight devuelva resultados de una búsqueda en Internet. **No configurado** (valor predeterminado) permite que la búsqueda de Spotlight se conecte a Internet para proporcionar resultados de la búsqueda.
- **Bloquear transferencia de archivos mediante iTunes**: **Bloquear** deshabilita los servicios de uso compartido de archivos de aplicaciones. **Sin configurar** (valor predeterminado) permite servicios de uso compartido de archivos de aplicaciones.

  Esta característica se aplica a:  
  - macOS 10.13 y versiones más recientes

## <a name="restricted-apps"></a>Aplicaciones restringidas

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Las opciones se aplican a: Inscripción de dispositivos e inscripción de dispositivos automatizada

- **Tipo de lista de aplicaciones restringidas**: cree una lista de aplicaciones que los usuarios no pueden instalar ni usar. Las opciones son:

  - **Sin configurar** (valor predeterminado): no hay restricciones en Intune. Los usuarios tienen acceso a las aplicaciones que asigne y a las aplicaciones integradas.
  - **Aplicaciones prohibidas**: aplicaciones no administradas por Intune que no se quieren instalar en el dispositivo. No se evita que los usuarios instalen una aplicación prohibida. Pero si un usuario instala una aplicación de esta lista, se notifica en Intune.
  - **Aplicaciones aprobadas**: aplicaciones que los usuarios pueden instalar. Los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente. No se impide a los usuarios que instalen una aplicación que no se encuentra en la lista aprobada, Pero si lo hacen, se notifica en Intune.
- **Identificador de lote de aplicaciones**: escriba el [identificador del lote](bundle-ids-built-in-ios-apps.md) de aplicaciones de la aplicación que quiere. Puede mostrar u ocultar aplicaciones integradas y aplicaciones de línea de negocio. El sitio web de Apple tiene una lista de [aplicaciones de Apple integradas](https://support.apple.com/HT208094).
- **Nombre de la aplicación**: escriba el nombre de la aplicación que quiere. Puede mostrar u ocultar aplicaciones integradas y aplicaciones de línea de negocio. El sitio web de Apple tiene una lista de [aplicaciones de Apple integradas](https://support.apple.com/HT208094).
- **Publicador**: escriba el publicador de la aplicación que quiere.

Para agregar aplicaciones a estas listas, puede:

- **Agregar**: seleccione para crear la lista de aplicaciones.
- **Importe** un archivo .csv con detalles sobre la aplicación, incluida la dirección URL. Use el formato `<app bundle ID>, <app name>, <app publisher>`. O bien, use **Exportar** para crear una lista de las aplicaciones agregadas, en el mismo formato.

## <a name="connected-devices"></a>Dispositivos conectados

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Las opciones se aplican a: Inscripción de dispositivos e inscripción de dispositivos automatizada

- **Bloquear AirDrop**: **Bloquear** evita el uso de AirDrop en el dispositivo. **No configurado** (valor predeterminado) permite usar la característica AirDrop para intercambiar contenido con dispositivos cercanos.
- **Impedir el desbloqueo automático de Apple Watch**: **Bloquear** evita que los usuarios desbloqueen su dispositivo macOS con su Apple Watch. **Sin configurar** (valor predeterminado) permite a los usuarios desbloquear su dispositivo macOS mediante Apple Watch.

## <a name="cloud-and-storage"></a>Nube y almacenamiento

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Las opciones se aplican a: Inscripción de dispositivos e inscripción de dispositivos automatizada

- **Bloquear la sincronización de Keychain en iCloud**: Elija **Bloquear** para deshabilitar la sincronización de las credenciales almacenadas en Keychain en iCloud. **No configurado** (valor predeterminado) permite que los usuarios sincronicen estas credenciales.
- **Bloquear la sincronización de documentos en iCloud**: **Bloquear** impide que iCloud sincronice documentos y datos. **No configurado** (valor predeterminado) permite la sincronización de clave-valor y documentos en el espacio de almacenamiento de iCloud.
- **Bloquear la copia de seguridad de iCloud Mail**: **Bloquear** evita que iCloud se sincronice con la aplicación de correo de macOS. **Sin configurar** (valor predeterminado) permite la sincronización de Correo en iCloud.
- **Bloquear la copia de seguridad de Contactos en iCloud**: **Bloquear** evita que iCloud sincronice los contactos de los dispositivos. **Sin configurar** (valor predeterminado) permite la sincronización de contactos con iCloud.
- **Bloquear la copia de seguridad de Calendario en iCloud**: **Bloquear** evita que iCloud se sincronice con la aplicación de calendario de macOS. **Sin configurar** (valor predeterminado) permite la sincronización de Calendario en iCloud.
- **Bloquear la copia de seguridad de Recordatorios de iCloud**: **Bloquear** evita que iCloud se sincronice con la aplicación de recordatorios de macOS. **Sin configurar** (valor predeterminado) permite la sincronización de Recordatorios en iCloud.
- **Bloquear la copia de seguridad de los marcadores en iCloud**: **Bloquear** evita que iCloud sincronice los marcadores de los dispositivos. **Sin configurar** (valor predeterminado) permite la sincronización de Marcadores en iCloud.
- **Bloquear la copia de seguridad de Notas de iCloud**: **Bloquear** evita que iCloud sincronice las notas de los dispositivos. **Sin configurar** (valor predeterminado) permite la sincronización de Notas en iCloud.
- **Bloquear la Fototeca de iCloud**: **Bloquear** deshabilita la Fototeca de iCloud y evita que iCloud sincronice las fotos de los dispositivos. Las fotos que no se hayan descargado de la Fototeca de iCloud se quitarán del almacenamiento local del dispositivo. **No configurado** (valor predeterminado) permite sincronizar fotos entre el dispositivo y la Fototeca de iCloud.
- **Handoff**: **No configurado** (valor predeterminado) permite que los usuarios comiencen a trabajar en un dispositivo macOS y, luego, seguir con el trabajo iniciado en otro dispositivo iOS/iPadOS o macOS. **Bloquear** impide la característica de entrega en el dispositivo. 

  Esta característica se aplica a:  
  - macOS 10.15 y versiones más recientes

## <a name="domains"></a>Dominios

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Las opciones se aplican a: Inscripción de dispositivos e inscripción de dispositivos automatizada

- **URL de dominio de correo electrónico**: **agregue** una o más direcciones URL a la lista. Cuando los usuarios reciben un correo electrónico de un dominio distinto del que ha configurado, este se marca como correo electrónico de no confianza en la aplicación Mail de macOS.

## <a name="next-steps"></a>Pasos siguientes

[Asigne el perfil](../device-profile-assign.md) y [supervise el estado](../device-profile-monitor.md).

También puede restringir la configuración y las características de dispositivos en dispositivos [iOS/iPadOS](../device-restrictions-ios.md).
