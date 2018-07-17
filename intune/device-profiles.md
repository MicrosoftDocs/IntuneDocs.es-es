---
title: Perfiles de dispositivo en Microsoft Intune - Azure | Microsoft Docs
description: Información general de los distintos perfiles de dispositivo de Microsoft Intune, incluidas características, restricciones, correo electrónico, Wi-Fi, VPN, educación, certificados, actualización de Windows 10, BitLocker y Windows Defender, Windows Information Protection y ajustes de configuración de dispositivos personalizada en Azure Portal. Use estos perfiles para administrar y proteger los datos y los dispositivos de su empresa.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f241c5bece72b44a6bd3c9047b5997bcd8879ec5
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905196"
---
# <a name="what-are-microsoft-intune-device-profiles"></a>¿Qué son los perfiles de dispositivo de Microsoft Intune?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune incluye valores de configuración y características que puede habilitar o deshabilitar en distintos dispositivos dentro de su organización. Estos valores de configuración y características se administran mediante perfiles. Estos son algunos ejemplos de perfiles: 

- Un perfil de Wi-Fi que proporciona a distintos dispositivos acceso a su Wi-Fi corporativa
- Un perfil de VPN que proporciona a distintos dispositivos acceso a su servidor VPN dentro de su red corporativa

En este artículo se proporciona una introducción a los distintos perfiles que puede crear para los dispositivos. Use estos perfiles para habilitar o deshabilitar algunas características en los dispositivos.

