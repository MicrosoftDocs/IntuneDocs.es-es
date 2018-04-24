---
title: Instalar la aplicación de portal de empresa para Windows | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 152519d9aa58688538d25f0fb43c0411d4aa6e38
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-windows-device-in-intune"></a>¿Qué ocurre si instala la aplicación de Portal de empresa e inscribe el dispositivo Windows en Intune?

Al instalar la aplicación Portal de empresa y después usarla para inscribir un dispositivo Windows o Windows Phone, lo que hace es permitir que el equipo de soporte técnico de su empresa administre el dispositivo para ayudar a mantener los datos profesionales o académicos seguros. En este tema se explica lo que ocurre con los dispositivos anteriores a Windows 10. Para dispositivos Windows 10, vea el [tema relacionado](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md).

## <a name="what-happens-to-all-windows-devices-after-enrollment"></a>¿Qué ocurre con todos los dispositivos Windows después de la inscripción?
Cuando inscribe un dispositivo Windows o Windows Phone en Intune, puede:

-   Acceder a la red, el correo electrónico y los archivos de trabajo de la empresa.

-   Obtener aplicaciones de empresa desde el sitio web del Portal de empresa. (__Nota__: Para Windows 7 y Windows Vista, solo puede obtener aplicaciones de empresa desde el sitio web del Portal de empresa).

-   Configurar automáticamente la cuenta de correo electrónico profesional o educativa.

-   Restablecer el teléfono a la configuración de fábrica si lo pierde o se lo roban.

Al inscribir el dispositivo, da permiso al equipo de soporte técnico de su empresa para hacer cosas como estas:

-   Restablecer la configuración predeterminada de fábrica del dispositivo. Esto es útil en caso de pérdida o robo del dispositivo.

-   Quitar solo los archivos relacionados con la empresa y las aplicaciones empresariales. *Los datos personales y la configuración no se quitan.*

-   El equipo de soporte técnico de su empresa puede ver el software instalado en el dispositivo, incluido el que usted haya instalado.

-   Establecer requisitos en el dispositivo, como la necesidad de disponer de una contraseña o de un PIN para ayudar a proteger los datos de la empresa. El equipo de soporte técnico de su empresa también puede limitar cuántas veces puede especificar una contraseña incorrecta y podría bloquearle el acceso al dispositivo si se equivoca demasiadas veces.

-   Exigir el cifrado de los datos en el dispositivo para ayudar a proteger los datos de la empresa, en caso de pérdida o robo de su dispositivo.

-   Debe aceptar los términos y condiciones.

-   Impedirle realizar fotos de datos relacionados con la empresa.

## <a name="what-happens-to-all-windows-pcs-after-enrollment"></a>¿Qué ocurre con todos los equipos de Windows después de la inscripción?

-  El software se instalará en el equipo para permitir que el equipo de soporte técnico de su empresa lo administre y para permitirle a usted obtener acceso a recursos de la empresa como aplicaciones e información de soporte técnico. El equipo de soporte técnico de su empresa puede actualizar automáticamente este software.

-  Intune Endpoint Protection puede instalarse en el equipo. Se trata de un software que permite detectar virus y malware.

-  El equipo de soporte técnico de su empresa puede recopilar o eliminar datos de la unidad de disco duro del equipo.

-  El equipo de soporte técnico de su empresa puede instalar aplicaciones y actualizaciones en el equipo.

## <a name="what-happens-every-eight-hours-after-device-enrollment"></a>¿Qué ocurre cada ocho horas después de la inscripción de dispositivo?

Cada ocho horas aproximadamente, los dispositivos inscritos harán lo siguiente:

-   Descargar las actualizaciones de directivas o aplicaciones proporcionadas por el equipo de soporte técnico de su empresa.

-   Enviar actualizaciones de inventario de hardware.

-   Enviar actualizaciones de inventario de aplicaciones de empresa.

Si tiene alguna pregunta, póngase en contacto con el equipo de soporte técnico de su empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
