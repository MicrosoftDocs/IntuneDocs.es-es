---
# required metadata

title: Configuración de directivas de seguridad de dispositivos móviles en Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configuración de directivas de seguridad de dispositivos móviles en Microsoft Intune
> [!IMPORTANT]
> Microsoft Intune ofrece ahora directivas de configuración independientes para cada plataforma de dispositivo. Estas directivas contienen la configuración más actualizada que se puede usar. Se puede seguir usando la directiva de seguridad de dispositivo móvil, pues las implementaciones existentes seguirán funcionando. Sin embargo, debe planear la migración a las nuevas directivas de configuración tan pronto como sea posible, ya que la directiva de seguridad de dispositivos móviles se eliminará en el futuro.

Use las directivas de seguridad de dispositivos móviles de Intune para configurar una amplia variedad de opciones que puede implementar para los dispositivos administrados de su organización. Estas opciones de configuración se pueden usar para controlar la funcionalidad y la seguridad de los dispositivos.

Puede crear e implementar directivas de seguridad de dispositivos móviles para los siguientes tipos de dispositivo:

-   Dispositivos Windows RT 8.1 y dispositivos Windows 8.1 inscritos

-   Windows RT

-   Windows Phone 8 y Windows Phone 8.1

-   iOS

-   Android y Samsung KNOX

> [!NOTE]
> Algunas opciones no son aplicables a algunos dispositivos. Consulte la tabla siguiente para obtener una lista completa de opciones que se pueden configurar.

## Configuración de seguridad

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Requerir una contraseña para desbloquear dispositivos móviles**|No|No|Sí|Sí|Sí|
|**Tipo de contraseña obligatoria**<br /><br />(especifica el tipo de contraseña que será necesario, como solo numérica o alfanumérica).|Sí|Sí|Sí|Sí|No|
|**Tipo de contraseña requerida: número mínimo de conjuntos de caracteres**<br /><br />Hay cuatro conjuntos de caracteres: letras minúsculas, letras mayúsculas, símbolos y números. Esta configuración especifica cuántos conjuntos de caracteres diferentes deben incluirse en la contraseña. Sin embargo, para dispositivos iOS, especifica el número de caracteres de símbolos que deben incluirse en la contraseña.|Sí|Sí|Sí|Sí|No|
|**Longitud mínima de contraseña**|Sí|Sí|Sí|Sí|Sí|
|**Permitir contraseñas sencillas**<br /><br />Contraseñas sencillas serían, por ejemplo, "0000" y "1234".|No|No|Sí|Sí|No|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Sí|Sí|Sí|Sí|Sí|
|**Minutos de inactividad antes de que se apague la pantalla**<sup>1</sup>|Sí|Sí|Sí|Sí|Sí|
|**Expiración de contraseña (días)**|Sí|Sí|Sí|Sí|Sí|
|**Recordar el historial de contraseñas**|Sí|Sí|Sí|Sí|Sí|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Sí|Sí|Sí|Sí|Sí|
|**Calidad de contraseña**|No|No|No|No|Sí|
|**Permitir contraseña de imagen y PIN**|Sí|Sí|No|No|No|
|**Minutos de inactividad antes de que se pida la contraseña**|No|No|No|Sí|No|
|**Permitir desbloqueo mediante huellas digitales**|No|No|No|iOS 7 y versiones posteriores|No|
En los dispositivos iOS, cuando configura las opciones **Minutos de inactividad antes de que se apague la pantalla** y **Minutos de inactividad antes de que sea necesaria la contraseña**, estas se aplican en secuencia. Por ejemplo, si establece el valor para ambas opciones en **5** minutos, la pantalla se apagará automáticamente transcurridos 5 minutos y el dispositivo se bloqueará pasados 5 minutos más. Sin embargo, si el usuario apaga la pantalla manualmente, la segunda opción se aplica inmediatamente. En el mismo ejemplo, una vez que el usuario apague la pantalla, el dispositivo se bloqueará 5 minutos más tarde.

Si se implementa una directiva de longitud de contraseña para dispositivos que ejecutan Windows RT, los usuarios deberán restablecer su contraseña, aunque la contraseña actual cumpla los requisitos de la directiva.

## Configuración de cifrado

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Requerir cifrado en dispositivo móvil**<sup>1</sup><br /><br />Para dispositivos de Windows Phone 8, debe establecerse en **Sí**..<br /><br />Para habilitar el cifrado en dispositivos iOS, habilite la opción **Requerir una contraseña para desbloquear dispositivos móviles**..|Sí|No|Sí|No|Sí|
|**Requerir cifrado en tarjetas de almacenamiento**<br /><br />Se aplica también a dispositivos administrados por Exchange ActiveSync.|n/a|n/a|n/d (las aplicaciones y los datos asociados se cifran automáticamente)|n/a|Sí|
Información adicional para los dispositivos que ejecutan Windows 8.1

