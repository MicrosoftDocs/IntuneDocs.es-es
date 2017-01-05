---
title: "¿Qué ocurre si restablece el dispositivo Windows mediante el Portal de empresa? | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1ee6e275-d1ec-4da3-bbef-d5da2c61a02a
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: cc2800d11bc36b4414f9b76587e3c4bf751d3224


---


# <a name="what-happens-if-you-reset-your-windows-device-using-the-company-portal"></a>¿Qué ocurre si restablece el dispositivo Windows mediante el Portal de empresa?

Cuando usa la aplicación del Portal de empresa o el [sitio web del Portal de empresa](reset-your-device-cpwebsite.md) para restablecer el dispositivo Windows, restablece el dispositivo a la configuración de fábrica y elimina todas las aplicaciones, configuración y datos, incluidos los datos personales. Lo que sucede en cada dispositivo depende del tipo y del empleo del mismo, como se describe en la tabla siguiente. Para obtener instrucciones sobre cómo restablecer el dispositivo perdido o robado, vea [Restablecer (borrar) el dispositivo perdido o robado](reset-erase-your-lost-or-stolen-device-windows.md).

|Administración y configuración de dispositivos|Tipo de dispositivo|
|---------------------------------------|---------------|
|El administrador de TI administra el dispositivo móvil|**Windows 10 y Windows Phone 8.1**</br>El dispositivo ya no aparecerá en el Portal de empresa y este intentará restablecerlo a la configuración predeterminada del fabricante. Se eliminarán los datos personales, las aplicaciones y la configuración. <br /><br />**Windows 10 Mobile**</br>La única forma de anular la inscripción del dispositivo es restablecerlo.|
|El dispositivo solo puede acceder al correo electrónico de la empresa|**Windows Phone 8.1**<br />El dispositivo ya no aparecerá en el Portal de empresa y se eliminarán la cuenta de correo corporativa y los mensajes sin guardar.<br /><br />**Windows 7 o Windows Vista**<br />No se puede restablecer un equipo con Windows 7 o anterior que solo se use para el correo electrónico.<br /><br />**Windows 8.1 y Windows 8**<br />El dispositivo ya no aparecerá en el Portal de empresa y se eliminarán la cuenta de correo corporativa y los mensajes sin guardar.|
|PCs y portátiles|**Windows 8.1 y Windows 8**<br />No se puede restablecer un equipo con Windows 8 o Windows 8.1 a menos que solo se use para el correo electrónico.<br /><br />**Windows 7 o Windows Vista**<br />No se puede restablecer un equipo con Windows 7 o anterior.|

Si tiene alguna pregunta, póngase en contacto con el administrador de TI. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).



<!--HONumber=Dec16_HO2-->


