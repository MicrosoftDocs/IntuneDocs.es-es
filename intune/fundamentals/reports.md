---
title: Microsoft Intune reports
titleSuffix: Microsoft Intune
description: Intune proporciona tipos de informes específicos con vistas concentradas que contienen datos coherentes y oportunos.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05258c5363b43398dee1815bb91c50878803e426
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391947"
---
# <a name="intune-reports"></a>Informes de Intune
Los informes de Microsoft Intune le permiten supervisar de forma más eficaz y proactiva el estado y la actividad de los puntos de conexión de toda la organización, además de proporcionar otros datos de informes en Intune. Por ejemplo, podrá ver informes sobre el cumplimiento, el estado y las tendencias de los dispositivos. Además, puede crear informes personalizados para obtener datos más específicos. 

> [!NOTE]
> Los cambios en los informes de Intune se implementarán gradualmente durante un período de tiempo para ayudarle a preparar la nueva estructura y adaptarse a ella.

Los tipos de informes se organizan en las siguientes áreas de enfoque:
- **Operativo**: proporciona datos dirigidos oportunamente que le ayudan a centrar la atención y tomar medidas. Los administradores, los expertos en la materia y el departamento de soporte técnico encontrarán estos informes particularmente útiles.
- **Organizativo**: proporciona un resumen más amplio de una vista general, como el estado de administración de los dispositivos. Los administradores encontrarán estos informes particularmente útiles.
- **Histórico**: proporciona patrones y tendencias a lo largo de un período de tiempo. Los administradores encontrarán estos informes particularmente útiles.
- **Especialista**: le permite usar datos sin procesar para crear sus propios informes personalizados. Los administradores encontrarán estos informes particularmente útiles.

La plataforma de informes proporciona una experiencia de informes coherente y más completa. Los informes disponibles proporcionan la siguiente funcionalidad:
- **Búsqueda y ordenación**: puede buscar y ordenar por columna, independientemente del tamaño del conjunto de datos.
- **Paginación de datos**: puede examinar los datos en función de la paginación (página a página o saltar a una página específica).
- **Rendimiento**: puede generar y ver rápidamente los informes creados a partir de inquilinos de gran tamaño.
- **Exportación**: puede exportar rápidamente los datos de informes generados a partir de inquilinos de gran tamaño.

### <a name="who-can-access-the-data"></a>¿Quién puede tener acceso a los datos?

Los usuarios con los siguientes permisos pueden revisar los registros:

- Administrador global
- Administrador del servicio de Intune
- Administradores asignados a un rol de Intune con los permisos de **Lectura**

## <a name="non-compliant-devices-report-operational"></a>Informe de dispositivos no conformes (operativo)
El informe de dispositivos no conformes muestra los datos que suelen usar los roles del departamento de soporte técnico o de administrador para identificar problemas y ayudar a resolverlos. Los datos que se encuentran en estos informes son oportunos, anuncian comportamientos inesperados y pretenden ser accionables. El informe está disponible junto con la carga de trabajo, lo que convierte a estos informes en accesibles sin desplazarse lejos de los flujos de trabajo activos. Este informe proporciona funcionalidades de filtrado, búsqueda, paginación y ordenación. También puede explorar en profundizar para solucionar problemas.

Puede ver el informe **Dispositivos no conformes** mediante los pasos siguientes:

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Cumplimiento del dispositivo** > **Dispositivos no conformes**.

    ![Informe de dispositivos no conformes](./media/intune-reports/intune-reports-02.png)