## <a name="before-you-begin"></a>Antes de comenzar
Para ver las características disponibles, abra [Azure Portal](https://portal.azure.com) y el recurso de Intune. 

En la **Configuración del dispositivo** se incluyen las siguientes opciones:

- **Información general**: muestra el estado de los perfiles y proporciona detalles adicionales sobre los perfiles que ha asignado a usuarios y dispositivos.
- **Administrar**: cree perfiles de dispositivo y cargue [scripts de PowerShell](intune-management-extension.md) personalizados para que se ejecuten en el perfil.
- **Monitor**: compruebe el estado de un perfil para ver si es correcto o erróneo, y consulte registros sobre los perfiles.
- **Programa de instalación**: agregue una entidad de certificación (SCEP o PFX) o habilite la administración de gastos de telecomunicaciones en el perfil.

## <a name="create-the-profile"></a>Creación del perfil

En [Creación de perfiles de dispositivo](device-profile-create.md) se proporciona una guía paso a paso para crear un perfil. 

## <a name="device-features---ios-and-macos"></a>Características de dispositivos: iOS y Mac OS

Las [características del dispositivo](device-features-configure.md) controlan las características de dispositivos iOS y macOS, como configuraciones de AirPrint, notificaciones y dispositivos compartidos.

Esta característica es compatible con:
- iOS 
- macOS

## <a name="device-restrictions"></a>Restricciones de dispositivos
Las [restricciones de dispositivos](device-restrictions-configure.md) controlan la seguridad, el hardware, el uso compartido de datos y otras opciones de configuración de los dispositivos. Por ejemplo, cree un perfil de restricción de dispositivos que impida que los usuarios de dispositivos iOS usen la cámara del dispositivo. 

Esta característica es compatible con:

- Android
- iOS
- macOS
- Windows 10
- Windows 10 Team

## <a name="endpoint-protection"></a>Endpoint Protection
La [configuración de Endpoint Protection para Windows 10](endpoint-protection-windows-10.md) configura los valores de BitLocker y Windows Defender para dispositivos Windows 10.

Para incorporar Protección contra amenazas avanzada de Windows Defender (WDATP) a Microsoft Intune, vea [Configure endpoints using Mobile Device Management (MDM) tools](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection) (Configuración de los puntos de conexión mediante las herramientas de Administración de dispositivos móviles (MDM)).

Esta característica es compatible con:
- Windows 10 y versiones posteriores

## <a name="kiosk"></a>Pantalla completa

En el perfil de [configuración de quiosco](kiosk-settings.md) se configura un dispositivo para ejecutar una o varias aplicaciones. También puede personalizar otras características en el quiosco, como un menú de inicio y un explorador web.

Esta característica es compatible con:
- Windows 10 y versiones posteriores

## <a name="email"></a>Correo electrónico
El perfil de [configuración de correo electrónico](email-settings-configure.md) crea, asigna y supervisa la configuración de correo electrónico de Exchange ActiveSync en los dispositivos. Los perfiles de correo electrónico ayudan a garantizar la coherencia, reducen las llamadas al soporte técnico y permiten a los usuarios finales acceder al correo electrónico de la empresa en sus dispositivos personales sin necesidad de ninguna configuración por su parte. 

Esta característica es compatible con: 

- Android
- iOS
- Windows Phone 8,1
- Windows 10

## <a name="vpn"></a>VPN
La [configuración de VPN](vpn-settings-configure.md) asigna perfiles de VPN a usuarios y dispositivos de la organización para que puedan conectarse a la red de forma fácil y segura. 

Las redes privadas virtuales (VPN) ofrecen a los usuarios un acceso remoto seguro a la red de la empresa. Dispositivos que usan un perfil de conexión VPN para iniciar una conexión con el servidor VPN. 

Esta característica es compatible con: 

- Android
- iOS
- macOS
- Windows Phone 8,1
- Windows 8.1
- Windows 10

## <a name="wi-fi"></a>Wi-Fi
La [configuración de Wi-Fi](wi-fi-settings-configure.md) asigna valores de configuración de red inalámbrica a los usuarios y los dispositivos. Al asignar un perfil de Wi-Fi, los usuarios obtienen acceso a su red Wi-Fi corporativa sin tener que configurarla ellos mismos. 

Esta característica es compatible con: 

- Android
- iOS
- macOS
- Windows 8.1 (solo importación)

## <a name="education"></a>Education
En [Configuración de los ajustes de educación de Windows 10 en Microsoft Intune](education-settings-configure.md) se configuran opciones para la [aplicación Take a Test de Windows](https://education.microsoft.com/gettrained/win10takeatest). Al configurar estas opciones, no puede ejecutar ninguna otra aplicación en el dispositivo hasta que se complete la prueba.

En [Configuración del entorno educativo de Intune para dispositivos iPad compartidos](education-settings-configure-ios-shared.md) se usa la aplicación Classroom de iOS para ayudar a los profesores a guiar el aprendizaje y controlar los dispositivos de los alumnos en el aula. Puede configurar dispositivos iPad para que varios alumnos puedan compartir un solo dispositivo.

## <a name="edition-upgrade"></a>Actualización de la edición
Las [actualizaciones de la edición de Windows 10](edition-upgrade-configure-windows-10.md) actualizan automáticamente dispositivos que ejecutan algunas versiones de Windows 10 a una edición más reciente.

Esta característica es compatible con: 
- Windows 10 y versiones posteriores

## <a name="update-policies"></a>Directivas de actualización
En [Configurar directivas de actualización de iOS en Microsoft Intune](software-updates-ios.md) se muestra cómo crear y asignar directivas de iOS para instalar actualizaciones de software en dispositivos iOS. También puede revisar el estado de la instalación.

Esta característica es compatible con:
- iOS

## <a name="certificates"></a>Certificados
El perfil de [certificados](certificates-configure.md) configura certificados SCEP y PKCS de confianza que se pueden asignar a dispositivos y usarse para la autenticación de perfiles de Wi-Fi, VPN y correo electrónico.

Esta característica es compatible con: 

- Android
- iOS
- Windows Phone 8,1
- Windows 8.1
- Windows 10

## <a name="windows-information-protection-profile"></a>Perfil de Windows Information Protection
[Windows Information Protection](windows-information-protection-configure.md) contribuye a la protección contra la pérdida de datos sin interferir en la experiencia del empleado. También ayuda a proteger los datos y las aplicaciones empresariales contra las pérdidas accidentales de datos en dispositivos propiedad de la empresa y dispositivos personales que los empleados usan en el trabajo. Esto consigue sin necesidad de realizar cambios en su entorno o en otras aplicaciones.

Esta característica es compatible con:
- Windows 10 y versiones posteriores

## <a name="custom-profile"></a>Perfil personalizado
La [configuración personalizada](custom-settings-configure.md) incluye la capacidad para asignar valores de configuración del dispositivo que no están integrados en Intune. Por ejemplo, en dispositivos Android, puede escribir valores de OMA-URI. Para dispositivos iOS, puede importar un archivo de configuración creado Apple Configurator. 

Esta característica es compatible con:

- Android
- iOS
- macOS
- Windows Phone 8,1

## <a name="manage-and-troubleshoot"></a>Supervisión y solución de problemas

[Administre los perfiles](device-profile-monitor.md) para comprobar el estado de los dispositivos y los perfiles asignados. También ayudan a resolver conflictos mediante la visualización de la configuración que provoca un conflicto y los perfiles que contienen esta configuración. [Problemas y soluciones comunes](device-profile-troubleshoot.md) proporciona una lista de preguntas y respuestas para ayudar a trabajar con perfiles, incluido lo que sucede cuando se elimina un perfil, qué provoca que las notificaciones se envíen a dispositivos y mucho más.