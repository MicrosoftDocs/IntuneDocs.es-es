---
# required metadata

title: Configuración de directivas de Windows en Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configuración de directivas de Windows en Microsoft Intune
Use la **directiva de configuración general de Windows** de Microsoft Intune para configurar las opciones de los dispositivos Windows 8 y Windows 8.1 inscritos:

## Configuración de seguridad

|Nombre de la configuración|Detalles|Windows 8.1 y Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Tipo de contraseña obligatoria**|Especifica el tipo de contraseña que será necesario, como solo numérica o alfanumérica.|Sí|Sí|
|**Tipo de contraseña requerida: número mínimo de conjuntos de caracteres**|Hay cuatro conjuntos de caracteres: letras minúsculas, letras mayúsculas, símbolos y números. Esta configuración especifica cuántos conjuntos de caracteres diferentes deben incluirse en la contraseña. Sin embargo, para dispositivos iOS, especifica el número de caracteres de símbolos que deben incluirse en la contraseña.|Sí|Sí|
|**Longitud mínima de contraseña**<sup>1</sup>|Configura la longitud mínima necesaria (en caracteres) de la contraseña de los dispositivos.|Sí|Sí|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Borra el dispositivo si hay este número de intentos de inicio de sesión incorrectos.|Sí|Sí|
|**Minutos de inactividad antes de que se apague la pantalla**|Elija el número de minutos durante el cual un dispositivo debe estar inactivo antes de que se requiera una contraseña para desbloquearlo.| Sí|Sí|
|**Caducidad de contraseña (días)**|Especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.|Sí|Sí|
|**Recordar el historial de contraseñas**|Especifica si el usuario puede configurar las contraseñas usadas anteriormente.|Sí|Sí|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Especifica el número de contraseñas usadas anteriormente que recuerda el dispositivo.|Sí|Sí|
|**Permitir contraseña de imagen y PIN**|Permite el uso de una contraseña de imagen y un PIN en el dispositivo. Una contraseña de imagen permite que el usuario se registre mediante gestos en una imagen. Un PIN permite que el usuario inicie sesión rápidamente con un código de 4 dígitos.|Sí|Sí|
<sup>1</sup> Cuando se implementa una directiva de longitud de contraseña para dispositivos que ejecutan Windows RT, los usuarios se verán obligados a restablecer su contraseña, aunque la contraseña actual cumpla los requisitos de la directiva.

## Configuración de cifrado

|Nombre de la configuración|Detalles|Windows 8.1 y Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Requerir cifrado en dispositivo móvil**<sup>1</sup>|Requiere el cifrado de los archivos en el dispositivo.<br>Para dispositivos de Windows Phone 8, debe establecerse en **Sí**..|Sí|No|
<sup>1</sup> Información adicional para los dispositivos que ejecutan Windows 8.1

-   Para forzar el cifrado en los dispositivos que ejecutan Windows 8.1, debe instalar la [Actualización de cliente de diciembre de 2014 MDM en Windows](http://support.microsoft.com/kb/3013816) en cada dispositivo.

-   Si habilita este valor para dispositivos de Windows 8.1, todos los usuarios del dispositivo deben tener una cuenta de Microsoft.

-   Para que el cifrado funcione, el dispositivo debe cumplir los requisitos de certificación de hardware de Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) .

-   Al exigir el cifrado en un dispositivo, solo se puede acceder a la clave de recuperación desde la cuenta de Microsoft de los usuarios, a la que se accede desde su cuenta de OneDrive. No se puede recuperar esta clave en nombre de un usuario.

## Configuración de malware

|Nombre de la configuración|Detalles|Windows 8.1 y Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Requerir firewall de red**|Requiere que el firewall de Windows esté activado.|Sí|No|
|**Habilitar SmartScreen**|Requiere el uso de Windows SmartScreen en dispositivos.|Sí|No|

## Configuración del sistema

