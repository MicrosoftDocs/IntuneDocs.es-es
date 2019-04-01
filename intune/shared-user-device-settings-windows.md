---
title: Configuración del dispositivo compartido con Windows 10; Microsoft Intune; Azure | Microsoft Docs
description: Agregue y use Windows 10 para configurar dispositivos compartidos o que usan varios usuarios en Microsoft Intune. Vea una lista de todas las configuraciones y qué hacen en los dispositivos, incluido Microsoft Surface. Controle las cuentas de invitado, administre cuentas y elimine cuentas inactivas, permita o impida que se guarde el contenido en el almacenamiento local, establezca las opciones de energía y suspensión, elija cuándo se instalan las actualizaciones y use dispositivos en entornos educativos en un perfil de configuración de dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 28f8a589f20cb63ad4f9873942e9ad511d729b37
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566461"
---
# <a name="windows-10-and-later-settings-to-manage-shared-devices-using-intune"></a>Configuración de Windows 10 y versiones posteriores para administrar dispositivos compartidos mediante Intune

Varios usuarios pueden utilizar los dispositivos con Windows 10 y versiones posteriores, como Microsoft Surface. Los dispositivos con varios usuarios se denominan dispositivos compartidos y forman parte de las soluciones de la administración de dispositivos móviles (MDM).

Con Microsoft Intune, los usuarios finales pueden iniciar sesión en estos dispositivos compartidos con una cuenta de invitado. Al usar el dispositivo, solamente tendrán acceso a las características que permita. Como administrador de Intune, configura el acceso, elige cuándo se eliminan las cuentas, controla la configuración de administración de energía y mucho más en los dispositivos compartidos con Windows 10.

En este artículo se enumeran y describen las configuraciones que usa en un perfil de configuración de dispositivo con Windows 10 y versiones posteriores. Al crear el perfil en Intune, implementa o asigna el perfil en los grupos de dispositivos de su organización. También puede asignar este perfil a grupos de dispositivos con distintos tipos de dispositivo y versiones del SO.

