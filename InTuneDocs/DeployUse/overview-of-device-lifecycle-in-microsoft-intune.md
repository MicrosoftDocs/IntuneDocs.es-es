---
# required metadata

title: Información general sobre el ciclo de vida del dispositivo | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f6051fa7-133f-4712-86a5-e5f5bc5ab3c7

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Información general sobre el ciclo de vida de administración de dispositivos móviles (MDM)

El ciclo de vida del dispositivo de Intune comienza con la inscripción inicial de un dispositivo, se extiende a través de otras fases y termina cuando ya no es necesario.

![Ciclo de vida del dispositivo](./media/devicelifecycle_nobg.png "the Intune device lifecycle")

## Inscribir
Las estrategias de administración de dispositivos móviles (MDM) de hoy en día se aplican a una serie de teléfonos, tabletas y equipos (iOS, Android, Windows y Mac OS X). Si tiene que administrar el dispositivo, que suele ser el caso de los dispositivos corporativos, el primer paso es [configurar la inscripción del dispositivo](enroll-devices-in-microsoft-intune.md). También puede administrar equipos Windows si los inscribe en Intune (MDM) o [instala el software cliente de Intune](manage-windows-pcs-with-microsoft-intune.md).

## Configurar
La inscripción de los dispositivos es solo el primer paso. Para aprovechar todas las posibilidades que Intune ofrece y asegurarse de que los dispositivos sean seguros y conformes con los estándares de la empresa, puede elegir entre una amplia gama de **directivas** que permiten configurar prácticamente todos los aspectos del funcionamiento de los dispositivos administrados. Por ejemplo, si los usuarios deben tener contraseñas en los dispositivos que contienen datos empresariales. Puede hacer que sea necesario disponer de una. ¿Tiene Wi-Fi corporativa? Puede configurarla automáticamente. Estos son los tipos de opciones de configuración disponibles:

- [**Directivas de configuración**](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md): estas directivas permiten configurar el funcionamiento de las características y las funcionalidades de los dispositivos administrados. Por ejemplo, se podría exigir el uso de una contraseña en Windows Phone o deshabilitar el uso de la cámara en dispositivos iPhone.
- [**Directivas de acceso a recursos de la empresa**](enable-access-to-company-resources-with-microsoft-intune.md): el hecho de permitir a los usuarios acceder al trabajo desde sus dispositivos personales puede plantear retos. Por ejemplo, ¿cómo se garantiza que todos los dispositivos que necesitan acceder al correo electrónico de la empresa estén configurados correctamente? ¿Cómo se puede garantizar que los usuarios puedan acceder a la red corporativa con una conexión VPN sin tener que conocer los valores necesarios, que a menudo son complejos? Intune puede ayudar a reducir esta carga; para conseguirlo, configura automáticamente los dispositivos administrados para acceder a recursos comunes de la empresa.
- [**Directivas de administración de equipos Windows (con el software cliente de Intune)**](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md): aunque la inscripción de los equipos Windows con Intune ofrece el máximo de funcionalidades de administración de dispositivos, Intune sigue siendo compatible con la administración de equipos Windows con el software cliente de Intune. Si necesita información sobre algunas de las tareas que puede realizar con los equipos, empiece aquí.

## Proteger
En el actual sector de las TI, la protección de los dispositivos frente al acceso no autorizado es una de las tareas más importantes que se realiza. Además de los elementos del paso **Configurar** del ciclo de vida del dispositivo, Intune proporciona más funcionalidades que ayudan a proteger los dispositivos que se administran frente al acceso no autorizado o a los ataques malintencionados:
- [**Autenticación multifactor**](protect-windows-devices-with-multi-factor-authentication.md): la presencia de una capa adicional de autenticación para inicios de sesión de usuario puede ayudar a proteger aún más los dispositivos. Los dispositivos Windows, Windows Phone y Windows Mobile ofrecen autenticación multifactor, que exige un segundo nivel de autenticación, como una llamada de teléfono o un mensaje de texto, para que los usuarios puedan acceder.
- [**Configuración de Microsoft Passport**](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md): Microsoft Passport es un método alternativo de inicio de sesión que permite a los usuarios usar un *gesto*, como una huella digital, o Windows Hello para iniciar una sesión sin necesidad de una contraseña.
- [**Directivas para proteger equipos Windows (con el software cliente de Intune)**](policies-to-protect-windows-pcs-in-microsoft-intune.md): al administrar equipos Windows con el software cliente de Intune, hay disponibles directivas que permiten controlar la configuración de Endpoint Protection, de las actualizaciones de software y de Firewall de Windows en los equipos que administra.

## Retirar
Cuando un dispositivo se pierde o es robado, cuando es necesario reemplazarlo o cuando el usuario cambia de cargo en la empresa, suele ser necesario [retirar o borrar](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) el dispositivo. Hay varias maneras de hacerlo, como restablecer el dispositivo, quitarlo de la administración o borrar los datos corporativos que contiene.


<!--HONumber=May16_HO1-->


