---
title: "Configuración de directivas de seguridad de dispositivos móviles | Microsoft Docs"
description: "Use Intune para configurar una amplia variedad de opciones que puede implementar en los dispositivos administrados de su organización."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 755cf7d87d7145c55eb5fe583748bd98d34e8fb1



---

# <a name="mobile-device-security-policy-settings-in-microsoft-intune"></a>Configuración de directivas de seguridad de dispositivos móviles en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

> [!IMPORTANT]
> Ahora Microsoft Intune presenta directivas de configuración independientes para cada plataforma de dispositivos. Estas directivas contienen la configuración más actualizada que puede usar. Puede seguir usando la directiva de seguridad de dispositivos móviles, ya que las implementaciones existentes seguirán funcionando. En cambio, debe planear la migración a las nuevas directivas de configuración tan pronto como sea posible, ya que la directiva de seguridad de dispositivos móviles se eliminará en el futuro.

Puede usar las directivas de seguridad de dispositivos móviles de Intune para configurar una amplia variedad de opciones que puede implementar para los dispositivos administrados de su organización. Estas opciones de configuración se usan para controlar la funcionalidad y la seguridad de los dispositivos.

Puede crear e implementar directivas de seguridad de dispositivos móviles para los siguientes tipos de dispositivo:

-   Dispositivos Windows RT 8.1 y dispositivos Windows 8.1 inscritos

-   Windows RT

-   Windows Phone 8 y Windows Phone 8.1

-   iOS

-   Android y Samsung KNOX Standard

> [!NOTE]
> Algunas opciones no son aplicables a algunos dispositivos. Vea las tablas siguientes para obtener una lista completa de las opciones que puede configurar.
> Desde octubre de 2016, Microsoft Intune dejará de ofrecer soporte a las aplicaciones del portal de empresa de Windows 8. Microsoft Intune también dejará de ofrecer soporte para la plataforma Windows Phone 8 y WinRT. Como consecuencia, no podrá inscribir ni actualizar ningún dispositivo Windows Phone 8 o WinRT. Puede seguir administrando los dispositivos Windows Phone 8, WinRT y Windows 8 que ya estén inscritos. Actualice los dispositivos Windows Phone 8 y Windows 8 a Windows 8.1 y Windows Phone 8.1 y use las aplicaciones de portal de empresa de Windows 8.1 y Windows Phone 8.1 correspondientes para poder seguir con la distribución de aplicaciones en estos dispositivos sin interrupciones.

## <a name="security-settings"></a>Configuración de seguridad

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Requerir una contraseña para desbloquear dispositivos móviles**|No|No|Sí|Sí|Sí|
|**Tipo de contraseña obligatoria**<br /><br />Esta opción especifica el tipo de contraseña que será necesario, como solo numérica o alfanumérica.|Sí|Sí|Sí|Sí|No|
|**Tipo de contraseña requerida: número mínimo de conjuntos de caracteres**<br /><br />Hay cuatro juegos de caracteres: letras minúsculas, letras mayúsculas, símbolos y números. Esta configuración especifica cuántos conjuntos de caracteres diferentes deben incluirse en la contraseña. En cambio, para dispositivos iOS, especifica el número de caracteres de símbolos que deben incluirse en la contraseña.|Sí|Sí|Sí|Sí|No|
|**Longitud mínima de contraseña**|Sí|Sí|Sí|Sí|Sí|
|**Permitir contraseñas sencillas**<br /><br />Las contraseñas sencillas incluyen “0000” y “1234”.|No|No|Sí|Sí|No|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Sí|Sí|Sí|Sí|Sí|
|**Minutos de inactividad antes de que se apague la pantalla**<sup>1</sup>|Sí|Sí|Sí|Sí|Sí|
|**Expiración de contraseña (días)**|Sí|Sí|Sí|Sí|Sí|
|**Recordar el historial de contraseñas**|Sí|Sí|Sí|Sí|Sí|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Sí|Sí|Sí|Sí|Sí|
|**Calidad de contraseña**|No|No|No|No|Sí|
|**Permitir contraseña de imagen y PIN**|Sí|Sí|No|No|No|
|**Minutos de inactividad antes de que se pida la contraseña**|No|No|No|Sí|No|
|**Permitir desbloqueo mediante huellas digitales**|No|No|No|iOS 7 y versiones posteriores|No|
<sup>1</sup>En los dispositivos iOS, cuando configura las opciones **Minutos de inactividad antes de que se apague la pantalla** y **Minutos de inactividad antes de que sea necesaria la contraseña**, se aplican en secuencia. Por ejemplo, si establece el valor para ambas opciones en **5** minutos, la pantalla se apagará automáticamente transcurridos 5 minutos y el dispositivo se bloqueará pasados 5 minutos más. Sin embargo, si el usuario apaga la pantalla manualmente, la segunda opción se aplica inmediatamente. En el mismo ejemplo, una vez que el usuario apague la pantalla, el dispositivo se bloqueará 5 minutos más tarde.

