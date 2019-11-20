---
title: Cifrado de dispositivos con el método de cifrado compatible con plataformas
titleSuffix: Microsoft Intune
description: Cifre dispositivos con métodos de cifrado integrados como BitLocker o FileVault y administre las claves de recuperación de esos dispositivos cifrados en el portal de Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: ce5db670f0084626f1c053b64679623ccf28eb21
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164645"
---
# <a name="use-device-encryption-with-intune"></a>Uso del cifrado de dispositivos con Intune  

Use Intune para administrar un cifrado integrado de disco o de unidad de dispositivos para proteger los datos de estos.

Configure el cifrado de disco como parte de un perfil de configuración de dispositivo para la protección de punto de conexión. Intune admite las plataformas y tecnologías de cifrado siguientes:

- macOS: FileVault
- Windows 10 y versiones posteriores: BitLocker

Intune también proporciona un [informe de cifrado](encryption-monitor.md) integrado que presenta los detalles sobre el estado de cifrado de los dispositivos en todos los dispositivos administrados.

## <a name="filevault-encryption-for-macos"></a>Cifrado de FileVault para macOS

Use Intune para configurar el cifrado de discos de FileVault en los dispositivos que ejecutan macOS. Después, use el informe de cifrado de Intune para ver los detalles de cifrado de esos dispositivos y administrar las claves de recuperación de los dispositivos cifrados de FileVault.

FileVault es un programa de cifrado de disco completo que se incluye con macOS. Puede usar Intune para configurar FileVault en dispositivos que ejecuten **macOS 10.13 o versiones posteriores**.

Para configurar FileVault, cree un [perfil de configuración de dispositivo](../configuration/device-profile-create.md) para la protección de punto de conexión en la plataforma de macOS. La configuración de FileVault es una de las categorías de configuración disponibles para la protección de punto de conexión de macOS.

Después de crear una directiva para cifrar dispositivos con FileVault, la directiva se aplica a los dispositivos en dos fases. En primer lugar, el dispositivo se prepara para habilitar a Intune a recuperar y hacer una copia de seguridad de la clave de recuperación. A esto se le conoce como custodia. Una vez que se ha custodiado la clave, se puede iniciar el cifrado de disco.

![Configuración de FileVault](./media/encrypt-devices/filevault-settings.png)

Para obtener más información sobre la configuración de FileVault que puede administrar con Intune, consulte [FileVault](endpoint-protection-macos.md#filevault) en el artículo de Intune para la configuración de protección de punto de conexión de MacOS.

### <a name="how-to-configure-macos-filevault"></a>Cómo configurar FileVault en macOS

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

3. Establece las siguientes opciones:

   - Plataforma: macOS
   - Tipo de perfil: Endpoint Protection

4. Seleccione **Configuración** > **FileVault**.

5. En *FileVault*, seleccione **Habilitar**.

6. En *Tipo de clave de recuperación*, solo se admite **Clave personal**.

   Considere la posibilidad de agregar un mensaje con el fin de guiar a los usuarios finales sobre cómo recuperar la clave de recuperación de su dispositivo. Esta información puede ser útil para los usuarios finales cuando se usa la configuración de Giro de clave de recuperación personal, que puede generar automáticamente una nueva clave de recuperación para un dispositivo de forma periódica.

   Por ejemplo: para recuperar una clave de recuperación perdida o girada recientemente, inicie sesión en el sitio web Portal de empresa de Intune desde cualquier dispositivo. En el portal, vaya a *Dispositivos*, seleccione el dispositivo que tiene habilitado FileVault y, después, seleccione *Obtener clave de recuperación*. Se muestra la clave de recuperación actual.  

7. Configure el resto de [valores de FileVault](endpoint-protection-macos.md#filevault) para cumplir con sus necesidades empresariales y luego seleccione **Aceptar**.

   > [!IMPORTANT]
   > Hay un problema conocido cuando el valor **Deshabilitar mensaje al cierre de sesión** se establece en *habilitado*. Cuando se establece en *habilitado*, el valor de **número de veces que se puede omitir** se debe establecer en un valor y no debe establecerse como *no configurado*. Si se establece en *Sin configurar*, el perfil producirá un error en el dispositivo. En este escenario, el dispositivo informa de que se trata de un **Resumen de estado del perfil** como **Error** sin detalles adicionales.
   >
   > Cuando **Deshabilitar mensaje al cierre de sesión** se establece en *Sin configurar*, **Número de veces que se permite omitir** puede estar *Sin configurar* o tener un valor.
   >
   > Esta incidencia se resolverá en una actualización futura.

8. Complete la configuración de valores adicionales y luego guarde el perfil.  

### <a name="manage-filevault"></a>Administración de FileVault

Después de que Intune cifre un dispositivo macOS con FileVault, podrá ver y administrar las claves de recuperación de FileVault cuando vea el [informe de cifrado](encryption-monitor.md) de Intune.

Una vez que Intune cifra un dispositivo macOS con FileVault, puede ver la clave de recuperación personal de dicho dispositivo en el Portal de empresa en cualquier dispositivo. Una vez en el Portal de empresa web, elija el dispositivo macOS cifrado y, a continuación, elija "Obtener clave de recuperación" como acción de dispositivos remotos.

## <a name="bitlocker-encryption-for-windows-10"></a>Cifrado de BitLocker en Windows 10

Use Intune para configurar el Cifrado de unidad BitLocker en los dispositivos que ejecutan Windows 10. Luego, use el informe de cifrado de Intune para ver los detalles de cifrado de esos dispositivos. También puede tener acceso a información importante para BitLocker desde sus dispositivos, tal como se ha encontrado en Azure Active Directory (Azure AD).

BitLocker está disponible en dispositivos que ejecutan **Windows 10 o versiones posteriores**.

Configure BitLocker cuando cree un [perfil de configuración de dispositivo](../configuration/device-profile-create.md) para la protección de punto de conexión en la plataforma de Windows 10 o versiones posteriores. La configuración de BitLocker se encuentra en la categoría de configuración de cifrado de Windows para la protección de punto de conexión de Windows 10.

![Configuración de BitLocker](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>Cómo configurar BitLocker de Windows 10

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

3. Establece las siguientes opciones:

   - Plataforma: Windows 10 y versiones posteriores
   - Tipo de perfil: Endpoint Protection

4. Seleccione **Configuración** > **Cifrado de Windows**.

5. Configure los valores de BitLocker para cumplir con sus necesidades empresariales y luego seleccione **Aceptar**.

6. Complete la configuración de valores adicionales y luego guarde el perfil.

### <a name="manage-bitlocker"></a>Administración de BitLocker  

Después de que Intune cifre un dispositivo Windows 10 con BitLocker, podrá ver y recuperar las claves de recuperación de BitLocker cuando vea el [informe de cifrado](encryption-monitor.md) de Intune.

## <a name="next-steps"></a>Pasos siguientes

Crear una directiva de [cumplimiento de dispositivos](compliance-policy-create-windows.md)

Use el informe de cifrado para administrar lo siguiente:

- [Claves de recuperación de BitLocker](encryption-monitor.md#bitlocker-recovery-keys)
- [Claves de recuperación de FileVault](encryption-monitor.md#filevault-recovery-keys)

Revise la configuración de cifrado que puede configurar con Intune para lo siguiente:

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)