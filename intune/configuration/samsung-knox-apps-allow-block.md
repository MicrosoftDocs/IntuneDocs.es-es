---
title: Directiva de Microsoft Intune para permitir o bloquear aplicaciones para Samsung Knox
titleSuffix: ''
description: Cree un perfil personalizado para permitir y bloquear aplicaciones para dispositivos Samsung Knox Standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b83a0339d87375502159467af323fceae5eb6e2
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207084"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Uso de directivas personalizadas en Microsoft Intune para permitir y bloquear aplicaciones para dispositivos Samsung Knox Standard 

Use los procedimientos de este artículo para crear una directiva personalizada de Microsoft Intune que cree una de las siguientes opciones:

- Una lista de aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo. Las aplicaciones de esta lista se bloquean y no se pueden ejecutar, aunque ya estuvieran instaladas en el momento en que se ha aplicado la directiva.
- Una lista de aplicaciones que los usuarios del dispositivo pueden instalar desde la tienda de Google Play. Solo las aplicaciones que enumere se pueden instalar. Desde la tienda no se puede instalar ninguna otra aplicación.

Esta configuración solo se puede usar en dispositivos que ejecutan Samsung Knox Standard.

## <a name="create-an-allowed-or-blocked-app-list"></a>Creación de una lista de aplicaciones permitidas o bloqueadas

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.
3. Escriba los valores siguientes:

    - **Nombre**: escriba un nombre descriptivo para el nuevo perfil. Asígnele un nombre a los perfiles para que pueda identificarlos de manera sencilla más adelante. Por ejemplo, un buen nombre de perfil es el **perfil personalizado de Windows Phone**.
    - **Descripción**: escriba una descripción con información general sobre la configuración y otros detalles importantes.
    - **Plataforma**: Seleccione **Android**.
    - **Tipo de perfil**: seleccione **personalizado**.

4. En **Configuración OMA-URI personalizada**, seleccione **Agregar**. Escriba los valores siguientes:

    Para ver una lista de aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo:

    - **Nombre**: Escriba **PreventStartPackages**.
    - **Descripción**: escriba una descripción que proporcione información general sobre el valor y cualquier otra información relevante que ayude a encontrar el perfil. Por ejemplo, escriba la **lista de aplicaciones que no se pueden ejecutar**.
    - **OMA-URI** (distingue mayúsculas de minúsculas): Escriba **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**.
    - **Tipo de datos**: seleccione **cadena**.
    - **Valor**: Escriba una lista de los nombres del paquete de aplicaciones que quiere permitir. Puede usar `;`, `:` o `|` como delimitadores. Por ejemplo, escriba `package1;package2;`.

   Para obtener una lista de las aplicaciones que los usuarios pueden instalar de Google Play Store al excluir todas las demás aplicaciones:

    - **Nombre**: Escriba **AllowInstallPackages**.
    - **Descripción**: escriba una descripción que proporcione información general sobre el valor y cualquier otra información relevante que ayude a encontrar el perfil. Por ejemplo, escriba una **lista de las aplicaciones que los usuarios pueden instalar desde Google Play**.
    - **OMA-URI** (distingue mayúsculas de minúsculas): Escriba **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**.
    - **Tipo de datos**: seleccione **cadena**.
    - **Valor**: Escriba una lista de los nombres del paquete de aplicaciones que quiere permitir. Puede usar `;`, `:` o `|` como delimitadores. Por ejemplo, escriba `package1;package2;`.

5. Haga clic en **Aceptar** para guardar los cambios.
6. Cuando termine, seleccione **Aceptar** > **Crear** para crear el perfil de Intune. Una vez hecho, el perfil aparece en la lista **Dispositivos - Perfiles de configuración**.

>[!TIP]
> Puede encontrar el identificador del paquete de una aplicación dirigiéndose a la aplicación en Google Play Store. El identificador del paquete se incluye en la dirección URL de la página de la aplicación. Por ejemplo, el identificador del paquete de la aplicación Microsoft Word es **com.microsoft.office.word**.

La siguiente vez que se registra cada dispositivo de destino, se aplica la configuración de la aplicación.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero todavía no hace nada. Después, [asigne el perfil](../device-profile-assign.md) y [supervise el estado](device-profile-monitor.md).