Cuando implementa una directiva de longitud de contraseña para dispositivos que ejecutan Windows RT, los usuarios se verán obligados a restablecer la contraseña, aunque la contraseña actual cumpla los requisitos de la directiva.

## <a name="encryption-settings"></a>Configuración de cifrado

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Requerir cifrado en dispositivo móvil**<sup>1</sup><br /><br />Para dispositivos de Windows Phone 8, debe establecerse en **Sí**.<br /><br />Para habilitar el cifrado en dispositivos iOS, habilite la opción **Requerir una contraseña para desbloquear dispositivos móviles**.|Sí|No|Sí|No|Sí|
|**Requerir cifrado en tarjetas de almacenamiento**<br /><br />Esta opción también se aplica a dispositivos administrados por Exchange ActiveSync.|n/a|n/a|n/a <br />Las aplicaciones y los datos asociados se cifran automáticamente.|n/a|Sí|
<sup>1</sup>Aquí se muestra información adicional para los dispositivos que ejecutan Windows 8.1:

-   Para forzar el cifrado en los dispositivos que ejecutan Windows 8.1, debe instalar la [Actualización de cliente de diciembre de 2014 MDM en Windows](http://support.microsoft.com/kb/3013816) en cada dispositivo.

-   Si habilita esta configuración para dispositivos Windows 8.1, todos los usuarios del dispositivo deben tener una cuenta de Microsoft.

-   Para que el cifrado funcione, el dispositivo debe cumplir los requisitos de certificación de hardware de Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) .

-   Al exigir el cifrado en un dispositivo, solo se puede obtener acceso a la clave de recuperación desde la cuenta Microsoft de los usuarios, a la que se obtiene acceso desde su cuenta de OneDrive. No se puede recuperar esta clave en nombre de un usuario.

## <a name="malware-settings"></a>Configuración de malware

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Requerir firewall de red**|Sí|No|No|No|No|
|**Habilitar SmartScreen**|Sí|No|No|No|No|

## <a name="system-settings"></a>Configuración del sistema

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Requerir actualizaciones automáticas**|Sí|No|No|No|No|
|**Requerir actualizaciones automáticas: clasificación mínima de actualizaciones para instalar automáticamente**<br /><br />Seleccione la clasificación de actualizaciones que se instalarán automáticamente:<br /><br />- **Importantes** Instala todas las actualizaciones que se clasifican como importantes.<br /><br />- **Recomendadas** Instala todas las actualizaciones que se clasifican como importantes o recomendadas.|Sí|No|No|No|No|
|**Permitir captura de pantalla**|No|No|Windows Phone 8.1 solo|Sí|Sí (solo Samsung KNOX Standard)|
|**Permitir centro de control en la pantalla de bloqueo**|No|No|No|iOS 7 y versiones posteriores|No|
|**Permitir vista de notificaciones en la pantalla de bloqueo**|No|No|No|iOS 7 y versiones posteriores|No|
|**Permitir vista de hoy en la pantalla de bloqueo**|No|No|No|iOS 7 y versiones posteriores|No|
|**Control de cuentas de usuario**|Sí|No|No|No|No|
|**Permitir el envío de datos de diagnóstico**|Sí|No|Windows Phone 8.1 solo|Sí|Sí (solo Samsung KNOX Standard)|
|**Permitir certificados TLS que no son de confianza**|No|No|No|Sí|No|
|**Permitir el software de cartera personal durante un bloqueo**|No|No|No|Sí|No|
|**Permitir el restablecimiento de la configuración de fábrica**|No|No|No|No|Sí (solo Samsung KNOX Standard)|


