---
title: Agregar directivas de configuración de aplicaciones para dispositivos Android administrados
titlesuffix: Microsoft Intune
description: Use directivas de configuración de aplicaciones de Microsoft Intune para facilitar los valores de configuración cuando los usuarios ejecutan una aplicación de perfil de trabajo Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdf927eff77b6a97e4c763ec0d75c7e44e4c6840
ms.sourcegitcommit: 28262384ec94e43970cc7a33e5d9063972bdf468
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48799591"
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>Agregar directivas de configuración de aplicaciones para dispositivos Android administrados

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Use directivas de configuración de aplicaciones de Microsoft Intune para facilitar los valores de configuración de las aplicaciones de perfil de trabajo Android. El desarrollador de aplicaciones debe exponer las opciones de configuración de las aplicaciones administradas de Android para poder especificar valores de configuración para la aplicación. Asigne la directiva de configuración de aplicaciones al grupo de usuarios al que quiere que se aplique la configuración.  La configuración de directivas se usa cada vez que la aplicación la comprueba, que suele ser la primera vez que se ejecuta.

> [!Note]  
> No todas las aplicaciones admiten la configuración de aplicaciones. Póngase en contacto con el desarrollador de la aplicación para comprobar si la aplicación admite directivas de configuración de aplicaciones.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Elija la carga de trabajo **Aplicaciones cliente**.
4. En el grupo **Administrar**, elija **Directivas de configuración de aplicaciones** y **Agregar**.
5. Especifique los siguientes detalles:
    - **Nombre**: nombre del perfil que aparecerá en Azure Portal.
    - **Descripción**: descripción del perfil que aparecerá en Azure Portal.
    - **Tipo de inscripción del dispositivo**: elija **Dispositivos administrados**.
6. En **Plataforma**, seleccione **Android**.
7. Seleccione **Aplicación asociada** para elegir la aplicación para la que quiera definir una directiva de configuración. Seleccione una de la lista de aplicaciones de perfil de trabajo Android que ha aprobado y sincronizado con Intune.
8. Seleccione **Permisos**. Las configuraciones se pueden establecer con lo siguiente:
    - [Diseñador de configuraciones](#Use-the-configuration-designer)
    - [Editor JSON](#Enter-the-JSON-editor)
9. Elija **Aceptar** y, luego, **Agregar**.

## <a name="use-the-configuration-designer"></a>Uso del diseñador de configuración

Puede usar el diseñador de configuración para las aplicaciones de Android que admitan la configuración. La configuración se aplicará a los dispositivos que estén inscritos en Intune. El diseñador le permite configurar opciones específicas de la configuración que expone una aplicación.

Seleccione **Agregar** para seleccionar la lista de valores de configuración que quiere especificar para la aplicación.  
Para cada clave y valor de la configuración, establezca lo siguiente:

  - **Tipo de valor**  
    Tipo de datos del valor de configuración. Para los tipos de valor de cadena, si quiere puede elegir un perfil de certificado o una variable como tipo de valor.
  - **Valor de configuración**  
    Se trata del valor de la configuración. Si selecciona una variable o un certificado como tipo de valor, puede elegir una opción de una lista de variables o de perfiles de certificado en la lista desplegable de valores de configuración.  Si elige un certificado, el alias del certificado implementado en el dispositivo se rellenará en tiempo de ejecución.
    
### <a name="supported-variables-for-configuration-values"></a>Variables admitidas para los valores de configuración

Puede elegir las opciones siguientes si elige una variable como tipo de valor:
- Nombre principal de usuario (por ejemplo, **John@contoso.com**)
- Correo (por ejemplo, **John@contoso.com**)
- UPN parcial: por ejemplo, **John**.
- Identificador de cuenta (por ejemplo, **fc0dc142-71d8-4b12-bbea-bae2a8514c81**)
- Identificador de dispositivo (por ejemplo, **b9841cd9-9843-405f-be28-b2265c59ef97**)
- Identificador de usuario (por ejemplo, **3ec2c00f-b125-4519-acf0-302ac3761822**)
- Nombre de usuario (por ejemplo, **John Doe**)


## <a name="enter-the-json-editor"></a>Editor de JSON

Algunos valores de configuración de las aplicaciones (como los que tienen tipos de agrupaciones) no se pueden configurar con el Diseñador de configuración. Para esos valores, se deberá usar el editor JSON. La configuración se proporciona a las aplicaciones de forma automática cuando se instalan.

1. En **Formato de opciones de configuración**, seleccione **Enter JSON editor** (Especificar editor JSON).
2. En el editor puede definir los valores JSON para las opciones de configuración. Puede elegir **Download JSON template** (Descargar plantilla JSON) para descargar un archivo de ejemplo que después puede configurar.
3. Elija **Aceptar** y, luego, **Agregar**.

La directiva se crea y aparece en la hoja de lista de directivas.

Cuando se ejecuta la aplicación asignada en un dispositivo, lo hará con las opciones configuradas en la directiva de configuración de aplicaciones.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Preconfiguración del estado de concesión de permisos para las aplicaciones

También puede preconfigurar permisos para que las aplicaciones accedan a las características de dispositivos Android. Las aplicaciones de Android que requieren permisos de dispositivo (como el acceso a la ubicación o la cámara del dispositivo) solicitan a los usuarios de forma predeterminada que acepten o denieguen permisos. Por ejemplo, si una aplicación usa el micrófono del dispositivo, se solicita al usuario que conceda a la aplicación el permiso para usar el micrófono.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Elija **Aplicaciones cliente**.
3. En **Administrar**, elija **Directivas de configuración de aplicaciones** y, después, **Agregar**.
4. Especifique los siguientes detalles:
    - **Nombre**. Nombre del perfil que aparecerá en Azure Portal.
    - **Descripción**. Descripción del perfil que aparecerá en Azure Portal.
    - **Tipo de inscripción del dispositivo**. Seleccione **Dispositivos administrados**.
    - **Plataforma**. Seleccione **Android**.
5. Seleccione **Aplicación asociada** para elegir la aplicación para la que desea definir una directiva de configuración. Seleccione una de la lista de aplicaciones de perfil de trabajo Android que ha aprobado y sincronizado con Intune.
6. Seleccione **Permisos** y después elija **Agregar**.
7. Seleccione en la lista de permisos de aplicación disponibles y después elija **Aceptar**.
8. Seleccione una opción para cada permiso que se concede con esta directiva:
    - **Pedir confirmación**. Pedir al usuario que acepte o deniegue
    - **Concesión automática**. Aprobar automáticamente sin notificar al usuario.
    - **Denegación automática**. Denegar automáticamente sin notificar al usuario.
9. Para asignar la directiva de configuración de aplicación, seleccione la directiva de configuración de aplicación, seleccione **Asignación** y después seleccione **Seleccionar grupos**.
10. Seleccione los grupos de usuarios para asignar y, a continuación, elija **Seleccionar**.
11. Elija **Guardar** para asignar la directiva.

## <a name="next-steps"></a>Pasos siguientes

Siga [asignando](apps-deploy.md) y [supervisando](apps-monitor.md) la aplicación.