-   Para forzar el cifrado en los dispositivos que ejecutan Windows 8.1, debe instalar la [Actualización de cliente de diciembre de 2014 MDM en Windows](http://support.microsoft.com/kb/3013816) en cada dispositivo.

-   Si habilita este valor para dispositivos de Windows 8.1, todos los usuarios del dispositivo deben tener una cuenta de Microsoft.

-   Para que el cifrado funcione, el dispositivo debe cumplir los requisitos de certificación de hardware de Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) .

-   Al exigir el cifrado en un dispositivo, solo se puede acceder a la clave de recuperación desde la cuenta de Microsoft de los usuarios, a la que se accede desde su cuenta de OneDrive. No se puede recuperar esta clave en nombre de un usuario.

## Configuración de malware

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Requerir firewall de red**|Sí|No|No|No|No|
|**Habilitar SmartScreen**|Sí|No|No|No|No|

## Configuración del sistema

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Requerir actualizaciones automáticas**|Sí|No|No|No|No|
|**Requerir actualizaciones automáticas: clasificación mínima de actualizaciones para instalar automáticamente**<br /><br />Seleccione la clasificación de actualizaciones que se instalarán automáticamente:<br /><br />**Importantes**: instala todas las actualizaciones que se clasifican como importantes.<br /><br />**Recomendadas**: instala todas las actualizaciones que se clasifican como importantes o recomendadas.|Sí|No|No|No|No|
|**Permitir captura de pantalla**|No|No|Windows Phone 8.1 solo|Sí|Sí (solo Samsung KNOX)|
|**Permitir centro de control en la pantalla de bloqueo**|No|No|No|iOS 7 y versiones posteriores|No|
|**Permitir vista de notificaciones en la pantalla de bloqueo**|No|No|No|iOS 7 y versiones posteriores|No|
|**Permitir vista de hoy en la pantalla de bloqueo**|No|No|No|iOS 7 y versiones posteriores|No|
|**Control de cuentas de usuario**|Sí|No|No|No|No|
|**Permitir el envío de datos de diagnóstico**|Sí|No|Windows Phone 8.1 solo|Sí|Sí (solo Samsung KNOX)|
|**Permitir certificados TLS que no son de confianza**|No|No|No|Sí|No|
|**Permitir el software de cartera personal durante un bloqueo**|No|No|No|Sí|No|
|**Permitir el restablecimiento de la configuración de fábrica**|No|No|No|No|Sí (solo Samsung KNOX)|


## Configuración de nube: documentos y datos

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir copias de seguridad en iCloud**|No|No|No|Sí|No|
|**Permitir sincronización de documentos en iCloud**|No|No|No|Sí|No|
|**Permitir sincronización de Photo Stream en iCloud**|No|No|No|Sí|No|
|**Requerir copia de seguridad cifrada**|No|No|No|Sí|No|
|**Dirección URL de carpetas de trabajo**<br /><br />(establece la dirección URL de la carpeta de trabajo para permitir que los documentos se sincronicen en todos los dispositivos)|Sí|No|No|No|No|
|**Permitir copia de seguridad de Google**|No|No|No|No|Sí (solo Samsung KNOX)|

## Configuración de nube: cuentas y sincronización

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir cuenta de Microsoft**|No|No|Windows Phone 8.1 solo|No|No|
|**Permitir la sincronización automática de la cuenta de Google**|No|No|No|No|Sí (solo Samsung KNOX)|

## Configuración de correo electrónico

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir a los usuarios descargar datos adjuntos de correo electrónico**<sup>1</sup>|n/a|n/a|n/a|n/a|n/a|
|**Periodo de sincronización de correo electrónico** Se aplica también a dispositivos administrados por Exchange ActiveSync.|n/a|n/a|n/a|n/a|n/a|
|**Permitir que los dispositivos móviles que no son totalmente compatibles con esta configuración se sincronicen con Exchange (Exchange ActiveSync)** Se aplica también a los dispositivos administrados por Exchange ActiveSync.|n/a|n/a|n/a|n/a|n/a|
|**Hacer que la cuenta Microsoft sea opcional en la aplicación Windows Mail**|Sí|No|No|No|No|
|**Permitir cuentas de correo electrónico personalizadas**|No|No|Windows Phone 8.1 solo|No|No|

