---
title: "Configuración de restricciones de dispositivos de Intune para Android for Work"
titleSuffix: Intune on Azure
description: "Conozca la configuración de Intune que puede usar para controlar los valores de configuración y la funcionalidad de los dispositivos de Android for Work."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1830720b-16cb-4f2f-a71a-62967f882563
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4a8053e54dcad692380b6762b22411f271337f29
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="android-for-work-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos Android for Work en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Configuración de perfil de trabajo
- **Uso compartido de datos entre el perfil de trabajo y el personal**: use esta configuración para controlar si las aplicaciones del perfil de trabajo y las aplicaciones del perfil personal pueden compartir datos. Este valor controla las acciones de uso compartido dentro de las aplicaciones (por ejemplo, la opción **Compartir...** de la aplicación de explorador Chrome) y no se aplica al comportamiento del Portapapeles de copiar y pegar. A diferencia de la [configuración de las directivas de protección de aplicaciones](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), la configuración de las restricciones del dispositivo se administra desde el portal de Intune y se usa la partición del perfil de trabajo de Android for Work para aislar las aplicaciones administradas. Elija de entre las siguientes opciones:
    - **Restricciones de uso compartido predeterminado**: esta opción es el comportamiento de uso compartido predeterminado del dispositivo que varía según la versión de Android que se ejecuta. De manera predeterminada, se permite el uso compartido desde el perfil personal hasta el perfil de trabajo. También de manera predeterminada, el uso compartido desde el perfil de trabajo hasta el perfil personal está bloqueado. Esta opción evita que se compartan datos desde el perfil de trabajo hasta el perfil personal. Google no proporciona ninguna manera de bloquear el uso compartido desde el perfil personal hasta el perfil de trabajo en dispositivos que ejecutan las versiones 6.0 y posteriores.   
    - **Las aplicaciones de un perfil profesional pueden controlar la solicitud de uso compartido desde un perfil personal**: use esta opción para habilitar la característica de Android integrada que permite el uso compartido desde el perfil personal al perfil profesional. Cuando esta opción está habilitada, una solicitud de uso compartido que se inicia en una aplicación del perfil personal se podrá compartir con las aplicaciones del perfil de trabajo. Esta opción es el comportamiento predeterminado de los dispositivos Android que ejecutan versiones anteriores a 6.0.
    - **Permitir el uso compartido a través de límites**: permite el uso compartido a través del límite del perfil de trabajo en ambas direcciones. Cuando selecciona esta configuración, las aplicaciones del perfil de trabajo pueden compartir datos con aplicaciones no administradas del perfil personal. Use esta configuración con precaución, ya que permite que las aplicaciones administradas en el perfil de trabajo se compartan con aplicaciones del lado sin administrar del dispositivo.

-   **Notificaciones del perfil profesional con dispositivo bloqueado**: controla si las aplicaciones del perfil de trabajo pueden mostrar datos en las notificaciones cuando el dispositivo está bloqueado.
-   **Permisos de aplicación predeterminados**: establece la directiva de permisos predeterminada para todas las aplicaciones del perfil profesional. A partir de Android 6, se solicita al usuario que conceda determinados permisos que requieren las aplicaciones cuando se inician. Esta configuración de directiva permite decidir si se pedirá a los usuarios que concedan permisos para todas las aplicaciones del perfil de trabajo. Por ejemplo, suponga que asigna una aplicación al perfil de trabajo que requiere acceso mediante la ubicación. Normalmente, esa aplicación pide al usuario que apruebe o deniegue el acceso a la aplicación mediante la ubicación. Esta directiva le permite decidir si todos los permisos deben concederse automáticamente sin preguntar al usuario, denegarse automáticamente sin preguntar al usuario o dejar que el usuario final decida. Elija de entre las siguientes opciones:
    -   **Valor predeterminado de dispositivo**
    -   **Aviso**
    -   **Concesión automática**
    -   **Denegación automática**

    El estado de concesión de los permisos se puede definir aún más para aplicaciones específicas mediante una directiva de configuración de aplicaciones (en **Aplicaciones móviles** > **Directivas de configuración de aplicaciones**).