## <a name="device-compliance-report-organizational"></a>Informe de cumplimiento de dispositivos (organizativo)
Los informes de cumplimiento de dispositivos son generales por naturaleza y proporcionan una vista más tradicional de los datos de informes para identificar las métricas agregadas. Este informe está diseñado para trabajar con grandes conjuntos de datos a fin de obtener una imagen completa del cumplimiento de los dispositivos. Por ejemplo, el informe de cumplimiento de dispositivos muestra todos los estados de cumplimiento de los dispositivos, de modo que se proporciona una vista más amplia de los datos, con independencia del tamaño del conjunto de datos. Este informe muestra el desglose completo de los registros, además de una visualización adecuada de las métricas agregadas. Para generarlo, se le pueden aplicar filtros y seleccionar el botón "Generar informe". Los datos se actualizan para mostrar el estado más reciente con la posibilidad de ver los registros individuales que componen los datos agregados. Al igual que la mayoría de los informes de la nueva plataforma, estos registros son susceptibles de ordenación y búsqueda para centrarse en la información que necesita. 

Para ver un informe generado del estado de un dispositivo, puede seguir estos pasos:
1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Informes** para ver el resumen de informes.
3. Seleccione **Cumplimiento del dispositivo**.
4. Seleccione los filtros **Estado de cumplimiento**, **OS** y **Propiedad** para refinar el informe.
5. Haga clic en **Generar informe** (o **Generar de nuevo**) para recuperar los datos actuales.

    ![Informe de cumplimiento de dispositivos](./media/intune-reports/intune-reports-02a.png)

    > [!NOTE]
    > Este informe de **Cumplimiento de dispositivos** proporciona una marca de tiempo de la última vez que se generó el informe. 

Para ver información relacionada, consulte acerca de la [aplicación del cumplimiento de ATP de Microsoft Defender con acceso condicional en Intune](~/protect/advanced-threat-protection.md).

## <a name="reports-summary"></a>Resumen de informes 

El informe de cumplimiento de dispositivos está disponible como informe de resumen en la carga de trabajo **Informes**. Use los pasos siguientes para ver el informe de cumplimiento de dispositivos:

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Informes** para ver el resumen de informes.

    ![Resumen de informes de Intune](./media/intune-reports/intune-reports-01.png)

## <a name="device-compliance-trend-report-historical"></a>Informe de tendencias de cumplimiento de dispositivos (histórico)
Los administradores y los arquitectos usarán probablemente los informes de tendencias de cumplimiento de dispositivos para identificar las tendencias a largo plazo en el cumplimiento de los dispositivos. Los datos agregados se muestran durante un período de tiempo y resultan útiles para tomar decisiones de inversión futuras, impulsar la mejora de los procesos o promover la investigación de posibles anomalías. También se pueden aplicar filtros para ver tendencias específicas. Los datos proporcionados por este informe son una instantánea del estado actual del inquilino (casi en tiempo real). 

Un informe de tendencias de cumplimiento de dispositivos puede mostrar la tendencia de los estados de cumplimiento de los dispositivos durante un período de tiempo. Puede identificar dónde se han producido los picos de cumplimiento y centrar su tiempo y esfuerzo en consecuencia.

Para ver el informe de **Tendencias**, siga estos pasos:

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Informes** > **Tendencias** para ver el cumplimiento de los dispositivos durante una tendencia de 60 días.

    ![Informe de tendencias de Intune](./media/intune-reports/intune-reports-03.png)

