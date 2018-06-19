---
title: Solución de problemas con la inscripción de dispositivos de Windows 10 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4ab630b6-47ff-443b-a2a5-be23388bcea7
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 97f23594a5c7b047caf37dbaa39c481585a96d76
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31018182"
---
# <a name="troubleshoot-your-windows-10-device-enrollment"></a>Solución de problemas con la inscripción de dispositivos de Windows 10
Si ha seguido los pasos descritos en [Inscribir un dispositivo de escritorio de Windows 10 Mobile o Windows 10 en Intune](enroll-your-w10-phone-or-w10-pc-windows.md), pero todavía no se puede obtener acceso a su correo electrónico profesional o educativo, pruebe estos pasos para solucionar problemas.

1.  Examine las dos pantallas siguientes y encuentre la que sea similar a lo que ve en el dispositivo. Siga los pasos que tienen que ver con la pantalla que verá en el dispositivo.

    Si aparece esta pantalla, siga los pasos de [Pasos de solución de problemas a seguir si ve acceso profesional o educativo](#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).

    ![settings-accounts-access-work-or-school](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    Si aparece esta pantalla, siga los pasos de [Pasos de solución de problemas a seguir si ve su cuenta](#troubleshooting-steps-to-follow-if-you-see-your-account).

    ![settings-accounts-your-account](./media/W10-enroll-2-accounts-your-account.png)

## <a name="troubleshooting-steps-to-follow-if-you-see-access-work-or-school"></a>Pasos de solución de problemas a seguir si ve "Acceso profesional o educativo"

1. Si después de seguir los pasos anteriores, no consigue tener acceso a los archivos y al correo electrónico profesional o educativo, vuelva a **Acceso profesional o educativo**.

2. Realice una de las siguientes acciones:

   - Si ve una conexión similar a la siguiente imagen, selecciónela y, a continuación, compruebe que ve las opciones Administrar, Información y Desconectar. Si ve estas opciones, está inscrito y conectado.

     ![validate-successful-enrollment](./media/w10-enroll-rs1-validate-successful-enrollment.png)

   - Si no ve la información de conexión que se muestra arriba, o la ve, pero carece de algunas de las opciones, seleccione **Conectar**, y, a continuación, inicie sesión con sus credenciales profesionales o educativas. Ahora debe estar conectado.

## <a name="troubleshooting-steps-to-follow-if-you-see-your-account"></a>Pasos de solución de problemas a seguir si ve "Su cuenta"

Si después de seguir los pasos anteriores, no consigue tener acceso al correo, a los archivos y a otros datos laborales o educativos, vuelva a **Cuentas** y pulse **Acceso profesional**.

- Si ve su cuenta profesional o educativa, felicidades. Está conectado.

- Si no la ve, pulse en **Conectar** y luego inicie sesión con sus credenciales laborales o educativas.

## <a name="troubleshooting-steps-to-follow-if-you-see-set-up-a-work-or-school-account"></a>Pasos de solución de problemas a seguir si ve "Configurar una cuenta profesional o educativa"

Si ve un mensaje que dice <strong>No pudimos detectar automáticamente un punto de conexión de administración que coincida con el nombre de usuario escrito. Compruebe su nombre de usuario y vuelva a intentarlo. Si conoce la dirección URL para el punto de conexión de administración, escríbala.</strong>, entonces debe intentar volver a escribir su nombre de usuario y contraseña. Si todavía no funciona, debe consultar con el equipo de soporte técnico de su empresa el sitio web que necesita proporcionar en el cuadro de texto <strong>Punto de conexión de administración</strong>. Este es un sitio web que probablemente tenga este aspecto <strong>www.yourcompany.onmicrosoft.com</strong>.

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
