---
title: Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune
titleSuffix: ''
description: Obtenga información sobre cómo usar Microsoft Intune para incluir y excluir asignaciones de aplicaciones.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f073c8ad7a8e087a791ee756683011fac6947162
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547961"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Inclusión y exclusión de asignaciones de aplicaciones en Microsoft Intune

Con Intune, puede determinar quién tiene acceso a una aplicación mediante la asignación de grupos de usuarios que quiera incluir o excluir. Antes de asignar grupos a la aplicación, se debe establecer el tipo de asignación de una aplicación. El tipo de asignación hace que la aplicación esté disponible, sea obligatoria o se desinstale. 

Para establecer la disponibilidad de una aplicación, la inclusión y exclusión de asignaciones de aplicaciones en un grupo de usuarios o dispositivos se realiza mediante una combinación de asignaciones de grupo de inclusión y exclusión. Esta capacidad puede serle útil en el momento de hacer que la aplicación esté disponible mediante la inclusión de un grupo grande, para después restringir los usuarios seleccionados excluyendo un grupo más reducido. El grupo más pequeño podría ser un grupo de prueba o un grupo ejecutivo. 

Como procedimiento recomendado, cree y asigne aplicaciones específicas para los grupos de usuarios y por separado para los grupos de dispositivos. Para más información sobre los grupos, consulte [Agregar grupos para organizar usuarios y dispositivos](~/fundamentals/groups-add.md).  

Existen casos importantes al incluir o excluir asignaciones de aplicaciones:

- La exclusión tiene prioridad sobre la inclusión en los siguientes escenarios de tipos de grupos:
    - Inclusión y exclusión de grupos de usuarios al asignar aplicaciones.
    - Inclusión y exclusión de grupos de dispositivos al asignar aplicaciones.

    Por ejemplo, si asigna un grupo de dispositivos al grupo **Todos los usuarios corporativos**, pero excluye los miembros del grupo de usuarios **Personal de administración ejecutiva**, **Todos los usuarios corporativos** excepto el **Personal de administración ejecutiva** obtienen la asignación, ya que ambos son grupos de usuarios.
- Intune no evalúa las relaciones entre grupos de usuarios y dispositivos. Si asigna aplicaciones a grupos mixtos, puede que los resultados no sean los deseados o esperados.

    Este sería el caso si asigna un grupo de dispositivos al grupo de usuarios **Todos los usuarios**, pero excluye un grupo de dispositivos **Todos los dispositivos personales**. En esta asignación de aplicaciones de grupo mixto, **Todos los usuarios** obtienen la aplicación. La exclusión no se aplica.

Como resultado, no se recomienda asignar aplicaciones a grupos mixtos.

> [!NOTE]
> Al establecer una asignación de grupo para una aplicación, el tipo **Not Applicable** (No es aplicable) queda en desuso y se reemplaza por la funcionalidad de exclusión de grupos. 
>
> Intune proporciona grupos **Todos los usuarios** y **Todos los dispositivos** ya creados en la consola. De forma práctica, los grupos llevan incorporadas optimizaciones. Es muy recomendable usar estos grupos para dirigirse a todos los usuarios y todos los dispositivos en lugar de a cualquier grupo "todos los usuarios" o "todos los dispositivos" que haya podido crear usted mismo.  
>
> Android Enterprise admite grupos incluidos y excluidos. Puede aprovechar los grupos integrados **Todos los usuarios** y **Todos los dispositivos** para la asignación de aplicaciones de Android Enterprise. 

## <a name="include-and-exclude-groups-when-assigning-apps"></a>Inclusión y exclusión de grupos al asignar aplicaciones 
Para asignar una aplicación a grupos mediante la asignación de inclusión y exclusión, siga estos pasos:
1. Inicie sesión en [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. En el panel **Intune**, seleccione **Aplicaciones cliente**.
4. En el panel **Aplicaciones cliente**, seleccione **Aplicaciones**. Se muestra la lista de aplicaciones agregadas.
5. Seleccione la aplicación que quiera asignar. Un panel muestra información sobre la aplicación. 
6. En la sección **Administrar** del menú, seleccione **Asignaciones**. 

    ![Inclusión de las asignaciones de aplicaciones al asignar aplicaciones](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)
7. Seleccione **Agregar grupo** para agregar los grupos de usuarios que están asignados a la aplicación. 
8. Seleccione un **tipo de asignación** entre los disponibles en el panel **Agregar grupo**.
9. Seleccione **Available with or without enrollment** (Disponible con o sin inscripción) como tipo de asignación.

    ![Asignaciones de aplicaciones de Intune: agregar un grupo](./media/apps-inc-exl-assignments/apps-inc-exl-02.png)
10. Seleccione **Grupos incluidos** para seleccionar el grupo de usuarios para los que estará disponible esta aplicación.

    > [!NOTE]
    > Al agregar un grupo, si ningún otro grupo se ha incluido para un tipo de asignación específica, la aplicación se preselecciona y no se puede modificar para otros tipos de asignación de inclusión. El grupo que se ha usado no se puede utilizar como un grupo incluido.

11. Seleccione **Sí** para que esta aplicación esté disponible para todos los usuarios.

    ![Asignaciones de aplicaciones de Intune: incluir grupos](./media/apps-inc-exl-assignments/apps-inc-exl-03.png)
12. Haga clic en **Aceptar** para establecer el grupo que quiere incluir.
13. Seleccione **Grupos excluidos** para seleccionar los grupos de usuarios para los que no estará disponible esta aplicación. 
14. Seleccione los grupos para excluir. A continuación, esta aplicación deja de estar disponible para esos grupos.

    ![Asignaciones de la aplicaciones de Intune: excluir grupos](./media/apps-inc-exl-assignments/apps-inc-exl-04.png)
15. Haga clic en **Seleccionar** para completar la selección de grupos.
16. En el panel **Agregar grupo**, seleccione **Aceptar**. Aparece la lista de **asignaciones** de aplicaciones.
17. Haga clic en **Guardar** para activar las asignaciones de grupo para la aplicación.

Cuando se realizan asignaciones de grupos, los grupos que se han asignado ya no están disponibles para modificarse. Si quiere seleccionar un grupo que actualmente no está disponible, quite primero la aplicación de lista asignada de aplicaciones. 

Para editar las asignaciones, en la lista de **asignaciones** de aplicaciones, seleccione la fila que contiene la asignación específica que quiere cambiar. Otra forma de quitar una asignación es seleccionar los puntos suspensivos ( **…** ) al final de una fila y, luego, seleccionar **Quitar**. Para cambiar la vista de la lista **Asignaciones**, agrupe por **Tipo de asignación** o por **Incluidos o excluidos**.

![Asignaciones de aplicaciones de Intune: completar](./media/apps-inc-exl-assignments/apps-inc-exl-05.png)

## <a name="next-steps"></a>Pasos siguientes

- Para más información sobre la inclusión y exclusión de asignaciones de aplicaciones para grupos, consulte el [blog de Microsoft Intune](https://aka.ms/new_app_assignment_process).
- Consulte [Supervisión de información y asignaciones de aplicaciones](apps-monitor.md).
