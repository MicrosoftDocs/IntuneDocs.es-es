---
title: 'Auditoría de cambios y eventos en Microsoft Intune: Azure | Microsoft Docs'
description: Obtenga información acerca de cómo revisar los registros de auditoría que registran las actividades de Microsoft Intune.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d01b1f745450785209bf289be5b6e36ac65cc2d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046301"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Uso de registros de auditoría para realizar un seguimiento y supervisar eventos en Microsoft Intune

Los registros de auditoría incluyen un registro de las actividades que generan un cambio en Microsoft Intune. Las acciones de creación, actualización (edición), eliminación, asignación y remotas crean eventos de auditoría que los administradores pueden revisar para la mayoría de las cargas de trabajo de Intune. La auditoría está habilitada de forma predeterminada para todos los clientes. No se puede deshabilitar.

> [!NOTE]
> Los eventos de auditoría comenzaron a registrarse en la versión de características de diciembre de 2017. Los eventos anteriores no están disponibles.

## <a name="who-can-access-the-data"></a>¿Quién puede tener acceso a los datos?

Los usuarios con los siguientes permisos pueden revisar los registros de auditoría:

- Administrador global
- Administrador del servicio de Intune
- Administradores asignados a un rol de Intune con los permisos **Datos de auditoría** - **Lectura**

## <a name="audit-logs-for-intune-workloads"></a>Registros de auditoría para cargas de trabajo de Intune

Puede revisar los registros de auditoría en el grupo de supervisión para cada carga de trabajo de Intune:

1. En [Azure Portal](https://portal.azure.com/), seleccione **Todos los servicios**, filtre por **Intune** > seleccione **Intune**.
2. Elija la carga de trabajo cuyos registros de auditoría quiere revisar. Por ejemplo, seleccione **Dispositivos**.
3. En **Supervisión**, elija **Registros de auditoría**.

## <a name="route-logs-to-azure-monitor"></a>Enrutamiento de registros a Azure Monitor

También se pueden enrutar registros de auditoría y registros operativos a Azure Monitor. En **Registros de auditoría**, seleccione **Exportar configuración de datos**:

![Exportación de datos de registro en Azure Monitor seleccionando Exportar configuración de datos en Intune](./media/audit-logs-export-data-settings.png)

Para más información sobre esta característica, consulte [Envío de datos de registro al almacenamiento, a Event Hubs o a Log Analytics](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Revisión de eventos de auditoría

![Elegir registros de auditoría en Intune para ver las acciones y las fechas en que se produjeron los eventos](./media/monitor-audit-logs.png "Registros de auditoría")

Un registro de auditoría tiene una vista de lista predeterminada que muestra los elementos siguientes:

- Fecha y hora en que se produjo el evento
- Iniciado por (actor)
- Nombre de aplicación
- Actividad
- Destinos
- Category
- Estado

Para ver información más específica sobre un evento, seleccione un elemento de la lista:

![Obtener información más específica sobre quiénes hicieron qué en registro de auditoría de Intune](./media/monitor-audit-log-detail.png "Detalles del registro de auditoría")

> [!NOTE]
> **Iniciado por (actor)** incluye información sobre quién ejecutó la tarea y sobre dónde se ejecutó. Por ejemplo, si ejecuta la actividad en Intune en Azure Portal, como **Aplicación** siempre figura **Extensión del portal de Microsoft Intune** y como **Id. de aplicación** siempre se usa el mismo GUID.
> 
> La sección **Destinos** muestra varios destinos y las propiedades que cambiaron.  

## <a name="filter-audit-events"></a>Filtrado de eventos de auditoría

Cada carga de trabajo tiene un elemento de menú que filtra previamente la categoría de eventos de auditoría asociados a ese panel. Una opción de filtro independiente le permite cambiar a distintas categorías, y se detalla una acción de evento dentro de esa categoría. Puede buscar por UPN, como el usuario que realizó la acción. Un filtro de intervalo de fechas permite opciones de 24 horas, 7 días o 30 días. De forma predeterminada, se muestran los últimos 30 días de eventos de auditoría.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Uso de API Graph para recuperar eventos de auditoría

Para más información sobre el uso de Graph API para recuperar hasta un año de eventos de auditoría, vea [Enumerar auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Pasos siguientes

[Envío de datos de registro a Storage, Event Hubs o Log Analytics](review-logs-using-azure-monitor.md).

[Revisión de los registros de protección de aplicaciones cliente](app-protection-policy-settings-log.md).
