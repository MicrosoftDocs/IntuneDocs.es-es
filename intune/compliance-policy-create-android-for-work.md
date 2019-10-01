---
title: Configuración de dispositivos Android Enterprise en Microsoft Intune - Azure | Microsoft Docs
description: Vea una lista de todas las opciones que puede usar al configurar el cumplimiento de dispositivos Android Enterprise en Microsoft Intune. Configure reglas de contraseña, elija una versión mínima o máxima de sistema operativo, restrinja aplicaciones específicas, evite reutilizar contraseñas y mucho más.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6351aa7adf9d9d5ca333bb2bd97e552e6f1e156
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2019
ms.locfileid: "71304151"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Configuración de Android Enterprise para marcar dispositivos como compatibles o no compatibles con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo se enumeran y describen las distintas opciones de configuración de cumplimiento que se pueden establecer en dispositivos Android Enterprise y versiones posteriores en Intune. Como parte de la solución de administración de dispositivos móviles (MDM), use estas opciones para marcar los dispositivos liberados (descodificados) como no compatibles, establecer un nivel de amenaza permitido, habilitar Google Play Protect y mucho más.

Esta característica se aplica a:

- Android Enterprise

Como administrador del servicio Intune, use esta configuración de cumplimiento para proteger mejor los recursos de la organización. Para más información sobre las directivas de cumplimiento y lo que hacen, vea [Introducción a las directivas de cumplimiento](device-compliance-get-started.md).

> [!IMPORTANT]
> Las directivas de cumplimiento también aplican dispositivos de Android Enterprise dedicados. Si se asigna una directiva de cumplimiento a un dispositivo dedicado, el dispositivo puede mostrarse como **no conforme**. El acceso condicional y la aplicación de cumplimiento no están disponibles en dispositivos dedicados. Asegúrese de completar las tareas o acciones para obtener dispositivos dedicados compatibles con las directivas asignadas.

## <a name="before-you-begin"></a>Antes de comenzar

