---
title: Aplicaciones permitidas y bloqueadas para KNOX | Microsoft Intune
description: Perfil personalizado para crear una lista de aplicaciones permitidas y bloqueadas para KNOX
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbc8e0df-7bf3-494e-8bc4-dac59a98ab41
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 65d2c9c1f5d81dae33422bd4bf7c0e2e21bb96e4
ms.openlocfilehash: 937e291f193f61329598395baa63c24d7fefa25f



---
# Usar directivas personalizadas para permitir y bloquear aplicaciones en los dispositivos Samsung KNOX

Use los procedimientos de este tema para crear una directiva personalizada de Microsoft Intune que cree una de las siguientes opciones:

- Una lista de aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo. No se podrá ejecutar ninguna otra aplicación. Las aplicaciones de esta lista se bloquean y no se pueden ejecutar, aunque ya estuvieran instaladas en el momento en que se ha aplicado la directiva.
- Una lista de aplicaciones que los usuarios del dispositivo pueden instalar desde la tienda Google Play. Solo las aplicaciones que enumere se pueden instalar. Desde la tienda no se puede instalar ninguna otra aplicación.

Esta configuración solo se puede usar en dispositivos que ejecutan Samsung KNOX.

## Para crear una lista de aplicaciones permitidas o bloqueadas

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), elija **Directiva** &gt; **Directivas de configuración** &gt; **Agregar**.
2. En el cuadro de diálogo **Crear nueva directiva**, expanda **Android**, elija **Configuración personalizada** y, después, elija **Crear directiva**.
3. Proporcione un nombre y una descripción opcional a la directiva y, después, en la sección **Configuración OMA-URI** elija **Agregar**.
4. En el cuadro de diálogo **Agregar o editar configuración OMA-URI**, especifique lo siguiente para obtener una lista de las aplicaciones bloqueadas que no se pueden ejecutar en el dispositivo:
    
    - **Nombre de la configuración.** Escriba **PreventStartPackages**.
    - **Descripción de la configuración.** Escriba una descripción opcional como "Lista de aplicaciones bloqueadas que no se pueden ejecutar".
    -   **Tipo de datos.** En la lista desplegable, elija **Cadena**.
    -   **OMA-URI.** Escriba **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages**
    -   **Valor.** Escriba una lista de los nombres del paquete de aplicaciones que quiere permitir. Puede usar **; : ,** o **|** como delimitador. (Ejemplo: paquete1;paquete2;)

    Para obtener una lista de las aplicaciones que los usuarios pueden instalar de Google Play Store al excluir todas las demás aplicaciones:

    - **Nombre de la configuración.** Escriba **AllowInstallPackages**.
    - **Descripción de la configuración.** Escriba una descripción opcional como "Lista de aplicaciones que los usuarios pueden instalar de Google Play".
    - **Tipo de datos.** En la lista desplegable, elija **Cadena**.
    - **OMA-URI.** Escriba **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages**
    - **Valor.** Escriba una lista de los nombres del paquete de aplicaciones que quiere permitir. Puede usar **; : ,** o **|** como delimitador. (Ejemplo: paquete1;paquete2;)

4. Haga clic en **Aceptar** y, después, en **Guardar directiva**. 

>[SUGERENCIA] Puede encontrar el identificador del paquete de una aplicación dirigiéndose a la aplicación en Google Play Store. El identificador del paquete se incluye en la dirección URL de la página de la aplicación. Por ejemplo, el identificador del paquete de la aplicación Microsoft Word es **com.microsoft.office.word**.

La próxima vez que se registre cada dispositivo de destino, se aplicará la configuración de la aplicación.


## Implementar la directiva

1.  En el área de trabajo **Directiva** , seleccione la directiva que quiera implementar y, a continuación, haga clic en **Administrar implementación**.

2.  En el cuadro de diálogo **Administrar implementación**, seleccione uno o varios grupos en los que quiera implementar la directiva y, después, haga clic en **Agregar** &gt; **Aceptar**.

 
Cuando se selecciona una directiva implementada, puede ver más información acerca de la implementación en la parte inferior de la lista de directivas.

### Consulte también
[Configuración de directivas de Android y Samsung KNOX en Microsoft Intune](android-policy-settings-in-microsoft-intune.md)



<!--HONumber=Aug16_HO3-->


