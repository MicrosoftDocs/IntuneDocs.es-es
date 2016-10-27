---
title: "¿Qué ocurre si restablece el dispositivo Windows mediante el Portal de empresa? | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1ee6e275-d1ec-4da3-bbef-d5da2c61a02a
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08f31db90f324ef5f93076c4e13bfa5328a15adc
ms.openlocfilehash: b597e3557ec2c5661490b417e1d0459eb4e8b477


---


# ¿Qué ocurre si restablece el dispositivo Windows mediante el Portal de empresa?

Cuando usa la aplicación del Portal de empresa o el [sitio web del Portal de empresa](reset-your-device-cpwebsite.md) para restablecer el dispositivo Windows, restablece el dispositivo a la configuración de fábrica y elimina todas las aplicaciones, configuración y datos, incluidos los datos personales. Lo que sucede en cada dispositivo depende del tipo de dispositivo y de cómo se usa, tal como se describe en la tabla siguiente. Para obtener instrucciones sobre cómo restablecer el dispositivo perdido o robado, vea [Restablecer (borrar) el dispositivo perdido o robado](reset-erase-your-lost-or-stolen-device-windows.md).

|Administración y configuración de dispositivos|Tipo de dispositivo|
|---------------------------------------|---------------|
|El administrador de TI administra el dispositivo móvil|**Windows 10 y Windows Phone 8.1**</br>El dispositivo ya no aparecerá en el Portal de empresa y este portal intentará restablecer la configuración predeterminada del fabricante en el dispositivo. Se eliminarán los datos personales, las aplicaciones y la configuración. <br /><br />**Windows 10 Mobile**: la única forma de anular la inscripción del dispositivo es restablecerlo.|
|El dispositivo solo puede acceder al correo electrónico de la empresa|**Windows Phone 8,1**<br />El dispositivo ya no aparecerá en el Portal de empresa, se eliminará la cuenta de correo laboral y se eliminarán los mensajes de correo que no se hayan guardado.<br /><br />**Equipos con Windows Vista o Windows 7**<br />No se puede restablecer un equipo que ejecute Windows 7 o versiones anteriores, y que se utilice para correo electrónico únicamente.<br /><br />**Equipos con Windows 8.1 y Windows 8**<br />El dispositivo ya no aparecerá en el Portal de empresa, se eliminará la cuenta de correo laboral y se eliminarán los mensajes de correo que no se hayan guardado.|
|PCs y portátiles|**Equipos con Windows 8.1 y Windows 8**<br />No se puede restablecer un equipo con Windows 8 o Windows 8.1 a menos que se utilice para correo electrónico únicamente.<br /><br />**Equipos con Windows Vista o Windows 7**<br />No se puede restablecer un equipo con Windows 7 o anterior.|

Si tiene alguna pregunta, póngase en contacto con el administrador de TI. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).





<!--HONumber=Oct16_HO2-->


