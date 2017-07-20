---
title: "Uso de directivas de configuración de aplicaciones de Intune para Android for Work"
titleSuffix: Intune on Azure
description: "Obtenga información sobre cómo usar directivas de configuración de aplicaciones para proporcionar datos de configuración a una aplicación de Android for Work cuando se ejecuta."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b86d2d7f4d295ed41168c9dfdbaf8d4c253a0f75
ms.sourcegitcommit: 388c5f59bc992375ac63968fd7330af5d84a1348
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-android-for-work"></a>Uso de directivas de configuración de aplicaciones de Microsoft Intune para Android for Work

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Use las directivas de configuración de aplicaciones de Microsoft Intune para proporcionar los valores de configuración que pueden estar disponibles cuando los usuarios ejecutan una aplicación Android for Work. No todas las aplicaciones admiten la configuración de aplicaciones. Póngase en contacto con el desarrollador de la aplicación para comprobar si la ha creado o no para admitir directivas de configuración de aplicaciones.

Las directivas de configuración de aplicaciones pueden ayudarle a configurar previamente la configuración de la aplicación disponible para los usuarios antes de ejecutar la aplicación. Algunas aplicaciones Android admiten las opciones de configuración administrada que puede configurar en la consola de Intune con el [Diseñador de configuración](#use-configuration-designer). Algunos valores de configuración de las aplicaciones (como los que tienen tipos de agrupaciones) no se pueden configurar con el Diseñador de configuración.  Debe utilizar el [editor JSON](#use-json-editor) para esos valores.   La configuración se proporciona a las aplicaciones de forma automática cuando se instalan.

No asigne estas directivas directamente a usuarios y dispositivos. Asocie la directiva con una aplicación y, a continuación, asigne la aplicación. La configuración de directiva se usa cada vez que la aplicación la comprueba, que suele ser la primera vez que se ejecuta.

## <a name="use-configuration-designer"></a>Uso del Diseñador de configuración

1. En el portal de Intune, elija **Mobile Apps**. En **Administrar**, elija **Directivas de configuración de aplicaciones** y después haga clic en **Agregar**.
2. Especifique los siguientes detalles:
    - **Nombre**: el nombre del perfil que aparecerá en la consola de Intune.
    - **Descripción**: la descripción del perfil que aparecerá en la consola de Intune.
    - **Plataforma**: seleccione **Android**.
    - **Tipo de inscripción del dispositivo** - **Inscrito en Intune** es la opción preseleccionada.
3. Seleccione **Aplicación asociada** para elegir la aplicación para la que desea definir una directiva de configuración.  Seleccione en la lista de Android for Work las aplicaciones que ha aprobado y sincronizado con Intune.
4. Seleccione **Opciones de configuración**.
5. En **Formato de opciones de configuración**, seleccione **Usar diseñador de configuraciones**.
6. Seleccione **Agregar**. Se muestra una lista de las opciones de configuración disponibles. La lista incluye lo siguiente:
    - **Claves de configuración**: nombre de la configuración.
    - **Tipo de valor**: la opción que se puede configurar como, por ejemplo, **booleano** o **cadena**.
    - **Descripción**: una descripción de la opción de configuración.
7. Seleccione las casillas de configuración que desea configurar con este perfil y luego haga clic en **Aceptar**.
8. Se muestra una lista de la configuración seleccionada con el **Valor de configuración** disponible. Especifique un valor para cada configuración y después haga clic en **Aceptar**.

## <a name="use-json-editor"></a>Uso del editor JSON

1. En el portal de Intune, elija **Mobile Apps**. En **Administrar**, elija **Directivas de configuración de aplicaciones** y después haga clic en **Agregar**.
2. Especifique los siguientes detalles:
    - **Nombre**: el nombre del perfil que aparecerá en la consola de Intune.
    - **Descripción**: la descripción del perfil que aparecerá en la consola de Intune.
    - **Plataforma**: seleccione **Android**.
    - **Tipo de inscripción del dispositivo** - **Inscrito en Intune** es la opción preseleccionada.
3. Seleccione **Aplicación asociada** para elegir la aplicación para la que desea definir una directiva de configuración.  Seleccione en la lista de Android for Work las aplicaciones que ha aprobado y sincronizado con Intune.
5. Seleccione **Opciones de configuración**.
6. En **Formato de opciones de configuración**, seleccione **Enter JSON editor** (Especificar editor JSON).
7. En el editor puede definir valores JSON para opciones de configuración. Puede elegir **Download JSON template** (Descargar plantilla JSON) para descargar un archivo de ejemplo que después puede configurar.
8. Cuando haya terminado, elija **Aceptar** y después haga clic en **Agregar**.

La directiva se crea y aparece en la hoja de lista de directivas.



Cuando se ejecuta la aplicación asignada en un dispositivo, se ejecutará con las opciones configuradas en la directiva de configuración de aplicaciones.

## <a name="preconfigure-permissions-grant-state-for-apps"></a>Preconfiguración del estado de concesión de permisos para las aplicaciones

También puede preconfigurar permisos para que las aplicaciones accedan a las características de dispositivos Android. De forma predeterminada, las aplicaciones de Android que requieren permisos de dispositivo como el acceso a la ubicación o la cámara del dispositivo solicitan a los usuarios que acepten o denieguen permisos. Por ejemplo, si una aplicación usa el micrófono del dispositivo, se solicita al usuario final que conceda a la aplicación el permiso para usar el micrófono.

1. En el portal de Intune, elija **Mobile Apps**. En **Administrar**, elija **Directivas de configuración de aplicaciones** y después haga clic en **Agregar**.
2. Especifique los siguientes detalles:
    - **Nombre**: el nombre del perfil que aparecerá en la consola de Intune.
    - **Descripción**: la descripción del perfil que aparecerá en la consola de Intune.
    - **Plataforma**: seleccione **Android**.
    - **Tipo de inscripción del dispositivo** - **Inscrito en Intune** es la opción preseleccionada.
3. Seleccione **Aplicación asociada** para elegir la aplicación para la que desea definir una directiva de configuración.  Seleccione en la lista de Android for Work las aplicaciones que ha aprobado y sincronizado con Intune.
5. Seleccione **Permisos** y después elija **Agregar**.
6. Seleccione en la lista de permisos de aplicación disponibles y después elija **Aceptar**.
7. Seleccione una opción para cada permiso que se concede con esta directiva:
    - **Pedir confirmación**: pedir al usuario que acepte o deniegue.
    - **Concesión automática**: aprobar automáticamente sin notificar al usuario.
    - **Denegación automática**: Denegar automáticamente sin notificar al usuario.
8. Para asignar la directiva de configuración de aplicación, seleccione la directiva de configuración de aplicación, seleccione **Asignación** y después seleccione **Seleccionar grupos**.
9. Seleccione los grupos de usuarios para asignar y, a continuación, elija **Seleccionar**.
10. Elija **Guardar** para asignar la directiva.

## <a name="next-steps"></a>Pasos siguientes

Siga [asignando](apps-deploy.md) y [supervisando](apps-monitor.md) la aplicación como de costumbre.

