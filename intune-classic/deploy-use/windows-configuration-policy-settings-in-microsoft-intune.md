---
title: Configuración de directivas de Windows
description: Use la directiva de configuración general de Windows de Intune (Windows 8.1 y posterior) para configurar las opciones de los dispositivos Windows 8.1 y Windows 8 inscritos.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ccd5bd201de59537dbf99ea9e19d84dbf80c1a20
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="windows-policy-settings-in-microsoft-intune"></a>Configuración de directivas de Windows en Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Use la **directiva de configuración general de Windows (Windows 8.1 y posterior)** de Microsoft Intune para configurar las siguientes opciones de los dispositivos Windows 8, Windows 8.1 y Windows RT 8.1 inscritos:

## <a name="applicability-settings"></a>Configuración de aplicabilidad

|Nombre de la configuración|Detalles|
|----------------|----------------------------------|
|**Aplicar todas las configuraciones a Windows 10**|Permite aplicar la configuración de esta directiva en dispositivos Windows 10 y en dispositivos Windows 8 y Windows 8.1.|

## <a name="security-settings"></a>Configuración de seguridad

|Nombre de la configuración|Detalles|
|----------------|------|
|**Tipo de contraseña obligatoria**|Especifica el tipo de contraseña que es necesario, como solo numérica o alfanumérica.|
|**Tipo de contraseña requerida: número mínimo de conjuntos de caracteres**|Especifica cuántos juegos de caracteres diferentes deben incluirse en la contraseña. Hay cuatro juegos de caracteres: letras minúsculas, letras mayúsculas, símbolos y números. En cambio, para dispositivos iOS, esta opción especifica el número de símbolos que deben incluirse en la contraseña.|
|**Longitud mínima de contraseña**|Configura la longitud mínima necesaria (en caracteres) de la contraseña.|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Borra el dispositivo si hay un error en este número de intentos de inicio de sesión.|
|**Minutos de inactividad antes de que se apague la pantalla**|Especifica el número de minutos durante el cual un dispositivo debe estar inactivo antes de que se requiera una contraseña para desbloquearlo.|
|**Expiración de contraseña (días)**|Especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.|
|**Recordar el historial de contraseñas**|Especifica si el usuario puede configurar las contraseñas usadas anteriormente.|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Especifica el número de contraseñas usadas anteriormente que recuerda el dispositivo.|
|**Permitir contraseña de imagen y PIN**|Permite el uso de una contraseña de imagen y un PIN. Una contraseña de imagen permite que el usuario inicie sesión mediante gestos en una imagen. Un PIN permite que los usuarios inicien sesión rápidamente con un código de cuatro dígitos.|

## <a name="encryption-settings"></a>Configuración de cifrado

|                           Nombre de la configuración                           |                     Detalles                      |
|------------------------------------------------------------------|--------------------------------------------------|
| <strong>Requerir cifrado en dispositivo móvil</strong><sup>1</sup> | Requiere el cifrado de los archivos en el dispositivo. |

<sup>1</sup> Información adicional para los dispositivos que ejecutan Windows 8.1

-   Para forzar el cifrado en los dispositivos que ejecutan Windows 8.1, debe instalar la [Actualización de cliente de diciembre de 2014 MDM en Windows](http://support.microsoft.com/kb/3013816) en cada dispositivo.

-   Si habilita esta configuración para dispositivos Windows 8.1, todos los usuarios del dispositivo deben tener una cuenta de Microsoft.

-   Para que el cifrado funcione, el dispositivo debe cumplir los requisitos de certificación de hardware de Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) .

-   Al exigir el cifrado en un dispositivo, solo se puede obtener acceso a la clave de recuperación desde la cuenta Microsoft de los usuarios, a la que se obtiene acceso desde su cuenta de OneDrive. No se puede recuperar esta clave en nombre de un usuario.

## <a name="malware-settings"></a>Configuración de malware

|Nombre de la configuración|Detalles|
|----------------|-----|
|**Requerir firewall de red**|Requiere que el Firewall de Windows esté activado.|
|**Habilitar SmartScreen**|Requiere el uso de Windows SmartScreen.|

