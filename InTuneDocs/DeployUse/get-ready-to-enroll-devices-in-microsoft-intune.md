---
# required metadata

title: Preparar la inscripción de dispositivos en Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Preparar la inscripción de dispositivos en Microsoft Intune
Para permitir que los empleados inscriban dispositivos móviles (incluidos Android, iOS, Windows Phone y equipos con Windows) con Intune, debe habilitar la inscripción de dispositivos. Para permitir la inscripción, debe establecer una entidad de administración de dispositivos móviles, configurar el Portal de empresa de Intune, asignar licencias y habilitar la asignación para la plataforma de dispositivos.

## <a name="BKMK_Set_MDM_Authority"></a>Establecer la entidad de administración de dispositivos móviles
La entidad de MDM define el servicio de administración que tiene permiso para administrar un conjunto de dispositivos. Las opciones para la entidad de MDM incluyen Intune y Configuration Manager con Intune. Si establece Configuration Manager como la entidad de administración, ningún otro servicio podrá usarse para la administración de dispositivos móviles.

>[!IMPORTANT]
> Considere detenidamente si quiere administrar los dispositivos móviles solo mediante Intune (servicio en línea) o mediante System Center Configuration Manager con Intune (solución de software local junto con el servicio en línea). Una vez que establezca la entidad de administración de dispositivos móviles, esta no se puede cambiar.



1.  En la [consola de administración de Microsoft Intune](http://manage.microsoft.com), haga clic en **Administrador** &gt; **Administración de dispositivos móviles**..

2.  En la lista **Tareas** , haga clic en **Configurar entidad de administración de dispositivos móviles**. Se abre el cuadro de diálogo **Establecer entidad de administración de dispositivos móviles** .

    ![Cuadro de diálogo Establecer entidad de MDM](../media/intune-mdm-authority.png)

3.  Intune solicita confirmación de que desea que Intune sea su entidad de MDM. Active la casilla y haga clic en **Sí** si desea utilizar Microsoft Intune para administrar dispositivos móviles.

## Configurar el Portal de empresa de Intune y asignar licencias
Con el Portal de empresa de Intune, es más fácil para los usuarios acceder a los recursos de la empresa (como por ejemplo, aplicaciones), buscar información de soporte técnico e inscribir o cancelar la inscripción de dispositivos. Antes de inscribir dispositivos debería [configurar el Portal de empresa](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-7). También debe [asignar licencias de usuario](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-4) para permitir el acceso a Intune.

## Configurar la administración de dispositivos
Después de configurar la entidad de MDM, debe configurar la administración de dispositivos para los sistemas operativos que su organización quiere admitir. Los pasos necesarios para configurar la administración de dispositivos varían según el sistema operativo. Por ejemplo, Android OS no necesita que haga nada en la consola de administración de Intune. Por otro lado, Windows y iOS necesitan una relación de confianza entre los dispositivos e Intune para permitir la administración.

> [!div class="op_single_selector"]
- [Configurar la administración de Android con Microsoft Intune](set-up-android-management-with-microsoft-intune.md)
- [Set up iOS and Mac management with Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Configurar la administración de Windows Phone con Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md)
- [Configurar la administración de dispositivos Windows con Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md)

También puede llevar a cabo lo siguiente:
 - Usar la [cuenta de administrador de inscripción de dispositivos](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) para inscribir muchos dispositivos
 - [Especificar los dispositivos propiedad de la empresa mediante los números del IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) para ayudar en la inscripción de dispositivos y de la directiva de destino


<!--HONumber=May16_HO1-->


