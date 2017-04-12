---
title: Directiva de Intune para permitir o bloquear aplicaciones para Samsung KNOX
titleSuffix: Intune Azure preview
description: "Versión preliminar de Intune Azure: cree un perfil personalizado para permitir y bloquear aplicaciones para dispositivos Samsung KNOX Standard."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: a47ea4c8d3027cb34fd8ecd8324fac52c9846a77
ms.lasthandoff: 03/17/2017



---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices-in-microsoft-intune"></a>Uso de directivas personalizadas para permitir y bloquear aplicaciones para dispositivos Samsung KNOX Standard en Microsoft Intune
[!INCLUDE[azure_preview](../includes/azure_preview.md)]Use los procedimientos de este tema para crear una directiva personalizada de Microsoft Intune que cree una de las siguientes opciones:

- Una lista de aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo. Las aplicaciones de esta lista se bloquean y no se pueden ejecutar, aunque ya estuvieran instaladas en el momento en que se ha aplicado la directiva.
- Una lista de aplicaciones que los usuarios del dispositivo pueden instalar desde la tienda Google Play. Solo las aplicaciones que enumere se pueden instalar. Desde la tienda no se puede instalar ninguna otra aplicación.

Esta configuración solo se puede usar en dispositivos que ejecutan Samsung KNOX Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Creación de una lista de aplicaciones permitidas o bloqueadas

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configuración del dispositivo**.
2. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
2. En la hoja de lista de perfiles, elija **Create Profile** (Crear perfil).
3. En la hoja **Create Profile** (Crear perfil), escriba un **nombre** y una **descripción** opcional para el perfil de dispositivo.
2. En **Tipo de plataforma**, elija **Android** y un tipo de perfil **Personalizado**.
3. Haga clic en **Configuración**.
3. En la hoja **Configuración OMA-URI personalizada**, elija **Agregar**.
4. En el cuadro de diálogo **Agregar o editar configuración OMA-URI**, especifique la siguiente información:

### <a name="for-a-list-of-apps-that-are-blocked-from-running-on-the-device"></a>Para ver una lista de aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo:

- **Nombre**: escriba **PreventStartPackages**.
- **Descripción**: escriba una descripción opcional, por ejemplo, "Lista de aplicaciones bloqueadas que no se pueden ejecutar".
-     **Tipo de datos**: en la lista desplegable, elija **Cadena**.
-     **OMA-URI**: escriba **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**.
-     **Valor**: escriba una lista de los nombres de paquetes de aplicaciones que quiere permitir. Puede usar **; : ,** o **|** como delimitador. (Ejemplo: paquete1;paquete2;)

### <a name="for-a-list-of-apps-that-users-are-allowed-to-install-from-the-google-play-store-while-excluding-all-other-apps"></a>Para obtener una lista de las aplicaciones que los usuarios pueden instalar de Google Play Store al excluir todas las demás aplicaciones:
- **Nombre**: escriba **AllowInstallPackages**.
- **Descripción**: escriba una descripción opcional, por ejemplo, "Lista de aplicaciones que los usuarios pueden instalar desde Google Play".
- **Tipo de datos**: en la lista desplegable, elija **Cadena**.
- **OMA-URI**: escriba **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**.
- **Valor**: escriba una lista de los nombres de paquetes de aplicaciones que quiere permitir. Puede usar **; : ,** o **|** como delimitador. (Ejemplo: paquete1;paquete2;)

4. Haga clic en **Aceptar** y, luego, en la hoja **Create Profile** (Crear perfil), elija **Crear**.

>[!TIP]
> Puede encontrar el identificador del paquete de una aplicación dirigiéndose a la aplicación en Google Play Store. El identificador del paquete se incluye en la dirección URL de la página de la aplicación. Por ejemplo, el identificador del paquete de la aplicación Microsoft Word es **com.microsoft.office.word**.

La próxima vez que se registre cada dispositivo de destino, se aplicará la configuración de la aplicación.


<!---## Assign the custom profile--->

