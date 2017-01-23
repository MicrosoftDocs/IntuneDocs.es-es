---
title: "¿Qué ocurre si instala la aplicación de Portal de empresa e inscribe el dispositivo Android en Intune? | Microsoft Docs"
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
ms.assetid: d22f5aea-7be4-419b-b51b-a522ca037b69
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: d0e244659f8a78504ffa2a0b8a6579c829e3642b


---


# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-android-device-in-intune"></a>¿Qué ocurre si instala la aplicación de Portal de empresa e inscribe el dispositivo Android en Intune?

Al instalar la aplicación Portal de empresa e inscribir su dispositivo Android en Intune, puede usar la aplicación Portal de empresa para:

-   Acceder a la red, el correo electrónico y los archivos de trabajo de la empresa.

-   Obtener aplicaciones de empresa desde el Portal de empresa.

-   Configurar automáticamente la cuenta de correo electrónico profesional.

-   Restablecer el teléfono a la configuración de fábrica si lo pierde o se lo roban.

Al inscribir un dispositivo Android, da permiso al administrador de TI para acceder a él. El administrador puede hacer cosas como:

-   Restablecer la configuración predeterminada de fábrica del dispositivo. Esto es útil en caso de pérdida o robo del dispositivo.

-   Quitar todos los datos relacionados con la empresa. Los datos personales y la configuración no se quitan.

-   Establecer requisitos en el dispositivo, como la necesidad de disponer de una contraseña o de un PIN para ayudar a proteger los datos de la empresa. El administrador de TI también puede limitar cuántas veces puede especificar una contraseña incorrecta y podría bloquearle el acceso al dispositivo si se equivoca demasiadas veces.

-   Debe aceptar los términos y condiciones.

-   Deshabilitar la cámara (solo en dispositivos Samsung Knox, no en dispositivos Nexus) para evitar que realice fotos de material de trabajo confidencial que no debe compartirse.

-   Exigir el cifrado de todos los datos del dispositivo para ayudar a proteger los datos si dicho dispositivo se pierde o se roba.

Una vez agregado el dispositivo al Portal de empresa, este hará lo siguiente cada ocho horas aproximadamente:

-   Descargar las actualizaciones de directivas o aplicaciones proporcionadas por el administrador de TI.

-   Enviar actualizaciones de inventario de hardware. (Estas actualizaciones no tienen información personal).

-   Enviar actualizaciones de inventario de aplicaciones de empresa. (Estas actualizaciones no tienen información personal).

¿Necesita ayuda? Póngase en contacto con el administrador de TI (visite el [sitio web del Portal de empresa](http://portal.manage.microsoft.com) para obtener la información de contacto), o escriba al [equipo de Microsoft Android](mailto:wintunedroidfbk@microsoft.com).



<!--HONumber=Dec16_HO2-->


