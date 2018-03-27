---
title: Aplicaciones bloqueadas y permitidas para KNOX
description: Perfil personalizado para crear una lista de aplicaciones permitidas y bloqueadas para KNOX
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/02/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a47e1388f640f96c2650e284ae0a5311fd816ba7
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="use-custom-policies-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Uso de directivas personalizadas para permitir y bloquear aplicaciones para dispositivos Samsung KNOX Standard

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Use los procedimientos de este tema para crear una directiva personalizada de Microsoft Intune que cree una de las siguientes opciones:

- Una lista de aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo. Las aplicaciones de esta lista se bloquean y no se pueden ejecutar, aunque ya estuvieran instaladas en el momento en que se ha aplicado la directiva.
- Una lista de aplicaciones que los usuarios del dispositivo pueden instalar desde la tienda Google Play. Solo las aplicaciones que enumere se pueden instalar. Desde la tienda no se puede instalar ninguna otra aplicación.

Esta configuración solo se puede usar en dispositivos que ejecutan Samsung KNOX Standard.

## <a name="to-create-an-allowed-or-blocked-app-list"></a>Para crear una lista de aplicaciones permitidas o bloqueadas

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), elija **Directiva** &gt; **Directivas de configuración** &gt; **Agregar**.
2. En el cuadro de diálogo **Crear nueva directiva**, expanda **Android**, elija **Configuración personalizada** y, después, elija **Crear directiva**.
3. Proporcione un nombre y una descripción opcional a la directiva y, después, en la sección **Configuración OMA-URI** elija **Agregar**.
4. En el cuadro de diálogo **Agregar o editar configuración OMA-URI**, especifique lo siguiente para obtener una lista de las aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo:
    
    - **Nombre de la configuración** Escriba **PreventStartPackages**.
    - **Descripción del valor** Escriba una descripción opcional como "Lista de aplicaciones bloqueadas que no se pueden ejecutar".
    -   **Tipo de datos** En la lista desplegable, elija **Cadena**.
    -   **OMA-URI.** Escriba **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
    -   **Valor** Escriba una lista de los nombres de paquetes de aplicaciones que quiera bloquear. Puede usar **; : ,** o **|** como delimitador. (Ejemplo: paquete1;paquete2;)

    Para obtener una lista de las aplicaciones que los usuarios pueden instalar de Google Play Store al excluir todas las demás aplicaciones:

    - **Nombre de la configuración** Escriba **AllowInstallPackages**.
    - **Descripción del valor** Escriba una descripción opcional como "Lista de aplicaciones que los usuarios pueden instalar de Google Play".
    - **Tipo de datos** En la lista desplegable, elija **Cadena**.
    - **OMA-URI.** Escriba **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
    - **Valor** Escriba una lista de los nombres del paquete de aplicaciones que quiere permitir. Puede usar **; : ,** o **|** como delimitador. (Ejemplo: paquete1;paquete2;)

4. Haga clic en **Aceptar** y, después, en **Guardar directiva**. 

>[!TIP]
> Puede encontrar el identificador del paquete de una aplicación dirigiéndose a la aplicación en Google Play Store. El identificador del paquete se incluye en la dirección URL de la página de la aplicación. Por ejemplo, el identificador del paquete de la aplicación Microsoft Word es **com.microsoft.office.word**.

La próxima vez que se registre cada dispositivo de destino, se aplicará la configuración de la aplicación.


## <a name="deploy-the-policy"></a>Implementar la directiva

1.  En el área de trabajo **Directiva** , seleccione la directiva que quiera implementar y, a continuación, haga clic en **Administrar implementación**.

2.  En el cuadro de diálogo **Administrar implementación**, seleccione uno o varios grupos en los que quiera implementar la directiva y, después, haga clic en **Agregar** &gt; **Aceptar**.

 
Cuando se selecciona una directiva implementada, puede ver más información acerca de la implementación en la parte inferior de la lista de directivas.

### <a name="see-also"></a>Vea también
[Configuración de directivas de Android y Samsung KNOX en Microsoft Intune](android-policy-settings-in-microsoft-intune.md)