## <a name="cloud-settings--documents-and-data"></a>Configuración de nube: documentos y datos

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir copias de seguridad en iCloud**|No|No|No|Sí|No|
|**Permitir sincronización de documentos en iCloud**|No|No|No|Sí|No|
|**Permitir sincronización de Photo Stream en iCloud**|No|No|No|Sí|No|
|**Requerir copia de seguridad cifrada**|No|No|No|Sí|No|
|**Dirección URL de carpetas de trabajo**<br /><br />Esta opción establece la dirección URL de la carpeta de trabajo para permitir que los documentos se sincronicen en todos los dispositivos.|Sí|No|No|No|No|
|**Permitir copia de seguridad de Google**|No|No|No|No|Sí (solo Samsung KNOX Standard)|

## <a name="cloud-settings--accounts-and-synchronization"></a>Configuración de nube: cuentas y sincronización

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir cuenta de Microsoft**|No|No|Windows Phone 8.1 solo|No|No|
|**Permitir la sincronización automática de la cuenta de Google**|No|No|No|No|Sí (solo Samsung KNOX Standard)|

## <a name="email-settings"></a>Configuración de correo electrónico

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir a los usuarios descargar datos adjuntos de correo electrónico**<sup>1</sup>|n/a|n/a|n/a|n/a|n/a|
|**Periodo de sincronización del correo electrónico** <br /><br />Esta opción también se aplica a dispositivos administrados por Exchange ActiveSync.|n/a|n/a|n/a|n/a|n/a|
|**Permitir que los dispositivos móviles que no son totalmente compatibles con esta configuración se sincronicen con Exchange (Exchange ActiveSync)** <br /><br />Esta opción también se aplica a dispositivos administrados por Exchange ActiveSync.|n/a|n/a|n/a|n/a|n/a|
|**Hacer que la cuenta Microsoft sea opcional en la aplicación Windows Mail**|Sí|No|No|No|No|
|**Permitir cuentas de correo electrónico personalizadas**|No|No|Windows Phone 8.1 solo|No|No|

## <a name="application-settings---browser"></a>Configuración de la aplicación: explorador

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir explorador web**|No|No|Windows Phone 8.1 solo|Sí|Sí (solo Samsung KNOX Standard)|
|**Permitir el autorrelleno**|Sí|No|No|Sí|Sí (solo Samsung KNOX Standard)|
|**Permitir bloqueador de elementos emergentes**|Sí|No|No|Sí|Sí (solo Samsung KNOX Standard)|
|**Permitir cookies**|No|No|No|Sí|Sí (solo Samsung KNOX Standard)|
|**Permitir complementos**|Sí|No|No|No|No|
|**Permitir Active scripting**|Sí|No|No|Sí|Sí (solo Samsung KNOX Standard)|
|**Permitir advertencias de fraude**|Sí|No|No|Sí|No|
|**Permitir el acceso a sitios de intranet por la entrada de una sola palabra**<br /><br />(Esta opción permite el uso de una sola palabra para dirigir Internet Explorer a un sitio web: por ejemplo, "Bing").|Sí|No|No|No|No|
|**Permitir la detección automática de redes de intranet**|Sí|No|No|No|No|
|**Nivel de seguridad de Internet**|Sí|No|No|No|No|
|**Nivel de seguridad de intranet**|Sí|No|No|No|No|
|**Nivel de seguridad de sitios de confianza**|Sí|No|No|No|No|
|**Nivel de seguridad de sitios restringidos**|Sí|No|No|No|No|
|**Enviar encabezado Do Not Track**|Sí|No|No|No|No|
|**Permitir el acceso al menú Modo de empresa**|Sí|No|No|No|No|
|**Ubicación de la lista de sitios de Modo de empresa**|Sí|No|No|No|No|

