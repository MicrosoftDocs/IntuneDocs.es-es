---
title: "Configuración de restricciones de dispositivo de Intune para macOS"
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: conozca los valores de configuración de Intune que puede usar para controlar la configuración y la funcionalidad de los dispositivos macOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3129cbaf-96c2-4837-8907-ca87a605a496
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c120c6af93234e153e4fb845942726a51bee98df
ms.contentlocale: es-es
ms.lasthandoff: 05/23/2017


---

# <a name="macos-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos macOS en Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="password"></a>Contraseña
-     **Contraseña necesaria**: exige que el usuario final escriba una contraseña para acceder al dispositivo.
    -     **Tipo de contraseña necesaria**: especifique si la contraseña solo puede ser numérica o si debe ser alfanumérica (contener letras y números). Esta configuración solo es compatible con Mac OS X versión 10.10.3 y posteriores.
    -     **Número de caracteres no alfanuméricos en la contraseña**: especifique el número de caracteres complejos necesarios en la contraseña (de **0** a **4**).<br>Un carácter complejo es un símbolo, como **?**.
    -     **Minimum password length** (Longitud mínima de contraseña): escriba la longitud mínima de contraseña que un usuario debe configurar (entre **4** y **16** caracteres).
    -     **Contraseñas sencillas**: permita el uso de contraseñas sencillas, como **0000** o **1234**.
    -     **Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña**: especifique cuánto tiempo el equipo debe estar inactivo antes de que se requiera una contraseña para desbloquearlo.
    -     **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique el período de tiempo que el equipo debe estar inactivo antes de la pantalla se bloquee.
    -     **Caducidad de la contraseña (días)**: especifique cuántos días deben transcurrir antes de que el usuario deba cambiar la contraseña (de **1** a **255** días).
    -     **Impedir la reutilización de contraseñas anteriores**: especifique el número de contraseñas de usuario usadas anteriormente que no se pueden volver a utilizar (de **1** a **24**).

## <a name="restricted-apps"></a>Aplicaciones restringidas

En la lista de aplicaciones restringidas, puede configurar una de las listas siguientes:

**Aplicaciones prohibidas**: aplicaciones (no administradas por Intune) que los usuarios no pueden instalar ni ejecutar.
**Aplicaciones aprobadas**: aplicaciones que los usuarios pueden instalar. Para mantener la conformidad, los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente.

Para configurar la lista, haga clic en **Agregar**, especifique un nombre de su elección (puede ser el publicador de la aplicación) y el identificador de paquete de la aplicación (por ejemplo *com.apple.calculator*).



