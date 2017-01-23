---

title: Opciones de directivas de Android for Work | Microsoft Docs
description: "Cree directivas que controlen la configuración y las características en los dispositivos Android for Work que administra con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 35a53076-74d6-486d-b201-e0da2e170008
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 6c5ea937e5f6e0c8d20c72e086de1faa17d0ad34


---

# <a name="android-for-work-policy-settings-in-microsoft-intune"></a>Opciones de directivas de Android for Work en Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

Intune proporciona una variedad de opciones generales integradas que puede configurar en los dispositivos Android for Work.

## <a name="general-configuration-policy"></a>Directiva de configuración general

Utilice la **directiva de configuración general de Android for Work** para configurar la seguridad y el perfil de trabajo de sus dispositivos Android for Work.

Si el valor que busca no aparece en este tema, puede crearlo mediante una directiva personalizada de Android que le permita usar la configuración de OMA-URI (identificador uniforme de recursos de Open Mobile Alliance) para controlar el dispositivo. Para obtener más información, vaya a [Configuración de directivas personalizadas](#custom-policy-settings).

> [!TIP]
> Los dispositivos se cifran automáticamente cuando se aprovisiona un perfil de trabajo. No se puede cambiar esta configuración.

### <a name="password-settings"></a>Configuración de contraseña

|Nombre de la configuración|Detalles|
|----------------|-|
|**Requerir una contraseña para desbloquear dispositivos móviles**|Especifica si se requiere una contraseña en los dispositivos administrados. Elija de entre las siguientes opciones:<br><br>- **Complejo**: requiere al menos una letra, un número y un símbolo.<br>- **Alfanumérico**: requiere al menos un número y un carácter alfabético.<br>- **Alfabético**: requiere al menos letras o símbolos.<br>- **Complejo numérico**: requiere caracteres numéricos que no son consecutivos o de repetición.<br>- **Numérico**<br><br>Si esta opción no está habilitada, no hay ningún requisito de complejidad.|
|**Longitud mínima de contraseña**|Especifica el número mínimo de caracteres o números de la contraseña.|
|**Minutos de inactividad antes de que se bloquee el dispositivo**|Especifica el número de minutos sin actividad del usuario antes de que el dispositivo se bloquee automáticamente.|
|**Permitir Smart Lock y otros agentes de confianza**<br>(Android 6 y versiones posteriores)|Vamos a controlar la característica Smart Lock en dispositivos Android compatibles. Esta funcionalidad del teléfono, conocida también en ocasiones como agentes de confianza, le permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si el dispositivo está en una ubicación de confianza (por ejemplo, cuando se conecta a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC). Puede usar esta opción para impedir que los usuarios configuren Smart Lock.|
|**Número de errores de inicio de sesión repetidos antes de que se quite el perfil de trabajo**|Especifica el número de errores de inicio de sesión que se permite antes de que se quite el perfil de trabajo del dispositivo. Esta opción no realiza un borrado completo del dispositivo.|
|**Recordar el historial de contraseñas**|Impide la reutilización de las contraseñas usadas anteriormente.|
|**Recordar historial de contraseñas** - **Impedir la reutilización de contraseñas anteriores**|Especifica el número de contraseñas usadas previamente que recordar.|
|**Expiración de contraseña (días)**|Especifica el número de días antes de que se deba cambiar la contraseña del dispositivo.|
|**Permitir desbloqueo mediante huellas digitales**<br>(Android 6 y versiones posteriores)|Le permite usar una huella digital para desbloquear dispositivos con esta funcionalidad.|


### <a name="work-profile-settings"></a>Configuración de perfil de trabajo

|Nombre de la configuración|Detalles|
|----------------|-|
|**Permitir uso compartido de datos entre perfiles de trabajo y personales**|Permite a las aplicaciones del perfil de trabajo compartir datos con las aplicaciones del perfil personal de los usuarios. Elija de entre las siguientes opciones:<br><br>- **Impide el uso compartido más allá de los límites**<br>- **Las aplicaciones de un perfil de trabajo pueden controlar la solicitud de uso compartido desde un perfil personal**<br>- **No hay restricciones para el uso compartido**|
|**Ocultar notificaciones del perfil de trabajo cuando el dispositivo está bloqueado**<br>(Android 6 y versiones posteriores)|Controle si se muestran las notificaciones del perfil de trabajo cuando el dispositivo está bloqueado.|
|**Establecer directiva de permisos de aplicación predeterminada**<br>(Android 6 y versiones posteriores)|Establece la directiva de permisos predeterminada para todas las aplicaciones del perfil de trabajo.|




## <a name="custom-policy-settings"></a>Configuración de directivas personalizadas
Use la **directiva de configuración personalizada de Android for Work** de Microsoft Intune para implementar las opciones de configuración de OMA-URI, que sirve para controlar características en dispositivos Android for Work. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta capacidad está pensada para que se puedan implementar las opciones de configuración de Android que no se pueden definir con directivas de Intune.
Intune admite un número limitado de directivas personalizadas de Android en este momento. Vea los ejemplos de este tema para averiguar qué directivas puede configurar.

### <a name="general-settings"></a>Configuración general

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre**|Escriba un nombre único para la directiva personalizada de Android que permita identificarla en la consola de Intune.|
    |**Descripción**|Proporcione una descripción que ofrezca una visión general de la directiva personalizada de Android y otra información relevante que le ayude a encontrarla.|

### <a name="oma-uri-settings"></a>Configuración de OMA-URI

   |Nombre de la configuración|Detalles|
    |--------|--------------------|
    |**Nombre de la configuración**|Escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.|
    |**Descripción del valor**|Proporcione una descripción que ofrezca una visión general del valor y otra información relevante que le ayude a encontrarlo.|
    |**Tipo de datos**|Seleccione el tipo de fecha en que especificará este valor OMA-URI. Elija entre las siguientes opciones **Cadena, Cadena (XML), Fecha y hora, Entero, Punto flotante** o **Booleano**.|
    |**OMA-URI (distingue mayúsculas de minúsculas)**|Especifique el OMA-URI para el que desee suministrar un valor.|
    |**Valor**|Especifique el valor asociado con el OMA-URI especificado anteriormente.|

### <a name="examples"></a>Ejemplos

- [Crear un perfil de Wi-Fi con una clave precompartida](pre-shared-key-wi-fi-profile.md)
- [Uso de una directiva personalizada para crear un perfil de VPN por aplicación para dispositivos Android](per-app-vpn-for-android-pulse-secure.md)

### <a name="see-also"></a>Consulte también
[Administrar la configuración y las características de los dispositivos con directivas de Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Dec16_HO2-->


