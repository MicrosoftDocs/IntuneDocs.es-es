---
title: "Configuración de restricciones de dispositivos de Intune para Android for Work"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune en Azure: Obtenga información sobre la configuración de Intune que puede usar para controlar la configuración y funcionalidad en dispositivos Android for Work."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1830720b-16cb-4f2f-a71a-62967f882563
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 03fec9d22e705ccb27f4eb1f8f82c7ace95e841e
ms.openlocfilehash: c5cff131e7bcedadbad42fe6ab8bf00017f933ff
ms.contentlocale: es-es
ms.lasthandoff: 04/26/2017


---

# <a name="android-for-work-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos de Android for Work en Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="work-profile-settings"></a>Configuración de perfil profesional
-     **Uso compartido de datos entre el perfil profesional y el personal**: utilice esta opción para controlar si las aplicaciones del perfil profesional pueden compartir datos con aplicaciones del perfil personal. Elija de entre las siguientes opciones:
    - **Restricciones de uso compartido predeterminadas**: se trata del comportamiento predeterminado del dispositivo que varía según la versión de Android que se está ejecutando. De forma predeterminada, se permite el uso compartido desde el perfil personal hasta el perfil profesional. También de forma predeterminada, el uso compartido entre el perfil profesional y el perfil personal está bloqueado. Esto evita la fuga de datos desde el perfil profesional hasta el perfil personal. Google no proporciona una manera de bloquear datos que van desde el perfil personal hasta el perfil profesional en dispositivos que ejecutan versiones anteriores a la 6.0.  
    - **Las aplicaciones del perfil profesional pueden controlar una solicitud de uso compartido del perfil personal**: utilice esta opción para habilitar la característica de Android integrada que permite el uso compartido desde el perfil personal hasta el perfil profesional. Cuando esta opción está habilitada, una solicitud de uso compartido iniciada desde una aplicación del perfil personal se puede compartirá con aplicaciones del perfil profesional. Este es el comportamiento predeterminado para dispositivos Android que ejecutan versiones anteriores a la 6.0.
    - **Las aplicaciones del perfil personal pueden controlar una solicitud de uso compartido del perfil profesional**: esta opción habilita el uso compartido a través del límite de perfil profesional en ambas direcciones. Cuando se selecciona esta opción, las aplicaciones del perfil profesional pueden compartir datos con aplicaciones no administradas del perfil personal.  Utilice esta opción con cuidado ya que esto permite que datos administrados del perfil profesional se transfieran al lado no administrado del dispositivo.


-     **Notificaciones del perfil profesional con dispositivo bloqueado**: controle si las aplicaciones del perfil profesional pueden mostrar notificaciones en pantalla cuando el dispositivo está bloqueado.
-     **Permisos de aplicación predeterminados**: establece la directiva de permisos predeterminada para todas las aplicaciones del perfil profesional. A partir de 6 Android, algunos permisos requeridos por las aplicaciones se solicitan al usuario final en tiempo de ejecución. Esta configuración de directiva permite decidir si se les pide a los usuarios que concedan permisos para las aplicaciones en el perfil profesional y cómo se lleva a cabo esta petición.
Por ejemplo, se inserta una aplicación en el perfil profesional que requiere acceso de ubicación. Normalmente, esa aplicación mostraría un cuadro de diálogo al usuario en el que se preguntaría si desea conceder el acceso de ubicación a la aplicación y el usuario podría aprobarlo o rechazarlo. Esta directiva permite decidir si todos los permisos se deben conceder automáticamente sin preguntar, denegar automáticamente sin preguntar o dejar que el usuario final decida. Elija de entre las siguientes opciones:
    -     **Valor predeterminado del dispositivo**
    -     **Pedir confirmación**
    -     **Concesión automática**
    -     **Denegación automática**

## <a name="password"></a>Contraseña

- **Longitud mínima de la contraseña**: especifique el número mínimo de caracteres que debe contener la contraseña del usuario (**4**-**14**).
- **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: seleccione la cantidad de tiempo antes de que un dispositivo inactivo se bloquee automáticamente.
- **Número de errores de inicio de sesión antes de borrar el dispositivo**: especifique el número de veces que una contraseña incorrecta puede introducirse antes de que se borren todos los datos del dispositivo.
- **Expiración de la contraseña (días)**: especifique el número de días hasta que se deba cambiar la contraseña de un usuario final (**1**-**255**).
- **Tipo de contraseña requerida**: seleccione el tipo de contraseña que se debe establecer en el dispositivo. Elija de entre las siguientes opciones:
    - **Valor predeterminado del dispositivo**
    - **Biométrica de seguridad baja**
    - **Requerido**
    - **Al menos numérica**
    - **Compleja numérico** (no se permiten números repetidos o consecutivos, como '1111' o '1234')
    - **Al menos alfabética**
    - **Al menos alfanumérica**
    - **Al menos alfanumérica con símbolos**
- **Impedir la reutilización de contraseñas anteriores**: especifique el número de nuevas contraseñas que deben haberse utilizado antes de que se pueda reutilizar una antigua (**1**-**24**).
- **Desbloqueo con huella digital**: impide que un usuario final utilice el escáner de huellas digitales de dispositivo para desbloquearlo.
- **Smart Lock y otros agentes de confianza**: esta opción le permite controlar la característica Smart Lock en dispositivos compatibles. Esta funcionalidad del teléfono, conocida también en ocasiones como agentes de confianza, le permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si este está en una ubicación de confianza (por ejemplo, cuando se conecta a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC). Puede usar esta opción para impedir que los usuarios configuren Smart Lock.

## <a name="custom-policy-settings"></a>Configuración de directivas personalizadas
Use la **directiva de configuración personalizada de Android for Work** de Microsoft Intune para implementar las opciones de configuración de OMA-URI, que sirve para controlar características en dispositivos Android for Work. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad está pensada para que se puedan implementar las opciones de configuración de Android que no se pueden definir con directivas de Intune.
Actualmente, Intune admite un número limitado de directivas personalizadas de Android. Vea los ejemplos de este tema para averiguar qué directivas se pueden configurar.

### <a name="general-settings"></a>Configuración general

|Nombre de la configuración|Detalles|
    |----------------|--------------------|
    |**Nombre** |Escriba un nombre único para la directiva personalizada de Android que permita identificarla en la consola de Intune.|
    |**Descripción** |Proporcione una descripción que ofrezca una visión general de la directiva personalizada de Android y otra información relevante que le ayude a encontrarla.|

### <a name="oma-uri-settings"></a>Configuración de OMA-URI

  |Nombre de la configuración|Detalles|
  |--------|--------------------|
  |**Nombre** |Escriba un nombre único para el valor OMA-URI que le ayude a identificarlo en la lista de valores de configuración.|
  |**Descripción** |Proporcione una descripción que ofrezca una visión general del valor y otra información relevante que le ayude a encontrarlo.|
    |**OMA-URI (distingue mayúsculas de minúsculas)** |Especifique el OMA-URI para el que desee suministrar un valor.|
  |**Tipo de datos** |Seleccione el tipo de datos en el que especificará este valor OMA-URI. Elija entre las siguientes las opciones **Cadena, Cadena (XML), Fecha y hora, Entero, Punto flotante** o **Booleano**.|
  |**Valor** |Especifique el valor para asociar con el OMA-URI especificado anteriormente.|

