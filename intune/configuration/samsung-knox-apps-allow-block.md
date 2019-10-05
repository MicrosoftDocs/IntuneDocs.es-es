---
title: Directiva de Microsoft Intune para permitir o bloquear aplicaciones para Samsung Knox
titleSuffix: ''
description: Cree un perfil personalizado para permitir y bloquear aplicaciones para dispositivos Samsung Knox Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8486e121e6497eefdd2d098c2421f2f3b53b8a2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734354"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Uso de directivas personalizadas en Microsoft Intune para permitir y bloquear aplicaciones para dispositivos Samsung Knox Standard 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Use los procedimientos de este artículo para crear una directiva personalizada de Microsoft Intune que cree una de las siguientes opciones:

- Una lista de aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo. Las aplicaciones de esta lista se bloquean y no se pueden ejecutar, aunque ya estuvieran instaladas en el momento en que se ha aplicado la directiva.
- Una lista de aplicaciones que los usuarios del dispositivo pueden instalar desde la tienda Google Play. Solo las aplicaciones que enumere se pueden instalar. Desde la tienda no se puede instalar ninguna otra aplicación.

Esta configuración solo se puede usar en dispositivos que ejecutan Samsung Knox Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Creación de una lista de aplicaciones permitidas o bloqueadas

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel **Intune**, elija **Configuración del dispositivo**.
2. En el panel **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
2. En la hoja de lista de perfiles, elija **Crear perfil**.
3. En el panel **Crear perfil**, escriba un **Nombre** y una **Descripción** opcional para el perfil de dispositivo.
2. En **Plataforma**, elija **Android** y, en **Tipo de perfil**, **Personalizado**.
3. Haga clic en **Configuración**.
3. En el panel **Configuración OMA-URI personalizada**, elija **Agregar**.
4. En el cuadro de diálogo **Agregar o editar configuración OMA-URI**, especifique la siguiente configuración:

   Para ver una lista de aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo:

   - **Nombre**: escriba **PreventStartPackages**.
   - **Descripción**: escriba una descripción opcional, por ejemplo, "Lista de aplicaciones bloqueadas que no se pueden ejecutar".
   - **Tipo de datos**: en la lista desplegable, elija **Cadena**.
   - **OMA-URI**: escriba **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**.
   - **Valor**: escriba una lista de los nombres de paquetes de aplicaciones que quiere permitir. Puede usar **; : ,** o **|** como delimitador. (Ejemplo: paquete1;paquete2;)

   Para obtener una lista de las aplicaciones que los usuarios pueden instalar de Google Play Store al excluir todas las demás aplicaciones:
   - **Nombre**: escriba **AllowInstallPackages**.
   - **Descripción**: escriba una descripción opcional, por ejemplo, "Lista de aplicaciones que los usuarios pueden instalar desde Google Play".
   - **Tipo de datos**: en la lista desplegable, elija **Cadena**.
   - **OMA-URI**: escriba **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**.
   - **Valor**: escriba una lista de los nombres de paquetes de aplicaciones que quiere permitir. Puede usar **; : ,** o **|** como delimitador. (Ejemplo: paquete1;paquete2;)

4. Haga clic en **Aceptar** y, luego, en el panel **Crear perfil**, elija **Crear**.

>[!TIP]
> Puede encontrar el identificador del paquete de una aplicación dirigiéndose a la aplicación en Google Play Store. El identificador del paquete se incluye en la dirección URL de la página de la aplicación. Por ejemplo, el identificador del paquete de la aplicación Microsoft Word es **com.microsoft.office.word**.

La próxima vez que se registre cada dispositivo de destino, se aplicará la configuración de la aplicación.


<!---## Assign the custom profile--->
