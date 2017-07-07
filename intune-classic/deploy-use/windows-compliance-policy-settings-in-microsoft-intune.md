---
title: "Configuración de directivas de cumplimiento normativo para dispositivos Windows"
description: En este tema se describen las reglas y opciones que se pueden configurar para las directivas de cumplimiento de dispositivos Windows.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f996842c-e9a4-4819-acb4-ee66e8fb35b8
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 67810c51c7a7b2ec1e1ff33c11a27a8757b2bcbd
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="compliance-policy-settings-for-windows-devices-in-microsoft-intune"></a>Configuración de directivas de cumplimiento para dispositivos Windows en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

La configuración de directiva que se describe en este tema se aplica a los dispositivos que ejecuten el sistema operativo Windows. En las secciones siguientes se describen las versiones de Windows compatibles.

Si quiere obtener información sobre otras plataformas, seleccione uno de los siguientes temas:
> [!div class="op_single_selector"]
- [Configuración de directivas de cumplimiento normativo para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Configuración de directivas de cumplimiento para dispositivos Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Configuración de directivas de cumplimiento para Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="compliance-policy-settings-for-windows-phone-devices"></a>Configuración de directivas de cumplimiento para dispositivos Windows Phone
La configuración que se indica en esta sección se admite en Windows Phone 8.1 y versiones posteriores.

### <a name="system-security-settings"></a>Configuración de seguridad del sistema
#### <a name="password"></a>Contraseña
- **Requerir una contraseña para desbloquear dispositivos móviles:** establezca esta opción en **Sí** para exigir que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos.

- **Permitir contraseñas sencillas**: establezca esta opción en **Sí** para permitir al usuario crear una contraseña sencilla como **1234** o **1111**.

-  **Longitud mínima de la contraseña**: especifique el número mínimo de dígitos o caracteres que debe tener la contraseña del usuario.
- **Tipo de contraseña obligatoria:** especifique si el usuario debe crear una contraseña **Alfanumérica** o **Numérica**.

  En los dispositivos a los que se obtiene acceso con una cuenta de Microsoft y que ejecutan Windows, la directiva de cumplimiento no podrá evaluarse correctamente si la longitud mínima de la contraseña es superior a ocho caracteres o si el número mínimo de conjuntos de caracteres es superior a dos.

- **Número mínimo de conjuntos de caracteres:** si la opción **Tipo de contraseña requerida** está establecida en **Alfanumérica**, esta opción especifica el número mínimo de conjuntos de caracteres que debe tener la contraseña. Los conjuntos de cuatro caracteres son los siguientes:
  -   Letras minúsculas
  -   Letras mayúsculas
  -   Símbolos
  -   Números

  Para establecer un número mayor para esta opción, será necesario que el usuario cree una contraseña más compleja. En los dispositivos a los que se obtiene acceso con una cuenta de Microsoft y que ejecutan Windows, la directiva de cumplimiento no podrá evaluarse correctamente si la longitud mínima de la contraseña es superior a ocho caracteres o si el número mínimo de conjuntos de caracteres es superior a dos.

- **Minutos de inactividad antes de que se requiera la contraseña:** esta opción especifica el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir su contraseña.

- **Expiración de la contraseña (días)**: elija el número de días que faltan para que la contraseña del usuario expire y durante los cuales debe crear una nueva.

- **Recordar historial de contraseñas:** use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para impedir que el usuario cree contraseñas que se han usado anteriormente.

- **Impedir la reutilización de contraseñas anteriores:** si la opción **Recordar historial de contraseñas** está seleccionada, especifique el número de contraseñas usadas previamente que no se pueden volver a usar.
- **Requerir una contraseña cuando el dispositivo vuelva de un estado de inactividad**: use este valor junto con el de la opción **Minutos de inactividad antes de que sea necesaria la contraseña**. Se pedirá al usuario que escriba una contraseña para obtener acceso a un dispositivo que haya estado inactivo durante el tiempo especificado en la opción **Minutos de inactividad antes de que sea necesaria la contraseña**.

  > [!NOTE]
  > Esta configuración solo se aplica a dispositivos Windows 10 Mobile.

#### <a name="encryption"></a>Cifrado
- **Requerir cifrado en el dispositivo móvil:** establezca esta opción en **Sí** para requerir que el dispositivo esté cifrado para poder conectarse a los recursos.

### <a name="device-health-settings"></a>Configuración de estado del dispositivo
- **Requerir que se informe del estado correcto de los dispositivos:** puede establecer una regla para requerir que se informe del mantenimiento correcto de los dispositivos con **Windows 10 Mobile** en las directivas de cumplimiento nuevas o existentes.  Si se habilita esta opción de configuración, se evaluarán los puntos de datos siguientes de los dispositivos con Windows 10 a través del servicio de atestación de mantenimiento (HAS):
  -  **BitLocker habilitado**: si BitLocker está activado, el dispositivo puede proteger los datos almacenados en la unidad frente al acceso no autorizado cuando el sistema se apaga o entra en estado de hibernación. La característica Cifrado de unidad BitLocker de Windows cifra todos los datos almacenados en el volumen del sistema operativo Windows. BitLocker usa el TPM para ayudar a proteger el sistema operativo Windows y los datos de usuario. BitLocker también ayuda a garantizar que no se manipule un equipo, incluso si se deja desatendido, se pierde o lo roban. Si el equipo incluye un TPM compatible, BitLocker lo usa para bloquear las claves de cifrado que ayudan a proteger los datos. Como resultado, las claves no son accesibles hasta que TPM termina la comprobación del estado del equipo.
  -  **Integridad de código habilitada**: la integridad de código es una característica que valida la integridad de un archivo del sistema o controlador cada vez que se carga en la memoria. La integridad de código detecta si se está cargando en el kernel un archivo del sistema o controlador sin firmar. También detecta si se ha modificado un archivo del sistema mediante software malintencionado que una cuenta de usuario ejecuta con privilegios de administrador.
  - **Arranque seguro habilitado**: si el arranque seguro está habilitado, el sistema debe arrancar en un estado de confianza de fábrica. Además, si el arranque seguro está habilitado, los componentes principales que se usan para arrancar el equipo deben tener las firmas de cifrado correctas que son de confianza para la organización que fabricó el dispositivo. El firmware UEFI lo comprueba antes de permitir iniciar el equipo. Si los archivos se han manipulado e interrumpido su firma, el sistema no arrancará.

  > [!IMPORTANT]
  > Los dispositivos de Windows no admiten software de terceros de **antimalware de inicio temprano** (ELAM) instalado como parte de la atestación de estado del dispositivo.

  Para obtener información sobre cómo funciona el servicio HAS, consulte [HealthAttestation CSP](https://msdn.microsoft.com/library/dn934876.aspx).
###  <a name="device-property-settings"></a>Configuración de propiedades de dispositivo
- **SO mínimo requerido:** cuando un dispositivo no cumpla el requisito de versión de SO mínima, se notificará como no compatible.
    Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario puede optar por actualizar el dispositivo, tras lo cual podrá tener acceso a los recursos de la empresa.

- **Versión de SO máxima permitida**: cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.


## <a name="compliance-policy-settings-for-windows-pcs"></a>Configuración de directivas de cumplimiento para equipos Windows
La configuración indicada en esta sección se admite en equipos Windows.
### <a name="system-security-settings"></a>Configuración de seguridad del sistema
#### <a name="password"></a>Contraseña
- **Longitud mínima de la contraseña:** se admite en Windows 8.1.

  Especifique el número mínimo de dígitos o caracteres que debe tener la contraseña del usuario.

  En los dispositivos a los que se obtiene acceso con una cuenta de Microsoft, la directiva de cumplimiento no podrá evaluarse correctamente si el valor de **Longitud mínima de la contraseña** es superior a ocho caracteres o el de **Número mínimo de conjuntos de caracteres** es superior a dos.

- **Tipo de contraseña requerida:** se admite en Windows RT, Windows RT 8.1 y Windows 8.1.

  Especifique si el usuario debe crear una contraseña **Alfanumérica** o **Numérica**.

- **Número mínimo de conjuntos de caracteres:** se admite en Windows RT, Windows RT 8.1 y Windows 8.1.

  Si la opción **Tipo de contraseña requerida** está establecida en **Alfanumérica**, esta opción especifica el número mínimo de caracteres que debe tener la contraseña. Los conjuntos de cuatro caracteres son los siguientes:
  -   Letras minúsculas
  -   Letras mayúsculas
  -   Símbolos
  -   Números     

  Para establecer un número mayor para esta opción, será necesario que el usuario cree una contraseña más compleja. En los dispositivos a los que se obtiene acceso con una cuenta de Microsoft, la directiva de cumplimiento no podrá evaluarse correctamente si el valor de **Longitud mínima de la contraseña** es superior a ocho caracteres o el de **Número mínimo de conjuntos de caracteres** es superior a dos.

- **Minutos de inactividad antes de que sea necesaria la contraseña:** se admite en Windows RT, Windows RT 8.1 y Windows 8.1.

  Especifique el tiempo de inactividad antes de que el usuario deba volver a escribir la contraseña.

- **Expiración de la contraseña (días):** se admite en Windows RT, Windows RT 8.1 y Windows 8.1.

  Elija el número de días que faltan para que la contraseña expire y durante los cuales deben crear una nueva.

- **Recordar historial de contraseñas:** se admite en Windows RT, Windows RT 8.1 y Windows 8.1.

  Use esta opción junto con **Impedir la reutilización de contraseñas anteriores** para impedir que el usuario cree contraseñas que se han usado anteriormente.

- **Impedir la reutilización de contraseñas anteriores:** se admite en Windows RT, Windows RT 8.1 y Windows 8.1.

  Si la opción **Recordar historial de contraseñas** está seleccionada, especifique el número de contraseñas usadas previamente que no se pueden volver a usar.

### <a name="device-health-settings"></a>Configuración de estado del dispositivo
- **Requerir que se informe del estado correcto de los dispositivos:** se admite en dispositivos Windows 10.
Puede establecer una regla para requerir que se informe del mantenimiento correcto de los dispositivos con Windows 10 en las directivas de cumplimiento nuevas o existentes. Si se habilita esta opción de configuración, se evaluarán los puntos de datos siguientes de los dispositivos con Windows 10 a través del servicio de atestación de mantenimiento (HAS):
  -  **BitLocker habilitado**: si BitLocker está activado, el dispositivo puede proteger los datos almacenados en la unidad frente al acceso no autorizado cuando el sistema se apaga o entra en estado de hibernación. La característica Cifrado de unidad BitLocker de Windows cifra todos los datos almacenados en el volumen del sistema operativo Windows. BitLocker usa el TPM para ayudar a proteger el sistema operativo Windows y los datos de usuario. BitLocker también ayuda a garantizar que no se manipule un equipo, incluso si se deja desatendido, se pierde o lo roban. Si el equipo incluye un TPM compatible, BitLocker lo usa para bloquear las claves de cifrado que ayudan a proteger los datos. Como resultado, las claves no son accesibles hasta que TPM termina la comprobación del estado del equipo.
  -  **Integridad de código habilitada**: la integridad de código es una característica que valida la integridad de un archivo del sistema o controlador cada vez que se carga en la memoria. La integridad de código detecta si se está cargando en el kernel un archivo del sistema o controlador sin firmar. También detecta si se ha modificado un archivo del sistema mediante software malintencionado que una cuenta de usuario ejecuta con privilegios de administrador.
  - **Arranque seguro habilitado**: si el arranque seguro está habilitado, el sistema debe arrancar en un estado de confianza de fábrica. Además, si el arranque seguro está habilitado, los componentes principales que se usan para arrancar el equipo deben tener las firmas de cifrado correctas que son de confianza para la organización que fabricó el dispositivo. El firmware UEFI lo comprueba antes de permitir iniciar el equipo. Si los archivos se han manipulado e interrumpido su firma, el sistema no arrancará.
  - **Early-launch antimalware is enabled** (El antimalware de inicio temprano está habilitado): el antimalware de inicio temprano (ELAM) proporciona protección para los equipos de la red cuando se inician y antes de que se inicialicen los controladores de terceros.

  Para obtener información sobre cómo funciona el servicio HAS, consulte [HealthAttestation CSP](https://msdn.microsoft.com/library/dn934876.aspx).

### <a name="device-property-settings"></a>Configuración de propiedades de dispositivo
- **Minimum OS required:** (Versión mínima de sistema operativo): se admite en Windows 8.1 y Windows 10.

  Especifique aquí el número de major.minor.build. El número de versión debe coincidir con la versión devuelta por el comando **winver**.

  Cuando un dispositivo tiene una versión anterior a la versión de sistema operativo especificada, se notifica como no conforme. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario puede optar por actualizar el dispositivo, tras lo cual podrá tener acceso a los recursos de la empresa.

- **Maximum OS version allowed** (Versión máxima de sistema operativo permitida): se admite en Windows 8.1 y Windows 10.

  Cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa y se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, este dispositivo no podrá usarse para acceder a los recursos de la empresa.

Para buscar la versión de sistema operativo que se usará para las opciones **Minimum OS required** (Versión mínima de sistema operativo) y **Maximum OS version allowed** (Versión máxima de sistema operativo permitida), ejecute el comando **winver** desde el símbolo del sistema. El comando **winver** devuelve la versión de sistema operativo notificada.

- Los equipos con Windows 8.1 devuelven la versión **6.3**. Si la regla de la versión de sistema operativo se establece en Windows 8.1 para Windows, el dispositivo se notificará como no conforme aunque tenga Windows 8.1.

- En los equipos que ejecutan Windows 10, la versión debe establecerse en **10.0** más el número de compilación del sistema operativo devuelto por el comando **winver**. Por ejemplo, podría ser similar a 10.0.10586.
> ![Versión de compilación del sistema operativo resaltada en el cuadro de diálogo "Acerca de Windows"](./media/ca_win10-os-version.png)
