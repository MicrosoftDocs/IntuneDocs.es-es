---
title: 'Enrutamiento de registros de auditoría en Azure Monitor mediante Microsoft Intune: Azure | Microsoft Docs'
description: Use la característica Configuración de diagnóstico para enviar los registros de auditoría y los registros operativos de Microsoft Intune a la cuenta de almacenamiento de Azure, Event Hubs o Log Analytics. Elija cuánto tiempo desea conservar los datos y vea algunos costos estimados para inquilinos de diferente tamaño.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb33a1207e165323de2e82467c7a0dd5239d9713
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "61507371"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>Envío de datos de registro al almacenamiento, a Event Hubs o a Log Analytics en Intune (versión preliminar)

Microsoft Intune incluye los registros integrados que proporcionan información sobre el entorno. Los **registros de auditoría** muestran detalles sobre los distintos eventos o tareas que tienen lugar en Intune. Los **registros operativos (versión preliminar)** muestran detalles sobre los usuarios y los dispositivos que se inscribieron correctamente o que no se pudieron inscribir, así como detalles sobre los dispositivos no compatibles.

Estos registros también se pueden enviar a los servicios de Azure Monitor, incluidas las cuentas de almacenamiento, Event Hubs y Log Analytics. En concreto, puede:

* Archivar registros de Intune en una cuenta de almacenamiento de Azure para mantener los datos, o archivarlos durante un tiempo establecido.
* Transmitir registros de Intune a un centro de eventos de Azure para su análisis con herramientas de Administración de eventos e información de seguridad (SIEM) populares, como Splunk y QRadar.
* Integrar los registros de Intune con sus propias soluciones de registro personalizadas transmitiéndolos a un centro de eventos.
* Enviar registros de Intune a Log Analytics para habilitar las visualizaciones enriquecidas, la supervisión y las alertas de los datos conectados.

Estas características forman parte de la característica **Configuración de diagnóstico** en Intune.

En este artículo se muestra cómo usar la característica **Configuración de diagnóstico** para enviar datos de registro a distintos servicios, ofrece ejemplos y estimaciones de costos y responde a algunas preguntas comunes.

## <a name="prerequisites"></a>Requisitos previos

Para usar esta característica, necesita:

