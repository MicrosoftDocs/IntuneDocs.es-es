---
title: Supervisión de las directivas de MAM con Microsoft Intune
description: Vea cuántos usuarios tienen la directiva y profundice para descubrir más detalles.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: de26b7614578b275802ca048ed17bfa5969f0387
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31021531"
---
# <a name="monitor-app-protection-policies-with-microsoft-intune"></a>Supervisión de directivas de protección de aplicaciones con Microsoft Intune
Puede supervisar el estado de cumplimiento de las directivas de protección de aplicaciones que haya aplicado a los usuarios. Podrá encontrar información sobre los usuarios afectados por las directivas de protección de aplicaciones, el estado de cumplimiento y cualquier problema que puedan estar experimentando sus usuarios.

Hay tres lugares diferentes para supervisar el estado de cumplimiento:

-   Vista Resumen

-   Vista detallada

-   Generación de informes

## <a name="summary-view"></a>Vista Resumen

Siga estos tres pasos para abrir la vista de resumen:

1. Vaya a [Azure Portal](https://portal.azure.com) y especifique sus credenciales.
2. Elija **More Services** (Más servicios) y escriba **Intune** en el cuadro de texto de filtro.
3. Elija **Protección de aplicaciones de Intune**.

En la hoja **Administración de aplicaciones móviles de Intune**, puede ver un resumen del estado de cumplimiento:

![Ventana de resumen en la hoja Administración de aplicaciones móviles de Intune](../media/mam-azure-portal-user-status-summary.png)

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

- Aplicaciones con una directiva de protección de aplicaciones en el dispositivo

- Estado:

  - **Protegido:** significa que la directiva se implementó para el usuario y que la aplicación se usó al menos una vez en el contexto de trabajo.

  - **No protegido:** significa que la directiva se implementó para el usuario, pero la aplicación no se ha usado desde entonces en el contexto de trabajo.

>[!NOTE]
> Si los usuarios que ha buscado no tienen la directiva de protección de aplicaciones implementada, verá un mensaje indicándole que el usuario no es objeto de ninguna directiva de protección de aplicaciones.

Para ver los informes sobre un usuario, siga estos pasos:

1.  Para seleccionar un usuario, elija el icono **Resumen**.

    ![Captura de pantalla 3](../media/MAM-reporting-6.png)

2. En la hoja **Informes de aplicaciones** que se abre, elija **Seleccionar usuario** para buscar un usuario de Azure Active Directory.

    ![Opción Seleccionar usuario de la hoja Informes de aplicaciones](../media/MAM-reporting-2.png)

3. Seleccione el usuario de la lista. Verá los detalles del estado de cumplimiento de ese usuario.

### <a name="flagged-users"></a>Usuarios marcados
La vista detallada muestra el mensaje de error, la aplicación a la que se obtuvo acceso cuando se produjo el error, la plataforma del sistema operativo del dispositivo afectada y una marca de hora.

## <a name="reporting-view"></a>Generación de informes

Puede encontrar los mismos informes en la vista detallada e informes adicionales que le ayudarán en el estado de cumplimiento de la directiva de protección de aplicaciones:

![Captura de pantalla 4](../media/MAM-reporting-7.png)

-   **Informe de usuario de protección de aplicaciones:** describe la misma información que puede encontrar en el informe **Estado usuario** en la sección de vista detallada anterior.

-   **Informe de aplicación de protección de aplicaciones:** ofrece dos estados de protección de aplicaciones diferentes que los administradores pueden seleccionar antes de generar el informe. Los estados pueden estar protegidos o desprotegidos.

    -   Estado de usuario para la actividad de MAM administrada (protegido): este informe resume la actividad de cada aplicación MAM administrada por el usuario.

        -   Muestra todas las aplicaciones de destino de las directivas de protección de aplicaciones para cada usuario y desglosa el estado de cada aplicación como registrado con directivas de protección de aplicaciones, o destinadas a una directiva de protección de aplicaciones, pero la aplicación nunca se ha registrado.
<br></br>
    -   Estado de usuario para la actividad de MAM sin administrar (sin proteger): este informe resume la actividad de las aplicaciones habilitadas por MAM que están sin administrar actualmente por el usuario. Esto puede ocurrir por los siguientes motivos:

        -   Estas aplicaciones están siendo usadas por un usuario o una aplicación que no está destinada actualmente mediante una directiva de protección de aplicaciones.

        -   Todas las aplicaciones están registradas, pero no reciben ninguna directiva de protección de aplicaciones.

![Captura de pantalla 2](../media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Agrupación de tablas

Cuando se muestren los datos del **informe de usuario de protección de aplicaciones**, puede agregar datos de las siguientes maneras:

- **Resultado de la validación:** los datos aparecen agrupados por estado de protección de la aplicación, que puede ser error, advertencia o correcto.
- **Nombre de la aplicación:** los datos aparecen agrupados por aplicaciones (el nombre de aplicación real) con error, advertencia o correcto.

## <a name="export-app-protection-activities-to-csv"></a>Exportación de actividades de protección de aplicaciones a CSV

Puede exportar todas las actividades de directiva de protección de aplicaciones a un archivo .csv único. Esto puede resultar útil para analizar todos los estados de protección de aplicaciones notificados por los usuarios.

Siga estos pasos para generar el informe de protección de aplicaciones:

1. En la hoja de administración de aplicaciones móviles de Intune, elija el informe de protección de aplicaciones.

    ![Captura de pantalla 6](../media/app-protection-report-csv-2.png)

2. Elija Sí para guardar el informe, elija Guardar como y seleccione la carpeta en la que quiere guardar el informe.

    ![Captura de pantalla 7](../media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Vea también
[Administrar la transferencia de datos entre aplicaciones iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [What to expect when your Android app is managed by app protection policies](/intune/end-user-mam-apps-android) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
* [What to expect when your iOS app is managed by app protection policies](/intune/end-user-mam-apps-ios) (Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones)
