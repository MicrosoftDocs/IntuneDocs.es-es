---
title: "Anulación de la inscripción del dispositivo si ha rechazado los términos de uso | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
searchScope:
- User help
ROBOTS: 
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 5207bab5994cc7fc5c23bee92cbe675644d27e97
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="unenroll-your-device-if-you-declined-terms-of-use"></a>Anular la inscripción del dispositivo si ha rechazado los "Términos de uso"

La mejor forma de anular la inscripción del dispositivo Android es aceptar los términos de uso, iniciar sesión en la aplicación Portal de empresa y después usar [estas instrucciones](unenroll-your-device-from-intune-android.md) para anular la inscripción. Pero si rechazó los términos de uso al intentar iniciar sesión en la aplicación del Portal de empresa, se le impedirá iniciar sesión en dicha aplicación en futuros intentos, por lo que necesita seguir estas instrucciones alternativas para anular la inscripción del dispositivo.

Cuando se desinstala la aplicación Portal de empresa, también se anula la inscripción del dispositivo de Intune. El dispositivo ya no puede acceder a los recursos de la empresa. Para más información sobre lo que ocurre cuando se anula la inscripción, vea [¿Qué ocurre cuando se anula la inscripción de un dispositivo de Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Para poder desinstalar la aplicación Portal de empresa, debe ir a la opción **Administradores de dispositivos** y desactivar **Portal de empresa**. Los pasos pueden ser algo distintos, en función del dispositivo Android que tenga.

Para anular la inscripción del dispositivo de Intune y desinstalar la aplicación Portal de empresa:

1.  Vaya a **Configuración** &gt; **Seguridad &amp; Bloqueo de pantalla** &gt; **Administradores de dispositivos**.

    Al completar este se anula la inscripción del dispositivo de forma inmediata.

2.  Desactive el **Portal de empresa** o la casilla situada a su lado.

    Ahora puede desinstalar la aplicación Portal de empresa.

¿Sigue necesitando ayuda? Póngase en contacto con el equipo de soporte técnico de su empresa (visite el [sitio web del Portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog) para obtener la información de contacto), o escriba al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having unenrolling my Android device&body=Describe the issue you're experiencing here.">equipo de Microsoft Android</a>.
