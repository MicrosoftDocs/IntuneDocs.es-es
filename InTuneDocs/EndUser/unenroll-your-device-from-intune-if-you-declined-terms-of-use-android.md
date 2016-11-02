---
title: Unenroll your device from Intune if you declined "Terms of Use" | Microsoft Intune
description: "Describe cómo anular la inscripción de un dispositivo Android de Intune si ha rechazado los términos de uso y no puede iniciar sesión en la aplicación Portal de empresa."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0d32aa982cf9d45da36f71be5554f31375521e35
ms.openlocfilehash: 4f5088bc645fed0451885078f5ab0dcd04a33d81


---


# Anular la inscripción del dispositivo de Intune si ha rechazado los “términos de uso”

La mejor forma de anular la inscripción del dispositivo Android es aceptar los términos de uso, iniciar sesión en la aplicación Portal de empresa y después usar [estas instrucciones](unenroll-your-device-from-intune-android.md) para anular la inscripción. Pero si ha rechazado los términos de uso al intentar iniciar sesión en la aplicación Portal de empresa, no podrá iniciar sesión en dicha aplicación en futuros intentos. En este caso, debe usar estas instrucciones de “solución” para anular la inscripción del dispositivo.

Cuando se desinstala la aplicación Portal de empresa, también se anula la inscripción del dispositivo de Intune. El dispositivo ya no puede acceder a los recursos de la empresa. Para más información sobre lo que ocurre cuando se anula la inscripción, vea [¿Qué ocurre cuando se anula la inscripción de un dispositivo de Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Para poder desinstalar la aplicación Portal de empresa, debe ir a la opción **Administradores de dispositivos** y desactivar **Portal de empresa**. Los pasos pueden ser algo distintos, en función del dispositivo Android que tenga.

Para anular la inscripción del dispositivo de Intune y desinstalar la aplicación Portal de empresa:

1.  Vaya a **Configuración** &gt; **Seguridad &amp; Bloqueo de pantalla** &gt; **Administradores de dispositivos**.

    Al completar este se anula la inscripción del dispositivo de forma inmediata.

2.  Desactive el **Portal de empresa** o la casilla situada a su lado.

    Ahora puede desinstalar la aplicación Portal de empresa.

¿Sigue necesitando ayuda? Póngase en contacto con el administrador de TI (consulte el [sitio web del Portal de empresa](http://portal.manage.microsoft.com) para obtener información de contacto) o escriba al equipo de Microsoft Android en wintunedroidfbk@microsoft.com.



<!--HONumber=Oct16_HO2-->