|Nombre de la configuración|Detalles|Windows 8.1 y Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Requerir actualizaciones automáticas**|Activar las actualizaciones automáticas en los dispositivos.|Sí|No|
|**Requerir actualizaciones automáticas: clasificación mínima de actualizaciones para instalar automáticamente**|Seleccione la clasificación de actualizaciones que se instalarán automáticamente:<br /><br />-   **Importantes**: instala todas las actualizaciones que se clasifican como importantes.<br />-   **Recomendadas**: instala todas las actualizaciones que se clasifican como importantes o recomendadas.|Sí|No|
|**Control de cuentas de usuario**|Requiere el uso de Control de cuentas de usuario (UAC) en los dispositivos.|Sí|No|
|**Permitir el envío de datos de diagnóstico**|Permite que el dispositivo envíe información de diagnóstico a Microsoft.|Sí|No|


## Configuración de nube: documentos y datos

|Nombre de la configuración|Detalles|Windows 8.1 y Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Dirección URL de carpetas de trabajo**|Establece la dirección URL de la carpeta de trabajo para permitir que los documentos se sincronicen en todos los dispositivos.|Sí|No|

## Configuración de correo electrónico

|Nombre de la configuración|Detalles|Windows 8.1 y Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Hacer que la cuenta Microsoft sea opcional en la aplicación Windows Mail**|Permite el acceso a la aplicación Correo de Windows sin cuenta de Microsoft.|Sí|No|

## Configuración de la aplicación: explorador

|Nombre de la configuración|Detalles|Windows 8.1 y Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Permitir el autorrelleno**|El usuario puede cambiar la configuración de Autocompletar en el explorador.|Sí|No|
|**Permitir bloqueador de elementos emergentes**|Habilita o deshabilita el bloqueador de elementos emergentes del explorador.|Sí|No|
|**Permitir complementos**|El usuario puede agregar complementos en Internet Explorer.|Sí|No|
|**Permitir Active scripting**|El explorador puede ejecutar scripts, como scripts de ActiveX.|Sí|No|
|**Permitir advertencias de fraude**|Habilita o deshabilita las advertencias de posibles sitios web fraudulentos.|Sí|No|
|**Permitir el acceso a sitios de intranet por la entrada de una sola palabra**|Permite el uso de una sola palabra para dirigir Internet Explorer a un sitio web como, por ejemplo, Bing.|Sí|No|
|**Permitir la detección automática de redes de intranet**|Ayuda a configurar la seguridad en sitios de intranet en Internet Explorer.|Sí|No|
|**Nivel de seguridad de Internet**|Establece el nivel de seguridad de Internet Explorer para sitios de Internet.|Sí|No|
|**Nivel de seguridad de intranet**|Establece el nivel de seguridad de Internet Explorer para sitios de intranet.|Sí|No|
|**Nivel de seguridad de sitios de confianza**|Configura el nivel de seguridad para la zona de sitios de confianza.|Sí|No|
|**Nivel de seguridad de sitios restringidos**|Configura el nivel de seguridad para la zona de sitios restringidos.|Sí|No|
|**Enviar encabezado Do Not Track**|En Internet Explorer, envía un encabezado Do Not Track a los sitios visitados.|Sí|No|
|**Permitir el acceso al menú Modo de empresa**|Permite a los usuarios tener acceso a las opciones del menú Modo de empresa desde Internet Explorer.<br>Si se selecciona, también puede especificar una **Ubicación de informes de registro** que contenga una dirección URL a un informe que muestre los sitios web para los que los usuarios hayan activado el acceso en Modo de empresa.|Sí|No|
|**Ubicación de la lista de sitios de Modo de empresa**|Especifique la ubicación de la lista de sitios web que van a usar el modo de empresa cuando esté activo.|Sí|No|

## Configuración de funcionalidades del dispositivo: datos móviles

|Nombre de la configuración|Detalles|Windows 8.1 y Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Permitir itinerancia de datos**|Permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.|Sí|No|



### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


