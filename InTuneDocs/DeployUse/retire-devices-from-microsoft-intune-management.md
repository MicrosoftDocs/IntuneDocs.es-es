---
title: Retirar dispositivos | Microsoft Intune
description: "Intune admite una eliminación selectiva y una eliminación completa para quitar el dispositivo de administración de Intune mediante la eliminación de la directiva y el portal de empresa."
keywords: 
author: staciebarker
ms.author: staciebarker
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
ms.sourcegitcommit: b76e9e16ef1fa6870783326630ae74d07ae59cbb
ms.openlocfilehash: be3a30535fc9cebad5d4a167b75c484ddafd7f85


---

# <a name="retire-devices-from-intune-management"></a>Retirar dispositivos de la administración de Intune

Al final es necesario eliminar un dispositivo administrado de la administración de Intune, tanto si se trata de un dispositivo personal como propiedad de la empresa. Es posible que tenga que retirar un dispositivo por una serie de motivos:

-   El usuario deja una organización de manera planeada (partida "administrada").
-   El usuario la deja repentinamente (se le despide, se va, etc.).
-   Pérdida del dispositivo.
-   Reasignación de un dispositivo (entrega a otro usuario, uso para otro propósito, etc.).

Puede realizar un borrado selectivo o completo en un dispositivo administrado como dispositivo móvil, o puede bloquearlo y restablecer la contraseña. Si borra el dispositivo, libera la suscripción del usuario para agregar otro dispositivo. También puede retirar los equipos administrados con el software cliente de Intune.

## <a name="wipe-data-and-apps-from-devices"></a>Borrar datos y aplicaciones de dispositivos
Tanto la eliminación selectiva como la completa quitan el dispositivo de la administración de Intune mediante la eliminación de su directiva y el Portal de empresa. Como resultado, el dispositivo ya no tiene las credenciales necesarias para iniciar sesión en recursos de la empresa como Microsoft SharePoint, el correo electrónico u Office 365.

El [borrado selectivo](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) es la acción preferida para los empleados que inscribieron sus propios dispositivos en Intune, porque no afecta a la información personal del dispositivo. Solo se quitan los datos corporativos.

En el caso de los dispositivos que deban reasignarse, también puede usar un [borrado completo](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe), que restablece el dispositivo a la configuración predeterminada de fábrica.

## <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>Eliminar dispositivos en el portal de Azure Active Directory

1.  Inicie sesión con las credenciales de la organización en [http://aka.ms/accessaad](http://aka.ms/accessaad) o en [https://portal.office.com](https://portal.office.com) y después elija **Centros de administración** &gt; **Azure AD**.

2.  Si no tiene ninguna, cree una suscripción de Azure. Si tiene una cuenta de pago, no debería necesitar tarjeta de crédito ni pago alguno. Elija el vínculo de suscripción **Registrar Azure Active Directory gratuito**.

4.  Elija **Active Directory** y luego elija su empresa.

5.  Elija la pestaña **Usuarios**.

6.  Elija el usuario cuyos dispositivos quiere eliminar.

7.  Seleccione **Dispositivos**.

8.  Elija los dispositivos según corresponda y, luego, **Eliminar dispositivo**. El dispositivo se eliminará la próxima vez que se sincronice con Active Directory. Esto suele producirse al cabo de cuatro horas. Después de la sincronización, el dispositivo se elimina de la administración. Con este proceso, se elimina un dispositivo del límite de dispositivos de este usuario.

## <a name="retire-managed-computers"></a>Retirar equipos administrados
Se pueden eliminar de la administración equipos administrados con el software cliente de Intune en la consola de administración de Intune. De esta forma también se desinstala el software cliente y se elimina del equipo la directiva de Intune. Vea información sobre cómo [retirar equipos administrados con el software cliente de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md).

## <a name="block-access-a-device"></a>Bloquear el acceso a un dispositivo
Si se ha perdido un dispositivo o si se debe retirar porque un empleado ha abandonado la empresa sin devolver un hardware propiedad de la misma, puede [restablecer el código de acceso y bloquear de forma remota](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) el dispositivo. Esto impide que la información de la empresa se use incorrectamente, aunque puede que tenga que cancelar el dispositivo por pérdida.

También querrá revocar la licencia de la cuenta de usuario de Intune del empleado. Esto hace que se libere la licencia para poder asignarla a una cuenta de usuario nueva.

## <a name="retire-hardware"></a>Retirar hardware
A veces, es el propio dispositivo el que llega al final del ciclo de vida. En tales casos, al [restablecer el dispositivo a la configuración de fábrica](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) con un borrado completo, se quitan todos los datos y se elimina el dispositivo de Intune. Luego, puede deshacerse del hardware según las directivas de la empresa.

### <a name="see-also"></a>Consulte también
[Ayudar a proteger los datos con un borrado selectivo o completo](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)



<!--HONumber=Nov16_HO3-->


