---
title: "Supervisión de las directivas de protección de aplicaciones"
titleSuffix: Intune on Azure
description: "Vea cuántos usuarios tienen la directiva y profundice para descubrir más detalles."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 241ae7d2d615cd58babfc2d14b98e2bfb2f63f7d
ms.sourcegitcommit: 2ee1e8248814d74cef80b609a8e43f59fa0b2618
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2017
---
# <a name="how-to-monitor-app-protection-policies"></a>Supervisión de las directivas de protección de aplicaciones
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**Si no tiene acceso a Azure Portal**, en este tema se explica [cómo crear directivas de protección de aplicaciones](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) en la consola de Intune clásica.


Puede supervisar el estado de cumplimiento de las directivas de administración de aplicaciones móviles (MAM) que haya aplicado a los usuarios en la hoja de protección de aplicaciones de Intune en [Azure Portal](https://portal.azure.com). Podrá encontrar información sobre los usuarios afectados por las directivas MAM, el estado de cumplimiento y cualquier problema que puedan estar experimentando los usuarios finales.

Hay tres lugares diferentes para supervisar el estado de cumplimiento:

-   Vista Resumen

-   Vista detallada

-   Generación de informes

## <a name="summary-view"></a>Vista Resumen

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Aplicaciones móviles**.
4. En la carga de trabajo **Mobile apps**, elija **Supervisar** > **Estado de usuario de protección de aplicaciones**, para ver la vista de resumen:

![Ventana de resumen en la hoja Administración de aplicaciones móviles de Intune](./media/app-protection-user-status-summary.png)

-   **Usuarios**: el número total de usuarios en su empresa que está usando una aplicación que está asociada con una directiva en un contexto de trabajo.

-   **ADMINISTRADO POR UNA DIRECTIVA**: el número de usuarios que ha usado una aplicación que tiene una directiva asignada a ellos en un contexto de trabajo.

-   **SIN DIRECTIVA**: el número de usuarios que está usando una aplicación que no tiene como destino ninguna directiva en un contexto de trabajo. Considere la posibilidad de agregar estos usuarios a la directiva.
    > [!NOTE]
    > Si tiene varias directivas por plataforma, se considerará que un usuario está administrado por una directiva cuando tenga al menos una directiva asignada.

- **Usuarios marcados:** número de usuarios que experimentan problemas. Actualmente, solo los usuarios con dispositivos descodificados aparecen como **Usuarios marcados**.


## <a name="detailed-view"></a>Vista detallada
Puede obtener la vista detallada del resumen si selecciona las ventanas **Estado del usuario** (según la plataforma del sistema operativo del dispositivo) y **Usuarios marcados**.

### <a name="user-status"></a>Estado del usuario
Puede buscar un solo usuario y examinar su estado de cumplimiento. La hoja **Informes de aplicaciones** muestra la siguiente información sobre el usuario seleccionado:
- Dispositivos que están asociados a la cuenta de usuario

- Aplicaciones con la directiva MAM en el dispositivo

- Estado:

  - **Protegido:** significa que la directiva se implementó para el usuario y que la aplicación se usó al menos una vez en el contexto de trabajo.

  - **No protegido:** significa que la directiva se implementó para el usuario, pero la aplicación no se ha usado desde entonces en el contexto de trabajo.

>[!NOTE]
> Si el usuario que buscó no tiene la directiva de MAM implementada, aparecerá un mensaje informándole de que el usuario no será objeto de ninguna directiva MAM.

Para ver los informes sobre un usuario, siga estos pasos:

1.  Para seleccionar un usuario, elija el icono **Resumen**.

    ![Captura de pantalla 3](./media/MAM-reporting-6.png)

2. En la hoja **Informes de aplicaciones** que se abre, elija **Seleccionar usuario** para buscar un usuario de Azure Active Directory.

    ![Opción Seleccionar usuario de la hoja Informes de aplicaciones](./media/MAM-reporting-2.png)

3. Seleccione el usuario de la lista. Verá los detalles del estado de cumplimiento de ese usuario.

### <a name="flagged-users"></a>Usuarios marcados
La vista detallada muestra el mensaje de error, la aplicación a la que se obtuvo acceso cuando se produjo el error, la plataforma del sistema operativo del dispositivo afectada y una marca de hora.

## <a name="reporting-view"></a>Generación de informes

Puede encontrar los mismos informes en la vista detallada e informes adicionales que le ayudarán en el estado de cumplimiento de la directiva MAM:

![Captura de pantalla 4](./media/MAM-reporting-7.png)

-   **Informe de usuario de protección de aplicaciones:** describe la misma información que puede encontrar en el informe **Estado usuario** en la sección de vista detallada anterior.

-   **Informe de aplicación de protección de aplicaciones:** ofrece dos estados de protección de aplicaciones diferentes que los administradores pueden seleccionar antes de generar el informe. Los estados pueden estar protegidos o desprotegidos.

    -   Estado de usuario para la actividad de MAM administrada (protegido): este informe resume la actividad de cada aplicación MAM administrada por el usuario.

        -   Muestra todas las aplicaciones de destino de las directivas MAM para cada usuario y desglosa el estado de cada aplicación como registrado con directivas MAM, o destinadas a una directiva MAM, pero que la aplicación nunca se registró.
<br></br>
    -   Estado de usuario para la actividad de MAM sin administrar (sin proteger): este informe resume la actividad de las aplicaciones habilitadas por MAM que están sin administrar actualmente por el usuario. Esto puede ocurrir por los siguientes motivos:

        -   Estas aplicaciones están siendo utilizadas por un usuario o una aplicación que no está destinada actualmente mediante una directiva MAM.

        -   Todas las aplicaciones están registradas, pero no reciben ninguna directiva MAM.

![Captura de pantalla 2](./media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Agrupación de tablas

Cuando se muestren los datos del **informe de usuario de protección de aplicaciones**, puede agregar datos de las siguientes maneras:

- **Resultado de la validación:** los datos aparecen agrupados por estado de protección de la aplicación, que puede ser error, advertencia o correcto.
- **Nombre de la aplicación:** los datos aparecen agrupados por aplicaciones (el nombre de aplicación real) con error, advertencia o correcto.

## <a name="export-app-protection-activities-to-csv"></a>Exportación de actividades de protección de aplicaciones a CSV

Puede exportar todas las actividades de directiva de protección de aplicaciones a un archivo .csv único. Esto puede resultar útil para analizar todos los estados de protección de aplicaciones notificados por los usuarios.

Siga estos pasos para generar el informe de protección de aplicaciones:

1. En la hoja de administración de aplicaciones móviles de Intune, elija el informe de protección de aplicaciones.

    ![Captura de pantalla 6](./media/app-protection-report-csv-2.png)

2. Elija Sí para guardar el informe, elija Guardar como y seleccione la carpeta en la que quiere guardar el informe.

    ![Captura de pantalla 7](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Consulte también
[Administrar la transferencia de datos entre aplicaciones iOS](data-transfer-between-apps-manage-ios.md)

* [What to expect when your Android app is managed by app protection policies](app-protection-enabled-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
* [What to expect when your iOS app is managed by app protection policies](app-protection-enabled-apps-ios.md) (Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones)
