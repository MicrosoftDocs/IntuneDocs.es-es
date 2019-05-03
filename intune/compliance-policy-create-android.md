---
title: Creación de una directiva de cumplimiento de dispositivos Android en Microsoft Intune - Azure | Microsoft Docs
description: Ver una lista de todas las opciones que puede usar al establecer el cumplimiento de los dispositivos Android en Microsoft Intune. Establecer reglas de contraseña, elija una versión de sistema operativo mínimo o máximo, restringir aplicaciones específicas, evitar reutilizar contraseñas y mucho más.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7670af46657fed048bfe10b8659eae6d45db7620
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423584"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Configuración de Android para marcar los dispositivos como compatible o no compatible con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo se enumera y se describe la configuración de cumplimiento diferentes que puede configurar en dispositivos Android en Intune. Como parte de la solución de administración (MDM) de dispositivos móviles, use estas opciones para marcar los dispositivos liberados (descodificados) como no conforme, establecer un nivel de amenaza permitido, habilitar Google Play Protect y mucho más.

Esta característica se aplica a:

- Android

Como administrador de Intune, use esta configuración de cumplimiento para ayudar a proteger los recursos de la organización. Para más información sobre las directivas de cumplimiento, consulte [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Crear una directiva de cumplimiento](create-compliance-policy.md#create-the-policy). Para **Plataforma**, seleccione **Android**.

## <a name="device-health"></a>Device health

- **Dispositivos raíz**: elija **Bloquear** para marcar los dispositivos raíz (con jailbreak) como no conformes. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Requerir que el dispositivo tenga el nivel de amenaza del dispositivo**: use esta opción para hacer que la evaluación del riesgo de la solución Lookout MTP sea una condición para el cumplimiento. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración. Para usar esta configuración, elija el nivel de amenaza permitido:
  - **Protegido**: esta opción es la más segura y el dispositivo no puede tener ninguna amenaza. Si se detecta cualquier nivel de amenaza en el dispositivo, se evaluará como no conforme.
  - **Bajo**: el dispositivo se evalúa como conforme si solo hay amenazas de nivel bajo. Cualquier valor por encima coloca al dispositivo en un estado de no conformidad.
  - **Medio:** el dispositivo se evalúa como compatible si las amenazas existentes en él son de nivel bajo o medio. Si se detecta que el dispositivo tiene amenazas de nivel alto, se determina como no conforme.
  - **Alto**: esta opción es la menos segura, ya que permite que todos los niveles de amenaza. Quizás sea útil si utiliza esta solución solo con fines informativos.

### <a name="google-play-protect"></a>Protección de Google Play

- **Google Play Services está configurado**: se **requiere** que la aplicación Google Play Services esté instalada y habilitada. Google Play Services permite actualizaciones de seguridad y es una dependencia de nivel base para muchas características de seguridad en los dispositivos de Google certificados. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Proveedor de seguridad actualizada**: se **requiere** que un proveedor de seguridad actualizado pueda proteger un dispositivo frente a vulnerabilidades conocidas. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Examen de amenazas en las aplicaciones**: se **requiere** que la característica **Verificar aplicaciones** de Android esté habilitada. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

  > [!NOTE]
  > En la plataforma Android heredada, esta característica es una configuración de cumplimiento. Intune solo puede comprobar si esta configuración está habilitada en el nivel de dispositivo.

- **Atestación de dispositivo SafetyNet**: especifique el nivel de [atestación de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que se debe cumplir. Las opciones son:
  - **Sin configurar** (valor predeterminado): no se evalúa el cumplimiento o incumplimiento de esta configuración.
  - **Comprobar integridad básica**
  - **Comprobar integridad básica y dispositivos certificados**

> [!NOTE]
> Para configurar la configuración de Google Play Protect con directivas de protección, consulte [configuración de directiva de protección de aplicaciones de Intune](app-protection-policy-settings-android.md#conditional-launch) en Android.

## <a name="device-property-settings"></a>Configuración de propiedades de dispositivo

- **Versión mínima del sistema operativo**: cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no conforme. Se muestra un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo y luego acceder a los recursos de la empresa.
- **Versión máxima de SO**: cuando un dispositivo usa una versión de SO posterior a la especificada en la regla, se bloquea el acceso a los recursos de la empresa. Se solicita al usuario que se ponga en contacto con el administrador de TI. Mientras no se cambie la regla para permitir la versión de SO, el dispositivo no podrá acceder a los recursos de la empresa.

## <a name="system-security-settings"></a>Configuración de seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: **requiere** que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Longitud mínima de la contraseña**: indique el número mínimo de dígitos o caracteres que debe tener la contraseña del usuario.
- **Tipo de contraseña requerida**: elija si una contraseña debe incluir solo caracteres numéricos o una combinación de números y otros caracteres. Las opciones son:
  - **Valor predeterminado del dispositivo**
  - **Biométrico de seguridad baja**
  - **Al menos numérica** (valor predeterminado)
  - **Numérica compleja**: no se permiten números consecutivos ni repetidos (como `1111` o `1234`).
  - **Al menos alfabética** 
  - **Al menos alfanumérica**
  - **Al menos alfanumérica con símbolos**

- **Máximo de minutos de inactividad antes de solicitar la contraseña**: indique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir la contraseña. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Expiración de la contraseña (días)**: seleccione el número de días que faltan para que expire la contraseña y durante los cuales el usuario debe crear otra.
- **Número de contraseñas anteriores que no se pueden reutilizar**: indique el número de contraseñas recientes que no se pueden volver a usar. Utilice esta configuración para impedir que el usuario cree contraseñas usadas anteriormente.

### <a name="encryption"></a>Cifrado

- **Cifrado de almacenamiento de datos en un dispositivo** (Android 4.0 y versiones posteriores, o KNOX 4.0 y versiones posteriores): elija **Requerir** para cifrar el almacenamiento de datos en los dispositivos. Los dispositivos se cifran al elegir la opción **Requerir una contraseña para desbloquear dispositivos móviles**. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

### <a name="device-security"></a>Seguridad de dispositivos

- **Bloquear aplicaciones de orígenes desconocidos**: elija **bloquear** los dispositivos con la opción "Seguridad > Orígenes desconocidos" habilitada (se admite de Android 4.0 a Android 7.x; no se admite en Android 8.0 ni versiones posteriores). Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

  Para realizar instalaciones de prueba de las aplicaciones, se deben permitir los orígenes desconocidos. Si no realiza instalaciones de prueba de las aplicaciones Android, establezca esta característica en **Bloquear** para habilitar esta directiva de cumplimiento. 

  > [!IMPORTANT]
  > Las aplicaciones de instalación de prueba requieren que se habilite la opción **Bloquear aplicaciones de orígenes desconocidos**. Aplique esta directiva de cumplimiento solo si no realiza instalaciones de prueba de las aplicaciones Android en dispositivos.

- **Integridad en tiempo de ejecución de la aplicación Portal de empresa**: elija **Requerir** para confirmar que la aplicación Portal de empresa cumple los siguientes requisitos:

  - Tiene instalado el entorno de tiempo de ejecución predeterminado.
  - Está firmada correctamente.
  - No se encuentra en modo de depuración.
  - Se ha instalado desde un origen conocido.

  Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.

- **Bloquear depuración USB en el dispositivo** (Android 4.2 o versiones posteriores): elija **Bloquear** para evitar que los dispositivos usen la característica de depuración USB. Si elige **Sin configurar** (valor predeterminado), no se evalúa el cumplimiento o incumplimiento de esta configuración.
- **Nivel mínimo de revisión de seguridad** (Android 6.0 o posterior): seleccione el nivel de revisión de seguridad más antiguo que puede tener un dispositivo. Los dispositivos que no estén al menos en este nivel de revisión se consideran no conformes. La fecha debe especificarse en el formato `YYYY-MM-DD`.
- **Aplicaciones restringidas**: escriba el **Nombre de la aplicación** y el **Identificador de lote de aplicaciones** de las aplicaciones que deben estar restringidas. Seleccione **Agregar**. Un dispositivo con al menos una aplicación restringida instalada se marca como no conforme.

Seleccione **Aceptar** > **Crear** para guardar los cambios.

## <a name="locations"></a>Ubicaciones

En la directiva, puede forzar cumplimiento por la ubicación del dispositivo. Elija entre ubicaciones existentes. ¿Aún no tiene una ubicación? En el apartado [Usar ubicaciones (límite de red) en Intune](use-network-locations.md) se proporcionan algunas instrucciones.

1. Elija **ubicaciones** > **seleccionar ubicaciones**.
2. En la lista, compruebe su ubicación > **seleccione**.
3. Haga clic en **Guardar** la directiva.

## <a name="next-steps"></a>Pasos siguientes

- [Adición de acciones para dispositivos no conformes](actions-for-noncompliance.md) y [usan etiquetas de ámbito para filtrar directivas](scope-tags.md).
- [Supervisar las directivas de cumplimiento de normas](compliance-policy-monitor.md).
- [Configuración de directivas de cumplimiento para Android Enterprise](compliance-policy-create-android-for-work.md)
