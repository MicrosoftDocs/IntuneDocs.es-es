---
title: "¿Qué ocurre si instala la aplicación de Portal de empresa e inscribe el dispositivo Windows en Intune? | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 7/8/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
ROBOTS: noindex,nofollow
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 618e2abda642c3b9b2e813824dfd4235c9309faa
ms.openlocfilehash: 8b6e9b1bbf2d870b57dfcd7cdefefa2550d07d14


---


# ¿Qué ocurre si instala la aplicación de Portal de empresa e inscribe el dispositivo Windows en Intune?

Al instalar la aplicación de Portal de empresa y después usarla para inscribir un dispositivo Windows o Windows Phone, lo que hace es permitir que el administrador de TI administre el dispositivo para mantener los datos profesionales o académicos seguros, tal como se describe a continuación para los dispositivos anteriores a Windows 10. Para más información sobre los dispositivos Windows 10, vea [esta página](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md).

## ¿Qué ocurre con todos los dispositivos Windows después de la inscripción?
Cuando inscribe un dispositivo Windows o Windows Phone en Intune, puede:

-   Acceder a la red, el correo electrónico y los archivos de trabajo de la empresa

-   Obtener aplicaciones de la compañía desde el sitio web de Portal de empresa (para Windows 7 y Vista, puede obtener aplicaciones de la compañía solo desde el sitio web de Portal de empresa)

-   Configurar automáticamente su cuenta de correo electrónico profesional o educativa

-   Restablecer su teléfono a la configuración de fábrica si lo pierde o se lo roban

Al inscribir el dispositivo, da permiso al administrador de TI para hacer cosas como estas:

-   Restablecer la configuración predeterminada de fábrica del dispositivo. Esto es útil en caso de pérdida o robo del dispositivo.

-   Quitar todos los datos relacionados con la empresa y las aplicaciones empresariales que se instalaron. Los datos personales y la configuración no se quitan.

-   El administrador de TI puede realizar un inventario de todo el software instalado en el equipo, incluido el software que usted haya instalado.

-   Exigirle el establecimiento de una contraseña o un PIN para el dispositivo, lo que podría bloquear el dispositivo o restablecer la configuración predeterminada del mismo (operación que podría incluir la eliminación de datos) tras varios intentos incorrectos de introducir la contraseña.

-   Exigir el cifrado de todos los datos del dispositivo, lo que ayuda a proteger los datos si dicho dispositivo se pierde o se roba.

-   Debe aceptar los términos y condiciones.

-   El administrador de TI puede aplicar directivas en el equipo. Por ejemplo, se le podría exigir establecer una contraseña o un PIN en el equipo, lo que podría impedir el acceso al equipo o eliminar todos los datos del disco duro del equipo tras varios intentos incorrectos de introducir la contraseña.

-   Deshabilitar la tarjeta SD.

## ¿Qué ocurre con todos los equipos de Windows después de la inscripción?

-  El software se instalará en su equipo para permitir que el administrador de TI administre el equipo, y para permitirle que obtenga los recursos de la empresa como aplicaciones o información de soporte técnico. El administrador de TI puede actualizar automáticamente este software.

-  Intune Endpoint Protection puede instalarse en su equipo. Se trata de software que permite detectar virus y malware.

-  El administrador de TI puede realizar un inventario de todo el software instalado en el equipo, incluido el software que usted haya instalado.

-  Deberá aceptar los términos y condiciones.

-  El administrador de TI puede recopilar o eliminar datos de la unidad de disco duro del equipo. El administrador de TI también puede eliminar todo el disco duro.

-  El administrador de TI puede instalar aplicaciones y actualizaciones en el equipo.

-  El administrador de TI puede aplicar directivas en el equipo. Por ejemplo, se le podría exigir establecer una contraseña o un PIN en el equipo, lo que podría impedir el acceso al equipo o eliminar todos los datos del disco duro del equipo tras varios intentos incorrectos de introducir la contraseña.


## ¿Qué ocurre cada ocho horas después de la inscripción de dispositivo?
Cada ocho horas aproximadamente, los dispositivos inscritos harán lo siguiente:

-   Descargar las actualizaciones de directivas o aplicaciones proporcionadas por el administrador de TI.

-   Enviar actualizaciones de inventario de hardware.

-   Enviar actualizaciones de inventario de aplicaciones de empresa.

Para obtener los pasos para la inscripción, consulte [Inscriba el dispositivo Windows en Intune](enroll-your-device-in-intune-windows.md). Para más información sobre lo que el administrador de TI puede ver en el dispositivo, vea [¿Qué puede ver mi administrador de TI cuando inscriba el dispositivo en Intune?](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md).

Si tiene alguna pregunta, póngase en contacto con el administrador de TI. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](http://portal.manage.microsoft.com).

### Consulte también
[Usar un dispositivo Windows con Intune](using-your-windows-device-with-intune.md)



<!--HONumber=Jul16_HO4-->