Para obtener más información sobre esta característica de Intune, vea [Control access, accounts, and power features on shared PC or multi-user devices](shared-user-device-settings.md) (Control de acceso, cuentas y características de energía en dispositivos con varios usuarios o equipos compartidos). Para obtener más información sobre el CSP de Windows, vea [SharedPC CSP](https://docs.microsoft.com/windows/client-management/mdm/sharedpc-csp) (CSP de SharedPC).

## <a name="before-your-begin"></a>Antes de empezar

[Cree el perfil](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Configuración de dispositivos compartidos con varios usuarios

- **Modo de PC compartido**: elija **habilitar** para activar el modo de PC compartido. En este modo, no puede haber más de un usuario que inicie sesión en el dispositivo. Otro usuario no puede iniciar sesión hasta que el primero la cierre. La opción **No configurado** (valor predeterminado) deja esta configuración sin que Intune la administre y no inserta ninguna directiva para controlar esta configuración en un dispositivo.
- **Cuenta de invitado**: elija crear una opción Invitado en la pantalla de inicio de sesión. Las cuentas de invitado no requieren autenticación ni credenciales de usuario. Esta configuración crea una cuenta local cada vez que se usa. Las opciones son:
  - **Invitado**: se crea una cuenta de invitado de forma local en el dispositivo.
  - **Dominio**: se crea una cuenta de invitado en Azure Active Directory (AD).
  - **Invitado y dominio**: se crea una cuenta de invitado de forma local en el dispositivo y en Azure Active Directory (AD).
- **Administración de cuentas**: establezca esta opción en **Habilitar** para eliminar de forma automática las cuentas locales creadas por invitados y las cuentas en AD y Azure AD. Cuando un usuario cierre sesión en el dispositivo, o cuando se ejecute el mantenimiento del sistema, estas cuentas se eliminarán. Al habilitar esta opción, también deberá establecer lo siguiente:
  - **Eliminación de la cuenta**: elegir cuándo se eliminan las cuentas: **al umbral de espacio de almacenamiento**, **al umbral de espacio de almacenamiento y el umbral inactiva**, o **inmediatamente después de cierre de sesión** . Indique también:
    - **Comience a eliminar threshold(%)**: escriba un porcentaje (0-100) de espacio en disco. Cuando el espacio de almacenamiento o en disco sea inferior al valor indicado, las cuentas en caché se eliminarán. Se eliminan las cuentas continuamente para recuperar espacio en disco. Las cuentas que lleven más tiempo inactivas serán las primeras en eliminarse.
    - **Detener la eliminación threshold(%)**: escriba un porcentaje (0-100) de espacio en disco. Cuando el espacio de almacenamiento o en disco alcance el valor indicado, la eliminación se detendrá.

  Establezca esta opción en **Deshabilitar** para mantener las cuentas locales, de AD y de Azure AD creadas por invitados.

- **Almacenamiento local**: elija **Habilitado** para impedir que los usuarios guarden y vean los archivos en el disco duro del dispositivo. Elija **Deshabilitado** para permitir que los usuarios vean y guarden archivos de forma local mediante el Explorador de archivos. La opción **No configurado** (valor predeterminado) deja esta configuración sin que Intune la administre y no inserta ninguna directiva para controlar esta configuración en un dispositivo.
- **Directivas de energía**: cuando se establece en **Habilitado**, los usuarios no pueden desactivar la hibernación, invalidar todas las acciones de suspensión (por ejemplo, cerrar la tapa) ni cambiar la configuración de energía. Cuando se establece en **Deshabilitado**, los usuarios pueden hibernar el dispositivo, cerrar la tapa para suspender el dispositivo y cambiar la configuración de energía. La opción **No configurado** (valor predeterminado) deja esta configuración sin que Intune la administre y no inserta ninguna directiva para controlar esta configuración en un dispositivo.
- **Modo de suspensión el tiempo de espera (en segundos)**: escriba el número de segundos inactivas (0-100) antes de que el dispositivo entra en modo de suspensión. Si no establece un tiempo, el dispositivo entrará en suspensión al cabo de 60 minutos.
- **Iniciar sesión cuando se reactive el PC**: establézcalo en **Habilitado** para requerir que los usuarios inicien sesión con una contraseña cuando el dispositivo salga del modo de suspensión. Elija **Deshabilitado** para que los usuarios no tengan que escribir su nombre de usuario y contraseña. La opción **No configurado** (valor predeterminado) deja esta configuración sin que Intune la administre y no inserta ninguna directiva para controlar esta configuración en un dispositivo.
- **Hora (en minutos desde la medianoche) de inicio del mantenimiento**: escriba el tiempo en minutos (de 0 a 1440) cuando se ejecutan las tareas de mantenimiento automático, como Windows Update. La hora de inicio predeterminada es medianoche o cero (`0`) minutos. Para cambiar la hora de inicio, escriba una hora de inicio en minutos desde la medianoche. Por ejemplo, si quiere que el mantenimiento empiece a las 2:00, escriba `120`. Si quiere que el mantenimiento empiece a las 20:00, escriba `1200`.
- **Directivas de educación**: seleccione **Habilitado** para usar la configuración recomendada para los dispositivos que se usan en escuelas, que es más restrictiva. Elija **Deshabilitado** para que no se usen las directivas de educación recomendadas y predeterminadas. La opción **No configurado** (valor predeterminado) deja esta configuración sin que Intune la administre y no inserta ninguna directiva para controlar esta configuración en un dispositivo.

  Para obtener más información sobre qué hacen las directivas de educación, consulte [Recomendaciones de configuración de Windows 10 para clientes del sector educativo](https://docs.microsoft.com/education/windows/configure-windows-for-education).

## <a name="next-steps"></a>Pasos siguientes

- [Asigne el perfil](device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
- Consulte la configuración para [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).
