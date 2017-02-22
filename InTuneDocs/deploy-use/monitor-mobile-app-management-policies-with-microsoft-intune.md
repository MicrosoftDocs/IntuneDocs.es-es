---
title: "Supervisión de las directivas de MAM con Microsoft Intune | Microsoft Docs"
description: "Vea cuántos usuarios tienen la directiva y profundice para descubrir más detalles."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 22c30f51bf83219053f97310ed1830ad9e01acd8
ms.openlocfilehash: bd270cd4b04894d4824487d36ea4f0c1929dd568


---

# <a name="monitor-mobile-app-management-policies-with-microsoft-intune"></a>Supervisión de directivas de administración de aplicaciones móviles con Microsoft Intune
Puede supervisar el estado de cumplimiento de las directivas de administración de aplicaciones móviles (MAM) que haya aplicado a los usuarios. Podrá encontrar información sobre los usuarios afectados por las directivas MAM, el estado de cumplimiento y cualquier problema que puedan estar experimentando los usuarios finales.

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

-   **USUARIOS:** número total de usuarios de la empresa que usan las aplicaciones que están asociadas a la directiva.

-   **ADMINISTRADO POR UNA DIRECTIVA:** número de usuarios que han usado al menos una de las aplicaciones en un contexto de trabajo.

-   **NINGUNA DIRECTIVA:** número de usuarios que usan las aplicaciones asociadas a la directiva, pero a los que no se les aplica la directiva. Considere la posibilidad de agregar estos usuarios a la directiva.

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

    ![Captura de pantalla 3](../media/MAM-reporting-6.png)

2. En la hoja **Informes de aplicaciones** que se abre, elija **Seleccionar usuario** para buscar un usuario de Azure Active Directory.

    ![Opción Seleccionar usuario de la hoja Informes de aplicaciones](../media/MAM-reporting-2.png)

3. Seleccione el usuario de la lista. Verá los detalles del estado de cumplimiento de ese usuario.

### <a name="flagged-users"></a>Usuarios marcados
La vista detallada muestra el mensaje de error, la aplicación a la que se obtuvo acceso cuando se produjo el error, la plataforma del sistema operativo del dispositivo afectada y una marca de hora.

## <a name="reporting-view"></a>Generación de informes

Puede encontrar los mismos informes en la vista detallada e informes adicionales que le ayudarán en el estado de cumplimiento de la directiva MAM:

![Captura de pantalla&4;](../media/MAM-reporting-7.png)

-   **Informe de usuario de protección de aplicaciones:** describe la misma información que puede encontrar en el informe **Estado usuario** en la sección de vista detallada anterior.

-   **Informe de aplicación de protección de aplicaciones:** ofrece dos estados de protección de aplicaciones diferentes que los administradores pueden seleccionar antes de generar el informe. Los estados pueden estar protegidos o desprotegidos.

    -   Estado de usuario para la actividad de MAM administrada (protegido): este informe resume la actividad de cada aplicación MAM administrada por el usuario.

        -   Muestra todas las aplicaciones de destino de las directivas MAM para cada usuario y desglosa el estado de cada aplicación como registrado con directivas MAM, o destinadas a una directiva MAM, pero que la aplicación nunca se registró.
<br></br>
    -   Estado de usuario para la actividad de MAM sin administrar (sin proteger): este informe resume la actividad de las aplicaciones habilitadas por MAM que están sin administrar actualmente por el usuario. Esto puede ocurrir por los siguientes motivos:

        -   Estas aplicaciones están siendo utilizadas por un usuario o una aplicación que no está destinada actualmente mediante una directiva MAM.

        -   Todas las aplicaciones están registradas, pero no reciben ninguna directiva MAM.

![Captura de pantalla&2;](../media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Agrupación de tablas

Cuando se muestren los datos del **informe de usuario de protección de aplicaciones**, puede agregar datos de las siguientes maneras:

- **Resultado de la validación:** los datos aparecen agrupados por estado de protección de la aplicación, que puede ser error, advertencia o correcto.
- **Nombre de la aplicación:** los datos aparecen agrupados por aplicaciones (el nombre de aplicación real) con error, advertencia o correcto.

## <a name="export-app-protection-activities-to-csv"></a>Exportación de actividades de protección de aplicaciones a CSV

Puede exportar todas las actividades de directiva de protección de aplicaciones a un archivo .csv único. Esto puede resultar útil para analizar todos los estados de protección de aplicaciones notificados por los usuarios.

Siga estos pasos para generar el informe de protección de aplicaciones:

1. En la hoja de administración de aplicaciones móviles de Intune, elija el informe de protección de aplicaciones.

    ![Captura de pantalla&6;](../media/app-protection-report-csv-2.png)

2. Elija Sí para guardar el informe, elija Guardar como y seleccione la carpeta en la que quiere guardar el informe.

    ![Captura de pantalla&7;](../media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Consulte también
[Administrar la transferencia de datos entre aplicaciones iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [Qué esperar cuando la aplicación Android está administrada por directivas MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [Qué esperar cuando la aplicación iOS está administrada por directivas MAM](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Feb17_HO2-->


