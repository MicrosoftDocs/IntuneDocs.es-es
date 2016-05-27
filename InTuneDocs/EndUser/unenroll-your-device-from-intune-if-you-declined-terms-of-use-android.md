---
# required metadata

title: Anular la inscripción del dispositivo de Intune si ha rechazado los términos de uso | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Anular la inscripción del dispositivo de Intune si ha rechazado los términos de uso

La mejor forma de anular la inscripción del dispositivo Android es aceptar los términos de uso, iniciar sesión en la aplicación de portal de empresa y después seguir [estas instrucciones](unenroll-your-device-from-intune-android.md) para anular la inscripción. Pero si rechazó los términos de uso al intentar iniciar sesión en la aplicación de portal de empresa, se le impedirá iniciar sesión en dicha aplicación en futuros intentos, por lo que necesita seguir estas instrucciones alternativas para anular la inscripción del dispositivo.

Cuando se desinstala la aplicación Portal de empresa, también se está anulando la inscripción del dispositivo en Intune, lo que significa que el dispositivo ya no podrá tener acceso a recursos de empresa.  Para más información sobre lo que ocurre cuando se anula la inscripción, vea [¿Qué ocurre cuando se anula la inscripción de un dispositivo de Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Para poder desinstalar la aplicación Portal de empresa, debe ir a la opción **Administradores de dispositivos** y desactivar **Portal de empresa**. Los pasos pueden ser algo distintos, en función del dispositivo Android que tenga.

Para anular la inscripción del dispositivo de Intune y desinstalar la aplicación Portal de empresa:

1.  Vaya a **Configuración** &gt; **Seguridad &amp;Bloqueo de pantalla** &gt; **Administradores de dispositivos**.

    Al completar este se anula la inscripción del dispositivo de forma inmediata.

2.  Desactive la casilla de su lado o desactive el **Portal de empresa**.

    Ahora puede desinstalar la aplicación Portal de empresa.


### Consulte también
[Uso de un dispositivo Android con Intune](using-your-android-device-with-intune.md)

<!--HONumber=May16_HO1-->