### <a name="work-profile-password"></a>Contraseña del perfil de trabajo
- **Requerir contraseña de perfil de trabajo** (Android 7.0 y versiones posteriores con el perfil del trabajo habilitado): defina una directiva de código de acceso que se aplique solo a las aplicaciones del perfil del trabajo. De manera predeterminada, el usuario final tiene la opción de usar los dos PIN definidos por separado o de optar por combinarlos en el más seguro de ellos.
- **Longitud mínima de la contraseña**: escriba el número mínimo de caracteres que debe contener la contraseña de los usuarios (de **4**-**16**)
- **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: seleccione la cantidad de tiempo antes de que el perfil de trabajo se bloquee. El usuario deberá especificar sus credenciales para volver a obtener acceso.
- **Número de errores de inicio de sesión antes de borrar el dispositivo**: escriba la cantidad de veces que se puede escribir una contraseña incorrecta antes de que se borre el perfil de trabajo del dispositivo.
- **Expiración de la contraseña (días)**: escriba el número de días hasta que se deba cambiar la contraseña de un usuario final (de **1**-**255**).
- **Tipo de contraseña obligatoria**: seleccione el tipo de contraseña que se debe establecer en el dispositivo. Elija de entre las siguientes opciones:
    - **Valor predeterminado de dispositivo**
    - **Biométrico de seguridad baja**
    - **Requerido**
    - **Al menos numérica**
    - **Complejo numérico**: (no se permiten números consecutivos o de repetición, como "1111" o "1234")
    - **Al menos alfabética**
    - **Al menos alfanumérica**
    - **Al menos alfanumérica con símbolos**
- **Impedir la reutilización de contraseñas anteriores**: escriba la cantidad de contraseñas nuevas que se deben usar antes de que se pueda reutilizar una nueva (de **1**-**24**).
- **Desbloqueo con huella digital**: impide que un usuario final use el escáner de huella digital del dispositivo para desbloquearlo.
- **Smart Lock y otros agentes de confianza**: permite controlar la característica de Smart Lock en dispositivos compatibles. Esta función del teléfono, conocida también en ocasiones como agentes de confianza, le permite deshabilitar u omitir la contraseña del perfil de trabajo si el dispositivo está en una ubicación de confianza (por ejemplo, cuando se conecta a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC). Puede usar esta opción para impedir que los usuarios configuren Smart Lock.

## <a name="device-password"></a>Contraseña del dispositivo

- **Longitud mínima de la contraseña**: escriba el número mínimo de caracteres que debe contener la contraseña de los usuarios (de **4**-**14**)
- **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: seleccione el tiempo antes de que un dispositivo inactivo se bloquee de forma automática.
- **Número de errores de inicio de sesión antes de borrar el dispositivo**: escriba la cantidad de veces que se puede escribir una contraseña incorrecta antes de que se borren todos los datos del dispositivo.
- **Expiración de la contraseña (días)**: escriba el número de días hasta que se deba cambiar la contraseña de un usuario final (de **1**-**255**).
- **Tipo de contraseña obligatoria**: seleccione el tipo de contraseña que se debe establecer en el dispositivo. Elija de entre las siguientes opciones:
    - **Valor predeterminado de dispositivo**
    - **Biométrico de seguridad baja**
    - **Requerido**
    - **Al menos numérica**
    - **Complejo numérico**: (no se permiten números consecutivos o de repetición, como "1111" o "1234")
    - **Al menos alfabética**
    - **Al menos alfanumérica**
    - **Al menos alfanumérica con símbolos**
- **Impedir la reutilización de contraseñas anteriores**: escriba la cantidad de contraseñas nuevas que se deben usar antes de que se pueda reutilizar una nueva (de **1**-**24**).
- **Desbloqueo con huella digital**: impide que un usuario final use el escáner de huella digital del dispositivo para desbloquearlo.
- **Smart Lock y otros agentes de confianza**: permite controlar la característica de Smart Lock en dispositivos compatibles. Esta función del teléfono, conocida también en ocasiones como agente de confianza, le permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si el dispositivo está en una ubicación de confianza (por ejemplo, cuando se conecta a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC). Puede usar esta opción para impedir que los usuarios configuren Smart Lock.

## <a name="next-steps"></a>Pasos siguientes

Use la información del tema [Configuración de restricciones de dispositivos en Microsoft Intune](device-restrictions-configure.md) para guardar y asignar el perfil a los usuarios y dispositivos.
