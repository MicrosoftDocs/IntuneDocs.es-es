---
title: 'Configuración de educación de Windows 8.1 en Microsoft Intune: Azure | Microsoft Docs'
description: Ver una lista de todas las opciones que puede usar al establecer el cumplimiento de los dispositivos Windows 8.1 y Windows Phone 8.1 en Microsoft Intune. Comprobación de compatibilidad en el sistema de operativo mínimo y máximo, establecer restricciones de contraseña y la longitud, habilitar el cifrado en el almacenamiento de datos y mucho más.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4ed863378616f8001beab89177c642404287e7d3
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424959"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Configuración de Windows 8.1 para marcar los dispositivos como compatible o no compatible con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En este artículo se enumera y se describe la configuración de cumplimiento diferentes que puede configurar en dispositivos Windows 8.1 en Intune. Como parte de la solución de administración (MDM) de dispositivos móviles, use estas opciones para bloquear contraseñas simples, establezca como mínimo y máximo versión del sistema operativo y mucho más.

Esta característica se aplica a:

- Windows Phone 8,1
- Windows 8.1 y posterior

Como administrador de Intune, use esta configuración de cumplimiento para ayudar a proteger los recursos de la organización. Para más información sobre las directivas de cumplimiento, consulte [Introducción a las directivas de cumplimiento de dispositivos de Intune](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de comenzar

[Crear una directiva de cumplimiento](create-compliance-policy.md#create-the-policy). Para **plataforma**, seleccione **Windows Phone 8.1** o **Windows 8.1 y versiones posteriores**.

## <a name="device-properties"></a>Propiedades del dispositivo

- **SO mínimo requerido**: especifique la versión mínima permitida. cuando un dispositivo no cumple el requisito de versión mínima del sistema operativo, se notifica como no conforme. Además, se mostrará un vínculo con información sobre cómo actualizar el sistema. El usuario final puede optar por actualizar el dispositivo y luego acceder a los recursos de la empresa.
- **Versión de SO máxima permitida**: especifique la versión máxima permitida. cuando un dispositivo usa una versión de SO posterior a la de la especificada en la regla, se bloquea el acceso a los recursos de la empresa. Se solicita al usuario que se ponga en contacto con el administrador de TI. El dispositivo no puede acceder a recursos de la organización hasta que cambie la regla para permitir la versión del SO.

Los equipos con Windows 8.1 devuelven la versión **3**. Si la regla de la versión de sistema operativo se establece en Windows 8.1 para Windows, el dispositivo se notificará como no conforme aunque tenga Windows 8.1.

## <a name="system-security"></a>Seguridad del sistema

### <a name="password"></a>Contraseña

- **Requerir una contraseña para desbloquear dispositivos móviles**: **requiere** que los usuarios escriban una contraseña antes de poder tener acceso a sus dispositivos.
- **Contraseñas sencillas**: establezca esta opción en **Bloquear** para que los usuarios no puedan crear contraseñas sencillas como **1234** o **1111**. Establézcala en **No configurado** para permitir a los usuarios crear contraseñas como **1234** o **1111**.
- **Longitud mínima de la contraseña**: indique el número mínimo de dígitos o caracteres que debe tener la contraseña.

  Para los dispositivos que ejecutan Windows y a los que se accede con una cuenta de Microsoft, la directiva de cumplimiento no se puede evaluar correctamente:
  - Si la longitud mínima de la contraseña es superior a ocho caracteres
  - O si el número mínimo de conjuntos de caracteres es superior a dos

- **Tipo de contraseña**: elija si una contraseña debe tener solo caracteres **numéricos** o si es necesario combinar números y otros caracteres (**alfanuméricos**).
  
  - **Número de caracteres no alfanuméricos en la contraseña**: si la opción **Tipo de contraseña requerida** está establecida en **Alfanumérico**, esta configuración especifica el número mínimo de caracteres que debe contener la contraseña. Los conjuntos de cuatro caracteres son los siguientes:
    - Letras minúsculas
    - Letras mayúsculas
    - Símbolos
    - Números

    Para establecer un número mayor, es necesario que el usuario cree una contraseña más compleja. Para los dispositivos a los que se accede con una cuenta de Microsoft, la directiva de cumplimiento no se puede evaluar correctamente:

    - Si la longitud mínima de la contraseña es superior a ocho caracteres
    - O si el número mínimo de conjuntos de caracteres es superior a dos

- **Máximo de minutos de inactividad antes de solicitar la contraseña**: indique el tiempo de inactividad que transcurre antes de que el usuario deba volver a escribir la contraseña.
- **Expiración de la contraseña (días)**: seleccione el número de días que faltan para que la contraseña expire y se deba crear una nueva.
- **Número de contraseñas anteriores que no se pueden reutilizar**: escriba el número de contraseñas usadas anteriormente que no se pueden utilizar.

### <a name="encryption"></a>Cifrado

- **Require encryption on mobile device** (Requerir cifrado en dispositivo móvil): **requerir** que el dispositivo se cifre para conectarse a recursos de almacenamiento de datos.

Seleccione **Aceptar** > **Crear** para guardar los cambios.

## <a name="next-steps"></a>Pasos siguientes

- [Adición de acciones para dispositivos no conformes](actions-for-noncompliance.md) y [usan etiquetas de ámbito para filtrar directivas](scope-tags.md).
- [Supervisar las directivas de cumplimiento de normas](compliance-policy-monitor.md).
- Consulte la [configuración de directiva de cumplimiento para Windows 10 y versiones posteriores](compliance-policy-create-windows.md) dispositivos.