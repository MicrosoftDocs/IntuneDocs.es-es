---
title: Supervisión de las directivas de protección de aplicaciones
titleSuffix: Microsoft Intune
description: En este tema se describe cómo configurar las directivas de protección de aplicaciones en Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b4ab3369f241c9f33d4e0bddfd0dcf98c8ab915
ms.sourcegitcommit: fc356fd69beaeb3d69982b47e2bdffb6f7127f8c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2019
ms.locfileid: "71830593"
---
# <a name="how-to-monitor-app-protection-policies"></a>Supervisión de las directivas de protección de aplicaciones
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Puede supervisar el estado de cumplimiento de las directivas de administración de aplicaciones móviles (MAM) que haya aplicado a los usuarios en el panel de protección de aplicaciones de Intune [Azure Portal](https://portal.azure.com). Además, podrá encontrar información sobre los usuarios afectados por las directivas MAM, el estado de cumplimiento de las directivas MAM y cualquier problema que puedan estar experimentando los usuarios finales.

Hay tres lugares diferentes desde donde se pueden supervisar las directivas de protección de aplicaciones:
- Vista Resumen
- Vista detallada
- Generación de informes

> [!NOTE]
> Para obtener información sobre cómo crear directivas de protección de aplicaciones, vea [Creación y asignación de directivas de protección de aplicaciones](app-protection-policies.md).

El período de retención de los datos de protección de la aplicación es de 90 días. Las instancias de aplicación que se han protegido en el servicio MAM en los últimos 90 días se incluirán en el informe de estado de protección de la aplicación. Una instancia de aplicación es un usuario único + aplicación + dispositivo. 

## <a name="summary-view"></a>Vista Resumen

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. En la carga de trabajo **Aplicaciones cliente**, elija **Estado de protección de la aplicación** en la sección **Supervisar** para ver la vista de resumen:

![Mosaico de resumen en el panel de administración de aplicaciones móviles de Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Usuarios asignados**: número total de usuarios asignados en la empresa que usan una aplicación que está asociada a una directiva en un contexto profesional, que está protegida y que tiene una licencia, así como los usuarios asignados que están desprotegidos y que non tienen ninguna licencia.
- **Usuarios marcados**: número de usuarios que experimentan problemas. Los dispositivos liberados (iOS y Android) se notifican en **Usuarios marcados**. Aquí se notifican los usuarios con dispositivos marcados por la comprobación de atestación de dispositivo Google SafetyNet (si el administrador de TI la activó). 
- **Usuarios con aplicaciones potencialmente perjudiciales**: el número de usuarios que pueden tener una aplicación perjudicial en su dispositivo Android detectado por Google Play Protect. 
- **Estado de usuario para iOS** y **Estado del usuario para Android**: número de usuarios que han usado una aplicación que tiene una directiva asignada a ellos en un contexto profesional en la plataforma relacionada. Esta información muestra el número de usuarios que administra la directiva, así como el número de usuarios que usan una aplicación que no es el destino de ninguna directiva en un contexto profesional. Considere la posibilidad de agregar estos usuarios a la directiva.
- **Principales aplicaciones iOS protegidas**: según las aplicaciones iOS más usadas, esta información muestra la cantidad de aplicaciones iOS protegidas y no protegidas.
- **Principales aplicaciones Android protegidas**: según las aplicaciones Android más usadas, esta información muestra la cantidad de aplicaciones Android protegidas y no protegidas.
- **Principales aplicaciones iOS configuradas sin inscripción**: según las aplicaciones iOS más usadas para dispositivos no inscritos, esta información muestra la cantidad de aplicaciones iOS configuradas.
- **Principales aplicaciones Android configuradas sin inscripción**: según las aplicaciones Android más usadas para dispositivos no inscritos, esta información muestra la cantidad de aplicaciones Android configuradas.

    > [!NOTE]
    > Si tiene varias directivas por plataforma, se considerará que un usuario está administrado por una directiva cuando tenga al menos una directiva asignada.

## <a name="detailed-view"></a>Vista detallada
Puede obtener la vista detallada del resumen si selecciona los iconos de **Estado del usuario** (según la plataforma del sistema operativo del dispositivo), de **Usuarios con aplicaciones potencialmente perjudiciales** y de **Usuarios marcados**.

### <a name="user-status"></a>Estado del usuario
Puede buscar un solo usuario y examinar su estado de cumplimiento. En el panel **Informes de aplicaciones** se muestra la siguiente información sobre el usuario seleccionado:
- **Icono**: muestra si el estado de la aplicación está actualizado.
- **Nombre de la aplicación**: nombre de la aplicación.
- **Nombre del dispositivo**: dispositivos asociados con la cuenta del usuario.
- **Tipo del dispositivo**: tipo de dispositivo o sistema operativo que el dispositivo ejecuta.
- **Directivas**: directivas asociadas con la aplicación.
- **Estado**:
  - **Protegido**: significa que la directiva se implementó para el usuario y que la aplicación se usó al menos una vez en el contexto de trabajo.
  - **No protegido**: significa que la directiva se implementó para el usuario, pero la aplicación no se ha usado desde entonces en el contexto de trabajo.
- **Última sincronización**: hora de la última sincronización de la aplicación con Intune. 

>[!NOTE]
> La columna "Última sincronización" representa el mismo valor tanto en el informe de estado de usuario de la consola como en el [informe .csv exportable](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities-to-csv) de la Directiva de protección de aplicaciones. La diferencia es un pequeño retraso en la sincronización entre el valor de los dos informes. 
>
> La hora de "Última sincronización" hace referencia a la última vez que Intune vio la "instancia de la aplicación". Una instancia de aplicación es una combinación única de aplicación + usuario + dispositivo. Cuando un usuario final inicia una aplicación, esta puede o no comunicarse con el servicio de Intune App Protection en el momento del inicio, en función de cuándo se insertó en el repositorio por última vez. Esta documentación ayuda a clarificar [las horas del intervalo de reintentos para la inserción en el repositorio de la Directiva de protección de aplicaciones](https://docs.microsoft.com/en-us/intune/app-protection-policy-delivery). Por lo tanto, si un usuario final no ha usado esa aplicación concreta en el último intervalo de inserción en el repositorio (que suele ser de 30 minutos para el uso activo) e inicia la aplicación, entonces:
>
> - El informe .csv exportable de la Directiva de protección de aplicaciones tendrá el tiempo más reciente entre un minuto (valor normal y mínimo) y 30 minutos (el SLA máximo que proporciona realmente la agregación de SQL que se usa en los informes de Intune).
> - El informe de estado de usuario tendrá la hora más reciente al instante.
>
> Por ejemplo, imagine un usuario final con licencia y dirigido que inicia una aplicación protegida a las 12:00:
> - Si se trata de un primer inicio de sesión, eso significa que el usuario final ha cerrado la sesión antes (sin uso activo), lo que evidencia que no se había registrado la instancia de la aplicación con Intune. Una vez que el usuario inicia sesión, recibirá un nuevo registro de la instancia de la aplicación y se insertará en el repositorio de inmediato si no hay problemas de conectividad, con los mismos retrasos de tiempo indicados anteriormente para las inserciones en el repositorio futuras. Por lo tanto, la hora de la última sincronización sería 12:00 en el informe de estado de usuario, y 12:01 (o 12:30 en el peor de los casos) en el informe de la Directiva de protección de aplicaciones. 
> - Si acaba de iniciar la aplicación, el tiempo de la última sincronización registrado dependerá de cuándo se insertó en el repositorio por última vez.


Para ver los informes sobre un usuario, siga estos pasos:

1. Para seleccionar un usuario, elija el icono de resumen **Estado del usuario**.

    ![Captura de pantalla del mosaico Resumen en la Administración de aplicaciones móviles de Intune](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. En el panel **Informes de aplicaciones** que se abre, elija **Seleccionar usuario** para buscar un usuario de Azure Active Directory.

    ![Captura de pantalla de la opción Seleccionar usuario en el panel Informes de aplicaciones](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Seleccione el usuario de la lista. Podrá ver los detalles del estado de cumplimiento de ese usuario.

>[!NOTE]
> Si el usuario que ha buscado no tiene la directiva de MAM implementada, aparecerá un mensaje informándole de que el usuario no es objeto de ninguna directiva de MAM.

### <a name="flagged-users"></a>Usuarios marcados
La vista detallada muestra el mensaje de error, la aplicación a la que se obtuvo acceso cuando se produjo el error, la plataforma del sistema operativo del dispositivo afectada y una marca de hora. Aquí se notifican los usuarios con dispositivos marcados por la comprobación de inicio condicional "atestación de dispositivo SafetyNet" con el motivo indicado por Google.

### <a name="users-with-potentially-harmful-apps"></a>Usuarios con aplicaciones potencialmente perjudiciales
La vista detallada muestra el usuario, el identificador del paquete de la aplicación, si la aplicación está habilitada para MAM, la categoría de amenaza, el correo electrónico, el nombre del dispositivo y una marca de tiempo. Aquí se notifican los usuarios con dispositivos marcados por la comprobación de inicio condicional "Requerir examen de amenazas en las aplicaciones" con la categoría de amenaza indicada por Google. Si hay aplicaciones enumeradas en este informe que se implementan a través de Intune, póngase en contacto con el desarrollador de la aplicación pertinente o quite la aplicación de la asignación a los usuarios finales. 

## <a name="reporting-view"></a>Generación de informes

Puede encontrar los mismos informes en la parte superior de la hoja **Estado de protección de la aplicación**.

> [!NOTE]
> Intune proporcionará campos adicionales con información sobre el dispositivo, como el identificador de registro de aplicación, el fabricante de Android, el modelo, la versión de la revisión de seguridad y el modelo de iOS. En Intune, estos campos estarán disponibles en **Aplicaciones cliente** > **Estado de protección de aplicaciones** y **Informe de protección de aplicaciones: iOS, Android**. Además, estos parámetros lo ayudarán a configurar la lista de **admitidos** correspondiente al fabricante de dispositivo (Android), la lista de **admitidos** del modelo de dispositivo (iOS y Android) y la configuración de versión de la revisión de seguridad mínima de Android. 

Hay informes adicionales disponibles que le ayudarán con el estado de cumplimiento de directivas MAM. Para ver estos informes, seleccione **Aplicaciones cliente** > **Estado protección de la aplicación** > **Informes**. 

En la hoja **Informes** se proporcionan varios informes basados en el usuario y la aplicación, incluidos los siguientes:


- **Informe de usuario**: en este informe, se describe la misma información que puede encontrar en el informe **Estado del usuario** de la sección [Vista detallada](app-protection-policies-monitor.md#detailed-view) anterior.

- **Informe de aplicación**: además de seleccionar la plataforma y la aplicación, en este informe se proporcionan dos estados de protección de aplicación distintos que puede seleccionar antes de generar el informe. Los estados pueden ser **Protegido** o **Desprotegido**.

  - Estado de usuario para la actividad de MAM administrada (**protegido**): este informe resume la actividad de cada aplicación MAM administrada por el usuario. Muestra todas las aplicaciones de destino de las directivas MAM para cada usuario y desglosa el estado de cada aplicación como registrado con directivas MAM, o destinadas a una directiva MAM, pero que la aplicación nunca se registró.
  - Estado de usuario para la actividad de MAM sin administrar (**desprotegido**): este informe resume la actividad de las aplicaciones habilitadas por MAM que están sin administrar actualmente por el usuario. Esto puede ocurrir por los siguientes motivos:
    - Estas aplicaciones están siendo utilizadas por un usuario o una aplicación que no está destinada actualmente mediante una directiva MAM.
    - Todas las aplicaciones están registradas, pero no reciben ninguna directiva MAM.

    ![Captura de pantalla de la hoja Informes de aplicaciones de un usuario con detalles de 3 aplicaciones](./media/app-protection-policies-monitor/MAM-reporting-4.png)

- **Informe de configuración del usuario**: según un usuario seleccionado, en este informe se proporcionan detalles sobre cualquier configuración de aplicación que haya recibido el usuario.
- **Informe de configuración de la aplicación**: según una aplicación y plataforma seleccionada, en este informe se proporcionan detalles sobre qué usuarios han recibido configuraciones para la aplicación seleccionada.
- **Informe de aprendizaje de aplicación para Windows Information Protection**: en este informe se muestran las aplicaciones que intentan cruzar los límites de las directivas.
- **Aprendizaje de sitio web para Windows Information Protection**: en este informe se muestran los sitios web que intentan cruzar los límites de las directivas.

## <a name="table-grouping"></a>Agrupación de tablas

Cuando se muestren los datos del **informe de usuario de protección de aplicaciones**, puede agregar datos de las siguientes maneras:

- **Resultado de la validación:** los datos aparecen agrupados por estado de protección de la aplicación, que puede ser error, advertencia o correcto.
- **Nombre de la aplicación:** los datos aparecen agrupados por aplicaciones (el nombre de aplicación real) con error, advertencia o correcto.

## <a name="export-app-protection-activities-to-csv"></a>Exportación de actividades de protección de aplicaciones a CSV

Puede exportar todas las actividades de directiva de protección de aplicaciones a un archivo *.csv* único. Esto puede resultar útil para analizar todos los estados de protección de aplicaciones notificados por los usuarios.

Siga estos pasos para generar el informe de protección de aplicaciones:

1. En el panel Administración de aplicaciones móviles de Intune, elija **Informe de protección de la aplicación**.

    ![Captura de pantalla del vínculo de descarga de Protección de aplicaciones](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Elija **Sí** para guardar el informe, luego elija **Guardar como** y seleccione la carpeta en la que quiere guardar el informe.

    ![Captura de pantalla del cuadro de diálogo de confirmación de Guardar informe](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)

## <a name="see-also"></a>Consulte también
- [Administrar la transferencia de datos entre aplicaciones iOS](data-transfer-between-apps-manage-ios.md)
- [What to expect when your Android app is managed by app protection policies](../fundamentals/end-user-mam-apps-android.md) (Qué esperar cuando la aplicación Android se administra con directivas de protección de aplicaciones)
- [What to expect when your iOS app is managed by app protection policies](../fundamentals/end-user-mam-apps-ios.md) (Qué esperar cuando la aplicación iOS se administra con directivas de protección de aplicaciones)