[Crear una directiva de cumplimiento](create-compliance-policy.md#create-the-policy). Para **Plataforma**, seleccione **Android Enterprise**.

## <a name="device-owner"></a>Propietario del dispositivo

### <a name="device-health"></a>Estado de dispositivos

- **Requerir que el dispositivo esté en el nivel de amenaza del dispositivo**: seleccione el nivel de amenaza de dispositivo máximo permitido evaluado por el [servicio de Mobile Threat Defense](mobile-threat-defense.md). Los dispositivos que superan este nivel de amenaza se marcan como no compatibles. Para usar esta configuración, elija el nivel de amenaza permitido:

  - **Sin configurar** (valor predeterminado): no se evalúa el cumplimiento o incumplimiento de esta configuración.
  - **Protegido**: esta opción es la más segura y significa que el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.
  - **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  - **Medio**: el dispositivo se evalúa como conforme si las amenazas presentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
  - **Alto**: esta opción es la menos segura, ya que permite que todos los niveles de amenaza. Quizás sea útil si utiliza esta solución solo con fines informativos.
  
> [!NOTE] 
> Los siguientes proveedores de Mobile Threat Threat (MTD) admiten implementaciones de propietarios de dispositivos empresariales de Android mediante la configuración de la aplicación:
> - Better Mobile 
> - Pradeo
> - Sophos Mobile
> - Zimperium 
>  
>  Consulte con su proveedor de MTD la configuración exacta necesaria para admitir las plataformas de propietarios de dispositivos empresariales de Android en Intune. Esta lista se actualiza a medida que los titulares de MTD admiten escenarios de propietario de dispositivos empresariales de Android. 

#### <a name="google-play-protect"></a>Google Play Protect

- **Atestación de dispositivo SafetyNet**: especifique el nivel de [atestación de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que se debe cumplir. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se evalúa el cumplimiento o incumplimiento de esta configuración.
  - **Comprobar integridad básica**
  - **Comprobar integridad básica y dispositivos certificados**

### <a name="device-properties"></a>Propiedades del dispositivo

- **Versión mínima del sistema operativo**: cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no conforme. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede actualizar el dispositivo y, a continuación, tener acceso a los recursos de la organización.
- **Versión máxima de SO**: cuando un dispositivo usa una versión de SO posterior a la de la regla, se bloquea el acceso a los recursos de la organización. Se pide al usuario que se ponga en contacto con el administrador de TI. El dispositivo no podrá acceder a los recursos de la empresa mientras no se cambie la regla para permitir la versión de sistema operativo.

### <a name="system-security"></a>Seguridad del sistema

- **Requerir una contraseña para desbloquear dispositivos móviles**: **requiere** que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

  Esta configuración se aplica en el nivel de dispositivo. Si solo tiene que solicitar una contraseña en el nivel de perfil de trabajo, entonces use una directiva de configuración. Vea [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](device-restrictions-android-for-work.md).

  - **Tipo de contraseña requerida**: elija si una contraseña debe incluir solo caracteres numéricos o una combinación de números y otros caracteres. Las opciones son:
    - **Dispositivo predeterminado**: para evaluar la compatibilidad con contraseñas, asegúrese de seleccionar una seguridad de contraseña distinta de la **predeterminada del dispositivo**.  
    - **Contraseña necesaria, sin restricciones**
    - **Biométrica deficiente**: [Biométricas eficientes frente a deficientes](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (abre el sitio web de Android).
    - **Numérica** (valor predeterminado): la contraseña solo debe contener números, por ejemplo: `123456789`. Escriba la **longitud mínima de la contraseña** que un usuario debe escribir, entre 4 y 16 caracteres.
    - **Complejo numérico**: no se permiten números repetidos ni consecutivos, como "1111" o "1234". Escriba la **longitud mínima de la contraseña** que un usuario debe escribir, entre 4 y 16 caracteres.
    - **Alfabética**: son necesarias letras del alfabeto. No son necesarios números ni símbolos. Escriba la **longitud mínima de la contraseña** que un usuario debe escribir, entre 4 y 16 caracteres.
    - **Alfanumérica**: incluye letras mayúsculas, minúsculas y caracteres numéricos. Escriba la **longitud mínima de la contraseña** que un usuario debe escribir, entre 4 y 16 caracteres.
    - **Alfanumérica con símbolos**: incluye letras mayúsculas, minúsculas, caracteres numéricos, signos de puntuación y símbolos. Indique también:

      - **Longitud mínima de la contraseña**: escriba la longitud mínima que debe tener la contraseña, entre 4 y 16 caracteres.
      - **Número de caracteres necesarios**: escriba el número de caracteres que debe tener la contraseña, entre 0 y 16 caracteres.
      - **Número de caracteres en minúscula necesarios**: escriba el número de caracteres en minúscula que debe tener la contraseña, entre 0 y 16 caracteres.
      - **Número de caracteres en mayúscula necesarios**: escriba el número de caracteres en mayúscula que debe tener la contraseña, entre 0 y 16 caracteres.
      - **Número de caracteres que no sean una letra necesarios**: escriba el número de caracteres que no son letras del alfabeto que debe tener la contraseña, entre 0 y 16 caracteres.
      - **Número de caracteres numéricos necesarios**: escriba el número de caracteres numéricos (`1`, `2`, `3`, etc.) que debe tener la contraseña, entre 0 y 16 caracteres.
      - **Número de caracteres de símbolos necesarios**: escriba el número de caracteres de símbolos (`&`, `#`, `%`, etc.) que debe tener la contraseña, entre 0 y 16 caracteres.

- **Máximo de minutos de inactividad antes de solicitar la contraseña**: indique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir la contraseña. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Número de días hasta que expira la contraseña**: escriba el número de días, entre 1 y 365, hasta que se deba cambiar la contraseña del dispositivo. Por ejemplo, para cambiar la contraseña después de 60 días, escriba `60`. Cuando la contraseña expire, se le solicitará a los usuarios que creen una nueva contraseña.
- **Número de contraseñas necesarias antes de que un usuario pueda volver a usar una contraseña**: escriba el número de contraseñas recientes que no se pueden volver a usar, entre 1 y 24. Utilice esta configuración para impedir que el usuario cree contraseñas usadas anteriormente.

- **Cifrado de almacenamiento de datos en el dispositivo**: elija **Requerir** para cifrar el almacenamiento de datos en los dispositivos. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

  No tiene que configurar este valor ya que los dispositivos Android Enterprise fuerzan el cifrado.

## <a name="work-profile"></a>Perfil de trabajo

### <a name="device-health"></a>Device health

- **Dispositivos raíz**: elija **Bloquear** para marcar los dispositivos raíz (con jailbreak) como no conformes. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Requerir que el dispositivo esté en el nivel de amenaza del dispositivo**: seleccione el nivel de amenaza de dispositivo máximo permitido evaluado por el [servicio de Mobile Threat Defense](mobile-threat-defense.md). Los dispositivos que superan este nivel de amenaza se marcan como no compatibles. Para usar esta configuración, elija el nivel de amenaza permitido:

  - **Sin configurar** (valor predeterminado): no se evalúa el cumplimiento o incumplimiento de esta configuración.
  - **Protegido**: esta opción es la más segura y significa que el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.
  - **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  - **Medio**: el dispositivo se evalúa como conforme si las amenazas presentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
  - **Alto**: esta opción es la menos segura, ya que permite que todos los niveles de amenaza. Quizás sea útil si utiliza esta solución solo con fines informativos.

#### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services está configurado**: se **requiere** que la aplicación Google Play Services esté instalada y habilitada. Google Play Services permite actualizaciones de seguridad y es una dependencia de nivel base para muchas características de seguridad en los dispositivos de Google certificados. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Proveedor de seguridad actualizada**: se **requiere** que un proveedor de seguridad actualizado pueda proteger un dispositivo frente a vulnerabilidades conocidas. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Atestación de dispositivo SafetyNet**: especifique el nivel de [atestación de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que se debe cumplir. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se evalúa el cumplimiento o incumplimiento de esta configuración.
  - **Comprobar integridad básica**
  - **Comprobar integridad básica y dispositivos certificados**

> [!NOTE]
> En los dispositivos Android Enterprise, **Examen de amenazas en las aplicaciones** es una directiva de configuración de dispositivos. Con una directiva de configuración, los administradores pueden habilitar la configuración en un dispositivo. Vea [Configuración de las restricciones de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

### <a name="device-properties"></a>Propiedades del dispositivo

- **Versión mínima del sistema operativo**: cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no conforme. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede actualizar el dispositivo y, a continuación, tener acceso a los recursos de la organización.
- **Versión máxima de SO**: cuando un dispositivo usa una versión de SO posterior a la de la regla, se bloquea el acceso a los recursos de la organización. Se pide al usuario que se ponga en contacto con el administrador de TI. El dispositivo no podrá acceder a los recursos de la empresa mientras no se cambie la regla para permitir la versión de sistema operativo.

### <a name="system-security"></a>Seguridad del sistema

- **Requerir una contraseña para desbloquear dispositivos móviles**: **requiere** que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración. Esta configuración se aplica en el nivel de dispositivo. Si solo tiene que solicitar una contraseña en el nivel de perfil de trabajo, entonces use una directiva de configuración. Vea [Configuración de dispositivos Android Enterprise para permitir o restringir características mediante Intune](device-restrictions-android-for-work.md).
- **Tipo de contraseña requerida**: elija si una contraseña debe incluir solo caracteres numéricos o una combinación de números y otros caracteres. Las opciones son:
  - **Valor predeterminado del dispositivo**
  - **Biométrico de seguridad baja**
  - **Al menos numérica** (valor predeterminado): escriba la **longitud mínima de la contraseña** que un usuario debe escribir (entre 4 y 16 caracteres).
  - **Numérica compleja** (valor predeterminado): escriba la **longitud mínima de la contraseña** que un usuario debe escribir (entre 4 y 16 caracteres).
  - **Al menos alfabética** (valor predeterminado): escriba la **longitud mínima de la contraseña** que un usuario debe escribir (entre 4 y 16 caracteres).
  - **Al menos alfanumérica** (valor predeterminado): escriba la **longitud mínima de la contraseña** que un usuario debe escribir (entre 4 y 16 caracteres).
  - **Al menos alfanumérico con símbolos**: escriba la **longitud mínima** de la contraseña que un usuario debe escribir, entre 4 y 16 caracteres.

- **Máximo de minutos de inactividad antes de solicitar la contraseña**: indique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir la contraseña. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Número de días hasta que expira la contraseña**: seleccione el número de días que faltan para que expire la contraseña y durante los cuales el usuario debe crear otra.
- **Número de contraseñas anteriores que no se pueden reutilizar**: indique el número de contraseñas recientes que no se pueden volver a usar. Utilice esta configuración para impedir que el usuario cree contraseñas usadas anteriormente.

#### <a name="encryption"></a>Cifrado

- **Cifrado de almacenamiento de datos en el dispositivo**: elija **Requerir** para cifrar el almacenamiento de datos en los dispositivos. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración. 

  No tiene que configurar este valor ya que los dispositivos Android Enterprise fuerzan el cifrado.

#### <a name="device-security"></a>Seguridad de dispositivos

- **Bloquear aplicaciones de orígenes desconocidos**: elija **bloquear** los dispositivos con la opción **Seguridad** > **Orígenes desconocidos** habilitada (se admite de Android 4.0 a Android 7.x; no se admite en Android 8.0 ni versiones posteriores). Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

  Para realizar instalaciones de prueba de las aplicaciones, se deben permitir los orígenes desconocidos. Si no realiza instalaciones de prueba de las aplicaciones Android, establezca esta característica en **Bloquear** para habilitar esta directiva de cumplimiento.

  > [!IMPORTANT]
  > Las aplicaciones de instalación de prueba requieren que se habilite la opción **Bloquear aplicaciones de orígenes desconocidos**. Aplique esta directiva de cumplimiento solo si no realiza instalaciones de prueba de las aplicaciones Android en dispositivos.

  No tiene que configurar este valor ya que los dispositivos Android Enterprise siempre restringen la instalación desde orígenes desconocidos.

- **Integridad en tiempo de ejecución de la aplicación Portal de empresa**: elija **Requerir** para confirmar que la aplicación Portal de empresa cumple los siguientes requisitos:

  - Tiene instalado el entorno de tiempo de ejecución predeterminado.
  - Está firmada correctamente.
  - No se encuentra en modo de depuración.
  - Se ha instalado desde un origen conocido.

  Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

- **Bloquear depuración USB en el dispositivo**: elija **Bloquear** para evitar que los dispositivos usen la característica de depuración USB. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

  No es necesario configurar esta opción porque la depuración USB ya está deshabilitada en los dispositivos Android Enterprise.

- **Nivel mínimo de revisión de seguridad**: seleccione el nivel de revisión de seguridad más antiguo que puede tener un dispositivo. Los dispositivos que no estén al menos en este nivel de revisión se consideran no conformes. La fecha debe especificarse en el formato *AAAA-MM-DD*.

## <a name="next-steps"></a>Pasos siguientes

- [Agregar acciones para dispositivos no compatibles](actions-for-noncompliance.md) y [usar etiquetas de ámbito para filtrar directivas](scope-tags.md).
- [Supervisar las directivas de cumplimiento](compliance-policy-monitor.md).
- Vea [Configuración de directivas de cumplimiento para dispositivos Android](compliance-policy-create-android.md).
