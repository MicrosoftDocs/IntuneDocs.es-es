---
title: Retirar dispositivos | Microsoft Intune
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: c06f1fc1168b0dde515eaa82d15095ec4d73d1cf


---

# Retirar dispositivos de la administración de Intune

Llega un momento en que es necesario retirar un dispositivo administrado de la administración de Intune, tanto si se trata de un dispositivo personal como propiedad de la empresa. La retirada de dispositivos es relativamente sencilla; para ello, deberá realizar un borrado selectivo o completo.
## Borrar datos y aplicaciones de dispositivos
Tanto el borrado selectivo como el borrado completo quitan el dispositivo de la administración de Intune. Para ello, quitan su directiva y el portal de empresa, lo que significa que el dispositivo ya no tiene las credenciales necesarias para iniciar sesión en los recursos de la empresa, como Microsoft SharePoint, el correo electrónico u Office 365.

El [borrado selectivo](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) es la acción preferida para los empleados que inscribieron sus propios dispositivos en Intune, porque no afecta a la información personal del dispositivo. Solo se quitan los datos corporativos.

En el caso de los dispositivos de empresa, también puede usar un [borrado completo](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe), que restablece el dispositivo a la configuración de fábrica.

## Revocar el acceso a la red de empresa
En el caso de que quiera retirar un dispositivo porque un empleado ha abandonado la empresa y no ha devuelto el hardware de la empresa, puede [bloquear de forma remota](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) el dispositivo. Esto impide que la información y el hardware de la empresa se usen incorrectamente, aunque puede que tenga que cancelar el dispositivo por pérdida.

También querrá revocar la licencia de la cuenta de usuario de Intune del empleado. Esto hace que se libere la licencia para poder asignarla a una cuenta de usuario nueva.

## Retirar hardware
A veces, es el propio dispositivo el que llega al final del ciclo de vida. En tales casos, al [restablecer el dispositivo a la configuración de fábrica](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) con un borrado completo, se quitan todos los datos y se elimina el dispositivo de Intune. Luego, puede deshacerse del hardware según las directivas de su empresa.

### Consulte también
[Ayudar a proteger los datos con un borrado selectivo o completo](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


