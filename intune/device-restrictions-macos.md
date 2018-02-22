---
title: "Configuración de restricciones de dispositivo de Intune para macOS"
titlesuffix: Azure portal
description: "Conozca la configuración de Intune que puede usar para controlar los valores de configuración y la funcionalidad de los dispositivos macOS."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/31/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a88cf11209726a622863339c3a6c117f7b83be1e
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="macos-device-restriction-settings-in-microsoft-intune"></a>Configuración de restricciones de dispositivos macOS en Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use estas opciones para administrar dispositivos macOS en un perfil de restricción de dispositivos.

## <a name="password"></a>Contraseña
-   **Contraseña**: exige que el usuario final escriba una contraseña para acceder al dispositivo.
    -   **Tipo de contraseña necesaria**: especifique si la contraseña solo puede ser numérica o si debe ser alfanumérica (contener letras y números). Esta configuración solo es compatible con Mac OS X versión 10.10.3 y posteriores.
    -   **Número de caracteres no alfanuméricos en la contraseña**: especifique el número de caracteres complejos necesarios en la contraseña (de **0** a **4**).<br>Un carácter complejo es un símbolo, por ejemplo, "**?**".
    -   **Minimum password length** (Longitud mínima de contraseña): escriba la longitud mínima de contraseña que un usuario debe configurar (entre **4** y **16** caracteres).
    -   **Contraseñas sencillas**: permita el uso de contraseñas sencillas, como **0000** o **1234**.
    -   **Máximo de minutos tras bloqueo de pantalla antes de solicitar la contraseña**: especifique cuánto tiempo el equipo debe estar inactivo antes de que se requiera una contraseña para desbloquearlo.
    -   **Máximo de minutos de inactividad hasta que se bloquea la pantalla**: especifique el período de tiempo que el equipo debe estar inactivo antes de la pantalla se bloquee.
    -   **Caducidad de la contraseña (días)**: especifique cuántos días deben transcurrir antes de que el usuario deba cambiar la contraseña (de **1** a **255** días).
    -   **Impedir la reutilización de contraseñas anteriores**: especifique el número de contraseñas de usuario usadas anteriormente que no se pueden volver a utilizar (de **1** a **24**).

## <a name="restricted-apps"></a>Aplicaciones restringidas

En la lista de aplicaciones restringidas, puede configurar una de las listas siguientes:

- **Aplicaciones prohibidas**: aplicaciones (no administradas por Intune) que los usuarios no pueden instalar ni ejecutar. Los usuarios pueden instalar una aplicación prohibida, aunque, si lo hacen, usted recibirá una notificación.
- **Aplicaciones aprobadas**: aplicaciones que los usuarios pueden instalar. Los usuarios no deben instalar aplicaciones que no se muestren en la lista. Las aplicaciones que se administran mediante Intune están permitidas automáticamente. Los usuarios pueden instalar una aplicación que no esté en la lista de aprobadas, aunque, si lo hacen, usted recibirá una notificación.

Para configurar la lista, haga clic en **Agregar**, especifique un nombre de su elección (puede ser el publicador de la aplicación) y el identificador de paquete de la aplicación (por ejemplo *com.apple.calculator*).

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Dominios de correo electrónico no marcados

En el campo **Email Domain URL** (Dirección URL de dominio de correo electrónico), agregue una o más direcciones URL a la lista. Cuando los usuarios finales reciben un correo electrónico de un dominio distinto del que ha configurado, el correo electrónico se marca como correo electrónico de no confianza en la aplicación Mail de iOS.

