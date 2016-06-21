---
# required metadata

title: ¿Qué ocurre si restablece el dispositivo con el Portal de empresa? | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1ee6e275-d1ec-4da3-bbef-d5da2c61a02a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: priyar
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# ¿Qué ocurre si restablece el dispositivo con el Portal de empresa?

Si usa el Portal de empresa o el sitio web del Portal de empresa para restablecer un dispositivo Windows, es posible que se eliminen algunas aplicaciones y configuraciones del dispositivo, incluidos algunos de sus datos personales. Lo que sucede en cada dispositivo depende del tipo de dispositivo y de cómo se usa, tal como se describe en la tabla siguiente. Para obtener instrucciones sobre cómo restablecer el dispositivo perdido o robado, vea [Restablecer (borrar) el dispositivo perdido o robado](reset-erase-your-lost-or-stolen-device-windows.md).

|Administración y configuración de dispositivos|Tipo de dispositivo|
|---------------------------------------|---------------|
|El administrador de TI administra el dispositivo móvil|**Windows 10, Windows Phone 8.1 y Windows Phone 8**</br>El dispositivo ya no aparecerá en el Portal de empresa y este portal intentará restablecer la configuración predeterminada del fabricante en el dispositivo. Se eliminarán los datos personales, las aplicaciones y la configuración.<br /><br />**Windows RT**<br />No se puede restablecer un dispositivo Windows RT a menos que se utilice para correo electrónico únicamente.|
|El dispositivo solo puede acceder al correo electrónico de la empresa|**Windows Phone 8.1 y Windows Phone 8**<br />El dispositivo ya no aparecerá en el Portal de empresa, se eliminará la cuenta de correo laboral y se eliminarán los mensajes de correo que no se hayan guardado.<br /><br />**Windows RT**<br />El dispositivo ya no aparecerá en el Portal de empresa, se eliminará la cuenta de correo laboral y se eliminarán los mensajes de correo que no se hayan guardado.<br /><br />**Equipos con Windows Vista o Windows 7**<br />No se puede restablecer un equipo que ejecute Windows 7 o versiones anteriores, y que se utilice para correo electrónico únicamente.<br /><br />**Equipos con Windows 8.1 y Windows 8**<br />El dispositivo ya no aparecerá en el Portal de empresa, se eliminará la cuenta de correo laboral y se eliminarán los mensajes de correo que no se hayan guardado.|
|PCs y portátiles|**Equipos con Windows 8.1 y Windows 8**<br />No se puede restablecer un equipo con Windows 8 o Windows 8.1 a menos que se utilice para correo electrónico únicamente.<br /><br />**Equipos con Windows Vista o Windows 7**<br />No se puede restablecer un equipo con Windows 7 o anterior.|

Si tiene alguna pregunta y no encuentra la información de contacto del administrador de TI, vea si aparece en el [sitio web del portal de empresa](http://portal.manage.microsoft.com).

### Consulte también
[Usar un dispositivo Windows con Intune](using-your-windows-device-with-intune.md)

<!--HONumber=Jun16_HO1-->


