---
title: Configuración de quiosco de Android en Microsoft Intune - Azure | Microsoft Docs
description: Configure dispositivos de quiosco de Android Enterprsie.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 9/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c4db49b6727a430696d6ade3bc8eb8f4600ebe3e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190292"
---
# <a name="android-enterprise-kiosk-settings-in-intune"></a>Configuración de quiosco de Android Enterprise en Intune

Los perfiles de quiosco de Android admiten las siguientes opciones de configuración. Al crear un perfil, estas opciones de configuración se muestran cuando se elige **Tipo de perfil** > **Solo propietario del dispositivo** > **Restricciones de dispositivos**. Para ver estas opciones de configuración, elija **Propiedades** en un perfil de restricción de dispositivos Android Enterprise y después elija **Configurar**.

## <a name="general-settings"></a>Configuración general

- **Captura de pantalla**: elija **Bloquear** para impedir que los usuarios hagan capturas de pantalla en el dispositivo.
- **Cámara**: elija **Bloquear** para deshabilitar la cámara del dispositivo.
- **Directiva de permisos predeterminada**: con esta opción se define la directiva de permisos predeterminada para las solicitudes de permisos en tiempo de ejecución. Los valores posibles incluyen:
    - **Valor predeterminado del dispositivo**: use la configuración predeterminada del dispositivo.
    - **Símbolo del sistema**: se solicita al usuario que apruebe el permiso.
    - **Concesión automática**: los permisos se conceden automáticamente.
    - **Denegación automática**: los permisos se deniegan automáticamente.
- **Cambios de volumen**: elija **Bloquear** para impedir que los usuarios cambien el volumen del dispositivo.
- **Borrado**: elija **Bloquear** para impedir que los usuarios borren el dispositivo.
- **Arranque seguro**: elija **Bloquear** para impedir que los usuarios reinicien el dispositivo en modo seguro.
- **Barra de estado**: elija **Bloquear** para impedir que los usuarios accedan a la barra de estado, incluidas las notificaciones y las opciones de configuración rápida.
- **Cambios de configuración de la Wi-Fi**: elija **Bloquear** para impedir que los usuarios cambien las configuraciones de Wi-Fi creadas por el propietario del dispositivo. Los usuarios pueden crear sus propias configuraciones de Wi-Fi.
- **Configuración del punto de acceso Wi-Fi**: elija **Bloquear** para impedir que los usuarios creen o editen las configuraciones de Wi-Fi.
- **Características de depuración**: elija **Permitir** para permitir que los usuarios usen las características de depuración.
- **Ajuste del micrófono**: elija **Bloquear** para impedir que los usuarios ajusten el volumen del micrófono o lo silencien.
- **Correos electrónicos de protección ante el borrado**: elija **Direcciones de correo electrónico de la cuenta de Google** para definir las direcciones de correo electrónico (separadas por punto y coma) que pueden desbloquear el dispositivo después de un borrado. Si no se especifica ningún correo electrónico, cualquier usuario podrá desbloquear el dispositivo después de un borrado.
- **Sombreado de escape de red**: elija **Habilitar** para permitir la activación de la característica de sombreado de escape de red. Si no se puede realizar una conexión de red en el momento de arranque, el sombreado de escape solicita al usuario que se conecte temporalmente a una red con el fin de actualizar la directiva del dispositivo. Después de aplicar la directiva, la red temporal se olvida y el dispositivo sigue arrancando. Esto impide que no se pueda conectar a una red si no hay ninguna red adecuada en la última directiva y el dispositivo arranca en una aplicación en modo de bloqueo de tareas o el usuario no puede llegar a la configuración del dispositivo.
- **Permitir la instalación desde orígenes desconocidos**: elija **Permitir** para permitir que los usuarios instalen desde orígenes desconocidos.
- **Actualización del sistema**: elija una opción para definir de qué forma funciona el dispositivo a través de las actualizaciones inalámbricas:
    - **Valor predeterminado del dispositivo**: use la configuración predeterminada del dispositivo.
    - **Automática**: las actualizaciones se instalan automáticamente sin intervención del usuario. Si se configura esta directiva se instalarán inmediatamente las actualizaciones pendientes.
    - **Pospuesta**: las actualizaciones se posponen durante 30 días. Al final de los 30 días, Android solicita al usuario que instale la actualización. Es posible que los fabricantes de dispositivos o los transportistas impidan que se pospongan actualizaciones de seguridad importantes (es decir, que las declaren como exentas). Una actualización exenta muestra al usuario una notificación en el dispositivo. 
    - **Ventana de mantenimiento**: instala las actualizaciones automáticamente durante una ventana de mantenimiento diaria configurada en Intune. La instalación se intenta diariamente durante 30 días y pueden producirse errores debido a niveles de batería o espacio insuficientes. Después de 30 días, Android solicita al usuario que instale la actualización. La ventana también se usa para instalar actualizaciones de aplicaciones de Google Play. Se recomienda esta opción para dispositivos dedicados, como quioscos, ya que se pueden actualizar las aplicaciones de primer plano de quioscos de una única aplicación. 

## <a name="kiosk-settings"></a>Configuración de quiosco

- **Modo de quiosco**: define si el dispositivo puede ejecutar una sola aplicación o varias aplicaciones. Para más información, consulte [Configuración del quiosco multimedia para Android en Intune](android-kiosk-settings.md).
    - **Quiosco con una sola aplicación**: los usuarios solo pueden acceder a una sola aplicación.
    - **Quiosco con varias aplicaciones**: los usuarios pueden acceder a un conjunto limitado de aplicaciones.

## <a name="device-password-settings"></a>Configuración de la contraseña del dispositivo

- **Keyguard**: elija **Deshabilitar** para impedir que los usuarios usen Keyguard en el dispositivo.
- **Tipo de contraseña requerida**: define el tipo de contraseña necesaria para el dispositivo.
- **Longitud mínima de la contraseña**: define la longitud mínima de la contraseña necesaria para el dispositivo.
- **Número de errores de inicio de sesión antes de borrar el contenido del dispositivo**: define el número de errores de inicio de sesión que pueden producirse antes de que se borre el contenido del dispositivo.

## <a name="power-settings"></a>Configuración de energía

- **Tiempo para bloquear la pantalla**: establece la cantidad de tiempo de inactividad requerido antes de que el dispositivo se bloquee.
- **Pantalla activada mientras el dispositivo está conectado**: elija qué fuentes de alimentación provocan que la pantalla del dispositivo permanezca activa cuando está conectado.

## <a name="users-and-accounts-settings"></a>Configuración de cuentas y usuarios

- **Agregar nuevos usuarios**: elija **Bloquear** para impedir que los usuarios agreguen nuevos usuarios.
- **Eliminación de usuarios**: elija **Bloquear** para impedir que los usuarios quiten usuarios.
- **Cambios de la cuenta**: elija **Bloquear** para impedir que los usuarios modifiquen las cuentas.

## <a name="next-steps"></a>Pasos siguientes
[Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).