* Una suscripción de Azure: Si no tiene una suscripción de Azure, puede [registrarse para obtener una evaluación gratuita](https://azure.microsoft.com/free/).
* Un entorno de Microsoft Intune (inquilino) en Azure
* Un usuario que sea un **administrador global** o **administrador de servicios de Intune** para el inquilino de Intune.

Dependiendo de dónde desea enrutar los datos de registro de auditoría, necesita uno de los siguientes servicios:

* Una [cuenta de almacenamiento de Azure](https://docs.microsoft.com/azure/storage/common/storage-account-overview) con permisos *ListKeys*. Se recomienda que use una cuenta de almacenamiento general y no una cuenta de almacenamiento de blobs. Para información sobre los precios de almacenamiento, consulte la [calculadora de precios de Azure Storage](https://azure.microsoft.com/pricing/calculator/?service=storage). 
* Un [espacio de nombres de Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace) para integrar con soluciones de terceros.
* Un [espacio de nombres de Azure Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) para enviar registros a Log Analytics.

## <a name="send-logs-to-azure-monitor"></a>Envío de registros a Azure Monitor

1. En [Azure Portal](https://portal.azure.com/), seleccione **Todos los servicios**, filtre por **Intune** > seleccione **Intune**.
2. En **Supervisión**, seleccione **Configuración de diagnóstico**. La primera vez que se abra, actívela:

    ![Activación de Configuración de diagnóstico en Intune para enviar registros a Azure Monitor](media/diagnostics-settings-turn-on.png)

3. Escriba las propiedades siguientes:

    - **Nombre**: escriba un nombre para la configuración de diagnóstico. Esta configuración incluye todas las propiedades que especifique. Por ejemplo, escriba `Route audit logs to storage account`.
    - **Archivar en una cuenta de almacenamiento**: guarda los datos de registro en una cuenta de almacenamiento de Azure. Use esta opción si desea guardar o archivar los datos.

        1. Seleccione esta opción > **Configurar**. 
        2. Elija una cuenta de almacenamiento existente en la lista > **Aceptar**.

    - **Transmitir a un centro de eventos**: transmite los registros a un centro de eventos de Azure. Si desea análisis en los datos de registro mediante las herramientas SIEM, como Splunk y QRadar, elija esta opción.

        1. Seleccione esta opción > **Configurar**. 
        2. Elija un espacio de nombres de centro de eventos existente y la directiva en la lista > **Aceptar**.

    - **Enviar a Log Analytics**: envía los datos a Azure Log Analytics. Si desea usar las visualizaciones, supervisión y alertas para los registros, elija esta opción.

        1. Seleccione esta opción > **Configurar**. 
        2. Cree una nueva área de trabajo y escriba los detalles de la misma. O bien, elija un área de trabajo existente en la lista > **Aceptar**.

            El [área de trabajo de Azure Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) proporciona más detalles sobre estas configuraciones.

    - **LOG** > **AuditLogs**: elija esta opción para enviar los [registros de auditoría de Intune](monitor-audit-logs.md) a su cuenta de almacenamiento, al centro de eventos o a Log Analytics. Los registros de auditoría muestran el historial de todas las tareas que genera un cambio en Intune, incluido quién lo hizo y cuándo.

      Si decide usar una cuenta de almacenamiento, especifique también cuántos días desea conservar los datos (retención). Para conservar los datos indefinidamente, establezca **Retención (días)** en `0` (cero).

    - **LOG** > **OperationalLogs**: los registros operativos (versión preliminar) muestran el éxito o el error de los usuarios y los dispositivos que se inscriben en Intune, así como detalles sobre los dispositivos no compatibles. Elija esta opción para enviar los registros de inscripción a su cuenta de almacenamiento, al centro de eventos o a Log Analytics.

      Si decide usar una cuenta de almacenamiento, especifique también cuántos días desea conservar los datos (retención). Para conservar los datos indefinidamente, establezca **Retención (días)** en `0` (cero).

      > [!NOTE]
      > Los registros operativos se encuentran en versión preliminar. Para proporcionar comentarios, incluida la información contenida en los registros operativos, vaya a [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback) (abre un nuevo sitio Web).

    Cuando termine, la configuración tendrá un aspecto similar a la siguiente configuración: 

    ![Imagen de ejemplo que envía los registros de auditoría de Intune a una cuenta de almacenamiento de Azure](media/diagnostics-settings-example.png)

4. Guarde los cambios mediante **Guardar**. La configuración se mostrará en la lista. Cuando se haya creado, puede cambiar la configuración seleccionando **Editar configuración** > **Guardar**.

## <a name="use-audit-logs-throughout-intune"></a>Uso de registros de auditoría en Intune

También puede exportar los registros de auditoría en otras partes de Intune, incluida la inscripción, el cumplimiento, la configuración, los dispositivos, las aplicaciones cliente y mucho más.

Por ejemplo, para exportar los registros de auditoría al usar el cumplimiento del dispositivo:

1. En [Azure Portal](https://portal.azure.com/), seleccione **Todos los servicios**, filtre por **Intune** > seleccione **Intune**.
2. Seleccione **Cumplimiento del dispositivo** > **Monitor** > **Registros de auditoría**:

    ![Selección de registros de auditoría para enrutar datos de Intune al almacenamiento de Azure Monitor, centros de eventos o análisis](media/audit-logs-under-monitor-in-compliance.png)

3. Seleccione **Exportar configuración de datos**. Si no está habilitada, puede activar la **Configuración de diagnóstico**. También puede elegir dónde enviar los registros, como se describe en [Envío de registros a Azure Monitor](#send-logs-to-azure-monitor) (en este artículo).

## <a name="cost-considerations"></a>Consideraciones sobre el costo

Si ya tiene una licencia de Microsoft Intune, necesita una suscripción de Azure para configurar la cuenta de almacenamiento y el centro de eventos. La suscripción de Azure normalmente es gratuita. Sin embargo, tiene que pagar por usar recursos de Azure, incluida la cuenta de almacenamiento para archivado y el centro de eventos para la transmisión. La cantidad de datos y los costos varían según el tamaño del inquilino.

### <a name="storage-size-for-activity-logs"></a>Tamaño de almacenamiento para los registros de actividad

Cada evento del registro de auditoría usa 2 KB de almacenamiento de datos aproximadamente. Para un inquilino con 100 000 usuarios, puede que tenga aproximadamente 1,5 millones de eventos al día. Puede necesitar unos 3 GB de almacenamiento de datos por día. Dado que suelen realizarse operaciones de escritura en lotes de cinco minutos, puede esperar aproximadamente 9000 operaciones de este tipo al mes.

En las siguientes tablas se muestra una estimación de costos según el tamaño del inquilino. También incluye una cuenta de almacenamiento de uso general v2 en la región Oeste de EE. UU. durante al menos un año de retención de datos. Para obtener una estimación para el volumen de datos que espera para sus registros, use la [calculadora de precios de Azure Storage](https://azure.microsoft.com/pricing/details/storage/blobs/).

**Registro de auditoría con 100 000 usuarios**

| | |
|---|---|
|Eventos por día| 1,5 millones|
|Volumen estimado de datos al mes| 90 GB|
|Costo estimado al mes (USD)| 1,93 USD|
|Costo estimado al año (USD)| 23,12 USD|

**Registro de auditoría con 1000 usuarios**

| | |
|---|---|
|Eventos por día| 15.000|
|Volumen estimado de datos al mes| 900 MB|
|Costo estimado al mes (USD)| 0,02 USD|
|Costo estimado al año (USD)| 0,24 USD|

### <a name="event-hub-messages-for-activity-logs"></a>Mensajes del centro de eventos para los registros de actividad

Los eventos normalmente se realizan por lotes en intervalos de cinco minutos y se envían como un solo mensaje con todos los eventos dentro de ese período de tiempo. Un mensaje del centro de eventos tiene un tamaño máximo de 256 KB. Si el tamaño total de todos los mensajes dentro del período de tiempo superó ese volumen, se envían varios mensajes.

Por ejemplo, normalmente tienen lugar unos 18 eventos por segundo para un inquilino de gran tamaño de más de 100 000 usuarios. Esto equivale a 5400 eventos cada cinco minutos (300 segundos x 18 eventos). Los registros de auditoría tienen un tamaño aproximado de 2 KB por evento. Esto equivale a 10,8 MB de datos. Por lo tanto, se envían 43 mensajes al centro de eventos en ese intervalo de cinco minutos.

La tabla siguiente contiene costos estimados por mes para un centro de eventos básico en la región Oeste de EE. UU., dependiendo del volumen de datos de evento. Para obtener una estimación del volumen de datos que espera para sus registros, use la [calculadora de precios de Event Hubs](https://azure.microsoft.com/pricing/details/event-hubs/).

**Registro de auditoría con 100 000 usuarios**

| | |
|---|---|
|Eventos por segundo| 18|
|Eventos por intervalo de cinco minutos| 5400|
|Volumen por intervalo| 10,8 MB|
|Mensajes por intervalo| 43|
|Mensajes al mes| 371 520|
|Costo estimado al mes (USD)| 10,83 USD|

**Registro de auditoría con 1000 usuarios**

| | |
|---|---|
|Eventos por segundo|0,1 |
|Eventos por intervalo de cinco minutos| 52|
|Volumen por intervalo|104 KB |
|Mensajes por intervalo|1 |
|Mensajes al mes|8640 |
|Costo estimado al mes (USD)|10,80 USD |

### <a name="log-analytics-cost-considerations"></a>Consideraciones sobre el costo de Log Analytics

Para revisar los costos relacionados con la administración del área de trabajo de Log Analytics, consulte [Administración del uso y los costos para Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage).

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

Obtenga respuestas a las preguntas más frecuentes así como información sobre los problemas conocidos con los registros de Intune en Azure Monitor.

#### <a name="which-logs-are-included"></a>¿Qué registros se incluyen?

Los registros de auditoría y los registros operativos (versión preliminar) están disponibles para el enrutamiento mediante esta característica.

#### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>Después de una acción, ¿cuándo se muestran los registros correspondientes en el centro de eventos?

Los registros normalmente se muestran en el centro de eventos unos minutos después de realizar la acción. [Documentación de Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs/) proporciona más información.

#### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>Después de una acción, ¿cuándo se muestran los registros correspondientes en la cuenta de almacenamiento?

Para las cuentas de almacenamiento de Azure, la latencia es en cualquier lugar de 5 a 15 minutos después de que se ejecuta la acción.

#### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>¿Qué ocurre si un administrador cambia el período de retención de una configuración de diagnóstico?

La nueva directiva de retención se aplica a los registros recopilados después del cambio. Los registros recopilados antes del cambio de directiva no se ven afectados.

#### <a name="how-much-does-it-cost-to-store-my-data"></a>¿Cuánto cuesta almacenar mis datos?

Los costos de almacenamiento dependen del tamaño de los registros y del período de retención que elija. Para una lista de los costos estimados para los inquilinos, que dependen del volumen de los registros generado, vea [Tamaño de almacenamiento para los registros de actividad](#storage-size-for-activity-logs) (en este artículo).

#### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>¿Cuánto cuesta transmitir mis datos a un centro de eventos?

Los costos de transmisión dependen del número de mensajes que se reciben por minuto. Para detalles sobre cómo se calculan los costos y las estimaciones de costos en función del número de mensajes, consulte [Mensajes del centro de eventos para los registros de actividad](#event-hub-messages-for-activity-logs) (en este artículo).

#### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>¿Cómo integro los registros de auditoría de Intune con mi sistema SIEM?

Use Azure Monitor con Event Hubs para transmitir registros al sistema SIEM. En primer lugar, [transmita los registros a un centro de eventos](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub). A continuación, [configure la herramienta SIEM](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub) con el centro de eventos configurado. 

#### <a name="what-siem-tools-are-currently-supported"></a>¿Qué herramientas SIEM se admiten actualmente?

Actualmente, [Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk), QRadar y [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) (abre un nuevo sitio Web) admiten Azure Monitor. Para más información sobre cómo funcionan los conectores, consulte [Flujo de datos de supervisión de Azure a un centro de eventos para que lo consuma una herramienta externa](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs).

#### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>¿Puedo acceder a los datos desde un centro de eventos sin usar una herramienta SIEM externa?

Sí. Para acceder a los registros desde su aplicación personalizada, puede usar la [API de Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph).

#### <a name="what-data-is-stored"></a>¿Dónde se almacenan los datos?

Intune no almacena los datos enviados a través de la canalización. Intune enruta los datos a la canalización de Azure Monitor, con la autorización del inquilino. Para más información, vea [Introducción a Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview).

## <a name="next-steps"></a>Pasos siguientes

* [Archivo de los registros de actividad en una cuenta de almacenamiento](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [Enrutamiento de registros de actividad a un centro de eventos](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [Integración de los registros de actividad con Log Analytics](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