## Configuración de la aplicación: explorador

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir explorador web**|No|No|Windows Phone 8.1 solo|Sí|Sí (solo Samsung KNOX)|
|**Permitir el autorrelleno**|Sí|No|No|Sí|Sí (solo Samsung KNOX)|
|**Permitir bloqueador de elementos emergentes**|Sí|No|No|Sí|Sí (solo Samsung KNOX)|
|**Permitir cookies**|No|No|No|Sí|Sí (solo Samsung KNOX)|
|**Permitir complementos**|Sí|No|No|No|No|
|**Permitir Active scripting**|Sí|No|No|Sí|Sí (solo Samsung KNOX)|
|**Permitir advertencias de fraude**|Sí|No|No|Sí|No|
|**Permitir el acceso a sitios de intranet por la entrada de una sola palabra**<br /><br />(permite el uso de una sola palabra para dirigir Internet Explorer a un sitio web como, por ejemplo, "Bing")|Sí|No|No|No|No|
|**Permitir la detección automática de redes de intranet**|Sí|No|No|No|No|
|**Nivel de seguridad de Internet**|Sí|No|No|No|No|
|**Nivel de seguridad de intranet**|Sí|No|No|No|No|
|**Nivel de seguridad de sitios de confianza**|Sí|No|No|No|No|
|**Nivel de seguridad de sitios restringidos**|Sí|No|No|No|No|
|**Enviar encabezado Do Not Track**|Sí|No|No|No|No|
|**Permitir el acceso al menú Modo de empresa**|Sí|No|No|No|No|
|**Ubicación de la lista de sitios de Modo de empresa**|Sí|No|No|No|No|

## Configuración de la aplicación: aplicaciones

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir almacén de aplicaciones**|No|No|Windows Phone 8.1 solo|Sí|Sí (solo Samsung KNOX)|
|**Requerir una contraseña para tener acceso al almacén de aplicaciones**|No|No|No|Sí|No|
|**Permitir compras dentro de la aplicación**|No|No|No|Sí|No|
|**Permitir documentos administrados en otras aplicaciones no administradas**|No|No|No|iOS 7 y versiones posteriores|No|
|**Permitir documentos no administrados en otras aplicaciones administradas**|No|No|No|iOS 7 y versiones posteriores|No|
|**Permitir videoconferencias**|No|No|No|Sí|No|
|**Permitir contenido para adultos en el almacén multimedia**|No|No|No|Sí|No|
|**Permitir la instalación de aplicaciones**|No|No|No|iOS 6 y versiones posteriores|No|

## Configuración de la aplicación: juegos

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir amigos del Game Center**|No|No|No|Sí|No|
|**Permitir juegos multijugador**|No|No|No|Sí|No|

## Configuración de funcionalidades del dispositivo: hardware

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir cámara**|No|No|Windows Phone 8.1 solo|Sí|Sí|
|**Permitir almacenamiento extraíble**|No|No|Sí|No|Sí (solo Samsung KNOX)|
|**Permitir Wi-Fi**|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX)|
|**Permitir Wi-Fi Tethering**|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX)|
|**Permitir la conexión automática a zonas Wi-Fi gratuitas**|No|No|Windows Phone 8.1 solo|No|No|
|**Permitir informar de zonas Wi-Fi**<br /><br />(enviar información acerca de las conexiones Wi-Fi para ayudar a detectar conexiones cercanas)|No|No|Windows Phone 8.1 solo|No|No|
|**Permitir geolocalización**<br /><br />(permite que el dispositivo use la información de ubicación)|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX)|
|**Permitir NFC**<br /><br />(permite las operaciones que usan la transmisión de datos en proximidad)|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX)|
|**Permitir Bluetooth**|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX)|
|**Permitir desconectar**<br>Si se deshabilita esta opción, la opción **Número de errores de inicio de sesión repetidos que se permiten antes de que se eliminen los datos del dispositivo** de los dispositivos Samsung KNOX no funciona.|No|No|No|No|Sí (solo Samsung KNOX)|

## Configuración de funcionalidades del dispositivo: datos móviles

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir itinerancia de voz**|No|No|No|Sí|Sí (solo Samsung KNOX)|
|**Permitir itinerancia de datos**|Sí|No|No|Sí|Sí (solo Samsung KNOX)|
|**Permitir la sincronización automática en itinerancia**|No|No|No|Sí|No|
|**Permitir mensajería SMS y MMS**|No|No|No|No|Sí (solo Samsung KNOX)|

## Configuración de funcionalidades del dispositivo: características

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir asistente de voz**|No|No|No|Sí|Sí (solo Samsung KNOX)|
|**Permitir asistente de voz con el dispositivo bloqueado**|No|No|No|Sí|No|
|**Permitir la marcación por voz**|No|No|No|Sí|Sí (solo Samsung KNOX)|
|**Permitir copiar y pegar**|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX)|
|**Permitir el uso compartido del Portapapeles entre aplicaciones**|No|No|No|No|Sí (solo Samsung KNOX)|
|**Permitir YouTube**|No|No|No|No|Sí (solo Samsung KNOX)|

### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


