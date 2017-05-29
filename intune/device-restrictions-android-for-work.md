---
title: "Configuración de restricciones de dispositivos de Intune para Android for Work | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: conozca los valores de configuración de Intune que puede usar para controlar la configuración y la funcionalidad de los dispositivos Android for Work."
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
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 857522ef4931407accf98b2a2ad97334278c138f
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="android-for-work-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos Android for Work en Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="work-profile-settings"></a>Configuración de perfil de trabajo
-     **Uso compartido de datos entre el perfil profesional y el perfil personal**: use esta configuración para controlar si las aplicaciones del perfil profesional pueden compartir datos con las aplicaciones del perfil personal. Elija de entre las siguientes opciones:
    - **Restricciones de uso compartido predeterminado**: se trata del comportamiento de uso compartido predeterminado del dispositivo que varía según la versión de Android que se ejecuta. De manera predeterminada, se permite el uso compartido desde el perfil personal al perfil profesional. También de manera predeterminada, el uso compartido entre el perfil profesional y el perfil personal está bloqueado. Esto evita la fuga de datos desde el perfil profesional al perfil personal. Google no proporciona ninguna forma de bloquear el paso de los datos desde el perfil personal al perfil profesional en dispositivos que ejecutan versiones anteriores a 6.0.  
    - **Las aplicaciones de un perfil profesional pueden controlar la solicitud de uso compartido desde un perfil personal**: use esta opción para habilitar la característica de Android integrada que permite el uso compartido desde el perfil personal al perfil profesional. Cuando esta opción está habilitada, una solicitud de uso compartido que se inicia en una aplicación del perfil personal se podrá compartir con las aplicaciones del perfil profesional. Este es el comportamiento predeterminado de los dispositivos Android que ejecutan versiones anteriores a 6.0.
    - **Las aplicaciones de un perfil personal pueden controlar la solicitud de uso compartido desde un perfil profesional**: esta opción habilita el uso compartido a través de los límites del perfil profesional en ambas direcciones. Cuando selecciona esta configuración, las aplicaciones del perfil profesional pueden compartir datos con aplicaciones no administradas del perfil personal.  Use esta configuración con precaución, porque esto permite que los datos administrados del perfil profesional se transfieran al lado no administrado del dispositivo.


-     **Notificaciones del perfil profesional con dispositivo bloqueado**: controla si las aplicaciones del perfil profesional pueden mostrar notificaciones en pantalla cuando el dispositivo está bloqueado.
-     **Permisos de aplicación predeterminados**: establece la directiva de permisos predeterminada para todas las aplicaciones del perfil profesional. A partir de Android 6, algunos permisos requeridos por las aplicaciones se solicitan al usuario final en tiempo de ejecución. Esta configuración de directiva permite decidir cómo o si se pide a los usuarios que concedan permisos para las aplicaciones en el perfil profesional.
Por ejemplo, puede insertar una aplicación en el perfil profesional que requiere acceso de ubicación. Normalmente, esa aplicación podría aparecer en un cuadro de diálogo al usuario preguntando si desea conceder el acceso de la ubicación a la aplicación y el usuario puede aprobarlo o rechazarlo. Esta directiva permite que decidir si todos los permisos deben concederse automáticamente sin preguntar al usuario, denegarse automáticamente sin preguntar al usuario o dejar que el usuario final decida. Elija de entre las siguientes opciones:
    -     **Valor predeterminado de dispositivo**
    -     **Aviso**
    -     **Concesión automática**
    -     **Denegación automática**

## <a name="password"></a>Contraseña

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
- **Smart Lock y otros agentes de confianza**: permite controlar la característica de Smart Lock en dispositivos compatibles. Esta funcionalidad del teléfono, conocida también en ocasiones como agentes de confianza, le permite deshabilitar u omitir la contraseña de la pantalla de bloqueo del dispositivo si este está en una ubicación de confianza (por ejemplo, cuando se conecta a un dispositivo Bluetooth específico o cuando está cerca de una etiqueta NFC). Puede usar esta opción para impedir que los usuarios configuren Smart Lock.

## <a name="custom-policy-settings"></a>Configuración de directivas personalizadas
Use la **directiva de configuración personalizada de Android for Work** de Microsoft Intune para asignar las opciones de configuración de OMA-URI, que sirve para controlar características en dispositivos Android for Work. Se trata de una configuración estándar que muchos fabricantes de dispositivos móviles usan para controlar las características del dispositivo.

Esta funcionalidad está pensada para que se puedan asignar las opciones de configuración de Android que no se pueden definir con directivas de Intune.
Intune admite un número limitado de directivas personalizadas de Android en este momento. Vea los ejemplos de este tema para averiguar qué directivas puede configurar.

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
  |**Tipo de datos** |Seleccione el tipo de fecha en que especificará este valor OMA-URI. Elija entre las siguientes las opciones **Cadena, Cadena (XML), Fecha y hora, Entero, Punto flotante** o **Booleano**.|
  |**Valor** |Especifique el valor para asociar con el OMA-URI especificado anteriormente.|

