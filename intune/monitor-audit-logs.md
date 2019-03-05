---
title: Registros de auditoría para actividades de Microsoft Intune
description: Obtenga información acerca de cómo revisar los registros de auditoría que registran las actividades de Microsoft Intune.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f44d25f75ccc68912bea7b108ca56afe6aecb528
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57239057"
---
# <a name="audit-logs-for-intune-activities"></a>Registros de auditoría para actividades de Intune
Los registros de auditoría proporcionan un registro de las actividades que generan un cambio en Microsoft Intune. Las acciones relacionadas con crear, actualizar (editar), eliminar y asignar, o las tareas remotas, generan eventos de auditoría que puede revisar. Puede revisar registros de auditoría para la mayoría de las cargas de trabajo de Intune. La auditoría está habilitada de forma predeterminada para todos los clientes y no se puede deshabilitar. Los eventos de auditoría empiezan a registrarse en la fecha de lanzamiento de la característica de diciembre de 2017; los eventos anteriores no están disponibles.

## <a name="who-can-access-the-data"></a>¿Quién puede tener acceso a los datos?
Los usuarios con los siguientes permisos pueden revisar los registros de auditoría:
- Administrador global
- Administrador del servicio de Intune
- Administradores asignados a un rol de Intune con los permisos **Datos de auditoría** - **Lectura**

## <a name="audit-logs-for-intune-workloads"></a>Registros de auditoría para cargas de trabajo de Intune
Puede revisar los registros de auditoría en el grupo de supervisión para cada carga de trabajo de Intune.  
1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija la carga de trabajo para la que desea revisar los registros de auditoría, por ejemplo, **Dispositivos**.
4. En el grupo **Supervisión** de la carga de trabajo, elija **Registros de auditoría**.

## <a name="review-audit-events"></a>Revisión de eventos de auditoría
![Registros de auditoría](./media/monitor-audit-logs.png "Registros de auditoría")

Un registro de auditoría tiene una vista de lista predeterminada que muestra los elementos siguientes:    

- fecha y hora en que se produjo el evento
- Iniciado por (actor)
- Nombre de aplicación
- Actividad
- Destinos
- Category
- Estado

Al hacer clic en un elemento en la vista de lista, obtendrá todos los detalles disponibles sobre él.

![Registros de auditoría](./media/monitor-audit-log-detail.png "Registros de auditoría")

> [!Note]    
> La sección **Iniciado por (actor)** de los detalles de registro de auditoría proporciona información sobre quién llevó a cabo la actividad y desde donde se ha ejecutado. Por ejemplo, si lleva a cabo la actividad en Intune en Azure Portal,como **Aplicación** siempre figura **Extensión del portal de Microsoft Intune** y como **Id. de aplicación** siempre se usa el mismo GUID. 
>    
> La sección **Destinos** puede mostrar varios destinos y las propiedades que cambiaron.  


## <a name="filter-audit-events"></a>Filtrado de eventos de auditoría
Cada carga de trabajo tiene un elemento de menú que filtra previamente la categoría de eventos de auditoría asociados a ese panel. Una opción de filtro independiente le permite cambiar a distintas categorías, y se detalla una acción de evento dentro de esa categoría. Puede buscar por UPN (por ejemplo, el usuario que realizó la acción). Un filtro de intervalo de fechas permite opciones de 24 horas, 7 días o 30 días. De forma predeterminada, se muestran los últimos 30 días de eventos de auditoría.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Uso de API Graph para recuperar eventos de auditoría
Para obtener más información acerca de cómo usar API Graph para recuperar hasta un año de eventos de auditoría, consulte [List auditEvents](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/intune_auditing_auditevent_list) (Enumeración de auditEvents).