## <a name="system-settings"></a>Configuración del sistema

|Nombre de la configuración|Detalles|
|----------------|-------|
|**Requerir actualizaciones automáticas**|Activa las actualizaciones automáticas en los dispositivos.|
|**Requerir actualizaciones automáticas: clasificación mínima de actualizaciones para instalar automáticamente**|Elige la clasificación de actualizaciones que se instalarán automáticamente:<br /><br />-   **Importante**: instala todas las actualizaciones que se clasifican como importantes.<br />-   **Recomendada**: instala todas las actualizaciones que se clasifican como importantes o recomendadas.|
|**Control de cuentas de usuario**|Requiere el uso de Control de cuentas de usuario (UAC) en los dispositivos.|
|**Permitir el envío de datos de diagnóstico**|Permite que el dispositivo envíe información de diagnóstico a Microsoft.|


## <a name="cloud-settings--documents-and-data"></a>Configuración de nube: documentos y datos

|Nombre de la configuración|Detalles|
|----------------|------|
|**Dirección URL de carpetas de trabajo**|Establece la dirección URL de la carpeta de trabajo para permitir que los documentos se sincronicen en todos los dispositivos.|

## <a name="email-settings"></a>Configuración de correo electrónico

|Nombre de la configuración|Detalles|
|----------------|-----|
|**Hacer que la cuenta Microsoft sea opcional en la aplicación Windows Mail**|Permite el acceso a la aplicación Correo de Windows sin una cuenta Microsoft.|

## <a name="application-settings---browser"></a>Configuración de la aplicación: explorador

|Nombre de la configuración|Detalles|
|----------------|-----|
|**Permitir el autorrelleno**|Permite a los usuarios cambiar la configuración de Autocompletar en el explorador.|
|**Permitir bloqueador de elementos emergentes**|Habilita o deshabilita el bloqueador de elementos emergentes del explorador.|
|**Permitir complementos**|Permite a los usuarios agregar complementos en Internet Explorer.|
|**Permitir Active scripting**|Permite al explorador ejecutar scripts, como scripts de ActiveX.|
|**Permitir advertencias de fraude**|Habilita o deshabilita las advertencias de posibles sitios web fraudulentos.|
|**Permitir el acceso a sitios de intranet por la entrada de una sola palabra**|Permite el uso de una sola palabra para dirigir Internet Explorer a un sitio web como, por ejemplo, Bing.|
|**Permitir la detección automática de redes de intranet**|Ayuda a configurar la seguridad en sitios de intranet en Internet Explorer.|
|**Nivel de seguridad de Internet**|Establece el nivel de seguridad de Internet Explorer para sitios de Internet.|
|**Nivel de seguridad de intranet**|Establece el nivel de seguridad de Internet Explorer para sitios de intranet.|
|**Nivel de seguridad de sitios de confianza**|Configura el nivel de seguridad para la zona de sitios de confianza.|
|**Nivel de seguridad de sitios restringidos**|Configura el nivel de seguridad para la zona de sitios restringidos.|
|**Enviar encabezado Do Not Track**|En Internet Explorer, envía un encabezado Do Not Track a los sitios visitados.|
|**Permitir el acceso al menú Modo de empresa**|Permite a los usuarios tener acceso a las opciones del menú Modo de empresa desde Internet Explorer.<br>Si selecciona esta opción, también puede especificar una **Ubicación de informes de registro** que contenga una dirección URL a un informe que muestre los sitios web para los que los usuarios hayan activado el acceso en Modo de empresa.|
|**Ubicación de la lista de sitios de Modo de empresa**|Especifica la ubicación de la lista de sitios web que van a usar el modo de empresa cuando esté activo.|

## <a name="device-capabilities-settings---cellular"></a>Configuración de funcionalidades del dispositivo: datos móviles

|Nombre de la configuración|Detalles|
|----------------|----|
|**Permitir itinerancia de datos**|Permite la itinerancia de datos cuando el dispositivo está en una red de telefonía móvil.|



### <a name="see-also"></a>Vea también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
