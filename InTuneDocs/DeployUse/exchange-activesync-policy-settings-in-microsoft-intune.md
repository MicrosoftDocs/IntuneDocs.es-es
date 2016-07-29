---
title: "Configuración de directivas de Exchange ActiveSync | Microsoft Intune"
description: "Use la directiva de Exchange ActiveSync de Intune para configurar las opciones que le permitirán controlar características y funciones en los dispositivos administrados por Exchange ActiveSync."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6716a3d1fb53dc3de0189f637d5664d0a2023d05
ms.openlocfilehash: 0779fca11a692ce6843ef2ebf1c6a459273fc7cc


---

# Configuración de directivas de Exchange ActiveSync en Microsoft Intune
Use la directiva de **Exchange ActiveSync** de Microsoft Intune para configurar las opciones que le permitirán controlar una variedad de características y funciones en los dispositivos administrados por Exchange ActiveSync.


## Configuración de contraseña

|Nombre de la configuración|Detalles
|----------------|
|**Requerir una contraseña para desbloquear dispositivos móviles**|Especifica si se deben bloquear los dispositivos con una contraseña.<br>(No aplicable a los dispositivos que ejecutan Windows RT).|
|**Tipo de contraseña obligatoria**|Especifica el tipo de contraseña que se necesitará, como solo numérica o alfanumérica.|
|**Longitud mínima de la contraseña**|Especifica el número mínimo de caracteres necesarios en la contraseña del dispositivo.|
|**Permitir contraseñas sencillas**|Las contraseñas sencillas incluyen “0000” y “1234”.|
|**Número de errores de inicio de sesión repetidos que se permiten antes de que se borre el dispositivo**|Permitir tantos intentos al escribir una contraseña correcta antes de que se borre el dispositivo.|
|**Caducidad de contraseña (días)**|Especifica el número de días tras el que debe cambiarse la contraseña del dispositivo.
|**Recordar el historial de contraseñas**|Especifica si no se permite el uso de contraseñas usadas previamente.|
|**Recordar historial de la contraseña** : **Impedir la reutilización de contraseñas anteriores**|Especifica el número de contraseñas usadas previamente que no se pueden volver a usar.|
|**Minutos de inactividad antes de que se pida la contraseña**|Especifica la cantidad de tiempo que un dispositivo debe estar inactivo antes de que se bloquee la pantalla.

## Configuración de cifrado

|Nombre de la configuración|Detalles|
|----------------|
|**Requerir cifrado en un dispositivo móvil**<sup>1</sup>|Requiere que se cifren los datos en el dispositivo cuando se admita esta característica.<br>Para dispositivos de Windows Phone 8, debe establecerse en **Sí**.<br /><br />Para habilitar el cifrado en dispositivos iOS, habilite la opción **Requerir una contraseña para desbloquear dispositivos móviles**.|
|**Requerir cifrado en tarjetas de almacenamiento**|Requiere que se cifren los datos almacenados en un almacenamiento externo, como una tarjeta SD (en dispositivos compatibles).
<sup>1</sup> Información adicional para los dispositivos que ejecutan Windows 8.1

-   Para forzar el cifrado en los dispositivos que ejecutan Windows 8.1, debe instalar la [Actualización de cliente de diciembre de 2014 MDM en Windows](http://support.microsoft.com/kb/3013816) en cada dispositivo.

-   Si habilita este valor para dispositivos de Windows 8.1, todos los usuarios del dispositivo deben tener una cuenta de Microsoft.

-   Para que el cifrado funcione, el dispositivo debe cumplir los requisitos de certificación de hardware de Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) .

-   Al exigir el cifrado en un dispositivo, solo se puede acceder a la clave de recuperación desde la cuenta de Microsoft de los usuarios, a la que se accede desde su cuenta de OneDrive. No se puede recuperar esta clave en nombre de un usuario.

## Configuración de correo electrónico

|Nombre de la configuración|Detalles
|----------------|
|**Permitir a los usuarios descargar datos adjuntos de correo electrónico**|Especifica si se pueden descargar datos adjuntos de correo electrónico en el dispositivo.|
|**Periodo de sincronización del correo electrónico**|Selecciona el número de días que se sincronizará el correo electrónico recibido en el dispositivo.
|**Permitir que los dispositivos móviles que no son totalmente compatibles con la configuración de Exchange ActiveSync se sincronicen con Exchange**|Especifica si se permite el acceso a Exchange en los dispositivos que no son compatibles con una o más configuraciones de Exchange ActiveSync.

## Configuración del explorador

|Nombre de la configuración|Detalles
|----------------|-
|**Permitir explorador web**|Especifica si se puede usar el explorador web en el dispositivo.<br>(no disponible para Windows RT o Windows Phone).

## Configuración de hardware

|Nombre de la configuración|Detalles
|----------------|
|**Permitir cámara**|Especifica si se puede usar la cámara del dispositivo.<br>(No disponible para Windows RT o Windows Phone).



### Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jul16_HO4-->