## <a name="application-settings---apps"></a>Configuración de la aplicación: aplicaciones

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir almacén de aplicaciones**|No|No|Windows Phone 8.1 solo|Sí|Sí (solo Samsung KNOX Standard)|
|**Requerir una contraseña para tener acceso al almacén de aplicaciones**|No|No|No|Sí|No|
|**Permitir compras dentro de la aplicación**|No|No|No|Sí|No|
|**Permitir documentos administrados en otras aplicaciones no administradas**|No|No|No|iOS 7 y versiones posteriores|No|
|**Permitir documentos no administrados en otras aplicaciones administradas**|No|No|No|iOS 7 y versiones posteriores|No|
|**Permitir videoconferencias**|No|No|No|Sí|No|
|**Permitir contenido para adultos en el almacén multimedia**|No|No|No|Sí|No|
|**Permitir la instalación de aplicaciones**|No|No|No|iOS 6 y versiones posteriores|No|

## <a name="application-settings---gaming"></a>Configuración de la aplicación: juegos

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir amigos del Game Center**|No|No|No|Sí|No|
|**Permitir juegos multijugador**|No|No|No|Sí|No|

## <a name="device-capabilities-settings---hardware"></a>Configuración de funcionalidades del dispositivo: hardware

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir cámara**|No|No|Windows Phone 8.1 solo|Sí|Sí|
|**Permitir almacenamiento extraíble**|No|No|Sí|No|Sí (solo Samsung KNOX Standard)|
|**Permitir Wi-Fi**|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX Standard)|
|**Permitir Wi-Fi Tethering**|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX Standard)|
|**Permitir la conexión automática a zonas Wi-Fi gratuitas**|No|No|Windows Phone 8.1 solo|No|No|
|**Permitir informar de zonas Wi-Fi**<br /><br />Esta opción envía información sobre las conexiones Wi-Fi para ayudar a detectar conexiones cercanas.|No|No|Windows Phone 8.1 solo|No|No|
|**Permitir geolocalización**<br /><br />Esta opción permite que el dispositivo use información de ubicación.|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX Standard)|
|**Permitir NFC**<br /><br />Esta opción permite las operaciones que usan la transmisión de datos en proximidad.|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX Standard)|
|**Permitir Bluetooth**|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX Standard)|
|**Permitir desconectar**<br>Si se deshabilita esta opción, la opción **Número de errores de inicio de sesión repetidos que se permiten antes de que se eliminen los datos del dispositivo** de los dispositivos Samsung KNOX Standard no funciona.|No|No|No|No|Sí (solo Samsung KNOX Standard)|

## <a name="device-capabilities-settings---cellular"></a>Configuración de funcionalidades del dispositivo: datos móviles

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir itinerancia de voz**|No|No|No|Sí|Sí (solo Samsung KNOX Standard)|
|**Permitir itinerancia de datos**|Sí|No|No|Sí|Sí (solo Samsung KNOX Standard)|
|**Permitir la sincronización automática en itinerancia**|No|No|No|Sí|No|
|**Permitir mensajería SMS y MMS**|No|No|No|No|Sí (solo Samsung KNOX Standard)|

## <a name="device-capabilities-settings---features"></a>Configuración de funcionalidades del dispositivo: características

|Nombre de la configuración|Windows 8.1 y Windows RT 8.1|Windows RT|Windows Phone 8 y Windows Phone 8.1|iOS|Android y Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Permitir asistente de voz**|No|No|No|Sí|Sí (solo Samsung KNOX Standard)|
|**Permitir asistente de voz con el dispositivo bloqueado**|No|No|No|Sí|No|
|**Permitir la marcación por voz**|No|No|No|Sí|Sí (solo Samsung KNOX Standard)|
|**Permitir copiar y pegar**|No|No|Windows Phone 8.1 solo|No|Sí (solo Samsung KNOX Standard)|
|**Permitir el uso compartido del Portapapeles entre aplicaciones**|No|No|No|No|Sí (solo Samsung KNOX Standard)|
|**Permitir YouTube**|No|No|No|No|Sí (solo Samsung KNOX Standard)|

### <a name="see-also"></a>Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Dec16_HO2-->


