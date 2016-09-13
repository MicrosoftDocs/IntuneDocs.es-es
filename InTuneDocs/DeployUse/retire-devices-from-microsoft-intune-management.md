---
title: Retirar dispositivos | Microsoft Intune
description: "Intune admite una eliminación selectiva y una eliminación completa para quitar el dispositivo de administración de Intune mediante la eliminación de la directiva y el portal de empresa."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cf471320f122eea7804ff6cd6cad208f8cd5a692
ms.openlocfilehash: 29d13dcbc367c18d64f9522fa9a3b962226feebb


---

# Retirar dispositivos de la administración de Intune

Llega un momento en que es necesario eliminar un dispositivo administrado de la administración de Intune, tanto si se trata de un dispositivo personal como propiedad de la empresa. Es posible que un dispositivo tenga que retirarse por una serie de motivos:

-   El usuario deja una organización de manera planeada (partida "administrada")
-   El usuario la deja repentinamente (se le despide, se va, etc.).
-   Pérdida del dispositivo
-   Reasignación de un dispositivo (trasladar a otro usuario, volver a utilizar para un propósito diferente, etc.).

Puede realizar un borrado selectivo o completo en los dispositivos administrados como dispositivos móviles o bloquearlo y restablecer la contraseña. Si limpia el dispositivo, libera la suscripción del usuario para agregar un dispositivo diferente. También puede retirar los PC administrados con software cliente de Intune.

## Borrar datos y aplicaciones de dispositivos
Tanto el borrado selectivo como el borrado completo quitan el dispositivo de la administración de Intune. Para ello, quitan su directiva y el portal de empresa, lo que significa que el dispositivo ya no tiene las credenciales necesarias para iniciar sesión en los recursos de la empresa, como Microsoft SharePoint, el correo electrónico u Office 365.

El [borrado selectivo](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) es la acción preferida para los empleados que inscribieron sus propios dispositivos en Intune, porque no afecta a la información personal del dispositivo. Solo se quitan los datos corporativos.

En el caso de los dispositivos que deban reasignarse, también puede usar un [borrado completo](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe), que restablece el dispositivo a la configuración predeterminada de fábrica.

## Eliminar dispositivos en el portal de Azure Active Directory

1.  Inicie sesión con sus credenciales de la organización en [http://aka.ms/accessaad](http://aka.ms/accessaad) o en [https://portal.office.com](https://portal.office.com) y, después, elija **Centros de administración** &gt; **Azure AD**.

2.  Cree una suscripción de Azure si no tiene una. Si tiene una cuenta de pago, no necesitará una tarjeta de crédito ni realizar ningún pago (seleccione el vínculo de suscripción **Registre su suscripción gratuita de Azure Active Directory**).

4.  Seleccione **Active Directory** y, a continuación, seleccione su empresa.

5.  Seleccione la pestaña **Usuarios** .

6.  Seleccione el usuario cuyos dispositivos desea eliminar.

7.  Seleccione **Dispositivos**.

8.  Seleccione los dispositivos según corresponda y elija **Eliminar dispositivo**. El dispositivo se eliminará la próxima vez que se sincronice con Active Directory. Esto suele producirse al cabo de 4 horas. Después de la sincronización, el dispositivo se elimina de la administración. Con este proceso, se elimina un dispositivo del límite de dispositivos de este usuario.

## Retirar equipos administrados
Se pueden eliminar de la administración equipos administrados con el software cliente de Intune desde la consola de administración de Intune. De esta forma, también se desinstala el software cliente y se elimina del equipo la directiva de Intune. Vea información sobre cómo [retirar equipos administrados con el software cliente de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md).

## Bloquear el acceso a un dispositivo
Si se ha perdido un dispositivo o si se debe retirar un dispositivo porque un empleado ha abandonado la empresa sin devolver el hardware propiedad de la empresa, puede [restablecer el código de acceso y bloquear de forma remota](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) el dispositivo. Esto impide que la información de la empresa se use incorrectamente, aunque puede que tenga que cancelar el dispositivo por pérdida.

También querrá revocar la licencia de la cuenta de usuario de Intune del empleado. Esto hace que se libere la licencia para poder asignarla a una cuenta de usuario nueva.

## Retirar hardware
A veces, es el propio dispositivo el que llega al final del ciclo de vida. En tales casos, al [restablecer el dispositivo a la configuración de fábrica](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) con un borrado completo, se quitan todos los datos y se elimina el dispositivo de Intune. Luego, puede deshacerse del hardware según las directivas de su empresa.

### Consulte también
[Ayudar a proteger los datos con un borrado selectivo o completo](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Aug16_HO4-->


