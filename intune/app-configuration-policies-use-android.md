---
title: "Agregar directivas de configuración de aplicaciones para dispositivos Android administrados"
titlesuffix: Microsoft Intune
description: "Use las directivas de configuración de aplicaciones de Microsoft Intune para proporcionar los valores de configuración cuando los usuarios ejecutan una aplicación Android for Work."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 206e229e95633ce553637bcedef708ee5630864c
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2018
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>Agregar directivas de configuración de aplicaciones para dispositivos Android administrados

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use las directivas de configuración de aplicaciones de Microsoft Intune para proporcionar los valores de configuración cuando los usuarios ejecutan una aplicación Android for Work. No asigne estas directivas directamente a usuarios y dispositivos. Asocie la directiva con una aplicación y, a continuación, asigne la aplicación. La configuración de directivas se usa cada vez que la aplicación la comprueba, que suele ser la primera vez que se ejecuta.

> [!Note]  
> No todas las aplicaciones admiten la configuración de aplicaciones. Póngase en contacto con el desarrollador de la aplicación para comprobar si la aplicación admite directivas de configuración de aplicaciones.

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services (Todos los servicios)** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Elija la carga de trabajo **Aplicaciones móviles**.
4. En el grupo **Administrar**, elija **Directivas de configuración de aplicaciones** y **Agregar**.
5. Especifique los siguientes detalles:
    - **Nombre**  
      Nombre del perfil que aparecerá en Azure Portal.
    - **Descripción**  
      Descripción del perfil que aparecerá en Azure Portal.
    - **Tipo de inscripción del dispositivo**  
      Elija **Dispositivos administrados**.
6. Seleccione **Android for Work** para **Plataforma**.
7. Seleccione **Aplicación asociada** para elegir la aplicación para la que quiera definir una directiva de configuración. Seleccione en la lista de Android for Work las aplicaciones que ha aprobado y sincronizado con Intune.
8. Seleccione **Opciones de configuración**. Las configuraciones se pueden establecer con lo siguiente:
    - [Diseñador de configuraciones](#Use-the-configuration-designer)
    - [Editor JSON](#Enter-the-JSON-editor)
9. Elija **Aceptar** y, luego, **Agregar**.

## <a name="use-the-configuration-designer"></a>Uso del diseñador de configuración

El diseñador de configuración se puede usar con las aplicaciones de dispositivos inscritos o no en Intune. El diseñador permite configurar valores y las claves de configuración específicos. También se debe especificar el tipo de datos para cada valor.

Para cada clave y valor de la configuración, establezca lo siguiente:

  - **Clave de configuración**  
     Clave con la que se identifica de manera única la configuración específica.
  - **Tipo de valor**  
    Tipo de datos del valor de configuración. Los tipos pueden ser entero, real, cadena o booleano.
  - **Valor de configuración**  
    Se trata del valor de la configuración. 

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
2. Elija **All services (Todos los servicios)** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. Elija **Aplicaciones móviles**.
3. En **Administrar**, elija **Directivas de configuración de aplicaciones** y, después, **Agregar**.
4. Especifique los siguientes detalles:
    - **Nombre**. Nombre del perfil que aparecerá en Azure Portal.
    - **Descripción**. Descripción del perfil que aparecerá en Azure Portal.
    - **Tipo de inscripción del dispositivo**. Seleccione **Dispositivos administrados**.
    - **Plataforma**. Seleccione **Android for Work**.
5. Seleccione **Aplicación asociada** para elegir la aplicación para la que desea definir una directiva de configuración. Seleccione en la lista de Android for Work las aplicaciones que ha aprobado y sincronizado con Intune.
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

