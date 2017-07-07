---
title: "Información general sobre el ciclo de vida de MDM"
description: "Obtenga información sobre cómo Intune le ayuda a administrar dispositivos a lo largo de su ciclo de vida desde la inscripción, pasando por la configuración, hasta su posible retirada."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6051fa7-133f-4712-86a5-e5f5bc5ab3c7
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7a2eab6ece5628598a7b5a5f9414aa43abc60d69
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="overview-of-the-mobile-device-management-mdm-lifecycle"></a>Información general sobre el ciclo de vida de administración de dispositivos móviles (MDM)

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Todos los dispositivos que administra tienen lo que llamamos un *ciclo de vida*. Intune puede ayudarle a administrar su ciclo de vida desde la inscripción, pasando por la configuración y la protección, hasta la retirada del dispositivo cuando ya no sea necesario:

![El ciclo de vida del dispositivo](./media/device-lifecycle.png "el ciclo de vida del dispositivo de Intune")

## <a name="enroll"></a>Inscribir
Las estrategias de administración de dispositivos móviles (MDM) de hoy en día se aplican a una serie de teléfonos, tabletas y equipos (iOS, Android, Windows y Mac OS X). Si tiene que administrar el dispositivo, lo que suele ser el caso de los dispositivos corporativos, el primer paso es [configurar la inscripción del dispositivo](device-enrollment.md) ([Portal clásico](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)). También puede administrar equipos Windows si los inscribe con Intune (MDM) o [instala el software cliente de Intune](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune).

## <a name="configure"></a>Configurar
La inscripción de los dispositivos es solo el primer paso. Para aprovechar todas las posibilidades que ofrece Intune y asegurarse de que los dispositivos sean seguros y conformes con los estándares de la empresa, puede elegir entre una amplia gama de directivas. Estas permiten configurar prácticamente todos los aspectos del funcionamiento de los dispositivos administrados. Por ejemplo, si los usuarios deben tener contraseñas en los dispositivos que contienen datos empresariales. Puede hacer que sea necesario disponer de una. ¿Tiene Wi-Fi corporativa? Puede configurarla automáticamente. Estos son los tipos de opciones de configuración disponibles:

- [**Configuración del dispositivo** ](device-profiles.md) ([Portal clásico](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)). Estas directivas permiten configurar las características y las funcionalidades de los dispositivos administrados. Por ejemplo, se podría exigir el uso de una contraseña en Windows Phone o deshabilitar el uso de la cámara en dispositivos iPhone.
- [**Acceso a los recursos de la empresa** ](device-profiles.md) ([Portal clásico](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune)). El hecho de permitir a los usuarios acceder al trabajo desde sus dispositivos personales puede plantear retos. Por ejemplo, ¿cómo se garantiza que todos los dispositivos que necesitan acceder al correo electrónico de la empresa estén configurados correctamente? ¿Cómo se puede garantizar que los usuarios puedan tener acceso a la red corporativa con una conexión VPN si no conocen valores complejos? Intune puede ayudar a reducir esta carga; para conseguirlo, configura automáticamente los dispositivos administrados para acceder a recursos comunes de la empresa.
- [**Directivas de administración de equipos Windows (con el software cliente de Intune)**](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client). Aunque la inscripción de los equipos Windows con Intune ofrece el máximo de funcionalidades de administración de dispositivos, Intune sigue siendo compatible con la administración de equipos Windows con el software cliente de Intune. Si necesita información sobre algunas de las tareas que puede realizar con los equipos, empiece aquí.

## <a name="protect"></a>Proteger
En el actual sector de las TI, la protección de los dispositivos frente al acceso no autorizado es una de las tareas más importantes que se realiza. Además de los elementos del paso **Configurar** del ciclo de vida del dispositivo, Intune proporciona más funcionalidades que ayudan a proteger los dispositivos que se administran frente al acceso no autorizado o a los ataques malintencionados:
- [**Autenticación multifactor**](/intune-classic/deploy-use/protect-your-devices-with-microsoft-intune). La presencia de una capa adicional de autenticación para inicios de sesión de usuario puede ayudar a proteger aún más los dispositivos. Muchos dispositivos admiten la autenticación multifactor, que exige un segundo nivel de autenticación, como una llamada de teléfono o un mensaje de texto, para que los usuarios puedan acceder.
- [**Configuración de Windows Hello para empresas**](windows-hello.md) ([Portal clásico](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)). Windows Hello para empresas es un método alternativo de inicio de sesión que permite a los usuarios usar un *gesto*, como una huella digital o Windows Hello, para iniciar sesión sin necesidad de una contraseña.
- [**Directivas para proteger equipos Windows (con el software cliente de Intune)**](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune). Al administrar equipos Windows con el software cliente de Intune, hay disponibles directivas que permiten controlar la configuración de Endpoint Protection, de las actualizaciones de software y de Firewall de Windows en los equipos que administra.

## <a name="retire"></a>Retirar
Cuando un dispositivo se pierde o es robado, cuando es necesario reemplazarlo o cuando el usuario cambia de cargo en la empresa, suele ser necesario [retirarlo o borrarlo](device-management.md) ([Portal clásico](/intune-classic/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune)). Hay varias maneras de hacerlo, como restablecer el dispositivo, quitarlo de la administración o borrar los datos corporativos que contiene.
