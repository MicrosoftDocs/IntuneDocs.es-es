---
title: "Configuración de directivas de Exchange ActiveSync | Microsoft Docs"
description: "Use la directiva de Exchange ActiveSync de Intune para configurar las opciones que le permitirán controlar características y funciones en los dispositivos administrados por Exchange ActiveSync."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: f35a6da93e48141489b89e62b37b473d885479cf


---

# <a name="exchange-activesync-policy-settings-in-microsoft-intune"></a>Configuración de directivas de Exchange ActiveSync en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use la directiva de **Exchange ActiveSync** de Microsoft Intune para configurar las opciones que controlan diversas características y funcionalidades en los dispositivos que Exchange ActiveSync administra.


## <a name="password-settings"></a>Configuración de contraseña

|Nombre de la configuración|Detalles
|----------------|---|
|**Requerir una contraseña para desbloquear dispositivos móviles**|Especifica si se deben bloquear los dispositivos con una contraseña.<br>(No aplicable a los dispositivos que ejecutan Windows RT).|
|**Tipo de contraseña obligatoria**|Especifica el tipo de contraseña que será necesaria, como solo numérica o alfanumérica.|
|**Longitud mínima de contraseña**|Especifica el número mínimo de caracteres necesarios en la contraseña del dispositivo.|
|**Permitir contraseñas sencillas**|Especifica si se pueden usar contraseñas simples, que incluyen "0000" y "1234".|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Especifica el número de veces que un usuario puede escribir una contraseña incorrecta antes de que se borre el dispositivo.|
|**Expiración de contraseña (días)**|Especifica el número de días tras el que debe cambiarse la contraseña del dispositivo.
|**Recordar el historial de contraseñas**|Especifica si no se permite el uso de contraseñas usadas previamente.|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Especifica el número de contraseñas usadas previamente que no se pueden volver a usar.|
|**Minutos de inactividad antes de que se pida la contraseña**|Especifica la cantidad de tiempo que un dispositivo debe estar inactivo antes de que se bloquee la pantalla.

## <a name="encryption-settings"></a>Configuración de cifrado

|Nombre de la configuración|Detalles|
|----------------|---|
|**Requerir cifrado en dispositivo móvil**<sup>1</sup>|Cuando se admite esta característica, requiere que los datos de un dispositivo se cifren.<br><br>Para dispositivos de Windows Phone 8, debe establecerse en **Sí**.<br /><br />Para habilitar el cifrado en dispositivos iOS, habilite la configuración **Requerir una contraseña para desbloquear dispositivos móviles**.|
|**Requerir cifrado en tarjetas de almacenamiento**|Requiere que se cifren los datos almacenados en un almacenamiento externo, como una tarjeta SD (en dispositivos compatibles).
<sup>1</sup> Información adicional para los dispositivos que ejecutan Windows 8.1

-   Para forzar el cifrado en los dispositivos que ejecutan Windows 8.1, debe instalar en cada dispositivo la [Actualización de cliente MDM de diciembre de 2014 para Windows](http://support.microsoft.com/kb/3013816).

-   Si habilita esta configuración para dispositivos Windows 8.1, todos los usuarios del dispositivo deben tener una cuenta de Microsoft.

-   Para que el cifrado funcione en dispositivos Windows 8.1, el dispositivo debe cumplir los requisitos de certificación de hardware de Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) .

-   Al aplicar el cifrado en un dispositivo Windows 8.1, solo se puede acceder a la clave de recuperación desde la cuenta de Microsoft del usuario, a la que se accede desde la cuenta de OneDrive del usuario. No se puede recuperar esta clave en nombre de un usuario.

## <a name="email-settings"></a>Configuración de correo electrónico

|Nombre de la configuración|Detalles
|----------------|---|
|**Permitir a los usuarios descargar datos adjuntos de correo electrónico**|Especifica si se pueden descargar datos adjuntos de correo electrónico en el dispositivo.|
|**Periodo de sincronización del correo electrónico**|Especifica el número de días que se sincroniza el correo electrónico recibido en el dispositivo.
|**Permitir que los dispositivos móviles que no son totalmente compatibles con la configuración de Exchange ActiveSync se sincronicen con Exchange**|Especifica si se permite el acceso a Exchange en los dispositivos que no son compatibles con una o más configuraciones de Exchange ActiveSync.

## <a name="browser-settings"></a>Configuración del explorador

|Nombre de la configuración|Detalles
|----------------|---|
|**Permitir explorador web**|Especifica si se puede usar el explorador web en el dispositivo.<br>(No disponible para Windows RT ni Windows Phone).

## <a name="hardware-settings"></a>Configuración de hardware

|Nombre de la configuración|Detalles
|----------------|---|
|**Permitir cámara**|Especifica si se puede usar la cámara del dispositivo.<br>(No disponible para Windows RT ni Windows Phone).



### <a name="see-also"></a>Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Dec16_HO5-->