## <a name="azure-monitor-integration-reports-specialist"></a>Informes de integración de Azure Monitor (especialista)
Puede personalizar sus propios informes para obtener los datos que desee. Los datos de los informes estarán disponibles opcionalmente a través de [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) mediante [Log Analytics](reports.md#log-analytics) y los [libros de Azure Monitor](reports.md#workbooks). Estas soluciones le permiten crear consultas personalizadas, configurar alertas y hacer que los paneles muestren los datos de cumplimiento de dispositivos de la manera deseada. Además, puede conservar los registros de actividad en su cuenta de almacenamiento de Azure, integrarlos con los informes mediante [herramientas de administración de eventos e información de seguridad (SIEM)](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration) y correlacionar los informes con los registros de actividad de Azure AD. Además de para importar paneles, los libros de Azure Monitor se pueden usar cuando es necesario generar informes personalizados.

> [!NOTE]
> La funcionalidad de informes complejos requiere una suscripción a Azure.

Un informe especialista de ejemplo crearía una correlación entre los datos de propiedad de los dispositivos y los datos de inscripción de la plataforma de un informe personalizado. Luego, este informe personalizado podría mostrarse en un panel existente en el portal de Azure Active Directory.

Para crear y ver informes personalizados, siga estos pasos:

1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Seleccione **Informes** > **Configuración de diagnóstico** y agregue una [configuración de diagnóstico](reports.md#diagnostic-settings).

    ![Resumen de informes de Intune](./media/intune-reports/intune-reports-04.png)

3. Haga clic en **Agregar configuración de diagnóstico** para mostrar el panel **Configuración de diagnóstico**. 
4. Rellene el campo **Nombre** de la configuración de diagnóstico. 
5. Seleccione los valores **Enviar a Log Analytics** y **DeviceComplianceOrg**.

    ![Resumen de informes de Intune](./media/intune-reports/intune-reports-04a.png)

6. Haga clic en **Guardar**.
7. Luego, seleccione **Log Analytics** para crear y ejecutar una nueva consulta mediante [Log Analytics](reports.md#log-analytics).

   ![Log Analytics: consulta de registros](./media/intune-reports/intune-reports-05.png)

8. Seleccione **Libros** para crear o abrir un informe interactivo mediante [libros de Azure Monitor](reports.md#workbooks).

   ![Libros: informes interactivos](./media/intune-reports/intune-reports-07.png)

### <a name="diagnostic-settings"></a>Configuración de diagnóstico
Cada recurso de Azure requiere su propia configuración de diagnóstico. La configuración de diagnóstico define lo siguiente para un recurso:

- Las categorías de registros y los datos de métricas enviados a los destinos definidos en la configuración. Las categorías disponibles variarán para los distintos tipos de recursos.
- Uno o más destinos para enviar los registros. Los destinos actuales incluyen el área de trabajo de Log Analytics, Event Hubs y Azure Storage.
- Directiva de retención de los datos almacenados en Azure Storage.

Una sola configuración de diagnóstico puede definir uno de cada uno de los destinos. Si quiere enviar datos a más de uno de un tipo de destino determinado (por ejemplo, dos áreas de trabajo de Log Analytics diferentes), cree varias opciones de configuración. Cada recurso puede tener hasta cinco configuraciones de diagnóstico.

Para más información sobre la configuración de diagnóstico, consulte [Creación de una configuración de diagnóstico para recopilar registros de plataforma y métricas en Azure](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings).

### <a name="log-analytics"></a>Análisis de registro
Log Analytics es la herramienta principal de Azure Portal para escribir consultas de registro y analizar de forma interactiva los resultados de las consultas. Incluso si una consulta de registro se usa en otra parte de Azure Monitor, normalmente escribirá y probará la consulta primero con Log Analytics. Para más información sobre el uso de Log Analytics y la creación de consultas de registro, consulte [Introducción a las consultas de registro en Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview). 

### <a name="workbooks"></a>Libros
Los libros combinan texto, consultas de análisis, métricas de Azure y parámetros en informes interactivos enriquecidos. Los libros son editables por cualquier otro miembro del equipo que tenga acceso a los mismos recursos de Azure. Para más información sobre los libros, consulte [Libros de Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks). Además, puede trabajar con las plantillas de libro y contribuir a ellas. Para más información, consulte [Plantillas de libro de Azure Monitor](https://go.microsoft.com/fwlink/?linkid=867045).

## <a name="next-steps"></a>Pasos siguientes

Conozca más sobre las siguientes tecnologías:
- [Blog: Plataforma de informes de Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)
- [Azure Monitor](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor)
- [¿Qué es Log Analytics?](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview#what-is-log-analytics)
- [Consultas de registros](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)
- [Introducción a Log Analytics en Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal)
- [Libros de Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)
- [Herramientas de administración de eventos e información de seguridad (SIEM)](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
